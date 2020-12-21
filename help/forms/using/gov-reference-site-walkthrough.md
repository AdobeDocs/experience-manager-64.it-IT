---
title: Procedura dettagliata sul sito di riferimento We.Gov
seo-title: Procedura dettagliata sul sito di riferimento We.Gov
description: 'Consultate la guida dettagliata del sito di riferimento We.Gov per comprendere in che modo  AEM Forms aiuta i governi a gestire le singole informazioni. '
seo-description: 'Consultate la guida dettagliata del sito di riferimento We.Gov per comprendere in che modo  AEM Forms aiuta i governi a gestire le singole informazioni. '
uuid: 348f9067-28b5-47ed-8e83-0dbadeff0854
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 25a6d702-9995-4c63-99d8-3e5d710bb0c4
translation-type: tm+mt
source-git-commit: 7e58d1d861f832d073fb178868804995ee8d855b
workflow-type: tm+mt
source-wordcount: '2737'
ht-degree: 0%

---


# Procedura dettagliata sul sito di riferimento We.Gov {#we-gov-reference-site-walkthrough}

## Pre-requisito {#pre-requisite}

Configurate il sito di riferimento We.Gov come descritto in [Configurare e configurare  siti di riferimento AEM Forms](/help/forms/using/setup-reference-sites.md).

## Scenario di riferimento del sito {#reference-site-scenario}

We.Gov è un&#39;organizzazione governativa che permette ai genitori adottivi di iscriversi al sostegno dei figli se adottano un figlio. Il sito gestisce quanto segue:

* Ammissibilità del richiedente, del padre adottivo
* Dati personali e professionali del richiedente (se il richiedente è idoneo al sostegno per i bambini)
* Dati personali del bambino adottato

   Il richiedente può fornire dettagli su più di un figlio
* Dati del conto bancario del richiedente in cui il richiedente può beneficiare di prestazioni di sostegno per i figli
* Recupero della tassa di domanda
* Valutazione della domanda
* Approvazione della domanda
* Comunicazione automatizzata al richiedente

Una volta inoltrata la domanda e pagata la tassa, il richiedente riceve un’e-mail dall’organizzazione con conferma della domanda inoltrata.

L&#39;organizzazione We.Gov riceve l&#39;applicazione. L&#39;organizzazione ottiene la valutazione dell&#39;applicazione e approva le applicazioni autentiche.

Dopo l&#39;approvazione della domanda, il richiedente riceve un&#39;e-mail dal sito We.Gov. L&#39;opzione **Visualizza documento** nell&#39;e-mail collega un documento con i dettagli di iscrizione del richiedente.

L&#39;infografica seguente mostra il flusso di lavoro dettagliato dello scenario del sito di riferimento We.Gov.

![workflow_aem_gov_2](assets/workflow_aem_gov_2.png)

Lo scenario coinvolge le seguenti persone:

* Sarah Rose, il genitore adottivo che richiede supporto per bambini
* Joe, il bambino adottato
* Gloria Rios, capo della divisione di approvazione, We.Gov
* Conard Simms, l&#39;agente di campo che si occupa della valutazione dell&#39;applicazione

## Sarah avvia il controllo di idoneità {#sarah-initiates-her-eligibility-check}

Un richiedente può verificare l’idoneità per richiedere prestazioni di assistenza per bambini. Il sito consente agli utenti di rispondere alle domande e consentire loro di determinare se la loro applicazione è idonea ai benefici. Sarah, una genitore adottiva, è una potenziale richiedente. Il modulo di idoneità fa parte dell’applicazione per i servizi di assistenza per i bambini del sito We.Gov. Per verificare la propria idoneità, Sarah fa clic su **[!UICONTROL Supporto per bambini]** nel sito Web di We.Gov. Nella pagina Assistenza figlio, Sarah fa clic su **[!UICONTROL Verifica la tua idoneità]**.

Oltre a questo approccio, Sarah può fare clic su **[!UICONTROL Get Started]** nella home page. Sarah viene visualizzata la pagina Tutte le applicazioni, in cui può fare clic su Applica in **[!UICONTROL Application for Child Support Services]**. Sarah viene poi portata al controllo di idoneità.

Nella pagina Verifica idoneità per supporto figlio, Sarah riceve una serie di domande per determinare la propria idoneità per i benefici di assistenza ai bambini. Attraverso la serie di domande, le viene chiesto:

* Se è il genitore custodito del figlio
* Se lei e il bambino vivono nello stato di GX
* Il gruppo di età dell&#39;educazione dei bambini e dei bambini.

