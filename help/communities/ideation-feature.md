---
title: Funzione ideativa
seo-title: Ideation Feature
description: Aggiunta e configurazione della funzione Ideazione
seo-description: Adding and configuring the Ideation feature
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 1%

---

# Funzione ideativa {#ideation-feature}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La funzione di identificazione fornisce un’area per i visitatori del sito con accesso (membri della community) nell’ambiente di pubblicazione per:

* Creare idee da condividere con la community
* Visualizza e commenta le idee
* Segui un&#39;idea
* Vota un&#39;idea

Questa sezione della documentazione descrive

* Aggiunta della funzione di identificazione a un sito AEM
* Impostazioni di configurazione per il componente Ideazione

## Aggiunta di un’idea a una pagina {#adding-a-ideation-to-a-page}

Per aggiungere una `Ideation` componente per una pagina in modalità di creazione, usate il browser componenti per individuare `Communities / Ideation` e trascinatela nella posizione desiderata su una pagina in cui dovrebbe essere visualizzata l’idea.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](ideation.md#essentials-for-client-side) sono inclusi, è così che `Ideation`apparirà il componente:

![chlimage_1-29](assets/chlimage_1-29.png)

## Configurazione di un’idea {#configuring-an-ideation}

Seleziona il `Ideation` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Scheda Impostazioni {#settings-tab}

Sotto la **[!UICONTROL Impostazioni]** scheda , specifica le impostazioni per idee e commenti:

* **[!UICONTROL Titolo ideazione]**
Il titolo visualizzato dell&#39;idea. Il valore predefinito è 
`Ideation`.

* **[!UICONTROL Descrizione ideazione]**
Descrizione da visualizzare come sottotitolo dell’idea. Il valore predefinito non è una descrizione.

* **[!UICONTROL Argomenti per pagina]**
Definisce il numero di idee/post visualizzati per pagina. Il valore predefinito è 10.

* **[!UICONTROL Moderato]**
Se questa opzione è selezionata, è necessario approvare la pubblicazione di idee e commenti prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiuso]**
Se questa opzione è selezionata, il forum di ideazione è chiuso a nuove idee e commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Editor Rich Text]**
Se questa opzione è selezionata, è possibile inserire con markup idee e commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti assegnazione tag]**
Se questa opzione è selezionata, consenti ai membri di aggiungere etichette di tag al proprio post (consulta **[!UICONTROL Campo tag]** ). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**
Se questa opzione è selezionata, consenti l’aggiunta di allegati all’idea o al commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Dimensione massima file]**
Pertinente solo se 
`Allow File Uploads` è controllata. Questo campo limita le dimensioni (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi di file consentiti]**
Pertinente solo se 
`Allow File Uploads` è controllata. Elenco di estensioni di file separate da virgola con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se sono specificati dei tipi di file, non sarà possibile caricare quelli non specificati. Il valore predefinito non è specificato in modo che tutti i tipi di file siano consentiti.

* **[!UICONTROL Dimensione massima file immagine allegato]**
Pertinente solo se l’opzione Consenti caricamenti file è selezionata. Numero massimo di byte di un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti risposte]**
Se questa opzione è selezionata, consenti risposte ai commenti pubblicati sull&#39;idea. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e argomenti]**
Se questa opzione è selezionata, consentire ai membri di eliminare i commenti e le idee che hanno pubblicato. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti seguenti]**
Se questa opzione è selezionata, includi la seguente funzione per i post di idee, che consente ai membri di essere [notificato](notifications.md) di nuovi posti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti sottoscrizioni e-mail]**
Se questa opzione è selezionata, consente ai membri di ricevere notifiche sui nuovi post via e-mail ([abbonamento](subscriptions.md)). Richiede `Allow Following` da controllare e [e-mail configurata](email.md). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti votazione]**
Se questa opzione è selezionata, consentire la votazione dei commenti di un&#39;idea. Il valore predefinito è deselezionato.

