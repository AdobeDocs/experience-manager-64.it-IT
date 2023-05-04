---
title: Gestione delle attività in una gerarchia organizzativa utilizzando la vista Gestione
seo-title: Managing tasks in an organizational hierarchy using Manager View
description: Modalità di accesso e di lavoro dei manager e dei responsabili dell’organizzazione ai rapporti diretti e indiretti nella scheda Da fare dell’area di lavoro di AEM Forms.
seo-description: How managers and organization heads can access and work on the tasks of their direct and indirect reports in the To-do tab in AEM Forms workspace.
uuid: a44d5a64-c03a-4337-8577-b121e6202449
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c7cf28bf-2806-47bc-a803-8bc0e803fc4d
exl-id: 28877528-2f91-4ee0-b9d8-c7df364ed803
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# Gestione delle attività in una gerarchia organizzativa utilizzando la vista Gestione {#managing-tasks-in-an-organizational-hierarchy-using-manager-view}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Nell’area di lavoro di AEM Forms, i responsabili possono ora accedere alle attività assegnate a qualsiasi persona nella propria gerarchia, ovvero ai rapporti diretti o indiretti, ed eseguire varie azioni su di esse. Le attività sono disponibili nella scheda Da eseguire nell’area di lavoro di AEM Forms. Le azioni supportate sulle attività dei rapporti diretti sono:

**Avanti** Inoltrare un&#39;attività dal rapporto diretto a qualsiasi utente.

**Richiesta** Rivendicare un’attività di un rapporto diretto.

**Richiesta e apertura** Richiedere l&#39;attività di un rapporto diretto e aprirlo automaticamente nell&#39;elenco To-do del manager.

**Rifiuta** Rifiuta un&#39;attività inoltrata a un report diretto da un altro utente. Questa opzione è disponibile per le attività inoltrate da altri utenti a un rapporto diretto.

AEM Forms limita l&#39;accesso degli utenti solo alle attività per le quali l&#39;utente ha il controllo degli accessi (ACL). Tale controllo assicura che un utente possa recuperare solo le attività per le quali l’utente dispone delle autorizzazioni di accesso. Utilizzando servizi web e implementazioni di terze parti per definire la gerarchia, un&#39;organizzazione può personalizzare la definizione di manager e i rapporti diretti in base alle proprie esigenze.

1. Crea un DSC. Per ulteriori informazioni, consulta l’argomento &quot;Sviluppo di componenti per AEM Forms&quot; in [Programmazione con AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63) guida.
1. Nel DSC, definisci un nuovo SPI per la gestione della gerarchia per definire rapporti diretti e la gerarchia all’interno degli utenti AEM Forms. Di seguito è riportato un esempio di frammento di codice Java™.

   ```as3
   public class MyHierarchyMgmtService 
   { 
        /*
       Input : Principal Oid for a livecycle user
       Output : Returns true when the user is either the service invoker OR his direct/indirect report.
       */
       boolean isInHierarchy(String principalOid) {
   
       }
   
       /* 
       Input : Principal Oid for a livecycle user
       Output : List of principal Oids for direct reports of the livecycle user
       A user may get direct reports only for himself OR his direct/indirect reports.
       So the API is functionally equivalent to - 
       isInHierarchy(principalOid) ? <return direct reports> : <return empty list>
       */
       List<String> getDirectReports(String principalOid) {
   
       }
   
       /* 
       Returns whether a livecycle user has direct reports or not.
       It's functionally equivalent to -
       getDirectReports(principalOid).size()>0
       */
       boolean isManager(String principalOid) {
   
       }  
   }
   ```

1. Crea un file component.xml. Assicurati che spec-id sia lo stesso mostrato nello snippet di codice sottostante. Di seguito è riportato un frammento di codice di esempio che è possibile riutilizzare.

   ```as3
   <component xmlns="https://adobe.com/idp/dsc/component/document"> 
       <component-id>com.adobe.sample.SampleDSC</component-id> 
       <version>1.1</version> 
       <supports-export>false</supports-export> 
         <descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class> 
         <services> 
           <service name="MyHierarchyMgmtService" title="My hierarchy management service" orchestrateable="false"> 
           <auto-deploy service-id="MyHierarchyMgmtService" category-id="Sample DSC" major-version="1" minor-version="0" /> 
           <description>Service for resolving hierarchy management.</description> 
            <specifications> 
            <specification spec-id="com.adobe.idp.taskmanager.dsc.enterprise.HierarchyManagementProvider"/> 
            </specifications> 
           <specification-version>1.0</specification-version> 
           <implementation-class>com.adobe.sample.hierarchymanagement.MyHierarchyMgmtService</implementation-class> 
           <request-processing-strategy>single_instance</request-processing-strategy> 
           <supported-connectors>default</supported-connectors> 
           <operation-config> 
               <operation-name>*</operation-name> 
               <transaction-type>Container</transaction-type> 
               <transaction-propagation>supports</transaction-propagation> 
               <!--transaction-timeout>3000</transaction-timeout--> 
           </operation-config> 
           <operations> 
               <operation anonymous-access="true" name="isInHierarchy" method="isInHierarchy"> 
                   <input-parameter name="principalOid" type="java.lang.String" /> 
                   <output-parameter name="result" type="java.lang.Boolean"/> 
               </operation> 
               <operation anonymous-access="true" name="getDirectReports" method="getDirectReports"> 
                   <input-parameter name="principalOid" type="java.lang.String" /> 
                   <output-parameter name="result" type="java.util.List"/> 
               </operation> 
               <operation anonymous-access="true" name="isManager" method="isManager"> 
                   <input-parameter name="principalOid" type="java.lang.String" /> 
                   <output-parameter name="result" type="java.lang.Boolean"/> 
               </operation> 
               </operations> 
               </service> 
         </services>
   </component>
   ```

1. Distribuire DSC tramite Workbench. Riavvia `ProcessManagementTeamTasksService` servizio.
1. Potrebbe essere necessario aggiornare il browser o disconnettersi/accedere nuovamente con l&#39;utente.

La schermata seguente illustra l’accesso alle attività dei rapporti diretti e alle azioni disponibili.

![cu_manager_view](assets/cu_manager_view.png)

Accesso ai compiti dei rapporti diretti e azione sui compiti
