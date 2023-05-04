---
title: Funzione forum Q&A
seo-title: Q&A Forum Feature
description: Aggiunta della funzione forum QnA a una pagina
seo-description: Adding the QnA forum feature to a page
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
exl-id: af16f4df-ed8e-40e4-b117-3d612e122947
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 1%

---

# Funzione forum Q&amp;A {#q-a-forum-feature}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La funzione forum QnA (domande e risposte) offre ai membri della community un&#39;area in cui possono porre e rispondere a domande:

* Crea nuove domande
* Immagini in linea (con supporto per trascinamento)
* Visualizza e rispondi alle domande
* Cercare una domanda
* Aiutare a moderare il contenuto QnA
* Identificare le risposte migliori
* Sposta le domande di controllo qualità da una pagina all’altra

Questa sezione della documentazione descrive

* Aggiunta della funzione forum QnA a un sito AEM
* Impostazioni di configurazione per `QnA`component

## Aggiunta di un forum di domande e risposte a una pagina {#adding-a-q-a-forum-to-a-page}

Per aggiungere una `QnA` componente per una pagina in modalità di creazione, usate il browser componenti per individuare `Communities / QnA` e trascinarlo nella posizione desiderata su una pagina in cui dovrebbe essere visualizzato il forum QnA.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](qna-essentials.md#essentials-for-client-side) sono inclusi, è così che `QnA` apparirà il componente:

![chlimage_1-280](assets/chlimage_1-280.png)

### Configurazione di QnA {#configuring-qna}

Seleziona il `QnA` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Scheda Impostazioni {#settings-tab}

Sotto la **[!UICONTROL Impostazioni]** scheda , specifica le impostazioni per gli argomenti (domande) e le risposte (risposte):

* **[!UICONTROL Argomenti per pagina]**
Definisce il numero di domande/post visualizzati per pagina. Il valore predefinito è 10.

* **[!UICONTROL Moderato]**
Se questa opzione è selezionata, la pubblicazione di argomenti e commenti deve essere approvata prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiuso]**
Se questa opzione è selezionata, il forum è chiuso a nuove domande e commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Editor Rich Text]**
Se questa opzione è selezionata, è possibile inserire argomenti e commenti con markup. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti assegnazione tag]**
Se questa opzione è selezionata, consenti ai membri di aggiungere etichette di tag al proprio post (consulta **[!UICONTROL Campo tag]** ). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**
Se questa opzione è selezionata, consentire l&#39;aggiunta di allegati alla domanda o al commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Dimensione massima file]**
Pertinente solo se 
`Allow File Uploads` è controllata. Questo campo limita le dimensioni (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi di file consentiti]**
Pertinente solo se 
`Allow File Uploads` è controllata. Elenco di estensioni di file separate da virgola con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se sono specificati dei tipi di file, non sarà possibile caricare quelli non specificati. Il valore predefinito non è specificato in modo che tutti i tipi di file siano consentiti.

* **[!UICONTROL Dimensione massima file immagine allegato]**
Pertinente solo se l’opzione Consenti caricamenti file è selezionata. Numero massimo di byte di un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti seguenti]**
Se questa opzione è selezionata, includi la seguente funzione per i post del forum, che consente ai membri di essere [notificato](notifications.md) di nuovi posti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti ritaglio]**
Se questa opzione è selezionata, gli argomenti del forum possono essere inseriti in cima all’elenco. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti sottoscrizioni e-mail]**
Se questa opzione è selezionata, consente ai membri di ricevere notifiche sui nuovi post via e-mail ([abbonamento](subscriptions.md)). Richiede `Allow Following` da controllare e [e-mail configurata](email.md). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti risposte]**
Se questa opzione è selezionata, consentire le risposte ai commenti inviati alla domanda. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e argomenti]**
Se questa opzione è selezionata, consentire ai membri di eliminare i commenti e le domande che hanno pubblicato. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti votazione]**
Se questa opzione è selezionata, includi la funzionalità di voto con una domanda. Il valore predefinito è deselezionato.

* **[!UICONTROL Sposta La Risposta Selezionata In Alto]**
Se questa opzione è selezionata, la prima risposta visualizzata è una risposta selezionata. Il valore predefinito è selezionato.

* **[!UICONTROL Badge di visualizzazione]**
Se selezionato, visualizza guadagnato e assegnato [badge](implementing-scoring.md) con il post di blog di un membro. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**
se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è deselezionato.

#### Scheda Moderazione utente {#user-moderation-tab}

Sotto la **[!UICONTROL Moderazione utente]** scheda , specifica come vengono gestiti gli argomenti pubblicati (domande) e le risposte (contenuto generato dall’utente). Per ulteriori informazioni, consulta [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

* **[!UICONTROL Rifiuta risposte]**
Se questa opzione è selezionata, ai moderatori di membri affidabili sarà consentito negare le risposte pubblicate e impedire che la risposta appaia sul forum Q&amp;A pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri argomenti]**
Se questa opzione è selezionata, i moderatori di membri affidabili possono chiudere una domanda (argomento) per ulteriori modifiche e risposte e possono anche riaprire una domanda. Il valore predefinito è deselezionato.

