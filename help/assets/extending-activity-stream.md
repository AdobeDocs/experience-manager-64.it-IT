---
title: Integrazione delle risorse con il flusso di attività
description: Descrive le funzionalità di registrazione di  [!DNL Experience Manager] and how to configure [!DNL Experience Manager] per registrare eventi specifici.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Integrazione delle risorse con il flusso di attività {#integrating-assets-with-activity-stream}

Gli utenti di Adobe Experience Manager Assets eseguono molte azioni, come la creazione, il caricamento e l’eliminazione di Assets. Queste azioni possono essere registrate in modo da fornire una cronologia di ciò che è stato fatto da un utente. Questa sezione descrive le funzionalità di registrazione di [!DNL Experience Manager] e come configurare [!DNL Experience Manager] per registrare eventi specifici.

## Considerazioni sulle prestazioni e comportamento predefinito {#performance-considerations-and-default-behavior}

Questa integrazione potrebbe richiedere CPU e spazio su disco, ad esempio durante l&#39;importazione in massa. Per questi motivi l’integrazione [!DNL Experience Manager] Assets con Activity Stream è disabilitata per impostazione predefinita.

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

## Configurazione della registrazione di eventi [!DNL Assets] {#configuring-aem-assets-events-recording}

La [console Web](/help/sites-deploying/configuring-osgi.md) consente di accedere alla regolazione del [!DNL Assets] Registratore eventi. Per configurare il [!DNL Assets] Registratore eventi, procedere come segue:

1. Passa alla **[!UICONTROL console Web]**

1. Fare clic su **[!UICONTROL Configurazione]**.

1. Fai doppio clic su **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Seleziona **[!UICONTROL Abilita questo servizio]**.

1. Controlla quali **[!UICONTROL Tipi di eventi]** desideri registrare nel flusso di attività dell&#39;utente.

1. Fai clic su **[!UICONTROL Salva]**.

## Lettura degli eventi registrati {#reading-recorded-events}

Gli eventi registrati vengono memorizzati come attività. Puoi leggerle a livello di programmazione utilizzando l&#39; [API ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
