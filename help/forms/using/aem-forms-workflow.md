---
title: Flusso di lavoro Forms basato su OSGi
seo-title: Creazione rapida di processi basati su moduli adattivi, automazione delle operazioni di document services e utilizzo  Adobe Sign con flussi di lavoro AEM
description: Utilizzare  flusso di lavoro AEM Forms per automatizzare e creare rapidamente revisioni e approvazioni, per avviare Document Services (ad esempio, per convertire un documento PDF in un altro formato), per integrare  flusso di lavoro delle firme Adobe Sign e altro ancora.
seo-description: Utilizzare  flusso di lavoro AEM Forms per automatizzare e creare rapidamente revisioni e approvazioni, per avviare Document Services (ad esempio, per convertire un documento PDF in un altro formato), per integrare  flusso di lavoro delle firme Adobe Sign e altro ancora.
uuid: 46be7ec6-d5cc-498a-9484-e66a29527064
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services, publish
discoiquuid: f8df5fa3-3843-4110-a46d-9a524d2657cd
noindex: true
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '2916'
ht-degree: 1%

---


# Flusso di lavoro Forms incentrato su OSGi {#forms-centric-workflow-on-osgi}

![](do-not-localize/header.png)

Le aziende raccolgono i dati da centinaia e migliaia di moduli, diversi sistemi back-end e origini dati online o offline. Hanno anche un set dinamico di utenti che prendono decisioni sui dati, il che implica processi di revisione e approvazione ripetitivi.

Oltre ai flussi di lavoro di revisione e approvazione per il pubblico interno ed esterno, le grandi organizzazioni e aziende hanno attività ripetitive. Ad esempio, conversione di un documento PDF in un altro formato. Una volta eseguite manualmente, queste attività richiedono molto tempo e risorse. Le aziende dispongono inoltre di requisiti legali per firmare digitalmente un documento e archiviare i dati del modulo per utilizzarli successivamente in formati predefiniti.

## Introduzione al flusso di lavoro Forms-centric su OSGi {#introduction-to-forms-centric-workflow-on-osgi}

È possibile utilizzare AEM flussi di lavoro per creare rapidamente flussi di lavoro basati su moduli adattivi. Questi flussi di lavoro possono essere utilizzati per revisioni e approvazioni, flussi di processi aziendali, per avviare Document Services, per l&#39;integrazione con  flusso di lavoro di firma Adobe Sign e operazioni simili. Ad esempio, l&#39;elaborazione delle applicazioni con carta di credito, i dipendenti, lasciando i flussi di lavoro di approvazione, salvando un modulo come documento PDF. Inoltre, questi flussi di lavoro possono essere utilizzati all&#39;interno di un&#39;organizzazione o attraverso un firewall di rete.

Con il flusso di lavoro Forms basato su OSGi, potete creare e implementare rapidamente flussi di lavoro per varie attività nello stack OSGi, senza dover installare la funzionalità di Process Management completa nello stack JEE. Lo sviluppo e la gestione dei flussi di lavoro utilizzano le funzionalità familiari AEM Workflow e AEM Inbox. I flussi di lavoro sono la base per automatizzare i processi aziendali reali che si estendono su più sistemi software, reti, reparti e persino organizzazioni.

