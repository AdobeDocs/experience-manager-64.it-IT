---
title: Passaggi generici per  personalizzazione dell'area di lavoro AEM Forms
seo-title: Passaggi generici per  personalizzazione dell'area di lavoro AEM Forms
description: Come iniziare a personalizzare 'interfaccia utente dell'area di lavoro di AEM Forms.
seo-description: Come iniziare a personalizzare 'interfaccia utente dell'area di lavoro di AEM Forms.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 1%

---


# Passaggi generici per  personalizzazione dell&#39;area di lavoro AEM Forms {#generic-steps-for-aem-forms-workspace-customization}

I passaggi generici per eseguire eventuali personalizzazioni sono:

1. Accedete al CRXDE Lite accedendo a `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Create una cartella denominata `ws`in `/apps`, se non esiste. Fare clic su **[!UICONTROL Salva tutto]**.
1. Accedere a `/apps/ws` e passare alla scheda **[!UICONTROL Controllo accesso]**.
1. Nell&#39;elenco **[!UICONTROL Controllo accesso]**, fare clic su **[!UICONTROL +]** per aggiungere una nuova voce. Fare di nuovo clic su **[!UICONTROL +]**.
1. Cercare e selezionare l&#39;entità **[!UICONTROL PERM_WORKSPACE_USER]**.

   ![Selezionate l&#39;entità PERM_WORKSPACE_USER come parte dei passaggi generici per personalizzare l&#39;area di lavoro HTML](assets/perm_workspace_user.png)

1. Assegnare il privilegio `jcr:read` al Principal.
1. Fare clic su **[!UICONTROL Salva tutto]**.
1. Copiate i file `GET.jsp` e `html.jsp`dalla cartella `/libs/ws`alla cartella `/apps/ws`.
1. Copiate la cartella `/libs/ws/locales` nella cartella `/apps/ws`. Fare clic su **[!UICONTROL Salva tutto]**.
1. Aggiornare i riferimenti e i percorsi relativi nel file `GET.jsp`, come illustrato di seguito, quindi fare clic su **[!UICONTROL Salva tutto]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Effettuate le seguenti operazioni per le personalizzazioni CSS:

   1. Andate alla cartella `/apps/ws` e create una nuova cartella denominata `css`.
   1. Nella cartella `css`creare un nuovo file denominato `newStyle.css`.
   1. Apri `/apps/ws/html`.jsp e cambia da

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   a

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >Inserite la voce del file CSS definito dall&#39;utente dopo la voce newStyle.css, come illustrato sopra.

1. Nel file /apps/ws/html.jsp, modificare da

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   a

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Effettua le seguenti operazioni:

   1. Create una cartella denominata `js`in `/apps/ws`. Fare clic su **[!UICONTROL Salva tutto]**.
   1. Create una cartella denominata `libs`in `/apps/ws/js`. Fare clic su **[!UICONTROL Salva tutto]**.
   1. Create una cartella denominata `jqueryui`in `/apps/ws/js/libs`. Fare clic su **[!UICONTROL Salva tutto]**.
   1. Copiare `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` in `/apps/ws/js/libs/jqueryui`. Fare clic su **[!UICONTROL Salva tutto]**.

1. Effettuate le seguenti operazioni per le personalizzazioni HTML:

   1. In `/apps/ws/js`, create una cartella denominata `runtime`. Fare clic su **[!UICONTROL Salva tutto]**.
   1. In `/apps/ws/js/runtime`, create una cartella denominata `templates`. Fare clic su **[!UICONTROL Salva tutto]**.
   1. Copiare `/libs/ws/js/main.js` in `/apps/ws/js/main.js`.
   1. Copiate /libs/ws/js/registry.js in `/apps/ws/js/registry.js`.

1. Fare clic su **[!UICONTROL Salva tutto]**, cancellare la cache e aggiornare &#39;area di lavoro AEM Forms.

   Accedete all&#39;URL `https://[server]:[port]/lc/ws` ed effettuate l&#39;accesso con le credenziali di amministratore/password. Il browser reindirizza a `https://[server]:[port]/lc/apps/ws/index.html`.

