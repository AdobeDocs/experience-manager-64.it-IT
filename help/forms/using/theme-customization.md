---
title: Personalizzazione del tema
seo-title: Theme Customization
description: Come personalizzare il tema della tua app AEM Forms.
seo-description: How to customize the theme of your AEM Forms app.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: fb1e0bec-c943-4468-920d-8ef360a01365
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 3%

---

# Personalizzazione del tema {#theme-customization}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi personalizzare il codice HTML e il file CSS per fornire all’app AEM Forms un aspetto e un aspetto specifici per l’organizzazione. Ad esempio, è possibile modificare il colore e l&#39;altezza dello sfondo delle attività o dei punti iniziali. L&#39;esempio seguente fornisce istruzioni per la modifica:

* visualizza le istruzioni al posto della descrizione
* numero di percorsi di visualizzazione
* colore sfumatura sfondo

## Passaggi {#steps}

1. Apri il progetto.

   * Per iOS, apri `Capture.xcodeproj` in Xcode
   * Per Android, apri il progetto Android in Eclipse.
   * Per Windows, apri `MWSWindows.sln` in Visual Studio.

1. Passa alla cartella dei modelli.

   * In Xcode, passa alla **Cattura > www > wsmobile > js > runtime > modelli** cartella.
   * In Eclipse, passa alla **risorse > www > wsmobile > js > runtime > modelli** cartella.
   * In Visual Studio, passare alla **MWSWindows > www > wsmobile > js > runtime > modelli** cartella.

1. Apri `template.html` file da modificare.
1. Individua la stringa seguente:

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else 
   ```

   Sostituisci con `<%`.

1. Individua il seguente codice nel `template.html` file:

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Commenta la riga seguente e salva il file.

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Passa alla cartella css .

   * In Xcode, accedi a **Cattura > www > wsmobile > css**.
   * In Eclipse, passa a **risorse > www > wsmobile > css**.
   * In Visual Studio, passare a **MWSWindows > www > wsmobile > css**.

1. Apri `_style.css` file da modificare.
1. Per l&#39;immagine di sfondo, modifica `#323232` a `#fff`.
1. Salva le modifiche e chiudi `_style.css` file.
1. Apri l’app AEM Forms.

   L’app AEM Forms ora visualizza le istruzioni anziché la descrizione.
