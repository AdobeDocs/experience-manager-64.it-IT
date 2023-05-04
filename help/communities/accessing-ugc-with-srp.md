---
title: Accesso a UGC con SRP
seo-title: Accessing UGC with SRP
description: Quando un sito è configurato per utilizzare ASRP o MSRP, l'UGC effettivo non viene memorizzato nell'archivio nodi AEM (JCR)
seo-description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 2%

---

# Accesso a UGC con SRP {#accessing-ugc-with-srp}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Informazioni sull’SRP {#about-srp}

Tutti i componenti e le funzioni di AEM Communities sono incorporati nella [quadro della componente sociale (SCF)](scf.md), che richiama l’API SocialResourceProvider per accedere a tutti i contenuti generati dall’utente (UGC).

Prima della creazione di un sito community, la funzione [provider di risorse di archiviazione (SRP)](working-with-srp.md) deve essere configurato per selezionare un&#39;implementazione coerente con il sottostante [topologia](topologies.md). Le implementazioni SRP si basano su tre opzioni di storage:

1. [ASRP](asrp.md) - Adobe on-demand storage
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## Informazioni sullo storage UGC {#about-ugc-storage}

Ciò che è importante sapere sull&#39;archiviazione di UGC è che, quando un sito è configurato per utilizzare ASRP o MSRP, l&#39;UGC effettivo non è memorizzato in AEM [archivio nodi](../../help/sites-deploying/data-store-config.md) (JCR).

Anche se ci possono essere nodi in JCR che ombreggiano l&#39;UGC per fornire metadati utili, questi nodi non devono essere confusi con l&#39;UGC effettivo.

Vedi [Panoramica del provider di risorse di archiviazione.](srp.md)

## Best practice {#best-practice}

Quando si sviluppano componenti personalizzati, gli sviluppatori devono fare attenzione al codice indipendentemente dalla topologia attualmente selezionata, mantenendo così la flessibilità per passare a una nuova topologia in futuro.

### Supponiamo che JCR non sia disponibile {#assume-jcr-not-available}

È opportuno evitare i metodi specifici di JCR.

Metodi per l&#39;uso:

* API Sling (risorsa Sling)
   * Non presumere che ci siano nodi JCR

* Eventi OSGi
   * Non presumere che ci siano eventi JCR

* [Utilità risorse sociali](socialutils.md#socialresourceutilities-package)
* [Utilità SCF](socialutils.md#scfutilities-package)

Metodi per evitare:

* API nodo
* Eventi JCR
* Lancio di flussi di lavoro (che utilizzano eventi JCR)

### Utilizzare le raccolte di ricerca {#use-search-collections}

I diversi SRP possono avere linguaggi di query nativi diversi. Si consiglia di utilizzare i metodi [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) per richiamare il linguaggio di query appropriato.

Per ulteriori informazioni, consulta [Nozioni di base sulla ricerca](search-implementation.md).

## Riferimenti {#resources}

* [Archiviazione dei contenuti della community](working-with-srp.md) - discute le scelte SRP disponibili per un negozio comune UGC
* [Panoramica del provider di risorse di storage](srp.md) - introduzione e utilizzo dell&#39;archivio
* [Essenze SRP e UGC](srp-and-ugc.md) - Metodi e esempi di utilità SRP
* [Nozioni di base sulla ricerca](search-implementation.md) - informazioni essenziali per la ricerca UGC
* [Refactoring di SocialUtils](socialutils.md) - mappatura di metodi di utilità obsoleti ai metodi di utilità SRP correnti
