---
title: Migrazione dei contenuti Lazy
seo-title: Lazy Content Migration
description: Scopri la Migrazione dei contenuti Lazy in AEM 6.4.
seo-description: Learn about Lazy Content Migration in AEM 6.4.
uuid: 9c84f7fe-31d3-4b63-8975-9e75a6c44b7d
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 282a828a-edb2-4643-9bf7-ec30c29dc6ce
feature: Upgrading
exl-id: 8dc2dfb8-037f-40ae-a962-ced89dd3fdd0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 7%

---

# Migrazione dei contenuti Lazy{#lazy-content-migration}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per motivi di compatibilità con le versioni precedenti, contenuti e configurazione in **/etc** e **/content** a partire da AEM 6.3 non sarà toccato o trasformato immediatamente con l&#39;aggiornamento. Ciò viene fatto per garantire che le dipendenze delle applicazioni dei clienti su tali strutture rimangano intatte. La funzionalità relativa a queste strutture di contenuto è ancora la stessa anche se il contenuto in una versione standard AEM 6.4 sarebbe ospitato in un’altra posizione.

Anche se non tutte queste posizioni possono essere trasformate automaticamente, ci sono alcuni ritardi `CodeUpgradeTasks` è anche noto come Migrazione dei contenuti Lazy. Questo consente ai clienti di attivare tali trasformazioni automatiche riavviando l&#39;istanza con questa proprietà del sistema:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Questo causerà il `CodeUpgradeTasks` da eseguire durante la migrazione.

Sebbene l&#39;obiettivo sia un&#39;esecuzione efficiente, questo processo di aggiornamento è sincrono e comporta pertanto un downtime a seconda della quantità di contenuto da elaborare. Si consiglia di valutare i tempi di esecuzione in un ambiente di stage prima di un sistema di produzione per pianificare un intervallo di manutenzione in base.

Poiché in genere è necessario regolare l’applicazione, questa attività deve essere eseguita insieme alla distribuzione dell’applicazione corrispondente.

Di seguito è riportato l&#39;elenco completo di `CodeUpgradeTasks` introdotto al punto 6.4:

| **Nome** | **Pertinente per le versioni AEM** | **Tipo di migrazione** | **Dettagli** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Immediato |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Immediato | Rileva tutti `LiveRelationShips` da `VersionStorage` che sono stati eliminati e aggiungono proprietà di esclusione all&#39;elemento padre |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Immediato | Ristruttura i servizi cloud per la configurazione sicura per impostazione predefinita |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Immediato | Rimuove il collegamento basato su proprietà da **/content** a **/conf** (sostituito dal meccanismo OSGi), genera la configurazione OSGi corrispondente |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Immediato | A causa della gestione merge_preserve della regola di negazione sicura per impostazione predefinita, le sostituzioni a causa di autorizzazioni specifiche che comportano la necessità di riordinare l&#39;aggiornamento |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Immediato | Rileva i componenti che utilizzano il widget Html5SmartFile, cerca gli utilizzi del componente nel contenuto e ristruttura la persistenza, spostando efficacemente il binario verso il basso e non archiviarlo a livello di componente. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Immediato | Sposta i progetti in stile precedente da **/etc/projects** a **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Immediato | Introduce un livello contenitore alla gerarchia (Aree) e regola i riferimenti. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Immediato | Imposta i nomi della posizione fissa sui componenti di destinazione. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Immediato | Trasformazione complessa dei modelli di flusso di lavoro precedente a strutture, istanze, notifiche 6.2 e unione dal percorso di backup **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Immediato | Sposta risorse, schemi di metadati personalizzati e profili di elaborazione da **/apps** a **/conf** e traduce lo schema metadati e i profili metadati dei moduli da coral2 a coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Immediato | Sposta le risorse e i facet di ricerca personalizzati da **/apps** a **/conf** e traduce lo schema metadati e i profili metadati dei moduli da coral2 a coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Immediato | Aggiorna InboxItems per ordinare gli elementi della casella in entrata (regolazione dei metadati per un ordinamento efficiente) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Immediato | Regola la proprietà metadataSchema nella cartella sostituendo i percorsi relativi in **/conf** al posto di **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Immediato | Regolazione della struttura di navigazione |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Immediato | Sposta le configurazioni personalizzate per le dashboard di monitoraggio da **/libs** e **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Immediato | Traduce la proprietà processingProfile (utilizzata fino alla versione 6.1) in Assets in modo che corrisponda alla struttura 6.3 e versioni successive. Regola anche i percorsi relativi del profilo in **/conf** al posto di **/apps**. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Immediato | Attività di aggiornamento che rimuove le voci di menu obsolete di CRXDE Lite e della console Web in caso di aggiornamento. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Ritardato | Spostamento delle configurazioni cloud SRP, configurazioni di parole d&#39;ordine community, pulizia **/etc/social** e **/etc/enablement** (tutti i riferimenti e i dati devono essere regolati quando si esegue la migrazione pigra - nessuna parte dell&#39;applicazione deve più dipendere da questa struttura). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Ritardato | Pulizia **/etc/cloudsettings** (contenente la configurazione ContextHub). La configurazione viene migrata automaticamente al primo accesso. Nel caso in cui venga avviata la migrazione dei contenuti Lazy insieme all’aggiornamento di questo contenuto in **/etc/cloudsettings** deve essere mantenuto tramite pacchetto prima dell&#39;aggiornamento e reinstallato per la trasformazione implicita da avviare, insieme a una successiva disinstallazione del pacchetto dopo il completamento. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Ritardato | Regola la struttura del titolo legacy in base al titolo nel nodo del profilo utente. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Ritardato | Eseguire la migrazione dei contenuti di e-commerce da **/etc/commerce** a **/var/commerce**. Durante la migrazione il contenuto viene spostato e i riferimenti al contenuto spostato vengono aggiornati per riflettere la nuova posizione. |
