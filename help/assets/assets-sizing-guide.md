---
title: Guida alla dimensionamento delle risorse
description: 'Procedure ottimali per determinare metriche efficienti per la stima dell’infrastruttura e delle risorse necessarie per la distribuzione di Risorse AEM. '
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
translation-type: tm+mt
source-git-commit: 6aec5927c00f70ce2c044ffd56cabbf68a81071a

---


# Guida alla dimensionamento delle risorse {#assets-sizing-guide}

Quando si esegue il ridimensionamento dell’ambiente per un’implementazione di Risorse Adobe Experience Manager (AEM), è importante assicurarsi che siano disponibili risorse sufficienti in termini di disco, CPU, memoria, IO e throughput di rete. Per ridimensionare molte di queste risorse è necessario conoscere il numero di risorse caricate nel sistema. Se una metrica migliore non è disponibile, potete dividere la dimensione della libreria esistente per l’età della libreria per individuare la frequenza con cui vengono create le risorse.

## Disco {#disk}

### DataStore {#datastore}

Quando si ridimensiona lo spazio su disco necessario per l’implementazione di Risorse, si commette un errore comune: basare i calcoli sulla dimensione delle immagini non elaborate da assimilare nel sistema. Per impostazione predefinita, AEM crea tre rappresentazioni oltre all’immagine originale da usare per il rendering degli elementi dell’interfaccia utente di AEM. Nelle implementazioni precedenti, queste rappresentazioni erano state osservate in modo da assumere il doppio delle dimensioni delle risorse assimilate.

La maggior parte degli utenti definisce rappresentazioni personalizzate oltre alle rappresentazioni pronte all&#39;uso. Oltre alle rappresentazioni, Risorse AEM consente di estrarre risorse secondarie da tipi di file comuni, come InDesign e Illustrator.

Infine, le funzionalità di controllo delle versioni di AEM memorizzano duplicati delle risorse nella cronologia delle versioni. Potete configurare le versioni da eliminare spesso. Tuttavia, molti utenti scelgono di mantenere le versioni nel sistema per un lungo periodo di tempo, che consuma ulteriore spazio di archiviazione.

Considerati questi fattori, è necessaria una metodologia per calcolare uno spazio di archiviazione accettabile e accurato per memorizzare le risorse degli utenti.

1. Consente di determinare la dimensione e il numero di risorse che verranno caricate nel sistema.
1. Ottenete un esempio rappresentativo delle risorse da caricare in AEM. Ad esempio, se intendete caricare nel sistema file PSD, JPG, AI e PDF, è necessario disporre di più immagini di esempio per ciascun formato di file. Inoltre, questi esempi devono essere rappresentativi delle diverse dimensioni di file e complessità delle immagini.
1. Definire le rappresentazioni da utilizzare.
1. Create le rappresentazioni in AEM utilizzando ImageMagick o le applicazioni Creative Cloud di Adobe. Oltre alle rappresentazioni specificate dagli utenti, create rappresentazioni pronte all&#39;uso. Per gli utenti che implementano Scene7, potete usare il binario IC per generare le rappresentazioni PTIFF da memorizzare in AEM.
1. Se prevedete di utilizzare le risorse secondarie, generatele per i tipi di file appropriati. Consultate la documentazione online su come generare pagine di risorse secondarie da file InDesign o file PNG/PDF da livelli Illustrator.
1. Confrontate le dimensioni delle immagini di output, delle rappresentazioni e delle risorse secondarie con le immagini originali. Consente di generare un fattore di crescita previsto quando il sistema viene caricato. Ad esempio, se generate rappresentazioni e risorse secondarie con una dimensione combinata di 3 GB dopo aver elaborato 1 GB di risorse, il fattore di crescita della rappresentazione è 3.
1. Determinate il tempo massimo per il quale le versioni delle risorse devono essere mantenute nel sistema.
1. Determinate con quale frequenza vengono modificate le risorse esistenti nel sistema. Se AEM viene utilizzato come hub di collaborazione nei flussi di lavoro creativi, la quantità di modifiche è elevata. Se nel sistema vengono caricate solo le risorse finite, questo numero è molto inferiore.
1. Determinate quante risorse vengono caricate nel sistema ogni mese. Se non si è certi, verificare il numero di risorse attualmente disponibili e dividere il numero per l&#39;età della risorsa più vecchia per calcolare un numero approssimativo.

I passaggi da 1 a 9 consentono di determinare quanto segue:

* Dimensione non elaborata delle risorse da caricare
* Numero di risorse da caricare
* Fattore di crescita della rappresentazione
* Numero di modifiche apportate alle risorse al mese
* Numero di mesi per mantenere le versioni delle risorse
* Numero di nuove risorse caricate ogni mese
* Anni di crescita per allocare spazio per

