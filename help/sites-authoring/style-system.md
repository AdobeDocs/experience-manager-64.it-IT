---
title: Sistema di stili
seo-title: Style System
description: Il sistema di stili consente all’autore del modello di definire le classi di stile nel criterio del contenuto di un componente, in modo che un autore di contenuti possa sceglierli quando modifica un componente in una pagina. Gli stili possono essere varianti visive alternative di un componente, per renderlo più flessibile.
seo-description: The Style System allows a template author to define style classes in the content policy of a component so that a content author is able to select them when editing the component on a page. These styles can be alternative visual variations of a component, making it more flexible.
uuid: 0d857650-8738-49e6-b431-f69c088be74f
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: e3ccddb6-be5e-4e5f-a017-0eed263555ce
exl-id: 8d7282dd-1e21-4862-af04-0daaea431e2c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 62%

---

# Sistema di stili{#style-system}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il sistema di stili consente all’autore del modello di definire le classi di stile nel criterio del contenuto di un componente, in modo che un autore di contenuti possa sceglierli quando modifica un componente in una pagina. Gli stili possono essere varianti visive alternative di un componente, allo scopo di renderlo più flessibile.

Questo elimina la necessità di sviluppare un componente personalizzato per ogni stile o di personalizzare la finestra di dialogo del componente per abilitare tale funzionalità di stile. Conduce a componenti riutilizzabili che possono essere rapidamente e facilmente adattati alle esigenze degli autori di contenuti senza AEM sviluppo back-end.

## Caso d’uso  {#use-case}

Gli autori di modelli non solo devono poter configurare il funzionamento dei componenti per gli autori di contenuti, ma anche configurare diverse varianti visive alternative di un componente.

Allo stesso modo, gli autori dei contenuti non solo devono poter strutturare e disporre i propri contenuti, ma anche selezionare come presentarli visivamente.

Il sistema di stili offre una soluzione unificata alle esigenze degli autori di modelli e di contenuti:

* Gli autori di modelli possono definire le classi di stile nel criterio del contenuto dei componenti.
* Gli autori di contenuti possono quindi selezionare queste classi da un menu a discesa quando modificano il componente su una pagina per applicare gli stili corrispondenti.

La classe di stile viene quindi inserita nell’elemento wrapper decorativo del componente, in modo che lo sviluppatore del componente non debba preoccuparsi della gestione degli stili oltre a fornire le proprie regole CSS.

## Panoramica {#overview}

La procedura per l’uso del sistema di stili è simile alla seguente.

1. Il web designer crea diverse varianti grafiche di un componente.

1. Allo sviluppatore HTML viene fornito l’output HTML dei componenti e le varianti visive desiderate da implementare.

1. Lo sviluppatore HTML definisce le classi CSS corrispondenti a ciascuna variante visiva da inserire nell’elemento che racchiude i componenti.

1. Lo sviluppatore HTML implementa il codice CSS (ed eventualmente il codice JS) corrispondente per ciascuna delle varianti visive in modo che risultino definite.

1. Lo sviluppatore AEM inserisce il CSS fornito (e l’eventuale JS) in una [Libreria client](/help/sites-developing/clientlibs.md) e la distribuisce.

1. Lo sviluppatore AEM o l’autore di modelli configura i modelli di pagina e modifica il criterio di ciascun componente con stili, aggiungendo le classi CSS definite, assegnando nomi descrittivi a ogni stile e indicando quali stili possono essere combinati.

1. L’autore della pagina AEM può quindi scegliere gli stili progettati nell’editor di pagine tramite il menu degli stili, nella barra degli strumenti del componente.

Si noti che solo gli ultimi tre passaggi sono effettivamente eseguiti in AEM. Questo significa che lo sviluppo dei CSS e Javascript necessari può essere fatto senza AEM.

L’implementazione degli stili richiede solo la distribuzione su AEM e la selezione all’interno dei componenti dei modelli desiderati.

Il diagramma seguente illustra l’architettura del sistema di stili.

![aem-style-system](assets/aem-style-system.png)

## Utilizzare {#use}

