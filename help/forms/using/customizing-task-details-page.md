---
title: Personalizzazione della pagina dei dettagli dell’attività
seo-title: Customizing the task details page
description: Come personalizzare la pagina dei dettagli dell’attività nell’area di lavoro di AEM Forms per modificare le informazioni predefinite visualizzate su un’attività.
seo-description: How-to customize the task details page in AEM Forms workspace to modify the default information displayed about a task.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
exl-id: de97e6f7-25bf-462b-b67d-0d3fbd86a321
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# Personalizzazione della pagina dei dettagli dell’attività {#customizing-the-task-details-page}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La pagina dei dettagli dell&#39;attività contiene informazioni su un&#39;attività e sui relativi processi. Tuttavia, è possibile personalizzare la pagina dei dettagli dell’attività per aggiungere o eliminare informazioni.

È possibile aggiungere le seguenti informazioni alla pagina dei dettagli dell’attività:

* Informazioni disponibili nell’oggetto JSON di un’attività (sezione Task in [Descrizione dell’oggetto JSON dell’area di lavoro AEM Forms](/help/forms/using/html-workspace-json-object-description.md))
* Informazioni disponibili nell’oggetto JSON di un’istanza di processo (sezione dell’istanza di processo in [Descrizione dell’oggetto JSON dell’area di lavoro AEM Forms](/help/forms/using/html-workspace-json-object-description.md))

Per personalizzare la pagina dei dettagli dell’attività:

1. Segui [Passaggi generici per la personalizzazione dell’area di lavoro AEM Forms.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Per visualizzare eventuali informazioni aggiuntive, aggiungi le coppie chiave-valore corrispondenti al `translation.json` file a `todo`block > `details`block > `app`block > [ `required`blocco].

   La [ `required`blocco] fa riferimento ai blocchi disponibili, ad esempio il blocco attività per le informazioni sulle attività, il blocco del processo per le informazioni sul processo e il blocco delle attività in sospeso per le informazioni sulle attività in sospeso.

   Ad esempio, per aggiungere informazioni sulla selezione della route obbligatoria nella pagina dei dettagli dell&#39;attività, è possibile aggiungere la seguente coppia chiave-valore nel blocco attività:

   ```
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >Aggiungi le coppie chiave-valore corrispondenti per tutte le lingue supportate.

1. Copia `/libs/ws/js/runtime/templates/taskdetails.html` a `/apps/ws/js/runtime/templates/taskdetails.html`.

   Aggiungi le nuove informazioni a `/apps/ws/js/runtime/templates/taskdetails.html`. Ad esempio:

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. Apri /apps/ws/js/registry.js per la modifica.

   Ricerca e sostituzione `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` con `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Per personalizzare la pagina dei dettagli dell’attività con le attività create nella scheda **Avvia processo **dell’area di lavoro di AEM Forms, aggiungi le nuove informazioni a `/apps/ws/js/runtime/templates/startprocess.html`.
>
>Per aggiungere nuovi stili per le informazioni aggiunte nella pagina dei dettagli, modifica il file CSS utilizzando il *Modifiche all&#39;interfaccia utente* sezione [Personalizzazione di Workspace](/help/forms/using/changing-locale-user-interface.md).
