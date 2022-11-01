---
title: Flusso di lavoro incentrato su Forms su OSGi
seo-title: Rapidly build adaptive forms-based processes, automate document services operations, and use Acrobat Sign with AEM workflows
description: Utilizza Flusso di lavoro AEM Forms per automatizzare e creare rapidamente revisioni e approvazioni, per avviare document services (ad esempio, per convertire un documento PDF in un altro formato), per integrare con il flusso di lavoro delle firme Acrobat Sign e altro ancora.
seo-description: Use AEM Forms Workflow to automate and rapidly build review and approvals, to start document services (For example, to convert a PDF document to another format), integrate with Acrobat Sign signature workflow, and more.
uuid: 46be7ec6-d5cc-498a-9484-e66a29527064
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services, publish
discoiquuid: f8df5fa3-3843-4110-a46d-9a524d2657cd
noindex: true
exl-id: fa39a4e8-ae22-4356-8935-44fdf1f4f609
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '2866'
ht-degree: 2%

---

# Flusso di lavoro incentrato su Forms su OSGi {#forms-centric-workflow-on-osgi}

![](do-not-localize/header.png)

Le aziende raccolgono dati da centinaia e migliaia di moduli, da diversi sistemi back-end e da fonti di dati online o offline. Hanno anche un set dinamico di utenti per prendere decisioni sui dati, il che implica processi di revisione e approvazione iterativi.

Oltre ai flussi di lavoro di revisione e approvazione per il pubblico interno ed esterno, le grandi organizzazioni e aziende hanno attività ripetitive. Ad esempio, la conversione di un documento PDF in un altro formato. Una volta eseguite manualmente, queste attività richiedono molto tempo e risorse. Le aziende hanno inoltre i requisiti legali necessari per firmare digitalmente un documento e archiviare i dati del modulo in modo da utilizzarli in formati predefiniti.

## Introduzione al flusso di lavoro Forms-centric su OSGi {#introduction-to-forms-centric-workflow-on-osgi}

Puoi utilizzare flussi di lavoro AEM per creare rapidamente flussi di lavoro basati su moduli adattivi. Questi flussi di lavoro possono essere utilizzati per la revisione e le approvazioni, per i flussi dei processi aziendali, per avviare document services, per l’integrazione con il flusso di lavoro della firma Acrobat Sign e per operazioni simili. Ad esempio, l&#39;elaborazione delle applicazioni con carta di credito, il dipendente lascia i flussi di lavoro di approvazione, salvando un modulo come documento PDF. Inoltre, questi flussi di lavoro possono essere utilizzati all&#39;interno di un&#39;organizzazione o attraverso un firewall di rete.

Con il flusso di lavoro Forms-centric su OSGi, puoi creare e distribuire rapidamente flussi di lavoro per varie attività sullo stack OSGi, senza dover installare la funzionalità di Process Management completa sullo stack JEE. Lo sviluppo e la gestione dei flussi di lavoro utilizzano le funzionalità familiari AEM Workflow e AEM Inbox. I flussi di lavoro costituiscono la base per automatizzare i processi aziendali reali che si estendono su più sistemi software, reti, reparti e persino organizzazioni.

