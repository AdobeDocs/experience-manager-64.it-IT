---
title: Aggiornamento ad AEM 6.4 Forms
seo-title: Aggiornamento ad AEM 6.4 Forms
description: 'È possibile eseguire un aggiornamento diretto da Forms 6.1, Forms 6.2 AEM e LiveCycle ES4 SP1 a Forms 6.3. '
seo-description: 'È possibile eseguire un aggiornamento diretto da Forms 6.1, Forms 6.2 AEM e LiveCycle ES4 SP1 a Forms 6.3. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: e41eb0fa-ae88-44d5-9181-0d925b8b62c6
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---

# Aggiornamento a AEM 6.4 Forms su JEE {#upgrade-to-aem-forms-jee}

Utilizza uno dei seguenti percorsi di aggiornamento, in base alle esigenze del tuo ambiente.

## AEM 6.2 Forms su JEE o AEM 6.3 Forms su JEE > AEM 6.4 Forms su JEE {#aem-forms-jee-62-63-to-64}

Esegui la seguente procedura per aggiornare AEM 6.2 Forms esistente su JEE o AEM 6.3 Forms su JEE a AEM 6.4 Forms su JEE:

1. Scarica il programma di installazione di Forms 6.4 AEM su JEE dal sito Web [Adobe Licensing (LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e supporto valido.
1. Per informazioni sui controlli da eseguire per garantire il successo dell&#39;aggiornamento, consulta [Lista di controllo per l&#39;aggiornamento e la pianificazione](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) .
1. Consulta [Prepare to upgrade to AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) per scoprire ed eseguire le attività che garantiscono che l&#39;aggiornamento venga eseguito correttamente con tempi di inattività del server minimi.
1. A seconda dell&#39;ambiente e del server applicazioni esistenti, scegli uno dei seguenti documenti e segui le istruzioni.

   * [Aggiornamento da AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms per JBoss](assets/upgrade-jboss.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms per WebLogic](assets/upgrade-weblogic.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms per WebSphere](assets/upgrade-websphere.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms per JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms su JEE > AEM 6.3 Forms su JEE {#aem-forms-jee-60-to-63}

Non è disponibile l&#39;aggiornamento diretto da LiveCycle ES2, LiveCycle ES3, Forms 6.0, AEM 6.1 Forms a AEM 6.4 Forms. Puoi eseguire un aggiornamento intermedio a una o più versioni di LiveCycle o AEM Forms e quindi eseguire l’aggiornamento da Forms 6.4 AEM. Per l&#39;elenco delle versioni intermedie e delle relative istruzioni di aggiornamento, consulta [Scegliere un percorso di aggiornamento](upgrade.md).

## LiveCycle ES4 SP1 > AEM 6.4 Forms su JEE {#livecycle-es4sp1-forms-jee}

L&#39;aggiornamento del LiveCycle ES4 SP1 a AEM 6.4 Forms su JEE è un aggiornamento out-of-place, in quanto comporta la migrazione di risorse e dati dalle versioni precedenti alle nuove istanze (nuove versioni) dei server applicativi, dei sistemi operativi e dei database supportati.

Di seguito è riportata una panoramica della procedura per aggiornare un server LiveCycle ES4 SP1 esistente a AEM 6.4 Forms. Per istruzioni dettagliate, vedere i documenti elencati al termine della procedura.

1. Prima dell’aggiornamento:

   1. Scarica il programma di installazione di Forms 6.4 AEM su JEE dal sito Web [Adobe Licensing (LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e supporto valido.
   1. Decidi il tipo di archivio dei contenuti (CRX Repository) da utilizzare. Solo poche funzionalità di AEM Forms su JEE utilizzano la persistenza dell’archivio dei contenuti per memorizzare contenuti e risorse. Installa e configura l’archivio dei contenuti solo se intendi utilizzare tali funzionalità di AEM Forms su JEE:

      * Nel LiveCycle ES4 SP1, le funzionalità di gestione delle corrispondenze, Forms Portal, HTML Workspace e reporting dei processi utilizzano l’archivio dei contenuti. Se non hai utilizzato queste funzionalità nel LiveCycle ES4 e hai intenzione di non utilizzarle in AEM Forms, non è necessario l’archivio dei contenuti.
      * In AEM Forms, Adaptive Forms, Gestione Corrispondenza, HTML5 Forms (noto come Forms mobile nel LiveCycle ES4 SP1), Forms Portal, HTML Workspace, Process Reporting, flussi di lavoro incentrati su Forms su OSGi, le funzionalità utilizzano Content Repository. Se prevedi di utilizzare AEM Forms per queste funzionalità, è necessario Content Repository.
      * Non è necessario Content Repository per AEM Forms Document Security.

      Inoltre, il tipo di archivio di LiveCycle e AEM Forms sono diversi. Per i tipi di archivio disponibili e le relative informazioni, consulta [Scelta di un tipo di persistenza per un&#39;installazione di AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Creare un backup dei contenuti e dei dati del LiveCycle ES4 SP1:

      Crea un backup del database LiveCycle ES4 SP1, Global Data Storage (GDS) e del repository crx (non necessario per la sicurezza dei documenti). Se stai eseguendo l&#39;aggiornamento alla persistenza MongoMK o RDBMK, esporta le risorse di gestione della corrispondenza del LiveCycle ES4 SP1 in un file .cmp e crea le risorse come pacchetto AEM.

   1. Assicurati che la piattaforma esistente (ovvero server applicazioni, database, sistema operativo, Adobe Acrobat, applicazioni di terze parti e hardware) sia supportata per Forms AEM 6.4 su JEE. Per informazioni sull&#39;hardware e il software supportati, consulta il documento [Combinazioni di piattaforme supportate](/help/forms/using/aem-forms-jee-supported-platforms.md) .

      Se si crea una nuova istanza del database, importare nel database i dati di cui al passaggio 3. Per informazioni su come importare dati in un database, vedere la documentazione del fornitore del database corrispondente.

      >[!NOTE]
      >
      >Se si utilizza il formato di persistenza RDBMK, utilizzare un singolo database sia per la persistenza dell&#39;archivio che per i servizi documenti in esecuzione su AEM Forms su JEE.


1. Esegui l&#39;aggiornamento:

   1. Installa AEM 6.4 Forms su JEE su un nuovo server eseguendo il programma di installazione. Il programma di installazione inserisce tutti i file richiesti sul computer, all&#39;interno di una struttura di directory di installazione.
   1. Al termine dell&#39;installazione, esegui **Configuration Manager** per configurare vari moduli AEM Forms e impostare le configurazioni appropriate. Insieme alla configurazione delle impostazioni, consente di specificare il percorso di Global Data Storage (GDS) e crx-repository.

      >[!NOTE]
      >
      >Nella schermata Selezione attività di aggiornamento , seleziona l’opzione **[!UICONTROL Aggiornamento da Adobe Experience Manager Forms 6.2.0]** . L&#39;opzione **[!UICONTROL Aggiornamento da Adobe Experience Manager Forms 6.2.0]** consente al gestore della configurazione di eseguire l&#39;aggiornamento da LiveCycle ES4 SP1 a Forms 6.4.

   1. (Non richiesto per il modulo di sicurezza dei documenti AEM Forms) Importa contenuto nell&#39;archivio dei contenuti (CRX-Repository) AEM server Forms 6.4.

      >[!NOTE]
      >
      >* Dopo l&#39;aggiornamento dell&#39;archivio crx e la migrazione del contenuto, cambia la password dell&#39;account amministratore. Per istruzioni dettagliate, vedere [Modifica della password per un utente esistente](/help/sites-administering/granite-user-group-admin.md).


1. Esegui le attività successive alla distribuzione per verificare le credenziali di accesso, configurare document services, gestione della corrispondenza, protezione dei documenti e altro a seconda del caso d’uso.
1. Verifica che il server sia stato aggiornato correttamente:

   Esegui alcune operazioni di routine sul server AEM Forms aggiornato per verificare che il server sia aggiornato correttamente. È possibile compilare e inviare alcuni moduli migrati o proteggere i documenti per garantire la riuscita dell’aggiornamento.

   >[!NOTE]
   >
   >In Forms 6.4 AEM, la struttura di crx-repository è cambiata. Dopo aver effettuato l’aggiornamento a AEM moduli 6.4, utilizza i percorsi modificati per la personalizzazione che hai creato nuovamente. Per l’elenco completo dei percorsi modificati, consulta [Ristrutturazione dell’archivio Forms in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**A seconda dell&#39;ambiente e del server applicazioni esistenti, scegli uno dei seguenti documenti e segui le istruzioni dettagliate:**

* [Aggiornamento da LiveCycle ES4 SP1 a Forms 6.4 per JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms per WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM Forms 6.4 utilizzando JBoss Turnkey](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms su JEE {#livecycle-es3-forms-jee}

L&#39;aggiornamento del LiveCycle ES3 a AEM 6.4 Forms su JEE è un aggiornamento fuori sede, in quanto comporta la migrazione di risorse e dati dalle versioni precedenti alle nuove istanze (nuove versioni) dei server applicativi, dei sistemi operativi e dei database supportati.

Di seguito è riportata una panoramica della procedura per aggiornare un server ES3 di LiveCycle esistente a Forms 6.4 AEM. Per istruzioni dettagliate, vedere i documenti elencati al termine della procedura.

1. Prima dell’aggiornamento:

   1. Scarica il programma di installazione di Forms 6.4 AEM su JEE dal sito Web [Adobe Licensing (LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e supporto valido.
   1. Decidi il tipo di archivio dei contenuti (CRX Repository) da utilizzare. Solo poche funzionalità di AEM Forms su JEE utilizzano la persistenza dell’archivio dei contenuti per memorizzare contenuti e risorse. Installa e configura l’archivio dei contenuti solo se intendi utilizzare tali funzionalità di AEM Forms su JEE:

      * In AEM Forms, Adaptive Forms, Gestione Corrispondenza, HTML5 Forms, Forms Portal, HTML Workspace, Process Reporting e flussi di lavoro incentrati su Forms sulle funzionalità OSGi utilizzano l’archivio dei contenuti. Se prevedi di utilizzare AEM Forms per queste funzionalità, è necessario Content Repository.
      * Non è necessario Content Repository per AEM Forms Document Security.

      Inoltre, il tipo di archivio di LiveCycle e AEM Forms sono diversi. Per i tipi di archivio disponibili e le relative informazioni, consulta [Scelta di un tipo di persistenza per un&#39;installazione di AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Crea un backup del database LiveCycle ES3, dell&#39;archivio dati globale (GDS) e del repository dei contenuti (non necessario per la sicurezza dei documenti). Se stai effettuando l&#39;aggiornamento alla persistenza MongoMK o RDBMK, esporta le risorse di gestione della corrispondenza ES3 del LiveCycle come archivio.
   1. Assicurati che la piattaforma esistente (ovvero server applicazioni, database, sistema operativo, Adobe Acrobat, applicazioni di terze parti e hardware) sia supportata per Forms AEM 6.4 su JEE. Per informazioni sull&#39;hardware e il software supportati, consulta il documento [Combinazioni di piattaforme supportate](/help/forms/using/aem-forms-jee-supported-platforms.md) .

      Se si crea una nuova istanza del database, importare nel database i dati di cui al passaggio 3. Per informazioni su come importare dati in un database, vedere la documentazione del fornitore del database corrispondente.

      >[!NOTE]
      >
      >Se si utilizza il formato di persistenza RDBMK, utilizzare un singolo database sia per la persistenza dell&#39;archivio che per i servizi documenti in esecuzione su AEM Forms su JEE.


1. Esegui l&#39;aggiornamento:

   1. Installa AEM 6.4 Forms su JEE su un nuovo server eseguendo il programma di installazione. Il programma di installazione inserisce tutti i file richiesti sul computer, all&#39;interno di una struttura di directory di installazione.
   1. Al termine dell&#39;installazione, esegui **Configuration Manager** per configurare vari moduli AEM Forms e impostare le configurazioni appropriate. Insieme alla configurazione delle impostazioni, consente di specificare il percorso di Global Data Storage (GDS) e crx-repository.

      >[!NOTE]
      >
      >Nella schermata Selezione attività di aggiornamento , seleziona l’opzione **[!UICONTROL Aggiornamento da Adobe Experience Manager Forms 6.2.0]** . L&#39;opzione **[!UICONTROL Aggiornamento da Adobe Experience Manager Forms 6.2.0]** consente al gestore della configurazione di eseguire l&#39;aggiornamento da LiveCycle ES3 a AEM Forms 6.4.

   1. (Non richiesto per il modulo di sicurezza dei documenti AEM Forms) Aggiorna e importa l&#39;archivio CRX sul server Forms 6.4 AEM.

      >[!NOTE]
      >
      >Dopo l&#39;aggiornamento dell&#39;archivio crx e la migrazione del contenuto, cambia la password dell&#39;account amministratore. Per istruzioni dettagliate, vedere [Modifica della password per un utente esistente](/help/sites-administering/granite-user-group-admin.md).
1. Esegui le attività successive alla distribuzione per verificare le credenziali di accesso, configurare document services, gestione della corrispondenza, protezione dei documenti e altro a seconda del caso d’uso.
1. Verifica che il server sia stato aggiornato correttamente:

   Esegui alcune operazioni di routine sul server AEM Forms aggiornato per verificare che il server sia aggiornato correttamente. È possibile compilare e inviare alcuni moduli migrati o proteggere i documenti per garantire la riuscita dell’aggiornamento.

   >[!NOTE]
   >
   >In Forms 6.4 AEM, la struttura di crx-repository è cambiata. Dopo aver effettuato l’aggiornamento a AEM moduli 6.4, utilizza i percorsi modificati per la personalizzazione che hai creato nuovamente. Per l’elenco completo dei percorsi modificati, consulta [Ristrutturazione dell’archivio Forms in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**A seconda dell&#39;ambiente e del server applicazioni esistenti, scegli uno dei seguenti documenti e segui le istruzioni dettagliate:**

* [Aggiornamento da LiveCycle ES3 a AEM 6.4 Forms per JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Aggiornamento da LiveCycle ES3 a AEM 6.4 Forms per WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Aggiornamento da LiveCycle ES3 a AEM 6.4 Forms per WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Aggiornamento da LiveCycle ES3 a Forms 6.4 AEM utilizzando JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
