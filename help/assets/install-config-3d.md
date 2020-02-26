---
title: Installazione e configurazione di AEM 3D
seo-title: Installazione e configurazione di AEM 3D
description: Scopri come installare e configurare AEM 3D
seo-description: Scopri come installare e configurare AEM 3D
uuid: a60732ff-fd66-4f29-b901-42a3cfd58b65
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5898d084-4b45-41bc-ad2e-2fcc65b0392c
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# Installazione e configurazione di AEM 3D {#installing-and-configuring-aem-d}

L’installazione e la configurazione di AEM 3D (versione 3.0) prevede quanto segue:

1. Installazione della libreria Autodesk® FBX® SDK.
1. Download e installazione del pacchetto di codice 3D nativo.
1. Configurazione del flusso di lavoro di assimilazione delle risorse 3D e riavvio di AEM.
1. Convalida della configurazione di AEM 3D.

Consultate anche [Utilizzo di risorse](assets-3d.md)3D.

Per informazioni su prerequisiti, browser supportati e altre importanti informazioni sulla versione, consulta anche le note [sulla versione di Risorse](/help/release-notes/aem3d-release-notes.md) AEM 3D.

Vedere anche [Utilizzo del componente](using-the-3d-sites-component.md)Siti 3D.

>[!NOTE]
>
>Prima di scaricare e installare il pacchetto 3D, accertatevi di aver installato correttamente tutti i pacchetti AEM preliminari. See the [AEM 3D Release Notes.](install-config-3d.md)

## Installazione della libreria Autodesk FBX SDK {#installing-the-autodesk-fbx-sdk-library}

Il codice AEM 3D nativo richiede la libreria Autodesk FBX per supportare il formato di file FBX. Al momento Adobe non è in grado di ridistribuire la libreria.

Consultate anche Impostazioni [di configurazione](advanced-config-3d.md)avanzate.

1. Accedete all’host in cui è installato AEM.

   * Se si tratta di una distribuzione di Windows Server, accedete al server come Amministratore.
   * Se si tratta di un desktop MAC o Windows, accertatevi di disporre dei privilegi di amministratore.

1. Utilizzate il collegamento appropriato per il sistema operativo in uso per scaricare **FBX SDK versione 2016.1.2**

   * **Windows**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe)

   * **OS X**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz)

   * **Linux**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz)

1. Installare l’SDK FBX:

   * Windows. Installate nella stessa unità in cui si trova AEM.
   * Mac. Installate nella stessa partizione in cui si trova AEM.
   * Linux. Estraete il pacchetto scaricato e seguite le istruzioni riportate in `<yourFBXSDKpath>/Install_FbxFileSdk.txt`. Installa l’SDK in `/usr`.

## Download e installazione del pacchetto di codice 3D nativo {#downloading-and-installing-the-native-d-code-package}

>[!NOTE]
>
>Prima di procedere con l’installazione e la configurazione di AEM 3D, Adobe consiglia di implementare eventuali service pack applicabili e altri pacchetti di funzioni correlati. See [AEM 3D Release Notes](/help/release-notes/aem3d-release-notes.md).

Consultate anche Impostazioni [di configurazione](advanced-config-3d.md)avanzate.

**Per installare il pacchetto** di codice 3D nativo:

1. Effettua una delle operazioni seguenti:

   * Se si tratta di una distribuzione di Windows Server, accedete al server come amministratore.
   * Se si tratta di un desktop Mac o Windows, accertatevi di disporre dei privilegi di amministratore.

