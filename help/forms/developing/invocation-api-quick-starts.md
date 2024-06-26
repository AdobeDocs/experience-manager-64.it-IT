---
title: Avvio rapido API di richiamo
seo-title: Invocation API Quick Starts
description: Utilizza Avvio rapido per richiamare programmaticamente i servizi AEM Forms.
seo-description: Use the Quick Starts to programmatically invoke AEM Forms services.
uuid: acf67177-98a4-4c99-95a5-3086907d7c2c
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: dcf83c9f-b818-44a2-9079-80a4fc357c4f
role: Developer
exl-id: dcfc1c9f-fedd-4e00-9b09-19268620fc6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 4%

---

# Avvio rapido API di richiamo {#invocation-api-quick-starts}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per richiamare programmaticamente i servizi AEM Forms sono disponibili i seguenti Quick Starts:

<table> 
 <thead> 
  <tr> 
   <th><p>Descrizione</p></th> 
   <th><p>API remota</p></th> 
   <th><p>API Java</p></th> 
   <th><p>API del servizio Web</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-human-centric-long-lived.md#invoking_human_centric_long_lived_processes">Richiamo dei processi a lunga durata incentrati sull'uomo</a></p></td> 
   <td><p><a href="/help/forms/developing/invoking-human-centric-long-lived.md#invoking-a-long-lived-process-using-remoting">Richiamare un processo di lunga durata utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting</a></p></td> 
   <td><p><a href="/help/forms/developing/invoking-human-centric-long-lived.md#quick_start_invoking_a_long_lived_process_using_the_invocation_api">Avvio rapido: Richiamare un processo di lunga durata utilizzando l’API di richiamo</a></p></td> 
   <td><p><a href="/help/forms/developing/invoking-human-centric-long-lived.md#quick_start_invoking_a_long_lived_process_using_the_web_service_api">Avvio rapido: Richiamare un processo di lunga durata utilizzando l’API del servizio Web</a></p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-java.md#invoking_a_short_lived_process_using_the_invocation_api">Richiamare un processo di breve durata utilizzando l’API di richiamo</a></p></td> 
   <td><p>N/D</p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick_start_invoking_a_short_lived_process_using_the_invocation_api">Avvio rapido: Richiamare un processo di breve durata utilizzando l’API di richiamo</a></p></td> 
   <td><p>N/D</p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding">Richiamo di AEM Forms con codifica Base64</a> (proxy del servizio web Java)</p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick_start_invoking_a_service_using_java_proxy_files_and_base64_encoding">Avvio rapido: Richiamo di un servizio tramite file proxy Java e codifica Base64</a></p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding">Richiamo di AEM Forms con codifica Base64</a> (proxy servizio Web .NET)</p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick_start_invoking_a_service_using_base64_in_a_microsoft_net_project">Avvio rapido: Richiamo di un servizio utilizzando base64 in un progetto Microsoft .NET</a></p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom">Richiamo di AEM Forms tramite MTOM</a> (esempio di servizio Web .NET)</p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick_start_invoking_a_service_using_mtom_in_a_net_project">Avvio rapido: Richiamo di un servizio utilizzando MTOM in un progetto .NET</a></p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref">Richiamo di AEM Forms tramite SwaRef</a> (esempio di servizio web Java)</p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick_start_invoking_a_service_using_swaref_in_a_java_project">Avvio rapido: Richiamo di un servizio utilizzando SwaRef in un progetto Java</a></p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http">Richiamo di dati AEM Forms tramite BLOB su HTTP</a> (esempio di servizio web Java)</p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick_start_invoking_a_service_using_blob_data_over_http_in_a_net_project">Avvio rapido: Richiamo di un servizio utilizzando dati BLOB su HTTP in un progetto .NET</a></p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http">Richiamo di dati AEM Forms tramite BLOB su HTTP</a> (esempio di servizio Web .NET)</p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick_start_invoking_a_service_using_blob_data_over_http_in_a_java_project">Avvio rapido: Richiamo di un servizio utilizzando dati BLOB su HTTP in un progetto Java</a></p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime">Richiamo di AEM Forms tramite DIME</a> (esempio di servizio web Java)</p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick_start_invoking_a_service_using_dime_in_a_java_project">Avvio rapido: Richiamo di un servizio tramite DIME in un progetto Java</a></p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting">Richiamo di AEM Forms utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting</a></p></td> 
   <td><p><a href="invocation-api-quick-starts.md#quick-start-invoking-a-short-lived-process-by-passing-an-unsecure-document-using-deprecated-for-aem-forms-aem-forms-remoting">Avvio rapido: Richiamare un processo di breve durata passando un documento non sicuro utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting</a></p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#passing_secure_documents_to_invoke_processes_using_remoting">Trasferimento di documenti protetti per richiamare i processi utilizzando Remoting</a></p></td> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#quick-start-invoking-a-short-lived-process-by-passing-a-secure-document-using-remoting">Avvio rapido: Richiamare un processo di breve durata passando un documento protetto utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting</a></p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
  </tr> 
  <tr> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking_custom_component_services_using_remoting">Richiamo dei servizi dei componenti personalizzati tramite Remoting</a></p></td> 
   <td><p><a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#quick-start-invoking-the-customer-custom-service-using-remoting">Avvio rapido: Richiamo del servizio personalizzato del cliente utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting</a></p></td> 
   <td><p>N/D</p></td> 
   <td><p>N/D</p></td> 
  </tr> 
 </tbody> 
</table>

