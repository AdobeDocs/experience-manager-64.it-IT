---
title: Avvio rapido API di Forms Service
seo-title: Forms Service API Quick Starts
description: Utilizza gli avvii rapidi per l’API del servizio Forms.
seo-description: Use the Quick Starts for the Forms Service API.
uuid: dfce259a-e392-4929-ad7e-6d902faceaeb
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 9fe48243-24c6-4e08-9886-148cd99dec87
role: Developer
exl-id: abc2af58-3bf7-493e-917d-081022afb9a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---

# Avvio rapido API di Forms Service {#forms-service-api-quick-starts}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per il servizio Forms sono disponibili i seguenti Quick Starts:

[Avvio rapido (modalità SOAP): Rendering di un modulo PDF interattivo utilizzando l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-interactive-pdf-form-using-the-java-api)

[Avvio rapido (modalità SOAP): Rendering di un modulo sul client utilizzando l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Avvio rapido (modalità SOAP): Rendering di un modulo basato su frammenti utilizzando l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[Avvio rapido (modalità SOAP): Rendering di un modulo abilitato per i diritti utilizzando l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Avvio rapido (modalità SOAP): Rendering di un modulo HTML utilizzando l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-using-the-java-api)

[Avvio rapido (modalità SOAP): Rendering di un modulo HTML con una barra degli strumenti personalizzata tramite l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Avvio rapido (modalità SOAP): Gestione dei PDF forms inviati come XML tramite l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api)

[Avvio rapido (modalità SOAP): Gestione dei PDF forms inviati come PDF tramite l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api)

[Avvio rapido (modalità SOAP): Gestione dei moduli HTML inviati come XML tramite l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api)

[Avvio rapido (modalità SOAP): Creazione di documenti PDF con dati XML inviati tramite API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api)

[Avvio rapido (modalità SOAP): Precompilazione di Forms con layout fluidi tramite l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api)

[Avvio rapido (modalità SOAP): Gestione di un modulo contenente uno script di calcolo tramite l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-handling-a-form-containing-a-calculation-script-using-the-java-api)

[Avvio rapido (modalità SOAP): Ottimizzazione delle prestazioni tramite l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Avvio rapido (modalità SOAP): Rendering per valore utilizzando l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Avvio rapido (modalità SOAP): Trasmissione di documenti al servizio Forms tramite l’API Java](forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

La logica dell’applicazione che utilizza l’API del servizio Forms viene implementata come servlet Java. Le operazioni AEM Forms possono essere eseguite utilizzando l’API fortemente tipizzata di AEM Forms e la modalità di connessione deve essere impostata su SOAP.

>[!NOTE]
>
>Gli avvii rapidi disponibili in Programmazione con v si basano sul server dei moduli utilizzato da un altro sistema operativo, ad esempio Unix, sostituisci percorsi specifici di Windows con percorsi supportati dal sistema operativo applicabile. Allo stesso modo, se utilizzi un altro server applicativo J2EE, assicurati di specificare proprietà di connessione valide. Vedi [Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).


## Avvio rapido (modalità SOAP): Rendering di un modulo PDF interattivo utilizzando l’API Java {#quick-start-soap-mode-rendering-an-interactive-pdf-form-using-the-java-api}

Nell’esempio di codice seguente viene eseguito il rendering di un modulo interattivo PDF denominato *Loan.xdp* a un browser web client. Al modulo viene allegato un file. Tenere presente che la struttura del modulo fa parte di un’applicazione e a cui si fa riferimento utilizzando il valore URI della directory principale contenuto `repository:///`. (Vedi [Rendering di PDF forms interattivi](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms. 
     */ 
 import java.io.FileInputStream; 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
  
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderPDFForm extends HttpServlet implements Servlet { 
  
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp); 
     } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Set the parameter values for the renderPDFForm method 
             String formName = "Applications/FormsApplication/1.0/FormsFolder/Loan.xdp";   
                      
             byte[]    cData = "".getBytes(); 
             Document oInputData = new Document(cData); 
                                      
             //Set run-time options using a PDFFormRenderSpec instance 
             PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec(); 
             pdfFormRenderSpec.setCacheEnabled(new Boolean(true)); 
             pdfFormRenderSpec.setAcrobatVersion(AcrobatVersion.Acrobat_9); 
                      
             //Specify URI values that are required to render a form 
             URLSpec uriValues = new URLSpec();  
             uriValues.setApplicationWebRoot("https://[server]:[port]/FormsQS"); 
             uriValues.setContentRootURI("repository:///"); 
             uriValues.setTargetURL("https://[server]:[port]/FormsQS/HandleData"); 
                      
             //Specify file attachments to attach to the form 
             FileInputStream fileAttachment = new FileInputStream("C:\\rideau1.jpg");  
             Document attachment1 = new Document(fileAttachment); 
             String fileName = "rideau1.jpg"; 
             Map fileAttachments = new HashMap(); 
             fileAttachments.put(fileName, attachment1);  
                          
             //Invoke the renderPDFForm method and write the  
             //results to a client web browser 
             FormsResult formOut = formsClient.renderPDFForm( 
                         formName,               //formQuery 
                         oInputData,             //inDataDoc 
                         pdfFormRenderSpec,      //PDFFormRenderSpec 
                         uriValues,                //urlSpec 
                         fileAttachments            //attachments 
                         ); 
          
             //Create a Document object that stores form data 
             Document myData = formOut.getOutputContent(); 
          
             //Get the content type of the response and 
             //set the HttpServletResponse objects content type 
             String contentType = myData.getContentType();  
             resp.setContentType(contentType); 
          
             //Create a ServletOutputStream object 
             ServletOutputStream oOutput = resp.getOutputStream(); 
          
             //Create an InputStream object 
             InputStream inputStream = myData.getInputStream(); 
          
             //Write the data stream to the web browser 
             byte[] data = new byte[4096]; 
             int bytesRead = 0; 
             while ((bytesRead = inputStream.read(data)) > 0) 
             { 
                 oOutput.write(data, 0, bytesRead); 
             } 
          
             }catch (Exception e) { 
                  e.printStackTrace(); 
               } 
         } 
 }
```

## Avvio rapido (modalità SOAP): Rendering di un modulo sul client utilizzando l’API Java {#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api}

Nell&#39;esempio di codice seguente viene eseguito il rendering di un modulo denominato *Loan.xdp *sul client tramite l&#39;API Java del servizio Forms. Tenere presente che la struttura del modulo fa parte di un’applicazione e a cui si fa riferimento utilizzando il valore URI della directory principale contenuto `repository:///`. (Vedi [Rendering di Forms sul client](/help/forms/developing/rendering-forms.md#rendering-forms-at-the-client).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms. 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderPDFFormClient extends HttpServlet implements Servlet { 
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
             doPost(req,resp); 
     } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
     try{ 
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
         //Create a FormsServiceClient object 
         FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
         //Set parameter values required by the renderPDFForm method 
         String formName = "Applications/FormsApplication/1.0/FormsFolder/Loan.xdp";  
         byte[]    cData = "".getBytes(); 
         Document oInputData = new Document(cData); 
                  
         //Set a run-time option required to render a form on the client 
         PDFFormRenderSpec pdfRenderSpec = new PDFFormRenderSpec();  
         pdfRenderSpec.setRenderAtClient(RenderAtClient.Yes); 
                  
         //Specify URI values required to render a form 
         URLSpec uriValues = new URLSpec();  
         uriValues.setApplicationWebRoot("https://[server]:[port]/FormsServiceClientApp"); 
         uriValues.setContentRootURI("repository:///"); 
         uriValues.setTargetURL("https://[server]:[port]/FormsServiceClientApp/HandleData"); 
          
         //Invoke the renderPDFForm method to render  
         //an interactive PDF form on the client 
         FormsResult formOut = formsClient.renderPDFForm( 
                 formName,            
                 oInputData,          
                 pdfRenderSpec,       
                 uriValues,             
                 null                 
             ); 
          
         //Create a Document object that stores form data 
         Document myData = formOut.getOutputContent(); 
          
         //Get the content type of the response and 
         //set the HttpServletResponse objects content type 
         String contentType = myData.getContentType();  
         resp.setContentType(contentType); 
          
         //Create a ServletOutputStream object 
         ServletOutputStream oOutput = resp.getOutputStream(); 
          
         //Create an InputStream object 
         InputStream inputStream = myData.getInputStream(); 
          
         //Write the data stream to the web browser 
         byte[] data = new byte[4096]; 
         int bytesRead = 0; 
         while ((bytesRead = inputStream.read(data)) > 0) 
         { 
             oOutput.write(data, 0, bytesRead); 
         } 
          
         }catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
          } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Rendering di una guida (obsoleto) tramite l’API Java {#quick-start-soap-mode-rendering-a-guide-deprecated-using-the-java-api}

Nell&#39;esempio di codice seguente viene eseguito il rendering di una Guida (obsoleta) denominata *TLALifeClaim.xdp* a un browser web client.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import java.io.InputStream; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderFormGuide extends HttpServlet implements Servlet { 
  
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp);  
     } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
     try{ 
              
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
         FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
         //Specify the parameters for the renderActivityGuide method 
         String formName = "Applications/FormsApplication/1.0/FormsFolder/TLALifeClaim.xdp";  
         byte[] cData = "".getBytes(); 
         Document oInputData = new Document(cData); 
                  
         //Cache the PDF form 
         PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec(); 
         pdfFormRenderSpec.setCacheEnabled(new Boolean(true)); 
  
         //Set Form Guide run-time options 
         ActivityGuideRenderSpec renderSpec = new ActivityGuideRenderSpec();  
         renderSpec.setGuidePDF(false); 
          
         //Specify URI values that are required to render a form 
         //design located in the AEM Forms repository 
         URLSpec uriValues = new URLSpec();  
         uriValues.setApplicationWebRoot("https://[server]:[port]/FormsQS"); 
         uriValues.setContentRootURI("repository:///"); 
         uriValues.setTargetURL("https://[server]:[port]/FormsQS/HandleData"); 
          
  
         //Invoke the renderFormGuide method 
         FormsResult formOut = formsClient.renderFormGuide( 
                 formName,            //formQuery 
                 oInputData,          //inDataDoc  
                 pdfFormRenderSpec,    //pdfFormRenderSpec 
                 renderSpec,           //activityGuideRenderSpec 
                 uriValues              //urlSpec 
                 );   
          
         //Create a Document object that stores form data 
         Document myData = formOut.getOutputContent(); 
          
         //Get the content type of the response 
         String contentType = myData.getContentType();  
         resp.setContentType(contentType); 
          
         //Create a ServletOutputStream object 
         ServletOutputStream oOutput = resp.getOutputStream(); 
          
         //Create an InputStream object 
         InputStream inputStream = myData.getInputStream(); 
          
         //Write the data stream to the web browser 
         byte[] data = new byte[4096]; 
         int bytesRead = 0; 
         while ((bytesRead = inputStream.read(data)) > 0) 
         { 
             oOutput.write(data, 0, bytesRead); 
         } 
  
     }catch (Exception e) { 
              System.out.println("The following exception occured: "+e.getMessage()); 
               } 
      } 
 } 
 
