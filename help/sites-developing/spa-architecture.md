---
title: Sviluppo di SPA per AEM
seo-title: Developing SPAs for AEM
description: Questo articolo presenta domande importanti da considerare quando si coinvolge uno sviluppatore front-end per sviluppare un SPA per AEM e fornisce una panoramica dell’architettura di AEM rispetto a SPA da tenere a mente quando si implementa un SPA sviluppato su AEM.
seo-description: This article presents important questions to consider when engaging a front-end developer to develop a SPA for AEM as well as gives an overview of the architecture of AEM with respect to SPAs to keep in mind when deploying a developed SPA on AEM.
uuid: c77b37be-6acc-4cb4-9ae3-ba09583e6fff
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 3f4c17cf-6f77-4a87-b27b-f13a6a976523
exl-id: 7b9f21eb-22f6-42f7-8dc7-770601ef51fc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2185'
ht-degree: 5%

---

# Sviluppo di SPA per AEM{#developing-spas-for-aem}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le applicazioni a pagina singola (SPA) possono offrire esperienze coinvolgenti agli utenti di siti web. Gli sviluppatori desiderano essere in grado di creare siti utilizzando framework SPA e gli autori desiderano modificare i contenuti all’interno di AEM per un sito creato utilizzando tali frameworks.

Questo articolo presenta domande importanti da considerare quando si coinvolge uno sviluppatore front-end per sviluppare un SPA per AEM e fornisce una panoramica dell’architettura di AEM rispetto alla distribuzione di SPA su AEM.

>[!NOTE]
>
>La funzione Editor applicazioni a pagina singola (SPA) richiede AEM service pack 2 o successivo 6.4.
>
>L’editor di SPA è la soluzione consigliata per i progetti che richiedono SPA rendering lato client basato su framework (ad esempio, React o Angular).

## Archetipo progetto AEM {#aem-project-archetype}

Qualsiasi progetto AEM deve utilizzare l’[archetipo di progetto AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=it), che supporta progetti SPA utilizzando React o Angular e sfrutta l’SDK di SPA.

## Principi di sviluppo SPA per le AEM {#spa-development-principles-for-aem}

