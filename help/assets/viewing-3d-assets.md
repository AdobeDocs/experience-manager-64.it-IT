---
title: Visualizzazione di risorse 3D
description: Scopri il visualizzatore 3D interattivo disponibile nella pagina dei dettagli delle risorse in AEM e come usarlo per visualizzare le risorse 3D.
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
exl-id: 71f89564-a413-49f6-8d6e-c5305bf92c75
feature: Risorse 3D
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '1780'
ht-degree: 32%

---

# Visualizzazione di risorse 3D {#viewing-d-assets}

>[!IMPORTANT]
>
>AEM 3D in AEM 6.4 non è più supportato. Adobe consiglia di utilizzare la funzione risorse 3D in [AEM come Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) o [AEM 6.5.3 o superiore.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) per visualizzare le risorse 3D.

Questo documento descrive sia come visualizzare le risorse 3D nei dettagli delle risorse sia come visualizzare le risorse presenti nel componente 3D nei siti.

## Visualizzazione delle risorse 3D nella pagina Dettagli risorsa {#viewing-d-assets-in-the-asset-details-page}

Il visualizzatore 3D interattivo è disponibile dalla pagina dei dettagli delle risorse in AEM. Il visualizzatore include, tra le altre, una raccolta di controlli interattivi della videocamera che consentono di eseguire zoom, rotazione e scorrimento della risorsa 3D.

![chlimage_1-139](assets/chlimage_1-139.png)

Oltre a usare le aree di visualizzazione 3D predefinite in AEM, puoi anche utilizzare i livelli creati in un’applicazione di terze parti e caricati in AEM.