* **[!UICONTROL Badge di visualizzazione]**
Se selezionato, visualizza guadagnato e assegnato [badge](implementing-scoring.md) con l&#39;idea di un membro. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**
se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è deselezionato.

### Scheda Moderazione utente {#user-moderation-tab}

Sotto la **[!UICONTROL Moderazione utente]** , specifica come vengono gestite le idee e i commenti pubblicati (contenuto generato dall’utente). Per ulteriori informazioni, consulta [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

* **[!UICONTROL Rifiuta post]**
Se questa opzione è selezionata, ai moderatori di membri affidabili sarà consentito di negare i post e impedire che il post appaia sul forum pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri argomenti]**
Se questa opzione è selezionata, i moderatori di membri attendibili possono chiudere un argomento per ulteriori modifiche e commenti e riaprire un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Contrassegna post]**
Se questa opzione è selezionata, consentire ai membri di contrassegnare gli argomenti o i commenti di altri come inappropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Elenco dei motivi del contrassegno]**
Se questa opzione è selezionata, consenti ai membri di scegliere, da un elenco a discesa, il motivo per cui contrassegnano un argomento o un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Motivo contrassegno personalizzato]**
Se questa opzione è selezionata, consenti ai membri di inserire il proprio motivo per contrassegnare un argomento o un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia moderazione]**
Immettere il numero di volte in cui un argomento o un commento deve essere segnalato dai membri prima che i moderatori ne vengano informati. Il valore predefinito è 1 (una volta).

* **[!UICONTROL Limite di flag]**
Immetti il numero di volte in cui un argomento o un commento deve essere contrassegnato prima che sia nascosto dalla visualizzazione pubblica. Se è impostato su -1, l&#39;argomento o il commento contrassegnato non viene mai nascosto dalla visualizzazione pubblica. In caso contrario, questo numero deve essere maggiore o uguale alla soglia di moderazione. Il valore predefinito è 5.

### Scheda Campo tag {#tag-field-tab}

Sotto la **[!UICONTROL Campo tag]** , i tag che possono essere applicati, se consentiti nella **[!UICONTROL Impostazioni]** sono limitati in base ai namespace selezionati.

* **[!UICONTROL Namespace consentiti]**
Pertinente se 
`Allow Tagging` è controllato sotto **Impostazioni** scheda . I tag che possono essere applicati sono limitati a quelli nelle categorie dello spazio dei nomi selezionate. L’elenco dei namespace include sia &quot;Tag standard&quot; (lo spazio dei nomi predefinito) che &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, il che significa che tutti i namespace sono consentiti.

* **[!UICONTROL Limite di suggerimenti]**
Immettere il numero di tag da visualizzare come suggerimento al membro che pubblica sul forum. Un valore di 
**-** 1 significa nessun limite. Il valore predefinito è 0.

### Scheda Impostazioni di ordinamento {#sort-settings-tab}

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

### Creazione di un&#39;idea {#creating-idea}

Come per tutte le funzionalità di Communities, se non hai effettuato l’accesso, un visitatore del sito può solo leggere idee e visualizzare opinioni altrui (tramite commenti e votanti/mi piace).

Una volta effettuato l&#39;accesso, un membro può creare una nuova idea.

![chlimage_1-32](assets/chlimage_1-32.png)

Prima di presentare l&#39;idea, è possibile per il membro salvare una bozza.

Selezionando la `Save as Draft` viene salvata una bozza.

![chlimage_1-33](assets/chlimage_1-33.png)

Quando si visualizzano le bozze salvate nel `My Drafts` scheda , seleziona `Read More` per tornare alla modalità di modifica:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Feedback {#providing-feedback}

Una volta pubblicata l’idea, altri membri possono accedervi, aprire l’idea ( `Read More`) e come l&#39;idea, aggiungendo così al conteggio dei voti, e fare commenti.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Idee Essenziali](ideation.md) per sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, vedi [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

Per assegnare tag agli argomenti e ai commenti pubblicati, vedi [Assegnazione tag ai contenuti generati dagli utenti](tag-ugc.md).
