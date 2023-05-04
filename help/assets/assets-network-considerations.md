---
title: Considerazioni sulla rete delle risorse
description: Esamina le considerazioni sulla rete durante la progettazione di un [!DNL Experience Manager] Distribuzione di risorse.
contentOwner: AG
feature: Developer Tools
role: Architect,Admin
exl-id: f8f9d86f-a5e3-46ac-8d96-c2e44eac9c93
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 1%

---

# Considerazioni sulla rete Assets {#assets-network-considerations}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La comprensione della rete è importante quanto la comprensione di Adobe Experience Manager Assets. La rete può influenzare le esperienze di caricamento, download e utente. Il diagramma della topologia di rete consente di identificare i punti di interruzione e le aree sottoottimizzate della rete che è necessario correggere per migliorare le prestazioni di rete e l&#39;esperienza utente.

Accertati di includere quanto segue nel diagramma di rete:

* Connettività dal dispositivo client (ad esempio computer, dispositivi mobili e tablet) alla rete
* Topologia della rete aziendale
* Collegamento a Internet dalla rete aziendale e [!DNL Experience Manager] ambiente
* Topologia del [!DNL Experience Manager] ambiente
* Definire consumatori simultanei del [!DNL Experience Manager] interfaccia di rete
* Flussi di lavoro definiti [!DNL Experience Manager] istanza

## Connettività dal dispositivo client alla rete aziendale {#connectivity-from-the-client-device-to-the-corporate-network}

Per iniziare, è necessario creare un diagramma della connettività tra i singoli dispositivi client e la rete aziendale. In questa fase, identifica le risorse condivise, come le connessioni WiFi, in cui più utenti accedono allo stesso punto o switch ethernet per caricare e scaricare le risorse.

![chlimage_1-353](assets/chlimage_1-353.png)

I dispositivi client si collegano alla rete aziendale in vari modi, come WiFi condiviso, Ethernet a uno switch condiviso e VPN. L’identificazione e la comprensione dei punti di interruzione di questa rete è importante per la pianificazione delle risorse e per la modifica della rete.

Nella parte superiore sinistra del diagramma, tre dispositivi sono rappresentati come condivisione di un punto di accesso WiFi a 48 Mbps. Se tutti i dispositivi vengono caricati contemporaneamente, la larghezza di banda della rete WiFi viene condivisa tra i dispositivi. Rispetto al sistema nel suo insieme, un utente può incontrare un diverso punto di blocco per i tre client su questo canale diviso.

È difficile misurare la velocità effettiva di una rete WiFi perché un dispositivo lento può influenzare altri clienti sul punto di accesso. Se prevedi di utilizzare WiFi per le interazioni delle risorse, esegui un test di velocità da più client simultaneamente per valutare il throughput.

Nella parte in basso a sinistra del diagramma sono rappresentati due dispositivi collegati alla rete aziendale attraverso canali indipendenti. Ogni dispositivo può quindi usufruire di una velocità minima di 10 Mbps e 100 Mbps.

Il computer visualizzato a destra ha un limite a monte della rete aziendale su una VPN con una velocità di 1 Mbps. L&#39;esperienza utente per la connessione a 1 Mbps è molto diversa dall&#39;esperienza utente sulla connessione a 1 Gb/s. A seconda delle dimensioni delle risorse con cui gli utenti interagiscono, il loro uplink VPN potrebbe essere inadeguato per l’attività.

## Topologia della rete aziendale {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Il diagramma mostra velocità di uplink superiori all&#39;interno della rete aziendale rispetto a quelle generalmente utilizzate. Questi tubi sono risorse condivise. Se si prevede che lo switch condiviso gestisca 50 client, potrebbe essere un punto di blocco. Nel diagramma iniziale, solo due computer condividono la connessione specifica.

## Collegamento a Internet dalla rete aziendale e [!DNL Experience Manager] ambiente {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

È importante considerare fattori sconosciuti su Internet e la connessione VPC perché la larghezza di banda su Internet può essere compromessa a causa del picco di carico o di interruzioni del provider su larga scala. In generale, la connettività Internet è affidabile. Tuttavia, a volte può introdurre dei punti di ostinazione.

