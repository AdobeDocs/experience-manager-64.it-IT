---
title: Preparare e inviare comunicazioni interattive tramite l’interfaccia utente dell’agente
seo-title: Prepare and send Interactive Communication using the Agent UI
description: L’interfaccia utente dell’agente consente agli agenti di preparare e inviare comunicazioni interattive al processo di pubblicazione. L’agente apporta le modifiche necessarie e invia la comunicazione interattiva a un processo di pubblicazione, ad esempio e-mail o stampa.
seo-description: Prepare and send Interactive Communication using the Agent UI
uuid: d1a19b83-f630-4648-9ad2-a22374e31aa9
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 110c86ea-9bd8-4018-bfcc-ca33e6b3f3ba
feature: Interactive Communication
exl-id: 5ec33ef5-1722-4d29-9979-d8da32923e66
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 1%

---

# Preparare e inviare comunicazioni interattive tramite l’interfaccia utente dell’agente {#prepare-and-send-interactive-communication-using-the-agent-ui}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’interfaccia utente dell’agente consente agli agenti di preparare e inviare comunicazioni interattive al processo di pubblicazione. L’agente apporta le modifiche necessarie e invia la comunicazione interattiva a un processo di pubblicazione, ad esempio e-mail o stampa.

## Panoramica {#overview}

Dopo la creazione di una comunicazione interattiva, l’agente può aprire la comunicazione interattiva nell’interfaccia utente dell’agente e preparare una copia specifica per il destinatario immettendo i dati e gestendo il contenuto e gli allegati. Infine, l&#39;agente può inviare la comunicazione interattiva a un processo post.

Durante la preparazione della comunicazione interattiva tramite l’interfaccia utente dell’agente, l’agente gestisce i seguenti aspetti della comunicazione interattiva nell’interfaccia utente dell’agente prima di inviarla a un processo post:

* **Dati**: Nella scheda Dati dell’interfaccia utente dell’agente vengono visualizzate le variabili modificabili dall’agente e le proprietà del modello dati del modulo sbloccato nella comunicazione interattiva. Queste variabili/proprietà vengono create durante la modifica o la creazione di frammenti di documento inclusi nella comunicazione interattiva. La scheda Dati include anche tutti i campi generati nel modello di canale XDP/print. La scheda Dati viene visualizzata solo quando sono presenti variabili, proprietà del modello dati del modulo o campi nella comunicazione interattiva modificabili dall’agente.
* **Contenuto**: Nella scheda Contenuto , l’agente gestisce il contenuto, ad esempio frammenti di documento e variabili di contenuto, nella comunicazione interattiva. Durante la creazione della comunicazione interattiva nelle proprietà di tali frammenti di documento, l&#39;agente può apportare le modifiche desiderate nel frammento di documento. L&#39;agente può inoltre riordinare, aggiungere o rimuovere un frammento di documento e aggiungere interruzioni di pagina, se consentito.
* **Allegati**: La scheda Allegati viene visualizzata nell’interfaccia utente dell’agente solo se la comunicazione interattiva contiene allegati o se l’agente dispone dell’accesso alla libreria. L&#39;agente può o non può essere autorizzato a modificare o modificare gli allegati.

## Preparare la comunicazione interattiva tramite l’interfaccia utente dell’agente {#prepare-interactive-communication-using-the-agent-ui}

1. Seleziona **[!UICONTROL Forms]** > **[!UICONTROL Forms e documenti]**.
1. Seleziona la comunicazione interattiva appropriata e tocca **[!UICONTROL Interfaccia utente di Open Agent]**.

   >[!NOTE]
   >
   >L’interfaccia utente dell’agente funziona solo se la comunicazione interattiva selezionata dispone di un canale di stampa.

   ![openagentiui](assets/openagentiui.png)

   In base al contenuto e alle proprietà della comunicazione interattiva, l’interfaccia utente dell’agente viene visualizzata con le tre schede seguenti: Dati, contenuto e allegati.

   ![agentuitabs](assets/agentuitabs.png)

   Procedi all’immissione dei dati, alla gestione del contenuto e alla gestione degli allegati.

### Inserisci dati {#enter-data}

1. Nella scheda Dati, immettere i dati necessari per i campi variabili, modello dati modulo e modello di stampa (XDP). Compila tutti i campi obbligatori contrassegnati da un asterisco (&amp;ast;) per abilitare il **Invia** pulsante .

   Tocca un valore del campo dati nell’anteprima Comunicazione interattiva per evidenziare il campo dati corrispondente nella scheda Dati o viceversa.

