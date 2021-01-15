---
title: Aggiunta di funzionalità di Dynamic Media Classic alla pagina
seo-title: Aggiunta di funzionalità di Dynamic Media Classic alla pagina
description: ' Adobe Dynamic Media Classic è una soluzione in hosting per la gestione, l''ottimizzazione, la pubblicazione e la distribuzione di risorse multimediali su schermi e stampe Web, mobili, e-mail e connessi a Internet.'
seo-description: ' Adobe Dynamic Media Classic è una soluzione in hosting per la gestione, l''ottimizzazione, la pubblicazione e la distribuzione di risorse multimediali su schermi e stampe Web, mobili, e-mail e connessi a Internet.'
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
translation-type: tm+mt
source-git-commit: 0016825ced6706cda7447546af876d5a897c8ff5
workflow-type: tm+mt
source-wordcount: '3428'
ht-degree: 31%

---


# Aggiunta di funzionalità di Dynamic Media Classic alla pagina{#adding-scene-features-to-your-page}

[ Adobe Dynamic Media ](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) Classicis è una soluzione in hosting per la gestione, il miglioramento, la pubblicazione e la distribuzione di risorse multimediali su display e stampe Web, mobili, e-mail e connessi a Internet.

Potete visualizzare AEM risorse pubblicate in Dynamic Media Classic in vari visualizzatori:

* Zoom
* A comparsa
* Video
* Modello immagini
* Immagine

Potete pubblicare le risorse digitali direttamente da AEM ad Dynamic Media Classic e pubblicare le risorse digitali da Dynamic Media Classic a AEM.

Questa sezione descrive come pubblicare risorse digitali da AEM ad Dynamic Media Classic e viceversa. Sono inoltre descritti nel dettaglio i visualizzatori. Per informazioni sulla configurazione di AEM per Dynamic Media Classic, consultate [Integrazione di Dynamic Media Classic con AEM](/help/sites-administering/scene7.md).

Consulta anche [Aggiunta di mappe immagine](/help/assets/image-maps.md).