Una volta configurati, questi flussi di lavoro possono essere attivati manualmente per completare un processo definito o eseguiti a livello di programmazione quando gli utenti inviano un modulo o [gestione della corrispondenza](/help/forms/using/cm-overview.md) lettera. Grazie a queste funzionalità avanzate AEM Workflow,  AEM Forms offre due funzionalità distinte ma simili. Come parte della strategia di distribuzione, è necessario decidere quale funziona. Vedere un [confronto](/help/forms/using/capabilities-osgi-jee-workflows.md) dei flussi di lavoro AEM Forms incentrati su OSGi e Process Management su JEE. Inoltre, per la topologia di distribuzione, vedere [Topologie di architettura e distribuzione per  AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

Il flusso di lavoro Forms basato su OSGi estende [AEM Inbox](/help/sites-authoring/inbox.md) e fornisce componenti aggiuntivi (passaggi) per AEM editor flussi di lavoro per aggiungere il supporto  flussi di lavoro incentrati su AEM Forms. La Casella in entrata AEM estesa dispone di funzionalità simili a [ AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md). Oltre a gestire flussi di lavoro basati su risorse umane (approvazione, revisione e così via), puoi utilizzare AEM flussi di lavoro per automatizzare le operazioni relative a [document services](/help/sites-developing/workflows-step-ref.md) (ad esempio, Genera PDF) e la firma elettronica ( Adobe Sign) dei documenti.

Nel diagramma seguente viene illustrata la procedura end-to-end per creare, eseguire e monitorare un flusso di lavoro Forms incentrato su OSGi.

![introduzione all’aem-forms-workflow](assets/introduction-to-aem-forms-workflow.jpg)

## Prima di iniziare {#before-you-start}

* Un flusso di lavoro è una rappresentazione di un processo aziendale reale. Tenete a portata di mano il processo aziendale e l&#39;elenco dei partecipanti al processo aziendale. Inoltre, tenete le risorse (moduli adattivi, documenti PDF e altro ancora) pronte prima di iniziare a creare un flusso di lavoro.
* Un flusso di lavoro può avere più fasi. Queste fasi vengono visualizzate nella AEM in entrata e consentono di segnalare l’avanzamento del flusso di lavoro. Dividi il processo aziendale in fasi logiche.
* È possibile configurare la fase di assegnazione dei flussi di lavoro AEM per inviare le notifiche e-mail agli utenti o assegnatari. Pertanto, [abilitare le notifiche e-mail](#configure-email-service).
* Un flusso di lavoro può inoltre utilizzare  Adobe per le firme digitali. Se prevedete di utilizzare  Adobe Sign in un flusso di lavoro, [configurate  Adobe Sign per  AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) prima di utilizzarlo in un flusso di lavoro.

## Creare un modello di workflow {#create-a-workflow-model}

Un modello di workflow è costituito dalla logica e dal flusso di lavoro di un processo aziendale. È costituito da una serie di passi. Questi passaggi sono AEM componenti. È possibile estendere i passaggi del flusso di lavoro con parametri e script per fornire funzionalità e controllo maggiori, a seconda delle necessità.  AEM Forms fornisce alcuni passaggi oltre AEM passaggi disponibili. Per un elenco dettagliato dei passaggi di AEM e  AEM Forms, vedere [AEM Workflow Step Reference](/help/sites-developing/workflows-step-ref.md) e [Forms-centric workflow on OSGi - Step Reference](/help/forms/using/aem-forms-workflow.md).

AEM un&#39;interfaccia utente intuitiva per creare un modello di workflow utilizzando i passaggi del flusso di lavoro forniti. Per istruzioni dettagliate sulla creazione di un modello di workflow, vedere [Creazione di modelli di workflow](/help/sites-developing/workflows-models.md). L&#39;esempio seguente fornisce istruzioni dettagliate per creare un modello di workflow per un flusso di lavoro di approvazione e revisione:

>[!NOTE]
>
>Per creare o modificare un modello di workflow, è necessario essere membri del gruppo di editor del flusso di lavoro.

### Creare un modello per un flusso di lavoro di approvazione e revisione {#create-a-model-for-an-approval-and-review-workflow}

Il flusso di lavoro di approvazione e revisione riguarda i compiti che richiedono l&#39;intervento umano per prendere decisioni. Nell&#39;esempio seguente viene creato un modello di flusso di lavoro per un&#39;applicazione di mutuo ipotecario da compilare da un agente bancario front-office. Una volta compilata, la domanda viene inviata per l&#39;approvazione. Successivamente, la domanda approvata viene inviata al richiedente per le firme elettroniche utilizzando  Adobe Sign.

L&#39;esempio è disponibile come pacchetto allegato di seguito. Importate e installate l&#39;esempio utilizzando il gestore pacchetti. Per creare manualmente il modello di flusso di lavoro per l’applicazione, potete inoltre effettuare le seguenti operazioni:

Nell&#39;esempio viene creato un modello di flusso di lavoro per un&#39;applicazione mutuo da compilare da un agente bancario front-office. Una volta compilata la domanda viene inviata per l&#39;approvazione. In seguito, l&#39;applicazione approvata verrà inviata al cliente per le firme elettroniche utilizzando  Adobe Sign. Potete importare e installare l’esempio utilizzando il gestore pacchetti.

[Ottieni file](assets/example-mortgage-loan-application.zip)

1. Aprite la console Modelli di workflow. L&#39;URL predefinito è `https://[Server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Selezionare **[!UICONTROL Crea]**, quindi **[!UICONTROL Crea modello]**. Viene visualizzata la finestra di dialogo Aggiungi modello flusso di lavoro.
1. Immettere **[!UICONTROL Title]** e **[!UICONTROL Name]** (facoltativo). Ad esempio, un&#39;applicazione di ipoteca. Toccate **[!UICONTROL Chiudi]**.
1. Selezionate il modello di flusso di lavoro appena creato e toccate **Modifica.** Ora puoi aggiungere passaggi al flusso di lavoro per creare logica di business. La prima volta che create un modello di workflow, questo contiene:

   * I passaggi: Inizio flusso e Fine flusso. Questi passaggi rappresentano l’inizio e la fine del flusso di lavoro. Questi passaggi sono obbligatori e non possono essere modificati o rimossi.
   * Esempio di passaggio partecipante denominato Passaggio 1. Questo passaggio è configurato per assegnare un elemento di lavoro all’utente amministratore. Rimuovi questo passaggio.

1. Abilitare le notifiche e-mail. Potete configurare il flusso di lavoro Forms-centric su OSGi per l’invio di notifiche e-mail a utenti o assegnatari. Per abilitare le notifiche e-mail, eseguite le seguenti configurazioni:

   1. Andate AEM gestore di configurazione all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
   1. Aprire la configurazione **[!UICONTROL Day CQ Mail Service]**. Specificare un valore per i campi **[!UICONTROL Nome host del server SMTP]**, **[!UICONTROL Porta server SMTP,]** e **[!UICONTROL &quot;Da&quot; indirizzo]**. Fai clic su **[!UICONTROL Salva]**.
   1. Aprite la configurazione **[!UICONTROL Day CQ Link Externalizer]**. Nel campo **[!UICONTROL Domains]**, specificate il nome host/indirizzo IP effettivo e il numero di porta per le istanze locali, di autori e di pubblicazione. Fai clic su **[!UICONTROL Salva]**.

1. Creare le fasi del flusso di lavoro. Un flusso di lavoro può avere più fasi. Tali fasi vengono visualizzate nella AEM in entrata e riportano l&#39;avanzamento del flusso di lavoro.

   Per definire un passaggio, toccate l&#39;icona ![info-cerchio](assets/info-circle.png) per aprire le proprietà del modello di workflow, aprite la scheda **[!UICONTROL Stages]**, aggiungete le fasi del modello di workflow e toccate **[!UICONTROL Save &amp; Close]** (Salva e chiudi). Per l&#39;applicazione ipoteca di esempio, creare le fasi: richiesta di prestito, stato della richiesta di prestito, documenti da firmare e documento di prestito firmato.

1. Trascinare il browser **[!UICONTROL Assegna attività]** sul modello di workflow. Impostatelo come primo passo del modello.

   Il componente Attività assegna l’attività, creata in base al flusso di lavoro, a un utente o a un gruppo. Oltre ad assegnare l’attività, è possibile utilizzare il componente per specificare un modulo adattivo o un PDF non interattivo per l’attività. Il modulo adattivo è richiesto per accettare l&#39;input degli utenti e i PDF non interattivi oppure un modulo adattivo di sola lettura viene utilizzato per i flussi di lavoro di sola revisione.

   È inoltre possibile utilizzare il passaggio per controllare il comportamento dell&#39;attività. Ad esempio, la creazione di un documento di record automatico, l&#39;assegnazione dell&#39;attività a un utente o gruppo specifico, il percorso dei dati inviati, il percorso dei dati da precompilare e le azioni predefinite. Per informazioni dettagliate sulle opzioni della fase di assegnazione delle attività, vedere il documento [Forms-centric workflow on OSGi - Step Reference](/help/forms/using/aem-forms-workflow.md) (Riferimento passo).

   ![editor workflow](assets/workflow-editor.png)

   Per l&#39;esempio dell&#39;applicazione ipotecaria, configurare il passaggio dell&#39;attività di assegnazione in modo che utilizzi un modulo adattivo di sola lettura e visualizzare il documento PDF al termine dell&#39;attività. Inoltre, selezionare il gruppo di utenti autorizzato ad approvare la richiesta di prestito. Nella scheda **[!UICONTROL Azioni]**, disabilitare l&#39;opzione **[!UICONTROL Invia]**. Specificare una variabile di percorso **[!UICONTROL Variabile di percorso]**. Ad esempio, actionTaken. Inoltre, aggiungere le route Approva e Rifiuta. Le route vengono visualizzate come azioni (pulsanti) separate nella AEM Posta in arrivo. Il flusso di lavoro seleziona un ramo in base all&#39;azione (pulsante) toccata dall&#39;utente.

   È possibile importare il pacchetto di esempio, disponibile per il download all&#39;inizio della sezione, per l&#39;insieme completo di valori di tutti i campi del passaggio dell&#39;attività di assegnazione configurato, ad esempio l&#39;applicazione mutuo.

1. Trascinate il componente O divisione dal browser a passi al modello di workflow. La divisione OR crea una divisione nel flusso di lavoro, dopo di che è attivo un solo ramo. Questo passaggio consente di introdurre i percorsi di elaborazione condizionale nel flusso di lavoro. Potete aggiungere i passaggi del flusso di lavoro a ogni ramo, a seconda delle necessità.

   Aprire le proprietà di OR Split e aggiungere i seguenti snippet di codice a Branch1 e Branch2. Questi snippet di codice consentono di scegliere un ramo in base all&#39;azione dell&#39;utente in AEM Posta in arrivo.

   **Frammento di codice per la diramazione 1**

   Quando un utente tocca **[!UICONTROL Approva]** in AEM Posta in arrivo, viene attivato il ramo 1.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Approve";
   }
   ```

   **Frammento di codice per la diramazione 2**

   Quando un utente tocca **[!UICONTROL Rifiuta]** in AEM Posta in arrivo, viene attivato il ramo 2.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Reject";
   }
   ```

1. Aggiungi altri passaggi del flusso di lavoro per creare la logica di business.

   Per l&#39;esempio relativo all&#39;ipoteca, aggiungere un documento di generazione del record, due passaggi dell&#39;attività di assegnazione e un passaggio del documento di firma al ramo 1 del modello, come illustrato nell&#39;immagine seguente. Un passaggio assegnato all&#39;attività consiste nel visualizzare e inviare **i documenti di prestito da firmare al richiedente** e un altro componente dell&#39;attività assegnata è **per visualizzare i documenti firmati**. È inoltre possibile aggiungere un componente attività di assegnazione al ramo 2. Viene attivato quando un utente tocca Rifiuta in AEM Posta in arrivo.

   Per l&#39;insieme completo di valori di tutti i campi dei passaggi dell&#39;attività di assegnazione, del passaggio del documento del record e del passaggio del documento di firma configurati ad esempio per l&#39;applicazione del mutuo, importare il pacchetto di esempio, disponibile per il download all&#39;inizio di questa sezione.

   Il modello di workflow è pronto. Potete avviare il flusso di lavoro tramite vari metodi. Per informazioni dettagliate, consultate [Avviare un flusso di lavoro Forms incentrato su OSGi](#launch).

   ![workflow-editor-mutuo](assets/workflow-editor-mortgage.png)

## Creare un&#39;applicazione per flussi di lavoro incentrata su Forms {#create-a-forms-centric-workflow-application}

L’applicazione è il modulo adattivo associato al flusso di lavoro. Quando un&#39;applicazione viene inviata tramite Inbox, avvia il flusso di lavoro associato. Per rendere disponibile un flusso di lavoro Forms come applicazione in AEM Posta in arrivo e  App AEM Forms, effettuate le seguenti operazioni per creare un’applicazione di flusso di lavoro:

>[!NOTE]
>
>È necessario essere membri del gruppo di amministratori di fd per poter creare e gestire le applicazioni del flusso di lavoro.

1. Nell&#39;istanza di AEM autore, andate a ![strumenti](assets/tools.png) > **[!UICONTROL Forms]** > **[!UICONTROL Gestisci applicazione flusso di lavoro]** e toccate **[!UICONTROL Crea]**.
1. Nella finestra Crea applicazione flusso di lavoro, fornire gli input per i campi seguenti e toccare **[!UICONTROL Crea]**. Una nuova applicazione viene creata ed elencata nella schermata Applicazioni flusso di lavoro.

<table> 
 <tbody> 
  <tr> 
   <td>Campo</td> 
   <td>Descrizione</td> 
  </tr> 
  <tr> 
   <td>Titolo</td> 
   <td>Il titolo è visibile in AEM Posta in arrivo e consente agli utenti di scegliere un’applicazione. Tenetelo descrittivo. Ad esempio, Salvataggio dell'applicazione di apertura dell'account.<br /> </td> 
  </tr> 
  <tr> 
   <td>Nome </td> 
   <td>Specificate il nome dell'applicazione. Tutti i caratteri diversi da alfabeti, numeri, trattini e caratteri di sottolineatura vengono sostituiti da trattini. </td> 
  </tr> 
  <tr> 
   <td>Descrizione</td> 
   <td>La descrizione è visibile in AEM Posta in arrivo. Fornire informazioni dettagliate sull'applicazione nei campi di descrizione. Ad esempio, Finalità dell'applicazione.<br /> </td> 
  </tr> 
  <tr> 
   <td>Modulo adattivo</td> 
   <td><p>Specificare il percorso di un modulo adattivo. Quando un utente avvia un'applicazione, viene visualizzato il modulo adattivo specificato.</p> <p><strong>Nota</strong>: Le applicazioni per i flussi di lavoro non supportano moduli e documenti PDF con più pagine o che richiedono lo scorrimento sull'iPad Apple. Quando un'applicazione viene aperta sull'iPad e il modulo adattivo o il documento PDF supera una pagina, i campi modulo e il contenuto della seconda pagina vengono persi.</p> </td> 
  </tr> 
  <tr> 
   <td>Gruppo di accesso</td> 
   <td><p>Selezionate un gruppo. L'applicazione è visibile in AEM Posta in arrivo solo ai membri del gruppo selezionato. L’opzione del gruppo di accesso rende disponibili per la selezione tutti i gruppi di utenti del flusso di lavoro. </p> <br /> </td> 
  </tr> 
  <tr> 
   <td>Servizio preriempimento</td> 
   <td>Selezionare un <a href="/help/forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">servizio di precompilazione</a> per il modulo adattivo.<br /> </td> 
  </tr> 
  <tr> 
   <td>Modello flusso di lavoro</td> 
   <td>Selezionare un <a href="/help/forms/using/aem-forms-workflow.md#create-a-workflow-model">modello di flusso di lavoro</a> per l'applicazione. Un modello di workflow è costituito dalla logica e dal flusso del processo aziendale. </td> 
  </tr> 
  <tr> 
   <td>Percorso del file di dati</td> 
   <td>Specificare il percorso del file di dati nell'archivio crx. Il percorso è relativo al payload del modulo adattivo e contiene il nome del file di dati. Includete sempre il nome completo del file, inclusa l'estensione, se applicabile. Ad esempio, [payload]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Percorso allegato</td> 
   <td>Specificare il percorso della cartella degli allegati in archivio crx. Il percorso dell'allegato è relativo alla posizione del payload. Ad esempio, [payload]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Percorso del documento record</td> 
   <td>Specificare il percorso del file del documento di registrazione nell'archivio crx. Il percorso è relativo alla posizione del payload del modulo adattivo. Includete sempre il nome completo del file, inclusa l'estensione, se applicabile. Ad esempio, [payload]/DOR/creditcard.pdf.</td> 
  </tr> 
 </tbody> 
</table>

## Avviare un flusso di lavoro Forms-centric su OSGi {#launch}

Puoi avviare o attivare un flusso di lavoro Forms:

* [Invio di un&#39;applicazione dalla AEM Posta in arrivo](#inbox)
* [Invio di un’applicazione da  app AEM Forms](#afa)

* [Invio di un modulo adattivo](#af)
* [Utilizzo della cartella esaminata](#watched)

* [Invio di una comunicazione interattiva o di una lettera](#letter)

### Invio di un&#39;applicazione da AEM Posta in arrivo {#inbox}

L’applicazione del flusso di lavoro creata è disponibile come applicazione in Posta in arrivo. Gli utenti membri del gruppo Workflow-users possono compilare e inviare l’applicazione che attiva il flusso di lavoro associato. Per informazioni sull&#39;utilizzo di AEM Inbox per inviare applicazioni e gestire attività, vedere [Gestione di applicazioni e attività Forms in AEM Inbox](/help/forms/using/manage-applications-inbox.md).

### Invio di un&#39;applicazione da  AEM Forms App {#afa}

L&#39;app  AEM Forms si sincronizza con un server  AEM Forms e consente di apportare modifiche ai dati del modulo, alle attività, alle applicazioni del flusso di lavoro e alle informazioni salvate (bozze/modelli) nel proprio account. Per ulteriori informazioni, consultate [ app AEM Forms](/help/forms/using/aem-forms-app.md) e articoli correlati.

### Invio di un modulo adattivo {#af}

È possibile configurare le azioni di invio di un modulo adattivo per avviare un flusso di lavoro dopo l’invio del modulo adattivo. I moduli adattivi forniscono l&#39;azione di invio **[!UICONTROL Richiama un flusso di lavoro AEM]** per avviare un flusso di lavoro dopo l&#39;invio di un modulo adattivo. Per informazioni dettagliate sull&#39;azione di invio, vedere [Configurazione dell&#39;azione di invio](/help/forms/using/configuring-submit-actions.md). Per inviare un modulo adattivo tramite l&#39;app AEM Forms , abilitare l&#39;opzione Sincronizza con  app AEM Forms nelle proprietà del modulo adattivo.

È possibile configurare un modulo adattivo per la sincronizzazione, l&#39;invio e l&#39;attivazione di un flusso di lavoro &#39;app AEM Forms. Per informazioni dettagliate, vedere [utilizzo di un modulo](/help/forms/using/working-with-form.md).

### Utilizzo di una cartella esaminata {#watched}

Un amministratore (membro del gruppo di amministratori di fd) può configurare una cartella di rete per eseguire un flusso di lavoro preconfigurato quando un utente inserisce un file (ad esempio un file PDF) nella cartella. Al termine del flusso di lavoro, è possibile salvare il file dei risultati in una cartella di output specificata. Tale cartella è nota come [Cartella esaminata](/help/forms/using/watched-folder-in-aem-forms.md). Per configurare una cartella esaminata e avviare un flusso di lavoro, effettuate le seguenti operazioni:

1. Nell&#39;istanza di AEM autore, andate a ![strumenti](assets/tools.png) **[!UICONTROL Forms > Configura cartella esaminata]**. Viene visualizzato un elenco di cartelle esaminate già configurate.
1. Toccate **[!UICONTROL Nuovo]**. Viene visualizzato un elenco di campi. Specificate un valore per i seguenti campi per configurare una cartella esaminata per un flusso di lavoro:

<table> 
 <tbody> 
  <tr> 
   <td>Campo</td> 
   <td>Descrizione</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Nome</span></td> 
   <td>Specificate il nome della cartella esaminata. Questo campo supporta solo caratteri alfanumerici.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Percorso</span></td> 
   <td>Specificate la posizione fisica della cartella esaminata. In un ambiente cluster, utilizzate una cartella di rete condivisa accessibile AEM nodo del cluster.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Elabora file tramite</span></td> 
   <td>Selezionare l'opzione <span class="uicontrol">Flusso di lavoro </span>. </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Modello flusso di lavoro</span></td> 
   <td>Selezionare un modello di workflow.<br /> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Motivo file di output</span></td> 
   <td>Specificate la struttura di directory per i file di output e le directory. È inoltre possibile specificare un <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">pattern per i file di output e le directory</a>.</td> 
  </tr> 
 </tbody> 
</table>

1. Toccate **[!UICONTROL Avanzate]**. Specificate un valore per il campo seguente e toccate **[!UICONTROL Crea]**. La cartella esaminata è configurata per avviare un flusso di lavoro. Ora, ogni volta che un file viene inserito nella directory di input della cartella esaminata, viene attivato il flusso di lavoro specificato.

   | Campo | Descrizione |
   |---|---|
   | Filtro servizio mappatura payload | Quando create una cartella esaminata, viene creata una struttura di cartelle nell’archivio crx. La struttura delle cartelle può fungere da payload per il flusso di lavoro. È possibile creare uno script per mappare un flusso di lavoro AEM per accettare input dalla struttura di cartelle controllata. Un&#39;implementazione out-of-the-box è disponibile ed elencata nel filtro Payload Mapper. Se non disponete di un&#39;implementazione personalizzata, selezionate l&#39;implementazione predefinita. |

   La scheda Avanzate contiene altri campi. La maggior parte di questi campi contiene un valore predefinito. Per ulteriori informazioni su tutti i campi, vedere l&#39;articolo [Crea o configura una cartella controllata](/help/forms/using/creating-configure-watched-folder.md).

### Invio di una comunicazione interattiva o di una lettera {#letter}

È possibile associare ed eseguire un flusso di lavoro Forms-centric su OSGi all&#39;invio di una comunicazione interattiva o di una lettera. Nei flussi di lavoro di gestione della corrispondenza vengono utilizzate le comunicazioni interattive e le lettere post-elaborazione. Ad esempio, invio tramite e-mail, stampa, fax o archiviazione delle lettere finali. Per informazioni dettagliate, vedere [Post-elaborazione di comunicazioni interattive e lettere](/help/forms/using/submit-letter-topostprocess.md).

## Configurazioni aggiuntive {#additional-configurations}

### Configurare il servizio e-mail {#configure-email-service}

Puoi utilizzare i passaggi Assegna attività e Invia e-mail di Flussi di lavoro AEM per inviare un messaggio e-mail. Per specificare i server e-mail e le altre configurazioni necessarie per l’invio di e-mail, effettuate le seguenti operazioni:

1. Andate AEM gestore di configurazione all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
1. Aprire la configurazione **[!UICONTROL Day CQ Mail Service]**. Specificare un valore per i campi **[!UICONTROL Nome host del server SMTP]**, **[!UICONTROL Porta server SMTP,]** e **[!UICONTROL &quot;Da&quot; indirizzo]**. Fai clic su **[!UICONTROL Salva]**.
1. Aprite la configurazione **[!UICONTROL Day CQ Link Externalizer]**. Nel campo **[!UICONTROL Domains]**, specificate il nome host/indirizzo IP effettivo e il numero di porta per le istanze locali, di autori e di pubblicazione. Fai clic su **[!UICONTROL Salva]**.

### Rimozione delle istanze del flusso di lavoro {#purge-workflow-instances}

Riducendo il numero di istanze del flusso di lavoro si ottengono maggiori prestazioni nel motore del flusso di lavoro, è possibile eliminare regolarmente dal repository le istanze del flusso di lavoro completate o in esecuzione. Per informazioni dettagliate, vedere [Scorrimento regolare delle istanze del flusso di lavoro](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).