```

## Avvio rapido (modalità SOAP): Rendering di un modulo basato su frammenti utilizzando l’API Java {#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api}

Nell&#39;esempio di codice seguente viene eseguito il rendering di un modulo basato su frammenti. Il nome della struttura del modulo è *PurchaseOrderDynamic.xdp* e si trova nell’archivio AEM Forms (il file XDP viene memorizzato in una cartella denominata FormsFolder situata nell’archivio). Anche i frammenti a cui fa riferimento il modulo POFragment devono trovarsi nell’archivio. (Vedi [Rendering di Forms basato su frammenti](/help/forms/developing/rendering-forms.md#rendering-forms-based-on-fragments).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.FileInputStream; 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderFormFragments extends HttpServlet implements Servlet { 
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp);  
  
     } 
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
     throws ServletException, IOException { 
              
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Set the parameter values for the renderPDFForm method 
             String formName = "Applications/FormsApplication/1.0/FormsFolder/PurchaseOrderDynamic.xdp";   
              
             FileInputStream myFormData = new FileInputStream("C:\\Adobe\Purchase Order US.xml"); 
             Document oInputData = new Document(myFormData); 
                                      
             //Cache the PDF form 
             PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec(); 
             pdfFormRenderSpec.setCacheEnabled(new Boolean(true)); 
          
             //Specify URI values that are required to render a form 
             //design based on fragments 
             URLSpec uriValues = new URLSpec();  
             uriValues.setApplicationWebRoot("https://[server]:[port]/FormsServiceClientApp"); 
             uriValues.setContentRootURI("repository:///"); 
             uriValues.setTargetURL("https://[server]:[port]/FormsServiceClientApp/HandleData"); 
                      
             //Invoke the renderPDFForm method and write the  
             //results to a client web browser 
             FormsResult formOut = formsClient.renderPDFForm( 
                         formName,               //formQuery 
                         oInputData,             //inDataDoc 
                         pdfFormRenderSpec,      //PDFFormRenderSpec 
                         uriValues,                //urlSpec 
                         null                    //attachments 
                         ); 
          
             //Create a Document object that stores form data 
             Document myData = formOut.getOutputContent(); 
          
             //Get the content type of the response and 
             //set the HttpServletResponse object’s content type 
             String contentType = myData.getContentType();  
             resp.setContentType(contentType); 
          
             //Create a ServletOutputStream object 
             ServletOutputStream oOutput = resp.getOutputStream(); 
          
             //Create an InputStream object 
             InputStream inputStream = myData.getInputStream(); 
          
             //Write the data stream to the web browser 
             byte[] data = new byte[4096]; 
             int bytesRead = 0; 
             while ((bytesRead = inputStream.read(data)) > 0) 
             { 
                 oOutput.write(data, 0, bytesRead); 
             } 
         }catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
       } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Rendering di un modulo abilitato per i diritti utilizzando l’API Java {#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api}

Nell&#39;esempio di codice seguente viene eseguito il rendering di un modulo abilitato per i diritti in un browser Web client. I diritti di utilizzo impostati in questo esempio di codice consentono a un utente di aggiungere commenti al modulo e salvare i dati del modulo. (Vedi [Forms con diritti di rendering](/help/forms/developing/rendering-forms.md#rendering-rights-enabled-forms).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
  
 public class RenderUsageRightsForms extends HttpServlet implements Servlet { 
  
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp); 
     } 
  
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
     try{ 
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a FormsServiceClient object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
         FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
         //Set parameter values for the renderPDFFormWithUsageRights method 
         String formName = "Applications/FormsApplication/1.0/FormsFolder/Loan.xdp";  
         byte[]    cData = "".getBytes(); 
         Document oInputData = new Document(cData); 
          
         //Set run-time options 
         PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec(); 
         pdfFormRenderSpec.setCacheEnabled(new Boolean(true)); 
          
         //Set usage-rights run-time options 
         ReaderExtensionSpec reOptions = new ReaderExtensionSpec(); 
         reOptions.setReCredentialAlias("RE2"); 
         reOptions.setReCommenting(true); 
         reOptions.setReFillIn(true); 
          
         //Specify URI values required to render the form 
         URLSpec uriValues = new URLSpec();  
         uriValues.setApplicationWebRoot("https://[server]:[port]/FormsQS"); 
         uriValues.setContentRootURI("repository:///"); 
         uriValues.setTargetURL("https://[server]:[port]/FormsQS/HandleData"); 
          
         //Render a rights-enabled PDF form 
         FormsResult formOut = formsClient.renderPDFFormWithUsageRights( 
             formName,            //formQuery 
             oInputData,          //inDataDoc  
             pdfFormRenderSpec,   //renderFormOptionsSpec 
             reOptions,              //applicationWebRoot 
             uriValues            //targetURL 
             ); 
          
         //Create a Document object that stores form data 
         Document myData = formOut.getOutputContent(); 
          
         //Get the content type of the response and 
         //set the HttpServletResponse objects content type 
         String contentType = myData.getContentType();  
         resp.setContentType(contentType); 
          
         //Create a ServletOutputStream object 
         ServletOutputStream oOutput = resp.getOutputStream(); 
          
         //Create an InputStream object 
         InputStream inputStream = myData.getInputStream(); 
          
         //Write the data stream to the web browser 
         byte[] data = new byte[4096]; 
         int bytesRead = 0; 
         while ((bytesRead = inputStream.read(data)) > 0) 
         { 
             oOutput.write(data, 0, bytesRead); 
         } 
          
     }catch (Exception e) { 
          System.out.println("The following exception occurred: "+e.getMessage()); 
       } 
     } 
 } 
  
 
```

## Avvio rapido (modalità SOAP): Rendering di un modulo HTML utilizzando l’API Java {#quick-start-soap-mode-rendering-an-html-form-using-the-java-api}

