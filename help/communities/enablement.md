---
title: Configurazione delle funzioni di abilitazione
seo-title: Configurazione delle funzioni di abilitazione
description: Configurare le funzioni di abilitazione in Communities
seo-description: Configurare le funzioni di abilitazione in Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# Configurazione delle funzioni di abilitazione {#configuring-enablement-features}

## Panoramica {#overview}

Le funzioni di abilitazione consentono di creare [community di abilitazione](overview.md#enablement-community).

* Questa funzione richiede licenze aggiuntive per l&#39;utilizzo in un ambiente di produzione.

L&#39;utilizzo delle funzioni di abilitazione richiede quanto segue:

Installazione di:

* **SCORMSharable Content Object Reference Model (SCORM) è un insieme di standard e specifiche per l&#39;e-learning.**
SCORM definisce anche come il contenuto può essere incluso in un file ZIP trasferibile.

* ****
MySQLMySQL è un database relazionale utilizzato principalmente per il tracciamento SCORM e i dati di reporting per l&#39;abilitazione, nonché tabelle per il monitoraggio dell&#39;avanzamento video. Il pacchetto di funzioni SCORM per l&#39;abilitazione richiede il driver JDBC MySQL.

* ****
FFmpegFFmpeg è una soluzione per la conversione e lo streaming audio e video e, se installato, viene utilizzato per la corretta transcodifica di risorse [ ](../../help/sites-authoring/default-components-foundation.md#video)video. Per le comunità di abilitazione, viene utilizzata nell’ambiente di authoring per ottenere i metadati per le risorse caricate e generare una miniatura da visualizzare quando si elenca le risorse.

Configurazione di:

* **Community**
ManagerPer le comunità di abilitazione, solo i membri 
`Community Enablement Managers` al gruppo di utenti può essere assegnato il ruolo di  `*Community Site* Enablement Manager`, le cui autorizzazioni possono includere la creazione di contenuto, le assegnazioni e la gestione di membri nell’ambiente di pubblicazione.

Configurazione opzionale di:

* **Adobe**
AnalyticsIntegrazione con  Adobe Analytics aggiunge funzionalità di reporting complete e supporta l&#39;aggiunta di heartbeat video ad Analytics.

* **Dispatcher**

## Passaggi di configurazione {#configuration-steps}

Di seguito sono riportati i passaggi necessari per abilitare le community.

Ogni passaggio fa riferimento alla documentazione che fornisce i dettagli necessari.

**Per tutte le istanze di creazione/pubblicazione:**

1. **[installare il driver JDBC per](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse Web Console (bundle): Installare  *http://localhost:4502/system/console/*
bundleInstallare  ** prima di installare il pacchetto SCORM

1. **[installare SCORM](deploy-communities.md#scorm-package)**
packageUtilizzare Package Manager: 
*http://localhost:4502/crx/packmgr/*

**Su qualsiasi server:**

1. **[installare MySQL, MySQL Workbench](mysql.md)**

1. **[installare](mysql.md#database-setup)**
database MySQLEseguire script SQL scaricati dall&#39;istanza di creazione
\
   Utilizzare Workbench MySQL

**Sulla stessa istanza di creazione del server host:**

1. **[install FFmpeg](ffmpeg.md)**

**Per tutte le istanze di creazione/pubblicazione:**

1. **[configura](mysql.md#configure-jdbc-connections)**
pool di connessioni JDBCUsa console Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurare il](mysql.md#aem-communities-scormengine-service)**
servizio del motore SCORMUtilizzare la console Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurare](mysql.md#adobe-granite-csrf-filter)**
filtri CSRFusiamo console Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

**Nell’istanza di creazione:**

1. (*facoltativo*) **[configura il servizio Analytics](analytics.md)**
Usa console Strumenti, Implementazione, Cloud Services: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configurare la console Flusso di lavoro/Modelli](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegUse

1. **[abilita Tunnel](deploy-communities.md#tunnel-service-on-author)**
ServiceUsa console Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[creazione di](users.md#creating-community-members)** amministratori della communityPer l’ambiente di authoring, utilizzate la console di protezione classica dell’interfaccia utente:  *http://localhost:4502/*
useradminare creare utenti con percorso = /home/users/community

   * Aggiungi membri ai seguenti gruppi:

      * Manager abilitazione community
      * Amministratori community

## Dispatcher {#dispatcher}

Se la distribuzione include [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), affinché le funzioni di abilitazione funzionino correttamente, le sezioni `clientheader`e `filter`devono essere modificate. Vedere [Configurazione del dispatcher per Communities](dispatcher.md#enablement).
