---
title: Gestione di applicazioni e attività Forms nella casella in entrata AEM
seo-title: Manage Forms applications and tasks in AEM Inbox
description: AEM casella in entrata consente di avviare flussi di lavoro incentrati su Forms inviando le applicazioni e gestendo le attività.
seo-description: AEM Inbox allows you to launch Forms-centric workflows through submitting applications and manage tasks.
uuid: 5173558a-542a-4130-8bb6-5ac555ecc507
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: document_services, publish
discoiquuid: c1515c58-7d9a-4a36-9390-f6d6b980b801
exl-id: 7076807a-40ad-4f3b-beb0-70c1577a8ee7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 2%

---

# Gestione di applicazioni e attività Forms nella casella in entrata AEM {#manage-forms-applications-and-tasks-in-aem-inbox}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Uno dei molti modi per avviare o attivare un flusso di lavoro incentrato su Forms è attraverso le applicazioni nella casella in entrata AEM. È necessario creare un’applicazione flusso di lavoro per rendere disponibile un flusso di lavoro Forms come applicazione nella casella in entrata. Per ulteriori informazioni sull&#39;applicazione del flusso di lavoro e su altri modi per avviare i flussi di lavoro Forms, vedi [Avvia un flusso di lavoro incentrato su Forms su OSGi](/help/forms/using/aem-forms-workflow.md#launch).

Inoltre, AEM Posta in arrivo consolida le notifiche e le attività da vari componenti AEM, inclusi i flussi di lavoro Forms. Quando viene attivato un flusso di lavoro dei moduli contenente un passaggio dell’attività Assegna, l’applicazione associata viene elencata come un’attività nella casella in entrata dell’assegnatario. Se l&#39;assegnatario è un gruppo, l&#39;attività viene visualizzata nella casella in entrata di tutti i membri del gruppo fino a quando l&#39;attività non viene attestata o delegata da un singolo utente.

L’interfaccia utente della casella in entrata fornisce viste elenco e calendario per visualizzare le attività. È inoltre possibile configurare le impostazioni di visualizzazione. È possibile filtrare le attività in base a vari parametri. Per ulteriori informazioni sulla visualizzazione e sui filtri, consulta [Casella in entrata](/help/sites-authoring/inbox.md).

In sintesi, la casella in entrata consente di creare una nuova applicazione e di gestire le attività assegnate.

>[!NOTE]
>
>Per poter utilizzare AEM casella in entrata, è necessario essere membro del gruppo utenti del flusso di lavoro.

## Creare un&#39;applicazione {#create-application}

1. Vai AEM casella in entrata in `https://[server]:[port]/aem/inbox`.
1. Nell’interfaccia utente della casella in entrata, tocca **[!UICONTROL Crea > Applicazione]**. Viene visualizzata la pagina Seleziona applicazione .
1. Seleziona un&#39;applicazione e fai clic su **[!UICONTROL Crea]**. Viene visualizzato il modulo adattivo associato all&#39;applicazione. Compila i moduli e tocca **[!UICONTROL Invia]**. Avvia il flusso di lavoro associato e crea un’attività nella casella in entrata dell’assegnatario.

## Gestione attività {#manage-tasks}

Quando si attiva un flusso di lavoro Forms e si è un assegnatario o parte del gruppo di assegnatari, un&#39;attività viene visualizzata nella casella in entrata. È possibile visualizzare i dettagli dell&#39;attività ed eseguire le azioni disponibili sull&#39;attività dall&#39;interno della casella in entrata.

### Attività di richiesta o delega {#claim-or-delegate-tasks}

Le attività assegnate a un gruppo vengono visualizzate nella casella in entrata di tutti i membri del gruppo. Qualsiasi membro del gruppo può reclamare tale attività o delegarla a un altro membro del gruppo. Per eseguire questa operazione:

1. Tocca per selezionare la miniatura dell’attività. Le opzioni per aprire o delegare l’attività vengono visualizzate nella parte superiore.

   ![attività di selezione](assets/select-task.png)

1. Effettua una delle operazioni seguenti:

   * Per delegare l’attività, tocca **[!UICONTROL Delega]**. Viene visualizzata la finestra di dialogo Delega elemento. Seleziona un utente, aggiungi facoltativamente un commento e tocca **[!UICONTROL OK]**.

   ![delegato](assets/delegate.png)

   * Per reclamare l’attività, tocca **[!UICONTROL Apri]**. Viene visualizzata la finestra di dialogo Assegna a se stesso. Tocca **[!UICONTROL Procedi]** per reclamare l&#39;attività. L’attività richiesta viene visualizzata insieme all’utente come assegnatario nella casella in entrata.

   ![rivendicazione](assets/claim.png)

### Visualizzare i dettagli ed eseguire azioni sulle attività {#view-details-and-perform-actions-on-tasks}

