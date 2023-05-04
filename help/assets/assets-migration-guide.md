---
title: Eseguire la migrazione delle risorse in massa ad Adobe Experience Manager Assets
description: Come portare le risorse in AEM, applicare i metadati, generare rappresentazioni e attivarle per pubblicare le istanze.
contentOwner: AG
feature: Migration,Renditions,Asset Management
role: Architect,Admin
exl-id: 31da9f3d-460a-4b71-9ba0-7487f1b159cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1808'
ht-degree: 8%

---

# Guida alla migrazione delle risorse {#assets-migration-guide}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Durante la migrazione delle risorse in AEM, è necessario prendere in considerazione diversi passaggi. L’estrazione di risorse e metadati dalla propria abitazione non rientra nell’ambito di applicazione di questo documento, in quanto varia notevolmente tra le implementazioni. Questo documento descrive invece come portare queste risorse in AEM, applicarne i metadati, generare rappresentazioni e attivare o pubblicare le risorse.

## Prerequisiti {#prerequisites}

Prima di eseguire uno dei passaggi descritti di seguito, controlla e implementa le linee guida in [Suggerimenti per ottimizzare le prestazioni delle risorse](performance-tuning-guidelines.md). Molti passaggi, come la configurazione del numero massimo di processi simultanei, migliorano la stabilità e le prestazioni del server sotto carico. È difficile eseguire altri passaggi, come la configurazione dell’archivio dati file, dopo che il sistema è stato caricato con le risorse.

