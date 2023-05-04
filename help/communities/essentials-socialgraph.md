---
title: Nozioni di base sul grafico social
seo-title: Social Graph Essentials
description: seguire la panoramica del componente e del componente seguente
seo-description: follow component and following component overview
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
exl-id: 55aa015e-e0e4-411e-8e28-75006ae3090b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 4%

---

# Nozioni di base sul grafico social {#social-graph-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La capacità di un membro della Comunità di seguire [attività](essentials-activities.md) oltre a essere seguito è costituito da due componenti:

La `follow`Il componente deve essere associato a un&#39;altra risorsa e questa associazione è già stabilita per i membri e le funzionalità esistenti di Communities in un [sito della community](overview.md#communitiessites).

La `following`In questo componente sono elencati i membri che seguono il membro corrente o che sono seguiti dal membro corrente. Questo grafico social delle relazioni tra i membri è incluso nel profilo utente stabilito per un sito community.

## Funzionalità di base per lato client {#essentials-for-client-side}

### Segue {#following}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/socialgrafo/componenti/hbs/relazioni</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>comprensivo</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.socialgraph</td> 
  </tr>
  <tr>
   <td> <strong>modelli</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td> 
  </tr>
  <tr>
   <td><strong> proprietà</strong></td> 
   <td>Vedi <a href="socialgraph.md">Utilizzo di Social Graph</a></td> 
  </tr>
  <tr>
   <td><strong> facoltativo<br /> property</strong></td> 
   <td>
    <ul> 
     <li>Nome: <strong><code>outgoing</code></strong></li> 
     <li>Tipo: Booleano</li> 
     <li>Valore:<br /> 
      <ul> 
       <li><i>true </i>- il <code>following</code> il componente elencherà i membri che hanno attualmente effettuato l’accesso <code>follows</code></li> 
       <li><i>false </i>- il <code>following</code> il componente elencherà i membri che <code>follow </code>membro attualmente connesso</li> 
      </ul> </li> 
    </ul> <p>Predefinito su <i>true</i> se la proprietà è mancante. Al momento, non è possibile impostare questa proprietà utilizzando la finestra di dialogo di modifica in modalità di creazione. La proprietà deve essere aggiunta a un'istanza del <code>following </code>nodo che utilizza <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>.</p> </td> 
  </tr>
 </tbody>
</table>

### Segui {#follow}

| **resourceType** | social/socialgraph/components/hbs/segue |
|---|---|
| [**comprensivo**](scf.md#add-or-include-a-communities-component) | No |
| **modelli** | /libs/social/socialgraph/components/hbs/following/following.hbs |
| **css** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [Personalizzazioni lato client](client-customize.md)

## Funzioni di base per lato server {#essentials-for-server-side}

* [API per grafico social network](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Endpoint di grafico social](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Personalizzazioni lato server](server-customize.md)
