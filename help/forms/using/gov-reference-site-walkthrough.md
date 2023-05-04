---
title: Procedura dettagliata sul sito di riferimento We.Gov
seo-title: We.Gov reference site walkthrough
description: Consulta la procedura dettagliata sul sito di riferimento We.Gov per comprendere in che modo AEM Forms aiuta i governi a gestire le informazioni individuali.
seo-description: See the We.Gov reference site walkthrough to understand how AEM Forms helps governments manage individual information.
uuid: 348f9067-28b5-47ed-8e83-0dbadeff0854
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 25a6d702-9995-4c63-99d8-3e5d710bb0c4
exl-id: c8ebd18b-fa24-4264-bd17-f553a2a784d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2753'
ht-degree: 0%

---

# Procedura dettagliata sul sito di riferimento We.Gov {#we-gov-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Prerequisito {#pre-requisite}

Imposta il tuo sito di riferimento We.Gov come descritto in [Configurare e configurare i siti di riferimento di AEM Forms](/help/forms/using/setup-reference-sites.md).

## Scenario di riferimento del sito {#reference-site-scenario}

We.Gov è un&#39;organizzazione statale che permette ai genitori adottivi di iscriversi al supporto dei figli se hanno adottato un bambino. Il sito gestisce quanto segue:

* Ammissibilità del richiedente, della controllante adottiva
* Dati personali e professionali del richiedente (se il richiedente può beneficiare di un sostegno per i figli)
* Dati personali del minore adottato

   Il richiedente può fornire dettagli su più di un figlio
* Informazioni sul conto bancario del richiedente in cui il richiedente può ricevere prestazioni di sostegno ai figli
* Recupero del canone
* Valutazione della domanda
* Approvazione della domanda
* Comunicazione automatizzata al richiedente

Una volta presentata la domanda e pagata la relativa tassa, il richiedente riceve un&#39;e-mail dall&#39;organizzazione con l&#39;accettazione della domanda presentata.

L&#39;organizzazione We.Gov riceve l&#39;applicazione. L&#39;organizzazione ottiene la valutazione dell&#39;applicazione e approva le applicazioni che sono autentiche.

Dopo l&#39;approvazione della domanda, il richiedente riceve un&#39;e-mail dal sito We.Gov. La **Visualizza documento** nell&#39;e-mail si collega a un documento con i dettagli di iscrizione del richiedente.

L’infografica seguente mostra il flusso di lavoro dettagliato dello scenario del sito di riferimento We.Gov.

![workflow_aem_gov_2](assets/workflow_aem_gov_2.png)

Lo scenario include i seguenti utenti tipo:

* Sarah Rose, il genitore adottivo che richiede supporto per bambini
* Joe, il bambino adottato
* Gloria Rios, capo della divisione di approvazione, We.Gov
* Conard Simms, l&#39;agente sul campo che si occupa della valutazione dell&#39;applicazione

## Sarah avvia il suo controllo di idoneità {#sarah-initiates-her-eligibility-check}

Un richiedente può verificare l’idoneità per richiedere prestazioni di supporto per bambini. Il sito consente agli utenti di rispondere alle domande per consentire loro di determinare se la loro applicazione è idonea ai benefici. Sarah, una genitore adottiva, è una potenziale richiedente per esso. Il modulo di idoneità fa parte dell&#39;applicazione per servizi di supporto per bambini del sito We.Gov. Per verificare la sua idoneità, Sarah fa clic su **[!UICONTROL Supporto per bambini]** sul sito web We.Gov. Nella pagina Supporto figlio, Sarah fa clic su **[!UICONTROL Controllare l&#39;idoneità]**.

Oltre all&#39;approccio di cui sopra, Sarah può fare clic su **[!UICONTROL Introduzione]** sulla homepage. Sarah viene visualizzata nella pagina Tutte le applicazioni, in cui può fare clic su Applica in **[!UICONTROL Applicazione per servizi di supporto per bambini]**. Sarah viene quindi sottoposta al controllo di idoneità.

Nella pagina Verifica idoneità per il supporto figlio , a Sarah viene richiesto un insieme di domande per determinare la sua idoneità per i benefici di supporto per i bambini. Attraverso la serie di domande, le si chiede:

* Se è il genitore custodito del figlio
* Se lei e il bambino vivono nello stato di GX
* La fascia d&#39;età dell&#39;istruzione infantile e infantile.

