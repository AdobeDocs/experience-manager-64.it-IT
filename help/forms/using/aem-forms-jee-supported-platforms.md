---
title: Piattaforme supportate per AEM Forms su JEE
seo-title: Piattaforme supportate per AEM Forms su JEE
description: Elenco dei componenti dell’infrastruttura richiesti e supportati per l’installazione di AEM Forms su JEE
seo-description: Elenco dei componenti dell’infrastruttura richiesti e supportati per l’installazione di AEM Forms su JEE
uuid: 22f05fd4-f9fc-423e-8a86-1e75df4b2b44
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 1b9f8d98-e7e8-4b9b-a0df-52ccba324da3
translation-type: tm+mt
source-git-commit: 95b5e70c1b474d4d207a5a33e8d1ab8ef39685b6
workflow-type: tm+mt
source-wordcount: '3316'
ht-degree: 1%

---


# Piattaforme supportate per AEM Forms su JEE {#supported-platforms-for-aem-forms-on-jee}

## Piattaforme supportate {#supported-platforms}

### Livelli di supporto {#support-levels}

È possibile configurare AEM Forms su un server JEE utilizzando qualsiasi combinazione di sistemi operativi, server di applicazioni, database, driver di database, JDK, server LDAP e server di posta elettronica supportati.

In questo documento sono elencate le piattaforme client e server supportate per AEM Forms su JEE. Adobe fornisce diversi livelli di supporto, sia per le configurazioni consigliate che per altre configurazioni. Il documento elenca anche gli altri software supportati e la relativa versione, le eccezioni, le definizioni delle patch e i criteri di supporto delle patch software di terze parti.

