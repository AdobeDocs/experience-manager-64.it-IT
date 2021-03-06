---
title: Procedura dettagliata sul sito di riferimento self-service dei dipendenti
seo-title: Self-service dipendente
description: ' sito di riferimento AEM Forms mostra come le organizzazioni possono sfruttare  funzioni di AEM Forms per implementare flussi di lavoro di assunzione e self-service dei dipendenti.'
seo-description: ' sito di riferimento AEM Forms mostra come le organizzazioni possono sfruttare  funzioni di AEM Forms per implementare flussi di lavoro di assunzione e self-service dei dipendenti.'
uuid: ecc98e0d-c964-44dc-b219-9ebe92632d22
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d2695f71-5126-477c-ae6b-a964fb55728b
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d
workflow-type: tm+mt
source-wordcount: '1644'
ht-degree: 0%

---


# Procedura dettagliata sul sito di riferimento self-service dipendente{#employee-self-service-reference-site-walkthrough}

## Prerequisito {#prerequisite}

Configurare i siti di riferimento come descritto in [Configurare e configurare  siti di riferimento AEM Forms](/help/forms/using/setup-reference-sites.md).

## Panoramica {#overview}

I sistemi self-service dei dipendenti, generalmente ospitati sulla Intranet aziendale, consentono ai dipendenti di accedere a una serie di informazioni e servizi che possono utilizzare dai loro uffici. Offre ai dipendenti il controllo completo sulle operazioni da eseguire, ad esempio l&#39;accesso ai dati sul lavoro, la richiesta di congedo e l&#39;invio di note spese. Dall&#39;altro lato, aiuta le organizzazioni a migliorare l&#39;efficienza dei processi e a ridurre i costi, mantenendo i dipendenti informati e impegnati.

Il sito di riferimento self-service dei dipendenti mostra come sfruttare  AEM Forms per implementare il sistema di self-service dei dipendenti nella tua organizzazione.

>[!NOTE]
>
>I casi di utilizzo self-service dei dipendenti sono disponibili sia nei siti di riferimento We.Finance che We.Gov. Gli esempi, le immagini e le descrizioni utilizzati nelle procedure dettagliate utilizzano il sito di riferimento We.Finance. Tuttavia, potete eseguire questi casi di utilizzo e rivedere gli artifact utilizzando anche We.Gov. A tal fine, ?? necessario sostituire **we-finance** con **we-gov** negli URL indicati.

## Procedura dettagliata del questionario sul conflitto di interessi {#conflict-of-interest-questionnaire-walkthrough}

Di tanto in tanto, le organizzazioni chiedono ai propri dipendenti di inviare un questionario sul conflitto di interessi per identificare le attivit?? esterne o i rapporti personali dei loro dipendenti che possono potenzialmente entrare in conflitto con la loro organizzazione.

Il reparto Conformit?? dell&#39;organizzazione di Sarah ha chiesto ai dipendenti di inviare il questionario sul conflitto di interessi.

### Sarah invia il questionario sul conflitto di interessi {#sarah-submits-the-conflict-of-interest-questionnaire}

Sarah passa al portale aziendale, accede e fa clic su Dipendente per accedere al dashboard del dipendente. Trova il questionario sul conflitto di interessi nel dashboard del dipendente e fai clic su **[!UICONTROL Applica]**.

![we-finance-](assets/we-finance-home.png)
**homeFigure:portale** *dell&#39;organizzazione*

![dipendente-](assets/employee-dashboard.png)
**dashboardFigura:dashboard** *dipendente*

Sarah naviga nel modulo utilizzando il pulsante Avanti e legge le sezioni Introduzione e Definizione. Risponde alle domande nella sezione Domande. Infine firma e invia il questionario.

Il portale dell&#39;organizzazione e il questionario sono reattivi e facili da usare per i dispositivi mobili. Il seguente flusso di lavoro mostra come Sarah esplora e invia il questionario sul suo dispositivo mobile.

![modulo in conflitto su dispositivo mobile](assets/conflict-form-on-mobile.png)

**Come funziona**

Il portale dell&#39;organizzazione e il dashboard del dipendente sono  pagine AEM Sites. Il dashboard elenca diverse opzioni self-service, come il questionario sui conflitti di interessi. Il pulsante Applica ?? collegato a un modulo adattivo.