Per illustrare questa funzione, come esempio verrà utilizzata l’implementazione [WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=it) del [componente titolo](https://www.adobe.com/go/aem_cmp_title_v2_it) del componente core.

Le sezioni seguenti, [Autore di contenuti](#as-a-content-author) e [Autore di modelli](#as-a-template-author) descrivono come verificare la funzionalità del sistema di stili utilizzando il sistema di stili di WKND.

Se desideri utilizzare il sistema di stili per i tuoi componenti, effettua le seguenti operazioni:

1. Installa il CSS come librerie client come descritto nella sezione [Panoramica](#overview).
1. Configura le classi CSS da rendere disponibili agli autori di contenuti come descritto nella sezione [Autore di modelli](#as-a-template-author).
1. Gli autori di contenuti possono quindi utilizzare gli stili come descritto nella sezione [Autore di contenuti](#as-a-content-author).

### Autore di contenuti  {#as-a-content-author}

1. Dopo aver installato il progetto WKND, visita la pagina principale in lingua inglese di WKND all’indirizzo `http://<host>:<port>/sites.html/content/wknd/language-masters/en` e modifica la pagina.
1. Seleziona un componente **Titolo** più in basso nella pagina.

   ![Sistema di stili per l’autore](assets/style-system-author.png)

1. Tocca o fai clic sul pulsante **Stili** nella barra degli strumenti del componente **Elenco** per aprire il menu degli stili e modificare l’aspetto del componente.

   ![Selezione degli stili](assets/style-system-author2.png)

   >[!NOTE]
   >
   >In questo esempio, gli stili **Colori** (**Nero**, **Bianco** e **Grigio**) si escludono a vicenda, mentre le opzioni di **Stile** (**Sottolineato**, **Allinea a destra** e **Spaziatura minima**) possono essere combinate. Tutto questo può essere [configurato nel modello se si è l’autore del modello](#as-a-template-author).

### Autore di modelli  {#as-a-template-author}

1. Durante la modifica della pagina mastro in lingua inglese di WKND all’indirizzo `http://<host>:<port>/sites.html/content/wknd/language-masters/en`, modifica il modello di pagina da **Informazioni pagina > Modifica modello**.

   ![Modifica modello](assets/style-system-edit-template.png)

1. Modifica il criterio del componente **Titolo** toccando o facendo clic sul pulsante **Criterio** del componente.

   ![Modifica del criterio](assets/style-system-edit-policy.png)

1. Nella scheda Stili delle proprietà puoi vedere come sono stati configurati gli stili.

   ![Modifica delle proprietà](assets/style-system-properties.png)

   * **Nome gruppo:** Gli stili possono essere raggruppati all’interno del menu di stile che verrà visualizzato dall’autore del contenuto durante la configurazione dello stile del componente.
   * **Gli stili possono essere combinati:** Consente la selezione simultanea di più stili all’interno del gruppo.
   * **Nome stile:** Descrizione dello stile che verrà visualizzato all’autore del contenuto durante la configurazione dello stile del componente.
   * **Classi CSS:** Nome effettivo della classe CSS associata allo stile.

   Utilizza le maniglie di trascinamento per disporre l’ordine dei gruppi e degli stili all’interno dei gruppi. Utilizza le icone di aggiunta o eliminazione per aggiungere o rimuovere gruppi o stili all’interno dei gruppi.

>[!CAUTION]
>
>Le classi CSS (nonché eventuale codice Javascript) configurate come proprietà di stile di un criterio di un componente devono essere distribuite come [librerie client](/help/sites-developing/clientlibs.md) per poter funzionare.

## Configurazione {#setup}

I componenti core versione 2 e successive sono già configurati in modo da sfruttare il sistema di stili e non richiedono alcuna configurazione aggiuntiva.

I passaggi seguenti sono necessari solo per abilitare il sistema di stile per i componenti personalizzati o per [abilitare la scheda Stili opzionale nella finestra di dialogo Modifica](#enable-styles-tab-edit).

### Abilitare la scheda Stili nella finestra di dialogo di progettazione {#enable-styles-tab-design}

Affinché un componente possa funzionare con il sistema di stili di AEM e visualizzare la scheda Stili nella finestra di dialogo di progettazione, lo sviluppatore del componente deve includere tale scheda con le seguenti impostazioni sul componente:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

Con il componente configurato, gli stili configurati dagli autori delle pagine vengono inseriti automaticamente da AEM sull’elemento decorativo che AEM racchiude automaticamente ogni componente modificabile. Il componente stesso non deve fare altro per farlo accadere.

### Abilitare la scheda Stili nella finestra di dialogo Modifica {#enable-styles-tab-edit}

AEM versione 6.4.7.0 è ora disponibile una scheda Stili opzionale nella finestra di dialogo Modifica . A differenza della scheda della finestra di progettazione, la scheda presente nella finestra di dialogo Modifica non è essenziale per il funzionamento del sistema di stili, ma offre all’autore di contenuti un’interfaccia alternativa opzionale per l’impostazione degli stili.

La scheda della finestra di dialogo Modifica può essere inclusa in modo analogo a quella della finestra di dialogo di progettazione:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_edit/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>
>Per impostazione predefinita, la scheda Stili nella finestra di dialogo Modifica non è abilitata.

### Stili con nomi di elementi  {#styles-with-element-names}

Uno sviluppatore può anche configurare un elenco di nomi di elementi consentiti per gli stili sul componente con la proprietà string array `cq:styleElements`. Quindi, nella scheda Stili del criterio all’interno della finestra di dialogo di progettazione, l’autore del modello può anche scegliere un nome di elemento da impostare per ogni stile. Questo imposta il nome dell’elemento wrapper.

Questa proprietà è impostata sul nodo `cq:Component`. Esempio:

* `/apps/<yoursite>/components/content/list@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Evita di definire i nomi degli elementi per gli stili che possono essere combinati. Quando vengono definiti più nomi di elementi, l’ordine di priorità è:
>
>1. HTL ha la precedenza su tutto: `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Poi, tra più stili attivi, viene considerato il primo nell’elenco degli stili configurati nel criterio del componente.
>1. Infine, il `cq:tagName`/ `cq:htmlTag` del componente sarà considerato un valore di fallback.

>


Questa capacità di definire i nomi degli stili è utile per i componenti molto generici, come Contenitore di layout, o il componente Frammento di contenuto, al fine di attribuire loro un significato aggiuntivo.

Ad esempio, consente di attribuire a un Contenitore di layout semantiche come `<main>`, `<aside>`, `<nav>` e così via.
