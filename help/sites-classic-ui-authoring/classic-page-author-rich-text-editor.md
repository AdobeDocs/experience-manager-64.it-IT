---
title: Editor Rich Text
seo-title: Rich Text Editor
description: L’editor Rich Text è un componente di base per l’inserimento di contenuti di testo in AEM.
seo-description: The Rich Text Editor is a basic building block for inputting textual content into AEM.
uuid: 42001071-f7a7-475d-8aab-a8054303db68
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: adc697e1-4a1c-4985-8690-79ed77736fec
exl-id: 44cd0092-de40-4a72-a682-1e8f5906b2e5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1832'
ht-degree: 3%

---

# Editor Rich Text{#rich-text-editor}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’editor Rich Text è un componente di base per l’inserimento di contenuti di testo in AEM. Costituisce la base di vari componenti, tra cui:

* Testo
* Testo e immagine
* Tabella

## Editor Rich Text {#rich-text-editor-2}

La finestra di dialogo di modifica WYSIWYG fornisce un’ampia gamma di funzionalità:

![cq55_rte_basicchars](assets/cq55_rte_basicchars.png)

>[!NOTE]
>
>Le funzioni disponibili possono essere configurate per i singoli progetti, pertanto potrebbero variare a seconda dell’installazione in uso.

## Modifica diretta {#in-place-editing}

Oltre alla modalità di modifica Rich Text basata su finestra di dialogo, AEM fornisce anche la modalità di modifica diretta, che consente di modificare direttamente il testo visualizzato nel layout della pagina.

Per accedere alla modalità di modifica locale, fai due volte clic su un paragrafo (doppio clic lento). Il bordo del componente diventa arancione.

È possibile modificare direttamente il testo sulla pagina, anziché all’interno di una finestra di dialogo. È sufficiente apportare le modifiche e verranno salvate automaticamente.

![cq55_rte_inlineediting](assets/cq55_rte_inlineediting.png)

>[!NOTE]
>
>Se è aperto Content Finder, nella parte superiore della scheda (come sopra) viene visualizzata una barra degli strumenti con le opzioni di formattazione dell’editor Rich Text.
>
>Se Content Finder non è aperto, la barra degli strumenti non verrà visualizzata.

Attualmente, la modalità di modifica locale è abilitata per gli elementi di pagina generati da **Testo** e **Titolo** componenti.

>[!NOTE]
>
>La **Titolo** Il componente è progettato per contenere un testo breve senza interruzioni di riga. Quando si modifica un titolo in modalità di modifica diretta, quando si immette un’interruzione di riga viene aperta una nuova **Testo** sotto il titolo.

## Funzioni dell’Editor Rich Text {#features-of-the-rich-text-editor}

L’Editor Rich Text fornisce una serie di funzioni: [dipende dalla configurazione](/help/sites-administering/rich-text-editor.md) del singolo componente. Le funzioni sono disponibili sia per l’interfaccia touch che per quella classica.

### Formati di carattere di base {#basic-character-formats}

![](do-not-localize/cq55_rte_basicchars.png)

Consente di applicare la formattazione ai caratteri selezionati (evidenziati); alcune opzioni dispongono anche di tasti di scelta rapida:

* Grassetto (Ctrl+B)
* Corsivo (Ctrl+I)
* Sottolineato (Ctrl+U)
* Pedice
* Apice

![cq55_rte_basicchars_use](assets/cq55_rte_basicchars_use.png)

Tutti funzionano come un interruttore, quindi la riselezione rimuoverà il formato.

### Stili e formati predefiniti {#predefined-styles-and-formats}

![cq55_rte_stylesparagrafo](assets/cq55_rte_stylesparagraph.png)

L’installazione può includere stili e formati predefiniti. Sono disponibili con **Stile** e **Formato** elenchi a discesa e possono essere applicati al testo selezionato.

Uno stile può essere applicato a una stringa specifica (lo stile è correlato ai CSS):

![cq55_rte_Styles_use](assets/cq55_rte_styles_use.png)

Un formato viene invece applicato all’intero paragrafo di testo (un formato è basato su HTML):

![cq55_rte_Paragraph_use](assets/cq55_rte_paragraph_use.png)

È possibile modificare solo un formato specifico (il formato predefinito è **Paragrafo**).

È possibile rimuovere uno stile; posizionare il cursore all’interno del testo a cui è stato applicato lo stile e fare clic sull’icona di rimozione:

>[!CAUTION]
>
>Non riselezionare il testo a cui è stato applicato lo stile oppure l’icona viene disattivata.

