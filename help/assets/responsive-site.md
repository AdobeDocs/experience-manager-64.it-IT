---
title: Distribuzione di immagini ottimizzate per un sito reattivo
description: Come utilizzare la funzione di codice reattivo in Dynamic Media per fornire immagini ottimizzate
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5edcc765-c374-4368-a0d9-e02a713a24f2
exl-id: 36bb526c-a6d9-4296-8318-97ac72d6b3ba
feature: Publishing
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 13%

---

# Distribuzione di immagini ottimizzate per un sito reattivo {#delivering-optimized-images-for-a-responsive-site}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Utilizza la funzione Codice reattivo quando desideri condividere il codice per il servizio reattivo con il tuo sviluppatore web. Copia la risposta (**[!UICONTROL RESS]**) negli Appunti in modo da poterlo condividere con lo sviluppatore web.

Questa funzione ha senso utilizzare se il sito web si trova su un sito web WCM di terze parti. Tuttavia, se il sito web si trova in AEM, un server di immagini fuori sede esegue il rendering dell&#39;immagine e la fornisce alla pagina web.

Vedi anche [Incorporamento del visualizzatore video in una pagina web.](embed-code.md)

Vedi anche [Collegamento di URL all&#39;applicazione Web.](linking-urls-to-yourwebapplication.md)

**Per fornire immagini ottimizzate per un sito reattivo**:

1. Passa all’immagine per la quale desideri fornire codice reattivo e, nel menu a discesa, tocca **[!UICONTROL Rendering]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Seleziona un predefinito per immagini reattive. Vengono visualizzati i pulsanti **[!UICONTROL URL]** e **[!UICONTROL RESS]**.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >Per poter rendere disponibili i pulsanti **[!UICONTROL URL]** o **[!UICONTROL RESS]**, la risorsa selezionata *e* il predefinito immagine o il predefinito visualizzatore devono essere pubblicati.
   >
   >Dynamic Media - La modalità ibrida richiede la pubblicazione di predefiniti per immagini; Dynamic Media - La modalità Scene7 pubblica automaticamente i predefiniti per immagini.

1. Tocca **[!UICONTROL RESS]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. In **[!UICONTROL Incorpora immagine reattiva]** seleziona e copia il testo del codice reattivo e incollalo nel sito web per accedere alla risorsa reattiva.
1. Modifica i punti di interruzione predefiniti nel codice di incorporamento in modo che corrispondano a quelli del sito web reattivo direttamente nel codice. Inoltre, prova le diverse risoluzioni immagine fornite in diversi punti di interruzione della pagina.

## Utilizzo di HTTP/2 per la distribuzione delle risorse Dynamic Media {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 è il nuovo protocollo web aggiornato che migliora il modo in cui i browser e i server comunicano. Fornisce un trasferimento più rapido delle informazioni e riduce la quantità di potenza di elaborazione necessaria. La distribuzione delle risorse Dynamic Media è supportata tramite HTTP/2, che fornisce tempi di risposta e caricamento migliori.

Vedi [Distribuzione di contenuti HTTP2](http2.md) per informazioni complete su come iniziare a utilizzare HTTP/2 con il tuo account Dynamic Media.
