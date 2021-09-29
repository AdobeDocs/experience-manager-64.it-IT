---
title: Supporto Camera Raw
description: Scopri come abilitare il supporto Camera Raw in Adobe Experience Manager Assets.
contentOwner: AG
feature: Developer Tools
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 2%

---

# Usa Camera Raw per elaborare le immagini {#camera-raw-support}

È possibile abilitare il supporto Camera Raw per elaborare formati di file non elaborati, come CR2, NEF e RAF, ed eseguire il rendering delle immagini in formato JPEG. La funzionalità è supportata in Adobe Experience Manager Assets utilizzando il [pacchetto Camera Raw](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) disponibile da Distribuzione software.

>[!NOTE]
>
>La funzionalità supporta solo le rappresentazioni JPEG. È supportato su Windows a 64 bit, Mac OS e RHEL 7.x.

Per abilitare il supporto Camera Raw in Adobe Experience Manager Assets, effettua le seguenti operazioni:

1. Scarica il [pacchetto Camera Raw](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) dalla Distribuzione di software.

1. Accesso `https://[aem_server]:[port]/workflow`. Apri il flusso di lavoro **[!UICONTROL Aggiorna risorsa DAM]** .

1. Apri il passaggio **[!UICONTROL Elabora miniature]** .

1. Fornisci la seguente configurazione nella scheda **[!UICONTROL Miniature]** :

   * **[!UICONTROL Miniature]**:  `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL Ignora tipi MIME]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![calcagno](assets/chlimage_1-334.png)

1. Nella scheda **[!UICONTROL Immagine abilitata per il Web]**, nel campo **[!UICONTROL Ignora elenco]** , specifica `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![calcagno](assets/chlimage_1-335.png)

1. Dal pannello laterale, aggiungi il passaggio **[!UICONTROL Camera Raw/DNG Handler]** sotto il passaggio **[!UICONTROL Creazione miniature]** .

1. Nel passaggio **[!UICONTROL Camera Raw/DNG Handler]** , aggiungi la seguente configurazione nella scheda **[!UICONTROL Argomenti]** :

   * **[!UICONTROL Tipi]** MIME:  `image/dng` e  `image/x-raw-(.*)`
   * **[!UICONTROL Comando]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. Fai clic su **[!UICONTROL Salva]**.

>[!NOTE]
>
>Assicurati che la configurazione di cui sopra sia la stessa della configurazione **[!UICONTROL Sample DAM Update Asset With Camera Raw and DNG Handling Step]** .

È ora possibile importare i file non elaborati della fotocamera in [!DNL Experience Manager] risorse. Dopo aver installato il pacchetto Camera Raw e configurato il flusso di lavoro richiesto, l&#39;opzione **[!UICONTROL Regolazione immagine]** viene visualizzata nell&#39;elenco dei riquadri laterali.

![chlimage_1-337](assets/chlimage_1-337.png)

*Figura: Opzioni nel riquadro laterale*

![chlimage_1-338](assets/chlimage_1-338.png)

*Figura: Utilizza l’opzione per apportare modifiche leggere alle immagini*

Dopo aver salvato le modifiche a un&#39;immagine Camera Raw, viene generato un nuovo rendering `AdjustedPreview.jpg` per l&#39;immagine. Per altri tipi di immagini, tranne Camera Raw, le modifiche vengono applicate a tutte le rappresentazioni.

## Best practice, problemi noti e limitazioni {#best-practices}

La funzionalità presenta le seguenti limitazioni:

* La funzionalità supporta solo le rappresentazioni JPEG. È supportato su Windows a 64 bit, Mac OS e RHEL 7.x.
* Il write-back di metadati non è supportato per i formati RAW e DNG.
* La libreria Camera Raw presenta limitazioni rispetto ai pixel totali che può elaborare alla volta. Attualmente, può elaborare un massimo di 65000 pixel sul lato lungo di un file o 512 MP qualunque sia il criterio che viene rilevato per primo.
