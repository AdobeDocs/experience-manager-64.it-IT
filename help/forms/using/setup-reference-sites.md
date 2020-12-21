---
title: Configurare e configurare  siti di riferimento AEM Forms
seo-title: Configurare e configurare  siti di riferimento AEM Forms
description: ' siti di riferimento AEM Forms illustrano come utilizzare  AEM Forms per implementare un flusso di lavoro end-to-end in un’organizzazione.'
seo-description: ' siti di riferimento AEM Forms illustrano come utilizzare  AEM Forms per implementare un flusso di lavoro end-to-end in un’organizzazione.'
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '2922'
ht-degree: 0%

---


# Configurare e configurare  siti di riferimento AEM Forms {#set-up-and-configure-aem-forms-reference-sites}

 AEM Forms fornisce un&#39;implementazione del sito di riferimento per dimostrare come  AEM Forms aiuta le organizzazioni del settore e del governo dei servizi finanziari a trasformare le loro complesse transazioni in esperienze digitali semplici e coinvolgenti ovunque, in qualsiasi momento, su qualsiasi dispositivo.

I siti di riferimento We.Finance e We.Gov attingono a casi di utilizzo reali per coinvolgere clienti esistenti e potenziali, dal punto di partenza alla gestione delle corrispondenze e delle transazioni in modo personalizzato ed economico.

I siti di riferimento consentono di esplorare e presentare le seguenti funzionalità chiave di  AEM Forms.

* Esperienza di authoring semplificata con moduli adattivi coinvolgenti e reattivi e comunicazioni interattive.
* Comunicazioni interattive per creare comunicazioni interattive, personalizzate e reattive per i clienti che si adattano all&#39;impostazione e al layout del dispositivo.
* Integrazione dei dati per la connessione a origini dati diverse per la precompilazione e l&#39;invio dei dati del modulo tramite un modello dati del modulo.
* Flusso di lavoro Forms per automatizzare processi e flussi di lavoro aziendali.
* Funzionalità avanzate di gestione ed elaborazione dei dati utente.
* Integrazione con  Adobe Sign per firmare e inviare moduli adattivi in modo sicuro.
* Integrazione con  Adobe Target per distribuire raccomandazioni mirate e eseguire test A/B per ottimizzare il ROI da un modulo.
* Integrazione con  Adobe Analytics per misurare le prestazioni di un modulo o di una campagna e prendere decisioni informate.
* Esperienza di compilazione dei moduli migliorata.

I siti di riferimento forniscono risorse riutilizzabili che potete usare come modelli per creare risorse personalizzate.

* Integrazione con  Adobe Sign per firmare e inviare moduli adattivi in modo sicuro.

* Integrazione con  Adobe Sign per firmare e inviare moduli adattivi in modo sicuro.

## Prerequisiti e passaggi per configurare i siti di riferimento {#prerequisites-and-steps-to-set-up-reference-sites}

Prima di configurare il sito di riferimento, accertatevi di disporre dei seguenti elementi:

