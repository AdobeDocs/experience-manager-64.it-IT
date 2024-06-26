---
title: Video in Dynamic Media
description: Scopri come lavorare con i video in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: Dynamic-Media
content-type: reference
exl-id: acb95a2b-0171-449e-97fa-f9a533f990de
feature: Video
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '10437'
ht-degree: 4%

---

# Video {#video}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa sezione descrive come lavorare con i video in Dynamic Media.

## Avvio rapido: Video {#quick-start-videos}

La seguente descrizione dettagliata del flusso di lavoro è stata progettata per aiutarti a iniziare rapidamente a usare i set di video adattivi in Dynamic Media. Dopo ogni passaggio sono riferimenti incrociati alle intestazioni degli argomenti, dove è possibile trovare ulteriori informazioni.

>[!NOTE]
>
>Prima di lavorare con i video in Dynamic Media, assicurati che l’amministratore AEM abbia già abilitato e configurato i Cloud Services Dynamic Media.
>
>* Vedi [Configurazione dei Cloud Services Dynamic Media in Configurazione di Dynamic Media - Modalità ibrida.](/help/assets/config-dynamic.md)
>* Vedi [Configurazione di Dynamic Media - Modalità Scene7](config-dms7.md) e [Risoluzione dei problemi Dynamic Media - Modalità Scene7](troubleshoot-dms7.md)
>


