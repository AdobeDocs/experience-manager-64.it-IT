---
title: Aggiunta di risorse Dynamic Media alle pagine
seo-title: Aggiunta di risorse Dynamic Media alle pagine
description: Come aggiungere componenti Dynamic Media a una pagina in AEM
seo-description: Come aggiungere componenti Dynamic Media a una pagina in AEM
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
translation-type: tm+mt
source-git-commit: 44fb6e0ae344111385be844dfad1c6618c9209f0
workflow-type: tm+mt
source-wordcount: '2825'
ht-degree: 34%

---


# Aggiunta di risorse Dynamic Media alle pagine {#adding-dynamic-media-assets-to-pages}

Per aggiungere la funzionalità per contenuti multimediali dinamici alle risorse utilizzate nei siti Web, potete aggiungere il componente **Dynamic Media** o **Interactive Media** direttamente sulla pagina. A tale scopo, è possibile accedere alla modalità Layout e abilitare i componenti per contenuti multimediali dinamici. Quindi, potrai aggiungere questi componenti alla pagina e fornire così risorse al componente. I componenti Elemento multimediale dinamico e File multimediali interattivi sono intelligenti: sanno se aggiungi un&#39;immagine o un video e le opzioni disponibili cambiano di conseguenza.

Se utilizzate AEM come WCM, potete aggiungere risorse multimediali dinamiche direttamente alla pagina. Se ti avvali di una terza parte per WCM, puoi [collegare](linking-urls-to-yourwebapplication.md) o [incorporare](embed-code.md) le risorse. Per un sito web dinamico di terze parti, consulta la sezione [Distribuzione di immagini ottimizzate in un sito dinamico](responsive-site.md).

>[!NOTE]
>
>È necessario pubblicare le risorse prima di aggiungerle alle pagine in AEM. Consultate [Pubblicazione di Dynamic Media Assets](publishing-dynamicmedia-assets.md).

## Aggiunta di un componente Dynamic Media a una pagina {#adding-a-dynamic-media-component-to-a-page}

L’aggiunta di un componente Dynamic Media a una pagina equivale all’aggiunta di un componente a qualsiasi pagina. I componenti Dynamic Media sono descritti dettagliatamente nelle sezioni seguenti.

>[!NOTE]
>
>Se in una pagina Web è presente un componente Dynamic Media a cui un utente ha accesso con autorizzazioni di sola lettura, il rendering delle interruzioni di pagina e dei componenti non viene eseguito correttamente. Questo perché la pagina viene ricostruita per garantire che le proprietà dei componenti siano buone e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina che causa l’interruzione dei componenti; il relativo codice componente sulla pagina non può essere riprodotto a causa dell’accesso in sola lettura dell’utente.
>  
>Per evitare questo problema, assicuratevi che  utenti AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

