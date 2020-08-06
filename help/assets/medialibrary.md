---
title: Confronto delle funzioni disponibili in  AEM Assets e AEM Media Library
description: Domande frequenti su  AEM Assets e AEM Media Library, comprese le differenze.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---


# AEM Assets e AEM MediaLibrary a confronto {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager (AEM) Assets è parte integrante della piattaforma AEM. Questa integrazione è vista come un vantaggio importante per la AEM e assicura la coerenza nella gestione dei contenuti e un&#39;elevata produttività per gli autori dei contenuti.

## Domande frequenti {#frequently-asked-questions}

### Cos&#39;è  AEM Assets? {#what-is-aem-assets}

 AEM Assets è un&#39;applicazione della piattaforma AEM che consente ai clienti di gestire le proprie risorse digitali (immagini, video, documenti e clip audio) in un archivio basato su Web.  AEM Assets include il supporto per metadati, rappresentazioni, il Finder di gestione delle risorse digitali e l&#39;interfaccia utente  di amministrazione AEM Assets.

### Cos&#39;è la AEM Media Library? {#what-is-the-aem-media-library}

AEM Media Library è una parte designata dell&#39;archivio di contenuti WCM AEM in cui vengono memorizzate le immagini e altre risorse condivise. La libreria Media utilizza le funzionalità di gestione delle risorse digitali di AEM WCM.

### Cosa si ottiene da  AEM Assets che non fa parte di AEM WCM? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Le funzioni uniche disponibili solo per  clienti di AEM Assets sono:

1. possibilità di estrarre e modificare metadati diversi da titolo, tag e descrizione.
1.  AEM Assets Admin, disponibile dalla schermata di benvenuto facendo clic sul secondo pulsante accanto a `siteadmin`.
1. Tutti i passaggi del flusso di lavoro relativi a Gestione delle risorse digitali, AEM l’assimilazione delle risorse,  l’eliminazione di AEM Assets,  gestione delle risorse secondarie AEM Assets,  l’estrazione dei metadati AEM Assets.
1. librerie, incluso lo spazio del pacchetto `dam` im.

L&#39;utilizzo di queste funzioni richiede una licenza valida di  AEM Assets.

###  AEM Assets è disponibile come pacchetto separato? {#is-aem-assets-available-as-a-separate-package}

No. Per semplificare l&#39;installazione e la distribuzione, tutte AEM applicazioni e componenti aggiuntivi vengono distribuiti in un unico pacchetto con tutte le funzionalità incluse. Ciò non implica che si disponga dell&#39;autorizzazione per utilizzare tutte le funzioni del pacchetto.

#### Desidero modificare i metadati delle risorse digitali. Ho bisogno  AEM Assets? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Se intendete modificare metadati diversi da titolo, descrizione e tag, è necessario disporre della licenza per  AEM Assets.

#### È possibile ridimensionare automaticamente le immagini al momento dell&#39;importazione. Ho bisogno  AEM Assets? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

No. Il ridimensionamento e la trasformazione automatica basata sul flusso di lavoro delle immagini statiche e la possibilità di gestire le rappresentazioni fanno parte AEM Media Library. Queste funzioni non richiedono una licenza AEM Assets .

### Voglio ridimensionare le immagini utilizzando un componente immagine personalizzato. Ho bisogno  AEM Assets? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

Il componente immagine fa parte di AEM WCM. La libreria grafica utilizzata dal componente immagine (ma anche da  AEM Assets) fa parte della piattaforma AEM e non richiede una licenza  AEM Assets.

### Come posso impedire ai miei utenti di utilizzare  AEM Assets se non ho ottenuto la licenza  AEM Assets? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

Puoi rimuovere da AEM tutti  flussi di lavoro, componenti, tassonomie, opzioni specifici di AEM Assets e l’amministratore  AEM Assets. In questo modo si evita che gli utenti utilizzino accidentalmente  funzioni AEM Assets che non erano in licenza.

### Desidero aggiungere delle immagini a una pagina e ritagliarle e ridimensionarle. Ho bisogno  AEM Assets? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

Per questo caso d’uso non è necessario acquistare  AEM Assets, anche l’utilizzo di Media Library non è richiesto per utilizzare immagini su un sito Web, in quanto il componente per immagini intelligenti consente di caricare le immagini direttamente nella pagina.

>[!MORELIKETHIS]
>
>* [Elenco dettagliato delle differenze tra le funzioni](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)