### Taglia, Copia, Incolla {#cut-copy-paste}

![](do-not-localize/cq55_rte_cutcopypaste.png)

Le funzioni standard di **Taglia** e **Copia** sono disponibili. Vari sapori di **Incolla** sono forniti per soddisfare i diversi formati.

* Taglia (**Ctrl-X**)
* Copia (**Ctrl+C**)
* Incolla

   Questo è il meccanismo di incolla predefinito (**Ctrl+V**) per il componente; quando installato out-of-the-box, è configurato come &quot;Incolla da Word&quot;.

* Incolla testo semplice

   Elimina tutti gli stili e la formattazione per incollare solo il testo normale.

* Incolla da Word

   Incolla il contenuto come HTML (eseguendo le operazioni di riformattazione necessarie).

### Annulla, Ripristina {#undo-redo}

![](do-not-localize/cq55_rte_undoredo.png)

AEM registra le ultime 50 azioni eseguite nel componente corrente, in ordine cronologico. Se necessario, queste azioni possono essere annullate (e successivamente ripristinate) in ordine preciso.

>[!CAUTION]
>
>La cronologia viene mantenuta solo per la sessione di modifica corrente. Viene riavviato ogni volta che si apre il componente per la modifica.

>[!NOTE]
>
>Il numero predefinito di attività è 50. L&#39;installazione potrebbe essere diversa.

### Allineamento {#alignment}

![](do-not-localize/cq55_rte_alignment.png)

Il testo può essere allineato a sinistra, al centro o a destra.

![cq55_rte_align_use](assets/cq55_rte_alignment_use.png)

### Rientro {#indentation}

![](do-not-localize/cq55_rte_indent.png)

È possibile aumentare o diminuire il rientro di un paragrafo. Il rientro viene applicato al paragrafo selezionato. Eventuale nuovo testo inserito mantiene il livello di rientro corrente.

![cq55_rte_rientro_use](assets/cq55_rte_indent_use.png)

### Elenchi {#lists}

![](do-not-localize/cq55_rte_lists.png)

All’interno del testo è possibile creare elenchi puntati e numerati. Selezionare il tipo di elenco e iniziare a digitare oppure evidenziare il testo da convertire. In entrambi i casi, un feed di riga avvierà una nuova voce dell’elenco.

È possibile creare elenchi nidificati applicando un rientro a una o più voci dell’elenco.

Per modificare lo stile di un elenco, posiziona il cursore all’interno dell’elenco e seleziona l’altro stile. Un sottoelenco può avere anche uno stile diverso da quello dell’elenco che lo contiene. Questo può essere applicato una volta creato il sottoelenco (tramite rientro).

![cq55_rte_lists_use](assets/cq55_rte_lists_use.png)

### Collegamenti {#links}

![](do-not-localize/cq55_rte_links.png)

Per generare un collegamento a un URL (all’interno o all’esterno del sito web), evidenzia il testo richiesto e fai clic sul pulsante **Collegamento ipertestuale** icona:

![](do-not-localize/chlimage_1-12.png)

Una finestra di dialogo consente di specificare l’URL di destinazione; anche se deve essere aperto in una nuova finestra.

![cq55_rte_link_use](assets/cq55_rte_link_use.png)

Operazioni disponibili:

* Digitare un URI direttamente
* utilizza la mappa del sito per selezionare una pagina all’interno del sito web
* immetti l’URI, quindi aggiungi l’ancoraggio di destinazione; ad esempio `www.TargetUri.org#AnchorName`
* immettere solo un ancoraggio (per fare riferimento alla pagina corrente); ad esempio `#anchor`
* cerca una pagina in Content Finder, quindi trascina e rilascia l’icona della pagina nella finestra di dialogo Collegamento ipertestuale

>[!NOTE]
>
>L’URI può essere preceduto da uno qualsiasi dei protocolli configurati per l’installazione. In un&#39;installazione standard questi sono `https://`, `ftp://`e `mailto:`. I protocolli non configurati per l’installazione in uso verranno rifiutati e contrassegnati come non validi.

Per interrompere il collegamento, posizionate il cursore all’interno del testo di collegamento e fate clic sul pulsante **Scollega** icona:

![](do-not-localize/chlimage_1-13.png)

### Ancoraggi {#anchors}

![](do-not-localize/cq55_rte_anchor.png)

Per creare un ancoraggio all’interno del testo, posizionate il cursore nel testo o selezionate parte del testo. Quindi fai clic sul pulsante **Ancoraggio** per aprire la finestra di dialogo.

Inserisci il nome dell’ancoraggio e fai clic su **OK** da salvare.

