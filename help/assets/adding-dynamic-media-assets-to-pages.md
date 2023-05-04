---
title: Aggiungere risorse Dynamic Media alle pagine
description: Come aggiungere componenti Dynamic Media alle pagine in Adobe Experience Manager
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
exl-id: bb97b649-a50d-49c8-97aa-18c32f18d527
feature: Components
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2845'
ht-degree: 4%

---

# Aggiunta di risorse Dynamic Media alle pagine {#adding-dynamic-media-assets-to-pages}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per aggiungere la funzionalità Dynamic Media alle risorse utilizzate sui siti web, puoi aggiungere la **Dynamic Media** o **File multimediali interattivi** direttamente sulla pagina. A tale scopo, entra in modalità Layout e attiva i componenti per contenuti multimediali dinamici. Quindi, potrai aggiungere questi componenti alla pagina e fornire così risorse al componente. I componenti per contenuti multimediali dinamici e per contenuti multimediali interattivi sono intelligenti: sanno se aggiungi un’immagine o un video e le opzioni disponibili cambiano di conseguenza.

Se utilizzi AEM come WCM, aggiungi direttamente alla pagina le risorse Dynamic Media. Se ti avvali di una terza parte per WCM, puoi [collegare](linking-urls-to-yourwebapplication.md) o [incorporare](embed-code.md) le risorse. Per un sito web dinamico di terze parti, consulta la sezione [Distribuzione di immagini ottimizzate in un sito dinamico](responsive-site.md).

>[!NOTE]
>
>È necessario pubblicare le risorse prima di aggiungerle alle pagine di AEM. Vedi [Pubblicazione delle risorse Dynamic Media](publishing-dynamicmedia-assets.md).

## Aggiunta di un componente Dynamic Media a una pagina {#adding-a-dynamic-media-component-to-a-page}

L’aggiunta di un componente Dynamic Media a una pagina equivale all’aggiunta di un componente a qualsiasi pagina. I componenti Dynamic Media sono descritti in dettaglio nelle sezioni seguenti.

>[!NOTE]
>
>Se in una pagina web è presente un componente Dynamic Media a cui accede un utente con autorizzazioni di sola lettura, le interruzioni di pagina e il rendering dei componenti non vengono eseguiti correttamente. Il motivo è che la pagina viene ricostruita per garantire che le proprietà dei componenti siano corrette e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina, causando l’interruzione dei componenti; non è possibile eseguire nuovamente il rendering del rispettivo codice componente sulla pagina a causa dell’accesso in sola lettura dell’utente.
>  
>Per evitare questo problema, accertati che gli utenti AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