Dall&#39;uplink da una rete aziendale a Internet, possono esserci altri servizi che utilizzano la larghezza di banda. È importante comprendere la quantità di larghezza di banda che può essere dedicata o prioritaria per [!DNL Assets]. Ad esempio, se un collegamento da 1 Gb/s è già utilizzato all&#39;80%, è possibile allocare solo un massimo del 20% della larghezza di banda per [!DNL Experience Manager] risorse.

I firewall e i proxy aziendali possono inoltre modellare la larghezza di banda in molti modi diversi. Questo tipo di dispositivo può dare priorità alla larghezza di banda utilizzando la qualità del servizio, i limiti di larghezza di banda per utente o i limiti di bitrate per host. Si tratta di punti di interruzione importanti da esaminare in quanto possono avere un impatto significativo sull’esperienza utente di Assets.

In questo esempio, l&#39;azienda dispone di un uplink a 10 Gb/s. Deve essere sufficientemente grande per diversi client. Inoltre, il firewall impone un limite di velocità host di 10 Mbps. Questa limitazione può potenzialmente limitare il traffico a un singolo host a 10 Mbps, anche se l&#39;uplink a Internet è a 10 Gbps.

Questo è il più piccolo punto di blocco orientato al cliente. Tuttavia, è possibile eseguire valutazioni per una modifica o per un elenco Consentiti con il gruppo di operazioni di rete responsabile di questo firewall.

Dai diagrammi di esempio si può concludere che sei dispositivi condividono un canale concettuale a 10 Mbps. A seconda delle dimensioni delle risorse utilizzate, ciò potrebbe risultare inadeguato per soddisfare le aspettative degli utenti.

## Topologia del [!DNL Experience Manager] ambiente {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

Progettazione della topologia [!DNL Experience Manager] ambiente richiede una conoscenza dettagliata della configurazione del sistema e del modo in cui la rete viene connessa all&#39;interno dell&#39;ambiente utente.

Lo scenario di esempio include una farm di pubblicazione con cinque server, un archivio binario S3 e un file multimediale dinamico configurati.

Il dispatcher condivide la sua connessione a 100 Mbps con due entità, il mondo esterno e il [!DNL Experience Manager] istanza. Per le operazioni di caricamento e download simultanee, è necessario dividere questo numero per due. L&#39;archiviazione esterna collegata utilizza una connessione separata.

La [!DNL Experience Manager] L&#39;istanza condivide la propria connessione a 1 Gb/s con più servizi. Dal punto di vista della topologia di rete, equivale a condividere un singolo canale con servizi diversi.

Verifica della rete dal dispositivo client al [!DNL Experience Manager] ad esempio, il punto di blocco più piccolo sembra essere la valvola a 10 Mbit del firewall aziendale. Puoi utilizzare questi valori nel calcolatore delle dimensioni nel [Guida al dimensionamento delle risorse](assets-sizing-guide.md) per determinare l’esperienza utente.

## Flussi di lavoro definiti [!DNL Experience Manager] istanza {#defined-workflows-of-the-aem-instance}

Quando si considerano le prestazioni di rete, può essere importante considerare i flussi di lavoro e la pubblicazione che si verificheranno nel sistema. Inoltre, le richieste S3 o altro storage collegato di rete che si utilizzano e I/O richiedono una larghezza di banda di rete. Pertanto, anche in una rete completamente ottimizzata, le prestazioni possono essere limitate dall&#39;I/O del disco.

Per semplificare i processi relativi all’inserimento delle risorse (in particolare durante il caricamento di un numero elevato di risorse), esplora i flussi di lavoro delle risorse e ne scopri di più sulla loro configurazione.

Durante la valutazione della topologia del flusso di lavoro interno, è necessario analizzare quanto segue:

* Procedure per la scrittura di una risorsa
* Flussi di lavoro/eventi che si attivano quando la risorsa/i metadati vengono modificati
* Procedure per la lettura di una risorsa

Di seguito sono riportati alcuni elementi da considerare:

* Metadati XMP letti/writeback
* Attivazione e replica automatiche
* Filigrana
* Acquisizione di risorse secondarie/estrazione pagina
* Sovrapposizione dei flussi di lavoro.

Ecco un esempio di cliente per la definizione di un flusso di lavoro delle risorse.

![chlimage_1-357](assets/chlimage_1-357.png)