Sarah risponde a queste domande e la sua idoneità viene convalidata. Le sue risposte determinano se ha diritto al supporto per i bambini.

Sarah viene informata che può usufruire del sostegno per i bambini e che la tassa di iscrizione è di 25 dollari.

### Come funziona {#how-it-works}

L&#39;idoneità di Sarah viene convalidata tramite una barriera di idoneità creata utilizzando l&#39;editor di regole. L’editor delle regole consente di specificare le condizioni che vengono soddisfatte prima che un richiedente possa compilare il modulo di domanda. Quando Sarah, la ricorrente, soddisfa tutte le condizioni di ammissibilità, si iscrive nel modulo di domanda.

Il controllo di idoneità fa parte del modulo adattivo dell’applicazione di supporto figlio. La regola convalida l&#39;idoneità quando:

* Il richiedente è una controllante depositaria
* Il richiedente e il bambino soggiornano nello stato di GX
* Il richiedente ha la cura principale giorno per giorno del bambino
* L&#39;età del bambino che riceve servizi di assistenza è sotto i 16 anni.

### Vedi di persona {#see-it-yourself}

Nel browser, apri `https://<hostname>:<PublishPort>/content/we-gov/en.html`. Nel sito We.Gov, fai clic su Supporto figlio. Nella pagina Supporto figlio fare clic su Verifica idoneità.

Per visualizzare le regole:

