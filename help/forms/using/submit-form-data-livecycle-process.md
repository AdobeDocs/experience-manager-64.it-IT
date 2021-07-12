---
title: Configurazione di AEM Forms per l’invio dei dati del modulo a un processo AEM Forms on JEE
seo-title: Configurazione di AEM Forms per l’invio dei dati del modulo a un processo AEM Forms on JEE
description: AEM Forms consente di integrare i moduli adattivi con i processi AEM Forms su JEE per l’elaborazione dei dati dei moduli.
seo-description: AEM Forms consente di integrare i moduli adattivi con i processi AEM Forms su JEE per l’elaborazione dei dati dei moduli.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
role: Admin
exl-id: 260e405e-f59c-4aea-b83f-53ee103df94e
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Configurazione di AEM Forms per l’invio dei dati del modulo a un processo AEM Forms on JEE {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

I moduli adattivi supportano l’invio di dati a un processo AEM Forms su JEE per un’ulteriore elaborazione. Ti consente di attivare un processo AEM Forms su JEE con i dati disponibili dal modulo inviato. Esegui i seguenti passaggi per abilitare l’istanza di AEM Forms all’invio di un modulo adattivo ad AEM Forms sul processo JEE:

## Configurare il server AEM Forms {#configure-your-aem-forms-server}

Per abilitare il server dei moduli di AEM all’invio di dati a un server AEM Forms su JEE, effettua le seguenti operazioni:

1. Vai AEM console di configurazione web all&#39;indirizzo https://[*host*]:[*port*]/system/console/configMgr.

1. Individua e fai clic sul componente **Configurazione SDK client LiveCycle di Adobe** .
1. Fai clic su per modificare l&#39;URL del server di configurazione, il nome utente e la password per AEM Forms sul server JEE.
1. Rivedi le impostazioni e fai clic su **Salva**.

![Configurazione Adobe LiveCycle Client SDK](assets/clientsdkconfiguration.jpg)

## Mappatura di dati con campi di processo {#map-data-with-process-fields}

Una volta configurato il tuo AEM Forms, mappa i dati XML e gli allegati dal modulo inviato ai campi nel processo AEM Forms on JEE. Per effettuare ciò:

1. Nella console di configurazione web AEM, fai clic su per modificare la configurazione **Individuazione processo LiveCycle guida e Invoker** .
1. Specifica i seguenti parametri:

   * **Nome del parametro xml dei dati**  (obbligatorio): Specifica il file di proprietà XML del processo AEM Forms on JEE che deve elaborare i dati inviati. Il valore predefinito è **dataxml**.
   * **Nome del parametro**  file allegati (facoltativo): Specifica l’elenco di oggetti documento che il processo AEM Forms su JEE deve elaborare. Il valore predefinito è **fileAttachmentsList**.

1. Rivedi le impostazioni e fai clic su **Salva**.

![Individuatore del processo del LiveCycle guida e del dispositivo di fatturazione](assets/test3.jpg)

Una volta configurata, l’azione Invia al Forms Workflow elenca i processi server AEM Forms on JEE contenenti il parametro xml dei dati specificato.
