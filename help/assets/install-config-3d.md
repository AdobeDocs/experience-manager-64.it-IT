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
exl-id: 5baaef61-5c70-4796-8ae2-44053e855ad9
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 1%

---

# Installazione e configurazione di AEM 3D {#installing-and-configuring-aem-d}

>[!IMPORTANT]
>
>AEM 3D in AEM 6.4 non è più supportato. Adobe consiglia di utilizzare la funzione risorse 3D in [AEM come Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) o [AEM 6.5.3 o superiore.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic)

L&#39;installazione e la configurazione di AEM 3D (versione 3.0) prevede quanto segue:

1. Installazione della libreria Autodesk® FBX® SDK.
1. Download e installazione del pacchetto di codice 3D nativo.
1. Configurazione del flusso di lavoro di acquisizione delle risorse 3D e riavvio AEM.
1. Convalida della configurazione di AEM 3D.

Consulta anche [Utilizzo di risorse 3D](assets-3d.md).

Consulta anche [AEM note sulla versione di 3D Assets](/help/release-notes/aem3d-release-notes.md) per prerequisiti, browser supportati e altre informazioni importanti sulla versione.

Vedi anche [Utilizzo del componente Siti 3D](using-the-3d-sites-component.md).

>[!NOTE]
>
>Prima di scaricare e installare il pacchetto 3D, assicurati di aver installato tutti i pacchetti AEM prerequisiti con successo. Consulta le [AEM note sulla versione 3D.](install-config-3d.md)

## Installazione della libreria SDK Autodesk FBX {#installing-the-autodesk-fbx-sdk-library}

Il codice 3D nativo AEM richiede la libreria Autodesk FBX per supportare il formato di file FBX. (Adobe non è attualmente in grado di ridistribuire questa libreria.)

Vedere anche [Impostazioni di configurazione avanzate](advanced-config-3d.md).

1. Accedi all&#39;host in cui è installato AEM.

   * Se si tratta di una distribuzione di Windows Server, accedere al server come Amministratore.
   * Se si tratta di un desktop MAC o Windows, assicurati di disporre dei privilegi di amministratore.

1. Usa il collegamento appropriato per il tuo sistema operativo per scaricare **FBX SDK versione 2016.1.2**

   * **Windows**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe)

   * **OS X**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz)

   * **Linux**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz)

1. Installa l&#39;SDK FBX:

   * Windows. Installare nella stessa unità in cui si trova AEM.
   * Mac. Installare nella stessa partizione in cui si trova AEM.
   * Linux. Estrai il pacchetto scaricato e segui le istruzioni in `<yourFBXSDKpath>/Install_FbxFileSdk.txt`. Installa l&#39;SDK su `/usr`.

## Download e installazione del pacchetto di codice 3D nativo {#downloading-and-installing-the-native-d-code-package}

>[!NOTE]
>
>Prima di procedere con l&#39;installazione e la configurazione di AEM 3D, l&#39;Adobe consiglia di distribuire eventuali service pack applicabili e altri feature pack correlati. Consulta [AEM Note sulla versione 3D](/help/release-notes/aem3d-release-notes.md).

Vedere anche [Impostazioni di configurazione avanzate](advanced-config-3d.md).

**Per installare il pacchetto** di codice 3D nativo:

1. Effettua una delle operazioni seguenti:

   * Se si tratta di una distribuzione di Windows Server, accedere al server come Amministratore.
   * Se si tratta di un desktop Mac o Windows, assicurati di disporre dei privilegi di amministratore.

