---
title: Home page Experience di AEM Assets
description: Personalizza la home page di AEM Assets per un’esperienza ricca di schermate di benvenuto, con un’istantanea delle attività recenti relative alle risorse.
contentOwner: AG
feature: Strumenti per sviluppatori,Gestione risorse
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 1%

---

# Home page Experience di AEM Assets {#aem-assets-home-page-experience}

Personalizza la home page di AEM Assets per un’esperienza ricca di schermate di benvenuto, con un’istantanea delle attività recenti relative alle risorse.

La home page di Adobe Experience Manager (AEM) Assets offre un’esperienza ricca e personalizzata con schermata di benvenuto, che include un’istantanea delle attività recenti, come le risorse visualizzate o caricate di recente.

Per impostazione predefinita, la home page delle risorse è disabilitata. Per abilitarlo, esegui le seguenti operazioni:

1. Per accedere AEM Configuration Manager, fare clic su **[!UICONTROL Strumenti > Operazione > Console Web]**.
1. Apri il servizio **Day CQ DAM Event Recorder** .
1. Seleziona il **[!UICONTROL Abilita questo servizio]** per abilitare la registrazione delle attività.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Dall’elenco **Tipi di eventi**, seleziona gli eventi da registrare e salva le modifiche.

   >[!CAUTION]
   >
   >Attivando le opzioni di visualizzazione Risorsa visualizzata, Progetti visualizzati e Raccolte, si aumenta in modo significativo il numero di eventi registrati.

1. Apri il servizio **[!UICONTROL DAM Asset Home Page Feature Flag]** da Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Seleziona l’opzione **[!UICONTROL isEnabled.name]** per abilitare la funzione Home page di Assets. Salva le modifiche.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Apri la finestra di dialogo **[!UICONTROL Preferenze utente]** e seleziona **[!UICONTROL Abilita pagina iniziale risorse]**. Salva le modifiche.

   ![user_preferences](assets/user_preferences.png)

Dopo aver abilitato la home page di Assets, passa all’interfaccia utente Assets dalla pagina di navigazione.

![home_page](assets/home_page.png)

Tocca/fai clic su **[!UICONTROL Fai clic qui per configurare il collegamento esperienza]** per aggiungere nome utente, immagine di sfondo e immagine di profilo.

La home page delle risorse include le sezioni seguenti:

* Sezione di benvenuto
* Sezione Widget

**Sezione di benvenuto**

Se il tuo profilo esiste, nella sezione Benvenuto viene visualizzato un messaggio di benvenuto a te indirizzato. Inoltre, mostra l’immagine del tuo profilo e un’immagine di benvenuto (se configurata).

Se il profilo è incompleto, nella sezione Benvenuto vengono visualizzati un messaggio di benvenuto generico e un segnaposto per l’immagine del profilo.

**Sezione Widget**

Questa sezione viene visualizzata sotto la sezione Benvenuto e presenta i widget preconfigurati nelle sezioni seguenti:

* Attività
* Recente
* Scopri

**Attività**: In questa sezione, il  **widget** Attività personale visualizza le attività recenti eseguite dall’utente connesso con risorse (incluse risorse senza rendering), ad esempio caricamenti di risorse, download, creazione di risorse, modifiche, commenti, annotazioni e condivisioni.

**Recenti**: Il  **widget** Visualizzato di recente in questa sezione visualizza le entità a cui l’utente ha effettuato l’accesso di recente, incluse cartelle, raccolte e progetti.

**Scopri**: Il  **** widget in questa sezione visualizza le risorse e le rappresentazioni recentemente caricate nell’istanza di AEM Assets.

Per abilitare l&#39;eliminazione dei dati delle attività utente, abilita il **servizio di eliminazione degli eventi DAM** da Configuration Manager. Dopo aver abilitato questo servizio, le attività dell&#39;utente connesso che superano un numero specificato vengono eliminate dal sistema.

La schermata introduttiva fornisce semplici strumenti di navigazione, ad esempio icone sulla barra degli strumenti per accedere a cartelle, raccolte e cataloghi.

>[!NOTE]
>
>L’abilitazione dei servizi Day CQ DAM Event Recorder e DAM Event Purge aumenta le operazioni di scrittura su JCR e l’indicizzazione della ricerca, che aumentano notevolmente il carico sul server AEM. Il carico aggiuntivo sul server AEM può influire sulle prestazioni.

>[!CAUTION]
>
>L’acquisizione, il filtraggio e l’eliminazione delle attività utente necessarie per la home page di Assets generano un sovraccarico delle prestazioni. Pertanto, gli amministratori devono configurare la home page in modo efficace per gli utenti target.
>
>L’Adobe consiglia agli amministratori e agli utenti che eseguono operazioni in blocco di evitare di utilizzare la funzione Home page della risorsa per evitare un aumento delle attività degli utenti. Inoltre, gli amministratori possono escludere le attività di registrazione per utenti specifici configurando **Day CQ DAM Event Recorder** da Configuration Manager.
>
>Se utilizzi questa funzione, Adobe consiglia di pianificare la frequenza di eliminazione in base al carico del server.
