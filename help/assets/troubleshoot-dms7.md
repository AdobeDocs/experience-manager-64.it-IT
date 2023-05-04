---
title: Risoluzione dei problemi Dynamic Media - Modalità Scene7
description: Risoluzione dei problemi Dynamic Media - Modalità di esecuzione Scene7.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: d8cc94b0-eacf-4e76-bd50-7934bbc28c92
feature: Troubleshooting
role: Admin,User
mini-toc-levels: 3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1431'
ht-degree: 1%

---

# Risoluzione dei problemi Dynamic Media - Modalità Scene7 {#troubleshooting-dynamic-media-scene-mode}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il seguente documento descrive la risoluzione dei problemi relativi all’esecuzione di Dynamic Media **dynamicmedia_scene7** modalità di esecuzione.

## Configurazione e configurazione {#setup-and-configuration}

Assicurati che Dynamic Media sia stato configurato correttamente eseguendo le operazioni seguenti:

* Il comando di avvio contiene `-r dynamicmedia_scene7` argomento runmode.
* Tutti i pacchetti correzioni cumulativi AEM 6.4 (CFP) sono stati installati per primi *prima* tutti i Feature Pack disponibili per Dynamic Media.
* È installato il Feature Pack 18912 opzionale.

   Questo pacchetto di funzioni opzionale è per il supporto FTP o se stai eseguendo la migrazione delle risorse a Dynamic Media da Dynamic Media Classic.

* Passa all’interfaccia utente dei Cloud Services e conferma che l’account predisposto sia visualizzato in **[!UICONTROL Configurazioni disponibili]**.
* Assicurati che **[!UICONTROL Attivazione risorsa Dynamic Media (scene7)]** l&#39;agente di replica è abilitato.

   Questo agente di replica si trova in **[!UICONTROL Agenti]** su Autore.

## Generale (tutte le attività) {#general-all-assets}

Di seguito sono riportati alcuni suggerimenti generali per tutte le risorse.

### Proprietà dello stato di sincronizzazione delle risorse {#asset-synchronization-status-properties}

Le seguenti proprietà delle risorse possono essere riviste in CRXDE Lite per confermare la sincronizzazione della risorsa da AEM a Dynamic Media:

| **Proprietà** | **Esempio** | **Descrizione** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | `a\|364266` | Indicatore generale che il nodo è collegato a Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **[!UICONTROL PublishComplete]** o testo di errore | Stato del caricamento della risorsa in Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | `myCompany/myAssetID` | Deve essere popolato per generare URL per la risorsa remota di Dynamic Media. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | `success` oppure `failed:<error text>` | Stato di sincronizzazione di set (set 360 gradi, set di immagini e così via), predefiniti immagine, predefiniti visualizzatore, aggiornamenti mappa immagine per una risorsa o immagini modificate. |

### Registrazione sincronizzazione {#synchronization-logging}

