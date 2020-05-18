---
title: Aggiunta di risorse Dynamic Media alle pagine
seo-title: Aggiunta di risorse Dynamic Media alle pagine
description: Come aggiungere componenti per contenuti multimediali dinamici a una pagina in AEM
seo-description: Come aggiungere componenti per contenuti multimediali dinamici a una pagina in AEM
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
translation-type: tm+mt
source-git-commit: 9b19484596948e9e166f5310622b7e6eacd78f93
workflow-type: tm+mt
source-wordcount: '2843'
ht-degree: 33%

---


# Aggiunta di risorse Dynamic Media alle pagine {#adding-dynamic-media-assets-to-pages}

To add the dynamic media functionality to assets you use on your websites, you can add the **Dynamic Media** or **Interactive Media** component directly on the page. A tale scopo, è possibile accedere alla modalità Layout e abilitare i componenti per contenuti multimediali dinamici. Quindi, potrai aggiungere questi componenti alla pagina e fornire così risorse al componente. I componenti Elemento multimediale dinamico e File multimediali interattivi sono intelligenti: sanno se aggiungi un&#39;immagine o un video e le opzioni disponibili cambiano di conseguenza.

Se utilizzi AEM come WCM, puoi aggiungere risorse multimediali dinamiche direttamente alla pagina. Se ti avvali di una terza parte per WCM, puoi [collegare](linking-urls-to-yourwebapplication.md) o [incorporare](embed-code.md) le risorse. Per un sito web dinamico di terze parti, consulta la sezione [Distribuzione di immagini ottimizzate in un sito dinamico](responsive-site.md).

>[!NOTE]
>
>È necessario pubblicare le risorse prima di aggiungerle alle pagine in AEM. See [Publishing Dynamic Media Assets](publishing-dynamicmedia-assets.md).

## Adding a Dynamic Media component to a page {#adding-a-dynamic-media-component-to-a-page}

L’aggiunta di un componente Contenuti multimediali dinamici a una pagina equivale all’aggiunta di un componente a una qualsiasi pagina. I componenti per contenuti multimediali dinamici sono descritti dettagliatamente nelle sezioni seguenti.

>[!NOTE]
>
>Se in una pagina Web è presente un componente Contenuti multimediali dinamici a cui accede un utente con autorizzazioni di sola lettura, il rendering delle interruzioni di pagina e dei componenti non viene eseguito correttamente. Questo perché la pagina viene ricostruita per garantire che le proprietà dei componenti siano buone e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina che causa l’interruzione dei componenti; il relativo codice componente sulla pagina non può essere riprodotto a causa dell’accesso in sola lettura dell’utente.
>  
>Per evitare questo problema, accertati che gli utenti di AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

