---
title: Distribuzione di risorse Dynamic Media
seo-title: Distribuzione di risorse Dynamic Media
description: Scopri come distribuire le risorse Dynamic Media
seo-description: Scopri come distribuire le risorse Dynamic Media
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: Gestione risorse
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 25%

---

# Distribuzione di risorse Dynamic Media {#delivering-dynamic-media-assets}

La modalità di distribuzione delle risorse Dynamic Media, sia video che immagini, dipende dall’implementazione del sito web.

Con l’elemento multimediale dinamico hai a disposizione diverse opzioni:

* Se il sito web è ospitato su AEM, allora è necessario aggiungere le risorse dell’elemento multimediale dinamico direttamente sulla pagina.
* Se il sito web non è AEM, puoi scegliere tra:

   * Incorporare il video o l’immagine sul sito web.
   * Collega URL all’applicazione web. Utilizza il collegamento quando desideri distribuire un lettore video come finestra a comparsa o modale.
   * Se il sito è reattivo, è possibile [fornire immagini ottimizzate.](responsive-site.md)

>[!NOTE]
>
>La funzione Smart imaging funziona con i predefiniti per immagini esistenti e utilizza funzionalità intelligenti all’ultimo millisecondo di distribuzione per ridurre ulteriormente le dimensioni dei file immagine in base al browser o alla velocità di connessione di rete. Per ulteriori informazioni, consulta [Smart imaging](imaging-faq.md) .

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Aggiunta di risorse Dynamic Media alle pagine web](adding-dynamic-media-assets-to-pages.md)
* [Incorporare il visualizzatore di video o immagini in una pagina web](embed-code.md)
* [Attivazione della protezione hotlinking in Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-64/assets/dynamic/hotlink-protection.html?lang=it#dynamic)
* Integrazione dell’watermarking digitale non visibile (Digimarc) con Dynamic Media (in arrivo)
* [Collegamento di URL all’applicazione web](linking-urls-to-yourwebapplication.md)
* [Distribuzione di immagini ottimizzate per un sito reattivo](responsive-site.md)
* [Distribuzione di contenuti HTTP2](http2.md)
* [Annullare la validità di contenuti CDN memorizzati nella cache](invalidate-cdn-cached-content.md)
* [Utilizzo di set di regole per la trasformazione degli URL](using-rulesets-to-transform-urls.md)

## Distribuzione di risorse Dynamic Media HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM ora supporta la distribuzione di tutti i contenuti Dynamic Media (immagini e video) su HTTP/2. In altre parole, è disponibile un URL o un codice di incorporamento pubblicato per l’immagine o il video da integrare con qualsiasi applicazione che accetta una risorsa in hosting. La risorsa pubblicata viene quindi distribuita tramite il protocollo HTTP/2. Questo metodo di consegna migliora il modo in cui i browser e i server comunicano, consentendo una migliore risposta e tempi di caricamento di tutte le risorse Dynamic Media.

Per ulteriori informazioni, consulta [Domande frequenti sulla distribuzione dei contenuti HTTP/2](/help/sites-administering/scene7-http2faq.md) .