* **[!UICONTROL Sposta argomenti]**
Se questa opzione è selezionata, consenti ai moderatori lato pubblicazione di spostare le domande. Il valore predefinito è deselezionato.

* **[!UICONTROL Contrassegna post]**
Se questa opzione è selezionata, consentire ai membri di contrassegnare le domande o le risposte di altri utenti come inadeguate. Il valore predefinito è deselezionato.

* **[!UICONTROL Elenco dei motivi del contrassegno]**
Se questa opzione è selezionata, consentire ai membri di scegliere, da un elenco a discesa, il motivo per cui contrassegnano una domanda o una risposta come inappropriata. Il valore predefinito è deselezionato.

* **[!UICONTROL Motivo contrassegno personalizzato]**
Se questa opzione è selezionata, consentire ai membri di inserire il proprio motivo per contrassegnare una domanda o una risposta come inappropriata. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia moderazione]**
Immettere il numero di volte in cui una domanda o una risposta deve essere contrassegnata dai membri prima che i moderatori siano informati. Il valore predefinito è 1 (una volta).

* **[!UICONTROL Limite di flag]**
Immetti il numero di volte in cui una domanda o una risposta deve essere contrassegnata prima che sia nascosta dalla visualizzazione pubblica. Se è impostato su -1, la domanda o la risposta contrassegnata non viene mai nascosta dalla visualizzazione pubblica. In caso contrario, questo numero deve essere maggiore o uguale alla soglia di moderazione. Il valore predefinito è 5.

#### Scheda Campo tag {#tag-field-tab}

Sotto la **[!UICONTROL Campo tag]** , i tag che possono essere applicati, se consentiti nella **[!UICONTROL Impostazioni]** sono limitati in base ai namespace selezionati.

* **[!UICONTROL Namespace consentiti]**
Pertinente se 
`Allow Tagging` è controllato sotto **Impostazioni** scheda . I tag che possono essere applicati sono limitati a quelli nelle categorie dello spazio dei nomi selezionate. L’elenco dei namespace include sia &quot;Tag standard&quot; (lo spazio dei nomi predefinito) che &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, il che significa che tutti i namespace sono consentiti.

* **[!UICONTROL Limite di suggerimenti]**
Immettere il numero di tag da visualizzare come suggerimento al membro che pubblica sul forum. Un valore di 
`-1` non significa limiti. Il valore predefinito è 0.

#### Scheda Impostazioni di ordinamento {#sort-settings-tab}

Sotto la **[!UICONTROL Impostazioni di ordinamento]** specificare l&#39;ordine dei commenti inviati quando vengono visualizzati.

* **[!UICONTROL Ordina per]**
Seleziona tutte le selezioni di ordinamento consentite: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Il valore predefinito è `Newest, Oldest, Last Updated`.

* **[!UICONTROL Imposta come predefinito]**
Passa il mouse verso il basso per selezionare una delle opzioni di ordinamento selezionate da visualizzare come impostazione predefinita. Il valore predefinito è 
`Newest`.

* **[!UICONTROL Selezionare le opzioni di ora per l’ordinamento di Analytics]**
Abbassi per selezionare uno dei 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. Il valore predefinito è `All`.

## Esperienza dei visitatori del sito {#site-visitor-experience}

### Identificazione delle risposte {#identifying-answers}

Una risposta può essere contrassegnata come risposta corretta o utile utilizzando `Select Answer` pulsante . Una volta che una domanda è contrassegnata come risposta, non è possibile selezionare un’altra risposta finché la prima non è stata deselezionata utilizzando la `Unmark Chosen Answer`pulsante .

Una volta selezionato come risposta valida, potrebbe essere deselezionato utilizzando il `Unmark Chosen Answer` pulsante .

Una volta che una risposta è stata selezionata come risposta valida, l&#39;indicazione che la domanda è stata `Answered`viene visualizzato accanto all’argomento della domanda nella pagina QnA principale.

### Moderatori e amministratori {#moderators-and-administrators}

Quando l&#39;utente connesso dispone di privilegi di moderatore o amministratore, può eseguire le attività di moderazione consentite dalla configurazione del componente, indipendentemente da chi ha creato la domanda o la risposta.

Hanno anche la capacità di identificare le risposte.

### Membri {#members}

Quando il visitatore del sito è connesso, a seconda della configurazione, può

* Pubblica una nuova domanda
* Modificare o eliminare le domande create
* Possono anche contrassegnare le domande o le risposte di altri
* Può identificare le risposte alle domande che ha creato

### Anonimo {#anonymous}

I visitatori del sito che non hanno effettuato l&#39;accesso possono solo leggere le domande pubblicate e le risposte, tradurle se supportate, ma non possono aggiungere domande o risposte, né contrassegnare i post di altri.

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Nozioni di base su QnA](qna-essentials.md) per sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, vedi [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

Per assegnare tag agli argomenti e ai commenti pubblicati, vedi [Assegnazione tag ai contenuti generati dagli utenti](tag-ugc.md).
