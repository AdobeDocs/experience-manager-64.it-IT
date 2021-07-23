---
title: Elabora le risorse per eseguire processi aziendali, eseguire audit, raggiungere la conformità e mantenere un livello di integrità di base
description: Elaborazione delle risorse per convertire i formati, creare rappresentazioni, gestire le risorse, convalidare le risorse ed eseguire flussi di lavoro.
contentOwner: AG
feature: Flusso di lavoro, rappresentazioni
role: User,Admin
exl-id: 4fb3d12c-feac-45b9-8d09-3b6995591b3d
source-git-commit: fc725206728e238ab9da1fb30cee8fb407257b62
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 3%

---

# Elabora risorse digitali {#process-assets}

[!DNL Adobe Experience Manager Assets] consente di lavorare sulle risorse digitali in diversi modi per consentire un’elaborazione affidabile delle risorse. Puoi utilizzare i metodi di elaborazione disponibili o estendere i metodi per garantire il completamento completo dei processi aziendali end-to-end utilizzando, eseguendo controlli e conformità, individuazione e distribuzione delle risorse digitali e dell’integrità di base. Puoi fare tutto questo ottenendo la scala e la personalizzazione necessarie.

## Comprendere i flussi di lavoro {#understand-workflows}

Per l’elaborazione delle risorse, [!DNL Experience Manager] utilizza i flussi di lavoro. I flussi di lavoro consentono di automatizzare la logica o le attività aziendali. I passaggi granulari per eseguire attività specifiche sono forniti per impostazione predefinita e gli sviluppatori possono creare i propri passaggi personalizzati. Questi passaggi possono essere combinati in un ordine logico per creare flussi di lavoro. Ad esempio, un flusso di lavoro può applicare automaticamente una filigrana alle immagini caricate in base a criteri specifici, come metadati incorporati nell’immagine, cartelle in cui viene caricata, risoluzione dell’immagine e così via. Un altro esempio è un flusso di lavoro configurato per applicare una filigrana alle immagini in modo tale da soddisfare contemporaneamente più esigenze di gestione delle risorse, come l’aggiunta di metadati, la creazione di rappresentazioni, l’aggiunta di tag intelligenti per l’individuazione delle risorse, la pubblicazione in un archivio dati, l’impostazione delle autorizzazioni per l’accesso degli utenti e così via.

## Flussi di lavoro predefiniti disponibili in Experience Manager {#default-workflows}

Per impostazione predefinita, tutte le risorse caricate vengono elaborate utilizzando il flusso di lavoro [!UICONTROL Aggiorna risorsa DAM] . Il flusso di lavoro viene eseguito per ogni risorsa caricata ed esegue attività di base di gestione delle risorse come la generazione del rendering, il write-back dei metadati, l’estrazione della pagina, l’estrazione dei contenuti multimediali e la transcodifica.

Per visualizzare i vari modelli di flusso di lavoro disponibili per impostazione predefinita, consulta [!UICONTROL Strumenti > Flusso di lavoro > Modelli] in [!DNL Experience Manager].

![Alcuni dei flussi di lavoro predefiniti](assets/aem-default-workflows.png)

*Figura: Alcuni dei flussi di lavoro predefiniti disponibili in  [!DNL Experience Manager].*

## Applicare flussi di lavoro alle risorse {#applying-workflows-to-assets}

L’applicazione dei flussi di lavoro alle risorse digitali è la stessa applicata alle pagine di siti web. Per una guida completa su come creare e utilizzare i flussi di lavoro, consulta [avviare flussi di lavoro](/help/sites-authoring/workflows-participating.md).

Utilizza i flussi di lavoro nelle risorse digitali per attivare la risorsa o creare filigrane. Molti dei flussi di lavoro per le risorse vengono attivati automaticamente. Ad esempio, il flusso di lavoro che crea automaticamente un rendering dopo la modifica di un’immagine viene attivato automaticamente.

>[!NOTE]
>
>Se un flusso di lavoro disponibile nell&#39;interfaccia classica non è disponibile nell&#39;interfaccia touch, come [!UICONTROL Richiedi di attivare] e [!UICONTROL Richiedi di disattivare], vedi [Crea modelli di flusso di lavoro](/help/sites-developing/workflows-models.md#make-workflow-models-available-in-touchui).

## Applicare un flusso di lavoro a una risorsa AEM {#apply-a-workflow-to-an-aem-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->

Per applicare un flusso di lavoro a una risorsa, effettua le seguenti operazioni:

1. Andate alla posizione della risorsa per la quale desiderate avviare un flusso di lavoro, quindi fate clic sulla risorsa per aprire la pagina della risorsa.

1. Andate alla posizione della risorsa per la quale desiderate avviare un flusso di lavoro, quindi fate clic sulla risorsa per aprire la pagina della risorsa. Seleziona **[!UICONTROL Timeline]** dal menu per visualizzare la timeline.

   ![timeline-2](assets/timeline-2.png)

1. Fai clic su **[!UICONTROL Azioni]** in basso per aprire l’elenco delle azioni disponibili per la risorsa.

1. Fai clic su **[!UICONTROL Avvia flusso di lavoro]** dall’elenco.

