---
title: NON PUBBLICARE, MA NON personalizzare i tipi di dati DELETE per i modelli di frammenti di contenuto
seo-title: Personalizzazione dei tipi di dati per i modelli di frammenti di contenuto
description: È possibile personalizzare i tipi di dati utilizzati nei modelli di frammenti di contenuto.
seo-description: È possibile personalizzare i tipi di dati utilizzati nei modelli di frammenti di contenuto.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 1%

---


# NON PUBBLICARE, MA NON personalizzare i tipi di dati DELETE per i modelli di frammenti di contenuto{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[I ](/help/assets/content-fragments.md) frammenti di contenuto si basano su modelli [ di frammenti di ](/help/assets/content-fragments-models.md)contenuto. Questi modelli sono composti da [elementi](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) di tipi di dati diversi.

Sono disponibili diversi tipi di dati out-of-the-box, tra cui testo su una sola riga, RTF per più righe, campi numerici, selettori booleani, opzioni di menu a discesa, data e ora e altri. AEM utenti possono selezionare i tipi di dati in base all&#39;intento editoriale dei frammenti corrispondenti. Questo consente di gestire modelli di testo semplici attraverso modelli complessi con diversi tipi di contenuto e l’esperienza di authoring dei frammenti associata.

I tipi di dati sono definiti da una [combinazione di proprietà nodo](#properties) in [posizioni specifiche nella directory archivio](#locations-in-the-repository). È inoltre possibile creare tipi di dati [personalizzati](#creating-your-data-type) e [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## Posizioni nel repository {#locations-in-the-repository}

Tutti i tipi di dati forniti sono dichiarati in:

`/libs/settings`

È possibile aggiungere nuovi tipi di dati sovrapponendo la struttura del nodo come segue in `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>Non è necessario modificare nulla nel percorso `/libs`.
>
>Tutto ciò che è possibile cambiare al successivo aggiornamento, o l&#39;installazione di un servizio o fix pack.

## Proprietà {#properties}

Le proprietà nodo vengono utilizzate per definire i tipi di dati:

* [Proprietà dei tipi di dati](#data-type-properties)
* e all&#39;interno di [fieldProperties](#fieldproperties)

### Proprietà tipo di dati {#data-type-properties}

Tutti i tipi di dati sono rappresentati in una struttura di nodi come in:

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

Ogni nodo in `/items` dispone di proprietà che definiscono il modo in cui tale tipo di dati deve essere rappresentato all&#39;interno dell&#39;editor modelli.

Affinché il tipo di dati sia presente nell&#39;editor modelli, devono essere presenti tutte le proprietà seguenti:

* `fieldIcon`

   [L’](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) icona CoralUI rappresenta il tipo di dati nell’interfaccia utente dell’editor modelli.

* ` [fieldProperties](#fieldproperties)`

   Array che rappresenta le proprietà di configurazione per ciascun tipo di dati.

* `fieldResourceType`

   Il tipo di risorsa Sling utilizzato per eseguire il rendering del tipo di dati in un frammento di contenuto. Per i tipi di dati che possono essere sottoposti a rendering in modi diversi (ad esempio, come input di testo semplice e/o immissione di testo su più righe), questa proprietà deve essere creata come array, contenente tutti i tipi di risorse. La proprietà `renderasfield` verrà aggiunta automaticamente a `fieldProperties` per consentire all&#39;utente di scegliere il tipo di risorsa da aggiungere al modello,

* `fieldPropResourceType`

   Il tipo di risorsa Sling utilizzato per rappresentare la proprietà predefinita per il tipo di dati.

   Ad esempio, per il tipo di dati:

   * Testo a riga singola, il `fieldPropResourceType` è un componente `textfield`
   * Booleano, `fieldPropResourceType` è un componente `checkbox`

* `fieldViewResourceType`

   Il tipo di risorsa Sling utilizzato per rappresentare il tipo di dati nell&#39;anteprima, durante la costruzione del modello. Quando l&#39;utente trascina il tipo di dati sul lato sinistro dell&#39;editor modelli, la proprietà `fieldViewResourceType` rappresenta il componente di cui viene eseguito il rendering. Questa opzione è utilizzata per i casi in cui non si desidera eseguire il rendering completo del componente, ma si desidera solo eseguire il rendering di un sostituto che riduce al minimo il sovraccarico per l&#39;editor modelli.

* `fieldTitle`

   Proprietà che definisce il titolo di questo tipo di dati. Ad esempio, **Testo su riga singola** per un componente `textfield`, **Testo su più righe** per un componente multicampo.

* `valueType`

   Questo è il tipo di valore che il tipo di dati restituisce quando viene memorizzato internamente. Vedere [Mappature](#mappings).

* `renderType`

   Si tratta di una rappresentazione interna del tipo di dati. Collega l&#39;elemento `valueType` a un componente dell&#39;interfaccia utente. Vedere [Mappature](#mappings).

* `listOrder`

   Ogni tipo di dati necessita di un valore che ne rappresenti l&#39;ordine nell&#39;elenco. Questo consente di garantire l&#39;ordine corretto dei vari campi (aggiunti o spostati mediante trascinamento) durante il salvataggio dell&#39;editor modelli. Questo valore deve essere un numero intero e si consiglia di assegnare il numero in modo crescente e ordinato. Durante la creazione di un nuovo tipo di dati è consigliabile assegnare il valore in base all&#39;ultimo tipo di dati nell&#39;elenco (il valore più alto di `listOrder` presente nei tipi di dati).

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
   <td>string</td> 
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
   <td>Numero (doppio/mobile)</td> 
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
   <td>string</td> 
   <td>tag</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alcuni tipi (ad esempio `string`, `long`) possono avere più valori. In questo caso, il componente utilizzato per il rendering e la modifica è in genere racchiuso da un componente multicampo ( `granite/ui/components/coral/foundation/form/multifield`). L’eccezione sono i tag, dove il componente di modifica è responsabile per il corretto rendering.

### fieldProperties {#fieldproperties}

Proprietà di configurazione per ciascun tipo di dati. Valori per `fieldProperties`:

* `base`

   Questa è la base per tutti i componenti `fieldProperties`. La definizione si trova in `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   Contiene la variabile `fieldRoot`, che successive `fieldProperties` possono utilizzare per creare input per recuperare il percorso corretto.

   Esempio: per ottenere il percorso corretto per un **etichetta campo** sarà necessario che la chiave identifichi il componente a cui appartiene, l&#39;input per questo campo deve essere `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   Questo componente aggiunge la casella di controllo predefinita per il tipo di dati `Boolean`, oltre ai parametri Sling `checked@Delete` e `checked@TypeHint`.

* `datepickerfields`

   Componente che aggiunge gli input nascosti necessari per il funzionamento del componente del selettore data. Include la creazione delle proprietà `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` e `maxDate`.

* `datetimepickerfields`

   Questo aggiunge un campo di selezione per il tipo di dati `Date&Time` per distinguere tra le opzioni `Date` e `Date&Time`.

* `datevaluefield`

   In questo modo si aggiunge un datepicker alle proprietà, in modo che l&#39;utente possa selezionare un valore predefinito per il tipo di dati `Date&Time`.

* `descriptionfield`

   Questo componente aggiunge un campo di testo a più righe che rappresenta la descrizione del componente attualmente selezionato nell’editor a più righe. Viene aggiunto automaticamente dal renderer Editor modello alla fine di ogni proprietà del tipo di dati.

* `labelfield`

   Componente che aggiunge un input `textfield` che aggiunge l&#39;etichetta del campo a un tipo di dati che può avere etichette di campo.

* `maptopropertyfield`

   Questo componente aggiunge il campo `Name` nelle proprietà, fornendo un identificatore al componente selezionato di un tipo di dati. Deve essere presente in tutti i tipi di dati.

* `maxlengthfield`

   Viene utilizzato per aggiungere la proprietà `maxLength` per l&#39;utilizzo con i tipi di dati che accettano questa proprietà. Ad esempio, con **Testo su riga singola**, **Numero**, ecc.

* `multieditorfield`

   Questo aggiunge tutti i campi nascosti necessari al funzionamento dell&#39;editor su più righe, rappresentato dal tipo di dati **Testo su più righe**.

* `mvfields`

   Componente che aggiunge tutti i campi nascosti necessari per il funzionamento di un componente multicampo. Ad esempio, per la seconda opzione di un tipo di dati **Testo su riga singola**. Deve essere aggiunto per qualsiasi componente rappresentato come multicampo.

* `numbertypefield`

   Selezionare l&#39;opzione per il tipo di dati **Number** che seleziona tra **Integer** o **Frazione** per il tipo di dati **Number**.

* `numbervaluefield`

   Selettore di valori `numberfield` predefinito per il **Number** `type.options` Questo aggiunge le opzioni inserite per il tipo di dati **Enumeration**, utilizzato per determinare i valori per il componente casella di selezione.

* `placeholderfield`

   Si tratta di un campo di testo che funge da input per la proprietà `emptyText` di un componente. Questo dovrebbe essere utilizzato da tutti i tipi di dati che accettano un segnaposto (che non è molto complicato; ad esempio **Testo su riga singola**, **Numero**, ecc.)

* `renderasfield`

   Si tratta del componente di cui viene eseguito il rendering automaticamente quando nella proprietà del nodo del tipo di dati sono presenti più `fieldResourceTypes`.

* `requiredfield`

   Questa casella di controllo rappresenta la proprietà `required` di un componente. Poiché la maggior parte dei componenti accetta il campo `required`, questo campo può essere utilizzato per la maggior parte dei tipi di dati.

* `tagsfields`

   Componenti che aggiungono gli input necessari per il rendering di un componente `tagfield`, utilizzati dal tipo di dati **Tags**.

* `tagsroot`

   Selettore percorso utilizzato dal tipo di dati **Tag** per impostare il percorso principale per il componente `tagsfield`.

* `textfield`

   Utilizzato dal tipo di dati `Boolean` per impostare l&#39;etichetta del campo della casella di controllo definita da questo tipo di dati.

* `textvaluefield`

   La proprietà valore predefinita per il tipo di dati **Testo su riga singola**.

## Creazione del tipo di dati {#creating-your-data-type}

Per creare un tipo di dati personalizzato è necessario:

* [Creare la struttura del nodo](#creating-the-node-structure)
* [Definire le proprietà per il tipo di dati](#defining-the-properties-for-your-data-type)

È quindi possibile [utilizzare il tipo di dati](#using-your-data-type).

È inoltre possibile [creare un `fieldProperties`](#creating-your-own-fieldproperties-property) personalizzato.

### Creazione della struttura del nodo {#creating-the-node-structure}

La struttura del nodo deve essere creata in `/apps` per sovrapporre i tipi di dati. Se non esiste già, è necessario creare:

1. Se non esiste già, è necessario creare:

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
   >`/apps/settings/dam` dovrebbe già esistere.
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` potrebbe essere necessario creare con i tipi di nodi specificati.

1. In `/items` è possibile aggiungere nuovi nodi per rappresentare i nuovi tipi di dati:

   * Tipo di nodo: `nt:unstructured`
   * &quot;Proprietà: vedere [Definizione delle proprietà per il tipo di dati](#defining-the-properties-for-your-data-type)

### Definizione delle proprietà per il tipo di dati {#defining-the-properties-for-your-data-type}

1. Determinare i valori per le seguenti proprietà [del tipo di dati](#data-type-properties) necessarie per il tipo di dati:

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   Questi definiscono il modo in cui verrà eseguito il rendering dei componenti per il tipo di dati. Possono essere un qualsiasi componente; includi i tuoi componenti personalizzati (è necessario un insieme corrispondente di ` [fieldProperties](#fieldproperties)`).

   Definire queste proprietà, con i valori appropriati, sul nodo del tipo di dati.

1. Determinare la ` [fieldProperties](#fieldproperties)` da utilizzare. Ciò dipende dagli attributi o dalle proprietà di cui `fieldResourceType` ha bisogno.

   Ad esempio, un `granite/ui/components/coral/foundation/form/textfield`deve avere una proprietà **Label Name**, una proprietà **Maximum Length**, un **Placeholder Text** e una proprietà **Default Value**.

   È possibile scegliere tra le [fieldProperties](#fieldproperties) predefinite oppure [creare proprietà personalizzate](#creating-your-own-fieldproperties-property).

   Definire queste proprietà, con i valori appropriati, sul nodo del tipo di dati.

1. Determinare i valori per le seguenti proprietà [del tipo di dati](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   Definire queste proprietà, con i valori appropriati, sul nodo del tipo di dati.

### Utilizzo del tipo di dati {#using-your-data-type}

Dopo aver salvato la struttura del nodo, con tutte le proprietà applicate, è possibile aprire qualsiasi modello con l&#39;editor modelli e visualizzare e utilizzare il nuovo tipo di dati.

## Creazione della proprietà fieldProperties personale {#creating-your-own-fieldproperties-property}

È possibile scegliere tra le [fieldProperties](#fieldproperties) pronte all&#39;uso oppure crearne di nuove:

1. Crea un componente in:

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   Se il percorso non esiste, è possibile crearlo utilizzando i nodi `nt:folder`.

   1. Per avere accesso alle variabili, questo componente deve estendere:

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. Il componente deve essere incluso tramite:

      `sling:include`

   1. Questo componente deve eseguire il rendering di un campo (se l&#39;utente deve inserire dei dati) o di un input nascosto con le proprietà necessarie per il tipo di dati. Ad esempio, un componente multicampo richiede un nodo secondario con il tipo di campo che deve duplicare, pertanto deve essere presente un input in grado di creare (attraverso la meccanica dei POST sling) un nodo secondario di un tipo specifico.

1. Il nome di base di questo componente deve essere aggiunto a `fieldProperties`.
1. Ripetere l&#39;operazione per tutte le proprietà necessarie.

