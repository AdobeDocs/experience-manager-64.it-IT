---
title: Utilizzo di frammenti di contenuto
seo-title: Working with Content Fragments
description: Scopri come i frammenti di contenuto ti consentono di progettare, creare, curare e utilizzare contenuti indipendenti dalla pagina.
seo-description: Learn how Content Fragments allow you to design, create, curate and use page-independent content.
uuid: aa5acda2-4c20-4fe7-929d-6c065b252cf2
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 22ae0d3a-083f-40e4-bf4a-7a755ae9e312
exl-id: e2804707-7b75-4fae-937e-9e258481878f
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1984'
ht-degree: 76%

---

# Utilizzo di frammenti di contenuto {#working-with-content-fragments}

>[!CAUTION]
>
>Alcune funzionalità dei frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](/help/release-notes/sp-release-notes.md).

I frammenti di contenuto di Adobe Experience Manager (AEM) consentono di progettare, creare, curare e [pubblicare contenuti indipendenti dalla pagina](/help/sites-authoring/content-fragments.md). Consentono di preparare i contenuti pronti per l’uso in più posizioni/su più canali.

I frammenti di contenuto possono essere consegnati anche in formato JSON, utilizzando le funzionalità di esportazione Sling Model (JSON) dei componenti core di AEM. Questo tipo di consegna:

* consente di utilizzare il componente per gestire gli elementi di un frammento da consegnare;
* consente la consegna in massa, aggiungendo più componenti core per frammenti di contenuto nella pagina utilizzata per la consegna API.

Nelle pagine seguenti sono illustrate le attività di creazione, configurazione e manutenzione dei frammenti di contenuto:

* [Gestione dei frammenti di contenuto](content-fragments-managing.md): come creare frammenti di contenuto, quindi modificarli, pubblicarli e farvi riferimento.

* [Modelli per frammenti di contenuto](content-fragments-models.md): come abilitare, creare e definire i modelli

* [Varianti: authoring dei contenuti di frammenti](content-fragments-variations.md): come creare il contenuto di un frammento e quindi varianti del contenuto principale

* [Markdown](content-fragments-markdown.md): come utilizzare la sintassi markdown per il frammento

* [Utilizzo di contenuti associati](content-fragments-assoc-content.md): come aggiungere contenuti associati

* [Metadati: proprietà dei frammenti](content-fragments-metadata.md): come visualizzare e modificare le proprietà dei frammenti

>[!NOTE]
>
>Queste pagine devono essere lette insieme a [Authoring delle pagine con frammenti di contenuto](/help/sites-authoring/content-fragments.md).

Il numero di canali di comunicazione aumenta ogni anno. In genere i canali si distinguono in base al meccanismo di consegna, come segue:

* Canale fisico, ad esempio desktop o mobile.
* Forma di consegna in un canale fisico, ad esempio “pagina dei dettagli di un prodotto”, “pagina della categoria del prodotto” per desktop oppure “web mobile”, “app mobile” per dispositivi mobili.

Tuttavia, probabilmente non vorrai utilizzare esattamente gli stessi contenuti per tutti i canali: vorrai piuttosto ottimizzarli in base ai singoli canali.

I frammenti di contenuto consentono di:

* valutare come raggiungere in modo efficiente il pubblico target su ciascun canale;
* creare e gestire contenuti editoriali indipendenti dal canale;
* creare pool di contenuti per una serie di canali;
* progettare varianti di contenuto per canali specifici;
* aggiungere immagini al testo inserendo delle risorse (frammenti con elementi multimediali diversi);

I frammenti di contenuto possono quindi essere assemblati per fornire esperienze su diversi canali.

## Frammenti di contenuto e Content Services {#content-fragments-and-content-services}

AEM Content Services è progettato per generalizzare la descrizione e la consegna dei contenuti in/da AEM, non limitandosi alle pagine web.

Fornisce contenuti a canali diversi dalle tradizionali pagine web di AEM, utilizzando metodi standardizzati utilizzabili da qualsiasi cliente. Questi canali possono includere:

* Applicazioni a pagina singola
* Applicazioni mobile native
* Altri canali e punti di contatto esterni ad AEM

La consegna viene effettuata in formato JSON.

I frammenti di contenuto di AEM possono essere utilizzati per descrivere e gestire contenuti strutturati. Il contenuto strutturato è definito in modelli che possono contenere diversi tipi di contenuto, compresi testo, dati numerici, dati booleani, data e ora e altro ancora.

Insieme alle funzionalità di esportazione JSON dei componenti core di AEM, tali contenuti strutturati possono quindi essere utilizzati per consegnare contenuti AEM a canali diversi dalle pagine AEM.

