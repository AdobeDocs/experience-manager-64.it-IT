---
title: Creazione di stili CSS per i moduli HTML5
seo-title: Creating CSS styles for HTML5 forms
description: Scopri come modificare l’aspetto dei moduli HTML5 modificando la classe CSS associata all’elemento modulo HTML.
seo-description: Learn how to change the appearance of HTML5 forms by modifying the CSS class associated with the HTML form element.
uuid: 43c689b4-243c-43de-a8be-1eef10d75295
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a8d986ab-2a4c-488b-957e-4606f7391bd3
feature: Mobile Forms
exl-id: 9e381e71-63ff-41ab-a6ec-9f92447b65a0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 4%

---

# Creazione di stili CSS per i moduli HTML5 {#creating-css-styles-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il rendering HTML5 di un modello di modulo basato su XFA è costituito da diversi elementi di HTML. Questi elementi sono disposti in ordine. Ogni elemento dispone di classi CSS ben definite. Puoi utilizzare queste classi CSS per selezionare e modificare l’aspetto di un elemento.

>[!NOTE]
>
>Nelle classi CSS, non modificare il valore degli attributi di larghezza, altezza, spessore del bordo, superiore, sinistra, destra, inferiore, spaziatura, margine e altri attributi di posizione e dimensione. Qualsiasi modifica negli attributi di posizione e dimensione comporta modifiche al layout del modulo.

## Classi CSS per gli elementi  {#css-classes-nbsp-for-elements-nbsp}

Ogni elemento contiene classi CSS ben definite. È possibile modificare queste classi per modificare l&#39;aspetto di un elemento. Ogni elemento, ad eccezione del campo e degli elementi di disegno, dispone di due classi CSS: Classe Type e Classe Name.

* La **Classe Type** rappresenta il tipo del campo XFA. È possibile ignorare le `type` per modificare gli stili di tutti gli elementi di un particolare tipo.

* La **Classe Nome** corrisponde al nome del campo XFA. È possibile ignorare le `name` per modificare e applicare uno stile personalizzato a un elemento.

>[!NOTE]
>
>Alcuni elementi XFA non hanno un nome. Per modificare gli stili di tali componenti, modifica tutti i componenti di quel particolare tipo.

Per le pagine senza nome in AEM Forms Designer, le pagine di un modulo HTML5 vengono denominate in ordine crescente rispetto al loro numero. Ad esempio, per un modulo HTML5 con due pagine, le pagine sono denominate Pagina1, Pagina2.

## Elemento del campo {#field-element}

L’elemento campo contiene due elementi nidificati: widget e didascalia.

**Elemento Widget**

L&#39;elemento widget contiene l&#39;elemento dell&#39;interfaccia utente per l&#39;interazione con gli utenti. Ha tre classi CSS:

* **Widget**: Ogni widget ha questa classe.
* **name**: Tutti i widget forniti con AEM contengono la classe del nome del widget. Per i widget personalizzati, lo sviluppatore di widget fornisce la classe Widget name.
* **type**: Ogni widget ha un elemento di interfaccia utente. Questa classe definisce il tipo di elemento dell&#39;interfaccia utente.

```xml
<!--field with caption-->
<div class="field numericfield NumericField3 ">
     <div class="caption">
        caption content
     </div>
     <div class="widget numericfieldwidget numericInput">
       widget content
     </div>
</div>
 
<!--field without caption-->
<div class="widget numericfieldwidget numericInput">
   widget content
</div>
```

Oltre alla classe tipo e nome, il componente campo contiene anche una classe CSS aggiuntiva denominata **sottotipo**. Un sottotipo identifica il tipo di campo, ad esempio NumericField, DateField, TextField. È possibile sostituire la classe di sottotipo per modificare lo stile di tutti i campi di tipo, sottotipo.

## Classi CSS per diversi componenti {#css-classes-for-different-components}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Componente</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Nome</strong></td> 
  </tr> 
  <tr> 
   <td>Pagina</td> 
   <td>pagina</td> 
   <td>Nome definito dall'utente<br /> o<br /> Pagina&lt;pagenumber&gt; (predefinito)</td> 
  </tr> 
  <tr> 
   <td>Area contenuto</td> 
   <td>contentarea</td> 
   <td>Nome definito dall'utente</td> 
  </tr> 
  <tr> 
   <td>Sottomodulo</td> 
   <td>sottomodulo</td> 
   <td>Nome definito dall'utente</td> 
  </tr> 
  <tr> 
   <td>Gruppo di esclusione</td> 
   <td>exclgroup</td> 
   <td>Nome definito dall'utente</td> 
  </tr> 
  <tr> 
   <td>Draw</td> 
   <td>draw</td> 
   <td>Nome definito dall'utente</td> 
  </tr> 
  <tr> 
   <td>Campo</td> 
   <td>o in un altro campo</td> 
   <td>Nome definito dall'utente</td> 
  </tr> 
  <tr> 
   <td>Didascalia</td> 
   <td>caption</td> 
   <td>ND</td> 
  </tr> 
  <tr> 
   <td>Widget</td> 
   <td>widget</td> 
   <td>Lo sviluppatore di widget lo definisce (per i widget definiti dall’utente, consulta la tabella nella sezione seguente)</td> 
  </tr> 
 </tbody> 
</table>

## Classi CSS per campi diversi {#css-classes-for-different-fields}

