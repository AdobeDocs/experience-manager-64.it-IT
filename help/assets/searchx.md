---
title: Estensione della ricerca delle risorse
description: Estendi le funzionalità di ricerca di [!DNL Experience Manager] Le risorse oltre a quelle predefinite ricercano le risorse in base alle stringhe.
contentOwner: AG
feature: Search
role: Developer
exl-id: d68c735f-2699-4923-a7e7-4d1356eae335
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 15%

---

# Estensione della ricerca delle risorse {#extending-assets-search}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi estendere le funzionalità di ricerca di Adobe Experience Manager Assets. Fuori dalla scatola, [!DNL Experience Manager] Le risorse vengono cercate in base alle stringhe.

La ricerca viene eseguita tramite l’interfaccia QueryBuilder per personalizzare la ricerca con diversi predicati. Puoi sovrapporre il set predefinito di predicati nella seguente directory: `/apps/dam/content/search/searchpanel/facets`.

Puoi anche aggiungere altre schede al [!DNL Experience Manager] Pannello di amministrazione delle risorse.

>[!CAUTION]
>
>A partire da [!DNL Experience Manager] 6.4, l’interfaccia classica è obsoleta. Per l&#39;annuncio, vedi [Funzioni obsolete e rimosse](../release-notes/deprecated-removed-features.md). È consigliabile utilizzare l’interfaccia touch. Per le personalizzazioni, consulta [Facet di ricerca](search-facets.md).

## Sovrapposizione {#overlaying}

Per sovrapporre i predicati preconfigurati, copia il `facets` nodo da `/libs/dam/content/search/searchpanel` a `/apps/dam/content/search/searchpanel/` o specificare un altro `facetURL` nella configurazione del pannello di ricerca (l&#39;impostazione predefinita è `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>Per impostazione predefinita, la struttura della directory sotto / `apps` non esiste e deve essere creato. Assicurati che i tipi di nodo corrispondano a quelli sotto / `libs`.

## Aggiunta di schede {#adding-tabs}

Puoi aggiungere ulteriori schede Ricerca configurandole nella [!DNL Experience Manager] Amministratore risorse. Per creare schede aggiuntive:

1. Creare la struttura della cartella `/apps/wcm/core/content/damadmin/tabs,`se non esiste già e copia il `tabs` nodo da `/libs/wcm/core/content/damadmin` e incollalo.
1. Crea e configura la seconda scheda, come desiderato.

   >[!NOTE]
   >
   >Quando crei un secondo siteadminsearchpanel, assicurati di impostare un `id` al fine di evitare conflitti di modulo.

## Creazione di predicati personalizzati {#creating-custom-predicates}

[!DNL Experience Manager] Le risorse sono dotate di un set di predicati predefiniti che possono essere utilizzati per personalizzare una pagina Condivisione risorse. La personalizzazione di una Condivisione risorse in questo modo è descritta in [Creazione e configurazione di una pagina Condivisione risorse](assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Oltre a utilizzare predicati preesistenti, [!DNL Experience Manager] gli sviluppatori possono anche creare predicati personalizzati utilizzando [API di Query Builder](/help/sites-developing/querybuilder-api.md).

La creazione di predicati personalizzati richiede conoscenze di base [Framework dei widget](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html).

La best practice prevede di copiare e regolare un predicato esistente. I predicati di esempio si trovano in `/libs/cq/search/components/predicates`.

### Esempio: Creare un predicato di proprietà semplice {#example-build-a-simple-property-predicate}

Per creare un predicato di proprietà:

1. Crea una cartella di componenti nella directory dei progetti, ad esempio `/apps/geometrixx/components/titlepredicate`.
1. Aggiungi `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Aggiungi `titlepredicate.jsp`.

   ```xml
   <%--
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
   
       });
   
   </script>
   ```

1. Per rendere disponibile il componente, devi essere in grado di modificarlo. Per rendere modificabile un componente, in CRXDE aggiungi un nodo `cq:editConfig` di tipo primario `cq:EditConfig`. Per rimuovere i paragrafi, aggiungi una proprietà con più valori `cq:actions` che presenta un singolo valore **DELETE**.
1. Passa al browser e alla pagina di esempio (ad esempio, `press.html`) passa alla modalità progettazione e attiva il nuovo componente per il sistema paragrafo predicato (ad esempio, **sinistra**).

1. In **Modifica** il nuovo componente è ora disponibile nella barra laterale (nella sezione **Ricerca** gruppo). Inserisci il componente nel **Predicati** e digitare una parola di ricerca, ad esempio, **Rombo** e fare clic sulla lente di ingrandimento per avviare la ricerca.

   >[!NOTE]
   >
   >Durante la ricerca, assicurati di digitare esattamente il termine, compreso il caso corretto.

### Esempio: Creare un predicato di gruppo semplice {#example-build-a-simple-group-predicate}

Per creare un predicato di gruppo:

1. Crea una cartella di componenti nella directory dei progetti, ad esempio `/apps/geometrixx/components/picspredicate`.
1. Aggiungi `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Aggiungi `titlepredicate.jsp`:

   ```java
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
   
       });
   ```

