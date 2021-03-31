---
title: Best practice per gestire le risorse tramite AEM
description: Identifica e rispetta le best practice che migliorano la stabilità e le prestazioni del sistema sotto carico, a seconda della distribuzione AEM Assets e delle funzionalità utilizzate per acquisire ed elaborare le risorse.
contentOwner: AG
feature: Gestione risorse
role: Architetto,Amministratore
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---


# Best practice per AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets è una parte fondamentale nella fornitura di esperienze di marketing digitale di alta qualità che contribuiscono al raggiungimento degli obiettivi aziendali aumentando la velocità dei contenuti. Se lavori con un gran numero di risorse in AEM Assets o carichi regolarmente/periodicamente numerose risorse, compresi video e contenuti multimediali dinamici, l’ottimizzazione dell’esperienza di gestione delle risorse digitali è fondamentale per l’efficienza del sistema.

A seconda di come hai posizionato AEM Assets per la tua organizzazione e delle funzioni utilizzate per l’inserimento delle risorse, la generazione del rendering e l’estrazione dei metadati, l’identificazione e il rispetto delle best practice in diverse aree migliora notevolmente la stabilità e le prestazioni del sistema sotto carico.

Dopo aver esaminato le guide seguenti, avrai a disposizione le conoscenze e gli strumenti necessari per creare e gestire un sistema di gestione delle risorse aziendali che soddisfi le tue esigenze.

* [Guida ](performance-tuning-guidelines.md)
all’ottimizzazione delle prestazioni di AssetsInclude una serie di best practice che possono essere seguite in qualsiasi momento della tua implementazione, anche dopo il tuo live, per assicurarti di trarre il massimo dal tuo sistema.
* [Guida ](assets-sizing-guide.md)
al dimensionamento delle risorseQuando si elaborano stime per un&#39;implementazione di Assets, è importante assicurarsi che siano disponibili risorse sufficienti in termini di archiviazione delle risorse, CPU, memoria, IO e throughput di rete. Il dimensionamento di molti di questi elementi richiede la comprensione del numero di risorse caricate nel sistema. Questa guida include best practice che consentono di determinare metriche efficienti per la stima dell’infrastruttura e delle risorse necessarie per distribuire AEM Assets e uno strumento di dimensionamento.
* [Guida ](assets-migration-guide.md)
alla migrazione delle risorseSe desideri trasferire le risorse dal sistema legacy ad AEM Assets, puoi prendere in considerazione diversi passaggi per semplificare il processo di migrazione. La guida alla migrazione include best practice sulle attività da eseguire per AEM le risorse in modo graduale. Ciò include l’applicazione dei metadati, la generazione di rappresentazioni e l’attivazione delle risorse per la distribuzione di pubblicazione.
* [Considerazioni ](assets-network-considerations.md)
sulla rete delle risorseQuando si gestisce AEM distribuzione, è importante comprendere la topologia di rete per comprendere le prestazioni della rete, identificare i punti di blocco e descrivere l’esperienza utente prevista. Il documento Asset Network Considerations (Considerazioni sulla rete di Assets) illustra le considerazioni sulla rete durante la progettazione della distribuzione di risorse AEM.
* [Guida ](assets-monitoring-best-practices.md)
al monitoraggio delle risorseUna volta implementata la distribuzione AEM, è necessario monitorare determinate attività e il sistema in generale per garantire l’integrità e l’efficienza del sistema. La guida al monitoraggio include le best practice per monitorare vari aspetti del sistema.
* (Obsoleto) [Guida allo scarico delle risorse](assets-offloading-best-practices.md)
La gestione di file di grandi dimensioni e l’esecuzione di flussi di lavoro in AEM Assets può richiedere notevoli risorse di CPU, memoria e I/O. Lo scaricamento di queste attività può ridurre le spese generali di CPU, memoria e IO. La guida allo scaricamento delle risorse include casi d’uso consigliati e best practice per lo scaricamento delle risorse.
* [AEM best ](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
practice per le app desktopL’app desktop AEM collega la soluzione di gestione delle risorse digitali (DAM) con il desktop, in modo da poter aprire i file disponibili nell’interfaccia web AEM direttamente sul desktop. AEM flusso di lavoro di facile utilizzo dell’app desktop è abilitato utilizzando la tecnologia di condivisione di rete fornita dai sistemi operativi desktop. Questa guida illustra le funzionalità chiave e l’utilizzo consigliato dell’app desktop AEM.
* [Best ](aem-cc-integration-best-practices.md)
practice per l’integrazione di AEM e Creative CloudÈ possibile integrare la distribuzione AEM con Creative Cloud in diversi modi. Seguendo alcune best practice per semplificare l’integrazione e i flussi di lavoro di trasferimento delle risorse, ottieni la massima efficienza. Questa guida include best practice sull’integrazione di AEM Assets con Adobe Creative Cloud.
* (Obsoleto) [AEM per Creative Cloud delle best practice per la condivisione delle cartelle](aem-cc-folder-sharing-best-practices.md)
Puoi configurare AEM per consentire agli utenti in DAM di condividere cartelle con gli utenti Creative Cloud (CC), in modo che siano disponibili come cartelle condivise nel servizio Creative Cloud Assets. La funzione può essere utilizzata per scambiare file tra team creativi e utenti DAM. Questa guida illustra le best practice per sfruttare la funzione di condivisione cartelle AEM a Creative Cloud.
