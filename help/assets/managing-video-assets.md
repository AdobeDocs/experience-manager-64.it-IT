---
title: Gestire le risorse video
description: Scopri come caricare, visualizzare in anteprima, annotare e pubblicare risorse video.
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: Asset Management,Video
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 9%

---


# Gestire le risorse video {#managing-video-assets}

Scopri come gestire e modificare le risorse video in Risorse Adobe Experience Manager (AEM). Inoltre, se disponi di una licenza per l&#39;utilizzo di Dynamic Media, consulta la [documentazione video Dynamic Media](video.md).

## Caricare e visualizzare in anteprima le risorse video {#uploading-and-previewing-video-assets}

AEM Assets genera anteprime per le risorse video con l’estensione MP4. Se il formato della risorsa non è MP4, installa il pacchetto FFmpeg per generare un&#39;anteprima. FFmpeg crea rappresentazioni video di tipo OGG e MP4. Puoi visualizzare in anteprima tali rappresentazioni nell’interfaccia utente di AEM Assets.

1. Nella cartella o nelle sottocartelle Risorse digitali, individua il percorso in cui desideri aggiungere le risorse digitali.
1. Per caricare la risorsa, tocca o fai clic su **[!UICONTROL Crea]** nella barra degli strumenti, quindi scegli **[!UICONTROL File]**. In alternativa, puoi rilasciarlo direttamente nell’area delle risorse. Per informazioni dettagliate sull’operazione di caricamento, consulta [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets) .
1. Per visualizzare un video in anteprima nella vista a schede, tocca il pulsante **[!UICONTROL Play]** sulla risorsa video.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   È possibile mettere in pausa o riprodurre video solo nella visualizzazione **[!UICONTROL Scheda]**. Il pulsante Riproduci/Pausa non è disponibile nella visualizzazione **[!UICONTROL Elenco]**.

1. Toccare l&#39;icona **[!UICONTROL Modifica]** sulla scheda per visualizzare l&#39;anteprima del video nella visualizzazione **[!UICONTROL Dettagli]**.

   Il video viene riprodotto nel lettore video nativo del browser. È possibile riprodurre, mettere in pausa, controllare il volume e ingrandire il video a schermo intero.

   ![chlimage_1-202](assets/chlimage_1-202.png)

## Configurazione per caricare risorse di dimensioni superiori a 2 GB {#configuration-to-upload-video-assets-that-are-larger-than-gb}

Per impostazione predefinita, AEM Assets non consente di caricare risorse di dimensioni superiori a 2 GB a causa di un limite di dimensioni del file. Tuttavia, puoi sovrascrivere questo limite entrando in CRXDE Lite e creando un nodo sotto la directory `/apps` . Il nodo deve avere lo stesso nome del nodo, la struttura della directory e le proprietà del nodo confrontabili dell&#39;ordine.

Oltre alla configurazione di AEM Assets, modifica le seguenti configurazioni per caricare risorse di grandi dimensioni:

