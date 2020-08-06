---
title: 'Utilizzare i metadati in una notifica e-mail '
seo-title: 'Utilizzare i metadati in una notifica e-mail '
description: Utilizzare i metadati per compilare le informazioni in una notifica e-mail del flusso di lavoro moduli
seo-description: Utilizzare i metadati per compilare le informazioni in una notifica e-mail del flusso di lavoro moduli
uuid: 17e018c9-6bf8-4042-bba9-4ebe449304ac
topic-tags: publish
discoiquuid: bdf13893-630a-43cd-aaeb-c7c16bf4f8a6
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 1%

---


# Utilizzare i metadati in una notifica e-mail  {#use-metadata-in-an-email-notification}

Utilizzare i metadati per compilare le informazioni in una notifica e-mail del flusso di lavoro moduli

È possibile utilizzare il passaggio Assegna attività per creare e assegnare attività a un utente o a un gruppo. Quando un&#39;attività viene assegnata a un utente o gruppo, viene inviata una notifica e-mail all&#39;utente definito o a ciascun membro del gruppo definito. Una tipica notifica [](/help/forms/using/use-custom-email-template-assign-task-step.md) e-mail contiene il collegamento dell’attività assegnata e le informazioni relative all’attività.

Potete utilizzare i metadati in un modello e-mail per compilare dinamicamente le informazioni in una notifica e-mail. Ad esempio, il valore del titolo, della descrizione, della data di scadenza, della priorità, del flusso di lavoro e dell’ultima data nella seguente notifica e-mail viene selezionato dinamicamente in fase di esecuzione (quando viene generata una notifica e-mail).

![default-email-template](assets/default-email-template.png)

I metadati sono memorizzati in coppie chiave-valore. Potete specificare la chiave nel modello e-mail e la chiave viene sostituita con un valore in fase di esecuzione (quando viene generata una notifica e-mail). Ad esempio, nell&#39;esempio di codice seguente, &quot;$ {workitem_title} &quot; è una chiave. Viene sostituito con il valore &quot;Loan-Request&quot; in fase di esecuzione.

```xml
subject=Task Assigned - ${workitem_title}

message=<html><body>\n\
 <table>\n\
  <tbody>\n\
   <tr>\n\
    <td>\n\
      Sample Company\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <pre style="font-size: 13px; font-family: Helvetica, Arial, sans-serif;  font-weight: normal; color: #323232;"> Hello ${workitem_assignee},\n\
 The following task has been assigned to you:</pre>\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <table>\n\
      <tbody>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> TITLE</td>\n\
        <td>\n\
         <p>${workitem_title}</p>\n\
        </td>\n\
       </tr>\n\
                            <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> DESCRIPTION</td>\n\
        <td>\n\
         <p>${workitem_description}</p>\n\
        </td>\n\
       </tr>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> DUE DATE</td>\n\
        <td>\n\
         <p>${workitem_due_date}</p>\n\
        </td>\n\
       </tr>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> PRIORITY</td>\n\
        <td>\n\
         <p>${workitem_priority}</p>\n\
        </td>\n\
       </tr>\n\
       <tr>\n\
        <td> WORKFLOW</td>\n\
        <td>\n\
         <p>${workitem_workflow}</p>\n\
        </td>\n\
       </tr>\n\
      </tbody>\n\
     </table>\n\
    </td>\n\
   </tr>\n\
   <tr style = "text-align: center; vertical-align: middle;">\n\
    <td> \n\
     <a href="${workitem_url}" target="_blank" style="background-color: #1EBBBB; font-size: 18px; line-height: 25px; font-weight: bold; color: #FFFFFF; text-decoration: none; padding: 15px 15px 15px 15px;">Open Task</a>\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <p><span style="font-size: 12px; font-weight: normal; font-style: italic; color: #919191;">This is an automatically generated email. Please do not reply to this email.</span></p>\n\
    </td>\n\
   </tr>\n\
  </tbody>\n\
 </table>\n\
</body>\n\
</html>\n\
```

## Utilizzo dei metadati generati dal sistema in una notifica e-mail {#using-system-generated-metadata-in-an-email-notification}

