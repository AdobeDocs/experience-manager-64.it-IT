---
title: Siti community
seo-title: Communities Sites
description: Panoramica della documentazione di AEM Communities
seo-description: Overview of the AEM Communities documentation
uuid: 9842ce6c-1af8-4b27-b199-07410e797ab2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 8799386a-c3b8-43cf-9f71-580ff2a81abc
role: Admin
exl-id: b5d20819-3a3f-4b9e-99a3-e7ae5ae28baf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 5%

---

# Siti community {#communities-sites}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa sezione è destinata a coloro che amministrano AEM Communities e acquisiscono familiarità con le funzioni di AEM Communities.

## Panoramica {#overview}

Per una panoramica e le esercitazioni introduttive, visita:

* [Panoramica di AEM Communities](overview.md)
* [Guida introduttiva ad AEM Communities](getting-started.md)
* [Guida introduttiva ad AEM Communities per l&#39;abilitazione](getting-started-enablement.md)

## Argomenti di amministrazione e configurazione {#administration-and-configuration-topics}

### Creazione e gestione di siti di Communities {#communities-site-creation-and-management}

* Community [console](consoles.md)

   * [Sites](sites-console.md)

      * [Gruppi (sottocomunità)](groups.md)
   * [Moderazione](moderation.md)
   * [Gestione dei membri e dei gruppi](members.md)
   * [Risorse di abilitazione](resources.md)
   * [Rapporti](reports.md)


* Community [*strumenti*](tools.md):

   * [Modelli per siti](sites.md)
   * [Modelli per gruppi](tools-groups.md)
   * [Funzioni community](functions.md)
   * [Configurazione archiviazione](srp-config.md)
   * [Guida dei componenti](components-guide.md)
   * [Badge](badges.md)


### Contenuto generato dall&#39;utente {#user-generated-content}

Una caratteristica principale di AEM Communities è la generazione di contenuti generati dagli utenti (UGC) mediante l’accesso ai visitatori del sito (membri). Per ulteriori informazioni sull’utilizzo di UGC, visita:

* [Archivio UGC comune](working-with-srp.md): scelta dell&#39;SRP per lo stoccaggio condiviso dell&#39;UGC
* [Moderazione UGC](moderate-ugc.md): i membri affidabili possono moderare UGC in massa o nel contesto
* [Assegnazione tag UGC](tag-ugc.md): le funzioni possono essere configurate per consentire ai membri di assegnare tag al contenuto
* [Traduzione di UGC](translate-ugc.md): le funzionalità possono essere configurate per tradurre tutti gli UGC o consentire ai membri di tradurre i post selezionati
* [Configurazione di Analytics](analytics.md): che consente ad Adobe Analytics di generare rapporti su varie metriche relative all’attività dei membri

### Membri community {#community-members}

* [Gestione di utenti e gruppi di utenti](users.md): dettagli dei membri della comunità e dei gruppi di membri, compresi i membri privilegiati
* [Limiti di contributo](limits.md): capacità di limitare la registrazione da parte di nuovi membri
* [Servizio tunnel](deploy-communities.md#tunnel-service-on-author): consente l’accesso ai membri e ai gruppi di membri lato pubblicazione dall’ambiente di authoring
* [Console Membri e gruppi](members.md): consente di creare e gestire membri e gruppi di membri lato pubblicazione dall’ambiente di authoring
* [Sincronizzazione utente](sync.md): per la sincronizzazione di membri e gruppi di membri in più istanze di pubblicazione
* [Accesso social con Facebook e Twitter](social-login.md): possibilità per i visitatori del sito di diventare membri della community utilizzando le proprie credenziali Facebook o Twitter
* [Punteggio e badge](implementing-scoring.md): la possibilità di assegnare distintivi per identificare i ruoli di un membro e di ottenere distintivi attraverso la loro partecipazione alla comunità
* [Notifiche](notifications.md): possibilità per i membri di essere informati dell&#39;attività che seguono
* [Abbonamenti](subscriptions.md): possibilità per i membri di interagire con la comunità utilizzando e-mail esterne
* [Messaggistica](messaging.md): capacità dei membri di interagire con la comunità utilizzando messaggi interni

### Funzioni di abilitazione {#enablement-features}

* [Configurazione dell’abilitazione](enablement.md): informazioni necessarie per configurare correttamente le funzioni di abilitazione
* [Configurazione di Analytics](analytics.md): informazioni necessarie per abilitare le funzioni di Adobe Analytics for Communities
* [Risorse di abilitazione assegnazione tag](tag-resources.md): necessari per creare cataloghi di abilitazione

### Distribuzione {#deployment}

La sezione Distribuzione contiene informazioni specifiche di AEM Communities.

La natura dell&#39;utilizzo dei contenuti della community influenza la struttura dell&#39;implementazione:

* [Topologie consigliate per community](topologies.md)

È importante installare la versione più recente di Communities sulla piattaforma AEM:

* [Feature Pack per le community più recenti](deploy-communities.md#latestfeaturepack)

Consulta la pagina di distribuzione per altre informazioni specifiche di Communities, ad esempio per [Aggiornamento](upgrade.md), [Dispatcher](dispatcher.md) e [Replica](deploy-communities.md#replication-agents-on-author).

## Documentazione di Communities correlata {#related-communities-documentation}

* Visita [Distribuzione di Communities](deploy-communities.md) per informazioni sulle distribuzioni consigliate.

* Visita [Sviluppo di Communities](communities.md) per informazioni sul framework dei componenti sociali (SCF) e sulla personalizzazione dei componenti e delle funzionalità di Communities.

* Visita [Authoring dei componenti di Communities](author-communities.md) per scoprire come creare e configurare i componenti di Communities.
