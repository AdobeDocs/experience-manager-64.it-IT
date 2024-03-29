---
title: Guida all’ottimizzazione delle prestazioni di Assets
description: Aree chiave intorno [!DNL Experience Manager] configurazione, modifiche a hardware, software e componenti di rete per rimuovere i colli di bottiglia e ottimizzare le prestazioni [!DNL Experience Manager] Risorse.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: 6c1bff46-f9e0-4638-9374-a9e820d30534
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3203'
ht-degree: 1%

---

# Guida all’ottimizzazione delle prestazioni di Assets {#assets-performance-tuning-guide}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Una configurazione di Adobe Experience Manager Assets contiene diversi componenti hardware, software e di rete. A seconda dello scenario di distribuzione, potrebbe essere necessario apportare modifiche specifiche alla configurazione di hardware, software e componenti di rete per rimuovere i colli di bottiglia delle prestazioni.

Inoltre, l&#39;identificazione e l&#39;aderenza a determinate linee guida per l&#39;ottimizzazione di hardware e software aiuta a creare una base audio che consenta al tuo [!DNL Experience Manager] Distribuzione delle risorse per soddisfare le aspettative relative a prestazioni, scalabilità e affidabilità.

Scarse prestazioni in [!DNL Experience Manager] Le risorse possono influenzare l’esperienza degli utenti in relazione alle prestazioni interattive, all’elaborazione delle risorse, alla velocità di download e ad altre aree.

L’ottimizzazione delle prestazioni è infatti un’attività fondamentale da eseguire prima di stabilire le metriche di destinazione per qualsiasi progetto.

Di seguito sono elencate alcune aree principali intorno alle quali puoi individuare e risolvere i problemi di prestazioni prima che abbiano un impatto sugli utenti.

## Platform {#platform}

Quando [!DNL Experience Manager] è supportato su diverse piattaforme, Adobe ha trovato il supporto più grande per gli strumenti nativi su Linux e Windows, che contribuisce alle prestazioni ottimali e alla facilità di implementazione. Idealmente, è necessario implementare un sistema operativo a 64 bit per soddisfare i requisiti di memoria elevati di un [!DNL Experience Manager] Distribuzione di risorse. Come qualsiasi [!DNL Experience Manager] implementa TarMK laddove possibile. Mentre TarMK non può scalare oltre una singola istanza di authoring, si scopre che funziona meglio di MongoMK. Puoi aggiungere istanze di offload TarMK per aumentare la potenza di elaborazione del flusso di lavoro del tuo [!DNL Experience Manager] Distribuzione di risorse.

### Cartella temporanea {#temp-folder}

Per migliorare i tempi di caricamento delle risorse, utilizza l’archiviazione ad alte prestazioni per la directory temporanea Java. Su Linux e Windows, è possibile utilizzare un&#39;unità RAM o SSD. In ambienti basati su cloud, è possibile utilizzare un tipo di storage ad alta velocità equivalente. Ad esempio in Amazon EC2, un [azionamento effimero](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) L&#39;unità può essere utilizzata per la cartella temporanea.

Supponendo che il server disponga di una memoria ampia, configura un&#39;unità RAM. Su Linux, esegui questi comandi per creare un&#39;unità RAM da 8 GB:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

In Windows OS, è necessario utilizzare un driver di terze parti per creare un&#39;unità RAM o semplicemente utilizzare un&#39;unità di storage ad alte prestazioni come SSD.

