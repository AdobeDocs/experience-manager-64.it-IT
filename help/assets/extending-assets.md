---
title: Personalizzazione ed estensione delle risorse
description: Scoprite come personalizzare ed estendere l’Editor risorse e condivisione di risorse, che offre agli utenti un’interfaccia e un set di funzionalità specifici.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Personalizzazione ed estensione delle risorse {#customizing-and-extending-assets}

Asset Editor è il punto di accesso principale che gli utenti di un sito Web Enterprise Manager (AEM)  Adobe utilizzeranno per trovare, visualizzare e manipolare le risorse digitali presenti nell’archivio.

In qualità di sviluppatore AEM, potete personalizzare ed estendere l’Editor risorse in diversi modi, presentando agli utenti un’interfaccia e un set di funzionalità specifici.

È possibile personalizzare o migliorare i seguenti aspetti della funzionalità:

* [Estensione dell’Editor risorse](asseteditorx.md)
* [Estensione della ricerca delle risorse](searchx.md)
* [Elaborazione delle risorse tramite gestori e flussi di lavoro](media-handlers.md)
* [Integrazione delle risorse con il flusso di attività](extending-activity-stream.md)
* [Sviluppo proxy risorse](proxy.md)
* [Best practice per la configurazione di ImageMagick](best-practices-for-imagemagick.md)

## Personalizzazione dell’aspetto {#customizing-the-look-and-feel}

È possibile personalizzare i seguenti aspetti dell’aspetto e del comportamento dell’Editor risorse:

* Logo: È possibile aggiungere il logo aziendale all&#39;interfaccia.
* Colori e font: È possibile modificare i colori e i font utilizzati nell&#39;interfaccia.
* Codice HTML: Per una personalizzazione più completa, potete modificare il codice HTML sottostante che definisce le interfacce.

## Personalizzazione delle rappresentazioni {#customizing-renditions}

 terminologia di AEM Assets, una rappresentazione è il modulo in cui viene presentata una risorsa. In generale, una particolare risorsa può avere più rappresentazioni. Ad esempio, l’immagine a colori interi può avere una rappresentazione nelle dimensioni originali, un’altra in una dimensione ridotta e un’altra in scala di grigio.

Le rappresentazioni in cui è disponibile una particolare risorsa possono essere personalizzate e create nuove rappresentazioni.