Nell’esempio di codice seguente viene eseguito il rendering di un modulo HTML tramite l’API Java del servizio Forms. Al modulo HTML viene aggiunta una barra degli strumenti e due file allegati. Inoltre, il valore dell&#39;agente utente viene ottenuto dal `HttpServletRequest` oggetto. (Vedi [Rendering di Forms as HTML](/help/forms/developing/rendering-forms.md#rendering-forms-as-html).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
  
 import java.util.*; 
 import java.io.InputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import java.io.FileInputStream; 
  
  
 public class RenderHTMLForms extends HttpServlet implements Servlet { 
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp);  
     } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
             try{ 
              
                 //Set connection properties required to invoke AEM Forms     
                 Properties connectionProps = new Properties(); 
                 connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
                 connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL","SOAP");           
                 connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
                 connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
                 connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
              
                 //Create a FormsServiceClient object 
                 ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                 FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
                 //Set parameter values for the (Deprecated) renderHTMLForm method 
                 String formName = "Applications/FormsApplication/1.0/FormsFolder/Loan.xdp";   
                 byte[]    cData = "".getBytes(); 
                 Document oInputData = new Document(cData); 
                  
                 //Obtain the user agent value from the HttpServletRequest object 
                 String userAgent = req.getHeader("user-agent"); 
                                      
                 //Create an HTMLRenderSpec object to store HTML run-time options 
                 HTMLRenderSpec htmlRS = new HTMLRenderSpec(); 
                 htmlRS.setHTMLToolbar(HTMLToolbar.Vertical); 
                                                          
                 //Specify the locale value 
                 htmlRS.setLocale("en_US"); 
                          
                 //Render the HTML form within full HTML tags 
                 htmlRS.setOutputType(OutputType.FullHTMLTags); 
                  
                 //Set style information that controls the presentation of the HTML form 
                 htmlRS.setStyleGenerationLevel(StyleGenerationLevel.InlineAndInternalStyles); 
                                                                  
                 //Specify URI values that are required to render a form 
                 URLSpec uriValues = new URLSpec();  
                 uriValues.setApplicationWebRoot("https://[server]:[port]/FormsQS"); 
                 uriValues.setContentRootURI("repository:///"); 
                 uriValues.setTargetURL("https://[server]:[port]/FormsQS/HandleSubmittedHTMLForm"); 
                                  
                 //Specify file attachments 
                 FileInputStream myForm = new FileInputStream("C:\\Attach1.txt");  
                 Document attachment1 = new Document(myForm); 
                 FileInputStream myForm2 = new FileInputStream("C:\\Attach2.txt");  
                 Document attachment2 = new Document(myForm2); 
                 String fileName = "Attach1.txt"; 
                 String fileName2 = "Attach2.txt"; 
                      
                 Map fileAttachments = new HashMap(); 
                 fileAttachments.put(fileName, attachment1);  
                 fileAttachments.put(fileName2, attachment2);  
                          
                 //Invoke the (Deprecated) renderHTMLForm method 
                 FormsResult formOut = formsClient.renderHTMLForm( 
                     formName,               //formQuery 
                     TransformTo.MSDHTML,    //transformTo 
                     oInputData,             //inDataDoc 
                     htmlRS,                    //renderHTMLSpec 
                     userAgent,                //User Agent 
                     uriValues,                //urlSpec 
                     fileAttachments            //attachments 
                     ); 
          
                 //Create a Document object that stores form data 
                 Document myData = formOut.getOutputContent(); 
          
                 //Get the content type of the response and 
                 //set the HttpServletResponse object’s content type 
                 String contentType = myData.getContentType();  
                 resp.setContentType(contentType); 
          
                 //Create a ServletOutputStream object 
                 ServletOutputStream oOutput = resp.getOutputStream(); 
          
                 //Create an InputStream object 
                 InputStream inputStream = myData.getInputStream(); 
          
                 //Write the data stream to the web browser 
                 byte[] data = new byte[4096]; 
                 int bytesRead = 0; 
                 while ((bytesRead = inputStream.read(data)) > 0) 
                 { 
                     oOutput.write(data, 0, bytesRead); 
                 } 
          
                 }catch (Exception e) { 
                      System.out.println("The following exception occurred: "+e.getMessage()); 
                      } 
             } 
 } 
  
  
  
 
```

## Avvio rapido (modalità SOAP): Rendering di un modulo HTML che utilizza un file CSS utilizzando l’API Java {#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api}

Nell’esempio di codice seguente viene eseguito il rendering di un modulo HTML utilizzando l’API client del servizio Forms. Il nome del file CSS personalizzato a cui si fa riferimento è *custom.css*. (Vedi [Rendering di HTML Forms utilizzando file CSS personalizzati](/help/forms/developing/rendering-forms.md#rendering-html-forms-using-custom-css-files).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
     * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
  
 import java.util.*; 
 import java.io.InputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 import java.io.FileInputStream; 
  
  
 public class RenderHTMLCSS extends HttpServlet implements Servlet { 
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp);  
     } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
             try{ 
                 //Set connection properties required to invoke AEM Forms                                 
                 Properties connectionProps = new Properties(); 
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
                 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
                 //Create a FormsServiceClient object 
                 ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                 FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
                 //Set parameter values for the (Deprecated) renderHTMLForm method 
                 String formName = "Applications/FormsApplication/1.0/FormsFolder/Loan.xdp";  
                 byte[]    cData = "".getBytes(); 
                 Document oInputData = new Document(cData); 
                 String userAgent = "" ; 
                                      
                 //Create an HTMLRenderSpec object to store HTML run-time options 
                 HTMLRenderSpec htmlRS = new HTMLRenderSpec(); 
                                                                          
                 //Specify the locale value 
                 htmlRS.setLocale("en_US"); 
                  
                 //Specify a custom CSS file to use 
                 htmlRS.setCustomCSSURI("C:\\Adobe\custom.css"); 
                  
                 //Render the HTML form within full HTML tags 
                 htmlRS.setOutputType(OutputType.FullHTMLTags); 
                                                                  
                 //Specify URI values that are required to render a form 
                 URLSpec uriValues = new URLSpec();  
                 uriValues.setApplicationWebRoot("https://[server]:[port]/FormsQS"); 
                 uriValues.setContentRootURI("repository:///"); 
                 uriValues.setTargetURL("https://[server]:[port]/FormsQS/HandleData"); 
                                  
                 //Specify file attachments 
                 FileInputStream myForm = new FileInputStream("C:\\Attach1.txt");  
                 Document attachment1 = new Document(myForm); 
                 FileInputStream myForm2 = new FileInputStream("C:\\Attach2.txt");  
                 Document attachment2 = new Document(myForm2); 
                 String fileName = "Attach1.txt"; 
                 String fileName2 = "Attach2.txt"; 
                      
                 Map fileAttachments = new HashMap(); 
                 fileAttachments.put(fileName, attachment1);  
                 fileAttachments.put(fileName2, attachment2);  
                          
                 //Invoke the (Deprecated) renderHTMLForm method 
                 FormsResult formOut = formsClient.renderHTMLForm( 
                     formName,               //formQuery 
                     TransformTo.MSDHTML,    //transformTo 
                     oInputData,             //inDataDoc 
                     htmlRS,                    //renderHTMLSpec 
                     userAgent,                //User Agent 
                     uriValues,                //urlSpec 
                     fileAttachments            //attachments 
                     ); 
          
                 //Create a Document object that stores form data 
                 Document myData = formOut.getOutputContent(); 
          
                 //Get the content type of the response and 
                 //set the HttpServletResponse object’s content type 
                 String contentType = myData.getContentType();  
                 resp.setContentType(contentType); 
          
                 //Create a ServletOutputStream object 
                 ServletOutputStream oOutput = resp.getOutputStream(); 
          
                 //Create an InputStream object 
                 InputStream inputStream = myData.getInputStream(); 
          
                 //Write the data stream to the web browser 
                 byte[] data = new byte[4096]; 
                 int bytesRead = 0; 
                 while ((bytesRead = inputStream.read(data)) > 0) 
                 { 
                     oOutput.write(data, 0, bytesRead); 
                 } 
          
             }catch (Exception e) { 
                      System.out.println("The following exception occurred: "+e.getMessage()); 
              } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Rendering di un modulo HTML con una barra degli strumenti personalizzata tramite l’API Java {#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api}

Nell&#39;esempio di codice seguente viene eseguito il rendering di un modulo HTML con una barra degli strumenti visualizzata in francese. Il percorso del file fscmenu.xml è C:\Adobe (questa cartella deve trovarsi sul server che ospita AEM Forms). Il valore locale è `fr_FR`. La sezione che illustra come eseguire il rendering di un modulo HTML con una barra degli strumenti personalizzata mostra la sintassi del file fscmenu.xml utilizzato in questo avvio rapido. (Vedi [Rendering di HTML Forms con barre degli strumenti personalizzate](/help/forms/developing/rendering-forms.md#rendering-html-forms-with-custom-toolbars).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
  
 import java.util.*; 
 import java.io.InputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import java.io.FileInputStream; 
  
  
 public class RenderCustomToolbar extends HttpServlet implements Servlet { 
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp);  
     } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
             try{ 
                 //Set connection properties required to invoke AEM Forms     
                 Properties connectionProps = new Properties(); 
                 connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
                 connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL","SOAP");           
                 connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
                 connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
                 connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
              
                 //Create a FormsServiceClient object 
                 ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                 FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
                 //Set parameter values for the renderHTMLForm method 
                 String formName = "Applications/FormsApplication/1.0/FormsFolder/Loan.xdp";   
                 byte[]    cData = "".getBytes(); 
                 Document oInputData = new Document(cData); 
                 String userAgent = "" ; 
                                      
                 //Create an HTMLRenderSpec object to store HTML run-time options 
                 HTMLRenderSpec htmlRS = new HTMLRenderSpec(); 
                 htmlRS.setHTMLToolbar(HTMLToolbar.Vertical); 
                                                          
                 //Specify the URI location of the  
                 // fscmenu.xml file that contains French 
                 htmlRS.setToolbarURI("C:\\Adobe"); 
                  
                 //Specify the locale value 
                 htmlRS.setLocale("fr_FR"); 
                                  
                 //Render the HTML form within full HTML tags 
                 htmlRS.setOutputType(OutputType.FullHTMLTags); 
                                                                  
                 //Specify URI values that are required to render a form 
                 URLSpec uriValues = new URLSpec();  
                 uriValues.setApplicationWebRoot("https://[server]:[port]/FormsQS"); 
                 uriValues.setContentRootURI("repository:///"); 
                 uriValues.setTargetURL("https://[server]:[port]/FormsQS/HandleData"); 
                                  
                 //Specify file attachments 
                 FileInputStream myForm = new FileInputStream("C:\\Attach1.txt");  
                 Document attachment1 = new Document(myForm); 
                 FileInputStream myForm2 = new FileInputStream("C:\\Attach2.txt");  
                 Document attachment2 = new Document(myForm2); 
                 String fileName = "Attach1.txt"; 
                 String fileName2 = "Attach2.txt"; 
                      
                 Map fileAttachments = new HashMap(); 
                 fileAttachments.put(fileName, attachment1);  
                 fileAttachments.put(fileName2, attachment2);  
                          
                 //Invoke the renderHTMLForm method 
                 FormsResult formOut = formsClient.renderHTMLForm( 
                     formName,               //formQuery 
                     TransformTo.MSDHTML,    //transformTo 
                     oInputData,             //inDataDoc 
                     htmlRS,                    //renderHTMLSpec 
                     userAgent,                //User Agent 
                     uriValues,                //urlSpec 
                     fileAttachments            //attachments 
                     ); 
          
                 //Create a Document object that stores form data 
                 Document myData = formOut.getOutputContent(); 
          
                 //Get the content type of the response and 
                 //set the HttpServletResponse object’s content type 
                 String contentType = myData.getContentType();  
                 resp.setContentType(contentType); 
          
                 //Create a ServletOutputStream object 
                 ServletOutputStream oOutput = resp.getOutputStream(); 
          
                 //Create an InputStream object 
                 InputStream inputStream = myData.getInputStream(); 
          
                 //Write the data stream to the web browser 
                 byte[] data = new byte[4096]; 
                 int bytesRead = 0; 
                 while ((bytesRead = inputStream.read(data)) > 0) 
                 { 
                     oOutput.write(data, 0, bytesRead); 
                 } 
          
                 }catch (Exception e) { 
                      System.out.println("The following exception occurred: "+e.getMessage()); 
                      } 
             } 
 } 
 
```

