---
title: Topologie consigliate per community
seo-title: Topologie consigliate per community
description: Come affrontare la gestione dei contenuti generati dall’utente (UGC)
seo-description: Come affrontare la gestione dei contenuti generati dall’utente (UGC)
uuid: 4bc1c423-0ba9-4f2e-b11c-4d6824f45641
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 46f135de-a0bf-451d-bdcc-fb29188250aa
translation-type: tm+mt
source-git-commit: 3db2abacf2161f8de715a2972bafacdad43563ef
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 1%

---


# Topologie consigliate per community {#recommended-topologies-for-communities}

A partire  AEM Communities 6.1, è stato adottato un approccio univoco per la gestione del contenuto generato dall’utente (UGC) inviato dai visitatori del sito (membri) dall’ambiente di pubblicazione.

Questo approccio è sostanzialmente diverso dal modo in cui la piattaforma AEM gestisce il contenuto del sito generalmente gestito dall’ambiente di authoring.

La piattaforma AEM utilizza un archivio nodi che replica il contenuto del sito dall&#39;autore alla pubblicazione, mentre  AEM Communities utilizza un singolo archivio comune per UGC che non viene mai replicato.

Per lo store UGC comune, è necessario scegliere un provider di risorse di storage [SRP (Storage Resource Provider)](working-with-srp.md). Le opzioni consigliate sono:

* [DSRP - Provider di risorse di archiviazione del database relazionale](dsrp.md)
* [MSRP - Provider di risorse di storage MongoDB](msrp.md)
* [ASRP - Fornitore di risorse di storage  Adobe](asrp.md)

Un&#39;altra opzione SRP, [JSRP - JCR Storage Resource Provider](jsrp.md), non supporta uno store UGC comune per gli ambienti di creazione e pubblicazione per entrambi gli accessi.

La richiesta di uno store comune genera le seguenti topologie consigliate.

>[!NOTE]
>
>Per  AEM Communities, [UGC non viene mai replicato](working-with-srp.md#ugc-never-replicated).
>
>Se la distribuzione non include uno [store comune](working-with-srp.md), UGC sarà visibile solo nell&#39;istanza di pubblicazione AEM o di creazione in cui è stato immesso.

>[!NOTE]
>
>Per ulteriori informazioni sulla piattaforma AEM, vedere [Implementazioni consigliate](../../help/sites-deploying/recommended-deploys.md) e [Introduzione alla piattaforma AEM](../../help/sites-deploying/data-store-config.md).

## Per produzione {#for-production}

La creazione di uno store comune per UGC è essenziale, e quindi l&#39;implementazione sottostante dipende dalla sua capacità di supportare uno store comune.

Due esempi:

1) Se il volume previsto di UGC è elevato e un&#39;istanza MongoDB locale è possibile, la scelta sarà [MSRP](msrp.md).

2) Per ottenere prestazioni ottimali per il contenuto della pagina, la scelta di una [farm di pubblicazione](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) e di [ASRP](asrp.md) offrirebbe un ridimensionamento ottimale di UGC con operazioni relativamente semplici.

Per entrambi, la distribuzione può essere basata su qualsiasi microkernel OAK.

Per scegliere lo store comune appropriato, considerare attentamente le caratteristiche [uniche](working-with-srp.md#characteristics-of-srp-options) di ciascuno.

Per ulteriori informazioni sui microkernel Oak, visitare [Deployments](../../help/sites-deploying/recommended-deploys.md) consigliati.

### TarMK Publish Farm {#tarmk-publish-farm}

Quando la topologia è una fattoria di pubblicazione, gli argomenti rilevanti sono

* [Sincronizzazione utente](sync.md)
* [Gestione di utenti e gruppi di utenti](users.md)

### Consigliato: DSRP, MSRP o ASRP {#recommended-dsrp-msrp-or-asrp}

| MicroKernel | CONTENTREPOSITIVO DEL SITO | CONTENUTO GENERATO DALL&#39;UTENTE | FORNITORE DI RISORSE DI STORAGE | STORE COMUNE |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| qualsiasi | JCR | MySQL | DSRP | Sì |
| qualsiasi | JCR | MongoDB | MSRP | Sì |
| qualsiasi | JCR |  Adobe di storage su richiesta | ASRP | Sì |

### JSRP {#jsrp}


| Implementazione | CONTENTREPOSITIVO DEL SITO | CONTENUTO GENERATO DALL&#39;UTENTE | FORNITORE DI RISORSE DI STORAGE | STORE COMUNE |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| Agriturismo TarMK (predefinito) | JCR | JCR | JSRP | No |
| Cluster Oak | JCR | JCR | JSRP | Sì solo per ambiente di pubblicazione |

## Per lo sviluppo {#for-development}

Per gli ambienti non di produzione, [JSRP](jsrp.md) offre semplicità nella configurazione di un ambiente di sviluppo con un&#39;istanza di creazione e un&#39;istanza di pubblicazione.

Se si sceglie [ASRP](asrp.md), [DSRP](dsrp.md) o [MSRP](msrp.md) per la produzione, è anche possibile impostare un ambiente di sviluppo simile utilizzando  Adobe di storage on-demand o MongoDB. Per un esempio, vedere [Come impostare MongoDB per Demo](demo-mongo.md).

## Riferimenti {#references}

* [Sincronizzazione utente](sync.md)

   Descrive la sincronizzazione dei dati utente tra le istanze della farm di pubblicazione.

* [Gestione di utenti e gruppi di utenti](users.md)

   Illustra i ruoli degli utenti e dei gruppi di utenti negli ambienti di creazione e pubblicazione.

* UGC [store comune](working-with-srp.md)

   Descrive l&#39;archiviazione di contenuto community separato dal contenuto del sito

* [Archivi di nodi e archivi di dati](../../help/sites-deploying/data-store-config.md)

   In sostanza, il contenuto del sito viene memorizzato in un archivio nodi. Per le risorse, un archivio dati può essere configurato per memorizzare dati binari. Per Communities, è necessario configurare uno store comune per selezionare l&#39;SRP.

* [Elementi di storage in AEM 6.3](../../help/sites-deploying/storage-elements-in-aem-6.md)

   Descrive le implementazioni di storage a due nodi: Tar e MongoDB.
