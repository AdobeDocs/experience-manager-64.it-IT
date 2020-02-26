---
title: Configurare l'assegnazione di tag basati sull'interfaccia utente mediante Smart Content Service
description: Scoprite come configurare i tag avanzati e i tag avanzati in AEM, utilizzando Smart Content Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90d39315207129aa4fc616e6fffb4bad5c450a7b

---


# Configurare i tag delle risorse tramite Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

Scoprite come configurare i tag avanzati e i tag avanzati in AEM, utilizzando Smart Content Service.

Potete integrare Adobe Experience Manager (AEM) con Smart Content Service. Utilizzate questa configurazione per accedere a Smart Content Service dall&#39;interno di AEM e assegnare automaticamente i tag alle immagini.

L&#39;articolo descrive le seguenti attività chiave necessarie per configurare Smart Content Service. Sul lato posteriore, il server AEM autentica le credenziali del servizio con il gateway Adobe IO prima di inoltrare la richiesta a Smart Content Service.

1. Create una configurazione di Smart Content Service in AEM per generare una chiave pubblica. Ottenete un certificato pubblico per l&#39;integrazione OAuth.
1. Create un&#39;integrazione in Adobe I/O e caricate la chiave pubblica generata.
1. Configura l’istanza AEM utilizzando la chiave API e altre credenziali dall’I/O di Adobe.
1. Se necessario, abilitate l’assegnazione automatica di tag al caricamento delle risorse.

## Prerequisiti {#prerequisites}

Prima di poter utilizzare Smart Content Service, accertatevi quanto segue per creare un&#39;integrazione su Adobe I/O:

* Un account Adobe ID con privilegi di amministratore per l’organizzazione.
* Il servizio Smart Content Service è abilitato per la vostra azienda.

Per abilitare i tag avanzati avanzati avanzati, oltre a quanto indicato sopra, installa anche il service pack [](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)AEM più recente.

## Ottenere il certificato pubblico {#obtain-public-certificate}

Un certificato pubblico consente di autenticare il profilo sull&#39;I/O di Adobe.

