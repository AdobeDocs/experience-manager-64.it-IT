---
title: Revisioni Essenziali
seo-title: Reviews Essentials
description: Recensioni e componenti Riepilogo revisioni
seo-description: Reviews and Review Summary components
uuid: 540c106e-ee3b-4261-82b2-a909d254dbf7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 62669a9d-2107-4644-a4bf-143d0ac148b3
exl-id: ddd2bd98-b375-4d1e-b9d1-5efc3dbca398
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# Revisioni Essenziali {#reviews-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa funzione è costituita da due componenti che funzionano insieme: riepilogo delle revisioni e delle revisioni.

Revisioni è un componente composito basato su un [sistema di commento](essentials-comments.md) che contiene uno o più [valutazione](rating-basics.md) (tally) componenti.

Pubblicazione anonima di una revisione non supportata. Per aggiungere una revisione, i visitatori del sito devono registrarsi e accedere. Il visitatore connesso (membro) può aggiornare la propria revisione in qualsiasi momento.

## Funzionalità di base per lato client {#essentials-for-client-side}

### Recensioni {#reviews}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/review/components/hbs/review</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>comprensivo</strong></a></td> 
   <td>Sì - le proprietà sono modificabili in <i>progettazione </i>modalità</td> 
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td>cq.social.hbs.reviews</td> 
  </tr>
  <tr>
   <td> <strong>modelli</strong></td> 
   <td> /libs/social/reviews/components/hbs/reviews/reviews.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/review.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/status.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/toolbar.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/reviews/components/hbs/reviews/clientlibs/review.css</td> 
  </tr>
  <tr>
   <td><strong>proprietà</strong></td> 
   <td>Vedi <a href="reviews.md">Utilizzo delle revisioni</a></td> 
  </tr>
 </tbody>
</table>

### Riepilogo recensioni {#review-summary}

| **resourceType** | social/review/components/hbs/summary |
|---|---|
| [**comprensivo**](scf.md#add-or-include-a-communities-component) | Sì - le proprietà sono modificabili nel modo *design *mode |
| [**clientlibs**](client-customize.md#clientlibs-for-scf) | cq.social.hbs.reviews |
| **modelli** | /libs/social/reviews/components/hbs/summary/summary.hbs |
| **css** | /libs/social/reviews/components/hbs/reviews/clientlibs/review.css |
| **proprietà** | Vedi [Utilizzo delle revisioni](reviews.md) |

* [Personalizzazioni lato client](client-customize.md)

## Funzioni di base per lato server {#essentials-for-server-side}

* [API di revisione](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/review/client/api/package-summary.html)

* [Endpoint di revisione](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/review/client/endpoints/package-summary.html)

* [Personalizzazioni lato server](server-customize.md)

### Accesso alle revisioni pubblicate (UGC) {#accessing-posted-reviews-ugc}

UGC dovrebbe essere moderato utilizzando uno dei metodi standard per la moderazione.\
Vedi [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

A partire da AEM 6.1 Comunità, l&#39;uso di un [negozio comune](working-with-srp.md) per UGC include l&#39;accesso programmatico a UGC indipendentemente dall&#39;opzione di archiviazione scelta (come ASRP, MSRP o JSRP).

**La posizione e il formato dell’UGC nell’archivio sono soggetti a modifiche senza preavviso**.

Consulta:

* [Panoramica del provider di risorse di storage](srp.md) - introduzione e utilizzo dell&#39;archivio
* [Essenze SRP e UGC](srp-and-ugc.md) - Metodi e esempi di utilità SRP
* [Accesso a UGC con SRP](accessing-ugc-with-srp.md) - linee guida per la codifica
* [Refactoring di SocialUtils](socialutils.md) - mappatura di metodi di utilità obsoleti ai metodi di utilità SRP correnti
