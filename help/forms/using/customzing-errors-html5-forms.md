---
title: Personalizzazione dei messaggi di errore per i moduli HTML5
seo-title: Personalizzazione dei messaggi di errore per i moduli HTML5
description: Scopri come personalizzare la visualizzazione dei messaggi di errore per i moduli HTML5, tra cui come modificarne posizione e aspetto.
seo-description: Scopri come personalizzare la visualizzazione dei messaggi di errore per i moduli HTML5, tra cui come modificarne posizione e aspetto.
uuid: 6f48b64e-858f-4323-ad50-88e25f3c2e3d
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 44e49789-9075-41b3-bce8-03e8efce2d5a
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Personalizzazione dei messaggi di errore per i moduli HTML5 {#customizing-error-messages-for-html-forms}

Nei moduli HTML5, i messaggi di errore e gli avvisi hanno una posizione e un aspetto fissi (font e colore), l’errore viene visualizzato solo per un campo selezionato e viene visualizzato un solo errore.

L’articolo fornisce i passaggi per personalizzare i messaggi di errore dei moduli HTML5 in,

* modificare l’aspetto e la posizione dei messaggi di errore. È possibile visualizzare un errore nella parte superiore, inferiore e destra di qualsiasi campo.
* visualizzare messaggi di errore per più campi in un dato momento.
* visualizza l&#39;errore indipendentemente dal fatto che un campo sia selezionato o meno.

## Personalizzazione dei messaggi di errore  {#customizing-error-messages-nbsp}

Prima di personalizzare i messaggi di errore, scarica ed estrai il pacchetto allegato (CustomErrorManager-1.0-SNAPSHOT.zip).

Dopo aver estratto il pacchetto, apri la cartella CustomErrorManager-1.0-SNAPSHOT . Contiene le cartelle jcr_root e META-INF. Queste cartelle contengono i file CSS e JS necessari per personalizzare il messaggio di errore.

[Ottieni file](assets/customerrormanager-1.0-snapshot.zip)

### Personalizzazione della posizione dei messaggi di errore  {#customizing-the-position-of-error-messages-nbsp}

Per personalizzare la posizione del messaggio di errore, aggiungi il tag &lt;div> per ogni campo di errore e avviso, posiziona il tag &lt;div> a sinistra o a destra e applica gli stili CSS sul tag &lt;div> . Per i passaggi dettagliati, vedi la procedura seguente:

1. Passa alla cartella `CustomErrorManager-1.0-SNAPSHOT`e apri la cartella `etc\clientlibs\mf-custom-error-manager\CustomErrorManager\javascript` .
1. Apri il file `customErrorManager.js` per la modifica. La funzione `markError` nel file accetta i seguenti parametri:

   |  |  |
   |---|---|
   | jqWidget | jqWidget è la maniglia del widget. |
   | msg | contiene il messaggio di errore |
   | tipo | indica se si tratta di un errore o di un avviso |

1. Nell’implementazione predefinita, a destra del campo vengono visualizzati messaggi di errore. Per far apparire i messaggi di errore nella parte superiore, utilizza il seguente codice.

   ```
   markError: function (jqWidget, msg, type) {
               var element = jqWidget.element,                                //Gives the div containing widget
                   pos = $(element).offset(),                          //Calculates the position of the div in the view port
                                                                   msgHeight = xfalib.view.util.TextMetrics.measureExtent(msg).height + 5;  //Calculating the height of the Error Message
                   styles = {};
                   styles.left = pos.left + "px";         // Assign the desired left position using pos.left. Here it is calculated for exact left of the field 
                   styles.top = pos.top - msgHeight + "px";  // Assign the desired top position using pos.top. Here it is calculated for top of the field 
               if (type != "warning") {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the warning div if it is not present already
                       jqWidget.errorDiv=$("<div id='customError'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the warning div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               } else {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the error div if it is not present already
                       jqWidget.errorDiv=$("<div id='customWarning'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the error div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               }
   
           },
   ```

1. Salva e chiudi il file 
1. Passa alla cartella `CustomErrorManager-1.0-SNAPSHOT` e crea un archivio delle cartelle jcr_root e META-INF. Rinomina l&#39;archivio in CustomErrorManager-1.0-SNAPSHOT.zip.
1. Utilizza il gestore dei pacchetti per caricare e installare il pacchetto.

## Visualizza messaggi di errore per più campi  {#display-error-messages-for-multiple-fields-nbsp}

Utilizza il pacchetto allegato per visualizzare contemporaneamente i messaggi di errore per tutti i campi. Per visualizzare un singolo messaggio di errore, utilizza il profilo predefinito.

### Personalizzazione dell’aspetto dei messaggi di errore.  {#customizing-the-appearance-of-error-messages-nbsp}

1. Passa a etc\clientlibs\mf-custom-error-manager\CustomErrorManager\css folder.

1. Apri il file sample.css per la modifica. Il file css contiene 2 id - #customError, #customWarning. È possibile utilizzare questi ID per modificare varie proprietà come il colore, la dimensione del font, ecc.

   Utilizzare il codice seguente per modificare le dimensioni del font e il colore dei messaggi di errore/avviso.

   ```
   #customError {
   color: #0000FF; // it changes the color of Error Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 24px;  // it changes the font size of Error Message
   z-index:5;
   }
   
   #customWarning {
   color: #00FF00;  // it changes the color of Warning Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 18px;   // it changes the font size of Warning Message
   z-index:5;
   }
   
   Save the changes.
   ```

1. Salva e chiudi il file 
1. Passa alla cartella CustomErrorManager-1.0-SNAPSHOT e crea un archivio delle cartelle jcr_root e META-INF. Rinomina l&#39;archivio in CustomErrorManager-1.0-SNAPSHOT.zip.
1. Utilizza il gestore dei pacchetti per caricare e installare il pacchetto.

## Eseguire il rendering del modulo con il nuovo profilo.  {#render-the-form-with-the-new-profile-nbsp}

I moduli html5 utilizzano un profilo predefinito: https://&lt;server>/content/xfaforms/profiles/default.html?contentRoot=&lt;xdp location>&amp;template=&lt;nome dell&#39;xdp>

Per visualizzare un modulo con messaggi di errore personalizzati, eseguire il rendering del modulo con un profilo di errore: https://&lt;server>/content/xfaforms/profiles/error.html?contentRoot=&lt;xdp location>&amp;template=&lt;nome dell&#39;xdp>

>[!NOTE]
>
>Il pacchetto allegato installa il profilo di errore.