Un&#39;applicazione AEM Forms  fornisce diverse variabili di metadati (coppie chiave-valore) pronte all&#39;uso. Potete usare queste variabili in un modello e-mail. Il valore della variabile si basa sull&#39;applicazione dei moduli associata. Nella tabella seguente sono elencate tutte le variabili di metadati disponibili:

<table> 
 <tbody> 
  <tr> 
   <td>Chiave</td> 
   <td>Descrizione</td> 
  </tr> 
  <tr> 
   <td>workitem_title</td> 
   <td>Titolo dell'applicazione dei moduli associata.</td> 
  </tr> 
  <tr> 
   <td>workitem_url</td> 
   <td>URL per accedere all'applicazione dei moduli associata.</td> 
  </tr> 
  <tr> 
   <td>workitem_description</td> 
   <td>Descrizione dell'applicazione dei moduli associata.</td> 
  </tr> 
  <tr> 
   <td>workitem_priority</td> 
   <td>Priorità specificata per l'applicazione dei moduli associata.</td> 
  </tr> 
  <tr> 
   <td>workitem_due_date</td> 
   <td>Ultima data di utilizzo dell'applicazione dei moduli associata.</td> 
  </tr> 
  <tr> 
   <td>workitem_workflow</td> 
   <td>Nome del flusso di lavoro associato all'applicazione dei moduli.</td> 
  </tr> 
  <tr> 
   <td>workitem_assign_timestamp</td> 
   <td>Data e ora in cui l’elemento del flusso di lavoro è stato assegnato all’assegnatario corrente.</td> 
  </tr> 
  <tr> 
   <td>workitem_assignee</td> 
   <td>Nome del presente assegnatario.</td> 
  </tr> 
  <tr> 
   <td>host_prefix</td> 
   <td>URL del server di creazione. Ad esempio, https://10.41.42.66:4502<br /> </td> 
  </tr> 
  <tr> 
   <td>publish_prefix</td> 
   <td>URL del server di pubblicazione. Ad esempio, https://10.41.42.66:4503</td> 
  </tr> 
 </tbody> 
</table>

## Utilizzo di metadati personalizzati in una notifica e-mail {#using-custom-metadata-in-an-email-notification}

Potete inoltre utilizzare metadati personalizzati in una notifica e-mail. I metadati personalizzati contengono informazioni oltre ai metadati generati dal sistema. Ad esempio, i dettagli dei criteri recuperati da un database. Potete utilizzare un bundle ECMAScript o OSGi per aggiungere metadati personalizzati in archivio crx:

### Utilizzare ECMAScript per aggiungere metadati personalizzati  {#use-ecmascript-to-add-custom-metadata}

