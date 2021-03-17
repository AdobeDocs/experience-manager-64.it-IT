---
title: Write-back XMP per le rappresentazioni
description: Scopri in che modo la funzione di XMP write-back propaga le modifiche ai metadati di una risorsa a tutte le rappresentazioni o a specifiche della risorsa.
contentOwner: AG
translation-type: tm+mt
source-git-commit: debf372e6a0b8f00bbfce16325908a5806c062d5
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 4%

---


# Write-back XMP per le rappresentazioni {#xmp-writeback-to-renditions}

Questa funzione di XMP write-back in [!DNL Adobe Experience Manager Assets] replica le modifiche ai metadati alle rappresentazioni della risorsa originale. Quando modifichi i metadati di una risorsa dall’interno di Assets o durante il caricamento della risorsa, le modifiche vengono inizialmente memorizzate nel nodo di metadati nella gerarchia delle risorse.

La funzione di XMP write-back consente di propagare le modifiche ai metadati a tutte le rappresentazioni o a specifiche della risorsa. La funzione riscrive solo le proprietà dei metadati che utilizzano lo spazio dei nomi `jcr`, ovvero viene riscritta una proprietà denominata `dc:title` ma non una proprietà denominata `mytitle`.

Considera uno scenario in cui modifichi la proprietà [!UICONTROL Title] della risorsa denominata `Classic Leather` in `Nylon`.

![Metadati](assets/metadata.png)

In questo caso, AEM Assets salva le modifiche alla proprietà **[!UICONTROL Title]** nel parametro `dc:title` per i metadati delle risorse memorizzati nella gerarchia delle risorse.

![metadata_memorizzati](assets/metadata_stored.png)

Tuttavia, [!DNL Experience Manager Assets] non propaga automaticamente eventuali modifiche ai metadati delle rappresentazioni di una risorsa. Vedere [come abilitare XMP writeback](#enabling-xmp-writeback).

## Abilita XMP writeback {#enabling-xmp-writeback}

Per abilitare la propagazione delle modifiche ai metadati alle rappresentazioni della risorsa durante il caricamento, modifica la configurazione **Adobe CQ DAM Rendition Maker** in Configuration Manager.

1. Apri Configuration Manager da `https://[aem_server]:[port]/system/console/configMgr`.
1. Apri la configurazione **[!UICONTROL Adobe CQ DAM Rendition Maker]** .
1. Selezionare l&#39;opzione **[!UICONTROL Propaga XMP]**, quindi salvare le modifiche.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Abilita XMP writeback per rappresentazioni specifiche {#enabling-xmp-writeback-for-specific-renditions}

Per consentire alla funzione XMP Writeback di propagare le modifiche ai metadati per selezionare le rappresentazioni, specifica queste rappresentazioni al passaggio del flusso di lavoro XMP Writeback Process del flusso di lavoro DAM Metadata WriteBack. Per impostazione predefinita, questo passaggio è configurato con il rendering originale.

Per la funzione Writeback di XMP per la propagazione dei metadati alle miniature di rendering 140.100.png e 319.319.png, esegui questi passaggi.

1. Ad Experience Manager, passa a **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Dalla pagina [!UICONTROL Modelli] , apri il modello di flusso di lavoro **[!UICONTROL Writeback di metadati DAM]** .
1. Nella pagina delle proprietà **[!UICONTROL Writeback di metadati DAM]**, apri il passaggio **[!UICONTROL Processo write-back XMPs]**.
1. Nella finestra di dialogo **[!UICONTROL Proprietà passaggio]**, tocca/fai clic sulla scheda **[!UICONTROL Processo]**.
1. Nella casella **[!UICONTROL Argomenti]**, aggiungi `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Tocca o fai clic su **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Per rigenerare le rappresentazioni TIFF piramidali per le immagini Dynamic Media con i nuovi attributi, aggiungi il passaggio **[!UICONTROL Dynamic Media Process Image Assets]** al flusso di lavoro Writeback di metadati DAM.
Le rappresentazioni PTIFF vengono create e memorizzate solo localmente in modalità ibrida di Dynamic Media. Salva il flusso di lavoro.

Le modifiche ai metadati vengono propagate alle rappresentazioni `thumbnail.140.100.png` e `thumbnail.319.319.png` della risorsa e non alle altre.

>[!NOTE]
>
>Per XMP problemi di write-back in Linux a 64 bit, vedere [Come abilitare XMP write-back su RedHat Linux a 64 bit](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Per ulteriori informazioni sulle piattaforme supportate, consulta [XMP prerequisiti per la riscrittura dei metadati](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtra metadati XMP {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] supporta sia il filtro elenco Bloccati che elenco Consentiti di proprietà/nodi per XMP metadati letti dai binari delle risorse e memorizzati in JCR quando le risorse vengono acquisite.

Il filtro mediante un elenco Bloccati consente di importare tutte le proprietà dei metadati XMP eccetto le proprietà specificate per l’esclusione. Tuttavia, per i tipi di risorse come i file INDD con grandi quantità di metadati XMP (ad esempio 1000 nodi con 10.000 proprietà), i nomi dei nodi da filtrare non sono sempre noti in anticipo. Se il filtraggio utilizzando un elenco Bloccati consente l’importazione di un gran numero di risorse con numerosi metadati XMP, l’istanza o il cluster AEM può incontrare problemi di stabilità, ad esempio code di osservazione intasate.

Il filtro dei metadati XMP tramite elenco Consentiti risolve questo problema consentendo di definire le proprietà XMP da importare. In questo modo, qualsiasi altra proprietà XMP o sconosciuta viene ignorata. Per la compatibilità con le versioni precedenti, puoi aggiungere alcune di queste proprietà al filtro che utilizza un elenco Bloccati.

>[!NOTE]
>
>Il filtraggio funziona solo per le proprietà derivate XMP origini nei binari delle risorse. Per le proprietà derivate da origini non XMP, come i formati EXIF e IPTC, il filtro non funziona. Ad esempio, la data di creazione delle risorse è memorizzata nella proprietà `CreateDate` in EXIF TIFF. AEM questo valore nel campo metadati denominato `exif:DateTimeOriginal`. Poiché l&#39;origine è un&#39;origine non XMP, il filtro non funziona su questa proprietà.

1. Apri Configuration Manager da `https://[aem_server]:[port]/system/console/configMgr`.
1. Apri la configurazione **[!UICONTROL Adobe CQ DAM XmpFilter]** .
1. Per applicare un filtro tramite un elenco Consentiti, selezionare **[!UICONTROL Applica Inserì nell&#39;elenco Consentiti a proprietà XMP]** e specificare le proprietà da importare nella casella **[!UICONTROL Nomi XML consentiti per XMP filtro]**.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Per filtrare le proprietà bloccate XMP dopo aver applicato il filtro tramite elenco Consentiti, specificale nella casella **[!UICONTROL Nomi XML bloccati per XMP filtro]**. Salva le modifiche.

   >[!NOTE]
   >
   >L&#39;opzione **[!UICONTROL Applica Inserii nell&#39;elenco Bloccati a proprietà XMP]** è selezionata per impostazione predefinita. In altre parole, il filtro utilizzando un elenco Bloccati è abilitato per impostazione predefinita. Per disattivare questo filtro, deselezionare l&#39;opzione **[!UICONTROL Applica Inserii nell&#39;elenco Bloccati a proprietà XMP]** .
