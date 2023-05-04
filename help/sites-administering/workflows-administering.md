---
title: Amministrazione delle istanze dei flussi di lavoro
seo-title: Administering Workflow Instances
description: Scopri come amministrare le istanze dei flussi di lavoro.
seo-description: Lear how to administer Workflow Instances.
uuid: 81e53ef5-fe62-4ed4-b2d4-132aa986d5aa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: d9c96e7f-9416-48e1-a6af-47384f7bee92
exl-id: 70d4117b-5e49-46e4-a0b8-f56cf985536e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 80%

---

# Amministrazione delle istanze dei flussi di lavoro{#administering-workflow-instances}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La console Flusso di lavoro fornisce diversi strumenti per l’amministrazione delle istanze del flusso di lavoro, in modo che vengano eseguite come previsto.

>[!NOTE]
>
>La [Console JMX](/help/sites-administering/jmx-console.md#workflow-maintenance) fornisce ulteriori operazioni di manutenzione del flusso di lavoro.

Sono disponibili diverse console per l’amministrazione dei flussi di lavoro. Utilizza la [navigazione globale](/help/sites-authoring/basic-handling.md#global-navigation) per aprire il riquadro **Strumenti**, quindi selezionare **Flusso di lavoro**:

* **Modelli**: gestire le definizioni dei flussi di lavoro
* **Istanze**: visualizzazione e gestione delle istanze di flussi di lavoro in esecuzione
* **Moduli di avvio**: gestire le modalità di avvio dei flussi di lavoro
* **Archiviazione**: visualizzazione della cronologia dei flussi di lavoro completati con successo
* **Errori**: visualizzazione della cronologia dei flussi di lavoro completati con errori

## Monitoraggio dello stato delle istanze del flusso di lavoro {#monitoring-the-status-of-workflow-instances}

1. Tramite navigazione, seleziona **Strumenti**, quindi **Flusso di lavoro**.
1. Seleziona **Istanze** per visualizzare l’elenco delle istanze del flusso di lavoro attualmente in corso.

   ![wf-96](assets/wf-96.png)

1. Seleziona un elemento specifico, quindi **Cronologia elementi aperti** per ulteriori dettagli:

   ![wf-97](assets/wf-97.png)

## Sospensione, Ripresa e Chiusura di un’istanza di flusso di lavoro {#suspending-resuming-and-terminating-a-workflow-instance}

1. Tramite navigazione, seleziona **Strumenti**, quindi **Flusso di lavoro**.
1. Seleziona **Istanze** per visualizzare l’elenco delle istanze del flusso di lavoro attualmente in corso.

   ![wf-96-1](assets/wf-96-1.png)

1. Seleziona un elemento specifico, quindi utilizza **Termina**, **Sospendi** oppure **Riprendi**, a seconda del caso; conferma e/o ulteriori dettagli richiesti:

   ![wf-97-1](assets/wf-97-1.png)

## Visualizzazione dei flussi di lavoro archiviati {#viewing-archived-workflows}

1. Tramite navigazione, seleziona **Strumenti**, quindi **Flusso di lavoro**.
1. Seleziona **Archivio** per visualizzare l’elenco delle istanze del flusso di lavoro completate correttamente.

   ![wf-98](assets/wf-98.png)

   >[!NOTE]
   >
   >Lo stato di interruzione viene considerato come una terminazione corretta in quanto si verifica in seguito a un’azione dell’utente; ad esempio:
   >
   >* utilizzo dell’azione **Termina**
   >* quando una pagina, soggetta a un flusso di lavoro, viene eliminata (forzatamente), il flusso di lavoro viene terminato


1. Seleziona un elemento specifico, quindi **Cronologia elementi aperti** per ulteriori dettagli:

   ![wf-99](assets/wf-99.png)

## Correzione degli errori di un&#39;istanza del flusso di lavoro {#fixing-workflow-instance-failures}

Quando un flusso di lavoro non riesce, AEM mette a disposizione la console **Errori** per indagare e intraprendere azioni appropriate una volta gestita la causa originale:

* **Dettagli errore**
Apre una finestra per visualizzare 
**Messaggio di errore**, **Passaggio** e **Stack errori**.

* **Cronologia elementi aperti**
Mostra i dettagli della cronologia del flusso di lavoro.

* **Ritenta passaggio** Esegue nuovamente lo script del passaggio dell’istanza del componente. Utilizzare il comando Riprova passaggio dopo aver risolto la causa dell&#39;errore originale. Ad esempio, prova a ripetere il passaggio dopo aver corretto un bug nello script eseguito dal passaggio del processo.
* **Termina** Termina il flusso di lavoro se l’errore ha causato una situazione irreprensibile per il flusso di lavoro. Ad esempio, il flusso di lavoro può basarsi su condizioni ambientali quali le informazioni nell’archivio che non sono più valide per l’istanza del flusso di lavoro.
* **Termina e riprova** Simile a **Termina** tranne per il fatto che una nuova istanza di flusso di lavoro viene avviata utilizzando il payload, il titolo e la descrizione originali.

Per approfondire gli errori, quindi riprendere o terminare il flusso di lavoro in seguito, utilizza i seguenti passaggi:

1. Tramite navigazione, seleziona **Strumenti**, quindi **Flusso di lavoro**.
1. Seleziona **Errori** per visualizzare l’elenco delle istanze del flusso di lavoro che non sono state completate correttamente.
1. Seleziona un elemento specifico, quindi l’azione appropriata:

   ![wf-47](assets/wf-47.png)

## Rimozione regolare delle istanze del flusso di lavoro {#regular-purging-of-workflow-instances}

Minimizzare il numero di istanze del flusso di lavoro aumenta le prestazioni del motore del flusso di lavoro, in modo da poter eliminare regolarmente dall’archivio le istanze del flusso di lavoro completate o in esecuzione.

Configura **Configurazione di eliminazione del flusso di lavoro di Adobe Granite** per eliminare le istanze del flusso di lavoro in base alla loro età e al loro stato. È inoltre possibile eliminare le istanze del flusso di lavoro di tutti i modelli o di un modello specifico.

Puoi anche creare più configurazioni del servizio per eliminare le istanze del flusso di lavoro che soddisfano criteri diversi. Ad esempio, crea una configurazione che elimina le istanze di un particolare modello di flusso di lavoro quando restano in esecuzione per molto più tempo del tempo previsto. Crea un’altra configurazione che elimina tutti i flussi di lavoro completati dopo un certo numero di giorni per ridurre al minimo le dimensioni dell’archivio.

Per configurare il servizio, puoi utilizzare la funzione [Console web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) o [aggiungi una configurazione OSGi all’archivio](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository). Nella tabella seguente sono descritte le proprietà necessarie per entrambi i metodi.

>[!NOTE]
>
>Per aggiungere la configurazione all’archivio, il PID del servizio è:
>
>`com.adobe.granite.workflow.purge.Scheduler`
>
>Poiché si tratta di un servizio di fabbrica, il nome del nodo `sling:OsgiConfig` richiede un suffisso di identificatore, ad esempio:
>
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

<table> 
 <tbody> 
  <tr> 
   <th>Nome proprietà (console Web)</th> 
   <th>Nome proprietà OSGi</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td>Nome processo</td> 
   <td>scheduledpurge.name</td> 
   <td>Nome descrittivo per l’eliminazione pianificata.</td> 
  </tr> 
  <tr> 
   <td>Stato flusso di lavoro</td> 
   <td>scheduledpurge.workflowStatus</td> 
   <td><p>Stato delle istanze del flusso di lavoro da eliminare. I seguenti valori sono validi:</p> 
    <ul> 
     <li>COMPLETATO: le istanze del flusso di lavoro completate vengono eliminate.</li> 
     <li>IN ESECUZIONE: le istanze del flusso di lavoro in esecuzione vengono eliminate.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Modelli da eliminare</td> 
   <td>scheduledpurge.modelIds</td> 
   <td><p>ID dei modelli di flusso di lavoro da eliminare. L’ID è il percorso del nodo del modello, ad esempio:<br /> /conf/global/settings/workflow/models/dam/update_asset/jcr:content/model<br /> Non specificare alcun valore per eliminare le istanze di tutti i modelli di flusso di lavoro.</p> <p>Per specificare più modelli, fai clic sul pulsante + nella console Web. </p> </td> 
  </tr> 
  <tr> 
   <td>Età del flusso di lavoro</td> 
   <td>scheduledpurge.daysold</td> 
   <td>Età in giorni delle istanze del flusso di lavoro da eliminare.</td> 
  </tr> 
 </tbody> 
</table>

## Impostazione della dimensione massima della casella in entrata {#setting-the-maximum-size-of-the-inbox}

Puoi impostare la dimensione massima della casella in entrata configurando la **Servizio flusso di lavoro di Adobe Granite**, utilizzando [Console web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) o [aggiungi una configurazione OSGi all’archivio](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository). Nella tabella seguente viene descritta la proprietà configurata per entrambi i metodi.

>[!NOTE]
>
>Per aggiungere la configurazione all’archivio, il PID del servizio è:
>
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Nome proprietà (console Web) | Nome proprietà OSGi |
|---|---|
| Dimensione massima query casella in entrata | granite.workflow.inboxQuerySize |
