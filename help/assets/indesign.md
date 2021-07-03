---
title: Integrare AEM Assets con Adobe InDesign Server
description: Scopri come integrare AEM Assets con InDesign Server.
contentOwner: AG
feature: Pubblicazione
role: Admin
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1703'
ht-degree: 4%

---

# Integrare AEM Assets con Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager (AEM) Assets utilizza:

* Un proxy per distribuire il carico di alcune attività di elaborazione. Un proxy è un&#39;istanza AEM che comunica con un proxy worker per eseguire un&#39;attività specifica e altre istanze AEM per fornire i risultati.
* Un processo di lavoro proxy per definire e gestire un’attività specifica.

Questi possono coprire un&#39;ampia gamma di compiti; ad esempio, l’utilizzo di un Adobe InDesign Server per elaborare i file.

Per caricare completamente i file in AEM Assets creati con Adobe InDesign viene utilizzato un proxy. Questo utilizza un processo di lavoro proxy per comunicare con Adobe InDesign Server, dove [gli script](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) vengono eseguiti per estrarre i metadati e generare diverse rappresentazioni per AEM Assets. Il proxy worker abilita la comunicazione bidirezionale tra le istanze InDesign Server e AEM in una configurazione cloud.

>[!NOTE]
>
>Adobe InDesign è dotato di due prodotti:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Consente di progettare layout di pagina per la stampa e/o la distribuzione digitale.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Questo motore consente di creare in modo programmatico documenti automatizzati in base a ciò che hai creato con InDesign. Funziona come un servizio che offre un&#39;interfaccia al suo motore [ExtendScript](https://www.adobe.com/devnet/scripting.html).\
   >  Gli script sono scritti in ExtendScript, che è simile a javascript. Per informazioni sugli script di Indesign, consulta [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>



## Come funziona l’estrazione {#how-the-extraction-works}

InDesign Server può essere integrato con AEM Assets in modo che i file creati con InDesign ( `.indd`) possano essere caricati, le rappresentazioni generate, tutti i file multimediali estratti (ad esempio, video) e memorizzati come risorse:**

>[!NOTE]
>
>Le versioni precedenti di AEM erano in grado di estrarre XMP e la miniatura, ora tutti i supporti possono essere estratti.

1. Carica il file `.indd` in AEM Assets.
1. Un framework invia script di comando ad InDesign Server tramite SOAP (Simple Object Access Protocol).

   Questo script di comando:

   * Recupera il file `.indd` .
   * Esegui comandi di InDesign Server:

      * Vengono estratti la struttura, il testo e tutti i file multimediali.
      * Vengono generate rappresentazioni PDF e JPG.
      * Vengono generati rendering HTML e IDML.
   * Ripubblicare i file risultanti in AEM Assets.

   >[!NOTE]
   >
   >IDML è un formato basato su XML che esegue il rendering di *tutto* nel file InDesign. Viene memorizzato come pacchetto compresso utilizzando la compressione [Zip](https://www.techterms.com/definition/zip).
   >
   >Per ulteriori informazioni, consulta [Formati di interscambio Adobe InDesign INX e IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) .

   >[!CAUTION]
   >
   >Se InDesign Server non è installato o non è configurato, puoi comunque caricare un file `.indd` in AEM. Tuttavia, le rappresentazioni generate saranno limitate a `png` e `jpeg`, non sarà possibile generare `html`, `idml` o rappresentazioni di pagina.

1. Dopo la generazione di estrazione e rendering:

   * La struttura viene replicata in un `cq:Page` (tipo di rendering).
   * Il testo e i file estratti vengono memorizzati in AEM Assets.
   * Tutte le rappresentazioni sono memorizzate in AEM Assets, nella risorsa stessa.

## Integrazione di InDesign Server con AEM {#integrating-the-indesign-server-with-aem}

Per integrare InDesign Server da utilizzare con AEM Assets e dopo aver configurato il proxy, è necessario:

1. [Installa InDesign Server](#installing-the-indesign-server).
1. Se necessario, [configura il flusso di lavoro AEM Assets](#configuring-the-aem-assets-workflow).

   Ciò è necessario solo se i valori predefiniti non sono appropriati per l’istanza.

1. Configura un processo di lavoro proxy [per InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installazione di InDesign Server {#installing-the-indesign-server}

Per installare e avviare InDesign Server da utilizzare con AEM:

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

### Configurazione del flusso di lavoro AEM Assets {#configuring-the-aem-assets-workflow}

AEM Assets dispone di un flusso di lavoro preconfigurato **Risorsa di aggiornamento DAM**, con diversi passaggi di processo specifici per InDesign:

* [Estrazione file multimediali](#media-extraction)
* [Estrazione pagina](#page-extraction)

Questo flusso di lavoro è configurato con valori predefiniti che possono essere adattati per la configurazione sulle varie istanze di authoring (si tratta di un flusso di lavoro standard, quindi ulteriori informazioni sono disponibili in [Modifica di un flusso di lavoro](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Se si utilizzano i valori predefiniti (inclusa la porta SOAP), non è necessaria alcuna configurazione.

Dopo la configurazione, il caricamento di file di InDesign in AEM Assets (con uno dei metodi consueti) attiverà il flusso di lavoro necessario per elaborare la risorsa e preparare le varie rappresentazioni. Verifica la configurazione caricando un file `.indd` in AEM Assets per confermare che sono presenti diverse rappresentazioni create da IDS in `<*your_asset*>.indd/Renditions`

#### Estrazione file multimediali {#media-extraction}

Questo passaggio controlla l’estrazione dei file multimediali dal file `.indd` .

Per personalizzare, puoi modificare la scheda **[!UICONTROL Arguments (Argomenti)]** del passaggio **[!UICONTROL Estrazione file multimediali]**.

![Argomenti di estrazione file multimediali e percorsi di script](assets/media_extraction_arguments_scripts.png)

Argomenti di estrazione file multimediali e percorsi di script

* **Libreria** ExtendScript: Si tratta di una semplice libreria di metodi http get/post, necessaria per gli altri script.

* **Estendi script**: Qui è possibile specificare diverse combinazioni di script. Se desideri eseguire gli script personalizzati su InDesign Server, salvali in `/apps/settings/dam/indesign/scripts`.

   Per informazioni sugli script di InDesign, consulta [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Non modificare la libreria ExtendScript. La libreria fornisce la funzionalità HTTP necessaria per comunicare con Sling. Questa impostazione specifica la libreria da inviare ad Adobe InDesign Server per l’utilizzo in tale ambiente.

Lo script `ThumbnailExport.jsx` eseguito dal passaggio del flusso di lavoro Estrazione file multimediali genera un rendering delle miniature in formato JPG. Questo rendering viene utilizzato dal passaggio del flusso di lavoro Elabora miniature per generare le rappresentazioni statiche richieste da AEM.

Puoi configurare il passaggio del flusso di lavoro Elabora miniature per generare rappresentazioni statiche con dimensioni diverse. Assicurati di non rimuovere i valori predefiniti, perché sono richiesti dall’interfaccia utente di AEM Assets. Infine, il passaggio del flusso di lavoro Elimina rappresentazione anteprima immagine rimuove il rendering delle miniature .jpg, in quanto non è più necessario.

#### Estrazione pagina {#page-extraction}

Viene creata una pagina AEM dagli elementi estratti. Un gestore estrazione viene utilizzato per estrarre dati da un rendering (attualmente HTML o IDML). Questi dati vengono quindi utilizzati per creare una pagina utilizzando PageBuilder.

Per personalizzare, è possibile modificare la scheda **[!UICONTROL Argomenti]** del passaggio **Estrazione pagina**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Gestore** estrazione pagina: Dall’elenco a discesa, seleziona il gestore da utilizzare. Un gestore estrazione opera su un rendering specifico, scelto da un `RenditionPicker` correlato (consulta l’API `ExtractionHandler`). Per impostazione predefinita, è disponibile il gestore estrazione esportazione IDML. Opera sul rendering `IDML` generato nel passaggio MediaExtract.

* **Nome** pagina: Specifica il nome da assegnare alla pagina risultante. Se lasciato vuoto, il nome è &quot;page&quot; (o un derivato, se &quot;page&quot; esiste già).

* **Titolo** pagina: Specifica il titolo da assegnare alla pagina risultante.

* **Percorso** principale pagina: Percorso della posizione principale della pagina risultante. Se lasciato vuoto, viene utilizzato il nodo contenente le rappresentazioni della risorsa.

* **Modello** pagina: Modello da utilizzare per la generazione della pagina risultante.

* **Progettazione** pagina: Progettazione di pagina da utilizzare per la generazione della pagina risultante.

### Configurazione del proxy Worker per InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Il processo di lavoro risiede nell&#39;istanza proxy.

1. Nella console Strumenti , espandi **[!UICONTROL Configurazioni Cloud Services]** nel riquadro a sinistra. Quindi espandi **[!UICONTROL Cloud Proxy Configuration]**.

1. Per aprire la configurazione, fai doppio clic su **[!UICONTROL IDS worker]**.

1. Fai clic su **[!UICONTROL Modifica]** per aprire la finestra di dialogo di configurazione e definire le impostazioni richieste:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Pool** IDS: Endpoint SOAP da utilizzare per la comunicazione con InDesign Server. È possibile aggiungere, rimuovere e ordinare gli elementi necessari.

1. Fate clic su **[!UICONTROL OK]** per salvare. 

### Configurazione di Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

Se InDesign Server e AEM si trovano su host diversi o se una o entrambe le applicazioni non funzionano sulle porte predefinite, configura **Day CQ Link Externalizer** per impostare il nome host, la porta e il percorso del contenuto per InDesign Server.

1. Accedi a Configuration Manager dall&#39;URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Individua la configurazione **[!UICONTROL Day CQ Link Externalizer]**. Fai clic su **[!UICONTROL Modifica]** per aprire.
1. Le impostazioni di Link Externalizer consentono di creare URL completi per la distribuzione [!DNL Experience Manager] e per [!DNL InDesign Server]. Utilizza il campo **[!UICONTROL Domains]** per specificare il nome host e il percorso contestuale per [!DNL Adobe InDesign Server]. Seguire le istruzioni visualizzate. Fai clic su **[!UICONTROL Salva]**.

   ![Impostazioni del collegamento esternalizzatore](assets/link-externalizer-config.png)

### Abilitazione dell’elaborazione parallela dei processi per gli InDesign Server {#enabling-parallel-job-processing-for-indesign-server}

È ora possibile abilitare l&#39;elaborazione dei processi paralleli per gli ID.

Innanzitutto devi determinare il numero massimo di processi paralleli ( `x`) elaborati da un InDesign Server:

* Su un singolo computer multiprocessore, il numero massimo di processi paralleli (x) che un InDesign Server può elaborare è inferiore di uno al numero di processori che eseguono ID.
* Quando si esegue l&#39;ID su più computer è necessario contare il numero totale di processori disponibili (ossia su tutti i computer), quindi sottrarre il numero totale di macchine.

Per configurare il numero di processi IDS paralleli:

1. Apri la scheda **[!UICONTROL Configurazioni]** della console Felix; ad esempio:

   `http://localhost:4502/system/console/configMgr`

1. Seleziona la coda di elaborazione IDS in:

   `Apache Sling Job Queue Configuration`

1. Imposta:

   * **[!UICONTROL Tipo]** - `Parallel`
   * **[!UICONTROL Processi]**  paralleli massimi -  `<*x*>` (come calcolato sopra)

1. Salva queste modifiche.
1. Per abilitare il supporto per più sessioni per Adobe CS6 e versioni successive, seleziona la casella di controllo `enable.multisession.name` in `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Crea un [pool di processi di lavoro &lt; `*x*>` IDS aggiungendo endpoint SOAP alla configurazione IDS Worker](#configuring-the-proxy-worker-for-indesign-server).

   Se sono presenti più computer che eseguono InDesign Server, aggiungere endpoint SOAP (numero di processori per computer -1) per ogni computer.

   >[!NOTE]
   >
   >Quando si lavora con un pool di lavoratori, è possibile abilitare l&#39;elenco Bloccati di lavoratori IDS.
   >
   >Per farlo, abilita la casella di controllo &quot;enable.try.name&quot;, nella configurazione `com.day.cq.dam.ids.impl.IDSJobProcessor.name`, che abilita i processi IDS.
   >
   >Inoltre, nella configurazione `com.day.cq.dam.ids.impl.IDSPoolImpl.name`, imposta un valore positivo per il parametro `max.errors.to.blacklist` che determina il numero di recuperi di processi prima di assegnare un ID dall&#39;elenco dei gestori di processi
   >
   >Per impostazione predefinita, dopo il tempo configurabile (`retry.interval.to.whitelist.name`) in minuti, il processo di lavoro IDS viene riconvalidato. Se il lavoratore viene trovato online, viene rimosso dall&#39;elenco Bloccati.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Abilita il supporto per il server Adobe InDesign 10.0 o versione successiva {#enabling-support-for-indesign-server-or-higher}

Per il server InDesign 10.0 o versione successiva, esegui i seguenti passaggi per abilitare il supporto per più sessioni.

1. Apri Configuration Manager dall&#39;istanza [!DNL Assets] `https://[aem_server]:[port]/system/console/configMgr`.
1. Modifica la configurazione `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selezionare l&#39;opzione **[!UICONTROL ids.cc.enable]** e fare clic su **[!UICONTROL Salva]**.

>[!NOTE]
>
>Per l&#39;integrazione di [!DNL InDesign Server] con [!DNL Assets], utilizza un processore multi-core perché la funzionalità di supporto della sessione necessaria per l&#39;integrazione non è supportata sui sistemi single-core.

## Configurare le credenziali di Experience Manager {#configure-aem-credentials}

È possibile modificare le credenziali di amministratore predefinite (nome utente e password) per accedere al server InDesign dall’istanza AEM senza interrompere l’integrazione con il server Adobe InDesign.

1. Passa a `/etc/cloudservices/proxy.html`.
1. Nella finestra di dialogo , specifica il nuovo nome utente e la nuova password.
1. Salva le credenziali.
