---
title: Applicazione di flussi di lavoro per elaborare le risorse digitali
description: Scopri come applicare flussi di lavoro a risorse, cartelle e raccolte in Risorse AEM per elaborare le risorse digitali.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Applicare flussi di lavoro alle risorse {#applying-workflows-to-assets}

L’applicazione dei flussi di lavoro alle risorse digitali è la stessa utilizzata per le pagine di siti Web. Per una guida completa su come creare e utilizzare i flussi di lavoro in AEM, consultate [Avvio dei flussi di lavoro](../sites-authoring/workflows-participating.md).

Usate i flussi di lavoro nelle risorse digitali per attivare la risorsa o creare filigrane. Molti dei flussi di lavoro per le risorse vengono automaticamente attivati. Ad esempio, il flusso di lavoro che crea automaticamente una rappresentazione dopo la modifica di un’immagine viene automaticamente attivato.

Se un flusso di lavoro disponibile nell’interfaccia classica non è disponibile nell’interfaccia touch, come Richiedi di attivare e Richiedi di disattivare, consulta [Rendere disponibili i modelli di flusso di lavoro nell’interfaccia](../sites-developing/workflows-models.md#make-workflow-models-available-in-touchui)touch.

## Applicazione di un flusso di lavoro a una risorsa AEM {#applying-a-workflow-to-an-aem-asset}

Per informazioni dettagliate sull’applicazione di un flusso di lavoro a una risorsa AEM, consultate [Avvio di un flusso di lavoro su una risorsa](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset).

## Applicazione di un flusso di lavoro a più risorse {#applying-a-workflow-to-multiple-assets}

1. Dalla console Risorse, individuate la posizione delle risorse per le quali desiderate avviare un flusso di lavoro e selezionate le risorse.
1. Fate clic sull&#39;icona GlobalNav, quindi scegliete **[!UICONTROL Timeline]** dal menu per visualizzare la timeline.

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Click the **[!UICONTROL Actions]** (arrow) icon at the bottom.

   ![chlimage_1-137](assets/chlimage_1-137.png)

1. Fate clic su **[!UICONTROL Avvia flusso di lavoro]**.
1. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. (Facoltativo) Specificate un titolo per il flusso di lavoro, che può essere utilizzato per fare riferimento all’istanza del flusso di lavoro.
1. Nella finestra di dialogo, fai clic su **[!UICONTROL Avvia]**, quindi su **[!UICONTROL Conferma]**. Il flusso di lavoro viene eseguito su tutte le risorse selezionate.

## Applicazione di un flusso di lavoro a più cartelle {#applying-a-workflow-to-multiple-folders}

La procedura per applicare un flusso di lavoro a più cartelle è simile a quella per applicare un flusso di lavoro a più risorse. Selezionate le cartelle nella console Risorse ed eseguite i passaggi da 2 a 7 della procedura [Applicazione di un flusso di lavoro a più risorse](assets-workflow.md#applying-a-workflow-to-multiple-assets).

## Applicazione di un flusso di lavoro a una raccolta {#applying-a-workflow-to-a-collection}

Per informazioni dettagliate sull&#39;applicazione di un flusso di lavoro a una raccolta, consultate [Esecuzione di un flusso di lavoro su una raccolta](managing-collections-touch-ui.md#running-a-workflow-on-a-collection).
