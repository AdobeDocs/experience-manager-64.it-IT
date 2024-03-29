---
title: Creazione di un’azione personalizzata della barra degli strumenti
seo-title: Creating a custom toolbar action
description: Gli sviluppatori di moduli possono creare azioni personalizzate sulla barra degli strumenti per i moduli adattivi in AEM Forms. L’utilizzo di azioni personalizzate da parte degli autori di moduli consente agli utenti finali di disporre di più flussi di lavoro e opzioni.
seo-description: Form developers can create custom toolbar actions for adaptive forms in AEM Forms. Using custom actions form authors can provide more workflows and options to their end users.
uuid: 6761f389-1baa-4a59-a6e0-0f86f70fc692
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: b80a2bfe-6f57-4229-a9ee-1ec87f3c3306
exl-id: bb0abe28-843a-4195-afd5-5ee7f0a279be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 2%

---

# Creazione di un’azione personalizzata della barra degli strumenti {#creating-a-custom-toolbar-action}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Prerequisiti {#prerequisite}

Prima di creare un’azione personalizzata della barra degli strumenti, acquisisci familiarità con [Utilizzo delle librerie lato client](/help/sites-developing/clientlibs.md) e [Sviluppo con CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Azione {#what-is-an-action-br}

Un modulo adattivo fornisce una barra degli strumenti che consente all’autore del modulo di configurare un set di opzioni. Queste opzioni sono definite come azioni per il modulo adattivo. Fai clic sul pulsante Modifica nella barra degli strumenti del pannello per impostare le azioni supportate dai moduli adattivi.

![Azioni predefinite della barra degli strumenti](assets/default_toolbar_actions.png)

Oltre al set di azioni fornito per impostazione predefinita, puoi creare azioni personalizzate nella barra degli strumenti. Ad esempio, è possibile aggiungere un’azione per consentire all’utente di esaminare tutti i campi del modulo adattivo prima dell’invio del modulo.

## Passaggi per creare un’azione personalizzata in un modulo adattivo {#steps}

Per illustrare la creazione di un’azione personalizzata nella barra degli strumenti, i passaggi seguenti ti consentono di creare un pulsante che consenta agli utenti finali di esaminare tutti i campi del modulo adattivo prima di inviare un modulo compilato.

1. Tutte le azioni predefinite supportate dai moduli adattivi sono presenti in `/libs/fd/af/components/actions` cartella. In CRXDE, copia il `fileattachmentlisting` nodo da `/libs/fd/af/components/actions/fileattachmentlisting` a `/apps/customaction`.

1. Dopo aver copiato il nodo in `apps/customaction` cartella, rinominare il nome del nodo in `reviewbeforesubmit`. Inoltre, cambia la `jcr:title` e `jcr:description` proprietà del nodo.

   La `jcr:title` contiene il nome dell&#39;azione visualizzata nella finestra di dialogo della barra degli strumenti. La `jcr:description` contiene ulteriori informazioni visualizzate quando un utente passa il puntatore sull&#39;azione.

   ![Gerarchia dei nodi per la personalizzazione della barra degli strumenti](assets/action3.png)

1. Seleziona `cq:template` nodo in `reviewbeforesubmit` nodo. Assicurati che il valore di `guideNodeClass` è `guideButton` e cambiare `jcr:title` di conseguenza.
1. Modifica la proprietà type in `cq:Template` nodo. Per l&#39;esempio corrente, modificare la proprietà type in pulsante.

   Il valore type viene aggiunto come classe CSS nel HTML generato per il componente. Gli utenti possono utilizzare tale classe CSS per definire lo stile delle loro azioni. Lo stile predefinito sia per i dispositivi mobili che per quelli desktop è disponibile per i valori del pulsante, invio, ripristino e salvataggio.

1. Seleziona l’azione personalizzata dalla finestra di dialogo della barra degli strumenti per la modifica dei moduli adattivi. Nella barra degli strumenti del pannello viene visualizzato il pulsante Revisione.

   ![L’azione personalizzata è disponibile nella barra degli strumenti](assets/custom_action_available_in_toolbar.png) ![Visualizzazione dell&#39;azione personalizzata della barra degli strumenti](assets/action7.png)

1. Per fornire funzionalità al pulsante Review, aggiungi alcuni codici JavaScript e CSS e codice lato server nel file init.jsp, presente all&#39;interno del `reviewbeforesubmit` nodo.

   Aggiungi il seguente codice in `init.jsp`.

   ```
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <guide:initializeBean name="guideField" className="com.adobe.aemds.guide.common.GuideButton"/>
   
   <c:if test="${not isEditMode}">
           <cq:includeClientLib categories="reviewsubmitclientlibruntime" />
   </c:if>
   
   <%--- BootStrap Modal Dialog  --------------%>
   <div class="modal fade" id="reviewSubmit" tabindex="-1">
       <div class="modal-dialog">
           <div class="modal-content">
               <div class="modal-header">
                   <h3>Review the Form Fields</h3>
               </div>
               <div class="modal-body">
                   <div class="modal-list">
                       <table>
                           <tr>
                               <td>
                                   <label>Your Name is: </label>
                               </td>
                           </tr>
                           <tr>
                               <td>
                                   <label>Your Pan Number is: </label>
                               </td>
                           </tr>
                           <tr>
                               <td>
                                   <label>Your Date Of Birth is: </label>
                               </td>
                           </tr>
                           <tr>
                               <td>
                                   <label>Your Total 80C Declaration Amount is: </label>
                               </td>
                           </tr>
                           <tr>
                               <td>
                                   <label>Your Total HRA Amount is: </label>
                               </td>
                           </tr>
                       </table>
                   </div>
               </div><!-- /.modal-body -->
               <div class="modal-footer">
                   <div class="fileAttachmentListingCloseButton col-md-2 col-xs-2 col-sm-2">
                       <button data-dismiss="modal">Close</button>
                   </div>
               </div>
           </div><!-- /.modal-content -->
       </div><!-- /.modal-dialog -->
   </div><!-- /.modal -->
   ```

   Aggiungi il seguente codice nel `ReviewBeforeSubmit.js` file.

   ```
   /*anonymous function to handle show of review before submit view */
   $(function () {
       if($("div.reviewbeforesubmit button[id*=reviewbeforesubmit]").length > 0) {
           $("div.reviewbeforesubmit button[id*=reviewbeforesubmit]").click(function(){
               // Create the options object to be passed to the getElementProperty API
               var options = {},
                   result = [];
               options.somExpressions = [];
               options.propertyName = "value";
               guideBridge.visit(function(model){
                   if(model.name === "name" || model.name === "pan" || model.name === "dateofbirth" || model.name === "total" || model.name === "totalmonthlyrent"){
                           options.somExpressions.push(model.somExpression);
                   }
               }, this);
               result = guideBridge.getElementProperty(options);
   
               $('#reviewSubmit .reviewlabel').each(function(index, item){
                   var data = ((result.data[index] == null) ? "No Data Filled" : result.data[index]);
                   if($(this).next().hasClass("reviewlabelvalue")){
                       $(this).next().html(data);
                   } else {
                       $(this).after($("<td></td>").addClass("reviewlabelvalue col-md-6 active").html(data));
                   }
               });
               // added because in mobile devices it was causing problem of backdrop
               $("#reviewSubmit").appendTo('body');
               $("#reviewSubmit").modal("show");
           });
       }
   });
   ```

   Aggiungi il codice seguente a `ReviewBeforeSubmit.css` file.

   ```css
   .modal-list .reviewlabel {
       white-space: normal;
       text-align: right;
       padding:2px;
   }
   
   .modal-list .reviewlabelvalue {
       border: #cde0ec 1px solid;
       padding:2px;
   }
   
   /* Adding icon for this action in mobile devices */
   /* This is the glyphicon provided by bootstrap eye-open */
   /* .<type> .iconButton-icon */
   .reviewbeforesubmit .iconButton-icon {
       position: relative;
       top: -8px;
       font-family: 'Glyphicons Halflings';
       font-style: normal;
   }
   
   .reviewbeforesubmit .iconButton-icon:before {
       content: "\e105"
   }
   ```

1. Per verificare la funzionalità dell’azione personalizzata, apri il modulo adattivo in modalità Anteprima e fai clic su Rivedi nella barra degli strumenti.

   >[!NOTE]
   >
   >La `GuideBridge` libreria non caricata in modalità authoring. Pertanto, questa azione personalizzata non funziona in modalità di authoring.

   ![Dimostrazione dell’azione del pulsante di revisione personalizzato](assets/action9.png)

## Esempi {#samples}

Il seguente archivio contiene un pacchetto di contenuti. Il pacchetto include un modulo adattivo correlato alla demo precedente dell’azione personalizzata della barra degli strumenti.

[Ottieni file](assets/customtoolbaractiondemo.zip)