* Aumenta il tempo di scadenza del token. Consulta [!UICONTROL Adobe Granite CSRF Servlet] nella console Web all&#39;indirizzo `https://[aem_server]:[port]/system/console/configMgr`. Per ulteriori informazioni, consulta [Protezione CSRF](/help/sites-developing/csrf-protection.md).
* Aumenta il `receiveTimeout` nella configurazione del Dispatcher. Per ulteriori informazioni, consulta [Configurazione di Experience Manager Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>L&#39;interfaccia utente di AEM Classic non dispone di un limite di dimensione del file di due gigabyte. Inoltre, il flusso di lavoro end-to-end per video di grandi dimensioni non è completamente supportato.

Per configurare un limite di dimensione del file più elevato, esegui i seguenti passaggi nella directory `/apps` .

1. In AEM, tocca **[!UICONTROL Strumenti > Generale > CRXDE Lite]**.
1. Nella pagina **[!UICONTROL CRXDE Lite]**, nella finestra della directory a sinistra, passa a `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Per visualizzare la finestra della directory, tocca l’icona `>>` .
1. Dalla barra degli strumenti, tocca **[!UICONTROL Sovrapponi nodo]**. In alternativa, seleziona **[!UICONTROL Sovrapponi nodo]** dal menu di scelta rapida.
1. Nella finestra di dialogo **[!UICONTROL Sovrapponi nodo]**, tocca **[!UICONTROL OK]**.

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. Aggiorna il browser. Il nodo di sovrapposizione `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` è selezionato.
1. Nella scheda **[!UICONTROL Proprietà]** , immetti il valore appropriato in byte per aumentare il limite di dimensioni alle dimensioni desiderate. Ad esempio, immetti il valore `32212254720` per aumentare il limite di dimensione a 30 GB.

1. Dalla barra degli strumenti, tocca **[!UICONTROL Salva tutto]**.
1. All’interno di AEM, tocca **[!UICONTROL Strumenti > Operazioni > Console web]**.
1. Nella pagina **[!UICONTROL Adobe Experience Manager Web Console Bundles]**, sotto la colonna **[!UICONTROL Name]** della tabella, individua e tocca **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Nella pagina **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** , imposta i secondi per i campi **[!UICONTROL Default Timeout]** e **[!UICONTROL Max Timeout]** su `18000` (cinque ore).
1. Tocca **[!UICONTROL Salva]**.
1. In AEM, tocca **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Nella pagina **[!UICONTROL Modelli di flusso di lavoro]**, seleziona **[!UICONTROL Codifica video Dynamic Media]**, quindi tocca **[!UICONTROL Modifica]**.
1. Nella pagina **[!UICONTROL Flusso di lavoro]**, tocca due volte il componente **[!UICONTROL Processo servizio video Dynamic Media]** .
1. Nella finestra di dialogo **[!UICONTROL Step Properties (Proprietà passo)]**, nella scheda **[!UICONTROL Common (Comune)]**, espandi **[!UICONTROL Impostazioni avanzate]**.
1. Nel campo **[!UICONTROL Timeout]**, specifica un valore di `18000`, quindi tocca **[!UICONTROL OK]** per tornare alla pagina del flusso di lavoro **[!UICONTROL Codifica video elementi multimediali dinamici]**.
1. Nella parte superiore della pagina, sotto il titolo della pagina **[!UICONTROL Codifica video Dynamic Media]** , tocca **[!UICONTROL Salva]**.

## Pubblicare risorse video {#publishing-video-assets}

Dopo la pubblicazione, le risorse video sono disponibili per l’inclusione in una pagina web tramite un URL o per l’incorporamento in una pagina web. Consulta [Pubblicare risorse](publishing-dynamicmedia-assets.md).

## Annotare risorse video {#annotating-video-assets}

1. Dalla console Assets, tocca l’icona **[!UICONTROL Modifica]** nella scheda delle risorse per visualizzare la pagina dei dettagli della risorsa.
1. Tocca l’icona **[!UICONTROL Anteprima]** per riprodurre il video.
1. Per annotare il video, tocca il pulsante **[!UICONTROL Annota]** . Nel video viene aggiunta un’annotazione al particolare punto temporale (fotogramma).

   Durante l&#39;annotazione, potete disegnare sull&#39;area di lavoro e includere un commento nel disegno. I commenti vengono salvati automaticamente in Adobe Experience Manager Assets.

   ![chlimage_1-204](assets/chlimage_1-204.png)

   Per uscire dalla procedura guidata di annotazione, tocca **[!UICONTROL Chiudi]**.

1. Per passare a un punto specifico del video, specifica il tempo in secondi nel campo di testo e fai clic su **[!UICONTROL Jump]**. Ad esempio, per saltare i primi 20 secondi del video, immetti `20` nel campo di testo.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. Fate clic su un’annotazione per visualizzarla nella timeline. Toccate **[!UICONTROL Elimina]** per rimuovere l’annotazione dalla timeline.

   ![chlimage_1-206](assets/chlimage_1-206.png)