1. Apri il modulo in modalità di modifica nell’istanza di authoring. URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`.
1. Seleziona un componente e fai clic su ![edit-rules](assets/edit-rules.png).

   Viene visualizzato l’Editor regole in cui sono elencate tutte le regole applicate nel modulo.

1. Nel pannello laterale sinistro, fai clic su regole `passMsg` e `failMsg` per comprendere come funziona il controllo di idoneità.

## Sarah avvia la sua applicazione per il supporto dei bambini {#sarah-starts-her-application-for-child-support}

Sarah clicca **[!UICONTROL Avvia applicazione]** dopo essere stata informata della sua idoneità per il sostegno ai bambini.\
Nella pagina Application For Child Support Services , Sarah fornisce i dettagli nelle sezioni seguenti:

* **[!UICONTROL Informazioni sul richiedente]**: Lascia che Sarah fornisca i suoi dettagli in questa sezione.

* **[!UICONTROL Informazioni sui bambini]**: Lascia che Sarah fornisca le informazioni del bambino, che è coperto dai servizi di supporto.

* **[!UICONTROL Pagamento]**: Lascia che Sarah fornisca i suoi dati bancari in cui We.Gov può depositare il risarcimento mensile del supporto.

* **[!UICONTROL Pagamento a pagamento]**: Permette a Sarah di fornire i dati della sua carta di credito da pagare per la tassa di iscrizione.

Per impostazione predefinita, Sarah viene portata al **[!UICONTROL Informazioni sul richiedente]** sezione .

![Applicazione di supporto per bambini sul desktop](assets/desktop.png)

In qualsiasi momento Sarah può fare clic su **[!UICONTROL Torna più tardi]** e riprendere con la sua domanda. Quando scatta **[!UICONTROL Torna più tardi]**, i suoi progressi vengono salvati come bozza e ottiene un&#39;opzione per inviare la bozza via e-mail.

Quando scatta **[!UICONTROL Invia e-mail]**, riceve un&#39;e-mail con un collegamento alla bozza del modulo.

Il modulo di supporto figlio sul sito We.Gov utilizza moduli adattivi. Può usare il collegamento nella sua e-mail e compilare il modulo sul suo dispositivo mobile.

>[!NOTE]
>
>Il flusso di lavoro di ripresa da e-mail funziona solo con gli utenti registrati. Nello scenario relativo al sito di riferimento, assicurati che l’utente Sarah Rose sia aggiunto. Le credenziali di accesso di Sarah sono `srose/password`.

![mob1](assets/mob1.png)

Sarah può fornire i dettagli in qualsiasi sezione, ma la tassa di iscrizione viene accettata solo dopo aver fornito le informazioni richieste in tutte le sezioni. Una domanda è incompleta senza pagamento a pagamento, e i campi contrassegnati con un asterisco sono obbligatori.

### <strong>Sarah fornisce le sue informazioni</strong> {#strong-sarah-provides-her-information-strong}

Dopo che Sarah clicca **[!UICONTROL Avvia applicazione]**, viene portata alla sezione Informazioni richiedente della pagina Richiesta di servizi di assistenza figlio. Alla voce Informazioni richiedente, Sarah naviga attraverso le schede e fornisce le sue informazioni personali per la domanda. Lei clicca **[!UICONTROL Successivo]** per navigare tra le schede.

In Richiedente Information, le viene chiesto di fornire i dettagli sotto le seguenti schede:

* **[!UICONTROL Informazioni di base]**

In Informazioni di base, Sarah fornisce la sua prova d&#39;identità e le sue informazioni personali. Le informazioni personali di Sarah includono il suo nome, l’ID e-mail e il numero di previdenza sociale.

* **[!UICONTROL Relazione]**

   Sotto la relazione, Sarah inserisce informazioni sul suo stato civile.

* **[!UICONTROL Informazioni aggiuntive]**

   In Ulteriori informazioni, Sarah immette un numero di identificazione, la data di nascita e l&#39;indirizzo e il numero di telefono attuali.

### Sarah fornisce informazioni sui bambini {#sarah-provides-child-information}

Dopo che Sarah fornisce le sue informazioni personali e i suoi clic **[!UICONTROL Successivo]**, viene portata alla sezione Informazioni sui bambini .

Nella sezione Informazioni sui bambini , fornisce i seguenti dettagli:

* Numero di figli da richiedere servizi di assistenza ai figli
* Nome del bambino, numero di previdenza sociale, data di nascita e luogo di nascita

Se Sarah sceglie più di un bambino, le vengono abilitati dei moduli aggiuntivi con gli stessi dettagli da compilare.\
Sarah sceglie il suo figlio unico, Joe, e immette il suo nome.

### Sarah fornisce informazioni sul pagamento {#sarah-provides-payment-information}

Dopo che Sarah fornisce informazioni sul bambino adottato (o bambini) e i clic **[!UICONTROL Successivo]**, viene portata al **[!UICONTROL Informazioni sul pagamento]** sezione .

Nella sezione Informazioni di pagamento, fornisce i dettagli del conto bancario in cui può ricevere i benefici di supporto per i bambini.\
Entra nel suo numero di conto bancario di dieci cifre.

## Sarah paga la tassa di iscrizione e firma il modulo {#sarah-pays-the-application-fee-and-signs-the-form}

Dopo che Sarah accetta i termini e le condizioni della domanda, paga la tassa di applicazione di $25. Per l&#39;elaborazione della sua domanda è richiesto il pagamento di una tassa.\
Sarah entra nei dettagli della sua carta di credito e clicca **[!UICONTROL Paga ora]**. Dopo aver pagato le tariffe, viene visualizzata una versione PDF dell’applicazione con un campo firma.

![segno di sarah-1](assets/sarah-sign-1.png)

Sarah può scegliere di digitare, utilizzare draw to handwrite, inserire un&#39;immagine di firma o utilizzare il touchscreen del suo cellulare per disegnare la sua firma. Sarah digita il suo nome e fa clic su Fai clic per firmare.

La sua domanda viene inoltrata al sito We.Gov.

### <strong>Sarah riceve un&#39;e-mail di riconoscimento</strong> {#strong-sarah-receives-an-acknowledgement-email-strong}

Dopo che Sarah pagherà la tassa di iscrizione, riceve un&#39;e-mail di conferma dal sito We.Gov.\
We.Gov elabora l&#39;applicazione e Sarah viene informata che riceverà un risarcimento mensile dopo l&#39;approvazione della sua domanda.

![sarah-ack-email](assets/sarah-ack-email.png)

### Come funziona {#how-it-works-1}

L’applicazione di supporto figlio utilizza una combinazione di layout di pannelli quali scheda superiore, procedura guidata e pannello a soffietto per creare l’esperienza. Utilizza un modello di modulo denominato Modello figlio We.Gov.

Il richiedente può spostarsi tra le sezioni per compilare diversi componenti del modulo. Quando il richiedente compila il modulo, lo invia, accetta i termini e le condizioni e paga la tariffa, viene avviato un flusso di lavoro personalizzato. Il flusso di lavoro personalizzato invia un messaggio e-mail automatizzato al richiedente che conferma l’invio della domanda. La domanda viene inoltrata al servizio competente dell&#39;organizzazione per la verifica e l&#39;approvazione.

Il layout del modulo è specificato nel Tema relativo al servizio di assistenza figlio Gov. Lo stile include lo stile del componente, lo sfondo della pagina, la formattazione dello stato di errore dei componenti e gli stili dei font.

Il controllo di idoneità utilizza le regole specificate nel modulo. Utilizza i controlli di validità specificati di seguito:

`SHOW passMsgWHEN (Does the child live in the state of GX? is equal to Yes) AND (Do you live in the state of GX? is equal to Yes) AND ( (Who has the main day-to-day care of the child? is equal to You) AND (Are you: is equal to The custodial parent) ) AND (Is the child you are applying for: is equal to Under 16 years) ELSE Hide`

`HIDE failMsg WHEN (Does the child lives in the state of GX? is equal to Yes) AND ( (Do you live in the state of GX? is equal to Yes) AND (Who has the main day-to-day care of the child? is equal to You) ) AND (Is the child you are applying for: is equal to Under 16 years) AND (Are you: is equal to The custodial parent) ELSE Show`

### Vedi di persona {#see-it-yourself-1}

Nel browser, apri `https://<hostname>:<PublishPort>/content/forms/af/we-gov/child-support/css.html` e compilare le informazioni richieste. Quando si invia l&#39;applicazione dopo aver compilato le informazioni richieste, pagare le tariffe e firmare il documento, si riceve l&#39;e-mail di conferma.

