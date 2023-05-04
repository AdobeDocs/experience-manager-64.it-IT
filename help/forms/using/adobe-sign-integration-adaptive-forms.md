---
title: Integrare Acrobat Sign con AEM Forms
seo-title: Integrate Acrobat Sign with AEM Forms
description: Scopri come configurare Acrobat Sign per AEM Forms
seo-description: Learn how to configure Acrobat Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Acrobat Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# Integrare Acrobat Sign con AEM Forms {#integrate-adobe-sign-with-aem-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Acrobat Sign abilita i flussi di lavoro di firma elettronica per i moduli adattivi. Le firme elettroniche migliorano i flussi di lavoro per elaborare documenti per scopi legali, di vendita, di retribuzione, di gestione delle risorse umane e molte altre aree.

In uno scenario tipico di Acrobat Sign e moduli adattivi, un utente compila un modulo adattivo in **richiedere un servizio**. Ad esempio, un&#39;applicazione con carta di credito e un modulo di benefit per i cittadini. Quando un utente compila, invia e firma il modulo di applicazione, il modulo viene inviato al provider di servizi per ulteriori azioni. Il fornitore di servizi esamina l&#39;applicazione e utilizza Acrobat Sign per contrassegnare l&#39;applicazione approvata. Per abilitare flussi di lavoro con firma elettronica simili, è possibile integrare Acrobat Sign con AEM Forms.

Per utilizzare Acrobat Sign con AEM Forms, configura Acrobat Sign in AEM Cloud Services:

## Prerequisiti {#prerequisites}

Per integrare Acrobat Sign con AEM Forms è necessario quanto segue:

* Attivo [Account sviluppatore Acrobat Sign.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* Un [SSL abilitato](/help/sites-administering/ssl-by-default.md) Server AEM Forms.
* Un [Applicazione API Acrobat Sign](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Credenziali (ID client e segreto client) dell’applicazione API Acrobat Sign.
* Durante la riconfigurazione, rimuovi la configurazione Acrobat Sign esistente sia dalle istanze di authoring che di pubblicazione.
* Utilizzo [chiave crittografica identica](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) per le istanze di authoring e pubblicazione.

## Configurare Acrobat Sign con AEM Forms {#configure-adobe-sign-with-aem-forms}

Dopo aver impostato i prerequisiti, esegui i seguenti passaggi per configurare Acrobat Sign con AEM Forms sull’istanza di authoring:

1. Nell’istanza di authoring di AEM Forms, passa a **Strumenti** ![martello](assets/hammer.png) > **Generale** > **Browser di configurazione**.
   * Consulta la sezione [Documentazione del browser di configurazione](/help/sites-administering/configurations.md) per ulteriori informazioni.
1. Sulla **[!UICONTROL Browser di configurazione]** pagina, tocca **[!UICONTROL Crea]**.
1. In **[!UICONTROL Crea configurazione]** specifica una finestra di dialogo **[!UICONTROL Titolo]** per la configurazione, abilita **[!UICONTROL Configurazioni cloud]**, e tocca **[!UICONTROL Crea]**. Crea un contenitore di configurazione per Cloud Services.
1. Passa a **Strumenti** ![martello](assets/hammer.png) > **Cloud Services** > **Acrobat Sign** e seleziona il contenitore di configurazione creato nel passaggio precedente.

   >[!NOTE]
   >
   >Puoi eseguire i passaggi da 1 a 4 per creare un nuovo contenitore di configurazione e creare una configurazione Acrobat Sign nel contenitore oppure utilizzare la configurazione esistente `global` cartella in **Strumenti** ![martello](assets/hammer.png) > **Cloud Services** > **Acrobat Sign**. Se crei la configurazione nel nuovo contenitore di configurazione, assicurati di specificare il nome del contenitore nel **[!UICONTROL Contenitore di configurazione]** quando si crea un modulo adattivo.

   >[!NOTE]
   Assicurati che l’URL della pagina di configurazione dei servizi cloud inizi con **HTTPS**. In caso contrario, [abilitare SSL](/help/sites-administering/ssl-by-default.md) per il server AEM Forms.

1. Nella pagina di configurazione, tocca **[!UICONTROL Crea]** per creare la configurazione di Acrobat Sign in AEM Forms.
1. In **[!UICONTROL Generale]** della scheda **[!UICONTROL Creare la configurazione di Acrobat Sign]** pagina, specifica un **Nome** per la configurazione e tocca **Successivo**. Facoltativamente, puoi specificare un titolo e cercare per selezionare una miniatura per la configurazione.

1. Copia l&#39;URL nella finestra del browser corrente su un blocco note. È necessario per configurare l’applicazione Acrobat Sign con AEM Forms.

1. Configura le impostazioni OAuth per l’applicazione Acrobat Sign:

   1. Apri una finestra del browser e accedi all’account sviluppatore Acrobat Sign.
   1. Seleziona l’applicazione configurata per AEM Forms e tocca Configura OAuth per l’applicazione.
   1. In **URL di reindirizzamento** aggiungi l’URL HTTPS copiato nel passaggio precedente e fai clic su **Salva**.
   1. Abilita le seguenti impostazioni OAuth per l’applicazione Acrobat Sign e fai clic su **Salva**.
   * aggrement_read
   * aggeggio_scrittura
   * annuncio_invio
   * widget_write
   * workflow_read

   Per informazioni dettagliate su come configurare le impostazioni OAuth per un’applicazione Acrobat Sign e ottenere le chiavi, consulta [Configurare le impostazioni di oAuth per l&#39;applicazione](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) documentazione per gli sviluppatori.

   ![Configurazione OAuth](assets/oauthconfig_new.png)

1. Torna alla pagina **Creare la configurazione di Acrobat Sign** pagina. In **[!UICONTROL Impostazioni]** scheda **[!UICONTROL URL OAuth]** Il campo cita il seguente URL predefinito:

   `https://secure.na1.echosign.com/public/oauth`

   Dove:

   **na1** fa riferimento alla condivisione di database predefinita.

   È possibile modificare il valore della condivisione del database. Riavvia il server per poter utilizzare il nuovo valore per la condivisione del database.

1. Specifica la **ID client** (noto anche come ID applicazione) e **Segreto client**. Seleziona la **Abilita anche Acrobat Sign per gli allegati** opzione per aggiungere file allegati a un modulo adattivo al documento Acrobat Sign corrispondente inviato per la firma.

   Tocca **[!UICONTROL Connettersi ad Acrobat Sign]**. Quando viene richiesto di specificare le credenziali, specificare il nome utente e la password dell’account utilizzato durante la creazione dell’applicazione Acrobat Sign.

   Tocca **[!UICONTROL Crea]** per creare la configurazione di Acrobat Sign.

1. Apri AEM console Web. L’URL è `https://'[server]:[port]'/system/console/configMgr`
1. Apri **Servizio di configurazione comune Forms.**
1. In **Consenti** campo, **select** Tutti gli utenti - Tutti gli utenti, anonimi o connessi, possono visualizzare in anteprima gli allegati, verificare e firmare i moduli e fare clic su **Salva.** L’istanza di authoring è configurata per l’utilizzo di Acrobat Sign.
1. Utilizzo [replica](/help/sites-deploying/replication.md) per creare una configurazione identica sulle istanze di pubblicazione corrispondenti.

Ora Acrobat Sign è integrato con AEM Forms ed è pronto per l’uso nei moduli adattivi. A [utilizzare il servizio Acrobat Sign in un modulo adattivo](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), specifica il contenitore di configurazione creato sopra nelle proprietà del modulo adattivo.

## Configurare Acrobat Sign Scheduler per sincronizzare lo stato della firma {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Un modulo adattivo abilitato per Acrobat Sign viene inviato solo dopo che tutti i firmatari hanno completato il processo di firma. Per impostazione predefinita, i servizi di pianificazione di Acrobat Sign sono programmati per controllare (controllare) la risposta del firmatario dopo ogni 24 ore. È possibile modificare l’intervallo predefinito per l’ambiente. Esegui i seguenti passaggi per modificare l’intervallo predefinito:

1. Accedi al server AEM Forms con le credenziali di amministratore e passa a **Strumenti** > **Operazioni** > **Console web**.

   Puoi anche aprire il seguente URL in una finestra del browser:
   `https://[localhost]:'port'/system/console/configMgr`

1. Individua e apri la **Servizio di configurazione di Acrobat Sign** opzione . Specifica una [espressione cron](https://en.wikipedia.org/wiki/Cron#CRON_expression) in **Espressione di pianificazione dell&#39;aggiornamento dello stato** campo e fai clic su **Salva**. Ad esempio, per eseguire il servizio di configurazione ogni giorno alle 00:00, specifica `0 0 0 1/1 * ? *` in **Espressione di pianificazione dell&#39;aggiornamento dello stato** campo .

L’intervallo predefinito per la sincronizzazione dello stato di Acrobat Sign è ora modificato.

## Articoli correlati {#related-articles}

* [Utilizzo di Acrobat Sign in un modulo adattivo](../../forms/using/working-with-adobe-sign.md)
* [Utilizzo di Acrobat Sign con AEM Forms (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Integrare Acrobat Sign con AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
