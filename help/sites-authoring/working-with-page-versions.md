---
title: 'Utilizzo delle versioni di una pagina  '
seo-title: 'Utilizzo delle versioni di una pagina  '
description: Creare, confrontare e ripristinare le versioni di una pagina
seo-description: Creare, confrontare e ripristinare le versioni di una pagina
uuid: b0328431-c2cf-48f4-b358-261238338241
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: fa331c03-5587-452d-ab96-ac2926ae0da3
translation-type: tm+mt
source-git-commit: 98fae2d51d73bda946f3c398e9276fe4d5a8a0fe
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 96%

---


# Utilizzo delle versioni di una pagina  {#working-with-page-versions}

Quando si crea una versione, viene creata un’istantanea di una pagina in un particolare momento. La funzione di gestione delle versioni consente di effettuare le seguenti operazioni:

* Creare una versione di una pagina.
* Ripristinare una versione precedente di una pagina, ad esempio per annullare una modifica apportata alla pagina.
* Confrontare la versione corrente di una pagina con una versione precedente, evidenziando le differenze nel testo e nelle immagini.

## Creazione di una nuova versione   {#creating-a-new-version}

Puoi creare una versione della risorsa da:

* la [barra laterale Timeline](#creating-a-new-version-timeline)
* l’opzione [Crea](#creating-a-new-version-create-with-a-selected-resource) (quando è selezionata una risorsa)

### Creazione di una nuova versione - Timeline {#creating-a-new-version-timeline}

1. Passa alla pagina per la quale desideri creare una nuova versione.
1. Seleziona la pagina in [modalità di selezione](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Apri la colonna **Timeline**.
1. Tocca o fai clic sulla freccia accanto al campo del commento per visualizzare le opzioni:

   ![screen_shot_2018-03-21at155035](assets/screen_shot_2018-03-21at155035.png)

1. Seleziona **Salva come versione**.
1. Inserisci un’**etichetta** e un **commento**, se necessario.

   ![chlimage_1-398](assets/chlimage_1-398.png)

1. Conferma la nuova versione selezionando **Crea**.

   Le informazioni nella timeline vengono aggiornate per indicare che si tratta di una nuova versione.

### Creazione di una nuova versione - Con una risorsa selezionata {#creating-a-new-version-create-with-a-selected-resource}

1. Passa alla pagina per la quale desideri creare una nuova versione.
1. Seleziona la pagina in [modalità di selezione](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Seleziona l’opzione **Crea** nella barra degli strumenti.
1. Viene aperta una finestra di dialogo. Puoi immettere un’**etichetta** e un **commento**, se necessario:

   ![screen_shot_2012-02-15at105050am](assets/screen_shot_2012-02-15at105050am.png)

1. Conferma la nuova versione selezionando **Crea**.

   Viene aperta la timeline con le informazioni aggiornate per indicare che si tratta di una nuova versione.

## Ripristino di una versione della pagina {#reverting-to-a-page-version}

Una volta creata una versione, puoi ripristinarla se necessario.

>[!NOTE]
>
>Durante il ripristino di una pagina, la versione creata farà parte di un nuovo ramo.
>
>Per maggiore chiarezza:
>
>* Crea versioni di qualsiasi pagina.
>* Le etichette iniziali e i nomi dei nodi di versione saranno 1.0, 1.1, 1.2 e così via.
>* Ripristina la prima versione, ovvero 1.0.
>* Crea di nuovo una o più nuove versioni.
>* Le etichette generati e i nomi dei nodi saranno ora 1.0.0, 1.0.1, 1.0.2 e così via.

>



Per ripristinare una versione precedente:

1. Passa alla pagina di cui desideri ripristinare una versione precedente.
1. Seleziona la pagina in [modalità di selezione](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Apri la colonna **Timeline** e seleziona **Mostra tutti** o **Versioni**. Vengono elencate le versioni disponibili per la pagina selezionata.
1. Seleziona la versione da ripristinare. Vengono visualizzate le opzioni disponibili:

   ![screen_shot_2018-03-21at155246](assets/screen_shot_2018-03-21at155246.png)

1. Seleziona **Ripristina questa versione**. La versione selezionata viene ripristinata e le informazioni nella timeline vengono aggiornate.

## Anteprima di una versione    {#previewing-a-version}

Puoi visualizzare in anteprima una versione specifica:

1. Passa alla pagina da confrontare.
1. Seleziona la pagina in [modalità di selezione](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Apri la colonna **Timeline** e seleziona **Mostra tutti** o **Versioni**.
1. Vengono elencate le versioni disponibili. Seleziona la versione che desideri vedere in anteprima:

   ![screen_shot_2018-03-21at155330](assets/screen_shot_2018-03-21at155330.png)

1. Seleziona **Anteprima**. La pagina viene visualizzata in una nuova scheda.

   >[!CAUTION]
   >
   >Se una pagina è stata spostata, non è più possibile eseguire un’anteprima su qualsiasi versione creata prima dello spostamento.
   >
   >In caso di problemi con l’anteprima, controlla la [Timeline](/help/sites-authoring/basic-handling.md#timeline) per verificare se la pagina è stata spostata.

## Confronto di una versione con la pagina corrente {#comparing-a-version-with-current-page}

Per confrontare una versione precedente con quella corrente:

1. Passa alla pagina da confrontare.
1. Seleziona la pagina in [modalità di selezione](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Apri la colonna **Timeline** e seleziona **Mostra tutti** o **Versioni**.
1. Vengono elencate le versioni disponibili. Seleziona la versione da confrontare.

   ![screen_shot_2018-03-21at155330](assets/screen_shot_2018-03-21at155330.png)

1. Seleziona **Confronta con corrente**. Viene visualizzata la finestra delle [differenze tra le pagine](/help/sites-authoring/page-diff.md), che mostra le differenze.

## Timewarp    {#timewarp}

Timewarp è una funzione progettata per simulare lo stato *di pubblicazione* di una pagina in specifici momenti nel passato.

Questo consente di tenere tracciare del sito pubblicato in un particolare momento. Le versioni delle pagine vengono usate per determinare lo stato dell’ambiente di pubblicazione.

Per effettuare ciò:

* Il sistema cerca la versione della pagina che era attiva nel momento temporale selezionato.
* In altre parole, la versione mostrata era stata creata/attivata *prima* del momento temporale selezionato in Timewarp.
* Quando si passa a una pagina che è stata successivamente eliminata, questa viene riprodotta purché nella directory archivio siano ancora disponibili le precedenti versioni di tale pagina.
* Se non viene individuata alcuna versione pubblicata, Timewarp ripristina lo stato corrente della pagina nell’ambiente di authoring, in modo da evitare un errore 404 di pagina non trovata, che impedirebbe la navigazione.

### Utilizzo di Timewarp {#using-timewarp}

Timewarp è una [modalità](/help/sites-authoring/author-environment-tools.md#page-modes) dell’editor pagina. Puoi avviarla come faresti con qualsiasi altra modalità.

1. Avvia l’editor per la pagina in cui desideri avviare Timewarp e quindi seleziona **Timewarp** nella selezione della modalità.

   ![screen_shot_2018-03-21at155416](assets/screen_shot_2018-03-21at155416.png)

1. Nella finestra di dialogo, imposta una data e un’ora di destinazione e tocca o fai clic su **Imposta data**. Se non si seleziona un’ora, per impostazione predefinita verrà utilizzata l’ora corrente.

   ![screen_shot_2018-03-21at155513](assets/screen_shot_2018-03-21at155513.png)

1. La pagina viene visualizzata in base alla data impostata. La modalità Timewarp è indicata dalla barra di stato blu nella parte superiore della finestra. Utilizza i collegamenti nella barra di stato per selezionare una nuova data di destinazione o per uscire dalla modalità Timewarp.

   ![screen_shot_2018-03-21at155544](assets/screen_shot_2018-03-21at155544.png)

### Limitazioni di Timewarp

Timewarp semplifica al massimo la riproduzione di una pagina in un determinato momento. Tuttavia, a causa delle complessità dell’authoring continuo di contenuti in AEM, questo non è sempre possibile. Tieni presenti queste limitazioni quando utilizzi Timewarp.

* **Timewarp funziona in base alle pagine pubblicate**: Timewarp funziona correttamente solo se la pagina è stata già pubblicata. In caso contrario viene mostrata la pagina corrente nell’ambiente di authoring.
* **Timewarp utilizza le versioni di pagina**: se passi a una pagina che è stata rimossa o eliminata dall’archivio, questa verrà riprodotta correttamente se nell’archivio sono ancora disponibili versioni precedenti della pagina.
* **Le versioni rimosse influiscono su Timewarp**: se dalla directory archivio sono state rimosse delle versioni, Timewarp non può mostrare la visualizzazione corretta.
* **Timewarp è di sola lettura**: non è possibile modificare la versione precedente della pagina, ma solo visualizzarla. Se desideri ripristinare la versione precedente, devi farlo manualmente utilizzando la funzione di ripristino.
* **Timewarp si basa solo sul contenuto della pagina**: se sono stati modificati alcuni elementi (come codice, css, risorse/immagini ecc.) per il rendering del sito web, la visualizzazione sarà diversa da come era all’origine, poiché per tali elementi non vengono conservate precedenti versioni nell’archivio.

>[!CAUTION]
>
>Timewarp è uno strumento che consente agli autori di comprendere e creare i propri contenuti. Non deve essere utilizzato come registro di controllo o per fini legali.