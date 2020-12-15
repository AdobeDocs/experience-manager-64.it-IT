---
title: Procedure ottimali per la gestione delle risorse tramite AEM
description: Identificazione e conformità alle best practice per migliorare la stabilità e le prestazioni del sistema in fase di caricamento, a seconda 'implementazione AEM Assets e delle funzionalità utilizzate per l'acquisizione ed elaborazione delle risorse.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Procedure ottimali per  AEM Assets {#best-practices-for-assets}

Adobe Experience Manager (AEM) Assets è un elemento fondamentale per offrire esperienze di marketing digitale di alta qualità che contribuiscono al raggiungimento degli obiettivi aziendali aumentando la velocità dei contenuti. Se lavorate con un gran numero di risorse in  AEM Assets o caricate regolarmente o periodicamente numerose risorse, inclusi video e contenuti multimediali dinamici, l’ottimizzazione dell’esperienza di gestione delle risorse digitali è fondamentale per l’efficienza del sistema.

A seconda di come avete posizionato  AEM Assets per la vostra organizzazione e delle funzioni utilizzate per l’assimilazione delle risorse, la generazione di rappresentazioni e l’estrazione dei metadati, l’identificazione e il rispetto delle procedure ottimali in diverse aree migliora notevolmente la stabilità e le prestazioni del sistema in condizioni di carico.

Dopo aver esaminato le guide seguenti, avrai a disposizione le conoscenze e gli strumenti necessari per creare e gestire un sistema di gestione delle risorse aziendale in grado di soddisfare le tue esigenze.

* [Guida all’ottimizzazione delle prestazioni delle risorseInclude una serie di best practice che possono essere seguite in qualsiasi momento dell’implementazione, anche dopo essere state live, per essere certi di trarre il massimo dal sistema. ](performance-tuning-guidelines.md)

* [Guida ](assets-sizing-guide.md)
al ridimensionamento delle risorseQuando si elaborano le stime per un’implementazione di Assets, è importante assicurarsi che siano disponibili risorse sufficienti in termini di storage delle risorse, CPU, memoria, IO e throughput di rete. Il ridimensionamento di molti di questi elementi richiede la comprensione del numero di risorse caricate nel sistema. Questa guida include procedure ottimali che consentono di determinare metriche efficienti per la stima dell&#39;infrastruttura e delle risorse necessarie per la distribuzione  AEM Assets nonché uno strumento di ridimensionamento.
* [Guida ](assets-migration-guide.md)
alla migrazione delle risorsePer migrare le risorse dal sistema precedente a  AEM Assets, è possibile procedere in diversi passaggi per semplificare il processo di migrazione. La guida alla migrazione include procedure ottimali relative alle attività eseguite per AEM le risorse in modo graduale. Ciò include l’applicazione di metadati, la generazione di rappresentazioni e l’attivazione delle risorse per la distribuzione di pubblicazione.
* [Considerazioni ](assets-network-considerations.md)
sulla rete delle risorseQuando si gestisce AEM distribuzione, è importante comprendere la topologia di rete per comprendere le prestazioni della rete, identificare i punti di interruzione e descrivere l&#39;esperienza utente prevista. Il documento Considerazioni sulla rete delle risorse descrive le considerazioni sulla rete al momento della progettazione della distribuzione delle risorse AEM.
* [Guida ](assets-monitoring-best-practices.md)
al monitoraggio delle risorseDopo l’implementazione AEM, è necessario monitorare determinate attività e il sistema in generale per garantire l’integrità e l’efficienza del sistema. La guida al monitoraggio include procedure ottimali per il monitoraggio di vari aspetti del sistema.
* (Obsoleto) [Guida allo scarico delle risorse](assets-offloading-best-practices.md)
La gestione di file di grandi dimensioni e l&#39;esecuzione di flussi di lavoro in  AEM Assets possono richiedere notevoli risorse di CPU, memoria e I/O. Lo scaricamento di queste attività può ridurre le spese di CPU, memoria e IO. La guida allo scaricamento delle risorse include i casi di utilizzo consigliati e le best practice per lo scarico delle risorse.
* [AEM best ](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
practice per le app desktop AEMl’app desktop collega la soluzione di gestione delle risorse digitali (DAM) con il desktop, in modo da poter aprire i file disponibili nell’interfaccia AEM Web direttamente sul desktop. AEM flusso di lavoro di facile utilizzo dell&#39;app desktop viene attivato utilizzando la tecnologia di condivisione di rete fornita dai sistemi operativi desktop. Questa guida descrive le funzionalità chiave e l&#39;uso consigliato AEM&#39;app desktop.
* [Best ](aem-cc-integration-best-practices.md)
practice per l&#39;integrazione di AEM e Creative CloudPotete integrare la distribuzione AEM con l&#39;Creative Cloud in diversi modi. Seguendo alcune best practice per semplificare i flussi di lavoro di integrazione e trasferimento delle risorse, potrai ottenere la massima efficienza. Questa guida include procedure ottimali per l&#39;integrazione  AEM Assets con Adobe Creative Cloud.
* (Obsoleto) [AEM di Creative Cloud delle procedure ottimali per la condivisione delle cartelle](aem-cc-folder-sharing-best-practices.md)
Puoi configurare AEM per consentire agli utenti di DAM di condividere cartelle con utenti di Creative Cloud (CC), in modo che siano disponibili come cartelle condivise nel servizio Creative Cloud Risorse. Questa funzione può essere utilizzata per scambiare file tra team creativi e utenti DAM. Questa guida illustra le procedure ottimali per utilizzare la funzione di condivisione delle AEM su Creative Cloud delle cartelle.
