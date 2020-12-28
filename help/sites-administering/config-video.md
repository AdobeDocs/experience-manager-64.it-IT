---
title: Configurare il componente Video
seo-title: Configurare il componente Video
description: Scoprite come configurare il componente Video.
seo-description: Scoprite come configurare il componente Video.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
translation-type: tm+mt
source-git-commit: d2b4e6599a7b1c01dc220a03b2be9aa55e5d7458
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 7%

---


# Configurare il componente Video {#configure-the-video-component}

Il [componente Video](/help/sites-authoring/default-components-foundation.md#video) consente di inserire un elemento video predefinito OOOTB (out-of-the-box) nella pagina.

Per eseguire la transcodifica corretta, l&#39;amministratore deve [installare FFmpeg e configurare AEM](#install-ffmpeg) separatamente. Possono anche [configurare i profili video](#configure-video-profiles) per l&#39;utilizzo con elementi di HTML5.

## Configurare i profili video {#configure-video-profiles}

Potete definire i profili video da usare per gli elementi HTML5. Quelli scelti qui sono utilizzati in ordine. Per accedere, utilizzare la [modalità Progettazione](/help/sites-authoring/default-components-designmode.md) (solo interfaccia classica) e selezionare la scheda **[!UICONTROL Profili]**:

![chlimage_1-317](assets/chlimage_1-317.png)

È inoltre possibile configurare la progettazione dei componenti video e dei parametri per [!UICONTROL Playback], [!UICONTROL Flash] e [!UICONTROL Advanced].

## Installare FFmpeg e configurare AEM {#install-ffmpeg}

Il componente Video si basa sul prodotto open-source di terze parti FFmpeg per la corretta transcodifica dei video che è possibile scaricare da [https://ffmpeg.org/](https://ffmpeg.org/). Dopo aver installato FFmpeg, è necessario configurare AEM per utilizzare un codec audio specifico e opzioni runtime specifiche.

**Per installare FFmpeg per la piattaforma**:

* **In Windows:**

   1. Scarica il binario compilato come `ffmpeg.zip`
   1. Decomprimete il file in una cartella.
   1. Impostare la variabile di ambiente del sistema `PATH` su `<*your-ffmpeg-locatio*n>\bin`
   1. Riavviate AEM.

* **In Mac OS X:**

   1. Installare Xcode ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. Installate XQuartz/X11.
   1. Installazione di MacPorts ([https://www.macports.org/](https://www.macports.org/))
   1. Nella console eseguire il comando seguente e seguire le istruzioni:

      `sudo port install ffmpeg`

      `FFmpeg` deve essere in  `PATH` modo AEM può recuperarlo tramite la riga di comando.

* **Utilizzo della versione precompilata per OS X 10.6:**

   1. Scaricate la versione precompilata.
   1. Estraetela nella directory `/usr/local`.
   1. Dal terminale, eseguire:

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**Per configurare AEM**:

1. Aprite [!UICONTROL CRXDE Lite] nel browser Web. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Selezionare il nodo `/libs/settings/dam/video/format_aac/jcr:content` e assicurarsi che le proprietà del nodo siano le seguenti:

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. Per personalizzare la configurazione, create una sovrapposizione nel nodo `/apps/settings/` e spostate la stessa struttura sotto il nodo `/conf/global/settings/`. Non può essere modificato nel nodo `/libs`. Ad esempio, per sovrapporre il percorso `/libs/settings/dam/video/fullhd-bp`, createlo in corrispondenza di `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Sovrapponi e modifica l’intero nodo del profilo e non solo la proprietà che deve essere modificata. Tali risorse non vengono risolte tramite SlingResourceMerger.

1. Se avete modificato una delle proprietà, fate clic su **[!UICONTROL Salva tutto]**.

>[!NOTE]
>
>I modelli di flusso di lavoro OOTB non vengono conservati quando si aggiorna l&#39;istanza AEM.  Adobe consiglia di copiare i modelli di flussi di lavoro OOTB prima di modificarli. Ad esempio, copiate il modello OOTB DAM Update Asset prima di modificare il passaggio di transcodifica FFmpeg nel modello DAM Update Asset per scegliere i nomi dei profili video esistenti prima dell’aggiornamento. Quindi, potete sovrapporre il nodo `/apps` per AEM recuperare le modifiche personalizzate al modello OOTB.

