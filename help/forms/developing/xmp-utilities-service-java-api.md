---
title: Servizio Utilità XMP Java APIQuick Start(SOAP)
seo-title: XMP Utilities Service Java APIQuick Start(SOAP)
description: Utilizza il servizio Utilità XMP per esportare e importare i metadati XMP.
seo-description: Use the XMP Utilities service to export and import XMP metadata.
uuid: 5db4c623-75db-4a34-9ad2-3c917619e296
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 1b229ddf-9350-40b6-8056-dcbe0c5afd5b
role: Developer
exl-id: fdbf9942-7e4d-4b76-971f-d26d89c4c4cf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Guida rapida API Java di XMP Utilities Service (SOAP) {#xmp-utilities-service-java-apiquick-start-soap}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per il servizio Utilità XMP sono disponibili i seguenti Avvio rapido.

[Avvio rapido (modalità SOAP): Esportazione dei metadati XMP tramite l’API Java](xmp-utilities-service-java-api.md#quick-start-soap-mode-exporting-xmp-metadata-using-the-java-api)

[Avvio rapido (modalità SOAP): Importazione di metadati XMP tramite l’API Java](xmp-utilities-service-java-api.md#quick-start-soap-mode-importing-xmp-metadata-using-the-java-api)

Le operazioni AEM Forms possono essere eseguite utilizzando l’API fortemente tipizzata di AEM Forms e la modalità di connessione deve essere impostata su SOAP.

>[!NOTE]
>
>Gli avvii rapidi disponibili in Programmazione con moduli AEM sono basati sul server Forms se si utilizza un altro sistema operativo, ad esempio UNIX, sostituisci percorsi specifici di Windows con percorsi supportati dal sistema operativo applicabile. Allo stesso modo, se utilizzi un altro server applicativo J2EE, assicurati di specificare proprietà di connessione valide. Vedi [Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Avvio rapido (modalità SOAP): Esportazione dei metadati XMP tramite l’API Java {#quick-start-soap-mode-exporting-xmp-metadata-using-the-java-api}

Nell&#39;esempio di codice seguente vengono recuperati, ispezionati e salvati i metadati XMP. (Vedi [Esportazione di metadati da documenti PDF](/help/forms/developing/xmp-utilities.md#exporting-metadata-from-pdf-documents).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-pdfutility-client.jar 
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
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
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
 import com.adobe.livecycle.xmputility.*; 
 import com.adobe.livecycle.xmputility.client.*; 
 import java.util.*; 
 import java.io.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class ExportMetadata 
 { 
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
  
             //Create a ServiceClientFactory instance 
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); 
  
             // Create a XMP Utility client 
             XMPUtilityServiceClient xmpUt = new XMPUtilityServiceClient(factory); 
  
             // Specify a PDF document whose metadata is to be exported 
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf"); 
             Document inDoc = new Document(fileInputStream); 
  
             // Export the XMP metadata object 
             XMPUtilityMetadata myXmp = xmpUt.exportMetadata(inDoc); 
  
             // Inspect the XMP metadata object (retrieve the document?s author in this case) 
             String name = myXmp.getAuthor(); 
             System.out.println("The document?s author is " + name); 
  
             // Export the XMP metadata to an XML file 
             Document outDoc = xmpUt.exportXMP(inDoc); 
             File xmpFile = new File("c:\\LoanMetaData.xml"); 
             outDoc.copyToFile(xmpFile); 
         } 
         catch (Exception e) 
         { 
             System.out.println("Error occurred: " + e.getMessage()); 
         } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Importazione di metadati XMP tramite l’API Java {#quick-start-soap-mode-importing-xmp-metadata-using-the-java-api}

Nell&#39;esempio di codice seguente vengono importati XMP metadati e viene salvato il nuovo file PDF su disco. Il documento PDF si basa su un file PDF denominato Loan.pdf. Il documento XML contenente i metadati da importare nel documento PDF si basa su un file XML denominato *LoanMetaData.xml*. Per informazioni su questo file XML, vedere [Importazione di metadati in documenti PDF](/help/forms/developing/xmp-utilities.md#importing-metadata-into-pdf-documents).

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-pdfutility-client.jar 
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
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
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
 import com.adobe.livecycle.xmputility.*; 
 import com.adobe.livecycle.xmputility.client.*; 
 import java.util.*; 
 import java.io.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class ImportMetadata 
 { 
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
  
             //Create a ServiceClientFactory instance 
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a XMP Utility client 
             XMPUtilityServiceClient xmpUt = new XMPUtilityServiceClient(factory); 
  
             //Specify a PDF document into which XMP metadata is imported 
             FileInputStream filePDF = new FileInputStream("C:\\Adobe\Loan.pdf"); 
             Document inDoc = new Document(filePDF); 
  
             //Specify an XML file containing XMP metadata to import 
             FileInputStream fileXML = new FileInputStream("C:\\Adobe\LoanMetaData.xml"); 
             Document xmpDoc = new Document(fileXML ); 
  
             //Import the XMP metadata 
             Document outDoc = xmpUt.importXMP(inDoc, xmpDoc); 
  
             //Inspect the XMP metadata object (retrieve the document?s author in this case) 
             XMPUtilityMetadata myXmp = xmpUt.exportMetadata(outDoc); 
             String name = myXmp.getAuthor(); 
             System.out.println("The document?s author is " + name); 
  
             //Save the PDF document containing the new metadata 
             File pdfFile = new File("c:\\Adobe\LoanWithMetadata.pdf"); 
             outDoc.copyToFile(pdfFile); 
         } 
         catch (Exception e) 
         { 
             System.out.println("Error occurred: " + e.getMessage()); 
         } 
     } 
 }
```
