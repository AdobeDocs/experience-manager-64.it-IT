---
title: Personalizzazione delle schede per un’attività
seo-title: Customizing tabs for a task
description: Personalizzare i nomi delle schede delle attività, ad LiveCycle nell’area di lavoro di AEM Forms.
seo-description: How-to customize the names of the tabs for your tasks, in LiveCycle AEM Forms workspace.
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
exl-id: 42671435-e0f0-41db-af83-182b01742954
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 5%

---

# Personalizzazione delle schede per un’attività {#customizing-tabs-for-a-task}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile personalizzare i nomi delle schede per `Start Process` nel `Start Process` La vista Uber e `Task Details` nel `ToDo` Vista Uber.

1. Segui [Passaggi generici per la personalizzazione dell’area di lavoro AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Modifica il valore di `tabname`in `translation.json` file.

   Ad esempio, modifica `/apps/ws/locales/en-US/translation.json` per l&#39;inglese al seguente indirizzo:

   * Per le attività avviate nel processo di avvio, utilizza il seguente frammento tratto dal `"startprocess" : {}` blocco.

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Per le attività in Da fare, utilizzare il seguente frammento dal `"todo" : {}` blocco.

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Aggiungi la coppia chiave-valore corrispondente per tutte le lingue supportate.
