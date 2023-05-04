---
title: Best practice per l’offload di risorse
description: Casi d’uso consigliati e best practice per scaricare i flussi di lavoro di acquisizione e replica delle risorse in [!DNL Experience Manager] Risorse.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 3ecc8988-add1-47d5-80b4-984beb4d8dab
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1841'
ht-degree: 1%

---

# Best practice per l’offload di risorse {#assets-offloading-best-practices}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!WARNING]
>
>Questa funzione è obsoleta [!DNL Experience Manager] 6.4 e viene rimosso in [!DNL Experience Manager] 6.5. Pianificare di conseguenza.

La gestione di file di grandi dimensioni e l’esecuzione di flussi di lavoro in Adobe Experience Manager Assets può utilizzare notevoli risorse di CPU, memoria e I/O. In particolare, le dimensioni delle risorse, i flussi di lavoro, il numero di utenti e la frequenza dell’inserimento delle risorse possono influenzare le prestazioni complessive del sistema. Le operazioni più impegnative in termini di risorse includono flussi di lavoro di acquisizione e replica delle risorse. L’utilizzo intensivo di questi flussi di lavoro in una singola istanza di authoring può influire negativamente sull’efficienza dell’authoring.

Lo scaricamento di queste attività alle istanze di lavoro dedicate può ridurre le spese generali di CPU, memoria e IO. In generale, l&#39;idea alla base dello scaricamento è quella di distribuire attività che consumano risorse CPU/Memory/IO intensive alle istanze di lavoro dedicate. Le sezioni seguenti includono casi d’uso consigliati per lo scaricamento delle risorse.

## [!DNL Experience Manager Assets] Offload {#aem-assets-offloading}

[!DNL Experience Manager] Assets implementa un’estensione del flusso di lavoro nativa specifica per le risorse per lo scaricamento. Si basa sull’estensione del flusso di lavoro generica fornita dal framework di offload, ma include funzionalità aggiuntive specifiche per le risorse nell’implementazione. Lo scopo dello scaricamento delle risorse è quello di eseguire in modo efficiente il flusso di lavoro Aggiorna risorsa DAM su una risorsa caricata. Lo scaricamento delle risorse ti consente di ottenere un maggiore controllo sui flussi di lavoro di acquisizione.

## [!DNL Experience Manager] Componenti di offload delle risorse {#aem-assets-offloading-components}

Il diagramma seguente illustra i componenti principali del processo di scaricamento delle risorse:

![chlimage_1-55](assets/chlimage_1-55.png)

### Flusso di lavoro Aggiorna risorsa DAM {#dam-update-asset-offloading-workflow}

Il flusso di lavoro DAM Update Asset Offloading viene eseguito sul server principale (autore) sul quale l’utente carica le risorse. Questo flusso di lavoro viene attivato da un modulo di avvio regolare del flusso di lavoro. Invece di elaborare la risorsa caricata, questo flusso di lavoro di scaricamento crea un nuovo lavoro utilizzando l’argomento *com/adobe/granite/workflow/offload*. Il flusso di lavoro di offload aggiunge il nome del flusso di lavoro di destinazione, in questo caso il flusso di lavoro Aggiorna risorsa DAM, e il percorso della risorsa al payload del processo. Dopo aver creato il processo di offload, il flusso di lavoro di offload nell’istanza primaria attende l’esecuzione del processo di offload.

### Responsabile del lavoro {#job-manager}

Il job manager distribuisce i nuovi job alle istanze del worker. Nella progettazione del meccanismo di distribuzione è importante tenere conto dell&#39;abilitazione degli argomenti. I processi possono essere assegnati solo alle istanze in cui è abilitato l’argomento del processo. Disattiva l&#39;argomento `com/adobe/granite/workflow/offloading` in primo luogo e consentire al lavoratore di assicurarsi che il lavoro sia assegnato al lavoratore.

### [!DNL Experience Manager] scarico {#aem-offloading}

Il framework di offload identifica i processi di offload del flusso di lavoro assegnati alle istanze di lavoro e utilizza la replica per trasportarli fisicamente, compreso il carico utile (ad esempio, le immagini da acquisire), ai lavoratori.

