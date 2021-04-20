---
title: Multi-tenancy per raccolte, snippet e modelli di snippet
description: Segrega il contenuto nell’archivio CRX in base all’organizzazione del cliente per impedire accessi non autorizzati.
contentOwner: AG
feature: Collections
role: Architect,Administrator,Leader
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 1%

---


# Multi-tenancy per raccolte, snippet e modelli di snippet {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La funzione Multi-tenancy consente di separare i contenuti in CRX in base al prefisso dell’organizzazione e all’ID organizzazione per proteggere il contenuto dall’accesso non autorizzato da parte degli utenti di altre organizzazioni.

Adobe Experience Manager (AEM) Assets memorizza i dati per ogni organizzazione in un percorso diverso. Ciascun percorso specifico per l&#39;organizzazione è identificato dal prefisso dell&#39;organizzazione e dall&#39;ID organizzazione.
che è incluso nella posizione tradizionale in cui diversi tipi di risorse sono memorizzati in CRX.

Ad esempio, se crei una cartella denominata `Demo`, per impostazione predefinita AEM risorse memorizza la cartella nella posizione `../content/dam/Demo` in CRX. Con la funzione multi-tenancy abilitata, puoi memorizzare i dati in `../content/dam/<organization prefix>/<organization id>Demo`.

Ad esempio, per gli utenti Adobe Marketing Cloud di AEM Assets (on-demand) assegnati all’organizzazione `aodpremium`, puoi utilizzare la funzione multi-tenancy per configurare il seguente percorso per `../content/dam/mac/aodpremiumDemo`, separando il contenuto. In questo esempio `mac` è il prefisso dell&#39;organizzazione e `aodpremium` è l&#39;ID organizzazione.

In base all’organizzazione e all’ID dell’utente, questo percorso qualificato viene visualizzato nell’interfaccia AEM Assets e in diverse procedure guidate, tra cui le procedure guidate per la creazione di Sposta e Frammento per applicare la segmentazione.

La funzione multi-tenancy consente di segmentare i seguenti tipi di risorse e componenti:

* Raccolte
* Raccolte pubbliche
* Cataloghi (inclusa la procedura guidata Aggiungi/Seleziona pagina )
* Modelli
* Modelli per snippet
* Lightbox