![cq55_rte_anchor_use](assets/cq55_rte_anchor_use.png)

L’ancoraggio viene visualizzato quando il componente viene modificato e può essere utilizzato all’interno di una destinazione per i collegamenti.

![chlimage_1-145](assets/chlimage_1-145.png)

### Trova e sostituisci {#find-and-replace}

![](do-not-localize/cq55_rte_findreplace.png)

AEM fornisce entrambe **Trova** e **Sostituisci** (trova e sostituisci).

Entrambi hanno un **Trova successivo** per cercare il testo specificato nel componente aperto. È inoltre possibile specificare la corrispondenza tra maiuscole e minuscole.

La ricerca inizia sempre dalla posizione corrente del cursore all’interno del testo. Una volta raggiunta la fine del componente, viene visualizzato un messaggio per informare l’utente che l’operazione di ricerca successiva inizierà dall’alto.

![cq55_rte_find_use](assets/cq55_rte_find_use.png)

La **Sostituisci** consente di: **Trova**, quindi **Sostituisci** una singola istanza con il testo specificato, oppure **Sostituisci tutto** nel componente corrente.

![cq55_rte_findreplace_use](assets/cq55_rte_findreplace_use.png)

### Immagini {#images}

È possibile trascinare le immagini da Content Finder per aggiungerle al testo.

![cq55_rte_image_use](assets/cq55_rte_image_use.png)

>[!NOTE]
>
>AEM inoltre offre componenti specializzati per una configurazione più dettagliata delle immagini. Ad esempio, **Immagine** e **Immagine testo** sono disponibili i componenti .

### Controllo ortografia {#spelling-checker}

![](do-not-localize/cq55_rte_spellchecker.png)

Il correttore ortografico controlla tutto il testo nel componente corrente.

Eventuali errori di ortografia vengono evidenziati:

![cq55_rte_spellchecker_use](assets/cq55_rte_spellchecker_use.png)

>[!NOTE]
>
>Il correttore ortografico funziona nella lingua del sito web, scegliendo la proprietà language della struttura secondaria o estraendo la lingua dall’URL. Ad esempio, `en` il ramo sarà controllato per inglese e `de` per il tedesco.

### Tabelle {#tables}

Le tabelle sono disponibili:

* Come **Tabella** component

   ![chlimage_1-146](assets/chlimage_1-146.png)

* Da all’interno di **Testo** component

   ![](do-not-localize/chlimage_1-14.png)

   >[!NOTE]
   >
   >Anche se le tabelle sono disponibili nell’editor Rich Text, si consiglia di utilizzare la variabile **Tabella** durante la creazione di tabelle.

In entrambi i casi **Testo** e **Tabella** la funzionalità della tabella dei componenti è disponibile tramite il menu di scelta rapida, solitamente il pulsante destro del mouse, selezionato all’interno della tabella; ad esempio:

![cq55_rte_Tablemenu](assets/cq55_rte_tablemenu.png)

>[!NOTE]
>
>In **Tabella** è disponibile anche una barra degli strumenti specializzata, che include varie funzioni standard dell’editor Rich Text e un sottoinsieme delle funzioni specifiche della tabella.

Le funzioni specifiche della tabella sono:

<table> 
 <tbody> 
  <tr> 
   <td><a href="#table-properties">Proprietà tabella</a><br /> </td> 
  </tr> 
  <tr> 
   <td><a href="#cell-properties">Proprietà cella<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-rows">Aggiungi/Elimina righe<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-columns">Aggiungi/Elimina colonne<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#selecting-entire-rows-or-columns">Selezione di righe o colonne intere<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#merge-cells">Unisci celle<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#split-cells">Dividi celle<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#creating-nested-tables">Tabelle nidificate</a></td> 
  </tr> 
  <tr> 
   <td><a href="#remove-table">Rimuovi tabella</a> </td> 
  </tr> 
 </tbody> 
</table>

#### Proprietà tabella {#table-properties}

![cq55_rte_tableproperties_icon](assets/cq55_rte_tableproperties_icon.png)

È possibile configurare le proprietà di base della tabella prima di fare clic su **OK** per salvare:

![cq55_rte_tableproperties_dialog](assets/cq55_rte_tableproperties_dialog.png)

* **Larghezza**

   Larghezza totale della tabella.

* **Altezza**

   Altezza totale della tabella.

* **Bordo**

   Dimensione del bordo della tabella.

* **Margine celle**

   Definisce lo spazio vuoto tra il contenuto di una cella e i relativi bordi.

