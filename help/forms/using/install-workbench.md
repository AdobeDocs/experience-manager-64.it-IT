---
title: Installare workbench
seo-title: Install workbench
description: Installa workbench.
uuid: null
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: null
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2779'
ht-degree: 0%

---


# Installare workbench {#install-workbench}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questo documento fornisce istruzioni per l’installazione e la configurazione di workbench. Il programma di installazione installa anche Designer.

## Informazioni su {#about}

Questo documento è destinato agli amministratori o agli sviluppatori responsabili dell’installazione, della configurazione, dell’amministrazione o della distribuzione di Workbench.
Sono incluse anche le informazioni necessarie per configurare il sistema in modo da supportare i processi aggiornati Adobe® AEM forms® Enterprise Suite (ES) Update 1 (8.2.x) e Adobe® AEM forms® Enterprise Suite 2 (ES2).
Le informazioni fornite si basano sul presupposto che chiunque legga questo documento abbia familiarità con il sistema operativo Microsoft® Windows®.

## Informazioni aggiuntive {#additional-information}

Le risorse presenti in questa tabella sono utili per ulteriori informazioni e per iniziare a utilizzare AEM Forms.
<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Per informazioni su</strong></p> </td> 
   <td><p><strong>Consulta</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Informazioni procedurali per Workbench</p> </td> 
   <td><p><a href="http://www.adobe.com/go/learn_aemforms_workbench_61">Guida di Workbench</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Informazioni generali su AEM Forms e su come si integra con altri prodotti Adobe</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">Panoramica di AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Esercitazione per creare un’applicazione AEM Forms e testarla in workspace</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_firstapp_ds_65">Creazione della prima applicazione AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Tutta la documentazione disponibile per AEM Forms</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">Documentazione di AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Altri servizi e prodotti che si integrano con AEM Forms</p> </td> 
   <td><p><a href="http://www.adobe.com/it/">www.adobe.com</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Aggiornamenti patch, note tecniche e informazioni aggiuntive su questa versione del prodotto</p> </td> 
   <td><p><a href="https://www.adobe.com/account/sign-in.supportportal.html">Contatta il supporto Adobe Enterprise</a><br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>L’area di lavoro Flex è obsoleta per AEM Forms. È disponibile per la versione AEM Forms.

## Prima dell’installazione {#before-you-install}

### Panoramica sull’installazione di Workbench {#workbench-installation-overview}

Workbench è un ambiente di sviluppo integrato (IDE) utilizzato dagli sviluppatori e dagli autori di moduli per creare processi e moduli aziendali automatizzati. Viene inoltre utilizzato per gestire le risorse e i servizi utilizzati dai processi e dai moduli.

La figura seguente illustra l’installazione di Workbench, che include:
* Progettazione dei processi con Workbench
* Struttura del modulo con Designer

>[!NOTE]
>
>Il server AEM Forms richiede un programma di installazione separato. Per ulteriori informazioni consulta la documentazione di installazione di AEM Forms su JEE .

## Prerequisiti del sistema {#system-prerequisites}

Questa sezione descrive i requisiti hardware e software e le piattaforme supportate.

### Requisiti minimi di hardware e software {#minimum-hardware-software-requirements}

**Workbench**
Si raccomandano come minimo i seguenti requisiti: Spazio su disco per l&#39;installazione:
* 680 MB solo per Workbench.
* 2,15 GB su un&#39;unica unità per un&#39;installazione completa di Workbench, Designer e dell&#39;assembly dei campioni.
* 400 MB per le directory di installazione temporanea - 200 MB nella directory \temp dell&#39;utente e 200 MB nella directory temporanea di Windows.

>[!NOTE]
>
>Se tutte queste posizioni risiedono su un&#39;unica unità, durante l&#39;installazione deve essere disponibile uno spazio di 1,5 GB. I file copiati nelle directory temporanee vengono eliminati al termine dell&#39;installazione.

