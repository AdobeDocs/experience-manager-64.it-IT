---
title: Confronto delle funzioni disponibili in Risorse AEM e Libreria di AEM Media
description: Domande frequenti su Risorse AEM e Libreria AEM Media, comprese le differenze.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968

---


# AEM Assets e AEM MediaLibrary a confronto {#aem-assets-vs-aem-medialibrary}

Risorse Adobe Experience Manager (AEM) è parte integrante della piattaforma AEM. Questa integrazione fluida è vista come un importante vantaggio di AEM e assicura coerenza nella gestione dei contenuti e un&#39;elevata produttività per gli autori dei contenuti.

## Domande frequenti {#frequently-asked-questions}

### Cos’è AEM Assets? {#what-is-aem-assets}

Risorse AEM è un’applicazione della piattaforma AEM che consente ai clienti di gestire le proprie risorse digitali (immagini, video, documenti e clip audio) in un archivio basato su Web. Risorse AEM include il supporto per metadati, rappresentazioni, il Finder di gestione delle risorse digitali e l’interfaccia utente di amministrazione di AEM Assets.

### Cos’è la libreria AEM Media? {#what-is-the-aem-media-library}

AEM Media Library è una parte designata dell&#39;archivio dei contenuti di AEM WCM in cui vengono memorizzate le immagini e altre risorse condivise. La libreria Media utilizza le funzionalità di gestione delle risorse digitali di AEM WCM.

### Cosa ottengo da Risorse AEM che non fa parte di AEM WCM? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Le funzioni esclusive disponibili solo per i clienti di Risorse AEM sono:

1. possibilità di estrarre e modificare metadati diversi da titolo, tag e descrizione.
1. l’amministratore di Risorse AEM, disponibile dalla schermata di benvenuto facendo clic sul secondo pulsante accanto a `siteadmin`.
1. Tutti i passaggi del flusso di lavoro relativi a Gestione delle risorse digitali, ad esempio l’assimilazione delle risorse AEM, l’eliminazione delle risorse AEM, la gestione delle risorse secondarie di AEM, l’estrazione dei metadati di Risorse AEM.
1. librerie, incluso lo spazio del pacchetto `dam` im.

L’utilizzo di queste funzioni richiede una licenza valida di Risorse AEM.

### Risorse AEM è disponibile come pacchetto separato? {#is-aem-assets-available-as-a-separate-package}

No. Per semplificare l&#39;installazione e la distribuzione, tutte le applicazioni AEM e i componenti aggiuntivi vengono forniti in un unico pacchetto con tutte le funzionalità incluse. Ciò non implica che si disponga dell&#39;autorizzazione per utilizzare tutte le funzioni del pacchetto.

#### Desidero modificare i metadati delle risorse digitali. Sono necessarie Risorse AEM? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Se intendete modificare metadati diversi da titolo, descrizione e tag, è necessario concedere la licenza a Risorse AEM.

#### È possibile ridimensionare automaticamente le immagini al momento dell&#39;importazione. Sono necessarie Risorse AEM? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

No. Il ridimensionamento e la trasformazione automatica basata sul flusso di lavoro delle immagini statiche, nonché la possibilità di gestire le rappresentazioni, fanno parte della libreria AEM Media. Queste funzioni non richiedono una licenza di AEM Assets.

### Voglio ridimensionare le immagini utilizzando un componente immagine personalizzato. Sono necessarie Risorse AEM? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

Il componente immagine fa parte di AEM WCM. La libreria grafica utilizzata dal componente immagine (ma anche da Risorse AEM) fa parte della piattaforma AEM e non richiede una licenza di Risorse AEM.

### Come posso impedire ai miei utenti di utilizzare Risorse AEM se non dispongo della licenza per Risorse AEM? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

Puoi rimuovere da AEM tutti i flussi di lavoro, i componenti, le tassonomie, le opzioni e l’amministratore di Risorse AEM. In questo modo si evita che gli utenti utilizzino accidentalmente le funzioni di Risorse AEM per le quali non è stata concessa la licenza.

### Desidero aggiungere delle immagini a una pagina e ritagliarle e ridimensionarle. Sono necessarie Risorse AEM? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

Per questo caso d’uso non è necessario acquistare AEM Assets, anche l’utilizzo della libreria Media non è richiesto per utilizzare immagini su un sito Web, in quanto il componente per immagini intelligenti consente di caricare le immagini direttamente nella pagina.

>[!MORELIKETHIS]
>
>* [Elenco dettagliato delle differenze tra le funzioni](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

