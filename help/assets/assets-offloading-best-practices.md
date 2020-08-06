---
title: Tecniche consigliate per l'offload di risorse
description: Casi d’uso e procedure ottimali consigliati per scaricare i flussi di lavoro di assimilazione e replica delle risorse in  AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---


# Tecniche consigliate per l&#39;offload di risorse {#assets-offloading-best-practices}

>[!WARNING]
>
>Questa funzione è obsoleta a partire AEM 6.4 e viene rimossa in AEM 6.5. Pianificare di conseguenza.

La gestione di file di grandi dimensioni e l’esecuzione di flussi di lavoro in Adobe Experience Manager (AEM) Assets può richiedere notevoli risorse di CPU, memoria e I/O. In particolare, le dimensioni delle risorse, i flussi di lavoro, il numero di utenti e la frequenza dell’assimilazione delle risorse possono influire sulle prestazioni complessive del sistema. Le operazioni che richiedono più risorse comprendono AEM flussi di lavoro di assimilazione e replica delle risorse. L’uso intensivo di questi flussi di lavoro su un’unica istanza di authoring AEM può influire negativamente sull’efficienza dell’authoring.

L&#39;offload di queste attività alle istanze di lavoro dedicate può ridurre le spese di CPU, memoria e IO. In generale, l&#39;idea dietro lo scaricamento è quella di distribuire le attività che richiedono risorse CPU/Memoria/IO intensive a istanze di lavoro dedicate. Le sezioni seguenti includono i casi di utilizzo consigliati per lo scaricamento delle risorse.

##  AEM Assets Offload {#aem-assets-offloading}

 AEM Assets implementa un’estensione di flusso di lavoro specifica per la risorsa nativa per lo scaricamento. Si basa sull’estensione del flusso di lavoro generica fornita dal framework di scaricamento, ma include nell’implementazione funzioni aggiuntive specifiche per le risorse. Lo scopo dello scaricamento delle risorse è di eseguire in modo efficiente il flusso di lavoro Aggiorna risorsa DAM su una risorsa caricata. Lo scaricamento delle risorse consente di ottenere un maggiore controllo sui flussi di lavoro di assimilazione.

##  AEM Assets Offload Components {#aem-assets-offloading-components}

