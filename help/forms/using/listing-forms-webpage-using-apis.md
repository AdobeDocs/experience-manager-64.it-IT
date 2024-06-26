---
title: Inserimento di moduli in una pagina web tramite API
seo-title: Listing forms on a web page using APIs
description: Eseguire una query programmatica su Forms Manager per recuperare un elenco filtrato di moduli e visualizzarlo sulle proprie pagine web.
seo-description: Programmatically query Forms Manager to retrieve a filtered list of forms and display on your own web pages.
uuid: e51cb2d4-816f-4e6d-a081-51e4999b00ba
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 515ceaf6-c132-4e1a-b3c6-5d2c1ccffa7c
exl-id: e42b7cdf-9a70-4ff6-8283-7bbc3690ca05
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 2%

---

# Inserimento di moduli in una pagina web tramite API {#listing-forms-on-a-web-page-using-apis}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Forms fornisce un’API di ricerca basata su REST che gli sviluppatori web possono utilizzare per eseguire query e recuperare un set di moduli che soddisfa i criteri di ricerca. È possibile utilizzare le API per cercare moduli basati su vari filtri. L&#39;oggetto response contiene gli attributi del modulo, le proprietà ed il rendering dei punti finali dei moduli.

Per cercare i moduli utilizzando l’API REST, invia una richiesta GET al server all’indirizzo `https://[server]:[port]/libs/fd/fm/content/manage.json` con i parametri di query descritti di seguito.

## Parametri query {#query-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Nome attributo<br /> </strong></td>
   <td><strong>Descrizione<br /> </strong></td>
  </tr>
  <tr>
   <td>func<br /> </td>
   <td><p>Specifica la funzione da chiamare. Per eseguire la ricerca nei moduli, impostare il valore di <code>func </code>attributo a <code>searchForms</code>.</p> <p>Ad esempio: <code class="code">
       URLParameterBuilder entityBuilder=new URLParameterBuilder ();
       entityBuilder.add("func", "searchForms");</code></p> <p><strong>Nota:</strong> <em>Questo parametro è obbligatorio.</em><br /> </p> </td>
  </tr>
  <tr>
   <td>appPath<br /> </td>
   <td><p>Specifica il percorso dell'applicazione per la ricerca dei moduli. Per impostazione predefinita, l'attributo appPath esegue la ricerca in tutte le applicazioni disponibili a livello di nodo principale.<br /> </p> <p>È possibile specificare più percorsi applicativi in una singola query di ricerca. Separa più percorsi con il carattere barra verticale (|). </p> </td>
  </tr>
  <tr>
   <td>cutPoints<br /> </td>
   <td><p>Specifica le proprietà da recuperare con le risorse. Puoi utilizzare un asterisco (*) per recuperare tutte le proprietà contemporaneamente. Utilizzare l'operatore pipe (|) per specificare più proprietà. </p> <p>Ad esempio: <code>cutPoints=propertyName1|propertyName2|propertyName3</code></p> <p><strong>Nota</strong>: </p>
    <ul>
     <li><em>Le proprietà quali id, percorso e nome vengono sempre recuperate. </em></li>
     <li><em>Ogni risorsa ha un set di proprietà diverso. Le proprietà come formUrl, pdfUrl e guideUrl non dipendono dall'attributo cutpoints. Queste proprietà dipendono dal tipo di risorsa e vengono recuperate di conseguenza. </em></li>
    </ul> </td>
  </tr>
  <tr>
   <td>relation<br /> </td>
   <td>Specifica le risorse correlate da recuperare insieme ai risultati della ricerca. Per recuperare le risorse correlate, puoi scegliere una delle seguenti opzioni:
    <ul>
     <li><strong>NO_RELATION</strong>: Non recuperare le risorse correlate.</li>
     <li><strong>IMMEDIATO</strong>: Recupera le risorse direttamente correlate ai risultati della ricerca.</li>
     <li><strong>TUTTO</strong>: Recupera risorse correlate direttamente e indirettamente.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>maxSize</td>
   <td>Specifica il numero massimo di moduli da recuperare.</td>
  </tr>
  <tr>
   <td>offset</td>
   <td>Specifica il numero di moduli da ignorare dall’inizio.</td>
  </tr>
  <tr>
   <td>returnCount</td>
   <td>Specifica se restituire o meno i risultati della ricerca corrispondenti ai criteri specificati. </td>
  </tr>
  <tr>
   <td>dichiarazioni</td>
   <td><p>Specifica l’elenco delle istruzioni. Le query vengono eseguite nell’elenco delle istruzioni specificate nel formato JSON. </p> <p>Ad esempio:</p> <p><code class="code">JSONArray statementArray=new JSONArray();
       JSONObject statement=new JSONObject();
       statement.put("name", "title");
       statement.put("value", "SimpleSurveyAF");
       statement.put("operator", "EQ"); statementArray.put(statement);</code></p> <p>Nell’esempio precedente, </p>
    <ul>
     <li><strong>name</strong>: specifica il nome della proprietà da cercare.</li>
     <li><strong>value</strong>: specifica il valore della proprietà da cercare.</li>
     <li><strong>operatore</strong>: specifica l'operatore da applicare durante la ricerca. Sono supportati i seguenti operatori:
      <ul>
       <li>EQ - Uguale a </li>
       <li>NEQ - Non uguale a</li>
       <li>GT - Maggiore di</li>
       <li>LT - Minore di</li>
       <li>GTEQ - Maggiore o uguale a</li>
       <li>LTEQ - Minore o uguale a</li>
       <li>CONTIENE - A contiene B se B fa parte di A</li>
       <li>FULLTEXT - Ricerca full-text</li>
       <li>STARTSWITH - A inizia con B se B è la parte iniziale di A</li>
       <li>ENDSWITH - A termina con B se B è la parte finale di A</li>
       <li>LIKE - Implementa l'operatore LIKE</li>
       <li>AND - Combinare più istruzioni</li>
      </ul> <p><strong>Nota:</strong> <em>Gli operatori GT, LT, GTEQ e LTEQ sono applicabili per proprietà di tipo lineare quali LONG, DOUBLE e DATE.</em></p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>ordinanza<br /> </td>
   <td><p>Specifica i criteri dell'ordine per i risultati della ricerca. I criteri sono definiti nel formato JSON. È possibile ordinare i risultati della ricerca in più campi. I risultati vengono ordinati nell’ordine in cui vengono visualizzati i campi nella query.</p> <p>Ad esempio:</p> <p>Per recuperare i risultati della query ordinati dalla proprietà title nell'ordine crescente, aggiungi il seguente parametro: </p> <p><code class="code">JSONArray orderingsArray=new JSONArray();
       JSONObject orderings=new JSONObject();
       orderings.put("name", "title");
       orderings.put("criteria", "ASC");
       orderingsArray.put(orderings);
       entityBuilder.add("orderings", orderingsArray.toString());</code></p>
    <ul>
     <li><strong>name</strong>: Specifica il nome della proprietà da utilizzare per ordinare i risultati della ricerca.</li>
     <li><strong>criteri</strong>: Specifica l'ordine dei risultati. L'attributo order accetta i seguenti valori:
      <ul>
       <li>ASC: utilizza ASC per disporre i risultati in ordine crescente.<br /> </li>
       <li>DES - Utilizza DES per disporre i risultati in ordine decrescente.</li>
      </ul> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>includeXdp</td>
   <td>Specifica se recuperare o meno il contenuto binario. La <code>includeXdp</code> attributo applicabile alle attività di tipo <code>FORM</code>, <code>PDFFORM</code>e <code>PRINTFORM</code>.</td>
  </tr>
  <tr>
   <td>assetType</td>
   <td>Specifica i tipi di risorse da recuperare da tutte le risorse pubblicate. Utilizza l’operatore pipe (|) per specificare più tipi di risorse. I tipi di risorse validi sono FORM, PDFFORM, PRINTFORM, RESOURCE e GUIDE.</td>
  </tr>
 </tbody>