1. In AEM, apri la pagina in cui desideri aggiungere il Componente elementi multimediali dinamici.
1. Nel pannello a sinistra della pagina (potrebbe essere necessario attivare o disattivare la visualizzazione del pannello laterale), fate clic sull&#39;icona **[!UICONTROL Components]**.
1. Nell&#39;intestazione **[!UICONTROL Componenti]**, selezionare **[!UICONTROL Dynamic Media]** dall&#39;elenco a discesa. Se non è disponibile alcun elenco di componenti Dynamic Media, è probabile che sia necessario abilitare i componenti Dynamic Media da utilizzare. Vedere [Abilitazione di componenti Dynamic Media](#enabling-dynamic-media-components).

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. Trascinate sulla pagina un componente Dynamic Media da usare nella posizione desiderata.
1. Passate il puntatore del mouse direttamente sul componente. Quando il componente è circondato da una casella blu, toccate una volta per visualizzare la barra degli strumenti del componente. Toccate l&#39;icona **[!UICONTROL Configuration]** (chiave inglese).
1. [Modificate i ](#dynamic-media-components) componenti secondo necessità e fate clic sul segno di spunta per salvare le modifiche.

### Abilitazione dei componenti Dynamic Media {#enabling-dynamic-media-components}

Se non è disponibile alcun componente Dynamic Media da aggiungere a una pagina, è probabile che sia necessario prima abilitare i componenti che si desidera utilizzare.

1. In AEM, apri la pagina in cui desideri aggiungere il Componente elementi multimediali dinamici.
1. Sul lato sinistro della barra degli strumenti accanto alla parte superiore della pagina, toccare l&#39;icona Informazioni pagina, quindi toccare **[!UICONTROL Modifica modello]** dall&#39;elenco a discesa.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Sul lato destro della barra degli strumenti accanto alla parte superiore della pagina, toccate **[!UICONTROL Struttura]** dall&#39;elenco a discesa.

   ![Criterio](/help/assets/assets-dm/structure-mode.png)

1. Nella parte inferiore della pagina, toccare **[!UICONTROL Contenitore di layout]** per aprire la barra degli strumenti, quindi toccare l&#39;icona Criterio.
1. Nella pagina **[!UICONTROL Contenitore di layout]**, sotto l&#39;intestazione **[!UICONTROL Proprietà]**, assicurarsi che la scheda **[!UICONTROL Componenti consentiti]** sia selezionata.

   ![Componenti consentiti](/help/assets/assets-dm/allowed-components.png)

1. Scorrete fino a visualizzare **[!UICONTROL Dynamic Media]**.
1. Toccate l&#39;icona > a sinistra di **[!UICONTROL Dynamic Media]** per espandere l&#39;elenco, quindi selezionate i componenti Dynamic Media da abilitare.

   ![Elenco dei componenti Dynamic Media](/help/assets/assets-dm/dm-components-select.png)

1. Nell&#39;angolo superiore destro della pagina **[!UICONTROL Contenitore di layout]**, toccate l&#39;icona Fine (segno di spunta).

1. Sul lato destro della barra degli strumenti accanto alla parte superiore della pagina, dall&#39;elenco a discesa, toccare **[!UICONTROL Contenuto iniziale]**, quindi [aggiungere un componente Dynamic Media a una pagina](#adding-a-dynamic-media-component-to-a-page) come al solito.

## Localizzazione dei componenti Dynamic Media {#localizing-dynamic-media-components}

Potete localizzare i componenti Dynamic Media in uno dei due modi seguenti:

* In una pagina web di Sites, apri **[!UICONTROL Proprietà]** e seleziona la scheda **[!UICONTROL Avanzate]**. Scegli la lingua desiderata per la localizzazione.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* Dal selettore del sito, selezionate la pagina o il gruppo di pagine desiderato. Toccare **[!UICONTROL Properties]** e selezionare la scheda **[!UICONTROL Advanced]**. Scegli la lingua desiderata per la localizzazione.

   >[!NOTE]
   >
   >Non tutte le lingue disponibili nel menu **[!UICONTROL Lingua]** dispongono attualmente di token assegnati.

## Componenti Dynamic Media {#dynamic-media-components}

Dynamic Media e Interactive Media sono disponibili nella scheda [!UICONTROL Dynamic Media] in [!UICONTROL Components]. Puoi utilizzare un componente [!UICONTROL File multimediali interattivi] per tutte le risorse interattive, come per esempio video, immagini interattive o inserzioni carosello. Per tutti gli altri componenti dinamici, si consiglia di utilizzare il componente elementi multimediali dinamici.

>[!NOTE]
>
>Questi componenti non sono disponibili per impostazione predefinita e devono essere resi disponibili tramite l’editor modelli prima di utilizzarli. [Una volta resi ](/help/sites-authoring/templates.md#editing-templates-template-authors) disponibili nell’editor modelli, potete aggiungere i componenti alla pagina come qualsiasi altro componente AEM.

![chlimage_1-539](assets/chlimage_1-539.png)

### Componente elementi multimediali dinamici {#dynamic-media-component}

Il componente Dynamic Media è avanzato: a seconda se aggiungete un’immagine o un video, sono disponibili diverse opzioni. Il componente supporta i predefiniti per immagini e i visualizzatori basati su immagini, come set di immagini, set di rotazione, set di file multimediali diversi e video. Inoltre, il visualizzatore è reattivo. In altre parole, le dimensioni dello schermo cambiano automaticamente in base alle dimensioni dello schermo. Tutti i visualizzatori sono visualizzatori HTML5.

>[!NOTE]
>
>Se è presente un componente Dynamic Media, un componente Media interattivo o entrambi in una pagina Web a cui si accede da un utente con autorizzazioni di sola lettura, le interruzioni di pagina e il rendering dei componenti non vengono eseguiti correttamente. Questo perché la pagina viene ricostruita per garantire che le proprietà dei componenti siano buone e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina che causa l’interruzione dei componenti; il relativo codice componente sulla pagina non può essere riprodotto a causa dell’accesso in sola lettura dell’utente.
>  
>Per evitare questo problema, assicuratevi che  utenti AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

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

È necessario modificare le seguenti impostazioni Dynamic Media facendo clic sull&#39;icona **[!UICONTROL Edit]** nel componente, quindi su **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Per impostazione predefinita, il componente immagine Dynamic Media è adattivo. Se si desidera impostare una dimensione fissa, impostare il componente nella scheda **[!UICONTROL Avanzate]** con le impostazioni **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]**.

* **[!UICONTROL Visualizzatore]**
predefinito: selezionate un predefinito per visualizzatori esistente dal menu a discesa. Se il predefinito per visualizzatori che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per visualizzatori. Non è possibile selezionare un predefinito per visualizzatori se si utilizza un predefinito per immagini, e viceversa.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi. Anche i predefiniti per visualizzatori sono avanzati: vengono visualizzati solo i predefiniti per visualizzatori pertinenti.

* **[!UICONTROL Modificatori di visualizzatoriI modificatori]**
Viewer assumono la forma di coppia nome=valore con un carattere di delimitazione &amp; e consentono di modificare i visualizzatori come indicato nella guida di riferimento dei visualizzatori. Un esempio di modificatore di visualizzatore è posterimage=img.jpg&amp;caption=text.vtt,1 che imposta un’immagine diversa per la miniatura del video e associa un file di sottotitoli/sottotitoli codificati al video.

* **[!UICONTROL Predefinito immagineSelezionate un predefinito per immagini esistente dal menu a discesa.]**
Se il predefinito per immagini che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per immagini. Non è possibile selezionare un predefinito per visualizzatori se si utilizza un predefinito per immagini, e viceversa.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL Modificatori]**
immaginiPotete applicare effetti immagine fornendo ulteriori comandi immagine. Questi sono descritti nei predefiniti per immagini e nel riferimento al comando Image Server.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL Punti di]**
interruzione: se utilizzi questa risorsa in un sito reattivo, devi aggiungere i punti di interruzione immagine. I punti di interruzione immagine devono essere separati da virgole (,). Questa opzione funziona quando non è stata definita alcuna altezza o larghezza in un predefinito immagine.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.
Per modificare le seguenti impostazioni avanzate, fai clic su **[!UICONTROL Modifica]** nel componente.

