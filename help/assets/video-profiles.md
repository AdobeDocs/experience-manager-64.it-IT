---
title: Profili video Dynamic Media
description: 'Dynamic Media viene fornito con un profilo di codifica video adattiva predefinito. Le impostazioni incluse in questo profilo out-of-the-box sono ottimizzate per offrire ai clienti la migliore esperienza di visualizzazione video possibile. '
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '3068'
ht-degree: 18%

---


# Profili video Dynamic Media {#video-profiles}

Dynamic Media è già dotato di un profilo di codifica video adattiva predefinito. Le impostazioni incluse in questo profilo out-of-the-box sono ottimizzate per offrire ai clienti la migliore esperienza di visualizzazione possibile. Quando codificate i video principali utilizzando il profilo di codifica per video adattivi, durante la riproduzione il lettore video regola automaticamente la qualità del flusso video in base alla velocità di connessione Internet dei clienti. È noto come streaming adattivo.

Di seguito sono riportati altri fattori che determinano la qualità dei video:

* **Risoluzione del video principale caricato**

   Se il video MP4 veniva registrato a una risoluzione inferiore, ad esempio 240p o 360p, non poteva essere trasmesso in streaming in alta definizione.

* **Dimensioni del lettore video**

   Per impostazione predefinita, la **[!UICONTROL Larghezza]** nel profilo di codifica video adattiva è impostata su **[!UICONTROL Auto]**. Anche in questo caso, durante la riproduzione, viene utilizzata la qualità migliore in base alle dimensioni del lettore.

