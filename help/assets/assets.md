---
title: Introduzione a [!DNL Adobe Experience Manager Assets]
description: Scopri cos’è la gestione delle risorse digitali, i relativi casi d’uso e l’offerta  [!DNL Adobe Experience Manager Asset] .
contentOwner: AG
feature: Asset Management
role: Leader,Architect,User
exl-id: 9292871d-3b10-49f8-ac1a-4770b4e44048
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 33%

---

# Informazioni su [!DNL Adobe Experience Manager Assets] come soluzione DAM {#about-assets}

[!DNL Assets] è uno strumento di gestione delle risorse digitali (DAM) che è parte integrante della  [!DNL Experience Manager] piattaforma e consente alla tua azienda di gestire e distribuire le risorse digitali. Gli utenti di un’organizzazione possono gestire, archiviare e accedere a numerosi tipi di risorse digitali quali immagini, video, documenti, clip audio, file 3D e contenuti multimediali avanzati da utilizzare sul web, nella stampa e per la distribuzione digitale.

## Che cos’è Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] consente di condividere e distribuire le risorse digitali chiave di un’organizzazione in tutta l’azienda. Gli utenti di un’organizzazione possono archiviare, gestire e accedere a risorse digitali quali immagini, elementi grafici, audio, video e documenti tramite un’interfaccia Web (o una cartella CIFS o WebDAV).

[!DNL Assets] funzionalità di  [!DNL Experience Manager] consente di effettuare le seguenti operazioni:

* Aggiungere e condividere immagini, documenti, file audio e video in diversi formati.
* Gestisci le risorse raggruppandole per tag, lightbox o stelle (i tuoi preferiti). Aggiungere note alle risorse.
* Trovare risorse cercando il nome dei file, l’intero testo dei documenti in base a data, tipo di documento e tag.
* Aggiungere o modificare le informazioni sui metadati per le risorse. La versione dei metadati viene adeguata automaticamente alla relativa risorsa. È possibile importare o esportare i metadati delle risorse.
* Utilizzare funzioni di modifica delle immagini come il ridimensionamento e l’aggiunta di filtri. È possibile importare ed esportare contemporaneamente più risorse digitali utilizzando una cartella WebDAV o CIFS.
* Utilizzare flussi di lavoro e notifiche per consentire l’elaborazione e il download simultanei di qualsiasi insieme di risorse e gestire i diritti di accesso alle risorse.

### [!DNL Experience Manager Assets] è integrato con  [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] si integra completamente con  [!DNL Sites] e funziona perfettamente per tutti i casi d&#39;uso. Ad esempio, durante la creazione di pagine web, gli autori [!DNL Sites] possono trovare e utilizzare le risorse digitali tramite Content Finder. L&#39;interfaccia utente di [!DNL Assets] è la stessa di [!DNL Sites]. Per informazioni dettagliate, consulta [panoramica di Sites](/help/sites-authoring/qg-page-authoring.md) .

<!-- TBD: Update image for branding 

![screen_shot_2012-04-17at15946pm](assets/screen_shot_2012-04-17at15946pm.png) ![screen_shot_2012-04-17at20100pm](assets/screen_shot_2012-04-17at20100pm.png)

Assets managed within [!DNL Experience Manager] DAM can then be accessed via the content finder of WCM:

![screen_shot_2012-04-17at20214pm](assets/screen_shot_2012-04-17at20214pm.png) -->

### Confronto tra la gestione delle risorse digitali e il componente Immagine {#digital-asset-management-versus-image-component}

Per determinare se inserire un’immagine nell’archivio DAM o utilizzare un componente immagine, considera il ciclo di vita dell’immagine:

* Se l&#39;immagine ha lo stesso ciclo di vita della pagina, utilizza il componente Immagine .
* Se l’immagine presenta un ciclo di vita separato, ad esempio se devi utilizzare l’immagine due volte o all’esterno di WCM, utilizza [!DNL Assets].

## Cosa sono le risorse digitali? {#what-are-digital-assets}

Una risorsa è un documento, un’immagine, un video o dell’audio digitale (o parte di essi) che può avere più rappresentazioni e risorse secondarie (ad esempio, livelli in un file Photoshop, slide in un file PowerPoint, pagine in un file pdf, file in un file ZIP).

