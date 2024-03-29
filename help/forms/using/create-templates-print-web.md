---
title: "Esercitazione: Crea modelli"
seo-title: Create Print and Web templates for Interactive Communication
description: Creare modelli di stampa e web per comunicazioni interattive
seo-description: Create Print and Web templates for Interactive Communication
uuid: d7b0d9a5-f5f0-4c21-a6f8-622bf94f4491
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 40c0a17b-6894-44cc-b1f7-490913061532
feature: Interactive Communication
exl-id: 5822145f-d317-4807-a3f0-1d2aea0a779b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1852'
ht-degree: 1%

---

# Esercitazione: Creare modelli {#tutorial-create-templates}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Creare modelli di stampa e web per comunicazioni interattive

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Questa esercitazione è un passaggio nel [Creare la prima comunicazione interattiva](/help/forms/using/create-your-first-interactive-communication.md) serie. Si consiglia di seguire la serie in sequenza cronologica per comprendere, eseguire e illustrare il caso d’uso completo dell’esercitazione.

Per creare una comunicazione interattiva, è necessario disporre di modelli disponibili sul server AEM per i canali Stampa e Web.

I modelli per il canale Stampa vengono creati in Adobe Forms Designer e caricati sul server AEM. Questi modelli sono quindi disponibili per l’utilizzo durante la creazione di una comunicazione interattiva.

I modelli per il canale Web vengono creati in AEM. Gli autori e gli amministratori dei modelli possono creare, modificare e abilitare i modelli web. Una volta creati e abilitati, questi modelli sono disponibili per l’utilizzo durante la creazione di una comunicazione interattiva.

Questa esercitazione illustra i passaggi necessari per creare modelli per i canali Stampa e Web in modo che siano disponibili per l&#39;utilizzo durante la creazione di comunicazioni interattive. Al termine di questa esercitazione, potrai:

* Creare modelli XDP per il canale di stampa utilizzando Adobe Forms Designer
* Caricare i modelli XDP sul server AEM Forms
* Creare e abilitare modelli per il canale Web

## Crea modello per canale di stampa {#create-template-for-print-channel}

Crea e gestisci modelli per il canale Stampa di Comunicazione interattiva utilizzando le seguenti attività:

* [Creare un modello XDP utilizzando Forms Designer](/help/forms/using/create-templates-print-web.md#create-xdp-template-using-forms-designer)
* [Carica il modello XDP sul server AEM Forms](/help/forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server)
* [Creare un modello XDP per i frammenti di layout](/help/forms/using/create-templates-print-web.md#create-xdp-template-for-layout-fragments)

### Creare un modello XDP utilizzando Forms Designer {#create-xdp-template-using-forms-designer}

In base ai [caso d&#39;uso](/help/forms/using/create-your-first-interactive-communication.md) e [anatomia](/help/forms/using/planning-interactive-communications.md), creare i seguenti sottomoduli nel modello XDP:

* Dettagli fattura: Include un frammento di documento
* Dettagli cliente: Include un frammento di documento
* Riepilogo fattura: Include un frammento di documento
* Riepilogo: Include un frammento di documento (sottomodulo Carica) e un grafico (sottomodulo Grafici)
* Chiamate dettagliate: Include una tabella (frammento di layout)
* Paga ora: Include un&#39;immagine
* Servizi a valore aggiunto: Include un&#39;immagine

![create_print_template](assets/create_print_template.gif)

Questi sottomoduli vengono visualizzati come aree di destinazione nel modello Stampa dopo il caricamento del file XDP sul server Forms. Durante la creazione della comunicazione interattiva, tutte le entità quali frammenti di documento, grafici, frammenti di layout e immagini vengono aggiunte alle aree di destinazione.

Esegui i seguenti passaggi per creare un modello XDP per il canale Stampa:

1. Apri Forms Designer e seleziona **File** > **Nuovo** > **Utilizzare un modulo vuoto,** toccare **Successivo**, quindi tocca **Fine** per aprire il modulo per la creazione del modello.

   Assicurati che **Libreria oggetto** e **Oggetto** sono selezionate tra le opzioni **Finestra** menu.

1. Trascina e rilascia la **Sottomodulo** dal **Libreria oggetto** al modulo.
1. Selezionare il sottomodulo per visualizzare le opzioni del sottomodulo nella **Oggetto** nel riquadro a destra.
1. Seleziona la **Sottomodulo** e seleziona **Flusso** dal **Contenuto** elenco a discesa. Trascinare l’endpoint sinistro del sottomodulo per regolare la lunghezza.
1. In **Binding** scheda:

   1. Specifica **DettagliFattura** in **Nome** campo .
   1. Seleziona **Nessun binding di dati** dal **Binding dei dati** elenco a discesa.

   ![forms_designer_subform](assets/forms_designer_subform.png)

1. Analogamente, selezionare il sottomodulo principale, quindi selezionare il **Sottomodulo** e seleziona **Flusso** dal **Contenuto** elenco a discesa. In **Binding** scheda:

   1. Specifica **TelecomBill** in **Nome** campo .
   1. Seleziona **Nessun binding di dati** dal **Binding dei dati** elenco a discesa.

   ![root_subform_print_template](assets/root_subform_print_template.png)

1. Ripetere i passaggi da 2 a 5 per creare i sottomoduli seguenti:

   * DettagliFattura
   * DettagliCliente
   * RiepilogoFatturazione
   * Riepilogo - Seleziona la **Sottomodulo** e seleziona **Posizionato** dal **Contenuto** elenco a discesa per questo sottomodulo. Inserire i sottomoduli seguenti nella **Riepilogo** sottomodulo.

      * Oneri
      * Grafici
   * Chiamate dettagliate
   * PayNow
   * ValueAddedServices

   Per risparmiare tempo, è inoltre possibile copiare e incollare i sottomoduli esistenti per creare nuovi sottomoduli.

   Per spostare il **Grafici** sottomodulo a destra del sottomodulo Addebiti, selezionare il **Grafici** nel riquadro a sinistra, selezionare il **Layout** e specifica un valore per **AncoraggioX** campo . Il valore deve essere maggiore del valore per **Larghezza** campo per **Oneri** sottomodulo. Seleziona la **Oneri** sottomodulo e seleziona il **Layout** per visualizzare il valore del **Larghezza** campo .

1. Trascina e rilascia la **Testo** dell&#39;oggetto **Libreria oggetto** nel modulo e immetti il **Chiama XXXX per iscriverti** testo nella casella.
1. Fare clic con il pulsante destro del mouse sull’oggetto testo nel riquadro a sinistra, quindi selezionare **Rinomina oggetto**, quindi immettere il nome dell’oggetto di testo come **Abbonati**.

   ![print_xdp_template_subform](assets/print_xdp_template_subform.png)

1. Seleziona **File** > **Salva con nome** per salvare il file sul file system locale:

   1. Passa alla posizione in cui salvare il file e specifica il nome come **create_first_ic_print_template**.
   1. Seleziona **.xdp** dal **Salva come tipo** elenco a discesa.
   1. Tocca **Salva**.

### Carica il modello XDP sul server AEM Forms {#upload-xdp-template-to-the-aem-forms-server}

Dopo aver creato un modello XDP utilizzando Forms Designer, è necessario caricarlo sul server AEM Forms in modo che sia disponibile per l’utilizzo durante la creazione della comunicazione interattiva.

1. Seleziona **[!UICONTROL Forms]** > **[!UICONTROL Forms e documenti]**.
1. Tocca **Crea** > **Caricamento file**.

   Naviga e seleziona la **create_first_ic_print_template** modello (XDP) e tocca **Apri** per importare il modello XDP nel server AEM Forms.

### Creare un modello XDP per i frammenti di layout {#create-xdp-template-for-layout-fragments}

Per creare un frammento di layout per il canale Stampa della comunicazione interattiva, crea un file XDP utilizzando Forms Designer e caricalo sul server AEM Forms.

1. Apri Forms Designer e seleziona **File** > **Nuovo** > **Utilizzare un modulo vuoto,** toccare **Successivo**, quindi tocca **Fine** per aprire il modulo per la creazione del modello.

   Assicurati che **Libreria oggetto** e **Oggetto** sono selezionate tra le opzioni **Finestra** menu.

1. Trascina e rilascia la **Tabella** dal **Libreria oggetto** al modulo.
1. Nella finestra di dialogo Inserisci tabella:

   1. Specifica il numero di colonne come **5**.
   1. Specifica il numero di righe corpo come **1**.
   1. Seleziona la **Includi riga di intestazione nella tabella** casella di controllo.
   1. Scheda **OK**.

1. Tocca **+** nel riquadro a sinistra accanto a **Tabella** 1 e fai clic con il pulsante destro del mouse **Cella1** e seleziona **Rinomina oggetto** a **Data**.

   Analogamente, rinominare **Cella2**, **Cella3**, **Cell4** e **Cella5** a **Time**, **Numero**, **Durata** e **Oneri** rispettivamente.

1. Fai clic sui campi di testo Intestazione nel **Visualizzazione Designer** e rinominarli in **Time**, **Numero**, **Durata** e **Oneri**.

   ![layout_fragment_print](assets/layout_fragment_print.png)

1. Seleziona **Riga 1** dal riquadro di sinistra e seleziona **Oggetto** > **Binding** > **Ripeti riga per ogni elemento dati**.

   ![layout_fragment_print_repeat](assets/layout_fragment_print_repeat.png)

1. Trascina e rilascia la **Campo di testo** dal **Libreria oggetto** al **Visualizzazione Designer**.

   ![layout_fragment_print_text_field](assets/layout_fragment_print_text_field.png)

   Analogamente, trascinamento della selezione **Campo di testo** nella **Time**, **Numero**, **Durata** e **Oneri** righe.

1. Seleziona **File** > **Salva con nome** per salvare il file sul file system locale:

   1. Passa alla posizione in cui salvare il file e specifica il nome come **table_lf**.
   1. Seleziona **.xdp** dal **Salva come tipo** elenco a discesa.
   1. Tocca **Salva**.

   Dopo aver creato un modello XDP per un frammento di layout utilizzando Forms Designer, è necessario [caricare](/help/forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server) al server AEM Forms in modo che il modello sia disponibile per l’uso durante la creazione di frammenti di layout.

## Crea modello per canale web {#create-template-for-web-channel}

Crea e gestisci un modello per il canale Web della comunicazione interattiva utilizzando le seguenti attività:

* [Crea cartella per i modelli](/help/forms/using/create-templates-print-web.md#create-folder-for-templates)
* [Creare il modello](/help/forms/using/create-templates-print-web.md#create-the-template)
* [Attiva il modello](/help/forms/using/create-templates-print-web.md#enable-the-template)
* [Abilitazione dei pulsanti nelle comunicazioni interattive](/help/forms/using/create-templates-print-web.md#enabling-buttons-in-interactive-communications)

### Crea cartella per i modelli {#create-folder-for-templates}

Per creare un modello di canale Web, definisci una cartella in cui salvare i modelli creati. Dopo aver creato un modello all’interno della cartella, abilitare il modello per consentire agli utenti dei moduli di creare un canale Web di una comunicazione interattiva basata sul modello.

Esegui i seguenti passaggi per creare una cartella per i modelli modificabili:

1. Tocca **Strumenti** ![Strumenti](assets/tools-icon.svg) > **Browser di configurazione**.
   * Consulta la sezione [Documentazione del browser di configurazione](/help/sites-administering/configurations.md) per ulteriori informazioni.
1. Nella pagina Browser configurazioni, tocca **Crea**.
1. In **Crea configurazione** finestra di dialogo, specifica **Crea_First_IC_templates** come titolo della cartella, controlla **Modelli modificabili**, e tocca **Crea**.

   ![create_first_ic_web_template](assets/create_first_ic_web_template.png)

   La **Crea_First_IC_templates** viene creata ed elencata nella **Browser di configurazione** pagina.

### Creare il modello {#create-the-template}

In base ai [caso d&#39;uso](/help/forms/using/create-your-first-interactive-communication.md) e [anatomia](/help/forms/using/planning-interactive-communications.md), creare i seguenti pannelli nel modello Web:

* Dettagli fattura: Include un frammento di documento
* Dettagli cliente: Include un frammento di documento
* Riepilogo fattura: Include un frammento di documento
* Sintesi delle tariffe: Include un frammento di documento e un grafico (layout a due colonne)
* Chiamate dettagliate: Include una tabella
* Paga ora: Include un **Paga ora** pulsante e immagine
* Servizi a valore aggiunto: Include un’immagine e un **Abbonati** pulsante .

![create_web_template](assets/create_web_template.gif)

Durante la creazione della comunicazione interattiva vengono aggiunte tutte le entità quali frammenti di documento, grafici, tabelle, immagini e pulsanti.

Esegui i seguenti passaggi per creare un modello per il canale Web nel **Crea_First_IC_templates** cartella:

1. Passa alla cartella del modello appropriata selezionando **Strumenti** > **Modelli** > **Crea_First_IC_templates** cartella.
1. Tocca **Crea**.
1. Sulla **Selezionare un tipo di modello** configurazione guidata, seleziona **Comunicazione interattiva - Canale Web** e toccare **Successivo**.
1. Sulla **Dettagli modello** configurazione guidata, specificare **Crea_Primo_IC_Modello_Web** come titolo del modello. Specifica una descrizione facoltativa e tocca **Crea**.

   Un messaggio di conferma che **Crea_Primo_IC_Modello_Web** viene visualizzato.

1. Tocca **Apri** per aprire il modello nell’editor modelli.
1. Seleziona **Contenuto iniziale** dall’elenco a discesa accanto a **Anteprima** opzione .

   ![template_editor_initial_content](assets/template_editor_initial_content.png)

1. Tocca **Pannello principale** quindi tocca **+** per visualizzare l’elenco dei componenti che è possibile aggiungere al modello.
1. Seleziona **Pannello** dall’elenco per aggiungere un pannello sopra il **Pannello principale**.
1. Seleziona la **Contenuto** nel riquadro a sinistra. Il nuovo pannello aggiunto al punto 8 viene visualizzato sotto la **Pannello principale** nella struttura contenuto.

   ![content_tree_root_panel](assets/content_tree_root_panel.png)

1. Seleziona il pannello e tocca ![configure_icon](assets/configure_icon.png) (Configura).
1. Nel riquadro Proprietà :

   1. Specifica **fatturato** nel campo Nome .
   1. Specifica **Dettagli fattura** nel campo Titolo .
   1. Seleziona **1** dal **Numero di colonne** elenco a discesa.
   1. Tocca ![done_icon](assets/done_icon.png) per salvare le proprietà.

   Il nome del pannello viene aggiornato in **Dettagli fattura** nella struttura contenuto.

1. Ripeti i passaggi da 7 a 11 per aggiungere al modello pannelli con le seguenti proprietà:

   | Nome | Titolo | Numero di colonne |
   |---|---|---|
   | dettagli cliente | Dettagli cliente | 1 |
   | billsummary | Riepilogo fatturazione | 1 |
   | riepiloghi | Sintesi dei costi | 2 |
   | itemisedcall | Chiamate dettagliate | 1 |
   | paga | Paga ora | 2 |
   | vas | Servizi a valore aggiunto | 1 |

   L’immagine seguente rappresenta la struttura del contenuto dopo l’aggiunta di tutti i pannelli al modello:

   ![content_tee_all_panel](assets/content_tee_all_panels.png)

### Attiva il modello {#enable-the-template}

Dopo aver creato il modello Web, è necessario attivarlo per utilizzare il modello durante la creazione della comunicazione interattiva.

Esegui i seguenti passaggi per abilitare il modello Web:

1. Tocca **Strumenti** ![Strumenti](assets/tools-icon.svg) > **Modelli**.
1. Passa a **Crea_Primo_IC_Modello_Web** modello, selezionalo e tocca **Abilita**.
1. Scheda **Abilita** di nuovo per confermare.

   Il modello è abilitato e il suo stato viene visualizzato come Abilitato. È possibile utilizzare questo modello durante la creazione di comunicazioni interattive per il canale Web.

### Abilitazione dei pulsanti nelle comunicazioni interattive {#enabling-buttons-in-interactive-communications}

In base al caso d’uso, devi includere **Paga ora** e **Abbonati** pulsanti (componenti per moduli adattivi) nella comunicazione interattiva. Per abilitare l’utilizzo di questi pulsanti nella comunicazione interattiva, esegui i seguenti passaggi:

1. Seleziona **Struttura** dall’elenco a discesa accanto a **Anteprima** opzione .
1. Seleziona la **Contenitore documento** pannello principale tramite la struttura del contenuto e tocca **Criterio** per selezionare i componenti consentiti per l’utilizzo nella comunicazione interattiva.

   ![structure_configure_policy](assets/structure_configure_policy.png)

1. In **Componenti consentiti** scheda di **Proprietà** sezione , seleziona **Pulsante** dal **Modulo adattivo** componenti.

   ![allowed_components_af](assets/allowed_components_af.png)

1. Tocca ![done_icon](assets/done_icon.png) per salvare le proprietà.
