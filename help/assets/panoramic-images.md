---
title: Immagini panoramiche
seo-title: Immagini panoramiche
description: Scopri come lavorare con immagini panoramiche in Dynamic Media.
seo-description: Scopri come lavorare con immagini panoramiche in Dynamic Media.
uuid: dfd7a55c-7bcc-4d62-8c3a-a73726881103
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: fc285b25-2bce-493c-87bc-5f1a8a26eb42
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 4%

---


# Immagini panoramiche {#panoramic-images}

Questa sezione descrive come utilizzare il visualizzatore immagini panoramiche per riprodurre immagini panoramiche sferiche per un’esperienza di visualizzazione a 360° di una stanza, una proprietà, una posizione o un paesaggio.

See also [Managing Viewer Presets](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Caricamento delle risorse da usare con il visualizzatore immagini panoramiche {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Affinché una risorsa caricata possa essere considerata un’immagine panoramica sferica che intendete usare con il visualizzatore immagini panoramiche, la risorsa deve contenere una o entrambe le opzioni seguenti:

* Proporzioni di 2.

   Potete ignorare l’impostazione predefinita delle proporzioni di 2 in **[!UICONTROL CRXDE Lite]** nel modo seguente:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Sono stati assegnati tag con le parole chiave `equirectangular`, oppure `spherical`e `panorama`, `spherical` e `panoramic`. Consultate [Utilizzo dei tag](/help/sites-authoring/tags.md).

Sia le proporzioni che i criteri delle parole chiave si applicano alle risorse panoramiche della pagina dettagli risorsa e al componente per **[!UICONTROL elementi multimediali panoramici]**.

Per caricare le risorse da usare con il visualizzatore immagini panoramiche, consultate [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets).

## Configurazione di Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Affinché il visualizzatore di immagini panoramiche funzioni correttamente all’interno AEM, è necessario sincronizzare i predefiniti per visualizzatori di immagini panoramiche con i metadati specifici di Dynamic Media Classic e Dynamic Media Classic, in modo che i predefiniti per visualizzatori vengano aggiornati nel JCR. A questo scopo, configura Dynamic Media Classic nel modo seguente:

1. [Accedi alla tua istanza di Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) per ogni account della società.

1. Nell’angolo in alto a destra della pagina, fate clic su **[!UICONTROL Configurazione > Impostazione applicazione > Impostazione pubblicazione > Server]** immagini.
1. Nella pagina Pubblica **[!UICONTROL su]** Image Server, selezionate Server **[!UICONTROL immagini dal menu a discesa Contesto]** di **** pubblicazione accanto alla parte superiore.

1. Nella stessa pagina Pubblica **[!UICONTROL su]** Image Server, individuate l’intestazione Attributi **** richiesta.
1. Sotto l’intestazione **[!UICONTROL Attributi]** richiesta, individuate Limite **** dimensioni immagine risposta. Quindi, nei campi **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]** associati, aumentate la dimensione massima consentita per le immagini panoramiche.

   Dynamic Media Classic ha un limite di 25.000.000 pixel. La dimensione massima consentita per le immagini con proporzioni 2:1 è 7000 x 3500. Tuttavia, per gli schermi desktop tipici, sono sufficienti 4096 x 2048 pixel.

   >[!NOTE]
   >
   >Sono supportate solo le immagini che rientrano nella dimensione massima consentita per le immagini. Le richieste di immagini che superano il limite di dimensione genereranno una risposta di 403.

1. Nell&#39;intestazione **Attributi richiesta]** , effettuate le seguenti operazioni:

   * Impostate **[!UICONTROL Richiedi modalità]** offuscamento su **[!UICONTROL Disabilitata]**.
   * Impostate **[!UICONTROL Richiedi modalità]** di blocco su **[!UICONTROL Disattivato]**.

   Queste impostazioni sono necessarie per utilizzare il componente **[!UICONTROL Panoramic Media]** in AEM.

1. Nella parte inferiore della pagina Pubblica **[!UICONTROL su]** Image Server, toccate **[!UICONTROL Salva]** a sinistra.

1. Nell&#39;angolo inferiore destro, toccate **[!UICONTROL Chiudi]**.

### Risoluzione dei problemi relativi al componente Panoramic Media {#troubleshooting-the-panoramic-media-wcm-component}

Se un’immagine viene rilasciata nel componente **[!UICONTROL Panoramic Media]** in WCM e il segnaposto del componente viene compresso, è possibile risolvere i seguenti problemi:

* Se si verifica un errore 403 Vietato, la dimensione dell&#39;immagine richiesta potrebbe essere eccessiva. Consultate le impostazioni Limite *dimensioni immagine risposta in* Configurazione di Dynamic Media Classic (Scene7) [](#configuring-dynamic-media-classic-scene).

* Per un blocco ** non valido sulla risorsa o un errore *di* analisi visualizzato sulla pagina, controllate **[!UICONTROL Richiedi modalità]** offuscamento e Modalità **[!UICONTROL blocco]** richiesta per assicurarsi che siano disattivate.
* Per un errore canvas contaminato, imposta un percorso per il file di definizione del set di **[!UICONTROL regole e Annulla validità CTN]** per le richieste precedenti per la risorsa immagine.
* Se dopo una richiesta di immagini con dimensioni superiori al limite supportato, la qualità dell’immagine diventa molto bassa, verificate che l’impostazione **[!UICONTROL JPEG Encoding Attributes (Attributi di codifica JPEG) > Quality (Qualità]** ) non sia vuota. Un&#39;impostazione tipica per il campo **[!UICONTROL Qualità]** è `95`. L’impostazione è disponibile nella pagina Pubblica **[!UICONTROL su]** Image Server. Per accedere alla pagina, consultate [Configurazione di Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Anteprima delle immagini panoramiche {#previewing-panoramic-images}

Consultate [Anteprima delle risorse](previewing-assets.md).

## Pubblicazione di immagini panoramiche {#publishing-panoramic-images}

Consultate [Pubblicazione delle risorse](publishing-dynamicmedia-assets.md).
