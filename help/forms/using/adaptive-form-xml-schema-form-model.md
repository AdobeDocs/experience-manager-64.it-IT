---
title: Creazione di moduli adattivi tramite schema XML
seo-title: Creating adaptive forms using XML Schema
description: I moduli adattivi possono utilizzare lo schema XML come modello di modulo, consentendo di sfruttare i modelli XSD esistenti per creare moduli adattivi. È possibile trascinare elementi dello schema da XSD nel modulo adattivo.
seo-description: Adaptive forms can use XML schema as form model, allowing you to leverage existing XSD templates to create adaptive forms. You can drag-and-drop schema elements from XSD onto your adaptive form.
uuid: a5f5d423-9b83-47e8-b0fa-88210d0d18d9
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a1070d9e-fb7c-4134-b6d5-ffa2d3e9718d
feature: Adaptive Forms
exl-id: 5f6d23b2-ab8b-48fd-b853-eea7d6c9d651
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 6%

---

# Creazione di moduli adattivi tramite schema XML {#creating-adaptive-forms-using-xml-schema}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Prerequisiti {#prerequisites}

La creazione di un modulo adattivo utilizzando uno schema XML come modello di modulo richiede la comprensione di base degli schemi XML. Inoltre, è consigliabile consultare il seguente contenuto prima di questo articolo.

