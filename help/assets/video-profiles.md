---
title: Profili video Dynamic Media
description: 'Dynamic Media viene fornito con un profilo di codifica video adattivo predefinito. Le impostazioni di questo profilo predefinito sono ottimizzate per offrire ai clienti la migliore esperienza di visualizzazione video possibile. '
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
exl-id: 3602e1b9-624d-408f-a7f6-1598b62dbd22
feature: Video Profiles,Video
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '3071'
ht-degree: 18%

---

# Profili video Dynamic Media {#video-profiles}

Dynamic Media dispone già di un profilo di codifica video adattivo predefinito. Le impostazioni di questo profilo predefinito sono ottimizzate per offrire ai clienti la migliore esperienza di visualizzazione possibile. Quando si codificano i video master utilizzando il profilo di codifica video adattiva, durante la riproduzione il lettore video regola automaticamente la qualità del flusso video in base alla velocità di connessione Internet dei clienti. Questo è noto come streaming adattivo.

Di seguito sono riportati altri fattori che determinano la qualità dei video:

* **Risoluzione del video principale caricato**

   Se il video MP4 è stato registrato a una risoluzione inferiore, ad esempio 240p o 360p, non può essere trasmesso in alta definizione.

* **Dimensioni del lettore video**

   Per impostazione predefinita, il valore **[!UICONTROL Larghezza]** nel profilo Codifica video adattiva è impostato su **[!UICONTROL Auto]**. Anche in questo caso, durante la riproduzione, viene utilizzata la migliore qualità in base alle dimensioni del lettore.

