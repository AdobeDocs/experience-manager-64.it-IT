---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: Guida utente allo sviluppo in AEM 6.4
breadcrumb-title: Guida allo sviluppo
user-guide-description: Questa guida illustra come creare l’istanza AEM.
feature: Developing
role: Developer
hide: true
source-git-commit: b61797a9096c0473658d6aabfb584a53e42095b7
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 25%

---


# Guida utente allo sviluppo in AEM 6.4 {#developing}

+ [Panoramica sullo sviluppo della Guida utente](home.md)
+ Introduzione per sviluppatori{#introduction}
   + [Guida introduttiva allo sviluppo per AEM Sites - Esercitazione WKND](getting-started.md)
   + [AEM Concetti di base](the-basics.md)
   + [Struttura dell’interfaccia utente AEM touch](touch-ui-structure.md)
   + [Concetti dell’interfaccia AEM touch](touch-ui-concepts.md)
   + [Sviluppo AEM - Linee guida e best practice](dev-guidelines-bestpractices.md)
   + [Utilizzo delle librerie lato client](clientlibs.md)
   + [Sviluppo e differenze tra pagine](pagediff.md)
   + [Limitazioni per l’editor](editor-limitations.md)
   + [Quadro di riferimento per la protezione del CSRF](csrf-protection.md)
   + [Modellazione dei dati - Modello di David Nuescheler](model-data.md)
   + [Contribuire a AEM](contributing-to-cq.md)
   + [Sicurezza](security.md)
   + [Materiali di riferimento](reference-materials.md)
   + [Creare un sito web completo (interfaccia classica)](website.md)
   + [Progettazioni e Designer (interfaccia classica)](designer.md)
+ Platform{#platform}
   + [Guida di riferimento rapido per Sling](sling-cheatsheet.md)
   + [Utilizzo di adattatori Sling](sling-adapters.md)
   + [Librerie di tag](taglib.md)
   + Modelli{#templates}
      + [Modelli](templates.md)
      + [Modelli di pagina - Modificabili ](page-templates-editable.md)
      + [Modelli di pagina - Statici](page-templates-static.md)
      + [Modelli per frammenti di contenuto](content-fragment-templates.md)
      + [Rendering di modelli adattivi](templates-adaptive-rendering.md)
   + [Utilizzo di Sling Resource Merger in AEM](sling-resource-merger.md)
   + [Sovrapposizioni](overlays.md)
   + [Convenzioni di denominazione](naming-conventions.md)
   + [Creazione di un nuovo componente campo dell’interfaccia Granite](granite-ui-component.md)
   + Query Builder{#query-builder}
      + [Implementazione di un valutatore del predicato personalizzato per il Generatore di query](implementing-custom-predicate-evaluator.md)
      + [Riferimento predicato di Query Builder](querybuilder-predicate-reference.md)
      + [API Query Builder](querybuilder-api.md)
   + Assegnazione dei tag{#tagging}
      + [Assegnazione dei tag](tags.md)
      + [Framework di assegnazione tag AEM](framework.md)
      + [Creazione di tag in un’applicazione AEM](building.md)
   + [Personalizzazione delle pagine mostrate dal gestore errori](customizing-errorhandler-pages.md)
   + [Tipi di nodo personalizzati](custom-nodetypes.md)
   + [Aggiunta di font al rendering grafico](adding-fonts.md)
   + [Connessione ai database SQL](jdbc.md)
   + [Esternalizzazione degli URL](externalizer.md)
   + [Creazione e consumo di processi per lo scaricamento](dev-offloading.md)
   + [Configurazione dell’utilizzo dei cookie](cookie-optout.md)
   + [Come accedere programmaticamente a AEM JCR](access-jcr.md)
   + [Integrazione dei servizi con la console JMX](jmx-integration.md)
   + [Sviluppo dell’editor in blocco](dev-bulk-editor.md)
   + [Sviluppo di rapporti](dev-reports.md)
   + eCommerce{#ecommerce}
      + [eCommerce](ecommerce.md)
      + [Sviluppo (generico)](generic.md)
      + [Sviluppo con SAP Commerce Cloud](sap-commerce-cloud.md)
+ Componenti{#components}
   + [Componenti core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=it)
   + [Sistema di stili](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/siteandpage/style-system.html)
   + [Panoramica dei componenti](components.md)
   + [Componenti AEM - Nozioni di base](components-basics.md)
   + [Sviluppo di componenti AEM](developing-components.md)
   + [Sviluppo di componenti AEM - Esempi di codice](developing-components-samples.md)
   + [Esportatore JSON per Content Services](json-exporter.md)
   + [Abilitazione dell’esportazione JSON per un componente](json-exporter-components.md)
   + [Editor immagine](image-editor.md)
   + [Tag di decorazione](decoration-tag.md)
   + [Utilizzo di Nascondi condizioni](hide-conditions.md)
   + [Configurazione di più editor in-place](multiple-inplace-editors.md)
   + [Modalità Sviluppatore](developer-mode.md)
   + [Verifica dell’interfaccia utente](hobbes.md)
   + [Componenti per frammenti di contenuto](components-content-fragments.md)
   + [Ottenimento di informazioni di pagina in formato JSON](pageinfo.md)
   + Internazionalizzazione{#internationalization}
      + [Componenti di internazionalizzazione](i18n.md)
      + [Internazionalizzazione delle stringhe di interfaccia utente](i18n-dev.md)
      + [Utilizzo di Translator per gestire i dizionari](i18n-translator.md)
      + [Estrazione di stringhe per la traduzione](i18n-extract.md)
   + Componenti dell’interfaccia classica{#classic-ui-components}
      + [Sviluppo di componenti AEM (interfaccia classica)](developing-components-classic.md)
      + [Utilizzo ed estensione dei widget (interfaccia classica)](widgets.md)
      + [Utilizzo di xtype (interfaccia classica)](xtypes.md)
      + [Sviluppo di Forms (interfaccia classica)](developing-forms.md)
+ Gestione delle esperienze headless{#headless}
   + [Senza testa e ibrido con AEM](https://business.adobe.com/content/dam/dx/us/en/products/experience-manager/sites/headless-content-management-system/pdfs/aem-hybrid-architecture-wp-1-18-19.pdf)
   + [Abilitazione dell’esportazione JSON per un componente](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/json-exporter-components.html)
   + Applicazioni a pagina singola{#spas}
      + [Introduzione a SPA e procedura dettagliata](spa-walkthrough.md)
      + [Tutorial WKND per SPA](spa-wknd.md)
      + [Guida introduttiva a SPA in AEM - React](spa-getting-started-react.md)
      + [Guida introduttiva a SPA in AEM - Angular](spa-getting-started-angular.md)
      + [Implementazione di un Componente React per applicazioni a pagina singola (SPA)](spa-implementing-react-component.md)
      + [Approfondimenti su SPA](spa-deep-dives.md)
      + [Panoramica dell’editor di SPA](spa-overview.md)
      + [Sviluppo di SPA per AEM](spa-architecture.md)
      + [Blueprint SPA](spa-blueprint.md)
      + [Componente pagina SPA](spa-page-component.md)
      + [Mappatura di un modello dinamico a un componente per SPA](spa-dynamic-model-to-component-mapping.md)
      + [Indirizzamento modello SPA](spa-routing.md)
      + [Integrazione di SPA e Adobe Experience Platform Launch](spa-launch.md)
      + [Rendering lato SPA e server](spa-ssr.md)
      + [Materiali di riferimento SPA](spa-reference-materials.md)
   + [API HTTP](https://experienceleague.adobe.com/docs/experience-manager-64/assets/extending/mac-api-assets.html)
   + [Frammenti di contenuto](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments.html)
   + [Frammenti esperienza](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/authoring/experience-fragments.html)
+ Strumenti di sviluppo{#devtools}
   + [Strumenti di sviluppo](dev-tools.md)
   + [Strumenti AEM Modernization Tools](modernization-tools.md)
   + [Editor finestre di dialogo](dialog-editor.md)
   + [Strumento di conversione finestra di dialogo](dialog-conversion.md)
   + [Sviluppo con CRXDE Lite](developing-with-crxde-lite.md)
   + [Gestione dei pacchetti con Maven](vlt-mavenplugin.md)
   + [Come sviluppare progetti AEM utilizzando Eclipse](howto-projects-eclipse.md)
   + [Come creare progetti AEM utilizzando Apache Maven](ht-projects-maven.md)
   + [Come sviluppare progetti AEM utilizzando IntelliJ IDEA](ht-intellij.md)
   + [Come utilizzare lo strumento VLT](ht-vlttool.md)
   + [Come utilizzare lo strumento Proxy Server](ht-proxy-server.md)
   + [Estensione Bracket AEM](aem-brackets.md)
   + [Strumenti AEM Developer per Eclipse](aem-eclipse.md)
   + [AEM Repo Tool](aem-repo-tool.md)
+ Personalizzazione{#personlization}
   + [ContextHub](contexthub.md)
   + [Riferimento API di ContextHub Javascript](contexthub-api.md)
   + [Estensione di ContextHub](ch-extend.md)
   + [Aggiunta di ContextHub alle pagine e accesso ai negozi](ch-adding.md)
   + [Candidati allo store ContextHub di esempio](ch-samplestores.md)
   + [Tipi di moduli di interfaccia utente ContextHub di esempio](ch-samplemodules.md)
   + [Diagnostica ContextHub](ch-diagnostics.md)
   + [Sviluppo per contenuti mirati](target.md)
   + ClientContext{#client-context}
      + [Contesto client in dettaglio](client-context.md)
      + [API JavaScript per il contesto client](ccjsapi.md)
+ Estensione AEM{#extending-aem}
   + [Personalizzazione dell’authoring delle pagine](customizing-page-authoring-touch.md)
   + [Personalizzazione delle console](customizing-consoles-touch.md)
   + [Personalizzazione delle visualizzazioni delle proprietà pagina](page-properties-views.md)
   + [Configurazione della pagina per la modifica in serie delle proprietà di pagina](bulk-editing.md)
   + [Personalizzazione ed estensione dei frammenti di contenuto](customizing-content-fragments.md)
   + Estensione dei flussi di lavoro{#extending-workflows}
      + [Sviluppo ed estensione dei flussi di lavoro](workflows.md)
      + [Creazione di modelli di flussi di lavoro](workflows-models.md)
      + [Estensione della funzionalità per flussi di lavoro](workflows-customizing-extending.md)
      + [Interazione con flussi di lavoro a livello di programmazione](workflows-program-interaction.md)
      + [Guida di riferimento per i passaggi dei flussi di lavoro](workflows-step-ref.md)
      + [Best practice per i flussi di lavoro](workflows-best-practices.md)
      + [Guida di riferimento per il processo dei flusso di lavoro](workflows-process-ref.md)
   + [Estensione di Multi Site Manager](extending-msm.md)
   + Tracciamento e analisi{#extending-analytics}
      + [Estensione del tracciamento degli eventi](extending-analytics.md)
      + [Aggiunta del tracciamento di Adobe Analytics ai componenti](extending-analytics-components.md)
      + [Personalizzazione del framework Adobe Analytics](extending-analytics-framework.md)
      + [Implementazione della denominazione delle pagine lato server per Analytics](extending-analytics-pa-naming.md)
   + Cloud Services{#extending-cloud-services}
      + [Configurazioni Cloud Service](extending-cloud-config.md)
      + [Creazione di un Cloud Service personalizzato](extending-cloud-config-custom-cloud.md)
   + [Creazione di estensioni personalizzate](extending-campaign-extensions.md)
   + Forms{#extending-forms}
      + [Creazione di mappature dei moduli personalizzate](extending-campaign-form-mapping.md)
      + [Creazione di un modello di pagina AEM personalizzato con i componenti del modulo Adobe Campaign](extending-campaign-custom-template.md)
      + [Script di analisi delle richieste](analyze-request.md)
   + [Integrazione dei servizi con la console JMX](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/jmx-integration.html)
   + [Sviluppo dell’editor in blocco](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-bulk-editor.html)
   + Estensione dell’interfaccia classica{#extending-classic-ui}
      + [Personalizzazione della console Siti web (interfaccia classica)](customizing-siteadmin.md)
      + [Personalizzazione della console di benvenuto (interfaccia classica)](customizing-the-welcome-console.md)
      + [Sviluppo di rapporti](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-reports.html)
+ Test{#testing}
   + [Pianificazione](planning.md)
   + [Quali ambienti di test saranno necessari?](test-environments.md)
   + [Definizione dei casi di test](test-cases.md)
   + [Test - quando e con chi?](when-who.md)
   + [Compilazione del piano di test](test-plan.md)
   + [Tracciamento dei risultati e fornitura di feedback](results-and-feedback.md)
   + [Strumenti di test e tracciamento](tools.md)
   + [Accettazione e cancellazione](acceptance-signoff.md)
   + [La prossima versione..](the-next-release.md)
   + [Elenchi di controllo](checklists.md)
   + [Giorno difficile](tough-day.md)
   + [Verifica dell’interfaccia utente](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/hobbes.html)
+ Best practice{#bestpractices}
   + [Panoramica delle best practice](best-practices.md)
   + [Linee guida per lo sviluppo AEM e best practice](https://experienceleague.adobe.com/docs/experience-manager-64/developing/introduction/dev-guidelines-bestpractices.html?lang=it)
   + [Tecniche consigliate per lo sviluppo](development-practices.md)
   + [Architettura dei contenuti](content-architecture.md)
   + [Architettura del software](software-architecture.md)
   + Implementazione di riferimento di We.Retail{#we-retail}
      + [Implementazione di riferimento di We.Retail](we-retail.md)
      + [Prova di frammenti di contenuto in We.Retail](we-retail-content-fragments.md)
      + [Prova dei componenti core in We.Retail](we-retail-core-components.md)
      + [Prova di modelli modificabili in We.Retail](we-retail-editable-templates.md)
      + [Layout reattivo in We.Retail](we-retail-responsive-layout.md)
      + [Prova la struttura del sito globale in We.Retail](we-retail-globalized-site-structure.md)
      + [Prova di frammenti esperienza in We.Retail](we-retail-experience-fragments.md)
   + [Suggerimenti sulla codifica](coding-tips.md)
   + [Problemi di codice](code-pitfalls.md)
   + [Bundle OSGI](osgi-bundles.md)
   + [Integrazione JCR](jcr-integration.md)
   + [Esempi di codice](code-samples.md)
   + [Risoluzione dei problemi relativi alle query lente](troubleshooting-slow-queries.md)
+ Web per dispositivi mobili{#mobileweb}
   + [Web per dispositivi mobili](mobile-web.md)
   + [Creazione di filtri per i gruppi di dispositivi](groupfilters.md)
   + [Progettazione reattiva per le pagine web](responsive.md)
   + [Creazione di siti per dispositivi mobili](mobile.md)
   + [Emulatori](emulators.md)

<!--
Deleted link to broken helpx video:
    + [Understanding Content Fragments and Content Services in AEM](https://helpx.adobe.com/experience-manager/kt/sites/using/content-fragments-content-services-feature-video-understand.html)
-->
