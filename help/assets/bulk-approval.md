---
title: Esaminare raccolte e risorse delle cartelle
description: Imposta i flussi di lavoro di revisione per le risorse all’interno di una cartella o di una raccolta e condividila con revisori o partner creativi per ottenere un feedback.
contentOwner: AG
feature: Collaboration, Collections
role: User
exl-id: 4c62e0cd-eaa5-456e-85f3-06f7a9f160f5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 23%

---

# Esaminare raccolte e risorse delle cartelle {#review-folder-assets-and-collections}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Imposta i flussi di lavoro di revisione per le risorse all’interno di una cartella o di una raccolta e condividila con revisori o partner creativi per ottenere un feedback.

Adobe Experience Manager Assets consente di impostare un flusso di lavoro di revisione ad hoc per le risorse all’interno di una cartella o di una raccolta e di condividerlo con revisori o partner creativi per ottenere un feedback.

È possibile associare il flusso di lavoro di revisione a un progetto o creare un&#39;attività di revisione indipendente.

Dopo aver condiviso le risorse, i revisori possono approvarle o rifiutarle. Le notifiche vengono inviate in varie fasi del flusso di lavoro per informare i destinatari in merito al completamento di varie attività. Ad esempio, quando si condivide una cartella o una raccolta, il revisore riceve una notifica relativa alla condivisione di una cartella o raccolta per la revisione.

Dopo che il revisore ha completato la revisione (approva o rifiuta le risorse), riceverai una notifica di completamento della revisione.

## Creazione di un&#39;attività di revisione per le cartelle {#creating-a-review-task-for-folders}

1. Dall’interfaccia utente Assets, seleziona la cartella per la quale desideri creare un’attività di revisione.
1. Dalla barra degli strumenti, tocca o fai clic sull’icona **[!UICONTROL Crea attività di revisione]** per aprire la pagina **[!UICONTROL Attività di revisione]**. Se l’icona non è visibile nella barra degli strumenti, tocca o fai clic su **[!UICONTROL More (Altro)]**, quindi seleziona l’icona.

   ![chlimage_1-403](assets/chlimage_1-403.png)

1. (Facoltativo) Dal **[!UICONTROL Progetto]** selezionare il progetto a cui si desidera associare l&#39;attività di revisione. Per impostazione predefinita, la **[!UICONTROL Nessuno]** è selezionata. Se non si desidera associare alcun progetto all&#39;attività di revisione, mantenere questa selezione.

   >[!NOTE]
   >
   >Solo i progetti per i quali disponi di autorizzazioni a livello di editor (o versioni successive) sono visibili nel **[!UICONTROL Progetti]** elenco.

1. Immettere un nome per l&#39;attività di revisione e selezionare un approvatore dal **[!UICONTROL Assegna a]** elenco.

   >[!NOTE]
   >
   >I membri/gruppi del progetto selezionato sono disponibili come approvatori nel **[!UICONTROL Assegna a]** elenco.

1. Immettere una descrizione, la priorità dell&#39;attività e la data di scadenza dell&#39;attività di revisione.

   ![task_details](assets/task_details.png)

1. Nella scheda Avanzate , immetti un’etichetta da utilizzare per creare l’URI.

   ![review_name](assets/review_name.png)

1. Tocca o fai clic su **[!UICONTROL Invia]**, quindi tocca o fai clic su **[!UICONTROL Fine]** per chiudere il messaggio di conferma. Una notifica per la nuova attività viene inviata al responsabile approvazione.
1. Accedi a [!DNL Experience Manager] Risorse come Approvatore e passa all’interfaccia utente Assets. Per approvare le risorse, tocca o fai clic sul pulsante **[!UICONTROL Notifiche]** quindi selezionare l&#39;attività di revisione dall&#39;elenco.

   ![notifica](assets/notification.png)

1. Nella pagina **[!UICONTROL Rivedi attività]**, esamina i dettagli dell’attività di revisione, quindi tocca o fai clic su **[!UICONTROL Review (Verifica)]**.
1. Nella pagina **[!UICONTROL Rivedi attività]**, seleziona le risorse, quindi tocca o fai clic sull’icona **[!UICONTROL Approva/Rifiuta]** per approvare o rifiutare, a seconda delle necessità.

   ![review_task](assets/review_task.png)

