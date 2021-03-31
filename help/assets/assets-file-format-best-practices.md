---
title: Best practice per i formati di file delle risorse
description: Best practice per il supporto dei file in AEM Assets.
contentOwner: AG
feature: Gestione delle risorse, Strumenti per sviluppatori
role: Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# Best practice per il formato dei file delle risorse {#assets-file-format-best-practices}

AEM Assets supporta numerose librerie di formati di file proprietari e di terze parti per soddisfare diversi requisiti di supporto dei file da parte degli utenti. Le librerie di Adobi supportate includono Adobe Camera Raw, Gibson, Adobe PDF Rasterizer e Adobe InDesign Server. Inoltre, AEM Assets supporta librerie di terze parti, tra cui ImageMagick, DodiciMonkeys e così via.

Per i formati di file supportati, consulta [Formati supportati da Assets](assets-formats.md).

## Libreria Adobe Camera Raw {#adobe-camera-raw-library}

Per ottenere prestazioni ottimali, Adobe consiglia di utilizzare la libreria Adobe Camera Raw per:

* RAZZA
* DNG

La libreria Adobe Camera Raw supporta il profilo colore CMYK come input. Tuttavia, genera l&#39;output nello spazio colore RGB e supporta l&#39;output solo in formato JPEG. Non mantiene lo spazio colore del file di origine (ad esempio CMYK) nelle miniature.

Per ulteriori informazioni, consulta [Supporto Camera Raw](camera-raw.md) in AEM Assets.

## Libreria Adobe PDF Rasterizer {#adobe-pdf-rasterizer-library}

Per risultati migliori, Adobe consiglia di utilizzare la libreria Adobe PDF Rasterizer per i seguenti file:

* File PDF pesanti e ad uso intensivo di contenuti
* File AI con miniature non generate come predefiniti
* Per i file AI con colori SPOT (PMS)

Miniature e anteprime generate con PDF Rasterizer sono di qualità migliore rispetto all’output raster preconfigurato. La libreria Adobe PDF Rasterizer non supporta la conversione dello spazio colore. Indipendentemente dallo spazio colore del file PDF sorgente, Adobe PDF Rasterizer genera solo output RGB.

## Server Adobe InDesign {#adobe-indesign-cc-server}

Adobe consiglia di utilizzare il server Adobe InDesign per estrarre rappresentazioni specifiche di Adobe InDesign, ad esempio IDML e HTML. Per ulteriori informazioni, consulta [Aggiunta di risorse AEM come riferimenti in Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media genera e offre diverse varianti di contenuti avanzati in tempo reale attraverso la rete globale, scalabile e ottimizzata per le prestazioni. Fornisce esperienze di visualizzazione interattive e semplifica il processo di gestione delle campagne digitali. Per informazioni dettagliate sull&#39;abilitazione di Dynamic Media, consulta [Configurazione di Dynamic Media](config-dynamic.md).

Al momento, Dynamic Media può supportare video fino a 15 GB di contenuto per file.

## Libreria ImageMagick {#imagemagick-library}

Adobe consiglia di utilizzare la libreria ImageMagick nei seguenti scenari:

* Per generare rappresentazioni miniature per i file EPS
* Per preservare le informazioni sul profilo immagine
* Per preservare la trasparenza
* Per elaborare file PSD e PSB

Per informazioni su come impostare la libreria ImageMagic in AEM, vedere [Uso di ImageMagick](media-handlers.md#an-example-using-imagemagick). Per un utilizzo ottimale, consulta [Best practice per la configurazione di ImageMagick](best-practices-for-imagemagick.md).

## Libreria di transcodifica delle immagini {#image-transcoding-library}

La libreria di transcodifica delle immagini di Adobe è una soluzione di elaborazione delle immagini che esegue funzioni di base per la gestione delle immagini, tra cui codifica, transcodifica, ricampionamento, ridimensionamento e così via.

La libreria di transcodifica delle immagini supporta i seguenti tipi MIME:

* JPG/JPEG
* PNG (8 bit e 16 bit)
* GIF
* BMP
* TIFF/TIFF compresso (a parte i TIFF a 32 bit e i PTiff).
* ICO
* ICN

Per informazioni dettagliate, consulta [Imaging Transcoding Library](imaging-transcoding-library.md).