* ****
Titolo: consente di cambiare il titolo dell’immagine.

* **[!UICONTROL Alt]**
TextAggiungete un titolo all’immagine per gli utenti che hanno disattivato la grafica.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL URL, Apri]**
inPotete impostare una risorsa per aprire un collegamento. Imposta l’URL e in Apri in indica se desideri aprirlo nella stessa finestra o in una nuova finestra.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL Larghezza]** e  ****
altezzaSe si desidera che l’immagine sia di dimensioni fisse, immettere il valore in pixel. Lasciando vuoti questi valori, la risorsa viene resa adattiva.

#### Quando esegui operazioni con i Video {#when-working-with-video}

Usate il componente Dynamic Media per aggiungere video dinamici alle pagine Web. Quando modifichi il componente puoi scegliere di usare un predefinito visualizzatore video predefinita per la riproduzione del video nella pagina.

![chlimage_1-540](assets/chlimage_1-540.png)

È necessario modificare le seguenti impostazioni Dynamic Media facendo clic su **[!UICONTROL Modifica]** nel componente.

>[!NOTE]
>
>Per impostazione predefinita, il componente video elementi multimediali dinamici è adattivo. Se si desidera impostarne una dimensione fissa, impostarla nel componente con la scheda **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]** nella scheda [!UICONTROL Avanzate].

* **[!UICONTROL Visualizzatore]**
predefinito: selezionate un predefinito per visualizzatori video esistente dal menu a discesa. Se il predefinito per visualizzatori che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per visualizzatori. 

