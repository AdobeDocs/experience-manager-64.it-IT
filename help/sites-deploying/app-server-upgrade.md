---
title: Passaggi di aggiornamento per le installazioni di Application Server
seo-title: Passaggi di aggiornamento per le installazioni di Application Server
description: Scopri come aggiornare le istanze di AEM distribuite tramite Application Server.
seo-description: Scopri come aggiornare le istanze di AEM distribuite tramite Application Server.
uuid: df3fa715-af4b-4c81-b2c5-130fbc82f395
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: c427c8b6-eb94-45fa-908f-c3d5a337427d
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Passaggi di aggiornamento per le installazioni di Application Server{#upgrade-steps-for-application-server-installations}

Questa sezione descrive la procedura da seguire per aggiornare AEM per le installazioni di Application Server.

Tutti gli esempi in questa procedura utilizzano JBoss come Application Server e implicano che una versione funzionante di AEM è già distribuita. La procedura è destinata a documentare gli aggiornamenti eseguiti da **AEM versione 5.6 a 6.3**.

1. Innanzitutto, avvia JBoss. Nella maggior parte delle situazioni, è possibile eseguire lo script di avvio `standalone.sh` eseguendo questo comando dal terminale:

   ```shell
   jboss-install-folder/bin/standalone.sh
   ```

1. Se AEM 5.6 è già distribuito, controlla che i bundle funzionino correttamente eseguendo:

   ```shell
   wget https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Quindi, annulla la distribuzione di AEM 5.6:

   ```shell
   rm jboss-install-folder/standalone/deployments/cq.war
   ```

1. Ferma JBoss.

1. Ora, esegui la migrazione dell&#39;archivio utilizzando lo strumento di migrazione crx2oak:

   ```shell
   java -jar crx2oak.jar crx-quickstart/repository/ crx-quickstart/oak-repository
   ```

   >[!NOTE]
   >
   >In questo esempio, oak-repository è la directory temporanea in cui risiederà il repository appena convertito. Prima di eseguire questo passaggio, assicurati di disporre dell’ultima versione di crx2oak.jar.

1. Elimina le proprietà necessarie nel file sling.properties facendo quanto segue:

   1. Apri il file che si trova in `crx-quickstart/launchpad/sling.properties`
   1. Testo del passaggio Rimuovi le seguenti proprietà e salva il file:

      1. `sling.installer.dir`
      1. `felix.cm.dir`
      1. `granite.product.version`
      1. `org.osgi.framework.system.packages`
      1. `osgi-core-packages`
      1. `osgi-compendium-services`
      1. `jre-*`
      1. `sling.run.mode.install.options`

1. Rimuovi i file e le cartelle non più necessari. Gli elementi da rimuovere sono:

   * La **cartella launchpad/startup**. È possibile eliminarlo eseguendo il seguente comando nel terminale: `rm -rf crx-quickstart/launchpad/startup`
   * Il file **base.jar**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`
   * Il file **BootstrapCommandFile_timestamp.txt**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

1. Copia l&#39;archivio segmenti appena migrato nella posizione corretta:

   ```shell
   mv crx-quickstart/oak-repository/segmentstore crx-quickstart/repository/segmentstore
   ```

1. Copia anche il datastore:

   ```shell
   mv crx-quickstart/repository/repository/datastore crx-quickstart/repository/datastore
   ```

1. Successivamente, devi creare la cartella che conterrà le configurazioni OSGi che verranno utilizzate con la nuova istanza aggiornata. Più specificamente, una cartella denominata install deve essere creata in **crx-quickstart**.

1. A questo punto, crea l&#39;archivio nodi e l&#39;archivio dati che verranno utilizzati con AEM 6.3. Puoi farlo creando due file con i seguenti nomi in **crx-quickstart\install**:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`

   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Questi due file configureranno AEM per utilizzare un archivio nodi TarMK e un archivio dati File.

1. Modifica i file di configurazione per renderli pronti all’uso. Più precisamente:

   * Aggiungi la seguente riga a **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**:

      `customBlobStore=true`

   * Quindi aggiungi le seguenti righe a **org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**:

      ```
      path=./crx-quickstart/repository/datastore
       minRecordLength=4096
      ```

1. Rimuovi la modalità runmode crx2 eseguendo:

   ```shell
   find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \
   ```

1. È ora necessario modificare le modalità di esecuzione nel file di guerra AEM 6.3. Per farlo, crea innanzitutto una cartella temporanea che ospiterà la guerra AEM 6.3. Il nome della cartella in questo esempio sarà **temp**. Una volta copiato il file WAR, estrarne il contenuto eseguendo la cartella temporanea:

   ```shell
   jar xvf aem-quickstart-6.3.0.war
   ```

1. Una volta estratto il contenuto, vai alla cartella **WEB-INF** e modifica il file `web.xml` per modificare le modalità di esecuzione. Per trovare la posizione in cui sono impostati nell&#39;XML, cercare la stringa `sling.run.modes`. Una volta trovato, modifica le modalità di esecuzione nella riga di codice successiva, che per impostazione predefinita è impostata per l’authoring:

   ```shell
   <param-value >author</param-value>
   ```

1. Modifica il valore dell&#39;autore riportato sopra e imposta le modalità di esecuzione su: autore,crx3,crx3tar Il blocco di codice finale dovrebbe essere così:

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. Ricrea il jar con il contenuto modificato:

   ```shell
   jar cvf aem62.war
   ```

1. Infine, distribuire il nuovo file war:

   ```shell
   cp temp/aem62.war jboss-install-folder/standalone/deployments/aem61.war
   ```

