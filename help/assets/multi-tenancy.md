---
title: Più tenant per raccolte, snippet e modelli snippet
description: Segregate il contenuto nell'archivio CRX in base all'organizzazione cliente per impedire accessi non autorizzati.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Più tenant per raccolte, snippet e modelli snippet {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La funzione Multi-Tenancy consente di separare i contenuti in CRX in base al prefisso dell’organizzazione e all’ID organizzazione per proteggere i contenuti dall’accesso non autorizzato da parte degli utenti di altre organizzazioni.

Risorse Adobe Experience Manager (AEM) memorizza i dati per ogni organizzazione in un percorso diverso. Ciascun percorso specifico dell&#39;organizzazione è identificato dal prefisso dell&#39;organizzazione e dall&#39;ID organizzazione.
inclusa nella posizione tradizionale in cui sono memorizzati in CRX diversi tipi di risorse.

Ad esempio, se create una cartella denominata `Demo`, per impostazione predefinita le risorse AEM memorizzano la cartella nella posizione `../content/dam/Demo` CRX. Con la funzione multi-tenant attivata, potete archiviare i dati in `../content/dam/<organization prefix>/<organization id>Demo`.

Ad esempio, per gli utenti di Adobe Marketing Cloud di Risorse AEM (su richiesta) assegnati all&#39; `aodpremium` organizzazione, potete utilizzare la funzione multi-tenant per configurare il percorso seguente per `../content/dam/mac/aodpremiumDemo`, segregare il contenuto. In questo esempio `mac` è il prefisso dell&#39;organizzazione e `aodpremium` l&#39;ID organizzazione.

In base all’organizzazione e all’ID dell’utente, questo percorso completo viene visualizzato nell’interfaccia di Risorse AEM e in varie procedure guidate, comprese le procedure guidate per la creazione di mosse e snippet, al fine di applicare la segmentazione.

La funzione multi-tenant consente di segmentare i seguenti tipi di risorse e componenti:

* Raccolte
* Raccolte pubbliche
* Cataloghi (inclusa la procedura guidata Aggiungi/Seleziona pagina)
* Modelli
* Modelli per snippet
* Lightbox
