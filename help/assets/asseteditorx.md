---
title: Estendi editor risorse
description: Scopri come estendere le funzionalità di Asset Editor utilizzando componenti personalizzati.
contentOwner: AG
feature: Developer Tools
role: User,Admin
exl-id: 1e02a2f6-8194-46b9-b418-87103c3f4a69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 14%

---

# Estendi editor risorse {#extending-asset-editor}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’Editor risorse è la pagina che si apre quando si fa clic su una risorsa reperibile tramite Condivisione risorse per consentire all’utente di modificare tali aspetti della risorsa quali metadati, miniature, titoli e tag.

La configurazione dell’editor che utilizza i componenti di modifica predefiniti è descritta in [Creazione e configurazione di una pagina dell’Editor risorse](assets-finder-editor.md#creating-and-configuring-an-asset-editor-page).

Oltre a utilizzare componenti dell’editor preesistenti, gli sviluppatori Adobe Experience Manager possono anche creare i propri componenti.

## Creazione di un modello di Editor risorse {#creating-an-asset-editor-template}

Le pagine di esempio seguenti sono incluse in geometrixx:

* Pagina di esempio di Geometrixx: `/content/geometrixx/en/press/asseteditor.html`
* Modello di esempio: `/apps/geometrixx/templates/asseteditor`
* Componente pagina di esempio: `/apps/geometrixx/components/asseteditor`

### Configurazione di Clientlib {#configuring-clientlib}

[!DNL Experience Manager Assets] i componenti utilizzano un’estensione della clientlib di modifica WCM. Le clientlibs di solito sono caricate in `init.jsp`.

Confrontato con il caricamento clientlib predefinito (nei’ `init.jsp`), [!DNL Assets] Il modello deve avere i seguenti elementi:

* Il modello deve includere `cq.dam.edit` clientlib (anziché `cq.wcm.edit`).

* Per poter eseguire il rendering di predicati, azioni e obiettivi, clientlib deve essere incluso anche in modalità WCM disabilitata (ad esempio, caricata **al momento della pubblicazione**).

Nella maggior parte dei casi, copia il campione esistente `init.jsp` (`/apps/geometrixx/components/asseteditor/init.jsp`) dovrebbe soddisfare queste esigenze.

### Configurazione delle azioni JS {#configuring-js-actions}

Alcuni dei [!DNL Assets] i componenti richiedono funzioni JS definite in `component.js`. Copia questo file nella directory dei componenti e collegalo.

```javascript
<script type="text/javascript" src="<%= component.getPath() %>/component.js"></script>
```

L&#39;esempio carica questa origine JavaScript in `head.jsp`(`/apps/geometrixx/components/asseteditor/head.jsp`).

### Fogli di stile aggiuntivi {#additional-style-sheets}

Alcuni dei [!DNL Assets] i componenti utilizzano [!DNL Experience Manager] libreria dei widget. Per eseguire correttamente il rendering nel contesto del contenuto, è necessario caricare un foglio di stile aggiuntivo. Il componente di azione tag ne richiede un altro.

```css
<link href="/etc/designs/geometrixx/ui.widgets.css" rel="stylesheet" type="text/css">
```

### Foglio di stile di Geometrixx {#geometrixx-style-sheet}

I componenti della pagina di esempio richiedono che tutti i selettori inizino con `.asseteditor` di `static.css` (`/etc/designs/geometrixx/static.css`). Procedure consigliate: Copia tutto `.asseteditor` seleziona il foglio di stile e regola le regole nel modo desiderato.

### Selettore modulo: Adeguamenti per le risorse eventualmente caricate {#formchooser-adjustments-for-eventually-loaded-resources}

L’Editor risorse utilizza il Selettore moduli, che consente di modificare le risorse, in questo caso le risorse, nella stessa pagina del modulo semplicemente aggiungendo un selettore di moduli e il percorso del modulo all’URL della risorsa.

Ad esempio:

* Pagina modulo normale: [http://localhost:4502/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/geometrixx/en/press/asseteditor.html)
* Risorsa caricata nella pagina del modulo: [http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html)

Le maniglie del campione in `head.jsp` (`/apps/geometrixx/components/asseteditor/head.jsp`) effettua le seguenti operazioni:

* Rilevano se una risorsa è caricata o se è necessario visualizzare il modulo normale.
* Se una risorsa viene caricata, disabilitano la modalità WCM in quanto parsys può essere modificato solo in una pagina di modulo normale.
* Se una risorsa viene caricata, utilizza il suo titolo invece di quello nella pagina del modulo.

```java
 List<Resource> resources = FormsHelper.getFormEditResources(slingRequest);
    if (resources != null) {
        if (resources.size() == 1) {
            // single resource
            FormsHelper.setFormLoadResource(slingRequest, resources.get(0));
        } else if (resources.size() > 1) {
            // multiple resources
            // not supported by CQ 5.3
        }
    }
    Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
    String title;
    if (loadResource != null) {
        // an asset is loaded: disable WCM
        WCMMode.DISABLED.toRequest(request);

        String path = loadResource.getPath();
        Asset asset = loadResource.adaptTo(Asset.class);
        try {
            // it might happen that the adobe xmp lib creates an array
            Object titleObj = asset.getMetadata("dc:title");
            if (titleObj instanceof Object[]) {
                Object[] titleArray = (Object[]) titleObj;
                title = (titleArray.length > 0) ? titleArray[0].toString() : "";
            } else {
                title = titleObj.toString();
            }
        }
        catch (NullPointerException e) {
            title = path.substring(path.lastIndexOf("/") + 1);
        }
    }
    else {
        title = currentPage.getTitle() == null ? currentPage.getName() : currentPage.getTitle();
    }
```

Nella parte HTML, utilizza il set di titoli precedente (risorsa o titolo della pagina):

```html
<title><%= title %></title>
```

## Creazione di un componente campo modulo semplice {#creating-a-simple-form-field-component}

Questo esempio descrive come creare un componente che mostri e visualizzi i metadati di una risorsa caricata.

1. Crea una cartella di componenti nella directory dei progetti, ad esempio `/apps/geometrixx/components/samplemeta`.
1. Aggiungi `content.xml` con lo snippet seguente:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Dimension"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Asset Editor"/>
   ```

1. Aggiungi `samplemeta.jsp` con lo snippet seguente:

   ```javascript
   <%--
   
     Sample metadata field component
   
   --%><%@ page import="com.day.cq.dam.api.Asset,
                    java.security.AccessControlException" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       String value = "";
       String name = "dam:sampleMetadata";
       boolean readOnly = false;
   
       // If the form page is requested for an asset loadResource will be the asset.
       Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
   
       if (loadResource != null) {
   
           // Determine if the loaded asset is read only.
           Session session = slingRequest.getResourceResolver().adaptTo(Session.class);
           try {
               session.checkPermission(loadResource.getPath(), "set_property");
               readOnly = false;
           }
           catch (AccessControlException ace) {
               // checkPermission throws exception if asset is read only
               readOnly = true;
           }
           catch (RepositoryException re) {}
   
           // Get the value of the metadata.
           Asset asset = loadResource.adaptTo(Asset.class);
           try {
               value = asset.getMetadata(name).toString();
           }
           catch (NullPointerException npe) {
               // no metadata dc:description available
           }
       }
   %>
   <div class="form_row">
       <div class="form_leftcol">
           <div class="form_leftcollabel">Sample Metadata</div>
       </div>
       <div class="form_rightcol">
           <%
           if (readOnly) {
               %><c:out value="<%= value %>"/><%
           }
           else {
               %><input class="text" type="text" name="./jcr:content/metadata/<%= name %>" value="<c:out value="<%= value %>" />"><%
           }%>
       </div>
   </div>
   ```

1. Per rendere disponibile il componente, devi essere in grado di modificarlo. Per rendere modificabile un componente, in CRXDE Lite aggiungi un nodo `cq:editConfig` di tipo primario `cq:EditConfig`. Per rimuovere i paragrafi, aggiungi una proprietà con più valori `cq:actions` che presenta un singolo valore `DELETE`.

1. Passa al browser e alla pagina di esempio (ad esempio, `asseteditor.html`) passa alla modalità progettazione e attiva il nuovo componente per il sistema paragrafo.

1. Nella modalità **Modifica**, il nuovo componente, ad esempio, **Metadati campione**, è ora disponibile nella barra laterale (gruppo **Editor risorse**). Inserisci il componente. Per memorizzare i metadati, è necessario aggiungerli al modulo relativo.

## Modifica delle opzioni dei metadati {#modifying-metadata-options}

Puoi modificare i namespace disponibili nella [modulo metadati](assets-finder-editor.md#metadata-form-and-text-field-configuring-the-view-metadata-component).

I metadati attualmente disponibili sono definiti in `/libs/dam/options/metadata`:

* Il primo livello all’interno di questa directory contiene i namespace.
* Gli elementi all’interno di ogni spazio dei nomi rappresentano metadati, ad esempio un elemento locale parte.
* Il contenuto di metadati contiene le informazioni per il tipo e le opzioni multivalore.

Le opzioni possono essere sovrascritte in `/apps/dam/options/metadata`:

1. Copia la directory da `/libs` a `/apps`.

1. Rimuovere, modificare o aggiungere elementi.

>[!NOTE]
>
>Se aggiungi nuovi namespace, devono essere registrati nel repository/CRX. In caso contrario, l’invio del modulo di metadati genererà un errore.
