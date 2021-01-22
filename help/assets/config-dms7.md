---
title: Configurazione di Dynamic Media - Modalità Scene7
seo-title: Configurazione di Dynamic Media - Modalità Scene7
description: Informazioni su come configurare la modalità Dynamic Media - Scene7.
seo-description: Informazioni su come configurare la modalità Dynamic Media - Scene7.
uuid: 81cc208b-e95d-4a01-9817-2b6d50cfe8b8
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: cd3adbac-9868-4838-9d8a-37dde8973df4
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '5577'
ht-degree: 4%

---


# Configurazione di Dynamic Media - Modalità Scene7 {#configuring-dynamic-media-scene-mode}

Se utilizzate la configurazione di Adobe Experience Manager per ambienti diversi, ad esempio uno per lo sviluppo, uno per la gestione temporanea e uno per la produzione live, dovete configurare i Cloud Services Dynamic Media per ciascuno di questi ambienti.

## Diagramma dell&#39;architettura di Dynamic Media - Modalità Scene7 {#architecture-diagram-of-dynamic-media-scene-mode}

Nel diagramma di architettura seguente viene descritto il funzionamento della modalità Dynamic Media - Scene7.

Con la nuova architettura, AEM è responsabile delle risorse principali e delle sincronizzazioni con Dynamic Media per l’elaborazione e la pubblicazione delle risorse:

1. Quando la risorsa principale viene caricata in AEM, viene replicata in Dynamic Media. A questo punto, Dynamic Media gestisce l’elaborazione delle risorse e la generazione di rappresentazioni, come la codifica video e le varianti dinamiche di un’immagine.
1. Una volta generate le rappresentazioni, AEM accedere in modo sicuro e visualizzare in anteprima le rappresentazioni Dynamic Media remote (i file binari non vengono inviati nuovamente all&#39;istanza AEM).
1. Quando il contenuto è pronto per essere pubblicato e approvato, attiva il servizio Dynamic Media per inviare contenuti ai server di distribuzione e memorizzare il contenuto nella cache del CDN.

![chlimage_1](assets/chlimage_1.png)

## Abilitazione di Dynamic Media in modalità Scene7 {#enabling-dynamic-media-in-scene-mode}

[Dynamic Media è disattivato per impostazione predefinita. ](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) Per sfruttare le funzioni per contenuti multimediali dinamici, è necessario attivarle.

>[!NOTE]
>
>Dynamic Media - La modalità Scene7 è destinata solo all&#39;istanza di AEM Author. Di conseguenza, è necessario configurare `runmode=dynamicmedia_scene7`nell&#39;istanza di AEM Author, non nell&#39;istanza di AEM Publish.

Per abilitare Dynamic Media, è necessario avviare AEM utilizzando la `dynamicmedia_scene7` modalità di esecuzione dalla riga di comando immettendo quanto segue in una finestra terminale (la porta di esempio utilizzata è 4502):

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## (Facoltativo) Migrazione di predefiniti e configurazioni Dynamic Media da 6.3 a 6.4 Zero Downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Se state effettuando l&#39;aggiornamento AEM Dynamic Media dalla versione 6.3 alla versione 6.4 (che ora include la possibilità di eseguire senza interruzioni delle installazioni), dovete eseguire il seguente comando curl per migrare tutti i predefiniti e le configurazioni da `/etc` a `/conf` in CRXDE Lite.

>[!NOTE]
>
>Se eseguite l&#39;istanza AEM in modalità di compatibilità, ovvero se avete installato il pacchetto di compatibilità, non è necessario eseguire questi comandi.

Per migrare i predefiniti e le configurazioni personalizzati da `/etc` a `/conf`, eseguite il seguente comando curl Linux:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

Per tutti gli aggiornamenti, con o senza il pacchetto di compatibilità, potete copiare i predefiniti per visualizzatori forniti con il prodotto eseguendo il comando seguente:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## (Facoltativo) Installazione del feature pack 18912 per la migrazione in massa delle risorse {#installing-feature-pack}

Il Feature Pack 18912 consente di caricare le risorse in blocco tramite FTP, oppure di migrare le risorse dalla modalità Dynamic Media - Hybrid o Dynamic Media Classic alla modalità Dynamic Media - Scene7 in AEM. È disponibile da Adobe Professional Services.

Per ulteriori informazioni, consultate [Installazione del feature pack 18912 per la migrazione di massa delle risorse](bulk-ingest-migrate.md).

## Configurazione di Cloud Services Dynamic Media {#configuring-dynamic-media-cloud-services}

Modificare la password prima di configurare Cloud Services Dynamic Media. Dopo aver ricevuto l&#39;e-mail di provisioning con le credenziali Dynamic Media, è necessario [accedere](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) all&#39;applicazione desktop Dynamic Media Classic per cambiare la password. La password fornita nel messaggio e-mail di provisioning è generata dal sistema e deve essere solo una password temporanea. È importante aggiornare la password in modo che il Cloud Service Dynamic Media sia configurato con le credenziali corrette.

>[!NOTE]
>
>Per impostazione predefinita, il percorso di configurazione per i Cloud Services è `/content/dam`. Qualsiasi altro percorso di configurazione non è supportato dalla modalità Dynamic Media - Scene7.

Per configurare Cloud Services Dynamic Media:

1. In AEM, toccate il logo AEM per accedere alla console di navigazione globale e toccate l&#39;icona Strumenti, quindi toccate **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Nella pagina del browser di configurazione Dynamic Media, nel riquadro a sinistra, toccate **[!UICONTROL global]** e toccate **[!UICONTROL Create]**. Non toccate o selezionate l&#39;icona della cartella a sinistra di [!UICONTROL global].
1. Nella pagina [!UICONTROL Crea configurazione Dynamic Media], immettete un titolo, l&#39;indirizzo e-mail dell&#39;account Dynamic Media, la password, quindi selezionate la vostra area geografica. Questi vengono forniti  Adobe nel messaggio e-mail di provisioning. Se non avete ricevuto questo messaggio, contattate il supporto tecnico.

   Toccate **[!UICONTROL Connetti ad Dynamic Media]**.

   >[!NOTE]
   >
   >Dopo aver ricevuto l&#39;e-mail di provisioning con le credenziali Dynamic Media, [accedere a ](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) Dynamic Media Classic per cambiare la password. La password fornita nel messaggio e-mail di provisioning è generata dal sistema e deve essere solo una password temporanea. È importante aggiornare la password in modo che il servizio cloud Dynamic Media sia configurato con le credenziali corrette.

1. Se la connessione ha esito positivo, potete anche impostare quanto segue:

   * **[!UICONTROL Società]** : il nome dell&#39;account Dynamic Media. È possibile che si disponga di più account Dynamic Media per diversi marchi secondari, divisioni o diversi ambienti di produzione e di staging.
   * **[!UICONTROL Percorso cartella principale della società]**
   * **[!UICONTROL Pubblicazione delle risorse]** : l’opzione  **** Immediatamente indica che quando vengono caricate le risorse, il sistema le raccoglie e fornisce l’URL/Incorpora immediatamente. Non è necessario alcun intervento da parte degli utenti per pubblicare le risorse. L&#39;opzione **[!UICONTROL Al momento dell&#39;attivazione]** indica che è necessario pubblicare esplicitamente la risorsa prima di fornire un collegamento URL/Incorpora.
   * **[!UICONTROL Secure Preview Server]** : consente di specificare il percorso URL del server di anteprima delle rappresentazioni protette. In altre parole, dopo la generazione delle rappresentazioni, AEM accedere in modo sicuro e visualizzare in anteprima le rappresentazioni Dynamic Media remote (nessun file binario viene inviato nuovamente all&#39;istanza AEM).

      A meno che non disponiate di una disposizione speciale per utilizzare il server della vostra società o un server speciale,  Adobe consiglia di utilizzare l&#39;impostazione predefinita.
   >[!NOTE]
   >
   >Non è supportato il controllo delle versioni in DMS7. Inoltre, l’attivazione ritardata si applica solo se l’opzione **[!UICONTROL Pubblica risorse]** della pagina Modifica configurazione Dynamic Media è impostata su **[!UICONTROL All’attivazione]** e soltanto fino alla prima attivazione della risorsa.
   >
   >Dopo l’attivazione di una risorsa, tutti gli aggiornamenti vengono immediatamente pubblicati in diretta su S7 Delivery.

   ![dynamicmediaconfiguration2updated](assets/dynamicmediaconfiguration2updated.png)

1. Toccate **[!UICONTROL Salva]**.
1. Per visualizzare in modo sicuro l’anteprima del contenuto Dynamic Media prima della pubblicazione, è necessario &quot; inserire nell&#39;elenco Consentiti&quot; l’istanza di autore AEM per collegarsi ad Dynamic Media:

   * Accedete al vostro account Dynamic Media Classic: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html). Le credenziali e l&#39;accesso sono stati forniti  Adobe al momento del provisioning. Se non disponete di tali informazioni, contattate il supporto tecnico.
   * Nella barra di navigazione in alto a destra della pagina, toccate **[!UICONTROL Configurazione > Impostazione applicazione > Impostazione pubblicazione > Server immagini]**.
   * Nella pagina Pubblica su Image Server, nell’elenco a discesa Contesto pubblicazione, selezionate **[!UICONTROL Test Image Server]**.
   * Per Filtro indirizzi client, toccate **[!UICONTROL Aggiungi]**.
   * Selezionate la casella di controllo per attivare l&#39;indirizzo, quindi immettete l&#39;indirizzo IP dell&#39;istanza di AEM Author (non l&#39;IP del dispatcher).
   * Toccate **[!UICONTROL Salva]**.

Ora hai finito con la configurazione di base; è possibile utilizzare la modalità Dynamic Media - Scene7.

Se desiderate personalizzare ulteriormente la configurazione, potete eventualmente completare una qualsiasi delle attività in [(Facoltativo) Configurazione delle impostazioni avanzate in Dynamic Media - modalità Scene7](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

## (Facoltativo) Configurazione delle impostazioni avanzate in Dynamic Media - Modalità Scene7 {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Se desiderate personalizzare ulteriormente la configurazione e l&#39;impostazione della modalità Dynamic Media - Scene7 o ottimizzarne le prestazioni, potete completare una o più delle seguenti attività facoltative:

* [(Facoltativo) Configurazione e configurazione di Dynamic Media - Impostazioni modalità Scene7](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [(Facoltativo) Ottimizzazione delle prestazioni della modalità Dynamic Media - Scene7](#optional-tuning-the-performance-of-dynamic-media-scene-mode)
* [(Facoltativo) Filtrare le risorse per la replica](#optional-filtering-assets-for-replication)

### (Facoltativo) Configurazione e configurazione di Dynamic Media - Impostazioni modalità Scene7</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

In modalità di esecuzione **dynamicmedia_scene7**, l&#39;interfaccia utente di Dynamic Media Classic (Scene7) consente di apportare modifiche alle impostazioni Dynamic Media.

Per alcune delle attività di cui sopra è necessario accedere ad Dynamic Media Classic qui: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

Le attività di configurazione sono:

* [Configurazione pubblicazione per Image Server](#publishing-setup-for-image-server)
* [Configurazione delle impostazioni generali dell’applicazione](#configuring-application-general-settings)
* [Configurazione della gestione del colore](#configuring-color-management)
* [Modifica dei tipi MIME per i formati supportati](#editing-mime-types-for-supported-formats)
* [Aggiunta di tipi MIME per i formati non supportati](#adding-mime-types-for-unsupported-formats)
* [Creazione di predefiniti per set di batch per generare automaticamente set di immagini e set 360 gradi](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### Configurazione pubblicazione per Image Server {#publishing-setup-for-image-server}

Le impostazioni Impostazione pubblicazione specificano il modo in cui le risorse vengono distribuite per impostazione predefinita da Dynamic Media. Se non viene specificata alcuna impostazione, Dynamic Media distribuisce una risorsa in base alle impostazioni predefinite definite in Impostazione pubblicazione. Ad esempio, una richiesta di invio di un&#39;immagine che non include un attributo di risoluzione produce un&#39;immagine con l&#39;impostazione Risoluzione oggetto predefinita.

Per configurare Impostazione pubblicazione: in Dynamic Media Classic, toccate **[!UICONTROL Configurazione > Impostazione applicazione > Impostazione pubblicazione > Server immagini]**.

La schermata Server immagini stabilisce le impostazioni predefinite per la distribuzione delle immagini. Consultate l’interfaccia utente per una descrizione di ciascuna impostazione.

* **[!UICONTROL Attributi]**  richiesta - Queste impostazioni impongono limiti alle immagini che possono essere distribuite dal server.
* **[!UICONTROL Attributi]**  richiesta predefiniti: queste impostazioni interessano l&#39;aspetto predefinito delle immagini.
* **[!UICONTROL Attributi]**  comuni delle miniature: queste impostazioni interessano l’aspetto predefinito delle miniature.
* **[!UICONTROL Valori predefiniti per i campi]**  catalogo: queste impostazioni interessano la risoluzione e il tipo predefinito di miniatura delle immagini.
* **[!UICONTROL Attributi]**  di gestione del colore: queste impostazioni determinano quali profili colore ICC vengono utilizzati.
* **[!UICONTROL Attributi]**  di compatibilità: questa impostazione consente ai paragrafi iniziali e finali nei livelli di testo di essere trattati come nella versione 3.6 per garantire la compatibilità con le versioni precedenti.
* **[!UICONTROL Supporto]**  per la localizzazione: queste impostazioni consentono di gestire più attributi della lingua. Consente inoltre di specificare una stringa di mappa lingua in modo da definire le lingue da supportare per le varie descrizioni comandi nei visualizzatori. Per ulteriori informazioni sulla configurazione del supporto per la localizzazione, consultate [Considerazioni per la configurazione della localizzazione delle risorse](https://help.adobe.com/en_US/scene7/using/WS997f1dc4cb0179f034e07dc31412799d19a-8000.html).

#### Configurazione delle impostazioni generali dell&#39;applicazione {#configuring-application-general-settings}

Per aprire la pagina [!UICONTROL Impostazioni generali applicazione], nella barra di navigazione globale di Dynamic Media Classic toccare **[!UICONTROL Configurazione > Impostazione applicazione > Impostazioni generali]**.

**[!UICONTROL Server]**  - Al provisioning dell&#39;account, Dynamic Media fornisce automaticamente i server assegnati alla società. Questi server vengono utilizzati per creare stringhe URL per il sito Web e le applicazioni. Queste chiamate URL sono specifiche per il vostro account. Non modificate i nomi dei server, a meno che non sia espressamente richiesto dal supporto AEM.

**[!UICONTROL Sovrascrivi immagini]**  - Dynamic Media non consente a due file di avere lo stesso nome. L’ID URL di ogni elemento (il nome del file senza l’estensione) deve essere univoco. Queste opzioni specificano la modalità di caricamento delle risorse sostitutive: se sostituiscono l’originale o diventano duplicati. Le risorse duplicate vengono rinominate con il suffisso &quot;-1&quot; (ad esempio, sedia.tif viene rinominato sedia-1.tif). Queste opzioni interessano le risorse caricate in una cartella diversa dall’originale o le risorse con un’estensione file diversa dall’originale (ad esempio, JPG, TIF o PNG).

* **[!UICONTROL Sovrascrivi in cartella corrente, nome/estensione]**  stessa immagine base: questa opzione rappresenta la regola di sostituzione più restrittiva. Richiede che l’immagine sostitutiva venga caricata nella stessa cartella dell’originale e che abbia la stessa estensione del nome file dell’originale. Se questi requisiti non sono soddisfatti, viene creato un duplicato.

>[!NOTE]
>
>Per mantenere la coerenza con AEM, selezionare **[!UICONTROL Sovrascrivi nella cartella corrente, nome/estensione base uguale]**.

* **[!UICONTROL Sovrascrivi in qualsiasi cartella, nome/estensione]**  della risorsa base - Richiede che l’immagine sostitutiva abbia la stessa estensione del nome file dell’immagine originale (ad esempio,  `chair.jpg` sostituisce  `chair.jpg` e non  `chair.tif`). Tuttavia, potete caricare l’immagine sostitutiva in una cartella diversa da quella dell’originale. L’immagine aggiornata si trova nella nuova cartella; il file non può più essere trovato nella posizione originale.
* **[!UICONTROL Sovrascrivi in qualsiasi cartella, nome della stessa risorsa di base, indipendentemente dall’estensione]** . Questa opzione è la regola di sostituzione più inclusiva. Potete caricare un’immagine sostitutiva in una cartella diversa da quella dell’originale, caricare un file con un’estensione diversa e sostituire il file originale. Se il file originale si trova in un’altra cartella, l’immagine sostitutiva si trova nella nuova cartella in cui è stata caricata.

**[!UICONTROL Profili]**  colore predefiniti - Per ulteriori informazioni, consultate  [Configurazione della ](#configuring-color-management) gestione del colore.

>[!NOTE]
>
>Per impostazione predefinita, il sistema mostra 15 rappresentazioni quando selezioni **[!UICONTROL Rappresentazioni]** e 15 predefiniti visualizzatore quando fai clic su **[!UICONTROL Visualizzatori]** nella vista Dettaglio della risorsa. Puoi aumentare questo limite. Consultate [Incremento del numero di predefiniti per immagini che visualizzano](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) o [Aumento del numero di predefiniti per visualizzatori che vengono visualizzati](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### Configurazione della gestione del colore {#configuring-color-management}

La gestione dinamica del colore dei contenuti multimediali consente di colorare le risorse corrette. Con la correzione del colore, le risorse inserite mantengono lo spazio colore (RGB, CMYK, Grigio) e il profilo colore incorporato. Quando si richiede una rappresentazione dinamica, il colore dell&#39;immagine viene corretto nello spazio colore di destinazione utilizzando l&#39;output CMYK, RGB o Grigio. Consultate [Configurazione dei predefiniti per immagini](managing-image-presets.md).

Per configurare le proprietà colore predefinite per attivare la correzione colore durante la richiesta delle immagini:

1. [Effettuate l&#39;accesso ad Dynamic Media ](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) Classic utilizzando le credenziali fornite durante il provisioning. Passare a **[!UICONTROL Configurazione > Impostazione applicazione]**.
1. Espandi l’area **[!UICONTROL Publish Setup (Impostazione pubblicazione)]** e seleziona **[!UICONTROL Image Server]**. Per le istanze di pubblicazione, imposta **[!UICONTROL Contesto di pubblicazione]** su **[!UICONTROL Image Server]**.
1. Scorrete fino alla proprietà da modificare, ad esempio una proprietà nell&#39;area **[!UICONTROL Attributi di gestione del colore]**.

   Potete impostare le seguenti proprietà di correzione del colore:

   * [!UICONTROL Spazio]  colore predefinito CMYK - Nome del profilo colore CMYK predefinito
   * [!UICONTROL Scala di grigio Spazio]  colore predefinito - Nome del profilo colore grigio predefinito
   * [!UICONTROL Spazio]  colore predefinito RGB - Nome del profilo colore RGB predefinito
   * [!UICONTROL Intento]  di rendering conversione colore - Specifica l&#39;intento di rendering. I valori accettabili sono `perceptual`, `relative` `colometric`, `saturation` e `absolute colometric`.  Adobe consiglia `relative` come impostazione predefinita.

1. Toccate **[!UICONTROL Salva]**.

Ad esempio, puoi impostare **[!UICONTROL Spazio colore predefinito RGB]** su `sRGB` e **[!UICONTROL Spazio colore predefinito CMYK]** su `WebCoated`.

In questo modo si effettua quanto segue:

* Attiva la correzione del colore per le immagini RGB e CMYK.
* Si presume che le immagini RGB che non hanno un profilo colore siano nello spazio colore `sRGB`.
* Si presume che le immagini CMYK che non hanno un profilo colore siano nello spazio colore `WebCoated`.
* Le rappresentazioni dinamiche che restituiscono l&#39;output RGB lo restituiranno nello spazio colore `sRGB`.
* Le rappresentazioni dinamiche che restituiscono l&#39;output CMYK, lo restituiranno nello spazio colore `WebCoated`.

#### Modifica dei tipi MIME per i formati supportati {#editing-mime-types-for-supported-formats}

Potete definire quali tipi di risorse elaborare da Dynamic Media e personalizzare i parametri di elaborazione avanzata delle risorse. Ad esempio, potete specificare i parametri di elaborazione delle risorse per effettuare le seguenti operazioni:

* Convertite un Adobe PDF  in una risorsa eCatalog.
* Convertite un documento Adobe Photoshop  (.PSD) in una risorsa modello banner per la personalizzazione.
* Rasterizzare un file Adobe Illustrator  (.AI) o un file  Encapsulated Postscript di Adobe Photoshop (.EPS).
* [I ](/help/assets/video-profiles.md) profili video e i  [profili ](/help/assets/image-profiles.md) immagine possono essere utilizzati rispettivamente per definire l’elaborazione di video e immagini.

Consulta [Caricamento delle risorse](managing-assets-touch-ui.md#uploading-assets).

**Per modificare i tipi mime per i formati supportati**

1. In AEM, toccate il logo AEM per accedere alla console di navigazione globale, quindi toccate l&#39;icona **[!UICONTROL Strumenti]** (martello) e passate a **[!UICONTROL Generale > CRXDE Lite]**.
1. Nella barra a sinistra, andate a:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. Sotto la cartella `mimeTypes`, selezionate un tipo mime.
1. Sul lato destro della pagina CRXDE Lite, nella parte inferiore:

   * fare doppio clic sul campo **[!UICONTROL enabled]**. Per impostazione predefinita, tutti i tipi di mime delle risorse sono attivati (impostati su **[!UICONTROL true]**), il che significa che le risorse verranno sincronizzate in Dynamic Media per l&#39;elaborazione. Se desiderate escludere l&#39;elaborazione di questo tipo di mime della risorsa, modificate questa impostazione in **[!UICONTROL false]**.
   * fare doppio clic su **[!UICONTROL jobParam]** per aprire il relativo campo di testo associato. Consultate [Tipi mime supportati](assets-formats.md#supported-mime-types) per un elenco dei valori di parametro di elaborazione consentiti che potete utilizzare per un determinato tipo mime.

1. Effettua una delle operazioni seguenti:

   * Ripetete i passaggi da 3 a 4 per modificare altri tipi di mime.
   * Nella barra dei menu della pagina dei CRXDE Lite, toccate **[!UICONTROL Salva tutto]**.

1. Nell&#39;angolo superiore sinistro della pagina, toccare **[!UICONTROL CRXDE Lite]** per tornare alla AEM.

#### Aggiunta di tipi MIME personalizzati per i formati non supportati {#adding-custom-mime-types-for-unsupported-formats}

All’interno di AEM Assets puoi aggiungere tipi MIME personalizzati per i formati non supportati. Per garantire che i nuovi nodi aggiunti nel CRXDE Lite non vengano eliminati da AEM, è necessario assicurarsi di spostare il tipo MIME prima di **[!UICONTROL image_]** e il relativo valore abilitato sia impostato su **[!UICONTROL false]**.

**Aggiunta di tipi MIME personalizzati per i formati non supportati**

1. Da AEM, fare clic su **[!UICONTROL Strumenti > Operazioni > Console Web]**.

   ![console Web](assets/2019-08-02_16-13-14.png)

1. Viene visualizzata una nuova scheda del browser nella pagina **[!UICONTROL Configurazione della console Web Adobe Experience Manager]**.

   ![console Web](assets/2019-08-02_16-17-29.png)

1. Nella pagina, scorrete verso il basso fino al nome **[!UICONTROL Adobe CQ Scene7 Asset MIME type Service]**. A destra del nome, toccare **[!UICONTROL Modifica i valori di configurazione]** (icona matita).

   ![modifica](assets/2019-08-02_16-44-56.png)

1. Nella pagina **[!UICONTROL Adobe CQ Scene7 Asset MIME type Service]** fare clic sull&#39;icona con il segno più `+`. La posizione nella tabella in cui si fa clic sul segno più per aggiungere il nuovo tipo mime è insignificante.

   ![plussaggio](assets/2019-08-02_16-27-27.png)

1. Digitare `DWG=image/vnd.dwg` nel campo di testo vuoto appena aggiunto.

   L&#39;esempio `DWG=image/vnd.dwg` è solo a scopo illustrativo. Il tipo MIME aggiunto qui può essere qualsiasi altro formato non supportato.

   ![dwg](assets/2019-08-02_16-36-36.png)

1. Nell&#39;angolo inferiore destro della pagina, fare clic su **[!UICONTROL Salva]**.

   A questo punto, è possibile chiudere la scheda del browser con la pagina di configurazione della console Web di Adobe Experience Manager aperta.

1. Tornate alla scheda del browser con la console AEM aperta.

1. Da AEM, fare clic su **[!UICONTROL Strumenti > Generale > CRXDE Lite]**.

   ![crxdelite](assets/2019-08-02_16-55-41.png)

1. Nella barra a sinistra, andate a:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Trascinate il tipo mime `image_vnd.dwg` e rilasciatelo direttamente sopra `image_` nella struttura.

   ![drag](assets/CRXDELite_CQDOC-14627.png)

1. Con il tipo mime `image_vnd.dwg` ancora selezionato nella struttura, dalla scheda **[!UICONTROL Proprietà]**, nella riga **[!UICONTROL enabled]**, nell&#39;intestazione della colonna **[!UICONTROL Valore]** fare doppio clic sul valore per aprire l&#39;elenco a discesa **[!UICONTROL Valore]**.

1. Digitare `false` nel campo (oppure selezionare `false` dall&#39;elenco a discesa).

   ![falsevalue](assets/2019-08-02_16_60_30.png)

1. Nell&#39;angolo superiore sinistro della pagina dei CRXDE Lite, fare clic su **[!UICONTROL Salva tutto]**.

#### Creazione di predefiniti per set di batch per generare automaticamente set di immagini e set 360 gradi {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

Usate i predefiniti per set di batch per automatizzare la creazione di set di immagini o set 360 gradi durante il caricamento delle risorse in Dynamic Media.

In primo luogo, definite la convenzione di denominazione in base alla quale le risorse devono essere raggruppate in un set. Potete quindi creare un predefinito per set di batch con un nome univoco e un set autonomo di istruzioni che definisca come creare il set utilizzando immagini che corrispondono alle convenzioni di denominazione definite nella definizione del predefinito.

Quando caricate dei file, Dynamic Media crea automaticamente un set con tutti i file che corrispondono alla convenzione di denominazione definita nei predefiniti attivi.

**Configurazione della denominazione predefinita**

Create una convenzione di denominazione predefinita da usare in qualsiasi predefinito per set di batch. La convenzione di denominazione predefinita selezionata nella definizione del predefinito per set di batch può essere l’unica impostazione effettivamente necessaria per generare i set in batch per la società. Per usare la convenzione di denominazione predefinita, viene creato un predefinito per set di batch. Potete creare tutti i predefiniti per set di batch con convenzioni di denominazione alternative e personalizzate necessarie per un particolare set di contenuti, nei casi in cui esiste un’eccezione alla denominazione predefinita definita dalla società.

Sebbene l’impostazione di una convenzione di denominazione predefinita non sia necessaria per utilizzare le funzionalità dei predefiniti per set di batch, è comunque consigliabile utilizzare la convenzione di denominazione predefinita per definire tutti gli elementi di denominazione da raggruppare in un set, semplificando così la creazione dei set di batch.

In alternativa, è possibile utilizzare **[!UICONTROL Visualizza codice]** senza campi modulo. In questa visualizzazione potete creare definizioni complete delle convenzioni di denominazione utilizzando espressioni regolari.

Sono disponibili due elementi per la definizione: **[!UICONTROL Match]** e **[!UICONTROL Base Name]**. Questi campi consentono di definire tutti gli elementi di una convenzione di denominazione e identificare la parte della convenzione utilizzata per denominare il set in cui sono contenuti. Una convenzione di denominazione individuale di una società può utilizzare una o più righe di definizione per ciascuno di questi elementi. Potete usare tutte le righe necessarie per creare una definizione univoca e raggrupparle in elementi distinti, ad esempio per l’immagine principale, l’elemento colore, l’elemento visualizzazione alternativa e l’elemento campione.

**Per configurare la denominazione predefinita:**

1. Accedete al vostro account Dynamic Media Classic (Scene7): [www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Le credenziali e l&#39;accesso sono stati forniti  Adobe al momento del provisioning. Se non disponete di tali informazioni, contattate il supporto tecnico.

1. Nella barra di navigazione accanto alla parte superiore della pagina, toccate **[!UICONTROL Configurazione > Impostazione applicazione > Predefiniti set di batch > Denominazione predefinita].**
1. Per specificare come visualizzare e immettere le informazioni di ciascun elemento, seleziona **[!UICONTROL Visualizza modulo]** o **[!UICONTROL Visualizza codice]**.

   È possibile selezionare la casella di controllo **[!UICONTROL Visualizza codice]** per visualizzare il valore dell&#39;espressione regolare creato accanto alle selezioni del modulo. Potete immettere o modificare questi valori per definire meglio gli elementi della convenzione di denominazione, se la visualizzazione modulo vi limita per qualsiasi motivo. Se i valori non possono essere analizzati nella visualizzazione modulo, i campi del modulo diventano inattivi.

   >[!NOTE]
   >
   >I campi del modulo disattivati non eseguono alcuna convalida relativa alla correttezza delle espressioni regolari. Vengono visualizzati i risultati dell&#39;espressione regolare che si sta creando per ogni elemento dopo la riga Risultato. L&#39;espressione regolare completa è visibile nella parte inferiore della pagina.

1. Espandete ciascun elemento come necessario e inserite le convenzioni di denominazione da utilizzare.
1. Se necessario, effettuate una delle seguenti operazioni:

   * Toccate **[!UICONTROL Aggiungi]** per aggiungere un&#39;altra convenzione di denominazione a un elemento.
   * Toccate **[!UICONTROL Remove]** per eliminare una convenzione di denominazione per un elemento.

1. Effettua una delle operazioni seguenti:

   * Toccate **[!UICONTROL Salva con nome]** e digitate un nome per il predefinito.
   * Toccate **[!UICONTROL Salva]** se state modificando un predefinito esistente.

**Creazione di un predefinito per set di batch**

Dynamic Media utilizza i predefiniti per set di batch per organizzare le risorse in set di immagini (immagini alternative, opzioni colore, 360 rotazioni) da visualizzare nei visualizzatori. I predefiniti per set di batch vengono eseguiti automaticamente insieme ai processi di caricamento delle risorse in Dynamic Media.

Potete creare, modificare e gestire i predefiniti per set di batch. Esistono due moduli per le definizioni dei predefiniti per set di batch: uno per una convenzione di denominazione eventualmente configurata e uno per convenzioni di denominazione generate al momento.

Potete definire un predefinito per set di batch con i campi modulo o con il metodo del codice, che consente di usare espressioni regolari. Come in Denominazione predefinita, è possibile scegliere [!UICONTROL Visualizza codice] allo stesso tempo che si sta definendo in [!UICONTROL Visualizzazione modulo] e utilizzare espressioni regolari per creare le definizioni. In alternativa, è possibile deselezionare una delle due visualizzazioni per utilizzare esclusivamente l&#39;una o l&#39;altra.

**Per creare un predefinito per set di batch:**

1. Accedete al vostro account Dynamic Media Classic (Scene7): [www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Le credenziali e l&#39;accesso sono stati forniti  Adobe al momento del provisioning. Se non disponete di tali informazioni, contattate il supporto tecnico.

1. Nella barra di navigazione accanto alla parte superiore della pagina, toccate **[!UICONTROL Configurazione > Impostazione applicazione > Predefiniti set di batch > Predefinito set di batch].**

   Tenere presente che la vista predefinita è [!UICONTROL Visualizza modulo], come impostato nell&#39;angolo superiore destro della pagina [!UICONTROL Dettagli].

1. Nel pannello Elenco predefiniti, toccate **[!UICONTROL Aggiungi]** per attivare i campi delle definizioni nel pannello **[!UICONTROL Dettagli]** sul lato destro dello schermo.
1. Nel pannello **[!UICONTROL Dettagli]**, digitate un nome per il predefinito nel campo **[!UICONTROL Nome predefinito]**.
1. Nel menu a discesa **[!UICONTROL Tipo set di batch]**, selezionate un tipo di predefinito.
1. Effettua una delle operazioni seguenti:

   * Se utilizzate una convenzione di denominazione predefinita precedentemente impostata in **[!UICONTROL Impostazione applicazione > Predefiniti set di batch > Denominazione predefinita]**, espandete **[!UICONTROL Convenzioni di denominazione delle risorse]**, quindi nell&#39;elenco a discesa **[!UICONTROL Denominazione file]** toccate **[!UICONTROL Predefinito]**.
   * Per definire una nuova convenzione di denominazione durante la configurazione del predefinito, toccate **[!UICONTROL Convenzioni di denominazione delle risorse]**, quindi nell&#39;elenco a discesa **[!UICONTROL Denominazione file]** toccate **[!UICONTROL Personalizzato]**.

1. Per [!UICONTROL Ordine sequenza], definite l&#39;ordine in cui vengono visualizzate le immagini dopo che il set è stato raggruppato in Dynamic Media.

   Per impostazione predefinita, le risorse sono ordinate in ordine alfabetico. Tuttavia, potete definire l’ordine utilizzando un elenco separato da virgole di espressioni regolari.

1. Per **[!UICONTROL Imposta denominazione]** e **[!UICONTROL Convenzione di creazione]**, specificate il suffisso o il prefisso per il nome di base definito nella **[!UICONTROL Convenzione di denominazione delle risorse]**. Inoltre, definite la posizione in cui verrà creato il set nella struttura di cartelle di Dynamic Media.

   Se definite un numero elevato di set, potete preferire tenerli separati dalle cartelle contenenti le risorse stesse. Ad esempio, potete creare una cartella per i set di immagini e inserire qui i set generati.

1. Nel pannello **[!UICONTROL Dettagli]**, toccare **[!UICONTROL Salva]**.
1. Toccate **[!UICONTROL Active]** accanto al nuovo nome del predefinito.

   Attivando il predefinito si garantisce che quando caricate le risorse su Dynamic Media, il predefinito per set di batch venga applicato per generare il set.

**Creazione di un predefinito per set di batch per la generazione automatica di un set 360 gradi 2D**

Potete usare il tipo di set di batch **[!UICONTROL Set 360 gradi con asse multiplo]** per creare una ricetta che automatizza la generazione di set 360 gradi 2D. Il raggruppamento di immagini utilizza espressioni regolari Riga e Colonna per allineare correttamente le risorse di immagine nella posizione corrispondente nell’array multidimensionale. Non esiste un numero minimo o massimo di righe o colonne da includere in un set 360 gradi con più assi.

Ad esempio, se desiderate creare un set 360 gradi con più assi denominato `spin-2dspin`, Sono disponibili una serie di immagini per set 360 gradi contenenti tre righe, con 12 immagini per riga. Le immagini sono denominate come segue:

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

Con queste informazioni, la ricetta [!UICONTROL Tipo set di batch] può essere creata come segue:

![chlimage_1-1](assets/chlimage_1-1.png)

Il raggruppamento per la parte del nome della risorsa condivisa del set 360 gradi viene aggiunto al campo **[!UICONTROL Match (Corrispondenza)]** (come evidenziato). La parte variabile del nome della risorsa, contenente la riga e la colonna, viene aggiunta rispettivamente ai campi **[!UICONTROL Riga]** e **[!UICONTROL Colonna]**.

Quando il set 360 gradi viene caricato e pubblicato, potete attivare il nome della definizione del set 360 gradi 2D elencata in **[!UICONTROL Predefiniti per set di batch]** nella finestra di dialogo **[!UICONTROL Opzioni processo di caricamento]**.

**Per creare un predefinito per set di batch per la generazione automatica di un set 360 gradi 2D:**

1. Accedete al vostro account Dynamic Media Classic (Scene7): [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Le credenziali e l&#39;accesso sono stati forniti  Adobe al momento del provisioning. Se non disponete di tali informazioni, contattate il supporto tecnico.

1. Nella barra di navigazione accanto alla parte superiore della pagina, toccate **[!UICONTROL Configurazione > Impostazione applicazione > Predefiniti set di batch > Predefinito set di batch]**.

   Tenere presente che la vista predefinita è [!UICONTROL Visualizza modulo], come impostato nell&#39;angolo superiore destro della pagina [!UICONTROL Dettagli].

1. Nel pannello **[!UICONTROL Elenco predefiniti]**, toccate **[!UICONTROL Aggiungi]** per attivare i campi delle definizioni nel pannello **[!UICONTROL Dettagli]** sul lato destro dello schermo.
1. Nel pannello **[!UICONTROL Dettagli]**, digitate un nome per il predefinito nel campo [!UICONTROL Nome predefinito].
1. Nel menu a discesa **[!UICONTROL Tipo set di batch]**, selezionare **[!UICONTROL Set risorse]**.
1. Nell&#39;elenco a discesa **[!UICONTROL Sottotipo]**, selezionare **[!UICONTROL Set 360 gradi con asse multiplo]**.
1. Espandete **[!UICONTROL Convenzioni di denominazione delle risorse]**, quindi nell&#39;elenco a discesa **[!UICONTROL Denominazione file]** toccate **[!UICONTROL Personalizzato]**.
1. Utilizza gli attributi **[!UICONTROL Match (Corrispondenza)]** e, facoltativamente, **[!UICONTROL Nome base]** per definire un’espressione regolare per la denominazione delle risorse dell’immagine che compongono il raggruppamento.

   Ad esempio, l&#39;espressione regolare letterale Corrispondenza potrebbe essere simile a quella riportata di seguito:

   `(w+)-w+-w+`

1. Espandete **[!UICONTROL Posizione colonna riga]**, quindi definite il formato del nome per la posizione della risorsa immagine nell’array di set 360 gradi 2D.

   Utilizzare le parentesi per racchiudere la posizione di riga o colonna nel nome del file.

   Ad esempio, per l&#39;espressione regolare riga, potrebbe essere simile a quella riportata di seguito:

   `\w+-R([0-9]+)-\w+`

   o

   `\w+-(\d+)-\w+`

   Per l&#39;espressione regolare della colonna, potrebbe essere simile a quella riportata di seguito:

   `\w+-\w+-C([0-9]+)`

   o

   `\w+-\w+-C(\d+)`

   Ricorda che questi sono solo esempi. Potete creare le espressioni regolari in base alle vostre esigenze.

   >[!NOTE]
   >
   >Se la combinazione di espressioni regolari per riga e colonna non è in grado di determinare la posizione della risorsa all’interno dell’array di set 360 gradi multidimensionale, la risorsa non viene aggiunta al set e viene registrato un errore.

1. Per **[!UICONTROL Imposta denominazione]** e **[!UICONTROL Convenzione di creazione]**, specificate il suffisso o il prefisso per il nome di base definito nella **[!UICONTROL Convenzione di denominazione delle risorse]**.

   Inoltre, definite la posizione in cui verrà creato il set 360 gradi nella struttura di cartelle di Dynamic Media Classic.

   Se definite un numero elevato di set, potete preferire tenerli separati dalle cartelle contenenti le risorse stesse. Ad esempio, create una cartella Set 360 gradi in cui inserire i set generati.

1. Nel pannello **[!UICONTROL Dettagli]**, toccare **[!UICONTROL Salva]**.
1. Toccate **[!UICONTROL Active]** accanto al nuovo nome del predefinito.

   Attivando il predefinito si garantisce che quando caricate le risorse su Dynamic Media, il predefinito per set di batch venga applicato per generare il set.

### (Facoltativo) Ottimizzazione delle prestazioni di Dynamic Media - Modalità Scene7 {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Per mantenere la modalità Dynamic Media - Scene7 in esecuzione senza problemi,   consiglia di impostare le prestazioni di sincronizzazione/ottimizzare la scalabilità come segue:

* Aggiornamento dei parametri di processo predefiniti per l’elaborazione di diversi formati di file.
* Aggiornamento dei thread di lavoro predefiniti per il flusso di lavoro Granite (risorse video) in coda.
* Aggiornamento dei thread di lavoro transitori Granite (immagini e risorse non video) predefiniti per il flusso di lavoro in coda.
* Aggiornamento delle connessioni di caricamento massime nel server Dynamic Media Classic.

#### Aggiornamento dei parametri di processo predefiniti per l’elaborazione di diversi formati di file

Potete ottimizzare i parametri di processo per velocizzare l’elaborazione quando caricate i file. Ad esempio, se caricate file PSD ma non desiderate elaborarli come modelli, potete impostare l’estrazione dei livelli su false (disattivato). In tal caso, il parametro del processo sintonizzato apparirebbe come `process=None&createTemplate=false`.

 Adobe consiglia di utilizzare i seguenti parametri di processo &quot;sintonizzati&quot; per i file PDF, Postscript e PSD:

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| Tipo di file | Parametri di processo consigliati |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

Per aggiornare uno di questi parametri, segui i passaggi descritti in [Abilitazione dei parametri di caricamento di risorse/Dynamic Media Classic basati su tipi MIME supporto dei parametri di caricamento di ](#enabling-mime-type-based-assets-scene-upload-job-parameter-support).

#### Aggiornamento della coda del flusso di lavoro transitorio Granite {#updating-the-granite-transient-workflow-queue}

La coda del flusso di lavoro di transito Granite viene utilizzata per il flusso di lavoro **[!UICONTROL DAM Update Asset]**. In Dynamic Media, viene utilizzata per l’assimilazione e l’elaborazione delle immagini.

**Per aggiornare la coda del flusso di lavoro transitorio Granite**

1. Andate su [https://&lt;server>/system/console/configMgr](http://localhost:4502/system/console/configMgr) e cercate **[!UICONTROL Coda: Granite Transient Workflow Queue]**.

   >[!NOTE]
   >
   >È necessaria una ricerca di testo invece di un URL diretto, perché il PID OSGi viene generato in modo dinamico.

1. Nel campo **[!UICONTROL Processi paralleli massimi]**, impostate il numero sul valore desiderato.

   È possibile aumentare il numero massimo di **[!UICONTROL processi paralleli]** per supportare in modo adeguato il caricamento di file in Dynamic Media. Il valore esatto dipende dalla capacità hardware. In alcuni scenari, ad esempio una migrazione iniziale o un caricamento in blocco una tantum, potete usare un valore elevato. Tenete presente, tuttavia, che l&#39;utilizzo di un valore elevato (ad esempio, due volte il numero di core) può avere effetti negativi su altre attività simultanee. È quindi necessario verificare e regolare il valore in base al caso di utilizzo specifico.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Toccate **[!UICONTROL Salva]**.

#### Aggiornamento della coda del flusso di lavoro Granite {#updating-the-granite-workflow-queue}

La coda Flusso di lavoro Granite viene utilizzata per i flussi di lavoro non transitori. In Dynamic Media, veniva utilizzato per elaborare i video con il flusso di lavoro **[!UICONTROL Dynamic Media Encode Video]**.

**Per aggiornare la coda del flusso di lavoro Granite:**

1. Andate su `https://<server>/system/console/configMgr` e cercate **[!UICONTROL Coda: Granite Workflow Queue]**.

   >[!NOTE]
   >
   >È necessaria una ricerca di testo invece di un URL diretto, perché il PID OSGi viene generato in modo dinamico.

1. Nel campo **[!UICONTROL Processi paralleli massimi]**, impostate il numero sul valore desiderato.

   Per impostazione predefinita, il numero massimo di processi paralleli dipende dal numero di core CPU disponibili. Ad esempio, su un server di 4 core assegna 2 thread di lavoro. (Un valore compreso tra 0,0 e 1,0 è basato sul rapporto, altrimenti qualsiasi numero maggiore di 1 assegnerà il numero di thread di lavoro.)

   Per la maggior parte dei casi di utilizzo, l&#39;impostazione predefinita 0.5 è sufficiente.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Toccate **[!UICONTROL Salva]**.

#### Aggiornamento della connessione di caricamento Scene7 {#updating-the-scene-upload-connection}

L&#39;impostazione di Scene7 Upload Connection sincronizza AEM risorse sui server Dynamic Media Classic.

**Per aggiornare la connessione di caricamento Scene7:**

1. Accedi a `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. Nel campo [!UICONTROL Numero di connessioni] e/o nel campo [!UICONTROL Timeout processo attivo], modificare il numero come desiderato.

   L&#39;impostazione **[!UICONTROL Numero di connessioni]** controlla il numero massimo di connessioni HTTP consentite per il caricamento di AEM su Dynamic Media; in genere, il valore predefinito di 10 connessioni è sufficiente.

   L&#39;impostazione **[!UICONTROL Timeout processo attivo]** determina il tempo di attesa per la pubblicazione delle risorse Dynamic Media caricate nel server di consegna. Per impostazione predefinita, questo valore è di 2100 secondi o 35 minuti.

   Per la maggior parte dei casi di utilizzo, è sufficiente impostare 2100.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Toccate **[!UICONTROL Salva]**.

### (Facoltativo) Filtrare le risorse per la replica {#optional-filtering-assets-for-replication}

Nelle distribuzioni non Dynamic Media, potete replicare *tutte le risorse *(sia immagini che video) dall&#39;ambiente di authoring AEM al nodo di pubblicazione AEM. Questo flusso di lavoro è necessario perché i server di pubblicazione AEM forniscono anche le risorse.

Tuttavia, nelle distribuzioni Dynamic Media, poiché le risorse vengono distribuite tramite il servizio cloud, non è necessario replicare le stesse risorse AEM nodi di pubblicazione. Tale flusso di lavoro &quot;ibrido per la pubblicazione&quot; evita costi di archiviazione aggiuntivi e tempi di elaborazione più lunghi per la replica delle risorse. Altri contenuti, come le pagine Sito, continuano a essere gestiti dai nodi di pubblicazione AEM.

I filtri forniscono un modo per escludere le risorse *escludendo* dalla replica nel nodo di pubblicazione AEM.

#### Utilizzo dei filtri risorse predefiniti per la replica {#using-default-asset-filters-for-replication}

Se utilizzate Dynamic Media per l&#39;imaging e/o il video, potete utilizzare i filtri predefiniti forniti così come sono. Per impostazione predefinita, sono attivi i seguenti filtri:

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Filtro</strong></td> 
   <td><strong>Tipo mime</strong></td> 
   <td><strong>Rappresentazioni</strong></td> 
  </tr> 
  <tr> 
   <td>Distribuzione delle immagini Dynamic Media</td> 
   <td><p>filter-images</p> <p>set di filtri</p> <p> </p> </td> 
   <td><p>Inizia con <strong>image/</strong></p> <p>Contiene <strong>application/</strong> e termina con <strong>set</strong>.</p> </td> 
   <td>Le "immagini filtro" predefinite (applicabili a singole risorse di immagini, comprese le immagini interattive) e i "set di filtri" (applicabili a set 360 gradi, set di immagini, set di file multimediali diversi e set di caroselli) consentono di: 
    <ul> 
     <li>Escludete dalla replica le rappresentazioni originali dell’immagine e dell’immagine statica.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Distribuzione video Dynamic Media</td> 
   <td>filter-video</td> 
   <td>Inizia con <strong>video/</strong></td> 
   <td>Il "filtro-video" preimpostato: 
    <ul> 
     <li>Escludere dalla replica le rappresentazioni video e thumbnail statiche originali.<br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>I filtri si applicano ai tipi mime e non possono essere specifici per un percorso.

#### Personalizzazione dei filtri risorse per la replica {#customizing-asset-filters-for-replication}

1. In AEM, toccate il logo AEM per accedere alla console di navigazione globale e toccate l&#39;icona **[!UICONTROL Strumenti]**, quindi andate a **[!UICONTROL Generale > CRXDE Lite]**.
1. Nella struttura delle cartelle a sinistra, andate a `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` per esaminare i filtri.

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. Per definire il tipo di mime per il filtro, potete individuare il tipo mime nel modo seguente:

   Nella barra a sinistra, espandete **[!UICONTROL content > dam > &lt;`locate_your_asset`> > jcr:content > metadata]**, quindi nella tabella individuate **[!UICONTROL dc:format]**.

   L’elemento grafico seguente è un esempio del percorso di una risorsa a dc:format.

   ![chlimage_1-3](assets/chlimage_1-3.png)

   Tenere presente che la `dc:format` della risorsa `Fiji Red.jpg` è `image/jpeg`.

   Affinché questo filtro possa essere applicato a tutte le immagini, indipendentemente dal loro formato, impostate il valore su `image/*` dove `*` è un&#39;espressione regolare applicata a tutte le immagini di qualsiasi formato.

   Affinché il filtro possa essere applicato solo alle immagini di tipo JPEG, immettete un valore di `image/jpeg`.

1. Definite le rappresentazioni da includere o escludere dalla replica.

   I caratteri utilizzabili per filtrare la replica includono quanto segue:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Carattere da usare</strong></td> 
    <td><strong>Filtrare le risorse per la replica</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>Carattere jolly<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>Include le risorse per la replica.</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>Esclude le risorse dalla replica.</td> 
    </tr> 
    </tbody> 
   </table>

   Andate a **content/dam/&lt;`locate your asset`>/jcr:content/renditions**.

   L’elemento grafico seguente è un esempio delle rappresentazioni di una risorsa.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Se si desidera replicare solo l&#39;originale, è necessario inserire `+original`.