Vedere anche [Best practice per la codifica video](video.md#best-practices-for-encoding-videos).

>[!NOTE]
>
>Per generare i metadati di un video e le miniature delle immagini video associate, il video stesso deve seguire il processo di codifica di Dynamic Media. Se hai attivato gli elementi multimediali dinamici e hai impostato Cloud Services per i video, il flusso di lavoro **[!UICONTROL Codifica video elementi multimediali dinamici]** di AEM ti consente di eseguire la codifica dei video. Questo flusso di lavoro acquisisce la cronologia del processo del flusso di lavoro e le informazioni di errore.
>
>Consulta la sezione [Monitoraggio della codifica video e stato della pubblicazione su YouTube](video.md#monitoring-video-encoding-and-youtube-publishing-progress). Se hai abilitato Dynamic Media e hai impostato Cloud Services per i video, il flusso di lavoro **[!UICONTROL Codifica video Dynamic Media]** ha effetto automaticamente al momento del caricamento di un video. Se non utilizzi gli elementi multimediali dinamici, viene applicato il flusso di lavoro **[!UICONTROL Risorsa di aggiornamento DAM]**.
>
>I metadati sono utili nella ricerca delle risorse. Le miniature sono immagini video statiche generate durante la codifica. Il sistema AEM li richiede e utilizza nell’interfaccia utente per identificare visivamente i video nella vista **[!UICONTROL Vista schede]**, **[!UICONTROL Risultati ricerca]** e nella vista **[!UICONTROL Elenco risorse]**. Puoi visualizzare le miniature generate toccando l’icona **[!UICONTROL Rappresentazioni]** (palette del pittore) di un video codificato.

Al termine della creazione del profilo video, lo si applica a una cartella o a più cartelle. Consulta [Applicazione di un profilo video alle cartelle.](#applying-a-video-profile-to-folders)

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione delle risorse](config-dms7.md#configuring-asset-processing).

## Predefiniti di codifica per video adattivo {#adaptive-video-encoding-presets}

La tabella seguente identifica i profili di codifica best practice per lo streaming di video adattivo su dispositivi mobili e tablet e computer desktop. Puoi usare questi predefiniti per qualsiasi video con proporzioni.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Codec formato video</strong></td> 
   <td><strong>Dimensioni video - Larghezza (px)</strong></td> 
   <td><strong>Dimensioni video - Altezza (px)</strong></td> 
   <td><strong>Mantieni proporzioni?</strong></td> 
   <td><strong>Bitrate video (Kbps)</strong></td> 
   <td><strong>Frame rate video (Fps)</strong></td> 
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

Dynamic Media è già dotato di un profilo di codifica video adattivo predefinito, un gruppo di impostazioni di caricamento video per MP4 H.264, ottimizzato per la migliore esperienza di visualizzazione. Puoi usare questo profilo quando carichi i tuoi video.

Tuttavia, se questo profilo predefinito non soddisfa le tue esigenze, puoi scegliere di creare un tuo profilo di codifica video adattivo. Quando utilizzi l’impostazione **[!UICONTROL Codifica per lo streaming adattivo]**-*a best practice*- tutti i predefiniti di codifica aggiunti al profilo vengono convalidati per garantire che tutte le immagini video abbiano le stesse proporzioni. Inoltre, i video codificati vengono trattati come un set a più bit rate per lo streaming.

Quando crei il profilo di codifica video, noterai che la maggior parte delle opzioni di codifica sono precompilate con le impostazioni predefinite consigliate per aiutarti. Tuttavia, se selezioni un valore diverso da quello predefinito consigliato, tieni presente che potrebbe causare problemi di qualità video durante la riproduzione e altri problemi di prestazioni.

Pertanto, per tutti i predefiniti di codifica video MP4 H.264 presenti nel profilo, i seguenti valori vengono convalidati per garantire che siano gli stessi tra i singoli predefiniti di codifica nel profilo, consentendo in tal modo lo streaming adattivo:

* Codec video formato - MP4 H.264 (.mp4)
* Codec audio
* Bitrate audio
* Mantieni proporzioni
* Codifica a due passate
* Bitrate costante
* Profilo H264
* Frequenza di campionamento audio

Se i valori non sono uguali, puoi continuare a creare il profilo così com’è. Tuttavia, lo streaming adattivo non sarà possibile. Gli utenti sperimenteranno invece lo streaming a bitrate singolo. È consigliabile modificare le impostazioni di codifica per utilizzare gli stessi valori tra i singoli predefiniti di codifica nel profilo. Se è abilitato **[!UICONTROL Codifica per lo streaming adattivo]** , l’editor del profilo video/predefinito deve applicare la parità delle impostazioni di codifica per i video adattivi.

Vedi anche [Creazione di un profilo di codifica video per lo streaming progressivo](#creating-a-video-encoding-profile-for-progressive-streaming).

Vedere anche [Best practice per la codifica video](video.md#best-practices-for-encoding-videos).

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione delle risorse](config-dms7.md#configuring-asset-processing).

Al termine della creazione del profilo video, lo si applica a una o più cartelle.

**Per creare un profilo di codifica video Dynamic Media per lo streaming** adattivo:

1. Tocca o fai clic sul logo AEM e passa a **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Tocca **[!UICONTROL Crea]** per aggiungere un nuovo profilo video.

1. Immetti un nome e una descrizione per il profilo.
1. Assicurati che sia selezionato **[!UICONTROL Codifica per lo streaming adattivo]** (impostazione predefinita).
1. Tocca **[!UICONTROL Aggiungi predefinito di codifica video]**.
1. Nella scheda **[!UICONTROL Base]** , imposta le opzioni video e audio.

   Toccare l’icona delle informazioni accanto a ciascuna opzione per ottenere descrizioni aggiuntive o impostazioni consigliate in base al codec del formato video selezionato.

1. Sotto l&#39;intestazione Dimensione video, assicurarsi che sia selezionato **[!UICONTROL Mantieni rapporto di formato]**.
1. Imposta la risoluzione del fotogramma video in pixel. Utilizzare il valore **[!UICONTROL Auto]** per ridimensionare automaticamente in modo che corrisponda alle proporzioni della sorgente (rapporto larghezza/altezza). Ad esempio, Auto x 480 o 640 x Auto.

   Effettua una delle operazioni seguenti:

   * Nel campo **[!UICONTROL Larghezza]**, immetti **[!UICONTROL auto]**. Nel campo **[!UICONTROL Altezza]**, immetti un valore in pixel.
   * Per visualizzare le dimensioni del video, tocca l’ icona **[!UICONTROL Informazioni]** (i) a destra di **[!UICONTROL Altezza]** per aprire la pagina **[!UICONTROL Calcolatore dimensioni]** . Utilizza **[!UICONTROL Calcolatore dimensioni]** per impostare le dimensioni video (rappresentate dalla casella blu) desiderate. Al termine, tocca **[!UICONTROL X]** nell’angolo superiore destro.

1. (Facoltativo) Tocca la scheda **[!UICONTROL Avanzate]** e assicurati che la casella di controllo **[!UICONTROL Usa valori predefiniti]** sia selezionata (scelta consigliata). In alternativa, puoi modificare le impostazioni audio e video avanzate.
1. Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Salva]** per salvare il predefinito.
1. Effettua una delle operazioni seguenti:

   * Ripeti i passaggi da 5 a 10 per creare altri predefiniti di codifica. Lo streaming video adattivo richiede più di un predefinito video.
   * Nell’angolo in alto a destra della pagina, tocca di nuovo **[!UICONTROL Salva]** per salvare il profilo.

## Monitoraggio dell’avanzamento di un processo di codifica {#monitoring-the-progress-of-an-encoding-job}

Viene visualizzato un indicatore di elaborazione (o barra di avanzamento) che consente di monitorare visivamente l’avanzamento di un processo di codifica video.

È inoltre possibile visualizzare il file `error.log` per monitorare l’avanzamento di un processo di codifica, verificare se la codifica è stata completata o visualizzare eventuali errori di processo. La cartella `error.log` si trova nella cartella `logs` in cui è installata l&#39;istanza di AEM.

## Creazione di un profilo di codifica video Dynamic Media per lo streaming progressivo {#creating-a-video-encoding-profile-for-progressive-streaming}

Se scegli di non utilizzare l’opzione **[!UICONTROL Codifica per lo streaming adattivo]**, tutti i predefiniti di codifica aggiunti al profilo vengono trattati come rappresentazioni video individuali per lo streaming a bitrate singolo o per la distribuzione progressiva di video. Inoltre, non esiste una convalida per garantire che tutte le rappresentazioni video abbiano le stesse proporzioni.

A seconda della modalità di esecuzione, i codec del formato video supportati sono i seguenti:

* Modalità Dynamic Media-Scene7: H.264 (mp4)
* Modalità Dynamic Media-Hybrid: H.264 (.mp4), WebM

Vedi anche [Creazione di un profilo di codifica video per lo streaming adattivo](#creating-a-video-encoding-profile-for-adaptive-streaming).

Vedere anche [Best practice per la codifica video](video.md#best-practices-for-encoding-videos).

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione delle risorse](config-dms7.md#configuring-asset-processing).

Al termine della creazione del profilo video, lo si applica a una o più cartelle.

**Per creare un profilo di codifica video Dynamic Media per lo streaming progressivo:**

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Tocca **[!UICONTROL Crea]** per aggiungere un nuovo profilo video.
1. Immetti un nome e una descrizione per il profilo.
1. Deseleziona la casella di controllo **[!UICONTROL Codifica per streaming adattivo]** .
1. Tocca **[!UICONTROL Aggiungi predefinito di codifica video]**.
1. Nella scheda **[!UICONTROL Base]** , imposta le opzioni video e audio.

   Tocca l’icona **[!UICONTROL Informazioni]** accanto a ciascuna opzione per ottenere descrizioni aggiuntive o impostazioni consigliate in base al codec del formato video selezionato.

1. (Facoltativo) Sotto l&#39;intestazione **Dimensioni video**, deselezionare **[!UICONTROL Mantieni proporzioni]**.
1. Nel campo **[!UICONTROL Larghezza]**, immetti **[!UICONTROL auto]**; a destra del campo **[!UICONTROL Altezza]**, tocca l&#39;icona **[!UICONTROL Informazioni]**. Utilizza la pagina **[!UICONTROL Calcolatore dimensioni]** per impostare ulteriormente la dimensione video (casella blu) in base alle tue preferenze. Al termine, tocca **[!UICONTROL X]** .
1. (Facoltativo) Effettua una delle seguenti operazioni:

   * Tocca la scheda **[!UICONTROL Avanzate]** e assicurati che la casella di controllo **[!UICONTROL Usa valori predefiniti]** sia selezionata (scelta consigliata).
   * Deselezionare la casella di controllo **[!UICONTROL Usa valori predefiniti]** e specificare le impostazioni video e audio desiderate.

      Tocca l’icona **[!UICONTROL Informazioni]** accanto a ciascuna opzione per ottenere descrizioni aggiuntive o impostazioni consigliate in base al codec del formato video selezionato.

1. Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Salva]** per salvare il predefinito.
1. Effettua una delle operazioni seguenti:

   * Ripeti i passaggi da 5 a 10 per creare altri predefiniti di codifica.
   * Nell’angolo superiore destro della pagina, tocca **[!UICONTROL Salva]** per salvare il profilo.

## Utilizzo di parametri di codifica video personalizzati {#using-custom-added-video-encoding-parameters}

Puoi modificare un profilo di codifica video esistente per sfruttare parametri di codifica video avanzati che non sono disponibili nell’interfaccia utente quando crei o modifichi un profilo video in AEM. Puoi aggiungere al profilo esistente uno o più parametri avanzati, ad esempio **[!UICONTROL minBitrate]** e **[!UICONTROL maxBitrate]**.

**Per utilizzare parametri** di codifica video personalizzati:

1. Tocca il logo AEM, quindi seleziona **[!UICONTROL Strumenti > Generale > CRXDE Lite]**.
1. Dalla pagina **[!UICONTROL CRXDE Lite]**, nel pannello **[!UICONTROL Esplora risorse]** a sinistra, passa al seguente percorso:

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. Nel pannello in basso a destra della pagina, dalla scheda **[!UICONTROL Proprietà]** , specifica il **[!UICONTROL Nome]**, **[!UICONTROL Tipo]** e **[!UICONTROL Valore]** del parametro che desideri utilizzare.

   Sono disponibili i seguenti parametri avanzati da utilizzare:

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
    <td>Livello H.264 da utilizzare per la codifica. Normalmente questo viene determinato automaticamente in base alle impostazioni di codifica in uso.</td> 
    <td><code>String</code></td> 
    <td><p>10 * livello h264</p> <p>Ad esempio, 3,0 = 30, 1,3 = 13)</p> <p>Nessun valore predefinito.</p> </td> 
    </tr> 
    <tr> 
    <td><code>keyframe</code></td> 
    <td>Il numero di fotogrammi di destinazione tra i fotogrammi chiave. Calcola questo valore per generare un fotogramma chiave ogni 2-10 secondi. Ad esempio, a 30 fotogrammi al secondo, l'intervallo del fotogramma chiave dovrebbe essere 60-300.<br /> <br /> Intervalli di fotogrammi chiave più bassi migliorano il comportamento di ricerca e commutazione del flusso per le codifiche video adattive e possono anche migliorare la qualità dei video che hanno molto movimento. Tuttavia, poiché i fotogrammi chiave aumentano le dimensioni di un file, un intervallo di fotogrammi chiave inferiore di solito si traduce in una qualità video complessiva inferiore a un dato bitrate.</td> 
    <td><code>String</code></td> 
    <td><p>Numero positivo.</p> <p>Il valore predefinito è 300.</p> <p>Il valore consigliato per HLS (HTTP Live Streaming) è 60-90.</p> </td> 
    </tr> 
    <tr> 
    <td><code>minBitrate</code></td> 
    <td><p>Bitrate minimo per consentire codifiche a bit rate variabile, in Kbps (kilobit al secondo).</p> <p>Questo parametro si applica solo quando<strong> Use Constant Bitrate</strong> è deselezionato nella scheda Avanzate quando crei o modifichi un profilo di codifica video.</p> <p>Vedere anche <a href="/help/assets/video.md#bitrate">Bitrate</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Numero positivo, in Kbps.</p> <p>Nessun valore predefinito.</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>Bitrate massimo per consentire codifiche a bit rate variabile, in Kbps.</p> <p>Questo parametro si applica solo quando<strong> Use Constant Bitrate</strong> è deselezionato nella scheda Avanzate quando crei o modifichi un profilo di codifica video.</p> <p>Vedere anche <a href="/help/assets/video.md#bitrate">Bitrate</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>Numero positivo, in Kbps.</p> <p>Nessun valore predefinito. Tuttavia, il valore consigliato è fino a due volte il bitrate di codifica.</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>Impostare il valore su <code>true</code> per forzare un bitrate costante per lo streaming audio, se supportato dal codec audio.</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>Il valore predefinito è <code>false</code>.</p> <p>Il valore consigliato per HLS (HTTP Live Streaming) è <code>false</code>.</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. Vicino all’angolo inferiore destro della pagina, tocca **[!UICONTROL Aggiungi]**.
1. Effettua una delle operazioni seguenti:

   * Ripeti i passaggi 3 e 4 per aggiungere un altro parametro al profilo di codifica video.
   * Nell’angolo in alto a sinistra della pagina, tocca **[!UICONTROL Salva tutto]**.

1. Nell&#39;angolo in alto a sinistra della pagina **[!UICONTROL CRXDE Lite]**, tocca l&#39;icona **[!UICONTROL Indietro Home]** per tornare a AEM.

### Modifica di un profilo di codifica video Dynamic Media {#editing-a-video-encoding-profile}

Puoi modificare qualsiasi profilo di codifica video creato per aggiungere, modificare o eliminare i predefiniti video all’interno di tale profilo.

Per impostazione predefinita, non è possibile modificare il profilo predefinito **[!UICONTROL Codifica video adattiva]** fornito con Dynamic Media. Puoi invece copiare facilmente il profilo e salvarlo con un nuovo nome. Puoi quindi modificare i predefiniti desiderati nel profilo copiato.

Vedere anche [Best practice per la codifica video](video.md#best-practices-for-encoding-videos).

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione delle risorse](config-dms7.md#configuring-asset-processing).

**Per modificare un profilo** di codifica video Dynamic Media:

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili video]** , controlla un nome di profilo video.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Modifica]**.
1. Nella pagina **[!UICONTROL Profilo di codifica video]** , modifica il nome e la descrizione desiderati.
1. Come best practice, accertati che la casella di controllo **[!UICONTROL Codifica per streaming adattivo]** sia selezionata.

   Per una descrizione dello streaming adattivo, tocca l’icona delle informazioni. Se stai modificando un profilo video progressivo, non selezionare questa casella di controllo.

1. Nell’intestazione **[!UICONTROL Predefiniti di codifica video]** , aggiungi, modifica o elimina i predefiniti di codifica video che compongono il profilo.

   Toccare l&#39;icona **[!UICONTROL Informazioni]** accanto a ciascuna opzione nelle schede **[!UICONTROL Base]** e **[!UICONTROL Avanzate]** per ottenere descrizioni aggiuntive o impostazioni consigliate in base al codec del formato video selezionato.

1. Nell’angolo in alto a destro della pagina, tocca **[!UICONTROL Salva]**.

### Copia di un profilo di codifica video Dynamic Media {#copying-a-video-encoding-profile}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili video]** , controlla un nome di profilo video.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Copia]**.
1. Nella pagina **[!UICONTROL Profilo di codifica video]** , immetti un nuovo nome per il profilo.
1. Come best practice, accertati che la casella di controllo **[!UICONTROL Codifica per streaming adattivo]** sia selezionata. Per una descrizione dello streaming adattivo, tocca l’icona delle informazioni. Se copi un profilo video progressivo, non selezionare la casella di controllo.

   In modalità Dynamic Media - Hybrid, se un predefinito video WebM fa parte del profilo video, non è possibile codificare **[!UICONTROL per lo streaming adattivo]** perché tutti i predefiniti devono essere MP4.
1. Nell’intestazione **[!UICONTROL Predefiniti di codifica video]** , aggiungi, modifica o elimina i predefiniti di codifica video che compongono il profilo.

   Per le impostazioni e le descrizioni consigliate, tocca l’icona **[!UICONTROL Informazioni]** accanto a ciascuna opzione nelle schede **[!UICONTROL Base]** e **[!UICONTROL Avanzate]** .

1. Nell’angolo in alto a destro della pagina, tocca **[!UICONTROL Salva]**.

### Eliminazione di un profilo di codifica video Dynamic Media {#deleting-a-video-encoding-profile}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Nella pagina **[!UICONTROL Profili video]** , controlla uno o più nomi di profilo video.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Elimina]**.
1. Toccare **[!UICONTROL OK]**.

## Applicazione di un profilo video Dynamic Media alle cartelle {#applying-a-video-profile-to-folders}

Quando assegni un profilo video a una cartella, qualsiasi sottocartella eredita automaticamente il profilo dalla relativa cartella principale. Questo significa che puoi assegnare un solo profilo video a una cartella. Considera attentamente la struttura delle cartelle in cui caricare, archiviare, utilizzare e archiviare le risorse.

Se hai assegnato un profilo video diverso a una cartella, il nuovo profilo sostituisce il profilo precedente. Le risorse della cartella esistenti in precedenza rimangono invariate. Il nuovo profilo viene applicato alle risorse aggiunte successivamente alla cartella.

Le cartelle a cui è assegnato un profilo sono indicate nell&#39;interfaccia utente in base al nome del profilo visualizzato nel nome della scheda.

![chlimage_1-517](assets/chlimage_1-517.png)

Puoi applicare i profili video a cartelle specifiche o globalmente a tutte le risorse.

### Applicazione dei profili video a cartelle specifiche {#applying-video-profiles-to-specific-folders}

Puoi applicare un profilo video a una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come applicare i profili video alle cartelle con entrambe le soluzioni.

Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili video Dynamic Media alle cartelle dall’interfaccia utente Profili {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Seleziona il profilo video da applicare a una o più cartelle.
1. Tocca **[!UICONTROL Applica profilo a cartelle]** e seleziona una o più cartelle da usare per ricevere le risorse appena caricate, quindi fai clic su **[!UICONTROL Applica]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili video Dynamic Media alle cartelle da Proprietà {#applying-video-profiles-to-folders-from-properties}

1. Tocca il logo AEM e passa a **[!UICONTROL Risorse]**, quindi alla cartella a cui desideri applicare un profilo video.
1. Sulla cartella, tocca il segno di spunta per selezionarlo, quindi tocca **[!UICONTROL Proprietà]**.
1. Seleziona la scheda **[!UICONTROL Profili video]** , fai clic sul profilo dal menu a discesa e infine tocca **[!UICONTROL Salva e chiudi]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

   ![chlimage_1-518](assets/chlimage_1-518.png)

### Applicazione globale di un profilo video Dynamic Media {#applying-a-video-profile-globally}

Oltre ad applicare un profilo a una cartella, puoi anche applicarne uno a livello globale in modo che a qualsiasi contenuto caricato AEM risorse in una cartella sia applicato il profilo selezionato.

**Per applicare un profilo video Dynamic Media a livello globale**:

1. Passa a CRXDE Lite al seguente nodo: `/content/dam/jcr:content`.
1. Aggiungi la proprietà **[!UICONTROL videoProfile]**: `/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. Tocca **[!UICONTROL Salva tutto]**.

![chlimage_1-519](assets/chlimage_1-519.png)

## Rimozione di un profilo video Dynamic Media dalle cartelle {#removing-a-video-profile-from-folders}

Quando rimuovi un profilo video da una cartella, tutte le sottocartelle ereditano automaticamente la rimozione del profilo dalla relativa cartella principale. Tuttavia, l’elaborazione dei file che si è verificata all’interno delle cartelle rimane intatta.

Puoi rimuovere un profilo video da una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Impostazioni cartella]**. Questa sezione descrive come rimuovere i profili video dalle cartelle con entrambe le soluzioni.

### Rimozione di profili video Dynamic Media dalle cartelle tramite l’interfaccia utente Profili {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. Tocca il logo AEM e seleziona **[!UICONTROL Strumenti > Risorse > Profili video]**.
1. Seleziona il profilo video da rimuovere da una o più cartelle.
1. Tocca **[!UICONTROL Rimuovi profilo da cartelle]** e seleziona una o più cartelle da cui vuoi rimuovere il profilo, infine tocca **[!UICONTROL Rimuovi]**.

   Puoi confermare che il profilo video non viene più applicato a una cartella perché il nome non viene più visualizzato sotto il nome della cartella.

### Rimozione di profili video Dynamic Media dalle cartelle tramite Proprietà {#removing-video-profiles-from-folders-via-properties}

1. Tocca il logo AEM e vai a **[!UICONTROL Risorse]**, quindi alla cartella da cui vuoi rimuovere un profilo video.
1. Sulla cartella, tocca il segno di spunta per selezionarlo, quindi tocca **[!UICONTROL Proprietà]**.
1. Seleziona la scheda **[!UICONTROL Profili video]** e seleziona **[!UICONTROL Nessuno]** dal menu a discesa, quindi tocca **[!UICONTROL Salva e chiudi]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.