1. Assicurati di disporre di un browser supportato per accedere ad AEM.

   Consultate Requisiti [di](/help/release-notes/aem3d-release-notes.md#system-requirements)sistema.

1. Utilizzando un browser supportato, accedete ad AEM con privilegi di amministratore.
1. In AEM, fai clic sul logo AEM per accedere alla console di navigazione globale, quindi fai clic sull’icona **[!UICONTROL Strumenti]** e passa a **[!UICONTROL Amministrazione > Distribuzione > Condivisione]** pacchetti.
1. Nella pagina Adobe, usate le credenziali Adobe ID per accedere al vostro account Adobe Creative Cloud.
1. Nella pagina dei pacchetti Adobe, individua la versione 3.0.1 del `AEM-6.4-DynamicMedia-3D` feature pack, quindi scaricala.

1. In AEM, fate clic su **[!UICONTROL Strumenti > Amministrazione > Distribuzione > Gestione]** pacchetti.
1. Individuate il pacchetto di funzionalità scaricato, quindi fate clic su **[!UICONTROL Installa]**.

1. Nella finestra di dialogo **[!UICONTROL Installa pacchetto]** , espandete Impostazioni **** avanzate, quindi impostate Gestione controllo **[!UICONTROL accesso]** su **Unisci**.
1. Fate clic su **[!UICONTROL Installa]** per avviare l&#39;installazione del pacchetto.

   Il file `sample-3D-content.zip` viene memorizzato nella cartella principale **[!UICONTROL Risorse]** . Per ulteriori informazioni, consultate [Convalida dell&#39;impostazione di AEM 3D](#validating-the-setup-of-aem-d) .

## Configurazione del flusso di lavoro di assimilazione delle risorse 3D e riavvio di AEM {#configuring-the-d-asset-ingestion-workflow-and-restarting-aem}

**Per configurare il flusso di lavoro** di assimilazione delle risorse 3D:

1. In AEM, fai clic sul logo AEM per accedere alla console di navigazione globale, quindi fai clic sull’icona **[!UICONTROL Strumenti]** e passa a **[!UICONTROL Flusso di lavoro > Modelli]**.
1. Nella pagina Modelli **[!UICONTROL di]** flusso di lavoro, passa il mouse sul flusso di lavoro **[!UICONTROL DAM Update Asset]** e, quando viene visualizzato il segno di spunta, selezionalo.

1. Sulla barra degli strumenti, fare clic su **[!UICONTROL Modifica]**.
1. Nella schermata Aggiorna risorsa **** DAM, nel pannello mobile AEM, fate clic sull&#39;icona **[!UICONTROL Più]** a destra di Workflow per espandere l&#39;elenco. Selezionare Passaggio **** processo nell&#39;elenco.
1. Trascina il Passaggio **** processo e rilascialo nel flusso di lavoro immediatamente prima del componente Flusso di lavoro risorse aggiornamento **[!UICONTROL DAM Completato]** vicino alla fine del flusso di lavoro.

   ![3d_process_step_underaem6-4](assets/3d_process_step_underaem6-4.png)

1. Fate doppio clic sul passaggio del processo appena aggiunto.
1. Nella finestra di dialogo Proprietà **** passo, nella scheda **[!UICONTROL Comune]** , nel campo **[!UICONTROL Titolo]** , immettere una descrizione appropriata per il processo, ad esempio `Process 3D content`.
1. Click the **[!UICONTROL Process]** tab.

1. Dal menu a discesa **[!UICONTROL Processo]** , selezionate Servizio **[!UICONTROL oggetto 3D]** geometrico, quindi selezionate la casella di controllo **[!UICONTROL Avanzamento]** gestore.

   ![3d_install-process-steppropertiesdlg](assets/3d_install-process-steppropertiesdlg.png)

1. Nell’angolo superiore destro della finestra di dialogo, fate clic sull’icona del segno di spunta per tornare alla pagina Aggiorna risorsa DAM.
1. Nell’angolo in alto a destra della pagina Aggiorna risorsa **** DAM, fate clic su **[!UICONTROL Sincronizza]** per salvare il modello di flusso di lavoro modificato.
1. Riavviate AEM.

   Dopo il riavvio, è possibile caricare il contenuto 3D e farlo elaborare da AEM.

   Continua con la [convalida dell’impostazione di AEM 3D](#validating-the-setup-of-aem-d).

## Convalida della configurazione di AEM 3D {#validating-the-setup-of-aem-d}

1. In AEM, fai clic su **[!UICONTROL Strumenti > Risorse]**, quindi scarica `sample-3D-content.zip`ed espandi il file scaricato. (È ora possibile eliminare `sample-3D-content.zip` in AEM.)

   Accertatevi di essere nella vista **[!UICONTROL a]** schede per visualizzare i commenti di caricamento ed elaborazione nei passaggi successivi.

1. Create una cartella denominata `test3d` per ricevere il contenuto di prova.
1. Caricate tutti i file `sample-3D-content/images` nella `test3d` cartella.
1. Attendete il completamento del caricamento e dell’elaborazione. Potrebbe essere necessario aggiornare il browser.

   Caricate i tre `.fbx` file `sample-3D-content/` nella `test3d` cartella.

   Non caricate ancora i file modello .ma.

1. Nella vista a schede, osservate i banner dei messaggi visualizzati sulle schede delle risorse 3d.

   Ogni risorsa procede attraverso diverse fasi di elaborazione. **[!UICONTROL Quando si]** crea anteprima... al termine del processo di elaborazione, la scheda viene aggiornata con una miniatura. Al termine dell&#39;elaborazione finale, il banner viene sostituito con l&#39;indicatore **[!UICONTROL NEW]** .

   >[!NOTE]
   >
   >Si prevede un utilizzo CPU molto elevato durante l&#39;elaborazione 3D in corso. A seconda della capacità della CPU disponibile, il completamento dell&#39;elaborazione potrebbe richiedere molto tempo.

   ![screenshot_2017-01-2518-29-32](assets/screenshot_2017-01-2518-29-32.png)

1. Verrà ora illustrato come risolvere le dipendenze dei file.

   Nel banner **[!UICONTROL Dipendenze]** non risolte per la `stage-helipad.fbx` scheda, fate clic sull&#39;icona Punto **** esclamativo per passare alle proprietà della risorsa e aprire la scheda **Dipendenze** .

   ![chlimage_1-372](assets/chlimage_1-372.png)

1. Fate clic sull’icona **[!UICONTROL Cartella/lente]** di ingrandimento a destra del nome del file per aprire il browser delle risorse e risolvere le dipendenze come segue:

   ![chlimage_1-373](assets/chlimage_1-373.png)

1. Fate clic su **[!UICONTROL Salva]** e **[!UICONTROL Chiudi]** per completare l’elaborazione della risorsa e tornare rispettivamente alla vista **[!UICONTROL a]** schede.
1. Al termine dell&#39;elaborazione, nella vista **[!UICONTROL a]** schede viene visualizzato quanto segue:

   ![chlimage_1-374](assets/chlimage_1-374.png)

1. Nella pagina test3d, fate clic sulla `logo-sphere.fbx` scheda per aprire il modello in visualizzazione **** Dettagli.

   Nell&#39;angolo superiore destro della pagina logo-space.fbx, fate clic sull&#39;icona Evidenziatore fase per espandere il menu a discesa, quindi selezionate `stage-spotlights.fbx`.

   ![chlimage_1-375](assets/chlimage_1-375.png)

1. Dall&#39;elenco a discesa **[!UICONTROL Evidenziatore]** fase, selezionate `stage-helipad.fbx`.

   Utilizzo del pulsante sinistro del mouse per regolare la visualizzazione. Lo sfondo e l’illuminazione del modello cambiano per riflettere la nuova selezione dell’area di visualizzazione.

   ![chlimage_1-376](assets/chlimage_1-376.png)

## Configurazione del supporto per le risorse Adobe Dimension {#configuring-support-for-adobe-dimension-assets}

>[!NOTE]
>
>Questa attività di configurazione è facoltativa.

Facoltativamente puoi configurare il supporto in AEM 3D per le risorse Adobe Dimension.

È necessario configurare un servizio di conversione esterno per consentire l’assimilazione, l’anteprima e la pubblicazione di risorse Adobe Dimension 3D in AEM. Il servizio converte dal formato proprietario Adobe Dimension (`.dn`) in una variante di glTF (formattata come `.glb` file) che viene salvata con la risorsa Dn come rappresentazione. La `.glb` rappresentazione viene utilizzata per la visualizzazione basata sul Web della risorsa 3D in Risorse AEM, Siti e Schermate ed è disponibile anche per il download e l’utilizzo con applicazioni di terze parti.

>[!NOTE]
>
>Il servizio di conversione è ospitato da Adobe in Amazon AWS. Dopo aver configurato correttamente il servizio, `.dn` i file caricati in AEM vengono quindi copiati in modo sicuro nel servizio di conversione tramite memorizzazione temporanea in Amazon S3. Il risultato della conversione viene trasferito nuovamente ad AEM tramite l’archiviazione temporanea S3. Tutti i trasferimenti e lo storage sono protetti. Inoltre, il contenuto persiste in S3 e il servizio di conversione solo brevemente (generalmente non più di pochi minuti).

**Per configurare il supporto per le risorse** Adobe Dimension:

1. Contatta il tuo account manager Adobe AEM, un esperto di provisioning o un rappresentante di supporto per richiedere le credenziali per i servizi **** AEM3D.

   >[!NOTE]
   >
   >Per ogni organizzazione è richiesto un solo set di credenziali, indipendentemente dal numero di istanze AEM in cui sono installate le credenziali.

1. Verificate di aver ricevuto le seguenti informazioni:

   * accountId
   * customerId
   * password
   * identityPoolId
   * userPoolId
   * clientId

1. In qualità di amministratore, accedete all’istanza di creazione di AEM in cui desiderate installare le credenziali, quindi aprite **[!UICONTROL CRXDE Lite]**.
1. Configurare le nuove informazioni sulle credenziali effettuando le seguenti operazioni in CRXDE Lite:

   1. Individuare `/libs/settings/dam/v3D/services/dncr` e impostare la `clientId` proprietà sul nuovo valore.
   1. Individuate `/libs/settings/dam/v3D/services/aws` e impostate le `accountId`, `customerId`, `identityPoolId`e `userPoolId` le proprietà sui nuovi valori.
   1. Caricate il nuovo valore della password nella `encryptedPassword` proprietà. Questo valore viene cifrato automaticamente quando toccate **[!UICONTROL Salva tutto]**.
   1. Toccate **[!UICONTROL Salva tutto]**, ricaricate la pagina, quindi verificate che la `encryptedPassword` proprietà contenga una stringa diversa racchiusa tra parentesi graffe. Questo aspetto indica che la password è crittografata e protetta correttamente.

1. Specificate il formato della rappresentazione di `.glb` conversione effettuando le seguenti operazioni in **[!UICONTROL CRXDE Lite]**:

   1. Passare a `/libs/settings/dam/v3D/services/dncr` in **[!UICONTROL CRXDE Lite]**.
   1. Impostare la `outputFormat` proprietà su `Dn` o `generic`.

      Quando è impostata su `Dn`, la `.glb` conversione include estensioni specifiche di Adobe, come l’illuminazione IBL, per una migliore qualità quando visualizzate le risorse Dn in AEM. Tuttavia, il rendering .glb convertito potrebbe non essere eseguito correttamente nelle applicazioni di terze parti.

      Quando è impostata su `generic`, la `.glb` rappresentazione è generica senza estensioni specifiche di Adobe. Questa impostazione consente di utilizzarla in applicazioni di terze parti, mentre la visualizzazione con il visualizzatore AEM 3D sarà visivamente non ottimale.

1. Attivate il formato di file Dn effettuando le seguenti operazioni in **[!UICONTROL CRXDE Lite]**:

   1. Accedi a `/libs/settings/dam/v3D/assetTypes/Dn`.
   1. Impostate la `Enabled` proprietà su true.

1. Convalida la configurazione effettuando le seguenti operazioni:

   1. Apri Risorse AEM.
   1. Caricate `logo_sphere.dn` nella `test3d` cartella. Il file si trova in `sample-3D-content/models`.

      Nota: `sample-3D-content.zip` in precedenza era stato scaricato per la convalida delle funzionalità 3D di base.
   1. Tornate alla vista **[!UICONTROL a]** schede e osservate il banner di messaggio mostrato sulla risorsa caricata. **[!UICONTROL Formato]** di conversione... il banner viene visualizzato mentre è in corso il processo di conversione.
   1. Al termine dell’elaborazione, aprite la risorsa in visualizzazione **** Dettagli per verificare che la risorsa convertita sia visualizzata correttamente e che i controlli di navigazione del visualizzatore siano utilizzabili.
   ![image2018-11-2_15-51-19](assets/image2018-11-2_15-51-19.png)

   Se sulla risorsa Dn nella vista **[!UICONTROL a]** schede viene visualizzato un &quot;Errore di elaborazione&quot; dopo 10-15 minuti, la conversione non è riuscita.

   In tal caso, potete risolvere i problemi di conversione effettuando le seguenti operazioni:

   * Eliminate la risorsa, quindi caricatela di nuovo.
   * Assicurarsi di aver impostato correttamente tutti i parametri di configurazione in **[!UICONTROL CRXDE Lite]**.
   * Verificate che nessun firewall stia bloccando l&#39;accesso al servizio di conversione e agli endpoint AWS.
