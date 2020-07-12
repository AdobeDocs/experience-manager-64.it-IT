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
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 3%

---


# Aggiornamento ad AEM 6.4 Forms su OSGi {#upgrade-to-aem-forms-osgi}

Utilizzate uno dei seguenti percorsi di aggiornamento, in base alle esigenze dell&#39;ambiente in uso.

## AEM 6.2 Forms o AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

È possibile eseguire un aggiornamento diretto da AEM 6.2 Forms o AEM 6.3 Forms a AEM 6.4 Forms. Effettua le seguenti operazioni:

1. Aggiorna l’istanza AEM esistente a AEM 6.4. I passaggi sono elencati di seguito:

   1. Installa il service pack e le patch più recenti per AEM 6.2 Forms o AEM 6.3 Forms. Per informazioni dettagliate, consultate:

      * [Note sulla versione di AEM 6.2](https://helpx.adobe.com/it/experience-manager/6-2/release-notes.html)
      * [Note sulla versione di AEM 6.3](https://helpx.adobe.com/it/experience-manager/6-3/release-notes.html)
      * [Hub di supporto AEM](https://helpx.adobe.com/it/experience-manager/aem-releases-updates.html)
   1. Preparare l’istanza di origine per l’aggiornamento. Per i passaggi dettagliati, consultate [Aggiornamento ad AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Scaricate la Guida rapida [di](/help/sites-deploying/deploy.md#getting%20the%20software)AEM 6.4.
   1. **(Solo installazioni basate su Unix/Linux)** Se utilizzate UNIX o Linux come sistema operativo sottostante, aprite la finestra del terminale, individuate la cartella contenente crx-quickstart ed eseguite il comando seguente:

      `chmod -R 755 ../crx-quickstart`

   1. Aggiorna l’istanza di AEM a AEM 6.3. Per istruzioni dettagliate, consultate [Aggiornamento ad AEM 6.4](/help/sites-deploying/upgrade.md).

      Prima di continuare con i passaggi successivi, attendere che i messaggi ServiceEvent REGISTERED e ServiceEvent UNREGISTERED non vengano visualizzati nel file &lt;crx-repository>/error.log.

      >[!NOTE]
      >
      >Una volta che il server è in esecuzione, alcuni bundle di AEM Forms rimangono nello stato di installazione. Il numero di pacchetti può variare per ogni installazione. Potete ignorare lo stato di questi bundle. I bundle sono elencati in `https://[server]:[port]/system/console/`.


1. Installare il pacchetto del componente aggiuntivo AEM Forms. I passaggi sono elencati di seguito:

   1. Apri distribuzione [](https://experience.adobe.com/downloads)software. È necessario un Adobe ID  per accedere a Distribuzione software.
   1. Toccate **[!UICONTROL Adobe Experience Manager]** disponibile nel menu dell&#39;intestazione.
   1. Nella sezione **[!UICONTROL Filtri]** :
      1. Selezionare **[!UICONTROL Forms]** dall&#39;elenco a discesa **[!UICONTROL Soluzione]** .
      1. Selezionate la versione e digitate il tipo di pacchetto. Potete anche utilizzare l&#39;opzione Download **[!UICONTROL di]** ricerca per filtrare i risultati.
   1. Toccate il nome del pacchetto applicabile al sistema operativo in uso, selezionate **[!UICONTROL Accetta termini]** EULA e toccate **[!UICONTROL Scarica]**.
   1. Aprite [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) e fate clic su **[!UICONTROL Carica pacchetto]** per caricare il pacchetto.
   1. Select the package and click **[!UICONTROL Install]**.

      Potete anche scaricare il pacchetto utilizzando il collegamento diretto elencato nell&#39;articolo delle release [](https://helpx.adobe.com/it/aem-forms/kb/aem-forms-releases.html) AEM Forms.

      >[!NOTE]
      >
      >Dopo l&#39;installazione del pacchetto, viene richiesto di riavviare l&#39;istanza di AEM. **Non arrestare immediatamente il server.** Prima di arrestare il server AEM Forms, attendere che i messaggi ServiceEvent REGISTERED e ServiceEvent UNREGISTERED non vengano visualizzati nel file &lt;crx-repository>/error.log e il registro sia stabile. Inoltre, alcuni pacchetti possono rimanere nello stato di installazione. Potete ignorare lo stato di questi pacchetti in tutta sicurezza.

   1. Arrestate l’istanza AEM ed eliminate i seguenti file:

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Avviate l’istanza AEM.


1. Eseguire attività post-installazione.

   * **Esegui utility di migrazione**

      L’utility di migrazione rende compatibili i moduli adattivi e le risorse per la gestione della corrispondenza delle versioni precedenti con i moduli AEM 6.4. Potete scaricare l&#39;utility da Distribuzione software AEM. Per informazioni dettagliate su come configurare e utilizzare l’utility di migrazione, consultate Utility [di](/help/forms/using/migration-utility.md)migrazione.

      Se si utilizza [Sample per integrare il componente](integrate-draft-submission-database.md) bozze e invii con il database e per eseguire l&#39;aggiornamento da una versione precedente, eseguire le query SQL seguenti dopo l&#39;esecuzione dell&#39;aggiornamento:

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(solo se si esegue l&#39;aggiornamento da AEM 6.2 Forms o versioni precedenti) Riconfigurare Adobe Sign**

      Se Adobe Sign è stato configurato nella versione precedente dei AEM Forms, riconfigurare Adobe Sign dai AEM cloud services. Per ulteriori dettagli, vedere [Integrazione di Adobe Sign con i AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(solo se si esegue l&#39;aggiornamento da AEM 6.2 Forms o versioni precedenti) Riconfigurare analisi e report**

      In AEM 6.4 Forms, la variabile di traffico per l’origine e l’evento di successo per l’impressione non sono disponibili. Pertanto, quando si esegue l&#39;aggiornamento da AEM 6.2 Forms o versioni precedenti, i AEM Forms smettono di inviare dati al server Adobe  Analytics e i report di analisi per i moduli adattivi non sono disponibili. Inoltre, AEM 6.4 Forms introduce la variabile del traffico per la versione dell&#39;analisi dei moduli e l&#39;evento di successo per il tempo trascorso su un campo. Quindi, riconfigurate analisi e report per l&#39;ambiente AEM Forms. Per informazioni dettagliate, consultate [Configurazione di analisi e rapporti](/help/forms/using/configure-analytics-forms-documents.md).

1. Verificare che il server sia aggiornato correttamente, che tutti i dati siano migrati correttamente e che possa funzionare normalmente.

   * **Verificare lo stato dei bundle:** Verificate che tutti i bundle siano nello stato attivo.
   * **Verifica replica e replica inversa:** Pubblicare, compilare e inviare alcuni moduli migrati. Verificare anche i dati inviati.
   * **Verificare l&#39;accesso alle interfacce utente amministratore e sviluppatore:** Accedi all’istanza AEM da un account amministratore e verifica di avere accesso ai seguenti URL:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   In AEM 6.4 Forms, la struttura del repository crx è cambiata. Dopo aver effettuato l&#39;aggiornamento ai moduli AEM 6.4, utilizzate i percorsi modificati per la personalizzazione creati di nuovo. Per l&#39;elenco completo dei percorsi modificati, consultate Ristrutturazione archivio [moduli in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## Moduli AEM 6.0 e moduli AEM 6.1 > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

Il percorso di aggiornamento diretto dai moduli **AEM 6.0 e** **** AEM 6.1 a AEM 6.4 non è disponibile. Effettuate un [aggiornamento intermedio a AEM 6.2 Forms](/help/forms/using/upgrade.md) o [eseguite l&#39;aggiornamento ad AEM 6.3 Forms](/help/forms/using/upgrade.md) , quindi da AEM 6.2 Forms o AEM 6.3 a AEM 6.4 Forms.
