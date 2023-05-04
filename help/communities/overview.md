---
title: Panoramica di AEM Communities
seo-title: AEM Communities Overview
description: Panoramica delle funzioni e della configurazione di AEM Communities
seo-description: An overview of AEM Communities features and setup
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 2%

---

# Panoramica di AEM Communities {#aem-communities-overview}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager (AEM) Communities consente di creare rapidamente un sito di community on-premise con prestazioni migliorate, una migliore gestione del sito e la possibilità di convertire i visitatori del sito in membri di valore della community.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Funzioni di Communities {#communities-features}

AEM Communities consente lo sviluppo di una relazione con i visitatori del sito che informa attraverso blog, domande e risposte e calendari di eventi, ottenendo allo stesso tempo informazioni attraverso forum, commenti e altri contenuti della community, spesso denominati contenuti generati dagli utenti (UGC).

Inoltre, AEM Communities consente la moderazione da parte dei membri fidati nell’ambiente di pubblicazione, l’accesso social con Twitter e Facebook, la traduzione in linea dei contenuti della community, la creazione di gruppi di community dal sito della community pubblicato, il punteggio per l’assegnazione di badge, condivisione di file, notifiche e flussi di attività.

Le funzioni di Communities possono essere dimostrate utilizzando [AEM Demo](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponibile pubblicamente su GitHub.com o con la nuova implementazione di riferimento We.Retail.

## Siti community {#community-sites}

Un sito community è un sito AEM creato utilizzando una semplice procedura guidata che consente di creare un sito web con numerose funzioni comuni precollegate al sito.

La [creazione guidata sito](sites-console.md):

* Assembla le caratteristiche del sito, in base alla [modello di sito community](sites.md) che
   * Costruito da [funzioni della community](#community-functions)
   * Facoltativo [gruppi comunitari](#communitygroups) caratteristica
* Utilizza le impostazioni per configurare:
   * Moderazione
   * Accesso
   * Traduzione
* Fornisce funzioni essenziali:
   * Design dinamico: Usi [Temi di Bootstrap twitter](https://getbootstrap.com)
   * Accesso: autoregistrazione, [accesso social](social-login.md), profili utente
   * Notifiche: I deputati vedono gli eventi rilevanti per loro
   * Messaggi: I membri possono inviare o ricevere messaggi all&#39;interno del sito della community
   * Ricerca: Possibilità di effettuare ricerche all&#39;interno del sito della community
   * Passaggio alla lingua: Possibilità di selezionare una lingua per un [sito multilingue](../../help/sites-administering/translation.md)
   * Amministrazione: Accesso dei membri autorizzati per moderare e gestire gli utenti all&#39;interno del sito della community
* Elimina molti passaggi di authoring a livello di pagina:
   * Branding: Caricamento facoltativo di un&#39;immagine banner da visualizzare su tutte le pagine del sito della community
   * Menu di navigazione: Sono disponibili collegamenti di navigazione per le funzioni incluse nel modello di sito community

Per scoprire la facilità di creazione rapida di un nuovo sito community, visita [Guida introduttiva ad AEM Communities](getting-started.md).

## Persistenza dei contenuti della community {#community-content-persistence}

Per migliorare le prestazioni e la sincronizzazione dei contenuti della community, AEM Communities richiede un archivio comune specifico per i contenuti generati dagli utenti (UGC) condivisi tra tutte le istanze di AEM (authoring e pubblicazione).

Il contenuto della community è facilmente accessibile tramite l’SRP (Storage Resource Provider), che fornisce un livello per separare l’accesso dalla topologia sottostante e supporta un archivio comune per UGC.

Per ulteriori informazioni sulla persistenza dei contenuti della community e sulle distribuzioni consigliate visita:

* [Archiviazione dei contenuti della community](working-with-srp.md): discute le opzioni di storage SRP disponibili per UGC
* [Topologie consigliate](topologies.md): discute le topologie in base al caso d’uso e alla scelta dell’SRP
* [Aggiornamento a AEM 6.3 Communities](upgrade.md): fornisce informazioni utili relative agli UGC quando si passa a AEM 6.3.

## Console di Communities {#communities-consoles}

Nell’ambiente di authoring, la console di navigazione globale consente di accedere alle [Console di Communities](consoles.md), che contiene:

* [Sites](sites-console.md) console

   * Creazione di siti
   * Modifica del sito
   * Gestione del sito
   * [Gruppi community](groups.md) console

* [Moderazione](moderation.md) console

   * Interfaccia utente comune per la moderazione in massa per gli ambienti di authoring e pubblicazione
   * Nuovi criteri di filtro

* [Membri e gruppi](members.md) console di gestione

   * Consente di creare e gestire utenti lato pubblicazione (membri) dall’ambiente di authoring
   * Consente di vietare i membri
   * Consente di creare e gestire gruppi di utenti lato pubblicazione (gruppi di membri) dall’ambiente di authoring

* [Rapporti](reports.md) console

   * Consente di generare rapporti su assegnazioni, post e visualizzazioni

* [Risorse](resources.md) console

   * Consente di creare risorse di abilitazione e percorsi di apprendimento
   * Consente di accedere ai rapporti sulle risorse di abilitazione e sui percorsi di apprendimento

La console strumenti globali consente di accedere ai seguenti strumenti di Communities:

* [Modelli di sito](tools.md#sitetemplatesconsole) console

   * Creare e gestire modelli di sito community

* [Modelli per gruppi](tools.md#grouptemplatesconsole) console

   * Creare e gestire modelli di gruppi di community

* [Funzioni della community](tools.md#communityfunctionsconsole) console

   * Creare e gestire funzioni di community

* [Configurazione dell&#39;archiviazione](tools.md#storageconfiguratonconsole) console

   * Seleziona e configura il [negozio comune](working-with-srp.md) per il sito

* [Guida dei componenti](components-guide.md)

   * un sito campione, [Componenti della community](http://localhost:4502/editor.html/content/community-components/en.html), che fornisce un esempio di tutti i componenti di Communities con la loro configurazione predefinita e la possibilità di sperimentare con essi

## Modelli per sito community {#community-site-templates}

La creazione di siti community si basa sulla selezione di un modello di sito community per configurare rapidamente un sito community indipendente da qualsiasi sito di esempio.

Un modello di sito community, composto da funzioni community e modelli di gruppo community, fornisce la struttura di un sito community che include login, profili utente, messaggistica, menu del sito, ricerca, temi e funzioni di branding.

Consulta la sezione [Console Modelli per siti](sites.md).

## Funzioni community {#community-functions}

Le funzioni previste per un’esperienza comunitaria sono ben note. Con AEM Communities, queste funzioni sono disponibili come blocchi predefiniti, noti come funzioni per community.

Le funzioni della community sono normali pagine AEM costituite da componenti collegati tra loro in una funzione facilmente incorporata in un modello di sito comune.

Consulta la sezione [Console Funzioni community](functions.md).

## Gruppi e modelli di gruppi della community {#community-groups-and-group-templates}

La funzione gruppi della community consente a una sottocommunity di creare in modo dinamico all’interno di un sito della community da parte di utenti autorizzati e membri della community sia dagli ambienti di authoring che di pubblicazione .

Dall’ambiente di authoring, i gruppi di community (sub-community) possono essere creati all’interno di un sito community esistente o nidificati all’interno di un gruppo esistente, quando la struttura del modello contiene il [Funzione Groups](functions.md#groups-function).

La creazione di un gruppo community richiede la selezione di un modello di gruppo community che fornisce la progettazione delle pagine del gruppo community. Quando una funzione Groups viene aggiunta a una struttura di modelli, viene configurata per specificare un modello di gruppo o per fornire una scelta di modelli al momento della creazione di un nuovo gruppo community.

Consulta anche:

* [Console dei gruppi del sito](groups.md) - creazione di sottocomunità nell’ambiente di authoring
* [Console Modelli di gruppo](tools-groups.md) - creazione della struttura del sito per i gruppi
* [Guida introduttiva ad AEM Communities](getting-started.md) - esercitazione per creare rapidamente un sito community con gruppi nidificati

## Componenti della community {#community-components}

La [componenti della community](author-communities.md) può essere utilizzato per aggiungere funzionalità di Communities a qualsiasi sito AEM.

La [guida ai componenti della community](components-guide.md) è disponibile per l’esplorazione interattiva dei componenti.

## Tipi di comunità {#types-of-communities}

### Community di coinvolgimento {#engagement-community}

Una community di coinvolgimento è un sito della community incentrato sul coinvolgimento dei clienti per informare, richiedere un feedback e consentire ai clienti di interagire come membri della community.

Le caratteristiche di una community di coinvolgimento possono includere:

* Accesso
* Messaggi
* Forum
* Commenti
* Recensioni
* Valutazioni
* Votazione
* Blog
* Gruppi
* Calendari
* Traduzione
* Moderazione
* Notifiche
* Punteggio e badge
* Reporting di Analytics

Per scoprire la facilità di creare rapidamente una nuova community di coinvolgimento, visita [Guida introduttiva ad AEM Communities](getting-started.md).

### Community di abilitazione {#enablement-community}

Una community di abilitazione è un sito della community che include funzionalità per l’apprendimento online.

Le caratteristiche di una community di abilitazione possono includere:

* Tutte le caratteristiche di un [community di coinvolgimento](#engagement-community)
* Possibilità di assegnare contenuti e risorse di apprendimento a membri e gruppi di membri
* Supporta contenuti SCORM, come quiz e test
* Monitoraggio del completamento delle assegnazioni
* Accesso a reporting e analisi
* La possibilità di conversare su una risorsa di apprendimento attraverso forum, messaggi, commenti e valutazioni

È possibile creare una community di abilitazione quando [Il componente aggiuntivo di abilitazione è configurato](enablement.md), che richiede licenze aggiuntive per l’utilizzo in un ambiente di produzione. Un sito della community di abilitazione includerà la [funzione di assegnazione](#community-functions).

Per scoprire la facilità di creazione di una nuova community di abilitazione, visita [Guida introduttiva ad AEM Communities per l&#39;abilitazione](getting-started-enablement.md).

## AEM Demo {#aem-demo-machine}

La [AEM Demo](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) gestisce ed esegue demo per AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Risorse](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Community](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [App](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) e [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), che spesso richiede una configurazione maggiore rispetto al semplice avvio di un&#39;istanza QuickStart. Il AEM Demo Machine configurerà ulteriori [infrastruttura](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) come i server MongoDB, Solr, MySQL, FFmpeg e email.

La AEM Demo Machine è costituita da

* A [interfaccia utente grafica](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Script Apache ANT con configurabile [proprietà](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) e [target](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Pacchetti per l&#39;installazione La AEM Demo Machine è stata testata con successo con CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 e AEM 6.3 su Windows, MacOS e Linux.

Il Demo Machine AEM richiede una licenza AEM valida.

>[!NOTE]
>
>Visualizzare un [introduzione video](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) alla AEM Demo Machine (13:26).

## Documentazione di AEM Communities {#aem-communities-documentation}

* Visita [Distribuzione di Communities](deploy-communities.md) per informazioni sulle distribuzioni consigliate.

* Visita [Amministrazione di siti di Communities](administer-landing.md) per ulteriori informazioni su come creare un sito community, aggiungere gruppi community, configurare modelli di sito community, moderare contenuti community, gestire membri, assegnare tag, notifiche, valutazione e badge,

* Visita [Sviluppo di Communities](communities.md) per informazioni sul framework dei componenti sociali (SCF) e sulla personalizzazione dei componenti e delle funzionalità di Communities.

* Visita [Authoring dei componenti di Communities](author-communities.md) per scoprire come creare e configurare i componenti di Communities.
