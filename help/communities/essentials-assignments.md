---
title: Componenti di base per le assegnazioni
seo-title: Assignments Essentials
description: Panoramica della funzione Assegnazioni per le community di abilitazione
seo-description: Assignments feature overview for enablement communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 14%

---

# Componenti di base per le assegnazioni {#assignments-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa pagina fornisce le informazioni essenziali per l&#39;utilizzo della funzione di assegnazione di [comunità di abilitazione](overview.md#enablement-community) siti.

La funzione assegnazioni consente di assegnare risorse di abilitazione e percorsi di apprendimento ai membri delle comunità di abilitazione.

## Funzionalità di base per lato client {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>comprensivo</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumb<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
  </tr>
  <tr>
   <td> <strong>modelli</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> proprietà</strong></td> 
   <td>Vedi <a href="assignments.md">Funzione Assegnazioni</a></td> 
  </tr>
 </tbody>
</table>

### Stato di completamento e successo {#completion-and-success-status}

Lo stato Completato e Completato viene utilizzato nei rapporti e nei banner di stato Assegnazioni.

Stato completamento:

* Non assegnato
* Non avviato (nuovo)
* In corso
* Completa

Stato di operazione riuscita:

* Sconosciuto
* Esito positivo
* Operazione non riuscita

Le uniche combinazioni possibili di stato di completamento e successo sono:

| **Completamento** | **Completato** |
|---|---|
| Non iniziato | Sconosciuto |
| In corso | Sconosciuto |
| Completa | Esito positivo |
| Completa | Operazione non riuscita |

## Funzioni di base per lato server {#essentials-for-server-side}

### Funzione Assegnazioni {#assignments-function}

Una struttura del sito community che include [Funzione Assegnazioni](functions.md#assignments-function)include un ` [assignments](assignments.md)` componente.

### API di riferimento {#reference-apis}

* [API di abilitazione](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API di reporting](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API di Reporting Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