### Flusso di lavoro che scarica il consumatore del lavoro {#workflow-offloading-job-consumer}

Una volta che un lavoro è scritto sul lavoratore, il responsabile del lavoro chiama il consumatore del posto di lavoro responsabile del *com/adobe/granite/workflow/offload* argomento. Il consumatore del lavoro esegue quindi il flusso di lavoro Aggiorna risorsa DAM sulla risorsa.

## Topologia Sling {#sling-topology}

I gruppi di topologia Sling [!DNL Experience Manager] e consente loro di conoscersi reciprocamente, indipendentemente dalla persistenza sottostante. Questa caratteristica della topologia Sling ti consente di creare topologie per scenari non raggruppati, raggruppati e misti. Un’istanza può esporre le proprietà all’intera topologia. Il framework fornisce callback per l&#39;ascolto delle modifiche della topologia (istanze e proprietà). La topologia Sling fornisce le basi per i lavori distribuiti Sling.

### Processi distribuiti Sling {#sling-distributed-jobs}

I lavori distribuiti Sling facilitano la distribuzione dei posti di lavoro tra una serie di istanze che sono membri della topologia. I lavori Sling si basano sull&#39;idea delle funzionalità. Un processo è definito dal relativo argomento di lavoro. Per eseguire un processo, un&#39;istanza deve fornire un consumer di processi per un argomento di lavoro specifico. L&#39;argomento del lavoro è il driver principale del meccanismo di distribuzione.

I processi vengono distribuiti solo alle istanze che forniscono un consumer di lavoro per l’argomento. Attivando/disattivando i processi consumer su un’istanza, puoi definire le funzionalità di un’istanza e influenzare il meccanismo di distribuzione. I consumatori di lavoro disponibili di un&#39;istanza vengono trasmessi a tutta la topologia.

In questo contesto, il termine distribuzione indica l&#39;assegnazione di un lavoro a un&#39;istanza specifica che fornisce un consumatore di lavoro. L&#39;assegnazione a un&#39;istanza viene memorizzata nell&#39;archivio. In altre parole, i lavori distribuiti Sling possono essere assegnati a qualsiasi istanza della topologia per impostazione predefinita. Tuttavia, altri processi possono essere eseguiti solo da istanze che condividono lo stesso archivio. Ciò implica che questi processi possono essere eseguiti solo da istanze che fanno parte dello stesso cluster. I processi assegnati a istanze di un cluster diverso non vengono eseguiti.

### Quadro di riferimento per lo scarico delle granaglie {#granite-offloading-framework}

Il framework di offload di Granite integra la distribuzione dei processi Sling per eseguire i processi assegnati a istanze non raggruppate. Non esegue alcuna distribuzione (assegnazione di istanza). Tuttavia, identifica i processi Sling distribuiti alle istanze non cluster e li trasporta all&#39;istanza target per l&#39;esecuzione. Attualmente, lo scaricamento utilizza la replica per eseguire questo trasporto di lavoro. Per eseguire un processo, lo scaricamento definisce l&#39;input e l&#39;output, che vengono quindi combinati con il processo per generare il payload del processo.

I lavori distribuiti Sling forniscono il quadro di lavoro e distribuzione. Lo scarico granito si occupa solo del trasporto per il caso speciale in cui i posti di lavoro sono distribuiti a istanze non raggruppate.

Oltre al trasporto, il framework di offload fornisce un&#39;estensione per il motore del flusso di lavoro. Consente al framework di creare processi distribuiti come parte di un flusso di lavoro e di attenderne il completamento, prima che il flusso di lavoro avanzi. Viene implementato utilizzando l’API di passaggio esterno del flusso di lavoro dal motore del flusso di lavoro. Una delle estensioni facilita la distribuzione generica dei flussi di lavoro. La distribuzione di singoli passaggi del flusso di lavoro non è supportata.