Quando si apre un&#39;attività, è possibile visualizzare i dettagli dell&#39;attività ed eseguire le azioni disponibili. Le azioni disponibili per un&#39;attività sono definite nella fase Assegna attività del flusso di lavoro Forms associato.

1. Tocca per selezionare la miniatura dell’attività. Le opzioni per aprire o delegare l’attività selezionata vengono visualizzate nella parte superiore.
1. Tocca **[!UICONTROL Apri]** per visualizzare i dettagli delle attività e intraprendere azioni. Viene visualizzata la visualizzazione dettagliata delle attività. In questa visualizzazione è possibile visualizzare i dettagli dell&#39;attività e intraprendere azioni sull&#39;attività.

   >[!NOTE]
   >
   >Se un&#39;attività viene assegnata a un gruppo, è necessario dichiararla in grado di aprirla in visualizzazione dettagliata.

![task-details](assets/task-details.png)

La visualizzazione dettagliata delle attività comprende le sezioni seguenti:

* Dettagli attività
* Modulo
* Dettagli flusso di lavoro
* Barra delle azioni

#### Dettagli attività {#task-details}

Nella sezione Dettagli attività vengono visualizzate informazioni sull’attività. Le informazioni visualizzate dipendono dalle impostazioni di configurazione del [Assegna passaggio attività](/help/sites-developing/workflows-step-ref.md) nel flusso di lavoro. Nell’esempio precedente vengono visualizzati la descrizione, lo stato, la data di inizio e il flusso di lavoro utilizzati per l’attività. Consente inoltre di allegare un file all&#39;attività.

#### Modulo {#form}

Nella scheda Modulo dell’area di contenuto principale sono visualizzati gli eventuali allegati a livello di modulo e di campo inviati.

#### Dettagli flusso di lavoro {#workflow-details}

La scheda Dettagli flusso di lavoro nella parte superiore mostra l’avanzamento dell’attività nelle varie fasi del flusso di lavoro. Mostra le fasi completate, correnti e in sospeso per l&#39;attività. Le fasi di un flusso di lavoro sono definite nella sezione [Assegna passaggio attività](/help/sites-developing/workflows-step-ref.md) del flusso di lavoro associato.

Inoltre, nella scheda viene visualizzata la cronologia delle attività per ogni fase completata del flusso di lavoro. Puoi toccare **[!UICONTROL Visualizza dettagli]** per una fase completata per conoscere i dettagli relativi a tale fase. Visualizza commenti, allegati di moduli e attività, stato, date di inizio e fine e così via sull&#39;attività.

![dettagli del flusso di lavoro](assets/workflow-details.png)

#### Barra delle azioni {#actions-toolbar}

La barra degli strumenti Azioni mostra tutte le opzioni disponibili per l’attività. Le azioni predefinite Salva, Reimposta e Delega sono le azioni predefinite, mentre le altre azioni disponibili sono configurate in [Assegna passaggio attività](/help/sites-developing/workflows-step-ref.md). Nell’esempio precedente, Approva e Rifiuta sono configurati nel flusso di lavoro.

Quando esegui un’azione sull’attività, continua a essere nel flusso di lavoro.

### Visualizza attività completate {#view-completed-tasks}

AEM casella in entrata visualizza solo le attività attive. Le attività completate non vengono visualizzate nell’elenco. Tuttavia, è possibile utilizzare i filtri Casella in entrata per filtrare le attività in base a diversi parametri, ad esempio tipo di attività, stato, date di inizio e fine e così via. Per visualizzare le attività completate:

1. Nella casella in entrata AEM toccare ![pannello laterale di attivazione/disattivazione1](assets/toggle-side-panel1.png) per aprire il selettore del filtro.
1. Tocca **[!UICONTROL Stato attività]** fisarmonica e selezionare **[!UICONTROL Completa]**. Vengono visualizzate tutte le attività completate.

   ![filter-1](assets/filter-1.png)

1. Tocca per selezionare un’attività e fai clic su **[!UICONTROL Apri]**.

Viene visualizzata l’attività per visualizzare il documento o il modulo adattivo associato all’attività. Per i moduli adattivi, visualizza il modulo adattivo di sola lettura o il relativo documento di record PDF configurato nella scheda Modulo/Documento della [Assegna passaggio flusso di lavoro attività](/help/sites-developing/workflows-step-ref.md).

Nella sezione dei dettagli dell&#39;attività sono visualizzate informazioni quali l&#39;azione eseguita, lo stato dell&#39;attività, la data di inizio e la data di fine.

![attività completata](assets/completed-task.png)

La **[!UICONTROL Dettagli flusso di lavoro]** mostra ogni passaggio del flusso di lavoro. Tocca **[!UICONTROL Visualizza dettagli]** per informazioni dettagliate.

![completato-task-workflow](assets/completed-task-workflow.png)
