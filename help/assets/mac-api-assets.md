---
title: API HTTP di Assets in [!DNL Adobe Experience Manager].
description: Crea, leggi, aggiorna, elimina, gestisci risorse digitali utilizzando l’API HTTP in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
feature: APIs,Assets HTTP API,Developer Tools
role: Developer
exl-id: 3d7d078c-5046-489a-a8e0-258acaea7191
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1588'
ht-degree: 1%

---

# API HTTP di Assets {#assets-http-api}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’API HTTP di Assets consente operazioni di creazione-lettura-aggiornamento-eliminazione (CRUD) sulle risorse digitali, compresi i metadati, le rappresentazioni e i commenti, nonché contenuti strutturati mediante [!DNL Experience Manager] Frammenti di contenuto. È esposto a `/api/assets` e viene implementato come API REST.

Per accedere all’API:

1. Apri il documento del servizio API in `https://[hostname]:[port]/api.json`.
1. Segui il collegamento al servizio Assets che porta a `https://[hostname]:[server]/api/assets.json`.

La risposta API è un file JSON per alcuni tipi MIME e un codice di risposta per tutti i tipi MIME. La risposta JSON è facoltativa e potrebbe non essere disponibile, ad esempio per i file PDF. Per ulteriori analisi o azioni, fai riferimento al codice di risposta.

Dopo la [!UICONTROL Ora di disattivazione], una risorsa e i relativi rendering non sono disponibili tramite il [!DNL Assets] interfaccia web e tramite l’API HTTP. L&#39;API restituisce un messaggio di errore 404 se la [!UICONTROL Ora di attivazione] è in futuro o [!UICONTROL Ora di disattivazione] è nel passato.

