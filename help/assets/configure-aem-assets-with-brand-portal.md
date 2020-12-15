---
title: Configurare AEM Assets con Brand Portal
description: 'Scoprite come configurare  AEM Assets con Brand Portal per la pubblicazione di risorse e raccolte in Brand Portal. '
contentOwner: VG
translation-type: tm+mt
source-git-commit: f86765084981cda1e255834bf83be0ff8a7a2a02
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 46%

---


# Configurare AEM Assets con Brand Portal {#configure-integration-64}

Adobe Experience Manager (AEM) Assets è configurato con Brand Portal tramite Adobe I/O, che fornisce un token IMS per l’autorizzazione del tenant di Brand Portal.

>[!NOTE]
>
>La configurazione  AEM Assets con Portale marchio tramite  Adobe I/O è supportata in AEM 6.4.8.0 e versioni successive.
>
>Precedentemente, Brand Portal era stato configurato nell’interfaccia classica tramite il gateway OAuth legacy, che utilizza lo scambio di token JWT per ottenere un token di accesso IMS per l’autorizzazione.

>[!TIP]
>
>***Solo per i clienti esistenti***
>
>Si consiglia di continuare a utilizzare la configurazione gateway OAuth esistente. Se si verificano problemi con la configurazione del gateway OAuth legacy, eliminare la configurazione esistente e creare una nuova configurazione tramite  Adobe I/O.

Questa guida descrive i due casi d’uso seguenti:

