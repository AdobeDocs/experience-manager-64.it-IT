---
title: Funzionalità forum D e R
seo-title: Funzionalità forum D e R
description: Aggiunta della funzione forum QnA a una pagina
seo-description: Aggiunta della funzione forum QnA a una pagina
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# Funzione forum D e R {#q-a-forum-feature}

## Introduzione {#introduction}

La funzione di forum QnA (domande e risposte) offre ai membri della community un&#39;area in cui porre e rispondere alle domande:

* Creare nuove domande
* Immagini in linea (con supporto per trascinamento)
* Visualizzare e rispondere alle domande
* Ricerca di una domanda
* Aiutare a moderare il contenuto QnA
* Identificare le risposte migliori
* Spostare le domande QnA da una pagina all&#39;altra

Questa sezione della documentazione descrive

* Aggiunta della funzione forum QnA a un sito AEM
* Impostazioni di configurazione per il componente `QnA`

## Aggiunta di un forum D e R a una pagina {#adding-a-q-a-forum-to-a-page}

Per aggiungere un componente `QnA` a una pagina in modalità di creazione, utilizzate il browser componenti per individuare `Communities / QnA` e trascinatelo nella posizione desiderata su una pagina in cui dovrebbe comparire il forum QnA.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando vengono incluse le [librerie lato client ](qna-essentials.md#essentials-for-client-side), viene visualizzato il componente `QnA`:

![chlimage_1-280](assets/chlimage_1-280.png)

### Configurazione di QnA {#configuring-qna}

Selezionare il componente `QnA` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### Scheda Impostazioni {#settings-tab}

Nella scheda **[!UICONTROL Impostazioni]**, specificate le impostazioni per gli argomenti (domande) e le risposte (risposte):

* **[!UICONTROL Argomenti per]**
paginaDefinisce il numero di domande/post mostrati per pagina. Il valore predefinito è 10.

* ****
Moderato: se questa opzione è selezionata, la pubblicazione di argomenti e commenti deve essere approvata prima che vengano visualizzati in un sito di pubblicazione. Il valore predefinito è deselezionato.

* ****
ChiusoSe questa opzione è selezionata, il forum è chiuso alle nuove domande e commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Rich Text]**
EditorSe questa opzione è selezionata, è possibile immettere commenti e argomenti con la marcatura. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
tag: se questa opzione è selezionata, consente ai membri di aggiungere etichette di tag al proprio post (consultate la scheda  **[!UICONTROL Tag]** fieldtab). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
caricamenti file: se questa opzione è selezionata, consente l’aggiunta di allegati alla domanda o al commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Max]**
Dimensione fileRilevante solo se 
`Allow File Uploads` è selezionato. Questo campo limita la dimensione (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi]**
di file consentitiRilevanti solo se 
`Allow File Uploads` è selezionato. Un elenco separato da virgole di estensioni di file con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati dei tipi di file, non sarà possibile caricare quelli non specificati. Il valore predefinito non è specificato, pertanto tutti i tipi di file sono consentiti.

* **[!UICONTROL Max Allega]**
dimensione file immaginePertinente solo se l&#39;opzione Consenti caricamenti file è selezionata. Numero massimo di byte di cui può disporre un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti]**
seguenti: se questa opzione è selezionata, includete la seguente funzione per i post dei forum, che consente ai membri di ricevere  [](notifications.md) notifiche sui nuovi post. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
blocco: se questa opzione è selezionata, gli argomenti del forum possono essere bloccati in cima all’elenco di argomenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
iscrizioni e-mailSe questa opzione è selezionata, consentite ai membri di ricevere notifiche sui nuovi post tramite e-mail ([iscrizione](subscriptions.md)). È necessario che `Allow Following` sia selezionato e che [e-mail sia configurato](email.md). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
risposte: se questa opzione è selezionata, consenti risposte ai commenti inviati alla domanda. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e]**
argomentiSe questa opzione è selezionata, consente ai membri di eliminare i commenti e le domande che hanno pubblicato. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
votazione: se questa opzione è selezionata, includete la funzione di votazione con una domanda. Il valore predefinito è deselezionato.

* **[!UICONTROL Sposta la risposta selezionata all&#39;]**
inizioSe questa opzione è selezionata, la prima risposta visualizzata è una risposta selezionata. Il valore predefinito è selezionato.

* **[!UICONTROL Visualizza]**
badge: se questa opzione è selezionata, vengono visualizzati  [](implementing-scoring.md) i badgesgesin acquisiti e assegnati con il post di blog di un membro. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuti]**
contenuti contenuti se questa opzione è selezionata, l’idea può essere identificata come contenuto [ ](featured.md)disponibile. Il valore predefinito è deselezionato.

#### Scheda Moderazione utente {#user-moderation-tab}

Nella scheda **[!UICONTROL Moderazione utente]**, specificate in che modo vengono gestiti gli argomenti (domande) e le risposte (contenuto generato dall&#39;utente) inviati. Per ulteriori informazioni, vedere [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

* **[!UICONTROL Rifiuta]**
risposte: se questa opzione è attivata, i moderatori di membri attendibili potranno negare le risposte pubblicate e impedire che la risposta venga visualizzata nel forum D e R pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri]**
argomentiSe questa opzione è attivata, i moderatori di membri attendibili potrebbero chiudere una domanda (argomento) per apportare ulteriori modifiche e risposte e potrebbe anche riaprire una domanda. Il valore predefinito è deselezionato.

