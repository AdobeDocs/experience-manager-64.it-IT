---
title: Creazione di pop-up personalizzati tramite Quickview
seo-title: Using Quickviews to create custom pop-ups
description: La visualizzazione rapida predefinita viene utilizzata nelle esperienze e-commerce in cui viene visualizzato un pop-up con le informazioni sul prodotto per promuovere un acquisto. Puoi attivare il contenuto personalizzato da visualizzare nei pop-up.
seo-description: The default Quickview is used in ecommerce experiences whereby a pop-up is displayed with product information to drive a purchase. You can trigger custom content to display in the pop-ups.
uuid: b906cfff-ac44-4989-b6da-8a9bbf02af03
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4bcab3f4-500f-432e-b16b-cdc26b9bab4d
exl-id: 56b070e4-b445-4488-acff-685b7ce5785f
feature: Configuration
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 1%

---

# Creazione di pop-up personalizzati tramite Quickview {#using-quickviews-to-create-custom-pop-ups}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La visualizzazione rapida predefinita viene utilizzata nelle esperienze e-commerce in cui viene visualizzato un pop-up con le informazioni sul prodotto per promuovere un acquisto. Tuttavia, puoi attivare il contenuto personalizzato da visualizzare nei pop-up. A seconda del visualizzatore che utilizzi, questa funzionalità consente agli utenti di fare clic su un punto attivo, su un&#39;immagine in miniatura o su una mappa immagine per visualizzare informazioni o contenuti correlati.

Le visualizzazioni rapide sono supportate dai seguenti visualizzatori in Dynamic Media:

* Immagini interattive (punti attivi cliccabili)
* Video interattivo (immagini thumbnail cliccabili durante la riproduzione del video)
* Banner a carosello (hotspot cliccabili o mappe immagine)

Sebbene le funzionalità di ciascun visualizzatore siano diverse, il processo di creazione di una visualizzazione rapida è lo stesso in tutti e tre i visualizzatori supportati.

**Per creare pop-up personalizzati utilizzando le Quickview:**

1. Crea una visualizzazione rapida per una risorsa caricata.

   In genere, quando modifichi una risorsa da utilizzare con il visualizzatore in uso, crei una visualizzazione rapida.

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Visualizzatore in uso</strong></td> 
    <td><strong>Completa questi passaggi per creare la visualizzazione rapida</strong></td> 
    </tr> 
    <tr> 
    <td>Immagini interattive</td> 
    <td><a href="/help/assets/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank">Aggiunta di punti attivi a un banner immagine</a>.</td> 
    </tr> 
    <tr> 
    <td>Video interattivi</td> 
    <td><a href="/help/assets/interactive-videos.md#adding-interactivity-to-your-video" target="_blank">Aggiunta di interattività al video</a>.</td> 
    </tr> 
    <tr> 
    <td>Banner a carosello</td> 
    <td><a href="/help/assets/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank">Aggiunta di punti attivi o mappe immagine a un banner</a>.<br /> </td> 
    </tr> 
    </tbody> 
   </table>

1. Ottieni il codice di incorporamento del visualizzatore per integrare il visualizzatore all’interno del tuo sito web.

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Visualizzatore in uso</strong><br /> </td> 
    <td><strong>Completa questi passaggi per integrare il visualizzatore con il tuo sito web</strong></td> 
    </tr> 
    <tr> 
    <td>Immagine interattiva</td> 
    <td><a href="/help/assets/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Integrazione di un’immagine interattiva con il sito web</a>.<br /> </td> 
    </tr> 
    <tr> 
    <td>Video interattivo<br /> </td> 
    <td><a href="/help/assets/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">Integrazione di un video interattivo con il sito web</a>.<br /> </td> 
    </tr> 
    <tr> 
    <td>Banner a carosello</td> 
    <td><a href="/help/assets/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">Aggiunta di un banner carosello alla pagina del sito web</a>.<br /> </td> 
    </tr> 
    </tbody> 
   </table>

1. Il visualizzatore che utilizzi ora deve sapere come utilizzare la visualizzazione rapida.

   A questo scopo, il visualizzatore utilizza un gestore denominato `QuickViewActive`.

   **Esempio**
