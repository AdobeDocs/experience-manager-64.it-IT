---
title: Note sulla versione di AEM 6.4 Service Pack
seo-title: Note sulla versione di AEM 6.4 Service Pack
description: Note sulla versione specifiche di Adobe Experience Manager 6.4 Service Pack.
seo-description: Note sulla versione specifiche di Adobe Experience Manager 6.4 Service Pack.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
translation-type: tm+mt
source-git-commit: 1d02401f6b1946062eb238baa2fb70bbd47881a6

---


# Note sulla versione di AEM 6.4 Service Pack {#aem-service-pack-release-notes}

## Informazioni sulla versione {#release-information}

| Prodotti | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versione | 6.4.7.0 |
| Tipo | Versione Service Pack |
| Data | 12 dicembre 2019 |
| URL di download | AEM 6.4.7.0 on [PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/servicepack/AEM-6.4.7.0) |

## Funzionalità incluse in AEM 6.4.7.0 {#what-s-included-in-aem}

AEM 6.4.7.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**

È inoltre cumulativo, il che significa che 6.4.7.0 include tutte le versioni dei Service Pack di AEM 6.4 precedenti.

Alcuni degli elementi di rilievo di AEM 6.4.7.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.17.
* È stato aggiunto il supporto per impostare la versione di una pagina Siti durante l&#39;eliminazione.
* La nuova colonna relativa alla data di creazione, ordinabile, è stata aggiunta nella vista a elenco **DAM e nei risultati della ricerca delle risorse nella vista a** elenco **** (NPR-31311).
* È stato consentito l’ordinamento delle risorse in base alla colonna **Nome** nella visualizzazione **Elenco** .
* Le dimensioni batch e il timeout del passaggio del flusso di lavoro per la rielaborazione e il caricamento batch ora sono configurabili dall’interfaccia utente in Contenuti multimediali dinamici.
* L’impostazione `pdfBrochure` è stata impostata su false nella configurazione cloud di Scene 7 per risparmiare memoria su IPS.

## Elenco delle modifiche {#list-of-changes}

### Assets {#assets}

**Miglioramenti dei prodotti**

* La versione di esportazione del pacchetto API `package com.day.cq.dam.handler.standard.msoffice` supportata dal `dam-handler` bundle viene aggiornata a 6.0.0 (CQ-4279059).
Se state utilizzando il pacchetto `com.day.cq.dam.handler.standard.msoffice` nella vostra implementazione personalizzata, si consiglia di compilare il `dam-handler` bundle con l&#39;ultimo jar uber.

**Problemi risolti**

* I metadati di alcuni documenti PDF non vengono aggiornati e salvati nel PDF quando si modifica il titolo (NPR-31575).

* Impossibile eliminare le risorse con il simbolo &quot;+&quot; nel nome del file (NPR-30588).

* Le proprietà delle cartelle DAM non mostrano gli utenti o i gruppi aggiunti (creati dalla sincronizzazione LDAP) nei gruppi di utenti chiusi (NPR-30555).

* I caratteri speciali che si verificano nella riga Oggetto dei modelli e-mail non vengono visualizzati correttamente (NPR-30547).

* I nomi delle risorse vengono modificati in lettere maiuscole quando si spostano le risorse da una cartella all’altra in AEM, in esecuzione in modalità di esecuzione Dynamic Media Scene 7 (NPR-31631).

* In Scene 7, i nomi dei set di immagini vengono modificati in minuscolo quando viene creato un set di immagini (o un set di file multimediali) con una convenzione di denominazione appropriata in DAM (NPR-31576).

* Il flusso di lavoro Codifica video elemento multimediale dinamico non riesce a generare la miniatura per il video migrato da Scene7 a Contenuti multimediali dinamici - Modalità di esecuzione di Scene7 (NPR-31523).

* Errore interno del server durante l’utilizzo del filtro per la ricerca dei set, in AEM su elemento multimediale dinamico - Modalità di esecuzione di Scene7 (NPR-31388).

* Durante la modifica di un set di immagini remoto, si verifica un errore per l’immagine che risiede nella cartella denominata come nome della società Scene 7 (NPR-31347).

* Le risorse contenenti riferimenti non vengono pubblicate (DM) (NPR-31179).

* Il valore di scadenza (durata della cache cliente) configurato per la modalità ibrida di Dynamic Media non viene replicato nell’ambiente di distribuzione di Dynamic Media (NPR-31126).

* I caricamenti da AEM Dynamic Media - La modalità di esecuzione di Scene7 su Scene7 richiedono troppo tempo per essere completati (NPR-30926).

* Dopo aver creato una pagina con un componente Contenuti multimediali dinamici durante la pubblicazione dello stesso elemento, dall’istanza di creazione in esecuzione su Contenuti multimediali dinamici - Modalità di esecuzione di Scene7, all’utente viene richiesto di pubblicare la configurazione dmscene7 (NPR-30880).

* Il valore del parametro &quot;asset&quot; nel codice da incorporare del visualizzatore rimane invariato dopo la modifica dei valori in &quot;Titolo dopo lo spostamento&quot; e &quot;Nome dopo lo spostamento&quot; nel campo Contenuti multimediali dinamici - Scene7 (NPR-30745).

* La pagina dei risultati della ricerca nell&#39;interfaccia touch (realizzata tramite Omnisearch) scorre automaticamente verso l&#39;alto e perde la posizione di scorrimento dell&#39;utente (NPR-31306).

* DAM Event Purge elimina i dati evento più recenti (maxSavedActivities) e li contiene i dati creati in precedenza (NPR-30870).

* La modifica del titolo e del nome della risorsa non è persistente dopo l&#39;operazione di spostamento in una cartella di destinazione che attiva lo scorrimento infinito durante la selezione (NPR-30647).

* Le raccolte vengono rimosse dalla visualizzazione quando si applica un filtro in Risorse AEM a cui si accede da Adobe Asset Link (CQ-4280534).

* Le dimensioni batch e il timeout del passaggio del flusso di lavoro per la rielaborazione e il caricamento batch non sono configurabili dall’interfaccia utente e devono essere impostati in CRXDE. Il flusso di lavoro deve essere sincronizzato due volte (CQ-4281254).

* Il nome del passaggio del flusso di lavoro per il caricamento batch e il caricamento semplice è lo stesso in Scene 7, con conseguente confusione (CQ-4281176).

* Se a una risorsa manca il nodo di metadati (CQ-4281170), il flusso di lavoro di rielaborazione si blocca.

* Il passaggio BatchUpload nel flusso di lavoro di rielaborazione non funziona per la cartella contenente una risorsa video (CQ-4280630).

* Per impostazione predefinita, le opzioni PDF inviate a DM contengono extractKeywords impostata su true (CQ-4280101).

* Eccezione punto nullo durante l’esecuzione del flusso di lavoro di rielaborazione di Scene7 in una cartella contenente risorse non-DM (CQ-4279555).

* La ridenominazione delle risorse in AEM non viene sincronizzata sulla scena 7, quando una risorsa con un nome duplicato esiste già in Scene7 (CQ-4276763).

* Il file ZIP inviato per e-mail per il download delle risorse non riesce a decomprimere quando un utente con le autorizzazioni di lettura tenta di aprirlo (CQ-4277925).

* Il flusso di lavoro rappresentazioni PPT non genera le rappresentazioni dei file PPT caricati, in quanto AEM 6.4 non viene aggiornato alla versione 2.0.28 (CQ-4279059).

* I file PDF non sono indicizzati e il contenuto al loro interno non è ricercabile (CQ-4278916).

* vulnerabilità XSS in DAM (NPR-31654).

### Sites {#sites}

* Quando i lanci vengono promossi con Promuovi solo pagine modificate e gli avvii Promuovi con pagine modificate vengono eseguiti, solo le pagine modificate vengono visualizzate come promosse. Inoltre, quando l&#39;elenco da promuovere è corretto, le pagine non modificate vengono ancora visualizzate in fondo all&#39;elenco (NPR-31314).

* Quando una pagina AEM Sites viene spostata in un percorso diverso, le relative proprietà non vengono aggiornate di conseguenza per rispecchiare la nuova posizione (NPR-31265).

* Per una nuova Blueprint, Se il numero di record è superiore a 40, vengono visualizzati solo i primi 40 record. Blueprint visualizza righe vuote per gli altri record (NPR-31182).

* Quando il numero di LiveCopy è elevato, il rendering dell&#39;anteprima richiede molto tempo (NPR-30945).

* È stato aggiunto il supporto per impostare una versione di una pagina durante l’eliminazione. Se il controllo delle versioni è disattivato per la pagina eliminata, AEM Sites non riesce a ripristinare tali pagine (NPR-30891).

* Quando un utente aggiunge caratteri giapponesi o coreani nella proprietà description di un menu, nel menu vengono visualizzati caratteri distorti per il testo in lingua giapponese e coreana (NPR-31331).

* Quando un utente sposta lo stato attivo sui campi della barra a sinistra e utilizza una scelta rapida da tastiera per incollare il contenuto, viene incollato il contenuto degli Appunti dell’Editor pagina invece del contenuto copiato dai campi della barra a sinistra (NPR-31169).

* Quando un utente modifica un frammento di contenuto, viene ripristinata la variante già eliminata del frammento di contenuto (NPR-31178).

* Query Modelli frammenti di contenuto inefficiente. È molto lento se l&#39;istanza ha molte pagine e genera un errore (NPR-30666).

* Quando si salva il modello di frammento di contenuto, l&#39;ora nel campo data e ora è impostata su 00:00 (NPR-30540).

* Sul lato server viene generato un file JavaScript con dati utente (NPR-30822).

* L&#39;interfaccia utente di authoring di AEM consente il phishing mediante contenuti esterni (NPR-29745).

### Integrazioni {#integrations}

* Quando si configura Adobe Launch, viene anteposta una barra (/) all&#39;URL della libreria (NPR-30700).

* Le prestazioni di ContextHub si sono ridotte dopo la pubblicazione (NPR-30884).

### Sling {#sling-6470}

* Aggiornate la versione del bundle del provider di sicurezza della console Web a 1.2.4 per rimuovere la dipendenza dell&#39;API starter del launchpad dal provider di protezione della console Web (NPR-30885).

### Platform {#platform}

* Gli aggiornamenti nella configurazione della dimensione del buffer per il servizio HTTP basato su Jetty non vengono salvati (NPR-30925).

* QueryBuilder supporta ora l&#39;ordine fn:name() nelle query xpath (NPR-31322).

* Aggiornamento dell&#39;amministratore di eventi distribuito Sling alla versione 1.1.4 per migliorare la qualità dei registri in un ambiente cluster (NPR-29256).

### Interfaccia di base {#ui-foundation}

* Lo scorrimento fino alla fine della pagina dei risultati con un numero elevato di risultati di ricerca causa l&#39;arresto anomalo del browser (NPR-31332).

* Quando si passa dalla vista Scheda alla vista Elenco in una pagina dei risultati di ricerca, si verifica un ritardo prima dello scorrimento della pagina (NPR-31280).

### Quercia {#oak}

* I file MS Office con estensione .docx e .xlsx contenenti immagini JPEG non possono essere analizzati utilizzando il parser Tika (NPR-31693).

### Livefyre

* L&#39;integrazione di Livefyre con l&#39;aggiornamento di AEM 6.4 fornisce un&#39;eccezione Null Point, quando l&#39;integrazione viene effettuata utilizzando il plug-in DITA per risorse sintetiche. L&#39;integrazione, tuttavia, funziona quando i componenti vengono aggiunti manualmente (FYR-11066).

### Traduzione {#translation}

* Il percorso del frammento esperienza di destinazione non viene aggiornato quando si promuove una pagina di lancio (NPR-30830).

### Communities {#communities}

* La funzionalità e-mail non funziona correttamente in alcuni casi anche quando la messaggistica e-mail è abilitata nelle impostazioni di notifica, il sistema genera un&#39;eccezione in NotificationsActivityStreamProvider (NPR-31521).
* Non è possibile creare nuovi membri, nella schermata Crea membro dell’istanza di creazione di AEM viene visualizzata una schermata vuota (NPR-30951).
* L&#39;utente non può pubblicare un commento su un blog in Internet Explorer 11 (NPR-30927).
* L’amministratore di un gruppo con restrizioni non è in grado di visualizzare la scheda del gruppo, né di eseguire operazioni di collegamento rapido (gruppi Modifica/Pubblica/Elimina) nell’istanza di creazione di AEM (NPR-30810).
* Le informazioni relative ai gruppi di membri non sono visibili durante la creazione di un nuovo sito nell’istanza di creazione di AEM (NPR-28840).

### Forms {#forms}

>[!NOTE]
>
>Il Service Pack di AEM non include le correzioni per AEM Forms. Tali correzioni vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi per Forms. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per AEM Forms su JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

### Pacchetto di componenti aggiuntivi per Forms {#forms-add-on-package}

#### Moduli adattivi {#adaptive-forms}

* Le stringhe contengono la chiave del dizionario durante la localizzazione dei moduli adattivi (NPR-31109).

* Le caselle di controllo e gli elenchi a discesa in Forms non consentono l&#39;accesso facilitato (NPR-31282).

#### Moduli HTML5 {#html5-forms}

* Quando si genera l’anteprima HTML5 di un modulo XDP, viene visualizzato uno sfarfallio durante l’aggiunta di istanze di un sottomodulo (NPR-30907).

#### Document Services per OSGi {#document-services-osgi}

* L&#39;esecuzione di più thread simultanei per assemblare i moduli utilizzando il metodo com.adobe.fd.assembler.service.AssemblerService.invoke() visualizza un messaggio di errore (NPR-31164).

* I file temporanei creati da Assembler Service non vengono eliminati automaticamente e richiedono il riavvio di AEM (NPR-30846).

* Se si applicano i diritti di ReaderExtension al PDF viene visualizzato un messaggio di errore (NPR-30930).

#### Flusso di lavoro {#forms-workflow}

* Il flusso di lavoro OSGi non riesce a causa dell&#39;utilizzo della CPU al 100% (NPR-31234).

### Programma di installazione di JEE per Forms {#forms-jee-installer}

#### Servizi basati su documenti {#document-services}

* Il servizio Converti PDF non riesce a convertire i documenti PDF in PostScript e visualizza un messaggio di errore (NPR-31267).

* La configurazione dell&#39;endpoint SOAP viene ripristinata dopo l&#39;applicazione di una patch per correggere l&#39;errore HTML in PDF (NPR-31309).

#### Servizio PDFG {#pdfg-service}

* Impossibile caricare il file delle impostazioni Adobe PDF scaricato utilizzando l&#39;interfaccia utente di amministrazione (NPR-31273).

### Hotfix e Feature Pack inclusi nei Service Pack precedenti {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**

È inoltre cumulativo, il che significa che 6.4.6.0 include tutte le versioni dei Service Pack di AEM 6.4 precedenti.

Alcuni degli elementi di rilievo di AEM 6.4.6.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.15.
* È stato aggiunto il supporto per il tracciamento degli stati dell&#39;interfaccia utente dinamica nel tracciamento degli eventi nell&#39;API foundation.
* È stato aggiunto il supporto per la rappresentazione al componente core dell’immagine.

**Assets**

* Asset share link of a folder with space and `&` character in the name displays blank gray cards for some assets. NPR-29934: Hotfix per CQ-4270187
* DAM Workflow si blocca durante la creazione di risorse MP4 per AEM. NPR-30031: Hotfix per CQ-4271352
* Problema di connettività di Tag avanzati di Adobe tramite DataPower. NPR-30026: Hotfix per CQ-4269457
* Impossibile trovare il PDF utilizzando OmniSearch. NPR-30046: Hotfix per GRANITE-26290
* I percorsi delle risorse negli URL e i metadati delle cartelle generati dall’API ACP non sono codificati in URL.  GRANITE-26198: Hotfix per CQ-4271814
* La funzionalità dell&#39;attività di creazione revisione non funziona a causa di payload non definito. NPR-30469: Hotfix CQ-4274263
* La possibilità di passare dalla vista a schede alla vista a elenco e viceversa scompare dopo aver effettuato una ricerca Omni nel selettore delle risorse. NPR-29852: Hotfix per CQ-4269369
* (Interfaccia touch) Durante la procedura guidata di gestione della pubblicazione, le risorse vengono aggiunte alla coda di replica dopo l’aggiunta delle pagine, causando la visualizzazione di alcune delle risorse dopo alcuni secondi. NPR-29985: Hotfix per CQ-4270724
* Se si ordinano le query di ricerca in base alla rilevanza, oltre ai modelli InDesign vengono restituiti documenti InDesign. Hotfix per CQ-4273864
* Se l’utente dispone di un ID e-mail in maiuscolo, non potrà eseguire la consegna per le risorse ritirate in precedenza. Hotfix per CQ-4276575
* Configuring Dynamic Media Cloud Services in `DMHybrid` mode results in multiple empty report suites created in Analytics with no report suite id stored on AEM resulting in report suite duplication. Hotfix per CQ-4276855
* La finestra di dialogo di avviso non viene visualizzata durante la promozione nella pagina &quot;Tag gestito&quot;. Hotfix per CQ-4252851
* Quando si utilizza il carosello per la gestione dei tag, il pulsante di navigazione non funziona. Hotfix per CQ-4275499
* La funzionalità per lo spostamento in massa delle risorse non funziona e non è possibile spostare le risorse. Hotfix per CQ-4272987

**Sites**

* `pageinfo.json` le richieste sono estremamente lente e il caricamento richiede troppo tempo. NPR-29709: Hotfix per CQ-4269560
* `onTime` o `offTime` le proprietà dei metadati salvate sulle risorse non vengono richiamate se il server AEM viene riavviato. NPR-30413: Hotfix per CQ-4272784
* A causa di un comportamento errato della classe ConfigPostProcessor, la sospensione della pagina padre rimuove cq: Tipo di mixaggio LiveRelationship dalla pagina figlio. NPR-30536, NPR-30510: Hotfix per CQ-4254113
* Cross-site scripting (XSS) nella finestra di dialogo del flusso di lavoro all&#39;avvio della pagina di modifica della campagna. NPR-29747: Hotfix per CQ-4271067
* (Interfaccia classica) L’area di blocco del flusso di lavoro disattiva la scheda del flusso di lavoro fino al rilascio del blocco. NPR-30356: Hotfix per CQ-4237557
* (IE11) Quando si incolla contenuto HTML in un componente Editor di testo RTF con defaultPasteMode = testo normale, l’HTML viene incollato con la formattazione, pertanto defaultPasteMode non ha alcun effetto. NPR-30045: Hotfix per GRANITE-26094
* (Interfaccia classica) Quando la pagina di amministrazione del sito viene ricaricata, tutti gli elementi a discesa nel menu &quot;Nuovo&quot; vengono disattivati. NPR-29980: Hotfix per CQ-4272044
* Impossibile aggiungere stili al testo o modificare gli stili esistenti creati sul contenuto. NPR-29712: Hotfix per CQ-4266249
* (interfaccia classica) Risorse senza dc: il valore title è elencato senza titolo nel browser della finestra di dialogo del campo path. NPR-30166: Richiesta backport per CQ-88858
* Cq: il listener non funziona con i componenti nidificati anche dopo l&#39;aggiunta del componente parsys. NPR-30422: Hotfix per CQ-4274863
* Errore di ContextHub durante l’integrazione di AEM e Campaign. NPR-30625: Hotfix per CQ-4250790
* Il valore del parametro di richiesta resourceType viene copiato nel valore di un attributo di tag HTML che è racchiuso tra virgolette doppie. NPR-29832: Hotfix per CQ-4255365
* È necessario aggiornare la pagina dopo che i componenti sono stati copiati e incollati da una pagina all’altra. NPR-29982: Hotfix per CQ-4256019
* Publish/Unpublish from a page alias non è supportato e deve essere rimosso. NPR-30062: Hotfix per CQ-4271249
* Avviso di ResourceResolver non chiuso in ExperienceFragmentsReplicationListener con problemi di stabilità nel tempo e il riavvio delle istanze AEM. NPR-30416: Hotfix per CQ-4257521
* Se si spostano frammenti esperienza a cui viene fatto riferimento in più di 150 pagine, il percorso del frammento non viene modificato nelle pagine a cui viene fatto riferimento. NPR-30556: Hotfix per CQ-4274900
* Errore di analisi durante l&#39;apertura di un frammento di contenuto con caratteri dollaro ($) e parentesi aperta ({) uno dopo l&#39;altro. Hotfix per CQ-4270266
* VersionPreviewServlet non riesce in NullPointerException quando si prova a visualizzare una versione di un frammento esperienza nella timeline. NPR-30074: Hotfix per CQ-4271881
* Impossibile bloccare i frammenti di contenuto tramite la funzione di archiviazione. NPR-29923: Hotfix per CQ-4258785

**Replica**

* Sessione JCR / Risolutore risorse viene trapelato durante l&#39;implementazione OAuth su ogni replica in MAC / Portale marchio. NPR-30000: Hotfix per GRANITE-26196

**Sling**

* L&#39;ordine degli elementi secondari interessati dalla sovrapposizione e dall&#39;ordine precedente causa IndexOutOfBoundException. NPR-30408: Hotfix per Sling-8296 e Sling-7375
* InactiveBundlesHealthCheck sta leggendo la configurazione MissingPackagesHealthCheck una volta salvate le configurazioni InactiveBundlesHealthCheck. NPR-30084: Hotfix per CQ-4272644

**Commerce**

* Impossibile eseguire il blueprint del catalogo dalla console Siti. NPR-29829: Hotfix per CQ-4271461
* La risorsa utilizzata nel prodotto non mostra alcun riferimento al prodotto nella sezione &quot;Riferimenti&quot; della risorsa, né il percorso della risorsa viene aggiornato se la risorsa viene spostata. NPR-30542: Hotfix per CQ-4270247

**Platform**

* Il mittente predefinito di AEM non è in grado di inviare messaggi a un server SMTP remoto tramite TLS v1.2. NPR-30476: Hotfix per GRANITE-26605

**Community**

* I gruppi eliminati dall’autore non sono sincronizzati con tutti gli editori. NPR-29987: Hotfix per CQ-4268738
* Gli utenti eliminati rimossi dal campo Amministratori community non sono sincronizzati con il gruppo Appartenenza. NPR-30389: Hotfix per CQ-4274339
* Gli utenti appartenenti al gruppo amministratori non dispongono di collegamenti rapidi per il gruppo. NPR-30546: Hotfix per CQ-4275579
* Quando si aggiornano i gruppi Community creati di recente e quelli esistenti, la proprietà viene sovrascritta su jcr: nodo di contenuto e modifica il nome nel titolo della prima pagina. NPR-30109: Hotfix per CQ-4273719
* La ricerca rapida e la ricerca attraverso posizione e indirizzo non funzionano quando la comunità è impostata per funzionare con il provider di risorse di archiviazione di database (DSRP). NPR-26737: Hotfix per CQ-4258493

**Traduzione**

* L&#39;esecuzione automatica della traduzione non funziona. NPR-30499: Hotfix per CQ-4276288
* L’utente può creare una copia per lingua nel percorso contenuto limitato alla sola lettura. NPR-29937: Hotfix per CQ-4270708
* Problema di traduzione - Solo alcuni componenti vengono tradotti utilizzando la traduzione automatica. NPR-30079: Hotfix per CQ-4273764

**Integrazione**

* Il contenuto personalizzato non viene visualizzato correttamente nell’istanza di pubblicazione fino al riavvio dell’istanza. NPR-30421: Hotfix per CQ-4273706

**Progetti**

* I valori dam:folderThumbnailPaths non vengono aggiornati e vengono visualizzate miniature vecchie anche dopo l’eliminazione delle risorse nella cartella. NPR-30424: Hotfix per CQ-4273667

