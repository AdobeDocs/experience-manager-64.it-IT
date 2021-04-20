---
title: Integrare Adobe Sign con AEM Forms
seo-title: Integrare Adobe Sign con AEM Forms
description: Scopri come configurare Adobe Sign per AEM Forms
seo-description: Scopri come configurare Adobe Sign per AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Adobe Sign
translation-type: tm+mt
source-git-commit: 5944eab0bf38551970685eaa98d90c4459720245
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---


# Integrare Adobe Sign con AEM Forms {#integrate-adobe-sign-with-aem-forms}

Adobe Sign abilita i flussi di lavoro di firma elettronica per i moduli adattivi. Le firme elettroniche migliorano i flussi di lavoro per elaborare documenti per scopi legali, di vendita, di retribuzione, di gestione delle risorse umane e molte altre aree.

In un tipico scenario di Adobe Sign e moduli adattivi, un utente compila un modulo adattivo per **richiedere un servizio**. Ad esempio, un&#39;applicazione con carta di credito e un modulo di benefit per i cittadini. Quando un utente compila, invia e firma il modulo di applicazione, il modulo viene inviato al provider di servizi per ulteriori azioni. Il fornitore di servizi esamina l&#39;applicazione e utilizza Adobe Sign per contrassegnare l&#39;applicazione approvata. Per abilitare flussi di lavoro con firma elettronica simili, è possibile integrare Adobe Sign con AEM Forms.

Per utilizzare Adobe Sign con AEM Forms, configura Adobe Sign in AEM Cloud Services:

## Prerequisiti {#prerequisites}

Per integrare Adobe Sign con AEM Forms è necessario quanto segue:

* Un account sviluppatore [Adobe Sign attivo.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* Un server AEM Forms [SSL abilitato](/help/sites-administering/ssl-by-default.md).
* Applicazione API Adobe Sign [](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Credenziali (ID client e segreto client) dell’applicazione API Adobe Sign.
* Durante la riconfigurazione, rimuovi la configurazione Adobe Sign esistente sia dalle istanze di authoring che di pubblicazione.
* Utilizza [la chiave di crittografia identica](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) per le istanze di authoring e pubblicazione.

## Configurare Adobe Sign con AEM Forms {#configure-adobe-sign-with-aem-forms}

Dopo aver impostato i prerequisiti, esegui i seguenti passaggi per configurare Adobe Sign con AEM Forms sull’istanza di authoring:

1. Nell&#39;istanza di authoring di AEM Forms, passa a **Strumenti** ![martello](assets/hammer.png) > **Generale** > **Browser di configurazione**.
   * Per ulteriori informazioni, consulta la [documentazione del browser di configurazione](/help/sites-administering/configurations.md) .
1. Nella pagina **[!UICONTROL Browser configurazione]**, tocca **[!UICONTROL Crea]**.
1. Nella finestra di dialogo **[!UICONTROL Crea configurazione]**, specifica un **[!UICONTROL Titolo]** per la configurazione, abilita **[!UICONTROL Configurazioni cloud]** e tocca **[!UICONTROL Crea]**. Crea un contenitore di configurazione per Cloud Services.
1. Passa a **Strumenti** ![martello](assets/hammer.png) > **Cloud Services** > **Adobe Sign** e seleziona il contenitore di configurazione creato nel passaggio precedente.

   >[!NOTE]
   >
   >Puoi eseguire i passaggi 1-4 per creare un nuovo contenitore di configurazione e creare una configurazione Adobe Sign nel contenitore oppure utilizzare la cartella esistente `global` in **Strumenti** ![martello](assets/hammer.png) > **Cloud Services** > **Adobe Sign**. Se crei la configurazione nel nuovo contenitore di configurazione, assicurati di specificare il nome del contenitore nel campo **[!UICONTROL Contenitore di configurazione]** quando crei un modulo adattivo.

   >[!NOTE]
   Assicurati che l&#39;URL della pagina di configurazione dei servizi cloud inizi con **HTTPS**. In caso contrario, [abilita SSL](/help/sites-administering/ssl-by-default.md) per il server AEM Forms.

1. Nella pagina di configurazione, tocca **[!UICONTROL Crea]** per creare la configurazione Adobe Sign in AEM Forms.
1. Nella scheda **[!UICONTROL Generale]** della pagina **[!UICONTROL Crea configurazione Adobe Sign]** , specifica un **Nome** per la configurazione e tocca **Avanti**. Facoltativamente, puoi specificare un titolo e cercare per selezionare una miniatura per la configurazione.

1. Copia l&#39;URL nella finestra del browser corrente su un blocco note. È necessario per configurare l’applicazione Adobe Sign con AEM Forms.

1. Configura le impostazioni OAuth per l’applicazione Adobe Sign:

   1. Apri una finestra del browser e accedi all’account sviluppatore Adobe Sign.
   1. Seleziona l’applicazione configurata per AEM Forms e tocca Configura OAuth per l’applicazione.
   1. Nella casella **URL di reindirizzamento** , aggiungi l’URL HTTPS copiato nel passaggio precedente e fai clic su **Salva**.
   1. Abilita le seguenti impostazioni OAuth per l’applicazione Adobe Sign e fai clic su **Salva**.
   * aggrement_read
   * aggeggio_scrittura
   * annuncio_invio
   * widget_write
   * workflow_read

   Per informazioni dettagliate su come configurare le impostazioni OAuth per un’applicazione Adobe Sign e ottenere le chiavi, consulta [Configurare le impostazioni oAuth per la documentazione per gli sviluppatori dell’applicazione](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md).

   ![Configurazione OAuth](assets/oauthconfig_new.png)

1. Torna alla pagina **Crea configurazione Adobe Sign** . Nella scheda **[!UICONTROL Impostazioni]** , il campo **[!UICONTROL URL OAuth]** cita il seguente URL predefinito:

   `https://secure.na1.echosign.com/public/oauth`

   dove:

   **na1** fa riferimento alla condivisione di database predefinita.

   È possibile modificare il valore della condivisione del database. Riavvia il server per poter utilizzare il nuovo valore per la condivisione del database.

1. Specifica l&#39; **ID client** (noto anche come ID applicazione) e il **Segreto client**. Selezionare l&#39;opzione **Abilita Adobe Sign per gli allegati anche** per aggiungere i file allegati a un modulo adattivo al documento Adobe Sign corrispondente inviato per la firma.

   Tocca **[!UICONTROL Connetti ad Adobe Sign]**. Quando viene richiesto di specificare le credenziali, specificare il nome utente e la password dell’account utilizzato durante la creazione dell’applicazione Adobe Sign.

   Tocca **[!UICONTROL Crea]** per creare la configurazione di Adobe Sign.

1. Apri AEM console Web. L&#39;URL è `https://'[server]:[port]'/system/console/configMgr`
1. Apri **Servizio di configurazione comune Forms.**
1. Nel campo **Consenti**, **seleziona** Tutti gli utenti - Tutti gli utenti, anonimi o connessi, possono visualizzare in anteprima gli allegati, verificare e firmare i moduli e fare clic su **Salva.** L’istanza di authoring è configurata per l’utilizzo di Adobe Sign.
1. Utilizza [replica](/help/sites-deploying/replication.md) per creare una configurazione identica sulle istanze di pubblicazione corrispondenti.

Ora Adobe Sign è integrato con AEM Forms ed è pronto per l’uso nei moduli adattivi. Per [utilizzare il servizio Adobe Sign in un modulo adattivo](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), specifica il contenitore di configurazione creato sopra nelle proprietà del modulo adattivo.

## Configura la pianificazione Adobe Sign per sincronizzare lo stato della firma {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Un modulo adattivo abilitato per Adobe Sign viene inviato solo dopo che tutti i firmatari hanno completato il processo di firma. Per impostazione predefinita, i servizi di pianificazione di Adobe Sign sono programmati per controllare (controllare) la risposta del firmatario dopo ogni 24 ore. È possibile modificare l’intervallo predefinito per l’ambiente. Esegui i seguenti passaggi per modificare l’intervallo predefinito:

1. Accedi al server AEM Forms con credenziali di amministratore e passa a **Strumenti** > **Operazioni** > **Console web**.

   Puoi anche aprire il seguente URL in una finestra del browser:
   `https://[localhost]:'port'/system/console/configMgr`

1. Individua e apri l&#39;opzione **Servizio di configurazione Adobe Sign** . Specifica un&#39;espressione [cron](https://en.wikipedia.org/wiki/Cron#CRON_expression) nel campo **Espressione pianificazione aggiornamento stato** e fai clic su **Salva**. Ad esempio, per eseguire il servizio di configurazione ogni giorno alle 00:00, specifica `0 0 0 1/1 * ? *` nel campo **Espressione pianificazione aggiornamento stato** .

L’intervallo predefinito per la sincronizzazione dello stato di Adobe Sign è ora modificato.

## Articoli correlati {#related-articles}

* [Utilizzo di Adobe Sign in un modulo adattivo](../../forms/using/working-with-adobe-sign.md)
* [Utilizzo di Adobe Sign con AEM Forms (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Integrare Adobe Sign con AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
