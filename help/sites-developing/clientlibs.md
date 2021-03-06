---
title: Utilizzo delle librerie lato client
seo-title: Utilizzo delle librerie lato client
description: AEM fornisce Cartelle libreria lato client che consentono di memorizzare il codice lato client nell'archivio, organizzarlo in categorie e definire quando e come ciascuna categoria di codice deve essere distribuita al client
seo-description: AEM fornisce Cartelle libreria lato client che consentono di memorizzare il codice lato client nell'archivio, organizzarlo in categorie e definire quando e come ciascuna categoria di codice deve essere distribuita al client
uuid: c022992d-a6db-4abb-8c53-4c91d6eed225
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 619de2e4-d7bd-4ca6-9763-1efa8b2dec05
translation-type: tm+mt
source-git-commit: 8e82c691affe3b2c4108beec394cc0ba2d607b61
workflow-type: tm+mt
source-wordcount: '2889'
ht-degree: 0%

---


# Utilizzo delle librerie lato client{#using-client-side-libraries}

I siti Web moderni si affidano in larga misura all&#39;elaborazione sul lato client basata su codice JavaScript e CSS complessi. L&#39;organizzazione e l&#39;ottimizzazione della gestione di questo codice può essere un problema complicato.

Per risolvere il problema, AEM fornisce **Cartelle libreria lato client** che consentono di memorizzare il codice lato client nell&#39;archivio, organizzarlo in categorie e definire quando e come ciascuna categoria di codice deve essere distribuita al client. Il sistema di libreria lato client si occupa quindi di generare i collegamenti corretti nella pagina Web finale per caricare il codice corretto.

## Funzionamento delle librerie lato client in AEM {#how-client-side-libraries-work-in-aem}

Il modo standard per includere una libreria lato client (ovvero un file JS o CSS) nell&#39;HTML di una pagina consiste semplicemente nell&#39;includere un tag `<script>` o `<link>` nel JSP per tale pagina, contenente il percorso del file in questione. Esempio,

```xml
...
<head>
   ...
   <script type="text/javascript" src="/etc/clientlibs/granite/jquery/source/1.8.1/jquery-1.8.1.js"></script>
   ...
</head>
...
```

Anche se questo approccio funziona in AEM, può causare problemi quando le pagine e i loro componenti diventano complessi. In tali casi esiste il rischio che più copie della stessa libreria JS possano essere incluse nell’output HTML finale. Per evitare questo problema e consentire l&#39;organizzazione logica delle librerie lato client AEM utilizzare **cartelle libreria lato client**.