Una risorsa, in pratica, è composta da un file binario, da metadati, da rappresentazioni e da risorse secondarie. Consulta la [Guida alle prestazioni di DAM](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html) per informazioni dettagliate.

>[!CAUTION]
>
>Il caricamento e/o la modifica di un grande volume di risorse (in particolare di immagini) può influire sulle prestazioni della distribuzione [!DNL Experience Manager].

### [!DNL Experience Manager Assets] terminologia {#aem-assets-terminology}

Quando lavori con risorse digitali in [!DNL Experience Manager], è necessario comprendere la seguente terminologia:

* **Raccolta**: Una raccolta di risorse in base alla posizione fisica (cartella), alle proprietà comuni (cartella di ricerca salvata) o alla selezione dell’utente (cartelle lightbox).

* **metadati** [!DNL Assets] ; ad esempio autore, data di scadenza, informazioni DRM (Digital Rights Management) e così via. I metadati disponibili dipendono dalle autorizzazioni di accesso. [!DNL Assets] offre e supporta i seguenti schemi di metadati di uso comune:

   * Dublin Core: comprende autore, descrizione, data, oggetto e così via.
   * IPTC: comprende evento, modello, luogo e così via.
   * WCM: incluse le proprietà della pagina, [!UICONTROL On Time] e [!UICONTROL Off Time] e così via.

* **Assegnazione tag**:  [!DNL Assets] possono essere contrassegnati e classificati. Consulta [organizzazione delle risorse](/help/assets/organize-assets.md).

* **Rappresentazioni**: Un rendering è la rappresentazione binaria di una risorsa. [!DNL Assets] hanno sempre una rappresentazione principale, quella del file caricato. Possono disporre di diverse rappresentazioni aggiuntive create, ad esempio, dai passaggi personalizzati del flusso di lavoro o durante il caricamento di una risorsa. Le rappresentazioni possono essere di dimensioni diverse, con diverse risoluzioni, con filigrana aggiunta o altre caratteristiche modificate.

* **Versioni**: Il controllo delle versioni crea un’istantanea delle risorse digitali in un momento specifico. Se necessario, puoi ripristinare le risorse alle versioni precedenti. Consulta [controllo delle versioni in [!DNL Assets]](managing-assets-touch-ui.md#asset-versioning).

* **Risorse secondarie**: Le risorse secondarie sono risorse che costituiscono una risorsa, ad esempio i livelli in un  [!DNL Adobe Photoshop] file o le pagine in un file PDF. In [!DNL Assets] puoi gestire le risorse secondarie come le risorse.

### Come lavorare con le risorse digitali {#how-to-work-with-assets}

È possibile intervenire su una risorsa o una raccolta eseguendo specifiche azioni per creare o modificare risorse, raccolte e rappresentazioni. Molte delle azioni di base eseguite sulle risorse (caricamento, eliminazione, aggiornamento, salvataggio di risorse secondarie) attivano flussi di lavoro preconfigurati. Questi vengono attivati automaticamente in [!DNL Assets] e sono descritti in dettaglio in [!DNL Assets] gestori di contenuti multimediali.

Le attività eseguibili con questi flussi di lavoro preconfigurati:

* Salva la risorsa nell’archivio o eliminala.
* Estrarre e salvare i metadati della risorsa; i singoli elementi di metadati vengono salvati come XMP.
* Genera rappresentazioni e miniature della risorsa; compreso, se necessario, il ridimensionamento e il ritaglio automatici.
* Se necessario, transcodifica la risorsa. Ad esempio, i video per dispositivi mobili e web vengono codificati con 24 fotogrammi al secondo, quelli per il download con 30 fotogrammi al secondo. L&#39;audio per dispositivi mobili e web viene codificato a 128 Kbps, quello per il download a 192 Kbps.

Ovviamente, puoi applicare i flussi di lavoro anche manualmente. Per un elenco dei flussi di lavoro predefiniti, consulta [Gestori di contenuti multimediali di Assets ](media-handlers.md).

## [!DNL Experience Manager Assets] e [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Per informazioni sulle differenze, consulta [Risorse e Media Library](medialibrary.md) .

>[!MORELIKETHIS]
>
>* [Video introduttivo - Experience Manager Assets come DAM moderno](https://www.youtube.com/watch?v=PBwQqZgC-yo)

