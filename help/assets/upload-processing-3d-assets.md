---
title: Caricamento ed elaborazione di risorse 3D in AEM
seo-title: Caricamento ed elaborazione di risorse 3D in AEM
description: Procedure ottimali per il caricamento e l’elaborazione di risorse 3D.
seo-description: Procedure ottimali per il caricamento e l’elaborazione di risorse 3D.
uuid: d8abf460-adff-4f0f-92ae-2c8651a17488
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: a0319701-21eb-4b7f-8b2e-ac81a7a75875
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 71%

---


# Caricamento ed elaborazione di risorse 3D in AEM {#about-the-uploading-and-processing-of-d-assets-in-aem}

Utilizza i meccanismi standard di caricamento o sincronizzazione per portare le risorse 3D e i file di riferimento associati agli AEM Assets.

Consulta [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets).

 Adobe consiglia di caricare tutti i file di riferimento prima o allo stesso tempo il file del modello 3D principale. Tuttavia, questo non è un requisito.

Una volta completato il caricamento, i file 3D vengono convertiti e viene applicata un&#39;elaborazione aggiuntiva per preparare la risorsa per la visualizzazione e il rendering.

## Buone pratiche per il caricamento di risorse 3D {#best-practices-for-uploading-d-assets}

* Generalmente, non ci sono restrizioni sulla posizione in cui si carica il contenuto 3D nella gerarchia delle cartelle AEM Assets. La risoluzione automatizzata delle dipendenze dei file di AEM 3D, tuttavia, ha limitazioni di intervallo per controllare il tempo necessario alla ricerca di repository di risorse grandi. Pertanto, Adobe consiglia di caricare le risorse 3D e i relativi file dipendenti entro una distanza ragionevole da ciascun file (cartella sopra la cartella genitore in comune). Una volta risolte le dipendenze dei file, è possibile spostare liberamente sia la risorsa 3D che i suoi dipendenti in qualsiasi punto dell&#39;archivio senza perdere le relazioni stabilite.
* Adobe consiglia di scegliere una struttura di cartelle coerente per il contenuto 3D *prima* di procedere all&#39;upload. I seguenti suggerimenti sono alcuni degli approcci suggeriti che puoi adottare:

   * **Mantenere una cartella separata per ogni risorsa 3D caricata**.

      La cartella contiene sia il file del modello 3D primario che tutti i suoi dipendenti. Mentre mettere tutte le risorse e i dipendenti in un&#39;unica cartella è facile da implementare, è ingombrante cercare i contenuti. Inoltre, complica la condivisione delle dipendenze (mappe di texture) tra i modelli.

   * **Mantieni i modelli in una cartella e i dipendenti in una cartella di pari livello o in una sottocartella**.

      Questo approccio favorisce facilmente la condivisione di dipendenti tra i modelli. Tuttavia, può diventare difficile trovare dipendenti specifici se il numero di risorse è elevato.

   * **Gerarchie di cartelle separate e parallele per modelli e dipendenti.**

      È possibile modellare questo approccio in base a come le applicazioni di creazione 3D come Autodesk Maya preferiscono archiviare i contenuti.

* Le risorse dipendenti non devono essere eliminate a meno che non vengano rimosse anche le risorse 3D associate o le risorse che vi facevano riferimento. Tuttavia, è possibile eliminare liberamente le risorse 3D senza dover eliminare le risorse dipendenti. Se una dipendenza viene accidentalmente persa, è possibile risolverla facilmente per ripristinarla.

   Consulta Risoluzione delle dipendenze dei file.

## Considerazioni sulle prestazioni durante il caricamento di file 3D {#performance-considerations-when-uploading-d-files}

La conversione e l&#39;elaborazione di file 3D in genere consumano notevoli risorse di CPU e di memoria su un server. Inoltre richiedono una notevole quantità di tempo. I tempi di elaborazione spesso variano notevolmente a seconda delle dimensioni del modello e delle capacità del server. Ad esempio, un tipico modello piccolo con meno di 100.000 facce è solitamente pronto per la visualizzazione in meno di un minuto e viene elaborato completamente in 2-3 minuti. Un grande modello con più di un milione di facce può invece richiedere decine di minuti per essere elaborato completamente.

I lavori di conversione, elaborazione e rendering vengono messi in coda in base alle necessità per evitare di rallentare troppo il server. The message &quot;Waiting for processing...&quot; is sometimes shown in the **[!UICONTROL Card View]** at the time you uploaded assets. Questo stato indica che altri lavori di elaborazione o rendering devono terminare prima che l&#39;attività corrente venga elaborata.

Sono disponibili meccanismi per limitare l’utilizzo della CPU per l’elaborazione dell’assimilazione e per il rendering. Consultate Impostazioni [di configurazione](advanced-config-3d.md) avanzate per informazioni su come configurare i limiti della CPU.

## Monitoraggio dello stato di elaborazione dei file 3D caricati {#monitoring-the-processing-status-of-your-uploaded-d-files}

In **[!UICONTROL Card View]** only, the processing status and progression is displayed as a progress banner on the asset&#39;s card. Ogni modello 3D caricato in genere si trova nelle seguenti fasi di elaborazione ordinata da 4 a 6:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Fase di elaborazione</strong><br /> </td> 
   <td><strong>Nomi di elaborazione</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>Elaborazione</td> 
   <td>Elaborazione iniziale di base ed estrazione dei metadati.</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>Conversione del formato</td> 
   <td>Il modello 3D viene convertito da un formato nativo (Autodesk® Maya® o Autodesk® 3ds Max®) a un formato intermedio (FBX).</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Creazione dell'anteprima</td> 
   <td>Il file FBX o OBJ viene assimilato ed elaborato. Le dipendenze dei file vengono valutate e risolte, ove possibile, come riferimenti di risorse.</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>Creazione di un’ombra esterna</td> 
   <td>Facoltativo. Consente di generare un'ombreggiatura di occlusione ambiente sul piano terreno sotto l'oggetto 3D. Consultate Impostazioni <a href="/help/assets/advanced-config-3d.md">di configurazione</a> avanzate per attivare o disattivare questa elaborazione.</td> 
  </tr> 
  <tr> 
   <td>5<br /> </td> 
   <td>Creazione di mappe luminose</td> 
   <td>Facoltativo. Consente di aumentare la qualità dell'anteprima interattiva e accelerare il rendering con il modulo di rendering predefinito. Consultate Impostazioni <a href="/help/assets/advanced-config-3d.md">di configurazione</a> avanzate per attivare o disattivare questa elaborazione.</td> 
  </tr> 
  <tr> 
   <td>6<br /> </td> 
   <td>Creazione di animazioni</td> 
   <td>Facoltativo. Consente di generare una semplice animazione che viene poi utilizzata come miniatura visiva nella Vista a schede. Consultate Impostazioni <a href="/help/assets/advanced-config-3d.md">di configurazione</a> avanzate per attivare o disattivare questa elaborazione.</td> 
  </tr> 
  <tr> 
   <td>7<br /> </td> 
   <td>In attesa di elaborazione</td> 
   <td>Visualizzato quando altre risorse 3D hanno priorità di elaborazione. Per esempio, risorse caricate in precedenza che non hanno ancora completato l'elaborazione.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>You can view a 3D asset in **[!UICONTROL Detail View]** or render it after the Creating preview stage is complete. Non è necessario attendere il completamento di tutti gli stadi di elaborazione.

