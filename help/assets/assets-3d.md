---
title: Utilizzo di AEM risorse 3D
description: Scopri come lavorare con le risorse 3D in AEM 3D
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
exl-id: 3cee9b4f-c4be-4ffc-970c-5680c8ebba47
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 5%

---

# Utilizzo AEM risorse 3D {#working-with-d-assets}

>[!IMPORTANT]
>
>AEM 3D in AEM 6.4 non è più supportato. Adobe consiglia di utilizzare la funzione risorse 3D in [AEM come Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) o [AEM 6.5.3 o superiore.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic)

AEM 3D (Adobe Experience Manager 3D) consente di caricare, gestire, visualizzare ed effettuare il rendering di contenuti 3D. Il supporto per la visualizzazione e il rendering è ottimizzato per i singoli contenuti.

Consulta anche [Note sulla versione di AEM 3D](/help/release-notes/aem3d-release-notes.md).

Consulta anche [Installazione e configurazione di AEM 3D](install-config-3d.md).

## Informazioni su modelli e stadi AEM 3D {#about-models-and-stages-in-aem-d}

AEM 3D consente di visualizzare ed eseguire il rendering di modelli 3D statici e autonomi di alta qualità in ambienti predefiniti denominati Stages. In sostanza, un’area di visualizzazione fornisce &quot;illuminazione&quot; per la scena 3D e le impostazioni per il rendering in un’applicazione nativa come Autodesk® Maya® o Autodesk 3ds Max®. Inoltre, l&#39;area di visualizzazione può includere videocamere predefinite, sfondi e geometria del piano terreno.

I file 3D caricati che contengono luci sono considerati un&#39;area di visualizzazione. Puoi ripristinare tali risorse come semplici oggetti 3D aprendo la risorsa nella pagina dei dettagli della risorsa. Tocca **[!UICONTROL Visualizza proprietà]**, quindi tocca la scheda **[!UICONTROL Base]** . Dall’elenco a discesa Classe risorsa, sotto l’intestazione Metadati , seleziona **[!UICONTROL Oggetto 3D]**.

Quando crei modelli 3D da utilizzare in AEM 3D, tieni presente quanto segue:

* I file del modello 3D devono contenere un solo oggetto, senza sfondi, piani terra, illuminazione della scena o videocamere.
* Posizionare il modello sopra il piano di massa. Questo posizionamento è particolarmente importante quando si visualizzano o si eseguono il rendering con fasi che forniscono un piano di terra. È disponibile un’impostazione di configurazione (e attivata per impostazione predefinita) che consente di spostare l’oggetto al di sopra del piano terreno durante l’anteprima o il rendering con Rapid Refine. Questa impostazione non influisce sul rendering con moduli di rendering di terze parti (ad esempio, tramite Maya), pertanto gli oggetti che non si trovano sopra il piano terreno potrebbero essere parzialmente nascosti.
* Posizionare il modello in modo che sia ragionevolmente centrato lateralmente intorno all&#39;origine del sistema di coordinate (0,0,0). In questo modo si garantisce una buona esperienza di visualizzazione interattiva.
* Oltre alle mappe di texture, sono supportati i riferimenti di file esterni. Pertanto, è necessario incorporare qualsiasi contenuto di riferimento nel file del modello principale prima di caricarlo in AEM.

   Vedi [Caricamento ed elaborazione di risorse 3D in AEM](upload-processing-3d-assets.md).

* L&#39;illuminazione generale della scena è fornita dal palco. Di conseguenza, Adobe sconsiglia di includere luci con file di modello 3D. Potete includere le luci nel modello. Tuttavia, devono essere specifici solo per il modello. Ad esempio, potrebbe essere necessario includere un&#39;illuminazione aggiuntiva per illuminare una parte dell&#39;oggetto oscurata da altre parti. Pertanto, non sarebbe sufficientemente visibile solo con le luci di scena.

## File supportati in AEM 3D {#supported-files-in-aem-d}

Una tipica risorsa 3D ha un file di modello principale e nessuno o più file di riferimento. I file di riferimento includono elementi come mappe della texture o immagini **IBL (Image-Based Lighting)**.

### Informazioni sul file del modello 3D primario {#about-the-primary-d-model-file}

Il file del modello 3D primario contiene la geometria del modello 3D e le definizioni per i materiali (predefiniti) applicati alle superfici del modello. AEM 3D supporta i seguenti formati di file modello 3D primari:

* Formato del file OBJ Wavefront (`.obj`)

   Il formato OBJ richiede uno o più file MTL esterni separati (Libreria dei modelli di materiale) (`.mtl`).

