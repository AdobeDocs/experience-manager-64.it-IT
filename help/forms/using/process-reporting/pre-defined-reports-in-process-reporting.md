---
title: Rapporti predefiniti in Process Reporting
seo-title: Pre-defined reports in Process Reporting
description: Query per AEM Forms sui dati del processo JEE per creare rapporti su processi a lungo termine, durata del processo e volume del flusso di lavoro
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 1%

---

# Rapporti predefiniti in Process Reporting {#pre-defined-reports-in-process-reporting}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Forms Process Reporting viene fornito con i seguenti *pronto all&#39;uso* rapporti:

* **[Processi a lunga esecuzione](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**: Report di tutti i processi AEM Forms che richiedono più di un tempo specificato per il completamento

* **[Grafico a barre della durata del processo](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**: Rapporto di un determinato processo AEM Forms per durata

* **[Volume del flusso di lavoro](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**: Rapporto delle istanze in esecuzione e completate del processo specificato per data

## Processi a lunga esecuzione {#long-running-processes}

Il rapporto Processi a esecuzione lunga visualizza i processi AEM Forms che hanno richiesto più di un tempo specificato per il completamento.

### Per eseguire un rapporto sul processo a lungo termine {#to-execute-a-long-running-process-report-br}

1. Per visualizzare l&#39;elenco dei report predefiniti in Reporting dei processi, nella sezione **Reporting dei processi** visualizzazione struttura, fare clic sul pulsante **Rapporti** nodo.
1. Fai clic sul pulsante **Processi a lunga esecuzione** nodo del report.

   ![long_run_node](assets/long_running_node.png)

   Quando selezioni un rapporto, la **Parametri del rapporto** viene visualizzato a destra della vista ad albero.

   ![pannello dei parametri del rapporto dei processi a lungo termine](assets/report_parameters_panel.png)

   Parametri:

   * **Durata**(*obbligatorio*): Specifica una durata e un’unità di tempo. Visualizza tutti i processi AEM Forms eseguiti per più della durata specificata.
   * **Avviato dopo** (*facoltativo*): Seleziona una data. Filtra il rapporto per visualizzare le istanze del processo iniziate dopo la data specificata.
   * **Avviato prima** (*facoltativo*): Seleziona una data. Filtrare il rapporto per visualizzare le istanze del processo avviate prima della data specificata.

1. Fai clic su **Vai** per eseguire il report.

   Il rapporto viene visualizzato nel **Rapporto** pannello a destra **Reporting dei processi** finestra.

   ![long_run_process](assets/long_running_processes.png)

   Utilizza le opzioni nell’angolo superiore destro del **Rapporto** per eseguire le seguenti operazioni sul report.

   * **Aggiorna**: Aggiorna il report con i dati più recenti presenti nell&#39;archivio
   * **Cambia colore della legenda**: Selezionare e modificare il colore della legenda del rapporto
   * **Esportazione in formato CSV**: Esporta e scarica i dati dal rapporto in un file separato da virgole

## Rapporto sulla durata del processo {#process-duration-report-br}

Il rapporto Durata processo visualizza il numero di istanze di un processo Forms per numero di giorni in cui ogni istanza è stata eseguita.

### Per eseguire un rapporto sulla durata del processo {#to-execute-a-process-duration-report-br}

1. Per visualizzare i report predefiniti in Reporting dei processi, nella sezione **Reporting dei processi** visualizzazione struttura, fare clic sul pulsante **Rapporti** nodo.
1. Fai clic sul pulsante **Durata dei processi** nodo del report.

   ![process_duration_node](assets/process_duration_node.png)

   Quando selezioni un rapporto, la **Parametri del rapporto** viene visualizzato a destra della vista ad albero.

   ![pannello dei parametri del rapporto dei processi a lungo termine](assets/process_duration_params.png)

   Parametri:

   * **Seleziona processo** (*obbligatorio*): Seleziona un processo AEM Forms.

1. Fai clic su **Vai** per eseguire il report.

   Il rapporto viene visualizzato nel **Rapporto** pannello a destra della finestra Reporting processi.

   ![process_duration_report](assets/process_duration_report.png)

   Utilizza le opzioni nell’angolo superiore destro del **Rapporto** per eseguire le seguenti operazioni sul report.

   * **Aggiorna**: Aggiorna il report con i dati più recenti presenti nell&#39;archivio
   * **Cambia colore della legenda**: Selezionare e modificare il colore della legenda del rapporto
   * **Esportazione in formato CSV**: Esporta e scarica i dati dal rapporto in un file separato da virgole

## Rapporto volume flusso di lavoro {#workflow-volume-report}

Il rapporto Volume flusso di lavoro visualizza il numero di istanze attualmente in esecuzione e completate di un processo AEM Forms per giorno di calendario.

### Per eseguire un rapporto sul volume di un flusso di lavoro {#to-execute-a-workflow-volume-report-br}

1. Per visualizzare i report predefiniti in Reporting dei processi, nella sezione **Reporting dei processi** visualizzazione struttura, fare clic sul pulsante **Rapporti** nodo.
1. Fai clic sul pulsante **Volume del flusso di lavoro** nodo del report.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Quando selezioni un rapporto, la **Parametri del rapporto** viene visualizzato a destra della vista ad albero.

   ![pannello dei parametri del rapporto dei processi a lungo termine](assets/workflow_volume_params.png)

   Parametri:

   * **Seleziona processo**(*obbligatorio*): Seleziona un processo AEM Forms.
   * **Avviato dopo** (*facoltativo*): Seleziona una data. Filtra il rapporto per visualizzare le istanze del processo iniziate dopo la data specificata.
   * **Avviato prima** (*facoltativo*): Seleziona una data. Filtra il rapporto per visualizzare le istanze del processo iniziate prima della data specificata.

1. Fai clic su **Vai** per eseguire il report.

   Il rapporto viene visualizzato nel **Rapporto** pannello a destra **Reporting dei processi** finestra.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Utilizza le opzioni nell’angolo superiore destro del **Rapporto** per eseguire le seguenti operazioni sul report.

   * **Aggiorna**: Aggiorna il report con i dati più recenti presenti nell&#39;archivio
   * **Cambia colore della legenda**: Selezionare e modificare il colore della legenda del rapporto
   * **Esportazione in formato CSV**: Esporta e scarica i dati dal rapporto in un file separato da virgole