1. **Caricare i video Dynamic Media** eseguendo le operazioni seguenti:

   * Crea il tuo profilo di codifica video. Oppure, puoi semplicemente utilizzare il profilo &quot;Codifica video adattiva&quot; predefinito fornito con Dynamic Media.

      * [Creazione di un profilo di codifica video](video-profiles.md).
      * Ulteriori informazioni [Best practice per la codifica video](#best-practices-for-encoding-videos).
   * Associa il profilo di elaborazione video a una o più cartelle in cui stai per caricare i video master.

      * [Applicazione di un profilo video alle cartelle](video-profiles.md#applying-a-video-profile-to-folders).
      * Ulteriori informazioni [Best practice per organizzare le risorse digitali per l’utilizzo dei profili di elaborazione](organize-assets.md#organize-using-folders).
      * Ulteriori informazioni [Organizzazione delle risorse digitali](organize-assets.md).
   * Carica i video sorgente principali nelle cartelle. Quando aggiungi dei video alla cartella, questi vengono codificati in base al profilo di elaborazione video assegnato alla cartella.

      * Dynamic Media supporta principalmente video in formato breve con una lunghezza massima di 30 minuti e una risoluzione minima superiore a 25 x 25.
      * Puoi caricare file video fino a 15 GB ciascuno.
      * [Caricare i video](managing-video-assets.md#uploading-and-previewing-video-assets).
      * Ulteriori informazioni [Formati di file di input supportati](assets-formats.md#supported-multimedia-formats).
   * Monitorare come [la codifica video è in corso](#monitoring-video-encoding-and-youtube-publishing-progress) dalla visualizzazione della risorsa o del flusso di lavoro.




1. **Gestire i video Dynamic Media** eseguendo una delle operazioni seguenti:

   * Organizzare, sfogliare ed eseguire ricerche nelle risorse video

      * [Organizzazione delle risorse digitali](organize-assets.md)

         Ulteriori informazioni [Best practice per organizzare le risorse digitali per l’utilizzo dei profili di elaborazione](organize-assets.md#organize-using-folders)

      * [Ricerca delle risorse video](search-video-assets.md) o [Ricerca delle risorse](managing-assets-touch-ui.md#searching-assets)
   * Anteprima e pubblicazione delle risorse video

      * Visualizzare il video sorgente e le rappresentazioni codificate del video insieme alle miniature associate:

         [Anteprima dei video](managing-video-assets.md#uploading-and-previewing-video-assets) o [Anteprima delle risorse](previewing-assets.md)

         [Visualizzazione delle rappresentazioni video](video-renditions.md)

[Gestione delle rappresentazioni video](managing-assets-touch-ui.md#managing-renditions)

      * [Gestire i predefiniti per visualizzatori](managing-viewer-presets.md)
      * [Pubblicazione delle risorse](publishing-dynamicmedia-assets.md)
   * Utilizzare i metadati video

      * Visualizzare le proprietà di un rendering video codificato quali frame rate, bitrate audio e video e codec:

         [Visualizzazione delle proprietà di rendering video](video-renditions.md)

      * Modifica le proprietà del video quali titolo, descrizione e tag, campi di metadati personalizzati:

[Modifica delle proprietà video](managing-assets-touch-ui.md#editing-properties)

      * [Gestione dei metadati per le risorse digitali](metadata.md)
      * [Schemi di metadati](metadata-schemas.md)
   * Revisione, approvazione e annotazione dei video

      * [Aggiunta di annotazioni ai video](managing-video-assets.md#annotating-video-assets) o [Aggiunta di annotazioni alle risorse](managing-assets-touch-ui.md#annotating)
      * [Applicazione dei flussi di lavoro alle risorse](assets-workflow.md) o [Avvio di un flusso di lavoro su una risorsa](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset)
      * [Esaminare le risorse delle cartelle](bulk-approval.md)
      * [Progetti](/help/sites-authoring/projects.md)




1. **Pubblicare i video Dynamic Media** eseguendo una delle operazioni seguenti:

   * Se utilizzi Adobe Experience Manager come sistema di gestione dei contenuti web, puoi aggiungere video direttamente alle pagine web.

      * [Aggiunta di video alle pagine web](adding-dynamic-media-assets-to-pages.md).
   * Se utilizzi un sistema di gestione dei contenuti web di terze parti, puoi collegare o incorporare video alle tue pagine web.

      * Integra i video utilizzando l’URL:

         [Collegamento di URL all’applicazione web](linking-urls-to-yourwebapplication.md).
      * Integra i video utilizzando il codice di incorporamento sulla pagina web:

         [Incorporare il visualizzatore video in una pagina web](embed-code.md).
   * [Pubblicazione di video in YouTube](#publishing-videos-to-youtube).
   * [Generazione di rapporti video](#viewing-video-reports).
   * [Aggiunta di sottotitoli a video](#adding-captions-to-video).



## Utilizzare i video in Dynamic Media {#working-with-video-in-dynamic-media}

Video in Dynamic Media è una soluzione end-to-end che semplifica la pubblicazione di video adattivi di alta qualità per lo streaming su più schermi, tra cui desktop, iOS, Android, Blackberry e dispositivi mobili Windows. Un Adaptive Video Set raggruppa versioni dello stesso video codificate con diversi bit rate e formati come 400 kbps, 800 kbps e 1000 kbps. Il computer desktop o il dispositivo mobile rileva la larghezza di banda disponibile.

Ad esempio, su un dispositivo mobile iOS, rileva una larghezza di banda come 3G, 4G o Wi-Fi. Quindi, seleziona automaticamente il video codificato a destra tra i vari bit rate video all&#39;interno del set video adattivo. Il video viene inviato in streaming a desktop, dispositivi mobili o tablet.

Inoltre, la qualità video viene commutata in modo dinamico automaticamente se le condizioni di rete cambiano sul desktop o sul dispositivo mobile. Inoltre, se un cliente entra in modalità a schermo intero su un desktop, il set video adattivo risponde utilizzando una risoluzione migliore, migliorando in tal modo l’esperienza di visualizzazione del cliente. L’utilizzo di Adaptive Video Sets offre la migliore riproduzione possibile per i clienti che riproducono video Dynamic Media su schermi e dispositivi multipli.

La logica utilizzata da un lettore video per determinare quale video codificato riprodurre o selezionare durante la riproduzione si basa sul seguente algoritmo:

1. Il lettore video carica il frammento video iniziale in base al bit rate più vicino al valore impostato per il &quot;bitrate iniziale&quot; nel lettore stesso.
1. Il lettore video commuta in base ai cambiamenti della velocità della larghezza di banda utilizzando i seguenti criteri:

   1. Player sceglie il flusso di banda più alto sotto o uguale alla larghezza di banda stimata.
   1. Il lettore considera solo l&#39;80% della larghezza di banda disponibile. Tuttavia, se sta cambiando, è più conservativo solo al 70% per evitare sovrastimazioni e immediatamente tornare indietro.

Per informazioni tecniche dettagliate sull’algoritmo, consulta [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Per la gestione di set video singoli e di set video adattivi, sono supportati i seguenti elementi:

* Caricamento di video da numerosi formati video e formati audio supportati e codifica di video in formato MP4 H.264 per la riproduzione su più schermi. È possibile utilizzare predefiniti per video adattivi, predefiniti di codifica per video singoli o personalizzare la propria codifica per controllare la qualità e le dimensioni del video.

   * Quando viene generato un set video adattivo, questo include video MP4.
   * **Nota**: I video master/sorgente non vengono aggiunti a un set video adattivo.

* sottotitoli video in tutti i visualizzatori video HTML5.
* Organizza, sfoglia e cerca video con il supporto completo dei metadati per una gestione efficiente delle risorse video.
* Distribuisci set video adattivi sul web, sui desktop e sui dispositivi mobili, inclusi iPhone, iPad, Android, Blackberry e Windows Phone.

Lo streaming video adattivo è supportato su diverse piattaforme iOS. Consulta la sezione [Guida di riferimento visualizzatori di Adobi](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

Dynamic Media supporta la riproduzione video mobile per video MP4 H.264. Puoi trovare i dispositivi Blackberry che supportano questo formato video nel seguente sito: [Formati video supportati su Blackberry](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

È possibile trovare i dispositivi Windows che supportano questo formato video nel seguente percorso: [Formati video supportati su Windows Phone](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)

* Riproduci il video utilizzando i predefiniti per visualizzatori video di Dynamic Media, tra cui:

   * Visualizzatori video singoli.
   * Visualizzatori per file multimediali diversi che combinano contenuti video e immagine.

* Configura i lettori video per soddisfare le tue esigenze di branding.
* Integra i video sul tuo sito web, sito mobile o applicazione mobile con un semplice URL o codice di incorporamento.

<!-- See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480). -->

Vedi anche [Informazioni sui visualizzatori HTML5](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) in Adobe Dynamic Media Viewers Reference Guide (Guida di riferimento visualizzatori di).

## Procedure consigliate: Utilizzo del visualizzatore video HTML5 {#best-practice-using-the-html-video-viewer}

I predefiniti per visualizzatori video Dynamic Media HTML5 sono lettori video affidabili. È possibile utilizzarli per evitare molti problemi comuni relativi alla riproduzione video di HTML5 e problemi associati a dispositivi mobili, come la mancanza di distribuzione dello streaming adattivo e la portata limitata del browser desktop.

Dal lato del design del lettore, puoi progettare tutte le funzionalità del lettore video utilizzando gli strumenti standard di sviluppo web. Ad esempio, puoi progettare pulsanti, controlli e sfondo personalizzato dell’immagine miniatura utilizzando HTML5 e CSS per aiutarti a raggiungere i clienti con un aspetto personalizzato.

Dal lato della riproduzione del visualizzatore, rileva automaticamente la funzionalità video del browser. Quindi distribuisce il video usando lo streaming HLS (streaming video adattivo). Oppure, se tali metodi di consegna non sono presenti, viene invece utilizzato HTML5 progressive.

Combinando in un singolo lettore la possibilità di progettare i componenti di riproduzione utilizzando HTML5 e CSS, di incorporare la riproduzione e di utilizzare lo streaming adattivo e progressivo a seconda delle funzionalità del browser, è possibile estendere la portata dei contenuti rich media sia agli utenti desktop che mobili e garantire un’esperienza video semplificata.

Vedi anche [Informazioni sui visualizzatori HTML5](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html) nella Guida di riferimento visualizzatori di Adobi.

### Riproduzione di video su computer desktop e dispositivi mobili utilizzando il visualizzatore video HTML5 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Per lo streaming video adattivo per desktop e dispositivi mobili, i video utilizzati per la commutazione del bit rate si basano su tutti i video MP4 nel set video adattivo.

La riproduzione video si verifica utilizzando lo streaming video HLS (HTTP Live Streaming) o il download progressivo del video. Nelle versioni precedenti di AEM, come 6.0, 6.1 e 6.2, i video venivano trasmessi in streaming via HTTP.

Tuttavia, in AEM 6.3 e versioni successive, i video vengono ora trasmessi in streaming su HTTPS (cioè, streaming video HLS) perché l&#39;URL del servizio gateway DM utilizza sempre anche HTTPS. In questo comportamento predefinito non vi è alcun impatto sui clienti. In altre parole, lo streaming video si verifica sempre su HTTPS a meno che non sia supportato dal browser. (vedere la tabella seguente). Pertanto,

* Se disponi di un sito web HTTPS con streaming video HTTPS, lo streaming è a posto.
* Se disponi di un sito web HTTP con streaming video HTTPS, lo streaming è a posto e il browser Web non presenta problemi di contenuto misto.

HLS (HTTP Live Streaming) è uno standard Apple per lo streaming video adattivo che regola automaticamente la riproduzione in base alla capacità della larghezza di banda della rete. Permette inoltre al cliente di &quot;cercare&quot; in qualsiasi punto del video senza dover attendere che il resto del video venga scaricato (vedi anche HTTP Live Streaming).

Il video progressivo viene distribuito scaricando e memorizzando localmente il video sullo schermo desktop o sul dispositivo mobile di un utente.

La tabella seguente descrive il dispositivo, il browser e il metodo di riproduzione dei video su computer desktop e dispositivi mobili che utilizzano il visualizzatore video Dynamic Media.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Dispositivo</strong></td>
   <td><strong>Browser</strong></td>
   <td><strong>Modalità di riproduzione video</strong></td>
  </tr>
  <tr> 
   <td>Desktop</td>
   <td>Internet Explorer 9 e 10</td>
   <td>Download progressivo.</td>
  </tr>
  <tr> 
   <td>Desktop</td>
   <td>Internet Explorer 11+</td>
   <td>Su Windows 8 e Windows 10 - Forza l'uso di HTTPS ogni volta che viene richiesto HLS. Limitazione nota: HTTP su HLS non funziona in questa combinazione browser/sistema operativo<br /> <br /> Su Windows 7 - Download progressivo. Utilizza la logica standard per selezionare il protocollo HTTP rispetto a quello HTTPS.</td>
  </tr>
  <tr> 
   <td>Desktop</td>
   <td>Firefox 23-44</td>
   <td>Download progressivo.</td>
  </tr>
  <tr> 
   <td>Desktop</td>
   <td>Firefox 45 o versione successiva</td>
   <td>Streaming video HLS.</td>
  </tr>
  <tr> 
   <td>Desktop</td>
   <td>Chrome</td>
   <td>Streaming video HLS.</td>
  </tr>
  <tr> 
   <td>Desktop</td>
   <td>Safari (Mac)</td>
   <td>Streaming video HLS.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Chrome (Android 6 o precedente)</td>
   <td>Download progressivo.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Chrome (Android 7 o successivo)</td>
   <td>Streaming video HLS.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Android (browser predefinito)</td>
   <td>Download progressivo.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Safari (iOS)</td>
   <td>Streaming video HLS.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Chrome (iOS)</td>
   <td>Streaming video HLS.</td>
  </tr>
  <tr> 
   <td>Mobile</td>
   <td>Blackberry</td>
   <td>Streaming video HLS.</td>
  </tr>
 </tbody>
</table>

## Architettura della soluzione video Dynamic Media {#architecture-of-dynamic-media-video-solution}

L’immagine seguente mostra il flusso di lavoro di authoring complessivo dei video caricati e codificati tramite DMGGateway e resi disponibili per il consumo pubblico.

![chlimage_1-427](assets/chlimage_1-427.png)

## Architettura di pubblicazione ibrida per i video {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Best practice per la codifica dei video {#best-practices-for-encoding-videos}

Se hai attivato gli elementi multimediali dinamici e hai impostato Cloud Services per i video flusso di lavoro, **[!UICONTROL Codifica video elementi multimediali dinamici]** ti consente di eseguire la codifica dei video. Questo flusso di lavoro acquisisce la cronologia del processo del flusso di lavoro e le informazioni di errore. Consulta la sezione [Monitoraggio della codifica video e stato della pubblicazione su YouTube](#monitoring-video-encoding-and-youtube-publishing-progress). Se hai abilitato Dynamic Media e hai impostato i servizi Cloud, la **[!UICONTROL Codifica video Dynamic Media]** il flusso di lavoro ha effetto automaticamente al momento del caricamento di un video. Se non utilizzi Dynamic Media, la **[!UICONTROL Risorsa di aggiornamento DAM]** il flusso di lavoro ha effetto).

<!-- DEAD ARTICLE AND VIDEO LINK The following are best-practice tips for encoding source video files.

For advice about video encoding, see the following:

* Article: *Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution:* [www.adobe.com/go/learn_s7_streaming101_en](https://www.adobe.com/go/learn_s7_streaming101_en).
* Video: *Video Encoding Basics:* [www.adobe.com/go/learn_s7_encoding_en](https://www.adobe.com/go/learn_s7_encoding_en). -->

### File video sorgente principali {#source-video-files}

Quando codifichi un file video, utilizza un file video sorgente della massima qualità possibile. Evita di utilizzare file video codificati in precedenza perché sono già compressi e un’ulteriore codifica crea un video di qualità scadente.

* Dynamic Media supporta principalmente video in formato breve con una lunghezza massima di 30 minuti e una risoluzione minima superiore a 25 x 25.
* È possibile caricare file video di origine primaria fino a 15 GB ciascuno.

La tabella seguente descrive le dimensioni consigliate, le proporzioni e il bit rate minimo che i file video sorgente dovrebbero avere prima di codificarli:

| Dimensione | Proporzioni | Bit rate minimo |
|--- |--- |--- |
| 1024 X 768 | 4:3 | 4500 kbps per la maggior parte dei video. |
| 1280 X 720 | 16:9 | 3000 - 6000 kbps, a seconda della quantità di movimento nel video. |
| 1920 X 1080 | 16:9 | 6000 - 8000 kbps, a seconda della quantità di movimento nel video. |

### Ottenere i metadati di un file {#obtaining-a-file-s-metadata}

È possibile ottenere i metadati di un file visualizzandone i metadati utilizzando uno strumento di editing video o un&#39;applicazione progettata per ottenere i metadati. Di seguito sono riportate le istruzioni per l’utilizzo di MediaInfo, un’applicazione di terze parti, per ottenere i metadati di un file video:

1. Vai a questa pagina web: [https://mediaarea.net/en/MediaInfo](https://mediaarea.net/en/MediaInfo).
1. Selezionare e scaricare il programma di installazione per la versione GUI in uso e seguire le istruzioni di installazione.
1. Dopo l&#39;installazione, fare clic con il pulsante destro del mouse sul file video (solo Windows) e selezionare **[!UICONTROL MediaInfo]** o apri **[!UICONTROL MediaInfo]** e trascina il file video nell’applicazione. Vengono visualizzati tutti i metadati associati al file video, inclusi larghezza, altezza e fps.

### Proporzioni {#aspect-ratio}

Quando scegli o crei un predefinito di codifica video per il file video principale, accertati che il predefinito abbia le stesse proporzioni del file video principale. Il rapporto di formato è il rapporto tra la larghezza e l&#39;altezza del video.

Per determinare le proporzioni di un file video, ottieni i metadati del file e prendi nota della larghezza e dell’altezza del file (vedi Ottenere i metadati di un file qui sopra). Quindi utilizzare questa formula per determinare le proporzioni:

*larghezza/altezza = proporzioni*

La tabella seguente descrive come i risultati delle formule si traducono in scelte di proporzioni comuni:

| Risultato della formula | Proporzioni |
|--- |--- |
| 1.33 | 4:3 |
| 0.75 | 3:4 |
| 1.78 | 16:9 |
| 0.56 | 9:16 |

Ad esempio, un video con una larghezza x 1080 di 1440 ha un rapporto di formato di 1440/1080 o 1,33. In questo caso scegli un predefinito di codifica video con un rapporto di formato 4:3 per codificare il file video.

### Bitrate {#bitrate}

Il bitrate è la quantità di dati codificati per creare un secondo di riproduzione video. Il bitrate viene misurato in kilobit al secondo (Kbps).

Poiché tutti i codec utilizzano la compressione con perdita di dati, il bitrate è il fattore più importante nella qualità video. Con la compressione con perdita di dati, più si comprime un file video, più la qualità è degradata. Per questo motivo, tutte le altre caratteristiche sono uguali (la risoluzione, il frame rate e il codec), più basso è il bitrate, minore è la qualità del file compresso.

Quando si seleziona una codifica a bit rate, è possibile scegliere due tipi:

* **Codifica a bit rate costante** (CBR) - Durante la codifica CBR, il bitrate o il numero di bit al secondo viene mantenuto lo stesso durante tutto il processo di codifica. La codifica CBR persiste quando la velocità dei dati impostata viene impostata sull’impostazione per l’intero video. Inoltre, la codifica CBR non ottimizza i file multimediali per la qualità, ma salva lo spazio di archiviazione.

   Utilizzare CBR se il video contiene un livello di movimento simile per l&#39;intero video. CBR viene utilizzato più comunemente per lo streaming di contenuti video. Vedi anche [Utilizzo di parametri di codifica video personalizzati](video-profiles.md#using-custom-added-video-encoding-parameters).

* **Codifica a bit rate variabile** (VBR) - La codifica VBR regola la velocità dei dati in basso e al limite superiore impostato, in base ai dati richiesti dal compressore. Ciò significa che durante un processo di codifica VBR il bitrate del file multimediale aumenta o diminuisce dinamicamente a seconda delle esigenze del bitrate dei file multimediali.

   VBR richiede più tempo per codificare ma produce i risultati più favorevoli; la qualità del file multimediale è superiore. VBR è utilizzato più comunemente per la distribuzione http progressiva dei contenuti video.

**Quando si devono usare VBR e CRB?**
Quando si tratta di selezionare VBR rispetto a CBR, si consiglia quasi sempre di utilizzare VBR per i file multimediali. VBR offre file di qualità superiore a bit rate competitivi. Quando si utilizza il VBR, assicurarsi di utilizzare con la codifica a due passaggi e impostare il bitrate massimo su 1,5 volte il bitrate video di destinazione.

Quando scegli un predefinito di codifica video, prendi in considerazione la velocità di connessione dell’utente finale di destinazione. Scegli un predefinito con una velocità dati pari all&#39;80% di quella velocità. Ad esempio, se la velocità di connessione dell’utente finale target è di 1000 Kbps, la preimpostazione migliore è quella con una velocità dati video di 800 Kbps.

Questa tabella descrive la velocità dati delle velocità di connessione tipiche.

| Velocità (Kbps) | Tipo di connessione |
|--- |--- |
| 256 | Connessione remota. |
| 800 | Connessione mobile tipica. Per questa connessione, esegui il targeting di una velocità dati compresa tra 400 e un massimo di 800 per le esperienze 3G. |
| 2000 | Connessione desktop a banda larga tipica. Per questa connessione, eseguire il targeting di una velocità dati nell&#39;intervallo 800-2000 Kbps, con la maggior parte delle destinazioni con una media di 1200-1500 Kbps. |
| 5000 | Connessione a banda larga tipica. La codifica in questo intervallo superiore non è consigliata perché la distribuzione video a questa velocità non è disponibile per la maggior parte dei consumatori. |

### Risoluzione {#resolution}

**Risoluzione** descrive l’altezza e la larghezza in pixel di un file video. La maggior parte dei video sorgente viene memorizzata ad alta risoluzione (ad esempio, 1920 x 1080). A scopo di streaming, il video sorgente viene compresso in una risoluzione più piccola (640 x 480 o inferiore).

La risoluzione e la velocità dei dati sono due fattori strettamente collegati che determinano la qualità video. Per mantenere la stessa qualità video, più alto è il numero di pixel in un file video (più alta è la risoluzione), più alta deve essere la velocità dei dati. Ad esempio, considera il numero di pixel per fotogramma in una risoluzione 320 x 240 e un file video con risoluzione 640 x 480:

| Risoluzione | Pixel per frame |
|--- |--- |
| 320 x 240 | 76,800 |
| 640 x 480 | 307,200 |

Il file 640 x 480 ha quattro volte più pixel per frame. Per ottenere la stessa velocità dati per queste due risoluzioni di esempio, si applica una compressione quattro volte maggiore al file 640 x 480, che può ridurre la qualità del video. Pertanto, una velocità dati video di 250 Kbps produce una visualizzazione di alta qualità con una risoluzione di 320 x 240, ma non con una risoluzione di 640 x 480.

In generale, maggiore è la velocità dei dati utilizzata, migliore è l&#39;aspetto del video e maggiore è la risoluzione utilizzata, maggiore è la velocità dei dati necessaria per mantenere la qualità di visualizzazione (rispetto alle risoluzioni più basse).

Poiché la risoluzione e la velocità dei dati sono collegate, durante la codifica dei video sono disponibili due opzioni:

* Scegli una velocità dati e quindi codifica alla risoluzione più alta che si adatta alla velocità dati scelta.
* Scegliete una risoluzione e quindi codificate alla velocità di dati necessaria per ottenere video di alta qualità alla risoluzione scelta.

Quando scegli (o crei) un predefinito di codifica video per il file video principale, utilizza questa tabella per definire la risoluzione corretta:

| Risoluzione | Altezza (pixel) | Dimensioni dello schermo |
|--- |--- |--- |
| 240p | 240 | Schermo compatto |
| 300p | 300 | Schermo piccolo in genere per dispositivi mobili |
| 360p | 360 | Schermo piccolo |
| 480p | 480 | Schermo medio |
| 720p | 720 | Schermo grande |
| 1080p | 1080 | Schermo grande ad alta definizione |

### Fps (fotogrammi al secondo) {#fps-frames-per-second}

Negli Stati Uniti e in Giappone la maggior parte dei video viene girata a 29,97 fotogrammi al secondo (fps); in Europa, la maggior parte dei video viene girata a 25 fps. Il film è girato a 24 fps.

Scegli un predefinito di codifica video che corrisponda alla frequenza fps del file video principale. Ad esempio, se il video principale è 25 fps, scegli un predefinito di codifica con 25 fps. Per impostazione predefinita, tutte le codifiche personalizzate utilizzano fps del file video principale. Per questo motivo, non è necessario specificare esplicitamente l’impostazione fps quando si crea un predefinito di codifica video.

### Dimensioni di codifica video {#video-encoding-dimensions}

Per risultati ottimali, seleziona dimensioni di codifica tali che il video sorgente sia un intero multiplo di tutti i video codificati.

Per calcolare questo rapporto, dividete la larghezza sorgente per la larghezza codificata per ottenere il rapporto di larghezza. Poi, dividi l&#39;altezza della sorgente per l&#39;altezza codificata per ottenere il rapporto di altezza.

Se il rapporto risultante è un numero intero, significa che il video viene ridimensionato in modo ottimale. Se il rapporto risultante non è un numero intero, influisce sulla qualità video lasciando sul display gli artefatti dei pixel rimasti. Questo effetto è più evidente quando il video ha del testo.

Ad esempio, supponiamo che il video sorgente sia 1920 x 1080. Nella tabella seguente, i tre video codificati forniscono le impostazioni di codifica ottimali da utilizzare.

<table> 
 <tbody> 
  <tr> 
   <th><p>Tipo video</p> </th> 
   <th><p>Larghezza x altezza</p> </th> 
   <th><p>Rapporto larghezza</p> </th> 
   <th><p>Rapporto altezza</p> </th> 
  </tr>
  <tr> 
   <td><p>Sorgente</p> </td> 
   <td><p>1920x1080</p> </td> 
   <td><p>1</p> </td> 
   <td><p>1</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificato</p> </td> 
   <td><p>960 x 540</p> </td> 
   <td><p>2</p> </td> 
   <td><p>2</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificato</p> </td> 
   <td><p>640 x 360</p> </td> 
   <td><p>3</p> </td> 
   <td><p>3</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codificato</p> </td> 
   <td><p>480 x 270</p> </td> 
   <td><p>4</p> </td> 
   <td><p>4</p> </td> 
  </tr> 
 </tbody> 
</table>

### Formato del file video codificato {#encoded-video-file-format}

Dynamic Media consiglia di utilizzare i predefiniti di codifica video MP4 H.264. Poiché i file MP4 utilizzano il codec video H.264, fornisce video di alta qualità ma in dimensioni file compresse.

## Pubblicazione di video in YouTube {#publishing-videos-to-youtube}

Puoi pubblicare risorse video on-premise AEM direttamente su un canale YouTube creato in precedenza.

Per pubblicare le risorse video in YouTube, imposta AEM Assets con i tag . Puoi associare questi tag a un canale YouTube. Se il tag di una risorsa video corrisponde al tag di un canale YouTube, il video viene pubblicato in YouTube. Se la risorsa video non ha un tag, non viene pubblicata in YouTube.

La pubblicazione in YouTube ignora il sistema di elaborazione dei profili in AEM e, quindi, anche il profilo di codifica video. Questo bypass si verifica perché YouTube dispone di una propria codifica, pertanto non è necessario un profilo di elaborazione video. Nella maggior parte dei casi, tuttavia, ci si aspetta che le risorse video siano già passate attraverso un profilo di elaborazione video. Se bypassi il profilo di elaborazione video e lo pubblichi direttamente in YouTube, significa semplicemente che la risorsa video in AEM risorsa non riceve una miniatura visibile. Significa anche che se esegui in modalità di esecuzione di Dynamic Media, i video non codificati non funzioneranno con nessuno dei tipi di risorse Dynamic Media.

La pubblicazione delle risorse video sui server YouTube comporta il completamento delle seguenti attività per garantire l’autenticazione server-to-server sicura con YouTube:

1. [Configurare le impostazioni di Google Cloud](#configuring-google-cloud-settings)
1. [Creare un canale YouTube](#creating-a-youtube-channel)
1. [Aggiungi tag per la pubblicazione](#adding-tags-for-publishing)
1. [Attivare l’agente di replica di pubblicazione YouTube](#enabling-the-youtube-publish-replication-agent)
1. [Configurare YouTube in AEM](#setting-up-youtube-in-aem)
1. [(Facoltativo) Automatizza l&#39;impostazione delle proprietà predefinite di YouTube per i video caricati](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Pubblicare video sul canale YouTube](#publishing-videos-to-your-youtube-channel)
1. [(Facoltativo) Verifica il video pubblicato su YouTube](video.md#optional-verifying-the-published-video-on-youtube)
1. [Collegare gli URL di YouTube all’applicazione Web](#linking-youtube-urls-to-your-web-application)

È inoltre possibile [annullare la pubblicazione dei video per rimuoverli da YouTube](#unpublishing-videos-to-remove-them-from-youtube).

### Configurare le impostazioni Google Cloud {#configuring-google-cloud-settings}

Per pubblicare su YouTube, è necessario un account Google. Se disponi di un account GMAIL, disponi già di un account Google. Se non disponi di un account Google, puoi facilmente crearne uno. È necessario l’account perché sono necessarie le credenziali per pubblicare le risorse video in YouTube. Se hai già creato un account, salta questa attività e procedi con [Creazione di un canale YouTube](#creating-a-youtube-channel).

>[!NOTE]
>
>I seguenti passaggi erano accurati al momento di questa scrittura. Tuttavia, Google aggiorna periodicamente i propri siti web senza preavviso. Di conseguenza, questi passaggi possono essere leggermente diversi.

**Per configurare le impostazioni Google Cloud:**

1. Crea un nuovo account Google.

   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   Se disponi già di un account Google, passa al passaggio successivo.

1. Vai a [https://cloud.google.com/](https://cloud.google.com/).
1. Nella pagina Google Cloud Platform, nella parte superiore, tocca **[!UICONTROL Console]**. Potrebbe essere necessario **Accedere** utilizzo delle credenziali del tuo account Google.
1. Sulla **[!UICONTROL Dashboard]** pagina, tocca **[!UICONTROL Crea progetto]**.
1. In **[!UICONTROL Nuovo progetto]** immettere il nome di un progetto nella finestra di dialogo.

   L’ID del progetto è basato sul nome del progetto. Scegliere con attenzione il nome del progetto; non può essere modificato dopo la creazione. Inoltre, quando configuri YouTube in Adobe Experience Manager in un secondo momento, dovrai immettere di nuovo lo stesso ID progetto. È possibile annotare l’ID del progetto.
1. Tocca **[!UICONTROL Crea]**.

1. Sul progetto **[!UICONTROL Dashboard]**, nella **[!UICONTROL Introduzione]** scheda, toccare **[!UICONTROL Abilita le API e ottieni le credenziali come chiavi]**.
1. Vicino alla parte superiore della **[!UICONTROL Dashboard]** pagina, tocca **[!UICONTROL Abilita API]**.
1. Sulla **[!UICONTROL Libreria]** in API YouTube, tocca **[!UICONTROL API dati di YouTube]**.
1. Vicino alla parte superiore della **[!UICONTROL API dati YouTube v3]** pagina, tocca **[!UICONTROL Abilita]** per accenderlo.
1. Per utilizzare l’API, potrebbero essere necessarie delle credenziali. Se necessario, tocca **[!UICONTROL Crea credenziali]**.
1. Da **[!UICONTROL Da dove chiamerai l’API?]** elenco a discesa, seleziona **[!UICONTROL Server web (ad esempio node.js, Tomcat)]**.
1. Sotto **[!UICONTROL A quali dati accederai?]** select **[!UICONTROL Dati utente]**.
1. Tocca **[!UICONTROL Di quali credenziali ho bisogno?]** pulsante.
1. Sotto la **[!UICONTROL Creare un ID client OAuth 2.0]** immetti un nome univoco.
1. Nel campo di testo sotto la **[!UICONTROL Origini Javascript autorizzate]** intestazione, immettere il seguente percorso, sostituendo il proprio dominio e il proprio numero di porta nel percorso, quindi premere **[!UICONTROL Invio]** per aggiungere il percorso all’elenco:

   `https://<servername.domain>:<port_number>`

   Ad esempio `https://1a2b3c.mycompany.com:4321`

   **Nota**: L’esempio di percorso sopra è destinato solo a scopo illustrativo.

1. Nel campo di testo sotto la **[!UICONTROL URI di reindirizzamento autorizzati]** immetti quanto segue, sostituendo il tuo dominio e il tuo numero di porta nel percorso, quindi premi Invio per aggiungere il percorso all&#39;elenco:

   `https://<servername.domain>:<port#>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Ad esempio `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **Nota**: L’esempio di percorso sopra è destinato solo a scopo illustrativo.

1. Tocca **[!UICONTROL Crea ID client]**.
1. Nella pagina Credenziali, sotto la sezione **[!UICONTROL Configurare la schermata di consenso OAuth 2.0]** selezionare l&#39;indirizzo Gmail che si sta utilizzando.
1. Nel campo di testo sotto la **[!UICONTROL Nome del prodotto visualizzato agli utenti]** intestazione , immetti ciò che desideri mostrare nella schermata di consenso.

   La schermata di consenso viene visualizzata all’amministratore AEM quando effettua l’autenticazione in YouTube; AEM contattare YouTube per l&#39;autorizzazione.

1. Tocca **[!UICONTROL Continua]**.
1. Sotto la **[!UICONTROL Scarica le credenziali]** intestazione, toccare **[!UICONTROL Scarica]**.
1. Salva il `client_id.json` file.

   Questo file json scaricato sarà necessario quando configuri YouTube in Adobe Experience Manager in un secondo momento.

1. Tocca **[!UICONTROL Fine]**.

   Ora creerai un canale YouTube.

### Creazione di un canale YouTube {#creating-a-youtube-channel}

Per pubblicare video in YouTube è necessario disporre di uno o più canali. Se hai già creato un canale YouTube, puoi saltare questa attività e passare a **Aggiunta di tag per la pubblicazione**.

>[!CAUTION]
>
>Assicurati di aver già configurato uno o più canali in YouTube &amp;ast;before&amp;ast; aggiungi canali in Impostazioni YouTube in AEM (vedi [Configurazione di YouTube in AEM](#setting-up-youtube-in-aem) qui sotto). Se non riesci a farlo, non riceverai alcun avviso relativo all’assenza di canali esistenti. Tuttavia, l’autenticazione Google si verifica ancora quando aggiungi un canale, ma non è disponibile un’opzione per scegliere quale canale viene inviato il video.

**Per creare un canale YouTube:**

1. Vai a [https://www.youtube.com](https://www.youtube.com/) e accedi utilizzando le credenziali del tuo account Google.
1. Nell’angolo in alto a destra della pagina YouTube, tocca l’immagine del profilo (potrebbe anche essere visualizzata come lettera all’interno di un cerchio colorato), quindi tocca **[!UICONTROL Impostazioni di YouTube]** (icona a forma di ingranaggio circolare).
1. Sulla **[!UICONTROL Panoramica]** sotto **[!UICONTROL Funzionalità aggiuntive]** intestazione, toccare **[!UICONTROL Visualizza tutti i miei canali o crea un nuovo canale]**.
1. Sulla **[!UICONTROL Canali]** pagina, tocca **[!UICONTROL Crea un nuovo canale]**.
1. Sulla **[!UICONTROL Account del marchio]** nella pagina **[!UICONTROL Nome account del marchio]** immetti un nome commerciale o un altro nome di canale scelto per la pubblicazione delle risorse video, quindi tocca **[!UICONTROL Crea]**.

   Ricorda il nome immesso qui perché sarà necessario immetterlo nuovamente quando configuri YouTube in AEM.

1. (Facoltativo) Se necessario, aggiungi altri canali.

   Ora è possibile aggiungere tag per la pubblicazione.

### Aggiungi tag per la pubblicazione {#adding-tags-for-publishing}

Per pubblicare nei video in YouTube, AEM associa i tag a uno o più canali YouTube. Per aggiungere tag per la pubblicazione, consulta [Amministrazione dei tag](/help/sites-administering/tags.md).

Oppure, se si desidera utilizzare i tag predefiniti in AEM, è possibile saltare questa attività e passare a [Abilitazione dell’agente di replica YouTube Publish](#enabling-the-youtube-publish-replication-agent).

### Abilitare l’agente di replica YouTube Publish {#enabling-the-youtube-publish-replication-agent}

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Implementazione > Replica > Agenti sull’autore]**.
1. Sulla **[!UICONTROL Agenti dell&#39;autore]** pagina, tocca **[!UICONTROL YouTube Publish (YouTube)]**.
1. Sulla barra degli strumenti, a destra di Impostazioni, tocca **[!UICONTROL Modifica]**.
1. Seleziona la **[!UICONTROL Abilitato]** per attivare l&#39;agente di replica.
1. toccare **[!UICONTROL OK]**.

   Ora configurerai YouTube in AEM.

### Configurare YouTube in AEM {#setting-up-youtube-in-aem}

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Implementazione > Cloud Services]**.
1. Sotto la **[!UICONTROL Servizi di terzi]** intestazione, sotto YouTube, tocca **[!UICONTROL Configura ora]**.
1. In **[!UICONTROL Crea configurazione]** immettere un titolo (obbligatorio) e un nome (facoltativo) nei rispettivi campi.
1. Tocca **[!UICONTROL Crea]**.
1. In **[!UICONTROL Impostazioni account YouTube]** nella finestra di dialogo **[!UICONTROL Nome applicazione]** , immetti l’ID progetto Google .

   Hai specificato l’ID del progetto quando hai inizialmente configurato le impostazioni di Google Cloud in precedenza.

   Lascia la **[!UICONTROL Impostazione account YouTube]** finestra di dialogo aperta; ritornerà su di esso tra un momento.

1. Utilizzando un editor di testo normale, apri il file JSON scaricato e salvato in precedenza nell’attività Configurazione delle impostazioni di Google Cloud .
1. Seleziona e copia l’intero testo JSON.
1. Torna a **[!UICONTROL Impostazioni account YouTube]** finestra di dialogo. Nel campo **[!UICONTROL Configurazione JSON]**, incolla il testo JSON.
1. Tocca **[!UICONTROL OK]**.

   Ora configurerai i canali YouTube in AEM.

1. A destra di **[!UICONTROL Canali disponibili]**, tocca **[!UICONTROL +]** (icona del segno più).
1. In **[!UICONTROL Impostazioni canale YouTube]** nella finestra di dialogo **[!UICONTROL Titolo]** immettere il nome del canale creato nell&#39;attività **C[!UICONTROL Creazione di un canale YouTube]** prima.

   Facoltativamente, puoi aggiungere una descrizione.

1. Tocca **[!UICONTROL OK]**.
1. Viene visualizzata l’autenticazione YouTube/Google. Se non hai già effettuato l’accesso all’account Google Cloud, salta questo passaggio.

   * Immetti il nome utente e la password Google associati all’ID progetto Google e al testo JSON sopra riportato.
   * A seconda del numero di canali di cui dispone l’account, vengono visualizzati due o più elementi. Seleziona un canale. Non selezionare l&#39;indirizzo di posta elettronica.
   * Nella pagina successiva, tocca **[!UICONTROL Accetta]** per consentire l&#39;accesso a questo canale.

1. Tocca **[!UICONTROL Consenti]**.

   Ora imposterai i tag per la pubblicazione.

1. **Impostazione dei tag per la pubblicazione** - Sul **[!UICONTROL Cloud Services > YouTube]** , tocca **[!UICONTROL Matita]** per modificare l’elenco dei tag da utilizzare.
1. Tocca l’icona dell’elenco a discesa (cursore verso il basso) per visualizzare l’elenco dei tag disponibili in AEM.
1. Tocca uno o più tag per aggiungerli.

   Per eliminare un tag aggiunto, selezionalo e tocca **[!UICONTROL X]**.

1. Al termine dell’aggiunta dei tag desiderati, tocca **[!UICONTROL OK]**.

   Ora pubblichi i video sul tuo canale YouTube.

### (Facoltativo) Automatizza l&#39;impostazione delle proprietà predefinite di YouTube per i video caricati {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

Puoi automatizzare l’impostazione delle proprietà di YouTube al caricamento dei video. A tal fine, crea un profilo di elaborazione dei metadati in AEM.

Per creare il profilo di elaborazione dei metadati, devi prima copiare i valori dai campi **[!UICONTROL Etichetta campo]**, **[!UICONTROL Mappa su proprietà]** e **[!UICONTROL Scelte]**, tutti disponibili in Schemi metadati per i video. Quindi, puoi aggiungere i valori per creare il tuo profilo di elaborazione dei metadati video di YouTube.

**Per automatizzare facoltativamente l’impostazione delle proprietà predefinite di YouTube per i video caricati:**

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Risorse > Schemi di metadati]**.
1. Tocca **[!UICONTROL default]**. (Non aggiungere un segno di spunta alla casella di selezione a sinistra di &quot;default&quot;.)
1. Sulla **[!UICONTROL default]** , seleziona la casella a sinistra di **[!UICONTROL video]**, quindi tocca **[!UICONTROL Modifica]**.
1. Sulla **[!UICONTROL Editor schema metadati]** , tocca **[!UICONTROL Avanzate]** scheda .
1. Nell’intestazione Pubblicazione YouTube , tocca **[!UICONTROL Categoria YouTube]**. (Non toccare l’elenco a discesa Categoria YouTube ).
1. Sul lato destro della pagina, sotto il **[!UICONTROL Impostazioni]** esegui le seguenti operazioni:

   * In **[!UICONTROL Etichetta campo]** campo di testo, selezionare e copiare il valore.

      Incolla il valore copiato in un editor di testo aperto. Questo valore sarà necessario in un secondo momento quando crei il profilo di elaborazione dei metadati. Lascia aperto l’editor di testo.

   * In **[!UICONTROL Mappa su proprietà]** campo di testo, selezionare e copiare il valore.

      Incolla il valore copiato nell’editor di testo aperto. Questo valore sarà necessario in un secondo momento quando crei il profilo di elaborazione dei metadati. Lascia aperto l’editor di testo.

   * Sotto **[!UICONTROL Scelte]**, seleziona e copia il valore predefinito da utilizzare (ad esempio Persone e blog o Scienza e tecnologia).

      Incolla il valore copiato nell’editor di testo aperto. Questo valore sarà necessario in un secondo momento quando crei il profilo di elaborazione dei metadati. Lascia aperto l’editor di testo.

1. Nell’intestazione Pubblicazione YouTube , tocca **[!UICONTROL Privacy di YouTube]**. (Non toccare l’elenco a discesa Privacy di YouTube.)
1. Sul lato destro della pagina, sotto il **[!UICONTROL Impostazioni]** esegui le seguenti operazioni:

   * In **[!UICONTROL Etichetta campo]** campo di testo, selezionare e copiare il valore.

      Incolla il valore copiato in un editor di testo aperto. Questo valore sarà necessario in un secondo momento quando crei il profilo di elaborazione dei metadati. Lascia aperto l’editor di testo.

   * In **[!UICONTROL Mappa su proprietà]** campo di testo, selezionare e copiare il valore.

      Incolla il valore copiato nell’editor di testo aperto. Questo valore sarà necessario in un secondo momento quando crei il profilo di elaborazione dei metadati. Lascia aperto l’editor di testo.

   * Sotto **[!UICONTROL Scelte]**, seleziona e copia il valore predefinito da utilizzare. Le scelte sono raggruppate in coppie di due. Il campo inferiore della coppia è il valore predefinito che si desidera copiare, ad esempio pubblico, non elencato o privato.

      Incolla il valore copiato nell’editor di testo aperto. Questo valore sarà necessario in un secondo momento quando crei il profilo di elaborazione dei metadati. Lascia aperto l’editor di testo.

1. Vicino all&#39;angolo superiore destro del **[!UICONTROL Editor schema metadati]** pagina, tocca **[!UICONTROL Annulla]**.
1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Risorse > Profili metadati]**.

1. Sulla **[!UICONTROL Profili metadati]** tocca **[!UICONTROL Crea]**. In **[!UICONTROL Aggiungi profilo metadati]** nella finestra di dialogo **[!UICONTROL Titolo del profilo]** campo di testo, immettere il nome `YouTube Video`.
1. Sulla **[!UICONTROL Editor profili metadati]** , tocca **[!UICONTROL Avanzamento]** scheda .
1. Aggiungi i valori di pubblicazione YouTube copiati al profilo facendo quanto segue:

   * Sul lato destro della pagina, tocca **[!UICONTROL Crea modulo]** scheda .
   * Trascina il componente etichettato **[!UICONTROL Intestazione sezione]** a sinistra e rilasciarla nell’area del modulo.
   * Tocca **[!UICONTROL Etichetta campo]** per selezionare il componente.
   * Sul lato destro della pagina, sotto il **[!UICONTROL Impostazioni]** nella scheda **[!UICONTROL Etichetta campo]** campo di testo, immettere `YouTube Publishing`.
   * Tocca **[!UICONTROL Crea modulo]** , quindi trascina il componente etichettato **[!UICONTROL Testo a riga singola]** e rilasciarlo sotto il **[!UICONTROL Pubblicazione YouTube]** intestazione appena creata.
   * Tocca **[!UICONTROL Etichetta campo]** per selezionare il componente.
   * Sul lato destro della pagina, sotto il **[!UICONTROL Impostazioni]** , incolla **[!UICONTROL Pubblicazione YouTube]** values (**[!UICONTROL Etichetta campo]** valore e **[!UICONTROL Mappa su proprietà]** (Valore) copiato in precedenza, nei rispettivi campi del modulo. Incolla **[!UICONTROL Scelte]** nel **[!UICONTROL Valore predefinito]** campo .

1. Aggiungi i valori di YouTube Privacy copiati al profilo facendo quanto segue:

   * Sul lato destro della pagina, tocca **[!UICONTROL Crea modulo]** scheda .
   * Trascina il componente etichettato **[!UICONTROL Intestazione sezione]** a sinistra e rilasciarla nell’area del modulo.
   * Tocca **[!UICONTROL Etichetta campo]** per selezionare il componente.
   * Sul lato destro della pagina, sotto la scheda Impostazioni, nel campo di testo Etichetta campo, immetti `YouTube Privacy`.
   * Tocca **[!UICONTROL Crea modulo]** , quindi trascina il componente etichettato **[!UICONTROL Testo a riga singola]** e rilasciarlo sotto il **[!UICONTROL Privacy di YouTube]** intestazione appena creata.
   * Tocca **[!UICONTROL Etichetta campo]** per selezionare il componente.
   * Sul lato destro della pagina, sotto il **[!UICONTROL Impostazioni]** , incolla **[!UICONTROL Pubblicazione YouTube]** values (**[!UICONTROL Etichetta campo]** valore e **[!UICONTROL Mappa su proprietà]** (Valore) copiato in precedenza, nei rispettivi campi del modulo. Incolla **[!UICONTROL Scelte]** nel **[!UICONTROL Valore predefinito]** campo .

1. Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Salva]**.
1. Applica il profilo metadati Pubblicazione YouTube alle cartelle in cui stai per caricare i video. Sarà necessario impostare sia il profilo metadati che il profilo video.

   Consulta le sezioni [Profili di metadati](metadata-profiles.md) e [Profili video](video-profiles.md).

### Pubblicare video sul canale YouTube {#publishing-videos-to-your-youtube-channel}

Ora puoi associare i tag aggiunti in precedenza alle risorse video. Questo processo AEM sapere quali risorse pubblicare sul tuo canale YouTube.

Per pubblicare contenuti da YouTube, AEM utilizza la funzione **[!UICONTROL Pubblicare su YouTube]** , che consente di monitorare l’avanzamento e visualizzare eventuali informazioni di errore.
Consulta la sezione [Monitoraggio della codifica video e stato della pubblicazione su YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Per pubblicare i video sul tuo canale YouTube:**

1. In AEM, accedi a una risorsa video da pubblicare sul tuo canale YouTube.
1. Seleziona la risorsa video.

   Indipendentemente dalla risorsa video selezionata, ad esempio il video sorgente originale o una rappresentazione codificata, il video sorgente originale viene sempre caricato.

1. Sulla barra degli strumenti, tocca **[!UICONTROL Proprietà]**.
1. In **[!UICONTROL Base]** , sotto l’intestazione Metadati , tocca **[!UICONTROL Sfoglia]** a destra del **[!UICONTROL Tag]** campo .
1. Sulla **[!UICONTROL Seleziona tag]** , passare ai tag da utilizzare e selezionare uno o più tag.
1. Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Conferma]** icona.
1. Nell’angolo in alto a destra della pagina delle proprietà del video, tocca **[!UICONTROL Salva]**.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Pubblica > Pubblica]**.

   Facoltativamente, puoi verificare il video pubblicato sul tuo canale YouTube.

### (Facoltativo) Verifica il video pubblicato su YouTube {#optional-verifying-the-published-video-on-youtube}

Puoi monitorare l’avanzamento della pubblicazione (o dell’annullamento della pubblicazione) in YouTube.

Consulta la sezione [Monitoraggio della codifica video e stato della pubblicazione su YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

I tempi di pubblicazione possono variare notevolmente a seconda di numerosi fattori che includono il formato del video principale, le dimensioni del file e il traffico di caricamento. Il processo di pubblicazione può richiedere da qualche minuto a diverse ore. Inoltre, tenete presente che i formati a risoluzione più elevata vengono resi molto più lentamente. Ad esempio, 720p e 1080p richiedono molto più tempo per apparire rispetto a 480p.

Dopo otto ore se vedi ancora un messaggio di stato che dice **[!UICONTROL Caricato (elaborazione, attendi)]**, prova a rimuovere il video dal nostro sito e caricarlo di nuovo.

### Collegare gli URL di YouTube all’applicazione Web {#linking-youtube-urls-to-your-web-application}

Puoi ottenere una stringa URL YouTube generata da Dynamic Media dopo la pubblicazione del video. Quando copi l’URL di YouTube, questo viene inserito negli Appunti, in modo da poterlo incollare come necessario nelle pagine del sito web o dell’applicazione.

L’URL di YouTube non è disponibile per la copia finché non avrai pubblicato la risorsa video in YouTube.

**Per collegare gli URL YouTube alla tua applicazione web:**

1. Passa a YouTube *pubblicato* risorsa video di cui desideri copiare l’URL, quindi selezionalo.

   Gli URL di YouTube sono disponibili solo per la copia *dopo* hai il primo *pubblicato* le risorse video in YouTube.

1. Sulla barra degli strumenti, tocca **[!UICONTROL Proprietà]**.
1. Tocca **[!UICONTROL Avanzate]** scheda .
1. Sotto la **[!UICONTROL Pubblicazione YouTube]** a) **[!UICONTROL URL YouTube]** Elenca, seleziona e copia il testo dell’URL nel browser web per visualizzare l’anteprima della risorsa o per aggiungerla alla pagina del contenuto web.

### Annullare la pubblicazione di video per rimuoverli da YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Quando annulli la pubblicazione di una risorsa video in AEM, il video viene rimosso da YouTube.

>[!CAUTION]
>
>Se rimuovi un video direttamente da YouTube, AEM ignora e continua a comportarsi come se il video fosse ancora pubblicato in YouTube. Annulla sempre la pubblicazione di una risorsa video da YouTube tramite AEM.

Per rimuovere il contenuto da YouTube, AEM utilizza il **[!UICONTROL Annullare la pubblicazione da YouTube]** , che consente di monitorare l’avanzamento e visualizzare eventuali informazioni di errore.
Consulta la sezione [Monitoraggio della codifica video e stato della pubblicazione su YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Per annullare la pubblicazione dei video e rimuoverli da YouTube:**

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti]** > **[!UICONTROL Risorse]**.
1. Passa alle risorse video da cui desideri annullare la pubblicazione dal canale YouTube.
1. In una modalità di selezione delle risorse, seleziona una o più risorse video pubblicate.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Annulla pubblicazione]** > **[!UICONTROL Annulla pubblicazione]**.

## Monitoraggio della codifica video e stato della pubblicazione in YouTube {#monitoring-video-encoding-and-youtube-publishing-progress}

Quando carichi un nuovo video in una cartella a cui è stata applicata la codifica video o lo pubblichi su youtube, puoi monitorare l’avanzamento (o il mancato funzionamento) della codifica video/pubblicazione youtube in diversi modi. L’avanzamento effettivo della pubblicazione in YouTube è disponibile solo tramite i registri, ma se ha esito negativo o positivo è elencato in modi aggiuntivi descritti nella procedura seguente. Inoltre, puoi ricevere notifiche e-mail quando un flusso di lavoro o una codifica video di pubblicazione di YouTube viene completata o interrotta.

### Avanzamento monitor {#monitoring-progress}

Per monitorare l’avanzamento (compresa la codifica non riuscita/pubblicazione YouTube):

1. Visualizza l’avanzamento della codifica video nella cartella delle risorse:

   * In **[!UICONTROL Vista a schede]**, l’avanzamento della codifica video viene visualizzato per percentuale sulla risorsa. In caso di errore, queste informazioni vengono visualizzate anche sulla risorsa.

      ![chlimage_1-429](assets/chlimage_1-429.png)

   * In **[!UICONTROL Vista a elenco]**, l’avanzamento della codifica video viene visualizzato in **[!UICONTROL Stato di elaborazione]** colonna. In caso di errore, il messaggio viene visualizzato nella stessa colonna.

      ![chlimage_1-430](assets/chlimage_1-430.png)

      Questa colonna non viene visualizzata per impostazione predefinita. Per abilitare la colonna, seleziona **[!UICONTROL Visualizza impostazioni]** dal **[!UICONTROL Viste]** e aggiungi il menu a discesa **[!UICONTROL Stato di elaborazione]** tocca e colonna **[!UICONTROL Aggiorna]**.

      ![chlimage_1-431](assets/chlimage_1-431.png)

1. Visualizza l’avanzamento nei dettagli della risorsa. Quando tocchi una risorsa, apri il menu a discesa e seleziona **[!UICONTROL Timeline]**. Per limitare l’attività al flusso di lavoro, ad esempio la codifica o la pubblicazione in YouTube, seleziona **[!UICONTROL Flussi di lavoro]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   Nella timeline vengono visualizzate tutte le informazioni sul flusso di lavoro, ad esempio la codifica . Per la pubblicazione di YouTube, l’ **[!UICONTROL Flusso di lavoro]** timeline include anche il nome del canale YouTube e l’URL del video YouTube. Inoltre, vengono visualizzate le notifiche di errore nella sezione **[!UICONTROL Flusso di lavoro]** timeline.

   >[!NOTE]
   >
   >Potrebbero essere necessari tempi lunghi per la registrazione dei messaggi di errore/errore a causa di più configurazioni del flusso di lavoro in **[!UICONTROL tentativi]**, **[!UICONTROL ritardo]** e **[!UICONTROL timeout]** da [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)ad esempio:
   >
   >* Configurazione della coda dei processi Sling Apache
   >* Adobe Granite Workflow External Process Job Handler
   >* Coda timeout flusso di lavoro Granite

   > 
   >In queste configurazioni è possibile regolare le proprietà dei **[!UICONTROL nuovi tentativi]**, dei **[!UICONTROL tentativi ritardati]** e del **[!UICONTROL timeout]**.

1. Per i flussi di lavoro in corso, consulta **Istanze del flusso di lavoro** disponibile da **[!UICONTROL Strumenti > Flusso di lavoro > Istanze]**.

   >[!NOTE]
   >
   >Potresti aver bisogno di diritti amministrativi per accedere al **[!UICONTROL Strumenti]** menu.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   Seleziona l’istanza e tocca **[!UICONTROL Cronologia aperta]**.

   ![chlimage_1-434](assets/chlimage_1-434.png)

   Da **[!UICONTROL Istanze del flusso di lavoro]** è inoltre possibile sospendere, terminare o rinominare i flussi di lavoro. Vedi [Amministrazione dei flussi di lavoro](/help/sites-administering/workflows-administering.md) per ulteriori informazioni.

1. Per i lavori non riusciti, vedi **Errori del flusso di lavoro** disponibile da **[!UICONTROL Strumenti > Flusso di lavoro > Errori]**. In **[!UICONTROL Errore flusso di lavoro]** sono elencate tutte le attività del flusso di lavoro che hanno generato errori.

   >[!NOTE]
   >
   >Potresti aver bisogno di diritti amministrativi per accedere al **[!UICONTROL Strumenti]** menu.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >Potrebbero essere necessari tempi lunghi per la registrazione del messaggio di errore a causa di più configurazioni del flusso di lavoro nelle **[!UICONTROL tentativi]**, **[!UICONTROL ritardo]** e **[!UICONTROL timeout]** da [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)ad esempio:
   >
   >* Configurazione della coda dei processi Sling Apache
   >* Adobe Granite Workflow External Process Job Handler
   >* Coda timeout flusso di lavoro Granite

   >
   >In queste configurazioni è possibile regolare le proprietà dei **[!UICONTROL nuovi tentativi]**, dei **[!UICONTROL tentativi ritardati]** e del **[!UICONTROL timeout]**.

1. Per i flussi di lavoro completati, vedi **[!UICONTROL Archivio flussi di lavoro]** disponibile da **[!UICONTROL Strumenti > Flusso di lavoro > Archivia]**. **[!UICONTROL Archivio flussi di lavoro]** elenca tutte le attività del flusso di lavoro che sono state completate.

   Potresti aver bisogno di diritti amministrativi per accedere al **[!UICONTROL Strumenti]** menu.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. È possibile ricevere notifiche e-mail relative a processi del flusso di lavoro interrotti o non riusciti. Queste notifiche e-mail sono configurabili da un amministratore.
Vedi [Configurazione delle notifiche e-mail](#configuring-e-mail-notifications).

#### Configurare le notifiche e-mail {#configuring-e-mail-notifications}

Potresti aver bisogno di diritti amministrativi per accedere al **[!UICONTROL Strumenti]** menu.

La modalità di configurazione della notifica dipende dal fatto se si desidera ricevere notifiche per i processi di codifica o pubblicazione in YouTube:

* Per i processi di codifica, puoi accedere alla pagina di configurazione per tutte le notifiche e-mail AEM flusso di lavoro all’indirizzo **[!UICONTROL Strumenti > Operazioni > Console web]** e ricercando **[!UICONTROL Servizio notifiche e-mail flusso di lavoro del giorno CQ]**. Vedi [Configurazione della notifica e-mail in AEM](/help/sites-administering/notification.md). È possibile selezionare o deselezionare le caselle di controllo per **[!UICONTROL Notifica per interruzione]** o **[!UICONTROL Notifica al completamento]** di conseguenza.

* Per i lavori di pubblicazione di YouTube, procedi come segue:

1. In AEM, seleziona **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]**.
1. Seleziona la **[!UICONTROL Pubblicare su YouTube]** flusso di lavoro, quindi tocca **[!UICONTROL Modifica]**.
1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL Caricamento YouTube]** passaggio del flusso di lavoro, quindi tocca **[!UICONTROL Modifica]**.
1. Tocca **[!UICONTROL Argomento]s** scheda .
1. È possibile selezionare o deselezionare le seguenti caselle di controllo:

   * **[!UICONTROL Inizio pubblicazione]**
   * **[!UICONTROL Errore di pubblicazione]**
   * **[!UICONTROL Completamento pubblicazione]**, che include informazioni sui canali e sugli URL

   Deselezionando una casella di controllo non riceverai la notifica e-mail specificata dal flusso di lavoro di pubblicazione di YouTube.

   >[!NOTE]
   >
   >Queste e-mail sono specifiche di YouTube e si aggiungono alle notifiche e-mail generiche del flusso di lavoro. Di conseguenza, puoi ricevere due set di notifiche e-mail, ovvero la notifica generica disponibile nel **Servizio notifiche e-mail flusso di lavoro del giorno CQ** e uno specifico per YouTube a seconda delle impostazioni di configurazione.

## Visualizzare i rapporti video {#viewing-video-reports}

I rapporti video sono disponibili quando si esegue Dynamic Media - Modalità ibrida; i rapporti non sono disponibili quando si esegue la modalità Dynamic Media - Scene7.

I rapporti video mostrano diverse metriche aggregate in un determinato periodo di tempo per aiutarti a monitorare che i video *pubblicati *singoli e aggregati abbiano prestazioni come previsto. I seguenti dati di metriche principali sono aggregati per tutti i video pubblicati sull’intero sito web:

* Inizio video
* Percentuale completata
* Tempo medio sul video
* Tempo totale sul video
* Video per visita

Un tavolo di tutti *pubblicato* i video sono elencati anche per consentire di tenere traccia dei video più visualizzati sul sito web in base al numero di avvii video totali.

Quando tocchi un nome video nell’elenco, questo ti mostra il rapporto di fidelizzazione (a discesa) del video sotto forma di grafico a linee. Il grafico mostra il numero di visualizzazioni per un dato momento di tempo durante la riproduzione del video. Quando si riproduce il video, la barra verticale traccia in sincronizzazione con l&#39;indicatore del tempo nel lettore. Le perdite nei dati del grafico a linee indicano dove il pubblico si allontana dal disinteresse.

Se il video è stato codificato al di fuori di Adobe Experience Manager Dynamic Media, il grafico a discesa di conservazione del pubblico e i dati in percentuale di riproduzione nella tabella non sono disponibili.

Vedi anche [Configurazione dei Cloud Services Dynamic Media](/help/assets/config-dynamic.md).

>[!NOTE]
>
>Il tracciamento e il reporting dei dati si basano esclusivamente sull’uso del lettore video Dynamic Media e del lettore video associato preimpostati. Di conseguenza, non è possibile tenere traccia e generare rapporti sui video riprodotti da altri lettori video.

Per impostazione predefinita, al primo accesso a Rapporti video, il rapporto visualizza i dati video a partire dal primo del mese corrente e termina con la data del mese corrente. Tuttavia, puoi ignorare l’intervallo di date predefinito specificando il tuo intervallo di date. Alla successiva immissione di Rapporti video, viene utilizzato l’intervallo di date specificato.

Affinché i rapporti video funzionino correttamente, viene automaticamente creato un ID suite di rapporti quando sono configurati Cloud Services Dynamic Media. Allo stesso tempo, l’ID suite di rapporti viene inviato al server di pubblicazione in modo che sia disponibile per la funzione Copia URL quando visualizzi l’anteprima delle risorse. Tuttavia, questo richiede che il server di pubblicazione sia già configurato. Se il server di pubblicazione non è configurato, è comunque possibile pubblicare per visualizzare il rapporto video, tuttavia sarà necessario tornare alla configurazione di Dynamic Media Cloud e toccare **OK**.

**Per visualizzare i rapporti video:**

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti]** > **[!UICONTROL Risorse]** > **[!UICONTROL Rapporti video]**.
1. Nella pagina Rapporti video , effettua una delle seguenti operazioni:

   * Nell’angolo in alto a destra, tocca **[!UICONTROL Aggiorna rapporto video]** icona.

      Utilizzare Aggiorna solo se la data di fine del rapporto è il giorno corrente. In questo modo puoi visualizzare il tracciamento video che si è verificato dall’ultima volta che hai eseguito il rapporto.

   * Nell’angolo in alto a destra, tocca **[!UICONTROL Selettore data]** icona.

      Specifica l’intervallo di date iniziale e finale per il quale vuoi visualizzare i dati video, quindi tocca **[!UICONTROL Esegui rapporto]**.
   La **[!UICONTROL Metriche principali]** casella di gruppo identifica varie misurazioni aggregate per tutti *pubblicato* video nel sito.

1. Nella tabella in cui sono elencati i video più pubblicati, tocca un nome video per riprodurre il video e guarda anche il rapporto di fidelizzazione (drop-off) del video.

### Visualizzare rapporti video basati su un visualizzatore video creato con l’SDK per visualizzatori Dynamic Media HTML5 {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

Se utilizzi un visualizzatore video predefinito fornito da Dynamic Media o se hai creato un predefinito per visualizzatori personalizzato basato su un visualizzatore video preconfigurato, non sono necessari ulteriori passaggi per visualizzare i rapporti video. Tuttavia, se hai creato un visualizzatore video personalizzato basato sull’API SDK per visualizzatori HTML5, procedi come segue per assicurarti che il visualizzatore video invii eventi di tracciamento ai rapporti video Dynamic Media.

Utilizza la [Guida di riferimento per i visualizzatori Dynamic Media di Adobe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html) e [API SDK visualizzatore HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) per creare visualizzatori video personalizzati.

Per visualizzare i rapporti video basati su un visualizzatore video creato utilizzando l’API SDK per visualizzatori HTML5:

1. Passa a qualsiasi risorsa video pubblicata.
1. Seleziona **[!UICONTROL Visualizzatori]** dall’elenco a discesa dell’angolo in alto a sinistra della pagina della risorsa.
1. Seleziona un predefinito per visualizzatori video e copia il codice da incorporare.
1. Nel codice di incorporamento, trova la riga con quanto segue:

   `videoViewer.setParam("config2", "<value>");`

   La `config2` abilita il tracciamento nei visualizzatori HTML5. È anche un predefinito specifico per l’azienda che contiene le informazioni di configurazione per Video Reporting e per le configurazioni Adobe Analytics specifiche per il cliente.

   Il valore corretto per il parametro config2 si trova sia nella funzione **[!UICONTROL Incorpora codice]** che in copia **[!UICONTROL URL]**. Nell’URL dal comando di copia **[!UICONTROL URL]**, il parametro da cercare è `&config2=<value>`. Il valore è quasi sempre `companypreset`, ma in alcuni casi può anche essere `companypreset-1`, `companypreset-2` e così via.

1. Nel codice del visualizzatore video personalizzato, aggiungi AppMeasurementBridge.jsp alla pagina del visualizzatore facendo quanto segue:

   * In primo luogo, determina se è necessario `&preset` parametro .

      Se la `config2` parameter is `companypreset`, *not* necessità `&preset=parameter`.

      Se `config2` è diverso, imposta il parametro predefinito come `config2` parametro . Ad esempio, se `config2=companypreset-2`, aggiungi `&param2=companypreset-2` all’URL AppMeasurementBridge.jsp.

   * Quindi, aggiungi lo script AppMeasurementBridge.jsp:

      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Crea il componente TrackingManager facendo quanto segue:

   * Dopo la chiamata `s7sdk.Util.init();` crea un&#39;istanza TrackingManager per tenere traccia degli eventi aggiungendo quanto segue:

      `var trackingManager = new s7sdk.TrackingManager();`

   * Connetti i componenti a TrackingManager eseguendo le operazioni seguenti:

      In `s7sdk.Event.SDK_READY` handler di eventi, allega il componente di cui desideri tenere traccia a TrackingManager.

      Ad esempio, se il componente è `videoPlayer`, aggiungi

      `trackingManager.attach(videoPlayer);`

      per allegare il componente a trackingManager. Per tenere traccia di più visualizzatori su una pagina, utilizza più componenti di gestione del tracciamento.

   * Crea l&#39;oggetto AppMeasurementBridge aggiungendo quanto segue:

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

   * Aggiungi la funzione di tracciamento aggiungendo quanto segue:

      ```
      trackingManager.setCallback(appMeasurementBridge.track, 
       appMeasurementBridge);
      ```
   L&#39;oggetto appMeasurementBridge dispone di una funzione di tracciamento incorporata. Tuttavia, puoi anche fornire un supporto personalizzato per supportare più sistemi di tracciamento o altre funzionalità.

<!--    For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

## Aggiungere sottotitoli codificati al video {#adding-captions-to-video}

Puoi estendere la portata dei tuoi video sui mercati globali aggiungendo sottotitoli codificati a singoli video o a set di video adattivi. Aggiungendo i sottotitoli si evita la necessità di duplicare l&#39;audio o la necessità di utilizzare gli altoparlanti nativi per registrare nuovamente l&#39;audio per ogni lingua diversa. Il video viene riprodotto nella lingua in cui è stato registrato. I sottotitoli in lingua straniera vengono visualizzati in modo che le persone di lingue diverse possano ancora comprendere la porzione audio.

I sottotitoli codificati consentono inoltre una maggiore accessibilità per le persone non udenti o ipoudenti.

>[!NOTE]
>
>Il lettore video utilizzato deve supportare la visualizzazione dei sottotitoli.

Dynamic Media è in grado di convertire i file di didascalie in formato JSON (JavaScript Object Notation). Questa conversione significa che puoi incorporare il testo JSON in una pagina web come trascrizione nascosta ma completa del video. I motori di ricerca possono quindi eseguire ricerche per indicizzazione e indicizzazione del contenuto per rendere i video più facilmente individuabili e fornire ai clienti ulteriori dettagli sul contenuto video.

Vedi [Distribuzione di contenuti statici (non immagine)](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) in *Guida API di Dynamic Media Image Serving e Rendering* per ulteriori informazioni sull’utilizzo della funzione JSON in un URL.

**Per aggiungere sottotitoli o sottotitoli al video:**

1. Utilizza un&#39;applicazione o un servizio di terze parti per creare il file di sottotitoli/sottotitoli video.

   Assicurati che il file creato sia conforme allo standard WebVTT (Web Video Text Tracks). L’estensione del nome del file dei sottotitoli è .vtt. Per ulteriori informazioni sullo standard WebVTT per i sottotitoli, consulta

   Vedi [WebVTT: Formato Tracce testo video web](https://dev.w3.org/html5/webvtt/).

   Sono disponibili strumenti e servizi gratuiti e premium da utilizzare per creare file di sottotitoli/sottotitoli all’esterno di Dynamic Media. Ad esempio, per creare un semplice file di sottotitoli video senza stili, è possibile utilizzare il seguente strumento online gratuito per la creazione e modifica di sottotitoli:

   [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   Per ottenere risultati ottimali, utilizza lo strumento in Internet Explorer 9 o versioni successive, Google Chrome o Safari.

   Nello strumento , nella **[!UICONTROL Immettere l&#39;URL del file video]** incolla l’URL copiato del file video, quindi tocca **[!UICONTROL Load]**. Consulta la sezione [Ottenere l’URL per una risorsa](linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) per conoscere l’URL del file video stesso, che potrai incollare nel campo **[!UICONTROL Enter URL of video file (Inserisci URL del file video)]**. A quel punto, Internet Explorer, Chrome o Safari possono riprodurre il video in modalità nativa.

   Segui ora le istruzioni visualizzate sul sito per creare e salvare il file WebVTT. Al termine, copia il contenuto del file della didascalia e incollalo in un editor di testo normale e salvalo con un’estensione .vtt.

   >[!NOTE]
   >
   >Per il supporto globale dei sottotitoli video in più lingue, tieni presente che lo standard WebVTT richiede la creazione di file .vtt separati e di chiamate per ogni lingua che desideri supportare.

   In genere, è consigliabile denominare il file VTT della didascalia con lo stesso nome del file video e aggiungerlo con le impostazioni internazionali della lingua, ad esempio -EN, o -FR, o -DE e così via. In questo modo è possibile automatizzare la generazione degli URL video utilizzando il sistema di gestione dei contenuti web esistente.

1. In AEM, carica il file della didascalia WebVTT in DAM.
1. Passa a *pubblicato* risorsa video da associare al file di didascalia caricato.

   Gli URL sono disponibili per la copia solo *dopo* la prima *pubblicazione* delle risorse.

   Vedi [Pubblicazione delle risorse.](publishing-dynamicmedia-assets.md)

1. Effettua una delle operazioni seguenti:

   * Per un’esperienza di visualizzazione video a comparsa, tocca **[!UICONTROL URL]**. Nella finestra di dialogo URL, seleziona e copia l’URL negli Appunti, quindi passa l’URL a un semplice editor di testo. Aggiungi l’URL copiato del video con la seguente sintassi:

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      Tieni presente che `,1` alla fine del percorso della didascalia. Subito dopo l’estensione .vtt nel percorso, puoi attivare o disattivare il pulsante dei sottotitoli nella barra del lettore video impostando su `,1` o `,0`, rispettivamente.

   * Per un’esperienza di visualizzazione video incorporata, tocca **[!UICONTROL Codice di incorporamento]**. Nella finestra di dialogo Incorpora codice , seleziona e copia il codice da incorporare negli Appunti, quindi incolla il codice in un semplice editor di testo. Aggiungi il codice di incorporamento copiato con la seguente sintassi:

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      Tieni presente che `,1` alla fine del percorso della didascalia. Subito dopo l’estensione .vtt nel percorso, puoi attivare o disattivare il pulsante dei sottotitoli nella barra del lettore video impostando su `,1` o `,0`, rispettivamente.

## Aggiungere marcatori capitolo al video {#adding-chapter-markers-to-video}

Per rendere più semplice la visualizzazione e la navigazione dei video in formato esteso, è possibile aggiungere marcatori capitolo a singoli video o a set di video adattivi. Quando un utente riproduce il video, può toccare i marcatori capitolo nella timeline del video (nota anche come scorrimento video) per navigare facilmente fino al loro punto di interesse, oppure passare immediatamente a nuovi contenuti, dimostrazioni, esercitazioni e così via.

>[!NOTE]
>
>Il lettore video utilizzato deve supportare l&#39;uso di marcatori capitolo. I lettori video Dynamic Media supportano i marcatori capitolo, ma l&#39;utilizzo di lettori video di terze parti potrebbe non essere supportato.

Se lo desideri, puoi creare e assegnare un marchio al tuo visualizzatore video personalizzato con capitoli invece di utilizzare un predefinito per visualizzatori video. Per istruzioni su come creare un visualizzatore HTML5 personalizzato con navigazione nei capitoli, nell’API SDK per visualizzatori di Adobe HTML5 fai riferimento all’intestazione &quot;Personalizzazione del comportamento utilizzando i modificatori&quot; sotto le classi `s7sdk.video.VideoPlayer` e `s7sdk.video.VideoScrubber`. Consulta la sezione [API SDK visualizzatore HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html) documentazione.

È possibile creare un elenco di capitoli per il video nello stesso modo in cui si creano le didascalie. In altre parole, si crea un file WebVTT. Si noti, tuttavia, che questo file deve essere separato da qualsiasi file di didascalia WebVTT che si potrebbe utilizzare; non è possibile combinare didascalie e capitoli in un unico file WebVTT.

È possibile utilizzare l&#39;esempio seguente come esempio del formato utilizzato per creare un file WebVTT con spostamento dei capitoli:

### File WebVTT con navigazione dei capitoli video {#webvtt-file-with-video-chapter-navigation}

```xml
WEBVTT 
Chapter 1 
00:00.000 --> 01:04.364 
The bicycle store behind it all. 
Chapter 2 
01:04.364 --> 02:00.944 
Creative Cloud. 
Chapter 3 
02:00.944 --> 03:02.937 
Ease of management for a working solution. 
Chapter 4 
03:02.937 --> 03:35.000 
Cost-efficient access to rapidly evolving technology.
```

Nell’esempio precedente, `Chapter 1` è l’identificatore del cue ed è facoltativo. Il tempo di cue di `00:00:000 --> 01:04:364` specifica l&#39;ora di inizio e di fine del capitolo, in `00:00:000` formato. Le ultime tre cifre sono millisecondi e possono essere lasciate come `000`, se necessario. Titolo del capitolo `The bicycle store behind it all` è la descrizione effettiva del contenuto del capitolo. L’identificatore di cue, il tempo di cue iniziale e il titolo del capitolo vengono visualizzati in un pop-up nel lettore video quando un utente passa il puntatore del mouse su un punto di cue visivo nella timeline del video.

Poiché si utilizza un visualizzatore video HTML5, assicurarsi che il file capitolo creato segua lo standard WebVTT (Web Video Text Tracks). L&#39;estensione del nome del capitolo è .vtt. Per ulteriori informazioni sullo standard WebVTT per i sottotitoli, consulta

Vedi [WebVTT: Formato Tracce testo video web](https://dev.w3.org/html5/webvtt/)

**Per aggiungere marcatori capitolo al video:**

1. Utilizzando un semplice editor di testo esterno a AEM, crea il file dei capitoli video.

   Per il supporto globale dei capitoli video in lingue diverse dall&#39;inglese, tieni presente che lo standard WebVTT richiede la creazione di file .vtt separati e di chiamate per ogni lingua che desideri supportare.

1. Salva il `.vtt` file in codifica UTF8 per evitare problemi con il rendering dei caratteri nel testo del titolo del capitolo.

   Generalmente, si desidera assegnare al file VTT capitolo lo stesso nome del file video e aggiungerlo con capitoli. In questo modo è possibile automatizzare la generazione degli URL video utilizzando il sistema di gestione dei contenuti web esistente.
1. In AEM, carica il file del capitolo WebVTT.

   Vedi [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets).

1. Effettua una delle operazioni seguenti:

   <table> 
     <tbody> 
      <tr> 
       <td>Per un’esperienza di visualizzazione video a comparsa</td> 
       <td> 
       <ol> 
       <li>Passa a <i>pubblicato </i>risorsa video da associare al file capitolo caricato. Gli URL sono disponibili per la copia solo <i>dopo</i> la prima <i>pubblicazione</i> delle risorse. Vedi <a href="/help/assets/publishing-dynamicmedia-assets.md">Pubblicazione delle risorse.</a></li> 
       <li>Dal menu a discesa, tocca <strong>Visualizzatori</strong>.</li> 
       <li>Nella barra a sinistra, tocca il nome predefinito del visualizzatore video. Un’anteprima del video viene aperta in una pagina separata.</li> 
       <li>Nella barra a sinistra, in basso, tocca <strong>URL</strong>.</li> 
       <li>Nella finestra di dialogo URL, seleziona e copia l’URL negli Appunti, quindi passa l’URL in un semplice editor di testo.</li> 
       <li>Aggiungi l’URL copiato del video con la sintassi seguente per associarlo all’URL copiato al file del capitolo:<br /> <br /> <code>&amp;navigation=&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;</code><br /> </li> 
      </ol> </td> 
      </tr> 
      <tr> 
       <td>Per un’esperienza di visualizzazione video incorporata<br /> </td> 
       <td> 
       <ol> 
       <li>Passa a <i>pubblicato </i>risorsa video da associare al file capitolo caricato. Gli URL sono disponibili per la copia solo <i>dopo</i> la prima <i>pubblicazione</i> delle risorse. Vedi <a href="/help/assets/publishing-dynamicmedia-assets.md">Pubblicazione delle risorse.</a></li> 
       <li>Dal menu a discesa, tocca <strong>Visualizzatori</strong>.</li> 
       <li>Nella barra a sinistra, tocca il nome predefinito del visualizzatore video. Un’anteprima del video viene aperta in una pagina separata.</li> 
       <li>Nella barra a sinistra, in basso, tocca <strong>Incorpora</strong>.</li> 
       <li>Nella finestra di dialogo Incorpora codice selezionare e copiare l’intero codice negli Appunti, quindi incollarlo in un semplice editor di testo.</li> 
       <li>Aggiungi il codice di incorporamento del video con la sintassi seguente per associarlo all'URL copiato al file del capitolo:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li> 
      </ol> </td> 
      </tr> 
     </tbody> 
    </table>

## Informazioni sulle miniature video {#about-video-thumbnails}

Puoi scegliere tra una delle dieci miniature generate automaticamente da Dynamic Media per aggiungere al video. Il lettore video visualizza la miniatura selezionata quando una risorsa video viene utilizzata con il componente Dynamic Media nell’ambiente di authoring di AEM Sites, AEM Mobile o AEM Screens. La miniatura funge da immagine statica che rappresenta al meglio il contenuto dell’intero video e incoraggia ulteriormente gli utenti a toccare il pulsante Play.

In base al tempo totale del video, Dynamic Media cattura dieci immagini in miniatura (impostazione predefinita) con 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81% e 91% nel video. Le dieci miniature persistono, il che significa che se decidi di scegliere una miniatura diversa in un secondo momento, non devi rigenerare la serie. Puoi visualizzare in anteprima le dieci immagini in miniatura e quindi selezionare quella che desideri utilizzare con il video. Se si desidera passare all’impostazione predefinita, è possibile utilizzare CRXDE Lite per configurare l’intervallo di tempo durante il quale vengono generate le immagini in miniatura. Ad esempio, se desideri generare dal video solo una serie di quattro immagini in miniatura con spaziatura uniforme, puoi configurare l’intervallo di tempo al 24%, 49%, 74% e 99%.

Idealmente, puoi aggiungere una miniatura video in qualsiasi momento dopo aver caricato il video, ma prima di pubblicarlo sul tuo sito web.

Se preferisci, puoi scegliere di caricare una miniatura personalizzata per rappresentare il video invece di utilizzare una miniatura generata da Dynamic Media. Ad esempio, puoi creare un’immagine miniatura personalizzata con il titolo del video, un’immagine di apertura accattivante o un’immagine molto specifica acquisita dal video. L’immagine miniatura video personalizzata caricata deve avere una risoluzione massima di 1280 x 720 pixel (larghezza minima di 640 pixel) e non deve essere superiore a 2 MB.

>[!NOTE]
>
>Le miniature video personalizzate sono disponibili solo quando si esegue Dynamic Media - Modalità ibrida.

### Aggiungi una miniatura video {#adding-a-video-thumbnail}

1. Passa a una risorsa video caricata alla quale desideri aggiungere una miniatura video.
1. In modalità di selezione delle risorse, dalla **[!UICONTROL Vista a elenco]** o **[!UICONTROL Vista a schede]**, tocca la risorsa video.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Visualizza proprietà]** icona (un cerchio con un &quot;i&quot; al suo interno).
1. Sul video **[!UICONTROL Proprietà]** pagina, tocca **[!UICONTROL Modifica miniatura]**.
1. Sulla **[!UICONTROL Modifica miniatura]** sulla barra degli strumenti, tocca **[!UICONTROL Seleziona frame]**.

   Dynamic Media genera immagini in miniatura di serie dal video, in base all’intervallo di tempo predefinito o all’intervallo di tempo personalizzato.

1. Anteprima delle miniature generate, quindi seleziona quella da aggiungere al video.
1. Tocca **[!UICONTROL Salva modifica]**.

   L’immagine in miniatura del video viene aggiornata per utilizzare la miniatura selezionata. Se successivamente decidi di modificare l’immagine in miniatura, puoi tornare alla **[!UICONTROL Modifica miniatura]** e selezionane uno nuovo.

   Se hai configurato nuovi intervalli di tempo predefiniti o hai caricato un nuovo video per sostituire il video esistente, dovrai far rigenerare le miniature in Dynamic Media.

   Vedi [Configurazione dell’intervallo di tempo predefinito per la generazione delle miniature video](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

#### Configura l’intervallo di tempo predefinito per la generazione delle miniature video {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

Quando configuri e salvi il nuovo intervallo di tempo predefinito, la modifica si applica automaticamente solo ai video caricati in futuro. Non applica automaticamente il nuovo predefinito ai video caricati in precedenza. Per i video esistenti, devi rigenerare le miniature.

Vedi [Aggiunta di una miniatura video](#adding-a-video-thumbnail).

Per configurare l’intervallo di tempo predefinito generato per la generazione delle miniature video, procedere come segue.

1. In AEM, tocca **[!UICONTROL Strumenti]** > **[!UICONTROL Generale]** > **[!UICONTROL CRXDE Lite]**.

1. Nella pagina CRXDE Lite, nel pannello della directory a sinistra, naviga verso `o etc/dam/imageserver/configuration/jcr:content/settings.`

   se il pannello della directory non è visibile, potrebbe essere necessario toccare l’icona >> a sinistra della scheda Home.

1. Sul pannello in basso a destra, nella **[!UICONTROL Proprietà]** tabulazione, doppio tocco `thumbnailtime`.
1. Nella finestra di dialogo Modifica miniatura, utilizzare i campi di testo per immettere valori di intervallo come percentuali.

   * Tocca l’icona del segno più (+) per aggiungere uno o più campi del valore dell’intervallo. Per visualizzare l’icona, potrebbe essere necessario scorrere fino alla parte inferiore della finestra di dialogo.
   * Toccare l’icona del segno meno (-) a destra di un campo del valore dell’intervallo per eliminarlo dall’elenco.
   * Tocca l’icona freccia su e l’icona freccia giù per riordinare i valori dell’intervallo.

1. Tocca **[!UICONTROL OK]** per tornare al **[!UICONTROL Proprietà]** scheda .
1. Nell’angolo in alto a sinistra della pagina CRXDE Lite, tocca **[!UICONTROL Salva tutto]**, quindi tocca **[!UICONTROL Pagina principale]** nell’angolo in alto a sinistra per tornare a AEM.

   Vedi [Aggiunta di una miniatura video.](#adding-a-video-thumbnail)

### Aggiungi una miniatura video personalizzata {#adding-a-custom-video-thumbnail}

>[!NOTE]
>
>Questa funzione è disponibile solo quando si esegue Dynamic Media - Modalità ibrida.

1. Passa a una risorsa video caricata alla quale desideri aggiungere una miniatura video.
1. In modalità di selezione delle risorse, dalla **[!UICONTROL Vista a elenco]** o **[!UICONTROL Vista a schede]**, tocca la risorsa video.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Visualizza proprietà]** icona (un cerchio con un &quot;i&quot; al suo interno).
1. Sul video **[!UICONTROL Proprietà]** pagina, tocca **[!UICONTROL Modifica miniatura]**.
1. Sulla **[!UICONTROL Modifica miniatura]** sulla barra degli strumenti, tocca **[!UICONTROL Carica nuova miniatura]**.
1. Passa all’immagine della miniatura da utilizzare, selezionala, quindi tocca **[!UICONTROL Apri]** per iniziare a caricare l’immagine in AEM
1. Una volta caricata correttamente l’immagine, nella **[!UICONTROL Modifica miniatura]** pagina, tocca **[!UICONTROL Salva modifiche]**.

   La miniatura personalizzata viene aggiunta al video.