Errori e problemi di sincronizzazione registrati `error.log` (directory del server AEM `/crx-quickstart/logs/`). È disponibile una registrazione sufficiente per determinare la causa principale della maggior parte dei problemi, tuttavia è possibile aumentare la registrazione in DEBUG sul `com.adobe.cq.dam.ips` pacchetto tramite la console Sling ([http://localhost:4502/system/console/slinglog](http://localhost:4502/system/console/slinglog)) per raccogliere ulteriori informazioni.

### Sposta, copia o elimina {#move-copy-delete}

Prima di eseguire un&#39;operazione Sposta, Copia o Elimina, eseguire le operazioni seguenti:

* Per immagini e video, conferma che un `<object_node>/jcr:content/metadata/dam:scene7ID` esiste prima di eseguire operazioni di spostamento, copia o eliminazione.
* Per i predefiniti per immagini e visualizzatori, verifica che un `https://<server>/crx/de/index.jsp#/etc/dam/presets/viewer/testpreset/jcr%3Acontent/metadata` esiste prima di eseguire operazioni di spostamento, copia o eliminazione.
* Se manca il valore dei metadati sopra riportato, è necessario ricaricare le risorse prima di spostare, copiare o eliminare le operazioni.

### Controllo della versione {#version-control}

Quando sostituisci una risorsa Dynamic Media esistente (nome e posizione identici), puoi mantenere entrambe le risorse o sostituirla o crearne una versione:

* Mantenere entrambi crea una nuova risorsa con un nome univoco per l’URL della risorsa pubblicata. Ad esempio: **[!UICONTROL image.jpg]** è la risorsa originale e **[!UICONTROL image1.jpg]** è la nuova risorsa caricata.

* La creazione di una versione non è supportata nella distribuzione in modalità Dynamic Media - Scene7. La nuova versione sostituisce la risorsa esistente nella consegna.

## Immagini e set {#images-and-sets}

Se riscontri problemi con immagini e set, consulta le seguenti indicazioni per la risoluzione dei problemi.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Problema  </strong></td> 
   <td><strong>Come eseguire il debug</strong></td> 
   <td><strong>Soluzione</strong></td> 
  </tr> 
  <tr> 
   <td>Impossibile accedere al pulsante Copia URL/Incorpora nella visualizzazione dei dettagli della risorsa</td> 
   <td> 
    <ol> 
     <li><p>Vai a CRX/DE:</p> 
      <ul> 
       <li>Controlla se la preimpostazione nel JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> definito. Tieni presente che questa posizione si applica se hai effettuato l’aggiornamento da AEM 6.x a 6.4 e hai rinunciato alla migrazione. In caso contrario, la posizione è <code>/conf/global/settings/dam/dm/presets/viewer</code>.</li> 
       <li>Controlla che la risorsa nel JCR sia dotata di <code>dam:scene7FileStatus</code><strong> </strong>in Metadati viene visualizzato come <code>PublishComplete</code>.</li> 
      </ul> </li> 
    </ol> </td> 
   <td><p>Aggiorna pagina/passa a un'altra pagina e torna (la barra laterale JSP deve essere ricompilata)</p> <p>Se questo non funziona:</p> 
    <ul> 
     <li>Pubblica la risorsa.</li> 
     <li>Ricarica e pubblica la risorsa.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Selettore risorse nell’editor impostato bloccato nel caricamento perpetuo</td> 
   <td><p>Problema noto da risolvere in 6.4</p> </td> 
   <td><p>Chiudi il selettore e riaprilo.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Seleziona</strong> il pulsante non è attivo dopo aver selezionato una risorsa come parte della modifica di un set</td> 
   <td><p> </p> <p>Problema noto da risolvere in 6.4</p> <p> </p> </td> 
   <td><p>Fai clic prima su un’altra cartella nel Selettore risorse e torna indietro per selezionare la risorsa.</p> </td> 
  </tr> 
  <tr> 
   <td>Il punto attivo del carosello si sposta dopo il passaggio tra le diapositive</td> 
   <td><p>Verificare che tutte le diapositive abbiano le stesse dimensioni.</p> </td> 
   <td><p>Utilizza solo immagini con la stessa dimensione per il carosello.</p> </td> 
  </tr> 
  <tr> 
   <td>L’immagine non viene visualizzata in anteprima con il visualizzatore Dynamic Media</td> 
   <td><p>Verifica che la risorsa contenga <code>dam:scene7File</code> nelle proprietà Metadati (CRXDE Lite)</p> </td> 
   <td><p>Verifica che tutte le risorse abbiano completato l’elaborazione.</p> </td> 
  </tr> 
  <tr> 
   <td>La risorsa caricata non viene visualizzata nel selettore delle risorse</td> 
   <td><p>Verificare che la risorsa abbia una proprietà <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)</p> </td> 
   <td><p>Verifica che tutte le risorse abbiano completato l’elaborazione.</p> </td> 
  </tr> 
  <tr> 
   <td>Mostra banner nella vista a schede <strong>Nuovo</strong> quando la risorsa non ha iniziato l’elaborazione</td> 
   <td>Controlla risorsa <code>jcr:content</code> &gt; <code>dam:assetState</code> = if <code>unprocessed</code> non è stato rilevato dal flusso di lavoro.</td> 
   <td>Attendi che la risorsa venga raccolta dal flusso di lavoro.</td> 
  </tr> 
  <tr> 
   <td>Le immagini o i set non visualizzano l’URL o il codice di incorporamento del visualizzatore</td> 
   <td>Controlla se il predefinito per visualizzatori è stato pubblicato.</td> 
   <td><p>Vai a <strong>Strumenti</strong> &gt; <strong>Risorse</strong> &gt; <strong>Predefiniti visualizzatore</strong> e pubblica il predefinito visualizzatore.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Video {#video}

In caso di problemi con il video, consulta le seguenti indicazioni per la risoluzione dei problemi.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Problema  </strong></td> 
   <td><strong>Come eseguire il debug</strong></td> 
   <td><strong>Soluzione</strong></td> 
  </tr> 
  <tr> 
   <td>Impossibile visualizzare in anteprima il video</td> 
   <td> 
    <ul> 
     <li>Verifica che alla cartella sia assegnato un profilo video (se non è supportato). Se non è supportato, viene visualizzata solo un’immagine.</li> 
     <li>Il profilo video deve contenere più di un predefinito di codifica per generare un set AVS (le codifiche singole vengono considerate come contenuto video per i file MP4; per i file non supportati, trattati come non elaborati).</li> 
     <li>Verifica che l’elaborazione del video sia stata completata tramite la conferma <code>dam:scene7FileAvs</code> di <code>dam:scene7File</code> nei metadati.</li> 
    </ul> </td> 
   <td> 
    <ol> 
     <li>Assegna un profilo video alla cartella.</li> 
     <li>Modifica il profilo video per includere più di un predefinito di codifica.</li> 
     <li>Attendere il completamento dell'elaborazione del video.</li> 
     <li>Ricarica il video e assicurati che il flusso di lavoro Codifica video di Dynamic Media non sia in esecuzione.<br /> </li> 
     <li>Ricarica il video.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Il video non è codificato</td> 
   <td> 
    <ul> 
     <li>Verifica che la modalità di esecuzione sia <span class="kbd">dynamicmedia_scene7</span>.</li> 
     <li>Verifica se il servizio cloud Dynamic Media è configurato.</li> 
     <li>Controlla se un profilo video è associato alla cartella di caricamento.</li> 
    </ul> </td> 
   <td> 
    <ol> 
     <li>Controlla la tua istanza AEM con <span class="kbd">-r dinamicmedia_scene7</span></li> 
     <li>Verifica che la configurazione di Dynamic Media in Cloud Services sia configurata correttamente.</li> 
     <li>Verifica che la cartella disponga di un profilo video. Inoltre, controlla il profilo video.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>L'elaborazione video richiede troppo tempo</td> 
   <td><p>Per determinare se la codifica video è ancora in corso o se è stato immesso uno stato di errore:</p> 
    <ul> 
     <li>Controllare lo stato del video <code>http://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <span class="kbd">dam:assetState</span></li> 
     <li>Monitorare il video dalla console del flusso di lavoro <code>http://localhost:4502/libs/cq/workflow/content/console.html</code> &gt; Schede Istanze, Archivio, Errori.</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Rendering video mancante</td> 
   <td><p>Quando il video viene caricato, ma non sono presenti rappresentazioni codificate:</p> 
    <ul> 
     <li>Verifica che alla cartella sia assegnato un profilo video.</li> 
     <li>Verifica che l’elaborazione del video sia stata completata tramite la conferma <code>dam:scene7FileAvs</code> nei metadati.</li> 
    </ul> </td> 
   <td> 
    <ol> 
     <li>Assegna un profilo video alla cartella.</li> 
     <li>Attendere il completamento dell'elaborazione del video.<br /> </li> 
    </ol> </td> 
  </tr> 
 </tbody> 
</table>

## Visualizzatori {#viewers}

Se riscontri problemi con i visualizzatori, consulta le seguenti indicazioni per la risoluzione dei problemi.

### Problema: I predefiniti visualizzatore non sono pubblicati {#viewers-not-published}

**Come eseguire il debug**

1. Passare alla pagina di diagnostica di sample manager: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`.
1. Osserva i valori calcolati. Quando funziona correttamente, vedi quanto segue: `_DMSAMPLE status: 0 unsyced assets - activation not necessary _OOTB status: 0 unsyced assets - 0 unactivated assets`.

   >[!NOTE]
   >
   >La sincronizzazione delle risorse del visualizzatore può richiedere circa 10 minuti dopo la configurazione delle impostazioni cloud di Dynamic Media.

1. Se le risorse non attivate rimangono, seleziona una delle seguenti opzioni **Elenca tutte le risorse non attivate** per visualizzare i dettagli.

**Soluzione**

1. Passa all’elenco dei predefiniti per visualizzatori in strumenti di amministrazione: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`
1. Seleziona tutti i predefiniti visualizzatore, quindi seleziona **Pubblica**.
1. Torna a Sample manager e osserva che il conteggio delle risorse non attivate è ora zero.

### Problema: L’immagine predefinita del visualizzatore restituisce 404 da Anteprima nei dettagli della risorsa o Copia URL/Incorpora codice {#viewer-preset-404}

**Come eseguire il debug**

In CRXDE Lite procedi come segue:

1. Passa a `<sync-folder>/_CSS/_OOTB` cartella all’interno della cartella di sincronizzazione Dynamic Media (ad esempio, `/content/dam/_CSS/_OOTB`).
1. Trova il nodo di metadati della risorsa problematica (ad esempio, `<sync-folder>/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/`).
1. Verifica la presenza di `dam:scene7*` proprietà. Se la risorsa è stata sincronizzata e pubblicata correttamente, viene visualizzata la `dam:scene7FileStatus` impostato su **PublishComplete**.
1. Tentativo di richiedere l’immagine direttamente da Dynamic Media concatenando i valori delle seguenti proprietà e valori letterali stringa:

   * `dam:scene7Domain`
   * `"is/content"`
   * `dam:scene7Folder`
   * `<asset-name>`
Esempio: 
`https://<server>/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png`

**Soluzione**

Se le risorse di esempio o l’immagine predefinita del visualizzatore non sono sincronizzate o pubblicate, riavvia l’intero processo di copia/sincronizzazione:

1. Passa a CRXDE Lite.
1. Eliminare `<sync-folder>/_CSS/_OOTB`.
1. Passa a Gestione pacchetti CRX: `https://localhost:4502/crx/packmgr/`.
1. Cerca il pacchetto visualizzatore nell&#39;elenco; inizia con `cq-dam-scene7-viewers-content`.
1. Seleziona **Reinstalla**.
1. In Cloud Services, accedi alla pagina Configurazione Dynamic Media, quindi apri la finestra di dialogo di configurazione per la configurazione Dynamic Media - S7.
1. Non apportare modifiche, seleziona **Salva**.
Questa azione di salvataggio attiva nuovamente la logica per creare e sincronizzare le risorse di esempio, i CSS predefiniti per visualizzatori e le immagini.

### Problema: L’anteprima dell’immagine non viene caricata nella creazione dei predefiniti visualizzatore {#image-preview-not-loading}

**Soluzione**

1. In Experience Manager, seleziona il logo Experience Manager per accedere alla console di navigazione globale, quindi accedi a . **[!UICONTROL Strumenti]** > **[!UICONTROL Generale]** > **[!UICONTROL CRXDE Lite]**.
1. Nella barra a sinistra, accedi alla cartella del contenuto di esempio nella posizione seguente:

   `/content/dam/_DMSAMPLE`

1. Elimina `_DMSAMPLE` cartella.
1. Nella barra a sinistra, accedi alla cartella dei predefiniti nel seguente percorso:

   `/conf/global/settings/dam/dm/presets/viewer`

1. Elimina `viewer` cartella.
1. Nell’angolo in alto a sinistra della pagina CRXDE Lite, seleziona **[!UICONTROL Salva tutto]**.
1. Nell’angolo in alto a sinistra della pagina CRXDE Lite, seleziona la **Pagina principale** icona.
1. Ricrea un [Configurazione Dynamic Media nei Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services).
