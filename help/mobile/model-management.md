---
title: Panoramica dei modelli
seo-title: Models Overview
description: Panoramica dei modelli
seo-description: null
uuid: e09dac52-9515-43f7-9d3b-6637e2283d59
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: c8281f98-9811-42f7-9a31-f82dd0f09319
exl-id: 03f06c10-9fe1-497e-89b0-70acb7ca7800
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 1%

---

# Panoramica dei modelli{#models-overview}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe consiglia di utilizzare l’editor di SPA per i progetti che richiedono il rendering lato client basato sul framework di un’applicazione a pagina singola (ad esempio, React). [Ulteriori informazioni](/help/sites-developing/spa-overview.md).

La gestione dei modelli comporta la creazione e la gestione di modelli allo scopo di associare a eventuali oggetti dati. Ogni modello include tutte le proprietà e le definizioni dei campi necessarie per facilitare la creazione e il rendering degli oggetti.

La gestione dei modelli prevede la creazione di **modelli**, **entità** e **spazi**. Il diagramma seguente illustra la relazione tra il contenuto AEM e i modelli.

![chlimage_1-81](assets/chlimage_1-81.png)

## Modello di contenuto {#the-content-model}

Un modello descrive il tipo di contenuto e indica quali informazioni saranno disponibili per l&#39;applicazione nativa. È una descrizione di ciò che costituisce un contenuto. Un modello di contenuto è la regola per creare un contenuto. Il modello di contenuto include i dati disponibili, le risorse utilizzabili, la relazione tra risorse e dati, la relazione con altri modelli di contenuto e i metadati disponibili.

I modelli servono anche come mezzo per trasformare i contenuti AEM esistenti in oggetti che possono essere facilmente utilizzati dalle app mobile native.

Content Services fornirà alcuni modelli predefiniti per oggetti comuni quali risorse, raccolte di risorse, pagine di HTML, configurazioni di app e pagine indipendenti dai canali. Questi saranno configurabili in modo da soddisfare esigenze specifiche dei clienti senza richiedere uno sforzo di sviluppo AEM.

L’utente può creare modelli personalizzati. Questo consente di creare nuovi tipi di contenuto che non sono già gestiti da AEM. La creazione di modelli viene eseguita tramite un’interfaccia utente che utilizza tipi di base esistenti.

Il diagramma seguente illustra il modello di contenuto per le app AEM Mobile e il modo in cui entità, cartelle e spazi vengono assegnati a un’app.

![chlimage_1-82](assets/chlimage_1-82.png)

### I modelli {#the-models}

I modelli vengono utilizzati per determinare come vengono create le entità. Definiscono ciò che è disponibile in un’entità e come tali dati vengono generati dal contenuto AEM. Prima di iniziare a utilizzare Spazi, Cartelle ed Entità, è necessario avere familiarità con la creazione e la gestione dei modelli.

>[!NOTE]
>
>Un modello esiste all&#39;esterno di un&#39;app in quanto più di un&#39;app può utilizzarlo.

Vedi **[Modelli](/help/mobile/administer-mobile-apps.md)** per creare e gestire modelli nel dashboard e nel repository.

### Entità nel modello di contenuto {#entities-in-content-model}

Un’entità è un’istanza di un modello di contenuto. Un’entità viene esposta tramite l’API Content Services alla libreria lato client e fornisce un modo per un’app nativa di accedere ai contenuti in modo indipendente dal canale.

Nel caso di contenuto AEM esistente, un’entità viene generata utilizzando un modello e l’origine di contenuto AEM. Ad esempio, un’entità pagina è un oggetto indipendente dal canale e dal layout generato da una pagina AEM e dal modello di pagina.

Le modifiche al contenuto di riferimento di un’entità determineranno una modifica dell’entità. Ad esempio, se un *cq:page* viene aggiornato, verranno aggiornate anche tutte le entità basate su tale pagina.

Vedi **[Utilizzo delle entità](/help/mobile/spaces-and-entities.md)** per creare entità personalizzate dai modelli.

>[!NOTE]
>
>Se il modello non corrisponde a un contenuto AEM esistente, ad esempio il cliente ha creato un nuovo modello, sarà disponibile un’interfaccia utente che consente al cliente di creare una nuova entità.

### Spazi nel modello di contenuto {#spaces-in-content-model}

Uno spazio viene utilizzato per organizzare le entità per un facile accesso. Uno spazio può contenere uno o più tipi di entità e può contenere sottocartelle.

Sul lato AEM, uno spazio è un modo conveniente per gestire le entità correlate. Può essere utilizzato anche per assegnare le autorizzazioni di autorizzazione. È possibile autorizzare uno spazio, in modo da proteggere le entità che si trovano in tale spazio.

*Ad esempio*,

Un utente dispone di tre classificazioni generali di entità. Uno è solo per uso interno, un altro è approvato per uso pubblico e ancora un terzo è per le entità comuni che sono utilizzati da molte app. Per semplificare la gestione, l&#39;utente crea tre spazi, ovvero *interno*, *pubblico* (con contenuto sia inglese che francese), e *comune* per la gestione delle entità appropriate come indicato di seguito:

* /content/entity/internal
* /content/entity/public/it
* /content/entity/public/fr
* /content/entity/common

Verrà fornito un punto finale del servizio allo spazio in modo che la libreria client nativa possa richiedere un elenco dei contenuti di uno spazio. Questo &quot;elenco&quot; verrà restituito come oggetto JSON.

Vedi **[Spazi ed entità](/help/mobile/spaces-and-entities.md)** per la creazione e la pubblicazione di spazi.

>[!NOTE]
>
>Uno spazio può essere utilizzato da molte app e un&#39;app può utilizzare molti spazi.

### Cartelle nel modello di contenuto {#folders-in-content-model}

Le cartelle consentono agli utenti di organizzare le entità come richiesto e facilita un controllo ACL più preciso. Gli spazi possono includere cartelle per organizzare ulteriormente il contenuto e le risorse dello spazio. Un utente può creare una propria gerarchia sotto uno spazio.

Vedi **[Utilizzo delle cartelle in uno spazio](/help/mobile/spaces-and-entities.md)** per creare e gestire cartelle all’interno di uno spazio.
