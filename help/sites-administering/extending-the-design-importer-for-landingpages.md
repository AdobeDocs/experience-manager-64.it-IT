---
title: Estensione e configurazione dell’importazione di progettazione per le pagine di destinazione
seo-title: Extending and Configuring the Design Importer for Landing Pages
description: Scopri come configurare Importazione progettazione per le pagine di destinazione.
seo-description: Learn how to configure the Design Importer for landing pages.
uuid: b2bfe831-bfaf-43f3-babc-687bf229dd44
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: f8991416-995b-4160-a705-d131e78089ee
exl-id: 4b37c866-30c3-45ff-b7a3-013b69598668
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3526'
ht-degree: 0%

---

# Estensione e configurazione dell’importazione di progettazione per le pagine di destinazione{#extending-and-configuring-the-design-importer-for-landing-pages}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa sezione descrive come configurare ed eventualmente estendere Importazione progettazione per le pagine di destinazione. L’utilizzo delle pagine di destinazione dopo l’importazione è trattato in [Pagine di destinazione.](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)

**Estrazione del componente personalizzato da parte di Importazione progettazione**

Di seguito sono riportati i passaggi logici per il riconoscimento del componente personalizzato da parte di Importazione progettazione

1. Creare un gestore di tag

   * Un gestore di tag è un POJO che gestisce i tag HTML di un tipo specifico. Il &quot;tipo&quot; di tag HTML che il gestore di tag può gestire è definito tramite la proprietà TagHandlerFactory OSGi &quot;tagpattern.name&quot;. Questa proprietà OSGi è essenzialmente un regex che deve corrispondere al tag HTML di input che desideri gestire. Tutti i tag nidificati vengono inviati al gestore di tag per la gestione. Ad esempio, se ti registri per un div che contiene un elemento nidificato &lt;p> tag, &lt;p> Il tag viene inviato anche al gestore di tag e dipende da come desideri gestirlo.
   * L’interfaccia del gestore di tag è simile a quella di un gestore di contenuti SAX. Riceve eventi SAX per ciascun tag HTML. In qualità di fornitore di gestori di tag, è necessario implementare alcuni metodi lifecycle che vengono automaticamente chiamati dal framework di Importazione progettazione.

1. Crea il tagHandlerFactory corrispondente.

   * L’elemento TagHandlerFactory è un componente OSGi (singleton) responsabile della generazione di istanze del gestore di tag.
   * il gestore di tag factory deve esporre una proprietà OSGi denominata &quot;tagpattern.name&quot; il cui valore viene confrontato con il tag HTML di input.
   * Se esistono più gestori di tag che corrispondono al tag HTML di input, viene scelto quello con una classificazione più alta. La classificazione stessa è esposta come proprietà OSGi **service.ranking**.
   * TagHandlerFactory è un componente OSGi. Eventuali riferimenti che desiderate fornire al gestore di tag devono essere effettuati tramite questa fabbrica.

1. Assicurati che il tuo TagHandlerFactory abbia una classificazione migliore se desideri ignorare il valore predefinito.

## Preparazione di HTML per l’importazione {#preparing-the-html-for-import}

Dopo aver creato una pagina di importazione, puoi importare la pagina di destinazione completa di HTML. Per importare la pagina di destinazione di HTML, è innanzitutto necessario comprimerne il contenuto in un pacchetto di progettazione. Il pacchetto di progettazione contiene la pagina di destinazione di HTML e le risorse a cui si fa riferimento (immagini, css, icone, script e così via).

Il seguente foglio di lavoro fornisce un esempio di come preparare HTML per l’importazione:

Foglio di riferimento della pagina di destinazione

[Ottieni file](assets/cheatsheet.zip)

### Requisiti e layout del file ZIP {#zip-file-layout-and-requirements}

>[!NOTE]
>
>A questo punto, i file ZIP possono contenere solo una pagina HTML o una parte di una pagina.

Esempio di layout del file ZIP:

* /index.html -> file HTML della pagina di destinazione
* /css -> da aggiungere a clientlib CSS
* /img -> tutte le immagini e le risorse
* /js -> da aggiungere a clientlib JS

