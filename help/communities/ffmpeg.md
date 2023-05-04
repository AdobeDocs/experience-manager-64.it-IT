---
title: FFmpeg per Communities
seo-title: FFmpeg for Communities
description: Come installare e configurare FFmpeg per Communities
seo-description: How to install and configure FFmpeg for Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Admin
exl-id: 9ed54ee3-3509-4a43-a710-90f4543ccaf3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# FFmpeg per Communities {#ffmpeg-for-communities}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

FFmpeg è una soluzione per la conversione e lo streaming audio e video e, quando installato, viene utilizzato per la corretta transcodifica di [risorse video](../../help/sites-authoring/default-components-foundation.md#video) e per la funzione di abilitazione di AEM Communities.

FFmpeg viene utilizzato nell’ambiente di authoring per ottenere i metadati per le risorse di abilitazione caricate e generare una miniatura da visualizzare quando si elenca la risorsa di abilitazione.

## Installazione di FFmpeg {#installing-ffmpeg}

FFmpeg deve essere installato sui server che ospitano il AEM *autore* istanze.

1. Vai a [https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. Scarica la versione più recente di FFmpeg per il tuo ambiente specifico (Macintosh, Windows o Linux)

   * è importante mantenere aggiornato FFmpeg a causa di vulnerabilità di sicurezza nelle versioni precedenti

1. Installa FFmpeg seguendo le istruzioni per il sistema operativo.

1. Assicurati che l&#39;eseguibile FFmpeg sia impostato nel percorso del sistema.

   Dovresti essere in grado di eseguire FFmpeg da qualsiasi directory del sistema.

   * ad esempio, `ffmpeg -version`

## Configurare il servizio di transcodifica FFmpeg {#configure-ffmpeg-transcoding-service}

Per impostazione predefinita, quando FFmpeg è installato, vengono configurate più rappresentazioni (transcodings) in base alla definizione del flusso di lavoro DAM Update Asset.

Poiché le transcodings sono ad alta intensità di CPU, si consiglia di modificare l’elenco delle rappresentazioni di destinazione. Nella maggior parte dei casi, la transcodifica non è necessaria.

Per modificare il flusso di lavoro Aggiorna risorsa DAM e, in questo esempio, per disattivare la transcodifica:

* Accedi all’istanza di authoring con privilegi amministrativi
* Dalla navigazione globale: **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**
* Individua **[!UICONTROL Risorsa di aggiornamento DAM]**
* Fai doppio clic per aprire il flusso di lavoro per la modifica nell’interfaccia classica

   Posizione risultante: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Fai doppio clic sul pulsante **[!UICONTROL Transcodifica FFmpeg]** passaggio per accedere alla finestra di dialogo Proprietà passaggio
* Sotto la **[!UICONTROL Processo]** scheda:

   * **[!UICONTROL Arruoli]**: Cancella tutte le voci per disabilitare la transcodifica Valori predefiniti: `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* Seleziona **[!UICONTROL OK]** per chiudere `Step Properties` dialogo

* Seleziona **[!UICONTROL Salva]** per salvare `DAM Update Asset` workflow

   (angolo in alto a sinistra)
