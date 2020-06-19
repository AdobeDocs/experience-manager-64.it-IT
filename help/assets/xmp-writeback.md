---
title: Write-back XMP per le rappresentazioni
description: Scoprite in che modo la funzione di writeback XMP propaga le modifiche dei metadati per una risorsa a tutte le rappresentazioni o a specifiche della risorsa.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 4%

---


# Write-back XMP per le rappresentazioni {#xmp-writeback-to-renditions}

Questa funzione di Write-back XMP in Risorse  Adobe Experience Manager (AEM) replica le modifiche apportate ai metadati delle risorse alle rappresentazioni della risorsa.

Quando modificate i metadati di una risorsa dall’interno dei AEM Assets o durante il caricamento della risorsa, le modifiche vengono inizialmente memorizzate all’interno del nodo della risorsa in Crx-De.

La funzione Write-back XMP propaga le modifiche ai metadati a tutte le rappresentazioni o a specifiche della risorsa.

Considerate uno scenario in cui modificate la proprietà [!UICONTROL Titolo] della risorsa `Classic Leather` con titolo `Nylon`.

![metadati](assets/metadata.png)

In questo caso, i AEM Assets salvano le modifiche alla proprietà **[!UICONTROL Titolo]** nel `dc:title` parametro per i metadati della risorsa memorizzati nella gerarchia delle risorse.

![metadata_stored](assets/metadata_stored.png)

Tuttavia, i AEM Assets non propagano automaticamente le modifiche apportate ai metadati alle rappresentazioni di una risorsa.

La funzione Write-back XMP consente di estendere le modifiche ai metadati a tutte le rappresentazioni o a specifiche della risorsa. Tuttavia, le modifiche non vengono memorizzate sotto il nodo di metadati nella gerarchia delle risorse. Questa funzione incorpora invece le modifiche apportate ai file binari per le rappresentazioni.

## Abilita writeback XMP {#enabling-xmp-writeback}

Per abilitare la propagazione delle modifiche ai metadati alle rappresentazioni della risorsa al momento del caricamento, modificate la configurazione di **Adobe CQ DAM Rendition Maker** in Configuration Manager.

1. Apri Configuration Manager da `https://[aem_server]:[port]/system/console/configMgr`.
1. Aprite la configurazione di **[!UICONTROL Adobe CQ DAM Rendition Maker]** .
1. Selezionate l&#39;opzione **[!UICONTROL Propaga XMP]** , quindi salvate le modifiche.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Abilita Write-back XMP per rappresentazioni specifiche {#enabling-xmp-writeback-for-specific-renditions}

Per consentire alla funzione di WriteBack XMP di estendere le modifiche ai metadati per selezionare le rappresentazioni, specificate queste rappresentazioni nel passaggio del flusso di lavoro di WriteBack dei metadati XMP del flusso di lavoro di WriteBack dei metadati DAM. Per impostazione predefinita, questo passaggio è configurato con la rappresentazione originale.

Per estendere i metadati alle miniature delle rappresentazioni 140.100.png e 319.319.png, effettuate le seguenti operazioni.

1. In  Experience Manager, accedi a **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Dalla pagina [!UICONTROL Modelli] , aprite il modello di flusso di lavoro **[!UICONTROL DAM Metadata Writeback]** .
1. Nella pagina delle proprietà **[!UICONTROL Writeback di metadati DAM]**, apri il passaggio **[!UICONTROL Processo write-back XMPs]**.
1. Nella finestra di dialogo **[!UICONTROL Proprietà passaggio]**, tocca/fai clic sulla scheda **[!UICONTROL Processo]**.
1. Nella casella **[!UICONTROL Argomenti]** , aggiungere `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Tap/click **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. To regenerate the pyramid TIFF renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata Writeback workflow.
Le rappresentazioni PTIFF vengono create e memorizzate localmente solo in modalità ibrida Dynamic Media. Salvare il flusso di lavoro.

Le modifiche ai metadati vengono propagate alle rappresentazioni `thumbnail.140.100.png` e `thumbnail.319.319.png` alla risorsa, non agli altri.

>[!NOTE]
>
>Per i problemi di reinserimento XMP in Linux a 64 bit, consultate [Come abilitare la riscrittura XMP su RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)a 64 bit.
>
>Per ulteriori informazioni sulle piattaforme supportate, consultate [Metadati XMP prerequisiti](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back)per la riscrittura.

## Filtrare i metadati XMP {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] supporta sia l’elenco bloccato che il filtro elenco consentito di proprietà/nodi per i metadati XMP che vengono letti dai file binari delle risorse e memorizzati in JCR quando vengono assimilate le risorse.

Il filtraggio mediante un elenco bloccato consente di importare tutte le proprietà dei metadati XMP, ad eccezione delle proprietà specificate per l&#39;esclusione. Tuttavia, per i tipi di risorse come i file INDD con enormi quantità di metadati XMP (ad esempio, 1000 nodi con 10.000 proprietà), i nomi dei nodi da filtrare non sono sempre noti in anticipo. Se l’utilizzo di un elenco bloccato consente l’importazione di un gran numero di risorse con numerosi metadati XMP, l’istanza o il cluster di AEM potrebbe incontrare problemi di stabilità, ad esempio code di osservazione bloccate.

Il filtro dei metadati XMP tramite l&#39;elenco consentito risolve il problema consentendo di definire le proprietà XMP da importare. In questo modo, qualsiasi altra proprietà XMP o sconosciuta viene ignorata. Per compatibilità con le versioni precedenti, potete aggiungere alcune di queste proprietà al filtro che utilizza un elenco bloccato.

>[!NOTE]
>
>Il filtro funziona solo per le proprietà derivate da origini XMP nei file binari delle risorse. Per le proprietà derivate da origini non XMP, come i formati EXIF e IPTC, il filtro non funziona. Ad esempio, la data di creazione delle risorse è memorizzata nella proprietà denominata `CreateDate` in EXIF TIFF. AEM memorizza questo valore nel campo di metadati denominato `exif:DateTimeOriginal`. Poiché l&#39;origine è un&#39;origine non XMP, il filtraggio non funziona su questa proprietà.

1. Apri Configuration Manager da `https://[aem_server]:[port]/system/console/configMgr`.
1. Aprite la configurazione **[!UICONTROL Adobe CQ DAM XmpFilter]** .
1. To apply filtering via an allowed list, select **[!UICONTROL Apply Allowlist to XMP Properties]**, and specify the properties to be imported in the **[!UICONTROL Allowed XML Names for XMP filtering]** box.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Per filtrare le proprietà XMP bloccate dopo l&#39;applicazione del filtro tramite l&#39;elenco consentito, specificate quelle nella casella Nomi XML **[!UICONTROL bloccati per il filtro]** XMP. Salva le modifiche.

   >[!NOTE]
   >
   >L&#39;opzione **[!UICONTROL Applica blocco alle proprietà]** XMP è selezionata per impostazione predefinita. In altre parole, il filtraggio utilizzando un elenco bloccato è attivato per impostazione predefinita. Per disattivare questo filtro, deselezionate l&#39;opzione **[!UICONTROL Applica blocco alle proprietà]** XMP.
