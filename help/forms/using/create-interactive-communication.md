---
title: Creazione di una comunicazione interattiva
seo-title: Creazione di una comunicazione interattiva
description: 'Creare una comunicazione interattiva utilizzando l''editor di comunicazione interattiva. Utilizzate la funzionalità di trascinamento per creare la comunicazione interattiva e visualizzate in anteprima sia le uscite di stampa che quelle Web su diversi tipi di dispositivi. '
seo-description: 'Creare una comunicazione interattiva utilizzando l''editor di comunicazione interattiva. Utilizzate la funzionalità di trascinamento per creare la comunicazione interattiva e visualizzate in anteprima sia le uscite di stampa che quelle Web su diversi tipi di dispositivi. '
uuid: b98e9a49-cef2-42f2-b484-8765b859895b
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c106aa41-cbc0-4daf-9ac6-6c0d23710010
translation-type: tm+mt
source-git-commit: 73d0dea62c294bea435364fb9c6892d80751d90d

---


# Creazione di una comunicazione interattiva {#create-an-interactive-communication}

Creare una comunicazione interattiva utilizzando l&#39;editor di comunicazione interattiva. Utilizzate la funzionalità di trascinamento per creare la comunicazione interattiva e visualizzate in anteprima sia le uscite di stampa che quelle Web su diversi tipi di dispositivi.

## Panoramica {#overview}

Le comunicazioni interattive centralizzano e gestiscono la creazione, l&#39;assemblaggio e la distribuzione di corrispondenze personalizzate e interattive. Utilizzando la stampa come canale principale per il Web, potete ridurre al minimo la duplicazione del lavoro per creare l&#39;output Web della comunicazione interattiva.

### Prerequisiti {#prerequisites}

Di seguito sono riportati i prerequisiti per la creazione di una comunicazione interattiva:

* Configurare un modello [dati](/help/forms/using/data-integration.md) modulo contenente dati di prova o con un&#39;origine dati effettiva, ad esempio un&#39;istanza di Microsoft® Dynamics.
* Assicurarsi di disporre dei frammenti [](/help/forms/using/document-fragments.md)del documento.
* Accertatevi di disporre di [Modelli per la stampa e il canale](/help/forms/using/web-channel-print-channel.md)Web.
* Accertatevi di disporre del [tema](/help/forms/using/themes.md) richiesto per il canale Web.

## Crea comunicazione interattiva {#createic}

1. Accedete all’istanza di creazione di AEM e passate ad **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Moduli]** > **[!UICONTROL Moduli e documenti]**.
1. Toccate **[!UICONTROL Crea]** e selezionate Comunicazione **** interattiva. Viene visualizzata la pagina Crea comunicazione interattiva.

   ![create-interactive-communication](assets/create-interactive-communication.png)

1. Inserite le seguenti informazioni. :

   * **[!UICONTROL Titolo]**: Inserite il titolo della comunicazione interattiva.
   * **[!UICONTROL Nome*]**: Il nome della comunicazione interattiva viene derivato dal titolo immesso. Modificatelo, se necessario.
   * **[!UICONTROL Descrizione]**: Inserite una descrizione della comunicazione interattiva.
   * **[!UICONTROL Modello dati modulo*]**: Individuare e selezionare il modello dati del modulo. Per ulteriori informazioni sul modello dati modulo, consulta Integrazione [dati](/help/forms/using/data-integration.md)AEM Forms.
   * **[!UICONTROL Servizio]** di precompilazione: Selezionate il servizio di precompilazione per recuperare i dati e precompilare la comunicazione interattiva.
   * **[!UICONTROL Tipo]** post-processo: Potete selezionare il flusso di lavoro AEM o Forms da attivare all&#39;invio della comunicazione interattiva. Selezionare il tipo di flusso di lavoro da attivare.
   * **[!UICONTROL Post-processo]**: Selezionate il nome del flusso di lavoro da attivare. Quando selezionate Flusso di lavoro AEM, specificate Percorso allegato, Percorso layout, Percorso PDF, Percorso dati di stampa e Percorso dati Web.
   * **[!UICONTROL Tag]**: Selezionate i tag da applicare alla comunicazione interattiva. Potete anche digitare un nome di tag nuovo/personalizzato e premere Invio per crearlo.
   * **[!UICONTROL Autore]**: il nome dell&#39;autore viene automaticamente prelevato dal nome utente dell&#39;utente connesso.
   * **** Data pubblicazione: Immettete la data di pubblicazione della comunicazione interattiva.
   * **[!UICONTROL Data]** annullamento pubblicazione: Immettete la data per annullare la pubblicazione della comunicazione interattiva.