Le operazioni AEM Forms possono essere eseguite utilizzando l’API fortemente tipizzata di AEM Forms e la modalità di connessione deve essere impostata su SOAP.

>[!NOTE]
>
>Gli avvii rapidi disponibili in Programmazione con moduli AEM si basano sul server Forms distribuito su JBoss Application Server e sul sistema operativo Microsoft Windows. Tuttavia, se si utilizza un altro sistema operativo, ad esempio UNIX, sostituire percorsi specifici di Windows con percorsi supportati dal sistema operativo applicabile. Allo stesso modo, se utilizzi un altro server applicativo J2EE, assicurati di specificare proprietà di connessione valide. Vedi [Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Avvio rapido: Richiamare un processo di breve durata utilizzando l’API di richiamo {#quick-start-invoking-a-short-lived-process-using-the-invocation-api}

Il seguente esempio di codice Java richiama un processo di breve durata denominato `MyApplication/EncryptDocument`. Tieni presente che questo processo viene richiamato in modo sincrono. Il parametro di input per questo processo è denominato `inDoc`. Il parametro di output per questo processo è denominato `outDoc`. Il documento PDF crittografato con password viene salvato come file PDF denominato `EncryptLoan.pdf`. (Vedi [Richiamare un processo di breve durata utilizzando l’API di richiamo](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-short-lived-process-using-the-invocation-api).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-convertpdf-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 7. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.io.InputStream; 
 import java.util.HashMap; 
 import java.util.Map; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.InvocationRequest; 
 import com.adobe.idp.dsc.InvocationResponse; 
 import com.adobe.idp.dsc.clientsdk.ServiceClient; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
      
  
     public class InvokeDocumentEncryptLooselyTypedAPI { 
  
         public static void main(String[] args) 
         { 
         try 
         { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
             // Create a ServiceClientFactory instance 
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); 
              
             //Create a ServiceClient object 
             ServiceClient myServiceClient = factory.getServiceClient(); 
  
             //Create a Map object to store the parameter value 
             Map params = new HashMap(); 
               
             InputStream inFile = new FileInputStream("C:\\Adobe\Loan.pdf"); 
             Document inDoc = new Document(inFile); 
              
             //Populate the Map object with a parameter value  
             //required to invoke the MyApplication/EncryptDocument short-lived process 
             //inDoc refers to the name of the input parameter for the process 
             params.put("inDoc", inDoc);  
  
             //Create an InvocationRequest object 
             InvocationRequest request =  factory.createInvocationRequest( 
                     "MyApplication/EncryptDocument",        //Specify the short-lived process name 
                     "invoke",           //Specify the operation name     
                     params,               //Specify input values 
                     true);               //Create a synchronous request  
  
             //Send the invocation request to the short-lived process and  
             //get back an invocation response -- outDoc refers to the output parameter for the  
             //MyApplication/EncryptDocument process 
             InvocationResponse response = myServiceClient.invoke(request); 
             Document encryptDoc = (Document) response.getOutputParameter("outDoc"); 
              
             //Save the encrypted PDF document returned by the process 
             //Save the password-encrypted PDF document 
             File outFile = new File("C:\\Adobe\EncryptLoan.pdf"); 
             encryptDoc.copyToFile (outFile); 
             }catch (Exception e) { 
                 e.printStackTrace(); 
             } 
         } 
 }
```

## Avvio rapido: Richiamo di un servizio utilizzando base64 in un progetto Microsoft .NET {#quick-start-invoking-a-service-using-base64-in-a-microsoft-net-project}

Il seguente esempio di codice C# richiama un processo denominato `MyApplication/EncryptDocument` da un progetto Microsoft .NET che utilizza la codifica Base64. (Vedi [Richiamo di AEM Forms con codifica Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

Un documento PDF non protetto basato su un file PDF denominato *Loan.pdf* viene passato al processo AEM Forms. Il processo restituisce un documento PDF crittografato con password salvato come file PDF denominato *EncryptedPDF.pdf*.

```as3
 /* 
     * Ensure that you create a .NET client assembly that uses  
     * base64 encoding. This is required to populate a BLOB  
     * object with data or retrieve data from a BLOB object. 
     * 
     * For information, see "Invoking AEM Forms using Base64 Encoding" in  
     * Programming with AEM forms 
     */ 
 using System; 
 using System.Collections; 
 using System.ComponentModel; 
 using System.Data; 
 using System.IO; 
  
 namespace InvokeEncryptDocumentBase64 
 { 
  
        class InvokeEncryptDocumentUsingBase64 
        { 
  
            const int BUFFER_SIZE = 4096; 
            [STAThread] 
            static void Main(string[] args) 
            { 
  
                try 
                { 
                    String pdfFile = "C:\\Adobe\Loan.pdf"; 
                    String encryptedPDF = "C:\\Adobe\EncryptedPDF.pdf"; 
  
  
                    //Create an MyApplication_EncryptDocumentService object and set authentication values 
                    MyApplication2_EncryptDocumentService encryptClient = new MyApplication2_EncryptDocumentService(); 
                    encryptClient.Credentials = new System.Net.NetworkCredential("administrator", "password"); 
  
                    //Reference the PDF file to send to the EncryptDocument process 
                    FileStream fs = new FileStream(pdfFile, FileMode.Open); 
      
                    //Create a BLOB object 
                    BLOB inDoc = new BLOB(); 
  
                    //Get the length of the file stream  
                    int len = (int)fs.Length; 
                    byte[] ByteArray = new byte[len]; 
  
                    //Populate the byte array with the contents of the FileStream object 
                    fs.Read(ByteArray, 0, len); 
                    inDoc.binaryData = ByteArray;  
      
                    //Invoke the EncryptDocument process 
                    BLOB outDoc = encryptClient.invoke(inDoc); 
  
                    //Populate a byte array with BLOB data 
                    byte[] outByteArray = outDoc.binaryData; 
  
                    //Create a new file named UsageRightsLoan.pdf 
                    FileStream fs2 = new FileStream(encryptedPDF, FileMode.OpenOrCreate); 
  
                    //Create a BinaryWriter object 
                    BinaryWriter w = new BinaryWriter(fs2); 
                    w.Write(outByteArray); 
                    w.Close(); 
                    fs2.Close(); 
                 } 
                catch (Exception ee) 
                { 
                    Console.WriteLine(ee.Message); 
                } 
            } 
        } 
 } 
 
```

## Avvio rapido: Richiamo di un servizio tramite file proxy Java e codifica Base64 {#quick-start-invoking-a-service-using-java-proxy-files-and-base64-encoding}

Il seguente esempio di codice Java richiama un processo denominato `MyApplication/EncryptDocument` utilizzo di file proxy Java creati con codifica JAX-WS e Base64. (Vedi [Richiamo di AEM Forms con codifica Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

Un documento PDF non protetto basato su un file PDF denominato *Loan.pdf* viene passato al processo AEM Forms. Il processo restituisce un documento PDF crittografato con password salvato come file PDF denominato *EncryptedDocument.pdf*.

```as3
 /** 
     * Ensure that you create Java proxy files that consume 
     * the AEM Forms service WSDL. You can use JAX-WS to create 
     * the Java proxy files.   
     * 
     * This Java quick start uses Base64 to invoke a short-lived process named 
     * EncryptDocument. For information, see  
     * "Invoking AEM Forms using Base64" in Programming with AEM forms.   
     */ 
  
 import java.io.*; 
  
 import javax.xml.ws.BindingProvider; 
 import com.adobe.idp.services.*; 
  
 public class InvokeEncryptDocumentBase64 { 
     public static void main(String[] args){ 
          
         try{ 
             //Create a MyApplicationEncryptDocument object 
             MyApplicationEncryptDocumentService encClient = new MyApplicationEncryptDocumentService(); 
             MyApplicationEncryptDocument encryptDocClient = encClient.getEncryptDocument(); 
              
             //Set connection values required to invoke AEM Forms 
             String url = "[server]:[port]/soap/services/MyApplication/EncryptDocument?blob=base64"; 
             String username = "administrator"; 
             String password = "password"; 
             ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url); 
             ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username); 
             ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password); 
              
                // Get the input PDF document to send to the EncryptDocument process 
                BLOB inDoc = new BLOB(); 
              
             // Get the input DDX document and input PDF sources 
             File fileName = new File("C:\\Adobe\Loan.pdf"); 
             FileInputStream inFs = new FileInputStream(fileName);  
                          
             // Get the length of the file stream and create a byte array 
             int inLen = (int)fileName.length(); 
             byte[] inByteArray = new byte[inLen]; 
              
                // Populate the byte array with the content of the file stream 
             inFs.read(inByteArray, 0, inLen); 
                   
                // Populate the BLOB objects 
             inDoc.setBinaryData(inByteArray); 
              
                //invoke the short-lived process named MyApplication/EncryptDocument 
             BLOB outDoc = encryptDocClient.invoke(inDoc); 
              
             //Save the encrypted file as a PDF file 
             byte[] encryptedDocument = outDoc.getBinaryData(); 
              
             //Create a File object 
             File outFile = new File("C:\\Adobe\EncryptedDocument.pdf"); 
              
             //Create a FileOutputStream object. 
             FileOutputStream myFileW = new FileOutputStream(outFile); 
              
             //Call the FileOutputStream object's write method and pass the pdf data 
             myFileW.write(encryptedDocument); 
              
             //Close the FileOutputStream object 
             myFileW.close(); 
                System.out.println("The short-lived process named MyApplication/EncryptDocument was successfully invoked.");             
         } 
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
      
     } 
  
 } 
  
 
