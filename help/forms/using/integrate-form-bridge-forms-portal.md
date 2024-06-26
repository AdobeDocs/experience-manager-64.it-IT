---
title: Integrazione di Form Bridge con il portale personalizzato per i moduli HTML5
seo-title: Integrating Form Bridge with custom portal for HTML5 forms
description: È possibile utilizzare l’API FormBridge per ottenere o impostare i valori dei campi del modulo dalla pagina HTML e inviare il modulo.
seo-description: You can use the FormBridge API to get or set the values of form fields from the HTML page and submit the form.
uuid: 09f2189f-d584-4b84-895e-22833b6b17e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e0608649-bd49-4f40-bc1b-821c9b208883
feature: Mobile Forms
exl-id: bf4ae163-5d89-48fb-9bc4-182281b28f35
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# Integrazione di Form Bridge con il portale personalizzato per i moduli HTML5 {#integrating-form-bridge-with-custom-portal-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

FormBridge è un’API bridge di HTML5 forms che consente di interagire con un modulo. Per informazioni di riferimento sulle API di FormBridge, consulta [Riferimento API di FormBridge](/help/forms/using/form-bridge-apis.md).

È possibile utilizzare l’API FormBridge per ottenere o impostare i valori dei campi del modulo dalla pagina HTML e inviare il modulo. Ad esempio, puoi utilizzare l’API per creare un’esperienza simile alla procedura guidata.

Un’applicazione HTML esistente può utilizzare l’API FormBridge per interagire con un modulo e incorporarlo nella pagina HTML. Per impostare il valore di un campo utilizzando l’API Form Bridge, è possibile effettuare le seguenti operazioni.

## Integrazione dei moduli di HTML5 in una pagina web {#integrating-html-forms-to-a-web-page}

1. **Scegli un profilo o crea un profilo**

   1. Nell&#39;interfaccia CRX DE, passa a: `https://[server]:[port]/crx/de`.
   1. Accedi con le credenziali di amministratore.
   1. Crea un profilo o scegli un profilo esistente.

      Per informazioni dettagliate su come creare un profilo, consulta [Creazione di un nuovo profilo](/help/forms/using/custom-profile.md).

1. **Modificare il profilo di HTML**

   Includere runtime XFA, libreria locale XFA e snippet di moduli XFA HTML nel modulo di rendering del profilo, progettare la pagina web e posizionare il modulo all’interno della pagina web.

   Ad esempio, utilizza il seguente frammento di codice per creare un’app con due campi di input e un modulo per illustrare l’interazione tra il modulo e un’app esterna.

   ```xml
   <%@ page session="false"
                  contentType="text/html; charset=utf-8"%><%
   %><%@ taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
   %><!DOCTYPE html>
   <html manifest="${param.offlineSpec}">
       <head>
          <cq:include script="formRuntime.jsp"/>
           <!-- Portal Scripts and Styles -->
          <cq:include script="portalheader.jsp"/> 
       </head>
       <body>
           <div id="leftdiv" >
               <div id="leftdivcontentarea">   
                   <!-- Portal Body -->
                 <cq:include script="portalbody.jsp"/>  
               </div>
           </div>
           <div id="rightdiv">
               <div id="formBody">
               <cq:include script="config.jsp"/>
               <!-- Form body -->
               <cq:include script="formBody.jsp"/>
               <!  --To assist in page transitions -- add navigation, based on scrolling -->
               <cq:include  script="../nav/scroll/nav_footer.jsp"/>
               <cq:include script="footer.jsp"/>
               </div>    
           </div>
       </body>
   </html>
   ```

   >[!NOTE]
   >
   >La **Linea 9**, contiene riferimenti JSP aggiuntivi per gli stili CSS e i file JavaScript per la progettazione della pagina.
   >
   >La &lt;div id=&quot;rightdiv&quot;> tag su **linea 18** contiene lo snippet HTML del modulo XFA.
   La pagina è formattata in due contenitori: **sinistra** e **right**. Il contenitore di destra contiene il modulo. Il contenitore sinistro dispone di due campi di input e parte della pagina esterna di HTML.
   La seguente schermata mostra come viene visualizzato il modulo in un browser.

   ![portale](assets/portal.jpg)

   Il lato sinistro è parte del **Pagina HTML**. Il lato destro contenente i campi è il **modulo xfa**.

1. **Accesso ai campi del modulo dalla pagina**

   Di seguito è riportato uno script di esempio che è possibile aggiungere per impostare valori in un campo modulo.

   Ad esempio, se desideri impostare il **NomeDipendente** utilizzo dei valori nei campi **Nome** e **Cognome**, chiama **window.formBridge.setFieldValue** funzione .

   Allo stesso modo, puoi leggere il valore chiamando l’API **window.formBridge.getFieldValue **API.

   ```
   $(function() {
               $(".input").blur(function() {
                   window.formBridge.setFieldValue(
                               'xfa.form.form1.#subform[0].EmployeeName',
                                $("#lname").val()+' '+$("#fname").val()
                              )
                   });
           });
   ```