Sarah risponde a queste domande e la sua idoneità è convalidata. Le sue risposte determinano se ha diritto al sostegno per i bambini.

Sarah viene informata che ha diritto al sostegno per i bambini, e la tariffa per l&#39;iscrizione è di $ 25.

### Come funziona {#how-it-works}

L&#39;idoneità di Sarah viene convalidata tramite una barriera di idoneità creata utilizzando l&#39;editor di regole. L&#39;editor di regole consente di specificare le condizioni che vengono soddisfatte prima che un richiedente possa compilare il modulo di domanda. Quando Sarah, la ricorrente, soddisfa tutte le condizioni di ammissibilità, si iscrive nel modulo di domanda.

La verifica di idoneità fa parte del modulo adattivo per l&#39;applicazione di supporto figlio. La regola convalida l&#39;idoneità quando:

* Il richiedente è un genitore custodito
* Il richiedente e il bambino soggiornano nello stato di GX
* Il richiedente ha la cura principale giorno per giorno del bambino
* L&#39;età del bambino che riceve servizi di assistenza è sotto i 16 anni.

### Vedere da soli {#see-it-yourself}

Nel browser, aprite `https://<hostname>:<PublishPort>/content/we-gov/en.html`. Nel sito We.Gov, fate clic su Supporto per bambini. Nella pagina Supporto figlio, fate clic su Verifica idoneità.

Per visualizzare le regole:

1. Aprire il modulo in modalità di modifica nell’istanza di creazione. URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`.
1. Selezionate un componente e fate clic su ![edit-rules](assets/edit-rules.png).

   Viene visualizzato l&#39;Editor regole in cui sono elencate tutte le regole applicate al modulo.

1. Nel pannello a sinistra, fate clic sulle regole `passMsg` e `failMsg` per capire come funziona il controllo di idoneità.

## Sarah avvia la sua applicazione per il supporto dei bambini {#sarah-starts-her-application-for-child-support}

Sarah fa clic su **[!UICONTROL Avvia applicazione]** dopo essere stata informata della sua idoneità per il supporto dei bambini.\
Nella pagina Application For Child Support Services, Sarah fornisce i dettagli nelle sezioni seguenti:

* **[!UICONTROL Informazioni sul richiedente]**: Lascia che Sarah fornisca i suoi dettagli in questa sezione.

* **[!UICONTROL Informazioni]** figlio: Lascia che Sarah fornisca le informazioni del bambino, che è coperto dai servizi di supporto.

* **[!UICONTROL Pagamento]**: Lascia che Sarah fornisca i suoi dati bancari in cui We.Gov può depositare il compenso mensile del supporto.

* **[!UICONTROL Pagamento]** della tariffa: Lascia che Sarah fornisca i dati della sua carta di credito per pagare la tassa di richiesta.

Per impostazione predefinita, Sarah viene portata alla sezione **[!UICONTROL Informazioni su richiedente]**.

![Applicazione di supporto per bambini sul desktop](assets/desktop.png)

In qualsiasi momento, Sarah può fare clic su **[!UICONTROL Torna più tardi]** e riprendere con la sua applicazione. Quando fa clic su **[!UICONTROL Torna più tardi]**, i suoi progressi vengono salvati come bozza e riceve un&#39;opzione per inviare via e-mail la bozza.

Quando fa clic su **[!UICONTROL Invia e-mail]**, riceve un messaggio e-mail contenente un collegamento alla bozza del modulo.

Il modulo di supporto figlio sul sito Web di We.Gov utilizza moduli adattivi. Può usare il collegamento nell’e-mail e compilare il modulo sul dispositivo mobile.

>[!NOTE]
>
>Il flusso di lavoro di ripresa da e-mail funziona solo con gli utenti connessi. Nello scenario del sito di riferimento, accertatevi che l’utente Sarah Rose sia aggiunto. Le credenziali di accesso di Sarah sono `srose/password`.

![mob1](assets/mob1.png)

Sarah può fornire i dettagli in qualsiasi sezione, ma la tariffa per l&#39;applicazione è accettata solo dopo aver fornito le informazioni richieste in tutte le sezioni. Un&#39;applicazione è incompleta senza pagamento a pagamento e i campi contrassegnati con un asterisco sono obbligatori.

### <strong>Sarah fornisce le sue informazioni</strong> {#strong-sarah-provides-her-information-strong}

Dopo che Sarah fa clic su **[!UICONTROL Avvia applicazione]**, viene portata alla sezione Informazioni sui candidati della pagina Application For Child Support Services. In Informazioni sul candidato, Sarah naviga tra le schede e fornisce i suoi dati personali per l&#39;applicazione. Fa clic su **[!UICONTROL Next]** per navigare tra le schede.

Nella sezione Informazioni sui candidati, le viene chiesto di fornire i dettagli nelle seguenti schede:

* **[!UICONTROL Informazioni di base]**

In Informazioni di base, Sarah fornisce la sua prova d&#39;identità e i suoi dati personali. Le informazioni personali di Sarah includono nome, ID e-mail e numero di previdenza sociale.

* **[!UICONTROL Relazione]**

   Sotto la relazione, Sarah inserisce informazioni sul suo stato civile.

* **[!UICONTROL Informazioni aggiuntive]**

   In Ulteriori informazioni, Sarah immette un numero di identificazione, la data di nascita e l&#39;indirizzo e il numero di telefono correnti.

### Sarah fornisce informazioni sui bambini {#sarah-provides-child-information}

Dopo che Sarah ha fornito i suoi dati personali e ha fatto clic su **[!UICONTROL Next]**, viene portata alla sezione Informazioni sui bambini.

Nella sezione Informazioni figlio, fornisce i seguenti dettagli:

* Numero di figli da richiedere servizi di supporto per bambini
* Nome del bambino, numero di previdenza sociale, data di nascita e luogo di nascita

Se Sarah sceglie più di un bambino, le verranno abilitati moduli aggiuntivi con gli stessi dettagli da compilare.\
Sarah sceglie il suo figlio singolo, Joe, e gli dà il nome.

### Sarah fornisce informazioni di pagamento {#sarah-provides-payment-information}

Dopo che Sarah fornisce informazioni sul figlio adottato (o sui figli) e fa clic su **[!UICONTROL Next]**, viene portata alla sezione **[!UICONTROL Informazioni sul pagamento]**.

Nella sezione Informazioni sul pagamento, l&#39;utente fornisce i dettagli del conto bancario in cui può ricevere i sussidi per l&#39;assistenza ai figli.\
Immette il suo numero di conto bancario di dieci cifre.

## Sarah paga la tariffa dell&#39;applicazione e firma il modulo {#sarah-pays-the-application-fee-and-signs-the-form}

Dopo che Sarah accetta i termini e le condizioni dell&#39;applicazione, paga la tassa di applicazione di $25. La tariffa per l&#39;applicazione è richiesta per l&#39;elaborazione della sua applicazione.\
Sarah immette i dati della sua carta di credito e fa clic su **[!UICONTROL Paga ora]**. Dopo aver pagato le tariffe, viene visualizzata una versione PDF dell&#39;applicazione con un campo firma.

![sarah-sign-1](assets/sarah-sign-1.png)

Sarah può scegliere di digitare, utilizzare il disegno per la scrittura a mano, inserire un&#39;immagine della firma o utilizzare il touchscreen del suo cellulare per disegnare la firma. Sarah digita il suo nome e fa clic su Fare clic per firmare.

La sua domanda viene inoltrata al sito We.Gov.

### <strong>Sarah riceve un messaggio e-mail di conferma</strong> {#strong-sarah-receives-an-acknowledgement-email-strong}

Dopo che Sarah ha pagato la tariffa per la richiesta, riceve un messaggio di conferma dal sito We.Gov.\
We.Gov elabora l&#39;applicazione, e Sarah è informata che riceverà un compenso mensile dopo che la sua applicazione sarà stata approvata.

![sarah-ack-email](assets/sarah-ack-email.png)

### Come funziona {#how-it-works-1}

L&#39;applicazione di supporto per elementi figlio utilizza una combinazione di layout di pannelli come la scheda superiore, la procedura guidata e il pannello a soffietto per creare l&#39;esperienza. Utilizza un modello di modulo denominato Modello figlio We.Gov.

Il richiedente può spostarsi tra le sezioni per compilare diversi componenti del modulo. Quando il richiedente compila il modulo, lo invia, accetta i termini e le condizioni e paga la tariffa, viene avviato un flusso di lavoro personalizzato. Il flusso di lavoro personalizzato invia un messaggio e-mail automatico al richiedente che conferma l’invio dell’applicazione. La domanda viene inoltrata all&#39;ufficio interessato per la verifica e l&#39;approvazione.

Il layout del modulo è specificato nel Tema del servizio di supporto figlio governativo. Lo stile include lo stile del componente, lo sfondo della pagina, la formattazione dello stato di errore dei componenti e gli stili dei font.

Il controllo di idoneità utilizza le regole specificate nel modulo. Utilizza i controlli di validità specificati di seguito:

`SHOW passMsgWHEN (Does the child live in the state of GX? is equal to Yes) AND (Do you live in the state of GX? is equal to Yes) AND ( (Who has the main day-to-day care of the child? is equal to You) AND (Are you: is equal to The custodial parent) ) AND (Is the child you are applying for: is equal to Under 16 years) ELSE Hide`

`HIDE failMsg WHEN (Does the child lives in the state of GX? is equal to Yes) AND ( (Do you live in the state of GX? is equal to Yes) AND (Who has the main day-to-day care of the child? is equal to You) ) AND (Is the child you are applying for: is equal to Under 16 years) AND (Are you: is equal to The custodial parent) ELSE Show`

### Vedere da soli {#see-it-yourself-1}

Nel browser, aprite `https://<hostname>:<PublishPort>/content/forms/af/we-gov/child-support/css.html` e compilate le informazioni richieste. Quando si invia l&#39;applicazione dopo aver compilato le informazioni richieste, pagato le tariffe e firmato il documento, si riceve l&#39;e-mail di conferma.