Una volta configurati, questi flussi di lavoro possono essere attivati manualmente per completare un processo definito o eseguiti a livello di programmazione quando gli utenti inviano un modulo o [gestione della corrispondenza](/help/forms/using/cm-overview.md) lettera. Con queste funzionalità avanzate del flusso di lavoro AEM, AEM Forms offre due funzionalità distinte ma simili. Come parte della strategia di implementazione, devi decidere quale funziona per te. Vedi [confronto](/help/forms/using/capabilities-osgi-jee-workflows.md) dei flussi di lavoro AEM incentrati su Forms su OSGi e Process Management su JEE. Inoltre, per la topologia di distribuzione vedere, [Architettura e topologie di implementazione per AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

Workflow Forms-centric su OSGi estende [Casella in entrata AEM](/help/sites-authoring/inbox.md) e fornisce componenti aggiuntivi (passaggi) per AEM editor di flussi di lavoro per aggiungere supporto per i flussi di lavoro incentrati su AEM Forms. La casella in entrata AEM estesa dispone di funzionalità simili a [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md). Oltre a gestire flussi di lavoro incentrati sulle persone (approvazione, revisione e così via), puoi utilizzare flussi di lavoro AEM per automatizzare [document services](/help/sites-developing/workflows-step-ref.md)Operazioni correlate (ad esempio, Genera PDF) e documenti per la firma elettronica (Acrobat Sign).

Il diagramma seguente illustra la procedura end-to-end per creare, eseguire e monitorare un flusso di lavoro incentrato su Forms su OSGi.

![introduzione ad aem-forms-workflow](assets/introduction-to-aem-forms-workflow.jpg)

## Prima di iniziare {#before-you-start}

* Un flusso di lavoro è una rappresentazione di un processo aziendale reale. Prepara il tuo processo aziendale e l&#39;elenco dei partecipanti al processo aziendale. Inoltre, tieni il materiale collaterale (moduli adattivi, documenti PDF e altro ancora) pronto prima di iniziare a creare un flusso di lavoro.
* Un flusso di lavoro può avere più fasi. Queste fasi vengono visualizzate nella casella in entrata AEM e consentono di segnalare l’avanzamento del flusso di lavoro. Dividi il tuo processo aziendale in fasi logiche.
* Puoi configurare la fase di assegnazione dell’attività dei flussi di lavoro AEM per inviare notifiche e-mail agli utenti o agli assegnatari. Quindi, [abilitare le notifiche e-mail](#configure-email-service).
* Un flusso di lavoro può inoltre utilizzare Acrobat Sign per le firme digitali. Se prevedi di utilizzare Acrobat Sign in un flusso di lavoro, la [configurare Acrobat Sign per AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) prima di utilizzarlo in un flusso di lavoro.

## Creare un modello di flusso di lavoro {#create-a-workflow-model}

Un modello di flusso di lavoro è costituito dalla logica e dal flusso di un processo aziendale. È costituito da una serie di passi. Questi passaggi sono componenti AEM. Puoi estendere i passaggi del flusso di lavoro con parametri e script per fornire ulteriori funzionalità e controlli, a seconda delle necessità. AEM Forms fornisce alcuni passaggi oltre a AEM passaggi disponibili. Per un elenco dettagliato dei passaggi di AEM e AEM Forms, vedi [Riferimento dettagliato sui flussi di lavoro AEM](/help/sites-developing/workflows-step-ref.md) e [Flusso di lavoro incentrato su Forms su OSGi - Riferimento dettagliato](/help/forms/using/aem-forms-workflow.md).

AEM fornisce un’interfaccia utente intuitiva per creare un modello di flusso di lavoro utilizzando i passaggi del flusso di lavoro forniti. Per istruzioni dettagliate sulla creazione di un modello di flusso di lavoro, consulta [Creazione di modelli di flussi di lavoro](/help/sites-developing/workflows-models.md). L&#39;esempio seguente fornisce istruzioni passo passo per creare un modello di flusso di lavoro per un flusso di lavoro di approvazione e revisione:

>[!NOTE]
>
>Per creare o modificare un modello di flusso di lavoro, devi essere membro del gruppo editor-flussi di lavoro.

### Creare un modello per un flusso di lavoro di approvazione e revisione {#create-a-model-for-an-approval-and-review-workflow}

Il flusso di lavoro di approvazione e revisione riguarda i compiti che richiedono l&#39;intervento umano per prendere decisioni. Nell&#39;esempio seguente viene creato un modello di flusso di lavoro per un&#39;applicazione di mutui ipotecari che deve essere compilata da un agente bancario di front-office. Una volta compilata, la domanda viene inviata per l&#39;approvazione. Successivamente, la domanda approvata viene inviata al richiedente la firma elettronica utilizzando Acrobat Sign.

L’esempio è disponibile come pacchetto allegato di seguito. Importa e installa l&#39;esempio utilizzando il gestore di pacchetti. Puoi anche eseguire i seguenti passaggi per creare manualmente il modello di flusso di lavoro per l’applicazione:

Nell&#39;esempio viene creato un modello di flusso di lavoro un&#39;applicazione mutuo che deve essere compilata da un agente bancario front-office. Una volta compilata la domanda viene inviata per l&#39;approvazione. Successivamente, l&#39;applicazione approvata viene inviata al cliente per le firme elettroniche che utilizzano Acrobat Sign. Puoi importare e installare l’esempio utilizzando il gestore dei pacchetti.

[Ottieni file](assets/example-mortgage-loan-application.zip)

1. Apri la console Modelli di flusso di lavoro . L’URL predefinito è `https://[Server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Seleziona **[!UICONTROL Crea]**, quindi **[!UICONTROL Crea modello]**. Viene visualizzata la finestra di dialogo Aggiungi modello flusso di lavoro.
1. Inserisci il **[!UICONTROL Titolo]** e **[!UICONTROL Nome]** (facoltativo). Ad esempio, un&#39;applicazione ipotecaria. Toccate **[!UICONTROL Chiudi]**.
1. Seleziona il modello di flusso di lavoro appena creato e tocca **Modifica.** Ora puoi aggiungere passaggi del flusso di lavoro per creare una logica di business. Quando crei un modello di flusso di lavoro per la prima volta, questo contiene:

   * I passaggi: Inizio flusso e Fine flusso. Questi passaggi rappresentano l’inizio e la fine del flusso di lavoro. Questi passaggi sono obbligatori e non possono essere modificati o rimossi.
   * Esempio di passaggio partecipante denominato Passaggio 1. Questo passaggio è configurato per assegnare un elemento di lavoro all’utente amministratore. Rimuovi questo passaggio.

1. Abilitare le notifiche e-mail. Puoi configurare un flusso di lavoro Forms-centric su OSGi per inviare notifiche e-mail agli utenti o agli assegnatari. Esegui le seguenti configurazioni per abilitare le notifiche e-mail:

   1. Vai a AEM gestione della configurazione all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
   1. Apri **[!UICONTROL Servizio e-mail Day CQ]** configurazione. Specifica un valore per **[!UICONTROL Nome host server SMTP]**, **[!UICONTROL porta server SMTP,]** e **[!UICONTROL Indirizzo &quot;Da&quot;]** campi. Fai clic su **[!UICONTROL Salva]**.
   1. Apri **[!UICONTROL Day CQ Link Externalizer]** configurazione. In **[!UICONTROL Domini]** Specifica l’indirizzo IP o nome host effettivo e il numero di porta per le istanze locali, di authoring e di pubblicazione. Fai clic su **[!UICONTROL Salva]**.

1. Crea fasi del flusso di lavoro. Un flusso di lavoro può avere più fasi. Queste fasi vengono visualizzate nella casella in entrata AEM e segnalano l’avanzamento del flusso di lavoro.

   Per definire un’area di visualizzazione, tocca ![info-cerchio](assets/info-circle.png) per aprire le proprietà del modello di flusso di lavoro, apri **[!UICONTROL Fasi]** scheda , aggiungi aree di visualizzazione per il modello di flusso di lavoro e tocca **[!UICONTROL Salva e chiudi]**. Per l&#39;esempio di applicazione ipotecaria, creare le fasi: richiesta di prestito, stato della richiesta di prestito, documenti da firmare e documento di prestito firmato.

1. Trascina e rilascia la **[!UICONTROL Assegna attività]** passa il browser al modello di flusso di lavoro. Impostalo come primo passo del modello.

   Il componente Assegnazione attività assegna l’attività, creata dal flusso di lavoro, a un utente o a un gruppo. Oltre ad assegnare l’attività, è possibile utilizzare il componente per specificare un modulo adattivo o un PDF non interattivo per l’attività. Il modulo adattivo è necessario per accettare l’input degli utenti e PDF non interattivo o un modulo adattivo di sola lettura viene utilizzato per i flussi di lavoro di sola revisione.

   È inoltre possibile utilizzare il passaggio per controllare il comportamento dell’attività. Ad esempio, per creare un documento di record automatico, assegnare l’attività a un utente o a un gruppo specifico, il percorso dei dati inviati, il percorso dei dati da precompilare e le azioni predefinite. Per informazioni dettagliate sulle opzioni della fase di assegnazione delle attività, vedere [Flusso di lavoro incentrato su Forms su OSGi - Riferimento dettagliato](/help/forms/using/aem-forms-workflow.md) documento.

   ![editor di workflow](assets/workflow-editor.png)

   Per l’esempio di applicazione ipotecaria, configurare il passaggio dell’attività di assegnazione in modo da utilizzare un modulo adattivo di sola lettura e visualizzare il documento di PDF una volta completata l’attività. Inoltre, selezionare il gruppo utenti autorizzato ad approvare la richiesta di prestito. Sulla **[!UICONTROL Azioni]** disabilita **[!UICONTROL Invia]** opzione . Specifica una **[!UICONTROL Variabile di percorso]**. Ad esempio, actionTaken. Inoltre, aggiungere le route Approva e Rifiuta. Le route vengono visualizzate come azioni separate (pulsanti) nella casella in entrata AEM. Il flusso di lavoro seleziona un ramo in base all’azione (pulsante) che un utente tocca.

   È possibile importare il pacchetto di esempio, disponibile per il download all&#39;inizio della sezione, per l&#39;insieme completo di valori di tutti i campi della fase di assegnazione delle attività configurate, ad esempio l&#39;applicazione mutuo.

1. Trascina il componente O diviso dal browser dei passaggi al modello di flusso di lavoro. La divisione OR crea una suddivisione nel flusso di lavoro, dopodiché è attivo un solo ramo. Questo passaggio ti consente di introdurre i percorsi di elaborazione condizionale nel flusso di lavoro. Puoi aggiungere i passaggi del flusso di lavoro a ogni ramo in base alle tue esigenze.

   Apri le proprietà della divisione OR e aggiungi i seguenti snippet di codice a Branch1 e Branch2. Questi snippet di codice consentono di scegliere un ramo in base all’azione dell’utente in AEM casella in entrata.

   **Frammento di codice per la diramazione 1**

   Quando un utente tocca **[!UICONTROL Approva]** in AEM casella in entrata viene attivato il ramo 1.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Approve";
   }
   ```

   **Frammento di codice per la diramazione 2**

   Quando un utente tocca **[!UICONTROL Rifiuta]** in AEM casella in entrata viene attivato il ramo 2.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Reject";
   }
   ```

1. Aggiungi altri passaggi del flusso di lavoro per generare la logica di business.

   Per l&#39;esempio di ipoteca, aggiungere un documento di generazione del record, due fasi di assegnazione delle attività e un passaggio del documento di firma al ramo 1 del modello, come illustrato nell&#39;immagine seguente. Una fase dell&#39;attività di assegnazione consiste nel visualizzare e inviare **da firmare al richiedente** e un altro componente dell’attività di assegnazione è **visualizzazione di documenti firmati**. Inoltre, aggiungi un componente task assegnato al ramo 2. Viene attivato quando un utente tocca Rifiuta nella casella in entrata AEM.

   Per l&#39;insieme completo di valori di tutti i campi dei passaggi dell&#39;attività di assegnazione, della fase del documento e della fase del documento di firma configurati ad esempio per l&#39;applicazione di ipoteca, importare il pacchetto di esempio, disponibile per il download all&#39;inizio di questa sezione.

   Il modello di flusso di lavoro è pronto. Puoi avviare il flusso di lavoro attraverso vari metodi. Per maggiori dettagli, vedi [Avvia un flusso di lavoro incentrato su Forms su OSGi](#launch).

   ![workflow-editor-mutui](assets/workflow-editor-mortgage.png)

## Creare un’applicazione per flussi di lavoro incentrata su Forms {#create-a-forms-centric-workflow-application}

L’applicazione è il modulo adattivo associato al flusso di lavoro. Quando un&#39;applicazione viene inviata tramite Posta in arrivo, avvia il flusso di lavoro associato. Per rendere disponibile un flusso di lavoro Forms come applicazione in AEM Posta in arrivo e nell’app AEM Forms, procedi come segue per creare un’applicazione flusso di lavoro:

>[!NOTE]
>
>È necessario essere membri del gruppo fd-administrator per poter creare e gestire le applicazioni del flusso di lavoro.

1. Nell’istanza di authoring di AEM, vai a ![strumenti](assets/tools.png) > **[!UICONTROL Forms]** > **[!UICONTROL Gestisci applicazione flusso di lavoro]** e tocco **[!UICONTROL Crea]**.
1. Nella finestra Crea applicazione flusso di lavoro, fornisci gli input per i campi seguenti e tocca **[!UICONTROL Crea]**. Viene creata una nuova applicazione ed è elencata nella schermata Applicazioni flusso di lavoro .

<table> 
 <tbody> 
  <tr> 
   <td>Campo</td> 
   <td>Descrizione</td> 
  </tr> 
  <tr> 
   <td>Titolo</td> 
   <td>Il titolo è visibile AEM casella in entrata e consente agli utenti di scegliere un’applicazione. Tenetela descrittiva. Ad esempio, Salvataggio dell'applicazione di apertura dell'account.<br /> </td> 
  </tr> 
  <tr> 
   <td>Nome </td> 
   <td>Specifica il nome dell'applicazione. Tutti i caratteri diversi da alfabeti, numeri, trattini e caratteri di sottolineatura vengono sostituiti con trattini. </td> 
  </tr> 
  <tr> 
   <td>Descrizione</td> 
   <td>La descrizione è visibile AEM casella in entrata. Fornisci informazioni dettagliate sull’applicazione nei campi di descrizione. Ad esempio, Scopo dell'applicazione.<br /> </td> 
  </tr> 
  <tr> 
   <td>Modulo adattivo</td> 
   <td><p>Specifica il percorso di un modulo adattivo. Quando un utente avvia un'applicazione, viene visualizzato il modulo adattivo specificato.</p> <p><strong>Nota</strong>: Le applicazioni per flussi di lavoro non supportano moduli e documenti PDF che hanno più pagine o richiedono lo scorrimento su Apple iPad. Quando un’applicazione viene aperta in Apple iPad e il modulo adattivo o il documento PDF è più lungo di una pagina, i campi modulo e il contenuto della seconda pagina vengono persi.</p> </td> 
  </tr> 
  <tr> 
   <td>Gruppo di accesso</td> 
   <td><p>Seleziona un gruppo. L'applicazione è visibile AEM casella in entrata solo ai membri del gruppo selezionato. L’opzione gruppo di accesso rende disponibili per la selezione tutti i gruppi del gruppo utenti del flusso di lavoro. </p> <br /> </td> 
  </tr> 
  <tr> 
   <td>Servizio preriempimento</td> 
   <td>Seleziona una <a href="/help/forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">servizio di precompilazione</a> per il modulo adattivo.<br /> </td> 
  </tr> 
  <tr> 
   <td>Modello flusso di lavoro</td> 
   <td>Seleziona una <a href="/help/forms/using/aem-forms-workflow.md#create-a-workflow-model">modello di flusso di lavoro</a> per la domanda. Un modello di flusso di lavoro è costituito dalla logica e dal flusso del processo aziendale. </td> 
  </tr> 
  <tr> 
   <td>Percorso del file di dati</td> 
   <td>Specifica il percorso del file di dati in crx-repository. Il percorso è relativo al payload del modulo adattivo e contiene il nome del file di dati. Includi sempre il nome completo del file, inclusa l’estensione, se applicabile. Ad esempio, [payload]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Percorso allegato</td> 
   <td>Specifica il percorso della cartella degli allegati in crx-repository. Il percorso allegato è relativo alla posizione del payload. Ad esempio, [payload]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Percorso del documento record</td> 
   <td>Specifica il percorso del file del documento di record in crx-repository. Il percorso è relativo alla posizione del payload del modulo adattivo. Includi sempre il nome completo del file, inclusa l’estensione, se applicabile. Ad esempio, [payload]/DOR/creditcard.pdf.</td> 
  </tr> 
 </tbody> 
</table>

## Avvia un flusso di lavoro incentrato su Forms su OSGi {#launch}

Puoi avviare o attivare un flusso di lavoro incentrato su Forms:

* [Invio di un’applicazione da AEM casella in entrata](#inbox)
* [Invio di un’applicazione dall’app AEM Forms](#afa)

* [Invio di un modulo adattivo](#af)
* [Utilizzo della cartella controllata](#watched)

* [Invio di una comunicazione interattiva o di una lettera](#letter)

### Invio di un’applicazione da AEM casella in entrata {#inbox}

L’applicazione del flusso di lavoro creata è disponibile come applicazione nella casella in entrata. Gli utenti membri del gruppo utenti del flusso di lavoro possono compilare e inviare l’applicazione che attiva il flusso di lavoro associato. Per informazioni sull&#39;utilizzo di AEM Posta in arrivo per inviare le applicazioni e gestire le attività, vedere [Gestione di applicazioni e attività Forms nella casella in entrata AEM](/help/forms/using/manage-applications-inbox.md).

### Invio di un’applicazione dall’app AEM Forms {#afa}

L’app AEM Forms si sincronizza con un server AEM Forms e consente di apportare modifiche ai dati del modulo, alle attività, alle applicazioni del flusso di lavoro e alle informazioni salvate (bozze/modelli) nel tuo account. Per ulteriori informazioni, consulta [app AEM Forms](/help/forms/using/aem-forms-app.md) e articoli correlati.

### Invio di un modulo adattivo {#af}

Puoi configurare le azioni di invio di un modulo adattivo per avviare un flusso di lavoro dopo l’invio del modulo adattivo. I moduli adattivi forniscono **[!UICONTROL Richiamare un flusso di lavoro AEM]** invia un’azione per avviare un flusso di lavoro dopo l’invio di un modulo adattivo. Per informazioni dettagliate sull’azione di invio, consulta [Configurazione dell’azione Invia](/help/forms/using/configuring-submit-actions.md). Per inviare un modulo adattivo tramite l’app AEM Forms, abilita Sincronizza con app AEM Forms nelle proprietà del modulo adattivo.

Puoi configurare un modulo adattivo per sincronizzare, inviare e attivare un flusso di lavoro dall’app AEM Forms. Per maggiori dettagli, vedi [utilizzo di un modulo](/help/forms/using/working-with-form.md).

### Utilizzo di una cartella controllata {#watched}

Un amministratore (membro del gruppo fd-administrators ) può configurare una cartella di rete per eseguire un flusso di lavoro preconfigurato quando un utente inserisce un file (ad esempio un file PDF) nella cartella. Al termine del flusso di lavoro, può salvare il file dei risultati in una cartella di output specificata. Tale cartella è nota come [Cartella osservata](/help/forms/using/watched-folder-in-aem-forms.md). Esegui la seguente procedura per configurare una cartella controllata per avviare un flusso di lavoro:

1. Nell’istanza di authoring di AEM, vai a ![strumenti](assets/tools.png) **[!UICONTROL Forms > Configura cartella osservata]**. Viene visualizzato un elenco di cartelle controllate già configurate.
1. Tocca **[!UICONTROL Nuovo]**. Viene visualizzato un elenco di campi. Specifica un valore per i campi seguenti per configurare una cartella sottoposta a controllo per un flusso di lavoro:

<table> 
 <tbody> 
  <tr> 
   <td>Campo</td> 
   <td>Descrizione</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Nome</span></td> 
   <td>Specifica il nome della cartella controllata. Questo campo supporta solo caratteri alfanumerici.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Percorso </span></td> 
   <td>Specificare la posizione fisica della cartella osservata. In un ambiente cluster, utilizza una cartella di rete condivisa accessibile AEM nodo cluster.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Elabora file tramite</span></td> 
   <td>Seleziona la <span class="uicontrol">Flusso di lavoro </span>opzione . </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Modello flusso di lavoro</span></td> 
   <td>Seleziona un modello di flusso di lavoro.<br /> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Motivo file di output</span></td> 
   <td>Specifica la struttura della directory per i file e le directory di output. Puoi inoltre specificare un <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">pattern per file e directory di output</a>.</td> 
  </tr> 
 </tbody> 
</table>

1. Tocca **[!UICONTROL Avanzate]**. Specifica un valore per il campo seguente e tocca **[!UICONTROL Crea]**. La cartella controllata è configurata per avviare un flusso di lavoro. Ora, ogni volta che un file viene inserito nella directory di input della cartella sottoposta a controllo, viene attivato il flusso di lavoro specificato.

   | Campo | Descrizione |
   |---|---|
   | Filtro servizio mappatura payload | Quando crei una cartella controllata, crea una struttura di cartelle nell&#39;archivio crx. La struttura delle cartelle può fungere da payload per il flusso di lavoro. È possibile scrivere uno script per mappare un flusso di lavoro AEM per accettare gli input dalla struttura delle cartelle controllate. Un’implementazione preconfigurata è disponibile ed elencata nel filtro Payload Mapper . Se non disponi di un’implementazione personalizzata, seleziona l’implementazione predefinita. |

   La scheda Avanzate contiene altri campi. La maggior parte di questi campi contiene un valore predefinito. Per informazioni su tutti i campi, consulta [Creare o configurare una cartella controllata](/help/forms/using/creating-configure-watched-folder.md) articolo.

### Invio di una comunicazione interattiva o di una lettera {#letter}

Puoi associare ed eseguire un flusso di lavoro Forms-centric su OSGi all’invio di una comunicazione interattiva o di una lettera. Nei flussi di lavoro di gestione della corrispondenza vengono utilizzati per la post-elaborazione di comunicazioni e lettere interattive. Ad esempio, inviare e-mail, stampare, inviare fax o archiviare le lettere finali. Per i passaggi dettagliati vedi [Post-elaborazione di comunicazioni e lettere interattive](/help/forms/using/submit-letter-topostprocess.md).

## Configurazioni aggiuntive {#additional-configurations}

### Configurare il servizio e-mail {#configure-email-service}

Puoi utilizzare i passaggi Assegna attività e Invia e-mail di flussi di lavoro AEM per inviare un’e-mail. Esegui i seguenti passaggi per specificare i server e-mail e le altre configurazioni necessarie per l’invio delle e-mail:

1. Vai a AEM gestione della configurazione all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
1. Apri **[!UICONTROL Servizio e-mail Day CQ]** configurazione. Specifica un valore per **[!UICONTROL Nome host server SMTP]**, **[!UICONTROL porta server SMTP,]** e **[!UICONTROL Indirizzo &quot;Da&quot;]** campi. Fai clic su **[!UICONTROL Salva]**.
1. Apri **[!UICONTROL Day CQ Link Externalizer]** configurazione. In **[!UICONTROL Domini]** Specifica l’indirizzo IP o nome host effettivo e il numero di porta per le istanze locali, di authoring e di pubblicazione. Fai clic su **[!UICONTROL Salva]**.

### Eliminare le istanze del flusso di lavoro {#purge-workflow-instances}

Minimizzare il numero di istanze del flusso di lavoro aumenta le prestazioni del motore del flusso di lavoro, in modo da poter eliminare regolarmente dall’archivio le istanze del flusso di lavoro completate o in esecuzione. Per informazioni dettagliate, consulta [Rimozione regolare delle istanze del flusso di lavoro](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).
