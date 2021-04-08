---
title: Immagini panoramiche
Description: Learn how to work with panoramic images in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Immagini panoramiche
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 4%

---

# Immagini panoramiche {#panoramic-images}

Questa sezione descrive come utilizzare il visualizzatore di immagini panoramiche per riprodurre immagini panoramiche sferiche per un’esperienza di visualizzazione a 360° di una stanza, una proprietà, una posizione o un paesaggio.

Consulta anche [Gestione dei predefiniti per visualizzatori](managing-viewer-presets.md).

![panoramico-immagine2](assets/panoramic-image2.png)

## Caricamento delle risorse da utilizzare con il visualizzatore di immagini panoramiche {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Affinché una risorsa caricata possa qualificarsi come immagine panoramica sferica che intendi utilizzare con il visualizzatore di immagini panoramiche, la risorsa deve avere uno o entrambi i seguenti elementi:

* Rapporto di formato 2.

   È possibile ignorare l&#39;impostazione predefinita delle proporzioni di 2 in **[!UICONTROL CRXDE Lite]** nel seguente percorso:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Tag con le parole chiave `equirectangular`, `spherical`e `panorama`, o `spherical` e `panoramic`. Consulta [Uso dei tag](/help/sites-authoring/tags.md).

Sia le proporzioni che i criteri delle parole chiave si applicano alle risorse panoramiche della pagina dettagli risorsa e al componente per **[!UICONTROL elementi multimediali panoramici]**.

Per caricare le risorse da utilizzare con il visualizzatore di immagini panoramiche, consulta [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets).

## Configurazione di Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Affinché il visualizzatore di immagini panoramiche funzioni correttamente all’interno di AEM, è necessario sincronizzare i predefiniti visualizzatore di immagini panoramiche con i metadati specifici di Dynamic Media Classic e Dynamic Media Classic in modo che i predefiniti visualizzatore vengano aggiornati nel JCR. A questo scopo, configura Dynamic Media Classic nel modo seguente:

1. [Accedi all’](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) applicazione desktop Dynamic Media Classic per ogni account aziendale.

1. Nell’angolo in alto a destra della pagina, fai clic su **[!UICONTROL Configurazione > Impostazione applicazione > Configurazione pubblicazione > Image Server]**.
1. Nella pagina **[!UICONTROL Pubblicazione server immagini]**, dal menu a discesa **[!UICONTROL Contesto pubblicazione]** vicino alla parte superiore, seleziona **[!UICONTROL Image Serving]**.

1. Nella stessa pagina **[!UICONTROL Pubblicazione su Image Server]**, individua l&#39;intestazione **[!UICONTROL Richiedi attributi]**.
1. Sotto l&#39;intestazione **[!UICONTROL Richiedi attributi]**, individua **[!UICONTROL Limite dimensione immagine di risposta]**. Quindi, nei campi **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]** associati, aumenta la dimensione massima dell&#39;immagine consentita per le immagini panoramiche.

   Dynamic Media Classic ha un limite di 25.000.000 pixel. Le dimensioni massime consentite per le immagini con un rapporto di formato 2:1 sono 7000 x 3500. Tuttavia, per gli schermi desktop tipici, sono sufficienti 4096 x 2048 pixel.

   >[!NOTE]
   >
   >Sono supportate solo le immagini che rientrano nella dimensione massima consentita. Le richieste di immagini che superano il limite di dimensione si tradurranno in una risposta 403.

1. Sotto l&#39;intestazione **[Richiedi attributi]** , procedi come segue:

   * Impostare **[!UICONTROL Modalità offuscamento richieste]** su **[!UICONTROL Disabilitato]**.
   * Impostare **[!UICONTROL Modalità blocco richieste]** su **[!UICONTROL Disabilitato]**.

   Queste impostazioni sono necessarie per utilizzare il componente **[!UICONTROL Elemento multimediale panoramico]** in AEM.

1. Nella parte inferiore della pagina **[!UICONTROL Pubblicazione server immagini]**, a sinistra, tocca **[!UICONTROL Salva]**.

1. Nell’angolo in basso a destra, tocca **[!UICONTROL Chiudi]**.

### Risoluzione dei problemi relativi al componente Elemento multimediale panoramico {#troubleshooting-the-panoramic-media-wcm-component}

Se hai rilasciato un&#39;immagine nel componente **[!UICONTROL Elemento multimediale panoramico]** in WCM e il segnaposto del componente è stato compresso, puoi risolvere i seguenti problemi:

* Se si verifica un errore 403 Vietato, potrebbe essere dovuto al fatto che la dimensione dell&#39;immagine richiesta è troppo grande. Rivedi le impostazioni *Limite dimensione immagine di risposta* in [Configurazione di Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* Per un *Blocco non valido* sulla risorsa o *Errore di parsing* visualizzato sulla pagina, controlla **[!UICONTROL Modalità offuscamento richieste]** e **[!UICONTROL Modalità blocco richieste]** per assicurarti che siano disattivate.
* Per un errore di tela colorata, imposta un **[!UICONTROL percorso del file di definizione del set di regole e invalida CTN]** per le richieste precedenti per la risorsa immagine.
* Se la qualità dell&#39;immagine diventa molto bassa dopo una richiesta di immagine con dimensioni superiori al limite supportato, controlla che l&#39;impostazione **[!UICONTROL Attributi di codifica JPEG > Qualità]** non sia vuota. Un&#39;impostazione tipica per il campo **[!UICONTROL Quality]** è `95`. Puoi trovare l’impostazione nella pagina **[!UICONTROL Pubblicazione server immagini]** . Per accedere alla pagina, consulta [Configurazione di Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Anteprima delle immagini panoramiche {#previewing-panoramic-images}

Consulta [Anteprima delle risorse](previewing-assets.md).

## Pubblicazione di immagini panoramiche {#publishing-panoramic-images}

Consulta [Pubblicazione di risorse](publishing-dynamicmedia-assets.md).
