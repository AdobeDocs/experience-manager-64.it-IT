---
title: supporto Camera Raw
description: Scopri come abilitare il supporto Camera Raw in Adobe Experience Manager Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dea673f8999656a5c5364f74f45eba41dd17b947
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 2%

---


# Utilizzare Camera Raw per elaborare le immagini {#camera-raw-support}

Potete abilitare il supporto Camera Raw per elaborare formati di file non elaborati, come CR2, NEF e RAF, ed eseguire il rendering delle immagini in formato JPEG. La funzionalità è supportata in Adobe Experience Manager Assets mediante il [pacchetto Camera Raw](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) disponibile da Distribuzione software.

>[!NOTE]
>
>La funzionalità supporta solo le rappresentazioni JPEG. È supportato su Windows a 64 bit, Mac OS e RHEL 7.x.

Per abilitare il supporto Camera Raw in Adobe Experience Manager Assets, procedi come segue:

1. Scaricate il [pacchetto Camera Raw](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) dalla distribuzione del software.

1. Accesso `https://[aem_server]:[port]/workflow`. Aprite il flusso di lavoro **[!UICONTROL DAM Update Asset]**.

1. Aprire il passaggio **[!UICONTROL Miniature processo]**.

1. Fornire la seguente configurazione nella scheda **[!UICONTROL Miniature]**:

   * **[!UICONTROL Miniature]**:  `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL Ignora tipi MIME]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![calce](assets/chlimage_1-334.png)

1. Nella scheda **[!UICONTROL Immagine abilitata per il Web]**, nel campo **[!UICONTROL Skip List]** specificare `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![calce](assets/chlimage_1-335.png)

1. Dal pannello laterale, aggiungete il passaggio **[!UICONTROL Camera Raw/DNG Handler]** sotto il passaggio **[!UICONTROL Creazione miniature]**.

1. Nel passaggio **[!UICONTROL Camera Raw/DNG Handler]**, aggiungere la seguente configurazione nella scheda **[!UICONTROL Argomenti]**:

   * **[!UICONTROL Tipi]** mime:  `image/dng` e  `image/x-raw-(.*)`
   * **[!UICONTROL Comando]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. Fai clic su **[!UICONTROL Salva]**.

>[!NOTE]
>
>Assicurarsi che la configurazione di cui sopra sia uguale alla configurazione **[!UICONTROL Sample DAM Update Asset With Camera Raw and DNG Handling Step]**.

È ora possibile importare file Camera Raw  AEM Assets. Dopo aver installato il pacchetto Camera Raw e configurato il flusso di lavoro, nell&#39;elenco dei riquadri laterali viene visualizzata l&#39;opzione **[!UICONTROL Regolazione immagine]**.

![chlimage_1-337](assets/chlimage_1-337.png)

*Figura: Opzioni nel riquadro laterale*

![chlimage_1-338](assets/chlimage_1-338.png)

*Figura: Opzione per apportare modifiche leggere alle immagini*

Dopo aver salvato le modifiche in un&#39;immagine Camera Raw, viene generata una nuova rappresentazione `AdjustedPreview.jpg` per l&#39;immagine. Per altri tipi di immagini, tranne Camera Raw, le modifiche vengono riportate in tutte le rappresentazioni.

## Best practice, problemi noti e limitazioni {#best-practices}

La funzionalità presenta le seguenti limitazioni:

* La funzionalità supporta solo le rappresentazioni JPEG. È supportato su Windows a 64 bit, Mac OS e RHEL 7.x.
* Il writeback dei metadati non è supportato per i formati RAW e DNG.
* La libreria Camera Raw presenta delle limitazioni rispetto ai pixel totali che può elaborare alla volta. Al momento, può elaborare un massimo di 65000 pixel sul lato lungo di un file o 512 MP, indipendentemente dai criteri rilevati per primi.