```

## Avvio rapido: Richiamare un processo di breve durata passando un documento non sicuro utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting {#quick-start-invoking-a-short-lived-process-by-passing-an-unsecure-document-using-deprecated-for-aem-forms-aem-forms-remoting}

L&#39;esempio di codice Flex seguente richiama un processo di breve durata denominato `MyApplication/EncryptDocument`. (Vedi [Richiamo di AEM Forms utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

>[!NOTE]
>
>Questo avvio rapido richiama un processo AEM Forms e carica un documento non sicuro. Per eseguire questo avvio rapido, AEM Forms deve essere configurato per caricare documenti non sicuri. Per informazioni su come configurare AEM Forms per l’accettazione di documenti non sicuri, consulta [Configurazione di AEM Forms per accettare documenti sicuri e non protetti](/help/forms/developing/invoking-aem-forms-using-remoting.md#configuring-aem-forms-to-accept-secure-and-unsecure-documents).

```as3
 <?xml version="1.0" encoding="utf-8"?> 
 <mx:Application  xmlns="*"  
      creationComplete="initializeChannelSet();"> 
      <mx:Script> 
        <![CDATA[ 
      
      import mx.rpc.AEM Forms.DocumentReference; 
      import flash.net.FileReference; 
      import flash.net.URLRequest; 
      import flash.events.Event; 
      import flash.events.DataEvent; 
      import mx.messaging.ChannelSet; 
      import mx.messaging.channels.AMFChannel;   
      import mx.rpc.events.ResultEvent; 
      import mx.collections.ArrayCollection; 
      import mx.rpc.AsyncToken; 
      
       // Classes used in file retrieval   
      private var fileRef:FileReference = new FileReference(); 
      private var docRef:DocumentReference = new DocumentReference(); 
      private var parentResourcePath:String = "/"; 
      private var serverPort:String = "[server]:[port]"; 
      private var now1:Date;     
      private  var cs:ChannelSet 
      
      // Holds information returned from AEM Forms 
      [Bindable] 
      public var progressList:ArrayCollection = new ArrayCollection(); 
      
      // Set up channel set to invoke AEM Forms. 
      // This must be done before calling any service or process, but only  
      // once for the entire application. 
       private function initializeChannelSet():void { 
        cs = new ChannelSet();  
        cs.addChannel(new AMFChannel("remoting-amf", "https://" + serverPort + "/remoting/messagebroker/amf"));  
        EncryptDocument.setCredentials("administrator", "password"); 
        EncryptDocument.channelSet = cs; 
      } 
      
      // Call this method to upload the file. 
      // This creates a file picker and lets the user select a PDF file to pass to the EncryptDocument process. 
      private function uploadFile():void { 
        fileRef.addEventListener(Event.SELECT, selectHandler); 
        fileRef.browse(); 
      } 
      
       private function selectHandler(event:Event):void 
             { 
             var authTokenService:RemoteObject = new RemoteObject("LC.FileUploadAuthenticator"); 
             authTokenService.addEventListener("result", authTokenReceived); 
             authTokenService.channelSet = cs; 
             authTokenService.getFileUploadToken(); 
             } 
      
     private function authTokenReceived(event:ResultEvent):void 
             { 
             var token:String = event.result as String; 
             var request:URLRequest = DocumentReference.constructRequestForUpload("https://[server]:[port]", token); 
              
             try 
             { 
           fileRef.upload(request); 
             } 
             catch (error:Error) 
             { 
             trace("Unable to upload file."); 
             }                               
             } 
  
      
      // Called once the file is completely uploaded. 
      private function completeHandler(event:DataEvent):void {                     
        now1 = new Date(); 
      
        // Set the docRefs url and referenceType parameters 
        docRef.url = event.data as String;       
        docRef.referenceType=DocumentReference.REF_TYPE_URL; 
        executeInvokeProcess();  
      }       
      
      //This method invokes the EncryptDocument process 
      public function executeInvokeProcess():void { 
      
         //Create an Object to store the input value for the EncryptDocument process 
         var params:Object = new Object(); 
         params["inDoc"]=docRef; 
      
         // Invoke the EncryptDocument process 
         var token:AsyncToken;             
         token = EncryptDocument.invoke(params); 
         token.name = name; 
      } 
      
      // This method handles a successful conversion invocation 
      public function handleResult(event:ResultEvent):void 
      { 
            //Retrieve information returned from the service invocation 
          var token:AsyncToken = event.token;         
          var res:Object = event.result; 
          var dr:DocumentReference = res["outDoc"] as DocumentReference; 
          var now2:Date = new Date(); 
      
          // These fields map to columns in the DataGrid 
          var progObject:Object = new Object(); 
          progObject.filename = token.name; 
          progObject.timing = (now2.time - now1.time).toString(); 
          progObject.state = "Success"; 
          progObject.link = "<a href=" + dr.url + "> open </a>"; 
          progressList.addItem(progObject); 
      } 
      
      private function resultHandler(event:ResultEvent):void { 
        // Do anything else here. 
      } 
  
        ]]> 
      </mx:Script> 
      <mx:RemoteObject id="EncryptDocument" destination="MyApplication/EncryptDocument" result="resultHandler(event);"> 
          <mx:method name="invoke" result="handleResult(event)"/> 
      </mx:RemoteObject> 
      
      <!--//This consists of what is displayed on the webpage--> 
      <mx:Panel id="lcPanel" title="EncryptDocument  (Deprecated for AEM forms) AEM Forms Remoting Example"  
           height="25%" width="25%" paddingTop="10" paddingLeft="10" paddingRight="10"  
           paddingBottom="10"> 
         <mx:Label width="100%" color="blue" 
                text="Select a PDF file to pass to the EncryptDocument process"/>  
        <mx:DataGrid x="10" y="0" width="500" id="idProgress" editable="false"  
           dataProvider="{progressList}" height="231" selectable="false" > 
          <mx:columns> 
            <mx:DataGridColumn headerText="Filename" width="200" dataField="filename" editable="false"/> 
            <mx:DataGridColumn headerText="State" width="75" dataField="state" editable="false"/> 
            <mx:DataGridColumn headerText="Timing" width="75" dataField="timing" editable="false"/> 
            <mx:DataGridColumn headerText="Click to Open" dataField="link" editable="false" > 
             <mx:itemRenderer> 
                <mx:Component> 
                   <mx:Text x="0" y="0" width="100%" htmlText="{data.link}"/> 
                </mx:Component> 
             </mx:itemRenderer> 
            </mx:DataGridColumn> 
          </mx:columns> 
        </mx:DataGrid> 
        <mx:Button label="Select File" click="uploadFile()" /> 
      </mx:Panel> 
 </mx:Application> 
 
