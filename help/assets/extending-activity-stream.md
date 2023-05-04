---
title: Integrazione delle risorse con il flusso di attività
description: Descrive le funzionalità di registrazione di [!DNL Experience Manager] e come configurare [!DNL Experience Manager] per registrare eventi specifici.
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 3%

---

# Integrazione delle risorse con il flusso di attività {#integrating-assets-with-activity-stream}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Gli utenti di Adobe Experience Manager Assets eseguono molte azioni, come la creazione, il caricamento e l’eliminazione di Assets. Queste azioni possono essere registrate in modo da fornire una cronologia di ciò che è stato fatto da un utente. Questa sezione descrive le funzionalità di registrazione di [!DNL Experience Manager] e come configurare [!DNL Experience Manager] per registrare eventi specifici.

## Considerazioni sulle prestazioni e comportamento predefinito {#performance-considerations-and-default-behavior}

Questa integrazione potrebbe richiedere CPU e spazio su disco, ad esempio durante l&#39;importazione in massa. Per queste ragioni, [!DNL Experience Manager] L’integrazione delle risorse con l’Flusso attività è disabilitata per impostazione predefinita.

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

## Configurazione [!DNL Assets] Registrazione eventi {#configuring-aem-assets-events-recording}

La [Console web](/help/sites-deploying/configuring-osgi.md) fornisce accesso al [!DNL Assets] Sintonizzazione del registratore di eventi. Per configurare le [!DNL Assets] Registratore eventi, procedere come segue:

1. Passa a **[!UICONTROL Console web]**

1. Fai clic su **[!UICONTROL Configurazione]**.

1. Doppio clic **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Controlla **[!UICONTROL Abilita questo servizio]**.

1. Controlla quali **[!UICONTROL Tipi di eventi]** vuoi essere registrato nel flusso di attività dell’utente.

1. Fai clic su **[!UICONTROL Salva]**.

## Lettura degli eventi registrati {#reading-recorded-events}

Gli eventi registrati vengono memorizzati come attività. Puoi leggerle a livello di programmazione utilizzando il [API di ActivityManager](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
