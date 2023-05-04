---
title: Nozioni di base sui componenti di Communities
seo-title: Communities Components Basics
description: Aggiungere funzionalità di Communities AEM siti in modalità di modifica e configurare componenti
seo-description: Add Communities features to AEM sites in edit mode and configure components
uuid: c017a7c5-40d1-4592-9317-96fd727dac86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 21714581-7645-4b47-a9b0-9f1424013240
exl-id: 17fbee1c-5657-442a-8c9d-1456b853f666
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 4%

---

# Nozioni di base sui componenti di Communities {#communities-components-basics}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

La sezione authoring della documentazione descrive l’aggiunta delle funzioni di Communities ai siti AEM in modalità di modifica dell’autore e descrive le configurazioni dei componenti.

I componenti possono essere esplorati utilizzando un’istanza AEM e interattivi [Guida ai componenti della community](components-guide.md).

## Accesso ai componenti di Communities {#accessing-communities-components}

Durante la creazione del contenuto di una pagina, se il modello sottostante consente di apportare modifiche alla progettazione della pagina, è possibile abilitare i componenti che non sono già disponibili nel browser Componenti come parte della progettazione del sito.

Sono elencati i componenti di Communities disponibili [qui](author-communities.md#available-communities-components).

>[!NOTE]
>
>Per informazioni generali sull’authoring, visualizzare il [guida rapida all’authoring delle pagine](../../help/sites-authoring/qg-page-authoring.md).
>
>Se non hai familiarità con AEM, consulta la documentazione su [trattamento di base](../../help/sites-authoring/basic-handling.md).

### Accesso alla modalità Progettazione {#entering-design-mode}

Se **Community** componente non trovato nel browser Componenti (barra laterale), sarà necessario inserire `Design Mode` per aggiungere altri componenti di Communities. [Librerie lato client richieste](#required-clientlibs) (clientlibs) può anche essere necessario aggiungere .

Per maggiori dettagli, vedi [Configurazione dei componenti in modalità Progettazione](../../help/sites-authoring/default-components-designmode.md).

Di seguito sono riportate le immagini che mostrano come selezionare alcuni componenti di Communities e visualizzarli nel browser Componenti:

![chlimage_1-424](assets/chlimage_1-424.png)

I componenti selezionati sono ora disponibili nel browser Componenti:

![chlimage_1-425](assets/chlimage_1-425.png)

## Clientlibs richiesti {#required-clientlibs}

[Librerie lato client](../../help/sites-developing/clientlibs.md) (clientlibs) sono necessari per il corretto funzionamento (JavaScript) e lo stile (CSS) di un componente.

Quando si aggiunge un componente Communities a una pagina, se il risultato è un errore o un aspetto imprevisto, la prima cosa da provare è l&#39;aggiunta delle clientlibs richieste per il componente Communities. Per maggiori dettagli, vedi [Componenti Clientlibs for Communities](clientlibs.md).

### Esempio: Recensioni iniziali senza librerie client... {#example-initially-placed-reviews-without-client-libraries}

![chlimage_1-426](assets/chlimage_1-426.png)

### ... E con le librerie client {#and-with-client-libraries}

![chlimage_1-427](assets/chlimage_1-427.png)

## Assegnazione dei tag {#tagging}

È possibile configurare molte funzioni di Communities per consentire ai membri di assegnare tag al contenuto immesso (pubblicato) nell’ambiente di pubblicazione.

Se l&#39;assegnazione tag è consentita, la configurazione del sito della community può essere impostata in modo da limitare i namespace presentati ai membri nell&#39;ambiente di pubblicazione. Consulta la sezione [Console Sites della community](sites-console.md#tagging).

Funzioni che consentono l’assegnazione tag: [blog](blog-feature.md), [calendario](calendar.md), [libreria file](file-library.md), [forum](forum.md)

Funzioni che utilizzano i tag: [catalogo](catalog.md), [ricerca](search.md), [social tag cloud](tagcloud.md)

Per informazioni sull’authoring:

* [Utilizzo dei tag](../../help/sites-authoring/tags.md)

Per informazioni amministrative:

* Creazione di spazi dei nomi dei tag (tassonomia): [Amministrazione dei tag](../../help/sites-administering/tags.md)
* Configurazione sito community: vedere [TAG](sites-console.md#tagging)
* [Assegnazione tag ai contenuti generati dagli utenti](../../help/sites-authoring/tags.md)
* [Risorse di abilitazione assegnazione tag](tag-resources.md)

Per informazioni sugli sviluppatori:

* [Framework di assegnazione tag AEM](../../help/sites-developing/framework.md)
* [Assegnazione tag di base](tag.md)
