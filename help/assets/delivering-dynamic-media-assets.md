---
title: Distribuzione di risorse Dynamic Media
seo-title: Delivering Dynamic Media Assets
description: Scopri come distribuire le risorse Dynamic Media
seo-description: Learn how to deliver dynamic media assets
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 15%

---

# Distribuzione di risorse Dynamic Media {#delivering-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La modalità di distribuzione delle risorse Dynamic Media, sia video che immagini, dipende dall’implementazione del sito web.

Con Dynamic Media hai diverse opzioni:

* Se il sito web è ospitato su AEM, è necessario aggiungere le risorse Dynamic Media direttamente alla pagina.
* Se il sito web non è AEM, puoi scegliere tra:

   * Incorporare il video o l’immagine sul sito web.
   * Collegamento degli URL all’applicazione Web. Utilizza il collegamento quando desideri distribuire un lettore video come finestra a comparsa o modale.
   * Se il sito è reattivo, puoi [fornire immagini ottimizzate.](responsive-site.md)

>[!NOTE]
>
>La funzione Smart imaging funziona con i predefiniti per immagini esistenti e utilizza funzionalità intelligenti all’ultimo millisecondo di distribuzione per ridurre ulteriormente le dimensioni dei file immagine in base al browser o alla velocità di connessione di rete. Vedi [Imaging avanzato](imaging-faq.md) per ulteriori informazioni.

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

Vedi [Domande frequenti sulla distribuzione dei contenuti HTTP/2](/help/sites-administering/scene7-http2faq.md) per saperne di più.