```

## Avvio rapido: Richiamo di un servizio tramite DIME in un progetto .NET {#quick-start-invoking-a-service-using-dime-in-a-net-project}

Il seguente esempio di codice C# richiama un processo denominato `MyApplication/EncryptDocument` da un progetto Microsoft .NET che utilizza Dime. (Vedi [Richiamo di AEM Forms con codifica Base64](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

Un documento PDF non protetto basato su un file PDF denominato *map.pdf* viene passato al processo AEM Forms utilizzando DIME. Il processo restituisce un documento PDF crittografato con password salvato come file PDF denominato *mapEncrypt.pdf*.

```as3
 /** 
     * 
     * Ensure that you create a .NET project that uses  
     * Web Services Enhancements 2.0. This is required to send a  
     * AEM Forms process an attachment using DIME. 
     * 
     * For information, see "Invoking AEM Forms using DIME" in Programming with AEM forms.   
     */ 
  
 using System; 
 using System.Collections; 
 using System.ComponentModel; 
 using System.Data; 
 using System.IO; 
 using Microsoft.Web.Services2.Dime; 
 using Microsoft.Web.Services2.Attachments; 
 using Microsoft.Web.Services2.Configuration; 
 using Microsoft.Web.Services2; 
  
 //The following statement represents a web reference to 
 //the forms server that contains the process that 
 //is invoked 
 using ConsoleApplication1.LC_Host; 
  
 namespace ConsoleApplication1 
 { 
  
      class InvokeEncryptDocumentUsingDime 
        { 
  
            const int BUFFER_SIZE = 4096; 
            [STAThread] 
            static void Main(string[] args) 
            { 
  
            try 
               { 
                   String pdfFile = "C:\\Adobe\map.pdf"; 
                   String encryptedPDF = "C:\\Adobe\mapEncrypt.pdf"; 
      
                   //Create an EncryptDocumentServiceWse object and set authentication values 
                   EncryptDocumentServiceWse encryptClient = new EncryptDocumentServiceWse(); 
                   encryptClient.Credentials = new System.Net.NetworkCredential("administrator", "password"); 
  
                   // Create the DIME attachment representing a PDF document 
                   DimeAttachment inputDocAttachment = new DimeAttachment( 
                       System.Guid.NewGuid().ToString(), 
                       "application/pdf", 
                       TypeFormat.MediaType, 
                       pdfFile); 
      
                    //Create a BLOB object 
                    BLOB inDoc = new BLOB(); 
      
                    //Set the DIME attachment ID 
                    inDoc.attachmentID = inputDocAttachment.Id; 
                    encryptClient.RequestSoapContext.Attachments.Add(inputDocAttachment); 
      
                    //Invoke the EncryptDocument process 
                    BLOB outDoc = encryptClient.invoke(inDoc); 
      
                    //Get the returned attachment identifier value     
                    String encryptedDocId = outDoc.attachmentID; 
                    FileStream myStream = new FileStream(encryptedPDF, FileMode.Create, FileAccess.Write); 
      
                    //Iterate through the attachments 
                    foreach (Attachment attachment in encryptClient.ResponseSoapContext.Attachments) 
                      { 
                        if (attachment.Id.Equals(encryptedDocId)) 
                          { 
                            //Create a byte array that contains the encrypted PDF document 
                            System.IO.Stream mySteam2 = attachment.Stream; 
                            byte[] myBytes = new byte[mySteam2.Length]; 
                            int size = (int)mySteam2.Length; 
                            mySteam2.Read(myBytes, 0, size); 
      
                            //Save the encrypted PDF document as a PDF file 
                            FileStream fs2 = new FileStream(encryptedPDF, FileMode.OpenOrCreate); 
      
                            //Create a BinaryWriter object 
                            BinaryWriter w = new BinaryWriter(fs2); 
                            w.Write(myBytes); 
                            w.Close(); 
                            fs2.Close(); 
                            Console.Out.WriteLine("Saved converted document at:" + encryptedPDF); 
                        } 
                   } 
                } 
                catch (Exception ee) 
               { 
                   Console.WriteLine(ee.Message); 
                } 
            } 
        } 
 } 
 
