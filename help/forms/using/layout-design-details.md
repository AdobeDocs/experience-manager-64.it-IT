---
title: Progettazione layout
seo-title: Progettazione layout
description: In Dettagli progettazione layout viene illustrato come creare layout da utilizzare per le lettere o per le comunicazioni interattive.
seo-description: In Dettagli progettazione layout viene illustrato come creare layout da utilizzare per le lettere o per le comunicazioni interattive.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# Progettazione layout {#layout-design}

I modelli di modulo XFA o XDP sono i modelli per:

* [Lettere](/help/forms/using/create-letter.md)
* [Canale](/help/forms/using/web-channel-print-channel.md#printchannel) di stampa delle comunicazioni [interattive](/help/forms/using/interactive-communications-overview.md)

* Frammenti di layout

Un XDP è progettato in Adobe Forms Designer. Questo articolo fornisce dettagli su come progettare i file XDP per la creazione di corrispondenze/comunicazioni interattive efficaci, ad esempio dove utilizzare i campi del modulo o le aree di destinazione e quando utilizzare i frammenti di layout.

## Creazione di un layout per le lettere o per il canale di stampa di Interactive Communications {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Un layout definisce il layout grafico di un canale lettera/stampa di una comunicazione interattiva. Il layout può contenere campi modulo tipici come &quot;Indirizzo&quot; e &quot;Numero di riferimento&quot;. Contiene inoltre sottomoduli vuoti che indicano le aree di destinazione. Crea il layout nella finestra di progettazione del modulo e, al termine, lo specialista dell’applicazione lo carica nel server AEM. Da qui potete selezionare il layout quando create un modello di corrispondenza o un canale di stampa di una comunicazione interattiva.

![Designer: creare un layout](assets/claimsubrogationlayout.png)

Per creare layout per lettere/canale di stampa delle comunicazioni interattive, effettuate le seguenti operazioni:

1. Analizzare il layout e determinare il contenuto da ripetere su tutte le pagine; in genere l&#39;intestazione e il piè di pagina rientrano in questa categoria. Questo contenuto viene inserito nelle pagine master del layout. Il contenuto rimanente va alle pagine corpo del layout. In una giacca dei criteri, il logo e l&#39;indirizzo della società possono essere aggiunti all&#39;intestazione e al piè di pagina della pagina master. Ad esempio, Avviso di annullamento utilizza lo stesso layout.
1. Durante la progettazione delle pagine corpo, suddividere il contenuto della pagina in sezioni. Ogni sezione è progettata come un sottomodulo incorporato nel layout stesso o come layout di frammento. Se la sezione contiene una tabella, modellare la sezione come un frammento di layout.
1. Un layout può essere progettato come segue:

   1. Creare ogni sezione come sottomodulo separato contenente tutti gli elementi della sezione.
   1. Rendere ogni sottomodulo di sezione secondario dello stesso sottomodulo principale. Il layout del sottomodulo principale è impostato in modo da consentire lo spostamento verso il basso delle sezioni nel caso in cui dati di grandi dimensioni vengano uniti nelle sezioni precedenti.
   1. La residenza principale sezione può essere riutilizzata anche in altri layout. Crea come layout di frammento.
   1. Sezione I dettagli di interesse aggiuntivi contengono solo due elementi posizionati uno sotto l&#39;altro, possono contenere dati di grandi dimensioni ed è progettato come flusso.
   1. Altre sezioni contengono elementi in posizioni specifiche, in modo che siano progettati come layout posizionato.
   1. Suddividere una sezione in sottomoduli se la sezione contiene elementi in posizioni specifiche e questi elementi contengono grandi quantità di dati. Disporre quindi i sottomoduli per ottenere il comportamento desiderato.
   1. Per la sezione Residenza principale, aggiungere un&#39;area di destinazione segnaposto. Questo segnaposto è associato al frammento Residenza principale al momento della progettazione Lettera/Comunicazione interattiva.
   1. Caricate il layout (e l&#39;eventuale frammento che utilizza il layout) nel server AEM Forms.

## Uso dello schema {#using-schema}

È possibile utilizzare uno schema in un layout o in un frammento di layout, ma non è obbligatorio. Se utilizzate uno schema, accertatevi di quanto segue:

1. Il layout e tutti i layout di frammento utilizzati in una lettera/comunicazione interattiva utilizzano lo stesso schema utilizzato per la comunicazione lettera/interattiva.
1. Tutti i campi necessari per essere compilati con i dati sono associati allo schema.

## Creazione di campi correlati {#creating-relatable-fields}

Per impostazione predefinita, tutti i campi sono considerati correlati a varie altre origini dati. Se il layout contiene campi che non possono essere correlati a un&#39;origine dati, assegnare al campo un nome con suffisso &quot;_int&quot; (interno); ad esempio, pageCount_int.

Un campo relativo deve:

* essere un XFA &lt;field> o &lt;exclGroup>
* avere un riferimento di binding XFA
* se è un &lt;exclGroup>, deve avere almeno un campo pulsante di scelta figlio; in caso contrario, il relativo tipo di valore non può essere determinato

Un campo relativo deve:

* avere un nome

Un campo relativo non può:

* Includere un suffisso &quot;_int&quot; nel nome
* con binding impostato su &quot;none&quot;
* essere figlio di un elemento &lt;exclGroup>

Fintanto che un campo relativo soddisfa i criteri sopra descritti, può trovarsi in qualsiasi posizione e a qualsiasi profondità di nidificazione nel layout. È possibile utilizzare campi correlati all&#39;interno delle pagine master.

I campi sono più flessibili nella configurazione del layout rispetto ai sottomoduli dell&#39;area di destinazione; tuttavia sono legati a un singolo tipo di valore. È possibile impostare un campo di grandi dimensioni o su larghezza, altezza e così via. Il risultato risolto del modulo o della regola viene inserito nel campo.

## Definizione di quando utilizzare sottomoduli e campi di testo {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Utilizzare un sottomodulo se si desidera acquisire più contenuto del modulo in un layout verticale con scorrimento dall&#39;alto verso il basso (più paragrafi o immagini). Il layout deve gestire l&#39;aumento dell&#39;altezza del sottomodulo per adattarlo al contenuto. Se non si può essere certi che la lunghezza del contenuto associato al sottomodulo o alla destinazione non superi mai lo spazio riservato al sottomodulo nel layout, creare il sottomodulo come elemento secondario all&#39;interno di un contenitore di sottomoduli scorrevole. Questo processo assicura che gli oggetti layout sotto il sottomodulo scorrano verso il basso man mano che il sottomodulo cresce.

Utilizzare un campo se si desidera acquisire i dati del modulo o dei dati del dizionario dati nello schema del layout (in quanto i campi sono associati ai dati) o per visualizzare il contenuto del modulo in una pagina master. Tenere presente che il contenuto di una pagina master non può fluire con il contenuto della pagina corpo, pertanto è necessario assicurarsi che il campo immagine sia utilizzato come logo intestazione. Questa tabella fornisce ulteriori criteri per decidere quando utilizzare un sottomodulo o un campo in un layout.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Utilizzare un sottomodulo quando</strong></p> </td> 
   <td><p><strong>Utilizzare un campo di testo quando</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Contiene una combinazione di elementi, ad esempio Cognome e Nome</p> </td> 
   <td><p>Contiene un singolo elemento, ad esempio un numero di criterio.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Include più paragrafi</p> </td> 
   <td><p>Il testo è racchiuso e giustificato</p> </td> 
  </tr> 
  <tr> 
   <td><p>I gruppi di dati ripetuti, facoltativi e condizionali sono associati a sottomoduli, per ridurre il rischio di errori di progettazione che potrebbero verificarsi se gli script vengono utilizzati per ottenere gli stessi risultati</p> </td> 
   <td><p>Elementi quali il logo e l'indirizzo dell'azienda vengono visualizzati su tutte le pagine di una lettera o comunicazione interattiva. In questo caso, creare campi modulo per tali elementi e inserirli nella pagina master. Se si imposta il binding dei campi su "Nessuno", i campi no vengono visualizzati come campi correlati nell'Editor di comunicazione interattiva/Lettera. Se si desidera collegare un certo tipo di contenuto a questi campi, è necessario che il binding sia associato.</p> <p>Se l'indirizzo della società contiene più righe di dati, utilizzare il campo di testo con l'opzione "Consenti righe multiple" per rappresentare l'indirizzo nel layout.</p> <p>Se il tipo di dati di un campo di testo è impostato su testo normale, viene utilizzata la versione in testo normale dell'output del modulo invece della versione in formato RTF (tutta la formattazione viene scartata). Per mantenere la formattazione, impostare il tipo di dati del campo di testo su RTF.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Il testo è scorrevole</p> </td> 
   <td><p>I campi di testo e i campi immagine vengono utilizzati nelle pagine master. Le pagine master non possono utilizzare i sottomoduli come aree di destinazione.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Gli oggetti sono raggruppati e organizzati senza eseguire il binding del sottomodulo con un elemento dati</p> </td> 
   <td><p> </p> </td> 
  </tr> 
  <tr> 
   <td><p>All'interno del sottomodulo è presente un campo di testo. Il sottomodulo può espandersi e non sovrascrivere gli altri oggetti sottostanti sul layout.</p> </td> 
   <td><p>È necessario un facile accesso ai relativi dati nel processo di pubblicazione.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Impostazione di elementi ripetitivi {#setting-up-repetitive-elements}

Quando elementi come il logo e l&#39;indirizzo dell&#39;organizzazione vengono visualizzati su tutte le pagine di una lettera o comunicazione interattiva, create campi modulo per tali elementi e inseriteli nella pagina master. Usa binding Nome (Nome campo) per questi campi.

## Specificare il formato di rendering del server {#specify-the-server-nbsp-render-format}

Utilizzare il formato di rendering del server del layout su Modulo XML dinamico; in caso contrario, il rendering di lettere/comunicazioni interattive basate su questo layout non può essere eseguito correttamente. Per impostazione predefinita, in Forms Designer il formato di rendering del server è impostato su Modulo XML dinamico. Per verificare di utilizzare il formato corretto:

* In Designer, fare clic su **[!UICONTROL File > Proprietà modulo > Predefinito]** e assicurarsi che l&#39;impostazione Rendering/Formato PDF sia impostata su Modulo XML dinamico.

