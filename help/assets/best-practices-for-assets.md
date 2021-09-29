---
title: Best practice per gestire le risorse tramite AEM
description: Identifica e rispetta le best practice che migliorano la stabilità e le prestazioni del sistema sotto carico, a seconda della distribuzione  [!DNL Experience Manager] Assets e delle funzionalità utilizzate per l’acquisizione ed il processo delle risorse.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Best practice per [!DNL Experience Manager] Assets {#best-practices-for-assets}

Adobe Experience Manager Assets è una parte fondamentale nella fornitura di esperienze di marketing digitale di alta qualità che contribuiscono al raggiungimento degli obiettivi aziendali aumentando la velocità dei contenuti. Se lavori con un numero elevato di risorse all’interno di [!DNL Assets] o carichi regolarmente/periodicamente numerose risorse, compresi video e contenuti multimediali dinamici, l’ottimizzazione dell’esperienza di gestione delle risorse digitali è fondamentale per l’efficienza del sistema.

A seconda di come hai posizionato [!DNL Assets] per la tua organizzazione e delle funzioni utilizzate per l’inserimento delle risorse, la generazione del rendering e l’estrazione dei metadati, l’identificazione e il rispetto delle best practice in diverse aree migliora notevolmente la stabilità e le prestazioni del sistema sotto carico.

Dopo aver esaminato le guide seguenti, avrai a disposizione le conoscenze e gli strumenti necessari per creare e gestire un sistema di gestione delle risorse aziendali che soddisfi le tue esigenze.

* [Guida ](performance-tuning-guidelines.md)
all’ottimizzazione delle prestazioni di AssetsInclude una serie di best practice che possono essere seguite in qualsiasi momento della tua implementazione, anche dopo il tuo live, per assicurarti di trarre il massimo dal tuo sistema.
* [Guida ](assets-sizing-guide.md)
al dimensionamento delle risorseQuando si elaborano stime per un&#39;implementazione di Assets, è importante assicurarsi che siano disponibili risorse sufficienti in termini di archiviazione delle risorse, CPU, memoria, IO e throughput di rete. Il dimensionamento di molti di questi elementi richiede la comprensione del numero di risorse caricate nel sistema. Questa guida include best practice che consentono di determinare metriche efficienti per la stima dell’infrastruttura e delle risorse necessarie per distribuire [!DNL Experience Manager] risorse e uno strumento di dimensionamento.
* [Guida ](assets-migration-guide.md)
alla migrazione delle risorseSe desideri trasferire le risorse dal sistema legacy ad  [!DNL Experience Manager] Assets, puoi prendere in considerazione diversi passaggi per semplificare il processo di migrazione. La guida alla migrazione include best practice sulle attività da eseguire per portare le risorse in [!DNL Experience Manager] in modo graduale. Ciò include l’applicazione dei metadati, la generazione di rappresentazioni e l’attivazione delle risorse per la distribuzione di pubblicazione.
* [Considerazioni ](assets-network-considerations.md)
sulla rete delle risorseQuando si gestisce l’ [!DNL Experience Manager] implementazione, è importante comprendere la topologia di rete per comprendere le prestazioni della rete, identificare i punti di blocco e descrivere l’esperienza utente prevista. Il documento Asset Network Considerations (Considerazioni sulla rete delle risorse) illustra le considerazioni sulla rete durante la progettazione della distribuzione delle risorse [!DNL Experience Manager].
* [Guida ](assets-monitoring-best-practices.md)
al monitoraggio delle risorseDopo l’implementazione della  [!DNL Experience Manager] distribuzione, è necessario monitorare determinate attività e il sistema in generale per garantire l’integrità e l’efficienza del sistema nelle operazioni. La guida al monitoraggio include le best practice per monitorare vari aspetti del sistema.
* (Obsoleto) [Guida allo scarico delle risorse](assets-offloading-best-practices.md)
La gestione di file di grandi dimensioni e l’esecuzione di flussi di lavoro in [!DNL Experience Manager] Assets può utilizzare notevoli risorse di CPU, memoria e I/O. Lo scaricamento di queste attività può ridurre le spese generali di CPU, memoria e IO. La guida allo scaricamento delle risorse include casi d’uso consigliati e best practice per lo scaricamento delle risorse.
* [[!DNL Experience Manager] best practice per le app desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] l’app desktop collega la soluzione DAM (Digital Asset Management) con il desktop, in modo da poter aprire i file disponibili nell’interfaccia utente  [!DNL Experience Manager] web direttamente sul desktop. [!DNL Experience Manager] il flusso di lavoro di facile utilizzo dell’app desktop è abilitato tramite la tecnologia di condivisione di rete fornita dai sistemi operativi desktop. Questa guida illustra le funzionalità chiave e l’utilizzo consigliato dell’app desktop [!DNL Experience Manager].
* [[!DNL Experience Manager] e Creative Cloud ](aem-cc-integration-best-practices.md)
le best practice per l’integrazioneÈ possibile integrare la  [!DNL Experience Manager] distribuzione con Creative Cloud in diversi modi. Seguendo alcune best practice per semplificare l’integrazione e i flussi di lavoro di trasferimento delle risorse, ottieni la massima efficienza. Questa guida include best practice sull’integrazione di [!DNL Experience Manager] risorse con Adobe Creative Cloud.
* (Obsoleto) [[!DNL Experience Manager] per Creative Cloud delle best practice per la condivisione delle cartelle](aem-cc-folder-sharing-best-practices.md)
Puoi configurare [!DNL Experience Manager] per consentire agli utenti in DAM di condividere cartelle con gli utenti Creative Cloud (CC), in modo che siano disponibili come cartelle condivise nel servizio Creative Cloud Assets. La funzione può essere utilizzata per scambiare file tra team creativi e utenti DAM. Questa guida illustra le best practice per sfruttare la funzione [!DNL Experience Manager] per Creative Cloud della condivisione delle cartelle.
