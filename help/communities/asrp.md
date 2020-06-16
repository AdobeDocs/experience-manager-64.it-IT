---
title: ASRP - Fornitore di risorse di storage Adobe
seo-title: ASRP - Fornitore di risorse di storage Adobe
description: Imposta AEM Communities per utilizzare un database relazionale come store comune
seo-description: Imposta AEM Communities per utilizzare un database relazionale come store comune
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


# ASRP - Fornitore di risorse di storage Adobe {#asrp-adobe-storage-resource-provider}

## Informazioni su ASRP {#about-asrp}

Quando i AEM Communities sono configurati per utilizzare ASRP come store comune, il contenuto generato dall’utente (UGC) è accessibile da tutte le istanze di creazione e pubblicazione senza la necessità di eseguire la sincronizzazione e la replica.

Vedere anche [Caratteristiche delle opzioni](working-with-srp.md#characteristics-of-srp-options) SRP e topologie [](topologies.md)consigliate.

## Requisiti {#requirements}

Per l’utilizzo di ASRP è necessaria una licenza aggiuntiva.

Per configurare il sito AEM Communities per l&#39;utilizzo di ASRP per UGC, contattate il rappresentante commerciale di riferimento per:

* URL del centro dati (indirizzo dell’endpoint ASRP)
* Chiave consumer
* Chiave segreta
* ID suite di rapporti

Le chiavi consumer e secret sono condivise tra tutte le suite di rapporti per una società. Esiste una suite di rapporti per tenant.

## Configurazione {#configuration}

### Seleziona ASRP {#select-asrp}

La console [Configurazione](srp-config.md) storage consente di selezionare la configurazione di storage predefinita, che identifica l&#39;implementazione di SRP da utilizzare.

**Per autore**:

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Configurazione dello storage]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Select **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**
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

* Selezionate **[!UICONTROL Verifica configurazione]** per ogni istanza di creazione e pubblicazione, verificate la connessione al data center dalla console Configurazione archiviazione

* Infine, accertati che gli URL del sito per i dati del profilo siano instradabili dal centro dati tramite l&#39; [esternalizzazione dei collegamenti](#externalize-links).

### Replicare la chiave Crypto {#replicate-the-crypto-key}

La Chiave Consumatore e la Chiave Segreta sono crittografate. Affinché le chiavi siano crittografate o decrittografate correttamente, la chiave di crittografia Granite principale deve essere la stessa in tutte le istanze di AEM.

Seguite le istruzioni riportate in [Replica della chiave](deploy-communities.md#replicate-the-crypto-key)di crittografia.

### Collegamenti esternalizzati {#externalize-links}

Per i collegamenti corretti alle immagini del profilo e del profilo, accertatevi di [configurare correttamente Link Externalizer](../../help/sites-developing/externalizer.md).

Accertatevi di impostare i domini come URL che possono essere indirizzati dall’URL del centro dati (endpoint ASRP).

### Sincronizzazione tempo {#time-synchronization}

Affinché l&#39;autenticazione con l&#39;endpoint ASRP abbia esito positivo, i computer che eseguono i AEM Communities ospitati devono essere sincronizzati in tempo, ad esempio con il protocollo NTP ( [Network Time Protocol)](https://www.ntp.org/).

### Pubblicazione della configurazione {#publishing-the-configuration}

L’ASRP deve essere identificato come store comune in tutte le istanze di creazione e pubblicazione.

Per rendere disponibile la stessa configurazione nell’ambiente di pubblicazione:

* **Per autore**:

   * Passare dal menu principale a **[!UICONTROL Strumenti > Operazioni > Replica]**
   * Seleziona **[!UICONTROL Attiva albero]**
   * **[!UICONTROL Percorso iniziale]**:

      * Passa a `/etc/socialconfig/srpc/`
   * Deseleziona **[!UICONTROL solo modifica]**
   * Seleziona **[!UICONTROL attiva]**


## Aggiornamento da AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Se abilitate ASRP su un sito community pubblicato, tutti gli UGC già memorizzati in [JCR](jsrp.md) non saranno più visibili in quanto non è disponibile la sincronizzazione dei dati tra l&#39;archiviazione locale e l&#39;archiviazione cloud.

**`AEM Communities Extension`** è stato introdotto in precedenza nelle social community di AEM 6.0 come servizio cloud. A partire da AEM 6.1 Communities, non è necessaria alcuna configurazione cloud. È sufficiente selezionare ASRP dalla console [di configurazione](srp-config.md)dello storage.

A causa della nuova struttura di storage, è necessario seguire le istruzioni di [aggiornamento](upgrade.md#adobe-cloud-storage) quando si esegue l&#39;aggiornamento dalle social community alle community.

## Gestione dei dati utente {#managing-user-data}

Per informazioni sugli *utenti*, i profili ** utente e i gruppi *di* utenti, spesso inseriti nell’ambiente di pubblicazione, visita

* [Sincronizzazione utente](sync.md)
* [Gestione di utenti e gruppi di utenti](users.md)

## Risoluzione dei problemi {#troubleshooting}

### UGC scompare dopo l&#39;aggiornamento {#ugc-disappears-after-upgrade}

Se esegui l’aggiornamento da un sito della community social AEM 6.0 esistente, assicurati di seguire le istruzioni [di](upgrade.md#adobe-cloud-storage)aggiornamento; in caso contrario UGC *risulterà* perduto.

### Errori di autenticazione {#authentication-errors}

Se ricevete errori di autenticazione rispetto all’URL del datacenter e il file di registro dell’errore AEM contiene messaggi sulle marche temporali non aggiornate, verificate che la sincronizzazione dell’ora avvenga.

Si consiglia di utilizzare uno strumento come il protocollo NTP ( [Network Time Protocol)](https://www.ntp.org/) per sincronizzare in tempo tutti i server di creazione e pubblicazione di AEM.

### Il nuovo contenuto non viene visualizzato nelle ricerche {#new-content-does-not-appear-in-searches}

L&#39;infrastruttura di storage cloud di Adobe utilizza *la coerenza* finale per raggiungere gli obiettivi di scalabilità e prestazioni. Per questo motivo, il nuovo contenuto non è immediatamente disponibile e potrebbe essere necessario qualche secondo per visualizzarlo nei risultati della ricerca.

Mentre viene monitorato l&#39;intervallo che influisce sulla coerenza finale, contattate il rappresentante commerciale di riferimento se le ricerche richiedono più di pochi secondi per visualizzare il nuovo contenuto.

### UGC non visibile nell’ASRP {#ugc-not-visible-in-asrp}

Verificare che ASRP sia stato configurato come fornitore predefinito, verificando la configurazione dell&#39;opzione di storage. Per impostazione predefinita, il provider delle risorse di storage è JSRP, non ASRP.

Per creare e pubblicare tutte le istanze di AEM, rivisitate la console Configurazione archiviazione o verificate l’archivio AEM:

* In JCR, se [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * Non contiene un nodo [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) , significa che il provider di archiviazione è JSRP
   * Se il nodo srpc esiste e contiene la configurazione [](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)predefinita del nodo, le proprietà della configurazione predefinita devono definire ASRP come provider predefinito

