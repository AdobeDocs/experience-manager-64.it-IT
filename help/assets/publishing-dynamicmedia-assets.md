---
title: Pubblicazione di risorse multimediali dinamiche
seo-title: Pubblicazione di risorse multimediali dinamiche
description: Come pubblicare le risorse multimediali dinamiche
seo-description: Come pubblicare le risorse multimediali dinamiche
uuid: b1bee905-86cf-4284-8d4e-067e11557899
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 99d7025f-d022-4213-83c0-815a4712c573
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 8%

---


# Publishing Dynamic Media Assets {#publishing-dynamic-media-assets}

Per pubblicare le risorse Contenuti multimediali dinamici, selezionatele e toccate **[!UICONTROL Pubblica]**. Dopo la pubblicazione, le risorse multimediali dinamiche possono essere incluse in una pagina Web tramite URL o mediante incorporazione.

Potete anche pubblicare istantaneamente le risorse caricate, senza alcun intervento da parte dell’utente. Consultate [Configurazione di contenuti multimediali dinamici - Modalità](config-dms7.md)Scene7.

Nella **[!UICONTROL Vista a schede]**, sotto il nome di una risorsa viene visualizzata una piccola icona a forma di globo, per indicare che è stata pubblicata. Nella **[!UICONTROL Vista a elenco]**, la colonna **[!UICONTROL Pubblicato]** indica lo stato di pubblicazione delle risorse.

>[!NOTE]
>
>Se una risorsa è già pubblicata, usate AEM per spostare la risorsa in un’altra cartella e ripubblicarla dalla nuova posizione, il percorso originale della risorsa pubblicata è ancora disponibile, insieme alla nuova risorsa pubblicata. La risorsa pubblicata originale, tuttavia, è &quot;perduta&quot; in AEM e non può essere annullata la pubblicazione. Di conseguenza, è consigliabile annullare la pubblicazione delle risorse prima di spostarle in un’altra cartella.

Se intendete pubblicare le risorse video subito dopo la codifica, accertatevi che la codifica sia stata completata. Quando i video vengono ancora codificati, il sistema segnala che è in corso un flusso di lavoro di elaborazione video. Al termine della codifica video, dovreste essere in grado di visualizzare in anteprima le rappresentazioni video. A questo punto, è sicuro pubblicare i video senza che si verifichino errori di pubblicazione.

See also [Linking URLs to your Web Application](linking-urls-to-yourwebapplication.md).

Consultate anche [Incorporamento del visualizzatore video in una pagina Web.](embed-code.md)

>[!NOTE]
>
>* Per usare l’URL, le risorse devono essere pubblicate. Se le risorse non vengono pubblicate, non sarà possibile copiare e incollare l’URL in un browser Web.
>* I predefiniti per immagini e per visualizzatori devono essere attivati e pubblicati per la distribuzione live.

>



Per informazioni dettagliate sulla pubblicazione di un set o di una risorsa, consultate [Pubblicazione di risorse.](managing-assets-touch-ui.md)

## Distribuzione HTTP/2 di risorse Dynamic Media {#http-delivery-of-dynamic-media-assets}

AEM ora supporta la distribuzione di tutti i contenuti multimediali dinamici (immagini e video) su HTTP/2. ossia un URL pubblicato o un codice da incorporare per l’immagine o il video può essere integrato con qualsiasi applicazione che accetta una risorsa ospitata. La risorsa pubblicata viene quindi distribuita tramite il protocollo HTTP/2. Questo metodo di distribuzione migliora il modo in cui i browser e i server comunicano, consentendo una migliore risposta e tempi di caricamento di tutte le risorse Dynamic Media.

Per ulteriori informazioni, consultate la distribuzione [HTTP/2 di contenuti con domande](/help/sites-administering/scene7-http2faq.md) frequenti.
