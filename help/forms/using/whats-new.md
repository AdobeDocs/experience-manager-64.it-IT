---
title: Riepilogo delle nuove funzioni| Moduli AEM 6.4
seo-title: Riepilogo delle nuove funzioni| Moduli AEM 6.4
description: Riepilogo delle nuove funzioni e dei miglioramenti in AEM 6.4 Forms.
seo-description: Riepilogo delle nuove funzioni e dei miglioramenti in AEM 6.4 Forms.
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
translation-type: tm+mt
source-git-commit: 715cff841252d79504d702817f91db92df919bfc

---


# Riepilogo delle nuove funzioni| Moduli AEM 6.4 {#new-features-summary-aem-forms}

Riepilogo delle nuove funzioni e dei miglioramenti in AEM 6.4 Forms.

AEM Forms include diverse nuove funzioni e miglioramenti che semplificano ulteriormente la creazione, la gestione e l&#39;esperienza utente con moduli adattivi e comunicazioni interattive.

Continua a leggere per una breve introduzione a nuove funzioni e miglioramenti. Per informazioni dettagliate sulle risorse, consultate la documentazione. Inoltre, consultate [Note](/help/release-notes/forms.md)sulla versione per moduli AEM 6.4. Per la documentazione completa sui moduli di AEM 6.4, consultare la guida [utente ai moduli di](/help/forms/home.md)AEM 6.4.

## Comunicazioni interattive {#interactive-communications}

![gestione della corrispondenza](assets/correspondence-management.png)

Le comunicazioni interattive centralizzano e gestiscono la creazione, l&#39;assemblaggio e la distribuzione di corrispondenza sicura, personalizzata e interattiva come corrispondenza aziendale, lettere, documenti, dichiarazioni, note sui benefit, prospetto di gestione patrimoniale, e-mail di marketing, fatture e kit di benvenuto.

Le comunicazioni interattive utilizzano la stessa tecnologia, gli stessi processi e gli stessi componenti di base dei moduli adattivi, per creare comunicazioni multicanale reattive, come i moduli adattivi reattivi.

La comunicazione interattiva offre vantaggi significativi:

* Fornisce l&#39;integrazione OOTB con il modello dati del modulo per consentire un accesso semplice e semplificato ai database back-end e ad altri sistemi CRM come MS Dynamics
* Offre un&#39;interfaccia di authoring integrata per canali Web e di stampa
* Offre un’interfaccia di creazione basata su trascinamento, simile all’authoring di moduli adattivi, per canali Web e per la stampa.

La comunicazione interattiva è l&#39;approccio predefinito e consigliato per creare comunicazioni con i clienti. Per continuare a utilizzare le lettere in AEM 6.3 Forms e AEM 6.2 Forms, è necessario installare un pacchetto di compatibilità.

### Authoring di comunicazioni interattive multicanale {#multi-channel-interactive-communication-authoring}

Utilizzando la comunicazione interattiva, potete creare e modificare documenti sia per la stampa che per il Web da un singolo editor di documenti. Utilizzando gli stessi frammenti di documento per creare rappresentazioni di entrambi i canali, è possibile evitare duplicazioni.
![printweb_2](assets/printweb_2.png)

Per ulteriori informazioni, consulta Panoramica [sulle comunicazioni](/help/forms/using/interactive-communications-overview.md)interattive.

### Editor documenti WYSIWYG {#wysiwyg-document-editor}

L&#39;editor di documenti con trascinamento WYSIWYG è semplice da usare. L&#39;interfaccia intuitiva, la funzionalità di trascinamento della selezione, componenti standard, modelli di dati e repository integrato per le risorse semplificano l&#39;authoring rapido e semplice delle comunicazioni interattive.

Per creare una comunicazione interattiva o modificare una comunicazione esistente, gli utenti aziendali possono utilizzare i seguenti blocchi costitutivi: Canali, contenuto, proprietà, risorse, componenti e origini dati.

![drag-n-drop-lf](assets/drag-n-drop-lf.png)