Vedi il modello figlio We.Gov qui: `https://<hostname>:<AuthorPort>/editor.html/conf/we-gov/settings/wcm/templates/we-gov-child-template/structure.html`

Vedi il tema qui: `https://<hostname>:<AuthorPort>/editor.html/content/dam/formsanddocuments-themes/we-gov/we-gov-theme-A/jcr:content`

Per visualizzare tutte le regole, esegui le seguenti operazioni:

1. Aprire il modulo in modalità di authoring.

   URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`

1. Seleziona un componente e tocca ![edit-rules](assets/edit-rules.png). Tutte le regole sono elencate nell’editor delle regole, incluse quelle elencate in precedenza.

## Gloria riceve l&#39;applicazione {#gloria-receives-the-application}

Gloria, responsabile delle approvazioni di We.Gov, può visualizzare, approvare o rifiutare le richieste inviate. AEM casella in entrata consente di visualizzare tutte le applicazioni inviate in un’unica posizione.

### Come funziona {#how-it-works-2}

Quando Sarah compila e invia l&#39;applicazione di supporto ai bambini, viene creato un PDF o un documento di registrazione dell&#39;applicazione e inviato alla casella in entrata di Gloria Rios. Gloria può visualizzare la domanda inviata e accettarla o rifiutarla.

### Vedi di persona {#see-it-yourself-2}

Apri pagina `https://<hostname***>:<PublishPort>/content/we-gov/en.html`. Sulla pagina, tocca **[!UICONTROL Accesso]**, seleziona **[!UICONTROL Accedi come rappresentante]** casella di controllo, accedi alla casella in entrata AEM utilizzando grios/password come nome utente/password per Gloria Rios. Viene visualizzata l&#39;applicazione di supporto figlio. Per informazioni sull’utilizzo della casella in entrata AEM per le attività del flusso di lavoro incentrate sui moduli, vedere [Gestione di applicazioni e attività Forms nella casella in entrata AEM](/help/forms/using/manage-applications-inbox.md).

![Posta in arrivo di Gloria nel refsite di We.Gov](assets/gloria-inbox.png)

Gloria può visualizzare, approvare o rifiutare l&#39;applicazione dal dashboard dell&#39;applicazione.

### Come funziona {#how-it-works-3}

Gloria, responsabile delle approvazioni di We.Gov, apre la sua casella in entrata AEM. Vede un compito di revisione nel suo elenco di compiti. Apre e visualizza l&#39;attività di revisione.

Vede un PDF del modulo compilato con i dettagli che Sarah ha inserito insieme ai documenti che Sarah ha caricato.\
Gloria può approvare o rifiutare la domanda. Tuttavia, i clic di Gloria **[!UICONTROL Valutazione richiesta]** per la valutazione della domanda.

![valutazione degli invii di gloria](assets/gloria-sends-assessment.png)

L&#39;applicazione di Sarah è un punto di partenza nel flusso di lavoro AEM. Avvia il flusso di lavoro AEM quando viene inviato il modulo di richiesta di supporto figlio. Il flusso di lavoro AEM crea un&#39;attività per Gloria, che compare nella sua casella di posta AEM. Quando Gloria richiede la valutazione in loco, viene creata una nuova attività per l&#39;agente di campo.