**Console interfaccia**

* Script intersito (XSS) sulle proprietà della pagina Siti nella scheda delle miniature. NPR-30048: Hotfix per GRANITE-26200

**UI-Foundation**

* È stato aggiunto il supporto per il tracciamento degli stati dell&#39;interfaccia utente dinamica nel tracciamento degli eventi nell&#39;API foundation. NPR-30742, GRANITE-26322: Hotfix per GRANITE-26036

**Forms**

>[!NOTE]
>
>Il Service Pack di AEM non include le correzioni per AEM Forms. Tali correzioni vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi per Forms. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per AEM Forms su JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

**Pacchetto di componenti aggiuntivi per Forms**

**Moduli adattivi**

* Il recupero del file .css vuoto richiede più tempo dall&#39;editore, causando problemi di prestazioni. NPR-30558: Hotfix per CQ-4274399
* I moduli modificati dopo la pubblicazione non vengono più postati alla pubblicazione del sito. NPR-30411: Hotfix per CQ-4236566

**Forms - Integrazione con il back-end**

* Viene generato un errore durante la creazione del modello dati del modulo con il linguaggio WSDL (Web Service Definition Language). NPR-30388: Hotfix per CQ-4272921

**Forms - Gestione della corrispondenza**

* I caratteri speciali quali minore di (&lt;), maggiore di (>) e e e commerciale (&amp;) vengono codificati nell&#39;interfaccia utente dell&#39;agente. NPR-30410: Hotfix per CQ-4273887
* Quando si attiva un frammento di testo contenente valori del dizionario dati, l&#39;interfaccia utente dell&#39;agente non risponde. NPR-30098, NPR-30083: Hotfix per CQ-4272204
* L&#39;interfaccia utente Crea corrispondenza (interfaccia utente CCR) non riesce in modo intermittente con la variabile di errore (oggetto Object). NPR-29983: Hotfix per CQ-4273874
* Il ricaricamento della bozza di lettera non riesce con un&#39;eccezione quando la descrizione dei frammenti di documento contiene caratteri speciali come minore di (&lt;), maggiore di (>) e e e commerciale (&amp;) nelle proprietà. NPR-29930: Hotfix per CQ-4252762

**Moduli HTML5**

* Quando si utilizza l’accesso desktop non visivo in modalità Sfoglia per leggere un modulo HTML5, il browser Chrome legge l’elemento “grafico” prima di qualsiasi file SVG nella struttura del modulo. NPR-30450: Hotfix per CQ-4274732

**Programma di installazione di JEE per Forms**

**Forms - JEE di base**

* L&#39;aggiunta o la modifica di una connessione a un servizio Web richiamando i servizi Web da Workbench moduli AEM genera un errore: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116: Hotfix per CQ-4273217

**Forms - Servizi basati su documenti**

* Errore dell&#39;etichetta PDF/A nella verifica preliminare di Acrobat. NPR-30594: Hotfix per CQ-4276032
* I binding dei dati con un singolo carattere nel PDF causano errori nelle estensioni di Reader con l&#39;errore &quot;java.lang.StringIndexOutOfBoundException: Indice stringa fuori intervallo: 1&quot; NPR-30128: Hotfix per CQ-4273878
* Quando si esegue un test di caricamento su un servizio di conversione da HTML a PDF, il test non riesce, viene restituito un errore e le impostazioni del tipo di file vengono rimosse dal server AEM Forms. NPR-30085: Hotfix per CQ-4272631
* La conversione di un PDF con Adobe Acrobat 9.1 (XFA versione 3.0) non mantiene lo stato del modulo PDF: Gli elementi invisibili del modulo vengono reimpostati sullo stato visibile. NPR-29978: Hotfix per CQ-4270888

**Forms - Sicurezza dei documenti**

* L’applicazione di una firma con marca temporale non riesce e viene restituito l’errore: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Errore di chiamata. NPR-30696, NPR-30537: Hotfix per CQ-4273778
* Configuration Manager non inserisce stringhe giapponesi per le colonne di tabella localizzate. NPR-30496: Hotfix per CQ-4274868

**Servizio PDFG**

* Errore di connessione durante il tentativo di convertire il documento Word in PDF in Windows Server 2016. NPR-30597: Hotfix per CQ-4275652
* Eccezione negata durante il tentativo di utilizzo del servizio backend HTML to PDF tramite la libreria &quot;phantomjs&quot;. NPR-30456: Hotfix per CQ-4258077
* maxReuseCount per il servizio da HTML a PDF non viene visualizzato con la console di gestione JBoss. NPR-30303, NPR-30135: Hotfix per CQ-4273763

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**

È inoltre cumulativo, il che significa che 6.4.5.0 include tutte le versioni dei Service Pack di AEM 6.4 precedenti.

Alcuni degli elementi di rilievo di AEM 6.4.5.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.13.
* Timeout socket e timeout di connessione aggiunti negli agenti di replica del Brand Portal.
* Miglioramenti della ricerca: il limite di impaginazione del risultato della ricerca è stato aumentato a 100 pagine.
* Il componente `AssetDownloadServlet` OSGi è stato disattivato per impostazione predefinita nelle istanze di pubblicazione AEM. Per ulteriori informazioni, consultate [Scaricare risorse da AEM](/help/assets/download-assets-from-aem.md).
* Abilitazione del supporto per l’utilità di gestione di più siti per Assets. For more information, see [Reuse assets using MSM for Assets](/help/assets/reuse-assets-using-msm.md).

**Assets**

* Le risorse con un apostrofo nel nome del file non vengono sincronizzate su elementi multimediali dinamici. NPR-29538: Hotfix per CQ-4270592
* Aggiornamento dell’interfaccia DMGGateway di DAM per il supporto multipart di S3. NPR-29740: Hotfix per CQ-4226303
* La finestra di dialogo per il download delle risorse mostra una dimensione file non corretta quando si scaricano le rappresentazioni per un video in Contenuti multimediali dinamici. NPR-29642: Hotfix per CQ-4246202
* Le risorse diventano inutilizzabili dopo che il servizio Day CQ DAM Mime Type Service applica il testo per m3u8. NPR-29276: Hotfix per CQ-4264052
* La regolazione del riferimento risorsa non salva la sessione se una delle risorse spostate o rinominate fa parte delle raccolte Sling Resource. NPR-29143: Hotfix per /CQ-4252605
* Impossibile tracciare o trovare le risorse eseguendo una ricerca nei valori dei metadati. NPR-29141: Hotfix per CQ-4260215
* Quando si utilizza il filtro di ricerca per salvare una raccolta avanzata, l&#39;azione di clic sul pannello non viene mantenuta attiva. NPR-29000: Hotfix per CQ-4240323
* Lo spostamento di una cartella consente la creazione di una cartella con nomi misti o maiuscoli. NPR-28945: Hotfix per CQ-4265234
* Risultati vuoti visualizzati in Omnisearch se il nome della raccolta ha spazio. NPR-29001: Hotfix per CQ-4236729
* Se si rinomina un file utilizzando alcuni caratteri speciali non supportati come e commerciale (&amp;), viene creata una cartella non valida. NPR-29196: Hotfix per CQ-4265037
* L&#39;archivio DAM Extract per la funzionalità dei file zip è danneggiato. NPR-29187: Hotfix per CQ-4254421
* L’importazione di metadati deve consentire l’importazione di metadati senza registrare gli spazi di nomi. NPR-29425, NPR-28132: Hotfix per CQ-4269445
* Il salvataggio delle modifiche ai metadati non funziona per le risorse il cui nome contiene un carattere di citazione. NPR-29395: Hotfix per CQ-4254305
* Impossibile spostare una risorsa DAM se il nome del file contiene spazi bianchi. NPR-29270: Hotfix per CQ-4266403
* Impossibile scaricare gli archivi ZIP compressi con l&#39;algoritmo Deflate64. NPR-29225: Hotfix per CQ-4253995
* Le miniature delle risorse vengono visualizzate lentamente quando si apre una cartella contenente risorse con più versioni. NPR-29833: Hotfix per CQ-4271629
* Impossibile inserire la raccolta evidenziata se viene premuto il tasto Invio dopo aver selezionato la raccolta. NPR-29723: Hotfix per CQ-4261607
* Gli attacchi di script tra siti (XSS) attraverso la finestra di avviso con restrizioni. NPR-29671: Hotfix per CQ-4270133
* L’aggiunta di relazioni alle risorse non riesce per gli utenti senza autorizzazioni di eliminazione. NPR-29640: Hotfix per CQ-4269196
* Dopo aver aggiunto il titolo della risorsa nella pagina delle proprietà, quando l’utente tenta di chiudere la pagina, AEM apre di nuovo la pagina delle proprietà. NPR-29628: Hotfix per CQ-4264929
* La creazione di un numero elevato di relazioni sulla risorsa genera un errore. NPR-28779: Hotfix per CQ-4250708
* L’assimilazione delle risorse è lenta nella modalità di esecuzione di Scene7 Connect. NPR-28658: Hotfix per CQ-4263007
* Errore TypeError non rilevato: Impossibile leggere la proprietà &#39;split&#39; di undefined viene visualizzata quando si tenta di visualizzare i risultati della ricerca. NPR-28803: Hotfix per CQ-4248371
* La replica da AEM a Brand Portal è bloccata per lunghi periodi. NPR-28914: Hotfix per CQ-4254932
* Lo spostamento delle risorse in DAM non determina un movimento simile in Scene7. NPR-28957: Hotfix per CQ-4264974
* Gli aggiornamenti di metadati non vengono passati a IPS se il campo di metadati viene aggiornato in AEM. NPR-28961: Hotfix per CQ-4255393
* VersioningTimelineEventProvider deve fornire la versione principale insieme al commento sulla versione. Hotfix per GRANITE-26063
* L&#39;invio di dati comporta l&#39;esecuzione di codice sul lato server. Hotfix per CQ-4270246
* Abilitazione del supporto per l’utilità di gestione di più siti per Assets. Hotfix per CQ-4271453, CQ-4268621, CQ-4257491
* L’interfaccia di AEM deve contenere una voce aggiuntiva per la versione corrente della risorsa nella cronologia della timeline, per visualizzare l’ultimo commento di consegna fornito da Adobe Asset Link. Hotfix per CQ-4262864
* Il video di esempio non viene caricato durante la creazione o la modifica di un set di file multimediali diversi. Hotfix per CQ-4244889
* La disabilitazione delle autorizzazioni per eliminare il contenuto dal lato di AEM impedisce all’utente di pubblicare contenuti nel Brand Portal. Hotfix per CQ-4270426
* Problemi relativi al limite di query con i rapporti sulle risorse dopo l’aggiornamento ad AEM 6.4.3. NPR-28588: Hotfix per CQ-4262022, CQ-4260697
* La funzionalità di download sfrutta Risorse AEM tramite il servlet di download delle risorse, consentendo agli utenti anonimi di scaricare tutte le risorse. NPR-27315, Hotfix per CQ-4254732

**Sites**

* Il nome del tag di reclamo JCR deve essere popolato automaticamente in base al titolo del tag. NPR-28990: Hotfix per CQ-4199411
* Il pulsante Annulla ereditarietà non è visibile in alcuni dei campi aggiunti nelle proprietà della pagina. NPR-29079: Hotfix per CQ-4265686
* L’azione di anteprima del rollout non deve tentare di ricreare la Live Copy o di visualizzarla nell’elenco delle pagine di rollout. NPR-29151: Hotfix per CQ-4266213
* (Editor modello) regressione dei criteri di stile in modalità struttura. NPR-28981: Hotfix per CQ-4264400
* Le copie live nidificate mostrano voci duplicate durante il rollout. NPR-29300: Hotfix per CQ-4268664
* La pubblicazione di una Live Copy di una Live Copy contenente un componente Importazione progettazione non riesce. Impossibile recuperare i riferimenti per la pagina selezionata. NPR-28944: Hotfix per CQ-4265014
* Se utilizzato con Multifield, CoralUI memorizza il parametro fileReferenceParameter a livello di componente anziché a livello di multicampo. NPR-29536: Hotfix per CQ-4266129
* Il riferimento alla progettazione non viene replicato in fase di pubblicazione dopo l&#39;annullamento dell&#39;ereditarietà in Importazione progettazione. NPR-29648, NPR-29721: Hotfix per CQ-4269270, CQ-4271087
* Il campo percorso nell’editor Rich Text si apre sul percorso principale indipendentemente dal percorso specificato per la ricerca. NPR-29483: Hotfix per CQ-4268997
* (IE11) Copiare e incollare il contenuto HTML in un componente RTE con defaultPasteMode = Plintext non viene incollato come testo normale. NPR-29432, NPR-29171: Hotfix per GRANITE-24941
* Il controllo ortografia Editor Rich Text non funziona più in altre lingue. NPR-29506: Hotfix per CQ-4264990
* Cross-site scripting (XSS) nella pagina Campaign. NPR-29614: Hotfix per CQ-4269322
* Se si riduce a icona la finestra a schermo intero di Editor Rich Text nella modalità di modifica dell’origine, si verifica una perdita di contenuto. NPR-29574: Hotfix per CQ-4260584
* (Interfaccia classica) La navigazione all&#39;ultima scheda non è sempre possibile se sono presenti numerosi tag. NPR-29544: Hotfix per CQ-4264548
* (Interfaccia classica) Il menu di navigazione di Admin Console scompare e la pagina non viene caricata completamente. NPR-29571: Hotfix per CQ-4264585
* Viene generato un avviso di errore durante l’aggiunta di componenti alla pagina WCM quando nell’istanza è abilitata la minificazione. NPR-29396: Hotfix per CQ-4266196
* Un problema relativo all&#39;ereditarietà dei nodi Style System dall&#39;elemento padre. NPR-29296: Hotfix per CQ-4266041
* La pagina ripristinata con Timewarp deve fare riferimento all’immagine corretta al momento del controllo delle versioni.  NPR-29431: Hotfix per CQ-4262638
* Pagina vuota con errori Javascript nell’editor dopo l’installazione della versione snapshot 6.4.5 più recente. NPR-29475: Hotfix per CQ-4266196
* Quando si aggiunge un componente a un parsys, la proprietà elenco componenti di progettazione non viene rispettata e viene risolta in un nome di nodo di modello diverso con una struttura parsys simile. NPR-29509: Hotfix per CQ-4269044
* cq:dropTargets copre l’intero componente invece delle dimensioni dell’immagine, rendendo difficoltoso il targeting con i componenti incorporati. NPR-29738: Hotfix per CQ-4268912
* Il componente immagine non chiama il listener &quot;after edit&quot; dopo l’utilizzo dell’editor locale delle immagini. Hotfix NPR-29616 per CQ-4268065
* È stato risolto un problema nella configurazione del post su Facebook. NPR-29212: Hotfix per CQ-4266630
* Quando promuovi i lanci per le pagine modificate, vengono considerate le modifiche nei rami sia sorgente che lancio. NPR-29308: Hotfix per CQ-4266746
* La miniatura di cui è stato eseguito il rendering nel frammento di contenuto mostra la rappresentazione interna del calendario per il campo Data e ora. NPR-29531: Hotfix per CQ-4269362
* Impossibile aggiungere in massa un tag alle pagine con tag diversi esistenti. NPR-28729: Hotfix per CQ-4262922
* L&#39;icona Attivazione pianificata non viene visualizzata nell&#39;amministratore del sito. NPR-28725: Hotfix per CQ-4263917

**Replica**

* Vulnerabilità nella divulgazione delle informazioni sensibili nel componente Replication Agent. NPR-29612, NPR-24951: Hotfix per GRANITE-25070
* I dati forniti dall’utente non sono preceduti dall’escape nell’output nel componente cq/replica/components/agent e causano la memorizzazione di una vulnerabilità cross-site scripting (XSS). Hotfix per CQ-4266263

**Frammenti esperienza**

* Impossibile esportare i frammenti esperienza nella destinazione quando si utilizza l’immagine intelligente. Hotfix per CQ-4269606

**Social - Reporting**

* I rapporti della community AEM non vengono visualizzati nell’istanza di creazione di AEM. Hotfix per CQ-4266294

**Platform**

* Script (XSS) tra siti in Gestione pacchetti durante l&#39;installazione di un pacchetto. NPR-29734, NPR-29713, NPR-29630: Hotfix per GRANITE-26161, GRANITE-
* Più script cross-site (XSS) memorizzati e riflessi in CRXDE Lite. NPR-29634: Hotfix per GRANITE-26049
* La funzionalità di accesso per Package Share utilizza la richiesta GET invece della richiesta POST, rendendo la password visibile nella scheda di rete. NPR-29631: Hotfix per GRANITE-26048

**Felix**

* Cross-site scripting (XSS) osservato nella console di sistema. La pagina viene caricata e la finestra a comparsa viene visualizzata quando si passa il mouse sul campo di testo. NPR-29853, NPR-29633: Hotfix per GRANITE-26188, GRANITE-26050

**GRANITE**

* La configurazione del logger di registrazione Apache Sling non applica alcun filtro allo script iniettato.  NPR-29775: Hotfix per GRANITE-26051

**Community**

* I gruppi eliminati in fase di creazione devono essere rimossi dalle istanze di pubblicazione. NPR-28933: Hotfix per CQ-4264645
* Il segreto dell&#39;app deve essere protetto con un campo password e non deve essere visualizzato in testo normale per gli strumenti di connessione social network. NPR-29728: Hotfix per CQ-4270480
* I visitatori e i membri, senza privilegi di moderatore, possono visualizzare i post non approvati/in sospeso incollando l’URL. NPR-29726: Hotfix per CQ-4271124, CQ-4271441
* Durante l’accesso dell’utente alla community è possibile notare un tempo di risposta elevato, fino a 40-50 secondi. NPR-29678: Hotfix per CQ-4269444

**Traduzione**

* Gli utenti che non dispongono della funzione di traduzione possono accedere alle relative sottopagine. NPR-29644: Hotfix per CQ-4269979
* Le autorizzazioni utente non supportate come procedura guidata consentono la creazione della copia di traduzione in un percorso di sola lettura. NPR-29375: Hotfix per CQ-4265877

**Interfaccia utente - Foundation**

* È stato aumentato il limite di impaginazione del risultato della ricerca a 100 pagine per la vista a schede e a 200 per la vista a elenco. NPR-29332: Hotfix per GRANITE-24644
* A causa di un caricamento non corretto dei tag, nella pagina della raccolta non viene visualizzato nulla. NPR-29267: Hotfix per GRANITE-24902
* Se si modifica il limite di impaginazione a 100 invece di 40, viene attivato un carico aggiuntivo senza la richiesta di impaginazione. NPR-29246: Hotfix per GRANITE-25027
* Il campo password granita di AEM non viene popolato dopo la crittografia. NPR-29245: Hotfix per GRANITE-24908

**Integrazione**

* Viene visualizzato un messaggio di eccezione quando si tenta di modificare e salvare la configurazione di avvio di AEM. NPR-29086: Hotfix per CQ-4266153
* Credenziali BrightEdge non valide ed errore di connessione.  NPR-29167: Hotfix per CQ-4265872
* È necessario rimuovere la casella di controllo ereditata dalla visualizzazione al livello principale nelle configurazioni del servizio cloud. NPR-27856: Hotfix per CQ-4259676

**Sling**

* Timeout connessione HTTP non letto dalle configurazioni. NPR-29264: Hotfix per SLING-7902
* Il writeback del programma di installazione JCR causa l&#39;uso di un formato non valido da parte della configurazione OSGi e il blocco della ridistribuzione. NPR-29027: Hotfix per CQ-4264694

**Progetti**

* Gli utenti non possono completare il flusso di lavoro del progetto. NPR-29621: Hotfix per CQ-4258791
* Nell&#39;elenco Flusso di lavoro progetto sono visualizzate righe vuote oltre i 40 flussi di lavoro. NPR-28739: Hotfix per CQ-4264005
* Se scegliete l’opzione Rendering dinamico in Brand Portal, viene scaricato un file .zip vuoto. NPR-29420: Hotfix per CQ-4268826
* La pubblicazione di risorse dalla cartella /content/dam/mac di AEM Author a Brand Portal non funziona. NPR-29820: Hotfix per CQ-4271118
* La punteggiatura nel nome causa problemi con il pulsante di pubblicazione. NPR-29573: Hotfix per CQ-4269317
* Impossibile creare la copia della lingua della risorsa tramite il pannello di riferimento. Hotfix per CQ-4269535

**Flusso di lavoro**

* L’aggiornamento da 6.4.2 a 6.4.4 interrompe il campo del selettore del calendario dei partecipanti alla finestra di dialogo. NPR-29727: Hotfix per CQ-4270423

**WCM - Interfaccia utente amministratore**

* L&#39;apertura della scheda delle autorizzazioni nell&#39;implementazione di Coral2 non mostra i pulsanti. Hotfix per CQ-4269419

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

* (Interfaccia touch) L&#39;opzione Avvia flusso di lavoro non apre la finestra di dialogo per la configurazione. NPR-29521: Hotfix per CQ-4269050

**Forms - Integrazione con il back-end**

* Abilitazione del supporto per ADFS (Active Directory Federation Services) v3.0 per l’integrazione On-Premise di Microsoft Dynamics. NPR-30003, NPR-29484: Hotfix per CQ-4270586
* Il servizio di precompilazione non riesce a causa di un tempo di elaborazione prolungato dal modulo di integrazione dei dati di AEM Forms. NPR-28997: Hotfix per CQ-4265988
* Richiesta SOAP Webservice non valida in AEM Forms. NPR-29013: Hotfix per CQ-4265443
* Durante il test del servizio SOAP non viene visualizzato alcun messaggio di errore, in caso di valore data non corretto. Hotfix per CQ-4265445

**Moduli - Comunicazione interattiva e moduli - Gestione della corrispondenza**

* L’interfaccia utente Crea corrispondenza (interfaccia utente CCR) non riesce a gestire un numero mobile.  NPR-29210: Hotfix per CQ-4254201
* La descrizione comando impostata su una variabile non è visibile nell’interfaccia utente Crea corrispondenza (interfaccia utente CCR). NPR-29739: Hotfix per CQ-4250533
* Impossibile copiare o incollare da Omnisearch all&#39;interno di lettere. NPR-29808: Hotfix per CQ-4270783

**Moduli HTML5**

* Quando si aggiunge uno spazio all&#39;interno del testo, il campo di testo non consente la compilazione alla fine. NPR-28844: Hotfix per CQ-4260239

**Programma di installazione di JEE per Forms**

**Forms - JEE di base**

* Il componente Servizio Web in AEM Forms Workbench non è in grado di richiamare un servizio Web, che richiede l’autenticazione SSL bidirezionale. NPR-29485: Hotfix per CQ-4246794
* Il gestore di configurazione AEM Forms JEE non funziona con più schede NIC. NPR-29236: Hotfix per CQ-4268598
* Errore di avvio AEM proveniente da GemFire: java.lang.IllegalStateException: È possibile creare una sola connessione AdminDistributedSystem alla volta. NPR-29524: Hotfix per CQ-4266295
* NoClassDefFoundError a causa di una mancata corrispondenza della versione Jar. NPR-28834: Hotfix per NPR-28834

**Forms - Servizi basati su documenti**

* Un file PDF/A non valido viene riportato come PDF/A valido utilizzando l&#39;operazione isPDFA. NPR-29076: Hotfix per CQ-4261541
* La conversione del PDF in PDF/A-1b con il campo Modulo non ha il codice di aspetto. NPR-29534: Hotfix per CQ-4269618
* La conversione PDF/A da PDF prodotto con Output Service non trasmette la convalida con Acrobat DC. NPR-29647: Hotfix per CQ-4270448
* Il bundle Apache POI non riesce con un&#39;eccezione. NPR-27861, NPR-28048: Hotfix per CQ-4245898, CQ-4244778

