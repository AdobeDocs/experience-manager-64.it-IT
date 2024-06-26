---
title: Creare un aspetto personalizzato per i campi modulo adattivo
seo-title: Create custom appearances for adaptive form fields
description: Personalizza l’aspetto dei componenti predefiniti in Forms adattivo.
seo-description: Customize appearance of out-of-the-box components in Adaptive Forms.
uuid: 1f2d2ac4-44e1-45f9-a6a0-eb95931b0633
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 1115697c-cb7d-441a-876f-3c01761568c0
exl-id: 91d9a31d-a0af-45f6-9a20-4b52e2848979
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 0%

---

# Creare un aspetto personalizzato per i campi modulo adattivo {#create-custom-appearances-for-adaptive-form-fields}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

I moduli adattivi sfruttano [framework di aspetto](/help/forms/using/introduction-widgets.md) per creare un aspetto personalizzato per i campi modulo adattivi e fornire un’esperienza utente diversa. Ad esempio, sostituisci i pulsanti di scelta e le caselle di controllo con i pulsanti di attivazione o utilizza i plug-in jQuery personalizzati per limitare gli input degli utenti in campi come numeri di telefono o ID e-mail.

Questo documento spiega come utilizzare un plug-in jQuery per creare queste esperienze alternative per i campi del modulo adattivo. Inoltre, mostra un esempio per creare un aspetto personalizzato per l’aspetto che il componente campo numerico deve avere come passo o cursore numerico.

Analizziamo innanzitutto i termini e i concetti chiave utilizzati in questo articolo.

**Aspetto** Si riferisce allo stile, all’aspetto e all’organizzazione di vari elementi di un campo modulo adattivo. In genere include un’etichetta, un’area interattiva per fornire gli input, un’icona della guida e descrizioni brevi e lunghe del campo. La personalizzazione dell&#39;aspetto di cui al presente articolo è applicabile per l&#39;aspetto dell&#39;area di input del campo.

**Plug-in jQuery** Fornisce un meccanismo standard, basato sul framework di widget jQuery, per implementare un aspetto alternativo.

**ClientLib** Un sistema di librerie lato client in AEM elaborazione lato client basato su codice JavaScript e CSS complessi. Per ulteriori informazioni, vedere Uso delle librerie lato client.

**Archetipo** toolkit per modelli di progetto Maven definito come modello o modello originale per i progetti Maven. Per ulteriori informazioni, vedere Introduzione agli Archetipi.

**Controllo utente** Si riferisce all&#39;elemento principale di un widget che contiene il valore del campo e viene utilizzato dal framework di aspetto per collegare l&#39;interfaccia utente dei widget personalizzati con il modello di modulo adattivo.

## Passaggi per creare un aspetto personalizzato {#steps-to-create-a-custom-appearance}

I passaggi da seguire per creare un aspetto personalizzato sono i seguenti:

1. **Creare un progetto**: Crea un progetto Maven che genera un pacchetto di contenuti da distribuire in AEM.
1. **Estendere una classe di widget esistente**: Estendi una classe di widget esistente e sovrascrivi le classi richieste.
1. **Creare una libreria client**: Crea un `clientLib: af.customwidget` e aggiungi i file JavaScript e CSS richiesti.

1. **Crea e installa il progetto**: Crea il progetto Maven e installa il pacchetto di contenuti generato su AEM.
1. **Aggiornare il modulo adattivo**: Aggiornare le proprietà dei campi del modulo adattivo per utilizzare l’aspetto personalizzato.

### Creare un progetto {#create-a-project}

Un archetipo maven è un punto di partenza per la creazione di un aspetto personalizzato. I dettagli dell&#39;archetipo da utilizzare sono i seguenti:

* **Archivio**: https://repo.adobe.com/nexus/content/groups/public/
* **Id Artifact**: custom-Appe-Archetype
* **ID gruppo**: com.adobe.aemforms
* **Versione**: 1.0.4

Esegui il comando seguente per creare un progetto locale basato sull&#39;archetipo:

`mvn archetype:generate -DarchetypeRepository=https://repo.adobe.com/nexus/content/groups/public/ -DarchetypeGroupId=com.adobe.aemforms -DarchetypeArtifactId=custom-appearance-archetype -DarchetypeVersion=1.0.4`

Il comando scarica i plug-in Maven e le informazioni sull’archetipo dall’archivio e genera un progetto basato sulle seguenti informazioni:

* **groupId**: ID gruppo utilizzato dal progetto Maven generato
* **artifactId**: ID artefatto utilizzato dal progetto Maven generato.
* **version**: Versione per il progetto Maven generato.
* **pacchetto**: Pacchetto utilizzato per la struttura del file.
* **artifactName**: Nome dell&#39;artefatto del pacchetto AEM generato.
* **packageGroup**: Gruppo di pacchetti del pacchetto AEM generato.
* **widgetName**: Nome dell&#39;aspetto utilizzato come riferimento.

La struttura del progetto generato è la seguente:

```java
─<artifactId>

 └───src

     └───main

         └───content

             └───jcr_root

                 └───etc

                     └───clientlibs

                         └───custom

                             └───<widgetName>

                                 ├───common [client library - af.customwidgets which encapsulates below clientLibs]

                                 ├───integration [client library - af.customwidgets.<widgetName>_widget which contains template files for integrating a third-party plugin with Adaptive Forms]

                                 │   ├───css

                                 │   └───javascript

                                 └───jqueryplugin [client library - af.customwidgets.<widgetName>_plugin which holds the third-party plugins and related dependencies]

                                     ├───css

                                     └───javascript
```

### Estendere una classe di widget esistente {#extend-an-existing-widget-class}

Una volta creato il modello di progetto, apporta le seguenti modifiche, a seconda delle necessità:

1. Includi la dipendenza del plug-in di terze parti nel progetto.

   1. Posiziona i plug-in jQuery di terze parti o personalizzati nel `jqueryplugin/javascript` e i relativi file CSS nel `jqueryplugin/css` cartella. Per ulteriori dettagli, consulta i file JS e CSS nella sezione `jqueryplugin/javascript and jqueryplugin/css` cartella.
   1. Modifica la `js.txt` e `css.txt` file per includere eventuali file JavaScript e CSS aggiuntivi del plug-in jQuery.

1. Integra il plug-in di terze parti con il framework per abilitare l’interazione tra il framework di aspetto personalizzato e il plug-in jQuery. Il nuovo widget funzionerà solo dopo aver esteso o sostituito le seguenti funzioni.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Funzione</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td><code>render</code></td> 
   <td>La funzione di rendering restituisce l'oggetto jQuery per l'elemento HTML predefinito del widget. L’elemento HTML predefinito deve essere di tipo focalizzabile. Ad esempio: <code>&lt;a&gt;</code>, <code>&lt;input&gt;</code>e <code>&lt;li&gt;</code>. L’elemento restituito viene utilizzato come <code>$userControl</code>. Se la <code>$userControl</code> specifica il vincolo di cui sopra, le funzioni del <code>AbstractWidget</code> funzionano come previsto, altrimenti alcune delle API comuni (attivazione, clic) richiedono modifiche. </td> 
  </tr> 
  <tr> 
   <td><code>getEventMap</code></td> 
   <td>Restituisce una mappa per convertire gli eventi HTML in eventi XFA. <br /> <code class="code">{
      blur: XFA_EXIT_EVENT,
      }</code><br /> Questo esempio mostra che <code>blur</code> è un evento di HTML e <code>XFA_EXIT_EVENT</code> è l'evento XFA corrispondente. </td> 
  </tr> 
  <tr> 
   <td><code>getOptionsMap</code></td> 
   <td>Restituisce una mappa che fornisce dettagli sull'azione da eseguire in caso di modifica di un'opzione. Le chiavi sono le opzioni fornite al widget e i valori sono funzioni che vengono chiamate ogni volta che viene rilevata una modifica nell'opzione. Il widget fornisce gestori per tutte le opzioni comuni (tranne <code>value</code> e <code>displayValue</code>).</td> 
  </tr> 
  <tr> 
   <td><code>getCommitValue</code></td> 
   <td>Il framework dei widget jQuery carica la funzione ogni volta che il valore del widget jQuery viene salvato nel modello XFA (ad esempio, in caso di uscita da un campo di testo). L'implementazione deve restituire il valore salvato nel widget. Al gestore viene fornito il nuovo valore per l’opzione .</td> 
  </tr> 
  <tr> 
   <td><code>showValue</code></td> 
   <td>Per impostazione predefinita, in XFA su evento enter, il <code>rawValue</code> del campo viene visualizzato. Questa funzione viene chiamata per mostrare la <code>rawValue</code> all'utente. </td> 
  </tr> 
  <tr> 
   <td><code>showDisplayValue</code></td> 
   <td>Per impostazione predefinita, in XFA all'evento exit, l' <code>formattedValue</code> del campo viene visualizzato. Questa funzione viene chiamata per mostrare la <code>formattedValue</code> all'utente. </td> 
  </tr> 
 </tbody> 
</table>

