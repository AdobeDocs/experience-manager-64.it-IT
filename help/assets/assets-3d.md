---
title: Utilizzo di risorse 3D
seo-title: Utilizzo di risorse 3D
description: Scopri come lavorare con risorse 3D in AEM 3D
seo-description: Scopri come lavorare con risorse 3D in AEM 3D
uuid: a1c1bb29-9d3d-4025-8142-ed9719434bf9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: 32143da1-09c8-45ce-b50d-32adf6efe383
translation-type: tm+mt
source-git-commit: 7c850ed0d20dd2ba2626242c67ba190e371f049f
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 6%

---


# Utilizzo delle risorse 3D {#working-with-d-assets}

AEM 3D (Adobe Experience Manager 3D) consente di caricare, gestire, visualizzare ed effettuare il rendering di contenuti 3D. Il supporto per la visualizzazione e il rendering è ottimizzato per i singoli contenuti.

Consulta anche [Note sulla versione di AEM 3D](/help/release-notes/aem3d-release-notes.md).

Consulta anche [Installazione e configurazione di AEM 3D](install-config-3d.md).

## Modelli e stadi di AEM 3D {#about-models-and-stages-in-aem-d}

AEM 3D consente di visualizzare ed eseguire il rendering di modelli 3D statici e autonomi di alta qualità in ambienti predefiniti denominati Stages. In sostanza, uno stage fornisce &quot;illuminazione&quot; per la scena 3D e le impostazioni per il rendering in un&#39;applicazione nativa come Autodesk® Maya® o Autodesk 3ds Max®. Inoltre, l&#39;area di visualizzazione può includere, facoltativamente, telecamere, sfondi e geometria del piano di messa a terra già definiti.

I file 3D caricati che contengono luci vengono considerati come un passaggio. Potete ripristinare tali risorse come semplici oggetti 3D aprendo la risorsa nella pagina dei dettagli della risorsa. Toccate **[!UICONTROL Visualizza proprietà]**, quindi toccate la scheda **[!UICONTROL Base]** . Nell’intestazione Metadati, dall’elenco a discesa Classe risorsa, selezionate Oggetto **** 3D.

Quando create modelli 3D da usare in AEM 3D, tenete presente quanto segue:

* I file modello 3D devono contenere un solo oggetto, senza sfondi, piani terra, illuminazione della scena o videocamere.
* Posizionare il modello sopra il piano terra. Questo posizionamento è particolarmente importante quando si visualizzano o si eseguono il rendering con fasi che forniscono un piano terreno. È disponibile un&#39;impostazione di configurazione (e attivata per impostazione predefinita) che causa lo spostamento dell&#39;oggetto sopra il piano terra durante l&#39;anteprima o il rendering con Rapida perfeziona. Questa impostazione non influisce sul rendering con renderer di terze parti (ad esempio tramite Maya), pertanto gli oggetti che non si trovano sopra il piano terreno potrebbero essere parzialmente nascosti.
* Posizionare il modello in modo che sia ragionevolmente centrato lateralmente attorno all&#39;origine del sistema di coordinate (0,0,0). In questo modo si garantisce una buona esperienza di visualizzazione interattiva.
* Oltre alle mappe di texture, sono supportati i riferimenti ai file esterni. Pertanto, è necessario incorporare qualsiasi contenuto di riferimento nel file del modello principale prima di caricarlo in AEM.

   Vedi [Caricamento ed elaborazione di risorse 3D in AEM](upload-processing-3d-assets.md).

* L&#39;illuminazione generale della scena è fornita dal palco. Di conseguenza,  Adobe non consiglia di includere luci con file di modelli 3D. È possibile includere le luci nel modello. Tuttavia, devono essere specifiche solo per il modello. Ad esempio, potrebbe essere necessario includere un&#39;illuminazione aggiuntiva per illuminare una parte dell&#39;oggetto oscurata da altre parti. Pertanto, non sarebbe sufficientemente visibile solo con le luci di scena.

## File supportati in AEM 3D {#supported-files-in-aem-d}

Una tipica risorsa 3D ha un file modello principale e nessuno o più file di riferimento. I file di riferimento includono ad esempio mappe di texture o immagini **IBL (Image-Based Lighting)** .

### Informazioni sul file modello 3D principale {#about-the-primary-d-model-file}

Il file principale del modello 3D contiene la geometria effettiva del modello 3D e le definizioni per i materiali (predefiniti) applicati alle superfici del modello. AEM 3D supporta i seguenti formati di file modello 3D principali:

* Formato di file OBJ Wavefront (`.obj`)

   Il formato OBJ richiede uno o più file MTL esterni separati (Libreria modelli materiali) (`.mtl`).