Lo sviluppo di applicazioni a pagina singola in AEM presuppone che lo sviluppatore front-end osservi le best practice standard durante la creazione di una SPA. Se in qualità di sviluppatore front-end segui queste best practice generali e pochi principi AEM specifici, il tuo SPA funzionerà con [AEM e le sue funzionalità di authoring dei contenuti](/help/sites-developing/spa-walkthrough.md#content-editing-experience-with-spa).

* **[Portabilità](/help/sites-developing/spa-architecture.md#portability) -** Come per tutti i componenti, i componenti devono essere costruiti in modo da essere il più possibile portatili. Il SPA deve essere generato con componenti portabili e riutilizzabili, evitando percorsi statici che fanno riferimento alla struttura del contenuto.
* **[Struttura del sito AEM](/help/sites-developing/spa-architecture.md#aem-drives-site-structure)** - Lo sviluppatore front-end crea componenti e possiede la propria struttura interna, ma si basa su AEM per definire la struttura dei contenuti del sito.
* **[Rendering dinamico](/help/sites-developing/spa-architecture.md#dynamic-rendering) -** Tutto il rendering deve essere dinamico.
* **[Routing dinamico](#dynamic-routing) -** Il SPA è responsabile dell’indirizzamento e AEM lo ascolta e recupera i dati del componente in base ad esso. Anche altri routing devono essere dinamici.

Se tieni presenti questi principi durante lo sviluppo del SPA, sarà il più flessibile e scalabile possibile, abilitando tutte le funzionalità di authoring AEM supportate.

Se non è necessario supportare AEM funzioni di authoring, potrebbe essere necessario considerare un [SPA modello di progettazione](/help/sites-developing/spa-architecture.md#spa-design-models).

### Portabilità {#portability}

Come per lo sviluppo di qualsiasi componente, i componenti devono essere progettati in modo da massimizzarne la portabilità. Eventuali schemi che si oppongono alla portabilità o alla riutilizzabilità dei componenti dovrebbero essere evitati per garantire la compatibilità, la flessibilità e la manutenibilità in futuro.

Lo sviluppatore deve evitare di utilizzare percorsi statici che si riferiscono alla struttura del contenuto, in quanto i percorsi possono essere modificati in qualsiasi momento dagli autori dei contenuti. Questo limita anche la riutilizzabilità della libreria e impedisce l’utilizzo dell’Editor modelli di AEM, in quanto la sua struttura si trova in una posizione diversa dal contenuto.

Il SPA risultante deve essere realizzato con componenti altamente portatili e riutilizzabili.

### Struttura del sito AEM {#aem-drives-site-structure}

Lo sviluppatore front-end deve ritenersi responsabile della creazione di una libreria di componenti SPA utilizzati per creare l’app. Lo sviluppatore front-end ha il pieno controllo della struttura interna dei componenti. [Tuttavia AEM in ogni momento possiede la struttura del sito.](/help/sites-developing/spa-overview.md)

Questo significa che lo sviluppatore front-end può aggiungere contenuto del cliente prima o dopo il punto di ingresso dei componenti e può anche effettuare chiamate di terze parti all’interno del componente. Tuttavia, lo sviluppatore front-end non ha il pieno controllo della modalità di nidificazione dei componenti, ad esempio.

### Rendering dinamico {#dynamic-rendering}

Il SPA dovrebbe basarsi solo sul rendering dinamico del contenuto. Questa è l’aspettativa predefinita in cui AEM recupera ed esegue il rendering di tutti gli elementi secondari della struttura del contenuto.

Qualsiasi rendering esplicito che punti a contenuti specifici viene considerato come rendering statico e, sebbene supportato, non sarà compatibile con le funzioni di authoring dei contenuti AEM. Ciò va anche contro il principio [portabilità](/help/sites-developing/spa-architecture.md#portability).

### Routing dinamico {#dynamic-routing}

Come per il rendering, anche tutto il ciclo di produzione deve essere dinamico. In AEM, [il SPA deve sempre essere proprietario del ciclo di produzione](/help/sites-developing/spa-routing.md) e AEM lo ascolta e recupera il contenuto in base ad esso.

Qualsiasi indirizzamento statico funziona contro [principio di portabilità](/help/sites-developing/spa-architecture.md#portability) e limita l’autore non essendo compatibile con le funzioni di authoring dei contenuti di AEM. Ad esempio, con l’indirizzamento statico, se l’autore del contenuto desidera modificare un percorso o una pagina, deve chiedere allo sviluppatore front-end di farlo.

## Modelli di progettazione SPA {#spa-design-models}

Se la [Principi di sviluppo delle SPA in AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem) le SPA funzioneranno con tutte le funzioni di authoring dei contenuti AEM supportate.

Ci possono essere tuttavia casi in cui ciò non è del tutto necessario. La tabella seguente fornisce una panoramica dei vari modelli di progettazione, dei relativi vantaggi e dei relativi svantaggi.

<table> 
 <tbody>
  <tr>
   <th><strong>Modello di progettazione<br /> </strong></th> 
   <th><strong>Vantaggi</strong></th> 
   <th><strong>Svantaggi</strong></th> 
  </tr>
  <tr>
   <td>AEM viene utilizzato come CMS headless senza utilizzare <a href="/help/sites-developing/spa-reference-materials.md">Framework SDK dell’editor SPA.</a></td> 
   <td>Lo sviluppatore front-end ha il pieno controllo sull’app.</td> 
   <td><p>Gli autori di contenuti non possono sfruttare AEM’esperienza di authoring dei contenuti.</p> <p>Il codice non è portatile né riutilizzabile se contiene riferimenti statici o cicli di elaborazione.</p> <p>Non consente l’utilizzo dell’editor modelli, pertanto lo sviluppatore front-end deve mantenere modelli modificabili tramite JCR.</p> </td> 
  </tr>
  <tr>
   <td>Lo sviluppatore front-end utilizza il framework SDK dell’editor di SPA, ma apre solo alcune aree all’autore dei contenuti.</td> 
   <td>Lo sviluppatore mantiene il controllo sull’app abilitando solo l’authoring nelle aree limitate dell’app.</td> 
   <td><p>Gli autori dei contenuti sono limitati a un set limitato di esperienze di authoring dei contenuti AEM.</p> <p>Il codice non rischia di essere portatile né riutilizzabile se contiene riferimenti statici o instradamento.</p> <p>Non consente l’utilizzo dell’editor modelli, pertanto lo sviluppatore front-end deve mantenere modelli modificabili tramite JCR.</p> </td> 
  </tr>
  <tr>
   <td>Il progetto sfrutta appieno l’SDK per l’editor di SPA e i componenti frontend vengono sviluppati come libreria e la struttura del contenuto dell’app viene delegata a AEM.</td> 
   <td><p>L'app è riutilizzabile e portatile.</p> <p>L’autore del contenuto può modificare l’app utilizzando AEM’esperienza di authoring dei contenuti.<br /> </p> <p>L’SPA è compatibile con l’editor modelli.</p> </td> 
   <td><p>Lo sviluppatore non controlla la struttura dell’app e la parte di contenuto delegata a AEM.</p> <p>Lo sviluppatore può comunque riservare aree dell’app per contenuti che non devono essere creati utilizzando AEM.</p> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Anche se tutti i modelli sono supportati in AEM, solo implementando il terzo (e quindi seguendo le raccomandazioni [SPA principi di sviluppo in AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)) gli autori dei contenuti potranno interagire con e modificare il contenuto del SPA in AEM come sono abituati.

## Migrazione di SPA esistenti a AEM {#migrating-existing-spas-to-aem}

Generalmente se il tuo SPA segue il [Principi di sviluppo SPA per le AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem), quindi il tuo SPA funzionerà in AEM e potrà essere modificato utilizzando l’editor SPA AEM.

Segui questi passaggi per rendere il tuo SPA esistente pronto per lavorare con AEM.

1. **Rendi i tuoi componenti JS modulari.**

   Renderli in grado di essere sottoposti a rendering in qualsiasi ordine, posizione e dimensione.

1. **Usa i contenitori forniti dal nostro SDK per posizionare i componenti sullo schermo.**

   AEM fornisce un componente del sistema di paragrafi e di pagina da utilizzare.

1. **Crea un componente AEM per ogni componente JS.**

   I componenti AEM definiscono la finestra di dialogo e l’output JSON.

## Istruzioni per gli sviluppatori front-end {#instructions-for-front-end-developers}

Il compito principale nell’coinvolgere uno sviluppatore front-end per creare un SPA per AEM è quello di concordare i componenti e i relativi modelli JSON.

Di seguito è riportato un profilo dei passaggi che uno sviluppatore front-end deve seguire durante lo sviluppo di un SPA per AEM.

1. **Accettare i componenti e il relativo modello JSON**

   Gli sviluppatori front-end e gli sviluppatori di back-end AEM devono concordare quali componenti sono necessari e un modello in modo che ci sia una corrispondenza uno a uno dai componenti SPA ai componenti back-end.

   AEM componenti sono ancora necessari principalmente per fornire finestre di dialogo di modifica ed esportare il modello componente.

1. **In React components, accedi al modello tramite`this.props.cqModel`**

   Una volta concordati i componenti e implementato il modello JSON, lo sviluppatore front-end è libero di sviluppare il SPA e può semplicemente accedere al modello JSON tramite `this.props.cqModel`.

1. **Implementare `render()` metodo**

   Lo sviluppatore front-end implementa le `render()` metodo che ritiene idoneo e può utilizzare i campi `cqModel` proprietà. In questo modo vengono generati i frammenti DOM e HTML che verranno inseriti nella pagina. Questo è il modo standard per creare un’app in React.

1. **Mappa il componente sul tipo di risorsa AEM tramite`MapTo()`**

   La mappatura memorizza le classi di componenti e viene utilizzata internamente dal `Container` per recuperare e creare dinamicamente un’istanza dei componenti in base al tipo di risorsa specificato.

   Questa funzione funge da &quot;colla&quot; tra front end e back end, in modo che l&#39;editor sappia a quali componenti corrispondono i componenti reattivi.

   La `Page` e `ResponsiveGrid` sono buoni esempi di classi che estendono la base `Container`.

1. **Definisci i del componente `EditConfig` come parametro per`MapTo()`**

   Questo parametro è necessario per dire all’editor come deve essere chiamato il componente a lungo che non è ancora stato sottoposto a rendering o non ha contenuto da riprodurre.

1. **Estendi i `Container` Classe per pagine e contenitori**

   Le pagine e i sistemi di paragrafo devono estendere questa classe in modo che la delega ai componenti interni funzioni come previsto.

1. **Implementare una soluzione di routing che utilizza HTML5 `History` API.**

   Quando il `ModelRouter` è abilitato, chiamando il `pushState` e `replaceState` le funzioni attiveranno una richiesta `PageModelManager` per recuperare un frammento mancante del modello.

   La versione corrente del `ModelRouter` supporta solo l’uso di URL che puntano al percorso effettivo della risorsa dei punti di ingresso del modello Sling. Non supporta l’uso di URL personalizzati o alias.

   La `ModelRouter` può essere disabilitato o configurato per ignorare un elenco di espressioni regolari.

## AEM-Agnostico {#aem-agnostic}

Questi blocchi di codice illustrano come i componenti React e Angular non necessitano di elementi specifici per un Adobe o un AEM.

* Tutto ciò che si trova all’interno del componente JavaScript è indipendente dalla AEM.
* Ciò che è tuttavia specifico di AEM è che il componente JS deve essere mappato su un componente AEM con l’helper MapTo.

![screen_shot_2018-12-11at144019](assets/screen_shot_2018-12-11at144019.png)

La `MapTo` helper è la &quot;colla&quot; che consente di associare i componenti back-end e front-end:

* Indica al contenitore JS (o al sistema di paragrafi JS) quale componente JS è responsabile del rendering di ciascuno dei componenti presenti nel JSON.
* Aggiunge un attributo di dati HTML al HTML di cui viene eseguito il rendering del componente JS, in modo che l’Editor di SPA sappia quale finestra di dialogo visualizzare all’autore durante la modifica del componente.

Per ulteriori informazioni sull&#39;utilizzo di `MapTo` e costruire SPA per AEM in generale, vedere la Guida introduttiva per il framework scelto.

* [Guida introduttiva a SPA in AEM - React](/help/sites-developing/spa-getting-started-react.md)
* [Guida introduttiva a SPA in AEM - Angular](/help/sites-developing/spa-getting-started-angular.md)

## Architettura AEM e SPA {#aem-architecture-and-spas}

L’architettura generale di AEM, inclusi gli ambienti di sviluppo, authoring e pubblicazione, non cambia quando si utilizza SPA. Tuttavia, è utile comprendere come lo sviluppo SPA si inserisce in questa architettura.

![screen_shot_2018-12-11at145348](assets/screen_shot_2018-12-11at145348.png)

* **Ambiente di build**

   In questo punto viene estratto l’origine dell’applicazione SPA e l’origine del componente.

   * Il generatore clientlib NPM crea una libreria client dal progetto SPA.
   * Tale libreria verrà prelevata da Maven e distribuita dal plug-in Maven Build insieme al componente per l’authoring di AEM.

* **Autore AEM**

   Il contenuto viene creato sull’autore AEM, inclusa la SPA di authoring.

   Quando un SPA viene modificato utilizzando l’Editor SPA nell’ambiente di authoring:

   1. Il SPA richiede il HTML esterno.
   1. Il CSS viene caricato.
   1. Viene caricato il codice JavaScript dell&#39;applicazione SPA.
   1. Quando l’applicazione SPA viene eseguita, viene richiesto il JSON, che consente all’app di creare il DOM della pagina, incluso il `cq-data` attributi.
   1. Questo `cq-data` attributes consente all&#39;editor di caricare informazioni aggiuntive sulla pagina in modo che sappia quali configurazioni di modifica sono disponibili per i componenti.

* **AEM Publish**

   In questo punto i contenuti creati e le librerie compilate, inclusi gli artefatti SPA applicazioni, le clientlibs e i componenti, vengono pubblicati per l’uso pubblico.

* **Dispatcher / CDN**

   Il dispatcher funge da livello di caching di AEM per i visitatori del sito.

   * Le richieste vengono elaborate in modo simile a come si trovano in AEM Author, tuttavia non vi è alcuna richiesta di informazioni sulla pagina, in quanto ciò è necessario solo per l’editor.
   * Javascript, CSS, JSON e HTML vengono memorizzati nella cache, ottimizzando la pagina per la consegna rapida.

>[!NOTE]
>
>All’interno AEM non è necessario eseguire meccanismi di creazione Javascript o eseguire il codice Javascript stesso. AEM ospita solo gli artefatti compilati dall&#39;applicazione SPA.

## Passaggi successivi {#next-steps}

Per una panoramica della struttura e del funzionamento di un SPA semplice in AEM, consulta la guida introduttiva per entrambe le [Reagire](/help/sites-developing/spa-getting-started-react.md) e [Angular](/help/sites-developing/spa-getting-started-angular.md).

Per una guida dettagliata alla creazione di un tuo SPA, consulta la sezione [Guida introduttiva all’editor di SPA AEM - Tutorial eventi WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=it).

Per ulteriori dettagli sul modello dinamico per la mappatura dei componenti e su come funziona all’interno di SPA in AEM, consulta l’articolo [Mappatura dinamica da modello a componente per SPA](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Se desideri implementare SPA in AEM per un framework diverso da React o Angular o desideri semplicemente approfondire il funzionamento dell’SDK SPA per AEM, consulta [Blueprint SPA](/help/sites-developing/spa-blueprint.md) articolo.
