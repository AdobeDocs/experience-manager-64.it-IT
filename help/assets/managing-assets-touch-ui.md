---
title: Gestire le risorse digitali utilizzando [!DNL Experience Manager] Risorse
description: Scopri le varie attività di gestione e modifica delle risorse che puoi eseguire utilizzando l’interfaccia utente ottimizzata per il tocco di [!DNL Experience Manager] Risorse
contentOwner: AG
feature: Asset Management,Search,Renditions,Collaboration
role: User
mini-toc-levels: 4
exl-id: aa1a702b-18dd-496b-a6e0-aa593af6e57c
source-git-commit: 14633d278f1e6fe7c1a47168006b8387c150e63d
workflow-type: tm+mt
source-wordcount: '10145'
ht-degree: 3%

---

# Gestire le risorse digitali {#managing-assets-with-the-touch-optimized-ui}

Scopri le varie attività di gestione e modifica delle risorse che puoi eseguire utilizzando l’interfaccia utente ottimizzata per il tocco di [!DNL Experience Manager] Risorse.

Questo articolo descrive come gestire e modificare le risorse utilizzando l’interfaccia utente ottimizzata per il tocco di Adobe Experience Manager Assets. Per una conoscenza elementare dell&#39;interfaccia utente, vedi [Gestione di base dell’interfaccia utente touch](/help/sites-authoring/basic-handling.md). Per gestire i frammenti di contenuto, consulta [Gestione dei frammenti di contenuto](content-fragments-managing.md) risorse.

## Creare cartelle {#create-folders}

Quando si organizza una raccolta di risorse, ad esempio, tutte le `Nature` immagini, puoi creare cartelle per mantenerle unite. Puoi utilizzare le cartelle per suddividere in categorie e organizzare le risorse. [!DNL Experience Manager] Per migliorare il funzionamento di Assets non è necessario organizzare le risorse nelle cartelle.

>[!NOTE]
>
>* Condivisione di una cartella di risorse del tipo `sling:OrderedFolder` non è supportato quando si condivide su Marketing Cloud. Per condividere una cartella, non selezionare Ordinato durante la creazione di una cartella.
>* L&#39;Experience Manager non consente di utilizzare `subassets` parola come nome di una cartella. È una parola chiave riservata al nodo che contiene risorse secondarie per le risorse composte.


1. Passa alla posizione nella cartella delle risorse digitali in cui desideri creare una nuova cartella.
1. Nel menu , fai clic su **[!UICONTROL Crea]**. Seleziona **[!UICONTROL Nuova cartella]**.
1. In **[!UICONTROL Titolo]** specificare un nome di cartella. Per impostazione predefinita, DAM utilizza il titolo fornito come nome della cartella. Una volta creata la cartella, è possibile sostituire l’impostazione predefinita e specificare un altro nome di cartella.
1. Fai clic su **[!UICONTROL Crea]**. La cartella viene visualizzata nella cartella delle risorse digitali.

I seguenti caratteri (elenco separato da spazi) non sono supportati:

* il nome del file risorsa non deve contenere  `* / : [ \ \ ] | # % { } ? &`
* il nome della cartella di risorse non deve contenere  `* / : [ \ \ ] | # % { } ? \" . ^ ; + & \t`

## Caricare le risorse {#uploading-assets}

Puoi caricare vari tipi di risorse (immagini, file PDF, file RAW e così via) dalla cartella locale o da un&#39;unità di rete in [!DNL Experience Manager] Risorse.

>[!NOTE]
>
>In modalità Dynamic Media - Scene7, puoi caricare solo le risorse le cui dimensioni di file sono pari o inferiori a 2 GB.

Puoi scegliere di caricare le risorse nelle cartelle con o senza un profilo di elaborazione ad esse assegnato.

Per le cartelle a cui è assegnato un profilo di elaborazione, il nome del profilo viene visualizzato sulla miniatura nella vista a schede. Nella vista a elenco, il nome del profilo viene visualizzato nella **[!UICONTROL Profilo di elaborazione]** colonna. Vedi [Profili di elaborazione](processing-profiles.md).

Prima di caricare una risorsa, accertati che si trovi in una [formato supportato](assets-formats.md).

**Per caricare le risorse**:

1. Nell’interfaccia web Assets, individua il percorso in cui desideri aggiungere risorse digitali.
1. Per caricare le risorse, effettua una delle seguenti operazioni:

   * Sulla barra degli strumenti, tocca **[!UICONTROL Crea]** icona. Quindi, dal menu, tocca **[!UICONTROL File]**. Se necessario, rinomina il file nella finestra di dialogo visualizzata.
   * In un browser che supporta HTML5, trascina le risorse direttamente sull’interfaccia. La finestra di dialogo per rinominare il file non viene visualizzata.

   ![crea_menu](assets/create_menu.png)

   Per selezionare più file, premi il tasto Ctrl/Comando e seleziona le risorse nella finestra di dialogo del selettore file. Da un iPad, è possibile selezionare un solo file alla volta.

   Puoi sospendere il caricamento di risorse di grandi dimensioni (superiori a 500 MB) e riprenderlo più tardi dalla stessa pagina. Tocca **[!UICONTROL Pausa]** accanto alla barra di avanzamento visualizzata all’avvio del caricamento.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   È possibile configurare la dimensione sopra la quale una risorsa viene considerata una risorsa di grandi dimensioni. Ad esempio, puoi configurare il sistema in modo che consideri le risorse superiori a 1000 MB (anziché 500 MB) come risorse di grandi dimensioni. In questo caso, il **[!UICONTROL Pausa]** nella barra di avanzamento viene visualizzato quando vengono caricate risorse di dimensioni superiori a 1000 MB.

   La **[!UICONTROL Pausa]** Il pulsante non mostra se un file superiore a 1000 MB viene caricato con un file inferiore a 1000 MB. Tuttavia, se si annulla il caricamento di file inferiori a 1000 MB, il **[!UICONTROL Pausa]** viene visualizzato il pulsante .

   Per modificare il limite di dimensione, configura il `chunkUploadMinFileSize` proprietà `fileupload`nel repository CRX.

   Quando fai clic sul pulsante **[!UICONTROL Pausa]** icona, passa a un **[!UICONTROL Play]** icona. Per riprendere il caricamento, fai clic sul pulsante **[!UICONTROL Play]** icona.

   ![chlimage_1-6](assets/chlimage_1-6.png)

   Per annullare un caricamento in corso, fai clic sul pulsante `X` accanto alla barra di avanzamento. Quando si annulla l&#39;operazione di caricamento, [!DNL Experience Manager] Le risorse eliminano la parte parzialmente caricata della risorsa.

   La possibilità di riprendere il caricamento è particolarmente utile in scenari con scarsa larghezza di banda e problemi di rete, in cui il caricamento di una risorsa di grandi dimensioni richiede molto tempo. Puoi sospendere l’operazione di caricamento e continuare in un secondo momento quando la situazione migliora. Quando riprendi, il caricamento inizia dal punto in cui l&#39;hai messo in pausa.

   Durante l&#39;operazione di caricamento, [!DNL Experience Manager] salva le parti della risorsa caricata come blocchi di dati nell’archivio CRX. Al termine del caricamento, [!DNL Experience Manager] consolida questi blocchi in un singolo blocco di dati nel repository.

   Per configurare l’attività di pulizia per i processi di caricamento dei blocchi non completati, vai a `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.

   Se carichi una risorsa con lo stesso nome di quella già disponibile nel percorso in cui stai caricando la risorsa, viene visualizzata una finestra di avviso.

   Puoi scegliere di sostituire una risorsa esistente, crearne un’altra versione o mantenere entrambe rinominando la nuova risorsa caricata. Se sostituisci una risorsa esistente, i metadati della risorsa e le eventuali modifiche e cronologia precedenti (ad esempio annotazioni, raccolti e così via) vengono eliminati. Se scegli di mantenere entrambe le risorse, la nuova risorsa viene rinominata.

   ![chlimage_1-7](assets/chlimage_1-7.png)

   >[!NOTE]
   >
   >Quando selezioni **[!UICONTROL Sostituisci]** in **[!UICONTROL Conflitto tra nomi]** L’ID della risorsa viene rigenerato per la nuova risorsa. Questo ID è diverso dall’ID della risorsa precedente.
   >
   >Se **[!UICONTROL Informazioni sulle risorse]** è abilitato per tenere traccia di impression/clic con Adobe Analytics. Questo ID risorsa rigenerato invalida i dati acquisiti per la risorsa in Adobe Analytics.

   Se la risorsa caricata esiste in [!DNL Experience Manager] Risorse, **[!UICONTROL Duplicati rilevati]** La finestra di dialogo avverte che stai tentando di caricare una risorsa duplicata. La finestra di dialogo viene visualizzata solo se il valore di checksum SHA 1 del binario della risorsa esistente corrisponde al valore di checksum della risorsa caricata. In questo caso, i nomi delle attività sono irrilevanti. In altre parole, la finestra di dialogo può persino essere visualizzata per le risorse con nomi diversi se i valori SHA 1 per i rispettivi binari sono gli stessi.

   >[!NOTE]
   >
   >La **[!UICONTROL Duplicati rilevati]** la finestra di dialogo viene visualizzata solo quando **[!UICONTROL Rilevamento di duplicati]** è abilitata. Per abilitare **[!UICONTROL Rilevamento di duplicati]** funzionalità, vedi [Abilitazione del rilevamento dei duplicati](duplicate-detection.md).

   ![chlimage_1-8](assets/chlimage_1-8.png)

   Tocca **[!UICONTROL Mantieni]** per mantenere la risorsa duplicata in [!DNL Experience Manager] Risorse. Tocca  **[!UICONTROL Elimina]** per eliminare la risorsa duplicata caricata.

   [!DNL Experience Manager] Le risorse impediscono il caricamento di risorse con caratteri non consentiti nei nomi dei file. Se provi a caricare una risorsa che include i caratteri non consentiti, [!DNL Experience Manager] Risorse visualizza un messaggio di avviso relativo alla presenza di caratteri non consentiti nel nome del file e interrompe il caricamento finché non rimuovi questi caratteri o li carichi con un nome consentito.

   Per soddisfare convenzioni specifiche di denominazione dei file per la tua organizzazione, la **[!UICONTROL Caricare risorse]** consente di specificare nomi lunghi per i file caricati.

   ![chlimage_1-9](assets/chlimage_1-9.png)

   Tuttavia, i seguenti caratteri (elenco separato da spazi) non sono supportati:
   * il nome del file risorsa non deve contenere  `* / : [ \ \ ] | # % { } ? &`
   * il nome della cartella di risorse non deve contenere  `* / : [ \ \ ] | # % { } ? \" . ^ ; + & \t`

   Inoltre, l’interfaccia di Assets visualizza la risorsa più recente caricata o la cartella creata per prima in tutte le visualizzazioni (**[!UICONTROL Vista a schede]**, **[!UICONTROL Vista a elenco]** e **[!UICONTROL Vista a colonne]**).

   Spesso, durante il caricamento simultaneo di risorse di grandi dimensioni o più risorse, gli indicatori visivi consentono di valutare lo stato di avanzamento. La **[!UICONTROL Avanzamento caricamento]** visualizza il conteggio dei file caricati correttamente e i file che non sono stati caricati.

   ![chlimage_1-10](assets/chlimage_1-10.png)

   Se annulli l’operazione di caricamento prima che i file vengano caricati, [!DNL Experience Manager] Le risorse smettono di caricare il file corrente e aggiornano il contenuto. Tuttavia, i file già caricati non vengono eliminati.

