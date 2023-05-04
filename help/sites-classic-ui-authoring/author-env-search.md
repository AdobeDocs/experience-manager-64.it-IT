---
title: Ricerca
seo-title: Search
description: L’ambiente di authoring di AEM offre vari metodi per la ricerca dei contenuti, a seconda del tipo di risorsa.
seo-description: The author environment of AEM provides various mechanisms for searching for content, dependent on the resource type.
uuid: b50c8144-1993-441d-8303-fcb6b0f24376
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b20e0f78-9ae4-47ba-8e9a-452a0a78b663
exl-id: 9c1d8969-6aa6-41b9-a797-3e6431475fc6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 11%

---

# Ricerca{#search-features}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’ambiente di authoring di AEM offre vari metodi per la ricerca dei contenuti, a seconda del tipo di risorsa.

>[!NOTE]
>
>Al di fuori dell’ambiente di authoring sono disponibili anche altri meccanismi per la ricerca, come [Query Builder](/help/sites-developing/querybuilder-api.md) e [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Informazioni di base sulla ricerca {#search-basics}

Per accedere al pannello di ricerca, fai clic sul pulsante **Ricerca** nella parte superiore del riquadro a sinistra della console appropriata.

![chlimage_1-140](assets/chlimage_1-140.png)

Il pannello di ricerca consente di effettuare ricerche in tutte le pagine del sito web. Contiene campi e widget per i seguenti elementi:

* **Testo completo**: Cerca il testo specificato
* **Modificato dopo/prima**: Cerca solo nelle pagine modificate tra date specifiche
* **Modello**: Cerca solo le pagine basate sul modello specificato
* **Tag**: Cerca solo nelle pagine con i tag specificati

>[!NOTE]
>
>Quando l’istanza è configurata per [Ricerca Lucene](/help/sites-deploying/queries-and-indexing.md) puoi utilizzare quanto segue in **Testo completo**:
>
>* [Caratteri jolly](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Wildcard_Searches)
>* [Operatori booleani](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boolean_operators)
>
>* [Espressioni regolari](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Regexp_Searches)
>* [Raggruppamento campi](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Field_Grouping)
>* [Incremento](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boosting_a_Term)
>


Esegui la ricerca facendo clic su **Ricerca** nella parte inferiore del riquadro. Fai clic su **Reimposta** per cancellare i criteri di ricerca.

## Filtro {#filter}

In varie posizioni è possibile impostare (e cancellare) un filtro per approfondire e perfezionare la visualizzazione:

![chlimage_1-141](assets/chlimage_1-141.png)

## Trova e sostituisci {#find-and-replace}

In **Siti Web** console a **Trova e sostituisci** l’opzione di menu consente di cercare e sostituire più istanze di una stringa all’interno di una sezione del sito web.

1. Selezionare la pagina o la cartella principale in cui si desidera eseguire l’azione Trova e sostituisci.
1. Seleziona **Strumenti** then **Trova e sostituisci**:

   ![screen_shot_2012-02-15at120346pm](assets/screen_shot_2012-02-15at120346pm.png)

1. La **Trova e sostituisci** la finestra di dialogo effettua le seguenti operazioni:

   * conferma il percorso principale in cui deve iniziare l&#39;azione di ricerca
   * definisce il termine da trovare
   * definisce il termine che deve sostituirlo
   * indica se la ricerca deve fare distinzione tra maiuscole e minuscole
   * indica se devono essere trovate solo parole intere (in caso contrario vengono trovate anche le sottostringhe)

   Clic **Anteprima** elenchi in cui è stato trovato il termine. È possibile selezionare o deselezionare istanze specifiche da sostituire:

   ![screen_shot_2012-02-15at120719pm](assets/screen_shot_2012-02-15at120719pm.png)

1. Fai clic su **Sostituisci** per sostituire effettivamente tutte le istanze. Viene richiesto di confermare l’operazione.

L’ambito predefinito del servlet di ricerca e sostituzione include le seguenti proprietà:

* `jcr:title`
* `jcr:description`
* `jcr:text`
* `text`

L’ambito può essere modificato utilizzando la console di gestione web Apache Felix (ad esempio, in `http://localhost:4502/system/console/configMgr`). Seleziona `CQ WCM Find Replace Servlet (com.day.cq.wcm.core.impl.servlets.FindReplaceServlet)` e configura l&#39;ambito come necessario.

>[!NOTE]
>
>In un’installazione standard AEM Trova e sostituisci utilizza Lucene per la funzionalità di ricerca.
>
>Lucene indicizza le proprietà delle stringhe con lunghezza fino a 16 k. Per le stringhe di lunghezza superiore a tale valore la ricerca non viene eseguita.