* **Spaziatura celle**

   Definisce la distanza tra le celle.

>[!NOTE]
>
>**Larghezza**, **Altezza** e alcune proprietà delle celle possono essere definite in:
>
>* pixel
>* percentuali


>[!CAUTION]
>
>L’Adobe consiglia vivamente di definire un **Larghezza** per il tuo tavolo.

#### Proprietà cella {#cell-properties}

![cq55_rte_cellproperties_icon](assets/cq55_rte_cellproperties_icon.png)

È possibile configurare le proprietà di una cella o di una serie di celle specifiche:

![cq55_rte_cellproperties_dialog](assets/cq55_rte_cellproperties_dialog.png)

* **Larghezza**
* **Altezza**
* **Allineamento orizzontale** - A sinistra, Centro o A destra
* **Allineamento verticale** - In alto, In mezzo, In basso o Linea di base
* **Tipo di cella** - Dati o intestazione
* **Applica a:**
   * Cella singola
   * Riga intera
   * Colonna intera

#### Aggiungi/Elimina righe {#add-or-delete-rows}

![cq55_rte_rows](assets/cq55_rte_rows.png)

Le righe possono essere aggiunte sopra o sotto la riga corrente.

È inoltre possibile eliminare la riga corrente.

#### Aggiungi/Elimina colonne {#add-or-delete-columns}

![cq55_rte_columns](assets/cq55_rte_columns.png)

Le colonne possono essere aggiunte a sinistra o a destra della colonna corrente.

È inoltre possibile eliminare la colonna corrente.

#### Selezione di righe o colonne intere {#selecting-entire-rows-or-columns}

![chlimage_1-147](assets/chlimage_1-147.png)

Seleziona l’intera riga o colonna corrente. Sono quindi disponibili azioni specifiche (ad esempio l’unione).

#### Unisci celle {#merge-cells}

![cq55_rte_cellmerge](assets/cq55_rte_cellmerge.png) ![cq55_rte_cellmerge-1](assets/cq55_rte_cellmerge-1.png)

* Se è stato selezionato un gruppo di celle, è possibile unirle in un unico gruppo.
* Se è selezionata una sola cella, è possibile unirla con la cella a destra o sotto.

#### Dividi celle {#split-cells}

![cq55_rte_cellsplit](assets/cq55_rte_cellsplit.png)

Selezionare una singola cella per dividerla:

* Se si divide una cella in orizzontale, viene generata una nuova cella a destra della cella corrente, all’interno della colonna corrente.
* Se si divide una cella in verticale, viene generata una nuova cella sotto la cella corrente, ma all’interno della riga corrente.

#### Creazione di tabelle nidificate {#creating-nested-tables}

![chlimage_1-148](assets/chlimage_1-148.png)

La creazione di una tabella nidificata creerà una nuova tabella indipendente all’interno della cella corrente.

>[!NOTE]
>
>Alcuni comportamenti aggiuntivi dipendono dal browser:
>
>* IE di Windows: Per selezionare più celle, premi Ctrl+clic con il pulsante principale del mouse (in genere il sinistro).
>* Firefox: Trascinare il mouse per selezionare un intervallo di celle.
>


#### Rimuovi tabella {#remove-table}

![cq55_rte_remove](assets/cq55_rte_removetable.png)

In questo modo la tabella verrà rimossa dall’interno della **Testo** componente.

### Caratteri speciali {#special-characters}

![](do-not-localize/cq55_rte_specialchars.png)

È possibile rendere disponibili caratteri speciali all’editor Rich Text; possono variare a seconda dell’installazione.

![cq55_rte_specialchars_use](assets/cq55_rte_specialchars_use.png)

Passa il mouse per visualizzare una versione ingrandita del carattere, quindi fai clic per includerlo nella posizione corrente nel testo.

### Modalità di modifica sorgente {#source-editing-mode}

![](do-not-localize/cq55_rte_sourceedit.png)

La modalità di modifica sorgente consente di visualizzare e modificare il HTML sottostante del componente.

Ecco il testo:

![cq55_rte_sourcemode_1](assets/cq55_rte_sourcemode_1.png)

avrà l’aspetto seguente nella modalità sorgente (spesso l’origine è molto più lunga, quindi dovrai scorrere):

![cq55_rte_sourcemode_2](assets/cq55_rte_sourcemode_2.png)

>[!CAUTION]
>
>Quando si esce dalla modalità di origine, AEM effettua alcuni controlli di convalida, ad esempio per verificare che il testo sia correttamente contenuto o nidificato nei blocchi. Questo può comportare modifiche alle modifiche apportate.