* [Nuova configurazione](#configure-new-integration-64): Se siete un nuovo utente di Brand Portal e desiderate configurare l’istanza di creazione di AEM Assets  con Brand Portal, potete creare una nuova configurazione su  Adobe I/O.
* [Configurazione](#upgrade-integration-64) aggiornamento: Se siete un utente esistente di Brand Portal con l’istanza di creazione  AEM Assets configurata con Brand Portal su OAuth Gateway legacy, è consigliabile eliminare le configurazioni esistenti e creare una nuova configurazione su  Adobe I/O.

Le informazioni fornite si basano sul presupposto che chiunque legga la presente Guida abbia familiarità con le seguenti tecnologie:

* Installazione, configurazione e amministrazione di pacchetti Adobe Experience Manager e AEM

* Utilizzo di sistemi operativi Linux e Microsoft Windows

## Prerequisiti {#prerequisites}

Per configurare AEM Assets con Brand Portal, è necessario quanto segue:

* Un’istanza di creazione di  AEM Assets con l’ultimo Service Pack.
* URL del tenant di Brand Portal.
* Un utente con privilegi di amministratore di sistema nell’organizzazione IMS del tenant di Brand Portal.

[Download e installazione AEM 6.4](#aemquickstart)

[Download e installazione della versione più recente di AEM Service Pack](#servicepack)

### Download e installazione AEM 6.4 {#aemquickstart}

Si consiglia di AEM 6.4 per impostare un’istanza AEM di creazione. Se non disponete di AEM pronti, scaricatelo dalle seguenti posizioni:

* Se siete già clienti AEM, scaricate AEM 6.4 dal [ sito Web delle licenze Adobe](http://licensing.adobe.com).

* Se siete un partner  Adobe, utilizzate il programma di formazione per i partner  Adobi [ per richiedere AEM 6.4.](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q)

Dopo aver scaricato AEM, per istruzioni su come impostare un&#39;istanza AEM di creazione, vedere [implementazione e manutenzione](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html#defaultlocalinstall).

### Download e installazione AEM Service Pack più recente {#servicepack}

Per istruzioni dettagliate, vedete

* [Note sulla versione di AEM 6.4 Service Pack](https://helpx.adobe.com/it/experience-manager/6-4/release-notes/sp-release-notes.html)

**Se non riesci a trovare il pacchetto di AEM o il Service Pack più recente, contatta la** Assistenza clienti.

## Creare la configurazione {#configure-new-integration-64}

Effettuate i seguenti passaggi nella sequenza elencata se state configurando  AEM Assets con Brand Portal per la prima volta:

1. [Recuperare il certificato pubblico](#public-certificate)
1. [Creare l’integrazione di Adobe I/O](#createnewintegration)
1. [Creare la configurazione dell’account IMS](#create-ims-account-configuration)
1. [Configurare il servizio cloud](#configure-the-cloud-service)
1. [Verificare la configurazione](#test-integration)

>[!NOTE]
>
>Un’istanza di autore  AEM Assets può essere configurata solo con un tenant Brand Portal.

### Creare la configurazione IMS {#create-ims-configuration}

La configurazione IMS autentica il tenant di Brand Portal con l’istanza di authoring di AEM Assets.

La configurazione IMS prevede due passaggi:

* [Recuperare il certificato pubblico](#public-certificate)
* [Creare la configurazione dell’account IMS](#create-ims-account-configuration)

### Recuperare il certificato pubblico {#public-certificate}

Il certificato pubblico consente di autenticare il profilo su Adobe I/O.

1. Effettuate il login all’istanza di creazione  AEM Assets
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

1. Fai clic su **[!UICONTROL Scarica chiave pubblica]** e salva il file di certificato *AEM-Adobe-IMS.crt* sul computer. Il file di certificato viene utilizzato per [creare l’integrazione di Adobe I/O](#createnewintegration).

   ![Scarica certificato](assets/ims-config3.png)

1. Fai clic su **[!UICONTROL Avanti]**.

   Nella scheda **Account**, puoi creare l’account Adobe IMS, ma dovrai disporre dei dettagli di integrazione. Per il momento tieni aperta questa pagina.

   Aprite una nuova scheda e [Create  integrazione Adobe I/O](#createnewintegration) per ottenere i dettagli di integrazione per le configurazioni dell&#39;account IMS.

### Creare l’integrazione di Adobe I/O {#createnewintegration}

L’integrazione di Adobe I/O genera i valori di Chiave API, Segreto client e Payload (JWT), necessari per definire le configurazioni dell’account IMS.

1. Accedi alla console di Adobe I/O con privilegi di amministratore di sistema nell’organizzazione IMS del tenant di Brand Portal.

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
* [Creare l’integrazione di Adobe I/O](#createnewintegration)

**Procedura per creare la configurazione dell’account IMS:**

1. Apri la scheda **[!UICONTROL Account]** nella pagina Configurazione IMS. Hai tenuto aperta questa pagina alla fine della sezione [Recuperare il certificato pubblico](#public-certificate).

1. Specifica un **[!UICONTROL titolo]** per l’account IMS.

   In **[!UICONTROL Server autorizzazioni]**, immetti l’URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Incolla la chiave API, il segreto client e il payload JWT che hai copiato al termine di [Creare l’integrazione di Adobe I/O](#createnewintegration).

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

1. Effettuate il login all’istanza di creazione  AEM Assets

   URL predefinito: http:// localhost:4502/aem/start.html
1. Dal pannello **Strumenti** ![Strumenti](assets/tools.png), passa a **[!UICONTROL Cloud Services >> AEM Brand Portal]**.

   Viene aperta la pagina Configurazioni di Brand Portal.

1. Fai clic su **[!UICONTROL Crea]**.

1. Specifica un **[!UICONTROL titolo]** per la configurazione.

   Seleziona la configurazione IMS creata nel passaggio [Creare la configurazione dell’account IMS](#create-ims-account-configuration).

   In **[!UICONTROL URL servizio]**, immetti l’URL del tenant di Brand Portal.

   ![](assets/create-cloud-service.png)

1. Fai clic su **[!UICONTROL Salva e chiudi]**. Viene creata la configurazione cloud. L’istanza di creazione  AEM Assets ora è integrata con il tenant del Brand Portal.

### Verificare la configurazione {#test-integration}

1. Effettuate il login all’istanza di creazione  AEM Assets

   URL predefinito: http:// localhost:4502/aem/start.html

1. Dal pannello **Strumenti** ![Strumenti](assets/tools.png), passare a **[!UICONTROL Distribuzione >> Replica]**.

   ![](assets/test-integration1.png)

1. Viene visualizzata la pagina Replica.

   Fare clic su **[!UICONTROL Agenti sull&#39;autore]**.

   ![](assets/test-integration2.png)

1. Per ciascun tenant vengono creati quattro agenti di replica.

   Individuate gli agenti di replica del tenant del Brand Portal.

   Fate clic sull&#39;URL dell&#39;agente di replica.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >Gli agenti di replica lavorano in parallelo e condividono la distribuzione dei processi in modo uniforme, aumentando così la velocità di pubblicazione di quattro volte la velocità originale. Una volta configurato il servizio cloud, non è richiesta ulteriore configurazione per abilitare gli agenti di replica attivati per impostazione predefinita per abilitare la pubblicazione parallela di più risorse.

1. Per verificare la connessione tra  autore AEM Assets e Brand Portal, fate clic su **[!UICONTROL Test Connection]**.

   ![](assets/test-integration4.png)

1. Esaminate la parte inferiore dei risultati del test per verificare che la replica sia riuscita.

   ![](assets/test-integration5.png)


1. Verificate i risultati del test su tutti e quattro gli agenti di replica uno per uno.

   >[!NOTE]
   >
   >Evitare di disattivare gli agenti di replica, in quanto potrebbe causare errori di replica di alcune risorse.
   >
   >Verificate che tutti e quattro gli agenti di replica siano configurati in modo da evitare errori di timeout. Consultate [risoluzione dei problemi relativi alla pubblicazione parallela in Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html#connection-timeout).

Brand Portal è stato configurato correttamente con l’istanza di creazione  AEM Assets. Ora puoi:

* [Pubblicare risorse da AEM Assets su Brand Portal](../assets/brand-portal-publish-assets.md)
* [Pubblicare cartelle da AEM Assets su Brand Portal](../assets/brand-portal-publish-folder.md)
* [Pubblicare raccolte da AEM Assets su Brand Portal](../assets/brand-portal-publish-collection.md)
* [Configurare l’](https://docs.adobe.com/content/help/it-IT/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) origine delle risorse per consentire agli utenti del Brand Portal di contribuire e pubblicare le risorse per  AEM Assets.

## Configurazione aggiornamento {#upgrade-integration-64}

Per aggiornare le configurazioni esistenti, eseguite i seguenti passaggi nella sequenza elencata:
1. [Verificare i processi in esecuzione](#verify-jobs)
1. [Elimina configurazioni esistenti](#delete-existing-configuration)
1. [Creare la configurazione](#configure-new-integration-64)

### Verificare i processi in esecuzione {#verify-jobs}

Prima di apportare eventuali modifiche, verificate che nessun processo di pubblicazione sia in esecuzione nell’istanza di authoring  AEM Assets. A tal fine, è possibile verificare tutti e quattro gli agenti di replica e assicurarsi che la coda sia ideale/vuota.

1. Effettuate il login all’istanza di creazione  AEM Assets

   URL predefinito: http:// localhost:4502/aem/start.html

1. Dal pannello **Strumenti** ![Strumenti](assets/tools.png), passare a **[!UICONTROL Distribuzione >> Replica]**.

1. Viene visualizzata la pagina Replica.

   Fare clic su **[!UICONTROL Agenti sull&#39;autore]**.

   ![](assets/test-integration2.png)

1. Individuate gli agenti di replica del tenant del Brand Portal.

   Verificare che la **coda sia inattiva** per tutti gli agenti di replica. Nessun processo di pubblicazione attivo.

   ![](assets/test-integration3.png)

### Elimina configurazioni esistenti {#delete-existing-configuration}

È necessario eseguire il seguente elenco di controllo durante l&#39;eliminazione della configurazione esistente.
* Elimina tutti e quattro gli agenti di replica
* Elimina servizio cloud
* Elimina utente MAC

Per eliminare la configurazione esistente, effettuate le seguenti operazioni:

1. Accedete all’istanza di creazione di  AEM Assets e aprite CRX Lite come amministratore.

   URL predefinito: http:// localhost:4502/crx/de/index.jsp

1. Andate a `/etc/replications/agents.author` ed eliminate tutti e quattro gli agenti di replica del tenant del Brand Portal.

   ![](assets/delete-replication-agent.png)

1. Passare a `/etc/cloudservices/mediaportal` ed eliminare la **configurazione del Cloud Service**.

   ![](assets/delete-cloud-service.png)

1. Andate a `/home/users/mac` ed eliminate l&#39; **utente MAC** del tenant del Brand Portal.

   ![](assets/delete-mac-user.png)


È ora possibile [creare la configurazione](#configure-new-integration-64) nell&#39;istanza di authoring AEM 6.4 su  Adobe I/O.



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

Una volta completata la replica, potete pubblicare risorse, cartelle e raccolte in Brand Portal. Per informazioni dettagliate, consultate:

* [Pubblicare risorse su Brand Portal](brand-portal-publish-assets.md)
* [Pubblicare risorse e cartelle su Brand Portal](brand-portal-publish-folder.md)
* [Pubblicare raccolte nel portale dei marchi](brand-portal-publish-collection.md)
