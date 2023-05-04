---
title: Configurare il componente Video
seo-title: Configure the Video component
description: Scopri come configurare il componente video.
seo-description: Learn how to configure the Video Component.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 46d0765d-fb77-4332-8fbb-5bd2abcd6806
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 2%

---

# Configurare il componente Video {#configure-the-video-component}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La [Componente video](/help/sites-authoring/default-components-foundation.md#video) consente di inserire un elemento video OOTB (preconfigurato) sulla pagina.

Per eseguire correttamente la transcodifica, l’amministratore deve [Installare FFmpeg e configurare AEM](#install-ffmpeg) separatamente. Possono inoltre [Configurare i profili video](#configure-video-profiles) da utilizzare con gli elementi di HTML5.

>[!CAUTION]
>
>Non è più previsto che questo componente funzioni come standard senza un’ampia personalizzazione a livello di progetto.

## Configurare i profili video {#configure-video-profiles}

È possibile definire profili video da utilizzare per gli elementi di HTML5. Quelli scelti qui sono utilizzati in ordine. Per accedere, utilizza [Modalità Progettazione](/help/sites-authoring/default-components-designmode.md) (Solo interfaccia classica) e seleziona la **[!UICONTROL Profili]** scheda:

![chlimage_1-317](assets/chlimage_1-317.png)

Puoi anche configurare la progettazione dei componenti video e dei parametri per [!UICONTROL Riproduzione], [!UICONTROL Flash]e [!UICONTROL Avanzate].

## Installare FFmpeg e configurare AEM {#install-ffmpeg}

Il componente video si basa sul prodotto open-source di terze parti FFmpeg per una corretta transcodifica dei video che è possibile scaricare da [https://ffmpeg.org/](https://ffmpeg.org/). Dopo aver installato FFmpeg, è necessario configurare AEM per utilizzare un codec audio specifico e opzioni di runtime specifiche.

**Per installare FFmpeg per la piattaforma**:

* **In Windows:**

   1. Scarica il binario compilato come `ffmpeg.zip`
   1. Decomprimi in una cartella.
   1. Imposta la variabile di ambiente del sistema `PATH` a `<*your-ffmpeg-locatio*n>\bin`
   1. Riavvia AEM.

* **Su Mac OS X:**

   1. Installa Xcode ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. Installa XQuartz/X11.
   1. Installa MacPorts ([https://www.macports.org/](https://www.macports.org/))
   1. Nella console esegui il seguente comando e segui le istruzioni:

      `sudo port install ffmpeg`

      `FFmpeg` deve essere `PATH` quindi AEM recuperarlo tramite la riga di comando.

* **Utilizzando la versione precompilata per OS X 10.6:**

   1. Scarica la versione precompilata.
   1. Estraetela nella `/usr/local` directory.
   1. Dal terminale, eseguire:

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**Per configurare AEM**:

1. Apri [!UICONTROL CRXDE Lite] nel browser web. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Seleziona la `/libs/settings/dam/video/format_aac/jcr:content` e assicurati che le proprietà del nodo siano le seguenti:

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. Per personalizzare la configurazione, crea una sovrapposizione in `/apps/settings/` e spostare la stessa struttura sotto `/conf/global/settings/` nodo. Non può essere modificato in `/libs` nodo. Ad esempio, per sovrapporre il percorso `/libs/settings/dam/video/fullhd-bp`, crea `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Sovrapponi e modifica l’intero nodo del profilo e non solo la proprietà che deve essere modificata. Tali risorse non vengono risolte tramite SlingResourceMerger.

1. Se hai modificato una delle proprietà, fai clic su **[!UICONTROL Salva tutto]**.

>[!NOTE]
>
>I modelli di flusso di lavoro OOTB non vengono mantenuti quando aggiorni l’istanza AEM. Adobe consiglia di copiare i modelli di flusso di lavoro OOTB prima di modificarli. Ad esempio, copia il modello Risorsa di aggiornamento DAM OOTB prima di modificare il passaggio Transcodifica FFmpeg nel modello Risorsa di aggiornamento DAM per scegliere i nomi dei profili video esistenti prima dell’aggiornamento. Quindi puoi sovrapporre il `/apps` per consentire AEM recuperare le modifiche personalizzate al modello OOTB.
