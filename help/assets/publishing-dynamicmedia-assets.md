---
title: Pubblicazione delle risorse Dynamic Media
description: Come pubblicare le risorse Dynamic Media, inclusa la distribuzione HTTP/2 di tali risorse.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: ebe30c07-1d76-4338-b301-49591f981688
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 9%

---

# Pubblicazione delle risorse Dynamic Media {#publishing-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per pubblicare le risorse Dynamic Media, seleziona le risorse e tocca **[!UICONTROL Pubblica]**. Dopo la pubblicazione, le risorse Dynamic Media sono disponibili per l’inclusione in una pagina web tramite URL o tramite incorporazione.

Puoi anche pubblicare istantaneamente le risorse caricate senza alcun intervento da parte dell’utente. Vedi [Configurazione di Dynamic Media - Modalità Scene7](config-dms7.md).

Nella **[!UICONTROL Vista a schede]**, sotto il nome di una risorsa viene visualizzata una piccola icona a forma di globo, per indicare che è stata pubblicata. Nella **[!UICONTROL Vista a elenco]**, la colonna **[!UICONTROL Pubblicato]** indica lo stato di pubblicazione delle risorse.

>[!NOTE]
>
>Se una risorsa è già stata pubblicata, utilizza AEM per spostarla in un’altra cartella e ripubblicarla dalla nuova posizione, la posizione originale della risorsa pubblicata è ancora disponibile, insieme alla nuova risorsa pubblicata. La risorsa pubblicata originale, tuttavia, è &quot;persa&quot; in AEM e non può essere annullata. Pertanto, come best practice, annulla la pubblicazione delle risorse prima di spostarle in un’altra cartella.

Se intendi pubblicare le risorse video subito dopo averle codificate, accertati che la codifica sia completa. Quando i video vengono ancora codificati, il sistema ti informa che è in corso un flusso di lavoro di elaborazione video. Al termine della codifica video, dovresti essere in grado di visualizzare in anteprima le rappresentazioni video. A questo punto, è sicuro per te pubblicare i video senza che si verifichino errori di pubblicazione.

Vedi anche [Collegamento di URL all’applicazione Web](linking-urls-to-yourwebapplication.md).

Vedi anche [Incorporamento del visualizzatore video in una pagina web.](embed-code.md)

>[!NOTE]
>
>* Per utilizzare l’URL, le risorse devono essere pubblicate. Se le risorse non vengono pubblicate, non sarà possibile copiare e incollare l’URL in un browser web.
>* I predefiniti per immagini e visualizzatori devono essere attivati e pubblicati per la distribuzione in diretta.
>


Per informazioni dettagliate sulla pubblicazione di un set o di una risorsa, consulta [Pubblicazione delle risorse.](managing-assets-touch-ui.md)

## Distribuzione di risorse Dynamic Media HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM ora supporta la distribuzione di tutti i contenuti Dynamic Media (immagini e video) su HTTP/2. In altre parole, è disponibile un URL o un codice di incorporamento pubblicato per l’immagine o il video da integrare con qualsiasi applicazione che accetta una risorsa in hosting. La risorsa pubblicata viene quindi distribuita tramite il protocollo HTTP/2. Questo metodo di consegna migliora il modo in cui i browser e i server comunicano, consentendo una migliore risposta e tempi di caricamento di tutte le risorse Dynamic Media.

Vedi [Domande frequenti sulla distribuzione di contenuti HTTP/2](/help/sites-administering/scene7-http2faq.md) per saperne di più.
