---
title: Rapporti sull’utilizzo e la condivisione delle risorse digitali.
description: Rapporti sulle risorse in [!DNL Adobe Experience Manager Assets] che consentono di comprendere l’utilizzo, l’attività e la condivisione delle risorse digitali.
contentOwner: AG
feature: Asset Reports,Asset Management
role: User,Admin
exl-id: 6f03ee04-d2e2-47e6-892b-50fad3043a28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 10%

---

# Rapporti sulle risorse {#asset-reports}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il reporting delle risorse consente di valutare l’utilità del [!DNL Adobe Experience Manager Assets] distribuzione. Con [!DNL Assets], puoi generare vari rapporti per le risorse digitali. I rapporti forniscono informazioni utili sull’utilizzo del sistema, su come gli utenti interagiscono con le risorse e quali risorse vengono scaricate e condivise.

Utilizza le informazioni contenute nei rapporti per derivare le metriche di successo chiave per misurare l’adozione di [!DNL Assets] all’interno dell’azienda e dai clienti.

La [!DNL Assets] utilizzo del framework di reporting [!DNL Sling] processi per elaborare in modo asincrono le richieste di rapporti in modo ordinato. È scalabile per archivi di grandi dimensioni. L’elaborazione asincrona dei rapporti aumenta l’efficienza e la velocità con cui vengono generati i rapporti.

L’interfaccia di gestione dei rapporti è intuitiva e include opzioni e controlli a grana fine per accedere ai rapporti archiviati e visualizzare gli stati di esecuzione dei rapporti (con esito positivo, non riuscito e in coda).

Quando viene generato un rapporto, riceverai una notifica tramite e-mail (opzionale) e una notifica tramite una casella in entrata. Puoi visualizzare, scaricare o eliminare un rapporto dalla pagina di elenco dei rapporti, in cui vengono visualizzati tutti i rapporti generati in precedenza.

## Prerequisito {#prerequisite-for-reporting}

Per generare i rapporti, accertati che:

* Abilita [!UICONTROL Day CQ DAM Event Recorder] servizio da **[!UICONTROL Strumenti]** > **[!UICONTROL Operazioni]** > **[!UICONTROL Console web]**.
* Seleziona le attività o gli eventi sui quali desideri creare rapporti. Ad esempio, per generare un rapporto sulle risorse scaricate, seleziona [!UICONTROL Risorsa scaricata (SCARICATA)].

![Abilitare il reporting delle risorse nella console Web](assets/reports-config-day-cq-dam-event-recorder.png)

## Genera report {#generate-reports}

[!DNL Experience Manager Assets] genera i seguenti rapporti standard:

* Caricare
* Scarica
* Scadenza
* Modifiche
* Pubblicazione
* [!DNL Brand Portal] pubblicazione
* Utilizzo disco
* File
* Condivisione collegamenti

[!DNL Adobe Experience Manager] gli amministratori possono generare e personalizzare facilmente questi rapporti per la tua implementazione. Un amministratore può seguire questi passaggi per generare un rapporto:

1. In [!DNL Experience Manager] interfaccia, fai clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Risorse]** > **[!UICONTROL Rapporti]**.

   ![Pagina degli strumenti per navigare nel rapporto delle risorse](assets/navigation.png)