Una cartella libreria lato client è un nodo di repository di tipo `cq:ClientLibraryFolder`. È la definizione in [Notazione CND](https://jackrabbit.apache.org/node-type-notation.html) è

```shell
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

Per impostazione predefinita, i nodi `cq:ClientLibraryFolder` possono essere posizionati ovunque nelle sottostrutture `/apps`, `/libs` e `/etc` dell&#39;archivio (queste impostazioni predefinite e altre impostazioni possono essere controllate tramite il pannello **Adobe Granite HTML Library Manager** della [console di sistema](http://localhost:4502/system/console/configMgr)).

Ogni file `cq:ClientLibraryFolder` viene popolato con un set di file JS e/o CSS, insieme ad alcuni file di supporto (vedere di seguito). Le proprietà di `cq:ClientLibraryFolder` sono configurate come segue:

* `categories`: Identifica le categorie in cui il set di file JS e/o CSS entro questo  `cq:ClientLibraryFolder` autunno. La proprietà `categories`, con un valore multiplo, consente a una cartella di libreria di appartenere a più categorie (vedere di seguito per informazioni su come potrebbe essere utile).

* `dependencies`: Si tratta di un elenco di altre categorie di libreria client da cui dipende la cartella libreria. Ad esempio, a due nodi `cq:ClientLibraryFolder` `F` e `G`, se un file in `F` richiede un altro file in `G` per funzionare correttamente, almeno uno dei `categories` di `G` deve essere compreso tra `dependencies` di `F`.

* `embed`: Utilizzato per incorporare il codice da altre librerie. Se il nodo F incorpora i nodi G e H, l&#39;HTML risultante sarà una concentrazione di contenuto dai nodi G e H.
* `allowProxy`: Se una libreria client si trova in  `/apps`, questa proprietà consente l&#39;accesso tramite servlet proxy. Vedere [Individuazione di una cartella della libreria client e Utilizzo del servlet delle librerie client proxy](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) di seguito.

## Riferimento a librerie lato client {#referencing-client-side-libraries}

Poiché HTL è la tecnologia preferita per lo sviluppo di siti AEM, HTL dovrebbe essere utilizzato per includere librerie lato client in AEM. Tuttavia è anche possibile farlo utilizzando JSP.

### Utilizzo di HTL {#using-htl}

In HTL, le librerie client vengono caricate tramite un modello helper fornito da AEM, accessibile tramite [ `data-sly-use`](https://helpx.adobe.com/experience-manager/htl/using/block-statements.html#use). In questo file sono disponibili tre modelli, che possono essere richiamati tramite [ `data-sly-call`](https://helpx.adobe.com/experience-manager/htl/using/block-statements.html#template-call):

* **css**  - Carica solo i file CSS delle librerie client di riferimento.
* **js** - Carica solo i file JavaScript delle librerie client di riferimento.
* **all** - Carica tutti i file delle librerie client di riferimento (sia CSS che JavaScript).

Ogni modello di supporto prevede un&#39;opzione `categories` per fare riferimento alle librerie client desiderate. Tale opzione può essere una matrice di valori stringa o una stringa contenente un elenco di valori separati da virgola.

Per ulteriori dettagli ed esempi di utilizzo, consultare la [Guida introduttiva al linguaggio HTML Template Language](https://helpx.adobe.com/experience-manager/htl/using/getting-started.html#loading-client-libraries).

### Utilizzo di JSP {#using-jsp}

Aggiungete un tag `ui:includeClientLib` al codice JSP per aggiungere un collegamento alle librerie client nella pagina HTML generata. Per fare riferimento alle librerie, utilizzare il valore della proprietà `categories` del nodo `ui:includeClientLib`.

```
<%@taglib prefix="ui" uri="https://www.adobe.com/taglibs/granite/ui/1.0" %>
<ui:includeClientLib categories="<%= categories %>" />
```

Ad esempio, il nodo `/etc/clientlibs/foundation/jquery` è di tipo `cq:ClientLibraryFolder` con una proprietà category di valore `cq.jquery`. Il codice seguente in un file JSP fa riferimento alle librerie:

```xml
<ui:includeClientLib categories="cq.jquery"/>
```

La pagina HTML generata contiene il seguente codice:

```xml
<script type="text/javascript" src="/etc/clientlibs/foundation/jquery.js"></script>
```

Per informazioni complete, inclusi gli attributi per filtrare le librerie JS, CSS o di temi, vedete [ui:includeClientLib](/help/sites-developing/taglib.md#amp-lt-ui-includeclientlib).

>[!CAUTION]
>
>`<cq:includeClientLib>`, che in passato veniva comunemente usato per includere le librerie client, è stato dichiarato obsoleto a partire dal AEM 5.6.  [ `<ui:includeClientLib>`](/help/sites-developing/taglib.md#amp-lt-ui-includeclientlib) devono essere utilizzati come descritto sopra.

## Creazione di cartelle libreria client {#creating-client-library-folders}

Creare un nodo `cq:ClientLibraryFolder` per definire le librerie JavaScript e Cascading Style Sheet e renderle disponibili per le pagine HTML. Utilizzare la proprietà `categories` del nodo per identificare le categorie di libreria alle quali appartiene.

Il nodo contiene uno o più file sorgente che, in fase di esecuzione, vengono uniti in un singolo file JS e/o CSS. Il nome del file generato è il nome del nodo con l&#39;estensione del nome di file `.js` o `.css`. Ad esempio, il nodo della libreria denominato `cq.jquery` restituisce il file generato denominato `cq.jquery.js` o `cq.jquery.css`.

Le cartelle della libreria client contengono i seguenti elementi:

* I file sorgente JS e/o CSS da unire.
* Risorse che supportano gli stili CSS, ad esempio i file di immagine.

   **Nota:** potete utilizzare le sottocartelle per organizzare i file sorgente.
* Un file `js.txt` e/o un file `css.txt` che identifica i file sorgente da unire nei file JS e/o CSS generati.

![clientlibarch](assets/clientlibarch.png)

Per informazioni sui requisiti specifici per le librerie client per i widget, vedere [Utilizzo ed estensione dei widget](/help/sites-developing/widgets.md).

Il client Web deve disporre delle autorizzazioni per accedere al nodo `cq:ClientLibraryFolder`. È inoltre possibile esporre le librerie dalle aree protette dell&#39;archivio (vedere Incorporazione di codice da altre librerie, di seguito).

### Sostituzione delle librerie in /lib {#overriding-libraries-in-lib}

Le cartelle della libreria client che si trovano sotto `/apps` hanno la precedenza rispetto alle cartelle omonime che si trovano in modo simile in `/libs`. Ad esempio, `/apps/cq/ui/widgets` ha la precedenza su `/libs/cq/ui/widgets`. Quando queste librerie appartengono alla stessa categoria, viene utilizzata la libreria seguente `/apps`.

### Individuazione di una cartella libreria client e utilizzo del servlet delle librerie client proxy {#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet}

Nelle versioni precedenti, le cartelle della libreria client si trovavano sotto `/etc/clientlibs` nella directory archivio. Questo è ancora supportato, tuttavia è consigliabile che le librerie client ora si trovino in `/apps`. Questo consente di individuare le librerie client accanto agli altri script, che si trovano generalmente sotto `/apps` e `/libs`.

>[!NOTE]
>
>Le risorse statiche sotto la cartella della libreria client devono trovarsi in una cartella denominata *resources*. Se le risorse statiche, come le immagini, non sono presenti nella cartella *resources*, non è possibile farvi riferimento in un&#39;istanza di pubblicazione. Esempio: http://localhost:4503/etc.clientlibs/geometrixx/components/clientlibs/resources/example.gif

>[!NOTE]
>
>Per isolare meglio il codice dal contenuto e dalla configurazione, si consiglia di individuare le librerie client in `/apps` e di esporle tramite `/etc.clientlibs` utilizzando la proprietà `allowProxy`.

Per rendere accessibili le librerie client in `/apps`, viene utilizzato un servlet proxy. Gli ACL sono ancora applicati alla cartella della libreria client, ma il servlet consente la lettura del contenuto tramite `/etc.clientlibs/` se la proprietà `allowProxy` è impostata su `true`.

Per accedere a una risorsa statica è possibile utilizzare il proxy solo se si trova sotto una risorsa sotto la cartella della libreria client.

Ad esempio:

* Hai una clientlib in `/apps/myproject/clientlibs/foo`
* L&#39;immagine è statica in `/apps/myprojects/clientlibs/foo/resources/icon.png`

Quindi si imposta la proprietà `allowProxy` su `foo` su true.

* È quindi possibile richiedere `/etc.clientlibs/myprojects/clientlibs/foo.js`
* È quindi possibile fare riferimento all&#39;immagine tramite `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

>[!CAUTION]
>
>Quando si utilizzano librerie client proxy, la configurazione del dispatcher AEM potrebbe richiedere un aggiornamento per garantire che gli URI con i clientlibs di estensione siano consentiti.

>[!CAUTION]
>
> Adobe consiglia di individuare le librerie client in `/apps` e renderle disponibili utilizzando il servlet proxy. Tuttavia, tenete presente che la best practice richiede ancora che i siti pubblici non includano mai nulla servito direttamente su un percorso `/apps` o `/libs`.

### Creare una cartella libreria client {#create-a-client-library-folder}

1. Aprite il CRXDE Lite in un browser Web ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Selezionate la cartella in cui desiderate individuare la cartella della libreria client e fate clic su **Crea > Crea nodo**.
1. Immettere un nome per il file libreria e selezionare `cq:ClientLibraryFolder` nell&#39;elenco Tipo. Fare clic su **OK**, quindi fare clic su **Salva tutto**.
1. Per specificare la categoria o le categorie a cui appartiene la libreria, selezionare il nodo `cq:ClientLibraryFolder`, aggiungere la seguente proprietà, quindi fare clic su **Salva tutto**:

   * Nome: category
   * Tipo: Stringa
   * Valore: Nome categoria
   * Multi: Select

1. Aggiungete i file sorgente alla cartella della libreria in qualsiasi modo. Ad esempio, utilizzate un client WebDav per copiare i file oppure create un file e create manualmente il contenuto.

   **Nota:** se necessario, potete organizzare i file sorgente in sottocartelle.

1. Selezionate la cartella della libreria client e fate clic su **Crea > Crea file**.
1. Nella casella Nome file digitare uno dei seguenti nomi di file e fare clic su OK:

   * **`js.txt`:** Utilizzate questo nome file per generare un file JavaScript.
   * **`css.txt`:** Utilizzate questo nome file per generare un foglio di stile a cascata.

1. Aprite il file e digitate il testo seguente per identificare la radice del percorso dei file sorgente:

   `#base=[root]`

   Sostituire `[root]` con il percorso della cartella che contiene i file sorgente, relativo al file TXT. Ad esempio, usate il testo seguente quando i file sorgente si trovano nella stessa cartella del file TXT:

   `#base=.`

   Il codice seguente imposta la radice come cartella denominata mobile sotto il nodo `cq:ClientLibraryFolder`:

   `#base=mobile`

1. Sulle righe sottostanti `#base=[root]`, digitare i percorsi dei file di origine relativi alla radice. Posizionare ciascun nome file su una riga separata.
1. Fare clic su **Salva tutto**.

### Collegamento a dipendenze {#linking-to-dependencies}

Quando il codice nella cartella della libreria client fa riferimento ad altre librerie, identificate le altre librerie come dipendenze. Nel JSP, il tag `ui:includeClientLib` che fa riferimento alla cartella della libreria client fa sì che il codice HTML includa un collegamento al file libreria generato e alle dipendenze.

Le dipendenze devono essere un&#39;altra `cq:ClientLibraryFolder`. Per identificare le dipendenze, aggiungi una proprietà al nodo `cq:ClientLibraryFolder` con i seguenti attributi:

* **Nome:** dipendenze
* **Tipo:** Stringa`[]`
* **Valori:** il valore della proprietà category del nodo cq:ClientLibraryFolder da cui dipende la cartella libreria corrente.

Ad esempio, il carattere / `etc/clientlibs/myclientlibs/publicmain` ha una dipendenza dalla libreria `cq.jquery`. L&#39;JSP che fa riferimento alla libreria client principale genera HTML che include il seguente codice:

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### Incorporazione del codice da altre librerie {#embedding-code-from-other-libraries}

Potete incorporare il codice da una libreria client a un&#39;altra libreria client. In fase di esecuzione, i file JS e CSS generati dalla libreria di incorporamento includono il codice della libreria incorporata.

L&#39;incorporazione del codice è utile per fornire l&#39;accesso alle librerie memorizzate nelle aree protette dell&#39;archivio.

#### Cartelle libreria client specifiche per l&#39;app {#app-specific-client-library-folders}

È consigliabile mantenere tutti i file relativi alle applicazioni nella cartella dell&#39;applicazione al di sotto di `/app`. È inoltre consigliabile negare l&#39;accesso ai visitatori del sito Web nella cartella `/app`. Per soddisfare entrambe le procedure ottimali, create una cartella della libreria client sotto la cartella `/etc` che incorpora la libreria client che si trova sotto `/app`.

Utilizzare la proprietà category per identificare la cartella della libreria client da incorporare. Per incorporare la libreria, aggiungere una proprietà al nodo `cq:ClientLibraryFolder` in cui incorporare, utilizzando i seguenti attributi di proprietà:

* **Nome:** embed
* **Tipo:** Stringa`[]`
* **Valore:** il valore della proprietà category del  `cq:ClientLibraryFolder` nodo da incorporare.

#### Utilizzo dell&#39;incorporazione per ridurre al minimo le richieste {#using-embedding-to-minimize-requests}

In alcuni casi, l&#39;HTML finale generato per la pagina tipica dall&#39;istanza di pubblicazione include un numero relativamente elevato di elementi `<script>`, in particolare se il sito utilizza le informazioni contestuali del client per l&#39;analisi o il targeting. Ad esempio, in un progetto non ottimizzato è possibile trovare la seguente serie di elementi `<script>` nell’HTML per una pagina:

```xml
<script type="text/javascript" src="/etc/clientlibs/granite/jquery.js"></script>
<script type="text/javascript" src="/etc/clientlibs/granite/utils.js"></script>
<script type="text/javascript" src="/etc/clientlibs/granite/jquery/granite.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/jquery.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/shared.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/personalization/kernel.js"></script>
```

In tali casi, può essere utile combinare tutti i codici libreria client richiesti in un singolo file in modo da ridurre il numero di richieste di andata e ritorno al caricamento della pagina. A questo scopo, è possibile `embed` inserire le librerie necessarie nella libreria client specifica per l&#39;app utilizzando la proprietà embed del nodo `cq:ClientLibraryFolder`.

Le seguenti categorie di libreria client sono incluse con AEM. È consigliabile incorporare solo quelli necessari per il funzionamento del sito specifico. Tuttavia, **è necessario mantenere l&#39;ordine indicato qui**:

1. `browsermap.standard`
1. `browsermap`
1. `jquery-ui`
1. `cq.jquery.ui`
1. `personalization`
1. `personalization.core`
1. `personalization.core.kernel`
1. `personalization.clientcontext.kernel`
1. `personalization.stores.kernel`
1. `personalization.kernel`
1. `personalization.clientcontext`
1. `personalization.stores`
1. `cq.collab.comments`
1. `cq.collab.feedlink`
1. `cq.collab.ratings`
1. `cq.collab.toggle`
1. `cq.collab.forum`
1. `cq.cleditor`

#### Percorsi nei file CSS {#paths-in-css-files}

Quando incorporate file CSS, il codice CSS generato utilizza percorsi verso risorse relative alla libreria di incorporamento. Ad esempio, la libreria accessibile al pubblico `/etc/client/libraries/myclientlibs/publicmain` incorpora la libreria client `/apps/myapp/clientlib`:

![screen_shot_2012-05-29at20122pm](assets/screen_shot_2012-05-29at20122pm.png)

Il file `main.css` contiene lo stile seguente:

```xml
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

Il file CSS generato dal nodo `publicmain` contiene il seguente stile, utilizzando l&#39;URL dell&#39;immagine originale:

```xml
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

### Utilizzo di una libreria per specifici gruppi di dispositivi mobili {#using-a-library-for-specific-mobile-groups}

Utilizzate la proprietà `channels` di una cartella libreria client per identificare il gruppo mobile che utilizza la libreria. La proprietà `channels` è utile quando librerie della stessa categoria sono progettate per diverse funzionalità del dispositivo.

Per associare una cartella libreria client a un gruppo di dispositivi, aggiungete una proprietà al nodo `cq:ClientLibraryFolder` con i seguenti attributi:

* **Nome:** canali
* **Tipo:** Stringa`[]`
* **Valori:** il nome del gruppo mobile. Per escludere la cartella libreria da un gruppo, aggiungete il prefisso al nome con un punto esclamativo (&quot;!&quot;).

Nella tabella seguente, ad esempio, è riportato il valore della proprietà `channels` per ogni cartella della libreria client della categoria `cq.widgets`:

| Cartella libreria client | Valore della proprietà channel |
|---|---|
| `/libs/cq/analytics/widgets` | `!touch` |
| `/libs/cq/analytics/widgets/themes/default` | `!touch` |
| `/libs/cq/cloudserviceconfigs/widgets` | `!touch` |
| `/libs/cq/searchpromote/widgets` | `!touch` |
| `/libs/cq/searchpromote/widgets/themes/default` | `[`*nessun valore*`]` |
| `/libs/cq/touch/widgets` | `touch` |
| `/libs/cq/touch/widgets/themes/default` | `touch` |
| `/libs/cq/ui/widgets` | `!touch` |
| `/libs/cq/ui/widgets/themes/default` | `!touch` |

## Utilizzo dei preprocessori {#using-preprocessors}

AEM è possibile collegare preprocessori e navi con supporto per [YUI Compressor](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) per CSS e JavaScript e [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler/) per JavaScript con YUI impostato AEM preprocessore predefinito.

I preprocessori collegabili consentono un utilizzo flessibile, tra cui:

* Definizione di ScriptProcessors in grado di elaborare origini di script
* I processori sono configurabili con opzioni
* I processori possono essere utilizzati per la minificazione, ma anche per i casi non minati
* clientlib può definire quale processore utilizzare

>[!NOTE]
>
>Per impostazione predefinita, AEM utilizza il compressore YUI. Per un elenco dei problemi noti, consultate la [documentazione GitHub del compressore YUI](https://github.com/yui/yuicompressor/issues). Il passaggio al compressore GCC per determinati clientlibs può risolvere alcuni problemi rilevati durante l’utilizzo di YUI.

>[!CAUTION]
>
>Non inserite una libreria ridotta in una libreria client. Fornite invece la libreria non elaborata e, se è necessaria la minificazione, utilizzate le opzioni dei preprocessori.

### Utilizzo {#usage}

Potete scegliere di configurare la configurazione dei preprocessori per clientlibrary o per tutta la struttura del sistema.

* Aggiungere le proprietà multivalore `cssProcessor` e `jsProcessor` nel nodo clientlibrary

* Oppure definire la configurazione predefinita del sistema tramite la configurazione **HTML Library Manager** OSGi

Una configurazione preprocessore sul nodo clientlib ha la precedenza rispetto alla configurazione OSGI.

### Formato ed esempi {#format-and-examples}

#### Formato {#format}

```xml
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

#### Compressore YUI per la riduzione CSS e GCC per JS {#yui-compressor-for-css-minification-and-gcc-for-js}

```xml
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

#### Typescript to Preprocess (Prepara da preelaborare) e poi GCC to Minify and Obfuscate {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate}

```xml
jsProcessor: [
   "default:typescript",
   "min:typescript", 
   "min:gcc;obfuscate=true"
]
```

#### Opzioni GCC aggiuntive {#additional-gcc-options}

```xml
failOnWarning (defaults to "false")
languageIn (defaults to "ECMASCRIPT5")
languageOut (defaults to "ECMASCRIPT5")
compilationLevel (defaults to "simple") (can be "whitespace", "simple", "advanced")
```

Per ulteriori dettagli sulle opzioni GCC, consultare la [documentazione GCC](https://developers.google.com/closure/compiler/docs/compilation_levels).

### Imposta minificatore predefinito di sistema {#set-system-default-minifier}

YUI è impostato come minificatore predefinito in AEM. Per modificare questa impostazione in GCC, attenetevi alla procedura seguente.

1. Andate al gestore di configurazione Apache Felix all&#39;indirizzo [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
1. Trovare e modificare il **Adobe Granite HTML Library Manager**.
1. Abilitare l&#39;opzione **Minify** (se non è già abilitata).
1. Impostare il valore **Configurazione predefinita processore JS** su `min:gcc`.

   Le opzioni possono essere passate se separate da un punto e virgola, ad esempio `min:gcc;obfuscate=true`.

1. Fare clic su **Salva** per salvare le modifiche.

## Strumenti di debug {#debugging-tools}

AEM fornisce diversi strumenti per il debug e il test delle cartelle della libreria client.

### Vedere File incorporati {#see-embedded-files}

Per tracciare l&#39;origine del codice incorporato o per assicurarsi che le librerie client incorporate producano i risultati previsti, è possibile visualizzare i nomi dei file che vengono incorporati in fase di esecuzione. Per visualizzare i nomi dei file, aggiungete il parametro `debugClientLibs=true` all&#39;URL della pagina Web. La libreria generata contiene istruzioni `@import` invece del codice incorporato.

Nell&#39;esempio della sezione precedente [Incorporamento del codice da altre librerie](/help/sites-developing/clientlibs.md#embedding-code-from-other-libraries), la cartella della libreria client `/etc/client/libraries/myclientlibs/publicmain` incorpora la cartella della libreria client `/apps/myapp/clientlib`. L&#39;aggiunta del parametro alla pagina Web genera il seguente collegamento nel codice sorgente della pagina Web:

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

Aprendo il file `publicmain.css` viene visualizzato il seguente codice:

```xml
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. Nella casella dell’indirizzo del browser Web, aggiungete il testo seguente all’URL del codice HTML:

   `?debugClientLibs=true`
1. Quando la pagina viene caricata, visualizzate l’origine della pagina.
1. Fare clic sul collegamento fornito come href per l&#39;elemento di collegamento per aprire il file e visualizzare il codice sorgente.

### Scopri librerie client {#discover-client-libraries}

Il componente `/libs/cq/granite/components/dumplibs/dumplibs` genera una pagina di informazioni su tutte le cartelle della libreria client nel sistema. Il nodo `/libs/granite/ui/content/dumplibs` ha il componente come tipo di risorsa. Per aprire la pagina, usate il seguente URL (modificando l’host e la porta come richiesto):

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

Le informazioni includono il percorso e il tipo della libreria (CSS o JS) e i valori degli attributi della libreria, come categorie e dipendenze. Le tabelle successive della pagina mostrano le librerie in ogni categoria e canale.

### Vedere Uscita generata {#see-generated-output}

Il componente `dumplibs` include un selettore di test che visualizza il codice sorgente generato per i tag `ui:includeClientLib`. La pagina include il codice per diverse combinazioni di attributi js, css e a tema.

1. Per aprire la pagina Test Output, utilizzare uno dei metodi seguenti:

   * Dalla pagina `dumplibs.html`, fare clic sul collegamento nel testo **Fare clic qui per il test dell&#39;output**.
   * Aprite il seguente URL nel browser Web (utilizzate un host e una porta diversi come richiesto):

      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`

   La pagina predefinita mostra l&#39;output per i tag senza valore per l&#39;attributo category.

1. Per visualizzare l&#39;output di una categoria, digitare il valore della proprietà `categories` della libreria client e fare clic su **Invia query**.

## Configurazione della gestione della libreria per lo sviluppo e la produzione {#configuring-library-handling-for-development-and-production}

Il servizio HTML Library Manager elabora i tag `cq:ClientLibraryFolder` e genera le librerie in fase di esecuzione. Il tipo di ambiente, sviluppo o produzione determina la modalità di configurazione del servizio:

* Maggiore protezione: Disabilita debugging
* Prestazioni migliorate: Rimuovete gli spazi bianchi e comprimete le librerie.
* Maggiore leggibilità: Includete gli spazi bianchi e non comprimete.

Per informazioni sulla configurazione del servizio, vedere [AEM HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md).
