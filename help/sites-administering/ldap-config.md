---
title: Configurazione di LDAP con AEM 6
seo-title: Configuring LDAP with AEM 6
description: Scopri come configurare LDAP con AEM.
seo-description: Learn how to configure LDAP with AEM.
uuid: 0007def4-86f0-401d-aa37-c8d49d5acea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 5faf6ee5-9242-48f4-87a8-ada887a3be1e
exl-id: 1e329725-538a-4058-8832-4eba036f7972
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1684'
ht-degree: 0%

---

# Configurazione di LDAP con AEM 6 {#configuring-ldap-with-aem}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

LDAP (il **L** poco **D** rettorio **A** accesso **P**(protocollo) viene utilizzato per accedere ai servizi centralizzati di directory. Questo consente di ridurre lo sforzo necessario per gestire gli account utente in quanto è possibile accedervi da più applicazioni. Uno di questi server LDAP è Active Directory. LDAP viene spesso utilizzato per ottenere Single Sign-On che consente a un utente di accedere a più applicazioni dopo l&#39;accesso una volta.

Gli account utente possono essere sincronizzati tra il server LDAP e l&#39;archivio, con i dettagli dell&#39;account LDAP che vengono salvati nell&#39;archivio. Questo consente di assegnare gli account ai gruppi di repository per l&#39;allocazione delle autorizzazioni e dei privilegi richiesti.

L&#39;archivio utilizza l&#39;autenticazione LDAP per autenticare tali utenti, con le credenziali trasmesse al server LDAP per la convalida, che è necessaria prima di consentire l&#39;accesso all&#39;archivio. Per migliorare le prestazioni, le credenziali convalidate correttamente possono essere memorizzate nella cache dell’archivio, con un timeout di scadenza per garantire che la riconvalida si verifichi dopo un periodo appropriato.

Quando un account viene rimosso dalla convalida del server LDAP non viene più concesso e viene quindi negato l&#39;accesso all&#39;archivio. È inoltre possibile eliminare i dettagli degli account LDAP salvati nell&#39;archivio.

L&#39;utilizzo di tali account è trasparente per gli utenti, non vedono alcuna differenza tra gli account utente e di gruppo creati da LDAP e quelli creati esclusivamente nell&#39;archivio.

Nel AEM 6, il supporto LDAP viene fornito con una nuova implementazione che richiede un tipo di configurazione diverso rispetto alle versioni precedenti.

Tutte le configurazioni LDAP sono ora disponibili come configurazioni OSGi. Possono essere configurati tramite la console di gestione web all’indirizzo:\
`https://serveraddress:4502/system/console/configMgr`

Per far funzionare LDAP con AEM, è necessario creare tre configurazioni OSGi:

1. Un provider di identità LDAP (IDP).
1. Un Gestore Di Sincronizzazione.
1. Un Modulo Di Accesso Esterno.

>[!NOTE]
>
>Guarda [Modulo di accesso esterno Oak - Autenticazione con LDAP e oltre]https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-oak-external-login-module-authenticating-with-ldap-and-beyond.html) per immergere in profondità i moduli di accesso esterni.
>
>Per leggere un esempio di configurazione di Experience Manager con Apache DS, vedi [Configurazione di Adobe Experience Manager 6.4 per l’utilizzo del servizio directory Apache.](https://helpx.adobe.com/experience-manager/using/configuring-aem64-apache-directory-service.html)

## Configurazione del provider di identità LDAP {#configuring-the-ldap-identity-provider}

Il provider di identità LDAP viene utilizzato per definire come gli utenti vengono recuperati dal server LDAP.

È disponibile nella console di gestione nella sezione **Provider di identità LDAP Apache Jackrabbit Oak** nome.

Per il provider di identità LDAP sono disponibili le seguenti opzioni di configurazione:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome provider LDAP</strong></td> 
   <td>Nome della configurazione del provider LDAP.</td> 
  </tr> 
  <tr> 
   <td><strong>Nome host server LDAP</strong><br /> </td> 
   <td>Nome host del server LDAP</td> 
  </tr> 
  <tr> 
   <td><strong>Porta server LDAP</strong></td> 
   <td>Porta del server LDAP</td> 
  </tr> 
  <tr> 
   <td><strong>Usa SSL</strong></td> 
   <td>Indica se utilizzare una connessione SSL (LDAP).</td> 
  </tr> 
  <tr> 
   <td><strong>Usa TLS</strong></td> 
   <td>Indica se TLS deve essere avviato sulle connessioni.</td> 
  </tr> 
  <tr> 
   <td><strong>Disattiva controllo certificati</strong></td> 
   <td>Indica se la convalida del certificato del server deve essere disabilitata.</td> 
  </tr> 
  <tr> 
   <td><strong>DN di associazione</strong></td> 
   <td>DN dell'utente per l'autenticazione. Se questo campo viene lasciato vuoto, verrà eseguito un binding anonimo.</td> 
  </tr> 
  <tr> 
   <td><strong>Password binding</strong></td> 
   <td>Password dell'utente per l'autenticazione</td> 
  </tr> 
  <tr> 
   <td><strong>Timeout ricerca</strong></td> 
   <td>Tempo di timeout della ricerca</td> 
  </tr> 
  <tr> 
   <td><strong>Massimo del pool di amministratori attivo</strong></td> 
   <td>Dimensione massima attiva del pool di connessioni amministratore.</td> 
  </tr> 
  <tr> 
   <td><strong>Massimo del pool di utenti attivo</strong></td> 
   <td>Dimensione massima attiva del pool di connessioni utente.</td> 
  </tr> 
  <tr> 
   <td><strong>DN base utente</strong></td> 
   <td>DN per ricerche utente</td> 
  </tr> 
  <tr> 
   <td><strong>Classi di oggetti utente</strong></td> 
   <td>L'elenco delle classi oggetto che una voce utente deve contenere.</td> 
  </tr> 
  <tr> 
   <td><strong>Attributo ID utente</strong></td> 
   <td>Nome dell'attributo contenente l'ID utente.</td> 
  </tr> 
  <tr> 
   <td><strong>Filtro extra utente</strong></td> 
   <td>Filtro LDAP aggiuntivo da utilizzare per la ricerca di utenti. Il filtro finale viene formattato come segue: '(&amp;()&lt;idattr&gt;=&lt;userid&gt;)(objectclass=&lt;objectclass&gt;)&lt;extrafilter&gt;)' (user.extraFilter)</td> 
  </tr> 
  <tr> 
   <td><strong>Percorsi DN utente</strong></td> 
   <td>Controlla se il DN deve essere utilizzato per calcolare una parte del percorso intermedio.</td> 
  </tr> 
  <tr> 
   <td><strong>DN base gruppo</strong></td> 
   <td>DN di base per ricerche di gruppi.</td> 
  </tr> 
  <tr> 
   <td><strong>Classi oggetto gruppo</strong></td> 
   <td>L'elenco delle classi oggetto che una voce di gruppo deve contenere.</td> 
  </tr> 
  <tr> 
   <td><strong>Attributo nome gruppo</strong></td> 
   <td>Nome dell'attributo contenente il nome del gruppo.</td> 
  </tr> 
  <tr> 
   <td><strong>Raggruppa filtro aggiuntivo</strong></td> 
   <td>Filtro LDAP aggiuntivo da utilizzare per la ricerca di gruppi. Il filtro finale è formattato come: '(&amp;()&lt;nameattr&gt;=&lt;groupname&gt;)(objectclass=&lt;objectclass&gt;)&lt;extrafilter&gt;)"</td> 
  </tr> 
  <tr> 
   <td><strong>Percorsi DN di gruppo</strong></td> 
   <td>Controlla se il DN deve essere utilizzato per calcolare una parte del percorso intermedio.</td> 
  </tr> 
  <tr> 
   <td><strong>Attributo membro del gruppo</strong></td> 
   <td>Attributo di gruppo che contiene i membri di un gruppo.</td> 
  </tr> 
 </tbody> 
</table>

## Configurazione Del Gestore Di Sincronizzazione {#configuring-the-synchronization-handler}

Il gestore di sincronizzazione definirà la modalità di sincronizzazione degli utenti e dei gruppi del provider di identità con il repository.

Si trova sotto la **Apache Jackrabbit Oak Default Sync Handler** nella console di gestione.

Per il gestore di sincronizzazione sono disponibili le seguenti opzioni di configurazione:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Nome del gestore di sincronizzazione</strong></td> 
   <td>Nome della configurazione di sincronizzazione.</td> 
  </tr> 
  <tr> 
   <td><strong>Ora di scadenza utente</strong></td> 
   <td>Durata fino alla scadenza di un utente sincronizzato.</td> 
  </tr> 
  <tr> 
   <td><strong>Iscrizione automatica utente</strong></td> 
   <td>Elenco di gruppi a cui viene aggiunto automaticamente un utente sincronizzato.</td> 
  </tr> 
  <tr> 
   <td><strong>Mappatura proprietà utente</strong></td> 
   <td>Definizione di mappatura elenco delle proprietà locali da quelle esterne.</td> 
  </tr> 
  <tr> 
   <td><strong>Prefisso percorso utente</strong></td> 
   <td>Prefisso del percorso utilizzato per la creazione di nuovi utenti.</td> 
  </tr> 
  <tr> 
   <td><strong>Scadenza iscrizione utente</strong></td> 
   <td>Tempo dopo la scadenza dell'iscrizione.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Profondità di nidificazione dell'iscrizione dell'utente</strong></td> 
   <td>Restituisce la profondità massima della nidificazione del gruppo quando le relazioni di appartenenza vengono sincronizzate. Il valore 0 disabilita efficacemente la ricerca di appartenenza al gruppo. Il valore 1 aggiunge solo i gruppi diretti di un utente. Questo valore non ha alcun effetto quando si sincronizzano singoli gruppi solo quando si sincronizzano gli antenati di un'appartenenza utente.</td> 
  </tr> 
  <tr> 
   <td><strong>Ora di scadenza del gruppo</strong></td> 
   <td>Durata fino alla scadenza di un gruppo sincronizzato.</td> 
  </tr> 
  <tr> 
   <td><strong>Iscrizione automatica al gruppo</strong></td> 
   <td>Elenco di gruppi a cui viene aggiunto automaticamente un gruppo sincronizzato.</td> 
  </tr> 
  <tr> 
   <td><strong>Mappatura delle proprietà del gruppo</strong></td> 
   <td>Definizione di mappatura elenco delle proprietà locali da quelle esterne.</td> 
  </tr> 
  <tr> 
   <td><strong>Prefisso percorso gruppo</strong></td> 
   <td>Prefisso percorso utilizzato per la creazione di nuovi gruppi.</td> 
  </tr> 
 </tbody> 
</table>

## Modulo di accesso esterno {#the-external-login-module}

Il modulo di accesso esterno si trova sotto la **Modulo di accesso esterno Apache Jackrabbit Oak** nella console di gestione.

>[!NOTE]
>
>Il modulo di accesso esterno Apache Jackrabbit Oak implementa le specifiche Java Authentication and Authorization Servi (JAAS) . Consulta la sezione [guida ufficiale di riferimento per la sicurezza Java di Oracle](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jaas/JAASRefGuide.html) per ulteriori informazioni.

Il suo compito è quello di definire il provider di identità e il gestore di sincronizzazione da utilizzare, legando in modo efficace i due moduli.

Sono disponibili le seguenti opzioni di configurazione:

| **Classifica JAAS** | Specifica della classificazione (cioè l’ordine di ordinamento) della voce del modulo di accesso. Le voci vengono ordinate in ordine decrescente (ad esempio, le configurazioni con ranking maggiore vengono prima). |
|---|---|
| **Flag di controllo JAAS** | Proprietà che specifica se un LoginModule è OBBLIGATORIO, OBBLIGATORIO, SUFFICIENTE o FACOLTATIVO.Per ulteriori informazioni sul significato di questi flag, fare riferimento alla documentazione di configurazione JAAS. |
| **Realm JAAS** | Nome dell&#39;area di autenticazione (o nome dell&#39;applicazione) rispetto al quale viene registrato il modulo di accesso. Se non viene fornito alcun nome di realm, LoginModule viene registrato con un realm predefinito come configurato nella configurazione Felix JAAS. |
| **Nome del provider di identità** | Nome del provider di identità. |
| **Nome del gestore di sincronizzazione** | Nome del gestore di sincronizzazione. |

>[!NOTE]
>
>Se prevedi di avere più di una configurazione LDAP con la tua istanza AEM, per ogni configurazione devono essere creati provider di identità e gestori di sincronizzazione separati.

## Configurare LDAP su SSL {#configure-ldap-over-ssl}

AEM 6 può essere configurato per l&#39;autenticazione con LDAP su SSL seguendo la procedura seguente:

1. Controlla la **Usa SSL** o **Usa TLS** caselle di controllo durante la configurazione [Provider di identità LDAP](#configuring-the-ldap-identity-provider).
1. Configura il gestore di sincronizzazione e il modulo di accesso esterno in base alla configurazione.
1. Se necessario, installa i certificati SSL nella macchina virtuale Java. Questo può essere fatto utilizzando keytool:

   `keytool -import -alias localCA -file <certificate location> -keystore <keystore location>`

1. Verifica la connessione al server LDAP.

### Creazione di certificati SSL {#creating-ssl-certificates}

I certificati autofirmati possono essere utilizzati durante la configurazione di AEM per l&#39;autenticazione con LDAP tramite SSL. Di seguito è riportato un esempio di procedura di lavoro per la generazione di certificati da utilizzare con AEM.

1. Assicurati di avere una libreria SSL installata e funzionante. Questa procedura utilizza OpenSSL come esempio.

1. Crea un file di configurazione OpenSSL personalizzato (cnf). Questo può essere fatto copiando il file di configurazione **openssl.cnf **predefinito e personalizzandolo. Nei sistemi UNIX, si trova in genere in `/usr/lib/ssl/openssl.cnf`

1. Procedi alla creazione della chiave radice CA eseguendo il comando sottostante in un terminale:

   ```
   openssl genpkey -algorithm [public key algorithm] -out certificatefile.key -pkeyopt [public key algorithm option] 
   ```

1. Quindi, crea un nuovo certificato autofirmato:

   `openssl req -new -x509 -days [number of days for certification] -key certificatefile.key -out root-ca.crt -config CA/openssl.cnf`

1. Inspect è il certificato appena generato per essere sicuro che tutto sia in ordine:

   `openssl x509 -noout -text -in root-ca.crt`

1. Assicurati che siano presenti tutte le cartelle specificate nel file di configurazione del certificato (.cnf). In caso contrario, creale.
1. Crea un seed casuale, eseguendo, ad esempio:

   `openssl rand -out private/.rand 8192`

1. Sposta i file .pem creati nelle posizioni configurate nel file .cnf .

1. Infine, aggiungi il certificato al keystore Java.

## Abilitazione della registrazione di debug {#enabling-debug-logging}

Per risolvere i problemi di connessione, è possibile abilitare la registrazione di debug sia per il provider di identità LDAP che per il modulo di accesso esterno.

Per abilitare la registrazione di debug, è necessario:

1. Passa alla console di gestione Web.
1. Trova &quot;Apache Sling Logging Logger Configuration&quot; e crea due logger con le seguenti opzioni:

* Livello di log: Debug
* File di log logs/ldap.log
* Pattern messaggio: {0,data,dd.MM.yyyy HH:mm:s.SSS} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.security.authentication.ldap

* Livello di log: Debug
* File di log: logs/external.log
* Pattern messaggio: {0,data,dd.MM.yyyy HH:mm:s.SSS} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.spi.security.authentication.external

## Parola sull&#39;affiliazione al gruppo {#a-word-on-group-affiliation}

Gli utenti sincronizzati tramite LDAP possono far parte di diversi gruppi in AEM. Questi gruppi possono essere gruppi LDAP esterni che verranno aggiunti a AEM come parte del processo di sincronizzazione, ma possono anche essere gruppi che vengono aggiunti separatamente e non fanno parte dello schema di affiliazione del gruppo LDAP originale.

Nella maggior parte dei casi, possono essere gruppi aggiunti da un amministratore AEM locale o da qualsiasi altro provider di identità.

Se un utente viene rimosso da un gruppo sul server LDAP, la modifica si rifletterà anche sul lato AEM al momento della sincronizzazione. Tuttavia, tutte le altre affiliazioni di gruppo dell&#39;utente che non sono state aggiunte da LDAP rimarranno in vigore.

AEM rileva e gestisce la rimozione degli utenti da gruppi esterni utilizzando `rep:externalId` proprietà. Questa proprietà viene aggiunta automaticamente a qualsiasi utente o gruppo sincronizzato dal Gestore sincronizzazione e contiene informazioni sul provider di identità di origine.

Per ulteriori informazioni, consulta la documentazione di Apache Oak su [Sincronizzazione di utenti e gruppi](https://jackrabbit.apache.org/oak/docs/security/authentication/usersync.html).

## Problemi noti {#known-issues}

Se prevedi di utilizzare LDAP su SSL, assicurati che i certificati utilizzati siano creati senza l&#39;opzione di commento Netscape. Se questa opzione è abilitata, l’autenticazione avrà esito negativo con un errore di Handshake SSL.