Supponiamo che tu stia utilizzando il seguente codice di incorporamento sulla tua pagina web per un&#39;immagine interattiva:

   ![chlimage_1-291](assets/chlimage_1-291.png)

   Il gestore viene caricato nel visualizzatore utilizzando `setHandlers`:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **Utilizzando l&#39;esempio di codice di incorporamento di esempio riportato sopra, abbiamo il seguente codice:**

   ```xml
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   Ulteriori informazioni `setHandlers()` metodo nel modo seguente:

   * Visualizzatore di immagini interattive: [setHandlers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html)
   * Visualizzatore video interattivo: [setHandlers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html)

1. È ora necessario configurare le `quickViewActivate` handler.

   Il gestore quickViewActivate controlla le Quickview nel visualizzatore. Il gestore contiene l&#39;elenco di variabili e le chiamate di funzioni da utilizzare con Quickview. Il codice di incorporamento fornisce la mappatura per la variabile SKU impostata in Quickview e per una chiamata della funzione loadQuickView di esempio.

   **Mappatura variabile**
Mappa le variabili da utilizzare nella pagina web al valore SKU e alle variabili generiche contenute in Quickview:

   `var *variable1*= inData.*quickviewVariable*`

   Il codice di incorporamento fornito ha una mappatura di esempio per la variabile SKU:

   `var sku=inData.sku`

   Mappa anche altre variabili dalla visualizzazione rapida, come illustrato di seguito:

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i> 
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **Chiamata funzione**
Il gestore richiede anche una chiamata di funzione per il funzionamento di Quickview. Si presume che la funzione sia accessibile dalla pagina host. Il codice di incorporamento fornisce un esempio di chiamata della funzione :

   `loadQuickView(sku)`

   La chiamata della funzione di esempio presuppone che la funzione `loadQuickView()` esiste ed è accessibile.

   Per ulteriori informazioni sul metodo quickViewActivate, consulta:

   * Visualizzatore immagini interattivo - [Callback degli eventi](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html)
   * Visualizzatore video interattivo - [Callback degli eventi](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html)
   * Supporto dei dati interattivi nel visualizzatore video interattivo - [Supporto dei dati interattivi](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html)

1. Effettua le seguenti operazioni:

   * Rimuovi il commento alla sezione setHandlers del codice di incorporamento.
   * Mappa eventuali variabili aggiuntive contenute nella visualizzazione rapida.

      * Aggiorna `loadQuickView(sku,*var1*,*var2*)` chiama se aggiungi ulteriori variabili.
   * Crea una semplice funzione loadQuickView () sulla pagina, all&#39;esterno del visualizzatore.

      Ad esempio, il seguente scrive il valore di sku nella console del browser:

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Carica una pagina HTML di test su un server web e apri.

      Con le variabili mappate da Quickview e la chiamata della funzione in atto, la console del browser scrive il valore della variabile nella console del browser utilizzando la funzione di esempio fornita.



1. È ora possibile utilizzare una funzione per richiamare un semplice pop-up in Quickview. Nell&#39;esempio seguente viene utilizzato un `DIV` per una finestra a comparsa.
1. Personalizzare lo stile della finestra a comparsa `DIV` nel modo seguente. Aggiungi lo stile aggiuntivo desiderato.

   ```xml
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Posiziona la finestra a comparsa `DIV` nel corpo della pagina HTML.

   Uno degli elementi viene impostato con un ID aggiornato con il valore sku quando l’utente richiama un Quickview. L’esempio include anche un semplice pulsante per nascondere nuovamente la finestra a comparsa quando diventa visibile.

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Aggiungi una funzione per aggiornare il valore SKU nel pop-up; rendere il pop-up visibile sostituendo la funzione semplice creata al punto 5. con le seguenti caratteristiche:

   ```xml
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. Carica una pagina HTML di test sul server web e apri. Il visualizzatore visualizza la finestra a comparsa `DIV` quando un utente richiama un Quickview.
1. **Come visualizzare il pop-up personalizzato in modalità a schermo intero**

   Alcuni visualizzatori, come il visualizzatore video interattivo, supportano la visualizzazione in modalità a schermo intero. Tuttavia, se si utilizza il pop-up come descritto nei passaggi precedenti, questo viene visualizzato dietro il visualizzatore in modalità a schermo intero.

   Per visualizzare la visualizzazione a comparsa sia in modalità standard che a schermo intero, allegare la finestra a comparsa al contenitore del visualizzatore. A questo scopo, puoi utilizzare un secondo metodo di gestione, `initComplete`.

   La `initComplete` viene richiamato dopo l’inizializzazione del visualizzatore.

   ```xml
   "initComplete":function() { code block }
   ```

   Ulteriori informazioni `init()` metodo nel modo seguente:

   * Visualizzatore immagini interattivo - [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html)
   * Visualizzatore video interattivo - [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html)

1. Per allegare al visualizzatore il pop-up (descritto nei passaggi precedenti), utilizza il seguente codice:

   ```xml
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   Nel codice riportato sopra, abbiamo fatto quanto segue:

   * Identificato il nostro pop-up personalizzato.
   * È stato rimosso dal DOM.
   * Identificato il contenitore del visualizzatore.
   * È stato allegato il pop-up al contenitore del visualizzatore.

1. L’intero codice setHandlers deve ora essere simile al seguente (è stato utilizzato il visualizzatore video interattivo):

   ```xml
   s7interactivevideoviewer.setHandlers({
       "quickViewActivate": function(inData) {
           var sku=inData.sku;
           loadQuickView(sku);
   
       },
       "initComplete":function() {
           var popup = document.getElementById('quickview_div'); // get custom quick view container
           popup.parentNode.removeChild(popup); // remove it from current DOM
           var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
           var inner_container = document.getElementById(sdkContainerId);
           inner_container.appendChild(popup);
       }
   });
   ```

1. Dopo il caricamento dei gestori, inizializza il visualizzatore:

   `*viewerInstance.*init()`

   **Esempio**
In questo esempio viene utilizzato il visualizzatore di immagini interattivo.

   `s7interactiveimageviewer.init()`

   Dopo aver incorporato il visualizzatore nella pagina host, assicurati che l’istanza del visualizzatore sia creata e che i gestori siano caricati prima che il visualizzatore venga richiamato utilizzando `init()`.
