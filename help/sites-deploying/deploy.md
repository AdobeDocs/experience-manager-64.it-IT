---
title: Implementazione e manutenzione
seo-title: Implementazione e manutenzione
description: Scoprite come iniziare a utilizzare l'installazione AEM.
seo-description: Scoprite come iniziare a utilizzare l'installazione AEM.
uuid: 552a41a1-a8b3-4c5a-bfb3-718bcb612752
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 6696c325-d188-41c8-a39f-c8ae7f339fe8
translation-type: tm+mt
source-git-commit: e7da0bb7906c3ad3d04531db0abfbc658646f6e4
workflow-type: tm+mt
source-wordcount: '1835'
ht-degree: 7%

---


# Implementazione e manutenzione{#deploying-and-maintaining}

In questa pagina troverai:

* [Concetti di base](#basic-concepts)

   * [Che cos’è AEM?](#what-is-aem)
   * [Implementazioni tipiche](#typical-deployment-scenarios)

      * [In sede](#on-premise)
      * [Managed Services tramite Cloud Manager](#managed-services-using-cloud-manager)

* [Guida introduttiva](#getting-started)

   * [Prerequisiti](#prerequisites)
   * [Ottenimento del software](#getting-the-software)
   * [Installazione locale predefinita](#default-local-install)
   * [Installazione di Author e Publish](#author-and-publish-installs)
   * [Directory di installazione non compressa](#unpacked-install-directory)
   * [Avvio e arresto](#starting-and-stopping)

Dopo aver acquisito familiarità con queste nozioni di base, nelle seguenti sottopagine troverai informazioni più avanzate e dettagliate:

* [Requisiti tecnici](/help/sites-deploying/technical-requirements.md)
* [Implementazioni consigliate](/help/sites-deploying/recommended-deploys.md)
* [Installazione personalizzata indipendente](/help/sites-deploying/custom-standalone-install.md)
* [Installazione dell’applicazione da server](/help/sites-deploying/application-server-install.md)
* [Risoluzione dei problemi](/help/sites-deploying/troubleshooting.md)
* [Avvio e interruzione da riga di comando](/help/sites-deploying/command-line-start-and-stop.md)
* [Configurazione](/help/sites-deploying/configuring.md)
* [Aggiornamento a AEM 6.4](/help/sites-deploying/upgrade.md)
* [eCommerce](/help/sites-deploying/ecommerce.md)
* [Articoli guida alla configurazione](/help/sites-deploying/ht-deploy.md)
* [Console Web](/help/sites-deploying/web-console.md)
* [Risoluzione dei problemi di replica](/help/sites-deploying/troubleshoot-rep.md)
* [Best practice  ](/help/sites-deploying/best-practices.md)
* [Implementazione di Communities](/help/communities/deploy-communities.md)
* [Introduzione alla piattaforma AEM](/help/sites-deploying/platform.md)
* [Linee guida sulle prestazioni](/help/sites-deploying/performance-guidelines.md)
* [Guida introduttiva di AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Cos&#39;è  AEM Screens?](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)

## Concetti di base {#basic-concepts}

### Che cos’è AEM? {#what-is-aem}

Adobe Experience Manager è un sistema client-server basato sul Web per la creazione, gestione e distribuzione di siti Web commerciali e di servizi correlati, che combina varie funzioni a livello di infrastruttura e di applicazione in un unico pacchetto integrato.

A livello di infrastruttura AEM fornisce quanto segue:

* **Server** applicazioni Web: AEM può essere implementato in modalità standalone (include un server Web Jetty integrato) o come applicazione Web all&#39;interno di un server applicazione di terze parti (WebLogic, WebSphere, ecc.).
* **Framework** applicazione Web: AEM incorpora Sling Web Application Framework che semplifica la scrittura di applicazioni Web RESTful orientate al contenuto.
* **Repository** contenuto: AEM include un JCR (Java Content Repository), un tipo di database gerarchico progettato specificamente per i dati non strutturati e semistrutturati. L&#39;archivio memorizza non solo il contenuto rivolto all&#39;utente, ma anche tutto il codice, i modelli e i dati interni utilizzati dall&#39;applicazione.

Sulla base di questa base, AEM offre anche una serie di funzionalità a livello di applicazione per la gestione di:

* **Siti Web**
* **Applicazioni mobili**
* **Pubblicazioni digitali**
* **Forms**
* **Risorse digitali**
* **Community**
* **Commerce online**

Infine, i clienti possono utilizzare questi blocchi di base a livello di infrastruttura e applicazione per creare soluzioni personalizzate creando applicazioni proprie.

Il server AEM è **Java-based** ed è eseguito sulla maggior parte dei sistemi operativi che supportano tale piattaforma. L&#39;interazione con AEM da parte del client viene eseguita tramite un **browser Web**.

### Scenari di distribuzione tipici {#typical-deployment-scenarios}

Nella terminologia AEM &quot;instance&quot; è una copia di AEM in esecuzione su un server. AEM installazioni in genere coinvolgono almeno due istanze, in genere eseguite su macchine separate:

* **Autore**: Istanza AEM utilizzata per creare, caricare e modificare i contenuti e amministrare il sito Web. Quando il contenuto è pronto per essere live, viene replicato nell’istanza di pubblicazione.
* **Pubblica**: Un&#39;istanza AEM che trasmette al pubblico il contenuto pubblicato.

Queste istanze sono identiche in termini di software installato. Sono differenziati solo per configurazione. Inoltre, la maggior parte delle installazioni utilizza un dispatcher:

* **Dispatcher**: Un server Web statico (Apache httpd, Microsoft IIS, ecc.) con il modulo dispatcher AEM. Memorizza nella cache le pagine Web prodotte dall’istanza di pubblicazione per migliorare le prestazioni.

Esistono molte opzioni ed elaborazioni avanzate di questa configurazione, ma il pattern di base di creazione, pubblicazione e dispatcher è al centro della maggior parte delle implementazioni. Cominceremo con l&#39;approccio relativamente semplice. Seguirà la discussione sulle opzioni di distribuzione avanzate.

Le sezioni seguenti descrivono entrambi gli scenari:

* **In sede**: AEM implementato e gestito nell&#39;ambiente aziendale.

* **Managed Services - Cloud Manager per Adobe Experience Manager**: AEM distribuito e gestito da Adobe Managed Services.

### In sede {#on-premise}

Puoi installare AEM sui server nel tuo ambiente aziendale. Le istanze di installazione tipiche includono: Ambienti di sviluppo, test e pubblicazione. Fare riferimento alla sezione [Guida introduttiva](/help/sites-deploying/deploy.md#getting-started) per informazioni di base su come ottenere il software AEM per installarlo localmente.

Per ulteriori informazioni sulle installazioni locali tipiche, fare riferimento a [Implementazioni consigliate](/help/sites-deploying/recommended-deploys.md).

### Managed Services con Cloud Manager {#managed-services-using-cloud-manager}

AEM Managed Services è una soluzione completa per la gestione dell&#39;esperienza digitale. Offre vantaggi della soluzione di distribuzione delle esperienze nel cloud, mantenendo al contempo tutti i vantaggi di controllo, sicurezza e personalizzazione derivanti da un&#39;installazione locale. AEM Managed Services consente ai clienti di avviarsi più rapidamente implementando sul cloud e basandosi sulle best practice e sul supporto  Adobe. Le organizzazioni e gli utenti aziendali possono coinvolgere i clienti in tempi limitati, promuovere quote di mercato e concentrarsi sulla creazione di campagne di marketing innovative, riducendo al contempo il carico sull&#39;IT.

Con AEM clienti Managed Services possono ottenere i seguenti vantaggi:

**Time to Market più rapido:** Grazie all&#39;infrastruttura cloud flessibile dei servizi gestiti Adobe, le organizzazioni possono pianificare, avviare e ottimizzare rapidamente le esperienze digitali di successo.  Adobe gestisce l&#39;architettura cloud senza bisogno di capitale aggiuntivo, hardware o software e  tecnici del successo cliente del Adobe, aiutando con AEM architettura, provisioning, personalizzazione per la connessione alle app back-end e procedure ottimali per il go-live.

**Prestazioni più elevate:** offre esperienze digitali affidabili per la vostra azienda con quattro opzioni di disponibilità del servizio: 99,5%, 99,9%, 99,95% e 99,99%. Inoltre, consente il backup automatico e modelli di disaster recovery multimodali per garantire affidabilità e gestione degli eventi.

**Costi IT ottimizzati:** una guida e un&#39;esperienza proattive aiutano le organizzazioni a rimanere aggiornate sull&#39;ultima versione di AEM.  Adobe Platinum Maintenance and Support è incluso automaticamente nelle nuove installazioni di AMS Enterprise/Basic, offrendo esperienza tecnica ed operativa per aiutare le organizzazioni a mantenere le proprie applicazioni mission critical. Le funzionalità Analytics o Target di base gratuite offrono un valore aggiuntivo, specialmente alle organizzazioni di mercato di fascia media con esigenze limitate di analisi e personalizzazione.

**Massima sicurezza:** garantisce la sicurezza fisica, di rete e dei dati a livello aziendale ospitando le applicazioni dei clienti in una struttura ad accesso limitato, dietro i sistemi firewall o all&#39;interno di un cloud privato virtuale. Include macchine virtuali a tenant singolo con crittografia solida dello storage dei dati, antivirali e isolamento dei dati.

**Cloud Manager**: Cloud Manager, parte dell&#39;offerta Adobe Experience Manager Managed Services è un portale self-service che consente alle organizzazioni di gestire autonomamente Adobe Experience Manager nel cloud. Include un&#39;integrazione continua all&#39;avanguardia e una pipeline di fornitura continua (CI/CD) che consente ai team IT e ai partner di implementazione di velocizzare la fornitura di personalizzazioni o aggiornamenti senza compromettere le prestazioni o la sicurezza. Cloud Manager è disponibile solo per  clienti di servizi gestiti di Adobe.

Per ulteriori informazioni su Cloud Manager e sulle relative risorse, consultare la [**Guida utente di Cloud Manager**](https://helpx.adobe.com/experience-manager/cloud-manager/user-guide.html).

## Guida introduttiva {#getting-started}

### Prerequisiti {#prerequisites}

Mentre le istanze di produzione vengono in genere eseguite su computer dedicati che eseguono un sistema operativo ufficialmente supportato (vedere [Requisiti tecnici](/help/sites-deploying/technical-requirements.md)), il server di Experience Manager  verrà eseguito su qualsiasi sistema che supporti [**Java Standard Edition 8**](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

Per scopi di familiarizzazione e per lo sviluppo su AEM è abbastanza comune utilizzare un&#39;istanza installata sul computer locale che esegue Apple OS X o versioni desktop di Microsoft Windows o Linux.

Sul lato client, AEM funziona con tutti i browser moderni (**Microsoft Edge**, **Internet Explorer** 11, **Chrome** 51+, **Firefox** 47+, **Safari** 8+) sia su computer desktop che su tablet . Per ulteriori informazioni, vedere [Piattaforme client supportate](/help/sites-deploying/technical-requirements.md#supported-client-platforms).

### Ottenimento del software {#getting-the-software}

I clienti con un contratto di manutenzione e assistenza valido dovrebbero aver ricevuto una notifica via e-mail con un codice e poter scaricare AEM dal sito Web [**licenze di Adobe**](https://licensing.adobe.com/). I partner commerciali possono richiedere l&#39;accesso per il download da [**spphelp@adobe.com**](mailto:spphelp@adobe.com).

Il pacchetto software AEM è disponibile in due moduli:

* **cq-quickstart-6.4.0.jar:** Un  ** jarfile eseguibile standalone che include tutto il necessario per iniziare a usare.

* **cq-quickstart-6.4.0.war:** Un file di  ** avviso per la distribuzione in un server applicazione di terze parti.

Nella sezione seguente viene descritta l&#39; **installazione autonoma**. Per informazioni dettagliate sull&#39;installazione di AEM in un server applicazione, vedere [Installazione del server applicazioni](/help/sites-deploying/application-server-install.md).

### Installazione locale predefinita {#default-local-install}

1. Creare una directory di installazione sul computer locale. Esempio:

   Percorso di installazione UNIX: **/opt/aem**

   Percorso di installazione di Windows: **`C:\Program Files\aem`**

   Analogamente, è comune installare istanze di esempio in una cartella direttamente sul desktop. In ogni caso ci riferiremo genericamente a questa posizione come:

   `<aem-install>`

   *Il percorso della directory del file deve essere composto solo da caratteri ASCII statunitensi.*

1. Inserire i file **jar** e **license** in questa directory:

   ```shell
   <aem-install>/
       cq-quickstart-6.4.0.jar
       license.properties
   ```

   Se non si fornisce un file `license.properties`, AEM reindirizzare il browser a una schermata **Benvenuti** all&#39;avvio, in cui è possibile immettere una chiave di licenza. È necessario richiedere una chiave di licenza valida dal  Adobe, se non ne è ancora disponibile una.

1. Per avviare l&#39;istanza in un ambiente GUI, fai doppio clic sul file **`cq-quickstart-6.4.0.jar`**.

   In alternativa, è possibile avviare AEM dalla riga di comando. Per una VM Java a 32 bit immettere quanto segue:

   ```shell
       java -Xmx1024M -jar cq-quickstart-6.4.0.jar
   ```

   Per una VM a 64 bit, immettere:

   ```shell
       java -XX:MaxPermSize=256m -Xmx1024M -jar cq-quickstart-6.4.0.jar
   ```

AEM alcuni minuti per rimuovere il pacchetto del file JAR, installarlo e avviare l&#39;installazione. La procedura di cui sopra comporta:

* un&#39;istanza **AEM author**
* in esecuzione su **localhost**
* sulla porta **4502**

Per accedere all’istanza, il browser deve:

**`http://localhost:4502`**

Il risultato nell&#39;istanza di creazione verrà configurato automaticamente per la connessione a un&#39;istanza di **pubblicazione** su **`localhost:4503`**.

### Installazioni di creazione e pubblicazione {#author-and-publish-installs}

L&#39;installazione predefinita (un&#39;istanza **author** su **`localhost:4502`**) può essere modificata semplicemente rinominando il file `jar` prima di avviarlo per la prima volta. Il pattern di denominazione è:

**`cq-<instance-type>-p<port-number>.jar`**

Ad esempio, rinominare il file in

**`cq-author-p4502.jar`**

e all&#39;avvio dell&#39;istanza di creazione verrà eseguita su **`localhost:4502`**.

Analogamente, potete rinominare e avviare il file

**`cq-publish-p4503.jar`**

restituirà un&#39;istanza di pubblicazione in esecuzione su **`localhost:4503`**.

Installate queste due istanze, ad esempio

`<aem-install>/author`e

**`<aem-install>/publish`**

Per ulteriori dettagli sulla personalizzazione dell&#39;installazione, consultate le seguenti risorse:

* [Installazione personalizzata indipendente](/help/sites-deploying/custom-standalone-install.md)
* [Modalità di esecuzione](/help/sites-deploying/configure-runmodes.md)

### Directory di installazione non compressa {#unpacked-install-directory}

Quando l&#39;avvio rapido viene avviato per la prima volta, si scomprime nella stessa directory in una nuova sottodirectory denominata `crx-quickstart`. Si conclude con quanto segue:

```xml
<aem-install>/
    license.properties
    cq-quickstart-6.4.0.jar
    crx-quickstart/
        app/
        bin/
        conf/
        launchpad/
        logs/
        metrics/        
        monitoring/
        opt/
        repository/
        threaddumps/
        eula-de_DE.html
        eula-en_US.html
        eula-fr_FR.html
        eula-ja_JP.html
        readme.txt
```

Se l’istanza è stata installata dall’interfaccia utente grafica, viene visualizzata automaticamente una finestra del browser e viene visualizzata anche una finestra dell’applicazione desktop con l’host e la porta dell’istanza e un interruttore di accensione/spegnimento:

![screen_shot_2018-04-05at91504am1](assets/screen_shot_2018-04-05at91504am1.png)

>[!NOTE]
>
>Se utilizzate i symlink, consultate [problemi relativi a symlink](https://helpx.adobe.com/experience-manager/kb/changing-symlink.html).

### Avvio e arresto di {#starting-and-stopping}

Una volta che AEM ha scompresso se stesso e avviato per la prima volta, facendo doppio clic sul file jar nella directory di installazione si avvia semplicemente l&#39;istanza, non la reinstalla.

Per arrestare l&#39;istanza dall&#39;interfaccia grafica, fare clic sull&#39;interruttore **on/off** nella finestra dell&#39;applicazione desktop.

È inoltre possibile arrestare e avviare AEM dalla riga di comando. Se l&#39;istanza è già stata installata per la prima volta, gli **script della riga di comando** si trovano nel seguente percorso:

**`<aem-install>/crx-quickstart/bin/`**

Questa cartella contiene i seguenti script Unix bash shell:

* **`start`**: Avvia l&#39;istanza
* `stop`: Interrompe l&#39;istanza
* **`status`**: Segnala lo stato dell’istanza
* **`quickstart`**: Utilizzato per configurare le informazioni di avvio, se necessario.

Esistono anche file **`bat`** equivalenti per Windows. Per ulteriori informazioni, consulta:

* [Avvio e interruzione da riga di comando](/help/sites-deploying/command-line-start-and-stop.md)

AEM viene avviato e reindirizzato automaticamente il browser Web alla pagina appropriata, in genere la pagina di accesso; ad esempio:

`http://localhost:4502/`

![screen_shot_2018-04-03at15317pm1](assets/screen_shot_2018-04-03at15317pm1.png)

Una volta effettuato l&#39;accesso, potete accedere a AEM. Per ulteriori informazioni, a seconda del ruolo, consulta quanto segue:

* [Authoring  ](/help/sites-authoring/home.md)
* [Amministrazione](/help/sites-administering/home.md)
* [Sviluppo](/help/sites-developing/home.md)
* [Gestione](/help/managing/best-practices.md)

## Implementazione avanzata {#advanced-deployment}

La sezione di cui sopra dovrebbe fornire una buona conoscenza delle basi dell&#39;installazione AEM. Tuttavia, l&#39;installazione di un sistema di produzione completo di AEM può comportare una maggiore complessità. Per informazioni complete sull’installazione avanzata, consulta le seguenti sottopagine:

* [Requisiti tecnici](/help/sites-deploying/technical-requirements.md)
* [Implementazioni consigliate](/help/sites-deploying/recommended-deploys.md)
* [Installazione personalizzata indipendente](/help/sites-deploying/custom-standalone-install.md)
* [Installazione dell’applicazione da server](/help/sites-deploying/application-server-install.md)
* [Risoluzione dei problemi](/help/sites-deploying/troubleshooting.md)
* [Avvio e interruzione da riga di comando](/help/sites-deploying/command-line-start-and-stop.md)
* [Configurazione](/help/sites-deploying/configuring.md)
* [Aggiornamento a AEM 6.4](/help/sites-deploying/upgrade.md)
* [eCommerce](/help/sites-deploying/ecommerce.md)
* [Articoli guida alla configurazione](/help/sites-deploying/ht-deploy.md)
* [Console Web](/help/sites-deploying/web-console.md)
* [Risoluzione dei problemi di replica](/help/sites-deploying/troubleshoot-rep.md)
* [Best practice  ](/help/sites-deploying/best-practices.md)
* [Implementazione di Communities](/help/communities/deploy-communities.md)
* [Introduzione alla piattaforma AEM](/help/sites-deploying/platform.md)
* [Linee guida sulle prestazioni](/help/sites-deploying/performance-guidelines.md)
* [Guida introduttiva di AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Cos&#39;è  AEM Screens?](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)