Vedi [Utilizzo delle aree di visualizzazione in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

>[!NOTE]
>
>Per visualizzare una risorsa 3D, il browser desktop o del dispositivo deve essere abilitato per WebGL. Inoltre, l&#39;hardware grafico sottostante deve disporre di capacità e memoria sufficienti per eseguire il rendering dei modelli delle dimensioni e della complessità desiderate. Alcune funzioni di anteprima, come l’ombreggiatura del cast, non sono disponibili su tutti i browser.

### Considerazioni sulle prestazioni per la visualizzazione di risorse 3D {#performance-considerations-when-you-view-d-assets}

Il tempo necessario per aprire una risorsa 3D nella pagina Dettagli risorsa dipende da vari fattori, quali:

* Larghezza di banda e latenze al server.
* Dimensione del modello (numero di facce).
* Quantità e dimensione delle mappe.
* Complessità delle aree di visualizzazione. Ad esempio, la dimensione dell’immagine IBL.

Inoltre, le funzionalità del computer client, come una workstation, un notebook o un dispositivo touch mobile, sono importanti anche quando si manipola la fotocamera in modo interattivo. Un sistema ragionevolmente potente con buone capacità grafiche può rendere l’esperienza di visualizzazione 3D interattiva più fluida e favorevole.

**Per visualizzare le risorse 3D**:

1. Assicurati di aver caricato le risorse 3D in AEM.

   Vedi [Caricamento ed elaborazione di risorse 3D in AEM](upload-processing-3d-assets.md).

1. Da AEM, nella pagina **[!UICONTROL Navigazione]**, tocca **[!UICONTROL Risorse]**.
1. Dall’elenco a discesa **[!UICONTROL Visualizza]** nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Vista a schede]**.
1. Accedi alla risorsa 3D da visualizzare.
1. Tocca la scheda della risorsa 3D per aprirla nella pagina dei dettagli della risorsa.
1. Effettua una delle operazioni seguenti:

   * Nell’angolo in basso a destra della pagina dei dettagli delle risorse, utilizza la barra dei comandi della fotocamera per cambiare le varie viste delle risorse.

      Se utilizzi un dispositivo di input non touch senza rotella di scorrimento, ad esempio un classico mouse Apple con un solo pulsante, puoi comunque cambiare lo zoom o la prospettiva di una risorsa 3D in ciascuna modalità. Per eseguire l&#39;azione, premi il tasto `SHIFT`tenendo premuto il tasto mentre tieni premuto il pulsante del mouse e trascini verso l&#39;alto o verso il basso.

      Quando utilizzi il touchpad di un computer portatile, è spesso difficile controllare lo zoom o la prospettiva mediante il gesto con due dita. In questi casi, puoi tenere premuto `SHIFT`durante l’azione. Questo riduce la velocità del gesto di avvicinamento delle dita e rende più semplice ottenere lo zoom o la prospettiva desiderati. In alternativa, puoi utilizzare un dito per trascinare verso l’alto o verso il basso mentre si preme il tasto `SHIFT`per modificare i comportamenti di zoom o prospettiva.
   <table> 
    <tbody> 
      <tr> 
      <td><strong>Nome del controllo della telecamera</strong><br /> </td> 
      <td><strong>Descrizione</strong></td> 
      </tr> 
      <tr> 
      <td><p>Zoom</p> <p>o</p> <p>Persp</p> </td> 
      <td><p>Tocca o fai clic per passare dalla modalità Zoom alla modalità Prospettiva e viceversa.</p> <p>Oppure, tieni premuto il tasto <code>ALT/OPTION</code> durante l'azione per passare momentaneamente alla modalità Prospettiva<br />. Rilascia il tasto per tornare alla modalità Zoom.</p> 
      <ul> 
      <li><strong>Zoom</strong>: consente di avvicinare o allontanare la videocamera dalla <br /> risorsa visualizzata. Lo zoom è il comportamento predefinito per la rotellina di scorrimento del mouse (se disponibile), per i movimenti di allontanamento o avvicinamento con due dita sui dispositivi mobili, o quando tieni premuto il tasto Maiusc mentre muovi il mouse su o giù premendo il pulsante sinistro.</li> 
      <li><strong>Prospettiva</strong>: cambia la lunghezza focale (anche nota come campo visivo) della fotocamera mantenendo le dimensioni relative della risorsa nella visualizzazione. La prospettiva è il comportamento alternativo per la rotellina (se disponibile), per i movimenti di allontanamento o avvicinamento con due dita sui dispositivi mobili, o quando tieni premuto il tasto Maiusc mentre muovi il mouse su o giù premendo il pulsante sinistro.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Orbita</p> <p>o</p> <p>Pan</p> </td> 
      <td><p>Tocca o fai clic per passare dalla modalità Rotazione alla modalità Panning e viceversa.</p> <p>Oppure, tieni premuto il tasto <code>ALT/OPTION</code> durante l’azione per passare momentaneamente alla modalità Panning. Rilascia il tasto per tornare alla modalità Rotazione.</p> 
      <ul> 
      <li><strong>Rotazione</strong>: sposta la telecamera di visualizzazione su una sfera centrata su un punto di destinazione che si trova vicino al centro della risorsa 3D come impostazione predefinita. La rotazione è il funzionamento predefinito per il trascinamento con il pulsante sinistro o con un singolo tocco sui dispositivi mobili.</li> 
      <li><strong>Panning</strong>: sposta la telecamera nel piano di visualizzazione. L’obiettivo viene spostato di conseguenza, quindi le successive azioni di rotazione sposteranno la videocamera intorno a un nuovo obiettivo. Il panning è il funzionamento predefinito per il trascinamento con il pulsante sinistro o con un singolo tocco.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Esamina</p> <p>o</p> <p>Target</p> </td> 
      <td><p>Tocca o fai clic per passare dalla modalità Esamina alla modalità Target e viceversa.</p> 
      <ul> 
      <li><strong>Esamina</strong>: tocca o fai clic per accedere alla modalità di Target.</li> 
      <li><strong>Target</strong>: tocca o fai clic su un punto qualsiasi della risorsa 3D per centrare la visualizzazione su quella parte della risorsa.<br /> Le azioni Rotazione utilizzano il nuovo obiettivo.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>Ripristina</td> 
      <td>Toccate o fate clic per ripristinare il punto di destinazione della vista al centro del modello. Ripristina inoltre sposta la telecamera<br /> più vicino o lontano per mostrare la risorsa nella sua interezza e a una dimensione di visualizzazione ragionevole.</td> 
      </tr> 
    </tbody> 
    </table>

   * Nell’angolo in alto a destra della pagina dei dettagli della risorsa, tocca l’icona **[!UICONTROL Selettore fase]** . Seleziona il nome di un’area di visualizzazione con lo sfondo e l’illuminazione che desideri applicare alla risorsa 3D.

   ![chlimage_1-140](assets/chlimage_1-140.png)

   Le aree di visualizzazione forniscono l&#39;ambiente-sfondo, il piano terreno e l&#39;illuminazione in cui viene visualizzato il modello 3D.

   Vedi [Utilizzo delle aree di visualizzazione in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   * Nell’angolo in alto a destra della pagina dei dettagli della risorsa, tocca l’icona **[!UICONTROL Selettore fotocamera]** , quindi seleziona la vista della fotocamera da applicare alla risorsa 3D.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   Le aree di visualizzazione spesso forniscono videocamere predefinite. Puoi selezionare di nuovo la videocamera corrente per tornare alle impostazioni predefinite.

   Vedi [Utilizzo delle aree di visualizzazione in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. Nell’angolo in alto a destro della pagina, tocca **[!UICONTROL Salva]**.
1. Effettua una delle operazioni seguenti:

   * Esegui il rendering della risorsa 3D.

      Vedi [Rendering delle risorse 3D](rendering-3d-assets.md).

   * Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Chiudi]** per tornare alla schermata Risorse.

## Visualizzazione delle risorse 3D nel componente 3D di Sites {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>Questa sezione si applica solo al visualizzatore webGL classico utilizzato per i tipi di risorse 3D diversi da Adobe Dimension.

A seconda del tipo di dispositivo, è possibile accedere alle funzioni del componente 3D in diversi modi.

Per ulteriori informazioni, consulta gli argomenti di seguito:

* [Dispositivi touchscreen](#touchscreen-devices)
* [Dispositivi touchpad](#touchpad-devices)
* [Dispositivi mouse e trackball](#mouse-and-trackball-devices)

Consulta anche [Anteprima di una pagina web con un componente 3D](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component).

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### Dispositivi touchscreen {#touchscreen-devices}

Per lavorare con componenti 3D con dispositivi touchscreen:

1. Per spostare (&quot;orbita&quot;) il punto di vista (&quot;fotocamera&quot;) attorno all’oggetto, trascinare o scorrere un dito solo. È possibile visualizzare l’oggetto da qualsiasi direzione.

1. Utilizzare un pizzico a due dita per avvicinare o allontanare la telecamera dall&#39;oggetto. Questa azione è simile allo zoom in/out e consente di controllare i dettagli dell’oggetto. In alternativa, tenere premuto il tasto + o - per avvicinare o allontanare la telecamera dall&#39;oggetto.

1. Usare un trascinamento con due dita per eseguire il panning della telecamera. Questa azione sposta la fotocamera lateralmente per consentire di guardare diverse parti dell&#39;oggetto durante lo zoom in. In alternativa, toccare il pulsante **[!UICONTROL Attiva/Disattiva rotazione/Rotazione]** per passare alla modalità Panning, quindi utilizzare un solo dito per trascinare la videocamera. Toccare il pulsante **[!UICONTROL Attiva/disattiva rotazione/rotazione]** per tornare alla modalità **[!UICONTROL Rotazione]**.

1. Toccare **[!UICONTROL Reset Viewer]** per ripristinare la fotocamera. Questa azione riporta l’oggetto in visualizzazione completa e, se abilitata, riprende l’esecuzione automatica dell’spin.

1. Toccare **[!UICONTROL Schermo intero]** per accedere alla modalità a schermo intero (se supportata dal dispositivo). Toccare nuovamente **[!UICONTROL Schermo intero]** per ripristinare il visualizzatore 3D in modalità incorporata nella pagina.

### Dispositivi touchpad {#touchpad-devices}

Per lavorare con componenti 3D con dispositivi touchpad:

1. Trascinare con un dito mentre si tiene premuto il pulsante (a sinistra) del touchpad verso il basso per spostare (&quot;orbita&quot;) il punto di vista (&quot;fotocamera&quot;) intorno all’oggetto. È possibile visualizzare l’oggetto da qualsiasi direzione.

1. Utilizzare un trascinamento verso il basso o verso l&#39;alto con i tasti del touchpad verso l&#39;alto per avvicinare o allontanare la telecamera dall&#39;oggetto. Questa azione è simile allo zoom in/out e consente di controllare i dettagli dell’oggetto. In alternativa, tenere premuto il tasto **[!UICONTROL Zoom in]** o **[!UICONTROL Zoom out]** per avvicinare o allontanare la videocamera dall&#39;oggetto.

1. Trascinare con un solo dito tenendo premuto il tasto **ALT/option** e il tasto (a sinistra) del touchpad per scorrere la fotocamera. Questa azione sposta la fotocamera lateralmente per consentire di guardare diverse parti dell&#39;oggetto durante lo zoom in. In alternativa, fare clic sul pulsante **[!UICONTROL Attiva/Disattiva rotazione orbitale]** per passare alla modalità **[!UICONTROL Panning]**, quindi trascinare un solo dito tenendo premuto il pulsante (a sinistra) per scorrere la fotocamera. Fai nuovamente clic sul pulsante **[!UICONTROL Attiva/disattiva rotazione/rotazione]** per tornare alla modalità **[!UICONTROL Rotazione]**.

1. Fare clic su **[!UICONTROL Reset Viewer]** per ripristinare la fotocamera. Questa azione riporta l’oggetto in visualizzazione completa e, se abilitata, riprende l’esecuzione automatica dell’spin.

1. Fare clic su **[!UICONTROL Schermo intero]** per accedere alla modalità a tutto schermo. Usa nuovamente il tasto **Esc** sulla tastiera oppure fai clic su **[!UICONTROL Schermo intero]** per ripristinare il visualizzatore 3D in modalità incorporata nella pagina.

### Dispositivi mouse e trackball {#mouse-and-trackball-devices}

Per lavorare con componenti 3D con mouse e dispositivi trackball:

1. Trascinare tenendo premuto il pulsante sinistro del mouse verso il basso per spostare (&quot;orbita&quot;) il punto di vista (&quot;fotocamera&quot;) intorno all&#39;oggetto. È possibile visualizzare l’oggetto da qualsiasi direzione.

1. Utilizzare la rotellina di scorrimento per avvicinare o allontanare la fotocamera dall&#39;oggetto. Simile allo zoom in/out e consente di controllare i dettagli dell’oggetto. In alternativa, tenere premuto il tasto **[!UICONTROL Zoom in]** o **[!UICONTROL Zoom out]** per avvicinare o allontanare la videocamera dall&#39;oggetto.

1. Trascinare tenendo premuto il tasto **ALT/option** e il pulsante sinistro del mouse per scorrere la fotocamera. In questo modo la videocamera si sposta lateralmente per consentire di osservare diverse parti dell&#39;oggetto durante lo zoom in. In alternativa, fare clic sul pulsante **[!UICONTROL Attiva/disattiva rotazione/rotazione]** per passare alla modalità **[!UICONTROL Panning]**, quindi trascinare tenendo premuto il pulsante sinistro del mouse per scorrere la fotocamera. Fai di nuovo clic su **[!UICONTROL Attiva/disattiva rotazione/rotazione]** per tornare alla modalità **[!UICONTROL Rotazione]**.
1. Fare clic su **[!UICONTROL Reset Viewer]** per ripristinare la fotocamera. Questa azione riporta l’oggetto in visualizzazione completa e, se abilitata, riprende l’esecuzione automatica dell’spin.
1. Fare clic su **[!UICONTROL Schermo intero]** per accedere alla modalità a tutto schermo. Usa nuovamente il tasto **[!UICONTROL Esc]** sulla tastiera oppure fai clic su **[!UICONTROL Schermo intero]** per ripristinare il visualizzatore 3D in modalità incorporata nella pagina.
