---
title: Flusso di attività nella timeline
description: 'Questo articolo descrive come visualizzare i registri attività per le risorse nella timeline. '
contentOwner: AG
feature: Gestione risorse
role: User,Admin
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 33%

---

# Flusso di attività nella timeline {#activity-stream-in-timeline}

Questa funzione visualizza i registri attività per le risorse nella timeline. Se esegui una delle seguenti operazioni relative alle risorse in Adobe Experience Manager (AEM) Assets, la funzione Flusso di attività aggiorna la timeline per riflettere l’attività.

Le seguenti operazioni vengono registrate nel flusso di attività:

* Crea
* Elimina
* Download (incluse le rappresentazioni)
* Pubblicazione
* Annulla pubblicazione
* Approva
* Rifiuta
* Sposta

I registri attività da visualizzare nella timeline vengono recuperati dalla posizione `/var/audit/com.day.cq.dam/content/dam` di CRX, dove vengono memorizzati i file di registro.

Inoltre, l’attività timeline viene registrata al caricamento di nuove risorse o quando le risorse esistenti vengono modificate e archiviate in AEM tramite [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) o l’[app desktop AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html).

>[!NOTE]
>
>I flussi di lavoro transitori non vengono visualizzati nella timeline, perché per questi flussi di lavoro non vengono salvate informazioni sulla cronologia.

Per visualizzare il flusso di attività, esegui una o più operazioni sulla risorsa, seleziona la risorsa, quindi scegli **[!UICONTROL Timeline]** dall’elenco Navigazione globale.

![timeline-3](assets/timeline-3.png)

La timeline mostra il flusso di attività per le operazioni eseguite sulle risorse.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>La posizione predefinita dell’archivio del registro per le attività di tipo **Pubblica** e **Annulla pubblicazione** è `/var/audit/com.day.cq.replication/content`. Per le attività di tipo **Sposta**, la posizione predefinita è `/var/audit/com.day.cq.wcm.core.page`.
