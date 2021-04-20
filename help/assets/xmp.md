---
title: Metadati XMP
description: Scopri lo standard di metadati XMP (Extensible Metadata Platform) utilizzato da AEM Assets per la gestione dei metadati. XMP fornisce un formato standard per la creazione, l'elaborazione e lo scambio di metadati per un'ampia varietà di applicazioni.
contentOwner: AG
feature: Metadata
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 19%

---


# Metadati XMP {#xmp-metadata}

XMP (Extensible Metadata Platform) è lo standard di metadati utilizzato da AEM Assets per la gestione di tutti i metadati. XMP fornisce un formato standard per la creazione, l&#39;elaborazione e lo scambio di metadati per un&#39;ampia varietà di applicazioni.

Oltre ad offrire una codifica universale dei metadati che può essere incorporata in tutti i formati di file, XMP fornisce un [modello di contenuto ](xmp.md#xmp-core-concepts) e è [supportato da Adobe](xmp.md#advantages-of-xmp) e da altre aziende, in modo che gli utenti di XMP in combinazione con AEM Assets abbiano una piattaforma potente su cui basarsi.

La [specifica XMP](https://www.adobe.com/devnet/xmp.html) è disponibile dall&#39;Adobe.

## Cos&#39;è XMP? {#what-is-xmp}

AEM Assets supporta in modo nativo l’XMP, la piattaforma di metadati estensibili guidata da Adobe. XMP è uno standard per l’elaborazione e l’archiviazione di metadati standardizzati e proprietari nelle risorse digitali. XMP è stato progettato per essere lo standard comune che consente a più applicazioni di lavorare in modo efficace con i metadati.

I professionisti della produzione, ad esempio, utilizzano il supporto integrato XMP all&#39;interno delle applicazioni Adobe per trasmettere informazioni in più formati di file. L’archivio AEM Assets estrae i metadati XMP e li utilizza per gestire il ciclo di vita dei contenuti e offre la possibilità di creare flussi di lavoro di automazione.

XMP standardizza il modo in cui i metadati vengono definiti, creati ed elaborati fornendo un modello di dati, un modello di archiviazione e schemi. Tutti questi concetti sono trattati in questa sezione.

Tutti i metadati legacy di EXIF, ID3 o Microsoft Office vengono automaticamente tradotti in XMP, che possono essere estesi per supportare lo schema di metadati specifico del cliente, ad esempio i cataloghi di prodotti.

I metadati in XMP sono costituiti da un insieme di proprietà. Queste proprietà sono sempre associate a un\
entità particolare indicata come risorsa; in altre parole, le proprietà riguardano la risorsa. Nel caso di XMP, la risorsa è sempre la risorsa.

### Adobe {#adobe}

Adobe ha introdotto lo standard XMP come parte del prodotto software Adobe Acrobat. Da allora, lo standard XMP è stato ampiamente adottato.

### ecosistema XMP {#xmp-ecosystem}

XMP definisce un modello di [metadati](https://it.wikipedia.org/wiki/Metadato) che può essere usato con qualsiasi insieme definito di elementi di metadati. XMP definisce anche [schemi](https://en.wikipedia.org/wiki/XML_schema) specifici per le proprietà di base, utili per registrare la cronologia di una risorsa, in quanto passano attraverso più fasi di elaborazione: dalla fotografia, dalla [scansione](https://it.wikipedia.org/wiki/Scanner_(informatica)) o creazione come testo, fino ai passaggi di modifica delle foto (come [ritaglio](https://en.wikipedia.org/wiki/Cropping_%28image%29) o regolazione colore), fino all’assemblaggio in un’immagine definitiva. XMP consente a ogni programma software o dispositivo di aggiungere le proprie informazioni a una risorsa digitale, che possono quindi essere poi mantenute nel file digitale finale.

XMP è spesso serializzato e memorizzato utilizzando un sottoinsieme del [W3C](https://it.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://it.wikipedia.org/wiki/Resource_Description_Framework) (RDF), che a sua volta è espresso in [XML](https://it.wikipedia.org/wiki/XML).

## Vantaggi di XMP {#advantages-of-xmp}

XMP presenta i seguenti vantaggi rispetto ad altri standard di codifica e schemi:

* I metadati basati su XMP sono molto potenti e precisi.
* XMP consente di avere più valori per una proprietà.
* XMP codifica standard, che consente di scambiare facilmente i metadati.
* XMP estensibile. Puoi aggiungere ulteriori informazioni alle risorse.

### Estensibili {#extensible}

Lo standard XMP è progettato per essere estensibile e consente di aggiungere tipi personalizzati di metadati ai dati di XMP. EXIF, d&#39;altro canto, no - ha un elenco fisso di proprietà che non può essere esteso.

>[!NOTE]
>
>XMP generalmente non consente l&#39;incorporazione di tipi di dati binari. Per trasportare i dati binari in XMP, ad esempio, le immagini in miniatura, devono essere codificati in un formato XML-friendly come Base64.

## XMP concetti di base {#xmp-core-concepts}

Le sezioni seguenti descrivono i concetti di base di XMP, compresi namespace e schemi, proprietà e valori e alternative linguistiche.

### Namespace e schemi {#namespaces-and-schemata}

Uno schema XMP è un insieme di nomi di proprietà in uno spazio dei nomi XML comune che include\
il tipo di dati e le informazioni descrittive. Uno schema XMP è identificato dal relativo URI dello spazio dei nomi XML. L’utilizzo di spazi dei nomi evita conflitti tra proprietà in schemi diversi con lo stesso nome ma con un significato diverso.

Ad esempio, la proprietà **Creatore** in due schemi progettati in modo indipendente potrebbe indicare la persona che ha creato la risorsa o l’applicazione che ha creato la risorsa (ad esempio, Adobe Photoshop).

### Proprietà e valori {#properties-and-values}

XMP possono includere proprietà di uno o più schemi.

Ad esempio, un sottoinsieme tipico utilizzato da molte applicazioni di Adobe potrebbe includere quanto segue:

* Schema di base Dublino: dc:title, dc:creator, dc:subject, dc:format, dc:rights
* Schema di base XMP: xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* Schema di gestione dei diritti XMP: xmpRights:WebStatement, xmpRights:Contrassegnato
* XMP schema di gestione file multimediali: xmpMM:DocumentID

### Alternative linguistiche {#language-alternatives}

XMP offre la possibilità di aggiungere una proprietà **xml:lang** alle proprietà di testo per specificare la lingua del testo.
