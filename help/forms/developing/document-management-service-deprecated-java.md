---
title: Guida rapida a Document Management Service (obsoleto)Java API (SOAP)
seo-title: Guida rapida a Document Management Service (obsoleto)Java API (SOAP)
description: Utilizza l’API Java del servizio di gestione documenti per creare spazi per i servizi di contenuto, eliminare gli spazi per i servizi di contenuto, aggiungere contenuti ai servizi di contenuto, recuperare contenuti dai servizi di contenuto, spostare il contenuto dei servizi di contenuto, elencare il contenuto dei servizi di contenuto, cercare il contenuto dei servizi di contenuto e impostare le autorizzazioni per i servizi di contenuto.
seo-description: Utilizza l’API Java del servizio di gestione documenti per creare spazi per i servizi di contenuto, eliminare gli spazi per i servizi di contenuto, aggiungere contenuti ai servizi di contenuto, recuperare contenuti dai servizi di contenuto, spostare il contenuto dei servizi di contenuto, elencare il contenuto dei servizi di contenuto, cercare il contenuto dei servizi di contenuto e impostare le autorizzazioni per i servizi di contenuto.
uuid: 967c282a-ccde-4489-a4d5-53c6a1a0cac0
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 9cffdb77-c8a4-4a15-b64f-1d3aadaa60c7
role: Developer
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---


# Guida rapida all’API Java (obsoleta) di Document Management Service {#document-management-service-deprecated-java-api-quick-start-soap}

Per il servizio Gestione documenti (obsoleto) sono disponibili i seguenti Quick Starts.

>[!NOTE]
>
>A partire dal 5 agosto 2011, Adobe sta eseguendo la migrazione dei clienti di Content Services ES ad Adobe Digital Enterprise Platform Experience Services. La roadmap del prodotto per i clienti che utilizzano Content Services è quella di passare al nuovo ADEP Experience Services - Core, che include un archivio dei contenuti nativo basato sulla moderna architettura CRX modulare, acquisita durante l&#39;acquisizione Adobe di Day Software.

