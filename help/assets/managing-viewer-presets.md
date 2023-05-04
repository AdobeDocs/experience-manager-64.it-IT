---
title: Gestione dei predefiniti per visualizzatori Dynamic Media
seo-title: Managing Dynamic Media viewer presets
description: Come creare e gestire i predefiniti visualizzatore Dynamic Media
seo-description: How to create and manage Dynamic Media viewer presets
uuid: 31ef7a4e-2053-43b5-ac6c-cdc4b30c3914
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e78bb08a-a923-4399-b3f7-13aa4b7994d5
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
exl-id: 53e53cb7-1854-44e9-9516-51bcc99378b4
feature: Viewer Presets
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4256'
ht-degree: 12%

---

# Gestione dei predefiniti per visualizzatori Dynamic Media {#managing-viewer-presets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Un predefinito per visualizzatori Dynamic Media è una raccolta di impostazioni che determinano il modo in cui gli utenti visualizzano le risorse multimediali sullo schermo del computer e sui dispositivi mobili. Gli amministratori possono creare i predefiniti visualizzatore. Le impostazioni sono disponibili per una serie di opzioni di configurazione del visualizzatore. Ad esempio, puoi modificare le dimensioni di visualizzazione o il comportamento di zoom del visualizzatore.

Per istruzioni su come creare e personalizzare i predefiniti visualizzatore HTML5, consulta l’Adobe Dynamic Media *Documentazione API dell’SDK per visualizzatori HTML5*. L&#39;SDK è disponibile sul server di pubblicazione IS incorporato nell&#39;SDK stesso. Ogni versione della libreria include la propria documentazione SDK.

Percorso: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
Ad esempio, 3.10 SDK: [https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)

Vedi anche [Guida di riferimento per i visualizzatori Dynamic Media di Adobe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

Questa sezione descrive come creare, modificare e gestire i predefiniti per visualizzatori. Puoi applicare un predefinito visualizzatore a una risorsa ogni volta che la visualizzi in anteprima. Vedi [Applicazione dei predefiniti per visualizzatori](viewer-presets.md).

>[!NOTE]
>
>Tieni presente che la modifica di qualsiasi *predefiniti per visualizzatori pronti all’uso* non è uno scenario supportato. Se tenti di modificare un predefinito visualizzatore predefinito, ti viene richiesto di salvare il predefinito visualizzatore con un nuovo nome.

## Accessibilità della tastiera per i visualizzatori {#keyboard-accessibility-for-viewers}

Tutti i visualizzatori predefiniti supportano l’accessibilità da tastiera.

Vedi anche [Accessibilità e navigazione da tastiera](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html).

## Gestione dei predefiniti per visualizzatori Dynamic Media {#managing-presets}

Per aggiungere, modificare, eliminare, pubblicare, annullare la pubblicazione e visualizzare in anteprima i predefiniti visualizzatore in AEM, tocca **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]**.

![strumenti-risorse](assets/tools-assets.png)