Vedete il Modello per bambini We.Gov qui: `https://<hostname>:<AuthorPort>/editor.html/conf/we-gov/settings/wcm/templates/we-gov-child-template/structure.html`

Consulta il tema qui: `https://<hostname>:<AuthorPort>/editor.html/content/dam/formsanddocuments-themes/we-gov/we-gov-theme-A/jcr:content`

Per visualizzare tutte le regole, eseguire le operazioni seguenti:

1. Aprire il modulo in modalità di creazione.

   URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`

1. Selezionate un componente e toccate ![edit-rules](assets/edit-rules.png). Tutte le regole sono elencate nell&#39;editor delle regole, incluse quelle elencate sopra.

## Gloria riceve l&#39;applicazione {#gloria-receives-the-application}

Gloria, responsabile delle approvazioni di We.Gov, può visualizzare, approvare o rifiutare le richieste inviate. AEM Posta in arrivo consente di visualizzare tutte le applicazioni inviate in un&#39;unica posizione.

### Come funziona {#how-it-works-2}

Quando Sarah riempie e invia l&#39;applicazione di supporto per bambini, viene creato un PDF o un documento di registrazione dell&#39;applicazione e inviato alla inbox di Gloria Rios. Gloria può visualizzare la domanda inviata e accettarla o rifiutarla.

### Vedere da soli {#see-it-yourself-2}

Apri pagina `https://<hostname***>:<PublishPort>/content/we-gov/en.html`. Sulla pagina, toccare **[!UICONTROL Accedi]**, selezionare la casella di controllo **[!UICONTROL Accedi come rappresentante]**, accedere alla casella in entrata AEM utilizzando grios/password come nome utente/password per Gloria Rios. Viene visualizzata l’applicazione di supporto figlio. Per informazioni sull&#39;utilizzo di AEM Inbox per le attività relative ai flussi di lavoro incentrate sui moduli, vedere [Gestione di applicazioni e attività Forms in AEM Inbox](/help/forms/using/manage-applications-inbox.md).

![La inbox di Gloria nel refsite We.Gov](assets/gloria-inbox.png)

Gloria può visualizzare, approvare o rifiutare l’applicazione dal dashboard dell’applicazione.

### Come funziona {#how-it-works-3}

Gloria, responsabile delle approvazioni a We.Gov, apre la sua casella AEM. Visualizza un&#39;attività di revisione nel suo elenco di compiti. Apre e visualizza l&#39;attività di revisione.

Vede un PDF del modulo compilato con i dettagli inseriti da Sarah insieme ai documenti caricati da Sarah.\
Gloria può approvare o respingere la domanda. Tuttavia, Gloria fa clic su **[!UICONTROL Valutazione richiesta]** per valutare l&#39;applicazione.

![gloria-invia-valutazione](assets/gloria-sends-assessment.png)

L&#39;applicazione di Sarah è un punto di partenza nel flusso di lavoro AEM. Viene avviato il flusso di lavoro AEM all’invio del modulo di richiesta del supporto figlio. Il flusso di lavoro AEM crea un&#39;attività per Gloria, che compare nella sua casella AEM. Quando Gloria richiede la valutazione in loco, viene creata una nuova attività per l&#39;agente di campo.

### Vedere da soli {#see-it-yourself-3}