AEM Forms Designer supporta diversi tipi di campi in un modulo come NumericField, DecimalField e Date Field. Tutti questi campi in HTML contengono le classi CSS sopra menzionate. Inoltre, contengono alcune classi aggiuntive a seconda del tipo di campo.

A ogni campo è associato un widget che rappresenta l’elemento dell’interfaccia utente. Di seguito sono elencate le classi di ciascun campo e i widget associati a ciascun campo.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Tipo di campo</strong></td> 
   <td><strong>Sottotipo</strong></td> 
   <td><strong>Nome Widget</strong></td> 
   <td><strong>Tipo di widget</strong></td> 
   <td><strong>Tag HTML UI</strong></td> 
  </tr> 
  <tr> 
   <td>Pulsante<br type="_moz" /> </td> 
   <td>ND</td> 
   <td>xfaButton<br type="_moz" /> </td> 
   <td>buttonfieldwidget<br type="_moz" /> </td> 
   <td>input type=button<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>CheckButton<br type="_moz" /> </td> 
   <td>campo di controllo<br /> </td> 
   <td>XfaCheckBox<br type="_moz" /> </td> 
   <td>checkboxfieldwidget<br type="_moz" /> </td> 
   <td>tipo di input=casella di controllo<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>DateField<br type="_moz" /> </td> 
   <td>datefield<br type="_moz" /> </td> 
   <td>dateField<br type="_moz" /> </td> 
   <td>datefieldwidget<br type="_moz" /> </td> 
   <td>input type=text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>DateTimeField<br type="_moz" /> </td> 
   <td>campo di testo<br type="_moz" /> </td> 
   <td>textField<br type="_moz" /> </td> 
   <td>textfieldwidget</td> 
   <td>input type=text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>CampoDecimale<br type="_moz" /> </td> 
   <td>campo numerico<br type="_moz" /> </td> 
   <td>numericInput<br type="_moz" /> </td> 
   <td>numericfieldwidget<br type="_moz" /> </td> 
   <td>input type=text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>DropDown<br type="_moz" /> </td> 
   <td>sciolto<br type="_moz" /> </td> 
   <td>dropDownListWidget<br type="_moz" /> </td> 
   <td>choicelistwidget<br type="_moz" /> </td> 
   <td>select</td> 
  </tr> 
  <tr> 
   <td>CasellaDiRiepilogo<br type="_moz" /> </td> 
   <td>sciolto<br type="_moz" /> </td> 
   <td>listBoxWidget<br type="_moz" /> </td> 
   <td>choicelistwidget<br type="_moz" /> </td> 
   <td>ol</td> 
  </tr> 
  <tr> 
   <td>NumericField<br type="_moz" /> </td> 
   <td>campo numerico<br type="_moz" /> </td> 
   <td>numericInput<br type="_moz" /> </td> 
   <td>numericfieldwidget<br type="_moz" /> </td> 
   <td>input type=text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>PasswordField<br type="_moz" /> </td> 
   <td>passwordfield<br type="_moz" /> </td> 
   <td>defaultWidget<br type="_moz" /> </td> 
   <td>passwordfieldwidget<br type="_moz" /> </td> 
   <td>input type=password<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>RadioButton<br type="_moz" /> </td> 
   <td>radiocampo<br type="_moz" /> </td> 
   <td>XfaCheckBox<br type="_moz" /> </td> 
   <td>radiofieldwidget<br type="_moz" /> </td> 
   <td>input type=radio<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>CampoTesto<br type="_moz" /> </td> 
   <td>campo di testo<br type="_moz" /> </td> 
   <td>textField<br type="_moz" /> </td> 
   <td>textfieldwidget<br type="_moz" /> </td> 
   <td>input type=text<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>TimeField<br type="_moz" /> </td> 
   <td>campo di testo<br type="_moz" /> </td> 
   <td>textField<br type="_moz" /> </td> 
   <td>textfieldwidget<br type="_moz" /> </td> 
   <td>input type=text<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

## Classi CSS per diversi elementi di disegno {#css-classes-for-different-draw-elements}

È possibile inserire elementi di disegno statici come testo e immagini utilizzando AEM Forms Designer. Per ogni elemento draw, a tale elemento è associata una classe CSS separata. Di seguito è riportato l’elenco delle classi CSS per gli elementi di disegno. A ogni elemento di disegno è associata una classe di disegno.

| **Tipo di disegno** | **Classe CSS** |
|---|---|
| Testo | text |
| Immagine | immagine |
| Rettangolo | rectangle |
| Line | riga |

## Stile di altre parti del modulo {#styling-other-parts-of-the-form}

Oltre all’aspetto dei componenti dell’interfaccia utente nel modulo HTML, è possibile modificare lo stile di elementi quali Errori in linea, Avvisi in linea e campi con errori di convalida.

`Styling Inline Errors`

Quando la convalida di un campo genera un errore, quando il campo è attivo viene visualizzato un errore in linea. Per modificare lo stile degli errori in linea, sovrascrivi l’ID CSS **error-msg**.

`Styling Inline Warnings`

Quando la convalida di un campo genera un avviso, quando il campo è attivo viene visualizzato un avviso in linea. Per modificare lo stile di questi avvisi in linea, sovrascrivi l’ID CSS **warning-msg**.

`Styling Fields with Validation Errors`

Quando la convalida di un campo non riesce, cambia lo stile del widget. Questa modifica allo stile viene eseguita applicando una classe CSS **widgetError** sul componente widget. Per modificare lo stile predefinito, sovrascrivi il **widgetError** classe.
