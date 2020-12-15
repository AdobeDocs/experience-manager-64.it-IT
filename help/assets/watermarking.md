---
title: Filigrana le immagini
description: Utilizzate la funzione di filigrana per aggiungere una filigrana digitale alle immagini PNG e JPEG.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 04de28347ddf0082d2e224aa3853297cad3aacd8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 4%

---


# Filigrana delle risorse {#watermarking}

Risorse Adobe Experience Manager (AEM) consente di aggiungere una filigrana digitale alle immagini per consentire agli utenti di verificare l’autenticità e la proprietà delle risorse sotto copyright.  AEM Assets supporta il testo da usare come filigrana nei file PNG e JPEG.

Per applicare una filigrana alle risorse, aggiungi il passaggio [!UICONTROL Filigrana] nel flusso di lavoro [!UICONTROL Aggiorna risorsa DAM].

1. Toccate il logo AEM e andate a **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]**.
1. Dalla pagina Modelli flusso di lavoro, selezionate il flusso di lavoro **[!UICONTROL Aggiorna risorsa DAM]** e fate clic su **[!UICONTROL Modifica]**.

1. Dal pannello laterale, trascinate il passaggio **[!UICONTROL Aggiungi filigrana]** e aggiungetelo al flusso di lavoro [!UICONTROL Aggiorna risorsa DAM].

   ![Scurisci il passaggio della filigrana nel flusso di lavoro della risorsa di aggiornamento DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Posizionare il passaggio [!UICONTROL Aggiungi filigrana] in un punto qualsiasi prima del passaggio [!UICONTROL Miniatura processo].

1. Aprire il passaggio **[!UICONTROL Aggiungi filigrana]** per visualizzarne le proprietà.
1. Nella scheda **[!UICONTROL Argomenti]**, specificare valori validi nei vari campi, quali testo, tipo di font, dimensione, colore, posizione, orientamento e così via. Per confermare le modifiche, toccate o fate clic sull’icona Fine.

   ![Fornire gli argomenti nel passaggio Aggiungi filigrana in Risorse](assets/arguments_add_watermark_aem_assets.png)

1. Con il passaggio Filigrana, salva il flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.
1. Dall’interfaccia utente AEM, caricate una risorsa di esempio. La filigrana viene visualizzata con la dimensione del font, il colore e così via, nella posizione configurata nei passaggi precedenti.

Per applicare una filigrana ai documenti PDF a livello di programmazione o con informazioni dinamiche, è consigliabile utilizzare l&#39;offerta [AEM Document Services](/help/forms/using/overview-aem-document-services.md).