```

## Avvio rapido: Richiamo di un servizio tramite DIME in un progetto Java {#quick-start-invoking-a-service-using-dime-in-a-java-project}

Il seguente esempio di codice Java richiama un processo denominato `MyApplication/EncryptDocument` utilizzando DIME. (Vedi [Richiamo di AEM Forms tramite DIME](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime).)

Un documento PDF non protetto basato su un file PDF denominato *Loan.pdf* viene passato al processo AEM Forms utilizzando DIME. Il processo restituisce un documento PDF crittografato con password salvato come file PDF denominato *EncryptLoan.pdf*.

```as3
 /** 
     * Ensure that you create Java Axis files that  
     * are required to send a AEM Forms process  
     * an attachment using DIME. 
     * 
     * For information, see "Invoking AEM Forms using DIME" in Programming with AEM forms.   
     */ 
 import com.adobe.idp.services.*; 
 import java.io.File; 
 import java.io.FileOutputStream; 
 import java.io.InputStream; 
 import java.net.URL; 
 import javax.activation.DataHandler; 
 import javax.activation.FileDataSource; 
  
 import org.apache.axis.attachments.AttachmentPart; 
  
 public class InvokeDocumentEncryptDime { 
     public static void main(String[] args) { 
      
     try{ 
          
         //Create a MyApplicationEncryptDocumentServiceLocator object 
         MyApplicationEncryptDocumentServiceLocator locate = new MyApplicationEncryptDocumentServiceLocator (); 
  
         //specify the service target URL and object type 
         URL serviceURL = new URL("https://[server]:[port]/soap/services/MyApplication/EncryptDocument?blob=dime"); 
          
         //Use the binding stub with the locator 
         EncryptDocumentSoapBindingStub encryptionClientStub = new EncryptDocumentSoapBindingStub(serviceURL,locate); 
         encryptionClientStub.setUsername("administrator"); 
         encryptionClientStub.setPassword("password");     
              
          //Get the DIME Attachments - which is the PDF document to encrypt 
          java.io.File file = new java.io.File("C:\\Adobe\Loan.pdf"); 
                        
          //Create a DataHandler object 
          DataHandler buildFile = new DataHandler(new FileDataSource(file)); 
           
          //Use the DataHandler object to create an AttachmentPart object  
          AttachmentPart part = new AttachmentPart(buildFile); 
         //get the attachment ID 
         String attachmentID = part.getContentId();     
          
         //Add the attachment to the encryption service stub 
         encryptionClientStub.addAttachment(part);  
                                  
         //Inform ES where the attachment is stored by providing the attachment id 
         BLOB inDoc = new BLOB(); 
         inDoc.setAttachmentID(attachmentID); 
                          
         BLOB outDoc = encryptionClientStub.invoke(inDoc); 
  
         //Go through the returned attachments and get the encrypted PDF document 
         byte[] resultByte = null;         
         attachmentID = outDoc.getAttachmentID(); 
          
         //Find the proper attachment 
         Object[] parts = encryptionClientStub.getAttachments(); 
         for (int i=0;i<parts.length;i++){ 
             AttachmentPart attPart = (AttachmentPart)  parts[i]; 
             if (attPart.getContentId().equals(attachmentID)) { 
                 //DataHandler 
                 buildFile = attPart.getDataHandler(); 
                 InputStream stream = buildFile.getInputStream();  
                  
                 byte[] pdfStream = new byte[stream.available()]; 
                 stream.read(pdfStream); 
                  
                 //Create a File object 
                 File outFile = new File("C:\\Adobe\EncryptLoan.pdf"); 
                  
                 //Create a FileOutputStream object. 
                 FileOutputStream myFileW = new FileOutputStream(outFile); 
                  
                 //Call the FileOutputStream object?s write method and pass the pdf data 
                 myFileW.write(pdfStream); 
                  
                 //Close the FileOutputStream object 
                 myFileW.close(); 
                  
             } 
         } 
     } 
     catch(Exception e) 
     { 
         e.printStackTrace(); 
     } 
     } 
  
 } 
 