Potete specificare questi numeri nel foglio di calcolo Ridimensionamento rete per determinare lo spazio totale richiesto per il datastore. È anche uno strumento utile per determinare l’impatto della manutenzione delle versioni delle risorse o della modifica delle risorse in AEM sulla crescita del disco.

I dati di esempio inseriti nello strumento dimostrano l&#39;importanza di eseguire i passaggi indicati. Se si modifica la dimensione del datastore in base esclusivamente alle immagini non elaborate caricate (1 TB), è possibile che la dimensione del repository sia stata sottostimata di 15 volte.

[Ottieni file](assets/disk_sizing_tool.xlsx)

### Database condivisi {#shared-datastores}

Per i grandi archivi dati, puoi implementare un archivio dati condiviso tramite un archivio dati condiviso su un&#39;unità collegata di rete o tramite un archivio dati S3. In questo caso, non è necessario mantenere una copia dei file binari. Inoltre, un datastore condiviso facilita la replica senza binario e consente di ridurre la larghezza di banda utilizzata per replicare le risorse in ambienti di pubblicazione o per scaricare le istanze.

#### Use Cases {#use-cases}

Il datastore può essere condiviso tra un’istanza di creazione primaria e standby per ridurre al minimo il tempo necessario per aggiornare l’istanza standby con le modifiche apportate nell’istanza principale. Adobe consiglia di condividere il datastore tra un’istanza di creazione principale e di scaricare le istanze di autori per ridurre i costi comuni durante lo scaricamento del flusso di lavoro. Potete anche condividere il datastore tra le istanze di creazione e pubblicazione per ridurre il traffico durante la replica.

#### Svantaggi {#drawbacks}

A causa di alcune insidie, la condivisione di un datastore non è consigliata in tutti i casi.

#### Singolo punto di errore {#single-point-of-failure}

Avere un datastore condiviso, introduce un singolo punto di fallimento in un&#39;infrastruttura. Considerate uno scenario in cui nel sistema sono presenti una o due istanze di creazione e pubblicazione, ciascuna con un datastore personalizzato. Se uno di questi si arresta in modo anomalo, gli altri due possono continuare a funzionare. Tuttavia, se il datastore è condiviso, un singolo errore del disco può abbattere l&#39;intera infrastruttura. Di conseguenza, è necessario mantenere un backup dell&#39;archivio dati condiviso da cui è possibile ripristinare rapidamente l&#39;archivio dati.

È preferibile distribuire il servizio AWS S3 per gli archivi dati condivisi, in quanto riduce notevolmente la probabilità di errore rispetto alle architetture disco normali.

#### Maggiore complessità {#increased-complexity}

I datastores condivisi aumentano anche la complessità delle operazioni, come il processo di raccolta dei rifiuti. Normalmente, è possibile avviare la raccolta dei rifiuti per un archivio dati standalone con un solo clic. Tuttavia, gli archivi di dati condivisi richiedono operazioni di sweep con contrassegno per ogni membro che utilizza l&#39;archivio dati, oltre a eseguire la raccolta effettiva su un singolo nodo.

Per le operazioni AWS, l&#39;implementazione di un&#39;unica posizione centrale (tramite S3), invece di creare un array RAID di volumi EBS, può compensare in modo significativo la complessità e i rischi operativi del sistema.

#### Preoccupazioni sulle prestazioni {#performance-concerns}

Un datastore condiviso richiede che i file binari siano memorizzati su un&#39;unità montata in rete condivisa tra tutte le istanze. Poiché tali file binari sono accessibili attraverso una rete, le prestazioni del sistema ne risentono negativamente. È possibile attenuare parzialmente l&#39;impatto utilizzando una connessione di rete rapida a un array veloce di dischi. Tuttavia, questa è una proposta costosa. Nel caso delle operazioni AWS, tutti i dischi sono remoti e richiedono connettività di rete. I volumi effimeri perdono i dati all&#39;avvio o all&#39;arresto dell&#39;istanza.

#### Latenza {#latency}

La latenza nelle implementazioni S3 è introdotta dai thread di scrittura in background. Le procedure di backup devono tenere conto di tale latenza e di eventuali procedure di scarico. La risorsa S3 potrebbe non essere presente in S3 all&#39;avvio di un processo di scarico. Inoltre, gli indici Lucene possono rimanere incompleti durante la creazione di un backup. Si applica a qualsiasi file sensibile all&#39;ora scritto nel datastore S3 e a cui si accede da un&#39;altra istanza.

### Archivio nodi/Archivio documenti {#node-store-document-store}

È difficile ottenere cifre di ridimensionamento precise per un NodeStore o un DocumentStore a causa delle risorse utilizzate da:

* Metadati risorsa
* Versioni delle risorse
* Registri di controllo
* Flussi di lavoro archiviati e attivi

