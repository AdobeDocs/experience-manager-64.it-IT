---
title: Configurazione di Microsoft Dynamics OData
seo-title: Configurazione Microsoft Dynamics OData
description: Sfruttare, integrare e utilizzare i servizi Microsoft Dynamics online e in sede tramite il modello dati del modulo.
seo-description: Scoprite come sfruttare l'integrazione e l'utilizzo con i servizi Microsoft Dynamics online e locali tramite il modello dati del modulo.
uuid: c9b2764f-9127-4a99-a469-b6ebcdee8fdf
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 62f9d1de-c397-46b5-964e-19777ddd130c
translation-type: tm+mt
source-git-commit: 7e58d1d861f832d073fb178868804995ee8d855b

---


# Configurazione di Microsoft Dynamics OData {#microsoft-dynamics-odata-configuration}

Sfruttare, integrare e utilizzare i servizi Microsoft Dynamics online e in sede tramite il modello dati del modulo.

![integrazione dei dati](assets/data-integeration.png)

Microsoft Dynamics è un software CRM (Customer Relationship Management) e ERP (Enterprise Resource Planning) che fornisce soluzioni aziendali per la creazione e la gestione di account cliente, contatti, lead, opportunità e casi. [L&#39;integrazione](/help/forms/using/data-integration.md) dei dati di AEM Forms fornisce una configurazione del servizio cloud OData per integrare Forms con il server Microsoft Dynamics online e locale. Consente di creare un modello dati modulo basato su entità, attributi e servizi definiti nel servizio Microsoft Dynamics. Il modello dati del modulo può essere utilizzato per creare moduli adattivi che interagiscono con il server Microsoft Dynamics per abilitare i flussi di lavoro aziendali. Ad esempio:

* Query del server Microsoft Dynamics per dati e precompilazione di moduli adattivi
* Inserimento di dati in Microsoft Dynamics per l&#39;invio di moduli adattivi
* Scrittura di dati in Microsoft Dynamics tramite entità personalizzate definite nel modello dati del modulo e viceversa

Il pacchetto del componente aggiuntivo AEM Forms include anche la configurazione di riferimento OData che puoi sfruttare per integrare rapidamente Microsoft Dynamics con AEM Forms.

Quando il pacchetto è installato, nell’istanza di AEM Forms sono disponibili le seguenti entità e servizi:

* Servizio cloud MS Dynamics OData (servizio OData)
* Modello dati modulo con entità e servizi Microsoft Dynamics preconfigurati.

Il servizio OData Cloud e il modello di dati del modulo con entità e servizi Microsoft Dynamics preconfigurati sono disponibili nell&#39;istanza di AEM Forms solo se la modalità di esecuzione dell&#39;istanza di AEM è impostata come `samplecontent`(impostazione predefinita). Per ulteriori informazioni sulla configurazione delle modalità di esecuzione per un’istanza di AEM, consultate Modalità di [esecuzione](https://helpx.adobe.com/in/experience-manager/6-4/sites-deploying/configure-runmodes.html).

## Prerequisiti {#prerequisites}

Prima di iniziare a configurare Microsoft Dynamics, accertati di disporre di:

* Installazione del pacchetto del componente aggiuntivo [AEM 6.4 Forms](https://helpx.adobe.com//experience-manager/6-4/forms/using/installing-configuring-aem-forms-osgi.html)
* Microsoft Dynamics 365 configurato online o installato un&#39;istanza di una delle seguenti versioni di Microsoft Dynamics:

   * Microsoft Dynamics 365 in loco
   * Microsoft Dynamics 2016 in locale

* [È stata registrata l&#39;applicazione per il servizio online Microsoft Dynamics con Microsoft Azure Active Directory](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Prendete nota dei valori per l&#39;ID client (altrimenti denominato ID applicazione) e il segreto client per il servizio registrato. Questi valori vengono utilizzati durante la [configurazione del servizio cloud per il servizio](/help/forms/using/ms-dynamics-odata-configuration.md#configure-cloud-service-for-your-microsoft-dynamics-service)Microsoft Dynamics.

## Imposta URL risposta per l&#39;applicazione Microsoft Dynamics registrata {#set-reply-url-for-registered-microsoft-dynamics-application}

Per impostare l&#39;URL di risposta per l&#39;applicazione Microsoft Dynamics registrata, effettuate le seguenti operazioni:

>[!NOTE]
>
>Utilizzare questa procedura solo durante l&#39;integrazione di AEM Forms con il server Microsoft Dynamics online.

1. Accedete all&#39;account Microsoft Azure Active Directory e aggiungete il seguente URL di configurazione del servizio cloud nelle impostazioni **[!UICONTROL URL]** risposta per l&#39;applicazione registrata:

   `https://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![azure_directory](assets/azure_directory.png)

1. Salvate la configurazione.

## Configurare Microsoft Dynamics per IFD {#configure-microsoft-dynamics-for-ifd}

Microsoft Dynamics utilizza l&#39;autenticazione basata sulle attestazioni per fornire l&#39;accesso ai dati del server Microsoft Dynamics CRM agli utenti esterni. Per abilitare questa opzione, effettuate le seguenti operazioni per configurare Microsoft Dynamics per la distribuzione Internet (IFD) e configurare le impostazioni delle attestazioni.

>[!NOTE]
>
>Utilizzare questa procedura solo durante l&#39;integrazione di AEM Forms con il server Microsoft Dynamics locale.

1. Configurare l&#39;istanza locale di Microsoft Dynamics per IFD come descritto in [Configurare IFD per Microsoft Dynamics](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Eseguite i comandi seguenti utilizzando Windows PowerShell per configurare le impostazioni delle attestazioni su Microsoft Dynamics abilitato per IFD:

   ```
   Add-PSSnapin Microsoft.Crm.PowerShell 
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings 
    $ClaimsSettings.Enabled = $true 
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Per informazioni dettagliate, consultate Registrazione [app per CRM locale (IFD)](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) .

## Configurare il client OAuth sul computer AD FS {#configure-oauth-client-on-ad-fs-machine}

Per registrare un client OAuth nel computer Active Directory Federation Services (AD FS) e concedere l&#39;accesso al computer AD FS, effettuare le seguenti operazioni:

>[!NOTE]
>
>Utilizzare questa procedura solo durante l&#39;integrazione di AEM Forms con il server Microsoft Dynamics locale.

1. Eseguite il comando seguente:

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Dove:

   * `Client-ID` è un ID client che è possibile generare utilizzando qualsiasi generatore GUID.
   * `redirect-uri` è l&#39;URL del servizio cloud Microsoft Dynamics OData su AEM Forms. Il servizio cloud predefinito installato con il pacchetto AEM Forms viene distribuito al seguente URL:

      ```
      http://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
      ```

1. Eseguire il comando seguente per concedere l&#39;accesso al computer AD FS:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   Dove:

   * `resource` è l&#39;URL organizzazione di Microsoft Dynamics.

1. Microsoft Dynamics utilizza il protocollo HTTPS. Per richiamare gli endpoint AD FS dal server Forms, installare il certificato del sito Microsoft Dynamics nell&#39;archivio certificati Java utilizzando il `keytool` comando disponibile nel computer in cui è in esecuzione AEM Forms.

## Configurare il servizio cloud per il servizio Microsoft Dynamics {#configure-cloud-service-for-your-microsoft-dynamics-service}

La configurazione **MS Dynamics OData Cloud Service (OData Service)** viene fornita con la configurazione OData predefinita. Per configurarlo per la connessione al servizio Microsoft Dynamics, effettuare le seguenti operazioni.

1. Passa a **[!UICONTROL Strumenti > Servizi cloud > Origini]** dati e tocca la cartella di `global` configurazione.
1. Selezionare la configurazione del servizio **[!UICONTROL MS Dynamics OData Cloud Service (OData Service)]** e toccare **[!UICONTROL Proprietà]**. Viene visualizzata la finestra di dialogo delle proprietà di configurazione del servizio cloud.

   Nella scheda **[!UICONTROL Impostazioni]** autenticazione:

   1. Immettere il valore per il campo **[!UICONTROL radice]** del servizio. Andate all&#39;istanza Dynamics e andate a Risorse **[!UICONTROL per]** sviluppatori per visualizzare il valore del campo radice del servizio. Ad esempio, https://&lt;nome-tenant>/api/data/v9.1/
   1. Sostituite i valori predefiniti in ID **** client (altrimenti denominati ID **** applicazione), Segreto **** client, URL **** OAuth, URL **[!UICONTROL token di]** aggiornamento, URL ******** token di accesso, URL token di accesso, e campi Resource con i valori della configurazione del servizio Microsoft Dynamics. È obbligatorio specificare l&#39;URL dell&#39;istanza dinamica nel campo **[!UICONTROL Risorse]** per configurare Microsoft Dynamics con un modello dati modulo. Utilizzate l&#39;URL di directory principale del servizio per derivare l&#39;URL dell&#39;istanza di dinamica. Ad esempio, [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).
   1. Specificate **[!UICONTROL open]** nel campo Ambito **** autorizzazione per il processo di autorizzazione in Microsoft Dynamics.
   ![dDynamics_authentication_settings](assets/dynamics_authentication_settings.png)

1. Fate clic su **[!UICONTROL Connetti a OAuth]**. Viene nuovamente visualizzata la pagina di accesso di Microsoft Dynamics.
1. Accedi con le tue credenziali di Microsoft Dynamics e accetta di consentire la configurazione del servizio cloud per connettersi al servizio Microsoft Dynamics. È un&#39;attività una tantum stabilire una connessione tra il servizio cloud e il servizio.

   Viene quindi eseguito il reindirizzamento alla pagina di configurazione del servizio cloud, in cui viene visualizzato un messaggio che informa che la configurazione OData è stata salvata correttamente.

Il servizio cloud MS Dynamics OData Cloud Service (OData Service) è configurato e connesso con il servizio Dynamics.

## Create form data model {#create-form-data-model}

Quando installate il pacchetto AEM Forms, nell’istanza di AEM viene distribuito un modello dati modulo,**Microsoft Dynamics FDM**. Per impostazione predefinita, il modello dati del modulo utilizza il servizio Microsoft Dynamics configurato nel servizio MS Dynamics OData Cloud Service (OData Service) come origine dati.

Quando apre il modello dati del modulo per la prima volta, si connette al servizio Microsoft Dynamics configurato e recupera entità dall&#39;istanza di Microsoft Dynamics. Le entità &quot;contatto&quot; e &quot;lead&quot; di Microsoft Dynamics sono già aggiunte nel modello dati del modulo.

Per esaminare il modello dati del modulo, passare a **[!UICONTROL Forms > Integrazioni]** dati. Selezionare **[!UICONTROL Microsoft Dynamics FDM]** e fare clic su **[!UICONTROL Modifica]** per aprire il modello dati del modulo in modalità di modifica. In alternativa, è possibile aprire il modello dati del modulo direttamente dal seguente URL:

`https://[*server*]:[*port*]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`

![default-fdm-1](assets/default-fdm-1.png)

È quindi possibile creare un modulo adattivo basato sul modello dati del modulo e utilizzarlo in vari casi di utilizzo di moduli adattivi, ad esempio:

* Precompilare il modulo adattivo eseguendo query sulle informazioni di entità e servizi di Microsoft Dynamics
* Richiamo delle operazioni del server Microsoft Dynamics definite in un modello dati modulo utilizzando le regole del modulo adattivo
* Scrittura dei dati del modulo inviati alle entità Microsoft Dynamics

È consigliabile creare una copia del modello dati del modulo fornito con il pacchetto AEM Forms e configurare modelli e servizi dati in base alle proprie esigenze. In questo modo, gli eventuali aggiornamenti futuri al pacchetto non avranno la precedenza sul modello dati del modulo.

Per ulteriori informazioni sulla creazione e l&#39;utilizzo del modello dati del modulo nei flussi di lavoro aziendali, vedere Integrazione [](/help/forms/using/data-integration.md)dei dati.