* Requisiti hardware: Processore Intel® Pentium® 4 o AMD equivalente, 1 GHz.
* Scarica e installa la versione più recente di Adobe AIR (da <a href="http://www.adobe.com/it/">www.adobe.com</a>) necessaria per il client di assistenza della community, integrato con Workbench.
* Java™ Runtime Environment (JRE) 6.0 aggiorna 22 o versioni successive alla versione 6.0 *Novità per 10*.
* Risoluzione minima del monitor di 1024 X 768 pixel o superiore con colore a 16 bit o superiore.
* Connessione di rete TCP/IPv4 o TCP/IPv6 al server AEM Forms.
* Installa Visual C++ Redistributable Runtime Packages 2012 a 32 bit.
* Installa Visual C++ Redistributable Runtime Packages 2013 a 32 bit.

>[!NOTE]
>
>Se sul computer è installato Adobe® Acrobat® X, assicurarsi di disinstallarlo prima di installare Workbench. È possibile reinstallare Acrobat dopo aver installato Workbench.

>[!NOTE]
>
>Per installare Workbench è necessario disporre dei privilegi di amministratore. Se stai effettuando l’installazione utilizzando un account non amministratore, il programma di installazione ti chiederà le credenziali per un account appropriato.

### Piattaforme supportate {#supported-platforms}