Poiché i file binari vengono memorizzati nel datastore, ogni file binario occupa spazio. La maggior parte dei repository ha dimensioni inferiori a 100 GB. Tuttavia, potrebbero essere presenti archivi di dimensioni maggiori fino a 1 TB. Inoltre, per eseguire la compattazione offline, è necessario spazio libero sufficiente sul volume per riscrivere l&#39;archivio compattato insieme alla versione pre-compattata. Una buona regola è ridimensionare il disco a 1,5 volte la dimensione prevista per il repository.

Per l&#39;archivio, utilizzare SSD o dischi con un livello IOPS superiore a 3000. Per eliminare le possibilità di IOPS di introdurre colli di bottiglia delle prestazioni, monitorare i livelli di attesa IO CPU per i primi segnali di problemi.

[Ottieni file](assets/aem_environment_sizingtool.xlsx)

## Rete {#network}

Risorse AEM offre una serie di casi d’uso che rendono le prestazioni di rete più importanti rispetto a molti dei nostri progetti AEM. Un cliente può disporre di un server veloce, ma se la connessione di rete non è sufficientemente grande per supportare il carico degli utenti che caricano e scaricano risorse dal sistema, la connessione continuerà a risultare lenta. Esiste una buona metodologia per determinare il punto di interruzione nella connessione di rete di un utente ad AEM in base a considerazioni di Risorse [AEM per l’esperienza utente, il ridimensionamento delle istanze, la valutazione del flusso di lavoro e la topologia](assets-network-considerations.md)di rete.

## WebDAV {#webdav}

Se aggiungete l&#39;app desktop AEM al mix, i problemi di rete si aggravano a causa delle inefficienze nel protocollo WebDAV.

Per illustrare queste inefficienze, Adobe ha testato le prestazioni del sistema utilizzando WebDAV su OS X. Un file InDesign da 3,5 MB è stato aperto, modificato e le modifiche sono state salvate. Sono state formulate le seguenti osservazioni:

* Totale di circa 100 richieste HTTP generate per completare l&#39;operazione
* Il file è stato caricato quattro volte tramite HTTP
* Il file è stato scaricato una volta via HTTP
* L&#39;intera operazione ha richiesto 42 secondi per essere completata
* Sono stati trasferiti complessivamente 18 MB di dati

Analizzando il tempo di risparmio medio per i file su WebDAV, è stato rilevato che le prestazioni aumentano notevolmente man mano che la larghezza di banda aumenta fino al livello di 5-10 Mbps. Adobe consiglia pertanto a ogni utente che accede simultaneamente al sistema di avere almeno 10 Mbps di velocità di caricamento e 5-10 Mbps di larghezza di banda.

Per ulteriori informazioni, consultate [Risoluzione di problemi relativi all&#39;app](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html)desktop AEM.

## Limitazioni  {#limitations}

Quando si esegue il ridimensionamento di un&#39;implementazione, è importante tenere presenti i limiti del sistema. Se l’implementazione proposta supera questi limiti, utilizza strategie creative, come il partizionamento delle risorse tra più implementazioni di Assets.

La dimensione del file non è l&#39;unico fattore che contribuisce a problemi di memoria insufficiente (OOM, Out of Memory). Dipende anche dalle dimensioni dell’immagine. Per evitare problemi di OOM, all’avvio di AEM specificate una dimensione di heap maggiore.

Inoltre, potete modificare la proprietà della dimensione della soglia del `com.day.cq.dam.commons.handler.StandardImageHandler` componente in Configuration Manager per utilizzare un file temporaneo intermedio maggiore di zero.

## Numero massimo di risorse {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

Il limite al numero di file che possono esistere in un datastore può essere di 2,1 miliardi a causa delle limitazioni del filesystem. È probabile che l&#39;archivio rilevi problemi a causa di un numero elevato di nodi molto lungo prima del raggiungimento del limite dell&#39;archivio dati.

Se le rappresentazioni non vengono generate correttamente, utilizzate la libreria Camera Raw. Tuttavia, in questo caso, il lato più lungo dell’immagine non deve essere maggiore di 65000 pixel. Inoltre, l&#39;immagine non deve contenere più di 512 MP (512 &amp;ast; 1024 &amp;ast; 1024 pixel)&#39;. *La dimensione della risorsa è irrilevante*.

È difficile stimare con precisione la dimensione del file TIFF supportato out-of-the-box (OOTB) con un heap specifico per AEM, perché fattori aggiuntivi, come l’elaborazione dell’influenza delle dimensioni dei pixel. È possibile che AEM sia in grado di elaborare un file di dimensioni pari a 255 MB di OOTB, ma non sia in grado di elaborare un file di dimensioni pari a 18 MB, poiché quest’ultimo comprende un numero di pixel insolitamente più elevato rispetto al primo.

## Dimensione delle risorse {#size-of-assets}

Per impostazione predefinita, AEM consente di caricare risorse di dimensioni file fino a 2 GB. Per caricare risorse molto grandi in AEM, consultate [Configurazione per caricare risorse](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb)molto grandi.
