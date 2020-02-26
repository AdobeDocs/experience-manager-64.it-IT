---
title: Configurazione di un’area di visualizzazione standard con Autodesk Maya e Mental Ray
seo-title: Configurazione di un’area di visualizzazione standard con Autodesk Maya e Mental Ray
description: Scopri come configurare un livello standard con Autodesk Maya e Mental Ray.
seo-description: Scopri come configurare un livello standard con Autodesk Maya e Mental Ray.
uuid: 05c4858b-6261-4de3-a87a-03dd6bc519a4
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f30c4039-3bbf-4d02-a9b5-bda6ccce16b9
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad

---


# Configurazione di un’area di visualizzazione standard con Autodesk Maya e Mental Ray{#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}

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

   Configure the **[!UICONTROL Render Settings]** with the following suggestions:

   * **[!UICONTROL Scheda Comune]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all [!UICONTROL Renderable Cameras].

   * **[!UICONTROL Scheda Qualità]**

      * **[!UICONTROL Qualità]** globale `- 0.5` o inferiore
      * **[!UICONTROL Modalità]** Indirect Diffuse (GI) - `Final Gather`
      * **[!UICONTROL Dimensioni]** filtro - `2.0`, `2.0`
   * Effettua il rendering della scena con le dimensioni immagine che prevedi di utilizzare. If necessary, refine the lights, or [!UICONTROL Render settings], or do both to achieve the results you want.

       Tieni presente che il rendering con Mental Ray, utilizzando l’illuminazione basata sull’immagine, è molto lento e fa un uso intensivo della CPU. Adobe consiglia di configurare le impostazioni per qualità inferiore, che forniscono comunque una qualità di rendering accettabile.


1. Elimina il riferimento creato al passaggio 2.
1. Salva la scena, quindi esci da Autodesk Maya.
1. Carica la scena in AEM e attendi il completamento del caricamento.

   Consulta [Caricamento delle risorse](/help/assets/managing-assets-touch-ui.md#uploading-assets).

   Se Autodesk® Maya® non è configurato sul server AEM, esporta un file FBX da Maya e caricalo in AEM.

1. Apri Proprietà risorsa in AEM. Imposta il titolo su una stringa adatta che apparirà nell&#39;elenco a discesa del selettore delle aree di visualizzazione. Verifica che **[!UICONTROL Class]** (Classe) sia impostato su **[!UICONTROL 3D Stage]** (Area di visualizzazione 3D). Salva e chiudi.
1. Apri una risorsa 3D, seleziona la nuova area di visualizzazione e verifica che anteprima e rendering siano come previsto.

