---
title: Visualizzazione di dati aggiuntivi nell'elenco Attività
seo-title: Visualizzazione di dati aggiuntivi nell'elenco Attività
description: Procedura per personalizzare la visualizzazione dell'elenco A dell'LiveCycle  dell'area di lavoro AEM Forms per visualizzare ulteriori informazioni oltre a quelle predefinite.
seo-description: Procedura per personalizzare la visualizzazione dell'elenco A dell'LiveCycle  dell'area di lavoro AEM Forms per visualizzare ulteriori informazioni oltre a quelle predefinite.
uuid: 4c678d9c-7794-4b62-8705-d62c7780c13f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b74a0933-2b96-4a88-9995-6fb21df141aa
translation-type: tm+mt
source-git-commit: a5cac0d369bb40659cfde011e5d6ef9a68dc4012
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Visualizzazione di dati aggiuntivi nell&#39;elenco ToDo {#displaying-additional-data-in-todo-list}

Per impostazione predefinita, nell&#39;elenco  attività dell&#39;area di lavoro di AEM Forms vengono visualizzati il nome e la descrizione dell&#39;attività. Tuttavia, potete aggiungere altre informazioni, ad esempio data di creazione e data di scadenza. È inoltre possibile aggiungere icone e modificare lo stile della visualizzazione.

![Vedere la scheda Attività di HTML Workspace che mostra la configurazione predefinita](assets/html-todo-list.png)

In questo articolo sono descritti i passaggi da eseguire per aggiungere informazioni da visualizzare per ogni attività nell&#39;elenco Attività.

## Cosa è possibile aggiungere {#what-can-be-added}

È possibile aggiungere le informazioni disponibili in `task.json` inviate dal server. Le informazioni possono essere aggiunte come testo normale oppure potete usare gli stili per formattare le informazioni.

Per ulteriori informazioni sulla descrizione dell&#39;oggetto JSON, consultate l&#39;articolo [this](/help/forms/using/html-workspace-json-object-description.md).

## Visualizzazione delle informazioni su un&#39;attività {#displaying-information-on-a-task}

1. Seguite i passaggi [Generici per  personalizzazione dell&#39;area di lavoro AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Per visualizzare informazioni aggiuntive su un&#39;attività, è necessario aggiungere le coppie chiave-valore corrispondenti all&#39;interno del blocco attività di `translation.json`.

   Ad esempio, modificare `/apps/ws/locales/en-US/translation.json` per Inglese:

   ```
   "task" : {
           "reminder" : {
               "value" : "Reminder",
               "tooltip" : "This is reminder __reminderCount__, for this task."
           },
           "deadlined" : {
               "value" : "Deadlined",
               "tooltip" : "This task has deadlined"
           },
           "save" : {
               "message" : "Task has been saved successfully"
           },
           "status" : {
               "deadlined" : "Deadlined",
               "created" : "Created",
               "assignedsaved" : "Draft from assigned task",
               "terminated" : "Terminated",
               "assigned" : "Assigned",
               "unknown" : "Unknown",
               "createdsaved" : "Draft from created task",
               "completed" : "Completed"
           },
           "draft" : {
               "value" : "Saved",
               "tooltip" : "This task is marked as a draft"
           },
           "escalated" : {
               "value" : "Escalated",
               "tooltip" : "This task has been escalated"
           },
           "forward" : {
               "value" : "Forwarded",
               "tooltip" : "This task was forwarded"
           },
           "priority" : {
               "highest" : "Highest priority",
               "normal" : "Normal priority",
               "high" : "High priority",
               "low" : "Low priority",
               "lowest" : "Lowest priority"
           },
           "claimed" : {
               "value" : "Claimed",
               "tooltip" : "This task has been claimed"
           },
           "locked" : {
               "value" : "Locked",
               "tooltip" : "This task is locked"
           },
           "consulted" : {
               "value" : "Consulted",
               "tooltip" : "This task has been consulted"
           },
           "returned" : {
               "value" : "Returned",
               "tooltip" : "This task was returned back"
           },
           "multiplesubmitbuttons" : {
               "message" : "The form associated with this task has multiple submit buttons so the Workspace Complete button will be disabled. Click the appropriate button on the form to submit it."
           },
           "nosubmitbutton" : {
               "message" : "The form associated with this task does not appear to have submit buttons. You may need to upgrade your Adobe Reader version to 9.1 or greater and enable the Reader Submit option in your process."
           },
           "icon" : {
               "tooltip" : "open the task __taskName__"
           }
       }
   ```

   >[!NOTE]
   >
   >Aggiungete le coppie chiave-valore corrispondenti per tutte le lingue supportate.

1. Ad esempio, aggiungere informazioni all&#39;interno del blocco attività:

   ```
   "stepname" : {
               "value" : "Step Name",
               "tooltip" : "This task belongs to __stepName__ step"
   }
   ```

## Definizione CSS per la nuova proprietà {#defining-css-for-the-new-property}

1. È possibile applicare lo stile alle informazioni (proprietà) aggiunte a un&#39;attività. A questo scopo, è necessario aggiungere informazioni di stile per la nuova proprietà aggiunta a `/apps/ws/css/newStyle.css`.

   Ad esempio, aggiungi:

   ```css
   .task .taskProperties .stepname{
       width: 25px;
       background: url(../images/stepname.png) no-repeat; /*-------- Or just reuse background image / image-sprite defined .task .taskProperties span of style.css---------------------*/
       background-position: 0px 0px; /*-------- Dummy values, need to be configured as per user background image / image-sprite ---------------------*/
   }
   ```

## Aggiunta di voci nel modello HTML {#adding-entry-in-the-html-template}

Infine, è necessario includere una voce nel pacchetto dev per ogni proprietà che si desidera aggiungere all&#39;attività. Per crearne uno, fare riferimento a Creazione  codice dell&#39;area di lavoro AEM Forms.

1. Copia `task.html`:

   * da: `/libs/ws/js/runtime/templates/`
   * a: `/apps/ws/js/runtime/templates/`

1. Aggiungete le nuove informazioni a `/apps/ws/js/runtime/templates/task.html`.

   Ad esempio, aggiungere sotto `div class="taskProperties"`:

   ```
   <span class="stepname" alt="<%= $.t('task.stepname.value')%>" title = '<%= $.t("task.stepname.tooltip",{stepName:stepName})%>'/>
   ```
