---
title: Creazione di moduli adattivi tramite lo schema JSON
seo-title: Creazione di moduli adattivi tramite lo schema JSON
description: 'I moduli adattivi possono utilizzare lo schema JSON come modello di modulo, consentendo di sfruttare gli schemi JSON esistenti per creare moduli adattivi. '
seo-description: 'I moduli adattivi possono utilizzare lo schema JSON come modello di modulo, consentendo di sfruttare gli schemi JSON esistenti per creare moduli adattivi. '
uuid: e73b4b4c-6ad7-4400-b776-5892549970c3
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcda96ff-6c7d-46c4-a9e8-7e0fb245cde9
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 4%

---


# Creazione di moduli adattivi tramite lo schema JSON {#creating-adaptive-forms-using-json-schema}

## Prerequisiti {#prerequisites}

Per creare un modulo adattivo utilizzando uno schema JSON come modello di modulo, è necessario conoscere di base lo schema JSON. Prima di questo articolo, è consigliabile consultare il contenuto seguente.

* [Creazione di un modulo adattivo](/help/forms/using/creating-adaptive-form.md)
* [Schema JSON](https://json-schema.org/)

## Utilizzo di uno schema JSON come modello di modulo {#using-a-json-schema-as-form-model}

AEM Forms supporta la creazione di un modulo adattivo utilizzando uno schema JSON esistente come modello di modulo. Questo schema JSON rappresenta la struttura in cui i dati vengono prodotti o utilizzati dal sistema back-end della tua organizzazione. Lo schema JSON utilizzato deve essere conforme alle [specifiche v4](https://json-schema.org/draft-04/schema).

Le caratteristiche principali dell’utilizzo di uno schema JSON sono le seguenti:

* La struttura del JSON viene visualizzata come una struttura nella scheda Content Finder nella modalità di creazione per un modulo adattivo. Puoi trascinare e aggiungere un elemento dalla gerarchia JSON al modulo adattivo.
* È possibile precompilare il modulo utilizzando JSON conforme allo schema associato.
* Al momento dell’invio, i dati immessi dall’utente vengono inviati come JSON in linea con lo schema associato.

Uno schema JSON è costituito da tipi di elementi semplici e complessi. Gli elementi dispongono di attributi che aggiungono regole all’elemento. Quando questi elementi e attributi vengono trascinati in un modulo adattivo, vengono mappati automaticamente sul componente del modulo adattivo corrispondente.

Questa mappatura degli elementi JSON con componenti per moduli adattivi è la seguente:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Elemento, proprietà o attributi JSON</strong></th> 
   <th><strong>Componente per moduli adattivi</strong></th> 
  </tr> 
  <tr> 
   <td><p>Proprietà stringa con vincolo enum e enumNames.</p> <p>Sintassi,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td><p>Componente a discesa:</p> 
    <ul> 
     <li>I valori elencati in enumNames vengono visualizzati nella casella a discesa.</li> 
     <li>I valori elencati nell'enum sono utilizzati per il calcolo.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Proprietà stringa con vincolo di formato. Ad esempio, e-mail e data.</p> <p>Sintassi,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td> 
   <td> 
    <ul> 
     <li>Il componente E-mail viene mappato quando il tipo è stringa e il formato è e-mail.</li> 
     <li>Il componente Textbox con convalida viene mappato quando il tipo è stringa e il formato è hostname.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>{</p> <p>"type" : "string",</p> <p>}</p> </td> 
   <td><br /> <br /> Campo di testo<br /> <br /> <br /> </td> 
  </tr> 
  <tr> 
   <td>number property<br /> </td> 
   <td>Campo numerico con sottotipo impostato su mobile<br /> </td> 
  </tr> 
  <tr> 
   <td>proprietà integer<br /> </td> 
   <td>Campo numerico con sottotipo impostato su integer<br /> </td> 
  </tr> 
  <tr> 
   <td>proprietà booleana<br /> </td> 
   <td>Scambia<br /> </td> 
  </tr> 
  <tr> 
   <td>proprietà oggetto<br /> </td> 
   <td>Pannello<br /> </td> 
  </tr> 
  <tr> 
   <td>proprietà array</td> 
   <td>Pannello ripetibile con minimo e massimo uguale rispettivamente a minItems e maxItems. Sono supportati solo gli array omogenei. Pertanto, il vincolo elementi deve essere un oggetto e non un array.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Proprietà comuni dello schema {#common-schema-properties}

Il modulo adattivo utilizza le informazioni disponibili nello schema JSON per mappare ogni campo generato. In particolare:

* La proprietà title funge da etichetta per i componenti del modulo adattivo.
* La proprietà description viene impostata come descrizione lunga per un componente modulo adattivo.
* La proprietà predefinita funge da valore iniziale di un campo modulo adattivo.
* La proprietà maxLength è impostata come attributo maxlength del componente campo di testo.
* Le proprietà minimum, maximum, esclusiveMinimum e esclusiveMaximum vengono utilizzate per il componente Casella numerica .
* Per supportare l’intervallo per il componente DatePicker, vengono fornite ulteriori proprietà dello schema JSON, tra cui minDate e maxDate.
* Le proprietà minItems e maxItems vengono utilizzate per limitare il numero di elementi/campi che possono essere aggiunti o rimossi da un componente del pannello.
* La proprietà readOnly imposta l&#39;attributo readonly di un componente di modulo adattivo.
* La proprietà obbligatoria contrassegna il campo modulo adattivo come obbligatorio, mentre nel caso del pannello (in cui il tipo è l’oggetto), i dati JSON inviati finali hanno campi con valore vuoto corrispondente a tale oggetto.
* La proprietà pattern viene impostata come pattern di convalida (espressione regolare) in forma adattiva.
* L’estensione del file di schema JSON deve essere mantenuta .schema.json. Ad esempio, &lt;filename>.schema.json.

## Schema JSON di esempio {#sample-json-schema}

Ecco un esempio di uno schema JSON.

```
{
 "$schema": "https://json-schema.org/draft-04/schema#",
 "definitions": {
  "employee": {
   "type": "object",
   "properties": {
    "userName": {
     "type": "string"
    },
    "dateOfBirth": {
     "type": "string",
     "format": "date"
    },
    "email": {
     "type": "string",
     "format": "email"
    },
    "language": {
     "type": "string"
    },
    "personalDetails": {
     "$ref": "#/definitions/personalDetails"
    },
    "projectDetails": {
     "$ref": "#/definitions/projectDetails"
    }
   },
   "required": [
    "userName",
    "dateOfBirth",
    "language"
   ]
  },
  "personalDetails": {
   "type": "object",
   "properties": {
    "GeneralDetails": {
     "$ref": "#/definitions/GeneralDetails"
    },
    "Family": {
     "$ref": "#/definitions/Family"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "projectDetails": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projects": {
      "$ref": "#/definitions/projects"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projects": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projectsAdditional": {
      "$ref": "#/definitions/projectsAdditional"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projectsAdditional": {
   "type": "array",
   "items": {
    "properties": {
     "Additional_name": {
      "type": "string"
     },
     "Additional_areacode": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "GeneralDetails": {
   "type": "object",
   "properties": {
    "age": {
     "type": "number"
    },
    "married": {
     "type": "boolean"
    },
    "phone": {
     "type": "number",
     "aem:afProperties": {
      "sling:resourceType": "/libs/fd/af/components/guidetelephone",
      "guideNodeClass": "guideTelephone"
     }
    },
    "address": {
     "type": "string"
    }
   }
  },
  "Family": {
   "type": "object",
   "properties": {
    "spouse": {
     "$ref": "#/definitions/spouse"
    },
    "kids": {
     "$ref": "#/definitions/kids"
    }
   }
  },
  "Income": {
   "type": "object",
   "properties": {
    "monthly": {
     "type": "number"
    },
    "yearly": {
     "type": "number"
    }
   }
  },
  "spouse": {
   "type": "object",
   "properties": {
    "name": {
     "type": "string"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "kids": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  }
 },
 "type": "object",
 "properties": {
  "employee": {
   "$ref": "#/definitions/employee"
  }
 }
}
```

### Definizioni dello schema riutilizzabili {#reusable-schema-definitions}

Le chiavi di definizione vengono utilizzate per identificare gli schemi riutilizzabili. Le definizioni dello schema riutilizzabile vengono utilizzate per creare i frammenti. È simile all&#39;identificazione di tipi complessi in XSD. Di seguito è riportato un esempio di schema JSON con definizioni:

```
{
  "$schema": "https://json-schema.org/draft-04/schema#",
 
  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },
 
  "type": "object",
 
  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

L&#39;esempio precedente definisce un record cliente, in cui ogni cliente ha sia un indirizzo di spedizione che un indirizzo di fatturazione. La struttura di entrambi gli indirizzi è la stessa - gli indirizzi hanno un indirizzo di strada, una città e uno stato - quindi è una buona idea non duplicare gli indirizzi. Permette inoltre di aggiungere ed eliminare facilmente i campi per eventuali modifiche future.

## Preconfigurazione dei campi nella definizione dello schema JSON {#pre-configuring-fields-in-json-schema-definition}

Puoi utilizzare la proprietà **aem:afProperties** per preconfigurare il campo Schema JSON per la mappatura su un componente modulo adattivo personalizzato. Di seguito è riportato un esempio:

```
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

## Limitare i valori accettabili per un componente modulo adattivo {#limit-acceptable-values-for-an-adaptive-form-component}

Puoi aggiungere le seguenti restrizioni agli elementi dello schema JSON per limitare i valori accettabili per un componente modulo adattivo:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Proprietà schema</strong></p> </td> 
   <td><p><strong>Tipo di dati</strong></p> </td> 
   <td><p><strong>Descrizione</strong></p> </td> 
   <td><p><strong>Componente</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><code>maximum</code></p> </td> 
   <td><p>Stringa</p> </td> 
   <td><p>Specifica il limite superiore per i valori numerici e le date. Per impostazione predefinita, è incluso il valore massimo.</p> </td> 
   <td> 
    <ul> 
     <li>Casella numerica</li> 
     <li>Stepper numerico<br /> </li> 
     <li>Selettore data</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minimum</code></p> </td> 
   <td><p>Stringa</p> </td> 
   <td><p>Specifica il limite inferiore per i valori numerici e le date. Per impostazione predefinita, è incluso il valore minimo.</p> </td> 
   <td> 
    <ul> 
     <li>Casella numerica</li> 
     <li>Stepper numerico</li> 
     <li>Selettore data</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMaximum</code></p> </td> 
   <td><p>Booleano</p> </td> 
   <td><p>Se true, il valore numerico o la data specificati nel componente del modulo devono essere inferiori al valore numerico o alla data specificati per la proprietà maximum.</p> <p>Se false, il valore numerico o la data specificati nel componente del modulo deve essere minore o uguale al valore numerico o alla data specificata per la proprietà maximum.</p> </td> 
   <td> 
    <ul> 
     <li>Casella numerica</li> 
     <li>Stepper numerico</li> 
     <li>Selettore data</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>exclusiveMinimum</code></p> </td> 
   <td><p>Booleano</p> </td> 
   <td><p>Se true, il valore numerico o la data specificati nel componente del modulo devono essere maggiori del valore numerico o della data specificati per la proprietà minima.</p> <p>Se false, il valore numerico o la data specificati nel componente del modulo devono essere maggiori o uguali al valore numerico o alla data specificata per la proprietà minima.</p> </td> 
   <td> 
    <ul> 
     <li>Casella numerica</li> 
     <li>Stepper numerico</li> 
     <li>Selettore data</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>minLength</code></p> </td> 
   <td><p>Stringa</p> </td> 
   <td><p>Specifica il numero minimo di caratteri consentiti in un componente. La lunghezza minima deve essere uguale o maggiore di zero.</p> </td> 
   <td> 
    <ul> 
     <li>Casella di testo</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>maxLength</code></td> 
   <td>Stringa</td> 
   <td>Specifica il numero massimo di caratteri consentiti in un componente. La lunghezza massima deve essere uguale o maggiore di zero.</td> 
   <td> 
    <ul> 
     <li>Casella di testo</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>pattern</code></p> </td> 
   <td><p>Stringa</p> </td> 
   <td><p>Specifica la sequenza dei caratteri. Un componente accetta i caratteri se questi sono conformi al pattern specificato.</p> <p>La proprietà pattern è associata al pattern di convalida del componente modulo adattivo corrispondente.</p> </td> 
   <td> 
    <ul> 
     <li>Tutti i componenti dei moduli adattivi mappati su uno schema XSD </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>maxItems</td> 
   <td>Stringa</td> 
   <td>Specifica il numero massimo di elementi in una matrice. Gli elementi massimi devono essere uguali o maggiori di zero.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>minItems</td> 
   <td>Stringa</td> 
   <td>Specifica il numero minimo di elementi in una matrice. Gli elementi minimi devono essere uguali o maggiori di zero.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

## costrutti non supportati {#non-supported-constructs}

I moduli adattivi non supportano i seguenti costrutti dello schema JSON:

* Tipo Null
* tipi dell&#39;Unione, quali eventuali, e
* Uno, AnyOf, AllOf e NOT
* Sono supportati solo gli array omogenei. Pertanto, il vincolo elementi deve essere un oggetto e non un array.

## Domande frequenti {#frequently-asked-questions}

**Perché non è possibile trascinare singoli elementi di un sottomodulo (struttura generata da qualsiasi tipo complesso) per sottomoduli ripetibili (i valori minOccours o maxOccours sono maggiori di 1)?**

In un sottomodulo ripetibile, è necessario utilizzare il sottomodulo completo. Se desideri solo campi selettivi, utilizza l’intera struttura ed elimina quelli indesiderati.

**Ho una lunga struttura complessa in Content Finder. Come posso trovare un elemento specifico?**

Sono disponibili due opzioni:

* Scorrere la struttura ad albero
* Utilizza la casella Ricerca per trovare un elemento

