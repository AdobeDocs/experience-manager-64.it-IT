---
title: Blog Essentials
seo-title: Blog Essentials
description: Panoramica del blog
seo-description: Blog overview
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 3%

---

# Blog Essentials {#blog-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

A partire da AEM 6.1 Communities, un blog è un&#39;attività comunitaria. Gli articoli di blog vengono ora pubblicati dall’ambiente di pubblicazione, dove in precedenza, gli articoli di blog potevano essere creati solo nell’ambiente di authoring e pubblicati .

Gli articoli di blog possono ora essere creati da qualsiasi membro della comunità, a meno che non siano limitati ai membri privilegiati.

Questa pagina fornisce le informazioni essenziali per l’utilizzo della funzione blog.

>[!NOTE]
>
>L&#39;infrastruttura sottostante della funzione blog è la funzione di diario.

## Funzionalità di base per lato client {#essentials-for-client-side}

La funzione blog è composta da due componenti principali disponibili aggiungendo il [Funzione blog](functions.md#blog-function) oppure aggiungendo i componenti a una pagina in modalità di modifica dell’autore.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>comprensivo</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>modelli</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> proprietà</strong></td> 
   <td>vedere <a href="blog-feature.md">Funzione blog</a></td> 
  </tr>
 </tbody>
</table>

### Barra laterale blog {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**comprensivo**](scf.md#add-or-include-a-communities-component) | No |
| [**clientlibs**](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **modelli** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **proprietà** | vedere [Funzione blog](blog-feature.md) |

* [Personalizzazioni lato client](client-customize.md)

## Funzioni di base per lato server {#essentials-for-server-side}

* [API blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Endpoint blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Personalizzazioni lato server](server-customize.md)

### Funzione Blog {#blog-function}

Una struttura del sito community che include [Funzione Bog](functions.md#blog-function) avrà configurato `Blog` e `Blog Sidebar` componenti. La funzione Blog supporta l&#39;identificazione di un [gruppo utenti membro privilegiato](users.md#privileged-members-group).

### Accesso alle voci di blog (UGC) {#accessing-blog-entries-ugc}

UGC dovrebbe essere moderato utilizzando uno dei metodi standard per la moderazione.\
Vedi [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

A partire da AEM 6.1 Comunità, l&#39;uso di un [negozio comune](working-with-srp.md) per UGC include l&#39;accesso programmatico a UGC indipendentemente dall&#39;opzione di archiviazione scelta (come ASRP, MSRP o JSRP).

**La posizione e il formato dell’UGC nell’archivio sono soggetti a modifiche senza preavviso**.

Consulta:

* [Panoramica del provider di risorse di storage](srp.md) - introduzione e utilizzo dell&#39;archivio
* [Essenze SRP e UGC](srp-and-ugc.md) - Metodi e esempi di utilità SRP
* [Accesso a UGC con SRP](accessing-ugc-with-srp.md) - linee guida per la codifica
* [Refactoring di SocialUtils](socialutils.md) - mappatura di metodi di utilità obsoleti ai metodi di utilità SRP correnti

## Editore principale {#primary-publisher}

Quando la distribuzione è una farm di pubblicazione, è necessario identificare un editore principale che eseguirà il polling per gli articoli pianificati da pubblicare.

Vedi [Editore principale](deploy-communities.md#primary-publisher) per ulteriori dettagli.

## Consentire contenuti multimediali avanzati {#allowing-rich-media}

La piattaforma AEM blocca i collegamenti da altri siti web per prevenire attacchi XSS come descritto in

* [Protect contro lo scripting tra siti (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

A partire da AEM 6.2, le modifiche precedentemente necessarie per essere fatte manualmente sono incluse nel file di configurazione predefinito di AntiSamy.

I contenuti rich media vengono incorporati in un articolo del blog selezionando `Embed Media from External Sites` icona:  ![chlimage_1-471](assets/chlimage_1-471.png)
