---
title: ASRP - Provider risorsa di archiviazione Adobe
seo-title: ASRP - Adobe Storage Resource Provider
description: Imposta AEM Communities per utilizzare un database relazionale come archivio comune
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: Admin
exl-id: 136c0913-c8b8-451d-bb28-3c3285c172a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---

# ASRP - Provider risorsa di archiviazione Adobe {#asrp-adobe-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Informazioni su ASRP {#about-asrp}

Quando AEM Communities è configurato per utilizzare ASRP come archivio comune, il contenuto generato dall’utente (UGC) è accessibile da tutte le istanze di authoring e pubblicazione senza la necessità di sincronizzazione o replica.

Vedi anche [Caratteristiche delle opzioni SRP](working-with-srp.md#characteristics-of-srp-options) e [Topologie consigliate](topologies.md).

## Requisiti {#requirements}

Per l’utilizzo dell’ASRP è necessaria una licenza aggiuntiva.

Per configurare il sito AEM Communities per l’utilizzo di ASRP per UGC, contatta il rappresentante del tuo account per:

* URL del centro dati (indirizzo dell’endpoint ASRP)
* Chiave consumer
* Chiave segreta
* ID suite di rapporti

Le chiavi consumer e segrete sono condivise in tutte le suite di rapporti per un&#39;azienda. Esiste una suite di rapporti per tenant.

## Configurazione {#configuration}

### Seleziona ASRP {#select-asrp}

La [Console di configurazione dell&#39;archiviazione](srp-config.md) consente la selezione della configurazione di storage predefinita, che identifica quale implementazione dell&#39;SRP utilizzare.

**Autore**:

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Configurazione storage]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Seleziona **[!UICONTROL Provider di risorse di archiviazione Adobe (ASRP)]**
* Le seguenti informazioni provengono dal processo di provisioning

   * **[!UICONTROL URL datacenter]**

      Pull down per selezionare il data center di produzione identificato dal rappresentante del tuo account

   * **[!UICONTROL Suite di rapporti predefinita]**

      Immetti il nome della suite di rapporti predefinita

   * **[!UICONTROL Chiave consumer]**

      Immetti la chiave del consumatore

   * **[!UICONTROL Segreto]**

      Immetti la chiave segreta

* Seleziona **[!UICONTROL Invia]**

Prepara le istanze di pubblicazione:

* [Replicare la chiave crittografica](#replicate-the-crypto-key)
* [Replicare la configurazione](#publishing-the-configuration)

Dopo aver inviato la configurazione, verifica la connessione:

* Seleziona **[!UICONTROL Configurazione del test]**
per ogni istanza di authoring e pubblicazione, verificare la connessione al data center dalla console di configurazione dello storage

* Infine, assicurati che gli URL del sito per i dati del profilo siano indirizzabili dal centro dati per [esternalizzazione dei collegamenti](#externalize-links).

### Replicare la chiave Crypto {#replicate-the-crypto-key}

La chiave del consumatore e la chiave segreta sono crittografate. Affinché le chiavi siano crittografate o decrittografate correttamente, la chiave principale di crittografia Granite deve essere la stessa su tutte le istanze AEM.

Segui le istruzioni riportate in [Replicare la chiave Crypto](deploy-communities.md#replicate-the-crypto-key).

### Collegamenti esternalizzati {#externalize-links}

Per i collegamenti corretti al profilo e all’immagine del profilo, assicurati di [Configurare l’esternalizzatore di collegamenti](../../help/sites-developing/externalizer.md).

Assicurati di impostare i domini come URL indirizzabili dall’URL del centro dati (endpoint ASRP).

### Sincronizzazione dei tempi {#time-synchronization}

Affinché l&#39;autenticazione con l&#39;endpoint ASRP abbia successo, i computer che eseguono l&#39;AEM Communities ospitato devono essere sincronizzati in tempo, ad esempio con il [Network Time Protocol (NTP)](https://www.ntp.org/).

### Pubblicazione della configurazione {#publishing-the-configuration}

L’ASRP deve essere identificato come archivio comune su tutte le istanze di authoring e pubblicazione.

Per rendere disponibile nell’ambiente di pubblicazione la stessa configurazione:

* **Autore**:

   * Passa dal menu principale a **[!UICONTROL Strumenti > Operazioni > Replica]**
   * Seleziona **[!UICONTROL Attiva albero]**
   * **[!UICONTROL Percorso iniziale]**:

      * Sfoglia per `/etc/socialconfig/srpc/`
   * Deseleziona **[!UICONTROL Modificato solo]**
   * Seleziona **[!UICONTROL Attiva]**


## Aggiornamento da AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Se si abilita ASRP su un sito community pubblicato, qualsiasi UGC già memorizzato in [JCR](jsrp.md) non sarà più visibile in quanto non vi è sincronizzazione di dati tra l’archiviazione on-premise e l’archiviazione cloud.

**`AEM Communities Extension`** è stato introdotto in AEM 6.0 social community as a cloud service. A partire da AEM 6.1 Communities, non è necessaria alcuna configurazione cloud, è sufficiente selezionare ASRP da [console di configurazione dello storage](srp-config.md).

A causa della nuova struttura di storage, è necessario seguire il [aggiornamento](upgrade.md#adobe-cloud-storage) istruzioni per l&#39;aggiornamento da social community a Communities.

## Gestione dei dati utente {#managing-user-data}

Per informazioni riguardanti *utenti*, *profili utente* e *gruppi di utenti*, spesso inserito nell’ambiente di pubblicazione, visita

* [Sincronizzazione utente](sync.md)
* [Gestione di utenti e gruppi di utenti](users.md)

## Risoluzione dei problemi {#troubleshooting}

### UGC scompare dopo l&#39;aggiornamento {#ugc-disappears-after-upgrade}

Se effettui l&#39;aggiornamento da un sito esistente della community social AEM 6.0, assicurati di seguire le [istruzioni di aggiornamento](upgrade.md#adobe-cloud-storage), altrimenti UGC *apparenza* da perdere.

### Errori di autenticazione {#authentication-errors}

Se ricevi errori di autenticazione rispetto all&#39;URL del centro dati e il registro degli errori AEM contiene messaggi sulle marche temporali non aggiornate, verifica che la sincronizzazione dell&#39;ora sia in corso.

Si consiglia di utilizzare uno strumento come [Network Time Protocol (NTP)](https://www.ntp.org/) sincronizza con il tempo tutti i server di authoring e pubblicazione AEM.

### Il nuovo contenuto non viene visualizzato nelle ricerche {#new-content-does-not-appear-in-searches}

L&#39;infrastruttura di archiviazione cloud Adobe utilizza *coerenza finale* per raggiungere gli obiettivi di scalabilità e prestazioni. Per questo motivo, i nuovi contenuti non sono immediatamente disponibili e potrebbe essere necessario qualche secondo per visualizzarli nei risultati della ricerca.

Durante il monitoraggio dell’intervallo che influisce sulla coerenza finale, contatta il rappresentante del tuo account se ci vogliono più di qualche secondo perché il nuovo contenuto venga visualizzato nelle ricerche.

### UGC non visibile nell’ASRP {#ugc-not-visible-in-asrp}

Assicurati che ASRP sia stato configurato come provider predefinito controllando la configurazione dell&#39;opzione di archiviazione. Per impostazione predefinita, il provider delle risorse di archiviazione è JSRP, non ASRP.

Su tutte le istanze di authoring e pubblicazione AEM, rivedi la console di configurazione dello storage o controlla l’archivio AEM:

* In JCR, se [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Non contiene un [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) node, significa che il provider di archiviazione è JSRP
   * Se il nodo srpc esiste e contiene il nodo [configurazione predefinita](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), le proprietà della configurazione predefinita devono definire ASRP come provider predefinito