Il framework di offload include anche un’interfaccia utente per visualizzare e controllare l’abilitazione degli argomenti di lavoro nell’intera topologia. L’interfaccia utente ti consente di configurare comodamente l’enablemenet dell’argomento dei lavori distribuiti Sling. Puoi anche impostare lo scaricamento senza l’interfaccia utente.

## Guida generale e best practice per lo scaricamento delle risorse {#general-guidance-and-best-practices-for-asset-offloading}

Ogni implementazione è unica e, come tale, non esiste una configurazione di offload unica per tutte le dimensioni. Le sezioni seguenti forniscono indicazioni e best practice sullo scarico dell’assimilazione delle risorse.

Lo scarico degli asset impone anche costi generali al sistema, comprese le spese generali di funzionamento. In caso di problemi con il caricamento dell’acquisizione delle risorse, Adobe consiglia di migliorare prima la configurazione senza scaricarla. Prima di passare allo scaricamento delle risorse, considera le seguenti opzioni:

* Scala hardware
* Ottimizzare i flussi di lavoro
* Utilizzare flussi di lavoro transitori
* Limitare il numero di core utilizzati per i flussi di lavoro

Se ritieni che lo scaricamento delle risorse sia un approccio appropriato, l’Adobe fornisce le seguenti indicazioni:

* Si consiglia un’implementazione basata su TarMK
* Lo scaricamento delle risorse basate su TarMK non è progettato per una scalabilità orizzontale estesa
* Assicurati che le prestazioni di rete tra l&#39;autore e i lavoratori siano soddisfacenti

### Distribuzione offload delle risorse consigliate {#recommended-assets-offloading-deployment}

Con [!DNL Experience Manager] e Oak, ci sono diversi scenari di implementazione possibili. Per lo scaricamento delle risorse, si consiglia una distribuzione basata su TarMK con un datastore condiviso. Il diagramma seguente illustra la distribuzione consigliata:

![chlimage_1-56](assets/chlimage_1-56.png)

Per informazioni dettagliate sulla configurazione di un archivio dati, consulta [Configurazione degli archivi di nodi e degli archivi di dati in AEM](../sites-deploying/data-store-config.md).

### Disattivazione della gestione automatica degli agenti {#turning-off-automatic-agent-management}

Adobe consiglia di disattivare la gestione automatica degli agenti perché non supporta la replica senza binario e può causare confusione durante l&#39;impostazione di una nuova topologia di offload. Inoltre, non supporta automaticamente il flusso di replica in avanti richiesto dalla replica senza binario.

1. Apri Configuration Manager dall&#39;URL `http://localhost:4502/system/console/configMgr`.
1. Apri la configurazione per `OffloadingAgentManager` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`).
1. Disattiva la gestione automatica degli agenti.

### Utilizzo della replica in avanti {#using-forward-replication}

Per impostazione predefinita, lo scaricamento del trasporto utilizza la replica inversa per richiamare le risorse scaricate dal processo di lavoro al sistema primario. Gli agenti di replica inversa non supportano la replica senza binario. È necessario configurare lo scaricamento per utilizzare la replica in avanti per riportare le risorse scaricate dal processo di lavoro al sistema primario.

1. Se effettui la migrazione dalla configurazione predefinita utilizzando la replica inversa, disattiva o elimina tutti gli agenti denominati &quot; `offloading_outbox`&quot; e &quot; `offloading_reverse_*`&quot; sul primario e sul lavoratore, dove &amp;ast; rappresenta l’id Sling dell’istanza target.
1. Su ogni processo di lavoro, crea un nuovo agente di replica in avanti che punta al principale. La procedura è la stessa della creazione di agenti in avanti da primario a lavoratore. Vedi [Creazione Di Agenti Di Replica Per Lo Scaricamento](../sites-deploying/offloading.md#creating-replication-agents-for-offloading) per istruzioni su come impostare gli agenti di replica di offload.
1. Apri configurazione per `OffloadingDefaultTransporter`  (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`).
1. Modifica il valore della proprietà `default.transport.agent-to-master.prefix` da `offloading_reverse` a `offloading`.

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### Utilizzo del datastore condiviso e della replica senza binario tra autori e lavoratori  {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

