---
title: Visualizzazione di risorse 3D
description: Scoprite il visualizzatore 3D interattivo disponibile dalla pagina dei dettagli delle risorse in AEM e come usarlo per visualizzare le risorse 3D.
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
translation-type: tm+mt
source-git-commit: 6be46f6986d1631f711cfd4464cc4f2d17014681
workflow-type: tm+mt
source-wordcount: '1778'
ht-degree: 32%

---


# Visualizzazione di risorse 3D {#viewing-d-assets}

>[!IMPORTANT]
>
>AEM 3D in AEM 6.4 non è più supportato.  Adobe consiglia di utilizzare la funzione delle risorse 3D in [AEM come Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) o [AEM 6.5.3 o superiore.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) per visualizzare le risorse 3D.

Questo documento descrive sia come visualizzare le risorse 3D nei dettagli delle risorse, sia come visualizzare le risorse che si trovano nel componente 3D nei siti.

## Visualizzazione delle risorse 3D nella pagina Dettagli risorsa {#viewing-d-assets-in-the-asset-details-page}

Il visualizzatore 3D interattivo è disponibile dalla pagina dei dettagli delle risorse in AEM. Il visualizzatore include, tra le altre, una raccolta di controlli interattivi della videocamera che consentono di eseguire zoom, rotazione e scorrimento della risorsa 3D.

![chlimage_1-139](assets/chlimage_1-139.png)

Oltre a usare le aree di visualizzazione 3D predefinite in AEM, puoi anche utilizzare i livelli creati in un’applicazione di terze parti e caricati in AEM.