1. Aggiorna il file JavaScript nel `integration/javascript` se necessario.

   * Sostituire il testo `__widgetName__` con il nome effettivo del widget.
   * Estendi il widget da una classe di widget preconfigurata adatta. Nella maggior parte dei casi, si tratta della classe di widget corrispondente al widget esistente che viene sostituito. Il nome della classe padre viene utilizzato in più posizioni, pertanto si consiglia di cercare tutte le istanze della stringa `xfaWidget.textField` nel file e sostituiscili con la classe padre effettiva utilizzata.
   * Estendi la `render` per fornire un&#39;interfaccia utente alternativa. È la posizione da cui verrà richiamato il plug-in jQuery per aggiornare l’interfaccia utente o il comportamento di interazione. La `render` deve restituire un elemento di controllo utente.
   * Estendi la `getOptionsMap` per ignorare qualsiasi impostazione di opzione interessata a causa di una modifica nel widget. La funzione restituisce una mappatura che fornisce dettagli sull&#39;azione da eseguire in caso di modifica di un&#39;opzione. Le chiavi sono le opzioni fornite al widget e i valori sono le funzioni chiamate ogni volta che viene rilevata una modifica nell&#39;opzione.
   * La `getEventMap` Il metodo mappa gli eventi attivati dal widget, con gli eventi richiesti dal modello di modulo adattivo. Il valore predefinito mappa gli eventi HTML standard per il widget predefinito e deve essere aggiornato se viene attivato un evento alternativo.
   * La `showDisplayValue` e `showValue` applicare la clausola di visualizzazione e modificare l&#39;immagine e può essere ignorato per avere un comportamento alternativo.
   * La `getCommitValue` viene richiamato dal framework dei moduli adattivi quando il `commit`si verifica l&#39;evento . In genere si tratta dell’evento exit , ad eccezione degli elementi a discesa, pulsante di scelta e casella di controllo in cui si verifica al momento della modifica). Per ulteriori informazioni, consulta [Espressioni Forms adattive](/help/forms/using/adaptive-form-expressions.md#p-value-commit-script-p).
   * Il file modello fornisce un esempio di implementazione per vari metodi. Rimuovere i metodi da non estendere.

### Creare una libreria client {#create-a-client-library}

Il progetto di esempio generato dall’archetipo Maven crea automaticamente le librerie client richieste e le racchiude in una libreria client con una categoria `af.customwidgets`. I file JavaScript e CSS disponibili nel `af.customwidgets` sono inclusi automaticamente in fase di runtime.

### Creare e installare {#build-and-install}

Per creare il progetto, esegui il seguente comando sulla shell per generare un pacchetto CRX che deve essere installato sul server AEM.

`mvn clean install`

>[!NOTE]
>
>Il progetto maven si riferisce a un archivio remoto all’interno del file POM. Questo è solo a scopo di riferimento e, secondo gli standard Maven, le informazioni dell’archivio vengono acquisite nel `settings.xml` file.

### Aggiornare il modulo adattivo {#update-the-adaptive-form}

Per applicare l’aspetto personalizzato a un campo modulo adattivo:

1. Apri il modulo adattivo in modalità di modifica.
1. Apri **Proprietà** finestra di dialogo relativa al campo in cui applicare l’aspetto personalizzato.
1. In **Stile** scheda , aggiorna `CSS class` per aggiungere il nome dell&#39;aspetto nel `widget_<widgetName>` formato. Ad esempio: **widget_numericstepper**

## Esempio: Creare un aspetto personalizzato   {#sample-create-a-custom-appearance-nbsp}

Vediamo ora un esempio per creare un aspetto personalizzato in modo che un campo numerico venga visualizzato come un passo o un cursore numerico. Esegui i seguenti passaggi:

1. Esegui il comando seguente per creare un progetto locale basato su archetipo Maven:

   `mvn archetype:generate -DarchetypeRepository=https://repo.adobe.com/nexus/content/groups/public/ -DarchetypeGroupId=com.adobe.aemforms -DarchetypeArtifactId=custom-appearance-archetype -DarchetypeVersion=1.0.4`

   Viene richiesto di specificare i valori per i seguenti parametri.

   *I valori utilizzati in questo esempio sono evidenziati in grassetto*.

   `Define value for property 'groupId': com.adobe.afwidgets`

   `Define value for property 'artifactId': customWidgets`

   `Define value for property 'version': 1.0.1-SNAPSHOT`

   `Define value for property 'package': com.adobe.afwidgets`

   `Define value for property 'artifactName': customWidgets`

   `Define value for property 'packageGroup': adobe/customWidgets`

   `Define value for property 'widgetName': numericStepper`

1. Passa a `customWidgets` (valore specificato per `artifactID` property) ed esegui il seguente comando per generare un progetto Eclipse:

   `mvn eclipse:eclipse`

