---
title: Configurare le operazioni asincrone in [!DNL Adobe Experience Manager].
description: Completate in modo asincrono alcune attività che richiedono risorse per ottimizzare le prestazioni in [!DNL Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: f6aa1ab2c7a0ddeda1504e95ce4bd57fe74a65fd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 22%

---


# Asynchronous operations {#asynchronous-operations}

Per ridurre l’impatto negativo sulle prestazioni, [!DNL Adobe Experience Manger Assets] elabora in modo asincrono alcune operazioni di risorse a lungo termine e che richiedono risorse. L&#39;elaborazione asincrona comporta l&#39;accodamento di più attività e la loro esecuzione in modo seriale, in base alla disponibilità di risorse di sistema. Alcune di queste operazioni sono:

* Eliminazione di numerose risorse.
* Spostamento di più di una risorsa o risorse con più riferimenti.
* Esportazione e importazione in massa dei metadati delle risorse.

Potete visualizzare lo stato delle attività asincrone dalla pagina Stato **[!UICONTROL processo]** asincrono.

>[!NOTE]
>
>Per impostazione predefinita, le [!DNL Assets] attività vengono eseguite in parallelo. If `N` is the number of CPU cores, `N/2` tasks can execute in parallel, by default. Per utilizzare le impostazioni personalizzate per la coda delle attività, modificare la configurazione della coda **[!UICONTROL predefinita dell&#39;operazione]** Async dalla console Web. Per ulteriori informazioni, consulta [Configurazione della coda](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitor the status of asynchronous operations {#monitoring-the-status-of-asynchronous-operations}

Whenever [!DNL Assets] processes an operation asynchronously, you receive a notification in your [!DNL Experience Manager] [Inbox](/help/sites-authoring/inbox.md) and via an email. Lo stato delle operazioni asincrone è consultabile in dettaglio alla pagina **[!UICONTROL Stato processo asincrono]**.

1. In the [!DNL Experience Manager] interface click **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.

1. Nella pagina **[!UICONTROL Stato processo asincrono]**, controlla i dettagli delle operazioni.

   ![Stato e dettagli delle operazioni asincrone](assets/job_status.png)

   Per verificare l&#39;avanzamento di un&#39;operazione, vedere la colonna **[!UICONTROL Stato]** . A seconda dell’avanzamento, viene visualizzato uno dei seguenti stati:

   * **[!UICONTROL Attivo]**: elaborazione dell’operazione in corso.
   * **[!UICONTROL Completato]**: operazione completata.
   * **[!UICONTROL Non riuscito]** o **[!UICONTROL Errore]**: impossibile elaborare l’operazione.
   * **[!UICONTROL Pianificato]**: l’elaborazione dell’operazione è pianificata per un momento successivo.

1. To stop an active operation, select it from the list and click **[!UICONTROL Stop]** ![stop icon](assets/do-not-localize/stop_icon.svg) from the toolbar.

1. To view extra details, for example description and logs, select the operation and click **[!UICONTROL Open]** ![open_icon](assets/do-not-localize/edit_icon.svg) from the toolbar. Viene visualizzata la pagina dei dettagli dell’attività.

   ![Dettagli di un’attività di importazione di metadati](assets/job_details.png)

1. Per eliminare un’operazione dall’elenco, seleziona **[!UICONTROL Elimina]** dalla barra degli strumenti. Per scaricare i dettagli in un file CSV, fai clic su **[!UICONTROL Scarica]**.

   >[!NOTE]
   >
   >Non è possibile eliminare un&#39;attività se il suo stato è attivo o in coda.

## Rimozione delle attività completate {#purge-completed-tasks}

[!DNL Experience Manager Assets] esegue un&#39;attività di eliminazione ogni giorno alle 0100 ore per eliminare le attività asincrone completate di oltre un giorno.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

È possibile modificare la pianificazione per l&#39;attività di eliminazione e la durata per la quale i dettagli delle attività completate vengono conservati prima di essere eliminati. È inoltre possibile configurare il numero massimo di attività completate per le quali i dettagli vengono conservati in qualsiasi momento.

1. Nell&#39; [!DNL Experience Manager] interfaccia fare clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > Console **** Web.
1. Aprite l&#39;attività **[!UICONTROL rimozione dei processi Async di Adobe CQ DAM pianificata]** .
1. Specificare la soglia del numero di giorni dopo i quali le attività completate vengono eliminate e il numero massimo di attività per le quali i dettagli vengono conservati nella cronologia. Salva le modifiche.

   ![Configurazione per pianificare l&#39;eliminazione delle attività asincrone](assets/purge_job.png)

## Configurare la soglia per le operazioni di eliminazione asincrone {#configure-thresholds-for-asynchronous-delete-operations}

Se il numero di risorse o cartelle da eliminare supera la soglia impostata, l’operazione di eliminazione viene eseguita in modo asincrono.

1. Nell&#39; [!DNL Experience Manager] interfaccia fare clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > Console **** Web.
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Delete Operation Job Processing]** configuration.
1. Nella casella **[!UICONTROL Soglia numero di risorse]** , specificate i numeri di soglia per eliminare in modo asincrono risorse, cartelle o riferimenti. Salva le modifiche.

   ![Impostare il limite di soglia per l&#39;attività di eliminazione delle risorse](assets/delete_threshold.png)

## Configurare la soglia per le operazioni di spostamento asincrone {#configure-thresholds-for-asynchronous-move-operations}

Se il numero di risorse, cartelle o riferimenti da spostare supera il numero di soglia impostato, l&#39;operazione di spostamento viene eseguita in modo asincrono.

1. Nell&#39; [!DNL Experience Manager] interfaccia, fare clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > Console **** Web.
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Move Operation Job Processing]** configuration.
1. Nella casella **[!UICONTROL Soglia numero di risorse/riferimenti]** , specificate i numeri di soglia per spostare in modo asincrono risorse, cartelle o riferimenti. Salva le modifiche.

   ![Impostare il limite di soglia per l&#39;attività di spostamento delle risorse](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Configura e-mail in  Experience Manager](/help/sites-administering/notification.md).
>* [Importare ed esportare in blocco i metadati delle risorse](/help/assets/metadata-import-export.md).

