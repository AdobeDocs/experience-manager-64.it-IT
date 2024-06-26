---
title: Best practice
seo-title: Best Practices
description: I team tecnici e di consulenza di Adobe hanno sviluppato un set completo di best practice per sviluppatori AEM
seo-description: Adobe Engineering and Consulting teams have developed a comprehensive set of best practices for AEM developers
uuid: f962c31f-8140-482f-b189-16376e23bfed
contentOwner: Justin Edelson
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 99678c1a-81f3-4fb3-bf73-98f0691c3fb6
exl-id: a2a299b5-a15a-47d9-a9d8-83f45917d080
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 13%

---

# Best practice{#best-practices}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Procedure consigliate per gli sviluppatori - Guida introduttiva {#best-practices-for-developers-getting-started}

I team tecnici e di consulenza di Adobe hanno sviluppato un set completo di best practice per sviluppatori AEM. Gli sviluppatori di Adobe aderiscono a queste best practice nello sviluppo di aggiornamenti di base AEM prodotto e codice cliente per le implementazioni dei clienti.

Prima di avviare il progetto di sviluppo AEM, controlla innanzitutto le seguenti best practice:

* [Pratiche di sviluppo](/help/sites-developing/development-practices.md)
* [Architettura dei contenuti](/help/sites-developing/content-architecture.md)
* [Architettura del software](/help/sites-developing/software-architecture.md)
* [Suggerimenti sulla codifica](/help/sites-developing/coding-tips.md)
* [Insidie del codice](/help/sites-developing/code-pitfalls.md)
* [Interazione JCR](/help/sites-developing/jcr-integration.md)
* [Bundle OSGi](/help/sites-developing/osgi-bundles.md)
* [Best practice per le API Java](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

### Informazioni aggiuntive sulle best practice {#additional-best-practices-information}

Le aree seguenti dispongono di documentazione specifica per lo sviluppo delle best practice:

* [Sites](#sites)
* [Communities](/help/sites-developing/best-practices.md#communities)
* [Strumenti/HTL](/help/sites-developing/best-practices.md#tooling-htl)

I documenti specifici sono descritti e collegati nelle tabelle che seguono.

Per le best practice relative all’amministrazione, alla distribuzione e alla manutenzione o all’authoring, consulta uno dei seguenti argomenti:

* [Best practice di amministrazione](/help/sites-administering/administer-best-practices.md)
* [Best practice di authoring](/help/sites-authoring/best-practices.md)
* [Best practice di distribuzione](/help/sites-deploying/best-practices.md)

## Sites {#sites}

La gestione e l’authoring dei contenuti del sito web sono caratterizzati da alcune best practice descritte di seguito:

<table> 
 <tbody>
  <tr>
   <td>Parte della teoria alla base dell’interfaccia utente standard touch.</td> 
   <td><p><a href="/help/sites-developing/touch-ui-concepts.md">Interfaccia touch: Concetti</a></p> <p><a href="/help/sites-developing/touch-ui-structure.md">Interfaccia touch: Struttura</a></p> </td> 
   <td>Questi documenti forniscono una panoramica dei concetti e della struttura dell’interfaccia touch.</td> 
  </tr>
  <tr>
   <td>Interfaccia touch: Personalizzazione delle console </td> 
   <td><a href="/help/sites-developing/customizing-consoles-touch.md">Personalizzazione delle console touch</a></td> 
   <td>Questo documento descrive il modo migliore per estendere le console per l’interfaccia touch.</td> 
  </tr>
  <tr>
   <td>Interfaccia touch: Personalizzazione dell’authoring delle pagine</td> 
   <td><a href="/help/sites-developing/customizing-page-authoring-touch.md">Personalizzazione dell’authoring delle pagine nell’interfaccia touch</a></td> 
   <td>Descrive come estendere l’authoring delle pagine per l’interfaccia touch.</td> 
  </tr>
  <tr>
   <td>Flussi di lavoro</td> 
   <td><a href="/help/sites-developing/workflows-best-practices.md">Sviluppo ed estensione dei flussi di lavoro</a></td> 
   <td><p>I flussi di lavoro ti consentono di automatizzare le attività di Adobe Experience Manager (AEM) e possono rappresentare una grande quantità di elaborazione che si verifica in un ambiente AEM, pertanto si consiglia vivamente di pianificare con attenzione le implementazioni dei flussi di lavoro.</p> </td> 
  </tr>
 </tbody>
</table>

## Communities {#communities}

[AEM Communities](/help/communities/overview.md) semplifica la creazione e la gestione delle comunità locali.

Alcune best practice per Communities sono descritte qui:

|  |  |  |
|---|---|---|
| Best practice per l’utilizzo di contenuti generati dagli utenti (UGC) | [Linee guida sulla codifica](/help/communities/code-guide.md) | Linee guida per lo sviluppo di un codice flessibile e portatile per [quadro della componente sociale](/help/communities/scf.md) (SCF) |
| Esempio di utilizzo dei componenti di Communities | [Guida ai componenti della community](/help/communities/components-guide.md) | Uno strumento di sviluppo interattivo. |

## Strumenti/HTL {#tooling-htl}

HTML Template Language (HTL) è un nuovo sistema di modelli HTML, introdotto con AEM 6.0. Sostituisce JSP e ESP come sistema di modelli preferito di AEM.

|  |  |  |
|---|---|---|
| Panoramica di HTL | [Panoramica e sintassi di HTL](https://helpx.adobe.com/experience-manager/htl/user-guide.html) | Questo documento descrive cosa è HTL, come passare a HTL, un progetto di esempio, sintassi, espressioni e istruzioni. |
| Utilizzo dell&#39;API in java | [API di utilizzo Java HTL](https://helpx.adobe.com/experience-manager/htl/using/use-api.html) | L’API di utilizzo Java HTL abilita un file HTL per accedere a metodi helper in una classe Java personalizzata. |

>[!NOTE]
>
>L’esercitazione in più parti potrebbe interessare alla best practice per impostare un nuovo progetto AEM, che descrive in dettaglio i componenti core, i modelli modificabili, le librerie client e lo sviluppo di componenti:\
>[Guida introduttiva ai AEM Sites: esercitazione WKND](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html)