1. Toccate **[!UICONTROL Avanti]**. Viene visualizzata la schermata per specificare i dettagli del canale Web e della stampa.
1. Digitate il testo seguente:

   * **[!UICONTROL Stampa]**: Selezionate questa opzione per generare il canale di stampa della comunicazione interattiva.
   * **** Modello di stampa*: Individuate e selezionate un file XDP come modello di stampa.
   * **** Usa Stampa Come Master Per Canale Web: Selezionate questa opzione per creare il canale Web sincronizzato con il canale di stampa. L&#39;utilizzo del canale di stampa come master per il canale Web garantisce che il contenuto e il binding dei dati del canale Web siano derivati dal canale di stampa e che le modifiche apportate al canale di stampa si riflettano sul canale Web quando si tocca Sincronizza. Gli autori possono tuttavia interrompere l’ereditarietà di componenti specifici nel canale Web, a seconda delle necessità. Per ulteriori informazioni, vedere [Sincronizzare il canale Web con il canale](/help/forms/using/create-interactive-communication.md#synchronize)Stampa.
   * **** Web: Selezionate questa opzione per generare il canale Web o l&#39;output reattivo della comunicazione interattiva.
   * **** Modello Web per comunicazioni interattive*: Sfogliate e selezionate il modello Web.
   * **[!UICONTROL Tema]** e **[!UICONTROL Seleziona tema*]**: Sfogliate e selezionate il tema per personalizzare il canale Web della comunicazione interattiva. Per ulteriori informazioni, consultate [Temi in AEM Forms](/help/forms/using/themes.md).
   Per ulteriori informazioni sui canali di stampa e web, vedere Canale di [stampa e canale](/help/forms/using/web-channel-print-channel.md)Web.