1. Assicurati di disporre di un browser supportato per accedere a AEM.

   Vedere [Requisiti di sistema](/help/release-notes/aem3d-release-notes.md#system-requirements).

1. Accedi a [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Individua la versione 3.0.1 del `AEM-6.4-DynamicMedia-3D` feature pack e scaricala.

1. In AEM, fai clic su **[!UICONTROL Strumenti > Amministrazione > Distribuzione > Gestione pacchetti]**.

1. Carica il feature pack scaricato in AEM. Individualo e fai clic su **[!UICONTROL Installa]**.

1. Nella finestra di dialogo **[!UICONTROL Installa pacchetto]**, espandi **Impostazioni avanzate**, quindi imposta **[!UICONTROL Gestione controllo accessi]** su **Unisci**.
1. Fai clic su **[!UICONTROL Installa]** per iniziare l&#39;installazione del pacchetto.

   Il file `sample-3D-content.zip` viene posizionato nella cartella principale **[!UICONTROL Risorse]**. Per ulteriori informazioni, consulta [Convalida della configurazione di AEM 3D](#validating-the-setup-of-aem-d) .

## Configurazione del flusso di lavoro di acquisizione delle risorse 3D e riavvio AEM {#configuring-the-d-asset-ingestion-workflow-and-restarting-aem}

**Per configurare il flusso di lavoro** di inserimento delle risorse 3D:

1. In AEM, fai clic sul logo AEM per accedere alla console di navigazione globale, quindi fai clic sull&#39;icona **[!UICONTROL Strumenti]** e passa a **[!UICONTROL Flusso di lavoro > Modelli]**.
1. Nella pagina **[!UICONTROL Modelli di flusso di lavoro]** , passa il puntatore del mouse sul flusso di lavoro **[!UICONTROL Aggiorna risorsa DAM]** e, quando viene visualizzato il segno di spunta, selezionalo.

1. Sulla barra degli strumenti, fai clic su **[!UICONTROL Modifica]**.
1. Nella schermata **[!UICONTROL Risorsa di aggiornamento DAM]**, nel pannello mobile AEM, fai clic sull&#39;icona **[!UICONTROL Più]** a destra di Flusso di lavoro per espandere l&#39;elenco. Selezionare **[!UICONTROL Process Step]** nell&#39;elenco.
1. Trascina **[!UICONTROL Process Step]** e rilascialo nel flusso di lavoro immediatamente prima del componente **[!UICONTROL DAM Update Asset Workflow Completed]** , accanto alla fine del flusso di lavoro.

   ![3d_process_step_underaem6-4](assets/3d_process_step_underaem6-4.png)

1. Fai doppio clic sul passaggio del processo appena aggiunto.
1. Nella finestra di dialogo **[!UICONTROL Proprietà passaggio]**, sotto la scheda **[!UICONTROL Comune]**, nel campo **[!UICONTROL Titolo]**, immetti una descrizione appropriata per il processo, ad esempio `Process 3D content`.
1. Fare clic sulla scheda **[!UICONTROL Processo]**.

1. Dal menu a discesa **[!UICONTROL Processo]**, selezionare **[!UICONTROL Servizio oggetti Geometric 3D]**, quindi selezionare la casella di controllo **[!UICONTROL Avanzamento gestore]**.

   ![3d_install-process-steppropertiesdlg](assets/3d_install-process-steppropertiesdlg.png)

1. Fai clic sull’icona del segno di spunta nell’angolo in alto a destra della finestra di dialogo per tornare alla pagina Risorsa di aggiornamento DAM.
1. Fai clic su **[!UICONTROL Sincronizza]** nell’angolo in alto a destra della pagina **[!UICONTROL Aggiorna risorsa DAM]** per salvare il modello di flusso di lavoro modificato.
1. Riavvia AEM.

   Dopo il riavvio, sei pronto per caricare il contenuto 3D e averlo AEM elaborato.

   Continua con [Convalida la configurazione di AEM 3D](#validating-the-setup-of-aem-d).

## Convalida della configurazione di AEM 3D {#validating-the-setup-of-aem-d}

1. In AEM, fai clic su **[!UICONTROL Strumenti > Risorse]**, quindi scarica `sample-3D-content.zip` ed espandi il file scaricato. (È ora possibile eliminare `sample-3D-content.zip` in AEM.)

   Assicurati di essere in **[!UICONTROL Vista a schede]** per visualizzare il caricamento e l&#39;elaborazione dei feedback nei passaggi successivi.

1. Crea una cartella denominata `test3d` per ricevere il contenuto del test.
1. Carica tutti i file da `sample-3D-content/images` alla cartella `test3d` .
1. Attendi il completamento del caricamento e dell’elaborazione. Potrebbe essere necessario aggiornare il browser.

   Carica i tre file `.fbx` da `sample-3D-content/` alla cartella `test3d` .

   Non caricare ancora i file del modello .ma.

1. Nella Vista a schede, osservate i banner dei messaggi visualizzati sulle schede delle risorse 3d.

   Ogni risorsa procede attraverso diverse fasi di elaborazione. Quando **[!UICONTROL Creazione anteprima...]** completamento del passaggio di elaborazione, la scheda viene aggiornata con un&#39;immagine in miniatura. Al termine dell&#39;elaborazione finale, il banner viene sostituito con l&#39;indicatore **[!UICONTROL NEW]**.

   >[!NOTE]
   >
   >Si prevede un utilizzo molto elevato della CPU durante l&#39;elaborazione 3D in corso. A seconda della capacità della CPU disponibile, potrebbe essere necessario un notevole tempo per completare tutta l&#39;elaborazione.

   ![screenshot_2017-01-2518-29-32](assets/screenshot_2017-01-2518-29-32.png)

1. Verrà ora illustrato come risolvere le dipendenze dei file.

   Nel banner **[!UICONTROL Dipendenze non risolte]** per la scheda `stage-helipad.fbx`, fai clic sull&#39;icona **[!UICONTROL Punto esclamativo]** per accedere alle proprietà della risorsa e apri la scheda **Dipendenze** .

   ![chlimage_1-372](assets/chlimage_1-372.png)

1. Fai clic sull&#39;icona **[!UICONTROL Cartella/Lente di ingrandimento]** a destra del nome del file per aprire il browser delle risorse e risolvere le dipendenze come segue:

   ![chlimage_1-373](assets/chlimage_1-373.png)

1. Fai clic su **[!UICONTROL Salva]** e **[!UICONTROL Chiudi]** per completare l’elaborazione della risorsa e tornare rispettivamente alla **[!UICONTROL Vista a schede]**.
1. Al termine dell&#39;elaborazione, vedi quanto segue in **[!UICONTROL Vista a schede]**:

   ![chlimage_1-374](assets/chlimage_1-374.png)

1. Nella pagina test3d, fai clic sulla scheda `logo-sphere.fbx` per aprire il modello in **[!UICONTROL Vista dettagli]**.

   Nell’angolo in alto a destra della pagina logo-sphere.fbx, fai clic sull’icona Proiettore area di visualizzazione per espandere il menu a discesa, quindi seleziona `stage-spotlights.fbx`.

   ![chlimage_1-375](assets/chlimage_1-375.png)

1. Dall&#39;elenco a discesa **[!UICONTROL Luce panoramica stage]**, selezionare `stage-helipad.fbx`.

   Usare il pulsante sinistro del mouse per regolare la visualizzazione. Lo sfondo e l&#39;illuminazione del modello cambiano per riflettere la nuova selezione dell&#39;area di visualizzazione.

   ![chlimage_1-376](assets/chlimage_1-376.png)

## Configurazione del supporto per le risorse Adobe Dimension {#configuring-support-for-adobe-dimension-assets}

>[!NOTE]
>
>Questa attività di configurazione è facoltativa.

Facoltativamente, puoi configurare il supporto in AEM 3D per le risorse Adobe Dimension.

È necessario configurare un servizio di conversione esterno per consentire l’acquisizione, l’anteprima e la pubblicazione di risorse Adobe Dimension 3D in AEM. Il servizio converte dal formato proprietario Adobe Dimension (`.dn`) in una variante di glTF (formattata come file `.glb`) che viene salvata con la risorsa Dn come rendering. Il rendering `.glb` viene utilizzato per la visualizzazione basata sul Web della risorsa 3D in AEM Assets, Sites e Screens ed è disponibile per il download per l’utilizzo con applicazioni di terze parti.

>[!NOTE]
>
>Il servizio di conversione è ospitato da Adobe in Amazon AWS. Dopo aver configurato correttamente il servizio, i file `.dn` caricati in AEM vengono quindi copiati in modo sicuro nel servizio di conversione tramite archiviazione temporanea in Amazon S3. Il risultato della conversione viene trasferito nuovamente in AEM tramite l&#39;archiviazione temporanea S3. Tutti i trasferimenti e lo storage sono protetti. Inoltre, il contenuto persiste in S3 e il servizio di conversione solo brevemente (in genere non più di qualche minuto).

**Per configurare il supporto per le risorse** Adobe Dimension:

1. Per richiedere le credenziali per **AEM3D Services**, contatta il tuo responsabile AEM account, l&#39;esperto di provisioning o il rappresentante del supporto di riferimento.

   >[!NOTE]
   >
   >Per ogni organizzazione è necessario un solo set di credenziali, indipendentemente dal numero di istanze AEM in cui sono installate le credenziali.

1. Verifica di aver ricevuto le seguenti informazioni:

   * accountId
   * customerId
   * password
   * identityPoolId
   * userPoolId
   * clientId

1. In qualità di amministratore, accedi all&#39;istanza di authoring AEM in cui desideri installare le credenziali, quindi apri **[!UICONTROL CRXDE Lite]**.
1. Configura le nuove informazioni sulle credenziali eseguendo le operazioni seguenti in CRXDE Lite:

   1. Passa a `/libs/settings/dam/v3D/services/dncr` e imposta la proprietà `clientId` sul nuovo valore.
   1. Passa a `/libs/settings/dam/v3D/services/aws` e imposta le proprietà `accountId`, `customerId`, `identityPoolId` e `userPoolId` sui nuovi valori.
   1. Carica il nuovo valore della password nella proprietà `encryptedPassword` . Questo valore viene crittografato automaticamente quando si tocca **[!UICONTROL Salva tutto]**.
   1. Tocca **[!UICONTROL Salva tutto]**, ricarica la pagina, quindi verifica che la proprietà `encryptedPassword` mostri una stringa diversa racchiusa tra parentesi graffe. Questo aspetto indica che la password è crittografata e protetta correttamente.

1. Specifica il formato del rendering di conversione `.glb` eseguendo le operazioni seguenti in **[!UICONTROL CRXDE Lite]**:

   1. Passa a `/libs/settings/dam/v3D/services/dncr` in **[!UICONTROL CRXDE Lite]**.
   1. Imposta la proprietà `outputFormat` su `Dn` o `generic`.

      Quando è impostata su `Dn`, la conversione `.glb` include estensioni specifiche per Adobe, come l’illuminazione IBL, per una migliore qualità quando si visualizzano le risorse Dn in AEM. Tuttavia, il rendering .glb convertito potrebbe non essere eseguito correttamente nelle applicazioni di terze parti.

      Se è impostato su `generic`, il rendering `.glb` è generico senza estensioni specifiche per Adobe. Questa impostazione consente di utilizzarla in applicazioni di terze parti, mentre la visualizzazione con il visualizzatore 3D AEM sarà visivamente non ottimale.

1. Abilita il formato del file Dn effettuando le seguenti operazioni in **[!UICONTROL CRXDE Lite]**:

   1. Accedi a `/libs/settings/dam/v3D/assetTypes/Dn`.
   1. Imposta la proprietà `Enabled` su true.

1. Convalida la configurazione effettuando le seguenti operazioni:

   1. Apri AEM Assets.
   1. Carica `logo_sphere.dn` nella cartella `test3d` . Il file si trova in `sample-3D-content/models`.

      Nota che `sample-3D-content.zip` è stato scaricato in precedenza per la convalida della funzionalità 3D di base.
   1. Torna alla **[!UICONTROL Vista a schede]** e osserva il banner messaggi mostrato sulla risorsa caricata. Il **[!UICONTROL Formato di conversione...Durante il processo di conversione viene visualizzato il banner]** .
   1. Al termine dell’elaborazione, apri la risorsa in **[!UICONTROL Vista dettagli]** per verificare che la risorsa convertita sia visualizzata correttamente e che i controlli di navigazione del visualizzatore siano utilizzabili.

   ![image2018-11-2_15-51-19](assets/image2018-11-2_15-51-19.png)

   Se sulla risorsa Dn viene visualizzato un &quot;Errore di elaborazione&quot; nella **[!UICONTROL Vista a schede]** dopo 10-15 minuti, la conversione non è riuscita.

   In tal caso, puoi risolvere i problemi della conversione facendo quanto segue:

   * Elimina la risorsa, quindi caricala di nuovo.
   * Assicurati di aver impostato correttamente tutti i parametri di configurazione in **[!UICONTROL CRXDE Lite]**.
   * Verifica che nessun firewall stia bloccando l’accesso al servizio di conversione e agli endpoint AWS.