[Avvio rapido (modalità SOAP): Creare spazi di Content Services utilizzando l’API Java](document-management-service-deprecated-java.md#quick-start-soap-mode-create-content-services-spaces-using-the-java-api-deprecated)

[Avvio rapido (modalità SOAP): Eliminare il contenuto dei Content Services utilizzando l’API Java](document-management-service-deprecated-java.md#quick-start-soap-mode-delete-content-services-content-using-the-java-api-deprecated)

[Avvio rapido (modalità SOAP): Aggiungere contenuti a Content Services tramite l’API Java](document-management-service-deprecated-java.md#quick-start-soap-mode-add-content-to-content-services-using-the-java-api-deprecated)

[Avvio rapido (modalità SOAP): Recuperare il contenuto da Content Services utilizzando l’API Java](document-management-service-deprecated-java.md#quick-start-soap-mode-retrieve-content-from-content-services-using-the-java-api-deprecated)

[Avvio rapido (modalità SOAP): Spostare il contenuto dei Content Services utilizzando l’API Java](document-management-service-deprecated-java.md#quick-start-soap-mode-move-content-services-content-using-the-java-api-deprecated)

[Avvio rapido (modalità SOAP): Elencare contenuti di Content Services utilizzando l’API Java](document-management-service-deprecated-java.md#quick-start-soap-mode-list-content-services-content-using-the-java-api-deprecated)

[Avvio rapido (modalità SOAP): Ricercare contenuti di Content Services utilizzando l’API Java](document-management-service-deprecated-java.md#quick-start-soap-mode-search-content-services-content-using-the-java-api-deprecated)

[Avvio rapido (modalità SOAP): Impostazione delle autorizzazioni di Content Services tramite l’API Java](document-management-service-deprecated-java.md#quick-start-soap-mode-setting-content-services-permissions-using-the-java-api-deprecated)

Le operazioni AEM Forms possono essere eseguite utilizzando l’API fortemente tipizzata di AEM Forms e la modalità di connessione deve essere impostata su SOAP.

>[!NOTE]
>
>Gli avvii rapidi disponibili in Programmazione con moduli AEM sono basati su Forms Server distribuito su JBoss e sul sistema operativo Windows. Tuttavia, se si utilizza un altro sistema operativo, ad esempio UNIX, sostituire percorsi specifici di Windows con percorsi supportati dal sistema operativo applicabile. Allo stesso modo, se utilizzi un altro server applicativo J2EE, assicurati di specificare proprietà di connessione valide. Vedere [Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Avvio rapido (modalità SOAP): Creare spazi nei servizi di contenuto utilizzando l’API Java (obsoleta) {#quick-start-soap-mode-create-content-services-spaces-using-the-java-api-deprecated}

Nell&#39;esempio di codice Java seguente viene creato un nuovo spazio denominato *Directory di test *situato nella home dell&#39;azienda. Il valore di identificazione del nuovo spazio viene scritto nella console.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class CreateNewSpaceSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and node 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory" ; 
                                  
             //Create a new space 
             String spaceId = docManager.createSpace(storeName,nodeName); 
             System.out.println("The identifier value of the new space is " +spaceId); 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Eliminare il contenuto dei Content Services utilizzando l’API Java (obsoleta) {#quick-start-soap-mode-delete-content-services-content-using-the-java-api-deprecated}

Nell&#39;esempio di codice Java seguente viene eliminato uno spazio denominato /Company Home/Test Directory.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class DeleteContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and node 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory" ; 
              
             //Delete the content from /Company Home/Test Directory 
             Boolean ans = docManager.deleteContent(storeName, nodeName); 
              
             if (ans == true) 
                 System.out.println("The content was successfully deleted"); 
             else 
                 System.out.println("The content was not deleted"); 
             } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Aggiungere contenuti a Content Services utilizzando l’API Java (obsoleta) {#quick-start-soap-mode-add-content-to-content-services-using-the-java-api-deprecated}

Nell&#39;esempio di codice Java seguente viene aggiunto un file PDF denominato *MutuiForm.pdf* a una cartella denominata /Company Home/Test Directory. Gli attributi di creazione e descrizione sono impostati. Il valore di identificazione del nuovo contenuto viene scritto nella console.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.util.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.CRCResult; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
 import com.adobe.livecycle.contentservices.client.impl.UpdateVersionType; 
  
 public class AddContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory); 
              
             //Specify the store and node name 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory" ; 
              
             //Retrieve the document to store in /Company Home/Test Directory 
             Document content =  new Document(new File("C:\\Adobe\MortgageForm.pdf"), false); 
              
             //Create a MAP instance to store attributes 
             Map<String,Object> inputs = new HashMap<String,Object>(); 
              
             //Specify attributes that belong to the new content 
             String creator = "{https://www.alfresco.org/model/content/1.0}creator"; 
             String description = "{https://www.alfresco.org/model/content/1.0}description";  
              
             inputs.put(creator,"Tony Blue"); 
             inputs.put(description,"A mortgage application form"); 
                                  
             //Store MortgageForm.pdf in /Company Home/Test Directory 
             CRCResult result = docManager.storeContent(storeName,  
                      nodeName, 
                     "MortgageForm.pdf", 
                     "{https://www.alfresco.org/model/content/1.0}content",  
                     content, 
                     "UTF-8", 
                     UpdateVersionType.INCREMENT_MAJOR_VERSION, 
                     null, 
                     inputs);  
              
             //Get the identifier value of the new content 
             String id = result.getNodeUuid(); 
             System.out.println("The identifier value of the new content is "+id); 
     } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Recupera il contenuto da Content Services utilizzando l’API Java (obsoleta) {#quick-start-soap-mode-retrieve-content-from-content-services-using-the-java-api-deprecated}

Nell&#39;esempio di codice Java seguente viene recuperato un file PDF denominato *MortgageForm.pdf* da /Company Home. Il file PDF viene salvato nel file system locale e denominato *UpdatedMortagelForm.pdf*.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.util.*; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.CRCResult; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class RetrieveContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and the content to retrieve 
                String storeName = "SpacesStore"; 
                String nodeName  = "/Company Home/MortgageForm.pdf"; 
  
                //Retrieve /Company Home/MortgageForm.pdf 
                CRCResult content = docManager.retrieveContent( 
                      storeName, 
                      nodeName, 
                      ""); 
      
                //Write the PDF file to the local file system 
                File myFile = new File("C:\\Adobe\UpdatedMortgageForm.pdf"); 
                Document doc =content.getDocument();  
                doc.copyToFile(myFile); 
          } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## Avvio rapido (modalità SOAP): Spostare il contenuto dei Content Services utilizzando l’API Java (obsoleta) {#quick-start-soap-mode-move-content-services-content-using-the-java-api-deprecated}

Nell&#39;esempio di codice Java seguente viene spostato un file PDF denominato *MutuiForm.pdf* da /Company Home/Test Directory a /Company Home. Il valore di identificazione del contenuto spostato viene scritto nella console.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class MoveContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and the content to move 
                String storeName = "SpacesStore"; 
                String nodeName = "/Company Home/Test Directory/MortgageForm.pdf"; 
                String newSpace = "/Company Home"; 
  
                //Move the content from /Company Home/Test Directory 
                //to /Company Home and display the identifier value of the  
                //moved content 
                String contentID = docManager.moveContent(storeName, nodeName, newSpace); 
                System.out.println("The identifier value of the moved content is "+contentID); 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## Avvio rapido (modalità SOAP): Elencare contenuti di Content Services utilizzando l’API Java (obsoleto) {#quick-start-soap-mode-list-content-services-content-using-the-java-api-deprecated}

Il seguente esempio di codice Java elenca il contenuto che si trova nella home /Company. Vengono visualizzati ogni tipo di nodo e il nome del nodo.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.CRCResult; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class ListingContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and the space 
                String storeName = "SpacesStore"; 
                String nodeName  = "/Company Home"; 
  
               //List the contents of /Company Home 
               List<CRCResult> allImages = docManager.getSpaceContents( 
                      storeName, 
                      nodeName, 
                      false); 
               
              //Create an Iterator object and iterate through  
              //the List object 
              Iterator iter = allImages.iterator();  
              int i = 0 ;  
              while (iter.hasNext()) {  
                                
                  //Get the node content type and name  
                  CRCResult sinContent = (CRCResult)iter.next();  
                  String nodeType =  sinContent.getNodeType(); 
                  String name = sinContent.getNodeName(); 
                  System.out.println("The node type is "+nodeType  +". The node name is "+name);   
              } 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## Avvio rapido (modalità SOAP): Ricercare contenuti di Content Services utilizzando l’API Java (obsoleta) {#quick-start-soap-mode-search-content-services-content-using-the-java-api-deprecated}

Il seguente codice Java cerca /Company Home per un documento che contiene il testo MortagingForm. Vengono inoltre cercate le sottocartelle.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.ResultSet; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
 import com.adobe.livecycle.contentservices.client.impl.QueryImpl; 
 import com.adobe.livecycle.contentservices.client.impl.StatementImpl; 
  
 public class SearchSpaceSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and node 
             String path ="/Company Home";  
              String storeName = "SpacesStore"; 
              
             //Create a Query expression 
             QueryImpl qImpl = new QueryImpl(); 
             String myName = "{https://www.alfresco.org/model/content/1.0}name"; 
             StatementImpl statement = new StatementImpl(myName, StatementImpl.OPERATOR_CONTAINS, "MortgageForm" ); 
             qImpl.addStatement(statement);  
          
             //Perform the search for a document that contains the text MortgageForm 
             ResultSet rs = docManager.searchRepository(storeName, path, true, qImpl, 200); 
             long resultSize = rs.getResultSize();  
              
             //Determine if the document is located in Content space 
             if (resultSize > 0) 
             { 
                 System.out.println("MortgageForm is located in the Repository"); 
             } 
         } 
     catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## Avvio rapido (modalità SOAP): Impostazione delle autorizzazioni dei servizi di contenuto tramite l’API Java (obsoleta) {#quick-start-soap-mode-setting-content-services-permissions-using-the-java-api-deprecated}

Nell&#39;esempio di codice Java seguente viene impostata un&#39;autorizzazione per un utente di nome tony blue. Il dominio specificato è quello predefinito. L&#39;autorizzazione Consumer viene specificata e il nodo è `/Company Home/Test Directory`.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
 import com.adobe.livecycle.contentservices.client.impl.ContentAccessPermission; 
  
 public class SetPermissionsSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode     
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory); 
              
             //Specify the store and node name 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory/"; 
              
              //Create a new permission 
             ContentAccessPermission permission = new ContentAccessPermission(); 
             permission.setAuthority("tblue/DefaultDom");  
             permission.setIsAllowed(false); 
             permission.setPermission("Consumer"); 
              
             //Create a collection to hold the values 
             List<ContentAccessPermission> permissionList = new ArrayList<ContentAccessPermission>(); 
             permissionList.add(0,permission); 
                          
             //Set the permission 
             docManager.writePermissions(storeName,  
                      nodeName, 
                      permissionList, 
                     false);  
     } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Creazione di associazioni tramite l’API Java (obsoleto) {#quick-start-soap-mode-creating-associations-using-the-java-api-deprecated}

Il seguente codice Java crea un’associazione a un file di dati XML e a un modulo PDF. Questo tipo di associazione è denominato LinkedBy.Al documento PDF deve essere applicato l&#39;aspetto collegabile.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
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
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class CreateAssociationsSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory); 
              
             //Specify the input values  
             String storeName ="SpacesStore"; 
             String associationType = "{https://www.adobe.com/lc/datacapture/1.0}linkedBy"; 
             String aspect = "{https://www.adobe.com/lc/datacapture/1.0}linkable"; 
             String parentPath= "/Company Home/MortgageForm.pdf"; 
             String childPath= "/Company Home/Loan.xml"; 
                      
             //Set the linkable aspect to MortgageForm.pdf 
             List<String> aspectList = new ArrayList(); 
             aspectList.add(aspect); 
              
             //Create an attribute map 
             Map<String,Object> inputs = new HashMap<String,Object>(); 
              
             //Specify attributes that belong to the new content 
             String creator = "{https://www.alfresco.org/model/content/1.0}creator"; 
             String description = "{https://www.alfresco.org/model/content/1.0}description";  
              
             inputs.put(creator,"Tony Blue"); 
             inputs.put(description,"Link the PDF document to loan data"); 
              
             //Set the aspects 
             docManager.setContentAttributes(storeName,parentPath,aspectList,inputs); 
  
             //Create an association between MortgageForm.pdf and Loan.xml  
             docManager.createAssociation(storeName,  
                     associationType, 
                     parentPath, 
                     childPath);  
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 
```

