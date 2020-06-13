---
title: Aggiornamento ad AEM 6.4 Forms
seo-title: Aggiornamento ad AEM 6.4 Forms
description: 'È possibile eseguire un aggiornamento diretto da AEM 6.1 Forms, AEM 6.2 Forms e LiveCycle ES4 SP1 a AEM 6.3 Forms. '
seo-description: 'È possibile eseguire un aggiornamento diretto da AEM 6.1 Forms, AEM 6.2 Forms e LiveCycle ES4 SP1 a AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: f234d368163f4260563d69230a2cbda37b6d315a
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---


# Aggiornamento ad AEM 6.4 Forms su JEE {#upgrade-to-aem-forms-jee}

Utilizzate uno dei seguenti percorsi di aggiornamento, in base alle esigenze dell&#39;ambiente in uso.

## Moduli AEM 6.2 su JEE o moduli AEM 6.3 su JEE > AEM 6.4 Forms su JEE {#aem-forms-jee-62-63-to-64}

Per aggiornare i moduli AEM 6.2 esistenti su JEE o AEM 6.3 su JEE ai moduli AEM 6.4 su JEE, procedi come segue:

1. Scaricate il programma di installazione AEM 6.4 Forms on JEE dal sito Web delle licenze [Adobe (LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e assistenza valido.
1. Consulta [Elenco di controllo e pianificazione](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) dell&#39;aggiornamento per informazioni sui controlli da eseguire per garantire il successo dell&#39;aggiornamento.
1. Consultate [Preparazione all’aggiornamento ad AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) per apprendere ed eseguire le attività che garantiscono il corretto funzionamento dell’aggiornamento con tempi di inattività del server ridotti.
1. A seconda dell’ambiente e del server applicazioni esistenti, scegliete uno dei seguenti documenti e seguite le istruzioni.

   * [Aggiornamento da AEM 6.2 o AEM 6.3 a AEM 6.4 Forms for JBoss](assets/upgrade-jboss.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 a AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 a AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [Aggiornamento da AEM 6.2 o AEM 6.3 a AEM 6.4 Forms for JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms on JEE > AEM 6.3 Forms on JEE {#aem-forms-jee-60-to-63}

L&#39;aggiornamento diretto da LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms a AEM 6.4 Forms non è disponibile. È possibile eseguire un aggiornamento intermedio a una o più versioni di LiveCycle o AEM Forms, quindi effettuare l&#39;aggiornamento da AEM 6.4 Forms. Per l&#39;elenco delle versioni intermedie e le istruzioni di aggiornamento corrispondenti, consultate [Scegliere un percorso](upgrade.md)di aggiornamento.

## LiveCycle ES4 SP1 > AEM 6.4 Forms on JEE {#livecycle-es4sp1-forms-jee}

L&#39;aggiornamento di LiveCycle ES4 SP1 ad AEM 6.4 Forms su JEE è un aggiornamento non aggiornato, in quanto comporta la migrazione di risorse e dati dalle versioni precedenti alle nuove istanze (nuove versioni) di server applicazione, sistemi operativi e database supportati.

Di seguito viene fornita una panoramica della procedura per aggiornare un server LiveCycle ES4 SP1 esistente a AEM 6.4 Forms. Per istruzioni dettagliate, vedere i documenti elencati al termine della procedura.

1. Prima di effettuare l’aggiornamento:

   1. Scaricate il programma di installazione AEM 6.4 Forms on JEE dal sito Web delle licenze [Adobe (LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e assistenza valido.
   1. Decidete il tipo di repository del contenuto (repository CRX) da utilizzare. Solo alcuni moduli AEM su funzionalità JEE utilizzano la persistenza dell&#39;archivio dei contenuti per memorizzare contenuto e risorse. Installate e configurate l&#39;archivio dei contenuti solo se intendete utilizzare tali moduli AEM su funzionalità JEE:

      * In LiveCycle ES4 SP1, le funzionalità Correspondence Management, Forms Portal, HTML Workspace e Process Reporting utilizzano l&#39;archivio dei contenuti. Se non avete utilizzato queste funzionalità in LiveCycle ES4 e non intendete utilizzarle in AEM Forms, l&#39;archivio dei contenuti non è obbligatorio.
      * In AEM Forms, Moduli adattivi, Gestione della corrispondenza, Moduli HTML5 (noti come Moduli mobili in LiveCycle ES4 SP1), Portale moduli, Area di lavoro HTML, Generazione dei rapporti sui processi, Flussi di lavoro incentrati sui moduli in OSGi, le funzionalità utilizzano l&#39;archivio dei contenuti. Se si intende utilizzare AEM Forms per queste funzionalità, è necessario l&#39;archivio dei contenuti.
      * Non è necessario Content Repository per AEM Forms Document Security.
      Inoltre, il tipo di archivio di LiveCycle e AEM Forms è diverso. Per i tipi di archivio disponibili e le relative informazioni, consultate [Scelta di un tipo di persistenza per un&#39;installazione](/help/forms/using/choosing-persistence-type-for-aem-forms.md)di AEM Forms.

   1. Creare un backup dei contenuti e dei dati di LiveCycle ES4 SP1:

      Creare un backup del database LiveCycle ES4 SP1, dell&#39;archivio dati globale (GDS) e del repository crx (non richiesto per la protezione dei documenti). Se state effettuando l&#39;aggiornamento alla persistenza MongoMK o RDBMK, esportate le risorse per la gestione della corrispondenza di LiveCycle ES4 SP1 in un file .cmp e create le risorse come pacchetto AEM.

   1. Verifica che la piattaforma esistente (ovvero il server applicazioni, il database, il sistema operativo, Adobe Acrobat, le applicazioni di terze parti e l&#39;hardware) sia supportata per AEM 6.4 Forms on JEE. Per informazioni su hardware e software supportati, consultare il documento [Supportate Platform Combinations (Combinazioni](/help/forms/using/aem-forms-jee-supported-platforms.md) di piattaforme supportate).

      Se create una nuova istanza del database, importate nel database i dati di cui al punto 3. Per informazioni su come importare dati in un database, consultate la documentazione del fornitore di database corrispondente.

      >[!NOTE]
      >
      >Se si utilizza il formato di persistenza RDBMK, utilizzare un singolo database sia per la persistenza dell&#39;archivio che per i servizi basati su documenti in esecuzione su AEM Forms su JEE.


1. Eseguire l&#39;aggiornamento:

   1. Installa AEM 6.4 Forms su JEE su un nuovo server eseguendo il programma di installazione. Il programma di installazione inserisce tutti i file richiesti nel computer, all&#39;interno di una struttura di directory di installazione.
   1. Al termine dell&#39;installazione, eseguite **Configuration Manager** per configurare vari moduli AEM Forms e impostare le configurazioni appropriate. Insieme alle impostazioni di configurazione, consente di specificare il percorso di Global Data Storage (GDS) e crx-repository.

      >[!NOTE]
      >
      >Nella schermata Aggiornamento selezione attività, selezionate l&#39;opzione **[!UICONTROL Aggiorna da Adobe Experience Manager Forms 6.2.0]** . L’opzione **[!UICONTROL Aggiorna da Adobe Experience Manager Forms 6.2.0]** consente al gestore di configurazione di effettuare l’aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms.

   1. (Non richiesto per il modulo di protezione dei documenti AEM Forms) Importa contenuto nell’archivio dei contenuti (CRX-Repository) nel server AEM 6.4 Forms.

      >[!NOTE]
      >
      >* Dopo l&#39;aggiornamento dell&#39;archivio crx e la migrazione del contenuto, modificate la password dell&#39;account amministratore. Per istruzioni dettagliate, consultate [Modifica della password per un utente](/help/sites-administering/granite-user-group-admin.md)esistente.


1. Eseguire le operazioni post-distribuzione per verificare le credenziali di accesso, configurare document services, la gestione della corrispondenza, la protezione dei documenti e altro a seconda del caso d&#39;uso.
1. Verificare che il server sia stato aggiornato correttamente:

   Effettuare alcune operazioni di routine sul server AEM Forms aggiornato per verificare che il server sia aggiornato correttamente. È possibile compilare e inviare alcuni moduli migrati o proteggere i documenti per garantire la corretta esecuzione dell&#39;aggiornamento.

   >[!NOTE]
   >
   >In AEM 6.4 Forms, la struttura del repository crx è cambiata. Dopo aver effettuato l&#39;aggiornamento ai moduli AEM 6.4, utilizzate i percorsi modificati per la personalizzazione creati di nuovo. Per l&#39;elenco completo dei percorsi modificati, consultate Ristrutturazione archivio [moduli in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**A seconda dell’ambiente e del server applicazioni esistenti, scegliete uno dei seguenti documenti e seguite le istruzioni dettagliate:**

* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms per JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Aggiornamento da LiveCycle ES4 SP1 a AEM 6.4 Forms tramite JBoss Turnkey](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms on JEE {#livecycle-es3-forms-jee}

L&#39;aggiornamento di LiveCycle ES3 a AEM 6.4 Forms su JEE è un aggiornamento non aggiornato, in quanto comporta la migrazione di risorse e dati dalle versioni precedenti alle nuove istanze (nuove versioni) di server applicazione, sistemi operativi e database supportati.

Di seguito viene fornita una panoramica della procedura per aggiornare un server LiveCycle ES3 esistente a AEM 6.4 Forms. Per istruzioni dettagliate, vedere i documenti elencati al termine della procedura.

1. Prima di effettuare l’aggiornamento:

   1. Scaricate il programma di installazione AEM 6.4 Forms on JEE dal sito Web delle licenze [Adobe (LWS)](https://licensing.adobe.com/). Per scaricare il programma di installazione è necessario un contratto di manutenzione e assistenza valido.
   1. Decidete il tipo di repository del contenuto (repository CRX) da utilizzare. Solo alcuni moduli AEM su funzionalità JEE utilizzano la persistenza dell&#39;archivio dei contenuti per memorizzare contenuto e risorse. Installate e configurate l&#39;archivio dei contenuti solo se intendete utilizzare tali moduli AEM su funzionalità JEE:

      * Nei flussi di lavoro incentrati su AEM Forms, Moduli adattivi, Gestione della corrispondenza, Moduli HTML5, Forms Portal, Area di lavoro HTML, Reporting dei processi e Moduli sulle funzionalità OSGi, viene utilizzato Content Repository. Se si intende utilizzare AEM Forms per queste funzionalità, è necessario l&#39;archivio dei contenuti.
      * Non è necessario Content Repository per AEM Forms Document Security.
      Inoltre, il tipo di archivio di LiveCycle e AEM Forms è diverso. Per i tipi di archivio disponibili e le relative informazioni, consultate [Scelta di un tipo di persistenza per un&#39;installazione](/help/forms/using/choosing-persistence-type-for-aem-forms.md)di AEM Forms.

   1. Creare un backup del database LiveCycle ES3, dell&#39;archivio dati globale (GDS) e dell&#39;archivio contenuti (non richiesto per la protezione dei documenti). Se state effettuando l&#39;aggiornamento alla persistenza MongoMK o RDBMK, esportate le risorse per la gestione della corrispondenza di LiveCycle ES3 come archivio.
   1. Verifica che la piattaforma esistente (ovvero il server applicazioni, il database, il sistema operativo, Adobe Acrobat, le applicazioni di terze parti e l&#39;hardware) sia supportata per AEM 6.4 Forms on JEE. Per informazioni su hardware e software supportati, consultare il documento [Supportate Platform Combinations (Combinazioni](/help/forms/using/aem-forms-jee-supported-platforms.md) di piattaforme supportate).

      Se create una nuova istanza del database, importate nel database i dati di cui al punto 3. Per informazioni su come importare dati in un database, consultate la documentazione del fornitore di database corrispondente.

      >[!NOTE] Se si utilizza il formato di persistenza RDBMK, utilizzare un singolo database sia per la persistenza dell&#39;archivio che per i servizi basati su documenti in esecuzione su AEM Forms su JEE.


1. Eseguire l&#39;aggiornamento:

   1. Installa AEM 6.4 Forms su JEE su un nuovo server eseguendo il programma di installazione. Il programma di installazione inserisce tutti i file richiesti nel computer, all&#39;interno di una struttura di directory di installazione.
   1. Al termine dell&#39;installazione, eseguite **Configuration Manager** per configurare vari moduli AEM Forms e impostare le configurazioni appropriate. Insieme alle impostazioni di configurazione, consente di specificare il percorso di Global Data Storage (GDS) e crx-repository.

      >[!NOTE] Nella schermata Aggiornamento selezione attività, selezionate l&#39;opzione **[!UICONTROL Aggiorna da Adobe Experience Manager Forms 6.2.0]** . L’opzione **[!UICONTROL Aggiorna da Adobe Experience Manager Forms 6.2.0]** consente al gestore di configurazione di effettuare l’aggiornamento da LiveCycle ES3 a AEM 6.4 Forms.

   1. (Non richiesto per il modulo di protezione dei documenti AEM Forms) Aggiorna e importa l’archivio CRX nel server AEM 6.4 Forms.

      >[!NOTE] Dopo l&#39;aggiornamento dell&#39;archivio crx e la migrazione del contenuto, modificate la password dell&#39;account amministratore. Per istruzioni dettagliate, consultate [Modifica della password per un utente](/help/sites-administering/granite-user-group-admin.md)esistente.
1. Eseguire le operazioni post-distribuzione per verificare le credenziali di accesso, configurare document services, la gestione della corrispondenza, la protezione dei documenti e altro a seconda del caso d&#39;uso.
1. Verificare che il server sia stato aggiornato correttamente:

   Effettuare alcune operazioni di routine sul server AEM Forms aggiornato per verificare che il server sia aggiornato correttamente. È possibile compilare e inviare alcuni moduli migrati o proteggere i documenti per garantire la corretta esecuzione dell&#39;aggiornamento.

   >[!NOTE] In AEM 6.4 Forms, la struttura del repository crx è cambiata. Dopo aver effettuato l&#39;aggiornamento ai moduli AEM 6.4, utilizzate i percorsi modificati per la personalizzazione creati di nuovo. Per l&#39;elenco completo dei percorsi modificati, consultate Ristrutturazione archivio [moduli in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**A seconda dell’ambiente e del server applicazioni esistenti, scegliete uno dei seguenti documenti e seguite le istruzioni dettagliate:**

* [Aggiornamento da LiveCycle ES3 a AEM 6.4 Forms per JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Aggiornamento da LiveCycle ES3 a AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Aggiornamento da LiveCycle ES3 a AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Aggiornamento da LiveCycle ES3 a AEM 6.4 Forms tramite JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
