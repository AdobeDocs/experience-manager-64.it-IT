---
title: Configurazione delle impostazioni di AEM DS
seo-title: Configurazione delle impostazioni di AEM DS
description: È necessario specificare l’URL del server di elaborazione prima di inviare un modulo.
seo-description: È necessario specificare l’URL del server di elaborazione prima di inviare un modulo.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Configurazione delle impostazioni di AEM DS {#configuring-aem-ds-settings}

Questo articolo descrive come configurare **AEM Servizio impostazioni DS**. Questa impostazione può essere utilizzata in più scenari, ad esempio:

* In Gestione della corrispondenza

   * Per configurare il flusso di lavoro AEM Forms
   * Durante l’utilizzo del portale dei moduli per il salvataggio remoto della bozza/invio

* Nei moduli adattivi per i casi in cui il modulo adattivo viene inviato dall’istanza di pubblicazione

Di seguito sono riportati i passaggi per configurare le **[!UICONTROL AEM impostazioni DS]**:

1. Apri Configuration Manager nell&#39;istanza di pubblicazione utilizzando l&#39;URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. Nella finestra **[!UICONTROL Configurazione console Web Adobe Experience Manager]**, individuare e fare clic sull&#39;opzione **[!UICONTROL AEM Impostazioni DS]**.

   ![ds_settings](assets/ds_settings.png)

1. Nella finestra **[!UICONTROL AEM Servizio impostazioni DS]** vengono visualizzate le impostazioni di configurazione comuni per i componenti DS di AEM.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Aggiungi le seguenti informazioni nei rispettivi campi:

   **[!UICONTROL URL]** del server di elaborazione: Il server di elaborazione è il server in cui deve essere attivato il flusso di lavoro Forms o AEM. Può essere lo stesso dell’URL dell’istanza di authoring AEM o dell’altro URL del server (cioè http:// localhost:port/).

   **[!UICONTROL Nome]** utente del server di elaborazione: Nome utente dell’utente del flusso di lavoro in  [base all’URL del server utilizzato]

   **[!UICONTROL Password]** server di elaborazione: Password dell&#39;utente del flusso di lavoro

   >[!NOTE]
   >
   >* Durante l&#39;utilizzo dei flussi di lavoro Forms o AEM, prima di effettuare invii dal server di pubblicazione, è necessario configurare il servizio delle impostazioni DS. In caso contrario, la presentazione del modulo non verrà eseguita.

