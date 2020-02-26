---
title: Distribuzione di Communities
seo-title: Distribuzione di Communities
description: Come implementare AEM Communities
seo-description: Come implementare AEM Communities
uuid: 1f7faf1a-a339-4eaa-b728-b9110cb350a8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: d0249609-2a9c-4d3b-92ee-dbc5fbdeaac6
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87

---


# Distribuzione di Communities {#deploying-communities}

## Prerequisiti {#prerequisites}

* [Piattaforma AEM 6.4](../../help/sites-deploying/deploy.md)

* Licenza di AEM Communities

* Licenze facoltative per:

   * [Funzioni di Adobe Analytics for Communities](analytics.md)
   * [MongoDB per MSRP](msrp.md)
   * [Adobe Cloud for ASRP](asrp.md)

## Elenco di controllo dell&#39;installazione {#installation-checklist}

**Per la piattaforma[AEM](../../help/sites-deploying/deploy.md#what-is-aem)**

* Installa gli ultimi aggiornamenti di [AEM 6.4](#aem-updates)

* Se non si utilizzano le porte predefinite (4502, 4503), [configurare gli agenti di replica](#replication-agents-on-author)
* [replicare la chiave di crittografia](#replicate-the-crypto-key)
* Se supporta la globalizzazione, [configurare la traduzione automatica](../../help/sites-administering/translation.md)

   (impostazione di esempio per lo sviluppo)

**Per la funzionalità[Community](overview.md)**

* Se distribuite una farm [di](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)pubblicazione, [identificate l&#39;editore principale](#primary-publisher)

* [Abilita il servizio tunnel](#tunnel-service-on-author)
* [Abilita login per social network](social-login.md#adobe-granite-oauth-authentication-handler)
* [Configurare Adobe Analytics](analytics.md)
* Impostazione di un servizio e-mail [predefinito](email.md)
* Identificare la scelta per lo storage [UGC](working-with-srp.md) condiviso (**SRP**)

   * Se MongoDB SRP [(MSRP)](msrp.md)

      * [Installare e configurare MongoDB](msrp.md#mongodb-configuration)
      * [Configura Solr](solr.md)
      * [Select MSRP](srp-config.md)
   * Se il database relazionale SRP [(DSRP)](dsrp.md)

      * [Installare il driver JDBC per MySQL](#jdbc-driver-for-mysql)
      * [Installare e configurare MySQL per DSRP](dsrp-mysql.md)
      * [Configura Solr](solr.md)
      * [Seleziona DSRP](srp-config.md)
   * Se Adobe SRP [(ASRP)](asrp.md)

      * Consultate il rappresentante commerciale di riferimento per il provisioning
      * [Seleziona ASRP](srp-config.md)
   * Se JCR SRP [(JSRP)](jsrp.md)

      * Store UGC non condiviso:

         * UGC non è mai replicato
         * UGC visibile solo nell’istanza o nel cluster AEM in cui è stato immesso
      * Il valore predefinito è JSRP
   Per la funzione di **[abilitazione](overview.md#enablement-community)**

   * [Installare e configurare FFmpeg](ffmpeg.md)
   * [Installare il driver JDBC per MySQL](#jdbc-driver-for-mysql)
   * [Installare AEM Communities SCORM Engine](#scorm-package)
   * [Installazione e configurazione di MySQL per l&#39;abilitazione](mysql.md)






## Ultime versioni {#latest-releases}

AEM 6.4 Communities GA con il pacchetto Communities. Per informazioni sugli aggiornamenti di AEM 6.4 [Communities](/help/release-notes/release-notes.md#experience-manager-communities), consulta le Note [sulla versione di](/help/release-notes/release-notes.md#release-information)AEM 6.4.

### Aggiornamenti di AEM 6.4 {#aem-updates}

A partire da AEM 6.3, gli aggiornamenti alle community vengono forniti come parte dei Service Pack e dei pacchetti AEM Cumulative Fix.

Per gli ultimi aggiornamenti ad AEM 6.4, verifica i Service Pack e i Service Pack di [Adobe Experience Manager 6.4 Cumulative Fix](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

### Cronologia versioni {#version-history}

Con AEM 6.4 e versioni successive, le funzioni e gli hotfix di AEM Communities fanno parte dei pacchetti di correzioni e dei Service Pack cumulativi di AEM Communities. Non esistono pertanto pacchetti di caratteristiche distinti.

### Driver JDBC per MySQL {#jdbc-driver-for-mysql}

Due funzionalità Community utilizzano un database MySQL:

* Per [l&#39;abilitazione](enablement.md): registrazione delle attività SCORM e degli studenti
* Per [DSRP](dsrp.md): memorizzazione di contenuto generato dall&#39;utente (UGC)

Il connettore MySQL deve essere ottenuto e installato separatamente.

Le misure necessarie sono:

1. Scaricate l&#39;archivio ZIP da [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * La versione deve essere >= 5.1.38

1. Estrarre mysql-Connector-java-&lt;versione>-bin.jar (bundle) dall&#39;archivio

1. Utilizzate la console Web per installare e avviare il bundle:

   * Ad esempio, http://localhost:4502/system/console/bundles
   * Seleziona **`Install/Update`**
   * Sfoglia... per selezionare il bundle estratto dall&#39;archivio ZIP scaricato
   * Verificare che il driver JDBC di *Oracle Corporation per MySQLcom.mysql.jdbc* sia attivo e avviarlo in caso contrario (o controllare i registri)

1. Se l&#39;installazione avviene su una distribuzione esistente dopo la configurazione di JDBC, eseguire un nuovo riferimento JDBC al nuovo connettore salvando nuovamente la configurazione JDBC dalla console Web:

   * Ad esempio, http://localhost:4502/system/console/configMgr
   * Individua `Day Commons JDBC Connections Pool` configurazione
   * Seleziona per aprire
   * Seleziona `Save`

1. Ripetere i passaggi 3 e 4 per tutte le istanze di creazione e pubblicazione

Ulteriori informazioni sull&#39;installazione dei bundle sono disponibili nella pagina Console [](../../help/sites-deploying/configuring-web-console.md#bundles) Web.

#### Esempio: Bundle del connettore MySQL installato {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### Pacchetto SCORM {#scorm-package}

SCORM (Shareable Content Object Reference Model) è una raccolta di standard e specifiche per l&#39;e-learning. SCORM definisce anche come il contenuto può essere incluso in un pacchetto ZIP trasferibile.

Il motore SCORM di AEM Communities è richiesto per la funzione di [abilitazione](overview.md#enablement-community) . I pacchetti scorm supportati nella versione AEM Communities 6.4 sono:

* **[cq -social- scorm -package, versione 1.2.11](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-pkg)**. Questo pacchetto SCORM è supportato da tutte le versioni di AEM 6.4 Communities.

* **[cq -social- scorm -package, versione 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)**include il motore[SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/). Questo pacchetto SCORM è supportato a partire da AEM 6.4.2.x Communities.

Per una nuova installazione del motore SCORM, utilizzare il pacchetto contenente [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) (che è [ cq -social- scorm -package, versione 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)). In modo da poter utilizzare le risorse di apprendimento supportate da SCORM 2017.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Per installare per la prima volta un pacchetto SCORM

1. Installate il pacchetto **[cq-social-scorm, versione 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Scaricate **`/libs/social/config/scorm/database_scormengine_data.sql`** dall&#39;istanza cq ed eseguitela in server mysql per creare uno schema scormEngineDB aggiornato.
1. Aggiungi `/content/communities/scorm/RecordResults` nella proprietà Percorsi esclusi nel filtro CSRF dagli `https://<hostname>;:<port>/system/console/configMgr` editori.

Le installazioni SCORM esistenti possono essere aggiornate al pacchetto [**cq-social-scorm versione 2.2.2 **](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg)(che utilizza[SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)), se il contenuto del corso creato richiede SCORM 2017.1.

>[!NOTE]
>
>L&#39;aggiornamento al pacchetto SCORM 2017.1 richiede la migrazione del database esistente (come spiegato più avanti).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Per aggiornare la versione del motore SCORM

1. Esegui il backup dello schema ScormEngineDB.
1. Installate il pacchetto **[cq-social-scorm, versione 2.2.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/scorm/cq-social-scorm-2017-pkg).**
1. Scaricate il pacchetto da `/libs/social/config/scorm/ScormEngine.zip` ed estraete lo stesso.
1. Andate alla cartella **Installer** della directory estratta.
1. Eseguire l&#39;aggiornamento `SystemDatabaseConnectionString` con il file `scorm db connection url` in **[!UICONTROL EngineInstall.xml]**.
1. Eseguire lo strumento di aggiornamento schema mysql nella cartella Installer con il comando:

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Monitorare `engine_upgrade.log` i file per qualsiasi tipo di errore e stato di aggiornamento dello schema.
1. Aggiungi `/content/communities/scorm/RecordResults` nella proprietà Percorsi **** esclusi nel filtro CSRF `https://<hostname>:<port>/system/console/configMgr` dagli editori.

### Registrazione SCORM {#scorm-logging}

Durante l&#39;installazione, tutte le attività di abilitazione vengono registrate in modo dettagliato nella console del sistema.

Se desiderato, il livello di registro può essere impostato su WARN per il `RusticiSoftware.*` pacchetto.

Per utilizzare i registri, vedere [Uso dei record di controllo e dei file](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)di registro.

### AEM Advanced MLS {#aem-advanced-mls}

Per la raccolta SRP (MSRP o DSRP) per supportare la ricerca multilingue avanzata (MLS), sono necessari nuovi plug-in Solr oltre a uno schema personalizzato e alla configurazione Solr. Tutti gli elementi richiesti vengono assemblati in un file zip scaricabile.

Il download avanzato di MLS (noto anche come &#39;phasetwo&#39;) è disponibile dall&#39;archivio di Adobe:

* [AEM-SOLR-MLS-phasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Versione 1.2.40, 6 aprile 2016
   * Scarica AEM-SOLR-MLS-phasetwo-1.2.40.zip

Per informazioni dettagliate e sull&#39;installazione, visitare Configurazione [](solr.md) solare per SRP.

### Collegamenti a Package Share {#about-links-to-package-share}

**Pacchetti visibili in Adobe AEM Cloud**

I collegamenti ai pacchetti in questa pagina non richiedono alcuna istanza in esecuzione di AEM in quanto devono creare pacchetti di condivisione su `adobeaemcloud.com`. Mentre i pacchetti sono visualizzabili, il `Install`pulsante consente di installare i pacchetti in un sito ospitato da Adobe. Se si desidera eseguire l&#39;installazione in un&#39;istanza AEM locale, la selezione `Install`darà luogo a un errore.

**Come eseguire l&#39;installazione su un&#39;istanza AEM locale**

Per installare i pacchetti visibili in `adobeaemcloud.com` un’istanza AEM locale, è necessario prima scaricare il pacchetto su un disco locale:

* Select the **[!UICONTROL Assets]** tab
* Seleziona **[!UICONTROL download su disco]**

Nell&#39;istanza locale di AEM, utilizza il gestore pacchetti (ad esempio [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)) per caricare nell&#39;archivio pacchetti di AEM locale.

In alternativa, accedendo al pacchetto utilizzando la condivisione di pacchetti dall&#39;istanza locale di AEM (ad esempio, [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)), il `Download`pulsante verrà scaricato nell&#39;archivio pacchetti dell&#39;istanza locale AEM.

Una volta nell&#39;archivio pacchetti dell&#39;istanza AEM locale, utilizzate il gestore pacchetti per installare il pacchetto.

Per ulteriori informazioni, vedere [Come utilizzare i pacchetti](../../help/sites-administering/package-manager.md#package-share).

## Implementazioni consigliate {#recommended-deployments}

In AEM Communities, uno store comune viene utilizzato per memorizzare il contenuto generato dall&#39;utente (UGC) ed è spesso denominato fornitore di risorse di [storage (SRP)](working-with-srp.md). La distribuzione consigliata si basa sulla scelta di un&#39;opzione SRP per lo store comune.

Lo store comune supporta la moderazione e l&#39;analisi di UGC nell&#39;ambiente di pubblicazione, eliminando al contempo la necessità di [replicare](sync.md) UGC.

* [Archivio](working-with-srp.md)contenuti community: illustra le opzioni di storage SRP per le community AEM

* [Topologie](topologies.md)consigliate: illustra la topologia da utilizzare in base al caso di utilizzo e alla scelta SRP

## Aggiornamento {#upgrading}

Quando effettuate l’aggiornamento alla piattaforma AEM 6.4 dalle versioni precedenti di AEM, è importante leggere Aggiornamento ad AEM 6.4.

Oltre ad aggiornare la piattaforma, leggi [Aggiornamento ad AEM Communities 6.4](upgrade.md) per informazioni sulle modifiche apportate a Communities.

## Configurazioni {#configurations}

### Editore principale {#primary-publisher}

Se la distribuzione scelta è una farm [di](topologies.md#tarmk-publish-farm)pubblicazione, un&#39;istanza di pubblicazione AEM deve essere identificata come **`primary publisher`** per le attività che non devono verificarsi in tutte le istanze, ad esempio per le funzioni che si basano sulle **notifiche** o su **Adobe Analytics**.

Per impostazione predefinita, la configurazione `AEM Communities Publisher Configuration` OSGi è configurata con la **`Primary Publisher`** casella di controllo selezionata, in modo che tutte le istanze di pubblicazione in una farm di pubblicazione si identifichino automaticamente come principali.

Pertanto, è necessario **modificare la configurazione su tutte le istanze** di pubblicazione secondarie per deselezionare la **`Primary Publisher`** casella di controllo.

![chlimage_1-411](assets/chlimage_1-411.png)

Per tutte le altre istanze di pubblicazione (secondarie) in una farm di pubblicazione:

* Accesso con privilegi di amministratore
* Accedere alla console [Web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Individua il `AEM Communities Publisher Configuration`
* Selezionate l’icona di modifica
* Deselezionare la casella Editore **** principale
* Seleziona **[!UICONTROL Salva]**

### Agenti di replica sull&#39;autore {#replication-agents-on-author}

La replica viene utilizzata per il contenuto del sito creato nell&#39;ambiente di pubblicazione, ad esempio i gruppi di community, nonché per la gestione di membri e gruppi di membri dall&#39;ambiente di authoring tramite il servizio [](#tunnel-service-on-author)tunnel.

Per l&#39;editore principale, accertatevi che [Replication Agent Config](../../help/sites-deploying/replication.md) identifichi correttamente il server di pubblicazione e l&#39;utente autorizzato. L&#39;utente autorizzato predefinito `admin,` dispone già delle autorizzazioni appropriate (è membro di `Communities Administrators`).

Affinché un altro utente disponga delle autorizzazioni appropriate, deve essere aggiunto come membro al gruppo di `administrators` utenti (anche membro di `Communities Administrators`).

Nell’ambiente di authoring sono disponibili due agenti di replica che richiedono la corretta configurazione del trasporto.

* Accedere alla console Replica durante l’authoring

   * Dalla navigazione globale: **[!UICONTROL Strumenti > Implementazione > Replica > Agenti per l&#39;autore]**

* Seguire la stessa procedura per entrambi gli agenti:

   * **Agente predefinito (pubblicazione)**
   * **Agente replica inversa (pubblicazione invertita)**

      1. Selezionare l&#39;agente
      1. Select **[!UICONTROL edit]**
      1. Select the **[!UICONTROL Transport]** tab
      1. Se non è una porta `4503`, modificate l&#39; **[!UICONTROL URI]** per specificare la porta corretta
      1. In caso contrario, modificate `admin`l’ **[!UICONTROL utente]** e la **[!UICONTROL password]** per specificare un membro del gruppo di `administrators` utenti

Le immagini seguenti mostrano i risultati della modifica della porta da 4503 a 6103 tramite:

#### Agente predefinito (pubblicazione) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Agente replica inversa (pubblicazione invertita) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Servizio Tunnel sull&#39;autore {#tunnel-service-on-author}

Quando si utilizza l’ambiente di authoring per [creare siti](sites-console.md), [modificare le proprietà](sites-console.md#modifying-site-properties) del sito o [gestire membri](members.md)della comunità, è necessario accedere ai membri (utenti) registrati nell’ambiente di pubblicazione, non agli utenti registrati nell’autore.

Il servizio tunnel fornisce questo accesso tramite l&#39;agente di replica in fase di creazione.

Per abilitare il servizio tunnel:

* All’ **autore**
* Accesso con privilegi amministrativi
* Se l&#39;editore non è localhost:4503 o se l&#39;utente del trasporto non lo è, `admin`,

   Quindi [configurate l&#39;agente di replica](#replication-agents-on-author)

* Accesso alla console [Web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Individua il `AEM Communities Publish Tunnel Service`
* Selezionate l’icona di modifica
* Selezionare la casella di **[!UICONTROL attivazione]**
* Seleziona **[!UICONTROL Salva]**

![chlimage_1-414](assets/chlimage_1-414.png)

### Replicare la chiave Crypto {#replicate-the-crypto-key}

Esistono due funzioni di AEM Communities che richiedono che tutte le istanze del server AEM utilizzino le stesse chiavi di crittografia. Si tratta di [Analytics](analytics.md) e [ASRP](asrp.md).

A partire da AEM 6.3, il materiale chiave viene memorizzato nel file system e non più nell’archivio.

Per copiare il materiale chiave dall’autore a tutte le altre istanze, è necessario:

* Accedete all’istanza AEM, in genere un’istanza di creazione, che contiene il materiale chiave da copiare

   * Individuare il `com.adobe.granite.crypto.file` bundle nel file system locale

      Ad esempio:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Il `bundle.info` file identificherà il bundle
   * Accedere alla cartella dei dati

      Ad esempio:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Copiare i file hmac e master



* Per ogni istanza AEM di destinazione

   * Accedere alla cartella dei dati

      Ad esempio:

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Incolla i 2 file precedentemente copiati
   * È necessario [aggiornare il bundle](#refresh-the-granite-crypto-bundle) Granite Crypto se l’istanza AEM di destinazione è in esecuzione


>[!CAUTION]
>
>Se è già stata configurata un&#39;altra funzione di protezione basata sulle chiavi di crittografia, la replica delle chiavi di crittografia potrebbe danneggiare la configurazione. Per assistenza, [contattate l&#39;assistenza](https://helpx.adobe.com/marketing-cloud/contact-support.html)clienti.

#### Replica archivio {#repository-replication}

È possibile conservare il materiale chiave memorizzato nell’archivio, come nel caso di AEM 6.2 e versioni precedenti, specificando la seguente proprietà di sistema al primo avvio di ogni istanza di AEM (che crea l’archivio iniziale):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>È importante verificare che l&#39;agente di [replica nell&#39;istanza di creazione](#replication-agents-on-author) sia configurato correttamente.

Con il materiale chiave memorizzato nella directory archivio, la procedura per replicare la chiave di crittografia dall’autore ad altre istanze è la seguente:

Utilizzo di [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* individuare [https://&lt;server>:&lt;porta>/crx/de](http://localhost:4502/crx/de)
* select `/etc/key`
* apri `Replication` scheda
* select `Replicate`

* [aggiorna il bundle Granite Crypto](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Aggiornare il pacchetto Granite Crypto {#refresh-the-granite-crypto-bundle}

* Per ogni istanza di pubblicazione, accedete alla console [Web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio, [https://&lt;server>:&lt;porta>/system/console/bundle](http://localhost:4503/system/console/bundles)

* Individua `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto)
* Seleziona **[!UICONTROL aggiornamento]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Dopo un momento, dovrebbe comparire una finestra di dialogo **Successo** :

   `Operation completed successfully.`

### Server Apache HTTP {#apache-http-server}

Se utilizzate il server Apache HTTP, accertatevi di utilizzare il nome server corretto per tutte le voci pertinenti.

In particolare, fate attenzione a utilizzare il nome corretto del server, non `localhost`nel `RedirectMatch`.

#### httpd.conf, esempio {#httpd-conf-sample}

```shell
<IfModule alias_module>
     # XAMPP does not have a favicon; this prevents any 404 errors which may arise.
     Redirect 404 /favicon.ico
     <Location /favicon.ico>
         ErrorDocument 404 "No favicon"
     </Location>

    # Return from "Sign Out" generates response header directing you to "/", generating a 404 error
    # The RedirectMatch resolves it correctly when modified for the target Community Site:
    RedirectMatch ^/$ https://[server name]/content/sites/engage/en.html
 ...
 </IfModule>
```

### Dispatcher {#dispatcher}

Se utilizzi un dispatcher, vedi:

* Documentazione di AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)
* [Installazione di Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Configurazione del dispatcher per Communities](dispatcher.md)
* [Problemi noti](troubleshooting.md#dispatcher-refetch-fails)

## Documentazione di Community correlate {#related-communities-documentation}

* Visitate [Administering Communities Sites](administer-landing.md) per informazioni su come creare un sito community, configurare modelli di sito community, moderare i contenuti della community, gestire i membri e configurare i messaggi.

* Visitate [Developing Communities](communities.md) per informazioni sul framework dei componenti sociali (SCF) e sulla personalizzazione dei componenti e delle funzionalità di Communities.

* Per informazioni su come creare e configurare i componenti di Community, consulta [Authoring dei componenti](author-communities.md) di Communities.

