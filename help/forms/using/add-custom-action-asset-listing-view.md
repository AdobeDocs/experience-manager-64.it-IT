---
title: Aggiungi un’azione personalizzata alla vista Elenco risorse
seo-title: Add custom action to the Asset Listing view
description: Questo articolo illustra come aggiungere azioni personalizzate alla vista Elenco risorse
seo-description: This article teaches how to add custom action to the Asset Listing view
uuid: 72ce6c24-2758-4888-b797-1b134acc54d2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: b35ea921-182f-4371-90f6-482d22694b42
feature: Correspondence Management
exl-id: 00b3efc5-ef1c-4b9d-957d-2eda01c0b985
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 3%

---

# Aggiungi un’azione personalizzata alla vista Elenco risorse {#add-custom-action-to-the-asset-listing-view}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

La soluzione Gestione della corrispondenza consente di aggiungere azioni personalizzate all’interfaccia utente Gestione risorse.

Puoi aggiungere un’azione personalizzata alla vista Elenco risorse per:

* Uno o più tipi di risorse o lettere
* Esecuzione (azione/comando diventa attivo) quando si selezionano singole risorse/lettere o senza selezione

Questa personalizzazione viene illustrata con lo scenario in cui viene aggiunto un comando &quot;Scarica PDF flat&quot; alla vista Elenco risorse per lettere. Questo scenario di personalizzazione consente agli utenti di scaricare PDF flat di una singola lettera selezionata.

### Prerequisiti {#prerequisites}

Per completare lo scenario seguente o uno scenario simile, è necessario conoscere:

* CRX
* JavaScript
* Java

## Scenario: Aggiungere un comando all&#39;interfaccia utente dell&#39;elenco Lettere per scaricare la versione di una lettera di flat PDF {#addcommandtoletters}

I passaggi seguenti aggiungono un comando &quot;Download Flat PDF&quot; alla visualizzazione Elenco risorse per lettere e consentono agli utenti di scaricare PDF flat della lettera selezionata. Utilizzando questi passaggi con il codice e i parametri appropriati, puoi aggiungere altre funzionalità per una risorsa diversa, ad esempio dizionari di dati o testi.

Per personalizzare Gestione Corrispondenza per consentire agli utenti di scaricare un PDF di lettere flat, completa i passaggi seguenti:

1. Vai a `https://[server]:[port]/[ContextPath]/crx/de` e accedi come amministratore.

1. Nella cartella delle app, crea una cartella denominata items con percorso/struttura simile alla cartella degli elementi che si trova nella cartella di selezione, seguendo i passaggi seguenti:

   1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL items]** nel seguente percorso e seleziona **[!UICONTROL Nodo di sovrapposizione]**:

      `/libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/selection/items`

      >[!NOTE]
      >
      >Questo percorso è specifico per la creazione di un’azione che funziona con la selezione di una o più risorse/lettere. Se desideri creare un&#39;azione che funzioni senza selezione, devi invece creare un nodo di sovrapposizione per il seguente percorso e completare di conseguenza i passaggi rimanenti:
      >
      >
      >`/libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/default/items`

      ![Crea nodo](assets/1_itemscreatenode.png)

   1. Assicurati che la finestra di dialogo Sovrapponi nodo abbia i seguenti valori:

      **[!UICONTROL Percorso:]** /libs/fd/cm/ma/gui/content/cmassets/jcr:content/body/content/header/items/selection/items

      **[!UICONTROL Posizione:]** /apps/

      **[!UICONTROL Tipi di nodo di corrispondenza:]** Selezionati

      ![nodo di sovrapposizione](assets/2_createnodedownloadflatpdf.png)

   1. Fai clic su **[!UICONTROL OK]**. La struttura delle cartelle viene creata nella cartella delle app.

      Fai clic su **[!UICONTROL Salva tutto]**.

