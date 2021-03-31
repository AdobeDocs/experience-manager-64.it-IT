---
title: Guida al dimensionamento di Assets
description: 'Best practice per determinare metriche efficienti per la stima dell’infrastruttura e delle risorse necessarie per la distribuzione di AEM Assets. '
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
feature: Gestione risorse
role: Architetto,Amministratore
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1862'
ht-degree: 0%

---


# Guida al dimensionamento di Assets {#assets-sizing-guide}

Quando si ridimensiona l’ambiente per un’implementazione di Adobe Experience Manager (AEM) Assets, è importante assicurarsi che siano disponibili risorse sufficienti in termini di disco, CPU, memoria, IO e throughput di rete. Il dimensionamento di molte di queste risorse richiede una comprensione del numero di risorse caricate nel sistema. Se una metrica migliore non è disponibile, puoi dividere la dimensione della libreria esistente per l’età della libreria per trovare la velocità con cui vengono create le risorse.

## Disco {#disk}

### DataStore {#datastore}

Un errore comune durante il dimensionamento dello spazio su disco necessario per un’implementazione di Assets consiste nel basare i calcoli sulle dimensioni delle immagini non elaborate da acquisire nel sistema. Per impostazione predefinita, AEM crea tre rappresentazioni oltre all’immagine originale da utilizzare nel rendering degli elementi dell’interfaccia utente AEM. Nelle implementazioni precedenti, queste rappresentazioni sono state osservate per assumere il doppio delle dimensioni delle risorse che vengono acquisite.

La maggior parte degli utenti definisce rappresentazioni personalizzate oltre alle rappresentazioni predefinite. Oltre alle rappresentazioni, AEM Assets consente di estrarre risorse secondarie da tipi di file comuni, come InDesign e Illustrator.

Infine, le funzionalità di controllo delle versioni di AEM memorizzano duplicati delle risorse nella cronologia delle versioni. Puoi configurare le versioni da eliminare spesso. Tuttavia, molti utenti scelgono di mantenere le versioni nel sistema per un lungo periodo di tempo, che consuma ulteriore spazio di archiviazione.

Considerati questi fattori, è necessaria una metodologia per calcolare uno spazio di archiviazione accettabile e accurato per archiviare le risorse degli utenti.

1. Determina le dimensioni e il numero di risorse che verranno caricate nel sistema.
1. Ottieni un esempio rappresentativo delle risorse da caricare in AEM. Ad esempio, se intendi caricare nel sistema file PSD, JPG, AI e PDF, è necessario disporre di più immagini di esempio di ciascun formato di file. Inoltre, questi campioni devono essere rappresentativi delle diverse dimensioni e complessità dei file delle immagini.
1. Definisci i rendering da utilizzare.
1. Crea le rappresentazioni in AEM utilizzando le applicazioni ImageMagick o Adobe Creative Cloud. Oltre alle rappresentazioni specificate dagli utenti, crea rappresentazioni predefinite. Per gli utenti che implementano Dynamic Media Classic, puoi utilizzare il binario IC per generare le rappresentazioni PTIFF da memorizzare in AEM.
1. Se prevedi di utilizzare le risorse secondarie, generale per i tipi di file appropriati. Consulta la documentazione online su come generare pagine di risorse secondarie da file InDesign o file PNG/PDF dai livelli Illustrator.
1. Confronta le dimensioni delle immagini, delle rappresentazioni e delle risorse secondarie di output con le immagini originali. Consente di generare un fattore di crescita previsto al caricamento del sistema. Ad esempio, se generi rappresentazioni e risorse secondarie con una dimensione combinata di 3 GB dopo aver elaborato 1 GB di risorse, il fattore di crescita del rendering è 3.
1. Determina il tempo massimo per il quale le versioni delle risorse devono essere mantenute nel sistema.
1. Determina la frequenza con cui le risorse esistenti vengono modificate nel sistema. Se AEM viene utilizzato come hub di collaborazione nei flussi di lavoro creativi, la quantità di modifiche è elevata. Se nel sistema vengono caricate solo le risorse completate, questo numero è molto inferiore.
1. Determina quante risorse vengono caricate ogni mese nel sistema. Se non sei sicuro, verifica il numero di risorse attualmente disponibili e dividi il numero per l’età della risorsa più vecchia per calcolare un numero approssimativo.

L&#39;esecuzione dei passaggi da 1 a 9 consente di determinare quanto segue:

* Dimensioni non elaborate delle risorse da caricare
* Numero di risorse da caricare
* Fattore di crescita della resa
* Numero di modifiche apportate alle risorse al mese
* Numero di mesi per la manutenzione delle versioni delle risorse
* Numero di nuove risorse caricate ogni mese
* Anni di crescita per assegnare spazio

