---
title: Aggiunta di ContextHub alle pagine e accesso ai negozi
seo-title: Adding ContextHub to Pages and Accessing Stores
description: Aggiungi ContextHub alle tue pagine per abilitare le funzionalità di ContextHub e per effettuare il collegamento alle librerie Javascript di ContextHub
seo-description: Add ContextHub to your pages to enable the ContextHub features and to link to the ContextHub Javascript libraries
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
exl-id: 99efe308-bf8a-41ad-8203-b57fce20820c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# Aggiunta di ContextHub alle pagine e accesso ai negozi {#adding-contexthub-to-pages-and-accessing-stores}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Aggiungi ContextHub alle tue pagine per abilitare le funzionalità di ContextHub e per effettuare il collegamento alle librerie Javascript di ContextHub

L’API Javascript di ContextHub fornisce l’accesso ai dati contestuali gestiti da ContextHub. Questa pagina descrive brevemente le funzioni principali dell’API per l’accesso e la manipolazione dei dati contestuali. Segui i collegamenti alla documentazione di riferimento API per visualizzare informazioni dettagliate ed esempi di codice.

## Aggiunta di ContextHub a un componente pagina {#adding-contexthub-to-a-page-component}

Per abilitare le funzioni ContextHub e per effettuare il collegamento alle librerie Javascript di ContextHub, includi il componente contexthub nel `head` della pagina. Il codice JSP per il componente pagina è simile al seguente esempio:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

È inoltre necessario configurare se la barra degli strumenti di ContextHub viene visualizzata in modalità Anteprima. Vedi [Mostrare e nascondere l’interfaccia utente di ContextHub](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui).

## Informazioni sugli archivi ContextHub {#about-contexthub-stores}

Utilizza gli archivi ContextHub per mantenere i dati contestuali. ContextHub fornisce i seguenti tipi di archivi che costituiscono la base di tutti i tipi di store:

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