### Gestione contenuto {#manage-content}

Nella scheda Contenuto , gestisci il contenuto, ad esempio frammenti di documento e variabili di contenuto, nella comunicazione interattiva.

1. Seleziona **[!UICONTROL Contenuto]**. Viene visualizzata la scheda del contenuto della comunicazione interattiva.

   ![agentuicontenttab](assets/agentuicontenttab.png)

1. Modificare i frammenti di documento, come necessario, nella scheda Contenuto. Per attivare il frammento pertinente nella gerarchia dei contenuti, tocca la riga o il paragrafo pertinente nell’anteprima Comunicazione interattiva oppure tocca il frammento direttamente nella gerarchia dei contenuti.

   Ad esempio, il frammento di documento con la riga &quot;Make a payment online now ...&quot; viene selezionato nell&#39;anteprima nell&#39;immagine seguente e lo stesso frammento di documento è stato selezionato nella scheda Contenuto.

   ![contentmodulefocus](assets/contentmodulefocus.png)

   Nella scheda Contenuto o Dati, tocca Evidenzia moduli selezionati nel contenuto ( ![highlightselectedmodulesincontentccr](assets/highlightselectedmodulesincontentccr.png)) in alto a sinistra nell’anteprima, è possibile disattivare o abilitare la funzionalità per passare al frammento di documento quando nell’anteprima viene toccato o selezionato il testo, il paragrafo o il campo dati pertinente.

   I frammenti che possono essere modificati dall’agente durante la creazione della comunicazione interattiva presentano la voce Modifica contenuto selezionato ( ![iconeditedselectedcontent](assets/iconeditselectedcontent.png)). Tocca l’icona Modifica contenuto selezionato per avviare il frammento in modalità di modifica e apportare le modifiche desiderate. Utilizzare le seguenti opzioni per la formattazione e la gestione del testo:

   * [Opzioni di formattazione](#formattingtext)

      * [Copia e incolla testo formattato da altre applicazioni](#pasteformattedtext)
      * [Evidenziare parti di testo](#highlightemphasize)
   * [Caratteri speciali](#specialcharacters)
   * [Scelte rapide da tastiera](/help/forms/using/keyboard-shortcuts.md)

   Per ulteriori informazioni sulle azioni disponibili per vari frammenti di documento nell&#39;interfaccia utente di Agent, vedere [Azioni e informazioni disponibili nell’interfaccia utente dell’agente](#actionsagentui).

1. Per aggiungere un’interruzione di pagina all’output di stampa della comunicazione interattiva, posizionare il cursore nel punto in cui si desidera inserire un’interruzione di pagina e selezionare Interruzione di pagina prima o Interruzione di pagina dopo ( ![pagebreakprima](assets/pagebreakbeforeafter.png)).

   Nella comunicazione interattiva viene inserito un segnaposto di interruzione di pagina esplicito. Per vedere in che modo un’interruzione di pagina esplicita influisce sulla comunicazione interattiva, vedere l’anteprima di stampa.

   ![esplicitpagebreak](assets/explicitpagebreak.png)

   Procedere alla gestione degli allegati della comunicazione interattiva.

### Gestisci allegati {#manage-attachments}

1. Seleziona **[!UICONTROL Allegato]**. Durante la creazione della comunicazione interattiva, l’interfaccia utente dell’agente visualizza gli allegati disponibili come configurati.

   È possibile scegliere di non inviare un allegato insieme alla comunicazione interattiva toccando l&#39;icona di visualizzazione e toccando la croce nell&#39;allegato per eliminarlo (se l&#39;agente è autorizzato a eliminare o nascondere l&#39;allegato) dalla comunicazione interattiva. Per gli allegati specificati come obbligatori durante la creazione della comunicazione interattiva, le icone Visualizza ed Elimina sono disabilitate.

   ![allegato sagentui](assets/attachmentsagentui.png)

1. Tocca Accesso alla libreria ( ![libraryaccess](assets/libraryaccess.png)) per accedere alla libreria dei contenuti e inserire risorse DAM come allegati.

   >[!NOTE]
   >
   >L&#39;icona Accesso libreria è disponibile solo se l&#39;accesso alla libreria è stato abilitato durante la creazione della comunicazione interattiva (nelle proprietà Contenitore documento del canale Stampa).

1. Se l’ordine degli allegati non è stato bloccato durante la creazione della comunicazione interattiva, è possibile riordinare gli allegati selezionando un allegato e toccando le frecce verso il basso e verso l’alto.
1. Utilizza Anteprima web e Anteprima di stampa per vedere se i due output sono conformi alle tue esigenze.

   Se trovi le anteprime soddisfacenti, tocca **[!UICONTROL Invia]** per inviare/inviare la comunicazione interattiva a un processo post. Oppure per apportare modifiche, esci dall’anteprima per tornare alle modifiche apportate.

## Formattazione del testo {#formattingtext}

Durante la modifica di un frammento di testo nell’interfaccia utente dell’agente, la barra degli strumenti cambia a seconda del tipo di modifica che scegli di apportare: Font, Paragrafo o Elenco:

![typeofformatting, barra degli strumenti](assets/typeofformattingtoolbar.png) ![Barra dei font](do-not-localize/fonttoolbar.png)

Barra dei font

![Barra degli strumenti Paragrafo](do-not-localize/paragraphtoolbar.png)

Barra degli strumenti Paragrafo

![Barra degli strumenti dell’elenco](do-not-localize/listtoolbar.png)

Barra degli strumenti dell’elenco

### Evidenziare/evidenziare parti di testo {#highlightemphasize}

Per evidenziare\enfatizzare parti di testo in un frammento modificabile, selezionarlo e toccare Evidenzia colore.

![highlightAgentui](assets/highlighttextagentui.png)

### Incolla il testo formattato {#pasteformattedtext}

![testo incollato](assets/pastedtext.png)

### Inserisci caratteri speciali nel testo {#specialcharacters}

L&#39;interfaccia utente dell&#39;agente ha integrato il supporto per 210 caratteri speciali. L&#39;amministratore può [aggiungi supporto per caratteri speciali più/personalizzati tramite personalizzazione](/help/forms/using/custom-special-characters.md).

#### Consegna degli allegati {#attachmentdelivery}

* Quando viene eseguito il rendering della comunicazione interattiva utilizzando le API lato server come PDF interattivo o non interattivo, PDF renderizzato contiene allegati come allegati di PDF.
* Quando un processo post associato a una comunicazione interattiva viene caricato come parte dell’interfaccia utente Invia tramite agente, gli allegati vengono passati come elenco&lt;com.adobe.idp.document> parametro inAttachmentDocs .
* I flussi di lavoro che utilizzano il meccanismo di distribuzione, ad esempio e-mail e stampa, distribuiscono anche allegati insieme alla versione PDF della comunicazione interattiva.

## Azioni e informazioni disponibili nell’interfaccia utente dell’agente {#actionsagentui}

### Frammenti di documento {#document-fragments}

![](do-not-localize/contentoptionsdocfragments.png)

* **Frecce Su/Giù**: Frecce per spostare i frammenti di documento verso l’alto o il basso nella comunicazione interattiva.
* **Elimina**: Se consentito, elimina il frammento di documento dalla comunicazione interattiva.
* **Interruzione di pagina prima** (applicabile per i frammenti secondari dell&#39;area target): Inserisce un’interruzione di pagina prima del frammento del documento.
* **Rientro**: Aumenta o diminuisce il rientro di un frammento di documento.
* **Interruzione di pagina dopo** (applicabile per i frammenti secondari dell&#39;area target): Inserisce un’interruzione di pagina dopo il frammento del documento.

![docfragoptions](assets/docfragoptions.png)

* Modifica (solo frammenti di testo): Apri l’editor Rich Text per modificare il frammento di documento di testo. Per ulteriori informazioni, consulta [Formattazione del testo](#formattingtext).

* Selezione (icona occhio): Include\esclude frammenti di documento dalla comunicazione interattiva.
* Valori non compilati (informazioni): Indica il numero di variabili non compilate nel frammento di documento.

### Elencare frammenti di documento {#list-document-fragments}

![listoptions](assets/listoptions.png)

* Inserisci linea vuota: Inserisce una nuova riga vuota.
* Selezione (icona occhio): Include\esclude frammenti di documento dalla comunicazione interattiva.
* Ignora punti/numeri: Consente di saltare elenchi puntati/numerati nel frammento di documento elenco.
* Valori non compilati (informazioni): Indica il numero di variabili non compilate nel frammento di documento.
