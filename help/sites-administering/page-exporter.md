---
title: Page Exporter
seo-title: Page Exporter
description: Scoprite come utilizzare AEM Page Exporter.
seo-description: Scoprite come utilizzare AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
translation-type: tm+mt
source-git-commit: aac5026a249e1cb09fec66313cc03b58597663f0
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---


# Page Exporter{#the-page-exporter}

AEM consente di esportare una pagina come pagina Web completa con immagini, file .js e .css.

Una volta configurata l&#39;esportazione, è sufficiente richiedere una pagina nel browser sostituendo `html` con `export.zip` nell&#39;URL e ottenere un file ZIP contenente la pagina rappresentata in formato html e le risorse di riferimento. Tutti i percorsi della pagina, ad esempio i percorsi delle immagini, vengono riscritti in modo da puntare ai file inclusi nel file zip o alle risorse sul server.

## Esportazione di una pagina {#exporting-a-page}

Nei passaggi seguenti viene descritto come esportare una pagina e si presuppone che esista un modello di configurazione per l’esportazione per il sito. Un modello di configurazione definisce il modo in cui una pagina viene esportata ed è specifica per il sito. Per creare un modello di configurazione, fare riferimento alla sezione [Creazione di una configurazione di esportazione di pagina per il sito](#creating-a-page-exporter-configuration-for-your-site).

Per esportare una pagina:

1. Nel browser, aprite la pagina. Esempio:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Aprite la finestra di dialogo delle proprietà della pagina, selezionate la scheda **Avanzate** ed espandete il set di campi **Esporta**.

1. Fate clic sull&#39;icona Lente di ingrandimento e selezionate un modello di configurazione. Selezionate il modello **geometrixx**, in quanto è il modello predefinito per il sito di Geometrixx. Fai clic su **OK**.

1. Fare clic su **OK** per chiudere la finestra di dialogo delle proprietà della pagina.
1. Richiedete la pagina sostituendo `html` con `export.zip` nell&#39;URL.

1. Scaricate il file `<page-name>.export.zip` nel file system.

1. Nel file system, decomprimete il file:

   * il file html della pagina ( `<page-name>.html`) è disponibile in `<unzip-dir>/<page-path>`
   * altre risorse (file .js, file .css, immagini, ...) si trovano in base alle impostazioni nel modello di esportazione. In questo esempio, alcune risorse sono inferiori a `<unzip-dir>/etc`, alcune inferiori a `<unzip-dir>/<page-path>`.

1. Aprite il file html della pagina ( `<unzip-dir>/<page-path>.html`) nel browser per controllare il rendering.

## Creazione di una configurazione di esportazione di pagina per il sito {#creating-a-page-exporter-configuration-for-your-site}

L&#39;esportatore di pagine si basa sul framework Content Sync (Sincronizzazione contenuti). Le configurazioni disponibili nella finestra di dialogo delle proprietà della pagina sono modelli di configurazione. Definiscono tutte le dipendenze richieste per una pagina. Quando viene attivata l’esportazione di una pagina, viene utilizzato il modello di configurazione e sia il percorso della pagina che il percorso di progettazione vengono applicati dinamicamente alla configurazione. Il file zip viene quindi creato utilizzando la funzionalità standard di sincronizzazione dei contenuti.

AEM incorpora alcuni modelli, tra cui:

* Un valore predefinito in `/etc/contentsync/templates/default`. Modello:

   * È il modello di fallback quando non viene trovato alcun modello di configurazione nella directory archivio.
   * Può fungere da base per un nuovo modello di configurazione.

* Uno dedicato al sito **Geometrixx**, all&#39;indirizzo `/etc/contentsync/templates/geometrixx`. Questo modello può essere utilizzato come esempio per crearne uno nuovo.

Per creare un modello di configurazione per l’esportazione di pagine:

1. In **CRXDE Lite**, creare un nodo sotto `/etc/contentsync/templates`:

   * Nome: ad esempio `mysite`. Il nome viene visualizzato nella finestra di dialogo delle proprietà della pagina quando si sceglie il modello di esportazione della pagina.
   * Tipo: `nt:unstructured`

1. Sotto il nodo del modello, denominato qui `mysite`, create una struttura di nodi utilizzando i nodi di configurazione descritti di seguito.

### Nodi di configurazione esportazione pagina {#page-exporter-configuration-nodes}

Il modello di configurazione è costituito da una struttura di nodi. Ogni nodo ha una proprietà `type` che definisce un&#39;azione specifica nel processo di creazione del file zip. Per ulteriori dettagli sulla proprietà type, consultate la sezione Panoramica dei tipi di configurazione nella pagina Framework di sincronizzazione dei contenuti.

Per creare un modello di configurazione per l’esportazione è possibile utilizzare i nodi seguenti:

**nodo paginaIl nodo pagina viene utilizzato per copiare il codice HTML della pagina nel file zip.** Ha le seguenti caratteristiche:

* È un nodo obbligatorio.
* Si trova sotto `/etc/contentsync/templates/<sitename>`.
* Il nome è `page`.
* Il tipo di nodo è `nt:unstructured`

Il nodo `page` ha le seguenti proprietà:

* Una proprietà `type` impostata con il valore `pages`.

* Non dispone di una proprietà `path` in quanto il percorso della pagina corrente viene copiato in modo dinamico nella configurazione.

* Le altre proprietà sono descritte nella sezione Panoramica dei tipi di configurazione del framework Content Sync.

**rewrite** nodeIl nodo di riscrittura definisce il modo in cui i collegamenti vengono riscritti nella pagina esportata. I collegamenti riscritti possono puntare ai file inclusi nel file zip o alle risorse sul server.

Per una descrizione completa del nodo `rewrite`, fare riferimento alla pagina Content Sync (Sincronizzazione contenuto).

**nodo di progettazioneIl nodo di progettazione viene utilizzato per copiare la progettazione utilizzata per la pagina esportata.** Ha le seguenti caratteristiche:

* È facoltativo.
* Si trova sotto `/etc/contentsync/templates/<sitename>`.
* Il nome è `design`.
* Il tipo di nodo è `nt:unstructured`.

Il nodo `design` ha le seguenti proprietà:

* Una proprietà `type` impostata sul valore `copy`.

* Non dispone di una proprietà `path` in quanto il percorso della pagina corrente viene copiato in modo dinamico nella configurazione.

**nodo genericoUn nodo generico viene utilizzato per copiare nel file zip risorse come file clientlibs .js o .css.** Ha le seguenti caratteristiche:

* È facoltativo.
* Si trova sotto `/etc/contentsync/templates/<sitename>`.
* Non ha un nome specifico.
* Il tipo di nodo è `nt:unstructured`.
* Possiede una proprietà `type` ed eventuali proprietà correlate `type` come definito nella sezione Panoramica dei tipi di configurazione del framework Content Sync.

Ad esempio, il seguente nodo di configurazione copia i file clientlibs .js geometrixx nel file zip:

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

Il modello di configurazione per l&#39;esportazione delle pagine **Geometrixx** mostra come è possibile configurare l&#39;esportazione delle pagine. Per visualizzare la struttura dei nodi del modello nel browser come formato json, richiedi il seguente URL:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Implementazione di una configurazione personalizzata**

Come avrete notato nella struttura del nodo, il modello di configurazione per l&#39;esportazione delle pagine **Geometrixx** ha un nodo `logo` con una proprietà `type` impostata su `image`. Si tratta di un tipo di configurazione speciale creato per copiare il logo immagine nel file zip. Per soddisfare alcuni requisiti specifici, potrebbe essere necessario implementare una proprietà `type` personalizzata: a tal fine, fate riferimento alla sezione Implementazione di un gestore di aggiornamenti personalizzato nella pagina Content Sync (Sincronizzazione contenuti).

## Esportazione programmata di una pagina {#programmatically-exporting-a-page}

Per esportare una pagina a livello di programmazione, è possibile utilizzare il servizio [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI. Questo servizio consente di:

* Esportate una pagina e scrivete la risposta del servlet HTTP.
* Esportate una pagina e salvate il file zip in un percorso specifico.

Il servlet associato al selettore `export` e all&#39;estensione `zip` utilizza il servizio PageExporter.

## Risoluzione dei problemi {#troubleshooting}

Se si verifica un problema con il download del file zip, è possibile eliminare il nodo `/var/contentsync` nella directory archivio e inviare di nuovo la richiesta di esportazione.

