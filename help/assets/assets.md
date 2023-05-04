---
title: Introduzione a [!DNL Adobe Experience Manager Assets]
description: Scopri cosa sono la gestione delle risorse digitali, i relativi casi d’uso e [!DNL Adobe Experience Manager Asset] offerta.
contentOwner: AG
feature: Asset Management
role: Leader,Architect,User
exl-id: 9292871d-3b10-49f8-ac1a-4770b4e44048
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 1%

---

# Informazioni [!DNL Adobe Experience Manager Assets] come soluzione DAM {#about-assets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

[!DNL Assets] è uno strumento di gestione delle risorse digitali (DAM) che è parte integrante del [!DNL Experience Manager] e consente alle aziende di gestire e distribuire le risorse digitali. Gli utenti di un’organizzazione possono gestire, archiviare e accedere a numerosi tipi di risorse digitali quali immagini, video, documenti, clip audio, file 3D e contenuti multimediali avanzati da utilizzare sul web, nella stampa e per la distribuzione digitale.

## Cos’è Digital Asset Management? {#what-is-digital-asset-management}

[!DNL Assets] fornisce condivisione e distribuzione a livello aziendale delle risorse digitali chiave di un&#39;organizzazione. Gli utenti di un’organizzazione possono archiviare, gestire e accedere a risorse digitali quali immagini, elementi grafici, audio, video e documenti tramite un’interfaccia Web (o una cartella CIFS o WebDAV).

[!DNL Assets] capacità [!DNL Experience Manager] consente di effettuare le seguenti operazioni:

* Aggiungere e condividere immagini, documenti, file audio e file video in diversi formati.
* Gestisci le risorse raggruppandole per tag, lightbox o stelle (i tuoi preferiti). Aggiungi annotazioni alle risorse.
* Trovare le risorse ricercando i nomi dei file, il testo completo dei documenti e ricercando le date, il tipo di documento e i tag.
* Aggiungere o modificare le informazioni sui metadati per le risorse. La versione dei metadati viene eseguita automaticamente insieme alla risorsa corrispondente. Puoi importare o esportare i metadati delle risorse.
* Esegui le funzioni di modifica delle immagini, come il ridimensionamento e l’aggiunta di filtri immagine. Importa ed esporta più risorse digitali simultaneamente utilizzando una cartella WebDAV o CIFS.
* Utilizza flussi di lavoro e notifiche per consentire l’elaborazione e il download simultanei di qualsiasi set di risorse e gestire i diritti di accesso alle risorse.

### [!DNL Experience Manager Assets] è integrato con [!DNL Experience Manager Sites] {#aem-assets-fully-integrated-in-cq-wcm}

[!DNL Assets] si integra completamente con [!DNL Sites] e funziona senza problemi per tutti i casi d&#39;uso. Ad esempio, durante la creazione di pagine web, il [!DNL Sites] Gli autori possono trovare e utilizzare le risorse digitali tramite Content Finder. Interfaccia utente di [!DNL Assets] è uguale a quello di [!DNL Sites]. Vedi [panoramica di Sites](/help/sites-authoring/qg-page-authoring.md) per informazioni complete.

<!-- TBD: Update image for branding 

![screen_shot_2012-04-17at15946pm](assets/screen_shot_2012-04-17at15946pm.png) ![screen_shot_2012-04-17at20100pm](assets/screen_shot_2012-04-17at20100pm.png)

Assets managed within [!DNL Experience Manager] DAM can then be accessed via the content finder of WCM:

![screen_shot_2012-04-17at20214pm](assets/screen_shot_2012-04-17at20214pm.png) -->

### Confronto tra la gestione delle risorse digitali e il componente Immagine {#digital-asset-management-versus-image-component}

Per determinare se inserire un’immagine nell’archivio DAM o utilizzare un componente immagine, considera il ciclo di vita dell’immagine:

* Se l&#39;immagine ha lo stesso ciclo di vita della pagina, utilizza il componente Immagine .
* Se l&#39;immagine ha un ciclo di vita separato, ad esempio, se utilizzi due volte o all&#39;esterno di WCM, utilizza [!DNL Assets].

## Cosa sono le risorse digitali? {#what-are-digital-assets}

Una risorsa è un documento, un’immagine, un video o dell’audio digitale (o parte di essi) che può avere più rappresentazioni e risorse secondarie (ad esempio, livelli in un file Photoshop, slide in un file PowerPoint, pagine in un file pdf, file in un file ZIP).

