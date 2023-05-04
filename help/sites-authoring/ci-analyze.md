---
title: Analisi delle prestazioni della pagina
seo-title: Analyzing Page Performance
description: Utilizza la pagina Approfondimenti contenuto per analizzare le prestazioni della pagina che crei
seo-description: Use the Content Insight page to analyze the performance of the page that you are authoring
uuid: 6b8a489d-f262-495d-adff-125c9a2c49b9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: ead74e39-3b07-488e-aeb1-fcb4aa6ff200
exl-id: dc24edaf-ca1d-4a6b-a2dc-86677267e18d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 2%

---

# Analisi delle prestazioni della pagina{#analyzing-page-performance}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Apri [Approfondimenti contenuto](/help/sites-authoring/content-insights.md) per analizzare le prestazioni della pagina che si sta creando. Configura il periodo di reporting per attivare l’analisi.

## Apertura di Analytics e Recommendations per una pagina {#opening-analytics-and-recommendations-for-a-page}

Segui la procedura seguente per visualizzare Analytics e Recommendations per una pagina:

1. Passa alla pagina da analizzare.
1. Nella barra degli strumenti, tocca o fai clic su **Analytics e Recommendations**.

   >[!NOTE]
   >
   >Analytics e Recommendations per una pagina vengono visualizzati solo se hai configurato AEM a [integrare con Adobe Analytics](/help/sites-administering/adobeanalytics-connect.md).

   ![screen_shot_2017-11-29at135651](assets/screen_shot_2017-11-29at135651.png)

## Modifica del periodo di riferimento {#changing-the-reporting-period}

Modifica i seguenti aspetti temporali dei rapporti di analisi:

* Il periodo di tempo in cui effettuare la segnalazione.
* Granularità dei dati.

Gli strumenti per modificare gli aspetti temporali dei rapporti vengono visualizzati nella parte superiore della pagina Approfondimenti contenuto . ![chlimage_1-249](assets/chlimage_1-249.png)

### Modifica del periodo di riferimento {#changing-the-reporting-period-1}

Modifica il periodo di reporting della pagina Approfondimenti contenuto per impostare l’analisi dell’attività della pagina su un periodo di tempo specifico. Quando modifichi il periodo di riferimento, i rapporti vengono aggiornati automaticamente. L’area ombreggiata nell’intervallo temporale rappresenta il periodo di reporting. Le date dell’intervallo temporale aumentano da sinistra a destra.

![chlimage_1-250](assets/chlimage_1-250.png)

Per modificare il periodo di riferimento di una pagina Approfondimenti contenuto:

1. Se l’intervallo temporale non viene visualizzato nella parte superiore della pagina, tocca o fai clic sull’icona Attiva/Disattiva intervallo temporale .

   ![](do-not-localize/chlimage_1-22.png)

1. Per modificare la data di inizio del periodo di reporting, trascina il cerchio visualizzato sul lato sinistro dell’area ombreggiata fino alla data di inizio desiderata.

   Se non è possibile visualizzare il lato sinistro dell’area ombreggiata, utilizzare la barra di scorrimento per visualizzarla.

1. Per modificare la data di fine del periodo di reporting, trascina il cerchio visualizzato sul lato destro dell’area ombreggiata fino alla data di fine desiderata.

### Modifica della granularità del periodo di riferimento {#changing-the-granularity-of-the-reporting-period}

Modifica il tempo di estensione di ogni punto dati in un rapporto. Ad esempio, se è selezionata la granularità Settimana, ogni punto dati del rapporto Visualizzazioni rappresenta il numero di visualizzazioni per una settimana.

![screen_shot_2017-11-29at141001](assets/screen_shot_2017-11-29at141001.png)

La granularità influisce sui rapporti che tracciano i dati rispetto al tempo, come le visualizzazioni e la media di coinvolgimento della pagina in minuti. La granularità influisce anche sulla scala temporale.

1. Se il controllo di granularità non viene visualizzato, tocca o fai clic sull’icona Attiva/Disattiva granularità .

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Tocca o fai clic sulla granularità desiderata. Una volta selezionato, il rapporto si aggiorna automaticamente per riflettere la granularità.

## Assegnazione di attività per SEO Recommendations {#assigning-tasks-for-seo-recommendations}

Utilizza il rapporto SEO Recommendations per creare attività per migliorare la visibilità delle pagine nei motori di ricerca. Per ogni consiglio nel rapporto senza segno di spunta, potete creare un’attività da assegnare a un utente per eseguire il lavoro richiesto.

![chlimage_1-252](assets/chlimage_1-252.png)

Lo stato della raccomandazione SEO (Search Engine Optimization) indica quando l’attività viene creata ma non ancora completata.

![chlimage_1-253](assets/chlimage_1-253.png)

Quando viene creata, l’attività viene visualizzata nell’elenco Attività dell’utente. Per informazioni sulle attività, consulta [Utilizzo delle attività](/help/sites-authoring/task-content.md).

Segui la procedura seguente per creare un’attività per un consiglio SEO.

1. Tocca o fai clic sull’icona delle informazioni per il consiglio SEO.

   ![](do-not-localize/chlimage_1-23.png)

1. Fai clic sull’icona del triangolo circondato visualizzata accanto all’icona delle informazioni.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Compila i campi del modulo visualizzati e tocca Crea :

   * Progetto: Selezionare il progetto in cui creare l&#39;attività.
   * Nome: Nome che identifica l&#39;attività. Il nome predefinito è il titolo della raccomandazione SEO.
   * Assegna a: Selezionare l’utente a cui assegnare l’attività. Inizia a digitare il nome dell’utente per filtrare l’elenco.
   * Descrizione: Descrizione dell’attività necessaria per completare l’attività. La descrizione predefinita è l’informazione che accompagna il consiglio SEO (Search Engine Optimization).
   * Priorità attività: Priorità dell&#39;attività.
   * Data di scadenza: Data entro la quale l’attività deve essere completata.

1. Tocca o fai clic su Fine per chiudere il messaggio Attività creata .

>[!NOTE]
>
>L’attività creata include anche il percorso della pagina a cui si applica il consiglio SEO.
