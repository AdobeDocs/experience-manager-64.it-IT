---
title: Video
description: Assets permette di gestire in modo centralizzato le risorse video. Consente di caricare i video direttamente in Assets per la codifica automatica in Scene7 e di accedere ai video di Scene7 direttamente da Assets per la creazione e modifica delle pagine.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
translation-type: tm+mt
source-git-commit: 6be46f6986d1631f711cfd4464cc4f2d17014681
workflow-type: tm+mt
source-wordcount: '1683'
ht-degree: 45%

---


# Video{#video}

Risorse offre una gestione centralizzata delle risorse video in cui è possibile caricare i video direttamente su Risorse per la codifica automatica in Dynamic Media Classic e accedere ai video Dynamic Media Classic direttamente da Risorse per l’authoring delle pagine.

L&#39;integrazione video di Dynamic Media Classic estende la portata dei video ottimizzati a tutti gli schermi (rilevamento automatico della periferica e della larghezza di banda).

* Il componente video Dynamic Media Classic (Scene7) esegue automaticamente il rilevamento del dispositivo e della larghezza di banda per riprodurre il formato e la qualità video corretti su computer desktop, tablet e dispositivi mobili.
* Risorse: è possibile includere set di video adattivi anziché risorse con un singolo video. Un set di video adattivo è un contenitore di tutte le rappresentazioni video necessarie a consentirne la riproduzione su diversi tipi di schermi. Un set video adattivo raggruppa versioni dello stesso video codificate con diversi bitrate e formati quali 400, 800 e 1000 kbps. Utilizza un set video adattivo, insieme al componente video S7, per lo streaming video adattivo per schermi diversi, come computer desktop e dispositivi mobili iOS, Android, Blackberry e Windows. Per ulteriori informazioni, vedi [la documentazione di Scene7 sui set di video adattivi](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).

## Informazioni su FFMPEG e Dynamic Media Classic {#about-ffmpeg-and-scene}

Il processo di codifica video predefinito si basa sull’utilizzo dell’integrazione con i profili video basata su FFMPEG. Pertanto, il flusso di lavoro Aggiorna risorsa DAM preconfigurato contiene i due passaggi seguenti, basato su FFMPEG:

* Miniature FFMPEG
* Codifica FFMPEG

Tenete presente che l’attivazione e la configurazione dell’integrazione con Dynamic Media Classic non rimuove o disattiva automaticamente questi due passaggi del flusso di lavoro dal flusso di lavoro per l’assimilazione delle risorse DAM Update. Se utilizzi già la codifica video basata su FFMPEG in AEM, è probabile che FFMPEG sia già installato negli ambienti di authoring. In questo caso, un nuovo video caricato con Risorse viene codificato due volte: una volta dall&#39;encoder FFMPEG e una dall&#39;integrazione con Dynamic Media Classic.

Se la codifica video basata su FFMPEG in AEM è configurata e FFMPEG è installato, Adobe consiglia di rimuovere i due flussi di lavoro FFMPEG dai flussi di lavoro Aggiorna risorsa DAM.

### Formati supportati {#supported-formats}

Per il componente Video Dynamic Media Classic sono supportati i seguenti formati:

* F4V H.264
* MP4 H.264

### Decidere dove caricare il video {#deciding-where-to-upload-your-video}

La decisione su dove caricare le risorse video dipende da quanto segue:

* Hai bisogno di un flusso di lavoro per la risorsa video?
* Hai bisogno della funzione di controllo delle versioni per la risorsa video?

Se la risposta è “sì” ad almeno una di queste domande, carica il video direttamente in Adobe DAM. Se la risposta è &quot;no&quot; a entrambe le domande, caricate il video direttamente in Dynamic Media Classic. Il flusso di lavoro per ogni scenario è descritto nella sezione seguente.

#### Se stai caricando il video direttamente in Adobe Assets  {#if-you-are-uploading-your-video-directly-to-adobe-assets}

Se hai bisogno di un flusso di lavoro o della gestione delle versioni per le tue risorse, devi prima caricarle in Adobe Assets. Di seguito è riportato il flusso di lavoro consigliato:

1. Caricate la risorsa video in  risorse di Adobe e codificatela e pubblicate automaticamente in Dynamic Media Classic.
1. In AEM, accedi alle risorse video in WCM nella scheda **[!UICONTROL Filmati]** del Content Finder.
1. Creazione con Dynamic Media Classic video o componente video di base.

#### Se state caricando il video in Dynamic Media Classic {#if-you-are-uploading-your-video-to-scene}

Se non avete bisogno di un flusso di lavoro o di un controllo delle versioni per le risorse, caricate le risorse in Dynamic Media Classic. Di seguito è riportato il flusso di lavoro consigliato:

1. In Dynamic Media Classic, [impostare un caricamento e una codifica FTP pianificati su Dynamic Media Classic (sistema automatizzato)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#uploading-your-files).
1. In AEM, accedete alle risorse video in WCM nella scheda **[!UICONTROL Dynamic Media Classic]** di Content Finder.
1. Creare contenuti con il componente video Dynamic Media Classic.

### Configurazione dell&#39;integrazione con Dynamic Media Classic Video {#configuring-integration-with-scene-video}

**Per configurare i predefiniti universali**:

1. In **[!UICONTROL Cloud Services]**, andate alla configurazione **[!UICONTROL Dynamic Media Classic]** e fate clic su **[!UICONTROL Modifica]**.
1. Seleziona la scheda **[!UICONTROL Video]**.

   >[!NOTE]
   >
   >La scheda **[!UICONTROL Video]** non viene visualizzata se la pagina non ha una configurazione cloud. Vedere [Abilitazione di Dynamic Media Classic per WCM](#enablingscene7forwcm).

1. Seleziona il profilo di codifica video adattivo, uno dei profili di codifica per video singolo preconfigurati oppure un profilo di codifica video personalizzato.

   >[!NOTE]
   >
   >Per ulteriori informazioni sul significato dei predefiniti per video, consultate la [documentazione di Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe consiglia di selezionare entrambi i set video adattivi per la configurazione dei predefiniti universali o di selezionare l’opzione **[!UICONTROL Codifica video adattiva]**.

1. I profili di codifica selezionati vengono applicati automaticamente a tutti i video caricati nella cartella di destinazione CQ DAM configurata per questa configurazione cloud Dynamic Media Classic. Potete impostare più configurazioni cloud Dynamic Media Classic con diverse cartelle di destinazione per applicare profili di codifica diversi in base alle esigenze.

### Aggiornamento del visualizzatore e dei predefiniti di codifica {#updating-viewer-and-encoding-presets}

Per aggiornare i predefiniti per visualizzatori e di codifica video in AEM, poiché i predefiniti sono stati aggiornati in Dynamic Media Classic, andate alla configurazione Dynamic Media Classic nella configurazione cloud e fate clic su **Aggiorna il visualizzatore e i predefiniti di codifica**.

![chlimage_1-131](assets/chlimage_1-131.png)

### Caricare il video principale {#uploading-your-master-video}

Per caricare il video principale in Dynamic Media Classic da  Adobe DAM:

1. Andate alla cartella di destinazione CQ DAM in cui avete configurato la configurazione cloud con i profili di codifica Dynamic Media Classic.
1. Fai su **[!UICONTROL Carica]** per caricare il video principale. Il caricamento e la codifica dei video sono completati dopo il completamento del flusso di lavoro [!UICONTROL DAM Update Asset] e dopo che **[!UICONTROL Publish to Dynamic Media Classic]** ha un segno di spunta.

   >[!NOTE]
   >
   >La generazione delle miniature video potrebbe richiedere del tempo.

   Trascinate il video principale DAM sul componente video per accedere alle rappresentazioni proxy codificate di Dynamic Media Classic per la distribuzione *all*.

### Componente video di base e componente video di Dynamic Media Classic {#foundation-video-component-versus-scene-video-component}

Quando usate AEM, potete accedere sia al componente Video disponibile in Siti che al componente video Dynamic Media Classic (Scene7). Questi componenti non sono intercambiabili.

Il componente video Dynamic Media Classic funziona solo per i video Dynamic Media Classic. Il componente foundation funziona con i video memorizzati da AEM (utilizzando ffmpeg) e video Dynamic Media Classic.

La matrice seguente spiega quando utilizzare questi componenti:

![chlimage_1-132](assets/chlimage_1-132.png)

>[!NOTE]
>
>Il componente video Dynamic Media Classic utilizza il profilo video universale. Tuttavia, potete ottenere il lettore video basato su HTML5 da usare per AEM. In Dynamic Media Classic, copiate il codice da incorporare del lettore video HTML5 predefinito e inseritelo nella pagina AEM.


## Componente video AEM {#aem-video-component}

Anche se per visualizzare i video di Dynamic Media Classic si consiglia di utilizzare il componente video Dynamic Media Classic, questa sezione descrive l&#39;utilizzo di video Dynamic Media Classic con [!UICONTROL Componente video di base] in AEM, per garantire la completezza.

### AEM confronto tra video e video classici di Dynamic Media {#aem-video-and-scene-video-comparison}

La tabella seguente fornisce un confronto ad alto livello delle capacità supportate tra il componente video di base di AEM e il componente video di Scene7:

|  | Video di base di AEM | Video Dynamic Media Classic |
|---|---|---|
| Approccio | Primo approccio HTML5. Flash viene utilizzato solo per il fallback non HTML5. | Flash è utilizzato sulla maggior parte dei computer desktop. HTML5 è usato per dispositivi mobili e tablet. |
| Consegna | Progressivo | Streaming adattivo |
| Tracciamento | Sì | Sì |
| Estensibilità | Sì | Sì (con Dynamic Media Classic viewer SDK) |
| Video mobile | Sì | Sì |

### Impostazione  {#setting-up}

#### Creazione di profili video {#creating-video-profiles}

Le diverse codifiche video vengono create in base ai predefiniti di codifica Dynamic Media Classic selezionati nella configurazione cloud di Dynamic Media Classic. Affinché il componente video di base possa utilizzarlo, è necessario creare un profilo video per ciascun predefinito di codifica Dynamic Media Classic selezionato. Il componente video potrà quindi selezionare le rappresentazioni DAM appropriate.

>[!NOTE]
>
>Per la pubblicazione, i nuovi profili video e le relative modifiche devono essere attivati.

1. In AEM, passa a **[!UICONTROL Strumenti]** e seleziona **[!UICONTROL Console di configurazione]**. Nella console di configurazione, andate a **[!UICONTROL Strumenti]** > **[!UICONTROL Risorse]** > **[!UICONTROL Profili video]** nella struttura di navigazione.
1. Create un nuovo profilo video Dynamic Media Classic. In **[!UICONTROL Nuovo...]**, selezionare **[!UICONTROL Crea pagina]**, quindi selezionare il modello di profilo video classico di Dynamic Media. Assegna un nome alla nuova pagina del profilo video e fai clic su **[!UICONTROL Crea]**.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Modifica il nuovo profilo video. Seleziona prima la configurazione cloud. Quindi seleziona lo stesso predefinito di codifica selezionato nella configurazione cloud.

   ![chlimage_1-134](assets/chlimage_1-134.png)

   | Proprietà | Descrizione |
   |---|---|
   | Configurazione cloud Dynamic Media Classic (Scene7) | Configurazione cloud da utilizzare per i predefiniti di codifica. |
   | Predefinito di codifica Dynamic Media Classic (Scene7) | Il predefinito di codifica con cui mappare il profilo video. |
   | Tipo video HTML5 | Questa proprietà consente di impostare il valore della proprietà type dell’elemento sorgente video HTML5. Queste informazioni non vengono fornite dai predefiniti di codifica Dynamic Media Classic, ma sono necessarie per il corretto rendering dei video mediante l’elemento video HTML5. Viene fornito un elenco dei formati più comuni, che può tuttavia essere sovrascritto per altri formati. |

   Ripeti questo passaggio per tutti i predefiniti di codifica selezionati nella configurazione cloud da usare nel componente video.

#### Configurazione della progettazione  {#configuring-design}

Il componente video di base deve sapere quali profili video utilizzare per creare l’elenco di sorgenti video. È necessario aprire la finestra di dialogo di progettazione dei componenti video e configurare la progettazione dei componenti per l’uso dei nuovi profili video.

>[!NOTE]
>
>Se utilizzi il componente video di base su una pagina mobile, potrebbe essere necessario ripetere questi passaggi nella progettazione della pagina mobile.

>[!NOTE]
>
>Le modifiche apportate alla progettazione richiedono l’attivazione della progettazione per avere effetto al momento della pubblicazione.

1. Apri la finestra di dialogo di progettazione del componente video di base e passa alla scheda **[!UICONTROL Profili]**. Quindi eliminate i profili predefiniti e aggiungete i nuovi profili video Dynamic Media Classic. L&#39;ordine dell&#39;elenco dei profili nella finestra di dialogo della progettazione definisce anche l&#39;ordine dell&#39;elemento delle sorgenti video durante il rendering.
1. Per i browser che non supportano HTML5, il componente video consente di configurare una versione Flash di fallback. Apri la finestra di dialogo di progettazione dei componenti video e passa alla scheda **[!UICONTROL Flash]**. Configura le impostazioni del lettore Flash e assegna un profilo di fallback per il lettore Flash.

#### Elenco di controllo  {#checklist}

1. Create una configurazione cloud Dynamic Media Classic (Scene7). Assicurati che i predefiniti di codifica video siano impostati e che il modulo di importazione sia in esecuzione.
1. Create un profilo video Dynamic Media Classic per ciascun predefinito di codifica video selezionato nella configurazione cloud.
1. I profili video devono essere attivati.
1. Configura la struttura del componente video di base sulla pagina.
1. Dopo aver apportato le modifiche, attiva la progettazione.

