---
title: Prova di frammenti di contenuto in We.Retail
seo-title: Trying out Content Fragments in We.Retail
description: Prova di frammenti di contenuto in We.Retail
seo-description: null
uuid: 66daddfe-8e98-47b6-8499-db055887ac17
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d1326737-f378-46d0-9916-61ead4d31639
exl-id: d93bec03-c651-4329-b220-4ac1ea189de1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 18%

---

# Prova di frammenti di contenuto in We.Retail{#trying-out-content-fragments-in-we-retail}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I Frammenti di contenuto consentono di creare contenuto versatile utilizzabile in qualsiasi canale, con possibili varianti per canali specifici. **We.Retail** (come disponibile in un’istanza standard di AEM) fornisce il frammento **Surf artico a Lofoten** come campione di base. Ciò illustra quanto segue:

* I frammenti di contenuto di Adobe Experience Manager (AEM) vengono [creati e gestiti come risorse indipendenti dalla pagina](/help/assets/content-fragments.md). Consentono di creare contenuti neutri per il canale, insieme a varianti (eventualmente specifiche per il canale).

   * Vedi [Dove trovare le risorse dei frammenti di contenuto in We.Retail](#where-to-find-content-fragments-in-we-retail)

* È quindi possibile [durante l’authoring, utilizza questi frammenti e le relative varianti](/help/sites-authoring/content-fragments.md) le pagine dei contenuti.

   * Vedi [Dove i frammenti di contenuto vengono utilizzati in We.Retail](#where-content-fragments-are-used-in-we-retail)

Per la documentazione completa sulla creazione, la gestione, l’utilizzo e lo sviluppo di frammenti di contenuto, consulta:

* Vedi [Ulteriori informazioni](#further-information)

>[!NOTE]
>
>I **frammenti di contenuto** e i **[frammenti di esperienza](/help/sites-authoring/experience-fragments.md)** sono funzioni diverse in AEM:
>
>* **Frammenti di contenuto** sono contenuti editoriali, principalmente testo e immagini correlate. Sono contenuti puri, senza design e layout.
>* I **frammenti di esperienza** sono contenuti completi di layout, frammenti di una pagina web.
>
>I frammenti esperienza possono includere contenuti sotto forma di frammenti di contenuto, ma non viceversa.

## Dove trovare frammenti di contenuto in We.Retail {#where-to-find-content-fragments-in-we-retail}

Ci sono diversi frammenti di contenuto di esempio in We.Retail; naviga via **Risorse**, **File**, **We.Retail**, **Inglese**, **Esperienze**.

Questi includono: **Surf artico a Lofoten**, un frammento insieme alle relative risorse visive:

* Passa a **Risorse**, **File**, **We.Retail**, **Inglese**, **Esperienze**, **Surf artico a Lofoten**:

   * [http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)

![cf-44](assets/cf-44.png)

Puoi selezionare e modificare il **Surf artico a Lofoten** frammento:

* [http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten](http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten)

Qui puoi [modifica e gestione](/help/assets/content-fragments.md) il frammento utilizzando le schede (pannello laterale sinistro):

![](do-not-localize/cf-45-aa.png) ![](do-not-localize/cf-45-a.png)

* **[Variazioni](/help/assets/content-fragments-variations.md)** compreso [Markdown](/help/assets/content-fragments-markdown.md)

* **[Contenuto associato](/help/assets/content-fragments-assoc-content.md)**
* **[Metadati](/help/assets/content-fragments-metadata.md)**

![cf-46](assets/cf-46.png)

## Dove i frammenti di contenuto vengono utilizzati in We.Retail {#where-content-fragments-are-used-in-we-retail}

Per illustrare [authoring di pagine con un frammento di contenuto](/help/sites-authoring/content-fragments.md) sono disponibili diversi esempi di pagine forniti in, ad esempio:

* [http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience](http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience)

Ad esempio, il **Surf artico a Lofoten** nella pagina Sites è presente un riferimento al frammento di contenuto:

* Passa a **Sites**, **We.Retail**, **Master per lingua**, **Inglese**, **Esperienza**. Quindi apri **Surf artico a Lofoten** per la modifica:

   * [http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html)

![cf-53](assets/cf-53.png)

## Ulteriori informazioni {#further-information}

Per maggiori dettagli vedi:

* [Utilizzo di frammenti di contenuto](/help/assets/content-fragments.md)

   * Scopri come creare, modificare e gestire le risorse dei frammenti di contenuto.

* [Authoring delle pagine con frammenti di contenuto](/help/sites-authoring/content-fragments.md)

   * Utilizza il frammento di contenuto durante la creazione di una pagina.

* [Sviluppo di AEM - Componenti per frammenti di contenuto](/help/sites-developing/components-content-fragments.md)

   * Panoramica dei componenti per frammenti di contenuto.

* [Sviluppo ed estensione di frammenti di contenuto](/help/sites-developing/customizing-content-fragments.md)

   * Informazioni utili per sviluppare ed estendere i frammenti di contenuto.
