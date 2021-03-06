---
title: Configurare le impostazioni del servizio
seo-title: Configure service settings
description: Scopri come configurare le impostazioni del servizio.
seo-description: Learn how to configure service settings.
uuid: e95425a4-62f6-473e-b21b-d081c432e02d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 2fab4b0c-e5db-47cd-b85a-4ff5ad6eb178
exl-id: be1f8c59-b5d8-4d87-af7b-1034d73e7e83
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '10683'
ht-degree: 0%

---

# Configurare le impostazioni del servizio {#configure-service-settings}

È possibile utilizzare la pagina Gestione servizi per configurare le impostazioni per ciascuno dei servizi che fanno parte dei moduli AEM. Le impostazioni disponibili variano a seconda del servizio configurato.

1. Nella console di amministrazione, fare clic su Servizi > Applicazioni e servizi > Gestione dei servizi.
1. Arrestare il servizio prima di modificarlo. (Vedere [Avvio e arresto dei servizi](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
1. Fai clic sul nome del servizio da configurare.
1. Se il servizio dispone di una scheda Configurazione, utilizzala per modificare le impostazioni del servizio. Per ulteriori informazioni, consulta l’elenco dei collegamenti riportato di seguito.

   >[!NOTE]
   >
   >Non tutti i servizi elencati nella pagina Gestione servizi dispongono di una scheda Configurazione. Per i processi creati, la scheda Configurazione viene visualizzata solo se è stato aggiunto un parametro di configurazione al processo in Workbench. (Vedere &quot;Parametri di configurazione&quot; nella * [Guida di Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63) .) *

1. Fare clic sulla scheda Protezione e impostare le impostazioni di protezione per il servizio. Consulta [Modifica delle impostazioni di protezione per un servizio](configure-service-settings.md#modifying-security-settings-for-a-service).
1. Se il servizio dispone di una scheda Endpoint, utilizzarla per modificare le impostazioni dell&#39;endpoint. Vedere [Gestione degli endpoint](/help/forms/using/admin-help/adding-enabling-modifying-or-removing.md).
1. Fare clic sulla scheda Pooling e impostare le impostazioni di pooling. Consulta [Configurazione del pooling per un servizio](configure-service-settings.md#configuring-pooling-for-a-service).
1. Fai clic su Salva per salvare le modifiche o su Annulla per eliminarle.
1. Seleziona la casella di controllo accanto al nome del servizio e fai clic su Avvia per riavviare il servizio.

## Impostazioni del servizio Flusso di lavoro di controllo {#audit-workflow-service-settings}

Workbench consente di registrare le istanze del processo durante l’esecuzione in fase di runtime e quindi di riprodurle per osservare il comportamento del processo. (Vedere [Guida di Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).) Per risparmiare spazio sul file system del server dei moduli, è possibile limitare la quantità di dati di registrazione del processo memorizzati. È possibile configurare le seguenti proprietà del servizio Audit Workflow ( `AuditWorkflowService`):

**maxNumberOfRecordingInstances:** Il numero massimo di registrazioni memorizzate. Quando viene memorizzato il numero massimo, la registrazione più vecchia viene rimossa dal file system quando viene creata una nuova registrazione. Questa proprietà è utile se si tende a creare molte registrazioni e si desidera rimuovere automaticamente le registrazioni precedenti. Il valore predefinito è 50.

**MaxNumberOfRecordingEntries:** Il numero massimo di voci di dati memorizzabili per ciascuna registrazione. Le voci dati sono informazioni sulle operazioni del processo. Vengono memorizzate diverse voci per ogni esecuzione di un&#39;operazione, ad esempio se l&#39;operazione è iniziata, se l&#39;operazione è stata completata e se il percorso che porta all&#39;operazione è completo. Questa proprietà è utile quando i processi possono includere molte esecuzioni di operazioni, ad esempio, quando viene rilevato un ciclo infinito. Il valore predefinito è 50.

## impostazioni del servizio moduli con codice a barre {#barcoded-forms-service-settings}

Il servizio moduli con codice a barre `(BarcodedFormsService)` estrae i dati del codice a barre dalle immagini digitalizzate. Il servizio accetta un modulo con codice a barre (TIFF o PDF) come input ed estrae la rappresentazione automatica dei dati codificati dal codice a barre.

Per il servizio moduli con codice a barre sono disponibili le seguenti impostazioni.

**Lettura a sinistra:** se selezionate, le immagini del codice a barre vengono digitalizzate orizzontalmente da destra a sinistra.

**Leggi a destra:** se selezionate, le immagini del codice a barre vengono scansionate orizzontalmente da sinistra a destra.

**Lettura in alto:** se selezionate, le immagini del codice a barre vengono digitalizzate verticalmente dal basso verso l&#39;alto.

**Lettura in basso:** se selezionate, le immagini del codice a barre vengono digitalizzate verticalmente dall&#39;alto verso il basso.

>[!NOTE]
>
>Per impostazione predefinita, sono selezionate tutte le opzioni. Deselezionare un’opzione solo se si è certi che sui moduli non verrà visualizzato alcun codice a barre.

**Percorso file di base:** il percorso del file relativo ai parametri del file di input e di output batch per le operazioni Esegui processo file XML ed Esegui processo di file Flat vengono risolti. Nelle configurazioni del cluster, il percorso del file di base deve essere un percorso del file system condiviso in cui tutti i nodi del cluster hanno accesso in lettura/scrittura.

**Nome origine dati:** il nome dell&#39;origine dati utilizzata per mantenere le informazioni sullo stato e sulla cronologia dei processi di elaborazione batch. L&#39;origine dati specificata deve supportare transazioni globali (XA).

## Impostazioni del servizio Central Migration Bridge (obsoleto) {#central-migration-bridge-service-settings}

Il servizio Central Migration Bridge ( `CentralMigrationBridge`) richiama un sottoinsieme di funzionalità Adobe Central Pro Output Server (Central), che include i comandi JFMERGE, JFTRANS e XMLIMPORT. Le operazioni del servizio Central Migration Bridge consentono di riutilizzare le risorse centrali seguenti nei moduli AEM:

* progettazione del modello (&amp;ast;.ifd)
* modelli di output (&amp;ast;.mdf)
* file di dati (&amp;ast;.dat files)
* file preambolo (&amp;ast;.pre files)
* file di definizione dati (&amp;ast;.tdf)

Per il servizio Central Migration Bridge è disponibile la seguente impostazione.

**Directory di installazione centrale:** la directory in cui è installato Adobe Central 5.7.

## Content Repository Connector per le impostazioni del servizio EMC Documentum {#content-repository-connector-for-emc-documentum-service-settings}

Il Content Repository Connector per il servizio EMC Documentum ( `EMCDocumentumContentRepositoryConnector`) consente di creare processi che interagiscono con i contenuti archiviati in un repository Documentum.

Per il servizio Content Repository Connector for EMC Documentum è disponibile l&#39;impostazione seguente.

**Percorso predefinito oggetto Asset Link:** la parte predefinita del percorso nel repository Documentum per la memorizzazione dell&#39;oggetto Asset Link. Il percorso effettivo è costituito dal percorso predefinito e dalla posizione del modello di modulo nell’archivio dei moduli di AEM.

Ad esempio, se il percorso predefinito è impostato su `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects` e il modello di modulo è memorizzato in una cartella `/Docbase/forms/`, l’oggetto Asset Link viene memorizzato nel percorso seguente:

`/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects/Docbase/forms/`

Il valore predefinito di questa impostazione è `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects`.

## Connettore dell&#39;archivio dei contenuti per le impostazioni del servizio IBM FileNet {#content-repository-connector-for-ibm-filenet-service-settings}

Il connettore Content Repository per IBM FileNet ti consente di creare processi che interagiscono con il contenuto memorizzato in un archivio IBM FileNet.

La seguente impostazione è disponibile per il Content Repository Connector per il servizio IBM FileNet.

**Percorso predefinito oggetto Asset Link:** la parte predefinita del percorso nell’archivio FileNet di IBM per la memorizzazione dell’oggetto Asset Link. Il percorso effettivo è costituito dal percorso predefinito e dalla posizione del modello di modulo nell’archivio dei moduli di AEM.

Ad esempio, se il percorso predefinito è impostato su `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects` e il modello di modulo è memorizzato in una cartella `/Docbase/forms/`, l’oggetto Asset Link viene memorizzato nel percorso seguente:

`/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects/Docbase/forms/`

Il valore predefinito di questa impostazione è `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects`.

## Conversione delle impostazioni del servizio PDF {#convert-pdf-service-settings}

Il servizio Converti PDF ( `ConvertPdfService`) converte i documenti PDF in PostScript e in diversi formati di immagine (JPEG, JPEG 2000, PNG e TIFF). La conversione di un documento PDF in PostScript è utile per la stampa automatica basata su server su qualsiasi stampante PostScript. La conversione di un documento PDF in un file TIFF multipagina è pratica quando si archiviano documenti in sistemi di gestione dei contenuti che non supportano documenti PDF.

Per il servizio Converti PDF sono disponibili le seguenti impostazioni.

**Tipo di transazione:** specifica il modo in cui il contesto di una transazione deve essere propagato a un&#39;operazione.

**Obbligatorio:** supporta un contesto di transazione, se esistente; in caso contrario, viene creato un nuovo contesto di transazione. Questo è il valore predefinito.

**Richiede nuovo:** crea sempre un nuovo contesto di transazione. Se esiste un contesto di transazione attivo, viene sospeso.

**Timeout transazione (in secondi):** il numero di secondi in cui il provider di transazioni sottostante deve attendere prima di eseguire il rollback di una transazione che sta racchiudendo questa operazione. Questo valore verrà ignorato se viene propagato un contesto di transazione esistente. Il valore predefinito è 180.

**Risoluzione soglia per uniformità (in dpi):** la risoluzione dell&#39;immagine al di sotto della quale l&#39;uniformità (o anti-aliasing) viene applicata al testo, alla grafica e alle immagini, se avete selezionato le opzioni &quot;Applica uniformità a&quot; per tali elementi.

**Applica l’uniformità al testo:** controlla l’anti-aliasing del testo. Per disattivare l’uniformità del testo e rendere il testo più nitido e leggibile con una lente di ingrandimento dello schermo, deselezionare questa casella.

**Applica l&#39;uniformità a LineArt:** applica l&#39;uniformità per rimuovere angoli bruschi nelle linee.

**Applica uniformità alle immagini:** applica l’uniformità per ridurre al minimo le modifiche brusche nelle immagini.

## Impostazioni del servizio Distiller {#distiller-service-settings}

Il servizio Distiller ( `DistillerService`) converte i file PostScript, Encapsulated PostScript (EPS) e PRN in file PDF su una rete.

Per il servizio Distiller sono disponibili le seguenti impostazioni.

**Impostazioni Adobe PDF:** le seguenti impostazioni preconfigurate vengono applicate al PDF generato:

* Stampa di alta qualità
* Pagine oversize
* CMYK PDFA1b 2005
* PDFA1b 2005 RGB
* PDFX1a 2001
* PDFX3 2002
* Qualità della stampa
* Dimensioni file più piccole
* Standard

È possibile creare nuove impostazioni tramite l’interfaccia utente di PDF Generator.

**Impostazioni di protezione:** impostazioni di protezione preconfigurate applicate ai documenti PDF generati. Il valore predefinito è Nessuna protezione. È necessario creare le impostazioni di protezione utilizzando PDF Generator, quindi immettere l&#39;impostazione qui.

**Dimensione pool:** La dimensione iniziale del pool. Quando il servizio Distiller viene distribuito, questo numero viene utilizzato per determinare il numero di istanze di implementazione del servizio create e allocate al pool gratuito in attesa di richieste di chiamata. Il contenitore del servizio può quindi rispondere immediatamente alle richieste di chiamata senza dover prima inizializzare un&#39;istanza del servizio.

## Impostazioni del servizio Gestione documenti {#document-management-service-settings}

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (obsoleto) è un sistema di gestione dei contenuti installato con il LiveCycle. Consente agli utenti di progettare, gestire, monitorare e ottimizzare processi incentrati sulle persone. Il supporto per Content Services (obsoleto) termina il 31/12/2014. Consulta [Adobe documento sul ciclo di vita del prodotto](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html).

Il servizio Document Management ( `DocumentManagementService`) consente ai processi di utilizzare la funzionalità di gestione dei contenuti fornita da Content Services (obsoleto). Le operazioni di gestione dei documenti forniscono le attività di base necessarie per mantenere spazi e contenuti nel sistema di gestione dei contenuti. Esempi di tali attività sono copiare, eliminare, spostare, recuperare e archiviare contenuti, creare spazi e associazioni e ottenere e impostare attributi di contenuto.

Per il servizio Gestione documenti sono disponibili le seguenti impostazioni.

**Store Scheme:** lo schema dell’archivio in cui si trova il contenuto. Il valore predefinito è workspace.

**Porta HTTP:** la porta utilizzata per accedere a Content Services (obsoleto). Il valore predefinito è 8080.

## Impostazioni del servizio e-mail {#email-service-settings}

L’e-mail viene comunemente utilizzata per distribuire contenuti o fornire informazioni sullo stato come parte di un processo automatizzato. Il servizio e-mail ( `EmailService`) consente ai processi di ricevere messaggi e-mail da un server POP3 o IMAP e di inviare messaggi e-mail a un server SMTP.

Ad esempio, un processo utilizza il servizio E-mail per inviare un messaggio e-mail con un allegato modulo PDF. Il servizio e-mail si connette a un server SMTP per inviare il messaggio e-mail con l’allegato. Il modulo PDF è progettato per consentire al destinatario di fare clic su Invia dopo aver completato il modulo. L’azione fa sì che il modulo venga restituito come allegato al server di posta elettronica designato. Il servizio e-mail recupera il messaggio e-mail restituito e memorizza il modulo completato in una variabile del modulo dati del processo.

Per il servizio e-mail sono disponibili le seguenti impostazioni.

**Host SMTP:** l’indirizzo IP o l’URL del server SMTP da utilizzare per l’invio dell’e-mail.

**Numero di porta SMTP:** la porta utilizzata per connettersi al server SMTP.

**Autenticazione SMTP:** seleziona se è necessaria l’autenticazione utente per connettersi al server SMTP.

**Utente SMTP:** il nome utente dell’account utente da utilizzare per accedere al server SMTP.

**Password SMTP:** password associata all’account utente SMTP.

**Sicurezza del trasporto SMTP:** protocollo di sicurezza da utilizzare per la connessione al server SMTP:

* Seleziona Nessuno se non viene utilizzato alcun protocollo (i dati vengono inviati in testo non crittografato)
* Seleziona SSL se utilizzi il protocollo Secure Sockets Layer.
* Seleziona TLS se utilizzi Transport Layer Security.

**Host POP3/IMAP:** l&#39;indirizzo IP o l&#39;URL del server POP3 o IMAP da utilizzare per l&#39;invio delle e-mail.

**Nome utente POP3/IMAP:** il nome utente dell’account utente da utilizzare per accedere al server POP3 o IMAP.

**Password POP3/IMAP:** password associata all&#39;account utente POP3 o IMAP.

**Numero di porta POP3/IMAP:** la porta utilizzata per connettersi al server POP3 o IMAP.

**POP3/IMAP:** il protocollo da utilizzare per l&#39;invio e la ricezione di e-mail.

**Ricevi sicurezza trasporto:** protocollo di sicurezza da utilizzare per la connessione al server SMTP:

* Selezionare Nessuno se non viene utilizzato alcun protocollo (i dati vengono inviati in testo non crittografato).
* Seleziona SSL se utilizzi il protocollo Secure Sockets Layer.
* Seleziona TLS se utilizzi Transport Layer Security.

## Impostazioni del servizio di crittografia {#encryption-service-settings}

Il servizio di cifratura ( `EncryptionService`) consente di cifrare e decrittografare i documenti. Quando un documento viene crittografato, il suo contenuto diventa illeggibile. Un utente autorizzato può decrittografare il documento per ottenere l&#39;accesso ai contenuti. Se un documento PDF è crittografato con una password, è necessario specificare la password aperta prima di poter visualizzare il documento in Adobe Reader o Adobe Acrobat. Analogamente, se un documento PDF è crittografato con un certificato, l’utente deve decrittografare il documento PDF con la chiave pubblica corrispondente al certificato (chiave privata) utilizzato per cifrare il documento PDF.

Per il servizio di cifratura sono disponibili le seguenti impostazioni.

**Server LDAP predefinito a cui connettersi:** nome host del server LDAP utilizzato per recuperare i certificati per la crittografia dei documenti.

**Porta LDAP predefinita a cui connettersi:** numero di porta del server LDAP.

**Nome utente LDAP predefinito:** se il server LDAP richiede l&#39;autenticazione, specifica il nome utente da utilizzare per connettersi al server LDAP.

**Password LDAP predefinita:** se il server LDAP richiede l&#39;autenticazione, specifica la password che corrisponde al nome utente da utilizzare per connettersi al server LDAP.

>[!NOTE]
>
>Utilizzare l’autenticazione semplice (nome utente e password) solo quando la connessione è protetta tramite SSL (utilizzando LDAPS).

**Modalità di compatibilità:**

## Impostazioni del servizio FTP {#ftp-service-settings}

Il servizio FTP ( `FTP`) consente ai processi di interagire con un server FTP. Le operazioni del servizio FTP possono recuperare file dal server FTP, inserire file sul server FTP ed eliminare file dal server FTP. Ad esempio, documenti come i report generati da un processo possono essere archiviati su un server FTP per la distribuzione. Oppure un sistema esterno può generare alcuni file in base ai passaggi precedenti di un processo. In una fase successiva del processo, i file possono essere trasferiti in una posizione remota.

Le seguenti impostazioni sono disponibili per il servizio FTP.

**Host predefinito:** l&#39;indirizzo IP o l&#39;URL del server FTP.

**Porta predefinita:** la porta utilizzata per la connessione al server FTP. Il valore predefinito è 21.

**Nome utente predefinito:** il nome dell&#39;account utente che puoi utilizzare per accedere al server FTP. L&#39;account utente deve disporre di privilegi sufficienti per eseguire le operazioni FTP necessarie per questo servizio.

**Password predefinita:** password da utilizzare con il nome utente specificato per l&#39;autenticazione con il server FTP.

## Genera impostazioni del servizio PDF {#generate-pdf-service-settings}

Il servizio Genera PDF ( `GeneratePDFService`) converte i file in vari formati nativi in documenti PDF e converte i documenti PDF in diversi formati di file.

Per il servizio Genera PDF sono disponibili le seguenti impostazioni.

**Impostazioni Adobe PDF:** il nome delle impostazioni Adobe PDF preconfigurate da applicare a un processo di conversione, se queste impostazioni non sono specificate come parte dei parametri di chiamata API. Le impostazioni Adobe PDF sono configurate nella console di amministrazione, facendo clic su Servizi > PDF Generator> Impostazioni Adobe PDF. Queste impostazioni sono applicabili solo alle conversioni basate su PDFMaker.

**Impostazioni di sicurezza:** il nome delle impostazioni di sicurezza preconfigurate da applicare a un processo di conversione, se queste impostazioni non sono specificate come parte dei parametri di chiamata API. Le impostazioni di protezione sono configurate nella console di amministrazione, facendo clic su Servizi > PDF Generator> Impostazioni di protezione.

**Tipo di file Impostazioni:** il nome dell&#39;impostazione del tipo di file preconfigurata da applicare a un processo di conversione, se queste impostazioni non sono specificate come parte dei parametri di chiamata API. Le impostazioni del tipo di file sono configurate nella console di amministrazione, facendo clic su Servizi > PDF Generator> File Type Settings.

**Utilizza Acrobat WebCapture (solo Windows):** quando questa impostazione è true, il servizio Generate PDF utilizza Acrobat X Pro per tutte le conversioni da HTML a PDF. Questo può migliorare la qualità dei file PDF prodotti da HTML, anche se le prestazioni potrebbero essere leggermente inferiori. Il valore predefinito è false.

**Usa conversione immagine di Acrobat (solo Windows):** quando questa impostazione è true, il servizio Genera PDF utilizza Acrobat X Pro per tutte le conversioni da immagine a PDF. Questa impostazione è utile solo se il meccanismo predefinito di conversione Java non è in grado di convertire correttamente una parte significativa delle immagini di input. Il valore predefinito è false.

**Abilita conversioni AutoCAD basate su Acrobat (solo Windows):** quando questa impostazione è true, il servizio Genera PDF utilizza Acrobat X Pro per tutte le conversioni da DWG a PDF. Questa impostazione è utile solo se AutoCAD non è installato sul server o se il meccanismo di conversione AutoCAD non è in grado di convertire i file con successo.

**Espressioni regolari per la ricerca di caratteri speciali proibiti nel nome utente (solo Windows):** specifica i caratteri che interferiscono con le operazioni di Export PDF e Optimize PDF quando i caratteri vengono visualizzati nel nome di un utente.

**ImageToPDF Pool Size:** La dimensione del pool del convertitore da immagine a PDF predefinito (puro Java) nel servizio Genera PDF. Questa impostazione controlla le conversioni simultanee da immagine a PDF massime eseguibili dal servizio Genera PDF. Il valore predefinito di questa impostazione (consigliato per i sistemi a processore singolo) è 3, che è possibile aumentare sui sistemi a più processori.

**Dimensione pool da HTML a PDF:** dimensione pool del convertitore da HTML a PDF nel servizio Genera PDF. Questa impostazione controlla le conversioni simultanee massime da HTML a PDF eseguibili dal servizio Genera PDF. Il valore predefinito di questa impostazione (consigliato per i sistemi a processore singolo) è 3, che è possibile aumentare sui sistemi a più processori.

**Dimensione pool OCR:** La dimensione pool del PaperCaptureService utilizzato da PDF Generator per OCR. Il valore predefinito di questa impostazione (consigliato per i sistemi a processore singolo) è 3, che è possibile aumentare sui sistemi a più processori. Questa impostazione è valida solo nei sistemi Windows.

**Famiglia di font di fallback per le conversioni da HTML a PDF:** il nome della famiglia di font da utilizzare nei documenti PDF quando il font utilizzato nell’HTML originale non è disponibile per il server dei moduli AEM. Specifica una famiglia di font se vuoi convertire le pagine HTML che utilizzano font non disponibili. Ad esempio, le pagine create in lingue regionali potrebbero utilizzare font non disponibili.

**La logica dei tentativi per** le conversioni native gestisce i tentativi di generazione dei PDF se il primo tentativo di conversione non è riuscito:

**Nessun tentativo**

Non ripetere la conversione PDF se il primo tentativo di conversione non è riuscito

**Riprova**

Riprova la conversione PDF indipendentemente dal raggiungimento della soglia di timeout. La durata predefinita del timeout per il primo tentativo è 270 s.

**Riprova se il tempo a disposizione lo consente**

Riprovare la conversione PDF se il tempo impiegato per il primo tentativo di conversione è inferiore alla durata di timeout specificata. Ad esempio, se la durata di timeout è 270 e il primo tentativo è stato consumato 200, PDF Generator tenterà nuovamente di convertire. Se il primo tentativo stesso ha consumato 270 anni, la conversione non verrà ritentata.

## Impostazioni del servizio Guide ES4 Utilities {#guides-es4-utilities-service-settings}

Quando crei una Guida, alcune risorse, come la definizione della Guida, sono incorporate nella Guida. Le risorse possono anche essere utilizzate come riferimenti alle risorse dell’applicazione memorizzate localmente o sul server dei moduli di AEM. La Guida non contiene dati e i valori per il percorso di invio e gli input non sono adatti a tutti gli ambienti esterni.

Nella maggior parte dei casi, i servizi di rendering predefiniti delle Guide sono sufficienti per preparare una Guida da utilizzare in Workspace o in altri ambienti esterni. (Nella vista Servizi, in Workbench, il servizio predefinito è Guide (sistema)/Processes/Render Guide - 1.0.) Il servizio Utilità guida ( `GuidesUtility`) consente di creare un processo personalizzato per il rendering di una Guida, se necessario.

Le operazioni di utilità guida consentono di aggiungere a un processo le seguenti attività di rendering della guida:

* Determinare se i dati sono disponibili per compilare la Guida con
* Incorporare i dati della Guida TV o convertirli in un collegamento
* Convertire il contenuto di riferimento in URL accessibili esternamente
* Sostituisci i valori in un documento HTML o in un altro wrapper o convertirli in URL accessibili esternamente
* Imposta il percorso di invio
* Specificare i valori di input
* Creare un parametro per rappresentare il contenuto a cui si fa riferimento
* Se sono disponibili delle varianti, imposta una variante

I valori predefiniti del servizio Guide Utilities supportano la maggior parte dei casi d&#39;uso. Tuttavia, se necessario, è possibile modificare i seguenti valori.

**publicPaths:** questa opzione è stata dichiarata obsoleta. Non utilizzare questa opzione con AEM moduli.

**pathInfoExpiryInSeconds:** l&#39;intervallo dopo il quale scade una richiesta di informazioni sul percorso da un client. Il valore predefinito è 1.

**collateraleExpiryInSeconds:** l’intervallo dopo il quale scade una richiesta di garanzia collaterale da parte di un cliente. Il valore predefinito è 315576000.

**mismatchExpiryInSeconds:** l’intervallo dopo la scadenza di una richiesta di garanzia collaterale da un client, quando eTag (tag entità) non corrisponde. Un eTag è un’intestazione di risposta HTTP. Il valore predefinito è 1.

**guideContext:** la directory principale del contesto dell&#39;applicazione Web Guide. Corrisponde al valore impostato utilizzando l&#39;applicazione Web Guide. Il valore predefinito è /Guides/.

**secureRandomAlgorithm:** l&#39;algoritmo da utilizzare per la generazione di chiavi e identificatori. Questo valore viene passato al metodo getInstance della classe Java SecureRandom. Il valore predefinito è SHA1PRNG.

**idBytes:** il numero di byte casuali da utilizzare per un identificatore chiave. Il valore predefinito è 6.

**macAlgorithm:** algoritmo MAC (message authentication code) da utilizzare per la verifica degli URL collaterali. Questo metodo viene passato al metodo getInstance della classe Mac. Il valore predefinito è HmacSHA1.

**macRefreshIntervalInMinutes:** la quantità di tempo in cui una chiave è attiva. Quando una chiave è stata attiva per questo intervallo, viene generata una nuova chiave. La nuova chiave diventa la chiave attiva. La chiave precedentemente attiva viene mantenuta per il 10% dell&#39;intervallo di aggiornamento. Questo comportamento consente agli URL generati utilizzando la chiave precedente di continuare a funzionare sullo switch di chiave. Il valore predefinito è 144000.

**macOverlapIntervalInMinutes:** Tempo in cui la chiave precedente rimarrà valida dopo la generazione di una nuova chiave. Il valore predefinito è 1440 minuti (1 giorno).

**macKeySeed:** valore di seed per la generazione dell’URL protetto. Quando questa opzione è attivata, la chiave non viene mai aggiornata. Se imposti lo stesso seed su server diversi, quei server generano URL sicuri compatibili. Ciò può essere utile se dietro un load balancer sono in uso più server di moduli. Immetti una sequenza casuale di caratteri e numeri come valori iniziali.

### Utilizzo delle Guide in un cluster di server {#using-guides-in-a-server-cluster}

Il rendering di una Guida in un cluster di server che non utilizza sessioni permanenti non riesce con un NullPointerException. Una richiesta Guide sfrutta gli URL sicuri che, per impostazione predefinita, sono univoci per il server su cui sono generati. In un cluster che utilizza sessioni permanenti, dopo che una richiesta raggiunge un nodo nel cluster, tutte le richieste successive per quella sessione o utente vengono indirizzate esclusivamente a tale server, e tutto va bene. In un cluster che non utilizza sessioni permanenti, le richieste successive possono colpire qualsiasi server del cluster. Se il server utilizzato per le richieste non è il server originale, non riesce a risolvere l’URL protetto.

Se si utilizzano Guide in un cluster di server che non utilizza sessioni permanenti, impostare il valore macKeySeed per il servizio GuidesUtility, quindi arrestare e avviare il cluster.

Il valore macKeySeed è il valore di base per il generatore di numeri casuali utilizzato per generare gli URL sicuri. Impostando questo valore, ogni nodo del cluster inizializza il generatore di numeri casuali nello stesso modo e ha accesso agli stessi URL protetti. Puoi utilizzare qualsiasi stringa casuale per questo valore di seed.

Modifica il valore macKeySeed quando devi aggiornare gli URL protetti. L’aggiornamento degli URL protetti dipende dai criteri di sicurezza in uso ed è simile ai criteri di aggiornamento per la modifica della password principale del server. macSeedValue è analogo alla password master per gli URL sicuri, in quanto viene utilizzato per generare un nuovo numero casuale univoco da utilizzare nella generazione e nel recupero sicuri degli URL.

È necessario riavviare il cluster perché macSeedValue è di sola lettura all&#39;avvio del sistema. Tutti i nodi devono riavviare per leggere il valore, perché lo utilizzano in modo indipendente per inizializzare i propri numeri casuali interni con il valore seed.

## Impostazioni del servizio JDBC {#jdbc-service-settings}

Il servizio JDBC ( `JdbcService`) consente ai processi di interagire con i database.

Per il servizio JDBC è disponibile la seguente impostazione.

**datasourceName:** valore stringa che rappresenta il nome JNDI dell&#39;origine dati da utilizzare per la connessione al server di database. L’origine dati deve essere definita sul server dell’applicazione che ospita il server dei moduli. Il valore predefinito è il nome JNDI dell’origine dati per il database dei moduli di AEM.

## Impostazioni del servizio JMS {#jms-service-settings}

Il servizio JMS ( `JMS`) consente l&#39;interazione con i provider JMS (Java Messaging System) che implementano sia la messaggistica punto-punto che la messaggistica di pubblicazione/sottoscrizione.

Configura il servizio JMS con le proprietà predefinite in modo che le operazioni del servizio possano connettersi e interagire con un provider JMS e un servizio JNDI associato. I valori delle proprietà del servizio sono impostati su valori predefiniti in base al server applicazioni JBoss. Modificare questi valori se si utilizza un server applicazioni diverso per ospitare moduli AEM.

Le seguenti impostazioni sono disponibili per il servizio JMS.

**URL del provider:** l&#39;URL del provider di servizi JNDI. Il valore predefinito è basato sul server applicazioni JBoss. I seguenti URL sono valori predefiniti per i server applicazioni supportati da AEM forms:

**JBoss:** `<server name>:1099`

**WebLogic:** `<server name>:7001`

**WebSphere:** `<server name>:2809`

**Nome utente JNDI:** il nome utente dell&#39;account da utilizzare per l&#39;autenticazione con il provider di servizi JNDI che viene utilizzato per cercare i nomi delle code e degli argomenti. Il valore predefinito è guest.

**Password JNDI:** password associata al nome utente specificato per il nome utente JNDI. Il valore predefinito è guest.

**Initial Context Factory:** la classe Java da utilizzare come elemento di base del contesto iniziale. Il servizio JMS utilizza questa classe per creare un contesto iniziale, che rappresenta il punto di partenza per la risoluzione dei nomi di argomenti e code. Il valore predefinito è la factory del contesto iniziale per il servizio JMS su JBoss. Le classi seguenti sono le prime fabbriche di contesto per i server applicazioni supportati da AEM forms:

**JBoss:** org.jnp.interfaces.NamingContextFactory

**WebLogic:** weblogic.jndi.WLInitialContextFactory

**WebSphere:** com.ibm.websphere.denominazione.WsnInitialContextFactory

**Nome utente connessione:** password associata al nome utente specificato per Nome utente connessione. Il valore predefinito è guest.

**Password connessione:** password associata al nome utente specificato per Nome utente connessione. Il valore predefinito è guest.

**Altre proprietà:** coppie di nome e valore di proprietà che puoi passare al provider di servizi JNDI. Queste proprietà dipendono dall’implementazione e dalla configurazione del provider in uso.

Le coppie nome e valore della proprietà sono separate da punti e virgola **;**. Ad esempio, il testo seguente mostra il valore specificato per due proprietà denominate name1 e name2, rispettivamente con i valori value1 e value2:

`name1=value1;name2=value2`

## Impostazioni del servizio LDAP {#ldap-service-settings}

Il servizio LDAP ( `LDAPService`) fornisce operazioni per eseguire query sulle directory LDAP. Le directory LDAP vengono generalmente utilizzate per memorizzare informazioni sulle persone, sui gruppi e sui servizi di un&#39;organizzazione.

Per il servizio LDAP sono disponibili le seguenti impostazioni.

**Initial Context Factory:** la classe Java da utilizzare come valore di fabbrica del contesto. Questa classe viene utilizzata per creare una connessione al server LDAP. Il valore predefinito è com.sun.jndi.ldap.LdapCtxFactory , appropriato per la maggior parte dei server LDAP.

**URL provider:** l&#39;URL da utilizzare per connettersi al servizio LDAP. Il formato del valore è `ldap://server name:port`

*nome server* è il nome del computer che ospita il server LDAP

** è la porta di comunicazione utilizzata dal servizio LDAP. Il valore predefinito è 389, che è la porta standard utilizzata per le connessioni LDAP.

**Nome utente:** il nome utente dell&#39;account utente da utilizzare per accedere al server LDAP. L&#39;account utente deve disporre dell&#39;autorizzazione per connettersi al server e leggere le informazioni nella directory LDAP.

A seconda del server LDAP, il nome utente può essere un nome utente semplice come `myname` o un DN, ad esempio `cn=myname,cn=users,dc=myorg`.

**Password:** la password che corrisponde al nome utente fornito per l’impostazione Nome utente.

**Altre proprietà:** valore stringa che rappresenta altre proprietà e i relativi valori corrispondenti che è possibile fornire al server LDAP. Il valore è nel seguente formato:

`property=value;property=value;...`

## Impostazioni del servizio di configurazione di Microsoft SharePoint {#microsoft-sharepoint-configuration-service-settings}

Il servizio di configurazione di Microsoft SharePoint `(MSSharePointConfigService)`consente di specificare le credenziali per l’utente dei moduli AEM che dispone delle autorizzazioni di rappresentazione. Per informazioni sulle autorizzazioni di rappresentazione, vedere [Configurazione del connettore per Microsoft SharePoint](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html).

Per il servizio di configurazione di Microsoft SharePoint sono disponibili le seguenti impostazioni:

* Nome utente per un utente con autorizzazioni di rappresentazione
* Password per l&#39;utente di cui sopra

**Abilita SSL (HTTPS):**

**Tempo di esecuzione:** tempo, in secondi, in cui questo profilo di provisioning è valido e memorizzato nella cache sul client. Il valore predefinito è 86400 (24 ore). Quando un&#39;applicazione client si sincronizza con il server e il tempo specificato è trascorso, l&#39;applicazione client richiede un nuovo profilo di provisioning dal server.

**Crittografia:** specifica se crittografare i dati memorizzati sul dispositivo mobile.

**Applicazione Forms:** abilita la funzione Forms nelle applicazioni client mobili. Quando questa opzione è selezionata, gli utenti possono aprire i moduli e avviare i processi dai propri dispositivi mobili.

**Applicazione attività:** abilita la funzione Attività nelle applicazioni client mobili. Quando questa opzione è selezionata, gli utenti possono accedere ai propri elenchi di attività e completare le attività dai propri dispositivi mobili.

**Applicazione Content Services:** abilita la funzione Content Services nell’applicazione client mobile. Questa funzione è disponibile solo per iOS. Quando questa opzione è selezionata, gli utenti iPhone e iPad possono accedere ai file memorizzati nel server WebDAV delle organizzazioni.

**Supporto offline:** consente agli utenti di continuare a utilizzare le applicazioni client mobili anche quando non dispongono di una connessione al server (ad esempio, quando non rientrano nell’intervallo di celle o in modalità aeroplano). Gli utenti devono inoltre abilitare l’impostazione Supporto offline sui propri dispositivi mobili. Questa funzione è disponibile per i dispositivi Android e iOS. Per impostazione predefinita, questa funzione è disattivata.

>[!NOTE]
>
>Se il supporto Offline è stato abilitato e successivamente lo si disabilita, i profili di provisioning degli utenti vengono aggiornati immediatamente o non appena sono online. Se un utente ha lavorato offline, tutte le attività in sospeso vengono restituite all&#39;elenco Attività e tutti gli elementi nella coda, inclusi i moduli in sospeso, le attività e i moduli contenenti errori di convalida, vengono eliminati dalla coda.

**Android:** consente ai dispositivi Android di connettersi al server.

**Apple iOS:** consente a iPhone e iPad di connettersi al server.

**AIR:** consente ai dispositivi che eseguono app basate su Adobe AIR® di connettersi al server.

**BlackBerry:** consente ai dispositivi BlackBerry di connettersi al server.

**Android Microsoft Exchange ActiveSync Obbligatorio:** specifica se Microsoft Exchange ActiveSync Policy Manager (EA) deve essere installato e attivo sui dispositivi Android. Quando questa opzione è selezionata, EA deve essere applicato sul dispositivo Android. Se questa opzione non è selezionata, non viene eseguito alcun controllo, anche se altri requisiti sono ancora applicati.

**Lunghezza minima PIN Android:** i dispositivi Android devono avere un&#39;impostazione globale che impone che il PIN o la password siano almeno di questa lunghezza. Non è sufficiente avere un PIN della lunghezza specificata. La lunghezza del PIN deve essere applicata dal sistema in modo che gli utenti non possano rimuovere o accorciare il PIN in un secondo momento. Il valore predefinito è 4.

**Numero massimo di tentativi di password Android prima di Wipe:** i dispositivi Android hanno un&#39;impostazione globale che cancella il sistema dopo un numero specificato di tentativi di password non validi. Questa impostazione globale è abilitata e uguale o inferiore al valore specificato qui. Il valore predefinito è 5.

**Android Wipe On Removal (Cancella Android alla rimozione):** specifica cosa accade quando si verifica una violazione di criteri su un dispositivo Android. Quando questa opzione è selezionata, l’account viene eliminato. Quando questa opzione non è selezionata, la password dell&#39;account memorizzato e i dati memorizzati nella cache vengono eliminati. Non vengono più effettuati tentativi di sincronizzazione finché l’utente non risolve la violazione dei criteri.

## Impostazioni del servizio di output {#output-service-settings}

Il servizio di output `(OutputService)`consente di unire i dati del modulo XML con una struttura del modulo creata in AEM Designer per creare un flusso di output del documento in uno dei seguenti formati:

* Flusso di output di un documento PDF o PDF/A.
* Flusso di output Adobe PostScript.
* Flusso di output PCL (Printer Control Language).
* Un flusso di output Zebra Programming Language (ZPL).

Il flusso di output può essere inviato a una stampante di rete, a una stampante locale o a un file disco. Quando utilizzi il servizio Output come parte di un processo, puoi anche inviare il flusso di output a un destinatario e-mail come file allegato.

Per il servizio Output sono disponibili le seguenti impostazioni.

**Tipo di transazione:** specifica il modo in cui il contesto di una transazione deve essere propagato a un&#39;operazione:

**Obbligatorio:** supporta un contesto di transazione se esiste già; in caso contrario, viene creato un nuovo contesto di transazione. Questo è il valore predefinito.

**Richiede nuovo:** crea sempre un nuovo contesto di transazione. Se esiste un contesto di transazione attivo, viene sospeso.

**Timeout transazione (in secondi):** il numero di secondi che il provider di transazioni sottostante attende prima di eseguire il rollback di una transazione che sta racchiudendo questa operazione. Questo valore viene ignorato se viene propagato un contesto di transazione esistente.

Quando si elaborano file di dati di grandi dimensioni o si utilizzano su un server occupato, può essere necessario aumentare il timeout del servizio Output. Per modificare il valore del timeout, assicurarsi che i server hardware dispongano di memoria adeguata e che la memoria sia disponibile per l&#39;heap di Java Application Server. Il valore predefinito è `180`.

## Impostazioni del servizio di configurazione PDFG {#pdfg-config-service-settings}

Per il servizio di configurazione PDFG ( `PDFGConfigService`) sono disponibili le seguenti impostazioni.

**Directory delle opzioni di lavoro utente:** il percorso della cartella del file system in cui il servizio c scrive i file delle opzioni di lavoro accessibili ad Acrobat Pro Extended. Il valore predefinito è [user.home]/Application Data/Adobe/Adobe PDF/Settings.

**Directory di avvio PS:** il percorso della cartella del file system in cui vengono salvati i file di avvio richiesti da Adobe Acrobat Distiller. Il valore predefinito è [user.home]/Application Data/Adobe/Adobe PDF/Distiller/Startup.

**File di avvio PS:** il nome del file di avvio richiesto da Adobe Acrobat Distiller. Il valore predefinito è example.ps.

**Timeout conversione server:** il timeout massimo di conversione del processo (in secondi) per il servizio Generate PDF e il servizio Distiller. Questa impostazione limita il timeout massimo di conversione che può essere specificato nel file config.xml e nelle pagine della console di amministrazione per PDF Generator. Il valore predefinito è 270.

**Timeout globale del server:** durante l’esecuzione di conversioni PDF, un server dei moduli tiene conto del limite di timeout. Configura il valore di timeout per risolvere il problema.

**Prefisso opzioni processo:** Prefisso utilizzato dal servizio Genera PDF per anteporre una stringa breve ai file delle opzioni di lavoro che crea temporaneamente per l&#39;uso da parte di Acrobat Distiller. Il valore predefinito è pdfg.

**App non Unicode:** un elenco separato da virgole di nomi di applicazione noti per l&#39;impossibilità di utilizzare Unicode. Questo elenco è precompilato con i nomi di diverse applicazioni, il cui supporto è preconfigurato in PDF Generator. Se si sceglie di aggiungere il supporto per le conversioni PDF tramite altre applicazioni di terze parti che non supportano Unicode, è necessario aggiungerle a questo elenco. Il valore predefinito è Autocad,Excel,PowerPoint,Project,Publisher,Visio,Word,WordPerfect.

**Conteggio pool di thread del server:** controlla le dimensioni del pool di thread utilizzato internamente dal servizio Genera PDF per soddisfare le richieste di conversione da HTML a PDF che coinvolgono il spider (conversione di pagine collegate accessibili dalla pagina principale). Il valore predefinito è 20.

**Secondi di scansione pulizia PDFG:** per ulteriori informazioni, consulta la sezione Secondi scadenza processo .

**Secondi scadenza processo:** il servizio Generate PDF elimina i file di input non appena vengono convertiti. Memorizza temporaneamente i file di output, per un periodo di tempo determinato dalle impostazioni PDFG Cleanup Scan Seconds e Job Expiration Seconds.

L’impostazione Secondi scadenza processo specifica la data di scadenza di un file o di una cartella vuota prima che sia possibile eliminarlo. L&#39;impostazione PDFG Cleanup Scan Seconds specifica la frequenza con cui un thread di pulizia esegue la scansione delle cartelle temporanee per i file che possono essere eliminati.

Ad esempio, se l’opzione Secondi scadenza processo è impostata su 100 e i secondi di pulizia PDFG sono impostati su 200, il thread di pulizia viene eseguito ogni 200 secondi ed elimina i file che sono di almeno 100 secondi.

Il valore predefinito dei secondi di scansione della pulizia PDFG è `43200` (12 ore). Il valore predefinito dei secondi di scadenza del processo è `86400` (24 ore).

**Impostazioni internazionali predefinite:** utilizzato per sostituire le impostazioni internazionali predefinite (paese + lingua) del server in cui viene distribuito il servizio Generate PDF. Se questo parametro non è specificato, le impostazioni internazionali predefinite sono determinate dal sistema operativo in cui viene distribuito il servizio. Questo parametro controlla la lingua in cui i messaggi di errore vengono restituiti alle API.

## impostazioni del servizio Data Services del flusso di lavoro moduli {#forms-workflow-data-services-service-settings}

I seguenti servizi estendono i Servizi dati ed espongono gli assemblatori utilizzati da Workspace per comunicare con il server. Non modificare le opzioni di configurazione per questi servizi a meno che non venga richiesto dal supporto Adobe. Tali servizi non sono destinati all&#39;accesso diretto:

* `ProcessManagementLcdsAttachmentService`
* `ProcessManagementLcdsPropertyService`
* `ProcessManagementLcdsTaskService`

## Impostazioni del servizio remoto {#remoting-service-settings}

La maggior parte dei servizi è configurata in modo da potervi accedere tramite AEM moduli Remoting (obsoleto per i moduli AEM). Per informazioni su AEM moduli (obsoleti per i moduli AEM) Remoting, vedere [Programmazione con moduli AEM](https://adobe.com/go/learn_aemforms_programming_63).

Per il servizio Remoting sono disponibili le seguenti impostazioni.

**Metodo di autenticazione client Flex:** determina il tipo di risposta che il server invia al client quando il servizio richiamato è abilitato per la sicurezza, l&#39;operazione richiamata non supporta chiamate anonime e il client trasmette credenziali non valide o non valide. Scegli tra Personalizzato o Base. Il valore predefinito è Base.

**Consenti serializzazione di classi non serializzabili:** la maggior parte degli endpoint dei moduli AEM consentono solo l&#39;utilizzo di classi serializzabili per la chiamata. Nelle versioni precedenti, l&#39;endpoint Remoting consentiva l&#39;utilizzo di classi non serializzabili per la chiamata dai client basati su Flex. Per evitare una vulnerabilità di sicurezza descritta in APS11-15, questa è stata modificata. Se si desidera continuare a utilizzare classi non serializzabili con l&#39;endpoint Remoting di Flex, selezionare questa casella di controllo.

## Impostazioni del servizio Repository {#repository-service-settings}

Il servizio Repository ( `RepositoryService`) fornisce servizi di archiviazione e gestione delle risorse ai moduli AEM. Quando gli sviluppatori creano un’applicazione, possono distribuire le risorse nell’archivio anziché in un file system. Le risorse possono includere qualsiasi tipo di materiale collaterale, inclusi moduli XML, PDF forms (inclusi i moduli Acrobat), frammenti di modulo, immagini, profili, criteri, file SWF, file DDX, schemi XML, file WSDL e dati di test.

È possibile utilizzare l&#39;archivio predefinito incluso nei moduli AEM oppure un archivio di terze parti (EMC Documentum Content Server, IBM FileNet Content Manager o IBM Content Manager).

Il servizio Repository Provider è un delegato di servizio che funge da interfaccia a un servizio provider. Questo consente di connettersi a un&#39;API comune e non è necessario sapere quale servizio provider sta implementando le funzionalità di archiviazione. Il servizio Repository Provider fornisce la memorizzazione del database per le risorse del servizio Repository.

Per il servizio Repository è disponibile la seguente impostazione.

**Provider Service:** il nome del servizio utilizzato come provider di archiviazione. Il valore predefinito è RepositoryProviderService.

## Impostazioni del servizio Firma {#signature-service-settings}

Il servizio Firma ( `SignatureService`) consente alla tua organizzazione di proteggere la sicurezza e la privacy dei documenti Adobe PDF che distribuisce e riceve. Questo servizio utilizza le firme digitali e la certificazione per garantire che i documenti non vengano modificati. La modifica di un documento ne interrompe la firma. Poiché le caratteristiche di sicurezza sono applicate al documento stesso, il documento rimane protetto e controllato per l&#39;intero ciclo di vita; oltre il firewall, quando viene scaricato offline e quando viene inviato nuovamente all’organizzazione.

Per il servizio Firma sono disponibili le seguenti impostazioni.

**Nome del servizio SPI HSM remoto:** questa opzione è da utilizzare quando l&#39;HSM è installato su un computer remoto. Specificare questa opzione quando AEM moduli è installato in un Windows a 64 bit e si utilizzano dispositivi HSM per la firma.

**URL del servizio Web HSM remoto:** specifica questa opzione quando AEM moduli è installato su Windows a 64 bit e stai utilizzando dispositivi HSM per la firma.

**Certificazione per includere le modifiche al caricamento del modulo:** quando questa opzione è selezionata, lo stato del modulo XFA è certificato oltre al modello XFA. Tieni presente che l’abilitazione di questa opzione può avere un impatto negativo sulle prestazioni. Il valore predefinito è vero.

**Esegui script JavaScript di documento:** specifica se eseguire gli script JavaScript di documento durante le operazioni di firma. Il valore predefinito è false.

**Elabora documenti con compatibilità Acrobat 9:** specifica se abilitare la compatibilità Acrobat 9. Ad esempio, quando questa opzione è selezionata, la certificazione visibile nei PDF dinamici è abilitata. Il valore predefinito è false.

**Incorpora informazioni di revoca durante la firma:** specifica se le informazioni di revoca sono incorporate durante la firma del documento PDF. Il valore predefinito è false.

**Incorpora informazioni di revoca durante la certificazione:** specifica se le informazioni di revoca sono incorporate durante la certificazione del documento PDF. Il valore predefinito è false.

**Applica incorporazione delle informazioni di revoca per tutti i certificati durante la firma/la certificazione:** specifica se un&#39;operazione di firma o certificazione non riesce se non sono incorporate informazioni di revoca valide per tutti i certificati. Si noti che se un certificato non contiene informazioni CRL o OCSP, è considerato valido, anche se non vengono recuperate informazioni di revoca. Il valore predefinito è false.

**Ordine di controllo revoca:** specifica l’ordine del controllo di revoca quando il controllo è possibile tramite i meccanismi dell’elenco di revoca dei certificati (CRL) e del protocollo di stato dei certificati online (OCSP). Il valore predefinito è OCSPFirst.

**Dimensione Massima Delle Informazioni Di Archiviazione Della Revoca:** Dimensione Massima Delle Informazioni Di Archiviazione Della Revoca In kilobyte. AEM forms tenta di memorizzare il maggior numero possibile di informazioni di revoca senza superare il limite. Il valore predefinito è 10 KB.

**Supporto delle firme create dalle build di pre-rilascio dei prodotti di Adobe:** quando questa opzione è selezionata, la firma creata utilizzando la versione precedente al rilascio dei prodotti di Adobe verrà convalidata correttamente. Il valore predefinito è false.

**Opzione relativa al tempo di verifica:** specifica l’ora di verifica del certificato di un firmatario. Il valore predefinito è Secure Time Else Current Time (Tempo residuo protetto).

**Utilizzare le informazioni sulla revoca archiviate nella firma durante la convalida:** specifica se le informazioni sulla revoca archiviate con la firma vengono utilizzate per il controllo della revoca. Il valore predefinito è vero.

**Utilizzare le informazioni di convalida memorizzate nel documento per la convalida delle firme:** quando questa opzione è selezionata, le informazioni di convalida (comprese le informazioni di revoca e di marca temporale) incorporate nel documento vengono utilizzate per convalidare le firme. Il valore predefinito è vero.

**Numero massimo di sessioni di verifica nidificate consentite:** il numero massimo di sessioni di verifica nidificate consentite. AEM forms utilizza questo valore per evitare un ciclo infinito durante la verifica dei certificati di firma OCSP o CRL quando il certificato OCSP o CRL non è configurato correttamente. Il valore predefinito è 10.

**Inclinazione massima dell’orologio per la verifica:** il tempo massimo, in minuti, entro il quale il tempo di firma può essere trascorso il tempo di convalida. Se l’inclinazione dell’orologio è maggiore di questo valore, la firma non sarà valida. Il valore predefinito è 65 minuti.

**Cache del ciclo di vita del certificato:** la durata di un certificato, recuperato online o con altri metodi, nella cache. Il valore predefinito è 1 giorno.

### Opzioni di trasporto {#transport-options}

**Host proxy:** l&#39;URL dell&#39;host proxy. Utilizzato solo se viene fornito un valore valido. Nessun valore predefinito.

**Porta proxy:** la porta proxy. Digitare un numero di porta valido compreso tra 0 e 65535. Il valore predefinito è 80.

**Nome utente di accesso proxy:** il nome utente di accesso proxy. Utilizzato solo se viene fornito un valore valido per l&#39;host proxy e la porta proxy. Nessun valore predefinito.

**Password di accesso proxy:** password di accesso proxy. Utilizzato solo se viene fornito un valore valido per l&#39;host proxy, la porta proxy e il nome utente per l&#39;accesso proxy. Nessun valore predefinito.

**Limite massimo di download:** la quantità massima di dati, in MB, che può essere ricevuta per connessione. Il valore minimo è 1 MB e il valore massimo è 1024 MB. Il valore predefinito è 16 MB.

**Timeout connessione:** tempo massimo di attesa, in secondi, per stabilire una nuova connessione. Il valore minimo è 1 e il valore massimo è 300. Il valore predefinito è 5.

**Timeout socket:** tempo massimo di attesa, in secondi, prima che si verifichi un timeout del socket (in attesa del trasferimento dei dati). Il valore minimo è 1 e il valore massimo è 3600. Il valore predefinito è 30.

### Opzioni di convalida del percorso {#path-validation-options}

**Richiedi criterio esplicito:** specifica se il percorso deve essere valido per almeno uno dei criteri di certificato associati all&#39;ancoraggio di attendibilità del certificato del firmatario. Il valore predefinito è false.

**Inibisci criterio ANY:** specifica se l&#39;identificatore dell&#39;oggetto criterio (OID) deve essere elaborato se è incluso in un certificato. Il valore predefinito è false.

**Inibisci mappatura criteri:** specifica se la mappatura dei criteri è consentita nel percorso di certificazione. Il valore predefinito è false.

**Seleziona tutti i percorsi:** specifica se tutti i percorsi devono essere convalidati o se la convalida deve terminare dopo aver trovato il primo percorso valido. Selezionare true o false. Il valore predefinito è false.

**Server LDAP:** il server LDAP utilizzato per cercare i certificati per la convalida del percorso. Nessun valore predefinito.

**Segui gli URI nell’AIA del certificato:** specifica se gli URI (Uniform Resource Identifiers) nell’AIA del certificato vengono elaborati durante l’individuazione del percorso. Il valore predefinito è false.

**Estensione dei vincoli di base richiesta nei certificati CA:** specifica se l&#39;estensione del certificato dei vincoli di base dell&#39;autorità di certificazione (CA) deve essere presente per i certificati CA. Alcuni certificati radice certificati tedeschi precedenti (7 e versioni precedenti) non sono conformi alla RFC 3280 e non contengono l&#39;estensione del vincolo di base. Se è noto che il certificato EE di un utente si concentra su una radice tedesca di questo tipo, deselezionare questa casella di controllo. Il valore predefinito è vero.

**Richiedi firma certificato valida durante l&#39;edificio a catena:** specifica se il generatore a catena richiede firme valide sui certificati utilizzati per creare catene. Quando questa casella di controllo è selezionata, il generatore di catene non genererà catene con firme RSA non valide sui certificati. Considera la catena CA > ICA > EE in cui la firma della CA su un&#39;ICA non è valida. Se questa impostazione è vera, l&#39;edificio a catena si fermerà all&#39;ICA e la CA non sarà inclusa nella catena. Se questa impostazione è falsa, viene prodotta la catena di 3 certificati completa. Questa impostazione non influisce sulle firme DSA. Il valore predefinito è false.

### Opzioni provider di timestamp {#timestamp-provider-options}

**URL del server TSP:** l’URL del provider di marche temporali predefinito. Utilizzato solo se viene fornito un valore valido. Nessun valore predefinito.

**Nome utente del server TSP:** il nome utente, se richiesto dal provider di marche temporali. Utilizzato solo se viene fornito un valore valido per l’URL. Nessun valore predefinito.

**Password server TSP:** la password per il nome utente indicato sopra, se richiesta dal provider di timestamp. Utilizzato solo se vengono forniti alcuni valori validi per l’URL e il nome utente. Nessun valore predefinito.

**Algoritmo hash richiesta:** specifica l&#39;algoritmo di hash da utilizzare durante la creazione della richiesta per il provider di timestamp. Il valore predefinito è SHA1.

**Stile controllo revoca:** specifica lo stile del controllo di revoca utilizzato per determinare lo stato di attendibilità del certificato del provider di timestamp dal relativo stato di revoca osservato. Il valore predefinito è BestEffort.

**Send Nonce:** specifica se un nonce viene inviato con la richiesta del provider di timestamp. Un nonce può essere una marca temporale, un contatore di visite in una pagina web o un marcatore speciale inteso a limitare o impedire la riproduzione o riproduzione non autorizzata di un file. Il valore predefinito è vero.

**Usa marche temporali scadute durante la convalida:**  quando questa opzione è selezionata, è possibile utilizzare le marche temporali scadute per recuperare i tempi di convalida delle firme. Il valore predefinito è vero.

**Dimensioni di risposta TSP:** dimensione stimata, in byte, della risposta TSP. Questo valore deve rappresentare la dimensione massima della risposta timestamp che il provider di timestamp configurato potrebbe restituire. Non modificare questo a meno che tu non sia assolutamente sicuro. Il valore minimo è 60B e il valore massimo è 10240B. Il valore predefinito è 4096B.

**Ignora estensione** server TimeStamp: Selezionare l&#39;opzione  **Ignora** estensione server TimeStamp per impedire al server AEM Forms di contattare il server di marca temporale specificato. La selezione dell’opzione consente di evitare errori di processo che si verificano a causa del timeout della connessione tra AEM Forms e i server di marca temporale.

### Opzioni elenco di revoche di certificati {#certificate-revocation-list-options}

**Consultare Prima URI locale:** specifica se la posizione CRL fornita nell’URI locale o nella ricerca CRL deve avere la preferenza su qualsiasi posizione specificata all’interno di un certificato per il controllo di revoca. Il valore predefinito è false.

**URI locale per ricerca CRL:** URL del provider CRL locale. Questo valore viene consultato solo se l’impostazione Consult Local URI First è impostata su true. Nessun valore predefinito.

**Stile controllo revoca:** specifica lo stile del controllo di revoca utilizzato per determinare lo stato di attendibilità del certificato del provider CRL dal relativo stato di revoca osservato. Il valore predefinito è BestEffort.

**Server LDAP per ricerca CRL:** il server LDAP utilizzato per ottenere i CRL (come www.ldap.com). Tutte le query basate su DN per i CRL verranno indirizzate a questo server. Nessun valore predefinito.

**Vai online:** specifica se andare online per recuperare un CRL. Se false, vengono consultati solo i CRL memorizzati nella cache (sul disco locale o quelli incorporati con firma). Il valore predefinito è vero.

**Ignora date di validità:** specifica se ignorare i tempi thisUpdate e nextUpdate della risposta, il che impedisce a questi tempi di avere un effetto negativo sulla validità della risposta. Il valore predefinito è false.

**Richiedi estensione AKI in CRL:** specifica se l’estensione dell’identificativo chiave dell’autorità deve essere inclusa in un CRL. Il valore predefinito è false.

### Opzioni del protocollo di stato del certificato online {#online-certificate-status-protocol-options}

**URL del server OCSP:** URL per il server OCSP predefinito. L’utilizzo del server OCSP specificato tramite questo URL dipende dall’impostazione dell’opzione URL da consultare. Nessun valore predefinito.

**Opzione URL da consultare:** controlla l’elenco e l’ordine dei server OCSP utilizzati per eseguire il controllo dello stato. Il valore predefinito è UseAIAInCert.

**Stile controllo revoca:** specifica lo stile del controllo di revoca utilizzato durante la verifica del certificato del server OCSP. Il valore predefinito è CheckIfAvailable.

**Send Nonce:** specifica se un nonce viene inviato con la richiesta OCSP. Un nonce può essere una marca temporale, un contatore di visite in una pagina web o un marcatore speciale inteso a limitare o impedire la riproduzione o riproduzione non autorizzata di un file. Il valore predefinito è vero.

**Tempo massimo di inclinazione dell&#39;orologio:** inclinazione massima consentita, in minuti, tra il tempo di risposta e l&#39;ora locale. Il valore minimo è 0 e il valore massimo è 2147483647m. Il valore predefinito è 5m.

**Tempo di freschezza della risposta:** tempo massimo, in minuti, per il quale una risposta OCSP precostruita è considerata valida. Il valore minimo è 1m e il valore massimo consentito è 2147483647. Il valore predefinito è 525600 (un anno).

**Firma richiesta OCSP:** specifica se la richiesta OCSP deve essere firmata. Il valore predefinito è false.

**Alias delle credenziali del firmatario della richiesta:** specifica l&#39;alias delle credenziali da utilizzare per la firma della richiesta OCSP se la firma è abilitata. Utilizzato solo se la firma della richiesta OCSP è abilitata. Nessun valore predefinito.

**Vai online:** specifica se andare online per eseguire il controllo di revoca. Il valore predefinito è vero.

**Ignora i tempi thisUpdate e nextUpdate della risposta:** specifica se ignorare i tempi thisUpdate e nextUpdate della risposta, impedendo a questi tempi di avere un effetto negativo sulla validità della risposta. Il valore predefinito è false.

**Consenti estensione OCSPNoCheck:** specifica se l&#39;estensione OCSPNoCheck è consentita nel certificato di firma della risposta. Il valore predefinito è vero.

**Richiedi estensione OCSP ISIS-MTT CertHash:** specifica se nelle risposte OCSP deve essere inclusa un&#39;estensione dell&#39;hash della chiave pubblica del certificato. Il valore predefinito è false.

### Opzioni di gestione degli errori per il debug {#error-handling-options-for-debugging}

**Elimina cache certificati nella successiva chiamata API:** specifica se rimuovere la cache dei certificati quando viene chiamata la successiva operazione Servizio firme. Dopo la chiamata dell&#39;operazione, questa opzione viene reimpostata su false. Il valore predefinito è false.

**Elimina la cache CRL nella successiva chiamata API:** specifica se rimuovere la cache CRL quando viene chiamata la successiva operazione del servizio Firma. Dopo la chiamata dell&#39;operazione, questa opzione viene reimpostata su false. Il valore predefinito è false.

**Elimina la cache OCSP dalla successiva chiamata API:** specifica se rimuovere la cache OCSP quando viene chiamata la successiva operazione Servizio firme. Dopo la chiamata dell&#39;operazione, questa opzione viene reimpostata su false. Il valore predefinito è false.

## Impostazioni del servizio Cartelle controllate {#watched-folder-service-settings}

Il servizio Cartella controllata ( `WatchedFolder`) configura gli attributi comuni per tutti gli endpoint cartelle controllati. Fornisce inoltre valori predefiniti per gli endpoint di cartelle controllati. (Consulta [Configurazione degli endpoint per cartelle controllate](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints).) Non viene richiamato da applicazioni client esterne o utilizzato nei processi creati in Workbench.

Per il servizio Cartella controllata sono disponibili le seguenti impostazioni.

**Espressione Cron:** l&#39;espressione cron utilizzata dal quarzo per pianificare il polling della directory di input.

**Ripeti conteggio:** il numero di volte in cui viene effettuato il polling della directory di input. Il conteggio di ripetizione predefinito da utilizzare se questo valore non è specificato nella configurazione dell’endpoint. Il valore -1 indica una scansione indefinita della directory. Il valore predefinito è -1.

**Intervallo di ripetizione:** il numero predefinito, se secondi, tra ciascun sondaggio. Questo valore viene utilizzato come intervallo di ripetizione a meno che non venga specificato un valore diverso nella configurazione dell’endpoint della cartella controllata. Il valore predefinito è 5. Per ulteriori informazioni, consulta la descrizione dell’impostazione Dimensione batch .

**Asincrono:** identifica il tipo di chiamata come asincrono o sincrono. I processi transitori e sincroni possono essere richiamati solo in modo sincrono. Il valore predefinito è asincrono.

**Tempo di attesa:** il valore predefinito per il tempo, in secondi, dopo il quale i file vengono recuperati dalle cartelle di input. Se il file o la cartella è più vecchia del tempo specificato nel tempo di attesa, viene selezionata per l’elaborazione. Il valore predefinito è 0.

**Dimensione batch:** il valore predefinito per il numero di file o cartelle elaborati per scansione. Il valore predefinito è 2.

Le impostazioni Intervallo di ripetizione e Dimensione batch determinano il numero di file recuperati da Cartella osservata in ogni scansione. Cartella osservata utilizza un pool di thread Quartz per eseguire la scansione della cartella di input. Il pool di thread è condiviso con altri servizi. Se l’intervallo di scansione è piccolo, i thread eseguono spesso la scansione della cartella di input. Se i file vengono eliminati frequentemente nella cartella controllata, mantenere l&#39;intervallo di scansione ridotto. Se i file vengono eliminati raramente, utilizza un intervallo di scansione più ampio in modo che gli altri servizi possano utilizzare i thread.

Se c&#39;è un grande volume di file da eliminare, rendere la dimensione del batch grande. Ad esempio, se il servizio richiamato dall&#39;endpoint della cartella controllata può elaborare 700 file al minuto e gli utenti rilasciano i file nella cartella di input allo stesso ritmo, impostando Dimensione batch su 350 e Intervallo di ripetizione su 30 secondi sarà più facile monitorare le prestazioni della cartella senza incorrere troppo spesso nel costo di scansione della cartella controllata.

Quando i file vengono rilasciati nella cartella controllata, elenca i file nell’input, il che può ridurre le prestazioni se la scansione si verifica ogni secondo. L&#39;aumento dell&#39;intervallo di scansione può migliorare le prestazioni. Se il volume dei file da rilasciare è piccolo, regolare di conseguenza le dimensioni del batch e l&#39;intervallo di ripetizione. Ad esempio, se vengono eliminati 10 file al secondo, provare a impostare l&#39;intervallo di ripetizione su 1 secondo e la dimensione batch su 10.

In una configurazione del cluster, la dimensione batch per un endpoint di cartelle controllate non viene ridimensionata in più nodi del cluster. Ad esempio, se la dimensione del batch è impostata su `2` per un cluster a due nodi e l&#39;opzione Limita è selezionata, i nodi elaborano i file collettivamente in batch di due anziché ogni nodo elaborando due file alla volta.

**Sovrascrivi nomi di file duplicati:** una stringa booleana che specifica se la cartella controllata sovrascrive i nomi dei file dei risultati duplicati e se i documenti conservati con lo stesso nome devono essere sovrascritti.

**Mantieni cartella:** il valore predefinito per la cartella preserve. Questa cartella viene utilizzata per copiare i file di origine in in caso di elaborazione corretta dell’input. Questo valore può essere un percorso vuoto, relativo o assoluto con un pattern di file come descritto per l’impostazione Cartella risultati.

**Cartella degli errori:** il nome della cartella in cui vengono copiati i file degli errori. Questo valore può essere un percorso vuoto, relativo o assoluto con un pattern di file come descritto per l’impostazione Cartella risultati.

**Cartella risultati:** il nome predefinito per la cartella dei risultati. Questa cartella viene utilizzata per copiare i file dei risultati in . Questo valore può essere un percorso vuoto, relativo o assoluto con il seguente pattern di file.

* %F = prefisso del nome del file
* %E = estensione del nome file
* %Y = anno (completo)
* %y = anno (ultime due cifre)
* %M = mese
* %D = giorno del mese
* %d = giorno dell&#39;anno
* %H = ora (24 ore)
* %h = ora (12 ore)
* %m = minuto
* %s = secondo
* %l = millisecondi
* %R = numero casuale (da 0 a 9)
* %P = ID processo o processo

Ad esempio, se il 17 luglio 2009 è alle 20:09 e si specifica `C:/Test/WF0/failure/%Y/%M/%D/%H/`, la cartella dei risultati sarà `C:/Test/WF0/failure/2009/07/17/20`.

Se il percorso non è assoluto ma relativo, la cartella viene creata all’interno della cartella controllata. Per ulteriori informazioni sui pattern di file, vedere [Informazioni sui pattern di file](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).

>[!NOTE]
>
>Minore è la dimensione delle cartelle dei risultati, migliore sarà la prestazione di Watched Folder. Ad esempio, se il carico stimato per la cartella controllata è di 1000 file all’ora, prova un pattern come `result/%Y%M%D%H` in modo che venga creata una nuova sottocartella ogni ora. Se il carico è più piccolo (ad esempio, 1000 file al giorno), puoi utilizzare un pattern come `result/%Y%M%D`.

**Cartella stage:** il nome predefinito per la cartella dell’area di visualizzazione all’interno della cartella controllata.

**Cartella di input:** il nome predefinito per la cartella di input all’interno della cartella controllata.

**Mantieni in caso di errore:** se true, i file originali vengono mantenuti nella cartella degli errori in caso di errore.

**Limita:** quando questa opzione è selezionata, limita il numero di processi di cartelle controllati che AEM i processi dei moduli in un dato momento. Il valore Dimensione batch determina il numero massimo di processi (vedere Informazioni sulla limitazione).

## Impostazioni del servizio Web {#web-service-service-settings}

Il servizio Web Service ( `WebService`) consente ai processi di richiamare le operazioni del servizio Web.

Il servizio Web Service consente ai processi di richiamare le operazioni del servizio Web. Ad esempio, un&#39;organizzazione può voler integrare un processo per memorizzare e recuperare informazioni quali i dettagli dei contatti e degli account richiamando i servizi Web esposti di un fornitore di servizi. Il servizio Web richiama un servizio Web specificato e trasmette i valori di ciascuno dei suoi parametri. Quindi salva i valori restituiti dall&#39;operazione in una variabile designata all&#39;interno di un processo.

Il servizio Web Service interagisce con i servizi Web inviando e ricevendo messaggi SOAP. Il servizio supporta anche l’invio di allegati MIME, MTOM e SwaRef con messaggi SOAP utilizzando il protocollo WS-Attachment. Le interazioni del servizio Web sono compatibili con i sistemi SAP e i servizi Web .NET.

Per il servizio Web Service sono disponibili le seguenti impostazioni.

**Archivio chiavi:** il percorso completo del file dell&#39;archivio chiavi che contiene la chiave privata da utilizzare per l&#39;autenticazione. Il server dei moduli deve essere in grado di accedere al file .

**Password archivio chiavi:** la password per il file dell&#39;archivio chiavi.

**Tipo archivio chiavi:** il tipo di archivio chiavi. Non fornire alcun valore per utilizzare il tipo di archivio chiavi predefinito configurato per la JVM che esegue il server dei moduli. In caso contrario, specificare uno dei seguenti valori:

* jks
* pkcs12
* cms
* scemo

**Trust Store:** percorso completo del file dell&#39;archivio attendibilità contenente la chiave pubblica del server del servizio Web.

**Password archivio attendibile:** password per il file truststore.

**Tipo archivio trust:** il tipo di truststore. Non fornire alcun valore per utilizzare il tipo di archivio chiavi predefinito configurato per la JVM che esegue il server dei moduli. In caso contrario, specificare uno dei seguenti valori:

* jks
* pkcs12
* cms
* scemo

## Impostazioni del servizio di trasformazione XSLT {#xslt-transformation-service-settings}

Il servizio di trasformazione XSLT ( `XSLTService`) consente ai processi di applicare trasformazioni XSLT (Extensible Stylesheet Language Transformations) sui documenti XML.

Per il servizio Trasformazione XSLT è disponibile la seguente impostazione.

**Nome di fabbrica:** il nome completo della classe Java da utilizzare per l&#39;esecuzione delle trasformazioni XSLT. Se non viene specificato alcun valore, viene utilizzata la fabbrica predefinita configurata in Java Virtual Machine che esegue il server dei moduli.

## Modifica delle impostazioni di protezione per un servizio {#modifying-security-settings-for-a-service}

il server forms consente di configurare le impostazioni di protezione per ogni servizio, che consentono di configurare un controllo di accesso dettagliato a livello di servizio.

Vengono installati i profili di sicurezza predefiniti, che possono quindi essere configurati per soddisfare le esigenze del sistema. Ogni profilo di sicurezza ha un dominio associato e viene creato a livello di utente o di gruppo.

### Modifica delle impostazioni di protezione per un servizio {#modify-security-settings-for-a-service}

1. Nella console di amministrazione, fare clic su Servizi > Applicazioni e servizi > Gestione dei servizi.
1. Nella pagina Gestione dei servizi fare clic sul servizio da configurare.
1. Fare clic sulla scheda Protezione.
1. Nell’elenco Richiedi ai chiamanti di eseguire l’autenticazione, selezionare Sì o No per specificare se il servizio può essere richiamato con o senza credenziali.

   Se si seleziona Sì, il chiamante del servizio deve essere autenticato e l&#39;entità utente per quel chiamante deve essere autorizzata a richiamare il servizio; altrimenti, il tentativo di invocazione verrà rifiutato.

   Se si seleziona No, il chiamante del servizio potrebbe essere autenticato o meno. L&#39;invocazione del servizio avrà sempre successo perché non vi è alcun controllo di autorizzazione.

1. Per i servizi che contengono una o più operazioni contrassegnate per l&#39;accesso anonimo, selezionare o deselezionare Accesso anonimo consentito. Quando l&#39;accesso anonimo è abilitato, qualsiasi utente all&#39;interno del sistema può richiamare operazioni sul servizio. Se l’accesso anonimo è disabilitato, gli utenti devono ottenere l’autorizzazione per chiamare il servizio e richiamare le operazioni. Agli utenti vengono concesse queste autorizzazioni direttamente o come parte di un gruppo che dispone di tali autorizzazioni.
1. Per alcuni servizi, l’account utente che esegue l’operazione influisce sui risultati. Ad esempio, in Content Services (obsoleto), l’utente che memorizza il contenuto diventa il proprietario del contenuto, il che influisce su chi può successivamente accedere al contenuto. Se si utilizza un processo per archiviare il contenuto, è consigliabile considerare l&#39;utente utilizzato per eseguire il servizio Gestione documenti, in quanto tale utente sarà proprietario del contenuto memorizzato.

   Per specificare l&#39;identità di esecuzione utilizzata da un servizio per eseguire le operazioni, selezionare Specifica esecuzione con nome, selezionare un&#39;opzione dall&#39;elenco associato, quindi fare clic su Salva. Scegli tra le seguenti opzioni:

   **Invoker:** utilizza la stessa identità dell’utente che ha richiamato il servizio.

   **Sistema:** utilizza l&#39;utente di sistema per eseguire il servizio con privilegi completi.

   **Utente con nome:** consente di eseguire il servizio come utente specifico. Quando selezioni questa opzione, fai clic su Seleziona utente per visualizzare la pagina Seleziona principale , in cui puoi cercare e selezionare l&#39;utente.

   Se non si seleziona Specifica esecuzione con nome, viene utilizzato il comportamento predefinito.

   >[!NOTE]
   >
   >I servizi di rendering e invio utilizzati con variabili xfaForm, Document Form e Form vengono sempre eseguiti utilizzando l&#39;account utente System.

1. Fai clic su Aggiungi entità per specificare le autorizzazioni di cui dispongono utenti e gruppi per questo servizio.
1. Nella schermata Seleziona principale sono visualizzati gli utenti e i gruppi configurati in Gestione utente. Se l&#39;utente o il gruppo desiderato non è visualizzato, utilizzare la funzione di ricerca per trovarlo. Fare clic sul nome di un utente o di un gruppo.
1. Nella schermata Aggiungi autorizzazioni , seleziona le autorizzazioni da assegnare all&#39;utente o al gruppo per questo servizio:

   * **INVOKE_PERM:** Per richiamare tutte le operazioni sul servizio
   * **MODIFY_CONFIG_PERM:** Per modificare la configurazione di un servizio
   * **SUPERVISOR_PERM:** Per visualizzare i dati delle istanze del processo per un servizio creato da un processo
   * **START_STOP_PERM:** Per avviare e interrompere un servizio
   * **ADD_REMOVE_ENDPOINTS_PERM:** Aggiungere, rimuovere e modificare gli endpoint di un servizio
   * **CREATE_VERSION_PERM:** Per creare una nuova versione del servizio
   * **DELETE_VERSION_PERM:** Per eliminare una versione del servizio
   * **MODIFY_VERSION_PERM:** Per modificare una versione del servizio
   * **READ_PERM:** Per visualizzare il servizio
   * **PROCESS_OWNER_PERM:** da utilizzare in una versione futura dei moduli AEM. Non utilizzare questa autorizzazione.
   * **SERVICE_MANAGER_PERM:** da utilizzare in una versione futura dei moduli AEM. Non utilizzare questa autorizzazione.
   * **SERVICE_AGENT_PERM:** da utilizzare in una versione futura dei moduli AEM. Non utilizzare questa autorizzazione.

1. Fate clic su Aggiungi.

### Rimuovere l&#39;entità da un profilo di sicurezza {#remove-the-principal-from-a-security-profile}

1. Nella pagina Gestione dei servizi , seleziona il servizio da configurare.
1. Fare clic sulla scheda **Sicurezza**, selezionare il profilo di protezione da rimuovere e fare clic su **Rimuovi**.

## Configurazione del pool per un servizio {#configuring-pooling-for-a-service}

Ogni servizio può sfruttare le funzionalità di raggruppamento per gestire le richieste di chiamata in arrivo. L&#39;utilizzo di un pool di servizi assicura che le istanze del servizio vengano richiamate da un singolo thread alla volta e riutilizzate tra le richieste di chiamata, il che può comportare un miglioramento delle prestazioni. È inoltre possibile utilizzare il pool per specificare l’opzione Massimo istanze di servizio asincrone, che consente ai servizi di limitare il numero di richieste gestite in parallelo.

### Abilita pooling {#enable-pooling}

1. Nella console di amministrazione, fare clic su Servizi > Applicazioni e servizi > Gestione dei servizi.
1. Nella pagina Gestione dei servizi fare clic sul servizio da configurare.
1. Fare clic sulla scheda Pool.
1. Nell’elenco Strategia di elaborazione delle richieste, selezionare Istanze in pool per tutte le richieste.
1. Nella casella Dimensioni pool istanza servizio iniziale immettere la dimensione iniziale del pool. Quando il servizio viene distribuito, questo numero viene utilizzato per determinare il numero di istanze di implementazione del servizio create e allocate al pool gratuito, in attesa di richieste di chiamata. Questo consente al contenitore di servizi di rispondere immediatamente alle richieste di chiamata senza dover prima inizializzare un&#39;istanza di servizio.
1. Nella casella Dimensione massima pool di istanze del servizio immettere il numero massimo di istanze nel pool per un determinato servizio. Questa impostazione controlla il numero di thread che possono eseguire un determinato servizio in un dato momento. Il valore predefinito è 0, che determina una dimensione illimitata del pool.
1. Nella casella Istanze di servizio asincrono massime immettere il numero massimo di istanze del pool che possono essere utilizzate per il servizio delle richieste asincrone in un dato momento. Questa impostazione consente al servizio di limitare il numero di richieste che può gestire in parallelo.
1. Nella casella Timeout attesa chiamata, immettere il numero di millisecondi di attesa che un servizio diventi disponibile per una richiesta di chiamata. Se non si specifica un valore per questa impostazione, il valore predefinito è 0, il che non comporta tempi di attesa.
1. Fai clic su Salva.

### Rimuovi pooling {#remove-pooling}

1. Nella console di amministrazione, fare clic su Servizi > Applicazioni e servizi > Gestione dei servizi.
1. Nella pagina Gestione dei servizi fare clic sul servizio da configurare.
1. Fare clic sulla scheda Pool.
1. Nell’elenco Strategia di elaborazione delle richieste, selezionare Nuova istanza per ogni richiesta o Istanza singola per tutte le richieste.

   **Istanza singola per tutte le richieste:** viene creata e memorizzata nella cache un&#39;istanza del servizio quando la prima richiesta viene inserita nel contenitore. Ogni richiesta successiva utilizza la stessa istanza di servizio per gestire la richiesta.

   **Nuova istanza per ogni richiesta:** viene creata una nuova istanza di servizio per ogni chiamata ricevuta.

1. Fai clic su Salva.
