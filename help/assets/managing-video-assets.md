---
title: Gestire le risorse video
description: Scoprite come caricare, visualizzare in anteprima, annotare e pubblicare risorse video.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
translation-type: tm+mt
source-git-commit: 9ced187ddc9bb2d12922fcc734b20ef9767d8fbf
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 9%

---


# Gestire le risorse video {#managing-video-assets}

Scopri come gestire e modificare le risorse video in Risorse Adobe Experience Manager (AEM). Inoltre, se disponete di una licenza per l’utilizzo di contenuti multimediali dinamici, consultate la documentazione [Video per contenuti multimediali](video.md)dinamici.

## Caricare e visualizzare in anteprima le risorse video {#uploading-and-previewing-video-assets}

 AEM Assets genera anteprime per le risorse video con l’estensione MP4. Se il formato della risorsa non è MP4, installate il pacchetto FFmpeg per generare un&#39;anteprima. FFmpeg crea rappresentazioni video di tipo OGG e MP4. Potete visualizzare l&#39;anteprima di queste rappresentazioni nell&#39;interfaccia utente  AEM Assets.

1. Nella cartella o nelle sottocartelle Risorse digitali, individuate il percorso in cui desiderate aggiungere le risorse digitali.
1. Per caricare la risorsa, toccate o fate clic su **[!UICONTROL Crea]** dalla barra degli strumenti, quindi scegliete **[!UICONTROL File]**. In alternativa, rilasciatelo direttamente nell’area delle risorse. Per informazioni dettagliate sull’operazione di caricamento, consultate [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets) .
1. Per visualizzare un’anteprima del video nella vista a schede, toccate il pulsante **[!UICONTROL Riproduci]** sulla risorsa video.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   Potete mettere in pausa o riprodurre il video solo nella vista **[!UICONTROL Scheda]** . Il pulsante Riproduci/Pausa non è disponibile nella vista **[!UICONTROL Elenco]** .

1. Toccate l&#39;icona **[!UICONTROL Modifica]** sulla scheda per visualizzare l&#39;anteprima del video nella visualizzazione **[!UICONTROL Dettagli]** .

   Il video viene riprodotto nel lettore video nativo del browser. Potete riprodurre, mettere in pausa, controllare il volume e ingrandire il video a schermo intero.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## Configurazione per il caricamento di risorse di dimensioni superiori a 2 GB {#configuration-to-upload-video-assets-that-are-larger-than-gb}

Per impostazione predefinita, l’AEM Assets  non consente di caricare risorse di dimensioni superiori a 2 GB a causa di un limite di dimensione file. Tuttavia, potete sovrascrivere questo limite entrando nel CRXDE Lite e creando un nodo sotto la `/apps` directory. Il nodo deve avere lo stesso nome di nodo, la stessa struttura di directory e le stesse proprietà di nodo confrontabili dell&#39;ordine.

Oltre  configurazione AEM Assets, modificate le seguenti configurazioni per caricare risorse di grandi dimensioni:

* Aumenta l’ora di scadenza del token. Consulta [!UICONTROL servlet] CSRF Granite Adobe nella console Web all’indirizzo `https://[aem_server]:[port]/system/console/configMgr`. Per ulteriori informazioni, vedere [Protezione](/help/sites-developing/csrf-protection.md)CSRF.
* Aumentare la configurazione `receiveTimeout` del dispatcher. Per ulteriori informazioni, consultate [configurazione](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)del dispatcher di Experienci Manager.

>[!NOTE]
>
>L&#39;interfaccia utente di AEM Classic non ha un limite di dimensione file di due gigabyte. Inoltre, il flusso di lavoro end-to-end per i video di grandi dimensioni non è completamente supportato.

Per configurare un limite di dimensione file più elevato, eseguire i seguenti passaggi nella `/apps` directory.

