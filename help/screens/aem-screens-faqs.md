---
title: Domande frequenti su AEM Screens
seo-title: Domande frequenti su AEM Screens
description: Segui questa pagina per ottenere le risposte alle domande frequenti relative a un progetto AEM Screens.
seo-description: Segui questa pagina per ottenere le risposte alle domande frequenti relative a un progetto AEM Screens.
uuid: e394b1bd-1e63-4bd1-b669-923b2a298743
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: troubleshoot
discoiquuid: 558a7c2f-b32e-428e-89f6-123d72ca1108
translation-type: tm+mt
source-git-commit: 9f505017b80fe54e228daea9b248fb0a7db93ca2

---


# Domande frequenti su AEM Screens {#aem-screens-faqs}

La sezione seguente contiene le risposte alle domande frequenti più frequenti relative a un progetto AEM Screens.

## Gestione del canale {#channel-management}

### Qual è la differenza tra un canale online e un canale offline? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***Canale online*** mostra il contenuto aggiornato in ambiente in tempo reale, mentre in ***Canale offline*** mostra il contenuto della cache.

### Come si crea un canale online? {#how-do-i-make-a-channel-online}

Seleziona il canale e vai alle proprietà del canale dalla barra delle azioni. Per rendere il canale online, selezionate la modalità **Sviluppatore (forzate il canale ad essere online)** nella scheda **Canale** .

### Qual è l&#39;utilizzo del campo Ruolo canale? {#what-is-the-use-of-the-channel-role-field}

Il ruolo canale è l&#39;astrazione del canale effettivo eseguito in modo che l&#39;autore possa concentrarsi direttamente sull&#39;esperienza generica. Potete considerarlo come un tipo di tag che identifica in modo univoco il canale nel suo contesto (visualizzazione o pianificazione).

### Come si realizza la risoluzione effettiva dei canali? {#how-does-actual-channel-resolution-happen}

Per i riferimenti ** statici, la risoluzione segue semplicemente il percorso specificato.

Per i riferimenti ** dinamici, la risoluzione si verifica quando il canale viene assegnato al display (non alla pianificazione). Il percorso di visualizzazione diventa il contesto del canale e la risoluzione si realizza come segue (priorità massima a priorità più bassa):

1. La visualizzazione ha un nodo figlio che corrisponde al nome del canale di riferimento
1. La visualizzazione ha un nodo di pari livello che corrisponde al nome del canale di riferimento
1. La posizione padre della visualizzazione ha un nodo secondario che corrisponde al nome del canale di riferimento
1. La posizione principale della visualizzazione ha un nodo secondario che corrisponde al nome del canale di riferimento

E così via, finché non raggiungete la cartella delle posizioni e vi fermate al momento (in modo da non poter fare riferimento a un canale che si troverebbe nella cartella dei canali, ad esempio, solo ai canali nella sottostruttura delle posizioni).

## Registrazione dispositivo {#device-registration}

### Se scopro endpoint come richieste di registrazione e onboarding del dispositivo, posso creare script su un gran numero di dispositivi e registrare tali dispositivi. Oltre a bloccare questo a un ramo Wi-Fi, è possibile proteggere queste richieste? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Attualmente la registrazione è possibile solo nell’istanza di creazione. Anche se il servizio di registrazione non è autenticato, creerà solo un dispositivo in sospeso in AEM e non registrerà il dispositivo né assegnerà alcun display.

Per registrare un dispositivo (ovvero creare un utente per il dispositivo in AEM), dovete comunque autenticare AEM e al momento seguire manualmente la procedura guidata di registrazione per completare la registrazione. In teoria, un utente malintenzionato può creare diversi dispositivi in sospeso, ma non può registrarne alcuno senza un accesso AEM.

### Esiste un modo per trasformare le richieste HTTP GET in HTTP POST con una qualche forma di autenticazione? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La richiesta di registrazione è una richiesta POST.

Si consiglia di ottenere l’ID dispositivo dalla sessione anziché passarlo come parametro. In questo modo si puliscono i registri del server, la cache del browser e così via. Attualmente non si tratta di un problema di sicurezza. Tenete presente che GET semanticamente viene utilizzato quando non vi è alcuna modifica dello stato sul server e POST viene utilizzato in caso di modifica dello stato.

