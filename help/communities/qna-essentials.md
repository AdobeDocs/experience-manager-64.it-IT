---
title: QnA Essentials
seo-title: QnA Essentials
description: Funzione forum Domande e risposte
seo-description: Funzione forum Domande e risposte
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 2%

---


# QnA Essentials {#qna-essentials}

Questa pagina contiene le informazioni essenziali per l’utilizzo della funzione forum Domande e risposte (QnA).

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> resourceType</td> 
   <td>social/qna/components/hbs/qnaforum</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">inclusa</a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientllibs</a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.registration<br /> cq.social.hbs.qna</td> 
  </tr>
  <tr>
   <td> templates</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td> 
  </tr>
  <tr>
   <td> css</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td> 
  </tr>
  <tr>
   <td> proprietà</td> 
   <td>Vedere <a href="working-with-qna.md">QnA Forum Feature</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizzazioni lato client](client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [API QnA](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [Endpoint QnA](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Personalizzazioni lato server](server-customize.md)

### Funzione D/R {#qna-function}

Una struttura del sito community che include la [funzione QnA](functions.md#qna-function) avrà un componente `QnA` configurato, nonché impostazioni che influiscono sulla moderazione e l&#39;assegnazione di tag. La funzione QnA supporta l&#39;identificazione di un [gruppo di utenti con privilegi](users.md#privileged-members-group).

### Accesso ai post di forum QnA (UGC) {#accessing-qna-forum-posts-ugc}

UGC deve essere moderato utilizzando uno dei metodi standard per la moderazione.\
Consultate [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

A partire da AEM 6.1 Communities, l&#39;utilizzo di un [store comune](working-with-srp.md) per UGC include l&#39;accesso programmatico a UGC indipendentemente dall&#39;opzione di storage scelta (come ASRP, MSRP o JSRP).

**La posizione e il formato dell’UGC nel repository sono soggetti a modifiche senza preavviso**.

Consulta:

* [Panoramica](srp.md)  del provider di risorse di storage - introduzione e utilizzo del repository
* [Funzioni essenziali](srp-and-ugc.md)  SRP e UGC - Metodi di utilità SRP ed esempi
* [Accesso a UGC con SRP](accessing-ugc-with-srp.md)  - linee guida di codifica
* [Refactoring](socialutils.md)  SocialUtils: mappatura di metodi di utilità obsoleti ai metodi di utilità SRP correnti

