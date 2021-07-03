---
title: Configura le operazioni asincrone in [!DNL Adobe Experience Manager].
description: Esegui in modo asincrono alcune attività ad alta intensità di risorse per ottimizzare le prestazioni in [!DNL Experience Manager Assets].
contentOwner: AG
feature: Gestione risorse
role: User
exl-id: 0abdfe87-d932-41dd-b1e6-9f5fa5b924fe
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 22%

---

# Operazioni asincrone {#asynchronous-operations}

Per ridurre l’impatto negativo sulle prestazioni, [!DNL Adobe Experience Manger Assets] elabora in modo asincrono alcune operazioni sulle risorse a lungo termine e ad alta intensità di risorse. L’elaborazione asincrona comporta l’accodamento di più attività e la loro esecuzione in modo seriale, in base alla disponibilità delle risorse di sistema. Alcune di queste operazioni sono:

* Eliminazione di numerose risorse.
* Spostamento di più di una risorsa o risorse con più riferimenti.
* Esportazione e importazione in blocco dei metadati delle risorse.

Puoi visualizzare lo stato delle attività asincrone dalla pagina **[!UICONTROL Stato processo asincrono]** .

>[!NOTE]
>
>Per impostazione predefinita, le attività [!DNL Assets] vengono eseguite in parallelo. Se `N` è il numero di core della CPU, le attività `N/2` possono essere eseguite in parallelo, per impostazione predefinita. Per utilizzare le impostazioni personalizzate per la coda attività, modifica la configurazione **[!UICONTROL Coda predefinita operazione asincrona]** dalla [!UICONTROL Console web]. Per ulteriori informazioni, consulta [Configurazione della coda](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitorare lo stato delle operazioni asincrone {#monitoring-the-status-of-asynchronous-operations}

Ogni volta che [!DNL Assets] elabora un&#39;operazione in modo asincrono, ricevi una notifica nel tuo [!DNL Experience Manager] [Inbox](/help/sites-authoring/inbox.md) e tramite e-mail. Lo stato delle operazioni asincrone è consultabile in dettaglio alla pagina **[!UICONTROL Stato processo asincrono]**.

1. Nell&#39;interfaccia [!DNL Experience Manager] fai clic su **[!UICONTROL Operazioni]** > **[!UICONTROL Processi]**.

1. Nella pagina **[!UICONTROL Stato processo asincrono]**, controlla i dettagli delle operazioni.

   ![Stato e dettagli delle operazioni asincrone](assets/job_status.png)

   Per verificare l’avanzamento di un’operazione, vedere la colonna **[!UICONTROL Stato]** . A seconda dell’avanzamento, viene visualizzato uno dei seguenti stati:

   * **[!UICONTROL Attivo]**: elaborazione dell’operazione in corso.
   * **[!UICONTROL Completato]**: operazione completata.
   * **[!UICONTROL Non riuscito]** o **[!UICONTROL Errore]**: impossibile elaborare l’operazione.
   * **[!UICONTROL Pianificato]**: l’elaborazione dell’operazione è pianificata per un momento successivo.

1. Per interrompere un&#39;operazione attiva, selezionala dall&#39;elenco e fai clic su **[!UICONTROL Stop]** ![icona di arresto](assets/do-not-localize/stop_icon.svg) nella barra degli strumenti.

1. Per visualizzare ulteriori dettagli, ad esempio la descrizione e i registri, seleziona l’operazione e fai clic su **[!UICONTROL Apri]** ![open_icon](assets/do-not-localize/edit_icon.svg) nella barra degli strumenti. Viene visualizzata la pagina dei dettagli dell’attività.

   ![Dettagli di un’attività di importazione dei metadati](assets/job_details.png)

1. Per eliminare un’operazione dall’elenco, seleziona **[!UICONTROL Elimina]** dalla barra degli strumenti. Per scaricare i dettagli in un file CSV, fai clic su **[!UICONTROL Scarica]**.

   >[!NOTE]
   >
   >Non è possibile eliminare un&#39;attività se il suo stato è attivo o in coda.

## Eliminare le attività completate {#purge-completed-tasks}

[!DNL Experience Manager Assets] esegue un’attività di eliminazione ogni giorno alle 01:00 per eliminare le attività asincrone completate di più di un giorno.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

È possibile modificare la pianificazione dell&#39;attività di eliminazione e la durata per la quale i dettagli delle attività completate vengono conservati prima di essere eliminate. Puoi anche configurare il numero massimo di attività completate per le quali i dettagli vengono conservati in qualsiasi momento.

1. Nell&#39;interfaccia [!DNL Experience Manager] fai clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > **[!UICONTROL Console web]**.
1. Apri l&#39;attività **[!UICONTROL Pulizia pianificata dei processi asincroni di Adobe CQ DAM]** .
1. Specificare il numero limite di giorni dopo i quali le attività completate vengono eliminate e il numero massimo di attività per le quali i dettagli vengono conservati nella cronologia. Salva le modifiche.

   ![Configurazione della rimozione pianificata delle attività asincrone](assets/purge_job.png)

## Configura la soglia per le operazioni di eliminazione asincrone {#configure-thresholds-for-asynchronous-delete-operations}

Se il numero di risorse o cartelle da eliminare supera la soglia impostata, l’operazione di eliminazione viene eseguita in modo asincrono.

1. Nell&#39;interfaccia [!DNL Experience Manager] fai clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > **[!UICONTROL Console web]**.
1. Dalla [!UICONTROL Console web], apri la configurazione **[!UICONTROL Processo di eliminazione asincrona]**.
1. Nella casella **[!UICONTROL Threshold number of assets]** (Soglia risorse), specifica i numeri di soglia per eliminare in modo asincrono risorse, cartelle o riferimenti. Salva le modifiche.

   ![Impostare il limite di soglia per l&#39;attività di eliminazione delle risorse](assets/delete_threshold.png)

## Configura la soglia per le operazioni di spostamento asincrone {#configure-thresholds-for-asynchronous-move-operations}

Se il numero di risorse, cartelle o riferimenti da spostare supera la soglia impostata, l’operazione di spostamento viene eseguita in modo asincrono.

1. Nell&#39;interfaccia [!DNL Experience Manager] fai clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > **[!UICONTROL Console web]**.
1. Dalla [!UICONTROL Console web], apri la configurazione **[!UICONTROL Elaborazione processo di spostamento asincrono]**.
1. Nella casella **[!UICONTROL Threshold number of assets/references]** (Soglia risorse/riferimenti), specifica i numeri di soglia per spostare in modo asincrono risorse, cartelle o riferimenti. Salva le modifiche.

   ![Impostare il limite di soglia per l&#39;attività di spostamento delle risorse](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Configura le e-mail in Experience Manager](/help/sites-administering/notification.md).
>* [Importare ed esportare in blocco i metadati delle risorse](/help/assets/metadata-import-export.md).