Se la configurazione è completa, il flusso di lavoro AEM inizia subito dopo l&#39;invio del modulo. Accedete alla inbox utilizzando le credenziali di Gloria.

Accedete alla inbox all&#39;indirizzo https://&lt;***hostname***>:&lt;***PublishPort***>/content/we-gov/en.html. Sulla pagina, toccare **[!UICONTROL Accesso]**, selezionare la casella di controllo **[!UICONTROL Accesso come rappresentante]** utilizzare le credenziali predefinite di Gloria:

* Nome utente: grios
* Password: password

Nella sua casella in entrata AEM, l&#39;applicazione di Sarah viene aggiunta come attività di revisione. Selezionate l&#39;attività e fate clic su **Valutazione richiesta** per passare al passaggio successivo.

### Conard ottiene l&#39;attività Valutazione {#conard-assessment-task}

Quando Gloria fa clic su **[!UICONTROL Valutazione richiesta]**, Conard riceve l&#39;attività di revisione nella propria casella in entrata AEM. L&#39;attività rappresenta il passaggio successivo nel flusso di lavoro AEM definito nel modello di workflow. Vede il compito di revisione e lo apre.

Conard ottiene il compito di valutazione del candidato come mostrato di seguito.

![conrad-inbox](assets/conrad-inbox.png)

La valutazione del supporto figlio è un modulo associato all&#39;attività. Riceve i dettagli di Sarah, insieme ai documenti di supporto (allegati nei dettagli del compito). Conard compila il modulo di valutazione nel campo su un dispositivo e lo invia per la rivalutazione.

Conard verifica tutti i dettagli forniti da Sarah e Sarah firma la valutazione.  AEM Forms può prendere la posizione e la marca temporale e aggiungerli alla firma.

![submit-for-re-assessment](assets/submit-for-re-evaluation.png)

Conard fa clic su **[!UICONTROL Invia per rivalutazione]** e il flusso di lavoro AEM invia la valutazione all&#39;organizzazione We.Gov.

### Come funziona {#how-it-works-4}

Quando Gloria richiede una valutazione, viene avviato il passaggio successivo AEM flusso di lavoro e l&#39;attività di valutazione viene aggiunta nella inbox di Conard. Conard è il personaggio del lavoratore sul campo.

Conard visita il posto di Sarah, verifica che le informazioni fornite da Sarah siano autentiche e compila il modulo di valutazione. Conard può accedere a un PDF dell&#39;intero modulo compilato da Sarah.

### Vedere da soli {#see-it-yourself-4}

Aprite la casella in entrata AEM sul tablet e utilizzate le credenziali di Conard per effettuare l&#39;accesso.

Le credenziali predefinite di Conard sono:

* Nome utente: csimms
* Password: password

Nella inbox è disponibile una nuova attività Richiesta di valutazione. Invia la valutazione completata e passa alla fase successiva.

### Gloria esamina la valutazione e approva la domanda{#gloria-reviews-the-assessment-and-approves-the-application}

Dopo che Conard ha presentato la valutazione, Gloria vede un compito di revisione nella sua inbox. Seleziona e apre **[!UICONTROL Review]**.

![gloriainbox-1](assets/gloriainbox-1.png)

In Dettagli attività, Gloria vede Ultima azione eseguita come &quot;Invia per nuova valutazione&quot; (da Conard). Gloria vede che Conard Simms ha valutato l&#39;applicazione.

![gloriaapproves](assets/gloriaapproves.png)

### Come funziona {#how-it-works-5}

Dopo che Conard ha presentato la valutazione, Gloria vede un compito di revisione nella sua inbox. Seleziona e apre Review. In Dettagli attività, Gloria vede il commento di valutazione fatto da Conard, che è &quot;Tutto trovato in ordine&quot;.

Gloria approva la domanda.

### Vedere da soli {#see-it-yourself-5}

Aprite la inbox ed effettuate l&#39;accesso utilizzando le credenziali di Gloria. Nella inbox viene visualizzata una nuova attività denominata Review.

Aprire l&#39;attività per visualizzare lo stato dell&#39;ultima azione eseguita. In base alla valutazione, approva la domanda.

## Sarah riceve un&#39;e-mail di approvazione {#sarah-receives-an-approval-email}

Dopo che Gloria ha approvato l&#39;applicazione, Sarah riceve un&#39;e-mail da We.Gov che la sua applicazione è stata approvata.