1. In AEM, apri la pagina in cui desideri aggiungere il Componente elementi multimediali dinamici.
1. Nel pannello a sinistra della pagina (potrebbe essere necessario attivare o disattivare la visualizzazione del pannello laterale), fate clic sull’icona **[!UICONTROL Componenti]** .
1. Nell’intestazione **[!UICONTROL Componenti]** , nell’elenco a discesa, selezionate Contenuti multimediali **** dinamici. Se non è disponibile alcun elenco di componenti per contenuti multimediali dinamici, è probabile che sia necessario attivarli. See [Enabling Dynamic Media components](#enabling-dynamic-media-components).

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. Trascinate sulla pagina un componente Contenuti multimediali dinamici da usare nella posizione desiderata.
1. Fate clic sulla casella blu intorno al componente, quindi toccate l&#39;icona **[!UICONTROL Configurazione]** (chiave inglese).
1. [Modificate i componenti](#dynamic-media-components) secondo necessità e fate clic sul segno di spunta per salvare le modifiche.

### Abilitazione di componenti per contenuti multimediali dinamici {#enabling-dynamic-media-components}

Se non è disponibile alcun componente per contenuti multimediali dinamici da aggiungere a una pagina, è probabile che sia necessario abilitare i componenti.

1. In AEM, apri la pagina in cui desideri aggiungere il Componente elementi multimediali dinamici.
1. Sul lato sinistro della barra degli strumenti accanto alla parte superiore della pagina, toccate l’icona Informazioni pagina, quindi toccate **[!UICONTROL Modifica modello]** dall’elenco a discesa.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Sul lato destro della barra degli strumenti accanto alla parte superiore della pagina, toccate **[!UICONTROL Struttura dall’elenco a discesa]**.

![Criterio](/help/assets/assets-dm/structure-mode.png)

1. Nella parte inferiore della pagina, toccate Contenitore **[!UICONTROL di]** layout per aprire la relativa barra degli strumenti, quindi toccate l&#39;icona Criterio.
1. Nella pagina Contenitore **[!UICONTROL di]** layout, sotto l&#39;intestazione **[!UICONTROL Proprietà]** , assicurarsi che la scheda Componenti **** consentiti sia selezionata.

![Componenti consentiti](/help/assets/assets-dm/allowed-components.png)

1. Scorrete fino a visualizzare gli elementi **[!UICONTROL multimediali]** dinamici.
1. Toccate l’icona > a sinistra di **[!UICONTROL Contenuti multimediali]** dinamici per espandere l’elenco, quindi selezionate i componenti Contenuti multimediali dinamici da attivare.

![Elenco dei componenti per elementi per elementi per elementi per elementi per contenuti multimediali dinamici](/help/assets/assets-dm/dm-components-select.png)

1. Nell&#39;angolo superiore destro della pagina Contenitore **[!UICONTROL di]** layout, toccate l&#39;icona Fine (segno di spunta).

1. Sul lato destro della barra degli strumenti accanto alla parte superiore della pagina, toccate Contenuto **** iniziale dall’elenco a discesa, quindi [aggiungete un componente Contenuti multimediali dinamici alla pagina](#adding-a-dynamic-media-component-to-a-page) come al solito.

## Localizzazione dei componenti per contenuti multimediali dinamici {#localizing-dynamic-media-components}

Potete localizzare i componenti per contenuti multimediali dinamici in uno dei due modi seguenti:

* In una pagina web di Sites, apri **[!UICONTROL Proprietà]** e seleziona la scheda **[!UICONTROL Avanzate]**. Scegli la lingua desiderata per la localizzazione.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* Dal selettore del sito, selezionate la pagina o il gruppo di pagine desiderato. Toccate **[!UICONTROL Proprietà]** e selezionate la scheda **[!UICONTROL Avanzate]** . Scegli la lingua desiderata per la localizzazione.

   >[!NOTE]
   >
   >Al momento non tutte le lingue disponibili nel menu **[!UICONTROL Lingua]** dispongono di token.

## Dynamic Media components {#dynamic-media-components}

Contenuti multimediali dinamici e contenuti multimediali interattivi sono disponibili nella scheda Contenuti multimediali  dinamici di [!UICONTROL Componenti]. Potete usare il componente Interactive Media] per qualsiasi risorsa interattiva, ad esempio video interattivo, immagini interattive o set di caroselli. Per tutti gli altri componenti dinamici, si consiglia di utilizzare il componente elementi multimediali dinamici.

>[!NOTE]
>
>Questi componenti non sono disponibili per impostazione predefinita e devono essere resi disponibili tramite l’editor modelli prima di utilizzarli. [Una volta resi disponibili](/help/sites-authoring/templates.md#editing-templates-template-authors)nell’editor modelli, potete aggiungere i componenti alla pagina come qualsiasi altro componente AEM.

![chlimage_1-539](assets/chlimage_1-539.png)

### Componente elementi multimediali dinamici {#dynamic-media-component}

Il componente Contenuti multimediali dinamici è un elemento avanzato, a seconda se aggiungete un’immagine o un video e se disponete di diverse opzioni. Il componente supporta i predefiniti per immagini e i visualizzatori basati su immagini, come set di immagini, set di rotazione, set di file multimediali diversi e video. Inoltre, il visualizzatore è reattivo. In altre parole, le dimensioni dello schermo cambiano automaticamente in base alle dimensioni dello schermo. Tutti i visualizzatori sono visualizzatori HTML5.

>[!NOTE]
>
>Se è presente un componente per contenuti multimediali dinamici, un componente per contenuti multimediali interattivi o entrambi in una pagina Web a cui accede un utente con autorizzazioni di sola lettura, le interruzioni di pagina e il rendering dei componenti non vengono eseguiti correttamente. Questo perché la pagina viene ricostruita per garantire che le proprietà dei componenti siano buone e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina che causa l’interruzione dei componenti; il relativo codice componente sulla pagina non può essere riprodotto a causa dell’accesso in sola lettura dell’utente.
>  
>Per evitare questo problema, accertati che gli utenti di AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

>[!NOTE]
>
>Quando aggiungi il Componente elementi multimediali dinamici e le **[!UICONTROL Impostazioni elemento multimediale dinamico]** sono vuote o non è possibile aggiungere correttamente una risorsa, controlla quanto segue:
>
>* È stato [abilitato Elemento multimediale dinamico](config-dynamic.md). Dynamic Media è disattivato per impostazione predefinita.
>* L&#39;immagine è in formato TIFF piramidale. Le immagini importate prima dell&#39;attivazione dell’elemento multimediale dinamico non hanno un file TIFF piramidale.
>



#### Quando si lavora con le immagini {#when-working-with-images}

Il componente elementi multimediali dinamici consente di aggiungere immagini dinamiche, compresi set di immagini, set di rotazione e set di file multimediali diversi. È possibile ingrandire, ridurre e, se applicabile, ruotare un&#39;immagine all&#39;interno di un set 360 gradi, o selezionare un&#39;immagine da un altro tipo di set.

È possibile anche configurare il predefinito visualizzatore, il predefinito immagine o il formato immagine direttamente nel componente. Per rendere un&#39;immagine reattiva è possibile impostare i punti di interruzione o applicare un predefinito immagine reattiva.

You must edit the following Dynamic Media Settings by clicking the **[!UICONTROL Edit]** icon in the component and then **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Per impostazione predefinita, il componente immagine Dynamic Media è adattivo. If you want to make it a fixed size, set it in the component in the **[!UICONTROL Advanced]** tab with the **[!UICONTROL Width]** and **[!UICONTROL Height]** settings.

* **[!UICONTROL Predefinito]**visualizzatore Selezionate un predefinito per visualizzatori esistente dal menu a discesa. Se il predefinito per visualizzatori che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per visualizzatori. Non è possibile selezionare un predefinito per visualizzatori se si utilizza un predefinito per immagini, e viceversa.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi. Anche i predefiniti per visualizzatori sono avanzati: vengono visualizzati solo i predefiniti per visualizzatori pertinenti.

* **[!UICONTROL I modificatori]** Visualizzatore visualizzatori hanno la forma di coppia nome=valore con un carattere di delimitazione &amp; e consentono di modificare i visualizzatori come indicato nella guida di riferimento dei visualizzatori. Un esempio di modificatore di visualizzatore è posterimage=img.jpg&amp;caption=text.vtt,1 che imposta un’immagine diversa per la miniatura del video e associa un file di sottotitoli/sottotitoli codificati al video.

* **[!UICONTROL Predefinito]**immagine Selezionate un predefinito per immagini esistente dal menu a discesa. Se il predefinito per immagini che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per immagini. Non è possibile selezionare un predefinito per visualizzatori se si utilizza un predefinito per immagini, e viceversa.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL Modificatori di immagini]**Potete applicare effetti immagine fornendo ulteriori comandi immagine. Questi sono descritti nei predefiniti per immagini e nel riferimento al comando Image Server.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL Punti di interruzione]**Se utilizzi questa risorsa in un sito reattivo, devi aggiungere i punti di interruzione immagine. I punti di interruzione immagine devono essere separati da virgole (,). Questa opzione funziona quando non è stata definita alcuna altezza o larghezza in un predefinito immagine.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.
You can edit the following Advanced Settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Titolo]** Consente di cambiare il titolo dell’immagine.

