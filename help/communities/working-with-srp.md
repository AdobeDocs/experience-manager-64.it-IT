---
title: SRP - Memorizzazione dei contenuti nella community
seo-title: SRP - Memorizzazione dei contenuti nella community
description: A partire  AEM Communities 6.1, il contenuto generato dall'utente (UGC) viene memorizzato in un unico store comune fornito da un provider di risorse di storage (SRP)
seo-description: A partire  AEM Communities 6.1, il contenuto generato dall'utente (UGC) viene memorizzato in un unico store comune fornito da un provider di risorse di storage (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---


# SRP - Memorizzazione dei contenuti nella community {#srp-community-content-storage}

## Introduzione {#introduction}

A partire  AEM Communities 6.1, i contenuti generati dall&#39;utente (UGC) vengono memorizzati in un unico store comune fornito da un provider di risorse di storage (SRP). È possibile scegliere tra diverse opzioni SRP, ad esempio ASRP, MSRP e JSRP.

A differenza delle versioni precedenti, non esiste replica inversa/avanti di UGC tra le istanze AEM. Al contrario, l’SRP rende direttamente accessibile UGC per le operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD) da tutte le istanze di creazione e pubblicazione, con un’eccezione per JSRP.

Di seguito sono riportate [le caratteristiche di ciascuna opzione](#characteristics-of-srp-options)SRP, che è un&#39;informazione fondamentale per il processo decisionale nella scelta dell&#39;SRP appropriato e della distribuzione [](topologies.md)sottostante.

Per informazioni dettagliate sull&#39;utilizzo di SRP per UGC, vedere Panoramica [del provider di risorse di](srp.md)storage.

>[!NOTE]
>
>SRP si applica solo ai contenuti della community. Non influenza la posizione di memorizzazione del contenuto del sito (archivio[](../../help/sites-deploying/data-store-config.md)nodi) e non influisce sulla gestione protetta della registrazione utente, dei profili utente e dei gruppi di utenti tra AEM istanze (vedere anche [Gestione dei dati](#managing-user-data)utente).

>[!CAUTION]
>
>A partire dal AEM 6.1, [UGC non viene mai replicato](#ugc-never-replicated).
>
>Se la distribuzione non include uno store comune, come la topologia [JSRP](topologies.md#jsrp) predefinita, UGC sarà visibile solo nell’istanza di pubblicazione o di creazione AEM in cui è stato immesso. Solo se la topologia include un cluster di pubblicazione, l’UGC sarà visibile su qualsiasi istanza di pubblicazione.

## Caratteristiche delle opzioni SRP {#characteristics-of-srp-options}

[ASRP - Fornitore di risorse di storage  Adobe](asrp.md)\
Con questa opzione, l&#39;UGC viene mantenuto in remoto in un servizio cloud ospitato e gestito da  Adobe. Richiede una licenza aggiuntiva e lavora con un rappresentante commerciale per fornire il conto per tale licenza specifica.

* Richiede un servizio cloud associato fornito e supportato da  Adobe per memorizzare il contenuto della community
* Richiede la scelta di un centro dati in una specifica area geografica (USA, EMEA, APAC)
* Richiede l&#39;accesso programmatico a UGC tramite l&#39;API SRP
* Ideale per la farm di pubblicazione TarMK
* Adatto quando non si intende investire nello storage locale

>[!NOTE]
>
>Esiste un limite per il caricamento di allegati a post (o commenti) in ASRP, pari a 50 MB.

[MSRP - Provider di risorse di storage MongoDB](msrp.md)\
Con questa opzione, l&#39;UGC viene mantenuto direttamente in un&#39;istanza MongoDB locale.

* Richiede un&#39;installazione locale con licenza di MongoDB per memorizzare il contenuto della community
* Richiede un&#39;installazione locale di Apache Solr
* Richiede l&#39;accesso programmatico a UGC tramite l&#39;API SRP
* Ideale per una farm di pubblicazione TarMK esistente
* Ideale per un cluster MongoMK o RdbMK
* Ideale per grandi quantità di contenuti comunitari

[DSRP - Provider di risorse di archiviazione del database relazionale](dsrp.md)\
Con questa opzione, l&#39;UGC viene mantenuto direttamente in un&#39;istanza di database MySQL locale.

* Richiede un&#39;installazione locale di MySQL per memorizzare il contenuto della community
* Richiede un&#39;installazione locale di Apache Solr
* Richiede l&#39;accesso programmatico a UGC tramite l&#39;API SRP
* Ideale per una farm di pubblicazione TarMK esistente
* Ideale per un cluster MongoMK o RdbMK
* Ideale per grandi quantità di contenuti comunitari

[JSRP - Provider di risorse di storage JCR](jsrp.md)\
Con l&#39;opzione predefinita, non è disponibile uno store comune. L&#39;UGC è persistente solo nello stesso repository JCR dell&#39;istanza AEM in cui è stato immesso.

* Memorizza il contenuto della community nell&#39;archivio JCR dell&#39;istanza di creazione o pubblicazione AEM cui è stato pubblicato
* Richiede l&#39;accesso programmatico a UGC tramite l&#39;API SRP
* Richiede un cluster di pubblicazione se vengono distribuite più istanze di pubblicazione (non esiste alcun meccanismo di replica tra le istanze di pubblicazione in una farm TarMK)
* La moderazione viene eseguita solo nell’ambiente di pubblicazione (non esiste un meccanismo di replica inverso/avanti tra l’autore e la pubblicazione)
* Generalmente ideale per lo sviluppo, le dimostrazioni e la formazione

## Configurazione di SRP {#configuring-srp}

La specifica dell&#39;opzione di memorizzazione predefinita, basata sulla distribuzione sottostante, viene effettuata tramite la console [Configurazione](srp-config.md)storage.

Per i dettagli di configurazione di ciascuna opzione, vedete:

* [ASRP - Fornitore di risorse di storage  Adobe](asrp.md)
* [MSRP - Provider di risorse di storage MongoDB](msrp.md)
* [DSRP - Provider di risorse di archiviazione del database relazionale](dsrp.md)
* [JSRP - Provider di risorse di storage JCR](jsrp.md)

Se non è selezionata alcuna opzione di archiviazione attiva, per impostazione predefinita viene attivato JSRP.

## Informazioni aggiuntive {#additional-information}

### UGC non replicato {#ugc-never-replicated}

Nell’ambiente di authoring, un autore crea il contenuto della pagina e lo replica nell’ambiente di pubblicazione. Quando una pagina include una funzione AEM Communities  interattiva, come commenti, revisioni, forum, blog o QnA, l&#39;interazione dei membri (con accesso ai visitatori del sito) in un&#39;istanza di pubblicazione genera contenuto generato dall&#39;utente (UGC) immesso nell&#39;ambiente di pubblicazione.

Precedentemente, questo contenuto della community veniva replicato in modo inverso nelle istanze dell&#39;autore e dagli autori replicati alle istanze di pubblicazione. È stato problematico mantenere la coerenza tra AEM istanze con replica inversa e successiva.

A partire da  AEM Communities 6.1, la necessità di replica di UGC è stata eliminata utilizzando la memorizzazione condivisa per UGC, come descritto in precedenza.

Mentre il contenuto del sito viene replicato, UGC non viene mai replicato.

### Gestione dei dati utente {#managing-user-data}

Anche per le comunità di interesse sono [*utenti *, gruppi* di *utenti e profili**](users.md)utente. Questi dati relativi all’utente, quando creati e aggiornati nell’ambiente di pubblicazione, devono essere resi disponibili ad altre istanze di pubblicazione quando la topologia è una farm[di](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)pubblicazione.

A partire da  AEM Communities 6.1, i dati relativi agli utenti vengono sincronizzati utilizzando la distribuzione Sling anziché la replica. Per ulteriori informazioni, visita Sincronizzazione [](sync.md)utente.

### Upgrading to AEM Communities 6.2 {#upgrading-to-aem-communities}

Quando si esegue l&#39;aggiornamento a  AEM Communities 6.3, se è necessario mantenere l&#39;UGC preesistente, è necessario adottare delle misure a seconda che la comunità AEM 5.6.1 o AEM 6.0 utilizzasse  Adobe su richiesta o lo storage locale di UGC.

Per informazioni dettagliate, visitate [Aggiornamento ad  AEM Communities 6.3](upgrade.md).
