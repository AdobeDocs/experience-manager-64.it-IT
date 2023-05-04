---
title: Progettazione layout
seo-title: Layout Design
description: Dettagli progettazione layout spiega come creare layout da utilizzare per le lettere o le comunicazioni interattive.
seo-description: Layout Design Details explains how you can create layouts to be used for your letters or Interactive Communications.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
feature: Correspondence Management
exl-id: 92f90e7f-2869-4201-a927-47de1fc08f5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 0%

---

# Progettazione layout {#layout-design}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I modelli di modulo XFA o XDP sono i modelli per:

* [Lettere](/help/forms/using/create-letter.md)
* [Canale di stampa](/help/forms/using/web-channel-print-channel.md#printchannel) di [Comunicazioni interattive](/help/forms/using/interactive-communications-overview.md)

* Frammenti di layout

Un XDP è progettato in Adobe Forms Designer. Questo articolo fornisce dettagli su come progettare XDP per creare corrispondenze/comunicazioni interattive efficaci, ad esempio dove utilizzare i campi del modulo o le aree di destinazione e quando utilizzare i frammenti di layout.

## Creazione di un layout per le lettere o per il canale di stampa delle comunicazioni interattive {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Un layout definisce il layout grafico di un canale lettera/stampa di una comunicazione interattiva. Il layout può contenere campi modulo tipici, ad esempio &quot;Indirizzo&quot; e &quot;Numero di riferimento&quot;. Contiene inoltre sottomoduli vuoti che indicano le aree di destinazione. Crea il layout in form designer e, una volta completato, lo specialista dell&#39;applicazione lo carica AEM server. Da lì è possibile selezionare il layout quando si crea un modello di corrispondenza o un canale di stampa di una comunicazione interattiva.

![Designer: creare un layout](assets/claimsubrogationlayout.png)

Segui questi passaggi per creare layout per lettere/canale di stampa delle comunicazioni interattive:

1. Analizzare il layout e determinare il contenuto che viene ripetuto su tutte le pagine; in genere l’intestazione e il piè di pagina rientrano in questa categoria. Questo contenuto viene inserito nelle pagine master di layout. Il contenuto rimanente viene indirizzato alle pagine corpo del layout. In una giacca di criterio, il logo e l’indirizzo dell’azienda possono essere aggiunti all’intestazione e al piè di pagina della pagina master. Ad esempio, Avviso di annullamento utilizza lo stesso layout.
1. Durante la progettazione delle pagine corpo, suddividi il contenuto della pagina in sezioni. Ciascuna sezione è progettata come un sottomodulo incorporato nel layout stesso o come layout di frammento. Se la sezione contiene una tabella, modellare la sezione come frammento di layout.
1. Un Layout può essere progettato come segue:

   1. Creare ogni sezione come sottomodulo separato contenente tutti gli elementi della sezione.
   1. Creare un sottomodulo di sezione secondario dello stesso sottomodulo principale. Il layout del sottomodulo principale è impostato in modo da consentire lo scorrimento verso il basso delle sezioni nel caso di dati di grandi dimensioni che vengono uniti nelle sezioni precedenti.
   1. Sezione residenza primaria può essere riutilizzato anche in altri layout. Crea come layout di frammento.
   1. Sezione Ulteriori dettagli di interesse contengono solo due elementi posizionati uno sotto l&#39;altro, possono contenere dati di grandi dimensioni ed è progettato come flusso.
   1. Altre sezioni contengono elementi in posizioni specifiche in modo che siano progettati come layout posizionato.
   1. Suddividi una sezione in sottomoduli se la sezione contiene elementi in posizioni specifiche e questi elementi contengono grandi quantità di dati. Quindi, disporre i sottomoduli per ottenere il comportamento desiderato.
   1. Per la sezione Residenza principale, aggiungere un&#39;area di destinazione segnaposto. Questo segnaposto è destinato a frammentare la residenza primaria al momento della progettazione della lettera/comunicazione interattiva.
   1. Carica il layout (e l’eventuale frammento che utilizza il layout) nel server AEM Forms.

## Utilizzo dello schema {#using-schema}

È possibile utilizzare uno schema in un frammento di layout o di layout , ma non è obbligatorio. Se utilizzi uno schema, verifica quanto segue:

1. Il layout e tutti i layout di frammento utilizzati in una comunicazione lettera/interattiva utilizzano lo stesso schema della comunicazione lettera/interattiva.
1. Tutti i campi necessari per essere compilati con i dati sono associati allo schema.

## Creazione di campi correlati {#creating-relatable-fields}

Per impostazione predefinita, tutti i campi sono considerati correlati a varie altre origini dati. Se il layout contiene campi che non sono correlati a un’origine dati, denominare il campo con un suffisso &quot;_int&quot; (interno); ad esempio, pageCount_int.

Un campo relativo deve:

* essere un XFA &lt;field> o &lt;exclgroup>
* dispongono di un riferimento di binding XFA
* se &lt;exclgroup>, deve avere almeno un campo pulsante di scelta figlio; in caso contrario, non è possibile determinare il relativo tipo di valore

Un campo relativo deve:

* hanno un nome

Un campo relativo non deve:

* Includi un suffisso &quot;_int&quot; nel nome
* hanno un binding impostato come &quot;none&quot;
* essere figlio di un &lt;exclgroup> elemento

Se un campo relativo soddisfa i criteri sopra descritti, può trovarsi in qualsiasi posizione e a qualsiasi profondità di nidificazione nel layout. È possibile utilizzare campi correlati all’interno delle pagine master.

I campi sono più flessibili nella configurazione del layout rispetto ai sottomoduli dell’area di destinazione; tuttavia sono legati a un singolo tipo di valore. È possibile ingrandire un campo oppure impostarlo su una larghezza e un&#39;altezza fisse e così via. Il risultato del modulo o della regola risolti viene inviato nel campo .

## Decidere quando utilizzare sottomoduli e campi di testo {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Utilizzare un sottomodulo se si desidera acquisire più contenuti del modulo in un layout verticale dall’alto verso il basso (più paragrafi o immagini). Il layout deve gestire l’aumento dell’altezza del sottomodulo per adattarne il contenuto. Se non si può essere certi che la lunghezza del contenuto associato al sottomodulo o alla destinazione non superi mai lo spazio riservato al sottomodulo nel layout, creare il sottomodulo come elemento secondario all’interno di un contenitore di sottomoduli scorrevole. Questo processo assicura che gli oggetti layout al di sotto del sottomodulo scorrano verso il basso man mano che il sottomodulo cresce.

Utilizzare un campo se si desidera acquisire i dati del modulo o i dati degli elementi del dizionario dati nello schema del layout (in quanto i campi sono associati ai dati) o per visualizzare il contenuto del modulo in una pagina master. Tenere presente che il contenuto di una pagina master non può fluire con il contenuto della pagina corpo, pertanto è necessario assicurarsi che il campo immagine sia utilizzato come logo intestazione. Questa tabella fornisce ulteriori criteri per decidere quando utilizzare un sottomodulo o un campo in un layout.

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
   <td><p>I gruppi di dati ripetuti, facoltativi e condizionali sono associati a sottomoduli, per ridurre il rischio di errori di progettazione che possono verificarsi se vengono utilizzati script per ottenere gli stessi risultati</p> </td> 
   <td><p>Elementi come il logo e l’indirizzo dell’organizzazione vengono visualizzati su tutte le pagine di una lettera/comunicazione interattiva. In questo caso, creare campi modulo per tali elementi e inserirli nella pagina master. Se si imposta il binding dei campi su "Nessun binding dei dati", i campi nessun vengono visualizzati come campi correlati nell’Editor di comunicazione interattiva/Lettera. Se si desidera associare un certo tipo di contenuto a questi campi, è necessario che il binding sia impostato su .</p> <p>Se l'indirizzo dell'azienda contiene più di una riga di dati, utilizzare il campo di testo con l'opzione "Consenti righe multiple" per rappresentare l'indirizzo nel layout.</p> <p>Se il tipo di dati di un campo di testo è impostato su testo normale, viene utilizzata la versione di testo normale dell’output del modulo invece della versione RTF (tutta la formattazione viene scartata). Per mantenere la formattazione, impostare il tipo di dati del campo di testo su RTF.</p> </td> 
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
   <td><p>All’interno del sottomodulo è presente un campo di testo. Il sottomodulo può espandersi e non sovrascrivere gli altri oggetti sottostanti al layout.</p> </td> 
   <td><p>È necessario un facile accesso ai suoi dati nel processo di post-produzione.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Impostazione di elementi ripetitivi {#setting-up-repetitive-elements}

Quando elementi quali il logo e l’indirizzo dell’organizzazione vengono visualizzati su tutte le pagine di una lettera/comunicazione interattiva, creare campi modulo per tali elementi e inserirli nella pagina master. Utilizzare il binding Nome (Nome campo) per questi campi.

## Specifica il formato di rendering del server {#specify-the-server-nbsp-render-format}

Utilizzare il formato di rendering del server del layout nel modulo XML dinamico; in caso contrario, non sarà possibile eseguire correttamente il rendering di lettere/comunicazioni interattive basate su questo layout. Per impostazione predefinita, il formato di rendering del server in Forms Designer è impostato su Modulo XML dinamico. Per assicurarti di utilizzare il formato corretto:

* In Designer, fai clic su **[!UICONTROL File > Proprietà modulo > Predefinito]** e assicurarsi che l&#39;impostazione PDF Render/Format sia impostata su Modulo XML dinamico.