È possibile specificare questi numeri nel foglio di calcolo Ridimensionamento di rete per determinare lo spazio totale necessario per l’archivio dati. È anche uno strumento utile per determinare l’impatto della manutenzione delle versioni delle risorse o della modifica delle risorse in AEM sulla crescita del disco.

I dati di esempio compilati nello strumento mostrano l’importanza di eseguire i passaggi indicati. Se si ridimensiona il datastore in base solo alle immagini non elaborate caricate (1 TB), è possibile che la dimensione del repository sia stata sottostimata di un fattore di 15.

[Ottieni file](assets/disk_sizing_tool.xlsx)

### Datastore condiviso {#shared-datastores}

Per i datastore di grandi dimensioni, è possibile implementare un datastore condiviso tramite un datastore di file condiviso su un&#39;unità di rete collegata o tramite un datastore S3. In questo caso, non è necessario mantenere una copia dei binari nelle singole istanze. Inoltre, un datastore condiviso facilita la replica senza binario e aiuta a ridurre la larghezza di banda utilizzata per replicare le risorse in ambienti di pubblicazione o le istanze di offload.

#### Casi d&#39;uso {#use-cases}

Il datastore può essere condiviso tra un’istanza di authoring primaria e standby per ridurre al minimo il tempo necessario per aggiornare l’istanza di standby con le modifiche apportate nell’istanza primaria. Adobe consiglia di condividere il datastore tra un’istanza dell’autore principale e di scaricare le istanze dell’autore per ridurre i costi comuni nello scaricamento del flusso di lavoro. Puoi anche condividere l’archivio dati tra le istanze di authoring e pubblicazione per ridurre al minimo il traffico durante la replica.

#### Drawback {#drawbacks}

A causa di alcune insidie, la condivisione di un datastore non è consigliata in tutti i casi.

#### Singolo punto di errore {#single-point-of-failure}

Avere un datastore condiviso, introduce un singolo punto di errore in un&#39;infrastruttura. Considera uno scenario in cui il tuo sistema dispone di un autore e due istanze di pubblicazione, ciascuna con il proprio datastore. Se uno di questi si blocca, gli altri due possono ancora continuare a funzionare. Tuttavia, se il datastore viene condiviso, un singolo errore del disco può abbattere l&#39;intera infrastruttura. Di conseguenza, assicurati di mantenere un backup dell&#39;archivio dati condiviso da cui puoi ripristinare rapidamente l&#39;archivio dati.

È preferibile implementare il servizio AWS S3 per i datastore condivisi, in quanto riduce in modo significativo la probabilità di errore rispetto alle architetture normali del disco.

#### Maggiore complessità {#increased-complexity}

I datastore condivisi aumentano anche la complessità delle operazioni, come la raccolta degli oggetti inattivi. Normalmente, la raccolta degli oggetti inattivi per un datastore indipendente può essere avviata con un solo clic. Tuttavia, i datastore condivisi richiedono operazioni di sweep di contrassegno su ogni membro che utilizza il datastore, oltre a eseguire la raccolta effettiva su un singolo nodo.

Per le operazioni AWS, l&#39;implementazione di una singola posizione centrale (tramite S3), invece di costruire un array RAID di volumi EBS, può compensare in modo significativo la complessità e i rischi operativi del sistema.

#### Problemi di prestazioni {#performance-concerns}

Un datastore condiviso richiede che i binari siano memorizzati su un&#39;unità montata in rete condivisa tra tutte le istanze. Poiché questi binari sono accessibili tramite una rete, le prestazioni del sistema sono influenzate negativamente. È possibile attenuare parzialmente l&#39;impatto utilizzando una connessione di rete rapida a un array veloce di dischi. Tuttavia, questa è una proposta costosa. Nel caso di operazioni AWS, tutti i dischi sono remoti e richiedono connettività di rete. I volumi effimeri perdono i dati quando l&#39;istanza viene avviata o arrestata.

#### Latenza {#latency}

La latenza nelle implementazioni S3 viene introdotta dai thread di scrittura in background. Le procedure di backup devono tenere conto di tale latenza e di eventuali procedure di scarico. La risorsa S3 potrebbe non essere presente in S3 all’avvio di un processo di scarico. Inoltre, gli indici Lucene possono rimanere incompleti durante la creazione di un backup. Si applica a qualsiasi file sensibile al tempo scritto nel datastore S3 e a cui si accede da un&#39;altra istanza.

### Archivio nodi/Archiviazione documenti {#node-store-document-store}

È difficile ottenere cifre precise di dimensionamento per un NodeStore o DocumentStore a causa delle risorse utilizzate da quanto segue:

* Metadati delle risorse
* Versioni delle risorse
* Registri di controllo
* Flussi di lavoro archiviati e attivi

