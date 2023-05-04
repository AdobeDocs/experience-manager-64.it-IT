---
title: Integrare [!DNL Experience Manager] Risorse con Adobe InDesign Server
description: Scopri come integrare [!DNL Experience Manager] Risorse con InDesign Server.
contentOwner: AG
feature: Publishing
role: Admin
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 4%

---

# Integrare le risorse con Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets utilizza:

* Un proxy per distribuire il carico di alcune attività di elaborazione. Un proxy è un [!DNL Experience Manager] istanza che comunica con un proxy worker per eseguire un&#39;attività specifica e altre [!DNL Experience Manager] per fornire i risultati.
* Un processo di lavoro proxy per definire e gestire un’attività specifica.

Questi possono coprire un&#39;ampia gamma di compiti; ad esempio, l’utilizzo di un Adobe InDesign Server per elaborare i file.

Per caricare completamente i file in [!DNL Experience Manager] Vengono utilizzate le risorse create con Adobe InDesign con un proxy. Questo utilizza un proxy worker per comunicare con Adobe InDesign Server, dove [script](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) vengono eseguiti per estrarre i metadati e generare diverse rappresentazioni per [!DNL Experience Manager] Risorse. Il proxy worker abilita la comunicazione bidirezionale tra InDesign Server e [!DNL Experience Manager] istanze in una configurazione cloud.

