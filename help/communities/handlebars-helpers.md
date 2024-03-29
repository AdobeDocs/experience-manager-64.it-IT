---
title: Helper manubrio SCF
seo-title: SCF Handlebars Helpers
description: Metodi Helper per Handlebars per facilitare il lavoro con SCF
seo-description: Handlebars Helper methods to facilitate work with SCF
uuid: 9c514199-871e-4b68-8147-2052d2eeda15
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8b6c1697-d693-41f4-8337-f41658465107
exl-id: 66045e67-4d33-4c0c-81d7-d4287ed68ccc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1550'
ht-degree: 2%

---

# Helper manubrio SCF {#scf-handlebars-helpers}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

| **[⇐ funzioni di base](essentials.md)** | **[Informazioni sulla personalizzazione lato server](server-customize.md)** |
|---|---|
|  | **[Informazioni sulla personalizzazione lato client](client-customize.md)** |

Gli Helper Handlebars (helper) sono metodi richiamabili dagli script Handlebars per facilitare l’utilizzo dei componenti SCF.

L&#39;implementazione include una definizione lato client e lato server. È inoltre possibile per gli sviluppatori creare helper personalizzati.

Gli helper SCF personalizzati forniti con AEM Communities sono definiti nella [libreria client](../../help/sites-developing/clientlibs.md):

* /etc/clientlibs/social/commons/scf/helpers.js

