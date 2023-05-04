---
title: Nozioni di base sul flusso di attività
seo-title: Activity Stream Essentials
description: Elenco delle attività recenti eseguite da un membro o elenco delle attività recenti su un singolo thread di contenuto
seo-description: List of recent activites performed by a member or a list of recent activities on a single thread of content
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
exl-id: 74dcbefa-e670-419b-af9b-b3d3c593ebaa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 4%

---

# Nozioni di base sul flusso di attività {#activity-stream-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le attività di un membro della community firmato, come l’invio a un forum o blog, vengono raccolte in un flusso che può essere filtrato e visualizzato in vari modi tramite la configurazione del componente flussi di attività.

La possibilità di seguire aggiunge un altro insieme di attività quando i membri della comunità seguono post di interesse o altri membri della comunità.

Tutto [siti della community](overview.md#communitiessites) includere una pagina del profilo utente per il membro firmato che visualizzerà le attività membro nello stesso modo.

## Concetti {#concepts}

Un *flusso di attività* è l’elenco delle attività recenti eseguite da un membro o un elenco delle attività recenti relative a un singolo thread di contenuto, ad esempio un argomento del forum o un blog.

Un membro può seguire un flusso di attività seguendo un altro individuo o contenuto.

A *news feed* è un’unione dei flussi di attività seguiti da un membro in un singolo flusso.

A [grafico sociale](essentials-socialgraph.md) acquisisce le seguenti relazioni di un membro con un altro.

## Funzionalità di base per lato client {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activitystream/components/hbs/activitystream</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>comprensivo</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>modelli</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> proprietà</strong></td> 
   <td>Vedi <a href="activities.md">Funzionalità dei flussi di attività</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizzazioni lato client](client-customize.md)

## Funzioni di base per lato server {#essentials-for-server-side}

* [API per flussi di attività](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [API del listener dei flussi di attività](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Personalizzazioni lato server](server-customize.md)

### Funzione Flusso attività {#activity-stream-function}

Una struttura del sito community che include [Funzione Activity Stream](functions.md#activity-stream-function)include un `activity streams` componente.