Il layout si basa sul layout delle best practice di HTML5 Boilerplate. Ulteriori informazioni su [https://html5boilerplate.com/](https://html5boilerplate.com/)

>[!NOTE]
>
>Come minimo, il pacchetto di progettazione **deve** contengono un **index.html** file a livello principale. Se la pagina di destinazione da importare ha anche una versione per dispositivi mobili, il file ZIP deve contenere un **mobile.index.html** insieme a **index.html** a livello principale.

### Preparazione del HTML della pagina di destinazione {#preparing-the-landing-page-html}

Per poter importare HTML, è necessario aggiungere un elemento canvas div alla pagina di destinazione HTML.

L’elemento canvas div è un HTML **div** con `id="cqcanvas"` che devono essere inseriti all&#39;interno della HTML `<body>` e deve racchiudere il contenuto destinato alla conversione.

Uno snippet di esempio di HTML della pagina di destinazione dopo l’aggiunta dell’elemento canvas div è il seguente:

```xml
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
  <meta name="description" content="">
</head>
<body>
 <div id="cqcanvas">
  <!-- HTML content intended for conversion -->
 </div>
</body>
</html>
```

### Preparazione di HTML per l’inclusione di componenti AEM modificabili {#preparing-the-html-to-include-editable-aem-components}

Quando importi una pagina di destinazione, puoi scegliere di importare la pagina così com’è, il che significa che dopo l’importazione della pagina di destinazione non puoi modificare nessuno degli elementi importati in AEM (puoi comunque aggiungere altri componenti AEM sulla pagina).

Prima di importare la pagina di destinazione, potrebbe essere utile convertire alcune parti della pagina di destinazione in modo che siano modificabili AEM componenti. Questo consente di modificare rapidamente alcune parti della pagina di destinazione anche dopo l’importazione della progettazione stessa.

Per eseguire questa operazione, aggiungi la variabile `data-cq-component` al componente appropriato nel file HTML importato.

La sezione seguente descrive come modificare il file HTML in modo da convertire alcune parti delle pagine di destinazione in diversi componenti AEM modificabili. I componenti sono descritti in dettaglio in [Componenti delle pagine di destinazione](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md).

>[!NOTE]
>
>Il markup di HTML per convertire parti della pagina di destinazione in componenti AEM presenta sia una forma lunga che una dichiarazione di tag in formato abbreviato. Per ciascun componente sono descritti entrambi.

### Limitazioni {#limitations}

Prima di importare, tieni presente le seguenti limitazioni:

### Eventuali attributi come class o id applicati al tag &amp;lt;body> non vengono mantenuti {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

Se un attributo come id o class viene applicato, ad esempio, al tag body `<body id="container">` quindi non viene conservato dopo l’importazione. Pertanto, la progettazione da importare non deve avere dipendenze dagli attributi applicati al `<body>` tag .

### Trascina e rilascia la zip {#drag-and-drop-zip}

Il caricamento ZIP tramite trascinamento non è supportato da Internet Explorer e Firefox versione 3.6 e precedenti. Per caricare una progettazione quando si utilizzano questi browser, fai clic sulla zona di rilascio del file per aprire una finestra di dialogo di caricamento del file e caricala utilizzando quella finestra di dialogo.

I browser che supportano il &quot;drag and drop&quot; dello zip di progettazione sono Chrome, Safari5.x, Firefox 4 e versioni successive.

### Modernizr non supportato {#modernizr-is-not-supported}

`Modernizr.js` è uno strumento basato su javascript che rileva le funzionalità native dei browser e rileva se sono o meno adatti per gli elementi html5. Le progettazioni che utilizzano Modernizr per migliorare il supporto nelle versioni precedenti di browser diversi possono causare problemi di importazione nella soluzione della pagina di destinazione. `Modernizr.js` Gli script non sono supportati da Importazione progettazione.

### Le proprietà della pagina non vengono mantenute al momento dell’importazione del pacchetto di progettazione {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

Qualsiasi proprietà di pagina (ad esempio Dominio personalizzato, Applicazione HTTPS, ecc.) impostate per una pagina (che utilizza il modello Pagina di destinazione vuota) prima dell’importazione del pacchetto di progettazione vengono perse dopo l’importazione della progettazione. Pertanto, si consiglia di impostare le proprietà della pagina dopo l’importazione del pacchetto di progettazione.

### Si presume solo il markup di HTML {#html-only-markup-assumed}

Al momento dell’importazione, il markup viene bonificato per motivi di sicurezza e al fine di evitare l’importazione e la pubblicazione di markup non validi. Ciò presuppone che il markup solo per HTML e tutte le altre forme di elementi come SVG in linea o Componenti web vengano filtrati.

### Testo {#text}

Marcatura di HTML per inserire un componente testo ( `foundation/components/text`) in HTML all’interno del pacchetto di progettazione:

```xml
<div data-cq-component="text"> <p>This is some editable text</p> </div>
```

Includendo il markup di cui sopra in HTML, effettua le seguenti operazioni:

* Crea un componente di testo AEM modificabile ( `sling:resourceType=foundation/components/text`) nella pagina di destinazione creata dopo l’importazione del pacchetto di progettazione.
* Imposta la `text` del componente di testo creato al HTML racchiuso all&#39;interno del `div`.

**Dichiarazione abbreviata del tag del componente**:

```xml
<p data-cq-component="text">Text component shorthand</p>
```

**Testo con elenco**

Per aggiungere un testo con un elenco:

* 1st
* 2nd

che può essere modificato nell’editor RTE:

```xml
<div data-cq-component="text"><p>This is text with a list:</p><ul><li>1st</li><li>2nd</li></ul><p>It can be edited with the RTE editor</p></div>
```

**Testo con colore**

Per aggiungere un testo con colore (rosa) modificabile nell’editor RTE:

```xml
<div class="pink" data-cq-component="text"><p>This is pink text.</p><p>It can be edited with the RTE editor</p></div>
```

### Titolo {#title}

Marcatura di HTML per inserire un componente titolo ( `wcm/landingpage/components/title`) in HTML all’interno del pacchetto di progettazione:

```xml
<div data-cq-component="title"> <h1>This is some editable title text</h1> </div>
```

Includendo il markup di cui sopra in HTML, effettua le seguenti operazioni:

* Crea un componente titolo AEM modificabile ( `sling:resourceType=wcm/landingpage/components/title`) nella pagina di destinazione creata dopo l’importazione del pacchetto di progettazione.
* Imposta la `jcr:title` del componente titolo creato al testo all&#39;interno del tag di intestazione racchiuso in div.
* Imposta la `type` al tag di intestazione, in questo caso `h1`.

Il componente titolo supporta 7 tipi: `h1, h2, h3, h4, h5, h6` e `default`.

**Dichiarazione abbreviata del tag del componente**:

```xml
<h1 data-cq-component="title">Title component shorthand</h1>
```

### Immagine {#image}

Marcatura di HTML per inserire un componente immagine (foundation/components/image) in HTML all’interno di un pacchetto di progettazione:

```xml
<div data-cq-component="image">
<img src="img/video1.png" alt="Video about Polar Brake Goggles in action" title="Polar Brake Goggles" width="300" height="200" />
</div>
```

Includendo il markup di cui sopra in HTML, effettua le seguenti operazioni:

* Crea un componente immagine AEM modificabile ( `sling:resourceType=foundation/components/image`) nella pagina di destinazione creata dopo l’importazione del pacchetto di progettazione.
* Imposta la `fileReference` del componente immagine creato sul percorso in cui viene importata l&#39;immagine specificata nell&#39;attributo src.
* Imposta la `alt` sul valore dell&#39;attributo alt nel tag img.
* Imposta la `title` sul valore dell&#39;attributo title nel tag img.
* Imposta la `width` sul valore dell&#39;attributo width nel tag img.
* Imposta la `height` sul valore dell&#39;attributo height nel tag img.

**Dichiarazione abbreviata del tag del componente:**

```xml
<img data-cq-component="image" src="test.png" alt="Image component shorthand"/>
```

#### L’URL assoluto img src non è supportato nel div del componente immagine {#absolute-url-img-src-not-supported-within-image-component-div}

Se `<img>` si tenta di eseguire la conversione del componente con un URL assoluto src, un **UnsupportedTagContentException** viene cresciuto. Ad esempio, quanto segue non è supportato:

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

In caso contrario, le immagini con URL assoluto sono supportate per i tag img che non fanno parte del div del componente immagine.

### Componenti di invito all’azione {#call-to-action-components}

Puoi contrassegnare una parte della pagina di destinazione da importare come &quot;componente Invito all’azione modificabile&quot;. Tali componenti importati da invito all’azione possono essere modificati dopo l’importazione della pagina di destinazione. AEM include i seguenti componenti CTA:

* Collegamento Click-through : consente di aggiungere un collegamento di testo su cui il visitatore può fare clic per passare all’URL di destinazione.
* Collegamento grafico : consente di aggiungere un’immagine su cui il visitatore può fare clic per passare all’URL di destinazione.

#### Collegamento ClickThrough {#click-through-link}

Questo componente CTA può essere utilizzato per aggiungere un collegamento di testo alla pagina di destinazione.

Proprietà supportate

* Etichetta, con opzioni grassetto, corsivo e sottolineato
* URL di destinazione, supporta URL di terze parti e AEM
* Opzioni di rendering della pagina (stessa finestra, nuova finestra, ecc.)

Tag HTML per includere un componente click-through nel file ZIP importato. Qui href viene mappato sull’URL di destinazione, &quot;Visualizza dettagli prodotto&quot; viene mappato sull’etichetta e così via.

```xml
<div id="cqcanvas">
.
.
                <div data-cq-component="clickThroughLink">
        <a href="/content/we-retail/us/en/products/equipment/snow-sports/flying-snowboard.html">View Product Details  ></a>
  </div>
.
.
</div>
```

Questo componente può essere utilizzato in qualsiasi applicazione autonoma o può essere importato da un file ZIP.

**Dichiarazione abbreviata del tag del componente**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### Collegamento grafico {#graphical-link}

Questo componente CTA può essere utilizzato per aggiungere qualsiasi immagine grafica con un collegamento sulla pagina di destinazione. L&#39;immagine può essere un semplice pulsante o un&#39;immagine grafica come sfondo. Quando fai clic sull’immagine, l’utente viene portato all’URL di destinazione specificato nelle proprietà del componente. Fa parte del gruppo &quot;Invito all&#39;azione&quot;.

Proprietà supportate

* Ritaglio immagine, rotazione
* Testo al passaggio del mouse, descrizione, dimensioni in px
* URL di destinazione, supporta URL di terze parti e AEM
* Opzioni di rendering della pagina (stessa finestra, nuova finestra, ecc.)

Tag HTML per includere un componente collegamento grafico nel file ZIP importato. Qui href viene mappato sull’URL di destinazione, img src è l’immagine di rendering, &quot;title&quot; viene preso come testo al passaggio del mouse e così via.

```xml
<div id="cqcanvas">
  <div data-cq-component="clickThroughGraphicalLink"><a href="https://www.adobe.com/go/wem"><img src="img/call-to-action-button.png" title="Click Here to Learn More" /></a></div>
</div>
```

**Dichiarazione abbreviata del tag del componente**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughGraphicalLink"><img src="linkimage.png" alt="Click Through Graphical Link shorthand"/></a>
```

>[!NOTE]
>
>Per creare un collegamento grafico, è necessario racchiudere un tag di ancoraggio e un tag immagine all’interno di un elemento div con `data-cq-component="clickthroughgraphicallink"` attributo.
>
>esempio `<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>Non sono supportati altri modi per associare un’immagine a un tag di ancoraggio utilizzando CSS, ad esempio il markup seguente non funzionerà:
>
>`<div data-cq-component="clickthroughgraphicallink">`
>
>`<a class="hasBackground" href="https://myURLhere/"></a>`
>
>`</div>`
>
>con un `css .hasbackground { background-image: pathtoimage }`

### Modulo lead {#lead-form}

Un modulo lead è un modulo utilizzato per raccogliere le informazioni sul profilo di un visitatore/lead. Queste informazioni possono essere memorizzate e utilizzate in un secondo momento per eseguire un marketing efficace basato sulle informazioni. Queste informazioni includono generalmente titolo, nome, e-mail, data di nascita, indirizzo, interesse e così via. Fa parte del gruppo &quot;Modulo lead CTA&quot;.

**Funzioni supportate**

* Campi per lead predefiniti: nome, cognome, indirizzo, punto di accesso, genere, informazioni, ID utente, ID e-mail, pulsante Invia sono disponibili nella barra laterale. È sufficiente trascinare il componente richiesto nel modulo per lead.
* Con l’aiuto di questi componenti, l’autore può progettare un modulo per lead autonomo, e questi campi corrispondono a campi per moduli per lead. In applicazioni ZIP indipendenti o importate, l’utente può aggiungere altri campi utilizzando i campi modulo per lead cq:form o cta, assegnare un nome e progettarli in base ai requisiti.
* Puoi mappare i campi per moduli lead utilizzando nomi predefiniti specifici per i moduli lead CTA, ad esempio firstName per il nome nel modulo per lead e così via.
* I campi che non sono mappati sul modulo lead vengono mappati su componenti cq:form: testo, radio, casella di controllo, elenco a discesa, nascosto, password.
* L’utente può fornire il titolo utilizzando il tag &quot;label&quot; e lo stile utilizzando l’attributo di stile &quot;class&quot; (disponibile solo per i componenti per modulo lead CTA).
* La pagina di ringraziamento e l’elenco degli abbonamenti possono essere forniti come parametro nascosto del modulo (presente nell’index.htm) oppure possono essere aggiunti/modificati dalla barra di modifica di &quot;Inizio del modulo lead&quot;

   &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot;/>

   &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot;/>

* Vincoli come - possono essere forniti dalla configurazione di modifica di ciascun componente.

Tag HTML per includere un componente collegamento grafico nel file ZIP importato. Qui &quot;firstName&quot; è mappato su firstName del modulo lead e così via, ad eccezione delle caselle di controllo - queste due caselle di controllo vengono mappate sul componente a discesa cq:form.

```xml
<div id="cqcanvas">
   <div id="form_wrapper">
    <h2>NEWSLETTER SIGN UP</h2>
       <div data-cq-component="leadFormGeneration">
       <form method="post" action="#" onsubmit="return popupBox()">
       <label for="firstName" class="checkText">
        FIRST NAME
       </label><br />
       <input name="firstName" class="text pink" type="text" /><br />
       <label for="lastName" class="checkText">
        LAST NAME
       </label><br />
       <input name="lastName" class="text pink" type="text" /><br />
       <label for="emailId" class="checkText">
        EMAIL ADDRESS
       </label><br />
       <input name="emailId" class="text pink" type="text" /><br />

       <div class="checkboxes">
       <input type="checkbox" class="check" name="send_news" /> <label for="send_news" class="checkText">Send me the latest We.Retail news and announcements.</label><br />
       <input type="checkbox" class="check" name="send_offers" /> <label for="send_offers" class="checkText">Send me We.Retail deals and special offers.</label><br />
       </div>
       <input type="submit" name="submit" class="submit pink" value="Sign Up >" />
       </form>
     </div>
   </div>
```

### Parsys {#parsys}

Il componente AEM parsys è un componente contenitore che può contenere altri componenti AEM. È possibile aggiungere un componente parsys in HTML importato. Questo consente all’utente di aggiungere/eliminare componenti AEM modificabili alla pagina di destinazione anche dopo l’importazione.

Il sistema paragrafo consente agli utenti di aggiungere componenti utilizzando la barra laterale.

Marcatura di HTML per inserire un componente parsys ( `foundation/components/parsys`) in HTML all’interno del pacchetto di progettazione:

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

L’inclusione del markup di cui sopra in HTML effettua le seguenti operazioni:

* Inserisce un componente parsys AEM (foundation/components/parsys) nella pagina di destinazione creata dopo l’importazione del pacchetto di progettazione.
* Inizializza la barra laterale con componenti predefiniti. Per aggiungere nuovi componenti alla pagina di destinazione, trascinateli dalla barra laterale al componente parsys.
* Anche due componenti titolo fanno parte del parsys.

### Destinazione {#target}

Il componente Target mostra il contenuto di un’esperienza sulla pagina. È possibile creare più esperienze in una campagna e il componente di destinazione può mostrare in modo dinamico i contenuti di diverse esperienze a vari utenti che visitano la pagina.

Marcatura HTML per inserire un componente di destinazione e anche creare diverse esperienze in una campagna:

```xml
<div data-cq-component="target">
 <section data-cq-component="experience" data-cq-experience="default">
  <p data-cq-component="text">Default content. Select this campaign in client context to view other experiences</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="over-30">
  <p data-cq-component="text">Content for Over 30</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="under-30">
  <p data-cq-component="text">Content for Under 30</p>
 </section>
</div>
```

## Opzioni di importazione aggiuntive {#additional-importing-options}

Oltre a specificare se i componenti importati sono componenti AEM modificabili, puoi anche configurare quanto segue prima di importare il pacchetto di progettazione:

* Impostazione delle proprietà della pagina mediante l’estrazione dei metadati definiti nel HTML importato.
* Specifica della codifica charset in HTML.
* Sovrapposizione del modello di pagina di importazione.

### Impostazione delle proprietà della pagina mediante l’estrazione dei metadati definiti in HTML importato {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

I seguenti metadati dichiarati nella testa del HTML importato vengono estratti e conservati da Importazione progettazione come proprietà &quot;jcr:description&quot;:

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

L’attributo Lang impostato nel tag HTML viene estratto e mantenuto da Importazione progettazione come proprietà &quot;jcr:language&quot;

* &lt;html lang=&quot;en&quot;>

### Specifica della codifica charset nell’html {#specifying-the-charset-encoding-in-the-html}

Importazione progettazione legge la codifica specificata nel HTML importato. La codifica può essere specificata come segue:

`<meta charset="UTF-8">`

*OPPURE*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

Se non viene specificata alcuna codifica in HTML importato, la codifica predefinita impostata da Importazione progettazione è UTF-8.

### Sovrapposizione del modello {#overlaying-template}

Per sovrapporre il modello Pagina di destinazione vuota, createne uno nuovo in: `/apps/<appName>/designimporter/templates/<templateName>`

Vengono descritti i passaggi per la creazione di un nuovo modello in AEM [qui](/help/sites-developing/templates.md).

### Riferimento a un componente dalla pagina di destinazione {#referring-a-component-from-landing-page}

Supponiamo che in HTML sia presente un componente a cui si desidera fare riferimento utilizzando l’attributo data-cq-component in modo che Importazione progettazione esegua il rendering di un componente da includere in questa posizione. Ad esempio, per fare riferimento al componente tabella ( `resourceType = /libs/foundation/components/table`). In HTML è necessario aggiungere quanto segue:

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

Il percorso nel data-cq-component deve essere resourceType del componente.

### Best practice {#best-practices}

L’utilizzo di selettori CSS simili a quelli seguenti non è consigliato per gli elementi contrassegnati per la conversione dei componenti al momento dell’importazione.

| E > F | un elemento F figlio di un elemento E | [Combinatore di bambini](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E + F | un elemento F immediatamente preceduto da un elemento E | [Combinazione di pari livello adiacente](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | un elemento F preceduto da un elemento E | [Combinazione generale di pari livello](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | un elemento E, radice del documento | [pseudoclassi strutturali](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-child(n) | un elemento E, n-esimo figlio del proprio elemento padre | [pseudoclassi strutturali](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | un elemento E, n-esimo figlio del padre, a partire dall’ultimo | [pseudoclassi strutturali](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-of-type(n) | un elemento E, n-esimo elemento di pari livello del suo tipo | [pseudoclassi strutturali](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-of-type(n) | un elemento E, n-esimo elemento di pari livello del suo tipo, a partire dall’ultimo | [pseudoclassi strutturali](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

Ciò è dovuto al fatto che elementi HTML aggiuntivi come &lt;div> vengono aggiunti all’HTML generato dopo l’importazione.

* Si sconsiglia inoltre l’utilizzo di script che si basano su una struttura simile a quella riportata sopra con elementi contrassegnati per la conversione in componenti AEM.
* Utilizzo di stili sui tag di marcatura per la conversione di componenti come &lt;div data-cq-component=&quot;”&amp;ast;”&quot;> non è consigliato.
* Il layout di progettazione deve seguire le best practice di HTML5 Boilerplate. Ulteriori informazioni su: [https://html5boilerplate.com/](https://html5boilerplate.com/).

## Configurazione dei moduli OSGI {#configuring-osgi-modules}

I componenti che espongono le proprietà configurabili tramite la console OSGI sono i seguenti:

* Importazione progettazione pagina di destinazione
* Generatore di pagine di destinazione
* Generatore di pagine di destinazione per dispositivi mobili
* Pre-processore di ingresso pagina di destinazione

La tabella seguente descrive brevemente le proprietà:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Componente</strong></td> 
   <td><strong>Nome proprietà</strong></td> 
   <td><strong>Descrizione proprietà </strong></td> 
  </tr> 
  <tr> 
   <td>Importazione progettazione pagina di destinazione</td> 
   <td>Filtro estrazione</td> 
   <td>Elenco di espressioni regolari da utilizzare per filtrare i file dall’estrazione. <br /> Le voci ZIP che corrispondono a uno dei pattern specificati sono escluse dall’estrazione</td> 
  </tr> 
  <tr> 
   <td>Generatore di pagine di destinazione</td> 
   <td>Pattern file</td> 
   <td>È possibile configurare il Generatore di pagine di destinazione per gestire i file HTML che corrispondono a un’espressione regolare definita dal pattern di file.</td> 
  </tr> 
  <tr> 
   <td>Generatore di pagine di destinazione per dispositivi mobili</td> 
   <td>Pattern file</td> 
   <td>È possibile configurare il Generatore di pagine di destinazione per gestire i file HTML che corrispondono a un’espressione regolare definita dal pattern di file.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Gruppi dispositivo</td> 
   <td>Elenco dei gruppi di dispositivi da supportare.</td> 
  </tr> 
  <tr> 
   <td>Pre-processore di ingresso pagina di destinazione</td> 
   <td>Pattern di ricerca </td> 
   <td>Il pattern da cercare, nel contenuto della voce di archivio. A questa espressione regolare corrisponde la riga del contenuto della voce per riga. Alla corrispondenza, il testo corrispondente viene sostituito con il pattern di sostituzione specificato.<br /> <br /> Vedi la nota seguente relativa alle limitazioni attuali del preprocessore per le voci di pagina di destinazione.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Pattern di sostituzione</td> 
   <td>Pattern che sostituisce le corrispondenze trovate. È possibile utilizzare riferimenti di gruppo regex come $1, $2. Inoltre, questo pattern supporta parole chiave come {designPath} che vengono risolte con il valore effettivo durante l’importazione.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>**Limitazione attuale del preprocessore della pagina di destinazione:**
>Se devi apportare delle modifiche al pattern di ricerca, quando apri l’editor di proprietà felix, devi aggiungere manualmente dei caratteri di barra rovesciata per evitare i metacaratteri regex. Se non si aggiungono manualmente caratteri di barra rovesciata, il regex viene considerato non valido e non sostituirà quello precedente.
>
>Ad esempio, se la configurazione predefinita è
>
>`/\&ast *CQ_DESIGN_PATH *\*/ *(['"])`
>
>E devi sostituire `CQ_DESIGN_PATH` con `VIPURL` nel pattern di ricerca, il pattern di ricerca deve essere simile al seguente:
>
>`/\* *VIPURL *\*/ *(['"])`

## Risoluzione dei problemi {#troubleshooting}

Quando si importa il pacchetto di progettazione, si potrebbero verificare diversi errori, descritti in questa sezione.

### Inizializzazione della barra laterale con componenti relativi alla pagina di destinazione {#initialization-of-sidekick-with-landing-page-relevant-components}

Se il pacchetto di progettazione contiene un markup del componente parsys, dopo l’importazione la barra laterale inizia a mostrare i componenti relativi alla pagina di destinazione. Puoi trascinare nuovi componenti sul componente parsys nella pagina di destinazione. Potete anche passare alla modalità di progettazione e aggiungere nuovi componenti alla barra laterale.

### Messaggi di errore visualizzati durante l’importazione {#error-messages-displayed-during-import}

In caso di errori (ad esempio, se il pacchetto importato non è un file ZIP valido), l’importazione di progettazione non importa il pacchetto e visualizza invece un messaggio di errore sulla pagina appena sopra la casella di trascinamento. Ecco alcuni esempi di scenari di errore. Dopo aver corretto l’errore, puoi reimportare il file ZIP aggiornato nella stessa pagina di destinazione vuota. Diversi scenari in cui vengono generati errori sono i seguenti:

* Il pacchetto di progettazione importato non è un archivio zip valido.
* Il pacchetto di progettazione importato non contiene un file index.html al livello superiore.

### Avvisi visualizzati dopo l’importazione {#warnings-displayed-after-import}

In caso di avvisi (ad esempio, se HTML fa riferimento a immagini che non esistono nel pacchetto), Importazione progettazione importa il file ZIP e visualizza nel contempo un elenco di problemi/avvisi nel riquadro dei risultati. Facendo clic sul collegamento dei problemi, viene visualizzato un elenco di avvisi che segnalano eventuali problemi nel pacchetto di progettazione. Diversi scenari in cui gli avvisi vengono rilevati e visualizzati da Importazione progettazione sono i seguenti:

* HTML fa riferimento a immagini che non esistono nel pacchetto.
* HTML fa riferimento a script che non esistono nel pacchetto.
* HTML fa riferimento a stili che non esistono nel pacchetto.

### Dove sono memorizzati in AEM i file del file ZIP? {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

Dopo l’importazione della pagina di destinazione, i file (immagini, css, js, ecc.) nel pacchetto di progettazione sono memorizzati nel seguente percorso in AEM:

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

Supponiamo che la pagina di destinazione venga creata nella campagna We.Retail e che il nome della pagina di destinazione sia **myBlankLandingPage** il percorso in cui i file Zip vengono memorizzati è il seguente:

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### Formattazione non mantenuta {#formatting-not-preserved}

Durante la creazione del CSS, tieni presente le seguenti limitazioni:

Se un testo e un’immagine (modificabile) sono simili ai seguenti:

```xml
<div class="box">
<p><div data-cq-component="image"><img src="assets/image.jpg" width="115"
height="116" /></div>Some Text </p>
</div>
```

con un CSS applicato alla classe `box` come segue:

```xml
.box

{ width: 450px; padding:10px; border: 1px #C5DBE7 solid; margin: 0px auto 0 auto; background-image:url(assets/box.gif); background-repeat:repeat-x,y; font-family:Verdana, Arial, Helvetica, sans-serif; font-size:12px; color:#6D6D6D; }
```

Then `box img` viene utilizzato in Importazione progettazione, la formattazione della pagina di destinazione risultante non viene mantenuta. Per ovviare a questo problema, AEM aggiunge tag div nel CSS e riscrive il codice di conseguenza. In caso contrario, alcune regole CSS non saranno valide.

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
>
>Inoltre, i designer devono essere consapevoli che solo il codice all’interno del **id=cqcanvas** Il tag viene riconosciuto dall’importazione, altrimenti la progettazione non viene mantenuta.
