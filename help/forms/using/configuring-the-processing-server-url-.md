---
title: Configurazione delle impostazioni di AEM DS
seo-title: Configuring AEM DS settings
description: È necessario specificare l’URL del server di elaborazione prima di inviare un modulo.
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Admin
exl-id: f60beaae-4082-4165-8a37-9d9c94e360b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 2%

---

# Configurazione delle impostazioni di AEM DS {#configuring-aem-ds-settings}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questo articolo descrive come configurare **Servizio impostazioni di DS AEM**. Questa impostazione può essere utilizzata in più scenari, ad esempio:

* In Gestione della corrispondenza

   * Per configurare il flusso di lavoro AEM Forms
   * Durante l’utilizzo del portale dei moduli per il salvataggio remoto della bozza/invio

* Nei moduli adattivi per i casi in cui il modulo adattivo viene inviato dall’istanza di pubblicazione

Di seguito sono riportati i passaggi per configurare il **[!UICONTROL Impostazioni di AEM DS]**:

1. Apri Configuration Manager nell&#39;istanza di pubblicazione utilizzando l&#39;URL:

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. In **[!UICONTROL Configurazione della console Web di Adobe Experience Manager]** finestra, individuare e fare clic **[!UICONTROL Impostazioni di AEM DS]** opzione .

   ![ds_settings](assets/ds_settings.png)

1. La **[!UICONTROL Servizio impostazioni di DS AEM]** In questa finestra sono visualizzate le impostazioni di configurazione comuni per i componenti DS AEM.

   ![ds_settings_1](assets/ds_settings_1.png)

1. Aggiungi le seguenti informazioni nei rispettivi campi:

   **[!UICONTROL URL server di elaborazione]**: Il server di elaborazione è il server in cui deve essere attivato il flusso di lavoro Forms o AEM. Può essere lo stesso dell’URL dell’istanza di authoring AEM o dell’altro URL del server (cioè http:// localhost:port/).

   **[!UICONTROL Nome utente del server di elaborazione]**: Nome utente dell’utente del flusso di lavoro [in base all’URL del server utilizzato]

   **[!UICONTROL Password server di elaborazione]**: Password dell&#39;utente del flusso di lavoro

   >[!NOTE]
   >
   >* Durante l&#39;utilizzo dei flussi di lavoro Forms o AEM, prima di effettuare invii dal server di pubblicazione, è necessario configurare il servizio delle impostazioni DS. In caso contrario, la presentazione del modulo non verrà eseguita.