[ECMAScript](https://en.wikipedia.org/wiki/ECMAScript) è un linguaggio di script. Viene utilizzato per applicazioni di script sul lato client e server. Effettuate le seguenti operazioni per utilizzare ECMAScript per aggiungere metadati personalizzati a un modello e-mail:

1. Accedete a CRX DE con un account amministrativo. L&#39;URL è `https://[server]:[port]/crx/de/index.jsp`

1. Andate a /apps/fd/dashboard/scripts/metadataScript. Create un file con estensione .ecma. Ad esempio, usermetadata.ecma

   Se il percorso sopra indicato non esiste, crealo.

1. Aggiungete il codice al file .ecma che ha la logica per generare metadati personalizzati nelle coppie chiave-valore. Ad esempio, il seguente codice ECMAScript genera metadati personalizzati per una polizza assicurativa:

   ```
   function getUserMetaData()  {
       //Commented lines below provide an overview on how to set user metadata in map and return it.
       var HashMap = Packages.java.util.HashMap;
       var valuesMap = new HashMap();
       valuesMap.put("policyNumber", "2017568972695");
       valuesMap.put("policyHolder", "Adobe Systems");
   
       return valuesMap;
   }
   ```

1. Fate clic su Salva tutto. Ora, lo script è disponibile per la selezione nel modello AEM flusso di lavoro.

   ![assign-task-metadata](assets/assigntask-metadata.png)

1. (Facoltativo) Specificare il titolo dello script:

   Se non si specifica il titolo, il campo Metadati personalizzati visualizza il percorso completo del file ECMAScript. Per specificare un titolo significativo per lo script, effettuare le operazioni seguenti:

   1. Espandete il nodo script, fate clic con il pulsante destro del mouse sul nodo **[!UICONTROL jcr:content]** e fate clic su **[!UICONTROL Mixins]**.
   1. Digitare mix:title nella finestra di dialogo Modifica mixin e fare clic su **+**.
   1. Aggiungete una proprietà con i seguenti valori.

      | Nome | jcr:title |
      |---|---|
      | Tipo | Stringa |
      | Valore | Specificate il titolo dello script. Ad esempio, metadati personalizzati per il titolare della polizza. Il valore specificato viene visualizzato nel passaggio dell&#39;attività di assegnazione. |

### Utilizzare un bundle OSGi e un&#39;interfaccia Java per aggiungere metadati personalizzati {#use-an-osgi-bundle-and-java-interface-to-add-custom-metadata}

Potete usare l’interfaccia Java WorkitemUserMetadataService per aggiungere metadati personalizzati per i modelli e-mail. Potete creare un bundle OSGi che utilizza l’interfaccia Java WorkitemUserMetadataService e distribuirlo sul server AEM Forms . Rende i metadati disponibili per la selezione nel passaggio Assegna attività.

Per creare un bundle OSGi con l’interfaccia Java, aggiungete [file JAR](https://helpx.adobe.com/it/aem-forms/kb/aem-forms-releases.html) AEM Forms Client SDK [e Jar](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.workflow.api/1.0.2/) granite come dipendenze esterne al progetto bundle OSGi. Potete utilizzare qualsiasi IDE Java per creare un bundle OSGi. La procedura seguente illustra i passaggi per utilizzare Eclipse per creare un bundle OSGi:

1. Aprite Eclipse IDE. Selezionare File > Nuovo progetto.

1. Nella schermata Seleziona una procedura guidata, selezionate Progetto Paradiso e fate clic su Avanti.

1. Nel progetto New Maven, mantenete le impostazioni predefinite e fate clic su Next (Avanti). Selezionate un archetipo e fate clic su Avanti. Ad esempio, maven-archetype-quickstart. Specificate ID gruppo, ID evento, versione e pacchetto per il progetto, quindi fate clic su Fine. Il progetto viene creato.

1. Aprite il file pom.xml per la modifica e sostituite tutto il contenuto del file con quanto segue:

   ```
   
   ```

1. Aggiungete il codice sorgente che utilizza l’interfaccia Java WorkitemUserMetadataService per aggiungere metadati personalizzati per i modelli e-mail. Di seguito è riportato un esempio di codice:

   ```java
   package com.aem.impl;
   
   import com.adobe.fd.workspace.service.external.WorkitemUserMetadataService;
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Properties;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.osgi.framework.Constants;
   
   import java.util.HashMap;
   import java.util.Map;
   
   @Component
   @Service
   @Properties({
           @Property(name = Constants.SERVICE_DESCRIPTION, value = "A sample implementation of a user metadata service."),
           @Property(name = WorkitemUserMetadataService.SERVICE_PROPERTY_LABEL, value = "Default User Metadata Service")})
   
   public class WorkitemUserMetadataServiceImpl
     implements WorkitemUserMetadataService
   {
     public WorkitemUserMetadataServiceImpl() {}
   
     public Map<String, String> getUserMetadataMap()
     {
       HashMap<String, String> metadataMap = null;
       metadataMap = new HashMap();
       metadataMap.put("test_metadata", "tested-interface implementation");
       return metadataMap;
     }
   }
   ```

1. Aprite un prompt dei comandi e andate alla directory contenente il progetto bundle OSGi. Usate il comando seguente per creare il bundle OSGi:

   `mvn clean install`

1. Caricate il bundle in un server AEM Forms . Potete usare AEM Package Manager per importare il bundle  server AEM Forms.

Una volta importato il bundle, potete selezionare i metadati nel passaggio Assegna attività e usarlo come modello e-mail.
