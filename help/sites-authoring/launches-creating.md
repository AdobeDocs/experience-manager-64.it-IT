---
title: Creazione dei lanci
seo-title: Creating Launches
description: Puoi creare un lancio per abilitare l’aggiornamento di una nuova versione di pagine web esistenti da attivare in futuro.
seo-description: You can create a launch to enable the updating of a new version of existing web pages for future activation.
uuid: c1a32710-8189-4a2e-bf2f-428ab30d48c8
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 4ec6b408-a165-4617-8d90-e89d8a415bb3
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 4b9d2f5f-aae7-4366-b6a6-a8277155cee9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 49%

---

# Creazione dei lanci{#creating-launches}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Crea un lancio per abilitare l’aggiornamento di una nuova versione di pagine web esistenti da attivare in futuro. Per creare un lancio, è necessario specificare un titolo e la pagina di origine:

* Il titolo viene visualizzato nella barra [Riferimenti](/help/sites-authoring/author-environment-tools.md#references), dalla quale gli autori potranno accedere per lavorarci.
* Per impostazione predefinita, nel lancio sono incluse le pagine figlie della pagina sorgente. Puoi utilizzare solo la pagina sorgente, se lo desideri.
* Per impostazione predefinita, [Live Copy](/help/sites-administering/msm.md) aggiorna automaticamente le pagine di lancio mano a mano che cambiano le pagine di origine. È possibile specificare la creazione di una copia statica per evitare modifiche automatiche.

Facoltativamente, puoi specificare la **Data lancio** (e l’ora) per definire quando promuovere e attivare le pagine del lancio. Tuttavia, la **Data lancio** funziona solo in combinazione con il flag **Production Ready** (vedi la sezione [Modifica di una configurazione di lancio](/help/sites-authoring/launches-editing.md#editing-a-launch-configuration)). Affinché le azioni vengano effettivamente eseguite in automatico, è necessario impostare entrambe.

## Creazione di un lancio {#creating-a-launch}

Puoi creare un lancio dalla console Sites o Lanci :

1. Apri la console **Sites** o **Lanci**.

   >[!NOTE]
   >
   >Quando utilizzi **Sites** la console solitamente consente di passare alla posizione della pagina sorgente, ma non è obbligatoria in quanto puoi spostarti selezionando la **Origine Launch** nella procedura guidata.

1. A seconda della console in uso:

   * **Lanci**:

      1. Seleziona **Creare un lancio** dalla barra degli strumenti per aprire la procedura guidata.
   * **Sites**:

      1. Seleziona **Crea** nella barra degli strumenti per aprire la casella di selezione.
      1. Da questa selezione **Creare un lancio** per aprire la procedura guidata.

   >[!NOTE]
   >
   >Nella console **Sites** è inoltre possibile utilizzare la [modalità di selezione](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) per scegliere una pagina prima di fare clic su **Crea**.
   >
   >La pagina selezionata verrà così utilizzata come pagina sorgente iniziale.

1. Nel passaggio **Seleziona origine** è necessario usare la funzione **Aggiungi pagine**. Puoi selezionare più pagine, specificando il percorso per ciascuna:

   * Passa alla posizione desiderata.
   * Seleziona le pagine sorgente e conferma (segno di spunta).

   Ripeti in base alle esigenze.  

   ![chlimage_1-225](assets/chlimage_1-225.png)

   >[!NOTE]
   >
   >Per aggiungere pagine e/o rami a un lancio, questi devono trovarsi all’interno di un sito; ovvero sotto una radice di livello superiore comune.
   >
   >Se un sito contiene directory principali per la lingua al di sotto del livello superiore, le pagine e i rami di un lancio devono trovarsi al di sotto di una directory principale per la lingua comune.

1. Per ogni voce è possibile specificare se:

   * **Includi le pagine secondarie**:

      * Specifica se creare il lancio con o senza pagine figlie.  Per impostazione predefinita, le pagine secondarie sono incluse.

   Procedi con **Successivo**.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. Nel passaggio **Proprietà** della procedura guidata puoi specificare:

   * **Titolo lancio**: Nome del lancio. Il nome deve essere significativo per gli autori.
   * **con contenuto esistente**: il contenuto originale verrà utilizzato per creare il lancio.
   * **con un nuovo modello per sostituire la pagina**: per ulteriori dettagli, vedi [Creare un lancio con un nuovo modello](#create-launch-with-new-template).
   * **Eredita i dati live della pagina di origine**: seleziona questa opzione per aggiornare automaticamente il contenuto delle pagine di lancio quando cambiano le pagine di origine. Questa opzione permette di ottenere questo risultato rendendo il lancio un [Live Copy](/help/sites-administering/msm.md).

      Per impostazione predefinita, questa opzione è selezionata.

   * **Data lancio**: la data e l&#39;ora in cui la copia del lancio deve essere attivata (in base alla segnalazione **Produzione pronta**; consulta [Lanci: l&#39;ordine degli eventi](/help/sites-authoring/launches.md#launches-the-order-of-events)).

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. Utilizzo **Crea** per completare il processo e creare il nuovo lancio. Viene visualizzata una finestra di dialogo di conferma in cui viene richiesto se desideri aprire immediatamente il lancio.

   Se torni alla console (con **Fine**) puoi visualizzare (e accedere al lancio da:

   * la [**Lanci** console](/help/sites-authoring/launches.md#the-launches-console)
   * la [**Riferimenti** in **Sites** console](/help/sites-authoring/launches.md#launches-in-references-sites-console)

### Creare un lancio con un nuovo modello {#create-launch-with-new-template}

Quando [creazione di un lancio](/help/sites-authoring/launches-creating.md#create-launch-with-new-template) puoi scegliere se utilizzare un nuovo modello:

**con un nuovo modello per sostituire la pagina**

>[!CAUTION]
>
>Questa opzione è disponibile solo quando crei un lancio dalla console **Sites**. Non è disponibile quando crei un lancio dalla console **Lanci**.

![chlimage_1-228](assets/chlimage_1-228.png)

Quando selezioni questa opzione:

* aggiornare le altre opzioni disponibili,
* includi un nuovo passaggio in cui puoi selezionare il modello richiesto.

![chlimage_1-229](assets/chlimage_1-229.png)

>[!CAUTION]
>
>Poiché viene utilizzato un modello diverso, la nuova pagina sarà vuota. A causa della diversa struttura della pagina, non verrà copiato alcun contenuto.
>
>Questo meccanismo può essere utilizzato per modificare il modello di un [pagina esistente](/help/sites-authoring/managing-pages.md#creating-a-new-page) - anche se la perdita di contenuto deve essere presa in considerazione.

### Creazione di un lancio nidificato {#creating-a-nested-launch}

La creazione di un lancio nidificato (lancio all’interno di un lancio) consente di creare un lancio da un lancio esistente in modo che gli autori possano sfruttare le modifiche già apportate, anziché dover apportare le stesse modifiche più volte per ogni lancio.

>[!NOTE]
>
>Vedi anche [Promozione di un lancio nidificato](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch).

#### Creazione di un lancio nidificato: console Lanci {#creating-a-nested-launch-launches-console}

La creazione di un lancio nidificato dalla console **Lanci** è molto simile alla creazione di qualsiasi altra forma di lancio, con l’eccezione che è necessario passare al ramo dei lanci `/content/launches`:

1. Nella console **Lanci** seleziona **Crea**.
1. Fai clic su **Aggiungi pagine**, quindi specifica `/content/launches` nel filtro per individuare il ramo lanci. Scegli il lancio necessario e conferma con **Seleziona**:

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. Procedi con **Successivo** e completa **Proprietà** come con qualsiasi altro lancio.

   ![chlimage_1-231](assets/chlimage_1-231.png)

#### Creazione di un lancio nidificato: console Sites {#creating-a-nested-launch-sites-console}

Per creare un lancio nidificato dalla console **Sites**, basato su un lancio esistente:

1. Accedi a [Lancio da Riferimenti (console Sites)](/help/sites-authoring/launches.md#launches-in-references-sites-console) per visualizzare le azioni disponibili.
1. Seleziona **Crea lancio** per aprire la procedura guidata (poiché l’origine è già stata selezionata, ignorerà il passaggio **Seleziona origine**).

1. Immetti il **Titolo lancio** e tutti gli altri dettagli richiesti (come con un normale lancio).

1. Utilizzo **Crea** per completare il processo e creare il nuovo lancio. Viene visualizzata una finestra di dialogo di conferma in cui viene richiesto se desideri aprire immediatamente il lancio.

   Se fai clic su **Fine**, vieni riportato alla barra **Riferimenti** della console **Sites**, se selezioni la pagina appropriata viene visualizzato il tuo nuovo lancio.

### Eliminazione di un lancio {#deleting-a-launch}

È possibile eliminare un lancio dal [console lanci](/help/sites-authoring/launches.md#the-launches-console):

* Seleziona il lancio toccando/facendo clic sulla miniatura.
* Viene visualizzata la barra degli strumenti. Selezionare Elimina.
* Conferma l’azione.

>[!CAUTION]
>
>L’eliminazione del lancio rimuove il lancio stesso e tutti i lanci nidificati discendenti.