Il modulo adattivo utilizza delle regole per mostrare o nascondere le informazioni in base alla risposta fornita nella scheda Domande. Inoltre, il modulo utilizza il componente Scribble per accedere alla scheda Dichiarazione. Esaminare il modulo adattivo in `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/conflict-of-interest.html`.

**Vedi te stesso**

Andate a `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` ed effettuate l&#39;accesso utilizzando `srose/srose` come nome utente/password per Sarah. Fare clic su **[!UICONTROL Dipendente]** per accedere al dashboard, quindi fare clic su **[!UICONTROL Applica]** al questionario sui conflitti di interesse. Riesaminare e presentare il questionario.

### Gloria esamina e approva il questionario sul conflitto di interessi inviato {#gloria-reviews-and-approves-the-conflict-of-interest-questionnaire-submission}

Il questionario sul Conflitto di interessi presentato da Sarah ?? assegnato a Gloria Rios per un riesame. Gloria lavora come Responsabile per la conformit?? nell&#39;organizzazione. Gloria accede alla propria casella AEM Posta in arrivo e rivede i compiti che le sono stati assegnati. Approva il questionario presentato da Sarah e completa il compito.

![Conflitto-](assets/conflict-inbox.png)
**inboxFigure:inbox di** *Gloria*

![conflittuale-](assets/conflict-approved.png)
**approvatoFigura:** *Apri attivit??*

**Come funziona**

L&#39;azione di invio nel questionario sul conflitto di interessi attiva un flusso di lavoro che crea un&#39;attivit?? nella inbox di Gloria per l&#39;approvazione. Rivedete l&#39;Forms Workflow all&#39;indirizzo `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-conflict-of-interest.html`

![sede di riferimento personale](assets/employee-self-service-reference-site.png)

**Vedi te stesso**

Andate a `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` ed effettuate l&#39;accesso utilizzando `grios/password` come nome utente/password per Gloria Rios. Aprite l&#39;attivit?? creata per il questionario sul conflitto di interessi e approvatela.

## Procedura dettagliata per l&#39;applicazione di schede aziendali {#corporate-card-application-walkthrough}

Sarah viaggia molto per lavoro e richiede una carta di credito aziendale per pagare le sue bollette in movimento. Fa domanda per una carta aziendale tramite il portale aziendale dei dipendenti.

### Sarah invia l&#39;applicazione della carta d&#39;identit?? {#sarah-submits-the-corporate-card-application}

Sarah passa al portale aziendale, accede e fa clic su **[!UICONTROL Dipendente]** per accedere al dashboard del dipendente. Trova l&#39;applicazione Carta aziendale nel dashboard del dipendente e fai clic su **[!UICONTROL Applica]**.

![we-finance-home-1](assets/we-finance-home-1.png)
**Figure:Portale** *organizzazione*

![dipendente-dashboard-1](assets/employee-dashboard-1.png)
**Figura:Pannello** *dipendente*

Fa clic su **[!UICONTROL Applica]** nell&#39;applicazione della scheda aziendale. Viene aperta un???applicazione a pagina singola. Compila tutti i dettagli e fa clic su **[!UICONTROL Applica]** per inviare l&#39;applicazione.

![scheda](assets/card-form.png)

**Come funziona**

Il portale dell&#39;organizzazione e il dashboard del dipendente sono  pagine AEM Sites. Il dashboard elenca diverse opzioni self-service, come l&#39;applicazione scheda aziendale. Il pulsante Applica dell&#39;applicazione ?? collegato a un modulo adattivo.

Il modulo adattivo per l&#39;applicazione con scheda aziendale ?? un modulo adattivo, semplice, di una pagina e reattivo. Utilizza componenti di base per moduli adattivi come testo, telefono, caselle numeriche e passaggi numerici. Esaminate il modulo adattivo all&#39;indirizzo:\
`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/corporate-card.html`.

**Vedi te stesso**

Andate a `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` ed effettuate l&#39;accesso utilizzando `srose/srose` come nome utente/password per Sarah. Fare clic su **[!UICONTROL Dipendente]** per accedere al dashboard, quindi fare clic su **[!UICONTROL Applica]** nell&#39;applicazione Carta aziendale. Compila i dettagli e invia la domanda.

### Gloria esamina e approva l&#39;applicazione scheda aziendale {#gloria-reviews-and-approves-the-corporate-card-application}

