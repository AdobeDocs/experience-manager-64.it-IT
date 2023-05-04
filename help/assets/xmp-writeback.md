---
title: XMP di ritorno alle rappresentazioni
description: Scopri in che modo la funzione di XMP write-back propaga le modifiche ai metadati di una risorsa a tutte le rappresentazioni o a specifiche della risorsa.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 4%

---

# XMP di ritorno alle rappresentazioni {#xmp-writeback-to-renditions}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa funzionalità di XMP ripristino in [!DNL Adobe Experience Manager Assets] replica le modifiche ai metadati alle rappresentazioni della risorsa originale. Quando modifichi i metadati di una risorsa dall’interno di Assets o durante il caricamento della risorsa, le modifiche vengono inizialmente memorizzate nel nodo di metadati nella gerarchia delle risorse.

La funzione di XMP write-back consente di propagare le modifiche ai metadati a tutte le rappresentazioni o a specifiche della risorsa. La funzione riscrive solo le proprietà dei metadati che utilizzano `jcr` namespace, ovvero una proprietà denominata `dc:title` viene riscritto ma la proprietà denominata `mytitle` non lo è.

Considera uno scenario in cui modifichi la [!UICONTROL Titolo] proprietà della risorsa con titolo `Classic Leather` a `Nylon`.

![metadati](assets/metadata.png)

In questo caso, il [!DNL Experience Manager] Le modifiche vengono salvate nella sezione **[!UICONTROL Titolo]** nella `dc:title` per i metadati delle risorse memorizzati nella gerarchia delle risorse.

![metadata_memorizzati](assets/metadata_stored.png)

Tuttavia, [!DNL Experience Manager Assets] non propaga automaticamente eventuali modifiche ai metadati delle rappresentazioni di una risorsa. Vedi [come abilitare XMP write-back](#enabling-xmp-writeback).

## Abilita XMP writeback {#enabling-xmp-writeback}

Per abilitare la propagazione delle modifiche ai metadati alle rappresentazioni della risorsa durante il caricamento, modifica la **Adobe CQ DAM Rendition Maker** configurazione in Configuration Manager.

1. Apri Configuration Manager da `https://[aem_server]:[port]/system/console/configMgr`.
1. Apri **[!UICONTROL Adobe CQ DAM Rendition Maker]** configurazione.
1. Seleziona la **[!UICONTROL Propagare XMP]** e quindi salvare le modifiche.

   ![chlimage_1-346](assets/chlimage_1-346.png)

## Abilita XMP writeback per rappresentazioni specifiche {#enabling-xmp-writeback-for-specific-renditions}

Per consentire alla funzione XMP Writeback di propagare le modifiche ai metadati per selezionare le rappresentazioni, specifica queste rappresentazioni al passaggio del flusso di lavoro XMP Writeback Process del flusso di lavoro DAM Metadata WriteBack. Per impostazione predefinita, questo passaggio è configurato con il rendering originale.

Per la funzione Writeback di XMP per la propagazione dei metadati alle miniature di rendering 140.100.png e 319.319.png, esegui questi passaggi.

1. Ad Experience Manager, passa a **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Da [!UICONTROL Modelli] aprire **[!UICONTROL Writeback di metadati DAM]** modello di flusso di lavoro.
1. Nella pagina delle proprietà **[!UICONTROL Writeback di metadati DAM]**, apri il passaggio **[!UICONTROL Processo write-back XMPs]**.
1. Nella finestra di dialogo **[!UICONTROL Proprietà passaggio]**, tocca/fai clic sulla scheda **[!UICONTROL Processo]**.
1. In **[!UICONTROL Argomenti]** aggiungi `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. Tocca o fai clic su **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Per rigenerare le rappresentazioni piramidali di TIFF per le immagini Dynamic Media con i nuovi attributi, aggiungi la **[!UICONTROL Risorse immagine di processo Dynamic Media]** al flusso di lavoro Writeback di metadati DAM.
Le rappresentazioni PTIFF vengono create e memorizzate solo localmente in modalità ibrida di Dynamic Media. Salva il flusso di lavoro.

Le modifiche ai metadati vengono propagate alle rappresentazioni `thumbnail.140.100.png` e `thumbnail.319.319.png` del bene e non degli altri.

>[!NOTE]
>
>Per XMP problemi di writeback in Linux a 64 bit, vedi [Come abilitare XMP write-back su RedHat Linux a 64 bit](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Per ulteriori informazioni sulle piattaforme supportate, consulta [Prerequisiti per la scrittura di metadati XMP](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtrare i metadati XMP {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] supporta sia il filtro elenco Bloccati che elenco Consentiti di proprietà/nodi per XMP metadati letti dai binari delle risorse e memorizzati in JCR quando le risorse vengono acquisite.

Il filtro mediante un elenco Bloccati consente di importare tutte le proprietà dei metadati XMP eccetto le proprietà specificate per l’esclusione. Tuttavia, per i tipi di risorse come i file INDD con grandi quantità di metadati XMP (ad esempio 1000 nodi con 10.000 proprietà), i nomi dei nodi da filtrare non sono sempre noti in anticipo. Se il filtraggio mediante un elenco Bloccati consente di importare un numero elevato di risorse con numerosi metadati XMP, la [!DNL Experience Manager] istanza o cluster possono incontrare problemi di stabilità, ad esempio code di osservazione intasate.

Il filtro dei metadati XMP tramite elenco Consentiti risolve questo problema consentendo di definire le proprietà XMP da importare. In questo modo, qualsiasi altra proprietà XMP o sconosciuta viene ignorata. Per la compatibilità con le versioni precedenti, puoi aggiungere alcune di queste proprietà al filtro che utilizza un elenco Bloccati.

>[!NOTE]
>
>Il filtraggio funziona solo per le proprietà derivate XMP origini nei binari delle risorse. Per le proprietà derivate da origini non XMP, come i formati EXIF e IPTC, il filtro non funziona. Ad esempio, la data di creazione della risorsa viene memorizzata nella proprietà denominata `CreateDate` in EXIF TIFF. [!DNL Experience Manager] memorizza questo valore nel campo metadati denominato `exif:DateTimeOriginal`. Poiché l&#39;origine è un&#39;origine non XMP, il filtro non funziona su questa proprietà.

1. Apri Configuration Manager da `https://[aem_server]:[port]/system/console/configMgr`.
1. Apri **[!UICONTROL Adobe CQ DAM XmpFilter]** configurazione.
1. Per applicare un filtro tramite un elenco Consentiti, seleziona **[!UICONTROL Applica Inserì nell&#39;elenco Consentiti alle proprietà XMP]** e specifica le proprietà da importare nel **[!UICONTROL Nomi XML consentiti per il filtro XMP]** scatola.

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. Per filtrare le proprietà bloccate XMP dopo aver applicato il filtro tramite elenco Consentiti, specifica quelle nel **[!UICONTROL Nomi XML bloccati per XMP filtro]** scatola. Salva le modifiche.

   >[!NOTE]
   >
   >La **[!UICONTROL Applica Inserii nell&#39;elenco Bloccati alle proprietà XMP]** è selezionata per impostazione predefinita. In altre parole, il filtro utilizzando un elenco Bloccati è abilitato per impostazione predefinita. Per disattivare questo filtro, deseleziona la **[!UICONTROL Applica Inserii nell&#39;elenco Bloccati alle proprietà XMP]** opzione .