Per ulteriori informazioni sull’uso dei componenti video con AEM, consulta i seguenti riferimenti:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Se le risorse Dynamic Media Classic non vengono visualizzate correttamente, accertatevi che il supporto dinamico sia [disabilitato](/help/assets/config-dynamic.md#disabling-dynamic-media), quindi aggiornate la pagina.

## Pubblicazione manuale in Dynamic Media Classic da risorse {#manually-publishing-to-scene-from-assets}

Puoi pubblicare risorse digitali in Dynamic Media Classic dalla console Risorse nell’interfaccia classica o direttamente dalla risorsa.

>[!NOTE]
>
>AEM viene pubblicato in Dynamic Media Classic in modo asincrono. Dopo aver fatto clic su **[!UICONTROL Pubblica]**, la pubblicazione della risorsa in Dynamic Media Classic potrebbe richiedere alcuni secondi.


### Pubblicazione dalla console Assets {#publishing-from-the-assets-console}

Per pubblicare contenuti da Dynamic Media Classic dalla console Risorse se le risorse si trovano in una cartella di destinazione Dynamic Media Classic:

1. Nell&#39;interfaccia AEM classica, fai clic su **[!UICONTROL Risorse digitali]** per accedere a Gestione risorse digitali.

1. Selezionate la risorsa (o le risorse) o la cartella dalla cartella di destinazione che desiderate pubblicare in Dynamic Media Classic e fate clic con il pulsante destro del mouse, quindi selezionate **[!UICONTROL Pubblica in Dynamic Media Classic]**. In alternativa, è possibile selezionare **[!UICONTROL Pubblica in Dynamic Media Classic]** dal menu **[!UICONTROL Strumenti]**.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Passate ad Dynamic Media Classic e verificate che le risorse siano disponibili.

   >[!NOTE]
   >
   >Se le risorse non si trovano in una cartella sincronizzata Dynamic Media Classic, **[!UICONTROL Pubblica in Dynamic Media Classic]** in entrambi i menu è visibile ma disattivata.

### Pubblicazione da una risorsa {#publishing-from-an-asset}

Potete pubblicare manualmente una risorsa purché sia ubicata all’interno della cartella sincronizzata di Dynamic Media Classic.

>[!NOTE]
>
>Se la risorsa non si trova nella cartella sincronizzata Dynamic Media Classic, il collegamento a **[!UICONTROL Pubblica in Dynamic Media Classic]** non è disponibile.

**Per pubblicare contenuti in Dynamic Media Classic direttamente da una risorsa** digitale:

1. In AEM, fai clic su **[!UICONTROL Risorse digitali]** per accedere al manager di risorse digitali.

1. Fai doppio clic per aprire una risorsa.

1. Nel riquadro dei dettagli delle risorse, selezionate **[!UICONTROL Pubblica in Dynamic Media Classic]**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. Il collegamento diventa **[!UICONTROL Pubblicazione...]** e quindi **[!UICONTROL Pubblicato]**. Andate ad Dynamic Media Classic e confermate che la risorsa sia disponibile.

   >[!NOTE]
   >
   >Se la risorsa non viene pubblicata correttamente in Dynamic Media Classic, il collegamento diventa **[!UICONTROL Pubblicazione non riuscita]**. Se la risorsa è già stata pubblicata in Dynamic Media Classic, il collegamento riporta **[!UICONTROL Ripubblica in Dynamic Media Classic]**. La ripubblicazione consente di apportare modifiche a una risorsa in AEM e di ripubblicarla.

### Pubblicazione di risorse dall&#39;esterno della cartella di destinazione CQ {#publishing-assets-from-outside-the-cq-target-folder}

 Adobe consiglia di pubblicare le risorse in Dynamic Media Classic solo dalle risorse presenti nella cartella di destinazione di Dynamic Media Classic. Tuttavia, se dovete caricare le risorse da una cartella esterna alla cartella di destinazione, potete comunque caricarle in una cartella *ad-hoc* in Dynamic Media Classic.

A tale scopo, configura la configurazione Cloud per la pagina in cui apparirà la risorsa. Quindi aggiungete un componente Dynamic Media Classic alla pagina e trascinate e rilasciate una risorsa sul componente. Dopo aver impostato le proprietà della pagina, viene visualizzato un collegamento **[!UICONTROL Pubblica in Dynamic Media Classic]** che, se selezionato, attiva il caricamento in Dynamic Media Classic.

>[!NOTE]
>
>Le risorse che si trovano nella cartella ad hoc non vengono visualizzate nel browser del contenuto di Dynamic Media Classic.

**Per pubblicare le risorse che risiedono al di fuori della cartella di destinazione di CQ**:

1. Nell&#39;AEM dell&#39;interfaccia classica, fai clic su **[!UICONTROL Siti Web]** e passa alla pagina Web in cui desideri aggiungere una risorsa digitale a cui non sia ancora stata pubblicata in Dynamic Media Classic. (Si applicano le normali regole di ereditarietà delle pagine.)

1. Nella barra laterale, fare clic sull&#39;icona **[!UICONTROL Pagina]**, quindi fare clic su **[!UICONTROL Proprietà pagina]**.

1. Fare clic su **[!UICONTROL Cloud Services] > [!UICONTROL Aggiungi servizi] > [!UICONTROL Dynamic Media Classic (Scene7)]**.
1. Nell&#39;elenco a discesa Dynamic Media Classic  Adobe, selezionate la configurazione desiderata, quindi fate clic su **[!UICONTROL OK]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. Nella pagina Web, aggiungete un componente Dynamic Media Classic (Scene7) nella posizione desiderata sulla pagina.
1. Dal Content Finder, trascina una risorsa digitale sul componente. Viene visualizzato un collegamento a **[!UICONTROL Controlla stato pubblicazione Dynamic Media Classic]**.

   >[!NOTE]
   >
   >Se la risorsa digitale si trova nella cartella di destinazione CQ, non viene visualizzato alcun collegamento a **[!UICONTROL Controlla stato pubblicazione Dynamic Media Classic]**. Le risorse sono semplicemente inserite nel componente.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Fare clic su **[!UICONTROL Controlla stato pubblicazione Dynamic Media Classic]**. Se la risorsa non è pubblicata, AEM pubblica la risorsa in Dynamic Media Classic. Dopo il caricamento, la risorsa si trova nella cartella ad-hoc. Per impostazione predefinita, la cartella ad hoc si trova in `name_of_the_company/CQ5_adhoc`. Se necessario, [è possibile configurarla](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Se la risorsa non si trova in una cartella sincronizzata Dynamic Media Classic e alla pagina corrente non è associata alcuna configurazione cloud Dynamic Media Classic, il caricamento non riuscirà.

## Componenti Dynamic Media Classic (Scene7) {#scene-components}

I seguenti componenti di Dynamic Media Classic sono disponibili in AEM:

* Zoom
* Zoom a comparsa
* Modello immagini
* Immagine
* Video

>[!NOTE]
>
>Questi componenti non sono disponibili per impostazione predefinita e devono essere selezionati in modalità **[!UICONTROL Progettazione]** prima di poter essere utilizzati.

Una volta resi disponibili in modalità **[!UICONTROL Progettazione]**, potete aggiungere i componenti alla pagina come qualsiasi altro componente AEM. Le risorse non ancora pubblicate in Dynamic Media Classic vengono pubblicate in Dynamic Media Classic se si trovano in una cartella sincronizzata o su una pagina o con una configurazione cloud Dynamic Media Classic.

### Avviso di fine ciclo di vita dei visualizzatori di Flash {#flash-viewers-end-of-life-notice}

A partire dal 31 gennaio 2017,  Adobe Dynamic Media Classic ha dichiarato ufficialmente terminato il supporto per la piattaforma di visualizzatori Flash.

Per ulteriori informazioni su questa importante modifica, consultate [Domande frequenti sulla fine del ciclo di vita del visualizzatore di Flash](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Aggiunta di un componente Dynamic Media Classic a una pagina {#adding-a-scene-component-to-a-page}

L’aggiunta di un componente Dynamic Media Classic a una pagina equivale all’aggiunta di un componente a qualsiasi pagina. I componenti di Dynamic Media Classic sono descritti dettagliatamente nelle sezioni seguenti.

**Per aggiungere un componente/visualizzatore Dynamic Media Classic a una pagina nell’interfaccia** classica:

1. In AEM, aprire la pagina in cui si desidera aggiungere il componente Dynamic Media Classic.

1. Se non sono disponibili componenti Dynamic Media Classic, fare clic sul righello nella barra laterale per passare alla modalità **[!UICONTROL Progettazione]**, fare clic su **[!UICONTROL Modifica]** parsys, quindi selezionare tutti i componenti **[!UICONTROL Dynamic Media Classic]** per renderli disponibili.

1. Tornate alla modalità **[!UICONTROL Modifica]** facendo clic sulla matita nella barra laterale.

1. Trascinate un componente dal gruppo **[!UICONTROL Dynamic Media Classic]** nella barra laterale sulla pagina nella posizione desiderata.

1. Fai clic su **[!UICONTROL Modifica]** per aprire il componente.

1. Se necessario, modifica il componente, quindi fai clic su **[!UICONTROL OK]** per salvare le modifiche.

### Aggiunta di esperienze di visualizzazione interattive a un sito web reattivo {#adding-interactive-viewing-experiences-to-a-responsive-website}

Una progettazione reattiva per le risorse significa che queste si adattano a seconda di dove vengono visualizzate. Con la progettazione reattiva, le stesse risorse vengono visualizzate in modo efficace su più dispositivi.

**Per aggiungere un’esperienza di visualizzazione interattiva a un sito reattivo nell’interfaccia classica**:

1. Accedete a AEM e accertatevi di avere [configurato  Adobe Dynamic Media Classic Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) e che siano disponibili componenti Dynamic Media Classic.

   >[!NOTE]
   >
   >Se i componenti di Dynamic Media Classic WCM non sono disponibili, accertatevi di attivarli in modalità **[!UICONTROL Progettazione].

1. In un sito Web con i componenti Dynamic Media Classic abilitati, trascinate un visualizzatore **[!UICONTROL Immagine]** sulla pagina.
1. Modificate il componente e regolate i punti di interruzione nella scheda **[!UICONTROL Dynamic Media Classic Settings]**.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Verifica che i visualizzatori si ridimensionino in modo reattivo e che tutte le interazioni siano ottimizzate per desktop, tablet e dispositivi mobili.

### Impostazioni comuni a tutti i componenti Dynamic Media Classic {#settings-common-to-all-scene-components}

Anche se le opzioni di configurazione variano, quanto segue è comune a tutti i componenti di Dynamic Media Classic:

* **[!UICONTROL File di riferimento]**: consente di individuare un file a cui fare riferimento. Il riferimento al file mostra l’URL della risorsa e non necessariamente l’URL completo di Dynamic Media Classic, inclusi i comandi e i parametri dell’URL. In questo campo non è possibile aggiungere parametri e comandi URL di Dynamic Media Classic. che devono essere aggiunti attraverso la funzionalità corrispondente nel componente.
* **[!UICONTROL Larghezza]**: consente di impostare la larghezza.
* **[!UICONTROL Altezza]**: consente di impostare l’altezza.

Per impostare queste opzioni di configurazione, fai doppio clic su un componente Dynamic Media Classic, ad esempio all&#39;apertura di un componente **[!UICONTROL Zoom]**:

![chlimage_1-80](assets/chlimage_1-80.png)

### Zoom {#zoom}

Il componente Zoom HTML5 visualizza un’immagine più grande quando si preme il pulsante +.

La risorsa dispone di strumenti di zoom nella parte inferiore. Fai clic su **[!UICONTROL +]** per ingrandire. Fai clic su **[!UICONTROL -]** per ridurre. Facendo clic su **[!UICONTROL x]** o sulla freccia di ripristino dello zoom, l&#39;immagine viene riportata alle dimensioni originali con cui è stata importata. Fai clic sulle frecce diagonali per renderla a schermo intero. Fai clic su **[!UICONTROL Modifica]** per configurare il componente. Con questo componente potete configurare le [impostazioni comuni a tutti i componenti Dynamic Media Classic](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-5.png)

### A comparsa {#flyout}

Nel componente A comparsa HTML5, la risorsa viene visualizzata come schermo diviso; a sinistra la risorsa nelle dimensioni specificate; a destra viene visualizzata la porzione di zoom. Fai clic su **[!UICONTROL Modifica]** per configurare il componente. Con questo componente potete configurare le [impostazioni comuni a tutti i componenti Dynamic Media Classic](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents).

>[!NOTE]
>
>Se il componente A comparsa utilizza una dimensione personalizzata, viene utilizzata tale dimensione e la configurazione reattiva del componente viene disabilitata.
>
>Se il componente a comparsa utilizza le dimensioni predefinite, come impostato nella vista [!UICONTROL Progettazione], viene utilizzata la dimensione predefinita e il componente si estende per adattarsi alle dimensioni del layout di pagina con l&#39;impostazione reattiva del componente abilitata. Tuttavia, tenete presente che esiste un limite alla configurazione reattiva del componente. Quando si utilizza il componente A comparsa con un’impostazione reattiva, non utilizzarlo con dilatazione sull’intera pagina. In caso contrario, il riquadro a comparsa potrebbe estendersi oltre il bordo destro della pagina.

![chlimage_1-81](assets/chlimage_1-81.png)

### Immagine {#image}

Il componente Immagine classica di Dynamic Media consente di aggiungere alle immagini funzionalità di Dynamic Media Classic, ad esempio modificatori Dynamic Media Classic, predefiniti per immagini o visualizzatori e nitidezza. Il componente immagine Dynamic Media Classic è simile ad altri componenti immagine in AEM con funzionalità Dynamic Media Classic speciale. In questo esempio, all&#39;immagine è applicato il modificatore URL Dynamic Media Classic, `&op_invert=1`.

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL Titolo, Testo]**  Alt - Nella scheda   Avanzate, aggiungete un titolo all’immagine e testo alternativo per gli utenti che hanno disattivato la grafica.

**[!UICONTROL URL, Apri in]**  - Puoi impostare una risorsa da cui aprire un collegamento. Impostare l&#39; **[!UICONTROL URL]** e **[!UICONTROL Apri in]** per indicare se si desidera aprirlo nella stessa finestra o in una nuova finestra.

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL Predefinito]**  visualizzatore - Selezionate un predefinito esistente dal menu a discesa. Se il predefinito per visualizzatori che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta [Gestione dei predefiniti per visualizzatori](/help/assets/managing-viewer-presets.md). Non è possibile selezionare un predefinito per visualizzatori se si utilizza un predefinito per immagini, e viceversa.

**[!UICONTROL Configurazione]**  Dynamic Media Classic - Selezionate la configurazione Dynamic Media Classic da usare per recuperare i predefiniti per immagini attivi da Scene7 Publishing System.

**[!UICONTROL Predefinito]**  immagine - Selezionate un predefinito per immagini esistente dal menu a discesa. Se il predefinito per immagini che cerchi non è visibile, potrebbe essere necessario renderlo visibile. Consulta [Gestione dei predefiniti per immagini](/help/assets/managing-image-presets.md). Non è possibile selezionare un predefinito per visualizzatori se si utilizza un predefinito per immagini, e viceversa.

**[!UICONTROL Formato]**  di output - Selezionare il formato di output dell&#39;immagine, ad esempio jpeg. A seconda del formato di output selezionato, è possibile che siano disponibili ulteriori opzioni di configurazione. Consulta [Gestione dei predefiniti per immagini](/help/assets/managing-image-presets.md).

**[!UICONTROL Nitidezza]**  - Selezionate la modalità di nitidezza dell’immagine. La nitidezza viene spiegata nel dettaglio in [*Adobe Dynamic Media Classic Image Quality and Sharpening Best Practices*](/help/assets/assets/sharpening_images.pdf).

**[!UICONTROL Modificatori]**  URL: potete modificare gli effetti immagine fornendo ulteriori comandi immagine Dynamic Media Classic. Sono descritte in [Gestione dei predefiniti per immagini](/help/assets/managing-image-presets.md) e [Riferimento comando](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL Punti di interruzione]**  - Se il sito Web è reattivo, è necessario regolare i punti di interruzione. I punti di interruzione devono essere separati da virgole `,`.

### Modello immagini {#image-template}

[I ](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) modelli di immagini classici di Dynamic Media sono contenuti Photoshop con più livelli importati in Dynamic Media Classic, con contenuti e proprietà parametrizzati per la variabilità. Il componente **[!UICONTROL Modello immagini]** consente di importare immagini e modificare il testo in modo dinamico in AEM. Inoltre, è possibile configurare il componente **[!UICONTROL Modello immagini]** in modo che utilizzi valori contestuali ClientContext, affinché ogni utente possa avere un’esperienza personalizzata dell’immagine.

Fai clic su **[!UICONTROL Modifica]** per configurare il componente. È possibile configurare le impostazioni [comuni a tutti i componenti di Dynamic Media Classic](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents), nonché altre impostazioni descritte in questa sezione.

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL Riferimento file, Larghezza, Altezza]**  - Vedere le impostazioni comuni a tutti i componenti Dynamic Media Classic.

>[!NOTE]
>
>I comandi e i parametri URL di Dynamic Media Classic non possono essere aggiunti direttamente all’URL di riferimento del file. Possono essere definiti solo nell’interfaccia utente del componente del pannello **[!UICONTROL Parametri]**.

**[!UICONTROL Titolo,]** Testo AltNella scheda Modello   Dynamic Media Classic per immagini, aggiungete un titolo all’immagine e testo alt per gli utenti che hanno disattivato la grafica.

**[!UICONTROL URL, Apri]** inPotete impostare una risorsa da cui aprire un collegamento. Imposta l’**[!UICONTROL URL]** e in **[!UICONTROL Apri in]** indica se desideri aprirlo nella stessa finestra o in una nuova finestra.

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL Pannello]** Parametri: quando importate un’immagine, i parametri vengono precompilati con le informazioni dell’immagine. Se non vi sono contenuti modificabili dinamicamente, questa finestra è vuota.