1. In AEM, apri la pagina in cui desideri aggiungere il componente Dynamic Media.
1. Nel pannello a sinistra della pagina (potrebbe essere necessario attivare o disattivare la visualizzazione del pannello laterale), fai clic sul pulsante **[!UICONTROL Componenti]** icona.
1. Sotto la **[!UICONTROL Componenti]** nell’elenco a discesa, seleziona **[!UICONTROL Dynamic Media]**. Se non è disponibile alcun elenco di componenti Dynamic Media, è probabile che sia necessario abilitare i componenti Dynamic Media che si desidera utilizzare. Vedi [Abilitazione dei componenti Dynamic Media](#enabling-dynamic-media-components).

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. Trascina un componente Dynamic Media da utilizzare nella pagina nella posizione desiderata.
1. Passa il puntatore del mouse direttamente sul componente. Quando un componente è circondato da una casella blu, tocca una volta per visualizzare la barra degli strumenti del componente. Tocca **[!UICONTROL Configurazione]** (chiave inglese).
1. [Modificare i componenti](#dynamic-media-components) se necessario, fai clic sul segno di spunta per salvare le modifiche.

### Abilitazione dei componenti Dynamic Media {#enabling-dynamic-media-components}

Se non è disponibile alcun componente Dynamic Media da aggiungere a una pagina, è probabile che sia necessario prima abilitare i componenti da utilizzare.

1. In AEM, apri la pagina in cui desideri aggiungere il componente Dynamic Media.
1. Sul lato sinistro della barra degli strumenti vicino alla parte superiore della pagina, tocca l’icona Informazioni pagina , quindi tocca **[!UICONTROL Modifica modello]** dall’elenco a discesa.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Sul lato destro della barra degli strumenti vicino alla parte superiore della pagina, dall’elenco a discesa tocca **[!UICONTROL Struttura]**.

   ![Criterio](/help/assets/assets-dm/structure-mode.png)

1. Nella parte inferiore della pagina, tocca **[!UICONTROL Contenitore di layout]** per aprire la relativa barra degli strumenti, tocca l’icona Criterio .
1. Sulla **[!UICONTROL Contenitore di layout]** sotto **[!UICONTROL Proprietà]** intestazione, assicurati che **[!UICONTROL Componenti consentiti]** è selezionata.

   ![Componenti consentiti](/help/assets/assets-dm/allowed-components.png)

1. Scorri fino a visualizzare **[!UICONTROL Dynamic Media]**.
1. Tocca l’icona > a sinistra di **[!UICONTROL Dynamic Media]** per espandere l’elenco, seleziona i componenti Dynamic Media che desideri abilitare.

   ![Elenco dei componenti di Dynamic Media](/help/assets/assets-dm/dm-components-select.png)

1. Vicino all&#39;angolo superiore destro del **[!UICONTROL Contenitore di layout]** Tocca l’icona Fine (segno di spunta) .

1. Sul lato destro della barra degli strumenti vicino alla parte superiore della pagina, dall’elenco a discesa tocca **[!UICONTROL Contenuto iniziale]**, quindi [aggiungere un componente Dynamic Media a una pagina](#adding-a-dynamic-media-component-to-a-page) come al solito.

## Localizzazione dei componenti Dynamic Media {#localizing-dynamic-media-components}

Puoi localizzare i componenti Dynamic Media in uno dei due modi seguenti:

* In una pagina web di Sites, apri **[!UICONTROL Proprietà]** e seleziona la scheda **[!UICONTROL Avanzate]**. Scegli la lingua desiderata per la localizzazione.

   ![chlimage_1-538](assets/chlimage_1-538.png)

* Dal selettore del sito, seleziona la pagina o il gruppo di pagine desiderato. Tocca **[!UICONTROL Proprietà]** e seleziona la **[!UICONTROL Avanzate]** scheda . Scegli la lingua desiderata per la localizzazione.

   >[!NOTE]
   >
   >Si prega di notare che non tutte le lingue disponibili nella **[!UICONTROL Lingua]** al momento sono assegnati token.

## Componenti Dynamic Media {#dynamic-media-components}

Dynamic Media e Interactive Media sono disponibili nella sezione [!UICONTROL Dynamic Media] scheda in [!UICONTROL Componenti]. Utilizzi le [!UICONTROL File multimediali interattivi] per qualsiasi risorsa interattiva, ad esempio video interattivo, immagini interattive o set carosello. Per tutti gli altri componenti multimediali dinamici, utilizza il componente Dynamic Media .

>[!NOTE]
>
>Questi componenti non sono disponibili per impostazione predefinita e devono essere resi disponibili tramite l’editor modelli prima dell’utilizzo. [Una volta resi disponibili](/help/sites-authoring/templates.md#editing-templates-template-authors) nell’editor modelli, puoi aggiungere i componenti alla pagina come qualsiasi altro componente AEM.

![chlimage_1-539](assets/chlimage_1-539.png)

### Componente Dynamic Media {#dynamic-media-component}

Il componente Dynamic Media è intelligente: a seconda che si aggiunga un’immagine o un video, sono disponibili varie opzioni. Il componente supporta i predefiniti per immagini, i visualizzatori basati su immagini come set di immagini, set 360 gradi, set di file multimediali diversi e video. Inoltre, il visualizzatore è reattivo. In altre parole, le dimensioni dello schermo cambiano automaticamente in base alle dimensioni dello schermo. Tutti i visualizzatori sono visualizzatori HTML5.

>[!NOTE]
>
>Se è presente un componente Dynamic Media, un componente File multimediali interattivi o entrambi in una pagina web a cui si accede da un utente con autorizzazioni di sola lettura, le interruzioni di pagina e il rendering dei componenti non vengono eseguiti correttamente. Il motivo è che la pagina viene ricostruita per garantire che le proprietà dei componenti siano corrette e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina, causando l’interruzione dei componenti; non è possibile eseguire nuovamente il rendering del rispettivo codice componente sulla pagina a causa dell’accesso in sola lettura dell’utente.
>  
>Per evitare questo problema, accertati che gli utenti AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

>[!NOTE]
>
>Quando aggiungi il componente Dynamic Media e **[!UICONTROL Impostazioni Dynamic Media]** è vuoto oppure non è possibile aggiungere correttamente una risorsa, controlla quanto segue:
>
>* Hai [Dynamic Media abilitato](config-dynamic.md). Dynamic Media è disattivato per impostazione predefinita.
>* L&#39;immagine ha un file TIFF piramidale. Le immagini importate prima dell’abilitazione del supporto dinamico non dispongono di un file TIFF piramidale.
>


#### Quando si lavora con le immagini {#when-working-with-images}

Il componente Dynamic Media consente di aggiungere immagini dinamiche, compresi set di immagini, set 360 gradi e set di file multimediali diversi. Potete ingrandire, ridurre e, se applicabile, ruotare un&#39;immagine all&#39;interno di un set 360 gradi o selezionare un&#39;immagine da un altro tipo di set.

Puoi anche configurare il predefinito visualizzatore, il predefinito immagine o il formato immagine direttamente nel componente. Per rendere un’immagine reattiva, puoi impostare i punti di interruzione o applicare un predefinito per immagini reattive.

Per modificare le seguenti impostazioni di Dynamic Media, fai clic sul pulsante **[!UICONTROL Modifica]** nel componente e quindi **[!UICONTROL Impostazioni Dynamic Media]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Per impostazione predefinita, il componente immagine Dynamic Media è adattivo. Se vuoi impostarne una dimensione fissa, impostala nel componente nel **[!UICONTROL Avanzate]** con la scheda **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]** impostazioni.

* **[!UICONTROL Predefinito visualizzatore]**
Seleziona un predefinito per visualizzatori dal menu a discesa. Se il predefinito per visualizzatori che stai cercando non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per visualizzatori . Non puoi selezionare un predefinito per visualizzatori se utilizzi un predefinito per immagini e viceversa.
Questa è l’unica opzione disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi. Anche i predefiniti visualizzatore visualizzati sono intelligenti: vengono visualizzati solo i predefiniti visualizzatore pertinenti.

* **[!UICONTROL Modificatori visualizzatore]**
I modificatori del visualizzatore assumono la forma di coppia nome=valore con un delimitatore &amp; e consentono di modificare i visualizzatori come descritto nella Guida di riferimento visualizzatori. Un esempio di modificatore di visualizzatore è posterimage=img.jpg&amp;caption=text.vtt,1 che imposta un’immagine diversa per la miniatura del video e associa un file di sottotitoli/sottotitoli codificati al video.

* **[!UICONTROL Predefinito immagine]**
Seleziona un predefinito per immagini dal menu a discesa. Se il predefinito immagine che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per immagini . Non puoi selezionare un predefinito per visualizzatori se utilizzi un predefinito per immagini e viceversa.
Questa opzione non è disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi.

* **[!UICONTROL Modificatori immagine]**
È possibile applicare effetti immagine fornendo comandi immagine aggiuntivi. Questi sono descritti in Predefiniti immagini e nella documentazione di riferimento Image Serving Command.
Questa opzione non è disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi.

* **[!UICONTROL Punti di interruzione]**
Se utilizzi questa risorsa su un sito reattivo, devi aggiungere i punti di interruzione immagine. I punti di interruzione dell’immagine devono essere separati da virgole (,). Questa opzione funziona quando non è definita alcuna altezza o larghezza in un predefinito per immagini.
Questa opzione non è disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi.
Puoi modificare le seguenti Impostazioni avanzate facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Titolo]**
Modifica il titolo dell’immagine.

* **[!UICONTROL Testo Alt]**
Aggiungi un titolo all’immagine per gli utenti che hanno disattivato la grafica.
Questa opzione non è disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi.

* **[!UICONTROL URL, Apri in]**
Puoi impostare una risorsa per aprire un collegamento. Imposta l’URL e in Apri in indica se desideri aprirlo nella stessa finestra o in una nuova finestra.
Questa opzione non è disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi.

* **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]**
Immetti il valore in pixel se desideri che l’immagine sia di dimensioni fisse. Lasciando vuoti questi valori, la risorsa diventa adattiva.

#### Quando si lavora con i video {#when-working-with-video}

Utilizza il componente Dynamic Media per aggiungere video dinamici alle pagine web. Quando modifichi il componente puoi scegliere di utilizzare un predefinito visualizzatore video per la riproduzione del video sulla pagina.

![chlimage_1-540](assets/chlimage_1-540.png)

È necessario modificare le seguenti impostazioni di Dynamic Media facendo clic su **[!UICONTROL Modifica]** nel componente.

>[!NOTE]
>
>Per impostazione predefinita, il componente video Dynamic Media è adattivo. Se vuoi impostarne una dimensione fissa, impostala nel componente con la **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]** in [!UICONTROL Avanzate] scheda .