* **[!UICONTROL Testo]**Alt Consente di aggiungere un titolo all’immagine per gli utenti che hanno disattivato la grafica.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL URL, Apri in]**Potete impostare una risorsa per aprire un collegamento. Imposta l’URL e in Apri in indica se desideri aprirlo nella stessa finestra o in una nuova finestra.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL Larghezza]** e **[!UICONTROL altezza]** Immettere il valore in pixel se si desidera che l&#39;immagine sia di dimensione fissa. Lasciando vuoti questi valori, la risorsa viene resa adattiva.

#### Quando esegui operazioni con i Video {#when-working-with-video}

Usate il componente Contenuti multimediali dinamici per aggiungere video dinamici alle pagine Web. Quando modifichi il componente puoi scegliere di usare un predefinito visualizzatore video predefinita per la riproduzione del video nella pagina.

![chlimage_1-540](assets/chlimage_1-540.png)

You must edit the following Dynamic Media Settings by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Per impostazione predefinita, il componente video elementi multimediali dinamici è adattivo. If you want to make it a fixed size, set it in the component with the **[!UICONTROL Width]** and **[!UICONTROL Height]** in the [!UICONTROL Advanced] tab.

* **[!UICONTROL Predefinito]** visualizzatoreSelezionate un predefinito per visualizzatori video esistente dal menu a discesa. Se il predefinito per visualizzatori che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per visualizzatori. 