* [Creazione di un modulo adattivo](/help/forms/using/creating-adaptive-form.md)
* [Schema XML](https://www.w3.org/TR/xmlschema-2/)

## Utilizzo di uno schema XML come modello di modulo {#using-an-xml-schema-as-form-model}

AEM Forms supporta la creazione di un modulo adattivo utilizzando uno schema XML esistente come modello di modulo. Questo schema XML rappresenta la struttura in cui i dati vengono prodotti o utilizzati dal sistema back-end della tua organizzazione.

Le caratteristiche principali dell&#39;utilizzo di uno schema XML sono:

* La struttura di XSD viene visualizzata come una struttura nella scheda Content Finder nella modalità di creazione per un modulo adattivo. Puoi trascinare e aggiungere un elemento dalla gerarchia XSD al modulo adattivo.
* È possibile precompilare il modulo utilizzando un XML conforme allo schema associato.
* Al momento dell’invio, i dati immessi dall’utente vengono inviati come XML che si allinea allo schema associato.

Uno schema XML è costituito da tipi di elementi semplici e complessi. Gli elementi dispongono di attributi che aggiungono regole all’elemento. Quando questi elementi e attributi vengono trascinati in un modulo adattivo, vengono mappati automaticamente sul componente del modulo adattivo corrispondente.

Questa mappatura degli elementi XML con componenti per moduli adattivi è la seguente:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Elemento o attributo XML </strong></th> 
   <th><strong>Componente per moduli adattivi</strong></th> 
  </tr> 
  <tr> 
   <td><code>xs:string</code></td> 
   <td>Casella di testo</td> 
  </tr> 
  <tr> 
   <td><code>xs:boolean</code></td> 
   <td>Casella di selezione</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li><code>xs:unsignedInt</code></li> 
     <li><code>xs:xs:int</code></li> 
     <li><code class="code">xs:decimal 
        </code></li> 
     <li>Tutti i tipi di valori numerici</li> 
    </ul> </td> 
   <td>Casella numerica</td> 
  </tr> 
  <tr> 
   <td><code>xs:date</code></td> 
   <td>Selettore data</td> 
  </tr> 
  <tr> 
   <td><code class="code">xs:enumeration
      </code></td> 
   <td>Elenco a discesa</td> 
  </tr> 
  <tr> 
   <td>Qualsiasi elemento di tipo complesso</td> 
   <td>Pannello</td> 
  </tr> 
 </tbody> 
</table>

## Schema XML di esempio {#sample-xml-schema}

Ecco un esempio di schema XML.

```xml
<?xml version="1.0" encoding="utf-8" ?> 
    <xs:schema targetNamespace="https://adobe.com/sample.xsd"
                    xmlns="https://adobe.com/sample.xsd"
                    xmlns:xs="https://www.w3.org/2001/XMLSchema"
                >

        <xs:element name="sample" type="SampleType"/>
        
        <xs:complexType name="SampleType">
            <xs:sequence>
                <xs:element name="leaderName" type="xs:string" default="Enter Name"/>
                <xs:element name="assignmentStartBirth" type="xs:date"/>
                <xs:element name="gender" type="GenderEnum"/>
                <xs:element name="noOfProjectsAssigned" type="IntType"/>
                <xs:element name="assignmentDetails" type="AssignmentDetails" 
                                            minOccurs="0" maxOccurs="10"/>
            </xs:sequence>
        </xs:complexType>

        <xs:complexType name="AssignmentDetails">
            <xs:attribute name="name" type="xs:string" use="required"/>
            <xs:attribute name="durationOfAssignment" type="xs:unsignedInt" use="required"/>
            <xs:attribute name="numberOfMentees" type="xs:unsignedInt" use="required"/>
             <xs:attribute name="descriptionOfAssignment" type="xs:string" use="required"/>
             <xs:attribute name="financeRelatedProject" type="xs:boolean"/>
       </xs:complexType>
  <xs:simpleType name="IntType">
            <xs:restriction base="xs:int">
            </xs:restriction>
        </xs:simpleType>
  <xs:simpleType name="GenderEnum">
            <xs:restriction base="xs:string">
                <xs:enumeration value="Female"/>
                <xs:enumeration value="Male"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:schema>
```

>[!NOTE]
>
>Assicurati che lo schema XML abbia un solo elemento principale. Uno schema XML con più di un elemento principale non è supportato.

## Aggiunta di proprietà speciali ai campi utilizzando lo schema XML {#adding-special-properties-to-fields-using-xml-schema}

È possibile aggiungere i seguenti attributi agli elementi dello schema XML per aggiungere proprietà speciali ai campi del modulo adattivo associato.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Proprietà schema</strong></th> 
   <th><strong>Uso in modulo adattivo</strong></th> 
   <th><strong>Supportato in </strong></th> 
  </tr> 
  <tr> 
   <td><code>use=required </code></td> 
   <td>Contrassegna un campo obbligatorio<br /> </td> 
   <td>Attributo</td> 
  </tr> 
  <tr> 
   <td><code>default="default value"</code></td> 
   <td>Aggiunge un valore predefinito</td> 
   <td>Elemento e attributo</td> 
  </tr> 
  <tr> 
   <td><code>minOccurs="3"</code></td> 
   <td><p>Specifica le occorrenze minime</p> <p>(Per sottomoduli ripetibili (tipi complessi))</p> </td> 
   <td>Elemento (tipo complesso)</td> 
  </tr> 
  <tr> 
   <td><code class="code">maxOccurs="10"
      </code></td> 
   <td><p>Specifica le occorrenze massime</p> <p>(Per sottomoduli ripetibili (tipi complessi))</p> </td> 
   <td>Elemento (tipo complesso)</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Quando si trascina un elemento dello schema in un modulo adattivo, una didascalia predefinita viene generata da:
>
>* Capitalizzazione del primo carattere del nome dell’elemento
>* Inserimento di spazio bianco ai limiti Camel Case.
>
>Ad esempio, se aggiungi il `userFirstName` elemento schema, la didascalia generata nel modulo adattivo è `User First Name`.

## Limitare i valori accettabili per un componente modulo adattivo {#limit-acceptable-values-for-an-adaptive-form-component}

È possibile aggiungere le seguenti restrizioni agli elementi dello schema XML per limitare i valori accettabili per un componente modulo adattivo:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> Proprietà schema</strong></p> </td> 
   <td><p><strong>Tipo di dati</strong></p> </td> 
   <td><p><strong>Descrizione</strong></p> </td> 
   <td><p><strong>Componente</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><code>totalDigits</code></p> </td> 
   <td><p>Stringa</p> </td> 
   <td><p>Specifica il numero massimo di cifre consentito in un componente. Il numero di cifre specificato deve essere maggiore di zero.</p> </td> 
   <td> 
    <ul> 
     <li>Casella numerica</li> 
     <li>Stepper numerico</li> 
    </ul> </td> 
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
   <td><p><code>maxLength</code></p> </td> 
   <td><p>Stringa</p> </td> 
   <td><p>Specifica il numero massimo di caratteri consentiti in un componente. La lunghezza massima deve essere maggiore di zero.</p> </td> 
   <td> 
    <ul> 
     <li>Casella di testo</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>length</code></p> </td> 
   <td><p>Stringa</p> </td> 
   <td><p>Specifica il numero esatto di caratteri consentiti in un componente. La lunghezza deve essere uguale o maggiore di zero.</p> </td> 
   <td> 
    <ul> 
     <li>Casella di testo</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p><code>fractionDigits</code></p> </td> 
   <td><p>Stringa</p> </td> 
   <td><p>Specifica il numero massimo di posizioni decimali consentite in un componente. La frazioneDigits deve essere uguale o maggiore di zero.</p> </td> 
   <td> 
    <ul> 
     <li> Casella numerica con tipo di dati mobile o decimale</li> 
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
 </tbody> 
</table>

## Domande frequenti {#frequently-asked-questions}

**Come faccio a sapere quale elemento della struttura è associato a quale elemento XML?**

Quando si fa doppio clic su un elemento in Content Finder, un pop-up visualizza un nome di campo e una proprietà denominata `bindRef`. Questa proprietà mappa l&#39;elemento struttura all&#39;elemento o all&#39;attributo nello schema.

![Campo di binding di un elemento di schema XML](assets/dblclick.png)

bindRef</code> mostra l&#39;associazione tra un elemento struttura e un elemento o un attributo in uno schema.

>[!NOTE]
>
>Gli attributi hanno un `@` simbolo `bindRef`per distinguerli dagli elementi. Esempio: `/config/projectDetails/@duration`.

**Perché non è possibile trascinare singoli elementi di un sottomodulo (struttura generata da qualsiasi tipo complesso) per sottomoduli ripetibili (i valori minOccours o maxOccours sono maggiori di 1)?**

In un sottomodulo ripetibile, è necessario utilizzare il sottomodulo completo. Se desideri solo campi selettivi, utilizza l’intera struttura ed elimina quelli indesiderati.

**Ho una lunga struttura complessa in Content Finder. Come posso trovare un elemento specifico?**

Sono disponibili due opzioni:

* Scorrere la struttura ad albero
* Utilizza la casella Ricerca per trovare un elemento

**Cos&#39;è un bindRef?**

A `bindRef` è la connessione tra un componente modulo adattivo e un elemento o attributo schema. Stabilisce la `XPath` dove il valore acquisito da questo componente o campo è disponibile nell&#39;XML di output. A `bindRef`viene utilizzato anche durante la precompilazione di un valore di campo da XML precompilato (prepopolato).
