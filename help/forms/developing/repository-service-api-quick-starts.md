---
title: Avvio rapido API del servizio archivio
seo-title: Repository Service API Quick Starts
description: Utilizza il servizio AEM Forms Repository per creare una cartella, scrivere una risorsa, elencare risorse, leggere una risorsa, aggiornare una risorsa, cercare risorse, creare relazioni tra risorse, bloccare una risorsa, gestire elenchi di controllo accessi ed eliminare una risorsa.
seo-description: Use the AEM Forms Repository service to create a folder, write  a resource, list resources, reading a resource, update a resource, search for resources, create relationships between resources, locking a resource, managing access control lists, and delete a resource.
uuid: 9c307e6e-d9a4-4021-8493-9f28a745dedb
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 2fd1a21a-0f90-49d8-9f62-383b268d540d
role: Developer
exl-id: 859a2b57-df90-4030-9061-c454d07cb753
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 1%

---

# Avvio rapido API del servizio archivio {#repository-service-api-quick-starts}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I seguenti Quick Starts sono disponibili per il servizio AEM Forms Repository.

[Avvio rapido (modalità SOAP): Creazione di una cartella tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api)

[Avvio rapido (modalità SOAP): Scrittura di una risorsa tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[Avvio rapido (modalità SOAP): Inserimento di risorse nell’elenco tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-listing-resources-using-the-java-api)

[Avvio rapido (modalità SOAP): Lettura di una risorsa tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-reading-a-resource-using-the-java-api)

[Avvio rapido (modalità SOAP): Aggiornamento di una risorsa tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-updating-a-resource-using-the-java-api)

[Avvio rapido (modalità SOAP): Ricerca di risorse tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Avvio rapido (modalità SOAP): Creazione di relazioni tra le risorse tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api)

[Avvio rapido (modalità SOAP): Blocco di una risorsa tramite API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-locking-a-resource-using-the-java-api)

[Avvio rapido (modalità SOAP): Gestione degli elenchi di controllo accessi tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-managing-access-control-lists-using-the-java-api)

[Avvio rapido (modalità SOAP): Eliminazione di una risorsa tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-deleting-a-resource-using-the-java-api)

Le operazioni AEM Forms possono essere eseguite utilizzando l’API fortemente tipizzata di AEM Forms e la modalità di connessione deve essere impostata su SOAP

**Applicazioni/FormsApplication**

La maggior parte dei servizi di archivio AEM Forms avvia rapidamente l&#39;interazione con un&#39;applicazione denominata `Applications/FormsApplication,` come illustrato nella figura seguente.

La cartella FormsFolder è una posizione nell’archivio AEM Forms. Ad esempio, puoi aggiungere questa cartella a livello di programmazione `Applications/FormsApplication`. (Vedi [Avvio rapido (modalità SOAP): Creazione di una cartella tramite l’API Java](repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api).)

Il percorso di una risorsa situata nell’archivio AEM Forms è:

`Applications/Application-name/Application-version/Folder.../Filename`

>[!NOTE]
>
>È possibile sfogliare l’archivio AEM Forms utilizzando un browser web. Per sfogliare l’archivio, immetti il seguente URL in un browser Web https://[nome server]:[porta server]/repository. Puoi verificare i risultati dell’avvio rapido utilizzando un browser web. Ad esempio, se aggiungi contenuto all’archivio AEM Forms, puoi visualizzarne il contenuto in un browser web.

>[!NOTE]
>
>Applicazioni/FormsApplication non esiste per impostazione predefinita. Per seguire gli avvii rapidi, crea questa applicazione utilizzando Workbench. Per informazioni sulla creazione di un&#39;applicazione tramite Workbench, consulta [Guida introduttiva alla progettazione dei processi](http://www.adobe.com/go/learn_aemforms_workbench_64).

## Avvio rapido (modalità SOAP): Creazione di una cartella tramite l’API Java {#quick-start-soap-mode-creating-a-folder-using-the-java-api}

Nell&#39;esempio di codice Java seguente viene creata una cartella denominata *FormsFolder* nella posizione seguente `/Applications/FormsApplication/1.0/`. (Vedi [Creazione di cartelle](/help/forms/developing/aem-forms-repository.md#creating-folders).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.*; 
 import com.adobe.repository.infomodel.bean.*; 
  
 public class CreateFolder { 
  
     public static void main(String[] args) { 
  
         // This quick start creates a folder in the AEM Forms repository 
         //Ensure that you create a AEM Forms application named FormsApplication using Workbench 
         try  
         { 
             //Set connection properties required to invoke AEM Forms                                  
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
  
             // Create a RepositoryInfomodelFactoryBean needed for creating resources 
             RepositoryInfomodelFactoryBean repositoryInfomodelFactory = new RepositoryInfomodelFactoryBean(null); 
              
             // Create a folder in a AEM Forms application named Application/FormsApplication 
             ResourceCollection folder = repositoryInfomodelFactory.newResourceCollection( 
                 new Id(),  
                 new Lid(),  
                 "FormsFolder" 
             ); 
  
             // Set the folder’s description 
             folder.setDescription("A folder to store forms"); 
  
             // Write the folder to the repository 
             Resource newFolder = repositoryClient.writeResource("/Applications/FormsApplication/1.0/", folder); 
  
             // Retrieve the folder’s identifier value 
             String msg = "The identifier value of the new folder is" + newFolder.getId(); 
  
             // Print folder verification message 
             System.out.println(msg); 
  
         } catch (Exception e) { 
                 System.out.println( 
                     "Exception thrown while trying to create the folder" + 
                     e.getMessage() 
                 ); 
           } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Scrittura di una risorsa tramite l’API Java {#quick-start-soap-mode-writing-a-resource-using-the-java-api}

Il seguente esempio di codice Java scrive una risorsa denominata *loan.xdp* nel repository. La risorsa viene aggiunta al `/Applications/FormsApplication/1.0/FormsFolder` posizione. (Vedi [Scrittura delle risorse](/help/forms/developing/aem-forms-repository.md#writing-resources).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.io.FileInputStream; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.Id; 
 import com.adobe.repository.infomodel.Lid; 
  
 import com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean; 
 import com.adobe.repository.infomodel.bean.Resource; 
 import com.adobe.repository.infomodel.bean.ResourceContent; 
  
 public class WriteFile { 
  
     // This quick start writes Loan.xdp to Applications/FormsApplication/1.0/FormsFolder 
     //Ensure that you create a AEM Forms application named FormsApplication using Workbench 
     public static void main(String[] args) { 
          
         try  
         { 
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
          
         //Create a ResourceRepositoryClient object 
         ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
          
         //Specify the parent path 
          String parentResourcePath = "/Applications/FormsApplication/1.0/FormsFolder"; 
          
         //Create a RepositoryInfomodelFactoryBean object 
          RepositoryInfomodelFactoryBean infomodelFactory = new RepositoryInfomodelFactoryBean(null); 
          
         //Create a Resource object to add to the Repository 
          Resource newResource = (Resource) infomodelFactory.newImage( 
                             new Id(),  
                             new Lid(),  
                             "Loan.xdp");  
                          
         //Create a ResourceContent object that contains the content (file bytes) 
         ResourceContent content = (ResourceContent) infomodelFactory.newResourceContent(); 
              
         //Create a Document that references an XDP file  
         //to add to the Repository 
         FileInputStream myForm = new FileInputStream("C:\\Adobe\Loan.xdp");  
         Document form = new Document(myForm); 
          
         //Set the description and the MIME type 
         content.setDataDocument(form);  
         content.setMimeType("application/vnd.adobe.xdp+xml"); 
                                          
         //Assign content to the Resource object 
         newResource.setContent(content) ; 
              
         //Set a description of the resource 
         newResource.setDescription("An XDP file"); 
                      
         //Commit to repository, and update resource 
         //in memory (by assignment) 
         Resource addResource = repositoryClient.writeResource(parentResourcePath, newResource); 
          
         //Get the description of the returned Resource object 
         System.out.println("The description of the new resource is "+addResource.getDescription()); 
          
         //Close the FileStream object 
         myForm.close();  
          
         } catch (Exception e) { 
              
              e.printStackTrace(); 
            } 
         } 
 } 
 
```

## Avvio rapido (modalità SOAP): Inserimento di risorse nell’elenco tramite l’API Java {#quick-start-soap-mode-listing-resources-using-the-java-api}

Nell&#39;esempio di codice Java seguente sono elencate le risorse che si trovano in `Applications/FormsApplication/1.0/FormsFolder`. (Vedi [Elencare risorse](/help/forms/developing/aem-forms-repository.md#listing-resources).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.bean.Resource; 
  
 //This quick start lists the content located in Applications/FormsApplication/1.0/FormsFolder 
 //Ensure that you create a AEM Forms application named Applications/FormsApplication using Workbench 
 public class ListFiles { 
  
     public static void main(String[] args) { 
  
         try  
         { 
             //Set connection properties required to invoke AEM Forms                             
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
              
             // List all the files located in the  
             String resourceFolderPath = "/Applications/FormsApplication/1.0/FormsFolder"; 
  
             // Retrieve the list of resources under the folder path 
             List members = repositoryClient.listMembers(resourceFolderPath); 
  
             // Print out the resources that were found 
             System.out.println("The following resources were found:"); 
             for (int i = 0; i < members.size(); i++) { 
                 Resource r = (Resource)(members.get(i)); 
                 System.out.println( 
                     "Resource name: " + 
                     r.getName() + 
                     "  Resource Description: " + 
                     r.getDescription() 
                 ); 
             } 
  
         } catch (Exception e) { 
              e.printStackTrace(); 
           } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Lettura di una risorsa tramite l’API Java {#quick-start-soap-mode-reading-a-resource-using-the-java-api}

Il seguente esempio di codice Java legge una risorsa chiamata *Loan.xdp* dal repository. Il file XDP si trova in `/Applications/FormsApplication/1.0/FormsFolder/`. (Vedi [Lettura delle risorse](/help/forms/developing/aem-forms-repository.md#reading-resources).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.bean.*; 
  
 //This quick start retrieves Loan.xdp from Applications/FormsApplication/1.0/FormsFolder 
 //Ensure that you create a AEM Forms application named FormsApplication using Workbench 
 public class ReadFile { 
  
      
     public static void main(String[] args) { 
  
         try  
         { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
  
             // Specify the path to the Loan.xdp 
             String resourceUri =  "/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp"; 
  
             // Retrieve the XDP file  
             Resource r = repositoryClient.readResource(resourceUri); 
  
             // Print the resource verification message 
             System.out.println( 
                 "Resource " +  
                 resourceUri +  
                 " was successfully retrieved." + 
                 "Resource content contains " + 
                 r.getContent().getDataDocument().length() + 
                 " bytes." 
             ); 
  
         } catch (Exception e) { 
             System.out.println( 
                 "Exception thrown while trying to read the file" + 
                 e.getMessage() 
             ); 
         } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Aggiornamento di una risorsa tramite l’API Java {#quick-start-soap-mode-updating-a-resource-using-the-java-api}

I seguenti aggiornamenti del codice Java `/Applications/FormsApplication/1.0/FormsFolder` modificando la descrizione. (Vedi [Aggiornamento delle risorse](/help/forms/developing/aem-forms-repository.md#updating-resources).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.bean.*; 
 import java.util.*; 
  
 //This quick start updates the description of Applications/FormsApplication/1.0/FormsFolder 
 //Ensure that you create a AEM Forms application named Applications/FormsApplication using Workbench 
 public class UpdateResource { 
  
     public static void main(String[] args) { 
  
         // This example will update a resource in the AEM Forms repository 
         try  
         { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
  
             // Specify the URI of the resource to update 
             String resourceUri =  "/Applications/FormsApplication/1.0/FormsFolder"; 
  
             // Retrieve the resource  
             Resource resource = repositoryClient.readResource(resourceUri); 
  
             // Update its description  
             resource.setDescription("This folder stores XDP files"); 
  
             // Update the resource in the repository 
             Resource updatedResource = repositoryClient.updateResource( 
                 resourceUri, 
                 resource, 
                 true 
             ); 
  
             // Print the resource verification message 
             System.out.println( 
                 "Resource " +  
                 resourceUri +  
                 "version " +  
                 updatedResource.getMajorVersion() + 
                 "." + 
                 updatedResource.getMinorVersion() + 
                 " was successfully updated." 
             ); 
  
         } catch (Exception e) { 
             System.out.println( 
                 "Exception thrown while trying to update the resource" + 
                 e.getMessage() 
             ); 
         } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Ricerca di risorse tramite l’API Java {#quick-start-soap-mode-searching-for-resources-using-the-java-api}

Il seguente esempio di codice Java cerca Loan.xdp in `Applications/FormsApplication/1.0/FormsFolder`. (Vedi [Ricerca di risorse](/help/forms/developing/aem-forms-repository.md#searching-for-resources).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.bean.*; 
 import com.adobe.repository.query.*; 
 import com.adobe.repository.query.sort.*; 
  
 //This quick start searches for Loan.xdp in Applications/FormsApplication/1.0/FormsFolder 
 //Ensure that you create a AEM Forms application named FormsApplication using Workbench 
 public class SearchResources { 
      
     public static void main(String[] args) { 
  
         try  
         { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
  
             // Specify the URI of the target folder  
             String testFolderUri = "/Applications/FormsApplication/1.0/FormsFolder"; 
  
             // Specify the attribute name for which to search 
             String name = "Loan.xdp"; 
  
             // Create a Query used in the search 
             Query query = new Query(); 
             Query.Statement statement = new Query.Statement( 
                 Resource.ATTRIBUTE_NAME,  
                 Query.Statement.OPERATOR_BEGINS_WITH,  
                 name 
             ); 
             statement.setNamespace(ResourceProperty.RESERVED_NAMESPACE_REPOSITORY); 
             query.addStatement(statement); 
  
             // Create the sort order used in the search 
             SortOrder sortOrder = new SortOrder(); 
             SortOrder.Element element = new SortOrder.Element(Resource.ATTRIBUTE_NAME, true); 
             sortOrder.addSortElement(element); 
  
             // Search for the resources 
             List listProperties = repositoryClient.searchProperties( 
                 testFolderUri,  
                 query, 
                 ResourceCollection.DEPTH_INFINITE,  
                 0,  
                 10,  
                 sortOrder 
             ); 
  
             // Display the resources that were found 
             System.out.println("The following resources were found:"); 
             for (int i = 0; i < listProperties.size(); i++) { 
                 Resource r = (Resource)(listProperties.get(i)); 
                 System.out.println(r.getName()); 
             } 
  
         } catch (Exception e) { 
             System.out.println( 
                 "An exception occurred while attempting to search for resources." + 
                 e.getMessage() 
             ); 
         } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Creazione di relazioni tra le risorse tramite l’API Java {#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api}

Nell’esempio di codice Java seguente viene creata una relazione tra due risorse nell’archivio AEM Forms. (Vedi [Creazione di relazioni tra risorse](/help/forms/developing/aem-forms-repository.md#creating-resource-relationships).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.*; 
 import com.adobe.repository.infomodel.bean.*; 
  
 public class CreateRelationship { 
  
     public static void main(String[] args) { 
  
         // This example creates a relationship between two resources in the AEM Forms repository. 
         // First, two resources are created. 
         // A dependence relationship between the two resources will then be established and verified. 
         try  
         { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
  
             // Create a RepositoryInfomodelFactoryBean needed for creating resources 
             RepositoryInfomodelFactoryBean repositoryInfomodelFactory = new RepositoryInfomodelFactoryBean(null); 
  
             // Specify the URI of the target folder for writing the resource 
             String testFolderUri = "/Applications/FormsApplication/1.0/FormsFolder"; 
  
             // Create the resources to be written to the folder 
             Resource testResource1 = repositoryInfomodelFactory.newResource( 
                 new Id(),  
                 new Lid(),  
                 "FormFolderA" 
             ); 
  
             Resource testResource2 = repositoryInfomodelFactory.newResource( 
                 new Id(), 
                 new Lid(), 
                 "FormFolderB" 
             ); 
  
             // Set the resources’ descriptions 
             testResource1.setDescription("test resource1"); 
             testResource2.setDescription("test resource2"); 
  
             // Write the resources to the folder 
             repositoryClient.writeResource(testFolderUri, testResource1); 
             repositoryClient.writeResource(testFolderUri, testResource2); 
  
             // Retrieve the resources’ URIs 
             String resourceUri1 = testFolderUri + "/" + testResource1.getName(); 
             String resourceUri2 = testFolderUri + "/" + testResource2.getName(); 
  
             // Retrieve the resources to verify that they were successfully written 
             Resource r1 = repositoryClient.readResource(resourceUri1); 
             Resource r2 = repositoryClient.readResource(resourceUri2); 
  
             // Create a relationship between the two resources 
             repositoryClient.createRelationship( 
                 resourceUri1,  
                 resourceUri2,  
                 Relation.TYPE_DEPENDANT_OF,  
                 true 
             ); 
  
             // Verify the relationship 
             List relations = repositoryClient.getRelated( 
                 resourceUri1,  
                 true,  
                 Relation.TYPE_DEPENDANT_OF 
             ); 
  
             // Print the relationship 
             for (int i = 0; i < relations.size(); i++) { 
                 Resource r = (Resource)(relations.get(i)); 
                 System.out.println("Related resource: " + r.getName()); 
             } 
  
         } catch (Exception e) { 
             System.out.println( 
                 "Exception thrown while trying to create the relationship" + 
                 e.getMessage() 
             ); 
         } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Blocco di una risorsa tramite API Java {#quick-start-soap-mode-locking-a-resource-using-the-java-api}

Il seguente esempio di codice Java blocca /Applications/FormsApplication/1.0/FormsFolder/Loan.xdp. (Vedi [Blocco delle risorse](/help/forms/developing/aem-forms-repository.md#locking-resources).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.bean.*; 
  
 public class LockFile { 
  
     public static void main(String[] args) { 
  
         // This example will lock and unlock a resource in the AEM Forms repository. 
         try { 
             //Set connection properties required to invoke AEM Forms                                  
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
  
             // Specify the URI of the resource to lock 
             String resourceUri = "/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp"; 
  
             // Lock the resource 
             repositoryClient.lockResource( 
                 resourceUri, 
                 Lock.SCOPE_EXCLUSIVE, 
                 Lock.DEPTH_ZERO 
             ); 
  
             // Retrieve the locks on the resource 
             List locks = repositoryClient.getLocks(resourceUri); 
  
             // Print out the locks for the resource 
             System.out.println("The following locks now exist for the resource:"); 
             for (int i = 0; i < locks.size(); i++) { 
                 Lock l = (Lock)(locks.get(i)); 
                 System.out.println( 
                     "Lock owner: " + 
                     l.getOwnerUserId() + 
                     "  Lock depth: " + 
                     l.getDepth() + 
                     " Lock scope: " + 
                     l.getType() 
                 ); 
             } 
  
             // Unlock the resource 
             String lockToken = repositoryClient.unlockResource(resourceUri); 
  
         } catch (Exception e) { 
             System.out.println( 
                 "Exception thrown while trying to lock the file" + 
                 e.getMessage() 
             ); 
         } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Gestione degli elenchi di controllo accessi tramite l’API Java {#quick-start-soap-mode-managing-access-control-lists-using-the-java-api}

Il seguente esempio di codice Java legge e crea elenchi di controllo accessi (ACL) nel repository.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.bean.*; 
  
 public class UseACL { 
  
     public static void main(String[] args) { 
  
         // This example will read and create access control lists for resources in the AEM Forms repository. 
         try { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
  
             // Specify the URI of the resource to be used 
             String resourceUri = "/Applications/FormsApplication"; 
  
             // Retrieve the access control list for the resource 
             AccessControlList acl = repositoryClient.readAccessControlList(resourceUri); 
  
             // Retrieve a list of the users having access permissions 
             List users = acl.getUsersWithPermissions(); 
  
             // Print out the list of users 
             System.out.println("The following users have permissions:"); 
             for (int i = 0; i < users.size(); i++) { 
                 String user = (String)(users.get(i)); 
                 System.out.println("User identifier: " + user); 
             } 
  
             // Set up a new access control list 
             acl = new AccessControlList(); 
  
             // Retrieve a user identifier to be used in the access control list 
             String userId = (String)(users.get(0)); 
  
             // Create traversal permissions for the user 
             List permissions = new ArrayList(); 
             permissions.add(AccessControlEntry.READ_METADATA_USER_PERM); 
             permissions.add(AccessControlEntry.READ_CONTENT_USER_PERM); 
             acl.setPermissionsForUser(userId, permissions); 
  
             // Set the access control list for the folder 
             repositoryClient.writeAccessControlList(resourceUri, acl, true); 
  
             // Print out confirmation message 
             System.out.println("User " + userId + " has traversal permissions for the folder"); 
  
         } catch (Exception e) { 
             System.out.println( 
                 "Exception thrown while trying to manage access control lists" + 
                 e.getMessage() 
             ); 
         } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Eliminazione di una risorsa tramite l’API Java {#quick-start-soap-mode-deleting-a-resource-using-the-java-api}

Il seguente esempio di codice Java elimina Loan.xdp da `Applications/FormsApplication/1.0/FormsFolder`. Se il file XDP non si trova in questa cartella, viene generata un&#39;eccezione. (Vedi [Eliminazione delle risorse](/help/forms/developing/aem-forms-repository.md#deleting-resources).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-repository-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. commons-code-1.3.jar 
     * 7. jacorb.jar (use a different JAR file if the forms server is not deployed on JBoss) 
     * 8. jnp-client.jar (use a different JAR file if the forms server is not deployed on JBoss) 
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
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
 import com.adobe.repository.infomodel.*; 
 import com.adobe.repository.infomodel.bean.*; 
 import com.adobe.repository.RepositoryException; 
 import com.adobe.idp.Document; 
  
  
 // This quick start deletes Loan.xdp from Applications/FormsApplication/1.0/FormsFolder 
 //If this XDP is not located in this folder, an exception is thrown 
 //Ensure that you create a AEM Forms application named FormsApplication using Workbench 
 public class DeleteResource { 
  
     public static void main(String[] args) { 
  
         try  
         { 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             // Create the service client factory 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             // Create a ResourceRepositoryClient object using the service client factory 
             ResourceRepositoryClient repositoryClient = new ResourceRepositoryClient(myFactory); 
  
             // Create a RepositoryInfomodelFactoryBean needed for creating resources 
             RepositoryInfomodelFactoryBean repositoryInfomodelFactory = new RepositoryInfomodelFactoryBean(null); 
  
             // Specify the URI of the target folder from which the resource is deleted 
             String testFolderUri = "/Applications/FormsApplication/1.0/FormsFolder"; 
  
             // Create the resource to be written to the folder 
             Resource testResource = repositoryInfomodelFactory.newResource( 
                 new Id(),  
                 new Lid(),  
                 "Loan.xdp" 
             ); 
  
             // Retrieve the resource’s URI 
             String resourceUri = testFolderUri + "/" + testResource.getName(); 
  
             // Retrieve the resource to verify that it exists 
             Resource r = repositoryClient.readResource(resourceUri); 
  
             // Print the resource verification message 
             System.out.println(r.getName() +" is about to be deleted"); 
  
             // Delete the resource 
             repositoryClient.deleteResource(resourceUri); 
  
         } catch (Exception e) { 
             System.out.println( 
                 "Exception thrown while trying to delete the resource" + 
                 e.getMessage() 
             ); 
         } 
     } 
 } 
  
 
```
