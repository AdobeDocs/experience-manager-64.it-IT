---
title: Configurare origini dati
seo-title: Configurare origini dati
description: Scopri come configurare diversi tipi di origini dati e come sfruttarle per creare modelli di dati modulo.
seo-description: Scopri come configurare diversi tipi di origini dati e come sfruttarle per creare modelli di dati modulo.
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: Form Data Model
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configurare le origini dati {#configure-data-sources}

Scopri come configurare diversi tipi di origini dati e come sfruttarle per creare modelli di dati modulo.

![](do-not-localize/data-integeration.png)

L’integrazione dei dati di AEM Forms consente di configurare e connettersi a diverse origini dati. I seguenti tipi sono supportati come predefiniti. Tuttavia, con poca personalizzazione, puoi integrare anche altre origini dati.

* Database relazionali - MySQL, Microsoft SQL Server, IBM DB2 e Oracle RDBMS
* Profilo utente AEM
* Servizi web RESTful
* Servizi web basati su SOAP
* Servizi OData

L’integrazione dei dati supporta i tipi di autenticazione predefiniti OAuth2.0, autenticazione di base e API Key e consente l’implementazione dell’autenticazione personalizzata per l’accesso ai servizi web. Mentre i servizi RESTful, basati su SOAP e OData sono configurati in AEM Cloud Services, JDBC per i database relazionali e il connettore per AEM profilo utente sono configurati in AEM console web.

## Configurare il database relazionale {#configure-relational-database}

È possibile configurare database relazionali utilizzando AEM configurazione della console Web. Effettua le seguenti operazioni:

1. Vai AEM console Web all&#39;indirizzo `https://[server]:[host]/system/console/configMgr`.
1. Cerca la configurazione **[!UICONTROL Apache Sling Connection Pooled DataSource]** . Tocca per aprire la configurazione in modalità di modifica.
1. Nella finestra di dialogo di configurazione, specifica i dettagli del database da configurare, ad esempio:

   * Nome dell’origine dati
   * Proprietà del servizio origine dati che memorizza il nome dell&#39;origine dati
   * Nome della classe Java per il driver JDBC
   * URI di connessione JDBC
   * Nome utente e password per stabilire la connessione con il driver JDBC

   >[!NOTE]
   >
   >Prima di configurare l’origine dati, assicurati di crittografare le informazioni sensibili come le password. Per crittografare:
   >
   >1. Passa a `https://[server]:[port]/system/console/crypto`.
   >1. Nel campo **[!UICONTROL Testo normale]** , specifica la password o qualsiasi stringa da crittografare e fai clic su **[!UICONTROL Protect]**.

   >
   >Il testo crittografato viene visualizzato nel campo Testo protetto che è possibile specificare nella configurazione.

1. Abilitare **[!UICONTROL Test su prestito]** o **[!UICONTROL Test su ritorno]** per specificare che gli oggetti vengono convalidati prima di essere presi in prestito o restituiti rispettivamente da e al pool.
1. Specificare una query SQL SELECT nel campo **[!UICONTROL Query di convalida]** per convalidare le connessioni dal pool. La query deve restituire almeno una riga. In base al database, specifica una delle seguenti opzioni:

   * SELECT 1 (MySQL e MS SQL)
   * SELECT 1 from dual (Oracle)

1. Tocca **[!UICONTROL Salva]** per salvare la configurazione.

## Configurare AEM profilo utente {#configure-aem-user-profile}

È possibile configurare AEM profilo utente utilizzando la configurazione di User Profile Connector in AEM Web Console. Effettua le seguenti operazioni:

1. Vai AEM console Web all&#39;indirizzo `https://[server]:[host]/system/console/configMgr`.
1. Cerca **[!UICONTROL Integrazioni dati AEM Forms - Configurazione connettore profilo utente]** e tocca per aprire la configurazione in modalità di modifica.
1. Nella finestra di dialogo Configurazione connettore profilo utente puoi aggiungere, rimuovere o aggiornare le proprietà del profilo utente. Le proprietà specificate saranno disponibili per l’uso nel modello dati del modulo. Utilizza il formato seguente per specificare le proprietà del profilo utente:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Esempi:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >Il **&amp;ast;** nell&#39;esempio precedente denota tutti i nodi sotto il nodo `profile/empLocation/` nel profilo utente AEM nella struttura CRXDE. Ciò significa che il modello dati del modulo può accedere alla proprietà `city` di tipo `string` presente in qualsiasi nodo sotto il nodo `profile/empLocation/`. Tuttavia, i nodi che contengono la proprietà specificata devono seguire una struttura coerente.

1. Tocca **[!UICONTROL Salva]** per salvare la configurazione.

## Configurare la cartella per le configurazioni del servizio cloud {#cloud-folder}

>[!NOTE]
>
>La configurazione della cartella dei servizi cloud è necessaria per configurare i servizi cloud per i servizi RESTful, SOAP e OData.

Tutte le configurazioni del servizio cloud in AEM sono consolidate nella cartella `/conf` nell’archivio AEM. Per impostazione predefinita, la cartella `conf` contiene la cartella `global` in cui è possibile creare configurazioni del servizio cloud. Tuttavia, devi abilitarlo manualmente per le configurazioni cloud. Puoi anche creare cartelle aggiuntive in `conf` per creare e organizzare configurazioni di servizi cloud.

Per configurare la cartella per le configurazioni del servizio cloud:

1. Vai a **[!UICONTROL Strumenti > Generale > Browser di configurazione]**.
   * Per ulteriori informazioni, consulta la [documentazione del browser di configurazione](/help/sites-administering/configurations.md) .
1. Effettua le seguenti operazioni per abilitare la cartella globale per le configurazioni cloud o salta questo passaggio per creare e configurare un’altra cartella per le configurazioni del servizio cloud.

   1. Nel **[!UICONTROL Browser configurazioni]**, seleziona la cartella `global` e tocca **[!UICONTROL Proprietà]**.
   1. Nella finestra di dialogo **[!UICONTROL Proprietà configurazione]**, abilita **[!UICONTROL Configurazioni cloud]**.
   1. Tocca **[!UICONTROL Salva e chiudi]** per salvare la configurazione e uscire dalla finestra di dialogo.

1. Nel **[!UICONTROL Browser di configurazione]**, tocca **[!UICONTROL Crea]**.
1. Nella finestra di dialogo **[!UICONTROL Crea configurazione]**, specifica un titolo per la cartella e abilita **[!UICONTROL Configurazioni cloud]**.
1. Tocca **[!UICONTROL Crea]** per creare la cartella abilitata per le configurazioni del servizio cloud.

## Configura i servizi web RESTful {#configure-restful-web-services}

Il servizio Web RESTful può essere descritto utilizzando [Specifiche Swagger](https://swagger.io/specification/) in formato JSON o YAML in un file di definizione Swagger. Per configurare il servizio Web RESTful in AEM Cloud Services, accertati di disporre del file Swagger sul sistema di file o dell’URL in cui è ospitato il file.

Per configurare i servizi RESTful, procedi come segue:

1. Vai a **[!UICONTROL Strumenti > Cloud Services > Origini dati]**. Tocca per selezionare la cartella in cui desideri creare una configurazione cloud.

   Per informazioni sulla creazione e la configurazione di una cartella per le configurazioni dei servizi cloud, consulta [Configurare la cartella per le configurazioni dei servizi cloud.](/help/forms/using/configure-data-sources.md#cloud-folder)

1. Tocca **[!UICONTROL Crea]** per aprire la finestra di dialogo **[!UICONTROL Crea configurazione origine dati]**. Specifica un nome ed eventualmente un titolo per la configurazione, seleziona **[!UICONTROL RESTful Service]** dal menu a discesa **[!UICONTROL Tipo di servizio]**, se lo desideri, sfoglia e seleziona un&#39;immagine di miniatura per la configurazione, quindi tocca **[!UICONTROL Avanti]**.
1. Specifica i seguenti dettagli per il servizio RESTful:

   * Seleziona URL o File dal menu a discesa Sorgente Swagger e specifica quindi l’URL Swagger nel file di definizione Swagger o carica il file Swagger dal file system locale.
   * Seleziona il tipo di autenticazione — Nessuno, OAuth2.0, Autenticazione di base, Chiave API o Autenticazione personalizzata — per accedere al servizio RESTful e, di conseguenza, fornisci i dettagli per l’autenticazione.

1. Tocca **[!UICONTROL Crea]** per creare la configurazione cloud per il servizio RESTful.

## Configurare i servizi Web SOAP {#configure-soap-web-services}

I servizi Web basati su SOAP sono descritti utilizzando le specifiche [WSDL (Web Services Description Language)](https://www.w3.org/TR/wsdl). Per configurare il servizio Web basato su SOAP in AEM Cloud Services, assicurati di disporre dell’URL WSDL per il servizio Web ed effettua le seguenti operazioni:

1. Vai a **[!UICONTROL Strumenti > Cloud Services > Origini dati]**. Tocca per selezionare la cartella in cui desideri creare una configurazione cloud.

   Per informazioni sulla creazione e la configurazione di una cartella per le configurazioni dei servizi cloud, consulta [Configurare la cartella per le configurazioni dei servizi cloud.](/help/forms/using/configure-data-sources.md#cloud-folder)

1. Tocca **[!UICONTROL Crea]** per aprire la finestra di dialogo **[!UICONTROL Crea configurazione origine dati]**. Specifica un nome ed eventualmente un titolo per la configurazione, seleziona **[!UICONTROL Servizio Web SOAP]** dal menu a discesa **[!UICONTROL Tipo di servizio]**, sfoglia facoltativamente e seleziona un&#39;immagine di miniatura per la configurazione, quindi tocca **[!UICONTROL Avanti]**.
1. Specifica quanto segue per il servizio Web SOAP:

   * URL WSDL per il servizio Web.
   * Endpoint servizio. Specificare un valore in questo campo per sostituire l&#39;endpoint del servizio menzionato in WSDL.
   * Seleziona il tipo di autenticazione: Nessuno, OAuth2.0, Autenticazione di base, Autenticazione personalizzata o Token X509 per accedere al servizio SOAP e, di conseguenza, fornisci i dettagli per l’autenticazione.

      Se selezioni X509 Token come tipo di autenticazione, configura il certificato X509. Per ulteriori informazioni, consulta [Configurare i certificati](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Specifica l&#39;alias KeyStore per il certificato X509 nel campo **[!UICONTROL Alias chiave]** . Specifica l&#39;ora, in secondi, fino a quando la richiesta di autenticazione non rimane valida, nel campo **[!UICONTROL Time To Live]** . Facoltativamente, seleziona per firmare il corpo del messaggio o l’intestazione della marca temporale o entrambe.

1. Tocca **[!UICONTROL Crea]** per creare la configurazione cloud per il servizio Web SOAP.

## Configurare i servizi OData {#config-odata}

Un servizio OData è identificato dall&#39;URL principale del servizio. Per configurare un servizio OData in AEM Cloud Services, accertati di disporre dell’URL principale del servizio e procedi come segue:

>[!NOTE]
>
>Per una guida dettagliata alla configurazione di Microsoft Dynamics 365, online o on-premise, consulta [Configurazione di Microsoft Dynamics OData](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Vai a **[!UICONTROL Strumenti > Cloud Services > Origini dati]**. Tocca per selezionare la cartella in cui desideri creare una configurazione cloud.

   Per informazioni sulla creazione e la configurazione di una cartella per le configurazioni dei servizi cloud, consulta [Configurare la cartella per le configurazioni dei servizi cloud.](/help/forms/using/configure-data-sources.md#cloud-folder)

1. Tocca **[!UICONTROL Crea]** per aprire la finestra di dialogo **[!UICONTROL Crea configurazione origine dati]**. Specifica un nome ed eventualmente un titolo per la configurazione, seleziona **[!UICONTROL Servizio OData]** dal menu a discesa **[!UICONTROL Tipo di servizio]**, se lo desideri, sfoglia e seleziona un&#39;immagine di miniatura per la configurazione, quindi tocca **[!UICONTROL Avanti]**.
1. Specifica i seguenti dettagli per il servizio OData:

   * URL principale del servizio per il servizio OData da configurare.
   * Seleziona il tipo di autenticazione (Nessuno, OAuth2.0, Autenticazione di base o Autenticazione personalizzata) per accedere al servizio OData e, di conseguenza, fornisci i dettagli per l’autenticazione.

   >[!NOTE]
   >
   >È necessario selezionare il tipo di autenticazione OAuth 2.0 per connettersi con Microsoft Dynamics Services utilizzando l’endpoint OData come radice del servizio.

1. Tocca **Crea** per creare la configurazione cloud per il servizio OData.

## Passaggi successivi {#next-steps}

Hai configurato le origini dati. Successivamente è possibile creare un modello dati modulo oppure, se è già stato creato un modello dati modulo senza un’origine dati, è possibile associarlo alle origini dati appena configurate. Per ulteriori informazioni, vedere [Creare un modello dati modulo](/help/forms/using/create-form-data-models.md) .