Il diagramma seguente illustra i componenti principali del processo di scarico delle risorse:

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM Update Asset Offloading workflow {#dam-update-asset-offloading-workflow}

Il flusso di lavoro di offload di risorse di aggiornamento DAM viene eseguito sul server principale (autore) in cui l&#39;utente carica le risorse. Questo flusso di lavoro viene attivato da un normale avvio del flusso di lavoro. Invece di elaborare la risorsa caricata, questo flusso di lavoro di scaricamento crea un nuovo processo, utilizzando l’argomento *com/adobe/granite/workflow/offload*. Il flusso di lavoro di scaricamento aggiunge il nome del flusso di lavoro di destinazione, ovvero il flusso di lavoro Aggiorna risorsa DAM in questo caso, e il percorso della risorsa al payload del processo. Dopo aver creato il processo di scaricamento, il flusso di lavoro di scarico nell’istanza principale attende l’esecuzione del processo di scaricamento.

### Job manager {#job-manager}

Il manager del processo distribuisce nuovi processi alle istanze del lavoratore. Nella progettazione del meccanismo di distribuzione, è importante tenere conto dell&#39;abilitazione degli argomenti. I processi possono essere assegnati solo alle istanze in cui è attivato l’argomento del processo. Disattivate l&#39;argomento `com/adobe/granite/workflow/offloading` principale e attivatelo sul lavoratore per assicurarvi che il processo sia assegnato al lavoratore.

### scarico AEM {#aem-offloading}

Il framework di offload identifica i processi di scarico del flusso di lavoro assegnati alle istanze del lavoratore e utilizza la replica per trasportarli fisicamente, incluso il relativo payload (ad esempio, immagini da assimilare), ai lavoratori.

### Flusso di lavoro che scarica il consumer di processi {#workflow-offloading-job-consumer}

Una volta scritto un processo sul lavoratore, il manager del lavoro chiama il consumatore responsabile dell’argomento *com/adobe/granite/workflow/offload* . Il consumer del processo esegue quindi il flusso di lavoro Aggiorna risorsa DAM sulla risorsa.

## Topologia Sling {#sling-topology}

I gruppi di topologia Sling AEM le istanze e consentono loro di essere consapevoli l&#39;uno dell&#39;altro, indipendentemente dalla persistenza sottostante. Questa caratteristica della topologia Sling consente di creare topologie per scenari non raggruppati, raggruppati e misti. Un&#39;istanza può esporre le proprietà all&#39;intera topologia. Il framework fornisce callback per l&#39;ascolto delle modifiche nella topologia (istanze e proprietà). La topologia Sling fornisce le basi per i lavori distribuiti Sling.

### Sling dei processi distribuiti {#sling-distributed-jobs}

La vendita di posti di lavoro distribuiti facilita la distribuzione dei posti di lavoro tra una serie di istanze appartenenti alla topologia. I processi di segatura si basano sull&#39;idea delle capacità. Un processo è definito dall’argomento del processo. Per eseguire un processo, un&#39;istanza deve fornire un consumer di processi per un argomento di processo specifico. L&#39;argomento processo è il driver principale per il meccanismo di distribuzione.

I processi vengono distribuiti solo alle istanze che forniscono un job consumer per l’argomento. Attivando o disattivando gli utenti del processo in un’istanza, potete definire le capacità di un’istanza e influenzare il meccanismo di distribuzione. Gli utenti di un’istanza di processo disponibili vengono trasmessi all’intera topologia.

In questo contesto, il termine distribuzione indica l’assegnazione di un processo a un’istanza specifica che fornisce un cliente. L&#39;assegnazione a un&#39;istanza viene memorizzata nella directory archivio. In altre parole, per impostazione predefinita i processi distribuiti Sling possono essere assegnati a qualsiasi istanza della topologia. Tuttavia, altri processi possono essere eseguiti solo da istanze che condividono lo stesso repository. Ciò implica che questi processi possono essere eseguiti solo da istanze appartenenti allo stesso cluster. I processi assegnati alle istanze di un altro cluster non vengono eseguiti.

### Granite offloading framework {#granite-offloading-framework}

Il framework di offload Granite integra la distribuzione dei processi Sling per eseguire i processi assegnati a istanze non cluster. Non esegue alcuna distribuzione (assegnazione di istanza). Tuttavia, identifica i processi Sling distribuiti a istanze non cluster e li trasporta all’istanza di destinazione per l’esecuzione. Al momento, lo scarico utilizza la replica per eseguire il trasporto del processo. Per eseguire un processo, lo scarico definisce l’input e l’output, che vengono quindi combinati con il processo per creare il payload del processo.

La vendita di lavori distribuiti fornisce il quadro di riferimento per l’occupazione e la distribuzione. Lo scarico Granite si occupa solo del trasporto per il caso speciale in cui i lavori sono distribuiti a istanze non raggruppate.

Oltre al trasporto, il framework di scarico fornisce un&#39;estensione per il motore del flusso di lavoro. Consente al framework di creare processi distribuiti come parte di un flusso di lavoro e di attenderne il completamento prima che il flusso di lavoro progredisca. Viene implementato utilizzando l&#39;API del passaggio esterno del flusso di lavoro dal motore del flusso di lavoro. Una delle estensioni facilita la distribuzione generica dei flussi di lavoro. La distribuzione di singoli passaggi del flusso di lavoro non è supportata.

Il framework di scaricamento include anche un&#39;interfaccia utente per visualizzare e controllare l&#39;abilitazione degli argomenti del processo nell&#39;intera topologia. L’interfaccia utente consente di configurare comodamente l’argomento enablemenet dei processi distribuiti Sling. Potete anche impostare lo scaricamento senza l’interfaccia utente.

## Guida generale e best practice per lo scarico delle risorse {#general-guidance-and-best-practices-for-asset-offloading}

Ogni implementazione è univoca e, di conseguenza, non esiste una configurazione di scarico unica per tutti. Le sezioni seguenti forniscono indicazioni e procedure ottimali per il caricamento delle risorse.

Lo scarico delle risorse impone anche costi generali sul sistema, comprese le spese generali di funzionamento. In caso di problemi con il caricamento della risorsa,  Adobe consiglia di migliorare la configurazione senza effettuare il caricamento. Prima di passare allo scarico delle risorse, considerate le seguenti opzioni:

* Adatta hardware
* Ottimizzare i flussi di lavoro
* Utilizzare flussi di lavoro transitori
* Limitare il numero di core utilizzati per i flussi di lavoro

Se si conclude che lo scaricamento delle risorse è un approccio appropriato,  Adobe fornisce le seguenti indicazioni:

* Si consiglia una distribuzione basata su TarMK
* Lo scarico delle risorse basate su TarMK non è progettato per il ridimensionamento orizzontale esteso
* Verificare che le prestazioni di rete tra l’autore e i lavoratori siano soddisfacenti

### Risorse consigliate per scaricare la distribuzione {#recommended-assets-offloading-deployment}

Con AEM e Oak, ci sono diversi scenari di implementazione possibili. Per lo scaricamento delle risorse, è consigliabile una distribuzione basata su TarMK con un datastore condiviso. Il diagramma seguente delinea la distribuzione consigliata:

![chlimage_1-56](assets/chlimage_1-56.png)

Per informazioni dettagliate sulla configurazione di un archivio dati, vedere [Configurazione di archivi di nodi e di archivi di dati in AEM](../sites-deploying/data-store-config.md).

### Disattivazione della gestione automatica degli agenti {#turning-off-automatic-agent-management}

 Adobe consiglia di disattivare la gestione automatica dell&#39;agente perché non supporta la replica senza binario e può creare confusione durante la configurazione di una nuova topologia di scaricamento. Inoltre, non supporta automaticamente il flusso di replica in avanti richiesto dalla replica senza binario.

1. Aprite Configuration Manager dall&#39;URL `http://localhost:4502/system/console/configMgr`.
1. Aprite la configurazione per `OffloadingAgentManager` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`).
1. Disattivate la gestione automatica dell&#39;agente.

### Utilizzo della replica in avanti {#using-forward-replication}

Per impostazione predefinita, lo scarico del trasporto utilizza la replica inversa per il pulling delle risorse scaricate dal lavoro al principale. Gli agenti di replica inversa non supportano la replica senza binario. È necessario configurare lo scaricamento per utilizzare la replica in avanti per rimandare le risorse scaricate dal lavoro al principale.

1. Se state eseguendo la migrazione dalla configurazione predefinita utilizzando la replica inversa, disattivate o eliminate tutti gli agenti denominati &quot; `offloading_outbox`&quot; e &quot; `offloading_reverse_*`&quot; sul primario e sul lavoratore, dove &amp;ast; rappresenta l’ID Sling dell’istanza di destinazione.
1. Per ciascun lavoratore, creare un nuovo agente di replica in avanti che indichi il principale. La procedura è identica alla creazione di agenti in avanti da primario a lavoratore. Per istruzioni su come impostare gli agenti di replica [per lo scaricamento](../sites-deploying/offloading.md#creating-replication-agents-for-offloading) , vedere Creazione di agenti di replica per lo scaricamento.
1. Apri la configurazione per `OffloadingDefaultTransporter` (`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`).
1. Modificare il valore della proprietà `default.transport.agent-to-master.prefix` da `offloading_reverse` a `offloading`.

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### Utilizzo dell&#39;archivio dati condiviso e della replica binaria-less tra autori e lavoratori  {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

Si consiglia di utilizzare la replica binaria-less per ridurre il sovraccarico di trasporto per lo scarico delle risorse. Per informazioni su come impostare la replica senza binario per un archivio dati condiviso, vedere [Configurazione di store di nodi e di archivi dati in AEM](/help/sites-deploying/data-store-config.md). La procedura non è diversa per lo scaricamento delle risorse, ma riguarda altri agenti di replica. Poiché la replica senza binario funziona solo con gli agenti di replica in avanti, è consigliabile utilizzare anche la replica in avanti per tutti gli agenti di offload.

### Disattivazione dei pacchetti di trasporto {#turning-off-transport-packages}

Per impostazione predefinita, lo scaricamento crea un pacchetto di contenuto che contiene il payload del processo e del processo di scaricamento (la risorsa originale) e trasporta questo pacchetto di scaricamento singolo utilizzando un&#39;unica richiesta di replica. La creazione di questi pacchetti di offload è controproducente quando si utilizza la replica senza binario, perché i file binari vengono serializzati nuovamente nel pacchetto quando si crea il pacchetto. L&#39;utilizzo di questi pacchetti di trasporto può essere disattivato, il che causa il trasporto del processo di scarico e del carico utile in più richieste di replica, una per ogni voce di payload. In questo modo, è possibile utilizzare i vantaggi della replica senza binario.

1. Apri la configurazione del componente *OffloadingDefaultTransporter* all’indirizzo [http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)
1. Disattivate la proprietà *Replication Package (default.Transport.contentpackage)*.

### Disattivazione del trasporto del modello di workflow {#disabling-the-transport-of-workflow-model}

Per impostazione predefinita, il flusso di lavoro *DAM Update Asset Offload* offload aggiunge il modello di workflow per chiamare il lavoratore al payload del processo. Poiché questo flusso di lavoro segue il modello predefinito di risorse *aggiornate* DAM, è possibile rimuovere il payload aggiuntivo.

Se il modello di flusso di lavoro è disabilitato dal payload del processo, accertatevi di distribuire le modifiche al modello di flusso di lavoro di riferimento utilizzando altri strumenti, ad esempio il gestore pacchetti.

Per disattivare il trasporto del modello di workflow, modificate il flusso di lavoro DAM Update Asset Offload.

1. Aprite la console del flusso di lavoro da [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).
1. Aprite la scheda Modelli.
1. Aprite il modello di flusso di lavoro DAM Update Asset Offload.
1. Aprire le proprietà del passaggio per il passaggio di offload del flusso di lavoro DAM.
1. Aprire la scheda Argomenti e deselezionare le opzioni Aggiungi modello a input e Aggiungi modello a output.
1. Salvare le modifiche apportate al modello.

### Ottimizzazione dell’intervallo di polling {#optimizing-the-polling-interval}

Lo scaricamento del flusso di lavoro è implementato utilizzando un flusso di lavoro esterno sul flusso di lavoro principale, che esegue il polling per il completamento del flusso di lavoro scaricato sul lavoratore. L’intervallo di polling predefinito per i processi del flusso di lavoro esterno è di cinque secondi.  Adobe consiglia di aumentare l’intervallo di polling del passaggio di scarico Risorse ad almeno 15 secondi per ridurre il sovraccarico di scarico sul primario.

1. Aprite la console del flusso di lavoro da [http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html).

1. Aprite la scheda Modelli.
1. Aprite il modello di flusso di lavoro DAM Update Asset Offload.
1. Aprire le proprietà del passaggio per il passaggio di offload del flusso di lavoro DAM.
1. Aprite la scheda Commons e regolate il valore della proprietà Period.
1. Salvare le modifiche apportate al modello.

## Altre risorse {#more-resources}

Questo documento è incentrato sullo scarico delle risorse. Di seguito è riportata una documentazione aggiuntiva sullo scarico:

* [Scaricamento dei processi](/help/sites-deploying/offloading.md)
* [Offload del flusso di lavoro delle risorse](/help/sites-administering/workflow-offloader.md)

