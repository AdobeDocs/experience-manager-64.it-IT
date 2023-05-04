---
title: Requisiti tecnici
seo-title: Technical Requirements
description: Elenco delle piattaforme client e server supportate per AEM.
seo-description: A list of the supported client and server platforms for AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
exl-id: 21c10b39-ca37-4085-86f8-063c30a180ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3294'
ht-degree: 1%

---

# Requisiti tecnici{#technical-requirements}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe supporta Adobe Experience Manager (AEM) sulle piattaforme come descritto nelle seguenti informazioni in questo documento.

Per qualsiasi problema specifico relativo alla piattaforma stessa, contatta direttamente il fornitore della piattaforma.

>[!NOTE]
>
>A seconda della piattaforma su cui installi AEM, potrebbero essere presenti diversi set di requisiti per la gestione degli utenti.

## Prerequisiti {#prerequisites}

Requisiti minimi per l’installazione di Adobe Experience Manager:

* Piattaforma Java installata, JDK Standard Edition o altro supporto [Macchine virtuali Java](#java-virtual-machines)
* File Quickstart di Experience Manager (JAR indipendente o WAR per la distribuzione di applicazioni web)

### Requisiti minimi di dimensionamento {#minimum-sizing-requirements}

Requisiti minimi per l’esecuzione di Adobe Experience Manager:

* 5 GB di spazio libero su disco nella directory di installazione
* 2 GB di memoria

>[!NOTE]
>
>* I casi di utilizzo delle risorse digitali necessitano di una maggiore memoria di base. Vedi [Implementazione e manutenzione](/help/sites-deploying/deploy.md#default-local-install) per i dettagli.
>* [Pacchetto aggiuntivo di AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) richiede 15 GB di spazio temporaneo.
>


Vedi la [Linee guida per il dimensionamento dell&#39;hardware](/help/managing/hardware-sizing-guidelines.md) per ulteriori informazioni.

### Livelli di supporto {#support-levels}

In questo documento sono elencate le piattaforme client e server supportate per Adobe Experience Manager. Adobe fornisce diversi livelli di supporto, sia per le configurazioni consigliate che per altre configurazioni.

### Configurazioni supportate {#supported-configurations}

L&#39;Adobe consiglia queste configurazioni e fornisce pieno supporto nell&#39;ambito del contratto standard di manutenzione del software.

<table> 
 <tbody> 
  <tr> 
   <td>Livello di supporto</td> 
   <td>Descrizione<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>R: Supportato</strong></td> 
   <td>Adobe fornisce supporto e manutenzione completi per questa configurazione. Questa configurazione è coperta dal processo di garanzia della qualità dell'Adobe.</td> 
  </tr> 
  <tr> 
   <td><strong>R: Supporto limitato</strong></td> 
   <td>Per garantire il successo del progetto dei nostri clienti, l'Adobe fornisce pieno supporto all'interno di un programma di supporto limitato, che richiede il rispetto di condizioni specifiche. Il supporto a livello R richiede una richiesta formale del cliente e una conferma per Adobe. Per ulteriori informazioni, contatta l’Assistenza clienti Adobe.</td> 
  </tr> 
 </tbody> 
</table>

### Configurazioni non supportate {#unsupported-configurations}

| Livello di supporto | Descrizione |
|---|---|
| **Z: Non supportato** | Configurazione non supportata. L&#39;Adobe non fornisce istruzioni sul funzionamento della configurazione e non la supporta. |

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

1. Oracle è stato spostato in un modello &quot;Long Term Support&quot; (LTS) per i prodotti Java SE di Oracle. Java 9 e 10 sono versioni non LTS per Oracle (vedi [Roadmap del supporto Java SE di Oracle](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe supporterà solo le versioni LTS di Java per l’esecuzione di AEM in produzione.

1. IBM JRE è supportato solo in combinazione con WebSphere Application Server.
1. Il supporto e la distribuzione dell&#39;Oracle Java SE JDK, inclusi tutti gli aggiornamenti di manutenzione delle versioni LTS oltre la fine degli aggiornamenti pubblici, saranno supportati da Adobe direttamente per tutti i clienti AEM utilizzando la tecnologia Oracle Java SE. Consulta la sezione [Oracle di supporto Java per le domande e risposte di Adobe Experience Manager](assets/adobe-oracle-java-license-agreement.pdf) per ulteriori informazioni.

### Storage e persistenza {#storage-persistence}

Esistono diverse opzioni per distribuire l’archivio di Adobe Experience Manager. Consulta il seguente elenco per le tecnologie supportate e le opzioni di storage.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Platform</strong></td> 
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
   <td>Archivio e database Forms</td> 
   <td>R: Supporto limitato (4)</td> 
  </tr> 
  <tr> 
   <td>Database Oracle 12c (12.1.x)</td> 
   <td>Archivio e database Forms</td> 
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

1. Il file system include lo storage a blocchi conforme a POSIX. Ciò include la tecnologia di storage in rete. Tenere presente che le prestazioni del file system potrebbero variare e influire sulle prestazioni complessive. Si consiglia di caricare AEM di prova in combinazione con il file system di rete/remoto.
1. Shopping MongoDB non supportato in AEM.
1. Il motore di archiviazione MongoDB WiredTiger è supportato solo.
1. Non supportato da AEM Forms.
1. MongoDB Enterprise 3.6 è supportato a partire da AEM versione 6.4.2.0.
1. Il supporto per MongoDB 3.4 ha raggiunto la fine del ciclo di vita (EOL), mentre MongoDB 3.6 dovrebbe raggiungere il sistema EOL il 30 aprile 2021. Nota che l&#39;Adobe fornirà supporto solo per AEM problemi relativi ai prodotti in corso.

>[!NOTE]
>
>Vedi [Distribuzione di Communities](/help/communities/deploy-communities.md) per ulteriori informazioni sulla funzionalità AEM Communities.

>[!NOTE]
>
>MongoDB è un software di terze parti e non è incluso nel pacchetto di licenze AEM. Per ulteriori informazioni, consulta la sezione [Criteri di licenza MongoDB](https://www.mongodb.org/about/licensing/) pagina.
>
>Per ottenere il massimo dalla distribuzione di AEM con MongoDB, Adobe consiglia di concedere in licenza la versione Enterprise MongoDB al fine di beneficiare del supporto professionale. Vedi [Implementazioni consigliate](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) per ulteriori informazioni.
>
>La licenza include un set di repliche standard, composto da una istanza primaria e due istanze secondarie che possono essere utilizzate per le distribuzioni di authoring o pubblicazione.
>
>Se desideri eseguire sia l’autore che la pubblicazione su MongoDB, devono essere acquistate due licenze separate.
>
>L’Assistenza clienti Adobe assisterà i problemi di qualificazione relativi all’utilizzo di MongoDB con AEM.
>
>Per ulteriori informazioni, consulta la sezione [Pagina MongoDB per Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>I database relazionali supportati elencati sopra sono software di terze parti e non sono inclusi nel pacchetto di licenze AEM.
>
>Per eseguire AEM 6.4 con un database relazionale supportato, è necessario un contratto di supporto separato con un fornitore di database. L’Assistenza clienti Adobe assisterà i problemi di qualificazione relativi all’utilizzo di database relazionali con AEM 6.4.
>
>**Nota che la maggior parte dei database relazionali è attualmente supportata all&#39;interno del livello R del AEM 6.4, che include criteri di supporto e un programma di supporto come indicato nella descrizione del livello R precedente.**

### Motori servlet / Server applicazioni {#servlet-engines-application-servers}

Adobe Experience Manager può essere eseguito sia come server indipendente (il file JAR quickstart) che come applicazione web all’interno di un server applicativo di terze parti (il file WAR).

La versione minima dell&#39;API del servlet è Servlet 3.1, ma inferiore a Servlet 4.0.

| Platform | Livello di supporto |
|---|---|
| **Motore servlet integrato Quickstart (Jetty 9.3)** | R: Supportato |
| Oracle WebLogic Server 12.2 (12cR2) | R: Supportato |
| Distribuzione continua (LibertyProfile) dell&#39;applicazione IBM WebSphere Application Server con profilo Web 7.0 e IBM JRE 1.8 | R: Supportato |
| IBM WebSphere Application Server 9.0 | R: Supportato |
| Apache Tomcat 8.5.x | R: Supportato |
| JBoss EAP 7.1.0 con server applicazioni JBoss | R: Supportato (1) |
| JBoss EAP 7.0.0 con server applicazioni JBoss | R: Supportato |

1. Non supportato da AEM Forms.

### Sistemi operativi server {#server-operating-systems}

Adobe Experience Manager funziona con le seguenti piattaforme server:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Platform</strong></td> 
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

1. Linux Kernel 2.6, 3.x e 4.x include derivati dalla distribuzione Red Hat, inclusi Red Hat Enterprise Linux, CentOS, Oracle Linux e Amazon Linux. Le funzionalità aggiuntive di AEM Forms sono supportate solo su CentOS 7 e Red Hat Enterprise Linux 7.
1. AEM Assets: Vedi la sezione [Supporto per la riscrittura dei metadati XMP](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets: Nessun supporto per Dynamic Media Imaging. Dynamic Media Video è supportato.
1. AEM Forms è supportato solo su Ubuntu 16.04 LTS.
1. AEM Assets: Nessun supporto per [Trasformazione di file non elaborati](/help/assets/camera-raw.md)
1. AEM Forms: Nessun supporto per l&#39;ambiente di produzione
1. AEM Assets: Nessun supporto per [potenziato PDF Rasterizer](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms: Non supportato

### Ambienti di elaborazione virtuali e cloud {#virtual-cloud-computing-environments}

Adobe Experience Manager è supportato in esecuzione in una macchina virtuale in ambienti di cloud computing, come Microsoft Azure e Amazon Web Services (AWS), in conformità ai requisiti tecnici elencati in questa pagina e in base ai termini di supporto standard di Adobe.

Adobe consiglia di utilizzare Adobe Managed Services per distribuire AEM su Azure o AWS. Adobe Managed Services offre agli esperti esperienza e competenze per l’implementazione e il funzionamento di AEM in questi ambienti di cloud computing. Per favore controlla il nostro [documentazione aggiuntiva su Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

In tutti gli altri casi di distribuzione di AEM su Azure o AWS o in qualsiasi altro ambiente cloud computing, il supporto di Adobe sarà contenuto nell&#39;ambiente di elaborazione virtuale in conformità alle specifiche tecniche elencate in questa pagina. Eventuali problemi segnalati relativi all&#39;AEM in esecuzione in uno qualsiasi di questi ambienti cloud dovranno essere riproducibili indipendentemente da qualsiasi servizio cloud specifico per l&#39;ambiente cloud computing, a meno che il servizio cloud non sia specificamente supportato come parte dei requisiti tecnici elencati in questa pagina, ad esempio archiviazione BLOB di Azure o AWS S3.

Per raccomandazioni su come distribuire AEM su Azure o AWS, al di fuori di Adobe Managed Services, si consiglia vivamente di lavorare direttamente con il provider cloud o i partner di Adobe che supportano la distribuzione di AEM nell’ambiente cloud desiderato. Il fornitore o il partner cloud selezionato sarà responsabile delle specifiche di dimensionamento, della progettazione e dell&#39;implementazione dell&#39;architettura., per soddisfare i requisiti specifici di prestazioni, carico, scalabilità e sicurezza.

### Piattaforme Dispatcher (server web) {#dispatcher-platforms-web-servers}

Dispatcher è il componente di memorizzazione in cache e bilanciamento del carico. [Scarica la versione più recente di Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html). Experience Manager 6.4 richiede la versione 4.3.1 o successiva di Dispatcher.

I seguenti server web sono supportati per l’utilizzo con Dispatcher versione 4.3.1:

| Platform | Livello di supporto |
|---|---|
| **Apache httpd 2.4.x** (vedi anche 1,2 di seguito) | R: Supportato |
| Microsoft IIS 10 (Internet Information Server) | R: Supportato |
| Microsoft IIS 8.5 (Internet Information Server) | R: Supportato |

1. I server web generati in base al codice sorgente httpd di Apache avranno lo stesso livello di supporto della versione di httpd su cui si basa. In caso di dubbi, chiedere ad Adobe la conferma del livello di supporto relativo al rispettivo prodotto server. I casi seguenti:

   1. Il server HTTP è stato creato utilizzando solo le distribuzioni di origine Apache ufficiali, oppure
   1. Il server HTTP è stato distribuito come parte del sistema operativo su cui è in esecuzione. Esempi: Server HTTP IBM, server HTTP Oracle

1. Dispatcher non è disponibile per Apache 2.4.x per i sistemi operativi Windows.

## Piattaforme client supportate {#supported-client-platforms}

### Browser supportati per l’interfaccia utente di authoring {#supported-browsers-for-authoring-user-interface}

L’interfaccia utente di Adobe Experience Manager funziona con le seguenti piattaforme client. Tutti i browser vengono testati con il set predefinito di plug-in e componenti aggiuntivi.

L’interfaccia utente AEM è ottimizzata per schermi di dimensioni maggiori (in genere notebook e computer desktop) e per fattori di forma tablet (come Apple iPad o Microsoft Surface). Il fattore di forma del telefono non è supportato.

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

1. Versione estesa del supporto di Firefox [Ulteriori informazioni su mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. Supporto per Apple iPad

### Browser supportati per siti web {#supported-browsers-for-websites}

In genere, il supporto del browser per i siti web sottoposti a rendering da AEM Sites dipende dall’implementazione di modelli di pagina AEM, dalla progettazione e dall’output di componenti ed è pertanto a capo dell’implementazione di tali parti.

### Client WebDAV {#webdav-clients}

**Microsoft Windows 7+**

Per connettersi con Microsoft Windows 7+ a un&#39;istanza AEM non protetta con SSL, è necessario abilitare l&#39;autenticazione di base su una rete non protetta in Windows. È necessaria una modifica nel Registro di sistema di Windows del WebClient:

1. Individua la sottochiave del Registro di sistema:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Aggiungere la voce del Registro di sistema BasicAuthLevel a questa sottochiave utilizzando un valore pari o superiore a 2.

Vedi [Supporto Microsoft KB 841215](https://support.microsoft.com/default.aspx/kb/841215).

Per migliorare la reattività del client WebDav sotto Windows - vedi [Supporto Microsoft KB 2445570](https://support.microsoft.com/kb/2445570)

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

* il caso predefinito di `localhost` verranno interpretati sia per le installazioni di rete IPv4 che IPv6

   ad esempio, `http://localhost:4502`

### Requisiti del componente aggiuntivo AEM Dynamic Media {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media è disattivato per impostazione predefinita. Vedi [Abilitazione di Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Con Dynamic Media abilitato, si applicano i seguenti requisiti di sistema aggiuntivi:
>[!NOTE]
>
>Si applicano i seguenti requisiti di sistema **_only_** se si utilizza Dynamic Media - Modalità ibrida; Dynamic Media - La modalità ibrida ha un server di immagini integrato, che è certificato solo su determinati sistemi operativi.
>
>Per i clienti Dynamic Media che eseguono la modalità Dynamic Media - Scene7 (ovvero **dynamicmedia_scene7** in modalità runmode), non vi sono ulteriori requisiti di sistema; solo gli stessi requisiti di sistema AEM. Dynamic Media - L&#39;architettura in modalità Scene7 utilizza il servizio immagine basato su cloud, non il servizio incorporato in AEM.

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
>Se le impostazioni internazionali sono impostate in modo tale che LC_CTYPE non sia uguale a en_US.UTF-8, il supporto dinamico non funzionerà. Per visualizzare il relativo valore, digitare &quot;locale&quot; al prompt dei comandi. Se non è impostato su questo, impostare la variabile di ambiente LC_CTYPE sulla stringa vuota digitando &quot;export LC_CTYPE=&quot; prima di eseguire AEM.

>[!NOTE]
>
>**Disabilitazione di SELinux:** Image Server non funziona con SELinux attivato. Questa opzione è attivata per impostazione predefinita. Per risolvere questo problema, modifica il **/etc/selinux/config** e modifica il valore SELinux da:
>
>`SELINUX=enforcing` a  `SELINUX=disabled`

>[!NOTE]
>
>**Architettura NUMA:** I sistemi con processori con AMD64 e Intel EM64T sono generalmente configurati come piattaforme NUMA (non-Uniform Memory Architecture), il che significa che il kernel costruisce più nodi di memoria in fase di avvio piuttosto che costruire un singolo nodo di memoria.
>
>Il costrutto a più nodi può causare esaurimento della memoria su uno o più nodi prima che gli altri nodi si esauriscano. Quando si verifica un esaurimento della memoria, il kernel può decidere di interrompere i processi (ad esempio, Image Server o Platform Server) anche se è disponibile memoria.
>
>Pertanto, l&#39;Adobe consiglia che, se si esegue un sistema di questo tipo, si disattiva NUMA utilizzando **numa=off** opzione di avvio per evitare che il kernel uccida questi processi.

>[!NOTE]
>
>**Il nome host del server deve essere risolvibile:** Assicurati che il nome host del server sia risolvibile in un indirizzo IP. Se ciò non è possibile, aggiungi il nome host completo e l’indirizzo IP a **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Spazio di scambio pari almeno al doppio della quantità di memoria fisica (RAM)

Per utilizzare Dynamic Media su Windows, è necessario installare Microsoft Visual Studio 2010, 2013 e 2015 ridistribuibili per x64 e x86.

x64

* È possibile trovare Microsoft Visual Studio 2010 ridistribuibile all&#39;indirizzo [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* È possibile trovare Microsoft Visual Studio 2013 ridistribuibile all&#39;indirizzo [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* È possibile trovare Microsoft Visual Studio 2015 ridistribuibile all&#39;indirizzo [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* È possibile trovare Microsoft Visual Studio 2010 ridistribuibile all&#39;indirizzo [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* È possibile trovare Microsoft Visual Studio 2013 ridistribuibile all&#39;indirizzo [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* È possibile trovare Microsoft Visual Studio 2015 ridistribuibile all&#39;indirizzo [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### macOS {#macos}

* 10.9.x e versioni successive
* Supportato solo a scopo di prova e demo

### Requisiti di AEM Forms PDF Generator {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Prodotto</strong></p> </th> 
   <th><p><strong>Formati supportati per la conversione in PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Tracciamento classico di Acrobat 2017</a></p> </td> 
   <td><p>XPS, formati immagine (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF e DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Progetto Microsoft® 2016</td> 
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
>* Le funzioni OCR PDF (Searchable PDF), Optimize PDF ed Export PDF sono supportate solo su Microsoft Windows.
>* Il servizio HTML2PDF è obsoleto su AIX.
>* Le conversioni di PDF Generator per OpenOffice sono supportate solo su Windows, Linux e Solaris.
>* Le funzioni OCR PDF, Optimize PDF ed Export PDF sono supportate solo su Windows.
>* Una versione di Acrobat è inclusa in bundle con AEM Forms per abilitare la funzionalità PDF Generator. La versione del bundle deve essere accessibile solo a livello di programmazione con AEM Forms, durante il periodo di validità della licenza AEM Forms, per l’utilizzo con AEM Forms PDF Generator. Per ulteriori informazioni, consulta la descrizione del prodotto AEM Forms in base alla distribuzione ([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) o [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
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

### Requisiti per la riscrittura dei metadati di AEM Assets XMP {#requirements-for-aem-assets-xmp-metadata-write-back}

XMP write-back è supportato e abilitato per le seguenti piattaforme e formati di file:

**Sistemi operativi**

* Linux (32 bit, richiede il supporto di applicazioni a 32 bit su sistemi a 64 bit). Per i passaggi per installare le librerie client a 32 bit, vedi [Come abilitare l&#39;estrazione XMP e il write-back su RedHat Linux a 64 bit](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

* Windows Server
* Oracle Solaris
* Mac OS X (64 bit)

**Formati di file**

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
* Sistema operativo Google Chome 62+
* Google Android 5.1.1 con versione aggiornata di Android System WebView 52+
* Apple iOS 10.3+
* Apple macOS 10.12+
