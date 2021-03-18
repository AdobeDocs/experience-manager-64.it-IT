---
title: SRP - Archiviazione dei contenuti della community
seo-title: SRP - Archiviazione dei contenuti della community
description: A partire da AEM Communities 6.1, il contenuto generato dall’utente (UGC) viene memorizzato in un singolo archivio comune fornito da un provider di risorse di archiviazione (SRP)
seo-description: A partire da AEM Communities 6.1, il contenuto generato dall’utente (UGC) viene memorizzato in un singolo archivio comune fornito da un provider di risorse di archiviazione (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---


# SRP - Archiviazione dei contenuti della community {#srp-community-content-storage}

## Introduzione {#introduction}

A partire da AEM Communities 6.1, il contenuto generato dall’utente (UGC) viene memorizzato in un singolo archivio comune fornito da un provider di risorse di archiviazione (SRP). Ci sono diverse opzioni SRP da scegliere, come ASRP, MSRP e JSRP.

A differenza delle versioni precedenti, non esiste una replica inversa/forward di UGC tra le istanze AEM. Al contrario, l’SRP rende l’UGC direttamente accessibile per le operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD) da tutte le istanze di authoring e pubblicazione, con un’eccezione per JSRP.

Di seguito sono riportate le [caratteristiche di ogni opzione SRP](#characteristics-of-srp-options), che sono informazioni cruciali per il processo decisionale quando si sceglie l&#39;SRP appropriato e la [distribuzione sottostante](topologies.md).

Per informazioni dettagliate sull&#39;utilizzo dell&#39;SRP per UGC, vedere [Panoramica del provider di risorse di storage](srp.md).

>[!NOTE]
>
>L’SRP si applica solo ai contenuti della community. Non influisce sulla posizione in cui viene memorizzato il contenuto del sito ([node store](../../help/sites-deploying/data-store-config.md)) e non sulla gestione sicura della registrazione utente, dei profili utente e dei gruppi di utenti tra le istanze AEM (vedi anche [Gestione dei dati utente](#managing-user-data)).

>[!CAUTION]
>
>A partire da AEM 6.1, [UGC non viene mai replicato](#ugc-never-replicated).
>
>Quando la distribuzione non include un archivio comune, ad esempio la topologia predefinita [JSRP](topologies.md#jsrp), UGC sarà visibile solo sull&#39;istanza di pubblicazione o authoring AEM in cui è stato immesso. Solo se la topologia include un cluster di pubblicazione, l&#39;UGC sarà visibile su qualsiasi istanza di pubblicazione.

## Caratteristiche delle opzioni SRP {#characteristics-of-srp-options}

[ASRP - Provider risorsa di archiviazione Adobe](asrp.md)\
Con questa opzione, l’UGC viene mantenuto in remoto in un servizio cloud ospitato e gestito da Adobe. Richiede una licenza aggiuntiva e collabora con un rappresentante commerciale per fornire l&#39;account per quella licenza specifica.

* Richiede un servizio cloud associato fornito e supportato da Adobe per archiviare i contenuti della community
* Richiede la scelta di un centro dati in una posizione geografica specifica (Stati Uniti, EMEA, APAC)
* Richiede l’accesso programmatico a UGC tramite l’API SRP
* Adatto per farm di pubblicazione TarMK
* Adatto quando non si intende investire nello storage locale

>[!NOTE]
>
>C&#39;è un limite per caricare gli allegati ai post (o commenti) in ASRP, che è di 50 MB.

[MSRP - Provider risorsa di archiviazione MongoDB](msrp.md)\
Con questa opzione, l’UGC viene mantenuto direttamente in un’istanza MongoDB locale.

* Richiede un&#39;installazione locale con licenza di MongoDB per memorizzare i contenuti della community
* Richiede un&#39;installazione locale di Apache Solr
* Richiede l’accesso programmatico a UGC tramite l’API SRP
* Ideale per una farm di pubblicazione TarMK esistente
* Adatto per un cluster MongoMK o RdbMK
* Adatto per grandi quantità di contenuti comunitari

[DSRP - Provider risorsa di archiviazione database relazionale](dsrp.md)\
Con questa opzione, l&#39;UGC viene mantenuto direttamente in un&#39;istanza di database MySQL locale.

* Richiede un&#39;installazione locale di MySQL per memorizzare il contenuto della community
* Richiede un&#39;installazione locale di Apache Solr
* Richiede l’accesso programmatico a UGC tramite l’API SRP
* Ideale per una farm di pubblicazione TarMK esistente
* Adatto per un cluster MongoMK o RdbMK
* Adatto per grandi quantità di contenuti comunitari

[JSRP - Provider risorsa di archiviazione JCR](jsrp.md)\
Con l&#39;opzione predefinita, non esiste un archivio comune. L’UGC viene mantenuto solo nello stesso archivio JCR dell’istanza AEM in cui è stato inserito.

* Memorizza i contenuti della community nell’archivio JCR dell’istanza di authoring o pubblicazione AEM a cui è stato pubblicato
* Richiede l’accesso programmatico a UGC tramite l’API SRP
* Richiede un cluster di pubblicazione se vengono distribuite più istanze di pubblicazione (non esiste un meccanismo di replica tra le istanze di pubblicazione in una farm TarMK)
* La moderazione viene eseguita solo nell’ambiente di pubblicazione (non esiste un meccanismo di replica inversa/forward tra l’autore e la pubblicazione)
* Generalmente migliore per lo sviluppo, le dimostrazioni e la formazione

## Configurazione dell&#39;SRP {#configuring-srp}

La specificazione dell&#39;opzione di archiviazione predefinita, basata sulla distribuzione sottostante, viene eseguita tramite la [console di configurazione dello storage](srp-config.md).

Per i dettagli di configurazione di ciascuna opzione, vedi:

* [ASRP - Provider risorsa di archiviazione Adobe](asrp.md)
* [MSRP - Provider risorsa di archiviazione MongoDB](msrp.md)
* [DSRP - Provider risorsa di archiviazione database relazionale](dsrp.md)
* [JSRP - Provider risorsa di archiviazione JCR](jsrp.md)

Se non è selezionata alcuna opzione di archiviazione attiva, per impostazione predefinita JSRP è abilitato.

## Informazioni aggiuntive {#additional-information}

### UGC non replicato {#ugc-never-replicated}

Nell’ambiente di authoring, un autore crea il contenuto della pagina e lo replica nell’ambiente di pubblicazione. Quando una pagina include una funzione di AEM Communities interattiva, ad esempio commenti, revisioni, forum, blog o QnA, l’interazione dei membri (connessi ai visitatori del sito) su un’istanza di pubblicazione si traduce in contenuti generati dagli utenti (UGC) inseriti nell’ambiente di pubblicazione.

In precedenza, il contenuto della community veniva replicato inverso nelle istanze dell’autore e dall’autore replicato alle istanze di pubblicazione. È stato problematico mantenere la coerenza tra le istanze AEM con la replica inversa e successiva.

A partire da AEM Communities 6.1, la necessità di replica di UGC è stata eliminata utilizzando lo storage condiviso per UGC, come descritto in precedenza.

Mentre il contenuto del sito viene replicato, UGC non viene mai replicato.

### Gestione dei dati utente {#managing-user-data}

Anche i siti Web sono [*utenti*, *gruppi di utenti* e *profili utente*](users.md). Questi dati relativi all’utente, quando creati e aggiornati nell’ambiente di pubblicazione, devono essere resi disponibili ad altre istanze di pubblicazione quando la topologia è una [farm di pubblicazione](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

A partire da AEM Communities 6.1, i dati relativi all’utente vengono sincronizzati utilizzando la distribuzione Sling invece della replica. Per ulteriori informazioni, visita [Sincronizzazione utente](sync.md).

### Aggiornamento a AEM Communities 6.2 {#upgrading-to-aem-communities}

Quando esegui l’aggiornamento ad AEM Communities 6.3, se è necessario mantenere gli UGC preesistenti, è necessario adottare misure a seconda che la community AEM 5.6.1 o AEM 6.0 utilizzasse lo storage Adobe on-demand o on-premise di UGC.

Per ulteriori informazioni, visita [Aggiornamento ad AEM Communities 6.3](upgrade.md).
