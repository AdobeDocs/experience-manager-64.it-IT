---
title: Configurazione di analisi e rapporti
seo-title: Configuring analytics and reports
description: Scopri come configurare Adobe Analytics per scoprire i pattern e i problemi di interazione che gli utenti devono affrontare durante l’utilizzo di moduli adattivi, documenti adattivi e moduli HTML5.
seo-description: Learn how to configure Adobe Analytics to discover interaction patterns and problems users face while using adaptive forms, adaptive documents, and HTML5 forms.
uuid: f5671600-e1e2-4fef-9e47-6c8ede027700
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integrations
discoiquuid: 6301e0ef-3faa-4e6f-932d-37b049577cec
exl-id: a55999a8-a92b-4750-bf05-ee326d079f65
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 3%

---

# Configurazione di analisi e rapporti {#configuring-analytics-and-reports}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Forms si integra con Adobe Analytics per acquisire e monitorare le metriche delle prestazioni dei moduli e dei documenti pubblicati. L’obiettivo dell’analisi di queste metriche è quello di prendere decisioni informate basate sui dati in merito alle modifiche necessarie a rendere i moduli o i documenti più utilizzabili.

>[!NOTE]
>
>La funzione di analisi in AEM Forms è disponibile come parte del pacchetto aggiuntivo di AEM Forms. Per informazioni sull&#39;installazione del pacchetto aggiuntivo, vedi [Installazione e configurazione di AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md).
>
>Oltre al pacchetto aggiuntivo, è necessario disporre di un account Adobe Analytics e di privilegi di amministratore sull’istanza AEM. Per informazioni sulla soluzione, vedi [Adobe Analytics](https://www.adobe.com/solutions/digital-analytics.html).

## Panoramica {#overview}

È possibile utilizzare Adobe Analytics per scoprire i pattern di interazione e i problemi riscontrati dagli utenti durante l’utilizzo di moduli adattivi, moduli HTML5 e comunicazioni interattive. Con Adobe Analytics è possibile tenere traccia e memorizzare informazioni sui seguenti parametri:

* **Tempo medio di riempimento**: Tempo medio impiegato per compilare il modulo.
* **Rendering**: Numero di volte in cui il modulo viene aperto.
* **Bozze**: Numero di volte in cui un modulo viene salvato nello stato di bozza.
* **Invii**: Numero di volte in cui il modulo viene inviato.
* **Interrompere**: Numero di volte in cui gli utenti si fermano senza compilare il modulo.

Puoi personalizzare Adobe Analytics per aggiungere/rimuovere altri parametri. Oltre alle informazioni di cui sopra, il rapporto contiene le seguenti informazioni su ogni pannello di HTML5 e del modulo adattivo:

* **Time**: Tempo trascorso sul pannello e sui campi del pannello.
* **Errore**: Numero di errori riscontrati nel pannello e nei campi del pannello.
* **Aiuto**: Numero di volte in cui un utente apre la guida di un pannello e dei campi del pannello.

## Creazione di una suite di rapporti {#creating-report-suite}

I dati di Analytics vengono memorizzati in archivi specifici del cliente denominati suite di rapporti. Per creare una suite di rapporti e utilizzare Adobe Analytics, devi disporre di un account Adobe Marketing Cloud valido. Prima di eseguire i seguenti passaggi, assicurati di disporre di un account Adobe Marketing Cloud valido.

Esegui i seguenti passaggi per creare una suite di rapporti.

1. Accedi a [https://sc.omniture.com/login/](https://sc.omniture.com/login/)
1. Nel Marketing Cloud, seleziona **Amministratore** > **Admin Console** >  **Suite di rapporti**.
1. Seleziona **Crea nuovo** > **Suite di rapporti** in Report Suite Manager.

   ![Creare una nuova suite di rapporti](assets/newreportsuite.png)

   Creare una nuova suite di rapporti

1. Assicurati che il primo elenco a discesa sia impostato su **Creazione da un modello** quindi seleziona **Commerce**.

1. Individua il **ID suite di rapporti** e aggiungi un nuovo ID suite di rapporti. Per esempio, JJEsquire. Sotto il campo ID suite di rapporti viene visualizzato un ID suite di rapporti. Include un prefisso automatico, che è spesso il nome dell’azienda.

1. Aggiungi nuovo **Titolo sito**. Ad esempio, JJEsquire Getting Started Suite. Questo titolo viene utilizzato nell’interfaccia utente di Analytics. Utilizza l&#39;ID suite di rapporti nel tuo codice.

1. Seleziona una **Fuso orario** dal menu a discesa . Tutti i dati che entrano in questa suite di rapporti vengono registrati in base al fuso orario definito.

1. Lascia la **URL di base** e **Pagina predefinita** campi vuoti. Questi due valori vengono utilizzati solo dall’interfaccia di Adobe Marketing Cloud per il collegamento al sito web.
1. Lascia la **Vai alla data live** impostato su oggi. La data di pubblicazione determina il giorno in cui la suite di rapporti viene attivata.

1. In **Visualizzazioni di pagina stimate al giorno** campo, digitare 100. Usa questo campo per stimare il numero di visualizzazioni di pagina che prevedi per il tuo sito web al giorno. Questa stima consente ad Adobe di mettere a punto la quantità appropriata di hardware per elaborare i dati che si sta raccogliendo.

1. Seleziona una **Valuta di base** dal menu a discesa . Tutti i dati di valuta che entrano in questa suite di rapporti vengono convertiti e memorizzati in questo formato di valuta.

1. Fai clic su **Creare un rapporto** Suite. Dovresti visualizzare l’aggiornamento della pagina con un messaggio che informa che la tua suite di rapporti è stata creata correttamente.

1. Seleziona la suite di rapporti appena creata. Passa a **Modifica impostazioni** > **Generale** >  **Impostazioni account generali**.

   ![Impostazioni account generali](assets/geographic_settings.png)
   **Figura:** *Impostazioni account generali*

1. Nella schermata Impostazioni account generali, abilita **Reporting sulla geografia** e fai clic su **Salva**.
1. Passa a **Modifica impostazioni** > **Traffico** > **Variabili di traffico**.

1. Nella suite di rapporti, configura e abilita le seguenti variabili di traffico.

   * **formName**: Identificatore per un modulo adattivo.
   * **formInstance**: Identificatore di un’istanza di modulo adattivo. Abilita i rapporti Percorso per questa variabile.
   * **fieldName**: Identificatore di un campo modulo adattivo. Abilita i rapporti Percorso per questa variabile.
   * **panelName**: Identificatore di un pannello adattivo del modulo. Abilita i rapporti Percorso per questa variabile.
   * **formTitle**: Titolo del modulo.
   * **fieldTitle**: Titolo del campo modulo.
   * **panelTitle**: Titolo del pannello del modulo.
   * **analyticsVersion**: Versione di analisi dei moduli.

1. Passa a **Modifica impostazioni** > **Conversione** >  **Eventi di successo**. Definisci e abilita i seguenti eventi di successo:

   | Evento di successo | Tipo |
   |---|---|
   | abbandonare | Contatore |
   | rendering | Contatore |
   | panelVisit | Contatore |
   | fieldVisit | Contatore |
   | salva | Contatore |
   | errore | Contatore |
   | Aiuto di  | Contatore |
   | invia | Contatore |
   | timeSpent | Numerico |

   >[!NOTE]
   >
   >Un numero di evento e di proprietà utilizzato per configurare AEM Forms Analytics deve essere diverso dal numero di evento e dal numero di proprietà utilizzati in [Analisi AEM](/help/sites-administering/adobeanalytics.md) configurazione.

1. Esci dall’account Adobe Marketing Cloud.

## Creazione della configurazione del Cloud Service {#creating-cloud-service-configuration}

La configurazione del Cloud Service è costituita da informazioni sull’account Adobe Analytics. La configurazione consente ad Adobe Experience Manager (AEM) di connettersi ad Adobe Analytics. Crea una configurazione separata per ogni account Analytics utilizzato.

1. Accedi alla tua istanza di authoring AEM come amministratore.
1. Nell’angolo in alto a sinistra, fai clic su **Adobe Experience Manager** > **Strumenti** ![strumenti](assets/tools.png)> **Cloud Services** > **Cloud Services legacy**.
1. Individua **Adobe Analytics** icona. Fai clic su **Mostra configurazioni** quindi procedi con il pulsante **[+]** per aggiungere una nuova configurazione.

   Se sei un utente nuovo, fai clic su **Configura ora**.

1. Aggiungi un titolo alla nuova configurazione (la compilazione del campo Nome è facoltativa). Ad esempio, Configurazione di Analytics . Fai clic su **Crea**.

1. Quando il pannello Modifica si apre nella pagina di configurazione, compila i campi:

   * **Azienda**: Il nome della tua azienda come descritto in Adobe Analytics.

   * **Nome utente**: Nome utilizzato per accedere ad Adobe Analytics.

   * **Password**: Password Adobe Analytics per l&#39;account di cui sopra.

   * **Centro dati**: Centro dati del tuo account Adobe Analytics.

1. Fai clic su **Connettersi ad Analytics**. Viene visualizzata una finestra di dialogo con il messaggio che indica che la connessione è riuscita. Fai clic su **OK**.

## Creazione di un framework di Cloud Service {#creating-cloud-service-framework}

Un framework Adobe Analytics è un insieme di mappature tra le variabili Adobe Analytics e le variabili AEM. Utilizzare un framework per configurare il modo in cui i moduli compilano i dati nei rapporti di Adobe Analytics. I framework sono associati a una configurazione Adobe Analytics. Puoi creare più framework per ogni configurazione.

1. Nella console di AEM Cloud Services, fai clic su **Mostra configurazioni**, in Adobe Analytics.

1. Fai clic sul pulsante **[+]** link accanto a accanto alla configurazione di Analytics.

   ![Configurazione di Adobe Analytics](assets/adobe-analytics-cloud-services.png)
   **Figura:** *Configurazione di Adobe Analytics*

1. Tipo a **Titolo** e **Nome** per il framework, seleziona **Adobe Analytics** Framework e fai clic su **Crea**. Il framework viene aperto per la modifica.

1. Nella sezione Suite per report del contenitore laterale, fai clic su **Aggiungi elemento**, quindi utilizza l’elenco a discesa per selezionare l’ID suite di rapporti (ad esempio, JJEsquire) con cui interagisce il framework.

1. Accanto all’ID suite di rapporti, seleziona le istanze del server che desideri inviare informazioni alla suite di rapporti.

   ![information_to_send_to_report_suite](assets/information_to_send_to_report_suite.png)

1. Trascina un **Componente Analisi dei moduli** dal **altro** da SideKick alla struttura.
1. Per mappare le variabili di Analytics con le variabili definite nel componente, trascina una variabile da AEM Content Finder su un campo del componente di tracciamento.

   ![Mappatura di variabili AEM con variabili Adobe Analytics](assets/analytics.png)

1. Attivare il framework utilizzando la **scheda pagina** nella barra laterale, fate clic su **Attiva framework**.

## Configurazione del servizio di configurazione di AEM Forms Analytics {#configuring-aem-forms-analytics-configuration-service}

1. Nell’istanza dell’autore, apri AEM Web Console Configuration Manager all’indirizzo https://&lt;*server*>:&lt;*porta*>/system/console/configMgr.
1. Individua e apri la configurazione di AEM Forms Analytics

   ![Servizio di configurazione di AEM Forms Analytics](assets/analytics_configuration.png)
   **Figura:** *Servizio di configurazione di AEM Forms Analytics*

1. Specifica i valori appropriati per i campi seguenti e fai clic su **Salva**.

   * **Quadro SiteCatalyst**: Seleziona la struttura/configurazione definita nella sezione Impostare un framework per il tracciamento .
   * **Linea guida di tracciamento del tempo sul campo**: Specifica la durata, in secondi, dopo la quale la visita sul campo deve essere tracciata. Il valore predefinito è 0. Quando il valore è maggiore di 0 (zero), due eventi di tracciamento separati vengono inviati al server Adobe Analytics. Il primo evento indica al server di analisi di interrompere il tracciamento del campo uscito. Il secondo evento viene inviato dopo la scadenza della durata specificata. Il secondo evento indica al server di analisi di avviare il tracciamento del campo visitato. L’utilizzo di due eventi separati consente di misurare con precisione il tempo trascorso su un campo. Quando il valore è 0 (zero), viene inviato un singolo evento di tracciamento al server Adobe Analytics.
   * **Cron di sincronizzazione dei report di Analytics**: Specifica l’espressione cron per recuperare i rapporti da Adobe Analytics. Il valore predefinito è 0 2 ?.
   * **Timeout del report di recupero:** Specifica la durata, in secondi, dell’attesa che il server risponda al rapporto di analisi. Il tempo predefinito è di 120 secondi.

   >[!NOTE]
   >
   >L’operazione di recupero del rapporto può richiedere fino a 10 secondi in più e quindi il numero specificato di secondi.

1. Ripeti i passaggi 1-3 sull’istanza di pubblicazione per configurare analytics.

Ora è possibile abilitare l’analisi dei moduli e generare un rapporto di analisi.

## Abilitazione di analytics per un modulo o un documento {#enabling-analytics-for-a-form-or-document}

1. Accedi al portale AEM in `https://[hostname]:[port]`.
1. Fai clic su **Forms > Forms e documenti**, selezionare un modulo o un documento e fare clic su **Abilitare Analytics**. L’analisi è abilitata.

   ![Abilitazione di analytics per un modulo o un documento](assets/enable-analytics-1.png)
   **Figura:** *Abilitazione dell’analisi per un modulo*

   **A.** Pulsante Abilita Analytics **B.** Modulo selezionato

   Per informazioni dettagliate sulla visualizzazione dei rapporti di analisi dei moduli, vedere [Visualizzazione e comprensione dei rapporti di AEM Forms Analytics](/help/forms/using/view-understand-aem-forms-analytics-reports.md)
