---
title: Installazione personalizzata indipendente
seo-title: Installazione personalizzata indipendente
description: 'Scoprite le opzioni disponibili durante l''installazione di un''istanza AEM autonoma. '
seo-description: 'Scoprite le opzioni disponibili durante l''installazione di un''istanza AEM autonoma. '
uuid: e1cb45c4-3b2b-4951-8f67-213072e825b3
contentOwner: Tyler Rushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: c9e51008-6009-49a2-9c74-1c610cef2e7f
translation-type: tm+mt
source-git-commit: b7e5c42009acb5044d1112e66b8e65b528355736
workflow-type: tm+mt
source-wordcount: '1523'
ht-degree: 1%

---


# Installazione personalizzata indipendente{#custom-standalone-install}

Questa sezione descrive le opzioni disponibili durante l&#39;installazione di un&#39;istanza AEM autonoma. Per ulteriori informazioni sulla scelta del tipo di storage di back-end dopo aver installato AEM 6, è inoltre possibile leggere [Storage Elements](/help/sites-deploying/storage-elements-in-aem-6.md) .

## Modifica del numero di porta rinominando il file {#changing-the-port-number-by-renaming-the-file}

La porta predefinita per AEM è 4502. Se la porta non è disponibile o è già in uso, Quickstart si configura automaticamente per utilizzare il primo numero di porta disponibile, come segue: 4502, 8080, 8081, 8082, 8083, 8084, 8085, 8888, 9362, `<random>`.

Potete anche impostare il numero di porta rinominando il file JAR di QuickStart in modo che il nome del file includa il numero di porta; ad esempio `cq5-publish-p4503.jar` o `cq5-author-p6754.jar`.

Quando si rinomina il file Jar di QuickStart è necessario attenersi a diverse regole:

* Quando si rinomina il file, questo deve iniziare con `cq;` come in `cq5-publish-p4503.jar`.

* Si consiglia di *assegnare sempre* il prefisso -p al numero di porta; come in cq5-publish-p4503.jar o cq5-author-p6754.jar.

>[!NOTE]
>
>Per evitare di dover rispettare le regole utilizzate per l&#39;estrazione del numero di porta:
>
>* il numero di porta deve essere di 4 o 5 cifre
>* queste cifre devono essere riportate dopo un trattino
>* se nel nome del file sono presenti altre cifre, il numero della porta deve avere il prefisso `-p`
>* il prefisso &quot;cq5&quot; all’inizio del nome del file viene ignorato

>



>[!NOTE]
>
>È inoltre possibile modificare il numero di porta utilizzando l&#39; `-port` opzione nel comando start.

## Modalità di esecuzione {#run-modes}

**Le modalità** di esecuzione consentono di sintonizzare l’istanza AEM per uno scopo specifico; ad esempio, autore o pubblicazione, test, sviluppo, Intranet ecc. Queste modalità consentono anche di controllare l’utilizzo di contenuti campione. Questo contenuto di esempio viene definito prima della creazione dell&#39;avvio rapido e può includere pacchetti, configurazioni e così via. Questa funzione può essere particolarmente utile per le installazioni pronte per la produzione, quando si desidera mantenere l&#39;installazione snella e senza contenuti campione. Per ulteriori informazioni, consultare:

* [Modalità di esecuzione](/help/sites-deploying/configure-runmodes.md)

## Aggiunta di un provider di installazione file {#adding-a-file-install-provider}

Per impostazione predefinita, la cartella `crx-quickstart/install` viene controllata per i file.\
Questa cartella non esiste, ma può essere creata semplicemente in fase di esecuzione.

Se in questa directory viene inserito un bundle, un pacchetto di configurazione o un pacchetto di contenuti, questo viene automaticamente rilevato e installato. Se viene rimosso, viene disinstallato.\
È un altro modo per inserire pacchetti, pacchetti di contenuti o configurazioni nella directory archivio.

Questo è particolarmente interessante per diversi casi d&#39;uso:

* Durante lo sviluppo, potrebbe essere più semplice inserire qualcosa nel file system.
* Se qualcosa va storto, la console Web e il repository non sono raggiungibili. Con questo è possibile inserire pacchetti aggiuntivi in questa directory e dovrebbero essere installati.
* La `crx-quickstart/install` cartella può essere creata prima dell&#39;avvio rapido e possono essere inseriti pacchetti aggiuntivi.