![chlimage_1-85](assets/chlimage_1-85.png)

#### Modifica dinamica del testo {#changing-text-dynamically}

Per modificare il testo in modo dinamico, immetti un nuovo testo nei campi e fai clic su **[!UICONTROL OK]**. In questo esempio, il **[!UICONTROL Prezzo]** è ora di $50 e la spedizione è di 99 centesimi.

![chlimage_1-86](assets/chlimage_1-86.png)

Il testo nell’immagine cambia. Per ripristinare il testo al valore originale, fai clic su **[!UICONTROL Ripristina]** accanto al campo.

![chlimage_1-87](assets/chlimage_1-87.png)

#### Modifica del testo in base a un valore personalizzato ClientContext {#changing-text-to-reflect-the-value-of-a-client-context-value}

Per collegare un campo a un valore di contesto client, fare clic su **[!UICONTROL Seleziona]** per aprire il menu di scelta rapida del client, selezionare il contesto client e fare clic su **[!UICONTROL OK]**. In questo esempio, il nome cambia perché è collegato al nome formattato nel profilo.

![chlimage_1-88](assets/chlimage_1-88.png)

Il testo si aggiorna con il nome dell’utente attualmente connesso. Per ripristinare il testo al valore originale, fai clic su **[!UICONTROL Ripristina]** accanto al campo.