1. Nella cartella degli elementi appena creati, aggiungi un nodo per il pulsante/azione personalizzato in una particolare risorsa (Esempio: scaricaFlatPDF) seguendo la seguente procedura:

   1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL items]** e seleziona **[!UICONTROL Crea]** > **[!UICONTROL Crea nodo]**.

   1. Assicurati che la finestra di dialogo Crea nodo abbia i seguenti valori e fai clic su **[!UICONTROL OK]**:

      **[!UICONTROL Nome:]** downloadFlatPDF (o il nome che si desidera assegnare a questa proprietà)

      **[!UICONTROL Tipo:]** nt:unstructured

   1. Fai clic sul nuovo nodo creato (qui downloadFlatPDF). CRX visualizza le proprietà del nodo.
   1. Aggiungi le seguenti proprietà al nodo (qui downloadFlatPDF) e fai clic su **[!UICONTROL Salva tutto]**:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Nome</strong></td> 
    <td><strong>Tipo</strong></td> 
    <td><strong>Valore e descrizione</strong></td> 
    </tr> 
    <tr> 
    <td>classe</td> 
    <td>Stringa</td> 
    <td>foundation-collection-action</td> 
    </tr> 
    <tr> 
    <td>foundation-collection-action</td> 
    <td>Stringa</td> 
    <td><p>{"target": ".cq-manageasset-admin-children pages", "activeSelectionCount": "single","type": "LETTER"}<br /> <br /> <br /> <strong>activeSelectionCount</strong> può essere una o più risorse per consentire la selezione di una o più risorse sulle quali viene eseguita l’azione personalizzata.</p> <p><strong>type</strong> può essere una o più voci (voci multiple separate da virgola) tra le seguenti: LETTERA, TESTO, ELENCO, CONDIZIONE, DATAZIONARIO</p> </td> 
    </tr> 
    <tr> 
    <td>icon</td> 
    <td>Stringa</td> 
    <td>icona-download<br /> <br /> Icona visualizzata sul lato sinistro del comando o del menu. Per le diverse icone e impostazioni disponibili, consulta <a href="https://docs.adobe.com/docs/en/aem/6-3/develop/ref/coral-ui/coralui3/Coral.Icon.html" target="_blank">Documentazione di CoralUI Icons</a>.<br /> </td> 
    </tr> 
    <tr> 
    <td>jcr:primaryType</td> 
    <td>Nome</td> 
    <td>nt:unstructured</td> 
    </tr> 
    <tr> 
    <td>cilindro</td> 
    <td>Stringa</td> 
    <td>download-flat-pdf-button</td> 
    </tr> 
    <tr> 
    <td>sling:resourceType</td> 
    <td>Stringa</td> 
    <td>granite/ui/components/endor/actionbar/button</td> 
    </tr> 
    <tr> 
    <td>text</td> 
    <td>Stringa</td> 
    <td>Scarica Flat PDF (O qualsiasi altra etichetta)<br /> <br /> Comando visualizzato nell’interfaccia Elenco risorse</td> 
    </tr> 
    <tr> 
    <td>titolo</td> 
    <td>Stringa</td> 
    <td>Scarica un PDF flat della lettera selezionata (o qualsiasi altra etichetta/testo Alt)<br /> <br /> Il titolo è il testo alt visualizzato quando l’utente passa il mouse sul comando personalizzato.</td> 
    </tr> 
    </tbody> 
    </table>

1. Nella cartella delle app, crea una cartella denominata js con percorso/struttura simile alla cartella degli elementi che si trova nella cartella di amministrazione, seguendo i passaggi seguenti:

   1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL js]** nel seguente percorso e seleziona **[!UICONTROL Nodo di sovrapposizione]**: &quot;

      `/libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js`

   1. Assicurati che la finestra di dialogo Sovrapponi nodo abbia i seguenti valori:

      **[!UICONTROL Percorso:]** /libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js

      **[!UICONTROL Posizione:]** /apps/

      **[!UICONTROL Tipi di nodo di corrispondenza:]** Selezionati

   1. Fai clic su **[!UICONTROL OK]**. La struttura delle cartelle viene creata nella cartella delle app. Fai clic su **[!UICONTROL Salva tutto]**.