Per ulteriori informazioni, consulta [Introduzione alla creazione di comunicazioni](/help/forms/using/introduction-interactive-communication-authoring.md)interattive.

### Generazione automatica della versione Web dal contenuto stampato nelle comunicazioni interattive {#auto-generate-web-version-from-print-content-in-interactive-communication}

Gli autori possono generare automaticamente contenuti di documenti Web dai documenti stampati per creare, visualizzare in anteprima e modificare documenti sia per la stampa che per il Web nello stesso editor. Gli autori delle comunicazioni interattive possono creare una volta e pubblicare contenuti su tutti i canali. Gli autori delle comunicazioni interattive possono utilizzare gli stessi frammenti di documento nei canali Web e per la stampa per evitare duplicazioni.

Per ulteriori informazioni, vedere Canale di [stampa e canale](/help/forms/using/web-channel-print-channel.md)Web.

### Utilizzare i temi per personalizzare il canale web della comunicazione interattiva {#use-themes-to-style-web-channel-of-interactive-communication}

La comunicazione interattiva supporta i temi. Potete creare temi e applicarli alla comunicazione interattiva. Un tema contiene dettagli di stile per componenti e pannelli. Potete riutilizzare un tema su diverse comunicazioni interattive per conferire loro un aspetto e un marchio comuni e coerenti.

AEM Forms include un tema preconfigurato per le comunicazioni interattive. Utilizzando un tema, potete anche personalizzare l&#39;aspetto di una comunicazione interattiva su un dispositivo.

Per ulteriori informazioni, consultate [Temi in AEM Forms](/help/forms/using/themes.md).

### Interfaccia agente avanzata {#enhanced-agent-interface}

L&#39;interfaccia utente Agent ora supporta la stampa e l&#39;anteprima Web della comunicazione interattiva. Dalla stessa interfaccia utente Agent, potete scegliere di modificare il canale di stampa e visualizzare in anteprima il canale Web della comunicazione interattiva multicanale. Campi, variabili, elementi FDM e frammenti di documento nel canale di stampa possono essere configurati in modo che vengano modificati dall&#39;agente nell&#39;interfaccia utente dell&#39;agente. Il supporto per i modelli di dati modulo consente di generare anteprime con dati di esempio precompilati.