![chlimage_1-89](assets/chlimage_1-89.png)

#### Come rendere il modello di immagine Dynamic Media Classic un collegamento {#making-the-scene-image-template-a-link}

**Per rendere il modello di immagine Dynamic Media Classic un collegamento**:

1. Sulla pagina con il componente Modello immagine di Dynamic Media Classic, fate clic su **[!UICONTROL Modifica]**.
1. Nel campo **[!UICONTROL URL]**, immetti l’URL a cui gli utenti verranno indirizzati quando fanno clic sull’immagine. Nel campo **[!UICONTROL Apri in]**, selezionare se si desidera aprire la destinazione (una nuova finestra o una stessa finestra).

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Fai clic su **[!UICONTROL OK]**.

### Componente video  {#video-component}

Il componente Dynamic Media Classic **[!UICONTROL Video]** (disponibile dalla sezione Dynamic Media Classic della barra laterale) utilizza il rilevamento della periferica e della larghezza di banda per distribuire il video corretto a ogni schermo. Questo componente è un lettore video HTML5; è un singolo visualizzatore che può essere usato su più canali.

Può essere usato per set video adattivi, un singolo video MP4 o un singolo video F4V.

Per ulteriori informazioni sul funzionamento dei video con l&#39;integrazione con Dynamic Media Classic, consultate [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md). Inoltre, il componente [Dynamic Media Classic video **viene confrontato con il componente** video **di base ](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).**

