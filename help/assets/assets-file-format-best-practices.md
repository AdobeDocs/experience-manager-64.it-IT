---
title: Best practice per il formato dei file delle risorse
description: Procedure ottimali per il supporto dei file in  AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a892ef7ab018aca715693125808d7ade540c8242
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# Assets file format best practices {#assets-file-format-best-practices}

 AEM Assets supporta numerose librerie di formati di file proprietari e di terze parti per soddisfare i diversi requisiti di supporto dei file da parte degli utenti. Le librerie di Adobi  supportate includono,  Adobe Camera Raw, Gibson,  Adobe PDF Rasterizer e  Adobe InDesign Server. Inoltre,  AEM Assets supporta librerie di terze parti, tra cui ImageMagick, DodiciMonkeys e così via.

For the supported file formats, see [Assets supported formats](assets-formats.md).

## Libreria Adobe Camera Raw  {#adobe-camera-raw-library}

Per ottenere prestazioni ottimali,  Adobe consiglia di utilizzare  libreria Adobe Camera Raw per:

* RAW
* DNG

La libreria Adobe Camera Raw  supporta il profilo colore CMYK come input. Tuttavia, genera l’output in spazio colore RGB e supporta solo l’output in formato JPEG. Non mantiene lo spazio colore del file di origine (ad esempio CMYK) nelle miniature.

Per ulteriori informazioni, consultate [Camera Raw supporto](camera-raw.md) in  AEM Assets.

##  libreria Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Per risultati ottimali,  Adobe consiglia di utilizzare la libreria  Adobe PDF Rasterizer per i file seguenti:

* File PDF pesanti e ricchi di contenuti
* File AI con miniature non generate
* Per i file AI con colori SPOT (PMS)

Le miniature e le anteprime generate con PDF Rasterizer hanno una qualità migliore rispetto all’output raster fornito con Scene7. La libreria  Adobe PDF Rasterizer non supporta la conversione dello spazio colore. A prescindere dallo spazio colore del file PDF di origine,  Adobe PDF Rasterizer genera solo l’output RGB.

##  server Adobe InDesign {#adobe-indesign-cc-server}

 Adobe consiglia di utilizzare  server Adobe InDesign per estrarre  rappresentazioni specifiche di Adobe InDesign, ad esempio IDML e HTML. Per ulteriori informazioni, consultate [Aggiunta di risorse AEM come riferimenti in  Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media genera e offre diverse varianti di contenuti avanzati in tempo reale attraverso la rete globale, scalabile e ottimizzata per le prestazioni. Offre esperienze di visualizzazione interattive e semplifica il processo di gestione delle campagne digitali. Per informazioni dettagliate sull’abilitazione di elementi multimediali dinamici, consultate [Configurazione di elementi multimediali](config-dynamic.md)dinamici.

Attualmente, Dynamic Media supporta i video fino a 15 GB di contenuto per file.

## Libreria ImageMagick {#imagemagick-library}

 Adobe consiglia di utilizzare la libreria ImageMagick nei seguenti scenari:

* Per generare rappresentazioni delle miniature per i file EPS
* Per mantenere le informazioni sul profilo immagine
* Per mantenere la trasparenza
* Per elaborare i file PSD e PSB

Per informazioni su come impostare la libreria ImageMagic in AEM, vedere [Utilizzo di ImageMagick](media-handlers.md#an-example-using-imagemagick). Per un utilizzo ottimale, consultate [Best practice per la configurazione di ImageMagick](best-practices-for-imagemagick.md).

## Libreria di transcodifica immagini {#image-transcoding-library}

La libreria  Adobe Imaging Transcoding è una soluzione per l’elaborazione delle immagini che esegue le funzioni di base per la gestione delle immagini, tra cui la codifica delle immagini, la transcodifica, il ricampionamento, il ridimensionamento e così via.

La libreria Imaging Transcoding supporta i seguenti tipi MIME:

* JPG/JPEG
* PNG (8 bit e 16 bit)
* GIF
* BMP
* TIFF/TIFF compresso (a parte i formati a 32 bit e PTiff).
* ICO
* ICN

Per informazioni dettagliate, consultate Libreria [transcodifica](imaging-transcoding-library.md)immagini.
