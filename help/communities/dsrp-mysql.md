---
title: Configurazione MySQL per DSRP
seo-title: MySQL Configuration for DSRP
description: Come connettersi al server MySQL e stabilire il database UGC
seo-description: How to connect to the MySQL server and establish the UGC database
uuid: c058cc88-7ca2-4aed-9a36-b080e603f886
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: edc3043c-7ec4-4e4a-b008-95f1784f012e
role: Admin
exl-id: 1de1ffc6-63f8-4316-a2fa-5095d407c265
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 4%

---

# Configurazione MySQL per DSRP {#mysql-configuration-for-dsrp}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

MySQL è un database relazionale che può essere utilizzato per memorizzare il contenuto generato dall&#39;utente (UGC).

Queste istruzioni descrivono come connettersi al server MySQL e stabilire il database UGC.

## Requisiti {#requirements}

* [pacchetto di funzioni per le community più recenti](deploy-communities.md#latestfeaturepack)
* [Driver JDBC per MySQL](deploy-communities.md#jdbc-driver-for-mysql)
* Database relazionale:

   * [Server MySQL](https://dev.mysql.com/downloads/mysql/) Server della community versione 5.6 o successiva

      * Può essere eseguito sullo stesso host AEM o eseguito in remoto
   * [Workbench di lavoro MySQL](https://dev.mysql.com/downloads/tools/workbench/)


## Installazione di MySQL {#installing-mysql}

[MySQL](https://dev.mysql.com/downloads/mysql/) devono essere scaricati e installati seguendo le istruzioni per il sistema operativo di destinazione.

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

## Connessione community {#communities-connection}

Al primo avvio di MySQL Workbench, a meno che non sia già in uso per altri scopi, non verrà ancora visualizzata alcuna connessione:

![chlimage_1-104](assets/chlimage_1-104.png)

### Nuove impostazioni di connessione {#new-connection-settings}

1. Seleziona la `+` a destra di `MySQL Connections`.
1. Nella finestra di dialogo `Setup New Connection`, immetti i valori appropriati per la piattaforma

   A scopo dimostrativo, con l&#39;istanza AEM autore e MySQL sullo stesso server:

   * Nome connessione: `Communities`
   * Metodo di connessione: `Standard (TCP/IP)`
   * Nome host: `127.0.0.1`
   * Nome utente: `root`
   * Password: `no password by default`
   * Schema predefinito: `leave blank`

1. Seleziona `Test Connection` per verificare la connessione al servizio MySQL in esecuzione

**Note**:

* La porta predefinita è `3306`
* Il nome di connessione scelto viene immesso come nome dell’origine dati in [Configurazione JDBC OSGi](#configurejdbcconnections)

#### Nuova connessione community {#new-communities-connection}

![chlimage_1-105](assets/chlimage_1-105.png)

## Configurazione del database {#database-setup}

Apri la connessione Communities per installare il database.

![chlimage_1-106](assets/chlimage_1-106.png)

### Ottenere lo script SQL {#obtain-the-sql-script}

Lo script SQL viene ottenuto dal repository AEM:

1. Sfoglia CRXDE Lite

   * Ad esempio: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Seleziona la cartella /libs/social/config/datastore/dsrp/schema
1. Download `init-schema.sql`

![chlimage_1-107](assets/chlimage_1-107.png)

Un metodo per scaricare lo schema è

* Seleziona la `jcr:content`nodo per il file sql
* Osserva il valore per `jcr:data`è un collegamento di visualizzazione

* Selezionare il collegamento di visualizzazione per salvare i dati in un file locale

### Creare il database DSRP {#create-the-dsrp-database}

Per installare il database, effettua le seguenti operazioni. Il nome predefinito del database è `communities`.

Se il nome del database viene modificato nello script, assicurarsi di modificarlo anche nel [Configurazione JDBC](#configurejdbcconnections).

#### Passaggio 1: apri file SQL {#step-open-sql-file}

In MySQL Workbench

* Dal menu a discesa File
* Seleziona il download `init_schema.sql`

![chlimage_1-108](assets/chlimage_1-108.png)

#### Passaggio 2: esegui script SQL {#step-execute-sql-script}

Nella finestra Workbench per il file aperto al passaggio 1, selezionare il `lightening (flash) icon` per eseguire lo script.

Nell&#39;immagine seguente, la `init_schema.sql` il file è pronto per essere eseguito:

![chlimage_1-109](assets/chlimage_1-109.png)

#### Aggiorna {#refresh}

Una volta eseguito lo script, è necessario aggiornare `SCHEMAS`della sezione `Navigator` per visualizzare il nuovo database. Utilizza l’icona di aggiornamento a destra di &quot;SCHEMAS&quot;:

![chlimage_1-110](assets/chlimage_1-110.png)

## Configurare la connessione JDBC {#configure-jdbc-connection}

Configurazione OSGi per **Pool di connessioni JDBC Day Commons** configura il driver JDBC MySQL.

Tutte le istanze di pubblicazione e creazione AEM devono puntare allo stesso server MySQL.

Quando MySQL viene eseguito su un server diverso da AEM, il nome host del server deve essere specificato al posto di &quot;localhost&quot; nel connettore JDBC.

* Su ogni istanza di authoring e pubblicazione AEM
* Accesso con privilegi di amministratore
* Accedere al [console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)

* Individua il `Day Commons JDBC Connections Pool`
* Seleziona la `+` icona per creare una nuova configurazione di connessione

![chlimage_1-111](assets/chlimage_1-111.png)

* Immetti i seguenti valori:

   * **[!UICONTROL Classe del driver JDBC]**: `com.mysql.jdbc.Driver`
   * **[!UICONTROL URI di connessione JDBC]**: `jdbc:mysql://localhost:3306/communities?characterEncoding=UTF-8`

      Specificare il server al posto di localhost se il server MySQL non è lo stesso del server AEM &#39;this&#39;

      *community* è il nome predefinito del database (schema)

   * **[!UICONTROL Nome utente]**: `root`

      Oppure immettere il nome utente configurato per il server MySQL, se non &quot;root&quot;

   * **[!UICONTROL Password]**:

      Cancella questo campo se non è impostata alcuna password per MySQL,

      altrimenti immettere la password configurata per il nome utente MySQL
   * **[!UICONTROL Nome origine dati]**: nome immesso per [Connessione MySQL](#new-connection-settings)ad esempio, &quot;community&quot;

* Seleziona **[!UICONTROL Salva]**