1. Nella cartella js , crea un file denominato formaction.js con il codice per la gestione dell’azione del pulsante seguendo i passaggi seguenti:

   1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL js]** nel seguente percorso e seleziona **[!UICONTROL Crea > Crea file]**:

      `/apps/fd/cm/ma/gui/components/admin/clientlibs/admin/js`

      Denomina il file come formaction.js.

   1. Fai doppio clic sul file per aprirlo in CRX.
   1. Nel file formaction.js (sotto il ramo /apps), copia il codice dal file formaction.js nel seguente percorso:

      `/libs/fd/cm/ma/gui/components/admin/clientlibs/admin/js/formaction.js`

      Quindi aggiungi il seguente codice alla fine nel file formaction.js (sotto il ramo /apps) e fai clic su **[!UICONTROL Salva tutto]**:

      ```
      /* Action url for xml file to be added.*/
      var ACTION_URL = "/apps/fd/cm/ma/gui/content/commons/actionhandlers/items/letterpdfdownloader.html";
      
      /* File upload handling*/
      var fileSelectedHandler = function(e){
          if(e && e.target && e.target.value)
              $(".downloadLetterPDFBtn").removeAttr('disabled');
          else
              $(".downloadLetterPDFBtn").attr('disabled','disabled');
      }
      
      /*Handing of Download button in pop up.*/
      var downloadClickHandler = function(){
          $('#downloadLetterPDFDilaog').modal("hide");
          var element = $('.foundation-selections-item');
          var path = $(element).data("path");
          $("#fileUploadForm").attr('action', ACTION_URL + "?letterId="+path).submit();
      }
      
      /*Click handling on action button.*/
      $(document).on("click",'.download-flat-pdf-button',function(e){
          $("#uploadSamepledata").val("");
           if($('#downloadLetterPDFDilaog').length == 0){
              $(document).on("click",".downloadLetterPDFBtn",downloadClickHandler);
              $(document).on("change","#uploadSamepledata",fileSelectedHandler);
              $("body").append(downloadLetterPDFDilaog);
          }
            $('#downloadLetterPDFDilaog').modal("show");
      });
      
      /*Download popup.*/
      var downloadLetterPDFDilaog = '<div id="downloadLetterPDFDilaog" class="coral-Modal notice " role="dialog"  aria-hidden="true">'+
          '<form id="fileUploadForm" method="POST" enctype="multipart/form-data">'+
              '<div class="coral-Modal-header">'+
                  '<h2 class="coral-Modal-title coral-Heading coral-Heading--2" id="modal-header1443020790107-label" tabindex="0">Download Letter as PDF.</h2>'+
                  '<button type="button" class="coral-MinimalButton coral-Modal-closeButton" data-dismiss="modal">×</button>'+
              '</div>'+
              '<div class="coral-Modal-body" id="modal-header1443020790107-message" role="document" tabindex="0">'+
                  '<div class="coral-Modal-message">'+
                      '<p></p>'+
                  '</div>'+
                  '<div class="coral-Modal-uploader">'+
                      '<p>Select sample data for letter.</p>'+
                      '<input type="file" id="uploadSamepledata" name="file" accept=".xml" size="70px">'+
                  '</div>'+
              '</div>'+
           '</form>'+
              '<div class="coral-Modal-footer">'+
                  '<button type="button" class="coral-Button" data-dismiss="modal">Cancel</button>'+
                  '<button type="button" class="coral-Button coral-Button--primary downloadLetterPDFBtn" disabled="disabled">Download</button>'+
              '</div>'+
      '</div>';
      ```

      Il codice aggiunto in questo passaggio sostituisce il codice sotto la cartella libs, quindi copia il codice precedente nel file formaction.js nel ramo /apps . Copiare il codice dal ramo /libs al ramo /apps assicura che funzioni anche la funzionalità precedente.

      Il codice di cui sopra è per la gestione dell&#39;azione specifica delle lettere del comando creato in questa procedura. Per la gestione delle azioni di altre risorse, modifica il codice JavaScript.