### Vedi di persona {#see-it-yourself-3}

Se la configurazione è completa, il flusso di lavoro AEM inizia immediatamente dopo l’invio del modulo. Accedi alla inbox utilizzando le credenziali di Gloria.

Accedi alla casella in entrata all’indirizzo https://&lt;***hostname***>:&lt;***PublishPort***>/content/we-gov/en.html. Sulla pagina, tocca **[!UICONTROL Accesso]**, seleziona **[!UICONTROL Accedi come rappresentante]** utilizza le credenziali predefinite di Gloria:

* Nome utente: grios
* Password: password

Nella sua casella in entrata AEM, l&#39;applicazione di Sarah viene aggiunta come attività di revisione. Seleziona l’attività e fai clic su **Valutazione richiesta** per passare al passaggio successivo.

### Conard ottiene l&#39;attività Valutazione {#conard-assessment-task}

Quando Gloria clicca **[!UICONTROL Valutazione richiesta]**, Conard ottiene l’attività di revisione nella sua casella in entrata AEM. L’attività rappresenta il passaggio successivo nel flusso di lavoro AEM definito nel modello di flusso di lavoro. Vede il compito di revisione e lo apre.

Conard ottiene il compito di valutazione del richiedente come mostrato di seguito.

![casella in entrata](assets/conrad-inbox.png)

La valutazione del supporto figlio è un modulo associato all&#39;attività. Riceve i dettagli di Sarah, insieme ai documenti giustificativi (allegati nei dettagli del compito). Conard compila il modulo di valutazione nel campo di un dispositivo e si sottomette per la rivalutazione.

Conard verifica tutti i dettagli forniti da Sarah e Sarah firma la valutazione. AEM Forms può prendere la posizione e la marca temporale e aggiungerli alla firma.

![presentare per una nuova valutazione](assets/submit-for-re-evaluation.png)

Clic su scheda **[!UICONTROL Invia per rivalutazione]** e il flusso di lavoro AEM invia la valutazione all’organizzazione We.Gov.

### Come funziona {#how-it-works-4}

Quando Gloria richiede la valutazione, viene avviato il passaggio successivo AEM flusso di lavoro e l’attività di valutazione viene aggiunta nella casella in entrata di Conard. Conard è l&#39;utente che lavora sul campo.

Conard visita il posto di Sarah, verifica che le informazioni fornite da Sarah siano autentiche e compila il modulo di valutazione. Conard può accedere a un PDF del modulo completo che Sarah ha compilato.

### Vedi di persona {#see-it-yourself-4}

Apri la casella in entrata AEM sul tablet e utilizza le credenziali di Conard per accedere.

Le credenziali predefinite di Conard sono:

* Nome utente: csimms
* Password: password

Nella casella in entrata è stata aggiunta una nuova attività di richiesta di valutazione. Invia la valutazione completata e procedi al passaggio successivo.

### Gloria esamina la valutazione e approva la domanda {#gloria-reviews-the-assessment-and-approves-the-application}

Dopo che Conard presenta la valutazione, Gloria vede un compito di revisione nella sua casella in entrata. Seleziona e apre **[!UICONTROL Revisione]**.

![gloriainbox-1](assets/gloriainbox-1.png)

In Dettagli attività, Gloria vede l&#39;ultima azione intrapresa come &quot;Invia per nuova valutazione&quot; (da Conard). Gloria vede che Conard Simms ha valutato la domanda.

![gloriaapproves](assets/gloriaapproves.png)

### Come funziona {#how-it-works-5}

Dopo che Conard presenta la valutazione, Gloria vede un compito di revisione nella sua casella in entrata. Seleziona e apre Review. Sotto Task Details, Gloria vede il commento di valutazione fatto da Conard, che è &quot;Tutto trovato in ordine&quot;.

Gloria approva la domanda.

### Vedi di persona {#see-it-yourself-5}

Apri la casella in entrata e accedi utilizzando le credenziali di Gloria. Nella casella in entrata viene visualizzata una nuova attività denominata Revisione.

Apri l’attività per visualizzare lo stato dell’ultima azione eseguita. Sulla base della valutazione, approva la domanda.

## Sarah riceve un&#39;e-mail di approvazione {#sarah-receives-an-approval-email}

Dopo che Gloria ha approvato l&#39;applicazione, Sarah riceve una e-mail da We.Gov che la sua applicazione è approvata.