La richiesta di carta aziendale inviata da Sarah ?? assegnata a Gloria Rios per la revisione. Gloria accede alla propria casella AEM Posta in arrivo e rivede i compiti che le sono stati assegnati. Approva la richiesta presentata da Sarah e completa il compito.

![corporate-card-](assets/corporate-card-inbox.png)
**inboxFigure:inbox di** *Gloria*

![scheda aziendale-](assets/corporate-card-approved.png)
**approvatoFigura:** *Apri attivit??*

**Come funziona**

Il flusso di lavoro di invio nell&#39;applicazione Card aziendale attiva un flusso di lavoro Forms che crea un&#39;attivit?? nella inbox di Gloria per l&#39;approvazione. Rivedete l&#39;Forms Workflow all&#39;indirizzo `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-corporate-card.html`

![scheda aziendale-workflow-model](assets/corporate-card-workflow-model.png)

**Vedi te stesso**

Andate a `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` ed effettuate l&#39;accesso utilizzando `grios/password` come nome utente/password per Gloria Rios. Aprite l&#39;attivit?? creata per l&#39;applicazione Carta aziendale e approvatela.

## Procedura dettagliata per l&#39;invio della nota spese {#expense-report-submission-walkthrough}

Mentre Sarah spende durante i viaggi d&#39;affari, deve inviare le note spese per l&#39;approvazione. L&#39;opzione self-service nella sua organizzazione le consente di inviare la nota spese online.

### Sarah invia l&#39;applicazione nota spese {#sarah-submits-the-expense-report-application}

Sarah passa al portale aziendale, accede e fa clic su **[!UICONTROL Dipendente]** per accedere al dashboard del dipendente. Trova l&#39;applicazione nota spese nel dashboard del dipendente e fa clic su **[!UICONTROL Applica]**.

![we-finance-home-2](assets/we-finance-home-2.png)
**Figure:Portale** *organizzazione*

![coi dipendenti-dashboard-2](assets/employee-dashboard-2.png)
**Figura:** *Pannello dei dipendenti*

Fare clic su **[!UICONTROL Applica]** nell&#39;applicazione Nota spese. Si apre un modulo di applicazione, con due schede: Nome rapporto e Dettagli rapporto. L&#39;icona **+** nella scheda Dettagli rapporto consente di aggiungere pi?? spese in un rapporto.

Il portale dell&#39;organizzazione e le applicazioni sono reattivi e facili da usare per i dispositivi mobili. Il seguente flusso di lavoro mostra come Sarah esplora e invia la nota spese sul suo dispositivo mobile.

![resoconto spese per dispositivi mobili](assets/expense-report-on-mobile.png)

**Come funziona**

Il portale dell&#39;organizzazione e il dashboard del dipendente sono  pagine AEM Sites. Il dashboard elenca diverse opzioni self-service, come l&#39;applicazione nota spese. Il pulsante Applica ?? collegato a un modulo adattivo.

Le schede Nome rapporto e Dettagli rapporto nel modulo adattivo sono componenti Pannello. Il pannello Dettagli rapporto contiene il pannello Spese. Si tratta di un pannello ripetibile che consente di aggiungere pi?? spese nel rapporto. Esaminare il modulo adattivo e le relative configurazioni in `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/expense-report.html`.

**Vedi te stesso**

Andate a `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` ed effettuate l&#39;accesso utilizzando `srose/srose` come nome utente/password per Sarah. Fare clic su **[!UICONTROL Dipendente]** per accedere al dashboard, quindi fare clic su **[!UICONTROL Applica]** nell&#39;applicazione Nota spese. Compila i dettagli e invia la domanda.

### Gloria esamina e approva la nota spese {#gloria-reviews-and-approves-the-expense-report}

La nota spese inviata da Sarah ?? assegnata a Gloria Rios per la revisione. Gloria accede alla propria casella AEM Posta in arrivo e rivede i compiti che le sono stati assegnati. Approva la richiesta presentata da Sarah e completa il compito.

![cost-report-](assets/expense-report-inbox.png)
**inboxFigure:inbox di** *Gloria*

![nota spese-rapporto-](assets/expense-report-approved.png)
**approvatoFigura:** *Apri attivit??*

**Come funziona**

Il flusso di lavoro di invio nell&#39;applicazione Nota spese attiva un flusso di lavoro Forms che crea un&#39;attivit?? nella inbox di Gloria per l&#39;approvazione. Rivedete l&#39;Forms Workflow all&#39;indirizzo `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-expense-report-workflow.html`