* **[!UICONTROL Modificatori di visualizzatoriI modificatori]**
Viewer hanno la forma di coppia nome=valore con un carattere di delimitazione &amp; e consentono di modificare i visualizzatori come indicato nella guida di riferimento dei visualizzatori di Adobi . Un esempio di modificatore di visualizzatore è posterimage=img.jpg&amp;caption=text.vtt,1

   Con i modificatori del visualizzatore, ad esempio, potete effettuare le seguenti operazioni:

   * Associare un file di sottotitoli a un video [caption.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Associare un file di navigazione a un video [di navigazione.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

È possibile modificare le seguenti [!UICONTROL Impostazioni avanzate] facendo clic su **[!UICONTROL Modifica]** nel componente.

* ****
Titolo: consente di cambiare il titolo del video.

* **[!UICONTROL Larghezza]** e  ****
altezza: specificate il valore in pixel se desiderate che il video sia di dimensione fissa. Se questi valori vengono lasciati vuoti, la risorsa sarà adattiva.

#### Durante l&#39;utilizzo di SmartCrop {#when-working-with-smart-crop}

Usate il componente Dynamic Media per aggiungere le risorse di immagine SmartCrop alle pagine Web. Quando modifichi il componente puoi scegliere di usare un predefinito visualizzatore video predefinita per la riproduzione del video nella pagina.

Vedere anche [Profili immagine](image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

È possibile modificare le seguenti [!UICONTROL Impostazioni Dynamic Media] facendo clic su **[!UICONTROL Modifica]** nel componente.

>[!NOTE]
>
>Per impostazione predefinita, il componente immagine Dynamic Media è adattivo. Se vuoi impostarne una dimensione fissa, lo puoi fare nella scheda [!UICONTROL Avanzate] del componente, alle voci **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]**.

* **[!UICONTROL Modificatori]**
immaginiPotete applicare effetti immagine fornendo ulteriori comandi immagine. Questi sono descritti nei predefiniti per immagini e nel riferimento al comando Image Server.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

Per modificare le seguenti impostazioni **[!UICONTROL Avanzate]**, fare clic su **[!UICONTROL Modifica]** nel componente.

* ****
Titolo: consente di cambiare il titolo dell’immagine Ritaglio avanzato.

* **[!UICONTROL Alt]**
TextAggiungete un titolo all’immagine di ritaglio avanzato per gli utenti che hanno disattivato la grafica.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **[!UICONTROL URL, Apri]**
inPotete impostare una risorsa per aprire un collegamento. Imposta l’URL e in Apri in indica se desideri aprirlo nella stessa finestra o in una nuova finestra.
Questa è l&#39;unica opzione disponibile se stai visualizzando set di immagini, set di rotazione o set di file multimediali diversi.

* **** Altezza e  ****
larghezzaImmettete il valore in pixel se desiderate che l’immagine di ritaglio avanzato sia di dimensione fissa. Se questi valori vengono lasciati vuoti, la risorsa sarà adattiva.

### Componente multimediale interattivo {#interactive-media-component}

Il Componente File multimediali interattivi è adatto per le risorse che dispongono di interattività, come punti attivi o mappe immagine. Se disponi di un&#39;immagine, un video interattivo o un banner carosello, utilizza il componente File multimediali interattivi.

Il componente Contenuti multimediali interattivi è elegante e offre diverse opzioni a seconda che sia stata aggiunta un’immagine o un video. Inoltre, il visualizzatore è reattivo: le dimensioni dello schermo cambiano automaticamente in base alle dimensioni reali dello stesso. Tutti i visualizzatori sono visualizzatori HTML5.

>[!NOTE]
>
>Se è presente un componente Dynamic Media, un componente Media interattivo o entrambi in una pagina Web a cui si accede da un utente con autorizzazioni di sola lettura, le interruzioni di pagina e il rendering dei componenti non vengono eseguiti correttamente. Questo perché la pagina viene ricostruita per garantire che le proprietà dei componenti siano buone e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina che causa l’interruzione dei componenti; il relativo codice componente sulla pagina non può essere riprodotto a causa dell’accesso in sola lettura dell’utente.
> 
>Per evitare questo problema, assicuratevi che  utenti AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

![chlimage_1-541](assets/chlimage_1-541.png)

È possibile modificare le seguenti impostazioni **[!UICONTROL Generali]**, facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Visualizzatore]**
predefinito: selezionate un predefinito per visualizzatori esistente dal menu a discesa. Se il predefinito per visualizzatori che cerchi non è visibile, potrebbe essere necessario renderlo visibile. I predefiniti per visualizzatori devono essere pubblicati prima di poter essere utilizzati. Consulta Gestione dei predefiniti per visualizzatori. 

* ****
Titolo: consente di cambiare il titolo del video.

* **[!UICONTROL Larghezza]** e  ****
altezza: specificate il valore in pixel se desiderate che il video sia di dimensione fissa. Se questi valori vengono lasciati vuoti, la risorsa sarà adattiva.

È possibile modificare le seguenti impostazioni **[!UICONTROL Aggiungi al carrello]**, facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Mostra]**
risorsa prodottoPer impostazione predefinita, questo valore è selezionato. La risorsa di prodotto mostra un&#39;immagine del prodotto in base a quanto definito nel modulo Commerce. Rimuovi il segno di spunta per non visualizzare la risorsa di prodotto.