>[!NOTE]
>
>Per esempi, vedere anche [Come installare automaticamente i pacchetti CRX all&#39;avvio](https://helpx.adobe.com/experience-manager/kb/HowToInstallPackagesUsingRepositoryInstall.html) del server.

## Installazione e avvio di Adobe Experience Manager come servizio Windows {#installing-and-starting-adobe-experience-manager-as-a-windows-service}

>[!NOTE]
>
>Assicuratevi di eseguire la procedura seguente durante l&#39;accesso come amministratore oppure di avviare/eseguire questi passaggi tramite la selezione del menu di scelta rapida **Esegui come amministratore** .
>
>L&#39;accesso come utente con privilegi di amministratore è **insufficiente**. Se non avete eseguito l&#39;accesso come amministratore al completamento di questi passaggi, ricevete errori **Accesso negato** .

Per installare e avviare AEM come servizio Windows:

1. Aprite il file crx-quickstart\opt\helpers\instsrv.bat in un editor di testo.
1. Se state configurando un server Windows a 64 bit, sostituite tutte le istanze di prunsrv con uno dei seguenti comandi, in base al sistema operativo in uso:

   * prunsrv_amd64
   * prunsrv_ia64

   Questo comando richiama lo script appropriato che avvia il daemon del servizio Windows in Java a 64 bit anziché in Java a 32 bit.

1. Per evitare che il processo si trasformi in più processi, aumentare la dimensione massima dell&#39;heap e i parametri JVM PermGen. Individuate il `set jvm_options` comando e impostate il valore come segue:

   `set jvm_options=-XX:MaxPermSize=256M;-Xmx1792m`

1. Aprite il prompt dei comandi, modificate la directory corrente nella cartella crx-quickstart/opt/helpers dell&#39;installazione AEM, quindi immettete il comando seguente per creare il servizio:

   `instsrv.bat cq5`

   Per verificare che il servizio sia stato creato, aprire Servizi nel pannello di controllo Strumenti di amministrazione o digitare `start services.msc` in Prompt dei comandi. Il servizio cq5 viene visualizzato nell’elenco.

1. Avviate il servizio effettuando una delle seguenti operazioni:

   * Nel pannello di controllo Servizi, fate clic su cq5 e fate clic su Avvia.

   ![chlimage_1-71](assets/chlimage_1-71.png)

   * Nella riga di comando, digitare net start cq5.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Windows indica che il servizio è in esecuzione. AEM viene avviato e l&#39;eseguibile prunsrv viene visualizzato in Task Manager. Nel browser Web, andate a AEM, ad esempio, `http://localhost:4502` per iniziare a utilizzare AEM.

   ![chlimage_1-73](assets/chlimage_1-73.png)

>[!NOTE]
>
>I valori delle proprietà nel file instsrv.bat vengono utilizzati durante la creazione del servizio Windows. Se modificate i valori delle proprietà in instsrv.bat, dovete disinstallare e reinstallare il servizio.

>[!NOTE]
>
>Durante l&#39;installazione di AEM come servizio, dovete fornire il percorso assoluto per la directory dei registri in `com.adobe.xmp.worker.files.ncomm.XMPFilesNComm` da Configuration Manager.

Per disinstallare il servizio, fare clic su **Interrompi** nel pannello di controllo **Servizi** o nella riga di comando, passare alla cartella e digitare `instsrv.bat -uninstall cq5`. Il servizio viene rimosso dall&#39;elenco nel pannello di controllo **Servizi** o dall&#39;elenco nella riga di comando quando si digita `net start`.

## Ridefinizione della posizione della directory di lavoro temporaneo {#redefining-the-location-of-the-temporary-work-directory}

Il percorso predefinito della cartella temporanea del computer Java è `/tmp`. AEM utilizza anche questa cartella, ad esempio per la creazione di pacchetti.

Se si desidera modificare la posizione della cartella temporanea (ad esempio, se è necessaria una directory con più spazio libero), definire una `<new-tmp-path>` aggiungendo il parametro JVM:

`-Djava.io.tmpdir="/<new-tmp-path>"`

a:

* la riga di comando di avvio del server
* parametro di ambiente CQ_JVM_OPTS nello script serverctl o start

## Ulteriori opzioni disponibili nel file Quickstart {#further-options-available-from-the-quickstart-file}

Ulteriori opzioni e convenzioni di ridenominazione sono descritte nel file della guida di Quickstart, disponibile tramite l&#39;opzione -help. Per accedere alla guida, digitare:

* `java -jar cq5-<version>.jar -help`

```shell
Loading quickstart properties: default
Loading quickstart properties: instance
Setting properties from filename '/Users/Desktop/AEM/cq-quickstart-5.6.0.jar'
--------------------------------------------------------------------------------
Adobe Experience Manager Quickstart (build 20130129)                            
--------------------------------------------------------------------------------
Usage:                                                                          
 Use these options on the Quickstart command line.                              
--------------------------------------------------------------------------------

-help (--help,-h)
         Show this help message                                                 
-quickstart.server.port (-p,-port) <port>
         Set server port number                                                 
-contextpath (-c,-org.apache.felix.http.context_path) <contextpath>
         Set context path                                                       
-debug <port>
         Enable Java Debugging on port number; forces forking                   
-gui 
         Show GUI if running on a terminal                                      
-nobrowser (-quickstart.nobrowser)
         Do not open browser at startup                                         
-unpack
         Unpack installation files only, do not start the server (implies       
         -verbose)                                                              
-v (-verbose)
         Do not redirect stdout/stderr to files and do not close stdin          
-nofork
         Do not fork the JVM, even if not running on a console                  
-fork
         Force forking the JVM if running on a console, using recommended       
         default memory settings for the forked JVM.                            
-forkargs <args> [<args> ...]
         Additional arguments for the forked JVM, defaults to '-Xmx1024m        
         -XX:MaxPermSize=256m '.  Use -- to specify values starting with -,     
         example: '-forkargs -- -server'                                        
-a (--interface) <interface>
         Optional IP address (interface) to bind to                             
-pt <string>
         Process type (main/fork) - do not use directly, used when forking a    
         process                                                                
-r <string> [<string> [<string> [<string> [<string> [<string> [<string> [<string> [<string> [<string>]]]]]]]]]
         Runmode(s) - Use this to define the run mode(s)                        
-b <string>
         Base folder - defines the path under which the quickstart work folder  
         is created                                                             
-low-mem-action <string>
         Low memory action - what to do if memory is insufficient at startup    
-use-control-port
         Start a control port                                                   
-ll <level>
         Define launchpad log level (1 = error...4 = debug)                     
--------------------------------------------------------------------------------
Quickstart filename options                                                     
--------------------------------------------------------------------------------
Usage:                                                                          
 Rename the jar file, including one of the patterns shown below, to set the     
corresponding option. Command-line options have priority on these filename      
patterns.                                                                       
--------------------------------------------------------------------------------

-NNNN
         Include -NNNN.jar or -pNNNN in the renamed jar filename to run on port 
         NNNN, for example: quickstart-8085.jar                                 
-nobrowser
         Include -nobrowser in the renamed jar filename to avoid opening the    
         browser at startup, example: quickstart-nobrowser-8085.jar             
-publish
         Include -publish in the renamed jar filename to run cq5 in "publish"   
         mode, example: cq5-publish-7502.jar                                    
--------------------------------------------------------------------------------
The license.properties file
--------------------------------------------------------------------------------
  The license.properties file stores licensing information, created from the    
  licensing form displayed on first startup and stored in the folder from where 
  Quickstart is run.                                                            
--------------------------------------------------------------------------------
Log files
--------------------------------------------------------------------------------
  Once Quickstart has been unpacked and started, log files can be found under   
  ./crx-quickstart/logs.                                                        
--------------------------------------------------------------------------------
```

## Installazione di AEM nell&#39;ambiente Amazon EC2  {#installing-aem-in-the-amazon-ec-environment}

Durante l&#39;installazione di AEM su un&#39;istanza di Amazon Elastic Compute Cloud (EC2) , se si installano sia l&#39;autore che la pubblicazione sull&#39;istanza EC2, l&#39;istanza Author viene installata correttamente seguendo la procedura per [installare un&#39;istanza di AEM](/help/sites-deploying/custom-standalone-install.md); tuttavia, l’istanza Pubblica diventa Autore.

Prima di installare l’istanza Pubblica nell’ambiente EC2, effettuate le seguenti operazioni:

1. Decomprimete il file jar per l’istanza Pubblica prima di avviare l’istanza per la prima volta. Per decomprimere il file, utilizzare il comando seguente:

   ```xml
   java -jar quickstart.jar -unpack
   ```

   >[!NOTE]
   >
   >Se si modifica la modalità **dopo** l&#39;avvio dell&#39;istanza la prima volta, non è possibile modificare la modalità di esecuzione.

1. Avviare l&#39;istanza eseguendo:

   ```xml
   java -jar quickstart.jar -r publish
   ```

   >[!CAUTION]
   >
   >Prima di eseguire l&#39;istanza dopo averlo decompresso, eseguire il comando precedente. In caso contrario, il riempimento quickstart.properties non verrà generato. Senza questo file, eventuali aggiornamenti futuri AEM non funzioneranno.

1. Nella cartella **bin** , aprite lo script **start** e verificate la sezione seguente:

   ```xml
   # runmode(s)
   if [ -z "$CQ_RUNMODE" ]; then
    CQ_RUNMODE='author'
   fi
   ```

1. Modificate la modalità di esecuzione per **pubblicare** e salvare il file.

   ```xml
   # runmode(s)
   if [ -z "$CQ_RUNMODE" ]; then
    CQ_RUNMODE='publish'
   fi
   ```

1. Arrestate l&#39;istanza e riavviatela eseguendo lo script **start** .

## Verifica dell’installazione {#verifying-the-installation}

I seguenti collegamenti possono essere utilizzati per verificare che l&#39;installazione sia operativa (tutti gli esempi si basano sul fatto che l&#39;istanza è in esecuzione sulla porta 8080 del localhost, che CRX è installato in /crx e Launchpad in /):

* `http://localhost:8080/crx/de`

   La console CRXDE Lite.

* `http://localhost:8080/system/console`

   Console Web.

## Azioni dopo l’installazione {#actions-after-installation}

Anche se esistono molte possibilità di configurare AEM WCM, alcune azioni devono essere intraprese, o almeno revisionate immediatamente dopo l&#39;installazione:

* Consultate l&#39; [elenco](/help/sites-administering/security-checklist.md) di controllo della sicurezza per verificare che il sistema rimanga protetto.
* Esaminate l&#39;elenco degli utenti e dei gruppi predefiniti installati con AEM WCM. Per ulteriori informazioni, consulta [Sicurezza e amministrazione](/help/sites-administering/security.md) utenti.

## Accesso a CRXDE Lite e console Web {#accessing-crxde-lite-and-the-web-console}

Una volta avviato AEM WCM, potete accedere anche a:

* [CRXDE Lite](#accessing-crxde-lite) : utilizzato per accedere e gestire l&#39;archivio
* [Console](#accessing-the-web-console) Web: utilizzata per gestire o configurare i bundle OSGi (detta anche console OSGi)

### Accesso a CRXDE Lite {#accessing-crxde-lite}

Per aprire il CRXDE Lite, potete selezionare il **CRXDE Lite** dalla schermata di benvenuto o utilizzare il browser per passare a

```
 https://<<i>host</i>>:<<i>port</i>>/crx/de/index.jsp
```

Ad esempio:\
`http://localhost:4502/crx/de/index.jsp` ``

![installcq_crxdelite](assets/installcq_crxdelite.png)

### Accesso alla console Web {#accessing-the-web-console}

Per accedere alla console Web di  Adobe CQ potete selezionare Console **** OSGi dalla schermata introduttiva oppure utilizzare il browser per accedere a

```
 https://<<i>host</i>>:<<i>port</i>>/system/console
```

Ad esempio:\
`http://localhost:4502/system/console`\
o per la pagina Bundle\
`http://localhost:4502/system/console/bundles`

![chlimage_1-74](assets/chlimage_1-74.png)

Per ulteriori informazioni, consulta Configurazione [OSGi con la console](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) Web.

## Risoluzione dei problemi {#troubleshooting}

Per informazioni su come risolvere i problemi che possono verificarsi durante l&#39;installazione, vedete:

* [Risoluzione dei problemi](/help/sites-deploying/troubleshooting.md)

## Uninstalling Adobe Experience Manager {#uninstalling-adobe-experience-manager}

Poiché AEM installato in una singola directory, non è necessario installare un&#39;utilità di disinstallazione. La disinstallazione può essere semplice come l&#39;eliminazione dell&#39;intera directory di installazione, anche se la modalità di disinstallazione AEM dipende da ciò che si desidera ottenere e da quale archivio permanente si utilizza.

Se la memorizzazione persistente è incorporata nella directory di installazione, ad esempio, nell&#39;installazione predefinita di TarPM, l&#39;eliminazione di cartelle rimuove anche i dati.

>[!NOTE]
>
> Adobe consiglia vivamente di eseguire il backup del repository prima di eliminare AEM. Se si elimina l&#39;intero &lt;cq-install-directory>, si elimina il repository. Per conservare i dati del repository prima di eliminare, spostare o copiare la cartella &lt;cq-install-directory>/crx-quickstart/repository altrove prima di eliminare le altre cartelle.

Se l&#39;installazione di AEM utilizza un archivio esterno, ad esempio un server di database, la rimozione della cartella non rimuove automaticamente i dati, ma rimuove la configurazione di storage, il che rende difficile il ripristino del contenuto JCR.
