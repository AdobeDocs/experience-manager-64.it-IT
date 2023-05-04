---
title: Immagini panoramiche
description: Scopri come utilizzare le immagini panoramiche in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Panoramic Images
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 5%

---

# Immagini panoramiche {#panoramic-images}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa sezione descrive come utilizzare il visualizzatore di immagini panoramiche per riprodurre immagini panoramiche sferiche per un’esperienza di visualizzazione a 360° di una stanza, una proprietà, una posizione o un paesaggio.

Vedi anche [Gestione dei predefiniti per visualizzatori](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Caricamento delle risorse da utilizzare con il visualizzatore di immagini panoramiche {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Affinché una risorsa caricata possa qualificarsi come immagine panoramica sferica che intendi utilizzare con il visualizzatore di immagini panoramiche, la risorsa deve avere uno o entrambi i seguenti elementi:

* Rapporto di formato 2.

   È possibile ignorare l&#39;impostazione predefinita delle proporzioni di 2 in **[!UICONTROL CRXDE Lite]** al seguente indirizzo:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Etichettate con le parole chiave `equirectangular`oppure `spherical`e `panorama`oppure `spherical` e `panoramic`. Vedi [Utilizzo dei tag](/help/sites-authoring/tags.md).

Sia le proporzioni che i criteri delle parole chiave si applicano alle risorse panoramiche della pagina dettagli risorsa e al componente per **[!UICONTROL elementi multimediali panoramici]**.

Per caricare le risorse da utilizzare con il visualizzatore di immagini panoramiche, vedi [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets).

## Configurazione di Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Affinché il visualizzatore di immagini panoramiche funzioni correttamente all’interno di AEM, devi sincronizzare i predefiniti visualizzatore di immagini panoramiche con i metadati specifici di Dynamic Media Classic e Dynamic Media Classic, in modo che i predefiniti visualizzatore vengano aggiornati nel JCR. A questo scopo, configura Dynamic Media Classic nel modo seguente:

1. [Accedere all’applicazione desktop Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) per ciascun account aziendale.

1. Fai clic su nell’angolo superiore destro della pagina **[!UICONTROL Configurazione > Impostazione applicazione > Impostazioni pubblicazione > Image Server]**.
1. Sulla **[!UICONTROL Pubblicazione su Image Server]** dalla pagina **[!UICONTROL Contesto di pubblicazione]** menu a discesa vicino alla parte superiore, seleziona **[!UICONTROL Image Serving]**.

1. Sullo stesso **[!UICONTROL Pubblicazione su Image Server]** pagina, individuare l’intestazione **[!UICONTROL Attributi della richiesta]**.
1. Sotto la **[!UICONTROL Attributi della richiesta]** intestazione, individuare **[!UICONTROL Limite dimensione immagine risposta]**. Quindi, nella **[!UICONTROL Larghezza]** e **[!UICONTROL Altezza]** aumentare le dimensioni massime consentite per le immagini panoramiche.

   Dynamic Media Classic ha un limite di 25.000.000 pixel. Le dimensioni massime consentite per le immagini con un rapporto di formato 2:1 sono 7000 x 3500. Tuttavia, per gli schermi desktop tipici, sono sufficienti 4096 x 2048 pixel.

   >[!NOTE]
   >
   >Sono supportate solo le immagini che rientrano nella dimensione massima consentita. Le richieste di immagini che superano il limite di dimensione si tradurranno in una risposta 403.

1. Sotto la **[Attributi della richiesta]** titolo, procedi come segue:

   * Imposta **[!UICONTROL Modalità offuscamento richieste]** a **[!UICONTROL Disabilitato]**.
   * Imposta **[!UICONTROL Modalità di blocco delle richieste]** a **[!UICONTROL Disabilitato]**.

   Queste impostazioni sono necessarie per utilizzare il **[!UICONTROL Supporti panoramici]** in AEM.

1. Nella parte inferiore del **[!UICONTROL Pubblicazione su Image Server]** pagina, a sinistra, tocca **[!UICONTROL Salva]**.

1. Nell’angolo in basso a destra, tocca **[!UICONTROL Chiudi]**.

### Risoluzione dei problemi relativi al componente Elemento multimediale panoramico {#troubleshooting-the-panoramic-media-wcm-component}

Se viene rilasciata un’immagine nel **[!UICONTROL Supporti panoramici]** componente in WCM e il segnaposto del componente è stato compresso. Potrebbe essere utile risolvere i seguenti problemi:

* Se si verifica un errore 403 Vietato, potrebbe essere dovuto al fatto che la dimensione dell&#39;immagine richiesta è troppo grande. Consulta la sezione *Limite dimensione immagine risposta* impostazioni in [Configurazione di Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* Per un *Blocco non valido* sull’attività o *Errore di analisi* visualizzato sulla pagina, controlla **[!UICONTROL Modalità offuscamento richieste]** e **[!UICONTROL Modalità di blocco delle richieste]** per garantire che siano disabilitati.
* Per un errore di tela contaminata, imposta un **[!UICONTROL Percorso file definizione set regole e annullamento della validità CTN]** per le richieste precedenti per la risorsa immagine.
* Se la qualità dell&#39;immagine diventa molto bassa dopo una richiesta di immagine con dimensioni superiori al limite supportato, controlla che la **[!UICONTROL Attributi di codifica JPEG > Qualità]** l&#39;impostazione non è vuota. Impostazione tipica per **[!UICONTROL Qualità]** campo `95`. Puoi trovare l’impostazione nella **[!UICONTROL Pubblicazione su Image Server]** pagina. Per accedere alla pagina, vedi [Configurazione di Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## Anteprima delle immagini panoramiche {#previewing-panoramic-images}

Vedi [Anteprima delle risorse](previewing-assets.md).

## Pubblicazione di immagini panoramiche {#publishing-panoramic-images}

Vedi [Pubblicazione delle risorse](publishing-dynamicmedia-assets.md).