1. Tocca o fai clic sul pulsante **[!UICONTROL Completa]** dalla barra degli strumenti. Nella finestra di dialogo, immetti un commento e tocca o fai clic su  **[!UICONTROL Completa]** per confermare.
1. Passa all’interfaccia utente Assets e apri la cartella . Le icone dello stato di approvazione per le risorse vengono visualizzate nelle viste a schede e a elenco.

   **Vista a schede**

   ![chlimage_1-404](assets/chlimage_1-404.png)

   **Vista a elenco**

   ![review_status_listview](assets/review_status_listview.png)

## Creare un’attività di revisione per le raccolte {#creating-a-review-task-for-collections}

1. Nella pagina Raccolte selezionare la raccolta per la quale si desidera creare un&#39;attività di revisione.
1. Dalla barra degli strumenti, tocca o fai clic sull’icona **[!UICONTROL Crea attività di revisione]** per aprire la pagina **[!UICONTROL Attività di revisione]**. Se l’icona non è visibile nella barra degli strumenti, tocca o fai clic su **[!UICONTROL More (Altro)]**, quindi seleziona l’icona.

   ![chlimage_1-405](assets/chlimage_1-405.png)

1. (Facoltativo) Dal **[!UICONTROL Progetto]** selezionare il progetto a cui si desidera associare l&#39;attività di revisione. Per impostazione predefinita, la **[!UICONTROL Nessuno]** è selezionata. Se non si desidera associare alcun progetto all&#39;attività di revisione, mantenere questa selezione.

   >[!NOTE]
   >
   >Solo i progetti per i quali disponi di autorizzazioni a livello di editor (o versioni successive) sono visibili nel **[!UICONTROL Progetti]** elenco.

1. Immettere un nome per l&#39;attività di revisione e selezionare un approvatore dal **[!UICONTROL Assegna a]** elenco.

   >[!NOTE]
   >
   >I membri/gruppi del progetto selezionato sono disponibili come approvatori nel **[!UICONTROL Assegna a]** elenco.

1. Immettere una descrizione, la priorità dell&#39;attività e la data di scadenza dell&#39;attività di revisione.

   ![task_details-collection](assets/task_details-collection.png)

1. Tocca o fai clic su **[!UICONTROL Invia]**, quindi tocca o fai clic su **[!UICONTROL Fine]** per chiudere il messaggio di conferma. Una notifica per la nuova attività viene inviata al responsabile approvazione.
1. Accedi a [!DNL Experience Manager] Risorse come Approvatore e passa alla console Risorse . Per approvare le risorse, tocca o fai clic sul pulsante **[!UICONTROL Notifiche]** quindi selezionare l&#39;attività di revisione dall&#39;elenco.
1. Nella pagina **[!UICONTROL Rivedi attività]**, esamina i dettagli dell’attività di revisione, quindi tocca o fai clic su **[!UICONTROL Review (Verifica)]**.
1. Tutte le risorse nella raccolta sono visibili nella pagina di revisione. Seleziona le risorse e tocca o fai clic sul pulsante **[!UICONTROL Approva/Rifiuta]** per approvare o rifiutare le risorse, a seconda dei casi.

   ![review_task_collection](assets/review_task_collection.png)

1. Tocca o fai clic sul pulsante **[!UICONTROL Completa]** dalla barra degli strumenti. Nella finestra di dialogo, immetti un commento e tocca o fai clic su **[!UICONTROL Completa]** per confermare.
1. Passa alla console Raccolte e apri la raccolta. Le icone dello stato di approvazione per le risorse vengono visualizzate nelle viste a schede e a elenco.

   **Vista a schede**

   ![collection_reviewstatuscardview](assets/collection_reviewstatuscardview.png)

   **Vista a elenco**

   ![collection_reviewstatuslistview](assets/collection_reviewstatuslistview.png)
