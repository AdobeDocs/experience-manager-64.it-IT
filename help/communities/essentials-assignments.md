---
title: Assignments Essentials
seo-title: Assignments Essentials
description: Panoramica della funzione Assegnazioni per le community di abilitazione
seo-description: Panoramica della funzione Assegnazioni per le community di abilitazione
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f

---


# Assignments Essentials {#assignments-essentials}

Questa pagina fornisce le informazioni essenziali per l&#39;utilizzo della funzione di assegnazione dei siti della community di [abilitazione](overview.md#enablement-community) .

La funzione di assegnazione consente di assegnare risorse di abilitazione e percorsi di apprendimento ai membri delle comunità di abilitazione.

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/myassign</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusa</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassign<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> proprietà</strong></td> 
   <td>Vedere Funzione <a href="assignments.md">Assegnazioni</a></td> 
  </tr>
 </tbody>
</table>

### Stato completamento e successo {#completion-and-success-status}

Lo stato di completamento e completamento viene utilizzato nei rapporti e nei banner di stato sulle assegnazioni.

Stato completamento:

* Non assegnato
* Non avviato (nuovo)
* In corso
* Completa

Stato di operazione riuscita:

* Sconosciuto
* Esito positivo
* Operazione non riuscita

Le uniche possibili combinazioni di Stato completamento e Successo sono:

| **Completamento** | **Completato** |
|---|---|
| Non iniziato | Sconosciuto |
| In corso | Sconosciuto |
| Completa | Esito positivo |
| Completa | Operazione non riuscita |

## Essentials for Server-Side {#essentials-for-server-side}

### Funzione Assegnazioni {#assignments-function}

Una struttura del sito community che include la funzione [](functions.md#assignments-function)Assegnazioni, include un ` [assignments](assignments.md)` componente configurato.

### API di riferimento {#reference-apis}

* [API di abilitazione](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API di reporting](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API di Reporting Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)