1. Sulla [!UICONTROL Rapporti sulle risorse] pagina, fai clic su **[!UICONTROL Crea]** dalla barra degli strumenti.
1. Da **[!UICONTROL Pagina Crea rapporto]** scegliere il rapporto da creare e fare clic su **[!UICONTROL Successivo]**.

   ![Seleziona tipo di rapporto](assets/choose_report.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, i frammenti di contenuto e le condivisioni di collegamento sono inclusi nella risorsa [!UICONTROL Rapporto scaricato]. Seleziona l’opzione appropriata per creare un rapporto di condivisioni di collegamenti o per escludere frammenti di contenuto dal rapporto di download.

   >[!NOTE]
   >
   >La [!UICONTROL Scarica] Il rapporto visualizza i dettagli solo delle risorse selezionate singolarmente e scaricate o scaricate utilizzando la funzione Azione rapida. Tuttavia, non include i dettagli delle risorse che si trovavano all’interno di una cartella scaricata.

1. Configura i dettagli del rapporto come titolo, descrizione, miniatura e percorso della cartella nell&#39;archivio CRX in cui è memorizzato il rapporto. Per impostazione predefinita, il percorso della cartella è `/content/dam`. È possibile specificare un percorso diverso.

   ![Pagina per aggiungere i dettagli del rapporto](assets/report_configuration.png)

   Scegli l’intervallo di date per il rapporto.

   Puoi scegliere di generare il rapporto ora o in una data e in un’ora future.

   >[!NOTE]
   >
   >Se scegli di pianificare il rapporto in un secondo momento, accertati di specificare la data e l’ora nei campi Data e ora. Se non si specifica alcun valore, il motore di report lo considera come un report da generare immediatamente.

   I campi di configurazione possono variare a seconda del tipo di rapporto creato. Ad esempio, il **[!UICONTROL Utilizzo del disco]** Il rapporto fornisce opzioni per includere rappresentazioni delle risorse nel calcolo dello spazio su disco utilizzato dalle risorse. È possibile scegliere di includere o escludere le risorse nelle sottocartelle per il calcolo dell’utilizzo del disco.

   >[!NOTE]
   >
   >Il rapporto **[!UICONTROL Utilizzo spazio su disco]** non include campi intervallo di date, poiché indica solo l’utilizzo attuale dello spazio.

   ![Pagina dei dettagli del rapporto Utilizzo disco](assets/disk_usage_configuration.png)

   Quando crei la **[!UICONTROL File]** puoi includere o escludere le sottocartelle. Tuttavia, non puoi includere rappresentazioni di risorse per questo rapporto.

   ![Pagina dei dettagli del rapporto File](assets/files_report.png)

   Il rapporto **[!UICONTROL Condivisione collegamenti]** visualizza gli URL delle risorse condivise con utenti esterni da [!DNL Assets]. Include gli ID e-mail dell’utente che ha condiviso le risorse, gli ID e-mail degli utenti con cui le risorse sono condivise, la data di condivisione e la data di scadenza del collegamento. Le colonne non sono personalizzabili.

   La **[!UICONTROL Condivisione collegamenti]** report, non include opzioni per sottocartelle e rendering perché pubblica solo gli URL condivisi visualizzati in `/var/dam/share`.

   ![Pagina dei dettagli del rapporto Condivisione collegamenti](assets/link_share.png)

1. Fai clic su **[!UICONTROL Successivo]** dalla barra degli strumenti.

1. In **[!UICONTROL Configura colonne]** Per impostazione predefinita, alcune colonne sono selezionate per essere visualizzate nel rapporto. Puoi selezionare più colonne. Deseleziona una colonna selezionata per escluderla nel rapporto.

   ![Selezionare o deselezionare le colonne del rapporto](assets/configure_columns.png)

   Per visualizzare un nome di colonna o un percorso di proprietà personalizzato, configura le proprietà per il binario della risorsa in `jcr:content` in CRX. In alternativa, aggiungilo tramite il selettore del percorso della proprietà.

   ![Selezionare o deselezionare le colonne del rapporto](assets/custom_columns.png)

1. Fai clic su **[!UICONTROL Crea]** dalla barra degli strumenti. Un messaggio notifica l’avvio della generazione del rapporto.
1. Sulla [!UICONTROL Rapporti sulle risorse] lo stato di generazione del rapporto si basa, ad esempio, sullo stato corrente del processo di rapporto [!UICONTROL Completato], [!UICONTROL Non riuscito], [!UICONTROL In coda]oppure [!UICONTROL Pianificato]. Lo stesso stato viene visualizzato nella casella in entrata delle notifiche.Per visualizzare la pagina del rapporto, fare clic sul collegamento del rapporto. In alternativa, seleziona il rapporto e fai clic su **[!UICONTROL Visualizza]** dalla barra degli strumenti.

   ![Un rapporto generato](assets/report_page.png)

   Fai clic su **[!UICONTROL Scarica]** dalla barra degli strumenti per scaricare il rapporto in formato CSV.

## Aggiungi colonne personalizzate {#add-custom-columns}

Puoi aggiungere colonne personalizzate ai seguenti rapporti per visualizzare più dati per le tue esigenze personalizzate:

* Caricare
* Scarica
* Scadenza
* Modifiche
* Pubblicazione
* [!DNL Brand Portal] pubblicazione
* File

Per aggiungere colonne personalizzate a questi rapporti, effettua le seguenti operazioni:

1. In [!DNL Manager interface], fai clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Risorse]** > **[!UICONTROL Rapporti]**.
1. Sulla [!UICONTROL Rapporti sulle risorse] pagina, fai clic su **[!UICONTROL Crea]** dalla barra degli strumenti.

1. Da **[!UICONTROL Creare un rapporto]** scegliere il rapporto da creare e fare clic su **[!UICONTROL Successivo]**.
1. Configura i dettagli del rapporto come titolo, descrizione, miniatura, percorso della cartella e intervallo di date, a seconda delle necessità.

1. Per visualizzare una colonna personalizzata, specificane il nome in **[!UICONTROL Colonne personalizzate]**.

   ![Specifica il nome della colonna del report personalizzata](assets/custom_columns-1.png)

1. Aggiungi il percorso della proprietà sotto il `jcr:content` in CRXDE utilizzando il selettore del percorso della proprietà. In alternativa, digitare il percorso nel campo percorso della proprietà.

   ![Mappa il percorso della proprietà dai percorsi in jcr:content](assets/property_picker.png)

   In alternativa, digitare il percorso nel campo percorso della proprietà.

   ![property_path](assets/property_path.png)

   Per aggiungere altre colonne personalizzate, fai clic su **[!UICONTROL Aggiungi]** e ripetere i punti 5 e 6.

1. Fai clic su **[!UICONTROL Crea]** dalla barra degli strumenti. Un messaggio notifica l’avvio della generazione del rapporto.

## Configurare il servizio di eliminazione {#configure-purging-service}

Per rimuovere i rapporti non più necessari, configura il servizio di eliminazione dei rapporti DAM dalla console Web per eliminare i rapporti esistenti in base alla loro quantità ed età.

1. Accedi alla console Web (gestione della configurazione) da `https://[aem_server]:[port]/system/console/configMgr`.
1. Apri **[!UICONTROL Servizio di eliminazione dei report DAM]** configurazione.
1. Specifica la frequenza (intervallo di tempo) del servizio di eliminazione nel `scheduler.expression.name` campo . Puoi anche configurare la soglia di età e quantità per i rapporti.
1. Salva le modifiche.
