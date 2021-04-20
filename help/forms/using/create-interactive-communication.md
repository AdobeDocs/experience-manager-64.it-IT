---
title: Creare una comunicazione interattiva
seo-title: Creare una comunicazione interattiva
description: 'Crea una comunicazione interattiva utilizzando l’editor di comunicazioni interattive. Utilizza la funzionalità di trascinamento della selezione per creare la comunicazione interattiva e visualizzare in anteprima sia le uscite di stampa che quelle web su diversi tipi di dispositivi. '
seo-description: 'Crea una comunicazione interattiva utilizzando l’editor di comunicazioni interattive. Utilizza la funzionalità di trascinamento della selezione per creare la comunicazione interattiva e visualizzare in anteprima sia le uscite di stampa che quelle web su diversi tipi di dispositivi. '
uuid: b98e9a49-cef2-42f2-b484-8765b859895b
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c106aa41-cbc0-4daf-9ac6-6c0d23710010
feature: Interactive Communication
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '3154'
ht-degree: 2%

---


# Creare una comunicazione interattiva {#create-an-interactive-communication}

Crea una comunicazione interattiva utilizzando l’editor di comunicazioni interattive. Utilizza la funzionalità di trascinamento della selezione per creare la comunicazione interattiva e visualizzare in anteprima sia le uscite di stampa che quelle web su diversi tipi di dispositivi.

## Panoramica {#overview}

Le comunicazioni interattive centralizzano e gestiscono la creazione, l&#39;assemblaggio e la distribuzione di corrispondenze personalizzate e interattive. Utilizza la stampa come canale principale per il web, per ridurre al minimo le duplicazioni nella creazione dell&#39;output web della comunicazione interattiva.

### Prerequisiti {#prerequisites}

Di seguito sono riportati i prerequisiti per la creazione di una comunicazione interattiva:

* Imposta un [modello dati modulo](/help/forms/using/data-integration.md) contenente dati di prova o con un’origine dati effettiva, ad esempio un’istanza di Microsoft® Dynamics.
* Assicurati di disporre dei [Frammenti documento](/help/forms/using/document-fragments.md).
* Assicurati di disporre di [Modelli per la stampa e il canale web](/help/forms/using/web-channel-print-channel.md).
* Assicurati di disporre del [tema](/help/forms/using/themes.md) richiesto per il canale web.

## Crea comunicazione interattiva {#createic}

1. Accedi all&#39;istanza di authoring AEM e passa a **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; Documents]**.
1. Tocca **[!UICONTROL Crea]** e seleziona **[!UICONTROL Comunicazione interattiva]**. Viene visualizzata la pagina Crea comunicazione interattiva .

   ![create-interattivo-communication](assets/create-interactive-communication.png)

1. Inserite le seguenti informazioni. :

   * **[!UICONTROL Titolo]**: Inserisci il titolo della comunicazione interattiva.
   * **[!UICONTROL Nome*]**: Il nome della comunicazione interattiva viene derivato dal titolo inserito. Se necessario, modificalo.
   * **[!UICONTROL Descrizione]**: Immettere una descrizione della comunicazione interattiva.
   * **[!UICONTROL Modello dati modulo*]**: Individuare e selezionare il modello dati del modulo. Per ulteriori informazioni su Form Data Model, vedere [Integrazione dei dati di AEM Forms](/help/forms/using/data-integration.md).
   * **[!UICONTROL Servizio]** di precompilazione: Seleziona il servizio di precompilazione per recuperare i dati e precompilare la comunicazione interattiva.
   * **[!UICONTROL Tipo]** di post-processo: È possibile selezionare AEM o il flusso di lavoro Forms da attivare quando viene inviata la comunicazione interattiva. Seleziona il tipo di flusso di lavoro da attivare.
   * **[!UICONTROL Processo]** post: Seleziona il nome del flusso di lavoro da attivare. Quando si seleziona AEM flusso di lavoro, specificare Percorso allegato, Percorso layout, Percorso PDF, Percorso dati di stampa e Percorso dati Web.
   * **[!UICONTROL Tag]**: Selezionare i tag da applicare alla comunicazione interattiva. Puoi anche digitare un nome di tag nuovo/personalizzato e premere Invio per crearlo.
   * **[!UICONTROL Autore]**: il nome dell’autore viene automaticamente prelevato dal nome utente dell’utente connesso.
   * **[!UICONTROL Data di pubblicazione:]** immetti la data di pubblicazione della comunicazione interattiva.
   * **[!UICONTROL Data]** di annullamento pubblicazione: Immettere la data per annullare la pubblicazione della comunicazione interattiva.

