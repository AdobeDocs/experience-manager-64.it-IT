---
title: Set 360 gradi
description: Scopri come utilizzare i set 360 gradi in Dynamic Media. Un set 360 gradi simula l’atto reale di ruotare un oggetto per esaminarlo da qualsiasi angolo.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 47cb6d40-a5c4-4f6a-9794-bd2eddfaa7d0
feature: Spin Sets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1959'
ht-degree: 7%

---

# Set 360 gradi {#spin-sets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Un set 360 gradi simula l’atto reale di trasformare un oggetto per esaminarlo. I set 360 gradi consentono di visualizzare gli elementi da qualsiasi angolo, ottenendo i dettagli visivi chiave da qualsiasi angolo.

Un set 360 gradi simula un’esperienza di visualizzazione a 360 gradi. Dynamic Media offre set 360 gradi a un asse in cui i visualizzatori possono ruotare un elemento. Inoltre, gli utenti possono effettuare lo zoom &quot;in forma libera&quot; e scorrere qualsiasi visualizzazione con pochi semplici clic del mouse. In questo modo, gli utenti possono esaminare un elemento più da vicino da un particolare punto di vista.

I set 360 gradi sono indicati da un banner con la parola **[!UICONTROL SPINSET]**. Inoltre, se il set 360 gradi è pubblicato, la data di pubblicazione è indicata dalla **[!UICONTROL World]** sul banner si trova l’ultima data di modifica, indicata dalla **[!UICONTROL Matita]** viene visualizzata l’icona .

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>Per informazioni sull’interfaccia utente di Assets, consulta [Gestione delle risorse con l’interfaccia utente touch](managing-assets-touch-ui.md).

Quando crei un set 360 gradi, Adobe consiglia di seguire la procedura consigliata e applica il seguente limite:

| Tipo di limite | Best practice | Limite imposto |
| --- | --- | --- |
| Numero massimo di righe/colonne per set 2D | 12-18 immagini per set | 1000 |

Vedi anche [Limiti Dynamic Media](/help/assets/limitations.md).

## Avvio rapido: Set 360 gradi {#quick-start-spin-sets}

Per iniziare rapidamente a usare i set 360 gradi, segui questo flusso di lavoro:

1. [Carica le immagini per più visualizzazioni.](#uploading-assets-for-spin-sets)

   Per un set 360 gradi a una dimensione e per un set 360 gradi a due dimensioni, è necessario effettuare almeno 8-12 scatti di un elemento. Le riprese devono essere effettuate a intervalli regolari per dare l&#39;impressione che l&#39;elemento stia ruotando e sia capovolto. Ad esempio, se un set 360 gradi monodimensionale include 12 scatti, ruotate l’elemento di 30 gradi (360/12) per ogni ripresa.

1. [Crea set 360 gradi.](#creating-spin-sets)

   Per creare un set 360 gradi, seleziona **[!UICONTROL Crea > Set 360 gradi]** quindi assegna un nome al set, scegli le risorse, quindi ordina le immagini nell’ordine in cui appariranno.

   Vedi [Utilizzo dei selettori](working-with-selectors.md).

   >[!NOTE]
   >
   >È inoltre possibile creare automaticamente i set 360 gradi attraverso [predefiniti per set di batch](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   >
   >*I set di batch vengono creati dall’IPS (Image Production System) come parte dell’inserimento delle risorse e sono disponibili solo in modalità Dynamic Media - Scene7*.

1. Configurazione [Predefiniti visualizzatore per set 360 gradi](managing-viewer-presets.md), se necessario.

   Gli amministratori possono creare o modificare i predefiniti visualizzatore di set 360 gradi. Per visualizzare il set 360 gradi con un predefinito visualizzatore, seleziona il set 360 gradi e fai clic su nel menu a discesa della barra a sinistra **[!UICONTROL Visualizzatori]**.

   Vedi **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]** per creare o modificare i predefiniti visualizzatore.

   Vedi [Aggiunta e modifica dei predefiniti per visualizzatori.](managing-viewer-presets.md)

1. [Visualizzazione dei set 360 gradi](#viewing-spin-sets).

   È possibile visualizzare e accedere ai set creati mediante i predefiniti per set di batch in tre modi diversi. (I set creati utilizzando i predefiniti set di batch, sì *not* nell&#39;interfaccia utente).

1. [Anteprima set 360 gradi.](previewing-assets.md)

   Seleziona il set 360 gradi e puoi visualizzarlo in anteprima. Ruota il set 360 gradi. È possibile scegliere diversi visualizzatori dal **[!UICONTROL Visualizzatori]** disponibile dal menu a discesa della barra a sinistra.

1. [Pubblicare Set 360 gradi.](publishing-dynamicmedia-assets.md)

   La pubblicazione di un set 360 gradi attiva l’ordine in cui le immagini vengono visualizzate in un set 360 gradi. Assicurati di ordinarli in modo che la rotazione sia una vista a 360 gradi liscia.**[!UICONTROL URL]** e **[!UICONTROL Incorpora]** stringa. Inoltre, devi [pubblicare il predefinito visualizzatore](managing-viewer-presets.md).

1. [Collegare gli URL all’applicazione Web](linking-urls-to-yourwebapplication.md) o [Incorporare il visualizzatore di video o immagini](embed-code.md).

   AEM Assets crea chiamate URL per i set 360 gradi e li attiva dopo la pubblicazione dei set 360 gradi. Puoi copiare questi URL quando visualizzi l’anteprima delle risorse. In alternativa è possibile incorporarli sul sito Web.

   Seleziona il set a 360 gradi, quindi fai clic su **[!UICONTROL Visualizzatori]** nel menu a discesa della barra a sinistra.

   Consulta le sezioni [Collegamento di un set 360 gradi a una pagina web](linking-urls-to-yourwebapplication.md) e [Incorporamento di un visualizzatore di video o immagini](embed-code.md).

Se devi, puoi [modifica set 360 gradi](#editing-spin-sets). Inoltre, puoi visualizzare e modificare [Proprietà del set 360 gradi](managing-assets-touch-ui.md#editing-properties).

## Caricamento delle risorse per i set 360 gradi {#uploading-assets-for-spin-sets}

Per un set 360 gradi a una dimensione e per un set 360 gradi a due dimensioni, è necessario effettuare almeno 8-12 scatti di un elemento. Le riprese devono essere effettuate a intervalli regolari per dare l&#39;impressione che l&#39;elemento stia ruotando e sia capovolto. Ad esempio, se un set 360 gradi monodimensionale include 12 scatti, ruotate l’elemento di 30 gradi (360/12) per ogni ripresa.

Puoi caricare le immagini per i set 360 gradi come faresti per [caricare qualsiasi altra risorsa in AEM Assets](managing-assets-touch-ui.md).

### Linee guida per la ripresa di immagini di set 360 gradi {#guidelines-for-shooting-spin-set-images}

Di seguito sono riportate alcune best practice relative alle immagini di set 360 gradi. In generale, più immagini si hanno in un set 360 gradi, migliore è l&#39;effetto di rotazione dell&#39;immagine. Tuttavia, l&#39;inclusione di molte immagini nel set aumenta anche il tempo necessario al caricamento delle immagini. AEM consiglia le seguenti linee guida per le riprese di immagini da utilizzare nei set 360 gradi:

* Utilizza almeno 8-12 immagini in un set 360 gradi unidimensionale e 16-24 immagini in un set 360 gradi bidimensionale. Per poter girare a 360 gradi è necessario un minimo di 8 immagini. I set 360 gradi a una dimensione sono più comuni in quanto la creazione di set 360 gradi a due dimensioni richiede un’intensa attività di lavoro.
* Utilizzare un formato senza perdita; Si consiglia TIFF e PNG.
* Maschera tutte le immagini in modo che l&#39;elemento venga visualizzato su uno sfondo bianco puro o su un altro sfondo ad alto contrasto. Facoltativamente, aggiungi ombre.
* Assicurati che i dettagli del prodotto siano ben illuminati e concentrati.
* Prendere le immagini di spin per abbigliamento moda con un manichino o modello. Spesso il mannequin è completamente mascherato (utilizzando un manichino in vetro) o un mannequin/dressform stilizzato è mostrato nell&#39;immagine. Potete creare un set 360 gradi su modello definendo il numero di angoli. Contrassegnare ogni angolo con nastro sul pavimento per guidare il modello a passo e guardare nella direzione di ogni ripresa.

## Creazione di set 360 gradi {#creating-spin-sets}

L&#39;ordine in cui le immagini appaiono in un set 360 gradi ha importanza. Assicurati di ordinarli in modo che la rotazione sia una vista a 360 gradi liscia.

>[!NOTE]
>
>Puoi anche creare in automatico i set 360 gradi da [predefiniti set di batch](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
>
>I set di batch vengono creati dall’IPS (Image Production System) come parte dell’inserimento delle risorse e sono disponibili solo in modalità Dynamic Media - Scene7.
>
>Consulta &quot;Creazione di predefiniti per set di batch per generare automaticamente set di immagini e set 360 gradi&quot; in [Configurazione di Dynamic Media - Modalità Scene7](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

Quando crei un set 360 gradi, Adobe consiglia di seguire la procedura consigliata e applica il seguente limite:

| Tipo di limite | Best practice | Limite imposto |
| --- | --- | --- |
| Numero massimo di righe/colonne per set 2D | 12-18 immagini per set | 1000 |

Vedi anche [Limiti Dynamic Media](/help/assets/limitations.md).

**Per creare dei set 360 gradi:**

1. In Assets, individua il punto in cui vuoi creare un set 360 gradi e tocca **[!UICONTROL Crea]**, quindi seleziona **[!UICONTROL Set 360 gradi]**. Puoi anche creare il set dall’interno di una cartella contenente le risorse.

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. Sulla **[!UICONTROL Editor set 360 gradi]** nella pagina **[!UICONTROL Titolo]** Immettere un nome per il set 360 gradi. Il nome viene visualizzato nel banner lungo il set 360 gradi. Facoltativamente, immetti una descrizione.

   ![chlimage_1-382](assets/chlimage_1-382.png)

   Quando crei il set 360 gradi, puoi modificare la miniatura del set 360 gradi o consentire AEM selezionare automaticamente la miniatura in base alle risorse nel set 360 gradi. Per selezionare una miniatura, tocca **[!UICONTROL Modifica miniatura]**. Seleziona qualsiasi immagine (puoi passare ad altre cartelle per trovare anche le immagini). Se hai selezionato una miniatura e poi decidi di AEM generarne una dal set 360 gradi, seleziona **[!UICONTROL Passa alla miniatura automatica]**.

1. Effettua una delle seguenti operazioni:

   * Vicino all&#39;angolo superiore sinistro del **[!UICONTROL Editor set 360 gradi]** pagina, tocca **[!UICONTROL Aggiungi risorsa]**.
   * Vicino al centro del **[!UICONTROL Editor set 360 gradi]** pagina, tocca **[!UICONTROL Tocca per aprire il selettore risorse]**.

   Tocca per selezionare le risorse da includere nel set 360 gradi. Le risorse selezionate dispongono di un’icona a forma di segno di spunta. Al termine della procedura, tocca **[!UICONTROL Seleziona]**.

   Con il Selettore risorse, puoi cercare le risorse digitando una parola chiave e toccando **[!UICONTROL Invio]**. Per perfezionare i risultati della ricerca, puoi anche applicare i filtri. Puoi filtrare in base a percorso, raccolta, tipo di file e tag. Seleziona il filtro e tocca l’icona **[!UICONTROL Filtro]** nella barra degli strumenti. Per modificare la visualizzazione, tocca **[!UICONTROL Visualizza]** icona, quindi tocca **[!UICONTROL Vista a colonne]**, **[!UICONTROL Vista a schede]** oppure **[!UICONTROL Vista a elenco]**.

   Vedi [Utilizzo dei selettori](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Quando aggiungi delle risorse al set, queste vengono aggiunte automaticamente in ordine alfanumerico. Puoi riordinare o ordinare manualmente le risorse dopo averle aggiunte. Se necessario, trascina le **[!UICONTROL Riordina]** a destra del nome del file della risorsa per riordinare le immagini verso l’alto o verso il basso nell’elenco dei set.

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. (Facoltativo) Effettua una delle seguenti operazioni:

   * Per eliminare un’immagine, selezionala e tocca **[!UICONTROL Elimina risorsa]**.
   * Per applicare un predefinito, tocca **[!UICONTROL Predefinito]**, quindi seleziona un predefinito da applicare a tutte le risorse contemporaneamente.

1. Tocca **[!UICONTROL Salva]**. Il set 360 gradi appena creato viene visualizzato nella cartella in cui è stato creato.

## Visualizzazione dei set 360 gradi {#viewing-spin-sets}

Puoi creare i set 360 gradi nell’interfaccia utente o automaticamente utilizzando [predefiniti per set di batch](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). Tuttavia, i set creati utilizzando i predefiniti per set di batch, sì *not* nell’interfaccia utente. Puoi accedere ai set creati tramite predefiniti per set di batch in tre modi diversi. (Questi metodi sono disponibili anche se hai creato i Set 360 gradi nell’interfaccia utente).

Puoi anche visualizzare i set tramite l’interfaccia utente descritta in [Modifica dei set 360 gradi](#editing-spin-sets).

**Per visualizzare i set 360 gradi:**

1. Quando si aprono le proprietà di una singola risorsa. Le proprietà indicano l’impostazione di un membro della risorsa selezionata (in **[!UICONTROL Membro dei set]**). Toccare il nome del set per visualizzare l’intero set.

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. Da un’immagine inclusa in un qualsiasi set. Seleziona la **[!UICONTROL Set]** per visualizzare i set di cui fa parte la risorsa.

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. Dalla ricerca, puoi selezionare **[!UICONTROL Filtri]**, quindi espandi **[!UICONTROL Dynamic Media]** e seleziona **[!UICONTROL Set]**.

   La ricerca restituisce i set corrispondenti creati manualmente nell’interfaccia utente o automaticamente tramite i predefiniti per set di batch. Per i set automatizzati, la query di ricerca viene eseguita utilizzando **[!UICONTROL Inizia con]** criteri di ricerca diversi dalla ricerca AEM basata sull’utilizzo **[!UICONTROL Contiene]** criteri di ricerca. Impostazione del filtro su **[!UICONTROL Set]** è l’unico modo per cercare i set automatizzati.

   ![chlimage_1-386](assets/chlimage_1-386.png)

## Modifica dei set 360 gradi {#editing-spin-sets}

Puoi eseguire diverse attività di modifica sui set 360 gradi, ad esempio:

* Aggiungi le immagini al set 360 gradi.
* Riordinare le immagini nel set 360 gradi.
* Elimina le risorse nel set 360 gradi.
* Applica i predefiniti visualizzatore.
* Elimina il set 360 gradi.

**Per modificare un set 360 gradi:**

1. Effettua una delle seguenti operazioni:

   * Passa il puntatore del mouse su una risorsa del set 360 gradi, quindi tocca **[!UICONTROL Modifica]** (icona a forma di matita).
   * Passa il puntatore del mouse su una risorsa del set 360 gradi **[!UICONTROL Seleziona]** (icona a forma di segno di spunta), quindi tocca **[!UICONTROL Modifica]** sulla barra degli strumenti.
   * Tocca una risorsa del set 360 gradi, quindi tocca **[!UICONTROL Modifica]** (icona a forma di matita) sulla barra degli strumenti.

1. Per modificare il set 360 gradi, effettuate una delle seguenti operazioni:

   * Per riordinare le immagini, trascinate un’immagine in una nuova posizione (selezionate l’icona di riordino per spostare gli elementi).
   * Per ordinare gli elementi in ordine crescente o decrescente, tocca l’intestazione della colonna.
   * Per aggiungere una risorsa o aggiornare una risorsa esistente, tocca **[!UICONTROL Aggiungi risorsa]**. Passa a una risorsa, selezionala, quindi tocca **[!UICONTROL Seleziona]** nell&#39;angolo in alto a destra.
Se elimini l&#39;immagine che AEM utilizzata per la miniatura sostituendola con un&#39;altra immagine, viene comunque visualizzata la risorsa originale.
   * Per eliminare una risorsa, selezionala e tocca **[!UICONTROL Elimina risorsa]**.
   * Per applicare un predefinito, tocca **[!UICONTROL Predefinito]** e seleziona un predefinito.
   * Per eliminare un intero set 360 gradi, accedi al set 360 gradi, selezionalo e seleziona **[!UICONTROL Elimina]**

      >[!NOTE]
      >* Per modificare le immagini di un set 360 gradi, tocca il set **[!UICONTROL Imposta membri]** nella barra a sinistra, quindi tocca **[!UICONTROL Modifica]** (icona a forma di matita) su una singola risorsa per aprire la finestra di modifica.


1. Fai clic su **[!UICONTROL Salva]** al termine della modifica.

## Anteprima dei set 360 gradi {#previewing-spin-sets}

Vedi [Anteprima delle risorse](previewing-assets.md).

## Pubblicazione dei set 360 gradi {#publishing-spin-sets}

Vedi [Pubblicazione delle risorse](publishing-dynamicmedia-assets.md).
