---
title: Integrazione con Salesforce
seo-title: Integrazione con Salesforce
description: Scopri come integrare AEM con Salesforce.
seo-description: Scopri come integrare AEM con Salesforce.
uuid: db3b25f3-b680-4054-a8db-4161d4c86201
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b9752c60-eb26-4840-9163-a99537a58727
translation-type: tm+mt
source-git-commit: 7dc90299b7a0e5166c30702323f1678353fe39b3
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 3%

---


# Integrazione con Salesforce{#integrating-with-salesforce}

L&#39;integrazione di Salesforce con AEM fornisce funzionalità di gestione dei lead e sfrutta le capacità già esistenti fornite da Salesforce. Puoi configurare AEM per pubblicare i lead su Salesforce e creare componenti che accedono direttamente ai dati da Salesforce.

L&#39;integrazione bidirezionale ed estensibile tra AEM e Salesforce consente:

* Organizzazioni per utilizzare e aggiornare completamente i dati per migliorare l&#39;esperienza del cliente.
* Coinvolgimento dal marketing alle attività di vendita.
* Organizzazioni per trasmettere e ricevere automaticamente i dati da un archivio dati Salesforce.

Il presente documento descrive quanto segue:

* come configurare Cloud Services Salesforce (configurare AEM da integrare con Salesforce).
* come utilizzare le informazioni di contatto/lead Salesforce in ClientContext e per la personalizzazione.
* come utilizzare il modello di flusso di lavoro Salesforce per pubblicare gli utenti AEM come lead a Salesforce.
* come creare un componente che mostri i dati da Salesforce.

## Configurazione di AEM da integrare con Salesforce {#configuring-aem-to-integrate-with-salesforce}

Per configurare AEM da integrare con Salesforce, devi prima configurare un’applicazione di accesso remoto in Salesforce. Quindi configuri il servizio cloud Salesforce per puntare a questa applicazione di accesso remoto.

>[!NOTE]
>
>Puoi creare un account sviluppatore gratuito in Salesforce.

Per configurare AEM da integrare con Salesforce:

1. In AEM, andate ai **Cloud Services**. In Servizi di terze parti, fai clic su **Configura ora** in **Salesforce**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Create una nuova configurazione, ad esempio **sviluppatore**.

   >[!NOTE]
   >
   >La nuova configurazione reindirizza a una nuova pagina: **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Si tratta dello stesso valore che è necessario specificare nell’URL di callback durante la creazione dell’applicazione di accesso remoto in Salesforce. Questi valori devono corrispondere.