* **[!UICONTROL Predefinito visualizzatore]**
Seleziona un predefinito per visualizzatori video dal menu a discesa. Se il predefinito per visualizzatori che stai cercando non è visibile, potrebbe essere necessario renderlo visibile. Consulta Gestione dei predefiniti per visualizzatori .

* **[!UICONTROL Modificatori visualizzatore]**
I modificatori del visualizzatore assumono la forma di coppia nome=valore con un delimitatore &amp; e consentono di modificare i visualizzatori come descritto nella Guida di riferimento visualizzatori di Adobe. Un esempio di modificatore di visualizzatore è posterimage=img.jpg&amp;caption=text.vtt,1

   Con i modificatori visualizzatore, ad esempio, puoi effettuare le seguenti operazioni:

   * Associare un file di didascalia a un video [didascalia.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Associare un file di navigazione a un video [navigazione.](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

È possibile modificare quanto segue [!UICONTROL Impostazioni avanzate] facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Titolo]**
Modifica il titolo del video.

* **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]**
Immetti il valore in pixel se vuoi che il video sia di dimensioni fisse. Lasciando vuoti questi valori, diventa adattivo.

#### Quando si lavora con Smart Crop {#when-working-with-smart-crop}

Utilizza il componente Dynamic Media per aggiungere le risorse immagine ritaglio avanzato alle pagine web. Quando modifichi il componente puoi scegliere di utilizzare un predefinito visualizzatore video per la riproduzione del video sulla pagina.