```

## Avvio rapido: Richiamo di un servizio utilizzando dati BLOB su HTTP in un progetto Java {#quick-start-invoking-a-service-using-blob-data-over-http-in-a-java-project}

Il seguente esempio di codice Java richiama un processo denominato `MyApplication/EncryptDocument` utilizzo di dati su HTTP. (Vedi [Richiamo di dati AEM Forms tramite BLOB su HTTP](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http).)

Un documento PDF non protetto basato su un file PDF denominato *Loan.pdf* viene passato al processo AEM Forms utilizzando SOAP su HTTP. Il file PDF si trova al seguente URL: `https://[server]:[port]/FormsQS`. Il processo restituisce un documento PDF crittografato con password salvato come file PDF denominato *EncryptedDocument.pdf*.

```as3
 /** 
     * Ensure that you create Java proxy files that consume 
     * the AEM Forms service WSDL. You can use JAX-WS to create 
     * the Java proxy files.   
     * 
     * This Java quick start uses BLOB over HTTP to invoke a short-lived process named 
     * EncryptDocument. For information, see  
     * "Invoking AEM Forms using BLOB over HTTP" in Programming with AEM forms.   
     */ 
 import java.io.*; 
 import java.net.URL; 
  
 import javax.xml.ws.BindingProvider; 
 import com.adobe.idp.services.*; 
  
 public class InvokeEncryptDocumentHTTP { 
     public static void main(String[] args){ 
          
         try{ 
             //Create a MyApplicationEncryptDocument object 
             MyApplicationEncryptDocumentService encClient = new MyApplicationEncryptDocumentService(); 
             MyApplicationEncryptDocument encryptDocClient = encClient.getEncryptDocument(); 
              
             //Set connection values required to invoke AEM Forms using BLOB over HTTP 
             String url = "https://[server]:[port]/soap/services/MyApplication/EncryptDocument?blob=http"; 
             String username = "administrator"; 
             String password = "password"; 
             ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url); 
             ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username); 
             ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password); 
              
             //Create a BLOB object and populate it by invoking the setRemoteURL method 
             BLOB inDoc = new BLOB(); 
             inDoc.setRemoteURL("https://[server]:[port]/FormsQS/Loan.pdf"); 
              
                //invoke the short-lived process named MyApplication/EncryptDocument 
             BLOB outDoc = encryptDocClient.invoke(inDoc); 
              
             //Retrieve an InputStream from the returned BLOB instance 
             URL myURL = new URL(outDoc.getRemoteURL()); 
             InputStream inputStream = myURL.openStream(); 
              
             //Create a new file containing the returned PDF document 
             File f = new File("C:\\Adobe\EncryptedDocument.pdf"); 
             OutputStream out = new FileOutputStream(f); 
              
             //Iterate through the buffer 
             byte buf[] = new byte[1024]; 
             int len; 
             while ((len = inputStream.read(buf)) > 0) 
                 out.write(buf, 0, len); 
             out.close(); 
             inputStream.close(); 
              
              System.out.println("The short-lived process named EncryptDocument was successfully invoked.");             
         } 
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
      
     } 
  
 } 
  
 
```

## Avvio rapido: Richiamo di un servizio utilizzando dati BLOB su HTTP in un progetto .NET {#quick-start-invoking-a-service-using-blob-data-over-http-in-a-net-project}

