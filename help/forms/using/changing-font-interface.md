---
title: Modifica del font nell'interfaccia
seo-title: Modifica del font nell'interfaccia
description: Come modificare selettivamente i font nell'interfaccia utente.
seo-description: Come modificare selettivamente i font nell'interfaccia utente.
uuid: d079f656-76f8-4908-9989-dde79e215eb2
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 487e3966-443a-408e-b5af-899fcba6fca6
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 1%

---


# Modifica del font nell&#39;interfaccia {#changing-the-font-on-the-interface}

Potete modificare il font visualizzato nell’area di lavoro  AEM Forms. I font utilizzati in una sezione specifica dell&#39;interfaccia utente sono definiti nella sezione corrispondente del foglio di stile. È possibile modificare i font nell&#39;interfaccia utente in modo selettivo.

Seguite i passaggi [Generici per  personalizzazione dell&#39;area di lavoro AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md) e, a seconda dei requisiti, seguite i passaggi per personalizzare CSS, HTML o entrambi.

1. Modificate o aggiungete la famiglia di font in uno stile esistente.
1. Modificate o aggiungete l&#39;agganciamento font-family per l&#39;elemento HTML.
1. Aggiungete uno stile e utilizzatelo per l&#39;elemento HTML.

Ad esempio, per modificare il font del testo di ancoraggio della barra di navigazione superiore in Courier New, effettuate le seguenti operazioni:

1. Accedete al CRXDE Lite accedendo a `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Effettua una delle operazioni seguenti:

   1. Per modificare la famiglia di font in uno stile esistente, aggiungete quanto segue nel file newStyle.css in /apps/ws/css.

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. Per aggiungere la famiglia di font in linea per l&#39;elemento HTML, copiate il file `/libs/ws/js/runtime/templates/appnavigation.html` in `/apps/ws/js/runtime/templates/appnavigation.html`.

      Aggiornate il file /apps/ws/js/runtime/templates/appnavigation.html come segue:

      ```
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      Aprite il file /apps/ws/js/registry.js per la modifica e sostituite `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` con `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. Per aggiungere uno stile che definisca la famiglia di font, aggiungete quanto segue nel file newStyle.css in /apps/ws/css.

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      Per aggiungere la famiglia di font in linea per l&#39;elemento HTML, aggiungete quanto segue nel file appnavigation.html in /apps/ws/js/runtime/templates.

      ```css
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. Riavviate l’area di lavoro e cancellate la cache del browser affinché le modifiche siano visibili.

![change_font_](assets/change_font_before.png)
**beforeFigure:Barra di navigazione** *principale prima della personalizzazione dei font*

![change_font_](assets/change_font_after.png)
**afterFigure:Barra di navigazione** *principale dopo la personalizzazione dei font della prima scheda*
