---
title: Aggiornamento del collegamento alla documentazione
seo-title: Updating the link to the documentation
description: Come aggiornare la destinazione del collegamento della Guida di Workspace nell’area di lavoro di AEM Forms per puntare al collegamento della documentazione personalizzato.
seo-description: How-to update the destination of Workspace Help link in AEM Forms workspace to point to your custom documentation link.
uuid: 64056d10-1451-44ed-8f25-81a21037dc75
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 788c427f-190f-4580-9efd-6a4c4a008837
exl-id: 68fe3f97-ded8-4223-b4b9-02704077e37e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 7%

---

# Aggiornamento del collegamento alla documentazione {#updating-the-link-to-the-documentation}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per accedere al contenuto della guida predefinito per l’area di lavoro di AEM Forms, seleziona **Aiuto > Aiuto di Workspace**. Indica la documentazione online sul sito web di Adobe. Tuttavia, puoi aggiornarlo per puntare a qualsiasi altro URL.

Considera i seguenti casi d’uso in cui puoi modificare l’URL predefinito della guida:

* Per fornire assistenza localizzata in una lingua a tua scelta.
* Per fornire contenuti di aiuto personalizzati per l&#39;area di lavoro personalizzata.

Per aggiornare l’URL della documentazione online, segui la [Passaggi generici di personalizzazione](/help/forms/using/generic-steps-html-workspace-customization.md) e quindi i seguenti passaggi.

1. Copia il `userinfo.html` file da `/libs/ws/js/runtime/templates` a `/apps/ws/js/runtime/templates`.
1. Cambia:

   ```
   <ul class="helpmenu">
     <li>            
       <a href="https://www.adobe.com/go/learn_aemforms_documentation_63" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

   a

   ```
   <ul class="helpmenu">
     <li>            
       <a href="<!--place new help url here-->" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

1. Effettua le seguenti operazioni:

   1. Apri /apps/ws/js/registry.js per la modifica.
   1. Ricerca e sostituzione `text!/lc/libs/ws/js/runtime/templates/userinfo.html` con `text!/lc/apps/ws/js/runtime/templates/userinfo.html`.
