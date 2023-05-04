---
title: Creare una pagina di esempio
seo-title: Create a Sample Page
description: Creare un sito community di esempio
seo-description: Create a Sample community site
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
exl-id: 00ac29fb-cc8f-4dd9-a261-839a4bf664c2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 5%

---

# Creare una pagina di esempio {#create-a-sample-page}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

A partire da AEM 6.1 Communities, il modo più semplice per creare una pagina di esempio è quello di creare un sito community semplice, composto semplicemente da una funzione Pagina .

Questo includerà un componente parsys in modo che sia possibile [abilitare i componenti per l’authoring](basics.md#accessing-communities-components).

Un’altra opzione per l’esplorazione con i componenti di esempio è quella di utilizzare le funzioni presentate nel [Guida ai componenti della community](components-guide.md).

## Creare un sito community {#create-a-community-site}

È molto simile alla creazione di un nuovo sito descritto in [Guida introduttiva ad AEM Communities](getting-started.md).

La differenza principale consiste nel fatto che questo tutorial creerà un nuovo modello di sito community che contiene solo [Funzione Pagina](functions.md#page-function) per creare un semplice sito community privo di altre funzioni (diverse dalle funzioni precablate di base per tutti i siti della community).

### Crea nuovo modello di sito {#create-new-site-template}

Per iniziare, crea una [modello di sito community](sites.md).

Dalla navigazione globale su un’istanza di authoring seleziona **[!UICONTROL Strumenti > Community > Modelli di sito]**.

![chlimage_1-82](assets/chlimage_1-82.png)

* Seleziona `Create button`
* INFORMAZIONI DI BASE

   * `Name`: Modello a pagina singola
   * `Description`: Un modello composto da una singola funzione Pagina.
   * select `Enabled`

![chlimage_1-83](assets/chlimage_1-83.png)

* STRUTTURA

   * Trascina un `Page` funzione per il Generatore di modelli
   * Per i dettagli della funzione di configurazione, immettere

      * `Title`: Pagina singola
      * `URL`: pagina

![chlimage_1-84](assets/chlimage_1-84.png)

* Seleziona **`Save`** per la configurazione
* Seleziona **`Save`** per il modello di sito

### Crea nuovo sito community {#create-new-community-site}

Ora crea un nuovo sito community basato sul modello di sito semplice.

Dopo aver creato il modello di sito, dalla navigazione globale seleziona **[!UICONTROL Community > Sites]**.

![chlimage_1-85](assets/chlimage_1-85.png)

* Seleziona **`Create`** icona

* Passaggio `1 - Site Template`

   * `Title`: Sito della community semplice
   * `Description`: Un sito della community composto da una singola pagina per la sperimentazione.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: esempio

      * url = http://localhost:4502/content/sites/sample
   * `Template`: scegli `Single Page Template`


![chlimage_1-86](assets/chlimage_1-86.png)

* Seleziona `Next`
* Passaggio `2 - Design`

   * Selezionare una progettazione

* Seleziona `Next`
* Seleziona `Next`

   (Accetta tutte le impostazioni predefinite)

* Seleziona `Create`

![chlimage_1-87](assets/chlimage_1-87.png)

## Pubblicare il sito {#publish-the-site}

![chlimage_1-88](assets/chlimage_1-88.png)

Da [console siti community](sites-console.md), seleziona l’icona pubblica per pubblicare il sito, per impostazione predefinita in http://localhost:4503.

## Apri il sito in modalità Modifica {#open-the-site-on-author-in-edit-mode}

![chlimage_1-89](assets/chlimage_1-89.png)

Seleziona l’icona del sito aperto per visualizzare il sito in modalità di modifica.

L’URL sarà [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![chlimage_1-90](assets/chlimage_1-90.png)

Nella semplice home page è possibile vedere cosa è preconnesso attraverso le funzioni e i modelli della community e giocare con l’aggiunta e la configurazione di componenti della community.

## Visualizza sito su Pubblica {#view-site-on-publish}

Dopo aver pubblicato la pagina, aprilo nella pagina [pubblica istanza](http://localhost:4503/content/sites/sample/en.html) per sperimentare le funzioni come visitatore anonimo del sito, iscritto o amministratore. Il collegamento Amministrazione visibile nell’ambiente di authoring non viene visualizzato nell’ambiente di pubblicazione, a meno che un amministratore non effettui l’accesso.
