---
title: Authoring - Ambiente e strumenti
seo-title: Authoring - the Environment and Tools
description: La console Siti web consente di gestire il sito web e navigare al suo interno. Tramite due riquadri, è possibile espandere la struttura del sito web e intervenire sugli elementi richiesti.
seo-description: The Websites console allows you to manage and navigate your website. Using two panes, the structure of your website can be expanded and actions taken on the required elements.
uuid: ec4ccc63-a3b8-464c-9c1a-204fd5d3b121
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 278195a6-3452-4966-9d56-022815cf6fb4
exl-id: f073c876-94cd-405d-885f-bfe433817ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 8%

---

# Authoring - Ambiente e strumenti{#authoring-the-environment-and-tools}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’ambiente di authoring di AEM offre diversi metodi per organizzare e modificare i contenuti. Gli strumenti disponibili sono accessibili da varie console ed editor di pagina.

## Amministrazione del sito {#site-administration}

La **Siti Web** la console consente di gestire il sito web e navigare al suo interno. Utilizzando i due riquadri è possibile espandere la struttura del sito web e intervenire sull’elemento richiesto:

![chlimage_1-153](assets/chlimage_1-153.png)

## Modifica del contenuto della pagina {#editing-your-page-content}

È disponibile un editor di pagine separato con l’interfaccia classica, utilizzando Content Finder e barra laterale:

