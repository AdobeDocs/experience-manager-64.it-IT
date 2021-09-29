---
title: Personalizzazione ed estensione delle risorse
description: Scopri come personalizzare ed estendere Asset Share e Asset Editor, che offre agli utenti un’interfaccia e un set di funzionalità personalizzati.
contentOwner: AG
feature: Developer Tools
role: Developer
exl-id: 0291690b-874a-483d-901f-f02cb6d8ab28
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Personalizzazione ed estensione delle risorse {#customizing-and-extending-assets}

Asset Editor è il punto di accesso principale che gli utenti di un sito web Adobe Enterprise Manager utilizzeranno per trovare, visualizzare e manipolare le risorse digitali nell’archivio.

In qualità di sviluppatore [!DNL Experience Manager], puoi personalizzare ed estendere Asset Editor in diversi modi, presentando agli utenti un’interfaccia e un set di funzionalità specifici.

È possibile personalizzare o migliorare i seguenti aspetti della funzionalità:

* [Estensione di Asset Editor](asseteditorx.md)
* [Estensione della ricerca delle risorse](searchx.md)
* [Elaborazione delle risorse tramite gestori di contenuti multimediali e flussi di lavoro](media-handlers.md)
* [Integrazione delle risorse con il flusso di attività](extending-activity-stream.md)
* [Sviluppo proxy risorse](proxy.md)
* [Best practice per la configurazione di ImageMagick](best-practices-for-imagemagick.md)

## Personalizzazione dell&#39;aspetto {#customizing-the-look-and-feel}

Sono personalizzabili i seguenti aspetti dell’aspetto e del comportamento di Asset Editor:

* Logo: Puoi aggiungere all’interfaccia il logo della tua organizzazione.
* Colori e caratteri: È possibile modificare i colori e i font utilizzati nell’interfaccia.
* Codice HTML: Per una personalizzazione più completa è possibile modificare il codice HTML sottostante che definisce le interfacce.

## Personalizzazione delle rappresentazioni {#customizing-renditions}

Nella terminologia [!DNL Experience Manager Assets] un rendering è il modulo in cui viene presentata una risorsa. In generale, una particolare risorsa può avere più rappresentazioni. Ad esempio, l’immagine a colori completi può avere un rendering nelle dimensioni originali, un altro in una dimensione ridotta e un altro in scala di grigi.

Le rappresentazioni disponibili in una particolare risorsa possono essere personalizzate e possono essere create nuove rappresentazioni.
