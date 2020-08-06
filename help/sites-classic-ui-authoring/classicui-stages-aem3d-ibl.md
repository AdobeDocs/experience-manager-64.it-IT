---
title: Utilizzo delle aree di visualizzazione IBL
seo-title: Utilizzo delle aree di visualizzazione IBL
description: AEM 3D supporta l’illuminazione basata su immagini (IBL) sia per la visualizzazione interattiva che per il rendering con il modulo di rendering integrato Adobe Rapid Refine e con moduli di terze parti. È possibile creare aree di visualizzazione IBL con strumenti di authoring comuni come Autodesk Maya o Autodesk 3ds Max.
seo-description: AEM 3D supporta l’illuminazione basata su immagini (IBL) sia per la visualizzazione interattiva che per il rendering con il modulo di rendering integrato Adobe Rapid Refine e con moduli di terze parti. È possibile creare aree di visualizzazione IBL con strumenti di authoring comuni come Autodesk Maya o Autodesk 3ds Max.
uuid: 6598fb8a-65b0-4b84-8063-fdc94f6ea935
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: f9291151-851a-4aff-a50e-a24330ee0c13
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 77%

---


# Utilizzo delle aree di visualizzazione IBL{#about-working-with-ibl-stages}

AEM 3D supporta l’illuminazione basata su immagini (IBL) sia per la visualizzazione interattiva che per il rendering con il modulo di rendering integrato Adobe Rapid Refine™ e con moduli di terze parti. È possibile creare aree di visualizzazione IBL con strumenti di authoring comuni come Autodesk® Maya® o Autodesk® 3ds Max®.

## Immagini per IBL {#images-for-ibl}

Per risultati ottimali, le immagini utilizzate per l’illuminazione basata sulle immagini dovrebbero essere in formato HDR (High Dynamic Range). Devono essere in formato lat/long con mappatura sferica con una copertura completa dell’ambiente.

Attualmente, AEM 3D supporta soltanto i TIFF a 32 bit. Se necessario, utilizza Adobe Photoshop o altro strumento simile per convertire in TIFF l’immagine HDR, utilizzando le seguenti impostazioni nella finestra di dialogo Esporta TIFF di Adobe Photoshop:

* **[!UICONTROL Profondità]** bit - 32 bit (mobile)
* **[!UICONTROL Ordine]** pixel - Interleaved (RGBRGB)
* **[!UICONTROL Compressione]** immagine - LZW
* **[!UICONTROL Ordine]** byte - PC IBM

Mentre una singola immagine HDR è spesso sufficiente per le aree di visualizzazione IBL, AEM 3D fornisce un controllo aggiuntivo sugli effetti IBL che consente fino a tre immagini distinte:

* **[!UICONTROL Immagine ambiente a illuminazione diffusa:]** questo tipo di immagine dovrebbe essere un’immagine HDR, ma può essere relativamente piccola, in quanto sarà pesantemente filtrata prima di essere utilizzata per l’illuminazione diffusa.
* **[!UICONTROL Immagine ambiente per riflessi:]** questo tipo di immagine viene utilizzato per creare riflessi nelle superfici dell’oggetto. Può essere un’immagine RGB standard a 8 bit, di dimensioni e risoluzione tali da fornire la qualità e la nitidezza desiderate per i riflessi. Se viene specificata un’immagine HDR, AEM 3D la converte in RGB a 8 bit prima di utilizzare un algoritmo proprietario.
* **[!UICONTROL Immagine ambiente di sfondo:]** questo tipo di immagine viene utilizzata come sfondo. Può essere un’immagine RGB standard a 8 bit e dovrebbe avere dimensioni, risoluzione e livello di dettagli appropriati per lo sfondo dell’area di visualizzazione. Se viene specificata un’immagine HDR, AEM 3D la converte in RGB a 8 bit utilizzando un algoritmo proprietario.

>[!NOTE]
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

