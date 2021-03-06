---
title: Attività di manutenzione pre-aggiornamento
seo-title: Attività di manutenzione pre-aggiornamento
description: Scopri le attività di pre-aggiornamento in AEM.
seo-description: Scopri le attività di pre-aggiornamento in AEM.
uuid: 6c0d4b31-6464-470b-9e40-1fc2abb9b2a6
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 899ea120-c96d-4dbf-85da-e5d25959d10a
feature: Aggiornamento
exl-id: f146cb2f-ee77-4c99-8dff-446cdb3a7797
source-git-commit: dd996d0bb856b9140d420d03dec446a382d10acd
workflow-type: tm+mt
source-wordcount: '2179'
ht-degree: 0%

---

# Attività di manutenzione pre-aggiornamento{#pre-upgrade-maintenance-tasks}

Prima di iniziare l’aggiornamento, è importante seguire queste operazioni di manutenzione per garantire che il sistema sia pronto e possa essere rimandato in caso di problemi:

* [Garantire spazio su disco sufficiente](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Backup completo AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Backup delle modifiche a /etc](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#backup-changes-etc)
* [Genera il file quickstart.properties](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Configurare l’eliminazione del flusso di lavoro e del registro di controllo](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Installare, configurare ed eseguire le attività di pre-aggiornamento](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Disattiva moduli di accesso personalizzati](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-login-modules)
* [Rimuovere Gli Aggiornamenti Dalla Directory /install](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Interrompi istanze di standby a freddo](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Disattiva processi pianificati personalizzati](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Esegui pulizia revisioni offline](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Esegui raccolta oggetti inattivi del datastore](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Se necessario, aggiornare lo schema del database](pre-upgrade-maintenance-tasks.md#upgrade-the-database-schema-if-needed)
* [Eliminare gli utenti che potrebbero ostacolare l’aggiornamento](pre-upgrade-maintenance-tasks.md#delete-users-that-might-hinder-the-upgrade)
* [Ruota file di registro](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Garantire spazio su disco sufficiente {#ensure-sufficient-disk-space}

Durante l’esecuzione dell’aggiornamento, oltre alle attività di aggiornamento del contenuto e del codice, sarà necessario eseguire una migrazione dell’archivio. La migrazione creerà una copia dell’archivio nel nuovo formato Segment Tar. Di conseguenza, sarà necessario spazio su disco sufficiente per mantenere una seconda versione dell’archivio, potenzialmente più grande.

## Backup completo AEM {#fully-back-up-aem}

È necessario eseguire il backup completo di AEM prima di avviare l&#39;aggiornamento. Se applicabile, assicurati di eseguire il backup dell’archivio, dell’installazione dell’applicazione, del datastore e delle istanze Mongo. Per ulteriori informazioni sul backup e il ripristino di un&#39;istanza AEM, vedere [Backup e ripristino](/help/sites-administering/backup-and-restore.md).

## Backup delle modifiche a /etc {#backup-changes-etc}

Il processo di aggiornamento consente di mantenere e unire i contenuti e le configurazioni esistenti dai percorsi `/apps` e `/libs` nell’archivio. Per le modifiche apportate al percorso `/etc`, incluse le configurazioni di Context Hub, spesso è necessario riapplicare queste modifiche dopo l’aggiornamento. Anche se l&#39;aggiornamento effettuerà una copia di backup delle modifiche che non possono essere unite in `/var`, è consigliabile eseguire manualmente il backup di queste modifiche prima di avviare l&#39;aggiornamento.

## Genera il file quickstart.properties {#generate-quickstart-properties}

Quando si avvia AEM dal file jar, un file `quickstart.properties` viene generato in `crx-quickstart/conf`. Se AEM è stato avviato solo con lo script di avvio in passato, questo file non sarà presente e l&#39;aggiornamento non riuscirà. Assicurati di verificare l&#39;esistenza di questo file e riavvia AEM dal file jar se non è presente.

## Configurare l&#39;eliminazione del flusso di lavoro e del registro di controllo {#configure-wf-audit-purging}

Le attività `WorkflowPurgeTask` e `com.day.cq.audit.impl.AuditLogMaintenanceTask` richiedono configurazioni OSGi separate e non funzioneranno senza di esse. Se non riescono durante l’esecuzione di un’attività di pre-aggiornamento, la ragione più probabile è la mancanza di configurazioni. Assicurati quindi di aggiungere le configurazioni OSGi per queste attività o rimuoverle completamente dall&#39;elenco delle attività di ottimizzazione pre-aggiornamento se non desideri eseguirle. La documentazione per la configurazione delle attività di eliminazione del flusso di lavoro si trova in [Amministrazione delle istanze del flusso di lavoro](/help/sites-administering/workflows-administering.md) e la configurazione delle attività di manutenzione del registro di controllo si trova in [Gestione del registro di controllo in AEM 6](/help/sites-administering/operations-audit-log.md).

Per l&#39;eliminazione del flusso di lavoro e del registro di controllo su CQ 5.6 e per l&#39;eliminazione del registro di controllo su AEM 6.0, consulta [Eliminare il flusso di lavoro e i nodi di controllo](https://helpx.adobe.com/experience-manager/kb/howtopurgewf.html).

## Installare, configurare ed eseguire le attività di pre-aggiornamento {#install-configure-run-pre-upgrade-tasks}

A causa del livello di personalizzazione AEM consente, gli ambienti di solito non aderiscono a un modo uniforme di eseguire gli aggiornamenti. Questo rende difficile la creazione di una procedura standardizzata per gli aggiornamenti.

Nelle versioni precedenti, era anche difficile per AEM aggiornamenti interrotti o che non sono stati ripresi in modo sicuro. Ciò portava a situazioni in cui era necessario riavviare la procedura di aggiornamento completo o in cui venivano eseguiti aggiornamenti difettosi senza attivare alcun avviso.

Per risolvere questi problemi, Adobe ha aggiunto diversi miglioramenti al processo di aggiornamento, rendendolo più flessibile e facile da usare. Le attività di manutenzione pre-aggiornamento che prima dovevano essere eseguite manualmente vengono ottimizzate e automatizzate. Inoltre, sono stati aggiunti rapporti post-aggiornamento in modo che il processo possa essere esaminato completamente nella speranza che tutti i problemi vengano trovati più facilmente.

Le attività di manutenzione pre-aggiornamento sono attualmente distribuite su varie interfacce che vengono eseguite manualmente o parzialmente. L&#39;ottimizzazione della manutenzione pre-aggiornamento introdotta in AEM 6.3 consente un modo unificato per attivare queste attività e poterne controllare i risultati su richiesta.

Tutte le attività incluse nel passaggio di ottimizzazione pre-aggiornamento sono compatibili con tutte le versioni a partire da AEM 6.0.

### Come configurarlo {#how-to-set-it-up}

In AEM 6.3 e versioni successive, le attività di ottimizzazione della manutenzione pre-aggiornamento sono incluse nel jar quickstart. Se esegui l’aggiornamento da una versione precedente di AEM 6, questi vengono resi disponibili tramite pacchetti separati che puoi scaricare da Gestione pacchetti.

Puoi trovare i pacchetti nelle seguenti posizioni:

* [Per l&#39;aggiornamento da AEM 6.0](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq600/product/pre-upgrade-tasks-content-cq60)

* [Per l&#39;aggiornamento da AEM 6.1](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/product/pre-upgrade-tasks-content-cq61)

* [Per l&#39;aggiornamento da AEM 6.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/product/pre-upgrade-tasks-content-cq62)

### Come usarlo {#how-to-use-it}

Il componente `PreUpgradeTasksMBean` OSGI è preconfigurato con un elenco di attività di manutenzione pre-aggiornamento che possono essere eseguite tutte insieme. Puoi configurare le attività seguendo la procedura seguente:

1. Vai alla Console web navigando su `https://serveraddress:serverport/system/console/configMgr`

1. Cerca &quot;**preupgradeTasks**&quot;, quindi fai clic sul primo componente corrispondente. Il nome completo del componente è `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`

1. Modificare l&#39;elenco delle attività di manutenzione da eseguire come illustrato di seguito:

   ![1487758925984](assets/1487758925984.png)

L&#39;elenco delle attività varia a seconda della modalità di esecuzione utilizzata per avviare l&#39;istanza. Di seguito è riportata una descrizione della modalità di esecuzione per cui ogni attività di manutenzione è progettata.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Attività</strong></td> 
   <td><strong>Modalità esecuzione</strong></td> 
   <td><strong>Note</strong></td> 
  </tr> 
  <tr> 
   <td><code>TarIndexMergeTask</code></td> 
   <td>crx2</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>DataStoreGarbageCollectionTask</code></td> 
   <td>crx2</td> 
   <td>Correrà mark e sweep. Per i datastore condivisi, rimuovi questo passaggio ed esegui<br /> manualmente o in modo appropriato le istanze prima dell'esecuzione.</td> 
  </tr> 
  <tr> 
   <td><code>ConsistencyCheckTask</code></td> 
   <td>crx2</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>WorkflowPurgeTask</code></td> 
   <td>crx2/crx3</td> 
   <td>È necessario configurare OSGi Adobe Granite Workflow Purge Configuration prima dell'esecuzione.</td> 
  </tr> 
  <tr> 
   <td><code>GenerateBundlesListFileTask</code></td> 
   <td>crx2/crx3</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><code>RevisionCleanupTask</code></td> 
   <td>crx3</td> 
   <td>Per le istanze TarMK su AEM 6.0 a 6.2, esegui manualmente il cleanup delle revisioni offline.</td> 
  </tr> 
  <tr> 
   <td><code>com.day.cq.audit.impl.AuditLogMaintenanceTask</code></td> 
   <td>crx3</td> 
   <td>È necessario configurare la configurazione OSGi dell’utilità di pianificazione della rimozione del registro di controllo prima dell’esecuzione.</td> 
  </tr> 
 </tbody> 
</table>

>[!CAUTION]
>
>`DataStoreGarbageCollectionTask` sta chiamando un&#39;operazione di raccolta oggetti inattivi Datastore con la fase di marcatura e sweep, se utilizzata. Per le distribuzioni che utilizzano un datastore condiviso, assicurati di riconfigurarlo o di prepararlo correttamente oppure di evitare l’eliminazione degli elementi a cui fa riferimento un’altra istanza. Questa operazione potrebbe richiedere l&#39;esecuzione manuale della fase di contrassegno su tutte le istanze prima di attivare questa attività di pre-aggiornamento.

### Configurazione predefinita dei controlli di stato pre-aggiornamento {#default-configuration-of-the-pre-upgrade-health-checks}

Il componente `PreUpgradeTasksMBeanImpl` OSGI è preconfigurato con un elenco di tag di controllo dello stato di pre-aggiornamento da eseguire quando si chiama il metodo `runAllPreUpgradeHealthChecks` :

* **sistema** : il tag utilizzato dai controlli di integrità della manutenzione granitica

* **pre-aggiornamento** : si tratta di un tag personalizzato che può essere aggiunto a tutti i controlli di integrità che è possibile impostare per l&#39;esecuzione prima di un aggiornamento

L’elenco è modificabile. È possibile utilizzare i pulsanti più **(+)** e meno **(-)** oltre ai tag per aggiungere altri tag personalizzati o rimuovere quelli predefiniti.

**Metodi MBean**

È possibile accedere alla funzionalità dei fagioli gestiti tramite la [console JMX](/help/sites-administering/jmx-console.md).

Per accedere ai MBeans:

1. Andando alla console JMX all&#39;indirizzo *https://serveraddress:serverport/system/console/jmx*
1. Cerca **PreUpgradeTasks** e fai clic sul risultato

1. Seleziona un metodo dalla sezione **Operazioni** e seleziona **Richiama** nella finestra seguente.

Di seguito è riportato un elenco di tutti i metodi disponibili esposti da `PreUpgradeTasksMBeanImpl`:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome metodo</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td><code>getAvailablePreUpgradeTasksNames()</code></td> 
   <td>INFO</td> 
   <td>Visualizza l'elenco dei nomi delle attività di manutenzione pre-aggiornamento disponibili.</td> 
  </tr> 
  <tr> 
   <td><code>getAvailablePreUpgradeHealthChecksTagNames()</code></td> 
   <td>INFORMAZIONI</td> 
   <td>Visualizza l'elenco dei nomi dei tag dei controlli di integrità pre-aggiornamento.</td> 
  </tr> 
  <tr> 
   <td><code>runAllPreUpgradeTasks()</code></td> 
   <td>AZIONE</td> 
   <td>Esegue tutte le attività di manutenzione pre-aggiornamento nell’elenco.</td> 
  </tr> 
  <tr> 
   <td><code>runPreUpgradeTask(preUpgradeTaskName)</code></td> 
   <td>AZIONE</td> 
   <td>Esegue l'attività di manutenzione pre-aggiornamento con il nome specificato come parametro.</td> 
  </tr> 
  <tr> 
   <td><code>isRunAllPreUpgradeTaskRunning()</code></td> 
   <td>ACTION_INFO</td> 
   <td>Controlla se l'attività <code>runAllPreUpgradeTasksmaintenance</code> è attualmente in esecuzione.</td> 
  </tr> 
  <tr> 
   <td><code>getAnyPreUpgradeTaskRunning()</code></td> 
   <td>ACTION_INFO</td> 
   <td>Controlla se un'attività di manutenzione pre-aggiornamento è attualmente in esecuzione e<br /> restituisce una matrice contenente i nomi delle attività in esecuzione.</td> 
  </tr> 
  <tr> 
   <td><code>getPreUpgradeTaskLastRunTime(preUpgradeTaskName)</code></td> 
   <td>AZIONE</td> 
   <td>Visualizza il tempo di esecuzione esatto dell'attività di manutenzione pre-aggiornamento con il nome specificato come parametro.</td> 
  </tr> 
  <tr> 
   <td><code>getPreUpgradeTaskLastRunState(preUpgradeTaskName)</code></td> 
   <td>AZIONE</td> 
   <td>Visualizza l'ultimo stato di esecuzione dell'attività di manutenzione pre-aggiornamento con il nome specificato come parametro.</td> 
  </tr> 
  <tr> 
   <td><code>runAllPreUpgradeHealthChecks(shutDownOnSuccess)</code></td> 
   <td>AZIONE</td> 
   <td><p>Esegue tutti i controlli di integrità pre-aggiornamento e ne salva lo stato in un file denominato <code>preUpgradeHCStatus.properties</code> che si trova nel percorso principale sling. Se il parametro <code>shutDownOnSuccess</code> è impostato su <code>true</code>, l'istanza AEM verrà chiusa, ma solo se tutti i controlli di integrità precedenti all'aggiornamento hanno uno stato OK.</p> <p>Il file delle proprietà verrà utilizzato come condizione preliminare per qualsiasi aggiornamento futuro<br /> e il processo di aggiornamento verrà interrotto se l'esecuzione del controllo dello stato di pre-aggiornamento<br /> non è riuscita. Se desideri ignorare il risultato dei controlli di integrità pre-aggiornamento<br /> e avviare comunque l'aggiornamento, puoi eliminare il file.</p> </td> 
  </tr> 
  <tr> 
   <td><code>detectUsageOfUnavailableAPI(aemVersion)</code></td> 
   <td>AZIONE</td> 
   <td>Elenca tutti i pacchetti importati che non saranno più soddisfatti quando<br /> viene eseguito l'aggiornamento alla versione AEM specificata. La versione di destinazione AEM deve essere<br /> specificata come parametro.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>I metodi MBean possono essere richiamati tramite:
>
>* Console JMX
>* Qualsiasi applicazione esterna che si connette a JMX
>* cURL

>



## Disattiva moduli di accesso personalizzati {#disable-custom-login-modules}

>[!NOTE]
>
>Questo passaggio è necessario solo se si esegue l’aggiornamento da una versione AEM 5. Può essere ignorato completamente per gli aggiornamenti dalle versioni precedenti di AEM 6.

Il modo in cui le `LoginModules` personalizzate sono configurate per l&#39;autenticazione a livello di archivio è cambiato radicalmente in Apache Oak.

Nelle versioni AEM che utilizzavano la configurazione CRX2 venivano inseriti nel file `repository.xml`, mentre a partire da AEM 6 viene eseguito nel servizio Apache Felix JAAS Configuration Factory tramite la console Web.

Pertanto, tutte le configurazioni esistenti dovranno essere disabilitate e ricreate per Apache Oak dopo l&#39;aggiornamento.

Per disabilitare i moduli personalizzati definiti nella configurazione JAAS di `repository.xml`, è necessario modificare la configurazione per utilizzare i moduli predefiniti `LoginModule`, come in questo esempio:

```xml
<Security >
             ....
          <!--
                 Use LoginModule authenticating against repository itself
                 -->
                 <LoginModule class = "com.day.crx.core.CRXLoginModule" >
                     <param name = "anonymousId" value = "anonymous" />
                     <param name = "adminId" value ="admin" />
                     <param name = "disableNTLMAuth" value = "true" />
                     <param name = "tokenExpiration" value = "43200000" />
                     <!-- param name="trust_credentials_attribute" value="d5b9167e95dad6e7d3b5d6fa8df48af8"/
                -->
                 </LoginModule >
         </ Security>
```

>[!NOTE]
>
>Per ulteriori informazioni, consulta [Autenticazione con il modulo di accesso esterno](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).
>
>Per un esempio di configurazione `LoginModule` nel AEM 6, consulta [Configurazione di LDAP con AEM 6](/help/sites-administering/ldap-config.md).

## Rimuovi aggiornamenti dalla directory /install {#remove-updates-install-directory}

>[!NOTE]
>
>Rimuovi i pacchetti solo dalla directory crx-quickstart/install DOPO aver chiuso l&#39;istanza AEM. Questo sarà uno degli ultimi passaggi prima di avviare la procedura di aggiornamento in-place.

Rimuovi tutti i service pack, i feature pack o gli hotfix distribuiti tramite la directory `crx-quickstart/install` nel file system locale. Questo impedirà l&#39;installazione involontaria di vecchi hotfix e service pack sulla nuova versione AEM al termine dell&#39;aggiornamento.

## Interrompi istanze di standby a freddo {#stop-tarmk-coldstandby-instance}

Se si utilizza lo standby a freddo di TarMK, arrestare le istanze di standby a freddo. Questo garantirà un modo efficiente di tornare online in caso di problemi nell&#39;aggiornamento. Una volta completato correttamente l’aggiornamento, le istanze di standby a freddo dovranno essere ricreate dalle istanze primarie aggiornate.

## Disattiva processi pianificati personalizzati {#disable-custom-scheduled-jobs}

Disattiva tutti i processi pianificati OSGi inclusi nel codice dell&#39;applicazione.

## Esegui pulizia revisioni offline {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Questo passaggio è necessario solo per le installazioni TarMK

Se utilizzi TarMK, devi eseguire il cleanup delle revisioni offline prima di eseguire l&#39;aggiornamento. In questo modo la fase di migrazione dell&#39;archivio e le successive attività di aggiornamento verranno eseguite molto più velocemente e sarà utile per garantire che il cleanup delle revisioni online possa essere eseguito correttamente al termine dell&#39;aggiornamento. Per informazioni sull&#39;esecuzione del cleanup delle revisioni offline, vedere [Esecuzione del cleanup delle revisioni offline](https://helpx.adobe.com/experience-manager/6-2/sites-deploying/storage-elements-in-aem-6.html#performing-offline-revision-cleanup).

## Esegui raccolta oggetti inattivi del datastore {#execute-datastore-garbage-collection}

>[!NOTE]
>
>Questo passaggio è necessario solo per le istanze che eseguono crx3

Dopo aver eseguito la pulizia revisioni sulle istanze CRX3, esegui la raccolta oggetti inattivi Datastore per rimuovere eventuali BLOB non referenziati nell&#39;archivio dati. Per istruzioni, consulta la documentazione su [Raccolta rifiuti del Data Store](/help/sites-administering/data-store-garbage-collection.md).

## Eliminare gli utenti che potrebbero ostacolare l&#39;aggiornamento {#delete-users-that-might-hinder-the-upgrade}

>[!NOTE]
>
>Questa attività di manutenzione pre-aggiornamento è necessaria solo se:
>
>* È in corso l&#39;aggiornamento da AEM versioni precedenti a AEM 6.3
>* Durante l&#39;aggiornamento si verifica uno degli errori indicati di seguito.


Ci sono casi eccezionali in cui gli utenti del servizio possono finire in una versione precedente AEM con tag non corretti come utenti normali.

Se questo accade, l&#39;aggiornamento avrà esito negativo con un messaggio come questo:

```
ERROR [Apache Sling Repository Startup Thread] com.adobe.granite.repository.impl.SlingRepositoryManager Exception in a SlingRepositoryInitializer, SlingRepository service registration aborted
java.lang.RuntimeException: Unable to create service user [communities-utility-reader]:java.lang.RuntimeException: Existing user communities-utility-reader is not a service user.
```

Per risolvere questo problema, assicurati di effettuare le seguenti operazioni:

Per risolvere questo problema, assicurati di effettuare le seguenti operazioni:

* Stacca l’istanza dal traffico di produzione
* Crea un backup degli utenti che causano il problema. Puoi eseguire questa operazione tramite Gestione pacchetti. Per ulteriori informazioni, vedere [Come lavorare con i pacchetti](/help/sites-administering/package-manager.md).
* Elimina gli utenti che causano il problema. Di seguito è riportato un elenco di utenti che potrebbero rientrare in questa categoria:
   * dynamic-media-replication
   * community-ugc-writer
   * lettore di utilità pubblica
   * community-user-admin
   * oauthservice
   * sling-scripting

## Aggiornare lo schema di database se necessario {#upgrade-the-database-schema-if-needed}

Di solito, lo stack Apache Oak sottostante utilizzato AEM per la persistenza si occuperà di aggiornare lo schema del database, se necessario.

Tuttavia, potrebbero verificarsi casi in cui lo schema non può essere aggiornato automaticamente. Si tratta per lo più di ambienti di sicurezza di elevata qualità in cui il database è in esecuzione sotto un utente con privilegi molto limitati. In questo caso, AEM continuerà a utilizzare il vecchio schema.

Per evitare che ciò si verifichi, devi aggiornare lo schema seguendo la procedura seguente:

1. Arresta l&#39;istanza AEM che deve essere aggiornata.
1. Aggiornare lo schema del database. Consulta la documentazione relativa al tipo di database in uso per vedere quali strumenti devi utilizzare per ottenere questo risultato.

   Per ulteriori informazioni su come Oak gestisce gli aggiornamenti dello schema, consulta [questa pagina sul sito web Apache](https://jackrabbit.apache.org/oak/docs/nodestore/document/rdb-document-store.html#upgrade).

1. Procedi con l&#39;aggiornamento AEM.

## Ruota file di registro {#rotate-log-files}

È consigliabile archiviare i file di registro correnti prima di avviare l&#39;aggiornamento. In questo modo sarà più facile monitorare e scansionare i file di registro durante e dopo l&#39;aggiornamento per identificare e risolvere eventuali problemi.
