---
title: Formati di file supportati in  AEM Assets
description: Elenco dei formati di file e dei tipi MIME supportati da  AEM Assets e delle funzioni supportate per ciascun formato.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 2baa172088f646752e85168d432d46942ac8244e
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 9%

---


# Formati di file supportati  AEM Assets {#assets-supported-formats}

 AEM Assets supporta un&#39;ampia gamma di formati di file e ogni funzionalità supporta vari tipi MIME.

Per integrare  AEM Assets con altre soluzioni di gestione delle risorse digitali (DAM) conformi agli standard e software desktop, utilizzate  Adobe  Extensible Metadata Platform (XMP).

Utilizzate la legenda per comprendere il livello di supporto.

| Livello di supporto | Descrizione |
|:---:|---|
| AND | Supportato |
| * | Supportato con le funzioni del componente aggiuntivo |
| - | Non applicabile |

## Formati immagine raster {#supported-raster-image-formats}

I formati immagine raster supportati per le funzioni di gestione delle risorse sono i seguenti:

| Formato | Archiviazione | Gestione dei metadati | Estrazione di metadati | Generazione delle miniature | Modifica interattiva | Write-back metadati | Approfondimenti |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | AND | AND | AND | AND | AND | AND | AND |
| GIF | AND | AND | AND | AND | AND |  | AND |
| TIFF | AND | AND | AND | AND |  | AND | AND |
| JPEG | AND | AND | AND | AND | AND | AND | AND |
| BMP | AND | AND | AND | AND | AND |  | AND |
| PNM | AND | AND |  |  |  |  | AND |
| PGM | AND | AND |  |  |  |  | AND |
| PBM | AND | AND |  |  |  |  | AND |
| PPM | AND | AND |  |  |  |  | AND |
| PSD **†** | AND | AND | AND | AND |  |  | AND |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | AND | AND | AND | AND |  | AND |  |
| PICT |  |  |  |  |  |  | AND |
| PSB | AND | AND | AND | AND |  |  |  |

**†** L&#39;immagine unita viene estratta dal file PSD. Si tratta di un&#39;immagine generata da  Adobe Photoshop e inclusa nel file PSD. A seconda delle impostazioni, l’immagine unita potrebbe essere l’immagine effettiva o meno.

I formati immagine raster supportati dalle funzioni Dynamic Media sono i seguenti:

| Formato | Upload<br> (formato di ingresso) | Crea<br> immagine<br> predefinito<br> (formato di output) | Rendering di Preview<br> dynamic<br> | Distribuzione di rappresentazioni dinamiche<br><br> | Download della rappresentazione<br> dinamica<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | AND | AND | AND | AND | AND |
| GIF | AND | AND | AND | AND | AND |
| TIFF | AND | AND | AND | AND | AND |
| JPEG | AND | AND | AND | AND | AND |
| BMP | AND |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **†** | AND |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | AND | AND | AND | AND | AND |
| PICT | AND |  |  |  |  |
| PSB |  |  |  |  |  |

**†** L&#39;immagine unita viene estratta dal file PSD. Si tratta di un&#39;immagine generata da  Adobe Photoshop e inclusa nel file PSD. A seconda delle impostazioni, l’immagine unita potrebbe essere l’immagine effettiva o meno.

Oltre alle informazioni di cui sopra, considerate quanto segue:

* Il supporto per i file EPS si applica solo alle immagini raster. Ad esempio, la generazione di miniature per le immagini vettoriali EPS non è supportata per impostazione predefinita. Per aggiungere supporto, [configurare ImageMagick](best-practices-for-imagemagick.md). Per integrare strumenti di terze parti per abilitare funzionalità aggiuntive, vedere [Gestore multimediale basato su riga di comando](media-handlers.md#command-line-based-media-handler).

* La funzione di reimpostazione dei metadati funziona per il formato di file PSB quando viene aggiunta al gestore `NComm`.

* Per utilizzare Dynamic Media per visualizzare in anteprima e generare rappresentazioni dinamiche per i file EPS, consultate [ formati di file Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Per i file EPS, la funzione di writeback dei metadati è supportata in PostScript Document Structuring Convention (Adobe PS-) versione 3.0 o successiva.

## Formati immagine raster non supportati in Dynamic Media {#unsupported-image-formats-dynamic-media}

L&#39;elenco seguente descrive i sottotipi di formati di file immagine raster *non* supportati in Dynamic Media.

Vedere anche [Rilevamento di formati di file non supportati per Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* File PNG con dimensioni blocco IDAT superiori a 100 MB.
* File PSB.
* I file PSD con uno spazio colore diverso da CMYK, RGB, Scala di grigio o Bitmap non sono supportati. Gli spazi colore DuoTone, Lab e Indexed non sono supportati.
* File PSD con una profondità di bit maggiore di 16.
* File TIFF con dati a virgola mobile.
* file TIFF con spazio colore Lab.

## Libreria Rasterizer PDF {#supported-pdf-rasterizer-library}

La libreria  Adobe PDF Rasterizer genera miniature e anteprime di alta qualità per file Adobe Illustrator e PDF  grandi e ricchi di contenuti.  Adobe consiglia di utilizzare la libreria PDF Rasterizer per le seguenti operazioni:

* I file AI/PDF ad alta intensità di contenuto che richiedono molte risorse per l&#39;elaborazione.
* File AI/PDF, per i quali le miniature non vengono generate per impostazione predefinita.
* File AI con colori Pantone Matching System (PMS).

Vedere [Utilizzo di PDF Rasterizer](aem-pdf-rasterizer.md).

## Libreria di transcodifica delle immagini {#supported-image-transcoding-library}

La libreria  Adobe Imaging Transcoding è una soluzione di elaborazione delle immagini che esegue funzioni fondamentali per la gestione delle immagini, come codifica, transcodifica, ricampionamento e ridimensionamento.

La libreria di transcodifica delle immagini supporta i tipi JPG/JPEG, PNG (8 bit e 16 bit), GIF, BMP, TIFF/Compresso TIFF (a parte file TIFF a 32 bit e PTIFF), ICO e ICN MIME.

Vedere [Libreria di transcodifica delle immagini](imaging-transcoding-library.md).

## Camera Raw {#supported-camera-raw}

La  libreria Adobe Camera Raw consente  AEM Assets di acquisire immagini crude. Vedere [Supporto Camera Raw](camera-raw.md).

## Formati di documento {#supported-document-formats}

I formati dei documenti supportati per le funzioni di gestione delle risorse sono i seguenti:

| Formato | Archiviazione | Gestione metadati<br> | Estrazione full-text<br> | Estrazione di metadati<br> | Generazione di miniature<br> | Estrazione Subasset<br> | Write-back di metadati<br> |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | AND | AND |  | AND | AND | AND | AND |
| DOC | AND | AND | AND | AND |  |  |  |
| DOCX | AND | AND | AND | AND |  |  |  |
| ODT | AND | AND | AND |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | AND | AND | AND | AND | AND | AND | AND |
| HTML | AND | AND | AND |  |  |  |  |
| RTF | AND | AND | AND |  |  |  |  |
| TXT | AND | AND | AND |  |  |  |  |
| XLS | AND | AND | AND |  |  |  |  |
| XLSX | AND | AND | AND | AND |  |  |  |
| ODS | AND | AND | AND |  |  |  |  |
| PPT | AND | AND | AND | AND | AND | AND |  |
| PPTX | AND | AND | AND | AND | AND | AND |  |
| ODP | AND | AND | AND |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | AND | AND |  | AND | AND | AND | AND |
| PS | AND | AND |  |  |  |  |  |
| QXP | AND | AND |  |  |  |  |  |
| EPUB | AND | AND |  | AND | AND |  |  |

I formati dei documenti supportati per le funzioni Dynamic Media sono i seguenti:

| Formato | Upload<br> (formato di ingresso) | Crea<br> immagine<br> predefinito<br> (formato di output) | Rendering di Preview<br> dynamic<br> | Distribuzione di rappresentazioni dinamiche<br><br> | Download della rappresentazione<br> dinamica<br> |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | AND |  |  |  |  |
| DOC |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | AND | AND | AND | AND | AND |
| HTML |  |  |  |  |  |
| TTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | AND |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

Oltre alla funzionalità di cui sopra, tenete presente quanto segue:

* Per utilizzare Dynamic Media per generare rappresentazioni dinamiche per i file PDF, vedere [ formati di file Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Per utilizzare Dynamic Media per visualizzare in anteprima e generare rappresentazioni dinamiche per i file AI, vedere [ formati di file Adobe Illustrator (AI), Postscript (EPS) e PDF.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Per utilizzare Dynamic Media per generare rappresentazioni dinamiche per i file INDD, vedere [ InDesign (INDD) file format](../assets/managing-image-presets.md#indesign-indd-file-format).

## Formati multimediali {#supported-multimedia-formats}

| Formato | Archiviazione | Gestione dei metadati | Estrazione di metadati | Generazione delle miniature | Transcodifica FFMPEG |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | AND | AND |  | - | * |
| MIDI | AND | AND |  | - | * |
| 3GP | AND | AND |  | - | * |
| MP3 | AND | AND | AND | - | * |
| MPG | AND | AND |  | - | * |
| OGA | AND | AND |  | - | * |
| OGG | AND | AND |  | - | * |
| RA | AND | AND |  | - | * |
| WAV | AND | AND |  | - | * |
| WMA | AND | AND |  | - | * |
| DVI | AND | AND |  | * | * |
| FLV | AND | AND |  | * | * |
| M4V | AND | AND |  | * | * |
| MPEG | AND | AND |  | * | * |
| OGV | AND | AND |  | * | * |
| MOV | AND | AND |  | * | * |
| WMV | AND | AND |  | * | * |
| SWF | AND | AND |  |  |  |

## Formati video di ingresso per Dynamic Media Transcoding {#supported-input-video-formats-for-dynamic-media-transcoding}

| Estensione dei file video | Contenitore | Codec video consigliati | Codec video non supportati |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (tutti i profili) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 e HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Animazione Apple |
| FLV, F4V | Flash Adobe  | H264/AVC, Flix VP6, H263, Sorenson | SWF (file di animazione vettoriale) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | Interferenza A/V | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Video Raw rosso | MJPEG 2000 |  |
| RAM, RM | RealVideo | Non supportato | Real G2 (RV 20), Real 8 (RV 30), Real 10 (RV 40) |
| FLAC | Flac nativo | Codec audio senza perdita di dati |  |
| MJ2 | Motion JPEG 2000 | Codec Motion JPEG 2000 |  |

## Formati di archivio {#supported-archive-formats}

I formati di archivio supportati e l&#39;applicabilità dei flussi di lavoro DAM comuni sono descritti nella tabella seguente.

| Formato | Archiviazione | Gestione versioni | Flusso di lavoro | Pubblicazione | Controllo accesso | Distribuzione Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | AND | AND | AND | AND | AND |  |
| JAR | AND | AND | AND | AND | AND |  |
| RAR | AND | AND | AND | AND | AND |  |
| TAR | AND | AND | AND | AND | AND |  |
| ZIP **†** | AND | AND | AND | AND | AND | AND |

**†** L&#39;immagine unita viene estratta dal file PSD. Si tratta di un&#39;immagine generata da  Adobe Photoshop e inclusa nel file PSD. A seconda delle impostazioni, l’immagine unita potrebbe essere l’immagine effettiva o meno. Gli archivi ZIP creati con l&#39;algoritmo `Deflate64` dispongono di un supporto limitato in AEM. Le operazioni di archiviazione e annullamento dell&#39;archiviazione non sono supportate. Tuttavia, sono supportate operazioni quali il caricamento, la navigazione e il download.

## Altri formati supportati {#other-supported-formats}

L&#39;applicabilità dei flussi di lavoro DAM comuni ad alcuni altri formati di file è descritta nella tabella seguente.

| Formato | Archiviazione | Gestione versioni | Flusso di lavoro | Pubblicazione | Controllo accesso | Distribuzione Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | AND | AND | AND | AND | AND |  |
| SVG | AND | AND | AND | AND | AND |  |
| CSS | AND | AND | AND | AND | AND | AND |
| VTT | AND | AND | AND | AND | AND | AND |
| XML | AND | AND | AND | AND | AND | AND |
| JavaScript (se configurato con un proprio dominio di consegna) |  |  |  |  |  | AND |

**#** Gli altri formati sono supportati in DAM per l’archiviazione, il controllo delle versioni, l’ACL, il flusso di lavoro, la pubblicazione e la gestione dei metadati.

## Tipi MIME supportati {#supported-mime-types}

Per impostazione predefinita, AEM rileva il tipo di file utilizzando l&#39;estensione del file. AEM rilevarlo dal contenuto dei file. Per quest&#39;ultima, selezionare l&#39;opzione [!UICONTROL Rileva MIME dal contenuto] in [!UICONTROL Day CQ DAM Mime Type Service] nella AEM Web Console.

Un elenco dei tipi MIME supportati è disponibile in CRXDE Lite in `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

| Estensione file | Tipo MIME/ Tipo di supporto Internet | Valore jobParam predefinito | Valore jobParam consentito |
|---|---|---|---|
| Immagine | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | Il valore predefinito jobParam viene applicato a tutte le risorse di tipo mime immagine.<ul><li>[knockoutBackgroundOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>application/eps</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| TTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shock-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Abilita il supporto](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support) dei parametri di processo di caricamento risorse/Scene7 basati su tipi MIME.
>* [Configurare il supporto](config-dynamic.md) dei parametri di processo di caricamento in base al tipo MIME.