* **[!UICONTROL Sposta]**
argomenti: se questa opzione è selezionata, i moderatori lato pubblicazione possono spostare le domande. Il valore predefinito è deselezionato.

* **[!UICONTROL Contrassegna]**
post: se questa opzione è selezionata, consentire ai membri di contrassegnare le domande o le risposte di altri utenti in modo inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Flag Reason]**
ListSe questa opzione è selezionata, consente ai membri di scegliere, da un elenco a discesa, il motivo per cui segnalano una domanda o una risposta non corretta. Il valore predefinito è deselezionato.

* **[!UICONTROL Custom Flag]**
Reason (Motivo contrassegno personalizzato): se questa opzione è selezionata, consente ai membri di inserire il proprio motivo per cui la domanda o la risposta è contrassegnata come non corretta. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia]**
moderazioneConsente di specificare quante volte i membri devono contrassegnare una domanda o una risposta prima che i moderatori ne vengano informati. Il valore predefinito è 1 (una volta).

* **[!UICONTROL Limite di]**
contrassegnazioneConsente di specificare quante volte deve essere segnalata una domanda o una risposta prima che venga nascosta dalla visualizzazione pubblica. Se è impostato su -1, la domanda o la risposta contrassegnata non viene mai nascosta dalla visualizzazione pubblica. In caso contrario, questo numero deve essere maggiore o uguale alla soglia di moderazione. Il valore predefinito è 5.

#### Scheda Campo tag {#tag-field-tab}

Nella scheda **[!UICONTROL Tag field]** (Campo tag), i tag che possono essere applicati, se consentiti nella scheda **[!UICONTROL Settings]** (Impostazioni), sono limitati in base agli spazi dei nomi scelti.

* **[!UICONTROL Spazi dei]**
nomi consentitiPertinente se 
`Allow Tagging` è selezionato sotto la  **** scheda Settingstab. I tag che possono essere applicati sono limitati a quelli all&#39;interno delle categorie dello spazio nomi selezionate. L’elenco degli spazi dei nomi include &quot;Tag standard&quot; (lo spazio dei nomi predefinito) e &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, il che significa che tutti gli spazi dei nomi sono consentiti.

* **[!UICONTROL Suggerimento]**
Limite: consente di immettere il numero di tag da visualizzare come suggerimento al membro che invia il messaggio al forum. Un valore di 
`-1` significa nessun limite. Il valore predefinito è 0.

#### Scheda Ordina impostazioni {#sort-settings-tab}

Nella scheda **[!UICONTROL Ordina impostazioni]**, specificare in che modo i commenti inviati vengono ordinati quando vengono visualizzati.

* **[!UICONTROL Ordina]**
perControlla tutte le selezioni di ordinamento consentite: 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Il valore predefinito è `Newest, Oldest, Last Updated`.

* **[!UICONTROL Imposta come]**
DefaultPull giù per selezionare una delle opzioni di ordinamento selezionate da visualizzare come predefinita. Il valore predefinito è 
`Newest`.

* **[!UICONTROL Seleziona Opzioni ora per Analytics]**
SortingPull in basso per selezionare una delle opzioni 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. Il valore predefinito è `All`.

## Esperienza visitatori del sito {#site-visitor-experience}

### Identificazione delle risposte {#identifying-answers}

Una risposta può essere contrassegnata come una risposta corretta o utile utilizzando il pulsante `Select Answer`. Una volta che una domanda è contrassegnata come Risposta, non è possibile selezionare un&#39;altra risposta fino a quando la prima non è stata deselezionata utilizzando il pulsante `Unmark Chosen Answer`.

Una volta selezionata come risposta valida, la selezione potrebbe essere annullata utilizzando il pulsante `Unmark Chosen Answer`.

Una volta selezionata una risposta come risposta valida, viene visualizzata un&#39;indicazione che la domanda è stata `Answered`accanto all&#39;argomento della domanda nella pagina QnA principale.

### Moderatori e amministratori {#moderators-and-administrators}

Quando l’utente che ha effettuato l’accesso dispone di privilegi di moderatore o amministratore, può eseguire le attività di moderazione consentite dalla configurazione del componente, indipendentemente da chi ha creato la domanda o la risposta.

Hanno anche la capacità di identificare le risposte.

### Membri {#members}

Quando il visitatore del sito ha effettuato l&#39;accesso, a seconda della configurazione, può

* Pubblica una nuova domanda
* Modificare o eliminare le domande create
* Possono anche contrassegnare altre domande o risposte
* Può identificare le risposte alle domande che hanno creato

### Anonimo {#anonymous}

I visitatori del sito che non hanno effettuato l&#39;accesso possono solo leggere le domande pubblicate e le risposte, tradurle se supportate, ma non aggiungere né una domanda né una risposta, né contrassegnare i post di altri utenti.

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [QnA Essentials](qna-essentials.md) per gli sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, vedere [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

Per assegnare tag agli argomenti e ai commenti inviati, consultate [Assegnazione di tag ai contenuti generati dall&#39;utente](tag-ugc.md).