1. Tocca **[!UICONTROL Avanti]**. Viene visualizzata la schermata per specificare i dettagli del canale web e di stampa.
1. Immetti quanto segue:

   * **[!UICONTROL Stampa]**: Selezionare questa opzione per generare il canale di stampa della comunicazione interattiva.
   * **[!UICONTROL Modello di stampa*:]** consente di selezionare un modello XDP come modello di stampa.
   * **[!UICONTROL Usa Stampa come master per il canale web:]** seleziona questa opzione per creare il canale web in sincronia con il canale di stampa. L&#39;utilizzo del canale di stampa come master per il canale web assicura che il contenuto e il binding dei dati del canale web siano derivati dal canale di stampa e che le modifiche apportate al canale di stampa si riflettano nel canale web quando si tocca Sincronizza. Tuttavia, gli autori possono interrompere l’ereditarietà di componenti specifici nel canale web, a seconda delle necessità. Per ulteriori informazioni, vedere [Sincronizzare il canale Web con il canale di stampa](/help/forms/using/create-interactive-communication.md#synchronize).
   * **[!UICONTROL Web:]** seleziona questa opzione per generare il canale web o l’output dinamico della comunicazione interattiva.
   * **[!UICONTROL Modello Web di comunicazione interattiva*:]** consente di sfogliare e selezionare il modello web.
   * **** Tema e  **[!UICONTROL seleziona tema*]**: Sfoglia e seleziona il tema per personalizzare lo stile del canale web della comunicazione interattiva. Per ulteriori informazioni, consulta [Temi in AEM Forms](/help/forms/using/themes.md).

   Per ulteriori informazioni sul canale di stampa e sul canale web, vedere [Canale di stampa e canale web](/help/forms/using/web-channel-print-channel.md).

