---
title: Configurazione di MySQL per le funzionalità di abilitazione
seo-title: MySQL Configuration for Enablement Features
description: Connessione del server MySQL
seo-description: Connecting your MySQL server
uuid: e02d9404-de75-4fdb-896c-ea3f64f980a3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9222bc93-c231-4ac8-aa28-30d784a4ca3b
role: Admin
exl-id: 1dfb55c2-41cb-445f-9bf8-f12ab6b8e9d8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 4%

---

# Configurazione di MySQL per le funzionalità di abilitazione {#mysql-configuration-for-enablement-features}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

MySQL è un database relazionale utilizzato principalmente per il tracciamento SCORM e i dati di reporting per le risorse di abilitazione. Sono incluse tabelle per altre funzioni quali il tracciamento della pausa/ripresa del video.

Queste istruzioni descrivono come connettersi al server MySQL, stabilire il database di abilitazione e popolare il database con i dati iniziali.

## Requisiti {#requirements}

Prima di configurare la funzionalità di abilitazione di MySQL for Communities, assicurati di

* Installa [Server MySQL](https://dev.mysql.com/downloads/mysql/) Server della community versione 5.6
   * La versione 5.7 non è supportata per SCORM
   * Può essere lo stesso server dell’istanza di authoring AEM
* In tutte le istanze AEM, installare il funzionario [Driver JDBC per MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Installa [Workbench di lavoro MySQL](https://dev.mysql.com/downloads/tools/workbench/)
* In tutte le istanze AEM, installa la [Pacchetto SCORM](enablement.md#scorm)

## Installazione di MySQL {#installing-mysql}

MySQL deve essere scaricato e installato seguendo le istruzioni per il sistema operativo di destinazione.

### Nomi delle tabelle minuscoli {#lower-case-table-names}

Poiché SQL non distingue tra maiuscole e minuscole, per i sistemi operativi con distinzione tra maiuscole e minuscole, è necessario includere un&#39;impostazione per tutte le tabelle con distinzione tra maiuscole e minuscole.

Ad esempio, per specificare tutti i nomi di tabella minuscolo su un sistema operativo Linux:

* Modifica file `/etc/my.cnf`
* In `[mysqld]` aggiungi la seguente riga:
   `lower_case_table_names = 1`

### Set di caratteri UTF8 {#utf-character-set}

Per fornire un supporto multilingue migliore, è necessario utilizzare il set di caratteri UTF8.

Modificare MySQL in modo che UTF8 sia impostato come set di caratteri:
* mysql> NAMES &#39;utf8&#39;;

Impostare il database MySQL come predefinito su UTF8:
* Modifica file `/etc/my.cnf`
* In `[client]` aggiungi la seguente riga:
   `default-character-set=utf8`
* In `[mysqld]` aggiungi la seguente riga:
   `character-set-server=utf8`

## Installazione di Workbench MySQL {#installing-mysql-workbench}

Workbench di MySQL fornisce un&#39;interfaccia utente per l&#39;esecuzione di script SQL che installano lo schema e i dati iniziali.

MySQL Workbench deve essere scaricato e installato seguendo le istruzioni per il sistema operativo di destinazione.

## Connessione abilitazione {#enablement-connection}

Al primo avvio di MySQL Workbench, a meno che non sia già in uso per altri scopi, non verrà ancora visualizzata alcuna connessione:

![chlimage_1-327](assets/chlimage_1-327.png)

### Nuove impostazioni di connessione {#new-connection-settings}

1. Seleziona l’icona &quot;+&quot; a destra di `MySQL Connections`.
1. Nella finestra di dialogo `Setup New Connection`, immetti i valori appropriati per la piattaforma a scopo dimostrativo, con l&#39;istanza AEM autore e MySQL sullo stesso server:
   * Nome connessione: `Enablement`
   * Metodo di connessione: `Standard (TCP/IP)`
   * Nome host: `127.0.0.1`
   * Nome utente: `root`
   * Password: `no password by default`
   * Schema predefinito: `leave blank`
1. Seleziona `Test Connection` per verificare la connessione al servizio MySQL in esecuzione

**Note**:

* La porta predefinita è `3306`
* La `Connection Name` viene selezionato come `datasource` nome in [Configurazione JDBC OSGi](#configure-jdbc-connections)

#### Connessione riuscita {#successful-connection}

![chlimage_1-328](assets/chlimage_1-328.png)

#### Nuova connessione di abilitazione {#new-enablement-connection}

![chlimage_1-329](assets/chlimage_1-329.png)

## Configurazione del database {#database-setup}

All&#39;apertura della nuova connessione di abilitazione, noterai che esiste uno schema di test e account utente predefiniti.

![chlimage_1-330](assets/chlimage_1-330.png)

### Ottenere gli script SQL {#obtain-sql-scripts}

Gli script SQL vengono ottenuti utilizzando CRXDE Lite nell&#39;istanza di authoring. La [Pacchetto SCORM](deploy-communities.md#scorm) deve essere installato:

1. Sfoglia CRXDE Lite
   * Ad esempio: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)
1. Espandi la `/libs/social/config/scorm/` cartella
1. Download `database_scormengine.sql`
1. Download `database_scorm_integration.sql`

![chlimage_1-331](assets/chlimage_1-331.png)

Un metodo per scaricare lo schema è

* Seleziona la `jcr:content`nodo per il file sql
* Osserva il valore per `jcr:data`è un collegamento di visualizzazione
* Selezionare il collegamento di visualizzazione per salvare i dati in un file locale

### Crea database SCORM {#create-scorm-database}

Il database SCORM di abilitazione da creare è:

* name: `ScormEngineDB`
* create dagli script:
   * schema: `database_scormengine.sql`
   * dati: `database_scorm_integration.sql`
Segui i passaggi seguenti (
[open](#step-open-sql-file), [execute](#step-execute-sql-script)) per installare ogni [Script SQL](#obtain-sql-scripts) . [Aggiorna](#refresh) quando necessario per visualizzare i risultati dell’esecuzione dello script.

Prima di installare i dati, assicurati di installare lo schema.

>[!CAUTION]
>
>Se il nome del database viene modificato, assicurarsi di specificarlo correttamente in
>
>* [Configurazione JDBC](#configure-jdbc-connections)
>* [Configurazione SCORM](#configure-scorm)
>


#### Passaggio 1: apri file SQL {#step-open-sql-file}

In MySQL Workbench

* Dal menu a discesa File
* Seleziona `Open SQL Script ...`
* In questo ordine, seleziona una delle seguenti opzioni:
   1. `database_scormengine.sql`
   1. `database_scorm_integration.sql`

![chlimage_1-332](assets/chlimage_1-332.png)

#### Passaggio 2: esegui script SQL {#step-execute-sql-script}

Nella finestra Workbench per il file aperto al passaggio 1, selezionare il `lightening (flash) icon` per eseguire lo script.

Si noti che l&#39;esecuzione della `database_scormengine.sql` per creare il database SCORM potrebbe essere necessario un minuto per completare lo script.

![chlimage_1-333](assets/chlimage_1-333.png)

#### Aggiorna {#refresh}

Una volta eseguiti gli script, è necessario aggiornare `SCHEMAS`della sezione `Navigator` per visualizzare il nuovo database. Utilizza l’icona di aggiornamento a destra di &quot;SCHEMAS&quot;:

![chlimage_1-334](assets/chlimage_1-334.png)

#### Risultato: scormenginedb {#result-scormenginedb}

Dopo aver installato e aggiornato gli SCHEMI, la **`scormenginedb`** sarà visibile.

![chlimage_1-335](assets/chlimage_1-335.png)

## Configurare le connessioni JDBC {#configure-jdbc-connections}

Configurazione OSGi per **Pool di connessioni JDBC Day Commons** configura il driver JDBC MySQL.

Tutte le istanze di pubblicazione e creazione AEM devono puntare allo stesso server MySQL.

Quando MySQL viene eseguito su un server diverso da AEM, il nome host del server deve essere specificato al posto di &quot;localhost&quot; nel connettore JDBC (che popola il [ScormEngine](#configurescormengineservice) config).

* Su ogni istanza di authoring e pubblicazione AEM
* Accesso con privilegi di amministratore
* Accedere al [console web](../../help/sites-deploying/configuring-osgi.md)
   * Ad esempio: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Individua il `Day Commons JDBC Connections Pool`
* Seleziona la `+` per creare una nuova configurazione

![chlimage_1-336](assets/chlimage_1-336.png)

* Immetti i seguenti valori:
   * **[!UICONTROL Classe del driver JDBC]**: `com.mysql.jdbc.Driver`
   * **Connessione DBC URIJ**: `jdbc:mysql://localhost:3306/aem63reporting` specifica il server al posto di localhost se il server MySQL non è lo stesso del server di AEM &#39;this&#39;
   * **[!UICONTROL Nome utente]**: Radice o immettere il nome utente configurato per il server MySQL, se non &quot;root&quot;
   * **[!UICONTROL Password]**: Cancella questo campo se non è impostata alcuna password per MySQL, altrimenti immetti la password configurata per il nome utente MySQL
   * **[!UICONTROL Nome origine dati]**: Nome immesso per [Connessione MySQL](#new-connection-settings)ad esempio, &quot;enablement&quot;
* Seleziona **[!UICONTROL Salva]**

## Configurare lo scorm {#configure-scorm}

### Servizio ScormEngine di AEM Communities {#aem-communities-scormengine-service}

Configurazione OSGi per **Servizio ScormEngine di AEM Communities** configura SCORM per l&#39;utilizzo del server MySQL da parte di una community di abilitazione.

Questa configurazione è presente quando [Pacchetto SCORM](deploy-communities.md#scorm-package) è installato.

Tutte le istanze di pubblicazione e creazione puntano allo stesso server MySQL.

Quando MySQL viene eseguito su un server diverso da AEM, il nome host del server deve essere specificato al posto di &quot;localhost&quot; nel servizio ScormEngine, che in genere viene popolato dal [Connessione JDBC](#configure-jdbc-connections) config.

* Su ogni istanza di authoring e pubblicazione AEM
* Accesso con privilegi di amministratore
* Accedere al [console web](../../help/sites-deploying/configuring-osgi.md)
   * Ad esempio: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
* Individua il `AEM Communities ScormEngine Service`
* Seleziona l’icona di modifica
   ![chlimage_1-337](assets/chlimage_1-337.png)
* Verifica che i seguenti valori dei parametri siano coerenti con [Connessione JDBC](#configurejdbcconnectionspool) config:
   * **[!UICONTROL URI di connessione JDBC]**: `jdbc:mysql://localhost:3306/ScormEngineDB` *ScormEngineDB* è il nome di database predefinito negli script SQL
   * **[!UICONTROL Nome utente]**: Radice o immettere il nome utente configurato per il server MySQL, se non &quot;root&quot;
   * **[!UICONTROL Password]**: Cancella questo campo se non è impostata alcuna password per MySQL, altrimenti immetti la password configurata per il nome utente MySQL
* Per quanto riguarda il seguente parametro:
   * **[!UICONTROL Password utente scorm]**: NON MODIFICARE

      Solo per uso interno. È per un utente di servizio speciale utilizzato da AEM Communities per comunicare con il motore di punteggio.
* Seleziona **[!UICONTROL Salva]**

### Filtro CSRF Granite Adobe {#adobe-granite-csrf-filter}

Per garantire il corretto funzionamento dei corsi di abilitazione in tutti i browser, è necessario aggiungere Mozilla come Agente utente che non è controllato dal filtro CSRF.

* Su ogni istanza di pubblicazione AEM
* Accesso con privilegi di amministratore
* Accedere al [console web](../../help/sites-deploying/configuring-osgi.md)
   * Ad esempio: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
* Individua `Adobe Granite CSRF Filter`
* Seleziona l’icona di modifica
   ![chlimage_1-338](assets/chlimage_1-338.png)
* Seleziona la `[+]` icona per aggiungere un agente utente sicuro
* Inserisci `Mozilla/*`
* Seleziona **[!UICONTROL Salva]**
