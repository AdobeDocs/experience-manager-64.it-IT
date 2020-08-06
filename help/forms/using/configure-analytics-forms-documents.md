---
title: Configurazione di analisi e rapporti
seo-title: Configurazione di analisi e rapporti
description: 'Scoprite come configurare  Adobe Analytics per individuare i pattern di interazione e i problemi che gli utenti devono affrontare durante l''uso di moduli adattivi, documenti adattivi e moduli HTML5. '
seo-description: 'Scoprite come configurare  Adobe Analytics per individuare i pattern di interazione e i problemi che gli utenti devono affrontare durante l''uso di moduli adattivi, documenti adattivi e moduli HTML5. '
uuid: f5671600-e1e2-4fef-9e47-6c8ede027700
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integrations
discoiquuid: 6301e0ef-3faa-4e6f-932d-37b049577cec
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d
workflow-type: tm+mt
source-wordcount: '1542'
ht-degree: 1%

---


# Configurazione di analisi e rapporti {#configuring-analytics-and-reports}

 AEM Forms si integra con  Adobe Analytics che consente di acquisire e monitorare le metriche delle prestazioni per i moduli e i documenti pubblicati. L&#39;obiettivo dell&#39;analisi di queste metriche è di rendere più utilizzabili moduli o documenti con decisioni informate basate sui dati richiesti.

>[!NOTE]
>
>La funzione di analisi in  AEM Forms è disponibile come parte del pacchetto  del componente aggiuntivo AEM Forms. Per informazioni sull&#39;installazione del pacchetto del componente aggiuntivo, consultate [Installazione e configurazione  AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md).
>
>Oltre al pacchetto del componente aggiuntivo, è necessario disporre di un account Adobe Analytics  e di privilegi di amministratore per l&#39;istanza AEM. Per informazioni sulla soluzione, consultate [Adobe Analytics](https://www.adobe.com/solutions/digital-analytics.html).

## Panoramica {#overview}

È possibile utilizzare  Adobe Analytics per individuare i pattern di interazione e i problemi che gli utenti devono affrontare durante l&#39;uso di moduli adattivi, moduli HTML5 e comunicazioni interattive. L&#39;analisi  Adobe tiene traccia e memorizza le informazioni sui seguenti parametri:

* **Tempo** medio di riempimento: Tempo medio impiegato per compilare il modulo.
* **Rappresentazioni**: Numero di volte che un modulo viene aperto.
* **Bozze**: Numero di volte in cui un modulo viene salvato nello stato bozza.
* **Invii**: Numero di volte in cui il modulo viene inviato.
* **Interrompi**: Numero di volte in cui gli utenti si allontanano senza compilare il modulo.

Potete personalizzare  Adobe Analytics per aggiungere o rimuovere altri parametri. Oltre alle informazioni di cui sopra, il rapporto contiene le seguenti informazioni su ogni pannello del modulo HTML5 e adattivo:

* **Ora**: Tempo trascorso sul pannello e sui campi del pannello.
* **Errore**: Numero di errori riscontrati nel pannello e nei campi del pannello.
* **Aiuto**: Numero di volte che un utente apre la guida di un pannello e dei campi del pannello.

## Creazione di una suite di rapporti {#creating-report-suite}

I dati di Analytics vengono memorizzati in repository specifici del cliente denominati suite di rapporti. Per creare una suite di rapporti e utilizzare  Adobe Analytics, è necessario disporre di un account Adobe Marketing Cloud valido. Prima di eseguire i seguenti passaggi, accertatevi di disporre di un account Adobe Marketing Cloud valido.

Per creare una suite di rapporti, effettuate le seguenti operazioni.

