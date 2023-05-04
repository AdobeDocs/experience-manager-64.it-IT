---
title: Set di file multimediali diversi
description: Scopri come lavorare con set di file multimediali diversi (immagini, set di immagini, set 360 gradi e video) in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 252c1a50-17ac-4412-88d6-49bb6850658d
feature: Mixed Media Sets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 19%

---

# Set di file multimediali diversi {#mixed-media-sets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I set di file multimediali diversi consentono di fornire un mix di immagini, set di immagini, set 360 gradi e video in una presentazione.

I set di file multimediali diversi sono indicati da un banner con la parola **[!UICONTROL MixedMediaSet]**. Inoltre, se il set di file multimediali diversi è pubblicato, la data di pubblicazione, indicata dall’icona **[!UICONTROL mondo]**, è riportata sul banner insieme all’ultima data di modifica, contrassegnata dall’icona a forma di **[!UICONTROL matita]**.

![chlimage_1-348](assets/chlimage_1-348.png)

>[!NOTE]
>
>Per informazioni sull’interfaccia utente di Assets, consulta [Gestione delle risorse con l’interfaccia utente touch](managing-assets-touch-ui.md).

## Avvio rapido: Set di file multimediali diversi {#quick-start-mixed-media-sets}

Per iniziare rapidamente a usare i set di file multimediali diversi, effettua le seguenti operazioni:

1. [Caricare le risorse](#uploading-assets).

   Per iniziare, carica le immagini e i video per i set di file multimediali diversi. Se necessario, crea i [Set di immagini](image-sets.md) e i [Set 360 gradi](spin-sets.md). Poiché gli utenti possono eseguire lo zoom sulle immagini nel Visualizzatore set di file multimediali diversi, calcola lo zoom al momento di scegliere le immagini. Verifica che le immagini abbiano una dimensione maggiore che sia di almeno 2000 pixel.

1. [Creare set di file multimediali diversi.](#creating-mixed-media-sets)

   Per creare un set di file multimediali diversi, dai **[!UICONTROL Risorse]** pagina, tocca **[!UICONTROL Crea > Set di file multimediali diversi]**, quindi denomina il set. Scegli le risorse, quindi scegli l’ordine in cui vengono visualizzate le immagini.

   Vedi [Utilizzo dei selettori.](working-with-selectors.md)

1. Configurazione [Predefiniti visualizzatore di file multimediali diversi](managing-viewer-presets.md), se necessario.

   Gli amministratori possono creare o modificare i predefiniti visualizzatore di set di file multimediali diversi predefiniti. Per visualizzare i file multimediali diversi con un predefinito per visualizzatori, seleziona il set di file multimediali diversi e fai clic su **[!UICONTROL Visualizzatori]** nel menu a discesa della barra a sinistra.

   Vedi **[!UICONTROL Strumenti > Risorse > Predefiniti visualizzatore]** per creare o modificare i predefiniti visualizzatore.

   Vedi [Aggiunta e modifica dei predefiniti per visualizzatori.](managing-viewer-presets.md)

1. [Anteprima di set di file multimediali diversi.](#previewing-mixed-media-sets)

   Seleziona il set di file multimediali diversi e puoi visualizzarlo in anteprima. Fai clic sulle icone delle miniature per esaminare il set di file multimediali diversi nel visualizzatore selezionato. Puoi scegliere diversi visualizzatori dal **[!UICONTROL Visualizzatori]** disponibile dal menu a discesa della barra a sinistra.

1. [Pubblicare Set Di File Multimediali Misti.](#publishing-mixed-media-sets)

   La pubblicazione di un set di file multimediali diversi attiva l’URL e la stringa di incorporamento. Inoltre, devi [pubblicare il predefinito visualizzatore](managing-viewer-presets.md#publishing-viewer-presets).

1. [Collegare gli URL all’applicazione Web](linking-urls-to-yourwebapplication.md) o [Incorporare il visualizzatore di video o immagini](embed-code.md).

   AEM Assets crea chiamate URL per set di file multimediali diversi e li attiva dopo la pubblicazione dei set di file multimediali diversi. Puoi copiare questi URL quando visualizzi l’anteprima delle risorse. In alternativa è possibile incorporarli sul sito Web.

   Seleziona il set di file multimediali diversi, quindi seleziona dal menu a discesa della barra a sinistra **[!UICONTROL Visualizzatori]**.

   Consulta le sezioni [Collegamento di un set di file multimediali diversi a una pagina web](linking-urls-to-yourwebapplication.md) e [Incorporamento di un visualizzatore di video o immagini](embed-code.md).

Se necessario, è possibile modificare [Set di file multimediali diversi](#editing-mixed-media-sets). Inoltre, puoi visualizzare e modificare [Proprietà set di file multimediali diversi](managing-assets-touch-ui.md#editing-properties).

>[!NOTE]
>
>In caso di problemi nella creazione dei set, vedi [Risoluzione dei problemi Dynamic Media - Modalità Scene7](troubleshoot-dms7.md).

## Caricamento delle risorse {#uploading-assets}

Per iniziare, carica le immagini e i video per i set di file multimediali diversi. Poiché gli utenti possono eseguire lo zoom sulle immagini nel visualizzatore di set di file multimediali diversi, accertati di tenere conto dello zoom quando scegli le immagini. Verifica che le immagini abbiano una dimensione maggiore che sia di almeno 2000 pixel.

Inoltre, se desideri aggiungere set 360 gradi o set di immagini al set di file multimediali diversi, crea anche questi.

## Creazione di set di file multimediali diversi {#creating-mixed-media-sets}

Puoi aggiungere immagini, set di immagini, set 360 gradi e video al set di file multimediali diversi. Assicurati che i file, i set di immagini e i set 360 gradi siano pronti per la pubblicazione prima di aggiungerli al set di file multimediali diversi.

Quando aggiungi delle risorse al set, queste vengono aggiunte automaticamente in ordine alfanumerico. Puoi riordinare o ordinare manualmente le risorse dopo averle aggiunte.

**Per creare un set di file multimediali diversi**:

1. In Assets, individua il punto in cui vuoi creare un set di file multimediali diversi, fai clic su **Crea** e seleziona **[!UICONTROL Set di file multimediali diversi]**. Puoi anche creare il set dall’interno di una cartella contenente le risorse.

   ![chlimage_1-349](assets/chlimage_1-349.png)

1. In **[!UICONTROL Editor set di file multimediali diversi]** in **[!UICONTROL Titolo]**, immetti un nome per il set di file multimediali diversi. Il nome viene visualizzato nel banner nel set di file multimediali diversi. Facoltativamente, immetti una descrizione.

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Quando crei il set di file multimediali diversi, puoi modificare la miniatura del set di file multimediali diversi o consentire AEM selezionare automaticamente la miniatura in base alle risorse nel set di file multimediali diversi. Per selezionare una miniatura, fai clic su **[!UICONTROL Modifica miniatura]** e seleziona qualsiasi immagine (puoi passare ad altre cartelle per trovare anche le immagini). Se hai selezionato una miniatura e poi decidi di AEM generarne una dal set di file multimediali diversi, seleziona **[!UICONTROL Passa alla miniatura automatica]**.

1. Tocca **[!UICONTROL Selettore risorse]** per selezionare le risorse da includere nel set di file multimediali diversi. Seleziona e tocca **[!UICONTROL Seleziona]**.

   Con la **[!UICONTROL Selettore risorse]**, puoi cercare le risorse digitando una parola chiave e toccando **[!UICONTROL Ritorno]**. Per perfezionare i risultati della ricerca, puoi anche applicare i filtri. Puoi filtrare in base a percorso, raccolta, tipo di file e tag. Seleziona il filtro e tocca l’icona **[!UICONTROL Filtro]** nella barra degli strumenti. Per modificare la visualizzazione, seleziona l’icona Visualizza e fai clic su **[!UICONTROL Elenco]**, **[!UICONTROL Colonna]** oppure **[!UICONTROL Scheda]** visualizza.

   Vedi [Utilizzo dei selettori](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. Riordinare le risorse trascinandole verso l’alto o verso il basso nell’elenco (deve selezionare l’icona di riordino), a seconda delle necessità.

   ![chlimage_1-352](assets/chlimage_1-352.png)

   Per aggiungere le miniature, fai clic sul pulsante **[!UICONTROL +]** accanto all’immagine e passa alla miniatura desiderata. Dopo aver selezionato tutte le miniature, tocca **[!UICONTROL Salva]**.

   >[!NOTE]
   >
   >Per aggiungere risorse, tocca **[!UICONTROL Aggiungi risorsa]**.

1. Per eliminare una risorsa, seleziona la casella di controllo corrispondente e tocca **[!UICONTROL Elimina risorsa]**.
1. Per applicare un predefinito, tocca **[!UICONTROL Predefinito]** nell’angolo in alto a destra e seleziona un predefinito da applicare alle risorse.
1. Fai clic su **[!UICONTROL Salva]**. Il set di file multimediali diversi appena creato viene visualizzato nella cartella in cui è stato creato.

## Modifica di set di file multimediali diversi {#editing-mixed-media-sets}

Puoi eseguire diverse attività di modifica alle risorse in Set di file multimediali diversi direttamente nell’interfaccia utente [come qualsiasi risorsa in Assets](managing-assets-touch-ui.md). In Set di file multimediali diversi è inoltre possibile effettuare le seguenti operazioni:

* Aggiungi le risorse al set di file multimediali diversi.
* Riordinare le risorse nel set di file multimediali diversi.
* Elimina le risorse nel set di file multimediali diversi.
* Applica i predefiniti visualizzatore.
* Modifica la miniatura predefinita.

**Per modificare i set di file multimediali diversi**:

1. Effettua una delle seguenti operazioni:

   * Passa il puntatore del mouse su una risorsa del set di file multimediali diversi, quindi tocca **[!UICONTROL Modifica]** (icona a forma di matita).
   * Passa il puntatore del mouse su una risorsa del set di file multimediali diversi e tocca **[!UICONTROL Seleziona]** (icona a forma di segno di spunta), quindi tocca **[!UICONTROL Modifica]** sulla barra degli strumenti.
   * Tocca una risorsa del set di file multimediali diversi, quindi tocca **[!UICONTROL Modifica]** (icona a forma di matita) sulla barra degli strumenti.

1. Nell’Editor set di file multimediali diversi, effettua una delle seguenti operazioni:

   * Per riordinare le risorse: nel pannello a sinistra, tocca **[!UICONTROL Risorse]** (icona immagine), trascina una risorsa in una nuova posizione.
   * Per aggiungere risorse, tocca sulla barra degli strumenti **[!UICONTROL Aggiungi risorsa]**. Passa alle risorse. Per ogni risorsa da aggiungere, passa il cursore del mouse sull’immagine della risorsa (non sul nome della risorsa), quindi tocca l’icona a forma di segno di spunta. Nell’angolo in alto a destra, tocca **[!UICONTROL Seleziona]**.
   * Per eliminare una risorsa: nel pannello a sinistra, tocca **[!UICONTROL Risorse]** (icona immagine), quindi seleziona la risorsa. Nella barra degli strumenti, tocca **[!UICONTROL Elimina risorsa]**.
   * Per ordinare le risorse in base al loro nome in ordine crescente o decrescente, nel pannello a sinistra tocca **[!UICONTROL Risorse]** (icona immagine). A destra del **[!UICONTROL Risorse]** intestazione, toccare le icone del cursore verso l’alto o verso il basso.

   >[!NOTE]
   >
   >* Per eliminare un intero set di file multimediali diversi da qualsiasi modalità di visualizzazione (ad esempio **[!UICONTROL Scheda]** visualizzare o **[!UICONTROL Colonna]** visualizza) vai al set di file multimediali diversi. Passa il puntatore del mouse sulla risorsa, quindi tocca l’icona del segno di spunta per selezionarla. Press **[!UICONTROL Backspace]** sulla tastiera o tocca **[!UICONTROL Altro]** (tre punti) sulla barra degli strumenti, quindi tocca **[!UICONTROL Elimina]**.
   >* Per modificare le risorse di un set di file multimediali diversi, tocca il set e fai clic su . **[!UICONTROL Imposta membri]** nella barra a sinistra, quindi tocca **[!UICONTROL Matita]** su una singola risorsa per aprire la finestra di modifica.


1. Tocca **[!UICONTROL Salva]** al termine della modifica.

   >[!NOTE]
   >
   >* Per modificare le risorse in un set di file multimediali diversi, passa a Set di file multimediali diversi. Tocca (non selezionare) il set per aprirlo nel AEM **[!UICONTROL Imposta anteprima]** pagina. Nella barra a sinistra, tocca il cursore verso il basso per aprire l’elenco a discesa, quindi tocca **[!UICONTROL Imposta membri]**. In **[!UICONTROL Imposta membri]** pagina, passa il mouse su una risorsa, quindi tocca **[!UICONTROL Modifica]** (icona a forma di matita) per aprire la pagina di modifica.
   >* Per eliminare un intero set di file multimediali diversi: da qualsiasi modalità di visualizzazione (ad esempio **[!UICONTROL Scheda]** visualizzare o **[!UICONTROL Colonna]** visualizza), passa al set di file multimediali diversi. Passa il puntatore del mouse sul set, quindi tocca **[!UICONTROL Seleziona]** (icona a forma di segno di spunta). Press **[!UICONTROL Backspace]** sulla tastiera o tocca **[!UICONTROL Altro]** (riga di tre punti), quindi tocca **[!UICONTROL Elimina]**.


## Anteprima dei set di file multimediali diversi {#previewing-mixed-media-sets}

Vedi [Anteprima delle risorse](previewing-assets.md) per informazioni dettagliate su come visualizzare in anteprima i set di file multimediali diversi.

## Pubblicazione di set di file multimediali diversi {#publishing-mixed-media-sets}

Vedi [Pubblicazione delle risorse](publishing-dynamicmedia-assets.md) per informazioni dettagliate su come pubblicare set di file multimediali diversi.

>[!NOTE]
>
>Se al primo momento della pubblicazione il set di file multimediali diversi non viene completamente incluso nel servizio di consegna, potrebbe essere necessario pubblicare il set di file multimediali diversi una seconda volta.