Poiché i binari vengono memorizzati nel datastore, ogni binario occupa un po&#39; di spazio. La maggior parte degli archivi ha dimensioni inferiori a 100 GB. Tuttavia, le dimensioni degli archivi potrebbero essere maggiori fino a 1 TB. Inoltre, per eseguire la compattazione offline, è necessario abbastanza spazio libero sul volume per riscrivere l&#39;archivio compattato insieme alla versione pre-compattata. Una buona regola è quella di ridimensionare il disco a 1,5 volte la dimensione prevista per l&#39;archivio.

Per l&#39;archivio, utilizzare SSD o dischi con un livello IOPS superiore a 3000. Per eliminare le possibilità che IOPS introduca i colli di bottiglia delle prestazioni, monitorare i livelli di attesa della CPU I/O per i primi segnali di problemi.

[Ottieni file](assets/aem_environment_sizingtool.xlsx)

## Rete {#network}

AEM Assets ha una serie di casi d’uso che rendono le prestazioni di rete più importanti rispetto a molti dei nostri progetti AEM. Un cliente può disporre di un server veloce, ma se la connessione di rete non è abbastanza grande per supportare il carico degli utenti che caricano e scaricano risorse dal sistema, allora apparirà comunque lento. Esiste una buona metodologia per determinare il punto di interruzione nella connessione di rete di un utente a AEM a [AEM Considerazioni sulle risorse per l&#39;esperienza utente, il dimensionamento dell&#39;istanza, la valutazione del flusso di lavoro e la topologia di rete](assets-network-considerations.md).

## WebDAV {#webdav}

Se aggiungi l&#39;app desktop AEM al mix, i problemi di rete diventano più gravi a causa di inefficienze nel protocollo WebDAV.

Per illustrare queste inefficienze, Adobe ha testato le prestazioni del sistema utilizzando WebDAV su OS X. È stato aperto, modificato un file InDesign da 3,5 MB e le modifiche sono state salvate. Sono state formulate le seguenti osservazioni:

* Totale di circa 100 richieste HTTP generate per completare l&#39;operazione
* Il file è stato caricato quattro volte tramite HTTP
* Il file è stato scaricato una volta via HTTP
* L&#39;intera operazione ha richiesto 42 secondi di completamento
* È stato trasferito un totale di 18 MB di dati

Analizzando il tempo medio di salvataggio dei file su WebDAV, si è riscontrato che le prestazioni aumentano notevolmente con l&#39;aumento della larghezza di banda fino al livello di 5-10 Mbps. Pertanto, l&#39;Adobe consiglia a ogni utente che accede simultaneamente al sistema di avere almeno 10 Mbps di velocità di caricamento e 5-10 Mbps di larghezza di banda.

Per ulteriori informazioni, consulta [Risoluzione dei problemi AEM&#39;app desktop](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html).

## Limitazioni  {#limitations}

Quando si dimensiona un&#39;implementazione, è importante tenere presenti le limitazioni di sistema. Se l’implementazione proposta supera tali limiti, utilizza strategie creative, ad esempio la suddivisione delle risorse tra più implementazioni di Assets.

La dimensione del file non è l’unico fattore che contribuisce a problemi di memoria esaurita (OOM). Dipende anche dalle dimensioni dell&#39;immagine. È possibile evitare problemi di OOM fornendo una dimensione di heap più alta quando si inizia AEM.

Inoltre, è possibile modificare la proprietà Dimensione soglia del componente `com.day.cq.dam.commons.handler.StandardImageHandler` in Configuration Manager per utilizzare un file temporaneo intermedio maggiore di zero.

## Numero massimo di risorse {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

Il limite al numero di file che possono esistere in un datastore può essere di 2,1 miliardi a causa di limitazioni del filesystem. È probabile che l’archivio incontri problemi a causa di un numero elevato di nodi molto lungo prima di raggiungere il limite del datastore.

Se le rappresentazioni non sono generate correttamente, utilizza la libreria Camera Raw. Tuttavia, in questo caso, il lato più lungo dell&#39;immagine non deve essere maggiore di 65000 pixel. Inoltre, l&#39;immagine non deve contenere più di 512 MP (512 &amp;ast; 1024 &amp;ast; 1024 pixel)&#39;. *La dimensione della risorsa è irrilevante*.

È difficile stimare con precisione la dimensione del file TIFF supportato come OOTB (out-of-the-box) con un heap specifico per AEM perché fattori aggiuntivi, come l’elaborazione dell’influenza della dimensione dei pixel. È possibile che AEM elaborare un file di dimensioni di 255 MB OOTB, ma non può elaborare un file di dimensioni di 18 MB perché quest&#39;ultimo comprende un numero di pixel insolitamente più alto rispetto al primo.

## Dimensione delle risorse {#size-of-assets}

Per impostazione predefinita, AEM consente di caricare risorse di dimensioni file fino a 2 GB. Per caricare risorse di grandi dimensioni in AEM, consulta [Configurazione per caricare risorse di grandi dimensioni](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb).
