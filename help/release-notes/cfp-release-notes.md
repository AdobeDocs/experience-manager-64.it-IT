---
title: Note sulla versione AEM 6.4 Cumulative Fix Pack
description: Note sulla versione specifiche di Adobe Experience Manager 6.4 Cumulative Fix Pack.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 7c19ef4a56fbfaa2f43b71e4dc48c79f797f32a8
workflow-type: tm+mt
source-wordcount: '4680'
ht-degree: 15%

---


# Note sulla versione AEM 6.4 Cumulative Fix Pack {#aem-cumulative-fix-pack-release-notes}

## Informazioni sulla versione {#release-information}

<!-- TBD: Update the SD URL. -->

| Prodotti | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versione | 6.4.8.4 |
| Tipo | Cumulative Fix Pack |
| Data | 25 febbraio 2021 |
| Prerequisito | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL di download | [Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## Funzionalità incluse in AEM 6.4.8.4 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.4 è un aggiornamento importante che include diverse correzioni di problemi interni e segnalati dai clienti, introdotte successivamente alla data di disponibilità generale di AEM 6.4 Service Pack 8 (6.4.8.0) nel marzo 2020.

AEM 6.4.8.4 è un Cumulative Fix Pack (CFP) che dipende da AEM 6.4 Service Pack 8. Installa il CFP dopo aver installato AEM 6.4 Service Pack 8.

Le funzioni chiave e i miglioramenti introdotti in [!DNL Adobe Experience Manager] 6.4.8.4 sono i seguenti:

* Possibilità di abilitare o disabilitare le modifiche del Registro di sistema [!DNL Experience Manager Forms] durante l&#39;esecuzione di una conversione PDFG.

* Autenticazione basata su certificato X-509 per i servizi web basati su SOAP nel modello per dati modulo.

* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.24.

Per informazioni sui CFP e su altri tipi di rilasci, consulta [Definizioni dei veicoli di rilascio degli aggiornamenti di AEM](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html?lang=en)

Adobe Experience Manager 6.4.8.4 fornisce correzioni per i seguenti problemi.

### Sites {#sites-6484}

* Dopo aver installato Experience Manager Service Pack 6.4.8.2, gli utenti non possono modificare i modelli di frammento di contenuto ed è stato rilevato il seguente errore:

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* Quando un utente fa clic sul pulsante di disconnessione, l&#39;utente non viene disconnesso da Gestione pacchetti. (NPR-35161)
* Dopo l’aggiornamento da Experience Manager 6.4.x a Experience Manager 6.4.8.3, gli utenti non possono pubblicare una pagina tramite Gestisci pubblicazione. (CQ-4312511)
* Quando si sposta nuovamente una pagina figlio blueprint nella posizione originale, la configurazione cq:liveSyncConfig non viene rimossa da una pagina figlia Live Copy. (NPR-35900)
* Quando sposti una blueprint con Live Copy avanti e indietro, funziona solo il primo spostamento, non riesce e non viene visualizzato alcun messaggio di errore. (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` causa  `OutOfMemoryError` errori poiché la funzionalità di assegnazione tag avanzati crea  `/oak:index/lucene` indici  `/oak:index/ntBaseLucene` e grandi dimensioni (NPR-35650).
* Gli utenti non possono archiviare le risorse dopo aver modificato quelle in [!DNL Adobe InDesign] e ricevono un errore per mancanza di autorizzazioni (NPR-35340).
* Quando viene creata una nuova versione di una risorsa esistente dopo la risoluzione del conflitto di denominazione, i metadati della risorsa originale vengono sovrascritti (NPR-35939).
* I gruppi generati automaticamente dalla cartella privata non vengono mantenuti e non vengono rimossi quando si elimina la cartella o si aggiorna la cartella con l&#39;opzione [!UICONTROL Rimuovi restrizioni cartella privata] impostata (NPR-35625).

#### [!DNL Dynamic Media] {#dynamic-media}

* L&#39;errore ImageServer intermittente causa la risposta 403 per un errore conseguente di alcune funzionalità di [!DNL Experience Manager]. (CQ-4308565)

### Integrazioni {#integrations-6484}

* Quando apri le proprietà di una pagina dopo l’aggiornamento a Experience Manager 6.4.8.3, gli errori JavaScript iniziano a comparire nella console (NPR-35649).

### Forms {#forms-6484}

>[!NOTE]
>
>Per [!DNL Experience Manager Forms] vengono rilasciati pacchetti del componente aggiuntivo una settimana dopo la data di rilascio pianificata per il Cumulative Fix Pack di [!DNL Experience Manager].

**Gestione della corrispondenza**

* Quando si modifica una lettera, il caricamento dei moduli con condizioni richiede un tempo maggiore (NPR-35326).

* Durante la modifica di una lettera, i binding dei contenuti e dei dati non vengono visualizzati nell’interfaccia utente (CQ-4312905).

**Servizi documentali**

* Impossibile assemblare i PDF dopo l&#39;aggiornamento da [!DNL JAVA] a [!DNL JDK1.8.0_261] (NPR-35761, NPR-35848).

**JEE per Foundation**

* Quando si modifica una notifica di attività nel flusso di lavoro [!DNL Forms], non è possibile salvarla (CQ-4315055).

Per informazioni sugli aggiornamenti di sicurezza, consulta la [pagina dei bollettini sulla sicurezza di Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## Hotfix e Feature Pack inclusi nei Cumulative Fix Pack precedenti {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM Cumulative Fix Pack 6.4.8.3 è un aggiornamento importante che include diverse correzioni di problemi interni e segnalati dai clienti, introdotte successivamente alla data di disponibilità generale di AEM 6.4 Service Pack 8 (6.4.8.0) nel marzo 2020.

AEM 6.4.8.3 è un Cumulative Fix Pack (CFP) che dipende da AEM 6.4 Service Pack 8. Installa il CFP dopo aver installato AEM 6.4 Service Pack 8.

In AEM 6.4.8.3, l’archivio incorporato (Apache Jackrabbit Oak) viene aggiornato alla versione 1.8.23.

Per informazioni sui CFP e su altri tipi di rilasci, consulta [Definizioni dei veicoli di rilascio degli aggiornamenti di AEM](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.3 fornisce correzioni per i seguenti problemi.

#### Siti {#sites-6483}

* Quando aggiorni il testo di una variante di un frammento di contenuto, il contenuto del frammento di contenuto principale viene aggiornato al posto della variante (NPR-35080).

* Quando si imposta un valore numerico per la proprietà etichetta di tipo stringa di un componente, lo si elimina e si utilizza l’opzione Annulla per riportarlo indietro, il tipo di proprietà etichetta cambia automaticamente da Stringa a Lungo (NPR-34738).

* Quando aggiungi un componente Caricamento file a più campi, il percorso immagine viene memorizzato nel nodo del componente invece del nodo Multicampo (NPR-34423).

* Nella procedura guidata Sposta pagina, anche se non è selezionata alcuna destinazione, il pulsante successivo rimane attivato (NPR-34460).

* Quando il componente principale include la proprietà `cq:isContainer` , il componente ereditato non include automaticamente la proprietà (CQ-4308409).

* Quando utilizzi la minimizzazione CSS utilizzando la funzione `calc()`, gli spazi vuoti intorno al segno `+` vengono rimossi (NPR-34991).

* Quando avvii un&#39;istanza AEM, i componenti `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` e `com.adobe.granite.maintenance.impl.TaskScheduler` non vengono visualizzati in stato `Active` (NPR-34952).

#### [!DNL Assets] {#assets-6483}

* Quando crei una versione di una risorsa esistente, gli aggiornamenti utente ai metadati non persistono se alla cartella viene applicato un profilo di metadati (NPR-34833).
* Quando si utilizza [!DNL Adobe Asset Link] con [!DNL Adobe InDesign], i risultati della ricerca non contengono cartelle e raccolte ma contengono solo risorse (NPR-34700).
* Quando si trascina una risorsa su una cartella per spostarla, l’interfaccia utente visualizza anche l’opzione [!UICONTROL Rilascia in Lightbox] e [!UICONTROL Rilascia in raccolta]. Anche se l&#39;operazione di spostamento viene annullata, l&#39;interfaccia utente continua a visualizzare le ultime due opzioni (NPR-34525).
* Quando l’interfaccia Gestisci pubblicazione è aperta, l’opzione di pubblicazione non è disponibile e selezionando l’opzione Annulla pubblicazione la pagina dell’ambito è vuota (CQ-4302509).

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* Nelle impostazioni dei predefiniti per immagini, quando l&#39;opzione [!UICONTROL Abilita JPG Chrominance Downsampling] è deselezionata in [!DNL Experience Manager], la modifica non viene sincronizzata con [!DNL Dynamic Media] (NPR-34284).
* Nel [!UICONTROL Editor predefiniti visualizzatore], quando si modifica il predefinito [!UICONTROL PanoramicImage/PanoramicImage_VR], nel componente `PanoramicView` l&#39;etichetta del modificatore `PANORAMICVIEW_AUTOROTATE` non è disponibile (CQ-4302043).
* L’annullamento della pubblicazione di un video da [!DNL Experience Manager] non annulla la pubblicazione del set di video adattivi su Dynamic Media Classic configurato. (CQ-4304405).

#### Platform {#platform-6483}

* Il flag `emitUseStrict` viene aggiunto alla funzione del processore Google Closure Compiler (GCC) `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. Il flag sopprime l&#39;output dell&#39;istruzione `use strict` (NPR-34830).
* Viene restituito un `NullPointerException` all&#39;avvio di attività di manutenzione giornaliere o settimanali (NPR-34702).
* Lo strumento [!DNL Apache Sling Health Check] è obsoleto. Utilizza invece [Rilevatore pattern](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html) per rilevare le violazioni dei contenuti (NPR-33929).

#### Integrazioni {#integrations-6483}

* Il pulsante [!UICONTROL Crea] viene visualizzato nella pagina [!UICONTROL Tipi di pubblico] quando si passa da una cartella alla pagina [!UICONTROL Tipi di pubblico] (NPR-35152).

#### Interfaccia utente {#ui-6483}

* Il pannello di ricerca [!UICONTROL Filtri] nell&#39;interfaccia utente [!UICONTROL Omnisearch] restituisce anche risultati da posizioni diverse da quelle da cui viene eseguita la ricerca (NPR-34877).
* Alla chiusura del pannello [!UICONTROL Filtri] sull&#39;interfaccia utente [!UICONTROL Omnisearch], la barra a sinistra non viene reimpostata sulla selezione [!UICONTROL Contenuto], il che impedisce la riapertura del pannello [!UICONTROL Filtri] (NPR-34483).
* All’accesso alle proprietà della pagina viene restituito un `NullPointerException` (NPR-34509).

#### Communities {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* Tutti i casi di terminologia iniqua nel prodotto sono sostituiti con equivalenti accettati (NPR-34506).

#### Commerce {#commerce-6483}

* Quando in una collezione sono presenti più di 15 prodotti, la collezione visualizza solo i primi 15 prodotti (NPR-34494).

#### Moduli {#forms-6483}

>[!NOTE]
>
>Per [!DNL Experience Manager Forms] vengono rilasciati pacchetti del componente aggiuntivo una settimana dopo la data di rilascio pianificata per il Cumulative Fix Pack di [!DNL Experience Manager].

>[!NOTE]
>
>[!DNL Experience Manager] Cumulative Fix Pack non include correzioni per  [!DNL Experience Manager Forms]. Vengono distribuite utilizzando un pacchetto aggiuntivo [!DNL Forms] separato. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per [!DNL Experience Manager Forms] su JEE. Per ulteriori informazioni, consulta [Installare il pacchetto aggiuntivo di AEM Forms](#install-aem-forms-add-on-package) e [Installare il programma di installazione di JEE per AEM Forms](#install-aem-forms-jee-installer).

**Moduli adattivi**

* Impossibile modificare un modulo adattivo utilizzando l’interfaccia classica dopo l’applicazione del pacchetto di correzioni cumulativo [!DNL Experience Manager] (NPR-35127).

* Il caricamento dei frammenti in un modulo adattivo richiede più tempo a causa dell’annullamento della validità della cache (NPR-34655).

* Accessibilità: La navigazione a schede non funziona correttamente per gli assistenti vocali in un modulo adattivo (NPR-34550).

**Gestione della corrispondenza**

* Quando esegui la migrazione delle risorse da ES3, le risorse includono due condizioni predefinite non modificabili (NPR-34971).

**JEE per Foundation**

* Migrare [!DNL AEM Forms] utenti da Flash a HTML (CQ-4304075).

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2 è un aggiornamento importante che include diverse correzioni di problemi interni e segnalati dai clienti, introdotte successivamente alla data di disponibilità generale di AEM 6.4 Service Pack 8 (6.4.8.0) nel marzo 2020.

AEM 6.4.8.2 è un Cumulative Fix Pack (CFP) che dipende da AEM 6.4 Service Pack 8. Installa il CFP dopo aver installato AEM 6.4 Service Pack 8.

In AEM 6.4.8.2, l’archivio incorporato (Apache Jackrabbit Oak) viene aggiornato alla versione 1.8.22.

Per informazioni sui CFP e su altri tipi di rilasci, consulta [Definizioni dei veicoli di rilascio degli aggiornamenti di AEM](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.2 fornisce correzioni per i seguenti problemi.

#### Siti {#sites-6482}

* Se il `RolloutConfigManagerFactoryImpl` non è in grado di caricare una configurazione di rollout, non tenta di caricare le configurazioni mancanti. Restituisce le configurazioni memorizzate nella cache (NPR-34091).
* Nel componente di base Testo, dopo aver utilizzato l’opzione di modifica HTML di origine, la classe dal tag `em` viene rimossa (NPR-34080).
* Quando esegui l’aggiornamento da Experience Manager 6.2 a Experience Manager 6.5, il componente Parsys dei modelli statici non viene visualizzato correttamente. L’altezza del componente Parsys è impostata su 0 e i componenti al suo interno non sono visibili (NPR-34044).
* Le informazioni sull’etichetta non vengono visualizzate sui componenti consentiti all’interno dell’Editor modelli (NPR-33908).

   ![Etichette mancanti nel contenitore di layout](assets/33908_missing_labels.png)

* Gli utenti non sono in grado di aggiungere o modificare componenti all’elemento parsys dopo il quarto livello dei componenti nidificati (NPR-33873).
* Se il contenuto iniziale di un modello modificabile viene modificato e il modello viene pubblicato, tutte le nuove pagine create con questo modello mostrano la data di pubblicazione del modello, anche se le pagine non vengono pubblicate (NPR-33822).
* Le proprietà `cq:acLinks` e `cq:acUUID` per [!DNL Adobe Campaign] nella copia vengono rimosse durante l&#39;operazione di copia e incolla (NPR-33793).
* Nella scheda [!UICONTROL Uso live] vengono visualizzati solo 49 risultati. Non mostra tutto l’utilizzo del componente (NPR-33710).
* Una pagina web con carattere `/` nell’URL non risponde durante l’authoring. Quando viene aggiunto un componente durante l&#39;authoring, l&#39;utilizzo della CPU aumenta e il browser smette di rispondere (NPR-33625).
* In modalità di modifica in linea in [!DNL RTE], il trascinamento di un’immagine non funziona per il componente Testo (NPR-33579).
* È possibile creare un componente in una pagina blueprint con lo stesso nome della pagina. Durante il rollout, tale componente viene rinominato con suffisso `_msm_moved`. Tuttavia, il componente viene spostato alla fine del [!UICONTROL Sistema paragrafo] (NPR-33534).
* La promozione Launch non pubblica le pagine quando la proprietà [!UICONTROL include subpages] non è selezionata nella prima directory principale del contenuto (NPR-33533).
* Il reindirizzamento alla pagina [!DNL Experience Manager] con ancoraggio non funziona sull&#39;istanza di authoring perché `PageRedirectServlets` inserisce la stringa di query dopo un frammento URL o un ancoraggio (NPR-34287).
* `PageRedirectServlet` viene aggiunto  `.html` dopo la mappatura Sling che porta a errori di collegamento (NPR-34271).
* Puoi sospendere la sezione [!DNL Live Copy] di una pagina e l’ereditarietà viene interrotta come mostrato nella modalità Editor. Tuttavia, nelle proprietà Pagina, l’icona che rappresenta l’ereditarietà indica in modo errato che l’ereditarietà esiste e non è interrotta (NPR-34096).
* Problema relativo alla visualizzazione dei componenti consentiti nella pagina Modifica modello (CQ-4297295).
* Dopo l&#39;aggiornamento di Chrome e Firefox, i menu a comparsa non funzionano come previsto. Al caricamento delle proprietà della pagina, il pannello non viene visualizzato quando sono presenti dei dati in esso contenuti (CQ-4292995).
* Più istanze di scripting tra siti nei componenti [!DNL Experience Manager Sites] (NPR-33926).
* Gli input degli utenti non vengono codificati in modo appropriato per vari componenti quando si inviano informazioni al client (NPR-33696).
* Un URL che termina con `childrenlist.html` visualizza una pagina HTML invece di una risposta 404. Tali URL sono vulnerabili agli script tra siti diversi (NPR-33441).

#### Assets {#assets-6482}

* L’estrazione del testo per i file PDF caricati non funziona e la ricerca full-text per alcune parole in un file PDF non riesce a recuperare quel file PDF (NPR-34165).

   >[!NOTE]
   >Per risolvere il problema, riavvia l’istanza di Adobe Experience Manager dopo l’installazione del Service Pack 6.4.8.2.

* Le barre rovesciate vengono aggiunte prima dei caratteri speciali nei suggerimenti di ricerca delle risorse, che hanno caratteri speciali nel loro nome (NPR-33833).

* I filtri personalizzati salvati come raccolte avanzate non vengono applicati correttamente alle risorse, pertanto i risultati della ricerca non sono precisi   (NPR-33725)

* La timeline di una risorsa all’interno di una cartella riordinata mostra che la risorsa è stata spostata (NPR-33580).

* L’annullamento della pubblicazione in blocco delle risorse da [!DNL Brand Portal] causa un errore `Request-URI Too Long` (NPR-34158).

* Nella vista a colonne se l’utente seleziona l’opzione [!UICONTROL Filtro] dopo aver selezionato un set di risorse (le risorse vengono deselezionate) e quindi seleziona un diverso set di risorse da spostare, anche le risorse selezionate in precedenza vengono spostate nella nuova posizione (NPR-34018).

* La barra di scorrimento non è visibile nella vista a elenco, anche se sono presenti numerose risorse da inserire nella pagina (NPR-34156).

* La pagina [!UICONTROL Gestisci pubblicazione] per le risorse non funziona e le opzioni in essa contenute non funzionano (CQ-4302509).

**Dynamic Media**

* La funzionalità Ritaglio avanzato non riesce e viene visualizzato un errore quando il profilo immagine viene aggiunto a una cartella con più rapporti di formato (ad esempio, 11) (NPR-34083).

* Le modifiche ai predefiniti immagine in [!UICONTROL Adobe Experience Manager] non si sincronizzano con Dynamic Media Classic (NPR-34284, CQ-4299713).

* L&#39;etichetta del modificatore [!UICONTROL PANORAMICVIEW_AUTOROTATE] è mancante dalla scheda [!UICONTROL Comportamento] nella pagina [!UICONTROL Editor predefiniti visualizzatore] (CQ-4302043).

#### Piattaforma {#platform-6482}

* I valori predefiniti per le impostazioni **[!UICONTROL Connect Timeout]** e **[!UICONTROL Socket Timeout]** per la configurazione Default Agent (publish) non sono specificati (NPR-33708).
* La pianificazione delle attività di manutenzione avvia e interrompe le attività di manutenzione troppo spesso rispetto alla configurazione (NPR-33520).
* Impossibile scaricare i registri utilizzando lo strumento Diagnosi su un&#39;istanza aggiornata di Experience Manager (NPR-34419).

#### Integrazioni {#integrations-6482}

* Il valore di `library_path` non viene considerato durante la generazione dell&#39;URL della libreria [!DNL Adobe Launch] per le librerie migrate da [!DNL Adobe Dynamic Tag Management]. Inoltre, le librerie migrate usano un prefisso diverso rispetto alle librerie [!DNL Adobe Launch] . (NPR-34238).
* Le proprietà ereditate da un servizio cloud non persistono quando si aggiornano le proprietà della pagina (NPR-33865).

#### Interfaccia utente {#ui-6482}

* La visualizzazione del conteggio delle risorse selezionate in una pagina di ricerca non è corretta (NPR-33540).

#### Community {#communities-6482}

* Gli utenti esistenti di un gruppo community aggiunto tramite admin console vengono rimossi dall’elenco di utenti in caso di modifiche nella console dei gruppi della community (NPR-34312).

#### Moduli {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] Cumulative Fix Pack non include correzioni per  [!DNL Experience Manager Forms]. Vengono distribuite utilizzando un pacchetto aggiuntivo [!DNL Forms] separato. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per [!DNL Experience Manager Forms] su JEE. Per ulteriori informazioni, consulta [Installare il pacchetto aggiuntivo di AEM Forms](#install-aem-forms-add-on-package) e [Installare il programma di installazione di JEE per AEM Forms](#install-aem-forms-jee-installer).

**Moduli adattivi**

* In presenza di un frammento di modulo adattivo mancante, il modulo adattivo non viene riprodotto correttamente (NPR-34303).

* La descrizione del contenuto della Guida per i campi di un modulo adattivo visualizza un tag HTML paragrafo (NPR-34117).

* Quando si aggiunge un contenitore Moduli in una pagina [!DNL Experience Manager Sites], la pagina visualizza il seguente messaggio di errore e non consente di aggiungere nuovi componenti (NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Quando si seleziona la proprietà **[!UICONTROL Rivalida sul server]** e si caricano più allegati, il modulo adattivo non viene inviato (NPR-33701).

* Quando si selezionano le opzioni **[!UICONTROL Usa lingua pagina]** e **[!UICONTROL Modulo copre l&#39;intera larghezza delle opzioni Pagina]** nel componente [!DNL Experience Manager Forms] in una pagina [!DNL Experience Manager Sites], la pagina non riesce a tradurre (NPR-33641).

* Quando si invia un modulo adattivo abilitato per Analytics incorporato in una pagina [!DNL Experience Manager Sites], analytics non funziona correttamente (NPR-31359).

* Sono state rimosse le dipendenze dalle librerie [!DNL Lodash] e [!DNL backbone] (NPR-33458).

* L&#39;azione di invio **[!UICONTROL Invia all&#39;endpoint REST]** non funziona per un modulo adattivo (NPR-34513).

* Accessibilità: Quando si tenta di inviare un modulo adattivo senza caricare un allegato per un campo obbligatorio, lo stato attivo non si sposta automaticamente al campo allegato (NPR-34511).

* Gli input utente non vengono codificati in modo appropriato per i componenti [!DNL Forms] quando si inviano informazioni al client (NPR-33611).

**Flusso di lavoro**

* [!DNL Experience Manager] L&#39;operazione di eliminazione del flusso di lavoro non riesce e visualizza il seguente messaggio di errore (NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Quando si installa [!DNL Experience Manager] 6.4.8.1, l&#39;elenco [!UICONTROL Da fare] degli elementi non viene visualizzato come collegamenti. Il testo per gli elementi [!UICONTROL Da fare] include i tag HTML (NPR-34318).

**BackendIntegration**

* Impossibile configurare un modello dati modulo in un ambiente ospitato da AWS [!DNL Experience Manager Forms Linux] (NPR-33617).

**Designer**

* Quando [!DNL Acrobat DC] è installato su un server [!DNL Experience Manager] Forms, l&#39;opzione **[!UICONTROL Distribuisci modulo]** non è disponibile nella versione 6.x di [!DNL Experience Manager Designer] (NPR-34325).

**Sicurezza dei documenti**

* Impossibile eseguire l&#39;operazione Sign con certificati basati su HSM in un file PDF dopo l&#39;installazione di [!DNL Experience Manager] 6.4.8.0 (NPR-34309).

**Aggiornamento**

* Quando si aggiorna la versione [!DNL JBoss] a 7.0.9 per [!DNL Experience Manager Forms] con Document Security in un ambiente [!DNL Linux], si verifica un errore (CQ-4300546).

Per informazioni sugli aggiornamenti di sicurezza, consulta la [pagina dei bollettini sulla sicurezza di Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1 è un aggiornamento importante che include diverse correzioni di problemi interni e segnalati dai clienti, introdotte successivamente alla data di disponibilità generale di AEM 6.4 Service Pack 8 (6.4.8.0) nel marzo 2020.

AEM Cumulative Fix Pack 6.4.8.1 dipende da AEM 6.4 Service Pack 8. Pertanto, è necessario installare il pacchetto AEM Cumulative Fix Pack 6.4.8.1 dopo aver installato AEM 6.4 Service Pack 8.

Alcuni degli elementi di rilievo di AEM 6.4.8.1 sono:

* L&#39;accesso anonimo a CRXDE Lite non è consentito per migliorare la sicurezza. Gli utenti vengono invece indirizzati alla schermata di accesso. Vedi [sviluppo con CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* È stata rimossa l’integrazione di Condivisione pacchetti con Adobe Experience Manager.
* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.21.

Per informazioni sui CFP e su altri tipi di rilasci, consulta [Definizioni dei veicoli di rilascio degli aggiornamenti di AEM](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.1 fornisce correzioni ai seguenti problemi.

#### Siti {#sites-6481}

* Gli utenti anonimi possono accedere alle funzioni CRX DE Lite (NPR-33522).
* Quando il nome di un componente locale in una LiveCopy è identico al nome di un componente nella blueprint e il componente viene rilasciato dalla blueprint, il termine _msm_move non viene aggiunto al nome del componente locale (NPR-33207).
* I parametri aggiunti alla richiesta originale non sono inclusi nell’URL di reindirizzamento (NPR-33174).
* Quando l&#39;opzione Coral.Select imposta emptyOption=true o contiene un elemento predefinito con valore = &quot;&quot;, il file dropdownshowhide.js rileva un errore: Errore di tipo non rilevato: component.getValue non è una funzione (NPR-33163).
* Quando un componente include un altro componente come risorsa sly per i dati, il segnaposto del componente contenitore principale viene sostituito con il segnaposto dei componenti interni (NPR-33119).
* Quando si basa un frammento di contenuto su uno schema e questo contiene un’area di testo obbligatoria o un campo percorso, il frammento di contenuto non viene salvato (NPR-33007)
* Quando crei un componente personalizzato utilizzando il componente Frammento esperienza predefinito e lo utilizzi nelle pagine AEM Sites, AEM non visualizza i riferimenti (utilizzo) per il componente personalizzato (NPR-32852).
* Quando una pagina AEM Sites fa parte di un set di contenuti di grandi dimensioni con più Live Copy, l’anteprima della cronologia della versione della pagina non viene caricata (NPR-32772).
* Quando promuovi un lancio, aggiunge il mixin &quot;cq:LiveRelationship&quot; a ogni componente aggiunto nel lancio. Ha un impatto su tutti i lanci, a prescindere dal fatto che un lancio venga creato con o senza selezionare l’opzione — Inherit source page live data — (NPR-32664).
* All’avvio dell’impaginazione, il selettore dei frammenti esperienza non carica tutti gli elementi (NPR-32605).
* Impossibile creare un lancio per una pagina AEM Sites. La creazione di un lancio genera un errore (NPR-32544).
* La funzione Gestisci pubblicazione non include le risorse di riferimento nel flusso di lavoro di richiesta dell’attivazione (NPR-32463).
* Il controllo dello stato di Dispatcher visualizza il messaggio di avviso `Invalid cookie header` nei file di log (NPR-33630).
* L’integrazione Salesforce è vulnerabile all’SSRF (NPR-32671).
* XSS riflesso in PreferencesServlet (NPR-33439).

#### Risorse {#assets-6481}

* Il conteggio delle risorse non cambia in base alla modifica nella selezione nella vista a elenco (NPR-33285).

* Il pulsante Avanti non è abilitato quando si seleziona il nodo principale (in cui è visibile una singola cartella figlio) e si seleziona la cartella figlio (NPR-33284).

* L’interfaccia utente touch non viene riprodotta (con errore) per gli utenti che non hanno accesso in lettura alla directory principale dell’archivio, quando è abilitata la modalità DMS7 o ibrida (NPR-33175).

* I caratteri GB18030 presenti nelle cartelle e nei nomi delle risorse diventano vuoti nei file zip scaricati (NPR-33150).

* La cartella aggiuntiva viene creata con il ritaglio avanzato di una risorsa che si trova all’interno di una cartella principale con il carattere punto `.` nel nome (NPR-32755).

* Il caricamento lento non viene attivato e non più di 100 risorse vengono visualizzate selezionando per rivedere le attività dalla casella in entrata delle notifiche (NPR-32749).

* La pagina di collegamento per la condivisione della raccolta è interrotta a causa di un cambiamento nelle informazioni sul corallo (NPR-32510).

* L’elaborazione delle risorse durante il caricamento in serie si blocca (CQ-4293916).

* Vulnerabilità SSRF in Experience Manager (NPR-33437).

#### Piattaforma {#platform-6481}

* Il filtro [!DNL Sling] non viene chiamato se la voce di mappa `sling:match` viene creata in `/etc/maps` (NPR-33308).
* Tutti gli agenti di scaricamento vengono attivati durante la disattivazione di una pagina (NPR-32941).
* Quando utilizzi l&#39;API `ScriptProcessor` per minimizzare una libreria JavaScript, il file di registro visualizza un messaggio di errore che indica che il codice JavaScript non è conforme alla modalità rigorosa. L’API non fornisce l’opzione per abilitare o disabilitare la modalità rigorosa. (NPR-32746).
* Quando una query SQL viene eseguita per un periodo di tempo più lungo, ad esempio 7 ore, AEM smette di rispondere (NPR-33043).

#### Interfaccia utente {#ui-6481}

* Quando cerchi o sfoglia un percorso utilizzando una finestra di dialogo di selezione, la finestra di dialogo di selezione visualizza tutti i contenuti del nodo JCR selezionato invece di visualizzare solo le immagini (NPR-32712).

#### Progetti traduzione {#tranlation-6481}

* Nei registri viene visualizzato un errore `NullPointerException` durante l’esecuzione di un processo di traduzione (NPR-32220).

#### Integrazioni {#integrations-6481}

* Script tra siti per JSON (NPR-32745).

#### Community {#communities-6481}

* Gli autori, dopo aver creato un nuovo gruppo, non vengono reindirizzati alla sezione [!UICONTROL Gruppo community] su [!DNL Internet Explorer] 11 (NPR-33202).
* Si verifica un errore durante l&#39;accesso alla pagina [!UICONTROL Flusso attività] (NPR-33152).
* La modifica di un gruppo [!DNL Communities] e la modifica dell&#39;immagine in miniatura non aggiorna l&#39;immagine in miniatura del gruppo (NPR-32603).
* Durante la creazione di una versione di notifiche e sottoscrizioni di contenuti generati dagli utenti (UGC, User Generated Content), viene memorizzato un ID errato della pagina sorgente (CQ-4289703).
* Problema di scripting tra siti (NPR-33212).

#### Flusso di lavoro {#workflow-6481}

* Alcuni componenti non vengono visualizzati nella finestra di dialogo visualizzata quando un utente completa un flusso di lavoro che include un [!UICONTROL Passaggio partecipante alla finestra di dialogo] (NPR-32989).

* Il caricamento dell&#39;opzione [!UICONTROL Timeline] nella barra a sinistra richiede più tempo del previsto (NPR-32850).

#### Moduli {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack non include correzioni per AEM Forms. Tali correzioni vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi per Forms. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per AEM Forms su JEE. Per ulteriori informazioni, consulta [Installare il pacchetto aggiuntivo di AEM Forms](#install-aem-forms-add-on-package) e [Installare il programma di installazione di JEE per AEM Forms](#install-aem-forms-jee-installer).

* Gestione della corrispondenza: Quando un utente incolla un contenuto da un documento [!DNL Word], il frammento di documento di testo non mantiene la formattazione (NPR-33213).
* Moduli adattivi: Una nuova riga a una stringa in un dizionario dei moduli adattivi aggiunge caratteri `&#xa;` al dizionario (NPR-33265).
* Moduli adattivi: L&#39;utente non è in grado di salvare un modulo adattivo con più di un allegato (NPR-33214).
* Moduli adattivi: I metodi `AddInstance` e `RemoveInstance` per la classe Instance Manager non aggiungono un numero dinamico di istanze per frammenti di carico pigri su [!DNL Internet Explorer 11] (NPR-33201).
* Moduli adattivi: Analytics abilitato su un modulo adattivo incorporato in una pagina [!DNL Sites] non registra i dati per gli eventi di invio e abbandono (NPR-31359).
* Moduli adattivi: Quando un utente incolla il contenuto di un documento [!DNL Word] in un modulo adattivo e lo invia, il modulo adattivo inviato include caratteri unicode. Inoltre, la conversione da PDF a PDF/A non riesce a causa di caratteri unicode (NPR-33348).
* Integrazione back-end: Le richieste del modello dati del modulo non riescono perché scade il token di aggiornamento a causa di uno stato inattivo non corretto (NPR-33168).
* Servizi documenti: Il servizio Converti PDF non riesce a convertire i documenti PDF in PostScript a causa di jar Gibson mancanti per [!DNL WebLogic] sul server [!DNL Linux] (NPR-33515, CQ-4292239).
* Servizi documenti: Quando un utente converte un file di testo in un PDF, i caratteri giapponesi non vengono riprodotti correttamente (NPR-33239).
* Archiviato XSS con il GuideSOMProviderServlet (NPR-32701).

## Installa 6.4.8.4 {#install}

### Requisiti di configurazione {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Per i clienti con Feature Pack installati su AEM 6.4. I Feature Pack opzionali forniti da Adobe dipendono dalla versione release e dai service pack. Se hai installato un Feature Pack, contatta il team di Assistenza clienti AEM per verificare la compatibilità di tali feature pack con questo fix pack cumulativo per AEM 6.4.

* AEM 6.4.8.4 richiede AEM 6.4.8.0. Per istruzioni dettagliate, visita la [documentazione di aggiornamento](../sites-deploying/upgrade.md) .
* In una distribuzione con MongoDB e più istanze, installa AEM 6.4.8.4 in una delle istanze Autore tramite Gestione pacchetti.
* Prima di installare il fix pack cumulativo, assicurati di avere uno snapshot o un nuovo backup della tua istanza AEM.
* Riavvia l’istanza prima dell’installazione. Anche se questo è necessario solo quando l’istanza è ancora in modalità di aggiornamento (e questo accade quando l’istanza è stata appena aggiornata da una versione precedente), si consiglia generalmente se l’istanza è in esecuzione per un periodo di tempo più lungo.

>[!NOTE]
>
>Adobe sconsiglia la rimozione o la disinstallazione del pacchetto AEM 6.4.8.4.

### Installa il Cumulative Fix Pack {#install-cumulative-fix-pack}

Per installare il Cumulative Fix Pack in un’istanza AEM 6.4.8.0 esistente, effettua le seguenti operazioni:

1. Fai clic sul collegamento [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) per scaricare il pacchetto.

1. Apri [Gestione pacchetti](http://localhost:4502/crx/packmgr/index.jsp) e fai clic su **[!UICONTROL Carica pacchetto]** per caricarlo.

1. Seleziona il nome del pacchetto e fai clic su **[!UICONTROL Installa]**.

>[!NOTE]
>
>**La finestra di dialogo nell’interfaccia utente di Gestione pacchetti talvolta si chiude prematuramente durante l’installazione della versione 6.4.8.4**
>
>È consigliabile attendere che i registri degli errori si stabilizzino prima di accedere all’istanza. L&#39;utente deve attendere i registri specifici relativi alla disinstallazione del bundle dell&#39;Updater prima di assicurarsi che l&#39;installazione abbia esito positivo. Il problema si verifica in genere in Safari, ma può accadere in modo intermittente in qualsiasi browser.

### Installazione automatica {#auto-installation}

Esistono due modi per installare automaticamente AEM 6.4.8.4 in un’istanza in esecuzione:

A. Inserisci il pacchetto in ..*/crx-quickstart/install* mentre il server è in esecuzione. Il pacchetto viene installato automaticamente.

B. Utilizza l’ [API HTTP da Gestione pacchetti](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - assicurati di utilizzare `cmd=install&recursive=true` - in modo che il pacchetto nidificato sia installato.

>[!NOTE]
>
>AEM 6.4.8.4 non supporta l’installazione tramite bootstrap.

### Convalidare l’installazione {#validate-install}

1. La pagina Informazioni prodotto (*/system/console/productinfo*) deve ora mostrare la stringa di versione aggiornata &quot;Adobe Experience Manager, versione 6.4.8.4&quot; in Prodotti installati.
1. Tutti i bundle OSGi risultano come ATTIVI o FRAMMENTI nella console OSGi (usa la console web: /system/console/bundles).
1. Il bundle OSGI org.apache.jackrabbit.oak-core è nella versione 1.8.17 o successiva (Usa la console Web: /system/console/bundles).

Per determinare la piattaforma certificata da eseguire con questa versione di AEM Sites e Assets, consulta [Requisiti tecnici](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Al termine dell&#39;installazione del pacchetto, viene visualizzato un messaggio informativo che indica che il pacchetto di contenuti è stato installato correttamente, ad esempio **&quot;Content Package AEM-6.4-Service-Pack-8 installato correttamente.&quot;**

### Aggiornare i visualizzatori Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.4 contiene una nuova versione dei visualizzatori Dynamic Media (5.10.1) che consente di verificare la presenza di nomi duplicati nella pagina Predefiniti immagine. Consigliamo ai clienti di Dynamic Media di eseguire il comando seguente per spostare i predefiniti visualizzatore predefiniti in uno stato aggiornato.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

che copierà i nuovi predefiniti visualizzatore nella posizione /conf.

### Installare il pacchetto di componenti aggiuntivi per AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Per [!DNL Experience Manager Forms] vengono rilasciati pacchetti del componente aggiuntivo una settimana dopo la data di rilascio pianificata per il Cumulative Fix Pack di [!DNL Experience Manager].

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms. Le correzioni apportate in AEM Forms vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi.

1. Assicurati di aver installato AEM Cumulative Fix Pack.
1. Scarica il pacchetto corrispondente dei componenti aggiuntivi per Forms elencato in [Versioni di AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#forms-updates) per il sistema operativo in uso.
1. Installa il pacchetto dei componenti aggiuntivi per Forms come descritto in [Installazione dei pacchetti dei componenti aggiuntivi per AEM Forms](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installare il programma di installazione di JEE per AEM Forms {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms in JEE. Le correzioni apportate a JEE per AEM Forms vengono distribuite tramite un programma di installazione separato.

Per informazioni sull’installazione del programma di installazione cumulativo per JEE per AEM Forms e sulla configurazione post-distribuzione, consulta [Modulo di installazione delle patch JEE per AEM Forms](jee-patch-installer-64.md).

>[!NOTE]
>
>Dopo aver installato il programma di installazione cumulativo per Experience Manager Forms su JEE, installa il pacchetto aggiuntivo Forms più recente, elimina il pacchetto aggiuntivo Forms dalla cartella `crx-repository\install` e riavvia il server.

### JAR Uber {#uber-jar}

Il file JAR Uber per AEM 6.4.8.4 è disponibile nell’ [archivio centrale Maven](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/).

Per utilizzare il file JAR Uber in un progetto Maven, consulta l’articolo [Come utilizzare il file JAR Uber](../sites-developing/ht-projects-maven.md) e includi nel POM del progetto la seguente dipendenza:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.4</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar e altri artefatti correlati sono disponibili nell’archivio centrale Maven invece dell’archivio pubblico Maven di Adobe (repo.adobe.com). Il file UberJar principale viene rinominato in `uber-jar-<version>.jar`. Di conseguenza, per il tag `dependency` non esiste `classifier`, con `apis` come valore.

## Funzioni rimosse/obsolete {#removed-deprecated-features}

In questa sezione sono elencate le funzionalità rimosse o dichiarate obsolete in AEM 6.4.

| Area | Funzione obsoleta | Sostituzione | Versione |
|---|---|---|---|
| Assets | Gestione azione tag per le risorse secondarie | Nessuna sostituzione | AEM 6.4.2.0 |
| Integrazione di Assets con Adobe Creative Cloud | La [condivisione cartelle da AEM a Creative Cloud](https://docs.adobe.com/content/help/it/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) è stata introdotta in AEM 6.2 per consentire agli utenti creativi di accedere alle risorse da AEM. Una nuova funzionalità introdotta nell’applicazione Creative Cloud, Adobe Asset Link, offre un’esperienza utente migliore e un accesso più efficace alle risorse da AEM direttamente da Photoshop, InDesign e Illustrator. Adobe non apporterà ulteriori miglioramenti alla funzionalità di condivisione cartelle. Anche se la funzione è inclusa in AEM, i clienti sono invitati a utilizzare la sostituzione. | Adobe Asset Link o l’app desktop. Per ulteriori informazioni, consulta l’articolo sull’[integrazione di AEM con Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Problemi noti {#known-issues}

* Se esegui l’aggiornamento da [!DNL Experience Manager] 6.4 a [!DNL Experience Manager] 6.5, alcuni bundle potrebbero non visualizzare il loro stato come `Active`. Installa l&#39;ultimo [!DNL Experience Manager] Service Pack 6.5 per risolvere il problema.

Per informazioni sui problemi noti relativi al Service Pack AEM 6.4.8.0, consulta [Note sulla versione di AEM 6.4.8.0 Service Pack](sp-release-notes.md).

## Bundle OSGi e pacchetti di contenuti inclusi {#osgi-bundles-and-content-packages-included}

Nei documenti di testo seguenti sono elencati i bundle OSGi e i pacchetti di contenuti inclusi in AEM 6.4.8.4.

Elenco dei bundle OSGi inclusi in AEM 6.4.8.4

[Ottieni file](assets/6.4.8.4_osgi_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.8.4

[Ottieni file](assets/6.4.8.4_content_packages.txt)

## Risorse utili {#helpful-resources}

* [Note sulla versione di AEM 6.4](../release-notes/release-notes.md)
* [Pagina del prodotto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentazione di AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64.html?lang=it)
* Abbonati ad [Adobe priority product update](https://www.adobe.com/subscription/priority-product-update.html)

## Siti con limitazioni {#restricted-sites-new}

Questi siti sono disponibili solo per i clienti. Se sei un cliente e hai bisogno di accedere, contatta il manager del tuo account Adobe.

* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/)
* [Assistenza clienti](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
