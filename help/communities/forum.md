---
title: Funzione forum
seo-title: Forum Feature
description: Aggiungere e configurare la funzione forum
seo-description: How to add and configure the forum feature
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 1%

---

# Funzione forum {#forum-feature}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La funzione forum fornisce un’area per i visitatori del sito con accesso (membri della community) nell’ambiente di pubblicazione per:

* Creazione di nuovi argomenti
* Visualizzare e rispondere agli argomenti
* Seguire un argomento
* Cercare un forum
* Aiutare a moderare il contenuto del forum
* Spostare gli argomenti del forum da una pagina all&#39;altra

Questa sezione della documentazione descrive

* Aggiunta della funzione forum a un sito AEM
* Impostazioni di configurazione per `Forum`component

## Aggiunta di un forum a una pagina {#adding-a-forum-to-a-page}

Per aggiungere una `Forum` componente per una pagina in modalità di creazione, usate il browser componenti per individuare

* `Communities / Forum`

Trascinala nella posizione desiderata su una pagina in cui dovrebbe essere visualizzato il forum.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](essentials-forum.md#essentials-for-client-side) sono inclusi, è così che `Forum`apparirà il componente:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configurazione di un forum {#configuring-a-forum}

Seleziona il `Forum` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Scheda Impostazioni {#settings-tab}

Sotto la **[!UICONTROL Impostazioni]** scheda , specifica le impostazioni per gli argomenti e le risposte:

* **[!UICONTROL Argomenti per pagina]**
Definisce il numero di argomenti/post visualizzati per pagina. Il valore predefinito è 10.

* **[!UICONTROL Moderato]**
Se questa opzione è selezionata, la pubblicazione di argomenti e commenti deve essere approvata prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiuso]**
Se questa opzione è selezionata, il forum viene chiuso ai nuovi argomenti e commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Editor Rich Text]**
Se questa opzione è selezionata, è possibile inserire argomenti e commenti con markup. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti assegnazione tag]**
Se questa opzione è selezionata, consenti ai membri di aggiungere etichette di tag al proprio post (consulta **[!UICONTROL Campo tag]** ). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**
Se questa opzione è selezionata, consenti l’aggiunta di allegati all’argomento o al commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti seguenti]**
Se questa opzione è selezionata, includi la seguente funzione per i post del forum, che consente ai membri di essere [notificato](notifications.md) di nuovi posti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti ritaglio]**
Se questa opzione è selezionata, gli argomenti del forum possono essere inseriti in cima all’elenco. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**
se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti sottoscrizioni e-mail]**
Se questa opzione è selezionata, consente ai membri di ricevere notifiche sui nuovi post via e-mail ([abbonamento](subscriptions.md)). Richiede `Allow Following` da controllare e [e-mail configurata](email.md). Il valore predefinito è deselezionato.

* **[!UICONTROL Dimensione massima file]**
Pertinente solo se 
`Allow File Uploads` è controllata. Questo campo limita le dimensioni (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi di file consentiti]**
Pertinente solo se 
`Allow File Uploads` è controllata. Elenco di estensioni di file separate da virgola con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se sono specificati dei tipi di file, non sarà possibile caricare quelli non specificati. Il valore predefinito non è specificato in modo che tutti i tipi di file siano consentiti.

* **[!UICONTROL Dimensione massima file immagine allegato]**
Pertinente solo se l’opzione Consenti caricamenti file è selezionata. Numero massimo di byte di un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti risposte thread]**
Se questa opzione è selezionata, consenti risposte ai commenti pubblicati nell&#39;argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e argomenti]**
Se questa opzione è selezionata, consentire ai membri di eliminare i commenti e gli argomenti pubblicati. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti votazione]**
Se questa opzione è selezionata, includi la funzionalità Voto con un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Mostra breadcrumb]**
Se questa opzione è selezionata, verranno visualizzate le breadcrumb di navigazione nelle pagine dell’argomento. Il valore predefinito è selezionato.

* **[!UICONTROL Badge di visualizzazione]**
Se selezionato, visualizza guadagnato e assegnato [badge](implementing-scoring.md) con il post di blog di un membro. Il valore predefinito è deselezionato.

>[!NOTE]
>
>Può essere necessario controllare entrambi `AllowThreaded Replies` e `Allow users to Delete Comments and Topics` per abilitare i commenti su un argomento.

### Scheda Moderazione utente {#user-moderation-tab}

Sotto la **[!UICONTROL Moderazione utente]** scheda , specifica come vengono gestiti gli argomenti e le risposte pubblicati (contenuto generato dall’utente). Per ulteriori informazioni, consulta [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

* **[!UICONTROL Rifiuta post]**
Se questa opzione è selezionata, ai moderatori di membri affidabili sarà consentito di negare i post e impedire che il post appaia sul forum pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri argomenti]**
Se questa opzione è selezionata, i moderatori di membri attendibili possono chiudere un argomento per ulteriori modifiche e commenti e riaprire un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Sposta argomenti]**
Se questa opzione è selezionata, consenti ai moderatori lato pubblicazione di spostare gli argomenti. Il valore predefinito è selezionato.

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
Pertinente se `Allow Tagging` è controllato sotto **[!UICONTROL Impostazioni]** scheda . I tag che possono essere applicati sono limitati a quelli nelle categorie dello spazio dei nomi selezionate. L’elenco dei namespace include sia &quot;Tag standard&quot; (lo spazio dei nomi predefinito) che &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, il che significa che tutti i namespace sono consentiti.

* **[!UICONTROL Limite di suggerimenti]**
Immettere il numero di tag da visualizzare come suggerimento al membro che pubblica sul forum. Il valore predefinito è 
**-** 1 (nessun limite).

### Scheda Traduzione {#translation-tab}

Sotto la **[!UICONTROL Traduzione]** Se la traduzione è abilitata per il sito community, la traduzione può essere impostata per tradurre l&#39;intero argomento o i post selezionati.

* **[!UICONTROL Traduci tutto]**
Se questa opzione è selezionata, il thread del forum viene tradotto nella lingua preferita dell&#39;utente. Il valore predefinito è deselezionato.

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

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Nozioni di base sul forum](essentials-forum.md) per sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, vedi [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

Per assegnare tag agli argomenti e ai commenti pubblicati, vedi [Assegnazione tag ai contenuti generati dagli utenti](tag-ugc.md).

Per la traduzione degli argomenti e dei commenti pubblicati, vedi [Traduzione di contenuti generati dagli utenti](translate-ugc.md).
