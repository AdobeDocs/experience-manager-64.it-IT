---
title: Sviluppo e differenze tra pagine
seo-title: Sviluppo e differenze tra pagine
description: Sviluppo e differenze tra pagine
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 8%

---


# Sviluppo e differenze tra pagine{#developing-and-page-diff}

## Panoramica delle funzioni {#feature-overview}

La creazione di contenuti è un processo iterativo. Per un authoring efficace, è necessario essere in grado di vedere cosa è cambiato da un’iterazione all’altro. La visualizzazione separata di due versioni di una pagina è inefficiente e soggetta a errori. Un autore desidera poter confrontare la pagina corrente con una versione precedente affiancata alle differenze evidenziate.

Le differenze tra pagine consentono a un utente di confrontare la pagina corrente con gli avvii, le versioni precedenti e così via. Per informazioni dettagliate su questa funzione utente, consulta [Page Diff](/help/sites-authoring/page-diff.md).

## Dettagli operazione {#operation-details}

Quando si confrontano le versioni di una pagina, la versione precedente che l’utente desidera confrontare viene ricreata da AEM in background per facilitare le differenze. È necessario per poter eseguire il rendering del contenuto [per un confronto affiancato](/help/sites-authoring/page-diff.md#presentation-of-differences).

Questa operazione di ricreazione viene eseguita da AEM internamente ed è trasparente per l&#39;utente e non richiede alcun intervento. Tuttavia, un amministratore che visualizza l’archivio, ad esempio in CRX DE Lite, vedrebbe queste versioni ricreati all’interno della struttura del contenuto.

A seconda del livello di patch AEM, il comportamento è diverso e può richiedere alcune autorizzazioni per funzionare correttamente.

### Prima di AEM 6.4.3 {#prior-to-aem}

Quando si confronta il contenuto, l’intera struttura fino alla pagina da confrontare viene ricreata nella posizione seguente:

`/content/versionhistory/<userId>/<site structure>`

Poiché quando si utilizza il meccanismo di differenze tra pagine, AEM ricrea la versione precedente della pagina, per utilizzare la funzione l’utente deve disporre di determinate autorizzazioni JCR.

>[!CAUTION]
>
>Per utilizzare la funzione differenze tra pagine, l&#39;utente deve disporre dell&#39;autorizzazione **Modifica/Crea/Elimina** sul nodo `/content/versionhistory`.

### A partire da AEM 6.4.3 {#as-of-aem}

Quando si confronta il contenuto, l’intera struttura fino alla pagina da confrontare viene ricreata nella posizione seguente:

`/tmp/versionhistory/`

Questo contenuto viene creato da un utente di servizio con autorizzazioni che limitano la visibilità all&#39;utente corrente. Per questo motivo non sono necessarie autorizzazioni speciali.

Un’attività di pulizia viene eseguita automaticamente per pulire questo contenuto temporaneo.

## Limitazioni per sviluppatori {#developer-limitations}

In precedenza, nell’interfaccia classica, era necessario prestare particolare attenzione allo sviluppo per facilitare la diffusione AEM (ad esempio, per usare la libreria di tag `cq:text` o per integrare il servizio `DiffService` OSGi nei componenti). Questa funzione non è più necessaria per la nuova funzione di confronto delle differenze, in quanto si verifica sul lato client tramite il confronto DOM.

Tuttavia, lo sviluppatore deve tenere in considerazione una serie di limitazioni.

* Questa funzione utilizza classi CSS che non hanno nomi separati nel Prodotto AEM. Se nella pagina sono incluse altre classi CSS personalizzate o classi CSS di terze parti con gli stessi nomi, la visualizzazione del confronto potrebbe essere interessata.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Poiché la differenza è lato client ed è eseguita al caricamento della pagina, non verranno prese in considerazione eventuali modifiche al DOM dopo l’esecuzione del servizio di diff lato client. Ciò può influire

   * Componenti che utilizzano AJAX per includere contenuti
   * Applicazioni a pagina singola
   * Componenti basati su JavaScript che manipolano il DOM in base all’interazione dell’utente.