>[!NOTE]
>
>* Per un elenco completo delle eccezioni alle piattaforme server supportate, consulta [Eccezioni alle piattaforme server supportate](#exceptions-to-supported-server-platforms).
>* AEM Forms su JEE supporta solo le versioni inglese, francese, tedesca e giapponese dei sistemi operativi e delle applicazioni supportati.

>



### Configurazioni consigliate {#recommendedconfigurations}

Adobe consiglia queste configurazioni e fornisce supporto completo o limitato nell’ambito del contratto di manutenzione software standard:

<table> 
 <tbody> 
  <tr> 
   <th>Livello di supporto</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td>R: Supportato<br /> </td> 
   <td>Adobe fornisce supporto e manutenzione completi per questa configurazione. Questa configurazione è coperta dal processo di garanzia della qualità di Adobe.</td> 
  </tr> 
  <tr> 
   <td>R: Supporto limitato</td> 
   <td>Adobe fornisce supporto completo per questa configurazione dopo aver soddisfatto alcuni prerequisiti. Contatta il supporto Adobe Enterprise per informazioni sui prerequisiti e richiedi il supporto.</td> 
  </tr> 
  <tr> 
   <td>L: Supporto limitato</td> 
   <td>Adobe fornisce supporto e manutenzione completi per queste configurazioni dopo aver soddisfatto alcuni prerequisiti. Non tutte le funzionalità sono disponibili nella configurazione. Contatta il supporto Adobe Enterprise per informazioni sui prerequisiti e richiedi il supporto.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Configurazioni non supportate {#unsupported-configurations}

| Livello di supporto | Descrizione |
|---|---|
| E: Previsto lavoro | La configurazione dovrebbe funzionare e non ci sono rapporti al contrario. |
| Z: Non supportato | Configurazione non supportata. Adobe non fornisce alcuna dichiarazione relativa al funzionamento della configurazione e al suo mancato supporto. |

### Macchine virtuali Java (JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms richiede l’esecuzione di una macchina virtuale Java fornita dalla distribuzione Java Development Kit (JDK). Adobe Experience Manager funziona con le seguenti versioni di Java Virtual Machines:

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Platform</strong></p> </th> 
   <th><p><strong>Livello di supporto</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Oracle Java™ SE 8 (64 bit)</p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Versioni e aggiornamenti minori</p> </td> 
  </tr> 
  <tr> 
   <td>Macchina virtuale IBM® J9 (build 2.8, JRE 1.8.0)</td> 
   <td>R: Supportato</td> 
   <td>Versioni e aggiornamenti minori</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* AEM Forms su JEE supporta solo JVM a 64 bit in ambienti di produzione.
>* Si consiglia di tenere traccia dei bollettini sulla sicurezza dal fornitore Java per garantire la sicurezza degli ambienti di produzione e installare gli ultimi aggiornamenti Java.

>



### Database e persistenza CRX {#databases-and-crx-persistence}

#### Supporto per la persistenza AEM {#aem-persistence-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Piattaforma</strong></p> </td> 
   <td><p><strong> Descrizione</strong></p> </td> 
   <td><p><strong>Livello di supporto</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>File system</p> </td> 
   <td><p>Microkernel dell'archivio (file TAR MK)</p> </td> 
   <td><p>Supportata</p> </td> 
  </tr> 
  <tr> 
   <td><p>MongoDB Enterprise 3.4</p> </td> 
   <td><p>Microkernel dell'archivio</p> </td> 
   <td><p>Supportata</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>Microkernel dell'archivio</td> 
   <td>Supportata</td> 
  </tr> 
  <tr> 
   <td><p>Oracle Database 12c, versione 1</p> </td> 
   <td><p>Microkernel dell'archivio</p> </td> 
   <td><p>Supportata</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>Microkernel dell'archivio</p> </td> 
   <td><p>Supportata</p> </td> 
  </tr> 
 </tbody> 
</table>

* MongoDB è un software di terze parti e non è incluso nel pacchetto di licenze AEM. Per ulteriori informazioni, consulta la pagina [Criteri di licenza MongoDB](https://www.mongodb.org/about/licensing/) .

* Per ottenere il massimo dalla distribuzione AEM, Adobe consiglia di concedere in licenza la versione Enterprise MongoDB per poter usufruire del supporto professionale.
* L’Assistenza clienti Adobe assisterà i problemi di qualificazione relativi all’utilizzo di MongoDB con AEM. Per ulteriori informazioni, consulta la pagina [MongoDB per Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
* Il file system include lo storage a blocchi conforme a POSIX. Ciò include la tecnologia di storage in rete. Tenere presente che le prestazioni del file system potrebbero variare e influire sulle prestazioni complessive. Si consiglia di caricare prova AEM in combinazione con il file system di rete/remoto.
* È supportato solo MongoDB Storage Engine WiredTiger.
* Lo Shopping MongoDB non è supportato in AEM.
* AEM Forms su JEE non supporta MySQL per la persistenza RDBMK.
* Il modulo Document Security non utilizza l’archivio dei contenuti. Ciò implica che, se si utilizza solo Document Security e non si intende utilizzare HTML Workspace, moduli HTML5 o moduli adattivi, non installare Content Repository.
* AEM Forms su JEE supporta l’architettura Oracle Multitenant.

#### Supporto DATABASE {#database-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Piattaforma</strong></p> </td> 
   <td><p><strong> Descrizione</strong></p> </td> 
   <td><p><strong>Livello di supporto AEM 6.4</strong></p> </td> 
   <td><p><strong>Supporto di AEM Forms 6.4 su JEE</strong></p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>Microkernel dell'archivio</td> 
   <td>Supportato</td> 
   <td>Supportato</td> 
  </tr> 
  <tr> 
   <td><p>Oracle Database 12c, versione 1</p> </td> 
   <td><p>Microkernel dell'archivio</p> </td> 
   <td><p>Supportato</p> </td> 
   <td><p>Supportato</p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5.7.19<br /> </p> </td> 
   <td><p>Microkernel dell'archivio</p> </td> 
   <td><p>Previsto lavoro</p> </td> 
   <td><p>Supportata</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>Microkernel dell'archivio</p> </td> 
   <td><p>Previsto lavoro</p> </td> 
   <td><p>Supportata</p> </td> 
  </tr> 
 </tbody> 
</table>

### Driver di database {#database-drivers}

<table> 
 <tbody> 
  <tr> 
   <th>Database </th> 
   <th><p><strong>Piattaforma</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td>MySQL</td> 
   <td><p>Connettore MySQL/J 5.7</p> <p>mysql-connector-java-5.1.30-bin.jar(versione 5.1.30)</p> </td> 
   <td><p>Fornito con AEM Forms su installazione JEE</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server<br /> </td> 
   <td><p>Driver JDBC di Microsoft® SQL Server 6.2.1.0<br /> </p> <p>sqljdbc6.jar</p> </td> 
   <td><p>Fornito con AEM Forms per l’installazione JEE.</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle</td> 
   <td><p>Driver JDBC di Oracle Database 12.1.0.2.0</p> <p>ojdbc7.jar (versione 12.1.0.2.0)<br /> </p> </td> 
   <td><p>Fornito con AEM Forms per l’installazione JEE.</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2</td> 
   <td><p>Driver IBM® DB2 Universal JDBC 4.16.53 (db2jcc4.jar)</p> </td> 
   <td><p>Scarica il driver dal <a href="https://www-01.ibm.com/support/docview.wss?uid=swg21363866" target="_blank">sito Web IBM</a></p> </td> 
  </tr> 
 </tbody> 
</table>

### Server applicazioni {#application-servers}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Piattaforma</strong></p> </td> 
   <td><p><strong>Livello di supporto</strong></p> </td> 
   <td><p><strong>Definizioni di patch supportate</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle WebLogic Server 12.2.1 (12c R2) <sup>[1] [2] [4] [8]</sup></p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Service Pack e aggiornamenti critici</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® WebSphere® Application Server 9.0 <sup>[2] [6]</sup><br /> </td> 
   <td>R: Supportato</td> 
   <td>Service Pack e aggiornamenti critici</td> 
  </tr> 
  <tr> 
   <td><p>JBoss® Enterprise Application Platform (EAP) 7.0.6 <sup>[1] [4] [5] [7] [8][11]</sup></p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Patch e patch cumulative per la versione EAP supportata<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>I cluster IBM® WebSphere® sono supportati solo nelle edizioni di distribuzione in rete.

### Sistemi operativi server {#server-operating-systems}

#### Ambienti di produzione {#production-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong> Piattaforma</strong></p> </th> 
   <th><p><strong>Livello di supporto</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>R: Supportato</td> 
   <td>Service Pack e aggiornamenti critici</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server 2012 R2 V6.3</p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Service Pack e aggiornamenti critici</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle Solaris™ 11 - V5.11<sup> [3] [10]</sup></p> </td> 
   <td><p>L: Limitato</p> </td> 
   <td><p>Aggiornamenti e patch</p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat Enterprise Linux 7 (Kernel 3.x)</br><b>Nota:</b> <a href="https://access.redhat.com/articles/4665701">Red Hat Enterprise Linux 6</a> raggiunge la fase di manutenzione e le transizioni alla fase di supporto del ciclo di vita esteso il 30 novembre 2020. Adobe consiglia Red Hat Enterprise Linux 7 per gli aggiornamenti e le nuove installazioni. Le installazioni esistenti possono utilizzare Red Hat Enterprise Linux 6 durante la fase di supporto del ciclo di vita esteso.</p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Versioni minori, aggiornamenti cumulativi e aggiornamenti critici</p> </td> 
  </tr> 
  <tr> 
   <td><p>SUSE® Linux® Enterprise Server 12</p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Service Pack, patch cumulative e aggiornamenti critici della sicurezza</p> </td> 
  </tr> 
  <tr> 
   <td>Aggiornamento 3 di Oracle Linux® 7</td> 
   <td>R: Supportato</td> 
   <td>Service Pack, patch cumulative e aggiornamenti critici della sicurezza</td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> [9]</sup></td> 
   <td>R: Supportato</td> 
   <td>Service Pack, patch cumulative e aggiornamenti critici della sicurezza</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2 [10]</td> 
   <td>R: Supporto limitato</td> 
   <td>Service Pack, patch cumulative e aggiornamenti critici della sicurezza</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>AEM Forms su JEE supporta solo sistemi operativi a 64 bit.

#### Ambiente virtualizzato {#virtualized-environment}

Puoi eseguire AEM Forms su JEE su una macchina fisica o su un ambiente virtuale. Tuttavia, se incontri un problema con AEM Forms in un ambiente virtuale, prova a replicare il problema su una macchina fisica. Se il problema persiste sul computer fisico, contatta il supporto Adobe per una risoluzione. Per problemi che non si replicano sulla macchina fisica, contattare il fornitore dell&#39;ambiente virtuale.

#### Ambienti di sviluppo {#development-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Piattaforma (versione di base)</strong></p> </th> 
   <th>Livello di supporto</th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> </td> 
   <td>E: Previsto lavoro</td> 
   <td><p>Service Pack e aggiornamenti critici</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* AEM Forms su JEE supporta solo sistemi operativi a 64 bit.
>* Il servizio PDF Generator non è supportato in Windows 10.

>



### Eccezioni alle piattaforme server supportate {#exceptions-to-supported-server-platforms}

Considera le seguenti eccezioni durante la scelta di una piattaforma per configurare AEM Forms sul server JEE.

1. AEM Forms su JEE non supporta Oracle WebLogic e JBoss® su IBM® AIX®.
1. AEM Forms su JEE non supporta Oracle WebLogic e IBM® WebSphere® con MySQL.
1. AEM Forms su JEE non supporta Oracle Solaris™ con architettura Intel® (è supportato solo SPARC®).
1. AEM Forms su JEE non supporta Oracle WebLogic e JBoss su SUSE Linux Enterprise Server 12. Solo IBM WebSphere è supportato su SUSE Linux Enterprise Server 12.
1. AEM Forms su JEE non supporta JDK con JBoss® diverso da Oracle Java™ SE.
1. AEM Forms su JEE non supporta JDK con IBM® WebSphere® diverso da IBM® JDK.
1. AEM Forms su JEE non supporta IBM® DB2 con JBoss®.
1. CRX-repository supporta la persistenza di tipo TarMK, MongoDB e database relazionali (RDBMK). Non è possibile avere due diversi sistemi di database tra l&#39;application server e il CRX-repository. Tuttavia, in un ambiente AEM Forms su JEE, puoi utilizzare MongoMK con CRX-repository e un database relazionale supportato con application server.
1. AEM Forms su JEE non supporta il server applicazioni WebSphere su CentOS.
1. I sistemi operativi AIX e Solaris sono disponibili solo per i clienti che eseguono l&#39;aggiornamento.
1. AEM Forms su JEE non supporta il controllo degli accessi basato sui ruoli JBoss (RBAC).

Inoltre, considera i seguenti punti durante la scelta del software per Adobe AEM Forms sulle implementazioni JEE:

* AEM Forms su JEE supporta aggiornamenti, patch e pacchetti di correzioni sulla versione principale e secondaria specificata del software supportato. Tuttavia, l&#39;aggiornamento alla versione principale o secondaria successiva non è supportato se non specificato.
* Le installazioni basate su cluster non supportano la persistenza di TarMK. Per informazioni sulla persistenza supportata, consulta [Scelta di un tipo di persistenza per un&#39;installazione di AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
* AEM Forms su JEE supporta vari software di terze parti in base alla nostra [Policy di supporto software di terze parti](#third-party-patch-support-policy).
* AEM Forms su JEE supporta le piattaforme in base al supporto fornito da fornitori di terze parti. Alcune combinazioni possono non essere consentite da fornitori di terze parti. Ad esempio, molti fornitori non hanno certificato i propri server applicazioni con IBM® DB2. Di conseguenza, anche AEM Forms su JEE non supporta queste combinazioni. Per assicurarsi di scegliere le versioni software supportate, controlla anche la matrice di supporto per i fornitori di terze parti.
* AEM Forms su JEE non supporta lo standby a freddo di TarMK.
* AEM Forms su JEE non supporta il clustering verticale.
* AEM Forms su JEE non supporta il database MySQL in un ambiente cluster.
* RDBMK non funziona con database DB2, MYSQL, MS SQL e Oracle quando i moduli JDBC del pacchetto sono configurati su Weblogic.

### Server LDAP (facoltativo) {#ldap-servers-optional}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Prodotto (versione di base)</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Oracle Unified Directory (OUD) versione 11g 2</td> 
   <td>Service Pack</td> 
  </tr> 
  <tr> 
   <td>Microsoft Active Directory 2016</td> 
   <td>Versione di manutenzione e pacchetti di correzione</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Active Directory 2012</p> </td> 
   <td><p>Aggiornamenti forniti con il sistema operativo</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Active Directory Lightweight Directory Services 2012</p> </td> 
   <td><p>Aggiornamenti forniti con il sistema operativo</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td> 
   <td><p>Feature pack e correzioni intermedie</p> </td> 
  </tr> 
  <tr> 
   <td>IBM Lotus Domino 8.5.0</td> 
   <td>Versione di manutenzione e pacchetti di correzione</td> 
  </tr> 
  <tr> 
   <td>Novell eDirectory 8.8.7</td> 
   <td>Aggiornamenti dei prodotti</td> 
  </tr> 
 </tbody> 
</table>

### Server e-mail (facoltativo) {#email-servers-optional}

* IBM Lotus Domino 9.0
* Microsoft Exchange 2013
* Microsoft Office 365

### Content manager e connettori corrispondenti {#content-managers-and-corresponding-connectors}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Prodotto<br /> </strong></td> 
   <td><strong>Versione</strong></td> 
  </tr> 
  <tr> 
   <td>Server IBM Content Manager</td> 
   <td>8.5 Fix pack 2<br /> </td> 
  </tr> 
  <tr> 
   <td>Client IBM Content Manager</td> 
   <td><p>È supportata la versione 8.5<strong> </strong>è</p> </td> 
  </tr> 
  <tr> 
   <td>EMC Documentum</td> 
   <td>7.0 e 7.3</td> 
  </tr> 
  <tr> 
   <td>Filenet IBM</td> 
   <td>5.2.</td> 
  </tr> 
  <tr> 
   <td>Microsoft Sharepoint</td> 
   <td>2013 e 2016<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Supporto per Cordova {#support-for-cordova}

L’app AEM Forms ora supporta Apache Cordova. Di seguito sono elencate le versioni di Cordova specifiche per la piattaforma supportate:

* Apache Cordova 6.4.0
* Cordova iOS 4.3.0
* Cordova Android 6.0.0
* Cordova Windows 4.4.3

### Supporto software per PDF Generator {#software-support-for-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Prodotto</strong></p> </th> 
   <th><p><strong>Formati supportati per la conversione in PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Traccia classica di Acrobat 2017</a></td> 
   <td>XPS, formati immagine (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF e DWF</td> 
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
   <td>WordPerfect X7</td> 
   <td>WP, WPD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2013</td> 
   <td>VSD, VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD, VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2013</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2013</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formati immagine (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF e TXT</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 3.4</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formati immagine (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF e TXT</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator supporta solo le versioni inglese, francese, tedesca e giapponese dei sistemi operativi e delle applicazioni supportati.
>
>Inoltre:
>
>* PDF Generator richiede la versione a 32 bit di [Acrobat 2017 classic track versione 17.011.30078 o successiva](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) per eseguire la conversione.
>* PDF Generator supporta solo la versione Retail a 32 bit di Microsoft Office Professional Plus e altri software necessari per la conversione.
>* PDF Generator non supporta Microsoft Office 365.
>* Le conversioni PDF Generator per OpenOffice sono supportate solo su Windows, Linux e Solaris.
>* Il servizio HTML2PDF è obsoleto su AIX.
>* Le funzioni OCR PDF, Optimize PDF e Export PDF sono supportate solo su Windows.
>* Una versione di Acrobat è inclusa in un pacchetto con AEM Forms per abilitare la funzionalità PDF Generator. La versione inclusa nel pacchetto deve essere accessibile solo a livello di programmazione con AEM Forms, durante il periodo di validità della licenza AEM Forms, per l’utilizzo con PDF Generator di AEM Forms. Per ulteriori informazioni, consulta la descrizione del prodotto AEM Forms in base alla distribuzione ([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) o [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;

>



### Eccezioni al supporto per l&#39;accessibilità {#exceptions-to-accessibility-support}

I seguenti sottosistemi di AEM Forms non sono [508](https://www.section508.gov/) conformi:

* Interfaccia utente di authoring dei moduli adattivi
* Interfaccia utente di authoring di Forms Manager
* Interfaccia utente di authoring per la gestione delle corrispondenze
* Interfaccia utente amministratore (interfaccia utente di Admin Console)

## Requisiti di sistema per AEM Forms su JEE {#system-requirements-for-aem-forms-on-jee}

### Requisiti hardware minimi {#minimum-hardware-requirements}

<table> 
 <tbody> 
  <tr> 
   <td>Piattaforma</td> 
   <td>Requisiti hardware minimi</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server</td> 
   <td>Processore Intel® Xeon® E5-2680, 2,4 GHz o equivalente<br /> VMWare ESX 5.1 o successivo<br /> RAM: 6 GB (sistema operativo a 64 bit con JVM a 64 bit)<br /> Spazio libero su disco: 15 GB di spazio temporaneo più 22 GB<br /> per AEM Forms su JEE</td> 
  </tr> 
  <tr> 
   <td>Sun Solaris</td> 
   <td>Processore UltraSPARC® IIIi a 1,5 GHz<br /> partizionamento di Solaris Containers (Zones)<br /> RAM: 6 GB (sistema operativo a 64 bit con JVM a 64 bit)<br /> Spazio libero su disco: 6 GB di spazio temporaneo più 22 GB<br /> per AEM Forms su JEE</td> 
  </tr> 
  <tr> 
   <td>IBM AIX</td> 
   <td>P6 pSeries 520 (Model 52A) 9131-52A, processore a 1,8 GHz<br /> LPAR partizionamento<br /> RAM: 6 GB (sistema operativo a 64 bit con JVM a 64 bit)<br /> Spazio libero su disco: 6 GB di spazio temporaneo più 22 GB<br /> per AEM Forms su JEE</td> 
  </tr> 
  <tr> 
   <td>SUSE Linux Enterprise Server</td> 
   <td>Processore Intel Xeon E5-2670v2, 1 vCPU, 2,5 GHz<br /> AWS m3.medium (3 ECU)<br /> RAM: 6 GB (sistema operativo a 64 bit con JVM a 64 bit)<br /> Spazio libero su disco: 6 GB di spazio temporaneo più 22 GB<br /> per AEM Forms su JEE</td> 
  </tr> 
  <tr> 
   <td>Red Hat Enterprise Linux</td> 
   <td>Processore Intel Xeon E5-2670v2, 1 vCPU, 2,5 GHz<br /> AWS m3.medium (3 ECU)<br /> RAM: 6 GB (sistema operativo a 64 bit con JVM a 64 bit)<br /> Spazio libero su disco: 6 GB di spazio temporaneo più 22 GB<br /> per AEM Forms su JEE<br /> </td> 
  </tr> 
  <tr> 
   <td>Requisiti hardware per un ambiente di produzione di piccole dimensioni</td> 
   <td> 
    <ul> 
     <li><strong>Ambiente</strong> basato su Intel: Intel® Xeon® E5-2680, 2,4 GHz o superiore. L'utilizzo di un processore dual-core migliora ulteriormente le prestazioni</li> 
     <li><strong>Ambiente con alimentazione Sun SPARC: </strong> UltraSPARC V o successivo</li> 
     <li><strong>Ambiente basato su IBM AIX: </strong> Power6 o successivo<br /> </li> 
     <li><strong>Memoria:  </strong>4 GB  <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

Per ulteriori requisiti consulta:

* [Requisiti di sistema per un’implementazione di AEM Forms su un singolo server in JEE](https://www.adobe.com/go/learn_aemforms_sysreq_single_64)
* [Requisiti di sistema per un’implementazione in cluster di AEM Forms su JEE](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_64)

## Client supportati per AEM Forms su JEE {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

>[!NOTE]
>
>Sono supportati sia i sistemi operativi a 32 bit che a 64 bit.

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Piattaforma</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> <p>(Enterprise, Pro, Basic)</p> </td> 
   <td>Service Pack e aggiornamenti critici</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Windows® 2012 Server R2</td> 
   <td>Service Pack e aggiornamenti critici</td> 
  </tr> 
  <tr> 
   <td>Server Microsoft® Windows® 2016</td> 
   <td>Service Pack e aggiornamenti critici</td> 
  </tr> 
 </tbody> 
</table>

* Spazio su disco per l&#39;installazione: 1,7 GB solo per Workbench, 2,7 GB su un&#39;unica unità per un&#39;installazione completa di Workbench, Designer e l&#39;assembly di campioni 400 MB per le directory di installazione temporanea - 200 MB nella directory temporanea dell&#39;utente e 200 MB nella directory temporanea di Windows

>[!NOTE]
>
>Se tutte queste posizioni risiedono su un&#39;unica unità, durante l&#39;installazione deve essere disponibile uno spazio di 1,5 GB. I file copiati nelle directory temporanee vengono eliminati al termine dell&#39;installazione.

* Memoria per l&#39;esecuzione di Workbench: 2 GB di RAM
* Requisiti hardware: Processore Intel® Pentium® 4 o AMD equivalente a 1 GHz
* Risoluzione minima del monitor 1024 X 768 pixel o superiore con colore a 16 bit o superiore
* Connessione di rete TCP/IPv4 o TCP/IPv6 a AEM Forms sul server JEE

>[!NOTE]
>
>Per installare Workbench in Windows, è necessario disporre dei privilegi di amministratore. Se stai effettuando l’installazione utilizzando un account non amministratore, il programma di installazione ti chiederà le credenziali per un account appropriato.

### Designer {#designer}

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

### Adobe Acrobat e Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Acrobat e Adobe Reader (base)</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Acrobat 2017 (traccia classica)</td> 
   <td>Versione 17.011.30078 o successiva<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>La famiglia di prodotti Acrobat DC introduce due tracce sia per Acrobat che per Reader, che sono essenzialmente prodotti diversi: &quot;Classic&quot; e &quot;Continuous&quot;. Per informazioni dettagliate e un confronto tra le due tracce, vedere [https://www.adobe.com/go/acrobatdctracks.](https://www.adobe.com/go/acrobatdctracks)

### Browser {#browsers}

#### Desktop {#desktops}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Browser (Base)</strong></p> </th> 
   <th><p><strong>Livello di supporto</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft Edge</p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Service Pack e aggiornamenti</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox 45.x</p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Tutti gli aggiornamenti</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome 46+</p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Tutti gli aggiornamenti</p> </td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x</td> 
   <td>R: Supportato</td> 
   <td>Tutti gli aggiornamenti</td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome e Firefox su MAC OS X</p> </td> 
   <td><p>R: Supportato</p> </td> 
   <td><p>Tutti gli aggiornamenti</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alcune eccezioni relative al browser per i desktop sono le seguenti:
>
>* La maggior parte dei browser moderni non supporta più i plug-in basati su NPAPI. Per informazioni sull’impatto delle applicazioni e dei flussi di lavoro AEM Forms, consulta [Discontinuità dei plug-in del browser NPAPI e relativo impatto](https://helpx.adobe.com/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html).
>* Safari è supportato solo su Macintosh OS X.


#### Client mobili {#mobile-clients}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Browser (Base)</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Chrome su Android™ 4.1.2 e versioni successive</p> </td> 
   <td><p>Tutti gli aggiornamenti</p> </td> 
  </tr> 
  <tr> 
   <td>Safari su iOS 11.0 e versioni successive</td> 
   <td>Tutti gli aggiornamenti</td> 
  </tr> 
  <tr> 
   <td>Internet Explorer su Windows 10</td> 
   <td>Tutti gli aggiornamenti</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge<br /> </td> 
   <td>Tutti gli aggiornamenti<br /> </td> 
  </tr> 
  <tr> 
   <td>Browser Android nativo su Android™ 4.4 e versioni successive</td> 
   <td>Tutti gli aggiornamenti</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Forms Portal è supportato solo su Safari su iPad.

>



### App AEM Forms {#aem-forms-workspace-app}

#### Supporto per dispositivi mobili {#mobile-device-support}

L’app AEM Forms è disponibile sulle seguenti piattaforme:

| **Platform** | **Dispositivi supportati** |
|---|---|
| Apple iOS | Apple iPhone, iPad, iPad Air e iPad mini con iOS 11 e versioni successive. |
| Google Android | Android 4.4 (Andoird Kit Kat) e oltre *[API Livello 19 e superiore]*. L&#39;app AEM Forms è certificata su 7- e 10-pollici Samsung Galaxy tablet e 7-pollici Google Nexus tablet e smartphone popolari. |
| Microsoft Windows | Dispositivi, tablet, laptop e desktop Microsoft Surface con sistema operativo Microsoft Windows 10. |

### Adobe Flash Player {#adobe-flash-player}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Flash Player (base)</strong></p> </th> 
   <th><p><strong>Definizioni di patch supportate</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Versione più recente di Flash Player</p> </td> 
   <td><p>Versioni e aggiornamenti minori</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Adobe [smetterà di aggiornare e distribuire Flash Player alla fine del 2020](https://theblog.adobe.com/adobe-flash-update/).

### Estensione Adobe Document Security per Microsoft Office {#adobe-rights-management-extension-for-microsoft-office}

Fai clic [qui](https://www.adobe.com/it/products/livecycle/rightsmanagement/extension/downloads.html) per visualizzare i requisiti di sistema per l&#39;estensione Adobe Document Security per Microsoft® Office.

### Eccezioni al supporto client {#exceptions-to-client-support}

Microsoft® Windows® 2012 non è supportato per tutti i software lato client specificati, ad eccezione di Reader e Acrobat.

Inoltre, AEM Forms su JEE supporta aggiornamenti, patch e pacchetti di correzioni sulla versione principale e secondaria specificata del software supportato. Tuttavia, l&#39;aggiornamento alla versione principale o secondaria successiva non è supportato se non specificato.

## Criteri di supporto per le patch di terze parti {#third-party-patch-support-policy}

I requisiti software di terze parti per AEM Forms su JEE sono documentati nella sezione &quot;Requisiti di sistema&quot; dei rispettivi documenti di prodotto. Tutta la documentazione è accessibile da [https://adobe.com/go/learn_aemforms_documentation_64](https://adobe.com/go/learn_aemforms_documentation_64) .

AEM Forms sulle piattaforme di riferimento di terze parti di JEE indica il livello di patch specifico dell’infrastruttura di terze parti corrente durante lo sviluppo e la versione di AEM Forms su JEE, e dal livello di patch/service pack minimo dell’infrastruttura supportata da tale versione di AEM Forms su JEE.

Adobe supporta patch urgenti o consigliate emesse da fornitori di terze parti al momento del rilascio, purché i fornitori di terze parti garantiscano la retrocompatibilità con le versioni supportate da AEM Forms su JEE. Adobe supporterà le patch rilasciate solo dopo il livello minimo di patch indicato nella documentazione di AEM Forms su JEE.

In alcuni casi, Adobe non supporta gli aggiornamenti di terze parti che modificano le funzionalità principali e non supportano quindi la piena compatibilità con le versioni precedenti. Per informazioni dettagliate sugli aggiornamenti supportati, consulta [Definizioni delle patch supportate](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html) per prodotti specifici del fornitore e i tipi di patch supportati da Adobe.

In circostanze che sfuggono al controllo di Adobe, le patch di terze parti che rivendicano la retrocompatibilità possono avere un impatto negativo sui prodotti Adobe o sugli ambienti dei clienti. In questi casi, Adobe consiglia ai clienti di valutare l’impatto di qualsiasi patch urgente di terze parti prima di applicarla ai sistemi critici. Adobe collaborerà con terze parti utilizzando ragionevoli sforzi commerciali per risolvere tali problemi, sia tramite i normali programmi di supporto Adobe o da terze parti che rettificano il problema nella relativa patch. Questo non garantisce che una nuova patch di terze parti rilasciata di recente e supportata da Adobe funzioni come documentato dal fornitore o con AEM Forms su JEE.

Adobe si riserva il diritto di modificare le piattaforme di riferimento di terze parti supportate da una versione di AEM Forms su JEE e le relative definizioni di patch supportate in qualsiasi momento.

Puoi trovare ulteriori informazioni per le patch di terze parti anche consultando il sito di supporto Adobe Enterprise per gli articoli della knowledgebase relativi al tuo prodotto.

[**Contatta il supporto**](https://www.adobe.com/account/sign-in.supportportal.html)
