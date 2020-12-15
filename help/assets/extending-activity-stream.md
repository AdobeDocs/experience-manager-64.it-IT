---
title: Integrazione delle risorse con il flusso di attività
description: Descrive le funzionalità di registrazione di AEM e come configurare AEM per registrare eventi specifici.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Integrazione delle risorse con il flusso di attività {#integrating-assets-with-activity-stream}

Adobe Experience Manager (AEM) Gli utenti delle risorse eseguono numerose azioni come la creazione, il caricamento e l’eliminazione di risorse. Queste azioni possono essere registrate in modo da fornire una cronologia delle operazioni eseguite da un utente. Questa sezione descrive le capacità di registrazione di AEM e come configurare AEM per registrare eventi specifici.

## Considerazioni sulle prestazioni e comportamento predefinito {#performance-considerations-and-default-behavior}

Questa integrazione potrebbe richiedere CPU e spazio su disco, ad esempio durante l&#39;importazione in massa. Per questi motivi, per impostazione predefinita l&#39;integrazione  AEM Assets con il Flusso attività è disabilitata.

## Eventi azione supportati {#supported-action-events}

È possibile configurare i seguenti eventi per la registrazione:

* Licenza accettata (ACCETTATA)
* Risorsa creata (ASSET_CREATED)
* Risorsa spostata (ASSET_MOVED)
* Risorsa rimossa (ASSET_REMOVED)
* Licenza rifiutata (RIFIUTATA)
* Risorsa scaricata (SCARICATA)
* Versione risorsa (VERSIONE)
* Versione risorsa ripristinata (RIPRISTINATA)
* Metadati risorsa aggiornati (METADATA_UPDATED)
* Risorsa pubblicata nel sistema esterno (PUBLISHED_EXTERNAL)
* Aggiornamento originale della risorsa (ORIGINAL_UPDATED)
* Rendering risorsa aggiornata (RENDITION_UPDATED)
* Rendering risorsa rimosso (RENDITION_REMOVED)
* Risorsa secondaria aggiornata (SUBASSET_UPDATED)
* Risorsa secondaria rimossa (SUBASSET_REMOVED)

## Configurazione  registrazione eventi AEM Assets {#configuring-aem-assets-events-recording}

La [console Web](/help/sites-deploying/configuring-osgi.md) consente di accedere al tuning del  del registratore eventi AEM Assets. Per configurare  AEM Assets Event Recorder, effettuate le seguenti operazioni:

1. Passare alla **[!UICONTROL console Web]**

1. Fare clic su **[!UICONTROL Configuration]**.

1. Fare doppio clic su **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Selezionare **[!UICONTROL Abilita questo servizio]**.

1. Verificare quali **[!UICONTROL Tipi di eventi]** si desidera registrare nel flusso di attività dell&#39;utente.

1. Fai clic su **[!UICONTROL Salva]**.

## Lettura degli eventi registrati {#reading-recorded-events}

Gli eventi registrati vengono memorizzati come attività. Potete leggerli a livello di programmazione utilizzando l&#39;API [ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