>[!NOTE]
>
>I seguenti strumenti di migrazione delle risorse non fanno parte di Adobe Experience Manager. L’Assistenza clienti di Adobe non supporta questi strumenti.
>
>* ACS [!DNL Experience Manager] Strumenti Tag Maker
>* ACS [!DNL Experience Manager] Strumenti Importazione risorse CSV
>* ACS Commons Bulk Workflow Manager
>* ACS Commons Fast Action Manager
>* Workflow sintetico
>
>Questo software è open source ed è coperto dalla [Licenza Apache v2](https://adobe-consulting-services.github.io/pages/license.html). Per porre una domanda o segnalare un problema, visita rispettivamente [ [!DNL Experience Manager] GitHub Issues for ACS Tools](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) e [ [!DNL Experience Manager] ACS Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Esegui migrazione a [!DNL Experience Manager] {#migrate-to-aem}

Migrazione delle risorse a [!DNL Experience Manager] richiede diversi passaggi e deve essere visualizzato come un processo graduale. Le fasi della migrazione sono le seguenti:

1. Disattiva i flussi di lavoro.
1. Caricare i tag.
1. Inserire le risorse.
1. Elabora le rappresentazioni.
1. Attiva le risorse.
1. Abilita i flussi di lavoro.

![chlimage_1-223](assets/chlimage_1-223.png)

### Disattiva flussi di lavoro {#disable-workflows}

Prima di avviare una migrazione, disattiva i moduli di avvio per `DAM Update Asset` workflow. È consigliabile acquisire tutte le risorse nel sistema ed eseguire i flussi di lavoro in batch. Se sei già attivo durante la migrazione, puoi pianificare l’esecuzione di queste attività durante le ore di inattività.

### Caricare tag {#load-tags}

È possibile che sia già attiva una tassonomia dei tag da applicare alle immagini. Strumenti come Importazione risorse CSV e la funzionalità dei profili di metadati consentono di automatizzare l’applicazione dei tag alle risorse. Prima di questo, aggiungi i tag nell’Experience Manager . La [ACS [!DNL Experience Manager] Strumenti Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) consente di popolare i tag utilizzando un foglio di calcolo di Microsoft Excel caricato nel sistema.

### Inserire risorse {#ingest-assets}

Le prestazioni e la stabilità sono fattori importanti per l’acquisizione delle risorse nel sistema. Quando carichi molti dati in Experience Manager, assicurati che il sistema funzioni bene. In questo modo è stato ridotto il tempo necessario per aggiungere i dati e si evita di sovraccaricare il sistema. Questo aiuta a prevenire gli arresti anomali del sistema, specialmente nei sistemi già in produzione.

Esistono due approcci per caricare le risorse nel sistema: un approccio basato su push tramite HTTP o un approccio basato su pull tramite le API JCR.

#### Push-through HTTP {#push-through-http}

Il team Managed Services di Adobe utilizza uno strumento chiamato Glutton per caricare i dati negli ambienti dei clienti. Glutton è una piccola applicazione Java che carica tutte le risorse da una directory in un&#39;altra directory su un [!DNL Experience Manager] istanza. Invece di Glutton, puoi anche utilizzare strumenti come gli script Perl per pubblicare le risorse nell’archivio.

Ci sono due aspetti negativi principali dell&#39;utilizzo dell&#39;approccio di spingere attraverso https:

1. Trasmetti le risorse tramite HTTP al server. Questo richiede un po&#39; di overhead ed è dispendioso in termini di tempo, allungando così il tempo necessario per eseguire la migrazione.
1. Se hai dei tag e dei metadati personalizzati da applicare alle risorse, questo approccio richiede un secondo processo personalizzato da eseguire per applicare questi metadati alle risorse una volta importati.

L’altro approccio per l’acquisizione delle risorse consiste nel estrarre le risorse dal file system locale. Tuttavia, se non è possibile ottenere un&#39;unità esterna o una condivisione di rete montata sul server per eseguire un approccio basato su pull, la pubblicazione delle risorse su HTTP è l&#39;opzione migliore.

#### Estrarre dal file system locale {#pull-from-the-local-file-system}

La [ACS [!DNL Experience Manager] Strumenti Importazione risorse CSV](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) richiama le risorse dal file system e i metadati delle risorse da un file CSV per l’importazione delle risorse. La [!DNL Experience Manager] L’API di Asset Manager viene utilizzata per importare le risorse nel sistema e applicare le proprietà dei metadati configurati. Idealmente, le risorse vengono montate sul server tramite un montaggio di file di rete o tramite un&#39;unità esterna.

Quando le attività non vengono trasmesse in rete, le prestazioni complessive migliorano notevolmente. Questo metodo è in genere il metodo più efficiente per caricare le risorse nell’archivio. Inoltre, puoi importare tutte le risorse e i metadati in un singolo passaggio, poiché lo strumento supporta l’acquisizione dei metadati. Per applicare i metadati, ad esempio utilizzando uno strumento separato, non è necessario alcun altro passaggio.

### Rendering dei processi {#process-renditions}

Dopo aver caricato le risorse nel sistema, devi elaborarle tramite il flusso di lavoro Risorsa di aggiornamento DAM per estrarre i metadati e generare rappresentazioni. Prima di eseguire questo passaggio, devi duplicare e modificare il flusso di lavoro Risorsa di aggiornamento DAM per adattarlo alle tue esigenze. Alcuni passaggi nel flusso di lavoro predefinito potrebbero non essere necessari, ad esempio la generazione di Dynamic Media Classic PTIFF o l’integrazione con il server InDesign.

Dopo aver configurato il flusso di lavoro in base alle tue esigenze, hai due opzioni per eseguirlo:

1. L&#39;approccio più semplice è [Workflow Manager di massa di ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Questo strumento ti consente di eseguire una query ed elaborare i risultati della query tramite un flusso di lavoro. Ci sono opzioni anche per l&#39;impostazione delle dimensioni batch.
1. Puoi utilizzare [ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) insieme a [Synthetic Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html) (Flussi di lavoro sintetici). Anche se questo approccio è molto più complesso, ti consente di rimuovere il sovraccarico del [!DNL Experience Manager] motore del flusso di lavoro durante l&#39;ottimizzazione dell&#39;utilizzo delle risorse del server. Inoltre, Fast Action Manager migliora ulteriormente le prestazioni monitorando dinamicamente le risorse del server e riducendo il carico posizionato sul sistema. Gli script di esempio sono stati forniti nella pagina delle funzioni di ACS Commons.

### Attivare le risorse {#activate-assets}

Per le distribuzioni con un livello di pubblicazione, devi attivare le risorse nella farm di pubblicazione. Mentre Adobe consiglia di eseguire più di una singola istanza di pubblicazione, è più efficiente replicare tutte le risorse in un’unica istanza di pubblicazione e quindi clonarla. Quando si attivano numerose risorse, potrebbe essere necessario intervenire dopo l’attivazione di una struttura ad albero. Ecco perché: Quando si attivano le attivazioni, gli elementi vengono aggiunti alla coda di eventi/lavori Sling. Dopo che le dimensioni di questa coda iniziano a superare i circa 40.000 elementi, l’elaborazione rallenta notevolmente. Dopo che la dimensione di questa coda supera i 100.000 elementi, la stabilità del sistema inizia a soffrire.

Per risolvere questo problema, puoi utilizzare il [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) per gestire la replica delle risorse. Questo funziona senza l&#39;utilizzo delle code Sling, riducendo il sovraccarico e riducendo al contempo il carico di lavoro per evitare che il server venga sovraccaricato. Un esempio di utilizzo di FAM per gestire la replica è mostrato nella pagina di documentazione della funzione.

Le altre opzioni per spostare le risorse nella farm di pubblicazione includono l’utilizzo di [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) o [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), forniti come strumenti nell’ambito di Jackrabbit. Un&#39;altra opzione è quella di utilizzare uno strumento open source per il tuo [!DNL Experience Manager] infrastruttura chiamata [Coniglio](https://github.com/TWCable/grabbit), che afferma di avere prestazioni più veloci rispetto a vlt.

Per uno di questi approcci, è necessario che le risorse nell’istanza di authoring non vengano visualizzate come attivate. Per gestire il contrassegno di queste risorse con lo stato di attivazione corretto, è inoltre necessario eseguire uno script per contrassegnare le risorse come attivate.

>[!NOTE]
>
>Adobe non mantiene o supporta Grabbit.

### Clona pubblicazione {#clone-publish}

Dopo l’attivazione delle risorse, puoi clonare l’istanza di pubblicazione per creare tutte le copie necessarie per la distribuzione. Clonare un server è abbastanza semplice, ma ci sono alcuni passaggi importanti da ricordare. Per clonare la pubblicazione:

1. Esegui il backup dell&#39;istanza sorgente e del datastore.
1. Ripristina il backup dell&#39;istanza e del datastore nel percorso di destinazione. I seguenti passaggi fanno riferimento a questa nuova istanza.
1. Eseguire una ricerca del file system in `crx-quickstart/launchpad/felix` per `sling.id`. Elimina questo file.
1. Sotto il percorso principale del datastore, individua ed elimina qualsiasi `repository-XXX` file.
1. Modifica `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` e `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config` puntare alla posizione del datastore sul nuovo ambiente.
1. Avvia l&#39;ambiente.
1. Aggiorna la configurazione di eventuali agenti di replica sugli autori per puntare alle istanze di pubblicazione corrette o agli agenti di flush del dispatcher sulla nuova istanza per puntare ai dispatcher corretti per il nuovo ambiente.

### Abilita flussi di lavoro {#enable-workflows}

Una volta completata la migrazione, i moduli di avvio per i flussi di lavoro Aggiorna risorsa DAM devono essere riabilitati per supportare la generazione di rendering e l’estrazione dei metadati per un utilizzo quotidiano del sistema.

## Migrazione delle risorse tra [!DNL Experience Manager] distribuzioni {#migrate-between-aem-instances}

Anche se non altrettanto comune, a volte è necessario migrare grandi quantità di dati da uno [!DNL Experience Manager] istanza a un altro; ad esempio, quando esegui un [!DNL Experience Manager] aggiornare, aggiornare l’hardware o eseguire la migrazione a un nuovo centro dati, ad esempio con una migrazione AMS.

In questo caso, le risorse sono già popolate con metadati e le rappresentazioni sono già generate. Puoi semplicemente concentrarti sullo spostamento delle risorse da un’istanza all’altra. Durante la migrazione tra [!DNL Experience Manager] Le istanze eseguono le seguenti operazioni:

1. Disattiva i flussi di lavoro: Poiché stai eseguendo la migrazione delle rappresentazioni insieme alle nostre risorse, vuoi disattivare i moduli di avvio dei flussi di lavoro per DAM Update Asset.

1. Esegui migrazione tag: Perché i tag sono già stati caricati nell&#39;origine [!DNL Experience Manager] ad esempio, puoi generarli in un pacchetto di contenuti e installare il pacchetto sull’istanza di destinazione.

1. Esegui migrazione risorse: Sono disponibili due strumenti consigliati per lo spostamento delle risorse da uno [!DNL Experience Manager] istanza a un altro:

   * **Vault Remote Copy** oppure `vlt rcp`, consente di utilizzare vlt in una rete. Puoi specificare una directory di origine e di destinazione e vlt scarica tutti i dati del repository da un&#39;istanza e li carica nell&#39;altra. Vlt rcp è documentato in [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Coniglio** è uno strumento di sincronizzazione dei contenuti open source sviluppato da Time Warner Cable per i [!DNL Experience Manager] implementazione. Poiché utilizza flussi di dati continui, rispetto a vlt rcp, ha una latenza inferiore e dichiara un miglioramento della velocità da due a dieci volte più veloce di vlt rcp. Grabbit supporta anche la sincronizzazione solo del contenuto delta, che consente di sincronizzare le modifiche dopo il completamento di un passaggio di migrazione iniziale.

1. Attivare le risorse: Segui le istruzioni per [attivazione delle risorse](#activate-assets) documentato per la migrazione iniziale a AEM.

1. Clona pubblicazione: Come per una nuova migrazione, il caricamento di una singola istanza di pubblicazione e la clonazione sono più efficienti dell’attivazione del contenuto su entrambi i nodi. Vedi [Clonazione di pubblicazione.](#clone-publish)

1. Abilitazione dei flussi di lavoro: Dopo aver completato la migrazione, riattiva i moduli di avvio per i flussi di lavoro Aggiorna risorsa DAM per supportare la generazione del rendering e l’estrazione dei metadati per un utilizzo quotidiano del sistema.
