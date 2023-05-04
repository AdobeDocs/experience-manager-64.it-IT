---
title: Utilizzare la funzione Assets Insights per tenere traccia dell’utilizzo delle immagini
description: La funzione Assets Insights ti consente di monitorare le valutazioni degli utenti e le statistiche di utilizzo delle immagini utilizzate in siti web di terze parti, campagne di marketing e soluzioni creative di Adobe.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 7%

---

# Informazioni sulle risorse {#asset-insights}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Scopri come la funzione Assets Insights ti consente di monitorare le valutazioni degli utenti e le statistiche di utilizzo delle risorse utilizzate nei siti web di terze parti, nelle campagne di marketing e nelle soluzioni creative di Adobe.

La funzione Assets Insights ti consente di monitorare le valutazioni degli utenti e le statistiche di utilizzo delle risorse utilizzate in siti web di terze parti, campagne di marketing e soluzioni creative di Adobe per ricavare informazioni sulle loro prestazioni e popolarità.

Informazioni sulle risorse acquisisce i dettagli delle attività dell’utente, ad esempio il numero di volte in cui una risorsa viene valutata, su cui è stato fatto clic e le impression (il numero di volte in cui la risorsa viene caricata sul sito web). Assegna punteggi alle risorse in base a queste statistiche. Puoi utilizzare i punteggi e le statistiche sulle prestazioni per selezionare le risorse più comuni da includere nei cataloghi, nelle campagne di marketing e così via. Puoi anche formulare criteri di archiviazione e rinnovo delle licenze per le risorse in base a queste statistiche.

Affinché Assets Insights possa acquisire le statistiche di utilizzo delle risorse da un sito web, devi includere il codice di incorporamento della risorsa nel codice del sito web.

Per consentire a Assets Insights di visualizzare le statistiche di utilizzo per le risorse, configura prima la funzione per recuperare i dati di reporting da [!DNL Adobe Analytics]. Per maggiori dettagli, vedi [Configurare Assets Insights](touch-ui-configuring-asset-insights.md). Per utilizzare questa funzione in un’installazione on-premise, acquista [!DNL Adobe Analytics] licenza separatamente. Clienti su [!DNL Managed Services] ricevere [!DNL Analytics] licenza abbinata a [!DNL Experience Manager]. Vedi [Descrizione del prodotto Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html).

>[!NOTE]
>
>Gli approfondimenti sono supportati e forniti solo per le immagini.

## Visualizzare le statistiche di una risorsa {#viewing-statistics-for-an-asset}

Puoi visualizzare i punteggi di Assets Insights dalla pagina dei metadati.

1. Dall’interfaccia utente di Assets, seleziona la risorsa e quindi tocca o fai clic sul pulsante **[!UICONTROL Proprietà]** dalla barra degli strumenti.
1. Dalla pagina Proprietà , tocca o fai clic sul pulsante **[!UICONTROL Informazioni approfondite]** scheda .
1. Esamina i dettagli di utilizzo della risorsa nella sezione **[!UICONTROL Informazioni approfondite]** scheda . La **[!UICONTROL Punteggio]** descrive le origini di utilizzo e prestazioni totali di una risorsa .

   Il punteggio di utilizzo descrive il numero di volte in cui la risorsa viene utilizzata in varie soluzioni.

   La **[!UICONTROL Impressioni]** punteggio è il numero di volte in cui la risorsa viene caricata sul sito web. Numero visualizzato sotto **[!UICONTROL Clic]** è il numero di volte in cui viene fatto clic sulla risorsa.

1. Consulta la sezione **[!UICONTROL Statistiche di utilizzo]** per sapere di quali entità faceva parte la risorsa e quali soluzioni creative l’ha utilizzata di recente. Maggiore è l’utilizzo, maggiori sono le probabilità che la risorsa sia popolare tra gli utenti. I dati di utilizzo vengono visualizzati sotto le seguenti intestazioni:

   * **[!UICONTROL Risorsa]**: Il numero di volte in cui la risorsa faceva parte di una raccolta o di una risorsa composta
   * **[!UICONTROL Web e dispositivi mobili]**: Il numero di volte in cui la risorsa faceva parte di siti web e app
   * **[!UICONTROL Social]**: Il numero di volte in cui la risorsa è stata utilizzata nelle soluzioni, come Adobe Social e Adobe Campaign
   * **[!UICONTROL E-mail]**: Il numero di volte in cui la risorsa è stata utilizzata nelle campagne e-mail

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >La funzione Assets Insights recupera i dati delle soluzioni da [!DNL Adobe Analytics] periodicamente, la sezione soluzioni potrebbe non visualizzare i dati più recenti. Il periodo di tempo per il quale vengono visualizzati i dati dipende dalla pianificazione dell’operazione di recupero da eseguire in Assets Insights [!DNL Analytics] dati.

1. Per visualizzare graficamente le statistiche sulle prestazioni della risorsa in un arco di tempo, seleziona il periodo nella sezione **[!UICONTROL Statistiche di prestazioni]**. I dettagli, compresi clic e impression, vengono visualizzati come linee di tendenza di un grafico.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >A differenza dei dati nella sezione delle soluzioni , la sezione statistiche sulle prestazioni visualizza i dati più recenti.

1. Per ottenere il codice di incorporamento della risorsa inclusa nei siti web per ottenere i dati sulle prestazioni, fai clic su **[!UICONTROL Ottieni codice di incorporamento]** sotto la miniatura della risorsa. Per ulteriori informazioni su come includere il codice da incorporare in pagine web di terze parti, consulta [Utilizzo del tracciamento pagina e del codice da incorporare nelle pagine web](touch-ui-using-page-tracker.md).

   ![chlimage_1-303](assets/chlimage_1-303.png)

## Visualizzare le statistiche aggregate per le risorse {#viewing-aggregate-statistics-for-assets}

Dalla **[!UICONTROL Visualizzazione approfondimenti]** puoi visualizzare simultaneamente un punteggio di tutte le risorse presenti all’interno di una cartella.

1. Nell’interfaccia utente di Assets, passa alla cartella contenente le risorse per le quali desideri visualizzare le informazioni.
1. Tocca o fai clic sull’icona Layout nella barra degli strumenti, quindi scegli **[!UICONTROL Visualizzazione approfondimenti]**.
1. Nella pagina vengono visualizzati i punteggi di utilizzo delle risorse. Confronta le valutazioni delle varie risorse e trai informazioni approfondite.

## Pianifica processo in background {#scheduling-background-job}

Assets Insights recupera periodicamente i dati di utilizzo per le risorse dalle suite di rapporti di Adobe Analytics. Per impostazione predefinita, Assets Insights esegue un processo in background ogni 24 ore alle 2 del mattino fino ai dati di recupero. Tuttavia, puoi modificare sia la frequenza che il tempo configurando il **[!UICONTROL Processo di sincronizzazione dei rapporti sulle prestazioni delle risorse DAM di Adobe CQ]** servizio dalla console web.

1. Tocca [!DNL Experience Manager] e vai a **[!UICONTROL Strumenti > Operazioni > Console web]**.
1. Apri **[!UICONTROL Processo di sincronizzazione dei rapporti sulle prestazioni delle risorse DAM di Adobe CQ]** configurazione del servizio.

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. Specifica la frequenza di pianificazione desiderata e l’ora di inizio del processo nell’espressione di pianificazione delle proprietà. Salva le modifiche.