Vedi anche [Profili immagine](image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

È possibile modificare quanto segue [!UICONTROL Impostazioni Dynamic Media] facendo clic su **[!UICONTROL Modifica]** nel componente.

>[!NOTE]
>
>Per impostazione predefinita, il componente immagine Dynamic Media è adattivo. Se vuoi impostarne una dimensione fissa, lo puoi fare nella scheda [!UICONTROL Avanzate] del componente, alle voci **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]**.

* **[!UICONTROL Modificatori immagine]**
È possibile applicare effetti immagine fornendo comandi immagine aggiuntivi. Questi sono descritti in Predefiniti immagini e nella documentazione di riferimento Image Serving Command.
Questa opzione non è disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi.

È possibile modificare quanto segue **[!UICONTROL Avanzate]** impostazioni facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Titolo]**
Modifica il titolo dell’immagine Ritaglio avanzato.

* **[!UICONTROL Testo Alt]**
Aggiungi un titolo all’immagine di ritaglio avanzato per gli utenti che hanno disattivato la grafica.
Questa opzione non è disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi.

* **[!UICONTROL URL, Apri in]**
Puoi impostare una risorsa per aprire un collegamento. Imposta l’URL e in Apri in indica se desideri aprirlo nella stessa finestra o in una nuova finestra.
Questa opzione non è disponibile se visualizzi set di immagini, set 360 gradi o set di file multimediali diversi.

* **[!UICONTROL Altezza]** e **[!UICONTROL Larghezza]**
Immetti il valore in pixel se desideri che l’immagine di ritaglio avanzato sia di dimensioni fisse. Lasciando vuoti questi valori, diventa adattivo.

### Componente File multimediali interattivi {#interactive-media-component}

Il componente File multimediali interattivi è destinato alle risorse che dispongono di interattività, come punti attivi o mappe immagine. Se disponi di un’immagine, un video interattivo o un banner carosello, utilizza il componente File multimediali interattivi .

Il componente File multimediali interattivi è intelligente: a seconda che si aggiunga un’immagine o un video, sono disponibili varie opzioni. Inoltre, il visualizzatore è reattivo: le dimensioni dello schermo cambiano automaticamente in base alle dimensioni dello schermo. Tutti i visualizzatori sono visualizzatori HTML5.

>[!NOTE]
>
>Se è presente un componente Dynamic Media, un componente File multimediali interattivi o entrambi in una pagina web a cui si accede da un utente con autorizzazioni di sola lettura, le interruzioni di pagina e il rendering dei componenti non vengono eseguiti correttamente. Il motivo è che la pagina viene ricostruita per garantire che le proprietà dei componenti siano corrette e che tutte le risorse e le configurazioni di riferimento siano accessibili. Viene quindi eseguito di nuovo il rendering della pagina, causando l’interruzione dei componenti; non è possibile eseguire nuovamente il rendering del rispettivo codice componente sulla pagina a causa dell’accesso in sola lettura dell’utente.
> 
>Per evitare questo problema, accertati che gli utenti AEM Sites dispongano delle autorizzazioni necessarie per accedere alle risorse.