>[!NOTE]
>
>Assicurati di installare il [pacchetto di funzioni per le community più recenti](deploy-communities.md#latestfeaturepack).

## Abbrevia {#abbreviate}

Un helper che restituisce una stringa abbreviata conforme alle proprietà maxWords e maxLength .

La stringa da abbreviare viene fornita come contesto. Se non viene fornito alcun contesto, viene restituita una stringa vuota.

In primo luogo, il contesto viene troncato su maxLength, quindi il contesto viene suddiviso in parole e ridotto a maxWords.

Se safeString è impostato su true, la stringa restituita è SafeString.

### Parametri {#parameters}

* **contesto**: Stringa

   (facoltativo) La stringa predefinita è vuota

* **maxLength**: Numero

   (facoltativo) L&#39;impostazione predefinita è la lunghezza del contesto.

* **maxWords**: Numero

   (facoltativo) Il valore predefinito è il numero di parole nella stringa tagliata.

* **safeString**: Booleano

   (facoltativo) Restituisce un oggetto Handlebars.SafeString() se true. Il valore predefinito è false.

### Esempi {#examples}

```
{{abbreviate subject maxWords=2}}

/*
If subject =
    "AEM Communities - Site Creation Wizard"

Then abbreviate would return
    "AEM Communities".
*/
```

```
{{{abbreviate message safeString=true maxLength=30}}}

/*
If message =
    "The goal of AEM Communities is to quickly create a community engagement site."

Then abbreviate would return
    "The goal of AEM Communities is"
*/
```

## Content-loadmore {#content-loadmore}

Un helper per per aggiungere due pagine sotto un div, una per il testo completo e l’altra per il testo meno, con la possibilità di passare da una visualizzazione all’altra.

### Parametri {#parameters-1}

* **contesto**: Stringa

   (facoltativo) L&#39;impostazione predefinita è la stringa vuota.

* **numChars**: Numero

   (facoltativo) Il numero di caratteri da visualizzare quando non viene visualizzato il testo completo. Il valore predefinito è 100.

* **moreText**: Stringa

   (Facoltativo) Il testo da visualizzare che indica che c&#39;è più testo da visualizzare. Il valore predefinito è &quot;more&quot;.

* **ellissiText**: Stringa

   (Facoltativo) Il testo da visualizzare che indica l’esistenza di testo nascosto. Il valore predefinito è &quot;..&quot;.

* **safeString**: Booleano

   (facoltativo) Valore booleano che indica se applicare o meno Handlebars.SafeString() prima di restituire il risultato. Il valore predefinito è false.

### Esempio {#example}

```
{{content-loadmore  context numChars=32  moreText="go on"  ellipsesText="..." }}

/*
If context = 
    "Here is the initial less content and this is more content."

Then content-loadmore would return
    "Here is the initial less content<span class="moreelipses">...</span> <span class="scf-morecontent"><span>and this is more content.</span>  <a href="" class="scf-morelink" evt="click=toggleContent">go on</a></span>"
*/
```

## DateUtil {#dateutil}

Un helper che restituisce una stringa data formattata.

### Parametri {#parameters-2}

* **contesto**: Numero

   (facoltativo) offset di un valore di millisecondi dal 1° gennaio 1970 (epoch). Il valore predefinito è la data corrente.

* **format**: Stringa

   (facoltativo) Il formato della data da applicare. Il valore predefinito è &quot;YYYY-MM-DDTHH&quot;:mm:ss.sssZ&quot; e il risultato appare come &quot;2015-03-18T18:17:13-07:00&quot;

### Esempi {#examples-1}

```
{{dateUtil this.memberSince format="dd MMM yyyy, hh:mm"}}

// returns "18 Mar 2015, 18:17"
```

```
{{dateUtil this.birthday format="MM-DD-YYYY"}}

// returns "03-18-2015"
```

## Uguale {#equals}

Un helper per per restituire il contenuto in base a una condizione di uguaglianza.

### Parametri {#parameters-3}

* **lvalue**: Stringa

   Valore sinistro da confrontare

* **valore**: Stringa

   Valore a destra da confrontare

### Esempio {#example-1}

```
{{#equals  value "some-value"}}
  <div>They are EQUAL!</div>
{{else}}
  <div>They are NOT equal!</div>
{{/equals}}
```

## Modalità If-wcm {#if-wcm-mode}

Un supporto per blocchi che verifica il valore corrente di [Modalità WCM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) in un elenco di modalità separate da stringa.

### Parametri {#parameters-4}

* **contesto**: Stringa

   (facoltativo) Stringa da tradurre. Obbligatorio se non è stato fornito alcun valore predefinito.

* **modalità**: Stringa

   (facoltativo) Un elenco separato da virgole di [Modalità WCM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) da verificare se impostato.

### Esempio {#example-2}

```xml
{{#if-wcm-mode mode="DESIGN, EDIT"}}
 ...
{{else}}
 ...
{{/if-wcm-mode}}
```

## i18n {#i-n}

Questo helper sostituisce l&#39;helper Handlebars &#39;i18n&#39;.

Vedi anche [Internazionalizzazione delle stringhe nel codice JavaScript](../../help/sites-developing/i18n-dev.md#internationalizing-strings-in-javascript-code).

### Parametri {#parameters-5}

* **contesto**: Stringa

   (facoltativo) Stringa da tradurre. Obbligatorio se non è stato fornito alcun valore predefinito.

* **default**: Stringa

   (Facoltativo) La stringa predefinita da tradurre. Obbligatorio se non viene fornito alcun contesto.

* **commento**: Stringa

   (facoltativo) Un suggerimento di traduzione

### Esempio {#example-3}

```
{{i18n "hello"}}
{{i18n "hello" comment="greeting" default="bonjour"}}
```

## Includi {#include}

Un helper per per includere un componente come risorsa non esistente in un modello.

Questo consente di personalizzare la risorsa in modo programmatico più facilmente di quanto sia possibile per una risorsa aggiunta come nodo JCR. Vedi [Aggiungere o includere un componente Community](scf.md#add-or-include-a-communities-component).

Sono inclusi solo alcuni componenti di Communities. Per AEM 6.1, quelli inclusi sono [commenti](essentials-comments.md), [valutazione](rating-basics.md), [recensioni](reviews-basics.md)e [votazione](essentials-voting.md).

Questo helper, appropriato solo sul lato server, fornisce funzionalità simili a [cq:include](../../help/sites-developing/taglib.md) per gli script JSP.

### Parametri {#parameters-6}

* **contesto**: Stringa o oggetto

   (facoltativo, a meno che non venga fornito un percorso relativo)

   use `this`per passare il contesto corrente

   use `this.id` per ottenere la risorsa in `id` per il rendering del resourceType richiesto

* **resourceType**: Stringa

   (facoltativo) per impostazione predefinita il tipo di risorsa viene impostato sul tipo di risorsa dal contesto

* **template**: Stringa

   percorso dello script componente

* **path**: Stringa

   (obbligatorio) Il percorso della risorsa. Se il percorso è relativo, è necessario fornire un contesto, altrimenti viene restituita la stringa vuota.

* **authoringDisabled**: Booleano

   (facoltativo) L&#39;impostazione predefinita è false. Solo per uso interno.

### Esempio {#example-4}

```
{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}
```

Questo include un nuovo componente Commenti in `this.id` + /commenti

## IncludeClientLib {#includeclientlib}

Un helper che include una libreria client HTML AEM, che può essere un js, un css o una libreria di temi. Per più inclusioni di tipi diversi, ad esempio js e css, questo tag deve essere utilizzato più volte nello script Handlebars.

Questo helper, appropriato solo sul lato server, fornisce funzionalità simili a [ui:includeClientLib](../../help/sites-developing/taglib.md) per gli script JSP.

### Parametri {#parameters-7}

* **categorie**: Stringa

   (facoltativo) Elenco di categorie di librerie client separate da virgola. Questo includerà tutte le librerie JavaScript e CSS per le categorie specificate. Il nome del tema viene estratto dalla richiesta.

* **tema**: Stringa

   (facoltativo) Elenco di categorie di librerie client separate da virgola. Questo includerà tutte le librerie correlate al tema (sia CSS che JS) per le categorie specificate. Il nome del tema viene estratto dalla richiesta.

* **js**: Stringa

   (facoltativo) Elenco di categorie di librerie client separate da virgola. Questo includerà tutte le librerie JavaScript per le categorie specificate.

* **css**: Stringa

   (facoltativo) Elenco di categorie di librerie client separate da virgola. Questo includerà tutte le librerie CSS per le categorie specificate.

### Esempi {#examples-2}

```
// all: js + theme (theme-js + css) 
{{includeClientLib categories="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/socialgraph.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/socialgraph.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// only js libs
{{includeClientLib js="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/socialgraph.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// theme only (theme-js + css) 
{{includeClientLib theme="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// css only
{{includeClientLib css="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/socialgraph.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
```

## Tempo utile {#pretty-time}

Un helper per per visualizzare il tempo trascorso fino a un punto di interruzione, dopo di che viene visualizzato un formato di data regolare.

Ad esempio:

* 12 ore fa
* 7 giorni fa

### Parametri {#parameters-8}

* **contesto**: Numero

   Un&#39;epoca in passato da paragonare a &quot;ora&quot;. Il tempo è espresso come valore in millisecondi offset dal 1 gennaio 1970 (epoch).

* **daysCutoff**: Numero

   Il numero di giorni fa prima del passaggio a una data effettiva. Il valore predefinito è 60.

### Esempio {#example-5}

```
{{pretty-time this.published daysCutoff=7}}

/*
Depending on how long in the past, may return
  
  "3 minutes ago"

  "3 hours ago"

  "3 days ago"
*/
```

## Xss-html {#xss-html}

Helper che codifica una stringa sorgente per il contenuto dell’elemento HTML per proteggerlo da XSS.

NOTA: questo non è un validatore e non deve essere utilizzato per scrivere i valori degli attributi.

### Parametri {#parameters-9}

* **contesto**: oggetto

   il HTML da codificare

### Esempio {#example-6}

```
<p>{{xss-html forum-ugc}}</p>
```

## Xss-htmlAttr {#xss-htmlattr}

Un helper che codifica una stringa di origine per la scrittura in un valore di attributo di HTML per proteggere XSS.

NOTA: non si tratta di un validatore e non deve essere utilizzato per la scrittura di attributi actionable (href, src, gestori eventi).

### Parametri {#parameters-10}

* **contesto**: Oggetto

   HTML da codificare

### Esempio {#example-7}

```
<div id={{xss-htmlAttr id}} />
```

## Xss-jsString {#xss-jsstring}

Un helper che codifica una stringa di origine per la scrittura nel contenuto della stringa JavaScript per proteggerlo da XSS.

NOTA: questo non è un validatore e non deve essere utilizzato per scrivere in JavaScript arbitrario.

### Parametri {#parameters-11}

* **contesto**: Oggetto

   HTML da codificare

### Esempio {#example-8}

```
var input = {{xss-jsString topic-title}}
```

## Xss-validHref {#xss-validhref}

Un helper che igienizza un URL per la scrittura come valore di attributo HTML href o srce per proteggere XSS.

NOTA: potrebbe restituire una stringa vuota

### Parametri {#parameters-12}

* **contesto**: Oggetto

   URL da bonificare

### Esempio {#example-9}

```
<a href="{{xss-validHref url}}">my link</a>
```

## Panoramica di base di Handlebars.js {#handlebars-js-basic-overview}

* Una chiamata dell&#39;helper Handlebars è un identificatore semplice (il *nome *dell&#39;helper), seguito da zero o più parametri separati dallo spazio.
* I parametri possono essere un semplice oggetto String, number, boolean o JSON, oltre a una sequenza facoltativa di coppie chiave-valore (argomenti hash) come ultimo parametro/i.
* Le chiavi negli argomenti hash devono essere identificatori semplici.
* I valori negli argomenti hash sono espressioni Handlebars: identificatori semplici, percorsi o stringhe.
* Il contesto attuale, `this`, è sempre disponibile per gli helper Handlebars.
* Il contesto può essere un oggetto dati String, number, boolean o JSON.
* È possibile passare un oggetto nidificato nel contesto corrente come contesto, ad esempio `this.url` o `this.id` (vedere i seguenti esempi di aiutanti semplici e a blocchi).

* Gli helper a blocchi sono funzioni che possono essere richiamate da qualsiasi punto del modello. Possono richiamare ogni volta un blocco del modello zero o più volte con un contesto diverso. Contengono un contesto tra {{#*name*}} and {{/*name*}}.

* Handlebars fornisce un parametro finale agli helper denominati &quot;options&quot;. L&#39;oggetto speciale &quot;options&quot; include

   * Dati privati opzionali (options.data)
   * Proprietà chiave-valore facoltative dalla chiamata (options.hash)
   * Possibilità di richiamarsi (options.fn())
   * Possibilità di richiamare l&#39;inverso di se stesso (options.inverse())

* È consigliabile che il contenuto di HTML String restituito da un helper sia SafeString.

### Esempio di un semplice helper dalla documentazione di Handlebars.js : {#an-example-of-a-simple-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link_to', function(title, options) {
    return new Handlebars.SafeString('<a href="/posts' + this.url + '">' + title + "!</a>");
});

var context = {posts: [
    {url: "/hello-world",
      body: "Hello World!"}
  ] };

// when link_to is called, posts is the current context
var source = '<ul>{{#posts}}<li>{{{link_to "Post"}}}</li>{{/posts}}</ul>'

var template = Handlebars.compile(source);

template(context);
```

Rendering:

&lt;ul>\
&lt;li>&lt;a href=&quot;/posts/hello-world&quot;>Post!&lt;/a>&lt;/li>\
&lt;/ul>

### Esempio di un helper per per blocchi nella documentazione di Handlebars.js : {#an-example-of-a-block-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link', function(options) {
    return new Handlebars.SafeString('<a href="/people/' + this.id + '">' + options.fn(this) + '</a>');
});

var data = { "people": [
  { "name": "Alan", "id": 1 },
  { "name": "Yehuda", "id": 2 }
]};

// when link is called, people is the current context
var source = "<ul>{{#people}}<li>{{#link}}{{name}}{{/link}}</li>{{/people}}</ul>";

var template = Handlebars.compile(source);

template(data);
```

Rendering:\
&lt;ul>\
&lt;li>&lt;a href=&quot;/people/1&quot;>Alan&lt;/a>&lt;/li>\
&lt;li>&lt;a href=&quot;/people/2&quot;>Yehuda&lt;/a>&lt;/li>\
&lt;/ul>

## Helper SCF personalizzati {#custom-scf-helpers}

Gli helper personalizzati devono essere implementati sia sul lato server che sul lato client, soprattutto quando si trasmettono i dati. Per SCF, la maggior parte dei modelli viene compilata e sottoposta a rendering sul lato server, in quanto il server genera HTML per un determinato componente quando la pagina viene richiesta.

### Helper personalizzati lato server {#server-side-custom-helpers}

Per implementare e registrare un helper SCF personalizzato sul lato server, è sufficiente implementare l’interfaccia Java [TemplateHelper](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/handlebars/api/TemplateHelper.html), rendilo un [Servizio OSGi](../../help/sites-developing/the-basics.md#osgi) e installalo come parte di un bundle OSGi.

Ad esempio:

### FooTextHelper.java {#footexthelper-java}

```java
/** Custom Handlebars Helper */

package com.my.helpers;

import java.io.IOException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

import com.adobe.cq.social.handlebars.api.TemplateHelper;
import com.github.jknack.handlebars.Options;

@Service
@Component
public class FooTextHelper implements TemplateHelper<String>{

    @Override
    public CharSequence apply(String context, Options options) throws IOException {
        return "foo-" + context;
    }

    @Override
    public String getHelperName() {
        return "foo-text";
    }

    @Override
    public Class<String> getContextType() {
        return String.class;
    }
}
```

>[!NOTE]
>
>È necessario creare un helper creato per il lato server anche per il lato client.
>
>Il componente viene riprodotto sul lato client per l’utente connesso e, se l’helper lato client non viene trovato, il componente scompare.

### Helper personalizzati lato client {#client-side-custom-helpers}

Gli helper lato client sono script Handlebars registrati richiamando `Handlebars.registerHelper()`.\
Ad esempio:

### custom-helpers.js {#custom-helpers-js}

```
function(Handlebars, SCF, $CQ) {

    Handlebars.registerHelper('foo-text', function(context, options) {
        if (!context) {
            return "";
        }
        return "foo-" + context;
    });

})(Handlebars, SCF, $CQ);
```

Gli helper personalizzati lato client devono essere aggiunti a una libreria client personalizzata.\
La clientlib deve:

* Includi una dipendenza in `cq.social.scf`
* Carica dopo il caricamento di Handlebars
* Essere [incluso](clientlibs.md)

Nota: gli assistenti SCF sono definiti in `/etc/clientlibs/social/commons/scf/helpers.js`.

| **[⇐ funzioni di base](essentials.md)** | **[Informazioni sulla personalizzazione lato server](server-customize.md)** |
|---|---|
|  | **[Informazioni sulla personalizzazione lato client](client-customize.md)** |
