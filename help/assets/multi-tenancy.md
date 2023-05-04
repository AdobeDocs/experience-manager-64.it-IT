---
title: Multi-tenancy per raccolte, snippet e modelli di snippet
description: Segrega il contenuto nell’archivio CRX in base all’organizzazione del cliente per impedire accessi non autorizzati.
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 4%

---

# Multi-tenancy per raccolte, snippet e modelli di snippet {#multi-tenancy-for-collections-snippets-and-snippet-templates}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La funzione Multi-tenancy consente di separare i contenuti in CRX in base al prefisso dell’organizzazione e all’ID organizzazione per proteggere il contenuto dall’accesso non autorizzato da parte degli utenti di altre organizzazioni.

Adobe Experience Manager (AEM) Assets memorizza i dati per ogni organizzazione in un percorso diverso. Ciascun percorso specifico per l&#39;organizzazione è identificato dal prefisso dell&#39;organizzazione e dall&#39;ID organizzazione.
che è incluso nella posizione tradizionale in cui diversi tipi di risorse sono memorizzati in CRX.

Ad esempio, se crei una cartella denominata `Demo`, AEM risorse per impostazione predefinita memorizza la cartella in `../content/dam/Demo` posizione in CRX. Con la funzione multi-tenancy abilitata, è possibile memorizzare i dati in `../content/dam/<organization prefix>/<organization id>Demo`.

Ad esempio, per gli utenti Adobe Marketing Cloud di AEM Assets (on-demand) assegnati a `aodpremium` per configurare il percorso seguente in `../content/dam/mac/aodpremiumDemo`, separa il contenuto. In questo esempio `mac` è il prefisso dell’organizzazione e `aodpremium` è l&#39;ID organizzazione.

In base all’organizzazione e all’ID dell’utente, questo percorso qualificato viene visualizzato nell’interfaccia AEM Assets e in diverse procedure guidate, tra cui le procedure guidate per la creazione di Sposta e Frammento per applicare la segmentazione.

La funzione multi-tenancy consente di segmentare i seguenti tipi di risorse e componenti:

* Raccolte
* Raccolte pubbliche
* Cataloghi (inclusa la procedura guidata Aggiungi/Seleziona pagina )
* Modelli
* Modelli per snippet
* Lightbox
