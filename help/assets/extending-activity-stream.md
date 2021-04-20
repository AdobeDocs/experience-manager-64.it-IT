---
title: Integrazione delle risorse con il flusso di attività
description: Descrive le funzionalità di registrazione di AEM e come configurare AEM per registrare eventi specifici.
contentOwner: AG
feature: Asset Management
role: Developer
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# Integrazione delle risorse con il flusso di attività {#integrating-assets-with-activity-stream}

Gli utenti di Adobe Experience Manager (AEM) Assets eseguono molte azioni, come la creazione, il caricamento e l’eliminazione di Assets. Queste azioni possono essere registrate in modo da fornire una cronologia di ciò che è stato fatto da un utente. Questa sezione descrive le funzionalità di registrazione di AEM e come configurare AEM per registrare eventi specifici.

## Considerazioni sulle prestazioni e comportamento predefinito {#performance-considerations-and-default-behavior}

Questa integrazione potrebbe richiedere CPU e spazio su disco, ad esempio durante l&#39;importazione in massa. Per questi motivi l’integrazione di AEM Assets con Activity Stream è disabilitata per impostazione predefinita.

## Eventi azione supportati {#supported-action-events}

È possibile configurare i seguenti eventi per la registrazione:

* Licenza accettata (ACCETTATA)
* Risorsa creata (ASSET_CREATED)
* Risorsa spostata (ASSET_MOVED)
* Risorsa rimossa (ASSET_REMOVED)
* Licenza rifiutata (RIFIUTATA)
* Risorsa scaricata (SCARICATA)
* Versione risorsa (VERSIONED)
* Versione risorsa ripristinata (RIPRISTINATA)
* Metadati risorsa aggiornati (METADATA_UPDATED)
* Risorsa pubblicata nel sistema esterno (PUBLISHED_EXTERNAL)
* Aggiornato originale della risorsa (ORIGINAL_UPDATED)
* Rendering risorsa aggiornato (RENDITION_AGGIORNATO)
* Rendering risorsa rimosso (RENDITION_REMOVED)
* Risorsa secondaria aggiornata (SUBASSET_UPDATED)
* Risorsa secondaria rimossa (SUBASSET_REMOVED)

## Configurazione della registrazione di eventi AEM Assets {#configuring-aem-assets-events-recording}

La [console Web](/help/sites-deploying/configuring-osgi.md) consente di accedere alla regolazione del Registratore eventi di AEM Assets. Per configurare il registratore di eventi AEM Assets, procedere come segue:

1. Passa alla **[!UICONTROL console Web]**

1. Fare clic su **[!UICONTROL Configurazione]**.

1. Fai doppio clic su **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Seleziona **[!UICONTROL Abilita questo servizio]**.

1. Controlla quali **[!UICONTROL Tipi di eventi]** desideri registrare nel flusso di attività dell&#39;utente.

1. Fai clic su **[!UICONTROL Salva]**.

## Lettura degli eventi registrati {#reading-recorded-events}

Gli eventi registrati vengono memorizzati come attività. Puoi leggerle a livello di programmazione utilizzando l&#39; [API ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
