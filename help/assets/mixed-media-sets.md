---
title: Set di file multimediali diversi
seo-title: Set di file multimediali diversi
description: Scoprite come utilizzare i set di file multimediali diversi nei contenuti multimediali dinamici
seo-description: Scoprite come utilizzare i set di file multimediali diversi nei contenuti multimediali dinamici
uuid: e37fa648-74e2-42e3-8611-8509c92ec00d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 599c316e-b6a7-4a28-bc4b-75d48409bde0
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 19%

---


# Set di file multimediali diversi {#mixed-media-sets}

I set di file multimediali diversi consentono di fornire immagini, set di immagini, set 360 gradi e video in un’unica presentazione.

I set di file multimediali diversi sono indicati da un banner con la parola **[!UICONTROL MixedMediaSet]**. Inoltre, se il set di file multimediali diversi è pubblicato, la data di pubblicazione, indicata dall’icona **[!UICONTROL mondo]**, è riportata sul banner insieme all’ultima data di modifica, contrassegnata dall’icona a forma di **[!UICONTROL matita]**.

![chlimage_1-348](assets/chlimage_1-348.png)

>[!NOTE]
>
>Per informazioni sull’interfaccia utente di Assets, consulta [Gestione delle risorse con l’interfaccia](managing-assets-touch-ui.md)touch.

## Avvio rapido: Set di file multimediali diversi {#quick-start-mixed-media-sets}

Per iniziare rapidamente a usare i set di file multimediali diversi, effettuate le seguenti operazioni:

1. [Caricate le risorse](#uploading-assets).

   Per iniziare, carica le immagini e i video per i set di file multimediali diversi. Se necessario, crea i [Set di immagini](image-sets.md) e i [Set 360 gradi](spin-sets.md). Poiché gli utenti possono eseguire lo zoom sulle immagini nel Visualizzatore set di file multimediali diversi, calcola lo zoom al momento di scegliere le immagini. Verifica che le immagini abbiano una dimensione maggiore che sia di almeno 2000 pixel.

1. [Creare set di file multimediali diversi.](#creating-mixed-media-sets)

   Per creare un set di file multimediali diversi, dalla pagina **[!UICONTROL Risorse]** toccate **[!UICONTROL Crea > Set]** di file multimediali diversi, quindi assegnate un nome al set. Scegliete le risorse, quindi scegliete l’ordine di visualizzazione delle immagini.

   See [Working with Selectors.](working-with-selectors.md)

1. Impostate i predefiniti [per visualizzatori](managing-viewer-presets.md)di file multimediali diversi in base alle esigenze.

   Gli amministratori possono creare o modificare i predefiniti visualizzatore di set di file multimediali diversi predefiniti. Per visualizzare i file multimediali diversi con un predefinito per visualizzatori, seleziona il set di file multimediali diversi e fai clic su **[!UICONTROL Visualizzatori]** nel menu a discesa della barra a sinistra.

   Consultate **[!UICONTROL Strumenti > Risorse > Predefiniti]** visualizzatore per creare o modificare i predefiniti per visualizzatori.

   Consultate [Aggiunta e modifica dei predefiniti per visualizzatori.](managing-viewer-presets.md)

1. [Anteprima set di file multimediali diversi.](#previewing-mixed-media-sets)

   Selezionate il set di file multimediali diversi ed effettuate l’anteprima. Fate clic sulle icone delle miniature per esaminare il set di file multimediali diversi nel visualizzatore selezionato. Potete scegliere diversi visualizzatori dal menu **[!UICONTROL Visualizzatori]** , disponibile dal menu a discesa della barra a sinistra.

1. [Pubblicare Set Di File Multimediali Diversi](#publishing-mixed-media-sets)

   La pubblicazione di un set di file multimediali diversi attiva la stringa URL e incorpora. Inoltre, dovete [pubblicare il predefinito](managing-viewer-presets.md#publishing-viewer-presets)per visualizzatori.

1. [Collegare gli URL all’applicazione](linking-urls-to-yourwebapplication.md) Web o [incorporare il visualizzatore](embed-code.md)video o immagini.

    AEM Assets crea richieste di URL per i set di file multimediali diversi e li attiva dopo la pubblicazione dei set di file multimediali diversi. Potete copiare questi URL quando visualizzate l’anteprima delle risorse. In alternativa, potete incorporarli nel sito Web.

   Select the Mixed Media Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   Consulta le sezioni [Collegamento di un set di file multimediali diversi a una pagina web](linking-urls-to-yourwebapplication.md) e [Incorporamento di un visualizzatore di video o immagini](embed-code.md).

Se necessario, potete modificare i set [di file multimediali](#editing-mixed-media-sets)diversi. Inoltre, potete visualizzare e modificare le proprietà [dei set di file multimediali](managing-assets-touch-ui.md#editing-properties)diversi.

>[!NOTE]
>
>In caso di problemi durante la creazione dei set, consultate [Risoluzione dei problemi relativi ai file multimediali dinamici - Modalità](troubleshoot-dms7.md)Scene7.

## Caricamento delle risorse {#uploading-assets}

Per iniziare, carica le immagini e i video per i set di file multimediali diversi. Poiché gli utenti possono eseguire lo zoom sulle immagini nel visualizzatore di set di file multimediali diversi, quando scegliete le immagini tenete conto dello zoom. Verifica che le immagini abbiano una dimensione maggiore che sia di almeno 2000 pixel.

Inoltre, se desiderate aggiungere set 360 gradi o set di immagini al set di file multimediali diversi, create anche questi.

## Creazione di set di file multimediali diversi {#creating-mixed-media-sets}

Potete aggiungere immagini, set di immagini, set 360 gradi e video al set di file multimediali diversi. Assicuratevi che i file, i set di immagini e i set 360 gradi siano pronti per la pubblicazione prima di aggiungerli al set di file multimediali diversi.

Quando aggiungete delle risorse al set, queste vengono automaticamente aggiunte in ordine alfanumerico. Potete riordinare o ordinare manualmente le risorse dopo averle aggiunte.

**Per creare un set** di file multimediali diversi:

1. In Assets, individua il punto in cui vuoi creare un set di file multimediali diversi, fai clic su **Crea** e seleziona **[!UICONTROL Set di file multimediali diversi]**. Puoi anche creare il set dall’interno di una cartella contenente le risorse.

   ![chlimage_1-349](assets/chlimage_1-349.png)

1. Nella pagina Editor **[!UICONTROL set di file multimediali]** diversi, in **[!UICONTROL Titolo]**, inserite un nome per il set di file multimediali diversi. Il nome viene visualizzato nel banner all’interno del set di file multimediali diversi. Facoltativamente, immettete una descrizione.

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Quando create il set di file multimediali diversi, potete modificare la miniatura del set di file multimediali diversi o consentire AEM selezionare la miniatura automaticamente in base alle risorse del set di file multimediali diversi. Per selezionare una miniatura, fate clic su **[!UICONTROL Cambia miniatura]** e selezionate una qualsiasi immagine (per trovare anche le immagini potete spostarvi in altre cartelle). If you have selected a thumbnail and then decide that you want AEM to generate one from the mixed media set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. Toccate il selettore **[!UICONTROL delle]** risorse per selezionare le risorse che desiderate includere nel set di file multimediali diversi. Selezionateli e toccate **[!UICONTROL Seleziona]**.

   With the **[!UICONTROL Asset Selector]**, you can search for assets by typing in a keyword and tapping **[!UICONTROL Return]**. Per perfezionare i risultati della ricerca, puoi anche applicare i filtri. Puoi filtrare in base a percorso, raccolta, tipo di file e tag. Seleziona il filtro e tocca l’icona **[!UICONTROL Filtro]** nella barra degli strumenti. Change the view by selecting the View icon and selecting **[!UICONTROL List]**, **[!UICONTROL Column]**, or **[!UICONTROL Card]** view.

   See [Working with Selectors](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. Riordinate le risorse trascinandole verso l’alto o verso il basso nell’elenco (se necessario, selezionate l’icona di riordinamento).

   ![chlimage_1-352](assets/chlimage_1-352.png)

   If you want to add thumbnails, click the **[!UICONTROL +]** icon next to the image and navigate to the thumbnail you want. Dopo aver selezionato tutte le miniature, toccate **[!UICONTROL Salva]**.

   >[!NOTE]
   >
   >Per aggiungere delle risorse, toccate **[!UICONTROL Aggiungi risorsa]**.

1. Per eliminare una risorsa, selezionate la casella di controllo corrispondente e toccate **[!UICONTROL Elimina risorsa]**.
1. Per applicare un predefinito, toccate **[!UICONTROL Predefinito]** nell’angolo in alto a destra e selezionate un predefinito da applicare alle risorse.
1. Fai clic su **[!UICONTROL Salva]**. Il set di file multimediali diversi appena creato viene visualizzato nella cartella in cui è stato creato.

## Modifica di set di file multimediali diversi {#editing-mixed-media-sets}

Potete eseguire diverse attività di modifica delle risorse in set di file multimediali diversi direttamente nell’interfaccia utente, [come qualsiasi risorsa in Risorse](managing-assets-touch-ui.md). In Set di file multimediali diversi potete inoltre effettuare le seguenti operazioni:

* Aggiungete le risorse al set di file multimediali diversi.
* Riordinare le risorse nel set di file multimediali diversi.
* Potete eliminare le risorse nel set di file multimediali diversi.
* Applicate i predefiniti per visualizzatori.
* Modificare la miniatura predefinita.

**Per modificare i set** di file multimediali diversi:

1. Effettuate una delle seguenti operazioni:

   * Passate il puntatore del mouse su una risorsa del set di file multimediali diversi, quindi toccate **[!UICONTROL Modifica]** (icona matita).
   * Passate il puntatore del mouse su una risorsa di set di file multimediali diversi, toccate **[!UICONTROL Seleziona]** (icona a forma di segno di spunta), quindi toccate **[!UICONTROL Modifica]** sulla barra degli strumenti.
   * Toccate una risorsa set di file multimediali diversi, quindi toccate **[!UICONTROL Modifica]** (icona matita) nella barra degli strumenti.

1. Nell’editor di set di file multimediali diversi, effettuate una delle seguenti operazioni:

   * Per riordinare le risorse - Nel pannello a sinistra, toccate **[!UICONTROL Risorse]** (icona immagine), trascinate una risorsa in una nuova posizione.
   * Per aggiungere risorse, toccate **[!UICONTROL Aggiungi risorsa]** nella barra degli strumenti. Andate alle risorse. Per ciascuna risorsa da aggiungere, passate il mouse sull&#39;immagine della risorsa (non sul nome della risorsa), quindi toccate l&#39;icona del segno di spunta. Nell&#39;angolo superiore destro, toccate **[!UICONTROL Seleziona]**.
   * Per eliminare una risorsa, toccate **[!UICONTROL Risorse]** (icona immagine) nel pannello a sinistra, quindi selezionate la risorsa. Nella barra degli strumenti toccate **[!UICONTROL Elimina risorsa]**.
   * Per ordinare le risorse in ordine crescente o decrescente in base al nome, toccate **[!UICONTROL Risorse]** nel pannello a sinistra (icona immagine). A destra dell’intestazione **[!UICONTROL Risorse]** , toccate le icone del carrello su o giù.

   >[!NOTE]
   >
   >* To delete an entire Mixed Media Set, from any viewing mode (such as **[!UICONTROL Card]** view or **[!UICONTROL Column]** view) navigate to the Mixed Media Set. Passa il puntatore del mouse sulla risorsa, quindi tocca l’icona del segno di spunta per selezionarla. Press **[!UICONTROL Backspace]** on the keyboard, or tap **[!UICONTROL More]** (three dots) on the toolbar, then tap **[!UICONTROL Delete]**.
   >* You can edit the assets in a Mixed Media Set by navigating to the set, tapping **[!UICONTROL Set Members]** in the left rail, and then tapping the **[!UICONTROL Pencil]** icon on an individual asset to open the editing window.


1. Toccate **[!UICONTROL Save** al termine della modifica.

   >[!NOTE]
   >
   >* Per modificare le risorse in un set di file multimediali diversi, passa a Set di file multimediali diversi. Tap (do not select) the set to open it in the AEM **[!UICONTROL Set Preview]** page. In the left rail, tap the down caret to open the drop-down list, then tap **[!UICONTROL Set Members]**. In the **[!UICONTROL Set Members]** page, hover on an asset, then tap **[!UICONTROL Edit]** (pencil icon) to open the editing page.
   >* To delete an entire Mixed Media Set - From any viewing mode (such as **[!UICONTROL Card]** view or **[!UICONTROL Column]** view), navigate to the Mixed Media Set. Hover on the set, then tap **[!UICONTROL Select]** (checkmark icon). Press **[!UICONTROL Backspace]** on your keyboard, or tap **[!UICONTROL More]** (row of three dots), then tap **[!UICONTROL Delete]**.


## Anteprima dei set di file multimediali diversi {#previewing-mixed-media-sets}

Consultate [Anteprima delle risorse](previewing-assets.md) per informazioni sull’anteprima dei set di file multimediali diversi.

## Pubblicazione di set di file multimediali diversi {#publishing-mixed-media-sets}

Consultate [Pubblicazione delle risorse](publishing-dynamicmedia-assets.md) per informazioni dettagliate sulla pubblicazione dei set di file multimediali diversi.

>[!NOTE]
>
>Se il set di file multimediali diversi non viene completamente incluso nel servizio di distribuzione al primo pubblicazione, potrebbe essere necessario pubblicarlo una seconda volta.