Una volta pronto il volume temporaneo ad alte prestazioni, imposta il parametro JVM -Djava.io.tmpdir. Ad esempio, puoi aggiungere il parametro JVM qui sotto alla variabile CQ_JVM_OPTS nello script bin/start di AEM:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Configurazione Java {#java-configuration}

### Versione Java {#java-version}

Poiché Oracle ha cessato di rilasciare aggiornamenti per Java 7 a partire da aprile 2015, Adobe consiglia di implementare [!DNL Experience Manager] Risorse su Java 8. In alcuni casi, ha dimostrato prestazioni migliori.

### Parametri JVM {#jvm-parameters}

Imposta i seguenti parametri JVM:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=vero

## Configurazione dell&#39;archivio dati e della memoria {#data-store-and-memory-configuration}

### Configurazione archivio dati file {#file-data-store-configuration}

È consigliabile separare l’archivio dati dall’archivio segmenti per tutti [!DNL Experience Manager] Utenti di Assets. Inoltre, configura la `maxCachedBinarySize` e `cacheSizeInMB` i parametri possono contribuire a massimizzare le prestazioni. Imposta `maxCachedBinarySize` alla dimensione più piccola del file che può essere mantenuta nella cache. Specifica la dimensione della cache in memoria da utilizzare per l’archivio dati in `cacheSizeInMB`. Adobe consiglia di impostare questo valore tra il 2 e il 10% della dimensione totale dell&#39;heap. Tuttavia, il test di carico/prestazioni può aiutare a determinare l&#39;impostazione ideale.

### Configura la dimensione massima della cache delle immagini bufferizzate {#configure-the-maximum-size-of-the-buffered-image-cache}

Quando si caricano grandi quantità di risorse in Adobe Experience Manager, per consentire picchi imprevisti nel consumo di memoria e per evitare errori JVM con OutOfMemoryErrors, ridurre la dimensione massima configurata della cache immagine bufferizzata. Considera un esempio di sistema con un heap massimo (- `Xmx`param) di 5 GB, un Oak BlobCache impostato a 1 GB, e la cache del documento impostata a 2 GB. In questo caso, la cache bufferizzata richiederebbe un massimo di 1,25 GB e memoria, lasciando solo 0,75 GB di memoria per picchi imprevisti.

Configura la dimensione della cache bufferizzata nella console Web OSGi. A `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`, imposta la proprietà `cq.dam.image.cache.max.memory` in byte. Ad esempio, 1073741824 è 1 GB (1024 x 1024 x 1024 = 1 GB).

Da [!DNL Experience Manager] 6.1 SP1, se utilizzi un `sling:osgiConfig` nodo per la configurazione di questa proprietà, assicurarsi di impostare il tipo di dati su Long. Per ulteriori dettagli, consulta [CQBufferedImageCache consuma heap durante il caricamento delle risorse](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Archiviazione dati condivisa {#shared-data-stores}

L&#39;implementazione di un S3 o Shared File Datastore può aiutare a risparmiare spazio su disco e ad aumentare il throughput di rete nelle implementazioni su larga scala. Per ulteriori informazioni sui pro e i contro dell’utilizzo di un datastore condiviso, consulta [Guida al dimensionamento delle risorse](assets-sizing-guide.md).

### Archiviazione dati S3 {#s-data-store}

La seguente configurazione dell’archivio dati S3 ( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) ha aiutato Adobe ad estrarre 12,8 TB di oggetti BLOB (binari di grandi dimensioni) da un archivio dati di file esistente in un archivio dati S3 in un sito cliente:

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

L’Adobe consiglia di abilitare HTTPS perché molte aziende dispongono di firewall per l’attivazione del traffico HTTP, il che influisce negativamente sui caricamenti e corrompe i file. Per caricamenti di file di grandi dimensioni, assicurati che gli utenti abbiano connessioni cablate alla rete perché una rete WiFi diventa rapidamente saturata. Per le linee guida sull&#39;identificazione delle strozzature di rete, vedi [Guida al dimensionamento delle risorse](assets-sizing-guide.md). Per valutare le prestazioni della rete analizzando la topologia di rete, vedi [Considerazioni sulla rete delle risorse](assets-network-considerations.md).

In primo luogo, la strategia di ottimizzazione della rete dipende dalla quantità di larghezza di banda disponibile e dal carico sul [!DNL Experience Manager] istanza. Opzioni di configurazione comuni, inclusi firewall o proxy, possono contribuire a migliorare le prestazioni di rete. Ecco alcuni punti chiave da tenere a mente:

* A seconda del tipo di istanza (piccolo, moderato, grande), assicurati di disporre di una larghezza di banda di rete sufficiente per [!DNL Experience Manager] istanza. Un&#39;adeguata allocazione della larghezza di banda è particolarmente importante se [!DNL Experience Manager] è ospitato su AWS.
* Se [!DNL Experience Manager] L&#39;istanza è ospitata su AWS, è possibile beneficiare di una policy di scalabilità versatile. Aggiorna l&#39;istanza se gli utenti prevedono un carico elevato. Ridimensionarla per un carico moderato/basso.
* HTTPS: La maggior parte degli utenti dispone di firewall che annusano il traffico HTTP, che può avere un impatto negativo sul caricamento di file o persino di file corrotti durante l’operazione di caricamento.
* Caricamenti di file di grandi dimensioni: Assicurati che gli utenti abbiano connessioni cablate alla rete (le connessioni WiFi saturano rapidamente).

## Flussi di lavoro {#workflows}

### Flussi di lavoro transitori {#transient-workflows}

Laddove possibile, imposta il flusso di lavoro Aggiorna risorsa DAM su Transitent. L’impostazione riduce notevolmente i costi generali necessari per elaborare i flussi di lavoro perché, in questo caso, i flussi di lavoro non devono passare attraverso i normali processi di tracciamento e archiviazione.

>[!NOTE]
>
>Per impostazione predefinita, il flusso di lavoro Aggiorna risorsa DAM è impostato su Transitent in [!DNL Experience Manager] 6.3. In questo caso, è possibile saltare la seguente procedura.

1. Apri `http://localhost:4502/miscadmin` sulla [!DNL Experience Manager] istanza da configurare.

1. Dalla struttura di navigazione, espandi **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]** > **[!UICONTROL dam]**.
1. Fare doppio clic **[!UICONTROL Risorsa di aggiornamento DAM]**.
1. Dal pannello degli strumenti mobili, passa alla **[!UICONTROL Pagina]** , quindi fai clic su **[!UICONTROL Proprietà pagina]**.
1. Seleziona **[!UICONTROL Flusso di lavoro transitorio]** Fai clic su **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Alcune funzionalità non supportano flussi di lavoro transitori. Se [!DNL Experience Manager] La distribuzione delle risorse richiede queste funzionalità e non configura flussi di lavoro transitori.

   Nei casi in cui non è possibile utilizzare flussi di lavoro transitori, esegui regolarmente l’eliminazione del flusso di lavoro per eliminare i flussi di lavoro archiviati DAM Update Asset per garantire che le prestazioni del sistema non peggiorino.

   Normalmente, è necessario eseguire lo svuotamento dei flussi di lavoro settimanalmente. Tuttavia, in scenari ad uso intensivo di risorse, ad esempio durante l’assimilazione di risorse su larga scala, puoi eseguirli più frequentemente.

   Per configurare l’eliminazione del flusso di lavoro, aggiungi una nuova configurazione Adobe Granite Workflow Purge tramite la console OSGi. Quindi, configura e pianifica il flusso di lavoro come parte della finestra di manutenzione settimanale.

   Se la pulizia viene eseguita per troppo tempo, si verifica un timeout. Pertanto, assicurati che i processi di eliminazione siano completi per evitare situazioni in cui l’eliminazione dei flussi di lavoro non riesce a essere completata a causa dell’elevato numero di flussi di lavoro.

   Ad esempio, dopo aver eseguito numerosi flussi di lavoro non transitori (che creano nodi di istanza del flusso di lavoro), puoi eseguire [Ripristino dei flussi di lavoro ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) su base ad hoc. Rimuove immediatamente le istanze del flusso di lavoro ridondanti e completate anziché attendere l’esecuzione della pianificazione di eliminazione del flusso di lavoro di Adobe Granite.

### Processi paralleli massimi {#maximum-parallel-jobs}

Per impostazione predefinita, [!DNL Experience Manager] esegue un numero massimo di processi paralleli uguale al numero di processori sul server. Il problema con questa impostazione è che durante i periodi di carico pesante, tutti i processori sono occupati dai flussi di lavoro DAM Update Asset, rallentando la reattività dell’interfaccia utente e impedendo [!DNL Experience Manager] dall&#39;esecuzione di altri processi che salvaguardano le prestazioni e la stabilità del server. Come buona pratica, imposta questo valore a metà dei processori disponibili sul server eseguendo i seguenti passaggi:

1. On [!DNL Experience Manager] Autore, vai a [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent).
1. Fai clic su Modifica in ogni coda di flusso di lavoro pertinente all’implementazione, ad esempio Granite Transitent Workflow Queue.
1. Modificare il valore di Massimo processi paralleli e fare clic su Salva.

Impostare una coda a metà dei processori disponibili è una soluzione praticabile con cui iniziare. Tuttavia, potrebbe essere necessario aumentare o diminuire questo numero per ottenere il massimo throughput e regolarlo in base all&#39;ambiente. Sono presenti code separate per i flussi di lavoro transitori e non transitori e per altri processi, ad esempio quelli esterni. Se diverse code impostate al 50% dei processori sono attive contemporaneamente, il sistema può essere sovraccaricato rapidamente. Le code utilizzate in modo massiccio variano notevolmente a seconda delle implementazioni degli utenti. Pertanto, potrebbe essere necessario configurarli con attenzione per la massima efficienza senza sacrificare la stabilità del server.

### Offload {#offloading}

Per flussi di lavoro o flussi di lavoro che richiedono un’elevata quantità di risorse, ad esempio la transcodifica video, puoi scaricare i flussi di lavoro Aggiorna risorsa DAM in una seconda istanza di authoring. Spesso, il problema dello scaricamento è che qualsiasi carico salvato scaricando l’elaborazione del flusso di lavoro viene compensato dal costo di replica del contenuto avanti e indietro tra le istanze.

A partire da [!DNL Experience Manager] 6.2 e con un pacchetto di funzioni per [!DNL Experience Manager] 6.1, è possibile eseguire lo scaricamento con la replica senza binario. In questo modello, le istanze dell’autore condividono un datastore comune e inviano i metadati avanti e indietro solo attraverso la replica in avanti. Anche se questo approccio funziona bene con un datastore di file condiviso, ci possono essere problemi con un datastore S3. Poiché i thread di scrittura in background possono causare latenza, è possibile che una risorsa non sia stata scritta nell’archivio dati prima dell’inizio del processo di scaricamento.

### Configurazione risorsa di aggiornamento DAM {#dam-update-asset-configuration}

Il flusso di lavoro Risorsa di aggiornamento DAM contiene una suite completa di passaggi configurati per attività quali la generazione PTIFF di Dynamic Media Classic e l’integrazione con InDesign Server. Tuttavia, la maggior parte degli utenti potrebbe non richiedere diversi di questi passaggi. Adobe consiglia di creare una copia personalizzata del modello di flusso di lavoro Aggiorna risorsa DAM e di rimuovere eventuali passaggi superflui. In questo caso, aggiorna i moduli di avvio per DAM Update Asset in modo che faccia riferimento al nuovo modello.

>[!NOTE]
>
>L’esecuzione intensiva del flusso di lavoro Risorsa di aggiornamento DAM può aumentare notevolmente la dimensione del datastore dei file. I risultati di un esperimento eseguito da Adobe hanno dimostrato che la dimensione del datastore può aumentare di circa 400 GB se vengono eseguiti circa 5500 flussi di lavoro in 8 ore.
>
>Si tratta di un aumento temporaneo e il datastore viene ripristinato alle dimensioni originali dopo aver eseguito l&#39;attività di raccolta rifiuti del datastore.
>
>In genere, l&#39;attività di raccolta oggetti inattivi del datastore viene eseguita settimanalmente insieme ad altre attività di manutenzione pianificate.
>
>Se hai uno spazio su disco limitato ed esegui i flussi di lavoro Aggiorna risorsa DAM in modo intensivo, considera la pianificazione dell’attività di raccolta degli oggetti inattivi con maggiore frequenza.

#### Generazione rendering runtime {#runtime-rendition-generation}

I clienti utilizzano immagini di varie dimensioni e formati sul proprio sito web o per la distribuzione ai partner commerciali. Poiché ogni rendering viene aggiunto all’impronta della risorsa nell’archivio, Adobe consiglia di utilizzare questa funzione in modo giudizioso. Per ridurre la quantità di risorse necessarie per elaborare e archiviare le immagini, puoi generarle in fase di esecuzione anziché come rappresentazioni durante l’acquisizione.

Molti clienti di Sites implementano un servlet immagine che ridimensiona e ritaglia le immagini al momento della richiesta, il che impone un carico aggiuntivo sull’istanza di pubblicazione. Tuttavia, finché queste immagini possono essere memorizzate nella cache, la sfida può essere attenuata.

Un approccio alternativo è quello di utilizzare la tecnologia Dynamic Media Classic per distribuire completamente la manipolazione delle immagini. Inoltre, puoi distribuire Brand Portal che non solo assume le responsabilità di generazione del rendering dal [!DNL Experience Manager] infrastruttura, ma anche l&#39;intero livello di pubblicazione.

#### ImageMagick {#imagemagick}

Se si personalizza il flusso di lavoro Aggiorna risorsa DAM per generare rappresentazioni utilizzando ImageMagick, Adobe consiglia di modificare il file policy.xml in */etc/ImageMagick/*. Per impostazione predefinita, ImageMagick utilizza l&#39;intero spazio su disco disponibile sul volume del sistema operativo e la memoria disponibile. Apporta le seguenti modifiche alla configurazione all’interno della `policymap` sezione di policy.xml per limitare queste risorse.

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

Inoltre, imposta il percorso della cartella temporanea di ImageMagick nel *configure.xml* o impostando la variabile di ambiente `MAGIC_TEMPORARY_PATH`) in una partizione disco con spazio sufficiente e IOPS.

>[!CAUTION]
>
>Una configurazione errata può rendere instabile il server se ImageMagick utilizza tutto lo spazio su disco disponibile. Le modifiche dei criteri necessarie per elaborare file di grandi dimensioni utilizzando ImageMagick possono influire sul [!DNL Experience Manager] prestazioni. Per ulteriori informazioni, consulta [installa e configura ImageMagick](best-practices-for-imagemagick.md).

>[!NOTE]
>
>ImageMagick `policy.xml` e `configure.xml` i file si trovano in `/usr/lib64/ImageMagick-*/config/` anziché `/etc/ImageMagick/`. Vedi [Documentazione di ImageMagick](https://www.imagemagick.org/script/resources.php) per informazioni dettagliate sulle posizioni dei file di configurazione.

Se utilizzi [!DNL Experience Manager] in Adobe Managed Services (AMS), contatta l’Assistenza clienti Adobe se intendi elaborare molti file PSD o PSB di grandi dimensioni. Experience Manager potrebbe non elaborare file PSB ad altissima risoluzione con una risoluzione superiore a 30000x23000 pixel.

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

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

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

### XMP {#xmp-writeback}

XMP writeback aggiorna la risorsa originale ogni volta che i metadati vengono modificati in AEM, il che si traduce in quanto segue:

* La risorsa stessa viene modificata
* Viene creata una versione della risorsa
* Risorsa di aggiornamento DAM eseguita sulla risorsa

I risultati elencati consumano notevoli risorse. Pertanto, l&#39;Adobe raccomanda [disabilitazione XMP Writeback](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html), se non è obbligatorio.

Se è selezionato il flag di esecuzione dei flussi di lavoro, l’importazione di una grande quantità di metadati può comportare un’attività di XMP write-back ad uso intensivo di risorse. Pianifica un&#39;importazione di questo tipo durante l&#39;utilizzo snello del server in modo che le prestazioni per altri utenti non siano influenzate.

## Replica {#replication}

Quando si replicano le risorse in un numero elevato di istanze di pubblicazione, ad esempio in un’implementazione di Sites, Adobe consiglia di utilizzare la replica a catena. In questo caso, l&#39;istanza dell&#39;autore si replica in una singola istanza di pubblicazione che a sua volta si replica alle altre istanze di pubblicazione, liberando l&#39;istanza dell&#39;autore.

### Configurare la replica a catena {#configure-chain-replication}

1. Scegliere l&#39;istanza di pubblicazione da utilizzare per concatenare le replicazioni
1. In quell&#39;istanza di pubblicazione aggiungi agenti di replica che puntano alle altre istanze di pubblicazione
1. Per ciascuno di questi agenti di replica, abilita **[!UICONTROL Al ricevimento]** sulla **[!UICONTROL Triggers]** scheda

>[!NOTE]
>
>Ad Adobe, non è consigliabile attivare automaticamente le risorse. Tuttavia, se necessario, Adobe consiglia di eseguire questo come passaggio finale in un flusso di lavoro, in genere DAM Update Asset.

## Cerca indici {#search-indexes}

Assicurati di implementare i service pack e gli hotfix più recenti relativi alle prestazioni, in quanto spesso includono aggiornamenti agli indici di sistema. Vedi [Suggerimenti per l’ottimizzazione delle prestazioni | 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) per alcune ottimizzazioni dell&#39;indice che possono essere applicate, a seconda della versione di AEM.

Crea indici personalizzati per le query che esegui spesso. Per maggiori dettagli, vedi [metodologia per l’analisi delle query lente](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) e [creazione di indici personalizzati](/help/sites-deploying/queries-and-indexing.md). Per ulteriori informazioni sulle best practice relative a query e indice, consulta [Tecniche consigliate per query e indicizzazione](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Configurazioni dell&#39;indice Lucene {#lucene-index-configurations}

Alcune ottimizzazioni possono essere fatte sulle configurazioni dell&#39;indice Oak che possono aiutare a migliorare [!DNL Experience Manager] Prestazioni delle risorse:

Aggiorna la configurazione LuceneIndexProvider:

1. Passa a /system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. Abilita **[!UICONTROL File di indice CopyOnRead , CopyOnWrite e Prefetch]** nelle versioni precedenti a [!DNL Experience Manager] 6.2. Questi valori sono attivati per impostazione predefinita in [!DNL Experience Manager] 6.2 e versioni successive.

Aggiorna le configurazioni dell&#39;indice per migliorare il tempo di reindicizzazione:

1. Apri CRXDe /crx/de/index.jsp e accedi come utente amministrativo
1. Sfoglia /oak:index/lucene
1. Aggiungi una stringa[] proprietà denominata **[!UICONTROL excludedPaths]** con valori &quot;/var&quot;, &quot;/etc/workflow/instances&quot; e &quot;/etc/replication&quot;
1. Sfoglia /oak:index/damAssetLucene
1. Aggiungi una stringa[] proprietà denominata **[!UICONTROL includedPaths]** con un valore &quot;/content/dam&quot;
1. Salva

(Solo AEM6.1 e 6.2) Aggiorna l&#39;indice ntBaseLucene per migliorare le prestazioni di eliminazione e spostamento delle risorse:

1. Sfoglia per */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Aggiungi due nodi nt:unstructured **[!UICONTROL slingResource]** e **[!UICONTROL damResolvedPath]** sotto */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. Imposta le proprietà seguenti sui nodi (dove le proprietà ordered e propertyIndex sono di tipo *Booleano*:

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

1. Sul nodo /oak:index/ntBaseLucene , imposta la proprietà `reindex=true`
1. Fai clic su **[!UICONTROL Salva tutto]**
1. Monitora il file error.log per vedere quando l&#39;indicizzazione è completata:

   Reindicizzazione completata per gli indici: [/oak:index/ntBaseLucene]

1. Puoi anche vedere che l&#39;indicizzazione è completata aggiornando il nodo /oak:index/ntBaseLucene in CRXDe in quanto la proprietà reindicizzazione tornerebbe a false
1. Una volta completata l&#39;indicizzazione, torna a CRXDe e imposta il **[!UICONTROL type]** su questi due indici

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Fai clic su **[!UICONTROL Salva tutto]**

Disattiva estrazione testo Lucene:

Se gli utenti non devono essere in grado di cercare il contenuto delle risorse, ad esempio ricercando il testo contenuto nei documenti di PDF, puoi migliorare le prestazioni dell’indice disattivando questa funzione.

1. Vai a [!DNL Experience Manager] gestore di pacchetti /crx/packmgr/index.jsp
1. Carica e installa il pacchetto qui sotto

[Ottieni file](assets/disable_indexingbinarytextextraction-10.zip)

### Totale Indovini {#guess-total}

Quando crei query che generano set di risultati di grandi dimensioni, utilizza la variabile `guessTotal` per evitare l&#39;utilizzo di memoria pesante quando vengono eseguiti.

## Problemi noti {#known-issues}

### File di grandi dimensioni {#large-files}

Ci sono due importanti problemi noti relativi ai file di grandi dimensioni in AEM. Quando i file raggiungono dimensioni superiori a 2 GB, la sincronizzazione standby a freddo può trovarsi in una situazione di esaurimento della memoria. In alcuni casi, impedisce l’esecuzione della sincronizzazione in standby. In altri casi, causa l’arresto anomalo dell’istanza primaria. Questo scenario si applica a qualsiasi file in [!DNL Experience Manager] superiore a 2 GB, inclusi i pacchetti di contenuti.

Allo stesso modo, quando i file raggiungono le dimensioni di 2 GB durante l&#39;utilizzo di un datastore S3 condiviso, potrebbe essere necessario un po&#39; di tempo perché il file venga mantenuto completamente dalla cache al filesystem. Di conseguenza, quando si utilizza la replica senza binario, è possibile che i dati binari non siano stati persistenti prima del completamento della replica. Questa situazione può causare problemi, soprattutto se la disponibilità di dati è importante, ad esempio in scenari di scarico.

## Test delle prestazioni {#performance-testing}

Per ogni [!DNL Experience Manager] implementazione, stabilire un regime di test delle prestazioni in grado di identificare e risolvere rapidamente i colli di bottiglia. Ecco alcune aree chiave su cui concentrarsi.

### Test di rete {#network-testing}

Per tutti i problemi di prestazioni della rete da parte del cliente, eseguire le seguenti operazioni:

* Verificare le prestazioni di rete dalla rete del cliente
* Verificare le prestazioni di rete dalla rete Adobe. Per i clienti AMS, collabora con il tuo CSE per eseguire il test dall’interno della rete Adobe.
* Verificare le prestazioni di rete da un altro punto di accesso
* Utilizzando uno strumento di benchmark della rete
* Test contro il dispatcher

### [!DNL Experience Manager] test di istanza {#aem-instance-testing}

Per ridurre al minimo la latenza e ottenere un throughput elevato grazie all&#39;utilizzo efficiente della CPU e alla condivisione del carico, controlla le prestazioni del tuo [!DNL Experience Manager] istanza regolarmente. In particolare:

* Eseguire test di carico contro [!DNL Experience Manager] istanza
* Monitoraggio delle prestazioni di caricamento e risposta dell’interfaccia utente

## [!DNL Experience Manager] Elenco di controllo delle prestazioni delle risorse {#aem-assets-performance-checklist}

* Abilita HTTPS per aggirare qualsiasi sniffer di traffico HTTP aziendale.
* Utilizza una connessione cablata per il caricamento di risorse pesanti.
* Imposta parametri JVM ottimali.
* Configura un archivio dati del sistema di file o un DataStore S3.
* Disattiva la generazione di risorse secondarie. Se è abilitata, AEM flusso di lavoro crea una risorsa separata per ogni pagina di una risorsa multipagina. Ciascuna di queste pagine è una singola risorsa che consuma ulteriore spazio su disco, richiede il controllo delle versioni e ulteriore elaborazione del flusso di lavoro. Se non richiedi pagine separate, disattiva la generazione di risorse secondarie e le attività di estrazione della pagina.
* Abilita flussi di lavoro transitori.
* Ottimizza le code del flusso di lavoro Granite per limitare i processi simultanei.
* Configura ImageMagick per limitare il consumo di risorse.
* Rimuovi i passaggi superflui dal flusso di lavoro Risorsa di aggiornamento DAM .
* Configura la pulizia del flusso di lavoro e delle versioni.
* Ottimizza la configurazione dell&#39;indice Lucene.
* Ottimizza gli indici con i service pack e gli hotfix più recenti. Consulta Adobe Customer Support per eventuali ottimizzazioni aggiuntive dell&#39;indice disponibili.
* Utilizzo `guessTotal` per ottimizzare le prestazioni della query.
* Se si configura [!DNL Experience Manager] per rilevare i tipi di file dal contenuto dei file (configurando [!UICONTROL Servizio Day CQ DAM Mime Type] in [!UICONTROL [!DNL Experience Manager] Console web]), carica molti file in blocco nelle ore non di picco, in quanto l&#39;operazione richiede molte risorse.