>[!NOTE]
>
>Per impostazione predefinita, quando selezioni Visualizzatori nella vista Dettaglio di una risorsa, il sistema mostra 15 predefiniti visualizzatore. Puoi aumentare questo limite. Consulta la sezione [Aumento del numero di predefiniti visualizzatore](#increasing-the-number-of-viewer-presets-that-display).

## Supporto visualizzatore per pagine web reattive {#viewer-support-for-responsive-designed-web-pages}

Pagine web diverse hanno esigenze diverse. Ad esempio, a volte si desidera una pagina web che fornisca un collegamento che apra il visualizzatore HTML5 in una finestra separata del browser. In altri casi, potrebbe essere necessario incorporare il visualizzatore HTML5 direttamente nella pagina di hosting. In quest&#39;ultimo caso, la pagina web può avere un layout statico. Oppure può essere *reattivo* e vengono visualizzati in modo diverso su diversi dispositivi o per diverse dimensioni della finestra del browser. Per soddisfare queste esigenze, tutti i visualizzatori HTML5 predefiniti forniti con Dynamic Media supportano sia le pagine web statiche che le pagine web reattive.

Vedi [Libreria di immagini reattive](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html) in *Guida API di Image Serving* per ulteriori informazioni su come incorporare visualizzatori reattivi nelle pagine web.

>[!NOTE]
>
>Prima di utilizzarli, è necessario pubblicare tutti i visualizzatori predefiniti.\
>Vedi [Pubblicazione dei predefiniti per visualizzatori.](#publishing-viewer-presets)

## Compatibilità del sistema predefinito del visualizzatore  {#viewer-preset-system-compatibility}

Tutti i predefiniti visualizzatore forniti con Dynamic Media sono completamente compatibili con i seguenti sistemi:

* Desktop
* Apple iPhone
* Apple iPad
* Smartphone Android
* Tablet Android
* Per i video, è disponibile un supporto aggiuntivo per la riproduzione MP4 [Blackberry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) e [Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx).

### Tipi di contenuti multimediali avanzati per i predefiniti per visualizzatori {#rich-media-types-for-viewer-presets}

Gli amministratori possono aggiungere e personalizzare i seguenti tipi di contenuti multimediali durante la creazione di nuovi predefiniti per visualizzatori.

| Tipi di contenuti multimediali avanzati | Descrizione |
|:---|:---|
| **Set carosello** | I punti attivi, le mappe immagine o entrambi vengono aggiunti a una serie di due o più immagini. Un cliente può scorrere le immagini a sinistra o a destra e quindi fare clic su un punto attivo di un&#39;immagine per ulteriori dettagli o per acquistare direttamente dalla categoria, dalla pagina principale o dalle pagine di destinazione di un sito web. |
| **Zoom a comparsa** | Visualizza una seconda immagine dell&#39;area ingrandita accanto all&#39;immagine originale. Nessun controllo da utilizzare: gli utenti spostano la selezione sull’area da visualizzare. |
|  | Nel determinare l’utilizzo completo della larghezza di banda per questo visualizzatore, considera che sia l’immagine principale che l’immagine a comparsa siano servite nel visualizzatore. Le dimensioni dell’immagine principale (larghezza e altezza dello stage) e il fattore di zoom determinano le dimensioni dell’immagine a comparsa. Per evitare che la dimensione del file a comparsa diventi troppo grande, bilanciare i due valori seguenti: in caso di dimensioni dell&#39;immagine principale grandi, abbassare il valore del fattore di zoom. (La larghezza a comparsa e l’altezza a comparsa determinano le dimensioni della finestra a comparsa, ma non le dimensioni dell’immagine a comparsa fornita nel visualizzatore.) |
|  | Ad esempio, se la dimensione dell’immagine principale è di 350 x 350 pixel con un fattore di zoom di 3, l’immagine a comparsa risultante sarà di 1050 x 1050 pixel. Se le dimensioni dell&#39;immagine principale sono 300 x 300 pixel, con un fattore di zoom di 4, l&#39;immagine a comparsa è 1200 x 1200 pixel. A seconda dell’impostazione della qualità JPEG (le impostazioni consigliate sono comprese tra 80 e 90), è possibile ridurre notevolmente la dimensione del file. I fattori di zoom consigliati sono da 2,5 a 4, a seconda delle dimensioni dell&#39;immagine principale. |
| **Zoom in linea** | Visualizza un&#39;immagine dell&#39;area ingrandita all&#39;interno del visualizzatore originale. Nessun controllo da utilizzare. In altre parole, gli utenti spostano la selezione sull’area da visualizzare. |
| **Set immagini** | Nel visualizzatore per set di immagini, gli utenti possono vedere diverse viste o varianti di colore di un elemento facendo clic su una miniatura. Questo visualizzatore offre anche strumenti di zoom per esaminare attentamente le immagini. |
| **Immagine interattiva** | Gli hotspot vengono aggiunti alle parti di un&#39;immagine su cui un cliente può fare clic per ulteriori dettagli o per acquistare direttamente dalla categoria, dalla pagina principale o dalle pagine di destinazione di un sito web. |
| **Video interattivo** | Le miniature vengono aggiunte ai segmenti della timeline di un video su cui un cliente può quindi fare clic per ulteriori dettagli o per acquistare direttamente dalla categoria, dalla pagina principale o dalle pagine di destinazione di un sito web. |
| **File multimediali diversi** | Visualizza diversi tipi di contenuti multimediali in un visualizzatore. Puoi includere set 360 gradi, set di immagini, immagini e video. |
| **Immagine panoramica** | I visualizzatori Panoramic Image (Immagine panoramica) e Panoramic VR (VR panoramico) consentono di riprodurre immagini panoramiche sferiche per immergere gli utenti in un&#39;esperienza di visualizzazione a 360° di una stanza, di una proprietà, di una posizione o di un paesaggio. |
|  | Affinché un&#39;immagine caricata possa essere definita come panorama sferico, deve avere uno o entrambi i seguenti elementi: <ul><li>Rapporto di formato 2:1.</li><li>Etichettate con le parole chiave equirettangolari o sferiche e panoramiche, o sferiche e panoramiche. Vedi [Utilizzo dei tag](../sites-authoring/tags.md).</li></ul> |
|  | Sia le proporzioni che i criteri delle parole chiave si applicano alle risorse panoramiche della pagina dei dettagli delle risorse che il componente WCM &quot;Elemento multimediale panoramico&quot;. |
|  | Importante: Questo visualizzatore è disponibile solo in modalità Dynamic Media - Scene7. |
| **Set 360 gradi** | Fornisce diverse viste di un&#39;immagine in modo che gli utenti possano ruotare l&#39;oggetto per esaminare i diversi lati e angoli. |
| **Video** | Riproduce video utilizzando lo streaming a bit rate progressivo o adattivo. Lo streaming a bit rate adattivo esegue automaticamente il rilevamento del dispositivo e della larghezza di banda per fornire la qualità video corretta nel formato giusto. |
| **Zoom verticale** | Il visualizzatore Zoom verticale consente di massimizzare l’esperienza di visualizzazione delle immagini di un prodotto per offrire agli utenti la migliore rappresentazione di un prodotto. La posizione verticale dei campioni effettua le seguenti operazioni: <ul><li>Assicura che i campioni siano al di sopra della piega. Con i campioni orizzontali, a seconda delle dimensioni dello schermo  desktop dell’utente, i campioni non erano visibili finché l’utente non ha fatto scorrere la pagina verso il basso. Posizionando i campioni in verticale nel visualizzatore, questi saranno visibili indipendentemente dalle dimensioni dello schermo dell’utente.</li><li>Massimizza le dimensioni dell&#39;immagine principale. Con i campioni orizzontali, è necessario riservare spazio sulla pagina per garantirne la visibilità. Questo posizionamento ha ridotto le dimensioni dell&#39;immagine principale. Con un layout di campioni verticali, tuttavia, non è necessario allocare questo spazio. È quindi possibile massimizzare le dimensioni dell&#39;immagine principale.</li></ul> |
| **Zoom** | Consente agli utenti di ingrandire l’area facendo clic su di essa. Gli utenti possono fare clic sui controlli per ingrandire, ridurre e ripristinare le dimensioni predefinite dell&#39;immagine. |

## Elenco dei predefiniti visualizzatore {#list-of-out-of-the-box-viewer-presets}

La tabella seguente identifica tutti i predefiniti visualizzatore predefiniti forniti con Dynamic Media.

Vedi anche [Demo live](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Per informazioni sulle versioni supportate del browser web e del sistema operativo per i visualizzatori, consulta le Note sulla versione dei visualizzatori.

Vedi *Note sulla versione dei visualizzatori* nella tabella dei contenuti [Guida di riferimento visualizzatori](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

>[!NOTE]
>
>Tutti i predefiniti per visualizzatori in Dynamic Media sono già attivati (on), ma è necessario pubblicarli.\
>Vedi [Pubblicazione dei predefiniti per visualizzatori](#publishing-viewer-presets).
>
>I nuovi predefiniti visualizzatore creati e aggiunti devono essere attivati *e* pubblicato.\
>Vedi [Attivazione o disattivazione dei predefiniti per visualizzatori](#activating-or-deactivating-viewer-presets) e [Pubblicazione dei predefiniti per visualizzatori](#publishing-viewer-presets).

| Titolo predefinito visualizzatore | Tipo | Nome file CSS |
|:---|:---|:---|
| Carosello_Punteggiato_scuro | Set_carosello | html5_carouselviewer_dotted_dark.css |
| Carosello_Punteggiato_light | Set_carosello | html5_carouselviewer_dotted_light.css |
| Carousel_Numeric_dark | Set_carosello | html5_carouselviewer_numeric_dark.css |
| Carousel_Numeric_light | Set_carosello | html5_carouselviewer_numeric_light.css |
| A comparsa | Zoom_A_comparsa | html5_flyoutviewer.css |
| ImageSet_dark | Set immagini | html5_zoomviewer_dark.css |
| ImageSet_light | Set immagini | html5_zoomviewer_light.css |
| InlineMixedMedia_dark | File multimediali diversi | html5_inlinemixedmediaviewer_dark.css |
| InlineMixedMedia_light | File multimediali diversi | html5_inlinemixedmediaviewer_light.css |
| InlineZoom | Zoom_A_comparsa | html5_inlinezoomviewer.css |
| MixedMedia_dark | File multimediali diversi | html5_mixedmediaviewer_dark.css |
| MixedMedia_light | File multimediali diversi | html5_mixedmediaviewer_light.css |
| Immagine panoramica | Panoramic_Image | html5_panoramicimage.css |
| PanoramicImageVR | Panoramic_Image | html5_panoramicimage.css |
| Banner_Shoppable | Immagine interattiva | html5_interactiveimage.css |
| Shoppable_Video_dark | Video interattivo | html5_interactivevideoviewer_dark.css |
| Shoppable_Video_light | Video interattivo | html5_interactivevideovewer_light.css |
| SpinSet_dark | Set_Spin | html5_spinviewer_dark.css |
| SpinSet_light | Set_Spin | html5_spinviewer_light.css |
| Video (con supporto per sottotitoli codificati) | Video | html5_videoviewer.css |
| Video_social (include il supporto per sottotitoli codificati e social media) | Video | html5_videoviewersocial.css |
| Zoom_scuro | Zoom | html5_basiczoomviewer_dark.css |
| Zoom_light | Zoom | html5_basiczoomviewer_light.css |
| ZoomVerticale_scura | Zoom_verticale | html5_zoomverticalviewer_dark.css |
| Zoom_Verticale | Zoom_verticale | html5_zoomverticalviewer_light.css |

### Matrice di gesti dei visualizzatori per dispositivi mobili supportati {#supported-mobile-viewers-gestures-matrix}

La tabella seguente identifica i gesti del visualizzatore mobile supportati sui dispositivi iOS, Android 2.x e Android 3.x.

| Gesto | Zoom a comparsa | Zoom | Set 360 gradi |
|---|---|---|---|
| **Trascina** | Pannelli | Pannelli | Pannelli |
| **Tocca** | Mostra la finestra a comparsa | Mostra o nasconde l’interfaccia utente | Mostra o nasconde l’interfaccia utente |
| **Doppio tocco** | Non applicabile | Ingrandisce o reimposta | Ingrandisce o reimposta |
| **Apri il pizzico** | Non applicabile | Ingrandisce (solo iOS e Android 3x) | Ingrandisce (solo iOS e Android 3x) |
| **Chiudi** | Non applicabile | Esegue lo zoom indietro (solo iOS e Android 3x) | Esegue lo zoom indietro (solo iOS e Android 3x) |
| **Passaggio del dito** | Barra dei campioni a scorrimento | Scorre le immagini | Giri |
| **Flick** | Barra dei campioni a scorrimento | Scorre le immagini | Giri |

## Aumento del numero di predefiniti visualizzatore Dynamic Media da visualizzare {#increasing-the-number-of-viewer-presets-that-display}

AEM mostra un’ampia varietà di predefiniti visualizzatore quando visualizzi una risorsa da **[!UICONTROL Vista dettagli > Visualizzatori]**. È possibile aumentare o diminuire il numero di visualizzatori visualizzati.

**Per aumentare il numero di predefiniti visualizzatore Dynamic Media da visualizzare**:

1. Passa a **[!UICONTROL CRXDE Lite]** ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Passa al nodo di elenco dei predefiniti visualizzatore in `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. Nella proprietà **[!UICONTROL limit]**, modifica **[!UICONTROL Valore]**, che corrisponde a 15 per impostazione predefinita, inserendo un numero a piacere.
1. Passa alla sorgente dati predefinita visualizzatore in `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. In **[!UICONTROL limite]** modifica il numero nel numero desiderato, ad esempio `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Tocca **[!UICONTROL Salva tutto]**.

## Creazione di un nuovo predefinito visualizzatore Dynamic Media {#creating-a-new-viewer-preset}

La creazione di predefiniti per visualizzatori consente di applicare diverse impostazioni per visualizzare e interagire con le risorse. Tuttavia, non è necessario creare nuovi predefiniti visualizzatore. Se lo desideri, puoi utilizzare i predefiniti predefiniti per visualizzatori già forniti con AEM Assets.

Se scegli di creare un nuovo predefinito visualizzatore, dopo averlo salvato lo stato del visualizzatore viene attivato automaticamente (impostato su **On**) nel **[!UICONTROL Predefiniti visualizzatore]** pagina. Questo stato significa che è visibile nel **[!UICONTROL Dynamic Media]** e **[!UICONTROL File multimediali interattivi]** e ogni volta che visualizzi l’anteprima di un’immagine o di un video.

Alcuni predefiniti per visualizzatori hanno impostazioni esclusive che possono influenzare l’uso e il comportamento generale del visualizzatore. A seconda del predefinito per visualizzatori che stai creando, potresti voler essere a conoscenza di queste considerazioni speciali.

Vedi [Considerazioni speciali per la creazione di un predefinito visualizzatore interattivo](#special-considerations-for-creating-an-interactive-viewer-preset).

Vedi [Considerazioni speciali per la creazione di un predefinito visualizzatore banner carosello](#special-considerations-for-creating-a-carousel-banner-viewer-preset).

**Per creare un nuovo predefinito visualizzatore Dynamic Media**:

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]**.

   ![visualizzatori predefiniti](assets/viewerpresets.png)

1. Sulla **[!UICONTROL Predefiniti visualizzatore]** sulla barra degli strumenti, tocca **[!UICONTROL Crea]**.
1. In **[!UICONTROL Nuovo predefinito per visualizzatori]** nella finestra di dialogo **[!UICONTROL Nome predefinito]** immetti il nome del nuovo predefinito. Scegli con attenzione un nome che non potrà essere modificato dopo aver toccato **[!UICONTROL Crea]**.

   Quando salvi il predefinito più avanti in questi passaggi, il nome viene visualizzato nella pagina Predefiniti visualizzatore sotto la **[!UICONTROL Titolo predefinito]** intestazione di colonna.

1. Sulla **[!UICONTROL Tipo di contenuti multimediali]** menu a discesa, seleziona il tipo di predefinito visualizzatore da creare, quindi tocca nell’angolo in alto a destra della pagina **[!UICONTROL Crea]**.

   Vedi [Tipi di contenuti multimediali avanzati per i predefiniti per visualizzatori](#rich-media-types-for-viewer-presets).

1. Sulla **Modifica predefinito visualizzatore** , tocca **[!UICONTROL Aspetto]** scheda .
1. Effettua una delle operazioni seguenti:

   * In **[!UICONTROL Tipo selezionato]** dal menu a discesa, selezionate un componente di cui desiderate personalizzare la progettazione visiva. In alternativa, puoi toccare qualsiasi elemento visivo del visualizzatore per selezionarlo per la configurazione.

      L’editor visivo consente di vedere l’effetto di una determinata proprietà su uno stile. È sufficiente impostare o regolare una proprietà per vedere immediatamente quale effetto ha sul visualizzatore utilizzando il campione a sinistra dell’editor.

      Le proprietà di stile CSS per ciascun tipo di predefinito visualizzatore sono descritte in qualsiasi &quot;Personalizzazione *&lt;viewer_name>* Argomento della Guida del visualizzatore in [Guida di riferimento visualizzatori](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

      Ad esempio, se stai creando un predefinito visualizzatore del tipo `Mixed_Media`, vedi [Personalizzazione del visualizzatore di file multimediali diversi](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) per un elenco e una descrizione di ciascuna proprietà.

   * Se hai definito le impostazioni stile in un file CSS separato, puoi caricarlo in AEM Assets. Tocca **[!UICONTROL Importa CSS]** sotto **[!UICONTROL Tipo selezionato]** menu a discesa (potrebbe essere necessario scorrere l’editor visivo per visualizzarlo) per trovare il file CSS caricato e associarlo al predefinito visualizzatore.

      Quando importi un file CSS, l’editor visivo controlla se il CSS utilizza gli indicatori di visualizzatore corretti. Ad esempio, se crei un visualizzatore zoom, tutte le regole CSS importate devono essere definite utilizzando il nome della classe del visualizzatore corrispondente `.s7mixedmediaviewer` definito su un elemento visualizzatore principale.

      È possibile importare CSS arbitrari creati a mano, purché definiscano correttamente i marcatori CSS per un determinato visualizzatore. (I marcatori CSS sono descritti in qualsiasi &quot;Personalizzazione *&lt;viewer name=&quot;&quot;>* Argomento della Guida del visualizzatore in [Guida di riferimento visualizzatori](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html). Ad esempio, per informazioni sui marcatori CSS per il visualizzatore zoom, consulta [Personalizzazione del visualizzatore zoom](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html).) È tuttavia possibile che l’editor visivo non comprenda alcuni valori CSS. In questi casi, l’editor visivo tenta di ignorare gli errori in modo che il CSS possa ancora funzionare.
   >[!NOTE]
   >
   >Se preferisci modificare il CSS direttamente nel relativo modulo non elaborato, tocca **[!UICONTROL Mostra/Nascondi CSS]** nel menu a discesa Tipo selezionato (potrebbe essere necessario scorrere l’editor visivo per visualizzare l’opzione).****
   >
   >Come l’editor visivo, quando apporti una modifica a una proprietà direttamente nel CSS, puoi vedere istantaneamente quale effetto ha sull’esempio del visualizzatore. Inoltre, la stessa proprietà viene aggiornata automaticamente nello stesso momento nell’editor visivo. Puoi quindi utilizzare l’editor CSS non elaborato o l’editor visivo oppure entrambi in modo intercambiabile.

   >[!NOTE]
   >
   >Per l&#39;immagine del pulsante, scegli l&#39;immagine 2x e carica opere d&#39;arte ad alta risoluzione. Quando si lavora con immagini interattive e banner acquistabili, è anche possibile scegliere tra diversi pulsanti pronti all’uso.

1. (Facoltativo) Vicino alla parte superiore del **[!UICONTROL Modifica predefinito visualizzatore]** pagina, tocca **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]** oppure **[!UICONTROL Telefono]** per definire in modo univoco gli stili visivi per dispositivi e tipi di schermo diversi.
1. Sulla **[!UICONTROL Modifica predefinito visualizzatore]** , tocca **Comportamento** scheda . In alternativa, puoi toccare o fare clic su qualsiasi elemento visivo del visualizzatore per configurarlo.
1. Dal menu a discesa **[!UICONTROL Tipo selezionato]**, scegli un componente di cui vuoi modificare i comportamenti.

   A molti componenti nell’editor visivo è associata una descrizione dettagliata. Queste descrizioni vengono visualizzate in caselle blu quando espandi un componente per visualizzarne i parametri associati.

   Alcuni tipi di Visualizzatore dispongono di componenti che consentono di specificare i comandi Image Server in un campo di testo **Comando IS**. Per un elenco dei comandi utilizzabili, consulta la sezione [Riferimento API di Server immagini](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html).

   >[!NOTE]
   >
   >**Se utilizzi un dispositivo touch, ad esempio un telefono o un tablet...**
   >
   >Dopo aver digitato un valore nel campo di testo, toccare un’altra posizione nell’interfaccia utente per inviare la modifica e chiudere la tastiera virtuale. Se tocchi **[!UICONTROL Invio]**, non si verifica alcuna azione.

1. Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Salva]**.
1. Pubblica il nuovo predefinito per visualizzatori. Devi pubblicare il predefinito prima di poterlo utilizzare sul tuo sito web.

   Vedi [Pubblicazione dei predefiniti per visualizzatori](#publishing-viewer-presets).

## Considerazioni speciali per la creazione di un predefinito visualizzatore interattivo {#special-considerations-for-creating-an-interactive-viewer-preset}

**Modalità di visualizzazione per le miniature delle immagini nel pannello**

Quando crei o modifichi un predefinito visualizzatore video interattivo, puoi scegliere quale **[!UICONTROL Modalità di visualizzazione]** impostazione da utilizzare quando si seleziona `InteractiveSwatches` dal **[!UICONTROL Componente selezionato]** menu a discesa sotto la **[!UICONTROL Comportamento]** scheda . La modalità di visualizzazione selezionata influisce su come e quando vengono visualizzate le miniature durante la riproduzione del video. Puoi scegliere una delle due opzioni `segment`modalità di visualizzazione (predefinita) o `continuous`modalità di visualizzazione.

| Modalità di visualizzazione | Descrizione |
|---|---|
| [!UICONTROL Segmento] | [!UICONTROL Segmento] è la modalità di visualizzazione predefinita per i predefiniti visualizzatore video interattivo preconfigurati Shoppable_Video_light e Shoppable_Video_dark e per tutti i predefiniti visualizzatore video interattivo creati dall’utente. |
|  | In questa modalità, quando a un segmento video sono assegnate meno miniature del numero di punti visibili nel pannello di visualizzazione, le miniature dei segmenti secondari successivi o precedenti non vengono estratte per riempire eventuali punti vuoti nel pannello. In altre parole, conserva la visualizzazione dei campioni assegnati al particolare segmento video. |
| [!UICONTROL Continuo] | In [!UICONTROL Continuo] modalità di visualizzazione, se il numero di miniature in un segmento è inferiore al numero visibile nel pannello, il visualizzatore include automaticamente la visualizzazione delle miniature dal segmento successivo o dal segmento precedente, nei casi in cui viene visualizzata l’ultima miniatura. |

**Comportamento dello scorrimento automatico nel visualizzatore video interattivo**

Il comportamento di scorrimento automatico delle miniature nel visualizzatore video interattivo funziona indipendentemente dalla modalità di visualizzazione scelta.

Quando crei o modifichi un predefinito per visualizzatori video interattivi, puoi accedere a **[!UICONTROL Scorrimento automatico]** dal **[!UICONTROL Comportamento]** scheda . Nella scheda Comportamento, seleziona il menu a discesa **[!UICONTROL Componenti selezionati]** e tocca **[!UICONTROL InteractiveSwatches]**. La **[!UICONTROL Scorrimento automatico]** la casella di controllo è elencata sotto il campo di testo Comando IS.

Se nel predefinito visualizzatore disattivi **[!UICONTROL Scorrimento automatico]** deselezionando la casella di controllo, durante la riproduzione del video da parte dell’utente il pannello visualizza solo la prima miniatura per l’intera durata del video. Tuttavia, un utente può scorrere manualmente le miniature utilizzando le icone di freccia su e giù, se necessario.

Durante la riproduzione del video, se hai abilitato tramite selezione l’opzione **[!UICONTROL Scorrimento automatico]** nel predefinito visualizzatore, le immagini in miniatura assegnate a un segmento video scorrono all’inizio di un segmento. Tuttavia, in alcuni casi, determinate miniature all’interno di un segmento vengono visualizzate con una durata raddoppiata rispetto alle altre miniature precedenti o successive. Questo comportamento si verifica perché il numero di miniature in un segmento è maggiore rispetto al numero visibile nel pannello e non è divisibile in modo uniforme.

Ad esempio, supponiamo di avere un segmento video di 30 secondi. E ci sono in totale nove miniature da visualizzare in 30 secondi. Il browser viene ridimensionato in modo tale che nel pannello di visualizzazione siano presenti quattro miniature visibili. Il segmento a 30 secondi di tempo video è diviso in tre sottosegmenti. La tabella seguente mostra il raggruppamento di cui vengono visualizzate le miniature per un determinato sottosegmento di tempo:

| **Sottosegmento video** | **Tempo del sottosegmento in secondi** | **Miniature visibili nel pannello** |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

Il sottosegmento video 3 non si estende oltre le miniature ad esso assegnate. Inoltre, le miniature 4, 6 e 7 sono visibili nel pannello con una durata doppia rispetto alle altre miniature.

La logica utilizzata dal visualizzatore per il numero di miniature visualizzate nel pannello in base al numero di posizioni disponibili è la seguente:

* Numero di sottosegmenti = arrotondato al sottosegmento successivo (numero di miniature/numero di slot visibili nel pannello miniature, in base alle dimensioni della finestra del browser).

   Utilizzando l&#39;esempio nella tabella precedente, 9 miniature / 4 slot = 2,25; la logica del visualizzatore la arrotonda a 3 segmenti secondari.

* Numero di miniature = da arrotondare alla miniatura successiva (numero di miniature/numero di sottosegmenti di video).

   Utilizzando l’esempio nella tabella precedente, 9 miniature / 3 sottosegmenti video = 3 miniature.

* Durata del sottosegmento = durata video totale/numero di sottosegmenti video.

   Utilizzando l’esempio nella tabella precedente, 30 secondi/3 segmenti video secondari = 10 secondi di visualizzazione di ciascun sottosegmento video.

### Considerazioni speciali per la creazione di un predefinito visualizzatore per banner carosello {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Quando si creano i predefiniti visualizzatore per banner carosello, è possibile accedere alle seguenti modifiche dello stile degli hotspot:

|  | **Descrizione** | **Azioni** |
|---|---|---|
| **Icona punto attivo** | Modificare l’icona utilizzata per il punto attivo | Per modificare l’immagine dell’icona del punto attivo, nella **[!UICONTROL Aspetto]** scheda in **[!UICONTROL Componente selezionato]**, tocca **[!UICONTROL ImageMapEffect]**. Seleziona **[!UICONTROL Sfondo]** alla voce **[!UICONTROL Icona]** e, nel campo **[!UICONTROL Immagine]**, individua l’immagine di sfondo desiderata. |

## Attivazione o disattivazione dei predefiniti per visualizzatori Dynamic Media {#activating-or-deactivating-viewer-presets}

I predefiniti per visualizzatori disponibili nell’interfaccia utente dipendono da quelli attivi nella modalità Creazione. Per impostazione predefinita, un predefinito per visualizzatori è *On* dopo averlo creato. Se disattiva il predefinito, questo non verrà visualizzato in modalità Autore. Se il predefinito viene pubblicato. verrà sempre pubblicato indipendentemente dal fatto che sia attivato o disattivato. Puoi disattivare i predefiniti per visualizzatori se l’elenco diventa troppo ingombrante o se non desideri che un predefinito per visualizzatori sia disponibile per l’uso.

**Per attivare o disattivare i predefiniti visualizzatore Dynamic Media**:

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]**.
1. Sulla **[!UICONTROL Predefinito visualizzatore]** sotto **[!UICONTROL Stato]** nell’intestazione della colonna, tocca l’interruttore per attivare o disattivare un predefinito visualizzatore.

   I predefiniti visualizzatore attivati presentano l’interruttore a destra, all’interno di una casella blu; i predefiniti visualizzatore disattivati presentano l’interruttore a sinistra, all’interno di una casella di colore grigio chiaro.

## Pubblicazione dei predefiniti per visualizzatori Dynamic Media {#publishing-viewer-presets}

Attivazione (o rotazione) *On*) lo stato di un predefinito per visualizzatori indica che è visibile nel componente Dynamic Media, nel componente File multimediali interattivi e ogni volta che visualizzi una risorsa.

Tuttavia, per fornire una risorsa con un predefinito visualizzatore, è necessario pubblicare anche il predefinito visualizzatore . Tutti i predefiniti visualizzatore devono essere attivati *e* pubblicato per ottenere l’URL o il codice di incorporamento per una risorsa. Devi attivare e pubblicare tutti i predefiniti visualizzatore che sono forniti con i Dynamic Media. I predefiniti visualizzatore personalizzati che crei e aggiungi vengono attivati automaticamente, ma devono anche essere pubblicati.

Vedi [Attivazione o disattivazione dei predefiniti per visualizzatori](#activating-or-deactivating-viewer-presets).

Vedi anche [Anteprima delle risorse](previewing-assets.md).

**Per pubblicare i predefiniti visualizzatore Dynamic Media**:

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]**.
1. Seleziona uno o più predefiniti visualizzatore da pubblicare.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Pubblica]** icona.

## Ordinamento dei predefiniti per visualizzatori Dynamic Media {#sorting-viewer-presets}

**Per ordinare i predefiniti visualizzatore Dynamic Media**:

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi, nella barra a sinistra, seleziona **Strumenti** (icona a forma di martello) > **[!UICONTROL Risorse > Predefiniti visualizzatore]**.
1. Per ordinare in base all’intestazione della colonna, fai clic su **[!UICONTROL Titolo del predefinito]**, **[!UICONTROL Tipo]**, **[!UICONTROL Pubblicato]** o **[!UICONTROL Stato]**. Ad esempio, fai clic su **[!UICONTROL Tipo]** per ordinare i tipi di predefiniti visualizzatore in ordine alfabetico o inverso.

## Modifica dei predefiniti per visualizzatori Dynamic Media {#editing-viewer-presets}

Tieni presente che la modifica di qualsiasi *predefiniti per visualizzatori pronti all’uso* non è uno scenario supportato. Se modifichi un predefinito per visualizzatori preconfigurato, viene richiesto di salvarlo con un nuovo nome.

**Per modificare i predefiniti visualizzatore Dynamic Media**:

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]**.
1. Seleziona un predefinito selezionando la casella a sinistra del titolo del predefinito visualizzatore.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Modifica]**.
1. Sulla **[!UICONTROL Modifica predefinito visualizzatore]** apporta le modifiche desiderate al predefinito visualizzatore.
1. Effettua una delle operazioni seguenti:

   * Tocca **[!UICONTROL Salva]** per salvare le modifiche e tornare al **[!UICONTROL Predefinito visualizzatore]** pagina.
   * Tocca **[!UICONTROL Annulla]** per evitare eventuali modifiche apportate e tornare alla sezione **[!UICONTROL Predefinito visualizzatore]** pagina.

## Eliminazione dei predefiniti visualizzatore Dynamic Media personalizzati {#deleting-custom-viewer-presets}

È possibile eliminare i predefiniti per visualizzatori creati e aggiunti a Dynamic Media.

**Per eliminare i predefiniti visualizzatore Dynamic Media personalizzati**:

1. Nell’angolo in alto a sinistra di AEM, tocca il logo AEM, quindi nella barra a sinistra tocca **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]**.
1. Sulla **[!UICONTROL Predefiniti visualizzatore]** pagina, controlla un **[!UICONTROL Titolo predefinito]**, quindi tocca **[!UICONTROL Cestino]** icona.
1. Tocca **[!UICONTROL Elimina]**.

## Applicazione di un predefinito visualizzatore Dynamic Media a una risorsa {#applying-a-viewer-preset-to-an-asset}

Se hai già pubblicato sia la risorsa che il visualizzatore selezionato, dopo aver selezionato un predefinito visualizzatore vengono visualizzati i pulsanti **[!UICONTROL URL]** e **[!UICONTROL Incorpora]**.

**Per applicare un predefinito visualizzatore Dynamic Media a una risorsa**:

1. Apri la risorsa e, vicino all’angolo in alto a sinistra della pagina, tocca il menu a discesa, quindi seleziona **[!UICONTROL Visualizzatori]**.

   >[!NOTE]
   >
   >Se hai già pubblicato sia la risorsa che il visualizzatore selezionato, dopo aver selezionato un predefinito visualizzatore vengono visualizzati i pulsanti **[!UICONTROL URL]** e **[!UICONTROL Incorpora]**.

1. Seleziona un predefinito visualizzatore dal riquadro a sinistra per applicarlo alla risorsa.

   È possibile [copia l’URL da condividere](linking-urls-to-yourwebapplication.md) con altri utenti.

## Distribuzione delle risorse con i predefiniti per visualizzatori Dynamic Media {#delivering-assets-with-viewer-presets}

Per ottenere gli URL per i predefiniti per visualizzatori, vedi [Collegamento di URL all’applicazione Web](linking-urls-to-yourwebapplication.md). Vedi anche [Incorporazione del visualizzatore video in una pagina web](embed-code.md).

Se utilizzi AEM come WCM, puoi aggiungere risorse utilizzando i predefiniti visualizzatore direttamente sulla pagina. Vedi [Aggiunta di risorse Dynamic Media alle pagine](adding-dynamic-media-assets-to-pages.md).
