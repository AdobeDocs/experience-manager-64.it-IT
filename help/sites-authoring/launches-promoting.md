---
title: Promozione dei lanci
seo-title: Promoting Launches
description: È necessario promuovere le pagine di lancio per spostare nuovamente il contenuto nell’origine (produzione) prima della pubblicazione.
seo-description: You need to promote launch pages to move the content back into the source (production) before publishing.
uuid: 56483f8f-d66e-4677-a7bd-3b1425625b2b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 977a3dda-4292-4bd2-bfa5-af4d789d9ef9
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 2a790f7d-03a1-4f60-a59e-0a5f15c44fa5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 27%

---

# Promozione dei lanci{#promoting-launches}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È necessario promuovere le pagine di lancio per spostare nuovamente il contenuto nell’origine (produzione) prima della pubblicazione. Quando una pagina di lancio viene promossa, la pagina corrispondente nelle pagine sorgente viene sostituita con il contenuto della pagina promossa. Quando si promuove una pagina di lancio sono disponibili le seguenti opzioni:

* Promuovere solo la pagina corrente o l’intero lancio.
* Promuovere le pagine figlie della pagina corrente.
* Promuovere il lancio completo o solo le pagine che sono state modificate.

>[!NOTE]
>
>Dopo aver promosso le pagine di lancio al target (**Produzione**), puoi attivare la **Produzione** come entità (per velocizzare il processo). Aggiungi le pagine a un pacchetto di flusso di lavoro e utilizzalo come payload per un flusso di lavoro che attiva un pacchetto di pagine. Devi creare il pacchetto del flusso di lavoro prima di promuovere il lancio. Vedi [Elaborazione di pagine promosse tramite AEM flusso di lavoro](#processing-promoted-pages-using-aem-workflow).

>[!CAUTION]
>
>Non è possibile promuovere contemporaneamente un singolo lancio. Due azioni di promozione sullo stesso lancio nello stesso momento possono causare un errore: `Launch could not be promoted` (con gli errori di conflitto nel registro).

>[!CAUTION]
>
>Quando promuovi i lanci per *Modificata* vengono considerate le modifiche apportate ai rami sorgente e lancio.

## Promozione delle pagine di lancio {#promoting-launch-pages}

>[!NOTE]
>
>Questo copre l’azione manuale per promuovere le pagine di lancio quando esiste un solo livello di lancio. Consulta:
>
>* [Promozione di un lancio nidificato](#promoting-a-nested-launch) quando la struttura contiene più di un lancio.
>* [Lanci - Ordine degli eventi](/help/sites-authoring/launches.md#launches-the-order-of-events) per ulteriori dettagli sulla promozione e la pubblicazione automatica.
>


Puoi promuovere i lanci da **Sites** o **Lanci** console:

1. Apri:

   * la **Sites** console:

      1. Apri la [barra dei riferimenti](/help/sites-authoring/author-environment-tools.md#references) e seleziona la pagina sorgente desiderata utilizzando la [modalità di selezione](/help/sites-authoring/basic-handling.md) (oppure seleziona e apri la barra dei riferimenti, l’ordine non è importante). Verranno visualizzati tutti i riferimenti.

      1. Seleziona **Lanci** (ad esempio Lanci (1)) per visualizzare un elenco dei lanci specifici.
      1. Seleziona il lancio specifico per visualizzare le azioni disponibili.
      1. Seleziona **Promuovi lancio** per aprire la procedura guidata.
   * la **Lanci** console:

      1. Seleziona il lancio (tocca o fai clic sulla miniatura).
      1. Seleziona **Promuovi**.


1. Nel primo passaggio puoi specificare:

   * **Promuovi tutto il lancio**
   * **Promuovi pagine modificate**
   * **Promuovi la pagina corrente**
   * **Promuovi la pagina corrente e le sottopagine**

   Ad esempio, quando selezioni solo la promozione delle pagine modificate:

   ![chlimage_1](assets/chlimage_1.png)

   >[!NOTE]
   >
   >Questo copre un singolo lancio, se hai lanci nidificati vedi [Promozione di un lancio nidificato](#promoting-a-nested-launch).

1. Seleziona **Successivo** per procedere.
1. Puoi rivedere le pagine da promuovere, a seconda dell’intervallo di pagine scelto:

   ![chlimage_1-1](assets/chlimage_1-1.png)

1. Seleziona **Promuovi**.

## Promozione delle pagine di lancio durante la modifica {#promoting-launch-pages-when-editing}

Quando modifichi una pagina di lancio, la **Promuovi lancio** l&#39;azione è disponibile anche da **Informazioni pagina**. Si aprirà la procedura guidata per raccogliere le informazioni necessarie.

![chlimage_1-2](assets/chlimage_1-2.png)

>[!NOTE]
>
>È disponibile per [lanci nidificati](#promoting-a-nested-launch).

## Promozione di un lancio nidificato {#promoting-a-nested-launch}

Dopo aver creato un lancio nidificato, puoi promuoverlo di nuovo in una qualsiasi delle sorgenti, inclusa la sorgente principale (produzione).

![chlimage_1-3](assets/chlimage_1-3.png)

1. Come con [Creazione di un lancio nidificato](/help/sites-authoring/launches-creating.md#creating-a-nested-launch), individua e seleziona il lancio richiesto nel **Lanci** o **Riferimenti** barra.
1. Seleziona **Promuovi lancio** per aprire la procedura guidata.

1. Immetti i dettagli necessari:

   * **Destinazione della promozione**

      Puoi promuovere a qualsiasi fonte.

   * **Ambito**
Qui puoi scegliere se promuovere l’intero lancio o solo le pagine che sono state effettivamente modificate. In quest’ultimo caso, puoi selezionare per includere/escludere le pagine secondarie. La configurazione predefinita consiste nel promuovere solo le modifiche alla pagina corrente:

      * **Promuovi tutto il lancio**
      * **Promuovi pagine modificate**
      * **Promuovi la pagina corrente**
      * **Promuovi la pagina corrente e le sottopagine**

   ![chlimage_1-4](assets/chlimage_1-4.png)

1. Seleziona **Avanti**.
1. Rivedi i dettagli della promozione prima di selezionare **Promuovi**:

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Le pagine elencate dipendono dal **Ambito** e le pagine effettivamente modificate.

1. Le modifiche verranno promosse e riportate nella **Lanci** console:

   ![chlimage_1-6](assets/chlimage_1-6.png)

## Elaborazione di pagine promosse tramite Flusso di lavoro AEM {#processing-promoted-pages-using-aem-workflow}

Utilizza i modelli di flusso di lavoro per eseguire l’elaborazione in blocco delle pagine dei lanci promossi:

1. Crea un pacchetto di flusso di lavoro.
1. Quando gli autori promuovono le pagine Launch, le memorizzano nel pacchetto del flusso di lavoro.
1. Avvia un modello di flusso di lavoro utilizzando il pacchetto come payload.

Per avviare automaticamente un flusso di lavoro quando vengono promosse le pagine, [configurare un modulo di avvio del flusso di lavoro](/help/sites-administering/workflows-starting.md#workflows-launchers) per il nodo del pacchetto.

Ad esempio, puoi generare automaticamente le richieste di attivazione pagina non appena un autore promuove una pagina di lancio. Configura un modulo di avvio del flusso di lavoro per avviare il flusso di lavoro Attivazione richiesta quando viene modificato il nodo del pacchetto.

![chlimage_1-7](assets/chlimage_1-7.png)