1. In AEM, tocca **[!UICONTROL Strumenti > Generale > CRXDE Lite]**.
1. Nella pagina **[!UICONTROL CRXDE Lite]** , nella finestra della directory a sinistra, passare a `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Per visualizzare la finestra della directory, toccate `>>` l&#39;icona.
1. From the toolbar, tap **[!UICONTROL Overlay Node]**. In alternativa, seleziona **[!UICONTROL Sovrapponi nodo]** dal menu di scelta rapida.
1. Nella finestra di dialogo **[!UICONTROL Sovrapponi nodo]**, tocca **[!UICONTROL OK]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. Aggiorna il browser. Il nodo di sovrapposizione `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` è selezionato.
1. Nella scheda **[!UICONTROL Proprietà]** , immettete il valore appropriato in byte per aumentare il limite delle dimensioni fino alla dimensione desiderata. Ad esempio, immettete il seguente valore per aumentare il limite di dimensione a 30 GB:

   `{sizeLimit : "32212254720"}`

1. Dalla barra degli strumenti, toccate **[!UICONTROL Salva tutto]**.
1. All’interno di AEM, tocca **[!UICONTROL Strumenti > Operazioni > Console web]**.
1. Nella pagina Bundle **[!UICONTROL della console Web di]** Adobe Experience Manager, nella colonna **[!UICONTROL Nome]** della tabella, individuare e toccare **[!UICONTROL Gestoreprocesso esterno del flusso di lavoro Granite del Adobe]**.
1. In the **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** page, set the seconds for both **[!UICONTROL Default Timeout]** and **[!UICONTROL Max Timeout]** fields to `18000` (five hours).
1. Toccate **[!UICONTROL Salva]**.
1. In AEM, toccate **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Nella pagina Modelli **[!UICONTROL di]** flusso di lavoro, seleziona **[!UICONTROL Codifica video]** elemento multimediale dinamico, quindi tocca **[!UICONTROL Modifica]**.
1. Nella pagina **[!UICONTROL Workflow]** , toccate due volte il componente **[!UICONTROL Dynamic Media Video Service Process]** .
1. Nella finestra di dialogo **[!UICONTROL Step Properties (Proprietà passo)]**, nella scheda **[!UICONTROL Common (Comune)]**, espandi **[!UICONTROL Impostazioni avanzate]**.
1. Nel campo **[!UICONTROL Timeout]**, specifica un valore di `18000`, quindi tocca **[!UICONTROL OK]** per tornare alla pagina del flusso di lavoro **[!UICONTROL Codifica video elementi multimediali dinamici]**.
1. Nella parte superiore della pagina, sotto il titolo della pagina **[!UICONTROL Codifica video]** elemento multimediale dinamico, toccate **[!UICONTROL Salva]**.

## Pubblicare risorse video {#publishing-video-assets}

Dopo la pubblicazione, le risorse video sono disponibili per l’inclusione in una pagina Web mediante un URL o l’incorporazione in una pagina Web. Consultate [Pubblicare le risorse](publishing-dynamicmedia-assets.md).

## Annotazione delle risorse video {#annotating-video-assets}

1. Dalla console Risorse, toccate l’icona **[!UICONTROL Modifica]** sulla scheda della risorsa per visualizzare la pagina dei dettagli della risorsa.
1. Toccate l’icona **[!UICONTROL Anteprima]** per riprodurre il video.
1. Per annotare il video, toccate il pulsante **[!UICONTROL Annota]** . Un’annotazione viene aggiunta al particolare punto temporale (fotogramma) del video.

   Durante l&#39;annotazione, è possibile disegnare sul quadro e inserire un commento con il disegno. I commenti vengono salvati automaticamente in Adobe Experience Manager Assets.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   Per uscire dalla procedura guidata di annotazione, toccate **[!UICONTROL Chiudi]**.

1. To jump to a specific point in the video, specify the time in seconds in the text field and click **[!UICONTROL Jump]**. For example, to skip the first 10 seconds of video, enter `20` in the text field.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. Fate clic su un’annotazione per visualizzarla nella timeline. Toccate **[!UICONTROL Elimina]** per rimuovere l’annotazione dalla timeline.

   ![chlimage_1-206](assets/chlimage_1-206.png)
