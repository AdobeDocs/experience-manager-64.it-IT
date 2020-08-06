---
title: Profili video per elementi multimediali dinamici
seo-title: Profili video per elementi multimediali dinamici
description: 'Gli elementi multimediali dinamici dispongono già di un profilo di codifica video adattiva predefinito. Le impostazioni incluse in questo profilo out-of-the-box sono ottimizzate per offrire ai clienti la migliore esperienza di visualizzazione possibile. '
seo-description: 'Gli elementi multimediali dinamici dispongono già di un profilo di codifica video adattiva predefinito. Le impostazioni incluse in questo profilo out-of-the-box sono ottimizzate per offrire ai clienti la migliore esperienza di visualizzazione possibile. '
uuid: cfb498f8-44a0-4d94-99b0-fed7c27f575b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: b893f366-279a-4872-9413-77626d3387ea
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '3100'
ht-degree: 18%

---


# Dynamic Media video profiles {#video-profiles}

Gli elementi multimediali dinamici dispongono già di un profilo di codifica video adattiva predefinito. Le impostazioni incluse in questo profilo out-of-the-box sono ottimizzate per offrire ai clienti la migliore esperienza di visualizzazione possibile. Quando codificate i video principali utilizzando il profilo di codifica per video adattivi, durante la riproduzione il lettore video regola automaticamente la qualità del flusso video in base alla velocità di connessione Internet dei clienti. È noto come streaming adattivo.

Di seguito sono riportati altri fattori che determinano la qualità dei video:

* **Risoluzione del video principale caricato**

   Se il video MP4 veniva registrato a una risoluzione inferiore, ad esempio 240p o 360p, non poteva essere trasmesso in streaming in alta definizione.

* **Dimensioni del lettore video**

   Per impostazione predefinita, la **[!UICONTROL larghezza]** nel profilo Codifica video adattiva è impostata su **[!UICONTROL Auto]**. Anche in questo caso, durante la riproduzione, viene utilizzata la qualità migliore in base alle dimensioni del lettore.

