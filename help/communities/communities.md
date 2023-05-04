---
title: Sviluppo di Communities
seo-title: Developing Communities
description: Creare e personalizzare funzioni della community quali forum, gruppi di utenti e altro ancora
seo-description: Create and customize community features such as forums, user groups, and more
uuid: 51dc54da-9090-4d36-adf9-72d5479062a5
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: fbfe8097-3c3f-4a05-97ad-1ce526362a26
exl-id: b051b279-b0d9-41a3-b5d8-4b9bad448c0f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 6%

---

# Sviluppo di Communities {#developing-communities}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

AEM Communities semplifica la creazione e la personalizzazione di funzioni della community quali forum, gruppi di utenti, blog, domande e risposte, calendari, commenti, recensioni, votazioni, valutazioni e assegnazioni. Queste funzioni consentono di immettere contenuti generati dagli utenti (UGC) nell’ambiente di pubblicazione.

La base di un [sito della community](overview.md#communitiessites) è [quadro della componente sociale](scf.md) (SCF) La creazione di un sito comunitario inizia con la selezione di un [modello di sito community](sites-console.md) composto da [funzioni della community](functions.md).

Per una panoramica e le esercitazioni introduttive, visita:

* [Panoramica di AEM Communities](overview.md)
* [Guida introduttiva ad AEM Communities](getting-started.md)
* [Guida introduttiva ad AEM Communities per l&#39;abilitazione](getting-started-enablement.md)

>[!NOTE]
>
>Si consiglia vivamente di tenere aggiornato con il [ultime versioni](deploy-communities.md#latest-releases).

## Implementazioni consigliate {#recommended-deployments}

* [Archiviazione dei contenuti della community](working-with-srp.md): discute le scelte SRP disponibili per un archivio comune UGC
* [Topologie consigliate per community](topologies.md): discute le topologie in base al caso d’uso e alla scelta dell’SRP

## Quadro dei componenti sociali {#social-component-framework}

* [Quadro dei componenti sociali](scf.md): panoramica di framework e API
* [Helper manubrio SCF](handlebars-helpers.md): helper predefiniti e modalità di scrittura degli helper personalizzati
* [Personalizzazione lato client](client-customize.md): personalizzazione del codice in esecuzione nel browser
* [Personalizzazione lato server](server-customize.md): personalizzazione del codice in esecuzione sul server
* [Provider di risorse di storage (SRP)](srp.md): panoramica dell&#39;archiviazione dei contenuti della community
* [Linee guida sulla codifica](code-guide.md): linee guida, suggerimenti e trucchi
* [Guida ai componenti della community](components-guide.md): strumento di sviluppo interattivo

## Componenti, funzioni e funzioni di base {#component-function-and-feature-essentials}

I componenti, le funzioni e le funzioni di AEM Communities costituiscono gli elementi di base per [siti della community](sites-console.md).

* [Componenti, funzioni e funzioni di base](essentials.md)
* [Componenti Clientlibs for Communities](clientlibs.md)
* [Funzioni community](functions.md)
* [Modelli per gruppi community](tools-groups.md)
* [Modelli per sito community](sites.md)

## Membri community {#community-members}

* [Gestione di utenti e gruppi di utenti](users.md)
* [Accesso social con Facebook e Twitter](social-login.md)

## Gruppi community {#community-groups}

[Gruppi comunitari](overview.md#communitygroups) è il concetto di consentire ai membri della comunità di formare sottocomunità all&#39;interno del sito della community. La creazione di un gruppo di community può avvenire nell’ambiente di pubblicazione o di authoring.

* [Nozioni di base sui gruppi community](essentials-groups.md)
* [Funzione Groups](functions.md#groups-function)
* [Modelli per gruppi community](tools-groups.md)
* [Gestione di utenti e gruppi di utenti](users.md)
* [Gruppi community per gli autori](creating-groups.md)

## Gestione dei dati {#managing-data}

* [Essenze SRP e UGC](srp-and-ugc.md) - Metodi ed esempi di utilità dell’API SRP
* [Nozioni di base sui tag](tag.md) - possibilità per i membri della community di assegnare tag UGC e/o risorse di abilitazione catalogate

## Esercitazioni {#tutorials}

* [Tutorial lato client](tutorials.md#client-side-customization)
* [Tutorial lato server](tutorials.md#server-side-customization)
* [Istruzioni dettagliate](tutorials.md#how-to-instructions)

## Risoluzione dei problemi {#troubleshooting}

* [Risoluzione dei problemi](troubleshooting.md)
* [Problemi noti](/help/release-notes/known-issues.md)

## Documentazione di Communities correlata {#related-communities-documentation}

* Visita [Distribuzione di Communities](deploy-communities.md) per informazioni sulle distribuzioni consigliate e sulla configurazione del dispatcher.

* Visita [Amministrazione di siti di Communities](administer-landing.md) per informazioni sulla creazione di un sito community, sulla configurazione di modelli di sito community, sulla moderazione dei contenuti della community, sulla gestione dei membri e sulla configurazione dei messaggi.

* Visita [Authoring dei componenti di Communities](author-communities.md) per scoprire come creare e configurare i componenti di Communities.