Vedere anche [Best practice per la codifica video](video.md#best-practices-for-encoding-videos).

>[!NOTE]
>
>Per generare i metadati di un video e le miniature delle immagini video associate, il video stesso deve seguire il processo di codifica di Dynamic Media. Se hai attivato gli elementi multimediali dinamici e hai impostato Cloud Services per i video, il flusso di lavoro **[!UICONTROL Codifica video elementi multimediali dinamici]** di AEM ti consente di eseguire la codifica dei video. Questo flusso di lavoro acquisisce la cronologia del processo del flusso di lavoro e le informazioni di errore.
>
>Consulta la sezione [Monitoraggio della codifica video e stato della pubblicazione su YouTube](video.md#monitoring-video-encoding-and-youtube-publishing-progress). Se avete attivato Dynamic Media e impostato i servizi cloud per video, il flusso di lavoro **[!UICONTROL Dynamic Media Encode Video]** diventa automaticamente attivo quando caricate un video. Se non utilizzi gli elementi multimediali dinamici, viene applicato il flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.
>
>I metadati sono utili per la ricerca delle risorse. Le miniature sono immagini video statiche generate durante la codifica. Sono richiesti dal sistema AEM e utilizzati nell&#39;interfaccia utente per identificare visivamente i video nella visualizzazione **[!UICONTROL Schede]**, **[!UICONTROL Risultati ricerca]** e nella visualizzazione **[!UICONTROL Elenco risorse]**. Potete visualizzare le miniature generate toccando l&#39;icona **[!UICONTROL Rendering]** (palette del pittore) di un video codificato.

Una volta creato il profilo video, questo viene applicato a una cartella o più cartelle. Consultate [Applicazione di un profilo video alle cartelle.](#applying-a-video-profile-to-folders)

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consultate [Configuring Asset Processing](config-dms7.md#configuring-asset-processing) (Configurazione dell&#39;elaborazione delle risorse).

## Predefiniti codifica video adattata {#adaptive-video-encoding-presets}

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

## Creazione di un profilo di codifica video Dynamic Media per lo streaming adattivo {#creating-a-video-encoding-profile-for-adaptive-streaming}

Dynamic Media è già dotato di un profilo di codifica video adattiva predefinito, un gruppo di impostazioni di caricamento video per MP4 H.264, ottimizzato per garantire una migliore esperienza di visualizzazione. Potete usare questo profilo quando caricate i video.

Tuttavia, se questo profilo predefinito non soddisfa le esigenze, potete scegliere di creare un profilo di codifica video adattivo personalizzato. Quando utilizzate l&#39;impostazione **[!UICONTROL Codifica per lo streaming adattivo]**-*una procedura consigliata*- tutti i predefiniti di codifica aggiunti al profilo vengono convalidati per garantire che tutti i video abbiano le stesse proporzioni. Inoltre, i video codificati vengono trattati come un set di bitrate multipli per lo streaming.

Quando create il profilo di codifica video, noterete che la maggior parte delle opzioni di codifica sono precompilate con le impostazioni predefinite consigliate per facilitare l’utente. Tuttavia, se selezionate un valore diverso da quello predefinito consigliato, tenete presente che potrebbe causare problemi di qualità video durante la riproduzione e altre prestazioni.

Pertanto, per tutti i predefiniti di codifica video MP4 H.264 presenti nel profilo, i seguenti valori vengono convalidati per garantire che siano identici tra i singoli predefiniti di codifica nel profilo, rendendo possibile lo streaming adattivo:

* Codec formato video - MP4 H.264 (.mp4)
* Codec audio
* Bitrate audio
* Mantieni proporzioni
* Codifica a due passate
* Bitrate costante
* Profilo H264
* Frequenza di campionamento audio

Se i valori non sono identici, potete continuare a creare il profilo così com&#39;è. Tuttavia, lo streaming adattivo non sarà possibile. Gli utenti possono invece utilizzare lo streaming a bitrate singolo. È consigliabile modificare le impostazioni di codifica in modo da utilizzare gli stessi valori per i singoli predefiniti di codifica presenti nel profilo. Tenete presente che l’editor del profilo video/predefinito deve applicare la parità delle impostazioni di codifica video adattiva se è abilitata la codifica **[!UICONTROL Encode for adaptive streaming]**.

Consultate anche [Creazione di un profilo di codifica video per lo streaming progressivo](#creating-a-video-encoding-profile-for-progressive-streaming).

Vedere anche [Best practice per la codifica video](video.md#best-practices-for-encoding-videos).

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consultate [Configuring Asset Processing](config-dms7.md#configuring-asset-processing) (Configurazione dell&#39;elaborazione delle risorse).

Una volta creato il profilo video, questo viene applicato a una o più cartelle.

**Per creare un profilo di codifica video Dynamic Media per lo streaming** adattivo:

1. Toccate o fate clic sul logo AEM e andate a **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Toccate **[!UICONTROL Crea]** per aggiungere un nuovo profilo video.

1. Immettete un nome e una descrizione per il profilo.
1. Assicurarsi che l&#39;opzione **[!UICONTROL Codifica per lo streaming adattivo]** sia selezionata (impostazione predefinita).
1. Toccate **[!UICONTROL Aggiungi predefinito di codifica video]**.
1. Nella scheda **[!UICONTROL Base]**, impostare le opzioni video e audio.

   Toccate l’icona delle informazioni accanto a ciascuna opzione per ottenere descrizioni aggiuntive o impostazioni consigliate in base al codec del formato video selezionato.

1. Sotto l’intestazione Dimensione video, verificate che **[!UICONTROL Mantieni proporzioni]** sia selezionato.
1. Impostate la risoluzione del fotogramma video in pixel. Utilizzare il valore **[!UICONTROL Auto]** per ridimensionare automaticamente in modo che corrisponda alle proporzioni di origine (rapporto larghezza/altezza). Ad esempio, Auto x 480 o 640 x Auto.

   Effettua una delle operazioni seguenti:

   * Nel campo **[!UICONTROL Larghezza]**, immettere **[!UICONTROL auto]**. Nel campo **[!UICONTROL Height]**, immettere un valore in pixel.
   * Per visualizzare le dimensioni del video, toccate l&#39;icona **[!UICONTROL Information]** (i) a destra di **[!UICONTROL Height]** per aprire la pagina **[!UICONTROL Size Calculator]**. Utilizzate **[!UICONTROL Calcolatore dimensioni]** per impostare le dimensioni video (rappresentate dalla casella blu) desiderate. Toccate **[!UICONTROL X]** nell&#39;angolo superiore destro al termine.

1. (Facoltativo) Toccare la scheda **[!UICONTROL Avanzate]** e assicurarsi che la casella di controllo **[!UICONTROL Usa valori predefiniti]** sia selezionata (consigliato). In alternativa, modificate le impostazioni audio e video avanzate.
1. Nell&#39;angolo superiore destro della pagina, toccate **[!UICONTROL Salva]** per salvare il predefinito.
1. Effettua una delle operazioni seguenti:

   * Ripetete i passaggi da 5 a 10 per creare altri predefiniti di codifica. Lo streaming di video adattivi richiede più di un predefinito video.
   * Nell&#39;angolo superiore destro della pagina, toccate di nuovo **[!UICONTROL Salva]** per salvare il profilo.

## Monitoraggio dell&#39;avanzamento di un processo di codifica {#monitoring-the-progress-of-an-encoding-job}

Viene visualizzato un indicatore di elaborazione (o una barra di avanzamento) che consente di monitorare visivamente l’avanzamento di un processo di codifica video.

È inoltre possibile visualizzare il file `error.log` per monitorare l&#39;avanzamento di un processo di codifica, verificare se la codifica è terminata o visualizzare eventuali errori di processo. La cartella `error.log` si trova nella cartella `logs` in cui è installata l&#39;istanza di AEM.

## Creazione di un profilo di codifica video Dynamic Media per lo streaming progressivo {#creating-a-video-encoding-profile-for-progressive-streaming}

Se scegli di non utilizzare l’opzione **[!UICONTROL Codifica per lo streaming adattivo]**, tutti i predefiniti di codifica aggiunti al profilo vengono trattati come rappresentazioni video individuali per lo streaming a bitrate singolo o per la distribuzione progressiva di video. Inoltre, non esiste una convalida per garantire che tutte le rappresentazioni video abbiano le stesse proporzioni.

A seconda della modalità in esecuzione, i codec supportati sono:

* Modalità Dynamic Media-Scene7: H.264 (.mp4)
* Modalità ibrida Dynamic Media: H.264 (.mp4), WebM

Consultate anche [Creazione di un profilo di codifica video per lo streaming adattivo](#creating-a-video-encoding-profile-for-adaptive-streaming).

Vedere anche [Best practice per la codifica video](video.md#best-practices-for-encoding-videos).

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consultate [Configuring Asset Processing](config-dms7.md#configuring-asset-processing) (Configurazione dell&#39;elaborazione delle risorse).

Una volta creato il profilo video, questo viene applicato a una o più cartelle.

**Per creare un profilo di codifica video Dynamic Media per lo streaming progressivo:**

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Toccate **[!UICONTROL Crea]** per aggiungere un nuovo profilo video.
1. Immettete un nome e una descrizione per il profilo.
1. Deselezionate la casella di controllo **[!UICONTROL Codifica per lo streaming adattivo]**.
1. Toccate **[!UICONTROL Aggiungi predefinito di codifica video]**.
1. Nella scheda **[!UICONTROL Base]**, impostare le opzioni video e audio.

   Toccate l&#39;icona **[!UICONTROL Information]** accanto a ciascuna opzione per le descrizioni aggiuntive o le impostazioni consigliate in base al codec del formato video selezionato.

1. (Facoltativo) Sotto l&#39;intestazione **Dimensioni video**, deselezionare **[!UICONTROL Mantieni proporzioni]**.
1. Nel campo **[!UICONTROL Larghezza]**, immettere **[!UICONTROL auto]**; a destra del campo **[!UICONTROL Height]**, toccate l&#39;icona **[!UICONTROL Information]**. Utilizzare la pagina **[!UICONTROL Calcolatore dimensioni]** per impostare ulteriormente la dimensione video (casella blu) come desiderato. Toccate **[!UICONTROL X]** al termine.
1. (Facoltativo) Effettuate una delle seguenti operazioni:

   * Toccare la scheda **[!UICONTROL Avanzate]** e assicurarsi che la casella di controllo **[!UICONTROL Usa valori predefiniti]** sia selezionata (consigliato).
   * Deselezionate la casella di controllo **[!UICONTROL Usa valori predefiniti]** e specificate le impostazioni video e audio desiderate.

      Toccate l&#39;icona **[!UICONTROL Information]** accanto a ciascuna opzione per le descrizioni aggiuntive o le impostazioni consigliate in base al codec del formato video selezionato.

1. Nell&#39;angolo superiore destro della pagina, toccate **[!UICONTROL Salva]** per salvare il predefinito.
1. Effettua una delle operazioni seguenti:

   * Ripetete i passaggi da 5 a 10 per creare altri predefiniti di codifica.
   * Nell’angolo superiore destro della pagina, tocca **[!UICONTROL Salva]** per salvare il profilo.

## Utilizzo di parametri di codifica video personalizzati {#using-custom-added-video-encoding-parameters}

Potete modificare un profilo di codifica video esistente per sfruttare i parametri di codifica video avanzati che non sono disponibili nell’interfaccia utente al momento della creazione o della modifica di un profilo video in AEM. Potete aggiungere uno o più parametri avanzati al profilo esistente, ad esempio **[!UICONTROL minBitrate]** e **[!UICONTROL maxBitrate]**.

**Per utilizzare parametri** di codifica video personalizzati:

1. Tocca il logo AEM, quindi seleziona **[!UICONTROL Strumenti > Generale > CRXDE Lite]**.
1. Dalla pagina **[!UICONTROL CRXDE Lite]**, nel pannello **[!UICONTROL Esplora risorse]** a sinistra, andate a:

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. Nel pannello in basso a destra della pagina, dalla scheda **[!UICONTROL Proprietà]**, specificare il **[!UICONTROL Nome]**, **[!UICONTROL Tipo]** e **[!UICONTROL Valore]** del parametro che si desidera utilizzare.

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
    <td><p>Bitrate minimo per consentire codifiche con bitrate variabile, in Kbps (kilobit al secondo).</p> <p>Questo parametro si applica solo quando l'opzione <strong> Usa bitrate costante</strong> è deselezionata nella scheda Avanzate quando si crea o si modifica un profilo di codifica video.</p> <p>Vedere anche <a href="/help/assets/video.md#bitrate">Bitrate</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Numero positivo, in Kbps.</p> <p>Nessun valore predefinito.</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>Bitrate massimo per consentire codifiche con bitrate variabile, in Kbps.</p> <p>Questo parametro si applica solo quando l'opzione <strong> Usa bitrate costante</strong> è deselezionata nella scheda Avanzate quando si crea o si modifica un profilo di codifica video.</p> <p>Vedere anche <a href="/help/assets/video.md#bitrate">Bitrate</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Numero positivo, in Kbps.</p> <p>Nessun valore predefinito. Tuttavia, il valore consigliato è fino a due volte il bitrate di codifica.</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>Impostate il valore su <code>true</code> per forzare un bitrate costante per il flusso audio, se supportato dal codec audio.</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>Il valore predefinito è <code>false</code>.</p> <p>Il valore consigliato per HLS (HTTP Live Streaming) è <code>false</code>.</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. Nell&#39;angolo inferiore destro della pagina, toccare **[!UICONTROL Aggiungi]**.
1. Effettua una delle operazioni seguenti:

   * Ripetete i passaggi 3 e 4 per aggiungere un altro parametro al profilo di codifica video.
   * Vicino all&#39;angolo superiore sinistro della pagina, toccare **[!UICONTROL Salva tutto]**.

1. Nell&#39;angolo superiore sinistro della pagina **[!UICONTROL CRXDE Lite]**, toccare l&#39;icona **[!UICONTROL Indietro Home]** per tornare alla AEM.

### Modifica di un profilo di codifica video Dynamic Media {#editing-a-video-encoding-profile}

Potete modificare qualsiasi profilo di codifica video creato per aggiungere, modificare o eliminare i predefiniti video all’interno di tale profilo.

Per impostazione predefinita, non è possibile modificare il profilo **[!UICONTROL Codifica video adattiva]** predefinito fornito con Dynamic Media. Potete invece copiare facilmente il profilo e salvarlo con un nuovo nome. Potete quindi modificare i predefiniti desiderati nel profilo copiato.

Vedere anche [Best practice per la codifica video](video.md#best-practices-for-encoding-videos).

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consultate [Configuring Asset Processing](config-dms7.md#configuring-asset-processing) (Configurazione dell&#39;elaborazione delle risorse).

**Per modificare un profilo** di codifica video Dynamic Media:

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili video]**, verificate il nome di un profilo video.
1. Sulla barra degli strumenti, toccare **[!UICONTROL Modifica]**.
1. Nella pagina **[!UICONTROL Video Encoding Profile]**, modificate il nome e la descrizione come desiderate.
1. Come best practice, accertati che la casella di controllo **[!UICONTROL Codifica per streaming adattivo]** sia selezionata.

   Per una descrizione dello streaming adattivo, tocca l’icona delle informazioni. (Se state modificando un profilo video progressivo, non selezionate questa casella di controllo.)

1. Nell’intestazione **[!UICONTROL Predefiniti codifica video]**, potete aggiungere, modificare o eliminare i predefiniti di codifica video che compongono il profilo.

   Toccate l&#39;icona **[!UICONTROL Information]** accanto a ciascuna opzione nelle schede **[!UICONTROL Basic]** e **[!UICONTROL Advanced]** per ottenere descrizioni aggiuntive o impostazioni consigliate in base al codec del formato video selezionato.

1. Nell’angolo in alto a destro della pagina, tocca **[!UICONTROL Salva]**.

### Copia di un profilo di codifica video Dynamic Media {#copying-a-video-encoding-profile}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili video]**, verificate il nome di un profilo video.
1. Sulla barra degli strumenti, toccare **[!UICONTROL Copia]**.
1. Nella pagina **[!UICONTROL Video Encoding Profile]**, immettete un nuovo nome per il profilo.
1. Come best practice, accertati che la casella di controllo **[!UICONTROL Codifica per streaming adattivo]** sia selezionata. Per una descrizione dello streaming adattivo, tocca l’icona delle informazioni. Se copi un profilo video progressivo, non selezionare la casella di controllo.

   In Dynamic Media - Modalità ibrida, se un predefinito video WebM fa parte del profilo video, non è possibile codificare **[!UICONTROL lo streaming adattivo]** perché tutti i predefiniti devono essere MP4.
1. Nell’intestazione **[!UICONTROL Predefiniti codifica video]**, potete aggiungere, modificare o eliminare i predefiniti di codifica video che compongono il profilo.

   Toccate l&#39;icona **[!UICONTROL Information]** accanto a ciascuna opzione nelle schede **[!UICONTROL Basic]** e **[!UICONTROL Advanced]** per le impostazioni e le descrizioni consigliate.

1. Nell’angolo in alto a destro della pagina, tocca **[!UICONTROL Salva]**.

### Eliminazione di un profilo di codifica video Dynamic Media {#deleting-a-video-encoding-profile}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili video]**, controllate uno o più nomi di profilo video.
1. Sulla barra degli strumenti, toccare **[!UICONTROL Elimina]**.
1. Toccate **[!UICONTROL OK]**.

## Applicazione di un profilo video Dynamic Media alle cartelle {#applying-a-video-profile-to-folders}

Quando assegnate un profilo video a una cartella, tutte le sottocartelle ereditano automaticamente il profilo dalla cartella principale. Questo significa che potete assegnare un solo profilo video a una cartella. Considerate quindi attentamente la struttura delle cartelle in cui caricare, memorizzare, usare e archiviare le risorse.

Se avete assegnato un profilo video diverso a una cartella, il nuovo profilo sostituisce il profilo precedente. Le risorse di cartella esistenti in precedenza restano invariate. Il nuovo profilo viene applicato alle risorse aggiunte successivamente alla cartella.

Le cartelle a cui è assegnato un profilo sono indicate nell&#39;interfaccia utente in base al nome del profilo visualizzato nel nome della scheda.

![chlimage_1-517](assets/chlimage_1-517.png)

Potete applicare i profili video a cartelle specifiche o globalmente a tutte le risorse.

### Applicazione dei profili video a cartelle specifiche {#applying-video-profiles-to-specific-folders}

Puoi applicare un profilo video a una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come applicare i profili video alle cartelle con entrambe le soluzioni.

Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili video Dynamic Media alle cartelle dall&#39;interfaccia utente Profili {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Selezionate il profilo video da applicare a una o più cartelle.
1. Tocca **[!UICONTROL Applica profilo a cartelle]** e seleziona una o più cartelle da usare per ricevere le risorse appena caricate, quindi fai clic su **[!UICONTROL Applica]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili video Dynamic Media alle cartelle da Proprietà {#applying-video-profiles-to-folders-from-properties}

1. Toccate il logo AEM e andate a **[!UICONTROL Risorse]**, quindi alla cartella alla quale desiderate applicare un profilo video.
1. Sulla cartella, toccare il segno di spunta per selezionarlo, quindi toccare **[!UICONTROL Properties]**.
1. Selezionate la scheda **[!UICONTROL Profili video]**, selezionate il profilo dal menu a discesa e toccate **[!UICONTROL Salva e chiudi]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

   ![chlimage_1-518](assets/chlimage_1-518.png)

### Applicazione di un profilo video Dynamic Media a livello globale {#applying-a-video-profile-globally}

Oltre ad applicare un profilo a una cartella, potete anche applicarne uno a livello globale in modo che a qualsiasi contenuto caricato AEM risorse di qualsiasi cartella sia applicato il profilo selezionato.

**Per applicare un profilo video Dynamic Media a livello globale**:

1. Passa al CRXDE Lite al seguente nodo: `/content/dam/jcr:content`.
1. Aggiungete la proprietà **[!UICONTROL videoProfile]**: `/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. Toccate **[!UICONTROL Salva tutto]**.

![chlimage_1-519](assets/chlimage_1-519.png)

## Rimozione di un profilo video Dynamic Media dalle cartelle {#removing-a-video-profile-from-folders}

Quando rimuovete un profilo video da una cartella, tutte le sottocartelle ereditano automaticamente la rimozione del profilo dalla cartella principale. Tuttavia, l&#39;elaborazione dei file che si è verificata all&#39;interno delle cartelle rimane intatta.

Puoi rimuovere un profilo video da una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Impostazioni cartella]**. Questa sezione descrive come rimuovere i profili video dalle cartelle con entrambe le soluzioni.

### Rimozione di profili video Dynamic Media dalle cartelle tramite l&#39;interfaccia utente Profili {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Selezionate il profilo video da rimuovere da una o più cartelle.
1. Toccate **[!UICONTROL Rimuovi profilo dalle cartelle]**, quindi selezionate la cartella o le cartelle da cui desiderate rimuovere il profilo e toccate **[!UICONTROL Rimuovi]**.

   Potete confermare che il profilo video non viene più applicato a una cartella perché il nome non viene più visualizzato sotto il nome della cartella.

### Rimozione di profili video Dynamic Media dalle cartelle tramite Proprietà{#removing-video-profiles-from-folders-via-properties}

1. Toccate il logo AEM e andate a **[!UICONTROL Risorse]**, quindi alla cartella da cui desiderate rimuovere un profilo video.
1. Sulla cartella, toccare il segno di spunta per selezionarlo, quindi toccare **[!UICONTROL Properties]**.
1. Selezionate la scheda **[!UICONTROL Profili video]**, quindi selezionate **[!UICONTROL Nessuno]** dal menu a discesa e toccate **[!UICONTROL Salva e chiudi]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

