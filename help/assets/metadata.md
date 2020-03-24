---
title: Gestione dei metadati delle risorse digitali
description: Scopri i tipi di metadati e come Risorse Adobe Experience Manager consente di gestire i metadati per le risorse per facilitarne la categorizzazione e l’organizzazione. Grazie alla possibilità di gestire e mantenere metadati arbitrari con le risorse, Risorse Adobe Experience Manager consente di organizzare ed elaborare automaticamente le risorse in base ai metadati.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5ef4c4e42165819191c6e3810c36183110f3f34a

---


# Gestione dei metadati delle risorse digitali {#managing-metadata-for-digital-assets}

Risorse Adobe Experience Manager conserva i metadati per ogni risorsa. Questo consente di suddividere le risorse in categorie e organizzarle in modo più semplice e aiuta le persone che cercano una risorsa specifica. Grazie alla possibilità di estrarre i metadati dai file caricati in Experience Manager Assets, la gestione dei metadati si integra con il flusso di lavoro creativo. Grazie alla capacità di Experience Manager di mantenere e gestire i metadati con le risorse, puoi organizzare ed elaborare automaticamente le risorse in base ai metadati.

* [Metadati XMP](xmp.md)
* [Come modificare o aggiungere i metadati](meta-edit.md)
* [Riferimento schemi metadati](meta-ref.md)

## Perché abbiamo bisogno di metadati {#why-we-need-metadata}

Metadati significa dati sui dati. A questo proposito, i dati si riferiscono alla risorsa digitale, ad esempio un&#39;immagine. I metadati sono fondamentali per una gestione efficiente delle risorse.

I metadati sono la raccolta di tutti i dati disponibili per una risorsa, ma non necessariamente contenuti in tale immagine. Alcuni esempi di metadati sono:

* Nome della risorsa.
* Ora e data dell’ultima modifica.
* Dimensione della risorsa così come è stata memorizzata nella directory archivio.
* Nome della cartella in cui è contenuta.
* Risorse correlate o tag applicati.

Queste sono le proprietà di metadati di base che Experience Manager è in grado di gestire per le risorse. Questo consente agli utenti di visualizzare tutte le risorse, ad esempio, ordinate in base alla data dell’ultima modifica, utile per scoprire quali risorse sono state aggiunte di recente alla directory archivio.

Puoi aggiungere più dati di alto livello alle risorse digitali, ad esempio:

* Tipo di risorsa (è un’immagine, un video, una clip audio o un documento?).
* Proprietario della risorsa.
* Titolo della risorsa.
* Descrizione della risorsa.
* Tag assegnati a una risorsa.

Più metadati consentono di classificare ulteriormente le risorse ed è utile man mano che cresce la quantità di informazioni digitali. È possibile gestire poche centinaia di file in base solo ai nomi dei file. Tuttavia, questo approccio non è scalabile e si riduce rapidamente quando il numero di persone coinvolte e il numero di risorse gestite aumenta.

Man mano che i metadati vengono aggiunti alle risorse, il valore della risorsa aumenta, poiché diventa,

* più accessibile - la gente può trovarlo molto più facile.
* gestione più semplice: è possibile trovare più facilmente le risorse con lo stesso set di proprietà e apportare loro le modifiche necessarie.
* più complessi: più metadati sono stati aggiunti a una risorsa, più importante sarà la gestione dei metadati.

Per questi motivi, Experience Manager Assets offre i mezzi giusti per creare, gestire e scambiare metadati per le risorse digitali.

## Tipi di metadati {#types-of-metadata}

I due tipi di metadati di base sono i metadati tecnici e i metadati descrittivi.

I metadati tecnici sono utili per le applicazioni software che si occupano di risorse digitali e non devono essere mantenuti manualmente. Experience Manager Assets e altri software determinano automaticamente i metadati tecnici e i metadati potrebbero essere modificati al momento della modifica della risorsa. I metadati tecnici disponibili per una risorsa dipendono in larga misura dal tipo di file della risorsa. Alcuni esempi di metadati tecnici sono:

* Dimensioni di un file
* Dimensioni (altezza e larghezza) di un’immagine
* Bitrate di un file audio o video
* Risoluzione (livello di dettaglio) di un&#39;immagine

