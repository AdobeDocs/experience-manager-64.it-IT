---
title: AEM 6.4 Note sulla versione Cumulative Fix Pack
description: Note sulla versione specifiche dei pacchetti di correzioni cumulativi Adobe Experience Manager 6.4.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 1d3476c3fdc8cf817e4784f36b4e0858fdc3b1ee
workflow-type: tm+mt
source-wordcount: '4217'
ht-degree: 11%

---


# AEM 6.4 Note sulla versione del Cumulative Fix Pack {#aem-cumulative-fix-pack-release-notes}

## Informazioni sulla versione {#release-information}

<!-- TBD: Update the SD URL. -->

| Prodotti | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versione | 6.4.8.3 |
| Tipo | Cumulative Fix Pack |
| Data | 26 novembre 2020 |
| Prerequisito | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL di download | AEM 6.4.8.3 su [distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-3.0.zip) |

## Funzionalità incluse in AEM 6.4.8.3 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.3 è un aggiornamento importante che include diverse correzioni interne e per i clienti, a partire dalla disponibilità generale di AEM 6.4 Service Pack 8 (6.4.8.0) nel marzo 2020.

AEM 6.4.8.3 è un Cumulative Fix Pack (CFP) che dipende da AEM 6.4 Service Pack 8. Installare il CFP dopo l&#39;installazione di AEM 6.4 Service Pack 8.

Nella AEM 6.4.8.3, il repository incorporato (Apache Jackrabbit Oak) viene aggiornato alla versione 1.8.23.

