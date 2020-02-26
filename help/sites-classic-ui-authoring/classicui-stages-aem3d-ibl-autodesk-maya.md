---
title: Configurazione di un’area di visualizzazione IBL con Autodesk Maya e Mental Ray
seo-title: Configurazione di un’area di visualizzazione IBL con Autodesk Maya e Mental Ray
description: Scopri come impostare un’area di visualizzazione IBL con Autodesk Maya e Mental Ray.
seo-description: Scopri come impostare un’area di visualizzazione IBL con Autodesk Maya e Mental Ray.
uuid: 99878112-74c1-4a52-a7c2-c39927ce0e2a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 00f7ed25-276b-42c2-ae4c-11de357a9ec6
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad

---


# Configurazione di un’area di visualizzazione IBL con Autodesk Maya e Mental Ray{#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. In Maya, crea una nuova scena vuota.

1. Crea un riferimento (temporaneo) a un modello rappresentativo. Questo consente di valutare la luce, impostare le videocamere e configurare il rendering.
1. Imposta l’illuminazione basata sull’immagine (IBL).

   1. Nelle impostazioni del rendering, seleziona **[!UICONTROL Render Using: mental ray]** e apri la scheda Scena.****
   1. Open the **[!UICONTROL Environment]** accordion, then click **[!UICONTROL Create Image Based Lighting]**.
   1. Fai clic sull&#39;icona della casella con una freccia destra sul lato sinistro del riquadro per selezionare il nodo IBL `mentalRayIblShape1`[!UICONTROL , quindi esci dalle impostazioni di rendering].
   1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.

   1. Set the [!UICONTROL Scale] of the node to make the environment sphere significantly larger than the largest 3D object to be shown with this stage (for example, `10000,10000,10000`).
   1. Seleziona il nodo `AdobeIblShape` e configuralo come segue:

      * **[!UICONTROL Mappatura]** : sferica
      * **[!UICONTROL Tipo]**: file dell’immagine
      * **[!UICONTROL Emissione della luce]**: vero
   1. Aggiungi l&#39;immagine TIFF da 32 bit al nodo `AdobeIbl` node.


1. Imposta il piano d’appoggio.

   * Crea un piano adatto all&#39;uso del piano d’appoggio e ridimensionalo per adattarlo alla sfera IBL passando attraverso l&#39;origine delle coordinate.
   * Allega del materiale **[!UICONTROL Use Background]** per il piano d’appoggio, rinominalo `AdobeUseBackground` e allegalo all&#39;oggetto del piano d’appoggio.

1. (Facoltativo) Crea e configura le videocamere.

   Imposta le videocamere in modo da inquadrare il centro della scena in cui verrà inserita la risorsa. Imposta le videocamere in modo che l’immagine sia renderizzabile.

1. Imposta il rendering con Mental Ray.

   Configure the [!UICONTROL Render Settings] with the following suggestions.

   * **[!UICONTROL Scheda Comune]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all Renderable Cameras.

   * **[!UICONTROL Scheda Qualità]**

      * **[!UICONTROL Qualità generale]** -`0.5` o minore
      * **[!UICONTROL Modalità]** Indirect Diffuse (GI) - `Final Gather`
      * **[!UICONTROL Dimensioni]** filtro - `2.0`, `2.0`
   * Effettua il rendering della scena con le dimensioni immagine che prevedi di utilizzare. Se necessario, perfeziona le luci, le impostazioni di rendering o entrambe per ottenere il risultato desiderato.

       Tieni presente che il rendering con Mental Ray, utilizzando l’illuminazione basata sull’immagine, è molto lento e fa un uso intensivo della CPU. Adobe consiglia di configurare le impostazioni per qualità inferiore, che forniscono comunque una qualità di rendering accettabile.


1. Elimina il riferimento creato al passaggio 2.

1. Salva la scena, quindi esci da Autodesk Maya.

1. Carica la scena e IBL PTIFF su AEM e aspetta che il caricamento sia completato.

   Consulta [Caricamento delle risorse](/help/assets/managing-assets-touch-ui.md#uploading-assets).

1. Risolvi tutte le dipendenze del file.

   Consulta [Risoluzione delle dipendenze dei file](/help/sites-classic-ui-authoring/classicui-upload-proc-3d-resolve-dependencies.md).

   AEM 3D potrebbe non essere in grado di individuare l&#39;immagine IBL configurata in questa area di visualizzazione. Se così fosse, devi risolvere manualmente le dipendenze mancanti. Puoi assegnare la stessa immagine IBL PTIFF precedentemente caricata a ciascuna delle dipendenze mancanti. In alternativa, puoi assegnare immagini diverse per controllare ulteriormente gli effetti IBL. Dopo la risoluzione delle dipendenze, fare clic su **Salva** per avviare la rielaborazione.

1. Apri Proprietà risorsa in AEM. Imposta il titolo su una stringa adatta che apparirà nell&#39;elenco a discesa del selettore delle aree di visualizzazione. Verifica che **[!UICONTROL Class]** (Classe) sia impostato su **[!UICONTROL 3D Stage]** (Area di visualizzazione 3D). Salva e chiudi.

1. Apri una risorsa 3D, seleziona la nuova area di visualizzazione e verifica che anteprima e rendering siano come previsto.

