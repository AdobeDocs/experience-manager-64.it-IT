---
title: Distribuzione di contenuti HTTP2
seo-title: HTTP2 Delivery of Content
description: HTTP/2 migliora il modo in cui i browser e i server comunicano, consentendo un trasferimento più rapido delle informazioni riducendo al contempo la quantità di potenza di elaborazione necessaria.
seo-description: HTTP/2 improves the way browsers and servers communicate, allowing for faster transfer of information while reducing the amount of needed processing power.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
exl-id: 59cd9f8c-6d01-448d-bf57-bdc9fd2e381b
feature: Asset Management
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 3%

---

# Distribuzione di contenuti HTTP2 {#http-delivery-of-content}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe è orgogliosa di annunciare la disponibilità della distribuzione HTTP/2 dei contenuti che offre il vantaggio complessivo di prestazioni migliorate.

## Cos’è HTTP/2? {#what-is-http}

HTTP/2 migliora il modo in cui i browser e i server comunicano, consentendo un trasferimento più rapido delle informazioni riducendo al contempo la quantità di potenza di elaborazione necessaria.

Il seguente sito web descrive HTTP/2 e i relativi vantaggi in modo breve e semplice:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Quali sono i vantaggi principali del passaggio a HTTP/2 per la distribuzione dei contenuti? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Il miglioramento delle prestazioni varia notevolmente in base a fattori come il codice del sito web, il modo in cui utilizzi Dynamic Media, il dispositivo, lo schermo e la posizione del consumatore e così via.

I test eseguiti da Adobe hanno dato i seguenti risultati:

* Per le immagini, il tempo di risposta è migliorato del 7%-28% a seconda del dispositivo e del browser. I vantaggi più significativi in termini di prestazioni sono stati registrati sui dispositivi iOS.
* Per i visualizzatori, le prestazioni del tempo di caricamento sono migliorate del 15%.

La dimostrazione seguente illustra la differenza tra il caricamento HTTP/1 e HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Posso passare a HTTP/2? {#am-i-eligible-to-switch-over-to-http}

Per utilizzare HTTP/2, è necessario soddisfare i seguenti requisiti:

* Utilizza HTTPS sicuro per le richieste rich media.
* Utilizza la rete CDN (content delivery network) in bundle Adobe come parte della tua licenza Dynamic Media.
* Utilizza un dominio dedicato (non-company-h.assetsadobe#.com).

   Se disponi già di un dominio dedicato, puoi effettuare il consenso tramite il supporto tecnico.

   Se non disponi di un dominio dedicato, Adobe pianificherà la transizione a HTTP/2 nel 2018.

## Qual è la procedura per abilitare HTTP/2 per il mio account Dynamic Media? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

È necessario avviare la richiesta per passare a HTTP/2; non viene fatto automaticamente per te.

1. Avvia una richiesta di supporto tecnico per passare a HTTP2. Vedi [Accesso al portale di assistenza clienti](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

   1. Fornisci le seguenti informazioni nella richiesta di assistenza:

      1. Nome contatto principale, e-mail, telefono.
      1. Tutti i domini da passare a HTTP2.
      1. Verifica di utilizzare HTTPS protetto per le richieste rich media.
      1. Verifica di utilizzare la CDN tramite Adobe e di non essere gestito con una relazione diretta.
      1. Verifica di utilizzare un dominio dedicato. Se utilizzi Dynamic Media, stai già utilizzando un dominio dedicato.
   1. Il supporto tecnico ti aggiunge all’elenco di attesa dei clienti HTTP/2 in base all’ordine in cui sono state inviate le richieste.
   1. Quando Adobe è pronto per gestire la richiesta, il supporto ti contatterà per coordinare la transizione e impostare una data di destinazione.
   1. Riceverai una notifica dopo il completamento e potrai verificare la riuscita della transizione a HTTP2.

      Poiché il browser non dichiara questo fatto, è necessario scaricare un&#39;estensione.

      Per Firefox e Chrome esiste un&#39;estensione chiamata &quot;HTTP/2 e SPDY Indicator&quot;. I browser supportano solo http/2 in modo sicuro, pertanto è necessario chiamare un URL con https per verificare. Se http/2 è supportato, questo è indicato dall&#39;estensione sotto forma di un simbolo di Flash blu e un&#39;intestazione &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.


## Quando posso aspettarmi la transizione verso HTTP/2? {#when-can-i-expect-to-be-transitioned-over-to-http}

Le richieste saranno elaborate nell’ordine in cui vengono ricevute dal supporto tecnico.

>[!NOTE]
>
>Ci può essere un lungo lead time perché la transizione a HTTP/2 comporta la cancellazione della cache. Pertanto, è possibile gestire solo alcune transizioni dei clienti alla volta.

## Quali sono i rischi connessi al passaggio a HTTP/2? {#what-are-the-risks-with-moving-to-http}

La transizione a HTTP/2 cancella la cache alla rete CDN perché comporta il passaggio a una nuova configurazione CDN.

Il contenuto non memorizzato nella cache colpisce direttamente i server di origine di Adobe fino a quando la cache non viene ricostruita nuovamente. Per questo motivo, Adobe pianifica di gestire alcune transizioni dei clienti alla volta in modo da mantenere prestazioni accettabili quando si richiamano le richieste dalla nostra origine.

## Come si verifica se un URL o un sito web è attivato con HTTP/2? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Poiché il browser non dichiara questo fatto, è necessario scaricare un&#39;estensione.

Per Firefox e Chrome esiste un&#39;estensione chiamata &quot;HTTP/2 e SPDY Indicator&quot;. I browser supportano solo http/2 in modo sicuro, pertanto è necessario chiamare un URL con https per verificare. Se http/2 è supportato, questo è indicato dall&#39;estensione sotto forma di un simbolo di Flash blu e un&#39;intestazione &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.