* Formato file Autodesk FBX (Filmbox) (`.fbx`)

   Il formato di interscambio file 3D di Autodesk; formati binario e ASCII.

   Quando create file FBX in applicazioni di terze parti,  Adobe consiglia le seguenti impostazioni di configurazione (vedere la tabella seguente). Queste impostazioni consentono di ottenere i risultati migliori per i file 3D che si intende utilizzare in AEM. I nomi delle opzioni sono ricavati dalla finestra di dialogo Opzioni **[!UICONTROL di esportazione]** Autodesk Maya FBX.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opzione nella finestra di dialogo di esportazione Autodesk Maya FBX</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>Mantieni riferimenti<br /> </td> 
   <td><p>Deseleziona.</p> <p>AEM 3D al momento non supporta riferimenti esterni.</p> </td> 
  </tr> 
  <tr> 
   <td>Trama uniforme<br /> </td> 
   <td>Seleziona.</td> 
  </tr> 
  <tr> 
   <td>Converti superfici NURBS in</td> 
   <td><strong>Rete di rendering software</strong></td> 
  </tr> 
  <tr> 
   <td>Animazione</td> 
   <td><p>Selezionate o deselezionate.</p> <p>Se scegliete di selezionare questa opzione, AEM 3D ignora le informazioni di animazione presenti nel file.</p> </td> 
  </tr> 
  <tr> 
   <td>Telecamere</td> 
   <td><p>Selezionare per le fasi <strong></strong>3D.</p> <p>Deselezionate questa opzione per i modelli 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Luci</td> 
   <td><p>Selezionare per le fasi <strong></strong>3D.</p> <p>Deselezionate questa opzione per i modelli <strong></strong>3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Unità - Automatico</td> 
   <td>Seleziona. AEM 3D viene convertito al momento dell'importazione.</td> 
  </tr> 
  <tr> 
   <td>Conversione asse - Asse Su</td> 
   <td><p><strong>Y-up</strong></p> <p>Y-up dà risultati coerenti quando si esporta da Maya ed è il sistema di coordinate preferito per i file FBX in questa release AEM 3D.</p> </td> 
  </tr> 
  <tr> 
   <td>Incorpora file multimediali</td> 
   <td>Sono supportate entrambe le opzioni. Se è selezionata l'opzione Incorpora, AEM 3D estrae il supporto incorporato in una cartella adiacente con lo stesso nome del file modello al quale è <code>.fbm</code> aggiunto.</td> 
  </tr> 
  <tr> 
   <td>Formato file FBX - Tipo</td> 
   <td>Sono <strong>supportati sia </strong>Binary che <strong>ASCII </strong>.</td> 
  </tr> 
  <tr> 
   <td>Formato file FBX - Versione</td> 
   <td>Si consiglia l'FBX 2014/2015. Anche altre versioni possono funzionare bene.</td> 
  </tr> 
 </tbody> 
</table>

I seguenti formati di file aggiuntivi sono supportati se Autodesk Maya è installato e configurato AEM server di authoring:

* Autodesk Maya

   Entrambi i `.ma` formati ASCII `.mb` e binario.

* `Jupiter Tesselation (ISO 14306-1).jt`.

   Un formato standard di settore per lo scambio di dati CAD, la collaborazione e la visualizzazione dei prodotti.

### Supporto per i file mappa texture {#support-for-texture-map-files}

Le definizioni dei materiali nei file modello 3D possono includere riferimenti a file immagine esterni che forniscono mappe di texture. AEM 3D supporta i seguenti tipi di file mappa texture:

* Diverse texture di colore
* Trame di colore speculare
* Trame di colore ambiente
* App di spostamento (o mappe di rilievo)
* Mappe normali
* Mappe opacità
* Mappe di rugosità (dette anche mappe di potenza della luce, riflettività o coseno)

I materiali presenti nel file principale del modello 3D possono fare riferimento ad altri tipi di mappe ignorate da AEM 3D.

### Immagini IBL (Image Based Lighting) {#ibl-image-based-lighting-images}

Un file di modello 3D che definisce uno stage può fare riferimento a una singola immagine dell’ambiente IBL. Attualmente, AEM 3D supporta solo immagini TIFF a 32 bit in formato latitudine/longitudine per IBL diffuso e per riflessioni. Per lo sfondo sferico delle scene, sono supportate anche le immagini RGB a 8 bit.

See [About working with IBL stages](working-with-ibl-stages.md).

>[!NOTE]
>
>I riferimenti ai file, diversi da quelli descritti in precedenza, presenti nel file del modello 3D principale vengono attualmente ignorati. AEM 3D non supporta i riferimenti a file di modelli 3D secondari.
Y-up è il sistema di coordinate preferito per i file FBX in questa versione.

## Ombreggiatura del materiale in un file modello 3D principale {#material-shading-in-a-primary-d-model-file}

Il file del modello nativo originale può contenere definizioni di materiale utilizzate con shader quali Blinn, Lambert o con shader procedurali. Questi materiali potenzialmente complessi sono supportati solo quando eseguite il rendering utilizzando l&#39;applicazione nativa corrispondente (ad esempio Autodesk Maya).

Per scopi di visualizzazione o per il rendering mediante il renderer rapido Refine™ predefinito, tutti i materiali sono semplificati, sostituiti o entrambi in modo che possano essere utilizzati con uno shader simile a Phong. Questo shader supporta un set limitato di attributi. Altri attributi nella definizione del materiale vengono ignorati.

Vedi [Visualizzazione delle risorse 3D](viewing-3d-assets.md).

Vedi [Rendering delle risorse 3D](rendering-3d-assets.md).

## Denominazione dei materiali in un file modello 3D principale {#naming-materials-in-a-primary-d-model-file}

Una *superficie* è definita come la superficie di un modello 3D ricoperta dallo stesso materiale. Questo materiale fornisce anche il nome della superficie. Come tale,  Adobe consiglia di assegnare i nomi ai materiali inclusi nei file di modelli 3D primari di conseguenza. Ad esempio, l&#39;uso di nomi specifici come &quot;Corpo&quot;, &quot;Finestre&quot;, &quot;Pneumatici&quot; o &quot;Rimetti&quot; è preferito all&#39;uso di nomi vaghi come &quot;Rosso&quot;, &quot;Vetro&quot;, &quot;Gomma&quot;, &quot;Alluminio&quot;.

