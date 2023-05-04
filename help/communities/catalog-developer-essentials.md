---
title: Nozioni di base sul catalogo
seo-title: Catalog Essentials
description: Panoramica del catalogo
seo-description: Catalog overview
uuid: 788512bb-fa38-48fb-a769-1eaae6bb95a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 542467ef-3793-4347-8424-c365c5a166f6
exl-id: 1e0a7cab-39b9-4c90-810c-c93fb76c3869
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 5%

---

# Nozioni di base sul catalogo {#catalog-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa pagina fornisce le informazioni essenziali per l’utilizzo della funzione di catalogo dei siti della community di abilitazione.

La funzione catalogo, se inclusa in un sito community, consente ai membri della community di sfogliare e selezionare le risorse di abilitazione elencate in un catalogo.

La [ `enablement catalog` component](catalog.md) consente ai membri della community di accedere a un catalogo di [risorse di abilitazione](resources.md). L’utilizzo dei tag AEM è una parte importante della gestione dell’aspetto delle risorse di abilitazione in un catalogo.

Vedi [Risorse di abilitazione assegnazione tag](tag-resources.md).

## Funzionalità di base per lato client {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/catalog</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>comprensivo</strong></a></td> 
   <td>No</td> 
  </tr> 
  <tr> 
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumb<br /> cq.social.enablement.hbs.catalog<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
  </tr> 
  <tr> 
   <td> <strong>modelli</strong></td> 
   <td> /libs/social/enablement/components/hbs/catalog/catalog.hbs<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/catalog/clientlibs/catalog.css</td> 
  </tr> 
  <tr> 
   <td><strong> proprietà</strong></td> 
   <td>Vedi <a href="catalog.md">Funzione catalogo</a></td> 
  </tr> 
 </tbody> 
</table>

## Funzioni di base per lato server {#essentials-for-server-side}

### Funzione Catalogo {#catalog-function}

Una struttura del sito community che include [Funzione di catalogo](functions.md#catalog-function)include un `enablement catalog` componente.

### Pre-filtri {#pre-filters}

Quando una funzione Catalogo è stata aggiunta a un sito community, è possibile limitare le risorse di abilitazione e i percorsi di apprendimento visualizzati nel catalogo specificando un filtro preliminare. A questo scopo, imposta le proprietà sull’istanza della risorsa del catalogo per il sito.

Utilizzando l’esempio di [Tutorial sull’abilitazione](getting-started-enablement.md):

* Autore
* Utilizzo [CRXDE](../../help/sites-developing/developing-with-crxde-lite.md)

   * Ad esempio [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)

* Passa alla risorsa del catalogo nella pagina del catalogo

   * Ad esempio `/content/sites/enable/en/catalog/jcr:content/content/primary/catalog`

* Aggiungi un nodo di filtri figlio

   * Seleziona la `catalog`nodo
   * Seleziona **[!UICONTROL Crea nodo]**

      * Nome: `filters`
      * Tipo: `nt:unstructured`
   * Seleziona **[!UICONTROL Salva tutto]**


* Aggiungi `se_resource-tags` della proprietà `filters` nodo

   * Seleziona la `filters` nodo
   * Aggiungi una proprietà multipla

      * Nome: `se_resource-tags`
      * Tipo: Stringa
      * Valore: *&lt;enter a=&quot;&quot; span=&quot;&quot; id=&quot;1&quot; translate=&quot;no&quot; />TagID](#pre-filter-tagids)>*[
      * Seleziona **[!UICONTROL Multi]**
      * Seleziona **[!UICONTROL Aggiungi]**

         * Nella finestra di dialogo a comparsa, seleziona `+` per aggiungere tag ID pre-filtro aggiuntivi

* Ripubblica il sito della community

![chlimage_1-189](assets/chlimage_1-189.png)

#### Tag ID pre-filtro {#pre-filter-tagids}

Il pre-filtro [TagIDs](../../help/sites-developing/framework.md#tagid) deve corrispondere esattamente ai tag applicati alle risorse di abilitazione. Sono visibili nella `resources` cartella del sito come valori della proprietà `se_resource-tags`.

![chlimage_1-190](assets/chlimage_1-190.png)

### API di riferimento {#reference-apis}

* [API di abilitazione](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API di reporting](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API di Reporting Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/model/api/package-summary.html)
