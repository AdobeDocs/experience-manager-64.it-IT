---
title: Set 360 gradi
description: Scoprite come utilizzare i set 360 gradi in Dynamic Media. Un set 360 gradi simula la rotazione di un oggetto per esaminarlo da qualsiasi angolazione.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 6%

---


# Set 360 gradi {#spin-sets}

Un set 360 gradi simula la rotazione reale di un oggetto per esaminarlo. I set 360 gradi consentono di visualizzare gli elementi da qualsiasi angolo, ottenendo i dettagli visivi chiave da qualsiasi angolazione.

Un set 360 gradi simula un’esperienza di visualizzazione a 360 gradi. Dynamic Media offre set 360 gradi con asse singolo in cui gli utenti possono ruotare un elemento. Inoltre, gli utenti possono effettuare lo zoom &quot;a mano libera&quot; e scorrere qualsiasi visualizzazione con pochi semplici clic del mouse. In questo modo, gli utenti possono esaminare un elemento più da vicino da un particolare punto di vista.

I set 360 gradi sono contrassegnati da un banner con la parola **[!UICONTROL SPINSET]**. Inoltre, se il set 360 gradi è pubblicato, la data di pubblicazione indicata dall&#39;icona **[!UICONTROL World]** si trova sul banner insieme all&#39;ultima data di modifica, indicata dall&#39;icona **[!UICONTROL Pencil]**.

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>Per informazioni sull&#39;interfaccia utente di Risorse, consultate [Gestione delle risorse con l&#39;interfaccia utente touch](managing-assets-touch-ui.md).

## Avvio rapido: Set 360 gradi {#quick-start-spin-sets}

Per iniziare rapidamente a usare i set 360 gradi, effettuate le seguenti operazioni:

1. [Caricate le immagini per più viste.](#uploading-assets-for-spin-sets)

   Per un set 360 gradi monodimensionale, sono necessari almeno 8-12 scatti di un elemento e 16-24 scatti per un set 360 gradi bidimensionale. Le riprese devono essere effettuate a intervalli regolari per dare l’impressione che l’elemento stia ruotando e sia capovolto. Ad esempio, se un set 360 gradi monodimensionale include 12 scatti, ruotate l’elemento di 30 gradi (360/12) per ciascuna ripresa.

1. [Creare set 360 gradi.](#creating-spin-sets)

   Per creare un set 360 gradi, selezionate **[!UICONTROL Crea > Set 360 gradi]**, quindi denominate il set, scegliete le risorse e ordinate le immagini nell’ordine in cui verranno visualizzate.

   Vedere [Utilizzo dei selettori](working-with-selectors.md).

   >[!NOTE]
   >
   >Potete anche creare automaticamente i set 360 gradi mediante i predefiniti per set di batch [predefiniti](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   >
   >*I set di batch vengono creati dall’IPS (Image Production System) come parte dell’assimilazione delle risorse e sono disponibili solo in modalità* Dynamic Media - Scene7.

1. Impostate i predefiniti per visualizzatori di set 360 gradi [a seconda delle necessità.](managing-viewer-presets.md)

   Gli amministratori possono creare o modificare i predefiniti per visualizzatori di set 360 gradi. Per visualizzare il set 360 gradi con un predefinito per visualizzatori, selezionate il set 360 gradi e, nel menu a discesa a sinistra, selezionate **[!UICONTROL Visualizzatori]**.

   Per creare o modificare i predefiniti per visualizzatori, consultate **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]**.

   Consultate [Aggiunta e modifica dei predefiniti per visualizzatori.](managing-viewer-presets.md)

1. [Visualizzazione di set](#viewing-spin-sets) 360 gradi

   Potete visualizzare e accedere ai set creati mediante i predefiniti per set di batch in tre modi diversi. (i set creati utilizzando i predefiniti per set di batch, non *vengono visualizzati nell’interfaccia utente.)*

1. [Anteprima set 360 gradi](previewing-assets.md)

   Selezionate il set 360 gradi ed effettuate l’anteprima. Ruotate il set 360 gradi. Potete scegliere diversi visualizzatori dal menu **[!UICONTROL Visualizzatori]**, disponibile dal menu a discesa della barra a sinistra.

1. [Pubblicare Set 360 gradi](publishing-dynamicmedia-assets.md)

   La pubblicazione di un set 360 gradi attiva l’ordine in cui le immagini vengono visualizzate in un set 360 gradi. Accertatevi di ordinarli in modo che la rotazione sia una vista a 360 gradi uniforme.**** URL e  **** stringa da incorporare. Inoltre, è necessario [pubblicare il predefinito per visualizzatori](managing-viewer-presets.md).

1. [Collegate gli URL all’](linking-urls-to-yourwebapplication.md) applicazione Web o  [incorporate il visualizzatore](embed-code.md) video o immagini.

    AEM Assets crea richieste URL per i set 360 gradi e le attiva dopo la pubblicazione dei set 360 gradi. Potete copiare questi URL quando visualizzate l’anteprima delle risorse. In alternativa, potete incorporarli nel sito Web.

   Seleziona il set a 360 gradi, quindi fai clic su **[!UICONTROL Visualizzatori]** nel menu a discesa della barra a sinistra.

   Consulta le sezioni [Collegamento di un set 360 gradi a una pagina web](linking-urls-to-yourwebapplication.md) e [Incorporamento di un visualizzatore di video o immagini](embed-code.md).

Se necessario, potete [modificare i set 360 gradi](#editing-spin-sets). Inoltre, potete visualizzare e modificare le proprietà dei set 360 gradi [a1/>.](managing-assets-touch-ui.md#editing-properties)

## Caricamento delle risorse per i set 360 gradi {#uploading-assets-for-spin-sets}

Per un set 360 gradi monodimensionale, sono necessari almeno 8-12 scatti di un elemento e 16-24 scatti per un set 360 gradi bidimensionale. Le riprese devono essere effettuate a intervalli regolari per dare l’impressione che l’elemento stia ruotando e sia capovolto. Ad esempio, se un set 360 gradi monodimensionale include 12 scatti, ruotate l’elemento di 30 gradi (360/12) per ciascuna ripresa.

Potete caricare le immagini per i set 360 gradi come fareste per [caricare qualsiasi altra risorsa in  AEM Assets](managing-assets-touch-ui.md).

### Linee guida per lo scatto di immagini per set 360 gradi {#guidelines-for-shooting-spin-set-images}

Di seguito sono riportate alcune best practice per le immagini dei set 360 gradi. In generale, più immagini si trovano in un set 360 gradi, migliore sarà l’effetto di rotazione dell’immagine. Tuttavia, l’inclusione di molte immagini nel set aumenta anche il tempo necessario al caricamento delle immagini. AEM consigliate le seguenti linee guida per lo scatto di immagini da usare nei set 360 gradi:

* Utilizzate almeno 8-12 immagini in un set 360 gradi monodimensionale e 16-24 immagini in un set 360 gradi bidimensionale. Per poter ruotare di 360 gradi è necessario disporre di almeno 8 immagini. I set 360 gradi monodimensionali sono più comuni quando la creazione di set 360 gradi bidimensionali richiede molta manodopera.
* Utilizzare un formato senza perdita di dati; Si consigliano TIFF e PNG.
* Mascherate tutte le immagini in modo che l’elemento venga visualizzato su uno sfondo bianco puro o su un altro sfondo ad alto contrasto. Se necessario, aggiungete ombre.
* Accertatevi che i dettagli del prodotto siano ben illuminati e messi a fuoco.
* Scattare immagini per capi di abbigliamento di moda con un manichino o un modello. Spesso il manichino è completamente mascherato (utilizzando un manichino in vetro) oppure nell’immagine è visibile un manichino/un set di cornici stilizzato. Potete creare un set 360 gradi su un modello definendo il numero di angoli. Contrassegnare ogni angolo con nastro sul pavimento per guidare il modello a passo e guardare nella direzione di ogni ripresa.

## Creazione di set 360 gradi {#creating-spin-sets}

Ordine in cui le immagini vengono visualizzate in un set 360 gradi Accertatevi di ordinarli in modo che la rotazione sia una vista a 360 gradi uniforme.

>[!NOTE]
>
>Puoi anche creare in automatico i set 360 gradi da [predefiniti set di batch](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
>
>I set di batch vengono creati dall’IPS (Image Production System) come parte dell’assimilazione delle risorse e sono disponibili solo in modalità Dynamic Media - Scene7.
>
>Consultate &quot;Creazione di predefiniti per set di batch per generare automaticamente set di immagini e set 360 gradi&quot; in [Configurazione di Dynamic Media - Modalità Scene7](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**Per creare dei set 360 gradi:**

1. In Risorse, andate nel punto in cui desiderate creare un set 360 gradi, toccate **[!UICONTROL Crea]**, quindi selezionate **[!UICONTROL Set 360 gradi]**. Puoi anche creare il set dall’interno di una cartella contenente le risorse.

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. Nella pagina **[!UICONTROL Editor set 360 gradi]**, nel campo **[!UICONTROL Titolo]**, inserite un nome per il set 360 gradi. Il nome viene visualizzato nel banner lungo il set 360 gradi. Facoltativamente, immettete una descrizione.

   ![chlimage_1-382](assets/chlimage_1-382.png)

   Quando create il set 360 gradi, potete modificare la miniatura del set 360 gradi o consentire AEM selezionare la miniatura automaticamente in base alle risorse del set 360 gradi. Per selezionare una miniatura, toccare **[!UICONTROL Cambia miniatura]**. Selezionate un’immagine (per trovare le immagini potete spostarvi anche in altre cartelle). Se è stata selezionata una miniatura e si decide di AEM generare una miniatura dal set 360 gradi, selezionare **[!UICONTROL Passa alla miniatura automatica]**.

1. Effettuate una delle seguenti operazioni:

   * Nell’angolo in alto a sinistra della pagina **[!UICONTROL Editor set 360 gradi]**, toccate **[!UICONTROL Aggiungi risorsa]**.
   * Vicino al centro della pagina **[!UICONTROL Editor set 360 gradi]**, toccate **[!UICONTROL Toccate per aprire il selettore risorse]**.

   Toccate per selezionare le risorse da includere nel set 360 gradi. Le risorse selezionate dispongono di un’icona a forma di segno di spunta. Al termine, nell&#39;angolo superiore destro della pagina, toccare **[!UICONTROL Seleziona]**.

   Con il Selettore risorse, puoi cercare le risorse digitando una parola chiave e toccando **[!UICONTROL Invio]**. Per perfezionare i risultati della ricerca, puoi anche applicare i filtri. Puoi filtrare in base a percorso, raccolta, tipo di file e tag. Seleziona il filtro e tocca l’icona **[!UICONTROL Filtro]** nella barra degli strumenti. Per modificare la visualizzazione, accanto all&#39;angolo superiore destro della pagina, toccate l&#39;icona **[!UICONTROL Visualizza]**, quindi toccate **[!UICONTROL Vista a colonne]**, **[!UICONTROL Vista a schede]** o **[!UICONTROL Visualizzazione a elenco]**.

   Vedere [Utilizzo dei selettori](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Quando aggiungete delle risorse al set, queste vengono automaticamente aggiunte in ordine alfanumerico. Potete riordinare o ordinare manualmente le risorse dopo averle aggiunte. Se necessario, trascinate l&#39;icona **[!UICONTROL Riordina]** di una risorsa a destra del nome file della risorsa per riordinare le immagini verso l&#39;alto o verso il basso nell&#39;elenco dei set.

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. (Facoltativo) Effettuate una delle seguenti operazioni:

   * Per eliminare un&#39;immagine, selezionate l&#39;immagine, quindi toccate **[!UICONTROL Elimina risorsa]**.
   * Per applicare un predefinito, nell’angolo superiore destro della pagina toccate **[!UICONTROL Preset]**, quindi selezionate un predefinito da applicare a tutte le risorse alla volta.

1. Toccate **[!UICONTROL Salva]**. Il set 360 gradi appena creato viene visualizzato nella cartella in cui è stato creato.

## Visualizzazione dei set 360 gradi {#viewing-spin-sets}

Potete creare i set 360 gradi nell’interfaccia utente o automaticamente utilizzando i predefiniti per set di batch [](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). Tuttavia, i set creati utilizzando i predefiniti per set di batch, non *vengono visualizzati nell’interfaccia utente.* Potete accedere ai set creati mediante i predefiniti per set di batch in tre modi diversi. (Questi metodi sono disponibili anche se avete creato i set 360 gradi nell’interfaccia utente).

Potete inoltre visualizzare i set mediante l’interfaccia utente come descritto in [Modifica di set 360 gradi](#editing-spin-sets).

**Per visualizzare i set 360 gradi:**

1. Quando si aprono le proprietà di una singola risorsa. Le proprietà indicano i set di risorse selezionate come membro di (sotto **[!UICONTROL Membro di set]**). Toccate il nome del set per visualizzare l’intero set.

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. Da un’immagine inclusa in un qualsiasi set. Selezionate il menu **[!UICONTROL Set]** per visualizzare i set di cui la risorsa è membro.

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. Dalla ricerca è possibile selezionare **[!UICONTROL Filtri]**, quindi espandere **[!UICONTROL Dynamic Media]** e selezionare **[!UICONTROL Set]**.

   La ricerca restituisce i set corrispondenti creati manualmente nell’interfaccia utente o automaticamente tramite i predefiniti per set di batch. Per i set automatizzati, la query di ricerca viene eseguita utilizzando i criteri di ricerca **[!UICONTROL Inizia con]** diversi da quelli AEM basati sull&#39;utilizzo dei criteri di ricerca **[!UICONTROL Contiene]**. L&#39;impostazione del filtro su **[!UICONTROL Sets]** è l&#39;unico modo per eseguire ricerche nei set automatizzati.

   ![chlimage_1-386](assets/chlimage_1-386.png)

## Modifica dei set 360 gradi {#editing-spin-sets}

Potete eseguire diverse attività di modifica sui set 360 gradi, ad esempio:

* Aggiungete immagini al set 360 gradi.
* Riordinare le immagini nel set 360 gradi.
* Potete eliminare le risorse nel set 360 gradi.
* Applicate i predefiniti per visualizzatori.
* Eliminate il set 360 gradi.

**Per modificare un set 360 gradi:**

1. Effettuate una delle seguenti operazioni:

   * Passate il puntatore del mouse su una risorsa set 360 gradi, quindi toccate **[!UICONTROL Modifica]** (icona matita).
   * Passate il puntatore del mouse su una risorsa set 360 gradi, toccate **[!UICONTROL Seleziona]** (icona a forma di segno di spunta), quindi toccate **[!UICONTROL Modifica]** sulla barra degli strumenti.
   * Toccate una risorsa set 360 gradi, quindi toccate **[!UICONTROL Modifica]** (icona matita) sulla barra degli strumenti.

1. Per modificare il set 360 gradi, effettuate una delle seguenti operazioni:

   * Per riordinare le immagini, trascinate un’immagine in una nuova posizione (selezionate l’icona di riordinamento per spostare gli elementi).
   * Per ordinare gli elementi in ordine crescente o decrescente, toccate l’intestazione della colonna.
   * Per aggiungere una risorsa o aggiornare una risorsa esistente, toccate **[!UICONTROL Aggiungi risorsa]**. Andate a una risorsa, selezionatela, quindi toccate **[!UICONTROL Seleziona]** vicino all&#39;angolo superiore destro.
Se eliminate l’immagine che AEM usata per la miniatura sostituendola con un’altra immagine, viene comunque visualizzata la risorsa originale.
   * Per eliminare una risorsa, selezionatela e toccate **[!UICONTROL Elimina risorsa]**.
   * Per applicare un predefinito, toccate l&#39;icona **[!UICONTROL Preset]** e selezionate un predefinito.
   * Per eliminare un intero set 360 gradi, portatevi sul set 360 gradi, selezionatelo e selezionate **[!UICONTROL Elimina]**

      >[!NOTE]
      >* Per modificare le immagini di un set 360 gradi, toccate il set, toccate **[!UICONTROL Imposta membri]** nella barra a sinistra, quindi toccate l&#39; **[!UICONTROL Modifica]** (icona matita) su una singola risorsa per aprire la finestra di modifica.


1. Fare clic su **[!UICONTROL Save]** al termine della modifica.

## Anteprima dei set 360 gradi {#previewing-spin-sets}

Consultate [Anteprima delle risorse](previewing-assets.md).

## Pubblicazione di set 360 gradi {#publishing-spin-sets}

Consultate [Pubblicazione di risorse](publishing-dynamicmedia-assets.md).