Vedi [Utilizzo delle aree di visualizzazione in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

>[!NOTE]
>
>Per visualizzare una risorsa 3D, il browser desktop o del dispositivo deve essere abilitato per WebGL. Inoltre, l&#39;hardware grafico sottostante deve disporre di capacità e memoria sufficienti per eseguire il rendering dei modelli delle dimensioni e della complessità desiderate. Alcune funzioni di anteprima, come l’ombra proiettata, non sono disponibili su tutti i browser.

### Considerazioni sulle prestazioni per la visualizzazione di risorse 3D {#performance-considerations-when-you-view-d-assets}

Il tempo necessario per aprire una risorsa 3D nella pagina Dettagli risorsa dipende da vari fattori, quali:

* Larghezza di banda e latenze al server.
* Dimensione del modello (numero di facce).
* Quantità e dimensione delle mappe.
* Complessità delle aree di visualizzazione. Ad esempio, la dimensione dell’immagine IBL.

Inoltre, le funzionalità del computer client, come una workstation, un notebook o un dispositivo mobile touch, sono importanti anche quando si modifica la telecamera in modo interattivo. Un sistema ragionevolmente potente con buone capacità grafiche può rendere l’esperienza di visualizzazione 3D interattiva più fluida e favorevole.

**Per visualizzare le risorse 3D**:

1. Assicurati di aver caricato le risorse 3D in AEM.

   Vedi [Caricamento ed elaborazione di risorse 3D in AEM](upload-processing-3d-assets.md).

1. Da AEM, nella pagina **[!UICONTROL Navigazione]**, toccare **[!UICONTROL Risorse]**.
1. Vicino all&#39;angolo superiore destro della pagina, dall&#39;elenco a discesa **[!UICONTROL View]**, toccare **[!UICONTROL Card View]**.
1. Accedi alla risorsa 3D da visualizzare.
1. Tocca la scheda della risorsa 3D per aprirla nella pagina dei dettagli della risorsa.
1. Effettua una delle operazioni seguenti:

   * Nell’angolo in basso a destra della pagina dei dettagli delle risorse, utilizza la barra dei comandi della fotocamera per cambiare le varie viste delle risorse.

      Se utilizzi un dispositivo di input non touch senza rotella di scorrimento, ad esempio un classico mouse Apple con un solo pulsante, puoi comunque cambiare lo zoom o la prospettiva di una risorsa 3D in ciascuna modalità. Per eseguire l&#39;azione, premere e tenere premuto il tasto `SHIFT`mentre si deprime il pulsante del mouse e si trascina verso l&#39;alto o il basso.

      Quando utilizzi il touchpad di un computer portatile, è spesso difficile controllare lo zoom o la prospettiva mediante il gesto con due dita. In questi casi, è possibile premere e tenere premuto `SHIFT`durante l&#39;azione. Questo riduce la velocità del gesto di avvicinamento delle dita e rende più semplice ottenere lo zoom o la prospettiva desiderati. In alternativa, è possibile trascinare un dito verso l&#39;alto o il basso mentre il tasto `SHIFT`viene premuto per influenzare i comportamenti di zoom o prospettiva.
   <table> 
    <tbody> 
      <tr> 
      <td><strong>Nome controllo telecamera</strong><br /> </td> 
      <td><strong>Descrizione</strong></td> 
      </tr> 
      <tr> 
      <td><p>Zoom</p> <p>o</p> <p>Persp</p> </td> 
      <td><p>Toccate o fate clic per alternare tra le modalità Zoom e Prospettiva.</p> <p>In alternativa, tenere premuto il tasto <code>ALT/OPTION</code> durante l'azione per passare temporaneamente alla modalità Prospettiva<br />. Rilascia il tasto per tornare alla modalità Zoom.</p> 
      <ul> 
      <li><strong>Comportamento Zoom</strong>-Dolly in e out, che avvicina o allontana la telecamera dalla <br /> risorsa visualizzata. Lo zoom è il comportamento predefinito per la rotellina di scorrimento del mouse (se disponibile), per i movimenti di allontanamento o avvicinamento con due dita sui dispositivi mobili, o quando tieni premuto il tasto Maiusc mentre muovi il mouse su o giù premendo il pulsante sinistro.</li> 
      <li><strong>Prospettiva</strong>: modifica la lunghezza focale (o campo visivo) della fotocamera, mantenendo le dimensioni relative della risorsa nella vista. La prospettiva è il comportamento alternativo per la rotellina (se disponibile), per i movimenti di allontanamento o avvicinamento con due dita sui dispositivi mobili, o quando tieni premuto il tasto Maiusc mentre muovi il mouse su o giù premendo il pulsante sinistro.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Orbita</p> <p>o</p> <p>Pan</p> </td> 
      <td><p>Toccate o fate clic per alternare tra le modalità Orbit e Panning.</p> <p>Oppure, tenete premuto il tasto <code>ALT/OPTION</code> durante l'azione per passare temporaneamente alla modalità Scorrimento. Rilascia il tasto per tornare alla modalità Rotazione.</p> 
      <ul> 
      <li><strong>Orbita</strong> - Per impostazione predefinita, sposta la telecamera di visualizzazione su una sfera centrata su un punto di destinazione vicino al centro della risorsa 3D. La rotazione è il funzionamento predefinito per il trascinamento con il pulsante sinistro o con un singolo tocco sui dispositivi mobili.</li> 
      <li><strong>Pan</strong>-Sposta la telecamera nel piano di visualizzazione. L’obiettivo viene spostato di conseguenza, quindi le successive azioni di rotazione sposteranno la videocamera intorno a un nuovo obiettivo. Il panning è il funzionamento predefinito per il trascinamento con il pulsante sinistro o con un singolo tocco.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Esaminare</p> <p>o</p> <p>Destinazione</p> </td> 
      <td><p>Toccate o fate clic per alternare tra le modalità Examine e Target.</p> 
      <ul> 
      <li><strong>Toccate o fate</strong> clic per passare alla modalità Target.</li> 
      <li><strong>Toccate</strong> o fate clic su un punto qualsiasi della risorsa 3D per centrare la visualizzazione sulla parte della risorsa.<br /> Le azioni Rotazione utilizzano il nuovo obiettivo.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>Ripristina</td> 
      <td>Toccate o fate clic per ripristinare il punto di destinazione della vista al centro del modello. Il ripristino consente inoltre di spostare la telecamera<br /> più vicino o più lontano per mostrare la risorsa nella sua interezza e con dimensioni di visualizzazione ragionevoli.</td> 
      </tr> 
    </tbody> 
    </table>

   * Vicino all&#39;angolo superiore destro della pagina dei dettagli della risorsa, toccate l&#39;icona **[!UICONTROL Selettore fase]**. Seleziona il nome di un’area di visualizzazione con lo sfondo e l’illuminazione che desideri applicare alla risorsa 3D.

   ![chlimage_1-140](assets/chlimage_1-140.png)

   Le fasi forniscono l&#39;ambiente-sfondo, il piano terra e l&#39;illuminazione in cui viene visualizzato il modello 3D.

   Vedi [Utilizzo delle aree di visualizzazione in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   * Nell&#39;angolo superiore destro della pagina dei dettagli della risorsa, toccate l&#39;icona **[!UICONTROL Selettore fotocamera]**, quindi selezionate una vista fotocamera da applicare alla risorsa 3D.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   Le aree di visualizzazione spesso forniscono videocamere predefinite. Puoi selezionare di nuovo la videocamera corrente per tornare alle impostazioni predefinite.

   Vedi [Utilizzo delle aree di visualizzazione in AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. Nell’angolo in alto a destro della pagina, tocca **[!UICONTROL Salva]**.
1. Effettua una delle operazioni seguenti:

   * Esegui il rendering della risorsa 3D.

      Vedi [Rendering delle risorse 3D](rendering-3d-assets.md).

   * Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Chiudi]** per tornare alla schermata Risorse.

## Visualizzazione delle risorse 3D nel componente Siti 3D {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>Questa sezione è valida solo per il visualizzatore WebGL classico utilizzato per tipi di risorse 3D diversi da  Adobe Dimension.

A seconda del tipo di dispositivo, è possibile accedere alle funzioni dei componenti 3D in diversi modi.

Per ulteriori informazioni, consulta gli argomenti di seguito:

* [Dispositivi touch screen](#touchscreen-devices)
* [Dispositivi touch](#touchpad-devices)
* [Dispositivi per mouse e trackball](#mouse-and-trackball-devices)

Vedere anche [Anteprima di una pagina Web con un componente 3D](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component).

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### Dispositivi touch screen {#touchscreen-devices}

Per lavorare con componenti 3D con dispositivi touch screen:

1. Per spostare (&quot;orbita&quot;) il punto di vista (&quot;fotocamera&quot;) attorno all’oggetto, trascinate un solo dito o passate il dito. È possibile visualizzare l&#39;oggetto da qualsiasi direzione.

1. Usate un gesto di due dita per avvicinare o allontanare la telecamera dall&#39;oggetto. Questa azione è simile allo zoom avanti e indietro e consente di esaminare i dettagli sull&#39;oggetto. In alternativa, tenere premuto il tasto + o - per avvicinare o allontanare la telecamera dall&#39;oggetto.

1. Per scorrere la videocamera, trascinate due dita. Questa azione consente di spostare la videocamera lateralmente per osservare diverse parti dell’oggetto durante lo zoom in. In alternativa, toccate il pulsante **[!UICONTROL Attiva/disattiva orbita/scorrimento]** per passare alla modalità Panning, quindi trascinate con un dito per scorrere la telecamera. Toccate il pulsante **[!UICONTROL Attiva/disattiva orbita/scorrimento]** per tornare alla modalità **[!UICONTROL Orbita]**.

1. Toccate **[!UICONTROL Reimposta visualizzatore]** per ripristinare la fotocamera. Questa azione reinserisce l’oggetto nella visualizzazione completa e, se attivata, riprende la rotazione automatica.

1. Toccate **[!UICONTROL Schermo intero]** per passare alla modalità a schermo intero (se supportata dal dispositivo). Toccate di nuovo **[!UICONTROL Schermo intero]** per ripristinare il visualizzatore 3D alla modalità incorporata nella pagina.

### Dispositivi Touchpad {#touchpad-devices}

Per lavorare con componenti 3D con dispositivi touchpad:

1. Per spostare (&quot;orbita&quot;) il punto di vista (&quot;fotocamera&quot;) attorno all’oggetto, trascinate un solo dito mentre tenete premuto il pulsante (a sinistra) del touchpad. È possibile visualizzare l&#39;oggetto da qualsiasi direzione.

1. Per spostare la videocamera in prossimità o in prossimità dell’oggetto, trascinare verso l’alto o verso il basso con due dita. Questa azione è simile allo zoom avanti o indietro e consente di esaminare i dettagli sull&#39;oggetto. In alternativa, fare clic e tenere premuto il tasto **[!UICONTROL Zoom in]** o **[!UICONTROL Zoom out]** per avvicinare o allontanare la fotocamera dall&#39;oggetto.

1. Per scorrere la videocamera, trascinate un solo dito tenendo premuto il tasto **ALT/option** e il tasto (a sinistra) del touchpad. Questa azione consente di spostare la videocamera lateralmente per osservare diverse parti dell’oggetto durante lo zoom in. In alternativa, fare clic sul pulsante **[!UICONTROL Attiva/disattiva orbita/scorrimento]** per passare alla modalità **[!UICONTROL Scorrimento]**, quindi trascinare un dito mentre si tiene premuto il pulsante (a sinistra) per scorrere la fotocamera. Fare di nuovo clic sul pulsante **[!UICONTROL Attiva/disattiva orbita/scorrimento]** per tornare alla modalità **[!UICONTROL Orbita]**.

1. Fare clic su **[!UICONTROL Reimposta visualizzatore]** per ripristinare la fotocamera. Questa azione reinserisce l’oggetto nella visualizzazione completa e, se attivata, riprende la rotazione automatica.

1. Fare clic su **[!UICONTROL Schermo intero]** per passare alla modalità a schermo intero. Utilizzate il tasto **Escape** sulla tastiera oppure fate di nuovo clic su **[!UICONTROL Schermo intero]** per ripristinare il visualizzatore 3D alla modalità incorporata nella pagina.

### Dispositivi mouse e trackball {#mouse-and-trackball-devices}

Per lavorare con componenti 3D con mouse e dispositivi trackball:

1. Trascinare tenendo premuto il pulsante sinistro del mouse per spostare (&quot;orbita&quot;) il punto di vista (&quot;fotocamera&quot;) intorno all&#39;oggetto. È possibile visualizzare l&#39;oggetto da qualsiasi direzione.

1. Utilizzare la rotellina di scorrimento per avvicinare o allontanare la fotocamera dall&#39;oggetto. Simile allo zoom in o zoom out, che consente di esaminare i dettagli dell’oggetto. In alternativa, fare clic e tenere premuto il tasto **[!UICONTROL Zoom in]** o **[!UICONTROL Zoom out]** per avvicinare o allontanare la fotocamera dall&#39;oggetto.

1. Trascinare tenendo premuto il tasto **ALT/option** e il pulsante sinistro del mouse per scorrere la fotocamera. In questo modo la videocamera si sposta lateralmente per consentire di osservare diverse parti dell&#39;oggetto durante lo zoom avanti. In alternativa, fare clic sul pulsante **[!UICONTROL Attiva/disattiva orbita/scorrimento]** per passare alla modalità **[!UICONTROL Pan]**, quindi trascinare tenendo premuto il pulsante sinistro del mouse per scorrere la fotocamera. Fare di nuovo clic sul pulsante **[!UICONTROL Attiva/disattiva orbita/scorrimento]** per tornare alla modalità **[!UICONTROL Orbita]**.
1. Fare clic su **[!UICONTROL Reimposta visualizzatore]** per ripristinare la fotocamera. Questa azione reinserisce l’oggetto nella visualizzazione completa e, se attivata, riprende la rotazione automatica.
1. Fare clic su **[!UICONTROL Schermo intero]** per passare alla modalità a schermo intero. Utilizzate il tasto **[!UICONTROL Escape]** sulla tastiera oppure fate di nuovo clic su **[!UICONTROL Schermo intero]** per ripristinare il visualizzatore 3D alla modalità incorporata nella pagina.

