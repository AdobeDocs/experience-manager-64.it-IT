---
title: Applicazione dei predefiniti immagine Dynamic Media
seo-title: Applying Dynamic Media image presets
description: Scopri come applicare i predefiniti immagine in Dynamic Media
seo-description: Learn how to apply image presets in Dynamic Media
uuid: 8bafcbd0-6df0-4d5b-b2f7-116ddb4ec060
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5c1f60ac-3741-4002-9c5d-c128f118342b
exl-id: 07a4f315-a60e-456b-b02d-035b3f6ad9ad
feature: Image Presets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 11%

---

# Applicazione dei predefiniti immagine Dynamic Media {#applying-image-presets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I predefiniti per immagini consentono alle risorse di distribuire dinamicamente le immagini con dimensioni diverse, in formati diversi o con altre proprietà immagine generate in modo dinamico. È possibile scegliere un predefinito quando si esportano le immagini, che riformatta anche le immagini in base alle specifiche specificate dall’amministratore.

Inoltre, puoi scegliere un predefinito per immagini che sia reattivo (designato dal **[!UICONTROL RESS]** dopo averlo selezionato).

Questa sezione descrive come utilizzare i predefiniti per immagini. [Gli amministratori possono creare e configurare i predefiniti per immagini](managing-image-presets.md).

>[!NOTE]
>
>La funzione Smart imaging funziona con i predefiniti per immagini esistenti e utilizza funzionalità intelligenti all’ultimo millisecondo di distribuzione per ridurre ulteriormente le dimensioni dei file immagine in base al browser o alla velocità di connessione di rete. Vedi [Imaging avanzato](imaging-faq.md) per ulteriori informazioni.

È possibile applicare un predefinito immagine a un&#39;immagine in qualsiasi momento in cui viene visualizzata in anteprima.

**Per applicare i predefiniti immagine di Dynamic Media**:

1. Apri la risorsa e, nella barra a sinistra, tocca il menu a discesa, quindi tocca **[!UICONTROL Rendering]**.

   >[!NOTE]
   >
   >* Le rappresentazioni statiche vengono visualizzate nella parte superiore del riquadro. Le rappresentazioni dinamiche vengono visualizzate nella metà inferiore. Solo con rappresentazioni dinamiche, puoi utilizzare l’URL per visualizzare l’immagine. La **[!UICONTROL URL]** viene visualizzato solo se si seleziona un rendering dinamico. La **[!UICONTROL RESS]** viene visualizzato solo se hai selezionato un predefinito per immagini reattive.
   >
   >* Il sistema mostra numerose rappresentazioni quando selezioni **[!UICONTROL Rendering]** nella vista Dettaglio di una risorsa. Puoi aumentare il numero di predefiniti visualizzati. Vedi [Aumento del numero di predefiniti immagine da visualizzare](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display).


   ![chlimage_1-208](assets/chlimage_1-208.png)

1. Effettua una delle seguenti operazioni:

   * Seleziona un rendering dinamico per visualizzare in anteprima il predefinito per immagini.
   * Tocca **[!UICONTROL URL]**, **[!UICONTROL Incorpora]** oppure **[!UICONTROL RESS]** per visualizzare il pop-up.

   >[!NOTE]
   >
   >Se la risorsa *e* il predefinito immagine non sono ancora stati pubblicati, il pulsante **[!UICONTROL URL]** (o **[!UICONTROL URL]** e **[!UICONTROL RESS]**, se presente) non è disponibile.
   >
   >I predefiniti per immagini vengono pubblicati automaticamente su un server Dynamic Media.
