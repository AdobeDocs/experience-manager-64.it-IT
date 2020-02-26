---
title: API HTTP di Assets
description: Scopri l’implementazione, il modello dati e le funzionalità dell’API HTTP Assets. Utilizzare l'API HTTP Assets per eseguire varie attività sulle risorse
contentOwner: AG
translation-type: tm+mt
source-git-commit: 57952323a3ae0990232506d551b91b724f830f20

---


# API HTTP di Assets {#assets-http-api}

L’API HTTP Assets consente di creare-leggere-aggiornare-eliminare (CRUD) le operazioni sulle risorse, inclusi i file binari, i metadati, le rappresentazioni e i commenti, nonché il contenuto strutturato utilizzando i frammenti di contenuto AEM. È esposto in `/api/assets` e viene implementato come REST API.

Per accedere all&#39;API:

1. Aprite il documento del servizio API in `http://[hostname]:[port]/api.json`.
1. Segui il collegamento del servizio Risorse `http://[hostname]:[server]/api/assets.json`.

La risposta API è un JSON per alcuni tipi mime e un codice di risposta per tutti i tipi mime. La risposta JSON è facoltativa e potrebbe non essere disponibile, ad esempio per i file PDF. Per ulteriori analisi o azioni, fai affidamento sul codice di risposta.

Dopo la [!UICONTROL disattivazione], una risorsa e le relative rappresentazioni non sono disponibili né tramite l’interfaccia Web di Assets né tramite l’API HTTP. L&#39;API restituisce un messaggio di errore 404 se l&#39;ora [!UICONTROL di] attivazione è futura o [!UICONTROL Ora] di disattivazione è passata.

## Dati, modello {#data-model}

L’API HTTP Assets espone due elementi principali, cartelle e risorse.

### Cartelle {#folders}

Le cartelle sono come directory nei file system tradizionali. Sono contenitori per altre cartelle o asserzioni. Le cartelle hanno i seguenti componenti:

**Entità**: Le entità di una cartella sono gli elementi secondari, che possono essere cartelle e risorse.

**Proprietà**:

```
name  -- Name of the folder. This is the same as the last segment in the URL path without the extension
title -- Optional title of the folder which can be displayed instead of its name
```

>[!NOTE]
>
>Alcune proprietà della cartella o della risorsa vengono mappate con un prefisso diverso. Il prefisso JCR di `jcr:title`, `jcr:description`, e `jcr:language` viene sostituito con `dc` prefisso. Quindi nel JSON restituito `dc:title` e `dc:description` contengono rispettivamente i valori di `jcr:title` e `jcr:description`.

**Le cartelle dei collegamenti** presentano tre collegamenti:

```xml
self      -- Link to itself
parent    -- Link to the parent folder
thumbnail -- (Optional) link to a folder thumbnail image
```

### Assets {#assets}

Le risorse sono elementi con più parti, che includono:

* Proprietà e metadati della risorsa.
* Rappresentazioni multiple, ad esempio la rappresentazione originale (che è la risorsa caricata originariamente), una miniatura e varie altre rappresentazioni. Rappresentazioni aggiuntive possono essere immagini di dimensioni diverse, codifiche video diverse o pagine estratte da PDF o Adobe InDesign.
* Commenti facoltativi.

In AEM una cartella contiene i seguenti componenti:

* Entità: Le rappresentazioni figlie di Risorse.
* Proprietà
* Collegamenti

L&#39;API HTTP Assets include le seguenti funzionalità:

* Recupero di un elenco di cartelle
* Creare una cartella
* Creare una risorsa
* Aggiorna binario risorsa
* Aggiornare i metadati delle risorse
* Creare una rappresentazione di una risorsa
* Aggiornare una rappresentazione di una risorsa
* Creare un commento sulla risorsa
* Copiare una cartella o una risorsa
* Spostare una cartella o una risorsa
* Eliminare una cartella, una risorsa o una rappresentazione