## Avvio rapido (modalità SOAP): Gestione dei PDF forms inviati come XML tramite l’API Java {#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api}

Nell&#39;esempio di codice seguente viene gestito un modulo inviato come XML. Il valore del tipo di contenuto trasmesso al `processFormSubmission` metodo `CONTENT_TYPE=text/xml`. Valori corrispondenti ai campi denominati `mortgageAmount`, `lastName`e `firstName` vengono visualizzati. Un metodo definito dall&#39;utente denominato `getNodeText` viene utilizzato in questo avvio rapido. Accetta un `org.w3c.dom.Document` istanza e valore stringa che specifica il nome del nodo. Questo metodo restituisce un valore stringa che rappresenta il valore del nodo. (Vedi [Gestione di Forms inviati](/help/forms/developing/rendering-forms.md#handling-submitted-forms).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 9. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.DataInputStream; 
 import java.io.File; 
 import java.io.InputStream; 
 import java.io.PrintWriter; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 //Import DOM libraries 
 import org.w3c.dom.NodeList; 
 import org.w3c.dom.Node; 
 import javax.xml.parsers.*; 
  
 public class HandleData extends HttpServlet implements Servlet { 
  
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
                 doPost(req,resp); 
         } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
         try{ 
             PrintWriter pp = resp.getWriter();      
              
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Get Form data to pass to the processFormSubmission method 
             Document formData = new Document(req.getInputStream());  
                          
             //Set run-time options 
              RenderOptionsSpec processSpec = new RenderOptionsSpec();  
              processSpec.setLocale("en_US"); 
              
             //Invoke the processFormSubmission method 
             FormsResult formOut = formsClient.processFormSubmission(formData, 
             "CONTENT_TYPE=text/xml", 
             "", 
             processSpec); 
              
             //Get the processing state 
             short processState = formOut.getAction(); 
                          
             //Determine if the form data is ready to be processed 
             //This code example checks only for submitted data (value is 0) 
             if (processState == 0)  
             { 
               //Determine the content type of the data 
               String myContentType = formOut.getContentType(); 
               System.out.println("THE CONTENT TYPS IS" +myContentType); 
              
                if (myContentType.equals("application/vnd.adobe.xdp+xml"))    { 
              
                 //Get the form data 
                 Document formOutput = formOut.getOutputContent();  
                 InputStream formInputStream = new DataInputStream(formOutput.getInputStream());  
                  
                 //Create DocumentBuilderFactory and DocumentBuilder objects 
                 DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance(); 
                 DocumentBuilder builder = factory.newDocumentBuilder(); 
                 org.w3c.dom.Document myDOM = builder.parse(formInputStream); 
                                          
                 //Call for each field in the form 
                 String Amount = getNodeText("mortgageAmount", myDOM); 
                 String myLastName =  getNodeText("lastName", myDOM);  
                 String myFirstName = getNodeText("firstName", myDOM); 
                  
                 //Write the form data to the web browser 
                 pp.println("<p> The form data is :<br><br>" + 
                         "<li> The mortgage amount is "+ Amount+"" + 
                         "<li> Last name is "+ myLastName+"" + 
                         "<li> First name is "+ myFirstName+"")    ; 
                  
                          
                 } 
              } 
             } 
         catch (Exception e) { 
              e.printStackTrace(); 
           } 
     } 
          
     //This method returns the value of the specified node 
     private String getNodeText(String nodeName, org.w3c.dom.Document myDOM) 
     { 
       //Get the XML node by name 
       NodeList oList = myDOM.getElementsByTagName(nodeName); 
       Node myNode = oList.item(0);  
       NodeList oChildNodes = myNode.getChildNodes(); 
                                   
      String sText = ""; 
      for (int i = 0; i < oChildNodes.getLength(); i++) 
      { 
          Node oItem = oChildNodes.item(i); 
         if (oItem.getNodeType() == Node.TEXT_NODE) 
          { 
            sText = sText.concat(oItem.getNodeValue()); 
          } 
      } 
     return sText; 
     } 
 } 
 
```

>[!NOTE]
>
>Quando si utilizza un `com.adobe.idp.Document` e un `org.w3c.dom.Document` nella stessa domanda, tutti i requisiti `org.w3c.dom.Document`.

## Avvio rapido (modalità SOAP): Gestione dei PDF forms inviati come PDF tramite l’API Java {#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api}

Nell&#39;esempio di codice seguente viene gestito un modulo inviato come dati di PDF. Il valore del tipo di contenuto trasmesso al `processFormSubmission` metodo `CONTENT_TYPE=application/pdf`. Il modulo inviato viene salvato come file PDF denominato *tempPDF.pdf*. Inoltre, poiché il modulo viene inviato come PDF, è possibile recuperare gli allegati del file. Tutti gli allegati vengono salvati come file JPEG. (Vedi [Gestione di Forms inviati](/help/forms/developing/rendering-forms.md#handling-submitted-forms).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.DataInputStream; 
 import java.io.File; 
 import java.io.InputStream; 
 import java.io.PrintWriter; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 //Import DOM libraries 
 import org.w3c.dom.NodeList; 
 import org.w3c.dom.Node; 
 import javax.xml.parsers.*; 
  
 public class HandleSubmittedPDFData extends HttpServlet implements Servlet { 
  
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
                 doPost(req,resp); 
         } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
         try{ 
             PrintWriter pp = resp.getWriter();      
              
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Get Form data to pass to the processFormSubmission method 
             Document formData = new Document(req.getInputStream());  
                          
             //Set run-time options 
              RenderOptionsSpec processSpec = new RenderOptionsSpec();  
              processSpec.setLocale("en_US"); 
              
             //Invoke the processFormSubmission method 
             FormsResult formOut = formsClient.processFormSubmission(formData, 
             "CONTENT_TYPE=application/pdf", 
             "", 
             processSpec); 
              
             //Determine if the form contains file attachments 
             //It is assumed that file attachments are JPG files 
             List fileAttachments = formOut.getAttachments();  
                                  
             //Create an Iterator object and iterate through  
             //the List object 
             Iterator iter = fileAttachments.iterator();  
             int i = 0 ;  
             while (iter.hasNext()) {  
                 Document file = (Document)iter.next();  
                 file.copyToFile(new File("C:\\Adobe\tempFile"+i+".jpg")); 
                 i++;  
             } 
              
             //Get the processing state 
             short processState = formOut.getAction(); 
                          
             //Determine if the form data is ready to be processed 
             //This code example checks only for submitted data (value is 0) 
             if (processState == 0)  
             { 
               //Determine the content type of the data 
               String myContentType = formOut.getContentType(); 
              
               if (myContentType.equals("application/pdf")){ 
                      
                     //Get the form data 
                     Document myPDFfile = formOut.getOutputContent();  
                                      
                     //Create a PDF object 
                     File myPDFFile = new File("C:\\Adobe\tempPDF.pdf"); 
                      
                     //Populate the PDF file 
                     myPDFfile.copyToFile(myPDFFile);                     
                     pp.println("<p> The PDF file is saved as C:\\Adobe\tempPDF.pdf") ;  
                      
                 } 
               } 
         } 
         catch (Exception e) { 
              e.printStackTrace(); 
           } 
     } 
  
 } 
  
  
 
```

