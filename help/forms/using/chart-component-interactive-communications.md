---
title: Utilizzo dei grafici nelle comunicazioni interattive
seo-title: Chart component in Interactive Communications
description: Utilizzando i grafici di una comunicazione interattiva, è possibile condensare grandi quantità di informazioni in un formato visivo facile da analizzare e comprendere
seo-description: AEM Forms provides a chart component that you can use to create charts in your Interactive Communication. This document explains basic and agent configurations of the chart component.
uuid: dedd670c-030b-4497-bbcb-3ad935cebcda
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications
discoiquuid: 16c7e698-258d-4e63-9828-f538dc7d3294
feature: Interactive Communication
exl-id: 99077042-cba9-4429-b1e0-830739de5939
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2426'
ht-degree: 0%

---

# Utilizzo dei grafici nelle comunicazioni interattive {#using-charts-in-interactive-communications}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Utilizzando i grafici di una comunicazione interattiva, è possibile condensare grandi quantità di informazioni in un formato visivo facile da analizzare e comprendere

Un grafico o un grafico è una rappresentazione visiva dei dati. Condensa grandi quantità di informazioni in formato visivo facile da comprendere, consentendo ai destinatari della comunicazione interattiva di visualizzare, interpretare e analizzare meglio i dati complessi.

Durante la creazione di una comunicazione interattiva, è possibile aggiungere grafici per rappresentare visivamente dati bidimensionali dal modello di dati del modulo della comunicazione interattiva. Il componente Grafico consente di aggiungere e configurare i seguenti tipi di grafici:

* Torta
* Colonna
* Anello
* Barra (solo canale Web)
* Line
* Linea e punto
* Punto
* Area

## Aggiunta e configurazione di grafici in una comunicazione interattiva {#add-and-configure-chart-in-an-interactive-communication}

Per aggiungere un grafico a una comunicazione interattiva, completa i passaggi seguenti:

1. Dalla barra laterale AEM Componenti , trascina e rilascia il componente Grafico in uno dei seguenti canali di stampa o web di una comunicazione interattiva:

   * Canale di stampa: Area di destinazione e campo immagine
   * Canale Web: Area del pannello e di Target

   Il componente Grafico rilasciato crea un segnaposto per un grafico.

1. Tocca il componente grafico nell’editor delle comunicazioni interattive e, dalla barra degli strumenti del componente, seleziona **[!UICONTROL Configura (]** ![configure_icon](assets/configure_icon.png)).

   Viene visualizzata la barra laterale delle proprietà con le proprietà Base del grafico attivo.

   ![Proprietà di base di un grafico a linee nel canale di stampa](assets/chart_basicproperties.png)
   **Figura:** *Proprietà di base di un grafico a linee nel canale di stampa*

   ![Proprietà di base di un grafico a linee nel canale web](assets/basicpropertieswebchannel.png)
   **Figura:** *Proprietà di base di un grafico a linee nel canale web*