>[!NOTE]
>
>Per semplificare la lettura, gli esempi seguenti omettono la notazione cURL completa. In realtà la notazione è correlata con [Resty](https://github.com/micha/resty) , che è un wrapper di script per cURL.

**Prerequisiti**

* Passa a `https://[AEM_server]:[port]/system/console/configMgr`.
* Andate a Filtro **[!UICONTROL CSRF]** Adobe Granite.
* Accertatevi che la proprietà **[!UICONTROL Filter Methods]** includa: `POST`, `PUT`, `DELETE`.

## Recupero di un elenco di cartelle {#retrieve-a-folder-listing}

Recupera una rappresentazione Siren di una cartella esistente e delle relative entità figlie (sottocartelle o risorse).

**Richiesta**

```
GET /api/assets/myFolder.json
```

**Codici di risposta**

```
200 - OK - success
404 - NOT FOUND - folder does not exist or is not accessible
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

**Risposta**

La classe dell&#39;entità restituita è assets/folder.

Le proprietà delle entità contenute sono un sottoinsieme dell&#39;intero insieme di proprietà di ciascuna entità. Per ottenere una rappresentazione completa dell&#39;entità, i clienti devono recuperare il contenuto dell&#39;URL indicato dal collegamento con un `rel` di `self`.

## Creare una cartella {#create-a-folder}

Crea un nuovo `sling`: `OrderedFolder` nel percorso indicato. Se un &amp;ast; invece del nome di un nodo, il servlet utilizzerà il nome del parametro come nome del nodo. Accettato come dati della richiesta è una rappresentazione Siren della nuova cartella o un set di coppie nome-valore, codificate come `application/www-form-urlencoded` o `multipart`/ `form`- `data`, utile per creare una cartella direttamente da un modulo HTML. Inoltre, le proprietà della cartella possono essere specificate come parametri di query URL.

L&#39;operazione avrà esito negativo con un codice di `500` risposta se il nodo padre del percorso specificato non esiste. Se la cartella esiste già, viene restituito un codice di `409` risposta.

**Parametri**

```
name - Folder name
```

**Richiesta**

```
POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'
```

Oppure

```
POST /api/assets/* -F"name=myfolder" -F"title=My Folder"
```

**Codici di risposta**

```
201 - CREATED - on successful creation
409 - CONFLICT - if folder already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Creare una risorsa {#create-an-asset}

Crea una risorsa DAM nel percorso specificato con il file specificato. Se un &amp;ast; invece del nome di un nodo, il servlet utilizzerà il nome del parametro o il nome del file come nome del nodo.

**Parametri**

```
name - Asset name
file - File reference
```

**Richiesta**

```
POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"
```

o

```
POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"
```

**Codici di risposta**

```
201 - CREATED - if Asset has been created successfully
409 - CONFLICT - if Asset already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Aggiorna binario risorsa {#update-asset-binary}

Aggiorna il binario Assets (rappresentazione con nome originale). Questo attiverà il flusso di lavoro predefinito per le risorse, se configurato.

**Richiesta**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png
```

**Codici di risposta**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Aggiorna metadati risorsa {#update-asset-metadata}

Aggiorna le proprietà dei metadati della risorsa.

**Richiesta**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'
```

**Codici di risposta**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Creare una rappresentazione risorsa {#create-an-asset-rendition}

Crea una nuova rappresentazione di risorsa per una risorsa. Se il nome del parametro della richiesta non viene specificato, il nome del file viene utilizzato come nome di rappresentazione.

**Parametri**

```
name - Rendition name
file - File reference
```

**Richiesta**

```
POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"
```

o

```
POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"
```

**Codici di risposta**

```
201 - CREATED - if Rendition has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Aggiornare una rappresentazione risorsa {#update-an-asset-rendition}

Gli aggiornamenti sostituiscono rispettivamente una rappresentazione di risorsa con i nuovi dati binari.

**Richiesta**

```
PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png
```

**Codici di risposta**

```
200 - OK - if Rendition has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Creare un commento risorsa {#create-an-asset-comment}

Crea un nuovo commento sulla risorsa.

**Parametri**

```
message - Message
annotationData - Annotation data (JSON)
```

**Richiesta**

```
POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"
```

**Codici di risposta**

```
201 - CREATED - if Comment has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Copiare una cartella o una risorsa {#copy-a-folder-or-asset}

Copia una cartella o una risorsa nel percorso specificato in una nuova destinazione.

**Richiedi intestazioni**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - 'F' to prevent overwriting an existing destination
```

**Richiesta**

```
COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"
```

**Codici di risposta**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Spostare una cartella o una risorsa {#move-a-folder-or-asset}

Sposta una cartella o una risorsa nel percorso specificato in una nuova destinazione.

**Richiedi intestazioni**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - either 'T' to force deletion of existing resources or 'F' to prevent overwriting an existing resource.
```

**Richiesta**

```
MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"
```

**Codici di risposta**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Eliminare una cartella, una risorsa o una rappresentazione {#delete-a-folder-asset-or-rendition}

Elimina una risorsa (-tree) nel percorso specificato.

**Richiesta**

```
DELETE /api/assets/myFolder
```

o

```
DELETE /api/assets/myFolder/myAsset.png
```

o

```xml
DELETE /api/assets/myFolder/myAsset.png/renditions/original
```

**Codici di risposta**

```
200 - OK - if folder has been deleted successfully
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

