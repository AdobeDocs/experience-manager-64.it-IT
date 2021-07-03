---
title: Video
description: Scopri la gestione centralizzata delle risorse video in cui puoi caricare video per Experience Manager Assets per la codifica automatica in Dynamic Media Classic. Puoi anche accedere ai video di Dynamic Media Classic direttamente da Risorse Experience Manager. L’integrazione video di Dynamic Media Classic estende la portata dei video ottimizzati a tutti gli schermi con rilevamento automatico della larghezza di banda e dispositivo.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
exl-id: 081e7db0-95cc-4260-8f08-318cd7d9d5b4
feature: Video
role: User
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 29%

---

# Video {#video}

Le risorse forniscono una gestione centralizzata delle risorse video che consente di caricare i video direttamente in Assets per la codifica automatica in Dynamic Media Classic. Puoi anche accedere ai video di Dynamic Media Classic direttamente da Assets per la creazione delle pagine.

L’integrazione video di Dynamic Media Classic estende la portata dei video ottimizzati a tutti gli schermi (rilevamento automatico della periferica e della larghezza di banda).

Il componente **[!UICONTROL Video Scene7]** esegue automaticamente il rilevamento del dispositivo e della larghezza di banda per riprodurre il formato e la qualità video appropriati su desktop, tablet e dispositivi mobili.

È possibile includere set di video adattivi anziché solo risorse video singole. Un set video adattivo è un contenitore per tutte le rappresentazioni video necessarie per riprodurre video in modo trasparente su più schermi. Un Adaptive Video Set raggruppa le versioni dello stesso video codificate con diversi bit rate e formati. Ad esempio, 400 kbps, 800 kbps e 1000 kbps. Utilizza un set video adattivo, insieme al componente video S7, per lo streaming video adattivo su più tipi di schermo. Ad esempio, dispositivi mobili desktop, iOS, Android, BlackBerry e Windows.

Per ulteriori informazioni, consulta la [documentazione di Dynamic Media Classic sui set di video adattivi.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia)

## FFMPEG e Dynamic Media Classic {#about-ffmpeg-and-scene}

Il processo di codifica video predefinito si basa sull’utilizzo dell’integrazione con i profili video basata su FFMPEG. Pertanto, il flusso di lavoro di acquisizione DAM predefinito contiene i due passaggi seguenti del flusso di lavoro basato su ffmpeg:

* Miniature FFMPEG
* Codifica FFMPEG

L’abilitazione e la configurazione dell’integrazione Dynamic Media Classic non rimuove o disattiva automaticamente questi due passaggi del flusso di lavoro dal flusso di lavoro di acquisizione DAM predefinito. Se utilizzi già la codifica video basata su FFMPEG in Experience Manager, è probabile che FFMPEG sia installato negli ambienti di authoring. In questo caso, un nuovo video acquisito tramite DAM viene codificato due volte: una volta dall&#39;encoder FFMPEG e una dall&#39;integrazione Dynamic Media Classic.

Se hai configurato la codifica video basata su FFMPEG in AEM e FFMPEG, puoi rimuovere i due flussi di lavoro FFMPEG dai flussi di lavoro di acquisizione DAM.

## Formati supportati {#supported-formats}

Il componente video Scene7 supporta i seguenti formati:

* F4V H.264
* MP4 H.264

## Decidere dove caricare il video {#deciding-where-to-upload-your-video}

La decisione su dove caricare le risorse video dipende da quanto segue:

* Hai bisogno di un flusso di lavoro per la risorsa video?
* Hai bisogno della funzione di controllo delle versioni per la risorsa video?

Se la risposta è “sì” ad almeno una di queste domande, carica il video direttamente in Adobe DAM. Se la risposta è &quot;no&quot; a entrambe le domande, carica il video direttamente in Dynamic Media Classic. Il flusso di lavoro per ogni scenario è descritto nelle sezioni successive.

### Se carichi il video direttamente in Adobe DAM {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Se hai bisogno di un flusso di lavoro o di un controllo delle versioni per le tue risorse, carica prima in Adobe DAM . Di seguito è riportato il flusso di lavoro consigliato:

1. Carica la risorsa video in Adobe DAM e codifica e pubblica automaticamente in Dynamic Media Classic.
1. Ad Experience Manager, accedi alle risorse video in WCM nella scheda **[!UICONTROL Filmati]** di Content Finder.
1. Esegui l’authoring con il componente **[!UICONTROL Video Scene7]** o **[!UICONTROL Video di base]**.

