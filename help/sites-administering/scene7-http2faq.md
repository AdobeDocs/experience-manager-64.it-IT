---
title: Domande frequenti sulla distribuzione dei contenuti HTTP2
description: Informazioni sulla distribuzione dei contenuti HTTP2.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
exl-id: 2da4c0b3-119e-436e-9f03-f794283e9a37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 3%

---

# Domande frequenti sulla distribuzione dei contenuti HTTP2{#http-delivery-of-content-faq}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe è entusiasta di annunciare la disponibilità della distribuzione di contenuti HTTP/2. Utilizzando HTTP/2 noterai un aumento complessivo delle prestazioni.

## Cos’è HTTP/2? {#what-is-http}

HTTP/2 migliora il modo in cui i browser e i server comunicano, consentendo un trasferimento più rapido delle informazioni riducendo al contempo la quantità di potenza di elaborazione necessaria.

Il seguente sito web descrive in modo breve e semplice HTTP/2 e i relativi vantaggi:

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
* Utilizza la rete CDN (content delivery network) in bundle Adobe come parte della tua licenza Dynamic Media Classic.
* Utilizza un dominio dedicato, ovvero `images.company.com` o `mycompany.scene7.com`), non un dominio Dynamic Media Classic generico (ovvero, `s7d1.scene7.com`, `s7d2.scene7.com`oppure `s7d13.scene7.com`).

   Per trovare i tuoi domini, accedi al tuo account tramite [applicazione desktop Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app). Quindi tocca **[!UICONTROL Configurazione > Impostazione applicazione > Impostazioni generali]**. Cerca il campo contrassegnato **Nome server pubblicato**. Se utilizzi un dominio Dynamic Media generico, puoi richiedere il passaggio al dominio personalizzato come parte di questa transizione.

## Qual è la procedura per abilitare HTTP/2 per il mio account Dynamic Media Classic? {#what-is-the-process-for-enabling-http-for-my-scene-account}

1. Devi [utilizza l’Admin Console per creare un caso di supporto](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) e richiedere il passaggio a HTTP/2; non viene fatto automaticamente per te.
1. Fornisci le seguenti informazioni nel tuo caso di assistenza:

   * Nome contatto principale, indirizzo e-mail e numero di telefono.
   * Tutti i domini da passare a HTTP2. Cioè, `images.company.com` o `mycompany.scene7.com`.

      Per trovare i tuoi domini, accedi al tuo account tramite [applicazione desktop Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app). Quindi tocca **[!UICONTROL Configurazione > Impostazione applicazione > Impostazioni generali]**. Cerca il campo contrassegnato **[!UICONTROL Nome server pubblicato.]**
   Fai clic su **[!UICONTROL Configurazione > Impostazione applicazione > Impostazioni generali]**. Cerca il campo contrassegnato **[!UICONTROL Nome server pubblicato]**.

   * Verifica di utilizzare HTTPS protetto per le richieste rich media.
   * Verifica di utilizzare la CDN tramite Adobe e di non gestirla con una relazione diretta.
   * Verifica di utilizzare un dominio dedicato. Cioè, `images.company.com` o `mycompany.scene7.com`, non un dominio Dynamic Media generico come `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

      Per trovare i tuoi domini, accedi al tuo account tramite [applicazione desktop Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app). Quindi tocca **[!UICONTROL Configurazione > Impostazione applicazione > Impostazioni generali]**. Cerca il campo contrassegnato **[!UICONTROL Nome server pubblicato.]** Se utilizzi un dominio Dynamic Media generico, puoi richiedere il passaggio al dominio personalizzato come parte di questa transizione.
   1. Il supporto tecnico ti aggiunge all’elenco di attesa dei clienti HTTP/2 in base all’ordine in cui sono state inviate le richieste.
   1. Quando Adobe è pronto per gestire la richiesta, il supporto ti contatterà per coordinare la transizione e impostare una data di destinazione.
   1. Dopo il completamento riceverai una notifica e potrai verificare la riuscita della transizione a HTTP2.



## Quando posso aspettarmi la transizione verso HTTP/2? {#when-can-i-expect-to-be-transitioned-over-to-http}

Le richieste vengono elaborate nell’ordine in cui vengono ricevute dal supporto tecnico.

>[!NOTE]
>
>Ci può essere un lungo lead time perché la transizione a HTTP/2 comporta la cancellazione della cache. Pertanto, è possibile gestire solo alcune transizioni dei clienti alla volta.

## Quali sono i rischi connessi al passaggio a HTTP/2? {#what-are-the-risks-with-moving-to-http}

La transizione a HTTP/2 cancella la cache alla rete CDN perché comporta il passaggio a una nuova configurazione CDN.

Il contenuto non memorizzato nella cache colpisce direttamente i server di origine di Adobe fino a quando la cache non viene ricostruita nuovamente. Per questo motivo, Adobe pianifica di gestire alcune transizioni dei clienti alla volta in modo da mantenere prestazioni accettabili quando si richiamano le richieste dalla nostra origine.

## Come si verifica se un URL o un sito web è attivato con HTTP/2? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

È necessario scaricare un&#39;esternalizzazione da utilizzare con il browser Web. Per Firefox e Chrome esiste un&#39;estensione denominata **[!UICONTROL Indicatore HTTP/2 e SPDY]**. I browser supportano solo HTTP/2 in modo sicuro, pertanto è necessario chiamare un URL con HTTPS per verificare. Se HTTP/2 è supportato, questo è indicato dall&#39;estensione sotto forma di un simbolo di Flash blu e un&#39;intestazione &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.
