---
title: NON PUBBLICARE, MA NON DELETE Personalizzazione dei tipi di dati per i modelli di frammenti di contenuto
seo-title: Customizing Data Types for Content Fragment Models
description: I tipi di dati utilizzati nei modelli di frammenti di contenuto possono essere personalizzati.
seo-description: Data types used in Content Fragment Models can be customized.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: AEM Docs
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 1%

---


# NON PUBBLICARE, MA NON DELETE Personalizzazione dei tipi di dati per i modelli di frammenti di contenuto{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[Frammenti di contenuto](/help/assets/content-fragments.md) sono basati su [modelli di frammento di contenuto](/help/assets/content-fragments-models.md). Questi modelli sono costruiti da [elementi](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) di diversi tipi di dati.

Sono disponibili diversi tipi di dati pronti all’uso, tra cui testo a riga singola, testo RTF su più righe, campi numerici, selettori booleani, opzioni di menu a discesa, data e ora e altri. Gli utenti AEM possono selezionare tipi di dati in base alle finalità editoriali dei frammenti corrispondenti. Questo consente di gestire modelli di testo semplici fino a modelli complessi con vari tipi di contenuto e l’esperienza di authoring dei frammenti associata.

I tipi di dati sono definiti da un [combinazione di proprietà del nodo](#properties) detenuti [posizioni specifiche nel repository](#locations-in-the-repository). Puoi anche creare un tuo [tipi di dati](#creating-your-data-type) e [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Posizioni nell’archivio {#locations-in-the-repository}

Tutti i tipi di dati predefiniti sono dichiarati in:

`/libs/settings`

È possibile aggiungere nuovi tipi di dati sovrapponendo la struttura del nodo come segue in `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>Non devi cambiare nulla nel `/libs` percorso.
>
>Qualsiasi cosa possa cambiare al prossimo aggiornamento o all&#39;installazione di un servizio o di un fix pack.

## Proprietà {#properties}

Le proprietà del nodo vengono utilizzate per definire i tipi di dati:

* [Proprietà dei tipi di dati](#data-type-properties)
* e all&#39;interno di [fieldProperties](#fieldproperties)

### Proprietà tipo di dati {#data-type-properties}

Tutti i tipi di dati sono rappresentati in una struttura di nodo come in:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Ogni nodo sotto `/items` dispone di proprietà che definiscono come tale tipo di dati deve essere rappresentato all&#39;interno dell&#39;editor modelli.

Tutte le seguenti proprietà devono essere presenti affinché il tipo di dati sia presente nell&#39;editor modelli:

* `fieldIcon`

   [Icona CoralUI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) per rappresentare il tipo di dati nell&#39;interfaccia utente dell&#39;editor modelli.

* ` [fieldProperties](#fieldproperties)`

   Matrice che rappresenta le proprietà di configurazione per ogni tipo di dati.

* `fieldResourceType`

   Il tipo di risorsa Sling utilizzato per eseguire il rendering del tipo di dati in un frammento di contenuto. Per i tipi di dati che possono essere sottoposti a rendering in modi diversi (ad esempio, come input di testo semplice e/o input di testo su più righe), questa proprietà deve essere creata come array, contenente tutti i tipi di risorse. La `renderasfield` viene aggiunta automaticamente a `fieldProperties` per consentire all&#39;utente di scegliere il tipo di risorsa da aggiungere al modello,

* `fieldPropResourceType`

   Il tipo di risorsa Sling utilizzato per eseguire il rendering della proprietà predefinita per il tipo di dati.

   Ad esempio, per il tipo di dati:

   * Testo a riga singola, `fieldPropResourceType` sarebbe un `textfield` component
   * Boolean, il `fieldPropResourceType` sarebbe un `checkbox` component

* `fieldViewResourceType`

   Il tipo di risorsa Sling utilizzato per eseguire il rendering del tipo di dati nell&#39;anteprima, durante la costruzione del modello. Quando l&#39;utente trascina il tipo di dati sul lato sinistro dell&#39;editor modelli, la `fieldViewResourceType` rappresenta il componente qui rappresentato. Viene utilizzato per i casi in cui non si desidera eseguire il rendering dell’intero componente, ma si desidera solo eseguire il rendering di un sostituto che riduce al minimo il sovraccarico per l’editor del modello.

* `fieldTitle`

   Proprietà che definisce il titolo di questo tipo di dati. Ad esempio: **Testo a riga singola** per `textfield` componente, **Testo a più righe** per un componente multicampo.

* `valueType`

   Questo è il tipo di valore che il tipo di dati restituisce quando viene memorizzato internamente. Vedi [Mappature](#mappings).

* `renderType`

   Questa è una rappresentazione interna del tipo di dati. Collega la `valueType` a un componente dell’interfaccia utente. Vedi [Mappature](#mappings).

* `listOrder`

   Ogni tipo di dati richiede un valore che rappresenta il proprio ordine nell’elenco. Questo viene utilizzato per garantire l&#39;ordine corretto dei vari campi (aggiunti o spostati mediante trascinamento) durante il salvataggio dell&#39;editor modelli. Questo valore deve essere un numero intero e si consiglia di assegnare il numero in modo crescente e ordinato. Durante la creazione di un nuovo tipo di dati, è consigliabile assegnare il valore in base all’ultimo tipo di dati nell’elenco (il valore più alto di `listOrder` presente nei tipi di dati).

#### Mappature {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>Tipo di dati<br /> </td> 
   <td>Tipo di valore<br /> </td> 
   <td>Tipo di rendering</td> 
  </tr> 
  <tr> 
   <td>Testo su riga singola</td> 
   <td>stringa</td> 
   <td>text-single</td> 
  </tr> 
  <tr> 
   <td>Testo su più righe</td> 
   <td>stringa, con tipo di contenuto<br /> </td> 
   <td>text-multi</td> 
  </tr> 
  <tr> 
   <td>Numero (intero/lungo)<br /> </td> 
   <td>long</td> 
   <td>numero</td> 
  </tr> 
  <tr> 
   <td>Numero (doppio/float)</td> 
   <td>double</td> 
   <td>numero</td> 
  </tr> 
  <tr> 
   <td>Booleano</td> 
   <td>booleano</td> 
   <td>booleano</td> 
  </tr> 
  <tr> 
   <td>Data e ora</td> 
   <td>calendario</td> 
   <td>time</td> 
  </tr> 
  <tr> 
   <td>Enumerazione</td> 
   <td>string/long</td> 
   <td>enumerazione</td> 
  </tr> 
  <tr> 
   <td>Tag</td> 
   <td>stringa</td> 
   <td>tag</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alcuni tipi (ad esempio, `string`, `long`, tra l&#39;altro) può avere più valori. In questo caso, il componente utilizzato per il rendering e la modifica è in genere racchiuso in un componente multicampo ( `granite/ui/components/coral/foundation/form/multifield`). L’eccezione sono i tag, dove il componente di modifica è responsabile del rendering corretto.

### fieldProperties {#fieldproperties}

Proprietà di configurazione per ogni tipo di dati. Valori per `fieldProperties`:

* `base`

   Questa è la base per tutti `fieldProperties` componenti. La definizione è situata in `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Contiene la variabile `fieldRoot`, che successivamente `fieldProperties` può essere utilizzato durante la creazione di input per recuperare il percorso corretto.

   Esempio: per ottenere il percorso corretto per un **Etichetta campo** se hai bisogno della chiave per identificare il componente a cui appartiene, l’input per questo campo deve essere `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Questo componente aggiunge la casella di controllo predefinita per `Boolean` tipo di dati, nonché i parametri Sling `checked@Delete` e `checked@TypeHint`.

* `datepickerfields`

   Componente che aggiunge gli input nascosti necessari per il funzionamento del componente del selettore data. Include la creazione delle proprietà `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` e `maxDate`.

* `datetimepickerfields`

   Viene aggiunto un campo di selezione per `Date&Time` tipo di dati per distinguere tra `Date` e `Date&Time` opzioni.

* `datevaluefield`

   In questo modo viene aggiunto un datepicker alle proprietà, in modo che un utente possa selezionare un valore predefinito per `Date&Time` tipo di dati.

* `descriptionfield`

   Questo componente aggiunge un campo di testo a più righe che rappresenta la descrizione del componente attualmente selezionato nell’editor a più righe. Viene aggiunto automaticamente dal renderer Editor modello alla fine di ogni proprietà del tipo di dati.

* `labelfield`

   Componente che aggiunge un `textfield` input che aggiunge l’etichetta del campo per un tipo di dati che può avere etichette di campo.

* `maptopropertyfield`

   Questo componente aggiunge la `Name` nelle proprietà, fornendo un identificatore al componente selezionato di un tipo di dati. Deve essere presente in tutti i tipi di dati.

* `maxlengthfield`

   Viene utilizzato per aggiungere il `maxLength` per i tipi di dati che accettano questa proprietà. Ad esempio, con **Testo a riga singola**, **Numero**, ecc.

* `multieditorfield`

   In questo modo vengono aggiunti tutti i campi nascosti necessari per il funzionamento dell’editor su più righe, rappresentato dal **Testo a più righe** tipo di dati.

* `mvfields`

   Componente che aggiunge tutti i campi nascosti necessari per il funzionamento di un componente multicampo. Ad esempio, per la seconda opzione di un **Testo a riga singola** tipo di dati. Deve essere aggiunto per qualsiasi componente di cui viene eseguito il rendering come campo multiplo.

* `numbertypefield`

   Seleziona l’opzione per la **Numero** tipo di dati che seleziona tra **Intero** o **Frazione** per **Numero** tipo di dati.

* `numbervaluefield`

   A `numberfield` selettore di valori predefinito per **Numero** `type.options` In questo modo vengono aggiunte le opzioni inserite per la **Enumerazione** tipo di dati, utilizzato per determinare i valori per il componente casella di selezione.

* `placeholderfield`

   Si tratta di un campo di testo che funge da input per `emptyText` di un componente. Questo dovrebbe essere utilizzato da tutti i tipi di dati che accettano un segnaposto (non molto complicato; ad esempio **Testo a riga singola**, **Numero**, ecc.).

* `renderasfield`

   Questo è il componente di cui viene eseguito il rendering automatico quando diversi `fieldResourceTypes` sono presenti nella proprietà del nodo del tipo di dati.

* `requiredfield`

   Questa è una casella di controllo che rappresenta la `required` per un componente. Poiché la maggior parte dei componenti accetta `required` campo , questo campo può essere utilizzato per la maggior parte dei tipi di dati.

* `tagsfields`

   Componenti che aggiungono gli input necessari per un `tagfield` componente di cui eseguire il rendering, utilizzato dalla **Tag** tipo di dati.

* `tagsroot`

   Selezione del percorso utilizzato da **Tag** tipo di dati per impostare il percorso principale per `tagsfield` componente.

* `textfield`

   Utilizzato da `Boolean` tipo di dati per impostare l’etichetta del campo della casella di controllo definita da questo tipo di dati.

* `textvaluefield`

   Proprietà valore predefinita per **Testo a riga singola** tipo di dati.

## Creazione di un tipo di dati {#creating-your-data-type}

Per creare un tipo di dati personalizzato è necessario:

* [Creare la struttura del nodo](#creating-the-node-structure)
* [Definire le proprietà per il tipo di dati](#defining-the-properties-for-your-data-type)

È quindi possibile [utilizzare il tipo di dati](#using-your-data-type).

È inoltre possibile [creare un proprio `fieldProperties`](#creating-your-own-fieldproperties-property).

### Creazione della struttura del nodo {#creating-the-node-structure}

La struttura del nodo deve essere creata in `/apps` per sovrapporre i tipi di dati. Se non esiste già, devi creare:

1. Se non esiste già, devi creare:

   ```
   + apps 
     + settings
       + dam 
         + cfm (cq:Page) 
           + models (nt:folder)
             + formbuilderconfig (sling:folder)
               + datatypes (nt:unstructured)
                 + items (nt:unstructured)
   ```

   >[!NOTE]
   >
   >`/apps/settings/dam` dovrebbe esistere già.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` potrebbe essere necessario creare i nodetypes specificati.

1. Sotto `/items` puoi aggiungere nuovi nodi per rappresentare i nuovi tipi di dati:

   * Tipo di nodo: `nt:unstructured`
   * &quot;Proprietà: vedere [Definizione delle proprietà per il tipo di dati](#defining-the-properties-for-your-data-type)

### Definizione delle proprietà per il tipo di dati {#defining-the-properties-for-your-data-type}

1. Determinare i valori per quanto segue [proprietà del tipo di dati](#data-type-properties) necessari per il tipo di dati:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Questi definiscono come verrà eseguito il rendering dei componenti per il tipo di dati. Possono essere di qualsiasi componente; inclusi i componenti personalizzati (è necessario un set corrispondente di ` [fieldProperties](#fieldproperties)`).

   Definisci queste proprietà, con i valori appropriati, sul nodo del tipo di dati.

1. Determinare il ` [fieldProperties](#fieldproperties)` da utilizzare. Dipende dagli attributi o dalle proprietà `fieldResourceType` bisogni.

   Ad esempio, un `granite/ui/components/coral/foundation/form/textfield`devono avere **Nome etichetta**, **Lunghezza massima**, **Testo segnaposto** e **Valore predefinito** proprietà.

   Puoi scegliere tra le opzioni predefinite [fieldProperties](#fieldproperties)oppure [creare proprietà personalizzate](#creating-your-own-fieldproperties-property).

   Definisci queste proprietà, con i valori appropriati, sul nodo del tipo di dati.

1. Determinare i valori per quanto segue [proprietà del tipo di dati](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Definisci queste proprietà, con i valori appropriati, sul nodo del tipo di dati.

### Utilizzo del tipo di dati {#using-your-data-type}

Dopo aver salvato questa struttura di nodo, con tutte le proprietà applicate, puoi aprire qualsiasi modello con l&#39;editor modelli e visualizzare e utilizzare il nuovo tipo di dati.

## Creazione di una proprietà fieldProperties personalizzata {#creating-your-own-fieldproperties-property}

Puoi scegliere tra le opzioni predefinite [fieldProperties](#fieldproperties)oppure crea il tuo:

1. Crea un componente in:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Se il percorso non esiste, puoi crearlo utilizzando `nt:folder` nodi.

   1. Per avere accesso alle variabili, questo componente deve estendere:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. Il componente deve essere incluso tramite:

      `sling:include`

   1. Questo componente deve eseguire il rendering di un campo (se un utente deve introdurre dei dati) o di un input nascosto con le proprietà necessarie per il tipo di dati. Ad esempio, un componente multicampo richiede un nodo figlio con il tipo di campo che deve duplicare, pertanto deve esserci un input che può creare (attraverso la meccanica di sling POST) un nodo figlio di un tipo specifico.

1. Il nome di base di questo componente deve essere aggiunto a `fieldProperties`.
1. Ripetere l&#39;operazione per tutte le proprietà necessarie.