Si consiglia di utilizzare la replica senza binario per ridurre il sovraccarico di trasporto per lo scarico delle risorse. Per informazioni su come impostare la replica senza binario per un datastore condiviso, vedi [Configurazione di Node Stores e Data Store in AEM](/help/sites-deploying/data-store-config.md). La procedura non è diversa per lo scaricamento delle risorse, tranne per il fatto che coinvolge altri agenti di replica. Poiché la replica senza binario funziona solo con agenti di replica in avanti, è necessario utilizzare anche la replica in avanti per tutti gli agenti di offload.

### Disattivazione dei pacchetti di trasporto {#turning-off-transport-packages}

Per impostazione predefinita, lo scaricamento crea un pacchetto di contenuto che contiene il carico di lavoro e di lavoro di scarico (la risorsa originale) e trasporta questo pacchetto di scaricamento singolo utilizzando una singola richiesta di replica. La creazione di questi pacchetti di offload è controproduttiva quando si utilizza la replica senza binario, perché i binari vengono serializzati nuovamente nel pacchetto durante la creazione del pacchetto. L&#39;utilizzo di questi pacchetti di trasporto può essere disattivato, il che fa sì che il processo di scarico e il carico utile siano trasportati in più richieste di replica, una per ogni entrata del carico utile. In questo modo, è possibile utilizzare il vantaggio della replica senza binario.

1. Apri la configurazione del componente di *OffloadingDefaultTransporter* componente a [http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)
1. Disattiva la proprietà *Pacchetto di replica (default.transport.contentpackage)*.

### Disabilitazione del trasporto del modello di flusso di lavoro {#disabling-the-transport-of-workflow-model}

Per impostazione predefinita, la *Offload delle risorse di aggiornamento DAM* lo scaricamento del flusso di lavoro aggiunge il modello di flusso di lavoro da chiamare sul lavoratore al payload del processo. Poiché questo flusso di lavoro segue l’ *Risorsa di aggiornamento DAM* per impostazione predefinita, questo payload aggiuntivo può essere rimosso.

Se il modello di flusso di lavoro è disabilitato dal payload del processo, assicurati di distribuire le modifiche al modello di flusso di lavoro di riferimento utilizzando altri strumenti, ad esempio il gestore dei pacchetti.

Per disabilitare il trasporto del modello di flusso di lavoro, modifica il flusso di lavoro Aggiorna risorsa DAM .

1. Apri la console del flusso di lavoro da [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).
1. Apri la scheda Modelli .
1. Apri il modello di flusso di lavoro Aggiorna risorsa DAM .
1. Apri le proprietà del passaggio per il passaggio Offload del flusso di lavoro DAM .
1. Apri la scheda Argomenti e deseleziona le opzioni Aggiungi modello a input e Aggiungi modello a output .
1. Salva le modifiche apportate al modello.

### Ottimizzazione dell’intervallo di polling {#optimizing-the-polling-interval}

Lo scaricamento del flusso di lavoro viene implementato utilizzando un flusso di lavoro esterno sul flusso di lavoro primario, che esegue il polling per il completamento del flusso di lavoro scaricato sul processo di lavoro. L’intervallo di polling predefinito per i processi del flusso di lavoro esterno è di cinque secondi. L’Adobe consiglia di aumentare l’intervallo di polling del passaggio di offload delle risorse ad almeno 15 secondi per ridurre il sovraccarico di scarico sul principale.

1. Apri la console del flusso di lavoro da [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).

1. Apri la scheda Modelli .
1. Apri il modello di flusso di lavoro Aggiorna risorsa DAM .
1. Apri le proprietà del passaggio per il passaggio Offload del flusso di lavoro DAM .
1. Aprire la scheda Commons e regolare il valore della proprietà Period.
1. Salva le modifiche apportate al modello.

## Altre risorse {#more-resources}

Questo documento si concentra sullo scarico delle risorse. Ecco alcuni documenti aggiuntivi sullo scaricamento:

* [Offload dei processi](/help/sites-deploying/offloading.md)
* [Offload del flusso di lavoro delle risorse](/help/sites-administering/workflow-offloader.md)
