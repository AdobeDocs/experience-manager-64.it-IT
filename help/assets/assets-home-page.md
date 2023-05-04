---
title: "[!DNL Experience Manager Assets] Home Page Experience"
description: Personalizza la home page delle risorse per un’esperienza ricca di schermate di benvenuto, con un’istantanea delle attività recenti relative alle risorse.
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 3%

---

# [!DNL Adobe Experience Manager Assets] Esperienza home page {#aem-assets-home-page-experience}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Personalizza le [!DNL Experience Manager Assets] Pagina principale per un’esperienza ricca di schermate di benvenuto, che include un’istantanea delle attività recenti relative alle risorse.

La [!DNL Adobe Experience Manager Assets] La home page offre un’esperienza ricca e personalizzata con schermata di benvenuto, che include un’istantanea delle attività recenti, come le risorse visualizzate o caricate di recente.

Per impostazione predefinita, la home page delle risorse è disabilitata. Per abilitarlo, esegui le seguenti operazioni:

1. Per accedere [!DNL Experience Manager] Gestione configurazione, fai clic su **[!UICONTROL Strumenti > Operazione > Console web]**.
1. Apri **Day CQ DAM Event Recorder** servizio.
1. Seleziona la **[!UICONTROL Abilita questo servizio]** per abilitare la registrazione dell’attività.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Da **Tipi di eventi** seleziona gli eventi da registrare e salva le modifiche.

   >[!CAUTION]
   >
   >Attivando le opzioni di visualizzazione Risorsa visualizzata, Progetti visualizzati e Raccolte, si aumenta in modo significativo il numero di eventi registrati.

1. Apri **[!UICONTROL Flag di funzione della pagina iniziale della risorsa DAM]** servizio da Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Seleziona la **[!UICONTROL isEnabled.name]** per abilitare la funzionalità Home page delle risorse. Salva le modifiche.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Apri **[!UICONTROL Preferenze utente]** e seleziona **[!UICONTROL Abilita pagina iniziale risorse]**. Salva le modifiche.

   ![user_preferences](assets/user_preferences.png)

Dopo aver abilitato la home page di Assets, passa all’interfaccia utente Assets dalla pagina di navigazione.

![home_page](assets/home_page.png)

Tocca o fai clic sul pulsante **[!UICONTROL Fai clic qui per configurare il collegamento esperienza]** per aggiungere nome utente, immagine di sfondo e immagine di profilo.

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

**Attività**: In questa sezione, il **Attività personale** widget visualizza le attività recenti eseguite dall’utente connesso con risorse (incluse risorse senza rendering), ad esempio caricamenti di risorse, download, creazione di risorse, modifiche, commenti, annotazioni e condivisioni.

**Recente**: La **Visualizzato di recente** in questa sezione vengono visualizzate le entità a cui l&#39;utente ha effettuato l&#39;accesso, incluse cartelle, raccolte e progetti.

**Scopri**: La **Nuovo** in questa sezione vengono visualizzate le risorse e i rendering caricati di recente in [!DNL Assets] istanza.

Per abilitare l’eliminazione dei dati dell’attività utente, abilita **Servizio di eliminazione degli eventi DAM** da Configuration Manager. Dopo aver abilitato questo servizio, le attività dell&#39;utente connesso che superano un numero specificato vengono eliminate dal sistema.

La schermata introduttiva fornisce semplici strumenti di navigazione, ad esempio icone sulla barra degli strumenti per accedere a cartelle, raccolte e cataloghi.

>[!NOTE]
>
>L’abilitazione dei servizi Day CQ DAM Event Recorder e DAM Event Purge aumenta le operazioni di scrittura su JCR e l’indicizzazione della ricerca, che aumentano notevolmente il carico sul JCR. [!DNL Experience Manager] server. Il carico aggiuntivo sul [!DNL Experience Manager] il server può influire sulle sue prestazioni.

>[!CAUTION]
>
>L’acquisizione, il filtraggio e l’eliminazione delle attività utente necessarie per la home page di Assets generano un sovraccarico delle prestazioni. Pertanto, gli amministratori devono configurare la home page in modo efficace per gli utenti target.
>
>L’Adobe consiglia agli amministratori e agli utenti che eseguono operazioni in blocco di evitare di utilizzare la funzione Home page della risorsa per evitare un aumento delle attività degli utenti. Inoltre, gli amministratori possono escludere le attività di registrazione per utenti specifici configurando **Day CQ DAM Event Recorder** da Configuration Manager.
>
>Se utilizzi questa funzione, Adobe consiglia di pianificare la frequenza di eliminazione in base al carico del server.
