---
title: Elabora risorse per eseguire processi aziendali, eseguire audit, ottenere conformità e mantenere l'integrità di base
description: Elaborazione delle risorse per convertire i formati, creare rappresentazioni, gestire le risorse, convalidare le risorse ed eseguire flussi di lavoro.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a7d6e9fa5d72eba0899f0aadea393fe0e9126a34

---


# Elabora risorse digitali {#process-assets}

[!DNL Adobe Experience Manager Assets] consente di lavorare sulle risorse digitali in molti modi per consentire una solida elaborazione delle risorse. È possibile utilizzare i metodi di elaborazione disponibili o estendere i metodi per garantire il completamento completo dei processi aziendali end-to-end utilizzando, eseguendo verifiche e conformità, individuazione e distribuzione delle risorse digitali e dell&#39;integrità di base. Potete fare tutto questo raggiungendo la scala e la personalizzazione richieste.

## Comprendere i flussi di lavoro {#understand-workflows}

Per l’elaborazione delle risorse, [!DNL Experience Manager] utilizza i flussi di lavoro. I flussi di lavoro consentono di automatizzare la logica o le attività aziendali. Per impostazione predefinita vengono forniti passaggi granulari per eseguire attività specifiche e gli sviluppatori possono creare i propri passi personalizzati. Questi passaggi possono essere combinati in un ordine logico per creare flussi di lavoro. Ad esempio, un flusso di lavoro può applicare automaticamente una filigrana alle immagini caricate in base a criteri specifici, quali i metadati incorporati in un’immagine, la cartella in cui viene caricata, la risoluzione dell’immagine e così via. Un altro esempio è rappresentato da un flusso di lavoro configurato per applicare filigrane alle immagini e per soddisfare contemporaneamente più esigenze di gestione delle risorse, come l’aggiunta di metadati, la creazione di rappresentazioni, l’aggiunta di tag avanzati per l’individuazione delle risorse, la pubblicazione in un datastore, l’impostazione delle autorizzazioni per l’accesso degli utenti e così via.

## Flussi di lavoro predefiniti disponibili in Experience Manager {#default-workflows}

Per impostazione predefinita, tutte le risorse caricate vengono elaborate utilizzando il flusso di lavoro Aggiorna risorsa  DAM. Il flusso di lavoro viene eseguito per ciascuna risorsa caricata ed esegue attività di base per la gestione delle risorse come generazione di rappresentazioni, remix di metadati, estrazione di pagina, estrazione di contenuti multimediali e transcodifica.

Per visualizzare i vari modelli di workflow disponibili per impostazione predefinita, vedi [!UICONTROL Strumenti > Flusso di lavoro > Modelli] in [!DNL Experience Manager].

![Alcuni dei flussi di lavoro predefiniti](assets/aem-default-workflows.png)

*Figura: Alcuni dei flussi di lavoro predefiniti disponibili in[!DNL Experience Manager]*

## Applicare flussi di lavoro alle risorse {#applying-workflows-to-assets}

L’applicazione dei flussi di lavoro alle risorse digitali è la stessa utilizzata per le pagine di siti Web. Per una guida completa su come creare e utilizzare i flussi di lavoro, consulta Flussi di lavoro [](/help/sites-authoring/workflows-participating.md)iniziali.

Usate i flussi di lavoro nelle risorse digitali per attivare la risorsa o creare filigrane. Molti dei flussi di lavoro per le risorse vengono automaticamente attivati. Ad esempio, il flusso di lavoro che crea automaticamente una rappresentazione dopo la modifica di un’immagine viene automaticamente attivato.