## Avvio rapido (modalità SOAP): Gestione dei moduli HTML inviati come XML tramite l’API Java {#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api}

Nell&#39;esempio di codice seguente viene gestito un modulo HTML inviato come dati XML. Il valore del tipo di contenuto trasmesso al `processFormSubmission` metodo `CONTENT_TYPE=application/x-www-form-urlencoded`.I valori corrispondenti ai campi denominati `mortgageAmount`, `lastName`e `firstName` vengono visualizzati. Un metodo definito dall&#39;utente denominato `getNodeText` viene utilizzato in questo avvio rapido. Accetta un `org.w3c.dom.Document` istanza e valore stringa che specifica il nome del nodo. Questo metodo restituisce un valore stringa che rappresenta il valore del nodo. (Vedi [Gestione di Forms inviati](/help/forms/developing/rendering-forms.md#handling-submitted-forms).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.DataInputStream; 
 import java.io.File; 
 import java.io.InputStream; 
 import java.io.PrintWriter; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 //Import DOM libraries 
 import org.w3c.dom.NodeList; 
 import org.w3c.dom.Node; 
 import javax.xml.parsers.*; 
  
 /* 
     * This quick start handles data submitted as XML from a rendered HTML form  
     */ 
 public class HandleSubmittedHTMLForm extends HttpServlet implements Servlet { 
  
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
                 doPost(req,resp); 
         } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
         try{ 
             PrintWriter pp = resp.getWriter();      
              
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Get Form data to pass to the processFormSubmission method 
             Document formData = new Document(req.getInputStream());  
                          
             //Set run-time options 
              RenderOptionsSpec processSpec = new RenderOptionsSpec();  
              processSpec.setLocale("en_US"); 
              
             //Invoke the processFormSubmission method 
             FormsResult formOut = formsClient.processFormSubmission(formData, 
             "CONTENT_TYPE=application/x-www-form-urlencoded", 
             "", 
             processSpec); 
              
             //Get the processing state 
             short processState = formOut.getAction(); 
                          
             //Determine if the form data is ready to be processed 
             //This code example checks only for submitted data (value is 0) 
             if (processState == 0)  
             { 
              
                     //Get the form data 
                     Document formOutput = formOut.getOutputContent();  
                     InputStream formInputStream = new DataInputStream(formOutput.getInputStream());  
                                                      
                     //Create DocumentBuilderFactory and DocumentBuilder objects 
                     DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance(); 
                     DocumentBuilder builder = factory.newDocumentBuilder(); 
                     org.w3c.dom.Document myDOM = builder.parse(formInputStream); 
                                              
                     //Call for each field in the form 
                     String Amount = getNodeText("mortgageAmount", myDOM); 
                     String myLastName =  getNodeText("lastName", myDOM);  
                     String myFirstName = getNodeText("firstName", myDOM); 
                      
                     //Write the form data to the web browser 
                     pp.println("<p> The form data is :<br><br>" + 
                             "<li> The mortgage amount is "+ Amount+"" + 
                             "<li> Last name is "+ myLastName+"" + 
                             "<li> First name is "+ myFirstName+"")    ; 
                      } 
                 } 
             catch (Exception e) { 
                  e.printStackTrace(); 
               } 
         } 
              
         //This method returns the value of the specified node 
         private String getNodeText(String nodeName, org.w3c.dom.Document myDOM) 
         { 
           //Get the XML node by name 
           NodeList oList = myDOM.getElementsByTagName(nodeName); 
           Node myNode = oList.item(0);  
           NodeList oChildNodes = myNode.getChildNodes(); 
                                       
          String sText = ""; 
          for (int i = 0; i < oChildNodes.getLength(); i++) 
          { 
              Node oItem = oChildNodes.item(i); 
             if (oItem.getNodeType() == Node.TEXT_NODE) 
              { 
                sText = sText.concat(oItem.getNodeValue()); 
              } 
          } 
         return sText; 
         } 
     } 
 
```

## Avvio rapido (modalità SOAP): Creazione di documenti PDF con dati XML inviati tramite API Java {#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api}

Nell&#39;esempio di codice Java seguente vengono gestiti i dati del modulo inviati come XML. I dati del modulo vengono recuperati dall’invio tramite l’API Forms e inviati al servizio Output. I dati del modulo e una struttura del modulo vengono utilizzati per creare un documento PDF non interattivo. Il documento PDF non interattivo viene memorizzato in un nodo Content Services (obsoleto) denominato `/Company Home/Test Directory`. Il nome del modulo viene creato in modo dinamico. In altre parole, il nome e il cognome dell’utente vengono utilizzati per denominare il file PDF. L’identificatore della risorsa del nuovo contenuto viene scritto nel browser Web client. (Vedi [Creazione di documenti PDF con dati XML inviati](/help/forms/developing/rendering-forms.md#creating-pdf-documents-with-submitted-xml-data).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
     * 20. adobe-output-client.jar 
     * 21. adobe-contentservices-client.jar 
     * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
  
 import com.adobe.livecycle.contentservices.client.CRCResult; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
 import com.adobe.livecycle.contentservices.client.impl.UpdateVersionType; 
 import com.adobe.livecycle.formsservice.client.*; 
 import com.adobe.livecycle.output.client.OutputClient; 
 import com.adobe.livecycle.output.client.OutputResult; 
 import com.adobe.livecycle.output.client.PDFOutputOptionsSpec; 
 import com.adobe.livecycle.output.client.TransformationFormat; 
  
 import java.util.*; 
 import java.io.DataInputStream; 
 import java.io.File; 
 import java.io.InputStream; 
 import java.io.PrintWriter; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.InvocationRequest; 
 import com.adobe.idp.dsc.InvocationResponse; 
 import com.adobe.idp.dsc.clientsdk.ServiceClient; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 //Import DOM libraries 
 import org.w3c.dom.NodeList; 
 import org.w3c.dom.Node; 
 import javax.xml.parsers.*; 
  
 public class HandleDataSendToOutput extends HttpServlet implements Servlet { 
  
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
                 doPost(req,resp); 
         } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
         try{ 
             PrintWriter pp = resp.getWriter();      
              
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Get Form data to pass to the processFormSubmission method 
             Document formData = new Document(req.getInputStream());  
                          
             //Set run-time options 
              RenderOptionsSpec processSpec = new RenderOptionsSpec();  
              processSpec.setLocale("en_US"); 
              
             //Invoke the processFormSubmission method 
             FormsResult formOut = formsClient.processFormSubmission(formData, 
             "CONTENT_TYPE=text/xml", 
             "", 
             processSpec); 
              
             //Get the processing state 
             short processState = formOut.getAction(); 
                          
             //Determine if the form data is ready to be processed 
             //This code example checks only for submitted data (value is 0) 
             if (processState == 0)  
             { 
               //Determine the content type of the data 
               String myContentType = formOut.getContentType(); 
              
               if (myContentType.equals("application/vnd.adobe.xdp+xml"))    { 
              
                 //Get the form data 
                 Document formOutput = formOut.getOutputContent();  
                 InputStream formInputStream = new DataInputStream(formOutput.getInputStream());  
                  
                 //Create DocumentBuilderFactory and DocumentBuilder objects 
                 DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance(); 
                 DocumentBuilder builder = factory.newDocumentBuilder(); 
                 org.w3c.dom.Document myDOM = builder.parse(formInputStream); 
                                          
                 //Call for each field in the form 
                 String Amount = getNodeText("mortgageAmount", myDOM); 
                 String myLastName =  getNodeText("lastName", myDOM);  
                 String myFirstName = getNodeText("firstName", myDOM); 
                  
                 //Write the form data to the web browser 
                 pp.println("<p> The form data is :<br><br>" + 
                         "<li> The mortgage amount is "+ Amount+"" + 
                         "<li> Last name is "+ myLastName+"" + 
                         "<li> First name is "+ myFirstName+"")    ; 
                  
                  
                 //Create a non-interactive PDF document by invoking the Output service 
                 Document myPDFform = GeneratePDFDocument(myFactory, formOutput); 
                  
                 //Create the name of the PDF file to store 
                 String pdfName = "Loan_"+myLastName+"_"+myFirstName+".pdf" ; 
                 String userName = myFirstName+" "+myLastName ;  
                  
                 //Store the PDF form into Content Services (deprecated) 
                 String resourceID = StorePDFDocument(myFactory, myPDFform, pdfName,userName); 
                 pp.println("<p> The pdf document was store in :<br><br>" + 
                         "<li> /Company home "+ 
                         "<li> The identifier value of the new resource is "+ resourceID+""); 
                   } 
             } 
         } 
         catch (Exception e) { 
              e.printStackTrace(); 
           } 
     } 
          
      
     //Store the PDF document in /Company Home/Test Directory using the  
     //AEM Forms Content Service API 
     private String StorePDFDocument(ServiceClientFactory myFactory, com.adobe.idp.Document pdfDoc, String formName, String userName) 
     { 
         try 
         { 
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory); 
              
             //Specify the store and node name 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory"; 
              
             //Create a MAP instance to store attributes 
             Map<String,Object> inputs = new HashMap<String,Object>(); 
              
             //Specify attributes that belong to the new content 
             String creator = "{https://www.alfresco.org/model/content/1.0}creator"; 
             String description = "{https://www.alfresco.org/model/content/1.0}description";  
              
             inputs.put(creator,userName); 
             inputs.put(description,"A mortgage application form"); 
                                  
             //Store MortgageForm.pdf in /Company Home/Test Directory 
             CRCResult result = docManager.storeContent(storeName,  
                      nodeName, 
                      formName, 
                     "{https://www.alfresco.org/model/content/1.0}content",  
                     pdfDoc, 
                     "UTF-8", 
                     UpdateVersionType.INCREMENT_MAJOR_VERSION, 
                     null, 
                     inputs);  
             //Get the identifier value of the new resource 
             String id = result.getNodeUuid(); 
             return id;  
     } 
         catch (Exception ee) 
         { 
             ee.printStackTrace(); 
         } 
         return null ;  
     } 
      
      
     //This method returns the value of the specified node 
     private com.adobe.idp.Document GeneratePDFDocument(ServiceClientFactory myFactory, com.adobe.idp.Document formData) 
     { 
         try 
         { 
         //Create an OutputClient object 
         OutputClient outClient = new OutputClient(myFactory);  
              
         //Set PDF run-time options     
         com.adobe.livecycle.output.client.PDFOutputOptionsSpec outputOptions = new PDFOutputOptionsSpec(); 
         outputOptions.setLocale("en_US"); 
              
         //Set rendering run-time options 
         com.adobe.livecycle.output.client.RenderOptionsSpec pdfOptions = new com.adobe.livecycle.output.client.RenderOptionsSpec();  
         pdfOptions.setLinearizedPDF(true); 
                                  
         //Create a PDF document             
         OutputResult outputDocument = outClient.generatePDFOutput( 
             TransformationFormat.PDF, 
             "Loan.xdp", 
             "C:\\Adobe", 
             outputOptions, 
             pdfOptions, 
             formData 
         ); 
      
         //Get the Generated PDF file  
         Document ouputDoc = outputDocument.getGeneratedDoc(); 
         return ouputDoc ;  
         } 
         catch (Exception ee) 
         { 
             ee.printStackTrace(); 
         } 
         return null;  
     } 
      
     //This method returns the value of the specified node 
     private String getNodeText(String nodeName, org.w3c.dom.Document myDOM) 
     { 
       //Get the XML node by name 
       NodeList oList = myDOM.getElementsByTagName(nodeName); 
       Node myNode = oList.item(0);  
       NodeList oChildNodes = myNode.getChildNodes(); 
                                   
      String sText = ""; 
      for (int i = 0; i < oChildNodes.getLength(); i++) 
      { 
          Node oItem = oChildNodes.item(i); 
         if (oItem.getNodeType() == Node.TEXT_NODE) 
          { 
            sText = sText.concat(oItem.getNodeValue()); 
          } 
      } 
     return sText; 
     } 
 }
```

