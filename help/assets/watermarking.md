---
title: Aggiungi una filigrana alle risorse digitali
description: Scopri come utilizzare la funzione Watermarking per aggiungere una filigrana digitale alle risorse.
contentOwner: AG
feature: Gestione risorse
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 3%

---

# Filigrana le risorse digitali {#watermarking}

[!DNL Adobe Experience Manager Assets] consente di aggiungere una filigrana digitale alle risorse, per consentire agli utenti di verificare l’autenticità e la proprietà del copyright delle risorse. [!DNL Experience Manager Assets] supporta il testo da utilizzare come filigrana nei file PNG e JPEG.

Risorse Adobe Experience Manager (AEM) consente di aggiungere una filigrana digitale alle immagini per consentire agli utenti di verificare l’autenticità e la proprietà del copyright delle risorse. AEM Assets supporta il testo da utilizzare come filigrana nei file PNG e JPEG.

Per applicare una filigrana alle risorse, aggiungi il passaggio di filigrana nel flusso di lavoro [!UICONTROL Aggiorna risorsa DAM] .

1. Accedi all&#39;interfaccia utente [!DNL Experience Manager] e vai a **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]**.
1. Dalla pagina Modelli di flusso di lavoro , seleziona il flusso di lavoro **[!UICONTROL Aggiorna risorsa DAM]** e fai clic su **[!UICONTROL Modifica]**.

1. Dal pannello laterale, trascina il passaggio **[!UICONTROL Aggiungi filigrana]** e aggiungilo al flusso di lavoro [!UICONTROL Aggiorna risorsa DAM] .

   ![Trascina il passaggio Aggiungi filigrana nel flusso di lavoro Aggiorna risorsa DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Posiziona il passaggio [!UICONTROL Aggiungi filigrana] in un punto qualsiasi prima del passaggio [!UICONTROL Elabora miniatura] .

1. Apri il passaggio **[!UICONTROL Aggiungi filigrana]** per visualizzarne le proprietà.
1. Nella scheda **[!UICONTROL Argomenti]** , specifica valori validi nei vari campi, compresi testo, tipo di font, dimensioni, colore, posizione, orientamento e così via. Per confermare le modifiche, fai clic su **[!UICONTROL Fine]**.

   ![Fornisci gli argomenti nel passaggio Aggiungi filigrana in Assets](assets/arguments_add_watermark_aem_assets.png)

1. Con il passaggio Filigrana, salva il flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.
1. Dall’interfaccia utente AEM, carica una risorsa di esempio. La filigrana viene visualizzata con le dimensioni del font, il colore e così via, nella posizione configurata nei passaggi precedenti.

Per applicare una filigrana ai documenti PDF a livello di programmazione o con informazioni dinamiche, è consigliabile utilizzare l&#39;offerta [AEM Document Services](/help/forms/using/overview-aem-document-services.md).

## Suggerimenti e limitazioni {#tips-limitations}

* Sono supportate solo le filigrane basate su testo. Le immagini non vengono utilizzate come filigrane, anche se è possibile caricare le immagini durante la creazione di [!UICONTROL Aggiungi processo filigrana].
* Solo i file PNG e JPEG sono supportati per essere contrassegnati con filigrana. Gli altri formati di risorse non sono contrassegnati con filigrana.