1. Nella finestra di dialogo **[!UICONTROL Avvia flusso di lavoro]**, seleziona un modello di flusso di lavoro dall’elenco.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. (Facoltativo) Specifica un titolo per il flusso di lavoro, che può essere utilizzato per fare riferimento all’istanza del flusso di lavoro.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Fai clic su **[!UICONTROL Start]**, quindi fai clic su **[!UICONTROL Procedi]** nella finestra di dialogo per confermare. Ciascun passaggio del flusso di lavoro viene visualizzato nella timeline come un evento.

   ![chlimage_1-52](assets/chlimage_1-52.png)

## Applicare un flusso di lavoro a più risorse {#applying-a-workflow-to-multiple-assets}

1. Dalla console Assets, individua il percorso delle risorse per le quali vuoi avviare un flusso di lavoro e seleziona le risorse. Seleziona **[!UICONTROL Timeline]** dal menu per visualizzare la timeline.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Fai clic su **[!UICONTROL Azioni]** in basso.

1. Fai clic su **[!UICONTROL Avvia flusso di lavoro]**. Nella finestra di dialogo **[!UICONTROL Avvia flusso di lavoro]** , seleziona un modello di flusso di lavoro dall’elenco.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Facoltativo) Specifica un titolo per il flusso di lavoro, che può essere utilizzato per fare riferimento all’istanza del flusso di lavoro.

1. Nella finestra di dialogo, fai clic su **[!UICONTROL Avvia]**, quindi su **[!UICONTROL Conferma]**. Il flusso di lavoro viene eseguito su tutte le risorse selezionate.

## Applicazione di un flusso di lavoro a più cartelle {#applying-a-workflow-to-multiple-folders}

La procedura per applicare un flusso di lavoro a più cartelle è simile a quella per applicare un flusso di lavoro a più risorse. Seleziona le cartelle nella console Risorse ed esegui i passaggi 2-7 della procedura [applicare un flusso di lavoro a più risorse](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Applicazione di un flusso di lavoro a una raccolta {#applying-a-workflow-to-a-collection}

Per informazioni dettagliate sull&#39;applicazione di un flusso di lavoro a una raccolta, consulta [applicare un flusso di lavoro a una raccolta](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Avviare automaticamente un flusso di lavoro per elaborare le risorse in modo condizionale {#auto-execute-workflow-on-some-assets}

Gli amministratori possono configurare un flusso di lavoro per eseguire ed elaborare automaticamente le risorse in base a condizioni predefinite. La funzionalità è utile per utenti e addetti al marketing della linea di business, ad esempio, per creare un flusso di lavoro personalizzato su cartelle specifiche. Supponiamo che tutte le risorse del servizio fotografico di un’agenzia possano essere filigranate o che tutte le risorse caricate da un freelancer possano essere elaborate per creare rappresentazioni specifiche.

Per un modello di flusso di lavoro, gli utenti possono creare un modulo di avvio del flusso di lavoro che lo esegue. Un modulo di avvio del flusso di lavoro monitora le modifiche nell’archivio dei contenuti ed esegue il flusso di lavoro quando vengono soddisfatte le condizioni predefinite. Gli amministratori possono fornire accesso agli esperti di marketing per creare i flussi di lavoro e configurare il modulo di avvio. Gli utenti possono modificare il flusso di lavoro predefinito [!UICONTROL Aggiorna risorsa DAM] per aggiungere i passaggi aggiuntivi necessari per elaborare risorse specifiche. Il flusso di lavoro viene eseguito su tutte le risorse appena caricate. Utilizza uno dei seguenti approcci per limitare l’esecuzione dei passaggi aggiuntivi su risorse specifiche:

* Crea una copia del flusso di lavoro [!UICONTROL Aggiorna risorsa DAM] e modificalo per l&#39;esecuzione su una specifica gerarchia di cartelle. Questo approccio è utile per alcune cartelle.
* I passaggi di elaborazione aggiuntivi possono essere aggiunti utilizzando una [O divisione](/help/sites-developing/workflows-step-ref.md#or-split) come applicabile in modo condizionato a tutte le cartelle richieste.

## Best practice e limitazioni {#best-practices-limitations-tips}

* Considera le tue esigenze per tutti i tipi di rendering durante la progettazione dei flussi di lavoro. Se non prevedete la necessità di un rendering in futuro, rimuovete il relativo passaggio di creazione dal flusso di lavoro. Le rappresentazioni non possono essere eliminate in blocco in seguito. Le rappresentazioni indesiderate possono occupare molto spazio di archiviazione dopo un uso prolungato di [!DNL Experience Manager]. Per le singole risorse, puoi rimuovere manualmente i rendering dall’interfaccia utente. Per più risorse, puoi personalizzare [!DNL Experience Manager] per eliminare rappresentazioni specifiche oppure eliminare le risorse e caricarle di nuovo.
* Per impostazione predefinita, il flusso di lavoro [!UICONTROL Aggiorna risorsa DAM] include alcuni passaggi per creare miniature e rappresentazioni web. Se dal flusso di lavoro vengono rimossi alcuni rendering predefiniti, l’interfaccia utente di [!DNL Assets] non viene riprodotta correttamente.

>[!MORELIKETHIS]
>
>* [Applicare e partecipare ai flussi di lavoro](/help/sites-authoring/workflows.md)
* [Creare modelli di flusso di lavoro ed estendere le funzionalità del flusso di lavoro](/help/sites-developing/workflows.md)
* [Metodi per l’esecuzione dei flussi di lavoro](/help/sites-administering/workflows-starting.md)
* [Best practice per i flussi di lavoro](/help/sites-developing/workflows-best-practices.md)

