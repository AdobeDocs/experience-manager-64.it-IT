---
title: Distribuzione di risorse Dynamic Media
seo-title: Distribuzione di risorse Dynamic Media
description: Scopri come distribuire risorse multimediali dinamiche
seo-description: Scopri come distribuire risorse multimediali dinamiche
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
translation-type: tm+mt
source-git-commit: 15d933a2e71a44e84cdcc9ae28f60c67b43bd8f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 23%

---


# Distribuzione di risorse Dynamic Media {#delivering-dynamic-media-assets}

La modalità di distribuzione delle risorse multimediali dinamiche (video e immagini) dipende dall’implementazione del sito Web.

Con l’elemento multimediale dinamico hai a disposizione diverse opzioni:

* Se il sito web è ospitato su AEM, allora è necessario aggiungere le risorse dell’elemento multimediale dinamico direttamente sulla pagina.
* Se il sito Web non è AEM, potete scegliere tra:

   * Incorporamento del video o dell’immagine nel sito Web.
   * Collegare gli URL all’applicazione Web. Usate il collegamento per distribuire un lettore video come finestra a comparsa o modale.
   * Se il sito è reattivo, potete [distribuire immagini ottimizzate.](responsive-site.md)

>[!NOTE]
>
>La funzione di imaging avanzato funziona con i predefiniti per immagini esistenti e utilizza funzionalità intelligenti all’ultimo millisecondo di distribuzione per ridurre ulteriormente le dimensioni dei file immagine in base alla velocità della connessione di rete o del browser. Per ulteriori informazioni, consulta [Smart Imaging](imaging-faq.md) .

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Aggiunta di risorse multimediali dinamiche alle pagine Web](adding-dynamic-media-assets-to-pages.md)
* [Incorporazione di un visualizzatore video o di immagini in una pagina Web](embed-code.md)
* [Attivazione della protezione hotlinking in Dynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/hotlink-protection.html)
* Integrazione della filigrana digitale non visibile (Digimarc) con Dynamic Media (disponibile a breve)
* [Collegamento di URL all’applicazione web](linking-urls-to-yourwebapplication.md)
* [Distribuzione di immagini ottimizzate per un sito reattivo](responsive-site.md)
* [Distribuzione di contenuti HTTP2](http2.md)
* [Annullare la validità di contenuti CDN memorizzati nella cache](invalidate-cdn-cached-content.md)
* [Utilizzo di set di regole per la trasformazione degli URL](using-rulesets-to-transform-urls.md)

## Distribuzione HTTP/2 di risorse Dynamic Media {#http-delivery-of-dynamic-media-assets}

AEM ora supporta la distribuzione di tutti i contenuti multimediali dinamici (immagini e video) su HTTP/2. ossia un URL pubblicato o un codice da incorporare per l’immagine o il video può essere integrato con qualsiasi applicazione che accetta una risorsa ospitata. La risorsa pubblicata viene quindi distribuita tramite il protocollo HTTP/2. Questo metodo di distribuzione migliora il modo in cui i browser e i server comunicano, consentendo una migliore risposta e tempi di caricamento di tutte le risorse Dynamic Media.

Per ulteriori informazioni, consulta [HTTP/2 Distribuzione di contenuti con domande](/help/sites-administering/scene7-http2faq.md) frequenti.