## Avvio rapido (modalità SOAP): Precompilazione di Forms con layout fluidi tramite l’API Java {#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api}

Nell&#39;esempio di codice seguente un modulo viene precompilato con un&#39;origine dati dinamica. In altre parole, l&#39;origine dati viene creata in fase di esecuzione e non è contenuta in un file XML o creata in fase di progettazione. Questo esempio di codice contiene tre metodi definiti dall&#39;utente:

* `createDataSource`: Crea un `org.w3c.dom.Document` oggetto che rappresenta l&#39;origine dati utilizzata per precompilare il modulo. Questo metodo definito dall&#39;utente restituisce il `org.w3c.dom.Document` oggetto.
* `convertDataSource`: Converte un `org.w3c.dom.Document` oggetto a un `com.adobe.idp.Document` oggetto. Questo metodo accetta un `org.w3c.dom.Document` come parametro di input e restituisce un `com.adobe.idp.Document` oggetto.
* `renderPOForm`: Utilizza l’API Java del servizio Forms per eseguire il rendering di un modulo di ordine di acquisto dinamico. La `com.adobe.idp.Document` oggetto restituito da `convertDataSource` viene utilizzato per precompilare il modulo.

   Tutti questi metodi sono invocati dall’interno del servlet Java `doPost` metodo . (Vedi [Precompilazione di Forms con layout fluidi](/help/forms/developing/rendering-forms.md#prepopulating-forms-with-flowable-layouts).)

```java
/*
* This Java Quick Start uses the following JAR files
* 1. adobe-forms-client.jar
* 2. adobe-livecycle-client.jar
* 3. adobe-usermanager-client.jar
* 4. activation.jar (required for SOAP mode)
* 5. axis.jar (required for SOAP mode)
* 6. commons-codec-1.3.jar (required for SOAP mode)
* 7. commons-collections-3.2.jar (required for SOAP mode)
* 8. commons-discovery.jar (required for SOAP mode)
* 9. commons-logging.jar (required for SOAP mode)
* 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
* 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
* 12. jaxrpc.jar (required for SOAP mode)
* 13. log4j.jar (required for SOAP mode)
* 14. mail.jar (required for SOAP mode)
* 15. saaj.jar (required for SOAP mode)
* 16. wsdl4j.jar (required for SOAP mode)
* 17. xalan.jar (required for SOAP mode)
* 18. xbean.jar (required for SOAP mode)
* 19. xercesImpl.jar (required for SOAP mode)
*
* (Because Forms quick starts are implemented as Java servlets, it is
* not necessary to include J2EE specific JAR files - the Java project
* that contains this quick start is exported as a WAR file which
* is deployed to the J2EE application server)
*
* These JAR files are located in the following path:
* <install directory>/sdk/client-libs/common
*
* For complete details about the location of these JAR files,
* see "Including AEM Forms library files" in Programming with AEM forms
*/
import java.io.IOException;
import javax.servlet.Servlet;
import javax.servlet.ServletException;
import javax.servlet.ServletOutputStream;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import com.adobe.livecycle.formsservice.client. * ;
import java.util. * ;
import java.io.ByteArrayOutputStream;
import java.io.InputStream;
import com.adobe.idp.Document;
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
import org.w3c.dom.Element;
import javax.xml.parsers. * ;
import javax.xml.transform. * ;
import javax.xml.transform.dom.DOMSource;
import javax.xml.transform.stream.StreamResult;
public class RenderDynamicForm extends HttpServlet implements Servlet {
 public void doGet(HttpServletRequest req, HttpServletResponse resp)
 throws ServletException,
 IOException {
  doPost(req, resp);
 }
 public void doPost(HttpServletRequest req, HttpServletResponse resp)
 throws ServletException,
 IOException {
  //Render a dynamic purchase order form
  //Create an org.w3c.dom.Document object
  org.w3c.dom.Document myDom = createDataSource();
  //Convert the org.w3c.dom.Document object
  //to a com.adobe.idp.Document object
  com.adobe.idp.Document formData = convertDataSource(myDom);
  //Render the dynamic form using data located within the
  //com.adobe.idp.Document object
  renderPOForm(resp, formData);
 }
 //Creates an org.w3c.dom.Document object
 private org.w3c.dom.Document createDataSource() {
  org.w3c.dom.Document document = null;
  try {
   //Create DocumentBuilderFactory and DocumentBuilder objects
   DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
   DocumentBuilder builder = factory.newDocumentBuilder();
   //Create a new Document object
   document = builder.newDocument();
   //Create the root element and append it to the XML DOM
   Element root = (Element) document.createElement("transaction");
   document.appendChild(root);
   //Create the header element
   Element header = (Element) document.createElement("header");
   root.appendChild(header);
   //Create the txtPONum element and append it to the
   //header element
   Element txtPONum = (Element) document.createElement("txtPONum");
   txtPONum.appendChild(document.createTextNode("8745236985"));
   header.appendChild(txtPONum);
   //Create the dtmDate element and append it to the
   //header element
   Element dtmDate = (Element) document.createElement("dtmDate");
   dtmDate.appendChild(document.createTextNode("2007-02-08"));
   header.appendChild(dtmDate);
   //Create the orderedByAddress element and append
   //it to the header element
   Element orderedByAddress = (Element) document.createElement("orderedByAddress");
   orderedByAddress.appendChild(document.createTextNode("222, Any Blvd"));
   header.appendChild(orderedByAddress);
   //Create the txtOrderedByPhone element and append
   //it to the header element
   Element txtOrderedByPhone = (Element) document.createElement("txtOrderedByPhone");
   txtOrderedByPhone.appendChild(document.createTextNode("(555) 555-2334"));
   header.appendChild(txtOrderedByPhone);
   //Create the txtOrderedByFax element and append
   //it to the header element
   Element txtOrderedByFax = (Element) document.createElement("txtOrderedByFax");
   txtOrderedByFax.appendChild(document.createTextNode("(555) 555-9334"));
   header.appendChild(txtOrderedByFax);
   //Create the txtOrderedByContactName element and append
   //it to the header element
   Element txtOrderedByContactName = (Element) document.createElement("txtOrderedByContactName");
   txtOrderedByContactName.appendChild(document.createTextNode("Frank Jones"));
   header.appendChild(txtOrderedByContactName);
   //Create the deliverToAddress element and append
   //it to the header element
   Element deliverToAddress = (Element) document.createElement("deliverToAddress");
   deliverToAddress.appendChild(document.createTextNode("555, Any Blvd"));
   header.appendChild(deliverToAddress);
   //Create the txtDeliverToPhone element and append
   //it to the header element
   Element txtDeliverToPhone = (Element) document.createElement("txtDeliverToPhone");
   txtDeliverToPhone.appendChild(document.createTextNode("(555) 555-9098"));
   header.appendChild(txtDeliverToPhone);
   //Create the txtDeliverToFax element and append
   //it to the header element
   Element txtDeliverToFax = (Element) document.createElement("txtDeliverToFax");
   txtDeliverToFax.appendChild(document.createTextNode("(555) 555-9000"));
   header.appendChild(txtDeliverToFax);
   //Create the txtDeliverToContactName element and
   //append it to the header element
   Element txtDeliverToContactName = (Element) document.createElement("txtDeliverToContactName");
   txtDeliverToContactName.appendChild(document.createTextNode("Jerry Johnson"));
   header.appendChild(txtDeliverToContactName);
   //Create the detail element and append it to the root
   Element detail = (Element) document.createElement("detail");
   root.appendChild(detail);

   //Create the txtPartNum element and append it to the
   //detail element
   Element txtPartNum = (Element) document.createElement("txtPartNum");
   txtPartNum.appendChild(document.createTextNode("00010-100"));
   detail.appendChild(txtPartNum);
   //Create the txtDescription element and append it
   //to the detail element
   Element txtDescription = (Element) document.createElement("txtDescription");
   txtDescription.appendChild(document.createTextNode("Monitor"));
   detail.appendChild(txtDescription);
   //Create the numQty element and append it to
   //the detail element
   Element numQty = (Element) document.createElement("numQty");
   numQty.appendChild(document.createTextNode("1"));
   detail.appendChild(numQty);
   //Create the numUnitPrice element and append it
   //to the detail element
   Element numUnitPrice = (Element) document.createElement("numUnitPrice");
   numUnitPrice.appendChild(document.createTextNode("350.00"));
   detail.appendChild(numUnitPrice);
   //Create another detail element named detail2 and
   //append it to root
   Element detail2 = (Element) document.createElement("detail");
   root.appendChild(detail2);
   //Create the txtPartNum element and append it to the
   //detail2 element
   Element txtPartNum2 = (Element) document.createElement("txtPartNum");
   txtPartNum2.appendChild(document.createTextNode("00010-200"));
   detail2.appendChild(txtPartNum2);
   //Create the txtDescription element and append it
   //to the detail2 element
   Element txtDescription2 = (Element) document.createElement("txtDescription");
   txtDescription2.appendChild(document.createTextNode("Desk lamps"));
   detail2.appendChild(txtDescription2);
   //Create the numQty element and append it to the
   //detail2 element
   Element numQty2 = (Element) document.createElement("numQty");
   numQty2.appendChild(document.createTextNode("3"));
   detail2.appendChild(numQty2);
   //Create the NUMUNITPRICE element
   Element numUnitPrice2 = (Element) document.createElement("numUnitPrice");
   numUnitPrice2.appendChild(document.createTextNode("55.00"));
   detail2.appendChild(numUnitPrice2);
  }
  catch(Exception e) {
   System.out.println("The following exception occurred: " + e.getMessage());
  }
  return document;

 }
 //Converts an org.w3c.dom.Document object to a
 //com.adobe.idp.Document object
 private Document convertDataSource(org.w3c.dom.Document myDOM) {
  byte[] mybytes = null;
  try {
   //Create a Java Transformer object
   TransformerFactory transFact = TransformerFactory.newInstance();
   Transformer transForm = transFact.newTransformer();
   //Create a Java ByteArrayOutputStream object
   ByteArrayOutputStream myOutStream = new ByteArrayOutputStream();
   //Create a Java Source object
   javax.xml.transform.dom.DOMSource myInput = new DOMSource(myDOM);
   //Create a Java Result object
   javax.xml.transform.stream.StreamResult myOutput = new StreamResult(myOutStream);
   //Populate the Java ByteArrayOutputStream object
   transForm.transform(myInput, myOutput);
   // Get the size of the ByteArrayOutputStream buffer
   int myByteSize = myOutStream.size();
   //Allocate myByteSize to the byte array
   mybytes = new byte[myByteSize];
   //Copy the content to the byte array
   mybytes = myOutStream.toByteArray();
  }
  catch(Exception e) {
   System.out.println("The following exception occurred: " + e.getMessage());
  }
  //Create a com.adobe.idp.Document object and copy the
  //contents of the byte array
  Document myDocument = new Document(mybytes);
  return myDocument;
 }
 //Render the purchase order form using the specified
 //com.adobe.idp.Document object
 private void renderPOForm(HttpServletResponse resp, Document formData) {
  try {
   //Set connection properties required to invoke AEM Forms
   Properties connectionProps = new Properties();
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL, ServiceC
   lientFactoryProperties.DSC_SOAP_PROTOCOL);
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
   //Create a ServiceClientFactory object
   ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
   //Create a FormsServiceClient object
   FormsServiceClient formsClient = new FormsServiceClient(myFactory);
   //Set the parameter values for the renderPDFForm method
   String formName = "Applications/FormsApplication/1.0/FormsFolder/PO.xdp";
   //Cache the form
   PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec();
   pdfFormRenderSpec.setCacheEnabled(new Boolean(true));
   //Specify URI values that are required to render a form
   URLSpec uriValues = new URLSpec();
   uriValues.setApplicationWebRoot("https://[server]:[port]/FormsQS");
   uriValues.setContentRootURI("repository:///");
   uriValues.setTargetURL("https://[server]:[port]/FormsQS/HandleData");
   //Invoke the renderForm method
   FormsResult formOut = formsClient.renderPDFForm(
   formName, //formQuery
   formData, //inDataDoc
   pdfFormRenderSpec, //PDFFormRenderSpec
   uriValues, //urlSpec
   null //attachments
   );
   //Create a ServletOutputStream object
   ServletOutputStream oOutput = resp.getOutputStream();
   //Create a Document object that stores form data
   Document myData = formOut.getOutputContent();
   //Create an InputStream object
   InputStream inputStream = myData.getInputStream();
   //Write the data stream to the web browser
   byte[] data = new byte[4096];
   int bytesRead = 0;
   while ((bytesRead = inputStream.read(data)) > 0) {
    oOutput.write(data, 0, bytesRead);
   }
  } catch(Exception e) {
   System.out.println("The following exception occurred: " + e.getMessage());
  }
 }
}
```

## Avvio rapido (modalità SOAP): Gestione di un modulo contenente uno script di calcolo tramite l’API Java {#quick-start-soap-mode-handling-a-form-containing-a-calculation-script-using-the-java-api}

Nell&#39;esempio di codice seguente viene elaborato un modulo contenente uno script di calcolo e i risultati vengono scritti nuovamente nel browser Web client. (Vedi [Calcolo dei dati del modulo](/help/forms/developing/rendering-forms.md#calculating-form-data).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class CalculateData extends HttpServlet implements Servlet { 
  
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp); 
     } 
  
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
              
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Get form data to pass to the processFormSubmission method 
             Document formData = new Document(req.getInputStream());  
  
             //Set run-time options 
             RenderOptionsSpec processSpec = new RenderOptionsSpec();  
             processSpec.setLocale("en_US"); 
                                    
             //Invoke the processFormSubmission method 
             FormsResult formOut = formsClient.processFormSubmission(formData,"CONTENT_TYPE=application/pdf&CONTENT_TYPE=application/vnd.adobe.xdp+xml","",processSpec); 
              
             //Get the processing state 
             short processState = formOut.getAction(); 
              
             //Determine if the form data is calculated 
             if (processState == 1)  
             { 
                  
                 //Write the data back to to the client web browser 
                 ServletOutputStream oOutput = resp.getOutputStream(); 
                 Document calData = formOut.getOutputContent(); 
                  
                 //Create an InputStream object 
                 InputStream inputStream = calData.getInputStream(); 
          
                 //Write the data stream to the web browser 
                 byte[] data = new byte[4096]; 
                 int bytesRead = 0; 
                 while ((bytesRead = inputStream.read(data)) > 0) 
                 { 
                     oOutput.write(data, 0, bytesRead); 
                 } 
              } 
             } 
         catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
         } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Ottimizzazione delle prestazioni tramite l’API Java {#quick-start-soap-mode-optimizing-performance-using-the-java-api}

L&#39;esempio di codice seguente ottimizza le prestazioni impostando le opzioni di memorizzazione in cache, autonoma e linearizzata. Un file linearizzato è ottimizzato per la distribuzione sul web. (Vedi [Ottimizzazione delle prestazioni del servizio Forms](/help/forms/developing/rendering-forms.md#optimizing-the-performance-of-the-forms-service).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderFormsPerformance extends HttpServlet implements Servlet { 
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp);  
     } 
  
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
     try{ 
              
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
         //Create a FormsServiceClient object 
         FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
         //Set the parameter values for the renderForm method 
         String formName = "Applications/FormsApplication/1.0/FormsFolder/Loan.xdp";  
         byte[]    cData = "".getBytes(); 
         Document oInputData = new Document(cData); 
                      
         //Set performance run-time options 
         PDFFormRenderSpec renderSpec = new PDFFormRenderSpec();  
         renderSpec.setCacheEnabled(new Boolean(true)); 
         renderSpec.setLinearizedPDF(true); 
                  
         //Specify URI values that are required to render a form 
         //design located in the AEM Forms Repository 
         URLSpec uriValues = new URLSpec();  
         uriValues.setApplicationWebRoot("https://[server]:[port]/FormsServiceClientApp"); 
         uriValues.setContentRootURI("repository:///"); 
         uriValues.setTargetURL("https://[server]:[port]/FormsServiceClientApp/HandleData"); 
                  
         //Invoke the renderPDFForm method and write the  
         //results to a client web browser 
         FormsResult formOut = formsClient.renderPDFForm( 
                     formName,       //formQuery 
                     oInputData,     //inDataDoc 
                     renderSpec,     //PDFFormRenderSpec 
                     uriValues,        //urlSpec 
                     null            //attachments 
                     ); 
          
         //Create a ServletOutputStream object 
         ServletOutputStream oOutput = resp.getOutputStream(); 
          
         //Create a Document object that stores form data 
         Document myData = formOut.getOutputContent(); 
          
         //Create an InputStream object 
         InputStream inputStream = myData.getInputStream(); 
          
         //Write the data stream to the web browser 
         byte[] data = new byte[4096]; 
         int bytesRead = 0; 
         while ((bytesRead = inputStream.read(data)) > 0) 
         { 
             oOutput.write(data, 0, bytesRead); 
         } 
          
         }catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
       } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Rendering per valore utilizzando l’API Java {#quick-start-soap-mode-rendering-by-value-using-the-java-api}

Il seguente avvio rapido Java esegue il rendering di un modulo interattivo PDF basato su una struttura del modulo denominata *Loan.xdp* per valore. Tenere presente che la struttura del modulo viene utilizzata per compilare un `com.adobe.idp.Document` oggetto denominato* inputXDP*. (Vedi [Rendering di Forms per valore](/help/forms/developing/rendering-forms.md#rendering-forms-by-value).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
    * 5. axis.jar (required for SOAP mode) 
    * 6. commons-codec-1.3.jar (required for SOAP mode) 
    * 7. commons-collections-3.2.jar  (required for SOAP mode) 
    * 8. commons-discovery.jar (required for SOAP mode) 
    * 9. commons-logging.jar (required for SOAP mode) 
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 12. jaxrpc.jar (required for SOAP mode) 
    * 13. log4j.jar (required for SOAP mode) 
    * 14. mail.jar (required for SOAP mode) 
    * 15. saaj.jar (required for SOAP mode) 
    * 16. wsdl4j.jar (required for SOAP mode) 
    * 17. xalan.jar (required for SOAP mode) 
    * 18. xbean.jar (required for SOAP mode) 
    * 19. xercesImpl.jar (required for SOAP mode) 
    * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms. 
     */ 
 import java.io.FileInputStream; 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
  
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderByValue extends HttpServlet implements Servlet { 
  
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp); 
     } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Retrieve the form design 
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.xdp");  
             Document inputXDP = new Document(fileInputStream); 
          
             //Specify URI values that are required to render a form 
             URLSpec uriValues = new URLSpec();  
             uriValues.setApplicationWebRoot("https://[server]:[port]/FormsQS"); 
             uriValues.setTargetURL("https://[server]:[port]/FormsQS/HandleData"); 
                      
             //Invoke the renderPDFForm method and pass the  
             //form design by value 
             FormsResult formOut = formsClient.renderPDFForm( 
                         "",                     //formQuery 
                         inputXDP,                 //inDataDoc 
                         new PDFFormRenderSpec(), //PDFFormRenderSpec 
                         uriValues,                //urlSpec 
                         null                    //attachments 
                         ); 
          
             //Create a Document object that stores form data 
             Document myData = formOut.getOutputContent(); 
          
             //Get the content type of the response and 
             //set the HttpServletResponse object?s content type 
             String contentType = myData.getContentType();  
             resp.setContentType(contentType); 
          
             //Create a ServletOutputStream object 
             ServletOutputStream oOutput = resp.getOutputStream(); 
          
             //Create an InputStream object 
             InputStream inputStream = myData.getInputStream(); 
          
             //Write the data stream to the web browser 
             byte[] data = new byte[4096]; 
             int bytesRead = 0; 
             while ((bytesRead = inputStream.read(data)) > 0) 
             { 
                 oOutput.write(data, 0, bytesRead); 
             } 
          
             }catch (Exception e) { 
                  e.printStackTrace(); 
               } 
         } 
 }
