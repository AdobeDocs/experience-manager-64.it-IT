---
title: Risoluzione delle dipendenze dei file
seo-title: Risoluzione delle dipendenze dei file
description: Come risolvere le dipendenze dei file 3D, come i file di mappa della texture quando la risoluzione automatica non riesce.
seo-description: Come risolvere le dipendenze dei file 3D, come i file di mappa della texture quando la risoluzione automatica non riesce.
uuid: 49cefabf-147b-4a78-90f3-0f2d6a8e8cae
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 05b7410b-82a1-4267-ac07-2edbc29e9ee8
exl-id: 088d32a8-a47e-4ae6-a171-8d327d3dac64
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 37%

---

# Risoluzione delle dipendenze dei file {#resolving-file-dependencies}

Le dipendenze principali dei file del modello 3D, come i file di mappe texture, vengono automaticamente risolte quando possibile. Questa funzionalità viene eseguita effettuando una ricerca AEM nelle cartelle Risorse vicine per trovare file con gli stessi nomi presenti nel file 3D. Se una o più dipendenze non sono risolvibili durante la fase di elaborazione Creazione dell’anteprima, la scheda della risorsa visualizza il seguente messaggio del banner rosso nella **[!UICONTROL Vista a schede]**:

![chlimage_1-124](assets/chlimage_1-124.png)

**Per risolvere le dipendenze dei file**:

1. Nella **[!UICONTROL Vista a schede]**, posiziona il puntatore del mouse sul messaggio del banner **[!UICONTROL Dipendenze non risolte]** presente nella scheda, quindi tocca l&#39;icona **[!UICONTROL Punto esclamativo]**.

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. Nella pagina **[!UICONTROL Proprietà metadati]**, tocca la scheda **[!UICONTROL Dipendenze]** .

   I file che AEM non è stato possibile risolvere automaticamente sono elencati in rosso nella colonna **[!UICONTROL Percorsi originali]**.

1. Esegui una o più delle seguenti operazioni:

   * **Individua e seleziona le dipendenze**. (Questa opzione presuppone che siano già stati caricati i file di dipendenza.

      1. Toccare l&#39;icona **[!UICONTROL Sfoglia file]** a sinistra del percorso rosso.
      1. Nella pagina **[!UICONTROL Seleziona contenuto]** , individua il file mancante, quindi tocca la scheda del file per selezionarlo.
      1. Nell&#39;angolo in alto a sinistra della pagina **[!UICONTROL Seleziona contenuto]**, tocca **[!UICONTROL Chiudi]** (icona X) per tornare alla pagina **[!UICONTROL Visualizza proprietà]**.
   * **Carica le dipendenze**. (Questa opzione presuppone che ancora non siano stati caricati i file mancanti.)

      1. Osserva i percorsi e i nomi dei file mancanti.
      1. Vicino all’angolo superiore destro della pagina delle proprietà, tocca **[!UICONTROL Chiudi]**.

   Dopo il caricamento dei file torna alla pagina **[!UICONTROL Visualizza proprietà > Dipendenze]** . Le risorse appena caricate sono ora correttamente elencate come risorse di riferimento.

   * **Ignora le dipendenze**.

      Se non è più necessaria una dipendenza mancante, digitare **[!UICONTROL Risorsa di riferimento]** nel campo di testo a sinistra del file mancante, in modo che AEM 3D ignori il file.`n/a`



1. Vicino all&#39;angolo superiore destro della pagina **[!UICONTROL Visualizza proprietà]**, tocca **[!UICONTROL Salva]**.
1. Tocca **[!UICONTROL Chiudi]****[!UICONTROL per tornare alla Vista a schede]**.

   La risorsa viene rielaborata automaticamente con le dipendenze appena risolte.
