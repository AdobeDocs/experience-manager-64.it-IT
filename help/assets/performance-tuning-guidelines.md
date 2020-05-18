---
title: Guida all'ottimizzazione delle prestazioni di Assets
description: AEM Assets offre aree di interesse chiave per la configurazione di AEM, modifiche a hardware, software e componenti di rete per rimuovere i colli di bottiglia e ottimizzare le prestazioni.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0560d47dcffbf9b74a36ea00e118f8a176adafcd
workflow-type: tm+mt
source-wordcount: '3201'
ht-degree: 0%

---


# Guida all&#39;ottimizzazione delle prestazioni di Assets {#assets-performance-tuning-guide}

Una configurazione di Risorse Adobe Experience Manager (AEM) contiene diversi componenti hardware, software e di rete. A seconda dello scenario di distribuzione, potrebbe essere necessario apportare modifiche specifiche alla configurazione di hardware, software e componenti di rete per rimuovere i colli di bottiglia delle prestazioni.

Inoltre, l’identificazione e il rispetto di alcune linee guida per l’ottimizzazione hardware e software consente di creare solide basi per l’implementazione di Risorse AEM, al fine di soddisfare le aspettative in termini di prestazioni, scalabilità e affidabilità.

Le scarse prestazioni in Risorse AEM possono influire sull’esperienza degli utenti in relazione alle prestazioni interattive, all’elaborazione delle risorse, alla velocità di download e ad altre aree.

In realtà, l&#39;ottimizzazione delle prestazioni è un&#39;attività fondamentale che esegui prima di stabilire le metriche di destinazione per qualsiasi progetto.

Di seguito sono riportate alcune aree di interesse principali intorno alle quali è possibile individuare e risolvere problemi di prestazioni prima che abbiano un impatto sugli utenti.

## Platform {#platform}

AEM è supportato su diverse piattaforme, ma Adobe ha trovato il maggiore supporto per gli strumenti nativi su Linux e Windows, il che contribuisce a ottimizzare le prestazioni e a semplificare l&#39;implementazione. È consigliabile implementare un sistema operativo a 64 bit in grado di soddisfare i requisiti di memoria elevati richiesti dalla distribuzione di Risorse AEM. Come per qualsiasi implementazione di AEM, è necessario implementare TarMK laddove possibile. Mentre TarMK non può essere ridimensionato oltre una singola istanza di creazione, si è scoperto che funziona meglio di MongoMK. Puoi aggiungere istanze di offload TarMK per aumentare la potenza di elaborazione del flusso di lavoro della distribuzione AEM Assets.

### Cartella Temp {#temp-folder}

Per migliorare i tempi di caricamento delle risorse, utilizzate lo storage ad alte prestazioni per la directory temporanea Java. In Linux e Windows, è possibile utilizzare un&#39;unità RAM o SSD. In ambienti basati su cloud, è possibile utilizzare un tipo di storage ad alta velocità equivalente. Ad esempio in Amazon EC2, un&#39;unità [effimera](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) può essere utilizzata per la cartella temp.

Presupponendo che il server disponga di memoria sufficiente, configurare un’unità RAM. In Linux, eseguite questi comandi per creare un&#39;unità RAM da 8 GB:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

In Windows OS, è necessario utilizzare un driver di terze parti per creare un&#39;unità RAM o semplicemente utilizzare storage ad alte prestazioni come SSD.

