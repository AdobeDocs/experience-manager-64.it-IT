---
title: Componenti, funzioni e funzioni di base
seo-title: Component, Function and Feature Essentials
description: Funzionamento di siti, modelli e gruppi community
seo-description: How community sites, templates, and groups function
uuid: 6edfca2d-fe5b-4261-b033-51dc2f9dbfd7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 2d308756-79d1-4d69-b51c-d4b6e692a137
exl-id: bde29d3a-8bc8-4c30-b764-a2fa1ac34069
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 18%

---

# Componenti, funzioni e funzioni di base {#component-function-and-feature-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le funzioni di AEM Communities richiedono ai visitatori del sito di diventare membri e di accedere al [sito della community](overview.md#communitiessites) prima di poter pubblicare contenuti. Pertanto, [modelli di sito community](sites.md), da cui proviene un sito della comunità [creato](sites-console.md), sono progettati per includere una funzione di accesso, nonché profili utente, messaggistica, ricerca, moderazione e traduzione.

Un sito community supporterà i membri che creano gruppi community quando [funzione dei gruppi community](functions.md#groups-function) è incluso nel modello di sito community selezionato.

Di seguito sono riportati i collegamenti alle informazioni essenziali per i componenti, le funzioni e le funzioni di Communities.

## Componenti di base {#base-components}

* [Commenti](essentials-comments.md)
* [Recensioni](reviews-basics.md)
* [Tally](tally.md)

   * [Con Mi piace](essentials-liking.md)
   * [Valutazione](rating-basics.md)
   * [Votazione](essentials-voting.md)
   * *Sondaggio (non più disponibile)*

## Componenti con funzioni {#components-with-functions}

* [Flussi attività](essentials-activities.md)
* [Assegnazioni](essentials-assignments.md)
* [Blog](blog-developer-basics.md) ( `Journal`)

* [Calendario](calendar-basics-for-developers.md)
* [Catalogo](catalog-developer-essentials.md)
* [Contenuto in primo piano](essentials-featured.md)
* [Libreria file](essentials-file-library.md)
* [Forum](essentials-forum.md)
* [Gruppi](essentials-groups.md)
* [Ideazione](ideation.md)
* [Classifica](leaderboard.md)
* [Domande e risposte](qna-essentials.md) `(QnA)`

## Funzioni {#features}

* [Librerie client](clientlibs.md)
* [Siti community](sites-for-developers.md)
* [Eventi OSGi component](events.md)
* [Caricamento laterale componente](sideloading.md)
* [Messaggi](essentials-messaging.md)
* [Editor Rich Text](rte.md)
* [Punteggio e badge](configure-scoring.md)
* [Ricerca](search-implementation.md)
* [Grafico social](essentials-socialgraph.md)
* [Provider di risorse di storage](srp-and-ugc.md) `(SRP)`

* [Assegnazione dei tag](tag.md)

## Javadocs {#javadocs}

La [javadocs online](../../help/sites-developing/reference-materials.md) riflettono le API disponibili nella versione 6.3 di AEM.\
Le API di Communities sono in `com.adobe.cq.social.*` pacchetti.

Per ogni [feature pack](deploy-communities.md#latestfeaturepack), viene reso disponibile un jar javadoc. Per ulteriori informazioni, visita [Utilizzo di Maven per Communities](maven.md#javadocs).

## Informazioni aggiuntive {#additional-information}

* [Quadro dei componenti sociali (SCF)](scf.md)

   * [Personalizzazioni lato client](client-customize.md)
   * [Personalizzazioni lato server](server-customize.md)
   * [Panoramica del provider di risorse di storage](srp.md)

* [Linee guida sulla codifica](code-guide.md)
* [Esercitazioni](tutorials.md)
* [Risoluzione dei problemi](troubleshooting.md)
