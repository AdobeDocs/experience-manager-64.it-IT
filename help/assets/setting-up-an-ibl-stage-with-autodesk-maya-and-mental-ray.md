---
title: Configurazione di un’area di visualizzazione IBL con Autodesk Maya e Mental Ray
seo-title: Configurazione di un’area di visualizzazione IBL con Autodesk Maya e Mental Ray
description: Come impostare una fase IBL con Autodesk Maya e Mental Ray
seo-description: Come impostare una fase IBL con Autodesk Maya e Mental Ray
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 75%

---


# Configurazione di un’area di visualizzazione IBL con Autodesk Maya e Mental Ray {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. In Maya, crea una nuova scena vuota.

1. Crea un riferimento (temporaneo) a un modello rappresentativo. Questo consente di valutare la luce, impostare le videocamere e configurare il rendering.
1. Imposta l’illuminazione basata sull’immagine (IBL).

   1. In **[!UICONTROL Render Settings]**, select **[!UICONTROL Render Render Using: mental ray]**, and open the Scene tab.
   1. Open the **[!UICONTROL Render Environment]** accordion and click **[!UICONTROL Render Create Image Based Lighting**.
   1. Click the box icon that has a right arrow on the left side of the box to select the IBL node `mentalRayIblShape1`, then exit **[!UICONTROL Render Settings]**.
   1. In the **[!UICONTROL Attribute Editor]**, select the transform node `mentalRayIbl1`, then rename the transform node to `AdobeIbl`.
   1. Imposta la scala del nodo per aumentare significativamente l&#39;ambiente rispetto all’oggetto in 3D più grande per poterlo visualizzare (ad esempio, `10000,10000,10000`).
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

   Configure the **[!UICONTROL Render Settings]** with the following suggestions.

   * **[!UICONTROL Scheda Comune]**

      Deselect the **[!UICONTROL Alpha channel (mask)]** check box for all **[!UICONTROL Renderable Cameras]**.

   * **[!UICONTROL Scheda Qualità]**

      * **Qualità generale** -`0.5` o minore
      * **Modalità** Indirect Diffuse (GI) - `Final Gather`
      * ``**Filter Size** - `2.0`, `2.0`
   * Effettua il rendering della scena con le dimensioni immagine che prevedi di utilizzare. Se necessario, perfeziona le luci, le impostazioni di rendering o entrambe per ottenere il risultato desiderato.

       Tieni presente che il rendering con Mental Ray, utilizzando l’illuminazione basata sull’immagine, è molto lento e fa un uso intensivo della CPU. Adobe consiglia di configurare le impostazioni per qualità inferiore, che forniscono comunque una qualità di rendering accettabile.


1. Elimina il riferimento creato al passaggio 2.

1. Salva la scena, quindi esci da Autodesk Maya.

1. Carica la scena e IBL PTIFF su AEM e aspetta che il caricamento sia completato.

   Consulta [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets).

1. Risolvi tutte le dipendenze del file.

   Consulta [Risoluzione delle dipendenze dei file](resolve-file-dependencies.md).

   AEM 3D potrebbe non essere in grado di individuare l&#39;immagine IBL configurata in questa area di visualizzazione. Se così fosse, devi risolvere manualmente le dipendenze mancanti. Puoi assegnare la stessa immagine IBL PTIFF precedentemente caricata a ciascuna delle dipendenze mancanti. In alternativa, puoi assegnare immagini diverse per controllare ulteriormente gli effetti IBL. Dopo la risoluzione delle dipendenze, fare clic su **[!UICONTROL Salva]** per avviare la rielaborazione.

1. Apri Proprietà risorsa in AEM. Set **[!UICONTROL Title]** to a suitable string that will appear in the **[!UICONTROL Stage Selector]** drop-down list. Verifica che **[!UICONTROL Class]** (Classe) sia impostato su **[!UICONTROL 3D Stage]** (Area di visualizzazione 3D). Salva e chiudi.

1. Apri una risorsa 3D, seleziona la nuova area di visualizzazione e verifica che anteprima e rendering siano come previsto.

