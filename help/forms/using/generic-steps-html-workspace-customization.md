---
title: Passaggi generici per la personalizzazione dell’area di lavoro AEM Forms
seo-title: Generic steps for AEM Forms workspace customization
description: Come iniziare a personalizzare l’interfaccia utente dell’area di lavoro di AEM Forms.
seo-description: How to get started customizing AEM Forms workspace user interface.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
exl-id: 2c0dab68-d77e-46fb-832d-90edea510750
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 4%

---

# Passaggi generici per la personalizzazione dell’area di lavoro AEM Forms {#generic-steps-for-aem-forms-workspace-customization}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I passaggi generici per eseguire eventuali personalizzazioni sono i seguenti:

1. Accedi a CRXDE Lite accedendo a `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Crea una cartella denominata `ws`a `/apps`, se non esiste. Fai clic su **[!UICONTROL Salva tutto]**.
1. Sfoglia per `/apps/ws`e naviga fino al **[!UICONTROL Controllo degli accessi]** scheda .
1. In **[!UICONTROL Controllo degli accessi]** elenco, fai clic su **[!UICONTROL +]** per aggiungere una nuova voce. Fai clic su **[!UICONTROL +]** di nuovo.
1. Cerca e seleziona la **[!UICONTROL PERM_WORKSPACE_USER]** Principale

   ![Selezionare l&#39;entità PERM_WORKSPACE_USER come parte dei passaggi generici per personalizzare HTML Workspace](assets/perm_workspace_user.png)

1. Dare `jcr:read` privilegio al Principale.
1. Fai clic su **[!UICONTROL Salva tutto]**.
1. Copia il `GET.jsp` e `html.jsp`file dal `/libs/ws`nella cartella `/apps/ws` cartella.
1. Copia il `/libs/ws/locales` nella cartella `/apps/ws` cartella. Fai clic su **[!UICONTROL Salva tutto]**.
1. Aggiorna i riferimenti e i percorsi relativi nel `GET.jsp` come mostrato di seguito, quindi fai clic su **[!UICONTROL Salva tutto]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Per le personalizzazioni CSS, procedi come segue:

   1. Passa a `/apps/ws` e crea una nuova cartella denominata `css`.
   1. In `css`cartella, creare un nuovo file denominato `newStyle.css`.
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
   >Posiziona la voce del file CSS definito dall’utente dopo la voce newStyle.css, come mostrato sopra.

1. Nel file /apps/ws/html.jsp, cambia da

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   a

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Effettua le seguenti operazioni:

   1. Crea una cartella denominata `js`a `/apps/ws`. Fai clic su **[!UICONTROL Salva tutto]**.
   1. Crea una cartella denominata `libs`a `/apps/ws/js`. Fai clic su **[!UICONTROL Salva tutto]**.
   1. Crea una cartella denominata `jqueryui`a `/apps/ws/js/libs`. Fai clic su **[!UICONTROL Salva tutto]**.
   1. Copia `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` a `/apps/ws/js/libs/jqueryui`. Fai clic su **[!UICONTROL Salva tutto]**.

1. Effettua le seguenti operazioni per le personalizzazioni di HTML:

   1. Sotto `/apps/ws/js`, crea una cartella denominata `runtime`. Fai clic su **[!UICONTROL Salva tutto]**.
   1. Sotto `/apps/ws/js/runtime`, crea una cartella denominata `templates`. Fai clic su **[!UICONTROL Salva tutto]**.
   1. Copia `/libs/ws/js/main.js` a `/apps/ws/js/main.js`.
   1. Copia /libs/ws/js/registry.js in `/apps/ws/js/registry.js`.

1. Fai clic su **[!UICONTROL Salva tutto]**, cancella la cache e aggiorna l’area di lavoro AEM Forms.

   Accedere all’URL `https://[server]:[port]/lc/ws` e accedi con le credenziali di amministratore/password. Il browser reindirizza a `https://[server]:[port]/lc/apps/ws/index.html`.