1. Toccate **[!UICONTROL Crea]**. Viene creata la comunicazione interattiva e viene visualizzata una finestra di avviso. Toccate **[!UICONTROL Modifica]** per iniziare a creare il contenuto della comunicazione interattiva come spiegato in [Aggiunta di contenuti mediante l’interfaccia](#step2)utente per la creazione di comunicazioni interattive. In alternativa, toccate **[!UICONTROL Fine]** e scegliete di modificare la comunicazione interattiva in un secondo momento.

## Aggiunta di contenuti alla comunicazione interattiva {#step2}

Dopo aver creato una comunicazione interattiva, potete usare l’interfaccia di creazione della comunicazione interattiva per crearne il contenuto.

Per ulteriori informazioni sull’interfaccia di authoring delle comunicazioni interattive, consulta [Introduzione all’authoring](/help/forms/using/introduction-interactive-communication-authoring.md)delle comunicazioni interattive.

1. L&#39;interfaccia di creazione delle comunicazioni interattive viene avviata quando toccate Modifica come indicato in [Creazione di comunicazioni](#createic)interattive. In alternativa, puoi accedere a una risorsa di comunicazione interattiva esistente su AEM, selezionarla e toccare **[!UICONTROL Modifica]** per avviare l’interfaccia di creazione della comunicazione interattiva.

   Per impostazione predefinita, viene visualizzato il canale di stampa della comunicazione interattiva, a meno che la comunicazione interattiva non sia solo per canale Web. Il canale di stampa della comunicazione interattiva visualizza le aree di destinazione, come disponibile nel modello di canale XDP/stampa selezionato. In queste aree e campi di destinazione, potete aggiungere componenti o risorse.

1. Con il canale di stampa selezionato, selezionare la scheda **[!UICONTROL Componenti]** . I seguenti componenti sono disponibili nel canale di stampa:

   | **Componente** | **Funzionalità** |
   |---|---|
   | Grafico | Aggiunge un grafico che è possibile utilizzare nella comunicazione interattiva per la rappresentazione visiva dei dati bidimensionali recuperati da una raccolta di modelli di dati del modulo. Per ulteriori informazioni, consulta [Utilizzo dei grafici nelle comunicazioni](/help/forms/using/chart-component-interactive-communications.md)interattive. |
   | Frammento di documento | Consente di aggiungere a una comunicazione interattiva un componente riutilizzabile, ad esempio testo, elenco o condizione. Il componente aggiunto può essere basato su un modello dati del modulo o senza un modello dati del modulo. |
   | Immagine | Consente di inserire un’immagine. |

   Trascina i componenti nella comunicazione interattiva e configurali come necessario.

1. Con il canale di stampa selezionato, andate alla scheda **[!UICONTROL Risorse]** e applicate il filtro per visualizzare solo le risorse da visualizzare.

   Utilizzando il browser Risorse, puoi anche trascinare e rilasciare risorse direttamente nelle aree di destinazione delle comunicazioni interattive.

   ![assets-docfragments](assets/assets-docfragments.png)

1. Trascinare i frammenti di documento nella comunicazione interattiva. Di seguito sono riportati i tipi di frammenti di documento che è possibile utilizzare nel canale di stampa della comunicazione interattiva.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Tipo frammento documento</strong></td> 
   <td><strong>Esempio di scopo</strong></td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/texts-interactive-communications.md" target="_blank">Testo</a></td> 
   <td>Testo per aggiungere indirizzo, e-mail del destinatario e testo della lettera </td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/conditions-interactive-communications.md" target="_blank">Condizione</a></td> 
   <td>Condizione per aggiungere l'immagine di intestazione appropriata alla comunicazione in base al tipo di criterio: Standard o Premium. <br /> </td> 
  </tr> 
  <tr> 
   <td>Elenco</td> 
   <td>Gruppo di frammenti di documento, inclusi testo, condizioni, altri elenchi e immagini. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Per ulteriori informazioni sui frammenti di documento, vedere [Frammenti](/help/forms/using/document-fragments.md)di documento.

1. Per impostare il binding delle variabili, toccare una variabile e selezionare ![configure_icon](assets/configure_icon.png) (Configure), quindi impostare le proprietà di binding nel pannello Proprietà nella barra laterale.

   * **[!UICONTROL Nessuno]**: L&#39;agente inserirà il valore della variabile.
   * **[!UICONTROL Frammento]** di testo: Se questa opzione è selezionata, è possibile individuare e selezionare un frammento di documento di testo il cui contenuto è rappresentato nel campo. Solo i frammenti di documento di testo possono essere associati a variabili prive di variabili.
   * **[!UICONTROL Oggetto]** modello dati: Selezionare una proprietà del modello dati del modulo il cui valore è popolato nel campo.
   È inoltre possibile configurare il frammento di documento di testo pertinente. Nel pannello Proprietà viene visualizzato l’elenco delle variabili presenti nel frammento del documento di testo. Toccate ![Modifica](assets/edit.png) (Modifica) accanto al nome di una variabile per visualizzare le impostazioni di modifica della variabile.

1. Per aggiungere una tabella, con il canale di stampa selezionato, nella scheda **[!UICONTROL Risorse]** applicare il filtro per visualizzare solo i frammenti di layout. Trascinate il frammento di layout desiderato nella comunicazione interattiva. Un frammento di layout è basato su un XDP e può essere utilizzato per creare layout grafici o tabelle statiche e dinamiche in Comunicazione interattiva con dati dinamici.

   Esempio: Tabella di layout per visualizzare il premio lordo, lo sconto fedeltà %, e la disponibilità di assistenza stradale di emergenza per le vecchie e le nuove politiche.

   Per ulteriori informazioni sui frammenti di layout, vedere [Frammenti](/help/forms/using/document-fragments.md)di documento.

1. Con il canale di stampa selezionato, nella scheda **[!UICONTROL Risorse]** applicare il filtro per visualizzare le immagini. Trascinate le immagini richieste nella comunicazione interattiva, ad esempio per il logo aziendale.

   Inoltre, nella comunicazione interattiva, gestite quanto segue:

   * [Aggiunta e configurazione di grafici](/help/forms/using/chart-component-interactive-communications.md)
   * [Sincronizzazione del canale Web con il canale di stampa](/help/forms/using/create-interactive-communication.md#synchronize)

      * Sincronizzazione automatica
      * Annulla ereditarietà
      * Riabilita ereditarietà
      * Sincronizza
   * [Allegati e accesso alla libreria](/help/forms/using/create-interactive-communication.md#attachmentslibrary)
   * [Proprietà dei campi XDP/Layout](/help/forms/using/create-interactive-communication.md#xdplayoutfieldproperties)
   * [Aggiunta di regole ai componenti](/help/forms/using/create-interactive-communication.md#rules)


1. Passate al canale **[!UICONTROL Web]**. Il canale Web viene visualizzato nell&#39;editor di comunicazione interattiva. Quando si passa dal canale Stampa al canale Web per la prima volta, si verifica la sincronizzazione automatica. Per ulteriori informazioni, vedere [Sincronizzazione del canale Web dal canale](/help/forms/using/create-interactive-communication.md#synchronize)di stampa.

   Poiché in questo esempio viene utilizzata la funzione Stampa come master per il Web, i segnaposto dei canali di stampa, i contenuti e il binding dei dati vengono sincronizzati sul canale Web. Tuttavia, potete modificare e personalizzare il contenuto specifico del canale Web come necessario.

   ![webchannelassets](assets/webchannelassets.png)

1. Per aggiungere altri componenti nel canale Web, toccate **[!UICONTROL Componenti]** con il canale Web selezionato. Trascina i componenti sul canale Web della comunicazione interattiva, come necessario, e procedi a configurarli.

   | Componenti | Funzionalità |
   |---|---|
   | Grafico | Aggiunge un grafico che è possibile utilizzare nella comunicazione interattiva per la rappresentazione visiva dei dati bidimensionali recuperati da una raccolta di modelli di dati del modulo. Per ulteriori informazioni, vedere [Uso del componente](/help/forms/using/chart-component-interactive-communications.md)grafico. |
   | Frammento di documento | Consente di aggiungere a una comunicazione interattiva un componente, un testo, un elenco o una condizione riutilizzabili. Il componente riutilizzabile aggiunto a una comunicazione interattiva potrebbe essere basato su un modello dati del modulo o non su un modello dati del modulo. |
   | Immagine | Consente di inserire un’immagine. |
   | Pannello | Il componente Pannello è un segnaposto per raggruppare altri componenti e controlla il modo in cui un gruppo di componenti, come fisarmonica e schede, vengono disposti nella comunicazione interattiva. Un componente pannello consente inoltre di rendere ripetibile un gruppo di componenti per l’utente finale, ad esempio in più voci richieste per compilare le credenziali educative. |
   | Tabella | Aggiunge una tabella che consente di organizzare i dati in righe e colonne. |
   | Area di destinazione | Inserisce un’area di destinazione in un canale Web per organizzare i componenti specifici del canale Web. L’area di destinazione è un contenitore semplice che consente di raggruppare componenti specifici per i canali Web. |
   | Testo | Aggiunge testo RTF al canale Web di una comunicazione interattiva. Il testo può anche utilizzare oggetti modello dati modulo per rendere dinamico il contenuto. |

1. Se necessario, inserite le risorse nel canale Web.

   Potete [visualizzare l&#39;anteprima della comunicazione](#previewic) interattiva per vedere l&#39;aspetto della stampa e delle uscite Web della comunicazione interattiva e continuare a apportare le modifiche necessarie.

## Anteprima della comunicazione interattiva {#previewic}

Potete utilizzare l&#39;opzione **[!UICONTROL Anteprima]** per valutare l&#39;aspetto della comunicazione interattiva. Il canale Web della comunicazione interattiva offre inoltre la possibilità di emulare l&#39;esperienza di una comunicazione interattiva per diversi dispositivi. Ad esempio, iPhone, iPad e Desktop. Potete utilizzare insieme le opzioni **[!UICONTROL Anteprima]** ed **[!UICONTROL Emulatore]** ![righello](assets/ruler.png) per visualizzare in anteprima le uscite Web per dispositivi di diverse dimensioni di schermo. I dati di esempio contenuti nell&#39;anteprima vengono compilati a partire dal modello dati del modulo specificato.

1. Selezionate il canale (stampa o Web) per visualizzare l’anteprima e toccate Anteprima. Viene visualizzata la comunicazione interattiva.

   >[!NOTE]
   >
   >L&#39;anteprima viene compilata con i dati di esempio del modello dati del modulo specificato. Per ulteriori informazioni sulla visualizzazione in anteprima della comunicazione interattiva con altri dati o sull&#39;utilizzo del servizio di precompilazione, vedere [Uso del modello](/help/forms/using/using-form-data-model.md) dati del modulo e [Uso del modello](/help/forms/using/work-with-form-data-model.md)dati del modulo.

1. Per il canale Web, utilizzate il ![righello](assets/ruler.png) per visualizzare l&#39;aspetto della comunicazione interattiva su vari dispositivi.

   ![webchannelpreview](assets/webchannelpreview.png)

Inoltre, puoi [preparare e inviare comunicazioni interattive utilizzando l&#39;interfaccia utente](/help/forms/using/prepare-send-interactive-communication.md)agente.

## Configurazione delle proprietà in Comunicazione interattiva {#configuring-properties-in-interactive-communication}

### Allegati e accesso alla libreria {#attachmentslibrary}

Nel canale Stampa, puoi configurare gli allegati e l&#39;accesso alla libreria per consentire all&#39;agente di gestire gli allegati nell&#39;interfaccia utente dell&#39;agente per la comunicazione interattiva:

1. Nel canale Stampa, evidenziare il Contenitore documento e toccare **[!UICONTROL Proprietà]**.

   ![documentcontainerproperties](assets/documentcontainerproperties.png)

   Il pannello Proprietà viene visualizzato nella barra laterale.

   ![proprietà:achment](assets/propertiesattachments.png)

1. Espandere **[!UICONTROL Allegati]** e specificare le proprietà seguenti:

   * **[!UICONTROL Consenti accesso]** libreria: Selezionate questa opzione per abilitare l&#39;accesso alla libreria per l&#39;agente nell&#39;interfaccia utente dell&#39;agente. Se attivato, l&#39;agente può aggiungere file dalla libreria durante la preparazione della comunicazione interattiva.
   * **[!UICONTROL Consenti Riordinamento Degli Allegati]**: Selezionare per abilitare l&#39;agente a riordinare gli allegati con la comunicazione interattiva.
   * **[!UICONTROL Numero Massimo Di Allegati Consentiti]**: Specificate il numero massimo di allegati consentiti con la comunicazione interattiva.
   * **[!UICONTROL File Da Allegare]**: Toccate **[!UICONTROL Aggiungi]** e sfogliate per selezionare i file da allegare e specificate quanto segue:

      * **[!UICONTROL Allega Questo File Al Documento Per Impostazione Predefinita]**: È possibile modificare questa opzione se solo l&#39;allegato non è obbligatorio.
      * **** Obbligatorio: L&#39;agente non sarà in grado di rimuovere l&#39;allegato nell&#39;interfaccia utente dell&#39;agente.
   ![file allegati](assets/attachfiles.png)

1. Toccate **[!UICONTROL Chiudi]**.

### Proprietà dei campi XDP/Layout {#xdplayoutfieldproperties}

1. Durante la modifica del canale di stampa di una comunicazione interattiva, passare il mouse su un campo, creato nel modello del canale di stampa, e selezionare ![configure_icon](assets/configure_icon.png) (Configura).

   Nella barra laterale viene visualizzata la finestra di dialogo Proprietà.

   ![xdpfieldproperties](assets/xdpfieldproperties.png)

1. Specificate quanto segue:

   * **[!UICONTROL Nome]**: Nome del nodo JCR.
   * **[!UICONTROL Titolo]**: Immettete un titolo che sarà visibile all’agente nell’interfaccia utente dell’agente e nella struttura del contenitore del documento.
   * **[!UICONTROL Tipo]** di binding: Selezionare uno dei seguenti tipi di binding per il campo.

      * Nessuno: L&#39;agente inserirà il valore della proprietà.
      * Frammento di testo: Se questa opzione è selezionata, è possibile individuare e selezionare un frammento di documento di testo il cui contenuto è rappresentato nel campo.
      * Oggetto modello dati: Selezionare una proprietà del modello dati del modulo il cui valore è popolato nel campo.
   * **[!UICONTROL Valori]** predefiniti: Il valore predefinito assicura che il campo non sia vuoto se non è presente alcun valore fornito dall&#39;oggetto modello dati o dal frammento di testo specificato. Se il tipo di binding dei dati è none, il valore predefinito viene precompilato nel campo.
   * **[!UICONTROL Modificabile dall&#39;agente]**: Selezionare questa opzione per consentire all&#39;agente di modificare il valore nel campo nell&#39;interfaccia utente dell&#39;agente. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.
   * **[!UICONTROL Etichetta]**: Specificate una stringa di testo da visualizzare con il campo nell’interfaccia utente dell’agente. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.
   * **[!UICONTROL Descrizione]**: Immettere una stringa di testo che sarà visibile quando si passa il puntatore del mouse sull&#39;agente nell&#39;interfaccia utente dell&#39;agente. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.
   * **[!UICONTROL Obbligatorio]**: Selezionare per rendere il campo obbligatorio per l&#39;agente. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.
   * **[!UICONTROL Consenti righe]** multiple: Selezionare questo campo per consentire l&#39;immissione di più righe di testo nel campo. Questa impostazione non è applicabile se il tipo di binding è Frammento di testo.


1. Toccate ![done_icon](assets/done_icon.png).

## Applicazione di regole ai componenti di comunicazione interattiva {#rules}

Per condizionare componenti o contenuti nella comunicazione interattiva, toccate il componente o il contenuto e selezionate ![createruleicon](assets/createruleicon.png) (Crea regola) per avviare Editor regole.

Per ulteriori informazioni, vedere:

* [Editor regola](/help/forms/using/rule-editor.md)
* [Introduzione all&#39;authoring delle comunicazioni interattive](/help/forms/using/introduction-interactive-communication-authoring.md)

## Uso delle tabelle {#tables}

### Tabelle dinamiche nella comunicazione interattiva {#dynamic-tables-in-interactive-communication}

È possibile aggiungere tabelle dinamiche in Comunicazione interattiva utilizzando i frammenti di layout. Nella procedura seguente viene illustrato l&#39;utilizzo di un frammento di layout per creare una tabella dinamica in una comunicazione interattiva tramite un esempio di istruzione con carta di credito.

1. Assicurati che il frammento di layout richiesto per la creazione della tabella sia disponibile in AEM.
1. Nel canale di stampa della comunicazione interattiva, trascinate un frammento di layout (con una tabella a più colonne) in un’area di destinazione dal browser Risorse.

   ![lf_dragdrop](assets/lf_dragdrop.png)

   Nell&#39;area del layout Comunicazione interattiva viene visualizzata una tabella.

   ![lf_dragdrop_table](assets/lf_dragdrop_table.png)

1. Specificare il binding dei dati per ciascuna cella della tabella. Per creare una riga ripetibile, inserire le proprietà del modello dati del modulo nella riga appartenente a una proprietà raccolta comune.

   1. Toccate una cella nella tabella e selezionate ![configure_icon](assets/configure_icon.png) (Configura).

      Nella barra laterale viene visualizzata la finestra di dialogo Proprietà.

      ![lf_cell_properties](assets/lf_cell_properties.png)

   1. Configurare le proprietà:

      * **[!UICONTROL Nome]**: Nome del nodo JCR.
      * **[!UICONTROL Titolo]**: Immettete un titolo che sarà visibile nell’editor per le comunicazioni interattive.
      * **[!UICONTROL Tipo]**&amp;amp di binding;ast;: Selezionare uno dei seguenti tipi di binding per il campo.

         * **[!UICONTROL Nessuno]**
         * **[!UICONTROL Oggetto]** del modello dati: Il valore della proprietà del modello dati del modulo è compilato nel campo.
      * **[!UICONTROL Oggetto]** modello dati: La proprietà del modello dati del modulo il cui valore è popolato nel campo.
      * **[!UICONTROL Valore]** predefinito: Il valore predefinito assicura che il campo non sia vuoto se non è presente alcun valore fornito dall&#39;oggetto modello dati specificato. Il valore predefinito è precompilato nel campo.
      * **[!UICONTROL Modificabile dall&#39;agente]**: Selezionare questa opzione per consentire all&#39;agente di modificare il valore nel campo nell&#39;interfaccia utente dell&#39;agente.
   1. Toccate ![done_icon](assets/done_icon.png).



1. Visualizzate l&#39;anteprima della comunicazione interattiva per visualizzare la tabella rappresentata con i dati.

   ![lf_preview](assets/lf_preview.png)

### Tabelle solo per canali Web {#web-channel-only-tables}

È possibile creare una tabella dinamica solo per i canali Web in una comunicazione interattiva utilizzando una proprietà modello dati di raccolta di tipi. Una tabella di questo tipo è una rappresentazione delle proprietà figlio di una raccolta. È possibile modificare solo le proprietà di formattazione delle varie celle della tabella.

1. Passate al canale Web e scegliete di visualizzare il browser Origini dati.
1. Trascinare una proprietà della raccolta in un sottomodulo.

   Nel sottomodulo viene creata una tabella.

1. Visualizzare l&#39;anteprima della tabella nell&#39;anteprima Web della comunicazione interattiva.

## Sincronizzazione del canale Web con il canale di stampa {#synchronize}

Quando si seleziona Stampa come canale principale per il canale Web durante la creazione di una comunicazione interattiva, il canale Web viene creato in sincronia con il canale Stampa e il binding dei contenuti e dei dati del canale Web viene derivato dal canale di stampa e le modifiche apportate al canale di stampa vengono riportate nel canale Web quando si tocca Sincronizza.

Gli autori possono tuttavia interrompere l’ereditarietà dei componenti nel canale Web, a seconda delle necessità.
![printweb_2-3](assets/printweb_2-3.png)Fare[clic per ingrandire](assets/printweb_2-3.png)

![Stampa e canali Web nell&#39;editor di comunicazione interattiva](assets/printweb_2-1.png)

### Sincronizzazione automatica {#auto-sync}

Se si utilizza il canale Stampa come master per il canale Web e si passa al canale Web dal canale Stampa, viene eseguita la sincronizzazione automatica. La sincronizzazione automatica porta i segnaposto, il contenuto e il binding dei dati nel canale Web dal canale Stampa. A seconda della complessità e del contenuto della comunicazione interattiva, la sincronizzazione automatica potrebbe richiedere un po&#39; di tempo.

>[!NOTE]
>
>La sincronizzazione dei canali sincronizza solo i frammenti di documento, le immagini, le condizioni, gli elenchi e i frammenti di layout dal canale di stampa al canale Web. I sottomoduli o i nodi padre che includono tali elementi non sono sincronizzati.

### Annulla ereditarietà {#cancel-inheritance}

Nel canale Web, i componenti sono incorporati nelle aree di destinazione.

Passa il cursore del mouse sull’area di destinazione desiderata nel canale Web e seleziona ![Annulla ereditarietà](assets/cancelinheritance.png) (Annulla ereditarietà), quindi tocca **[!UICONTROL Sì]** nella finestra di dialogo Annulla ereditarietà.

L&#39;ereditarietà dei componenti all&#39;interno dell&#39;area di destinazione viene annullata e ora è possibile modificarli come necessario.

### Riattiva ereditarietà {#re-enable-inheritance}

Nel canale Web, se avete annullato l’ereditarietà di un componente, potete riattivarlo. Per abilitare nuovamente l&#39;ereditarietà, passate il puntatore del mouse sul contorno dell&#39;area di destinazione interessata, che include il componente, e toccate ![renableinheritance](assets/reenableinheritance.png).

Viene visualizzata la finestra di dialogo Ripristina ereditarietà.

![revertinheritance](assets/revertinheritance.png)

Se necessario, selezionate **[!UICONTROL Sincronizza pagina dopo il ripristino dell’ereditarietà]**. Selezionate questa opzione per sincronizzare l&#39;intera comunicazione interattiva. Se non si seleziona questa opzione, al ripristino dell&#39;ereditarietà viene sincronizzata solo l&#39;area di destinazione interessata.

Toccate **[!UICONTROL Sì]**.

### Sincronizza {#synchronize-1}

Se utilizzate Stampa come canale principale per il canale Web e apportate modifiche al canale di stampa, potete toccare Sincronizza per portare le modifiche appena apportate al canale Web.

1. Per sincronizzare il canale Web con il canale di stampa, toccate **[!UICONTROL Sincronizza]**.

   Viene visualizzata la finestra di dialogo Sincronizza contenuto dal canale principale.

   ![sync econtentfrommasterchannel](assets/synchronizecontentfrommasterchannel.png)

1. Toccate una delle seguenti opzioni:

   * **[!UICONTROL Ignora modifiche]**: Ignora tutte le modifiche apportate al canale Web, indipendentemente dalle modifiche apportate al canale Web.
   * **[!UICONTROL Mantieni modifiche]**: Sincronizza il contenuto solo per le aree di destinazione in cui l&#39;ereditarietà non viene annullata.