Una volta che il volume temporaneo ad alte prestazioni è pronto, impostare il parametro JVM -Djava.io.tmpdir. Ad esempio, potete aggiungere il parametro JVM di seguito alla variabile CQ_JVM_OPTS nello script bin/start di AEM:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Configurazione Java {#java-configuration}

### Versione Java {#java-version}

Poiché Oracle ha smesso di rilasciare aggiornamenti per Java 7 a partire da aprile 2015, Adobe consiglia di implementare AEM Assets su Java 8. In alcuni casi, ha dimostrato prestazioni migliorate.

### Parametri JVM {#jvm-parameters}

Impostare i seguenti parametri JVM:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=vero

## Configurazione dell&#39;archivio dati e della memoria {#data-store-and-memory-configuration}

### Configurazione archivio dati file {#file-data-store-configuration}

Per tutti gli utenti di AEM Assets è consigliabile separare l’archivio dati dall’archivio segmenti. Inoltre, la configurazione dei `maxCachedBinarySize` parametri e dei `cacheSizeInMB` parametri può contribuire a massimizzare le prestazioni. Impostate `maxCachedBinarySize` la dimensione file più piccola che può essere mantenuta nella cache. Specificate la dimensione della cache in memoria da utilizzare per il datastore all&#39;interno `cacheSizeInMB`. Adobe consiglia di impostare questo valore tra il 2 e il 10% della dimensione totale dell&#39;heap. Tuttavia, il test di carico/prestazioni può aiutare a determinare l&#39;impostazione ideale.

### Configurare la dimensione massima della cache delle immagini nel buffer {#configure-the-maximum-size-of-the-buffered-image-cache}

Quando si caricano grandi quantità di risorse in Adobe Experience Manager, per consentire picchi imprevisti nel consumo di memoria e per evitare errori JVM con OutOfMemoryErrors, ridurre la dimensione massima configurata della cache delle immagini nel buffer. Si consideri un esempio di sistema con un heap massimo (- `Xmx`param) di 5 GB, un Oak BlobCache impostato a 1 GB e una cache del documento impostata a 2 GB. In questo caso, la cache nel buffer richiederebbe al massimo 1,25 GB di memoria, lasciando solo 0,75 GB di memoria per picchi imprevisti.

Configurare la dimensione della cache nel buffer nella console Web OSGi. In `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`, impostare la proprietà `cq.dam.image.cache.max.memory` in byte. Ad esempio, 1073741824 è 1 GB (1024 x 1024 x 1024 = 1 GB).

Da AEM 6.1 SP1, se utilizzate un `sling:osgiConfig` nodo per configurare questa proprietà, accertatevi di impostare il tipo di dati su Long. Per ulteriori dettagli, consultate [CQBufferedImageCache consuma un heap durante il caricamento](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html)delle risorse.

### Archivio dati condivisi {#shared-data-stores}

L&#39;implementazione di un archivio dati file condiviso o S3 può contribuire a risparmiare spazio su disco e ad aumentare il throughput di rete nelle implementazioni su larga scala. Per ulteriori informazioni sui pro e i contro dell’utilizzo di un datastore condiviso, consulta Guida [al ridimensionamento delle](assets-sizing-guide.md)risorse.

### S3 data store {#s-data-store}

La seguente configurazione dell&#39;archivio dati S3 ( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) ha aiutato Adobe a estrarre 12,8 TB di oggetti BLOB (Binary Large Object) da un archivio dati di file esistente in un archivio dati S3 presso un sito cliente:

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Ottimizzazione della rete {#network-optimization}

Adobe consiglia di abilitare HTTPS perché molte aziende dispongono di firewall che troncano il traffico HTTP, il che influisce negativamente sui caricamenti e corrompe i file. Per caricamenti di file di grandi dimensioni, accertatevi che gli utenti dispongano di connessioni cablate alla rete perché una rete WiFi diventa rapidamente saturata. Per linee guida sull’identificazione dei colli di bottiglia della rete, consultate la Guida [al ridimensionamento delle](assets-sizing-guide.md)risorse. Per valutare le prestazioni della rete analizzando la topologia di rete, vedi Considerazioni sulla rete di [risorse](assets-network-considerations.md).

In primo luogo, la strategia di ottimizzazione della rete dipende dalla quantità di larghezza di banda disponibile e dal carico sull’istanza di AEM. Le comuni opzioni di configurazione, inclusi firewall o proxy, possono migliorare le prestazioni della rete. Ecco alcuni punti chiave da tenere a mente:

* A seconda del tipo di istanza (piccolo, moderato, grande), accertati di disporre di una larghezza di banda di rete sufficiente per l’istanza di AEM. Un’adeguata allocazione della larghezza di banda è particolarmente importante se AEM è ospitato su AWS.
* Se l’istanza di AEM è ospitata su AWS, è possibile trarre vantaggio da un criterio di ridimensionamento versatile. Aggiornate l&#39;istanza se gli utenti prevedono un carico elevato. Sgrandisci per un carico moderato o basso.
* HTTPS: La maggior parte degli utenti dispone di firewall che troncano il traffico HTTP, il che può avere un impatto negativo sul caricamento di file o persino di file danneggiati durante l’operazione di caricamento.
* Caricamenti di file di grandi dimensioni: Verificate che gli utenti dispongano di connessioni cablate alla rete (le connessioni WiFi si saturano rapidamente).

## Flussi di lavoro {#workflows}

### Flussi di lavoro transitori {#transient-workflows}

Laddove possibile, impostate il flusso di lavoro Aggiorna risorsa DAM su Temporaneo. L&#39;impostazione riduce notevolmente i costi generali necessari per l&#39;elaborazione dei flussi di lavoro perché, in questo caso, i flussi di lavoro non devono passare attraverso i normali processi di monitoraggio e archiviazione.

>[!NOTE]
>
>Per impostazione predefinita, il flusso di lavoro Aggiorna risorsa DAM è impostato su Temporaneo in AEM 6.3. In questo caso, potete saltare la seguente procedura.

1. Aprite `http://localhost:4502/miscadmin` l’istanza di AEM da configurare.

1. Dalla struttura di navigazione, espandi **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]** > **[!UICONTROL dam]**.
1. Fate doppio clic su **[!UICONTROL DAM Update Asset (Aggiorna risorsa]** DAM).
1. Dal pannello degli strumenti mobile, passate alla scheda **[!UICONTROL Pagina]** e fate clic su Proprietà **** pagina.
1. Selezionate Flusso di lavoro **** transitorio e fate clic su **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Alcune funzioni non supportano flussi di lavoro transitori. Se la distribuzione di AEM Assets richiede queste funzioni, non configurare flussi di lavoro transitori.

   Nei casi in cui non è possibile utilizzare flussi di lavoro transitori, esegui regolarmente la rimozione del flusso di lavoro per eliminare i flussi di lavoro archiviati di DAM Update Asset per garantire che le prestazioni del sistema non si compromettano.

   In genere, è consigliabile eseguire i flussi di lavoro di eliminazione settimanali. Tuttavia, negli scenari che richiedono risorse, ad esempio durante l’assimilazione di risorse su larga scala, potete eseguirle con maggiore frequenza.

   Per configurare la rimozione del flusso di lavoro, aggiungi una nuova configurazione Adobe Granite Workflow Purge tramite la console OSGi. Quindi, configurate e pianificate il flusso di lavoro come parte della finestra di manutenzione settimanale.

   Se l&#39;eliminazione dura troppo, si verifica un timeout. È quindi necessario assicurarsi che i processi di eliminazione siano completati in modo da evitare situazioni in cui i flussi di lavoro di eliminazione non vengono completati a causa dell’elevato numero di flussi di lavoro.

   Ad esempio, dopo aver eseguito numerosi flussi di lavoro non transitori (che crea nodi di istanza del flusso di lavoro), puoi eseguire [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) su base ad hoc. Rimuove immediatamente le istanze del flusso di lavoro ridondanti e completate anziché attendere l&#39;esecuzione della pianificazione Adobe Granite Workflow Purge.

### Numero massimo di processi paralleli {#maximum-parallel-jobs}

Per impostazione predefinita, AEM esegue un numero massimo di processi paralleli pari al numero di processori presenti sul server. Il problema di questa impostazione è che durante i periodi di carico eccessivo, tutti i processori sono occupati da flussi di lavoro Risorse aggiornamento DAM, rallentando la reattività dell’interfaccia utente e impedendo ad AEM di eseguire altri processi che salvaguardano le prestazioni e la stabilità del server. Come procedura corretta, impostare questo valore su metà dei processori disponibili sul server eseguendo la procedura seguente:

1. In AEM Author, andate a [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent).
1. Fate clic su Modifica in ogni coda di workflow rilevante per l’implementazione, ad esempio Granite Transient Workflow Queue (Coda flussi di lavoro transitori granita).
1. Modificate il valore di Massimo processi paralleli e fate clic su Salva.

L&#39;impostazione di una coda a metà dei processori disponibili è una soluzione praticabile con cui iniziare. Tuttavia, potrebbe essere necessario aumentare o diminuire questo numero per ottenere il massimo throughput e ottimizzarlo in base all&#39;ambiente. Sono presenti code separate per flussi di lavoro transitori e non transitori, nonché per altri processi, come i flussi di lavoro esterni. Se diverse code impostate al 50% dei processori sono attivi contemporaneamente, il sistema può sovraccaricare rapidamente. Le code che vengono utilizzate in modo molto diffuso variano notevolmente tra le implementazioni degli utenti. Di conseguenza, potrebbe essere necessario configurarli con attenzione per la massima efficienza senza compromettere la stabilità del server.

### Offload {#offloading}

Per flussi di lavoro o flussi di lavoro ad alta intensità di risorse, come la transcodifica video, potete scaricare flussi di lavoro DAM Update Asset in una seconda istanza di authoring. Spesso, il problema dello scaricamento è che qualsiasi carico salvato mediante l&#39;offload dell&#39;elaborazione del flusso di lavoro viene compensato dal costo della replica del contenuto avanti e indietro tra le istanze.

A partire da AEM 6.2 e con un pacchetto di funzioni per AEM 6.1, potete eseguire lo scaricamento con la replica binaria-less. In questo modello, le istanze dell&#39;autore condividono un datastore comune e inviano i metadati solo avanti e indietro attraverso la replica in avanti. Anche se questo approccio funziona bene con un archivio dati file condiviso, possono verificarsi problemi con un archivio dati S3. Poiché i thread di scrittura in background possono determinare una latenza, è possibile che una risorsa non sia stata scritta nel datastore prima dell&#39;inizio del processo di scaricamento.

### Configurazione risorsa aggiornamento DAM {#dam-update-asset-configuration}

Il flusso di lavoro Aggiorna risorsa DAM contiene una suite completa di passaggi configurati per attività quali generazione PTIFF di Scene7 e integrazione con InDesign Server. Tuttavia, la maggior parte degli utenti potrebbe non richiedere diversi di questi passaggi. Adobe consiglia di creare una copia personalizzata del modello di flusso di lavoro Aggiorna risorsa DAM e di rimuovere eventuali passaggi superflui. In questo caso, aggiornate gli avviatori per DAM Update Asset in modo che puntino al nuovo modello.

>[!NOTE]
>
>L&#39;esecuzione intensiva del flusso di lavoro DAM Update Asset (Aggiorna risorsa DAM) può aumentare notevolmente la dimensione del datatastore del file. I risultati di un esperimento eseguito da Adobe hanno dimostrato che la dimensione del datastore può aumentare di circa 400 GB se vengono eseguiti circa 5500 flussi di lavoro entro 8 ore.
>
>Si tratta di un aumento temporaneo e il datastore viene ripristinato alle dimensioni originali dopo l&#39;esecuzione dell&#39;attività di raccolta dei rifiuti del datastore.
>
>In genere, l&#39;attività di raccolta rifiuti del datastore viene eseguita settimanalmente insieme ad altre attività di manutenzione pianificate.
>
>Se disponete di uno spazio su disco limitato ed eseguite i flussi di lavoro DAM Update Asset in modo intensivo, prendete in considerazione la pianificazione dell&#39;attività di raccolta dei rifiuti con maggiore frequenza.

#### Generazione di rappresentazioni in fase di esecuzione {#runtime-rendition-generation}

I clienti utilizzano immagini di varie dimensioni e formati all&#39;interno del sito Web o per la distribuzione ai partner commerciali. Poiché ogni rappresentazione aggiunge un’impronta alla risorsa nell’archivio, Adobe consiglia di usare questa funzione con cautela. Per ridurre la quantità di risorse necessarie per elaborare e archiviare le immagini, potete generare queste immagini in fase di esecuzione anziché come rappresentazioni durante l’assimilazione.

Molti clienti di Sites implementano un servlet di immagini che ridimensiona e ritaglia le immagini al momento della richiesta, il che impone un carico aggiuntivo sull’istanza di pubblicazione. Tuttavia, finché queste immagini possono essere memorizzate nella cache, la sfida può essere attenuata.

Un approccio alternativo consiste nell’usare la tecnologia Scene7 per distribuire completamente la manipolazione delle immagini. Inoltre, potete implementare Brand Portal, che non solo prende in consegna le responsabilità di generazione delle rappresentazioni dall’infrastruttura AEM, ma anche l’intero livello di pubblicazione.

#### ImageMagick {#imagemagick}

Se personalizzate il flusso di lavoro DAM Update Asset per generare rappresentazioni utilizzando ImageMagick, Adobe consiglia di modificare il file policy.xml in */etc/ImageMagick/*. Per impostazione predefinita, ImageMagick utilizza l’intero spazio disponibile sul volume del sistema operativo e la memoria disponibile. Apportate le seguenti modifiche di configurazione nella `policymap` sezione policy.xml per limitare tali risorse.

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

Inoltre, impostare il percorso della cartella temporanea di ImageMagick nel file *configure.xml* (o impostando la variabile di ambiente `MAGIC_TEMPORARY_PATH`) su una partizione del disco con spazio sufficiente e IOPS.

>[!CAUTION]
>
>Una configurazione errata può rendere instabile il server se ImageMagick utilizza tutto lo spazio disponibile su disco. Le modifiche dei criteri necessarie per elaborare file di grandi dimensioni con ImageMagick possono influire sulle prestazioni di AEM. Per ulteriori informazioni, consultate [installare e configurare ImageMagick](best-practices-for-imagemagick.md).

>[!NOTE]
>
>I file ImageMagick `policy.xml` e `configure.xml` imageMagick si trovano in `/usr/lib64/ImageMagick-*/config/` anziché `/etc/ImageMagick/`. Per informazioni dettagliate sui percorsi dei file di configurazione, consultate la documentazione [di](https://www.imagemagick.org/script/resources.php) ImageMagick.

Se utilizzi AEM su Adobe Managed Services (AMS), contatta l’Assistenza clienti Adobe se intendi elaborare molti file PSD o PSB di grandi dimensioni. Experience Manager potrebbe non essere in grado di elaborare file PSB ad alta risoluzione con risoluzione superiore a 30000 x 23000 pixel.

<!-- 

#### Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model 
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents **workflow model 

-->

<!--
# Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model.
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents** workflow model.
-->

### XMP writeback {#xmp-writeback}

La funzione di writeback XMP aggiorna la risorsa originale ogni volta che i metadati vengono modificati in AEM, con le seguenti conseguenze:

* La risorsa stessa viene modificata
* Viene creata una versione della risorsa
* Risorsa aggiornamento DAM viene eseguita sulla risorsa

I risultati elencati richiedono notevoli risorse. Adobe consiglia pertanto di [disattivare la funzione di Write](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html)XMP, se non è necessaria.

Se è selezionato il flag di flusso di lavoro di esecuzione, l&#39;importazione di una grande quantità di metadati può comportare attività di reinserimento XMP che richiedono risorse. Pianificate tale importazione durante l&#39;utilizzo di un server snello in modo che le prestazioni per altri utenti non vengano compromesse.

## Replica {#replication}

Quando si replicano le risorse in un numero elevato di istanze pubblicate, ad esempio in un&#39;implementazione di Sites, Adobe consiglia di utilizzare la replica a catena. In questo caso, l’istanza di creazione si replica in una singola istanza di pubblicazione che a sua volta viene replicata nelle altre istanze di pubblicazione, liberando l’istanza di creazione.

### Configurare la replica della catena {#configure-chain-replication}

1. Scegliere l&#39;istanza di pubblicazione da utilizzare per concatenare le repliche
1. In tale istanza di pubblicazione aggiungere agenti di replica che puntano alle altre istanze di pubblicazione
1. Per ciascuno di questi agenti di replica, abilita **[!UICONTROL Alla ricezione]** nella scheda **[!UICONTROL Triggers]**

>[!NOTE]
>
>Adobe non consiglia di attivare automaticamente le risorse. Tuttavia, se necessario, Adobe consiglia di eseguire questa operazione come passaggio finale in un flusso di lavoro, in genere DAM Update Asset.

## Indice di ricerca {#search-indexes}

Assicuratevi di implementare i Service Pack più recenti e gli hotfix correlati alle prestazioni, in quanto spesso includono aggiornamenti agli indici di sistema. Consultate Suggerimenti per l’ottimizzazione [delle prestazioni | 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) per alcune ottimizzazioni indice che possono essere applicate, a seconda della versione di AEM in uso.

Creare indici personalizzati per le query eseguite spesso. Per informazioni dettagliate, consultate [Metodologia per l’analisi di query](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) lente e per la creazione di [indici](/help/sites-deploying/queries-and-indexing.md)personalizzati. Per ulteriori informazioni sulle best practice relative alle query e agli indici, consulta [Best practice per query e indicizzazione](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Configurazioni indice Lucene {#lucene-index-configurations}

Alcune ottimizzazioni possono essere eseguite sulle configurazioni dell&#39;indice Oak, per migliorare le prestazioni di Risorse AEM:

Aggiorna la configurazione di LuceneIndexProvider:

1. Andate a /system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. Abilita **[!UICONTROL CopyOnRead, CopyOnWrite e Preacquisizione dei file]** di indice nelle versioni precedenti a AEM 6.2. Questi valori sono attivati per impostazione predefinita in AEM 6.2 e versioni successive.

Aggiornare le configurazioni dell&#39;indice per migliorare il tempo di reindicizzazione:

1. Aprite CRXDe /crx/de/index.jsp ed effettuate l’accesso come utente amministrativo
1. Passa a /oak:index/lucene
1. Aggiungere una proprietà String[] denominata **[!UICONTROL excludedPaths]** con valori &quot;/var&quot;, &quot;/etc/workflow/instance&quot; e &quot;/etc/Replication&quot;
1. Passa a /oak:index/damAssetLucene
1. Aggiungere una proprietà String[] denominata **[!UICONTROL includePaths]** con un valore &quot;/content/dam&quot;
1. Salva

(solo AEM 6.1 e 6.2) Aggiornate l’indice ntBaseLucene per migliorare le prestazioni di eliminazione e spostamento delle risorse:

1. Passa a */quercia:index/ntBaseLucene/indexRules/nt:base/properties*
1. Aggiungere due nodi nt:unstructure **[!UICONTROL slingResource]** e **[!UICONTROL damResolvedPath]** in */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Impostare le proprietà seguenti sui nodi (dove le proprietà ordered e propertyIndex sono di tipo *Boolean*:

   slingResource

   name=&quot;sling:resource&quot;

   ordered=false

   propertyIndex= true

   type=&quot;String&quot;

   damResolvedPath

   name=&quot;dam:resolvePath&quot;

   ordered=false

   propertyIndex=true

   type=&quot;String&quot;

1. Sul nodo /oak:index/ntBaseLucene, imposta la proprietà `reindex=true`
1. Fate clic su **[!UICONTROL Salva tutto]**
1. Monitorate il file error.log per vedere quando l&#39;indicizzazione è completata:

   Reindicizzazione completata per gli indici: [/oak:index/ntBaseLucene]

1. È inoltre possibile verificare che l&#39;indicizzazione viene completata aggiornando il nodo /oak:index/ntBaseLucene in CRXDe, poiché la proprietà reindex torna a false
1. Una volta completata l&#39;indicizzazione, tornare a CRXDe e impostare la proprietà **[!UICONTROL type]** su disabled su questi due indici

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Fate clic su **[!UICONTROL Salva tutto]**

Disattiva estrazione testo Lucene:

Se non è necessario che gli utenti siano in grado di eseguire ricerche nel contenuto delle risorse, ad esempio, cercando il testo contenuto nei documenti PDF, potete migliorare le prestazioni dell’indice disattivando questa funzione.

1. Andate al gestore pacchetti AEM /crx/packmgr/index.jsp
1. Caricate e installate il pacchetto di seguito

[Ottieni file](assets/disable_indexingbinarytextextraction-10.zip)

### Totale {#guess-total}

Quando create query che generano set di risultati di grandi dimensioni, utilizzate il `guessTotal` parametro per evitare un utilizzo eccessivo della memoria durante la loro esecuzione.

## Problemi noti {#known-issues}

### File grandi {#large-files}

Esistono due importanti problemi noti relativi ai file di grandi dimensioni in AEM. Quando i file raggiungono dimensioni superiori a 2 GB, la sincronizzazione in standby a freddo può trovarsi in una situazione di memoria insufficiente. In alcuni casi, impedisce l&#39;esecuzione della sincronizzazione in standby. In altri casi, causa l&#39;arresto anomalo dell&#39;istanza principale. Questo scenario si applica a qualsiasi file in AEM maggiore di 2 GB, inclusi i pacchetti di contenuto.

Allo stesso modo, quando i file raggiungono le dimensioni di 2 GB durante l&#39;utilizzo di un datastore S3 condiviso, potrebbe essere necessario del tempo per mantenere il file completamente persistente dalla cache al file system. Di conseguenza, quando si utilizza la replica senza binario, è possibile che i dati binari non siano stati persistenti prima del completamento della replica. Questa situazione può causare problemi, soprattutto se la disponibilità di dati è importante, ad esempio negli scenari di scarico.

## Test delle prestazioni {#performance-testing}

Per ogni implementazione di AEM, stabilite un regime di test delle prestazioni in grado di identificare e risolvere rapidamente i colli di bottiglia. Ecco alcune aree chiave su cui concentrarsi.

### Test della rete {#network-testing}

Per tutti i problemi di prestazioni della rete da parte del cliente, eseguire le seguenti operazioni:

* Verificare le prestazioni della rete dall&#39;interno della rete del cliente
* Verificare le prestazioni di rete dalla rete Adobe. Per i clienti di AMS, collabora con il tuo CSE per eseguire il test dall&#39;interno della rete Adobe.
* Verificare le prestazioni di rete da un altro punto di accesso
* Utilizzando uno strumento di benchmark di rete
* Prova contro lo speditore

### Test delle istanze di AEM {#aem-instance-testing}

Per ridurre al minimo la latenza e ottenere un throughput elevato grazie all’utilizzo efficiente della CPU e alla condivisione del carico, controlla regolarmente le prestazioni dell’istanza AEM. In particolare:

* Eseguire test di carico sull’istanza AEM
* Monitoraggio delle prestazioni di caricamento e risposta dell’interfaccia utente

## Elenco di controllo delle prestazioni di AEM Assets {#aem-assets-performance-checklist}

* Abilitate HTTPS per aggirare eventuali misuratori di traffico HTTP aziendali.
* Usate una connessione cablata per il caricamento di risorse pesanti.
* Impostare parametri JVM ottimali.
* Configurare un archivio dati del file system o un archivio dati S3.
* Disattiva la generazione delle risorse secondarie. Se è attivato, il flusso di lavoro di AEM crea una risorsa separata per ogni pagina di una risorsa con più pagine. Ciascuna di queste pagine è una singola risorsa che consuma ulteriore spazio su disco, richiede il controllo delle versioni e un&#39;ulteriore elaborazione del flusso di lavoro. Se non sono necessarie pagine separate, disattivate la generazione di risorse secondarie e le attività di estrazione della pagina.
* Abilita flussi di lavoro transitori.
* Regola le code del flusso di lavoro Granite per limitare i processi simultanei.
* Configurare ImageMagick per limitare il consumo di risorse.
* Rimuovete i passaggi superflui dal flusso di lavoro DAM Update Asset (Aggiorna risorsa).
* Configurare l&#39;eliminazione del flusso di lavoro e delle versioni.
* Ottimizzare la configurazione dell&#39;indice Lucene.
* Ottimizzate gli indici con i service pack e gli hotfix più recenti. Consultate il supporto Adobe per eventuali ottimizzazioni di indice aggiuntive disponibili.
* Utilizzare `guessTotal` per ottimizzare le prestazioni della query.
* If you configure AEM to detect file types from the content of the files (by configuring [!UICONTROL Day CQ DAM Mime Type Service] in the [!UICONTROL AEM Web Console]), upload many files in bulk during non-peak hours as the operation is resource-intensive.
