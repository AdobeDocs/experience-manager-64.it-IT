---
title: Esportatore di pagine
seo-title: The Page Exporter
description: Scopri come utilizzare AEM Page Exporter.
seo-description: Learn how to use the AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# Esportatore di pagine{#the-page-exporter}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM consente di esportare una pagina come pagina web completa, inclusi immagini, file .js e .css.

Una volta configurata l’esportazione, richiedi semplicemente una pagina nel browser sostituendo `html` con `export.zip` nell’URL e ottieni un download di file zip contenente la pagina sottoposta a rendering in formato html e le risorse a cui si fa riferimento. Tutti i percorsi nella pagina, ad esempio i percorsi delle immagini, vengono riscritti in modo che puntino ai file inclusi nel file zip o alle risorse sul server.

## Esportazione di una pagina {#exporting-a-page}

I passaggi seguenti descrivono come esportare una pagina e presuppongono che esista un modello di configurazione per l’esportazione per il sito. Un modello di configurazione definisce il modo in cui una pagina viene esportata ed è specifica per il sito. Per creare un modello di configurazione, fai riferimento alla sezione [Creazione di una configurazione di esportazione pagina per il sito](#creating-a-page-exporter-configuration-for-your-site) sezione .

Per esportare una pagina:

1. Nel browser, apri la pagina. Ad esempio:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Apri la finestra di dialogo delle proprietà della pagina, seleziona la **Avanzate** ed espandi la **Esporta** set di campi.

1. Fai clic sull’icona lente di ingrandimento e seleziona un modello di configurazione. Seleziona la **geometrixx** , poiché è quello predefinito per il sito Geometrixx. Fai clic su **OK**.

1. Fai clic su **OK** per chiudere la finestra di dialogo delle proprietà della pagina.
1. Richiedere la pagina sostituendo `html` con `export.zip` nell’URL.

1. Scarica la `<page-name>.export.zip` nel file system.

1. Nel file system, decomprimi il file:

   * il file html della pagina ( `<page-name>.html`) è disponibile di seguito `<unzip-dir>/<page-path>`
   * altre risorse (file .js, file .css, immagini, ...) si trovano in base alle impostazioni nel modello di esportazione. In questo esempio, di seguito sono riportate alcune risorse `<unzip-dir>/etc`, alcuni sotto `<unzip-dir>/<page-path>`.

1. Apri il file HTML della pagina ( `<unzip-dir>/<page-path>.html`) nel browser per controllare il rendering.

## Creazione di una configurazione di esportazione pagina per il sito {#creating-a-page-exporter-configuration-for-your-site}

La funzione di esportazione della pagina si basa sul framework Content Sync. Le configurazioni disponibili nella finestra di dialogo delle proprietà della pagina sono modelli di configurazione. Definiscono tutte le dipendenze richieste per una pagina. Quando viene attivata un’esportazione di pagina, viene utilizzato il modello di configurazione e sia il percorso della pagina che il percorso di progettazione vengono applicati dinamicamente alla configurazione. Il file zip viene quindi creato utilizzando la funzionalità standard Content Sync.

AEM incorpora alcuni modelli, tra cui:

* Uno predefinito a `/etc/contentsync/templates/default`. Questo modello:

   * È il modello di fallback quando non viene trovato alcun modello di configurazione nel repository.
   * Può fungere da base per un nuovo modello di configurazione.

* Uno dedicato al **Geometrixx** sito, `/etc/contentsync/templates/geometrixx`. Questo modello può essere utilizzato come esempio per crearne uno nuovo.

Per creare un modello di configurazione di esportazione pagina:

1. In **CRXDE Lite**, crea un nodo qui sotto `/etc/contentsync/templates`:

   * Nome: ad esempio `mysite`. Il nome viene visualizzato nella finestra di dialogo delle proprietà della pagina quando si sceglie il modello di esportazione della pagina.
   * Tipo: `nt:unstructured`

1. Sotto il nodo del modello, chiamato qui `mysite`, crea una struttura di nodo utilizzando i nodi di configurazione descritti di seguito.

### Nodi di configurazione dell’esportatore di pagine {#page-exporter-configuration-nodes}

Il modello di configurazione è costituito da una struttura di nodo. Ogni nodo ha un `type` che definisce un&#39;azione specifica nel processo di creazione del file zip. Per ulteriori dettagli sulla proprietà type , consulta la sezione Panoramica dei tipi di configurazione nella pagina del framework Content Sync .

I seguenti nodi possono essere utilizzati per creare un modello di configurazione dell’esportazione:

**nodo pagina** Il nodo della pagina viene utilizzato per copiare l’html della pagina nel file zip. Ha le seguenti caratteristiche:

* È un nodo obbligatorio.
* Si trova sotto `/etc/contentsync/templates/<sitename>`.
* Il suo nome è `page`.
* Il tipo di nodo è `nt:unstructured`

La `page` il nodo ha le seguenti proprietà:

* A `type` impostata con il valore `pages`.

* Non ha un `path` come percorso della pagina corrente viene copiata in modo dinamico nella configurazione.

* Le altre proprietà sono descritte nella sezione Panoramica dei tipi di configurazione del framework Content Sync.

**nodo di riscrittura** Il nodo di riscrittura definisce il modo in cui i collegamenti vengono riscritti nella pagina esportata. I collegamenti riscritti possono puntare ai file inclusi nel file zip o alle risorse sul server.

Per una descrizione completa della `rewrite` nodo.

**nodo di progettazione** Il nodo di progettazione viene utilizzato per copiare la progettazione utilizzata per la pagina esportata. Ha le seguenti caratteristiche:

* È facoltativo.
* Si trova sotto `/etc/contentsync/templates/<sitename>`.
* Il suo nome è `design`.
* Il tipo di nodo è `nt:unstructured`.

La `design` il nodo ha le seguenti proprietà:

* A `type` impostato sul valore `copy`.

* Non ha un `path` come percorso della pagina corrente viene copiata in modo dinamico nella configurazione.

**nodo generico** Un nodo generico viene utilizzato per copiare risorse come file clientlibs .js o .css nel file zip. Ha le seguenti caratteristiche:

* È facoltativo.
* Si trova sotto `/etc/contentsync/templates/<sitename>`.
* Non ha un nome specifico.
* Il tipo di nodo è `nt:unstructured`.
* Ha `type` proprietà ed eventuali `type` proprietà correlate definite nella sezione Panoramica dei tipi di configurazione del framework Content Sync.

Ad esempio, il seguente nodo di configurazione copia i file geometrixx clientlibs .js nel file zip:

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

La **Geometrixx** il modello di configurazione per l’esportazione di pagine mostra come è possibile configurare un’esportazione di pagine. Per visualizzare la struttura del nodo del modello nel browser come formato json, richiedi il seguente URL:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Implementazione di una configurazione personalizzata**

Come avrete notato nella struttura del nodo, la **Geometrixx** il modello di configurazione per l’esportazione di pagine presenta `logo` nodo con un `type` proprietà impostata su `image`. Si tratta di un tipo di configurazione speciale creato per copiare il logo immagine nel file zip. Per soddisfare alcuni requisiti specifici, potrebbe essere necessario implementare un `type` proprietà: a tale scopo, consulta la sezione Implementazione di un gestore di aggiornamenti personalizzati nella pagina Sincronizzazione dei contenuti .

## Esportazione di una pagina a livello di programmazione {#programmatically-exporting-a-page}

Per esportare una pagina a livello di programmazione, puoi utilizzare la funzione [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) Servizio OSGI. Questo servizio consente di:

* Esporta una pagina e scrivi nella risposta del servlet HTTP.
* Esporta una pagina e salva il file zip in una posizione specifica.

Il servlet associato al `export` selettore e `zip` l&#39;estensione utilizza il servizio PageExporter.

## Risoluzione dei problemi {#troubleshooting}

Se si verifica un problema con il download del file zip, è possibile eliminare il `/var/contentsync` nel repository e invia nuovamente la richiesta di esportazione.
