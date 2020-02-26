---
title: Guida di Kickstart
seo-title: Guida di Kickstart
description: Segui questa pagina per creare un progetto dimostrativo AEM Screens. Consente di creare un’esperienza di digital signage a partire dall’installazione e dalla configurazione di un nuovo progetto per visualizzare i contenuti nel lettore AEM Screens.
seo-description: Segui questa pagina per creare un progetto dimostrativo AEM Screens. Consente di creare un’esperienza di digital signage a partire dall’installazione e dalla configurazione di un nuovo progetto per visualizzare i contenuti nel lettore AEM Screens.
uuid: 73fff2f2-c926-4435-8ab2-891771c843aa
contentOwner: Jyotika syal
content-type: reference
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
discoiquuid: 9e03f35e-284b-43d8-b095-c94800e2e9b3
translation-type: tm+mt
source-git-commit: 5f613cbae9dccbc277287e5e58c8f0648c4f3bed

---


# Guida di Kickstart{#kickstart-guide}

Questa sezione è un esempio pratico per AEM Screens e illustra come eseguire azioni di base. Questa sezione descrive come impostare un&#39;esperienza di digital signage di base con contenuti e risorse e pubblicare contenuti su un lettore Screens. Per una conoscenza approfondita di tutti i componenti per lo sviluppo di Screens, consultate le risorse alla fine della pagina.

## Creazione di un&#39;esperienza di digital signage in 5 minuti {#creating-a-digital-signage-experience-in-minutes}

La procedura seguente consente di creare un progetto di esempio per Screens e pubblicare contenuti per il lettore Screens.