>[!NOTE]
>
>Adobe InDesign è dotato di due prodotti:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Consente di progettare layout di pagina per la stampa e/o la distribuzione digitale.
>
>* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Questo motore consente di creare in modo programmatico documenti automatizzati in base a ciò che hai creato con InDesign. Opera come servizio che offre un’interfaccia ai suoi [ExtendScript](https://www.adobe.com/devnet/scripting.html) motore.\
   >  Gli script vengono scritti in ExtendScript in modo analogo a JavaScript. Per informazioni sugli script Adobe InDesign, consulta [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>


## Come funziona l’estrazione {#how-the-extraction-works}

InDesign Server può essere integrato con [!DNL Experience Manager] Risorse in modo che i file creati con InDesign ( `.indd`) può essere caricata, possono essere generate rappresentazioni, *tutto* file multimediali estratti (ad esempio, video) e memorizzati come risorse:

>[!NOTE]
>
>Versioni precedenti di [!DNL Experience Manager] sono stati in grado di estrarre XMP e la miniatura, ora tutti i supporti possono essere estratti.

1. Carica il `.indd` file a [!DNL Experience Manager] Risorse.
1. Un framework invia script di comando ad InDesign Server tramite SOAP (Simple Object Access Protocol).

   Questo script di comando:

   * Recupera il `.indd` file.
   * Esegui comandi di InDesign Server:

      * Vengono estratti la struttura, il testo e tutti i file multimediali.
      * Vengono generati rendering di PDF e JPG.
      * Vengono generati rendering HTML e IDML.
   * Ripubblicare i file risultanti in [!DNL Experience Manager] Risorse.

   >[!NOTE]
   >
   >IDML è un formato basato su XML che esegue il rendering *tutto* nel file InDesign. Viene memorizzato come pacchetto compresso utilizzando [ZIP](https://www.techterms.com/definition/zip) compressione.
   >
   >Vedi [Adobe InDesign Interchange Formats INX e IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) per ulteriori informazioni.

   >[!CAUTION]
   >
   >Se InDesign Server non è installato o non è configurato, puoi comunque caricare un `.indd` file in [!DNL Experience Manager]. Tuttavia, le rappresentazioni generate saranno limitate a `png` e `jpeg`, non puoi generare `html`, `idml` o le rappresentazioni della pagina.

1. Dopo la generazione di estrazione e rendering:

   * La struttura viene replicata in un `cq:Page` (tipo di rendering).
   * Il testo e i file estratti vengono memorizzati in [!DNL Experience Manager] Risorse.
   * Tutte le rappresentazioni sono memorizzate in [!DNL Experience Manager] Risorse, nella risorsa stessa.

## Integrazione di InDesign Server con [!DNL Experience Manager] {#integrating-the-indesign-server-with-aem}

Per integrare InDesign Server con [!DNL Experience Manager] Risorse e dopo aver configurato il proxy, devi:

1. [Installare InDesign Server](#installing-the-indesign-server).
1. Se necessario, [configura [!DNL Experience Manager] Flusso di lavoro delle risorse](#configuring-the-aem-assets-workflow).

   Ciò è necessario solo se i valori predefiniti non sono appropriati per l’istanza.

1. Configura un [proxy worker per InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installazione di InDesign Server {#installing-the-indesign-server}

Per installare e avviare InDesign Server da utilizzare con [!DNL Experience Manager]:

1. Scarica e installa Adobe InDesign Server.

   >[!NOTE]
   >
   >InDesign Server (CS6 e versioni successive).

1. Se necessario, puoi personalizzare la configurazione dell’istanza di InDesign Server.

1. Dalla riga di comando, avvia il server:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Verrà avviato il server con il plug-in SOAP in ascolto sulla porta 8080. Tutti i messaggi e gli output di log vengono scritti direttamente nella finestra dei comandi.

   >[!NOTE]
   >
   >Se si desidera salvare i messaggi di output in un file, utilizzare il reindirizzamento; ad esempio, in Windows:
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configurazione della [!DNL Experience Manager] Flusso di lavoro delle risorse {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager] Assets dispone di un flusso di lavoro preconfigurato **Risorsa di aggiornamento DAM**, che prevede diversi passaggi di processo specifici per InDesign:

* [Estrazione file multimediali](#media-extraction)
* [Estrazione pagina](#page-extraction)

Questo flusso di lavoro è configurato con valori predefiniti che possono essere adattati per la configurazione sulle varie istanze di authoring (si tratta di un flusso di lavoro standard, quindi ulteriori informazioni sono disponibili in [Modifica di un flusso di lavoro](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Se si utilizzano i valori predefiniti (inclusa la porta SOAP), non è necessaria alcuna configurazione.

Dopo la configurazione, caricamento dei file InDesign in [!DNL Experience Manager] Le risorse (con uno dei metodi consueti) attiveranno il flusso di lavoro necessario per elaborare la risorsa e preparare le varie rappresentazioni. Verifica la configurazione caricando un `.indd` file in [!DNL Experience Manager] Risorse per confermare che visualizzi le diverse rappresentazioni create da ID in `<*your_asset*>.indd/Renditions`

#### Estrazione file multimediali {#media-extraction}

Questo passaggio controlla l’estrazione dei file multimediali dal `.indd` file.

Per personalizzare, puoi modificare la scheda **[!UICONTROL Arguments (Argomenti)]** del passaggio **[!UICONTROL Estrazione file multimediali]**.

![Argomenti di estrazione file multimediali e percorsi di script](assets/media_extraction_arguments_scripts.png)

Argomenti di estrazione file multimediali e percorsi di script

* **Libreria ExtendScript**: Si tratta di una semplice libreria di metodi http get/post, necessaria per gli altri script.

* **Estendi script**: Qui è possibile specificare diverse combinazioni di script. Se si desidera che gli script personalizzati vengano eseguiti in InDesign Server, salvare gli script in `/apps/settings/dam/indesign/scripts`.

   Per informazioni sugli script di InDesign, consulta [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Non modificare la libreria ExtendScript. La libreria fornisce la funzionalità HTTP necessaria per comunicare con Sling. Questa impostazione specifica la libreria da inviare ad Adobe InDesign Server per l’utilizzo in tale ambiente.

La `ThumbnailExport.jsx` lo script eseguito dal passaggio del flusso di lavoro Estrazione file multimediali genera un rendering delle miniature in formato JPG. Questo rendering viene utilizzato dal passaggio del flusso di lavoro Elabora miniature per generare le rappresentazioni statiche richieste da [!DNL Experience Manager].

Puoi configurare il passaggio del flusso di lavoro Elabora miniature per generare rappresentazioni statiche con dimensioni diverse. Assicurati di non rimuovere i valori predefiniti, perché sono richiesti da [!DNL Experience Manager] Interfaccia utente Assets. Infine, il passaggio del flusso di lavoro Elimina rappresentazione anteprima immagine rimuove il rendering delle miniature .jpg, in quanto non è più necessario.

#### Estrazione pagina {#page-extraction}

Questo crea un [!DNL Experience Manager] dagli elementi estratti. Un gestore estrazione viene utilizzato per estrarre dati da un rendering (attualmente HTML o IDML). Questi dati vengono quindi utilizzati per creare una pagina utilizzando PageBuilder.

Per personalizzare, è possibile modificare la scheda **[!UICONTROL Argomenti]** del passaggio **Estrazione pagina**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Gestore estrazione pagina**: Dall’elenco a discesa, seleziona il gestore da utilizzare. Un gestore estrazione opera su un rendering specifico, scelto da un `RenditionPicker` correlato (consulta l’API `ExtractionHandler`). Per impostazione predefinita, è disponibile il gestore estrazione esportazione IDML. Opera sulla `IDML` rendering generato nel passaggio MediaExtract.

* **Nome pagina**: Specifica il nome da assegnare alla pagina risultante. Se lasciato vuoto, il nome è &quot;page&quot; (o un derivato, se &quot;page&quot; esiste già).

* **Titolo pagina**: Specifica il titolo da assegnare alla pagina risultante.

* **Percorso principale pagina**: Percorso della posizione principale della pagina risultante. Se lasciato vuoto, viene utilizzato il nodo contenente le rappresentazioni della risorsa.

* **Modello di pagina**: Modello da utilizzare per la generazione della pagina risultante.

* **Progettazione pagina**: Progettazione di pagina da utilizzare per la generazione della pagina risultante.

### Configurazione del proxy Worker per InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Il processo di lavoro risiede nell&#39;istanza proxy.

1. Nella console Strumenti , espandi **[!UICONTROL Configurazioni Cloud Services]** nel riquadro a sinistra. Quindi espandi **[!UICONTROL Configurazione proxy cloud]**.

1. Per aprire la configurazione, fai doppio clic su **[!UICONTROL IDS worker]**.

1. Fai clic su **[!UICONTROL Modifica]** per aprire la finestra di dialogo di configurazione e definire le impostazioni richieste:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Pool IDS**: Endpoint SOAP da utilizzare per la comunicazione con InDesign Server. È possibile aggiungere, rimuovere e ordinare gli elementi necessari.

1. Fai clic su **[!UICONTROL OK]** da salvare.

### Configurazione di Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

Se l’InDesign Server e [!DNL Experience Manager] sono su host diversi o una o entrambe le applicazioni non funzionano sulle porte predefinite, configura **Day CQ Link Externalizer** per impostare il nome host, la porta e il percorso del contenuto per InDesign Server.

1. Accedere a Configuration Manager dall&#39;URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Individua la configurazione **[!UICONTROL Day CQ Link Externalizer]**. Fai clic su **[!UICONTROL Modifica]** per aprire.
1. Le impostazioni di Link Externalizer consentono di creare URL completi per [!DNL Experience Manager] e per [!DNL InDesign Server]. Utilizzo **[!UICONTROL Domini]** campo per specificare il nome host e il percorso contestuale per il [!DNL Adobe InDesign Server]. Seguire le istruzioni visualizzate. Fai clic su **[!UICONTROL Salva]**.

   ![Impostazioni del collegamento esternalizzatore](assets/link-externalizer-config.png)

### Abilitazione dell’elaborazione parallela dei processi per gli InDesign Server {#enabling-parallel-job-processing-for-indesign-server}

È ora possibile abilitare l&#39;elaborazione dei processi paralleli per gli ID.

Innanzitutto devi determinare il numero massimo di processi paralleli ( `x`) un InDesign Server può elaborare:

* Su un singolo computer multiprocessore, il numero massimo di processi paralleli (x) che un InDesign Server può elaborare è inferiore di uno al numero di processori che eseguono ID.
* Quando si esegue l&#39;ID su più computer è necessario contare il numero totale di processori disponibili (ossia su tutti i computer), quindi sottrarre il numero totale di macchine.

Per configurare il numero di processi IDS paralleli:

1. Apri **[!UICONTROL Configurazioni]** scheda della console Felix; ad esempio:

   `http://localhost:4502/system/console/configMgr`

1. Seleziona la coda di elaborazione IDS in:

   `Apache Sling Job Queue Configuration`

1. Imposta:

   * **[!UICONTROL Tipo]** - `Parallel`
   * **[!UICONTROL Processi paralleli massimi]** - `<*x*>` (come calcolato in precedenza)

1. Salva queste modifiche.
1. Per abilitare il supporto per più sessioni per Adobe CS6 e versioni successive, controlla la `enable.multisession.name` spunta sotto `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Crea un [pool di &lt; `*x*>` I processi di lavoro IDS aggiungendo endpoint SOAP alla configurazione di IDS Worker](#configuring-the-proxy-worker-for-indesign-server).

   Se sono presenti più computer che eseguono InDesign Server, aggiungere endpoint SOAP (numero di processori per computer -1) per ogni computer.

   >[!NOTE]
   >
   >Quando si lavora con un pool di lavoratori, è possibile abilitare l&#39;elenco Bloccati di lavoratori IDS.
   >
   >Per farlo, abilita la casella di controllo &quot;enable.try.name&quot;, sotto la sezione `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configurazione, che abilita il recupero del processo IDS.
   >
   >Inoltre, sotto `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configurazione, imposta un valore positivo per `max.errors.to.blacklist` parametro che determina il numero di recuperi di processi prima di associare un ID dall&#39;elenco dei gestori di processi
   >
   >Per impostazione predefinita, dopo il`retry.interval.to.whitelist.name`) in minuti il processo di lavoro IDS viene riconvalidato. Se il lavoratore viene trovato online, viene rimosso dall&#39;elenco Bloccati.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Abilita il supporto per il server Adobe InDesign 10.0 o versione successiva {#enabling-support-for-indesign-server-or-higher}

Per il server InDesign 10.0 o versione successiva, esegui i seguenti passaggi per abilitare il supporto per più sessioni.

1. Apri Configuration Manager dal [!DNL Assets] istanza `https://[aem_server]:[port]/system/console/configMgr`.
1. Modificare la configurazione `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Seleziona **[!UICONTROL ids.cc.enable]** e fai clic su **[!UICONTROL Salva]**.

>[!NOTE]
>
>Per [!DNL InDesign Server] integrazione con [!DNL Assets], utilizza un processore multi-core perché la funzionalità di supporto delle sessioni necessaria per l&#39;integrazione non è supportata sui sistemi single-core.

## Configurare le credenziali di Experience Manager {#configure-aem-credentials}

È possibile modificare le credenziali di amministratore predefinite (nome utente e password) per accedere al server InDesign dal proprio [!DNL Experience Manager] senza interrompere l’integrazione con il server Adobe InDesign.

1. Passa a `/etc/cloudservices/proxy.html`.
1. Nella finestra di dialogo , specifica il nuovo nome utente e la nuova password.
1. Salva le credenziali.
