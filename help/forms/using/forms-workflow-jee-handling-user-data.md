---
title: Flussi di lavoro JEE Forms | Gestione dei dati utente
seo-title: Forms JEE workflows | Handling user data
description: I flussi di lavoro JEE di AEM Forms forniscono strumenti per la progettazione, la creazione e la gestione dei processi aziendali. Scopri di più su come accedere ai dati utente ed eliminarli, identificare gli ID delle istanze del processo quando l’iniziatore del flusso di lavoro o il partecipante è noto, identificare gli ID delle istanze del processo quando i dati utente vengono memorizzati in variabili primitive, eliminare i dati utente dalle istanze del flusso di lavoro in base agli ID delle istanze del processo e lavorare con le attività orfane.
seo-description: AEM Forms JEE workflows provide tools to design, create, and manage business processes. Learn more on how to access and delete user data, identify process instance IDs when workflow initiator or participant is known, identify process instance IDs when user data is stored in primitive variables, purge user data from workflow instances based on process instance IDs, and work with orphan tasks.
uuid: 3b06ef19-d3c4-411e-9530-2c5d2159b559
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5632a8df-a827-4e38-beaa-18b61c2208a3
role: Admin
exl-id: 8cbace00-c354-4f37-a781-04cadd441419
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1461'
ht-degree: 0%

---

# Flussi di lavoro JEE Forms | Gestione dei dati utente {#forms-jee-workflows-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I flussi di lavoro JEE di AEM Forms forniscono strumenti per la progettazione, la creazione e la gestione dei processi aziendali. Un processo di flusso di lavoro consiste in una serie di passaggi che vengono eseguiti in un ordine specificato. Ogni passaggio esegue un’azione specifica, ad esempio l’assegnazione di un’attività a un utente o l’invio di un messaggio e-mail. Un processo può interagire con risorse, account utente e servizi e può essere attivato utilizzando uno dei seguenti metodi:

* Avvio di un processo da AEM Forms Workspace
* Utilizzo del servizio SOAP o RESTful
* Invio di un modulo adattivo
* Utilizzo della cartella controllata
* Utilizzo di e-mail

Per ulteriori informazioni sulla creazione del processo del flusso di lavoro JEE per AEM Forms, vedi [Guida di Workbench](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/pdf/WorkbenchHelp.pdf).

## Archiviazione dati e dati utente {#user-data-and-data-stores}

Quando un processo viene attivato e procede, acquisisce i dati relativi ai partecipanti al processo, i dati immessi dai partecipanti al modulo associato al processo e gli allegati aggiunti al modulo. I dati vengono memorizzati nel database del server JEE di AEM Forms e, se configurati, alcuni dati come gli allegati vengono memorizzati nella directory Global Document Storage (GDS). La directory GDS può essere configurata su un file system condiviso o su un database.

## Accedere ed eliminare i dati utente {#access-and-delete-user-data}

Quando un processo viene attivato, viene generato un ID univoco dell&#39;istanza del processo e viene generato un ID di chiamata di lunga durata, che viene associato all&#39;istanza del processo. Puoi accedere ed eliminare i dati per un&#39;istanza di processo in base all&#39;ID di chiamata di lunga durata. Puoi dedurre l’ID di chiamata di lunga durata di un’istanza di processo con il nome utente dell’iniziatore del processo o dei partecipanti al processo che hanno inviato le loro attività.

Tuttavia, non è possibile identificare l&#39;ID dell&#39;istanza di processo per un iniziatore nei seguenti scenari:

* **Processo attivato tramite una cartella controllata**: Impossibile identificare un&#39;istanza di processo utilizzando il proprio iniziatore se il processo viene attivato da una cartella controllata. In questo caso, le informazioni utente vengono codificate nei dati memorizzati.
* **Processo avviato dall&#39;istanza di pubblicazione AEM**: Tutte le istanze di processo attivate da AEM&#39;istanza di pubblicazione non acquisiscono informazioni sull&#39;iniziatore. Tuttavia, i dati utente possono essere acquisiti nel modulo associato al processo, memorizzato nelle variabili del flusso di lavoro.
* **Processo avviato tramite e-mail**: L’ID e-mail del mittente viene acquisito come proprietà in una colonna BLOB opaca del `tb_job_instance` tabella di database, che non può essere interrogata direttamente.

### Identificare gli ID delle istanze del processo quando l’iniziatore del flusso di lavoro o il partecipante è noto {#initiator-participant}

Esegui i seguenti passaggi per identificare gli ID delle istanze del processo per un iniziatore di flusso di lavoro o un partecipante:

1. Esegui il seguente comando nel database del server AEM Forms per recuperare l’ID principale per l’iniziatore del flusso di lavoro o il partecipante dal `edcprincipalentity` tabella del database.

   ```sql
   select id from edcprincipalentity where canonicalname='user_ID'
   ```

   La query restituisce l&#39;ID principale per il `user_ID`.

1. (**Per l’iniziatore del flusso di lavoro**) Esegui il comando seguente per recuperare tutte le attività associate all&#39;ID principale per l&#39;iniziatore dal `tb_task` tabella del database.

   ```sql
   select * from tb_task where start_task = 1 and create_user_id= 'initiator_principal_id'
   ```

   La query restituisce i task avviati dal `initiator`_ `principal_id`. Le attività sono di due tipi:

   * **Attività completate**: Queste attività sono state inviate e presentano un valore alfanumerico nel `process_instance_id` campo . Prendi nota di tutti gli ID delle istanze del processo per le attività inviate e continua con i passaggi.
   * **Attività avviate ma non completate**: Questi compiti sono iniziati ma non ancora inviati. Il valore nel `process_instance_id` il campo di queste attività è **0** (zero). In questo caso, prendi nota degli ID attività corrispondenti e vedi [Operazioni con le attività orfane](#orphan).

1. (**Per i partecipanti al flusso di lavoro**) Esegui il comando seguente per recuperare gli ID dell&#39;istanza del processo associati all&#39;ID principale del partecipante al processo per l&#39;iniziatore dal `tb_assignment` tabella del database.

   ```sql
   select distinct a.process_instance_id from tb_assignment a join tb_queue q on a.queue_id = q.id where q.workflow_user_id='participant_principal_id'
   ```

   La query restituisce gli ID istanza per tutti i processi associati al partecipante, compresi quelli in cui il partecipante non ha inviato alcuna attività.

   Prendi nota di tutti gli ID delle istanze del processo per le attività inviate e continua con i passaggi.

   Per le attività o i compiti orfani in cui `process_instance_id` è 0 (zero), prendi nota degli ID attività corrispondenti e vedi [Operazioni con le attività orfane](#orphan).

1. Segui le istruzioni in [Elimina i dati utente dalle istanze del flusso di lavoro in base agli ID delle istanze del processo](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge) per eliminare i dati utente per gli ID di istanze del processo identificati.

### Identificare gli ID delle istanze del processo quando i dati utente vengono memorizzati in variabili primitive {#primitive}

Un flusso di lavoro può essere progettato in modo tale che i dati utente vengano acquisiti in una variabile che viene memorizzata come BLOB nel database. In questi casi, puoi eseguire query sui dati utente solo se sono memorizzati in una delle seguenti variabili di tipo primitivo:

* **Stringa**: Contiene l&#39;ID utente direttamente o come sottostringa e può essere interrogato utilizzando SQL.
* **Numerico**: Contiene direttamente l’ID utente.
* **XML**: Contiene l’ID utente come sottostringa all’interno del testo memorizzato come colonne di testo nel database e può essere interrogato come stringhe.

Esegui i seguenti passaggi per determinare se un flusso di lavoro che memorizza dati in variabili di tipo primitivo contiene dati per l’utente:

1. Esegui il seguente comando del database:

   ```sql
   select database_table from omd_object_type where name='pt_<app_name>/<workflow_name>'
   ```

   La query restituisce un nome di tabella in `tb_<number>` formato per l&#39;applicazione specificata ( `app_name`) e flusso di lavoro ( `workflow_name`).

   >[!NOTE]
   >
   >Il valore del `name` può essere complessa se il flusso di lavoro è nidificato all’interno di sottocartelle all’interno dell’applicazione. Assicurati di specificare l’esatto percorso completo del flusso di lavoro, che puoi ottenere dal `omd_object_type` tabella del database.

1. Consulta la sezione `tb_<number>` schema tabella. La tabella contiene variabili che memorizzano i dati utente per il flusso di lavoro specificato. Le variabili nella tabella corrispondono alle variabili nel flusso di lavoro.

   Identifica e prendi nota della variabile che corrisponde alla variabile del flusso di lavoro contenente l’ID utente. Se la variabile identificata è di tipo primitivo, puoi eseguire una query per determinare le istanze del flusso di lavoro associate a un ID utente.

1. Esegui il seguente comando del database. In questo comando, la `user_var` è la variabile di tipo primitivo che contiene l’ID utente.

   ```sql
   select process_instance_id from <tb_name> where <user_var>=<user_ID>
   ```

   La query restituisce tutti gli ID di istanza del processo associati al `user_ID`.

1. Segui le istruzioni in [Elimina i dati utente dalle istanze del flusso di lavoro in base agli ID delle istanze del processo](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge) per eliminare i dati utente per gli ID di istanze del processo identificati.

### Elimina i dati utente dalle istanze del flusso di lavoro in base agli ID delle istanze del processo {#purge}

Dopo aver identificato gli ID di istanza del processo associati a un utente, procedi come segue per eliminare i dati utente dalle rispettive istanze del processo.

1. Esegui il seguente comando per recuperare l&#39;ID e lo stato di chiamata a lunga durata per un&#39;istanza di processo dal `tb_process_instance` tabella.

   ```sql
   select long_lived_invocation_id, status from tb_process_instance where id='process_instance_id'
   ```

   La query restituisce l&#39;ID e lo stato di chiamata a lunga durata per il valore specificato `process_instance_id`.

1. Crea un&#39;istanza del pubblico `ProcessManager` client ( `com.adobe.idp.workflow.client.ProcessManager`) utilizzando un `ServiceClientFactory` istanza con le impostazioni di connessione corrette.

   Per ulteriori informazioni, consulta Riferimento API Java per [Classe ProcessManager](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/com/adobe/idp/workflow/client/ProcessManager.html).

1. Controlla lo stato dell’istanza del flusso di lavoro. Se lo stato è diverso da 2 (COMPLETE) o 4 (TERMINATED), interrompi prima l&#39;istanza chiamando il seguente metodo:

   `ProcessManager.terminateProcess(<long_lived_invocation_id>)`.

1. Elimina l’istanza del flusso di lavoro chiamando il seguente metodo:

   `ProcessManager.purgeProcessInstance(<long_lived_invocation_id>)`

   La `purgeProcessInstance` elimina completamente tutti i dati per l&#39;ID di chiamata specificato dal database del server AEM Forms e da GDS, se configurato.

### Operazioni con le attività orfane {#orphan}

Le attività orfane sono le attività il cui processo di contenimento è stato avviato ma non ancora inviato. in questo caso, `process_instance_id` è **0** (zero). Pertanto, non è possibile tracciare i dati utente archiviati per le attività orfane utilizzando gli ID delle istanze del processo. Tuttavia, è possibile tracciarlo utilizzando l&#39;ID attività per un&#39;attività orfana. Puoi identificare gli ID delle attività dalla `tb_task` tabella per un utente come descritto in [Identificare gli ID delle istanze del processo quando l’iniziatore del flusso di lavoro o il partecipante è noto](/help/forms/using/forms-workflow-jee-handling-user-data.md#initiator-participant).

Una volta ottenuti gli ID attività, procedi come segue per eliminare i file e i dati associati con un’attività orfana da GDS e dal database.

1. Esegui il seguente comando sul database del server AEM Forms per recuperare gli ID per gli ID attività identificati.

   ```sql
   select id from tb_form_data where task_id=<task_id>
   ```

   La query restituisce un elenco di ID. Per ogni ID ( `fd_id`) restituita nei risultati, crea un elenco di stringhe ID sessione come segue:

   * _ `wfattach<task_id>`
   * `_wftask<fd_id>`
   * `_wftaskformid<fd_id>`

1. A seconda che il GDS punti a un file system o a un database, effettua una delle seguenti operazioni:

   1. **GDS nel file system**

      Nel file system GDS:

      1. Cerca i file con le seguenti stringhe ID sessione come estensioni:
      * `_wfattach<task_id>`
      * `_wftask<fd_id>`
      * `_wftaskformid<fd_id>`

         I file con queste estensioni sono i file marker. Vengono memorizzati con nomi file nel seguente formato:

         `<file_name_guid>.session<session_id_string>`
      1. Elimina tutti i file marker e altri file con il nome file esatto come `<file_name_guid>` dal file system.
   1. **GDS nel database**

      Esegui i seguenti comandi per ogni ID sessione:

      ```sql
      delete from tb_dm_chunk where documentid in (select documentid from tb_dm_session_reference where sessionid=<session_id>)
      delete from tb_dm_session_reference where sessionid=<session_id>
      delete from tb_dm_deletion where sessionid=<session_id>
      ```




1. Esegui i seguenti comandi per eliminare i dati per gli ID attività dal database del server AEM Forms:

   ```sql
   delete from tb_task_acl where task_id=<task_id>
   delete from tb_task_attachment where task_id=<task_id>
   delete from tb_form_data where task_id=<task_id>
   delete from tb_assignment where task_id=<task_id>
   delete from tb_task where id=<task_id>
   ```
