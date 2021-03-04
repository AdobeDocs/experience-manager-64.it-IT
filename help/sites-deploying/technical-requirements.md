---
title: Requisiti tecnici
seo-title: Requisiti tecnici
description: Elenco delle piattaforme client e server supportate per AEM.
seo-description: Elenco delle piattaforme client e server supportate per AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
translation-type: tm+mt
source-git-commit: 95b5e70c1b474d4d207a5a33e8d1ab8ef39685b6
workflow-type: tm+mt
source-wordcount: '3271'
ht-degree: 2%

---


# Requisiti tecnici{#technical-requirements}

Adobe supporta Adobe Experience Manager (AEM) sulle piattaforme come descritto nelle seguenti informazioni in questo documento.

Per qualsiasi problema specifico relativo alla piattaforma stessa, contatta direttamente il fornitore della piattaforma.

>[!NOTE]
>
>A seconda della piattaforma su cui installi AEM, potrebbero esserci diversi set di requisiti per la gestione degli utenti.

## Prerequisiti {#prerequisites}

Requisiti minimi per l’installazione di Adobe Experience Manager:

* Piattaforma Java installata, JDK Standard Edition o altre [macchine virtuali Java](#java-virtual-machines) supportate
* File Quickstart di Experience Manager (JAR indipendente o WAR per la distribuzione di applicazioni web)

### Requisiti minimi di dimensionamento {#minimum-sizing-requirements}

Requisiti minimi per l’esecuzione di Adobe Experience Manager:

* 5 GB di spazio libero su disco nella directory di installazione
* 2 GB di memoria

>[!NOTE]
>
>* I casi di utilizzo delle risorse digitali necessitano di una maggiore memoria di base. Per ulteriori informazioni, consulta [Distribuzione e manutenzione](/help/sites-deploying/deploy.md#default-local-install) .
>* [Il ](/help/forms/using/installing-configuring-aem-forms-osgi.md) pacchetto aggiuntivo di AEM Forms richiede 15 GB di spazio temporaneo.

>



Per ulteriori informazioni, vedere le [Linee guida per il dimensionamento dell&#39;hardware](/help/managing/hardware-sizing-guidelines.md).

### Livelli di supporto {#support-levels}

In questo documento sono elencate le piattaforme client e server supportate per Adobe Experience Manager. Adobe fornisce diversi livelli di supporto, sia per le configurazioni consigliate che per altre configurazioni.

### Configurazioni supportate {#supported-configurations}

Adobe consiglia queste configurazioni e fornisce supporto completo come parte del contratto di manutenzione software standard.

<table> 
 <tbody> 
  <tr> 
   <td>Livello di supporto</td> 
   <td>Descrizione<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>R: Supportato</strong></td> 
   <td>Adobe fornisce supporto e manutenzione completi per questa configurazione. Questa configurazione è coperta dal processo di garanzia della qualità di Adobe.</td> 
  </tr> 
  <tr> 
   <td><strong>R: Supporto limitato</strong></td> 
   <td>Per garantire il successo del progetto dei nostri clienti, Adobe fornisce supporto completo all’interno di un programma di supporto limitato, che richiede il rispetto di condizioni specifiche. Il supporto a livello R richiede una richiesta formale del cliente e una conferma da parte di Adobe. Per ulteriori informazioni, contatta l’Assistenza clienti Adobe.</td> 
  </tr> 
 </tbody> 
</table>

### Configurazioni non supportate {#unsupported-configurations}

| Livello di supporto | Descrizione |
|---|---|
| **Z: Non supportato** | Configurazione non supportata. Adobe non fornisce alcuna dichiarazione relativa al funzionamento della configurazione e al suo mancato supporto. |

## Piattaforme supportate {#supported-platforms}

### Macchine virtuali Java {#java-virtual-machines}

L&#39;applicazione richiede l&#39;esecuzione di una macchina virtuale Java, fornita dalla distribuzione Java Development Kit (JDK).

Adobe Experience Manager funziona con le seguenti versioni di Java Virtual Machines:

>[!CAUTION]
>
>Si consiglia di tenere traccia dei bollettini sulla sicurezza dal fornitore Java per garantire la sicurezza degli ambienti di produzione e installare gli ultimi aggiornamenti Java.

<table> 
 <tbody> 
  <tr> 
   <td>Platform</td> 
   <td>Livello di supporto<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z: Non supportato </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z: Non supportato </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z: Non supportato</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK - 64 bit</strong></td> 
   <td>R: Supportato [3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - build 2.9, JRE 1.8.0 [2]</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - build 2.8, JRE 1.8.0 [2]</td> 
   <td>R: Supportato</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle è passato al modello “Long Term Support” (LTS) per i prodotti Oracle Java SE. Java 9 e 10 sono versioni non LTS di Oracle (vedi [roadmap del supporto Java SE di Oracle](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe fornirà supporto solo per le versioni LTS di Java per l’esecuzione di AEM in ambienti di produzione.

1. IBM JRE è supportato solo in combinazione con WebSphere Application Server.
1. Il supporto e la distribuzione di Oracle Java SE JDK, inclusi tutti gli aggiornamenti di manutenzione delle versioni LTS oltre la fine degli aggiornamenti pubblici, saranno supportati da Adobe direttamente per tutti i clienti AEM che utilizzano la tecnologia Oracle Java SE. Per ulteriori informazioni, consulta il [Supporto di Oracle Java per Adobe Experience Manager Q&amp;A](assets/adobe-oracle-java-license-agreement.pdf) .

### Storage e persistenza {#storage-persistence}

Esistono diverse opzioni per distribuire l’archivio di Adobe Experience Manager. Consulta il seguente elenco per le tecnologie supportate e le opzioni di storage.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Piattaforma</strong></td> 
   <td><strong>Descrizione</strong></td> 
   <td><strong>Livello di supporto</strong></td> 
  </tr> 
  <tr> 
   <td><strong>File system con file TAR [1]</strong></td> 
   <td>Archivio</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td><strong>File system con Datastore [1]</strong></td> 
   <td>Binari</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Memorizzare file binari in file TAR su file system [1]</td> 
   <td>Binari</td> 
   <td>Z: Non supportato per la produzione</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>Binari</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Archiviazione BLOB di Microsoft Azure</td> 
   <td>Binari</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>Archivio</td> 
   <td>R: Supportato con limitazioni</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>Archivio</td> 
   <td>R: Supportato con limitazioni</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Database Forms</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Database Forms</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>Archivio e database moduli</td> 
   <td>R: Supporto limitato (4)</td> 
  </tr> 
  <tr> 
   <td>Oracle Database 12c (12.1.x)</td> 
   <td>Archivio e database moduli</td> 
   <td>R: Supporto limitato</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Database Forms</td> 
   <td>Z: Non supportato (4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Database Forms</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Database Forms</td> 
   <td>R: Supporto limitato (4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene (integrato con Quickstart)</strong></td> 
   <td>Servizio di ricerca</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>Servizio di ricerca</td> 
   <td>R: Supportato</td> 
  </tr> 
 </tbody> 
</table>

1. Il file system include lo storage a blocchi conforme a POSIX. Ciò include la tecnologia di storage in rete. Tenere presente che le prestazioni del file system potrebbero variare e influire sulle prestazioni complessive. Si consiglia di caricare prova AEM in combinazione con il file system di rete/remoto.
1. Lo Shopping MongoDB non è supportato in AEM.
1. Il motore di archiviazione MongoDB WiredTiger è supportato solo.
1. Non supportato per AEM Forms.
1. MongoDB Enterprise 3.6 è supportato a partire da AEM versione 6.4.2.0.
1. Il supporto per MongoDB 3.4 ha raggiunto la fine del ciclo di vita (EOL), mentre MongoDB 3.6 dovrebbe raggiungere il sistema EOL il 30 aprile 2021. Tieni presente che Adobe fornirà supporto solo per i problemi relativi ai prodotti AEM in corso.

>[!NOTE]
>
>Consulta [Implementazione di Communities](/help/communities/deploy-communities.md) per ulteriori informazioni sulla funzionalità di AEM Communities.

>[!NOTE]
>
>MongoDB è un software di terze parti e non è incluso nel pacchetto di licenze AEM. Per ulteriori informazioni, consulta la pagina [Criteri di licenza MongoDB](https://www.mongodb.org/about/licensing/) .
>
>Per ottenere il massimo dalla distribuzione AEM con MongoDB, Adobe consiglia di concedere in licenza la versione Enterprise MongoDB per poter usufruire del supporto professionale. Per ulteriori informazioni, consulta [Implementazioni consigliate](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) .
>
>La licenza include un set di repliche standard, composto da una istanza primaria e due istanze secondarie che possono essere utilizzate per le distribuzioni di authoring o pubblicazione.
>
>Se desideri eseguire sia l’autore che la pubblicazione su MongoDB, devono essere acquistate due licenze separate.
>
>L’Assistenza clienti Adobe assisterà i problemi di qualificazione relativi all’utilizzo di MongoDB con AEM.
>
>Per ulteriori informazioni, consulta la pagina [MongoDB per Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>I database relazionali supportati come sopra elencati sono software di terze parti e non sono inclusi nel pacchetto di licenze AEM.
>
>Per eseguire AEM 6.4 con un database relazionale supportato, è necessario un contratto di assistenza separato con un fornitore di database. L’Assistenza clienti Adobe assisterà i problemi di qualificazione relativi all’utilizzo di database relazionali con AEM 6.4.
>
>**Nota che la maggior parte dei database relazionali è attualmente supportata all’interno del livello R su AEM 6.4, che include criteri di supporto e un programma di supporto come indicato nella descrizione del livello R precedente.**

### Motori servlet / Server applicazioni {#servlet-engines-application-servers}

Adobe Experience Manager può essere eseguito sia come server autonomo (il file JAR quickstart) che come applicazione web all’interno di un server applicativo di terze parti (il file WAR).

La versione minima dell&#39;API del servlet è Servlet 3.1, ma inferiore a Servlet 4.0.

| Piattaforma | Livello di supporto |
|---|---|
| **Motore servlet integrato Quickstart (Jetty 9.3)** | R: Supportato |
| Oracle WebLogic Server 12.2 (12cR2) | R: Supportato |
| Distribuzione continua di IBM WebSphere Application Server (LibertyProfile) con profilo Web 7.0 e IBM JRE 1.8 | R: Supportato |
| IBM WebSphere Application Server 9.0 | R: Supportato |
| Apache Tomcat 8.5.x | R: Supportato |
| JBoss EAP 7.1.0 con server applicazioni JBoss | R: Supportato (1) |
| JBoss EAP 7.0.0 con server applicazioni JBoss | R: Supportato |

1. Non supportato per AEM Forms.

### Sistemi operativi server {#server-operating-systems}

Adobe Experience Manager funziona con le seguenti piattaforme server:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Piattaforma</strong></td> 
   <td><strong>Livello di supporto</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux, basato sulla distribuzione Red Hat</strong></td> 
   <td>R: Supportato (1)</td> 
  </tr> 
  <tr> 
   <td>Linux, basato sulla distribuzione Debian incl. Ubuntu</td> 
   <td>R: Supportato (4)</td> 
  </tr> 
  <tr> 
   <td>Linux, basato sulla distribuzione SUSE</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Oracle Solaris 11</td> 
   <td>R: Supportato con limitazioni (3,5,7)<br /> R: Sostegno limitato per i nuovi contratti</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>R: Supportato con limitazioni (2,5,7)<br /> R: Sostegno limitato per i nuovi contratti</td> 
  </tr> 
 </tbody> 
</table>

1. Linux Kernel 2.6, 3.x e 4.x include derivati dalla distribuzione Red Hat, inclusi Red Hat Enterprise Linux, CentOS, Oracle Linux e Amazon Linux. Le funzioni aggiuntive di AEM Forms sono supportate solo su CentOS 7 e Red Hat Enterprise Linux 7.
1. AEM Assets: Consulta la sezione [Supporto per la riscrittura dei metadati XMP](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets: Nessun supporto per Dynamic Media Imaging. È supportato Dynamic Media Video.
1. AEM Forms è supportato solo su Ubuntu 16.04 LTS.
1. AEM Assets: Nessun supporto per [Trasformazione file non elaborati](/help/assets/camera-raw.md)
1. Moduli AEM: Nessun supporto per l&#39;ambiente di produzione
1. AEM Assets: Nessun supporto per [PDF Rasterizer migliorato](/help/assets/aem-pdf-rasterizer.md)
1. Moduli AEM: Non supportato

### Ambienti di elaborazione virtuali e cloud {#virtual-cloud-computing-environments}

Adobe Experience Manager è supportato in esecuzione in una macchina virtuale in ambienti di cloud computing, come Microsoft Azure e Amazon Web Services (AWS), in conformità ai requisiti tecnici elencati in questa pagina e ai termini di supporto standard di Adobe.

Adobe consiglia di utilizzare Adobe Managed Services per distribuire AEM su Azure o AWS. Adobe Managed Services offre agli esperti esperienza e competenze necessarie per implementare e utilizzare AEM in questi ambienti di cloud computing. Consulta la nostra [documentazione aggiuntiva su Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

In tutti gli altri casi di distribuzione di AEM su Azure o AWS, o in qualsiasi altro ambiente di cloud computing, il supporto di Adobe sarà contenuto nell’ambiente di elaborazione virtuale in conformità alle specifiche tecniche elencate in questa pagina. Qualsiasi problema segnalato relativo ad AEM in esecuzione in uno qualsiasi di questi ambienti cloud dovrà essere riproducibile indipendentemente da qualsiasi servizio cloud specifico per l’ambiente cloud computing, a meno che il servizio cloud non sia specificamente supportato come parte dei requisiti tecnici elencati in questa pagina, ad esempio archiviazione BLOB di Azure o AWS S3.

Per raccomandazioni su come distribuire AEM su Azure o AWS, al di fuori di Adobe Managed Services, si consiglia vivamente di collaborare direttamente con il provider cloud o i partner Adobe per supportare la distribuzione di AEM nell’ambiente cloud desiderato. Il fornitore o il partner cloud selezionato sarà responsabile delle specifiche di dimensionamento, della progettazione e dell&#39;implementazione dell&#39;architettura., per soddisfare i requisiti specifici di prestazioni, carico, scalabilità e sicurezza.

### Piattaforme Dispatcher (server web) {#dispatcher-platforms-web-servers}

Dispatcher è il componente di memorizzazione in cache e bilanciamento del carico. [Scarica la versione](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html) più recente di Dispatcher. Experience Manager 6.4 richiede la versione 4.3.1 o successiva di Dispatcher.

I seguenti server web sono supportati per l’utilizzo con Dispatcher versione 4.3.1:

| Piattaforma | Livello di supporto |
|---|---|
| **Apache httpd 2.4.x**  (vedi anche 1,2 di seguito ) | R: Supportato |
| Microsoft IIS 10 (Internet Information Server) | R: Supportato |
| Microsoft IIS 8.5 (Internet Information Server) | R: Supportato |

1. I server web generati in base al codice sorgente httpd di Apache avranno lo stesso livello di supporto della versione di httpd su cui si basa. In caso di dubbi, chiedi ad Adobe la conferma del livello di supporto relativo al rispettivo prodotto server. I casi seguenti:

   1. Il server HTTP è stato creato utilizzando solo le distribuzioni di origine Apache ufficiali, oppure
   1. Il server HTTP è stato distribuito come parte del sistema operativo su cui è in esecuzione. Esempi: IBM HTTP Server, Oracle HTTP Server

1. Dispatcher non è disponibile per Apache 2.4.x per i sistemi operativi Windows.

## Piattaforme client supportate {#supported-client-platforms}

### Browser supportati per l’authoring dell’interfaccia utente {#supported-browsers-for-authoring-user-interface}

L’interfaccia utente di Adobe Experience Manager funziona con le seguenti piattaforme client. Tutti i browser vengono testati con il set predefinito di plug-in e componenti aggiuntivi.

L’interfaccia utente di AEM è ottimizzata per schermi più grandi (in genere notebook e computer desktop) e per fattori di forma per tablet (come Apple iPad o Microsoft Surface). Il fattore di forma del telefono non è supportato.

>[!NOTE]
>
>**Supporto per browser con cicli di rilascio rapidi:**
>
>Mozilla Firefox, Google Chrome e Microsoft Edge aggiornano la versione ogni pochi mesi. Adobe si impegna a fornire aggiornamenti ad Adobe Experience Manager per mantenere il livello di supporto come indicato di seguito con le prossime versioni di questi browser.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Browser</strong></td> 
   <td><strong>Supporto per l’interfaccia utente<br /> </strong></td> 
   <td><strong>Supporto per l’interfaccia classica</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome (Evergreen)</strong></td> 
   <td>R: Supportato</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge (Evergreen)</td> 
   <td>R: Supportato</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>R: Supportato</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox (Evergreen)</td> 
   <td>R: Supportato</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox ultima ESR [1]</td> 
   <td>R: Supportato</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 12.x su macOS</td> 
   <td>R: Supportato</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x su macOS</td> 
   <td>R: Supportato</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 10.x su macOS</td> 
   <td>R: Supportato</td> 
   <td>R: Supportato</td> 
  </tr> 
  <tr> 
   <td>Apple Safari su iOS 12.x</td> 
   <td>R: Supportato [2]</td> 
   <td>Z: Non supportato</td> 
  </tr> 
  <tr> 
   <td>Apple Safari su iOS 11.x</td> 
   <td>R: Supportato [2]</td> 
   <td>Z: Non supportato</td> 
  </tr> 
  <tr> 
   <td>Apple Safari su iOS 10.3</td> 
   <td>R: Supportato [2]</td> 
   <td>Z: Non supportato</td> 
  </tr> 
 </tbody> 
</table>

1. Versione estesa del supporto Firefox [Ulteriori informazioni su mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. supporto per Apple iPad

### Browser supportati per siti web {#supported-browsers-for-websites}

In genere, il supporto del browser per i siti web di cui è stato eseguito il rendering da AEM Sites dipende dall’implementazione dei modelli di pagina AEM, dalla progettazione e dall’output del componente, ed è pertanto a capo dell’implementazione di tali parti.

### Client WebDAV {#webdav-clients}

**Microsoft Windows 7+**

Per connettersi con Microsoft Windows 7+ a un&#39;istanza AEM non protetta con SSL, è necessario abilitare l&#39;autenticazione di base su una rete non protetta in Windows. È necessaria una modifica nel Registro di sistema di Windows del WebClient:

1. Individua la sottochiave del Registro di sistema:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Aggiungere la voce del Registro di sistema BasicAuthLevel a questa sottochiave utilizzando un valore pari o superiore a 2.

Consultare [Supporto Microsoft KB 841215](https://support.microsoft.com/default.aspx/kb/841215).

Per migliorare la reattività del client WebDav in Windows - vedere [Supporto Microsoft KB 2445570](https://support.microsoft.com/kb/2445570)

## Note aggiuntive sulla piattaforma {#additional-platform-notes}

Questa sezione fornisce note speciali e informazioni più dettagliate sull’esecuzione di Adobe Experience Manager e dei relativi componenti aggiuntivi.

### IPv4 e IPv6 {#ipv-and-ipv}

Tutti gli elementi di Adobe Experience Manager (Instance, Dispatcher) possono essere installati nelle reti IPv4 e IPv6.

Il funzionamento è semplice in quanto non è necessaria alcuna configurazione speciale. È sufficiente specificare un indirizzo IP utilizzando il formato appropriato per il tipo di rete, se necessario.

Ciò significa che, quando è necessario specificare un indirizzo IP, è possibile selezionare (come richiesto) da:

* un indirizzo IPv6

   ad esempio `https://[ab12::34c5:6d7:8e90:1234]:4502`

* un indirizzo IPv4

   ad esempio `https://123.1.1.4:4502`

* un nome server

   ad esempio, `https://www.yourserver.com:4502`

* il caso predefinito di `localhost` verrà interpretato sia per le installazioni di rete IPv4 che IPv6

   ad esempio, `http://localhost:4502`

### Requisiti del componente aggiuntivo Dynamic Media AEM {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media è disattivato per impostazione predefinita. Consulta [Abilitazione di Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Con Dynamic Media abilitato, si applicano i seguenti requisiti di sistema aggiuntivi:
>[!NOTE]
>
>I seguenti requisiti di sistema si applicano **_solo_** se utilizzi Dynamic Media - modalità ibrida; Dynamic Media - La modalità ibrida dispone di un server di immagini integrato, certificato solo su determinati sistemi operativi.
>
>Per i clienti di Dynamic Media che eseguono Dynamic Media - Modalità Scene7 (ovvero, **modalità runmode dynamic_media_scene7** ), non sono previsti requisiti di sistema aggiuntivi; solo gli stessi requisiti di sistema di AEM. Dynamic Media - L’architettura in modalità Scene7 utilizza il servizio immagine basato su cloud, non il servizio incorporato in AEM.

#### Hardware {#hardware}

I seguenti requisiti hardware si applicano ai sistemi operativi Linux e Windows:

* CPU Intel Xeon o AMD Opteron con almeno 4 core
* Almeno 16 GB di RAM

#### Linux {#linux}

L&#39;utilizzo di Dynamic Media su Linux richiede i seguenti prerequisiti:

* RedHat Enterprise 7 o CentOS 7 e versioni successive con ultime patch di correzione
* Sistema operativo a 64 bit
* Scambio disattivato (consigliato)
* SELinux disabilitato (vedere la nota seguente)

>[!NOTE]
>
>Se le impostazioni internazionali sono impostate in modo tale che LC_CTYPE non sia uguale a en_US.UTF-8, il supporto dinamico non funzionerà. Per visualizzare il relativo valore, digitare &quot;locale&quot; al prompt dei comandi. Se non è impostato su tale valore, impostare la variabile di ambiente LC_CTYPE sulla stringa vuota digitando &quot;export LC_CTYPE=&quot; prima di eseguire AEM.

>[!NOTE]
>
>**Disabilitazione di SELinux:** Image Server non funziona con SELinux attivato. Questa opzione è attivata per impostazione predefinita. Per risolvere questo problema, modifica il file **/etc/selinux/config** e modifica il valore SELinux da:
>
>`SELINUX=enforcing` a  `SELINUX=disabled`

>[!NOTE]
>
>**Architettura NUMA:** i sistemi con processori con AMD64 e Intel EM64T sono in genere configurati come piattaforme NUMA (non uniformi memory architecture), il che significa che il kernel costruisce più nodi di memoria in fase di avvio anziché costruire un singolo nodo di memoria.
>
>Il costrutto a più nodi può causare esaurimento della memoria su uno o più nodi prima che gli altri nodi si esauriscano. Quando si verifica un esaurimento della memoria, il kernel può decidere di interrompere i processi (ad esempio, Image Server o Platform Server) anche se è disponibile memoria.
>
>Pertanto, Adobe consiglia di disattivare NUMA se si esegue un sistema di questo tipo utilizzando l&#39;opzione di avvio **numa=off** per evitare che il kernel uccida questi processi.

>[!NOTE]
>
>**Il nome host del server deve essere risolvibile:** assicurati che il nome host del server sia risolvibile in un indirizzo IP. Se ciò non è possibile, aggiungi il nome host completo e l&#39;indirizzo IP a **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Spazio di scambio pari almeno al doppio della quantità di memoria fisica (RAM)

Per utilizzare Dynamic Media su Windows, è necessario installare Microsoft Visual Studio 2010, 2013 e 2015 ridistribuibili per x64 e x86.

x64

* Per la ridistribuzione di Microsoft Visual Studio 2010, visitare il sito [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* Il file ridistribuibile di Microsoft Visual Studio 2013 si trova all&#39;indirizzo [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* Per informazioni sulla ridistribuzione di Microsoft Visual Studio 2015, visitare il sito [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* Per la ridistribuzione di Microsoft Visual Studio 2010, visitare il sito [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Il file ridistribuibile di Microsoft Visual Studio 2013 si trova all&#39;indirizzo [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Per informazioni sulla ridistribuzione di Microsoft Visual Studio 2015, visitare il sito [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### MacOS {#macos}

* 10.9.x e versioni successive
* Supportato solo a scopo di prova e demo

### Requisiti del generatore PDF di AEM Forms {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Prodotto</strong></p> </th> 
   <th><p><strong>Formati supportati per la conversione in PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Traccia classica di Acrobat 2017</a></p> </td> 
   <td><p>XPS, formati immagine (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF e DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF e TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF e TXT</td> 
  </tr> 
  <tr> 
   <td>Corel WordPerfect X7</td> 
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formati immagine (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF e TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formati immagine (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF e TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator supporta solo le versioni inglese, francese, tedesca e giapponese dei sistemi operativi e delle applicazioni supportati.
>
>Inoltre:
>
>* PDF Generator richiede [Acrobat 2017 classic track versione 17.011.30078 o successiva](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) per eseguire la conversione.
>* AEM Forms supporta solo versioni a 32 bit di software supportato.
>* Le funzionalità PDF OCR (PDF ricercabile), Ottimizza PDF ed Esporta PDF sono supportate solo in Microsoft Windows.
>* Il servizio HTML2PDF è obsoleto su AIX.
>* Le conversioni PDF Generator per OpenOffice sono supportate solo su Windows, Linux e Solaris.
>* Le funzioni OCR PDF, Optimize PDF e Export PDF sono supportate solo su Windows.
>* Una versione di Acrobat è inclusa in un pacchetto con AEM Forms per abilitare la funzionalità PDF Generator. La versione inclusa nel pacchetto deve essere accessibile solo a livello di programmazione con AEM Forms, durante il periodo di validità della licenza AEM Forms, per l’utilizzo con PDF Generator di AEM Forms. Per ulteriori informazioni, consulta la descrizione del prodotto AEM Forms in base alla distribuzione ([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) o [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;

>



### Requisiti di AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2012 Server R2, Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10
* Processore da 1 GHz o più veloce con supporto per PAE, NX e SSE2.
* 1 GB di RAM per sistemi operativi a 64 bit o 32 bit o 2 GB di RAM
* 16 GB di spazio su disco per 32 bit o 20 GB per sistemi operativi a 64 bit
* Memoria grafica - 128 MB di GPU (256 MB consigliati)
* 2,35 GB di spazio disponibile su disco rigido
* Risoluzione del monitor di 1024 X 768 pixel o superiore
* Accelerazione hardware video (opzionale)
* Acrobat Pro DC, Acrobat Standard DC o Adobe Acrobat Reader DC
* Privilegi di amministratore per installare Designer

### Requisiti per la riscrittura dei metadati XMP di AEM Assets {#requirements-for-aem-assets-xmp-metadata-write-back}

La funzione di write-back XMP è supportata e abilitata per le seguenti piattaforme e formati di file:

**Sistemi operativi**

* Linux (32 bit, richiede il supporto di applicazioni a 32 bit su sistemi a 64 bit). Per i passaggi per installare le librerie client a 32 bit, vedi [Come abilitare l&#39;estrazione e la riscrittura XMP su RedHat Linux a 64 bit](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

* Windows Server
* Oracle Solaris
* Mac OS X (64 bit)

**Formati file**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### Requisiti di AEM Screens Player {#requirements-for-aem-screens-player}

La versione 3.3.x di AEM Screens Player supporta i seguenti sistemi operativi:

* Microsoft Windows 10 Enterprise LTSB
* Google Chome OS 62+
* Google Android 5.1.1 con versione aggiornata di Android System WebView versione 52+
* Apple iOS 10.3+
* Apple macOS 10.12+
