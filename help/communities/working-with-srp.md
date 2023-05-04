---
title: SRP - Archiviazione dei contenuti della community
seo-title: SRP - Community Content Storage
description: A partire da AEM Communities 6.1, il contenuto generato dall’utente (UGC) viene memorizzato in un singolo archivio comune fornito da un provider di risorse di archiviazione (SRP)
seo-description: As of AEM Communities 6.1, user generated content (UGC) is stored in a single, common store provided by a storage resource provider (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Admin
exl-id: 4ff530ae-c676-4259-86f2-a3881843b642
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 1%

---

# SRP - Archiviazione dei contenuti della community {#srp-community-content-storage}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

A partire da AEM Communities 6.1, il contenuto generato dall’utente (UGC) viene memorizzato in un singolo archivio comune fornito da un provider di risorse di archiviazione (SRP). Ci sono diverse opzioni SRP da scegliere, come ASRP, MSRP e JSRP.

A differenza delle versioni precedenti, non esiste una replica inversa/forward di UGC tra le istanze AEM. Al contrario, l’SRP rende l’UGC direttamente accessibile per le operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD) da tutte le istanze di authoring e pubblicazione, con un’eccezione per JSRP.

Di seguito sono riportati i [caratteristiche di ciascuna opzione SRP](#characteristics-of-srp-options), che costituisce un&#39;informazione fondamentale per il processo decisionale nella scelta dell&#39;SRP appropriato e [distribuzione sottostante](topologies.md).

Per informazioni dettagliate sull&#39;uso dell&#39;SRP per UGC, vedi [Panoramica del provider di risorse di storage](srp.md).

>[!NOTE]
>
>L’SRP si applica solo ai contenuti della community. Non influisce sul luogo in cui viene memorizzato il contenuto del sito ([archivio nodi](../../help/sites-deploying/data-store-config.md)) e non influisce sulla gestione sicura della registrazione utente, dei profili utente e dei gruppi di utenti tra le istanze AEM (vedi anche [Gestione dei dati utente](#managing-user-data)).

>[!CAUTION]
>
>A partire dal AEM 6.1, [UGC non viene mai replicato](#ugc-never-replicated).
>
>Quando la distribuzione non include un archivio comune, ad esempio [JSRP](topologies.md#jsrp) topologia, UGC sarà visibile solo sull’istanza di pubblicazione o authoring AEM in cui è stato inserito. Solo se la topologia include un cluster di pubblicazione, l&#39;UGC sarà visibile su qualsiasi istanza di pubblicazione.

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

## Configurazione dell’SRP {#configuring-srp}

La specificazione dell&#39;opzione di archiviazione predefinita, basata sulla distribuzione sottostante, viene eseguita tramite [Console di configurazione dell&#39;archiviazione](srp-config.md).

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

Anche di interesse per i Comuni sono [*utenti*, *gruppi di utenti* e *profili utente*](users.md). Questi dati relativi all’utente, quando creati e aggiornati nell’ambiente di pubblicazione, devono essere resi disponibili ad altre istanze di pubblicazione quando la topologia è una [pubblica azienda](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

A partire da AEM Communities 6.1, i dati relativi all’utente vengono sincronizzati utilizzando la distribuzione Sling invece della replica. Per ulteriori informazioni, visita [Sincronizzazione utente](sync.md).

### Aggiornamento ad AEM Communities 6.2 {#upgrading-to-aem-communities}

Quando esegui l’aggiornamento ad AEM Communities 6.3, se è necessario mantenere gli UGC preesistenti, è necessario adottare misure a seconda che la community AEM 5.6.1 o AEM 6.0 utilizzasse lo storage Adobe on-demand o on-premise di UGC.

Per maggiori dettagli, visita [Aggiornamento ad AEM Communities 6.3](upgrade.md).