1. From the AEM user interface, tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. Nella pagina Cloud Services, seleziona **[!UICONTROL Tag avanzati risorse]** e tocca o fai clic su **[!UICONTROL Configura ora]**.
1. Nella finestra di dialogo **[!UICONTROL Crea configurazione]** , specificate un titolo e un nome per la configurazione Smart Tags. Tocca o fai clic su **[!UICONTROL Crea]**.
1. Nella finestra di dialogo **[!UICONTROL AEM Smart Content Service]** , usate i seguenti valori:

   **[!UICONTROL URL servizio]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Server autorizzazioni]**: `https://ims-na1.adobelogin.com`

   Lasciate vuoti gli altri campi per ora (da fornire successivamente). Tap/click **[!UICONTROL OK]**.

   ![Finestra di dialogo di AEM Smart Content Service per fornire l&#39;URL del servizio di contenuto](assets/aem_scs.png)

   >[!NOTE]
   >
   >L&#39;URL fornito come URL  del servizio non è accessibile tramite browser e genera un errore 404. La configurazione funziona correttamente con lo stesso valore del parametro URL  servizio. Per informazioni generali sullo stato del servizio di I/O e sulla pianificazione della manutenzione, consultate [https://status.adobe.com](https://status.adobe.com).

1. Toccate/fate clic su **[!UICONTROL Scarica certificato pubblico per l&#39;integrazione]** OAuth e scaricate il file del certificato pubblico `AEM-SmartTags.crt`.

   ![Una rappresentazione delle impostazioni create per il servizio di smart tag](assets/download_link.png)

## Crea integrazione I/O Adobe {#create-adobe-i-o-integration}

Per utilizzare le API Smart Content Service, create un&#39;integrazione in Adobe I/O per generare la chiave API, l&#39;ID account tecnico, l&#39;ID organizzazione e il Segreto cliente.

1. Accedete a [https://console.adobe.io](https://console.adobe.io/).
1. Dalla pagina **[!UICONTROL Integrazioni]** , seleziona la tua organizzazione.
1. Toccate o fate clic su **[!UICONTROL Nuova integrazione]**.
1. Nella pagina **[!UICONTROL Crea nuova integrazione]** , selezionate **[!UICONTROL Accedi a un&#39;API]**. Tocca o fai clic su **[!UICONTROL Continua]**.
1. In **[!UICONTROL Experience Cloud]**, seleziona **[!UICONTROL Smart Content]**. Tocca o fai clic su **[!UICONTROL Continua]**.

   ![Quando crei una nuova integrazione, seleziona Smart Content in Experience Cloud dalle opzioni disponibili](assets/smart_content.png)

1. Nella pagina successiva, selezionate **[!UICONTROL Nuova integrazione]**. Tocca o fai clic su **[!UICONTROL Continua]**.
1. Nella pagina **[!UICONTROL Dettagli]** integrazione, specificate un nome per il gateway di integrazione e aggiungete una descrizione.
1. Nei certificati delle chiavi **[!UICONTROL pubbliche]**, caricate il `AEM-SmartTags.crt` file scaricato in precedenza.
1. Tap/click **[!UICONTROL Create Integration]**.
1. Per visualizzare le informazioni sull&#39;integrazione, toccate o fate clic su **[!UICONTROL Continua per visualizzare i dettagli]**.

   ![Nella scheda Panoramica è possibile esaminare le informazioni fornite per l&#39;integrazione.](assets/integration_details.png)

## Configurare Smart Content Service {#configure-smart-content-service}

Per configurare l&#39;integrazione, utilizzate i valori dei campi ID account tecnico, ID organizzazione, Segreto cliente, Server autorizzazioni e chiave API dall&#39;integrazione I/O di Adobe. La creazione di una configurazione cloud di Smart Tags consente l’autenticazione delle richieste API dall’istanza AEM.

1. Dall’interfaccia utente di AEM, toccate o fate clic sul logo AEM. Per aprire la console Servizi cloud, passa a **[!UICONTROL Strumenti > Servizi cloud > Servizi]** cloud legacy.
1. In Tag **[!UICONTROL avanzati]** risorse, apri la configurazione creata sopra. Nella pagina delle impostazioni del servizio, fate clic su **[!UICONTROL Modifica]**.
1. Nella finestra di dialogo **[!UICONTROL Servizio di contenuti avanzati AEM]**, utilizza i valori precompilati per i campi **[!UICONTROL URL servizio]** e **[!UICONTROL Server autorizzazioni]**.
1. Per i campi Chiave API, ID account tecnico, ID organizzazione e Segreto client, utilizza i valori generati sopra.

## Convalida della configurazione {#validate-the-configuration}

Dopo aver completato la configurazione, puoi usare un MBean JMX per convalidare la configurazione. Per eseguire la convalida, effettuare le seguenti operazioni.

1. In AEM, per aprire la console OSGi, fate clic su **[!UICONTROL Strumenti > Operazioni > Console]** Web. Fate clic su **[!UICONTROL Principale > JMX]**.
1. Fate clic su **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Si apre **[!UICONTROL SimilaritySearch Attività varie.]**
1. Fare clic su **[!UICONTROL validateConfigs()]**. Nella finestra di dialogo **[!UICONTROL Convalida configurazioni]** , fare clic su **[!UICONTROL Richiama]**.

   Il risultato della convalida viene visualizzato nella stessa finestra di dialogo.

## Abilitare i tag avanzati nel flusso di lavoro Risorse aggiornamento DAM (facoltativo) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Dall’interfaccia utente di AEM, toccate/fate clic sul logo AEM, quindi andate a **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Nella pagina **[!UICONTROL Modelli flusso di lavoro]**, seleziona il modello del flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.
1. Toccate o fate clic su **[!UICONTROL Modifica]** nella barra degli strumenti.
1. Per visualizzare i passaggi, espandi il pannello laterale. Trascina il passaggio **[!UICONTROL Risorsa di tag avanzati]** della sezione Flusso di lavoro DAM e inseriscilo dopo il passaggio **[!UICONTROL Elabora miniature]**.

   ![Aggiungi il passaggio di una risorsa smart tag dopo il passaggio della miniatura del processo nel flusso di lavoro DAM Update Asset](assets/chlimage_1-105.png)

1. Apri il passaggio in modalità di modifica. In **[!UICONTROL Impostazioni avanzate]**, accertati che sia selezionata l’opzione **[!UICONTROL Avanzamento gestore]**.

   ![chlimage_1-106](assets/chlimage_1-106.png)

1. Nella scheda **[!UICONTROL Argomenti]**, seleziona **[!UICONTROL Ignora errori]** se vuoi che il flusso di lavoro venga completato anche con esito negativo del passaggio di assegnazione tag automatica.

   ![chlimage_1-107](assets/chlimage_1-107.png)

   Per assegnare tag alle risorse quando vengono caricate, a prescindere dal fatto che l’assegnazione di tag avanzati sia abilitata o meno nelle cartelle, selezionate **[!UICONTROL Ignora contrassegno]** smart tag.

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. Toccate o fate clic su **[!UICONTROL OK]** per chiudere il passaggio del processo, quindi salvate il flusso di lavoro.

>[!MORELIKETHIS]
>
>* [Comprendere i tag avanzati in Risorse AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-understand.html)
>* [Utilizzo di tag avanzati con AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-use.html)
>* [Utilizzo di tag avanzati avanzati con AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-feature-video-use.html)
>* [Impostazione di smart tag avanzati in AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-technical-video-setup.html)

