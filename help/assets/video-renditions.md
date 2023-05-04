---
title: Rappresentazioni video
description: Rappresentazioni video
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 3%

---

# Rappresentazioni video {#video-renditions}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets genera rappresentazioni video per risorse video di vari formati, inclusi OGG, FLV e così via.

AEM Assets supporta le rappresentazioni statiche e dinamiche (rappresentazioni con codifica DM) per le risorse multimediali.

Le rappresentazioni statiche vengono generate in modo nativo utilizzando FFMPEG (installato e disponibile nel percorso di sistema) e memorizzate nell’archivio dei contenuti.

Le rappresentazioni con codifica DM vengono memorizzate nel server proxy e distribuite in fase di runtime.

Le risorse AEM supportano la riproduzione di queste rappresentazioni sul lato client.

Per visualizzare le rappresentazioni di una particolare risorsa video, apri la relativa pagina delle risorse e tocca l’icona Navigazione globale . Quindi, scegli **[!UICONTROL Rendering]** dall&#39;elenco.

![chlimage_1-478](assets/chlimage_1-478.png)

L’elenco delle rappresentazioni video viene visualizzato in **[!UICONTROL Rendering]** pannello.

![chlimage_1-479](assets/chlimage_1-479.png)

Per configurare il server proxy per le rappresentazioni con codifica DM, [configurare i servizi Dynamic Media Cloud.](config-dynamic.md)

Per generare rappresentazioni video con i parametri desiderati, [creare un profilo video corrispondente](video-profiles.md).

Dopo aver configurato il server proxy e creato i profili video, puoi includere questo predefinito video in un profilo di elaborazione e applicare il profilo di elaborazione a una cartella.

>[!NOTE]
>
>La riproduzione audio non funziona per i file OGG e WAV su Internet Explorer 11. Nella pagina dei dettagli della risorsa viene visualizzato un errore &quot;Sorgente non valida&quot; per le risorse con estensione OGG o WAV.
>
>Su MS Edge e iPad , i file OGG non vengono riprodotti e generano un errore di formato non supportato.