1. Nella cartella delle app, crea una cartella denominata items con percorso/struttura simile alla cartella items che si trova nella cartella actionhandlers seguendo i seguenti passaggi:

   1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL items]** nel seguente percorso e seleziona **[!UICONTROL Nodo di sovrapposizione]**:

      `/libs/fd/cm/ma/gui/content/commons/actionhandlers/items/`

   1. Assicurati che la finestra di dialogo Sovrapponi nodo abbia i seguenti valori:

      **[!UICONTROL Percorso:]** /libs/fd/cm/ma/gui/content/commons/actionhandlers/items/

      **[!UICONTROL Posizione:]** /apps/

      **[!UICONTROL Tipi di nodo di corrispondenza:]** Selezionati

   1. Fai clic su **[!UICONTROL OK]**. La struttura delle cartelle viene creata nella cartella delle app.

   1. Fai clic su **[!UICONTROL Salva tutto]**.

1. Sotto il nodo elementi appena creati, aggiungi un nodo per il pulsante/azione personalizzato in una particolare risorsa (Esempio: letterpdfdownloader) seguendo i seguenti passaggi:

   1. Fai clic con il pulsante destro del mouse sulla cartella degli elementi e seleziona **[!UICONTROL Crea > Crea nodo]**.

   1. Assicurati che la finestra di dialogo Crea nodo abbia i seguenti valori e fai clic su **[!UICONTROL OK]**:

      **[!UICONTROL Nome:]** letterpdfdownloader (o il nome che desideri assegnare a questa proprietà - deve essere univoco. Se utilizzi un nome diverso, specifica lo stesso nella variabile ACTION_URL del file formaction.js.)

      **[!UICONTROL Tipo:]** nt:unstructured

   1. Fai clic sul nuovo nodo creato (qui downloadFlatPDF). CRX visualizza le proprietà del nodo.

   1. Aggiungi la seguente proprietà al nodo (qui letterpdfdownloader) e fai clic su **[!UICONTROL Salva tutto]**:

      | **Nome** | **Tipo** | **Valore** |
      |---|---|---|
      | sling:resourceType | Stringa | fd/cm/ma/gui/components/admin/clientlibs/admin |

