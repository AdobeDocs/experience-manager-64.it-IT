---
title: Video
description: Scopri la gestione centralizzata delle risorse video in cui puoi caricare video per Experience Manager Assets per la codifica automatica in Dynamic Media Classic. Puoi anche accedere ai video Dynamic Media Classic direttamente da Experience Manager Assets. L'integrazione video di Dynamic Media Classic estende la portata dei video ottimizzati a tutti gli schermi con rilevamento automatico della larghezza di banda e dispositivo automatico.
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
exl-id: 081e7db0-95cc-4260-8f08-318cd7d9d5b4
feature: Video
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 2%

---

# Video {#video}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le risorse forniscono una gestione centralizzata delle risorse video che consente di caricare i video direttamente in Assets per la codifica automatica in Dynamic Media Classic. Puoi anche accedere ai video Dynamic Media Classic direttamente da Assets per la creazione delle pagine.

L&#39;integrazione video Dynamic Media Classic estende la portata dei video ottimizzati a tutti gli schermi (rilevamento automatico della periferica e della larghezza di banda).

La **[!UICONTROL Video Scene7]** component esegue automaticamente il rilevamento del dispositivo e della larghezza di banda per riprodurre il formato e la qualità video appropriati su desktop, tablet e dispositivi mobili.

È possibile includere set di video adattivi anziché solo risorse video singole. Un set video adattivo è un contenitore per tutte le rappresentazioni video necessarie per riprodurre video in modo trasparente su più schermi. Un Adaptive Video Set raggruppa le versioni dello stesso video codificate con diversi bit rate e formati. Ad esempio, 400 kbps, 800 kbps e 1000 kbps. Utilizza un set video adattivo, insieme al componente video S7, per lo streaming video adattivo su più tipi di schermo. Ad esempio, dispositivi mobili desktop, iOS, Android, BlackBerry e Windows.

Vedi [Documentazione di Dynamic Media Classic sui set video adattivi per ulteriori informazioni](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia).

## FFMPEG e Dynamic Media Classic {#about-ffmpeg-and-scene}

Il processo di codifica video predefinito si basa sull’utilizzo dell’integrazione basata su FFMPEG con i profili video. Pertanto, il flusso di lavoro di acquisizione DAM predefinito contiene i due passaggi seguenti del flusso di lavoro basato su ffmpeg:

* Miniature FFMPEG
* Codifica FFMPEG

L’abilitazione e la configurazione dell’integrazione Dynamic Media Classic non rimuovono o disattivano automaticamente questi due passaggi del flusso di lavoro dal flusso di lavoro di acquisizione DAM predefinito. Se utilizzi già la codifica video basata su FFMPEG in Experience Manager, è probabile che FFMPEG sia installato negli ambienti di authoring. In questo caso, un nuovo video acquisito tramite DAM viene codificato due volte: una volta dall&#39;encoder FFMPEG e una dall&#39;integrazione Dynamic Media Classic.

Se hai configurato la codifica video basata su FFMPEG in AEM e FFMPEG, puoi rimuovere i due flussi di lavoro FFMPEG dai flussi di lavoro di acquisizione DAM.

## Formati supportati {#supported-formats}

Per il componente Video di Scene7 sono supportati i seguenti formati:

* F4V H.264
* MP4 H.264

## Decidere dove caricare il video {#deciding-where-to-upload-your-video}

La decisione su dove caricare le risorse video dipende dai seguenti elementi:

* È necessario un flusso di lavoro per la risorsa video?
* È necessario il controllo delle versioni per la risorsa video?

Se la risposta è &quot;sì&quot; a una di queste domande o a entrambe, carica il video direttamente in Adobe DAM. Se la risposta è &quot;no&quot; a entrambe le domande, carica il video direttamente in Dynamic Media Classic. Il flusso di lavoro per ogni scenario è descritto nelle sezioni successive.

### Se carichi il video direttamente in Adobe DAM {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Se hai bisogno di un flusso di lavoro o di un controllo delle versioni per le tue risorse, carica prima in Adobe DAM . Di seguito è riportato il flusso di lavoro consigliato:

1. Carica la risorsa video in Adobe DAM e codifica e pubblica automaticamente in Dynamic Media Classic.
1. Ad Experience Manager, puoi accedere alle risorse video in WCM nel **[!UICONTROL Filmati]** scheda di Content Finder.
1. Autore con **[!UICONTROL Video Scene7]** o **[!UICONTROL Video di base]** componente.