>[!NOTE]
>
>I **frammenti di contenuto** e i **[frammenti di esperienza](/help/sites-authoring/experience-fragments.md)** sono funzioni diverse in AEM:
>
>* I **frammenti di contenuto** sono contenuti editoriali, in particolare testo e immagini correlate. Sono contenuti puri, privi di design e layout.
>* I **frammenti di esperienza** sono contenuti completi di layout, frammenti di una pagina web.
>
>I frammenti esperienza possono includere contenuti sotto forma di frammenti di contenuto, ma non viceversa.
>
>Per ulteriori informazioni consulta anche [Frammenti di contenuto e frammenti di esperienza in AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/content-fragments-experience-fragments-article-understand.html).

>[!CAUTION]
>
>I frammenti di contenuto non sono disponibili nell’interfaccia classica.
>
>Il componente Frammento di contenuto può essere visualizzato nella barra laterale dell’interfaccia classica, ma ulteriori funzionalità non sono disponibili.

>[!NOTE]
>
>AEM supporta anche la traduzione del contenuto dei frammenti. Vedi [Creazione di progetti di traduzione per frammenti di contenuto](creating-translation-projects-for-content-fragments.md) per ulteriori informazioni.

## Tipi di frammenti di contenuto {#types-of-content-fragment}

I frammenti di contenuto possono essere:

* Frammenti semplici

   * Non hanno una struttura predefinita. Contengono solo testo e immagini.
   * Si basano sul modello Frammento semplice .

* Frammenti contenenti contenuto strutturato

   * Si basano su [Modello per frammento di contenuto](content-fragments-models.md), che predefinisce una struttura per il frammento risultante.
   * Questi possono anche essere utilizzati per realizzare Content Services utilizzando l’esportatore JSON.

## Tipo di contenuto {#content-type}

I frammenti di contenuto sono:

* Memorizzati come **Risorse**:

   * I frammenti di contenuto (e le relative varianti) possono essere creati e mantenuti dal **Risorse** console.
   * Vengono creati e modificati nell’Editor frammenti di contenuto.

* Utilizzati nell’[editor pagina tramite il componente Frammento di contenuto](/help/sites-authoring/content-fragments.md) (componente di riferimento):

   * Il componente **Frammento di contenuto** è disponibile per gli autori delle pagine. Consente loro di fare riferimento e distribuire il frammento di contenuto richiesto in formato HTML o JSON.

I frammenti di contenuto sono una struttura di contenuto che:

