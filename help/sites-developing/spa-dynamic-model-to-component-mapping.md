---
title: Mappatura dinamica da modello a componente per SPA
seo-title: Dynamic Model to Component Mapping for SPAs
description: Questo articolo descrive come avviene la mappatura del modello dinamico ai componenti nell'SDK Javascript SPA per AEM.
seo-description: This article describes how the dynamic model to component mapping occurs in the Javascript SPA SDK for AEM.
uuid: 337b8d90-efd7-442e-9fac-66c33cc26212
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 8b4b0afc-8534-4010-8f34-cb10475a8e79
exl-id: 2bbbfbaa-b0a1-4f8a-9445-51325d80e368
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 2%

---

# Mappatura dinamica da modello a componente per SPA{#dynamic-model-to-component-mapping-for-spas}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questo documento descrive come avviene la mappatura del modello dinamico ai componenti nell&#39;SDK Javascript SPA per AEM.

>[!NOTE]
>La funzione Editor applicazioni a pagina singola (SPA) richiede AEM service pack 2 o successivo 6.4.
>
>L’editor di SPA è la soluzione consigliata per i progetti che richiedono SPA rendering lato client basato su framework (ad esempio, React o Angular).

## Modulo di mappatura componenti {#componentmapping-module}

La `ComponentMapping` Il modulo viene fornito come pacchetto NPM al progetto front-end. Memorizza i componenti front-end e consente all’applicazione a pagina singola di mappare i componenti front-end sui tipi di risorse AEM. In questo modo si abilita una risoluzione dinamica dei componenti durante l’analisi del modello JSON dell’applicazione.

Ogni elemento presente nel modello contiene un `:type` campo che espone un tipo di risorsa AEM. Quando è montato, il componente front-end può renderizzarsi utilizzando il frammento di modello ricevuto dalle librerie sottostanti.

Fai riferimento alla [Blueprint SPA](/help/sites-developing/spa-blueprint.md) per ulteriori informazioni sull&#39;analisi dei modelli e sull&#39;accesso al modello dei componenti front-end.

Vedi anche il pacchetto npm: [https://www.npmjs.com/package/@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Applicazione a pagina singola basata su modello {#model-driven-single-page-application}

Le applicazioni a pagina singola che sfruttano l’SDK SPA Javascript per AEM sono basate su modelli:

1. I componenti front-end si registrano al [Archivio di mappatura dei componenti](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Quindi il [Contenitore](/help/sites-developing/spa-blueprint.md#container)una volta fornito con un modello [Provider di modelli](/help/sites-developing/spa-blueprint.md#the-model-provider), esegue iterazioni sul contenuto del modello ( `:items`).

1. Nel caso di una pagina, i relativi elementi secondari ( `:children`) per prima cosa, ottieni una classe di componente dal [Mappatura dei componenti](/help/sites-developing/spa-blueprint.md#componentmapping) e poi istanziarlo.

## Inizializzazione app {#app-initialization}

Ogni componente viene esteso con le funzionalità del [ `ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider). L&#39;inizializzazione assume pertanto la seguente forma generale:

1. Ogni provider di modelli si inizializza e ascolta le modifiche apportate al pezzo di modello che corrisponde al suo componente interno.
1. La [ `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) deve essere inizializzato come rappresentato dal [flusso di inizializzazione](/help/sites-developing/spa-blueprint.md).

1. Una volta memorizzato, il gestore dei modelli di pagina restituisce il modello completo dell’app.
1. Questo modello viene quindi trasmesso alla radice front-end [Contenitore](/help/sites-developing/spa-blueprint.md#container) componente dell&#39;applicazione.
1. I pezzi del modello vengono infine propagati a ogni singolo componente figlio.

![app_model_initialize](assets/app_model_initialization.png)
