---
title: Sviluppo e Page Diff
seo-title: Sviluppo e Page Diff
description: 'null'
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 6de5e6f12f123ca2ec45358a138becc410c89e4e
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 7%

---


# Sviluppo e Page Diff{#developing-and-page-diff}

## Panoramica delle funzioni {#feature-overview}

La creazione di contenuti è un processo iterativo. Per un authoring efficace, è necessario essere in grado di vedere cosa è cambiato da un’iterazione all’altro. La visualizzazione separata di due versioni di una pagina è inefficiente e soggetta a errori. Un autore desidera poter confrontare la pagina corrente con una versione precedente, affiancando le differenze evidenziate.

Le differenze di pagina consentono a un utente di confrontare la pagina corrente con gli avvii, le versioni precedenti e così via. Per informazioni dettagliate su questa funzione utente, vedere [Page Diff](/help/sites-authoring/page-diff.md).

## Dettagli operazione {#operation-details}

Quando si confrontano le versioni di una pagina, la versione precedente che l&#39;utente desidera confrontare viene ricreata AEM in background per facilitare la diff. Questo è necessario per poter eseguire il rendering del contenuto [per il confronto affiancato](/help/sites-authoring/page-diff.md#presentation-of-differences).

Questa operazione di ricreazione viene eseguita da AEM internamente ed è trasparente per l&#39;utente e non richiede alcun intervento. Tuttavia, un amministratore che visualizza l&#39;archivio, ad esempio in CRX DE Lite, visualizzerà queste versioni ricreato all&#39;interno della struttura del contenuto.

A seconda del livello della patch AEM, il comportamento è diverso e può richiedere determinate autorizzazioni per funzionare correttamente.

### Prima della AEM 6.4.3 {#prior-to-aem}

Quando si confronta il contenuto, l&#39;intera struttura fino alla pagina da confrontare viene ricreata nel seguente percorso:

`/content/versionhistory/<userId>/<site structure>`

Poiché quando si utilizza il meccanismo delle differenze di pagina, AEM ricreare la versione precedente della pagina, per utilizzare la funzione l&#39;utente deve disporre di determinate autorizzazioni JCR.

>[!CAUTION]
>
>Per utilizzare la funzione diff pagina, l&#39;utente deve disporre dell&#39;autorizzazione **Modifica/Crea/Elimina** sul nodo `/content/versionhistory`.

### A partire dal AEM 6.4.3 {#as-of-aem}

Quando si confronta il contenuto, l&#39;intera struttura fino alla pagina da confrontare viene ricreata nel seguente percorso:

`/tmp/versionhistory/`

Questo contenuto viene creato da un utente di servizi con autorizzazioni che limitano la visibilità all’utente corrente. Per questo motivo, non sono richieste autorizzazioni speciali.

Un&#39;attività di pulizia viene eseguita automaticamente per ripulire il contenuto temporaneo.

## Limitazioni per sviluppatori {#developer-limitations}

Precedentemente, nell&#39;interfaccia classica, era necessario prestare particolare attenzione allo sviluppo per facilitare la AEM diffusione (ad esempio per utilizzare la funzione `cq:text` tag lib o per integrare il servizio `DiffService` OSGi nei componenti). Questo non è più necessario per la nuova funzione diff, poiché la diff si verifica sul lato client tramite il confronto DOM.

Tuttavia, lo sviluppatore deve tenere in considerazione una serie di limitazioni.

* Questa funzione utilizza classi CSS che non hanno un nome con spazio sul prodotto AEM. Se nella pagina sono incluse altre classi CSS personalizzate o classi CSS di terze parti con gli stessi nomi, la visualizzazione della diff potrebbe essere interessata.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Poiché la diff è lato client ed è eseguita al caricamento della pagina, eventuali modifiche al DOM dopo l&#39;esecuzione del servizio diff lato client non verranno prese in considerazione. Ciò può incidere

   * Componenti che utilizzano AJAX per includere il contenuto
   * Applicazioni a pagina singola
   * Componenti basati su JavaScript che modificano il DOM in base all’interazione dell’utente.