1. Crea un file denominato POST.jsp con il codice per la gestione delle azioni del comando nella posizione seguente:

   /apps/fd/cm/ma/gui/components/admin/clientlibs/admin

   1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL admin]** nel seguente percorso e seleziona **[!UICONTROL Crea > Crea file]**:

      /apps/fd/cm/ma/gui/components/admin/clientlibs/admin

      Denomina il file come POST.jsp. (Il nome del file deve essere solo POST.jsp.)

   1. Fai doppio clic sul pulsante **[!UICONTROL POST.jsp]** per aprirlo in CRX.
   1. Aggiungi il codice seguente al file POST.jsp e fai clic su **[!UICONTROL Salva tutto]**:

      Questo codice è specifico per il servizio di rendering della lettera. Per qualsiasi altra risorsa, aggiungi le librerie java della risorsa a questo codice. Per ulteriori informazioni sulle API di AEM Forms, consulta [API AEM Forms](https://adobe.com/go/learn_aemforms_javadocs_63_en).

      Per ulteriori informazioni sulle librerie AEM, consulta AEM [Componenti](/help/sites-developing/components.md).

      ```xml
      /*Import libraries. Here we are downloading letter flat pdf with input xml data so we require letterRender Api. For any other Module functionality we need to first import that library. */            
      <%@include file="/libs/foundation/global.jsp"%>
      <!DOCTYPE html lang="en" PUBLIC "-//W3C//DTD XHTML 1.1//EN" "https://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
      <%@page import="com.adobe.icc.ddg.api.*"%>
      <%@page import="com.adobe.icc.dbforms.obj.*"%>
      <%@page import="com.adobe.icc.render.obj.*" %>
      <%@page import="com.adobe.icc.services.api.*" %>
      <%@page import="org.apache.sling.api.resource.*" %>
      <%@page import="java.io.File" %>
      <%@page import="java.util.*" %>
      <%@page import="com.adobe.livecycle.content.appcontext.AppContextManager"%>
      <%@page import=" com.adobe.icc.dbforms.exceptions.ICCException"%>
      <%@page import="java.io.InputStream" %>
      <%@page import="java.io.FileInputStream" %>
      <%@page import="org.apache.commons.io.IOUtils" %>
      <%@page session="false" contentType="text/html; charset=utf-8"%>
      <%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0"%>
      <%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %>
       <%@page session="false" contentType="text/html; charset=utf-8"%>
      <%
         AppContextManager.setCurrentAppContext("/content/apps/cm");
         /*Get letter id sent in js file.*/
          String letterId = request.getParameter("letterId");
          if(letterId.lastIndexOf("?") != -1)
              letterId = letterId.substring(0, letterId.indexOf("?"));
          String fileName = null;
          String letterName = null;
          InputStream inputStream = null;
          /*Get xml file data*/
          if (slingRequest.getRequestParameter("file") != null)
              inputStream = slingRequest.getRequestParameter("file").getInputStream();
          if(letterId != null){
              String xmlData = null;
              try{
                  xmlData = IOUtils.toString(inputStream, "UTF-8");
              }
              catch (Exception e) {
                  log.error("Xml data does not exists.");
              }
              /*letter Name from letter letter id.*/
              letterName = letterId.substring(letterId.lastIndexOf("/")+1);
              /*Invoking letter render services API.*/
              LetterRenderService letterRenderService = sling.getService(LetterRenderService.class);
              /*using CM renderLetter api to get pdfbytes.*/
              PDFResponseType  pdfResponseType= letterRenderService.renderLetter(letterId,xmlData,true,false,false,false);
              byte[] bytes = null;
              /*Downloading pdf bytes as pdf.*/
              if(pdfResponseType != null && pdfResponseType.getFile() != null){
                  bytes = pdfResponseType.getFile().getDocument();
                  /*set the response header to enable download*/
                  response.setContentType("application/OCTET-STREAM");
                  response.setHeader("Content-Disposition", "attachment;filename=\"" + letterName + ".pdf\"");
                  response.setHeader("Pragma", "cache");
                  response.setHeader("Cache-Control", "private");
                  out.clear();
                  response.getOutputStream().write(bytes);
              }
          }
          else{
              log.error("Letter id does not exists.");
          }
      %>
      ```

## Scaricare un PDF di lettera utilizzando la funzionalità personalizzata {#download-flat-pdf-of-a-letter-using-the-custom-functionality}

Dopo aver aggiunto funzionalità personalizzate per scaricare le lettere in PDF flat, è possibile utilizzare i seguenti passaggi per scaricare la versione a PDF flat della lettera selezionata:

1. Vai a `https://[server]:[port]/[ContextPath]/projects.html` e accedi.

1. Seleziona **[!UICONTROL Forms > Lettere]**. Gestione corrispondenza elenca le lettere disponibili nel sistema.
1. Fai clic su **[!UICONTROL Seleziona]** quindi fare clic su una lettera per selezionarla.
1. Seleziona **[!UICONTROL Altro]** > &lt;download flat=&quot;&quot; pdf=&quot;&quot;> (La funzionalità personalizzata creata seguendo le istruzioni di questo articolo). Viene visualizzata la finestra di dialogo Scarica lettera come PDF.

   Il nome, la funzionalità e il testo alt del menu dipendono dalla personalizzazione creata in [Scenario: Aggiungere un comando all’interfaccia utente dell’elenco Lettere per scaricare la versione di una lettera di un PDF flat.](#addcommandtoletters)

   ![Funzionalità personalizzata: Scarica Flat PDF](assets/5_downloadflatpdf.png)

1. Nella finestra di dialogo Scarica lettera come PDF, selezionare il codice XML pertinente da cui si desidera compilare i dati in PDF.

   >[!NOTE]
   >
   >Prima di scaricare la lettera come un PDF flat, è possibile creare il file XML con i dati contenuti nella lettera utilizzando il **[!UICONTROL Creare un rapporto]** opzione .

   ![Scarica lettera come PDF](assets/6_downloadflatpdf.png)

   La lettera viene scaricata sul tuo computer come PDF piatto.
