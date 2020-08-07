---
title: Aggiornamento a AEM 6.4 Forms
seo-title: Aggiornamento a AEM 6.4 Forms
description: 'È possibile eseguire un aggiornamento diretto da Forms 6.1, Forms 6.2 e da Forms ES4 SP1 a AEM 6.3. '
seo-description: 'È possibile eseguire un aggiornamento diretto da Forms 6.1, Forms 6.2 e da Forms ES4 SP1 a AEM 6.3. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: ffa45c8fa98e1ebadd656ea58e4657b669ddd830
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---


# Aggiornamento a AEM 6.4 Forms su JEE {#upgrade-to-aem-forms-jee}

Utilizzate uno dei seguenti percorsi di aggiornamento, in base alle esigenze dell&#39;ambiente in uso.

## AEM 6.2 Forms su JEE o AEM Forms 6.3 su JEE > AEM 6.4 Forms su JEE {#aem-forms-jee-62-63-to-64}

Effettuate la seguente procedura per aggiornare l&#39;Forms AEM 6.2 esistente su JEE o AEM 6.3 su Forms JEE a AEM 6.4 Forms su JEE:

1. Scaricate l&#39;Forms AEM 6.4 sul programma di installazione JEE dal sito Web delle licenze del Adobe [(LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e assistenza valido.
1. Consulta [Elenco di controllo e pianificazione](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) dell&#39;aggiornamento per informazioni sui controlli da eseguire per garantire il successo dell&#39;aggiornamento.
1. Consultate [Preparazione all&#39;aggiornamento  AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) per apprendere ed eseguire le attività che garantiscono il corretto funzionamento dell&#39;aggiornamento con tempi di inattività ridotti del server.
1. A seconda dell’ambiente e del server applicazioni esistenti, scegliete uno dei seguenti documenti e seguite le istruzioni.

   * [Aggiornamento da AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms per JBoss](assets/upgrade-jboss.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms per WebLogic](assets/upgrade-weblogic.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms per JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms su JEE > AEM 6.3 Forms su JEE {#aem-forms-jee-60-to-63}

Non è disponibile l&#39;aggiornamento diretto da LiveCycle ES2, LiveCycle ES3, Forms 6.0, AEM Forms 6.1 a AEM 6.4 Forms. È possibile eseguire un aggiornamento intermedio a una o più versioni di AEM Forms  o LiveCycle e quindi effettuare l&#39;aggiornamento da AEM 6.4 Forms. Per l&#39;elenco delle versioni intermedie e le istruzioni di aggiornamento corrispondenti, consultate [Scegliere un percorso](upgrade.md)di aggiornamento.

## LiveCycle ES4 SP1 > AEM 6.4 Forms su JEE {#livecycle-es4sp1-forms-jee}

L&#39;aggiornamento dell&#39;LiveCycle ES4 SP1 a AEM 6.4 Forms su JEE è un aggiornamento obsoleto, in quanto comporta la migrazione di risorse e dati dalle versioni precedenti alle nuove istanze (nuove versioni) di server applicazioni, sistemi operativi e database supportati.

Di seguito viene fornita una panoramica della procedura per aggiornare un server ES4 SP1 esistente a AEM 6.4 Forms. Per istruzioni dettagliate, vedere i documenti elencati al termine della procedura.

1. Prima di effettuare l’aggiornamento:

   1. Scaricate l&#39;Forms AEM 6.4 sul programma di installazione JEE dal sito Web delle licenze del Adobe [(LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e assistenza valido.
   1. Decidete il tipo di repository del contenuto (repository CRX) da utilizzare. Solo poche  funzionalità AEM Forms su JEE utilizzano la persistenza dell&#39;archivio dei contenuti per memorizzare contenuti e risorse. Installate e configurate l&#39;archivio dei contenuti solo se prevedete di utilizzare tale  AEM Forms sulle funzionalità JEE:

      * In LiveCycle ES4 SP1, le funzionalità di gestione della corrispondenza, Forms Portal, HTML Workspace e Reporting dei processi utilizzano l&#39;archivio dei contenuti. Se non avete utilizzato queste funzionalità in LiveCycle ES4 e non intendete utilizzarle in  AEM Forms, l&#39;archivio dei contenuti non è richiesto.
      * In  AEM Forms, Forms adattivo, Gestione della corrispondenza, HTML5 Forms (noto come Forms mobile in LiveCycle ES4 SP1), Forms Portal, HTML Workspace, Process Reporting, flussi di lavoro Forms incentrati su OSGi, le funzionalità utilizzano Content Repository. Se intendete utilizzare  AEM Forms per queste funzionalità, è necessario Content Repository.
      * Non è necessario Content Repository per  AEM Forms Document Security.

      Inoltre, il tipo di LiveCycle del repository e  AEM Forms sono diversi. Per i tipi di repository disponibili e le relative informazioni, vedere [Scelta di un tipo di persistenza per un&#39;installazione](/help/forms/using/choosing-persistence-type-for-aem-forms.md)AEM Forms .

   1. Creare un backup dei contenuti e dei dati di LiveCycle ES4 SP1:

      Creare un backup del database di LiveCycle ES4 SP1, dell&#39;archivio dati globale (GDS) e del repository crx (non richiesto per la protezione dei documenti). Se state effettuando l’aggiornamento alla persistenza MongoMK o RDBMK, esportate le risorse per la gestione della corrispondenza del LiveCycle ES4 SP1 in un file .cmp e create le risorse come pacchetto AEM.

   1. Verificare che la piattaforma esistente (ovvero il server applicazioni, il database, il sistema operativo,  Adobe Acrobat, applicazioni di terze parti e l&#39;hardware) sia supportata per AEM Forms 6.4 su JEE. Per informazioni su hardware e software supportati, consultare il documento [Supportate Platform Combinations (Combinazioni](/help/forms/using/aem-forms-jee-supported-platforms.md) di piattaforme supportate).

      Se create una nuova istanza del database, importate nel database i dati di cui al punto 3. Per informazioni su come importare dati in un database, consultate la documentazione del fornitore di database corrispondente.

      >[!NOTE]
      >
      >Se si utilizza il formato di persistenza RDBMK, utilizzare un singolo database sia per la persistenza dell&#39;archivio che per i servizi documenti in esecuzione su  AEM Forms su JEE.


1. Eseguire l&#39;aggiornamento:

   1. Installate AEM 6.4 Forms su JEE su un nuovo server eseguendo il programma di installazione. Il programma di installazione inserisce tutti i file richiesti nel computer, all&#39;interno di una struttura di directory di installazione.
   1. Al termine dell&#39;installazione, eseguite **Configuration Manager** per configurare vari moduli AEM Forms  e impostare le configurazioni appropriate. Insieme alle impostazioni di configurazione, consente di specificare il percorso di Global Data Storage (GDS) e crx-repository.

      >[!NOTE]
      >
      >Nella schermata Aggiornamento selezione attività, selezionate l&#39;opzione **[!UICONTROL Aggiorna da  Adobe Experience Manager Forms 6.2.0]** . L&#39; **[!UICONTROL aggiornamento da  Adobe Experience Manager Forms 6.2.0]** consente al gestore di configurazione di effettuare l&#39;aggiornamento dal LiveCycle ES4 SP1 a AEM Forms 6.4.

   1. (Non richiesto per  modulo AEM Forms Document Security) Importare il contenuto nell&#39;archivio dei contenuti (CRX-Repository) AEM server Forms 6.4.

      >[!NOTE]
      >
      >* Dopo l&#39;aggiornamento dell&#39;archivio crx e la migrazione del contenuto, modificate la password dell&#39;account amministratore. Per istruzioni dettagliate, consultate [Modifica della password per un utente](/help/sites-administering/granite-user-group-admin.md)esistente.


1. Eseguire le operazioni post-distribuzione per verificare le credenziali di accesso, configurare document services, la gestione della corrispondenza, la protezione dei documenti e altro a seconda del caso d&#39;uso.
1. Verificare che il server sia stato aggiornato correttamente:

   Eseguire alcune operazioni di routine sul server AEM Forms aggiornato  per garantire che il server sia aggiornato correttamente. È possibile compilare e inviare alcuni moduli migrati o proteggere i documenti per garantire la corretta esecuzione dell&#39;aggiornamento.

   >[!NOTE]
   >
   >In Forms AEM 6.4, la struttura del repository crx è cambiata. Dopo aver effettuato l&#39;aggiornamento ai moduli AEM 6.4, utilizzare i percorsi modificati per la personalizzazione creati di nuovo. Per l&#39;elenco completo dei percorsi modificati, vedere Ristrutturazione archivio [Forms in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**A seconda dell’ambiente e del server applicazioni esistenti, scegliete uno dei seguenti documenti e seguite le istruzioni dettagliate:**

* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms per JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms per WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms per WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM Forms 6.4 tramite chiavi JBoss](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms su JEE {#livecycle-es3-forms-jee}

L&#39;aggiornamento dell&#39;LiveCycle ES3 a AEM 6.4 Forms su JEE è un aggiornamento obsoleto, in quanto comporta la migrazione di risorse e dati dalle versioni precedenti alle nuove istanze (nuove versioni) di server applicazioni, sistemi operativi e database supportati.

Di seguito viene fornita una panoramica della procedura per aggiornare un server LiveCycle ES3 esistente a AEM 6.4 Forms. Per istruzioni dettagliate, vedere i documenti elencati al termine della procedura.

1. Prima di effettuare l’aggiornamento:

   1. Scaricate l&#39;Forms AEM 6.4 sul programma di installazione JEE dal sito Web delle licenze del Adobe [(LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e assistenza valido.
   1. Decidete il tipo di repository del contenuto (repository CRX) da utilizzare. Solo poche  funzionalità AEM Forms su JEE utilizzano la persistenza dell&#39;archivio dei contenuti per memorizzare contenuti e risorse. Installate e configurate l&#39;archivio dei contenuti solo se prevedete di utilizzare tale  AEM Forms sulle funzionalità JEE:

      * In  AEM Forms, Forms adattivo, Gestione della corrispondenza, HTML5 Forms, Forms Portal, HTML Workspace, Process Reporting e flussi di lavoro Forms incentrati sulle funzionalità OSGi utilizzano Content Repository. Se intendete utilizzare  AEM Forms per queste funzionalità, è necessario Content Repository.
      * Non è necessario Content Repository per  AEM Forms Document Security.

      Inoltre, il tipo di LiveCycle del repository e  AEM Forms sono diversi. Per i tipi di repository disponibili e le relative informazioni, vedere [Scelta di un tipo di persistenza per un&#39;installazione](/help/forms/using/choosing-persistence-type-for-aem-forms.md)AEM Forms .

   1. Create un backup del database di LiveCycle ES3, dell&#39;archivio dati globale (GDS) e dell&#39;archivio dei contenuti (non richiesto per la protezione dei documenti). Se state effettuando l&#39;aggiornamento alla persistenza MongoMK o RDBMK, esportate le risorse di gestione della corrispondenza ES3 del LiveCycle come archivio.
   1. Verificare che la piattaforma esistente (ovvero il server applicazioni, il database, il sistema operativo,  Adobe Acrobat, applicazioni di terze parti e l&#39;hardware) sia supportata per AEM Forms 6.4 su JEE. Per informazioni su hardware e software supportati, consultare il documento [Supportate Platform Combinations (Combinazioni](/help/forms/using/aem-forms-jee-supported-platforms.md) di piattaforme supportate).

      Se create una nuova istanza del database, importate nel database i dati di cui al punto 3. Per informazioni su come importare dati in un database, consultate la documentazione del fornitore di database corrispondente.

      >[!NOTE]
      >
      >Se si utilizza il formato di persistenza RDBMK, utilizzare un singolo database sia per la persistenza dell&#39;archivio che per i servizi documenti in esecuzione su  AEM Forms su JEE.


1. Eseguire l&#39;aggiornamento:

   1. Installate AEM 6.4 Forms su JEE su un nuovo server eseguendo il programma di installazione. Il programma di installazione inserisce tutti i file richiesti nel computer, all&#39;interno di una struttura di directory di installazione.
   1. Al termine dell&#39;installazione, eseguite **Configuration Manager** per configurare vari moduli AEM Forms  e impostare le configurazioni appropriate. Insieme alle impostazioni di configurazione, consente di specificare il percorso di Global Data Storage (GDS) e crx-repository.

      >[!NOTE]
      >
      >Nella schermata Aggiornamento selezione attività, selezionate l&#39;opzione **[!UICONTROL Aggiorna da  Adobe Experience Manager Forms 6.2.0]** . L&#39; **[!UICONTROL opzione di aggiornamento da  Adobe Experience Manager Forms 6.2.0]** consente al gestore di configurazione di effettuare l&#39;aggiornamento dall&#39;LiveCycle ES3 a AEM Forms 6.4.

   1. (Non richiesto per  modulo AEM Forms Document Security) Aggiornare e importare l&#39;archivio CRX nel server Forms AEM 6.4.

      >[!NOTE]
      >
      >Dopo l&#39;aggiornamento dell&#39;archivio crx e la migrazione del contenuto, modificate la password dell&#39;account amministratore. Per istruzioni dettagliate, consultate [Modifica della password per un utente](/help/sites-administering/granite-user-group-admin.md)esistente.
1. Eseguire le operazioni post-distribuzione per verificare le credenziali di accesso, configurare document services, la gestione della corrispondenza, la protezione dei documenti e altro a seconda del caso d&#39;uso.
1. Verificare che il server sia stato aggiornato correttamente:

   Eseguire alcune operazioni di routine sul server AEM Forms aggiornato  per garantire che il server sia aggiornato correttamente. È possibile compilare e inviare alcuni moduli migrati o proteggere i documenti per garantire la corretta esecuzione dell&#39;aggiornamento.

   >[!NOTE]
   >
   >In Forms AEM 6.4, la struttura del repository crx è cambiata. Dopo aver effettuato l&#39;aggiornamento ai moduli AEM 6.4, utilizzare i percorsi modificati per la personalizzazione creati di nuovo. Per l&#39;elenco completo dei percorsi modificati, vedere Ristrutturazione archivio [Forms in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**A seconda dell’ambiente e del server applicazioni esistenti, scegliete uno dei seguenti documenti e seguite le istruzioni dettagliate:**

* [Aggiornamento dall&#39;LiveCycle ES3 a AEM Forms 6.4 per JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Aggiornamento dall&#39;LiveCycle ES3 a AEM 6.4 Forms per WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Aggiornamento dall&#39;LiveCycle ES3 a AEM 6.4 Forms per WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Aggiornamento dall&#39;LiveCycle ES3 a AEM Forms 6.4 tramite JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