Una risorsa è essenzialmente un binario, contiene metadati, rappresentazioni e risorse secondarie. Consulta la sezione [Guida alle prestazioni di DAM](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html) per informazioni dettagliate.

>[!CAUTION]
>
>Il caricamento e/o la modifica di un grande volume di risorse (in particolare di immagini) può influire sulle prestazioni del [!DNL Experience Manager] distribuzione.

### [!DNL Experience Manager Assets] terminologia {#aem-assets-terminology}

Quando si lavora con risorse digitali in [!DNL Experience Manager], è necessario comprendere la seguente terminologia:

* **Raccolta**: Una raccolta di risorse in base alla posizione fisica (cartella), alle proprietà comuni (cartella di ricerca salvata) o alla selezione dell’utente (cartelle lightbox).

* **Metadati** [!DNL Assets] avere metadati; ad esempio autore, data di scadenza, informazioni DRM (Digital Rights Management) e così via. I metadati sono sotto controllo accessi. [!DNL Assets] supporta i seguenti schemi di metadati comuni pronti all’uso:

   * Dublin Core: compresi autore, descrizione, data, oggetto e così via.
   * IPTC: inclusi evento, modello, posizione e così via.
   * WCM: comprese le proprietà della pagina, [!UICONTROL Ora di attivazione] e [!UICONTROL Ora di disattivazione]e così via.

* **Assegnazione tag**: [!DNL Assets] possono essere contrassegnati e classificati. Vedi [organizzazione delle risorse](/help/assets/organize-assets.md).

* **Rendering**: Un rendering è la rappresentazione binaria di una risorsa. [!DNL Assets] hanno sempre una rappresentazione principale, quella del file caricato. Possono disporre di un numero qualsiasi di rappresentazioni aggiuntive create, ad esempio dai passaggi di un flusso di lavoro personalizzato o quando viene caricata una risorsa. Le rappresentazioni possono avere dimensioni diverse, con una risoluzione diversa, con una filigrana aggiunta o altre caratteristiche modificate.

* **Versioni**: Il controllo delle versioni crea un’istantanea delle risorse digitali in un momento specifico. Puoi ripristinare le risorse alle versioni precedenti. Vedi [versione in [!DNL Assets]](managing-assets-touch-ui.md#asset-versioning).

* **Risorse secondarie**: Le risorse secondarie sono risorse che costituiscono una risorsa, ad esempio i livelli in una [!DNL Adobe Photoshop] in un file PDF. In [!DNL Assets], puoi gestire le risorse secondarie in modo analogo alle risorse.

### Come lavorare con le risorse digitali {#how-to-work-with-assets}

Esegui un&#39;azione su una risorsa o una raccolta. Le azioni possono creare o modificare risorse, raccolte e rappresentazioni. Molte delle azioni di base eseguite sulle risorse (caricamento, eliminazione, aggiornamento, salvataggio di risorse secondarie) attivano flussi di lavoro preconfigurati. che vengono attivate automaticamente [!DNL Assets] e sono descritti in dettaglio in [!DNL Assets] gestori di contenuti multimediali.

Le attività eseguibili con questi flussi di lavoro preconfigurati:

* Salva la risorsa nell’archivio o eliminala.
* Estrarre e salvare i metadati della risorsa; i singoli elementi di metadati vengono salvati come XMP.
* Genera rappresentazioni e miniature della risorsa; compreso, se necessario, il ridimensionamento e il ritaglio automatici.
* Se necessario, transcodifica la risorsa. Ad esempio, i video per dispositivi mobili e web vengono codificati con 24 fotogrammi al secondo, quelli per il download con 30 fotogrammi al secondo. L&#39;audio per dispositivi mobili e web viene codificato a 128 Kbps, quello per il download a 192 Kbps.

Naturalmente, puoi anche applicare i flussi di lavoro manualmente. Vedi [Gestori file multimediali di Assets](media-handlers.md)per un elenco dei flussi di lavoro predefiniti.

## [!DNL Experience Manager Assets] e [!DNL Media Library] {#cq-dam-vs-cq-medialibrary}

Vedi [Risorse e Media Library](medialibrary.md) per informazioni sulle differenze.

>[!MORELIKETHIS]
>
>* [Video introduttivo - Experience Manager Assets come DAM moderno](https://www.youtube.com/watch?v=PBwQqZgC-yo)