* è priva di layout o design (in modalità Testo formattato è possibile formattare del testo);
* contiene una o più [parti costituenti](#constituent-parts-of-a-content-fragment);
* può [contenere immagini o essere connessa ad esse](#fragments-with-visual-assets);
* può utilizzare [contenuto intermedio](#in-between-content-when-page-authoring-with-content-fragments) se referenziato in una pagina;

* è indipendente dal meccanismo di consegna (ad esempio, pagina, canale).

### Frammenti con risorse visive {#fragments-with-visual-assets}

Per dare agli autori un maggiore controllo sui contenuti, le immagini possono essere aggiunte a e/o integrate con un frammento di contenuto.

Le risorse possono essere utilizzate con un frammento di contenuto in diversi modi, ciascuno con i propri vantaggi:

* Tramite **Inserisci risorsa** per inserire una risorsa in un frammento (frammenti con elementi multimediali diversi)

   * Sono parte integrante del frammento (vedi [Parti costitutive di un frammento di contenuto](#constituent-parts-of-a-content-fragment)).
   * Viene definita la posizione della risorsa.
   * Per ulteriori informazioni consulta [Inserimento di risorse nel frammento](content-fragments-variations.md#inserting-assets-into-your-fragment) nell’editor di frammenti.

   >[!NOTE]
   >
   >Le risorse visive inserite nel frammento di contenuto stesso sono associate al paragrafo precedente. Quando il frammento viene aggiunto a una pagina e quindi viene aggiunto del contenuto intermedio, queste risorse si spostano in relazione a tale paragrafo.

* Come **Contenuto associato**

   * È collegato a un frammento, ma non è una parte fissa del frammento (vedi [Parti costitutive di un frammento di contenuto](#constituent-parts-of-a-content-fragment)).
   * Offre una certa flessibilità di posizionamento.
   * È facilmente disponibile per l’uso (come contenuto intermedio) quando si utilizza il frammento su una pagina.
   * Per ulteriori informazioni vedi [Contenuto associato](content-fragments-assoc-content.md).

* Risorse disponibili nel **browser Risorse** dell’editor pagina

   * Offrono massima flessibilità nella selezione di una risorsa.
   * Offre una certa flessibilità di posizionamento.
   * Non supportano il concetto di approvazione per un frammento specifico.
   * Per ulteriori informazioni vedi [Browser risorse](/help/sites-authoring/author-environment-tools.md#assets-browser).

### Parti costitutive di un frammento di contenuto {#constituent-parts-of-a-content-fragment}

Le risorse dei frammenti di contenuto sono composte dalle seguenti parti (direttamente o indirettamente):

* **Elementi del frammento**

   * Gli elementi sono correlati ai campi di dati che contengono il contenuto.
   * Per i frammenti con contenuto strutturato, è possibile utilizzare un modello di contenuto per creare il frammento di contenuto. Gli elementi (campi) specificati nel modello definiscono la struttura del frammento. Questi elementi (campi) possono essere di diversi tipi di dati.
   * Per frammenti semplici:

      * Il contenuto è contenuto in uno o più campi di testo a più righe o elementi.
      * Gli elementi sono definiti nel modello di frammento (non è possibile definirli durante la creazione del frammento, consulta [Modelli per frammenti di contenuto](/help/sites-developing/content-fragment-templates.md)).

* **Paragrafi del frammento**

   * Blocchi di testo, ovvero:

      * separati da spazi verticali (ritorno a capo)
      * in elementi di testo su più righe; in frammenti semplici o strutturati
   * Nelle modalità [Testo formattato](content-fragments-variations.md#rich-text) e [Markdown](content-fragments-variations.md#markdown), un paragrafo può essere formattato come intestazione, in tal caso appartiene a un’unica unità insieme al paragrafo seguente.
   * Consentono di controllare i contenuti durante l’authoring delle pagine.


* **Risorse inserite in un frammento (frammenti con elementi multimediali diversi)**

   * Risorse (immagini) inserite nel frammento effettivo e utilizzate come contenuto interno di un frammento.
   * Sono incorporate nel sistema paragrafo del frammento.
   * Possono essere formattate quando il [frammento viene utilizzato o inserito come riferimento in una pagina](/help/sites-authoring/content-fragments.md).
   * Possono solo essere aggiunte, eliminate o spostate all’interno di un frammento utilizzando l’editor di frammenti. Queste azioni non possono essere eseguite nell’editor pagina.
   * Possono essere aggiunte, eliminate o spostate all’interno di un frammento solo utilizzando il formato [Testo formattato nell’editor di frammenti](content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Possono essere aggiunte solo a elementi di testo su più righe (qualsiasi tipo di frammento).
   * Sono associate al testo che precede (paragrafo).

   >[!CAUTION]
   >
   >Può essere rimosso (inavvertitamente) da un frammento passando al formato Testo normale.

   >[!NOTE]
   >
   >È inoltre possibile aggiungere le risorse come [contenuto aggiuntivo (intermedio)](/help/sites-authoring/content-fragments.md#using-associated-content) quando si utilizza un frammento su una pagina, utilizzando Contenuto associato o risorse dal Browser risorse.

* **Contenuto associato**

   * Contenuti esterni a un frammento, ma con rilevanza editoriale per esso. In genere si tratta di immagini, video o altri frammenti.
   * Le singole risorse all’interno di una raccolta sono disponibili per essere utilizzate con il frammento nell’editor pagina quando questo viene aggiunto a una pagina. Sono quindi elementi opzionali, a seconda dei requisiti del canale specifico.
   * Le risorse sono [associate a frammenti tramite raccolte](content-fragments-assoc-content.md); le raccolte associate consentono all’autore di decidere quali risorse utilizzare durante l’authoring della pagina.

      * Le raccolte possono essere associate ai frammenti tramite modelli, come contenuto predefinito o da parte degli autori durante la creazione dei frammenti.
      * Le [raccolte di risorse (DAM)](managing-collections-touch-ui.md) sono la base del contenuto associato dei frammenti.
   * Volendo, puoi anche aggiungere il frammento stesso a una raccolta per facilitare il tracciamento.


* **Metadati del frammento**

   * Utilizzano gli [schemi di metadati delle risorse](metadata.md).
   * È possibile creare i tag quando:

      * si crea e si effettua l’authoring del frammento;
      * oppure in un secondo tempo:

         * visualizzando e modificando le **Proprietà** del frammento dalla console;
         * modificando i **Metadati** nell’editor di frammenti.

   >[!CAUTION]
   >
   >I profili di elaborazione dei metadati non sono applicabili ai frammenti di contenuto.

* **Principale**

   * Parte integrante del frammento

      * Ogni frammento di contenuto dispone di un’istanza Principale.
      * L’elemento Principale non può essere eliminato.
   * L’elemento Principale è accessibile nella sezione **[Varianti](content-fragments-variations.md)** dell’editor di frammenti.
   * l’elemento Principale non è una variante in sé, ma è la base di tutte le varianti.


* **Varianti**

   * Sono rappresentazioni di testo dei frammenti a scopo editoriale; possono essere relative a un canale ma non necessariamente, e possono anche essere utilizzate per modifiche locali ad hoc.
   * Sono create come copie dell’elemento **Principale**, ma possono essere modificate secondo necessità; di solito c’è una sovrapposizione di contenuti tra le varianti stesse.
   * Può essere definito durante l’authoring dei frammenti o predefinito nei modelli di frammento.
   * Sono memorizzate nel frammento, per evitare la dispersione delle copie del contenuto.
   * Le varianti possono essere [sincronizzate](content-fragments-variations.md#synchronizing-with-master) con l’elemento principale se il suo contenuto viene aggiornato.
   * Il testo può essere [riepilogato](content-fragments-variations.md#summarizing-text) per ridurlo rapidamente a una lunghezza predefinita.
   * Sono disponibili nella scheda [Varianti](content-fragments-variations.md) dell’editor di frammenti.

### Contenuto intermedio nell’authoring di pagine con frammenti di contenuto {#in-between-content-when-page-authoring-with-content-fragments}

Contenuto intermedio:

* Può essere utilizzato nell’[Editor pagina quando si lavora con frammenti di contenuto](/help/sites-authoring/content-fragments.md).
* Una volta utilizzato o inserito mediante riferimento in una pagina, diventa [contenuto aggiuntivo all’interno del flusso di un frammento](/help/sites-authoring/content-fragments.md#adding-in-between-content).
* Il contenuto intermedio può essere aggiunto a qualsiasi frammento, in cui è visibile un solo elemento.
* È possibile utilizzare il contenuto associato, così come le risorse e/o i componenti dal browser appropriato.

>[!CAUTION]
>
>Il contenuto intermedio è contento di pagina. Non viene memorizzato nel frammento di contenuto.

### Elementi necessari per i frammenti {#required-by-fragments}

Per creare, modificare e utilizzare frammenti di contenuto è inoltre necessario effettuare le operazioni riportate di seguito.

* **Modello di contenuto**

   * Sono [abilitato e quindi creato mediante Strumenti](content-fragments-models.md).
   * Obbligatorio per [creare un frammento strutturato](content-fragments-managing.md#creating-content-fragments).
   * Definisce la struttura di un frammento (titolo, elementi di contenuto, definizioni tag).
   * Le definizioni dei modelli di contenuto richiedono un titolo e un elemento dati; tutto il resto è facoltativo. Il modello definisce un ambito minimo del frammento e, se applicabile, del contenuto predefinito. Durante l’authoring del contenuto di un frammento, gli autori non possono modificare la struttura definita.

* **Modello frammento**

   * Obbligatorio per [creare un frammento semplice](content-fragments-managing.md#creating-content-fragments).
   * Di solito [sviluppato durante l&#39;implementazione del progetto](/help/sites-developing/content-fragment-templates.md); non può essere creato durante l’authoring.
   * Definisce le proprietà di base di un frammento semplice (titolo, numero di elementi di testo, definizioni di tag).
   * Le definizioni dei modelli richiedono un titolo e un elemento di testo; tutto il resto è facoltativo. Il modello definisce un ambito minimo del frammento e, se applicabile, del contenuto predefinito. In seguito, gli autori possono estendere un frammento oltre a quanto definito nel modello.

* **Componente Frammento di contenuto**

   * Essenziale per la distribuzione del frammento in formato HTML e/o JSON.
   * Obbligatorio per [fare riferimento al frammento in una pagina](/help/sites-authoring/content-fragments.md).
   * Responsabile del layout e della distribuzione di un frammento, ovvero i canali.
   * I frammenti devono disporre di uno o più componenti dedicati per definire il layout e fornire alcuni o tutti gli elementi/varianti e i contenuti associati.
   * Quando si trascina un frammento su una pagina in fase di authoring, il componente richiesto viene associato automaticamente.

## Esempio di utilizzo {#example-usage}

Un frammento, con i relativi elementi e varianti, può essere utilizzato per creare contenuti coerenti per più canali. Durante la progettazione del frammento è necessario considerare quali elementi verranno utilizzati e dove.

### Esempio di We.Retail {#we-retail-sample}

Un frammento di esempio è disponibile in:

[http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)