Tutti i tipi di archivio sono estensioni del [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) classe. Per informazioni sulla creazione di un nuovo tipo di archivio, consulta [Creazione di store personalizzati](/help/sites-developing/ch-extend.md#creating-custom-store-candidates). Per informazioni sui tipi di archivio di esempio, consulta [Candidati allo store ContextHub di esempio](/help/sites-developing/ch-samplestores.md).

### Modalità di persistenza {#persistence-modes}

Gli archivi di Context Hub utilizzano una delle seguenti modalità di persistenza:

* **Locale:** Utilizza HTML5 localStorage per mantenere i dati. L&#39;archiviazione locale viene mantenuta sul browser in più sessioni.
* **Sessione:** Utilizza HTML5 sessionStorage per mantenere i dati. L’archiviazione della sessione viene mantenuta per tutta la durata della sessione del browser ed è disponibile per tutte le finestre del browser.
* **Cookie:** Utilizza il supporto nativo dei cookie del browser per l&#39;archiviazione dei dati. I dati dei cookie vengono inviati a e dal server nelle richieste HTTP.
* **Window.name:** Utilizza la proprietà window.name per mantenere i dati.
* **Memoria:** Utilizza un oggetto Javascript per mantenere i dati.

Per impostazione predefinita, Context Hub utilizza la modalità di persistenza locale. Se il browser non supporta o consente HTML5 localStorage, viene utilizzata la persistenza della sessione. Se il browser non supporta o consente HTML5 sessionStorage, viene utilizzata la persistenza Window.name.

### Dati store {#store-data}

All’interno, archiviare i dati forma una struttura ad albero, consentendo l’aggiunta di valori come tipi principali o oggetti complessi. Quando si aggiungono oggetti complessi agli archivi, le proprietà dell&#39;oggetto vengono aggiunte ai rami della struttura dati. Ad esempio, il seguente oggetto complesso viene aggiunto a un archivio vuoto denominato location:

```xml
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

La struttura ad albero dei dati archiviati può essere concettualizzata come segue:

```xml
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

La struttura ad albero definisce gli elementi dati nell’archivio come coppie chiave/valore. Nell’esempio precedente, la chiave `/number` corrisponde al valore `321`e la chiave `/data/country` corrisponde al valore `Switzerland`.

### Manipolazione degli oggetti {#manipulating-objects}

ContextHub fornisce [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) Classe per la manipolazione di oggetti JavaScript. Utilizzare le funzioni di questa classe per manipolare gli oggetti Javascript prima di aggiungerli a uno store o dopo averli ottenuti da uno store.

Inoltre, la [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) Questa classe fornisce funzioni per la serializzazione degli oggetti alle punture e la deserializzazione delle stringhe agli oggetti. Usa questa classe per gestire i dati JSON per supportare i browser che non includono in modo nativo i `JSON.parse` e `JSON.stringify` funzioni.

## Interazione con gli archivi ContextHub {#interacting-with-contexthub-stores}

Utilizza la [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) Oggetto JavaScript per ottenere un archivio come oggetto Javascript. Una volta ottenuto l&#39;oggetto Store è possibile manipolare i dati contenuti. Utilizza la [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) o [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) per ottenere lo store.

### Accesso ai dati dell’archivio {#accessing-store-data}

La [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) La classe JavaScript definisce diverse funzioni per l&#39;interazione con i dati dell&#39;archivio. Le seguenti funzioni memorizzano e recuperano più elementi dati contenuti negli oggetti:

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

I singoli elementi dati sono memorizzati come un insieme di coppie chiave/valore. Per memorizzare e recuperare i valori si specifica la chiave corrispondente:

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

I candidati all’archivio personalizzati possono definire funzioni aggiuntive che consentono l’accesso ai dati archiviati.

>[!NOTE]
>
>ContextHub non è per impostazione predefinita a conoscenza dell&#39;accesso attualmente utilizzato sui server di pubblicazione e tali utenti sono considerati da ContextHub come &quot;Anonymous&quot;.
>
>Puoi rendere ContextHub consapevole degli utenti connessi caricando l’archivio dei profili come implementato in [Sito di riferimento We.Retail](/help/sites-developing/we-retail.md). Fai riferimento a [codice pertinente su GitHub qui](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### Evento ContextHub {#contexthub-eventing}

ContextHub include un framework di eventi che consente di reagire automaticamente agli eventi archiviati. Ogni oggetto store contiene un [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) oggetto disponibile come [`eventing`](/help/sites-developing/contexthub-api.md#eventing) proprietà. Utilizza la [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) o [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) per associare una funzione Javascript a un evento store.

## Utilizzo di Context Hub per manipolare i cookie {#using-context-hub-to-manipulate-cookies}

L’API Javascript di Context Hub fornisce supporto cross-browser per la gestione dei cookie del browser. La [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) Lo spazio dei nomi definisce diverse funzioni per la creazione, la manipolazione e l’eliminazione dei cookie.

## Determinazione dei segmenti ContextHub risolti {#determining-resolved-contexthub-segments}

Il motore di segmenti ContextHub ti consente di determinare quali dei segmenti registrati vengono risolti nel contesto corrente. Utilizzare la funzione getResolvedSegments del [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) per recuperare i segmenti risolti. Quindi, utilizza il `getName` o `getPath` funzione [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) da sottoporre a test per un segmento.

### Segmenti installati {#installed-segments}

I segmenti ContextHub sono installati sotto la `/conf/we-retail/settings/wcm/segments` nodo.

* femmina
* femmina-over-30
* femmina sotto i 30 anni
* maschio
* maschio su 30
* maschio-under-30
* order-value-75-to-100
* order-value-over-100
* oltre 30
* estate
* femminile d&#39;estate
* estate-femminile-over-30
* estate-femminile-under-30
* maschio estivo
* estate-maschio-over-30
* estate-maschio-under-30
* under 30
* inverno
* femminile invernale
* inverno-femmina-over-30
* inverno-femmina-under-30
* maschio invernale
* inverno-maschio-over-30
* inverno-maschio-under-20

Le regole utilizzate per risolvere questi segmenti sono riepilogate come segue:

* Femmina o maschio è determinato dalla `gender` la voce [profilo](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) archiviare.

* L’età è determinata dall’elemento dati età dell’archivio profili.
* La stagionalità è determinata dalla voce dei dati di latitudine del [geolocalizzazione](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) e l&#39;elemento dati del mese dell&#39;archivio surferinfo.

>[!WARNING]
>
>I segmenti installati vengono forniti come configurazioni di riferimento per facilitare la creazione di una configurazione dedicata per il progetto e non devono quindi essere utilizzati direttamente.

## Registrazione dei messaggi di debug per ContextHub {#logging-debug-messages-for-contexthub}

Configura il servizio Adobe OSGi ContextHub Granite (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) per registrare messaggi di debug dettagliati utili durante lo sviluppo.

Per configurare il servizio è possibile utilizzare [Console web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) o utilizzare [Nodo JCR nell&#39;archivio](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* Console Web: Per registrare i messaggi di debug, selezionare la proprietà Debug.
* Nodo JCR: Per registrare i messaggi di debug, imposta il valore booleano `com.adobe.granite.contexthub.debug` proprietà di `true`.

## Vedi una panoramica del framework ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub fornisce un [pagina di diagnostica](/help/sites-developing/ch-diagnostics.md) dove puoi visualizzare una panoramica del framework ContextHub.
