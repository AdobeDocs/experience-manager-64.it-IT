---
title: Note sulla versione di AEM 6.4 Service Pack
seo-title: AEM 6.4 Service Pack Release Notes
description: Note sulla versione specifiche dei Service Pack di Adobe Experience Manager 6.4.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
exl-id: d0da9390-2167-47ee-82fd-8c81d8d68a3e
source-git-commit: 1537055fd88cbc3b01e4df7855a99f993f2052e4
workflow-type: tm+mt
source-wordcount: '21547'
ht-degree: 26%

---

# Note sulla versione di AEM 6.4 Service Pack {#aem-service-pack-release-notes}

## Informazioni sulla versione {#release-information}

| Prodotti | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versione | 6.4.8.0 |
| Tipo | Versione Service Pack |
| Data | 5 marzo 2020 |
| URL di download | AEM 6.4.8.0 on [Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## Funzionalità incluse in AEM 6.4.8.0 {#what-s-included-in-aem}

AEM 6.4.8.0 è un aggiornamento importante che include nuove funzionalità, miglioramenti e prestazioni richiesti dai clienti chiave, stabilità, miglioramenti a livello di sicurezza, rilasciato a partire dalla disponibilità generale di AEM 6.4 in **Aprile 2018.**

È anche cumulativo, il che significa che 6.4.8.0 include tutti i service pack AEM 6.4 rilasciati prima di esso.

Di seguito sono elencati alcuni elementi di rilievo di questo Service Pack:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.20.

* La funzionalità di ritorno a capo automatico è supportata per i siti web giapponesi in WCM-RTE.

* L’elaborazione delle interruzioni di riga e di parola è supportata per i siti web giapponesi.

* È stato aggiunto il supporto per utilizzare il metodo BUNSETSU per interrompere la frase e le linee in lingua giapponese nelle posizioni appropriate.

* L’interfaccia utente CCR per la gestione della corrispondenza ora supporta i valori decimali per le impostazioni internazionali tedesche.

* L’integrazione del modello dati modulo con il servizio Web SOAP ora supporta i gruppi di scelta o gli attributi sugli elementi.

* AEM Assets è ora configurato con Brand Portal tramite [!DNL Adobe I/O].

* È stata aggiornata la versione jQuery inclusa nel pacchetto ContextHub alla versione 3.2.1.

## Elenco delle modifiche {#list-of-changes}

### Sites {#sites}

* Quando un URL di una pagina AEM Sites contiene due punti o un simbolo di percentuale, il browser sottostante smette di rispondere e i cicli della CPU mostrano un picco (NPR-32368, NPR-31917).
* Quando una pagina AEM Sites viene aperta per la modifica e un componente viene copiato, l’azione Incolla non è disponibile per alcuni segnaposto (NPR-32328).
* Il flusso di lavoro di richiesta dell’attivazione non include le risorse di riferimento (NPR-32304).
* Quando viene creata una Blueprint, se il numero di record è superiore a 80, vengono visualizzati solo i primi 80 record. Blueprint visualizza le righe vuote per il resto dei record (NPR-32058).
* Gli utenti possono salvare un frammento di contenuto senza fornire informazioni nei campi richiesti (NPR-31988).
* La navigazione automatica non funziona per il percorso configurato in un componente Frammento esperienza core (NPR-31921).
* Quando si modifica il tipo di cella di una tabella nell’Editor Rich Text, si verifica il seguente errore:
   `Error: No common ancestor found, cannot continue` (NPR-31916)
* Quando il contenuto viene spostato all’interno della stessa cartella, l’opzione di spostamento della pagina viene disabilitata (NPR-31841).
* È stato aggiunto il supporto per dividere le frasi in lingua giapponese utilizzando il metodo BUNSETSU e le linee di interruzione nella posizione appropriata (NPR-31836).
* Quando si modifica un collegamento ipertestuale nell’Editor Rich Text, il percorso appena selezionato non viene salvato (NPR-31659).
* Quando elimini un componente con più campi e annulli l’eliminazione, il componente viene ripristinato ma i dati non vengono ripristinati (NPR-31617).

### Assets {#assets}

* Viene creata una cartella senza nome in Dynamic Media Classic mentre si sposta una risorsa da una cartella all’altra in Experience Manager con configurazione Dynamic Media Classic (NPR-32440).

* La pagina dei dettagli delle risorse dei file PDF non mostra i pulsanti di azione in Experience Manager in esecuzione in modalità Scene7 di Dynamic Media (NPR-32316).

* Non è possibile eliminare le rappresentazioni di risorse e video (NPR-32213).

* L’icona del calendario per l’attivazione pianificata non viene visualizzata nella colonna Stato (nell’interfaccia classica dell’elenco delle risorse DAM) per le risorse la cui attivazione è pianificata per una data e un’ora successive (NPR-32198).

* La relazione tra le risorse viene sovrascritta quando le risorse sono collegate a più risorse utilizzando Altro (NPR-32196).

* Il pulsante Salva non importa il set remoto se l’utente non ha apportato modifiche nell’Editor set nel client Dynamic Media (NPR-32178).

* L’inserimento delle risorse di PSD causa il picco della CPU e l’istanza di authoring di Experience Manager non reattiva (NPR-32165).

* Eccezione di memoria esaurita osservata quando un file ZIP di grandi dimensioni viene caricato in Experience Manager DAM (NPR-32155).

* Gli URL della cronologia delle versioni vengono visualizzati nel campo Con riferimento nella pagina Proprietà delle risorse (NPR-31889).

* L’annullamento della pubblicazione da Brand Portal, nella pagina Gestisci pubblicazione, non riesce per le sottocartelle di una cartella pubblicata (NPR-31835).

* Le codifiche video Dynamic Media non vengono caricate quando la configurazione di Scene7 Cloud viene inserita in una cartella privata `/conf` anziché `/conf/global` (NPR-31779)

* L’immagine non viene visualizzata nella timeline dopo l’aggiunta di annotazioni, ad Experience Manager in esecuzione in modalità di esecuzione di Dynamic Media Scene7 (NPR-31754).

* Impossibile aprire il file ZIP scaricato da DAM utilizzando WinZip (NPR-31745).

### Integrazioni {#integrations-6480}

* La **Azienda** e **Reporting** I menu a discesa Suite sono nascosti una volta **Origine per i rapporti** è selezionato durante la configurazione di Adobe Analytics in Experience Manager Cloud Services (NPR-31729).

* Le proprietà di Adobe Campaign non vengono pulite quando viene effettuata la copia in lingua di una newsletter collegata a un Adobe Campaign, mentre la pulizia viene eseguita quando una newsletter collegata a un Adobe Campaign viene copiata o incollata (NPR-32540).

* ReportSuitesServlet è vulnerabile a SSRF (NPR-32161).

### Sling {#sling-6480}

* L&#39;ombreggiatura non deterministica dell&#39;osservazione delle risorse non funziona (CQ-4286466).

### Progetti {#projects-6480}

* Il pulsante Crea non è visibile all’utente anche se l’utente dispone dell’autorizzazione per creare un progetto nella sottocartella (NPR-31831).

* La funzionalità per passare dalla visualizzazione a schede, dalla visualizzazione a elenco alla visualizzazione Calendario non funziona dopo aver selezionato Vista calendario in Progetti (NPR-31829).

### Traduzione {#translation-6480}

* La creazione di progetti di traduzione per più lingue genera il progetto solo per alcune lingue invece che per tutte e nel registro viene osservato un errore (il risolutore risorse è già chiuso) (NPR-32212).

### WCM-MSM {#wcm-msm-6480}

* I problemi di autorizzazione generano errori durante lo spostamento di pagine all’interno di una blueprint (NPR-32610).

### Editor pagina WCM {#wcm-page-editor-6480}

* Il browser smette di rispondere quando si tenta di aggiungere un componente a una pagina con un formato URL specifico (NPR-32368, NPR-31917).

### WCM-Admin UI {#wcm-admin-ui-6480}

* La pubblicazione della gestione non include le risorse di riferimento nel flusso di lavoro di richiesta dell’attivazione (NPR-32304).

### Communities {#communities}

* Impossibile aggiornare l&#39;immagine della miniatura del gruppo per i gruppi (NPR-32603).

### Brand Portal {#brand-portal}

* Lo schema di metadati di annullamento della pubblicazione in AEM Assets popola un messaggio di errore anche se lo schema viene rimosso nel back-end (CQ-4286871).

### Interfaccia utente di base {#foundations-ui-6480}

* I caratteri non validi vengono visualizzati nell’URL aggiunto a un componente Pulsante (NPR-32684).

### Forms {#forms}

>[!NOTE]
>
>Il Service Pack di AEM non include le correzioni per AEM Forms. Tali correzioni vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi per Forms. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per AEM Forms su JEE. Per ulteriori informazioni, consulta [Installare il pacchetto aggiuntivo di AEM Forms](#install-aem-forms-add-on-package) e [Installare il programma di installazione di JEE per AEM Forms](#install-aem-forms-jee-installer).

* Designer: Se l’opzione di assegnazione tag è abilitata, il bordo del sottomodulo scompare nell’output di PDF generato (NPR-32546, NPR-32322).

* Designer: se in una tabella sono presenti celle unite, il test di accessibilità non riesce per il file PDF di output convertito da un modulo XDP utilizzando l’apposito servizio (NPR-32079).

* Sicurezza dei documenti: Un file PDF protetto non si apre offline con l&#39;opzione DisableGlobalOfflineSynchronizationData impostata su True (NPR-32080).

* Sicurezza dei documenti: Problemi durante l&#39;apertura di un file PDF protetto dopo l&#39;aggiornamento da ES4 a AEM 6.3 (NPR-32170).

* Servizi documenti: Viene visualizzato un messaggio di errore durante il tentativo di convertire un file PDF in un documento PDF/A utilizzando il metodo di conversione toPDFA (NPR-32663).

* Servizi documenti: Viene visualizzata un’eccezione durante l’applicazione del servizio Estensioni di Reader su un file PDF (NPR-32639).

* Servizi documenti: Viene visualizzato un messaggio di errore durante l’assemblaggio e la conversione di file XDP in file PDF (NPR-31821).

* Analytics non visualizza i risultati appropriati per l’invio o l’abbandono dei moduli su una pagina Sites (NPR-31359).

### Hotfix e Feature Pack inclusi nei Service Pack precedenti {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

AEM 6.4.7.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio di AEM 6.4 in **Aprile 2018.**

È anche cumulativo, il che significa che 6.4.7.0 include tutte le versioni di Service Pack 6.4 AEM prima di esso.

Alcuni degli elementi di rilievo di AEM 6.4.7.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.17.
* È stato aggiunto il supporto per impostare la versione di una pagina Sites durante l’eliminazione.
* È stata aggiunta una nuova colonna per la data creata, ordinabile, in **Elenco DAM** visualizza e sui risultati della ricerca delle risorse in **Elenco** vista (NPR-31311).
* Ordinamento delle risorse in base a **Nome** La colonna è consentita in **Elenco** visualizza.
* Le dimensioni del batch e il timeout del passaggio del flusso di lavoro per la rielaborazione e il caricamento in batch sono ora configurabili dall’interfaccia utente di Dynamic Media.
* La `pdfBrochure` è stato impostato su false nella configurazione cloud di Scene 7 per salvare la memoria su IPS.

##### Risorse {#assets-6470}

**Miglioramenti al prodotto**

* Versione di esportazione del pacchetto API `package com.day.cq.dam.handler.standard.msoffice` supportato da `dam-handler` il bundle viene aggiornato alla versione 6.0.0 (CQ-4279059).
Se utilizzi il pacchetto `com.day.cq.dam.handler.standard.msoffice` nell’implementazione personalizzata, ti consigliamo di compilare il tuo `dam-handler` con l&#39;ultimo jar uber.

* La nuova colonna per la data creata, ordinabile, è stata aggiunta nella vista a elenco DAM e nei risultati della ricerca delle risorse nella vista a elenco (NPR-31311).

* L’ordinamento delle risorse in base alla colonna Nome è consentito nella vista a elenco (NPR-31299).

**Problemi risolti**

* I metadati per alcuni documenti PDF non vengono aggiornati e salvati in PDF quando si modifica il titolo (NPR-31575).

* Le risorse con il simbolo &quot;+&quot; nel nome file non possono essere eliminate (NPR-30588).

* Le proprietà della cartella DAM non mostrano gli utenti o i gruppi aggiunti (creati dalla sincronizzazione LDAP) nei gruppi di utenti chiusi (NPR-30555).

* I caratteri speciali che si verificano nella riga Oggetto dei modelli e-mail non vengono visualizzati correttamente (NPR-30547).

* I nomi delle risorse vengono modificati in minuscolo quando si spostano le risorse da una cartella all’altra in AEM in esecuzione in modalità runmode Dynamic Media Scene 7 (NPR-31631).

* I nomi del set di immagini vengono modificati in minuscolo in Scene 7, quando il set di immagini (o il set di file multimediali) viene creato e denominato con la convenzione di denominazione appropriata in DAM (NPR-31576).

* Il flusso di lavoro Codifica video di Dynamic Media non riesce a generare miniature per il video migrato da Scene 7 a Dynamic Media - Modalità di esecuzione di Scene 7 (NPR-31523).

* Errore interno del server durante l&#39;utilizzo del filtro per la ricerca dei set, in AEM in esecuzione in modalità runmode Dynamic Media - Scene 7 (NPR-31388).

* Si osserva un errore durante la modifica di un set di immagini remoto, per l&#39;immagine che si trova nella cartella denominata come nome dell&#39;azienda Scene 7 (NPR-31347).

* Le risorse contenenti riferimenti non vengono pubblicate (DM) (NPR-31179).

* Il valore di scadenza (durata della cache del client) configurato per la modalità ibrida di Dynamic Media non viene replicato nell’ambiente di distribuzione di Dynamic Media (NPR-31126).

* I caricamenti da AEM Dynamic Media - Scene 7 in modalità runmode a Scene 7 richiedono troppo tempo per essere completati (NPR-30926).

* Dopo aver creato una pagina con un componente Dynamic Media durante la pubblicazione dello stesso, dall’istanza di authoring in esecuzione in modalità runmode Dynamic Media - Scene 7, all’utente viene richiesto di pubblicare la configurazione dmscene7 (NPR-30880).

* Il valore del parametro &quot;asset&quot; nel codice di incorporamento del visualizzatore rimane invariato dopo la modifica dei valori nei campi &quot;Title after move&quot; e &quot;Name after move&quot; in Dynamic Media - Scene 7 (NPR-30745).

* La pagina dei risultati della ricerca nell’interfaccia touch (tramite Omnisearch) scorre automaticamente verso l’alto e perde la posizione di scorrimento dell’utente (NPR-31306).

* DAM Event Purge elimina i dati dell’evento più recenti (maxSavedActivities) e contiene i dati creati in precedenza (NPR-30870).

* La modifica del titolo e del nome della risorsa non viene mantenuta dopo l’operazione di spostamento in una cartella di destinazione che attiva lo scorrimento infinito durante la selezione (NPR-30647).

* Le raccolte vengono rimosse dalla visualizzazione per l’applicazione di qualsiasi filtro in AEM Assets accessibile da Adobe Asset Link (CQ-4280534).

* Le dimensioni del batch e il timeout del passaggio del flusso di lavoro per la rielaborazione e il caricamento in batch non sono configurabili dall&#39;interfaccia utente e devono essere impostati in CRXDE e il flusso di lavoro deve essere sincronizzato due volte (CQ-4281254).

* Il nome del passaggio del flusso di lavoro per il caricamento in batch e il semplice passaggio di caricamento è lo stesso in Scene 7, il che crea confusione (CQ-4281176).

* Il flusso di lavoro di rielaborazione in Scene 7 si blocca se a una risorsa manca il nodo di metadati (CQ-4281170).

* Il passaggio BatchUpload nel flusso di lavoro di rielaborazione non funziona per la cartella con risorse video (CQ-4280630).

* Per le opzioni di PDF inviate a DM, l’impostazione predefinita di extractKeywords è true (CQ-4280101).

* Eccezione Null Point durante l&#39;esecuzione del flusso di lavoro di rielaborazione di Scene 7 in una cartella contenente risorse non-DM (CQ-4279555).

* La ridenominazione delle risorse in AEM non viene sincronizzata con la scena 7, quando una risorsa con un nome duplicato esiste già in Scene 7 (CQ-4276763).

* Il file ZIP inviato tramite e-mail per il download delle risorse non riesce a decomprimere quando un utente con autorizzazioni di lettura tenta di aprirlo (CQ-4277925).

* Il flusso di lavoro di rendering PPT non riesce a generare rappresentazioni dei file PPT caricati, in quanto AEM 6.4 non riesce ad aggiornare alla versione 2.0.28 di com.adobe.granite.poi (CQ-4279059).

* I file PDF non sono indicizzati e il contenuto all’interno non è ricercabile (CQ-4278916).

##### Sites {#sites-6470}

* Quando i lanci vengono promossi con Promuovi solo pagine modificate e Promuovi i lanci con pagine modificate vengono eseguiti, solo le pagine modificate appaiono come promosse. Inoltre, quando l’elenco da promuovere è corretto, le pagine non modificate vengono ancora visualizzate in fondo all’elenco (NPR-31314).

* Quando una pagina AEM Sites viene spostata in una posizione diversa, le relative proprietà non vengono aggiornate di conseguenza per riflettere la nuova posizione (NPR-31265).

* Per una nuova blueprint, se il numero di record è superiore a 40, vengono visualizzati solo i primi 40 record. Blueprint visualizza le righe vuote per il resto dei record (NPR-31182).

* Quando il numero di LiveCopy è grande, il rendering dell’anteprima richiede molto tempo dalla panoramica LiveCopy (NPR-30945).

* È stato aggiunto il supporto per impostare una versione di una pagina durante l’eliminazione. Se il controllo delle versioni è disabilitato per la pagina eliminata, AEM Sites non può ripristinarle (NPR-30891).

* Quando un utente aggiunge caratteri giapponesi o coreani nella proprietà description di un menu, nel menu vengono visualizzati caratteri distorti per il testo in giapponese e coreano (NPR-31331).

* Quando un utente usa i campi della barra a sinistra e una scelta rapida da tastiera per incollare il contenuto, viene incollato il contenuto degli Appunti dell’Editor pagina invece del contenuto copiato dai campi della barra a sinistra (NPR-31169).

* Quando un utente modifica un frammento di contenuto, viene ripristinata la variante già eliminata del frammento di contenuto (NPR-31178).

* La query Modelli per frammenti di contenuto non è efficiente. È molto lento se l&#39;istanza ha molte pagine e si traduce in un errore (NPR-30666).

* Quando si salva il modello di frammento di contenuto, l’ora nel campo data e ora è impostata su 00:00 (NPR-30540).

##### Integrazioni {#integrations-6470}

* Durante la configurazione di Adobe Launch, nell’URL della libreria viene preceduta una barra (/) (NPR-30700).

* Le prestazioni di ContextHub si degradano dopo la pubblicazione (NPR-30884).

##### Sling {#sling-6470}

* Aggiorna la versione del bundle del provider di sicurezza della console Web a 1.2.4 per rimuovere la dipendenza dell&#39;api avviatore del launchpad da webconsole esecurityprovider (NPR-30885).

##### Platform {#platform-6470}

* Gli aggiornamenti nella configurazione della dimensione del buffer per il servizio HTTP basato su Jetty non vengono salvati (NPR-30925).

* QueryBuilder ora supporta orderby fn:name() nelle query xpath (NPR-31322).

* Aggiornamento dell&#39;amministratore di eventi distribuiti Sling alla versione 1.1.4 per migliorare la qualità dei registri in un ambiente cluster (NPR-29256).

##### Interfaccia utente di base {#foundation-6470}

* Se si scorre la pagina dei risultati con un numero elevato di risultati, il browser si blocca (NPR-31332).

* Quando si passa dalla vista Scheda alla vista Elenco in una pagina dei risultati di ricerca, si verifica un ritardo prima dello scorrimento della pagina (NPR-31280).

##### Oak {#oak-6470}

* I file MS Office con estensione .docx e .xlsx contenenti immagini JPEG non riescono ad analizzare utilizzando il parser Tika (NPR-31693).

##### Livefyre {#livefyre-6470}

* L’integrazione di Livefyre con l’aggiornamento AEM 6.4 fornisce un’eccezione Null Point, quando l’integrazione viene eseguita utilizzando il plug-in DITA per le risorse sintetiche. L’integrazione, tuttavia, funziona quando i componenti vengono aggiunti manualmente (FYR-11066).

##### Traduzione {#translation-6470}

* Il percorso del frammento di esperienza di destinazione non viene aggiornato quando si promuove una pagina di lancio (NPR-30830).

##### Community {#communities-6470}

* La funzionalità e-mail non funziona correttamente in alcuni casi anche quando la messaggistica e-mail è abilitata nelle impostazioni di notifica, il sistema genera un&#39;eccezione in NotificationsActivityStreamProvider (NPR-31521).
* Impossibile creare nuovi membri. Viene visualizzata una schermata vuota nella schermata Crea membro nell&#39;istanza AEM autore (NPR-30951).
* L&#39;utente non è in grado di pubblicare un commento su un blog in Internet Explorer 11 (NPR-30927).
* L&#39;amministratore di un gruppo con restrizioni non è in grado di visualizzare la scheda Gruppo, non è in grado di eseguire operazioni di collegamento rapido (gruppi di modifica/pubblicazione/eliminazione) nell&#39;istanza di authoring AEM (NPR-30810).
* Le informazioni sui gruppi di membri non sono visibili durante la creazione di un nuovo sito nell’istanza di authoring AEM (NPR-28840).

##### Forms {#forms-6470}

>[!NOTE]
>
>Il Service Pack di AEM non include le correzioni per AEM Forms. Tali correzioni vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi per Forms. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per AEM Forms su JEE. Per ulteriori informazioni, consulta [Installare il pacchetto aggiuntivo di AEM Forms](#install-aem-forms-add-on-package) e [Installare il programma di installazione di JEE per AEM Forms](#install-aem-forms-jee-installer).

**Pacchetto di componenti aggiuntivi per Forms**

**Moduli adattivi**

* Le stringhe contengono la chiave del dizionario durante la localizzazione dei moduli adattivi (NPR-31109).

* Le caselle di controllo e gli elenchi a discesa nei controlli per l’accessibilità di Forms (NPR-31282).

**Moduli HTML5**

* Quando si genera l’anteprima HTML5 di un modulo XDP, viene visualizzato uno sfarfallio durante l’aggiunta di istanze di un sottomodulo (NPR-30907).

**Document Services per OSGi**

* L&#39;esecuzione di più thread simultanei per l&#39;assemblaggio dei moduli utilizzando il metodo com.adobe.fd.assembler.service.AssemblerService.invoke() visualizza un messaggio di errore (NPR-31164).

* I file temporanei creati dal servizio Assembler non vengono eliminati automaticamente e richiedono AEM riavvio (NPR-30846).

* L&#39;applicazione dei diritti di estensione di Reader ad PDF genera un messaggio di errore (NPR-30930).

**Flusso di lavoro**

* Il flusso di lavoro OSGi non riesce a causa dell&#39;utilizzo della CPU al 100% (NPR-31234).

**Programma di installazione di JEE per Forms**

**Document Services**

* Il servizio Convert PDF non riesce a convertire i documenti PDF in formato PostScript e visualizza un messaggio di errore (NPR-31267).

* La configurazione dell’endpoint SOAP viene reimpostata dopo l’applicazione di una patch per correggere l’errore di HTML in PDF (NPR-31309).

**Servizio PDFG**

* Impossibile caricare il file delle impostazioni Adobe PDF scaricato utilizzando l&#39;interfaccia utente amministratore (NPR-31273).

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio di AEM 6.4 in **Aprile 2018.**

È anche cumulativo, il che significa che 6.4.6.0 include tutte le versioni di Service Pack 6.4 AEM prima di esso.

Alcuni degli elementi di rilievo di AEM 6.4.6.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.15.
* È stato aggiunto il supporto per il tracciamento degli stati dell’interfaccia utente dinamica nell’evento di tracciamento nell’API di base.
* È stato aggiunto il supporto per il rendering al componente di base immagine.

**Assets**

* Collegamento di condivisione risorse di una cartella con spazio e `&` Nel nome vengono visualizzate schede grigie vuote per alcune risorse. NPR-29934: Hotfix per CQ-4270187
* Il flusso di lavoro DAM si blocca durante la creazione di risorse MP4 per AEM. NPR-30031: Hotfix per CQ-4271352
* Problema di connettività di Tag avanzati di Adobe tramite DataPower. NPR-30026: Hotfix per CQ-4269457
* Impossibile trovare PDF utilizzando OmniSearch. NPR-30046: Hotfix per GRANITE-26290
* I percorsi delle risorse negli URL e i metadati delle cartelle generati dall’API ACP non sono codificati in URL.  GRANITE-26198: Hotfix per CQ-4271814
* La funzionalità Crea attività di revisione non funziona a causa di un payload non definito. NPR-30469: Hotfix CQ-4274263
* La possibilità di passare dalla vista a schede alla vista a elenco e viceversa scompare dopo aver effettuato una ricerca Omni nel selettore delle risorse. NPR-29852: Hotfix per CQ-4269369
* (Interfaccia touch) Durante la procedura guidata di gestione della pubblicazione, le risorse vengono aggiunte alla coda di replica dopo l’aggiunta delle pagine, causando la visualizzazione di alcune risorse dopo alcuni secondi. NPR-29985: Hotfix per CQ-4270724
* Se si ordinano le query di ricerca in base alla rilevanza, oltre ai modelli InDesign vengono restituiti documenti InDesign. Hotfix per CQ-4273864
* Se l’utente dispone di un ID e-mail in maiuscolo, non potrà eseguire la consegna per le risorse ritirate in precedenza. Hotfix per CQ-4276575
* Configurazione di Cloud Services Dynamic Media in `DMHybrid` in questo modo si ottengono più suite di rapporti vuote create in Analytics senza l’ID suite di rapporti memorizzato in AEM, con conseguente duplicazione delle suite di rapporti. Hotfix per CQ-4276855
* La finestra di dialogo di avviso non viene visualizzata durante la promozione nella pagina &quot;Tag gestito&quot;. Hotfix per CQ-4252851
* Quando si utilizza il carosello per la gestione dei tag, il pulsante di navigazione non funziona. Hotfix per CQ-4275499
* La funzionalità di spostamento in blocco delle risorse non funziona e le risorse non vengono spostate. Hotfix per CQ-4272987

**Sites**

* `pageinfo.json` le richieste sono estremamente lente e richiedono troppo tempo per essere caricate. NPR-29709: Hotfix per CQ-4269560
* `onTime` o `offTime` le proprietà dei metadati salvate nelle risorse non vengono richiamate se il server AEM viene riavviato. NPR-30413: Hotfix per CQ-4272784
* A causa di un comportamento errato della classe ConfigPostProcessor, la sospensione della pagina padre rimuove cq: Tipo di mixaggio LiveRelationship dalla pagina figlio. NPR-30536, NPR-30510: Hotfix per CQ-4254113
* Vulnerabilità cross-site scripting (XSS) nella finestra di dialogo del flusso di lavoro all’avvio nella pagina di modifica di Campaign. NPR-29747: Hotfix per CQ-4271067
* (Interfaccia classica) La fase di blocco del flusso di lavoro disattiva la scheda del flusso di lavoro fino al rilascio del blocco. NPR-30356: Hotfix per CQ-4237557
* (IE11) Quando si incolla il contenuto di HTML in un componente Editor Rich Text con defaultPasteMode = testo normale, il HTML viene incollato con la formattazione, pertanto defaultPasteMode non ha alcun effetto. NPR-30045: Hotfix per GRANITE-26094
* (Interfaccia classica) Quando la pagina di amministrazione del sito viene ricaricata, tutti gli elementi a discesa nel menu &quot;Nuovo&quot; sono disabilitati. NPR-29980: Hotfix per CQ-4272044
* Impossibile aggiungere stili al testo o modificare gli stili esistenti creati sul contenuto. NPR-29712: Hotfix per CQ-4266249
* (Interfaccia classica) Risorse senza dc: il valore del titolo viene elencato senza titolo nel browser della finestra di dialogo del campo percorso. NPR-30166: Richiesta di backport per CQ-88858
* QC: Il listener non funziona con i componenti nidificati anche dopo l&#39;aggiunta del componente parsys. NPR-30422: Hotfix per CQ-4274863
* Errore di ContextHub durante l’integrazione di AEM e Campaign. NPR-30625: Hotfix per CQ-4250790
* Il valore del parametro di richiesta resourceType viene copiato nel valore di un attributo di tag HTML che è racchiuso tra virgolette doppie. NPR-29832: Hotfix per CQ-4255365
* È necessario un aggiornamento della pagina dopo che i componenti sono stati copiati e incollati da una pagina all’altra. NPR-29982: Hotfix per CQ-4256019
* L’opzione Pubblica/Annulla pubblicazione da un alias di pagina non è supportata e deve essere rimossa. NPR-30062: Hotfix per CQ-4271249
* Avviso ResourceResolver non chiuso in ExperienceFragmentsReplicationListener che nel tempo causava problemi di stabilità, forzando il riavvio delle istanze AEM. NPR-30416: Hotfix per CQ-4257521
* Lo spostamento dei frammenti esperienza a cui si fa riferimento in più di 150 pagine non modifica il fragmentPath nelle pagine a cui si fa riferimento. NPR-30556: Hotfix per CQ-4274900
* Errore di analisi durante l’apertura di un frammento di contenuto con caratteri dollaro (`$`) e parentesi graffa aperta (`{`) una dopo l&#39;altra. Hotfix per CQ-4270266
* VersionPreviewServlet non riesce in NullPointerException quando si prova a visualizzare una versione di un frammento esperienza nella timeline. NPR-30074: Hotfix per CQ-4271881
* Impossibile bloccare i frammenti di contenuto tramite la funzione di archiviazione. NPR-29923: Hotfix per CQ-4258785
* Errore di verifica della firma nel gestore di autenticazione SAML. NPR-30379: Richiesta di backport per GRANITE-26567

**Replica**

* La sessione JCR / Resource Resolver viene persa durante l&#39;implementazione di OAuth su ogni replica in MAC / Brand Portal. NPR-30000: Hotfix per GRANITE-26196

**Sling**

* L&#39;ordine degli elementi figlio interessati dalla sovrapposizione e dall&#39;ordine precedenti causa IndexOutOfBoundException. NPR-30408: Hotfix per Sling-8296 e Sling-7375
* InactiveBundlesHealthCheck sta leggendo la configurazione MissingPackagesHealthCheck una volta salvate le configurazioni InactiveBundlesHealthCheck. NPR-30084: Hotfix per CQ-4272644

**Commerce**

* Impossibile eseguire la blueprint del catalogo dalla console Sites. NPR-29829: Hotfix per CQ-4271461
* La risorsa utilizzata nel prodotto non mostra alcun riferimento al prodotto nella sezione &quot;Riferimenti&quot; della risorsa né il percorso della risorsa viene aggiornato se la risorsa viene spostata. NPR-30542: Hotfix per CQ-4270247

**Platform**

* Il mittente predefinito di AEM non è in grado di inviare messaggi a un server SMTP remoto tramite TLS v1.2. NPR-30476: Hotfix per GRANITE-26605

**Communities**

* I gruppi eliminati sull&#39;autore non sono sincronizzati con tutti gli editori. NPR-29987: Hotfix per CQ-4268738
* Gli utenti eliminati rimossi dal campo Amministratori community non sono sincronizzati con il gruppo Appartenenza. NPR-30389: Hotfix per CQ-4274339
* Gli utenti appartenenti al gruppo amministratori non dispongono di collegamenti rapidi per il gruppo. NPR-30546: Hotfix per CQ-4275579
* L&#39;aggiornamento di un gruppo Community appena creato ed esistente sovrascrive la proprietà su jcr: nodo di contenuto e modifica il nome del nodo nel titolo della prima pagina. NPR-30109: Hotfix per CQ-4273719
* La ricerca rapida e la ricerca attraverso la posizione e l&#39;indirizzo non funzionano quando la community è impostata per funzionare con Database Storage Resource Provider (DSRP). NPR-26737: Hotfix per CQ-4258493

**Traduzione**

* L’esecuzione automatica della traduzione non funziona. NPR-30499: Hotfix per CQ-4276288
* L’utente può creare una copia per lingua nel percorso del contenuto limitata alla sola lettura. NPR-29937: Hotfix per CQ-4270708
* Problema di traduzione - Solo alcuni componenti vengono tradotti utilizzando la traduzione automatica. NPR-30079: Hotfix per CQ-4273764

**Integrazione**

* Il contenuto personalizzato non viene visualizzato correttamente nell’istanza di pubblicazione fino al riavvio dell’istanza. NPR-30421: Hotfix per CQ-4273706

**Progetti**

* I valori dam:folderThumbnailPaths non vengono aggiornati e vengono visualizzate miniature vecchie anche dopo l’eliminazione delle risorse nella cartella. NPR-30424: Hotfix per CQ-4273667

**Console dell’interfaccia utente**

* Script tra siti (XSS) nelle proprietà della pagina Sites nella scheda miniature. NPR-30048: Hotfix per GRANITE-26200

**UI-Foundation**

* È stato aggiunto il supporto per il tracciamento degli stati dell’interfaccia utente dinamica nell’evento di tracciamento nell’API di base. NPR-30742, GRANITE-26322: Hotfix per GRANITE-26036

**Forms**

>[!NOTE]
>
>Il Service Pack di AEM non include le correzioni per AEM Forms. Tali correzioni vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi per Forms. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per AEM Forms su JEE. Per ulteriori informazioni, consulta [Installare il pacchetto aggiuntivo di AEM Forms](#install-aem-forms-add-on-package) e [Installare il programma di installazione di JEE per AEM Forms](#install-aem-forms-jee-installer).

**Pacchetto di componenti aggiuntivi per Forms**

**Moduli adattivi**

* Il recupero del file .css vuoto dall’editore richiede più tempo, causando problemi di prestazioni. NPR-30558: Hotfix per CQ-4274399
* I Forms che vengono modificati dopo la pubblicazione non vengono postati di nuovo alla pubblicazione del sito. NPR-30411: Hotfix per CQ-4236566

**Forms - Integrazione back-end**

* Viene generato un errore durante la creazione del modello dati del modulo con il linguaggio WSDL (Web Service Definition Language). NPR-30388: Hotfix per CQ-4272921

**Forms - Gestione della corrispondenza**

* I caratteri speciali come &lt; (&lt;), maggiore di (>) e e commerciale (&amp;) vengono codificati nell’interfaccia utente dell’agente. NPR-30410: Hotfix per CQ-4273887
* Quando si attiva un frammento di testo contenente valori del dizionario dati, l’interfaccia utente dell’agente non risponde. NPR-30098, NPR-30083: Hotfix per CQ-4272204
* L’interfaccia utente Crea corrispondenza (interfaccia utente CCR) non riesce a intermittenza con la variabile di errore (oggetto Object). NPR-29983: Hotfix per CQ-4273874
* Il ricaricamento della bozza della lettera non riesce, con un&#39;eccezione quando la descrizione dei frammenti del documento contiene caratteri speciali come minore di (&lt;), maggiore di (>) e e commerciale (&amp;) nelle proprietà. NPR-29930: Hotfix per CQ-4252762

**Moduli HTML5**

* Quando si utilizza l’accesso desktop non visivo in modalità Sfoglia per leggere un modulo HTML5, il browser Chrome legge l’elemento “grafico” prima di qualsiasi file SVG nella struttura del modulo. NPR-30450: Hotfix per CQ-4274732

**Programma di installazione di JEE per Forms**

**Forms - JEE di base**

* L’aggiunta o la modifica di una connessione a un servizio Web richiamando i servizi Web da Workbench moduli genera un errore: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116: Hotfix per CQ-4273217

**Forms - Servizi basati su documenti**

* Errore mancante nell’etichetta PDF/A in Acrobat preflight. NPR-30594: Hotfix per CQ-4276032
* I binding dei dati a carattere singolo in PDF causano il mancato funzionamento delle estensioni del Reader con un errore &quot;java.lang.StringIndexOutOfBoundException: Indice di stringa fuori intervallo: 1&quot; NPR-30128: Hotfix per CQ-4273878
* Quando si esegue un test di caricamento su un servizio di conversione da HTML a PDF, il test non riesce, viene restituito un errore e le impostazioni del tipo di file vengono rimosse dal server AEM Forms. NPR-30085: Hotfix per CQ-4272631
* L’appiattimento di un PDF con Adobe Acrobat 9.1 (XFA versione 3.0) non mantiene lo stato del modulo PDF: Gli elementi invisibili del modulo vengono reimpostati su uno stato visibile. NPR-29978: Hotfix per CQ-4270888

**Forms - Sicurezza dei documenti**

* L’applicazione di una firma con marca temporale non riesce e viene restituito l’errore: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Errore di chiamata. NPR-30696, NPR-30537: Hotfix per CQ-4273778
* Configuration Manager non inserisce stringhe giapponesi per colonne di tabella localizzate. NPR-30496: Hotfix per CQ-4274868

**Servizio PDFG**

* Errore di connessione durante il tentativo di convertire il documento Word in PDF in Windows Server 2016. NPR-30597: Hotfix per CQ-4275652
* Eccezione negata quando si tenta di utilizzare il servizio backend HTML to PDF tramite la libreria &quot;phantomjs&quot;. NPR-30456: Hotfix per CQ-4258077
* maxReuseCount per il servizio da HTML a PDF non viene visualizzato con la console di gestione JBoss. NPR-30303, NPR-30135: Hotfix per CQ-4273763

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio di AEM 6.4 in **Aprile 2018.**

È anche cumulativo, il che significa che 6.4.5.0 include tutte le versioni di Service Pack 6.4 AEM prima di esso.

Alcuni degli elementi di rilievo di AEM 6.4.5.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.13.
* È stato aggiunto il timeout del socket e della connessione negli agenti di replica Brand Portal.
* Miglioramenti della ricerca Omnisearch : il limite di impaginazione del risultato della ricerca è stato aumentato a 100 pagine.
* Disabilitato `AssetDownloadServlet` Componente OSGi per impostazione predefinita su istanze di pubblicazione AEM. Per ulteriori informazioni, consulta [Scaricare risorse da AEM](/help/assets/download-assets-from-aem.md).
* Abilitazione del supporto per l’utilità di gestione di più siti per Assets. Per ulteriori informazioni, consulta [Riutilizzare le risorse con MSM per le risorse](/help/assets/reuse-assets-using-msm.md).

**Risorse**

* Le risorse con un apostrofo nel nome file non vengono sincronizzate con Dynamic Media. NPR-29538: Hotfix per CQ-4270592
* Aggiornamento dell’interfaccia DMGateway di DAM per il supporto multipart di S3. NPR-29740: Hotfix per CQ-4226303
* La finestra di dialogo per il download delle risorse visualizza una dimensione file non corretta durante il download delle rappresentazioni per un video in Dynamic Media. NPR-29642: Hotfix per CQ-4246202
* Le risorse diventano inutilizzabili dopo l’applicazione del testo per m3u8 da parte del servizio Day CQ DAM Mime Type . NPR-29276: Hotfix per CQ-4264052
* La regolazione del riferimento delle risorse non riesce a salvare la sessione se una delle risorse spostate/rinominate fa parte delle raccolte di risorse Sling. NPR-29143: Hotfix per /CQ-4252605
* Impossibile tenere traccia o trovare le risorse ricercando i valori dei metadati. NPR-29141: Hotfix per CQ-4260215
* Quando si utilizza il filtro di ricerca per salvare una raccolta avanzata, l’azione di clic sul pannello non mantiene lo stato attivo. NPR-29000: Hotfix per CQ-4240323
* Lo spostamento di una cartella consente la creazione di una cartella con nomi misti o maiuscoli. NPR-28945: Hotfix per CQ-4265234
* I risultati vuoti vengono visualizzati in Omnisearch se il nome della raccolta dispone di spazio. NPR-29001: Hotfix per CQ-4236729
* Se si rinomina un file utilizzando alcuni caratteri speciali non supportati come e commerciale (&amp;), viene creata una cartella non valida. NPR-29196: Hotfix per CQ-4265037
* L&#39;archivio di estrazione DAM per la funzionalità dei file zip è danneggiato. NPR-29187: Hotfix per CQ-4254421
* L’importazione di metadati deve consentire l’importazione di metadati senza la registrazione di spazi dei nomi. NPR-29425, NPR-28132: Hotfix per CQ-4269445
* Il salvataggio delle modifiche ai metadati non funziona per le risorse il cui nome contiene un carattere di virgolette. NPR-29395: Hotfix per CQ-4254305
* Impossibile spostare una risorsa DAM se il nome del file contiene spazi bianchi. NPR-29270: Hotfix per CQ-4266403
* Impossibile scaricare archivi ZIP compressi con algoritmo Deflate64. NPR-29225: Hotfix per CQ-4253995
* Le miniature delle risorse vengono visualizzate lentamente quando si apre una cartella contenente risorse con più versioni. NPR-29833: Hotfix per CQ-4271629
* Impossibile inserire la raccolta evidenziata se viene premuto il tasto Invio dopo aver selezionato la raccolta. NPR-29723: Hotfix per CQ-4261607
* Attacco di vulnerabilità cross-site scripting (XSS) attraverso la finestra di avviso con restrizioni. NPR-29671: Hotfix per CQ-4270133
* L’aggiunta di relazioni alle risorse non riesce per gli utenti senza autorizzazioni di eliminazione. NPR-29640: Hotfix per CQ-4269196
* Dopo aver aggiunto il titolo della risorsa nella pagina delle proprietà, quando l’utente tenta di chiudere la pagina, AEM riapre la pagina delle proprietà. NPR-29628: Hotfix per CQ-4264929
* La creazione di un numero elevato di relazioni sulla risorsa genera un errore. NPR-28779: Hotfix per CQ-4250708
* L’inserimento delle risorse è lento nella modalità di esecuzione di Scene7 Connect. NPR-28658: Hotfix per CQ-4263007
* Errore TypeError non rilevato: Impossibile leggere la proprietà &#39;split&#39; di undefined viene visualizzata quando si tenta di visualizzare i risultati della ricerca. NPR-28803: Hotfix per CQ-4248371
* La replica da AEM a Brand Portal è bloccata per lunghi periodi. NPR-28914: Hotfix per CQ-4254932
* Lo spostamento delle risorse in DAM non determina un movimento simile su Scene7. NPR-28957: Hotfix per CQ-4264974
* Gli aggiornamenti dei metadati non vengono passati a IPS se il campo di metadati viene aggiornato in AEM. NPR-28961: Hotfix per CQ-4255393
* VersioningTimelineEventProvider deve fornire la versione principale insieme al commento sulla versione. Hotfix per GRANITE-26063
* L’inserimento dei dati porta all’esecuzione del codice sul lato server. Hotfix per CQ-4270246
* Abilitazione del supporto per l’utilità di gestione di più siti per Assets. Hotfix per CQ-4271453, CQ-4268621, CQ-4257491
* L’interfaccia di AEM deve contenere una voce aggiuntiva per la versione corrente della risorsa nella cronologia della timeline, per visualizzare l’ultimo commento di consegna fornito da Adobe Asset Link. Hotfix per CQ-4262864
* Il video di esempio non viene caricato durante la creazione o la modifica di un MixedMediaSet. Hotfix per CQ-4244889
* La disattivazione delle autorizzazioni per eliminare i contenuti sul lato AEM impedisce all’utente di pubblicare su Brand Portal. Hotfix per CQ-4270426
* Problemi relativi al limite di query con i rapporti sulle risorse dopo l’aggiornamento a AEM 6.4.3. NPR-28588: Hotfix per CQ-4262022, CQ-4260697
* La funzionalità di download usufruisce di AEM Assets tramite il servlet assetdownload, consentendo agli utenti anonimi di scaricare tutte le risorse. NPR-27315, Hotfix per CQ-4254732

**Sites**

* Il nome del tag di reclamo JCR deve essere compilato automaticamente in base al titolo del tag. NPR-28990: Hotfix per CQ-4199411
* Il pulsante Annulla ereditarietà non è visibile su alcuni campi aggiunti nelle proprietà della pagina. NPR-29079: Hotfix per CQ-4265686
* L’azione di anteprima rollout non deve provare a ricreare la Live Copy o a mostrarla nell’elenco delle pagine di rollout. NPR-29151: Hotfix per CQ-4266213
* (Editor modelli) Regressione dei criteri di stile in modalità struttura. NPR-28981: Hotfix per CQ-4264400
* Le Live Copy nidificate mostrano voci duplicate durante il rollout. NPR-29300: Hotfix per CQ-4268664
* La pubblicazione di una Live Copy di una Live Copy contenente un componente Importazione progettazione non riesce e i riferimenti per la pagina selezionata non vengono recuperati. NPR-28944: Hotfix per CQ-4265014
* Se utilizzato con Multifield, CoralUI memorizza il parametro fileReferenceParameter a livello di componente anziché a livello di multicampo. NPR-29536: Hotfix per CQ-4266129
* Il riferimento alla progettazione non viene replicato in fase di pubblicazione dopo l’annullamento dell’ereditarietà in Importazione progettazione. NPR-29648, NPR-29721: Hotfix per CQ-4269270, CQ-4271087
* Il campo percorso nell’Editor Rich Text viene aperto nel percorso principale indipendentemente dal percorso specificato per la ricerca. NPR-29483: Hotfix per CQ-4268997
* (IE11) Copiare e incollare il contenuto HTML in un componente RTE con defaultPasteMode = plaintext non incolla il contenuto come testo normale. NPR-29432, NPR-29171: Hotfix per GRANITE-24941
* Il controllo ortografico dell’Editor Rich Text non funziona più in altre lingue. NPR-29506: Hotfix per CQ-4264990
* Script tra siti (XSS) nella pagina Campaign. NPR-29614: Hotfix per CQ-4269322
* Se si riduce a icona la finestra a schermo intero di Editor Rich Text nella modalità di modifica dell’origine, si verifica una perdita di contenuto. NPR-29574: Hotfix per CQ-4260584
* (Interfaccia classica) La navigazione all’ultima scheda non è sempre possibile quando sono presenti numerosi tag. NPR-29544: Hotfix per CQ-4264548
* (Interfaccia classica) Il menu di navigazione Admin Console scompare e la pagina non viene caricata completamente. NPR-29571: Hotfix per CQ-4264585
* Viene generato un avviso di errore durante l’aggiunta di componenti alla pagina WCM quando nell’istanza è abilitata la minificazione. NPR-29396: Hotfix per CQ-4266196
* Problema relativo all’ereditarietà dei nodi del sistema di stili dall’elemento padre. NPR-29296: Hotfix per CQ-4266041
* La pagina ripristinata con Timewarp deve fare riferimento all’immagine corretta al momento del controllo delle versioni.  NPR-29431: Hotfix per CQ-4262638
* Pagina vuota con errori Javascript nell&#39;editor dopo l&#39;installazione della versione più recente dello snapshot 6.4.5. NPR-29475: Hotfix per CQ-4266196
* Quando si aggiunge un componente a un parsys, la proprietà dell’elenco dei componenti di progettazione non viene rispettata e viene risolta in un nome di nodo di modello diverso con una struttura parsys simile. NPR-29509: Hotfix per CQ-4269044
* cq:dropTargets copre l&#39;intero componente invece delle dimensioni dell&#39;immagine, rendendo il targeting difficile con i componenti incorporati. NPR-29738: Hotfix per CQ-4268912
* Il componente immagine non chiama il listener &quot;after edit&quot; dopo l&#39;utilizzo dell&#39;editor in-place dell&#39;immagine. Hotfix NPR-29616 per CQ-4268065
* Problema durante la configurazione del post social su Facebook. NPR-29212: Hotfix per CQ-4266630
* Quando promuovi i lanci per le pagine modificate, vengono considerate le modifiche nei rami sia sorgente che lancio. NPR-29308: Hotfix per CQ-4266746
* La miniatura di cui è stato eseguito il rendering nel frammento di contenuto mostra la rappresentazione interna del calendario per il campo Data e ora. NPR-29531: Hotfix per CQ-4269362
* Impossibile aggiungere in massa un tag a pagine con tag diversi esistenti. NPR-28729: Hotfix per CQ-4262922
* L&#39;icona Activation pianificata non viene visualizzata nell&#39;amministratore del sito. NPR-28725: Hotfix per CQ-4263917

**Replica**

* Vulnerabilità alla divulgazione delle informazioni sensibili nel componente Agente di replica. NPR-29612, NPR-24951: Hotfix per GRANITE-25070
* I dati forniti dall’utente non sono preceduti dall’escape nell’output nel componente cq/replica/components/agent e causano la memorizzazione di una vulnerabilità cross-site scripting (XSS). Hotfix per CQ-4266263

**Frammenti esperienza**

* Impossibile esportare i frammenti di esperienza nella destinazione quando si utilizza l’immagine intelligente. Hotfix per CQ-4269606

**Social - Reporting**

* AEM rapporti della community non vengono visualizzati nell’istanza AEM autore. Hotfix per CQ-4266294

**Piattaforma**

* Script cross-site (XSS) nel gestore dei pacchetti durante l&#39;installazione di un pacchetto. NPR-29734, NPR-29713, NPR-29630: Hotfix per GRANITE-26161, GRANITE-
* Varie funzioni di scripting cross-site (XSS) memorizzate e riflesse in CRXDE Lite. NPR-29634: Hotfix per GRANITE-26049
* La funzionalità di accesso per Condivisione pacchetti utilizza una richiesta di GET anziché una richiesta di POST, rendendo la password visibile nella scheda di rete. NPR-29631: Hotfix per GRANITE-26048

**Felix**

* Script tra siti (XSS) osservato nella console di sistema. La pagina viene caricata e il pop-up si verifica quando il mouse passa sopra il campo di testo. NPR-29853, NPR-29633: Hotfix per GRANITE-26188, GRANITE-26050

**Granite**

* La configurazione del logger di registrazione Apache Sling non filtra lo script inserito.  NPR-29775: Hotfix per GRANITE-26051

**Community**

* I gruppi eliminati sull&#39;autore devono essere rimossi dalle istanze di pubblicazione. NPR-28933: Hotfix per CQ-4264645
* Il segreto dell&#39;app deve essere protetto con un campo password e non deve essere visualizzato in testo normale per gli strumenti di connessione social network. NPR-29728: Hotfix per CQ-4270480
* Visitatori e membri, senza privilegi di moderatore, possono visualizzare post non approvati/in sospeso incollando l&#39;URL. NPR-29726: Hotfix per CQ-4271124, CQ-4271441
* Durante l’accesso dell’utente alla community è possibile notare un tempo di risposta elevato, fino a 40-50 secondi. NPR-29678: Hotfix per CQ-4269444

**Traduzione**

* Gli utenti senza accesso alla funzione di traduzione nella navigazione non devono essere in grado di accedere alle relative sottopagine. NPR-29644: Hotfix per CQ-4269979
* Le autorizzazioni utente non supportate come procedura guidata consentono la creazione della copia di traduzione in un percorso di sola lettura. NPR-29375: Hotfix per CQ-4265877

**Interfaccia utente - Foundation**

* Il limite di impaginazione del risultato della ricerca è stato aumentato a 100 pagine per la vista a schede e a 200 per la vista a elenco. NPR-29332: Hotfix per GRANITE-24644
* A causa del caricamento lento dei tag, nella pagina della raccolta non viene visualizzato nulla. NPR-29267: Hotfix per GRANITE-24902
* Se si modifica il limite di impaginazione a 100 invece di 40, viene attivato un carico supplementare lento senza la richiesta di impaginazione. NPR-29246: Hotfix per GRANITE-25027
* AEM campo password granita non viene popolato dopo la crittografia. NPR-29245: Hotfix per GRANITE-24908

**Integrazione**

* Viene visualizzato un messaggio di eccezione quando si tenta di modificare e salvare la configurazione del lancio AEM. NPR-29086: Hotfix per CQ-4266153
* Credenziali BrightEdge non valide ed errore di connessione.  NPR-29167: Hotfix per CQ-4265872
* È necessario rimuovere la casella di controllo ereditata dalla visualizzazione al livello principale in Configurazioni Cloud Service. NPR-27856: Hotfix per CQ-4259676

**Sling**

* Il timeout della connessione HTTP non viene letto dalle configurazioni. NPR-29264: Hotfix per Sling-7902
* Il write-back del programma di installazione di JCR causa l&#39;utilizzo di un formato non valido nella configurazione di OSGi e il blocco della ridistribuzione. NPR-29027: Hotfix per CQ-4264694

**Progetti**

* Gli utenti non possono completare il flusso di lavoro del progetto. NPR-29621: Hotfix per CQ-4258791
* L’elenco Flusso di lavoro progetto mostra righe vuote oltre i 40 flussi di lavoro. NPR-28739: Hotfix per CQ-4264005
* Se scegli l’opzione Rendering dinamico in Brand Portal, viene scaricato un file .zip vuoto. NPR-29420: Hotfix per CQ-4268826
* La pubblicazione di risorse dalla cartella /content/dam/mac di AEM Author a Brand Portal non funziona. NPR-29820: Hotfix per CQ-4271118
* La punteggiatura nel nome causa problemi con il pulsante di pubblicazione. NPR-29573: Hotfix per CQ-4269317
* Impossibile creare la copia della lingua della risorsa tramite il pannello di riferimento. Hotfix per CQ-4269535

**Flusso di lavoro**

* L’aggiornamento da 6.4.2 a 6.4.4 interrompe il campo del selettore del calendario del partecipante alla finestra di dialogo. NPR-29727: Hotfix per CQ-4270423

**WCM - Interfaccia utente amministratore**

* L&#39;apertura della scheda delle autorizzazioni nell&#39;implementazione Coral2 non mostra i pulsanti. Hotfix per CQ-4269419

**WCM - MSM**

* Se si elimina un nodo figlio nella Live Copy, è necessario scollegare liveRelationship. Hotfix per CQ-4270395
* Con l’aggiornamento ad AEM 6.4.3 il rollout dell’utilità di gestione di più siti richiede molto tempo. Hotfix per CQ-4271410

**Vulnerabilità**

* Il framework di protezione CSRF non funziona con i moduli di AEM Foundation. NPR-28612: Hotfix per GRANITE-22231

**WCM - Editor pagina**

* Vulnerabilità cross-site scripting (XSS) rilevabile quando si utilizza un selettore non valido. Hotfix per CQ-4270397

**Forms**

Elementi di rilievo di AEM 6.4.5.0 Forms:

**Pacchetto di componenti aggiuntivi per Forms**

**Moduli adattivi**

* (Interfaccia touch) L’opzione Avvia flusso di lavoro non apre la finestra di dialogo per la configurazione. NPR-29521: Hotfix per CQ-4269050

**Forms - Integrazione back-end**

* Abilitazione del supporto per ADFS (Active Directory Federation Services) v3.0 per l’integrazione On-Premise di Microsoft Dynamics. NPR-30003, NPR-29484: Hotfix per CQ-4270586
* Il servizio di precompilazione non riesce a causa del tempo di consegna prolungato dal modulo di integrazione dei dati di AEM Forms. NPR-28997: Hotfix per CQ-4265988
* Richiesta di servizio Web SOAP non valida in AEM Forms. NPR-29013: Hotfix per CQ-4265443
* Durante il test del servizio SOAP non viene visualizzato alcun messaggio di errore in caso di valore di data errato. Hotfix per CQ-4265445

**Forms - Comunicazione interattiva e Forms - Gestione della corrispondenza**

* L’interfaccia utente Crea corrispondenza (interfaccia utente CCR) non riesce a gestire un numero mobile.  NPR-29210: Hotfix per CQ-4254201
* La descrizione comando impostata su una variabile non è visibile nell’interfaccia utente Crea corrispondenza (interfaccia utente CCR). NPR-29739: Hotfix per CQ-4250533
* Impossibile copiare o incollare da Omnisearch all’interno di lettere. NPR-29808: Hotfix per CQ-4270783

**Moduli HTML5**

* Quando si aggiunge uno spazio all’interno del testo, il campo di testo non consente di riempire fino alla fine. NPR-28844: Hotfix per CQ-4260239

**Programma di installazione di JEE per Forms**

**Forms - JEE di base**

* Il componente Servizio Web in AEM Forms Workbench non è in grado di richiamare un servizio Web che richiede l’autenticazione SSL bidirezionale. NPR-29485: Hotfix per CQ-4246794
* AEM Forms JEE configuration manager non funziona con più schede NIC. NPR-29236: Hotfix per CQ-4268598
* AEM errore di avvio proveniente da GemFire: java.lang.IllegalStateException: È possibile effettuare una sola connessione AdminDistributedSystem alla volta. NPR-29524: Hotfix per CQ-4266295
* NoClassDefFoundError a causa di una mancata corrispondenza della versione jar. NPR-28834: Hotfix per NPR-28834

**Forms - Servizi basati su documenti**

* Il file PDF/A non valido viene riportato come PDF/A valido utilizzando l&#39;operazione isPDFA. NPR-29076: Hotfix per CQ-4261541
* La conversione di PDF in PDF/A-1b non riesce con il campo Modulo senza il codice di aspetto. NPR-29534: Hotfix per CQ-4269618
* La conversione PDF/A da PDF prodotta con il servizio di output non passa la convalida con Acrobat DC. NPR-29647: Hotfix per CQ-4270448
* Il bundle Apache POI fallisce con un&#39;eccezione. NPR-27861, NPR-28048: Hotfix per CQ-4245898, CQ-4244778

**Forms - Designer**

* È stato aggiunto il supporto di PDF/UA ai moduli XFA (XML Forms Architecture) generati utilizzando Designer e Output Service. NPR-23022

**Forms - Flusso di lavoro**

* L&#39;invio dall&#39;area di lavoro non riesce con il carattere Umlaut. NPR-29087: Hotfix per CQ-4263172

**Feature Pack inclusi**

**Risorse**

* Abilitazione del supporto per l’utilità di gestione di più siti per Assets. Per ulteriori informazioni, consulta [Riutilizzare le risorse con MSM per le risorse](/help/assets/reuse-assets-using-msm.md). NPR-26450: Hotfix per CQ-4259922

**Bundle OSGi e pacchetti di contenuti inclusi**

Nei documenti di testo seguenti sono elencati i bundle OSGi e i pacchetti di contenuti inclusi nel CFP.

Elenco dei bundle OSGi inclusi in AEM 6.4.5.0

[Ottieni file](assets/6.4.5.0_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.5.0

[Ottieni file](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio di AEM 6.4 in **Aprile 2018.**

È anche cumulativo, il che significa che 6.4.4.0 include tutte le versioni di Service Pack 6.4 AEM prima di esso.

Alcuni degli elementi di rilievo di AEM 6.4.4.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.11.
* È stato aggiunto il supporto per la versione del servizio di caching per evitare richieste HTTP frequenti sulla versione del servizio.
* È stato aggiunto il supporto per l’eliminazione dei tag automatici.
* Implementazione dello scorrimento continuo per la procedura guidata catalogo.
* Possibilità di limitare le autorizzazioni in base ai siti della community.
* Correzioni delle prestazioni (caching, esecuzione asincrona, elenco di esclusione) per Sling Granite Content Health Check.
* Pulsante assetpicker aggiunto alla finestra di dialogo pagethumbnail .
* È stata aggiunta una nuova proprietà per consentire il posizionamento della descrizione comando sui campi.
* È stato migliorato il supporto di ColorPicker all’interno del campo Multifield.
* È stato aggiunto un controllo per ignorare i valori vuoti per i campi multipli di input numerici nelle clientlibs del frammento di contenuto.
* Abilitazione del supporto per l’API di testo di Microsoft Translator v3.

**Risorse**

* Migrazione dell’integrazione di ACP e Stock a AEM 6.4.4.0 NPR-27632
* Pubblica più tardi una cartella di risorse vuota con sottocartelle che scompare. NPR-27558: Hotfix per CQ-4254701
* L&#39;aggiunta della proprietà String\[\] senza namespace Single non causa un writeback XMP incompleto. NPR-26805: Hotfix per CQ-4254142
* Dopo aver rasterizzato il pdf di ingresso, l&#39;output prodotto ha immagini mancanti. NPR-27929: Hotfix per CTG-4150481
* Spostamento guidato risorse mostra un numero errato di pagine di riferimento per le pagine pubblicate. NPR-27833: Hotfix per CQ-4258014
* AssetPicker cerca solo il primo tag per filtrare il risultato quando si filtrano i tag. NPR-27778: Hotfix per CQ-4257705
* AEM gestore OOTB PDF si blocca durante l&#39;elaborazione di PDF con caratteri stranieri. NPR-28778: Hotfix per CQ-4254234
* Quando un file CSV ha un valore separato da virgole in una singola colonna, AEM editor CSV non esegue l’escape della virgola e la tratta come una colonna separata. NPR-28801: Hotfix per CQ-4261694
* Problema con l’Editor schema metadati durante l’utilizzo del Browser percorsi per selezionare i dati. NPR-28674: Hotfix per CQ-4263005
* Troppe risorse vengono elaborate dal Servizio di contenuti avanzati e il processo di assegnazione tag periodica richiede molto tempo. NPR-28640: Hotfix per CQ-4262661, CQ-4262644, CQ-4263234
* Le azioni desktop non funzionano per i risultati Omnisearch da `aem/start.html` pagina. NPR-27242: Hotfix per CQ-4248176
* L’API delle risorse non consente il caricamento di file > 2 GB, causando un errore di caricamento. NPR-27629: Hotfix per GRANITE-23590
* I metadati non vengono salvati nella risorsa scaricata al primo tentativo nel caso in cui Dynamic Media sia abilitato nell’istanza. NPR-28233: Hotfix per CQ-4260759
* Il risolutore del servizio non è chiuso nella configurazione del SiteCatalyst. NPR-28015: Hotfix per CQ-4259397
* Lo spostamento delle risorse in DAM non si traduce in uno spostamento simile su Scene7 (configurazione p2p). NPR-28313: Hotfix per CQ-4261091

**Sites**

* (Interfaccia classica) Una frazione delle Live Copy viene visualizzata nell’elenco di rollout. NPR-28598, NPR-28574: Hotfix per CQ-4263410
* LiveRelationshipManagerImpl genera eccezioni quando cq:master è vuoto o non valido. NPR-28590: Hotfix per CQ-4263115
* Il flusso di lavoro &quot;Richiesta di cancellazione&quot; predefinito non elimina correttamente le pagine. NPR-28668: Hotfix per CQ-4263195
* L’interfaccia utente Stato relazione non mostra i valori anno o timestamp corretti per i campi relativi di visualizzazione dati coral-datepicker. NPR-28666: Hotfix per CQ-4263661
* Vulnerabilità cross-site scripting (XSS) in SuggestionHandler per la versione 6.4. NPR-28693: Hotfix per CQ-4253821
* La cartella Sposta da siteadmin termina con una memoria esaurita e rende AEM non disponibile. NPR-28346: Hotfix per CQ-4261398
* Le configurazioni di rollout di MSM LiveCopy vengono perse dopo l’aggiornamento. NPR-28311: Hotfix per CQ-4258705
* Impossibile scorrere oltre 40 configurazioni blueprint. NPR-27640: Hotfix per CQ-4239166
* L&#39;utilizzo di SyntheticResource come riferimento genera un&#39;eccezione Null Pointer e blocca lo spostamento delle pagine.  NPR-27576: Hotfix per CQ-4258262
* Il pushOnModify non funziona all&#39;eliminazione dell&#39;istanza aggiornata da 6.1 a 6.4. NPR-28108: Hotfix per CQ-4259833
* (Interfaccia classica) Il pulsante Annulla ereditarietà è mancante e il componente è modificabile in una pagina Live Copy. NPR-28256: Hotfix per CQ-4260161
* OakState0001: Conflitti irrisolti in Rollout. NPR-27982: Hotfix per CQ-4259548
* Quando si copia/incolla una struttura contenente riferimenti SyntheticResource, il processo termina con un errore 500. NPR-27709: Hotfix per CQ-4259179
* Impossibile terminare i flussi di lavoro in esecuzione quando i payload sono attivati. NPR-27672: Hotfix per CQ-4258520
* Il rollout mostra percorsi di rollout duplicati dopo l’aggiornamento da 6.1 a 6.4. NPR-27845: Hotfix per CQ-4259487
* Integra dam assetpicker modale nel componente di miniatura della pagina. NPR-28131: Hotfix per CQ-108042
* (Interfaccia classica) Impossibile aprire le finestre di dialogo con il widget Tag. NPR-28575: Hotfix per CQ-4262680
* Il caricamento di file multicampo non mostra la zona di rilascio. NPR-28676: Hotfix per CQ-4263516
* Errore di tipo “Valore del selettore di ricorsione non valido” durante la migrazione di un componente da AEM 6.0 a AEM 6.2. NPR-28609: Hotfix per CQ-4241258
* L’editor Rich Text nella finestra di dialogo si attiva quando il pover di un plug-in è più alto dell’area di testo, bloccando quindi qualsiasi ulteriore authoring. NPR-27579: Hotfix per CQ-4257440
* (Interfaccia classica) cq:action edit annotate non funziona. NPR-28232: Hotfix per CQ-4257703
* La rimozione dei tag dal pannello di ricerca delle risorse del filtro dei tag nell’editor di pagine non aggiorna l’elenco correttamente. NPR-27983: Hotfix per CQ-4245567
* Se i valori del numero di campi multipli sono vuoti, facendo clic su Salva si otterrà un prompt di caricamento infinito senza essere completato.  NPR-28400, NPR-28393: Hotfix per CQ-4244058, CQ-4244349
* Con il permesso di lettura, gli utenti/gruppi non sono in grado di selezionare un XF e non hanno alcuna opzione per visualizzare il XF e le sue proprietà di pagina. NPR-28341: Hotfix per CQ-4260412
* I dati JSON ricevuti da Target hanno una serie di caratteri di escape che causano l’interruzione della pagina dell’applicazione. NPR-28318: Hotfix per CQ-4252043
* Impossibile modificare alcun componente dopo l&#39;installazione di AEM 6.4.3. NPR-28125: Hotfix per CQ-4261216
* L’eliminazione di tutti i tag per un campo tag non viene mantenuta per un frammento di contenuto strutturato. NPR-28133: Hotfix per CQ-4247241
* Durante la modifica di una proprietà dei frammenti di contenuto &quot;jcr:lastmodiedby&quot; e &quot;jcr:lastmodified&quot;, i valori vengono aggiornati senza che l’utente apporti modifiche. NPR-27847: Hotfix per CQ-4257138
* Il controllo delle versioni dei frammenti di contenuto confronta i miglioramenti delle differenze per AEM 6.4. NPR-27764
* Se nel modello Frammento esperienza non è definito alcun cq:allowedTemplates su /content/experience-fragments e allowedPaths è utilizzato, viene generato un errore quando il Frammento esperienza viene spostato/copiato. NPR-27487: Hotfix per CQ-4257489
* All’aggiornamento del nuovo utente viene visualizzato il pulsante Crea . NPR-27335: Hotfix per CQ-4255360
* Durante il tentativo di spostare una pagina pubblicata, il conteggio &quot;Pagine di riferimento&quot; visualizzato nella prima pagina della procedura guidata &quot;Sposta pagina&quot; non è corretto. NPR-28111: Hotfix per CQ-4259663
* (Interfaccia touch) La barra laterale Riferimenti non mostra i collegamenti in entrata. NPR-28529: Hotfix per CQ-4262306
* Impossibile modificare le proprietà dei componenti e della pagina dopo l&#39;installazione di AEM 6.4.3. NPR-27998: Hotfix per CQ-4261216, CQ-4260441
* È stata eseguita la migrazione di contexthub a jquery 3. NPR-28397: Hotfix per GRANITE-19902

**Commerce**

* Impossibile selezionare il catalogo se sono presenti più di 20 cataloghi in una cartella. NPR-27649: Hotfix per CQ-4258119
* Le visualizzazioni delle procedure guidate e delle proprietà di Commerce sono interrotte a causa di header.referer mancante. Hotfix per CQ-4261122

**Campaign - Targeting**

* com.day.cq.personalization.impl.TeaserResourceEventHandler entra in un ciclo infinito e causa aggiornamenti ai nodi sulle istanze di pubblicazione. Hotfix per CQ-4263096

**Replica**

* Errore durante la creazione del contenuto di replica com.day.cq.replication.AccessDeniedException. NPR-28314: Hotfix per CQ-4261401
* Perdita di sessione quando l&#39;ID dell&#39;agente utente è impostato su admin nell&#39;agente di replica. NPR-28220: Hotfix per CQ-4255517

**DAM - Creative Cloud**

* Esegui il backup dell’API HTTP per trovare immagini simili da AEM Assets. Hotfix per CQ-4254091
* Ottimizza l’API ACP per consentire che i risultati di una query siano limitati ai membri di una raccolta. Hotfix per CQ-4258708

**DAM - Formati**

* Dopo l’attivazione dell’esportazione dei metadati, la pagina viene reindirizzata a una pagina 404. Hotfix per CQ-4262447

**DAM - Generale**

* (Integrazione Adobe Stock) Il modale di errore del server viene visualizzato con un errore Oauth nel file error.log. Hotfix per CQ-4260406
* L&#39;integrazione di Adobe Stock non funziona se la versione 6.4.4 è applicata alla versione 6.4.3. Hotfix per CQ-4266009
* Il collegamento al modello CF è mancante anche dopo l’applicazione della patch SP3. Hotfix per CQ-4259029

**Piattaforma**

* (Interfaccia classica) Il pulsante di modifica non è disponibile nel componente Rapporto di base dopo l’aggiornamento alla versione 6.4.2. NPR-28560: Hotfix per CQ-4262825
* Quando si utilizza una query che combina property.operation=like e property.depth, si finisce in un InvalidQueryException. NPR-28570: Hotfix per CQ-4262652
* Errore interno del server quando il nodo della lingua appena aggiunto viene rimosso dal nodo della lingua sovrapposto. NPR-28661: Hotfix per CQ-4239194
* Eccezione Null Pointer in stderr.log nel thread sling-oak-1 su avvii casuali. NPR-28665: Hotfix per CQ-4237845

**Felix**

* webconsole.plugins.memoryusage causa un deadlock all&#39;aggiornamento. NPR-27895: Hotfix per GRANITE-20715

**Granite**

* Sling Content Access Health Check esegue una lunga e eccessiva convalida /libs per il percorso di ricerca personalizzato del risolutore di risorse. NPR-28113: Hotfix per GRANITE-23529

**Gestione dei frammenti di contenuto**

* Miglioramenti a livello di usabilità e parità di funzioni con le risorse per i frammenti di contenuto. Hotfix per CQ-4253883

**Community**

* Aggiorna il bootstrap vulnerabile a 3.4 e le librerie ckeditor a 4.5.11. NPR-28490: Hotfix per CQ-4257511
* L&#39;annullamento delle modalità di modifica non ripristina l&#39;allegato eliminato. NPR-27902: Hotfix per CQ-4255150
* La composizione per conto di box deve essere visibile solo ai membri privilegiati. NPR-27900: Hotfix per CQ-4251235
* Aggiungi rep:cache nei nodi ignorabili in AEM Communities User Sync Listener sulle istanze di pubblicazione. NPR-27842: Hotfix per CQ-4247234
* La casella di ricerca mostra il carattere di escape a livello di interfaccia utente. NPR-27838: Hotfix per CQ-4259757
* Viene generato un errore durante la ricerca di caratteri speciali come ( , +,? in ricerca rapida. NPR-28213: Hotfix per CQ-4260969
* Crea un gruppo di amministratori &quot;specifici della community&quot; per consentire agli utenti di modificare e creare il sito della community pertinente. NPR-27731
* È stata aggiunta una logica per l’evento della tastiera per aprire il video. NPR-27726: Hotfix per CQ-4254026
* Attivazione della navigazione tramite tastiera per i componenti di Attivazione per AEM Communities durante la pubblicazione. NPR-27728: Hotfix per CQ-4254028
* Aggiunta dell’attributo aria-label per il pulsante della vista a elenco e a schede. NPR-27727: Hotfix per CQ-4254027
* Gestione delle sessioni del risolutore di risorse aperte in Social - Communities. NPR-27721: Hotfix per CQ-4258714

**Traduzione**

* Fornisci il supporto per l’API di testo di Microsoft Translator v3. NPR-28366: Hotfix per CQ-4249755
* jcr:language e cq:language non vengono aggiornati automaticamente nella lingua tradotta. NPR-28338: Hotfix per CQ-4256046
* I riferimenti ciclici causano StackOverflowError durante la creazione della copia della lingua. NPR-27596: Hotfix per CQ-4255621
* In un progetto di traduzione multilingue, se si fa clic su Salva e chiudi i risultati nelle pagine successive aggiunte al progetto, vengono creati nuovi progetti invece che nuovi lavori di traduzione nel progetto esistente. NPR-28219, NPR-28236: Hotfix per CQ-4261276, CQ-4260731
* Stringa di errore troppo lunga quando si aggiunge un frammento di contenuto con dati in blocco a causa di una limitazione del numero di caratteri consentiti. NPR-28722: Hotfix per CQ-4262362

**Social network**

* Il commento pubblicato nella pagina successiva viene evidenziato in giallo ogni volta che viene pubblicato un nuovo commento. Hotfix per CQ-4261359
* Impossibile utilizzare l’API per eliminare i commenti nei contenuti generati dagli utenti (UGC, User-Generated Content). NPR-28075: Hotfix per CQ-4261135
* AbstractNotificationOperationService causa ClassCastException. Hotfix per CQ-4260456
* Rimozione del riferimento al cloud SCORM (Shared Content Object Reference Model) nel lettore. Hotfix per CQ-4260779

**Interfaccia utente - Foundation**

* La funzione &quot;Filesystem output cache&quot; integrata in HTML Client Library Manager interrompe la funzione &quot;debugClientLibs&quot; per gli script compilati come i file LESS. NPR-27249: Hotfix per GRANITE-23313
* Il numero di risorse visualizzate quando la modalità di debug viene attivata è sempre 1 e molti errori JS vengono lanciati nella console del browser.  NPR-27575: Hotfix per GRANITE-23750
* Il salvataggio e la chiusura delle proprietà di pagina non torna alla pagina corretta in AEM WAR con Tomcat. NPR-27566: Hotfix per GRANITE-23671

**Integrazione**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` genera un ciclo infinito e causa aggiornamenti ai nodi nelle istanze di pubblicazione. NPR-28561: Hotfix per CQ-4263096
* Le azioni  cq  :actions non vengono considerate per un componente di destinazione. NPR-27616: Hotfix per CQ-4257497
* L’annullamento dell’ereditarietà Live Copy non funziona correttamente sui contenitori di destinazione. NPR-28129: Hotfix per CQ-4259813
* (Configurazioni servizi cloud) La casella di controllo “Ereditato da” visualizzata al livello principale deve essere rimossa. NPR-27856: Hotfix per CQ-4259676

**Sling**

* Aggiornamento a Sling Models API 1.3.8, Impl 1.4.10. NPR-27636: Hotfix per GRANITE-23537

**OAK - Persistenza del segmento**

* SegmentBufferWriter non scaricato dopo OnRC. NPR-27464

**Progetti**

* Il progetto di traduzione multilingue non sta creando più processi in lingua per gli utenti che non fanno parte del gruppo di amministratori. NPR-28508: Hotfix per CQ-4262023
* ProjectTaskListServlet perde un ResourceResolver ogni volta che viene chiamato getTaskRenderers durante l&#39;avvio del servizio. NPR-27590: Hotfix per CQ-4258011
* Se una directory ha più sottodirectory rispetto alle dimensioni della pagina e l&#39;ordine è in base alla data o alle dimensioni, un errore impedisce di spostarsi oltre la prima pagina. NPR-28867: Hotfix per CQ-4265039
* Correzioni di vulnerabilità cross-site scripting (XSS) in DAM Viewers. NPR-28106: Hotfix per CQ-4253215
* Impossibile aggiungere pagine al progetto di traduzione da parte degli amministratori del progetto, in quanto il collegamento per aggiungere nuove pagine al progetto di traduzione non è visibile. Hotfix per CQ-4266334

**Flusso di lavoro**

* Quando si apre la finestra di dialogo dell’elemento di lavoro completo nella notifica del flusso di lavoro che dispone di un campo Tag , facendo clic sul segno di spunta si aggiunge una proprietà Tag. NPR-28304: Hotfix per CQ-4261321
* Il pulsante di attivazione/disattivazione selezione utente nella finestra di dialogo Riassegna attività non funziona. NPR-28963: Hotfix per CQ-4264206

**Forms**

Elementi di rilievo di AEM 6.4.4.0 Forms:

* È stato aggiunto il supporto per registrare le API di sicurezza dei documenti per la firma e la certificazione come transazioni.

**Pacchetto di componenti aggiuntivi per Forms**

**Integrazione Adobe Sign**

* AEM 6.4 Forms Client SDK non contiene il pacchetto adobesign-recipent. NPR-27735: Hotfix per CQ-4259372

**Moduli adattivi**

* Quando si crea un modulo adattivo Wan con un modello vuoto, i clienti non possono aggiungere pannelli secondari al pannello principale del modulo. NPR-28758: Hotfix per CQ-4264157
* Se il valore del componente Campo anno della data è 9999, lo script di convalida non riesce. NPR-28580: Hotfix per CQ-4262620
* Quando si crea un modulo adattivo con un modello vuoto, i clienti non possono aggiungere pannelli secondari al pannello principale del modulo. NPR-28758: Hotfix per CQ-4264157
* Impossibile impostare il valore tra i campi dei frammenti caricati pigri di un modulo adattivo. NPR-27758: Hotfix per CQ-4259703
* Il modulo adattivo non utilizza l’editor Rich Text, ma ne carica le librerie.  NPR-27759: Hotfix per CQ-4259193
* Il reindirizzamento all’URL non funziona per i moduli adattivi incorporati in una pagina AEM Sites. NPR-27620: Hotfix per CQ-4239287
* Impossibile impostare il valore tra i campi dei frammenti caricati pigri di un modulo adattivo. NPR-28320: Hotfix per CQ-4262345
* Il modulo adattivo non utilizza l’editor Rich Text, ma ne carica le librerie.  NPR-28001: Hotfix per CQ-4259703, CQ-4259193
* La firma digitale non funziona per l’app AEM Forms in esecuzione su Apple iOS 12.1. NPR-28497: Hotfix per CQ-4261765
* Invia un’azione utilizzando i problemi di authoring &quot;Forms Workflow&quot; Classic in 6.4. Hotfix per CQ-4252740
* Errore durante la gestione del blocco e la rimozione dell&#39;archiviazione tmp. NPR-28806: Hotfix per CQ-4264441

**Forms - Gestione della corrispondenza**

* L&#39;interfaccia utente dell&#39;agente non mantiene le dimensioni originali dell&#39;immagine. NPR-28800: Hotfix per CQ-4259767
* Interfaccia utente CCR/Agente: Etichette dei campi data spostate nella scheda Dati. Hotfix per CQ-4255499

**Forms - Reporting delle transazioni**

* È stato aggiunto il supporto per il conteggio tramite firme digitali o la certificazione di un documento come transazioni fatturabili. NPR-28495: Hotfix per CQ-4260236
* È stata aggiunta la firma digitale e la certificazione all’API fatturabile. Hotfix per CQ-4260236

**Gestione Forms**

È stato aggiunto il supporto per sostituire l’utilizzo della libreria client handlebars con underscore nella procedura guidata di revisione di Forms Manager e nella procedura guidata per lo spostamento delle risorse. NPR-27643: Hotfix per CQ-4246536.
Un bundle rimane in stato di installazione dopo l&#39;installazione del pacchetto Forms Management sul ramo release/640. L&#39;Hotfix per CQ-4265410 Forms inviato con gli allegati non viene visualizzato nel flusso di lavoro con l&#39;azione di invio &quot;Richiama flusso di lavoro AEM Forms&quot; e abilita l&#39;invio del portale selezionato . Hotfix per CQ-4263110

**Forms - Integrazione back-end**

* Impossibile eseguire il test del preprocessore/post e l&#39;invio personalizzato tramite Client SDK, Hotfix per CQ-4238469

**Programma di installazione di JEE per Forms**

**Forms - Sicurezza dei documenti**

* Quando si utilizza il servizio updatepolicy, si verifica l&#39;errore di oggetti non coerenti. NPR-28751: Hotfix per CQ-4252287
* Errore nella creazione della firma con la versione precedente di commons-pkg. Hotfix per CQ-4265535

**Forms - JEE di base**

* Quando AEM Forms è abilitato su IBM WebSphere, la creazione di un modello dati modulo basato su SOAP non riesce. NPR-27923: Hotfix per CQ-4251134
* Lo strumento SRT di PDF Generator non rileva la versione installata di Adobe Acrobat. NPR-27971

**Forms - Designer**

* Alcune immagini JPEG in un modello XDP non vengono renderizzate correttamente.  NPR-26702: Hotfix per LC-3917457

**Forms - Flusso di lavoro**

* HTML5 Forms con processo di invio predefinito in an.lca non funziona su JBoss 7. NPR-28675: Hotfix per CQ-4243928
* Impossibile inviare PDF forms in HTML Workspace. NPR-28058: Hotfix per CQ-4260373
* I dati del cliente vengono stampati nei registri delle informazioni utilizzando il Forms Workflow di servizi FDM di Invoke. Hotfix per CQ-4260385

**Feature Pack inclusi**

**Sites**

* Il controllo delle versioni dei frammenti di contenuto confronta i miglioramenti delle differenze per AEM 6.4. NPR-26760: FP per CQ-4248839
* Miglioramenti alle differenze di variazione dei frammenti di contenuto per AEM 6.4. NPR-27866: FP per CQ-4248839
* Funzione abilitata nella configurazione OSGI **Flag di funzione Ritiro flusso di lavoro AEM**. L’azione di ritiro deve terminare l’istanza del flusso di lavoro dopo aver impostato il flag . NPR-26451: Hotfix per CQ-4259090

**Piattaforma**

* Estrazione facet di Query Builder migliorata sfrutta l’API Oak per 6.4. NPR-26674: FP per CQ-4230337

**Bundle OSGi e pacchetti di contenuti inclusi**

Nei documenti di testo seguenti sono elencati i bundle OSGi e i pacchetti di contenuti inclusi nel CFP.

Elenco dei bundle OSGi inclusi in AEM 6.4.4.0

[Ottieni file](assets/bundles_6_4_4_0.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.4.0

[Ottieni file](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

AEM 6.4.3.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio della versione 6.4 di AEM nell’aprile 2018.

È anche cumulativo, il che significa che 6.4.3.0 include tutte le versioni di Service Pack 6.4 AEM prima di esso.

Alcuni degli elementi di rilievo di AEM 6.4.3.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.9.
* È stato aggiunto il supporto per la proprietà allowedPaths sui modelli di moduli adattivi.
* Ricerca ottimizzata basata su pannelli per le risorse in AEM
* Correzioni di vulnerabilità cross-site scripting (XSS) nella pagina di accesso.
* È stata migliorata la strumentazione dell’interfaccia utente.
* Miglioramenti nella gestione di FormData.
* È stata migliorata la gestione della denominazione degli elementi all’interno di un campo multiplo.
* È stata migliorata la gestione degli elementi segnaposto (vista a schede e vista a elenco) durante la selezione.
* È stata aggiunta l’autenticazione Adobe IMS e il supporto per Admin Console per Managed Services.

**Risorse**

* Il flusso di lavoro Risorsa di aggiornamento DAM non estrae riferimenti dai file INDD se l’opzione Disaccoppiamento IDS è abilitata. NPR-26243; Hotfix per CQ-4250933
* Il messaggio di successo non viene visualizzato quando le risorse vengono pubblicate con Assets Bulk Editor. NPR-26252; Hotfix per CQ-4251688.
* Dopo aver guardato una risorsa da un risultato della ricerca, se fai clic sul pulsante Indietro nel browser, si genera un messaggio di errore &quot;Bad Request&quot; con codice di errore 400. NPR 26578; Hotfix per CQ-4253741
* I metadati della risorsa mostrano un errore dello spazio dei nomi non valido dopo l&#39;installazione di un service pack. NPR-22341; Quickfix per CQ-4237202
* L’opzione per riordinare cartelle e frammenti di contenuto nella visualizzazione a elenco non viene visualizzata per le cartelle applicabili. NPR-27153; Hotfix per CQ-4255873
* Gli utenti non possono aggiungere risorse a una nuova raccolta, in quanto si verifica un messaggio di errore con un’immagine interrotta nella finestra di dialogo a comparsa degli errori. NPR-22431; Hotfix per CQ-4237086
* Il menu a discesa a cascata non è supportato negli elenchi a discesa dinamici. NPR-27043; Hotfix per CQ-4252564
* Se gli utenti impostano un valore non predefinito per la &quot;Cartella principale società&quot; nella configurazione cloud DMS7, il predefinito visualizzatore non funziona come previsto. NPR-26360; Hotfix per CQ-4249505
* La generazione di rapporti sulle risorse non riesce per le istanze con un numero molto elevato di risorse. NPR-27278; Hotfix per CQ-4256748
* Le sottocartelle non ereditano il profilo immagine SmartCrop della cartella principale. NPR-27197; Hotfix per CQ-4256273
* Quando l’integrazione di Dynamic Media è abilitata, alcune proprietà dei metadati di Assets vengono modificate. Gli attributi di larghezza, altezza e posizione non vengono visualizzati. NPR-27203; Hotfix per CQ-4256258
* Dynamic Media non utilizza il proxy configurato per alcuni tipi di risorse. NPR-25211; Hotfix per CQ-4244871
* La pagina Editor metadati contiene un&#39;eccezione Null Pointer per il parametro dell&#39;elemento non valido. NPR-26169; Hotfix per CQ-4241368.
* Se a un menu a discesa è applicata una regola di scelta e una regola obbligatoria, la regola richiesta non può essere soddisfatta nell’editor di metadati. NPR-27479; Hotfix di CQ-4251428

**Sites**

* Un utente può controllare le funzioni dell’editor Rich Text in modalità a schermo intero in linea utilizzando i criteri dei contenuti, ma non può controllare le funzioni dell’editor Rich Text della finestra di dialogo Modifica con i criteri dei contenuti. NPR-26750: Hotfix per CQ-4241130
* L’editor Rich Text diventa inutilizzabile quando si passa da una finestra di dialogo a schermo intero a una mobile. La visualizzazione mobile contiene due editor Rich Text. NPR-25589: Hotfix per CQ-4206008
* Quando si preme il tasto Invio in un campo di testo, l’editor Rich Text passa alla modalità a schermo intero. NPR-26204: Hotfix per CQ-4245893
* Il plug-in elenco dell’editor Rich Text viene disabilitato automaticamente e non consente modifiche. NPR-26507: Hotfix per CQ-4239387
* Quando si aggiunge un carattere speciale alla finestra dell’editor Rich Text, la finestra scorre verso l’alto. NPR-26435: Hotfix per CQ-4249869
* Domande sui casi in cui adottare o meno la memorizzazione in cache per segment.js in ClientContext. NPR-26622: Hotfix per CQ-4253486
* Quando una regola figlio viene attivata dall&#39;istanza dell&#39;autore all&#39;istanza di pubblicazione, l&#39;istanza di pubblicazione smette di funzionare. NPR-26601: Hotfix per CQ-4253588
* Quando si combina l’Editor Rich Text con più campi, si verifica un errore di tipo “TypeError non rilevato: fieldAPI.getName non è una funzione in foundation.js”. NPR-27146: Hotfix per CQ-4253155
* L&#39;integrazione Salesforce non è in grado di utilizzare la configurazione proxy. NPR-27244: Hotfix per CQ-4245300
* Quando pianifichi l’attivazione di una pagina utilizzando l’opzione Gestisci pubblicazione per una data successiva e passi alla vista a elenco, manca l’icona Calendario. NPR-26974: Hotfix per CQ-4239206
* Gli utenti non possono modificare le autorizzazioni per gruppi di utenti chiusi nelle proprietà della pagina. NPR-27138: Hotfix per CQ-4256089 Impossibile modificare i tag tramite tag. NPR-26957: Hotfix per CQ-4254858
* Quando si sposta un tag a cui fa riferimento un modello di frammento di contenuto strutturato, i riferimenti esistenti al tag all’interno di un frammento di contenuto non vengono aggiornati. Questo accade nella schermata di modifica del modello di frammento di contenuto. NPR-26776: Hotfix per CQ-4251805
* Quando crei e promuovi un lancio con più pagine, viene creata più versioni per ogni pagina. NPR-26917: Hotfix per CQ-4254663
* AEM siteadmin non gestisce i percorsi digitati nella barra degli indirizzi del browser. NPR-26780: Hotfix per CQ-4254097
* Quando una pagina viene spostata in una nuova posizione senza rinominarla, la cronologia delle versioni della pagina viene persa. NPR-26706: Hotfix per CQ-4254025
* Gli URL nell’editor per l’amministrazione dei frammenti di esperienza non consentono sovrapposizioni. NPR-26319: Hotfix per CQ-4252156
* Quando una pagina viene creata con un modello contenente un frammento di esperienza vuoto e viene pubblicata, la pagina non si apre e si verifica un errore DefaultSlingScript. NPR-26305: Hotfix per CQ-4252460
* Quando si utilizza data-sly-use con classi con lo stesso nome, viene prodotto codice non conforme. NPR-27282: Hotfix per Sling-7581
* Dopo l&#39;installazione dell&#39;SP di aggiornamento, i siti dispongono di una configurazione di rollout blueprint vuota. NPR-27609: Hotfix per CQ-4257078

**DAM - Brand Portal**

* I predicati tag non vengono pubblicati quando il modulo schema metadati viene pubblicato in Brand Portal. Hotfix per CQ-4256218
* Quando una cartella di terzo livello viene pubblicata da AEM a Brand Portal senza pubblicare le cartelle principali, il nome della cartella cambia. Hotfix per CQ-4255423
* Il predicato del browser percorsi viene pubblicato da AEM Assets a Brand Portal come previsto. Tuttavia, il percorso pubblicato su BP rimane /content/dam, che deve essere aggiornato. Hotfix per CQ-4256240

**DAM - Creative Cloud**

* Icona &quot;Ricerca risorse Adobi&quot; mancante dalla navigazione principale AEM. Hotfix per CQ-4254343

**DAM - Client DM**

* Dopo aver acquisito i video in una cartella associata al profilo di elaborazione video AVS, la finestra del browser si aggiorna più e più volte. Hotfix per CQ-4253563
* La pubblicazione di YouTube non riesce quando si utilizza un tag Ad Hoc che include caratteri maiuscoli. Hotfix per CQ-4252477
* Quando un’annotazione viene creata in una risorsa come PDF, l’interfaccia utente inizia un ciclo infinito di aggiornamento della pagina. NPR-27052: Hotfix per CQ-4255396

**DAM - Servizi DM**

* Dynamic Media non utilizza il proxy configurato per alcuni tipi di risorse. NPR-10727; Hotfix per CQ-4244871

**Piattaforma**

* Problemi di prestazioni con org.apache.sling.i18n. NPR-26812: Hotfix per Sling-7543
* Impossibile visualizzare le proprietà del nodo quando il codice XML di input viene formattato e distribuito. NPR-26198: Hotfix per CQ-4250448
* IndexOutOfBoundException in ResourceProviderTracker. NPR-26968: Hotfix per GRANITE-23310
* La console JMX accumula numerose sessioni di amministrazione e una nuova sessione viene aperta ogni 5 minuti. NPR-26958: Hotfix per CQ-4251090
* Dopo l’aggiornamento da 6.2 a 6.4, il file di registro mostra la traccia dello stack per il risolutore di risorse non chiuso com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck. NPR-26176: Hotfix per GRANITE-21734
* Quando un agente di flush del dispatcher preconfigurato è configurato per aggiornare gli alias, l&#39;operazione non riesce con un StackOverflowError. NPR-26373: Hotfix per CQ-4242928
* La replica utilizza il token OAuth scaduto fino a quando non riesce. NPR-25894
* Pagina con restrizioni (pagina Gruppo utenti chiuso) con sling: l&#39;alias non reindirizza l&#39;utente alla pagina di accesso. NPR-25715: Hotfix per GRANITE=22263
* Quando si pubblicano i tag, nell’interfaccia utente non viene visualizzata alcuna attività. Hotfix per CQ-4255961
* Impossibile modificare i tag nell’interfaccia classica. Hotfix per CQ-4258697
* Aggiornamento org.apache.felix.http.bridge alla versione 4.0.4. NPR-27038: Backport per GRANITE - 23334
* I registri attività di Gestione pacchetti devono essere estratti in un file di registro separato. NPR-27323: Hotfix per GRANITE-14866
* La convalida del pacchetto non segnala le sovrapposizioni in CFP. NPR-27119: Hotfix per GRANITE-22825

**Progetti**

* L&#39;API ACP gestisce in modo errato il paging solo con elementi secondari della sottodirectory. NPR-27617: Hotfix per CQ-4258639

**OAK**

* Impossibile accedere al repository dopo l&#39;installazione di AEM 6.4 Service Pack 2. NPR-27171: Hotfix per GRANITE-23317

**Replica**

* Audit Log rimane aperto con sessioni attive che continuano ad aumentare costantemente con circa 750 al giorno. NPR-27062: Hotfix per CQ-4241350

**Community**

* I post e le risposte del forum vengono aggiunti all’inizio della seconda pagina e, dopo l’aggiornamento, il post si sposta nella posizione corretta all’inizio della prima pagina. NPR-27342: Hotfix per CQ-4247338
* I collegamenti a tutte le risorse rilasciano il percorso contestuale (/aempublish) dopo lo scorrimento. NPR-26982: Hotfix per CQ-4254345
* I gruppi aggiunti non sono visibili nel menu a discesa Community Manager, Community Moderators e Privileged Member durante la modifica di un sito pubblicato. NPR-27190: Hotfix per CQ-4258574
* Nella pagina delle risorse di abilitazione sono elencati solo 10 gruppi, anche se l’impaginazione è abilitata per l’elenco dei gruppi. NPR-26934: Hotfix per CQ-4252985
* L&#39;opzione per abilitare/disabilitare la ricerca per il post pianificato nel componente journal è fornita in ConfigMgr e il processo SearchScheduledPosts è ottimizzato. NPR-26923: Hotfix per CQ-4250463
* La ricerca per parole chiave nell’indirizzo non funziona nella pagina del componente calendario quando AEM community è impostata per funzionare con DSRP. NPR-26737: Hotfix per CQ-4258493
* È stato implementato un collegamento diretto al commento invece del post principale nei dettagli di un commento, per informazioni sull’interfaccia utente di moderazione e risorse di abilitazione. NPR-26704: Hotfix per CQ-4251381
* Il contenuto moderato tramite selezione multipla nella console di moderazione non viene visualizzato in Flusso attività. NPR-26695: Hotfix per CQ-4253244
* La ricerca con nome e cognome nel campo A della messaggistica di Communities non restituisce il risultato previsto. NPR-26385: Hotfix per CQ-4248673
* Errore durante il caricamento di un allegato in un formato diverso da quello immagine (ad esempio .pdf) nel forum. NPR-27360: Hotfix per CQ-4257753
* Sblocca o annulla la funzionalità di un post del forum se Author-Publish è impostato con MySQL DSRP. NPR-26125; Hotfix per CQ-4251520
* I componenti della raccolta (forum, blog, calendario, ideazione, QnA) ora dispongono di una proprietà nella finestra di dialogo del componente per abilitare/disabilitare &quot;Blocca UGC in modalità Modifica autore&quot;, per consentire/negare il caricamento UGC in modalità Modifica WCM. NPR-26978: Hotfix per CQ-4248161
* La ricerca dei tag non funziona per i termini di ricerca localizzati. NPR-26171: Hotfix per CQ-4249926
* Il pulsante Indietro ignora una pagina nella ricerca nel forum. NPR-26950: Hotfix per CQ-4254804
* AEM&#39;istanza in esecuzione sulla porta Http predefinita (80) non può raggiungere il file imsmanifest.xml. NPR-27173: Hotfix per CQ-4252211
* Scontra commento come risposta per QnA non funziona se AEM Communities è impostato con DSRP. NPR-26247: Hotfix per CQ-4252232
* Impossibile chiamare Adobe Storage: Errore 414 - URI lungo GET osservato quando gli utenti cercano /content/community-components/en/search.html e selezionano il campo autore come uno dei filtri per quel termine di ricerca. NPR-26643: Hotfix per CQ-4251303
* Il valore a discesa per DataCentreURL nella configurazione ASRP viene modificato da Dallas a Virginia (per VA6). NPR-26936: Hotfix per CQ-4254434
* Caratteri speciali negli errori di ritorno della ricerca nel forum o nessun risultato. NPR-26930: Hotfix per CQ-4247744
* Il numero visualizzato per &quot;Numero di risultati&quot; nella ricerca nel forum utilizza un delimitatore non corretto per le impostazioni internazionali Inglese e Tedesco. NPR-27050: Hotfix per CQ-4248939
* Le notifiche non lette non aumentano oltre 21. NPR-26946, NPR-27480: Hotfix per CQ-4252829, CQ-4256939
* La paginazione nella sezione commenti di qualsiasi componente fa scorrere gli utenti verso l’alto per visualizzare il contenuto della pagina, una volta raggiunta una pagina attraverso l’impaginazione. NPR-27032: Hotfix per CQ-4251228
* La cartella Sito community non è cliccabile sull’immagine miniatura quando viene visualizzata da Admin Console nell’istanza di authoring di AEM. NPR-26986: Hotfix per CQ-4254036
* L’opzione &quot;Contrassegna tutto letto&quot; contrassegna solo le prime 10 notifiche come lette e le altre rimangono da leggere fino all’aggiornamento della pagina. NPR-27037: Hotfix per CQ-4254058
* L&#39;impaginazione non viene attivata per l&#39;idea e l&#39;elenco di argomenti (o risposte) diventa più lungo a meno che non venga ricaricato. NPR-26193: Hotfix per CQ-4252104
* Le attività di altri utenti e l’UGC eliminato sono visibili al momento dell’accesso con le credenziali del moderatore e all’aggiunta di &quot;#social-activities&quot; o &quot;#tabs-2&quot; alla fine dell’URL del profilo del moderatore. Hotfix per CQ-4251355
* Non è possibile rimuovere tutti i tag assegnati da un articolo di blog. NPR-26851: Hotfix per CQ-4253359
* Le relazioni con UGC non vengono eliminate al momento dell’eliminazione UGC. NPR-27630: Hotfix per CQ-4258706
* Il collegamento per le risposte non funziona quando si fa clic sulla riga nelle risposte del forum. NPR-27623: Hotfix per CQ-4256138
* Il limite degli abbonamenti utente è limitato a 1000. NPR-27614: Hotfix per CQ-4254689
* La modifica di un sito e la modifica di ruoli nelle impostazioni del ruolo generano un’eccezione Null Pointer. NPR-27377; Hotfix per CQ-4255909

**Traduzione**

* L’anteprima della traduzione non funziona con il contenuto di esempio we.retail. NPR-26727: Hotfix per CQ-4241179

**Interfaccia utente - Foundation**

* Viene restituita un&#39;eccezione NullPointerException quando si tenta di scaricare configurazioni dopo l&#39;aggiornamento a AEM 6.4. NPR-27310: Hotfix per GRANITE-23573
* Backport proattivo per correzioni granite.platform.login. NPR-26941
* Backport proattivo per granite.ui.content correzioni. NPR-26294
* Il componente Campo numero non convalida i numeri negativi in Internet Explorer 11. NPR-26701
* Backport proattivo per granite.ui.coralui3 correzioni. NPR-26662
* Backport proattivo per granite.ui.coralui3-eon correzioni. NPR-26666
* Backport proattivo per granite.ui.foundation.components correzioni. NPR-27313
* Backport proattivo per correzioni granite.ui.commons. NPR-26753
* Backport proattivi dell’interfaccia utente di Foundation. NPR-26248

**Integrazione**

* Le modifiche alle esperienze AEM create tramite il motore di targeting non vengono pubblicate. NPR-24869: Hotfix per CQ-4247832
* Non è possibile creare più attività ed esperienze se i loro nomi includono caratteri giapponesi. NPR-27271: Hotfix per CQ-4256857
* Aggiorna l&#39;endpoint API di Launch. NPR-26790: Hotfix per CQ-4254380
* (Personalization) BrandsRetriever percorre l&#39;intero albero. NPR-27060: Hotfix per CQ-4255790

**WCM - Interfaccia utente amministratore**

* È stato aggiunto un test HTTP per la pubblicazione/annullamento della pubblicazione di una pagina con riferimenti e un test dell’interfaccia utente per Live Copy. Hotfix per CQ-4256894

**WCM - Editor pagina**

* La barra degli strumenti Modifica viene disabilitata per i componenti al primo momento della modifica. Hotfix per CQ-4253270

**Forms**

Elementi di rilievo di AEM 6.4.3.0 Forms:

* Abilitazione del supporto per una matrice o un elenco di oggetti con Sostituzione entità dinamica.
* Abilitazione della conformità FIPS per il flusso di lavoro esteso di Reader in Digital Signature, Reader Extensions, CryptoProvider e TrustStore.
* È stato aggiunto il supporto PDF/UA ai moduli XFA generati utilizzando Designer o Output Service.
* Abilitazione del supporto per la proprietà allowedPaths nei modelli di moduli adattivi.
* È stato aggiunto il supporto JBoss 7.1.4 per AEM Forms 6.4.

**Pacchetto di componenti aggiuntivi per Forms**

**Integrazione con il back-end**

* Impossibile compilare le mappature del modello dati del modulo in base alle entità dinamiche nella risposta SOAP. NPR-26428: Hotfix per CQ-4250639
* Il valore per _elementNamespace nel modello dati del modulo di dati aggiuntivi, immesso utilizzando l’interfaccia utente di test, non viene riportato correttamente nella richiesta SOAP. Hotfix per CQ-4255373
* Un vincolo di proprietà nullable viene inizializzato con un valore predefinito e non può essere sincronizzato con FDM. Hotfix per CQ-4253873
* Il valore predefinito della proprietà nullable non è impostato su True per l&#39;origine dati OData. Hotfix per CQ-4253870

**Moduli adattivi**

* Impossibile caricare l’editor di siti e moduli. NPR-26977; Hotfix per CQ-4249170
* Problemi durante l’aggiunta di un allegato a un modulo adattivo utilizzando la tastiera. NPR-25913; Hotfix per CQ-4249456

**Forms - Comunicazione interattiva**

* Impossibile spostare un pannello aggiunto utilizzando l’opzione Aggiungi pannello figlio nella struttura del contenuto del canale Web di Comunicazione interattiva e nei moduli adattivi. Hotfix per CQ-4253915
* I nomi delle tabelle vengono visualizzati al posto del titolo dell&#39;associazione FDM nella sezione Origini dati del canale Stampa. Hotfix per CQ-4253669
* La funzione isUseXFABullets() non è disabilitata nella classe PrintChannelRenderOptions ed è disponibile nell&#39;SDK client. Hotfix per CQ-4246583, CQ-4252700

**Gestione della corrispondenza**

* Javadocs per 6.4 non contiene il com.adobe.dbforms.* pacchetto e le classi corrispondenti. Hotfix per CQ-4253200
* L’interfaccia utente CCR visualizza un valore junk predefinito per il campo data nel caso in cui non vi sia alcun input dall’XML dei dati di prova. Hotfix per CQ-4252041
* Se una lettera contiene un modulo elenco, lo spazio tra punto elenco e testo viene perso durante la generazione di PDF dalla lettera. Hotfix per CQ-4250588

**Forms Manager**

* Abilitazione del supporto per la proprietà allowedPaths nei modelli di moduli adattivi. NPR-26598: Hotfix per CQ-4255892

**Forms - Flusso di lavoro**

* Se nel nome dell’attività sono incluse parentesi graffe durante l’esecuzione del flusso di lavoro di Forms, nei registri viene visualizzata un’eccezione. Hotfix per CQ-4256626
* Impossibile aprire un modello di ricerca nell&#39;area di lavoro di AEM Forms. Hotfix per CQ-4255651

**Forms Mobile**

* La notifica di uscita non viene visualizzata quando si esce dal campo data in AEM Forms di cui è stato eseguito il rendering come HTML in Internet Explorer o Chrome. NPR-26483: Hotfix per CQ-4239352
* Le date contenute nell’XML all’inizio dell’elaborazione causano la visualizzazione di un errore di convalida quando l’utente tenta di uscire dal modulo. NPR-26787: Hotfix per CQ-4251211

**Programma di installazione di JEE per Forms**

**Servizio PDF Generator**

* Impossibile visualizzare le impostazioni di reporting e conformità per PDF Generator. NPR-26715: Hotfix per CQ-4253384
* file binario convertpdf mancante nel pacchetto aggiuntivo AIX Forms, che causa un errore durante l&#39;avvio del servizio PDFA. Hotfix per CQ-4257873
* Arresto anomalo del servizio di acquisizione su carta durante l’elaborazione dei file TIFF. NPR-28079: Hotfix per CQ-4240649

**Servizi basati su documenti**

* Aggiungi la conformità FIPS per il flusso di lavoro RE in Digital Signature, Reader Extensions, CryptoProvider e TrustStore. NPR-27495: Hotfix per CQ-4257572
* La conversione non riesce durante l&#39;esecuzione del servizio AssemblerService.toPDFA in un ciclo. NPR-26354: Hotfix per CQ-4248656
* Impossibile convalidare correttamente la conformità dei PDF in base agli standard PDF/A-1b. NPR-26286: Hotfix per CQ-4227539
* Problemi di memoria esauriti durante l’aggiornamento di AEM Forms da 6.1 SP2 CFP5 a CFP13. NPR-26285: Hotfix per CQ-4244379
* Impossibile convalidare correttamente la conformità dei PDF in base agli standard PDF/A. NPR-26272: Hotfix per CQ-4248823

**Forms - JEE di base**

* È stato aggiunto il supporto JBoss 7.1.4 per AEM Forms 6.4. NPR-27331; Hotfix per CQ-4255601

**Feature Pack inclusi**

* Abilitazione del supporto per una matrice o un elenco di oggetti con Sostituzione entità dinamica. NPR-26590: Hotfix per CQ-4254655

**Bundle OSGi e pacchetti di contenuti inclusi**

Elenco dei bundle OSGi inclusi in AEM 6.4.3.0

[Ottieni file](assets/6.4.3.0_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.3.0

[Ottieni file](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio di AEM 6.4 in **Aprile 2018.**
È anche cumulativo, il che significa che 6.4.2.0 include tutte le versioni di Service Pack 6.4 AEM prima di esso.

Alcuni degli elementi di rilievo di AEM 6.4.2.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.7.
* È stato aggiunto il supporto per le funzioni della specifica 1.4 di HTML Template Language (HTL)
* È stato aggiunto il supporto per MongoDB Enterprise 3.6.
* L’Editor pagina di Sites aggiunge il supporto per la modifica e la composizione contestuali con componenti lato client generati in React o Angular in combinazione con <a href="../sites-developing/spa-walkthrough.md">AEM Editor JS SDK</a>.
* Miglioramenti ai frammenti di contenuto: è stata aggiunta la possibilità di aggiungere annotazioni nei campi di testo e di confrontare le versioni in modalità affiancata.
* Aggiunto [Integrazione con Adobe Stock](/help/assets/aem-assets-adobe-stock.md) in modo che gli utenti possano cercare, visualizzare in anteprima, salvare e concedere in licenza le risorse Adobe Stock direttamente dall’interfaccia utente AEM. Per informazioni più dettagliate, consulta [Utilizzo di risorse Adobe Stock con AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html).
* Le risorse hanno aggiunto il supporto per il metaschema condizionale dinamico e la possibilità di impostare uno schema di metadati per le cartelle di risorse.
* È stata aggiunta una configurazione in ciascun componente per abilitare/disabilitare la funzionalità di creazione/aggiornamento delle miniature delle cartelle.
* Miglioramenti dell’Editor immagini nella creazione delle pagine.
* Correzione di regressione in Communities per l&#39;evento di punteggio che non viene gestito correttamente in caso di eliminazione della risposta selezionata.
* Limite massimo dei risultati di ricerca rivisto per solr a MAX_INT-10000.
* Il processo di svuotamento della transazione viene avviato solo nella prima chiamata a storeTransaction.
* Il pulsante Seleziona tutto è ora disponibile nella vista a schede e nella vista a colonne.
* Miglioramenti all’accessibilità in CoralUI.
* È stata migliorata la gestione di Coral.Keys .
* Aggiornato momento.js a 2.22.2
* Aggiornamento jquery alla versione 1.12.1
* È stato introdotto il componente foundation-workflowstatus .
* Aggiornamento di GCC alla versione più recente.
* Sposta SAML alla nuova sincronizzazione IDP esterna.

**Risorse**

* La generazione di risorse secondarie per i file pptx non contiene immagini e miniature. NPR-24286: Hotfix per CQ-4217986
* migrateAllAssets - Aggiungi il supporto per l’elaborazione batch e migliora il metodo AEM che aggiunge UID alle vecchie risorse. NPR-24861: Hotfix per CQ-4242863 e CQ-4247874
* Problema di prestazioni nella generazione delle miniature. NPR-24693: Hotfix per CQ-4246960
* (Interfaccia touch) Il componente &quot;predicato opzioni&quot; rimane vuoto quando viene aggiunto alla pagina dell’editore di Asset Share. NPR-24643: Hotfix per CQ-4245295
* (Flusso di lavoro) La funzione Risorse di tag avanzati non viene elaborata tramite la configurazione proxy. NPR-25840: Hotfix per CQ-4248202
* (Omnisearch) la rimozione di filetype:image dai criteri di ricerca non rimuove il tipo di immagine. NPR-25232: Hotfix per CQ-4248280
* Quando si tenta di spostare un file in una cartella diversa, le cartelle con apostrofo nel loro nome non vengono visualizzate. NPR-25125: Hotfix per CQ-4248660
* Il cursore nella pagina Risorse secondarie non funziona correttamente se la preferenza per la lingua è impostata su Inglese. NPR-25274: Hotfix per CQ-4248489
* Problema con il file csv di esportazione di metadati quando aperto su computer con formato numero europeo. NPR-26009: Hotfix per CQ-4250677
* Il pulsante Crea non è disponibile per la selezione della cartella di risorse senza l’autorizzazione &quot;Elimina&quot;. NPR-25788: Hotfix per CQ-4250140
* (Backport) Miglioramenti all’accessibilità: Duplicate-id: Il valore dell&#39;attributo id deve essere univoco, Etichetta: Gli elementi modulo devono avere etichette e nome collegamento: I collegamenti devono avere testo distinguibile. NPR-24252: Hotfix per CQ-4250905, CQ-4250906, CQ-4250907
* Il caricamento di un CSV con campi separati da &quot;,&quot; non riesce per i paesi europei. NPR-25549: Hotfix per CQ-4249931
* (Brand Portal) Le risorse secondarie di un file pdf multipagina non vengono pubblicate quando una risorsa viene pubblicata. NPR-25991: Hotfix per CQ-4245162
* Consente di pubblicare funzionalità successive per la replica di AEM in Brand Portal. NPR-25911: Hotfix per CQ-109139
* Quando si pubblica e si annulla la pubblicazione della raccolta privata da parte di utenti non amministratori, si verifica un NPE. NPR-25906: Hotfix per CQ-4250594
* Disattiva la pubblicazione di frammenti di contenuto e schemi di moduli in Brand Portal. NPR-24176, NPR-26004: Hotfix per CQ-4251592, CQ-4252026
* (Dynamic Media) I visualizzatori DM sono stati aggiornati alla versione 5.10.1 che consente di verificare la presenza di nomi duplicati nella pagina Predefiniti immagine. Consulta Aggiornare i visualizzatori Dynamic Media (5.10.1). NPR-24403: Hotfix per CQ-4247554
* Errore JavaScript nella console del browser nella vista a colonne della selezione di una risorsa o di una cartella. NPR-25939: Hotfix per CQ-4250228
* (Vista a colonne) Impossibile identificare le attività in quanto il file di chiave viene visualizzato come voce bianca vuota. NPR-25903: Hotfix per CQ-4246307

**Sites**

* La query di datasource.jsp su AEM 6.2 è diversa da AEM 6.4. NPR-24968: Hotfix per CQ-4244235
* (Interfaccia classica) Impossibile aggiungere tag alle pagine. NPR-25255, NPR-25612: Hotfix per CQ-4249615
* Specifiche di lingua del modello di HTML 1.4: funzionalità riportate in AEM 6.4.2.0 NPR-24585
* Eredità errata sul componente locale dopo la copia di una pagina Live Copy. NPR-25920: Hotfix per CQ-4236737, CQ-4248957
* Il tempo di attivazione/disattivazione è memorizzato in crx/de ma non lo recupera nella console dell’interfaccia utente delle proprietà della pagina. NPR-25154: Hotfix per CQ-4243431
* Il sistema di stili interrompe i valori iniziali delle proprietà della finestra di dialogo. NPR-25648: Hotfix per CQ-4250073
* Quando si definisce una proprietà cq:tagName in un nodo cq:htmlTag, il nome del tag non viene considerato se il componente è incluso tramite JSP. NPR-24154: Hotfix per CQ-4244120
* Per i componente parsys nidificati, viene sempre applicato il primo design adeguato (quello con il percorso con meno nidificazioni) tra i vari componenti disponibili. Per ulteriori informazioni, consulta [Design Path Resolution](https://docs.adobe.com/content/help/it/experience-manager-64/developing/platform/templates/page-templates-static.html) (Risoluzione del percorso di progettazione). NPR-24973: Hotfix per CQ-4246276
* Quando si incolla del testo in un componente RTE, viene visualizzata una finestra di dialogo a comparsa, ma questa non viene riprodotta correttamente. NPR-24895: Hotfix per CQ-4245901
* (RTE) Problemi di prestazioni con l’indicatore di campo obbligatorio. NPR-24894: Hotfix per CQ-4241895
* (Componente Pagina) L’aggiunta di un componente a Parsys viene ritagliata da destra ed esce dalla larghezza del frame del dispositivo. NPR-25536: Hotfix per CQ-4238224
* L’editor di testo invia dati non tagliati e aggiunge spazi aggiuntivi. NPR-25312: Hotfix per CQ-4249006
* Quando si apre il componente utilizzando la modalità di inlide, i plug-in caricati in precedenza non sono visibili la seconda volta. NPR-24610: Hotfix per CQ-4236850
* Il caricamento di un XF nella visualizzazione editor tramite copia/incolla non carica automaticamente la variante principale. NPR-24841: Hotfix per CQ-4248037
* La struttura HTML errata in siteadmin / damadmin interrompe IE11. NPR-24686: Hotfix per CQ-4246363, CQ-4248402
* (Procedura guidata Gestisci pubblicazione) Il calendario per la data di attivazione al passaggio Opzioni non si apre dopo alcune azioni nel passaggio Ambito . NPR-25681: Hotfix per CQ-4250205
* L’interfaccia classica non funziona per la modifica di gruppi utente chiusi (CUG) perché è diventata obsoleta. NPR-25075: Hotfix per 4241823
* Opzione Crea non disponibile per creare frammenti esperienza. NPR-26053: Hotfix per CQ-4249923
* La variante XF viene attivata due volte, generando ID duplicati per lo stesso elemento. NPR-24179: Hotfix per CQ-4245093
* La tabella di Foundation presenta una vulnerabilità cross-site scripting archiviati. NPR-25185: Hotfix per CQ-4240760
* Errore &quot;Valore del selettore di ricorsività non valido&quot; durante la migrazione di un componente da AEM 6.2.1.13 a AEM 6.4. NPR-24146

**WCM - Editor pagina**

* La presenza di più istanze sovrapposte di parsys (più di 6) causate da query con tempi di esecuzione lunghi rallenta l’esecuzione di AEM. Hotfix per CQ-4240247
* Errore JS quando si aggiunge cq:tagName vuoto nel nodo cq:htmlTag. Hotfix per CQ-4251852
* Aggiorna EditableActions in base alla riallocazione columnClassNames. Hotfix per CQ-4250781
* È possibile esporre i percorsi delle risorse e dei modelli utilizzando un&#39;unica proprietà e attributo. Hotfix per CQ-4251255
* Ripristino delle modifiche di interruzione dell’API export.json. Hotfix per CQ-4251854
* (SPA modificabile) Candidato alla versione 1.0.0. Hotfix per CQ-4251991
* La barra degli strumenti Modifica viene disabilitata per altri componenti quando si modifica un componente. Hotfix per CQ-4253270

**Integrazione**

* I campi Libreria e Scarica URL devono essere modificabili. NPR-24804: Hotfix per CQ-4246864
* Problema con più configurazioni DTM. NPR-24685: Hotfix per CQ-4247293
* È stato aggiunto il supporto per la distribuzione asincrona per le librerie client in hosting. NPR-25716: Hotfix per CQ-4245745
* Il componente di destinazione con offerta corrispondente mancante esegue il rendering dell’intera pagina e, invece di un componente di destinazione vuoto, viene aggiunta un’altra rappresentazione completa della pagina. NPR-25273: Hotfix per CQ-4248003
* Il motore target (mbox.js, at.js) non utilizza URL gestiti e utilizza URL contenenti due punti, che potrebbero non riuscire con determinate implementazioni. NPR-25339: Hotfix per CQ-4237854
* (Launch)LibraryDownloadProcess memorizza il valore libraryUri errato. NPR-25330: Hotfix per CQ-4250006

**Piattaforma**

* Ciclo di reindicizzazione | NPE durante l&#39;esecuzione del BinaryTextExtraction durante l&#39;aggiornamento locale da 6.3 a 6.4. Hotfix per GRANITE - 21677
* Sovrascrittura transfrontaliera del percorso interno contrassegnato /libs/cq/cloudserviceconfigs/templates/configpage/jcr:content - Problema durante l&#39;esecuzione del rilevatore di pattern. NPR-25036: Hotfix per CQ-4248597
* Voci di registro non scritte a causa di NPE in LogEntryImpl. NPR-25627: Hotfix per GRANITE-22383
* La replica dell’evento di eliminazione non verifica i diritti. NPR-25679: Hotfix per CQ-4241234
* È stato aggiunto il supporto STARTTLS in &quot;Day CQ Mail Service&quot;. NPR-25611: Hotfix per CQ-4249924
* Backport proattivo per correzioni granite.platform.login per migliorare l&#39;accessibilità. NPR-25176: Hotfix per GRANITE 21746 e GRANITE-21309
* (AEM 6.4) Errore durante la ricostruzione del pacchetto e la reinstallazione. NPR-25173: Hotfix per CQ-4247939
* È stato rimosso il valore predefinito MERGE_PRESERVE aclHandling. NPR-24593: Hotfix per GRANITE-21889
* Content-Type non viene propagato e mancante nella risposta dopo aver applicato due volte ContentDispositionFilter. NPR-24175: Hotfix per Sling-7525
* Lo stato di Gestione pacchetti è errato dopo l&#39;aggiornamento al ramo 6.4 AEM. NPR-24551: Hotfix per GRANITE-21750
* Istanza AMS - Analisi dei registri di errore. Hotfix per CQ-4249567

**Sicurezza**

* SAML re-login reindirizza alla pagina di logout utilizzando Okta IDP. NPR-25523: Hotfix per GRANITE-22364
* L’autenticazione IMS tramite OAK tramite la configurazione del provider OAuth IDP esterno disattiva l’utente creato in AEM. NPR-25301: Hotfix per GRANITE-22363

**MAC - Integrazione Test&amp;Target**

* (Targeting) Errore del componente Testo durante il targeting. Hotfix per CQ-4233343

**Community**

* (Libreria file) Il download di risorse con spazi vuoti da causa problemi di formato. NPR-24260: Hotfix per CQ-4245159
* Correzioni per diversi problemi relativi ad Adobe Social. NPR-24247: Hotfix per CQ-4245054, CQ-4245120, CQ-4245296
* Se la pubblicazione dell’autore viene eseguita su percorsi contestuali diversi, lo scorrimento infinito per la console di membri e gruppi non riesce. NPR-24437: Hotfix per CQ-4246013
* Il post non ritorna allo stato senza risposta anche quando si rimuove dallo stato di risposta e il punteggio non diminuisce. NPR-24419: Hotfix per CQ-4245797, CQ-4245932
* Gli eventi aggiunti utilizzando la funzionalità Calendario in Communities producono valori errati. NPR-24883: Hotfix per CQ-4244056
* (Forum di Communities) Problemi relativi al comportamento di clic e caricamento della pagina nell’impaginazione. NPR-24880: Hotfix per CQ-4246109
* (Chrome) Le conversioni del fuso orario non riescono sugli eventi delle community. NPR-24881: Hotfix per CQ-4247115
* Impossibile eseguire il rendering dell&#39;oggetto incorporato in E-mail. NPR-24999: Hotfix per CQ-4248022
* La sequenza di automazione deve essere eseguita su aggiornamento UGC oltre alla creazione UGC. NPR-25892: Hotfix per CQ-4251399
* Risposta della finestra di dialogo modale sui gruppi. NPR-25623: Hotfix per CQ-4248805
* L&#39;eccezione Solr viene lanciata all&#39;eliminazione del contenuto. NPR-25869: Hotfix per CQ-4248908
* I collegamenti impaginati a thread con molti post non funzionano sulle notifiche. NPR-25678: Hotfix per CQ-4243038
* I valori di ora nel risultato della ricerca visualizzano l&#39;ora del server invece del fuso orario del client. NPR-25594: Hotfix per CQ-4248986
* (Commenti forum) Il pulsante Indietro del browser non funziona come previsto. NPR-25205: Hotfix per CQ-4248573
* (Risultati ricerca) Il pulsante Indietro del browser non funziona come previsto. NPR-25214: Hotfix per CQ-4248574
* Quando si sovrappone il componente communitygroupmemberlist, viene restituito Null. NPR-25228: Hotfix per CQ-4248523
* (Calendario community) ClassCastException viene generato durante il salvataggio dell&#39;evento con la nuova immagine Cover. NPR-25167: Hotfix per CQ-4248662
* (Community) Messaggi troncati. NPR-25326
* (Pubblicazione AEM) La risorsa Scorm non riesce con il percorso del contesto e mostra la schermata vuota. NPR-26155: Hotfix per CQ-4251942
* (MSRP) Il calendario appena creato viene salvato generando parzialmente NPE nel registro degli errori. NPR-26071: Hotfix per CQ-4250531
* L’impaginazione di forum/argomenti viene aggiornata solo quando la pagina viene aggiornata. NPR-26070, NPR-25965: Hotfix per CQ-4249509
* (Forum Q&amp;A) Impossibile passare alla pagina precedente quando si apre un collegamento diretto a un commento. NPR-26069: Hotfix per CQ-4251699
* Il caricamento dell&#39;immagine nel gruppo Crea non funziona su dispositivi mobili. NPR-26172: Hotfix per CQ-4251703
* (Messaggistica) Quando si utilizza DSRP, il nome del ricevitore del messaggio viene sempre visualizzato come &quot;Sconosciuto&quot;. NPR-26056: Hotfix per CQ-4251397
* L’etichetta dello stato per il completamento dell’attivazione di una risorsa SCOR risulta vuota nell’interfaccia utente. NPR-26034: Hotfix per CQ-4249994
* Durante la creazione di un nuovo gruppo community, viene creato un gruppo community duplicato su un cluster mongoMK attivo/attivo. NPR-26032: Hotfix per CQ-4245884
* (Autore) La procedura guidata per la creazione di gruppi richiede troppo tempo per caricare o creare un gruppo all’interno della procedura guidata. NPR-26031: Hotfix per CQ-4244966
* Parsys scompare quando si aggiunge un&#39;istruzione include nello script hbs. NPR-25908: Hotfix per CQ-4250489
* Quando si abilita “Consenti membri privilegiati”, i membri con le autorizzazioni necessarie dovrebbero essere in grado di comporre solo per gli utenti che sono membri della community. NPR-25877: Hotfix per CQ-4248450
* Collegamenti profondi bloccati per l&#39;abilitazione. NPR-25966: Hotfix per CQ-4251478
* La paginazione del forum non viene aggiornata dinamicamente alla rimozione delle risposte. NPR-25970: Hotfix per CQ-4248975, CQ-4252843
* Scorrimento automatico e evidenziazione non funzionano sugli eventi calendario e filelib in caso di commenti nidificati. NPR-25958: Hotfix per CQ-4251471
* (DSRP) Le prestazioni dei collegamenti diretti/profondi si degradano con un’elevata quantità di contenuti generati dagli utenti. NPR-25957: Hotfix per CQ-4251470
* Impossibile modificare le proprietà di Consenti membri con privilegi e membri con privilegi. NPR-26014: Hotfix per CQ-4244592
* Contrassegna tutto come letto ripristina i contatori di notifica per tutte le pagine della community. NPR-25931: Hotfix per CQ-4248612
* Modifica IT non riuscita per DSRP. NPR-25929: Hotfix per CQ-4251382
* L’attività IT dell’e-mail non riesce a causa di NPE durante la creazione di modelli e-mail. NPR-26039: Hotfix per CQ-4250962
* Problemi di thread del forum quando si incorporano immagini con una risoluzione molto elevata. NPR-26037: Hotfix per CQ-4244453, CQ-4253099
* L&#39;ora visualizza gli switch quando il fuso orario del server è diverso da quello dell&#39;utente. NPR-26036: Hotfix per CQ-4248751
* Se si allega due volte un file con lo stesso nome a un post del forum, si verifica un errore del server. NPR-24172: Hotfix per CQ-4244367
* Correzioni delle prestazioni di backport : impaginazione di gruppo su autore e pubblicazione, ricerca di gruppo sull&#39;autore, Evitare la serializzazione delle risposte per giornale, calendario e ideazione e caricamento lento per ottenere l&#39;iscrizione al gruppo (invito/annullamento invito) pulsante per ogni gruppo durante la visualizzazione della pagina di elenco dei gruppi. NPR-24538: Hotfix per CQ-4246515
* Le risorse di abilitazione non sono visibili sull’autore. Hotfix per CQ-4252618
* Le notifiche non vengono generate per il thread da un utente sconosciuto. Hotfix per CQ-4245132
* La ricerca del gruppo non viene visualizzata nella barra a sinistra. Hotfix per CQ-4252621
* (Autore) La paginazione non funziona per la console Gruppi. Hotfix per CQ-4242786
* Aggiornamento dell’interfaccia utente jQuery. Hotfix per CQ-4248894
* Effettua l’aggiornamento alla versione più recente di SCORM 2017.1. NPR-25675: Hotfix per CQ-4240671
* I campi &quot;Componi per conto&quot; sono visibili agli utenti non appartenenti alla community. NPR-25331: Hotfix per CQ-4247858
* Il post è ancora visibile nell’interfaccia utente anche dopo l’eliminazione e genera un errore nella console. NPR-26290: Hotfix per CQ-4252803
* (Impostazioni sito) È possibile salvare le modifiche apportate a Ruoli. NPR-26274: Hotfix per CQ-4252187
* (Vulnerabilità di sicurezza) Acquisizione account a causa di configurazione errata dei token web JSON. NPR-26458: Hotfix per CQ-4253314
* L&#39;impaginazione non viene reimpostata al momento della rimozione delle risposte. NPR-26326: Hotfix per CQ-4252997
* L&#39;immagine dell&#39;allegato non viene visualizzata nelle bozze durante la modifica. Hotfix per CQ-4253360
* Impossibile aggiornare la pagina durante l&#39;allegato nel database relazionale (DSRP). Hotfix per CQ-4253084
* I gruppi non funzionano nella risorsa del sito di abilitazione. Hotfix per CQ-4252975
* I percorsi di apprendimento dei prerequisiti non vengono mantenuti in Abilitazione. Hotfix per CQ-4252948

**Flusso di lavoro**

* L’interfaccia utente del modulo di avvio del flusso di lavoro non visualizza configurazioni precedenti al modulo di avvio 41 e attiva un errore javascript nella console. NPR-25028: Hotfix per CQ-4247604
* La modifica di un flusso di lavoro legacy senza modificarne il modulo di avvio causa la creazione di più flussi di lavoro in qualsiasi flusso di lavoro che contiene un passaggio Attiva pagina/Risorsa . NPR-25870: Hotfix per CQ-4250896
* Collegamento errato nel payload del flusso di lavoro se la pagina dispone di un nodo di metadati. NPR-25916: Hotfix per CQ-4250733

**Traduzione**

* È stato corretto che l’importazione di un progetto tradotto effettuasse due richieste POST simultanee, causando quindi un errore. NPR-24889: Hotfix per CQ-4247638
* Durante la creazione di un progetto di traduzione per più lingue, tutte le pagine per la stessa lingua vengono aggiunte allo stesso processo. NPR-25091: Hotfix per CQ-4246112
* È stato corretto che in alcuni casi, il processo di traduzione elenca solo le prime 40 pagine. NPR-25974: Hotfix per CQ-4248661
* Il componente DataPicker (Coral2) non modifica l’anno. NPR-24466: Hotfix per GRANITE-21893

**Interfaccia utente - Foundation**

* Backport proattivi dell’interfaccia utente di Foundation. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-259 35, NPR-25976
* (Importazione progettazione) L’importazione di una pagina non importa js,css. NPR-25203: Hotfix per GRANITE-22236
* Backport proattivi dell’interfaccia utente di Foundation per migliorare la stabilità del prodotto. NPR-24334

**MAC - Integrazione Test&amp;Target**

* La seconda pagina di PersonalizationWizard ( avviata da &quot;Start Targeting&quot; ) è vuota e genera errori della console. Hotfix per CQ-4253277

**Frammenti esperienza**

* Integrazione di frammenti esperienza/Target uniti a AEM 6.4.2.0. Hotfix per CQ-4248653

**Gestione dei frammenti di contenuto**

* Annotazioni dei frammenti di contenuto e confronto affiancato delle versioni dei frammenti di contenuto. Hotfix per CQ-4247148

**DAM - Generale**

* Filtro &quot;estratto da&quot; non funzionante correttamente nella ricerca. Hotfix per CQ-4247070
* Quando si esegue il flusso di lavoro di aggiornamento delle risorse, la copia della lingua della risorsa e la relativa miniatura diventano vuote. Hotfix per CQ-4250641
* Duplicate-id: il valore dell&#39;attributo id deve essere univoco. Hotfix per CQ-4250905
* Etichetta: Gli elementi modulo devono avere delle etichette. Hotfix per CQ-4250906
* Nome collegamento: I collegamenti devono avere testo distinguibile. Hotfix per CQ-4250907
* Migrazione JMX e ServiceUserMapping dei modelli di metadati delle cartelle delle porte. Hotfix per CQ-4252947
* Test WebdriverIO non in esecuzione nel ramo release/640 di CQ/dam. Hotfix per CQ-4252749
* I collegamenti alle risorse spostate non vengono reinseriti se il collegamento viene pubblicato. Hotfix per CQ-4245756

**DAM - Visualizzatori**

* Errore intermittente durante il caricamento del video con i nuovi visualizzatori 5.10.1. Hotfix per CQ-4250562

**DAM-Brand Portal**

* Errore durante l&#39;annullamento della pubblicazione della raccolta da Brand Portal. Hotfix per CQ-4245990
* Impossibile annullare la pubblicazione dei predefiniti immagine da Brand Portal. Hotfix per CQ-4246140
* Le risorse secondarie di un file pdf con più pagine non vengono pubblicate quando una risorsa viene pubblicata. Hotfix per CQ-4245162

**DAM - DMClient**

* Quando si pubblica una risorsa video in YouTube, i tag che ne risultano in YouTube includono il percorso completo del tag. Hotfix per CQ-4245549
* (Aggiornamenti Opt-out e Opt-in) Problema con il reindirizzamento CSS del visualizzatore. Hotfix per CQ-4247854
* Impossibile creare/modificare il predefinito visualizzatore come non membro del gruppo &#39;amministratori&#39;. Hotfix per CQ-4247618
* (6.4.1.0) L’aggiunta di più video in più parsys interrompe il lettore video. Hotfix per CQ-4248517
* La ridenominazione e lo spostamento delle risorse all’interno di un set di immagini rende impossibile la modifica. Hotfix per CQ-4248434
* La pubblicazione di video di grandi dimensioni in YouTube genera messaggi di timeout. Hotfix per CQ-4237831
* (Vista a elenco) L’interfaccia utente del Selettore/Selettore risorse è grigia e disabilitata per l’utente. Hotfix per CQ-4237817
* (Zoom verticale) Css non viene caricato con un errore 404. Hotfix per CQ-4236508
* Se tenti di scaricare una risorsa con il carattere percentuale (%) nel nome della risorsa, ottieni un archivio vuoto. Hotfix per CQ-4250558
* (Vista a schede) Non viene visualizzato alcun indicatore di elaborazione quando si utilizzano le opzioni Copia e Incolla su una risorsa video. Hotfix per CQ-4249037
* (Aggiornamento da 6.3.2 a 6.4) I predefiniti immagine pre-aggiornamento sono visualizzati come &quot;Non pubblicato&quot; nella pagina Rendering ma non producono il pulsante URL quando selezionato. Hotfix per CQ-4240406
* Debiti Tecnici/Miglioramenti Minori. Hotfix per CQ-4240648
* Il Selettore risorse (o Selettore risorse) non mostra tutte le risorse dalle cartelle disponibili. Hotfix per CQ-4218414
* Il predefinito per immagini senza altezza visualizza immagini con dimensioni errate. Hotfix per CQ-4246546
* L’interfaccia utente di (Risorse multiple) si interrompe quando si fa clic sulle annotazioni. Hotfix per CQ-4251434
* Con l’aggiornamento dalla versione 6.3 alla versione 6.4 e successive al predefinito Analytics, viene creata una nuova suite di rapporti e un nuovo predefinito di analisi per perdere i vecchi dati di reporting dell’utente. Hotfix per CQ-4244529
* (Procedura guidata Gestisci pubblicazione) L&#39;elenco delle risorse sembra vuoto quando si tenta di pubblicare o annullare la pubblicazione. Hotfix per CQ-4251881
* Quando si selezionano i visualizzatori dopo aver visualizzato i Membri set, i video AVS non riescono a essere riprodotti. Hotfix per CQ-4205308
* I predefiniti di elaborazione video pre-aggiornamento non possono avere un nuovo predefinito di codifica video aggiunto né modificare i predefiniti di codifica esistenti. Hotfix per CQ-4240407
* I predefiniti immagine non vengono applicati alle rappresentazioni dinamiche scaricate. Hotfix per CQ-4249862
* Il pulsante Seleziona tutto non funziona correttamente nella pagina di elenco Predefiniti visualizzatore . Hotfix per CQ-4252462
* Profili video: Il pulsante Seleziona tutto non funziona. Hotfix per CQ-4253076, CQ-4251447
* Passaggio convalida SP2 - Fumo Pass. Hotfix per CQ-4251639

**DAM - Servizi DM**

* Impossibile generare rappresentazioni Dynamic Media per il file EPS. Hotfix per CQ-4243688

**Granite**

* Digita nel bundle SymbolicName porta a un bundle duplicato. Hotfix per GRANITE-22155
* CUGConfiguration non può raccogliere CugExclude. Hotfix per GRANITE-21109
* Il riavvio di Adobe Granite Workflow Core esegue nuovamente i passaggi del flusso di lavoro dal centro creando flussi di lavoro non necessari. NPR-25057: Hotfix per GRANITE-22218
* JcrResourceBundle non supporta correttamente più nomi di base. NPR-25245: Hotfix per GRANITE-22317
* Al momento dell&#39;installazione dei pacchetti di contenuto, le ACL sono raggruppate per entità, quindi, infrangendo il modello di autorizzazione. NPR-24583: Hotfix per GRANITE-21591
* Aggiorna Jetty alla versione 9.4.11 per correggere le vulnerabilità. NPR-25030: Hotfix per GRANITE-22120

**Forms**

Elementi di rilievo di AEM 6.4.2.0 Forms:

* È stata aggiunta una nuova proprietà per le code da aggiornare senza aggiornare il browser.
* È stata aggiunta la possibilità per l’utente di utilizzare lo stesso file WSDL per più servizi.
* È stato rimosso il pattern di marca temporale non supportato dal menu a discesa della visualizzazione momentanea di altri contenuti.
* È stato aggiunto il supporto per la sottoutilizzazione di xfaf e pdf in OSGI.
* È stato aggiunto il supporto per utilizzare il [capacità rapporti sulle transazioni](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) distribuzioni on-premise.
* È stato aggiunto del codice per non visualizzare le var secondarie nell’editor di regole di condizione.

**Pacchetto di componenti aggiuntivi per Forms**

**Reporting sulle transazioni**

* Aggiorna la configurazione di Transaction Reporting con l&#39;importanza della replica inversa configurata su un server Publish. NPR-26050: Hotfix per CQ-4246650
* Inizializzazione ritardata del processo di scaricamento periodico. NPR-25968: Hotfix per CQ-4245024
* La registrazione delle transazioni non riesce con un&#39;eccezione Null Pointer. Hotfix per CQ-4247302

**Forms - Flusso di lavoro**

* (Area di lavoro HTML) Quando un utente richiede un’attività, il numero nella coda viene aggiornato per quel particolare utente, ma non per altri utenti, a meno che la pagina non venga aggiornata. Questo problema è stato risolto da una nuova proprietà. Per configurare questa nuova proprietà nell&#39;istanza AEM, consulta le relative impostazioni di configurazione. NPR-24536: Hotfix per CQ-4233665
* Impossibile caricare il modulo di grandi dimensioni nell&#39;app AEM Forms alla versione 6.4. NPR-24463: Hotfix per CQ-4245091
* Problema nell&#39;app di Mobile Workspace quando si tenta di visualizzare l&#39;attività condivisa. NPR-25177: Hotfix per CQ-4248733
* Comportamento di convalida incoerente tra Web e APK. NPR-25670: Hotfix per CQ-4248178
* Quando si effettua una chiamata a un servizio Web e si apre un modulo HTML5 all’interno del client, questa non riesce e viene restituito un messaggio di errore. NPR-26048: Hotfix per CQ-4244716
* Problema durante la chiamata del servizio in AEM forms Windows app 6.3. NPR-26468: Hotfix per CQ-4252341

**Forms Mobile**

* (Set di moduli) Problema di convalida dei campi SSN e Mobile durante l’anteprima. NPR-24458: Hotfix per CQ-4244983
* I dati non vengono visualizzati con la precompilazione di campi con più righe nell’anteprima di HTML. NPR-24549: Hotfix per CQ-4244212
* I dati vengono persi quando lo script viene valutato in un campo su più righe. NPR-25333, Hotfix per CQ-4249610

**Forms - Comunicazione interattiva e gestione della corrispondenza**

* La sincronizzazione non riesce su IC con il modello di base e il modello di stampa IC di riferimento. NPR-24912
* (CCR) I validatori non funzionano per campi/variabili. Hotfix per CQ-4245047
* L’icona Oggetto modello dati scompare a intermittenza nella barra degli strumenti Modifica testo. Hotfix per CQ-4245122
* I registri di eccezione vengono visualizzati sull&#39;IC copiato se l&#39;IC originale viene eliminato. Hotfix per CQ-4249378
* Nel rendering della lettera, la condizione non restituisce true anche quando i dati sono corretti. Hotfix per CQ-4245944
* I componenti generati automaticamente non vengono evidenziati quando si seleziona dalla struttura contenuto. Hotfix per CQ-4246178
* Problemi durante l&#39;apertura dell&#39;editor modelli canale web. Hotfix per CQ-4248182
* Impossibile modificare l&#39;ordine delle risorse aggiunte poiché le frecce su/giù rimangono disabilitate. Hotfix per CQ-4252042
* Impossibile aggiornare le proprietà del modulo Condition. Hotfix per CQ-4247909
* È necessario migliorare l’UX della finestra di dialogo &quot;Annulla ereditarietà&quot; quando l’utente ridispone un oggetto nel canale web. Hotfix per CQ-4241076
* Nella lettera corrispondente ai binding definiti in XDP, i dati non vengono aggiunti tramite l’URL diretto della lettera. Hotfix per CQ-4245833
* (Problema di memorizzazione nella cache) La sincronizzazione del canale web non riflette le modifiche apportate ai frammenti di layout, al frammento di testo del canale di stampa. Hotfix per CQ-4251460
* Impossibile aggiornare il frammento di layout e le proprietà DD. Hotfix per CQ-4247830
* (CCR) Errore durante il ricaricamento della bozza a causa dell&#39;analisi XML. Hotfix per CQ-4250950
* (IC Editor) Il pulsante &quot;Modifica frammento&quot; deve essere più individuabile. Hotfix per CQ-4244694
* (XDP) All’aggiunta di un frammento di layout nel nuovo sottomodulo creato viene visualizzata una schermata vuota. Hotfix per CQ-4248810
* Errore di test di DocumentFragment-master-DeployWithServerSideTests. Hotfix per CQ-4245496
* Variabile del modulo di testo Istanza duplicata nel modulo Condizione. Hotfix per CQ-4252128
* L’URL di anteprima di PDF non mostra i rapporti sulle transazioni al momento della pubblicazione. Hotfix per CQ-4246158
* Problemi relativi alla sincronizzazione IC con la sincronizzazione da canale di stampa a canale Web. Hotfix per CQ-4251505
* Pulizia codice EXM: Rimuovi LocalFunctionMapper. Hotfix per CQ-4243265
* Per correggere il tipo di risorsa del componente tabella WebChannel di IC TableHeader. Hotfix per CQ-4251821
* (IC Editor) Problemi di usabilità. Hotfix per CQ-4241081
* Il sottomodulo del canale di stampa non mostra la funzionalità di inserimento. Hotfix per CQ-4252994
* Mantieni le modifiche sincronizzate non riesce dopo aver rimosso il nodo FDM o il segnaposto Variabile. Hotfix per CQ-4253178
* (Editor modelli) Il modello di base mostra le aree di trascinamento aggiuntive dell’intestazione/piè di pagina e lo schermo lampeggia all’apertura del canale Web. Hotfix per CQ-4253323
* I componenti generati automaticamente non vengono evidenziati quando si seleziona dalla struttura contenuto. Hotfix per CQ-4246178

**Servizi basati su documenti**

* (Servizio moduli) OSGI non supporta XFAF. NPR-25181, Hotfix per CQ-4251313
* I caratteri nell&#39;intestazione del file PDF assemblato stanno diventando confusi. NPR-25113: Hotfix per CQ-4244682

**Moduli adattivi**

* Invia azione come Invia posta genera un&#39;eccezione con i campi CC/BC vuoti. NPR-25019: Hotfix per CQ-4243039
* Impossibile utilizzare il componente Modulo AEM OOTB a causa di una query inefficiente. NPR-25065: Hotfix per CQ-4247256
* Rimuovi sling:orderBefore dai nodi di dialogo di guideImageChoiceComponent. Hotfix per CQ-4245013
* (Selezione data) Il pattern di modifica non supporta due tipi di pattern di marca temporale. Hotfix per CQ-4237982
* Invia un’azione utilizzando i problemi di authoring di Forms Workflow Classic. Hotfix per CQ-4236981
* (Canale Web) Grafico IC deve ereditare la proprietà colspan dal grafico AF. Hotfix per CQ-4252143

**Integrazione con il back-end**

* (Richieste SOAP) I decimali principali (più di 6 cifre) sono rappresentati in notazione esponenziale con conseguente errore di convalida. NPR-25283: Hotfix per CQ-4248100
* Convalida non corretta dei parametri facoltativi definiti in tipi complessi. NPR-25070: Hotfix per CQ-4247107
* È stata aggiunta la possibilità per l’utente di utilizzare lo stesso file WSDL per più servizi. NPR-24604, Hotfix per CQ-4247756
* L’ordine dei parametri nelle chiamate SOAP viene mescolato in FDM. NPR-25069, Hotfix per CQ-4247180
* FDM unisce le entità (in List/Array) nella richiesta SOAP. NPR-25284: Hotfix per CQ-4248375

**Programma di installazione Forms JEE**

**Servizio PDFG**

* La funzione di creazione/modifica delle impostazioni di protezione non funziona. NPR-24769: Hotfix per CQ-4246927
* Optimize PDF rimuovendo in modo selettivo i font tramite una singola chiamata API. NPR-23287

**Servizi basati su documenti**

* Il servizio di output non fornisce i tag corretti per il Reader di accessibilità. NPR-24438, NPR-24439, NPR-24440, NPR-24441: Hotfix per CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Sicurezza dei documenti**

* Problema relativo alla creazione dei criteri tramite Document Security. NPR-25586, NPR-25547: Hotfix per CQ-4247086

**Forms - JEE di base**

* Processi in esecuzione come account di contesto di sistema a intermittenza. NPR-25289, NPR-25313: Hotfix per CQ-4249331
* JEE per AEM Forms interessato dall’avviso di sicurezza di associazione dati Apache Struts e Jackson. NPR-25628: Hotfix per CQ-4242891
* Il processo punto di inizio e-mail non funziona. NPR-25253: Hotfix per CQ-4248518

**Feature Pack inclusi**

**Risorse**

* Aggiunto [Integrazione con Adobe Stock](/help/assets/aem-assets-adobe-stock.md) in modo che gli utenti possano cercare, visualizzare in anteprima, salvare e concedere in licenza le risorse Adobe Stock direttamente dall’interfaccia utente AEM. Per informazioni più dettagliate, consulta [Utilizzo di risorse Adobe Stock con risorse AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html). NPR-15779: Hotfix per CQ-30857
* È stato aggiunto il supporto per il metaschema condizionale dinamico. Per ulteriori informazioni, consulta [Metadati a cascata](/help/assets/cascading-metadata.md). NPR-25189: Hotfix per CQ-4237413
* Abilitazione dell’opzione &quot;Download risorse&quot; nei frammenti di contenuto. Per ulteriori informazioni, consulta [Rapporti sulle risorse](/help/assets/asset-reports.md). NPR-25186: Hotfix per CQ-4237410
* Possibilità di impostare uno schema di metadati per le cartelle di risorse. Per ulteriori informazioni, consulta [Schema metadati cartelle](/help/assets/folder-metadata-schema.md) e fare riferimento alle [Impostazioni di configurazione](#configuration-settings-required-for-npr) installazione successiva AEM 6.4.2.0. NPR-21268: Hotfix per CQ-4221574

**Sites**

* Consente di modificare un frammento di contenuto senza eliminare le autorizzazioni. Per ulteriori informazioni, consulta [Personalizzazione ed estensione dei frammenti di contenuto](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-delete.html). NPR-25793: Hotfix per CQ-4248750
* Aggiunta la possibilità di annotare frammenti di contenuto. Per ulteriori informazioni, consulta [Varianti-Authoring di frammenti](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment). NPR-25188: Hotfix per CQ-4235336
* Controllo delle versioni: Confronta i frammenti di contenuto affiancati. Per ulteriori informazioni, consulta [Gestione dei frammenti di contenuto](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions). NPR-25187: Hotfix per CQ-4237412
* Miglioramenti dell’Editor immagini riportati a AEM 6.4.2.0. Per ulteriori informazioni, consulta [Editor immagini](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24467

**Bundle OSGi e pacchetti di contenuti inclusi**

Elenco dei bundle OSGi inclusi in AEM 6.4.2.0

[Ottieni file](assets/6.4.2.0_bundle-list.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.2.0

[Ottieni file](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

AEM 6.4.1.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio della versione 6.4 di AEM nell’aprile 2018.

AEM 6.4.1.0 può essere installato su AEM 6.4 GA. Alcuni elementi di rilievo del service pack sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.3.
* Sono stati introdotti tag avanzati migliorati.
* Correzioni nel selettore progettazione, nel selettore tag (cambiare la VM di origine e la VM di destinazione in automatica).
* È stato aggiunto il supporto di typeHint per salvare i valori come stringa.
* È stato aggiunto il supporto per SMTP su TLS nel servizio e-mail.
* Correzione per la gestione dei proxy per il server d&#39;inoltro HTTP in DMS7.
* Aggiornamento a /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js versione 1.3.
* Correzioni nei pacchetti DMHybrid Opt-OUT e Opt-in.
* Correzioni in Smart Crop.
* I valori di configurazione OOTB trasferiti nella nuova posizione ( da /etc a /conf).
* Sono stati aggiunti profili di colore alle impostazioni del cliente sui server di consegna.
* Migrazione delle impostazioni di Image Server da /etc —&amp;gt; /conf.
* È stato aggiunto il frammento di contenuto sorgente per la traduzione.
* È stato aggiunto il supporto ARIA a Print and PrintDialog.
* È stato aggiunto il supporto ARIA per la convalida dell’e-mail.
* Backport proattivo per correzioni di platform.clientlibs .
* Prevenzione dell&#39;esecuzione automatica degli script in assenza di input per l&#39;oggetto dataType esplicito (risolve CVE-2015-9251).

**Risorse**

* Il valore a discesa a cascata viene visualizzato vuoto alla riapertura della pagina delle proprietà della risorsa. NPR-23042: Hotfix per CQ-4238761
* I collegamenti condivisi nella pagina mylinkshare e i collegamenti alla pagina non sono disponibili per l’utente non amministratore NPR-23044: Hotfix per CQ-4239004
* Per evitare un’eccezione Null Pointer nel flusso di lavoro DAM Asset Update in 6.4.0. NPR-24134: Hotfix per CQ-4244972
* La pagina WCM pubblicata mostra le icone dei segnaposto per il punto attivo, file CSS mancanti con errore 403 per i visualizzatori OOTB. NPR-23041: Hotfix per CQ-4233716
* (Vista dettagli) La funzione Navigazione successiva/posteriore lascia una sovrapposizione DIV nell’area di anteprima Rendering dinamico che blocca l’accesso al visualizzatore. NPR-23043: Hotfix per CQ-4238499
* Il rendering dell&#39;immagine CMYK presenta una saturazione non corretta. NPR-23048: Hotfix per CQ-4235470
* L’estrazione dei metadati XMP da Scene7ListInfoProvider richiede un uso intensivo delle risorse. NPR-23754
* (dam-delivery) Il server di inoltro HTTP non rispetta le impostazioni proxy HTTP. NPR-24002: Hotfix per CQ-4244140

**Sites**

* Quando si rinomina la pagina durante lo spostamento, lo spostamento della pagina ha esito positivo, ma la funzionalità di ridenominazione non funziona. NPR-22923: Hotfix per CQ-4235907
* Errore durante la pubblicazione di una pagina Live Copy che punta a una pagina di importazione in Adobe Campaigns. NPR-23053: Hotfix per CQ-4237164
* Lo spostamento/ridenominazione nell’interfaccia classica non riesce con l’errore &quot;Errore durante lo spostamento della pagina&quot; e non viene rinominato. NPR-23051: Hotfix per CQ-4235907
* Il passaggio dalla vista a colonne alla vista a elenco esegue il rendering di una pagina vuota e attiva un’eccezione Null Pointer per le pagine con OffTime impostato e OnTime come vuoto. NPR-22968, NPR-23052: Hotfix per CQ-4238940

**Commerce**

* Correggi il test Hobbes Core non riuscito (modulo CQ/Commerce). Hotfix per CQ-4253494

**Vulnerabilità**

* L’integrazione con Salesforce è vulnerabile ad attacchi di tipo SSRF (Server Side Request Forgery). NPR-24289: Hotfix per CQ-4245277
* Server Side Request Forgery (SSRF) e Cross-Site Scripting (XSS) in ReportingServicesProxyServlet. NPR-24657: Hotfix per CQ-4246880
* Script tra siti (XSS): Riflesso in commerce createcatalogwizard.html/content. NPR-24642: Hotfix per CQ-4237017
* Vulnerabilità cross-site scripting (XSS) nei collegamenti di progetto di Interfaccia utente amministratore. NPR-23272: Hotfix per CQ-4241795

**WCM - Componenti Foundation**

* Quando si apre il selettore Progettazione, viene generata un’eccezione Null Pointer. NPR-23047: Hotfix per CQ-4238736

**Interfaccia utente**

* (Coral3 Datepicker) Aggiungi il supporto per typeHint per salvare i valori come &quot;String&quot;. NPR-23398: Hotfix per GRANITE-21194
* La traduzione internazionalizzata non funziona a livello di lingua. NPR-22967, NPR-23046: Hotfix per GRANITE-21111
* Backport proattivo per correzioni granite.ui.commons. NPR-23537
* Backport proattivo per granite.ui.content correzioni. NPR-23535
* Backport proattivo per granite.ui.coralui correzioni. NPR-23538
* Impossibile rimuovere più utenti dal gruppo contemporaneamente. NPR-23846
* (OMEGA) Report &quot;Feature&quot; solo in inglese. NPR-23989: Hotfix per GRANITE-21231
* (Importazione progettazione) L’importazione di una pagina non importa js, css. NPR-25203: Hotfix per GRANITE-22236

**Integrazione**

* ResourceResolver non chiuso in com.day.cq.analytics.sitecatalyst. NPR-22340: Hotfix per CQ-4236515
* TargetContentImpl rallenta l’esecuzione di AEM durante le query con tempi di esecuzione lunghi. NPR-22359: Hotfix per CQ-4236907
* Il motore target (mbox.js, at.js) non utilizza URL gestiti e utilizza URL contenenti due punti, che potrebbero non riuscire con determinate implementazioni. NPR-22434: Hotfix per CQ-4237854
* In modalità Target gli autori possono modificare un componente ereditato dalla blueprint senza annullare l’ereditarietà. NPR-22865: Hotfix per CQ-4237907
* (Personalization) Le icone sono deformate quando si passa alla vista a schede. NPR-23373, NPR-23374: Hotfix per CQ-4240018, CQ-4240019
* (Personalization) La console Pubblico non mostra i tipi di cartella nt:folder. NPR-23375: Hotfix per CQ-4242293
* Quando un componente è destinato a un’istanza di pubblicazione, un effetto sfarfallio rende brevemente visibile l’esperienza predefinita prima di quella di destinazione. NPR-23415: Hotfix per CQ-4242038
* (Console Adobe IMS) La configurazione del servizio AccessTokenProvider OSGi viene visualizzata nuovamente dopo l’eliminazione. NPR-23520: Hotfix per CQ-4208250
* Impossibile eseguire la replica dei riferimenti di configurazione con la struttura di cartelle intermedia. NPR-23485: Hotfix per CQ-4242751
* (Personalization) clientlib bloccato dal servlet proxy. NPR-23521: Hotfix per CQ-4240995
* (Console Adobe IMS) Le soluzioni Cloud registrate non vengono raccolte nella procedura guidata di configurazione. NPR-23977: Hotfix per CQ-4244549
* Ciclo infinito durante il caricamento di contenuto mirato su pagine senza estensione HTML. NPR-23522: Hotfix per CQ-4223600
* L&#39;attivazione non riesce per una pagina con riferimenti di configurazione Dynamic Tag Management ereditati. NPR-23485: Hotfix per CQ-4242751

**Piattaforma**

* (Interfaccia classica) (interfaccia utente touch) Il selettore tag non viene visualizzato e genera un’eccezione quando si tenta di cercare i tag tramite un predicato tag nello schema Ricerca risorse. NPR-23049: Hotfix per CQ-4239371
* (Interfaccia classica) I componenti che utilizzano xtype=tags restituiscono null e non possono essere selezionati dal eth elenco di tag. NPR-23050: Hotfix per CQ-4239937
* (Branding) La finestra di dialogo Opt-in menziona Adobe Marketing Cloud invece di Adobe Experience Cloud. NPR-23210: Hotfix per CQ-4237799
* L&#39;opzione Filtro rallenta AEM dopo l&#39;aggiornamento da 6.3 a 6.4. NPR-23260: Hotfix per CQ-4239847 (da controllare)
* Backport proattivo per correzioni granite.omnisearch.core. NPR-23536
* Backport proattivo per correzioni di platform.clientlibs . NPR-23569
* L&#39;ereditarietà della configurazione di Cloud Service non funziona quando si modificano altre proprietà della pagina. NPR-23216: Hotfix per CQ-4239782
* Abilitazione del supporto per STARTTLS in Day CQ Mail Service. NPR-23941: Hotfix per CQ-4240397

**Progetti**

* (Frammento di contenuto) La copia in lingua per la risorsa incorporata non viene creata mentre la risorsa in lingua inglese viene aggiunta alla traduzione. Hotfix per CQ-4243477
* Il menu a discesa di configurazione msft mostra la configurazione da /libs(6.4 configs) invece di da /etc(6.3 configs) in modalità legacy. Hotfix per CQ-4243475
* Promuovi ed elimina automaticamente i lanci di traduzione nei progetti di traduzione. Hotfix per CQ-4243474
* I frammenti di contenuto all’interno dei siti non vengono tradotti. Hotfix per CQ-4243482, CQ-4243483, CQ-4245687
* Errore del server all&#39;apertura del filtro di ricerca dei processi di traduzione. Hotfix per CQ-4236813
* Il menu a discesa della configurazione delle credenziali è vuoto anche dopo che tif è presente in /conf/we-retail. Hotfix per CQ-4236315
* KPI del progetto aperto: degradazione delle prestazioni durante la creazione di più progetti. NPR-23840: Hotfix per CQ-4238392
* Il flusso di lavoro Starter non è in grado di accettare il valore TypeHint di String. NPR-23863: Hotfix per CQ-4238356

**Community**

* Vulnerabilità di sicurezza nella versione 1.0 di Handlebars. NPR-23636: Hotfix per CQ-4243055
* L&#39;autorizzazione in blocco dei messaggi contrassegnati non funziona. NPR-23867: Hotfix per CQ-4243962
* Il valore predefinito non viene visualizzato sul pulsante di ordinamento nel componente forum. NPR-23882: Hotfix per CQ-4243375
* Problemi relativi alla consegna dei messaggi dai siti della community ai gruppi. NPR-23935

**Flusso di lavoro**

* Il servizio di notifica e-mail del flusso di lavoro Day CQ attiva un messaggio e-mail per ciascun nodo Mongo per le notifiche WorkflowCompleted e WorkflowAborted. NPR-22515: Hotfix per CQ-4238172
* L’esecuzione del flusso di lavoro della risorsa di aggiornamento DAM genera un NullPointerException. NPR-23010: Hotfix per GRANITE-21096
* Il passaggio Processo flusso di lavoro non visualizza gli script da /etc/workflow/scripts. NPR-23263: Hotfix per GRANITE-20775
* Workflow Dynamic Participant Step non visualizza gli script da /apps/workflow/scripts. NPR-23464: Hotfix per GRANITE-21276
* Impossibile modificare qualsiasi flusso di lavoro dopo averlo modificato una volta. NPR-23742: Hotfix per CQ-4238526
* (Interfaccia classica) Quando si modificano i moduli di avvio del flusso di lavoro, le condizioni scompaiono e i flussi di lavoro vengono avviati senza condizioni. NPR-23835: Hotfix per CQ-4239153
* Casella in entrata progetto: il passaggio alla visualizzazione calendario mostra il contenuto della casella in entrata principale. NPR-23947: Hotfix per CQ-4241236
* È necessario esporre i dettagli del payload nel bundle in modo che il componente HTL possa visualizzare il valore nella vista a elenco. NPR-23948: Hotfix per CQ-4240953
* Impossibile memorizzare i dati della finestra di dialogo nel passaggio Partecipante finestra di dialogo. NPR-23965: Hotfix per CQ-4234123
* (Interfaccia touch) Quando si salva un modello di flusso di lavoro, il pulsante &#39;Sincronizza&#39; diventa &#39;Sincronizzato&#39; e si verifica un errore ortografico. Hotfix per CQ-4244843
* Casella in entrata progetto: il passaggio alla visualizzazione calendario mostra il contenuto della casella in entrata principale. Hotfix per CQ-4244436
* Impossibile selezionare le finestre di dialogo nel passaggio Partecipante finestra di dialogo. Hotfix per CQ-4244532
* Backport proattivo per correzioni granite.omnisearch.core. NPR-23536
* Problema nell’app Mobile Workspace 6.4 con attività condivisa. NPR-26383

**WCM - Traduzione**

* (Pannello di riferimento) I lavori di traduzione non vengono eseguiti durante la creazione del progetto. Hotfix per CQ-4245327

**WCM - MSM**

* (MSM) Miglioramento delle prestazioni di rollout. Hotfix per CQ-4231488
* (MSM) Intervallo di tempo nell’ascolto degli eventi tra eventi effettivamente in corso e gestione degli eventi. Hotfix per CQ-4227766

**Screens**

* La pagina dello schermo non riesce con un errore a causa di dipendenze mancanti per screens-core-pkg:1.4.42. Hotfix per CQ-4245918

**Progetti - Traduzione**

* (Frammento di contenuto) La copia in lingua per la risorsa incorporata non viene creata mentre la risorsa in lingua inglese viene aggiunta alla traduzione. Hotfix per CQ-4243477
* Il menu a discesa di configurazione msft mostra la configurazione da /libs(6.4 configs)invece di da /etc(6.3 configs) in modalità legacy. Hotfix per CQ-4243475
* Promuovi ed elimina automaticamente i lanci di traduzione nei progetti di traduzione. Hotfix per CQ-4243474
* I frammenti di contenuto all’interno dei siti non vengono tradotti. Hotfix per CQ-4243482, CQ-4243483, CQ-4245687
* Errore del server all&#39;apertura del filtro di ricerca dei processi di traduzione. Hotfix per CQ-4236813
* Il menu a discesa della configurazione delle credenziali è vuoto anche dopo che tif è presente in /conf/we-retail. Hotfix per CQ-4236315

**Gestione dei frammenti di contenuto**

* L’eliminazione del componente riempie i registri con tracce di stack. Hotfix per CQ-4242315

**DAM - Generale**

* La chiusura della visualizzazione dettagliata di una risorsa restituisce una pagina dei risultati di ricerca non corretta. Hotfix per CQ-4240960
* (Camera Raw) L&#39;opzione Regolazione immagine è mancante. Hotfix per CQ-4246121
* IndexOutOfBoundException: Rapporto sulla modifica delle risorse OOTB. Hotfix per CQ-4239744
* Rimuovi il punteggio di affidabilità dal csv del rapporto. Hotfix per CQ-4241491
* Consegna e-mail condivisione link interrotta per il mittente non &quot;amministratore&quot;. Hotfix per CQ-4240357
* Correzione degli errori IT. Hotfix per CQ-4249891

**DAM - Brand Portal**

* Le proprietà della risorsa elencano solo 3 proprietà nella prima scheda, tutte le schede sembrano vuote. Hotfix per CQ-4242503
* I predicati tipo file e dimensione file non sono disponibili nel modulo di ricerca pubblicato. Hotfix per CQ-4242026
* La ricerca nel predicato della directory deve essere filtrata o non visualizzata nei filtri di ricerca. Hotfix per CQ-4241386
* La ricerca predefinita da deve esistere dopo l’annullamento della pubblicazione. Hotfix per CQ-4241383, CQ-4241113
* Il gesto di pubblicazione su brand portal non funziona per i predefiniti per immagini. Hotfix per CQ-4241074
* La pubblicazione in Brand Portal non funziona per le raccolte. Hotfix per CQ-4241122, CQ-4246558

**DAM - Client DM**

* L’aggiornamento alla versione 6.4 rimuove i profili di codifica video creati in precedenza. Hotfix per CQ-4244067
* L’attributo Testo Alt è interrotto nel componente Dynamic Media. Hotfix per CQ-4244081
* (DMS7) La modifica dei set remoti in AEM non viene sovrascritta in Scene7. Hotfix per CQ-4243430
* Verifica della versione 6.4 SP1 basata su DM Hybrid. Hotfix per CQ-4244623
* (DMS7-UA) Quando si fa clic sul pulsante Incorpora per una risorsa video pubblicata, non viene visualizzato nulla. La finestra di dialogo Incorpora deve essere visualizzata con codice HTML. Hotfix per CQ-4245237
* (DM ibrido) L&#39;URL della copia per le risorse video pubblicate o i set di file multimediali diversi ottiene &quot;`[object Object]`&quot; nella finestra di dialogo URL. Hotfix per CQ-4245236, CQ-4245451
* (DMHybrid) La pagina Vista dettagli video non contiene l’anteprima della visualizzazione della risorsa video e invia un messaggio di errore alla console. Hotfix per CQ-4244320
* Codifica automatica S7 del contenuto we.retail. Hotfix per CQ-4242253
* I predefiniti di elaborazione video pre-aggiornamento non possono avere un nuovo predefinito di codifica video aggiunto né modificare i predefiniti di codifica esistenti. Hotfix per CQ-4240407
* I predefiniti per immagini pre-aggiornamento vengono visualizzati come Non pubblicato nella pagina Rendering e non producono URL. Hotfix per CQ-4240406
* (CSS) Le risorse vengono visualizzate, ma i visualizzatori utilizzati sono predefiniti e non i visualizzatori OOTB. Hotfix per CQ-4239839
* Pulizia disattivata esecuzione manuale del passo di sospensione e uso delle classi di corallo private. Hotfix per CQ-4239729
* Il visualizzatore di immagini sta generando un errore e non visualizza il ritaglio avanzato corretto. Hotfix per CQ-4237564
* Il predefinito legacy sotto /etc sembra essere rotto e non migrato in posizione sotto /conf al momento del salvataggio. Hotfix per CQ-4237416
* Regressione in OOB VideoViewer 5.8.x - il visualizzatore espande l’iframe a destra, interrompendo così il layout della pagina. Hotfix per CQ-4235465
* (DMS7) I pulsanti URL di rendering ritaglio avanzato e Incorpora sono attivi per le immagini che non sono state pubblicate. Hotfix per CQ-4233696
* (DMHybrid) Ripristina la funzione di ritaglio/rotazione precedente. Hotfix per CQ-4239489
* Quando si visualizza l&#39;anteprima di un video nella vista a schede, il pulsante di riproduzione non si attiva/disattiva per mettere in pausa. Hotfix per CQ-4238592
* Quando si esegue un aggiornamento di Opt-in, la configurazione di YouTube non viene spostata/copiata dalla posizione precedente alla nuova posizione. Hotfix per CQ-4238590
* I profili di elaborazione video OOTB AVS DropTwo sono elencati in Proprietà cartella e solo uno contiene codifiche definite. Hotfix per CQ-4238096
* Ritaglio avanzato (DMS7): Vista dettagli: Il pulsante URL è etichettato Pulsante Copia per i rendering. Hotfix per CQ-4237804
* La pagina di elenco dei predefiniti per visualizzatori rimane vuota anche dopo l’esecuzione dei comandi curl. Hotfix per CQ-4243246
* Pulizia disattivata fase sospensione esecuzione manuale e uso di classi di corallo private. Hotfix per CQ-4239729
* La pagina Dettagli report video non mostra la risorsa video. Hotfix per CQ-4246208

**DAM - Servizi DM**

* Configurazione cloud (DMS7): Impossibile sincronizzare il nuovo contenuto con Scene7 dopo l&#39;aggiornamento a SP1. Hotfix per CQ-4244437
* (DMHybrid) I profili di colore e le impostazioni del catalogo non vengono registrati in una chiamata debug_info=catalog. Hotfix per CQ-4242346
* Aggiungi profili di colore alle impostazioni del cliente sui server di consegna. Hotfix per CQ-4241818, CQ-4241819
* (DMHybrid) dopo 6.3 &amp;gt; Aggiornamento 6.4, le impostazioni del catalogo vengono spostate nel nodo errato. Hotfix per CQ-4239974, CQ-4239975
* Lo script (DMHybrid) pushviewerpresets non crea i nodi necessari per modificare le impostazioni del catalogo. Hotfix per CQ-4240076
* Quando si utilizza la selezione a discesa &quot;Formato&quot; e si selezionano i formati PNG o JPG, il file scaricato viene visualizzato come sovrasaturato e più scuro della risorsa originale. Hotfix per CQ-4240073
* (DMS7) Rimuovi la mappatura del tipo MIME: image_x-eps. Hotfix per CQ-4240394
* (DMS7) I parametri di caricamento per lo sfondo di eliminazione non passano il file ipsApiService.log e quindi non funzionano. Hotfix per CQ-4240686
* L’aggiornamento dei profili di elaborazione delle immagini creati in un’istanza da 6.3 a 6.4 interrompe la proprietà &quot;tipo di ritaglio&quot;. Hotfix per CQ-4237739
* (Dynamic Media) Il caricamento di risorse regolari all’esterno della cartella smartcrop non riesce. Hotfix per CQ-4237670
* Regola il codice di fallback del profilo per &quot;Codifica video adattiva&quot; su &quot;Adaptive_Video_Encoding&quot;. Hotfix per CQ-4237666
* I dati EmbedXMP sono sempre impostati su “active” per il processo di generazione Ptiff. Hotfix per CQ-4234498
* Il rendering dell&#39;immagine CMYK presenta una saturazione non corretta. Hotfix per CQ-4235470
* Le impostazioni di Image Server non vengono replicate nella distribuzione mentre i log di replica li contrassegnano con successo. Hotfix per CQ-4239480, CQ-4239046
* (DMS7) Impossibile creare i set utilizzando riferimenti vecchi/nuovi alla configurazione cloud. Hotfix per CQ-4238078
* Il passaggio del flusso di lavoro Scene7 legge solo Scene7 nel nome e nella descrizione, ma non chiarisce il passaggio del flusso di lavoro nel flusso di lavoro DAM Update. Hotfix per CQ-4237865

**DAM - Tag avanzati**

* Introduzione [Tag avanzati migliorati](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951

**Forms**

Le correzioni per AEM Forms vengono distribuite tramite pacchetti di componenti aggiuntivi e altri programmi di installazione delle patch forniti con la versione. Per informazioni dettagliate, consulta Versioni di AEM Forms.

Gli elementi di rilievo di AEM Forms sono:

* AEM Forms introduce [capacità rapporti sulle transazioni](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) per tenere traccia e tenere conto delle transazioni come i moduli inviati, i documenti elaborati e i documenti di cui è stato eseguito il rendering nella distribuzione AEM Forms. Fornisce informazioni sull’utilizzo dei prodotti e aiuta gli utenti aziendali a comprendere i volumi di elaborazione digitale.
* Abilitazione del supporto PDF/UA per i moduli XML.
* Aggiunto allowProxy = true per Clientlib **aemfd.ccm.channel.contentpage**
* È stato aggiornato il codice per effettuare la ricerca avanzata del titolo come contiene anziché uguale a.
* Aggiornamento alla nuova versione di Node Package Manager (NPM) su Continuous Integration Machine.

**Pacchetto di componenti aggiuntivi per Forms**

**Integrazione con il back-end**

* Viene generato un errore quando si fornisce null come valore a un campo facoltativo. NPR-24397
* La chiamata WSDL non riesce quando l’elemento ha uno spazio dei nomi diverso dallo spazio dei nomi globale. NPR-24281
* (WSDL FDM) Ottenimento di DermisException: Dati elenco esclusi in caso di array di tipo di proprietà. NPR-24265
* (WSDL FDM) Ottenimento di DermisException: java.lang.Exception: createSOAPParam: Parametri non validi. NPR-24264
* (FDM Client SDK) Impossibile eseguire il test del preprocessore/post e dell&#39;azione di invio personalizzata. Hotfix per CQ-4238469
* Correzioni per problemi Javadoc in Dermis. Hotfix per CQ-4244250
* Input migliorato in WSDL (Web Services Description Language). Hotfix per CQ-4244133
* Il test di autenticazione di base per WSDL genera errori diversi per la stessa configurazione in AEM 6.3 e AEM 6.4. Hotfix per CQ-4244132
* Richiesta di includere ValueUtil in client-sdk e javadocs. Hotfix per CQ-4242803
* (Configurazione cloud FDM) Impossibile configurare l&#39;autenticazione basata su SOAP dalla configurazione cloud. Hotfix per CQ-4238462
* Dermis - Aggiungi i pacchetti mancanti in Javadocs. Hotfix per CQ-4242815
* WSDLInvokerParams da includere nell’sdk client Forms Add-On. NPR-23381: Hotfix per CQ-4240233

**Moduli adattivi**

* Il rendering del documento (IC) deve essere registrato come una transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4245333
* Durante l&#39;esecuzione di UAT5, una voce manca nel pdf generato nella fase di verifica. Hotfix per CQ-4243184
* Caso di test per una copia approfondita di guideContext. Hotfix per CQ-4242924
* Campo del tipo di bozza mancante durante l’esecuzione dell’UAT3 sul server aggiornato più recente. Hotfix per CQ-4243120
* Sul server aggiornato, nel modulo inviato mancano i valori Stato/Provincia/Regione e Paese presenti sul server di pre-aggiornamento. Hotfix per CQ-4241444
* (ExpressionEditor) Errore durante la navigazione alla fase Verifica durante l’invio del modulo. Hotfix per CQ-4241384
* Mancano valori nella fase di verifica nella fase di pre-aggiornamento e nel server aggiornato per il modulo inviato. Hotfix per CQ-4241896
* Il pulsante Esci e salva nella parte inferiore della pagina non funziona. Hotfix per CQ-4240112
* Numero di contatto mancante nella configurazione aggiornata. Hotfix per CQ-4239870
* Sotto `ACTION TAKEN` nella sezione della scheda Tipo di controversia , &quot;Documenti aggiuntivi per supportare la mia attestazione&quot; è presente un campo aggiuntivo Tipo di prova salvato &quot;in esso. Hotfix per CQ-4239873
* Errore in getDataAPI durante il passaggio verifyPdf. Hotfix per CQ-4239865
* Errori nei registri di migrazione per l’istanza di authoring e pubblicazione. Hotfix per CQ-4239365
* Errori nei registri di migrazione per l’istanza di authoring e pubblicazione. Hotfix per CQ-4239635
* Errore di deserializzazione come &quot;Deserializzazione non consentita per la classe sun.util.calendar.ZoneInfo&quot; nei registri di errore dopo l&#39;invio di un Modulo adattivo. Hotfix per CQ-4240419
* Il campo Stato non viene compilato nel rendering del modulo Mobile. Hotfix per CQ-4240597
* Rimuovere l&#39;utilizzo di riferimento dei componenti nei modelli dall&#39;elenco anti-pattern. Hotfix per CQ-4239217
* La casella numerica di HTML5 impostata come Mobile o Decimal restituisce risultati di convalida diversi in browser diversi. NPR-23528: Hotfix per CQ-4244097
* (Caricamento immagine) L&#39;immagine non viene visualizzata nell&#39;anteprima DOR. Hotfix per CQ-4243178
* Il server JEE genera un errore durante il tentativo di invio del modulo adattivo con &quot;E-mail PDF&quot; e &quot;Includi allegati&quot;. Hotfix per CQ-4239894
* Il grafico non viene tracciato in fase di runtime utilizzando tabella/pannello. Hotfix per CQ-4240010
* L’invio del modulo adattivo non funziona e non viene eseguita alcuna modifica nel conteggio delle transazioni a causa di un errore di invio. Hotfix per CQ-4246125
* (Scelta immagine) Le opzioni del documento non sono visibili. Hotfix per CQ-4236976
* L’interfaccia utente dell’editor modelli non è stabile. Hotfix per CQ-4241497
* Gli AF non vengono visualizzati utilizzando la scheda delle risorse del pannello laterale, mentre vengono visualizzati utilizzando l’opzione Sfoglia per AEM finestra di dialogo delle proprietà dei componenti modulo. Hotfix per CQ-4236751
* L’ID flusso di lavoro generato per la conversione del modulo deve essere disponibile nel modulo adattivo generato. Hotfix per CQ-4240014
* Impossibile selezionare il modello per creare una pagina nei siti in aggiornamento diretto: Livecycle sul server 6.4. Hotfix per CQ-4241300

**Servizio assemblatore**

* Registrazione delle transazioni nei servizi di assemblaggio. Hotfix per CQ-4245018, CQ-4245017, CQ-4245016.
* La transazione non viene segnalata quando la conversione PDF/A viene effettuata utilizzando DDX. Hotfix per CQ-4246039

**Forms Manager**

* Elenco dei pulsanti CREA FM in ordine alfabetico. Hotfix per CQ-4242307

**Portale moduli**

* Le bozze salvate sul server di pre-aggiornamento non si aprono correttamente sul server aggiornato. Hotfix per CQ-4243303
* Aggiornamento della versione 7.1 per adobe-formsmanager-core-module. Hotfix per CQ-4245753
* Le bozze salvate sul server di pre-aggiornamento non si aprono correttamente sul server aggiornato. Hotfix per CQ-4243303
* Gli scenari di allegato si interrompono quando si sostituiscono/aggiungono/rimuovono allegati in una nuova istanza/stessa istanza di bozza. Hotfix per CQ-4243165
* Il conteggio delle bozze recuperate dalla query del database è maggiore del conteggio delle bozze presenti nel portale. Hotfix per CQ-4241489
* Forms inviato sul server di pre-aggiornamento non è presente sul server aggiornato. Hotfix per CQ-4241490
* Il modulo visualizzato nell’interfaccia utente nella scheda Invia è in stato Non inviato nonostante il messaggio di invio sia stato inviato correttamente. Hotfix per CQ-4241487
* Il guideContext deve essere formato copiando in profondità i campi come guideContext contiene customPropertyMap che è un oggetto. Hotfix per CQ-4240126
* Errore durante il tentativo di salvare un modulo. Hotfix per CQ-4240763
* La voce per i moduli salvati e inviati viene compilata in crx/de nonostante la configurazione del database sia specificata in Configurazione bozza e invio di Forms Portal. Hotfix per CQ-4240726
* (Ricerca e filtro) Il valore fisso del titolo di ricerca avanzato deve funzionare come contiene anziché come uguale. Hotfix per CQ-4245499

**Forms Mobile**

* Il campo data si sovrappone in Mobile Forms. Hotfix per CQ-4242256
* L’invio del modulo per Mobile Forms deve essere registrato come transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4246166
* L’invio del modulo in FormSet deve essere registrato come transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4246165

**App AEM Forms**

* (App Windows) Impossibile eseguire il rendering del modulo. Hotfix per CQ-4238005

**Workflow OSGI**

* Registrazione delle transazioni nell&#39;attività Assegna flusso di lavoro. Hotfix per CQ-4244440
* (Passaggio FDM) Impossibile utilizzare i valori dai metadati del flusso di lavoro quando viene inserito un passaggio Assegna attività tra il passaggio del processo e il passaggio fdm. Hotfix per CQ-4241472
* La delega dell’attività di assegnazione non funziona nell’integrazione Forms nei flussi di lavoro OSGI. NPR-23709: Hotfix per CQ-4243700
* (Editor modello flusso di lavoro) Alcuni modelli di flusso di lavoro non sono modificabili tramite l’editor modelli WF ClassicUI. Hotfix per CQ-4241151

**Documento multicanale**

* Il campo data in Modello si sovrappone al sottomodulo nell’authoring IC. Hotfix per CQ-4240110
* L’intestazione non deve essere eliminata o spostata verso l’alto o il basso nell’authoring dei canali web IC. Hotfix per CQ-4243358
* (IC Editor) Le righe predefinite devono essere impostate su 1 per i componenti Tabella. Hotfix per CQ-4244848
* Area di destinazione per rimanere visibile anche dopo che il contenuto è stato trascinato e rilasciato. Hotfix per CQ-4244534
* Il canale Web non riconosce lo spazio delle schede nei frammenti di documento di testo. Hotfix per CQ-4244481
* (Canale di stampa) Il rendering del documento (IC) deve essere registrato come una transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4245335
* (Canale Web) Il rendering del documento (IC) deve essere registrato come una transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4245334
* La ricerca nel contenitore di documenti o nell’albero del modello dati deve essere unificata alla ricerca nel filtro delle risorse. Hotfix per CQ-4242305
* (Frammento di documento) La proprietà indentazione fa rientrare il testo in base al numero di unità che non è possibile comprendere. Hotfix per CQ-4241082, CQ-4240643
* (IC Editor) L’icona Modifica frammento nella sezione del frammento di documento elencata nella scheda Risorse non è facilmente individuabile e comprensibile. Hotfix per CQ-4241047
* Consenti accesso anonimo alla libreria client inaccessibile IC Anonymous. Hotfix per CQ-4245588
* (Canale Web) I dati non vengono risolti in nessuna delle tabelle nell’anteprima Web e vengono visualizzati come vuoti. Hotfix per CQ-4244476
* Le intestazioni di tabella vengono visualizzate come variabili nel canale web durante la generazione automatica. Hotfix per CQ-4244242
* (IC Editor) Il contenuto di un frammento di documento utilizzato in un IC deve essere ridimensionato automaticamente per adattarsi alla larghezza dell’area di destinazione. Hotfix per CQ-4244094
* Il nome del canale mostrato nella parte superiore centrale deve essere coerente con il titolo IC per WEB / PRINT. Hotfix per CQ-4242498
* Editor di testo Il pannello oggetto dati deve elencare solo le entità di livello superiore, Hotfix per CQ-4244121
* Il nome predefinito non viene assegnato quando si aggiunge un nuovo componente nell’editor. Hotfix per CQ-4244691
* Aggiunta della configurazione Colspan in tutti i componenti del canale web. Hotfix per CQ-4244946
* La proprietà Larghezza tabella frammento di layout non viene reimpostata e rispettata nel canale di stampa della comunicazione al cliente o lettera. Hotfix per CQ-4241574

**Gestione della corrispondenza**

* Le didascalie vengono rimosse dal modello di lettera dopo la modifica di una risorsa di testo contenente segnaposto. NPR-24196
* Il file XDP, quando caricato e utilizzato come layout per i modelli di lettera, non riesce a visualizzare in anteprima o modificare i modelli. NPR-24143: Hotfix per CQ-4244407
* La selezione dell&#39;assegnazione è selezionata per impostazione predefinita nel frammento elenco. Hotfix per CQ-4240097
* Editor condizioni : la valutazione di più risultati deve essere abilitata per impostazione predefinita. Hotfix per CQ-4240096
* L&#39;immagine eliminata da Elenco mostra ancora l&#39;immagine in anteprima. Hotfix per CQ-4239909
* La regola impostata sul modulo condizione viene impostata come &#39;Predefinito&#39; per tutti i moduli. Hotfix per CQ-4239878
* La creazione del dizionario dati non riesce con l&#39;errore &quot;Eccezione JCR sconosciuta&quot;. Hotfix per CQ-4244122
* Gap in JavaDocs di contenuto 6.3. Hotfix per CQ-4213586

**Programma di installazione di JEE per Forms**

**Core**

* (HTML Workspace) Dettagli di tracciamento mancanti per le applicazioni il cui nome contiene il simbolo delle parentesi. NPR-23402

**Servizio PDFG**

* Registrazione delle transazioni nei servizi PDFG. Hotfix per CQ-4244951, CQ-4244586
* Riduzione dei PDF tramite l’annullamento selettivo dei font tramite una singola chiamata API. NPR-23287
* Problema di aggiornamento delle configurazioni del PDFG durante AEM aggiornamento. Hotfix per CQ-4241176
* Registrazione delle transazioni nel servizio PDFUtility. Hotfix per CQ-4245014

**Gestione processi**

* (Workspace HTML) I punti iniziali del processo non sono visualizzati in ordine alfanumerico. Hotfix per CQ-4239629
* (Area di lavoro di HTML) Prepara la chiamata dei dati in arrivo due volte quando la bozza viene aperta la prima volta. Hotfix per CQ-4243280
* (HTML Workspace) Il processo di preparazione dei dati viene attivato durante la chiusura di un modulo. Hotfix per CQ-4239456
* Lo spazio di lavoro si blocca quando viene attraversato tra due attività. Hotfix per CQ-4237125

**Workbench**

* Gestisci profilo azione Il processo di preparazione dei dati non riesce quando la configurazione predefinita del processo di rendering è impostata su HTML. Hotfix per CQ-4244292

**Forms Designer**

* Aggiunta del supporto per PDF/UA ai moduli XML generati tramite Designer e il servizio Output. NPR-23022
* Ai collegamenti ipertestuali inline definiti in Designer non vengono assegnati tag né testo alternativo se vengono salvati in formato PDF da Designer. NPR-23023

**Feature Pack inclusi**

**Risorse**

* Aggiunta della funzionalità per tag avanzati migliorati. Per ulteriori informazioni, consulta [Tag avanzati migliorati](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951: Hotfix per CQ-4234883
* Introduzione ai riferimenti AEM Assets in InDesign. Per ulteriori informazioni, consulta [Riferimenti AEM Assets in InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sites**

* (Authoring delle pagine) Miglioramenti all’Editor immagini. Per ulteriori informazioni, consulta [Editor immagini](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24267: Hotfix per CQ-4245502

**Bundle OSGi e pacchetti di contenuti inclusi**

Nei documenti di testo seguenti sono elencati i bundle OSGi e i pacchetti di contenuti inclusi nel CFP.

Elenco dei bundle OSGi inclusi in AEM 6.4.1.0

[Ottieni file](assets/6_4_1_0_bundle-list.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.1.0

[Ottieni file](assets/6_4_1_0_content-package-list.txt)

### Installare la versione 6.4.8.0 {#install}

#### Requisiti di configurazione {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Per i clienti con Feature Pack installati su AEM 6.4. I Feature Pack opzionali forniti da Adobe hanno dipendenze dalla versione di rilascio e dal service pack. Se hai installato un Feature Pack, contatta il team di assistenza clienti AEM per verificare la compatibilità di tali feature pack con questo service pack per AEM 6.4.

* AEM 6.4.8.0 richiede AEM 6.4. Per ulteriori informazioni, vedere [documentazione di aggiornamento](../sites-deploying/upgrade.md).
* Il download del Service Pack è disponibile su [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html) per il download.
* In una distribuzione con MongoDB e più istanze, installa AEM 6.4.8.0 in una delle istanze Autore tramite Gestione pacchetti.
* Prima di installare il Service Pack, assicurati di disporre di uno snapshot o di un nuovo backup dell’istanza AEM.
* Riavvia l’istanza prima dell’installazione. Anche se questo è necessario solo quando l’istanza è ancora in modalità di aggiornamento (e questo accade quando l’istanza è stata appena aggiornata da una versione precedente), si consiglia generalmente se l’istanza è in esecuzione per un periodo di tempo più lungo.

>[!NOTE]
>
>Adobe sconsiglia la rimozione o la disinstallazione del pacchetto AEM 6.4.8.0.

### Installare il Service Pack tramite Gestione pacchetti {#install-the-service-pack-via-package-share}

Per installare il Service Pack in un’istanza AEM 6.4 esistente, effettua le seguenti operazioni:

1. Scarica il pacchetto da Distribuzione di software.

1. In AEM, accedi a Gestione pacchetti e aggiungi il pacchetto scaricato AEM 6.4.8.0. Seleziona il pacchetto caricato e fai clic su **[!UICONTROL Installa]**.

>[!NOTE]
>
>**La finestra di dialogo nell’interfaccia utente di Gestione pacchetti talvolta si chiude prematuramente durante l’installazione della versione 6.4.8.0**
>
>È consigliabile attendere che i registri degli errori si stabilizzino prima di accedere all’istanza. L’utente deve attendere i registri specifici relativi alla disinstallazione del bundle dell’aggiornamento prima di assicurarsi che le installazioni abbiano esito positivo. Il problema si verifica in genere in Safari, ma può accadere in modo intermittente in qualsiasi browser.

### Installazione automatica {#auto-installation}

Esistono due modi per installare automaticamente AEM 6.4.8.0 in un’istanza in esecuzione:

A. Inserisci il pacchetto in ..*/crx-quickstart/install* mentre il server è in esecuzione. Il pacchetto viene installato automaticamente.

B. Utilizza il [API HTTP da Gestione pacchetti](/help/sites-administering/package-manager.md) - assicurati di utilizzare `cmd=install&recursive=true` - in modo che il pacchetto nidificato sia installato.

>[!NOTE]
>
>AEM 6.4.8.0 non supporta l’installazione tramite bootstrap.

### Convalidare l’installazione {#validate-install}

1. La pagina Informazioni prodotto (*/system/console/ productinfo *) dovrebbe ora mostrare la stringa di versione aggiornata &quot;Adobe Experience Manager, versione 6.4.8.0&quot; in Prodotti installati.
1. Tutti i bundle OSGi risultano come ATTIVI o FRAMMENTI nella console OSGi (usa la console web: /system/console/bundles).
1. Il bundle OSGI org.apache.jackrabbit.oak-core è nella versione 1.8.17 o successiva (Usa la console Web: /system/console/bundles).

Per determinare la piattaforma certificata da eseguire con questa versione di AEM Sites e Assets, consulta [Requisiti tecnici](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Quando l&#39;installazione del pacchetto è riuscita, viene visualizzato un messaggio informativo che indica che il pacchetto contenuto >è stato installato correttamente, ad esempio **&quot;Pacchetto di contenuti AEM-6.4-Service-Pack-7 installato correttamente.&quot;**

### Aggiornare i visualizzatori Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.8.0 contiene una nuova versione dei visualizzatori Dynamic Media (5.10.1) che consente di verificare la presenza di nomi duplicati nella pagina Predefiniti immagine. Consigliamo ai clienti Dynamic Media di eseguire il seguente comando per portare i predefiniti visualizzatore predefiniti pronti per l’uso in uno stato aggiornato.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

che copierà i nuovi predefiniti visualizzatore nella posizione /conf.

### Installare il pacchetto di componenti aggiuntivi per AEM Forms {#install-aem-forms-add-on-package}

#### Installare il componente aggiuntivo per AEM Forms {#installaemformsaddon}

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms. Le correzioni apportate in AEM Forms vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi.

>[!NOTE]
>
>AEM 6.4.8.0 include una nuova versione del [pacchetto di compatibilità di AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). Se utilizzi una versione precedente del pacchetto di compatibilità di AEM Forms e aggiorni a AEM 6.4.8.0, installa la versione più recente del pacchetto di compatibilità di AEM Forms dopo l’installazione del pacchetto aggiuntivo di Forms.

1. Assicurati di aver installato il Service Pack di AEM.
1. Scarica il pacchetto corrispondente dei componenti aggiuntivi per Forms elencato in [Versioni di AEM Forms](https://helpx.adobe.com/it/aem-forms/kb/aem-forms-releases.html) per il sistema operativo in uso.
1. Installa il pacchetto aggiuntivo dei moduli come descritto in [Installazione dei pacchetti aggiuntivi per moduli AEM](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installare il programma di installazione di JEE per AEM Forms {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms in JEE. Le correzioni apportate a JEE per AEM Forms vengono distribuite tramite un programma di installazione separato.

Per informazioni sull&#39;installazione del programma di installazione cumulativo per JEE per AEM Forms e sulla configurazione post-distribuzione, vedi [Modulo di installazione di patch JEE per AEM Forms 0015](https://helpx.adobe.com/it/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### Impostazioni di configurazione richieste per NPR-21268 {#configuration-settings-required-for-npr}

Se utilizzi l’interfaccia classica (vecchia) e hai creato modelli di metadati utilizzando essa, segui i passaggi per eseguire lo script JMX per preservarli -

1. Vai a /system/console/jmx.
1. Fai clic su &quot;Migra modelli di metadati&quot;.
1. Fai clic su &quot;migrateMetadataTemplatesAtPath&quot; e fornisci il percorso della cartella in cui vuoi mantenere i modelli di metadati.

#### Impostazioni di configurazione richieste per NPR-24536 {#configuration-settings-required-for-npr-1}

Quando un utente richiede un’attività, per impostazione predefinita il conteggio della coda condivisa non viene aggiornato per gli altri utenti. Per questo è stata introdotta una nuova proprietà. Per configurare questa proprietà in un’istanza di AEM, segui la procedura seguente:

1. Accedi all’interfaccia utente Amministratore -> Servizi -> Area di lavoro -> Amministrazione globale.
1. Esporta le impostazioni globali.
1. Nel file XML scaricato, aggiungi il tag . &lt;client_taskspollinginterval>10&lt;/client_taskspollinginterval> In questo caso, 10 è il valore di esempio in secondi. È possibile modificarlo in base alle proprie esigenze.
1. Salva il file.
1. Torna all’interfaccia utente Amministratore -> Servizi -> Area di lavoro -> Amministrazione globale.
1. Importa il file XML nella sezione Importa impostazioni globali.
1. Ora puoi uscire dal sistema e accedere di nuovo.
1. Il conteggio della coda condivisa si aggiorna anche per gli altri utenti dell’area di lavoro.
1. Per disattivare il limite di polling, impostare il valore su 0 e importare di nuovo il file XML.

### JAR Uber {#uber-jar}

Il Jar Uber per AEM 6.4.8.0 è disponibile nella sezione [Archivio Maven pubblico Adobe](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/).

Per utilizzare il file JAR Uber in un progetto Maven, consulta l’articolo [Come utilizzare il file JAR Uber](../sites-developing/ht-projects-maven.md) e includi nel POM del progetto la seguente dipendenza:

```shell
<dependency>
      <code>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

### Funzioni rimosse/obsolete {#removed-deprecated-features}

In questa sezione sono elencate le funzionalità rimosse o dichiarate obsolete in AEM 6.4.

| Area | Funzione obsoleta | Sostituzione | Versione |
|---|---|---|---|
| Risorse | Gestione azione tag per le risorse secondarie | Nessuna sostituzione | AEM 6.4.2.0 |
| Integrazione di Assets con Adobe Creative Cloud | La [condivisione cartelle da AEM a Creative Cloud](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) è stata introdotta in AEM 6.2 per consentire agli utenti creativi di accedere alle risorse da AEM. Una nuova funzionalità introdotta nell’applicazione Creative Cloud, Adobe Asset Link, offre un’esperienza utente migliore e un accesso più efficace alle risorse da AEM direttamente da Photoshop, InDesign e Illustrator. Adobe non apporterà ulteriori miglioramenti alla funzionalità di condivisione cartelle. Mentre la funzione è inclusa in AEM, i clienti sono invitati a utilizzare la sostituzione. | Adobe Asset Link o app desktop. Per ulteriori informazioni, consulta l’articolo sull’[integrazione di AEM con Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

### Problemi noti {#known-issues}

* Durante l&#39;installazione possono essere visualizzati i seguenti errori e avvisi:

   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Timeout in attesa del completamento della modifica del registro.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` Non è stata trovata alcuna finestra di manutenzione in granite/operations/maintenance
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: Il metodo unbindEdit ha generato un&#39;eccezione (java.lang.IllegalStateException: Servizio già non registrato).
Questi errori non richiedono alcuna azione in quanto non influiscono sull’istanza AEM.

### Problemi risolti {#resolved-issues}

**AEM 6.4.4.0**

* Durante l&#39;importazione/esportazione dei metadati non viene rilevato alcun errore di risorsa. CQ-4253263
* Impossibile modificare alcun componente immagine e proprietà di pagina dopo l&#39;applicazione della versione 6.4.3.0 sulla versione 6.4.2.0. CQ-4260316 e CQ-4260441 Per risolvere questo problema:
   * Vai a Gestione pacchetti
   * Reinstalla il pacchetto &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot;
   * Ricompila tutti i JSP `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` O Riavvia l&#39;istanza.

### Bundle OSGi e pacchetti di contenuti inclusi {#osgi-bundles-and-content-packages-included}

Nei documenti di testo seguenti sono elencati i bundle OSGi e i pacchetti di contenuti inclusi in AEM 6.4.8.0.

Elenco dei bundle OSGi inclusi in AEM 6.4.8.0

[Ottieni file](assets/6.4.8.0_osgi_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.8.0

[Ottieni file](assets/6.4.8.0_content_packages.txt)

### Risorse utili {#helpful-resources}

* [Note sulla versione di AEM 6.4](../release-notes/release-notes.md)
* [Pagina del prodotto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentazione di AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64.html?lang=it)
* Abbonati ad [Adobe priority product update](https://www.adobe.com/subscription/priority-product-update.html)

### Siti con limitazioni {#restricted-sites-new}

Questi siti sono disponibili solo per i clienti. Se sei un cliente e hai bisogno di accedere, contatta il manager del tuo account Adobe.

* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/).
* Aggiornamenti dei prodotti, patch e pacchetti per funzionalità aggiuntive su [Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Assistenza clienti tramite Admin Console](https://adminconsole.adobe.com/). Per ulteriori informazioni, consulta [Nuova esperienza di accesso all’Assistenza clienti di Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
