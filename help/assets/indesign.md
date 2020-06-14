---
title: Integrare AEM Assets con Adobe InDesign Server
description: Scopri come integrare AEM Assets con InDesign Server.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 77c62a8f2ca50f8aaff556a6848fabaee71017ce
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 5%

---


# Integrare AEM Assets con Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

Risorse Adobe Experience Manager (AEM) utilizza:

* Un proxy per distribuire il carico di alcune attività di elaborazione. Un proxy è un&#39;istanza di AEM che comunica con un proxy worker per eseguire un&#39;attività specifica, e altre istanze di AEM per fornire i risultati.
* Un lavoratore proxy per definire e gestire un&#39;attività specifica.

Questi possono coprire un&#39;ampia gamma di compiti; ad esempio, l&#39;utilizzo di Adobe InDesign Server per elaborare i file.

Per caricare completamente i file in Risorse AEM che avete creato con Adobe InDesign, viene utilizzato un proxy. Questo utilizza un lavoratore proxy per comunicare con Adobe InDesign Server, dove [gli script](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) vengono eseguiti per estrarre i metadati e generare diverse rappresentazioni per Risorse AEM. Il lavoratore proxy abilita la comunicazione bidirezionale tra InDesign Server e le istanze AEM in una configurazione cloud.

>[!NOTE]
>
>Adobe InDesign è dotato di due prodotti:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Questo consente di progettare layout di pagina per la stampa e/o la distribuzione digitale.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Questo motore consente di creare a livello di programmazione documenti automatizzati basati su ciò che avete creato con InDesign. Funziona come un servizio che offre un&#39;interfaccia al suo motore [ExtendScript](https://www.adobe.com/devnet/scripting.html) .\
   >  Gli script sono scritti in ExtendScript, simile a javascript. Per informazioni sugli script Indesign, vedere [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>



## Come funziona l&#39;estrazione {#how-the-extraction-works}

Il server InDesign può essere integrato con Risorse AEM in modo che i file creati con InDesign ( `.indd`) possano essere caricati, generati rappresentazioni, *tutti* i file multimediali estratti (ad esempio, video) e memorizzati come risorse:

>[!NOTE]
>
>Nelle versioni precedenti di AEM era possibile estrarre XMP e la miniatura, ora è possibile estrarre tutti i contenuti multimediali.

1. Carica il `.indd` file in Risorse AEM.
1. Un framework invia script di comando a InDesign Server tramite SOAP (Simple Object Access Protocol).

   Questo script di comando:

   * Recuperate il `.indd` file.
   * Eseguite i comandi di InDesign Server:

      * Vengono estratti la struttura, il testo e tutti i file multimediali.
      * Vengono generate rappresentazioni PDF e JPG.
      * Vengono generate rappresentazioni HTML e IDML.
   * Ripubblica i file risultanti in Risorse AEM.
   >[!NOTE]
   >
   >IDML è un formato basato su XML che esegue il rendering di *tutto* il contenuto del file InDesign. Viene memorizzato come pacchetto compresso utilizzando la compressione [Zip](https://www.techterms.com/definition/zip) .
   >
   >Per ulteriori informazioni, consultate [Adobe InDesign Interchange Formats INX e IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) .

   >[!CAUTION]
   >
   >Se InDesign Server non è installato o non è configurato, potete comunque caricare un `.indd` file in AEM. Tuttavia, le rappresentazioni generate saranno limitate a `png` e `jpeg`, non sarà possibile generare rappresentazioni `html``idml` di pagina.

1. Dopo la generazione di estrazione e rappresentazione:

   * La struttura viene replicata in un `cq:Page` (tipo di rappresentazione).
   * Il testo e i file estratti sono memorizzati in AEM Assets.
   * Tutte le rappresentazioni sono memorizzate in Risorse AEM, nella risorsa stessa.

## Integrazione di InDesign Server con AEM {#integrating-the-indesign-server-with-aem}

Per integrare InDesign Server per l’utilizzo con Risorse AEM e dopo aver configurato il proxy, è necessario:

1. [Installate InDesign Server](#installing-the-indesign-server).
1. Se necessario, [configura il flusso di lavoro](#configuring-the-aem-assets-workflow)Risorse AEM.

   Ciò è necessario solo se i valori predefiniti non sono appropriati per l’istanza in uso.

1. Configurate un lavoratore [proxy per InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installazione di InDesign Server {#installing-the-indesign-server}

Per installare e avviare InDesign Server da usare con AEM:

1. Scaricate e installate Adobe InDesign Server.

   >[!NOTE]
   >
   >InDesign Server (CS6 e versioni successive).

1. Se necessario, potete personalizzare la configurazione dell&#39;istanza InDesign Server.

1. Dalla riga di comando, avviate il server:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Verrà avviato il server con il plug-in SOAP in ascolto sulla porta 8080. Tutti i messaggi e gli output del registro vengono scritti direttamente nella finestra del comando.

   >[!NOTE]
   >
   >Se si desidera salvare i messaggi di output in un file, utilizzare redirection; ad esempio, in Windows:
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configurazione del flusso di lavoro Risorse AEM {#configuring-the-aem-assets-workflow}

AEM Assets has a pre-configured workflow **DAM Update Asset**, that has several process steps specifically for InDesign:

* [Estrazione file multimediali](#media-extraction)
* [Estrazione pagina](#page-extraction)

Questo flusso di lavoro è configurato con valori predefiniti che possono essere adattati per la configurazione nelle varie istanze di authoring (si tratta di un flusso di lavoro standard, per cui ulteriori informazioni sono disponibili in [Modifica di un flusso di lavoro](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Se si utilizzano i valori predefiniti (inclusa la porta SOAP), non è necessaria alcuna configurazione.

Dopo l’impostazione, il caricamento di file InDesign in Risorse AEM (con uno dei metodi più comuni) attiverà il flusso di lavoro necessario per elaborare la risorsa e preparare le varie rappresentazioni. Verifica la configurazione caricando un `.indd` file in Risorse AEM per confermare la visualizzazione delle diverse rappresentazioni create da IDS in `<*your_asset*>.indd/Renditions`

#### Estrazione file multimediali {#media-extraction}

Questo passaggio controlla l’estrazione dei file multimediali dal `.indd` file.

Per personalizzare, puoi modificare la scheda **[!UICONTROL Arguments (Argomenti)]** del passaggio **[!UICONTROL Estrazione file multimediali]**.

![Argomenti di estrazione dei supporti e percorsi di script](assets/media_extraction_arguments_scripts.png)

Argomenti di estrazione dei supporti e percorsi di script

* **Libreria** ExtendScript: Si tratta di una semplice libreria di metodi http get/post, richiesta dagli altri script.

* **Estendi script**: Qui è possibile specificare diverse combinazioni di script. Se desiderate che gli script personalizzati vengano eseguiti in InDesign Server, salvate gli script in `/apps/settings/dam/indesign/scripts`.

   Per informazioni sugli script Indesign, vedere [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Non modificare la libreria ExtendScript. La libreria fornisce la funzionalità HTTP necessaria per comunicare con Sling. Questa impostazione specifica la libreria da inviare ad Adobe InDesign Server per l&#39;utilizzo in tale ambiente.

Lo `ThumbnailExport.jsx` script eseguito dal passaggio del flusso di lavoro Estrazione file multimediali genera una rappresentazione in miniatura in formato .jpg. Questa rappresentazione viene utilizzata dal passaggio del flusso di lavoro Miniature di processo per generare le rappresentazioni statiche richieste da AEM.

Potete configurare il passaggio del flusso di lavoro Miniature di processo per generare rappresentazioni statiche di dimensioni diverse. Assicurati di non rimuovere i valori predefiniti, perché sono richiesti dall’interfaccia utente di Risorse AEM. Infine, il passaggio del flusso di lavoro Elimina rappresentazione anteprima immagine rimuove la rappresentazione in miniatura .jpg, in quanto non è più necessaria.

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

### Configurazione del Proxy Worker per InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Il lavoratore risiede nell&#39;istanza proxy.

1. Nella console Strumenti, espandi Configurazioni **[!UICONTROL Servizi]** cloud nel riquadro a sinistra. Quindi espandete Configurazione **[!UICONTROL proxy]** Cloud.

1. Per aprire la configurazione, fai doppio clic su **[!UICONTROL IDS worker]**.

1. Fate clic su **[!UICONTROL Modifica]** per aprire la finestra di dialogo di configurazione e definire le impostazioni richieste:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Pool** IDS: Endpoint SOAP da utilizzare per comunicare con InDesign Server. È possibile aggiungere, rimuovere e ordinare gli elementi necessari.

1. Fate clic su **[!UICONTROL OK]** per salvare. 

### Configurazione di Day CQ Link Externalizer  {#configuring-day-cq-link-externalizer}

Se il server InDesign e AEM vengono eseguiti su host diversi o entrambe le applicazioni non vengono eseguite sulle porte predefinite, configurate **Day CQ Link Externalizer** per impostare il nome host, la porta e il percorso del contenuto per il server InDesign.

1. Accedere a Configuration Manager dall&#39;URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Individua la configurazione **[!UICONTROL Day CQ Link Externalizer]** e fai clic sull’icona **[!UICONTROL Modifica]** per aprirla.
1. Specificate il nome host e il percorso contestuale per il server Indesign e fate clic su **[!UICONTROL Salva]**.

   ![chlimage_1-290](assets/chlimage_1-290.png)

### Abilitazione dell&#39;elaborazione processi paralleli per InDesign Server {#enabling-parallel-job-processing-for-indesign-server-s}

È ora possibile abilitare l&#39;elaborazione processi paralleli per gli ID.

Prima di tutto dovete determinare il numero massimo di processi paralleli ( `x`) che un server InDesign può elaborare:

* Su un singolo computer multiprocessore, il numero massimo di processi paralleli (x) che un InDesign Server può elaborare è uno in meno del numero di processori che eseguono IDS.
* Quando si esegue IDS su più computer è necessario contare il numero totale di processori disponibili (ossia su tutti i computer), quindi sottrarre il numero totale di computer.

Per configurare il numero di processi IDS paralleli:

1. Aprite la scheda **[!UICONTROL Configurazioni]** della console Felix; ad esempio:

   `http://localhost:4502/system/console/configMgr`

1. Selezionate la coda di elaborazione IDS in:

   `Apache Sling Job Queue Configuration`

1. Imposta:

   * **[!UICONTROL Tipo]** - `Parallel`
   * **[!UICONTROL Processi]** paralleli massimi - `<*x*>` (come calcolato sopra)

1. Salvate queste modifiche.
1. Per abilitare il supporto per più sessioni per Adobe CS6 e versioni successive, selezionate la `enable.multisession.name` casella di controllo in `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Create un [pool di &lt; `*x*>` IDS worker aggiungendo endpoint SOAP alla configurazione](#configuring-the-proxy-worker-for-indesign-server)IDS Worker.

   Se sono presenti più computer che eseguono i server InDesign, aggiungete endpoint SOAP (numero di processori per computer -1) per ciascun computer.

   >[!NOTE]
   >
   >Quando si lavora con un pool di lavoratori, è possibile abilitare l&#39;elenco bloccato di lavoratori IDS.
   >
   >A tale scopo, abilitare la casella di controllo &quot;enable.try.name&quot; nella `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configurazione, che consente di recuperare i processi IDS.
   >
   >Inoltre, nella `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configurazione, impostare un valore positivo per il `max.errors.to.blacklist` parametro che determina il numero di recuperi di processi prima di barrare un ID dall&#39;elenco dei gestori di processi
   >
   >Per impostazione predefinita, dopo il tempo configurabile (`retry.interval.to.whitelist.name`) in minuti, il lavoratore IDS viene riconvalidato. Se il lavoratore viene trovato in linea, viene rimosso dall&#39;elenco bloccato.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done.
-->

## Supporto per Adobe InDesign Server 10.0 o versione successiva {#enabling-support-for-indesign-server-or-higher}

Per InDesign Server 10.0 o versione successiva, eseguite i seguenti passaggi per abilitare il supporto per più sessioni.

1. Aprire Gestione configurazione dall’ [!DNL Assets] istanza `https://[aem_server]:[port]/system/console/configMgr`.
1. Modificate la configurazione `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selezionate **[!UICONTROL ids.cc.enable]** e fate clic su **[!UICONTROL Salva]**.

>[!NOTE]
>
>Per [!DNL InDesign Server] l&#39;integrazione con [!DNL Assets], utilizzate un processore multi-core perché la funzione di supporto delle sessioni necessaria per l&#39;integrazione non è supportata nei sistemi single core.

## Configurare le credenziali Experience Manager {#configure-aem-credentials}

Potete modificare le credenziali di amministratore predefinite (nome utente e password) per accedere al server InDesign dall’istanza AEM senza interrompere l’integrazione con Adobe InDesign Server.

1. Passa a `/etc/cloudservices/proxy.html`.
1. Nella finestra di dialogo, specificate il nuovo nome utente e la nuova password.
1. Salvare le credenziali.
