---
title: Nozioni di base sul flusso di attività
seo-title: Nozioni di base sul flusso di attività
description: Elenco delle attività recenti eseguite da un membro o elenco delle attività recenti su un singolo thread di contenuto
seo-description: Elenco delle attività recenti eseguite da un membro o elenco delle attività recenti su un singolo thread di contenuto
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 2%

---


# Nozioni di base sul flusso di attività {#activity-stream-essentials}

Le attività di un membro della comunità firmato, come l&#39;invio a un forum o blog, vengono raccolte in un flusso che può essere filtrato e visualizzato in vari modi attraverso la configurazione del componente Flussi di attività.

La possibilità di seguire aggiunge un altro gruppo di attività quando i membri della comunità seguono postazioni di interesse o altri membri della comunità.

Tutti i siti [](overview.md#communitiessites) della community includono una pagina del profilo utente per il membro che ha effettuato l&#39;accesso, che mostrerà le attività dei membri allo stesso modo.

## Concetti {#concepts}

Un flusso *di* attività è l&#39;elenco delle attività recenti eseguite da un membro o un elenco delle attività recenti su un singolo thread di contenuto, ad esempio un argomento del forum o un blog.

Un membro può seguire un flusso di attività, seguendo un altro individuo o contenuto.

Un feed *di* notizie è un&#39;unione dei flussi di attività seguiti da un membro in un singolo flusso.

Un grafico [](essentials-socialgraph.md) sociale acquisisce le seguenti relazioni di un membro con un altro.

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activitystreams/components/hbs/activitystream</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusa</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> proprietà</strong></td> 
   <td>Vedere <a href="activities.md">Activity Streams Feature</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizzazioni lato client](client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [API Activity Streams](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [API Listener flussi di attività](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Personalizzazioni lato server](server-customize.md)

### Funzione Flusso attività {#activity-stream-function}

Una struttura del sito community che include la funzione [Flusso](functions.md#activity-stream-function)attività, include un `activity streams` componente configurato.
