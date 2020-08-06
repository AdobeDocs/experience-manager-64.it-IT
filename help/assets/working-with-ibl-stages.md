---
title: Utilizzo delle aree di visualizzazione IBL
seo-title: Utilizzo delle aree di visualizzazione IBL
description: AEM 3D supporta l’illuminazione basata su immagini (IBL) sia per la visualizzazione interattiva che per il rendering con il modulo di rendering integrato Adobe Rapid Refine™ e con moduli di terze parti.
seo-description: AEM 3D supporta l’illuminazione basata su immagini (IBL) sia per la visualizzazione interattiva che per il rendering con il modulo di rendering integrato Adobe Rapid Refine™ e con moduli di terze parti.
uuid: 495ba9cc-02f5-4ce5-9503-9f61ca5482db
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 658ff671-16b9-41bd-ba24-b77a32b3346b
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 56%

---


# Utilizzo delle aree di visualizzazione IBL {#about-working-with-ibl-stages}

AEM 3D supporta l’illuminazione basata su immagini (IBL) sia per la visualizzazione interattiva che per il rendering con il modulo di rendering integrato Adobe Rapid Refine™ e con moduli di terze parti. È possibile creare aree di visualizzazione IBL con strumenti di authoring comuni come Autodesk® Maya® o Autodesk® 3ds Max®.

## Immagini per IBL {#images-for-ibl}

Per risultati ottimali, le immagini utilizzate per l’illuminazione basata sulle immagini dovrebbero essere in formato HDR (High Dynamic Range). Devono essere in formato lat/long con mappatura sferica con una copertura completa dell’ambiente.

Attualmente, AEM 3D supporta soltanto i TIFF a 32 bit. Se necessario, utilizza Adobe Photoshop o altro strumento simile per convertire in TIFF l’immagine HDR, utilizzando le seguenti impostazioni nella finestra di dialogo Esporta TIFF di Adobe Photoshop:

* **[!UICONTROL Profondità]** bit - 32 bit (mobile)
* **[!UICONTROL Ordine]** pixel - Interleaved (RGBRGB)
* **[!UICONTROL Compressione]** immagine - LZW
* **[!UICONTROL ordine** byte - PC IBM

Mentre una singola immagine HDR è spesso sufficiente per le aree di visualizzazione IBL, AEM 3D fornisce un controllo aggiuntivo sugli effetti IBL che consente fino a tre immagini distinte:

* **Immagine** ambiente di illuminazione diffusa - Questo tipo di immagine deve essere un&#39;immagine HDR, ma può essere relativamente piccola, in quanto l&#39;immagine verrà filtrata pesantemente prima di essere utilizzata per l&#39;illuminazione diffusa.
* **Immagine** ambiente di riflessione - Questo tipo di immagine viene usato per creare riflessi nelle superfici degli oggetti. Può essere un’immagine RGB standard a 8 bit, di dimensioni e risoluzione tali da fornire la qualità e la nitidezza desiderate per i riflessi. Se viene specificata un’immagine HDR, AEM 3D la converte in RGB a 8 bit prima di utilizzare un algoritmo proprietario.
* **Immagine** ambiente di sfondo - Questo tipo di immagine viene usato come sfondo. Può essere un’immagine RGB standard a 8 bit e dovrebbe avere dimensioni, risoluzione e livello di dettagli appropriati per lo sfondo dell’area di visualizzazione. Se viene specificata un’immagine HDR, AEM 3D la converte in RGB a 8 bit utilizzando un algoritmo proprietario. ``

>[!NOTE]
>
>L’algoritmo di conversione potrebbe avere difficoltà con alcune immagini IBL. Ne possono conseguire sfondi troppo luminosi o troppo saturi in Anteprima o durante il rendering con Rapid Refine. In tali situazioni, Adobe consiglia di utilizzare Photoshop o uno strumento simile per convertire manualmente l’immagine IBL in un’immagine RGB a 8 bit. Carica questa immagine separatamente e collegala all’area di visualizzazione come immagine ambiente per lo sfondo. Le immagini ambiente a illuminazione diffusa e per riflessi devono sempre essere TIFF a 32 bit.

## Regolazione dell’aspetto dell’area di visualizzazione IBL {#adjusting-the-ibl-stage-appearance}

È possibile ottimizzare l’aspetto dell’area di visualizzazione IBL con le seguenti proprietà:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Proprietà</strong><br /> </td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>IBL Sun Details</td> 
   <td><p>Consente di regolare la direzione e la forza della sorgente di luce supplementare che simula il sole. <span class="diff-html-added">Questa sorgente di luce aumenta la luminosità dell’illuminazione e fa sì che l’oggetto proietti un’ombra esterna sul piano terreno. La funzione di generazione ombre è supportata quando si esegue il rendering con Rapid Refine e per l’anteprima con Google Chrome; tuttavia, al momento non è supportata da altri browser.</span></p> 
    <ul> 
     <li><strong>lat</strong> - La posizione verticale della sorgente luminosa del sole (<code>0.0</code>-<code>1.0</code>).<br /> Un'impostazione di <code>0.0</code> è all'orizzonte (centro verticale dell'immagine dell'ambiente di illuminazione diffusa); <code>1.0</code> si trova nello zenith (bordo superiore dell’immagine dell’ambiente di luce diffusa).</li> 
     <li><strong>long</strong> - La posizione orizzontale della sorgente luminosa del sole (<code>0.0</code>-<code>1.0</code>).<br /> Un’impostazione pari a 0,0 corrisponde a sinistra; 1,0 corrisponde al bordo destro dell’immagine ambiente di illuminazione diffusa.<br /> </li> 
     <li><strong>luminoso</strong> - La luminosità della sorgente luminosa del sole. Aumenta questo valore per schiarire la fonte di luce solare; diminuiscilo per scurirla. <br /> Un'impostazione <code>0</code> disattiva l'illuminazione supplementare e disabilita le ombre proiettate. Il parametro non influisce sui riflessi ambientali.<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Altezza telecamera IBL</td> 
   <td>Se lo sfondo IBL appare distorto vicino all'orizzonte, è possibile ridurre o eliminare la distorsione regolando questa proprietà. <br /> </td> 
  </tr> 
  <tr> 
   <td>Illuminazione ambiente</td> 
   <td><p><span class="diff-html-added">Consente di controllare l'illuminazione diffusa. Potrebbe essere necessario regolare manualmente questa proprietà per correggere la luminosità dell’illuminazione se l’immagine ambiente di illuminazione diffusa è insolitamente chiara o scura (ad esempio, scene notturne).</span></p> 
    <ul> 
     <li><strong>r, g, b</strong> - Attualmente non utilizzato.</li> 
     <li><strong>luminoso</strong> - Moltiplicatore <span class="diff-html-added">luminosità. Aumentando o diminuendo questo valore si aumenta o diminuisce l’intensità di illuminazione complessiva (sia l’illuminazione di base IBL che la luminosità della sorgente solare).</span></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Aumento del diametro dello sfondo sferico di un passaggio IBL {#increasing-the-spherical-background-diameter-of-an-ibl-stage}

Le fasi IBL utilizzano immagini di sfondo sferiche con un diametro di 20 metri per impostazione predefinita. Tali fasi funzionano bene per oggetti fino a 10 metri. Tuttavia, se visualizzate oggetti più grandi, potete aumentare il diametro di sfondo sferico di un’area IBL.

**Per aumentare il diametro dello sfondo sferico di uno stadio** IBL:

1. In CRXDE Lite, andate all’area di visualizzazione di cui desiderate aumentare il diametro di sfondo sferico. Ad esempio,

   `/content/dam/test3d/stage-helipad.fbx`

1. Espandi il nodo dell’area di visualizzazione in `jcr:content/metadata`.
1. Impostare la proprietà `dam:gPlaneRadius` sul valore millimetrico desiderato.

   Per l’efficienza del rendering,  Adobe consiglia di limitare questo valore a circa la dimensione più grande dell’oggetto più grande che si intende visualizzare nell’area di visualizzazione.

   Ad esempio, un modello di piano a getto lungo 20 metri viene visualizzato bene se `dam:gPlaneRadius=20000`.

1. Nell’angolo in alto a sinistra della pagina del CRXDE Lite, toccate **[!UICONTROL Salva tutto]**.

