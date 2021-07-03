---
title: Rappresentazioni video
description: Rappresentazioni video
contentOwner: AG
feature: Video, rappresentazioni
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Rappresentazioni video {#video-renditions}

Adobe Experience Manager (AEM) Assets genera rappresentazioni video per risorse video di vari formati, inclusi OGG, FLV e così via.

AEM Assets supporta le rappresentazioni statiche e dinamiche (rappresentazioni con codifica DM) per le risorse multimediali.

Le rappresentazioni statiche vengono generate in modo nativo utilizzando FFMPEG (installato e disponibile nel percorso di sistema) e memorizzate nell’archivio dei contenuti.

Le rappresentazioni con codifica DM vengono memorizzate nel server proxy e distribuite in fase di runtime.

Le risorse AEM supportano la riproduzione di queste rappresentazioni sul lato client.

Per visualizzare le rappresentazioni di una particolare risorsa video, apri la relativa pagina delle risorse e tocca l’icona Navigazione globale . Quindi, scegli **[!UICONTROL Rendering]** dall’elenco.

![chlimage_1-478](assets/chlimage_1-478.png)

L’elenco delle rappresentazioni video viene visualizzato nel pannello **[!UICONTROL Rappresentazioni]** .

![chlimage_1-479](assets/chlimage_1-479.png)

Per configurare il server proxy per rappresentazioni con codifica DM, [configura i servizi Dynamic Media Cloud.](config-dynamic.md)

Per generare rappresentazioni video con i parametri desiderati, [crea un profilo video corrispondente](video-profiles.md).

Dopo aver configurato il server proxy e creato i profili video, puoi includere questo predefinito video in un profilo di elaborazione e applicare il profilo di elaborazione a una cartella.

>[!NOTE]
>
>La riproduzione audio non funziona per i file OGG e WAV su Internet Explorer 11. Nella pagina dei dettagli della risorsa viene visualizzato un errore &quot;Sorgente non valida&quot; per le risorse con estensione OGG o WAV.
>
>Su MS Edge e iPad , i file OGG non riproducono e generano un errore di formato non supportato.
