---
title: Incorporare il visualizzatore video o immagine Dynamic Media in una pagina web
seo-title: Embedding the Dynamic Media Video or Image viewer on a web page
description: Scopri come incorporare video o immagini Dynamic Media in una pagina web
seo-description: Learn how to embed Dynamic media video or images on a web page
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
exl-id: bff564a8-e982-4e1a-a9b5-05e44e3e4d46
feature: Components
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 21%

---

# Incorporare il visualizzatore video o immagine Dynamic Media in una pagina web {#embedding-the-video-or-image-viewer-on-a-web-page}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Utilizza la funzione **[!UICONTROL Incorpora codice]** per riprodurre il video o visualizzare una risorsa incorporata in una pagina web. Puoi copiare il codice da incorporare negli Appunti, per poi incollarlo nelle pagine web. La modifica del codice non è consentita nella finestra di dialogo **[!UICONTROL Incorpora codice]**.

Incorpora gli URL solo se lo sei _not_ utilizzo [!DNL Experience Manager] come WCM. Se utilizzi [!DNL Experience Manager] come WCM, [aggiungi le risorse direttamente sulla pagina.](adding-dynamic-media-assets-to-pages.md)

Vedi [Collegamento di URL all&#39;applicazione Web.](linking-urls-to-yourwebapplication.md)

Vedi [Distribuzione di immagini ottimizzate per un sito reattivo.](responsive-site.md)

>[!NOTE]
>
>Il codice di incorporamento non è disponibile per la copia finché non avrai pubblicato la risorsa selezionata. Inoltre, devi pubblicare il predefinito visualizzatore o il predefinito immagine.
>
>Vedi [Pubblicazione delle risorse](publishing-dynamicmedia-assets.md).
>
>Vedi [Pubblicazione dei predefiniti per visualizzatori](managing-viewer-presets.md#publishing-viewer-presets).
>
>Vedi [Pubblicazione dei predefiniti per immagini](managing-image-presets.md#publishing-image-presets).

**Per incorporare il visualizzatore video o immagine Dynamic Media in una pagina web**:

1. Passa a *pubblicato* risorsa video o immagine di cui desideri copiare il codice da incorporare.

   Il codice è disponibile per la copia solo *dopo* la prima *pubblicazione* delle risorse. Inoltre, è necessario pubblicare anche il predefinito visualizzatore o il predefinito immagine.

   Vedi [Pubblicazione delle risorse.](publishing-dynamicmedia-assets.md)

   Vedi [Pubblicazione dei predefiniti per visualizzatori](managing-viewer-presets.md#publishing-viewer-presets).

   Vedi [Pubblicazione dei predefiniti per immagini](managing-image-presets.md#publishing-image-presets).

1. Nella barra a sinistra, seleziona il menu a discesa e tocca **[!UICONTROL Visualizzatori]**.
1. Nella barra a sinistra, tocca un nome predefinito per visualizzatori. Il predefinito visualizzatore viene applicato alla risorsa.
1. Tocca **[!UICONTROL Incorpora]**.
1. In **[!UICONTROL Codice di incorporamento]** , copia l’intero codice negli Appunti, quindi tocca **[!UICONTROL Chiudi]**.
1. Incolla il codice di incorporamento nelle pagine web.

## Utilizzo di HTTP/2 per fornire le risorse Dynamic Media {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 è il nuovo protocollo web aggiornato che migliora il modo in cui i browser e i server comunicano. Fornisce un trasferimento più rapido delle informazioni e riduce la quantità di potenza di elaborazione necessaria. La distribuzione delle risorse Dynamic Media può ora avvenire tramite HTTP/2, garantendo tempi di risposta e caricamento migliori.

Vedi [Distribuzione di contenuti HTTP2](http2.md) per informazioni complete su come iniziare a utilizzare HTTP/2 con il tuo account Dynamic Media.