Consultate anche [Best practice per la codifica](video.md#best-practices-for-encoding-videos)video.

>[!NOTE]
>
>Per generare i metadati di un video e le miniature delle immagini video associate, il video stesso deve seguire il processo di codifica di Dynamic Media. Se hai attivato gli elementi multimediali dinamici e hai impostato Cloud Services per i video, il flusso di lavoro **[!UICONTROL Codifica video elementi multimediali dinamici]** di AEM ti consente di eseguire la codifica dei video. Questo flusso di lavoro acquisisce la cronologia del processo del flusso di lavoro e le informazioni di errore.
>
>Consulta la sezione [Monitoraggio della codifica video e stato della pubblicazione su YouTube](video.md#monitoring-video-encoding-and-youtube-publishing-progress). If you have enabled Dynamic Media and set up video cloud services, the **[!UICONTROL Dynamic Media Encode Video]** workflow automatically takes effect when you upload a video. Se non utilizzi gli elementi multimediali dinamici, viene applicato il flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.
>
>I metadati sono utili per la ricerca delle risorse. Le miniature sono immagini video statiche generate durante la codifica. Sono richiesti dal sistema di AEM e utilizzati nell’interfaccia utente per identificare visivamente i video nelle visualizzazioni **[!UICONTROL Schede]**, Risultati **** ricerca e Elenco **** risorse. Potete visualizzare le miniature generate toccando l&#39;icona **[!UICONTROL Rappresentazioni]** (la palette del pittore) di un video codificato.

Una volta creato il profilo video, questo viene applicato a una cartella o più cartelle. See [Applying a video profile to folders.](#applying-a-video-profile-to-folders)

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione](config-dms7.md#configuring-asset-processing)delle risorse.

## Predefiniti codifica video adattiva {#adaptive-video-encoding-presets}

Nella tabella seguente sono riportati i profili di codifica best practice per lo streaming di video adattivi per dispositivi mobili, tablet e computer desktop. Potete usare questi predefiniti per qualsiasi video con proporzioni qualsiasi.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Codec formato video</strong></td> 
   <td><strong>Dimensioni video - Larghezza (px)</strong></td> 
   <td><strong>Dimensioni video - Altezza (px)</strong></td> 
   <td><strong>Mantieni proporzioni?</strong></td> 
   <td><strong>Bitrate video (Kbps)</strong></td> 
   <td><strong>Frame Rate Video (Fps)</strong></td> 
   <td><strong>Codec audio</strong></td> 
   <td><strong>Bitrate audio (Kbps)</strong></td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>360</td> 
   <td>Sì</td> 
   <td>730</td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>540</td> 
   <td>Sì</td> 
   <td>2000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>720<br /> </td> 
   <td>Sì</td> 
   <td>3000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
 </tbody> 
</table>

## Creazione di un profilo di codifica video per contenuti multimediali dinamici per lo streaming adattivo {#creating-a-video-encoding-profile-for-adaptive-streaming}

Gli elementi multimediali dinamici sono già dotati di un profilo di codifica video adattiva predefinito, un gruppo di impostazioni di caricamento video per MP4 H.264, ottimizzato per garantire una migliore esperienza di visualizzazione. Potete usare questo profilo quando caricate i video.

Tuttavia, se questo profilo predefinito non soddisfa le esigenze, potete scegliere di creare un profilo di codifica video adattivo personalizzato. Quando utilizzate l’impostazione **[!UICONTROL Codifica per lo streaming]** adattivo,*come procedura* consigliata, tutti i predefiniti di codifica aggiunti al profilo vengono convalidati per garantire che tutti i video abbiano le stesse proporzioni. Inoltre, i video codificati vengono trattati come un set di bitrate multipli per lo streaming.

Quando create il profilo di codifica video, noterete che la maggior parte delle opzioni di codifica sono precompilate con le impostazioni predefinite consigliate per facilitare l’utente. Tuttavia, se selezionate un valore diverso da quello predefinito consigliato, tenete presente che potrebbe causare problemi di qualità video durante la riproduzione e altri problemi di prestazioni.

Pertanto, per tutti i predefiniti di codifica video MP4 H.264 presenti nel profilo, i seguenti valori vengono convalidati per garantire che siano identici tra i singoli predefiniti di codifica nel profilo, rendendo possibile lo streaming adattivo:

* Codec formato video - MP4 H.264 (.mp4)
* Codec audio
* Bitrate audio
* Mantieni proporzioni
* Codifica a due passate
* Bitrate costante
* Profilo H264
* Frequenza di campionamento audio

Se i valori non sono identici, potete continuare a creare il profilo così com&#39;è. Tuttavia, lo streaming adattivo non sarà possibile. Gli utenti possono invece utilizzare lo streaming a bitrate singolo. È consigliabile modificare le impostazioni di codifica in modo da utilizzare gli stessi valori per i singoli predefiniti di codifica presenti nel profilo. Tenete presente che l’editor del profilo video/predefinito deve applicare la parità delle impostazioni di codifica video adattiva se è abilitata la funzione **[!UICONTROL Codifica per lo streaming]** adattivo.

Consultate anche [Creazione di un profilo di codifica video per lo streaming](#creating-a-video-encoding-profile-for-progressive-streaming)progressivo.

Consultate anche [Best practice per la codifica](video.md#best-practices-for-encoding-videos)video.

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione](config-dms7.md#configuring-asset-processing)delle risorse.

Una volta creato il profilo video, questo viene applicato a una o più cartelle.

**Per creare un profilo di codifica video per contenuti multimediali dinamici per lo streaming** adattivo:

1. Tap or click the AEM logo and navigate to **[!UICONTROL Tools > Assets > Video Profiles]**.
1. Toccate **[!UICONTROL Crea]** per aggiungere un nuovo profilo video.

1. Immettete un nome e una descrizione per il profilo.
1. Accertatevi che **[!UICONTROL Encode for adaptive streaming]** sia selezionato (impostazione predefinita).
1. Tap **[!UICONTROL Add Video Encoding Preset]**.
1. Nella scheda **[!UICONTROL Base]** , impostate le opzioni video e audio.

   Toccate l’icona delle informazioni accanto a ciascuna opzione per ottenere descrizioni aggiuntive o impostazioni consigliate in base al codec del formato video selezionato.

1. Nella sezione Dimensione video, accertatevi che le proporzioni **[!UICONTROL Mantieni siano selezionate]** .
1. Impostate la risoluzione del fotogramma video in pixel. Usate il valore **[!UICONTROL Auto]** per ridimensionare automaticamente in base alle proporzioni sorgente (rapporto larghezza/altezza). Ad esempio, Auto x 480 o 640 x Auto.

   Effettua una delle operazioni seguenti:

   * In the **[!UICONTROL Width]** field, enter **[!UICONTROL auto]**. In the **[!UICONTROL Height]** field, enter a value in pixels.
   * Per visualizzare le dimensioni del video, toccate l’icona **[!UICONTROL Informazioni]** (i) a destra di **[!UICONTROL Altezza]** per aprire la pagina **[!UICONTROL Calcolatore]** dimensioni. Utilizzate **[!UICONTROL Calcolatore]** dimensioni per impostare le dimensioni video (rappresentate dalla casella blu) desiderate. Toccate **[!UICONTROL X]** nell&#39;angolo superiore destro al termine.

1. (Facoltativo) Toccate la scheda **[!UICONTROL Avanzate]** e verificate che la casella di controllo **[!UICONTROL Usa valori]** predefiniti sia selezionata (opzione consigliata). In alternativa, modificate le impostazioni audio e video avanzate.
1. In the upper-right corner of the page, tap **[!UICONTROL Save]** to save the preset.
1. Effettua una delle operazioni seguenti:

   * Ripetete i passaggi da 5 a 10 per creare altri predefiniti di codifica. Lo streaming di video adattivi richiede più di un predefinito video.
   * In the upper-right corner of the page, tap **[!UICONTROL Save]** again to save the profile.

## Monitoraggio dell’avanzamento di un processo di codifica {#monitoring-the-progress-of-an-encoding-job}

Viene visualizzato un indicatore di elaborazione (o una barra di avanzamento) che consente di monitorare visivamente l’avanzamento di un processo di codifica video.

Potete inoltre visualizzare il `error.log` file per monitorare l’avanzamento di un processo di codifica, verificare se la codifica è terminata o visualizzare eventuali errori di processo. L’ `error.log` elemento si trova nella `logs` cartella in cui è installata l’istanza di AEM.

## Creazione di un profilo di codifica video per contenuti multimediali dinamici per lo streaming progressivo {#creating-a-video-encoding-profile-for-progressive-streaming}

Se scegli di non utilizzare l’opzione **[!UICONTROL Codifica per lo streaming adattivo]**, tutti i predefiniti di codifica aggiunti al profilo vengono trattati come rappresentazioni video individuali per lo streaming a bitrate singolo o per la distribuzione progressiva di video. Inoltre, non esiste una convalida per garantire che tutte le rappresentazioni video abbiano le stesse proporzioni.

A seconda della modalità in esecuzione, i codec supportati sono:

* Modalità Dynamic Media-Scene7: H.264 (.mp4)
* Modalità Dynamic Media-Hybrid: H.264 (.mp4), WebM

Consultate anche [Creazione di un profilo di codifica video per lo streaming](#creating-a-video-encoding-profile-for-adaptive-streaming)adattivo.

Consultate anche [Best practice per la codifica](video.md#best-practices-for-encoding-videos)video.

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione](config-dms7.md#configuring-asset-processing)delle risorse.

Una volta creato il profilo video, questo viene applicato a una o più cartelle.

**Per creare un profilo di codifica video per contenuti multimediali dinamici per lo streaming progressivo:**

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Toccate **[!UICONTROL Crea]** per aggiungere un nuovo profilo video.
1. Immettete un nome e una descrizione per il profilo.
1. Deselezionate la casella di controllo **[!UICONTROL Codifica per streaming]** adattivo.
1. Tap **[!UICONTROL Add Video Encoding Preset]**.
1. Nella scheda **[!UICONTROL Base]** , impostate le opzioni video e audio.

   Tap the **[!UICONTROL Information]** icon next to each option for additional descriptions or recommended settings based on the selected video format codec.

1. (Facoltativo) Sotto l’intestazione Dimensione **** video, deselezionate **[!UICONTROL Mantieni proporzioni]**.
1. Nel campo **[!UICONTROL Larghezza]** , immettere **[!UICONTROL auto]**; a destra del campo **[!UICONTROL Altezza]** , toccate l&#39;icona **[!UICONTROL Informazioni]** . Use the **[!UICONTROL Size Calculator]** page to further set the video dimension (blue box) how you want. Toccate **[!UICONTROL X]** al termine.
1. (Facoltativo) Effettuate una delle seguenti operazioni:

   * Toccate la scheda **[!UICONTROL Avanzate]** e verificate che la casella di controllo **[!UICONTROL Usa valori]** predefiniti sia selezionata (opzione consigliata).
   * Deselezionate la casella di controllo **[!UICONTROL Usa valori]** predefiniti e specificate le impostazioni video e audio desiderate.

      Tap the **[!UICONTROL Information]** icon next to each option for additional descriptions or recommended settings based on the selected video format codec.

1. In the upper-right corner of the page, tap **[!UICONTROL Save]** to save the preset.
1. Effettua una delle operazioni seguenti:

   * Ripetete i passaggi da 5 a 10 per creare altri predefiniti di codifica.
   * Nell’angolo superiore destro della pagina, tocca **[!UICONTROL Salva]** per salvare il profilo.

## Utilizzo di parametri di codifica video personalizzati {#using-custom-added-video-encoding-parameters}

Potete modificare un profilo di codifica video esistente per sfruttare i parametri di codifica video avanzati che non sono disponibili nell’interfaccia utente al momento della creazione o della modifica di un profilo video in AEM. Potete aggiungere uno o più parametri avanzati (ad esempio **[!UICONTROL minBitrate]** e **[!UICONTROL maxBitrate]**) al profilo esistente.

**Per utilizzare parametri** di codifica video personalizzati:

1. Tocca il logo AEM, quindi seleziona **[!UICONTROL Strumenti > Generale > CRXDE Lite]**.
1. Dalla pagina **[!UICONTROL CRXDE Lite]** , nel pannello **[!UICONTROL Esplora risorse]** a sinistra, individuate quanto segue:

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. In the panel on the lower-right side of the page, from the **[!UICONTROL Properties]** tab, specify the **[!UICONTROL Name]**, **[!UICONTROL Type]**, and **[!UICONTROL Value]** of the parameter you want to use.

   Sono disponibili i seguenti parametri avanzati:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Nome</strong></td> 
    <td><strong>Descrizione</strong><br /> </td> 
    <td><strong>Tipo</strong><br /> </td> 
    <td><strong>Valore</strong></td> 
    </tr> 
    <tr> 
    <td><code>h264Level</code></td> 
    <td>Livello H.264 da usare per la codifica. In genere questo viene determinato automaticamente in base alle impostazioni di codifica utilizzate.</td> 
    <td><code>String</code></td> 
    <td><p>10 * livello h264</p> <p>Ad esempio, 3.0 = 30, 1.3 = 13)</p> <p>Nessun valore predefinito.</p> </td> 
    </tr> 
    <tr> 
    <td><code>keyframe</code></td> 
    <td>Il numero target di fotogrammi tra i fotogrammi chiave. Calcolate questo valore per generare un fotogramma chiave ogni 2-10 secondi. Ad esempio, a 30 fotogrammi al secondo, l’intervallo del fotogramma chiave dovrebbe essere compreso tra 60 e 300.<br /> <br /> Intervalli di fotogrammi chiave più bassi migliorano la ricerca del flusso e il comportamento di commutazione del flusso per le codifiche video adattive e possono anche migliorare la qualità dei video con molto movimento. Tuttavia, poiché i fotogrammi chiave aumentano le dimensioni di un file, un intervallo di fotogrammi chiave inferiore in genere riduce la qualità video complessiva a un dato bitrate.</td> 
    <td><code>String</code></td> 
    <td><p>Numero positivo.</p> <p>Il valore predefinito è 300.</p> <p>Il valore consigliato per HLS (HTTP Live Streaming) è 60-90.</p> </td> 
    </tr> 
    <tr> 
    <td><code>minBitrate</code></td> 
    <td><p>Bitrate minimo per consentire codifiche con bitrate variabile, in Kbps (kilobit al secondo).</p> <p>Questo parametro si applica solo quando<strong> l’opzione Usa bitrate</strong> costante è deselezionata nella scheda Avanzate quando si crea o si modifica un profilo di codifica video.</p> <p>Vedere anche <a href="/help/assets/video.md#bitrate">Bitrate</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Numero positivo, in Kbps.</p> <p>Nessun valore predefinito.</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>Bitrate massimo per consentire codifiche con bitrate variabile, in Kbps.</p> <p>Questo parametro si applica solo quando<strong> l’opzione Usa bitrate</strong> costante è deselezionata nella scheda Avanzate quando si crea o si modifica un profilo di codifica video.</p> <p>Vedere anche <a href="/help/assets/video.md#bitrate">Bitrate</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Numero positivo, in Kbps.</p> <p>Nessun valore predefinito. Tuttavia, il valore consigliato è fino a due volte il bitrate di codifica.</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>Impostate un valore <code>true</code> per forzare un bitrate costante per lo streaming audio, se supportato dal codec audio.</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>Default is <code>false</code>.</p> <p>Il valore consigliato per HLS (HTTP Live Streaming) è <code>false</code>.</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. Nell’angolo inferiore destro della pagina, toccate **[!UICONTROL Aggiungi]**.
1. Effettua una delle operazioni seguenti:

   * Ripetete i passaggi 3 e 4 per aggiungere un altro parametro al profilo di codifica video.
   * Nell’angolo in alto a sinistra della pagina, toccate **[!UICONTROL Salva tutto]**.

1. Nell&#39;angolo superiore sinistro della pagina **[!UICONTROL CRXDE Lite]** , toccate l&#39;icona **[!UICONTROL Indietro - Home]** per tornare alla AEM.

### Modifica di un profilo di codifica video per contenuti multimediali dinamici {#editing-a-video-encoding-profile}

Potete modificare qualsiasi profilo di codifica video creato per aggiungere, modificare o eliminare i predefiniti video all’interno di tale profilo.

Per impostazione predefinita, non è possibile modificare il profilo predefinito per la codifica **[!UICONTROL video]** adattiva fornito con gli elementi multimediali dinamici. Potete invece copiare facilmente il profilo e salvarlo con un nuovo nome. Potete quindi modificare i predefiniti desiderati nel profilo copiato.

Consultate anche [Best practice per la codifica](video.md#best-practices-for-encoding-videos)video.

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione](config-dms7.md#configuring-asset-processing)delle risorse.

**Per modificare un profilo** di codifica video per contenuti multimediali dinamici:

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili]** video, verificate il nome di un profilo video.
1. Sulla barra degli strumenti, toccate **[!UICONTROL Modifica]**.
1. Nella pagina Profilo **[!UICONTROL di codifica]** video, modificate il nome e la descrizione come desiderate.
1. Come best practice, accertati che la casella di controllo **[!UICONTROL Codifica per streaming adattivo]** sia selezionata.

   Per una descrizione dello streaming adattivo, tocca l’icona delle informazioni. (Se state modificando un profilo video progressivo, non selezionate questa casella di controllo.)

1. Nell’intestazione Predefiniti **[!UICONTROL di codifica]** video potete aggiungere, modificare o eliminare predefiniti di codifica video che compongono il profilo.

   Tap the **[!UICONTROL Information]** icon next to each option on the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs for additional descriptions or recommended settings based on the selected video format codec.

1. Nell’angolo in alto a destro della pagina, tocca **[!UICONTROL Salva]**.

### Copia di un profilo di codifica video per contenuti multimediali dinamici {#copying-a-video-encoding-profile}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili]** video, verificate il nome di un profilo video.
1. Sulla barra degli strumenti, toccate **[!UICONTROL Copia]**.
1. Nella pagina Profilo **[!UICONTROL di codifica]** video, immettete un nuovo nome per il profilo.
1. Come best practice, accertati che la casella di controllo **[!UICONTROL Codifica per streaming adattivo]** sia selezionata. Per una descrizione dello streaming adattivo, tocca l’icona delle informazioni. Se copi un profilo video progressivo, non selezionare la casella di controllo.

   In modalità Dynamic Media - Hybrid, se un predefinito video WebM fa parte del profilo video, **[!UICONTROL Codifica per lo streaming]** adattivo non è possibile perché tutti i predefiniti devono essere MP4.
1. Nell’intestazione Predefiniti **[!UICONTROL di codifica]** video potete aggiungere, modificare o eliminare predefiniti di codifica video che compongono il profilo.

   Toccate l&#39;icona **[!UICONTROL Informazioni]** accanto a ciascuna opzione nelle schede **[!UICONTROL Base]** e **[!UICONTROL Avanzate]** per le impostazioni e le descrizioni consigliate.

1. Nell’angolo in alto a destro della pagina, tocca **[!UICONTROL Salva]**.

### Eliminazione di un profilo di codifica video per contenuti multimediali dinamici {#deleting-a-video-encoding-profile}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili]** video, verificate i nomi di uno o più profili video.
1. Sulla barra degli strumenti, toccate **[!UICONTROL Elimina]**.
1. Toccate **[!UICONTROL OK]**.

## Applicazione di un profilo video per contenuti multimediali dinamici alle cartelle {#applying-a-video-profile-to-folders}

Quando assegnate un profilo video a una cartella, tutte le sottocartelle ereditano automaticamente il profilo dalla cartella principale. Questo significa che potete assegnare un solo profilo video a una cartella. Considerate quindi attentamente la struttura delle cartelle in cui caricare, memorizzare, usare e archiviare le risorse.

Se avete assegnato un profilo video diverso a una cartella, il nuovo profilo sostituisce il profilo precedente. Le risorse di cartella esistenti in precedenza restano invariate. Il nuovo profilo viene applicato alle risorse aggiunte successivamente alla cartella.

Le cartelle a cui è assegnato un profilo sono indicate nell&#39;interfaccia utente in base al nome del profilo visualizzato nel nome della scheda.

![chlimage_1-517](assets/chlimage_1-517.png)

Potete applicare i profili video a cartelle specifiche o globalmente a tutte le risorse.

### Applicazione di profili video a cartelle specifiche {#applying-video-profiles-to-specific-folders}

Puoi applicare un profilo video a una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come applicare i profili video alle cartelle con entrambe le soluzioni.

Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili video per contenuti multimediali dinamici alle cartelle dall’interfaccia utente Profili {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Selezionate il profilo video da applicare a una o più cartelle.
1. Tocca **[!UICONTROL Applica profilo a cartelle]** e seleziona una o più cartelle da usare per ricevere le risorse appena caricate, quindi fai clic su **[!UICONTROL Applica]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili video per contenuti multimediali dinamici alle cartelle da Proprietà {#applying-video-profiles-to-folders-from-properties}

1. Toccate il logo AEM e accedete a **[!UICONTROL Risorse]** , quindi alla cartella alla quale desiderate applicare un profilo video.
1. Sulla cartella, toccate il segno di spunta per selezionarlo, quindi toccate **[!UICONTROL Proprietà]**.
1. Select the **[!UICONTROL Video Profiles]** tab and select the profile from the drop-down menu and tap **[!UICONTROL Save &amp; Close]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

   ![chlimage_1-518](assets/chlimage_1-518.png)

### Applicazione di un profilo video per contenuti multimediali dinamici a livello globale {#applying-a-video-profile-globally}

Oltre ad applicare un profilo a una cartella, potete anche applicarne uno a livello globale in modo che a qualsiasi contenuto caricato AEM risorse di qualsiasi cartella sia applicato il profilo selezionato.

**Per applicare un profilo video per contenuti multimediali dinamici a livello globale**:

1. Passa al CRXDE Lite al seguente nodo: `/content/dam/jcr:content`.
1. Aggiungete la proprietà **[!UICONTROL videoProfile]**: `/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. Toccate **[!UICONTROL Salva tutto]**.

![chlimage_1-519](assets/chlimage_1-519.png)

## Rimozione di un profilo video per contenuti multimediali dinamici dalle cartelle {#removing-a-video-profile-from-folders}

Quando rimuovete un profilo video da una cartella, tutte le sottocartelle ereditano automaticamente la rimozione del profilo dalla cartella principale. Tuttavia, l&#39;elaborazione dei file che si è verificata all&#39;interno delle cartelle rimane intatta.

Puoi rimuovere un profilo video da una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Impostazioni cartella]**. Questa sezione descrive come rimuovere i profili video dalle cartelle con entrambe le soluzioni.

### Rimozione dei profili video per elementi multimediali dinamici dalle cartelle tramite l’interfaccia utente Profili {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Selezionate il profilo video da rimuovere da una o più cartelle.
1. Tap **[!UICONTROL Remove Profile from Folder(s)]** and select the folder or multiple folders you want use to remove the profile from and tap **[!UICONTROL Remove]**.

   Potete confermare che il profilo video non viene più applicato a una cartella perché il nome non viene più visualizzato sotto il nome della cartella.

### Rimozione dei profili video per contenuti multimediali dinamici dalle cartelle tramite Proprietà {#removing-video-profiles-from-folders-via-properties}

1. Toccate il logo AEM e accedete a **[!UICONTROL Risorse]** , quindi alla cartella da cui desiderate rimuovere un profilo video.
1. Sulla cartella, toccate il segno di spunta per selezionarlo, quindi toccate **[!UICONTROL Proprietà]**.
1. Select the **[!UICONTROL Video Profiles]** tab and select **[!UICONTROL None]** from the drop-down menu and tap **[!UICONTROL Save &amp; Close]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