1. Per scaricare **AEM Screens Player**, fai clic [qui](https://download.macromedia.com/screens/).

   AEM Screens è disponibile anche in **Google Play**.

   Per l&#39;implementazione di Chrome OS Player, consulta [Chrome Management Console](implementing-chrome-os-player.md) per ulteriori informazioni.

   Per ulteriori informazioni, vedere [Installazione e configurazione delle schermate](configuring-screens-introduction.md) .

   >[!NOTE]
   >
   >**Impostazioni OSGI**
   >
   >È necessario abilitare il referente vuoto per consentire al dispositivo di inviare dati al server. Ad esempio, se la proprietà del referente vuoto è disabilitata, il dispositivo non può inviare una schermata indietro. Attualmente alcune di queste funzioni sono disponibili solo se il filtro Apache Sling Referrer Consenti nullo è abilitato nel configurazione OSGI. Il dashboard potrebbe visualizzare un avviso che segnala che le impostazioni di protezione potrebbero impedire il funzionamento di alcune di queste funzioni.
   >
   >Per attivare il filtro ***Apache Sling Referrer Filter Allow Empty***, effettuate le seguenti operazioni:
   >
   >1. Passa alla configurazione [della console Web di](http://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter)Adobe Experience Manager.
   >1. Selezionare l&#39;opzione **allow.empty** .
   >1. Fai clic su **Salva**.
   >    
   >Per ulteriori informazioni sui passaggi precedenti, consulta la sezione ***Prerequisiti*** in [Configurazione e distribuzione di AEM Screens](configuring-screens-introduction.md).

1. **Creazione di un nuovo progetto**

   1. Seleziona il collegamento all’Adobe Experience Manager (in alto a sinistra) e quindi **Schermi**. Alternatively, you can ﻿go directly to: [http://localhost:4502/screens.html/content/screens](http://localhost:4502/screens.html/content/screens).
   1. Fai clic su **Crea** per creare un nuovo progetto Screens (vedi la figura qui sotto).
   1. Select **Screens** from the **Create Screens Project** wizard and click **Next**.
   1. Enter the title as **Test_Project** and click **Create**.
   ![chlimage_1-64](assets/chlimage_1-64.png)

   Una volta creato il progetto, tornerete alla console Progetto schermate. Ora puoi selezionare il progetto. In un progetto, ci sono cinque tipi di cartelle, vale a dire **Pianificazioni**, **Posizioni**, **Applicazioni**, **Dispositivi** e **Canali**, come mostrato nella figura seguente.

   >[!NOTE]
   >
   >Le pianificazioni sono disponibili solo se hai installato AEM 6.3 Sites Feature Pack 1. Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

   ![screen_shot_2019-03-04at85952am](assets/screen_shot_2019-03-04at85952am.png)

   Per ulteriori informazioni, consulta [Creare e gestire il progetto](creating-a-screens-project.md) Schermi.

1. **Creazione di un nuovo canale**

   Una volta installato il progetto, è necessario creare un nuovo canale in cui gestire il contenuto.

   Per creare un nuovo canale per il progetto, effettuate le seguenti operazioni:

   1. Navigate to the **Test_Project** you created and select the **Channels** folder.
   1. Click **Create** from the action bar (see the figure below). Si apre una procedura guidata.
   1. Choose the **Sequence Channel** and click **Next**.
   1. Enter the **Name** and **Title** as **TestChannel** and click **Create**.
   ![screen_shot_2019-03-04at90236am](assets/screen_shot_2019-03-04at90236am.png)

   Il *TestChannel* viene creato e aggiunto alla cartella dei canali, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-03-04at90346am](assets/screen_shot_2019-03-04at90346am.png)

   Per ulteriori informazioni sulla creazione e la gestione dei canali, consulta [Gestione](managing-channels.md) dei canali.

1. **Aggiunta di contenuto a un canale**

   Una volta installato il canale, è necessario aggiungere al canale il contenuto che verrà visualizzato dal lettore AEM Screens.

   Per aggiungere contenuti al canale (*TestChannel*) del progetto, effettuate le seguenti operazioni:

   1. Navigate to the *Test_Project* you created and select the **Channels** folder.
   1. Click **Edit** from the action bar (see the figure below). The editor for the *TestChannel* opens.
   1. Fai clic sull’icona che apre o chiude il pannello laterale sinistro della barra delle azioni per aprire le risorse e i componenti.
   1. Trascina i componenti da aggiungere al canale.
   ![screen_shot_2019-03-04at90507am](assets/screen_shot_2019-03-04at90507am.png)

   In questo esempio, l’editor mostra un’immagine aggiunta al canale.

   ![screen_shot_2019-03-04at90558am](assets/screen_shot_2019-03-04at90558am.png)

1. **Crea una nuova posizione**

   Una volta installato il canale, è necessario creare la posizione.

   ***Le posizioni*** consentono di compartimentare le diverse esperienze di digital signage e contengono le configurazioni dei display in base a dove si trovano i vari schermi.

   Per creare una nuova posizione per il progetto, effettuate le seguenti operazioni:

   1. Navigate to the *Test_Project* you created and select the **Locations** folder.
   1. Fate clic su **Crea** accanto all&#39;icona più nella barra delle azioni (vedere la figura sotto). Si apre una procedura guidata.
   1. Select **Location** from the wizard and click **Next**.
   1. Enter the **Name** and **Title** for your location (enter the title as *TestLocation*) and click **Create**.
   ![screen_shot_2019-03-04at91021am](assets/screen_shot_2019-03-04at91021am.png)

   Il *TestLocation* viene creato e aggiunto alla cartella **Locations** .

   ![screen_shot_2019-03-04at91117am](assets/screen_shot_2019-03-04at91117am.png)

1. **Creazione di una nuova visualizzazione per *TestLocation ***

   Dopo aver creato un percorso, è necessario creare una nuova visualizzazione per il percorso.

   ***I display*** rappresentano l&#39;esperienza digitale che viene eseguita su uno o più schermi.

   1. Andate alla posizione in cui desiderate creare la visualizzazione (*Test_* Project —> **Locations** —> *TestLocation)* come illustrato nella figura precedente e selezionate *TestLocation*.
   1. Fare clic su** Crea **dalla barra di azione.
   1. Select **Display** from the **Create** wizard and click **Next**.
   1. Enter **Title** for your display location (enter the title as *TestDisplay*).
   1. Fai clic su **Crea**.
   Viene aggiunto un nuovo *TestDisplay* alla posizione *TestLocation*, come illustrato nella figura riportata di seguito.

   ![screen_shot_2019-03-04at91341am](assets/screen_shot_2019-03-04at91341am.png)

1. **Aggiunta di una pianificazione**

   Le *Pianificazioni*, negli AEM Screens, consentono di organizzare i canali in gruppi riutilizzabili, in modo da non dover ripetere la loro assegnazione singolarmente per ogni visualizzazione.

   >[!NOTE]
   >
   >Questa funzionalità Screens è disponibile solo se è stato installato AEM 6.3 Sites Feature Pack 1 o versione successiva. Per accedere a questo Feature Pack, è necessario contattare Adobe Support e richiedere l&#39;accesso. Una volta ottenute le autorizzazioni, è possibile scaricare il Feature Pack da Condivisione pacchetti.

   1. Andate alla cartella **Pianificazioni** da Test_Project > **Pianificazioni**.
   1. Fare clic su** Crea **dalla barra di azione. Si apre una procedura guidata.
   1. Selezionare **Pianificazione** dalla pagina **Creazione** guidata.
   1. Immettere il **Titolo** come *MorningSchedule* nella pagina delle proprietà.
   1. Fate clic su **Crea** e la pianificazione verrà aggiunta alla cartella **Pianificazioni** , come illustrato nella figura seguente.
   ![screen_shot_2019-03-04at91836am](assets/screen_shot_2019-03-04at91836am.png)

   Inoltre, seleziona la pianificazione (*MorningSchedule*) e fai clic su **Dashboard** nella barra delle azioni per visualizzare il dashboard delle pianificazioni. È possibile visualizzare/modificare le proprietà della pianificazione, assegnare canali e visualizzare gli schermi assegnati tramite il dashboard.

   ![chlimage_1-65](assets/chlimage_1-65.png)

   Consultate [Creare e gestire le pianificazioni](managing-schedules.md) per ottenere informazioni dettagliate sulle pianificazioni.

1. **Assegnazione di un canale**

   1. Navigate to the display from *Test_Project* --> **Locations** --> *TestLocation* --> *TestDisplay*.
   1. Select *TestDisplay* and tap/click **Assign Channel **from the action bar, *Or*,
   1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure below. **Viene visualizzata la finestra di dialogo Assegnazione** canale.
   1. Select **Reference Channel** by **path**.
   1. Selezionate il percorso **del** canale (*Test_Project* —> *Channels* —> *TestChannel* ) nel **canale**. Il ruolo **** canale verrà popolato automaticamente con il nome del canale.
   1. Select the **Priority** for this channel as *1*.
   1. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. Immettere **Schedule** e selezionare le date in **attivo da** e **attivo fino**. *(È necessario compilare questi campi solo se si desidera che il canale venga visualizzato per un particolare intervallo di tempo.)*
   1. Fai clic su **Salva**.
   Il canale viene assegnato e aggiunto al pannello.

   ![screen_shot_2019-03-04at92423am](assets/screen_shot_2019-03-04at92423am.png)

   Per ulteriori informazioni sulla finestra di dialogo Assegnazione **** canale e sulle proprietà ad essa associate, vedere Assegnazione [canale.](channel-assignment.md)

1. **Aggiunta di una pianificazione a un canale**

   1. Navigate to the display from *Test_Project* --> **Locations** --> *TestLocation* --> *TestDisplay*.
   1. Click **Dashboard** and select **+Assign Schedule** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure above. **Viene visualizzata la finestra di dialogo Assegnazione** pianificazione.
   1. Scegliete il percorso in cui avete creato la pianificazione (qui, *Test_Project* —> **Pianificazioni** —> *MorningSchedule*).
   1. Fai clic su **Salva** per aggiungere la pianificazione al canale.
   ![screen_shot_2019-03-04at93309am](assets/screen_shot_2019-03-04at93309am.png)

1. **Registrazione di un dispositivo**

   È necessario registrare il dispositivo mediante il dashboard di AEM.

   >[!NOTE]
   >
   >Potete aprire il lettore Screens utilizzando l&#39;app AEM Screens che avete scaricato o il browser Web.

   Per visualizzare il dispositivo in sospeso:

   1. Avvia una finestra separata del browser.
   1. Go to Screens player using the [web browser](http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html) or launch the AEM Screens app. Una volta aperto il dispositivo, vedrai che lo stato del dispositivo è non registrato.
   1. From the AEM dashboard, navigate to *Test_Project* --> **Devices**
   1. Click **Device Manager** from the action bar.
   1. Fai clic su Registrazione **** dispositivo per visualizzare i dispositivi in sospeso, come illustrato nella figura riportata di seguito.
   >[!NOTE]
   >
   >Se utilizzate AEM Screens Player come estensione ChromeOS, fate riferimento alla query in ***How to Install ChromeOS Player as Chrome Browser Plugin*** in [AEM Screens FAQ](aem-screens-faqs.md) .

   ![screen_shot_2019-03-04at94604am](assets/screen_shot_2019-03-04at94604am.png)

   Select the device you want to register and click **Register Device**.

   ![screen_shot_2019-03-04at94641am](assets/screen_shot_2019-03-04at94641am.png)

   Dovrai convalidare il codice di verifica dal browser web o da AEM Screens Player.

   Click **Validate** to navigate to **Device Registration** screen.

   ![screen_shot_2019-03-04at94738am](assets/screen_shot_2019-03-04at94738am.png)

   Enter **Title** and click **Register** and the device will be registered.

   Fate clic su **Fine** per completare il passaggio di registrazione del dispositivo.

   ![screen_shot_2019-03-04at94901am](assets/screen_shot_2019-03-04at94901am.png)

   Facendo clic su **Fine** si torna alla pagina del dispositivo in cui sono visualizzati i dispositivi non assegnati e assegnati.

   ![screen_shot_2019-03-04at94943am](assets/screen_shot_2019-03-04at94943am.png)

   >[!NOTE]
   >
   >Il dispositivo aggiunto viene visualizzato come **Non assegnato** con lo stato **Assegnato** .

1. **Assegnazione del dispositivo da visualizzare**

   Dopo aver registrato il dispositivo, è necessario assegnarlo a un display.

   Per assegnare un dispositivo, effettuate le operazioni seguenti:

   1. Selezionare il dispositivo da assegnare.
   1. Click **Assign Device** from the action bar.
   1. Select the display path for your channel as */content/screens/Test_Project/***Locations***/TestLocation/TestDisplay.*
   1. Click **Assign**.
   1. Click **Finish** to complete the process, and now the device is assigned.
   ![screen_shot_2019-03-04at95026am](assets/screen_shot_2019-03-04at95026am.png)

   Si apre il dashboard di visualizzazione e vengono visualizzate tutte le informazioni relative ai canali e alle pianificazioni assegnati insieme ai dettagli di configurazione del dispositivo.

   ![screen_shot_2019-03-04at95124am](assets/screen_shot_2019-03-04at95124am.png)

### Viewing the content in Screens Player {#viewing-the-content-in-screens-player}

Dopo aver aggiunto le configurazioni di cui sopra, il lettore deve mostrare automaticamente il canale predefinito per la visualizzazione sul dispositivo, ad esempio un&#39;immagine (in questo caso, un canale di sequenza e il contenuto è visibile in Screens Player per il browser Web).

![screen_shot_2019-03-04at95334am](assets/screen_shot_2019-03-04at95334am.png)

Per ulteriori informazioni sul lettore AEM Screens, consulta [AEM Screens Player](working-with-screens-player.md).

### Additional Resources {#additional-resources}

Per una conoscenza approfondita di tutti i moduli per Screens, consulta le risorse seguenti:

1. [Installazione e configurazione delle schermate](configuring-screens-introduction.md)
1. [Creare e gestire il progetto Screens](creating-a-screens-project.md)
1. [Assegna dispositivi](managing-devices.md)
1. [Creare e gestire canali](managing-channels.md)
1. [Creare e gestire le posizioni](managing-locations.md)
1. [Creare e gestire le visualizzazioni](managing-displays.md)
1. [Assegna canali](channel-assignment.md)
1. [Gestisci dispositivi](managing-devices.md)
1. [Creare e gestire le pianificazioni](managing-schedules.md)
1. [Lettore AEM Screens](working-with-screens-player.md)
1. [Risoluzione dei problemi relativi a Device Control Center](monitoring-screens.md)

