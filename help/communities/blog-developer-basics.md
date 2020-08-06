---
title: Blog Essentials
seo-title: Blog Essentials
description: Panoramica del blog
seo-description: Panoramica del blog
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---


# Blog Essentials {#blog-essentials}

A partire da AEM 6.1 Communities, un blog è un&#39;attività della community. Gli articoli dei blog vengono ora pubblicati dall&#39;ambiente di pubblicazione, dove in precedenza, gli articoli dei blog potevano essere creati solo nell&#39;ambiente di authoring e pubblicati.

Gli articoli di blog possono ora essere creati da qualsiasi membro della community, a meno che non siano limitati ai membri privilegiati.

Questa pagina contiene le informazioni essenziali per l’utilizzo della funzione blog.

>[!NOTE]
>
>L&#39;infrastruttura sottostante della funzione blog è la funzione journal.

## Essentials for Client-Side {#essentials-for-client-side}

La funzione blog è composta da due componenti principali disponibili aggiungendo la funzione [](functions.md#blog-function) Blog o aggiungendo i componenti a una pagina in modalità di modifica dell’autore.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusa</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.Voto<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> proprietà</strong></td> 
   <td>consulta Funzione <a href="blog-feature.md">Blog</a></td> 
  </tr>
 </tbody>
</table>

### Barra laterale blog {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**inclusa **](scf.md#add-or-include-a-communities-component) | No |
| [**clientllibs **](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **proprietà** | consulta Funzione [Blog](blog-feature.md) |

* [Personalizzazioni lato client](client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [API blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Endpoint blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Personalizzazioni lato server](server-customize.md)

### Funzione Blog {#blog-function}

Una struttura del sito community che include la funzione [](functions.md#blog-function) Bog avrà configurato `Blog` e `Blog Sidebar` componenti. La funzione Blog supporta l&#39;identificazione di un gruppo [utenti membro](users.md#privileged-members-group)privilegiato.

### Accesso a voci di blog (UGC) {#accessing-blog-entries-ugc}

UGC deve essere moderato utilizzando uno dei metodi standard per la moderazione.\
Consultate [Moderazione del contenuto](moderate-ugc.md)generato dall&#39;utente.

A partire da AEM 6.1 Communities, l&#39;uso di uno store [](working-with-srp.md) comune per UGC include l&#39;accesso programmatico a UGC indipendentemente dall&#39;opzione di storage scelta (come ASRP, MSRP o JSRP).

**La posizione e il formato dell’UGC nel repository sono soggetti a modifiche senza preavviso**.

Consulta:

* [Panoramica](srp.md) del provider di risorse di storage - introduzione e utilizzo del repository
* [Caratteristiche essenziali di SRP e UGC](srp-and-ugc.md) - Metodi e esempi di utilità SRP
* [Accesso a UGC con SRP](accessing-ugc-with-srp.md) - linee guida di codifica
* [Refactoring](socialutils.md) SocialUtils - mappatura di metodi di utilità obsoleti ai metodi di utilità SRP correnti

## Editore principale {#primary-publisher}

Quando la distribuzione è una farm di pubblicazione, è necessario identificare un editore principale che eseguirà il sondaggio per gli articoli pianificati per la pubblicazione.

Per ulteriori informazioni, vedere Editore [](deploy-communities.md#primary-publisher) principale.

## Consentire contenuti multimediali avanzati {#allowing-rich-media}

La piattaforma AEM blocca i collegamenti da altri siti Web per prevenire attacchi XSS come descritto in

* [Protect contro lo scripting tra siti (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

A partire dal AEM 6.2, le modifiche precedentemente richieste per essere effettuate manualmente sono incluse nel file di configurazione AntiSamy predefinito.

I contenuti multimediali avanzati vengono incorporati in un articolo di blog selezionando l&#39; `Embed Media from External Sites` icona:  ![chlimage_1-471](assets/chlimage_1-471.png)

