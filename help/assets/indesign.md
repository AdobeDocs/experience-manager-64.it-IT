---
title: Integrare  AEM Assets con  Adobe InDesign Server
description: Scoprite come integrare  AEM Assets con  InDesign Server.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 5%

---


# Integrare  AEM Assets con  Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager (AEM) Assets utilizza:

* Un proxy per distribuire il carico di alcune attività di elaborazione. Un proxy è un&#39;istanza AEM che comunica con un lavoratore proxy per eseguire un&#39;attività specifica e altre istanze AEM per fornire i risultati.
* Un lavoratore proxy per definire e gestire un&#39;attività specifica.

Questi possono coprire un&#39;ampia gamma di compiti; ad esempio, l&#39;utilizzo di un Adobe InDesign Server  per elaborare i file.

Per caricare completamente i file in  AEM Assets creati con  Adobe InDesign, viene utilizzato un proxy. Questo utilizza un proxy worker per comunicare con l&#39;Adobe InDesign Server , dove [gli script](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) vengono eseguiti per estrarre i metadati e generare diverse rappresentazioni per  AEM Assets. Il lavoratore proxy abilita la comunicazione bidirezionale tra il InDesign Server  e le istanze AEM in una configurazione cloud.

>[!NOTE]
>
> Adobe InDesign è disponibile come due prodotti:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Questo consente di progettare layout di pagina per la stampa e/o la distribuzione digitale.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Questo motore consente di creare a livello di programmazione documenti automatizzati basati su ciò che è stato creato con  InDesign. Funziona come un servizio che offre un&#39;interfaccia al suo [motore ExtendScript](https://www.adobe.com/devnet/scripting.html) .\
   >  Gli script sono scritti in  ExtendScript, simile a javascript. Per informazioni sugli script Indesign, vedere [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>



## Come funziona l&#39;estrazione {#how-the-extraction-works}

Il InDesign Server  può essere integrato con  AEM Assets in modo che i file creati con  InDesign ( `.indd`) possano essere caricati, generati rappresentazioni, *tutti* i file multimediali estratti (ad esempio, video) e memorizzati come risorse:

>[!NOTE]
>
>Le versioni precedenti di AEM erano in grado di estrarre XMP e la miniatura, ora tutti i supporti possono essere estratti.

1. Caricate il `.indd` file in  AEM Assets.
1. Un framework invia script di comando al InDesign Server  tramite SOAP (Simple Object Access Protocol).

   Questo script di comando:

   * Recuperate il `.indd` file.
   * Esegui comandi  InDesign Server:

      * Vengono estratti la struttura, il testo e tutti i file multimediali.
      * Vengono generate rappresentazioni PDF e JPG.
      * Vengono generate rappresentazioni HTML e IDML.
   * Pubblicare nuovamente i file risultanti su  AEM Assets.

   >[!NOTE]
   >
   >IDML è un formato basato su XML che esegue il rendering di *tutti* gli elementi presenti nel file InDesign . Viene memorizzato come pacchetto compresso utilizzando la compressione [Zip](https://www.techterms.com/definition/zip) .
   >
   >Per ulteriori informazioni, consulta [formati di interscambio Adobe InDesign INX e IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) .

   >[!CAUTION]
   >
   >Se il InDesign Server  non è installato o non è configurato, potete comunque caricare un `.indd` file in AEM. Tuttavia, le rappresentazioni generate saranno limitate a `png` e `jpeg`, non sarà possibile generare rappresentazioni `html``idml` di pagina.

1. Dopo la generazione di estrazione e rappresentazione:

   * La struttura viene replicata in un `cq:Page` (tipo di rappresentazione).
   * Il testo e i file estratti vengono memorizzati in  AEM Assets.
   * Tutte le rappresentazioni sono memorizzate in  AEM Assets, nella risorsa stessa.

## Integrazione del InDesign Server  con AEM {#integrating-the-indesign-server-with-aem}

Per integrare il InDesign Server  per l&#39;uso con  AEM Assets e dopo aver configurato il proxy, è necessario:

1. [Installare il InDesign Server](#installing-the-indesign-server).
1. Se necessario, [configurate il  AEM Assets Workflow](#configuring-the-aem-assets-workflow).

   Ciò è necessario solo se i valori predefiniti non sono appropriati per l’istanza in uso.

1. Configurare un lavoratore [proxy per il InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installazione del InDesign Server  {#installing-the-indesign-server}

Per installare e avviare il InDesign Server  da utilizzare con AEM:

1. Scaricate e installate il  Adobe InDesign Server.

   >[!NOTE]
   >
   > InDesign Server (CS6 e versioni successive).

1. Se necessario, potete personalizzare la configurazione dell’istanza di InDesign Server .

1. Dalla riga di comando, avviate il server:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Verrà avviato il server con il plug-in SOAP in ascolto sulla porta 8080. Tutti i messaggi e gli output del registro vengono scritti direttamente nella finestra del comando.

   >[!NOTE]
   >
   >Se si desidera salvare i messaggi di output in un file, utilizzare redirection; ad esempio, in Windows:
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configurazione del flusso di lavoro AEM Assets  {#configuring-the-aem-assets-workflow}

AEM Assets has a pre-configured workflow **DAM Update Asset**, that has several process steps specifically for InDesign:

* [Estrazione file multimediali](#media-extraction)
* [Estrazione pagina](#page-extraction)

Questo flusso di lavoro è configurato con valori predefiniti che possono essere adattati per la configurazione nelle varie istanze di authoring (si tratta di un flusso di lavoro standard, per cui ulteriori informazioni sono disponibili in [Modifica di un flusso di lavoro](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Se si utilizzano i valori predefiniti (inclusa la porta SOAP), non è necessaria alcuna configurazione.

Dopo l’impostazione, il caricamento di file  InDesign in  AEM Assets (con uno dei metodi consueti) attiverà il flusso di lavoro necessario per elaborare la risorsa e preparare le varie rappresentazioni. Verificare la configurazione caricando un `.indd` file in  AEM Assets per confermare che sono visualizzate le diverse rappresentazioni create da IDS in `<*your_asset*>.indd/Renditions`

#### Estrazione file multimediali {#media-extraction}

Questo passaggio controlla l’estrazione dei file multimediali dal `.indd` file.

Per personalizzare, puoi modificare la scheda **[!UICONTROL Arguments (Argomenti)]** del passaggio **[!UICONTROL Estrazione file multimediali]**.

![Argomenti di estrazione dei supporti e percorsi di script](assets/media_extraction_arguments_scripts.png)

Argomenti di estrazione dei supporti e percorsi di script

* **Libreria** ExtendScript : Si tratta di una semplice libreria di metodi http get/post, richiesta dagli altri script.

* **Estendi script**: Qui è possibile specificare diverse combinazioni di script. Se si desidera che gli script personalizzati siano eseguiti sul InDesign Server , salvare gli script in `/apps/settings/dam/indesign/scripts`.

   Per informazioni sugli script Indesign, vedere [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Non modificare la libreria ExtendScript. La libreria fornisce la funzionalità HTTP necessaria per comunicare con Sling. Questa impostazione specifica la libreria da inviare all&#39;Adobe InDesign Server  per l&#39;utilizzo.

Lo `ThumbnailExport.jsx` script eseguito dal passaggio del flusso di lavoro Estrazione file multimediali genera una rappresentazione in miniatura in formato .jpg. Questa rappresentazione viene utilizzata dal passaggio del flusso di lavoro Miniature di processo per generare le rappresentazioni statiche richieste da AEM.

You can configure the Process Thumbnails workflow step to generate static renditions at different sizes. Accertatevi di non rimuovere i valori predefiniti, in quanto sono richiesti dall’interfaccia  di AEM Assets. Infine, il passaggio del flusso di lavoro Elimina rappresentazione anteprima immagine rimuove la rappresentazione in miniatura .jpg, in quanto non è più necessaria.

#### Estrazione pagina {#page-extraction}

Viene creata una pagina AEM dagli elementi estratti. Un gestore di estrazione viene utilizzato per estrarre i dati da una rappresentazione (attualmente HTML o IDML). Questi dati vengono quindi utilizzati per creare una pagina con PageBuilder.

Per personalizzare, è possibile modificare la scheda **[!UICONTROL Argomenti]** del passaggio **Estrazione pagina**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Gestore** estrazione pagina: Dall&#39;elenco a discesa, selezionare il gestore che si desidera utilizzare. Un gestore estrazione opera su un rendering specifico, scelto da un `RenditionPicker` correlato (consulta l’API `ExtractionHandler`). Per impostazione predefinita, è disponibile il gestore estrazione esportazione IDML. Funziona sulla `IDML` rappresentazione generata nel passaggio MediaExtract.

* **Nome** pagina: Specificate il nome che desiderate assegnare alla pagina risultante. Se lasciato vuoto, il nome è &quot;page&quot; (o un derivato, se &quot;page&quot; esiste già).

* **Titolo** pagina: Specificate il titolo che desiderate assegnare alla pagina risultante.

* **Percorso** directory principale pagina: Percorso della posizione principale della pagina risultante. Se lasciato vuoto, viene utilizzato il nodo che contiene le rappresentazioni della risorsa.

* **Modello** pagina: Modello da utilizzare per la generazione della pagina risultante.

* **Progettazione** pagina: Struttura della pagina da utilizzare per la generazione della pagina risultante.

### Configurazione del Proxy Worker per  InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Il lavoratore risiede nell&#39;istanza proxy.

1. Nella console Strumenti, espandete Configurazioni **** Cloud Services nel riquadro a sinistra. Quindi espandete Configurazione **[!UICONTROL proxy]** Cloud.

1. Per aprire la configurazione, fai doppio clic su **[!UICONTROL IDS worker]**.

1. Fate clic su **[!UICONTROL Modifica]** per aprire la finestra di dialogo di configurazione e definire le impostazioni richieste:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Pool** IDS: Endpoint SOAP da utilizzare per la comunicazione con il InDesign Server . È possibile aggiungere, rimuovere e ordinare gli elementi necessari.

1. Fate clic su **[!UICONTROL OK]** per salvare. 

### Configurazione di Day CQ Link Externalizer  {#configuring-day-cq-link-externalizer}

If the InDesign server and AEM run on different hosts or either or both these applications do not run on default ports, configure **Day CQ Link Externalizer** to set the host name, port, and content path for the InDesign server.

1. Access Configuration Manager at the URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Individua la configurazione **[!UICONTROL Day CQ Link Externalizer]** e fai clic sull’icona **[!UICONTROL Modifica]** per aprirla.
1. Specify the host name and context path for the Indesign server and click **[!UICONTROL Save]**.

   ![chlimage_1-290](assets/chlimage_1-290.png)

### Enabling Parallel Job Processing for InDesign Server(s) {#enabling-parallel-job-processing-for-indesign-server-s}

You can now enable parallel job processing for IDS.

First you need to determine the maximum number of parallel jobs ( `x`) an InDesign Server can process:

* On a single multiprocessor machine, the maximum number of parallel jobs (x) that an InDesign Server can process is one less than the number of processors running IDS.
* Quando si esegue IDS su più computer è necessario contare il numero totale di processori disponibili (ossia su tutti i computer), quindi sottrarre il numero totale di computer.

Per configurare il numero di processi IDS paralleli:

1. Open the **[!UICONTROL Configurations]** tab of the Felix Console; for example:

   `http://localhost:4502/system/console/configMgr`

1. Selezionate la coda di elaborazione IDS in:

   `Apache Sling Job Queue Configuration`

1. Imposta:

   * **[!UICONTROL Tipo]** - `Parallel`
   * **[!UICONTROL Processi]** paralleli massimi - `<*x*>` (come calcolato sopra)

1. Salvate queste modifiche.
1. Per abilitare il supporto per più sessioni per  Adobe CS6 e versioni successive, selezionate la `enable.multisession.name` casella di controllo in `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Create un [pool di &lt; `*x*>` IDS worker aggiungendo endpoint SOAP alla configurazione](#configuring-the-proxy-worker-for-indesign-server)IDS Worker.

   Se sono presenti più computer che eseguono  InDesign Server, aggiungere endpoint SOAP (numero di processori per computer -1) per ogni computer.

   >[!NOTE]
   >
   >Quando si lavora con un pool di lavoratori, è possibile abilitare  elenco Bloccati di lavoratori IDS.
   >
   >A tale scopo, abilitare la casella di controllo &quot;enable.try.name&quot; nella `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configurazione, che consente di recuperare i processi IDS.
   >
   >Inoltre, nella `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configurazione, impostare un valore positivo per il `max.errors.to.blacklist` parametro che determina il numero di recuperi di processi prima di barrare un ID dall&#39;elenco dei gestori di processi
   >
   >Per impostazione predefinita, dopo il tempo configurabile (`retry.interval.to.whitelist.name`) in minuti, il lavoratore IDS viene riconvalidato. Se il lavoratore viene trovato online, viene rimosso dal elenco Bloccati .

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Supporto per  server Adobe InDesign 10.0 o versione successiva {#enabling-support-for-indesign-server-or-higher}

Per  server InDesign 10.0 o versione successiva, eseguite i seguenti passaggi per abilitare il supporto per più sessioni.

1. Aprire Gestione configurazione dall’ [!DNL Assets] istanza `https://[aem_server]:[port]/system/console/configMgr`.
1. Modificate la configurazione `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selezionate **[!UICONTROL ids.cc.enable]** e fate clic su **[!UICONTROL Salva]**.

>[!NOTE]
>
>Per [!DNL InDesign Server] l&#39;integrazione con [!DNL Assets], utilizzate un processore multi-core perché la funzione di supporto delle sessioni necessaria per l&#39;integrazione non è supportata nei sistemi single core.

## Configurare  credenziali Experience Manager {#configure-aem-credentials}

Potete modificare le credenziali di amministratore predefinite (nome utente e password) per accedere al server di InDesign  dall&#39;istanza AEM senza interrompere l&#39;integrazione con il server  Adobe InDesign.

1. Passa a `/etc/cloudservices/proxy.html`.
1. Nella finestra di dialogo, specificate il nuovo nome utente e la nuova password.
1. Salvare le credenziali.