Il seguente esempio di codice C# richiama un processo denominato `MyApplication/EncryptDocument` da un progetto Microsoft .NET che utilizza dati tramite HTTP. (Vedi [Richiamo di dati AEM Forms tramite BLOB su HTTP](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http).)

Un documento PDF non protetto basato su un file PDF denominato *Loan.pdf* viene passato al processo AEM Forms utilizzando BLOB su HTTP. Il processo restituisce un documento PDF crittografato con password salvato come file PDF denominato *EncryptedPDF.pdf*.

```as3
 /* 
     * Ensure that you create a .NET client assembly that uses  
     * SOAP over HTTP. This is required to populate a BLOB  
     * object’s remote URL data memeber. 
     * 
     * For information, see "Invoking AEM Forms using BLOB data over HTTP" in  
     * Programming with AEM forms 
     */ 
 using System; 
 using System.Collections; 
 using System.ComponentModel; 
 using System.Data; 
 using System.IO; 
 using System.Security.Policy; 
  
 namespace InvokeEncryptDocumentHTTP 
 { 
  
        class InvokeEncryptDocumentUsingHTTP 
        { 
  
            const int BUFFER_SIZE = 4096; 
            [STAThread] 
            static void Main(string[] args) 
            { 
  
                try 
                { 
                    String urlData = "https://[server]:[port]/FormsQS/Loan.pdf"; 
  
                    //Create a MyApplication_EncryptDocumentService object and set authentication values 
                    MyApplication_EncryptDocumentService encryptClient = new MyApplication_EncryptDocumentService(); 
                    encryptClient.Credentials = new System.Net.NetworkCredential("administrator", "password"); 
  
                    //Create a BLOB object 
                    BLOB inDoc = new BLOB(); 
  
                    //Populate the BLOB object’s remoteURL data member 
                    inDoc.remoteURL = urlData; 
  
                    //Invoke the EncryptDocument process 
                    BLOB outDoc = encryptClient.invoke(inDoc); 
  
                    //Create a UriBuilder object using the  
                    //BLOB object’s remoteURL data member field 
                    UriBuilder uri = new UriBuilder(outDoc.remoteURL); 
  
                   //Convert the UriBuilder to a Stream object 
                    System.Net.WebRequest wr = System.Net.WebRequest.Create(uri.Uri); 
                    System.Net.WebResponse response = wr.GetResponse(); 
                    System.IO.StreamReader sr = new System.IO.StreamReader(response.GetResponseStream()); 
                    Stream mySteam = sr.BaseStream; 
  
                    //Create a byte array 
                    byte[] myData = new byte[BUFFER_SIZE]; 
  
                   //Populate the byte array 
                   PopulateArray(mySteam, myData); 
  
                   //Create a new file named UsageRightsLoan.pdf 
                   FileStream fs2 = new FileStream("C:\\Adobe\EncryptedPDF.pdf", FileMode.OpenOrCreate); 
  
                   //Create a BinaryWriter object 
                   BinaryWriter w = new BinaryWriter(fs2); 
                   w.Write(myData); 
                   w.Close(); 
                   fs2.Close(); 
                } 
                catch (Exception ee) 
                { 
                    Console.WriteLine(ee.Message); 
                } 
            } 
  
            public static void PopulateArray(Stream stream, byte[] data) 
            { 
                int offset = 0; 
                int remaining = data.Length; 
                while (remaining > 0) 
                { 
                    int read = stream.Read(data, offset, remaining); 
                    if (read <= 0) 
                        throw new EndOfStreamException(); 
                    remaining -= read; 
                    offset += read; 
                } 
            } 
      
        } 
 } 
 
```

## Avvio rapido: Richiamo di un servizio utilizzando MTOM in un progetto .NET {#quick-start-invoking-a-service-using-mtom-in-a-net-project}

Il seguente esempio di codice C# richiama un processo denominato `MyApplication/EncryptDocument` da un progetto Microsoft .NET che utilizza MTOM. (Vedi [Richiamo di AEM Forms tramite MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom).)

Un documento PDF non protetto basato su un file PDF denominato *loan.pdf* viene passato al processo AEM Forms utilizzando MTOM. Il processo restituisce un documento PDF crittografato con password salvato come file PDF denominato *EncryptedDocument.pdf*.

