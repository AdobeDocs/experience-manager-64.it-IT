---
title: Aggiornamento ad AEM 6.4 Forms
seo-title: Upgrade to AEM 6.4 Forms
description: È possibile eseguire un aggiornamento diretto da Forms 6.1, Forms 6.2 AEM e LiveCycle ES4 SP1 a Forms 6.3.
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: 183ed9c6-6a9a-4932-8405-5ae2c6fac1ec
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 9%

---

# Aggiornamento a AEM 6.4 Forms su OSGi {#upgrade-to-aem-forms-osgi}

Utilizza uno dei seguenti percorsi di aggiornamento, in base alle esigenze del tuo ambiente.

## AEM 6.2 Forms o AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

Puoi eseguire un aggiornamento diretto da AEM 6.2 Forms o AEM 6.3 Forms a AEM 6.4 Forms. Effettua le seguenti operazioni:

1. Aggiorna l&#39;istanza AEM esistente a AEM 6.4. I passaggi sono elencati di seguito:

   1. Installa il service pack e le patch più recenti per Forms 6.2 o AEM 6.3 Forms. Per ulteriori informazioni, consulta:

      * [Note sulla versione di AEM 6.2](https://helpx.adobe.com/it/experience-manager/6-2/release-notes.html)
      * [Note sulla versione di AEM 6.3](https://helpx.adobe.com/it/experience-manager/6-3/release-notes.html)
      * [Hub di AEM](https://helpx.adobe.com/it/experience-manager/aem-releases-updates.html)
   1. Prepara l&#39;istanza sorgente per l&#39;aggiornamento. Per i passaggi dettagliati vedi [Aggiornamento a AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Scarica la [Guida rapida di AEM 6.4](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(solo installazioni basate su Unix/Linux)** Se utilizzi UNIX o Linux come sistema operativo sottostante, apri la finestra del terminale, passa alla cartella contenente crx-quickstart ed esegui il seguente comando:

      `chmod -R 755 ../crx-quickstart`

   1. Aggiorna l&#39;istanza AEM a AEM 6.3. Per istruzioni dettagliate, consulta [Aggiornamento a AEM 6.4](/help/sites-deploying/upgrade.md).

      Prima di continuare con i passaggi successivi, attendere che i messaggi ServiceEvent REGISTERED e ServiceEvent UNREGISTERED smettano di apparire nel &lt;crx-repository>file /error.log .

      >[!NOTE]
      >
      >Quando il server è in esecuzione, alcuni bundle AEM Forms rimangono nello stato di installazione. Il numero di bundle può variare per ogni installazione. Puoi tranquillamente ignorare lo stato di questi bundle. I bundle sono elencati in `https://[server]:[port]/system/console/`.


1. Installa il pacchetto aggiuntivo di AEM Forms. I passaggi sono elencati di seguito:

   1. Apri [Software Distribution](https://experience.adobe.com/downloads). Per accedere a Software Distribution è necessario disporre di un Adobe ID.
   1. Tocca **[!UICONTROL Adobe Experience Manager]** che si trova nel menu di intestazione.
   1. In **[!UICONTROL Filtri]** sezione:
      1. Seleziona **[!UICONTROL Forms]** dal **[!UICONTROL Soluzione]** elenco a discesa.
      1. Seleziona la versione e digita il pacchetto. È inoltre possibile utilizzare **[!UICONTROL Download di ricerca]** per filtrare i risultati.
   1. Toccare il nome del pacchetto applicabile al sistema operativo in uso, selezionare **[!UICONTROL Accettare i termini dell&#39;EULA]**, e tocca **[!UICONTROL Scarica]**.
   1. Apri [Gestione pacchetti](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=it) e fai clic su **[!UICONTROL Carica pacchetto]** per caricarlo.
   1. Seleziona il pacchetto e fai clic su **[!UICONTROL Installa]**.

      Puoi anche scaricare il pacchetto utilizzando il collegamento diretto elencato in [Versioni di AEM Forms](https://helpx.adobe.com/it/aem-forms/kb/aem-forms-releases.html) articolo.

      >[!NOTE]
      >
      >Una volta installato il pacchetto, viene richiesto di riavviare l&#39;istanza AEM. **Non arrestare immediatamente il server.** Prima di arrestare il server AEM Forms, attendi che i messaggi ServiceEvent REGISTERED e ServiceEvent UNREGISTERED non vengano più visualizzati nel &lt;crx-repository>/error.log e il registro è stabile. Inoltre, alcuni pacchetti possono rimanere nello stato di installazione. Puoi ignorare lo stato di questi pacchetti in tutta sicurezza.

   1. Arresta l’istanza AEM ed elimina i file seguenti:

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Avvia l’istanza di AEM.


1. Eseguire attività post-installazione.

   * **Esegui utility di migrazione**

      L’utility di migrazione rende compatibili le risorse di gestione della corrispondenza e dei moduli adattivi delle versioni precedenti con AEM 6.4 forms. È possibile scaricare l&#39;utility da Distribuzione software AEM. Per informazioni dettagliate su come configurare e utilizzare l’utility di migrazione, consulta [utility di migrazione](/help/forms/using/migration-utility.md).

      Se utilizzi [Esempio per l&#39;integrazione del componente bozze e invii](integrate-draft-submission-database.md) con il database e l&#39;aggiornamento da una versione precedente, quindi eseguire le seguenti query SQL dopo l&#39;esecuzione dell&#39;aggiornamento:

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

   * **(Solo per l’aggiornamento da AEM 6.2 Forms o versioni precedenti) Riconfigura Acrobat Sign**

      Se Acrobat Sign era stato configurato nella versione precedente di AEM Forms, riconfigura Acrobat Sign dai servizi AEM Cloud. Per ulteriori dettagli, consulta [Integrare Acrobat Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(Solo per l’aggiornamento da Forms 6.2 o versioni precedenti) Riconfigura analisi e rapporti**

      In Forms 6.4 AEM, la variabile di traffico per la sorgente e l’evento di successo per l’impression non sono disponibili. Pertanto, quando esegui l’aggiornamento da AEM 6.2 Forms o versioni precedenti, AEM Forms smette di inviare dati al server Adobe Analytics e i rapporti di analisi per i moduli adattivi non sono disponibili. Inoltre, AEM 6.4 Forms introduce una variabile di traffico per la versione di analisi dei moduli e un evento di successo per la quantità di tempo trascorso su un campo. Quindi, riconfigura analisi e rapporti per il tuo ambiente AEM Forms. Per i passaggi dettagliati vedi [Configurazione di analisi e rapporti](/help/forms/using/configure-analytics-forms-documents.md).

1. Verificare che il server sia stato aggiornato correttamente, che anche tutti i dati siano migrati correttamente e che possa funzionare normalmente.

   * **Verifica lo stato dei bundle:** Assicurati che tutti i bundle siano in stato attivo.
   * **Verifica replica e replica inversa:** Pubblicare, compilare e inviare alcuni moduli migrati. Verifica anche i dati inviati.
   * **Verifica l’accesso alle interfacce utente amministratore e sviluppatore:** Accedi a AEM&#39;istanza da un account amministratore e verifica di avere accesso ai seguenti URL:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   In Forms 6.4 AEM, la struttura di crx-repository è cambiata. Dopo aver effettuato l’aggiornamento a AEM moduli 6.4, utilizza i percorsi modificati per la personalizzazione che hai creato nuovamente. Per l’elenco completo dei percorsi modificati, vedi [Ristrutturazione dell’archivio Forms in AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms e AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

Percorso di aggiornamento diretto da **Forms 6.0 AEM** e **Forms 6.1** a AEM 6.4 Forms non è disponibile. Eseguire un intermedio [aggiornamento a AEM 6.2 Forms](/help/forms/using/upgrade.md) o [aggiornamento a AEM 6.3 Forms](/help/forms/using/upgrade.md) e quindi effettuare l&#39;aggiornamento da AEM 6.2 Forms o AEM 6.3 Forms a AEM 6.4 Forms.
