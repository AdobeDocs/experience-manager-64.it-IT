---
title: Configurare le operazioni asincrone in [!DNL Adobe Experience Manager].
description: Completate in modo asincrono alcune attività che richiedono molte risorse per ottimizzare le prestazioni in [!DNL Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: f6aa1ab2c7a0ddeda1504e95ce4bd57fe74a65fd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 22%

---


# Operazioni asincrone {#asynchronous-operations}

Per ridurre l&#39;impatto negativo sulle prestazioni, [!DNL Adobe Experience Manger Assets] elabora in modo asincrono alcune operazioni di risorse a lungo termine e che richiedono molte risorse. L&#39;elaborazione asincrona comporta l&#39;accodamento di più attività e la loro esecuzione in modo seriale, in base alla disponibilità di risorse di sistema. Alcune di queste operazioni sono:

* Eliminazione di numerose risorse.
* Spostamento di più di una risorsa o risorse con più riferimenti.
* Esportazione e importazione in massa dei metadati delle risorse.

È possibile visualizzare lo stato delle attività asincrone dalla pagina **[!UICONTROL Stato processo asincrono]**.

>[!NOTE]
>
>Per impostazione predefinita, le attività [!DNL Assets] vengono eseguite in parallelo. Se `N` è il numero di core CPU, per impostazione predefinita le attività `N/2` possono essere eseguite in parallelo. Per utilizzare le impostazioni personalizzate per la coda delle attività, modificare la configurazione **[!UICONTROL Coda predefinita operazione asincrona]** dalla [!UICONTROL Console Web]. Per ulteriori informazioni, consulta [Configurazione della coda](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitorare lo stato delle operazioni asincrone {#monitoring-the-status-of-asynchronous-operations}

Ogni volta che [!DNL Assets] elabora un&#39;operazione in modo asincrono, si riceve una notifica nella [!DNL Experience Manager] [Inbox](/help/sites-authoring/inbox.md) e tramite e-mail. Lo stato delle operazioni asincrone è consultabile in dettaglio alla pagina **[!UICONTROL Stato processo asincrono]**.

1. Nell&#39;interfaccia [!DNL Experience Manager] fare clic su **[!UICONTROL Operazioni]** > **[!UICONTROL Processi]**.

1. Nella pagina **[!UICONTROL Stato processo asincrono]**, controlla i dettagli delle operazioni.

   ![Stato e dettagli delle operazioni asincrone](assets/job_status.png)

   Per verificare l&#39;avanzamento di un&#39;operazione, vedere la colonna **[!UICONTROL Stato]**. A seconda dell’avanzamento, viene visualizzato uno dei seguenti stati:

   * **[!UICONTROL Attivo]**: elaborazione dell’operazione in corso.
   * **[!UICONTROL Completato]**: operazione completata.
   * **[!UICONTROL Non riuscito]** o **[!UICONTROL Errore]**: impossibile elaborare l’operazione.
   * **[!UICONTROL Pianificato]**: l’elaborazione dell’operazione è pianificata per un momento successivo.

1. Per interrompere un&#39;operazione attiva, selezionarla dall&#39;elenco e fare clic su **[!UICONTROL Stop]** ![icona di arresto](assets/do-not-localize/stop_icon.svg) nella barra degli strumenti.

1. Per visualizzare ulteriori dettagli, ad esempio descrizione e registri, selezionare l&#39;operazione e fare clic su **[!UICONTROL Apri]** ![open_icon](assets/do-not-localize/edit_icon.svg) dalla barra degli strumenti. Viene visualizzata la pagina dei dettagli dell’attività.

   ![Dettagli di un’attività di importazione di metadati](assets/job_details.png)

1. Per eliminare un’operazione dall’elenco, seleziona **[!UICONTROL Elimina]** dalla barra degli strumenti. Per scaricare i dettagli in un file CSV, fai clic su **[!UICONTROL Scarica]**.

   >[!NOTE]
   >
   >Non è possibile eliminare un&#39;attività se il suo stato è attivo o in coda.

## Elimina le attività completate {#purge-completed-tasks}

[!DNL Experience Manager Assets] esegue un&#39;attività di eliminazione ogni giorno alle 0100 ore per eliminare le attività asincrone completate di oltre un giorno.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

È possibile modificare la pianificazione per l&#39;attività di eliminazione e la durata per la quale i dettagli delle attività completate vengono conservati prima di essere eliminati. È inoltre possibile configurare il numero massimo di attività completate per le quali i dettagli vengono conservati in qualsiasi momento.

1. Nell&#39;interfaccia [!DNL Experience Manager] fare clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > **[!UICONTROL Console Web]**.
1. Apri l&#39;attività **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]**.
1. Specificare la soglia del numero di giorni dopo i quali le attività completate vengono eliminate e il numero massimo di attività per le quali i dettagli vengono conservati nella cronologia. Salva le modifiche.

   ![Configurazione per pianificare l&#39;eliminazione delle attività asincrone](assets/purge_job.png)

## Configurare la soglia per le operazioni di eliminazione asincrone {#configure-thresholds-for-asynchronous-delete-operations}

Se il numero di risorse o cartelle da eliminare supera la soglia impostata, l’operazione di eliminazione viene eseguita in modo asincrono.

1. Nell&#39;interfaccia [!DNL Experience Manager] fare clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > **[!UICONTROL Console Web]**.
1. Dalla [!UICONTROL Console Web], aprire la configurazione **[!UICONTROL Processo operazione eliminazione asincrona]**.
1. Nella casella **[!UICONTROL Numero di risorse]**, specificate i numeri di soglia per eliminare in modo asincrono risorse, cartelle o riferimenti. Salva le modifiche.

   ![Impostare il limite di soglia per l&#39;attività di eliminazione delle risorse](assets/delete_threshold.png)

## Configurare la soglia per le operazioni di spostamento asincrone {#configure-thresholds-for-asynchronous-move-operations}

Se il numero di risorse, cartelle o riferimenti da spostare supera il numero di soglia impostato, l&#39;operazione di spostamento viene eseguita in modo asincrono.

1. Nell&#39;interfaccia [!DNL Experience Manager], fare clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > **[!UICONTROL Console Web]**.
1. Dalla [!UICONTROL Console Web], aprire la configurazione **[!UICONTROL Processo operazione di spostamento asincrono]**.
1. Nella casella **[!UICONTROL Numero di risorse/riferimenti di soglia]**, specificate i numeri di soglia per spostare in modo asincrono risorse, cartelle o riferimenti. Salva le modifiche.

   ![Impostare il limite di soglia per l&#39;attività di spostamento delle risorse](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Configura e-mail in  Experience Manager](/help/sites-administering/notification.md).
>* [Importare ed esportare in blocco i metadati delle risorse](/help/assets/metadata-import-export.md).

