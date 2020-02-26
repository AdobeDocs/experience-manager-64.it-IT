---
title: Configurazione di AEM Forms per l'invio dei dati del modulo a un processo AEM Forms su JEE
seo-title: Configurazione di AEM Forms per l'invio dei dati del modulo a un processo AEM Forms su JEE
description: AEM Forms consente di integrare moduli adattivi con i processi AEM Forms su JEE per l'elaborazione dei dati dei moduli.
seo-description: AEM Forms consente di integrare moduli adattivi con i processi AEM Forms su JEE per l'elaborazione dei dati dei moduli.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18

---


# Configurazione di AEM Forms per l&#39;invio dei dati del modulo a un processo AEM Forms su JEE {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

I moduli adattivi supportano l&#39;invio di dati a un processo AEM Forms on JEE per un&#39;ulteriore elaborazione. Consente di attivare un processo AEM Forms on JEE con i dati disponibili nel modulo inviato. Per abilitare l’istanza di AEM Forms per inviare un modulo adattivo ad AEM Forms su JEE, procedi come segue:

## Configurare il server AEM Forms {#configure-your-aem-forms-server}

Per abilitare il server moduli AEM per l’invio di dati a un server AEM Forms su JEE, procedi come segue:

1. Andate alla console di configurazione Web di AEM all&#39;indirizzo https://[*host*]:[*port*]/system/console/configMgr.

1. Individua e fai clic sul componente Configurazione **SDK client** Adobe LiveCycle.
1. Fate clic per modificare l&#39;URL del server di configurazione, il nome utente e la password per AEM Forms sul server JEE.
1. Esaminate le impostazioni e fate clic su **Salva**.

![Configurazione Adobe LiveCycle Client SDK](assets/clientsdkconfiguration.jpg)

## Mappatura dei dati con i campi di processo {#map-data-with-process-fields}

Una volta configurato AEM Forms, mappate i dati XML e gli allegati del modulo inviato ai campi del processo AEM Forms on JEE. Per effettuare ciò:

1. Nella console di configurazione Web di AEM, fate clic per modificare la configurazione **Guide LiveCycle Process Locator e Invoker** .
1. Specificate i seguenti parametri:

   * **Nome del parametro** data xml (obbligatorio): Specifica il file delle proprietà XML del processo AEM Forms on JEE che deve elaborare i dati inviati. The default value is **dataxml**.
   * **Nome del parametro** degli allegati del file (facoltativo): Specifica l&#39;elenco degli oggetti del documento che il processo AEM Forms on JEE deve elaborare. The default value is **fileAttachmentsList**.

1. Esaminate le impostazioni e fate clic su **Salva**.

![Guida a LiveCycle Process Locator e Invoker](assets/test3.jpg)

Una volta configurata, l&#39;azione Invia a flusso di lavoro moduli elenca i processi del server AEM Forms on JEE contenenti il parametro XML dei dati specificato.
