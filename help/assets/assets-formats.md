---
title: Formati di file supportati in AEM Assets
description: Elenco dei formati di file e dei tipi MIME supportati da AEM Assets e delle funzioni supportate per ciascun formato.
contentOwner: AG
feature: Gestione risorse, rappresentazioni
role: Business Practices, Amministratore
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 10%

---


# Formati di file supportati in AEM Assets {#assets-supported-formats}

AEM Assets supporta un’ampia gamma di formati di file e ogni funzionalità supporta diversi tipi MIME.

Per integrare AEM Assets con altre soluzioni di gestione delle risorse digitali (DAM) conformi agli standard e con il software desktop, utilizza l’Extensible Metadata Platform (XMP) di Adobe.

Utilizza la legenda per comprendere il livello di supporto.

| Livello di supporto | Descrizione |
|:---:|---|
| . | Supportata |
| * | Supportato con funzioni aggiuntive |
| - | Non applicabile |

## Formati immagine raster {#supported-raster-image-formats}

I formati immagine raster supportati per le funzioni di gestione delle risorse sono i seguenti:

| Formato | Archiviazione | Gestione dei metadati | Estrazione di metadati | Generazione di miniature | Modifica interattiva | Write-back metadati | Approfondimenti |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | . | . | . | . | . | . | . |
| GIF | . | . | . | . | . |  | . |
| TIFF | . | . | . | . |  | . | . |
| JPEG | . | . | . | . | . | . | . |
| BMP | . | . | . | . | . |  | . |
| PNM | . | . |  |  |  |  | . |
| PGM | . | . |  |  |  |  | . |
| PBM | . | . |  |  |  |  | . |
| PPM | . | . |  |  |  |  | . |
| PSD **** | . | . | . | . |  |  | . |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | . | . | . | . |  | . |  |
| PICT |  |  |  |  |  |  | . |
| PSB | . | . | . | . |  |  |  |

**** L&#39;immagine unita viene estratta dal file PSD. Si tratta di un’immagine generata da Adobe Photoshop e inclusa nel file PSD. A seconda delle impostazioni, l’immagine unita potrebbe essere o meno l’immagine effettiva.

I formati immagine raster supportati per le funzioni Dynamic Media sono i seguenti:

| Formato | Upload<br> (formato di input) | Crea<br> immagine<br> preset<br> (formato di output) | Rendering Preview<br> dinamico<br> | Rendering <br> dinamico<br> | Rendering Download<br> dinamico<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | . | . | . | . | . |
| GIF | . | . | . | . | . |
| TIFF | . | . | . | . | . |
| JPEG | . | . | . | . | . |
| BMP | . |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **** | . |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | . | . | . | . | . |
| PICT | . |  |  |  |  |
| PSB |  |  |  |  |  |

**** L&#39;immagine unita viene estratta dal file PSD. Si tratta di un’immagine generata da Adobe Photoshop e inclusa nel file PSD. A seconda delle impostazioni, l’immagine unita potrebbe essere o meno l’immagine effettiva.

Oltre alle informazioni di cui sopra, considera quanto segue:

* Il supporto per i file EPS si applica solo alle immagini raster. Ad esempio, la generazione di miniature per le immagini vettoriali EPS non è supportata per impostazione predefinita. Per aggiungere supporto, [configura ImageMagick](best-practices-for-imagemagick.md). Per integrare strumenti di terze parti per abilitare funzionalità aggiuntive, consulta [Gestore multimediale basato su riga di comando](media-handlers.md#command-line-based-media-handler).

* Il write-back di metadati funziona per il formato di file PSB quando viene aggiunto al gestore `NComm`.

* Per utilizzare Dynamic Media per visualizzare in anteprima e generare rappresentazioni dinamiche per i file EPS, vedere [Formati di file Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Per i file EPS, il write-back di metadati è supportato nella versione 3.0 o successiva della convenzione di struttura dei documenti PostScript (PS-Adobe).

## Formati immagine raster non supportati in Dynamic Media {#unsupported-image-formats-dynamic-media}

L&#39;elenco seguente descrive i sottotipi di formati di file immagine raster *non* supportati in Dynamic Media.

Vedere anche [Rilevamento di formati di file non supportati per Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* File PNG con una dimensione del blocco IDAT superiore a 100 MB.
* File PSB.
* I file PSD con uno spazio colore diverso da CMYK, RGB, Scala di grigio o Bitmap non sono supportati. Gli spazi colore DuoTone, Lab e Indexed non sono supportati.
* File PSD con una profondità di bit maggiore di 16.
* File TIFF con dati a virgola mobile.
* File TIFF con spazio colore Lab.

## Libreria PDF Rasterizer {#supported-pdf-rasterizer-library}

La libreria Adobe PDF Rasterizer genera miniature e anteprime di alta qualità per file Adobe Illustrator e PDF di grandi dimensioni e ad alta intensità di contenuto. L&#39;Adobe consiglia di utilizzare la libreria PDF Rasterizer per le seguenti operazioni:

* File AI/PDF ad alta intensità di contenuto che richiedono un&#39;elaborazione intensiva di risorse.
* File AI/PDF, per i quali le miniature non sono generate per impostazione predefinita.
* File AI con colori Pantone Matching System (PMS).

Vedere [Uso di PDF Rasterizer](aem-pdf-rasterizer.md).

## Libreria di transcodifica delle immagini {#supported-image-transcoding-library}

La libreria di transcodifica delle immagini di Adobe è una soluzione di elaborazione delle immagini che esegue funzioni di base per la gestione delle immagini quali codifica, transcodifica, ricampionamento e ridimensionamento.

La libreria di transcodifica delle immagini supporta i tipi MIME JPG/JPEG, PNG (8-bit e 16-bit), GIF, BMP, TIFF/Compress TIFF (a parte i file TIFF a 32 bit e i file PTIFF), ICO e ICN.

Consulta [Imaging Transcoding Library](imaging-transcoding-library.md).

## Camera Raw {#supported-camera-raw}

La libreria Adobe Camera Raw consente ad AEM Assets di acquisire immagini crude. Consulta [Supporto Camera Raw](camera-raw.md).

## Formati di documenti {#supported-document-formats}

I formati dei documenti supportati per le funzioni di gestione delle risorse sono i seguenti:

| Formato | Archiviazione | Gestione dei metadati<br> | Estrazione full text<br> | Estrazione metadati<br> | Generazione di miniature<br> | Estrazione subasset<br> | Metadata<br> writeback |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | . | . |  | . | . | . | . |
| DOC | . | . | . | . |  |  |  |
| DOCX | . | . | . | . |  |  |  |
| ODT | . | . | . |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | . | . | . | . | . | . | . |
| HTML | . | . | . |  |  |  |  |
| RTF | . | . | . |  |  |  |  |
| TXT | . | . | . |  |  |  |  |
| XLS | . | . | . |  |  |  |  |
| XLSX | . | . | . | . |  |  |  |
| ODS | . | . | . |  |  |  |  |
| PPT | . | . | . | . | . | . |  |
| PPTX | . | . | . | . | . | . |  |
| ODP | . | . | . |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | . | . |  | . | . | . | . |
| PS | . | . |  |  |  |  |  |
| QXP | . | . |  |  |  |  |  |
| EPUB | . | . |  | . | . |  |  |

I formati dei documenti supportati per le funzioni Dynamic Media sono i seguenti:

| Formato | Upload<br> (formato di input) | Crea<br> immagine<br> preset<br> (formato di output) | Rendering Preview<br> dinamico<br> | Rendering <br> dinamico<br> | Rendering Download<br> dinamico<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | . |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | . | . | . | . | . |
| HTML |  |  |  |  |  |
| TTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | . |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

Oltre alla funzionalità di cui sopra, considera quanto segue:

* Per utilizzare Dynamic Media per generare rappresentazioni dinamiche per i file PDF, vedere [Formati di file Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Per utilizzare Dynamic Media per visualizzare in anteprima e generare rappresentazioni dinamiche per i file AI, consulta [Formati di file Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Per utilizzare Dynamic Media per generare rappresentazioni dinamiche per i file INDD, vedere [Formato file InDesign (INDD)](../assets/managing-image-presets.md#indesign-indd-file-format).

## Formati multimediali {#supported-multimedia-formats}

| Formato | Archiviazione | Gestione dei metadati | Estrazione di metadati | Generazione di miniature | Transcodifica FFMPEG |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | . | . |  | - | * |
| MIDI | . | . |  | - | * |
| 3GP | . | . |  | - | * |
| MP3 | . | . | . | - | * |
| MPG | . | . |  | - | * |
| OGA | . | . |  | - | * |
| OGG | . | . |  | - | * |
| RA | . | . |  | - | * |
| WAV | . | . |  | - | * |
| WMA | . | . |  | - | * |
| DVI | . | . |  | * | * |
| FLV | . | . |  | * | * |
| M4V | . | . |  | * | * |
| MPEG | . | . |  | * | * |
| OGV | . | . |  | * | * |
| MOV | . | . |  | * | * |
| WMV | . | . |  | * | * |
| SWF | . | . |  |  |  |

## Formati video di input per la transcodifica Dynamic Media {#supported-input-video-formats-for-dynamic-media-transcoding}

| Estensione file video | Contenitore | Codec video consigliati | Codec video non supportati |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (tutti i profili) |  |
| MOV, QT | QuickTime Apple | H264/AVC, Apple ProRes422 e HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Animazione Apple |
| FLV, F4V | Flash Adobe | H264/AVC, Flix VP6, H263, Sorenson | SWF (file di animazione vettoriale) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | Interleave A/V | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Video a barre rosse | MJPEG 2000 |  |
| RAM, RM | Video reale | Non supportato | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Flac nativo | Codec audio senza perdita |  |
| MJ2 | Motion JPEG 2000 | Codec Motion JPEG 2000 |  |

## Formati di archivio {#supported-archive-formats}

I formati di archivio supportati e l’applicabilità dei flussi di lavoro DAM comuni sono descritti nella tabella seguente.

| Formato | Archiviazione | Gestione versioni | Flusso di lavoro | Pubblicazione | Controllo accesso | Consegna Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | . | . | . | . | . |  |
| JAR | . | . | . | . | . |  |
| RAR | . | . | . | . | . |  |
| TAR | . | . | . | . | . |  |
| ZIP **†** | . | . | . | . | . | . |

**†** L&#39;immagine unita viene estratta dal file PSD. Si tratta di un’immagine generata da Adobe Photoshop e inclusa nel file PSD. A seconda delle impostazioni, l’immagine unita potrebbe essere o meno l’immagine effettiva. Gli archivi ZIP creati con l&#39;algoritmo `Deflate64` hanno un supporto limitato in AEM. Le operazioni di archiviazione e annullamento dell’archiviazione non sono supportate. Tuttavia, sono supportate operazioni come il caricamento, la navigazione e il download.

## Altri formati supportati {#other-supported-formats}

L’applicabilità dei flussi di lavoro DAM comuni per alcuni altri formati di file è descritta nella tabella seguente.

| Formato | Archiviazione | Gestione versioni | Flusso di lavoro | Pubblicazione | Controllo accesso | Consegna Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | . | . | . | . | . |  |
| SVG | . | . | . | . | . |  |
| CSS | . | . | . | . | . | . |
| VTT | . | . | . | . | . | . |
| XML | . | . | . | . | . | . |
| JavaScript (se configurato con un proprio dominio di consegna) |  |  |  |  |  | . |

**#** Gli altri formati sono supportati in DAM per l’archiviazione, il controllo delle versioni, ACL, il flusso di lavoro, la pubblicazione e la gestione dei metadati.

## Tipi MIME supportati {#supported-mime-types}

Per impostazione predefinita, AEM rileva il tipo di file utilizzando l’estensione file. AEM rilevarlo dal contenuto dei file. Per quest&#39;ultimo, seleziona l&#39;opzione [!UICONTROL Rileva MIME dal contenuto] in [!UICONTROL Servizio Day CQ DAM Mime Type Service] nella console Web AEM.

In CRXDE Lite è disponibile un elenco dei tipi MIME supportati all’indirizzo `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

| Estensione file | Tipo MIME/tipo di supporto Internet | Valore jobParam predefinito | Valore jobParam consentito |
|---|---|---|---|
| Immagine | immagine/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | Il jobParam predefinito si applica a tutte le risorse di tipo mime immagine.<ul><li>[knockoutBackgroundOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unSharpMaskOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>application/eps</li><li>application/x-eps</li><li>immagine/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | immagine/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| TTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Abilita il supporto](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support) dei parametri di processo di caricamento di Assets/Dynamic Media Classic basati su tipi MIME.
>* [Configura basato su tipo MIME per il supporto](config-dynamic.md) dei parametri dei processi di caricamento.

