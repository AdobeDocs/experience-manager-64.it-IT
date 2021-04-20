---
title: Configura l’assegnazione tag alle risorse utilizzando il Servizio di contenuti avanzati.
description: Scopri come configurare l’assegnazione tag avanzati e l’assegnazione di tag avanzati migliorati in [!DNL Adobe Experience Manager] utilizzando il Servizio di contenuti avanzati.
contentOwner: AG
feature: Smart Tags,Tagging
role: Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 53%

---


# Configurare l’assegnazione tag delle risorse tramite il Servizio di contenuti avanzati {#configure-asset-tagging-using-the-smart-content-service}

Puoi integrare [!DNL Adobe Experience Manager] con il Servizio di contenuti avanzati utilizzando [!DNL Adobe Developer Console]. Utilizza questa configurazione per accedere al Servizio di contenuti avanzati da [!DNL Experience Manager].

L’articolo descrive le seguenti attività chiave necessarie per configurare il Servizio di contenuti avanzati. Nel back-end, il server di [!DNL Experience Manager] autentica le credenziali del servizio con il gateway di prima di inoltrare la richiesta al Servizio di contenuti avanzati.[!DNL Adobe Developer Console]

1. [](#obtain-public-certificate)Crea una configurazione del Servizio di contenuti avanzati in [!DNL Experience Manager] per generare una chiave pubblica. [Ottieni un certificato pubblico](#obtain-public-certificate) per l’integrazione di OAuth.

1. [Crea un’integrazione in Adobe Developer Console](#create-adobe-i-o-integration) e carica la chiave pubblica generata.

1. [Configura la ](#configure-smart-content-service) distribuzione utilizzando la chiave API e altre credenziali di  [!DNL Adobe Developer Console].

1. [Verifica la configurazione](#validate-the-configuration).

1. Facoltativamente, [abilita l&#39;assegnazione tag automatica al caricamento delle risorse](#enable-smart-tagging-in-the-update-asset-workflow-optional).

## Prerequisiti {#prerequisites}

Prima di utilizzare il Servizio di contenuti avanzati, verifica quanto segue per creare un’integrazione su [!DNL Adobe Developer Console]:

* Devi disporre di un account Adobe ID con privilegi di amministratore dell’organizzazione.

* Il Servizio di contenuti avanzati è abilitato per la tua organizzazione.

Per abilitare i tag avanzati migliorati, oltre a quanto indicato sopra, installa anche l’ ultimo [Service Pack di Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=it).

## Creare una configurazione del Servizio di contenuti avanzati per ottenere il certificato pubblico {#obtain-public-certificate}

Un certificato pubblico ti consente di autenticare il profilo su [!DNL Adobe Developer Console].

1. Nell’interfaccia di [!DNL Experience Manager], accedi a **[!UICONTROL Strumenti]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Servizi cloud precedenti]**.

1. Nella pagina Cloud Services, fai clic su **[!UICONTROL Configura ora]** in **[!UICONTROL Tag avanzati risorse]**.

1. Nella finestra di dialogo **[!UICONTROL Crea configurazione]**, specifica un titolo e un nome per la configurazione di tag avanzati. Fai clic su **[!UICONTROL Crea]**.

1. Nella finestra di dialogo **[!UICONTROL Servizio di contenuti avanzati AEM]**, usa i seguenti valori:

   **[!UICONTROL URL servizio]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Server autorizzazioni]**: `https://ims-na1.adobelogin.com`

   Lascia vuoti gli altri campi per il momento (dovranno essere riempiti successivamente). Fai clic su **[!UICONTROL OK]**.

   ![Finestra di dialogo Servizio di contenuti avanzati di Experience Manager per fornire l’URL del servizio di contenuti](assets/aem_scs.png)


   *Figura: Finestra di dialogo Servizio di contenuti avanzati per fornire l’URL del servizio di contenuti*

   >[!NOTE]
   >
   >L&#39;URL fornito come [!UICONTROL URL del servizio] non è accessibile tramite il browser e genera un errore 404. La configurazione funziona correttamente con lo stesso valore del parametro [!UICONTROL URL servizio] . Per informazioni sullo stato generale del servizio e sul programma di manutenzione, consulta [https://status.adobe.com](https://status.adobe.com).

1. Fai clic su **[!UICONTROL Scarica certificato pubblico per integrazione OAuth]** e scarica il file del certificato pubblico `AEM-SmartTags.crt`.

   ![Una rappresentazione delle impostazioni create per il servizio assegnazione tag avanzati](assets/smart-tags-download-public-cert.png)


   *Figura: Impostazioni del servizio di assegnazione tag avanzati*

### Riconfigura quando scade un certificato {#certrenew}

Dopo la scadenza di un certificato, non è più attendibile. Non è possibile rinnovare un certificato scaduto. Per aggiungere un nuovo certificato, effettua le seguenti operazioni.

1. Accedi alla tua implementazione di [!DNL Experience Manager] come amministratore. Fai clic su **[!UICONTROL Strumenti]** > **[!UICONTROL Protezione]** > **[!UICONTROL Utenti]**.

1. Individua e fai clic sull’utente **[!UICONTROL dam-update-service]**. Fare clic sulla scheda **[!UICONTROL Registro chiavi]**.

1. Elimina il registro chiavi esistente **[!UICONTROL similaritysearch]** con il certificato scaduto. Fai clic su **[!UICONTROL Salva e chiudi]**.

   ![Elimina la voce esistente similaritysearch in Registro chiavi per aggiungere un nuovo certificato di sicurezza](assets/smarttags_delete_similaritysearch_keystore.png)

   *Figura: per aggiungere un nuovo certificato di sicurezza, elimina la voce esistente `similaritysearch` in Registro chiavi*

1. Vai a **[!UICONTROL Strumenti]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Servizi cloud precedenti]**. Fai clic su **[!UICONTROL Tag avanzati risorse]** > **[!UICONTROL Mostra configurazioni]** > **[!UICONTROL Configurazioni disponibili]**. Seleziona la configurazione richiesta.

1. Per scaricare un certificato pubblico, fai clic su **[!UICONTROL Scarica certificato pubblico per integrazione OAuth]**.

1. Accedi a [https://console.adobe.io](https://console.adobe.io) e passa ai Servizi di contenuti avanzati esistenti nella pagina **[!UICONTROL Integrazioni]**. Carica il nuovo certificato. Per ulteriori informazioni, consulta le istruzioni in [Creare l’integrazione di Adobe Developer Console](#create-adobe-i-o-integration).

## Creare l’integrazione con Adobe Developer Console {#create-adobe-i-o-integration}

Per utilizzare le API del Servizio di contenuti avanzati, crea un’integrazione in Adobe Developer Console per ottenere [!UICONTROL Chiave API] (generata nel campo [!UICONTROL ID CLIENT] dell’integrazione Adobe Developer Console), [!UICONTROL ID ACCOUNT TECNICO], [!UICONTROL ID ORGANIZZAZIONE] e [!UICONTROL ID ACCOUNT CLIENT SECRET] per [!UICONTROL Assets Smart Tagging Service Settings] della configurazione cloud in [!DNL Experience Manager].

1. Accedi a [https://console.adobe.io](https://console.adobe.io/) in un browser. Seleziona l’account appropriato e verifica che il ruolo aziendale associato sia quello di amministratore di sistema.

1. Crea un progetto con il nome desiderato. Fai clic su **[!UICONTROL Aggiungi API]**.

1. Nella pagina **[!UICONTROL Aggiungi un API]**, seleziona **[!UICONTROL Experience Cloud]**, quindi seleziona **[!UICONTROL Contenuto avanzato]**. Fai clic su **[!UICONTROL Avanti]**.

1. Seleziona **[!UICONTROL Carica la chiave pubblica]**. Fornisci il file del certificato scaricato da [!DNL Experience Manager]. Viene visualizzato il messaggio [!UICONTROL Chiavi pubbliche caricate correttamente]. Fai clic su **[!UICONTROL Avanti]**.

   Nella pagina per la [!UICONTROL creazione di una nuova credenziale dell’account di servizio (JWT)] viene visualizzata la chiave pubblica per l’account di servizio appena configurato.

1. Fai clic su **[!UICONTROL Avanti]**.

1. Nella pagina per la **[!UICONTROL selezione dei profili di prodotto]**, seleziona **[!UICONTROL Servizi di contenuti avanzati]**. Fai clic su **[!UICONTROL Salva API configurata]**.

   In una pagina vengono visualizzate ulteriori informazioni sulla configurazione. Tieni aperta questa pagina per copiare e aggiungere questi valori in [!UICONTROL Impostazioni del servizio di tag avanzati risorse] della configurazione cloud in [!DNL Experience Manager] per configurare tag avanzati.

   ![Nella scheda Panoramica, puoi esaminare le informazioni fornite sull’integrazione.](assets/integration_details.png)

   *Figura: Dettagli dell’integrazione in Adobe Developer Console*

## Configurare il Servizio di contenuti avanzati {#configure-smart-content-service}

Per configurare l’integrazione, utilizza i valori dei campi [!UICONTROL ID ACCOUNT TECNICO], [!UICONTROL ID ORGANIZZAZIONE], [!UICONTROL CLIENT SECRET] e [!UICONTROL ID CLIENT] dall’integrazione di Adobe Developer Console. La creazione di una configurazione cloud di tag avanzati consente l’autenticazione delle richieste API dalla distribuzione [!DNL Experience Manager].

1. In [!DNL Experience Manager], passa a **[!UICONTROL Strumenti > Cloud Service > Servizi cloud precedenti]** per aprire la console [!UICONTROL Cloud Services].

1. In **[!UICONTROL Tag avanzati risorse]**, apri la configurazione creata in precedenza. Nella pagina delle impostazioni del servizio, fai clic su **[!UICONTROL Modifica]**.

1. Nella finestra di dialogo **[!UICONTROL Servizio di contenuti avanzati AEM]**, utilizza i valori precompilati per i campi **[!UICONTROL URL servizio]** e **[!UICONTROL Server autorizzazioni]**.

1. Per i campi [!UICONTROL Chiave API], [!UICONTROL ID account tecnico], [!UICONTROL ID organizzazione] e [!UICONTROL Segreto client], copia e utilizza i seguenti valori generati in [Integrazione Adobe Developer Console](#create-adobe-i-o-integration).

   | [!UICONTROL Impostazioni servizio tag avanzati di Assets] | [!DNL Adobe Developer Console] campi di integrazione |
   |--- |--- |
   | [!UICONTROL Chiave API] | [!UICONTROL ID CLIENT] |
   | [!UICONTROL ID account tecnico] | [!UICONTROL ID ACCOUNT TECNICO] |
   | [!UICONTROL ID organizzazione] | [!UICONTROL ID ORGANIZZAZIONE] |
   | [!UICONTROL Segreto client] | [!UICONTROL SEGRETO CLIENT] |

## Convalidare la configurazione {#validate-the-configuration}

Dopo aver completato la configurazione, utilizza un MBean JMX per convalidare la configurazione. Per eseguire la convalida, effettua le seguenti operazioni.

1. Accedi al server di [!DNL Experience Manager] all’indirizzo `https://[aem_server]:[port]`.

1. Passa a **[!UICONTROL Strumenti > Operazioni > Console Web]** per aprire la console OSGi. Fai clic su **[!UICONTROL Principale > JMX]**.

1. Fai clic su **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Si apre **[!UICONTROL Attività varie SimilaritySearch]**.

1. Fai clic su **[!UICONTROL validateConfigs()]**. Nella finestra di dialogo **[!UICONTROL Validate Configurations]** (Convalida configurazioni), fai clic su **[!UICONTROL Invoke]** (Richiama).

   I risultati della convalida vengono visualizzati nella stessa finestra di dialogo.

## Abilitare l’assegnazione tag avanzati nel flusso di lavoro Risorsa di aggiornamento DAM (facoltativo) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. In [!DNL Experience Manager], vai a **[!UICONTROL Strumenti]** > **[!UICONTROL Flusso di lavoro]** > **[!UICONTROL Modelli]**.

1. Nella pagina **[!UICONTROL Modelli flusso di lavoro]**, seleziona il modello del flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.

1. Fai clic su **[!UICONTROL Modifica]** nella barra degli strumenti.

1. Per visualizzare i passaggi, espandi il pannello laterale. Trascina il passaggio **[!UICONTROL Risorsa di tag avanzati]** della sezione Flusso di lavoro DAM e inseriscilo dopo il passaggio **[!UICONTROL Elabora miniature]**.

   ![Aggiungi il passaggio Risorsa di tag avanzati dopo il passaggio Elabora miniature nel flusso di lavoro Aggiorna risorsa DAM](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Figura: Aggiungi il passaggio Risorsa di tag avanzati dopo il passaggio Elabora miniature nel flusso di lavoro Aggiorna risorsa DAM.*

1. Apri il passaggio in modalità di modifica. In **[!UICONTROL Impostazioni avanzate]**, accertati che sia selezionata l’opzione **[!UICONTROL Avanzamento gestore]**.

   ![Configura il flusso di lavoro Aggiorna risorsa DAM e aggiungi il passaggio tag avanzati](assets/smart-tag-step-properties-workflow1.png)


   *Figura: Configura il flusso di lavoro Aggiorna risorsa DAM e aggiungi il passaggio tag avanzati*

1. Nella scheda **[!UICONTROL Argomenti]**, seleziona **[!UICONTROL Ignora errori]** se vuoi che il flusso di lavoro venga completato anche con esito negativo del passaggio di assegnazione tag automatica.

   ![Configura il flusso di lavoro Aggiorna risorsa DAM per aggiungere il passaggio tag avanzati e selezionare l&#39;avanzamento del gestore](assets/smart-tag-step-properties-workflow2.png)


   *Figura: Configura il flusso di lavoro Aggiorna risorsa DAM per aggiungere il passaggio tag avanzati e selezionare l&#39;avanzamento del gestore*

   Per assegnare i tag alle risorse quando vengono caricate, a prescindere dal fatto che l’assegnazione tag avanzati sia abilitata o meno per le cartelle, seleziona **[!UICONTROL Ignora flag di tag avanzati]**.

   ![Configura il flusso di lavoro Risorsa di aggiornamento DAM per aggiungere il passaggio tag avanzati e selezionare ignora il flag di tag avanzati](assets/smart-tag-step-properties-workflow3.png)


   *Figura: Configura il flusso di lavoro Risorsa di aggiornamento DAM per aggiungere il passaggio tag avanzati e selezionare ignora il flag di tag avanzati*

1. Fai clic su **[!UICONTROL OK]** per chiudere il passaggio del processo, quindi salva il flusso di lavoro.

>[!MORELIKETHIS]
>
>* [Gestire tag avanzati](managing-smart-tags.md)
>* [Panoramica e modalità di formazione dei tag avanzati](enhanced-smart-tags.md)
>* [Linee guida e regole per la formazione del Servizio di contenuti avanzati](smart-tags-training-guidelines.md)

