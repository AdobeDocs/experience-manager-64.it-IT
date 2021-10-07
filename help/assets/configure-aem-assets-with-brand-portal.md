---
title: Configurare AEM Assets con Brand Portal
description: 'Scopri come configurare AEM Assets con Brand Portal per la pubblicazione di risorse e raccolte su Brand Portal. '
contentOwner: VG
feature: Brand Portal
role: Admin
exl-id: cde35555-259f-4d16-999f-2b93d597b8a5
source-git-commit: 8910716cf6b5c4e872db8d965200787de7c2d121
workflow-type: tm+mt
source-wordcount: '1646'
ht-degree: 41%

---

# Configurare AEM Assets con Brand Portal {#configure-integration-64}

Adobe Experience Manager Assets è configurato con Brand Portal tramite [!DNL Adobe I/O], che fornisce un token IMS per l’autorizzazione del tenant Brand Portal.

>[!NOTE]
>
>La configurazione di AEM Assets con Brand Portal tramite [!DNL Adobe I/O] è supportata in AEM 6.4.8.0 e versioni successive.
>
>In precedenza, Brand Portal era configurato nell’interfaccia classica tramite la versione precedente del gateway OAuth, che utilizza lo scambio di token JWT per ottenere un token di accesso IMS per l’autorizzazione.

>[!TIP]
>
>***Solo per i clienti esistenti***
>
>Si consiglia di continuare a utilizzare la configurazione del gateway OAuth esistente. Nel caso in cui si verifichino problemi con la configurazione del gateway OAuth legacy, elimina la configurazione esistente e crea una nuova configurazione tramite [!DNL Adobe I/O].

Questa guida descrive i due casi d’uso seguenti:

* [Nuova configurazione](#configure-new-integration-64): Se sei un nuovo utente Brand Portal e desideri configurare la tua istanza di authoring AEM Assets con Brand Portal, puoi creare una nuova configurazione in  [!DNL Adobe I/O].
* [Aggiorna la configurazione](#upgrade-integration-64): Se sei un utente Brand Portal esistente con la tua istanza di authoring AEM Assets configurata con Brand Portal sul gateway OAuth legacy, ti consigliamo di eliminare le configurazioni esistenti e crearne di nuove su  [!DNL Adobe I/O].

Le informazioni fornite si basano sul presupposto che chiunque legga questa Guida abbia familiarità con le seguenti tecnologie:

* Installazione, configurazione e amministrazione dei pacchetti Adobe Experience Manager e AEM

* Utilizzo dei sistemi operativi Windows Linux e Microsoft

## Prerequisiti {#prerequisites}

Per configurare AEM Assets con Brand Portal, è necessario quanto segue:

* Un’istanza di authoring AEM Assets in esecuzione con Service Pack più recente.
* URL del tenant di Brand Portal.
* Un utente con privilegi di amministratore di sistema nell’organizzazione IMS del tenant di Brand Portal.

[Scarica e installa AEM 6.4](#aemquickstart)

[Scarica e installa l&#39;ultimo Service Pack AEM](#servicepack)

### Scarica e installa AEM 6.4 {#aemquickstart}

Si consiglia di avere AEM 6.4 per impostare un&#39;istanza di authoring AEM. Se non hai AEM in esecuzione, scaricalo dalle seguenti posizioni:

* Se sei un cliente AEM esistente, scarica AEM 6.4 dal [sito web Adobe Licensing](http://licensing.adobe.com).

* Se sei un partner di Adobe, utilizza [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) per richiedere AEM 6.4.

Dopo aver scaricato AEM, per istruzioni su come impostare un&#39;istanza AEM dell&#39;autore, consulta [distribuzione e manutenzione](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html#defaultlocalinstall).

### Scarica e installa AEM Service Pack più recente {#servicepack}

Per istruzioni dettagliate, vedi

* [Note sulla versione di AEM 6.4 Service Pack](https://helpx.adobe.com/it/experience-manager/6-4/release-notes/sp-release-notes.html)

**Se non riesci a trovare l&#39;ultimo pacchetto AEM o Service Pack, contatta l&#39;** Assistenza clienti.

## Creare la configurazione {#configure-new-integration-64}

Esegui i seguenti passaggi nella sequenza elencata se stai configurando AEM Assets con Brand Portal per la prima volta:

1. [Recuperare il certificato pubblico](#public-certificate)
1. [ [!DNL Adobe I/O] Integrazione creativa](#createnewintegration)
1. [Creare la configurazione dell’account IMS](#create-ims-account-configuration)
1. [Configurare il servizio cloud](#configure-the-cloud-service)
1. [Verificare la configurazione](#test-integration)

>[!NOTE]
>
>Un’istanza di authoring di AEM Assets può essere configurata con un solo tenant Brand Portal.

### Creare la configurazione IMS {#create-ims-configuration}

La configurazione IMS autentica il tenant di Brand Portal con l’istanza di authoring di AEM Assets.

La configurazione IMS prevede due passaggi:

* [Recuperare il certificato pubblico](#public-certificate)
* [Creare la configurazione dell’account IMS](#create-ims-account-configuration)

### Recuperare il certificato pubblico {#public-certificate}

Il certificato pubblico ti consente di autenticare il profilo su [!DNL Adobe I/O].

1. Accedi alla tua istanza di authoring di AEM Assets
URL predefinito: http:// localhost:4502/aem/start.html
1. Dal pannello **Strumenti** ![Strumenti](assets/tools.png), passa a **[!UICONTROL Protezione]** >> **[!UICONTROL Configurazioni Adobe IMS]**.

   ![Interfaccia utente di configurazione dell’account Adobe IMS](assets/ims-config1.png)

1. Viene visualizzata la pagina Configurazioni Adobe IMS.

   Fai clic su **[!UICONTROL Crea]**.

   Viene visualizzata la pagina **[!UICONTROL Configurazione account tecnico Adobe IMS]**.

1. Per impostazione predefinita, viene aperta la scheda **Certificato**.

   In **Soluzione cloud**, seleziona **[!UICONTROL Adobe Brand Portal]**.

1. Seleziona la casella di controllo **[!UICONTROL Crea nuovo certificato]** e specifica un **alias** per il certificato. L’alias funge da nome della finestra di dialogo.

1. Fai clic su **[!UICONTROL Crea certificato]**. Viene visualizzata una finestra di dialogo. Fai clic su **[!UICONTROL OK]** per generare il certificato pubblico.

   ![Crea certificato](assets/ims-config2.png)

1. Fai clic su **[!UICONTROL Scarica chiave pubblica]** e salva il file di certificato *AEM-Adobe-IMS.crt* sul computer. Il file del certificato viene utilizzato per [creare [!DNL Adobe I/O] integrazione](#createnewintegration).

   ![Scarica certificato](assets/ims-config3.png)

1. Fai clic su **[!UICONTROL Avanti]**.

   Nella scheda **Account**, puoi creare l’account Adobe IMS, ma dovrai disporre dei dettagli di integrazione. Per il momento tieni aperta questa pagina.

   Apri una nuova scheda e [Crea [!DNL Adobe I/O] integrazione](#createnewintegration) per ottenere i dettagli di integrazione per le configurazioni dell’account IMS.

### Creare l&#39;integrazione [!DNL Adobe I/O] {#createnewintegration}

[!DNL Adobe I/O]L’integrazione di genera i valori di Chiave API, Segreto client e Payload (JWT), necessari per definire le configurazioni dell’account IMS.

1. Accedi alla console [!DNL Adobe I/O] con privilegi di amministratore di sistema nell’organizzazione IMS del tenant Brand Portal.

   URL predefinito: [https://console.adobe.io/](https://console.adobe.io/)

1. Fai clic su **[!UICONTROL Create Integration]** (Crea integrazione).

1. Seleziona **[!UICONTROL Access an API]** (Accesso a un’API) e fai clic su **[!UICONTROL Continue]** (Continua).

   ![Creare una nuova integrazione](assets/create-new-integration1.png)

1. Viene visualizzata la pagina Create a new integration (Crea una nuova integrazione).

   Seleziona la tua organizzazione dall’elenco a discesa.

   In **[!UICONTROL Experience Cloud]**, seleziona **[!UICONTROL AEM Brand Portal]** e fai clic su **[!UICONTROL Continue]** (Continua).

   Se l’opzione Brand Portal è disabilitata, assicurati di aver selezionato l’organizzazione corretta dalla casella a discesa sopra l’opzione **[!UICONTROL Adobe Services]**. Se non sai qual è la tua organizzazione, contatta l’amministratore.

   ![Creare un’integrazione](assets/create-new-integration2.png)

1. Specifica un nome e una descrizione per l’integrazione. Fai clic su **[!UICONTROL Seleziona un file dal computer]** e carica il file `AEM-Adobe-IMS.crt` scaricato nella sezione [Recupero del certificato pubblico](#public-certificate).

1. Seleziona il profilo della tua organizzazione.

   In alternativa, seleziona il profilo predefinito **[!UICONTROL Assets Brand Portal]** e fai clic su **[!UICONTROL Create Integration]** (Crea integrazione). L’integrazione viene creata.

1. Fai clic su **[!UICONTROL Continue to integration details]** (Passa ai dettagli dell’integrazione) per visualizzare le informazioni sull’integrazione.

   Copia il valore di **[!UICONTROL API Key]** (Chiave API).

   Fai clic su **[!UICONTROL Retrieve Client Secret]** (Recupera segreto client) e copia la chiave del segreto client.

   ![Informazioni su chiave API, segreto client e payload di un’integrazione](assets/create-new-integration3.png)

1. Passa alla scheda **[!UICONTROL JWT]** e copia il valore del **[!UICONTROL payload JWT]**.

   Le informazioni relative alla chiave API, al segreto client e al payload JWT verranno utilizzate per creare la configurazione dell’account IMS.

### Creare la configurazione dell’account IMS {#create-ims-account-configuration}

Verifica di aver eseguito i seguenti passaggi:

* [Recuperare il certificato pubblico](#public-certificate)
* [Creare l’integrazione [!DNL Adobe I/O] ](#createnewintegration)

**Procedura per creare la configurazione dell’account IMS:**

1. Apri la scheda **[!UICONTROL Account]** nella pagina Configurazione IMS. Hai tenuto aperta questa pagina alla fine della sezione [Recuperare il certificato pubblico](#public-certificate).

1. Specifica un **[!UICONTROL titolo]** per l’account IMS.

   In **[!UICONTROL Server autorizzazioni]**, immetti l’URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Incolla la chiave API, il segreto client e il payload JWT che hai copiato al termine di [Crea [!DNL Adobe I/O] integrazione](#createnewintegration).

   Fai clic su **[!UICONTROL Crea]**.

   L’integrazione viene creata.

   ![Configurazione dell’account IMS](assets/create-new-integration6.png)

1. Seleziona la configurazione IMS e fai clic su **[!UICONTROL Verifica stato]**. Viene visualizzata una finestra di dialogo.

   Fai clic su **[!UICONTROL Verifica]**. Una volta stabilita la connessione, viene visualizzato il messaggio *Token recuperato correttamente*.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Puoi disporre di una sola configurazione IMS. Non creare più configurazioni IMS.
>
>Verifica che la configurazione IMS superi il controllo di integrità. Se la configurazione non supera questa verifica, non è valida. Dovrai quindi eliminarla e creare una nuova configurazione valida.

### Configurare il servizio cloud {#configure-the-cloud-service}

Per creare la configurazione del servizio cloud di Brand Portal, effettua le seguenti operazioni:

1. Accedi alla tua istanza di authoring di AEM Assets

   URL predefinito: http:// localhost:4502/aem/start.html
1. Dal pannello **Strumenti** ![Strumenti](assets/tools.png), passa a **[!UICONTROL Cloud Services >> AEM Brand Portal]**.

   Viene aperta la pagina Configurazioni di Brand Portal.

1. Fai clic su **[!UICONTROL Crea]**.

1. Specifica un **[!UICONTROL titolo]** per la configurazione.

   Seleziona la configurazione IMS creata nel passaggio [Creare la configurazione dell’account IMS](#create-ims-account-configuration).

   In **[!UICONTROL URL servizio]**, immetti l’URL del tenant di Brand Portal.

   ![](assets/create-cloud-service.png)

1. Fai clic su **[!UICONTROL Salva e chiudi]**. Viene creata la configurazione cloud. L’istanza di authoring di AEM Assets è ora integrata con il tenant Brand Portal.

### Verificare la configurazione {#test-integration}

1. Accedi alla tua istanza di authoring di AEM Assets

   URL predefinito: http:// localhost:4502/aem/start.html

1. Dal pannello **Strumenti** ![Strumenti](assets/tools.png), passa a **[!UICONTROL Implementazione >> Replica]**.

   ![](assets/test-integration1.png)

1. Viene visualizzata la pagina Replica.

   Fai clic su **[!UICONTROL Agenti sull&#39;autore]**.

   ![](assets/test-integration2.png)

1. Per ogni tenant vengono creati quattro agenti di replica.

   Individua gli agenti di replica del tenant Brand Portal.

   Fai clic sull’URL dell’agente di replica.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >Gli agenti di replica lavorano in parallelo e condividono la distribuzione del lavoro in modo uniforme, aumentando così la velocità di pubblicazione di quattro volte la velocità originale. Una volta configurato il servizio cloud, non è necessaria alcuna configurazione aggiuntiva per abilitare gli agenti di replica attivati per impostazione predefinita per abilitare la pubblicazione parallela di più risorse.

1. Per verificare la connessione tra l&#39;autore di AEM Assets e Brand Portal, fai clic su **[!UICONTROL Prova connessione]**.

   ![](assets/test-integration4.png)

1. Osserva la parte inferiore dei risultati del test per verificare che la replica sia riuscita.

   ![](assets/test-integration5.png)


1. Verifica i risultati del test su tutti e quattro gli agenti di replica uno per uno.

   >[!NOTE]
   >
   >Evita di disabilitare uno qualsiasi degli agenti di replica, in quanto può causare errori di replica di alcune delle risorse.
   >
   >Assicurati che tutti e quattro gli agenti di replica siano configurati per evitare errori di timeout. Consulta [risoluzione dei problemi relativi alla pubblicazione parallela in Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html#connection-timeout).

Brand Portal è stato configurato correttamente con l’istanza di authoring di AEM Assets. Ora puoi:

* [Pubblicare risorse da AEM Assets su Brand Portal](../assets/brand-portal-publish-assets.md)
* [Pubblicare cartelle da AEM Assets su Brand Portal](../assets/brand-portal-publish-folder.md)
* [Pubblicare raccolte da AEM Assets su Brand Portal](../assets/brand-portal-publish-collection.md)
* [Configura la ](https://docs.adobe.com/content/help/it/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) sorgente delle risorse per consentire agli utenti di Brand Portal di contribuire e pubblicare risorse in AEM Assets.

## Configurazione dell&#39;aggiornamento {#upgrade-integration-64}

Esegui i seguenti passaggi nella sequenza elencata per aggiornare le configurazioni esistenti:
1. [Verificare i processi in esecuzione](#verify-jobs)
1. [Elimina configurazioni esistenti](#delete-existing-configuration)
1. [Creare la configurazione](#configure-new-integration-64)

### Verificare i processi in esecuzione {#verify-jobs}

Assicurati che nessun processo di pubblicazione sia in esecuzione nell’istanza di authoring di AEM Assets prima di apportare eventuali modifiche. Per questo, puoi verificare tutti e quattro gli agenti di replica e verificare che la coda sia ideale/vuota.

1. Accedi alla tua istanza di authoring di AEM Assets

   URL predefinito: http:// localhost:4502/aem/start.html

1. Dal pannello **Strumenti** ![Strumenti](assets/tools.png), passa a **[!UICONTROL Implementazione >> Replica]**.

1. Viene visualizzata la pagina Replica.

   Fai clic su **[!UICONTROL Agenti sull&#39;autore]**.

   ![](assets/test-integration2.png)

1. Individua gli agenti di replica del tenant Brand Portal.

   Assicurati che la **coda sia inattiva** per tutti gli agenti di replica, nessun processo di pubblicazione è attivo.

   ![](assets/test-integration3.png)

### Elimina configurazioni esistenti {#delete-existing-configuration}

È necessario eseguire il seguente elenco di controllo durante l&#39;eliminazione della configurazione esistente.
* Elimina tutti e quattro gli agenti di replica
* Elimina servizio cloud
* Elimina utente MAC

Esegui i seguenti passaggi per eliminare la configurazione esistente:

1. Accedi alla tua istanza di authoring di AEM Assets e apri CRX Lite come amministratore.

   URL predefinito: http:// localhost:4502/crx/de/index.jsp

1. Passa a `/etc/replications/agents.author` ed elimina tutti e quattro gli agenti di replica del tenant Brand Portal.

   ![](assets/delete-replication-agent.png)

1. Passa a `/etc/cloudservices/mediaportal` ed elimina la **configurazione del Cloud Service**.

   ![](assets/delete-cloud-service.png)

1. Passa a `/home/users/mac` ed elimina l’ **utente MAC** del tenant Brand Portal.

   ![](assets/delete-mac-user.png)


Ora è possibile [creare la configurazione](#configure-new-integration-64) sull&#39;istanza di authoring AEM 6.4 su [!DNL Adobe I/O].



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

Una volta completata la replica, puoi pubblicare risorse, cartelle e raccolte in Brand Portal. Per ulteriori informazioni, consulta:

* [Pubblicare risorse su Brand Portal](brand-portal-publish-assets.md)
* [Pubblicare risorse e cartelle su Brand Portal](brand-portal-publish-folder.md)
* [Pubblicare raccolte su Brand Portal](brand-portal-publish-collection.md)