```

## Avvio rapido (modalità SOAP): Trasmissione di documenti al servizio Forms tramite l’API Java {#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api}

Il seguente avvio rapido Java recupera il file Loan.xdp da Content Services (obsoleto). Questo file XDP si trova nello spazio `/Company Home/Form Designs`. Il file XDP viene restituito in un `com.adobe.idp.Document` istanza. La `com.adobe.idp.Document` viene passata al servizio Forms. Il modulo interattivo viene scritto in un browser Web client. (Vedi [Trasmissione di documenti al servizio Forms](/help/forms/developing/passing-documents-forms-service.md).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-contentservices-client.jar 
     * 3. adobe-livecycle-client.jar 
     * 4. adobe-usermanager-client.jar 
     * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms. 
     */ 
 import java.io.IOException; 
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
  
 import com.adobe.livecycle.contentservices.client.CRCResult; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
 import com.adobe.livecycle.formsservice.client.*; 
  
 import java.util.*; 
 import java.io.InputStream; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderFormsFromContentServices extends HttpServlet implements Servlet { 
  
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp); 
     } 
      
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
         try{ 
             //Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
                          
             //Create an empty Document that represents form data 
             byte[]    cData = "".getBytes(); 
             Document oInputData = new Document(cData); 
              
             //Get the form design from Content Services (deprecated) 
             Document formDesign =  GetFormDesign(myFactory); 
                                      
             //Cache the PDF form 
             PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec(); 
             pdfFormRenderSpec.setCacheEnabled(new Boolean(true)); 
                      
             //Invoke the renderPDFForm2 and pass to the  
             //Document that contains the form design 
             FormsResult formOut = formsClient.renderPDFForm2( 
                     formDesign,               
                     oInputData,              
                     pdfFormRenderSpec,       
                     null,                 
                     null             
                     ); 
          
             //Create a Document object that stores form data 
             Document myData = formOut.getOutputContent(); 
          
             //Get the content type of the response and 
             //set the HttpServletResponse object?s content type 
             String contentType = myData.getContentType();  
             resp.setContentType(contentType); 
          
             //Create a ServletOutputStream object 
             ServletOutputStream oOutput = resp.getOutputStream(); 
          
             //Create an InputStream object 
             InputStream inputStream = myData.getInputStream(); 
          
             //Write the data stream to the web browser 
             byte[] data = new byte[4096]; 
             int bytesRead = 0; 
             while ((bytesRead = inputStream.read(data)) > 0) 
             { 
                 oOutput.write(data, 0, bytesRead); 
             } 
          
             }catch (Exception e) { 
                  e.printStackTrace(); 
               } 
         } 
          
     //Retrieve the form design from Content Services (deprecated) 
     private Document GetFormDesign(ServiceClientFactory myFactory) 
     { 
         try{ 
              
         //Create a DocumentManagementServiceClientImpl object 
         DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
         //Specify the name of the store and the content to retrieve 
            String storeName = "SpacesStore"; 
            String nodeName  = "/Company Home/Form Designs/Loan.xdp"; 
  
            //Retrieve /Company Home/Form Designs/Loan.xdp 
            CRCResult content = docManager.retrieveContent( 
                      storeName, 
                      nodeName, 
                      ""); 
      
            //Return the Document instance 
             Document doc =content.getDocument();  
             return  doc; 
          } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
         return null;  
     } 
      
 } 
 
```