```as3
 ???/** 
     * Ensure that you create a .NET project that uses  
     * MS Visual Studio 2008 and version 3.5 of the .NET 
     * framework. This is required to invoke a  
     * AEM Forms service using MTOM. 
     * 
     * For information, see "Invoking AEM Forms using MTOM" in Programming with AEM forms  
     */ 
 using System; 
 using System.Collections.Generic; 
 using System.Linq; 
 using System.Text; 
 using System.ServiceModel; 
 using EncryptDocumentMTOM.ServiceReference1; 
 using System.IO; 
  
 //Invoke the EncryptDocument process using MTOM 
 namespace EncryptDocumentUsingMTOM 
 { 
        class Program 
        { 
            static void Main(string[] args) 
            { 
                try 
                { 
                    //Specify the name of the PDF file to encrypt 
                    String pdfFile = "C:\\Adobe\loan.pdf"; 
  
                    //Create an EncryptDocumentClient object 
                    MyApplication_EncryptDocumentClient encryptProcess = new MyApplication_EncryptDocumentClient(); 
                    encryptProcess.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://[server]:[port]/soap/services/MyApplication/EncryptDocument?blob=mtom"); 
                    BasicHttpBinding b = (BasicHttpBinding)encryptProcess.Endpoint.Binding; 
                    b.MessageEncoding = WSMessageEncoding.Mtom; 
  
                    //Enable BASIC HTTP authentication 
                    encryptProcess.ClientCredentials.UserName.UserName = "administrator"; 
                    encryptProcess.ClientCredentials.UserName.Password = "password"; 
                    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                    b.MaxReceivedMessageSize = 4000000; 
                    b.MaxBufferSize = 4000000; 
                    b.ReaderQuotas.MaxArrayLength = 4000000; 
      
                    //Reference the PDF file to send to the EncryptDocument process 
                    FileStream fs = new FileStream(pdfFile, FileMode.Open); 
  
                    //Create a BLOB object 
                    BLOB inDoc = new BLOB(); 
  
                    //Get the length of the file stream  
                    int len = (int)fs.Length; 
                    byte[] ByteArray = new byte[len]; 
  
                    //Populate the byte array with the contents of the FileStream object 
                    fs.Read(ByteArray, 0, len); 
                    inDoc.MTOM = ByteArray; 
      
                    //Invoke the EncryptDocument short-lived process 
                    BLOB outDoc = encryptProcess.invoke(inDoc); 
                    byte[] encryptDoc = outDoc.MTOM; 
  
                    //Create a new file containing the encrypted PDF document 
                    string FILE_NAME = "C:\\Adobe\EncryptedDocument.pdf"; 
                    FileStream fs2 = new FileStream(FILE_NAME, FileMode.OpenOrCreate); 
                    BinaryWriter w = new BinaryWriter(fs2); 
                    w.Write(encryptDoc); 
                    w.Close(); 
                    fs2.Close(); 
                } 
                catch (Exception ee) 
                { 
                    Console.WriteLine(ee.Message); 
                } 
            } 
        } 
 } 
 
```

>[!NOTE]
>
>Molti avvii rapidi che mostrano come eseguire le operazioni del servizio AEM Forms includono un esempio di codice MTOM.

## Avvio rapido: Richiamo di un servizio utilizzando SwaRef in un progetto Java {#quick-start-invoking-a-service-using-swaref-in-a-java-project}

Il seguente esempio di codice Java richiama un processo denominato `MyApplication/EncryptDocument` da un progetto Java. Questo progetto Java utilizza classi proxy create utilizzando JAX-WS e SwaRef come tipo di codifica. (Vedi [Richiamo di AEM Forms tramite SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref).)

Un documento PDF non protetto basato su un file PDF denominato *Loan.pdf* viene passato al processo AEM Forms utilizzando SwaRef. Il documento PDF crittografato viene salvato come file PDF denominato *EncryptedDocument.pdf*.

```as3
 /** 
     * Ensure that you create Java proxy files that consume 
     * the AEM Forms service WSDL. You can use JAX-WS to create 
     * the Java proxy files.   
     * 
     * This Java quick start uses SwaRef to invoke a short-lived process named 
     * EncryptDocument. For information, see  
     * "Invoking AEM Forms using SwaRef" in Programming with AEM forms.   
     */ 
  
 import javax.xml.ws.BindingProvider; 
 import javax.activation.DataHandler; 
 import javax.activation.DataSource; 
 import javax.activation.FileDataSource;  
 import java.io.*; 
  
 import com.adobe.idp.services.*; 
  
 public class InvokeEncryptDocumentSwaRef { 
  
 public static void main(String[] args) { 
          
         try{ 
              
         //Specify connection values required to invoke the MyApplication/EncryptDocument process  
         //using SwaRef     
         String url = "https://[server]:[port]/soap/services/MyApplication/EncryptDocument?blob=swaref"; 
         String username = "administrator"; 
         String password = "password"; 
         String pdfFile = "C:\\Adobe\Loan.pdf"; 
          
         //Create a MyApplicationEncryptDocument object 
         MyApplicationEncryptDocumentService encClient = new MyApplicationEncryptDocumentService(); 
         MyApplicationEncryptDocument encryptDocClient = encClient.getEncryptDocument(); 
          
         ((BindingProvider)encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url); 
         ((BindingProvider)encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username); 
         ((BindingProvider)encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password); 
           
          //Create a file object 
          File pdf = new File(pdfFile);  
           
          //Create a DataSource object 
          DataSource myDS = new FileDataSource(pdf); 
           
          //Create a DataHandler object 
          DataHandler dataHandler = new DataHandler(myDS);  
                                         
         //Create a BLOB object and populate it with the DataHandler 
         BLOB inDoc = new BLOB(); 
         inDoc.setSwaRef(dataHandler); 
          
         //Invoke the EncryptDocument process 
         BLOB outDoc = encryptDocClient.invoke(inDoc);   
          
         //Save the encrypted file as a PDF file 
         DataHandler handler = outDoc.getSwaRef(); 
          
         //Create a new file containing the returned PDF document 
         File f = new File("C:\\Adobe\EncryptedDocument.pdf"); 
         InputStream inputStream = handler.getInputStream(); 
         OutputStream out = new FileOutputStream(f); 
          
         //Iterate through the buffer 
         byte buf[] = new byte[1024]; 
         int len; 
         while ((len = inputStream.read(buf)) > 0) 
             out.write(buf, 0, len); 
         out.close(); 
         inputStream.close(); 
  
          System.out.println("The short-lived process named MyApplication/EncryptDocument was successfully invoked.");             
              
         }catch (Exception e) { 
              e.printStackTrace(); 
             }     
         } 
 } 
  
 
```

>[!NOTE]
>
>Molti avvii rapidi che mostrano come eseguire le operazioni di servizio includono un esempio di codice SwaRef.
