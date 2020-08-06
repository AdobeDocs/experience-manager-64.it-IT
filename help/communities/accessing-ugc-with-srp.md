---
title: Accesso a UGC con SRP
seo-title: Accesso a UGC con SRP
description: Quando un sito è configurato per l'utilizzo di ASRP o MSRP, l'UGC effettivo non viene memorizzato in AEM archivio nodi (JCR)
seo-description: Quando un sito è configurato per l'utilizzo di ASRP o MSRP, l'UGC effettivo non viene memorizzato in AEM archivio nodi (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# Accesso a UGC con SRP {#accessing-ugc-with-srp}

## Informazioni su SRP {#about-srp}

Tutti  componenti e funzionalità AEM Communities sono basati sul framework di componenti [social network (SCF)](scf.md), che richiama l&#39;API SocialResourceProvider per accedere a tutto il contenuto generato dall&#39;utente (UGC).

Prima di creare un sito community, è necessario configurare il provider di risorse di [storage (SRP)](working-with-srp.md) per selezionare un&#39;implementazione coerente con la [topologia](topologies.md)sottostante. Le implementazioni SRP si basano su tre opzioni di storage:

1. [ASRP](asrp.md) -  Adobe di storage su richiesta
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## Archiviazione UGC {#about-ugc-storage}

Ciò che è importante sapere sull&#39;archiviazione di UGC è che, quando un sito è configurato per utilizzare ASRP o MSRP, l&#39;UGC effettivo non è memorizzato in AEM archivio [](../../help/sites-deploying/data-store-config.md) nodi (JCR).

Anche se in JCR possono essere presenti nodi che oscurano l&#39;UGC per fornire metadati utili, questi nodi non devono essere confusi con l&#39;UGC effettivo.

Vedere Panoramica sui provider delle risorse [di storage.](srp.md)

## Best practice {#best-practice}

Quando si sviluppano componenti personalizzati, gli sviluppatori devono prestare attenzione alla codifica indipendentemente dalla topologia scelta, conservando la flessibilità necessaria per passare a una nuova topologia in futuro.

### Presupponi JCR non disponibile {#assume-jcr-not-available}

I metodi specifici per JCR dovrebbero essere evitati.

Metodi da utilizzare:

* API Sling (risorsa Sling)
   * Non supporre che ci siano nodi JCR

* Eventi OSGi
   * Non presumere che ci siano eventi JCR

* [Utilità risorse social](socialutils.md#socialresourceutilities-package)
* [Utilità SCF](socialutils.md#scfutilities-package)

Metodi per evitare:

* API nodo
* Eventi JCR
* Lancio di flussi di lavoro (che utilizzano eventi JCR)

### Usa raccolte di ricerca {#use-search-collections}

Diversi SRP possono avere lingue di query native diverse. È consigliabile utilizzare i metodi del pacchetto [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) per richiamare la lingua di query appropriata.

Per ulteriori informazioni, consulta [Ricerca in Essentials](search-implementation.md).

## Riferimenti {#resources}

* [Archiviazione](working-with-srp.md) dei contenuti della community - illustra le opzioni SRP disponibili per uno store comune UGC
* [Panoramica](srp.md) del provider di risorse di storage - introduzione e utilizzo del repository
* [Caratteristiche essenziali di SRP e UGC](srp-and-ugc.md) - Metodi e esempi di utilità SRP
* [Ricerca Essentials](search-implementation.md) - informazioni essenziali per la ricerca UGC
* [Refactoring](socialutils.md) SocialUtils - mappatura di metodi di utilità obsoleti ai metodi di utilità SRP correnti