![chlimage_1-91](assets/chlimage_1-91.png)

### Limitazioni note per il componente video {#known-limitations-for-the-video-component}

Adobe DAM e WCM mostrano se è stato caricato un video principale. Non mostrano queste risorse proxy:

* Rappresentazioni codificate di Dynamic Media Classic
* Set video adattivi Dynamic Media Classic

Quando usate un set video adattivo con il componente video Dynamic Media Classic, dovete ridimensionare il componente per adattarlo alle dimensioni del video.

## Browser contenuti Dynamic Media Classic {#scene-content-browser}

Il browser Dynamic Media Classic consente di visualizzare i contenuti di Dynamic Media Classic direttamente in AEM. Per accedere al browser dei contenuti, in Content Finder selezionate **[!UICONTROL Dynamic Media Classic]** nell&#39;interfaccia utente ottimizzata per il tocco o l&#39;icona **[!UICONTROL S7]** nell&#39;interfaccia utente classica. La funzionalità è identica nelle due interfacce utente.

Se si dispone di più configurazioni, per impostazione predefinita AEM visualizza la [configurazione predefinita](/help/sites-administering/scene7.md#configuring-a-default-configuration). Puoi selezionare diverse configurazioni direttamente nel browser del contenuto di Dynamic Media Classic nel menu a discesa.

>[!NOTE]
>
>* Le risorse che si trovano nella cartella ad hoc non vengono visualizzate nel browser del contenuto di Dynamic Media Classic.
>* Quando [Anteprima protetta è abilitata](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), le risorse pubblicate e non pubblicate in Dynamic Media Classic vengono visualizzate nel browser dei contenuti di Dynamic Media Classic.
>* Se non visualizzate l&#39;icona **[!UICONTROL Dynamic Media Classic]** o **[!UICONTROL S7]** come opzione nel browser del contenuto, è necessario [configurare Dynamic Media Classic per lavorare con AEM](/help/sites-administering/scene7.md).

   >
   >
* Per i video, il browser del contenuto Dynamic Media Classic supporta:
   >
   >
* Set di video adattivo: contenitore di tutte le rappresentazioni video necessarie per consentirne la riproduzione su diversi tipi di schermi
>* Video MP4 singolo
>* Video F4V singolo


### Navigazione dei contenuti nell’interfaccia classica {#browsing-content-in-the-classic-ui}

Sfogliate il contenuto in Dynamic Media Classic facendo clic sulla scheda **[!UICONTROL S7]**.

Per modificare la configurazione a cui accedete, selezionate la configurazione. Le cartelle cambiano a seconda della configurazione selezionata.

![chlimage_1-92](assets/chlimage_1-92.png)

Come per il Content Finder di Assets, è possibile cercare le risorse e filtrare i risultati. Tuttavia, a differenza del finder di Assets, quando si immette una parola chiave nella scheda **[!UICONTROL S7]**, il nome del file *inizia con* la stringa immessa, anziché *contenere* la parola chiave nel nome del file.

Per impostazione predefinita, le risorse vengono visualizzate per nome di file. È anche possibile filtrare i risultati per tipo di risorsa.

>[!NOTE]
>
>Per i video, il browser di contenuti Dynamic Media Classic di WCM supporta:
>
>* Set di video adattivo: contenitore di tutte le rappresentazioni video necessarie per consentirne la riproduzione su diversi tipi di schermi
>* Video MP4 singolo
>* Video F4V singolo

>



### Ricerca di risorse Dynamic Media Classic con il browser dei contenuti {#searching-for-scene-assets-with-the-content-browser}

La ricerca di risorse Dynamic Media Classic è simile alla ricerca AEM risorse, ma quando effettuate una ricerca viene visualizzata una visualizzazione remota delle risorse nel sistema Dynamic Media Classic, anziché importarle direttamente in AEM.

Per visualizzare e cercare le risorse è possibile utilizzare l’interfaccia touch o classica. A seconda dell’interfaccia, la modalità di ricerca è leggermente diversa.

Durante la ricerca in una qualsiasi delle interfacce utente, è possibile filtrare in base ai seguenti criteri (mostrati qui nell’interfaccia touch):

**[!UICONTROL Inserite le parole chiave]** : potete cercare le risorse per nome. Durante la ricerca, immetti le parole chiave con cui inizia il nome del file. Ad esempio, se digiti la parola “nuoto” verranno cercati i nomi dei file delle risorse che iniziano con queste lettere, in questo ordine. Assicurati di fare clic su Invia dopo aver digitato il termine per trovare la risorsa.

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL Cartella/percorso]** : il nome della cartella visualizzata si basa sulla configurazione selezionata. Per passare alle cartelle di livello inferiore, fai clic sull’icona della cartella e seleziona una sottocartella, quindi fai clic sul segno di spunta per selezionarla.