* **[!UICONTROL I modificatori]** Visualizzatore visualizzatori hanno la forma di coppia nome=valore con un carattere di delimitazione &amp; e consentono di modificare i visualizzatori come indicato nella Guida di riferimento dei visualizzatori Adobe. Un esempio di modificatore di visualizzatore è posterimage=img.jpg&amp;caption=text.vtt,1

   Con i modificatori del visualizzatore, ad esempio, potete effettuare le seguenti operazioni:

   * Associare un file di sottotitoli a un video [https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_caption.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_caption.html)
   * Associare un file di navigazione a un video [https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_navigation.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_video_viewer_url_navigation.html)

You can edit the following [!UICONTROL Advanced Settings] by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Titolo]** Consente di cambiare il titolo del video.

* **[!UICONTROL Larghezza]** e **[!UICONTROL altezza]** Immettere il valore in pixel se si desidera che il video sia di dimensioni fisse. Se questi valori vengono lasciati vuoti, la risorsa sarà adattiva.

#### Quando si lavora con Smart Crop {#when-working-with-smart-crop}

Usate il componente Contenuti multimediali dinamici per aggiungere le risorse di immagine Ritaglio avanzato alle pagine Web. Quando modifichi il componente puoi scegliere di usare un predefinito visualizzatore video predefinita per la riproduzione del video nella pagina.

Consultate anche Profili [immagine](image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

You can edit the following [!UICONTROL Dynamic Media Settings] by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Per impostazione predefinita, il componente immagine Dynamic Media è adattivo. Se vuoi impostarne una dimensione fissa, lo puoi fare nella scheda [!UICONTROL Avanzate] del componente, alle voci **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]**.

* **[!UICONTROL Modificatori di immagini]**Potete applicare effetti immagine fornendo ulteriori comandi immagine. Questi sono descritti nei predefiniti per immagini e nel riferimento al comando Image Server.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

You can edit the following **[!UICONTROL Advanced]** settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Titolo]** Consente di cambiare il titolo dell’immagine Ritaglio avanzato.

* **[!UICONTROL Testo]**Alt Consente di aggiungere un titolo all’immagine di ritaglio avanzato per gli utenti che hanno disattivato la grafica.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL URL, Apri in]**Potete impostare una risorsa per aprire un collegamento. Imposta l’URL e in Apri in indica se desideri aprirlo nella stessa finestra o in una nuova finestra.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL Height** and **[!UICONTROL Width]** Immettere il valore in pixel se si desidera che l&#39;immagine di ritaglio avanzato sia a dimensione fissa. Se questi valori vengono lasciati vuoti, la risorsa sarà adattiva.

### Interactive Media component {#interactive-media-component}

Il Componente File multimediali interattivi è adatto per le risorse che dispongono di interattività, come punti attivi o mappe immagine. Se disponi di un&#39;immagine, un video interattivo o un banner carosello, utilizza il componente File multimediali interattivi.

Il componente Contenuti multimediali interattivi è elegante e offre diverse opzioni a seconda che sia stata aggiunta un’immagine o un video. Inoltre, il visualizzatore è reattivo: le dimensioni dello schermo cambiano automaticamente in base alle dimensioni reali dello stesso. Tutti i visualizzatori sono visualizzatori HTML5.

>[!NOTE]
>
>Se è presente un componente per contenuti multimediali dinamici, un componente per contenuti multimediali interattivi o entrambi in una pagina Web a cui accede un utente con autorizzazioni di sola lettura, le interruzioni di pagina e il rendering dei componenti non vengono eseguiti correttamente. Questo perché la pagina viene ricostruita per garantire che le proprietà dei componenti siano buone e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina che causa l’interruzione dei componenti; il relativo codice componente sulla pagina non può essere riprodotto a causa dell’accesso in sola lettura dell’utente.
> 
>Per evitare questo problema, accertati che gli utenti di AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