* **[!UICONTROL Mostra]**
prezzo prodottoPer impostazione predefinita, questo valore è selezionato. Prezzo del prodotto mostra il prezzo dell&#39;elemento in base a quanto definito nel modulo Commerce. Rimuovi il segno di spunta per non visualizzare il prezzo del prodotto.

* **[!UICONTROL Mostra]**
modulo prodotto Per impostazione predefinita, questo valore non è selezionato. Il Modulo del prodotto include tutte le varianti del prodotto, come la dimensione e il colore. Rimuovi il segno di spunta per non visualizzare le varianti prodotto.

### Componente multimediale panoramica {#panoramic-media-component}

Il componente Contenuti multimediali panoramici è destinato alle risorse che sono immagini panoramiche sferiche. Tali immagini forniscono un&#39;esperienza di visualizzazione a 360° di una stanza, una proprietà, una posizione o un paesaggio. Affinché un’immagine possa essere definita come panorama sferico, deve avere una O entrambe le caratteristiche seguenti:

* Proporzioni di 2:1.
* Etichettate con le parole chiave &quot;equirettangolare&quot; o (&quot;sferico&quot; + &quot;panorama&quot;) o (&quot;sferico&quot; + &quot;panoramico&quot;). Vedere [Utilizzo dei tag](/help/sites-authoring/tags.md).

Sia le proporzioni che i criteri delle parole chiave si applicano alle risorse panoramiche per la pagina dei dettagli delle risorse che per il componente WCM &quot;File multimediali panoramici&quot;.

![panoramica-media-predefinito per visualizzatori](assets/panoramic-media-viewer-preset.png)

Per modificare la seguente impostazione, tocca **[!UICONTROL Configura]** nel componente.

* **[!UICONTROL Visualizzatore]**
predefinito: selezionate un visualizzatore esistente dal menu a discesa Predefinito visualizzatore.

Se il predefinito per visualizzatori ricercato non è visibile, accertatevi che sia pubblicato. Per poter usare i predefiniti per visualizzatori, dovete pubblicarli. Consulta [Gestione dei predefiniti per visualizzatori](managing-viewer-presets.md). 

### Utilizzo di HTTP/2 per la distribuzione di risorse Dynamic Media {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 è il nuovo protocollo Web aggiornato che migliora il modo in cui i browser e i server comunicano. Fornisce un trasferimento più rapido delle informazioni e riduce la quantità di potenza di elaborazione necessaria. La distribuzione delle risorse Dynamic Media ora può avvenire tramite HTTP/2, migliorando la risposta e i tempi di caricamento.

Per informazioni dettagliate sull&#39;utilizzo di HTTP/2 con l&#39;account Dynamic Media, vedere [HTTP2 Delivery of Content](http2.md).

>[!MORELIKETHIS]
>
>* [Gestione del colore con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [Utilizzo della miniatura video personalizzata con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Il visualizzatore delle risorse con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [Utilizzo di video interattivi con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [Utilizzo del lettore video in AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [Utilizzo della nitidezza delle immagini con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

