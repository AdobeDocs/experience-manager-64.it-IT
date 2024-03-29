---
title: Visualizzazione dell’avatar utente
seo-title: Displaying the user avatar
description: Come personalizzare l’area di lavoro di AEM Forms per visualizzare l’immagine di un utente connesso.
seo-description: How to customize the AEM Forms workspace to display the image of a logged-in user.
uuid: 2961dc93-f0d0-4842-80f1-3c239a20e348
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: aec03ea5-17a6-4775-92cb-2ad361895fdf
exl-id: 2bc70cd6-1ea6-4594-9b42-ab3d3000a0c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 3%

---

# Visualizzazione dell’avatar utente {#displaying-the-user-avatar}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’avatar dell’utente connesso viene visualizzato nell’angolo superiore destro dell’area di lavoro di AEM Forms. Inoltre, gli avatar dei rapporti diretti nella gerarchia organizzativa vengono visualizzati nella visualizzazione Gestione. È possibile configurare l&#39;area di lavoro AEM Forms per scegliere le immagini utente dal database, ad esempio il server LDAP.

>[!NOTE]
>
>Le proporzioni supportate delle immagini utente sono 1:1.

1. Crea un DSC utilizzando i dettagli indicati nel passaggio successivo. Per ulteriori informazioni, consulta l’argomento &quot;Sviluppo di componenti per AEM Forms&quot; in [Programmazione con AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63) guida.
1. Nel DSC, definisci un nuovo SPI che espone i metodi getCurrentUserImageUrl e getUserImageUrl per ottenere un URL immagine per un utente AEM Forms. Di seguito è riportato un esempio di frammento di codice Java™:

   ```as3
   public class DemoUserImageURLProviderService { 
     public String getCurrentUserImageUrl() 
     { 
        // return the URL for profile Image of logged in user 
     } 
     public String getUserImageUrl(String principalOid) 
     { 
         // return the URL for profile Image for user represented by this principal Oid 
      } 
   }
   ```

1. Crea un file component.xml. Assicurati che spec-id sia come mostrato nello snippet di codice seguente.

   Il seguente frammento di codice è un esempio. Personalizzalo in base alle tue esigenze specifiche.

   ```as3
   <component xmlns="https://adobe.com/idp/dsc/component/document"> 
       <component-id>com.adobe.sample.DemoUsersComponent</component-id> 
       <version>1.1</version> 
       <supports-export>false</supports-export> 
       <descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class> 
       <services> 
           <service name="DemoUserImageURLProviderService" title="Demo User ImageURL provider service" orchestrateable="false"> 
           <auto-deploy service-id="DemoUserImageURLProviderService" category-id="Demo Users Component DSC" major-version="1" minor-version="0" /> 
           <description>Service for resolving user image url.</description> 
            <specifications> 
            <specification spec-id="com.adobe.idp.taskmanager.dsc.enterprise.UserImageUrlProvider"/> 
            </specifications> 
           <specification-version>1.0</specification-version> 
           <implementation-class>com.adobe.sample.demousers.DemoUserImageURLProviderService</implementation-class> 
           <request-processing-strategy>single_instance</request-processing-strategy> 
           <supported-connectors>default</supported-connectors> 
           <operation-config> 
               <operation-name>*</operation-name> 
               <transaction-type>Container</transaction-type> 
               <transaction-propagation>supports</transaction-propagation> 
               <!--transaction-timeout>3000</transaction-timeout--> 
           </operation-config> 
           <operations> 
               <operation anonymous-access="false" name="getCurrentUserImageUrl" method="getCurrentUserImageUrl"> 
                   <output-parameter name="result" type="java.lang.String"/> 
               </operation> 
               <operation anonymous-access="false" name="getUserImageUrl" 
   method="getUserImageUrl"> 
               <input-parameter name="principalOid" type="java.lang.String"/> 
               <output-parameter name="result" type="java.lang.String"/> 
               </operation> 
           </operations> 
           </service> 
       </services>
   </component>
   ```

1. Distribuire DSC tramite Workbench. Riavvia `ProcessManagementClientSessionService` servizio.
1. Potrebbe essere necessario aggiornare il browser o disconnettersi/accedere nuovamente con l&#39;utente.