</table>

## Richiesta di esempio {#sample-request}

```
func : searchForms
appPath : /content/dam/formsanddocuments/MyApplication23
cutPoints : title|description|author|status|creationDate|lastModifiedDate|activationDate|expiryDate|tags|allowedRenderFormat|formmodel
relation : NO_RELATION
includeXdp : false
maxSize : 10
offset : 0
returnCount : true
statements: [{"name":"name","value":"*Claim.xdp","operator":"CONTAINS"},
                {"name":"","value":"Expense","operator":"FULLTEXT"},
                {"name":"description","value":"ABCD*","operator":"CONTAINS"},
                {"name":"status","value":"false","operator":"EQ"},
                {"name":"lastModifiedDate","value":"01/09/2013","operator":"GTEQ"},
                {"name":"lastModifiedDate","value":"01/18/2013","operator":"LTEQ"}]
orderings:[{"name" :“lastModifiedDate“:”order”:”ASC”}]
```

## Risposta di esempio {#sample-response}

```
[
{"resultCount":2},
    {"assetType":"FORM","name":"ExpenseClaim.xdp","id":"509fa2d5-e3c9-407b-b8dc-fa0ba08eb0ce",
       "path":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp",
       "title":"Expense Report","description":"ABCDEFGIJK","author":"Frank Bowman",
       "tags":[],"formUrl":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp/jcr:content",
       "pdfUrl":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp/jcr:content?type=pdf",
       "references":[],"images":[{"assetType":"resource","name":"Image.gif","id":"5477a127-8bbf-4cec-8f81-2689e5cb4a15",
       "path":"/content/dam/formsanddocuments/MyApplication23/1.0/Image.gif","resourceSize":0}],
       "status":false,"creationDate":1358429845623,"lastModifiedDate":1358429846771},
{"assetType":"FORM","name":"ExpenseClaim.xdp","id":"4312239b-b666-4d36-95bc-641b3a39ddd4",
       "path":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp",
       "title":"Expense Report","description":"ABCDefghijklm","author":"Frank Bowman",
       "tags":[],"formUrl":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp/jcr:content",
       "pdfUrl":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp/jcr:content?type=pdf",
       "references":[],"images":[{"assetType":"resource","name":"Image.gif","id":"118a2e3f-7097-4d8c-85d1-651306de284a",
       "path":"/content/dam/formsanddocuments/MyApplication23/Image.gif","resourceSize":0}],"status":false,
       "creationDate":1358429856690,"lastModifiedDate":1358430109023}
]
```

## Articoli correlati

* [Abilitare i componenti del portale moduli](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina del portale dei moduli](/help/forms/using/creating-form-portal-page.md)
* [Elencare moduli in una pagina web utilizzando le API](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Usa componente Bozze e invii](/help/forms/using/draft-submission-component.md)
* [Personalizzare l’archiviazione delle bozze e dei moduli inviati](/help/forms/using/draft-submission-component.md)
* [Esempio per l&#39;integrazione del componente bozze e invii con il database](/help/forms/using/integrate-draft-submission-database.md)
* [Personalizzazione dei modelli per i componenti del portale dei moduli](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Introduzione alla pubblicazione di moduli su un portale](/help/forms/using/introduction-publishing-forms.md)