![scheda aziendale-cost-report-workflow-model](assets/corporate-card-expense-report-workflow-model.png)

**Vedi te stesso**

Andate a `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` ed effettuate l&#39;accesso utilizzando `grios/password` come nome utente/password per Gloria Rios. Aprire l&#39;attivit?? creata per l&#39;applicazione nota spese e approvarla.

## Esclusione della procedura dettagliata dell&#39;applicazione {#leave-application-walkthrough}

Sarah sta pianificando una vacanza in famiglia il mese prossimo e vuole fare domanda per una settimana di congedo dal lavoro.

### Sarah invia l&#39;applicazione di congedo {#sarah-submits-the-leave-application}

Sarah passa al portale aziendale, accede e fa clic su **[!UICONTROL Dipendente]** per accedere al dashboard del dipendente. Trova di lasciare l&#39;applicazione sul dashboard del dipendente e fare clic su **[!UICONTROL Applica]**.

![we-finance-home-3](assets/we-finance-home-3.png)
**Figure:Portale** *organizzazione*

![coi dipendenti-dashboard-3](assets/employee-dashboard-3.png)
**Figura:** *Pannello dei dipendenti*

Si apre l&#39;applicazione di congedo con il nome di Sarah e l&#39;ID dipendente precompilati nel modulo. Mostra anche l&#39;equilibrio e la storia del suo congedo. Compila i dettagli del congedo e presenta la domanda di approvazione.

Il portale dell&#39;organizzazione e le applicazioni sono reattivi e facili da usare per i dispositivi mobili. Nel seguente flusso di lavoro viene illustrato come Sarah esplora e invia l???applicazione sul suo dispositivo mobile.

![left-form-on mobile](assets/leave-form-on-mobile.png)

**Come funziona**

Il portale dell&#39;organizzazione e il dashboard del dipendente sono  pagine AEM Sites. Nel dashboard sono elencate diverse opzioni self-service, ad esempio l&#39;applicazione di destinazione. Il pulsante Applica ?? collegato a un modulo adattivo.

Il modulo adattivo per l&#39;applicazione di congedo si basa sul modello dati dipendente Lascia il modulo. Nella sezione Saldo congedo, la tabella dei saldi di uscita viene compilata utilizzando il servizio `getLeavesOf` Modello dati modulo. I campi Data di inizio e Data di fine utilizzano regole per convalidare che i valori di data siano uguali o successivi alla data corrente. La durata dell&#39;uscita viene calcolata utilizzando la funzione `calcBusinessDays`.

?? possibile esaminare il modulo adattivo e il modello dati modulo nelle seguenti posizioni:

`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/leave-application.html`

`https://[authorHost]:[authorPort]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/db`

**Vedi te stesso**

Andate a `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` ed effettuate l&#39;accesso utilizzando `srose/srose` come nome utente/password per Sarah. Fare clic su **[!UICONTROL Dipendente]** per accedere al dashboard, quindi fare clic su **[!UICONTROL Applica]** in Esci dall&#39;applicazione. Compila i dettagli e invia la domanda.

### Gloria esamina e approva l&#39;applicazione di congedo {#gloria-reviews-and-approves-the-leave-application}

La richiesta di congedo presentata da Sarah ?? assegnata a Gloria Rios per la revisione. Gloria accede alla propria casella AEM Posta in arrivo e rivede i compiti che le sono stati assegnati. Approva la richiesta presentata da Sarah e completa il compito.

![left-](assets/leave-inbox.png)
**inboxFigure:inbox di** *Gloria*

![left-](assets/leave-approved.png)
**approvatoFigure:** *Apri attivit??*

**Come funziona**

Il flusso di lavoro di invio nell???applicazione di uscita attiva un flusso di lavoro Forms che crea un???attivit?? nella inbox di Gloria per l???approvazione. Rivedete l&#39;Forms Workflow all&#39;indirizzo `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-leave-application.html`

![corporate-card-left-application-workflow-model](assets/corporate-card-leave-application-workflow-model.png)

**Vedi te stesso**

Andate a `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` ed effettuate l&#39;accesso utilizzando `grios/password` come nome utente/password per Gloria Rios. Aprire l&#39;attivit?? creata per uscire dall&#39;applicazione e approvarla.