1. Tocca **[!UICONTROL Crea]**. Viene creata la comunicazione interattiva e viene visualizzata una finestra di avviso. Tocca **[!UICONTROL Modifica]** per iniziare a creare il contenuto della comunicazione interattiva, come spiegato in [Aggiungi il contenuto utilizzando l&#39;interfaccia utente per l&#39;authoring delle comunicazioni interattive](#step2). In alternativa, è possibile toccare **[!UICONTROL Fine]** e scegliere di modificare la comunicazione interattiva in un secondo momento.

## Aggiungere contenuto alla comunicazione interattiva {#step2}

Dopo aver creato una comunicazione interattiva, puoi utilizzare l’interfaccia di creazione della comunicazione interattiva per crearne i contenuti.

Per ulteriori informazioni sull&#39;interfaccia di authoring delle comunicazioni interattive, vedere [Introduzione all&#39;authoring delle comunicazioni interattive](/help/forms/using/introduction-interactive-communication-authoring.md).

1. L&#39;interfaccia di creazione delle comunicazioni interattive viene avviata quando tocchi Modifica come indicato in [Crea comunicazione interattiva](#createic). In alternativa, puoi passare a una risorsa di comunicazione interattiva esistente su AEM, selezionarla e toccare **[!UICONTROL Modifica]** per avviare l’interfaccia di creazione di comunicazioni interattive.

   Per impostazione predefinita, viene visualizzato il canale di stampa della comunicazione interattiva, a meno che la comunicazione interattiva non sia solo un canale web. Il canale Stampa della comunicazione interattiva visualizza le aree di destinazione, come disponibile nel modello di canale XDP/print selezionato. In queste aree e campi di destinazione, puoi aggiungere componenti o risorse.

1. Con il canale di stampa selezionato, selezionare la scheda **[!UICONTROL Componenti]** . I seguenti componenti sono disponibili nel canale di stampa:

   | **Componente** | **Funzionalità** |
   |---|---|
   | Grafico | Aggiunge un grafico che è possibile utilizzare nella comunicazione interattiva per la rappresentazione visiva dei dati bidimensionali recuperati da una raccolta di modelli di dati del modulo. Per ulteriori informazioni, consulta [Uso dei grafici nelle comunicazioni interattive](/help/forms/using/chart-component-interactive-communications.md). |
   | Frammento di documento | Consente di aggiungere un componente riutilizzabile, ad esempio testo, elenco o condizione, a una comunicazione interattiva. Il componente aggiunto può essere basato su modelli di dati modulo o senza un modello di dati modulo. |
   | Immagine | Consente di inserire un’immagine. |

   Trascina i componenti nella comunicazione interattiva e configurali in base alle tue esigenze.

1. Con il canale di stampa selezionato, vai alla scheda **[!UICONTROL Risorse]** e applica il filtro per visualizzare solo le risorse che desideri visualizzare.

   Utilizzando il browser Risorse, puoi anche trascinare e rilasciare risorse direttamente nelle aree di destinazione di Comunicazione interattiva.

   ![assets-docfragments](assets/assets-docfragments.png)

1. Trascina i frammenti del documento nella comunicazione interattiva. Di seguito sono riportati i tipi di frammenti di documento che è possibile utilizzare nel canale di stampa della comunicazione interattiva.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Tipo frammento documento</strong></td> 
   <td><strong>Scopo di esempio</strong></td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/texts-interactive-communications.md" target="_blank">Testo</a></td> 
   <td>Testo per aggiungere indirizzo, e-mail del destinatario e testo del corpo della lettera </td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/conditions-interactive-communications.md" target="_blank">Condizione</a></td> 
   <td>Condizione per aggiungere l’immagine di intestazione appropriata alla comunicazione in base al tipo di criterio: Standard o Premium. <br /> </td> 
  </tr> 
  <tr> 
   <td>Elenco</td> 
   <td>Gruppo di frammenti di documento, inclusi testo, condizioni, altri elenchi e immagini. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Per ulteriori informazioni sui frammenti di documento, vedere [Frammenti di documento](/help/forms/using/document-fragments.md).

1. Per impostare il binding delle variabili, toccare una variabile e selezionare ![configure_icon](assets/configure_icon.png) (Configura), quindi impostare le proprietà di binding nel pannello Proprietà nella barra laterale.

   * **[!UICONTROL Nessuno]**: L&#39;agente compilerà il valore della variabile.
   * **[!UICONTROL Frammento]** di testo: Se questa opzione è selezionata, è possibile sfogliare e selezionare un frammento di documento di testo il cui contenuto è sottoposto a rendering nel campo. Solo i frammenti di documento di testo possono essere associati a variabili prive di variabili.
   * **[!UICONTROL Oggetto]** modello dati: Selezionare una proprietà del modello dati del modulo il cui valore viene compilato nel campo .

   È inoltre possibile scegliere di configurare il frammento di documento di testo pertinente. Nel pannello Proprietà viene visualizzato l’elenco delle variabili nel frammento di documento di testo. Puoi toccare ![modifica](assets/edit.png) (Modifica) accanto al nome di una variabile per visualizzare le impostazioni di modifica della variabile.

1. Per aggiungere una tabella con il canale di stampa selezionato, nella scheda **[!UICONTROL Risorse]** applicare il filtro per visualizzare solo i frammenti di layout. Trascina il frammento di layout desiderato nella comunicazione interattiva. Un frammento di layout è basato su un XDP e può essere utilizzato per creare layout grafici o tabelle statiche e dinamiche in Comunicazione interattiva che vengono popolate con dati dinamici.

   Esempio: Una tabella di layout per visualizzare il premio lordo, lo sconto fedeltà % e la disponibilità di assistenza stradale di emergenza per le politiche vecchie e nuove.

   Per ulteriori informazioni sui frammenti di layout, vedere [Frammenti documento](/help/forms/using/document-fragments.md).

1. Con il canale di stampa selezionato, nella scheda **[!UICONTROL Risorse]** applicare il filtro per visualizzare le immagini. Trascina le immagini richieste nella comunicazione interattiva, ad esempio per il logo aziendale.

   Inoltre, nella comunicazione interattiva, gestisci quanto segue:

   * [Aggiunta e configurazione di grafici](/help/forms/using/chart-component-interactive-communications.md)
   * [Sincronizzazione del canale web con il canale di stampa](/help/forms/using/create-interactive-communication.md#synchronize)

      * Sincronizzazione automatica
      * Annulla ereditarietà
      * Riattiva ereditarietà
      * Sincronizza
   * [Allegati e accesso alla libreria](/help/forms/using/create-interactive-communication.md#attachmentslibrary)
   * [Proprietà dei campi XDP/Layout](/help/forms/using/create-interactive-communication.md#xdplayoutfieldproperties)
   * [Aggiungere regole ai componenti](/help/forms/using/create-interactive-communication.md#rules)


1. Passa a **[!UICONTROL Canale Web]**. Il canale web viene visualizzato nell’editor di comunicazioni interattive. Quando si passa per la prima volta dal canale Stampa al canale Web, si verifica la sincronizzazione automatica. Per ulteriori informazioni, vedere [Sincronizzazione del canale Web dal canale di stampa](/help/forms/using/create-interactive-communication.md#synchronize).

   Poiché in questo esempio utilizziamo Stampa come master per il web, i segnaposto del canale Stampa, il contenuto e il binding dei dati vengono sincronizzati sul canale Web. Tuttavia, puoi modificare e personalizzare il contenuto specifico nel canale web in base alle tue esigenze.

   ![webchannelassets](assets/webchannelassets.png)

1. Per aggiungere altri componenti nel canale Web, con il canale Web selezionato, tocca **[!UICONTROL Componenti]**. Trascina i componenti nel canale web della comunicazione interattiva in base alle esigenze e procedi alla configurazione.

   | Componenti | Funzionalità |
   |---|---|
   | Grafico | Aggiunge un grafico che è possibile utilizzare nella comunicazione interattiva per la rappresentazione visiva dei dati bidimensionali recuperati da una raccolta di modelli di dati del modulo. Per ulteriori informazioni, vedere [Uso del componente grafico](/help/forms/using/chart-component-interactive-communications.md). |
   | Frammento di documento | Consente di aggiungere un componente, un testo, un elenco o una condizione riutilizzabili a una comunicazione interattiva. Il componente riutilizzabile aggiunto a una comunicazione interattiva può essere basato su un modello di dati del modulo o senza un modello di dati del modulo. |
   | Immagine | Consente di inserire un’immagine. |
   | Pannello | Il componente Pannello è un segnaposto per raggruppare altri componenti e controlla come un gruppo di componenti, come il pannello a soffietto e le schede, vengono disposti nella comunicazione interattiva. Un componente pannello consente inoltre di rendere ripetibile un gruppo di componenti per l’utente finale, ad esempio in più voci richieste per il riempimento delle credenziali educative. |
   | Tabella | Aggiunge una tabella che consente di organizzare i dati in righe e colonne. |
   | Area di destinazione | Inserisce un’area di destinazione in un canale web per organizzare i componenti specifici del canale web. L’area di destinazione è un contenitore semplice che consente di raggruppare componenti specifici per canale web. |
   | Testo | Aggiunge testo RTF al canale web di una comunicazione interattiva. Il testo può inoltre utilizzare gli oggetti del modello dati del modulo per rendere dinamico il contenuto. |

1. Se necessario, inserisci le risorse nel canale web.

   È possibile [visualizzare in anteprima la comunicazione interattiva](#previewic) per verificare l&#39;aspetto delle uscite di stampa e web della comunicazione interattiva e continuare a apportare le modifiche necessarie.

## Anteprima della comunicazione interattiva {#previewic}

È possibile utilizzare l&#39;opzione **[!UICONTROL Anteprima]** per valutare l&#39;aspetto della comunicazione interattiva. Il canale web della comunicazione interattiva offre inoltre la possibilità di emulare l’esperienza di una comunicazione interattiva per diversi dispositivi. Ad esempio, iPhone, iPad e Desktop. È possibile utilizzare le opzioni **[!UICONTROL Anteprima]** e **[!UICONTROL Emulatore]** ![righer](assets/ruler.png) insieme per visualizzare in anteprima le uscite web per dispositivi di diverse dimensioni dello schermo. I dati di esempio contenuti nell’anteprima vengono compilati dal modello dati dei moduli specificato.

1. Seleziona il canale (stampa o web) da visualizzare in anteprima e tocca anteprima. Viene visualizzata la comunicazione interattiva.

   >[!NOTE]
   >
   >L’anteprima viene compilata con i dati di esempio del modello dati del modulo specificato. Per ulteriori informazioni sull&#39;anteprima della comunicazione interattiva con altri dati o sull&#39;utilizzo del servizio di precompilazione, vedere [Utilizzare il modello dati del modulo](/help/forms/using/using-form-data-model.md) e [Utilizzare il modello dati del modulo](/help/forms/using/work-with-form-data-model.md).

1. Per il canale web, utilizza ![righer](assets/ruler.png) per visualizzare l&#39;aspetto della comunicazione interattiva su vari dispositivi.

   ![webchannelpreview](assets/webchannelpreview.png)

Inoltre, è possibile [Preparare e inviare comunicazioni interattive utilizzando l&#39;interfaccia utente dell&#39;agente](/help/forms/using/prepare-send-interactive-communication.md).

## Configurazione delle proprietà nella comunicazione interattiva {#configuring-properties-in-interactive-communication}

### Allegati e accesso alla libreria {#attachmentslibrary}

Nel canale Stampa è possibile configurare gli allegati e l&#39;accesso alla libreria per consentire all&#39;agente di gestire gli allegati nell&#39;interfaccia utente dell&#39;agente per la comunicazione interattiva:

1. Nel canale Stampa, evidenzia il Contenitore documento e tocca **[!UICONTROL Proprietà]**.

   ![documentcontainerproperties](assets/documentcontainerproperties.png)

   Il pannello Proprietà viene visualizzato nella barra laterale.

   ![proprietà](assets/propertiesattachments.png)

1. Espandi **[!UICONTROL Allegati]** e specifica le seguenti proprietà:

   * **[!UICONTROL Consenti accesso]** libreria: Seleziona per abilitare l&#39;accesso alla libreria per l&#39;agente nell&#39;interfaccia utente dell&#39;agente. Se attivato, l’agente può aggiungere file dalla libreria durante la preparazione della comunicazione interattiva.
   * **[!UICONTROL Consenti Il Riordinamento Degli Allegati]**: Selezionare per abilitare l&#39;agente a riordinare gli allegati con la comunicazione interattiva.
   * **[!UICONTROL Numero Massimo Di Allegati Consentiti]**: Specifica il numero massimo di allegati consentiti con la comunicazione interattiva.
   * **[!UICONTROL File Da Allegare]**: Tocca  **** Aggiungi e sfoglia per selezionare i file da allegare e specificare quanto segue:

      * **[!UICONTROL Allega Questo File Al Documento Per Impostazione Predefinita]**: È possibile modificare questa opzione se solo l&#39;allegato non è obbligatorio.
      * **[!UICONTROL Obbligatorio:]** l&#39;agente non sarà in grado di rimuovere l&#39;allegato nell&#39;interfaccia utente dell&#39;agente.

   ![file allegati](assets/attachfiles.png)

1. Toccate **[!UICONTROL Chiudi]**.

### Proprietà dei campi XDP/Layout {#xdplayoutfieldproperties}

1. Durante la modifica del canale di stampa di una comunicazione interattiva, passa il cursore del mouse su un campo creato nel modello del canale di stampa e seleziona ![configure_icon](assets/configure_icon.png) (Configura).

   La finestra di dialogo Proprietà viene visualizzata nella barra laterale.

   ![xdpfieldproperties](assets/xdpfieldproperties.png)

1. Specifica quanto segue:

   * **[!UICONTROL Nome]**: Nome del nodo JCR.
   * **[!UICONTROL Titolo]**: Immettere un titolo che sarà visibile all&#39;agente nell&#39;interfaccia utente dell&#39;agente e nella struttura del contenitore del documento.
   * **[!UICONTROL Tipo]** di binding: Selezionare uno dei seguenti tipi di binding per il campo.

      * Nessuno: Il valore della proprietà verrà compilato dall&#39;agente.
      * Frammento di testo: Se questa opzione è selezionata, è possibile sfogliare e selezionare un frammento di documento di testo il cui contenuto è sottoposto a rendering nel campo.
      * Oggetto modello dati: Selezionare una proprietà del modello dati del modulo il cui valore viene compilato nel campo .
   * **[!UICONTROL Valori]** predefiniti: Il valore predefinito assicura che il campo non sia vuoto se non è presente alcun valore fornito dall’oggetto modello dati o dal frammento di testo specificato. Se il tipo di binding dei dati non è nessuno, il valore predefinito viene precompilato nel campo .
   * **[!UICONTROL Modificabile dall&#39;agente]**: Seleziona per consentire all’agente di modificare il valore nel campo nell’interfaccia utente dell’agente. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.
   * **[!UICONTROL Etichetta]**: Specifica una stringa di testo visualizzata con il campo nell&#39;interfaccia utente dell&#39;agente. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.
   * **[!UICONTROL Descrizione]**: Immettere una stringa di testo che sarà visibile al passaggio del mouse sull&#39;agente nell&#39;interfaccia utente dell&#39;agente. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.
   * **[!UICONTROL Obbligatorio]**: Selezionare questa opzione per rendere il campo obbligatorio per l&#39;agente. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.
   * **[!UICONTROL Consenti righe]** multiple: Selezionare questo campo per consentire più righe di testo come voce nel campo. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.


1. Tocca ![done_icon](assets/done_icon.png).

## Applicare regole ai componenti di comunicazione interattiva {#rules}

Per condizionare componenti o contenuti nella comunicazione interattiva, tocca il componente o parte di contenuto e seleziona ![createruleicon](assets/createruleicon.png) (Crea regola) per avviare l’Editor regole.

Per ulteriori informazioni, vedere:

* [Editor regola](/help/forms/using/rule-editor.md)
* [Introduzione all’authoring delle comunicazioni interattive](/help/forms/using/introduction-interactive-communication-authoring.md)

## Uso delle tabelle {#tables}

### Tabelle dinamiche nella comunicazione interattiva {#dynamic-tables-in-interactive-communication}

È possibile aggiungere tabelle dinamiche nella comunicazione interattiva utilizzando frammenti di layout. I passaggi seguenti utilizzano un esempio di rendiconto della carta di credito per illustrare l’utilizzo di un frammento di layout per creare una tabella dinamica in una comunicazione interattiva.

1. Assicurati che il frammento di layout richiesto per la creazione della tabella sia disponibile in AEM.
1. Nel canale di stampa della comunicazione interattiva, trascina e rilascia un frammento di layout (con una tabella a più colonne) in un’area di destinazione dal browser Risorse.

   ![lf_dragdrop](assets/lf_dragdrop.png)

   Nell’area layout Comunicazione interattiva viene visualizzata una tabella.

   ![lf_dragdrop_table](assets/lf_dragdrop_table.png)

1. Specificare il binding dei dati per ciascuna cella della tabella. Per creare una riga ripetibile, inserire le proprietà del modello dati del modulo nella riga appartenente a una proprietà di raccolta comune.

   1. Tocca una cella nella tabella e seleziona ![configure_icon](assets/configure_icon.png) (Configura).

      La finestra di dialogo Proprietà viene visualizzata nella barra laterale.

      ![lf_cell_properties](assets/lf_cell_properties.png)

   1. Configura le proprietà:

      * **[!UICONTROL Nome]**: Nome del nodo JCR.
      * **[!UICONTROL Titolo]**: Immetti un titolo che sarà visibile nell’editor di comunicazioni interattive.
      * **[!UICONTROL Tipo]**&amp;ast di binding;: Selezionare uno dei seguenti tipi di binding per il campo.

         * **[!UICONTROL Nessuna]**
         * **[!UICONTROL Oggetto]** del modello dati: Il valore della proprietà del modello dati modulo viene compilato nel campo .
      * **[!UICONTROL Oggetto]** modello dati: Proprietà del modello dati del modulo il cui valore è popolato nel campo .
      * **[!UICONTROL Valore]** predefinito: Il valore predefinito assicura che il campo non sia vuoto se non è presente alcun valore fornito dall&#39;oggetto modello dati specificato. Il valore predefinito viene precompilato nel campo .
      * **[!UICONTROL Modificabile dall&#39;agente]**: Seleziona per consentire all’agente di modificare il valore nel campo nell’interfaccia utente dell’agente.
   1. Tocca ![done_icon](assets/done_icon.png).



1. Visualizza in anteprima la comunicazione interattiva per visualizzare la tabella rappresentata con i dati.

   ![lf_preview](assets/lf_preview.png)

### Tabelle solo per il canale web {#web-channel-only-tables}

È possibile creare una tabella dinamica solo per il canale web in una comunicazione interattiva utilizzando una proprietà del modello dati di raccolta di tipo . Una tabella di questo tipo rappresenta le proprietà secondarie di una proprietà di raccolta. È possibile modificare solo le proprietà di formattazione delle varie celle della tabella.

1. Passa al canale Web e scegli di visualizzare il browser Origini dati.
1. Trascinare una proprietà di raccolta in un sottomodulo.

   Nel sottomodulo viene creata una tabella.

1. Visualizzare l’anteprima della tabella nell’anteprima Web della comunicazione interattiva.

## Sincronizzazione del canale web con il canale di stampa {#synchronize}

Quando si seleziona Stampa come master per canale Web durante la creazione di una comunicazione interattiva, il canale Web viene creato in sincronia con il canale Stampa e il contenuto e il binding dei dati del canale Web viene derivato dal canale di stampa e le modifiche apportate nel canale di stampa vengono riportate nel canale Web quando si tocca Sincronizza.

Tuttavia, gli autori possono interrompere l’ereditarietà dei componenti nel canale web, a seconda delle necessità.
![printweb_2-3](assets/printweb_2-3.png)
[Fare clic per ingrandire](assets/printweb_2-3.png)

![Stampa e canali web nell’editor delle comunicazioni interattive](assets/printweb_2-1.png)

### Sincronizzazione automatica {#auto-sync}

Se si utilizza il canale Stampa come master per il canale Web e si passa al canale Web dal canale Stampa, viene eseguita la sincronizzazione automatica. La sincronizzazione automatica porta i segnaposto, il contenuto e il binding dei dati nel canale Web dal canale Stampa. A seconda della complessità e del contenuto della comunicazione interattiva, la sincronizzazione automatica potrebbe richiedere un po&#39; di tempo.

>[!NOTE]
>
>La sincronizzazione dei canali sincronizza solo i frammenti di documento, le immagini, le condizioni, gli elenchi e i frammenti di layout dal canale di stampa al canale Web. I sottomoduli o i nodi padre di che includono tali elementi non sono sincronizzati.

### Annulla ereditarietà {#cancel-inheritance}

Nel canale web, i componenti sono incorporati nelle aree di destinazione.

Passa il puntatore del mouse sull&#39;area di destinazione desiderata nel canale web e seleziona ![cancelinheritance](assets/cancelinheritance.png) (Annulla ereditarietà), quindi, nella finestra di dialogo Annulla ereditarietà, tocca **[!UICONTROL Sì]**.

L’ereditarietà dei componenti all’interno dell’area di destinazione viene annullata e ora è possibile modificarli in base alle esigenze.

### Riattiva ereditarietà {#re-enable-inheritance}

Nel canale Web, se hai annullato l’ereditarietà di un componente, puoi riabilitarlo. Per riabilitare l’ereditarietà, passa il cursore del mouse sul bordo dell’area di destinazione rilevante, che include il componente, e tocca ![reenableinheritance](assets/reenableinheritance.png).

Viene visualizzata la finestra di dialogo Ripristina ereditarietà.

![revertereditarietà](assets/revertinheritance.png)

Se necessario, seleziona **[!UICONTROL Sincronizza la pagina dopo aver ripristinato l&#39;ereditarietà]**. Seleziona questa opzione per sincronizzare l’intera comunicazione interattiva. Se non selezioni questa opzione, al momento del ripristino dell’ereditarietà viene sincronizzata solo l’area di destinazione interessata.

Toccare **[!UICONTROL Sì]**.

### Sincronizza {#synchronize-1}

Se si utilizza Stampa come master per il canale Web e si apportano modifiche al canale di stampa, è possibile toccare Sincronizza per portare le modifiche appena apportate al canale Web.

1. Per sincronizzare il canale Web con il canale Stampa, toccare **[!UICONTROL Sincronizza]**.

   Viene visualizzata la finestra di dialogo Sincronizza contenuto dal canale principale.

   ![sync contentfrommasterchannel](assets/synchronizecontentfrommasterchannel.png)

1. Toccate una delle seguenti opzioni:

   * **[!UICONTROL Elimina modifiche]**: Ignora tutte le modifiche apportate al canale Web, indipendentemente dalle modifiche apportate al canale Web.
   * **[!UICONTROL Mantieni modifiche]**: Sincronizza il contenuto solo per le aree di destinazione in cui l’ereditarietà non viene annullata.

