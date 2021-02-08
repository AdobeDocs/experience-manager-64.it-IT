---
title: Aggiungere una filigrana alle risorse digitali
description: Scoprite come usare la funzione Filigrana per aggiungere una filigrana digitale alle risorse.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dfd6d022ef7d21ab6fc4ed17483890eb5766af18
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Filigrana le risorse digitali {#watermarking}

[!DNL Adobe Experience Manager Assets] consente di aggiungere una filigrana digitale alle risorse per consentire agli utenti di verificare l’autenticità e la proprietà del copyright delle risorse. [!DNL Experience Manager Assets] supporta il testo da usare come filigrana nei file PNG e JPEG.

Risorse Adobe Experience Manager (AEM) consente di aggiungere una filigrana digitale alle immagini per consentire agli utenti di verificare l’autenticità e la proprietà delle risorse sotto copyright.  AEM Assets supporta il testo da usare come filigrana nei file PNG e JPEG.

Per applicare una filigrana alle risorse, aggiungi la filigrana nel flusso di lavoro [!UICONTROL Aggiorna risorsa DAM].

1. Accedete all&#39;interfaccia utente [!DNL Experience Manager] e andate a **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]**.
1. Dalla pagina Modelli flusso di lavoro, selezionate il flusso di lavoro **[!UICONTROL Aggiorna risorsa DAM]** e fate clic su **[!UICONTROL Modifica]**.

1. Dal pannello laterale, trascinate il passaggio **[!UICONTROL Aggiungi filigrana]** e aggiungetelo al flusso di lavoro [!UICONTROL Aggiorna risorsa DAM].

   ![Trascina il passaggio Aggiungi filigrana nel flusso di lavoro della risorsa di aggiornamento DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Posizionare il passaggio [!UICONTROL Aggiungi filigrana] in un punto qualsiasi prima del passaggio [!UICONTROL Miniatura processo].

1. Aprire il passaggio **[!UICONTROL Aggiungi filigrana]** per visualizzarne le proprietà.
1. Nella scheda **[!UICONTROL Argomenti]**, specificare valori validi nei vari campi, quali testo, tipo di font, dimensione, colore, posizione, orientamento e così via. Per confermare le modifiche, fare clic su **[!UICONTROL Fine]**.

   ![Fornire gli argomenti nel passaggio Aggiungi filigrana in Risorse](assets/arguments_add_watermark_aem_assets.png)

1. Con il passaggio Filigrana, salva il flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.
1. Dall’interfaccia utente AEM, caricate una risorsa di esempio. La filigrana viene visualizzata con la dimensione del font, il colore e così via, nella posizione configurata nei passaggi precedenti.

Per applicare una filigrana ai documenti PDF a livello di programmazione o con informazioni dinamiche, è consigliabile utilizzare l&#39;offerta [AEM Document Services](/help/forms/using/overview-aem-document-services.md).

## Suggerimenti e limitazioni {#tips-limitations}

* Sono supportate solo le filigrane basate su testo. Le immagini non vengono utilizzate come filigrane, anche se potete caricare le immagini durante la creazione del processo [!UICONTROL Aggiungi filigrana].
* Solo i file PNG e JPEG sono supportati per le filigrane. Gli altri formati di risorse non sono con filigrana.