Vedi l’elenco completo delle piattaforme supportate per Workbench all’indirizzo [Piattaforme supportate da AEM Forms](http://adobe.com/go/learn_aemforms_supportedplatforms_65).

## Considerazioni sull’installazione di Designer {#designer-installation-considerations}

Per impostazione predefinita, l’installazione di Workbench include una versione di Designer in lingua inglese corrispondente. Se l&#39;applicazione di installazione di Workbench rileva una versione esistente di Designer sul computer in uso, l&#39;installazione potrebbe terminare e sarà necessario rimuovere la versione corrente di Designer prima di continuare.
Nella tabella seguente è riportato un elenco completo dei possibili scenari di installazione di Designer che è possibile incontrare, nonché delle azioni da intraprendere durante l’installazione di Workbench.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Versione di Designer attualmente installata</strong></p> </td> 
   <td><p><strong>Azioni necessarie</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Acrobat Pro o Acrobat Pro Extended (incluso Designer)</p> </td> 
   <td><p>Nessuno. L’installazione di Workbench rileva nel computer un’istanza di Designer installata con Acrobat Pro o Acrobat Pro Extended.
Sullo stesso sistema possono coesistere diverse versioni di Designer, ad esempio Designer 8.2.x e 9.0.x. Non è necessario disinstallare la versione di Designer installata con Acrobat 10 Pro o Acrobat 10 Pro Extended.
<br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Designer (autonomo)</p> </td> 
   <td><p>Nessuno. La versione di Designer inclusa in Workbench è disponibile solo in lingua inglese. Il programma di installazione di Workbench non reinstallerà una nuova versione di Designer. Verrà invece applicata una versione aggiornata, inclusa nel pacchetto di installazione di Workbench. Consente inoltre di utilizzare la versione localizzata di Designer all’interno di Workbench.<br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

### Disinstallazione di Designer (autonoma) {#uninstall-designer-standalone}

1. Vai a **Pannello di controllo Campaign > Programmi > Programmi e funzionalità**
1. Nell&#39;elenco Programmi attualmente installati, selezionare **Adobe Designer**.
1. Fai clic su **Disinstalla** quindi fai clic su **Sì**.

### Disinstallazione di Designer (autonomo) su Windows 10 {#uninstall-designer-standalone-windows10}

1. Vai a **Pannello di controllo Campaign > Programmi > Programmi e funzionalità**
1. Nell&#39;elenco Programmi attualmente installati, selezionare **Adobe Designer**.
1. Fai clic su **Disinstalla** quindi fai clic su **Sì**.

### Disinstallazione di Designer incluso in Acrobat Pro o Acrobat Pro Extended {#uninstall-designer-included-with-acrobatpro-or-acrobatextended}

1. Vai a **Pannello di controllo Campaign > Programmi > Programmi e funzionalità**
1. Nell&#39;elenco Programmi attualmente installati, selezionare **Adobe Acrobat Pro** o **Adobe Acrobat Pro Extended**.
1. Fai clic su **Modifica** quindi fai clic su **Successivo**.
1. Seleziona **Modifica** quindi fai clic su **Successivo**.
1. Seleziona **Adobe Designer**, seleziona **Questa funzionalità non sarà disponibile**, quindi fai clic su **Successivo**
1. Fai clic su **Aggiorna** quindi fai clic su **Fine**

### Disinstallazione di Designer incluso in Acrobat Pro o Acrobat Pro Extended su Windows 10 {#uninstall-designer-included-with-acrobatpro-or-acrobatextended-windows10}

1. Vai a **Pannello di controllo Campaign > Programmi > Programmi e funzionalità**
1. Nell&#39;elenco Programmi attualmente installati, selezionare **Adobe Acrobat Pro** o **Adobe Acrobat Pro Extended**.
1. Fai clic su **Modifica** quindi fai clic su **Successivo**.
1. Seleziona **Modifica** quindi fai clic su **Successivo**.
1. Seleziona **Adobe Designer**, seleziona **Questa funzionalità non sarà disponibile**, quindi fai clic su **Successivo**
1. Fai clic su **Aggiorna** quindi fai clic su **Fine**

## Installazione di Workbench {#installing-workbench}

Questo capitolo descrive come installare Workbench.

### Installazione ed esecuzione di Workbench {#installing-and-running-workbench}

Prima di installare Workbench, è necessario assicurarsi che l’ambiente includa il software e l’hardware necessari per eseguirlo (vedere la sezione: **Prima dell’installazione**).

**Per installare ed eseguire Workbench:**

1. Effettuare una delle seguenti operazioni:
   * Passa alla directory \workbench nel supporto di installazione e fai doppio clic sul file run_windows_installer.bat.
   * Scarica e decomprimi Workbench nel file system. Dopo il download, accedi alla directory \workbench e fai doppio clic sul file run_windows_installer.bat.

   >[!IMPORTANT]
   >
   >Il programma di installazione di Workbench viene eseguito solo da un&#39;unità DVD o locale. Non può essere eseguito da un sito remoto.

   >[!NOTE]
   >
   >Se si verifica un errore &quot;Impossibile creare la macchina virtuale Java&quot;, creare una variabile di ambiente denominata _JAVA_OPTIONS con valore -Xmx512M ed eseguire il programma di installazione.

1. Nella schermata Introduzione fare clic su Avanti.
1. Leggere il Contratto di licenza del prodotto, selezionare Accetto i termini del Contratto di licenza, quindi fare clic su Avanti.
1. (Facoltativo) Selezionare Installa Adobe Designer se è necessario questo strumento per creare e modificare i moduli.

   >[!NOTE]
   >
   >Per continuare a utilizzare Designer installato con Acrobat 10, lasciare deselezionata questa opzione.

1. Accettare la directory predefinita come elencata oppure fare clic su Scegli e passare alla directory in cui si installerà Workbench, quindi fare clic su Avanti.

   >[!NOTE]
   >
   >Il percorso della directory di installazione non deve contenere caratteri # (pound) e $ (dollaro).

1. Rivedi il riepilogo della preinstallazione e fai clic su Installa. Il programma di installazione visualizza l&#39;avanzamento dell&#39;installazione.
1. Rivedi il riepilogo dell&#39;installazione. Selezionare Avvia AEM Forms Workbench per avviare Workbench e fare clic su Avanti.
1. Rivedi le Note sulla versione e fai clic su Fine.
1. Gli elementi seguenti sono ora installati nel computer:
   * **Workbench**: Per eseguire Workbench dal menu Start, selezionare Tutti i programmi > AEM Forms > Workbench, se si sceglie di archiviare la cartella dei collegamenti. Per informazioni, consulta la documentazione Utilizzo di Workbench .
   * **Designer**: È possibile accedere a Designer direttamente da Workbench. Per informazioni, consultare l&#39;argomento Guida introduttiva nella Guida di Designer.
   * **Plug-in di Workbench**: Segui le istruzioni riportate in &quot;3.3 Installazione della funzione Workbench Eclipse&quot; a pagina 6.
   * **AEM Forms SDK**: Per ulteriori informazioni sull&#39;utilizzo dell&#39;SDK, vedi <a href="http://www.adobe.com/go/learn_lc_programming_10">Programmazione con AEM Forms</a>.

## Aggiornamento dei processi {#upgrading-processes}

I processi AEM Forms Update 1 e LiveCycle ES2 possono essere aggiornati alle applicazioni AEM Forms tramite l&#39;Aggiornamento guidato. Per ulteriori informazioni, consulta Aggiornamento della documentazione sugli artefatti legacy nella Guida di Workbench .

### Installazione della funzione Workbench Eclipse {#installing-workbench-eclipse-feature}

Facoltativamente, puoi aggiungere la funzione Workbench a Eclipse. È possibile aggiungere Workbench dopo aver installato Workbench. Ad esempio, per JBoss il percorso seguente contiene il file :

* Workbench_DVD/aggiuntivo/eclipse Scarica e installa Eclipse 3.6 da <a href="https://www.eclipse.org/downloads/">www.eclipse.org/downloads</a>.

### Configurazione della funzione di aggiornamento Eclipse per Workbench {#configuring-eclipse-update-feature-for-workbench}

Workbench supporta la funzione di aggiornamento per assicurarsi di utilizzare la versione Eclipse più aggiornata. Tuttavia, è necessario assicurarsi che alcuni moduli aggiuntivi siano inclusi in ogni download:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Versione Eclipse</strong></p> </td> 
   <td><p><strong>Moduli richiesti da Workbench</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Eclipse 3.6.x</p> </td> 
   <td><p>

* Quadro di modifica grafico GEF [org.eclipse.gef.feature.group]: Questo è contenuto in &quot;Graphical Modeling Framework SDK&quot; [org.eclipse.gmf.sdk.feature.group]

* Core XML WST [org.eclipse.wst.xml_core.feature.feature.group]: Questo è contenuto in &quot;Eclipse XML Editors and Tools&quot; [org.eclipse.wst.xml_ui.feature.feature.group]

* Plug-in &#39;org.apache.commons.lang_2.3.0&#39; [n/d]: Questo è contenuto nell’&quot;Elenco attività Mylyn (obbligatorio)&quot; [org.eclipse.mylyn_feature.feature.group]

   </p> </td> 
  </tbody>
  </table>

**Installazione e distribuzione della funzionalità Workbench in Eclipse**:
1. Avvia Eclipse.
1. Selezionare Aiuto > Installa nuovo software, fare clic su Aggiungi per aprire la finestra di dialogo Aggiungi archivio.
1. Nella finestra di dialogo Aggiungi archivio fare clic su Locale e individuare la directory in cui l’installazione di Workbench ha salvato il file ZIP del plug-in, selezionare workbench-updatesite.zip, quindi fare clic su Apri.
1. Segui le istruzioni riportate nelle schermate successive per distribuire la funzione Workbench in Eclipse.

   >[!NOTE]
   >
   >Ignora il messaggio &quot;Avviso: Stai per installare una funzionalità non firmata&quot;, quindi fai clic su Installa per continuare.

   >[!NOTE]
   >
   >Il plug-in Adobe AEM Forms Discovery per Flash Builder consente di creare rapidamente applicazioni Adobe Flex e AIR che richiamano un servizio che fa parte di AEM Forms attraverso gli endpoint remoti. Informazioni su come installare e aggiornare il plug-in sono disponibili sul sito web di Adobe all&#39;indirizzo **Collegamento richiesto**.

### Configurazione e accesso al server {#configuring-and-logging-server}

Per utilizzare Workbench, è necessario che sia in esecuzione un&#39;istanza di AEM Forms, in genere su un computer separato. Devi disporre di un nome utente e di una password per accedere ad AEM Forms, nonché di dettagli sulla posizione del server.

>[!NOTE]
>
>Se AEM Forms è stato configurato per l&#39;utilizzo del provider di repository EMC Documentum o IBM FileNet e si desidera accedere a un repository diverso da quello configurato come predefinito nella console di amministrazione di AEM forms, specificare il nome utente username@Repository.

### Configurazione delle impostazioni di timeout {#configuring-timeout-settings}

Per impostazione predefinita, Workbench scade dopo due ore, indipendentemente dall’attività o dall’inattività. Per modificare l’impostazione di timeout, consulta &quot;Configurazione di User Management > Configura attributi di sistema avanzati&quot; nella Guida della console di amministrazione.

### Configurazione di Workbench per la connessione tramite HTTPS {#configuring-workbench-to-connect-over-HTTPS}

Per collegare Workbench a un server AEM Forms tramite HTTPS, è necessario assicurarsi che l’autorità di certificazione (CA) che ha rilasciato la chiave pubblica sia riconosciuta attendibile da Workbench. Se il certificato non è riconosciuto come proveniente da un&#39;origine attendibile, è necessario aggiornare il file di registro che si trova in [Workbench_HOME]/workbench/jre/lib/security directory.

>[!NOTE]
>
>[Workbench_HOME] rappresenta la directory in cui è stato installato Workbench. Il percorso predefinito è C:\Program Files (x86)\Adobe Experience Manager forms Workbench.

Assicurati di connetterti a HTTPS utilizzando il nome specificato nel certificato. Questo nome è in genere il nome host completo.

**Per aggiornare il file del cacert**:
1. Verifica di disporre di una copia del certificato SSL (Secure Sockets Layer). Contatta l’amministratore che ha configurato il server SSL o esporta il certificato utilizzando un browser web.

   >[!NOTE]
   >
   >Per esportare il certificato, apri un browser web e accedi alla console di amministrazione, installa il certificato nel browser, quindi esporta il certificato dal browser in un percorso di archiviazione temporanea (o direttamente nel [Workbench_HOME]/workbench/jre/lib/security directory).

1. Copia il certificato nel [Workbench_HOME]/workbench/jre/lib/security directory.

1. Apri una finestra del prompt dei comandi e passa a [Workbench_HOME]/workbench/jre/bin, quindi digitare il comando seguente:
   `keytool -import -storepass changeit -file [Workbench_HOME]\workbench\jre\lib\security\ssl_cert_for_certname.cer -keystore [Workbench_HOME]\workbench\jre\lib\security\cacerts -alias example`
Dove:
   * changeit è la password predefinita del keystore di cacerts.
   * certname è il certificato selezionato al passaggio 1.
   * esempio è l’alias scelto per il certificato. Questo valore può essere modificato

1. Quando viene richiesto di dichiarare attendibile il certificato, digitare Sì e premere il tasto Invio. Il keytool prosegue per importare il file dei cacerts in [Workbench_HOME]/workbench/jre/lib/security directory.

1. Chiudere e riavviare Workbench per applicare le modifiche.

### Configurazione delle impostazioni della cache per i modelli generati dinamicamente {#configuring-cache-settings-for-dynamically-generated-templates}

I seguenti aspetti del funzionamento della cache devono essere considerati se l’applicazione genera al volo modelli univoci aggiornando automaticamente il contenuto XFA. In effetti, ogni transazione utilizza un nuovo modello univoco.

Quando il generatore di moduli o l’output cerca, o aggiorna, le voci nella cache per un modello di modulo specifico, utilizza diversi valori chiave per individuare la voce di cache specifica a cui si accede.

* **Nome file modello**: Posizione e nome del modello utilizzato come identificatore univoco principale del modulo memorizzato nella cache.
* **Timestamp**: Il file modello contiene una marca temporale utilizzata per determinare l’ora dell’ultimo aggiornamento del modulo.
* **UUID modello**: Designer inserisce in ciascun modello un identificatore univoco (UUID) per il modulo e la relativa versione. Ogni volta che il modulo viene aggiornato, viene aggiornato l’UUID incorporato. Ad esempio, un modello XDP potrebbe mostrare il seguente contenuto:

   `<?xml version="1.0" encoding="UTF-8"?>`
   `<?xfa generator="AdobeAEM formsDesignerES_V8.2" APIVersion="2.6.7185.0"?><xdp:xdp xmlns:xdp=http://ns.adobe.com/xdp/ timeStamp="2008-07-29T21:22:12Z" uuid="823e538f-ff6c-4961-b759-f7626978a223"><template xmlns="http://www.xfa.org/schema/xfa-template/2.6/">`

* **Opzioni di rendering**: All’interno della cache del modulo di cui è stato effettuato il rendering, il contenuto della cache viene memorizzato separatamente per ciascun set di opzioni di rendering univoche.


Il servizio Forms riceve i modelli in riferimento al nome del file o alla posizione del repository, o in base al valore come oggetto XML in memoria.
* **Modelli trasmessi tramite riferimento**: Utilizza la directory principale del contenuto e il nome del modulo. Se in ogni richiesta che utilizza questo metodo vengono trasmessi modelli univoci con nomi di file diversi, la cache del disco crescerà all’infinito e non verrà mai riutilizzata. Per evitare questo problema, è necessario trasmettere modelli univoci con lo stesso nome file per garantire che la stessa cache venga aggiornata per tutte le richieste.
* **Modelli passati per valore**: Utilizza i byte dei modelli passati insieme ai dati utilizzando il parametro theinDataDoc . Se vengono passati modelli univoci con UUID diversi utilizzando questo metodo, la cache del disco crescerà all’infinito e non verrà mai riutilizzata. Per evitare questo problema, l’attributo UUID deve essere rimosso da tutti i modelli per garantire che non venga creata alcuna cache per il modello. In alternativa, il passaggio dello stesso UUID non-null consente di creare gli oggetti cache, ma assicura che la stessa cache venga aggiornata con ogni richiesta.

Per evitare che la cache cresca all’infinito, considera i seguenti fattori per il rendering dei modelli generati dinamicamente utilizzando le nuove API di AEM Forms, ovvero renderHTMLForm2 e renderPDFForm2.

Quando si utilizzano le nuove API, il modello viene passato come oggetto documento, gestito nel servizio Forms in base al fatto che sia passivato o meno.

Per i documenti passiving in cui l’UUID e la directory principale del contenuto fungono da chiave di cache, considera i seguenti aspetti:
* La cache non viene creata per modelli di input passivati senza UUID.
* Se vengono passati più di un modello di input passivo con lo stesso UUID e la stessa directory principale del contenuto, la stessa cache viene sovrascritta.

Per i documenti non passivati in cui il nome del file e la directory principale del contenuto fungono da chiave di cache, considera il seguente aspetto:
* Per i modelli di input non passivati, la memorizzazione in cache dipende dalla directory principale del contenuto e dal nome del file da cui è stato generato il documento.
La stessa cache verrà utilizzata solo per le richieste con la stessa directory principale del contenuto e lo stesso nome del file modello.
Le seguenti best practice garantiscono che la cache non cresca all’infinito quando i modelli generati dinamicamente vengono passati al servizio Forms:
   * Elimina l’UUID o passa lo stesso UUID in tutti i modelli generati dinamicamente.
   * Generare il documento da byte di modello o dallo stesso nome di file su disco.

### Disinstallazione di Workbench {#uninstalling-workbench}

Utilizzare la funzione Installazione applicazioni nel Pannello di controllo Campaign per avviare il programma di disinstallazione. Le applicazioni Workbench e Designer dispongono di programmi di disinstallazione separati.

## Configurazione di AEM Forms XDC Editor {#configuring-aem-forms-xdc-editor}

Utilizzando XDC Editor, gli amministratori della stampante di rete possono creare e modificare file XDC (XML Forms Architecture Device Configuration). I file XDC descrivono le funzionalità delle stampanti, ad esempio il linguaggio della stampante o la correlazione tra le dimensioni della carta e la posizione del vassoio.

Prima che l&#39;amministratore della stampante di rete utilizzi XDC Editor, riposizionare i file XDC di esempio e vedere Creazione di profili dispositivo tramite XDC Editor.

**Per ottenere i file XDC di esempio**:
1. Sul server AEM Forms, individua la cartella XDC in [Directory principale di AEM Forms]\sdk\samples\Output\IVS.
1. Copiare il contenuto di questa cartella in una directory accessibile dal sistema Workbench o Eclipse.

**Per ottenere la Guida di XDC Editor**:
1. Vai al sito web della documentazione di AEM Forms.
1. Fai clic sulla scheda Sviluppa e passa a Creazione di profili dispositivo tramite XDC Editor. Scarica il file xdc_editor_help_web.zip e installa i file della Guida seguendo le istruzioni fornite nel file Leggimi.