* **AEM di base**

   AEM QuickStart,  pacchetto aggiuntivo AEM Forms e pacchetti di riferimento per siti. Per informazioni dettagliate sui pacchetti di componenti aggiuntivi e di riferimento per i siti, vedere [ rilasci di AEM Forms](https://helpx.adobe.com/it/aem-forms/kb/aem-forms-releases.html).

* **Un**
servizio SMTP: è possibile utilizzare qualsiasi servizio SMTP.

* **account sviluppatore Adobe Sign e  applicazione API Adobe Sign**

   Per utilizzare le funzionalità di firma digitale, è necessario  account sviluppatore Adobe Sign. Vedere [ Adobe Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html).

* Un&#39;istanza in esecuzione di Microsoft Dynamics 365 da integrare con  AEM Forms. Per eseguire il sito di riferimento, importare i dati di esempio nell&#39;istanza di Microsoft Dynamics per precompilare la comunicazione interattiva utilizzata nel sito di riferimento.
* Un&#39;istanza in esecuzione di AEM 6.4 con il pacchetto aggiuntivo Forms. Per ulteriori informazioni, vedere [Installazione e configurazione  AEM Forms](installing-configuring-aem-forms-osgi.md).

Effettuate i seguenti passaggi nella sequenza consigliata per configurare e impostare i siti di riferimento.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Incremento</strong></th> 
   <th><strong>Configurazione</strong></th> 
   <th><strong>Note</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">Installare e configurare  AEM Forms</a></td> 
   <td>Creazione e pubblicazione</td> 
   <td>Installate e configurate  istanze di creazione e pubblicazione AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">Configurare SSL</a></td> 
   <td>Autore e pubblicazione<br /> </td> 
   <td>Abilita HTTP su SSL per comunicazioni sicure con  Adobe Sign.</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">Configurare la configurazione Day CQ Link Externalizer</a></p> </td> 
   <td>Autore e pubblicazione<br /> </td> 
   <td><p>Casi di utilizzo del sito di riferimento forniscono e-mail per diverse transazioni. Questa impostazione è necessaria per la consegna della newsletter tramite e-mail. Gli URL e le immagini puntano all’istanza di pubblicazione. </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">Configura servizio di posta CQ Day</a></td> 
   <td>Creazione e pubblicazione</td> 
   <td>Obbligatorio per la comunicazione tramite e-mail.</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">Ignora configurazione XSS predefinita</a></td> 
   <td>Pubblicazione</td> 
   <td>Utilizzato per ignorare $, { e } caratteri bloccati dalla sicurezza xss.</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">Configurare le impostazioni di AEM DS</a></td> 
   <td>Autore</td> 
   <td>Configurare AEM DS per l'invio del modulo nell'istanza di pubblicazione e per l'elaborazione dei flussi di lavoro nell'istanza di creazione.</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">Distribuzione di pacchetti di siti di riferimento</a></td> 
   <td>Autore</td> 
   <td>Distribuire pacchetti per siti di riferimento ’istanza di creazione AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">Importa dati di esempio in Microsoft Dynamics</a></td> 
   <td>Creazione e pubblicazione</td> 
   <td>Importazione di dati di esempio per l'applicazione di carte di credito, l'applicazione di ipoteca per la casa e l'applicazione di assicurazione per la casa dettagliata</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Configurare il servizio cloud OAuth per Microsoft Dynamics</a></td> 
   <td>Creazione e pubblicazione</td> 
   <td>Configurare il servizio cloud OAuth in  AEM Forms per abilitare la comunicazione tra  AEM Forms e Microsoft Dynamics. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Configurare  pianificazione Adobe Sign</a></td> 
   <td>Autore e pubblicazione<br /> </td> 
   <td>Modifica la configurazione del pianificatore per controllare lo stato ogni due minuti.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">Configura sito di riferimento  Cloud Service Adobe Sign</a></td> 
   <td>Autore e pubblicazione<br /> </td> 
   <td>Una configurazione fornita con i siti di riferimento crea pacchetti e richiede la riconfigurazione con credenziali valide.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">Configurare Forms Common Configuration Service per gli utenti anonimi</a></td> 
   <td>Pubblicazione</td> 
   <td>La configurazione consente l’invio, la firma e la generazione del documento di registrazione per gli utenti anonimi.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">Modifica file Swagger del servizio residuo per il modello dati del modulo</a></td> 
   <td>Autore e pubblicazione<br /> </td> 
   <td>Modificare il servizio per il proprio ambiente.</td> 
  </tr> 
 </tbody> 
</table>

## Installazione e configurazione  AEM Forms {#install-and-configure-aem-forms}

Installate e distribuite  AEM Forms come descritto in [Installazione e configurazione  AEM Forms su OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md).

>[!NOTE]
>
>Configurate gli agenti di replica e replica inversa se esistono più istanze di pubblicazione o di creazione e pubblicazione su computer diversi.

## Configurare SSL {#ssl}

La configurazione SSL è necessaria per comunicare con  server Adobe Sign. Per i passaggi dettagliati, vedere [Abilitazione di HTTP su SSL](/help/sites-administering/ssl-by-default.md).

>[!CAUTION]
>
>Non configurate l&#39;opzione SSL sulla cartella `/etc/map`.

## Configurare la configurazione Day CQ Link Externalizer {#externalizer}

In AEM, il **Externalizer** è un servizio OSGI che consente di trasformare programmaticamente un percorso di risorse (ad es. /path/to/my/page) in un URL esterno e assoluto (ad esempio, https://www.mycompany.com/path/to/my/page) anteponendo il percorso a un DNS preconfigurato. Consultate [Esternalizzazione di URL](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>Non esternalizzate con l’URL HTTPS se utilizzate un certificato autofirmato per SSL.
>
>Inoltre, per il server locale utilizzate localhost invece del relativo nome host.

Effettuate le seguenti operazioni sia sulle istanze di creazione che di pubblicazione:

1. Andate alla configurazione OSGi all&#39;indirizzo https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr.
1. Individuate e toccate la configurazione **[!UICONTROL Day CQ Link Externalizer]**.

   Viene visualizzata la finestra di dialogo Day CQ Link Externalizer (Esternalizzatore collegamento CQ Day) per modificare la configurazione.

1. Nella finestra di dialogo Day CQ Link Externalizer, nel campo Domains (Domini):

   * Nell’istanza di creazione, specificate un URL di pubblicazione a cui potete accedere da un sistema esterno. Ad esempio, un nome host o un server Web di pubblicazione.
   * Nell’istanza di pubblicazione, specificate gli URL di creazione e pubblicazione.

1. Sia nelle istanze di creazione che di pubblicazione, accertatevi che l’URL del server locale sia specificato nel campo Domini.
1. Toccate **[!UICONTROL Salva]**. Attendi il riavvio di tutti i servizi.

## Configurare il servizio di posta di CQ Day {#cqmail}

L&#39;implementazione del sito di riferimento richiede l&#39;invio di e-mail agli utenti di esempio quando compilano e inviano i moduli. La configurazione di Day CQ Mail Service consente di fornire i dettagli del servizio SMTP per inviare e-mail automatizzate ai clienti. Vedere [Configurazione delle notifiche e-mail](/help/sites-administering/notification.md).

Per configurare il servizio di posta elettronica nell’istanza di pubblicazione, effettuate le seguenti operazioni:

1. Andate alla configurazione OSGi all&#39;indirizzo https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr.
1. Individuate e toccate **[!UICONTROL Day CQ Mail Service]** per aprirlo alla configurazione.
1. Specificare il nome host del server SMTP e i valori della porta.
1. Toccate **[!UICONTROL Salva]**.

>[!NOTE]
>
>Potete utilizzare il vostro servizio SMTP aziendale o i servizi pubblici come Gmail. Per configurare il servizio SMTP, consulta la documentazione del servizio SMTP.

## Ignora configurazione XSS predefinita {#xss}

I modelli e-mail per il sito di riferimento We.Finance contengono collegamenti personalizzati nelle e-mail. Tali collegamenti hanno un segnaposto come `${placeholder}`. Questi segnaposto vengono sostituiti dai valori effettivi prima dell&#39;invio delle e-mail. La configurazione di protezione XSS predefinita per AEM non consente l&#39;utilizzo di parentesi graffe (**{ }**) nell&#39;URL nel contenuto HTML. Tuttavia, potete ignorare la configurazione predefinita eseguendo i seguenti passaggi sull’istanza di pubblicazione:

1. Copiare `/libs/cq/xssprotection/config.xml` in `/apps/cq/xssprotection/config.xml`.
1. Apri `/apps/cq/xssprotection/config.xml`.
1. Nella sezione `common-regexps`, modificare la voce `onsiteURL` come segue e salvare il file.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>Le parentesi graffe (**{ }**) sono incluse come caratteri accettati nell&#39;URL nel contenuto HTML.

Dopo aver configurato il server SMTP, provare a compilare un modulo utilizzando il nome Sarah Rose e salvarlo come bozza. Quando salvate come bozza, potete ricevere la bozza tramite e-mail. Toccando il pulsante **Invia e-mail**, se si riceve un messaggio e-mail con un collegamento alla bozza dell&#39;applicazione, la configurazione dell&#39;e-mail viene completata correttamente. Assicurati di accedere utilizzando le credenziali di Sarah per vedere la bozza.

## Configurare le impostazioni AEM DS {#aemds}

AEM le impostazioni del servizio DS sono richieste nell&#39;istanza Pubblica per le comunicazioni e-mail nei casi di utilizzo del sito di riferimento. Per i passaggi dettagliati per configurare AEM configurazione del servizio DS nell&#39;istanza Pubblica, vedere [Configurare AEM impostazioni DS](/help/forms/using/configuring-the-processing-server-url-.md).

Per  siti di riferimento AEM Forms, in AEM DS Settings Service, specificate l&#39;URL del server di pubblicazione invece dell&#39;URL del server di elaborazione.

>[!CAUTION]
>
>Non inserire `/lc` nell&#39;URL del server di elaborazione se lo state configurando per  AEM Forms OSGi.

## Distribuzione di pacchetti di siti di riferimento {#refsite}

Installate i seguenti pacchetti di siti di riferimento tramite Distribuzione software.

* [AEM-FORMS-6.4-FSI-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

Per ulteriori informazioni sull&#39;utilizzo dei pacchetti, vedere [Come utilizzare i pacchetti](/help/sites-administering/package-manager.md).

Dopo aver installato i pacchetti e avviato le istanze di creazione e pubblicazione, visitate i seguenti URL nel browser:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

Se l&#39;installazione ha esito positivo, potete accedere alle pagine di destinazione dei siti di riferimento We.Gov e We.Finance.

## (Facoltativo) Importa dati di esempio in Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

I siti di riferimento dell&#39;applicazione ipoteca principale e dell&#39;applicazione di assicurazione automatica sono configurati per utilizzare i record di Microsoft Dynamics. Il pacchetto del sito di riferimento installa un&#39;entità personalizzata e record di esempio che è possibile importare in Microsoft Dynamics per eseguire il sito di riferimento. Effettuare le seguenti operazioni per migrare e impostare i dati di esempio:

Per importare l&#39;entità personalizzata per l&#39;applicazione di assicurazione automatica:

1. Scaricate il pacchetto della soluzione **WeFinanceAutoInsurance_1_0.zip** da `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` nell&#39;istanza AEM autore.
1. Nell&#39;istanza di Microsoft Dynamics, andare a **[!UICONTROL Soluzioni]** nel menu **[!UICONTROL Impostazioni]** e fare clic su **[!UICONTROL Importa]**. Selezionate e importate il pacchetto.

Per importare l&#39;entità personalizzata per l&#39;applicazione di assicurazione automatica:

1. Scaricate il pacchetto **AEMFormsFSIRefsite_1_0.zip** da https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip. Selezionate e importate il pacchetto.

1. Nell&#39;istanza di Microsoft Dynamics, andare a **[!UICONTROL Soluzioni]** nel menu **[!UICONTROL Impostazioni]** e fare clic su **[!UICONTROL Importa]**. Selezionate e importate il pacchetto.

Per importare i record cliente e polizza assicurativa:

1. Scaricate i file di dati **We.Finance Customers.csv, We.Finance Auto Insurance Renewals.csv** e **home Mutuo** dai seguenti percorsi nell&#39;istanza di AEM autore:

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Nell’istanza di Microsoft Dynamics, effettuate le seguenti operazioni:

   * Vai a **[!UICONTROL Vendite > We.Finance Customers]** e fai clic su **[!UICONTROL Importa]**.
   * Vai a **[!UICONTROL Vendite > We.Finance Auto Insurance]** e fai clic su **[!UICONTROL Importa]**.
   * Vai a **[!UICONTROL Vendite > We.Finance Home Mortgage]** e fai clic su **[!UICONTROL Import]**.

## Configurare il servizio cloud OAuth per Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}

Configurare il servizio cloud OAuth in  AEM Forms per abilitare la comunicazione tra  AEM Forms e Microsoft Dynamics. Effettuate le seguenti operazioni per configurare l’Cloud Service OAuth sulle istanze di creazione e pubblicazione AEM:

1. Per AEM&#39;istanza di creazione, andate a **[!UICONTROL Strumenti > Cloud Services > Origini dati > globale]**. Toccate l&#39;icona **[!UICONTROL Refsite Dynamics Integration]** e toccate **[!UICONTROL Properties]**.
1. Accedere all&#39;account Microsoft Azure Active Directory. Aggiungete l&#39;URL di configurazione del servizio cloud copiato nell&#39;impostazione **[!UICONTROL Rispondi all&#39;URL]** per l&#39;applicazione registrata. Salva la configurazione.
1. Nella scheda Impostazioni autenticazione, specificare **[!UICONTROL Radice servizio]**, **[!UICONTROL ID client]**, **[!UICONTROL Segreto cliente]** e **[!UICONTROL URL risorsa]** per l&#39;istanza di Microsoft Dynamics. Fare clic su **[!UICONTROL Connetti a OAuth]** per reindirizzare alla pagina di accesso di Microsoft Dynamics.
1. Immettete le credenziali di accesso. Una volta effettuato l&#39;accesso, verrete reindirizzati alla pagina di configurazione del servizio cloud  AEM Forms. Fai clic su **[!UICONTROL Salva e chiudi]**. La configurazione del servizio cloud viene salvata.
1. Vai a **[!UICONTROL Forms > Integrazioni dati > We.Finance]**. Selezionare Auto Insurance (Dynamics) e fare clic su Edit (Modifica). Le entità di Microsoft Dynamics sono elencate nella scheda Origini dati. Attendere che tutte le entità siano recuperate da Microsoft Dynamics ed elencate nella scheda origini dati.
1. Selezionare l&#39;entità **[!UICONTROL AutoInsuranceRenewal]** e fare clic su **[!UICONTROL Oggetto modello di prova]**. Nella sezione della richiesta di input, specificate il valore per l&#39;ID cliente come &quot;900001&quot; e fate clic su **[!UICONTROL Test]**. Nella sezione Output vengono visualizzati i record recuperati da Microsoft Dynamics per ID cliente 900001.
1. Nella sezione della richiesta di input, specificate il valore per l&#39;ID cliente come &quot;900001&quot; e fate clic su **[!UICONTROL Test]**. Nella sezione Output vengono visualizzati i record recuperati da Microsoft Dynamics per ID cliente 900001.
1. Ripetete i passaggi da 1 a 6 sull’istanza di pubblicazione.

## Configurare  pianificazione Adobe Sign {#scheduler}

Per le istanze di creazione e pubblicazione effettuate le seguenti operazioni:

1. Passate AEM console Configurazione Web all&#39;indirizzo `https://[server]:[host]/system/console/configMgr`.
1. Individuate e toccate **[!UICONTROL Adobe Sign Configuration Service]** per aprirlo alla configurazione.
1. Configurare **[!UICONTROL Status Update Scheduler Expression]** come **0 0/2 &amp;ast; &amp;ast; &amp;ast; ?**.

   >[!NOTE]
   >
   >La configurazione del pianificatore di cui sopra verifica lo stato del servizio Adobe Sign  ogni due minuti.

1. Toccate **[!UICONTROL Salva]**.

## Configurare il sito di riferimento  servizio cloud Adobe Sign {#sign-service}

Per le istanze di creazione e pubblicazione effettuate le seguenti operazioni:

1. Vai a **[!UICONTROL Strumenti > Cloud Services >  Adobe Sign > globale]**. Selezionare **[!UICONTROL AEM Forms Reference Site Sign]** e toccare **[!UICONTROL Properties]**.

   >[!CAUTION]
   >
   >Accertatevi che l&#39;URL https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html sia aggiunto all&#39;elenco degli URL di reindirizzamento della configurazione OAuth dell&#39;applicazione API  Adobe Sign.

1. Specificate l&#39;ID client e il segreto della configurazione OAuth dell&#39;applicazione Adobe Sign .
1. (Facoltativo) Selezionare l&#39;opzione **[!UICONTROL Abilita  Adobe Sign per gli allegati anche]**, quindi toccare **[!UICONTROL Connetti a  Adobe Sign]**. Aggiunge i file allegati a un modulo adattivo al documento Adobe Sign  corrispondente inviato per la firma.
1. Toccate **[!UICONTROL Connetti a  Adobe Sign]** ed effettuate l&#39;accesso con le  credenziali Adobe Sign.

## Configurare Forms Common Configuration Service {#anonymous}

Effettuate le seguenti operazioni nell’istanza di pubblicazione per consentire l’accesso agli utenti anonimi:

1. Passate AEM console Configurazione Web all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
1. Trovare e toccare **[!UICONTROL Forms Common Configuration Service]** per aprirlo alla configurazione.
1. Configurare il campo **[!UICONTROL Consenti]** per **[!UICONTROL Tutti gli utenti]**.
1. Toccate **[!UICONTROL Salva]**.

## Modifica servizio di riposo per il modello dati modulo {#fdm}

Per le istanze di creazione e pubblicazione effettuate le seguenti operazioni:

1. Passate a CRXDE all&#39;indirizzo `https://[server]:[port]/crx/de/index.jsp`.
1. Andate a **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** e aprite il file swagger.
1. Aggiornate le impostazioni di host e porta in base all&#39;ambiente in uso.
1. Salvate le impostazioni.
1. (**Solo istanza Author**) Passare a **[!UICONTROL Strumenti]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Origini dati]** > **[!UICONTROL globale]**. Selezionare **[!UICONTROL roi-rest]** e toccare **[!UICONTROL Properties]**. Toccate **[!UICONTROL Impostazioni autenticazione]** e impostate **[!UICONTROL Tipo di autenticazione]** su **[!UICONTROL Autenticazione di base]**. Specificare `admin`/ `admin`come nome utente/password per accedere al servizio. Toccate **[!UICONTROL Save and Close]** (Salva e chiudi).

## Integrazione con il Marketing Cloud {#integrate-with-marketing-cloud}

È possibile integrare il  AEM Forms con  Adobe Analytics e  Adobe Target.  Adobe Analytics consente di generare report e analizzare le prestazioni dei moduli adattivi, mentre  Adobe Target consente di distribuire esperienze personalizzate ed eseguire test A/B per i moduli adattivi.

Effettuate le seguenti operazioni per configurare  Adobe Analytics e  Adobe Target  AEM Forms.

### Configurare  Adobe Analytics {#configure-adobe-analytics}

&#39;integrazione AEM Forms con  Adobe Analytics consente di monitorare e analizzare in che modo i clienti interagiscono con moduli e documenti. Consente di identificare e risolvere le aree problematiche e di agire per aumentare il tasso di conversione.

Per provare questa funzionalità nel sito di riferimento, configura il tuo account Analytics come descritto in [Configurazione di analisi e report](/help/forms/using/configure-analytics-forms-documents.md).

Per generare un rapporto, i dati iniziali vengono raggruppati con i siti di riferimento. Prima di utilizzare i dati iniziali, effettuate le seguenti operazioni:

1. Verifica che le configurazioni di analisi We.Finance e We.Gov siano disponibili nei servizi AEM Cloud. Puoi trovare i servizi cloud in uno dei seguenti modi:

   * Andate a **[!UICONTROL Strumenti>Cloud Services>Cloud Services precedenti]** oppure individuate https://&lt;host>:&lt;porta>/libs/cq/core/content/tools/cloudservices.html.
   * Nella pagina **[!UICONTROL Cloud Services]**, nella sezione **[!UICONTROL Adobe Analytics]** fare clic su `Show Configurations`. Potete vedere le configurazioni We.Finance e We.Gov disponibili. Fate clic per aprire la configurazione. Nella pagina di configurazione, fare clic su **[!UICONTROL Modifica]**. Specifica società, nome utente, segreto condiviso (password) e centro dati validi e fai clic su **[!UICONTROL Connetti ad Analytics]**. Dopo aver ottenuto la finestra di dialogo Connessione, fare clic su **[!UICONTROL OK]** nella finestra di dialogo di configurazione. Configurate il framework nella configurazione di Analytics come descritto in [Configuring Analytics and Reports](/help/forms/using/configure-analytics-forms-documents.md) (Configurazione di Analytics e Reporting).

1. Andate su https://&lt;*host*>:&lt;*port*>/system/console/configMgr ed effettuate le seguenti operazioni:

   * Nella pagina **[!UICONTROL Configurazione console Web]**, individua e fai clic su **[!UICONTROL Configurazione AEM Forms Analytics]**.
   * Nel campo **[!UICONTROL Framework di SiteCatalyst]** della finestra di dialogo Configurazione AEM Forms Analytics , selezionate we-finance(we-finance) o we-gov(we-gov).
   * Fare clic su **[!UICONTROL Salva]** e consentire l&#39;aggiornamento della pagina.

1. Passare a Forms Manager all&#39;indirizzo https://&lt;host>:&lt;porta>/aem/forms ed effettuare le seguenti operazioni:

   * Aprite la cartella We.Finance o We.Gov e selezionate il modulo per il quale desiderate visualizzare il rapporto.
   * Fate clic su Abilita analisi nella barra degli strumenti Azioni. Dopo aver attivato l&#39;analisi del modulo, fai clic su Rapporto analisi. Potete visualizzare un rapporto vuoto generato. Dopo la generazione di un report vuoto, devi fornire i dati iniziali forniti con il pacchetto refsite per generare report di analisi a scopo dimostrativo.

   I siti di riferimento forniscono report di analisi con dati iniziali per i casi di utilizzo di carte di credito, ipoteche per la casa e assistenza ai bambini. Per la configurazione dei dati iniziali, vedere [We.Finance site walkthrough](/help/forms/using/finance-reference-site-walkthrough.md) and [We.Gov sito di riferimento walkthrough](/help/forms/using/gov-reference-site-walkthrough.md).

### Configurare Target {#configure-target}

Il sito di riferimento mostra l&#39;integrazione di  AEM Forms con  Adobe Target che consente di includere contenuti mirati e personalizzati nei documenti adattivi. Consente inoltre di creare test A/B per i moduli adattivi.

Per provare l&#39;integrazione nel sito di riferimento, effettuate le seguenti operazioni per configurare Target in AEM:

1. Avviate l&#39;avvio rapido dell&#39;autore con l&#39;argomento jvm `-Dabtesting.enabled=true` per abilitare il test A/B sul server.

   **Nota**: Se l&#39;istanza AEM è in esecuzione su JBoss, che viene avviata come servizio dall&#39;installazione di Turnkey, aggiungere il  `-Dabtesting.enabled=true` parametro nella seguente voce del  `jboss\bin\standalone.conf.bat` file:

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Accedete a https://&lt;*hostname*>:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html.

1. Nella sezione **[!UICONTROL Adobe Target]**, fare clic su **[!UICONTROL Mostra configurazioni]**. È possibile visualizzare la configurazione di destinazione We.Finance disponibile. Fate clic per aprire la configurazione. Nella pagina di configurazione, fare clic su **[!UICONTROL Modifica]**. Viene visualizzata la finestra di dialogo **[!UICONTROL Edit Component]** per la configurazione.

1. Specifica il codice cliente, l&#39;e-mail e la password associati all&#39;account Target. Selezionare il tipo di API come **[!UICONTROL REST]**.
1. Fare clic su **[!UICONTROL Connetti per  destinazione Adobe]**. Una volta configurato l&#39;account Target, fate clic su **[!UICONTROL OK]**. Potete vedere che la configurazione del pacchetto include un framework di Target.

1. Andate a https://&lt;*hostname*>:&lt;*port*>/system/console/configMgr.

1. Fate clic su **[!UICONTROL AEM Forms Target Configuration]**.
1. Selezionate un framework Target.
1. Nel campo **[!UICONTROL URL di destinazione]**, specificate l&#39;URL per  AEM Forms. Ad esempio: https://&lt;*hostname*>:&lt;*port*>.

1. Fai clic su **[!UICONTROL Salva]**.

I casi di utilizzo di applicazioni con carta di credito e applicazioni con ipoteche domestiche dimostrano come eseguire test A/B e presentare un rapporto a scopo dimostrativo. Per informazioni dettagliate, vedere [Sito di riferimento We.Finance in corso](/help/forms/using/finance-reference-site-walkthrough.md).

## Passaggio successivo {#next-step}

Ora siete tutti impostati per esplorare il sito di riferimento. Per ulteriori informazioni sul flusso di lavoro e i passaggi del sito di riferimento, vedi:

* [Procedura dettagliata sul sito di riferimento We.Finance](/help/forms/using/finance-reference-site-walkthrough.md)
* [Procedura dettagliata sul sito di riferimento We.Gov](/help/forms/using/gov-reference-site-walkthrough.md)

* [Procedura dettagliata sul sito di riferimento self-service dei dipendenti](/help/forms/using/employee-self-service-reference-site.md)

