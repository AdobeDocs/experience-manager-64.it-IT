---
title: ASRP - Fornitore di risorse di storage  Adobe
seo-title: ASRP - Fornitore di risorse di storage  Adobe
description: Imposta  AEM Communities per utilizzare un database relazionale come store comune
seo-description: Imposta  AEM Communities per utilizzare un database relazionale come store comune
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 2%

---


# ASRP - Provider risorse di storage  Adobe {#asrp-adobe-storage-resource-provider}

## Informazioni su ASRP {#about-asrp}

Quando  AEM Communities è configurato per utilizzare ASRP come store comune, il contenuto generato dall’utente (UGC) è accessibile da tutte le istanze di creazione e pubblicazione senza la necessità di eseguire la sincronizzazione e la replica.

Vedere anche [Caratteristiche delle opzioni SRP](working-with-srp.md#characteristics-of-srp-options) e [Topologie consigliate](topologies.md).

## Requisiti {#requirements}

Per l’utilizzo di ASRP è necessaria una licenza aggiuntiva.

Per configurare il sito AEM Communities  per utilizzare ASRP per UGC, contattate il rappresentante commerciale di riferimento per:

* URL del centro dati (indirizzo dell’endpoint ASRP)
* Chiave consumer
* Chiave segreta
* ID suite di rapporti

Le chiavi consumer e secret sono condivise tra tutte le suite di rapporti per una società. Esiste una suite di rapporti per tenant.

## Configurazione {#configuration}

### Seleziona ASRP {#select-asrp}

La [console di configurazione dell&#39;archivio](srp-config.md) consente di selezionare la configurazione di storage predefinita, che identifica l&#39;implementazione dell&#39;SRP da utilizzare.

**Per autore**:

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Configurazione dell&#39;archivio]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Selezionare **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**
* Le seguenti informazioni provengono dal processo di provisioning

   * **[!UICONTROL URL datacenter]**

      Estrazione per selezionare il centro dati di produzione identificato dal rappresentante commerciale

   * **[!UICONTROL Suite di rapporti predefinita]**

      Immettere il nome della suite di rapporti predefinita

   * **[!UICONTROL Chiave consumer]**

      Immettete il codice cliente

   * **[!UICONTROL Segreto]**

      Immettere la chiave segreta

* Seleziona **[!UICONTROL Invia]**

Preparate le istanze di pubblicazione:

* [Replicare la chiave di crittografia](#replicate-the-crypto-key)
* [Replica della configurazione](#publishing-the-configuration)

Dopo aver inviato la configurazione, verificare la connessione:

* Selezionare **[!UICONTROL Verifica configurazione]**
per ogni istanza di creazione e pubblicazione, verificare la connessione al centro dati dalla console Configurazione archiviazione

* Infine, assicurarsi che gli URL del sito per i dati del profilo siano eseguibili in modo instradabile dal centro dati [esternalizzando i collegamenti](#externalize-links).

### Replicare la chiave di crittografia {#replicate-the-crypto-key}

La Chiave Consumatore e la Chiave Segreta sono crittografate. Affinché le chiavi siano crittografate/decrittografate correttamente, la chiave di crittografia Granite primaria deve essere la stessa in tutte le istanze AEM.

Seguire le istruzioni riportate in [Replicare la chiave di crittografia](deploy-communities.md#replicate-the-crypto-key).

### Esternalizzare i collegamenti {#externalize-links}

Per i collegamenti corretti alle immagini del profilo e del profilo, accertatevi di configurare correttamente [Link Externalizer](../../help/sites-developing/externalizer.md).

Accertatevi di impostare i domini come URL che possono essere indirizzati dall’URL del centro dati (endpoint ASRP).

### Sincronizzazione ora {#time-synchronization}

Affinché l&#39;autenticazione con l&#39;endpoint ASRP abbia esito positivo, i computer che eseguono l&#39;AEM Communities ospitato  devono essere sincronizzati nel tempo, ad esempio con il [Network Time Protocol (NTP)](https://www.ntp.org/).

### Pubblicazione della configurazione {#publishing-the-configuration}

L’ASRP deve essere identificato come store comune in tutte le istanze di creazione e pubblicazione.

Per rendere disponibile la stessa configurazione nell’ambiente di pubblicazione:

* **Per autore**:

   * Passare dal menu principale a **[!UICONTROL Strumenti > Operazioni > Replica]**
   * Selezionare **[!UICONTROL Attiva albero]**
   * **[!UICONTROL Percorso iniziale]**:

      * Passa a `/etc/socialconfig/srpc/`
   * Deselezionare **[!UICONTROL Solo modificate]**
   * Selezionare **[!UICONTROL Activate]**


## Aggiornamento da AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Se si abilita ASRP in un sito community pubblicato, qualsiasi UGC già memorizzato in [JCR](jsrp.md) non sarà più visibile in quanto non è disponibile la sincronizzazione dei dati tra l&#39;archiviazione locale e l&#39;archiviazione cloud.

**`AEM Communities Extension`** è stato introdotto in AEM social community 6.0 come servizio cloud. A partire da AEM community 6.1, non è necessaria alcuna configurazione cloud, è sufficiente selezionare ASRP dalla [console di configurazione dello storage](srp-config.md).

A causa della nuova struttura di storage, è necessario seguire le istruzioni [upgrade](upgrade.md#adobe-cloud-storage) quando si esegue l&#39;aggiornamento da social community a Communities.

## Gestione dei dati utente {#managing-user-data}

Per informazioni su *utenti*, *profili utente* e *gruppi di utenti*, spesso inseriti nell&#39;ambiente di pubblicazione, visita

* [Sincronizzazione utente](sync.md)
* [Gestione di utenti e gruppi di utenti](users.md)

## Risoluzione dei problemi {#troubleshooting}

### UGC scompare dopo l&#39;aggiornamento {#ugc-disappears-after-upgrade}

Se si esegue l&#39;aggiornamento da un sito della community social AEM 6.0 esistente, seguire le [istruzioni di aggiornamento](upgrade.md#adobe-cloud-storage), altrimenti UGC *apparirà* per andare perso.

### Errori di autenticazione {#authentication-errors}

Se ricevete errori di autenticazione rispetto all&#39;URL del centro dati e il file AEM error.log contiene messaggi sulle marche temporali non aggiornate, verificate che la sincronizzazione dell&#39;ora avvenga.

Si consiglia di utilizzare uno strumento come [Network Time Protocol (NTP)](https://www.ntp.org/) per sincronizzare ora tutti i server di creazione e pubblicazione AEM.

### Il nuovo contenuto non viene visualizzato nelle ricerche {#new-content-does-not-appear-in-searches}

L&#39;infrastruttura di storage cloud del Adobe  utilizza *coerenza finale* per raggiungere gli obiettivi di scalabilità e prestazioni. Per questo motivo, il nuovo contenuto non è immediatamente disponibile e potrebbe essere necessario qualche secondo per visualizzarlo nei risultati della ricerca.

Mentre viene monitorato l&#39;intervallo che influisce sulla coerenza finale, contattate il rappresentante commerciale di riferimento se le ricerche richiedono più di pochi secondi per visualizzare il nuovo contenuto.

### UGC non visibile in ASRP {#ugc-not-visible-in-asrp}

Verificare che ASRP sia stato configurato come fornitore predefinito, verificando la configurazione dell&#39;opzione di storage. Per impostazione predefinita, il provider delle risorse di storage è JSRP, non ASRP.

Per tutte le istanze di creazione e pubblicazione AEM, rivedete la console Configurazione archiviazione o verificate l&#39;archivio AEM:

* In JCR, se [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Non contiene un nodo [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc), significa che il provider di archiviazione è JSRP
   * Se il nodo srpc esiste e contiene il nodo [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), le proprietà della configurazione predefinita devono definire ASRP come provider predefinito