Il pulsante **[!UICONTROL Visualizza documento]** nell&#39;e-mail rimanda ai dettagli di iscrizione. Sarah fa clic su **[!UICONTROL Visualizza documento.]**

![approvazione-iscrizione-kit-email](assets/approval-enrolment-kit-email.png)

Il documento di iscrizione elenca dettagli quali l’ID di riferimento, l’ID figlio coperto, la data di inizio, il numero del conto bancario, la frequenza del pagamento e l’importo del pagamento.

![arruba-enrollment-details](assets/sarah-enrollment-details.png)

Sarah può visualizzare i documenti caricati nella stessa pagina.

![documenti caricati](assets/uploaded-documents.png)

### Come funziona {#how-it-works-6}

Quando Gloria approva l&#39;applicazione, Sarah riceve un&#39;e-mail automatizzata con un collegamento al documento di iscrizione.

Il documento di iscrizione è una comunicazione interattiva e può essere visualizzato su qualsiasi dispositivo. Contiene i dettagli del servizio di assistenza per i bambini e le informazioni fornite da Sarah.

### Vedere da soli {#see-it-yourself-6}

Controllate il client e-mail configurato per l’e-mail automatica con un collegamento al documento di iscrizione.

In alternativa, per visualizzare il documento nel browser, aprite: `https://<hostname>:<PublishPort>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-gov/child-support/enrollment-document&referenceId=[reference-id]&channel=web`

## We.Gov analizza le prestazioni dell&#39;applicazione {#we-gov-analyzes-the-performance-of-the-application}

We.Gov, di tanto in tanto, analizza le prestazioni dell&#39;applicazione di servizi di assistenza ai figli per verificare se i clienti potrebbero dover affrontare dei problemi. Utilizzano questa analisi per prendere decisioni informate sulle modifiche richieste nell&#39;applicazione dei servizi di assistenza per migliorare l&#39;esperienza dell&#39;utente, ridurre il tasso di abbandono dei moduli e quindi migliorare la conversione. Utilizzano l&#39;integrazione di  AEM Forms con  Adobe Analytics per la loro analisi. L&#39;immagine seguente mostra il loro dashboard di analisi.

![child-support-analytics-dashboard](assets/child-support-analytics-dashboard.png)

### Come funziona {#how-it-works-7}

Le metriche delle prestazioni per il modulo dell&#39;applicazione dei servizi di supporto figlio vengono tracciate utilizzando  Adobe Analytics. Per ulteriori informazioni sulla configurazione  Adobe Analytics e la visualizzazione dei report, vedere [Configuring analytics for forms and documents](/help/forms/using/configure-analytics-forms-documents.md) (Configurazione dell&#39;analisi per moduli e documenti).

### Vedere da soli {#see-it-yourself-7}

Per visualizzare ed esaminare il rapporto di analisi, nel sito di riferimento vengono forniti i dati iniziali per l&#39;applicazione dei servizi di supporto per bambini. Prima di utilizzare i dati iniziali, vedete [Configurare Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). Per visualizzare il rapporto con i dati iniziali, effettuate i seguenti passaggi nell’istanza di creazione:

1. Andate all&#39;interfaccia di **[!UICONTROL Forms &amp; Documents]** all&#39;indirizzo https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Fare clic per aprire la cartella **We.Gov**.
1. Selezionare il modulo adattivo **[!UICONTROL Application for Child Support Services]**, quindi fare clic su **[!UICONTROL Enable Analytics]** (Abilita Analytics) nella barra degli strumenti.

1. Selezionate di nuovo il modulo e fate clic su **[!UICONTROL Rapporto analisi]** nella barra degli strumenti per generare il rapporto. Inizialmente viene visualizzato un rapporto vuoto.

Per generare report di analisi con dati iniziali:

1. Nel browser dell&#39;indirizzo di CRXDE lite, digitare: **/apps/we-gov/demo-artifact/analyticsTestData/Child support service Analytics Test Data**
1. I dati iniziali vengono selezionati nella struttura di directory a sinistra.
1. Fate doppio clic sul file selezionato per aprirne il contenuto nel pannello a destra.
1. Copiate tutto il contenuto nel file di dati di prova.
1. In CRXDE, passa a: **/content/dam/formsanddocuments/we-gov/child-support/css/jcr:content/analyticsdatanode/lastsevendays**
1. Nel campo dei dati di analisi in Proprietà, incollate il contenuto copiato del file di dati di prova.
1. Ora generate di nuovo il report di analisi per **[!UICONTROL Application for Child Support Services]**. Puoi visualizzare i dati iniziali nel rapporto generato.