Per ulteriori informazioni, vedi [Preparare e inviare comunicazioni interattive utilizzando l&#39;interfaccia utente](/help/forms/using/prepare-send-interactive-communication.md)agente.

### Presentare informazioni nei grafici {#present-information-in-charts}

La comunicazione interattiva supporta grafici in rete e nel canale di stampa per comunicazioni più ricche. Utilizzando grafici come torta, ciambella, barra e colonna, potete condensare e presentare visivamente grandi quantità di informazioni per una facile interpretazione e analisi.

![grafico-2](assets/chart-2.png) ![grafico](assets/chart.png)

Per ulteriori informazioni, consulta [Utilizzo dei grafici nelle comunicazioni](/help/forms/using/chart-component-interactive-communications.md)interattive.

### Connettori dati forniti per precompilare i documenti {#out-of-the-box-data-connectors-to-prefill-documents}

La comunicazione interattiva fornisce l&#39;integrazione dei dati con strumenti aziendali per la connessione a più sistemi aziendali, inclusi i sistemi CRM, e la personalizzazione dei dati nei documenti.

![fdm_ad](assets/fdm_ad.png)

Per ulteriori informazioni, vedere [Uso del modello](/help/forms/using/using-form-data-model.md)dati del modulo.

### Editor frammento di documento avanzato {#enhanced-document-fragment-editor}

È ora possibile utilizzare elementi e regole FDM all&#39;interno di frammenti di documento della comunicazione interattiva.

* Supporto per gli elementi del modello dati del modulo
* Mostrare o nascondere una risorsa/un frammento di testo utilizzando le regole
* Convalida del valore di un elemento/variabile
* Eseguire funzioni per calcolare il valore di un&#39;espressione matematica

Per ulteriori informazioni, vedere:

* [Testi nelle comunicazioni interattive](/help/forms/using/texts-interactive-communications.md)
* [Condizioni nelle comunicazioni interattive](/help/forms/using/conditions-interactive-communications.md)

### Pacchetto di compatibilità per le risorse esistenti {#compatibility-package-for-existing-assets}

Per impostazione predefinita, le risorse Lettera dalle versioni precedenti di AEM Forms non sono supportate in questa versione. Se si intende continuare a utilizzare le lettere da AEM 6.3 Forms e AEM 6.2 Forms, è necessario installare il pacchetto Compatibilità.

## Integrazione dei dati {#data-integration}

![](do-not-localize/data-integeration-1.png)

[L&#39;integrazione](/help/forms/using/data-integration.md) dei dati di AEM Forms consente di configurare origini dati diverse; come i database, i servizi Web basati su RESTful o SOAP e i servizi OData; per creare un modello dati modulo da utilizzare per eseguire il binding dei dati, precompilare e richiamare i servizi nei moduli e nei documenti adattivi.

Questa versione offre diverse nuove funzioni e miglioramenti nell&#39;integrazione dei dati.

### Crea modello dati modulo senza origine dati {#create-form-data-model-without-data-source}

Gli utenti aziendali e gli autori di moduli ora possono creare un modello dati del modulo con le relative entità e proprietà senza configurare un&#39;origine dati e possono essere utilizzati per creare moduli e documenti adattivi. È possibile eseguire un binding del modello dati del modulo con le origini dati in un secondo momento. Elimina le dipendenze dalle origini dati per la creazione di moduli e documenti utilizzando il modello dati del modulo.

Allo stesso modo, è possibile creare entità e proprietà secondarie in un modello dati del modulo esistente e associarle successivamente alle entità e proprietà corrispondenti in un&#39;origine dati.

Per ulteriori informazioni, vedere [Creazione di un modello](/help/forms/using/create-form-data-models.md)dati del modulo.

### Creare proprietà calcolate {#create-computed-properties}

Gli autori e gli sviluppatori di moduli possono creare proprietà calcolate nel modello dati del modulo. Consentono di calcolare un valore per la proprietà creando regole o logiche sui dati disponibili nelle origini dati configurate. Una regola è un&#39;espressione che viene valutata quando i dati vengono caricati nel modello dati del modulo o i valori delle proprietà nell&#39;espressione cambiano. Ad esempio, una proprietà calcolata denominata Installazioni calcola l&#39;importo mensile da pagare per un prestito in base al tasso di interesse specificato nell&#39;origine dati e all&#39;importo e alla durata del prestito specificati dall&#39;utente nel modulo.

Una proprietà calcolata risiede localmente in un modello dati modulo e non esiste in un&#39;origine dati. È possibile utilizzare le proprietà calcolate nei moduli adattivi e nelle comunicazioni interattive.

Per ulteriori informazioni, vedere [Uso del modello](/help/forms/using/work-with-form-data-model.md)dati del modulo.

### Anteprima di moduli e documenti con dati di esempio {#preview-forms-and-documents-with-sample-data}

Il modello dati modulo consente di generare dati di esempio per le proprietà di tutte le entità in un modello dati del modulo. I dati generati corrispondono ai tipi di dati configurati per le proprietà. Quando si visualizza l&#39;anteprima di un modulo adattivo o di un documento associato al modello dati del modulo, viene eseguito il rendering con dati di esempio precompilati.

I dati di esempio sono un insieme di valori casuali che vengono modificati ogni volta che vengono generati. Tuttavia, potete modificare e salvare i dati di esempio che persistono anche se li rigenerate. Ad esempio, se si modificano e salvano i dati di esempio per le proprietà Nome e Cognome e successivamente si aggiunge un&#39;altra proprietà o entità nel modello dati del modulo e si rigenerano i dati di esempio, le proprietà Nome e Cognome mostreranno i valori salvati mentre i valori per altre proprietà vengono rigenerati.

Per informazioni dettagliate, vedere [Uso del modello](/help/forms/using/using-form-data-model.md)dati del modulo.

### Refresh data source definitions {#refresh-data-source-definitions}

Qualsiasi aggiornamento nelle entità o proprietà dell&#39;origine dati non si riflette automaticamente nei modelli di dati dei moduli associati. L&#39;editor del modello dati del modulo ora dispone di ![refresh_forms_di](assets/refresh_forms_di.png) (Aggiorna definizioni origine dati) che invalida la cache del server e recupera lo schema aggiornato dall&#39;origine dati per riflettere immediatamente nel modello dati del modulo.

### Configurare le origini dati utilizzando l&#39;interfaccia Touch {#configure-data-sources-using-touch-user-interface}

Con questa versione, la configurazione dei servizi cloud per le origini dati è disponibile nell&#39;interfaccia Touch. Inoltre, la posizione in cui configurare i servizi cloud è stata modificata in **[!UICONTROL Strumenti > Servizi cloud > Origini]** dati. See [Configure data sources](/help/forms/using/configure-data-sources.md).

## Moduli adattivi {#adaptive-forms}

![semplificazione delle procedure di authoring-forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### Miglioramento delle prestazioni dei moduli adattivi con caricamento più lento {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

La funzionalità di caricamento pigro nei moduli adattivi posticipa l&#39;inizializzazione dei frammenti di modulo fino a quando non sono necessari. Migliora le prestazioni dei moduli di grandi dimensioni riducendo al minimo il tempo necessario per eseguire il rendering di un modulo e migliorando l&#39;esperienza dell&#39;utente.

In questa versione sono stati introdotti diversi miglioramenti alla funzione di caricamento pigro:

* I componenti allegati e termini e condizioni del file sono supportati nei frammenti di modulo con caricamento pigro abilitato.
* I frammenti di modulo adattivi con caricamento pigro abilitato sono supportati nei pannelli ripetibili.
* I moduli adattivi con frammenti abilitati per il caricamento pigro sono supportati nell&#39;app AEM Forms.

## Flussi di lavoro AEM incentrati sui moduli {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

Grazie alla funzionalità Flussi di lavoro AEM incentrati sui moduli, puoi creare e implementare rapidamente flussi di lavoro per varie attività nello stack OSGi. Non è più necessario installare la funzionalità Process Management disponibile nello stack JEE, semplificando la distribuzione ed eliminando i costi del server delle applicazioni e dell&#39;infrastruttura. Per ulteriori informazioni, vedere Flussi di lavoro incentrati sui [moduli in OSGi](/help/forms/using/aem-forms-workflow.md).

Di seguito sono riportati i miglioramenti apportati ai flussi di lavoro AEM incentrati sui moduli: ・

* L&#39;editor del modello di workflow è disponibile nell&#39;interfaccia Touch. Questo consente di ridurre il tempo necessario per creare flussi di lavoro AEM incentrati sui moduli.
* Passaggio del flusso di lavoro per l&#39;invio di e-mail. Ad esempio, potete utilizzare il passaggio e-mail per inviare un documento di record al completamento di un flusso di lavoro.
* Passaggio del flusso di lavoro per utilizzare i servizi del modello dati del modulo in un modello di workflow. Questo passaggio consente di richiamare i servizi di integrazione dei dati senza scrivere codice personalizzato. Ad esempio, potete richiamare un servizio GET per ottenere i dettagli dei dipendenti da un archivio di database senza scrivere codice personalizzato.

## App AEM Forms {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

L&#39;app AEM Forms consente ai lavoratori del campo di sincronizzare i dispositivi mobili con un server AEM Forms e di lavorare sui moduli. L&#39;applicazione funziona perfettamente quando il dispositivo è offline, salvando i dati localmente sul dispositivo e sincronizzando i dati con il server quando il dispositivo è nuovamente online. Per ulteriori informazioni, consultate App [](/help/forms/using/aem-forms-app.md)AEM Forms.

Seguono i miglioramenti nell&#39;app AEM Forms:

* I moduli adattivi con frammenti abilitati per il caricamento pigro sono supportati nell&#39;app AEM Forms.
* I moduli adattivi con il modello dati del modulo sono supportati nell&#39;app AEM Forms.

## Sicurezza dei documenti {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

La protezione dei documenti consente di distribuire in modo sicuro tutte le informazioni salvate in un formato supportato. La protezione dei documenti garantisce che solo gli utenti autorizzati possano utilizzare i documenti. Di seguito sono riportate le principali modifiche alla protezione dei documenti:

* Document Security fornisce una [Portable Protection Library (PPL)](/help/forms/using/document-security-offerings.md) per proteggere localmente un documento, senza inviarlo al server AEM Forms. Solo le credenziali di protezione e i dettagli dei criteri vengono trasferiti sulla rete al server AEM Forms. AEM 6.4 Forms ha introdotto la Portable Protection Library (PPL) in un formato bundle OSGi. Ora puoi installare direttamente la libreria PPL su un server AEM Forms e utilizzare le funzionalità di AEM e PPL in combinazione tra loro.
* È possibile compilare la libreria SDK C++ e PPL C++ con Microsoft Visual Studio 2013. La versione precedentemente supportata era Microsoft Visual Studio 2010.

## Piattaforme supportate {#supported-platforms}

I moduli AEM possono essere configurati utilizzando qualsiasi combinazione di sistemi operativi, server applicazione, database, driver di database, JDK, server LDAP e server e-mail supportati. Di seguito sono riportate le principali modifiche apportate alle piattaforme supportate:

<table> 
 <tbody> 
  <tr> 
   <td>Componente</td> 
   <td>Supporto aggiunto</td> 
   <td>Supporto rimosso</td> 
  </tr> 
  <tr> 
   <td>Sistemi operativi</td> 
   <td> 
    <ul> 
     <li>Microsoft Windows Server 2016</li> 
     <li>Aggiornamento 3 di Oracle Linux 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM AIX 7.2 <sup>[1]</sup><br /> </li> 
     <li>Solaris 11 <sup>[1]</sup></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Server applicazioni<br /> </td> 
   <td> 
    <ul> 
     <li>Red Hat JBoss EAP 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM Weblogic 12.1.3</li> 
     <li>IBM WebSphere 8.5.5</li> 
     <li>Red Hat JBoss EAP 6</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Database</td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2016</li> 
     <li>MySQL 5.7.19 e versioni successive</li> 
     <li>IBM DB2 11.1</li> 
     <li>Architettura Oracle Multittenant</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2012<br /> </li> 
     <li>Microsoft SQL Server 2014</li> 
     <li>MySQL 5.5</li> 
     <li>IBM DB2 10.5<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Server LDAP</td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2016</li> 
     <li>IBM Tivoli Directory Server 6.4</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2008</li> 
     <li>IBM Tivoli Directory Server 6.3</li> 
     <li>Oracle Directory Server Enterprise Edition 7.0</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Server e-mail</td> 
   <td> 
    <ul> 
     <li>Microsoft Office 365</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Novell Groupwise 7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Connettori</td> 
   <td> 
    <ul> 
     <li>Connettore per Microsoft SharePoint 2016</li> 
     <li>Connettore per EMC Documentum 7.3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Connettore per Microsoft SharePoint 2007</li> 
     <li>Connettore per Microsoft SharePoint 2010</li> 
     <li>Connettore per IBM Filenet 5.0</li> 
     <li>Connettore per EMC Documentum 6.7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Browser</td> 
   <td> 
    <ul> 
     <li>Apple Safari 11.x su macOS</li> 
     <li>Apple Safari 11.x su iOS</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Browser Blackberry per dispositivi Blackberry Z30 e Q10</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>AEM Forms app<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4 o versione successiva</li> 
     <li>Apple iOS 10 o versione successiva</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. I sistemi operativi AIX e Solaris sono disponibili solo per i clienti che effettuano l&#39;aggiornamento.
