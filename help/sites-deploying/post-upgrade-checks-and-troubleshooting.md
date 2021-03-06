---
title: Controlli e risoluzione dei problemi post-aggiornamento
seo-title: Controlli e risoluzione dei problemi post-aggiornamento
description: Scopri come risolvere i problemi che potrebbero verificarsi dopo un aggiornamento.
seo-description: Scopri come risolvere i problemi che potrebbero verificarsi dopo un aggiornamento.
uuid: 3f83e8fc-1c45-4ef0-b8da-d29ff483d3d5
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: bc8c9aa2-f669-41f3-a526-6146ff5cf0cd
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1888'
ht-degree: 0%

---


# Controlli e risoluzione dei problemi post-aggiornamento{#post-upgrade-checks-and-troubleshooting}

## Controlli post aggiornamento {#post-upgrade-checks}

In seguito all&#39; [Aggiornamento sul posto](/help/sites-deploying/in-place-upgrade.md) per finalizzare l&#39;aggiornamento è necessario eseguire le seguenti attività. Si presume che AEM sia stato avviato con il jar 6.4 e che la base di codice aggiornata sia stata distribuita.

* [Verificare i registri per il successo dell’aggiornamento](#verify-logs-for-upgrade-success)

* [Verificare i bundle OSGi](#verify-osgi-bundles)

* [Verifica versione Oak](#verify-oak-version)

* [Inspect la cartella PreUpgradeBackup](#inspect-preupgradebackup-folder)

* [Convalida iniziale delle pagine](#initial-validation-of-pages)
* [Applica AEM Service Pack](#apply-aem-service-packs)

* [Migrazione AEM funzionalità](#migrate-aem-features)

* [Verificare le configurazioni di manutenzione pianificate](#verify-scheduled-maintenance-configurations)

* [Abilita agenti di replica](#enable-replication-agents)

* [Abilita processi pianificati personalizzati](#enable-custom-scheduled-jobs)

* [Esegui piano di test](#execute-test-plan)

### Verificare i registri per il successo dell&#39;aggiornamento {#verify-logs-for-upgrade-success}

**upgrade.log**

In passato, l&#39;ispezione dello stato post aggiornamento dell&#39;istanza richiedeva un&#39;attenta ispezione di vari file di log, parti dell&#39;archivio e del launchpad. La generazione di un rapporto di post aggiornamento può aiutare a rilevare gli aggiornamenti difettosi prima di andare in diretta.

Lo scopo principale di questa funzione è ridurre la necessità di interpretare manualmente o di eseguire analisi complesse su più endpoint necessari per qualificare il successo di un aggiornamento. La soluzione intende fornire informazioni non ambigue ai sistemi di automazione esterni per reagire al successo o al guasto identificato di un aggiornamento.

In particolare, garantisce che:

* Gli errori di aggiornamento rilevati dal framework di aggiornamento possono essere centralizzati in un unico rapporto di aggiornamento;
* Il rapporto di aggiornamento include indicatori relativi all&#39;intervento manuale necessario.

Per ovviare a questo problema, sono state apportate modifiche nel modo in cui i registri vengono generati nel file `upgrade.log`.

Ecco un esempio di rapporto che non mostra errori durante l&#39;aggiornamento:

![1487887443006](assets/1487887443006.png)

Ecco un esempio di rapporto che mostra un bundle non installato durante il processo di aggiornamento:

![1487887532730](assets/1487887532730.png)

**error.log**

Il file error.log deve essere attentamente rivisto durante e dopo l&#39;avvio di AEM utilizzando il file jar della versione di destinazione. Eventuali avvisi o errori devono essere rivisti. In generale è meglio cercare i problemi all&#39;inizio del log. Gli errori che si verificano successivamente nel registro possono in realtà essere effetti collaterali di una causa principale che viene richiamata in anticipo nel file. Se si verificano errori e avvisi ripetuti, vedi di seguito per [Analisi dei problemi relativi all&#39;aggiornamento](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-upgrade).

### Verificare i bundle OSGi {#verify-osgi-bundles}

Passa alla console OSGi `/system/console/bundles` e cerca di vedere se eventuali bundle non sono avviati. Se uno stato dei bundle è installato, consulta `error.log` per determinare il problema principale.

### Verifica la versione Oak {#verify-oak-version}

Dopo l’aggiornamento, noterai che la versione Oak è stata aggiornata a **1.8.2**. Per verificare la versione Oak, passa alla console OSGi e osserva la versione associata ai bundle Oak: Oak Core, Oak Commons, Oak Segment Tar.

### Cartella Inspect PreUpgradeBackup {#inspect-preupgradebackup-folder}

Durante l&#39;aggiornamento AEM tentare di eseguire il backup delle personalizzazioni e archiviarle sotto `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>`. Per visualizzare questa cartella in CRXDE Lite, potrebbe essere necessario [abilitare temporaneamente CRXDE Lite](/help/sites-administering/enabling-crxde-lite.md).

La cartella con timestamp deve avere una proprietà denominata `mergeStatus` con un valore di `COMPLETED`. La cartella **to-process** deve essere vuota e il nodo **sovrascritto** indica quali nodi sono stati sovrascritti durante l&#39;aggiornamento. Il contenuto sotto il nodo **leftovers** indica il contenuto che non è stato possibile unire in modo sicuro durante l&#39;aggiornamento. Se l’implementazione dipende da uno qualsiasi dei nodi figlio (e non è già installato dal pacchetto di codice aggiornato), dovrà essere unita manualmente.

Disattiva CRXDE Lite dopo questo esercizio se in un ambiente Stage o Production.

### Convalida iniziale delle pagine {#initial-validation-of-pages}

Esegui una convalida iniziale rispetto a più pagine in AEM. Se si aggiorna un ambiente di authoring, aprire la pagina iniziale e la pagina di benvenuto ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). Negli ambienti Author e Publish aprono alcune pagine dell’applicazione e ne eseguono il rendering corretto. Se si verificano problemi, consulta la sezione `error.log` per la risoluzione dei problemi.

### Applicare AEM Service Pack {#apply-aem-service-packs}

Applicare i Service Pack AEM 6.4 pertinenti se sono stati rilasciati.

### Funzionalità di migrazione AEM {#migrate-aem-features}

Diverse funzioni in AEM richiedono passaggi aggiuntivi dopo l’aggiornamento. Un elenco completo di queste funzioni e dei passaggi per migrarle in AEM 6.4 è disponibile nella pagina [Aggiornamento del codice e delle personalizzazioni](/help/sites-deploying/upgrading-code-and-customizations.md) .

### Verificare le configurazioni di manutenzione pianificate {#verify-scheduled-maintenance-configurations}

#### Abilita raccolta oggetti inattivi dell&#39;archivio dati {#enable-data-store-garbage-collection}

Se utilizzi un archivio dati file , assicurati che l’attività Archivio dati raccolta oggetti inattivi sia abilitata e aggiunta all’elenco Manutenzione settimanale. Le istruzioni sono descritte [qui](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Questa opzione non è consigliata per le installazioni dell&#39;archivio dati personalizzato S3 o quando si utilizza un archivio dati condiviso.

#### Abilita pulizia revisioni online {#enable-online-revision-cleanup}

Se utilizzi MongoMK o il nuovo formato del segmento TarMK, assicurati che l&#39;attività Pulizia revisioni sia abilitata e aggiunta all&#39;elenco Manutenzione giornaliera. Istruzioni descritte [qui](/help/sites-deploying/revision-cleanup.md).

### Esegui piano di test {#execute-test-plan}

Esegui un piano di test dettagliato rispetto a come definito [Aggiornamento del codice e delle personalizzazioni](/help/sites-deploying/upgrading-code-and-customizations.md) nella sezione **Procedura di test** .

### Abilita agenti di replica {#enable-replication-agents}

Dopo aver aggiornato e convalidato completamente l’ambiente di pubblicazione, abilita gli agenti di replica nell’ambiente di authoring. Verifica che gli agenti siano in grado di connettersi alle rispettive istanze Publish. Per ulteriori informazioni sull&#39;ordine degli eventi, consulta [Procedura di aggiornamento](/help/sites-deploying/upgrade-procedure.md) .

### Abilita processi pianificati personalizzati {#enable-custom-scheduled-jobs}

A questo punto è possibile abilitare tutti i processi pianificati come parte della base di codice.

## Analisi dei problemi relativi all&#39;aggiornamento {#analyzing-issues-with-upgrade}

Questa sezione contiene alcuni scenari di problema che si potrebbero incontrare durante la procedura di aggiornamento a AEM 6.4.

Questi scenari dovrebbero aiutare a individuare la causa principale dei problemi relativi all’aggiornamento e dovrebbero aiutare a identificare problemi specifici relativi a progetti o prodotti.

### Ricrea la configurazione cloud di Dynamic Media dopo l&#39;aggiornamento {#dynamic-media-cloud-configuration}

Dopo l&#39;aggiornamento a AEM 6.4 da una versione precedente, la configurazione di Dynamic Media Cloud dalle impostazioni precedenti potrebbe diventare inaccessibile dall&#39;interfaccia utente touch AEM 6.4. Per risolvere il problema, utilizza CRXDE Lite per rimuovere le impostazioni precedenti, quindi crea una nuova configurazione cloud Dynamic Media. Vedi anche [Ristrutturazione dell&#39;archivio Dynamic Media in AEM 6.4](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md).

### Migrazione archivio non riuscita {#repository-migration-failing-}

La migrazione dei dati da CRX2 a Oak dovrebbe essere fattibile per qualsiasi scenario a partire da Istanze sorgente basate su CQ 5.4. Assicurati di seguire esattamente le istruzioni di aggiornamento in questo documento, che includono la preparazione del `repository.xml`, assicurandoti che nessun autenticatore personalizzato venga avviato tramite JAAS e che l&#39;istanza sia stata controllata per individuare eventuali incongruenze prima di avviare la migrazione.

Se la migrazione continua a non riuscire, è possibile individuare la causa principale ispezionando il `upgrade.log`. Se il problema non è ancora noto, segnalalo all’Assistenza clienti.

### L&#39;aggiornamento non è stato eseguito {#the-upgrade-did-not-run}

Prima di avviare i passaggi di preparazione, assicurati di eseguire prima l&#39;istanza **source** eseguendola con il comando java -jar aem-quickstart.jar . Questo è necessario per assicurarti che il file quickstart.properties sia generato correttamente. Se manca, l&#39;aggiornamento non funzionerà. In alternativa, è possibile verificare se il file è presente cercando in `crx-quickstart/conf` nella cartella di installazione dell&#39;istanza di origine. Inoltre, quando si avvia AEM per avviare l&#39;aggiornamento, deve essere eseguito con il comando java -jar aem-quickstart.jar . L&#39;avvio da uno script iniziale non verrà avviato AEM in modalità di aggiornamento.

### Impossibile aggiornare pacchetti e bundle {#packages-and-bundles-fail-to-update-}

Nel caso in cui i pacchetti non vengano installati durante l&#39;aggiornamento, nemmeno i bundle che contengono verranno aggiornati. Questa categoria di problemi è solitamente causata da configurazione errata dell’archivio dati. Verranno inoltre visualizzati come messaggi **ERROR** e **WARN** nel registro degli errori. Poiché nella maggior parte di questi casi l&#39;accesso predefinito potrebbe non funzionare, è possibile utilizzare CRXDE direttamente per ispezionare e trovare i problemi di configurazione.

### Alcuni bundle AEM non passano allo stato attivo {#some-aem-bundles-are-not-switching-to-the-active-state}

In caso di bundle che non si avviano, dovresti verificare la presenza di dipendenze non soddisfatte.

Nel caso in cui questo problema sia presente ma si basa su un&#39;installazione non riuscita del pacchetto che ha portato a bundle non essere in fase di aggiornamento, saranno considerati incompatibili per la nuova versione. Per ulteriori informazioni su come risolvere questo problema, consulta **Impossibile aggiornare pacchetti e bundle** sopra.

Si consiglia inoltre di confrontare l&#39;elenco dei bundle di una nuova istanza AEM 6.4 con quella aggiornata per rilevare i bundle che non sono stati aggiornati. Questo fornirà un ambito più dettagliato di cosa cercare in `error.log`.

### I bundle personalizzati non passano allo stato attivo {#custom-bundles-not-switching-to-the-active-state}

Nel caso in cui i bundle personalizzati non passino allo stato attivo, è molto probabile che ci sia codice che non importa l&#39;API di modifica. Ciò spesso porterà a dipendenze non soddisfatte.

L’API rimossa deve essere contrassegnata come obsoleta in una delle versioni precedenti. Puoi trovare istruzioni su una migrazione diretta del tuo codice in questo avviso di rimozione. Adobe punta al controllo delle versioni semantiche, ove possibile, in modo che le versioni possano indicare eventuali modifiche di interruzione.

È anche meglio verificare se la modifica che ha causato il problema è assolutamente necessaria e ripristinarla se non lo è. Controlla anche se l&#39;aumento di versione dell&#39;esportazione del pacchetto è stato aumentato più del necessario, dopo un rigoroso controllo delle versioni semantiche.

### Interfaccia utente della piattaforma non funzionante {#malfunctioning-platform-ui}

Nel caso di alcune funzionalità dell’interfaccia utente che non funzionano correttamente dopo l’aggiornamento, controlla prima le sovrapposizioni personalizzate dell’interfaccia. Alcune strutture potrebbero essere cambiate e la sovrapposizione potrebbe aver bisogno di un aggiornamento o essere obsoleta.

Quindi, controlla eventuali errori Javascript che possono essere tracciati verso le estensioni aggiunte personalizzate collegate alle librerie client. Lo stesso può essere applicato per i CSS personalizzati che potrebbero causare problemi al layout di AEM.

Infine, verifica la presenza di errori di configurazione che Javascript potrebbe non essere in grado di gestire. Questo accade solitamente con le estensioni disattivate in modo errato.

### Funzionamento errato dei componenti personalizzati, dei modelli o delle estensioni dell&#39;interfaccia utente {#malfunctioning-custom-components-templates-or-ui-extensions}

Nella maggior parte dei casi, le cause principali di questi problemi sono le stesse dei bundle che non vengono avviati o dei pacchetti che non vengono installati con l&#39;unica differenza che i problemi iniziano quando si utilizzano i componenti.

Il modo per trattare con codice personalizzato errato è quello di eseguire prima prove di fumo al fine di identificare la causa. Una volta trovato, cerca i consigli in questa sezione [link] dell&#39;articolo per trovare i modi per risolverli.

### Personalizzazioni mancanti in etc {#missing-customizations-under-etc}

`/apps` e  `/libs` sono gestite correttamente dall&#39;aggiornamento, ma le modifiche in  `/etc` potrebbero dover essere ripristinate manualmente da  `/var/upgrade/PreUpgradeBackup` dopo l&#39;aggiornamento. Assicurati di controllare questa posizione per eventuali contenuti da unire manualmente.

### Analisi di error.log e upgrade.log {#analyzing-the-error-log-and-upgrade-log}

Nella maggior parte delle situazioni i registri devono essere consultati per gli errori al fine di trovare la causa di un problema. Tuttavia, in caso di aggiornamenti è anche necessario monitorare i problemi di dipendenza, in quanto i vecchi bundle potrebbero non essere aggiornati correttamente.

Il modo migliore per farlo è quello di eliminare il file error.log rimuovendo tutti i messaggi che ci si aspetta che non siano correlati al problema che stai affrontando. Puoi farlo tramite strumenti come grep, utilizzando:

```shell
grep -v UnrelatedErrorString
```

Alcuni messaggi di errore potrebbero non essere immediatamente esplicativi. In questo caso, esaminare il contesto in cui si verificano può anche aiutare a capire dove è stato creato l’errore. Puoi separare l’errore utilizzando:

* `grep -B` per aggiungere righe prima dell’errore;

o

* `grep -A` per aggiungere righe dopo.

In alcuni casi si possono trovare errori anche nei messaggi WARN in quanto ci possono essere casi validi che portano a questo stato e l&#39;applicazione non è sempre in grado di decidere se si tratta di un errore effettivo. Assicurati di consultare anche questi messaggi.

### Contattare il supporto Adobe {#contacting-adobe-support}

Se hai seguito i consigli su questa pagina e stai ancora riscontrando dei problemi, contatta il supporto Adobe. Per fornire il maggior numero possibile di informazioni al tecnico del supporto che lavora sul tuo caso, assicurati di includere il file upgrade.log dal tuo aggiornamento.
