---
title: Risoluzione delle dipendenze dei file
seo-title: Risoluzione delle dipendenze dei file
description: Come risolvere le dipendenze dei file 3D, ad esempio i file delle mappe di texture quando la risoluzione automatica non riesce.
seo-description: Come risolvere le dipendenze dei file 3D, ad esempio i file delle mappe di texture quando la risoluzione automatica non riesce.
uuid: 49cefabf-147b-4a78-90f3-0f2d6a8e8cae
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 05b7410b-82a1-4267-ac07-2edbc29e9ee8
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 37%

---


# Risoluzione delle dipendenze dei file {#resolving-file-dependencies}

Le dipendenze principali dei file del modello 3D, come i file di mappe texture, vengono automaticamente risolte quando possibile. Questa funzionalità viene eseguita effettuando una ricerca AEM nelle cartelle Risorse vicine per trovare file con gli stessi nomi presenti nel file 3D. Se una o più dipendenze non sono risolvibili durante la fase di elaborazione della creazione dell&#39;anteprima, nella scheda della risorsa viene visualizzato il seguente messaggio del banner rosso nella **[!UICONTROL vista a schede]**:

![chlimage_1-124](assets/chlimage_1-124.png)

**Per risolvere le dipendenze dei file**:

1. Nella **[!UICONTROL vista a schede]**, posizionate il puntatore sul messaggio del banner **[!UICONTROL Dipendenze non risolte]** presente sulla scheda, quindi toccate l&#39;icona **[!UICONTROL Punto esclamativo]**.

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. Nella pagina **[!UICONTROL Proprietà metadati]**, toccate la scheda **[!UICONTROL Dipendenze]**.

   I file che AEM non è stato possibile risolvere automaticamente sono elencati nella colonna **[!UICONTROL Percorsi originali]**, in rosso.

1. Esegui una o più delle seguenti operazioni:

   * **Individua e seleziona le dipendenze**. (Questa opzione presuppone che siano già stati caricati i file di dipendenza.

      1. Toccate l&#39;icona **[!UICONTROL File Browse]** a sinistra del percorso rosso.
      1. Nella pagina **[!UICONTROL Seleziona contenuto]**, andate al file mancante, quindi toccate la scheda del file per selezionarlo.
      1. Nell&#39;angolo superiore sinistro della pagina **[!UICONTROL Seleziona contenuto]**, toccare **[!UICONTROL Chiudi]** (icona X) per tornare alla pagina **[!UICONTROL Visualizza proprietà]**.
   * **Carica le dipendenze**. (Questa opzione presuppone che ancora non siano stati caricati i file mancanti.)

      1. Osserva i percorsi e i nomi dei file mancanti.
      1. Vicino all’angolo superiore destro della pagina delle proprietà, tocca **[!UICONTROL Chiudi]**.

   Dopo il caricamento, tornate alla pagina **[!UICONTROL Visualizza proprietà > Dipendenze]**. Le risorse appena caricate sono ora correttamente elencate come risorse di riferimento.

   * **Ignora le dipendenze**.

      Se non è più necessaria una dipendenza mancante, nella colonna **[!UICONTROL Risorsa di riferimento]**, nel campo di testo a sinistra del file mancante digitare `n/a` in modo che AEM 3D ignori il file.



1. Nell&#39;angolo superiore destro della pagina **[!UICONTROL Visualizza proprietà]**, toccare **[!UICONTROL Salva]**.
1. Tocca **[!UICONTROL Chiudi]****[!UICONTROL per tornare alla Vista a schede]**.

   La risorsa viene rielaborata automaticamente con le nuove dipendenze risolte.