1. Configura le proprietà di base del grafico per il canale di stampa e il canale web. Oltre alle proprietà comuni, esistono proprietà specifiche per la stampa e il canale web e il tipo di grafico.

   * **[!UICONTROL Nome]**: Nome dell&#39;oggetto grafico. Il nome del grafico specificato non viene visualizzato nell&#39;output del grafico, ma viene utilizzato nelle regole per fare riferimento al grafico.
   * **[!UICONTROL Tipo di grafico]**: Specifica il tipo di grafico: Torta, Colonna, Anello, Linea, Linea e Punto, Punto o Area.
   * **[!UICONTROL Nascondi oggetto]**: Selezionare questa opzione per nascondere il grafico nell&#39;output finale.
   * Specifica quanto segue per **[!UICONTROL asse x]** e **[!UICONTROL asse y]**:

      * **[!UICONTROL Titolo]**: Specifica i titoli degli assi X e Y da visualizzare nella comunicazione interattiva.
      * **[!UICONTROL Oggetto del modello dati *]**: Sfogliare e selezionare gli oggetti modello dati per l’asse X e Y del grafico dal modello dati del modulo specificato durante la creazione della comunicazione interattiva. Scegliere due proprietà di tipo raccolta/matrice dello stesso oggetto del modello dati padre significative l&#39;una rispetto all&#39;altra per eseguire il grafico sull&#39;asse X e Y di un grafico.
      * **[!UICONTROL Funzione]**: Per utilizzare le funzioni statistiche per calcolare i valori sull&#39;asse, selezionare la funzione per l&#39;asse X/Y. Per ulteriori informazioni sulle funzioni, consulta [Usa funzioni nel grafico](#usefunction) e [Esempio 2: Applicazione delle funzioni di somma e media in un grafico a linee](#applicationsumfrequency).

   >[!NOTE]
   >
   >Per il canale di stampa, sull&#39;asse X, l&#39;oggetto modello dati associato deve essere di tipo Numero, Stringa o Data. Sull&#39;asse Y l&#39;oggetto del modello dati associato deve essere di tipo Number. Si consiglia di utilizzare la legenda sul lato destro nel canale di stampa.

   Per ulteriori informazioni sulle proprietà del grafico, consulta [Proprietà di base nei grafici](#basicpropertiescharts).

1. (Solo canale di stampa) In Impostazioni agente specificare se è obbligatorio per l&#39;agente utilizzare questo grafico. Se **[!UICONTROL È obbligatorio per l&#39;agente utilizzare questo grafico]** L’opzione non è selezionata, l’agente può toccare l’icona occhio del grafico nella scheda Contenuto dell’interfaccia utente dell’agente per mostrare/nascondere il grafico.

   ![Chart_agentproperties](assets/chart_agentproperties.png)

1. Nella barra laterale Proprietà, tocca ![done_icon](assets/done_icon.png).

   Anteprima per visualizzare l’aspetto e i dati del grafico. Se necessario, torna per riconfigurare le proprietà del grafico.

1. Torna a apportare altre modifiche nella comunicazione interattiva.

## Esempio 1: Output grafico in stampa e web {#chartoutputprintweb}

Nella scheda Base è possibile definire il tipo di grafico, le proprietà del modello di dati del modulo di origine che contengono dati, le etichette da tracciare sull&#39;asse x e sull&#39;asse y del grafico ed eventualmente la funzione statistica per calcolare i valori per il grafico.

Comprendiamo in dettaglio le informazioni minime richieste nelle proprietà di base, con l&#39;aiuto di un estratto conto della carta di credito generato utilizzando una comunicazione interattiva. Tenere presente che si desidera generare un grafico per rappresentare la quantità di spese diverse nell&#39;istruzione. Utilizzare diversi tipi di grafici per la stampa e l&#39;output Web della comunicazione interattiva.

A questo scopo, devi specificare:

* **[!UICONTROL Tipo di grafico]** - in questo esempio, Colonna per il canale di stampa e Anello per il canale web
* **[!UICONTROL Oggetti del modello dati]** come origine per l&#39;asse X e Y del grafico - in questo esempio, Importo transazione per l&#39;asse X e Nome spesa per l&#39;asse Y
* **[!UICONTROL Titolo]** per l&#39;asse X e Y (per il grafico a colonne nel canale di stampa solo in questo esempio) - in questo esempio, Importo ($) per l&#39;asse X e Spese per l&#39;asse Y.
* **[!UICONTROL Direzione etichetta]** (per Grafico a colonne solo nel canale di stampa in questo esempio) - in questo esempio `Tilt Left`

* **[!UICONTROL Descrizione comandi]** per visualizzare il mouse su una spesa (solo canale web) - in questo esempio `${x}: $ ${y}`, che viene visualizzato come `[Expense Label: $ Amount]` (Esempio: Visita del parco tematico: $ 315)

![Grafico a colonne nell’output di stampa di una comunicazione interattiva](assets/chartprintchannel.png)
**Figura:** *Grafico a colonne nell’output di stampa di una comunicazione interattiva*

**A.** Asse Y: importo recuperato dalla proprietà del modello dati del modulo e dalla proprietà Titolo impostata su Importo ($) **B.** Direzione etichetta dell&#39;asse X impostata su Inclinazione a sinistra **C.** Asse X: descrizione delle spese recuperata dalla proprietà del modello dati del modulo e dalla proprietà Titolo impostata su Spesa

![Grafico ad anello nell&#39;output web di una comunicazione interattiva](assets/chartwebchannel.png)
**Figura:** *Grafico ad anello nell&#39;output web di una comunicazione interattiva*

**A.** La proprietà Raggio interno della ciambella è impostata **B.** Mostra proprietà legenda selezionata e la proprietà Posizione legenda è impostata su Destra **C.** La descrizione comandi visualizza i dettagli dell&#39;elemento al passaggio del mouse. La descrizione comandi è impostata su ${x}: ${y}

## Esempio 2: Applicazione delle funzioni Somma e Frequenza in un grafico a linee {#applicationsumfrequency}

Applicando funzioni in un grafico, è possibile tracciare dati non forniti direttamente dal modello dati del modulo. In questo esempio, utilizziamo un esempio di rendiconto della carta di credito per comprendere come le funzioni Somma e Frequenza possono essere applicate al grafico.

![Grafico a linee senza funzione con tre transazioni &quot;Bed and Breakfast&quot;](assets/creditcarddatalinechartcopy.png)
**Figura:** *Grafico a linee senza funzione con tre transazioni &quot;Bed and Breakfast&quot;*

### Funzione Sum {#sum-function}

È possibile applicare la funzione sum per aggiungere valori di più istanze della stessa proprietà dati e visualizzarla una sola volta. Ad esempio, nel grafico seguente, la funzione Somma viene applicata sull&#39;asse Y per sommare l&#39;importo delle tre transazioni Bed and Breakfast ($99,45, $78 e $12) e mostrare una sola transazione ($189,45).

La funzione Somma può rendere il grafico più utile quando si desidera raccogliere e visualizzare la somma per molte istanze della stessa proprietà dati.

![creditcardchartsumfunzionioncopy](assets/creditcardchartsumfunctioncopy.png)

### Funzione di frequenza {#frequency-function}

La funzione Frequenza restituisce il numero di valori sull&#39;asse X o Y per un valore specificato sull&#39;altro asse. Con l&#39;applicazione della funzione Frequenza sull&#39;asse y (Importo/ImportoTransazione), il grafico mostra che ci sono state tre occorrenze di transazioni Bed and Breakfast e una occorrenza del resto dei tipi di transazioni.

![crecardchartfrequencyfunzionioncopy](assets/creditcardchartfrequencyfunctioncopy.png)

## Proprietà di base nei grafici {#basicpropertiescharts}

Nella scheda Base è possibile configurare le seguenti proprietà:

**Nome** Identificatore per l&#39;elemento grafico. Il nome non è visibile sul grafico, ma è utile quando si fa riferimento all’elemento da altri componenti, script ed espressioni SOM.

**Titolo (solo canale di stampa)** Specifica il titolo del grafico.

**Tipo di grafico** Specifica il tipo di grafico che si desidera generare. Le opzioni disponibili sono Torta, Colonna, Anello, Barre (solo canale web), Linea, Linea e Punto, Punto e Area. Per ulteriori informazioni, vedi l&#39;esempio 1: Output grafico in stampa e web.

**Asse X > Titolo** Specifica il titolo dell&#39;asse x.

**Asse X > Oggetto modello dati &amp;ast;** Specificare il nome dell&#39;elemento di raccolta del modello dati modulo da tracciare sull&#39;asse x.

**Asse X > Funzione** Specifica la funzione statistica/personalizzata da utilizzare per il calcolo dei valori sull&#39;asse x. Per ulteriori informazioni sulle funzioni, vedere Uso delle funzioni nel grafico e Esempio 2: Applicazione delle funzioni di somma e media in un grafico a linee.

**Asse X > Direzione etichetta** Direzione dell&#39;etichetta sul grafico nel canale di stampa. Se scegliete la direzione dell&#39;etichetta come Rotazione personalizzata, viene visualizzato il campo Angolo di rotazione personalizzato (gradi). Nel campo Angolo di rotazione personalizzato (gradi) è possibile scegliere l’angolo di rotazione in passaggi di 15 gradi.

**Asse Y > Titolo** Specifica il titolo dell&#39;asse y.

**Asse Y > Oggetto modello dati &amp;ast;** Specifica l&#39;elemento di raccolta del modello dati modulo da tracciare sull&#39;asse y. Nel canale Stampa, l&#39;oggetto modello dati per l&#39;asse Y deve essere di tipo Numero.

**Asse Y > Funzione** Specifica la funzione statistica/personalizzata da utilizzare per il calcolo dei valori sull&#39;asse y. Per ulteriori informazioni sulle funzioni, vedere Uso delle funzioni nel grafico e Esempio 2: Applicazione delle funzioni di somma e media in un grafico a linee.

**Mostra legenda** Mostra una legenda per il grafico a torta o ad anello quando è attivato.

**Posizione della legenda** Specifica la posizione della legenda rispetto al grafico. Le opzioni disponibili sono Destra, Sinistra, Superiore e Inferiore.

**Altezza (solo canale di stampa)** Altezza del grafico in pixel.

**Larghezza (solo canale di stampa)** Larghezza del grafico in pixel.

>[!NOTE]
>
>È possibile controllare la larghezza del grafico nel canale web utilizzando il livello di stile o applicando un tema.

**Tooltip (solo canale Web)** Specifica il formato in cui la descrizione comando viene visualizzata al passaggio del mouse su un punto dati del grafico nel canale Web. Il valore predefinito è \${x}(\${y}). A seconda del tipo di grafico, quando si posiziona il mouse su un punto, una barra o una sezione del grafico, le variabili \${x} e \${y} vengono sostituite dinamicamente con i valori corrispondenti sull&#39;asse x e sull&#39;asse y e visualizzate nella descrizione comando.

Per disattivare la descrizione comando, lasciare vuoto il campo Descrizione comando. Questa opzione non è applicabile ai grafici a linee e a superfici. Ad esempio, vedi [Esempio 1: Output grafico in stampa e web](#chartoutputprintweb).

**Classe CSS (solo canale web)** Specifica il nome di una classe CSS nel campo della classe CSS da applicare allo stile personalizzato al grafico.

**Interruzione di pagina obbligatoria prima (solo canale di stampa)** Selezionare questa opzione per aggiungere un’interruzione di pagina obbligatoria prima del grafico e posizionare il grafico sopra una nuova pagina.

**Interruzione di pagina obbligatoria dopo (solo canale di stampa)** Selezionare questa opzione per aggiungere un’interruzione di pagina obbligatoria dopo il grafico e inserire il contenuto che segue il grafico nella parte superiore di una nuova pagina.

**Rientro (solo canale di stampa)** Specifica il rientro del grafico a sinistra della pagina.

**Configurazioni specifiche del grafico** Oltre alle configurazioni comuni, sono disponibili le seguenti configurazioni specifiche per il grafico:

* **Raggio interno**: disponibili per i grafici ad anello per specificare il raggio (in pixel) del cerchio interno nel grafico.
* **Colore linea**: disponibili per i grafici a linee, a linee e a punti e ad area per specificare il valore esadecimale del colore della linea nel grafico.
* **Colore punto**: disponibili per i grafici Punto e Linea e Punto per specificare il valore esadecimale del colore per i punti del grafico.

* **Colore area**: disponibili per i grafici Area per specificare il valore esadecimale del colore per l’area sotto la linea del grafico.

## Usa funzioni nel grafico {#usefunction}

È possibile configurare un grafico in modo da utilizzare le funzioni statistiche per calcolare i valori dei dati di origine per il grafico. Applicando funzioni in un grafico, è possibile tracciare dati non forniti direttamente dal modello dati del modulo.

Mentre il componente Grafico include alcune funzioni integrate, è possibile scrivere le proprie funzioni e renderle disponibili per l&#39;uso nella configurazione del grafico nel canale Web.

![grafico funzionale](assets/functionchart.png)

>[!NOTE]
>
>È possibile utilizzare le funzioni per calcolare i valori dell&#39;asse X o dell&#39;asse Y in un grafico.

### Funzioni predefinite {#default-functions}

Per impostazione predefinita, con il componente Grafico sono disponibili le seguenti funzioni:

**Media (media)** Restituisce la media dei valori sull&#39;asse X o Y di un valore specificato sull&#39;altro asse.

**Somma** Restituisce la somma di tutti i valori sull&#39;asse X o Y per un valore specificato sull&#39;altro asse.

**Massimo** Restituisce il valore massimo dei valori sull&#39;asse X o Y per un valore specificato sull&#39;altro asse.

**Frequenza** Restituisce il numero di valori sull&#39;asse X o Y per un valore specificato sull&#39;altro asse.

**Intervallo** Restituisce la differenza tra il massimo e il minimo dei valori sull&#39;asse X o Y per un valore specificato sull&#39;altro asse.

**mediana** Restituisce il valore che separa i valori più alti e i valori più bassi nella metà dell&#39;asse X o Y per un valore specificato sull&#39;altro asse.

**Minimo** Restituisce il minimo dei valori sull&#39;asse X o Y per un valore specificato sull&#39;altro asse.

**Modalità** Restituisce il valore con la maggior parte delle occorrenze sull&#39;asse X o Y per un valore specificato sull&#39;altro asse

### Funzioni personalizzate nel canale web {#custom-functions-in-web-channel}

Oltre a utilizzare le funzioni predefinite nei grafici, è possibile scrivere funzioni personalizzate in JavaScript™ e renderle disponibili nell&#39;elenco delle funzioni del componente Grafico per il canale web.

Una funzione prende una matrice o valori e un nome di categoria come input e restituisce un valore. Ad esempio:

```
Multiply(valueArray, category) {
 var val = 1;
 _.each(valueArray, function(value) {
 val = val * value;
 });
 return val;
}
```

Dopo aver scritto una funzione personalizzata, procedi come segue per renderla disponibile per l&#39;uso nella configurazione del grafico:

1. Aggiungi la funzione personalizzata nella libreria client associata alla comunicazione interattiva pertinente. Per ulteriori informazioni, consulta [Configurazione dell’azione Invia](/help/forms/using/configuring-submit-actions.md) e [Utilizzo delle librerie lato client](/help/sites-developing/clientlibs.md).

1. Per visualizzare la funzione personalizzata nel menu a discesa Funzione, in CRXDe Lite, crea un `nt:unstructured` nella cartella apps con le seguenti proprietà:

   * Aggiungi proprietà `guideComponentType` con valore come `fd/af/reducer`. (obbligatorio)
   * Aggiungi proprietà `value` a un nome completo della funzione JavaScript™ personalizzata. (obbligatorio) e imposta il relativo valore sul nome della funzione personalizzata, ad esempio Moltiplica.
   * Aggiungi proprietà `jcr:description` con il valore che si desidera visualizzare come nome della funzione personalizzata visualizzata nel menu a discesa Funzione. Ad esempio: **Moltiplica**.
   * Aggiungi proprietà `qtip` con valore che sarà una breve descrizione della funzione personalizzata. Viene visualizzata come descrizione quando si passa il puntatore sul nome della funzione nel **Funzione** elenco a discesa.

1. Fai clic su **Salva tutto** per salvare la configurazione.

La funzione è ora disponibile per l&#39;utilizzo nel grafico.
