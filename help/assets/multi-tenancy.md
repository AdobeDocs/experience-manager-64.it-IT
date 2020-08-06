---
title: Più tenant per raccolte, snippet e modelli snippet
description: Segregate il contenuto nell'archivio CRX in base all'organizzazione cliente per impedire accessi non autorizzati.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 1%

---


# Più tenant per raccolte, snippet e modelli snippet {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La funzione Multi-Tenancy consente di separare i contenuti in CRX in base al prefisso dell’organizzazione e all’ID organizzazione per proteggere i contenuti dall’accesso non autorizzato da parte degli utenti di altre organizzazioni.

Adobe Experience Manager (AEM) Assets memorizza i dati per ogni organizzazione in un percorso diverso. Ciascun percorso specifico dell&#39;organizzazione è identificato dal prefisso dell&#39;organizzazione e dall&#39;ID organizzazione.
inclusa nella posizione tradizionale in cui sono memorizzati in CRX diversi tipi di risorse.

Ad esempio, se create una cartella denominata `Demo`, per impostazione predefinita AEM risorse memorizza la cartella in `../content/dam/Demo` posizione CRX. Con la funzione multi-tenant attivata, potete archiviare i dati in `../content/dam/<organization prefix>/<organization id>Demo`.

Ad esempio, per gli utenti Adobe Marketing Cloud di  AEM Assets (su richiesta) assegnati all&#39; `aodpremium` organizzazione, potete utilizzare la funzione multi-tenant per configurare il percorso seguente per `../content/dam/mac/aodpremiumDemo`separare il contenuto. In questo esempio `mac` è il prefisso dell&#39;organizzazione e `aodpremium` l&#39;ID organizzazione.

In base all&#39;organizzazione e all&#39;ID dell&#39;utente, questo percorso qualificato viene visualizzato nell&#39;interfaccia AEM Assets  e in varie procedure guidate, tra cui le procedure guidate per la creazione di Sposta e Snippet per applicare la segmentazione.

La funzione multi-tenant consente di segmentare i seguenti tipi di risorse e componenti:

* Raccolte
* Raccolte pubbliche
* Cataloghi (inclusa la procedura guidata Aggiungi/Seleziona pagina)
* Modelli
* Modelli per snippet
* Lightbox