1. Accedete a [https://sc.omniture.com/login/](https://sc.omniture.com/login/)
1. Nel Marketing Cloud, selezionate **Admin** > **Admin Console** > **Suite** di rapporti.
1. Selezionate **Crea nuovo** > Suite **di** rapporti in Report Suite Manager.

   ![Crea nuova suite di rapporti](assets/newreportsuite.png)

   Crea nuova suite di rapporti

1. Accertatevi che il primo elenco a discesa sia impostato su **Crea da un modello** , quindi selezionate **Commerce**.

1. Individuate il campo ID **suite di** rapporti e aggiungete un nuovo ID suite di rapporti. Ad esempio, JJEsquire. Sotto il campo ID suite di rapporti viene visualizzato un ID suite di rapporti. Include un prefisso automatico, che è spesso il nome della società.

1. Aggiungete un nuovo titolo **** del sito. Ad esempio, JJEsquire Getting Started Suite. Questo titolo viene usato nell’interfaccia utente di Analytics. Usa l&#39;ID suite di rapporti nel tuo codice.

1. Selezionate un **fuso** orario dal menu a discesa. Tutti i dati inclusi in questa suite di rapporti vengono registrati in base al fuso orario definito.

1. Lasciate vuoti i campi URL **di** base e Pagina **** predefinita. Questi due valori vengono utilizzati solo dall’interfaccia Adobe Marketing Cloud per il collegamento al sito Web.
1. Lascia l&#39;opzione Data **** live impostata su Oggi. Go Live Date determina il giorno in cui viene attivata la suite di rapporti.

1. Nel campo Visualizzazioni **stimate di pagina per giorno** , digitare 100. Utilizzate questo campo per stimare il numero di visualizzazioni di pagina previste per il sito Web al giorno. Questa stima consente  Adobe di mettere in atto la quantità appropriata di hardware per elaborare i dati che si sta raccogliendo.

1. Selezionare una divisa **di** base dal menu a discesa. Tutti i dati di valuta inclusi in questa suite di rapporti vengono convertiti e memorizzati in questo formato di valuta.

1. Fate clic su **Crea suite di rapporti** . Dovresti visualizzare l&#39;aggiornamento della pagina con un messaggio che informa che la tua suite di rapporti è stata creata correttamente.

1. Seleziona la suite di rapporti appena creata. Andate a **Modifica impostazioni** > **Generale** > Impostazioni account **generali**.

   ![Impostazioni account generali](assets/geographic_settings.png)
   **Figura:** *Impostazioni account generali*

1. Nella schermata Impostazioni account generali, abilita **Reporting** geografia e fai clic su **Salva**.
1. Andate a **Modifica impostazioni** > **Traffico** > Variabili **** traffico.

1. Nella suite di rapporti, configura e abilita le seguenti variabili di traffico.

   * **formName**: Identificatore per un modulo adattivo.
   * **formInstance**: Identificatore di un’istanza di modulo adattivo. Abilita i rapporti Percorso per questa variabile.
   * **fieldName**: Identificatore di un campo modulo adattivo. Abilita i rapporti Percorso per questa variabile.
   * **panelName**: Identificatore di un pannello di moduli adattivi. Abilita i rapporti Percorso per questa variabile.
   * **formTitle**: Titolo del modulo.
   * **fieldTitle**: Titolo del campo modulo.
   * **panelTitle**: Titolo del pannello del modulo.
   * **analyticsVersion**: Versione dell&#39;analisi dei moduli.

1. Andate a **Modifica impostazioni** > **Conversione** > Eventi **di** successo. Definire e attivare i seguenti eventi di successo:

   | Evento Success | Tipo |
   |---|---|
   | abbandono | Contatore |
   | rendering | Contatore |
   | panelVisit | Contatore |
   | fieldVisit | Contatore |
   | save | Contatore |
   | errore | Contatore |
   | aiuto | Contatore |
   | submit | Contatore |
   | timeSpent | Numerico |

   >[!NOTE]
   >
   >Un numero di evento e di proprietà utilizzato per configurare &#39;analisi AEM Forms deve essere diverso dal numero di evento e dal numero di proprietà utilizzati nella configurazione di [AEM analisi](/help/sites-administering/adobeanalytics.md) .

1. Disconnettetevi dall&#39;account Adobe Marketing Cloud.

## Creazione della configurazione del Cloud Service {#creating-cloud-service-configuration}

La configurazione del Cloud Service è un insieme di informazioni sull&#39;account Adobe Analytics . La configurazione consente ad Adobe Experience Manager (AEM) di connettersi a  Adobe Analytics. Create una configurazione separata per ciascun account Analytics che utilizzate.

1. Accedete all’istanza di creazione AEM come amministratore.
1. Nell’angolo in alto a sinistra, fate clic su **Adobe Experience Manager** > **Strumenti** ![strumenti](assets/tools.png)> **Distribuzione** > **Cloud Services**.
1. Individuate **&#39;icona Adobe Analytics** . Fate clic su **Mostra configurazioni** , quindi fate clic su **[+]** per aggiungere una nuova configurazione.

   Se siete un utente principiante, fate clic su **Configura ora**.

1. Aggiungete un Titolo alla nuova configurazione (la compilazione del campo Nome è facoltativa). Ad esempio, Configurazione della mia analisi. Fai clic su **Crea**.

1. Quando il pannello Modifica si apre nella pagina di configurazione, compila i campi:

   * **Società**: Il nome dell&#39;azienda, come mostrato  Adobe Analytics.

   * **Nome utente**: Nome utilizzato per accedere a  Adobe Analytics.

   * **Password**: La password Adobe Analytics  per l&#39;account indicato sopra.

   * **Centro** dati: Centro dati del tuo account Adobe Analytics .

1. Fate clic su **Connetti ad Analytics**. Viene visualizzata una finestra di dialogo con il messaggio che indica che la connessione è stata eseguita correttamente. Fai clic su **OK**.

## Creazione di un framework Cloud Service {#creating-cloud-service-framework}

Un framework Adobe Analytics  è un insieme di mappature tra  variabili Adobe Analytics e AEM variabili. Utilizzare un framework per configurare il modo in cui i moduli compilano i dati per  rapporti Adobe Analytics. I framework sono associati a una configurazione Adobe Analytics . Potete creare più framework per ciascuna configurazione.

1. Nella console dei servizi cloud AEM, fai clic su **Mostra configurazioni** in  Adobe Analytics.

1. Fai clic sul collegamento **[+]** accanto a accanto alla configurazione di Analytics.

   ![Configurazione  Adobe Analytics](assets/adobe-analytics-cloud-services.png)
   **Figura:** *Configurazione  Adobe Analytics*

1. Digitate un **Titolo** e un **Nome** per il framework, selezionate **Adobe Analytics** Framework e fate clic su **Crea**. Il framework viene aperto per la modifica.

1. Nella sezione Suite di rapporti del contenitore laterale, fate clic su **Aggiungi elemento**, quindi utilizzate il menu a discesa per selezionare l&#39;ID suite di rapporti (ad esempio, JJEsquire) con cui interagisce il framework.

1. Accanto all&#39;ID della suite di rapporti, seleziona le istanze del server che desideri inviare informazioni alla suite di rapporti.

   ![information_to_send_to_report_suite](assets/information_to_send_to_report_suite.png)

1. Trascinare un componente **Analisi** modulo dall’ **altra** categoria da SideKick al framework.
1. Per mappare le variabili di Analytics con le variabili definite nel componente, trascinate una variabile da AEM Content Finder su un campo del componente di tracciamento.

   ![Mappatura AEM variabili con  variabili Adobe Analytics](assets/analytics.png)

1. Attivate il framework utilizzando la scheda **della** pagina nella barra laterale, fate clic su **Attiva framework**.

## Configurazione  servizio di configurazione di AEM Forms Analytics {#configuring-aem-forms-analytics-configuration-service}

1. Nell’istanza di creazione, aprite AEM Web Console Configuration Manager all’indirizzo https://&lt;*server*>:&lt;*porta*>/system/console/configMgr.
1. Individua e apri  configurazione AEM Forms Analytics

   ![servizio di configurazione di AEM Forms Analytics](assets/analytics_configuration.png)
   **Figura:** *servizio di configurazione di AEM Forms Analytics*

1. Specificate i valori appropriati per i campi seguenti e fate clic su **Salva**.

   * **Quadro** SiteCatalyst: Selezionate la struttura/configurazione definita nella sezione Impostare una struttura per il tracciamento.
   * **Linea di base** tracciamento ora campo: Specificate la durata, in secondi, dopo la quale la visita sul campo deve essere tracciata. Il valore predefinito è 0. Quando il valore è maggiore di 0 (zero), due eventi di tracciamento separati vengono inviati  server Adobe Analytics. Il primo evento indica al server di analisi di interrompere il tracciamento del campo uscito. Il secondo evento viene inviato dopo la scadenza della durata specificata. Il secondo evento indica al server di analisi di avviare il tracciamento del campo visitato. L&#39;utilizzo di due eventi separati consente di misurare con precisione il tempo trascorso su un campo. Quando il valore è 0 (zero), un singolo evento di tracciamento viene inviato  server Adobe Analytics.
   * **Cron** di sincronizzazione dei report di analisi: Specifica l&#39;espressione cron per il recupero dei rapporti da  Adobe Analytics. Il valore predefinito è 0 0 2 ?.
   * **Timeout report recupero:** Specificate la durata, in secondi, dell&#39;attesa che il server risponda al report di analisi. Il tempo predefinito è 120 secondi.

   >[!NOTE]
   >
   >L&#39;operazione di recupero del rapporto di timeout può richiedere fino a 10 secondi in più, quindi il numero specificato di secondi.

1. Ripetete i passaggi da 1 a 3 nell’istanza di pubblicazione per configurare l’analisi.

Ora è possibile abilitare l&#39;analisi per i moduli e generare un rapporto di analisi.

## Abilitazione dell&#39;analisi per un modulo o un documento {#enabling-analytics-for-a-form-or-document}

1. Effettuate l&#39;accesso AEM portale all&#39;indirizzo `https://[hostname]:[port]`.
1. Fate clic su **Forms > Forms e documenti**, selezionate un modulo o un documento, quindi fate clic su **Abilita analisi**. L&#39;analisi è abilitata.

   ![Abilitazione dell&#39;analisi per un modulo o un documento](assets/enable-analytics-1.png)
   **Figura:** *Abilitazione dell&#39;analisi per un modulo*

   **A.** Pulsante Abilita Analytics **B.** Modulo selezionato

   Per informazioni dettagliate sulla visualizzazione dei report di analisi dei moduli, vedere [Visualizzazione e comprensione  report di analisi AEM Forms](/help/forms/using/view-understand-aem-forms-analytics-reports.md)

