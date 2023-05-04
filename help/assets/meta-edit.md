---
title: Come modificare o aggiungere metadati
description: Informazioni sui metadati delle risorse in [!DNL Experience Manager] Risorse e vari modi per modificare i metadati delle risorse.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: f0522343-f8a9-4d89-8ce8-b3357ae3fe70
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 9%

---

# Come modificare o aggiungere metadati {#how-to-edit-or-add-metadata}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I metadati sono informazioni aggiuntive sulla risorsa ricercabile. Viene estratto automaticamente quando carichi un’immagine. È possibile modificare i metadati esistenti o aggiungere nuove proprietà di metadati ai campi esistenti (ad esempio, quando un campo di metadati è vuoto).

Perché le aziende hanno bisogno di vocabolari di metadati controllati e affidabili, [!DNL Experience Manager] Le risorse non consentono l’aggiunta ad hoc di nuove proprietà di metadati. Anche se gli autori non possono aggiungere nuovi campi di metadati per le risorse, gli sviluppatori possono farlo. Vedi [Creazione di una nuova proprietà metadati per le risorse](meta-edit.md#editing-metadata-schema).

## Modifica dei metadati di una risorsa {#editing-metadata-for-an-asset}

Per modificare i metadati:

1. Effettua una delle operazioni seguenti:

   * Dall’interfaccia utente Assets, seleziona la risorsa e tocca o fai clic sul pulsante **[!UICONTROL Visualizza proprietà]** dalla barra degli strumenti.
   * Dalla miniatura della risorsa, seleziona la **[!UICONTROL Visualizza proprietà]** azione rapida.
   * Dalla pagina della risorsa, tocca o fai clic sul pulsante **[!UICONTROL Visualizza proprietà]** icona ![icona info](assets/do-not-localize/info_icon.png) dalla barra degli strumenti.

   Nella pagina della risorsa vengono visualizzati tutti i metadati della risorsa. Questi metadati sono stati estratti automaticamente al momento del caricamento (acquisito) in [!DNL Experience Manager] Risorse.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Apporta le modifiche necessarie ai metadati delle varie schede e, al termine, per salvarle tocca o fai clic su **[!UICONTROL Salva]** nella barra degli strumenti. Tocca o fai clic su **[!UICONTROL Chiudi]** per tornare all’interfaccia web Assets.

   >[!NOTE]
   >
   >Se un campo di testo è vuoto, non sono presenti metadati esistenti. È possibile immettere un valore nel campo e salvarlo per aggiungere tale proprietà di metadati.

Qualsiasi modifica ai metadati di una risorsa viene riscritta nel binario originale come parte dei suoi dati XMP. Questo avviene tramite AEM flusso di lavoro di write-back di metadati. Modifiche apportate alle proprietà esistenti (ad esempio `dc:title`) vengono sovrascritte e le proprietà appena create (comprese proprietà personalizzate come `cq:tags`) vengono aggiunte insieme allo schema .

XMP write-back è supportato e abilitato per le piattaforme e i formati di file descritti in [Requisiti tecnici](/help/sites-deploying/technical-requirements.md)

## Modifica dello schema metadati {#editing-metadata-schema}

Per informazioni dettagliate su come modificare lo schema dei metadati, consulta [Modifica dei moduli schema metadati](metadata-schemas.md#editing-metadata-schema-forms).

## Registrazione di uno spazio dei nomi personalizzato in [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

Puoi aggiungere i tuoi namespace all’interno di AEM. Come ci sono spazi dei nomi predefiniti come cq, jcr e sling, puoi avere uno spazio dei nomi per i metadati del tuo archivio e l&#39;elaborazione xml.

1. Vai alla pagina di amministrazione del tipo di nodo `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Tocca o fai clic su **[!UICONTROL Namespace]** nella parte superiore della pagina. La pagina di amministrazione dello spazio dei nomi viene visualizzata in una finestra.

1. Per aggiungere uno spazio dei nomi, tocca o fai clic su **[!UICONTROL Nuovo]** in basso.
1. Specifica uno spazio dei nomi personalizzato nella convenzione dello spazio dei nomi XML (specifica l’id sotto forma di URI e un prefisso associato per l’id), quindi tocca o fai clic su **[!UICONTROL Salva]**.

## Suggerimenti e limitazioni {#best-practices-limitations}

* Gli aggiornamenti dei metadati tramite l&#39;interfaccia Touch modificano le proprietà dei metadati nel `dc` spazio dei nomi. Qualsiasi aggiornamento effettuato tramite l’API HTTP modifica le proprietà dei metadati nel `jcr` spazio dei nomi. Vedi [come aggiornare i metadati utilizzando l’API HTTP](/help/assets/mac-api-assets.md#update-asset-metadata).

>[!MORELIKETHIS]
>
>* [Informazioni sui metadati e sulle relative esigenze in Assets](metadata.md)