Per informazioni su CFP e altri tipi di rilasci, vedere [AEM Aggiornamento delle definizioni dei veicoli di rilascio](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.3 fornisce delle correzioni per i seguenti problemi.

### Sites {#sites-6483}

* Quando aggiornate il testo di una variante di un frammento di contenuto, il contenuto del frammento di contenuto principale viene aggiornato al posto della variante (NPR-35080).

* Quando si imposta un valore numerico per la proprietà dell&#39;etichetta del tipo di stringa di un componente, si elimina il componente e si utilizza l&#39;opzione Annulla per riportarlo indietro, il tipo di proprietà dell&#39;etichetta passa automaticamente da String a Long (NPR-34738).

* Quando aggiungete un componente Caricamento file a più campi, il percorso immagine viene memorizzato nel nodo del componente invece del nodo Multi-Campo (NPR-34423).

* Nella procedura guidata Sposta pagina, anche se non è selezionata alcuna destinazione, il pulsante successivo rimane attivato (NPR-34460).

* Quando il componente principale include la proprietà `cq:isContainer`, il componente ereditato non include automaticamente la proprietà (CQ-4308409).

* Quando si utilizza la funzione di riduzione CSS con la funzione `calc()`, gli spazi vuoti intorno al segno `+` vengono rimossi (NPR-34991).

* Quando avviate un&#39;istanza AEM, i componenti `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` e `com.adobe.granite.maintenance.impl.TaskScheduler` non vengono visualizzati nello stato `Active` (NPR-34952).

### [!DNL Assets] {#assets-6483}

* Durante la creazione di una versione di una risorsa esistente, gli aggiornamenti ai metadati da parte dell’utente non vengono mantenuti se alla cartella viene applicato un profilo di metadati (NPR-34833).
* Quando si utilizza [!DNL Adobe Asset Link] con [!DNL Adobe InDesign], i risultati della ricerca non contengono cartelle e raccolte ma solo risorse (NPR-34700).
* Quando trascinate una risorsa su una cartella per spostarla, l&#39;interfaccia utente visualizza anche l&#39;opzione su [!UICONTROL Drop in Lightbox] e [!UICONTROL Drop in Collection] (Rilascia nella raccolta). Anche se l&#39;operazione di spostamento viene annullata, l&#39;interfaccia utente continua a visualizzare le ultime due opzioni (NPR-34525).
* Quando l&#39;interfaccia Gestisci pubblicazione è aperta, l&#39;opzione Pubblica non è disponibile e dopo aver selezionato l&#39;opzione Annulla pubblicazione la pagina dell&#39;ambito è vuota (CQ-4302509).

#### [!DNL Dynamic Media] {#dynamic-media}

* Nelle impostazioni del predefinito per immagini, quando l&#39;opzione [!UICONTROL Abilita downsampling crominanza JPG] è deselezionata in [!DNL Experience Manager], la modifica non viene sincronizzata con [!DNL Dynamic Media] (NPR-34284).
* Nell&#39;editor [!UICONTROL Predefiniti visualizzatore], quando si modifica il predefinito [!UICONTROL PanoramicImage/PanoramicImage_VR], nel componente `PanoramicView` l&#39;etichetta del modificatore `PANORAMICVIEW_AUTOROTATE` non è disponibile (CQ-4302043).
* L&#39;annullamento della pubblicazione di un video da [!DNL Experience Manager] non annulla la pubblicazione del set video adattivo sull&#39;Scene7 configurato. (CQ-4304405).

### Platform {#platform-6483}

* Il flag `emitUseStrict` viene aggiunto alla funzione del processore Google Closure Compiler (GCC) `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. Il flag sopprime l&#39;output dell&#39;istruzione `use strict` (NPR-34830).
* Viene restituito un `NullPointerException` all&#39;avvio delle attività di manutenzione giornaliera o settimanale (NPR-34702).
* Lo strumento [!DNL Apache Sling Health Check] è obsoleto. Utilizzate invece [Rilevamento pattern](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html) per rilevare le violazioni dei contenuti (NPR-33929).

### Integrations (Integrazioni){#integrations-6483}

* Il pulsante [!UICONTROL Crea] viene visualizzato nella pagina [!UICONTROL Audiences] quando si passa da una cartella alla pagina [!UICONTROL Audiences] (NPR-35152).

### Interfaccia utente {#ui-6483}

* Il pannello di ricerca [!UICONTROL Filtri] nell&#39;interfaccia utente [!UICONTROL Omnisearch] restituisce anche risultati da posizioni diverse da quelle da cui viene eseguita la ricerca (NPR-34877).
* Alla chiusura del pannello [!UICONTROL Filtri] sull&#39;interfaccia utente di [!UICONTROL Omnisearch], la barra a sinistra non viene reimpostata sulla selezione [!UICONTROL Content], il che impedisce la riapertura del pannello [!UICONTROL Filters] (NPR-34483).
* All&#39;accesso alle proprietà della pagina viene restituito un `NullPointerException` (NPR-34509).

### Communities {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* Tutti i casi di terminologia iniqua nel prodotto vengono sostituiti con equivalenti accettati (NPR-34506).

### Commerce {#commerce-6483}

* Se in una raccolta sono presenti più di 15 prodotti, la raccolta visualizza solo i primi 15 prodotti (NPR-34494).

### Forms {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] rilascia i pacchetti aggiuntivi una settimana dopo la data di rilascio pianificata per il  [!DNL Experience Manager] Cumulative Fix Pack.

>[!NOTE]
>
>[!DNL Experience Manager] Cumulative Fix Pack non include correzioni per  [!DNL Experience Manager Forms]. Vengono distribuite utilizzando un pacchetto aggiuntivo [!DNL Forms] separato. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per [!DNL Experience Manager Forms] su JEE. Per ulteriori informazioni, vedere [Installare  pacchetto aggiuntivo AEM Forms](#install-aem-forms-add-on-package) e [Installare  programma di installazione AEM Forms JEE](#install-aem-forms-jee-installer).

**Moduli adattivi**

* Impossibile modificare un modulo adattivo utilizzando l&#39;interfaccia classica dopo l&#39;applicazione del pacchetto di correzioni cumulative [!DNL Experience Manager] (NPR-35127).

* Il caricamento dei frammenti in un modulo adattivo richiede più tempo a causa dell&#39;annullamento della validità della cache (NPR-34655).

* Accessibilità: La navigazione mediante tabulazione non funziona correttamente per gli assistenti vocali in un modulo adattivo (NPR-34550).

**Gestione della corrispondenza**

* Quando si esegue la migrazione delle risorse da ES3, le risorse includono due condizioni predefinite non modificabili (NPR-34971).

**JEE per Foundation**

* Migrare gli utenti [!DNL AEM Forms] dall&#39;Flash all&#39;HTML (CQ-4304075).

Per informazioni sugli aggiornamenti della sicurezza, vedere [ pagina dei bollettini sulla sicurezza degli Experienci Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## Hotfix e Feature Pack inclusi nei Cumulative Fix Pack precedenti {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2 è un aggiornamento importante che include diverse correzioni interne e per i clienti, a partire dalla disponibilità generale di AEM 6.4 Service Pack 8 (6.4.8.0) nel marzo 2020.

AEM 6.4.8.2 è un Cumulative Fix Pack (CFP) che dipende da AEM 6.4 Service Pack 8. Installare il CFP dopo l&#39;installazione di AEM 6.4 Service Pack 8.

Nella AEM 6.4.8.2, il repository incorporato (Apache Jackrabbit Oak) viene aggiornato alla versione 1.8.22.

Per informazioni su CFP e altri tipi di rilasci, vedere [AEM Aggiornamento delle definizioni dei veicoli di rilascio](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.2 fornisce delle correzioni per i seguenti problemi.

#### Siti {#sites-6482}

* Se `RolloutConfigManagerFactoryImpl` non è in grado di caricare una configurazione di rollout, non tenta di caricare le configurazioni mancanti. Restituisce le configurazioni memorizzate nella cache (NPR-34091).
* Nel componente di base Testo, dopo aver utilizzato l&#39;opzione di modifica HTML di origine, la classe dal tag `em` viene rimossa (NPR-34080).
* Quando eseguite l&#39;aggiornamento  Experience Manager 6.2 a  Experience Manager 6.5, il componente Parsys dei modelli statici non viene visualizzato correttamente. L&#39;altezza del componente Parsys è impostata su 0 e i componenti al suo interno non sono visibili (NPR-34044).
* Le informazioni sull&#39;etichetta non vengono visualizzate sui componenti consentiti all&#39;interno dell&#39;Editor modelli (NPR-33908).

   ![Etichette mancanti nel contenitore di layout](assets/33908_missing_labels.png)

* Gli utenti non possono aggiungere o modificare componenti a parsys dopo il quarto livello di componenti nidificati (NPR-33873).
* Se il contenuto iniziale di un modello modificabile viene modificato e il modello viene pubblicato, tutte le nuove pagine create con questo modello mostrano la data di pubblicazione del modello anche se le pagine non sono pubblicate (NPR-33822).
* Le proprietà `cq:acLinks` e `cq:acUUID` della copia [!DNL Adobe Campaign] vengono rimosse durante l&#39;operazione di copia e incolla (NPR-33793).
* Nella scheda [!UICONTROL Live Usage] sono visualizzati solo 49 risultati. Non mostra tutto l&#39;utilizzo del componente (NPR-33710).
* Una pagina Web con un carattere `/` nell’URL non risponde durante l’authoring. Quando un componente viene aggiunto durante l&#39;authoring, l&#39;utilizzo della CPU aumenta e il browser smette di rispondere (NPR-33625).
* In modalità di modifica in linea in [!DNL RTE], il trascinamento di un&#39;immagine non funziona per il componente Testo (NPR-33579).
* È possibile creare un componente in una pagina blueprint con lo stesso nome del nome della pagina. Durante il rollout, tale componente viene rinominato con il suffisso `_msm_moved`. Tuttavia, il componente viene spostato alla fine del [!UICONTROL Sistema paragrafo] (NPR-33534).
* La promozione di avvio non pubblica le pagine quando la proprietà [!UICONTROL include subpages] non è selezionata nella radice del primo contenuto (NPR-33533).
* Il reindirizzamento a [!DNL Experience Manager] pagina con ancoraggio non funziona sull&#39;istanza Author come `PageRedirectServlets` inserisce una stringa di query dopo un frammento URL o un ancoraggio (NPR-34287).
* `PageRedirectServlet` viene aggiunto  `.html` dopo la mappatura Sling che provoca errori di collegamento (NPR-34271).
* È possibile sospendere la [!DNL Live Copy] di una pagina e l&#39;ereditarietà viene interrotta come mostrato in modalità Editor. Tuttavia, nelle proprietà Page, l&#39;icona che rappresenta l&#39;ereditarietà indica erroneamente che l&#39;ereditarietà esiste e non è interrotta (NPR-34096).
* Problema con la visualizzazione dei componenti consentiti nella pagina del modello Modifica (CQ-4297295).
* Dopo l&#39;aggiornamento di Chrome e Firefox, i menu a comparsa non funzionano come previsto. Quando si caricano le proprietà della pagina, il pannello non viene visualizzato in presenza di dati (CQ-4292995).
* Più istanze di script tra siti nei componenti [!DNL Experience Manager Sites] (NPR-33926).
* Gli input dell&#39;utente non vengono codificati correttamente per vari componenti quando inviano informazioni al client (NPR-33696).
* Un URL che termina con `childrenlist.html` visualizza una pagina HTML invece di una risposta 404. Tali URL sono vulnerabili agli script tra siti diversi (NPR-33441).

#### Assets {#assets-6482}

* L&#39;estrazione del testo per i file PDF caricati non funziona e la ricerca full-text di alcune parole in un file PDF non riesce a recuperare il file PDF (NPR-34165).

   >[!NOTE]
   >Per risolvere il problema, riavviate l&#39;istanza di Adobe Experience Manager dopo l&#39;installazione di Service Pack 6.4.8.2.

* Le barre rovesciate vengono aggiunte prima dei caratteri speciali nei suggerimenti per la ricerca di risorse, che contengono caratteri speciali nel nome (NPR-33833).

* I filtri personalizzati salvati come raccolte avanzate non vengono applicati correttamente alle risorse, pertanto i risultati della ricerca non sono precisi   (NPR-33725).

* La cronologia di una risorsa all’interno di una cartella riordinata mostra che la risorsa è stata spostata (NPR-33580).

* L&#39;annullamento della pubblicazione delle risorse in blocco da [!DNL Brand Portal] genera un errore `Request-URI Too Long` (NPR-34158).

* Nella vista a colonne, se l&#39;utente seleziona l&#39;opzione [!UICONTROL Filtro] dopo aver selezionato un set di risorse (le risorse vengono deselezionate), quindi seleziona un altro set di risorse da spostare, le risorse selezionate in precedenza vengono spostate nella nuova posizione (NPR-34018).

* La barra di scorrimento non è visibile nella vista a elenco, anche se sono presenti numerose risorse da inserire nella pagina (NPR-34156).

* La pagina [!UICONTROL Gestisci pubblicazione] delle risorse è interrotta e le opzioni in essa contenute non funzionano (CQ-4302509).

**Dynamic Media**

* La funzionalità Smart Crop non riesce con un errore quando il profilo immagine viene aggiunto a una cartella con più proporzioni (ad esempio, 11) (NPR-34083).

* Le modifiche ai predefiniti per immagini in [!UICONTROL Adobe Experience Manager] non si sincronizzano con Scene7 Publishing System (NPR-34284, CQ-4299713).

* L&#39;etichetta del modificatore [!UICONTROL PANORAMICVIEW_AUTOROTATE] non è presente nella scheda [!UICONTROL Behavior] nella pagina [!UICONTROL Viewer Preset Editor] (CQ-4302043).

#### Piattaforma {#platform-6482}

* I valori predefiniti per le impostazioni **[!UICONTROL Timeout connessione]** e **[!UICONTROL Timeout socket]** per la configurazione Agente predefinito (pubblicazione) non sono specificati (NPR-33708).
* L&#39;utilità di pianificazione delle attività di manutenzione avvia e arresta le attività di manutenzione troppo spesso rispetto alla configurazione (NPR-33520).
* Impossibile scaricare i registri utilizzando lo strumento Diagnosi in un&#39;istanza di Experience Manager  aggiornata (NPR-34419).

#### Integrations (Integrazioni){#integrations-6482}

* Il valore di `library_path` non viene considerato durante la generazione dell&#39;URL della libreria [!DNL Adobe Launch] per le librerie migrate da [!DNL Adobe Dynamic Tag Management]. Inoltre, le librerie migrate utilizzano un prefisso diverso dalle librerie [!DNL Adobe Launch]. (NPR-34238).
* Le proprietà ereditate da un servizio cloud non persistono durante l&#39;aggiornamento delle proprietà della pagina (NPR-33865).

#### Interfaccia utente {#ui-6482}

* La visualizzazione del conteggio delle risorse selezionate in una pagina di ricerca non è corretta (NPR-33540).

#### Community {#communities-6482}

* Gli utenti esistenti di un gruppo di community aggiunto tramite Admin Console vengono rimossi dall&#39;elenco di utenti in caso di modifiche nella console del gruppo di community (NPR-34312).

#### Forms {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] Cumulative Fix Pack non include correzioni per  [!DNL Experience Manager Forms]. Vengono distribuite utilizzando un pacchetto aggiuntivo [!DNL Forms] separato. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per [!DNL Experience Manager Forms] su JEE. Per ulteriori informazioni, vedere [Installare  pacchetto aggiuntivo AEM Forms](#install-aem-forms-add-on-package) e [Installare  programma di installazione AEM Forms JEE](#install-aem-forms-jee-installer).

**Moduli adattivi**

* In presenza di un frammento di modulo adattivo mancante, il rendering del modulo adattivo non riesce (NPR-34303).

* La descrizione del contenuto della Guida relativa a un campo modulo adattivo visualizza un tag HTML paragrafo (NPR-34117).

* Quando aggiungete un contenitore Forms su una pagina [!DNL Experience Manager Sites], la pagina visualizza il seguente messaggio di errore e non consente di aggiungere nuovi componenti (NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Quando si seleziona la proprietà **[!UICONTROL Revoca sul server]** e si caricano più allegati, il modulo adattivo non viene inviato (NPR-33701).

* Quando si seleziona l&#39;opzione **[!UICONTROL Usa lingua pagina]** e **[!UICONTROL Modulo copre l&#39;intera larghezza delle opzioni Pagina]** nel componente [!DNL Experience Manager Forms] su una pagina [!DNL Experience Manager Sites], la pagina non viene convertita (NPR-33641).

* Quando si invia un modulo adattivo abilitato per l&#39;analisi incorporato in una pagina [!DNL Experience Manager Sites], l&#39;analisi non funziona correttamente (NPR-31359).

* Sono state rimosse dipendenze dalle librerie [!DNL Lodash] e [!DNL backbone] (NPR-33458).

* L&#39;azione di invio **[!UICONTROL Invia all&#39;endpoint REST]** non funziona per un modulo adattivo (NPR-34513).

* Accessibilità: Quando si tenta di inviare un modulo adattivo senza caricare un allegato per un campo obbligatorio, lo stato attivo non si sposta automaticamente sul campo allegato (NPR-34511).

* Gli input dell&#39;utente non vengono codificati correttamente per i componenti [!DNL Forms] quando inviano informazioni al client (NPR-33611).

**Flusso di lavoro**

* [!DNL Experience Manager] L&#39;operazione di eliminazione del flusso di lavoro non riesce e visualizza il seguente messaggio di errore (NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Quando si installa [!DNL Experience Manager] 6.4.8.1, l&#39;elenco [!UICONTROL Da fare] degli elementi non viene visualizzato come collegamenti. Il testo per gli elementi [!UICONTROL Da fare] include tag HTML (NPR-34318).

**BackendIntegration**

* Impossibile configurare un modello dati modulo in un ambiente ospitato da AWS [!DNL Experience Manager Forms Linux] (NPR-33617).

**Designer**

* Se [!DNL Acrobat DC] è installato su un server [!DNL Experience Manager] Forms, l&#39;opzione **[!UICONTROL Distribuisci modulo]** non è disponibile in [!DNL Experience Manager Designer] versione 6.x (NPR-34325).

**Sicurezza dei documenti**

* Impossibile eseguire l&#39;operazione Sign con certificati basati su HSM in un file PDF dopo l&#39;installazione di [!DNL Experience Manager] 6.4.8.0 (NPR-34309).

**Aggiornamento**

* Quando si aggiorna la versione [!DNL JBoss] a 7.0.9 per [!DNL Experience Manager Forms] con Document Security in un ambiente [!DNL Linux], si verifica un errore (CQ-4300546).

Per informazioni sugli aggiornamenti della sicurezza, vedere [ pagina dei bollettini sulla sicurezza degli Experienci Manager](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1 è un aggiornamento importante che include diverse correzioni interne e per i clienti, a partire dalla disponibilità generale di AEM 6.4 Service Pack 8 (6.4.8.0) nel marzo 2020.

AEM Cumulative Fix Pack 6.4.8.1 dipende da AEM 6.4 Service Pack 8. È pertanto necessario installare il pacchetto AEM Cumulative Fix Pack 6.4.8.1 dopo aver installato AEM 6.4 Service Pack 8.

Alcuni degli elementi salienti della AEM 6.4.8.1 sono:

* L&#39;accesso anonimo ai CRXDE Lite non è consentito per migliorare la sicurezza. Al contrario, gli utenti vengono indirizzati alla schermata di accesso. Vedere [sviluppo con CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* È stata rimossa l&#39;integrazione di Package Share con Adobe Experience Manager.
* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.21.

Per informazioni su CFP e altri tipi di rilasci, vedere [AEM Aggiornamento delle definizioni dei veicoli di rilascio](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.1 fornisce delle correzioni ai seguenti problemi.

#### Siti {#sites-6481}

* Gli utenti anonimi possono accedere alle funzioni CRX DE Lite (NPR-33522).
* Quando il nome di un componente locale in LiveCopy è identico al nome di un componente nel blueprint e il componente viene implementato dal blueprint, il termine _msm_move non viene aggiunto al nome del componente locale (NPR-33207).
* I parametri aggiunti alla richiesta originale non sono inclusi nell&#39;URL di reindirizzamento (NPR-33174).
* Quando l&#39;opzione Coral.Select imposta emptyOption=true o contiene un elemento predefinito con valore = &quot;, il file dropdownshowhide.js restituisce un errore: Errore di tipo non rilevato: component.getValue non è una funzione (NPR-33163).
* Quando un componente include un altro componente come risorsa semplice per i dati, il segnaposto del componente contenitore principale viene sostituito con il segnaposto dei componenti interni (NPR-33119).
* Se si basa un frammento di contenuto su uno schema e questo contiene un&#39;area di testo obbligatoria o un campo percorso, il frammento di contenuto non viene salvato (NPR-33007)
* Quando create un componente personalizzato utilizzando il componente per frammento esperienza fornito e lo utilizzate  pagine AEM Sites, AEM non visualizza riferimenti (utilizzo) per il componente personalizzato (NPR-32852).
* Quando una pagina AEM Sites  fa parte di un set di contenuti di grandi dimensioni con più Live Copy, l&#39;anteprima della cronologia della versione della pagina non viene caricata (NPR-32772).
* Quando promuovi un lancio, aggiunge il mixin &quot;cq:LiveRelationship&quot; a ogni componente aggiunto al lancio. Influisce su tutti gli avvii, indipendentemente dal fatto che sia stato creato un lancio con o senza selezionare il comando —  Eredita dati dal vivo della pagina di origine —  (NPR-32664).
* All&#39;avvio dell&#39;impaginazione, il Selettore frammenti esperienza non carica tutti gli elementi (NPR-32605).
* Impossibile creare un lancio per una pagina AEM Sites . La creazione dell&#39;avvio genera un errore (NPR-32544).
* Manage Publication non include le risorse di riferimento nel flusso di lavoro di attivazione della richiesta (NPR-32463).
* Il controllo dello stato del dispatcher visualizza il messaggio di avviso `Invalid cookie header` nei file di registro (NPR-33630).
* L&#39;integrazione di Salesforce è vulnerabile all&#39;SSRF (NPR-32671).
* XSS riflesso in PreferencesServlet (NPR-33439).

#### Risorse {#assets-6481}

* Il conteggio delle risorse non cambia in base alla modifica nella selezione in visualizzazione a elenco (NPR-33285).

* Il pulsante Avanti non è attivato quando si seleziona il nodo principale (dove è visibile una singola cartella figlia) e si seleziona la cartella secondaria (NPR-33284).

* L’interfaccia utente touch non riesce a eseguire il rendering (con errore) per gli utenti che non dispongono dell’accesso in lettura nella directory principale dell’archivio, quando è abilitata la modalità DMS7 o ibrida (NPR-33175).

* I caratteri GB18030 che si verificano nei nomi delle cartelle e delle risorse diventano vuoti nei file zip scaricati (NPR-33150).

* Al ritaglio avanzato di una risorsa all’interno di una cartella principale con il carattere punto `.` nel nome (NPR-32755) viene creata una cartella aggiuntiva.

* Il caricamento lento non viene attivato e non più di 100 risorse vengono visualizzate quando si seleziona per controllare le attività dalla inbox delle notifiche (NPR-32749).

* La pagina di collegamento per la condivisione della raccolta è interrotta a causa della modifica in coral-info (NPR-32510).

* L&#39;elaborazione delle risorse durante il caricamento in blocco si blocca (CQ-4293916).

* Vulnerabilità SSRF nel Experience Manager  (NPR-33437).

#### Piattaforma {#platform-6481}

* Il filtro [!DNL Sling] non viene chiamato se la voce di mapping `sling:match` viene creata in `/etc/maps` (NPR-33308).
* Tutti gli agenti di scaricamento vengono attivati quando si disattiva una pagina (NPR-32941).
* Quando si utilizza l&#39;API `ScriptProcessor` per minificare una libreria JavaScript, il file di registro visualizza un messaggio di errore che indica che il codice JavaScript non è conforme alla modalità rigorosa. L&#39;API non fornisce l&#39;opzione per abilitare o disabilitare la modalità rigorosa. (NPR-32746).
* Quando una query SQL viene eseguita per un periodo di tempo più lungo, ad esempio 7 ore, AEM interrompe la risposta (NPR-33043).

#### Interfaccia utente {#ui-6481}

* Quando eseguite una ricerca o sfogliate un percorso utilizzando una finestra di dialogo di selezione, viene visualizzato tutto il contenuto del nodo JCR selezionato invece di visualizzare solo le immagini (NPR-32712).

#### Progetti traduzione {#tranlation-6481}

* Nei registri viene visualizzato un errore `NullPointerException` durante l&#39;esecuzione di un processo di traduzione (NPR-32220).

#### Integrations (Integrazioni){#integrations-6481}

* Script tra siti per JSON (NPR-32745).

#### Community {#communities-6481}

* Dopo aver creato un nuovo gruppo, gli autori non vengono reindirizzati alla sezione [!UICONTROL Gruppo community] su [!DNL Internet Explorer] 11 (NPR-33202).
* Errore durante l&#39;accesso alla pagina [!UICONTROL Activity Stream] (NPR-33152).
* Se si modifica un gruppo [!DNL Communities] e si modifica l&#39;immagine in miniatura, l&#39;immagine del gruppo non viene aggiornata (NPR-32603).
* Durante la creazione di una versione di notifiche e sottoscrizioni di contenuti generati dall&#39;utente (UGC), viene memorizzato un ID errato della pagina di origine (CQ-4289703).
* Problema di scripting tra siti (NPR-33212).

#### Flusso di lavoro {#workflow-6481}

* Alcuni componenti non vengono visualizzati nella finestra di dialogo che viene visualizzata quando un utente completa un flusso di lavoro che include un [!UICONTROL Passaggio partecipante alla finestra di dialogo] (NPR-32989).

* Il caricamento dell&#39;opzione [!UICONTROL Timeline] nella barra a sinistra richiede più tempo del previsto (NPR-32850).

#### Forms {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack non include correzioni per  AEM Forms. Tali correzioni vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi per Forms. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per  AEM Forms su JEE. Per ulteriori informazioni, vedere [Installare  pacchetto aggiuntivo AEM Forms](#install-aem-forms-add-on-package) e [Installare  programma di installazione AEM Forms JEE](#install-aem-forms-jee-installer).

* Gestione corrispondenza: Quando un utente incolla contenuto da un documento [!DNL Word], il frammento del documento di testo non mantiene la formattazione (NPR-33213).
* Forms adattivo: Una nuova riga di una stringa in un dizionario di moduli adattivi aggiunge caratteri `&#xa;` al dizionario (NPR-33265).
* Forms adattivo: L&#39;utente non è in grado di salvare un modulo adattivo con più allegati (NPR-33214).
* Forms adattivo: I metodi `AddInstance` e `RemoveInstance` per la classe Instance Manager non aggiungono un numero dinamico di istanze per i frammenti di caricamento pigri su [!DNL Internet Explorer 11] (NPR-33201).
* Forms adattivo: Le analisi abilitate su un modulo adattivo incorporato in una pagina [!DNL Sites] non registrano i dati per gli eventi Submit e Abandon (NPR-31359).
* Forms adattivo: Quando un utente incolla il contenuto da un documento [!DNL Word] a un modulo adattivo e lo invia, il modulo adattivo inviato include caratteri unicode. Inoltre, la conversione da PDF a PDF/A non riesce a causa dei caratteri unicode (NPR-33348).
* BackendIntegration: Le richieste del modello dati del modulo non riescono a causa dello stato inattivo non corretto del token di aggiornamento (NPR-33168).
* Document Services: Il servizio Converti PDF non è in grado di convertire i documenti PDF in PostScript a causa di jar Gibson mancanti per [!DNL WebLogic] nel server [!DNL Linux] (NPR-33515, CQ-4292239).
* Document Services: Quando un utente converte un file di testo in un PDF, i caratteri giapponesi non vengono rappresentati correttamente (NPR-33239).
* Memorizzato XSS con GuideSOMProviderServlet (NPR-32701).

## Installare 6.4.8.3 {#install}

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
>Per i clienti con Feature Pack installati su AEM 6.4. I Feature Pack opzionali forniti dal Adobe  hanno dipendenze dalla versione release e dai service pack. Se avete installato Feature Pack, contattate il team AEM assistenza clienti per verificare la compatibilità di questi pacchetti con questo fix pack cumulativo per AEM 6.4.

* AEM 6.4.8.3 richiede AEM 6.4.8.0. Per istruzioni dettagliate, visitare la [documentazione sull&#39;aggiornamento](../sites-deploying/upgrade.md).
* In una distribuzione con MongoDB e più istanze, installa AEM 6.4.8.3 in una delle istanze Autore tramite Gestione pacchetti.
* Prima di installare il fix pack cumulativo, assicurarsi di disporre di uno snapshot o di un nuovo backup dell&#39;istanza AEM.
* Riavvia l’istanza prima dell’installazione. Anche se ciò è necessario solo quando l&#39;istanza è ancora in modalità di aggiornamento (e questo accade quando l&#39;istanza è stata appena aggiornata da una versione precedente), si consiglia generalmente se l&#39;istanza è in esecuzione per un periodo di tempo più lungo.

>[!NOTE]
>
>Adobe sconsiglia la rimozione o la disinstallazione del pacchetto AEM 6.4.8.3.

### Installare Cumulative Fix Pack {#install-cumulative-fix-pack}

Per installare il Cumulative Fix Pack in un’istanza AEM 6.4.8.0 esistente, effettua le seguenti operazioni:

1. Fate clic sul collegamento [Distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-3.0.zip) per scaricare il pacchetto.

1. Aprite [Gestione pacchetti](http://localhost:4502/crx/packmgr/index.jsp) e fate clic su **[!UICONTROL Carica pacchetto]** per caricare il pacchetto.

1. Selezionate il nome del pacchetto e fate clic su **[!UICONTROL Installa]**.

>[!NOTE]
>
>**La finestra di dialogo nell’interfaccia utente di Gestione pacchetti talvolta si chiude prematuramente durante l’installazione della versione 6.4.8.3**
>
>È consigliabile attendere che i registri degli errori si stabilizzino prima di accedere all’istanza. L&#39;utente deve attendere i registri specifici relativi alla disinstallazione del bundle dell&#39;utility di aggiornamento prima di assicurarsi che l&#39;installazione abbia esito positivo. Il problema si verifica in genere in Safari, ma può accadere in modo intermittente in qualsiasi browser.

### Installazione automatica {#auto-installation}

Esistono due modi per installare automaticamente AEM 6.4.8.3 in un’istanza in esecuzione:

A. Inserite il pacchetto in ..*/crx-quickstart/install* mentre il server è in esecuzione. Il pacchetto viene installato automaticamente.

B. Utilizzate l&#39; [API HTTP da Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - accertatevi di utilizzare `cmd=install&recursive=true` - in modo che il pacchetto nidificato venga installato.

>[!NOTE]
>
>AEM 6.4.8.3 non supporta l’installazione tramite bootstrap.

### Convalidare l’installazione {#validate-install}

1. La pagina Informazioni sul prodotto (*/system/console/productinfo*) ora deve mostrare la stringa di versione aggiornata &quot;Adobe Experience Manager, versione 6.4.8.3&quot; in Prodotti installati.
1. Tutti i bundle OSGi risultano come ATTIVI o FRAMMENTI nella console OSGi (usa la console Web: /system/console/bundles).
1. Il bundle OSGI org.apache.jackrabbit.oak-core è sulla versione 1.8.17 o successiva (Usa console Web: /system/console/bundle).

Per determinare la piattaforma certificata da eseguire con questa release di  AEM Sites e Assets, vedi [Requisiti tecnici](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Dopo l&#39;installazione corretta del pacchetto, viene visualizzato un messaggio informativo che indica che il pacchetto di contenuti è stato installato correttamente, ad esempio **&quot;Content Package AEM-6.4-Service-Pack-8 installato correttamente.&quot;**

### Aggiornamento dei visualizzatori Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.3 contiene la nuova versione dei visualizzatori Dynamic Media (5.10.1) che consente di verificare la presenza di nomi duplicati nella pagina dei predefiniti per immagini. Ai clienti Dynamic Media viene consigliato di eseguire il comando seguente per aggiornare i predefiniti per visualizzatori in scatola.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

che copierà i nuovi predefiniti per visualizzatori nella posizione /conf.

### Installare il pacchetto di componenti aggiuntivi per AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] rilascia i pacchetti aggiuntivi una settimana dopo la data di rilascio pianificata per il  [!DNL Experience Manager] Cumulative Fix Pack.

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms. Le correzioni apportate in AEM Forms vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi.

1. Accertatevi di aver installato AEM Cumulative Fix Pack.
1. Scaricare il pacchetto del componente aggiuntivo moduli corrispondente elencato in [ versioni di AEM Forms](https://helpx.adobe.com/it/aem-forms/kb/aem-forms-releases.html) per il sistema operativo in uso.
1. Installare il pacchetto del componente aggiuntivo dei moduli come descritto in [Installazione di pacchetti del componente aggiuntivo AEM moduli](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installazione  programma di installazione AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms in JEE. Le correzioni apportate in JEE per AEM Forms vengono distribuite tramite un programma di installazione separato.

Per informazioni sull&#39;installazione del programma di installazione cumulativo per  configurazione AEM Forms JEE e post-distribuzione, vedere [ AEM Forms JEE Patch Installer](jee-patch-installer-64.md).

### JAR Uber {#uber-jar}

Il Jar Uber per AEM 6.4.8.3 è disponibile nell&#39;archivio [Maven Central](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.3/).

Per utilizzare Uber Jar in un progetto Maven, fare riferimento all&#39;articolo [Come utilizzare Uber jar](../sites-developing/ht-projects-maven.md) e includere nel POM del progetto la seguente dipendenza:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.3</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar e altri artifact correlati sono disponibili nel repository centrale di Maven invece  repository di Public Maven Adobe (repo.adobe.com). Il file UberJar principale viene rinominato in `uber-jar-<version>.jar`. Di conseguenza, per il tag `dependency` non è presente alcun valore `classifier`, con `apis` come valore.

## Funzioni rimosse/obsolete {#removed-deprecated-features}

In questa sezione sono elencate le funzionalità rimosse o dichiarate obsolete in AEM 6.4.

| Area | Funzione obsoleta | Sostituzione | Versione |
|---|---|---|---|
| Assets | Gestisci azione tag per risorse secondarie | Nessuna sostituzione | AEM 6.4.2.0   |
| Integrazione di Assets con Adobe Creative Cloud | [AEM la ](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) condivisione delle cartelle di Creative Cloud è stata introdotta in AEM 6.2 per consentire agli utenti creativi di accedere alle risorse da AEM. Una nuova funzionalità introdotta nell’applicazione Creative Cloud, Adobe Asset Link, offre un’esperienza utente migliore e un accesso più efficace alle risorse da AEM direttamente da Photoshop, InDesign e Illustrator. Adobe non apporterà ulteriori miglioramenti alla funzionalità di condivisione cartelle. Sebbene la funzione sia inclusa in AEM, i clienti sono invitati a utilizzare la sostituzione. |  collegamento risorsa Adobe o app desktop. Per ulteriori informazioni, consulta l’articolo sull’[integrazione di AEM con Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0   |

## Problemi noti {#known-issues}

* Se esegui l&#39;aggiornamento da [!DNL Experience Manager] 6.4 a [!DNL Experience Manager] 6.5, alcuni dei bundle potrebbero non visualizzare il loro stato come `Active`. Per risolvere il problema, installate l&#39;ultimo [!DNL Experience Manager] 6.5 Service Pack.

Per informazioni sui problemi noti AEM 6.4.8.0 Service Pack, consultare le [AEM 6.4.8.0 Service Pack Note sulla versione](sp-release-notes.md).

## Bundle OSGi e pacchetti di contenuti inclusi {#osgi-bundles-and-content-packages-included}

Nei documenti di testo seguenti sono elencati i bundle OSGi e i pacchetti di contenuti inclusi in AEM 6.4.8.3.

Elenco dei bundle OSGi inclusi in AEM 6.4.8.3

[Ottieni file](assets/6.4.8.3_osgi_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.8.3

[Ottieni file](assets/6.4.8.3_content_packages.txt)

## Risorse utili {#helpful-resources}

* [Note sulla versione di AEM 6.4](../release-notes/release-notes.md)
* [Pagina del prodotto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentazione di AEM 6.4](https://helpx.adobe.com/it/support/experience-manager/6-4.html)
* Iscriviti a [ aggiornamenti dei prodotti con priorità di Adobe](https://www.adobe.com/subscription/priority-product-update.html)

## Siti con limitazioni {#restricted-sites-new}

Questi siti sono disponibili solo per i clienti. Se sei un cliente e hai bisogno di accedere, contatta il manager del tuo account Adobe.

* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/)
* [Assistenza clienti](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
