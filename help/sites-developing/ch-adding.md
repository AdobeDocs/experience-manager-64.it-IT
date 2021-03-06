---
title: Aggiunta di ContextHub alle pagine e accesso agli store
seo-title: Aggiunta di ContextHub alle pagine e accesso agli store
description: Aggiungere ContextHub alle pagine per abilitare le funzionalità ContextHub e per collegarsi alle librerie ContextHub Javascript
seo-description: Aggiungere ContextHub alle pagine per abilitare le funzionalità ContextHub e per collegarsi alle librerie ContextHub Javascript
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---


# Aggiunta di ContextHub alle pagine e accesso agli store {#adding-contexthub-to-pages-and-accessing-stores}

Aggiungere ContextHub alle pagine per abilitare le funzionalità ContextHub e per collegarsi alle librerie ContextHub Javascript

L&#39;API ContextHub Javascript fornisce l&#39;accesso ai dati contestuali gestiti da ContextHub. Questa pagina descrive brevemente le funzioni principali dell&#39;API per l&#39;accesso e la manipolazione dei dati contestuali. Seguite i collegamenti alla documentazione di riferimento API per visualizzare informazioni dettagliate ed esempi di codice.

## Aggiunta di ContextHub a un componente pagina {#adding-contexthub-to-a-page-component}

Per abilitare le funzioni ContextHub e per collegarsi alle librerie ContextHub Javascript, includete il componente contestub nella sezione `head` della pagina. Il codice JSP per il componente pagina è simile al seguente esempio:

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

