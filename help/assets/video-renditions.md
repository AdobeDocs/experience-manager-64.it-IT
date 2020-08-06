---
title: Rappresentazioni video
description: Rappresentazioni video
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Video renditions {#video-renditions}

Adobe Experience Manager (AEM) Assets genera rappresentazioni video per risorse video di vari formati, inclusi OGG, FLV e così via.

 AEM Assets supporta rappresentazioni statiche e dinamiche (rappresentazioni con codifica DM) per risorse multimediali.

Le rappresentazioni statiche vengono generate in modo nativo utilizzando FFMPEG (installato e disponibile nel percorso di sistema) e memorizzate nell&#39;archivio dei contenuti.

Le rappresentazioni con codifica DM vengono memorizzate nel server proxy e servite in fase di esecuzione.

AEM risorse supportano la riproduzione per queste rappresentazioni sul lato client.

Per visualizzare le rappresentazioni di una particolare risorsa video, aprite la relativa pagina di risorse e toccate l’icona Navigazione globale. Quindi, scegliete **[!UICONTROL Rappresentazioni]** dall&#39;elenco.

![chlimage_1-478](assets/chlimage_1-478.png)

L&#39;elenco delle rappresentazioni video viene visualizzato nel pannello **[!UICONTROL Rappresentazioni]** .

![chlimage_1-479](assets/chlimage_1-479.png)

Per configurare il server proxy per le rappresentazioni con codifica DM, [configura i servizi Dynamic Media Cloud.](config-dynamic.md)

Per generare rappresentazioni video con i parametri desiderati, [create un profilo](video-profiles.md)video corrispondente.

Dopo aver configurato il server proxy e creato i profili video, potete includere questo predefinito video in un profilo di elaborazione e applicare il profilo di elaborazione a una cartella.

>[!NOTE]
>
>La riproduzione audio non funziona per i file OGG e WAV in Internet Explorer 11. Nella pagina dei dettagli della risorsa viene visualizzato un errore &quot;Sorgente non valida&quot; per le risorse con estensione OGG o WAV.
>
>In MS Edge e iPad, i file OGG non vengono riprodotti e generano un errore di formato non supportato.