>[!NOTE]
>
>Se un flusso di lavoro disponibile nell’interfaccia classica non è disponibile nell’interfaccia touch, come [!UICONTROL Richiesta di attivazione] e [!UICONTROL Richiesta di disattivazione], consultate [Realizzare modelli](/help/sites-developing/workflows-models.md#make-workflow-models-available-in-touchui)di flusso di lavoro.

## Applicazione di un flusso di lavoro a una risorsa AEM {#apply-a-workflow-to-an-aem-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->

Per applicare un flusso di lavoro a una risorsa, effettuate le seguenti operazioni:

1. Andate alla posizione della risorsa per la quale desiderate avviare un flusso di lavoro e fate clic sulla risorsa per aprire la pagina della risorsa.

1. Andate alla posizione della risorsa per la quale desiderate avviare un flusso di lavoro e fate clic sulla risorsa per aprire la pagina della risorsa. Selezionate **[!UICONTROL Timeline]** dal menu per visualizzare la timeline.

   ![timeline-2](assets/timeline-2.png)

1. Fate clic su **[!UICONTROL Azioni]** in basso per aprire l’elenco delle azioni disponibili per la risorsa.

1. Fare clic su **[!UICONTROL Avvia flusso di lavoro]** dall&#39;elenco.

1. In the **[!UICONTROL Start Workflow]** dialog box, select a workflow model from the list.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. (Facoltativo) Specificate un titolo per il flusso di lavoro, che può essere utilizzato per fare riferimento all’istanza del flusso di lavoro.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Fate clic su **[!UICONTROL Avvia]**, quindi fate clic su **[!UICONTROL Procedi]** nella finestra di dialogo per confermare. Ciascun passaggio del flusso di lavoro viene visualizzato nella timeline come un evento.

   ![chlimage_1-52](assets/chlimage_1-52.png)

## Applicazione di un flusso di lavoro a più risorse {#applying-a-workflow-to-multiple-assets}

1. Dalla console Risorse, individuate la posizione delle risorse per le quali desiderate avviare un flusso di lavoro e selezionate le risorse. Selezionate **[!UICONTROL Timeline]** dal menu per visualizzare la timeline.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Fate clic su **[!UICONTROL Azioni]** in basso.

1. Fate clic su **[!UICONTROL Avvia flusso di lavoro]**. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Facoltativo) Specificate un titolo per il flusso di lavoro, che può essere utilizzato per fare riferimento all’istanza del flusso di lavoro.

1. Nella finestra di dialogo, fai clic su **[!UICONTROL Avvia]**, quindi su **[!UICONTROL Conferma]**. Il flusso di lavoro viene eseguito su tutte le risorse selezionate.

## Applicazione di un flusso di lavoro a più cartelle {#applying-a-workflow-to-multiple-folders}

La procedura per applicare un flusso di lavoro a più cartelle è simile a quella per applicare un flusso di lavoro a più risorse. Selezionate le cartelle nella console Risorse ed eseguite i passaggi da 2 a 7 della procedura per [applicare un flusso di lavoro a più risorse](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Applicazione di un flusso di lavoro a una raccolta {#applying-a-workflow-to-a-collection}

Per informazioni dettagliate sull&#39;applicazione di un flusso di lavoro a una raccolta, consultate [applicare un flusso di lavoro a una raccolta](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Avvio automatico di un flusso di lavoro per elaborare le risorse in modo condizionale {#auto-execute-workflow-on-some-assets}

Gli amministratori possono configurare il flusso di lavoro per eseguire ed elaborare automaticamente le risorse in base a condizioni predefinite. Questa funzionalità è utile per utenti e addetti al marketing della linea di business, ad esempio per creare flussi di lavoro personalizzati per cartelle specifiche. Supponiamo che tutte le risorse del servizio fotografico di un&#39;agenzia possano essere filigrane o che tutte le risorse caricate da un freelancer possano essere elaborate per creare rappresentazioni specifiche.

Per un modello di workflow, gli utenti possono creare un modulo di avvio che lo esegua. Un avvio di workflow monitora le modifiche nell&#39;archivio dei contenuti ed esegue il flusso di lavoro quando vengono soddisfatte le condizioni predefinite. Gli amministratori possono fornire l&#39;accesso agli addetti al marketing per creare i flussi di lavoro e configurare il programma di avvio. Gli utenti possono modificare il flusso di lavoro predefinito [!UICONTROL DAM Update Asset] per aggiungere i passaggi aggiuntivi necessari per elaborare risorse specifiche. Il flusso di lavoro viene eseguito su tutte le risorse appena caricate. Utilizzate uno dei seguenti metodi per limitare l&#39;esecuzione dei passaggi aggiuntivi su risorse specifiche:

* Effettuate una copia del flusso di lavoro Aggiorna risorsa  DAM e modificatelo per l&#39;esecuzione in una gerarchia di cartelle specifica. Questo approccio è utile per alcune cartelle.
* I passaggi di elaborazione aggiuntivi possono essere aggiunti utilizzando un [OR diviso](/help/sites-developing/workflows-step-ref.md#or-split) in base alle condizioni applicabili a tutte le cartelle richieste.

>[!MORELIKETHIS]
>
>* [Applicazione e partecipazione ai flussi di lavoro](/help/sites-authoring/workflows.md)
>* [Creare modelli di workflow ed estendere le funzionalità dei flussi di lavoro](/help/sites-developing/workflows.md)
>* [Metodi per eseguire i flussi di lavoro](/help/sites-administering/workflows-starting.md)
>* [Best practice per i flussi di lavoro](/help/sites-developing/workflows-best-practices.md)
>* [Articolo della community sulla modifica delle risorse mediante il flusso di lavoro](https://helpx.adobe.com/experience-manager/using/modify_asset_workflow.html)

