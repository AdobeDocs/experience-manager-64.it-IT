---
title: Configurare e configurare i siti di riferimento di AEM Forms
seo-title: Set up and configure AEM Forms reference sites
description: Nei siti di riferimento di AEM Forms viene illustrato come utilizzare AEM Forms per implementare un flusso di lavoro end-to-end in un’organizzazione.
seo-description: AEM Forms reference sites showcase how you can use AEM Forms to implement end-to-end workflow in an organization.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
exl-id: 9c5d956c-06bc-4428-afcd-02b4f81b802f
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '2911'
ht-degree: 2%

---

# Configurare e configurare i siti di riferimento di AEM Forms {#set-up-and-configure-aem-forms-reference-sites}

AEM Forms fornisce un’implementazione del sito di riferimento per dimostrare in che modo AEM Forms aiuta le organizzazioni del settore e del governo dei servizi finanziari a trasformare le loro transazioni complesse in esperienze digitali semplici e coinvolgenti ovunque, in qualsiasi momento, su qualsiasi dispositivo.

I siti di riferimento We.Finance e We.Gov richiamano casi d&#39;uso reali per interagire con clienti esistenti e potenziali, dal momento del primo contatto alla gestione di corrispondenze e transazioni in modo personalizzato ed economico.

I siti di riferimento ti consentono di esplorare e mostrare le seguenti funzionalità chiave di AEM Forms.

* Esperienza di authoring semplificata per moduli adattivi coinvolgenti e reattivi e comunicazioni interattive.
* Comunicazioni interattive per creare comunicazioni cliente interattive, personalizzate e reattive che si adattano all&#39;impostazione e al layout del dispositivo.
* Integrazione dei dati per connettersi a diverse origini dati per precompilare e inviare i dati del modulo tramite un modello di dati del modulo.
* Flusso di lavoro Forms per automatizzare i processi e i flussi di lavoro aziendali.
* Funzionalità avanzate di gestione ed elaborazione dei dati utente.
* Integrazione con Acrobat Sign per la firma e l’invio sicuri di moduli adattivi.
* Integrazione con Adobe Target per distribuire consigli mirati ed eseguire test A/B per massimizzare il ROI da un modulo.
* Integrazione con Adobe Analytics per misurare le prestazioni di un modulo o di una campagna e prendere decisioni informate.
* Esperienza migliorata di compilazione dei moduli.

I siti di riferimento forniscono risorse riutilizzabili che possono essere utilizzate come modelli per creare risorse personalizzate.

* Integrazione con Acrobat Sign per la firma e l’invio sicuri di moduli adattivi.

* Integrazione con Acrobat Sign per la firma e l’invio sicuri di moduli adattivi.

## Prerequisiti e passaggi per configurare siti di riferimento {#prerequisites-and-steps-to-set-up-reference-sites}

Prima di configurare il sito di riferimento, assicurarsi di disporre dei seguenti elementi:

* **AEM di base**

   AEM QuickStart, pacchetto aggiuntivo AEM Forms e pacchetti di riferimento per siti. Vedi [Versioni di AEM Forms](https://helpx.adobe.com/it/aem-forms/kb/aem-forms-releases.html) per i dettagli dei pacchetti di componenti aggiuntivi e di riferimenti a siti.

* **Servizio SMTP**
È possibile utilizzare qualsiasi servizio SMTP.

* **Account sviluppatore Acrobat Sign e applicazione API Acrobat Sign**

   Per utilizzare le funzionalità di firma digitale, è necessario un account sviluppatore Acrobat Sign. Vedi [Acrobat Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html).

* Un’istanza in esecuzione di Microsoft Dynamics 365 da integrare con AEM Forms. Per eseguire il sito di riferimento, è necessario importare i dati di esempio nell’istanza di Microsoft Dynamics per precompilare la comunicazione interattiva utilizzata nel sito di riferimento.
* Un&#39;istanza in esecuzione di AEM 6.4 con pacchetto aggiuntivo Forms. Per ulteriori informazioni, consulta [Installazione e configurazione di AEM Forms](installing-configuring-aem-forms-osgi.md).

Esegui i seguenti passaggi nella sequenza consigliata per configurare e configurare i siti di riferimento.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Passaggio</strong></th> 
   <th><strong>Configurare</strong></th> 
   <th><strong>Note</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">Installare e configurare AEM Forms</a></td> 
   <td>Creazione e pubblicazione</td> 
   <td>Installa e configura le istanze di authoring e pubblicazione di AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">Configurare SSL</a></td> 
   <td>Creazione e pubblicazione<br /> </td> 
   <td>Abilita HTTP su SSL per comunicazioni sicure con Acrobat Sign.</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">Configurare la configurazione Day CQ Link Externalizer</a></p> </td> 
   <td>Creazione e pubblicazione<br /> </td> 
   <td><p>I casi di utilizzo del sito di riferimento forniscono e-mail per transazioni diverse. Questa impostazione è necessaria per la consegna della newsletter tramite e-mail. Gli URL e le immagini puntano all’istanza di pubblicazione. </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">Configura il servizio di posta CQ Day</a></td> 
   <td>Creazione e pubblicazione</td> 
   <td>Obbligatorio per la comunicazione via e-mail.</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">Ignora configurazione XSS predefinita</a></td> 
   <td>Pubblicazione</td> 
   <td>Utilizzato per sostituire i caratteri $, { e } bloccati dalla sicurezza xss.</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">Configurare le impostazioni di AEM DS</a></td> 
   <td>Autore</td> 
   <td>Configura AEM DS per l’invio del modulo sull’istanza di pubblicazione e per l’elaborazione dei flussi di lavoro sull’istanza di authoring.</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">Distribuire pacchetti di siti di riferimento</a></td> 
   <td>Autore</td> 
   <td>Distribuisci pacchetti di siti di riferimento sull’istanza di authoring di AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">Importare dati di esempio in Microsoft Dynamics</a></td> 
   <td>Creazione e pubblicazione</td> 
   <td>Importazione di dati di esempio per l'applicazione di carte di credito, l'applicazione di mutui per la casa e l'applicazione di assicurazione per la casa procedura dettagliata</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Configurazione del servizio cloud OAuth per Microsoft Dynamics</a></td> 
   <td>Creazione e pubblicazione</td> 
   <td>Configura il servizio cloud OAuth in AEM Forms per abilitare la comunicazione tra AEM Forms e Microsoft Dynamics. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Configurare Acrobat Sign Scheduler</a></td> 
   <td>Creazione e pubblicazione<br /> </td> 
   <td>Modifica la configurazione della pianificazione per controllare lo stato ogni due minuti.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">Configurare l’Cloud Service Acrobat Sign del sito di riferimento</a></td> 
   <td>Creazione e pubblicazione<br /> </td> 
   <td>Configurazione fornita con pacchetti di siti di riferimento e che richiede la riconfigurazione con credenziali valide.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">Configurazione del servizio di configurazione comune Forms per gli utenti anonimi</a></td> 
   <td>Pubblicazione</td> 
   <td>La configurazione consente l’invio, la firma e la generazione di documenti di record per gli utenti anonimi.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">Modificare il file Swagger del servizio residuo per il modello dati del modulo</a></td> 
   <td>Creazione e pubblicazione<br /> </td> 
   <td>Modifica il servizio per il tuo ambiente.</td> 
  </tr> 
 </tbody> 
</table>

## Installare e configurare AEM Forms {#install-and-configure-aem-forms}

Installa e distribuisci AEM Forms come descritto in [Installazione e configurazione di AEM Forms su OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md).

>[!NOTE]
>
>Configura gli agenti di replica e di replica inversa se ci sono più istanze di pubblicazione o di authoring e pubblicazione su computer diversi.

## Configurare SSL {#ssl}

La configurazione SSL è necessaria per comunicare con i server Acrobat Sign. Per i passaggi dettagliati vedi [Abilitazione di HTTP su SSL](/help/sites-administering/ssl-by-default.md).

>[!CAUTION]
>
>Non configurare Forza SSL su `/etc/map` cartella.

## Configurare la configurazione Day CQ Link Externalizer {#externalizer}

In AEM, il **Esternalizzatore** è un servizio OSGI che consente di trasformare programmaticamente un percorso di risorsa (ad esempio, /path/to/my/page) in un URL esterno e assoluto (ad esempio, https://www.mycompany.com/path/to/my/page) prefissando il percorso con un DNS preconfigurato. Vedi [Esternalizzazione degli URL](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>Non esternalizzare l’URL HTTPS se utilizzi un certificato autofirmato per SSL.
>
>Inoltre, utilizza localhost invece del relativo nome host per il server locale.

Esegui i seguenti passaggi sia sulle istanze di creazione che di pubblicazione:

1. Vai alla configurazione OSGi all&#39;indirizzo https://&lt;*hostname>*:&lt;*porta>*/system/console/configMgr.
1. Trova e tocca **[!UICONTROL Day CQ Link Externalizer]** configurazione.

   Viene visualizzata la finestra di dialogo Day CQ Link Externalizer (Esternalizzatore di collegamento Day CQ) per modificare la configurazione.

1. Nella finestra di dialogo Day CQ Link Externalizer, nel campo Domains (Domini):

   * Nell’istanza di authoring, specifica un URL di pubblicazione a cui è possibile accedere da un sistema esterno. Ad esempio, un nome host o un server Web di pubblicazione.
   * Nell’istanza di pubblicazione, specifica gli URL di authoring e di pubblicazione.

1. Sia nelle istanze di authoring che di pubblicazione, accertati che l’URL del server locale sia specificato nel campo Domini .
1. Tocca **[!UICONTROL Salva]**. Attendi il riavvio di tutti i servizi.

## Configura il servizio di posta CQ Day {#cqmail}

L’implementazione del sito di riferimento richiede l’invio di e-mail agli utenti di esempio al momento della compilazione e dell’invio dei moduli. La configurazione di Day CQ Mail Service consente di fornire i dettagli del servizio SMTP per inviare e-mail automatizzate ai clienti. Vedi [Configurazione delle notifiche e-mail](/help/sites-administering/notification.md).

Esegui i seguenti passaggi per configurare il servizio di posta nell’istanza di pubblicazione:

1. Vai alla configurazione OSGi all&#39;indirizzo https://&lt;*hostname>*:&lt;*porta>*/system/console/configMgr.
1. Trova e tocca **[!UICONTROL Servizio e-mail Day CQ]** per aprirlo per la configurazione.
1. Fornire i valori dell’host del server SMTP e della porta.
1. Tocca **[!UICONTROL Salva]**.

>[!NOTE]
>
>Puoi utilizzare il tuo servizio SMTP aziendale o i servizi pubblici come Gmail. Per la configurazione del servizio SMTP, vedere la documentazione del servizio SMTP.

## Ignora configurazione XSS predefinita {#xss}

I modelli e-mail per il sito di riferimento We.Finance contengono collegamenti personalizzati nelle e-mail. Questi collegamenti hanno un segnaposto come `${placeholder}`. Questi segnaposto vengono sostituiti dai valori effettivi prima dell’invio delle e-mail. La configurazione di protezione XSS predefinita per AEM non consente parentesi graffe (**{ }**) nell’URL nel contenuto di HTML. Tuttavia, puoi ignorare la configurazione predefinita eseguendo i seguenti passaggi sull’istanza di pubblicazione:

1. Copia `/libs/cq/xssprotection/config.xml` a `/apps/cq/xssprotection/config.xml`.
1. Apri `/apps/cq/xssprotection/config.xml`.
1. In `common-regexps` sezione, modifica `onsiteURL` inserisci come segue e salva il file .

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>Parentesi graffe (**{ }**) sono inclusi come caratteri accettati nell’URL nel contenuto di HTML.

Dopo aver configurato il server SMTP, prova a compilare un modulo utilizzando la persona Sarah Rose e salvalo come bozza. Quando salvi come bozza, ottieni un’opzione per ricevere la bozza utilizzando l’e-mail. Al tocco di **Invia e-mail** Se ricevi un’e-mail con un collegamento alla bozza dell’applicazione, la configurazione dell’e-mail avrà esito positivo. Assicurati di accedere utilizzando le credenziali di Sarah per visualizzare la bozza.

## Configurare le impostazioni di AEM DS {#aemds}

AEM le impostazioni del servizio DS sono necessarie nell&#39;istanza Pubblica per le comunicazioni e-mail nei casi di utilizzo del sito di riferimento. Per i passaggi dettagliati per la configurazione AEM configurazione del servizio DS sull&#39;istanza Publish, vedi [Configurare le impostazioni di AEM DS](/help/forms/using/configuring-the-processing-server-url-.md).

Per i siti di riferimento AEM Forms, nel servizio Impostazioni DS AEM, specifica l&#39;URL del server di pubblicazione invece dell&#39;URL del server di elaborazione.

>[!CAUTION]
>
>Non mettere `/lc` nell’URL del server di elaborazione se lo stai configurando per AEM Forms OSGi.

## Distribuire pacchetti di siti di riferimento {#refsite}

Installa i seguenti pacchetti siti di riferimento utilizzando Distribuzione di software.

* [AEM-FORMS-6.4-FSI-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

Per ulteriori informazioni sull’utilizzo dei pacchetti, consulta [Come lavorare con i pacchetti](/help/sites-administering/package-manager.md).

Dopo aver installato i pacchetti e avviato le istanze di authoring e pubblicazione, visita i seguenti URL nel browser:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

Se l’installazione ha esito positivo, puoi accedere alle pagine di destinazione dei siti di riferimento We.Gov e We.Finance.

## (Facoltativo) Importare dati di esempio in Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

I siti di riferimento per l’applicazione di mutui per la casa e l’applicazione di assicurazione automatica sono configurati per utilizzare i record di Microsoft Dynamics. Il pacchetto del sito di riferimento installa un&#39;entità personalizzata e record di esempio che puoi importare in Microsoft Dynamics per eseguire il sito di riferimento. Esegui i seguenti passaggi per eseguire la migrazione e impostare i dati di esempio:

Per importare l&#39;entità personalizzata per l&#39;applicazione di assicurazione automatica:

1. Scarica la **WeFinanceAutoInsurance_1_0.zip** pacchetto di soluzioni da `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` sull’istanza di authoring AEM.
1. Nella tua istanza di Microsoft Dynamics, vai a **[!UICONTROL Soluzioni]** in **[!UICONTROL Impostazioni]** menu e fai clic su **[!UICONTROL Importa]**. Seleziona e importa il pacchetto.

Per importare l&#39;entità personalizzata per l&#39;applicazione di assicurazione automatica:

1. Scarica la **AEMFormsFSIRefsite_1_0.zip** pacchetto da https://[autore]:[porta]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip. Seleziona e importa il pacchetto.

1. Nella tua istanza di Microsoft Dynamics, vai a **[!UICONTROL Soluzioni]** in **[!UICONTROL Impostazioni]** menu e fai clic su **[!UICONTROL Importa]**. Seleziona e importa il pacchetto.

Per importare i record dei contratti di assicurazione e cliente:

1. Scarica la **Clienti We.Finance.csv, We.Finance Auto Insurance Renewals.csv** e **mutuo ipotecario** file di dati dalle seguenti posizioni nell’istanza di authoring di AEM:

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Nell’istanza di Microsoft Dynamics, procedi come segue:

   * Vai a **[!UICONTROL Vendite > Clienti We.Finance]** e fai clic su **[!UICONTROL Importa]**.
   * Vai a **[!UICONTROL Vendite > Assicurazione automatica We.Finance]** e fai clic su **[!UICONTROL Importa]**.
   * Vai a **[!UICONTROL Vendite > We.Finance Home Mutuo]**  e fai clic su **[!UICONTROL Importa]**.

## Configurazione del servizio cloud OAuth per Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}

Configura il servizio cloud OAuth in AEM Forms per abilitare la comunicazione tra AEM Forms e Microsoft Dynamics. Esegui i seguenti passaggi per configurare il Cloud Service OAuth su AEM istanze di authoring e pubblicazione:

1. Su AEM&#39;istanza dell&#39;autore, vai a **[!UICONTROL Strumenti > Cloud Services > Origini dati > globale]**. Tocca **[!UICONTROL Integrazione con Refsite Dynamics]** icona e tocco **[!UICONTROL Proprietà]**.
1. Passa all’account Microsoft Azure Active Directory. Aggiungi l’URL di configurazione del servizio cloud copiato nel **[!UICONTROL URL di risposta]** impostazione per l&#39;applicazione registrata. Salva la configurazione.
1. Nella scheda Impostazioni autenticazione , specifica **[!UICONTROL Directory principale servizio]**, **[!UICONTROL ID client]**, **[!UICONTROL Segreto client]** e **[!UICONTROL URL risorsa]** per la tua istanza di Microsoft Dynamics. Fai clic su **[!UICONTROL Connettiti a OAuth]** reindirizza alla pagina di accesso di Microsoft Dynamics.
1. Immetti le credenziali di accesso. Una volta effettuato l’accesso, verrai reindirizzato alla pagina di configurazione del servizio cloud AEM Forms. Fai clic su **[!UICONTROL Salva e chiudi]**. La configurazione del servizio cloud viene salvata.
1. Vai a **[!UICONTROL Forms > Integrazioni dati > We.Finance]**. Selezionare Assicurazione automatica (Dynamics) e fare clic su Modifica. Le entità di Microsoft Dynamics sono elencate nella scheda Origini dati . Attendi che tutte le entità vengano recuperate da Microsoft Dynamics ed elencate nella scheda origini dati.
1. Seleziona la **[!UICONTROL Entità AutoInsuranceRenewal]** e fai clic su **[!UICONTROL Oggetto modello di test]**. Nella sezione richiesta di input, specifica il valore per l’ID cliente come &quot;900001&quot; e fai clic su **[!UICONTROL Test]**. Nella sezione Output vengono visualizzati i record recuperati da Microsoft Dynamics per l’ID cliente 90001.
1. Nella sezione richiesta di input, specifica il valore per l’ID cliente come &quot;900001&quot; e fai clic su **[!UICONTROL Test]**. Nella sezione Output vengono visualizzati i record recuperati da Microsoft Dynamics per l’ID cliente 90001.
1. Ripeti i passaggi 1-6 sull’istanza di pubblicazione.

## Configurare Acrobat Sign Scheduler {#scheduler}

Esegui le seguenti operazioni sia sulle istanze di authoring che di pubblicazione:

1. Vai AEM console Configurazione Web all&#39;indirizzo `https://[server]:[host]/system/console/configMgr`.
1. Trova e tocca **[!UICONTROL Servizio di configurazione di Acrobat Sign]** per aprirlo per la configurazione.
1. Configura **[!UICONTROL Espressione di pianificazione dell&#39;aggiornamento dello stato]** come **0 0/2 &amp;ast; &amp;ast; &amp;ast; ?**.

   >[!NOTE]
   >
   >La configurazione di pianificazione di cui sopra controlla lo stato del servizio Acrobat Sign ogni due minuti.

1. Tocca **[!UICONTROL Salva]**.

## Configurare il sito di riferimento Acrobat Sign Cloud Service {#sign-service}

Esegui le seguenti operazioni sia sulle istanze di authoring che di pubblicazione:

1. Vai a **[!UICONTROL Strumenti > Cloud Services > Acrobat Sign > globale]**. Seleziona **[!UICONTROL Firma del sito di riferimento AEM Forms]** e toccare **[!UICONTROL Proprietà]**.

   >[!CAUTION]
   >
   >Assicurati che https://[host]:[ssl_port]L’URL /mnt/overlay/adobesign/cloudservices/adobesign/properties.html viene aggiunto all’elenco degli URL di reindirizzamento della configurazione OAuth dell’applicazione API di Acrobat Sign.

1. Specifica l’ID client e il segreto della configurazione OAuth dell’applicazione Acrobat Sign.
1. (Facoltativo) Seleziona la **[!UICONTROL Abilita anche Acrobat Sign per gli allegati]** e tocca **[!UICONTROL Connettersi ad Acrobat Sign]**. Aggiunge i file allegati a moduli adattivi al documento Acrobat Sign corrispondente inviato per la firma.
1. Tocca **[!UICONTROL Connettersi ad Acrobat Sign]** e accedi con le tue credenziali Acrobat Sign.

## Configurare il servizio di configurazione comune Forms {#anonymous}

Per consentire l’accesso agli utenti anonimi, procedi come segue nell’istanza di pubblicazione:

1. Vai AEM console Configurazione Web all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
1. Trova e tocca **[!UICONTROL Servizio di configurazione comune Forms]** per aprirlo per la configurazione.
1. Configura le **[!UICONTROL Consenti]** campo per **[!UICONTROL Tutti gli utenti]**.
1. Tocca **[!UICONTROL Salva]**.

## Modifica del servizio di riposo per il modello dati del modulo {#fdm}

Esegui le seguenti operazioni sia sulle istanze di authoring che di pubblicazione:

1. Vai a CRXDE in `https://[server]:[port]/crx/de/index.jsp`.
1. Passa a **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** e aprire il file swagger.
1. Aggiorna le impostazioni dell&#39;host e della porta in base all&#39;ambiente.
1. Salva le impostazioni.
1. (**Solo istanza autore**) Vai a **[!UICONTROL Strumenti]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Origini dati]** > **[!UICONTROL globale]**. Seleziona **[!UICONTROL poggiatesta]** e toccare **[!UICONTROL Proprietà]**. Tocca **[!UICONTROL Impostazioni di autenticazione]** e impostare **[!UICONTROL Tipo di autenticazione]** a **[!UICONTROL Autenticazione di base]**. Specifica `admin`/ `admin`come nome utente/password per accedere al servizio. Tocca **[!UICONTROL Salva e chiudi]**.

## Integrare con il Marketing Cloud {#integrate-with-marketing-cloud}

Puoi integrare AEM Forms con Adobe Analytics e Adobe Target. Mentre Adobe Analytics consente di generare rapporti e analizzare le prestazioni dei moduli adattivi, Adobe Target consente di fornire esperienze personalizzate ed eseguire test A/B per i moduli adattivi.

Per configurare Adobe Analytics e Adobe Target in AEM Forms, procedi come segue.

### Configurare Adobe Analytics {#configure-adobe-analytics}

L’integrazione di AEM Forms con Adobe Analytics consente di monitorare e analizzare il modo in cui i clienti interagiscono con i moduli e i documenti. Ti aiuta a identificare e correggere le aree problematiche e ad agire per aumentare il tasso di conversione.

Per utilizzare questa funzionalità nel sito di riferimento, configura l’account Analytics come descritto in [Configurazione di analisi e rapporti](/help/forms/using/configure-analytics-forms-documents.md).

Per generare un rapporto, i dati seed vengono raggruppati con i siti di riferimento. Prima di utilizzare i dati di seed, procedi come segue:

1. Assicurati che le configurazioni di analisi We.Finance e We.Gov siano disponibili in AEM Cloud Services. Puoi trovare servizi cloud in uno dei seguenti modi:

   * Passa a **[!UICONTROL Strumenti>Cloud Services>Cloud Services legacy]** oppure vai su https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html.
   * In **[!UICONTROL Cloud Services]** pagina, sotto **[!UICONTROL Adobe Analytics]** sezione, fai clic su `Show Configurations`. Puoi vedere le configurazioni We.Finance e We.Gov disponibili. Fai clic su per aprire la configurazione. Nella pagina di configurazione, fai clic su **[!UICONTROL Modifica]**. Fornire una società, un nome utente, un segreto condiviso (password) e un centro dati validi e fare clic su **[!UICONTROL Connettersi ad Analytics]**. Una volta visualizzata la finestra di dialogo Connessione riuscita, fai clic su **[!UICONTROL OK]** nella finestra di dialogo di configurazione. Configura il framework nella configurazione di Analytics come descritto in [Configurazione di Analytics e Report](/help/forms/using/configure-analytics-forms-documents.md).

1. Vai su https://&lt;*host*>:&lt;*porta*>/system/console/configMgr e procedi come segue:

   * In **[!UICONTROL Configurazione della console Web]** pagina, trova e fai clic su **[!UICONTROL Configurazione di AEM Forms Analytics]**.
   * In **[!UICONTROL Quadro SiteCatalyst]** nella finestra di dialogo Configurazione di AEM Forms Analytics, seleziona we-finance(we-finance) o we-gov(we-gov).
   * Fai clic su **[!UICONTROL Salva]** e consente l’aggiornamento della pagina.

1. Passa a Forms Manager all’indirizzo https://&lt;host>:&lt;port>/aem/forms e procedi come segue:

   * Aprire la cartella We.Finance o We.Gov e selezionare il modulo per il quale si desidera visualizzare il rapporto.
   * Fai clic su Abilita Analytics nella barra degli strumenti Azioni. Dopo aver abilitato Analytics per il modulo, fai clic su Rapporto Analytics . È possibile visualizzare un rapporto vuoto generato. Dopo aver generato un rapporto vuoto, devi fornire i dati seed forniti con pacchetto refsite per generare un rapporto di analisi a scopo dimostrativo.

   I siti di riferimento forniscono rapporti di analisi con dati iniziali per i casi di utilizzo di carte di credito, mutui per la casa e assistenza ai bambini. Per la configurazione dei dati di seed, vedi [Procedura dettagliata sul sito di riferimento We.Finance](/help/forms/using/finance-reference-site-walkthrough.md) e [Procedura dettagliata sul sito di riferimento We.Gov](/help/forms/using/gov-reference-site-walkthrough.md).

### Configurare Target {#configure-target}

Il sito di riferimento mostra l’integrazione di AEM Forms con Adobe Target che consente di includere contenuti mirati e personalizzati nei documenti adattivi. Consente inoltre di creare test A/B per i moduli adattivi.

Per provare l’integrazione nel sito di riferimento, procedi come segue per configurare Target in AEM:

1. Avvia l&#39;avvio rapido dell&#39;autore con l&#39;argomento jvm `-Dabtesting.enabled=true` per abilitare il test A/B sul server.

   **Nota**: Se l&#39;istanza AEM è in esecuzione su JBoss, che viene avviato come servizio dall&#39;installazione di Turnkey, aggiungi la `-Dabtesting.enabled=true` nella seguente voce nel `jboss\bin\standalone.conf.bat` file :

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Accedi a https://&lt;*hostname*>:&lt;*porta*>/libs/cq/core/content/tools/cloudservices.html.

1. In **[!UICONTROL Adobe Target]** sezione, fai clic su **[!UICONTROL Mostra configurazioni]**. È possibile visualizzare la configurazione di destinazione We.Finance disponibile. Fai clic su per aprire la configurazione. Nella pagina di configurazione, fai clic su **[!UICONTROL Modifica]**. La **[!UICONTROL Modifica componente]** viene visualizzata la finestra di dialogo per la configurazione.

1. Specifica il codice client, l’e-mail e la password associati all’account Target. Seleziona il tipo di API come **[!UICONTROL REST]**.
1. Fai clic su **[!UICONTROL Connetti a destinazione Adobe]**. Una volta configurato correttamente l’account Target, fai clic su **[!UICONTROL OK]**. Puoi vedere che la configurazione del pacchetto ha un framework di Target.

1. Vai su https://&lt;*hostname*>:&lt;*porta*>/system/console/configMgr.

1. Fai clic su **[!UICONTROL Configurazione di AEM Forms Target]**.
1. Seleziona un framework di Target.
1. In **[!UICONTROL URL di destinazione]** specifica l’URL di AEM Forms. Ad esempio: https://&lt;*hostname*>:&lt;*porta*>

1. Fai clic su **[!UICONTROL Salva]**.

I casi d&#39;uso di applicazioni con carta di credito e ipoteche domestiche dimostrano come eseguire test A/B e mostrare un rapporto a scopo dimostrativo. Per informazioni dettagliate, consulta [Procedura dettagliata sul sito di riferimento We.Finance](/help/forms/using/finance-reference-site-walkthrough.md).

## Passaggio successivo {#next-step}

Ora siete tutti impostati per esplorare il sito di riferimento. Per ulteriori informazioni sul flusso di lavoro e sui passaggi del sito di riferimento, consulta:

* [Procedura dettagliata sul sito di riferimento We.Finance](/help/forms/using/finance-reference-site-walkthrough.md)
* [Procedura dettagliata sul sito di riferimento We.Gov](/help/forms/using/gov-reference-site-walkthrough.md)

* [Procedura dettagliata sul sito di riferimento self-service dei dipendenti](/help/forms/using/employee-self-service-reference-site.md)