>[!CAUTION]
>
>[L’API HTTP aggiorna le proprietà dei metadati](#update-asset-metadata) in `jcr` spazio dei nomi. Tuttavia, l’interfaccia utente di Experience Manager aggiorna le proprietà dei metadati nel `dc` spazio dei nomi.

## Modello dati {#data-model}

L’API HTTP di Assets espone due elementi principali, cartelle e risorse (per le risorse standard).

### Cartelle {#folders}

Le cartelle sono simili alle directory dei file system tradizionali. Sono contenitori per altre cartelle o asserzioni. Le cartelle hanno i seguenti componenti:

**Entità**: Le entità di una cartella sono i relativi elementi secondari, che possono essere cartelle e risorse.

**Proprietà**:

* `name` è il nome della cartella. È lo stesso dell’ultimo segmento nel percorso URL senza estensione.
* `title` è un titolo facoltativo della cartella che può essere visualizzato al posto del suo nome.

>[!NOTE]
>
>Alcune proprietà della cartella o della risorsa sono mappate a un prefisso diverso. La `jcr` prefisso `jcr:title`, `jcr:description`e `jcr:language` sono sostituiti con `dc` Prefisso. Quindi nel JSON restituito, `dc:title` e `dc:description` contengono i valori di `jcr:title` e `jcr:description`, rispettivamente.

**Collegamenti** Le cartelle mostrano tre collegamenti:

* `self`: Collega a se stesso.
* `parent`: Collega alla cartella principale.
* `thumbnail`: (Facoltativo) collega a un&#39;immagine miniatura della cartella.

### Risorse {#assets}

Ad Experience Manager, una risorsa contiene i seguenti elementi:

* Proprietà e metadati della risorsa.
* Rappresentazioni multiple, come il rendering originale (che è la risorsa originariamente caricata), una miniatura e varie altre rappresentazioni. Rappresentazioni aggiuntive possono essere immagini di dimensioni diverse, codifiche video diverse o pagine estratte da file PDF o Adobe InDesign.
* Commenti facoltativi.

In [!DNL Experience Manager] una cartella presenta i seguenti componenti:

* Entità: Gli elementi secondari delle risorse sono le relative rappresentazioni.
* Proprietà.
* Collegamenti.

L’API HTTP di Assets include le seguenti funzionalità:

* [Recupera elenco cartelle](#retrieve-a-folder-listing).
* [Creare una cartella](#create-a-folder).
* [Creare una risorsa](#create-an-asset).
* [Aggiorna binario risorsa](#update-asset-binary).
* [Aggiornare i metadati delle risorse](#update-asset-metadata).
* [Creare un rendering delle risorse](#create-an-asset-rendition).
* [Aggiornare un rendering di una risorsa](#update-an-asset-rendition).
* [Creare un commento sulla risorsa](#create-an-asset-comment).
* [Copiare una cartella o una risorsa](#copy-a-folder-or-asset).
* [Spostare una cartella o una risorsa](#move-a-folder-or-asset).
* [Eliminare una cartella, una risorsa o un rendering](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>Per semplificare la leggibilità, gli esempi seguenti omettono la notazione cURL completa. Infatti la notazione è correlata con [Riposato](https://github.com/micha/resty) che è un wrapper di script per `cURL`.

**Prerequisiti**

* Accesso `https://[aem_server]:[port]/system/console/configMgr`.
* Passa a **[!UICONTROL Filtro CSRF Granite Adobe]**.
* Assicurati che la proprietà **[!UICONTROL Metodi di Filtro]** include: `POST`, `PUT`, `DELETE`.

## Recupera elenco cartelle {#retrieve-a-folder-listing}

Recupera una rappresentazione Siren di una cartella esistente e delle relative entità secondarie (sottocartelle o risorse).

**Richiesta**: `GET /api/assets/myFolder.json`

**Codici di risposta**: I codici di risposta sono:

* 200 - OK - successo.
* 404 - NON TROVATO - la cartella non esiste o non è accessibile.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

**Risposta**: La classe dell’entità restituita è una risorsa o una cartella. Le proprietà delle entità contenute sono un sottoinsieme dell&#39;intero insieme di proprietà di ciascuna entità. Per ottenere una rappresentazione completa dell’entità, i clienti devono recuperare il contenuto dell’URL indicato dal collegamento con un `rel` di `self`.

## Crea una cartella . {#create-a-folder}

Crea un nuovo `sling`: `OrderedFolder` nel percorso indicato. Se `*` viene fornito al posto del nome di un nodo, il servlet utilizza il nome del parametro come nome del nodo. Accettati come dati di richiesta è una rappresentazione Siren della nuova cartella o un set di coppie nome-valore, codificate come `application/www-form-urlencoded` o `multipart`/ `form`- `data`, utile per creare una cartella direttamente da un modulo HTML. Inoltre, le proprietà della cartella possono essere specificate come parametri di query URL.

Una chiamata API non riesce con un `500` codice di risposta se il nodo principale del percorso fornito non esiste. Una chiamata restituisce un codice di risposta `409` se la cartella esiste già.

**Parametri**: `name` è il nome della cartella.

**Richiesta**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Codici di risposta**: I codici di risposta sono:

* 201 - CREATO - sulla creazione di successo.
* 409 - CONFLICT - se la cartella esiste già.
* 412 - PRECONDIZIONE NON RIUSCITA - se non è possibile trovare o accedere alla raccolta radice.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

## Creare una risorsa {#create-an-asset}

Posiziona il file fornito nel percorso fornito per creare una risorsa nell’archivio DAM. Se `*` viene fornito al posto del nome di un nodo, il servlet utilizza il nome del parametro o il nome del file come nome del nodo.

**Parametri**: I parametri sono `name` per il nome della risorsa e `file` per il riferimento al file.

**Richiesta**

* `POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"`
* `POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"`

**Codici di risposta**: I codici di risposta sono:

* 201 - CREATO - se Asset è stato creato con successo.
* 409 - CONFLITTO - se Asset esiste già.
* 412 - PRECONDIZIONE NON RIUSCITA - se non è possibile trovare o accedere alla raccolta radice.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

## Aggiornare un binario di risorse {#update-asset-binary}

Aggiorna il file binario di una risorsa (rendering con nome originale). Un aggiornamento attiva l’esecuzione del flusso di lavoro di elaborazione delle risorse predefinito, se configurato.

**Richiesta**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png`

**Codici di risposta**: I codici di risposta sono:

* 200 - OK - Se Asset è stato aggiornato correttamente.
* 404 - NON TROVATO - se non è stato possibile trovare o accedere a Asset nell’URI fornito.
* 412 - PRECONDIZIONE NON RIUSCITA - se non è possibile trovare o accedere alla raccolta radice.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

## Aggiornare i metadati delle risorse {#update-asset-metadata}

Aggiorna le proprietà dei metadati della risorsa. Se aggiorni una proprietà in `dc:` namespace, l’API aggiorna la stessa proprietà nel `jcr` spazio dei nomi. L’API non sincronizza le proprietà sotto i due namespace.

**Richiesta**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"jcr:title":"My Asset"}}'`

**Codici di risposta**: I codici di risposta sono:

* 200 - OK - Se Asset è stato aggiornato correttamente.
* 404 - NON TROVATO - se non è stato possibile trovare o accedere a Asset nell’URI fornito.
* 412 - PRECONDIZIONE NON RIUSCITA - se non è possibile trovare o accedere alla raccolta radice.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

### Sincronizza l&#39;aggiornamento dei metadati tra `dc` e `jcr` namespace {#sync-metadata-between-namespaces}

Il metodo API aggiorna le proprietà dei metadati nel `jcr` spazio dei nomi. Gli aggiornamenti effettuati utilizzando l’interfaccia Touch modificano le proprietà dei metadati nel `dc` spazio dei nomi. Per sincronizzare i valori dei metadati tra `dc` e `jcr` namespace, puoi creare un flusso di lavoro e configurare un Experience Manager per eseguire il flusso di lavoro al momento della modifica della risorsa. Utilizza uno script ECMA per sincronizzare le proprietà dei metadati richieste. Lo script di esempio seguente sincronizza la stringa del titolo tra `dc:title` e `jcr:title`.

```javascript
var workflowData = workItem.getWorkflowData();
if (workflowData.getPayloadType() == "JCR_PATH")
{
 var path = workflowData.getPayload().toString();
 var node = workflowSession.getSession().getItem(path);
 var metadataNode = node.getNode("jcr:content/metadata");
 var jcrcontentNode = node.getNode("jcr:content");
if (jcrcontentNode.hasProperty("jcr:title"))
{
 var jcrTitle = jcrcontentNode.getProperty("jcr:title");
 metadataNode.setProperty("dc:title", jcrTitle.toString());
 metadataNode.save();
}
}
```

## Creare un rendering delle risorse {#create-an-asset-rendition}

Crea un nuovo rendering della risorsa per una risorsa. Se il nome del parametro della richiesta non viene fornito, il nome del file viene utilizzato come nome di rendering.

**Parametri**: I parametri sono `name` nome del rendering e `file` come riferimento di file.

**Richiesta**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Codici di risposta**: I codici di risposta sono:

* 201 - CREATO - se la rappresentazione è stata creata correttamente.
* 404 - NON TROVATO - se non è stato possibile trovare o accedere a Asset nell’URI fornito.
* 412 - PRECONDIZIONE NON RIUSCITA - se non è possibile trovare o accedere alla raccolta radice.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

## Aggiornare un rendering di una risorsa {#update-an-asset-rendition}

Gli aggiornamenti sostituiscono rispettivamente il rendering di una risorsa con i nuovi dati binari.

**Richiesta**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Codici di risposta**: I codici di risposta sono:

* 200 - OK - se Rendering è stato aggiornato correttamente.
* 404 - NON TROVATO - se non è stato possibile trovare o accedere a Asset nell’URI fornito.
* 412 - PRECONDIZIONE NON RIUSCITA - se non è possibile trovare o accedere alla raccolta radice.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

## Aggiungere un commento a una risorsa {#create-an-asset-comment}

Crea un nuovo commento sulla risorsa.

**Parametri**: I parametri sono `message` per il corpo del messaggio del commento e `annotationData` per i dati Annotation in formato JSON.

**Richiesta**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Codici di risposta**: I codici di risposta sono:

* 201 - CREATO - se il Commento è stato creato correttamente.
* 404 - NON TROVATO - se non è stato possibile trovare o accedere a Asset nell’URI fornito.
* 412 - PRECONDIZIONE NON RIUSCITA - se non è possibile trovare o accedere alla raccolta radice.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

## Copiare una cartella o una risorsa {#copy-a-folder-or-asset}

Copia una cartella o una risorsa disponibile nel percorso specificato in una nuova destinazione.

**Intestazioni richieste**: I parametri sono:

* `X-Destination` - un nuovo URI di destinazione nell’ambito della soluzione API in cui copiare la risorsa.
* `X-Depth` - o `infinity` o `0`. Utilizzo `0` copia solo la risorsa e le relative proprietà e non i relativi elementi secondari.
* `X-Overwrite` - Utilizzo `F` per evitare la sovrascrittura di una risorsa nella destinazione esistente.

**Richiesta**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Codici di risposta**: I codici di risposta sono:

* 201 - CREATO - se la cartella/risorsa è stata copiata in una destinazione non esistente.
* 204 - NO CONTENT - Se la cartella o la risorsa è stata copiata in una destinazione esistente.
* 412 - PRECONDIZIONE NON RIUSCITA - se manca un&#39;intestazione di richiesta.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

## Spostare una cartella o una risorsa {#move-a-folder-or-asset}

Sposta una cartella o una risorsa nel percorso specificato in una nuova destinazione.

**Intestazioni richieste**: I parametri sono:

* `X-Destination` - un nuovo URI di destinazione nell’ambito della soluzione API in cui copiare la risorsa.
* `X-Depth` - o `infinity` o `0`. Utilizzo `0` copia solo la risorsa e le relative proprietà e non i relativi elementi secondari.
* `X-Overwrite` - Utilizzare `T` per forzare l&#39;eliminazione di risorse esistenti o `F` per evitare la sovrascrittura di una risorsa esistente.

**Richiesta**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**Codici di risposta**: I codici di risposta sono:

* 201 - CREATO - se la cartella/risorsa è stata copiata in una destinazione non esistente.
* 204 - NO CONTENT - Se la cartella o la risorsa è stata copiata in una destinazione esistente.
* 412 - PRECONDIZIONE NON RIUSCITA - se manca un&#39;intestazione di richiesta.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.

## Eliminare una cartella, una risorsa o un rendering {#delete-a-folder-asset-or-rendition}

Elimina una risorsa (-tree) nel percorso specificato.

**Richiesta**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Codici di risposta**: I codici di risposta sono:

* 200 - OK - Se la cartella è stata eliminata correttamente.
* 412 - PRECONDIZIONE NON RIUSCITA - se non è possibile trovare o accedere alla raccolta radice.
* 500 - ERRORE SERVER INTERNO - se qualcos&#39;altro non funziona.
