---
title: Risoluzione delle dipendenze dei file
seo-title: Risoluzione delle dipendenze dei file
description: Le dipendenze principali dei file del modello 3D, come i file di mappe texture, vengono automaticamente risolte quando possibile. Questa funzionalità viene eseguita effettuando una ricerca AEM nelle cartelle Risorse vicine per trovare file con gli stessi nomi presenti nel file 3D.
seo-description: Le dipendenze principali dei file del modello 3D, come i file di mappe texture, vengono automaticamente risolte quando possibile. Questa funzionalità viene eseguita effettuando una ricerca AEM nelle cartelle Risorse vicine per trovare file con gli stessi nomi presenti nel file 3D.
uuid: b1b83cb7-b6e5-4417-9a53-b6d8bcf8d2e0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 14754023-e7c4-4dc5-a9d8-408b81861d95
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 59%

---


# Risoluzione delle dipendenze dei file{#resolving-file-dependencies}

Le dipendenze principali dei file del modello 3D, come i file di mappe texture, vengono automaticamente risolte quando possibile. Questa funzionalità viene eseguita effettuando una ricerca AEM nelle cartelle Risorse vicine per trovare file con gli stessi nomi presenti nel file 3D. Se una o più dipendenze non sono risolvibili durante la fase di elaborazione della creazione dell&#39;anteprima, nella scheda della risorsa viene visualizzato il seguente messaggio del banner rosso nella [!UICONTROL vista a schede]:

![chlimage_1-189](assets/chlimage_1-189.png)

**Per risolvere le dipendenze dei file**:

1. Nella **[!UICONTROL vista a schede]**, posizionate il puntatore sul messaggio del banner **[!UICONTROL Dipendenze non risolte]** della scheda, quindi toccate l&#39;icona del punto esclamativo.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. Nella pagina delle proprietà metadati, tocca la scheda **[!UICONTROL Dipendenze]**.

   I file che AEM non è riuscita a risolvere in automatico sono elencati in rosso nella colonna Percorsi originali.

1. Esegui una o più delle seguenti operazioni:

   * **[!UICONTROL Individua e seleziona le dipendenze]**. (Questa opzione presuppone che siano già stati caricati i file di dipendenza.

      1. Toccate l&#39;icona **[!UICONTROL File Browse]** a sinistra del percorso rosso.
      1. Nella pagina **[!UICONTROL Seleziona contenuto]**, andate al file mancante, quindi toccate la scheda del file per selezionarlo.
      1. Nell&#39;angolo superiore sinistro della pagina **[!UICONTROL Seleziona contenuto]**, toccare **[!UICONTROL Chiudi]** (icona X) per tornare alla pagina **[!UICONTROL Visualizza proprietà]**.
   * **[!UICONTROL Carica le dipendenze]**. (Questa opzione presuppone che ancora non siano stati caricati i file mancanti.)

      1. Osserva i percorsi e i nomi dei file mancanti.
      1. Vicino all’angolo superiore destro della pagina delle proprietà, tocca **[!UICONTROL Chiudi]**.

   Dopo il caricamento, tornate alla pagina **[!UICONTROL Visualizza proprietà > Dipendenze]**. Le risorse appena caricate sono ora correttamente elencate come risorse di riferimento.

   * **[!UICONTROL Ignora le dipendenze]**.

      Se non è più necessaria una dipendenza mancante, nella colonna **[!UICONTROL Risorsa di riferimento]**, nel campo di testo a sinistra del file mancante digitare `n/a` in modo che AEM 3D ignori il file.



1. Nell&#39;angolo superiore destro della pagina **[!UICONTROL Visualizza proprietà]**, toccare **[!UICONTROL Salva]**.
1. Tocca **[!UICONTROL Chiudi]****[!UICONTROL per tornare alla Vista a schede]**.

   La risorsa viene rielaborata automaticamente con le nuove dipendenze risolte.

