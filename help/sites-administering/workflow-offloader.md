---
title: Offloader flusso di lavoro risorse
seo-title: Offloader flusso di lavoro risorse
description: Ulteriori informazioni sul flusso di lavoro Assets Offloader.
seo-description: Ulteriori informazioni sul flusso di lavoro Assets Offloader.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 2%

---


# Offloader flusso di lavoro risorse{#assets-workflow-offloader}

Lo scaricatore del flusso di lavoro di Assets consente di abilitare più istanze di Adobe Experience Manager (AEM) Assets per ridurre il carico di elaborazione sull’istanza principale (riempimento iniziale). Il carico di elaborazione viene distribuito tra l&#39;istanza di riempimento iniziale e le varie istanze offload (Worker) ad essa aggiunte. La distribuzione del carico di elaborazione delle risorse aumenta l’efficienza e la velocità con cui  AEM Assets elabora le risorse. Inoltre, consente di allocare risorse dedicate per elaborare risorse di un particolare tipo MIME. Ad esempio, potete allocare un nodo specifico nella topologia per elaborare solo risorse  InDesign.

## Configurare la topologia offloader {#configure-offloader-topology}

Utilizzate Configuration Manager per aggiungere l&#39;URL per l&#39;istanza leader e i nomi host delle istanze offloader per le richieste di connessione nell&#39;istanza leader.

1. Toccate/fate clic sul logo AEM e scegliete **Strumenti** > **Operazioni** > **Console Web** per aprire Gestione configurazione.
1. Dalla console Web, selezionare **Sling** > **Gestione topologia**.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Nella pagina Gestione topologia, tocca o fai clic sul collegamento **Configura servizio Discovery.Oak**.

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Nella pagina Configurazione servizio di individuazione, specificate l&#39;URL del connettore per l&#39;istanza leader nel campo **URL del connettore topologia**.

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. Nel campo **Whitelist del connettore topologia**, specificate l&#39;indirizzo IP o i nomi host delle istanze offloader che possono connettersi all&#39;istanza leader. Toccate/fate clic su **Salva**.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Per visualizzare le istanze offloader collegate all&#39;istanza leader, passare a **Strumenti** > **Distribuzione** > **Topologia** e toccare/fare clic sulla vista Cluster.

## Disattivazione dell&#39;offload {#disable-offloading}

1. Toccate/fate clic sul logo AEM e scegliete **Strumenti** > **Distribuzione** > **Offload**. La pagina **Scaricamento del browser** visualizza gli argomenti e le istanze del server che possono utilizzare gli argomenti.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Disattiva l&#39;argomento *com/adobe/granite/workflow/offloading* sulle istanze iniziali con cui gli utenti interagiscono per caricare o modificare AEM risorse.

   ![chlimage_1-49](assets/chlimage_1-49.png)

## Configurare i avviatori di workflow sull&#39;istanza iniziale {#configure-workflow-launchers-on-the-leader-instance}

Configurate gli avviatori del flusso di lavoro per utilizzare il flusso di lavoro **Aggiornamento DAM Asset Offloading** sull&#39;istanza principale invece del flusso di lavoro **Aggiorna risorsa Dam**.

1. Toccate/fate clic sul logo AEM e scegliete **Strumenti** > **Flusso di lavoro** > **Avviatori** per aprire la console **Avviatori flusso di lavoro**.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Individuate le due configurazioni di avvio con il tipo di evento **Node Create** e **Node Modified** rispettivamente, che eseguono il flusso di lavoro **DAM Update Asset**.
1. Per ogni configurazione, seleziona la casella di controllo prima e tocca o fai clic sull&#39;icona **Visualizza proprietà** nella barra degli strumenti per visualizzare la finestra di dialogo **Proprietà di avvio**.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Nell&#39;elenco **Workflow**, scegliere **Aggiornamento DAM Asset Offloading** e toccare o fare clic su **Salva**.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. Toccate/fate clic sul logo AEM e scegliete **Strumenti** > **Workflow** > **Modelli** per aprire la pagina **Modelli di workflow**.
1. Selezionate il flusso di lavoro **DAM Update Asset Offloading**, quindi toccate o fate clic su **Edit** dalla barra degli strumenti per visualizzarne i dettagli.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Visualizzare il menu di scelta rapida per il passaggio **Scaricamento del flusso di lavoro DAM** e scegliere **Modifica**. Verificare la voce nel campo **Argomento processo** della scheda **Argomenti generici** della finestra di dialogo di configurazione.

   ![chlimage_1-54](assets/chlimage_1-54.png)

## Disabilitare gli avviatori del flusso di lavoro sulle istanze offload {#disable-the-workflow-launchers-on-the-offloader-instances}

Disattivate i avviatori del flusso di lavoro che eseguono il flusso di lavoro **DAM Update Asset** sull&#39;istanza iniziale.

1. Toccate/fate clic sul logo AEM e scegliete **Strumenti** > **Flusso di lavoro** > **Avviatori** per aprire la console **Avviatori flusso di lavoro**.

   ![chlimage_1-55](assets/chlimage_1-55.png)

1. Individuate le due configurazioni di avvio con il tipo di evento **Node Create** e **Node Modified** rispettivamente, che eseguono il flusso di lavoro **DAM Update Asset**.
1. Per ogni configurazione, seleziona la casella di controllo prima e tocca o fai clic sull&#39;icona **Visualizza proprietà** nella barra degli strumenti per visualizzare la finestra di dialogo **Proprietà di avvio**.

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. Nella sezione **Activate **, trascinare il cursore per disattivare l&#39;avvio del flusso di lavoro e toccare/fare clic su **Save** per disattivarlo.

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. Caricate qualsiasi risorsa di tipo immagine nell’istanza di riempimento iniziale. Verifica le miniature generate e riportate di nuovo per la risorsa dall’istanza scaricata.

