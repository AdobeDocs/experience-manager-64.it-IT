---
title: Guida rapida API Java di Task Manager Service (SOAP)
seo-title: Task Manager Service Java API QuickStart(SOAP)
description: Utilizzare il servizio Gestione attività per assegnare le attività, bloccare le attività, recuperare le attività assegnate agli utenti, recuperare i dati del modulo dalle attività, modificare i dati del modulo, recuperare gli allegati dei file e recuperare le informazioni sulle attività.
seo-description: Use the Task Manager service to assign tasks, lock tasks, retrieve tasks assigned to users, retrieve form data from tasks, modify form data, retrieve file attachments, and retrieve task information.
uuid: fd6fceb1-865e-47a7-83fc-a63dcc2c21de
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 532e607d-5bc5-4ccc-92c6-30efe1081872
role: Developer
exl-id: 302b38e9-71fc-4e83-af01-856d7bd9af40
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 1%

---

# Guida rapida API Java di Task Manager Service (SOAP) {#task-manager-service-java-api-quickstart-soap}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per il servizio Task Manager sono disponibili i seguenti avvii rapidi.

[Avvio rapido (modalità SOAP): Assegnazione di attività tramite l’API Java](task-manager-service-java-api.md#quick-start-soap-mode-assigning-tasks-using-the-java-api)

[Avvio rapido (modalità SOAP): Blocco delle attività tramite l’API Java](task-manager-service-java-api.md#quick-start-soap-mode-locking-tasks-using-the-java-api)

[Avvio rapido (modalità SOAP): Recupero delle attività assegnate agli utenti tramite l’API Java](task-manager-service-java-api.md#quick-start-soap-mode-retrieving-tasks-assigned-to-users-using-the-java-api)

[Avvio rapido (modalità SOAP): Recupero dei dati dei moduli dalle attività tramite l’API Java](task-manager-service-java-api.md#quick-start-soap-mode-retrieving-form-data-from-tasks-using-the-java-api)

[Avvio rapido (modalità SOAP): Modifica dei dati dei moduli tramite l’API Java](task-manager-service-java-api.md#quick-start-soap-mode-modifying-form-data-using-the-java-api)

[Avvio rapido (modalità SOAP): Recupero degli allegati di file dalle attività tramite l’API Java](task-manager-service-java-api.md#quick-start-soap-mode-retrieving-file-attachments-from-tasks-using-the-java-api)

[Avvio rapido (modalità SOAP): Recupero delle informazioni sulle attività tramite l’API Java](task-manager-service-java-api.md#quick-start-soap-mode-retrieving-task-information-using-the-java-api)

Le operazioni AEM Forms possono essere eseguite utilizzando l’API fortemente tipizzata di AEM Forms e la modalità di connessione deve essere impostata su SOAP.

>[!NOTE]
>
>Non è possibile cercare le attività assegnate agli utenti utilizzando l’API del servizio Web. Il motivo è che non è possibile invocare il `taskList` , che è una chiamata del metodo necessaria per eseguire questa attività.

>[!NOTE]
>
>Quick Start situato in Programmazione con AEM Forms si basa sul sistema operativo del server Forms. Tuttavia, se si utilizza un altro sistema operativo, ad esempio UNIX, sostituire percorsi specifici di Windows con percorsi supportati dal sistema operativo applicabile. Allo stesso modo, se utilizzi un altro server applicativo J2EE, assicurati di specificare proprietà di connessione valide. Vedi [Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Avvio rapido (modalità SOAP): Assegnazione di attività tramite l’API Java {#quick-start-soap-mode-assigning-tasks-using-the-java-api}

L&#39;esempio di codice Java seguente assegna un&#39;attività a un utente chiamato Tony Blue.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
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
     * 20. adobe-workflow-client-sdk.jar 
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
  
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager; 
 import com.adobe.idp.taskmanager.dsc.client.*; 
 import com.adobe.idp.um.api.infomodel.PrincipalSearchFilter; 
 import com.adobe.idp.um.api.infomodel.User; 
 import com.adobe.livecycle.usermanager.client.DirectoryManagerServiceClient; 
  
 public class AssignTask { 
  
     public static void main(String[] args) { 
          
         try{ 
         //Set connection properties required to invoke AEM Forms 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
         //Create a TaskManager object 
         TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);     
              
         //Get the user identifer by calling  
         //a user-defined method 
         String userID = getUserId(myFactory); 
              
         //Forward task to another user 
         myTaskManager.forwardTask(343,userID); 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
      
      
     //This method returns the identifier value of tony blue 
      static private String getUserId(ServiceClientFactory myFactory){ 
       String oid = "";     
       try{ 
      
           //Create a DirectoryManagerServiceClient object              
           DirectoryManagerServiceClient dirClient = new DirectoryManagerServiceClient(myFactory); 
          
          //Find a local user 
          PrincipalSearchFilter psf = new PrincipalSearchFilter(); 
          psf.setUserId("tblue"); 
          List principalList = dirClient.findPrincipals(psf); 
          Iterator pit = principalList.iterator(); 
      
          User testUser = null; 
          if (pit.hasNext()) 
          { 
              //Obtain the principals object identifier 
              testUser = (User)(pit.next()); 
          } 
          oid = testUser.getOid(); 
          } 
              
           catch(Exception e) 
           { 
               e.printStackTrace(); 
           } 
               return oid; 
       } 
 } 
  
  
 
```

## Avvio rapido (modalità SOAP): Blocco delle attività tramite l’API Java {#quick-start-soap-mode-locking-tasks-using-the-java-api}

L&#39;esempio di codice Java seguente blocca un&#39;attività che corrisponde al valore dell&#39;identificatore dell&#39;attività 2.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
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
     * 20. adobe-workflow-client-sdk.jar 
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
     */ 
  
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager; 
 import com.adobe.idp.taskmanager.dsc.client.*;  
  
 public class LockTask { 
  
     public static void main(String[] args) { 
      
     try{ 
         //Set connection properties required to invoke AEM Forms 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
         //Create a TaskManager object 
         TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);     
              
         //Lock the task that corresponds to task identifier 2 
         myTaskManager.lockTask(2); 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Avvio rapido (modalità SOAP): Recupero delle attività assegnate agli utenti tramite l’API Java {#quick-start-soap-mode-retrieving-tasks-assigned-to-users-using-the-java-api}

Il seguente esempio di codice Java recupera tutte le attività assegnate a un utente denominato *azzurro*. Questo utente viene specificato nelle proprietà di connessione. Vengono visualizzate informazioni sulle attività restituite, ad esempio il valore e la descrizione dell’identificatore.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
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
     * 20. adobe-workflow-client-sdk.jar 
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
     */ 
  
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.taskmanager.dsc.client.query.StatusFilter; 
 import com.adobe.idp.taskmanager.dsc.client.query.TaskFilter; 
 import com.adobe.idp.taskmanager.dsc.client.query.TaskRow; 
 import com.adobe.idp.taskmanager.dsc.client.*; 
  
 public class RetrieveTaskInfo { 
  
     public static void main(String[] args) { 
  
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
  
             //Create a TaskManagerQueryService object     
             TaskManagerQueryService queryManager = TaskManagerClientFactory.getQueryManager(myFactory); 
  
             //Define search criteria by performing a search on  
             //Assigned tasks (tasks assigned to the user specified 
             //in connection properties)  
             TaskFilter filter = queryManager.newTaskFilter();  
             StatusFilter sf = filter.newStatusFilter();  
             sf.addStatus(StatusFilter.assigned);  
             filter.setStatusFiltering(sf);  
  
             //Perform the search 
             List result = queryManager.taskList(filter);  
  
             //Create an Iterator object and iterate through 
             //the List object 
             Iterator iter = result.iterator(); 
             int i = 0 ; 
  
             while (iter.hasNext()) { 
  
                 TaskRow myTask = (TaskRow)iter.next(); 
  
                 //Get the task identifier value 
                 long taskId = myTask.getTaskId(); 
  
                 //Get the status of the task 
                 long taskStatus = myTask.getTaskStatus(); 
                  
                 //Get the name of process on which this task is based 
                 String processName = myTask.getProcessName(); 
  
                 //Get the task description 
                 String taskDes = myTask.getDescription(); 
  
                 System.out.println("The task identifier is "+taskId +"\n"+ 
                  "The status of the task is "+taskStatus +"\n"+ 
                  "The name of the process on which the task is based is "+processName +"\n"+ 
                  "The task description is "+taskDes); 
                  i++ ;  
                  } 
             } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 }
```

## Avvio rapido (modalità SOAP): Recupero dei dati dei moduli dalle attività tramite l’API Java {#quick-start-soap-mode-retrieving-form-data-from-tasks-using-the-java-api}

L&#39;esempio di codice Java seguente recupera i dati del modulo da un&#39;attività con il valore di identificatore 304. I dati del modulo vengono scritti in un file XML denominato *FormData.xml* all&#39;indirizzo C:\Adobe.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
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
      * 20. adobe-workflow-client-sdk.jar 
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
     */ 
 import java.io.File; 
 import java.util.*; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 import com.adobe.idp.taskmanager.dsc.client.*; 
 import com.adobe.idp.taskmanager.dsc.client.task.FormInstance; 
 import com.adobe.idp.taskmanager.dsc.client.task.TaskInfo; 
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager; 
  
 public class RetrieveFormData { 
  
     public static void main(String[] args) { 
              
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
  
             //Create a TaskManager object 
             TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);     
                          
             //Retrieve information about task 304 
             long taskId = 304;  
             TaskInfo tInfo = myTaskManager.getTaskInfo(taskId); 
                          
             //Retrieve the form instance associated with task 304 
             FormInstance[] fi = tInfo.getTaskItems(); 
             long formInstanceId = fi[0].getFormInstanceId(); 
             FormInstance newfi = myTaskManager.getFormInstanceForTask(taskId, formInstanceId, true); 
              
             //Get data located in the form and  
             //write the data to FormData.xml 
             Document doc = newfi.getDocument(); 
             File myTestFile = new File("C:\\Adobe\FormData.xml"); 
             doc.copyToFile(myTestFile); 
             } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## Avvio rapido (modalità SOAP): Modifica dei dati dei moduli tramite l’API Java {#quick-start-soap-mode-modifying-form-data-using-the-java-api}

Il seguente esempio di codice Java aggiorna un modulo con dati che si trovano nella *FormData.xml* file.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
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
      * 20. adobe-workflow-client-sdk.jar 
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
     */ 
  
 import java.io.FileInputStream; 
 import java.io.InputStream; 
 import java.util.*; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 import com.adobe.idp.taskmanager.dsc.client.*; 
 import com.adobe.idp.taskmanager.dsc.client.task.FormInstance; 
 import com.adobe.idp.taskmanager.dsc.client.task.SaveTaskResult; 
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager; 
  
 public class SetFormData { 
  
     public static void main(String[] args) { 
     try{ 
         //Set connection properties required to invoke AEM Forms 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "tblue"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
         //Create a TaskManager object 
         TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);     
                                  
         //Specify form data that is used to update the form 
         FileInputStream myData = new FileInputStream("C:\\Adobe\FormData.xml"); 
         Document doc = new Document(myData);  
         InputStream in = doc.getInputStream();  
         byte[] formarray = new byte[in.available()];  
         in.read(formarray);  
                          
         //Get an empty form instance 
         FormInstance newForm = myTaskManager.getEmptyForm(); 
         newForm.setTemplatePath("C:\\Adobe\Mortgage.xdp"); 
         newForm.setXFAData(formarray); 
         newForm.setDocument(doc); 
              
         //Save the modified form 
         SaveTaskResult result = myTaskManager.save(4, newForm);  
         System.out.println("ActionFromData= "+result.getActionFromData());  
         System.out.println("task id= "+result.getTaskId());  
         } 
              
     catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## Avvio rapido (modalità SOAP): Recupero degli allegati di file dalle attività tramite l’API Java {#quick-start-soap-mode-retrieving-file-attachments-from-tasks-using-the-java-api}

Il seguente esempio di codice Java recupera gli allegati di file. Ciascun file allegato viene salvato come file TXT.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
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
     * 20. adobe-workflow-client-sdk.jar 
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
     */ 
  
 import java.io.File; 
 import java.util.*; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.taskmanager.dsc.client.*; 
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager; 
  
 public class RetrieveFileAttachments 
     { 
  
     public static void main(String[] args) { 
              
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
  
             //Create a TaskManager object 
             TaskManager myTaskManager = TaskManagerClientFactory.getTaskManager(myFactory);     
                          
             //Retrieve file attachments associated with the task 
             List fileAttachments = myTaskManager.getAttachmentListForTask(322); 
              
             //Create an Iterator object and iterate through 
             //the List object 
             Iterator iter = fileAttachments.iterator(); 
             int i = 0 ; 
             while (iter.hasNext()) { 
                  Document fileAttachment= (Document)iter.next(); 
                  File myFile = new File("C:\\FileAtt" +i+".txt"); 
                  fileAttachment.copyToFile(myFile); 
                   i++ ;  
               } 
             } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## Avvio rapido (modalità SOAP): Recupero delle informazioni sulle attività tramite l’API Java {#quick-start-soap-mode-retrieving-task-information-using-the-java-api}

Il seguente esempio di codice Java recupera tutte le attività basate su un processo denominato *mutuo ipotecario - Precostruito*. Lo stato di ogni attività restituita viene controllato per verificare che sia un&#39;attività completata. Vengono recuperate e visualizzate informazioni quali il nome dell’utente che ha completato l’attività e la data in cui l’attività è stata completata.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-taskmanager-client.jar 
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
     * 20. adobe-workflow-client-sdk.jar 
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
     */ 
 import java.util.*; 
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.taskmanager.dsc.client.query.TaskRow; 
 import com.adobe.idp.taskmanager.dsc.client.query.TaskSearchFilter; 
 import com.adobe.idp.taskmanager.dsc.client.task.ParticipantInfo; 
 import com.adobe.idp.taskmanager.dsc.client.task.TaskInfo; 
 import com.adobe.idp.taskmanager.dsc.client.task.TaskManager; 
 import com.adobe.idp.taskmanager.dsc.client.*; 
 import com.adobe.idp.um.api.infomodel.Principal; 
 import com.adobe.livecycle.usermanager.client.DirectoryManagerServiceClient; 
  
 public class RetrievingTasks { 
  
     public static void main(String[] args) { 
              
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
  
             //Create a TaskManagerQueryService object     
             TaskManagerQueryService queryManager = TaskManagerClientFactory.getQueryManager(myFactory); 
              
             //Create a TaskManager object 
             TaskManager taskManager = TaskManagerClientFactory.getTaskManager(myFactory); 
              
             //Define search criteria by performing a search on  
             //completed tasks 
             TaskSearchFilter filter = new TaskSearchFilter();  
             filter.setServiceName("MortgageLoan - Prebuilt"); 
             filter.setAdminIgnoreAllAcls(true); 
                                                              
             //Perform the search on tasks 
             List result = queryManager.taskSearch(filter);  
                      
             //Create an Iterator object and iterate through 
             //the List object 
             Iterator iter = result.iterator(); 
             int i = 0 ; 
             while (iter.hasNext()) { 
                 TaskRow myTask = (TaskRow)iter.next(); 
                              
                 //Make sure that the task is completed- 100 represents 
                 //a completed task 
                 if (myTask.getTaskStatus()== 100) 
                 { 
                     //Get the name of the user who completed the task 
                     long taskId = myTask.getTaskId(); 
                     TaskInfo taskInfo= taskManager.getTaskInfo(taskId); 
                     ParticipantInfo user = taskInfo.getAssignedTo(); 
                     String userId = user.getSpecifiedUserId(); 
                     String userName = getUserName(myFactory, userId); 
                      
                     //Get the name of the process 
                     String processName = myTask.getProcessName(); 
                      
                     //Get the completion time 
                     Date completionTime = myTask.getCompleteTime(); 
                      
                     //Display task information     
                      System.out.println("The task identifier is "+taskId +"\n"+ 
                     "The name of the user who completed the task is "+ userName +"\n"+ 
                     "The name of the process on which the task is based is "+ processName+"\n"+ 
                      "The completion time is "+ completionTime.getDate()); 
                      i++ ; 
                     } 
                  } 
             } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
      
      
     //This method accepts a user Id and returns the corresponding user name 
     static private String getUserName(ServiceClientFactory myFactory, String userId){ 
          String userName = "";     
          try{ 
              //Create a DirectoryManagerServiceClient object              
              DirectoryManagerServiceClient dirClient = new DirectoryManagerServiceClient(myFactory); 
          
             //Find a local user 
             Principal prin = dirClient.findPrincipal(userId); 
             userName = prin.getCanonicalName(); 
             } 
          catch(Exception e) 
          { 
              e.printStackTrace(); 
          } 
          return userName; 
       } 
     } 
 
```
