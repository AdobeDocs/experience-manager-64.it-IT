---
title: JSRP - Provider risorsa di archiviazione JCR
seo-title: JSRP - JCR Storage Resource Provider
description: JSRP è generalmente più adatto per gli ambienti di dimostrazione o sviluppo di un’istanza di pubblicazione e di un’istanza di authoring
seo-description: JSRP is generally best suited for demonstration or development environments of one publish instance and one author instance
uuid: 358a43c1-4137-4300-8443-c0d7166968ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: f5316a73-84e2-4a18-98c1-a384eeaa77cf
role: Admin
exl-id: 73c59497-43fe-4e15-afda-e3cf5264696e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 3%

---

# JSRP - Provider risorsa di archiviazione JCR {#jsrp-jcr-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Informazioni su JSRP {#about-jsrp}

Quando AEM Communities utilizza JSRP come opzione di archiviazione (opzione predefinita), il contenuto della community viene memorizzato in JCR e il contenuto generato dall’utente (UGC) è accessibile solo dall’istanza di authoring o pubblicazione a cui è stato pubblicato.

A causa della semplicità di implementazione, JSRP è generalmente più adatto per gli ambienti di dimostrazione o sviluppo di un’istanza di pubblicazione e di un’istanza di authoring.

Vedi anche [Caratteristiche delle opzioni SRP](working-with-srp.md#characteristics-of-srp-options) e [Topologie consigliate](topologies.md).

## Configurazione {#configuration}

### Seleziona JSRP {#select-jsrp}

Per impostazione predefinita, JSRP è l’opzione di archiviazione per UGC.

La [Console di configurazione dell&#39;archiviazione](srp-config.md) consente la selezione della configurazione di storage predefinita, che identifica quale implementazione dell&#39;SRP utilizzare.

Nell’ambiente di authoring, per raggiungere la console di configurazione dello storage

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Configurazione storage]**

![chlimage_1-234](assets/chlimage_1-234.png)

* Seleziona **[!UICONTROL Provider risorsa di archiviazione JCR (JSRP)]**
* Seleziona **[!UICONTROL Invia]**

### Pubblicazione della configurazione {#publishing-the-configuration}

Mentre JSRP è la configurazione predefinita, per assicurarsi che la configurazione identica sia impostata nell&#39;ambiente di pubblicazione:

* Autore:

   * Dalla navigazione globale: **[!UICONTROL Strumenti > Implementazione > Replica]**
   * Seleziona **[!UICONTROL Attiva albero]**
   * **[!UICONTROL Percorso iniziale]**:

      * Sfoglia per `/conf/global/settings/community/srpc/`
   * Seleziona **[!UICONTROL Attiva]**


## Gestione dei dati utente {#managing-user-data}

Per informazioni riguardanti *utenti*, *profili utente* e *gruppi di utenti*, spesso inserito nell’ambiente di pubblicazione, visita

* [Sincronizzazione utente](sync.md)
* [Gestione di utenti e gruppi di utenti](users.md)

## Risoluzione dei problemi {#troubleshooting}

### UGC non visibile in JCR {#ugc-not-visible-in-jcr}

Assicurati che JSRP sia stato configurato come provider predefinito controllando la configurazione dell&#39;opzione di archiviazione. Per impostazione predefinita, il provider delle risorse di archiviazione è JSRP.

Su tutte le istanze di authoring e pubblicazione AEM, rivedi la console di configurazione dello storage o controlla l’archivio AEM:

* in JCR, se [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Non contiene un [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) node, significa che il provider di archiviazione è JSRP
   * Se il nodo srpc esiste e contiene il nodo [configurazione predefinita](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration), le proprietà della configurazione predefinita devono definire JSRP come provider predefinito

### UGC non visibile nell’istanza di authoring {#ugc-not-visible-on-author-instance}

Questo non è un bug. Una caratteristica di JSRP è che il contenuto della community inserito nell’ambiente di pubblicazione sarà visibile solo nell’ambiente di pubblicazione.

### UGC non visibile sull&#39;istanza di pubblicazione {#ugc-not-visible-on-publish-instance}

Se viene distribuita una singola istanza di pubblicazione o un cluster di pubblicazione, segui le istruzioni per [UGC non visibile in JCR](#ugc-not-visible-in-jcr).

Se viene implementata una farm di pubblicazione, una caratteristica di JSRP è che il contenuto della community sarà visibile solo sull’istanza di pubblicazione in cui è stato pubblicato.

Affinché UGC sia visibile da qualsiasi istanza di pubblicazione, è necessario un cluster di pubblicazione.