È inoltre necessario configurare la visualizzazione della barra degli strumenti ContextHub in modalità Anteprima. Consultate [Mostrare e nascondere l&#39;interfaccia utente ContextHub](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui).

## Informazioni su ContextHub Store {#about-contexthub-stores}

Utilizzate gli store ContextHub per mantenere i dati contestuali. ContextHub fornisce i seguenti tipi di store che costituiscono la base di tutti i tipi di store:

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

Tutti i tipi di store sono estensioni della classe [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core). Per informazioni sulla creazione di un nuovo tipo di store, vedere [Creazione di store personalizzati](/help/sites-developing/ch-extend.md#creating-custom-store-candidates). Per informazioni sui tipi di store di esempio, consultate [Sample ContextHub Store Candidate](/help/sites-developing/ch-samplestores.md).

### Modalità di persistenza {#persistence-modes}

Gli store Context Hub utilizzano una delle seguenti modalità di persistenza:

* **Locale:** utilizza HTML5 localStorage per mantenere i dati. L&#39;archiviazione locale viene mantenuta nel browser tra le sessioni.
* **Sessione:** utilizza HTML5 sessionStorage per mantenere i dati. L&#39;archiviazione delle sessioni viene mantenuta per tutta la durata della sessione del browser ed è disponibile per tutte le finestre del browser.
* **Cookie:** utilizza il supporto nativo dei cookie del browser per l&#39;archiviazione dei dati. I dati del cookie vengono inviati a e dal server in richieste HTTP.
* **Window.name:** utilizza la proprietà window.name per mantenere i dati.
* **Memoria:** utilizza un oggetto Javascript per mantenere i dati.

Per impostazione predefinita, Context Hub utilizza la modalità di persistenza locale. Se il browser non supporta o non consente HTML5 localStorage, viene utilizzata la persistenza della sessione. Se il browser non supporta o non consente HTML5 sessionStorage, viene utilizzata la persistenza Window.name.

### Dati store {#store-data}

All&#39;interno, memorizzare i dati in una struttura ad albero, consentendo l&#39;aggiunta di valori come tipi primari o oggetti complessi. Quando si aggiungono oggetti complessi agli store, le proprietà dell&#39;oggetto vengono suddivise in rami nella struttura dei dati. Ad esempio, il seguente oggetto complesso viene aggiunto a uno store vuoto denominato location:

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

La struttura ad albero dei dati dello store può essere concettualizzata come segue:

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

La struttura ad albero definisce gli elementi dati nell&#39;archivio come coppie chiave/valore. Nell&#39;esempio precedente, la chiave `/number` corrisponde al valore `321` e la chiave `/data/country` corrisponde al valore `Switzerland`.

### Manipolazione di oggetti {#manipulating-objects}

ContextHub fornisce la classe [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) per la manipolazione degli oggetti Javascript. Utilizzare le funzioni di questa classe per manipolare gli oggetti Javascript prima di aggiungerli a uno store o dopo averli ottenuti da uno store.

Inoltre, la classe [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) fornisce funzioni per la serializzazione degli oggetti alle stringhe e la deserializzazione delle stringhe agli oggetti. Utilizzare questa classe per gestire i dati JSON per supportare i browser che non includono in modo nativo le funzioni `JSON.parse` e `JSON.stringify`.

## Interazione con gli store ContextHub {#interacting-with-contexthub-stores}

Utilizzare l&#39;oggetto JavaScript [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) per ottenere uno store come oggetto Javascript. Una volta ottenuto l&#39;oggetto store è possibile manipolare i dati in esso contenuti. Utilizzare la funzione [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) o [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) per ottenere lo store.

### Accesso ai dati dell&#39;archivio {#accessing-store-data}

La classe [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) Javascript definisce diverse funzioni per l&#39;interazione con i dati dello store. Le seguenti funzioni memorizzano e recuperano più elementi di dati contenuti negli oggetti:

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

I singoli elementi di dati sono memorizzati come un insieme di coppie chiave/valore. Per memorizzare e recuperare i valori si specifica la chiave corrispondente:

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

I candidati all&#39;archivio personalizzati possono definire funzioni aggiuntive che forniscono l&#39;accesso ai dati dell&#39;archivio.

>[!NOTE]
>
>Per impostazione predefinita, ContextHub non è a conoscenza dell&#39;accesso attualmente utilizzato sui server di pubblicazione e tali utenti sono considerati da ContextHub come &quot;anonimi&quot;.
>
>Puoi rendere ContextHub consapevole degli utenti che hanno eseguito l&#39;accesso caricando l&#39;archivio profili come implementato nel [sito di riferimento We.Retail](/help/sites-developing/we-retail.md). Fare riferimento al [codice pertinente su GitHub qui](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### Evento ContextHub {#contexthub-eventing}

ContextHub include un framework di eventi che consente di reagire automaticamente agli eventi di memorizzazione. Ciascun oggetto store contiene un oggetto [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) disponibile come proprietà [`eventing`](/help/sites-developing/contexthub-api.md#eventing) dello store. Utilizzare la funzione [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) o [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) per associare una funzione Javascript a un evento store.

## Utilizzo di Context Hub per manipolare i cookie {#using-context-hub-to-manipulate-cookies}

L&#39;API Context Hub Javascript fornisce il supporto cross-browser per la gestione dei cookie del browser. Lo spazio dei nomi [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) definisce diverse funzioni per la creazione, la manipolazione e l&#39;eliminazione dei cookie.

## Determinazione dei segmenti ContextHub risolti {#determining-resolved-contexthub-segments}

Il motore del segmento ContextHub consente di determinare quali segmenti registrati vengono risolti nel contesto corrente. Utilizzare la funzione getResolvedSegments della classe [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) per recuperare i segmenti risolti. Quindi, utilizzate la funzione `getName` o `getPath` della classe [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) per eseguire il test per un segmento.

### Segmenti installati {#installed-segments}

I segmenti ContextHub sono installati sotto il nodo `/conf/we-retail/settings/wcm/segments`.

* femmina
* femmina su 30
* femmina sotto i 30
* maschio
* maschio su 30
* maschile sotto i 30
* order-value-75-to-100
* order-value-over-100
* over-30
* estate
* estiva femminile
* estate-femminile-over-30
* estiva-femminile-under-30
* estivo-maschio
* estate-maschio-over-30
* estivo-maschile-under-30
* under 30
* inverno
* invernale femminile
* invernale femminile su 30
* invernale-femminile-under-30
* invernale
* inverno-maschio-over-30
* invernale-maschile-under-20

Le regole utilizzate per risolvere questi segmenti sono riepilogate come segue:

* Le donne o gli uomini sono determinati dall&#39;elemento di dati `gender` dello store [profile](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate).

* L’età è determinata dall’elemento dati età dell’archivio profili.
* La stagione è determinata dall&#39;elemento dei dati di latitudine dello store [geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) e dall&#39;elemento dei dati del mese dello store surferinfo.

>[!WARNING]
>
>I segmenti installati sono forniti come configurazioni di riferimento per facilitare la creazione di una propria configurazione dedicata per il progetto e come tali non devono essere utilizzati direttamente.

## Registrazione dei messaggi di debug per ContextHub {#logging-debug-messages-for-contexthub}

Configurate il servizio  Adobe Granite ContextHub OSGi (PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`) per registrare i messaggi di debug dettagliati utili durante lo sviluppo.

Per configurare il servizio è possibile utilizzare la [console Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) oppure utilizzare un nodo [JCR nell&#39;archivio](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* Console Web: Per registrare i messaggi di debug, selezionare la proprietà Debug.
* Nodo JCR: Per registrare i messaggi di debug, impostare la proprietà booleana `com.adobe.granite.contexthub.debug` su `true`.

## Vedere una panoramica del framework ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub fornisce una [pagina di diagnostica](/help/sites-developing/ch-diagnostics.md) in cui potete vedere una panoramica del framework ContextHub.