**Forms - Designer**

* È stato aggiunto il supporto PDF/UA ai moduli XFA (XML Forms Architecture) generati utilizzando Designer e Output Service. NPR-23022

**Forms - Flusso di lavoro**

* Gli invii dall&#39;area di lavoro non vanno a buon fine con il carattere Umlaut. NPR-29087: Hotfix per CQ-4263172

**Feature Pack inclusi**

**Assets**

* Abilitazione del supporto per l’utilità di gestione di più siti per Assets. For more information, see [Reuse assets using MSM for Assets](/help/assets/reuse-assets-using-msm.md). NPR-26450: Hotfix per CQ-4259922

**Pacchetti OSGI e pacchetti di contenuti inclusi**

Il testo seguente documenta l’elenco dei pacchetti OSGI e dei pacchetti di contenuti inclusi nel CFP.

Elenco dei bundle OSGi inclusi in AEM 6.4.5.0

[Ottieni file](assets/6.4.5.0_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.5.0

[Ottieni file](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**

È inoltre cumulativo, il che significa che 6.4.4.0 include tutte le versioni dei Service Pack di AEM 6.4 precedenti.

Alcuni degli elementi di rilievo di AEM 6.4.4.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.11.
* È stato aggiunto il supporto per la versione del servizio di caching per evitare richieste HTTP con versioni frequenti del servizio.
* È stato aggiunto il supporto per l&#39;eliminazione dei tag automatici.
* Implementato lo scorrimento infinito per la procedura guidata catalogo.
* Possibilità di restringere le autorizzazioni in base ai siti della community.
* Correzioni delle prestazioni (caching, esecuzione asincrona, elenco di esclusione) per Sling Granite Content Health Check.
* È stato aggiunto il pulsante assetpicker alla finestra di dialogo delle miniature di pagina.
* Aggiunta di una nuova proprietà per consentire il posizionamento della descrizione comando sui campi.
* Supporto migliorato di ColorPicker all&#39;interno del campo Multifield.
* È stato aggiunto un controllo per ignorare i valori vuoti per i multicampi di immissione di numeri nei clientlibs del frammento di contenuto.
* Abilitato il supporto per Microsoft Translator Text API v3.

**Assets**

* Migrazione dell’integrazione ACP e Stock ad AEM 6.4.4.0 NPR-27632
* La pubblicazione successiva di una cartella di risorse vuota con sottocartelle fa scomparire le sottocartelle. NPR-27558: Hotfix per CQ-4254701
* L&#39;aggiunta di una singola proprietà String non con nome\[\] causa il blocco di scrittura XMP incompleto. NPR-26805: Hotfix per CQ-4254142
* Dopo aver rasterizzato il pdf di input, l&#39;output prodotto presenta immagini mancanti. NPR-27929: Hotfix per CTG-4150481
* Spostamento guidato risorse mostra un numero errato di pagine di riferimento per le pagine pubblicate. NPR-27833: Hotfix per CQ-4258014
* AssetPicker esegue la ricerca solo del primo tag per filtrare il risultato durante il filtraggio con i tag. NPR-27778: Hotfix per CQ-4257705
* Il gestore AEM OOOTB PDF si blocca durante l&#39;elaborazione di PDF con caratteri stranieri. NPR-28778: Hotfix per CQ-4254234
* Quando un file CSV ha un valore separato da virgole in una singola colonna, l’editor CSV AEM non esce dalla virgola e la tratta come una colonna separata. NPR-28801: Hotfix per CQ-4261694
* Problema con l&#39;Editor schema metadati quando si utilizza il browser percorsi per selezionare i dati. NPR-28674: Hotfix per CQ-4263005
* Troppe risorse vengono elaborate in Smart Content Service e il processo periodico di assegnazione dei tag viene completato per un periodo di tempo molto lungo. NPR-28640: Hotfix per CQ-4262661, CQ-4262644, CQ-4263234
* Le azioni desktop non funzionano per i risultati di ricerca Omnyce dalla `aem/start.html` pagina. NPR-27242: Hotfix per CQ-4248176
* L’API Assets non consente il caricamento di file > 2 GB, causando errori di caricamento. NPR-27629: Hotfix per GRANITE-23590
* I metadati non vengono salvati nella risorsa scaricata nel primo tentativo nel caso in cui l&#39;elemento multimediale dinamico sia abilitato nell&#39;istanza. NPR-28233: Hotfix per CQ-4260759
* Il risolutore del servizio non è chiuso nella configurazione SiteCatalyst. NPR-28015: Hotfix per CQ-4259397
* Lo spostamento delle risorse in DAM non determina un movimento simile in Scene7 (configurazione p2p). NPR-28313: Hotfix per CQ-4261091

**Sites**

* (Interfaccia classica) Una frazione di copie live viene visualizzata nell&#39;elenco di rollout. NPR-28598, NPR-28574: Hotfix per CQ-4263410
* LiveRelationshipManagerImpl genera eccezioni quando cq:master è vuoto o non valido. NPR-28590: Hotfix per CQ-4263115
* Il flusso di lavoro &quot;Richiedi eliminazione&quot; non elimina le pagine correttamente. NPR-28668: Hotfix per CQ-4263195
* L’interfaccia utente Stato relazione non mostra i valori corretti per l’anno o la marca temporale per i campi relativi al cardine-datepicker. NPR-28666: Hotfix per CQ-4263661
* Vulnerabilità cross-site scripting (XSS) in SuggestionHandler per la versione 6.4. NPR-28693: Hotfix per CQ-4253821
* Lo spostamento della cartella dall&#39;amministratore del sito termina con un errore di memoria insufficiente e rende AEM non disponibile. NPR-28346: Hotfix per CQ-4261398
* Le configurazioni di Rollout MSM LiveCopy vanno perse dopo l&#39;aggiornamento. NPR-28311: Hotfix per CQ-4258705
* Impossibile scorrere oltre 40 configurazioni di blueprint. NPR-27640: Hotfix per CQ-4239166
* L&#39;utilizzo di SyntheticResource come riferimento genera un&#39;eccezione di puntatore Null e blocca lo spostamento delle pagine.  NPR-27576: Hotfix per CQ-4258262
* PushOnModify non funziona sull&#39;eliminazione dell&#39;istanza aggiornata da 6.1 a 6.4. NPR-28108: Hotfix per CQ-4259833
* (Interfaccia classica) Pulsante Annulla ereditarietà mancante e componente modificabile in una pagina Live Copy. NPR-28256: Hotfix per CQ-4260161
* OakState0001: Conflitti irrisolti in Rollout. NPR-27982: Hotfix per CQ-4259548
* Quando si copia/incolla una struttura contenente riferimenti SyntheticResource, il processo termina con un errore 500. NPR-27709: Hotfix per CQ-4259179
* Impossibile terminare i flussi di lavoro in esecuzione quando i payload sono attivati. NPR-27672: Hotfix per CQ-4258520
* Il rollout mostra percorsi di rollout duplicati dopo l’aggiornamento da 6.1 a 6.4. NPR-27845: Hotfix per CQ-4259487
* Integrare il modale di risorsa della diga nel componente delle miniature di pagina. NPR-28131: Hotfix per CQ-108042
* (Interfaccia classica) Impossibile aprire le finestre di dialogo con il widget Tag. NPR-28575: Hotfix per CQ-4262680
* Il caricamento di file multicampo non mostra la zona di rilascio. NPR-28676: Hotfix per CQ-4263516
* Errore &#39;Valore selettore ricorsione non valido&#39; durante la migrazione di un componente da AEM 6.0 a AEM 6.2. NPR-28609: Hotfix per CQ-4241258
* L’Editor Rich Text nella finestra di dialogo è sfarfallio quando il puntatore di un plug-in è superiore all’area di testo, bloccando così l’ulteriore authoring. NPR-27579: Hotfix per CQ-4257440
* (Interfaccia classica) l&#39;annotazione di modifica cq:action non funziona. NPR-28232: Hotfix per CQ-4257703
* La rimozione dei tag dal pannello di ricerca delle risorse del filtro tag nell’editor pagina non aggiorna l’elenco correttamente. NPR-27983: Hotfix per CQ-4245567
* Se i valori dei numeri multicampo sono vuoti, facendo clic su Salva si genererà un messaggio di caricamento infinito senza essere effettivamente completati.  NPR-28400, NPR-28393: Hotfix per CQ-4244058, CQ-4244349
* Con un&#39;autorizzazione di sola lettura, gli utenti/gruppi non sono in grado di selezionare un XF e non hanno alcuna opzione per visualizzare il XF e le sue proprietà di pagina. NPR-28341: Hotfix per CQ-4260412
* I dati JSON ricevuti da Target hanno una serie di caratteri escape che causano l&#39;interruzione della pagina dell&#39;applicazione. NPR-28318: Hotfix per CQ-4252043
* Non è possibile modificare alcun componente dopo l’installazione di AEM 6.4.3. NPR-28125: Hotfix per CQ-4261216
* L&#39;eliminazione di tutti i tag per un campo tag non è persistente per un frammento di contenuto strutturato. NPR-28133: Hotfix per CQ-4247241
* Quando modificate una proprietà frammento di contenuto &quot;jcr:lastmodiedby&quot; e &quot;jcr:lastmodified&quot;, i valori vengono aggiornati senza che l’utente apporti modifiche. NPR-27847: Hotfix per CQ-4257138
* La versione dei frammenti di contenuto confronta diversi miglioramenti per AEM 6.4. NPR-27764
* Se nel modello di frammento esperienza non è definito alcun cq:allowTemplates su /content/experience-fragments e allowPaths, viene generato un errore quando il frammento esperienza viene spostato/copiato. NPR-27487: Hotfix per CQ-4257489
* Il pulsante Crea viene visualizzato all’aggiornamento per il nuovo utente. NPR-27335: Hotfix per CQ-4255360
* Durante il tentativo di spostare una pagina pubblicata, il conteggio &quot;Riferimenti alle pagine&quot; visualizzato nella prima pagina della procedura guidata &quot;Sposta pagina&quot; non è corretto. NPR-28111: Hotfix per CQ-4259663
* (Interfaccia touch) La barra laterale Riferimenti non mostra i collegamenti in entrata. NPR-28529: Hotfix per CQ-4262306
* Impossibile modificare le proprietà dei componenti e della pagina dopo l’installazione di AEM 6.4.3. NPR-27998: Hotfix per CQ-4261216, CQ-4260441
* Migra contexthub a jquery 3. NPR-28397: Hotfix per GRANITE-19902

**Commerce**

* Impossibile selezionare il catalogo se la cartella contiene più di 20 cataloghi. NPR-27649: Hotfix per CQ-4258119
* Le visualizzazioni delle procedure guidate e delle proprietà del commercio non funzionavano a causa della mancanza di header.referer. Hotfix per CQ-4261122

**Campaign - Targeting**

* com.day.cq.personalization.impl.TeaserResourceEventHandler entra in un ciclo infinito e causa aggiornamenti ai nodi sulle istanze di pubblicazione. Hotfix per CQ-4263096

**Replica**

* Errore durante la creazione del contenuto di replica com.day.cq.replication.AccessDeniedException. NPR-28314: Hotfix per CQ-4261401
* Perdita di sessione quando l&#39;ID agente utente è impostato su admin nell&#39;agente di replica. NPR-28220: Hotfix per CQ-4255517

**DAM - Creative Cloud**

* Esegui il backup dell’API HTTP per trovare immagini simili da Risorse AEM. Hotfix per CQ-4254091
* Ottimizzate l&#39;API ACP per consentire ai risultati di una query di essere limitati ai membri di una raccolta. Hotfix per CQ-4258708

**DAM - Formati**

* Dopo l’attivazione dell’esportazione dei metadati, la pagina viene reindirizzata a una pagina 404. Hotfix per CQ-4262447

**DAM - Generale**

* (Integrazione di Adobe Stock) Il modale di errore del server viene visualizzato con un errore Oauth nel file error.log. Hotfix per CQ-4260406
* L’integrazione di Adobe Stock non funziona se la versione 6.4.4 è applicata alla versione 6.4.3. Hotfix per CQ-4266009
* Collegamento al modello CF mancante anche dopo l&#39;applicazione della patch SP3. Hotfix per CQ-4259029

**Platform**

* (Interfaccia classica) Il pulsante Modifica non è disponibile nel componente Rapporto di base dopo l’aggiornamento alla versione 6.4.2. NPR-28560: Hotfix per CQ-4262825
* Quando si utilizza una query che combina property.operation=like e property.profondità, si conclude in una InvalidQueryException. NPR-28570: Hotfix per CQ-4262652
* Errore interno del server quando il nodo della lingua appena aggiunto viene rimosso dal nodo della lingua sovrapposta. NPR-28661: Hotfix per CQ-4239194
* Eccezione puntatore Null in stderr.log nel thread sling-oak-1 all&#39;avvio casuale. NPR-28665: Hotfix per CQ-4237845

**Felix**

* webconsole.plugins.memyusage causa un blocco critico all&#39;aggiornamento. NPR-27895: Hotfix per GRANITE-20715

**GRANITE**

* Sling Content Access Health Check esegue una lunga e eccessiva convalida /libs per il percorso di ricerca del risolutore di risorse personalizzato. NPR-28113: Hotfix per GRANITE-23529

**Gestione dei frammenti di contenuto**

* Miglioramenti a livello di usabilità e parità di funzionalità con le risorse per i frammenti di contenuto. Hotfix per CQ-4253883

**Community**

* Aggiorna il file di avvio vulnerabile a 3.4 e le librerie di editor binario a 4.5.11. NPR-28490: Hotfix per CQ-4257511
* L&#39;annullamento delle modalità di modifica non ripristina l&#39;allegato eliminato. NPR-27902: Hotfix per CQ-4255150
* La composizione per conto della casella deve essere visibile solo ai membri privilegiati. NPR-27900: Hotfix per CQ-4251235
* Aggiungi rep:cache nei nodi ignorabili nel listener di sincronizzazione utenti di AEM Communities sulle istanze di pubblicazione. NPR-27842: Hotfix per CQ-4247234
* La casella di ricerca mostra il carattere escape a livello di interfaccia utente. NPR-27838: Hotfix per CQ-4259757
* Errore durante la ricerca di caratteri speciali come ( , +,? nella ricerca rapida. NPR-28213: Hotfix per CQ-4260969
* Create un gruppo di &#39;amministratori specifici per la comunità&#39; affinché gli utenti possano modificare e creare il sito della comunità rilevante. NPR-27731
* È stata aggiunta la logica per l&#39;evento della tastiera per aprire il video. NPR-27726: Hotfix per CQ-4254026
* Attivazione della navigazione tramite tastiera per i componenti di Attivazione per AEM Communities durante la pubblicazione. NPR-27728: Hotfix per CQ-4254028
* È stata aggiunta l&#39;etichetta aria per il pulsante di visualizzazione elenco e a schede. NPR-27727: Hotfix per CQ-4254027
* Gestione delle sessioni di risoluzione delle risorse aperte in Social - Communities. NPR-27721: Hotfix per CQ-4258714

**Traduzione**

* Fornisce il supporto per Microsoft Translator Text API v3. NPR-28366: Hotfix per CQ-4249755
* jcr:language e cq:language non vengono aggiornati automaticamente nella lingua tradotta. NPR-28338: Hotfix per CQ-4256046
* I riferimenti ciclici causano StackOverflowError durante la creazione della copia della lingua. NPR-27596: Hotfix per CQ-4255621
* In un progetto di traduzione in più lingue, se si fa clic su Salva e chiudi i risultati nelle pagine successive aggiunte al progetto, vengono creati nuovi progetti invece di creare nuovi processi di traduzione nel progetto esistente. NPR-28219, NPR-28236: Hotfix per CQ-4261276, CQ-4260731
* Stringa di errore troppo lunga quando si aggiunge un frammento di contenuto con dati in massa a causa di un limite al numero di caratteri consentiti. NPR-28722: Hotfix per CQ-4262362

**Social network**

* I commenti pubblicati sulla pagina successiva vengono evidenziati con un colore giallo ogni volta che viene pubblicato un nuovo commento. Hotfix per CQ-4261359
* Impossibile utilizzare l’API per eliminare i commenti in UGC (User-Generated Content). NPR-28075: Hotfix per CQ-4261135
* AbstractNotificationOperationService causa ClassCastException. Hotfix per CQ-4260456
* Rimozione del riferimento al cloud SCORM (Shared Content Object Reference Model) nel lettore. Hotfix per CQ-4260779

**Interfaccia utente - Foundation**

* La funzione &quot;FileSystem Output Cache&quot; integrata in HTML Client Library Manager interrompe la funzione &quot;debugClientLibs&quot; per gli script compilati come i file LESS. NPR-27249: Hotfix per GRANITE-23313
* Il numero di risorse visualizzate quando la modalità di debug è attivata è sempre 1 e molti errori JS vengono visualizzati nella console del browser.  NPR-27575: Hotfix per GRANITE-23750
* Il salvataggio e la chiusura delle proprietà della pagina non torna alla pagina corretta in AEM WAR con Tomcat. NPR-27566: Hotfix per GRANITE-23671

**Integrazione**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` genera un ciclo infinito e causa aggiornamenti ai nodi nelle istanze di pubblicazione. NPR-28561: Hotfix per CQ-4263096
* Per un componente con targeting non vengono prese in considerazione le azioni cq:action. NPR-27616: Hotfix per CQ-4257497
* La cancellazione dell&#39;ereditarietà LiveCopy non funziona correttamente sui contenitori di destinazione. NPR-28129: Hotfix per CQ-4259813
* (Configurazione servizio cloud) La casella di controllo &quot;ereditato da&quot; visualizzata al livello principale deve essere rimossa. NPR-27856: Hotfix per CQ-4259676

**Sling**

* Aggiornamento a Sling Models API 1.3.8, Impl 1.4.10. NPR-27636: Hotfix per GRANITE-23537

**OAK - Persistenza del segmento**

* SegmentBufferWriter non scaricato dopo OnRC. NPR-27464

**Progetti**

* Il progetto di traduzione multilingue non crea più processi in lingua per gli utenti che non fanno parte del gruppo di amministratori. NPR-28508: Hotfix per CQ-4262023
* ProjectTaskListServlet perde un ResourceResolver ogni volta che viene chiamato getTaskRenderers durante l&#39;avvio del servizio. NPR-27590: Hotfix per CQ-4258011
* Se una directory contiene più sottodirectory rispetto alle dimensioni della pagina e l&#39;ordine è in base alla data o alle dimensioni, l&#39;errore impedisce di spostarsi oltre la prima pagina. NPR-28867: Hotfix per CQ-4265039
* Correzioni di script tra siti backport (XSS) nei visualizzatori DAM. NPR-28106: Hotfix per CQ-4253215
* Impossibile aggiungere pagine al progetto di traduzione da parte degli amministratori del progetto poiché il collegamento per aggiungere nuove pagine al progetto di traduzione non è visibile. Hotfix per CQ-4266334

**Flusso di lavoro**

* Quando si apre la finestra di dialogo dell’elemento di lavoro completo nella notifica del flusso di lavoro che dispone di un campo Tag, facendo clic sul segno di croce si aggiunge una proprietà Tag. NPR-28304: Hotfix per CQ-4261321
* Il pulsante di attivazione/disattivazione selezione utente nella finestra di dialogo Riassegna attività non funziona. NPR-28963: Hotfix per CQ-4264206

**Forms**

Elementi di rilievo di AEM 6.4.4.0 Forms:

* È stato aggiunto il supporto per registrare le API di protezione dei documenti per la firma e la certificazione come transazioni.

**Pacchetto di componenti aggiuntivi per Forms**

**Integrazione di Adobe Sign**

* AEM 6.4 Forms Client SDK non contiene il pacchetto adobesign-recipent. NPR-27735: Hotfix per CQ-4259372

**Moduli adattivi**

* Quando si crea un modulo adattivo Wan con un modello vuoto, i clienti non possono aggiungere pannelli secondari al pannello principale del modulo. NPR-28758: Hotfix per CQ-4264157
* Se il valore del campo dell&#39;anno del componente data è 9999, lo script di convalida non riesce. NPR-28580: Hotfix per CQ-4262620
* Quando un modulo adattivo viene creato con un modello vuoto, i clienti non possono aggiungere pannelli secondari al pannello principale del modulo. NPR-28758: Hotfix per CQ-4264157
* Impossibile impostare il valore tra i campi dei frammenti caricati pigri di un modulo adattivo. NPR-27758: Hotfix per CQ-4259703
* Il modulo adattivo non utilizza l’editor Rich Text, ma ne carica le librerie.  NPR-27759: Hotfix per CQ-4259193
* Il reindirizzamento all&#39;URL non funziona per i moduli adattivi incorporati in una pagina AEM Sites. NPR-27620: Hotfix per CQ-4239287
* Impossibile impostare il valore tra i campi dei frammenti caricati pigri di un modulo adattivo. NPR-28320: Hotfix per CQ-4262345
* Il modulo adattivo non utilizza l’editor Rich Text, ma ne carica le librerie.  NPR-28001: Hotfix per CQ-4259703, CQ-4259193
* La firma scarabocchio non funziona per l&#39;app AEM Forms in esecuzione su Apple iOS 12.1. NPR-28497: Hotfix per CQ-4261765
* Invia un’azione utilizzando i problemi di creazione classici di ‘Flusso di lavoro moduli’ in 6.4. Hotfix per CQ-4252740
* Errore nella gestione della rimozione di blocchi e spazio di archiviazione tmp. NPR-28806: Hotfix per CQ-4264441

**Forms - Gestione della corrispondenza**

* L’interfaccia utente dell’agente non mantiene le dimensioni originali dell’immagine. NPR-28800: Hotfix per CQ-4259767
* Interfaccia utente CCR/agente: Etichette dei campi Data spostate nella scheda Dati. Hotfix per CQ-4255499

**Moduli - Report transazione**

* È stato aggiunto il supporto per il conteggio tramite firme digitali o la certificazione di un documento come transazioni fatturabili. NPR-28495: Hotfix per CQ-4260236
* Aggiunta firma digitale e certificazione all&#39;API fatturabile. Hotfix per CQ-4260236

**Gestione moduli**

È stato aggiunto il supporto per sostituire l&#39;utilizzo della libreria client handlebars con un carattere di sottolineatura nella procedura guidata di analisi iniziale di Forms Manager e per spostare le risorse. NPR-27643: Hotfix per CQ-4246536.
Un bundle rimane nello stato installato dopo l&#39;installazione del pacchetto Forms Management nel ramo release/640. Hotfix per CQ-4265410I moduli inviati con allegati non vengono visualizzati nel flusso di lavoro con l&#39;azione di invio &quot;Richiama flusso di lavoro moduli AEM&quot; e l&#39;opzione di attivazione dell&#39;invio del portale è selezionata. Hotfix per CQ-4263110

**Forms - Integrazione con il back-end**

* Impossibile eseguire il test del preprocessore pre/post e l&#39;invio personalizzato tramite Client SDK, Hotfix per CQ-4238469

**Programma di installazione di JEE per Forms**

**Forms - Sicurezza dei documenti**

* Quando si utilizza il servizio updatepolicy, l&#39;errore dell&#39;oggetto non può essere risolto. NPR-28751: Hotfix per CQ-4252287
* Compilazione firma non riuscita con versione precedente di commons-pkg. Hotfix per CQ-4265535

**Forms - JEE di base**

* Quando AEM Forms è attivato su IBM WebSphere, la creazione di un modello dati modulo basato su SOAP non riesce. NPR-27923: Hotfix per CQ-4251134
* Lo strumento SRT di PDF Generator non è in grado di rilevare la versione installata di Adobe Acrobat. NPR-27971

**Forms - Designer**

* Alcune immagini JPEG in un modello XDP non vengono sottoposte a rendering correttamente.  NPR-26702: Hotfix per LC-3917457

**Moduli - OBSOLETE**

* Il servizio di acquisizione della carta si blocca durante l&#39;elaborazione dei file TIFF. NPR-28079: Hotfix per CQ-4240649

**Forms - Flusso di lavoro**

* I moduli HTML5 con processo di invio predefinito in an.lca non funzionano su JBoss 7. NPR-28675: Hotfix per CQ-4243928
* Impossibile inviare moduli PDF in HTML Workspace. NPR-28058: Hotfix per CQ-4260373
* I dati del cliente vengono stampati nei registri delle informazioni utilizzando il flusso di lavoro Richiama moduli di servizio FDM. Hotfix per CQ-4260385

**Feature Pack inclusi**

**Sites**

* Il controllo delle versioni per i frammenti di contenuto confronta i miglioramenti in termini di differenze per AEM 6.4.  NPR-26760: FP per CQ-4248839
* Miglioramenti alle differenze di variazione dei frammenti di contenuto per AEM 6.4.  NPR-27866: FP per CQ-4248839
* Funzione attivata nella configurazione OSGI **AEM Workflow Revdraw Feature Flag**(Flag di rimozione flusso di lavoro AEM). L’azione di ritiro deve terminare l’istanza del flusso di lavoro dopo l’impostazione del flag. NPR-26451: Hotfix per CQ-4259090

**Platform**

* Estrazione facet di Query Builder avanzata sfrutta l&#39;API Oak per 6.4. NPR-26674: FP per CQ-4230337

**Pacchetti OSGI e pacchetti di contenuti inclusi**

Il testo seguente documenta l’elenco dei pacchetti OSGI e dei pacchetti di contenuti inclusi nel CFP.

Elenco dei bundle OSGi inclusi in AEM 6.4.4.0

[Ottieni file](assets/bundles_6_4_4_0.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.4.0

[Ottieni file](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

AEM 6.4.3.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio di AEM 6.4 ad aprile 2018.

È inoltre cumulativo, il che significa che 6.4.3.0 include tutte le versioni dei Service Pack di AEM 6.4 precedenti.

Alcuni degli elementi di rilievo di AEM 6.4.3.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.9.
* È stato aggiunto il supporto per la proprietà allowPaths nei modelli di moduli adattivi.
* Ricerca avanzata basata su pannello di risorse in AEM
* Correzioni di scripting tra siti (XSS) nella pagina di accesso.
* Miglioramento della strumentazione dell&#39;interfaccia utente.
* Miglioramenti nella gestione dei dati modulo.
* È stata migliorata la gestione della denominazione degli elementi all&#39;interno di un campo multiplo.
* È stata migliorata la gestione degli elementi segnaposto (vista a schede e vista a elenco) durante la selezione.
* Aggiunta autenticazione Adobe IMS e supporto Admin Console per i servizi gestiti.

**Assets**

* Il flusso di lavoro Aggiorna risorsa DAM non estrae i riferimenti dai file INDD se l&#39;opzione Disconnetti IDS è abilitata. NPR-26243; Hotfix per CQ-4250933
* Il messaggio di riuscita non viene visualizzato quando le risorse vengono pubblicate con Assets Bulk Editor. NPR-26252; Hotfix per CQ-4251688.
* Dopo aver letto una risorsa da un risultato di ricerca, se fate clic sul pulsante Indietro nel browser, viene visualizzato un messaggio di errore &quot;Richiesta non valida&quot; con codice di errore 400. NPR 26578; Hotfix per CQ-4253741
* I metadati della risorsa mostrano un errore dello spazio nomi non valido dopo l&#39;installazione di un service pack. NPR-22341; Quickfix per CQ-4237202
* L&#39;opzione per riordinare cartelle e frammenti di contenuto nella visualizzazione a elenco non viene visualizzata per le cartelle applicabili. NPR-27153; Hotfix per CQ-4255873
* Gli utenti non sono in grado di aggiungere risorse a una nuova raccolta, in quanto genera un messaggio di errore con un&#39;immagine interrotta nella finestra di dialogo a comparsa degli errori. NPR-22431; Hotfix per CQ-4237086
* Il menu a discesa a cascata non è supportato negli elenchi a discesa dinamici. NPR-27043; Hotfix per CQ-4252564
* Se gli utenti impostano un valore non predefinito per la &#39;Cartella principale società&#39; nella configurazione cloud DMS7, il predefinito per visualizzatori non funziona come previsto. NPR-26360; Hotfix per CQ-4249505
* La segnalazione delle risorse non riesce per le istanze con un numero molto elevato di risorse. NPR-27278; Hotfix per CQ-4256748
* Le sottocartelle non ereditano il profilo immagine SmartCrop della cartella principale. NPR-27197; Hotfix per CQ-4256273
* Quando l’integrazione con Dynamic Media è abilitata, alcune proprietà di metadati di Risorse vengono modificate. Gli attributi width, height e location non vengono visualizzati. NPR-27203; Hotfix per CQ-4256258
* Per alcuni tipi di risorse, il file multimediale dinamico non utilizza il proxy configurato. NPR-25211; Hotfix per CQ-4244871
* La pagina Editor metadati contiene un&#39;eccezione di puntatore Null per il parametro dell&#39;elemento non valido. NPR-26169; Hotfix per CQ-4241368.
* Se a un elenco a discesa è applicata una regola di scelta e una regola richiesta, la regola richiesta non può essere soddisfatta nell&#39;editor di metadati. NPR-27479; Hotfix di CQ-4251428

**Sites**

* Un utente può controllare le funzioni dell’editor Rich Text in modalità a schermo intero in linea utilizzando i criteri dei contenuti, ma non può controllare le funzioni dell’editor Rich Text finestra di dialogo di modifica con i criteri dei contenuti. NPR-26750: Hotfix per CQ-4241130
* L’editor Rich Text diventa inutilizzabile quando si passa dalla finestra di dialogo a schermo intero a quella mobile. La visualizzazione mobile contiene due editor di testo RTF. NPR-25589: Hotfix per CQ-4206008
* Quando si preme il tasto Invio in un campo di testo, l&#39;editor Rich Text passa alla modalità a schermo intero. NPR-26204: Hotfix per CQ-4245893
* Il plug-in dell&#39;elenco dell&#39;editor Rich Text è disattivato automaticamente e non consente modifiche. NPR-26507: Hotfix per CQ-4239387
* Quando un carattere speciale viene aggiunto alla finestra dell’editor Rich Text, la finestra scorre verso l’alto. NPR-26435: Hotfix per CQ-4249869
* Domande sui casi in cui adottare o meno la memorizzazione in cache per segment.js in ClientContext. NPR-26622: Hotfix per CQ-4253486
* Quando una regola figlio viene attivata dall’istanza di creazione all’istanza di pubblicazione, l’istanza di pubblicazione smette di funzionare. NPR-26601: Hotfix per CQ-4253588
* Quando si combina l’Editor Rich Text con più campi, si verifica un errore di tipo “TypeError non rilevato: fieldAPI.getName non è una funzione in foundation.js”. NPR-27146: Hotfix per CQ-4253155
* L&#39;integrazione Salesforce non è in grado di utilizzare la configurazione proxy. NPR-27244: Hotfix per CQ-4245300
* Quando pianificate l&#39;attivazione di una pagina utilizzando l&#39;opzione Gestisci pubblicazione per una data successiva e passate alla vista a elenco, l&#39;icona del calendario risulta mancante. NPR-26974: Hotfix per CQ-4239206
* Gli utenti non possono modificare le autorizzazioni per i gruppi di utenti chiusi nelle proprietà della pagina. NPR-27138: Hotfix per CQ-4256089Impossibile modificare i tag tramite tag. NPR-26957: Hotfix per CQ-4254858
* Quando si sposta un tag a cui fa riferimento un modello di frammento di contenuto strutturato, i riferimenti esistenti al tag all&#39;interno di un frammento di contenuto non vengono aggiornati. Ciò si verifica nella schermata di modifica del modello di frammento di contenuto. NPR-26776: Hotfix per CQ-4251805
* Quando create e promuovete un lancio con più pagine, vengono create più versioni per ciascuna pagina. NPR-26917: Hotfix per CQ-4254663
* L&#39;amministratore del sito AEM non gestisce i percorsi digitati nella barra degli indirizzi del browser. NPR-26780: Hotfix per CQ-4254097
* Quando una pagina viene spostata in una nuova posizione senza rinominarla, la cronologia delle versioni della pagina viene persa. NPR-26706: Hotfix per CQ-4254025
* Gli URL nell&#39;editor amministrativo dei frammenti esperienza non consentono le sovrapposizioni. NPR-26319: Hotfix per CQ-4252156
* Quando una pagina viene creata con un modello contenente un frammento esperienza vuoto e viene pubblicata, la pagina non si apre e si verifica un errore DefaultSlingScript. NPR-26305: Hotfix per CQ-4252460
* Se si utilizza l&#39;uso semplice dei dati con classi con lo stesso nome, viene prodotto codice non conforme. NPR-27282: Hotfix per Sling-7581
* Dopo l&#39;installazione dell&#39;SP di aggiornamento, i siti dispongono di una configurazione di rollout blueprint vuota. NPR-27609: Hotfix per CQ-4257078

**DAM - Portale marchio**

* I predicati dei tag non vengono pubblicati quando il modulo dello schema di metadati viene pubblicato su Brand Portal. Hotfix per CQ-4256218
* Quando una cartella di terzo livello viene pubblicata da AEM a Brand Portal, senza pubblicare le cartelle principali, il nome della cartella cambia. Hotfix per CQ-4255423
* Il predicato del browser Percorsi viene pubblicato da Risorse AEM al Portale marchio come previsto. Tuttavia, il percorso pubblicato in BP rimane /content/dam, che deve essere aggiornato. Hotfix per CQ-4256240

**DAM - Creative Cloud**

* Icona &quot;Cerca risorse Adobe&quot; mancante nella navigazione principale di AEM. Hotfix per CQ-4254343

**DAM - Client DM**

* Dopo aver inserito i video in una cartella associata al profilo di elaborazione video AVS, la finestra del browser si aggiorna ripetutamente. Hotfix per CQ-4253563
* Pubblicazione su YouTube non riuscita quando si utilizza un tag Ad Hoc che include caratteri maiuscoli. Hotfix per CQ-4252477
* Quando un’annotazione viene creata in una risorsa come PDF, l’interfaccia utente avvia un ciclo infinito di aggiornamento delle pagine. NPR-27052: Hotfix per CQ-4255396

**DAM - Servizi DM**

* Per alcuni tipi di risorse, il file multimediale dinamico non utilizza il proxy configurato. NPR-10727; Hotfix per CQ-4244871

**Platform**

* Problemi di prestazioni con org.apache.sling.i18n. NPR-26812: Hotfix per SLING-7543
* Impossibile visualizzare le proprietà del nodo quando l&#39;XML di input è formattato e distribuito. NPR-26198: Hotfix per CQ-4250448
* IndexOutOfBoundException in ResourceProviderTracker. NPR-26968: Hotfix per GRANITE-23310
* La console JMX accumula numerose sessioni di amministrazione e una nuova sessione viene aperta ogni 5 minuti. NPR-26958: Hotfix per CQ-4251090
* Dopo l’aggiornamento da 6.2 a 6.4, il file di registro mostra la traccia dello stack per il risolutore di risorse non chiuso com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck. NPR-26176: Hotfix per GRANITE-21734
* Quando un agente di svuotamento del dispatcher out-of-the-box è configurato per l’aggiornamento degli alias, l’operazione non riesce con StackOverflowError. NPR-26373: Hotfix per CQ-4242928
* La replica utilizza il token OAuth scaduto finché non ha esito negativo. NPR-25894
* Pagina con limitazioni (pagina Gruppo utenti chiuso) con sling: alias non reindirizzerà l&#39;utente alla pagina di accesso. NPR-25715: Hotfix per Granite=22263
* Quando si pubblicano tag, non viene visualizzata alcuna attività nell&#39;interfaccia utente. Hotfix per CQ-4255961
* Impossibile modificare i tag nell’interfaccia classica. Hotfix per CQ-4258697
* Aggiornato org.apache.felix.http.bridge alla versione 4.0.4. NPR-27038: Backport per Granite - 23334
* I registri attività di Gestione pacchetti devono essere estratti in un file di registro separato. NPR-27323: Hotfix per GRANITE-14866
* La convalida del pacchetto non segnala le sovrapposizioni in CFP. NPR-27119: Hotfix per GRANITE-22825

**Progetti**

* API ACP non gestisce correttamente il paging con solo elementi secondari della sottodirectory. NPR-27617: Hotfix per CQ-4258639

**OAK**

* Impossibile accedere all&#39;archivio dopo l&#39;installazione di AEM 6.4 Service Pack 2. NPR-27171: Hotfix per GRANITE-23317

**Replica**

* Audit Log rimane aperto con sessioni attive che continuano ad aumentare costantemente con circa 750 al giorno. NPR-27062: Hotfix per CQ-4241350

**Community**

* I post e le risposte del forum vengono aggiunti all’inizio della seconda pagina e, dopo l’aggiornamento, il post si sposta nella posizione corretta all’inizio della prima pagina. NPR-27342: Hotfix per CQ-4247338
* Dopo lo scorrimento, i collegamenti a tutte le risorse rilasciano il percorso contestuale (/aempublish). NPR-26982: Hotfix per CQ-4254345
* I gruppi aggiunti non sono visibili nel menu a discesa Manager community, Moderatori community e Membri con privilegi durante la modifica di un sito pubblicato. NPR-27190: Hotfix per CQ-4258574
* Solo 10 gruppi sono elencati nella pagina delle risorse di abilitazione, anche se l’impaginazione è abilitata per l’elenco dei gruppi. NPR-26934: Hotfix per CQ-4252985
* L&#39;opzione per abilitare/disabilitare la ricerca per il post pianificato nel componente del giornale di registrazione è fornita in ConfigMgr, e il processo SearchScheduledPosts è ottimizzato. NPR-26923: Hotfix per CQ-4250463
* La ricerca per parole chiave nell’indirizzo non funziona nella pagina del componente calendario quando la community AEM è impostata per funzionare con DSRP. NPR-26737: Hotfix per CQ-4258493
* È stato implementato un collegamento diretto al commento invece del post principale nei dettagli di un commento, per le risorse relative all&#39;interfaccia utente e all&#39;abilitazione della moderazione. NPR-26704: Hotfix per CQ-4251381
* Il contenuto moderato tramite la selezione multipla nella console di moderazione non viene visualizzato nel Flusso attività. NPR-26695: Hotfix per CQ-4253244
* La ricerca con Nome e Cognome nel campo A di Messaggi di community non restituisce il risultato previsto. NPR-26385: Hotfix per CQ-4248673
* Errore durante il caricamento di un allegato in un formato diverso da quello immagine (ad esempio .pdf) nel forum. NPR-27360: Hotfix per CQ-4257753
* Se Author-Publish è impostato con MySQL DSRP, la funzione di annullamento o rimozione della funzionalità di un post del forum non funziona. NPR-26125; Hotfix per CQ-4251520
* I componenti della raccolta (forum, blog, calendario, ideazione, QnA) ora dispongono di una proprietà nella finestra di dialogo dei componenti per attivare/disattivare &quot;Blocca UGC in modalità Modifica autore&quot;, per consentire/negare il caricamento UGC in modalità Modifica WCM. NPR-26978: Hotfix per CQ-4248161
* La ricerca dei tag non funziona per i termini di ricerca localizzati. NPR-26171: Hotfix per CQ-4249926
* Il pulsante Indietro consente di saltare una pagina nella ricerca nel forum. NPR-26950: Hotfix per CQ-4254804
* L&#39;istanza AEM in esecuzione sulla porta HTTP predefinita (80) non riesce a raggiungere il file imsmanifest.xml. NPR-27173: Hotfix per CQ-4252211
* Se AEM Communities è impostato con DSRP, l&#39;opzione Rimuovi contrassegno commento come risposta per QnA non funziona. NPR-26247: Hotfix per CQ-4252232
* Impossibile chiamare Adobe Storage: Errore 414 - URI GET lungo osservato quando gli utenti effettuano la ricerca in /content/community-components/en/search.html e selezionano il campo autore come uno dei filtri per quel termine di ricerca. NPR-26643: Hotfix per CQ-4251303
* Il valore a discesa per DataCenterURL nella configurazione ASRP viene modificato da Dallas a Virginia (per VA6). NPR-26936: Hotfix per CQ-4254434
* Caratteri speciali negli errori di ritorno della ricerca nel forum o nessun risultato. NPR-26930: Hotfix per CQ-4247744
* Il numero visualizzato per &quot;Numero di risultati&quot; nella ricerca nel forum utilizza un delimitatore errato per le impostazioni internazionali Inglese e Tedesco. NPR-27050: Hotfix per CQ-4248939
* Le notifiche non lette non aumentano oltre le 21. NPR-26946, NPR-27480: Hotfix per CQ-4252829, CQ-4256939
* La paginazione nella sezione commenti di qualsiasi componente consente agli utenti di scorrere verso l’alto per visualizzare il contenuto della pagina, quando raggiungono una pagina attraverso l’impaginazione. NPR-27032: Hotfix per CQ-4251228
* Non è possibile fare clic sulla cartella Sito community sull&#39;immagine in miniatura quando si visualizza dalla console di amministrazione nell&#39;istanza di AEM Author. NPR-26986: Hotfix per CQ-4254036
* L&#39;opzione &quot;Contrassegna tutte le notifiche&quot; contrassegna solo le prime 10 notifiche come lette e le altre non vengono lette fino all&#39;aggiornamento della pagina. NPR-27037: Hotfix per CQ-4254058
* La paginazione non viene attivata per Ideazione e l&#39;elenco di argomenti (o risposte) diventa più lungo a meno che non venga ricaricato. NPR-26193: Hotfix per CQ-4252104
* Le attività di altri utenti e l&#39;UGC eliminato sono visibili al momento dell&#39;accesso con le credenziali del moderatore e durante l&#39;aggiunta di &quot;#social-activity&quot; o &quot;#tab-2&quot; alla fine dell&#39;URL del profilo del moderatore. Hotfix per CQ-4251355
* Non è possibile rimuovere tutti i tag assegnati da un articolo di blog. NPR-26851: Hotfix per CQ-4253359
* Le relazioni con UGC non vengono eliminate durante l&#39;eliminazione UGC. NPR-27630: Hotfix per CQ-4258706
* Il collegamento per le risposte non funziona con il clic di riga sulle risposte del forum. NPR-27623: Hotfix per CQ-4256138
* Il limite degli abbonamenti utente è limitato a 1000. NPR-27614: Hotfix per CQ-4254689
* La modifica di un sito e la modifica dei ruoli nelle impostazioni del ruolo generano un&#39;eccezione di puntatore Null. NPR-27377; Hotfix per CQ-4255909

**Traduzione**

* L&#39;anteprima della traduzione non funziona con il contenuto di esempio di We.retail. NPR-26727: Hotfix per CQ-4241179

**Interfaccia utente - Foundation**

* NullPointerException viene restituito quando si tenta di scaricare configurazioni dopo l’aggiornamento ad AEM 6.4. NPR-27310: Hotfix per Granite-23573
* Correzioni di Backport proattivo per granite.platform.login. NPR-26941
* Supporto proattivo per granite.ui.content. NPR-26294
* Il componente Campo numerico non convalida numeri negativi in Internet Explorer 11. NPR-26701
* Correzioni di granite.ui.coralui3 a supporto proattivo. NPR-26662
* Supporto proattivo per granite.ui.coralui3-eon. NPR-26666
* Correzioni di Proactive Backport per granite.ui.foundation.components. NPR-27313
* Correzioni di granite.ui.commons proactive Backport. NPR-26753
* Backport proattivi dell’interfaccia utente di Foundation. NPR-26248

**Integrazione**

* Le modifiche nelle esperienze AEM create tramite il motore di targeting non vengono pubblicate. NPR-24869: Hotfix per CQ-4247832
* Non è possibile creare più attività ed esperienze se i loro nomi includono caratteri giapponesi. NPR-27271: Hotfix per CQ-4256857
* Aggiorna endpoint API Launch. NPR-26790: Hotfix per CQ-4254380
* (Personalizzazione) BrandsRetriever guida l&#39;intero albero. NPR-27060: Hotfix per CQ-4255790

**WCM - Interfaccia utente amministratore**

* È stato aggiunto un test HTTP per pubblicare/annullare la pubblicazione di una pagina con riferimenti e un test dell&#39;interfaccia utente per Live Copy. Hotfix per CQ-4256894

**WCM - Editor pagina**

* La barra degli strumenti Modifica viene disattivata per i componenti al primo momento della modifica. Hotfix per CQ-4253270

**Forms**

Elementi di rilievo di AEM 6.4.3.0 Forms:

* È stato abilitato il supporto per un array o un elenco di oggetti con la sostituzione dinamica delle entità.
* Conformità FIPS abilitata per il flusso di lavoro di Reader Extended in Digital Signature, Reader Extensions, CryptoProvider e TrustStore.
* È stato aggiunto il supporto PDF/UA ai moduli XFA generati tramite Designer o Output Service.
* Abilitato il supporto per la proprietà allowPaths nei modelli di moduli adattivi.
* È stato aggiunto il supporto per JBoss 7.1.4 per AEM Forms 6.4.

**Pacchetto di componenti aggiuntivi per Forms**

**Integrazione con il back-end**

* Impossibile compilare le mappature del modello dati del modulo basate su entità dinamiche nella risposta SOAP. NPR-26428: Hotfix per CQ-4250639
* Il valore per _elementNamespace nel modello dati del modulo dati aggiuntivi, immesso utilizzando l&#39;interfaccia utente di prova, non viene riflesso correttamente nella richiesta SOAP. Hotfix per CQ-4255373
* Un vincolo di proprietà nullable viene inizializzato con un valore predefinito e non può essere sincronizzato con FDM. Hotfix per CQ-4253873
* Il valore predefinito per la proprietà nullable non è impostato su True per l&#39;origine dati OData. Hotfix per CQ-4253870

**Moduli adattivi**

* Impossibile caricare l&#39;editor siti e moduli. NPR-26977; Hotfix per CQ-4249170
* Problemi durante l&#39;aggiunta di un allegato a un modulo adattivo utilizzando la tastiera. NPR-25913; Hotfix per CQ-4249456

**Forms - Comunicazione interattiva**

* Impossibile spostare un pannello aggiunto utilizzando l&#39;opzione Aggiungi pannello figlio nella struttura del contenuto del canale Web della comunicazione interattiva e nei moduli adattivi. Hotfix per CQ-4253915
* I nomi delle tabelle vengono visualizzati al posto del titolo dell&#39;associazione FDM nella sezione Origini dati del canale Stampa. Hotfix per CQ-4253669
* La funzione isUseXFABullets() non è disabilitata nella classe PrintChannelRenderOptions ed è disponibile nell&#39;SDK client. Hotfix per CQ-4246583, CQ-4252700

**Gestione della corrispondenza**

* Javadocs per 6.4 non contiene i moduli com.adobe.dbforms.* pacchetto e le classi corrispondenti. Hotfix per CQ-4253200
* Nell&#39;interfaccia utente CCR viene visualizzato un valore spazzatura predefinito per il campo data, nel caso in cui non sia presente alcun input dall&#39;XML dei dati di prova. Hotfix per CQ-4252041
* Se una lettera contiene un modulo elenco, lo spazio tra punto elenco e testo viene perso durante la generazione del PDF dalla lettera. Hotfix per CQ-4250588

**Forms Manager**

* Abilitato il supporto per la proprietà allowPaths nei modelli di moduli adattivi. NPR-26598: Hotfix per CQ-4255892

**Forms - Flusso di lavoro**

* Se nel nome dell&#39;attività sono incluse le parentesi graffe durante l&#39;esecuzione del flusso di lavoro Forms, nei registri viene visualizzata un&#39;eccezione. Hotfix per CQ-4256626
* Impossibile aprire un modello di ricerca nell&#39;area di lavoro Moduli AEM. Hotfix per CQ-4255651

**Moduli mobili**

* La notifica di uscita non viene visualizzata durante l&#39;uscita dal campo data in AEM Forms rappresentata come HTML in Internet Explorer o Chrome. NPR-26483: Hotfix per CQ-4239352
* Le date contenute nel codice XML all&#39;inizio dell&#39;elaborazione causano la visualizzazione di un errore di convalida da parte dei moduli quando l&#39;utente tenta di uscire dal modulo. NPR-26787: Hotfix per CQ-4251211

**Programma di installazione di JEE per Forms**

**PDF Generator Service**

* Impossibile visualizzare le impostazioni di Reporting e conformità per PDF Generator. NPR-26715: Hotfix per CQ-4253384
* file binario convertpdf mancante nel pacchetto del componente aggiuntivo AIX Forms, che causa un errore durante la chiamata del servizio PDFA. Hotfix per CQ-4257873

**Servizi basati su documenti**

* Conformità FIPS per il flusso di lavoro RE in Digital Signature, Reader Extensions, CryptoProvider e TrustStore. NPR-27495: Hotfix per CQ-4257572
* La conversione non riesce durante l&#39;esecuzione del servizio AssemblerService.toPDFA in un ciclo. NPR-26354: Hotfix per CQ-4248656
* Impossibile convalidare correttamente la conformità dei PDF in base agli standard PDF/A-1b. NPR-26286: Hotfix per CQ-4227539
* Problemi di memoria insufficiente durante l&#39;aggiornamento di AEM Forms da 6.1 SP2 CFP5 a CFP13. NPR-26285: Hotfix per CQ-4244379
* Impossibile convalidare correttamente la conformità dei PDF in base agli standard PDF/A. NPR-26272: Hotfix per CQ-4248823

**Forms - JEE di base**

* È stato aggiunto il supporto per JBoss 7.1.4 per AEM Forms 6.4. NPR-27331; Hotfix per CQ-4255601

**Feature Pack inclusi**

* È stato abilitato il supporto per un array o un elenco di oggetti con la sostituzione dinamica delle entità. NPR-26590: Hotfix per CQ-4254655

**Pacchetti OSGI e pacchetti di contenuti inclusi**

Elenco dei bundle OSGi inclusi in AEM 6.4.3.0

[Ottieni file](assets/6.4.3.0_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.3.0

[Ottieni file](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0 is an important update that includes performance, stability, security and key customer fixes and enhancements released since the general availability of AEM 6.4 in **April 2018.**
È inoltre cumulativo, il che significa che 6.4.2.0 include tutte le versioni dei Service Pack di AEM 6.4 precedenti.

Alcuni degli elementi di rilievo di AEM 6.4.2.0 sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.7.
* È stato aggiunto il supporto per le funzionalità HTML Template Language (HTL) Specification 1.4
* È stato aggiunto il supporto per MongoDB Enterprise 3.6.
* L’Editor pagina Siti offre supporto per la modifica e la composizione contestuali con componenti lato client creati in React o Angular in combinazione con l’SDK <a href="../sites-developing/spa-walkthrough.md">JS per editor SPA di</a>AEM.
* Miglioramenti per i frammenti di contenuto: aggiunta la possibilità di inserire annotazioni nei campi di testo e confronto tra versioni affiancate.
* È stata aggiunta [l’integrazione con Adobe Stock](/help/assets/aem-assets-adobe-stock.md) per consentire agli utenti di effettuare ricerche, visualizzare in anteprima, salvare e ottenere la licenza per le risorse Adobe Stock direttamente dall’interfaccia utente di AEM. Per informazioni dettagliate, consultate [Utilizzo di risorse Adobe Stock con Risorse](https://helpx.adobe.com/experience-manager/kt/assets/stock-assets-feature-video-use.md)AEM.
* Risorse ha aggiunto il supporto per il metaschema condizionale dinamico e la possibilità di impostare uno schema di metadati per le cartelle di risorse.
* È stata aggiunta una configurazione in ciascun componente per attivare/disattivare la funzionalità di creazione/aggiornamento delle miniature delle cartelle.
* Miglioramenti nell’editor di immagini per l’authoring delle pagine.
* Correzione di regressione in Communities per la gestione non corretta dell&#39;evento di punteggio nel caso in cui la risposta selezionata venga eliminata.
* Limite massimo di risultati di ricerca rivisto per solr a MAX_INT-10000.
* Il processo di scaricamento delle transazioni viene avviato solo sulla prima chiamata a storeTransaction.
* Il pulsante &quot;Seleziona tutto&quot; è ora disponibile nelle viste a schede e a colonne.
* Miglioramenti all’accessibilità in CoralUI.
* Gestione Coral.Keys migliorata.
* Aggiornato momento.js a 2.22.2
* Jquery aggiornata a 1.12.1
* È stato introdotto il componente foundation-workflowstatus.
* Aggiornato GCC alla versione più recente.
* Sposta SAML nella nuova sincronizzazione IDP esterna.

**Assets**

* La generazione di risorse secondarie per i file pptx non contiene immagini e miniature. NPR-24286: Hotfix per CQ-4217986
* migrateAllAssets - Aggiungi supporto per l’elaborazione batch e migliora il metodo AEM che aggiunge UUID alle risorse precedenti. NPR-24861: Hotfix per CQ-4242863 e CQ-4247874
* Problema di prestazioni con la generazione delle miniature. NPR-24693: Hotfix per CQ-4246960
* (Interfaccia touch) Il componente &quot;predicato opzioni&quot; rimane vuoto quando viene aggiunto alla pagina di pubblicazione di Condivisione risorse. NPR-24643: Hotfix per CQ-4245295
* (Workflow) Smart Tag Assets non viene elaborato tramite la configurazione proxy. NPR-25840: Hotfix per CQ-4248202
* (Omnisearch) la rimozione di filetype:image dai criteri di ricerca non rimuove il tipo di immagine. NPR-25232: Hotfix per CQ-4248280
* Quando si tenta di spostare un file in un&#39;altra cartella, le cartelle con l&#39;apostrofo nel nome non vengono visualizzate. NPR-25125: Hotfix per CQ-4248660
* Il cursore nella pagina Risorse secondarie non funziona correttamente se le preferenze della lingua sono impostate su un valore diverso dall&#39;inglese. NPR-25274: Hotfix per CQ-4248489
* Problema con il file CSV di esportazione dei metadati quando aperto su computer con formato numero europeo. NPR-26009: Hotfix per CQ-4250677
* Il pulsante Crea non è disponibile per la selezione delle cartelle di risorse senza l’autorizzazione &quot;Elimina&quot;. NPR-25788: Hotfix per CQ-4250140
* (Backport) Miglioramenti all&#39;accessibilità: Duplicate-id: il valore dell&#39;attributo id deve essere univoco, Label: Gli elementi modulo devono avere etichette e nome collegamento: I collegamenti devono avere testo visibile. NPR-24252: Hotfix per CQ-4250905, CQ-4250906, CQ-4250907
* Il caricamento di un CSV con campi separati da &quot;,&quot; non riesce per i paesi europei. NPR-25549: Hotfix per CQ-4249931
* (Portale del marchio) Le risorse secondarie di un file pdf con più pagine non vengono pubblicate quando una risorsa viene pubblicata. NPR-25991: Hotfix per CQ-4245162
* Pubblica funzionalità successive per la replica di AEM su Brand Portal. NPR-25911: Hotfix per CQ-109139
* La pubblicazione e l&#39;annullamento della pubblicazione della raccolta privata da parte di utenti non amministratori generano un NPE. NPR-25906: Hotfix per CQ-4250594
* Disattiva la pubblicazione di frammenti di contenuto e schemi di moduli in Brand Portal. NPR-24176, NPR-26004: Hotfix per CQ-4251592, CQ-4252026
* (Contenuti multimediali dinamici) Sono stati aggiornati visualizzatori DM alla versione 5.10.1, che consente di verificare la presenza di nomi duplicati nella pagina Predefinito immagine. Consultate Aggiornamento dei visualizzatori per contenuti multimediali dinamici (5.10.1). NPR-24403: Hotfix per CQ-4247554
* Errore JavaScript nella console del browser nella vista a colonne quando si seleziona una risorsa o una cartella. NPR-25939: Hotfix per CQ-4250228
* (Vista a colonne) Impossibile identificare le attività in quanto il file chiave viene visualizzato come voce bianca vuota. NPR-25903: Hotfix per CQ-4246307

**Sites**

* La query di datasource.jsp su AEM 6.2 è diversa da AEM 6.4. NPR-24968: Hotfix per CQ-4244235
* (Interfaccia classica) Impossibile aggiungere tag alle pagine. NPR-25255, NPR-25612: Hotfix per CQ-4249615
* Funzionalità HTML Template Language Specification 1.4 riportate in AEM 6.4.2.0 NPR-24585
* Ereditarietà errata sul componente locale dopo la copia di una pagina Live Copy. NPR-25920: Hotfix per CQ-4236737, CQ-4248957
* Il tempo di attivazione/disattivazione è memorizzato in crx/de ma non recupera lo stesso nella console dell’interfaccia utente delle proprietà della pagina. NPR-25154: Hotfix per CQ-4243431
* Stili Il sistema interrompe i valori iniziali delle proprietà della finestra di dialogo. NPR-25648: Hotfix per CQ-4250073
* Quando si definisce una proprietà cq:tagName in un nodo cq:htmlTag, il nome del tag non viene considerato se il componente è incluso tramite JSP. NPR-24154: Hotfix per CQ-4244120
* Per un componente parsys nidificato, viene sempre applicato il primo (con un percorso meno nidificato) che soddisfa i requisiti di progettazione da più componenti disponibili. Per ulteriori informazioni, consultate Risoluzione [del percorso di](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/page-templates-static.html)progettazione. NPR-24973: Hotfix per CQ-4246276
* Quando incollate del testo in un componente RTE, viene visualizzata una finestra di dialogo a comparsa ma non viene eseguito correttamente il rendering. NPR-24895: Hotfix per CQ-4245901
* (RTE) Problemi di prestazioni con l&#39;indicatore di campo obbligatorio. NPR-24894: Hotfix per CQ-4241895
* (Componente Pagina) L’aggiunta di un componente a Parsys viene ritagliata da destra ed esce dalla larghezza del fotogramma del dispositivo. NPR-25536: Hotfix per CQ-4238224
* L’editor di testo normale invia dati non tagliati e aggiunge spazi aggiuntivi. NPR-25312: Hotfix per CQ-4249006
* Quando aprite il componente in modalità inline, i plug-in caricati in precedenza non sono visibili alla seconda volta. NPR-24610: Hotfix per CQ-4236850
* Il caricamento di un XF nella visualizzazione dell&#39;editor tramite copia/incolla non carica automaticamente la variante principale. NPR-24841: Hotfix per CQ-4248037
* Struttura HTML errata in siteadmin / damadmin interrompe IE11. NPR-24686: Hotfix per CQ-4246363, CQ-4248402
* (Gestione guidata pubblicazione) Il calendario per la data di attivazione al passaggio Opzioni non si apre dopo alcune azioni nel passaggio Ambito. NPR-25681: Hotfix per CQ-4250205
* L’interfaccia classica non funziona per la modifica di gruppi utente chiusi (CUG) perché è diventata obsoleta. NPR-25075: Hotfix per 4241823
* Opzione Crea non disponibile per creare frammenti esperienza. NPR-26053: Hotfix per CQ-4249923
* La variazione XF viene attivata due volte di più, generando ID duplicati per lo stesso elemento. NPR-24179: Hotfix per CQ-4245093
* La tabella di Foundation presenta una vulnerabilità cross-site scripting archiviati. NPR-25185: Hotfix per CQ-4240760
* Errore &#39;Valore selettore ricorsione non valido&#39; durante la migrazione di un componente da AEM 6.2.1.13 ad AEM 6.4. NPR-24146

**WCM - Editor pagina**

* La presenza di più istanze sovrapposte di parsys (più di 6) causate da query con tempi di esecuzione lunghi rallenta l’esecuzione di AEM. Hotfix per CQ-4240247
* Errore JS quando si aggiunge cq:tagName vuoto nel nodo cq:htmlTag. Hotfix per CQ-4251852
* Aggiorna EditableActions in base alla rilocalizzazione columnClassNames. Hotfix per CQ-4250781
* Esporre i percorsi delle risorse e dei modelli utilizzando un&#39;unica proprietà e un singolo attributo. Hotfix per CQ-4251255
* Ripristina le modifiche dell&#39;API export.json. Hotfix per CQ-4251854
* (Editable SPA) Versione candidata per la versione 1.0.0. Hotfix per CQ-4251991
* La barra degli strumenti Modifica viene disattivata per altri componenti quando si modifica un componente. Hotfix per CQ-4253270

**Integrazione**

* I campi Libreria e Scarica URL devono essere modificabili. NPR-24804: Hotfix per CQ-4246864
* Problema con più configurazioni DTM. NPR-24685: Hotfix per CQ-4247293
* È stato aggiunto il supporto per la distribuzione asincrona per le librerie client ospitate. NPR-25716: Hotfix per CQ-4245745
* Il componente di destinazione con offerta corrispondente mancante esegue il rendering dell’intera pagina e, invece di un componente di destinazione vuoto, viene aggiunta un’altra rappresentazione completa della pagina. NPR-25273: Hotfix per CQ-4248003
* Il motore target (mbox.js, at.js) non utilizza URL gestiti e utilizza URL contenenti due punti, che potrebbero non riuscire con determinate implementazioni. NPR-25339: Hotfix per CQ-4237854
* (Launch)LibraryDownloadProcess memorizza il valore libraryUri errato. NPR-25330: Hotfix per CQ-4250006

**Platform**

* Ciclo di reindicizzazione| NPE durante l&#39;esecuzione di BinaryTextExtraction durante l&#39;aggiornamento locale da 6.3 a 6.4. Hotfix per Granite - 21677
* Sostituzione transfrontaliera del percorso interno contrassegnato /libs/cq/cloudserviceconfigs/templates/configpage/jcr:content - Problema durante l&#39;esecuzione del rilevatore di pattern. NPR-25036: Hotfix per CQ-4248597
* Voci di registro non scritte a causa di NPE in LogEntryImpl. NPR-25627: Hotfix per GRANITE-22383
* La replica dell&#39;evento delete non verifica i diritti. NPR-25679: Hotfix per CQ-4241234
* È stato aggiunto il supporto STARTTLS in &quot;Day CQ Mail Service&quot;. NPR-25611: Hotfix per CQ-4249924
* Correzioni proattive di backport per granite.platform.login per migliorare l&#39;accessibilità. NPR-25176: Hotfix per Granite 21746 e Granite-21309
* (AEM 6.4) Errore durante la ricreazione del pacchetto e la reinstallazione. NPR-25173: Hotfix per CQ-4247939
* Rimosso il valore predefinito MERGE_PRESERVE aclHandling. NPR-24593: Hotfix per GRANITE-21889
* Content-Type non viene propogato e manca nella risposta dopo l&#39;applicazione di ContentDispositionFilter due volte. NPR-24175: Hotfix per Sling-7525
* Stato di Package Manager errato dopo l&#39;aggiornamento al ramo AEM 6.4. NPR-24551: Hotfix per GRANITE-21750
* Istanza AMS - Analisi dei registri di errore. Hotfix per CQ-4249567

**Sicurezza**

* Il login SAML reindirizza alla pagina di disconnessione tramite Okta IDP. NPR-25523: Hotfix per GRANITE-22364
* L&#39;autenticazione IMS tramite le configurazioni OAK del provider OAuth IDP esterno disattiva l&#39;utente creato in AEM. NPR-25301: Hotfix per GRANITE-22363

**MAC - Integrazione Test&amp;Target**

* (Targeting) Errore del componente di testo durante il targeting. Hotfix per CQ-4233343

**Community**

* (Libreria file) Il download di risorse con spazi vuoti per problemi di formato. NPR-24260: Hotfix per CQ-4245159
* Correzioni per diversi problemi relativi ad Adobe Social. NPR-24247: Hotfix per CQ-4245054, CQ-4245120, CQ-4245296
* Lo scorrimento infinito per la console di membri e gruppi non riesce nel caso in cui l’authoring venga eseguito su percorsi di contesto diversi. NPR-24437: Hotfix per CQ-4246013
* Il post non ritorna allo stato senza risposta anche quando si rimuove dallo stato di risposta e il punteggio non diminuisce. NPR-24419: Hotfix per CQ-4245797, CQ-4245932
* Gli eventi aggiunti utilizzando la funzionalità di calendario nelle comunità restituiscono valori errati. NPR-24883: Hotfix per CQ-4244056
* (Forum community) Problemi con il comportamento di clic e caricamento della pagina nell’impaginazione. NPR-24880: Hotfix per CQ-4246109
* (Chrome) Le conversioni del fuso orario non vanno a buon fine sugli eventi delle community. NPR-24881: Hotfix per CQ-4247115
* Impossibile eseguire il rendering dell&#39;oggetto incorporato in E-mail. NPR-24999: Hotfix per CQ-4248022
* La sequenza di automazione deve essere eseguita con l&#39;aggiornamento UGC oltre alla creazione UGC. NPR-25892: Hotfix per CQ-4251399
* Risposta modale del dialogo sui gruppi. NPR-25623: Hotfix per CQ-4248805
* Eccezione Solr restituita all&#39;eliminazione del contenuto. NPR-25869: Hotfix per CQ-4248908
* I collegamenti impaginati a thread con molti post non funzionano sulle notifiche. NPR-25678: Hotfix per CQ-4243038
* I valori temporali nei risultati della ricerca mostrano l&#39;ora del server invece del fuso orario del client. NPR-25594: Hotfix per CQ-4248986
* (Commenti forum) Il pulsante Indietro del browser non funziona come previsto. NPR-25205: Hotfix per CQ-4248573
* (Risultati ricerca) Il pulsante Indietro del browser non funziona come previsto. NPR-25214: Hotfix per CQ-4248574
* Il valore Null viene restituito quando si sovrappone il componente communityGrouperlist. NPR-25228: Hotfix per CQ-4248523
* (Calendario community) ClassCastException viene generata durante il salvataggio dell&#39;evento con la nuova immagine Cover. NPR-25167: Hotfix per CQ-4248662
* (Community) Messaggi che vengono troncati. NPR-25326
* (AEM Publish) Scorm Resource non riesce con il percorso contestuale e mostra una schermata vuota. NPR-26155: Hotfix per CQ-4251942
* (MSRP) Il calendario appena creato viene salvato generando parzialmente NPE nel registro degli errori. NPR-26071: Hotfix per CQ-4250531
* L&#39;impaginazione forum/Argomento viene aggiornata solo quando la pagina viene aggiornata. NPR-26070, NPR-25965: Hotfix per CQ-4249509
* (Forum D e R) Impossibile passare alla pagina precedente quando si apre un collegamento diretto a un commento. NPR-26069: Hotfix per CQ-4251699
* Il caricamento dell’immagine nel gruppo Crea non funziona sui dispositivi mobili. NPR-26172: Hotfix per CQ-4251703
* (Messaggi) Quando si utilizza DSRP, il nome del ricevitore dei messaggi viene sempre visualizzato come &quot;Sconosciuto&quot;. NPR-26056: Hotfix per CQ-4251397
* L’etichetta dello stato di completamento Risorsa Scorm di attivazione risulta vuota nell’interfaccia utente. NPR-26034: Hotfix per CQ-4249994
* Durante la creazione di un nuovo gruppo community, viene creato un gruppo community duplicato su un cluster mongoMK attivo/attivo. NPR-26032: Hotfix per CQ-4245884
* (Autore) La procedura guidata per la creazione di gruppi richiede troppo tempo per caricare o creare un gruppo all’interno della procedura guidata. NPR-26031: Hotfix per CQ-4244966
* Parsys scompare quando si aggiunge un&#39;istruzione include nello script hbs. NPR-25908: Hotfix per CQ-4250489
* Quando si abilita “Consenti membri privilegiati”, i membri con le autorizzazioni necessarie dovrebbero essere in grado di comporre solo per gli utenti che sono membri della community. NPR-25877: Hotfix per CQ-4248450
* Dettagli bloccati per l&#39;abilitazione. NPR-25966: Hotfix per CQ-4251478
* L&#39;impaginazione dei forum non viene aggiornata dinamicamente alla rimozione delle risposte. NPR-25970: Hotfix per CQ-4248975, CQ-4252843
* Lo scorrimento automatico e l&#39;evidenziazione non funzionano sugli eventi calendario e filelib in caso di commenti nidificati. NPR-25958: Hotfix per CQ-4251471
* (DSRP) Le prestazioni dei collegamenti diretti/profondi si degradano con l&#39;elevata quantità di contenuti generati dall&#39;utente. NPR-25957: Hotfix per CQ-4251470
* Impossibile modificare le proprietà di Consenti membri privilegiati e membri privilegiati. NPR-26014: Hotfix per CQ-4244592
* Contrassegna tutto come letto ripristina i contatori di notifica per tutte le pagine della community. NPR-25931: Hotfix per CQ-4248612
* Modifica IT non riuscita per DSRP. NPR-25929: Hotfix per CQ-4251382
* L&#39;IT dell&#39;e-mail non riesce a causa del NPE durante la creazione dei modelli delle e-mail. NPR-26039: Hotfix per CQ-4250962
* Problemi di thread del forum durante l&#39;incorporazione di immagini con risoluzione molto elevata. NPR-26037: Hotfix per CQ-4244453, CQ-4253099
* L&#39;ora visualizza gli switch quando il fuso orario del server è diverso dal fuso orario dell&#39;utente. NPR-26036: Hotfix per CQ-4248751
* Se si allega due volte un file con lo stesso nome a un post del forum, si verifica un errore del server. NPR-24172: Hotfix per CQ-4244367
* Correzioni delle prestazioni di backport: impaginazione di gruppo su autore e pubblicazione, ricerca di gruppo sull&#39;autore, Evitare la serializzazione delle risposte per giornale di registrazione, calendario e ideazione e caricamento pigro per ottenere l&#39;appartenenza al gruppo (invito/annullamento dell&#39;invito) pulsante per ogni gruppo durante la visualizzazione della pagina di elenco dei gruppi. NPR-24538: Hotfix per CQ-4246515
* Risorse di abilitazione non sono visibili sull’autore. Hotfix per CQ-4252618
* Le notifiche non vengono generate per il thread di un utente sconosciuto. Hotfix per CQ-4245132
* La ricerca del gruppo non viene visualizzata nella barra a sinistra. Hotfix per CQ-4252621
* (Autore) La paginazione non funziona per la console Gruppi. Hotfix per CQ-4242786
* Aggiornamento dell’interfaccia utente jQuery. Hotfix per CQ-4248894
* Aggiornamento alla versione più recente di SCORM 2017.1. NPR-25675: Hotfix per CQ-4240671
* I campi &quot;Componi per conto&quot; sono visibili agli utenti non appartenenti alla community. NPR-25331: Hotfix per CQ-4247858
* Post è ancora visibile nell’interfaccia utente anche dopo l’eliminazione e restituisce un errore sulla console. NPR-26290: Hotfix per CQ-4252803
* (Impostazioni del sito) È possibile salvare le modifiche apportate ai ruoli. NPR-26274: Hotfix per CQ-4252187
* (Vulnerabilità di sicurezza) Recupero account a causa di configurazione errata del token Web JSON. NPR-26458: Hotfix per CQ-4253314
* La paginazione non viene reimpostata al momento della rimozione delle risposte. NPR-26326: Hotfix per CQ-4252997
* L&#39;immagine dell&#39;allegato non viene visualizzata nelle bozze durante la modifica. Hotfix per CQ-4253360
* La pagina non viene aggiornata durante il collegamento dell&#39;allegato nel database relazionale (DSRP). Hotfix per CQ-4253084
* I gruppi non funzionano all&#39;interno della risorsa del sito di abilitazione. Hotfix per CQ-4252975
* I prerequisiti Percorsi di apprendimento non sono persistenti in Abilitazione. Hotfix per CQ-4252948

**Flusso di lavoro**

* L’interfaccia utente di avvio del flusso di lavoro non visualizza precedenti configurazioni di avvio 41 e genera un errore javascript nella console. NPR-25028: Hotfix per CQ-4247604
* La modifica di un flusso di lavoro legacy senza modificarne il lancio causa la creazione di più flussi di lavoro in qualsiasi flusso di lavoro che contenga un passaggio Attiva pagina/Risorsa. NPR-25870: Hotfix per CQ-4250896
* Collegamento non corretto nel payload del flusso di lavoro se la pagina ha un nodo di metadati. NPR-25916: Hotfix per CQ-4250733

**Traduzione**

* È stato corretto il seguente problema: l’importazione di un progetto convertito generava due richieste POST simultanee, causando quindi un errore. NPR-24889: Hotfix per CQ-4247638
* È stato corretto il seguente problema: durante la creazione di un progetto di traduzione per più lingue, tutte le pagine della stessa lingua venivano aggiunte allo stesso processo. NPR-25091: Hotfix per CQ-4246112
* È stato corretto il seguente problema: in alcuni casi, il processo di traduzione conteneva solo le prime 40 pagine. NPR-25974: Hotfix per CQ-4248661
* Il componente DataPicker (Coral2) non modifica l’anno. NPR-24466: Hotfix per GRANITE-21893

**Interfaccia utente - Foundation**

* Backport proattivi dell’interfaccia utente di Foundation. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-259 35, NPR-25976
* (Importazione progettazione) L&#39;importazione di una pagina non importa js,css. NPR-25203: Hotfix per GRANITE-22236
* Interfaccia utente Proactive Foundation Backport per migliorare la stabilità del prodotto. NPR-24334

**MAC - Integrazione Test&amp;Target**

* La seconda pagina di PersonalizationWizard ( avviata da &quot;Start Targeting&quot;) è vuota e genera errori nella console. Hotfix per CQ-4253277

**Frammenti esperienza**

* Integrazione di frammenti esperienza/Target uniti in AEM 6.4.2.0. Hotfix per CQ-4248653

**Gestione dei frammenti di contenuto**

* Note sui frammenti di contenuto e confronto affiancato delle versioni dei frammenti di contenuto. Hotfix per CQ-4247148

**DAM - Generale**

* Filtro &quot;Estratto da&quot; non funzionante correttamente nella ricerca. Hotfix per CQ-4247070
* Durante il flusso di lavoro di aggiornamento delle risorse, la copia della lingua e la relativa miniatura diventano vuote. Hotfix per CQ-4250641
*  Duplicate-id: il valore dell&#39;attributo id deve essere univoco. Hotfix per CQ-4250905
* Etichetta: Gli elementi modulo devono avere etichette. Hotfix per CQ-4250906
* Nome collegamento: I collegamenti devono avere testo visibile. Hotfix per CQ-4250907
* JMX e ServiceUserMapping di migrazione dei modelli di metadati delle cartelle porte. Hotfix per CQ-4252947
* Test WebdriverIO non in esecuzione nel ramo release/640 di CQ/dam. Hotfix per CQ-4252749
* I collegamenti alle risorse spostate non vengono modificati se il collegamento viene pubblicato. Hotfix per CQ-4245756

**DAM - Visualizzatori**

* Errore intermittente durante il caricamento di video con i nuovi visualizzatori 5.10.1. Hotfix per CQ-4250562

**DAM-Brand Portal**

* L&#39;annullamento della pubblicazione della raccolta da Brand Portal non riesce. Errore. Hotfix per CQ-4245990
* Impossibile annullare la pubblicazione dei predefiniti per immagini dal Brand Portal. Hotfix per CQ-4246140
* Le risorse secondarie di un file PDF con più pagine non vengono pubblicate quando una risorsa viene pubblicata. Hotfix per CQ-4245162

**DAM - DMClient**

* Quando pubblicate una risorsa video su YouTube, i tag che determinano la pubblicazione su YouTube includono il percorso completo del tag. Hotfix per CQ-4245549
* (Aggiornamenti di rifiuto e consenso) Problema con il reindirizzamento CSS del visualizzatore. Hotfix per CQ-4247854
* Impossibile creare/modificare il predefinito per visualizzatori come non membro del gruppo &#39;amministratori&#39;. Hotfix per CQ-4247618
* (6.4.1.0) L’aggiunta di più video in più parsys interrompe il lettore video. Hotfix per CQ-4248517
* Se si rinomina e si sposta la risorsa all’interno di un set di immagini, la modifica risulta impossibile. Hotfix per CQ-4248434
* Pubblicare video di grandi dimensioni su YouTube genera messaggi di timeout. Hotfix per CQ-4237831
* (Visualizzazione a elenco) L’interfaccia utente del selettore/selettore risorse è grigia e disattivata per l’utente. Hotfix per CQ-4237817
* (Zoom Verticale) Css non viene caricato con un errore 404. Hotfix per CQ-4236508
* Se si tenta di scaricare una risorsa con il carattere percentuale (%) nel nome della risorsa, l&#39;archivio rimane vuoto. Hotfix per CQ-4250558
* (Vista a schede) Quando si utilizza Copia e Incolla su una risorsa video, non viene visualizzato alcun indicatore di elaborazione. Hotfix per CQ-4249037
* (Aggiornamento da 6.3.2 a 6.4) I predefiniti per immagini pre-aggiornamento sono visualizzati come &quot;Non pubblicato&quot; nella pagina Rendering, ma non generano un pulsante URL se selezionato. Hotfix per CQ-4240406
* Debiti Tecnici/Miglioramenti Minori. Hotfix per CQ-4240648
* Il selettore risorse (o selettore risorse) non mostra tutte le risorse dalle cartelle disponibili. Hotfix per CQ-4218414
* Il predefinito per immagini senza altezza mostra le immagini con dimensioni errate. Hotfix per CQ-4246546
* Quando si fa clic sulle annotazioni, l’interfaccia utente si interrompe. Hotfix per CQ-4251434
* Con l’aggiornamento dal 6.3 al 6.4 e versioni successive del predefinito Analytics, viene creata una nuova suite di rapporti e un nuovo predefinito di analisi che perde i vecchi dati di reporting dell’utente. Hotfix per CQ-4244529
* (Gestione guidata pubblicazione) L’elenco delle risorse appare vuoto quando si tenta di pubblicare o annullare la pubblicazione. Hotfix per CQ-4251881
* Quando si scelgono i visualizzatori dopo aver visualizzato i membri del set, i video AVS non vengono riprodotti. Hotfix per CQ-4205308
* I predefiniti di elaborazione video pre-aggiornamento non possono presentare nuovi predefiniti di codifica video aggiunti o modificati. Hotfix per CQ-4240407
* I predefiniti per immagini non vengono applicati alle rappresentazioni dinamiche scaricate. Hotfix per CQ-4249862
* Il pulsante Seleziona tutto non funziona correttamente nella pagina di elenco dei predefiniti per visualizzatori. Hotfix per CQ-4252462
* Profili video: Il pulsante Seleziona tutto non funziona. Hotfix per CQ-4253076, CQ-4251447
* Passaggio convalida SP2 - Passaggio fumo. Hotfix per CQ-4251639

**DAM - Servizi DM**

* Generazione di rappresentazioni per file EPS non riuscita. Hotfix per CQ-4243688

**GRANITE**

* Digitate nel bundle SymbolicName per creare un bundle duplicato. Hotfix per GRANITE-22155
* La configurazione CUGConfiguration non può rilevare CugExclude. Hotfix per GRANITE-21109
* Il riavvio di Adobe Granite Workflow Core riavvia i passaggi del flusso di lavoro dal centro alla creazione di flussi di lavoro non necessari. NPR-25057: Hotfix per GRANITE-22218
* JcrResourceBundle non supporta correttamente più nomi di base. NPR-25245: Hotfix per GRANITE-22317
* Una volta installati i pacchetti di contenuto, gli ACL vengono raggruppati per entità, pertanto, interrompendo il modello di autorizzazione. NPR-24583: Hotfix per GRANITE-21591
* Aggiorna Jetty a 9.4.11 per risolvere le vulnerabilità. NPR-25030: Hotfix per GRANITE-22120

**Forms**

Elementi di rilievo di AEM 6.4.2.0 Forms:

* Aggiunta di una nuova proprietà per le code da aggiornare senza aggiornare il browser.
* Aggiunta la possibilità per l&#39;utente di utilizzare lo stesso file WSDL per più servizi.
* È stato rimosso il pattern di marca temporale non supportato dal menu a discesa del carrello.
* È stato aggiunto il supporto per la sovrapposizione di xfaf e pdf in OSGI.
* È stato aggiunto il supporto per utilizzare la funzionalità [di rapporti sulle](https://helpx.adobe.com/experience-manager/6-4/forms/using/transaction-reports-overview.html) transazioni nelle distribuzioni in sede.
* È stato aggiunto del codice per non visualizzare var figlio nell&#39;editor delle regole di condizione.

**Pacchetto di componenti aggiuntivi per Forms**

**Reporting transazione**

* Aggiornare la configurazione di Report transazione con l&#39;importanza della replica inversa configurata su un server di pubblicazione. NPR-26050: Hotfix per CQ-4246650
* Inizializzazione ritardata del processo di scaricamento periodico. NPR-25968: Hotfix per CQ-4245024
* La registrazione della transazione non riesce con un&#39;eccezione di puntatore Null. Hotfix per CQ-4247302

**Forms - Flusso di lavoro**

* (Area di lavoro HTML) Quando un utente richiede un’attività, il numero di code viene aggiornato per quel particolare utente ma non per altri utenti a meno che la pagina non venga aggiornata. Questo problema è stato risolto da una nuova proprietà. Per configurare questa nuova proprietà nell’istanza di AEM, consulta Impostazioni di configurazione. NPR-24536: Hotfix per CQ-4233665
* Impossibile caricare il modulo di grandi dimensioni nell&#39;app AEM Forms in 6.4. NPR-24463: Hotfix per CQ-4245091
* Problema nell&#39;app di Mobile Workspace quando si tenta di visualizzare l&#39;attività condivisa. NPR-25177: Hotfix per CQ-4248733
* Comportamento di convalida non coerente tra Web e APK. NPR-25670: Hotfix per CQ-4248178
* Quando si effettua una chiamata a un servizio Web, un modulo HTML5 aperto all’interno del client ha esito negativo e viene restituito un messaggio di errore. NPR-26048: Hotfix per CQ-4244716
* Problema durante la chiamata di un servizio in AEM moduli Windows app 6.3. NPR-26468: Hotfix per CQ-4252341

**Moduli mobili**

* (Set di moduli) Problema di convalida dei campi SSN e Mobile durante l&#39;anteprima. NPR-24458: Hotfix per CQ-4244983
* I dati non vengono visualizzati con la precompilazione di campi con più righe nell&#39;anteprima HTML. NPR-24549: Hotfix per CQ-4244212
* I dati vengono persi quando lo script viene valutato in un campo multiriga. NPR-25333, Hotfix per CQ-4249610

**Moduli - Comunicazione interattiva e gestione della corrispondenza**

* La sincronizzazione non riesce su IC con Modello di base e Modello di stampa IC di riferimento. NPR-24912
* (CCR) I convalidatori non funzionano per campi/variabili. Hotfix per CQ-4245047
* L&#39;icona Oggetto modello dati scompare a intervalli sulla barra degli strumenti Modifica testo. Hotfix per CQ-4245122
* I registri delle eccezioni vengono visualizzati sull&#39;IC copiato se l&#39;IC originale viene eliminato. Hotfix per CQ-4249378
* Nella rappresentazione della lettera, la condizione non restituisce true anche quando i dati sono corretti. Hotfix per CQ-4245944
* I componenti generati automaticamente non vengono evidenziati quando si seleziona dalla struttura Contenuto. Hotfix per CQ-4246178
* Problemi durante l&#39;apertura dell&#39;editor Modello canale Web. Hotfix per CQ-4248182
* Impossibile modificare l&#39;ordine delle risorse aggiunte poiché le frecce su/giù rimangono disattivate. Hotfix per CQ-4252042
* Impossibile aggiornare le proprietà del modulo Condizione. Hotfix per CQ-4247909
* UX della finestra di dialogo &quot;Annulla ereditarietà&quot; quando l&#39;utente ridispone un oggetto nel canale Web deve essere migliorata. Hotfix per CQ-4241076
* I dati nella lettera corrispondente ai binding definiti in XDP non vengono compilati utilizzando l&#39;URL della lettera diretta. Hotfix per CQ-4245833
* (Problema di cache) La sincronizzazione del canale Web non riflette le modifiche apportate ai frammenti di layout, al frammento di testo del canale di stampa. Hotfix per CQ-4251460
* Impossibile aggiornare il frammento di layout e le proprietà DD. Hotfix per CQ-4247830
* (CCR) Il ricaricamento della bozza non riesce a causa dell&#39;analisi XML. Hotfix per CQ-4250950
* (Editor IC) Il pulsante &quot;Edit Fragment&quot; (Modifica frammento) deve essere più individuabile. Hotfix per CQ-4244694
* (XDP) All&#39;aggiunta di un frammento di layout nel nuovo sottomodulo creato viene visualizzata una schermata vuota. Hotfix per CQ-4248810
* Errore di test di DocumentFragment-master-DeployWithServerSideTest. Hotfix per CQ-4245496
* Variabile del modulo di testo Istanza duplicata nel modulo Condizione. Hotfix per CQ-4252128
* L&#39;URL di anteprima PDF non mostra i rapporti sulle transazioni al momento della pubblicazione. Hotfix per CQ-4246158
* Problemi correlati alla sincronizzazione IC con Stampa canale su canale Web. Hotfix per CQ-4251505
* Pulizia codice EXM: Rimuovere LocalFunctionMapper. Hotfix per CQ-4243265
* Per correggere il tipo di risorsa TableHeader del componente tabella webChannel di IC. Hotfix per CQ-4251821
* (Editor IC) Problemi di usabilità. Hotfix per CQ-4241081
* Il sottomodulo canale di stampa non mostra la funzionalità di inserimento. Hotfix per CQ-4252994
* Mantieni le modifiche sincronizzate non riesce dopo la rimozione del nodo FDM o del segnaposto della variabile. Hotfix per CQ-4253178
* (Editor modello) Il modello di base mostra le aree di rilascio aggiuntive del trascinamento di intestazione e piè di pagina e gli sfarfalli dello schermo all&#39;apertura del canale Web. Hotfix per CQ-4253323
* I componenti generati automaticamente non vengono evidenziati quando si seleziona dalla struttura Contenuto. Hotfix per CQ-4246178

**Servizi basati su documenti**

* (Form Service) OSGI non supporta XFAF. NPR-25181, Hotfix per CQ-4251313
* I caratteri nell&#39;intestazione del file PDF assemblato stanno diventando illeggibili. NPR-25113: Hotfix per CQ-4244682

**Moduli adattivi**

* Invia azione come Invia posta genera un’eccezione con i campi CC/BC vuoti. NPR-25019: Hotfix per CQ-4243039
* Impossibile utilizzare il componente Modulo AEM OOOTB a causa di query inefficienti. NPR-25065: Hotfix per CQ-4247256
* Rimuovere sling:orderBefore dai nodi di dialogo di guideImageChoiceComponent. Hotfix per CQ-4245013
* (Selettore data) Il pattern di modifica non supporta due tipi di pattern di marca temporale. Hotfix per CQ-4237982
* Invio di un’azione mediante l’uso di &quot;Flusso di lavoro moduli&quot; problemi di authoring classici. Hotfix per CQ-4236981
* (Canale Web) Il grafico IC deve ereditare la proprietà colspan dal grafico AF. Hotfix per CQ-4252143

**Integrazione con il back-end**

* (richieste SOAP) I decimali principali (più di 6 cifre) sono rappresentati in notazione esponenziale e ciò genera un errore di convalida. NPR-25283: Hotfix per CQ-4248100
* Convalida non corretta dei parametri facoltativi definiti nei tipi complessi. NPR-25070: Hotfix per CQ-4247107
* Aggiunta la possibilità per l&#39;utente di utilizzare lo stesso file WSDL per più servizi. NPR-24604, Hotfix per CQ-4247756
* FDM visualizza l&#39;ordine dei parametri nelle chiamate SOAP. NPR-25069, Hotfix per CQ-4247180
* FDM unisce le entità (in List/Array) nella richiesta SOAP. NPR-25284: Hotfix per CQ-4248375

**Programma di installazione di JEE per Forms**

**Servizio PDFG**

* La funzione di creazione/modifica delle impostazioni di protezione non funziona. NPR-24769: Hotfix per CQ-4246927
* Ottimizzate i PDF rimuovendo selettivamente i font tramite una singola chiamata API. NPR-23287

**Servizi basati su documenti**

* Output Service non fornisce i tag corretti per l&#39;accesso facilitato a Reader. NPR-24438, NPR-24439, NPR-24440, NPR-24441: Hotfix per CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Sicurezza dei documenti**

* Problema con la creazione dei criteri tramite Document Security. NPR-25586, NPR-25547: Hotfix per CQ-4247086

**Forms - JEE di base**

* Processi eseguiti come account di contesto di sistema a intervalli intermittenti. NPR-25289, NPR-25313: Hotfix per CQ-4249331
* AEM Forms JEE è influenzato dall’avviso di sicurezza relativo ai binding dei dati Apache Struts e Jackson. NPR-25628: Hotfix per CQ-4242891
* Il processo punto iniziale e-mail non funziona. NPR-25253: Hotfix per CQ-4248518

**Feature Pack inclusi**

**Assets**

* È stata aggiunta [l’integrazione con Adobe Stock](/help/assets/aem-assets-adobe-stock.md) per consentire agli utenti di effettuare ricerche, visualizzare in anteprima, salvare e ottenere la licenza per le risorse Adobe Stock direttamente dall’interfaccia utente di AEM. Per informazioni dettagliate, consultate [Utilizzo di risorse Adobe Stock con risorse]AEM (https://helpx.adobe.com/experience-manager/kt/assets/using/stock-assets-feature-video-use.html). NPR-15779: Hotfix per CQ-30857
* È stato aggiunto il supporto per il metaschema condizionale dinamico. For more information, see [Cascading Metadata](/help/assets/cascading-metadata.md). NPR-25189: Hotfix per CQ-4237413
* Opzione &quot;Download risorsa&quot; attivata nei frammenti di contenuto. For more information, see [Asset Reports](/help/assets/asset-reports.md). NPR-25186: Hotfix per CQ-4237410
* Possibilità di impostare uno schema di metadati per le cartelle di risorse. Per ulteriori informazioni, consultate Schema [metadati](/help/assets/folder-metadata-schema.md) cartella e fate riferimento alle impostazioni [di](#configuration-settings-required-for-npr) configurazione post-installazione di AEM 6.4.2.0. NPR-21268: Hotfix per CQ-4221574

**Sites**

* Consente di modificare un frammento di contenuto senza eliminare le autorizzazioni. Per ulteriori informazioni, vedere [Personalizzazione ed estensione dei frammenti](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/customizing-content-fragments.html#AssetPermissions)di contenuto. NPR-25793: Hotfix per CQ-4248750
* Aggiunta la possibilità di annotare frammenti di contenuto. For more information, see [Variations-Authoring Fragments](https://helpx.adobe.com/experience-manager/6-4/assets/using/content-fragments-variations.html#AnnotatingaContentFragment). NPR-25188: Hotfix per CQ-4235336
* Gestione versioni: Confronta i frammenti di contenuto affiancati. Per ulteriori informazioni, vedere [Gestione dei frammenti](https://helpx.adobe.com/experience-manager/6-4/assets/using/content-fragments-managing.html#ComparingFragmentVersions)di contenuto. NPR-25187: Hotfix per CQ-4237412
* Miglioramenti dell’Editor immagini riportati su AEM 6.4.2.0. Per ulteriori informazioni, consultate Editor [](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/image-editor.html)immagini. NPR-24467

**Pacchetti OSGI e pacchetti di contenuti inclusi**

Elenco dei bundle OSGi inclusi in AEM 6.4.2.0

[Ottieni file](assets/6.4.2.0_bundle-list.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.2.0

[Ottieni file](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

AEM 6.4.1.0 è un aggiornamento importante che include correzioni suggerite dai clienti e miglioramenti a prestazioni, stabilità sicurezza disponibili dal rilascio di AEM 6.4 ad aprile 2018.

AEM 6.4.1.0 può essere installato su AEM 6.4 GA. Alcuni degli elementi di rilievo del service pack sono:

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.3.
* Sono Stati Introdotti Smart Tags Avanzati.
* Correzioni nel selettore progettazione, nel selettore tag (cambiare la VM di origine e la VM di destinazione in auto).
* È stato aggiunto il supporto per typeHint per salvare i valori come stringa.
* È stato aggiunto il supporto per SMTP su TLS in Mail Service.
* Correzione per la gestione dei proxy per l’inoltro HTTP in DMS7.
* Effettuate l&#39;aggiornamento a /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js versione 1.3.
* Correzioni nei pacchetti DMHybrid Opt-OUT e Opt-IN.
* Correzioni in Smart Crop.
* Migrazione dei valori di configurazione OOTB alla nuova posizione (da /etc a /conf).
* Sono stati aggiunti profili colore alle impostazioni cliente sui server di distribuzione.
* Migrazione delle impostazioni del server immagini da /etc —&amp;gt; /conf.
* Aggiunto frammento di contenuto sorgente per la traduzione.
* È stato aggiunto il supporto ARIA a Stampa e StampaFinestra di dialogo.
* È stato aggiunto il supporto ARIA per la convalida dell&#39;e-mail.
* Correzioni di backport proattivo per platform.clientlibs.

**Assets**

* Il valore a discesa a cascata viene visualizzato vuoto alla riapertura della pagina delle proprietà della risorsa. NPR-23042: Hotfix per CQ-4238761
* I collegamenti condivisi sulla pagina mylinkshare e i collegamenti alla pagina non sono disponibili per l&#39;utente non amministratore NPR-23044: Hotfix per CQ-4239004
* Per evitare un’eccezione di puntatore Null nel flusso di lavoro di aggiornamento delle risorse DAM in 6.4.0. NPR-24134: Hotfix per CQ-4244972
* La pagina WCM pubblicata mostra le icone dei segnaposto per il punto di attivazione, file CSS mancanti con l&#39;errore 403 per i visualizzatori OOOTB. NPR-23041: Hotfix per CQ-4233716
* (Visualizzazione dettagli) La funzione Navigazione avanti/indietro lascia una sovrapposizione DIV nell’area di anteprima Rappresentazione dinamica che blocca l’accesso al visualizzatore. NPR-23043: Hotfix per CQ-4238499
* La rappresentazione immagine CMYK presenta una saturazione non corretta. NPR-23048: Hotfix per CQ-4235470
* L’estrazione di metadati XMP da parte di Scene7 ListInfoProvider richiede molte risorse. NPR-23754
* (consegna DAM) L&#39;inoltro HTTP non rispetta le impostazioni proxy HTTP. NPR-24002: Hotfix per CQ-4244140

**Sites**

* Quando rinominiamo la pagina mentre ci spostiamo, lo spostamento della pagina ha esito positivo ma la funzionalità di ridenominazione non funziona. NPR-22923: Hotfix per CQ-4235907
* Errore durante la pubblicazione di una pagina Live Copy che punta a una pagina di importazione in Adobe Campaigns. NPR-23053: Hotfix per CQ-4237164
* L’opzione Sposta/Rinomina nell’interfaccia classica non riesce con l’errore &quot;Si è verificato un errore durante lo spostamento della pagina&quot; e non è stata rinominata. NPR-23051: Hotfix per CQ-4235907
* Se si passa dalla visualizzazione a colonne alla visualizzazione a elenco, viene visualizzata una pagina vuota e viene attivata un&#39;eccezione di puntatore Null per le pagine con OffTime impostato e OnTime impostato come vuoto. NPR-22968, NPR-23052: Hotfix per CQ-4238940

**Commerce**

* Correggi caso di test Hobbes core non riuscito (modulo CQ/Commerce). Hotfix per CQ-4253494

**Vulnerabilità**

* L’integrazione con Salesforce è vulnerabile ad attacchi di tipo SSRF (Server Side Request Forgery). NPR-24289: Hotfix per CQ-4245277
* File SSRF (Server Side Request Forgery) e XSS (Cross-Site Scripting) in ReportingServicesProxyServlet. NPR-24657: Hotfix per CQ-4246880
* Cross-Site Scripting (XSS): Riflettete in commerce create atecatalogwizard.html/content. NPR-24642: Hotfix per CQ-4237017
* Vulnerabilità cross-site scripting (XSS) nei collegamenti di progetto di Interfaccia utente amministratore. NPR-23272: Hotfix per CQ-4241795

**WCM - Componenti Foundation**

* Se si apre il selettore Progettazione, viene generata un&#39;eccezione di puntatore null. NPR-23047: Hotfix per CQ-4238736

**Interfaccia utente**

* (Coral3 Datepicker) Aggiungete il supporto per typeHint per salvare i valori come &quot;String&quot;. NPR-23398: Hotfix per GRANITE-21194
* La traduzione internazionalizzazione non funziona a livello di lingua. NPR-22967, NPR-23046: Hotfix per Granite-21111
* Correzioni di granite.ui.commons proactive Backport. NPR-23537
* Supporto proattivo per granite.ui.content. NPR-23535
* Correzioni di granite.ui.coralui proattive. NPR-23538
* Impossibile rimuovere più utenti dal gruppo contemporaneamente. NPR-23846
* (OMEGA) Report &quot;Feature&quot; solo in inglese. NPR-23989: Hotfix per GRANITE-21231
* (Importazione progettazione) L&#39;importazione di una pagina non importa il js, css. NPR-25203: Hotfix per GRANITE-22236

**Integrazione**

* ResourceResolver non chiuso in com.day.cq.analytics.sitecatalyst. NPR-22340: Hotfix per CQ-4236515
* TargetContentImpl rallenta l’esecuzione di AEM durante le query con tempi di esecuzione lunghi. NPR-22359: Hotfix per CQ-4236907
* Il motore target (mbox.js, at.js) non utilizza URL gestiti e utilizza URL contenenti due punti, che potrebbero non riuscire con determinate implementazioni. NPR-22434: Hotfix per CQ-4237854
* In modalità Target gli autori possono modificare un componente ereditato dalla blueprint senza annullare l’ereditarietà. NPR-22865: Hotfix per CQ-4237907
* (Personalizzazione) Le icone sono disattivate quando si passa alla vista a schede. NPR-23373, NPR-23374: Hotfix per CQ-4240018, CQ-4240019
* (Personalizzazione) La console Audience non mostra i tipi di cartelle nt:folder. NPR-23375: Hotfix per CQ-4242293
* Quando un componente è destinato all’istanza di pubblicazione, lo sfarfallio visualizza l’esperienza predefinita prima di quella di destinazione. NPR-23415: Hotfix per CQ-4242038
* (Console Adobe IMS) La configurazione del servizio AccessTokenProvider OSGi viene visualizzata nuovamente dopo l’eliminazione. NPR-23520: Hotfix per CQ-4208250
* Impossibile eseguire la replica dei riferimenti di configurazione con la struttura di cartelle intermedia. NPR-23485: Hotfix per CQ-4242751
* (Personalizzazione) clientlib bloccata dal servlet proxy. NPR-23521: Hotfix per CQ-4240995
* (Console Adobe IMS) Le soluzioni Cloud registrate non vengono individuate nella procedura guidata di configurazione. NPR-23977: Hotfix per CQ-4244549
* Ciclo infinito quando si carica il contenuto di destinazione su pagine senza estensione HTML. NPR-23522: Hotfix per CQ-4223600
* Attivazione non riuscita per una pagina con riferimenti di configurazione di Gestione tag dinamica ereditata. NPR-23485: Hotfix per CQ-4242751

**Platform**

* (Interfaccia classica)(Interfaccia touch) Il selettore di tag non viene visualizzato e genera un’eccezione quando si tenta di individuare i tag tramite un predicato di tag nello schema di ricerca delle risorse. NPR-23049: Hotfix per CQ-4239371
* (Interfaccia classica) I componenti che utilizzano xtype=tags restituiscono null e non possono essere selezionati dall’ennesimo elenco di tag. NPR-23050: Hotfix per CQ-4239937
* (Marchio) La finestra di dialogo di consenso menziona Adobe Marketing Cloud invece di Adobe Experience Cloud. NPR-23210: Hotfix per CQ-4237799
* L’opzione Filtro rallenta AEM dopo l’aggiornamento da 6.3 a 6.4. NPR-23260: Hotfix per CQ-4239847 (da verificare)
* Correzioni proattive Backport per granite.omnisearch.core. NPR-23536
* Correzioni di backport proattivo per platform.clientlibs. NPR-23569
* L&#39;ereditarietà di configurazione del servizio cloud non è riuscita durante la modifica di altre proprietà di pagina. NPR-23216: Hotfix per CQ-4239782
* Attivazione del supporto STARTTLS in Day CQ Mail Service. NPR-23941: Hotfix per CQ-4240397

**Progetti**

* (Frammento di contenuto) La copia della lingua per la risorsa incorporata non viene creata mentre la risorsa inglese viene aggiunta alla traduzione. Hotfix per CQ-4243477
* Il menu a discesa di configurazione msft mostra la configurazione da /libs(6.4 configs) invece di /etc(6.3 configs) in modalità legacy. Hotfix per CQ-4243475
* Promuovere ed eliminare automaticamente gli avvii di traduzione nei progetti di traduzione. Hotfix per CQ-4243474
* I frammenti di contenuto all&#39;interno dei siti non vengono convertiti. Hotfix per CQ-4243482, CQ-4243483, CQ-4245687
* Errore del server all&#39;apertura del filtro di ricerca del processo di traduzione. Hotfix per CQ-4236813
* Il menu a discesa Configurazione credenziali è vuoto anche dopo che tif è presente in /conf/we-retail. Hotfix per CQ-4236315
* Apri KPI progetto: riduzione delle prestazioni mano a mano che vengono creati più progetti. NPR-23840: Hotfix per CQ-4238392
* Workflow Starter non è in grado di accettare il valore TypeHint di String. NPR-23863: Hotfix per CQ-4238356

**Community**

* vulnerabilità di sicurezza nella versione 1.0 di Handlebars. NPR-23636: Hotfix per CQ-4243055
* Consenti blocco di messaggi contrassegnati non funziona. NPR-23867: Hotfix per CQ-4243962
* Il valore predefinito non viene visualizzato sul pulsante di ordinamento nel componente forum. NPR-23882: Hotfix per CQ-4243375
* Problemi relativi alla distribuzione di messaggi dai siti community ai gruppi. NPR-23935

**Flusso di lavoro**

* Il servizio di notifica e-mail del flusso di lavoro del giorno CQ attiva un messaggio e-mail per il nodo Mongo per le notifiche WorkflowCompleted e WorkflowAborted. NPR-22515: Hotfix per CQ-4238172
* L&#39;esecuzione del flusso di lavoro della risorsa di aggiornamento DAM genera un&#39;eccezione NullPointerException. NPR-23010: Hotfix per GRANITE-21096
* Il passaggio Processo flusso di lavoro non visualizza gli script da /etc/workflow/scripts. NPR-23263: Hotfix per GRANITE-20775
* Workflow Dynamic Participant Step non visualizza gli script da /apps/workflow/script. NPR-23464: Hotfix per GRANITE-21276
* Impossibile modificare un flusso di lavoro dopo averlo modificato una volta. NPR-23742: Hotfix per CQ-4238526
* (Interfaccia classica) Dopo aver modificato gli avviatori dei flussi di lavoro, le condizioni scompaiono e i flussi di lavoro vengono avviati senza condizioni. NPR-23835: Hotfix per CQ-4239153
* Inbox progetto: il passaggio alla visualizzazione calendario mostra il contenuto della inbox principale. NPR-23947: Hotfix per CQ-4241236
* Dovete esporre i dettagli del payload nel bundle in modo che il componente HTL possa visualizzare il valore nella vista a elenco. NPR-23948: Hotfix per CQ-4240953
* Impossibile memorizzare i dati della finestra di dialogo nel passaggio Partecipante alla finestra di dialogo. NPR-23965: Hotfix per CQ-4234123
* (Interfaccia touch) Quando si salva un modello di workflow, il pulsante &#39;Sincronizza&#39; diventa &#39;Sincronizzato&#39; e si verifica un errore ortografico. Hotfix per CQ-4244843
* Inbox progetto: il passaggio alla visualizzazione calendario mostra il contenuto della inbox principale. Hotfix per CQ-4244436
* Impossibile selezionare Finestre di dialogo nel passaggio Partecipante finestra di dialogo. Hotfix per CQ-4244532
* Correzioni proattive Backport per granite.omnisearch.core. NPR-23536
* Problema nell&#39;app di Mobile Workspace 6.4 con attività condivisa. NPR-26383

**WCM - Traduzione**

* (Pannello di riferimento) I processi di traduzione non vengono eseguiti durante la creazione del progetto. Hotfix per CQ-4245327

**WCM - MSM**

* (MSM) Miglioramento delle prestazioni di rollout. Hotfix per CQ-4231488
* (MSM) Intervallo di tempo vuoto nell&#39;ascolto degli eventi tra la gestione degli eventi in corso e quella degli eventi. Hotfix per CQ-4227766

**Schermi**

* La pagina dello schermo non riesce con un errore a causa di dipendenze mancanti per screens-core-pkg:1.4.42. Hotfix per CQ-4245918

**Progetti - Traduzione**

* (Frammento di contenuto) La copia della lingua per la risorsa incorporata non viene creata mentre la risorsa inglese viene aggiunta alla traduzione. Hotfix per CQ-4243477
* Il menu a discesa di configurazione msft mostra la configurazione da /libs(6.4 configs) invece di /etc(6.3 configs) in modalità legacy. Hotfix per CQ-4243475
* Promuovere ed eliminare automaticamente gli avvii di traduzione nei progetti di traduzione. Hotfix per CQ-4243474
* I frammenti di contenuto all&#39;interno dei siti non vengono convertiti. Hotfix per CQ-4243482, CQ-4243483, CQ-4245687
* Errore del server all&#39;apertura del filtro di ricerca del processo di traduzione. Hotfix per CQ-4236813
* Il menu a discesa Configurazione credenziali è vuoto anche dopo che tif è presente in /conf/we-retail. Hotfix per CQ-4236315

**Gestione dei frammenti di contenuto**

* Quando si elimina un componente, i file di registro vengono riempiti con tracce di stack. Hotfix per CQ-4242315

**DAM - Generale**

* La chiusura della visualizzazione Dettagli di una risorsa torna alla pagina dei risultati di ricerca non corretta. Hotfix per CQ-4240960
* (Camera Raw) Opzione di regolazione immagine mancante. Hotfix per CQ-4246121
* IndexOutOfBoundException: Report di modifica delle risorse OOTB. Hotfix per CQ-4239744
* Rimuovete il punteggio di attendibilità dal CSV dei report. Hotfix per CQ-4241491
* Invio e-mail condivisione collegamento interrotto per il mittente non &quot;admin&quot;. Hotfix per CQ-4240357
* Correzione degli errori IT. Hotfix per CQ-4249891

**DAM - Portale marchio**

* Le proprietà della risorsa elencano solo 3 proprietà nella prima scheda, mentre tutte le schede sembrano vuote. Hotfix per CQ-4242503
* Il tipo di file e i predicati delle dimensioni del file non sono disponibili nel modulo di ricerca pubblicato. Hotfix per CQ-4242026
* La ricerca nel predicato della directory deve essere filtrata/non visualizzata nei filtri di ricerca. Hotfix per CQ-4241386
* Dopo l’annullamento della pubblicazione, la ricerca predefinita da dovrebbe esistere. Hotfix per CQ-4241383, CQ-4241113
* Il gesto di pubblicazione sul portale del marchio non funziona per i predefiniti per immagini. Hotfix per CQ-4241074
* Publish to Brand Portal non funziona per le raccolte. Hotfix per CQ-4241122, CQ-4246558

**DAM - Client DM**

* L’aggiornamento alla versione 6.4 rimuove i profili di codifica video creati in precedenza. Hotfix per CQ-4244067
* L’attributo Testo Alt è danneggiato nel componente Contenuti multimediali dinamici. Hotfix per CQ-4244081
* (DMS7) La modifica dei set remoti in AEM non viene sovrascritta in Scene7. Hotfix per CQ-4243430
* Verifica della build 6.4 SP1 su DM Hybrid. Hotfix per CQ-4244623
* (DMS7-UA) Quando fate clic sul pulsante Incorpora per una risorsa video pubblicata, non viene visualizzato nulla. La finestra di dialogo Incorpora deve essere visualizzata con codice HTML. Hotfix per CQ-4245237
* (DM ibrido) Copia URL per risorse video pubblicate o set di file multimediali diversi ottiene &quot;[oggetto[]oggetto&quot; nella finestra di dialogo URL. Hotfix per CQ-4245236, CQ-4245451
* (DMHybrid) La pagina Visualizzazione dettagli video non contiene l’anteprima della visualizzazione della risorsa video e invia un messaggio di errore alla console. Hotfix per CQ-4244320
* Codifica automatica S7 del contenuto We.retail. Hotfix per CQ-4242253
* I predefiniti di elaborazione video pre-aggiornamento non possono presentare un nuovo predefinito di codifica video aggiunto né modificare i predefiniti di codifica esistenti. Hotfix per CQ-4240407
* I predefiniti per immagini pre-aggiornamento sono visualizzati come Non pubblicato nella pagina Rendering e non generano URL. Hotfix per CQ-4240406
* (CSS) Le risorse vengono visualizzate, ma i visualizzatori utilizzati sono predefiniti e non i visualizzatori OOOTB. Hotfix per CQ-4239839
* Disabilitata la pulizia del passo appesa esecuzione manuale e utilizzata delle classi di corallo private. Hotfix per CQ-4239729
* Il visualizzatore di immagini sta generando un errore e non visualizza il ritaglio avanzato corretto. Hotfix per CQ-4237564
* Il predefinito precedente in /etc sembra essere danneggiato e non migrato nella posizione in /conf al momento del salvataggio. Hotfix per CQ-4237416
* Regressione in OOB VideoViewer 5.8.x: il visualizzatore espande iframe a destra, quindi interrompe il layout della pagina. Hotfix per CQ-4235465
* (DMS7) Per le immagini che non sono state pubblicate sono attivi i pulsanti URL di rappresentazione Ritaglio avanzato e Incorpora. Hotfix per CQ-4233696
* (DMHybrid) Ripristina la precedente funzione di ritaglio/rotazione. Hotfix per CQ-4239489
* Quando si visualizza l&#39;anteprima di un video nella vista a schede, il pulsante di riproduzione non viene attivato per essere messo in pausa. Hotfix per CQ-4238592
* Quando si esegue un aggiornamento di consenso, la configurazione di YouTube non viene spostata/copiata dalla posizione precedente alla nuova posizione. Hotfix per CQ-4238590
* DropDue profili di elaborazione video OOTB AVS sono elencati nelle proprietà della cartella e solo uno contiene codifiche definite. Hotfix per CQ-4238096
* (DMS7) Smart Crop: Visualizzazione dettagli: Il pulsante URL è etichettato Pulsante Copia per le rappresentazioni. Hotfix per CQ-4237804
* La pagina di elenco dei predefiniti per visualizzatori rimane vuota anche dopo l’esecuzione dei comandi curl. Hotfix per CQ-4243246
* Disattivato pulizia passo appendere esecuzione manuale e uso di classi di corallo privato. Hotfix per CQ-4239729
* La pagina Dettagli rapporto video non mostra la risorsa video. Hotfix per CQ-4246208

**DAM - Servizi DM**

* Configurazione cloud (DMS7): Impossibile sincronizzare il nuovo contenuto con Scene7 dopo l’aggiornamento a SP1. Hotfix per CQ-4244437
* (DMHybrid) I profili colore e le impostazioni catalogo non vengono registrati in una chiamata debug_info=catalogo. Hotfix per CQ-4242346
* Aggiungete profili colore alle impostazioni cliente sui server di distribuzione. Hotfix per CQ-4241818, CQ-4241819
* (DMHybrid) Dopo 6.3 &amp;gt; 6.4, le impostazioni del catalogo vengono spostate nel nodo errato. Hotfix per CQ-4239974, CQ-4239975
* (DMHybrid) lo script push viewerpresets non crea i nodi necessari per modificare le impostazioni del catalogo. Hotfix per CQ-4240076
* Quando si utilizza la selezione a discesa &quot;Formato&quot; e si selezionano i formati PNG o JPG, il file scaricato viene mostrato come troppo saturo e più scuro della risorsa originale. Hotfix per CQ-4240073
* (DMS7) Rimuovere la mappatura del tipo MIME: image_x-eps. Hotfix per CQ-4240394
* (DMS7) I parametri di caricamento per lo sfondo della foratura non superano il file ipsApiService.log, pertanto non funzionano. Hotfix per CQ-4240686
* L’aggiornamento dei profili di elaborazione immagine creati in un’istanza da 6.3 a 6.4 interrompe la proprietà &quot;Tipo di ritaglio&quot;. Hotfix per CQ-4237739
* (Contenuti multimediali dinamici) Il caricamento di risorse regolari all’esterno della cartella smartritaglio non riesce. Hotfix per CQ-4237670
* Regolate il codice di riserva del profilo per il nome del profilo &quot;Codifica video adattiva&quot; su &quot;Adaptive_Video_Encoding&quot;. Hotfix per CQ-4237666
* I dati di EmbedXMP sono sempre impostati su “active” per il processo di generazione Ptiff. Hotfix per CQ-4234498
* La rappresentazione immagine CMYK presenta una saturazione non corretta. Hotfix per CQ-4235470
* Le impostazioni del server immagini non vengono replicate per la distribuzione mentre i registri di replica li contrassegnano correttamente. Hotfix per CQ-4239480, CQ-4239046
* (DMS7) Impossibile creare i set utilizzando riferimenti vecchi/nuovi alla configurazione cloud. Hotfix per CQ-4238078
* Il passaggio del flusso di lavoro di Scene7 legge solo Scene7 nel nome e nella descrizione, ma non specifica il passaggio del flusso di lavoro nel flusso di lavoro di aggiornamento DAM. Hotfix per CQ-4237865

**DAM - Tag avanzati**

* Sono Stati Introdotti Smart Tags Avanzati. NPR-21951

**Forms**

Le correzioni per AEM Forms vengono distribuite tramite pacchetti di componenti aggiuntivi e altri programmi di installazione delle patch forniti con la versione. Per informazioni dettagliate, consulta Versioni di AEM Forms.

Gli elementi di rilievo di AEM Forms sono:

* AEM Forms offre la possibilità [](https://helpx.adobe.com/experience-manager/6-4/forms/using/transaction-reports-overview.html) di tenere traccia e il conteggio delle transazioni come i moduli inviati, i documenti elaborati e i documenti sottoposti a rendering nella distribuzione di AEM Forms. Fornisce informazioni sull&#39;utilizzo dei prodotti e aiuta gli utenti aziendali a comprendere i volumi di elaborazione digitale.
* Supporto PDF/UA abilitato per i moduli XML.
* Aggiunta di allowProxy = true per Clientlib **aemfd.ccm.channel.contentpage**
* È stato aggiornato il codice per effettuare ricerche avanzate nel titolo come contenuto anziché uguale.
* Aggiornamento alla nuova versione di Node Package Manager (NPM) su Continuous Integration Machine.

**Pacchetto di componenti aggiuntivi per Forms**

**Integrazione con il back-end**

* Viene generato un errore quando si fornisce null come valore a un campo facoltativo. NPR-24397
* La chiamata WSDL non riesce quando l&#39;elemento ha uno spazio nomi diverso dallo spazio nomi globale. NPR-24281
* (WSDL FDM) Ottenimento di DermisException: I dati dell&#39;elenco esclusi nel caso di array di tipi di proprietà. NPR-24265
* (WSDL FDM) Ottenimento di DermisException: java.lang.Exception: createSOAPParam: Param non validi. NPR-24264
* (FDM Client SDK) Impossibile eseguire il test del preprocessore e dell&#39;azione di invio personalizzata prima/dopo. Hotfix per CQ-4238469
* Correzioni per problemi Javadoc in Dermis. Hotfix per CQ-4244250
* È stato migliorato l&#39;input in WSDL (Web Services Description Language). Hotfix per CQ-4244133
* Il test di autenticazione di base per WSDL genera un errore diverso per la stessa configurazione in AEM 6.3 e AEM 6.4. Hotfix per CQ-4244132
* Richiesta di includere ValueUtil in client-sdk e javadocs. Hotfix per CQ-4242803
* (Configurazione cloud FDM) Impossibile configurare l&#39;autenticazione basata su SOAP dalla configurazione cloud. Hotfix per CQ-4238462
* Dermis - Aggiungi pacchetti mancanti in Javadocs. Hotfix per CQ-4242815
* WSDLInvokerParams da includere nell&#39;SDK client del componente aggiuntivo di Forms. NPR-23381: Hotfix per CQ-4240233

**Moduli adattivi**

* La rappresentazione del documento (IC) deve essere registrata come transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4245333
* Durante l&#39;esecuzione di UAT5, nel file pdf generato nella fase di verifica manca una voce. Hotfix per CQ-4243184
* Test case for deep copy of guideContext. Hotfix per CQ-4242924
* Campo del tipo di prova mancante durante l&#39;esecuzione dell&#39;UAT3 sul server aggiornato più recente. Hotfix per CQ-4243120
* Nel server aggiornato, nel modulo inviato mancano i valori Stato/Provincia/Regione e Paese presenti nel server di pre-aggiornamento. Hotfix per CQ-4241444
* (ExpressionEditor) Errore durante la navigazione alla fase Verifica durante l&#39;invio del modulo. Hotfix per CQ-4241384
* I valori mancano nella fase di verifica nella fase di pre-aggiornamento e nel server aggiornato per il modulo inviato. Hotfix per CQ-4241896
* Il pulsante Chiudi e Salva nella parte inferiore della pagina non funziona. Hotfix per CQ-4240112
* Numero di contatto mancante nella configurazione aggiornata. Hotfix per CQ-4239870
* Nella `ACTION TAKEN` sezione della scheda Tipo di controversia, &quot;Documenti aggiuntivi per supportare la mia richiesta&quot; contiene un campo aggiuntivo Tipo prova salvato &quot;in esso. Hotfix per CQ-4239873
* Errore &quot;Errore in getDataAPI&quot; rilevato nel passaggio verifyPdf. Hotfix per CQ-4239865
* Errori nei registri di migrazione per l’istanza di creazione e pubblicazione. Hotfix per CQ-4239365
* Errori nei registri di migrazione per l’istanza di creazione e pubblicazione. Hotfix per CQ-4239635
* Errore di deserializzazione come &quot;Deserializzazione non consentita per la classe sun.util.Calendar.ZoneInfo&quot; nei registri degli errori dopo l&#39;invio di un modulo adattivo. Hotfix per CQ-4240419
* Il campo Stato non viene popolato nella rappresentazione del modulo Mobile. Hotfix per CQ-4240597
* Rimuovere dall&#39;elenco anti-pattern l&#39;uso di riferimento dei componenti nei modelli. Hotfix per CQ-4239217
* HTML5 Numeric Box impostato come Mobile o Decimale fornisce risultati di convalida diversi in browser diversi. NPR-23528: Hotfix per CQ-4244097
* (Caricamento immagine) L’immagine non viene visualizzata nell’anteprima DOR. Hotfix per CQ-4243178
* Il server JEE genera un errore durante il tentativo di invio del modulo adattivo con &quot;PDF per e-mail&quot; e &quot;Includi allegati&quot;. Hotfix per CQ-4239894
* Il grafico non viene stampato in fase di esecuzione utilizzando tabella/pannello. Hotfix per CQ-4240010
* L&#39;invio del modulo adattivo non funziona e non è stata apportata alcuna modifica al conteggio delle transazioni a causa di un errore di invio. Hotfix per CQ-4246125
* (Immagine selezionata) Le opzioni del documento del record non sono visibili. Hotfix per CQ-4236976
* L’interfaccia utente dell’editor modelli non è stabile. Hotfix per CQ-4241497
* Gli AF non vengono visualizzati utilizzando la scheda delle risorse del pannello laterale, mentre vengono visualizzati utilizzando l&#39;opzione Sfoglia per la finestra di dialogo delle proprietà del componente Modulo AEM. Hotfix per CQ-4236751
* L&#39;ID del flusso di lavoro generato per la conversione del modulo deve essere disponibile nel modulo adattivo generato. Hotfix per CQ-4240014
* Impossibile selezionare il modello per creare una pagina nei siti in Aggiornamento diretto: Livecycle al server 6.4. Hotfix per CQ-4241300

**Servizio assemblatore**

* Registrazione delle transazioni in Assembler Services. Hotfix per CQ-4245018, CQ-4245017, CQ-4245016.
* La transazione non viene segnalata quando si esegue la conversione PDF/A utilizzando DDX. Hotfix per CQ-4246039

**Forms Manager**

* Elenco pulsanti CREATE FM in ordine alfabetico. Hotfix per CQ-4242307

**Portale moduli**

* Le bozze salvate nel server di pre-aggiornamento non si aprono correttamente sul server aggiornato. Hotfix per CQ-4243303
* Aggiornamento della versione a 7.1 per adobe-formsmanager-core-module. Hotfix per CQ-4245753
* Le bozze salvate nel server di pre-aggiornamento non si aprono correttamente sul server aggiornato. Hotfix per CQ-4243303
* Gli scenari di allegati vengono interrotti al momento della sostituzione, aggiunta o rimozione di allegati in una nuova istanza/stessa istanza di bozza. Hotfix per CQ-4243165
* Il numero di bozze recuperate dalla query al database è superiore al numero di bozze presenti nel portale. Hotfix per CQ-4241489
* I moduli inviati nel server di pre-aggiornamento non sono presenti nel server aggiornato. Hotfix per CQ-4241490
* Il modulo visualizzato nell’interfaccia utente nella scheda degli invii è nello stato Non inviato nonostante il messaggio di invio sia stato corretto. Hotfix per CQ-4241487
* guideContext deve essere formato copiando in profondità i campi come guideContext contiene customPropertyMap che è un oggetto. Hotfix per CQ-4240126
* Errore durante il tentativo di salvare un modulo. Hotfix per CQ-4240763
* La voce relativa ai moduli salvati e inviati viene compilata in formato crx/de nonostante la configurazione DB sia specificata in Configurazione bozza e invio di Forms Portal. Hotfix per CQ-4240726
* (Search &amp; Lister) Il valore fisso del titolo di ricerca avanzato deve funzionare come contiene anziché come uguale. Hotfix per CQ-4245499

**Moduli mobili**

* Il campo data si sovrappone nei moduli per dispositivi mobili. Hotfix per CQ-4242256
* L&#39;invio del modulo per Mobile Forms deve essere registrato come transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4246166
* L&#39;invio del modulo in FormSet deve essere registrato come una transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4246165

**App AEM Forms**

* (App Windows) Impossibile eseguire il rendering del modulo. Hotfix per CQ-4238005

**Flusso di lavoro OSGI**

* Registrazione delle transazioni nell&#39;attività Assegna flusso di lavoro. Hotfix per CQ-4244440
* (Passaggio FDM) Impossibile utilizzare i valori dai metadati del flusso di lavoro quando viene inserito un passaggio Assegna attività tra il passaggio del processo e il passaggio fdm. Hotfix per CQ-4241472
* La delega dell&#39;attività di assegnazione non funziona in Integrazione moduli nei flussi di lavoro OSGI. NPR-23709: Hotfix per CQ-4243700
* (Editor modello flusso di lavoro) Alcuni modelli di flussi di lavoro non possono essere modificati tramite l&#39;editor modelli WF ClassicUI. Hotfix per CQ-4241151

**Documento multi-canale**

* Il campo Data in Template si sovrappone al sottomodulo nella creazione IC. Hotfix per CQ-4240110
* L’intestazione non deve essere eliminata o spostata verso l’alto o il basso nell’authoring dei canali Web IC. Hotfix per CQ-4243358
* (Editor IC) Le righe predefinite devono essere impostate su 1 per i componenti Tabella. Hotfix per CQ-4244848
* Area di destinazione per restare visibile anche dopo che il contenuto è stato trascinato e rilasciato. Hotfix per CQ-4244534
* Il canale Web non riconosce lo spazio delle schede nei frammenti di documento di testo. Hotfix per CQ-4244481
* (Canale di stampa) La rappresentazione del documento (IC) deve essere registrata come transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4245335
* (Canale Web) La rappresentazione del documento (IC) deve essere registrata come transazione utilizzando il servizio di registrazione delle transazioni. Hotfix per CQ-4245334
* La ricerca nel contenitore del documento o nell’albero del modello dati deve essere unificata alla ricerca nel filtro delle risorse. Hotfix per CQ-4242305
* (Frammento documento) La proprietà indentation fa rientrare il testo in base al numero di unità che non è possibile comprendere. Hotfix per CQ-4241082, CQ-4240643
* (Editor IC) L&#39;icona Modifica frammento nella sezione del frammento di documento elencata nella scheda Risorse non è facilmente individuabile e comprensibile. Hotfix per CQ-4241047
* Consenti accesso anonimo alla libreria client IC Anonymous non accessibile. Hotfix per CQ-4245588
* (Canale Web) I dati non vengono risolti in alcuna tabella nell’anteprima Web e vengono visualizzati come vuoti. Hotfix per CQ-4244476
* Le intestazioni delle tabelle sono visualizzate come variabili nel canale Web durante la generazione automatica. Hotfix per CQ-4244242
* (Editor IC) Il contenuto di un frammento di documento utilizzato in un IC deve essere ridimensionato automaticamente per adattarsi alla larghezza dell&#39;area di destinazione. Hotfix per CQ-4244094
* Il nome del canale mostrato nella parte superiore centrale deve essere coerente con il titolo IC per WEB / PRINT. Hotfix per CQ-4242498
* Editor di testo Il pannello degli oggetti dati dovrebbe elencare solo le entità di livello principale, Hotfix per CQ-4244121
* Il nome predefinito non viene assegnato quando si aggiunge un nuovo componente nell’editor. Hotfix per CQ-4244691
* Aggiunta della configurazione Colspan in tutti i componenti del canale Web. Hotfix per CQ-4244946
* La proprietà Larghezza tabella frammento di layout non viene ripristinata e rispettata nel canale di stampa Lettera o Comunicazione cliente. Hotfix per CQ-4241574

**Gestione della corrispondenza**

* Le didascalie rimosse dal modello di lettera dopo la modifica di una risorsa di testo contenente segnaposto. NPR-24196
* Il file XDP, quando caricato e utilizzato come layout per i modelli Lettera, non visualizza l&#39;anteprima o non modifica i modelli. NPR-24143: Hotfix per CQ-4244407
* La selezione dell&#39;assegnazione è selezionata per impostazione predefinita nel frammento elenco. Hotfix per CQ-4240097
* Editor condizione: per impostazione predefinita, la valutazione di più risultati deve essere abilitata. Hotfix per CQ-4240096
* Immagine eliminata da Elenco mostra ancora l’immagine nell’anteprima. Hotfix per CQ-4239909
* La regola impostata nel modulo condizione è impostata su &quot;Default&quot; per tutti i moduli. Hotfix per CQ-4239878
* Creazione del dizionario dati non riuscita con errore &quot;Eccezione JCR sconosciuta&quot;. Hotfix per CQ-4244122
* Spazio vuoto in JavaDocs 6.3 di contenuto. Hotfix per CQ-4213586

**Programma di installazione di JEE per Forms**

**Core**

* (Area di lavoro HTML) Mancano i dettagli di tracciamento per le applicazioni con il simbolo delle parentesi nel nome. NPR-23402

**Servizio PDFG**

* Registrazione delle transazioni nei servizi PDFG. Hotfix per CQ-4244951, CQ-4244586
* Riduzione dei PDF mediante l&#39;annullamento selettivo dei font tramite una singola chiamata API. NPR-23287
* Problema di aggiornamento delle configurazioni PDFG con l’aggiornamento di AEM. Hotfix per CQ-4241176
* Registrazione delle transazioni in PDFUtility Service. Hotfix per CQ-4245014

**Gestione processi**

* (Area di lavoro HTML) I punti di partenza del processo non sono ordinati in ordine alfanumerico. Hotfix per CQ-4239629
* (area di lavoro HTML) Prepara la chiamata dati in arrivo due volte quando la bozza viene aperta la prima volta. Hotfix per CQ-4243280
* (Area di lavoro HTML) Il processo Prepara dati viene attivato durante la chiusura di un modulo. Hotfix per CQ-4239456
* Lo spazio di lavoro si blocca quando viene attraversato tra due attività. Hotfix per CQ-4237125

**Workbench**

* Gestisci profilo azione Il processo di preparazione dei dati non riesce quando la configurazione del processo di rendering predefinito è impostata su HTML. Hotfix per CQ-4244292

**Forms Designer**

* Aggiunta del supporto per PDF/UA ai moduli XML generati tramite Designer e il servizio Output. NPR-23022
* Ai collegamenti ipertestuali inline definiti in Designer non vengono assegnati tag né testo alternativo se vengono salvati in formato PDF da Designer. NPR-23023

**Feature Pack inclusi**

**Assets**

* Aggiunta la funzionalità per Smart Tag avanzati. Per ulteriori informazioni, consultate Tag [avanzati](https://helpx.adobe.com/experience-manager/6-4/assets/using/enhanced-smart-tags.html)avanzati. NPR-21951: Hotfix per CQ-4234883
* In InDesign sono stati introdotti i riferimenti a Risorse AEM. Per ulteriori informazioni, consultate Riferimenti a Risorse [AEM in InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sites**

* (Authoring delle pagine) Miglioramenti all’editor di immagini.  Per ulteriori informazioni, consultate Editor [](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/image-editor.html)immagini. NPR-24267: Hotfix per CQ-4245502

**Pacchetti OSGI e pacchetti di contenuti inclusi**

Il testo seguente documenta l’elenco dei pacchetti OSGI e dei pacchetti di contenuti inclusi nel CFP.

Elenco dei bundle OSGi inclusi in AEM 6.4.1.0

[Ottieni file](assets/6_4_1_0_bundle-list.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.1.0

[Ottieni file](assets/6_4_1_0_content-package-list.txt)

### Install 6.4.7.0 {#install}

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
>Per i clienti con Feature Pack installati in AEM 6.4. I Feature Pack opzionali forniti da Adobe dipendono dalla versione release e dal service pack. Se avete installato Feature Pack, contattate il team di assistenza clienti di AEM per verificare la compatibilità di questi pacchetti con questo service pack per AEM 6.4.

* AEM 6.4.7.0 requires AEM 6.4. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* Il download del Service Pack è disponibile in Condivisione pacchetti Adobe, a cui puoi accedere direttamente dall’istanza di AEM 6.4.
* In una distribuzione con MongoDB e più istanze, installa AEM 6.4.7.0 in una delle istanze Autore tramite Gestione pacchetti.
* Prima di installare il Service Pack, assicurati di disporre di uno snapshot o di un nuovo backup dell’istanza AEM.
* Riavvia l’istanza prima dell’installazione. Anche se ciò è necessario solo quando l&#39;istanza è ancora in modalità di aggiornamento (e questo accade quando l&#39;istanza è stata appena aggiornata da una versione precedente), si consiglia generalmente se l&#39;istanza è in esecuzione per un periodo di tempo più lungo.

>[!NOTE]
>
>Adobe sconsiglia la rimozione o la disinstallazione del pacchetto AEM 6.4.7.0.

### Installare il Service Pack tramite Condivisione pacchetti {#install-the-service-pack-via-package-share}

Per installare il Service Pack in un’istanza AEM 6.4 esistente, effettua le seguenti operazioni:

1. Accedi a Condivisione pacchetti in AEM o direttamente dal browser e scarica il pacchetto AEM 6.4.7.0.

    Per trovarlo, cerca “AEM-6.4.7.0”.
1. Installa il pacchetto scaricato utilizzando Gestione pacchetti.

>[!NOTE]
>
>**La finestra di dialogo nell’interfaccia utente di Gestione pacchetti talvolta si chiude prematuramente durante l’installazione della versione 6.4.7.0**
>
>È consigliabile attendere che i registri degli errori si stabilizzino prima di accedere all’istanza. L&#39;utente deve attendere i registri specifici relativi alla disinstallazione del bundle dell&#39;utility di aggiornamento prima di assicurarsi che le installazioni abbiano esito positivo. Il problema si verifica in genere in Safari, ma può accadere in modo intermittente in qualsiasi browser.

### Installazione automatica {#auto-installation}

Esistono due modi per installare automaticamente AEM 6.4.7.0 in un’istanza in esecuzione:

A. Inserite il pacchetto in ..*/crx-quickstart/install* mentre il server è in esecuzione. Il pacchetto viene installato automaticamente.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.7.0 non supporta l’installazione tramite bootstrap.

### Convalidare l’installazione {#validate-install}

1. La pagina Informazioni sul prodotto (*/system/console/ productinfo *) ora mostra la stringa di versione aggiornata &quot;Adobe Experience Manager, versione 6.4.7.0&quot; in Prodotti installati.
1. Tutti i bundle OSGi risultano come ATTIVI o FRAMMENTI nella console OSGi (usa la console Web: /system/console/bundles).
1. Il bundle OSGI org.apache.jackrabbit.oak-core è sulla versione 1.8.17 o successiva (Usa console Web: /system/console/bundle).

Per determinare la piattaforma certificata da eseguire con questa versione di AEM Sites and Assets, consulta Requisiti [](../sites-deploying/technical-requirements.md)tecnici.

>[!Note]
>On successful installation of the package, an >informational message appears indicating that the content >package has installed successfully,  such as **&quot;Content Package AEM-6.4-Service-Pack-7 installed successfully.&quot;**

### Aggiornamento dei visualizzatori per contenuti multimediali dinamici (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.7.0 contiene la nuova versione dei visualizzatori per contenuti multimediali dinamici (5.10.1) che consente di verificare la presenza di nomi duplicati nella pagina dei predefiniti per immagini. Ai clienti di contenuti multimediali dinamici viene consigliato di eseguire il comando seguente per aggiornare i predefiniti per visualizzatori box.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

che copierà i nuovi predefiniti per visualizzatori nella posizione /conf.

### Installare il pacchetto di componenti aggiuntivi per AEM Forms {#install-aem-forms-add-on-package}

#### Installare il componente aggiuntivo per AEM Forms {#installaemformsaddon}

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms. Le correzioni apportate in AEM Forms vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi.

>[!NOTE]
>
>AEM 6.4.7.0 include una nuova versione del [pacchetto di compatibilità di AEM Forms](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/AEM-FORMS-6.4.7.0-COMPAT). Se si utilizza una versione precedente del pacchetto di compatibilità AEM Forms e si aggiorna a AEM 6.4.7.0, installare la versione più recente del pacchetto di compatibilità AEM Forms dopo l&#39;installazione del pacchetto di componenti aggiuntivi Forms.

1. Assicurati di aver installato il Service Pack di AEM.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://helpx.adobe.com/experience-manager/6-4/forms/using/installing-configuring-aem-forms-osgi.html#InstallAEMFormsaddonpackage).

### Install AEM Forms JEE installer {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms in JEE. Le correzioni apportate in JEE per AEM Forms vengono distribuite tramite un programma di installazione separato.

For information about installing the cumulative installer for AEM Forms JEE and post-deployment configuration, see [AEM Forms JEE Patch Installer 0013](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0013.html).

#### Impostazioni di configurazione richieste per NPR-21268 {#configuration-settings-required-for-npr}

Se utilizzate l&#39;interfaccia classica (vecchia) e avete creato modelli di metadati utilizzando questa, seguite i passaggi per eseguire lo script JMX per mantenerli -

1. Passate a /system/console/jmx.
1. Fate clic su &quot;Migra modelli di metadati&quot;.
1. Fate clic su &quot;migrateMetadataTemplatesAtPath&quot; e fornite il percorso della cartella in cui desiderate mantenere i modelli di metadati.

#### Impostazioni di configurazione richieste per NPR-24536 {#configuration-settings-required-for-npr-1}

Per impostazione predefinita, il conteggio per la coda condivisa non viene aggiornato per gli altri utenti quando un utente richiede un&#39;attività. Per questo abbiamo introdotto una nuova proprietà. Per configurare questa proprietà nell’istanza di AEM, procedi come segue:

1. Vai all&#39;interfaccia utente Amministratore -> Servizi -> Area di lavoro -> Amministrazione globale.
1. Esporta impostazioni globali.
1. Nel file XML scaricato, aggiungete il tag &lt;client_taskPollingInterval>10&lt;/client_taskPollingInterval> Qui, 10 è il valore di esempio in secondi. Potete modificarlo di conseguenza.
1. Salvate il file.
1. Torna all&#39;interfaccia utente Amministratore -> Servizi -> Area di lavoro -> Amministrazione globale.
1. Importate il file xml nella sezione Importa impostazioni globali.
1. Ora potete disconnettervi dal sistema ed effettuare di nuovo l&#39;accesso.
1. Il conteggio della coda condivisa inizia ad aggiornarsi per gli altri utenti nell&#39;area di lavoro.
1. Per disattivare il polling, modificare il valore su 0 e importare di nuovo il file XML.

### JAR Uber {#uber-jar}

The Uber Jar for AEM 6.4.7.0 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.7/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <code>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.6</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

### Funzioni rimosse/obsolete {#removed-deprecated-features}

In questa sezione sono elencate le funzionalità rimosse o dichiarate obsolete in AEM 6.4.

| Area | Funzione | Sostituzione | Versione |
|---|---|---|---|
| Assets | Gestisci azione tag per risorse secondarie | Nessuna sostituzione | AEM 6.4.2.0 |
| Integrazione di Assets con Adobe Creative Cloud | [AEM per la condivisione](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/creative-cloud.html) di cartelle di Creative Cloud è stato introdotto in AEM 6.2 per consentire agli utenti creativi di accedere alle risorse da AEM. Una nuova funzionalità introdotta nell’applicazione Creative Cloud, Adobe Asset Link, offre un’esperienza utente migliore e un accesso più efficace alle risorse da AEM direttamente da Photoshop, InDesign e Illustrator. Adobe non apporterà ulteriori miglioramenti alla funzionalità di condivisione cartelle. Sebbene la funzione sia inclusa in AEM, i clienti sono invitati a usare la sostituzione. | Collegamento risorse Adobe o app desktop. Per ulteriori informazioni, consulta l’articolo sull’[integrazione di AEM con Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

### Problemi noti {#known-issues}

* Durante l&#39;installazione possono essere visualizzati i seguenti errori e avvisi:

   * Errori durante la creazione dell’istanza del componente e la restituzione del valore null da parte di Service Factory a causa del riavvio dell’archivio:

      * com.day.cq.cq-personalization \[com.day.cq.personalization.impl.DefaultProfileProvider(938)\] Impossibile creare l’istanza di componente a causa di un errore nel binding di profileManager di riferimento
      * org.apache.sling.commons.scheduler FrameworkEvent ERROR (org.osgi.framework.ServiceException: Service factory ha restituito null. (Componente: com.day.cq.tagging.impl.TagGarbageCollector (1687))
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Timeout in attesa del completamento della modifica del reg.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` Non è stata trovata alcuna finestra di manutenzione in granite/operations/maintenance
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: Il metodo unbindEdit ha generato un&#39;eccezione (java.lang.IllegalStateException: Servizio già non registrato).
Questi errori non richiedono alcuna azione in quanto non influiscono sull’istanza di AEM.


### Problemi risolti {#resolved-issues}

**AEM 6.4.4.0**

* Durante l’importazione/esportazione dei metadati non viene rilevato alcun errore di risorsa. CQ-4253263
* Impossibile modificare i componenti immagine e le proprietà della pagina dopo l’applicazione della versione 6.4.3.0 in cima alla versione 6.4.2.0. CQ-4260316 e CQ-4260441Per risolvere il problema:
   * Vai a Gestione pacchetti
   * Reinstallare il pacchetto &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot;
   * Ricompila tutti i JSP `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` O Riavvia l&#39;istanza.

### Bundle OSGi e pacchetti di contenuti inclusi {#osgi-bundles-and-content-packages-included}

Nei documenti di testo seguenti sono elencati i bundle OSGi e i pacchetti di contenuti inclusi in AEM 6.4.7.0.

Elenco dei bundle OSGi inclusi in AEM 6.4.7.0

[Ottieni file](assets/6.4.7.0_osgi_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.7.0

[Ottieni file](assets/sp_6.4.7.0_content_packages.txt)

### Risorse utili {#helpful-resources}

* [Note sulla versione di AEM 6.4](../release-notes/release-notes.md)
* [Pagina del prodotto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Supporto per sviluppatori AEM](https://docs.adobe.com/content/ddc/en.html)
* [Documentazione di AEM 6.4](https://helpx.adobe.com/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

### Siti con limitazioni {#restricted-sites-new}

Questi siti sono disponibili solo per i clienti. Se sei un cliente e hai bisogno di accedere, contatta il manager del tuo account Adobe.

* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/)
* [Assistenza clienti](https://daycare.day.com/)