Se si immette una parola chiave e si seleziona una cartella, AEM esegue la ricerca in tale cartella e in tutte le relative sottocartelle. Tuttavia, se non si immettono parole chiave durante la ricerca, la selezione della cartella mostrerà solo le risorse in quella cartella, senza includere le sottocartelle.

Per impostazione predefinita, AEM cerca nella cartella selezionata e in tutte le sue sottocartelle.

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL Tipo di]** risorsa: selezionate Dynamic Media Classic per sfogliare il contenuto di Dynamic Media Classic. Questa opzione è disponibile solo se avete già configurato Dynamic Media Classic.

![chlimage_1-95](assets/chlimage_1-95.png)

**** Configurazione: se hai più di una configurazione Dynamic Media Classic definita in  [!UICONTROL Cloud Services], puoi selezionarla qui. Di conseguenza, la cartella cambierà in base alla configurazione scelta.

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL Tipo]** di risorsaNel browser Dynamic Media Classic potete filtrare i risultati in modo da includere i seguenti elementi: immagini, modelli, video e set video adattivi. Se non si seleziona alcun tipo di risorsa, per impostazione predefinita AEM ricerca tutti i tipi di risorsa.

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* Durante la ricerca di video, si cerca una singola rappresentazione. I risultati restituiscono la rappresentazione originale (solo &amp;ast;.mp4) e la rappresentazione codificata.
>* Quando eseguite una ricerca in un set video adattivo, state cercando la cartella e tutte le sottocartelle, ma solo se avete aggiunto una parola chiave alla ricerca. Se non hai aggiunto una parola chiave, AEM non cerca nelle sottocartelle.

>



**[!UICONTROL Pubblica]** statoPotete filtrare le risorse in base allo stato di pubblicazione:   Pubblicato o  [!UICONTROL Non pubblicato]. Se non selezionate [!UICONTROL Stato pubblicazione], per impostazione predefinita AEM esegue la ricerca in tutti gli stati di pubblicazione.

![chlimage_1-98](assets/chlimage_1-98.png)