### Caricamenti seriali {#serial-uploads}

Il caricamento di numerose risorse in blocco consuma risorse di sistema significative che possono influire negativamente sulle prestazioni del [!DNL Experience Manager] distribuzione. I potenziali colli di bottiglia possono essere la connessione Internet, le operazioni di lettura e scrittura su disco, le limitazioni del browser web sul numero di richieste POST sul caricamento di risorse simultanee. L&#39;operazione di caricamento in blocco può non riuscire o terminare prematuramente. In altre parole, [!DNL Experience Manager] le risorse potrebbero perdere alcuni file durante l’acquisizione di una serie di file o nel complesso non riuscire a acquisire alcun file.

Per superare questa situazione, [!DNL Experience Manager] Le risorse acquisiscono una risorsa alla volta (caricamento seriale) durante un’operazione di caricamento in blocco, anziché tutte le risorse simultaneamente.

Il caricamento seriale delle risorse è abilitato per impostazione predefinita. Per disattivare la funzione e consentire il caricamento simultaneo, sovrapponi la `fileupload` in CRXDe e imposta il valore del `parallelUploads` proprietà di `true`.

### Caricare risorse tramite FTP {#uploading-assets-using-ftp}

Dynamic Media consente il caricamento batch delle risorse tramite server FTP. Se vuoi caricare risorse di grandi dimensioni (>1 GB) o caricare intere cartelle e sottocartelle, devi utilizzare l&#39;FTP. Puoi anche impostare il caricamento FTP in modo che si verifichi su base ricorrente pianificata.

>[!NOTE]
>
>In modalità Dynamic Media - Scene7, puoi caricare solo le risorse le cui dimensioni di file sono pari o inferiori a 2 GB.

>[!NOTE]
>
>Per caricare le risorse tramite FTP in Dynamic Media - modalità di installazione Scene7 feature pack (FP) 18912 on [!DNL Experience Manager] autore. Contatta l’Assistenza clienti Adobe per accedere a FP-18912 e completare la configurazione del tuo account FTP. Vedi [Installazione del feature pack 18912 per la migrazione di massa delle risorse](/help/assets/bulk-ingest-migrate.md).
>
>Se utilizzi l’FTP per caricare le risorse, le impostazioni di caricamento specificate in [!DNL Experience Manager] vengono ignorati. Vengono invece utilizzate le regole di elaborazione dei file definite in Dynamic Media Classic.

**Per caricare le risorse tramite FTP**