### Esiste un modo per rifiutare una richiesta di registrazione del dispositivo?

Non potete rifiutare le richieste di registrazione. Al contrario, le richieste di registrazione dovrebbero scadere dopo un timeout configurato nella console Web di Adobe Experience Manager.

Per impostazione predefinita, questo valore è impostato su un giorno e viene memorizzato in una cache della memoria.

## Monitoraggio dei dispositivi e rapporti sullo stato {#device-monitoring-and-health-reports}

### Come si risolve il problema se il lettore AEM Screens mostra uno schermo vuoto? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Per risolvere il problema dello schermo vuoto, verificare le seguenti possibilità:

* AEM non è in grado di inviare il contenuto offline
* Il canale non ha contenuto
* Nessuna delle risorse è pianificata per essere visualizzata al momento.

### Cosa posso fare se il lettore AEM Screens non riesce a registrarsi e il suo stato viene visualizzato come Errore? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

È necessario abilitare il filtro Apache Sling Referrer Filter Allow Empty. Questo è richiesto per un funzionamento ottimale del protocollo di controllo tra AEM Screens Player e il server AEM Screens.

1. Passa alla configurazione della console Web di **Adobe Experience Manager**
1. Selezionare l&#39;opzione **allow.empty **.
1. Fai clic su **Salva**.

### Come risolvere il problema se durante la registrazione di un lettore di AEM Screens, il dispositivo mostra FAILURE e i registri di console visualizzano l&#39;errore ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Questo problema può verificarsi se il lettore non è in grado di trovare il DNS del server AEM Screens. È possibile provare a utilizzare l&#39;indirizzo IP per la connessione. Per ottenere l’IP del server, utilizzate: *arp &lt;server_dns_name>*.

### AMS consiglia di implementare un Android Watchdog su tutti i dispositivi? Il plugin Watchdog (Cordova) è incluso come parte del APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un cane da guardia Android multipiattaforma che utilizza API Android pure è già una parte dell&#39;apk. Non è necessario alcun software aggiuntivo, ma a seconda del dispositivo utilizzato, potrebbe essere necessario ridimensionare l&#39;apk per ottenere privilegi di sistema per un ciclo di alimentazione completo (Powermanager api). Se non viene rassegnato utilizzando i tasti del produttore, si chiude e si riavvia l&#39;applicazione ma non il ciclo di alimentazione.

Per ulteriori informazioni su come implementare Android Player, consultate [**Implementazione di Android Player **](implementing-android-player.md).

### Quali strumenti di monitoraggio remoto e di allarme (software) di terze parti sono consigliati da Adobe/AMS per monitorare ciascun dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

A seconda delle esigenze in termini di monitoraggio e avvisi, un nuovo servizio di notifica delle schermate AEM segnala se un dispositivo non ha eseguito il ping nel tempo. Gli strumenti di terze parti dipenderanno dal sistema operativo in uso, dalle sue funzionalità e dalle esigenze specifiche del cliente.

Per ulteriori informazioni sulle aree in cui è possibile monitorare l&#39;attività dei dispositivi, consultate il servizio [**di notifica **](screens-notifications-service.md)AEM Screens.

### Utilizzando la topologia del dispositivo di pubblicazione con Smart Sync, i dispositivi sono ancora collegati direttamente all&#39;istanza di creazione per istantanee e funzioni di battito cardiaco?

No, i dispositivi non sono collegati direttamente all’autore. Le istanze pubblicate vengono segnalate e l’autore del rapporto ne esegue il sondaggio per verificare la disponibilità di aggiornamenti.

## Lettore AEM Screens {#aem-screens-player}

### Come installare il lettore ChromeOS come plug-in browser Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

Il lettore ChromeOS può essere installato come il plugin Chrome Browser in modalità sviluppatore senza richiedere un dispositivo effettivamente chrome player. Per l’installazione, effettuate le seguenti operazioni:

1. Clicca [qui](https://download.macromedia.com/screens/) per scaricare la versione più recente di Chrome Player.
1. Decomprimete il file e salvatelo su disco.
1. Aprite il browser Chrome e fate clic sul menu a 3 punti e selezionate **Altri strumenti** —> **Estensioni** dall&#39;angolo in alto a destra oppure passate direttamente a ***chrome://extensions***.
1. Attivate la modalità **** Sviluppatore dall&#39;angolo in alto a destra.
1. Fare clic su **Load Unimballato **dall&#39;angolo superiore sinistro e caricare il lettore Chrome decompresso.
1. Se disponibile nell&#39;elenco delle estensioni, controllate il plug-in **AEM Screens Chrome Player** .
1. Aprite una nuova scheda e fate clic sull&#39;icona **App** dall&#39;angolo in alto a sinistra oppure passate direttamente a ***chrome://apps***.
1. Fate clic su **AEM Screens** Plugin per avviare Chrome Player. Per impostazione predefinita, il lettore viene avviato in modalità a schermo intero. Premere **esc** per uscire dalla modalità a schermo intero.

### Come risolvere il problema se il lettore Screens non è in grado di eseguire l&#39;autenticazione tramite l&#39;istanza di pubblicazione con un gestore di errori personalizzato? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Quando viene avviato il lettore AEM Screens, invia una richiesta a ***/content/screens/svc.ping.json***, quando il lettore riceve un errore 404. Il lettore avvia una richiesta di autenticazione per l’autenticazione rispetto all’istanza di pubblicazione. Se nell’istanza di pubblicazione è presente un gestore errori personalizzato, accertatevi di restituire il codice di stato 404 per l’utente anonimo all’indirizzo ***/content/screens/svc.ping.json***.

### Come impostare lo schermo del dispositivo su un lettore Android?

Seguite i passaggi indicati di seguito per attivare Stay Awake su qualsiasi lettore Android:

1. Passa alle impostazioni del lettore Android -> **Informazioni**
1. Toccate 7 volte il numero di build per abilitare le opzioni per sviluppatori in Impostazioni
1. Vai a Opzioni **sviluppatore**
1. Abilita **veglia**

### Se un aggiornamento viene inviato da AEM e il lettore non è in linea, esiste un meccanismo di tentativi che verifica se il dispositivo è tornato online per distribuire il contenuto aggiornato? Inoltre, per quanto tempo ci vuole?

Il prossimo ping dal dispositivo che arriva vedrà un&#39;ultima modifica che è più recente di quello che ha e che verrà scaricato questo nuovo contenuto.
Proverà per sempre finché un ping non riesce.

### Utilizzo delle risorse {#using-assets}

### Come utilizzare i video in un canale AEM Screens maggiore di 2 GB? {#how-to-use-videos-in-an-aem-screens-channel-larger-than-gb}

Per impostazione predefinita, l’interfaccia touch di AEM Assets non consente di caricare risorse maggiori di 2 GB a causa di un limite di dimensione file in un canale AEM Screens. Tuttavia, potete sovrascrivere questo limite entrando in CRXDE Lite e creando un nodo sotto la directory /apps.

Per informazioni dettagliate su come configurare un limite di dimensione file più elevato (ad esempio, 30 GB) nella directory */apps* , consultate *Configurazione per caricare risorse video più grandi di 2 GB* in [Gestione delle risorse](/help/assets/managing-video-assets.md)video.

### Suggerimenti generali per la risoluzione dei problemi {#general-troubleshooting}

### Come disattivare Livefyre per evitare l&#39;errore A/P Screens?

Per disattivare Livefyre per evitare errori di registro:

**Disattivazione del bundle Livefyre:**

1. Accedi a `http://<host>:<port>/system/console/bundles`
1. Cercate il bundle AEM Livefyre:  *com.adobe.cq.social.cq-social-livefyre*
1. Fate clic su **Interrompi**.

**Disattivazione del poller Livefyre:**

1. In CRXDE Lite, andate a */etc/importer/polling/livefyre-poller/jcr:content*
1. Aggiungi una nuova proprietà abilitata tipo Boolean
1. Imposta proprietà **** enabled su **false**
