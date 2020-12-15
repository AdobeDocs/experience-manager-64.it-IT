---
title: Immagini panoramiche
seo-title: Immagini panoramiche
description: Scoprite come utilizzare le immagini panoramiche in Dynamic Media.
seo-description: Scoprite come utilizzare le immagini panoramiche in Dynamic Media.
uuid: dfd7a55c-7bcc-4d62-8c3a-a73726881103
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: fc285b25-2bce-493c-87bc-5f1a8a26eb42
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 4%

---


# Immagini panoramiche {#panoramic-images}

Questa sezione descrive come utilizzare il visualizzatore immagini panoramiche per riprodurre immagini panoramiche sferiche per un’esperienza di visualizzazione a 360° di una stanza, una proprietà, una posizione o un paesaggio.

Consultate anche [Gestione dei predefiniti per visualizzatori](managing-viewer-presets.md).

![panoramico-immagine2](assets/panoramic-image2.png)

## Caricamento delle risorse da usare con il visualizzatore immagini panoramiche {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Affinché una risorsa caricata possa essere considerata un’immagine panoramica sferica che intendete usare con il visualizzatore immagini panoramiche, la risorsa deve contenere una o entrambe le opzioni seguenti:

* Proporzioni di 2.

   È possibile ignorare l&#39;impostazione predefinita delle proporzioni di 2 in **[!UICONTROL CRXDE Lite]** nel modo seguente:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Tag con le parole chiave `equirectangular`, `spherical`e `panorama`, oppure `spherical` e `panoramic`. Vedere [Utilizzo dei tag](/help/sites-authoring/tags.md).

Sia le proporzioni che i criteri delle parole chiave si applicano alle risorse panoramiche della pagina dettagli risorsa e al componente per **[!UICONTROL elementi multimediali panoramici]**.

Per caricare le risorse da usare con il visualizzatore immagini panoramiche, consultate [Caricamento di risorse](managing-assets-touch-ui.md#uploading-assets).

## Configurazione di Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Affinché il visualizzatore immagini panoramiche funzioni correttamente all’interno AEM, è necessario sincronizzare i predefiniti per visualizzatori immagini panoramiche con i metadati specifici di Dynamic Media Classic e Dynamic Media Classic, in modo che i predefiniti per visualizzatori vengano aggiornati nel JCR. A questo scopo, configura Dynamic Media Classic nel modo seguente:

1. [Accedi alla tua istanza di Dynamic Media ](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) Classicfor per ogni account aziendale.

1. Nell’angolo superiore destro della pagina, fate clic su **[!UICONTROL Configurazione > Impostazione applicazione > Impostazione pubblicazione > Server immagini]**.
1. Nella pagina **[!UICONTROL Image Server Publish]**, dal menu a discesa **[!UICONTROL Contesto pubblicazione]** vicino alla parte superiore, selezionare **[!UICONTROL Image Serving]**.

1. Nella stessa pagina **[!UICONTROL Image Server Publish]**, individuare l&#39;intestazione **[!UICONTROL Request Attributes]**.
1. Sotto l&#39;intestazione **[!UICONTROL Richiedi attributi]**, individuare **[!UICONTROL Rispondi limite dimensioni immagine]**. Quindi, nei campi **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]** associati, aumentate la dimensione massima consentita per le immagini panoramiche.

   Dynamic Media Classic ha un limite di 25.000.000 pixel. La dimensione massima consentita per le immagini con proporzioni 2:1 è 7000 x 3500. Tuttavia, per gli schermi desktop tipici, sono sufficienti 4096 x 2048 pixel.

   >[!NOTE]
   >
   >Sono supportate solo le immagini che rientrano nella dimensione massima consentita per le immagini. Le richieste di immagini che superano il limite di dimensione genereranno una risposta di 403.

1. Sotto l&#39;intestazione **[Richiedi attributi]**, effettuare le seguenti operazioni:

   * Impostare **[!UICONTROL Modalità offuscamento richieste]** su **[!UICONTROL Disattivato]**.
   * Impostare **[!UICONTROL Richiedi modalità di blocco]** su **[!UICONTROL Disattivato]**.

   Queste impostazioni sono necessarie per utilizzare il componente **[!UICONTROL Supporto panoramico]** in AEM.

1. Nella parte inferiore della pagina **[!UICONTROL Image Server Publish]**, toccate **[!UICONTROL Save]** a sinistra.

1. Nell&#39;angolo inferiore destro, toccare **[!UICONTROL Chiudi]**.

### Risoluzione dei problemi relativi al componente Supporto panoramico {#troubleshooting-the-panoramic-media-wcm-component}

Se un&#39;immagine è stata rilasciata nel componente **[!UICONTROL File multimediali panoramici]** in WCM e il segnaposto del componente è stato compresso, è possibile risolvere i seguenti problemi:

* Se si verifica un errore 403 Vietato, la dimensione dell&#39;immagine richiesta potrebbe essere eccessiva. Rivedete le impostazioni *Reply Image Size Limit* (Limite dimensioni immagine risposta) in [Configuring Dynamic Media Classic (Scene7)](#configuring-dynamic-media-classic-scene).

* Per un *blocco non valido* sulla risorsa o per un errore di analisi *Parsing* visualizzato sulla pagina, controllate **[!UICONTROL Modalità offuscamento richieste]** e **[!UICONTROL Modalità blocco richieste]** per assicurarsi che siano disattivate.
* Per un errore canvas con tag, impostate un percorso per il file di definizione del set di regole e annullate CTN **[!UICONTROL per le richieste precedenti per la risorsa immagine.]**
* Se dopo una richiesta di immagini con dimensioni superiori al limite supportato la qualità delle immagini risulta molto bassa, verificate che l&#39;impostazione **[!UICONTROL JPEG Encoding Attributes > Quality]** non sia vuota. Un&#39;impostazione tipica per il campo **[!UICONTROL Quality]** è `95`. L&#39;impostazione è disponibile nella pagina **[!UICONTROL Image Server Publish]**. Per accedere alla pagina, vedere [Configurazione di Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Anteprima delle immagini panoramiche {#previewing-panoramic-images}

Consultate [Anteprima delle risorse](previewing-assets.md).

## Pubblicazione di immagini panoramiche {#publishing-panoramic-images}

Consultate [Pubblicazione di risorse](publishing-dynamicmedia-assets.md).
