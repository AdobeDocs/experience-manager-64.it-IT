---
title: Aggiungi una filigrana alle risorse digitali
description: Scopri come utilizzare la funzione Watermarking per aggiungere una filigrana digitale alle risorse.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 5%

---

# Filigrana le risorse digitali {#watermarking}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] consente di aggiungere una filigrana digitale alle risorse, per consentire agli utenti di verificare l’autenticità e la proprietà del copyright delle risorse. [!DNL Experience Manager Assets] supporta il testo da utilizzare come filigrana nei file PNG e JPEG.

Risorse Adobe Experience Manager consente di aggiungere una filigrana digitale alle immagini per consentire agli utenti di verificare l’autenticità e la proprietà del copyright delle risorse. [!DNL Experience Manager] Le risorse supportano il testo da utilizzare come filigrana nei file PNG e JPEG.

Per applicare una filigrana alle risorse, aggiungi la fase di filigrana nel [!UICONTROL Risorsa di aggiornamento DAM] workflow.

1. Accedere al [!DNL Experience Manager] e vai a **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]**.
1. Dalla pagina Modelli di flusso di lavoro , seleziona il **[!UICONTROL Risorsa di aggiornamento DAM]** workflow e fai clic su **[!UICONTROL Modifica]**.

1. Dal pannello laterale, trascina la **[!UICONTROL Aggiungi filigrana]** e aggiungilo al [!UICONTROL Risorsa di aggiornamento DAM] workflow.

   ![Trascina il passaggio Aggiungi filigrana nel flusso di lavoro Aggiorna risorsa DAM](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >Posiziona il [!UICONTROL Aggiungi filigrana] prima di [!UICONTROL Miniatura processo] passo.

1. Apri **[!UICONTROL Aggiungi filigrana]** per visualizzare le relative proprietà.
1. In **[!UICONTROL Argomenti]** specificare valori validi nei vari campi, ad esempio testo, tipo di font, dimensioni, colore, posizione, orientamento e così via. Per confermare le modifiche, fai clic su **[!UICONTROL Fine]**.

   ![Fornisci gli argomenti nel passaggio Aggiungi filigrana in Assets](assets/arguments_add_watermark_aem_assets.png)

1. Con il passaggio Filigrana, salva il flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.
1. Da [!DNL Experience Manager] interfaccia utente, carica una risorsa di esempio. La filigrana viene visualizzata con le dimensioni del font, il colore e così via, nella posizione configurata nei passaggi precedenti.

Per applicare una filigrana ai documenti PDF a livello di programmazione o con informazioni dinamiche, è consigliabile utilizzare [[!DNL Experience Manager] Servizi basati su documenti](/help/forms/using/overview-aem-document-services.md) offerta.

## Suggerimenti e limitazioni {#tips-limitations}

* Sono supportate solo le filigrane basate su testo. Le immagini non vengono utilizzate come filigrane, anche se è possibile caricare le immagini durante la creazione del [!UICONTROL Aggiungi processo filigrana].
* Solo i file PNG e JPEG sono supportati per essere contrassegnati con filigrana. Gli altri formati di risorse non sono contrassegnati con filigrana.