I metadati descrittivi sono metadati relativi al dominio applicazione, ad esempio l’azienda da cui proviene una risorsa. I metadati descrittivi non possono essere determinati automaticamente. Viene creato manualmente o semi-automaticamente. Ad esempio, una fotocamera GPS può tracciare automaticamente latitudine e longitudine e aggiungere il geotag all&#39;immagine.

A causa dell&#39;alto costo del lavoro manuale necessario per creare informazioni descrittive sui metadati, sono stati definiti standard per facilitare lo scambio di metadata tra i sistemi software e le organizzazioni.

Experience Manager Assets supporta tutti gli standard pertinenti per la gestione dei metadati.

Data l&#39;importanza dei metadata e l&#39;elevato coinvolgimento manuale necessario per creare i metadata, sono stati definiti standard che semplificano lo scambio.

## Standard di codifica {#encoding-standards}

Esistono diversi modi per incorporare i metadati nei file. Sono supportati alcuni standard di codifica:

* XMP: utilizzato da Experience Manager Assets per archiviare i metadati estratti nell’archivio.
* ID3: per i file audio e video.
* Exif: per i file di immagine.
* Altro/Legacy: da Microsoft Word, PowerPoint, Excel e così via.

### XMP {#xmp}

XMP (Extensible Metadata Platform) è uno standard aperto utilizzato da Experience Manager Assets per la gestione di tutti i metadati. Lo standard offre una codifica universale dei metadati che può essere incorporata in tutti i formati di file. Adobe e altre società supportano lo standard XMP in quanto fornisce un modello di contenuto avanzato. Gli utenti dello standard XMP e di Experience Manager Assets dispongono di una piattaforma potente su cui basarsi. For more information, see [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

I dati memorizzati in questi tag ID3 vengono visualizzati quando si riproduce un file audio digitale sul computer o su un lettore MP3 portatile.

I tag ID3 sono progettati per il formato di file MP3. Ulteriori informazioni sui formati:

* I tag ID3 funzionano nei file MP3 e mp3PRO.
* WAV non ha tag.
* WMA dispone di tag proprietari che non consentono l&#39;implementazione open-source.
* Ogg Vorbis utilizza i commenti Xiph incorporati nel contenitore Ogg.
* AAC utilizza un formato di tag proprietario.

### Exif {#exif}

Exchangeable image file format (Exif) è il formato di metadati più diffuso utilizzato nella fotografia digitale. Fornisce un modo per incorporare un vocabolario fisso di proprietà di metadati in molti formati di file, come JPEG, TIFF, RIFF e WAV. Exif memorizza i metadati come coppie di un nome di metadati e di un valore di metadati. Queste coppie nome-valore di metadati sono anche denominate tag, da non confondere con i tag in Experience Manager. Exif viene creato automaticamente dalle moderne fotocamere digitali e viene supportato dai moderni software grafici, e può essere considerato il denominatore più basso per la gestione dei metadata.

Un importante limite di Exif è dato dal fatto che alcuni formati di file immagine popolari come BMP, GIF o PNG non lo supportano.

I campi di metadati generalmente definiti da Exif sono di natura tecnica e sono di utilizzo limitato per la gestione dei metadati descrittivi. Per questo motivo, Experience Manager Assets offre la mappatura delle proprietà Exif in schemi [di metadati](metadata-schemas.md) comuni e in [XMP](xmp-writeback.md).

### Altri metadati {#other-metadata}

Altri metadati che possono essere incorporati dai file sono Microsoft Word, PowerPoint, Excel e così via.

## Schemi metadati {#metadata-schemata}

Gli schemi di metadati sono set predefiniti di definizioni di proprietà di metadati utilizzabili in varie applicazioni. Le proprietà sono sempre associate a una risorsa, il che significa che le proprietà sono &quot;informazioni sulla risorsa&quot;.

Potete anche progettare i vostri schemi di metadati, se non ne esiste uno che soddisfi le vostre esigenze. Non duplicare le informazioni esistenti. La separazione degli schemi all&#39;interno di un&#39;organizzazione semplifica la condivisione dei metadati. Experience Manager fornisce un elenco predefinito degli schemi di metadati più comuni. L’elenco consente di iniziare nuovamente la strategia dei metadati e di scegliere rapidamente le proprietà di metadati necessarie.

Gli schemi di metadati supportati sono elencati di seguito.

### Metadati standard {#standard-metadata}

* dc - Dublin Core - il set di metadati più importante e ampiamente utilizzato.
* DICOM - Digital Imaging and Communications in Medicine.
* Iptc4xmpCore &amp; iptc4xmpExt - International Press Communications Standard - molti metadati specifici per oggetto.
* rdf - Framework di descrizione delle risorse - per metadati Web semantici generici.
* xmp - Piattaforma di metadati estensibile.
* xmpBJ - Job Ticketing di base.

### Metadati specifici per l’applicazione {#application-specific-metadata}

I metadati specifici dell&#39;applicazione includono metadati tecnici e descrittivi. Se utilizzate queste opzioni, altre applicazioni potrebbero non essere in grado di utilizzare i metadati. Ad esempio, se disponete di una risorsa con metadati Adobe Photoshop e un’altra applicazione per il rendering delle immagini tenta di accedere ai metadati, potrebbe non essere in grado di accedere ai metadati. Se nelle risorse sono presenti molti metadati specifici per l’applicazione, potete creare un passaggio del flusso di lavoro che modifica una proprietà specifica per l’applicazione in una proprietà standard.

* acdsee - metadati gestiti dal programma ACDSee [www.acdsee.com/](https://www.acdsee.com/).
* album - Adobe Photoshop Album.
* cq - utilizzato da Experience Manager Assets.
* dam, utilizzato da Experience Manager Assets.
* dex - Optima SC Description Explorer.
* crs - Adobe Photoshop Camera Raw.
* lr - Adobe Lightroom.
* mediapro - IView MediaPro.
* MicrosoftPhoto e MP - Microsoft Photo.
* pdf e pdfx
* photoshop &amp; psAux - Adobe Photoshop

### Metadati Digital Rights Management {#digital-rights-management-metadata}

* cc - creative commons
* xmpRights
* più - Sistema universale di gestione delle immagini - https://www.useplus.com/
* prisma - https://www.idealliance.org/prism-metadata di pubblicazione per metadati standard di settore
* prl - Prism
* pur - Diritti di utilizzo Prism
* xmpPlus - integrazione di PLUS con XMP

### Metadati specifici per la fotografia {#photography-specific-metadata}

* exif - molte informazioni tecniche dalla telecamera, inclusa la posizione GPS
* crs - photoshop camera raw
* Iptc4xmpCore e iptc4xmpExt
* TIFF - Metadati immagine (non solo per le immagini TIFF)

### Metadati specifici per la stampa {#print-specific-metadata}

* pdf e pdfx - Adobe PDF e applicazioni di terze parti
* prisma - [www.prismstandard.org](https://www.prismstandard.org) di pubblicazione DPS per metadati standard di settore
* XMP
* xmpPG - xmp per il testo in pagine

### Metadati multimediali specifici {#multimedia-specific-metadata}

* xmpDM - Contenuti multimediali dinamici
* xmpMM - Gestione dei supporti

## Flussi di lavoro basati su metadati {#metadata-driven-workflows}

La creazione di flussi di lavoro basati su metadati consente di automatizzare alcuni processi, migliorando l&#39;efficienza. In un flusso di lavoro basato su metadati, il sistema di gestione del flusso di lavoro legge il flusso di lavoro ed esegue quindi alcune azioni predefinite. Ad esempio, potete usare alcuni dei flussi di lavoro basati su metadati:

* Il flusso di lavoro può verificare se un’immagine ha un titolo. In caso contrario, il sistema avvisa un utente specifico di aggiungere un titolo.
* Il flusso di lavoro può verificare se una notifica di copyright su una risorsa consente la distribuzione. In caso contrario, il sistema invia la risorsa a un server. In caso contrario, il sistema invia la risorsa a un altro server.
* Un flusso di lavoro può controllare le risorse senza metadati obbligatori predefiniti o con metadati *non validi* .