1. Per rendere disponibile il componente, devi essere in grado di modificarlo. Per rendere modificabile un componente, in CRXDE aggiungi un nodo `cq:editConfig` di tipo primario `cq:EditConfig`. Per rimuovere i paragrafi, aggiungi una proprietà con più valori `cq:actions` che presenta un singolo valore `DELETE`.
1. Passa al browser e alla pagina di esempio (ad esempio, `press.html`) passa alla modalità progettazione e attiva il nuovo componente per il sistema paragrafo predicato (ad esempio, **sinistra**).
1. In **Modifica** il nuovo componente è ora disponibile nella barra laterale (nella sezione **Ricerca** gruppo). Inserisci il componente nel **Predicati** colonna.

### Widget Predicate installati {#installed-predicate-widgets}

I seguenti predicati sono disponibili come widget ExtJS preconfigurati.

### PredicatoTestoCompleto {#fulltextpredicate}

| Proprietà | Tipo | Descrizione |
|---|---|---|
| predicateName | Stringa | Nome del predicato. Impostazione predefinita `fulltext` |
| searchCallback | Funzione | Callback per attivare la ricerca sull&#39;evento `keyup`. Impostazione predefinita `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Proprietà | Tipo | Descrizione |
|---|---|---|
| predicateName | Stringa | Nome del predicato. Impostazione predefinita `property` |
| propertyName | Stringa | Nome della proprietà JCR. Impostazione predefinita `jcr:title` |
| defaultValue | Stringa | Valore predefinito. |

### PathPredicate {#pathpredicate}

| Proprietà | Tipo | Descrizione |
|---|---|---|
| predicateName | Stringa | Nome del predicato. Impostazione predefinita `path` |
| rootPath | Stringa | Percorso principale del predicato. Impostazione predefinita `/content/dam` |
| pathFieldPredicateName | Stringa | Impostazione predefinita `folder` |
| showFlatOption | Booleano | Flag per visualizzare la casella di controllo `search in subfolders`. Predefinito su true. |

### DatePredicate {#datepredicate}

| Proprietà | Tipo | Descrizione |
|---|---|---|
| predicateName | Stringa | Nome del predicato. Impostazione predefinita `daterange` |
| nomeproprietà | Stringa | Nome della proprietà JCR. Impostazione predefinita `jcr:content/jcr:lastModified` |
| defaultValue | Stringa | Valore predefinito precompilato |

### OptionsPredicate {#optionspredicate}

| Proprietà | Tipo | Descrizione |
|---|---|---|
| titolo | Stringa | Aggiunge un titolo superiore aggiuntivo |
| predicateName | Stringa | Nome del predicato. Impostazione predefinita `daterange` |
| nomeproprietà | Stringa | Nome della proprietà JCR. Impostazione predefinita `jcr:content/metadata/cq:tags` |
| collassare | Stringa | Comprimi livello. Impostazione predefinita `level1` |
| triggerSearch | Booleano | Flag per l&#39;attivazione della ricerca su controllo. Predefinito su false |
| searchCallback | Funzione | Callback per attivare la ricerca. Impostazione predefinita `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Numero | Timeout prima dell&#39;attivazione di searchCallback. Il valore predefinito è 800 ms |

## Personalizzazione dei risultati di ricerca {#customizing-search-results}

La presentazione dei risultati di ricerca in una pagina Condivisione risorse è gestita dall’obiettivo selezionato. [!DNL Experience Manager] Le risorse sono dotate di una serie di obiettivi predefiniti che possono essere utilizzati per personalizzare una pagina Condivisione risorse. La personalizzazione di una Condivisione risorse in questo modo è descritta in [Creazione e configurazione di una pagina Condivisione risorse](assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Oltre a utilizzare ottiche preesistenti, [!DNL Experience Manager] gli sviluppatori possono anche creare le proprie lenti.
