---
title: Contesto client in dettaglio
seo-title: Client Context in Detail
description: ClientContext rappresenta una raccolta di dati utente assemblata in modo dinamico
seo-description: The Client Context represents a dynamically assembled collection of user data
uuid: 31cfcfd0-14f3-4777-ae85-45eb352756d0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 7b97fc27-30de-4ef9-9efe-673aec50cff2
feature: Context Hub
exl-id: fb613a57-d064-45eb-be15-c4f7e06bb0ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3013'
ht-degree: 1%

---

# Contesto client in dettaglio{#client-context-in-detail}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Il contesto client è stato sostituito da ContextHub nell’interfaccia utente touch. Vedi la [documentazione correlata](/help/sites-developing/contexthub.md) per i dettagli.

ClientContext rappresenta una raccolta di dati utente assemblata in modo dinamico. Puoi utilizzare i dati per determinare il contenuto da visualizzare su una pagina web in una determinata situazione (targeting del contenuto). I dati sono disponibili anche per l’analisi dei siti web e per qualsiasi javascript nella pagina.

Il contesto client è costituito principalmente dai seguenti aspetti:

* Archivio sessione contenente i dati utente.
* L’interfaccia utente che visualizza i dati utente e fornisce gli strumenti per simulare l’esperienza utente.
* A [API javascript](/help/sites-developing/ccjsapi.md) per interagire con gli archivi di sessione.

Per creare un archivio di sessioni autonomo e aggiungerlo al contesto client o creare un archivio di sessioni associato a un componente dell’archivio contesti. AEM installa diversi componenti dell’archivio contesti che puoi utilizzare immediatamente. Puoi utilizzare questi componenti come base per i componenti.

Per informazioni sull’apertura del contesto client, sulla configurazione delle informazioni visualizzate e sulla simulazione dell’esperienza utente, consulta [Contesto client](/help/sites-administering/client-context.md).

## Session Stores {#session-stores}

ClientContext include vari archivi di sessione contenenti dati utente. I dati archiviati provengono dalle seguenti origini:

* Il browser Web client.
* Il server (vedi [Store JSONP](/help/sites-administering/client-context.md) per la memorizzazione di informazioni da fonti di terze parti)

Il framework ClientContext fornisce un [API javascript](/help/sites-developing/ccjsapi.md) che è possibile utilizzare per interagire con gli archivi di sessione per leggere e scrivere i dati degli utenti, nonché per ascoltare e reagire agli eventi archiviati. Puoi anche creare archivi di sessioni per i dati utente utilizzati per il targeting dei contenuti o per altri scopi.

I dati dell’archivio sessioni rimangono sul client. Il contesto client non riscrive i dati sul server. Per inviare dati al server, utilizzare un modulo o sviluppare JavaScript personalizzato.

Ogni archivio di sessione è un insieme di coppie proprietà-valore. L&#39;archivio delle sessioni rappresenta una raccolta di dati (di qualsiasi tipo) il cui significato concettuale può essere deciso dal progettista e/o sviluppatore. Il seguente codice javascript di esempio definisce un oggetto che rappresenta i dati di profilo che potrebbero contenere gli archivi di sessione:

```
{
  age: 20,
  authorizableId: "aparker@geometrixx.info",
  birthday: "27 Feb 1992",
  email: "aparker@geometrixx.info",
  formattedName: "Alison Parker",
  gender: "female",
  path: "/home/users/geometrixx/aparker@geometrixx.info/profile"
}
```

Un archivio delle sessioni può essere mantenuto in tutte le sessioni del browser, oppure può durare solo per la sessione del browser in cui viene creato.

>[!NOTE]
>
>La persistenza dell’archivio utilizza l’archiviazione del browser o i cookie (il `SessionPersistence` cookie). La memorizzazione del browser è più comune.
>
>Quando il browser viene chiuso e riaperto, è possibile caricare un archivio di sessione con i valori di un archivio persistente. La cancellazione della cache del browser è quindi necessaria per rimuovere i vecchi valori.

### Componenti per l’archiviazione del contesto {#context-store-components}

Un componente dell’archivio contesti è un componente AEM che può essere aggiunto al contesto client. In genere, i componenti dell’archivio di contesto visualizzano i dati provenienti da un archivio di sessioni a cui sono associati. Tuttavia, le informazioni visualizzate dai componenti dell’archivio di contesto non sono limitate ai dati dell’archivio di sessione.