1. Utilizzando il client FTP desiderato, accedi al server FTP utilizzando il nome utente e la password FTP ricevuti dall&#39;e-mail di provisioning. Nel client FTP, carica file o cartelle sul server FTP.
1. Apri [applicazione desktop Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), quindi accedi al tuo account utilizzando le credenziali ricevute dall’e-mail di provisioning.
1. Nella barra di navigazione globale, tocca **[!UICONTROL Carica]**.
1. Sulla **[!UICONTROL Carica]** , vicino all’angolo superiore sinistro, tocca **[!UICONTROL Tramite FTP]** scheda .
1. Sul lato sinistro della pagina, scegli una cartella FTP da cui caricare i file; sul lato destro della pagina, scegli una cartella di destinazione.
1. Nell’angolo in basso a destra della pagina, tocca **[!UICONTROL Opzioni processo]** quindi impostate le opzioni desiderate in base alle risorse nella cartella selezionata.

   Vedi [Opzioni processo di caricamento](#upload-job-options).

   >[!NOTE]
   >
   >Quando carichi le risorse tramite FTP, le opzioni del processo di caricamento impostate in Dynamic Media Classic hanno un precedente sui parametri di elaborazione delle risorse impostati in AEM.

1. Nell&#39;angolo in basso a destra della **[!UICONTROL Opzioni processo di caricamento]** finestra di dialogo, tocca **[!UICONTROL Salva]**.
1. Nell&#39;angolo in basso a destra della **[!UICONTROL Carica]** pagina, tocca **[!UICONTROL Invia caricamento]**.

   Per visualizzare l’avanzamento del caricamento, nella barra di navigazione globale tocca **[!UICONTROL Processi]**. La **[!UICONTROL Processi]** visualizza l’avanzamento del caricamento. Puoi continuare a lavorare in [!DNL Experience Manager] e tornare alla pagina Processi in Dynamic Media Classic in qualsiasi momento per esaminare un processo in corso.

   Per annullare un processo di caricamento in corso, tocca **[!UICONTROL Annulla]** accanto al **[!UICONTROL Durata]** tempo.

#### Opzioni processo di caricamento {#upload-job-options}

| Opzione Carica | Opzione secondaria | Descrizione |
|---|---|---|
| Nome processo |  | Il nome predefinito precompilato nel campo di testo include la parte del nome inserita dall’utente e la data e l’ora. Puoi utilizzare il nome predefinito o immettere un nome della tua creazione per questo processo di caricamento. <br>Il processo e gli altri processi di caricamento e pubblicazione vengono registrati nella pagina Processi , dove puoi controllare lo stato dei processi. |
| Pubblica dopo il caricamento |  | Pubblica automaticamente le risorse caricate. |
| Sovrascrivi in qualsiasi cartella, nome come risorsa base, ignora estensione |  | Seleziona questa opzione se desideri che i file caricati sostituiscano quelli esistenti con gli stessi nomi. Il nome di questa opzione potrebbe essere diverso, a seconda delle impostazioni in **[!UICONTROL Impostazione applicazione]** > **[!UICONTROL Impostazioni generali]** > **[!UICONTROL Carica nell’applicazione]** > **[!UICONTROL Sovrascrivi immagini]**. |
| Decomprimi file ZIP o TAR al caricamento |  |  |
| Opzioni processo |  | Tocca o fai clic su **[!UICONTROL Opzioni processo]** per aprire [!UICONTROL Opzioni processo di caricamento] e scegli le opzioni che interessano l’intero processo di caricamento. Queste opzioni sono le stesse per tutti i tipi di file.<br>Puoi scegliere le opzioni predefinite per il caricamento dei file a partire dalla pagina Impostazioni generali applicazione. Per aprire la pagina, scegli **[!UICONTROL Configurazione]** > **[!UICONTROL Impostazione applicazione]**. Tocca **[!UICONTROL Opzioni di caricamento predefinite]** per aprire [!UICONTROL Opzioni processo di caricamento] finestra di dialogo. |
|  | Quando   | Selezionare Una tantum o Ricorrente. Per impostare un lavoro ricorrente, scegli un’opzione Ripeti (Giornaliero, Settimanale, Mensile o Personalizzato) per specificare quando vuoi che il processo di caricamento FTP si ripeta. Quindi specifica le opzioni di pianificazione in base alle esigenze. |
|  | Includi sottocartelle | Carica tutte le sottocartelle all’interno della cartella che desideri caricare. I nomi della cartella e delle relative sottocartelle caricate vengono inseriti automaticamente in [!DNL Experience Manager] Risorse. |
|  | Opzioni di ritaglio | Per ritagliare manualmente i lati di un’immagine, selezionate il menu Ritaglio e scegliete Manuale. Quindi immetti il numero di pixel da ritagliare da qualsiasi lato o lato dell’immagine. La quantità di immagine ritagliata dipende dall’impostazione ppi (pixel per pollice) nel file di immagine. Ad esempio, se l’immagine viene visualizzata a 150 ppi e immetti 75 nelle caselle di testo In alto, A destra, In basso e A sinistra, viene ritagliato mezzo pollice da ciascun lato.<br> Per ritagliare automaticamente i pixel dello spazio bianco da un’immagine, aprite il menu Ritaglio, scegliete Manuale e immettete le misurazioni dei pixel nei campi In alto, A destra, In basso e A sinistra per ritagliare dai lati. Potete anche scegliere Rifila dal menu Ritaglia e scegliere le seguenti opzioni:<br> **Rifila in base a** <ul><li>**Colore** - Scegliere l&#39;opzione Colore. Selezionate quindi il menu Angolo (Corner) e scegliete l’angolo dell’immagine con il colore che rappresenta meglio lo spazio bianco da ritagliare.</li><li>**Trasparenza** - Scegliere l&#39;opzione Trasparenza.<br> **Tolleranza** - Trascinate il cursore per specificare una tolleranza da 0 a 1.Per il ritaglio in base al colore, specificate 0 per ritagliare i pixel solo se corrispondono esattamente al colore selezionato nell’angolo dell’immagine. I numeri più vicini a 1 consentono una maggiore differenza di colore.<br>Per il ritaglio in base alla trasparenza, specificare 0 per ritagliare i pixel solo se sono trasparenti. I numeri più vicini a 1 consentono una maggiore trasparenza.</li></ul><br>Queste opzioni di ritaglio non sono distruttive. |
|  | Opzioni del profilo colore | Scegli una conversione del colore quando crei file ottimizzati utilizzati per la distribuzione:<ul><li>Conservazione colore predefinita: mantiene i colori dell&#39;immagine sorgente ogni volta che le immagini contengono informazioni sullo spazio colore; non vi è alcuna conversione del colore. Quasi tutte le immagini oggi hanno il profilo colore appropriato già incorporato. Tuttavia, se un&#39;immagine sorgente CMYK non contiene un profilo colore incorporato, i colori vengono convertiti in spazio colore sRGB (standard Rosso Verde Blu). sRGB è lo spazio colore consigliato per la visualizzazione di immagini su pagine web.</li><li>Mantieni spazio colore originale: Mantiene i colori originali senza alcuna conversione al punto. Per le immagini prive di un profilo colore incorporato, qualsiasi conversione di colore viene effettuata utilizzando i profili colore predefiniti configurati nelle impostazioni di pubblicazione. I profili colore potrebbero non essere allineati al colore nei file creati con questa opzione. Pertanto, si consiglia di utilizzare l&#39;opzione Conservazione colore predefinita.</li><li>Personalizzato Da > A<br> Apre i menu in modo da poter scegliere uno spazio colore Converti da e Converti in. Questa opzione avanzata sostituisce tutte le informazioni sui colori incorporate nel file di origine. Selezionare questa opzione quando tutte le immagini che si stanno inviando contengono dati di profilo colore errati o mancanti.</li></ul> |
|  | Opzioni di modifica delle immagini | È possibile mantenere le maschere di ritaglio nelle immagini e scegliere un profilo colore.<br> Vedi [Impostazione delle opzioni di modifica delle immagini al caricamento](#setting-image-editing-options-at-upload). |
|  | Opzioni Postscript | È possibile rasterizzare file di PostScript®, ritagliare file, mantenere sfondi trasparenti, scegliere una risoluzione e scegliere uno spazio colore.<br> Vedi [Impostazione delle opzioni di caricamento PostScript e Illustrator](#setting-postscript-and-illustrator-upload-options). |
|  | Opzioni Photoshop | È possibile creare modelli da file Adobe® Photoshop®, mantenere i livelli, specificare il nome dei livelli, estrarre il testo e specificare il modo in cui le immagini vengono ancorate ai modelli.<br> I modelli non sono supportati in AEM.<br> Vedi [Impostazione delle opzioni di caricamento di Photoshop](#setting-photoshop-upload-options). |
|  | Opzioni di PDF | È possibile rasterizzare i file, estrarre parole di ricerca e collegamenti, generare automaticamente un eCatalog, impostare la risoluzione e scegliere uno spazio colore.<br> Gli eCatalog non sono supportati in AEM. <br> Vedi [Impostazione delle opzioni di caricamento di PDF ](#setting-pdf-upload-options)<br>**Nota**: Il numero massimo di pagine per un PDF da considerare per l’estrazione è 5000 per i nuovi caricamenti. Questo limite verrà modificato in 100 pagine (per tutti i PDF) il 31 dicembre 2022. Vedi anche [Limiti Dynamic Media](/help/assets/limitations.md). |
|  | Opzioni Illustrator | È possibile rasterizzare i file Adobe Illustrator®, mantenere sfondi trasparenti, scegliere una risoluzione e scegliere uno spazio colore.<br> Vedi [Impostazione delle opzioni di caricamento PostScript e Illustrator](#setting-postscript-and-illustrator-upload-options). |
|  | Opzioni eVideo | È possibile transcodificare un file video scegliendo un predefinito per video.<br> Vedi [Impostazione delle opzioni di caricamento di eVideo](#setting-evideo-upload-options). |
|  | Predefiniti set di batch | Per creare un set di immagini o un set 360 gradi dai file caricati, fai clic sulla colonna Attivo per il predefinito da utilizzare. Puoi selezionare più di un predefinito. Puoi creare i predefiniti nella pagina Impostazione applicazione/Predefiniti set di batch di Dynamic Media Classic.<br> Vedi [Configurazione dei predefiniti per set di batch per generare automaticamente set di immagini e set 360 gradi](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) per ulteriori informazioni sulla creazione di predefiniti per set di batch.<br> Vedi [Impostazione dei predefiniti per set di batch al caricamento](#setting-batch-set-presets-at-upload). |

#### Imposta le opzioni di modifica delle immagini al caricamento {#setting-image-editing-options-at-upload}

Durante il caricamento di file di immagine, inclusi i file AI, EPS e PSD, puoi effettuare le seguenti azioni di modifica in **[!UICONTROL Opzioni processo di caricamento]** finestra di dialogo:

* Ritaglia lo spazio bianco dal bordo delle immagini (vedi descrizione nella tabella precedente).
* Ritaglia manualmente dai lati delle immagini (vedi descrizione nella tabella precedente).
* Scegli un profilo colore (consulta la descrizione dell’opzione nella tabella precedente).
* Create una maschera da un tracciato di ritaglio.
* Nitidezza delle immagini con opzioni di mascheramento definite
* Sfondo Knockout

| Opzione | Opzione secondaria | Descrizione |
|---|---|---|
| Crea maschera dal tracciato di ritaglio |  | Crea una maschera per l&#39;immagine in base alle informazioni del relativo tracciato di ritaglio. Questa opzione si applica alle immagini create con applicazioni di modifica delle immagini in cui è stato creato un tracciato di ritaglio. |
| Maschera di contrasto |  | Consente di regolare con precisione un effetto filtro di nitidezza sull’immagine ricampionata verso il basso finale, controllando l’intensità dell’effetto, il raggio dell’effetto (misurato in pixel) e una soglia di contrasto ignorata.<br> Questo effetto utilizza le stesse opzioni del filtro Maschera definizione dettagli di Photoshop. Contrariamente a quanto suggerisce il nome, Maschera definizione dettagli è un filtro di nitidezza. In Maschera definizione dettagli impostare le opzioni desiderate. Le opzioni di impostazione sono descritte in quanto segue: |
|  | Quantità | Controlla la quantità di contrasto applicata ai pixel del bordo.<br> Pensatelo come l&#39;intensità dell&#39;effetto. La differenza principale tra i valori di quantità di Maschera definizione dettagli in Dynamic Media e i valori di quantità in Adobe Photoshop, è che Photoshop ha un intervallo di quantità compreso tra l’1% e il 500%. considerando che, in Dynamic Media, l&#39;intervallo di valori è compreso tra 0,0 e 5,0. Un valore pari a 5,0 corrisponde approssimativamente al 500% in Photoshop; il valore 0,9 equivale al 90% e così via. |
|  | Raggio | Controlla il raggio dell&#39;effetto. L&#39;intervallo di valori è compreso tra 0 e 250.<br> L&#39;effetto viene eseguito su tutti i pixel di un&#39;immagine e si irradiano da tutti i pixel in tutte le direzioni. Il raggio viene misurato in pixel. Ad esempio, per ottenere un effetto di nitidezza simile per un&#39;immagine da 2000 x 2000 pixel e un&#39;immagine da 500 x 500 pixel, è necessario impostare un raggio di due pixel sull&#39;immagine da 2000 x 2000 pixel e un valore di raggio di un pixel sull&#39;immagine da 500 x 50 pixel. Per un’immagine con più pixel viene utilizzato un valore più grande. |
|  | Soglia | La soglia è un intervallo di contrasto ignorato quando viene applicato il filtro Maschera definizione dettagli. È importante in modo che non venga introdotto alcun &quot;rumore&quot; a un&#39;immagine quando si utilizza questo filtro. L&#39;intervallo di valori è compreso tra 0 e 255, ovvero il numero di passaggi di luminosità in un&#39;immagine in scala di grigi. 0=nero, 128=grigio 50% e 255=bianco.<br> Ad esempio, con un valore di soglia pari a 12 vengono ignorate le variazioni lievi di luminosità nell’incarnato per evitare l’aggiunta di rumore, ma viene comunque aggiunto il contrasto lungo i bordi delle aree di contrasto, ad esempio in cui le ciglia incontrano l’incarnato.<br> Ad esempio, se scegli una foto del volto di un utente, la Maschera definizione dettagli influisce sulle parti contrastanti dell’immagine, come ad esempio il punto in cui le ciglia e la pelle si incontrano per creare un’area di contrasto evidente e la pelle uniforme stessa. Anche la pelle più liscia presenta sottili cambiamenti nei valori di luminosità. Se non utilizzi un valore di soglia, il filtro accentua queste sottili modifiche nei pixel dell’interfaccia. A sua volta, viene creato un effetto rumoroso e indesiderato mentre il contrasto sulle ciglia viene aumentato, aumentando la nitidezza.<br> Per evitare questo problema, viene introdotto un valore di soglia che indica al filtro di ignorare i pixel che non cambiano radicalmente il contrasto, come la pelle liscia.<br> Nell&#39;immagine della cerniera mostrata in precedenza, notate la texture accanto alle cerniere. Il rumore dell&#39;immagine è visibile perché i valori di soglia erano troppo bassi per eliminare il rumore. |
|  | Monocromatico | Selezionare per applicare una maschera di contrasto alla luminosità dell&#39;immagine (intensità).<br> Deseleziona per applicare una maschera di contrasto a ciascun componente di colore separatamente. |
| Sfondo Knockout |  | Rimuove automaticamente lo sfondo di un’immagine quando viene caricata. Questa tecnica è utile per attirare l&#39;attenzione su un particolare oggetto e farlo risaltare da uno sfondo occupato. Seleziona per abilitare o &quot;attivare&quot; la funzione Sfondo di blocco e le seguenti opzioni secondarie: |
|  | Angoli | Obbligatorio.<br> Angolo dell’immagine utilizzato per definire il colore di sfondo da forare.<br> Puoi scegliere tra **In alto a sinistra**, **In basso a sinistra**, **In alto a destra** oppure **In basso a destra**. |
|  | Metodo di riempimento | Obbligatorio.<br> Controlla la trasparenza dei pixel dalla posizione Angolo impostata.<br> Puoi scegliere tra i seguenti metodi di riempimento: <ul><li>**Riempimento Flood** - Trasforma tutti i pixel trasparenti che corrispondono all&#39;angolo specificato e ad esso collegati.</li><li>**Corrispondenza pixel** - rende trasparenti tutti i pixel corrispondenti, indipendentemente dalla loro posizione sull&#39;immagine.</li></ul> |
|  | Tolleranza | Facoltativo.<br> Controlla la quantità consentita di variazione nella corrispondenza dei colori dei pixel in base alla posizione dell&#39;angolo impostata.<br> Utilizza un valore di 0.0 per far corrispondere esattamente i colori dei pixel oppure utilizza un valore di 1.0 per consentire la variazione maggiore. |

#### Impostare le opzioni di caricamento PostScript e Illustrator {#setting-postscript-and-illustrator-upload-options}

Quando carichi i file immagine PostScript (EPS) o Illustrator (AI), puoi formattarli in vari modi. È possibile rasterizzare i file, mantenere lo sfondo trasparente, scegliere una risoluzione e scegliere uno spazio colore. Le opzioni per la formattazione dei file PostScript e Illustrator sono disponibili nella finestra di dialogo Opzioni processo di caricamento in Opzioni PostScript e Opzioni Illustrator.

| Opzione | Opzione secondaria | Descrizione |
|---|---|---|
| Elaborazione |  | Scegli **[!UICONTROL Rasterizza]** per convertire la grafica vettoriale nel file in formato bitmap. |
| Mantenere lo sfondo trasparente nell&#39;immagine renderizzata |  | Mantenere la trasparenza in background del file. |
| Risoluzione |  | Determina l&#39;impostazione della risoluzione. Questa impostazione determina quanti pixel vengono visualizzati per pollice nel file. |
| Spazio colore |  | Selezionare il menu Spazio colore e scegliere tra le seguenti opzioni di spazio colore: |
|  | Rileva automaticamente | Mantiene lo spazio colore del file. |
|  | Forza come RGB | Si converte nello spazio colore di RGB. |
|  | Forza come CMYK | Si converte nello spazio colore CMYK. |
|  | Forza come scala di grigi | Converte lo spazio colore in scala di grigi. |

#### Impostare le opzioni di caricamento di Photoshop {#setting-photoshop-upload-options}

I file PSD (Photoshop Document) vengono utilizzati più spesso per creare modelli di immagine. Quando carichi un file PSD, puoi creare automaticamente un modello di immagine dal file (seleziona l’opzione Crea modello nella schermata Carica ).

Dynamic Media crea più immagini da un file PSD con livelli se utilizzi il file per creare un modello; crea un&#39;immagine per ogni livello.

Utilizza la **[!UICONTROL Opzioni di ritaglio]** e **[!UICONTROL Opzioni del profilo colore]**, descritto in precedenza, con le opzioni di caricamento di Photoshop.

>[!NOTE]
>
>I modelli non sono supportati in AEM.

| Opzione | Opzione secondaria | Descrizione |
|---|---|---|
| Gestisci livelli |  | Racchiude gli eventuali livelli di PSD in singole risorse. I livelli delle risorse rimangono associati al PSD. Per visualizzarli, aprite il file PSD in visualizzazione Dettagli e selezionate il pannello dei livelli. |
| Crea modello |  | Crea un modello dai livelli nel file PSD. |
| Estrai testo |  | Estrae il testo in modo che gli utenti possano cercare il testo in un visualizzatore. |
| Estendi livelli a dimensione sfondo |  | Estende le dimensioni dei livelli immagine ritagliati alle dimensioni del livello di sfondo. |
| Denominazione dei livelli |  | I livelli nel file PSD vengono caricati come immagini separate. |
|  | Nome livello | Assegna un nome alle immagini dopo i relativi nomi di livello nel file PSD. Ad esempio, un livello denominato Tag prezzo nel file PSD originale diventa un’immagine denominata Tag prezzo . Tuttavia, se i nomi dei livelli nel file PSD sono nomi di livello Photoshop predefiniti (Sfondo, Livello 1, Livello 2 e così via), le immagini vengono denominate in base ai numeri dei rispettivi livelli nel file PSD, non in base ai nomi dei livelli predefiniti. |
|  | Photoshop e numero di livelli | Assegna un nome alle immagini dopo i relativi numeri di livello nel file PSD, ignorando i nomi dei livelli originali. Le immagini vengono denominate con il nome del file Photoshop e un numero di livello aggiunto. Ad esempio, il secondo livello di un file denominato Spring Ad.psd si chiama Spring Ad_2 anche se in Photoshop era presente un nome non predefinito. |
|  | Photoshop e nome livello | Assegna un nome alle immagini dopo il file PSD seguito dal nome del livello o dal numero del livello. Il numero del livello viene utilizzato se i nomi dei livelli nel file PSD sono nomi di livello Photoshop predefiniti. Ad esempio, un livello denominato Tag prezzo in un file PSD denominato SpringAd è denominato Tag Ad_Price di primavera. Un livello con il nome predefinito Layer 2 si chiama Spring Ad_2. |
| Ancoraggio |  | Specifica il modo in cui le immagini vengono ancorate nei modelli generati dalla composizione a livelli prodotta dal file PSD. Per impostazione predefinita, l’ancoraggio è al centro. Un ancoraggio centrale consente alle immagini sostitutive di riempire al meglio lo stesso spazio, indipendentemente dalle proporzioni dell&#39;immagine sostitutiva. Le immagini con un aspetto diverso che sostituiscono questa immagine, quando fanno riferimento al modello e utilizzano la sostituzione di parametri, occupano effettivamente lo stesso spazio. Passa a un’impostazione diversa se l’applicazione richiede le immagini sostitutive per riempire lo spazio allocato nel modello. |

#### Impostare le opzioni di caricamento di PDF {#setting-pdf-upload-options}

Quando carichi un file PDF, puoi formattarlo in vari modi. Ritagliate le pagine, estraete le parole di ricerca, immettete una risoluzione pixel per pollice e scegliete uno spazio colore. I file PDF contengono spesso un margine di taglio, indicatori di ritaglio, segni di registrazione e altri segni della stampante. È possibile ritagliare questi segni dai lati delle pagine durante il caricamento di un file PDF.

Il numero massimo di pagine per un PDF da considerare per l’estrazione è 5000 per i nuovi caricamenti. Questo limite verrà modificato in 100 pagine (per tutti i PDF) il 31 dicembre 2022. Vedi anche [Limiti Dynamic Media](/help/assets/limitations.md).

>[!NOTE]
>
>Gli eCatalog non sono supportati in AEM.

Scegli tra le seguenti opzioni:

| Opzione | Opzione secondaria | Descrizione |
|---|---|---|
| Elaborazione | Rasterizza | (Impostazione predefinita) Esegue l’striping delle pagine nel file PDF e converte la grafica vettoriale in immagini bitmap. Scegli questa opzione per creare un eCatalog. |
| Estrai | Cerca parole | Estrae le parole dal file PDF in modo che la ricerca nel file possa essere eseguita per parola chiave in un visualizzatore di eCatalog. |
|  | Collegamenti | Estrae i collegamenti dai file PDF e li converte in mappe immagine utilizzate in un visualizzatore di eCatalog. |
| Genera automaticamente eCatalog da più PDF di pagina |  | Crea automaticamente un eCatalog dal file PDF. L’eCatalog prende il nome dal file PDF caricato. Questa opzione è disponibile solo se il file PDF viene rasterizzato durante il caricamento. |
| Risoluzione |  | Determina l&#39;impostazione della risoluzione. Questa impostazione determina quanti pixel vengono visualizzati per pollice nel file PDF. Il valore predefinito è 150. |
| Spazio colore |  | Selezionare il menu Spazio colore e scegliere uno spazio colore per il file PDF. La maggior parte dei file PDF dispone sia di immagini a colori RGB che CMYK. Lo spazio colore RGB è preferibile per la visualizzazione online. |
|  | Rileva automaticamente | Mantiene lo spazio colore del file PDF. |
|  | Converti in RGB | Si converte nello spazio colore di RGB. |
|  | Converti in CMYK | Si converte nello spazio colore CMYK. |
|  | Converti in scala di grigio | Converte lo spazio colore in scala di grigi. |

#### Impostare le opzioni di caricamento di eVideo {#setting-evideo-upload-options}

Puoi transcodificare un file video scegliendo tra diversi predefiniti video.

| Opzione | Opzione secondaria | Descrizione |
|---|---|---|
| Video adattivo |  | Un singolo predefinito di codifica che funziona con qualsiasi proporzione per creare video da distribuire a dispositivi mobili, tablet e desktop. I video sorgente caricati codificati con questo predefinito sono impostati con un’altezza fissa. Tuttavia, la larghezza viene ridimensionata automaticamente per mantenere le proporzioni del video. <br>Si consiglia di utilizzare la codifica video adattiva. |
| Predefiniti di codifica singoli | Ordina predefiniti di codifica | Selezionare Nome o Dimensione per ordinare i predefiniti di codifica elencati in Desktop, Mobile e Tablet in base al nome o alla dimensione della risoluzione. |
|  | Desktop | Crea un file MP4 per fornire un&#39;esperienza video in streaming o progressiva ai computer desktop.Seleziona una o più proporzioni con la dimensione di risoluzione e la velocità dati target desiderati. |
|  | Mobile | Crea un file MP4 per la distribuzione su dispositivi mobili iPhone o Android.Seleziona una o più proporzioni con la dimensione di risoluzione e la velocità dati target desiderati. |
|  | Tablet | Crea un file MP4 per la consegna su dispositivi tablet iPad o Android. Seleziona una o più proporzioni con la dimensione di risoluzione e la velocità dati target desiderati. |

#### Imposta predefiniti set di batch al caricamento {#setting-batch-set-presets-at-upload}

Per creare automaticamente un set di immagini o un set 360 gradi dalle immagini caricate, fai clic sul pulsante **[!UICONTROL Attivo]** per il predefinito da utilizzare. Puoi selezionare più di un predefinito.

Vedi [Configurazione dei predefiniti per set di batch per generare automaticamente set di immagini e set 360 gradi](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) per ulteriori informazioni sulla creazione di predefiniti per set di batch.

### Caricamenti in streaming {#streamed-uploads}

Se carichi numerose risorse, le chiamate di I/O al [!DNL Experience Manager] il server aumenta drasticamente, riducendo l&#39;efficienza di caricamento e causando anche un timeout. [!DNL Experience Manager] Le risorse supportano il caricamento in streaming delle risorse. Il caricamento in streaming riduce l’I/O del disco durante l’operazione di caricamento, evitando l’archiviazione delle risorse in una cartella temporanea sul server prima di copiarlo nell’archivio. Al contrario, i dati vengono trasferiti direttamente nell’archivio. In questo modo, il tempo necessario per caricare risorse di grandi dimensioni e la possibilità di timeout viene ridotto. Il caricamento in streaming è abilitato per impostazione predefinita in [!DNL Experience Manager] Risorse.

Il caricamento in streaming è disattivato per [!DNL Experience Manager] su server JEE con versione servlet-api inferiore a 3.1.

### Estrai archivio ZIP contenente risorse {#extract-zip-archive-containing-assets}

Puoi caricare gli archivi ZIP come qualsiasi altra risorsa supportata. Le stesse regole del nome file si applicano ai file ZIP. [!DNL Experience Manager] consente di estrarre un archivio ZIP in una posizione DAM.

Seleziona un archivio ZIP alla volta, fai clic su **[!UICONTROL Extract Archive]**, quindi seleziona una cartella di destinazione. Selezionare un&#39;opzione per gestire eventuali conflitti. Se le risorse nel file ZIP esistono già nella cartella di destinazione, puoi selezionare una delle seguenti opzioni: salta l’estrazione, sostituisci i file esistenti, mantieni entrambe le risorse rinominando o crea una nuova versione.

Al termine dell’estrazione, [!DNL Experience Manager] notifica nell’area di notifica. Quando [!DNL Experience Manager] estrae il file ZIP, puoi tornare al tuo lavoro senza interrompere l’estrazione.

![Notifica dell’estrazione ZIP](assets/zip_extract_notification.png)

Alcune limitazioni della funzione sono:

* Se nella destinazione esiste una cartella con lo stesso nome, le risorse del file ZIP vengono estratte nella cartella esistente.

* Se annulli l’estrazione, le risorse già estratte non vengono eliminate.

* Non è possibile selezionare due file ZIP contemporaneamente ed estrarli. Puoi estrarre un solo archivio ZIP alla volta.

## Visualizzare l’anteprima delle risorse {#previewing-assets}

**Per visualizzare in anteprima le risorse**:

1. Dall’interfaccia utente Assets, passa alla posizione della risorsa da visualizzare in anteprima.
1. Tocca la risorsa desiderata per aprirla.

1. Nella modalità di anteprima sono disponibili le opzioni di zoom per [Tipi di immagini supportati](assets-formats.md#supported-raster-image-formats) (con modifica interattiva).

   Per ingrandire una risorsa, tocca **[!UICONTROL +]** (oppure tocca la lente di ingrandimento sulla risorsa). Per ridurre lo zoom, tocca **[!UICONTROL -]**. Quando ingrandisci, puoi osservare da vicino qualsiasi area dell&#39;immagine tramite panoramica. La **[!UICONTROL Ripristina zoom]** freccia consente di tornare alla visualizzazione originale.

   ![uploadicon](assets/uploadicon.png)

   Tocca **[!UICONTROL Reimposta]** per ripristinare le dimensioni originali della visualizzazione.

   ![chlimage_1-11](assets/chlimage_1-11.png)

>[!MORELIKETHIS]
>
>* [Anteprima risorse Dynamic Media](/help/assets/previewing-assets.md).
>* [Visualizzare le risorse secondarie](managing-linked-subassets.md#viewing-subassets).


## Modifica delle proprietà {#editing-properties}

1. Andate alla posizione della risorsa di cui desiderate modificare i metadati.

1. Seleziona la risorsa e tocca **[!UICONTROL Proprietà]** dalla barra degli strumenti per visualizzare le proprietà della risorsa. In alternativa, scegli la **[!UICONTROL Proprietà]** azione rapida sulla scheda delle risorse.

   ![properties_quickaction](assets/properties_quickaction.png)

1. In **[!UICONTROL Proprietà]** , modifica le proprietà dei metadati in varie schede. Ad esempio, sotto il **[!UICONTROL Base]** , modifica il titolo, la descrizione e così via.

   Il layout del **[!UICONTROL Proprietà]** le proprietà di pagina e metadati disponibili dipendono dallo schema di metadati sottostante. Per scoprire come modificare il layout del **[!UICONTROL Proprietà]** pagina, vedi [Schemi metadati](metadata-schemas.md).

1. Per pianificare una data/ora specifica per l’attivazione della risorsa, utilizza il selettore data posto accanto al campo **[!UICONTROL On Time (All’ora)]**.

   ![Imposta l&#39;ora di attivazione delle risorse per rendere le risorse disponibili per un periodo di tempo fisso tra l&#39;ora di attivazione e quella di disattivazione](assets/chlimage_1-12.png)

1. Per disattivare la risorsa dopo una determinata durata, scegli la data e l’ora di disattivazione dal selettore data accanto al **[!UICONTROL Ora di disattivazione]** campo .

   La data di disattivazione deve essere successiva alla data di attivazione di una risorsa. Dopo la [!UICONTROL Ora di disattivazione], una risorsa e le relative rappresentazioni non sono disponibili né tramite l’interfaccia web Assets né tramite l’API HTTP.

   ![Disattivare il tempo necessario affinché le risorse interrompano la disponibilità dopo un certo periodo di tempo](assets/chlimage_1-13.png)

1. In **[!UICONTROL Tag]** selezionare uno o più tag. Per aggiungere un tag personalizzato, digita il nome del tag nella casella e premi **[!UICONTROL Invio]**. Il nuovo tag viene salvato in AEM.

   YouTube richiede tag per pubblicare e dispone di un collegamento ad YouTube (se è possibile trovare un collegamento adatto).
Per creare i tag è necessario disporre di un&#39;autorizzazione di scrittura per `/content/cq:tags/default` nell’archivio CRX.

1. Per assegnare una valutazione alla risorsa, tocca il **[!UICONTROL Avanzate]** quindi tocca la stella nella posizione appropriata per assegnare la valutazione desiderata.

   ![valutazioni](assets/ratings.png)

   Il punteggio di valutazione assegnato alla risorsa viene visualizzato in **[!UICONTROL Valutazioni]**. Il punteggio medio di valutazione della risorsa ricevuto dagli utenti che hanno valutato la risorsa viene visualizzato in **[!UICONTROL Valutazione]**. Inoltre, viene visualizzata la suddivisione dei punteggi di rating che contribuiscono al punteggio medio in **[!UICONTROL Suddivisione dei rating]**. Puoi cercare le risorse in base ai punteggi di valutazione medi.

1. Per visualizzare le statistiche di utilizzo della risorsa, tocca **[!UICONTROL Informazioni approfondite]** scheda .

   Le statistiche di utilizzo includono:

   * Numero di volte in cui la risorsa è stata visualizzata o scaricata.
   * Canali/dispositivi attraverso i quali è stata utilizzata la risorsa.
   * Soluzioni creative in cui la risorsa è stata recentemente utilizzata.

   Per ulteriori dettagli, consulta [Informazioni sulle risorse](touch-ui-asset-insights.md).

1. Tocca **[!UICONTROL Salva e chiudi]**.
1. Passa all’interfaccia utente Assets. Le proprietà dei metadati modificati, quali titolo, descrizione, valutazioni e così via, vengono visualizzate sulla scheda delle risorse nella vista a schede e nelle relative colonne nella vista a elenco.

## Copiare le risorse {#copying-assets}

Quando copi una risorsa o una cartella, viene copiata l’intera risorsa o la cartella insieme alla relativa struttura del contenuto. Una risorsa o una cartella copiata viene duplicata nel percorso di destinazione. La risorsa nella posizione di origine non viene modificata.

Alcuni attributi univoci per una particolare copia di una risorsa non vengono riportati in avanti. Alcuni esempi sono:

* ID risorsa, data e ora di creazione, versioni e cronologia delle versioni. Alcune di queste proprietà sono indicate dalle proprietà `jcr:uuid`, `jcr:created`e `cq:name`.

* L’ora di creazione e i percorsi di riferimento sono univoci per ogni risorsa e per ogni suo rendering.

Le altre proprietà e informazioni sui metadati vengono mantenute. Non viene creata una copia parziale durante la copia di una risorsa.

1. Dall’interfaccia utente Assets, seleziona una o più risorse, quindi tocca il **[!UICONTROL Copia]** dalla barra degli strumenti. In alternativa, scegli la **[!UICONTROL Copia]** azione rapida dalla scheda delle risorse.

   ![copy_icon](assets/copy_icon.png)

   >[!NOTE]
   >
   >Se utilizzi **[!UICONTROL Copia]** azione rapida, puoi copiare una sola risorsa alla volta.

1. Andate alla posizione in cui desiderate copiare le risorse.

   >[!NOTE]
   >
   >Se copi una risorsa nella stessa posizione, [!DNL Experience Manager] genera automaticamente una variante del nome. Ad esempio, se copi una risorsa denominata Quadrato, [!DNL Experience Manager] genera automaticamente il titolo della copia come quadrato1.

1. Tocca **[!UICONTROL Incolla]** icona della risorsa dalla barra degli strumenti:

   ![chlimage_1-14](assets/chlimage_1-14.png)

   Le risorse vengono copiate in questa posizione.

   >[!NOTE]
   >
   >La **[!UICONTROL Incolla]** l’icona è disponibile nella barra degli strumenti fino al completamento dell’operazione Incolla .

## Spostare e rinominare le risorse {#moving-or-renaming-assets}

Quando sposti le risorse (o le cartelle) in un altro percorso, le risorse (o le cartelle) non vengono duplicate come durante la copia della risorsa. Le risorse (o le cartelle) vengono posizionate nel percorso di destinazione e rimosse dal percorso di origine. È inoltre possibile rinominare la risorsa quando la si sposta nella nuova posizione. Se sposti una risorsa pubblicata in un percorso diverso, puoi ripubblicare la risorsa. Per impostazione predefinita, l’operazione di spostamento su una risorsa pubblicata la annulla automaticamente. La risorsa spostata viene ripubblicata se l’autore seleziona la [!UICONTROL Ripubblica] quando si sposta la risorsa.

![Quando la si sposta, è possibile ripubblicare una risorsa già pubblicata](assets/republish-on-move.png)

Per spostare risorse o cartelle:

1. Andate alla posizione della risorsa da spostare.

![Quando la si sposta, è possibile ripubblicare una risorsa già pubblicata](assets/republish-on-move.png)

Per spostare risorse o cartelle:

1. Andate alla posizione della risorsa da spostare.

1. Seleziona la risorsa e fai clic su **[!UICONTROL Sposta]** dalla barra degli strumenti.
   ![Opzione Sposta nella barra degli strumenti Risorse](assets/do-not-localize/move_icon.png)

1. In [!UICONTROL Sposta risorse] eseguire una delle operazioni seguenti:

   * Specifica il nome della risorsa dopo averlo spostata. Quindi fai clic su **[!UICONTROL Successivo]** per procedere.

   * Fai clic su **[!UICONTROL Annulla]** per interrompere il processo.
   >[!NOTE]
   >
   >* Potete specificare lo stesso nome per la risorsa se nella nuova posizione non è presente alcuna risorsa con tale nome. Tuttavia, se sposti la risorsa in una posizione in cui esiste una risorsa con lo stesso nome, utilizza un nome diverso. Se utilizzi lo stesso nome, il sistema genera automaticamente una variante del nome. Ad esempio, se la risorsa ha il nome Square, il sistema genera il nome Square1 per la relativa copia.
   >* Durante la ridenominazione, lo spazio vuoto non è consentito nel nome del file.


1. Sulla **[!UICONTROL Seleziona destinazione]** eseguire una delle operazioni seguenti:

   * Passa alla nuova posizione delle risorse, quindi fai clic su **[!UICONTROL Successivo]** per procedere.

   * Fai clic su **[!UICONTROL Indietro]** per tornare al **[!UICONTROL Rinomina]** schermo.

1. Se le risorse che stai spostando dispongono di pagine, risorse o raccolte di riferimento, la **[!UICONTROL Regolare i riferimenti]** accanto alla scheda **[!UICONTROL Seleziona destinazione]** scheda .

   Effettua una delle seguenti operazioni nel **[!UICONTROL Regolare i riferimenti]** schermo:

   * Specificare i riferimenti da modificare in base ai nuovi dettagli, quindi fare clic su **[!UICONTROL Sposta]** per procedere.

   * Da **[!UICONTROL Regola]** , seleziona o deseleziona i riferimenti alle risorse.
   * Fai clic su **[!UICONTROL Indietro]** per tornare al **[!UICONTROL Seleziona destinazione]** schermo.

   * Fai clic su **[!UICONTROL Annulla]** per interrompere l&#39;operazione di spostamento.

   Se non aggiorni i riferimenti, continuano a indicare il percorso precedente della risorsa. Se regoli i riferimenti, vengono aggiornati al nuovo percorso della risorsa.

### Spostare le risorse tramite trascinamento {#move-using-drag}

È possibile spostare le risorse (o le cartelle) in una cartella di pari livello trascinandole nella posizione di destinazione, anziché utilizzare [!UICONTROL Sposta] nell’interfaccia utente di . Tuttavia, questa operazione è possibile solo nella vista a elenco.

Lo spostamento delle risorse trascinandole non si apre [!UICONTROL Sposta risorsa] non è quindi possibile rinominare le risorse durante lo spostamento. Inoltre, le risorse già pubblicate vengono ripubblicate trascinandole per spostarle, senza richiedere l&#39;approvazione dell&#39;utente per ripubblicare.

![Spostare le risorse in cartelle di pari livello trascinandole](assets/move-by-drag.gif)

## Gestire le rappresentazioni {#managing-renditions}

1. Puoi aggiungere o rimuovere rappresentazioni per una risorsa, tranne l’originale. Passa alla posizione della risorsa per la quale desideri aggiungere o rimuovere rappresentazioni.

1. Toccate la risorsa per aprire la relativa pagina di risorse.

   ![chlimage_1-15](assets/chlimage_1-15.png)

1. Tocca **[!UICONTROL Navigazione globale]** e seleziona **[!UICONTROL Rendering]** dall&#39;elenco.

   ![renditions_menu](assets/renditions_menu.png)

1. In **[!UICONTROL Rendering]** Visualizza l’elenco delle rappresentazioni generate per la risorsa.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, [!DNL Experience Manager] Il rendering originale della risorsa non viene visualizzato in modalità anteprima. Gli amministratori possono utilizzare le sovrapposizioni per configurare [!DNL Experience Manager] Risorse per visualizzare le rappresentazioni originali in modalità anteprima.

1. Selezionare un rendering per visualizzare o eliminare il rendering.

   **Eliminare un rendering**

   Selezionare un rendering dal **[!UICONTROL Rendering]** , quindi tocca **[!UICONTROL Elimina rappresentazione]** dall&#39;icona [barra degli strumenti](/help/sites-authoring/basic-handling.md). Le rappresentazioni non possono essere eliminate in blocco al termine dell’elaborazione delle risorse. Per le singole risorse, puoi rimuovere manualmente i rendering dall’interfaccia utente. Per più risorse, puoi personalizzare l’Experience Manager per eliminare rappresentazioni specifiche o eliminare le risorse e ricaricare le risorse eliminate.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **Caricare un nuovo rendering**

   Passa alla pagina dei dettagli della risorsa e tocca il **[!UICONTROL Aggiungi rappresentazione]** nella barra degli strumenti per caricare una nuova rappresentazione della risorsa.

   ![chlimage_1-16](assets/chlimage_1-16.png)

   >[!NOTE]
   >
   >Se selezioni un rendering dal pannello **[!UICONTROL Rendering]**, la barra degli strumenti cambia contesto, visualizzando solo le azioni del rendering specifico. Opzioni, ad esempio **[!UICONTROL Carica rappresentazione]** non viene visualizzata. Per visualizzare queste opzioni nella barra degli strumenti, vai alla pagina dei dettagli della risorsa.

   Puoi configurare le dimensioni per il rendering da visualizzare nella pagina dei dettagli di un’immagine o di una risorsa video. In base alle dimensioni specificate, [!DNL Experience Manager] Assets visualizza il rendering con le dimensioni esatte o più vicine.

   Per configurare le dimensioni di rendering di un’immagine a livello di dettaglio della risorsa, sovrapponi **[!UICONTROL renditionpicker]** nodo `libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker` e configura il valore della proprietà width.  Per personalizzare il rendering sulla pagina dei dettagli della risorsa in base alle dimensioni dell’immagine, configura la proprietà **[!UICONTROL size (Long) in KB (dimensione (lunga) in KB)]** al posto della larghezza. Per la personalizzazione basata sulle dimensioni, la proprietà **[!UICONTROL PreferisciOriginale]** assegna le preferenze all&#39;originale se la dimensione del rendering corrispondente è maggiore dell&#39;originale.

   Allo stesso modo, puoi personalizzare la **[!UICONTROL Annotazione]** immagine della pagina sovrapposta `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`.

   ![chlimage_1-17](assets/chlimage_1-17.png)

   Per configurare le dimensioni di rendering per una risorsa video, passa alla **[!UICONTROL videopicker]** nodo nell&#39;archivio CRX nella posizione `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`, sovrapponi il nodo e quindi modifica la proprietà appropriata.

   >[!NOTE]
   >
   >Le annotazioni video sono supportate solo sui browser con formati video compatibili con HTML5. Inoltre, a seconda del browser, sono supportati diversi formati video.

Per informazioni sulle risorse secondarie, consulta [gestire le risorse secondarie](managing-linked-subassets.md).

## Eliminare le risorse {#deleting-assets}

Per risolvere o rimuovere i riferimenti in entrata da altre pagine, aggiorna i riferimenti rilevanti prima di eliminare una risorsa.

Inoltre, disattiva il pulsante force delete utilizzando una sovrapposizione, per impedire agli utenti di eliminare le risorse di riferimento e di lasciare i collegamenti interrotti.

Per poter eliminare una risorsa è necessario disporre delle autorizzazioni di eliminazione per dam/asset. Se disponi solo di autorizzazioni di modifica, puoi modificare solo i metadati della risorsa e aggiungere annotazioni alla risorsa. Tuttavia, non puoi eliminare la risorsa o i relativi metadati.

**Per eliminare le risorse**:

1. Andate alla posizione delle risorse da eliminare.

1. Seleziona la risorsa e tocca il **[!UICONTROL Elimina]** dalla barra degli strumenti.

   ![delete_icon](assets/delete_icon.png)

1. Nella finestra di dialogo di conferma, tocca:

   * **[!UICONTROL Annulla]** per interrompere l&#39;azione
   * **[!UICONTROL Elimina]** per confermare l’azione in base ai seguenti elementi:

      * Se la risorsa non ha riferimenti, viene eliminata.
      * Se la risorsa dispone di riferimenti, un messaggio di errore segnala che **[!UICONTROL Riferimento a una o più risorse]**. Potete selezionare **[!UICONTROL Forza eliminazione]** o **[!UICONTROL Annulla]**.

   >[!NOTE]
   >
   >Per risolvere o rimuovere i riferimenti in entrata da altre pagine, aggiorna i riferimenti rilevanti prima di eliminare una risorsa.
   >
   >Inoltre, disattiva la **[!UICONTROL Forza eliminazione]** utilizzando una sovrapposizione, per impedire agli utenti di eliminare le risorse di riferimento e di lasciare i collegamenti interrotti.

## Scaricare le risorse {#downloading-assets}

Vedi [Scaricare risorse da AEM](download-assets-from-aem.md)

## Pubblicare e annullare la pubblicazione delle risorse {#publish-assets}

Dopo aver caricato, elaborato o modificato le risorse su [!DNL Experience Manager] autore, pubblichi la risorsa sul server di pubblicazione. La pubblicazione rende la risorsa disponibile pubblicamente. L’annullamento della pubblicazione ha rimosso la risorsa dal server di pubblicazione ma non dal server di authoring.

Per informazioni specifiche su [!DNL Dynamic Media], vedi [pubblicazione [!DNL Dynamic Media] assets](publishing-dynamicmedia-assets.md).

1. Passa alla posizione della risorsa o della cartella di risorse che desideri pubblicare o che desideri rimuovere dall’ambiente di pubblicazione (Annulla pubblicazione).

1. Seleziona la risorsa o la cartella da annullare la pubblicazione e fai clic su **[!UICONTROL Gestisci pubblicazione]** ![opzione gestione pubblicazione](assets/do-not-localize/globe-publication.png) dalla barra degli strumenti. In alternativa, per pubblicare rapidamente, seleziona la **[!UICONTROL Pubblicazione rapida]** dalla barra degli strumenti. Se la cartella da pubblicare include una cartella vuota, questa non verrà pubblicata.

1. Seleziona la **[!UICONTROL Pubblica]** o **[!UICONTROL Annulla pubblicazione]** se necessario.

   ![Annulla pubblicazione azione](assets/unpublish_action.png)
   *Figura: Opzioni di pubblicazione e annullamento della pubblicazione e opzione di pianificazione.*

1. Seleziona **[!UICONTROL Ora]** per agire immediatamente sulla risorsa o seleziona **[!UICONTROL Più tardi]** per pianificare l’azione. Seleziona una data e un’ora se scegli la **[!UICONTROL Più tardi]** opzione . Fai clic su **[!UICONTROL Avanti]**.

1. Durante la pubblicazione, se una risorsa fa riferimento ad altre risorse, i relativi riferimenti sono elencati nella procedura guidata. Vengono visualizzati solo i riferimenti, che vengono annullati o modificati dall’ultima pubblicazione. Scegli i riferimenti da pubblicare.

1. Quando si annulla la pubblicazione, se una risorsa fa riferimento ad altre risorse, scegliete i riferimenti di cui desiderate annullare la pubblicazione. Fai clic su **[!UICONTROL Annulla pubblicazione]**. Nella finestra di dialogo di conferma, fai clic su **[!UICONTROL Annulla]** per interrompere l’azione o fare clic su **[!UICONTROL Annulla pubblicazione]** per confermare l’annullamento della pubblicazione delle risorse alla data specificata.

Scopri i seguenti limiti e suggerimenti relativi alla pubblicazione o all’annullamento della pubblicazione di risorse o cartelle:

* L’opzione [!UICONTROL Gestisci pubblicazione] è disponibile solo per gli account utente che dispongono di autorizzazioni di replica.
* Quando si annulla la pubblicazione di una risorsa complessa, è necessario annullare solo la pubblicazione della risorsa. Evita di annullare la pubblicazione dei riferimenti, poiché altri contenuti pubblicati potrebbero farvi riferimento.
* Le cartelle vuote non vengono pubblicate.
* Se pubblichi una risorsa in fase di elaborazione, viene pubblicato solo il contenuto originale. Mancano i rendering. Attendi il completamento dell’elaborazione, quindi pubblica o ripubblica la risorsa al termine dell’elaborazione.

## Creare un gruppo utenti chiuso {#closed-user-group}

Un gruppo utenti chiuso viene utilizzato per limitare l’accesso a specifiche cartelle di risorse pubblicate da AEM. Se si crea un CUG per una cartella, l’accesso alla cartella (incluse le risorse della cartella e le sottocartelle) è limitato solo ai membri o ai gruppi assegnati. Per accedere alla cartella, è necessario che accedano utilizzando le proprie credenziali di sicurezza.

I CUG sono un modo aggiuntivo per limitare l’accesso alle risorse. Puoi anche configurare una pagina di accesso per la cartella.

**Per creare un gruppo utenti chiuso**:

1. Seleziona una cartella dall’interfaccia utente Assets, quindi tocca **[!UICONTROL Proprietà]** dalla barra degli strumenti per visualizzare la pagina delle proprietà.
1. Da **[!UICONTROL Autorizzazioni]** scheda aggiungi membri o gruppi in **[!UICONTROL Gruppo utenti chiuso]**.

   ![add_user](assets/add_user.png)

1. Per visualizzare una schermata di accesso quando gli utenti accedono alla cartella, seleziona la **[!UICONTROL Abilita]** opzione . Quindi, seleziona il percorso di una pagina di accesso in AEM e salva le modifiche.

   ![login_page](assets/login_page.png)

   Se non si specifica il percorso di una pagina di accesso, [!DNL Experience Manager] visualizza la pagina di accesso predefinita nell’istanza di pubblicazione.

1. Pubblica la cartella e prova ad accedervi dall&#39;istanza di pubblicazione. Viene visualizzata una schermata di accesso.
1. Se sei un membro CUG, immetti le tue credenziali di sicurezza. La cartella viene visualizzata dopo [!DNL Experience Manager] ti autentica.

## Cercare risorse {#searching-assets}

La ricerca di base è descritta in [Ricerca e filtro](/help/sites-authoring/search.md#search-and-filter) sezione . Utilizza la **[!UICONTROL Ricerca]** per cercare risorse, tag e metadati. È possibile cercare parti di una stringa utilizzando l&#39;asterisco con carattere jolly. Inoltre, puoi personalizzare la **[!UICONTROL Ricerca]** pannello che utilizza [Facet di ricerca](search-facets.md).

![filters_panel](assets/filters_panel.png)

Per le risorse caricate di recente, i relativi metadati (inclusi titoli, tag e così via) non sono immediatamente disponibili nell’elenco dei suggerimenti che vengono visualizzati quando digiti nella casella di ricerca Omnisearch.

Questo perché [!DNL Experience Manager] Le risorse attendono la scadenza di un periodo di timeout (1 ora per impostazione predefinita) prima di eseguire un processo in background per indicizzare i metadati per tutte le risorse appena caricate/aggiornate e aggiungerle all’elenco dei suggerimenti.

## Usa azioni rapide {#quick-actions}

Le icone delle azioni rapide sono disponibili per una singola risorsa alla volta. A seconda del dispositivo, esegui le seguenti azioni per visualizzare le icone delle azioni rapide:

* Dispositivi touch: Toccare e tenere premuto. Ad esempio, in un iPad, puoi toccare e tenere premuto una risorsa per visualizzare le azioni rapide.
* Dispositivi non touch: Puntatore al passaggio del mouse. Ad esempio, su un dispositivo desktop, se passi il puntatore sulla miniatura della risorsa viene visualizzata la barra delle azioni rapide.

### Passa alle risorse e selezionale {#navigating-and-selecting-assets}

Puoi visualizzare, navigare e selezionare le risorse tramite una qualsiasi delle viste disponibili (scheda, colonna, elenco) utilizzando **[!UICONTROL Seleziona]** icona. **[!UICONTROL Seleziona]** viene visualizzata come un’azione rapida nella vista a schede.

![select_quick_action](assets/select_quick_action.png)

Nella vista a elenco, **[!UICONTROL Seleziona]** appare quando passi il cursore del mouse sulla miniatura prima dei nomi delle risorse o della cartella nell’elenco.

![select_quick_in_listview](assets/select_quick_in_listview.png)

Simile alla vista a elenco, **[!UICONTROL Seleziona]** quando passi il cursore sull’icona del mouse sulla miniatura prima dei nomi delle risorse o della cartella nella vista a colonne.

![select_quick_in_columnview](assets/select_quick_in_columnview.png)

Per ulteriori informazioni, consulta [Visualizzazione e selezione delle risorse](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).

## Modificare le immagini {#editing-images}

Gli strumenti di modifica [!DNL Experience Manager] L’interfaccia di Assets consente di eseguire piccoli lavori di modifica sulle risorse di immagini. È possibile ritagliare, ruotare, capovolgere ed eseguire altri lavori di modifica sulle immagini. Puoi anche aggiungere mappe immagine alle risorse.

La modifica delle immagini è supportata per i file con i seguenti formati:

* BMP
* GIF
* PNG
* JPEG

Per alcuni componenti, **[!UICONTROL Schermo intero]** dispone di opzioni aggiuntive.

Per modificare un file TXT, imposta **[!UICONTROL Day CQ Link Externalizer]** da Configuration Manager.

Puoi anche aggiungere mappe immagine utilizzando l’editor di immagini. Per maggiori dettagli, vedi [Aggiunta di mappe immagine](image-maps.md).

**Per modificare le immagini**:

1. Effettua una delle seguenti operazioni per aprire una risorsa in modalità di modifica:

   * Seleziona la risorsa e fai clic sul pulsante **[!UICONTROL Modifica]** nella barra degli strumenti.
   * Tocca **[!UICONTROL Modifica]** che viene visualizzata su una risorsa nella vista a schede.
   * Nella pagina della risorsa, tocca **[!UICONTROL Modifica]** nella barra degli strumenti.

   ![edit_icon](assets/edit_icon.png)

1. Per ritagliare l’immagine, tocca **[!UICONTROL Ritaglio]**.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Seleziona l’opzione desiderata dall’elenco. L’area di ritaglio viene visualizzata sull’immagine in base all’opzione scelta. L’opzione **[!UICONTROL Mano libera]** consente di ritagliare l’immagine senza limitazioni di proporzioni.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. Selezionate l&#39;area da ritagliare e ridimensionatela o riposizionatela sull&#39;immagine.
1. Utilizza la **[!UICONTROL Fine]** nell’angolo in alto a destra per ritagliare l’immagine. Tocca **[!UICONTROL Fine]** attiva anche la rigenerazione dei rendering.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Utilizza la **[!UICONTROL Annulla]** e **[!UICONTROL Ripeti]** in alto a destra per ripristinare l’immagine non ritagliata o mantenere l’immagine ritagliata, rispettivamente.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Toccare il pulsante appropriato **[!UICONTROL Ruota]** per ruotare l&#39;immagine in senso orario o antiorario.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Toccare il pulsante appropriato **[!UICONTROL Capovolgimento]** per capovolgere l’immagine in orizzontale o verticale.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Tocca **[!UICONTROL Fine]** per salvare le modifiche.

   ![chlimage_1-28](assets/chlimage_1-28.png)

## Utilizza la timeline {#timeline}

La **[!UICONTROL Timeline]** consente di visualizzare vari eventi per un elemento selezionato, ad esempio flussi di lavoro attivi per una risorsa, commenti, annotazioni, registri attività e versioni.

In [Console Raccolte](managing-collections-touch-ui.md#navigating-the-collections-console), **[!UICONTROL Mostra tutto]** fornisce opzioni per visualizzare solo i commenti e i flussi di lavoro. Inoltre, la timeline viene visualizzata solo per le raccolte di primo livello elencate nella console. Non viene visualizzato se vi spostate all’interno di una qualsiasi delle raccolte.

**[!UICONTROL Timeline]** contiene diversi [opzioni specifiche per i frammenti di contenuto](content-fragments-managing.md#timeline-for-content-fragments); questa funzionalità richiede [[!DNL Experience Manager] 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) o successiva.

**Per utilizzare la timeline**:

1. Apri la pagina della risorsa o selezionala nell’interfaccia utente Assets.
1. Tocca **[!UICONTROL Navigazione globale]** e scegli **[Timeline]** dall&#39;elenco.

   ![timeline](assets/timeline.png)

1. Nell’elenco visualizzato, utilizza **[!UICONTROL Mostra tutto]** elenco per filtrare i risultati in base a commenti, versioni, flussi di lavoro e attività.

   ![timeline_options](assets/timeline_options.png)

## Aggiungi annotazioni {#annotating}

Le annotazioni sono commenti o note esplicative aggiunte a immagini o video. Le annotazioni consentono agli addetti al marketing di collaborare e lasciare un feedback sulle risorse.

Le annotazioni video sono supportate solo sui browser con formati video compatibili con HTML5. Formati video [!DNL Experience Manager] Il supporto delle risorse dipende dal browser.

Per i frammenti di contenuto, [le annotazioni vengono create nell’editor](content-fragments-variations.md#annotating-a-content-fragment); questa funzionalità richiede [[!DNL Experience Manager] 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) o successiva.

È possibile aggiungere più annotazioni prima di salvarle.

Puoi aggiungere annotazioni alle risorse video. Durante l&#39;annotazione dei video, il lettore si mette in pausa per consentirvi di annotare un fotogramma. Per maggiori dettagli, vedi [gestione delle risorse video](managing-video-assets.md).

È inoltre possibile aggiungere annotazioni a una raccolta. Tuttavia, se una raccolta contiene raccolte secondarie, è possibile aggiungere solo annotazioni o commenti alla raccolta principale. La **[!UICONTROL Annota]** l’opzione non è disponibile per le raccolte figlio.

**Aggiunta di annotazioni**:

1. Andate alla posizione della risorsa alla quale desiderate aggiungere annotazioni.
1. Tocca **[!UICONTROL Annota]** da una delle seguenti icone:

   * [Azioni rapide](managing-assets-touch-ui.md#quick-actions)
   * Dalla barra degli strumenti dopo aver selezionato la risorsa o essere passato alla pagina della risorsa

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Aggiungi un commento nella casella **[!UICONTROL Commento]** posta nella parte inferiore della timeline. In alternativa, contrassegna un’area sull’immagine e aggiungi un’annotazione nel **[!UICONTROL Aggiungi annotazione]** finestra di dialogo.

   ![chlimage_1-30](assets/chlimage_1-30.png)

1. Per inviare un’annotazione a un utente, specifica l’indirizzo e-mail dell’utente e aggiungi il commento. Ad esempio, per notificare ad Aaron McDonald un&#39;annotazione, immetti @aa. I suggerimenti per tutti gli utenti corrispondenti vengono visualizzati in un elenco. Seleziona l’indirizzo e-mail di Aaron dall’elenco per contrassegnarlo con il commento. Allo stesso modo, è possibile assegnare tag a più utenti in qualsiasi punto dell’annotazione, prima o dopo.

   >[!NOTE]
   >
   >Per un utente non amministratore, i suggerimenti vengono visualizzati solo se l’utente dispone delle autorizzazioni di lettura in `/home` in CRXDE.

   ![chlimage_1-31](assets/chlimage_1-31.png)

1. Dopo aver aggiunto l’annotazione, tocca **[!UICONTROL Aggiungi]** per salvarlo. Ad Aaron viene inviata una notifica relativa all’annotazione.

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Tocca **[!UICONTROL Chiudi]** per uscire **[!UICONTROL Annotazione]** modalità.
1. Per visualizzare la notifica, accedi a [!DNL Experience Manager] Risorse con le credenziali di Aaron MacDonald e toccare **[!UICONTROL Notifiche]** per visualizzare la notifica.

1. Per scegliere un colore diverso in modo da poter differenziare gli utenti, tocca **[!UICONTROL Profilo]** icona e tocco **[!UICONTROL Preferenze]**.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Specifica il colore desiderato nella **[!UICONTROL Colore annotazione]** casella, quindi toccare **[!UICONTROL Accetta]**.

   ![chlimage_1-34](assets/chlimage_1-34.png)

### Visualizzare le annotazioni salvate {#viewing-saved-annotations}

È possibile visualizzare una sola annotazione alla volta.

>[!NOTE]
>
>Se selezioni più annotazioni, l’ultima sarà visibile nell’interfaccia utente.
>
>La selezione multipla è supportata solo per la stampa della risorsa annotata come PDF.

1. Per visualizzare le annotazioni salvate per una risorsa, accedi alla posizione della risorsa e apri la pagina della risorsa.

1. Tocca **[!UICONTROL Navigazione globale]** e tocca **[!UICONTROL Timeline]** dall&#39;elenco.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Dall’elenco **[!UICONTROL Mostra tutti]** nella timeline, seleziona **[!UICONTROL Commenti]** per filtrare i risultati in base alle annotazioni.

   ![chlimage_1-36](assets/chlimage_1-36.png)

1. Toccare un commento nella **[!UICONTROL Timeline]** per visualizzare l’annotazione corrispondente sull’immagine.

   ![chlimage_1-37](assets/chlimage_1-37.png)

1. Tocca **[!UICONTROL Elimina]** per rimuovere un commento specifico.

### Stampa annotazioni {#printing-annotations}

Se una risorsa dispone di annotazioni o è stata sottoposta a un flusso di lavoro di revisione, puoi stampare la risorsa insieme a annotazioni e rivederne lo stato come file PDF per la revisione offline.

È inoltre possibile scegliere di stampare solo le annotazioni o lo stato di revisione.

>[!NOTE]
>
>È possibile selezionare più annotazioni durante la stampa della risorsa annotata come PDF.

Il rendering delle annotazioni lunghe potrebbe non essere corretto nel file PDF. Per un rendering ottimale, l’Adobe consiglia di limitare le annotazioni a 50 parole.

Per stampare le annotazioni e controllare lo stato, tocca **[!UICONTROL Stampa]** e segui le istruzioni della procedura guidata. La **[!UICONTROL Stampa]** l’icona viene visualizzata nella barra degli strumenti solo quando alla risorsa è assegnata almeno un’annotazione o uno stato di revisione.

1. Dall’interfaccia utente Assets, apri la pagina di anteprima per una risorsa.
1. Effettua una delle operazioni seguenti:

   * Per stampare tutte le annotazioni e lo stato di revisione, andare al passaggio 4.
   * Per stampare annotazioni specifiche e controllare lo stato, aprire [Timeline](managing-assets-touch-ui.md#timeline) quindi procedere al punto 3.

1. Per stampare annotazioni specifiche, selezionate le annotazioni nella sezione **[!UICONTROL Timeline]**.

   ![chlimage_1-38](assets/chlimage_1-38.png)

   Per stampare solo lo stato di revisione, selezionarlo dalla **[!UICONTROL Timeline]**.

   ![chlimage_1-39](assets/chlimage_1-39.png)

1. Sulla barra degli strumenti, tocca **[!UICONTROL Stampa]** icona.

   ![chlimage_1-40](assets/chlimage_1-40.png)

1. Da **[!UICONTROL Stampa]** scegliere la posizione in cui visualizzare le annotazioni o lo stato di revisione in PDF. Ad esempio, se desideri che le annotazioni o lo stato vengano stampati in alto a destra nella pagina contenente l’immagine stampata, utilizza la **[!UICONTROL In alto a sinistra]** (impostazione predefinita).

   ![chlimage_1-41](assets/chlimage_1-41.png)

   È possibile scegliere altre impostazioni a seconda della posizione in cui si desidera visualizzare le annotazioni o lo stato nel PDF stampato. Se desideri che le annotazioni o lo stato vengano visualizzati in una pagina separata dalla risorsa stampata, scegli **[!UICONTROL Pagina successiva]**.

1. Tocca **[!UICONTROL Stampa]**. A seconda dell’opzione scelta al passaggio 2, PDF generato visualizza le annotazioni o lo stato nella posizione specificata. Ad esempio, se scegli di stampare sia le annotazioni che lo stato di revisione utilizzando l’impostazione **[!UICONTROL In alto a sinistra]**, l’output generato sarà simile al file PDF qui riportato.

   ![chlimage_1-42](assets/chlimage_1-42.png)

1. Scarica o stampa il PDF utilizzando le opzioni in alto a destra.

   ![chlimage_1-43](assets/chlimage_1-43.png)

   >[!NOTE]
   >
   >Se la risorsa dispone di risorse secondarie, puoi stampare tutte le risorse secondarie insieme alle relative annotazioni specifiche a livello di pagina.

   Per modificare l’aspetto del file PDF renderizzato, ad esempio il colore, la dimensione e lo stile del font, il colore di sfondo dei commenti e degli stati, aprire il **[!UICONTROL Configurazione di Annotation PDF]** da **[!UICONTROL Gestione configurazione]** e modifica le opzioni desiderate. Ad esempio, per modificare il colore di visualizzazione dello stato approvato, modificare il codice del colore nel campo corrispondente. Per informazioni sulla modifica del colore del font delle annotazioni, consultare [Annotazione](managing-assets-touch-ui.md#annotating).

   ![chlimage_1-44](assets/chlimage_1-44.png)

   Torna al file PDF renderizzato e aggiornalo. Il PDF aggiornato riflette le modifiche apportate.

**Per stampare annotazioni in lingue straniere**: Se una risorsa include annotazioni in lingue straniere (in particolare lingue non latine), devi prima configurare il servizio di gestione dei font CQ-DAM-Handler-Gibson sul [!DNL Experience Manager] per poter stampare queste annotazioni. Quando si configura CQ-DAM-Handler-Gibson Font Manager Service, fornisci il percorso in cui si trovano i font per le lingue desiderate.

1. Apri **[!UICONTROL Servizio di gestione font CQ-DAM-Handler-Gibson]** pagina di configurazione dall’URL [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl).
1. Per configurare **[!UICONTROL Servizio di gestione font CQ-DAM-Handler-Gibson]**, effettua una delle seguenti operazioni:

   * In **[!UICONTROL Font di sistema]** opzione directory, specifica il percorso completo della directory dei font sul sistema. Ad esempio, se sei un utente di Mac, puoi specificare il percorso come `/Library/Fonts` in **[!UICONTROL Font di sistema]** opzione directory. [!DNL Experience Manager] recupera i font da questa directory.
   * Crea una directory denominata **font** all&#39;interno del **[!UICONTROL crx-quickstart]** cartella. **[!UICONTROL Servizio di gestione font CQ-DAM-Handler-Gibson]** recupera automaticamente i font nella posizione `crx-quickstart/fonts`. È possibile ignorare questo percorso predefinito da **[!UICONTROL Font del server Adobe]** opzione directory.
   * Crea una nuova cartella per i font nel sistema e archivia i font desiderati nella cartella. Quindi, specifica il percorso completo della cartella nella **[!UICONTROL Font cliente]** opzione directory.

1. Accedere al **[!UICONTROL PDF di annotazione]** configurazione dall’URL [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig](http://localhost:4502/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig).
1. Configura le **[!UICONTROL PDF di annotazione]** con il set corretto di font-family come segue:

   * Includi la stringa `<font_family_name_of_custom_font, sans-serif>` all’interno dell’opzione font-family (famiglia di font). Ad esempio, se desideri stampare annotazioni in CJK (cinese, giapponese e coreano), includi la stringa `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` nell’opzione font-family (famiglia di font). Se si desidera stampare le annotazioni in hindi, scaricare il font appropriato e configurare la famiglia di font come Arial Unicode MS, Noto Sans, Noto Sans CJK JP, Noto Sans Devanagari, sans-serif.

1. Riavvia [!DNL Experience Manager] istanza.

Esempio di configurazione [!DNL Experience Manager] per stampare annotazioni in CJK (cinese, giapponese e coreano):

1. Scarica i font Google Noto CJK dai seguenti collegamenti e memorizzali nella directory dei font configurata in Font Manager Service.

   * Carattere All In One Super CJK: [https://www.google.com/get/noto/help/cjk/](https://www.google.com/get/noto/help/cjk/)
   * Noto Sans (per le lingue europee): [https://www.google.com/get/noto/](https://www.google.com/get/noto/)
   * Nessun carattere per una lingua scelta: [https://www.google.com/get/noto/](https://www.google.com/get/noto/)

1. Configura il file PDF di annotazione impostando il parametro font-family su `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif`. Questa configurazione è disponibile per impostazione predefinita e funziona per tutte le lingue europee e CJK.
1. Se la lingua scelta è diversa dalle lingue menzionate al punto 2, aggiungi una voce appropriata (separata da virgole) alla famiglia di font predefinita.

## Creare il controllo delle versioni delle risorse {#asset-versioning}

Il controllo delle versioni crea un’istantanea delle risorse digitali in un momento preciso. Il controllo delle versioni consente di ripristinare le risorse a uno stato precedente in un secondo momento. Ad esempio, per annullare una modifica apportata a una risorsa, ripristina la versione non modificata della risorsa.

Di seguito sono riportati gli scenari in cui si creano versioni:

* Puoi modificare un&#39;immagine in un&#39;altra applicazione e caricarla in [!DNL Experience Manager] Risorse. Viene creata una versione dell’immagine in modo che l’immagine originale non venga sovrascritta.
* Puoi modificare i metadati di una risorsa.
* Utilizzate [!DNL Experience Manager] app desktop per estrarre una risorsa esistente e salvare le modifiche. A ogni salvataggio della risorsa viene creata una nuova versione.

È inoltre possibile abilitare il controllo delle versioni automatico tramite un flusso di lavoro. Quando crei una versione per una risorsa, i metadati e le rappresentazioni vengono salvati insieme alla versione. Le rappresentazioni sono alternative di rendering delle stesse immagini, ad esempio, una rappresentazione PNG di un file JPEG caricato.

La funzionalità di controllo delle versioni consente di effettuare le seguenti operazioni:

* Crea una versione di una risorsa.
* Visualizza la revisione corrente per una risorsa.
* Ripristina una versione precedente della risorsa.

**Per creare il controllo delle versioni delle risorse**:

1. Andate alla posizione della risorsa per la quale desiderate creare una versione e fate clic su di essa per aprire la relativa pagina di risorse.

1. Fai clic sul pulsante **[!UICONTROL Navigazione globale]** e la scelta **[!UICONTROL Timeline]** dal menu.

   ![timeline-1](assets/timeline-1.png)

1. Fai clic su **[!UICONTROL Azioni]** in basso per visualizzare le azioni disponibili che puoi eseguire sulla risorsa.

1. Fai clic su **[!UICONTROL Salva come versione]** per creare una versione della risorsa.

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. Aggiungi un&#39;etichetta e un commento, quindi fai clic su **[!UICONTROL Crea]** per creare una versione. In alternativa, tocca **[!UICONTROL Annulla]** per uscire dall&#39;operazione.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. Per visualizzare la nuova versione, apri la **[!UICONTROL Mostra tutto]** nella timeline dalla pagina dei dettagli della risorsa o [!DNL Assets] e scegli **[!UICONTROL Versioni]**.

   ![version_option](assets/versions_option.png)

1. Seleziona una versione specifica per la risorsa da visualizzare in anteprima o abilitare per visualizzarla nell’interfaccia utente di Assets.

   ![select_version](assets/select_version.png)

   >[!NOTE]
   >
   >Puoi anche selezionare la risorsa dalla [Vista a elenco](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) o [Vista a colonne](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).

1. Aggiungi un’etichetta e un commento per la versione da ripristinare alla versione specifica nell’interfaccia utente di Assets.

   ![save_version](assets/save_version.png)

1. Per generare un’anteprima per la versione, fai clic su **[!UICONTROL Anteprima versione]**.
1. Per visualizzare questa versione nell’interfaccia utente di Assets, seleziona **[!UICONTROL Ripristina questa versione]**.
1. Per confrontare tra due versioni, passa alla pagina della risorsa e fai clic sulla versione da confrontare con la versione corrente.

   ![Seleziona una versione precedente della risorsa da confrontare con la versione corrente](assets/select_version_tocompare.png)

1. Dalla timeline, seleziona la versione da confrontare e trascina il cursore a sinistra per sovrapporre questa versione alla versione corrente e confrontare.

   ![confrontare_versioni](assets/compare_versions.png)

### Avviare un flusso di lavoro su una risorsa {#starting-a-workflow-on-an-asset}

Vedi [applicare un flusso di lavoro a un [!DNL Experience Manager] risorsa](/help/assets/assets-workflow.md#apply-a-workflow-to-an-aem-asset).

## Informazioni sulle raccolte {#collections}

Una raccolta è un set ordinato di risorse. Puoi utilizzare le raccolte per condividere le risorse tra i vari utenti.

* Una raccolta può includere risorse provenienti da posizioni diverse, poiché contiene solo riferimenti a tali risorse. Ogni raccolta mantiene l’integrità referenziale delle risorse.
* Puoi condividere raccolte con più utenti con diversi livelli di privilegi, ad esempio per la modifica, la visualizzazione e così via.

Un utente può avere accesso a più raccolte. Le raccolte sono dei tipi seguenti, in base alla modalità di raccolta delle risorse:

* Una raccolta con un **elenco di riferimento statico** di risorse, cartelle e altre raccolte.

* Una raccolta che utilizza un **criteri di ricerca** e popola dinamicamente le risorse in base ai criteri. Questa funzione è denominata **Raccolta avanzata**.

Vedi [Gestire le raccolte](managing-collections-touch-ui.md) per informazioni dettagliate sulla gestione della raccolta.

>[!NOTE]
>
>Per creare o modificare le risorse è necessario disporre di diritti di accesso appropriati per l’account.
