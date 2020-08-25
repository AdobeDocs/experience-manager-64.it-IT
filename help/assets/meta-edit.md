---
title: Come modificare o aggiungere i metadati
description: Scoprite i metadati delle risorse in  AEM Assets e in vari modi in cui potete modificare i metadati delle risorse.
contentOwner: AG
translation-type: tm+mt
source-git-commit: e9f50a1ddb6a162737e6e83b976f96911b3246d6
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 8%

---


# Come modificare o aggiungere i metadati {#how-to-edit-or-add-metadata}

I metadati sono informazioni aggiuntive sulla risorsa ricercabile. Viene estratto automaticamente quando caricate un’immagine. Potete modificare i metadati esistenti o aggiungere nuove proprietà di metadati ai campi esistenti (ad esempio, quando un campo di metadati è vuoto).

Poiché le aziende necessitano di vocabolari di metadati controllati e affidabili,  AEM Assets non consente l&#39;aggiunta ad hoc di nuove proprietà di metadati. Sebbene gli autori non possano aggiungere nuovi campi di metadati per le risorse, gli sviluppatori possono farlo. Consultate [Creazione di nuove proprietà di metadati per le risorse](meta-edit.md#editing-metadata-schema).

## Modifica dei metadati per una risorsa {#editing-metadata-for-an-asset}

Per modificare i metadati:

1. Effettua una delle operazioni seguenti:

   * Nell’interfaccia utente Risorse, seleziona la risorsa e tocca o fai clic sull’icona **[!UICONTROL Visualizza proprietà]** nella barra degli strumenti.
   * Dalla miniatura della risorsa, selezionate l’azione rapida **[!UICONTROL Visualizza proprietà]** .
   * Dalla pagina della risorsa, toccate o fate clic sull’icona **[!UICONTROL Visualizza proprietà]** Icona ![info dalla barra degli strumenti](assets/do-not-localize/info_icon.png) .

   Nella pagina della risorsa vengono visualizzati tutti i metadati della risorsa. Questi metadati sono stati estratti automaticamente quando sono stati caricati (assimilati)  AEM Assets.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Apporta le modifiche necessarie ai metadati delle varie schede e, al termine, per salvarle tocca o fai clic su **[!UICONTROL Salva]** nella barra degli strumenti. Tocca o fai clic su **[!UICONTROL Chiudi]** per tornare all’interfaccia web Assets.

   >[!NOTE]
   >
   >Se un campo di testo è vuoto, non esiste alcun set di metadati. Potete immettere un valore nel campo e salvarlo per aggiungere la proprietà dei metadati.

Qualsiasi modifica ai metadati di una risorsa viene riscritta nel binario originale come parte dei dati XMP. Questo avviene tramite AEM flusso di lavoro di riscrittura metadati. Le modifiche apportate alle proprietà esistenti (ad esempio `dc:title`) vengono sovrascritte e le proprietà create di recente (comprese le proprietà personalizzate come `cq:tags`) vengono aggiunte insieme allo schema.

XMP riscrittura è supportata e abilitata per le piattaforme e i formati di file descritti in Requisiti [tecnici.](/help/sites-deploying/technical-requirements.md)

## Modifica dello schema metadati {#editing-metadata-schema}

Per informazioni dettagliate su come modificare lo schema di metadati, vedere [Modifica dei moduli](metadata-schemas.md#editing-metadata-schema-forms)dello schema di metadati.

## Registrazione di uno spazio dei nomi personalizzato all&#39;interno di AEM {#registering-a-custom-namespace-within-aem}

Potete aggiungere spazi dei nomi personalizzati all&#39;interno di AEM. Così come esistono spazi dei nomi predefiniti come cq, jcr e sling, potete avere uno spazio dei nomi per i metadati dell&#39;archivio e l&#39;elaborazione xml.

1. Vai alla pagina di amministrazione del tipo di nodo `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Tocca o fai clic su **[!UICONTROL Spazi dei nomi]** nella parte superiore della pagina. La pagina di amministrazione dello spazio dei nomi viene visualizzata in una finestra.

1. Per aggiungere uno spazio nomi, fate clic o toccate **[!UICONTROL Nuovo]** in basso.
1. Specificate uno spazio dei nomi personalizzato nella convenzione dello spazio dei nomi XML (specificate l’ID nel modulo di un URI e un prefisso associato per l’ID), quindi toccate o fate clic su **[!UICONTROL Salva]**.

## Suggerimenti e limitazioni {#best-practices-limitations}

* Gli aggiornamenti dei metadati tramite l&#39;interfaccia touch modificano le proprietà dei metadati nello `dc` spazio dei nomi. Eventuali aggiornamenti effettuati tramite l’API HTTP modificano le proprietà dei metadati nello `jcr` spazio nomi. Scoprite [come aggiornare i metadati mediante l&#39;API](/help/assets/mac-api-assets.md#update-asset-metadata)HTTP.

>[!MORELIKETHIS]
>
>* [Informazioni sui metadati e le relative esigenze in Risorse](metadata.md)