I componenti dell’archivio contesti possono includere i seguenti elementi:

* Script JSP che definiscono l’aspetto nel contesto client.
* Proprietà per elencare il componente nella barra laterale.
* Modificare le finestre di dialogo per configurare le istanze dei componenti.
* JavaScript che inizializza l&#39;archivio sessioni.

Per una descrizione dei componenti del Context Store installati che è possibile aggiungere al Context Store, vedi [Componenti Client Context disponibili](/help/sites-administering/client-context.md#available-client-context-components).

>[!NOTE]
>
>I dati di pagina non sono più nel contesto client come componente predefinito. Se necessario, puoi aggiungere questa opzione modificando il contesto client, aggiungendo il **Proprietà store generico** , quindi configuralo per definire il **Store** come `pagedata`.

### Consegna di contenuti mirati {#targeted-content-delivery}

Le informazioni sul profilo vengono utilizzate anche per la consegna [contenuto di destinazione](/help/sites-authoring/content-targeting-touch.md).

![clientcontext_targetedcontentdelivery](assets/clientcontext_targetedcontentdelivery.png) ![clientcontext_targetedcontentdeliverydetail](assets/clientcontext_targetedcontentdeliverydetail.png)

## Aggiunta Di Contesto Client A Una Pagina {#adding-client-context-to-a-page}

Includi il componente ClientContext nella sezione body delle pagine web per abilitare ClientContext. Il percorso del nodo del componente contesto client è `/libs/cq/personalization/components/clientcontext`. Per includere il componente, aggiungi il seguente codice al file JSP del componente di pagina, che si trova appena sotto il `body` elemento della pagina:

```java
<cq:include path="clientcontext" resourceType="cq/personalization/components/clientcontext"/>
```

Il componente clientcontext fa sì che la pagina carichi le librerie client che implementano Client Context.

* API javascript Client Context.
* Il framework Client Context che supporta gli archivi di sessione, la gestione degli eventi, ecc.
* Segmenti definiti.
* Gli script init.js generati per ciascun componente dell’archivio di contesto aggiunto al contesto client.
* (Solo per l’istanza di authoring) L’interfaccia utente del contesto client.

L’interfaccia utente ClientContext è disponibile solo sull’istanza di authoring.

## Estensione del contesto client {#extending-client-context}

Per estendere Client Context, crea un archivio di sessione e, facoltativamente, visualizza i dati dell&#39;archivio:

* Crea un archivio di sessione per i dati utente necessari per il targeting dei contenuti e l’analisi web.
* Crea un componente per l’archivio di contesto per consentire agli amministratori di configurare l’archivio di sessioni associato e di visualizzare i dati dell’archivio di dati nel contesto client a scopo di test.

>[!NOTE]
>
>Se hai (o crei) un `JSONP` servizio che può fornire i dati, è sufficiente utilizzare il `JSONP` componente archivio di contesto e mapparlo al servizio JSONP. In questo modo verrà gestito l&#39;archivio delle sessioni.

### Creazione di un archivio sessioni {#creating-a-session-store}

Crea un archivio di sessione per i dati da aggiungere e recuperare dal contesto client. In genere, si utilizza la procedura seguente per creare un archivio sessioni:

1. Crea una cartella della libreria client con un `categories` valore di proprietà di `personalization.stores.kernel`. Client Context carica automaticamente le librerie client di questa categoria.

1. Configura la cartella della libreria client in modo che abbia una dipendenza da `personalization.core.kernel` cartella della libreria client. La `personalization.core.kernel` la libreria client fornisce l&#39;API javascript Client Context.

1. Aggiungi il javascript che crea e inizializza l&#39;archivio sessioni.

L&#39;inclusione del javascript nella libreria client personalization.stores.kernel causa la creazione dell&#39;archivio quando viene caricato il framework del contesto client.

>[!NOTE]
>
>Se crei un archivio sessioni come parte di un componente per l’archivio contesti, puoi in alternativa inserire il codice javascript nel file init.js.jsp del componente. In questo caso, l’archivio sessioni viene creato solo se il componente viene aggiunto al contesto client.

#### Tipi di archivi di sessioni {#types-of-session-stores}

Gli archivi di sessione vengono creati e disponibili durante una sessione del browser oppure vengono mantenuti nell&#39;archiviazione del browser o nei cookie. L&#39;API JavaScript del contesto client definisce diverse classi che rappresentano entrambi i tipi di archivio dati:

* [`CQ_Analytics.SessionStore`](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore): Questi oggetti risiedono solo nel DOM della pagina. I dati vengono creati e mantenuti per tutta la durata della pagina.
* [`CQ_Analytics.PerstistedSessionStore`](/help/sites-developing/ccjsapi.md#cq-analytics-persistedsessionstore): Questi oggetti risiedono nel DOM della pagina e sono persistenti sia nell’archiviazione del browser che nei cookie. I dati sono disponibili su più pagine e tra sessioni utente.

L’API fornisce anche le estensioni di queste classi specializzate per la memorizzazione di dati JSON o JSONP:

* Oggetti solo sessione: [`CQ_Analytics.JSONStore`](/help/sites-developing/ccjsapi.md#cq-analytics-jsonstore) e [`CQ-Analytics.JSONPStore`](/help/sites-developing/ccjsapi.md#cq-analytics-jsonpstore).

* Oggetti persistenti: [`CQ_Analytics.PersistedJSONStore`](/help/sites-developing/ccjsapi.md#cq-analytics-persistedjsonstore) e [`CQ-Analytics.PersistedJSONPStore`](/help/sites-developing/ccjsapi.md#cq-analyics-persistedjsonpstore).

#### Creazione dell&#39;oggetto Session Store {#creating-the-session-store-object}

Il javascript della cartella della libreria client crea e inizializza l&#39;archivio sessioni. L&#39;archivio delle sessioni deve quindi essere registrato utilizzando Context Store Manager. Nell&#39;esempio seguente viene creato e registrato un [CQ_Analytics.SessionStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore) oggetto.

```
//Create the session store
if (!CQ_Analytics.MyStore) {
    CQ_Analytics.MyStore = new CQ_Analytics.SessionStore();
    CQ_Analytics.MyStore.STOREKEY = "MYSTORE";
    CQ_Analytics.MyStore.STORENAME = "mystore";
    CQ_Analytics.MyStore.data={};
}
//register the session store
if (CQ_Analytics.ClientContextMgr){
    CQ_Analytics.ClientContextMgr.register(CQ_Analytics.MyStore)
}
```

Per memorizzare i dati JSON, l’esempio seguente crea e registra un [CQ_Analytics.JSONStore](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore) oggetto.

```
if (!CQ_Analytics.myJSONStore) {
    CQ_Analytics.myJSONStore = CQ_Analytics.JSONStore.registerNewInstance("myjsonstore",{});
}
```

### Creazione di un componente Context Store {#creating-a-context-store-component}

Crea un componente per l’archivio di contesto per eseguire il rendering dei dati dell’archivio di sessione nel contesto client. Una volta creato, puoi trascinare il componente dell’archivio contesti sul contesto client per eseguire il rendering dei dati da un archivio sessioni. I componenti dell’archivio contesti sono costituiti dai seguenti elementi:

* Script JSP per il rendering dei dati.
* Finestra di dialogo di modifica.
* Uno script JSP per l&#39;inizializzazione dell&#39;archivio sessioni.
* (Facoltativo) Cartella libreria client che crea l&#39;archivio sessioni. Non è necessario includere la cartella della libreria client se il componente utilizza un archivio di sessione esistente.

#### Estensione dei componenti del Context Store forniti {#extending-the-provided-context-store-components}

AEM fornisce i componenti dell&#39;archivio dati generici e quelli dell&#39;archivio dati contestuali genericstoreproperties che è possibile estendere. La struttura dei dati dell’archivio determina il componente che si estende:

* Coppie proprietà-valore: Estendi la `GenericStoreProperties` componente. Questo componente esegue automaticamente il rendering degli archivi di coppie proprietà-valore. Sono forniti diversi punti di interazione:

   * `prolog.jsp` e `epilog.jsp`: interazione del componente che consente di aggiungere logica lato server prima o dopo il rendering del componente.

* Dati complessi: Estendi la `GenericStore` componente. L’archivio sessioni dovrà quindi utilizzare un metodo &quot;renderer&quot; che verrà chiamato ogni volta che il componente deve essere rappresentato. La funzione di rendering viene chiamata con due parametri:

   * `@param {String} store`

      Archivio di cui eseguire il rendering

   * `@param {String} divId`

      Id del div in cui deve essere eseguito il rendering dello store.

>[!NOTE]
>
>Tutti i componenti Client Context sono estensioni dei componenti Generic Store o Generic Store Properties. Sono installati diversi esempi in `/libs/cq/personalization/components/contextstores` cartella.

#### Configurazione dell’aspetto nella barra laterale {#configuring-the-appearance-in-sidekick}

Durante la modifica del contesto client, i componenti dell’archivio del contesto vengono visualizzati nella barra laterale. Come per tutti i componenti, il `componentGroup` e `jcr:title` le proprietà del componente ClientContext determinano il gruppo e il nome del componente.

Tutti i componenti che hanno un `componentGroup` valore di proprietà di `Client Context` per impostazione predefinita, sono disponibili nella barra laterale. Se utilizzi un valore diverso per la variabile `componentGroup` , è necessario aggiungere manualmente il componente alla barra laterale utilizzando la modalità Progettazione .

#### Istanze dei componenti dell&#39;archivio contesti {#context-store-component-instances}

Quando aggiungi un componente dell’archivio di contesto al contesto client, di seguito viene creato un nodo che rappresenta l’istanza del componente `/etc/clientcontext/default/content/jcr:content/stores`. Questo nodo contiene i valori delle proprietà configurati utilizzando la finestra di dialogo di modifica del componente.

Quando Client Context viene inizializzato, questi nodi vengono elaborati.

#### Inizializzazione dell&#39;archivio sessioni associato {#initializing-the-associated-session-store}

Aggiungi un file init.js.jsp al tuo componente per generare codice javascript che inizializza l’archivio sessioni utilizzato dal componente dell’archivio contesti. Ad esempio, utilizza lo script di inizializzazione per recuperare le proprietà di configurazione per il componente e utilizzale per popolare l’archivio sessioni.

Il javascript generato viene aggiunto alla pagina quando Client Context viene inizializzato al caricamento della pagina sia sulle istanze di authoring che di pubblicazione. Questo JSP viene eseguito prima che l’istanza del componente dell’archivio di contesto venga caricata e sottoposta a rendering.

Il codice deve impostare il tipo mime del file su `text/javascript`o non viene eseguito.

>[!CAUTION]
>
>Lo script init.js.jsp viene eseguito sull’istanza di authoring e pubblicazione, ma solo se il componente dell’archivio contesti viene aggiunto al contesto client.

La procedura seguente crea il file di script init.js.jsp e aggiunge il codice che imposta il tipo di mime corretto. Segue il codice che esegue l&#39;inizializzazione dell&#39;archivio.

1. Fai clic con il pulsante destro del mouse sul nodo del componente archivio contesti e fai clic su Crea > Crea file .
1. Nel campo Nome digitare `init.js.jsp` quindi fare clic su OK.
1. Nella parte superiore della pagina, aggiungi il seguente codice e fai clic su Salva tutto.

   ```java
   <%@page contentType="text/javascript" %>
   ```

### Rendering dei dati dell’archivio sessioni per i componenti genericstoreproperties {#rendering-session-store-data-for-genericstoreproperties-components}

Visualizza i dati dell&#39;archivio sessioni in ClientContext utilizzando un formato coerente.

#### Visualizzazione dei dati delle proprietà {#displaying-property-data}

La libreria di personalizzazione fornisce `personalization:storePropertyTag` che visualizza il valore di una proprietà da un archivio sessioni. Per utilizzare il tag , includi la seguente riga di codice nel file JSP:

```xml
<%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
```

Il tag ha il seguente formato:

```xml
<personalization:storePropertyTag propertyName="property_name" store="session_store_name"/>
```

La `propertyName` attribute è il nome della proprietà store da visualizzare. La `store` attributo è il nome dell&#39;archivio registrato. Il seguente tag di esempio visualizza il valore del `authorizableId` proprietà `profile` negozio:

```xml
<personalization:storePropertyTag propertyName="authorizableId" store="profile"/>
```

#### Struttura HTML {#html-structure}

La cartella della libreria client personalization.ui (/etc/clientlibs/foundation/personalization/ui/theme/default) fornisce gli stili CSS utilizzati da Client Context per formattare il codice HTML. Il codice seguente illustra la struttura consigliata da utilizzare per la visualizzazione dei dati dell&#39;archivio:

```xml
<div class="cq-cc-store">
   <div class="cq-cc-thumbnail">
      <div class="cq-cc-store-property">
           <!-- personalization:storePropertyTag for the store thumbnail image goes here -->
      </div>
   </div>
   <div class="cq-cc-content">
       <div class="cq-cc-store-property cq-cc-store-property-level0">
           <!-- personalization:storePropertyTag for a store property goes here --> 
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level1">
           <!-- personalization:storePropertyTag for a store property goes here --> 
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level2">
           <!-- personalization:storePropertyTag for a store property goes here --> 
       </div>
       <div class="cq-cc-store-property cq-cc-store-property-level3">
           <!-- personalization:storePropertyTag for a store property goes here --> 
       </div>
   </div>
   <div class="cq-cc-clear"></div>
</div>
```

La `/libs/cq/personalization/components/contextstores/profiledata` il componente archivio contesto utilizza questa struttura per visualizzare i dati dall’archivio delle sessioni del profilo. La `cq-cc-thumbnail` La classe inserisce l&#39;immagine miniatura. La `cq-cc-store-property-level*x*` le classi formattano i dati alfanumerici:

* livello0, livello1 e livello2 sono distribuiti verticalmente e utilizzano un font bianco.
* livello3 ed eventuali livelli aggiuntivi vengono distribuiti orizzontalmente e utilizzano un carattere bianco con uno sfondo più scuro.

![chlimage_1-222](assets/chlimage_1-222.png)

### Rendering dei dati dell’archivio delle sessioni per i componenti generici {#rendering-session-store-data-for-genericstore-components}

Per eseguire il rendering dei dati dell’archivio utilizzando un componente genericstore, è necessario:

* Aggiungi il tag personalization:storeRendererTag allo script JSP del componente per identificare il nome dell&#39;archivio sessioni.
* Implementa un metodo renderer sulla classe dell&#39;archivio sessioni.

#### Identificazione dello store di sessioni genericstore {#identifying-the-genericstore-session-store}

La libreria di personalizzazione fornisce `personalization:storePropertyTag` che visualizza il valore di una proprietà da un archivio sessioni. Per utilizzare il tag , includi la seguente riga di codice nel file JSP:

```xml
<%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
```

Il tag ha il seguente formato:

```java
<personalization:storeRendererTag store="store_name"/>
```

#### Implementazione del metodo di rendering dell’archivio sessioni {#implementing-the-session-store-renderer-method}

L’archivio sessioni dovrà quindi utilizzare un metodo &quot;renderer&quot; che verrà chiamato ogni volta che il componente deve essere rappresentato. La funzione di rendering viene chiamata con due parametri:

* `@param {String} store`

   Archivio di cui eseguire il rendering

* `@param {String} divId`

   Id del div in cui deve essere eseguito il rendering dello store.

## Interazione con gli archivi di sessioni {#interacting-with-session-stores}

Utilizza javascript per interagire con gli archivi di sessione.

### Accesso agli archivi delle sessioni {#accessing-session-stores}

Ottenere un oggetto archivio sessioni per leggere o scrivere dati nell&#39;archivio. [`CQ_Analytics.ClientContextMgr`](/help/sites-developing/ccjsapi.md#cq-analytics-clientcontextmgr) fornisce l&#39;accesso agli archivi in base al nome dello store. Una volta ottenuto, utilizza i metodi [`CQ-Analytics.SessionStore`](/help/sites-developing/ccjsapi.md#cq-analytics-sessionstore) o [`CQ-Analytics.PersistedSessionStore`](/help/sites-developing/ccjsapi.md#cq-analytics-persistedsessionstore) per interagire con i dati archiviati.

L&#39;esempio seguente ottiene il `profile` e quindi recupera il `formattedName` dall&#39;archivio.

```
function getName(){
   var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
   if(profilestore){
      return profilestore.getProperty("formattedName", false);
   } else {
      return null;
   }
} 
```

### Creazione di un listener per reagire a un aggiornamento dell&#39;archivio sessioni {#creating-a-listener-to-react-to-a-session-store-update}

La sessione memorizza gli eventi di attivazione, quindi è possibile aggiungere listener e attivare gli eventi in base a questi eventi.

Gli archivi di sessione sono costruiti in `Observable` modello. Si estendono [`CQ_Analytics.Observable`](/help/sites-developing/ccjsapi.md#cq-analytics-observable) che fornisce [`addListener`](/help/sites-developing/ccjsapi.md#addlistener-event-fct-scope) metodo .

Nell&#39;esempio seguente viene aggiunto un listener al `update` evento `profile` archivio sessioni.

```
var profileStore = ClientContextMgr.getRegisteredStore("profile");
if( profileStore ) {
  //callback execution context
  var executionContext = this;

  //add "update" event listener to store
  profileStore.addListener("update",function(store, property) {
    //do something on store update

  },executionContext);
}
```

### Controllo della definizione e dell&#39;inizializzazione di un archivio sessioni {#checking-that-a-session-store-is-defined-and-initialized}

Gli archivi di sessione non sono disponibili finché non vengono caricati e inizializzati con i dati. I seguenti fattori possono influenzare il tempo di disponibilità dell&#39;archivio sessioni:

* Caricamento pagina
* Caricamento JavaScript
* Tempo di esecuzione JavaScript
* Tempi di risposta per le richieste XHR
* Modifiche dinamiche all&#39;archivio sessioni

Utilizza la [`CQ_Analytics.ClientContextUtils`](/help/sites-developing/ccjsapi.md#cq-analytics-clientcontextutils) dell&#39;oggetto [`onStoreRegistered`](/help/sites-developing/ccjsapi.md#onstoreregistered-storename-callback) e [`onStoreInitialized`](/help/sites-developing/ccjsapi.md#onstoreinitialized-storename-callback-delay) metodi per accedere agli archivi delle sessioni solo quando sono disponibili. Questi metodi consentono di registrare listener di eventi che reagiscono agli eventi di registrazione e inizializzazione della sessione.

>[!CAUTION]
>
>Se si dipende da un altro negozio, è necessario provvedere per il caso di quando il negozio non è mai registrato.

Nell&#39;esempio seguente viene utilizzato il `onStoreRegistered` evento `profile` archivio sessioni. Quando l&#39;archivio è registrato, viene aggiunto un listener al `update` evento dell&#39;archivio sessioni. Quando lo store viene aggiornato, il contenuto della `<div class="welcome">` viene aggiornato con il nome del `profile` archiviare.

```
//listen for the store registration
CQ_Analytics.ClientContextUtils.onStoreRegistered("profile", listen);

//listen for the store's update event
function listen(){
 var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
    profilestore.addListener("update",insertName);
}

//insert the welcome message
function insertName(){
 $("div.welcome").text("Welcome "+getName());
}

//obtain the name from the profile store
function getName(){
 var profilestore = CQ_Analytics.ClientContextMgr.getRegisteredStore("profile");
 if(profilestore){
  return profilestore.getProperty("formattedName", false);
    } else {
        return null;
    }
}
```

### Esclusione di una proprietà dal cookie di persistenza sessione {#excluding-a-property-from-the-sessionpersistence-cookie}

Per impedire la proprietà di una `PersistedSessionStore` dal persistere (ovvero escluderlo dal `sessionpersistence` cookie), aggiungi la proprietà all&#39;elenco delle proprietà non persistenti dell&#39;archivio sessioni persistente.

Consulta [`CQ_Analytics.PersistedSessionStore.setNonPersisted(propertyName)`](/help/sites-developing/ccjsapi.md#setnonpersisted-name)

```
CQ_Analytics.ClientContextUtils.onStoreRegistered("surferinfo", function(store) {
  //this will exclude the browser, OS and resolution properties of the surferinfo session store from the 
  store.setNonPersisted("browser");
  store.setNonPersisted("OS");
  store.setNonPersisted("resolution");
});
```

## Configurazione del dispositivo di scorrimento {#configuring-the-device-slider}

### Condizioni {#conditions}

La pagina corrente deve avere una pagina mobile corrispondente; questo è determinato solo se la pagina dispone di una Live Copy configurata con una configurazione di rollout mobile ( `rolloutconfig.path.toLowerCase` contiene `mobile`).

#### Configurazione {#configuration}

Quando si passa dalla pagina desktop al suo equivalente mobile:

* Il DOM della pagina mobile viene caricato.
* Il principale `div` (obbligatorio) che contiene il contenuto, viene estratto e inserito nella pagina desktop corrente.

* Le classi CSS e corpo da caricare devono essere configurate manualmente.

Ad esempio:

```
window.CQMobileSlider["geometrixx-outdoors"] = {
  //CSS used by desktop that need to be removed when mobile
  DESKTOP_CSS: [
    "/etc/designs/${app}/clientlibs_desktop_v1.css"
  ],
  
  //CSS used by mobile that need to be removed when desktop
  MOBILE_CSS: [
    "/etc/designs/${app}/clientlibs_mobile_v1.css"
  ],
  
  //id of the content that needs to be removed when mobile
  DESKTOP_MAIN_ID: "main",
  
  //id of the content that needs to be removed when desktop
  MOBILE_MAIN_ID: "main",
  
  //body classes used by desktop that need to be removed when mobile
  DESKTOP_BODY_CLASS: [
    "page"
  ],
  
  //body classes used by mobile that need to be removed when desktop
  MOBILE_BODY_CLASS: [
    "page-mobile"
  ]
};
```

## Esempio: Creazione di un componente Archivio contesti personalizzato {#example-creating-a-custom-context-store-component}

In questo esempio, si crea un componente dell’archivio di contesto che recupera i dati da un servizio esterno e li memorizza nell’archivio delle sessioni:

* Estende il componente genericstoreproperties .
* Inizializza un archivio utilizzando un `CQ_Analytics.JSONPStore` oggetto javascript.
* Chiama un servizio JSONP per recuperare i dati e aggiungerli all&#39;archivio.
* Esegue il rendering dei dati nel contesto client.

### Aggiungi il componente geoloc {#add-the-geoloc-component}

Crea un&#39;applicazione CQ e aggiungi il componente geoloc.

1. Apri CRXDE Lite nel browser Web ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Fai clic con il pulsante destro del mouse sul pulsante `/apps` e fai clic su Crea > Crea cartella. Specifica un nome di `myapp` quindi fare clic su OK.
1. Analogamente, sotto `myapp`, crea una cartella denominata `contextstores`. &quot;
1. Fai clic con il pulsante destro del mouse sul pulsante `/apps/myapp/contextstores` e fai clic su Crea > Crea componente. Specifica i seguenti valori di proprietà e fai clic su Avanti:

   * Etichetta: **geoloc**
   * Titolo: **Store posizione**
   * Super Type: **`cq/personalization/components/contextstores/genericstoreproperties`**
   * Gruppo: **Contesto client**

1. Nella finestra di dialogo Crea componente fare clic su Avanti su ciascuna pagina fino a quando il pulsante OK non è abilitato, quindi fare clic su OK.
1. Fai clic su Salva tutto.

### Creare la finestra di dialogo Modifica geoloc {#create-the-geoloc-edit-dialog}

Il componente per l’archiviazione del contesto richiede una finestra di dialogo di modifica. La finestra di dialogo di modifica del geoloc conterrà un messaggio statico che indica che non sono presenti proprietà da configurare.

1. Fai clic con il pulsante destro del mouse sul pulsante `/libs/cq/personalization/components/contextstores/genericstoreproperties/dialog` e fare clic su Copia.
1. Fai clic con il pulsante destro del mouse sul pulsante `/apps/myapp/contextstores/geoloc` e fare clic su incolla.
1. Elimina tutti i nodi figlio sotto il nodo /apps/myapp/contextstores/geoloc/dialog/items/items/tab1/items :

   * archiviare
   * proprietà
   * miniatura

1. Fai clic con il pulsante destro del mouse sul pulsante `/apps/myapp/contextstores/geoloc/dialog/items/items/tab1/items` e fai clic su Crea > Crea nodo. Specificare i seguenti valori di proprietà e fare clic su OK:

   * Nome: **statico**
   * Tipo: **cq:Widget**

1. Aggiungi le seguenti proprietà al nodo :

   | Nome | Tipo | Valore |
   |---|---|---|
   | cls | Stringa | x-form-field-description |
   | text | Stringa | Il componente geoloc non richiede alcuna configurazione. |
   | xtype | Stringa | statico |

1. Fai clic su Salva tutto.

   ![chlimage_1-223](assets/chlimage_1-223.png)

### Creare lo script di inizializzazione {#create-the-initialization-script}

Aggiungi un file init.js.jsp al componente geoloc e usalo per creare l&#39;archivio sessioni, recuperare i dati sulla posizione e aggiungerlo all&#39;archivio.

Il file init.js.jsp viene eseguito quando il contesto client viene caricato dalla pagina. A questo punto, l’API JavaScript Client Context viene caricata e disponibile per il tuo script.

1. Fai clic con il pulsante destro del mouse sul pulsante `/apps/myapp/contextstores/geoloc` nodo e fai clic su **Crea -> Crea file**. Specificare un Nome di init.js.jsp e fare clic su OK.
1. Aggiungi il codice seguente nella parte superiore della pagina, quindi fai clic su Salva tutto.

   ```java
   <%@page contentType="text/javascript;charset=utf-8" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   log.info("***** initializing geolocstore ****");
   String store = "locstore";
   String jsonpurl = "https://api.wipmania.com/jsonp?callback=${callback}";
   
   %>
   var locstore = CQ_Analytics.StoreRegistry.getStore("<%= store %>");
   if(!locstore){
    locstore = CQ_Analytics.JSONPStore.registerNewInstance("<%= store %>", "<%= jsonpurl %>",{});
   }
   <% log.info(" ***** done initializing geoloc ************"); %>
   ```

### Rendering dei dati dell’archivio sessioni geoloc {#render-the-geoloc-session-store-data}

Aggiungi il codice al file JSP del componente geoloc per eseguire il rendering dei dati dell’archivio nel contesto client.

![chlimage_1-224](assets/chlimage_1-224.png)

1. In CRXDE Lite, apri le `/apps/myapp/contextstores/geoloc/geoloc.jsp` file.
1. Aggiungi il seguente codice HTML sotto il codice stub:

   ```xml
   <%@taglib prefix="personalization" uri="https://www.day.com/taglibs/cq/personalization/1.0" %>
   <div class="cq-cc-store">
      <div class="cq-cc-content">
          <div class="cq-cc-store-property cq-cc-store-property-level0">
              Continent: <personalization:storePropertyTag propertyName="address/continent" store="locstore"/> 
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level1">
              Country: <personalization:storePropertyTag propertyName="address/country" store="locstore"/> 
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level2">
              City: <personalization:storePropertyTag propertyName="address/city" store="locstore"/> 
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level3">
              Latitude: <personalization:storePropertyTag propertyName="latitude" store="locstore"/> 
          </div>
          <div class="cq-cc-store-property cq-cc-store-property-level4">
              Longitude: <personalization:storePropertyTag propertyName="longitude" store="locstore"/> 
          </div>
      </div>
       <div class="cq-cc-clear"></div>
   </div>
   ```

1. Fai clic su Salva tutto.

### Aggiungere il componente al contesto client {#add-the-component-to-client-context}

Aggiungi il componente Location Store al contesto client in modo che venga inizializzato al caricamento della pagina.

1. Apri la home page dei Geometrixx Outdoors nell’istanza di authoring ([http://localhost:4502/content/geometrixx-outdoors/en.html](http://localhost:4502/content/geometrixx-outdoors/en.html)).
1. Fai clic su Ctrl+Alt+C (Windows) o Ctrl+Opzione+C (Mac) per aprire Client Context.
1. Fai clic sull’icona di modifica nella parte superiore del contesto client per aprire Client Context Designer.

   ![](do-not-localize/chlimage_1-11.png)

1. Trascina il componente Store posizione nel contesto client.

### Vedi Informazioni sulla posizione nel contesto client {#see-the-location-information-in-client-context}

Apri la home page dei Geometrixx Outdoors in modalità di modifica, quindi apri Client Context per visualizzare i dati dal componente Location Store.

1. Apri la pagina inglese del sito Geometrixx Outdoors. ([http://localhost:4502/content/geometrixx-outdoors/en.html](http://localhost:4502/content/geometrixx-outdoors/en.html))
1. Per aprire Client Context, premere Ctrl-Alt-C (windows) o Control-option-c (Mac).

## Creazione di un contesto client personalizzato {#creating-a-customized-client-context}

Per creare un secondo contesto client, devi duplicare il ramo:

`/etc/clientcontext/default`

* La sottocartella:

   `/content`

   conterrà il contenuto del contesto client personalizzato.

* La cartella:

   `/contextstores`

   consente di definire configurazioni diverse per gli archivi di contesto.

Per utilizzare il proprio contesto client personalizzato, modifica la proprietà\
`path`\
nello stile di progettazione del componente contesto client, come incluso nel modello di pagina. Ad esempio, come posizione standard di:\
`/libs/cq/personalization/components/clientcontext/design_dialog/items/path`
