---
title: Distribuzione di Communities
seo-title: Deploying Communities
description: Come distribuire AEM Communities
seo-description: How to deploy AEM Communities
uuid: 1f7faf1a-a339-4eaa-b728-b9110cb350a8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: d0249609-2a9c-4d3b-92ee-dbc5fbdeaac6
exl-id: 0b7496f0-0b3c-4d12-a659-d95744157f14
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2216'
ht-degree: 2%

---

# Distribuzione di Communities {#deploying-communities}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Prerequisiti {#prerequisites}

* [Piattaforma AEM 6.4](../../help/sites-deploying/deploy.md)

* Licenza AEM Communities

* Licenze opzionali per:

   * [Funzioni di Adobe Analytics for Communities](analytics.md)
   * [MongoDB per MSRP](msrp.md)
   * [Adobe Cloud per ASRP](asrp.md)

## Elenco di controllo dell&#39;installazione {#installation-checklist}

**Per [piattaforma AEM](../../help/sites-deploying/deploy.md#what-is-aem)**

* Installa più recente [Aggiornamenti di AEM 6.4](#aem-updates)

* Se non si utilizzano le porte predefinite (4502, 4503), allora [configurare gli agenti di replica](#replication-agents-on-author)
* [replicare la chiave crittografica](#replicate-the-crypto-key)
* Sostenere la globalizzazione, [configurazione della traduzione automatica](../../help/sites-administering/translation.md)

   (impostazione di esempio disponibile per lo sviluppo)

**Per [Funzionalità community](overview.md)**

* Se distribuisci un [pubblica azienda](../../help/sites-deploying/recommended-deploys.md#tarmk-farm), [identificare l&#39;editore principale](#primary-publisher)

* [Attiva il servizio tunnel](#tunnel-service-on-author)
* [Abilita accesso social](social-login.md#adobe-granite-oauth-authentication-handler)
* [Configurare Adobe Analytics](analytics.md)
* Imposta un [servizio e-mail predefinito](email.md)
* Identifica la scelta per [archiviazione UGC condivisa](working-with-srp.md) (**SRP**)

   * Se MongoDB SRP [(MSRP)](msrp.md)

      * [Installare e configurare MongoDB](msrp.md#mongodb-configuration)
      * [Configura Solr](solr.md)
      * [Seleziona MSRP](srp-config.md)
   * Se SRP database relazionale [(DSRP)](dsrp.md)

      * [Installare il driver JDBC per MySQL](#jdbc-driver-for-mysql)
      * [Installare e configurare MySQL per DSRP](dsrp-mysql.md)
      * [Configura Solr](solr.md)
      * [Seleziona DSRP](srp-config.md)
   * Se Adobe SRP [(ASRP)](asrp.md)

      * Collabora con il rappresentante del tuo account per il provisioning
      * [Seleziona ASRP](srp-config.md)
   * Se JCR SRP [(JSRP)](jsrp.md)

      * Non è un archivio UGC condiviso:

         * UGC non viene mai replicato
         * UGC visibile solo su AEM&#39;istanza o cluster in cui è stato inserito
      * Il valore predefinito è JSRP

   Per **[funzione di abilitazione](overview.md#enablement-community)**

   * [Installare e configurare FFmpeg](ffmpeg.md)
   * [Installare il driver JDBC per MySQL](#jdbc-driver-for-mysql)
   * [Installare AEM Communities SCORM-Engine](#scorm-package)
   * [Installare e configurare MySQL per l&#39;abilitazione](mysql.md)






## Versioni più recenti {#latest-releases}

AEM 6.4 Communities GA include il pacchetto Community. Per informazioni sugli aggiornamenti a AEM 6.4 [Community](/help/release-notes/release-notes.md#experience-manager-communities), fai riferimento a [Note sulla versione di AEM 6.4](/help/release-notes/release-notes.md#release-information).

### Aggiornamenti di AEM 6.4 {#aem-updates}

A partire dalla AEM 6.3, gli aggiornamenti alle Community vengono forniti come parte di AEM Cumulative Fix Pack e Service Pack.

Per gli ultimi aggiornamenti a AEM 6.4, assicurati di controllare [Adobe Experience Manager 6.4 Cumulative Fix Pack e Service Pack](https://helpx.adobe.com/it/experience-manager/aem-releases-updates.html).

### Cronologia delle versioni {#version-history}

Come in AEM 6.4 e versioni successive, le funzioni e gli hotfix di AEM Communities fanno parte dei pacchetti correzioni cumulativi e dei Service Pack di AEM Communities. Non esistono pertanto pacchetti di funzioni separati.

### Driver JDBC per MySQL {#jdbc-driver-for-mysql}

Due funzionalità di Communities utilizzano un database MySQL:

* Per [abilitazione](enablement.md): registrazione di attività SCORM e studenti
* Per [DSRP](dsrp.md): archiviazione di contenuti generati dall’utente (UGC)

Il connettore MySQL deve essere ottenuto e installato separatamente.

Le misure necessarie sono:

1. Scarica l&#39;archivio ZIP da [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * La versione deve essere >= 5.1.38

1. Estrai mysql-connector-java-&lt;version>-bin.jar (bundle) dall&#39;archivio

1. Usa la console web per installare e avviare il bundle:

   * Ad esempio, http://localhost:4502/system/console/bundles
   * Seleziona **`Install/Update`**
   * Sfoglia... per selezionare il bundle estratto dall&#39;archivio ZIP scaricato
   * Controlla che *Driver JDBC di Oracle Corporation per MySQLcom.mysql.jdbc* è attivo e avvialo in caso contrario (o controlla i registri)

1. Se esegui l’installazione su un’implementazione esistente dopo la configurazione di JDBC, esegui un rebind JDBC al nuovo connettore, salvando nuovamente la configurazione JDBC dalla console Web:

   * Ad esempio, http://localhost:4502/system/console/configMgr
   * Individua `Day Commons JDBC Connections Pool` configurazione
   * Seleziona per aprire
   * Seleziona `Save`

1. Ripeti i passaggi 3 e 4 su tutte le istanze di authoring e pubblicazione

Ulteriori informazioni sull&#39;installazione dei bundle sono disponibili sul [Console web](/help/sites-deploying/web-console.md#bundles) pagina.

#### Esempio: Bundle del connettore MySQL installato {#example-installed-mysql-connector-bundle}

![chlimage_1-410](assets/chlimage_1-410.png)

### Pacchetto SCORM {#scorm-package}

SCORM (Shared Content Object Reference Model) è una raccolta di standard e specifiche per l&#39;e-learning. SCORM definisce anche come il contenuto può essere confezionato in un file ZIP trasferibile.

Il motore AEM Communities SCORM è richiesto per [abilitazione](overview.md#enablement-community) funzionalità. I pacchetti Scorm supportati nella versione AEM Communities 6.4 sono:

* **[cq -social- scorm -package, versione 1.2.11](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-pkg)**. Questo pacchetto SCORM è supportato da tutte le versioni di AEM 6.4 Communities.

* **[cq -social- scorm -package, versione 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg)** include [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) motore. Questo pacchetto SCORM è supportato a partire AEM versione 6.4.2.x Communities.

Per una nuova installazione del motore SCORM, il pacchetto contenente [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) (che è [  cq -social- scorm -package, versione 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg)). In modo da poter utilizzare le risorse di apprendimento supportate da SCORM 2017.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Per installare un pacchetto SCORM per la prima volta

1. Installa il **[cq-social-scorm-package, versione 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg).**
1. Scarica **`/libs/social/config/scorm/database_scormengine_data.sql`** dall&#39;istanza cq e eseguiscila in mysql server per creare uno schema scormEngineDB aggiornato.
1. Aggiungi `/content/communities/scorm/RecordResults` in Proprietà Percorsi esclusi nel filtro CSRF da `https://<hostname>;:<port>/system/console/configMgr` sugli editori.

Le installazioni SCORM esistenti possono essere aggiornate a [**cq-social-scorm-package, versione 2.2.2**](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg) (che utilizza [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/)), se il contenuto del corso creato richiede SCORM 2017.1.

>[!NOTE]
>
>L&#39;aggiornamento al pacchetto SCORM 2017.1 richiede la migrazione del database esistente (come spiegato più avanti).

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Per aggiornare la versione del motore SCORM

1. Esegui il backup dello schema ScormEngineDB.
1. Installa il **[cq-social-scorm-package, versione 2.2.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fsocial%2Fscorm%2Fcq-social-scorm-2017-pkg).**
1. Scarica il pacchetto da `/libs/social/config/scorm/ScormEngine.zip` ed estrarne lo stesso.
1. Vai a **Installazione** della directory estratta.
1. Aggiorna `SystemDatabaseConnectionString` con il tuo `scorm db connection url` in file **[!UICONTROL EngineInstall.xml]**.
1. Esegui lo strumento di aggiornamento dello schema mysql nella cartella Installer con il comando:

   `java -Dlogback.configurationFile=logback.xml -cp "lib/*" RusticiSoftware.ScormContentPlayer.Logic.Upgrade.ConsoleApp EngineInstall.xml`
1. Monitor `engine_upgrade.log` per qualsiasi tipo di errore e stato di aggiornamento dello schema.
1. Aggiungi `/content/communities/scorm/RecordResults` in **[!UICONTROL Percorsi esclusi]** proprietà nel filtro CSRF da `https://<hostname>:<port>/system/console/configMgr` sugli editori.

### Registrazione SCORM {#scorm-logging}

Come installato, tutte le attività di abilitazione vengono registrate in modo dettagliato nella console di sistema.

Se lo desideri, puoi impostare il livello di log su WARN per `RusticiSoftware.*` pacchetto.

Per lavorare con i registri, consulta [Utilizzo dei record di controllo e dei file di registro](../../help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### MLS avanzate AEM {#aem-advanced-mls}

Per la raccolta SRP (MSRP o DSRP) per supportare la ricerca multilingue avanzata (MLS), sono necessari nuovi plug-in Solr oltre a uno schema personalizzato e una configurazione Solr. Tutti gli elementi richiesti vengono assemblati in un file zip scaricabile.

Il download avanzato di MLS (noto anche come &#39;phasetwo&#39;) è disponibile dall&#39;archivio Adobe:

* Fasetwo AEM-SOLR-MLS

   Per ottenere il pacchetto MLS avanzato, vedi [MLS avanzate AEM](deploy-communities.md#aem-advanced-mls) nella sezione implementazione della documentazione.

   * Versione 1.2.40, 6 aprile 2016
   * Scarica AEM-SOLR-MLS-phasetwo-1.2.40.zip

Per informazioni dettagliate e sull&#39;installazione, visita [Configurazione Solr](solr.md) per SRP

### Informazioni sui collegamenti alla condivisione dei pacchetti {#about-links-to-package-share}

**Pacchetti visibili in Adobe AEM Cloud**

I collegamenti ai pacchetti in questa pagina non richiedono alcuna istanza in esecuzione di AEM in quanto devono condividere i pacchetti in `adobeaemcloud.com`. Mentre i pacchetti sono visualizzabili, la `Install`Il pulsante è per installare i pacchetti in un sito ospitato da Adobe. Se si desidera eseguire l&#39;installazione in un&#39;istanza AEM locale, selezionare `Install`genererà un errore.

**Come eseguire l&#39;installazione su un&#39;istanza AEM locale**

Per installare i pacchetti visibili in `adobeaemcloud.com` in un&#39;istanza AEM locale, il pacchetto deve prima essere scaricato su un disco locale:

* Seleziona la **[!UICONTROL Risorse]** scheda
* Seleziona **[!UICONTROL scaricare su disco]**

Nell’istanza di AEM locale, utilizza il gestore dei pacchetti (ad esempio [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)), per caricare nell’archivio locale dei pacchetti AEM.

In alternativa, puoi accedere al pacchetto utilizzando la condivisione del pacchetto dall’istanza AEM locale (ad esempio, [http://localhost:4502/crx/packageshare/](http://localhost:4502/crx/packageshare/)), `Download`verrà scaricato nell’archivio dei pacchetti dell’istanza AEM locale.

Una volta nell&#39;archivio dei pacchetti dell&#39;istanza AEM locale, utilizza il gestore dei pacchetti per installare il pacchetto.

Per ulteriori informazioni, visita [Come lavorare con i pacchetti](../../help/sites-administering/package-manager.md#package-share).

## Implementazioni consigliate {#recommended-deployments}

In AEM Communities, un archivio comune viene utilizzato per memorizzare i contenuti generati dagli utenti (UGC) e viene spesso indicato come [provider di risorse di archiviazione (SRP)](working-with-srp.md). La distribuzione consigliata si basa sulla scelta di un’opzione SRP per lo store comune.

L&#39;archivio comune supporta la moderazione e l&#39;analisi degli UGC nell&#39;ambiente di pubblicazione, eliminando al contempo la necessità di [replica](sync.md) dell&#39;UGC.

* [Archivio dei contenuti della community](working-with-srp.md): illustra le opzioni di storage SRP per le AEM community

* [Topologie consigliate](topologies.md): discute la topologia da utilizzare in base al caso d’uso e alla scelta dell’SRP

## Aggiornamento {#upgrading}

Quando esegui l’aggiornamento alla piattaforma AEM 6.4 dalle versioni precedenti di AEM, è importante leggere Aggiornamento a AEM 6.4.

Oltre all’aggiornamento della piattaforma, consulta [Aggiornamento ad AEM Communities 6.4](upgrade.md) per informazioni sulle modifiche apportate a Communities.

## Configurazioni {#configurations}

### Editore principale {#primary-publisher}

Quando la distribuzione scelta è un [pubblica azienda](topologies.md#tarmk-publish-farm), quindi un&#39;istanza di pubblicazione AEM deve essere identificata come **`primary publisher`** per le attività che non devono verificarsi su tutte le istanze, ad esempio le funzionalità che si basano su **Notifiche** o **Adobe Analytics**.

Per impostazione predefinita, la `AEM Communities Publisher Configuration` La configurazione OSGi è configurata con **`Primary Publisher`** selezionata, in modo che tutte le istanze di pubblicazione in una farm di pubblicazione si identifichino come principali.

È pertanto necessario **modifica la configurazione in tutte le istanze di pubblicazione secondarie** per deselezionare **`Primary Publisher`** casella di controllo.

![chlimage_1-411](assets/chlimage_1-411.png)

Per tutte le altre istanze di pubblicazione (secondarie) in una farm di pubblicazione:

* Accesso con privilegi di amministratore
* Accedere al [console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Individua il `AEM Communities Publisher Configuration`
* Seleziona l’icona di modifica
* Deseleziona **[!UICONTROL Editore principale]** scatola
* Seleziona **[!UICONTROL Salva]**

### Agenti di replica sull’autore {#replication-agents-on-author}

La replica viene utilizzata per il contenuto del sito creato nell’ambiente di pubblicazione, ad esempio i gruppi della community, nonché per la gestione di membri e gruppi di membri dall’ambiente di authoring tramite l’ [servizio tunnel](#tunnel-service-on-author).

Per l&#39;editore principale, assicurati che [Configurazione dell&#39;agente di replica](../../help/sites-deploying/replication.md) identifica correttamente il server di pubblicazione e l&#39;utente autorizzato. Utente autorizzato predefinito, `admin,` dispone già delle autorizzazioni appropriate (è membro di `Communities Administrators`).

Affinché un altro utente disponga delle autorizzazioni appropriate, deve essere aggiunto come membro al `administrators` gruppo di utenti (anche membro di `Communities Administrators`).

Nell’ambiente di authoring sono disponibili due agenti di replica che richiedono la configurazione corretta del trasporto.

* Accedere alla console Replica sull’autore

   * Dalla navigazione globale: **[!UICONTROL Strumenti > Implementazione > Replica > Agenti sull’autore]**

* Seguire la stessa procedura per entrambi gli agenti:

   * **Agente predefinito (pubblicazione)**
   * **Agente di replica inversa (pubblicazione inversa)**

      1. Seleziona l&#39;agente
      1. Seleziona **[!UICONTROL modifica]**
      1. Seleziona la **[!UICONTROL Trasporti]** scheda
      1. Se non la porta `4503`, modifica il **[!UICONTROL URI]** per specificare la porta corretta
      1. Se non utente `admin`, modifica il **[!UICONTROL Utente]** e **[!UICONTROL Password]** per specificare un membro della `administrators` gruppo utenti

Le immagini seguenti mostrano i risultati della modifica della porta da 4503 a 6103:

#### Agente predefinito (pubblicazione) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Agente di replica inversa (pubblicazione inversa) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Servizio tunnel su Autore {#tunnel-service-on-author}

Quando si utilizza l’ambiente di authoring in [creare siti](sites-console.md), [modificare le proprietà del sito](sites-console.md#modifying-site-properties) o [gestire membri della community](members.md), è necessario accedere ai membri (utenti) registrati nell’ambiente di pubblicazione, non agli utenti registrati sull’autore.

Il servizio tunnel fornisce questo accesso utilizzando l&#39;agente di replica sull&#39;autore.

Per attivare il servizio tunnel:

* On **autore**
* Accesso con privilegi amministrativi
* Se l&#39;editore non è localhost:4503 o l&#39;utente del trasporto non lo è `admin`,

   Then [configurare l&#39;agente di replica](#replication-agents-on-author)

* Accedere al [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Individua il `AEM Communities Publish Tunnel Service`
* Seleziona l’icona di modifica
* Controlla la **[!UICONTROL abilita]** scatola
* Seleziona **[!UICONTROL Salva]**

![chlimage_1-414](assets/chlimage_1-414.png)

### Replicare la chiave Crypto {#replicate-the-crypto-key}

Esistono due funzioni di AEM Communities che richiedono che tutte le istanze AEM server utilizzino le stesse chiavi di crittografia. Questi sono [Analytics](analytics.md) e [ASRP](asrp.md).

A partire da AEM 6.3, il materiale chiave viene memorizzato nel file system e non più nel repository.

Per copiare il materiale chiave dall’autore a tutte le altre istanze, è necessario:

* Accedi all&#39;istanza AEM, in genere un&#39;istanza dell&#39;autore, che contiene il materiale chiave da copiare

   * Individua il `com.adobe.granite.crypto.file` nel file system locale

      Ad esempio:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * La `bundle.info` il file identificherà il bundle
   * Passa alla cartella dati

      Ad esempio:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Copia i file hmac e i file dei nodi principali



* Per ogni istanza AEM target

   * Passa alla cartella dati

      Ad esempio:

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Incolla i 2 file precedentemente copiati
   * È necessario [aggiorna il bundle Granite Crypto](#refresh-the-granite-crypto-bundle) se l’istanza di AEM di destinazione è attualmente in esecuzione


>[!CAUTION]
>
>Se è già stata configurata un’altra funzione di sicurezza basata sulle chiavi crittografiche, la replica delle chiavi crittografiche potrebbe danneggiare la configurazione. Per assistenza, [contattare l&#39;assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html).

#### Replica dell’archivio {#repository-replication}

È possibile conservare il materiale chiave memorizzato nell&#39;archivio, come nel caso di AEM 6.2 e versioni precedenti, specificando la seguente proprietà di sistema al primo avvio di ogni istanza AEM (che crea l&#39;archivio iniziale):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>È importante verificare che la [agente di replica sull&#39;autore](#replication-agents-on-author) è configurato correttamente.

Con il materiale chiave memorizzato nell’archivio, il modo per replicare la chiave crittografica dall’autore ad altre istanze è il seguente:

Utilizzo [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* naviga a [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* select `/etc/key`
* open `Replication` scheda
* select `Replicate`

* [aggiorna il bundle Granite Crypto](#refresh-the-granite-crypto-bundle)

![chlimage_1-415](assets/chlimage_1-415.png)

#### Aggiorna il bundle Crypto Granite {#refresh-the-granite-crypto-bundle}

* In ogni istanza di pubblicazione, accedi al [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio: [https://&lt;server>:&lt;port>/system/console/bundle](http://localhost:4503/system/console/bundles)

* Individua `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto)
* Seleziona **[!UICONTROL Aggiorna]**

![chlimage_1-416](assets/chlimage_1-416.png)

* Dopo un momento, un **Completato** viene visualizzata la finestra di dialogo:

   `Operation completed successfully.`

### Server HTTP Apache {#apache-http-server}

Se utilizzi il server HTTP Apache, assicurati di utilizzare il nome server corretto per tutte le voci pertinenti.

In particolare, fare attenzione a utilizzare il nome server corretto, non `localhost`, nella `RedirectMatch`.

#### campione httpd.conf {#httpd-conf-sample}

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

Se utilizzi un’istanza di Dispatcher, consulta:

* AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) documentazione
* [Installazione di Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Configurazione di Dispatcher per Communities](dispatcher.md)
* [Problemi noti](troubleshooting.md#dispatcher-refetch-fails)

## Documentazione di Communities correlata {#related-communities-documentation}

* Visita [Amministrazione di siti di Communities](administer-landing.md) per informazioni sulla creazione di un sito community, sulla configurazione di modelli di sito community, sulla moderazione dei contenuti della community, sulla gestione dei membri e sulla configurazione della messaggistica.

* Visita [Sviluppo di Communities](communities.md) per informazioni sul framework dei componenti sociali (SCF) e sulla personalizzazione dei componenti e delle funzionalità di Communities.

* Visita [Authoring dei componenti di Communities](author-communities.md) per scoprire come creare e configurare i componenti di Communities.