### Se stai caricando il video in Scene7 {#if-you-are-uploading-your-video-to-scene}

Se non hai bisogno di un flusso di lavoro o di un controllo delle versioni per le tue risorse, carica le risorse in Scene7. Di seguito è riportato il flusso di lavoro consigliato:

1. In Dynamic Media Classic, [configura un caricamento e una codifica FTP pianificati in Scene7 (sistema automatizzato)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading).
1. Ad Experience Manager, accedi alle risorse video in WCM nella scheda **[!UICONTROL Scene7]** di Content Finder.
1. Crea con il componente **[!UICONTROL Video Scene7]** .

## Configurazione dell’integrazione con video Scene7 {#configuring-integration-with-scene-video}

Per configurare i predefiniti universali:

1. In **[!UICONTROL Servizi cloud]**, accedi alla tua configurazione di **[!UICONTROL Scene7]** e fai clic su **[!UICONTROL Modifica]**.
1. Seleziona la scheda **[!UICONTROL Video]**.

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >La scheda **[!UICONTROL Video]** non viene visualizzata se la pagina non ha una configurazione cloud.

1. Seleziona il profilo di codifica video adattivo, uno dei profili di codifica per video singolo preconfigurati oppure un profilo di codifica video personalizzato.

   >[!NOTE]
   >
   >Per ulteriori informazioni sul significato dei predefiniti video, consulta la [documentazione Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe consiglia di selezionare entrambi i set video adattivi per la configurazione dei predefiniti universali o di selezionare l’opzione **[!UICONTROL Codifica video adattiva]**.

1. I profili di codifica selezionati vengono applicati automaticamente a tutti i video caricati nella cartella di destinazione CQ DAM impostata per questa configurazione cloud di Scene7. Puoi impostare più configurazioni cloud di Scene7 con diverse cartelle di destinazione, per applicare profili di codifica diversi a seconda delle esigenze.

## Aggiornamento del visualizzatore e dei predefiniti di codifica {#updating-viewer-and-encoding-presets}

È necessario aggiornare il visualizzatore e i predefiniti di codifica video in Experience Manager se i predefiniti sono stati aggiornati in Scene7. In questi casi, accedi alla configurazione Scene7 nella configurazione cloud e fai clic su **[!UICONTROL Aggiorna il visualizzatore e i predefiniti di codifica]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Caricamento del video principale in Scene7 da DAM Adobe {#uploading-your-master-video}

1. Individua la cartella di destinazione CQ DAM in cui hai impostato la configurazione cloud con i profili di codifica di Scene7.
1. Fai su **[!UICONTROL Carica]** per caricare il video principale. Il caricamento e la codifica dei video viene completato al termine del flusso di lavoro Risorsa di aggiornamento DAM e **[!UICONTROL Pubblica in Scene7]** ha un segno di spunta.

   >[!NOTE]
   >
   >La generazione delle miniature video richiede del tempo.

   Trascinando il video principale DAM sul componente video, si accede a *all* le rappresentazioni proxy codificate di Scene7 per la distribuzione.

## Componente video di base e componente video di Scene7 {#foundation-video-component-versus-scene-video-component}

Quando utilizzi Experience Manager, puoi accedere sia al componente Video disponibile in Sites che al componente video Scene7. Questi componenti non sono intercambiabili.

Il componente video di Scene7 funziona solo per i video di Scene7. Il componente foundation funziona con i video archiviati da Experience Manager (utilizzando ffmpeg) e i video Scene7.

La matrice seguente spiega quando utilizzare il componente:

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>Preconfigurato, il componente video S7 utilizza il profilo video universale. Tuttavia, puoi ottenere in Experience Manager il lettore video basato su HTML5. È sufficiente copiare il codice di incorporamento del lettore video HTML5 predefinito e inserirlo nella pagina di Experience Manager.

## Componente video Experience Manager {#aem-video-component}

Anche se si consiglia di utilizzare il componente video Scene7 per visualizzare i video Scene7, per motivi di completezza utilizza i video Scene7 con il componente video di base.

### Confronto tra video e video Scene7 di Experience Manager {#aem-video-and-scene-video-comparison}

La tabella seguente fornisce un confronto ad alto livello delle funzionalità supportate tra il componente Video di base di Experience Manager e il componente Video di Scene7:

|  | Video Experience Manager Foundation | Video di Scene7 |
|---|---|---|
| Approccio | Primo approccio HTML5. Flash viene utilizzato solo per il fallback non HTML5. | Flash è utilizzato sulla maggior parte dei computer desktop. HTML5 è usato per dispositivi mobili e tablet. |
| Consegna | Progressivo | Streaming adattivo |
| Tracciamento | Sì | Sì |
| Estensibilità | Sì | Sì (con [Documentazione API SDK visualizzatore HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) |
| Video mobile | Sì | Sì |

### Impostazione {#setting-up}

#### Creazione di profili video {#creating-video-profiles}

Le varie codifiche video vengono create in base ai predefiniti di codifica Scene7 selezionati nella configurazione cloud di Scene7. Affinché il componente Video di base possa utilizzarli, è necessario creare un profilo video per ogni predefinito di codifica Scene7 selezionato. Questo metodo consente al componente video di selezionare di conseguenza le rappresentazioni DAM.

>[!NOTE]
>
>Per la pubblicazione, i nuovi profili video e le relative modifiche devono essere attivati.

1. Ad Experience Manager, tocca **[!UICONTROL Strumenti] > [!UICONTROL Console di configurazione]**.
1. Dalla **[!UICONTROL Console di configurazione]** passa a **[!UICONTROL Strumenti > DAM > Profili video]** nella struttura di navigazione.
1. Crea un profilo video Scene7. In **[!UICONTROL Nuovo...Dall’elenco a discesa]**, seleziona **[!UICONTROL Crea pagina]**, quindi seleziona il modello di profilo video Scene7. Assegna un nome alla nuova pagina del profilo video e fai clic su **[!UICONTROL Crea]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Modifica il nuovo profilo video. Seleziona prima la configurazione cloud. Quindi seleziona lo stesso predefinito di codifica selezionato nella configurazione cloud.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Proprietà | Descrizione |
   |---|---|
   | Configurazione cloud Scene7 | Configurazione cloud da utilizzare per i predefiniti di codifica. |
   | Predefinito di codifica Scene7 | Predefinito di codifica con cui mappare il profilo video. |
   | Tipo video HTML5 | Questa proprietà consente di impostare il valore della proprietà type dell&#39;elemento di origine video HTML5. Queste informazioni non vengono fornite dai predefiniti di codifica S7, ma sono necessarie per la corretta esecuzione del rendering dei video mediante l’elemento video HTML5. Viene fornito un elenco dei formati più comuni, che può tuttavia essere sovrascritto per altri formati. |

   Ripeti questo passaggio per tutti i predefiniti di codifica selezionati nella configurazione cloud da usare nel componente video.

#### Configurazione della progettazione {#configuring-design}

Il componente **[!UICONTROL Video di base]** deve sapere quali profili video utilizzare per creare l’elenco delle sorgenti video. Apri la finestra di dialogo di progettazione dei componenti video e configura la progettazione dei componenti per l’utilizzo dei nuovi profili video.

>[!NOTE]
>
>Se utilizzi il componente **[!UICONTROL Video di base]** su una pagina mobile, ripeti questi passaggi nella progettazione della pagina mobile.

>[!NOTE]
>
>Le modifiche apportate alla progettazione richiedono l’attivazione della progettazione in modo che possano avere effetto al momento della pubblicazione.

1. Apri la finestra di dialogo di progettazione del componente **[!UICONTROL Video di base]** e passa alla scheda **[!UICONTROL Profili]** . Quindi elimina i profili predefiniti e aggiungi i nuovi profili video S7. L’ordine dell’elenco dei profili nella finestra di dialogo di progettazione definisce l’ordine dell’elemento origini video durante il rendering.
1. Per i browser che non supportano HTML5, il componente video ti consente di configurare un fallback di Flash. Apri la finestra di dialogo di progettazione dei componenti video e passa alla scheda **[!UICONTROL Flash]** . Configura le impostazioni del Flash Player e assegna un profilo di fallback al Flash Player.

#### Elenco di controllo {#checklist}

1. Crea una configurazione cloud S7. Assicurati che i predefiniti di codifica video siano impostati e che l’importazione sia in esecuzione.
1. Crea un profilo video S7 per ogni predefinito di codifica video selezionato nella configurazione cloud.
1. I profili video devono essere attivati.
1. Configura la progettazione del componente **[!UICONTROL Video di base]** sulla pagina.
1. Dopo aver apportato le modifiche, attiva la progettazione.