![chlimage_1-541](assets/chlimage_1-541.png)

È possibile modificare le seguenti impostazioni **[!UICONTROL Generali]**, facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Predefinito]** visualizzatore Selezionate un predefinito per visualizzatori esistente dal menu a discesa. Se il predefinito per visualizzatori che cerchi non è visibile, potrebbe essere necessario renderlo visibile. I predefiniti per visualizzatori devono essere pubblicati prima di poter essere utilizzati. Consulta Gestione dei predefiniti per visualizzatori. 

* **[!UICONTROL Titolo]** Consente di cambiare il titolo del video.

* **[!UICONTROL Larghezza]** e **[!UICONTROL altezza]** Immettere il valore in pixel se si desidera che il video sia di dimensioni fisse. Se questi valori vengono lasciati vuoti, la risorsa sarà adattiva.

È possibile modificare le seguenti impostazioni **[!UICONTROL Aggiungi al carrello]**, facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Mostra risorsa]** prodotto Per impostazione predefinita, questo valore è selezionato. La risorsa di prodotto mostra un&#39;immagine del prodotto in base a quanto definito nel modulo Commerce. Rimuovi il segno di spunta per non visualizzare la risorsa di prodotto.

* **[!UICONTROL Mostra prezzo]** prodotto Per impostazione predefinita, questo valore è selezionato. Prezzo del prodotto mostra il prezzo dell&#39;elemento in base a quanto definito nel modulo Commerce. Rimuovi il segno di spunta per non visualizzare il prezzo del prodotto.

* **[!UICONTROL Mostra modulo]** prodotto Per impostazione predefinita, questo valore non è selezionato. Il Modulo del prodotto include tutte le varianti del prodotto, come la dimensione e il colore. Rimuovi il segno di spunta per non visualizzare le varianti prodotto.

### Componente per contenuti multimediali panoramici {#panoramic-media-component}

Il componente Contenuti multimediali panoramici è destinato alle risorse che sono immagini panoramiche sferiche. Tali immagini forniscono un&#39;esperienza di visualizzazione a 360° di una stanza, una proprietà, una posizione o un paesaggio. Affinché un’immagine possa essere definita come panorama sferico, deve avere una O entrambe le caratteristiche seguenti:

* Proporzioni di 2:1.
* Etichettate con le parole chiave &quot;equirettangolare&quot; o (&quot;sferico&quot; + &quot;panorama&quot;) o (&quot;sferico&quot; + &quot;panoramico&quot;). Consultate [Utilizzo dei tag](/help/sites-authoring/tags.md).

Sia le proporzioni che i criteri delle parole chiave si applicano alle risorse panoramiche per la pagina dei dettagli delle risorse che per il componente WCM &quot;File multimediali panoramici&quot;.

![panoramica-media-predefinito per visualizzatori](assets/panoramic-media-viewer-preset.png)

Per modificare la seguente impostazione, tocca **[!UICONTROL Configura]** nel componente.

* **[!UICONTROL Predefinito]** visualizzatore Selezionate un visualizzatore esistente dal menu a discesa Predefinito visualizzatore.

Se il predefinito per visualizzatori ricercato non è visibile, accertatevi che sia pubblicato. Per poter usare i predefiniti per visualizzatori, dovete pubblicarli. Consulta [Gestione dei predefiniti per visualizzatori](managing-viewer-presets.md). 

### Utilizzo di HTTP/2 per la distribuzione di risorse multimediali dinamiche {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 è il nuovo protocollo Web aggiornato che migliora il modo in cui i browser e i server comunicano. Fornisce un trasferimento più rapido delle informazioni e riduce la quantità di potenza di elaborazione necessaria. La distribuzione delle risorse Dynamic Media ora può avvenire tramite HTTP/2, migliorando la risposta e i tempi di caricamento.

Per informazioni dettagliate sull’utilizzo di HTTP/2 con l’account per contenuti multimediali dinamici, consultate Consegna di contenuti [](http2.md) HTTP2.

>[!MORELIKETHIS]
>
>* [Gestione del colore con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [Utilizzo della miniatura video personalizzata con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Il visualizzatore delle risorse con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [Utilizzo di video interattivi con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [Utilizzo del lettore video in AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [Utilizzo della nitidezza delle immagini con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

