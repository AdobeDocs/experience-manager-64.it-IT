---
title: Configurazione delle impostazioni di AEM DS
seo-title: Configurazione delle impostazioni di AEM DS
description: È necessario specificare l'URL del server di elaborazione prima di inviare il modulo.
seo-description: È necessario specificare l'URL del server di elaborazione prima di inviare il modulo.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Configurazione delle impostazioni di AEM DS {#configuring-aem-ds-settings}

Questo articolo descrive come configurare il servizio **Impostazioni di** AEM DS. Questa impostazione può essere utilizzata in più scenari, ad esempio:

* In Gestione della corrispondenza

   * Per configurare il flusso di lavoro per AEM Forms
   * Durante l&#39;utilizzo del portale dei moduli per il salvataggio remoto della bozza/invio

* Nei moduli adattivi per i casi in cui il modulo adattivo viene inviato dall’istanza di pubblicazione

Seguono i passaggi per configurare le impostazioni **[!UICONTROL di]** AEM DS:

1. Aprite Configuration Manager nell&#39;istanza di pubblicazione utilizzando l&#39;URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. Nella finestra Configurazione **[!UICONTROL console Web di]** Adobe Experience Manager, individua e fai clic sull’opzione Impostazioni **[!UICONTROL di]** AEM DS.

   ![ds_settings](assets/ds_settings.png)

1. Nella finestra del servizio **[!UICONTROL Impostazioni]** AEM DS vengono visualizzate le impostazioni di configurazione comuni per i componenti AEM DS.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Aggiungete le seguenti informazioni nei rispettivi campi:

   **[!UICONTROL URL]** server di elaborazione: Il server di elaborazione è il server in cui è necessario avviare il flusso di lavoro Forms o AEM. Può corrispondere all’URL dell’istanza di creazione AEM o dell’altro URL del server (http:// localhost:port/).

   **[!UICONTROL Nome]** utente del server di elaborazione: Nome utente dell’utente del flusso di lavoro [in base all’URL del server utilizzato]

   **[!UICONTROL Password]** server di elaborazione: Password utente flusso di lavoro

   >[!NOTE]
   >
   >* Durante l&#39;utilizzo di flussi di lavoro Forms o AEM, prima di effettuare qualsiasi invio dal server di pubblicazione è necessario configurare il servizio delle impostazioni DS. In caso contrario, la presentazione del modulo non può essere effettuata.

