---
title: Configurazione di un’area di visualizzazione standard con Autodesk Maya e Mental Ray
seo-title: Configurazione di un’area di visualizzazione standard con Autodesk Maya e Mental Ray
description: Come impostare uno stadio standard con Autodesk Maya e Mental Ray
seo-description: Come impostare uno stadio standard con Autodesk Maya e Mental Ray
uuid: 3895fda6-29ae-46f5-b2bc-abc989808648
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: da8fc33b-84ae-4ead-87bb-5a7870a38b1f
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 85%

---


# Configurazione di un’area di visualizzazione standard con Autodesk Maya e Mental Ray {#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

1. In Maya, crea una nuova scena vuota.
1. Crea un riferimento (temporaneo) a un modello rappresentativo. Questo consente di valutare la luce, impostare le videocamere e configurare il rendering.

1. Aggiungi luci come di consueto. Attualmente, AEM 3D supporta i seguenti tipi di luce:

   * Luci direzionali
   * Faretti
   * Luci puntiformi

   Altri tipi di luce vengono ignorati o convertiti in uno dei tipi supportati sopra quando l’area di visualizzazione viene caricata in AEM 3D. I tipi convertiti vengono utilizzati quando visualizzi la risorsa e quando esegui il rendering utilizzando il modulo di rendering Rapid Refine integrato. I tipi di luce originali vengono utilizzati durante il rendering con Maya.

1. Se necessario, crea un piano base e applica un materiale adatto.

   Adobe consiglia di impostare un piano base su un solo lato. In questo modo puoi visualizzare la risorsa dal basso in AEM 3D senza che il piano base nasconda la risorsa.

1. (Facoltativo) Crea e configura le videocamere.

   Imposta le videocamere in modo da inquadrare il centro della scena in cui verrà inserita la risorsa. Imposta le videocamere in modo che l’immagine sia renderizzabile.

1. Imposta il rendering con Mental Ray.

   Configura le impostazioni di rendering con i seguenti suggerimenti:

   * **[!UICONTROL Scheda Comune]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all Renderable Cameras.

   * **[!UICONTROL Scheda Qualità]**

      * **[!UICONTROL Qualità]** globale `- 0.5` o inferiore
      * **[!UICONTROL Modalità]** Indirect Diffuse (GI) - `Final Gather`
      * **[!UICONTROL Dimensioni]** filtro - `2.0`, `2.0`
   * Effettua il rendering della scena con le dimensioni immagine che prevedi di utilizzare. Se necessario, perfeziona le luci o le impostazioni di rendering, o entrambi, fino a ottenere il risultato desiderato.

       Tieni presente che il rendering con Mental Ray, utilizzando l’illuminazione basata sull’immagine, è molto lento e fa un uso intensivo della CPU. Adobe consiglia di configurare le impostazioni per qualità inferiore, che forniscono comunque una qualità di rendering accettabile.


1. Elimina il riferimento creato al passaggio 2.

1. Salva la scena, quindi esci da Autodesk Maya.
1. Carica la scena in AEM e attendi il completamento del caricamento.

   Consulta [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets).

   Se Autodesk® Maya® non è configurato sul server AEM, esporta un file FBX da Maya e caricalo in AEM.

1. Apri Proprietà risorsa in AEM. Set **[!UICONTROL Title]** to a suitable string that will appear in the **[!UICONTROL Stage Selector]** drop-down list. Verifica che **[!UICONTROL Class]** (Classe) sia impostato su **[!UICONTROL 3D Stage]** (Area di visualizzazione 3D). Salva e chiudi.
1. Apri una risorsa 3D, seleziona la nuova area di visualizzazione e verifica che anteprima e rendering siano come previsto.

