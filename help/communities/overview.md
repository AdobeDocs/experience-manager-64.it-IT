---
title: ' Panoramica di AEM Communities'
seo-title: ' Panoramica di AEM Communities'
description: Panoramica  funzioni e configurazione di AEM Communities
seo-description: Panoramica  funzioni e configurazione di AEM Communities
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 1375282df15b1a1a1ab5ed760190af8d6288970e
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 4%

---


#  AEM Communities Overview {#aem-communities-overview}

Adobe Experience Manager (AEM) Communities permette di creare rapidamente un sito di community on-premise con prestazioni ottimizzate e una migliore gestione del sito, che favorisce la conversione dei visitatori in membri attivi della community.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Caratteristiche delle community {#communities-features}

 AEM Communities consente lo sviluppo di una relazione con i visitatori del sito che li informa attraverso blog, domande e risposte e calendari dell&#39;evento, ottenendo allo stesso tempo informazioni approfondite attraverso forum, commenti e altri contenuti della community, spesso denominati contenuti generati dall&#39;utente (UGC).

Inoltre,  AEM Communities consente la moderazione da parte di membri fidati nell&#39;ambiente di pubblicazione, il login mediante social network con Twitter e Facebook, la traduzione in linea di contenuti della comunità, la creazione di gruppi di community dal sito della comunità pubblicato, il punteggio per l&#39;assegnazione di badge, la condivisione di file, le notifiche e i flussi di attività.

Le funzionalità Community possono essere dimostrate utilizzando la [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponibile pubblicamente su GitHub.com o con la nuova implementazione di riferimento We.Retail.

## Siti community {#community-sites}

Un sito community è un sito AEM creato utilizzando una semplice procedura guidata che consente di creare un sito Web con molte funzioni comuni già collegate al sito.

La [procedura guidata per la creazione del sito](sites-console.md):

* Assembla le funzionalità del sito, in base al [modello di sito community selezionato](sites.md) che è
   * Costruito da [funzioni della community](#community-functions)
   * Funzionalità [community group](#communitygroups) opzionale
* Utilizza le impostazioni per configurare:
   * Moderazione
   * Accesso
   * Traduzione
* Offre funzionalità essenziali:
   * Design reattivo: Utilizza [temi di Bootstrap Twitter](https://getbootstrap.com)
   * Login: Registrazione automatica, [login social](social-login.md), profili utente
   * Notifiche: I membri vedono gli eventi rilevanti per loro
   * Messaggi: I membri possono inviare o ricevere messaggi all&#39;interno del sito della community
   * Ricerca: Possibilità di effettuare ricerche all&#39;interno del sito della community
   * Passaggio alla lingua: Possibilità di selezionare una lingua per un [sito multilingue](../../help/sites-administering/translation.md)
   * Amministrazione: Accesso per i membri autorizzati per moderare e gestire gli utenti all&#39;interno del sito della community
* Elimina molti passaggi di authoring a livello di pagina:
   * Branding: Caricamento facoltativo di un&#39;immagine banner da visualizzare su tutte le pagine del sito della community
   * Menu di navigazione: I collegamenti di navigazione sono forniti per le funzioni incluse nel modello di sito community

Per provare la facilità di creare rapidamente un nuovo sito community, visita la [Guida introduttiva  AEM Communities](getting-started.md).

## Persistenza del contenuto della community {#community-content-persistence}

Per migliorare le prestazioni e la sincronizzazione del contenuto della community,  AEM Communities richiede uno store comune specifico per il contenuto generato dall&#39;utente (UGC) condiviso tra tutte le istanze AEM (autore e pubblicazione).

Il contenuto della community è facilmente accessibile tramite l&#39;SRP (Storage Resource Provider), che fornisce un livello per l&#39;accesso separato dalla topologia sottostante e supporta un archivio comune per UGC.

Per saperne di più sulla persistenza del contenuto della community e sulle distribuzioni consigliate, visita:

* [Archiviazione](working-with-srp.md) contenuto community: illustra le opzioni di storage SRP disponibili per UGC
* [Topologie](topologies.md) consigliate: illustra le topologie in base al caso di utilizzo e alla scelta SRP
* [Aggiornamento a AEM 6.3 Communities](upgrade.md): fornisce informazioni utili relative all&#39;UGC quando si passa alla AEM 6.3.

## Console community {#communities-consoles}

Nell&#39;ambiente di authoring, la console di navigazione globale consente di accedere alla [console Community](consoles.md), che contiene:

* La console [Sites](sites-console.md)

   * Creazione del sito
   * Modifica del sito
   * Gestione del sito
   * [Community ](groups.md) Groupsconsole

* [](moderation.md) Moderationconsole

   * Interfaccia utente comune per la moderazione in blocco per gli ambienti di creazione e pubblicazione
   * Nuovi criteri di filtro

* [Console di gestione Membri e ](members.md) Gruppi

   * Consente di creare e gestire utenti (membri) lato pubblicazione dall’ambiente di authoring
   * Consente di vietare i membri
   * Consente di creare e gestire gruppi di utenti lato pubblicazione (gruppi di membri) dall’ambiente di authoring

* [Console ](reports.md) Rapporti

   * Consente di generare rapporti su assegnazioni, post e viste

* [](resources.md) Resourcesconsole

   * Consente di creare risorse di abilitazione e percorsi di apprendimento
   * Fornisce l&#39;accesso ai rapporti sulle risorse di abilitazione e sui percorsi di apprendimento

La console degli strumenti globali consente di accedere ai seguenti strumenti di Communities:

* [Site ](tools.md#sitetemplatesconsole) Templatesconsole

   * Creazione e gestione di modelli di sito community

* [Group ](tools.md#grouptemplatesconsole) Templatesconsole

   * Creazione e gestione di modelli di gruppi di community

* [Community ](tools.md#communityfunctionsconsole) Functionsconsole

   * Creazione e gestione di funzioni per community

* [Console ](tools.md#storageconfiguratonconsole) di configurazione dello storage

   * Selezionare e configurare il [store comune](working-with-srp.md) per il sito

* [Guida dei componenti](components-guide.md)

   * Un sito di esempio, [Community Components](http://localhost:4502/editor.html/content/community-components/en.html), che fornisce un esempio di tutti i componenti Community con la configurazione predefinita e la possibilità di sperimentare con essi

## Modelli per sito community {#community-site-templates}

La creazione di siti community si basa sulla selezione di un modello di sito community per configurare rapidamente un sito community indipendente da qualsiasi sito di esempio.

Un modello di sito community, composto da funzioni per la community e modelli per gruppi di community, fornisce la struttura per un sito della community con login, profili utente, messaggistica, menu del sito, ricerca, temi e funzioni di branding.

Vedere la [console Modelli di sito](sites.md).

## Funzioni per community {#community-functions}

Le caratteristiche previste per un&#39;esperienza comunitaria sono ben note. Con  AEM Communities, queste funzioni sono disponibili come elementi costitutivi, noti come funzioni per community.

Le funzioni della community sono normali pagine AEM composte da componenti collegati tra loro in una funzione facilmente integrata in un modello di sito comune.

Vedere la [console Funzioni community](functions.md).

## Gruppi community e modelli di gruppo {#community-groups-and-group-templates}

La funzione per i gruppi della community è la possibilità che una sub-community venga creata in modo dinamico all&#39;interno di un sito della community da utenti autorizzati e membri della community sia dall&#39;ambiente di creazione che da quello di pubblicazione.

Dall&#39;ambiente di authoring, i gruppi di community (sub-community) possono essere creati all&#39;interno di un sito community esistente o nidificati all&#39;interno di un gruppo esistente, quando la struttura del modello contiene la funzione [Groups](functions.md#groups-function).

La creazione di un gruppo community richiede la selezione di un modello di gruppo community che fornisce la progettazione delle pagine del gruppo community. Quando una funzione Groups viene aggiunta a una struttura di modelli, viene configurata per specificare un modello di gruppo o per fornire una scelta di modelli al momento della creazione di un nuovo gruppo community.

Consulta anche:

* [Console](groups.md)  Gruppi del sito - creazione di sottocomunità nell’ambiente di authoring
* [Console](tools-groups.md)  Modelli per gruppi: creazione della struttura del sito per i gruppi
* [Guida introduttiva  AEM Communities](getting-started.md)  - esercitazione per creare rapidamente un sito community con gruppi nidificati

## Componenti community {#community-components}

I [componenti della community](author-communities.md) da cui viene creato un sito community possono essere utilizzati per aggiungere funzioni Community a qualsiasi AEM sito.

La [guida ai componenti della community ](components-guide.md) è disponibile per l&#39;esplorazione interattiva dei componenti.

## Tipi di community {#types-of-communities}

### Community di coinvolgimento {#engagement-community}

Una community di coinvolgimento è un sito della community incentrato sul coinvolgimento dei clienti per informare, richiedere feedback e consentire ai clienti di interagire come membri della community.

Le funzioni di una community di partecipazione possono includere:

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
* Punteggio e simboli
* Reporting di Analytics

Per provare la facilità di creare rapidamente una nuova community di coinvolgimento, visita la [Guida introduttiva  AEM Communities](getting-started.md).

### Community di abilitazione {#enablement-community}

Una community di abilitazione è un sito della community che include funzionalità per l&#39;apprendimento online.

Le funzioni di una community di abilitazione possono includere:

* Tutte le caratteristiche di una [community di coinvolgimento](#engagement-community)
* Possibilità di assegnare contenuti e risorse di apprendimento a membri e gruppi di membri
* Supporta il contenuto SCORM, come quiz e test
* Monitoraggio del completamento delle assegnazioni
* Accesso a reporting e analisi
* La possibilità di conversare su una risorsa di apprendimento attraverso forum, messaggi, commenti e valutazioni

Una community di abilitazione può essere creata quando il componente aggiuntivo [Abilitazione è configurato](enablement.md), il che richiede licenze aggiuntive da utilizzare in un ambiente di produzione. Un sito della community di abilitazione includerà la funzione [assegnazioni](#community-functions).

Per provare la facilità di creazione di una nuova community di abilitazione, visita la [Guida introduttiva  AEM Communities per Enablement](getting-started-enablement.md).

## AEM Demo {#aem-demo-machine}

La [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) gestisce ed esegue dimostrazioni per AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) e [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms), che spesso richiedono una configurazione maggiore rispetto al semplice avvio di QuickQuick Avvia istanza. Il AEM Demo Machine configurerà l&#39;infrastruttura [aggiuntiva](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) come i server MongoDB, Solr, MySQL, FFmpeg e email.

La AEM Demo Machine è costituita da

* A [interfaccia utente grafica](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Script Apache ANT con proprietà configurabili [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) e [target](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)
* Pacchetti da installare
La AEM Demo Machine è stata testata con CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2 e AEM 6.3 su Windows, MacOS e Linux.

AEM Demo Machine richiede una licenza AEM valida.

>[!NOTE]
>
>Visualizzare un [video introduttivo](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) sulla AEM Demo Machine (13:26).

##  documentazione AEM Communities {#aem-communities-documentation}

* Per informazioni sulle distribuzioni consigliate, visitare [Implementazione di Communities](deploy-communities.md).

* Per informazioni su come creare un sito community, aggiungere gruppi community, configurare modelli di sito community, moderare i contenuti della community, gestire membri, assegnare tag, notifiche, punteggio e simboli, visitate [Administering Communities Sites](administer-landing.md).

* Visitate [Developing Communities](communities.md) per informazioni sul framework dei componenti social network (SCF) e sulla personalizzazione dei componenti e delle funzioni di Communities.

* Per informazioni su come creare e configurare i componenti di Communities, visita [Componenti di authoring](author-communities.md).

