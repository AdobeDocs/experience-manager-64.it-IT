---
title: Best practice per gestire le risorse tramite AEM
description: Identificare e rispettare le best practice che migliorano la stabilità del sistema e le prestazioni sotto carico, a seconda dei [!DNL Experience Manager] Distribuzione delle risorse e funzionalità utilizzate per acquisire ed elaborare le risorse.
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Best practice per [!DNL Experience Manager] Risorse {#best-practices-for-assets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets è una parte fondamentale nella fornitura di esperienze di marketing digitale di alta qualità che contribuiscono al raggiungimento degli obiettivi aziendali aumentando la velocità dei contenuti. Se lavori con un numero elevato di risorse all’interno di [!DNL Assets] oppure carica regolarmente/periodicamente numerose risorse, compresi video e contenuti multimediali dinamici, l’ottimizzazione dell’esperienza di gestione delle risorse digitali è fondamentale per l’efficienza del sistema.

A seconda della posizione [!DNL Assets] per la tua organizzazione e le funzioni utilizzate per l’inserimento delle risorse, la generazione di rendering e l’estrazione dei metadati, l’identificazione e il rispetto delle best practice in aree diverse migliora notevolmente la stabilità e le prestazioni del sistema sotto carico.

Dopo aver esaminato le guide seguenti, avrai a disposizione le conoscenze e gli strumenti necessari per creare e gestire un sistema di gestione delle risorse aziendali che soddisfi le tue esigenze.

* [Guida all’ottimizzazione delle prestazioni di Assets](performance-tuning-guidelines.md)
Include un set di best practice che possono essere seguite in qualsiasi momento dell’implementazione, anche dopo il lancio, per garantire di trarre il massimo dal sistema.
* [Guida al dimensionamento delle risorse](assets-sizing-guide.md)
Quando si elaborano stime per un’implementazione di Assets, è importante assicurarsi che siano disponibili risorse sufficienti in termini di archiviazione delle risorse, CPU, memoria, IO e throughput di rete. Il dimensionamento di molti di questi elementi richiede la comprensione del numero di risorse caricate nel sistema. Questa guida include best practice che consentono di determinare metriche efficienti per la stima dell’infrastruttura e delle risorse necessarie per l’implementazione [!DNL Experience Manager] Risorse e uno strumento di ridimensionamento.
* [Guida alla migrazione delle risorse](assets-migration-guide.md)
Se desideri migrare le risorse dal sistema legacy a [!DNL Experience Manager] Risorse, puoi prendere in considerazione diversi passaggi per semplificare il processo di migrazione. La guida alla migrazione include best practice sulle attività da eseguire per inserire le risorse in [!DNL Experience Manager] in modo graduale. Ciò include l’applicazione dei metadati, la generazione di rappresentazioni e l’attivazione delle risorse per la distribuzione di pubblicazione.
* [Considerazioni sulla rete Assets](assets-network-considerations.md)
Durante la movimentazione [!DNL Experience Manager] l&#39;implementazione, la comprensione della topologia di rete è importante per comprendere le prestazioni della rete, identificare i punti di blocco e descrivere l&#39;esperienza utente prevista. Il documento Asset Network Considerations illustra le considerazioni sulla rete durante la progettazione delle [!DNL Experience Manager] Distribuzione delle risorse.
* [Guida al monitoraggio delle risorse](assets-monitoring-best-practices.md)
Dopo il [!DNL Experience Manager] la distribuzione viene implementata. È necessario monitorare determinate attività e il sistema in generale per garantire l&#39;integrità e l&#39;efficienza del sistema. La guida al monitoraggio include le best practice per monitorare vari aspetti del sistema.
* (Obsoleto) [Guida allo scaricamento delle risorse](assets-offloading-best-practices.md)
Gestione di file di grandi dimensioni ed esecuzione di flussi di lavoro in [!DNL Experience Manager] Le risorse possono utilizzare CPU, memoria e risorse di I/O considerevoli. Lo scaricamento di queste attività può ridurre le spese generali di CPU, memoria e IO. La guida allo scaricamento delle risorse include casi d’uso consigliati e best practice per lo scaricamento delle risorse.
* [[!DNL Experience Manager] best practice per le app desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] l’app desktop collega la soluzione DAM (Digital Asset Management) con il desktop, in modo da poter aprire i file disponibili nel [!DNL Experience Manager] interfaccia utente web direttamente sul desktop. [!DNL Experience Manager] il flusso di lavoro di facile utilizzo dell’app desktop è abilitato tramite la tecnologia di condivisione di rete fornita dai sistemi operativi desktop. Questa guida illustra le funzionalità chiave e l’utilizzo consigliato di [!DNL Experience Manager] app desktop.
* [[!DNL Experience Manager] e le best practice per l’integrazione con Creative Cloud](aem-cc-integration-best-practices.md)
È possibile integrare [!DNL Experience Manager] distribuzione con Creative Cloud in diversi modi. Seguendo alcune best practice per semplificare l’integrazione e i flussi di lavoro di trasferimento delle risorse, ottieni la massima efficienza. Questa guida include best practice sull’integrazione [!DNL Experience Manager] Risorse con Adobe Creative Cloud.
* (Obsoleto) [[!DNL Experience Manager] Creative Cloud delle best practice per la condivisione delle cartelle](aem-cc-folder-sharing-best-practices.md)
Puoi configurare [!DNL Experience Manager] per consentire agli utenti in DAM di condividere cartelle con gli utenti di Creative Cloud, in modo che siano disponibili come cartelle condivise nel servizio Creative Cloud Assets. La funzione può essere utilizzata per scambiare file tra team creativi e utenti DAM. Questa guida illustra le best practice per sfruttare [!DNL Experience Manager] per Creative Cloud la funzionalità di condivisione cartelle.