![chlimage_1-541](assets/chlimage_1-541.png)

È possibile modificare quanto segue **[!UICONTROL Generale]** impostazioni facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Predefinito visualizzatore]**
Seleziona un predefinito per visualizzatori dal menu a discesa. Se il predefinito per visualizzatori che stai cercando non è visibile, potrebbe essere necessario renderlo visibile. I predefiniti per visualizzatori devono essere pubblicati prima di poter essere utilizzati. Consulta Gestione dei predefiniti per visualizzatori .

* **[!UICONTROL Titolo]**
Modifica il titolo del video.

* **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]**
Immetti il valore in pixel se vuoi che il video sia di dimensioni fisse. Lasciando vuoti questi valori, diventa adattivo.

È possibile modificare quanto segue **[!UICONTROL Aggiungi al carrello]** impostazioni facendo clic su **[!UICONTROL Modifica]** nel componente.

* **[!UICONTROL Mostra risorsa prodotto]**
Per impostazione predefinita, questo valore è selezionato. La risorsa prodotto mostra un’immagine del prodotto come definito nel modulo Commerce . Deseleziona il segno di spunta per non visualizzare la risorsa del prodotto.

* **[!UICONTROL Mostra prezzo prodotto]**
Per impostazione predefinita, questo valore è selezionato. Il prezzo del prodotto mostra il prezzo dell’articolo come definito nel modulo Commerce. Deselezionare il segno di spunta per non visualizzare il prezzo del prodotto.

* **[!UICONTROL Mostra modulo di prodotto]**
Per impostazione predefinita, questo valore non è selezionato. Il modulo di prodotto include tutte le varianti di prodotto, ad esempio le dimensioni e il colore. Deselezionare il segno di spunta per non visualizzare le varianti di prodotto.

### Componente Elemento multimediale panoramico {#panoramic-media-component}

Il componente Elemento multimediale panoramico è per le risorse che sono immagini panoramiche sferiche. Tali immagini offrono un&#39;esperienza di visualizzazione a 360° di una stanza, proprietà, posizione o paesaggio. Affinché un&#39;immagine si qualifichi come panorama sferico, deve avere uno O entrambi i seguenti elementi:

* Rapporto di formato 2:1.
* Etichettate con le parole chiave &quot;equirettangolare&quot; o (&quot;sferico&quot; + &quot;panorama&quot;) o (&quot;sferico&quot; + &quot;panoramico&quot;). Vedi [Utilizzo dei tag](/help/sites-authoring/tags.md).

Sia le proporzioni che i criteri delle parole chiave si applicano alle risorse panoramiche della pagina dei dettagli delle risorse che il componente WCM &quot;Elemento multimediale panoramico&quot;.

![panoramico-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

Per modificare l’impostazione seguente, tocca **[!UICONTROL Configura]** nel componente.

* **[!UICONTROL Predefinito visualizzatore]**
Seleziona un visualizzatore esistente dal menu a discesa Predefinito visualizzatore .

Se il predefinito per visualizzatori che stai cercando non è visibile, assicurati che sia pubblicato. È necessario pubblicare i predefiniti visualizzatore prima di poterli utilizzare. Vedi [Gestione dei predefiniti per visualizzatori](managing-viewer-presets.md).

### Utilizzo di HTTP/2 per la distribuzione delle risorse Dynamic Media {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 è il nuovo protocollo web aggiornato che migliora il modo in cui i browser e i server comunicano. Fornisce un trasferimento più rapido delle informazioni e riduce la quantità di potenza di elaborazione necessaria. La distribuzione delle risorse Dynamic Media può ora avvenire tramite HTTP/2, garantendo tempi di risposta e caricamento migliori.

Vedi [Distribuzione di contenuti HTTP2](http2.md) per informazioni complete su come iniziare a utilizzare HTTP/2 con il tuo account Dynamic Media.

>[!MORELIKETHIS]
>
>* [Informazioni sulla gestione del colore con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [Utilizzo di miniature video personalizzate con Dynamic Media AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Informazioni sul Visualizzatore risorse con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [Utilizzo di video interattivi con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [Utilizzo del lettore video in AEM Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [Utilizzo della nitidezza delle immagini con AEM Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)

