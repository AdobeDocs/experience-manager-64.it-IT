---
title: Configurate i tag delle risorse mediante Smart Content Service.
description: Scoprite come configurare i tag avanzati e i tag avanzati in [!DNL Adobe Experience Manager] utilizzando Smart Content Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 54%

---


# Configurare i tag delle risorse tramite Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

È possibile integrare [!DNL Adobe Experience Manager] con Smart Content Service utilizzando [!DNL Adobe Developer Console]. Utilizzate questa configurazione per accedere a Smart Content Service dall&#39;interno di [!DNL Experience Manager].

L’articolo descrive le seguenti attività chiave necessarie per configurare il Servizio di contenuti avanzati. Nel back-end, il server di [!DNL Experience Manager] autentica le credenziali del servizio con il gateway di prima di inoltrare la richiesta al Servizio di contenuti avanzati.[!DNL Adobe Developer Console]

1. [](#obtain-public-certificate)Crea una configurazione del Servizio di contenuti avanzati in [!DNL Experience Manager] per generare una chiave pubblica. [Ottieni un certificato pubblico](#obtain-public-certificate) per l’integrazione di OAuth.

1. [Crea un’integrazione in Adobe Developer Console](#create-adobe-i-o-integration) e carica la chiave pubblica generata.

1. [Configurate la ](#configure-smart-content-service) distribuzione utilizzando la chiave API e altre credenziali da  [!DNL Adobe Developer Console].

1. [Verifica la configurazione](#validate-the-configuration).

1. Facoltativamente, [abilita l&#39;assegnazione di tag automatica al caricamento delle risorse](#enable-smart-tagging-in-the-update-asset-workflow-optional).

## Prerequisiti {#prerequisites}

Prima di utilizzare Smart Content Service, accertatevi quanto segue per creare un&#39;integrazione su [!DNL Adobe Developer Console]:

* Devi disporre di un account Adobe ID con privilegi di amministratore dell’organizzazione.

* Smart Content Service è abilitato per la vostra organizzazione.

Per abilitare Enhanced Smart Tags, oltre a quanto sopra, installare anche il service pack [ Experience Manager più recente](https://helpx.adobe.com/it/experience-manager/aem-releases-updates.html).

## Creare la configurazione di Smart Content Service per ottenere il certificato pubblico {#obtain-public-certificate}

Un certificato pubblico consente di autenticare il profilo su [!DNL Adobe Developer Console].

1. Nell’interfaccia di [!DNL Experience Manager], accedi a **[!UICONTROL Strumenti]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Servizi cloud precedenti]**.

1. Nella pagina Cloud Services, fare clic su **[!UICONTROL Configura ora]** in **[!UICONTROL Risorse Smart Tags]**.

1. Nella finestra di dialogo **[!UICONTROL Crea configurazione]**, specifica un titolo e un nome per la configurazione di tag avanzati. Fai clic su **[!UICONTROL Crea]**.

1. Nella finestra di dialogo **[!UICONTROL Servizio di contenuti avanzati AEM]**, usa i seguenti valori:

   **[!UICONTROL URL servizio]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Server autorizzazioni]**: `https://ims-na1.adobelogin.com`

   Lascia vuoti gli altri campi per il momento (dovranno essere riempiti successivamente). Fai clic su **[!UICONTROL OK]**.

   ![Finestra di dialogo Servizio di contenuti avanzati di Experience Manager per fornire l’URL del servizio di contenuti](assets/aem_scs.png)


   *Figura: Finestra di dialogo Smart Content Service per fornire l&#39;URL del servizio di contenuto*

   >[!NOTE]
   >
   >L&#39;URL fornito come [!UICONTROL URL servizio] non è accessibile tramite browser e genera un errore 404. La configurazione funziona correttamente con lo stesso valore del parametro [!UICONTROL URL del servizio]. Per informazioni sullo stato generale del servizio e sul programma di manutenzione, vedere [https://status.adobe.com](https://status.adobe.com).

1. Fai clic su **[!UICONTROL Scarica certificato pubblico per integrazione OAuth]** e scarica il file del certificato pubblico `AEM-SmartTags.crt`.

   ![Una rappresentazione delle impostazioni create per il servizio assegnazione tag avanzati](assets/smart-tags-download-public-cert.png)


   *Figura: Impostazioni per il servizio di smart tag*

### Riconfigura alla scadenza del certificato {#certrenew}

Una volta scaduto, il certificato non è più affidabile. Non è possibile rinnovare un certificato scaduto. Per aggiungere un nuovo certificato, effettua le seguenti operazioni.

1. Accedi alla tua implementazione di [!DNL Experience Manager] come amministratore. Fai clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Protezione]** > **[!UICONTROL Utenti]**.

1. Individua e fai clic sull’utente **[!UICONTROL dam-update-service]**. Fare clic sulla scheda **[!UICONTROL Keystore]**.

1. Elimina il registro chiavi esistente **[!UICONTROL similaritysearch]** con il certificato scaduto. Fai clic su **[!UICONTROL Salva e chiudi]**.

   ![Per aggiungere un nuovo certificato di protezione, eliminate la voce di ricerca per similarità esistente in Keystore](assets/smarttags_delete_similaritysearch_keystore.png)

   *Figura: per aggiungere un nuovo certificato di sicurezza, elimina la voce esistente `similaritysearch` in Registro chiavi*

1. Vai a **[!UICONTROL Strumenti]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Servizi cloud precedenti]**. Fai clic su **[!UICONTROL Tag avanzati risorse]** > **[!UICONTROL Mostra configurazioni]** > **[!UICONTROL Configurazioni disponibili]**. Seleziona la configurazione richiesta.

1. Per scaricare un certificato pubblico, fai clic su **[!UICONTROL Scarica certificato pubblico per integrazione OAuth]**.

1. Accedi a [https://console.adobe.io](https://console.adobe.io) e passa ai Servizi di contenuti avanzati esistenti nella pagina **[!UICONTROL Integrazioni]**. Carica il nuovo certificato. Per ulteriori informazioni, consultare le istruzioni riportate in [Creare &#39;integrazione della console per sviluppatori di Adobi](#create-adobe-i-o-integration).

## Crea &#39;integrazione con Developer Console di Adobe {#create-adobe-i-o-integration}

Per utilizzare le API di Smart Content Service, create un&#39;integrazione in  Adobe Developer Console per ottenere [!UICONTROL Chiave API] (generata nel campo [!UICONTROL ID CLIENT] dell&#39;integrazione  Adobe Developer Console), [!UICONTROL ID ACCOUNT TECNICO], [!UICONTROL ID ORGANIZZAZIONE] e [!UICONTROL ID CLIENT SECRET] per [!UICONTROL Assets Smart Tagging Service Settings] della configurazione cloud in [!DNL Experience Manager].

1. Accedi a [https://console.adobe.io](https://console.adobe.io/) in un browser. Seleziona l’account appropriato e verifica che il ruolo aziendale associato sia quello di amministratore di sistema.

1. Crea un progetto con il nome desiderato. Fai clic su **[!UICONTROL Aggiungi API]**.

1. Nella pagina **[!UICONTROL Aggiungi un API]**, selezionare **[!UICONTROL Experience Cloud]**, quindi selezionare **[!UICONTROL Smart Content]**. Fai clic su **[!UICONTROL Avanti]**.

1. Seleziona **[!UICONTROL Carica la chiave pubblica]**. Fornisci il file del certificato scaricato da [!DNL Experience Manager]. Viene visualizzato il messaggio [!UICONTROL Chiavi pubbliche caricate correttamente]. Fai clic su **[!UICONTROL Avanti]**.

   Nella pagina per la [!UICONTROL creazione di una nuova credenziale dell’account di servizio (JWT)] viene visualizzata la chiave pubblica per l’account di servizio appena configurato.

1. Fai clic su **[!UICONTROL Avanti]**.

1. Nella pagina per la **[!UICONTROL selezione dei profili di prodotto]**, seleziona **[!UICONTROL Servizi di contenuti avanzati]**. Fai clic su **[!UICONTROL Salva API configurata]**.

   In una pagina vengono visualizzate ulteriori informazioni sulla configurazione. Tenete aperta questa pagina per copiare e aggiungere questi valori in [!UICONTROL Impostazioni servizio Smart Tagging Assets] della configurazione cloud in [!DNL Experience Manager] per configurare gli smart tag.

   ![Nella scheda Panoramica, puoi esaminare le informazioni fornite sull’integrazione.](assets/integration_details.png)

   *Figura: Dettagli dell&#39;integrazione in  Adobe Developer Console*

## Configurare il Servizio di contenuti avanzati {#configure-smart-content-service}

Per configurare l&#39;integrazione, utilizzate i valori dei campi [!UICONTROL ID ACCOUNT TECNICO], [!UICONTROL ID ORGANIZZAZIONE], [!UICONTROL CLIENT SECRET] e [!UICONTROL ID CLIENT] dall&#39;integrazione  Developer Console. La creazione di una configurazione cloud di Smart Tags consente l&#39;autenticazione delle richieste API dalla distribuzione [!DNL Experience Manager].

1. In [!DNL Experience Manager], passa a **[!UICONTROL Strumenti > Cloud Service > Servizi cloud precedenti]** per aprire la console [!UICONTROL Cloud Services].

1. In **[!UICONTROL Tag avanzati risorse]**, apri la configurazione creata in precedenza. Nella pagina delle impostazioni del servizio, fai clic su **[!UICONTROL Modifica]**.

1. Nella finestra di dialogo **[!UICONTROL Servizio di contenuti avanzati AEM]**, utilizza i valori precompilati per i campi **[!UICONTROL URL servizio]** e **[!UICONTROL Server autorizzazioni]**.

1. Per i campi [!UICONTROL Chiave API], [!UICONTROL ID account tecnico], [!UICONTROL ID organizzazione] e [!UICONTROL Segreto cliente], copiate e utilizzate i seguenti valori generati in [ Integrazione con Developer Console di Adobe](#create-adobe-i-o-integration).

   | [!UICONTROL Impostazioni servizio tag avanzati di Assets] | [!DNL Adobe Developer Console] campi di integrazione |
   |--- |--- |
   | [!UICONTROL Chiave API] | [!UICONTROL ID CLIENT] |
   | [!UICONTROL ID account tecnico] | [!UICONTROL ID ACCOUNT TECNICO] |
   | [!UICONTROL ID organizzazione] | [!UICONTROL ID ORGANIZZAZIONE] |
   | [!UICONTROL Segreto client] | [!UICONTROL SEGRETO CLIENT] |

## Convalidare la configurazione {#validate-the-configuration}

Dopo aver completato la configurazione, utilizzate un MBean JMX per convalidare la configurazione. Per eseguire la convalida, effettua le seguenti operazioni.

1. Accedi al server di [!DNL Experience Manager] all’indirizzo `https://[aem_server]:[port]`.

1. Passa a **[!UICONTROL Strumenti > Operazioni > Console Web]** per aprire la console OSGi. Fai clic su **[!UICONTROL Principale > JMX]**.

1. Fai clic su **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Si apre **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.

1. Fai clic su **[!UICONTROL validateConfigs()]**. Nella finestra di dialogo **[!UICONTROL Validate Configurations]** (Convalida configurazioni), fai clic su **[!UICONTROL Invoke]** (Richiama).

   I risultati della convalida vengono visualizzati nella stessa finestra di dialogo.

## Abilitare i tag avanzati nel flusso di lavoro DAM Update Asset (facoltativo) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. In [!DNL Experience Manager], passare a **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]**.

1. Nella pagina **[!UICONTROL Modelli flusso di lavoro]**, seleziona il modello del flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.

1. Fai clic su **[!UICONTROL Modifica]** nella barra degli strumenti.

1. Per visualizzare i passaggi, espandi il pannello laterale. Trascina il passaggio **[!UICONTROL Risorsa di tag avanzati]** della sezione Flusso di lavoro DAM e inseriscilo dopo il passaggio **[!UICONTROL Elabora miniature]**.

   ![Aggiungi il passaggio Risorsa di tag avanzati dopo il passaggio Elabora miniature nel flusso di lavoro Aggiorna risorsa DAM](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Figura: Aggiungi il passaggio Risorsa di tag avanzati dopo il passaggio Elabora miniature nel flusso di lavoro Aggiorna risorsa DAM.*

1. Apri il passaggio in modalità di modifica. In **[!UICONTROL Impostazioni avanzate]**, accertati che sia selezionata l’opzione **[!UICONTROL Avanzamento gestore]**.

   ![Configurare il flusso di lavoro Aggiorna risorsa DAM e aggiungere il passaggio smart tag](assets/smart-tag-step-properties-workflow1.png)


   *Figura: Configurare il flusso di lavoro Aggiorna risorsa DAM e aggiungere il passaggio smart tag*

1. Nella scheda **[!UICONTROL Argomenti]**, seleziona **[!UICONTROL Ignora errori]** se vuoi che il flusso di lavoro venga completato anche con esito negativo del passaggio di assegnazione tag automatica.

   ![Configurare il flusso di lavoro Aggiorna risorsa DAM per aggiungere il passaggio smart tag e selezionare l&#39;avanzamento del gestore](assets/smart-tag-step-properties-workflow2.png)


   *Figura: Configurare il flusso di lavoro Aggiorna risorsa DAM per aggiungere il passaggio smart tag e selezionare l&#39;avanzamento del gestore*

   Per assegnare i tag alle risorse quando vengono caricate, a prescindere dal fatto che l’assegnazione tag avanzati sia abilitata o meno per le cartelle, seleziona **[!UICONTROL Ignora flag di tag avanzati]**.

   ![Configurare il flusso di lavoro Aggiorna risorsa DAM per aggiungere il passo smart tag e selezionare Ignora flag Smart Tag](assets/smart-tag-step-properties-workflow3.png)


   *Figura: Configurare il flusso di lavoro Aggiorna risorsa DAM per aggiungere il passo smart tag e selezionare Ignora flag Smart Tag*

1. Fai clic su **[!UICONTROL OK]** per chiudere il passaggio del processo, quindi salva il flusso di lavoro.

>[!MORELIKETHIS]
>
>* [Gestire i tag avanzati](managing-smart-tags.md)
>* [Panoramica e come formare i tag avanzati](enhanced-smart-tags.md)
>* [Linee guida e regole per la formazione di Smart Content Service](smart-tags-training-guidelines.md)