* Formato di file Autodesk FBX (Filmbox) (`.fbx`)

   Il formato di scambio file 3D di Autodesk; formati sia binari che ASCII.

   Quando crei file FBX in applicazioni di terze parti, Adobe consiglia le seguenti impostazioni di configurazione (vedi tabella seguente). Queste impostazioni possono aiutarti a ottenere i migliori risultati per i file 3D che intendi utilizzare in AEM. I nomi delle opzioni sono ricavati dalla finestra di dialogo **[!UICONTROL Opzioni di esportazione Autodesk Maya FBX]**.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opzione nella finestra di dialogo Esportazione Autodesk Maya FBX</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>Mantieni riferimenti<br /> </td> 
   <td><p>Deseleziona.</p> <p>AEM 3D attualmente non supporta riferimenti esterni.</p> </td> 
  </tr> 
  <tr> 
   <td>Maglia<br /> </td> 
   <td>Seleziona.</td> 
  </tr> 
  <tr> 
   <td>Converti superfici NURBS in</td> 
   <td><strong>Rete di rendering software</strong></td> 
  </tr> 
  <tr> 
   <td>Animazione</td> 
   <td><p>Seleziona o deseleziona.</p> <p>Se scegli di selezionare questa opzione, AEM 3D ignora le informazioni di animazione nel file.</p> </td> 
  </tr> 
  <tr> 
   <td>Videocamere</td> 
   <td><p>Selezionare per <strong>stadi 3D</strong>.</p> <p>Deselezionare per i modelli 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Luci</td> 
   <td><p>Selezionare per <strong>stadi 3D</strong>.</p> <p>Deseleziona per <strong>modelli 3D</strong>.</p> </td> 
  </tr> 
  <tr> 
   <td>Unità - Automatico</td> 
   <td>Seleziona. AEM 3D si converte all'importazione.</td> 
  </tr> 
  <tr> 
   <td>Conversione asse - Asse su</td> 
   <td><p><strong>Y</strong></p> <p>Y-up fornisce risultati coerenti quando si esporta da Maya ed è il sistema di coordinate preferito per i file FBX in questa versione AEM 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Incorpora file multimediali</td> 
   <td>Sono supportate entrambe le opzioni. Se è selezionata l'opzione Incorpora, AEM 3D estrae il supporto incorporato in una cartella adiacente che ha lo stesso nome del file modello a cui è stato aggiunto <code>.fbm</code>.</td> 
  </tr> 
  <tr> 
   <td>Formato file FBX - Tipo</td> 
   <td>Sono supportati sia <strong>Binary </strong>che <strong>ASCII </strong>.</td> 
  </tr> 
  <tr> 
   <td>Formato file FBX - Versione</td> 
   <td>Si consiglia FBX 2014/2015. Anche altre versioni possono funzionare bene.</td> 
  </tr> 
 </tbody> 
</table>

Sono supportati i seguenti formati di file aggiuntivi se Autodesk Maya è installato e configurato su AEM server di authoring:

* Autodesk Maya

   I formati ASCII `.ma` e binario `.mb`.

* `Jupiter Tesselation (ISO 14306-1).jt`.

   Un formato standard di settore per lo scambio di dati CAD, la collaborazione e la visualizzazione dei prodotti.

### Supporto per i file mappa texture {#support-for-texture-map-files}

Le definizioni dei materiali nei file di modello 3D possono includere riferimenti a file di immagine esterni che forniscono mappe di texture. AEM 3D supporta i seguenti tipi di file mappa texture:

* Trame di colore diffuse
* Trame a colori speciali
* Trame di colore ambiente
* App di spostamento (dette anche mappe di rilievo)
* Mappe normali
* Mappe di opacità
* Mappe di rugosità (dette anche mappe di Gloss, Reflectivity o Cosine Power)

I materiali nel file del modello 3D primario possono fare riferimento ad altri tipi di mappe ignorate da AEM 3D.

### Immagini IBL (Image Based Lighting) {#ibl-image-based-lighting-images}

Un file di modello 3D che definisce un’area di visualizzazione può fare riferimento a una singola immagine di ambiente IBL. Attualmente, AEM 3D supporta solo immagini TIFF a 32 bit in formato latitudine/longitudine per IBL diffusa e per riflessi. Per lo sfondo sferico della scena, sono supportate anche le immagini RGB a 8 bit.

Vedere [Informazioni sull&#39;utilizzo delle aree di visualizzazione IBL](working-with-ibl-stages.md).

>[!NOTE]
>
>I riferimenti ai file, diversi da quelli descritti in precedenza, presenti nel file del modello 3D primario vengono attualmente ignorati. AEM 3D non supporta i riferimenti a file di modelli 3D secondari.
Y-up è il sistema di coordinate preferito per i file FBX in questa versione.

## Ombreggiatura del materiale in un file di modello 3D primario {#material-shading-in-a-primary-d-model-file}

Il file del modello nativo originale può contenere definizioni di materiale utilizzate con shader come Blinn, Lambert o con shader procedurali. Questi materiali potenzialmente complessi sono supportati solo quando esegui il rendering utilizzando l’applicazione nativa corrispondente (come Autodesk Maya).

Per scopi di visualizzazione o quando esegui il rendering utilizzando il modulo di rendering Rapid Refine™ predefinito, tutti i materiali sono semplificati, sostituiti o entrambi in modo che possano essere utilizzati con uno shader simile a Phong. Questo shader supporta un set limitato di attributi. Altri attributi nella definizione del materiale vengono ignorati.

Vedi [Visualizzazione delle risorse 3D](viewing-3d-assets.md).

Vedi [Rendering delle risorse 3D](rendering-3d-assets.md).

## Denominazione dei materiali in un file di modello 3D primario {#naming-materials-in-a-primary-d-model-file}

Una *superficie* è definita come l&#39;area di superficie di un modello 3D coperta dallo stesso materiale. Questo materiale fornisce anche il nome della superficie. Di conseguenza, Adobe consiglia di denominare di conseguenza i materiali inclusi nei file del modello 3D primario. Ad esempio, l&#39;uso di nomi specifici come &quot;Corpo&quot;, &quot;Finestre&quot;, &quot;Pneumatici&quot; o &quot;Rims&quot; è preferito all&#39;uso di nomi vaghi come &quot;Rosso&quot;, &quot;Vetro&quot;, &quot;Gomma&quot;, &quot;Alluminio&quot;.
