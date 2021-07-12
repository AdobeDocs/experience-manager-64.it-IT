---
title: Configurazione delle funzionalità di abilitazione
seo-title: Configurazione delle funzionalità di abilitazione
description: Configurare le funzioni di abilitazione in Communities
seo-description: Configurare le funzioni di abilitazione in Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Configurazione delle funzionalità di abilitazione {#configuring-enablement-features}

## Panoramica {#overview}

Le funzioni di abilitazione consentono di creare [community di abilitazione](overview.md#enablement-community).

* Questa funzione richiede licenze aggiuntive per l’utilizzo in un ambiente di produzione.

L’utilizzo delle funzioni di abilitazione richiede quanto segue:

Installazione di:

* ****
SCORMSharable Content Object Reference Model (SCORM) è una raccolta di standard e specifiche per l&#39;e-learning. SCORM definisce anche come il contenuto può essere confezionato in un file ZIP trasferibile.

* ****
MySQLMySQL è un database relazionale utilizzato principalmente per il tracciamento SCORM e i dati di reporting per l&#39;abilitazione, nonché tabelle per il tracciamento dell&#39;avanzamento video. Il feature pack SCORM per l&#39;abilitazione richiede il driver JDBC MySQL.

* ****
FFmpegFFmpeg è una soluzione per la conversione e lo streaming audio e video e, se installata, viene utilizzata per la corretta transcodifica di  [Video Assets](../../help/sites-authoring/default-components-foundation.md#video). Per le community di abilitazione, viene utilizzato nell’ambiente di authoring per ottenere i metadati per le risorse caricate e generare una miniatura da visualizzare durante l’elenco della risorsa.

Configurazione di:

* **Community**
ManagerPer le comunità di abilitazione, solo membri del gruppo 
`Community Enablement Managers` al gruppo di utenti può essere assegnato il ruolo di  `*Community Site* Enablement Manager`, le cui autorizzazioni possono includere la creazione di contenuti, le assegnazioni e la gestione di membri nell’ambiente di pubblicazione.

Configurazione opzionale di:

* **Adobe**
AnalyticsIntegration con Adobe Analytics aggiunge funzioni di reporting complete e supporta l’aggiunta di Video Heartbeat ad Analytics.

* **Dispatcher**

## Passaggi di configurazione {#configuration-steps}

Di seguito sono riportati i passaggi necessari per abilitare le comunità.

Ogni passaggio è collegato alla documentazione che fornisce i dettagli necessari.

**Su tutte le istanze di authoring/pubblicazione:**

1. **[installare il driver JDBC per](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse Web Console (bundles): Installa  *http://localhost:4502/system/console/*
bundleInstalla  ** prima di installare il pacchetto SCORM

1. **[installa SCORM](deploy-communities.md#scorm-package)**
packageUse Package Manager: 
*http://localhost:4502/crx/packmgr/*

**Su qualsiasi server:**

1. **[installare MySQL, MySQL Workbench](mysql.md)**

1. **[installa](mysql.md#database-setup)**
database MySQLEsegui script SQL scaricati dall&#39;istanza di authoring
\
   Utilizzare Workbench MySQL

**Nella stessa istanza di authoring del server di hosting:**

1. **[installare FFmpeg](ffmpeg.md)**

**Su tutte le istanze di authoring/pubblicazione:**

1. **[configura](mysql.md#configure-jdbc-connections)**
pool connessioni JDBCUsa console Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configura il](mysql.md#aem-communities-scormengine-service)**
servizio del motore SCORMUtilizzare la console Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[configurare](mysql.md#adobe-granite-csrf-filter)**
i filtri CSRFUtilizzare la console Web (configMgr): 
*http://localhost:4502/system/console/configMgr*

**Nell’istanza dell’autore:**

1. (*facoltativo*) **[configura il servizio Analytics](analytics.md)**
Usa la console Strumenti, Implementazione, Cloud Services: 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[configura la console](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpegUse Workflow/Models

1. **[abilita Tunnel](deploy-communities.md#tunnel-service-on-author)**
ServiceUsa Web Console (configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[crea](users.md#creating-community-members)** amministratori della communityPer l’ambiente di authoring utilizza la console di sicurezza classica-interfaccia utente:  *http://localhost:4502/*
useradmincreate user(s) con percorso = /home/users/community

   * Aggiungi membri ai gruppi seguenti:

      * Responsabili dell&#39;abilitazione della community
      * Amministratori community

## Dispatcher {#dispatcher}

Quando la distribuzione include [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), affinché le funzioni di abilitazione funzionino correttamente, le sezioni `clientheader`e `filter`devono essere modificate. Consulta [Configurazione di Dispatcher per Communities](dispatcher.md#enablement).