1. Accedi al tuo account di vendita (o, se non ne hai uno, creane uno all&#39;indirizzo [https://developer.force.com](https://developer.force.com).)
1. In Salesforce, passa a **Crea** > **App** per accedere alle app **** collegate (nelle versioni precedenti di Salesforce, il flusso di lavoro era **Distribuisci** > Accesso **** remoto).
1. Fai clic su **Nuovo** per collegare AEM con Salesforce.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Immettete il Nome **app** connesso, il Nome **** API e l&#39;E-mail **di** contatto. Selezionate la casella di controllo **Abilita impostazioni** OAuth e immettete l’URL **per il** callback, quindi aggiungete un ambito OAuth (ad esempio, accesso completo). L’URL di callback è simile al seguente: `http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   Modificate il nome del server, il numero della porta e il nome della pagina in modo che corrisponda alla configurazione.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. Fai clic su **Salva** per salvare la configurazione di Salesforce. Salesforce crea una chiave **di** consumo e un segreto **per** il consumatore, necessari per AEM configurazione.

   ![chlimage_1-87](assets/chlimage_1-87.png)

   >[!NOTE]
   >
   >Potrebbe essere necessario attendere alcuni minuti (fino a 15 minuti) per attivare l’applicazione di accesso remoto in Salesforce.

1. In AEM, andate agli **Cloud Services** e andate alla configurazione di salesforce creata in precedenza (ad esempio, **sviluppatore**). Fai clic su **Modifica** e immetti la chiave cliente e il segreto cliente da salesforce.com.

   ![chlimage_1-23](assets/chlimage_1-23.jpeg)

   | Url di accesso | Questo è l&#39;endpoint di autorizzazione di Salesforce. Il suo valore è precompilato e serve la maggior parte dei casi. |
   |---|---|
   | Chiave cliente | Immettete il valore ottenuto dalla pagina Registrazione dell&#39;applicazione di accesso remoto in salesforce.com |
   | Segreto cliente | Immettete il valore ottenuto dalla pagina Registrazione dell&#39;applicazione di accesso remoto in salesforce.com |

1. Fate clic su **Connetti a Salesforce** per connettersi. Salesforce richiede che la configurazione sia connessa a Salesforce.

   ![chlimage_1-88](assets/chlimage_1-88.png)

   In AEM viene visualizzata una finestra di dialogo di conferma in cui viene indicato che la connessione è stata completata.

1. Andate alla pagina principale del sito Web e fate clic su Proprietà **** pagina. Quindi seleziona **Cloud Services** e aggiungi **Salesforce** , quindi seleziona la configurazione corretta (ad esempio, **sviluppatore**).

   ![chlimage_1-89](assets/chlimage_1-89.png)

   Ora puoi usare il modello di workflow per pubblicare i lead su Salesforce e creare componenti che accedono ai dati da Salesforce.

## Esportazione AEM utenti come lead Salesforce {#exporting-aem-users-as-salesforce-leads}

Se desiderate esportare un utente AEM come lead di Salesforce, dovete configurare il flusso di lavoro per pubblicare i lead a Salesforce.

Per esportare AEM utenti come lead Salesforce:

1. Andate al flusso di lavoro Salesforce `http://localhost:4502/workflow` facendo clic con il pulsante destro del mouse sul flusso di lavoro **Salesforce.com Export** e facendo clic su **Start**.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Selezionate l’utente AEM che desiderate creare come lead come **payload** per questo flusso di lavoro (home -> utenti). Assicurati di selezionare il nodo del profilo dell&#39;utente, in quanto contiene informazioni come **givenName**, **familyName** e così via, mappate sui campi **FirstName** e **LastName** del lead Salesforce.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >Prima di avviare questo flusso di lavoro, è necessario che un nodo lead in AEM disponga di alcuni campi obbligatori prima di essere pubblicato in Salesforce. Questi sono **datiName**, **familyName**, **** companyName ed **email**. Per visualizzare un elenco completo della mappatura tra AEM utente e il lead Salesforce, vedi Configurazione della [mappatura tra AEM utente e il lead Slaesforce.](#mapping-configuration-between-aem-user-and-salesforce-lead)

1. Fai clic su **OK**. Le informazioni utente vengono esportate in salesforce.com. Potete verificarlo su salesforce.com.

   >[!NOTE]
   >
   >I registri errori mostrano se un lead viene importato. Per ulteriori informazioni, controllare il registro degli errori.

### Configurazione del flusso di lavoro di esportazione Salesforce.com {#configuring-the-salesforce-com-export-workflow}

Potrebbe essere necessario configurare il flusso di lavoro di esportazione Salesforce.com in modo che corrisponda alla configurazione Salesforce.com corretta o per apportare altre modifiche.

Per configurare il flusso di lavoro di esportazione Salesforce.com:

1. Accedi a `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`

   ![chlimage_1-24](assets/chlimage_1-24.jpeg)

1. Aprite il passaggio Salesforce.com Export, selezionate la scheda **Argomenti** , selezionate la configurazione corretta e fate clic su **OK**. Inoltre, se desiderate che il flusso di lavoro ricrei un lead eliminato in Salesforce, selezionate la casella di controllo.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Click **Save** to save your changes.

   ![chlimage_1-93](assets/chlimage_1-93.png)

### Mappatura della configurazione tra AEM utente e il lead Salesforce {#mapping-configuration-between-aem-user-and-salesforce-lead}

Per visualizzare o modificare la configurazione di mappatura corrente tra un utente AEM e un lead Salesforce, apri Gestione configurazione: `https://<hostname>:<port>/system/console/configMgr` e cerca la configurazione **Mappatura lead** Salesforce.

1. Aprire Gestione configurazione facendo clic su Console **** Web o andando direttamente a `https://<hostname>:<port>/system/console/configMgr.`
1. Cerca configurazione **mappatura lead** Salesforce.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Modificate le mappature, come necessario. La mappatura predefinita segue il pattern** aemUserAttribute=sfLeadAttribute**. Click **Save** to save your changes.

## Configurazione dell&#39;archivio contestuale del client Salesforce {#configuring-salesforce-client-context-store}

L&#39;archivio contestuale del client Salesforce mostra informazioni aggiuntive sull&#39;utente attualmente connesso rispetto a quanto è già disponibile all&#39;interno di AEM. Richiama queste informazioni aggiuntive da Salesforce a seconda della connessione dell&#39;utente con Salesforce.

A questo scopo, è necessario configurare quanto segue:

1. Collegate un utente AEM con un ID Salesforce tramite il componente Salesforce Connect.
1. Aggiungi i dati del profilo Salesforce nella pagina del contesto del client per configurare le proprietà che desideri visualizzare.
1. (Facoltativo) Crea un segmento che utilizza i dati dallo store Client Context di Salesforce.

### Collegamento di un utente AEM con un ID Salesforce {#linking-an-aem-user-with-a-salesforce-id}

Devi mappare un utente AEM con un ID Salesforce per caricarlo nel contesto client. In uno scenario reale, il collegamento si basa su dati utente noti con la convalida. A scopo dimostrativo, in questa procedura viene utilizzato il componente **Salesforce Connect** .

1. Andate a un sito Web in AEM, accedete e trascinate il componente **Salesforce Connect** dalla barra laterale.

   >[!NOTE]
   >
   >Se il componente **Salesforce Connect** non è disponibile, andate alla visualizzazione **Struttura** e selezionatelo per renderlo disponibile nella visualizzazione **Modifica** .

   ![chlimage_1-25](assets/chlimage_1-25.jpeg)

   Quando trascinate il componente sulla pagina, viene visualizzato **Collega a Salesforce=Disattivato**.

   ![chlimage_1-95](assets/chlimage_1-95.png)

   >[!NOTE]
   >
   >Questo componente è solo a scopo dimostrativo. Per gli scenari reali, ci sarebbe un altro processo per collegare/far corrispondere gli utenti con i lead.

1. Dopo aver trascinato il componente sulla pagina, apritelo per configurarlo. Seleziona la configurazione, il tipo di contatto e il lead o il contatto Salesforce, quindi fai clic su **OK**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   AEM collega l’utente con il contatto Salesforce o il lead.

   ![chlimage_1-97](assets/chlimage_1-97.png)

### Aggiunta di dati Salesforce a ClientContext {#adding-salesforce-data-to-client-context}

Puoi caricare i dati utente da Salesforce nel ClientContext per utilizzarli per la personalizzazione:

1. Aprite il contesto client da estendere, ad esempio, navigando in tale posizione `http://localhost:4502/etc/clientcontext/default/content.html.`

   ![chlimage_1-26](assets/chlimage_1-26.jpeg)

1. Trascina il componente Dati **profilo di** Salesforce nel contesto client.

   ![chlimage_1-27](assets/chlimage_1-27.jpeg)

1. Fate doppio clic sul componente per aprirlo. Selezionare **Aggiungi elemento** e selezionare una proprietà dall&#39;elenco a discesa. Aggiungete tutte le proprietà desiderate e selezionate **OK**.

   ![chlimage_1-98](assets/chlimage_1-98.png)

1. Ora vengono visualizzate le proprietà specifiche di Salesforce di Salesforce nel contesto client.

   ![chlimage_1-99](assets/chlimage_1-99.png)

### Creazione di un segmento utilizzando i dati dallo store Client Context di Salesforce {#building-a-segment-using-data-from-salesforce-client-context-store}

Puoi creare un segmento che utilizza i dati dall&#39;archivio di contesto client Salesforce. Per effettuare ciò:

1. Andate alla segmentazione in AEM da **Strumenti** > **Segmentazione** oppure da [http://localhost:4502/miscadmin#/etc/segmentation](Http://localhost:4502/miscadmin#/etc/segmentation).
1. Crea o aggiorna un segmento per includere dati da Salesforce. For more information, see [Segmentation](/help/sites-administering/campaign-segmentation.md).

## Ricerca di lead {#searching-leads}

AEM viene fornito con un componente Ricerca di esempio che esegue la ricerca dei lead in Salesforce in base ai criteri specificati. Questo componente mostra come utilizzare l’API REST di Salesforce per cercare oggetti Salesforce. Devi collegare una pagina con una configurazione Salesforce per avviare una chiamata a salesforce.com.

>[!NOTE]
>
>Questo è un componente di esempio che mostra come utilizzare l&#39;API REST di Salesforce per eseguire query sugli oggetti Salesforce. Utilizzatelo come esempio per creare componenti più complessi in base alle vostre esigenze.

Per utilizzare questo componente:

1. Passate alla pagina in cui desiderate utilizzare questa configurazione. Aprite le proprietà della pagina e selezionate **Cloud Services.** Fai clic su **Aggiungi servizi** , seleziona **Salesforce** e la configurazione appropriata, quindi fai clic su **OK**.

   ![chlimage_1-28](assets/chlimage_1-28.jpeg)

1. Trascina il componente di ricerca Salesforce sulla pagina (purché sia stato abilitato. Per attivarla, passate alla modalità Progettazione e aggiungetela all&#39;area appropriata.

   ![chlimage_1-29](assets/chlimage_1-29.jpeg)

1. Aprite il componente Ricerca e specificate i parametri di ricerca e fate clic su **OK.**

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. AEM visualizza i lead specificati nel componente di ricerca che corrispondono ai criteri specificati.

   ![chlimage_1-101](assets/chlimage_1-101.png)