### Se carichi il video in Scene7 {#if-you-are-uploading-your-video-to-scene}

Se non hai bisogno di un flusso di lavoro o di un controllo delle versioni per le tue risorse, carica le risorse in Scene7. Di seguito è riportato il flusso di lavoro consigliato:

1. In Dynamic Media Classic, [configurare un caricamento e una codifica FTP pianificati su Scene7 (sistema automatizzato)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading).
1. Ad Experience Manager, puoi accedere alle risorse video in WCM nel **[!UICONTROL Scene7]** scheda di Content Finder.
1. Crea con **[!UICONTROL Video Scene7]** componente.

## Configurazione dell’integrazione con video Scene7 {#configuring-integration-with-scene-video}

Per configurare i predefiniti universali:

1. In **[!UICONTROL Cloud Services]**, vai alla **[!UICONTROL Scene7]** configurazione e fai clic su **[!UICONTROL Modifica]**.
1. Seleziona la **[!UICONTROL Video]** scheda .

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >La **[!UICONTROL Video]** non viene visualizzata se la pagina non dispone di una configurazione cloud.

1. Seleziona il profilo di codifica del video adattivo, un profilo di codifica video singolo predefinito o un profilo di codifica video personalizzato.

   >[!NOTE]
   >
   >Per ulteriori informazioni sul significato dei predefiniti video, consulta la [Documentazione di Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe consiglia di selezionare entrambi i set di video adattivi al momento della configurazione dei predefiniti universali o di selezionare il **[!UICONTROL Codifica video adattiva]** opzione .

1. I profili di codifica selezionati vengono applicati automaticamente a tutti i video caricati nella cartella di destinazione CQ DAM impostata per questa configurazione cloud Scene7. Puoi impostare più configurazioni cloud di Scene7 con diverse cartelle di destinazione per applicare profili di codifica diversi in base alle esigenze.

## Aggiornamento del visualizzatore e dei predefiniti di codifica {#updating-viewer-and-encoding-presets}

È necessario aggiornare il visualizzatore e i predefiniti di codifica video in Experience Manager se i predefiniti sono stati aggiornati in Scene7. In questi casi, accedi alla configurazione Scene7 nella configurazione cloud e fai clic su **[!UICONTROL Aggiornare il visualizzatore e i predefiniti di codifica]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Caricamento del video principale in Scene7 da DAM Adobe {#uploading-your-master-video}

1. Passa alla cartella di destinazione CQ DAM in cui hai configurato la configurazione cloud con i profili di codifica Scene7.
1. Fai clic su **[!UICONTROL Carica]** per caricare il video principale. Il caricamento e la codifica dei video vengono completati al completamento del flusso di lavoro Risorsa di aggiornamento DAM e **[!UICONTROL Pubblicare su Scene7]** ha un segno di spunta.

   >[!NOTE]
   >
   >La generazione delle miniature video richiede del tempo.

   Quando si trascina il video principale DAM sul componente video, è possibile accedere *tutto* rappresentazioni proxy codificate Scene7 per la distribuzione.

## Componente video di base e componente video di Scene7 {#foundation-video-component-versus-scene-video-component}

Quando utilizzi Experience Manager, puoi accedere sia al componente Video disponibile in Sites che al componente video Scene7. Questi componenti non sono intercambiabili.

Il componente video Scene7 funziona solo per i video Scene7. Il componente foundation funziona con i video archiviati da Experience Manager (utilizzando ffmpeg) e i video Scene7.

La matrice seguente spiega quando utilizzare il componente:

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>Preconfigurato, il componente video S7 utilizza il profilo video universale. Tuttavia, è possibile ottenere in Experience Manager il lettore video basato su HTML5. È sufficiente copiare il codice di incorporamento del lettore video HTML5 preconfigurato e inserirlo nella pagina di Experience Manager.

## Componente video Experience Manager {#aem-video-component}

Anche se si consiglia di utilizzare il componente video Scene7 per visualizzare i video Scene7, per motivi di completezza utilizza i video Scene7 con il componente video di base.

### Confronto tra video e video Scene7 di Experience Manager {#aem-video-and-scene-video-comparison}

La tabella seguente fornisce un confronto ad alto livello delle funzionalità supportate tra il componente Video di base di Experience Manager e il componente Video di Scene7:

|  | Video Experience Manager Foundation | Video Scene7 |
|---|---|---|
| Approccio | primo approccio di HTML5. Il Flash viene utilizzato solo per il fallback non di HTML5. | Flash sulla maggior parte dei desktop. HTML5 viene utilizzato per dispositivi mobili e tablet. |
| Distribuzione | Progressivo | Streaming adattivo |
| Tracking | Sì | Sì |
| Estensibilità | Sì | Sì (con [Documentazione API dell’SDK per visualizzatori HTML5](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) |
| Video mobile | Sì | Sì |

### Impostazione {#setting-up}

#### Creazione di profili video {#creating-video-profiles}

Le varie codifiche video vengono create in base ai predefiniti di codifica Scene7 selezionati nella configurazione cloud di Scene7. Affinché il componente Video di base possa utilizzarli, è necessario creare un profilo video per ogni predefinito di codifica Scene7 selezionato. Questo metodo consente al componente video di selezionare di conseguenza le rappresentazioni DAM.

>[!NOTE]
>
>Per pubblicare, è necessario attivare i nuovi profili video e le relative modifiche.

1. Ad Experience Manager, tocca **[!UICONTROL Strumenti] > [!UICONTROL Console di configurazione]**.
1. Da **[!UICONTROL Console di configurazione]** naviga a **[!UICONTROL Strumenti > DAM > Profili video]** nella struttura di navigazione.
1. Crea un profilo video Scene7. In **[!UICONTROL Nuovo...]** elenco a discesa, seleziona **[!UICONTROL Crea pagina]** quindi seleziona il modello Profilo video Scene7 . Assegna un nome alla nuova pagina del profilo video e fai clic su **[!UICONTROL Crea]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Modifica il nuovo profilo video. Seleziona prima la configurazione cloud. Quindi seleziona lo stesso predefinito di codifica selezionato nella configurazione cloud.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Proprietà | Descrizione |
   |---|---|
   | Configurazione cloud Scene7 | Configurazione cloud da utilizzare per i predefiniti di codifica. |
   | Predefinito di codifica Scene7 | Predefinito di codifica con cui mappare il profilo video. |
   | Tipo video HTML5 | Questa proprietà consente di impostare il valore della proprietà type dell&#39;elemento video source HTML5. Queste informazioni non vengono fornite dai predefiniti di codifica S7, ma sono necessarie per il corretto rendering dei video con l’elemento video HTML5. Viene fornito un elenco dei formati comuni, ma può essere sovrascritto per altri formati. |

   Ripeti questo passaggio per tutti i predefiniti di codifica selezionati nella configurazione cloud che desideri utilizzare nel componente video.

#### Configurazione della progettazione {#configuring-design}

La **[!UICONTROL Video di base]** Il componente deve sapere quali profili video utilizzare per creare l’elenco delle sorgenti video. Apri la finestra di dialogo di progettazione dei componenti video e configura la progettazione dei componenti per l’utilizzo dei nuovi profili video.

>[!NOTE]
>
>Se utilizzi **[!UICONTROL Video di base]** in una pagina mobile, ripeti questi passaggi nella progettazione della pagina mobile.

>[!NOTE]
>
>Le modifiche apportate alla progettazione richiedono l’attivazione della progettazione in modo che possano avere effetto al momento della pubblicazione.

1. Apri **[!UICONTROL Video di base]** finestra di dialogo di progettazione del componente e passare alla **[!UICONTROL Profili]** scheda . Quindi elimina i profili predefiniti e aggiungi i nuovi profili video S7. L’ordine dell’elenco dei profili nella finestra di dialogo di progettazione definisce l’ordine dell’elemento origini video durante il rendering.
1. Per i browser che non supportano HTML5, il componente video ti consente di configurare un fallback di Flash. Apri la finestra di dialogo di progettazione dei componenti video e passa a **[!UICONTROL Flash]** scheda . Configura le impostazioni del Flash Player e assegna un profilo di fallback al Flash Player.

#### Elenco di controllo {#checklist}

1. Crea una configurazione cloud S7. Assicurati che i predefiniti di codifica video siano impostati e che l’importazione sia in esecuzione.
1. Crea un profilo video S7 per ogni predefinito di codifica video selezionato nella configurazione cloud.
1. I profili video devono essere attivati.
1. Configura la progettazione del **[!UICONTROL Video di base]** nella pagina.
1. Dopo aver apportato le modifiche di progettazione, attiva la progettazione.