`http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

![chlimage_1-154](assets/chlimage_1-154.png)

## Accedere all’Aiuto   {#accessing-help}

Varie **Aiuto** è possibile accedere direttamente alle risorse da AEM:

nonché l&#39;accesso [Aiuto dalle barre degli strumenti della console](/help/sites-classic-ui-authoring/author-env-basic-handling.md#accessing-help), è inoltre possibile accedere all’Aiuto dalla barra laterale (utilizzando l’ ? durante la modifica di una pagina:

![](do-not-localize/sidekick-collapsed-2.png)

Oppure utilizzando la **Aiuto** nella finestra di dialogo di modifica di componenti specifici; questo mostrerà la guida sensibile al contesto.

## Barra laterale {#sidekick}

La **Componenti** La scheda della barra laterale consente di scorrere i componenti disponibili per essere aggiunti alla pagina corrente. È possibile espandere il gruppo richiesto e quindi trascinare un componente nella posizione desiderata sulla pagina.

![chlimage_1-155](assets/chlimage_1-155.png)

## Content Finder {#the-content-finder}

Content Finder è un modo rapido e semplice per trovare risorse e/o contenuti all’interno dell’archivio durante la modifica di una pagina.

È possibile utilizzare Content Finder per individuare una serie di risorse. Se appropriato, puoi trascinare un elemento e rilasciarlo in un paragrafo sulla pagina:

* [Immagini](#finding-images)
* [Documenti](#finding-documents)
* [Filmati](#finding-movies)
* [Browser Dynamic Media](/help/sites-administering/scene7.md#scene7contentbrowser)
* [Pagine](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#finding-pages)
* [Paragrafi](#referencing-paragraphs-from-other-pages)
* [Prodotti](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#products)
* Oppure [sfogliare il sito web in base alla struttura dell’archivio](#the-content-finder)

Con tutte le opzioni è possibile [cercare elementi specifici](#the-content-finder).

### Ricerca di immagini {#finding-images}

In questa scheda vengono elencate tutte le immagini presenti nella directory archivio.

Dopo aver creato un paragrafo Immagine sulla pagina, puoi trascinarvi un elemento.

![chlimage_1-156](assets/chlimage_1-156.png)

### Ricerca di documenti {#finding-documents}

In questa scheda vengono elencati tutti i documenti presenti nella directory archivio.

Dopo aver creato un paragrafo Scarica sulla pagina, puoi trascinare un elemento nel paragrafo.

![chlimage_1-157](assets/chlimage_1-157.png)

### Ricerca di filmati {#finding-movies}

In questa scheda vengono elencati tutti i filmati (ad esempio, elementi Flash) presenti nella directory archivio.

Dopo aver creato sulla pagina un paragrafo appropriato (ad esempio, Flash), puoi trascinare un elemento nel paragrafo.

![chlimage_1-158](assets/chlimage_1-158.png)

### Prodotti {#products}

In questa scheda vengono elencati tutti i prodotti. Dopo aver creato sulla pagina un paragrafo appropriato (ad esempio, Prodotto), puoi trascinare un elemento nel paragrafo.

![chlimage_1-159](assets/chlimage_1-159.png)

### Ricerca di pagine {#finding-pages}

Questa scheda mostra tutte le pagine. Fai doppio clic su una pagina per aprirla in modalità di modifica.

![chlimage_1-160](assets/chlimage_1-160.png)

### Riferimento a paragrafi da altre pagine {#referencing-paragraphs-from-other-pages}

Questa scheda ti consente di cercare un’altra pagina. Vengono elencati tutti i paragrafi presenti nella pagina. È quindi possibile trascinare un paragrafo nella pagina corrente, in modo da creare un riferimento al paragrafo originale.

![chlimage_1-161](assets/chlimage_1-161.png)

### Utilizzo della vista Repository completa {#using-the-full-repository-view}

In questa scheda vengono visualizzate tutte le risorse presenti nella directory archivio.

![chlimage_1-162](assets/chlimage_1-162.png)

### Utilizzo della ricerca con il browser dei contenuti {#using-search-with-the-content-browser}

Per tutte le opzioni è possibile cercare elementi specifici. Vengono elencati tutti i tag e le risorse corrispondenti al pattern di ricerca:

![screen_shot_2012-02-08at100746am](assets/screen_shot_2012-02-08at100746am.png)

Puoi anche utilizzare i caratteri jolly per la ricerca. I caratteri jolly supportati sono:

* `*` - corrisponde a una sequenza di zero o più caratteri.

* `?` - corrisponde a un singolo carattere.

>[!NOTE]
>
>È necessario utilizzare una pseudo proprietà &quot;name&quot; per eseguire una ricerca con caratteri jolly.

Ad esempio, se è disponibile un’immagine con il nome:

`ad-nmvtis.jpg`

lo troveranno i seguenti pattern di ricerca (e tutte le altre immagini che corrispondono al pattern):

* `name:*nmv*`
* `name:AD*` - la corrispondenza dei caratteri è *not* sensibile a maiuscole e minuscole.
* `name:ad?nm??is.*` - è possibile utilizzare un numero qualsiasi di caratteri jolly in una query.

>[!NOTE]
>
>È inoltre possibile utilizzare [SQL2](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/commons/query/sql2/package-summary.html) ricerca.

## Visualizzazione dei riferimenti {#showing-references}

AEM consente di visualizzare le pagine collegate alla pagina su cui si sta lavorando.

Per visualizzare i riferimenti diretti alle pagine:

1. Nella barra laterale, seleziona la **Pagina** icona della scheda .

   ![screen_shot_2012-02-16at83127pm](assets/screen_shot_2012-02-16at83127pm.png)

1. Seleziona **Mostra riferimenti...** AEM apre la finestra Riferimenti e visualizza le pagine che fanno riferimento a quella selezionata, complete di percorso.

   ![screen_shot_2012-02-16at83311pm](assets/screen_shot_2012-02-16at83311pm.png)

In alcune situazioni sono disponibili ulteriori azioni dalla barra laterale, tra cui:

* [Lanci](/help/sites-classic-ui-authoring/classic-launches.md)
* [Live Copy](/help/sites-administering/msm.md)

* [Blueprint](/help/sites-administering/msm-best-practices.md)

Altro [Le relazioni tra pagine sono visibili nella console Siti web](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console).

## Registro di controllo {#audit-log}

La **Registro di controllo** accessibile dal **Informazioni** scheda della barra laterale. elenca le azioni recenti intraprese sulla pagina corrente; ad esempio:

![chlimage_1-163](assets/chlimage_1-163.png)

## Informazioni sulle pagine {#page-information}

Anche la console Siti Web [fornisce informazioni sullo stato corrente della pagina](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) come pubblicazione, modifica, blocco, Live Copy, ecc.

## Modalità pagina   {#page-modes}

Quando modifichi una pagina nell’interfaccia classica, è possibile accedere a diverse modalità mediante le icone nella parte inferiore della barra laterale:

![](do-not-localize/chlimage_1-15.png)

La riga di icone nella parte inferiore della barra laterale consente di cambiare la modalità di utilizzo delle pagine:

* [Modifica](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md)

   Questa è la modalità predefinita e consente di modificare la pagina, aggiungere o eliminare componenti e apportare altre modifiche.

* [Anteprima](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#previewing-pages)

   Questa modalità consente di visualizzare un’anteprima della pagina, così come apparirà sul sito web nella sua forma finale.

* [Design](/help/sites-classic-ui-authoring/classic-page-author-design-mode.md#main-pars-procedure-0)

   In questa modalità, puoi modificare la progettazione della pagina configurando i componenti accessibili.

>[!NOTE]
>
>Sono disponibili anche altre opzioni:
>
>* [Scaffolding](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md)
>* [ClientContext](/help/sites-administering/client-context.md)
>* Siti web : consente di aprire la console Siti web .
>* Ricarica - aggiorna la pagina.


## Scelte rapide da tastiera {#keyboard-shortcuts}

Sono disponibili alcune [scelte rapide da tastiera](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md).