La **[!UICONTROL Visualizza documento]** nell&#39;e-mail si collega ai relativi dettagli di iscrizione. Sarah clicca **[!UICONTROL Visualizza documento.]**

![approvazione-iscrizione-kit-email](assets/approval-enrolment-kit-email.png)

Il documento di registrazione elenca dettagli quali l&#39;ID di riferimento, l&#39;ID figlio coperto, la data di inizio, il numero del conto bancario, la frequenza di pagamento e l&#39;importo del pagamento.

![iscrizione sarah-dettagli](assets/sarah-enrollment-details.png)

Sarah può visualizzare i documenti che ha caricato sulla stessa pagina.

![documenti caricati](assets/uploaded-documents.png)

### Come funziona {#how-it-works-6}

Quando Gloria approva l&#39;applicazione, Sarah riceve un&#39;e-mail automatica con un collegamento al documento di iscrizione.

Il documento di registrazione è una comunicazione interattiva e può essere visualizzato su qualsiasi dispositivo. Contiene i dettagli del servizio di assistenza ai bambini e le informazioni fornite da Sarah.

### Vedi di persona {#see-it-yourself-6}

Controlla il client e-mail configurato per l’e-mail automatica con un collegamento al documento di iscrizione.

In alternativa, per visualizzare il documento nel browser, apri: `https://<hostname>:<PublishPort>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-gov/child-support/enrollment-document&referenceId=[reference-id]&channel=web`

## We.Gov analizza le prestazioni dell&#39;applicazione {#we-gov-analyzes-the-performance-of-the-application}

We.Gov, di tanto in tanto, esamina le prestazioni della loro applicazione di servizi di supporto per bambini per verificare eventuali problemi che i clienti potrebbero affrontare. Essi utilizzano questa analisi per prendere decisioni informate sui cambiamenti richiesti nell’applicazione servizi di assistenza ai bambini per migliorare l’esperienza utente, ridurre il tasso di abbandono dei moduli e quindi migliorare la conversione. Sfruttano l’integrazione di AEM Forms con Adobe Analytics per la loro analisi. L&#39;immagine seguente mostra il loro dashboard di analisi.

![child-support-analytics-dashboard](assets/child-support-analytics-dashboard.png)

### Come funziona {#how-it-works-7}

Le metriche delle prestazioni per il modulo dell’applicazione servizi di supporto figlio vengono tracciate utilizzando Adobe Analytics. Per ulteriori informazioni sulla configurazione di Adobe Analytics e sulla visualizzazione dei rapporti, vedi [Configurazione di analytics per moduli e documenti](/help/forms/using/configure-analytics-forms-documents.md).

### Vedi di persona {#see-it-yourself-7}

Per visualizzare ed esplorare il rapporto di analisi, forniamo i dati seed per l’applicazione dei servizi di supporto figlio nel sito di riferimento. Prima di utilizzare i dati di seed, consulta [Configurare Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). Esegui i seguenti passaggi nell’istanza di authoring per visualizzare il rapporto con i dati di seed:

1. Vai a **[!UICONTROL Forms e documenti]** Interfaccia utente all’indirizzo https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments .

1. Fai clic per aprire **We.Gov** Cartella.
1. Seleziona **[!UICONTROL Applicazione per servizi di supporto per bambini]** modulo adattivo e fai clic su **[!UICONTROL Abilitare Analytics]** nella barra degli strumenti.

1. Selezionare nuovamente il modulo e fare clic su **[!UICONTROL Rapporto di Analytics]** nella barra degli strumenti per generare il rapporto. Viene visualizzato inizialmente un rapporto vuoto.

Per generare un rapporto di analisi con dati di seed:

1. Nel browser degli indirizzi di CRXDE lite, digita: **/apps/we-gov/demo-artifact/analyticsTestData/Child Support service Analytics Test Data**
1. I dati seed vengono selezionati nella struttura della directory laterale sinistra.
1. Fai doppio clic sul file selezionato per aprirne il contenuto nel pannello laterale destro.
1. Copia tutto il contenuto nel file di dati di prova.
1. In CRXDE, passa a: **/content/dam/formsanddocuments/we-gov/child-support/css/jcr:content/analyticsdatanode/lastsevendays**
1. Nel campo analyticsdata in Proprietà, incolla il contenuto copiato del file di dati di prova.
1. Ora genera di nuovo un rapporto di analisi per **[!UICONTROL Applicazione per servizi di supporto per bambini]**. Puoi visualizzare i dati seed nel rapporto generato.