1. Apri lo strumento Eclipse ed effettua le seguenti operazioni per importare il progetto Eclipse:

   1. Seleziona **[!UICONTROL File > Importa > Progetti esistenti in Workspace]**.

   1. Sfoglia e seleziona la cartella in cui è stato eseguito il `archetype:generate` comando.

   1. Fai clic su **[!UICONTROL Fine]**.

      ![eclipse-screenshot](assets/eclipse-screenshot.png)

1. Seleziona il widget da utilizzare per l&#39;aspetto personalizzato. Questo esempio utilizza il seguente widget passo numerico:

   [https://www.jqueryscript.net/form/User-Friendly-Number-Input-Spinner-with-jQuery-Bootstrap.html](https://www.jqueryscript.net/form/User-Friendly-Number-Input-Spinner-with-jQuery-Bootstrap.html)

   Nel progetto Eclipse, controlla il codice plug-in nel `plugin.js` per assicurarsi che corrisponda ai requisiti dell&#39;aspetto. In questo esempio, l&#39;aspetto soddisfa i seguenti requisiti:

   * Lo step numerico deve estendersi da `- $.xfaWidget.numericInput`.
   * La `set value` Il metodo del widget imposta il valore dopo che lo stato attivo è sul campo. È un requisito obbligatorio per un widget modulo adattivo.
   * La `render` per richiamare `bootstrapNumber` metodo .
   * Non esiste alcuna dipendenza aggiuntiva per il plug-in che non sia il codice sorgente principale del plug-in.
   * L’esempio non esegue alcuno stile sullo stepper, pertanto non è necessario alcun CSS aggiuntivo.
   * La `$userControl` deve essere disponibile per `render` metodo . È un campo della `text` tipo clonato con il codice del plug-in.
   * La **+** e **-** i pulsanti devono essere disattivati quando il campo è disabilitato.

1. Sostituire il contenuto della `bootstrap-number-input.js` (plugin jQuery) con il contenuto del `numericStepper-plugin.js` file.
1. In `numericStepper-widget.js` aggiungi il seguente codice per ignorare il metodo di rendering per richiamare il plug-in e restituire `$userControl` oggetto:

   ```java
   render : function() {
        var control = $.xfaWidget.numericInput.prototype.render.apply(this, arguments);
        var $control = $(control);
        var controlObject;
        try{
            if($control){
            $control.bootstrapNumber();
            var id = $control.attr("id");
            controlObject = $("#"+id);
            }
        }catch (exc){
             console.log(exc);
        }
        return controlObject;
   }
   ```

1. In `numericStepper-widget.js` , sovrascrivi `getOptionsMap` per ignorare l&#39;opzione di accesso e nascondere i pulsanti + e - in modalità disabilitata.

   ```java
   getOptionsMap: function(){
       var parentOptionsMap = $.xfaWidget.numericInput.prototype.getOptionsMap.apply(this,arguments),
   
       newMap = $.extend({},parentOptionsMap,
   
        {
   
              "access": function(val) {
              switch(val) {
                 case "open" :
                   this.$userControl.removeAttr("readOnly");
                   this.$userControl.removeAttr("aria-readonly");
                   this.$userControl.removeAttr("disabled");
                   this.$userControl.removeAttr("aria-disabled");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',false);
                   break;
                 case "nonInteractive" :
                 case "protected" :
                   this.$userControl.attr("disabled", "disabled");
                   this.$userControl.attr("aria-disabled", "true");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',true);
                   break;
                case "readOnly" :
                   this.$userControl.attr("readOnly", "readOnly");
                   this.$userControl.attr("aria-readonly", "true");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',true);
                   break;
               default :
                   this.$userControl.removeAttr("disabled");
                   this.$userControl.removeAttr("aria-disabled");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',false);
                   break;
             }
          },
      });
      return newMap;
    }
   ```

1. Salva le modifiche, passa alla cartella contenente il `pom.xml` ed esegui il seguente comando Maven per creare il progetto:

   `mvn clean install`

1. Installa il pacchetto utilizzando AEM Gestione pacchetti.

1. Apri il modulo adattivo in modalità di modifica in cui desideri applicare l’aspetto personalizzato ed effettua le seguenti operazioni:

   1. Fare clic con il pulsante destro del mouse sul campo a cui si desidera applicare l&#39;aspetto e fare clic su **[!UICONTROL Modifica]** per aprire la finestra di dialogo Modifica componente.

   1. Nella scheda Stile , aggiorna la **[!UICONTROL Classe CSS]** proprietà da aggiungere `widget_numericStepper`.

Il nuovo aspetto appena creato è ora disponibile per l’uso.
