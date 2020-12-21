---
title: Funzione forum
seo-title: Funzione forum
description: Come aggiungere e configurare la funzione forum
seo-description: Come aggiungere e configurare la funzione forum
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# Funzione forum {#forum-feature}

## Introduzione {#introduction}

La funzione forum fornisce un’area per i visitatori del sito che hanno effettuato l’accesso (membri della community) nell’ambiente di pubblicazione per:

* Creazione di nuovi argomenti
* Visualizzazione e risposta agli argomenti
* Seguire un argomento
* Ricerca in un forum
* Aiutare a moderare il contenuto del forum
* Spostare gli argomenti dei forum da una pagina all’altra

Questa sezione della documentazione descrive

* Aggiunta della funzione forum a un sito AEM
* Impostazioni di configurazione per il componente `Forum`

## Aggiunta di un forum a una pagina {#adding-a-forum-to-a-page}

Per aggiungere un componente `Forum` a una pagina in modalità di creazione, usate il browser componenti per individuare

* `Communities / Forum`

Trascinala nella stessa posizione di una pagina in cui dovrebbe essere visualizzato il forum.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando sono incluse le [librerie lato client ](essentials-forum.md#essentials-for-client-side), viene visualizzato il componente `Forum`seguente:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configurazione di un forum {#configuring-a-forum}

Selezionare il componente `Forum` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### Scheda Impostazioni {#settings-tab}

Nella scheda **[!UICONTROL Impostazioni]**, specificare le impostazioni per gli argomenti e le risposte:

* **[!UICONTROL Argomenti per]**
paginaDefinisce il numero di topic/post mostrati per pagina. Il valore predefinito è 10.

* ****
Moderato: se questa opzione è selezionata, la pubblicazione di argomenti e commenti deve essere approvata prima che vengano visualizzati in un sito di pubblicazione. Il valore predefinito è deselezionato.

* ****
Chiuso: se questa opzione è selezionata, il forum è chiuso ai nuovi argomenti e commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Rich Text]**
EditorSe questa opzione è selezionata, è possibile immettere commenti e argomenti con la marcatura. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
tag: se questa opzione è selezionata, consente ai membri di aggiungere etichette di tag al proprio post (consultate la scheda  **[!UICONTROL Tag]** fieldtab). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
caricamenti fileSe questa opzione è selezionata, consentire l&#39;aggiunta di allegati all&#39;argomento o al commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
seguenti: se questa opzione è selezionata, includete la seguente funzione per i post dei forum, che consente ai membri di ricevere  [](notifications.md) notifiche sui nuovi post. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
blocco: se questa opzione è selezionata, gli argomenti del forum possono essere bloccati in cima all’elenco di argomenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuti]**
contenuti contenuti se questa opzione è selezionata, l’idea può essere identificata come contenuto [ ](featured.md)disponibile. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
iscrizioni e-mailSe questa opzione è selezionata, consentite ai membri di ricevere notifiche sui nuovi post tramite e-mail ([iscrizione](subscriptions.md)). È necessario che `Allow Following` sia selezionato e che [e-mail sia configurato](email.md). Il valore predefinito è deselezionato.

* **[!UICONTROL Max]**
Dimensione fileRilevante solo se 
`Allow File Uploads` è selezionato. Questo campo limita la dimensione (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi]**
di file consentitiRilevanti solo se 
`Allow File Uploads` è selezionato. Un elenco separato da virgole di estensioni di file con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati dei tipi di file, non sarà possibile caricare quelli non specificati. Il valore predefinito non è specificato, pertanto tutti i tipi di file sono consentiti.

* **[!UICONTROL Max Allega]**
dimensione file immaginePertinente solo se l&#39;opzione Consenti caricamenti file è selezionata. Numero massimo di byte di cui può disporre un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti]**
risposte threadSe questa opzione è selezionata, consenti risposte ai commenti inviati all&#39;argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e]**
argomentiSe questa opzione è selezionata, i membri possono eliminare commenti e argomenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
votazione: se questa opzione è selezionata, includete la funzione di votazione con un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Mostra]**
breadcrumbSe questa opzione è selezionata, vengono mostrate le breadcrumb di navigazione nelle pagine dell&#39;argomento. Il valore predefinito è selezionato.

* **[!UICONTROL Visualizza]**
badge: se questa opzione è selezionata, vengono visualizzati  [](implementing-scoring.md) i badgesgesin acquisiti e assegnati con il post di blog di un membro. Il valore predefinito è deselezionato.

>[!NOTE]
>
>Potrebbe essere necessario controllare sia `AllowThreaded Replies` che `Allow users to Delete Comments and Topics` per abilitare i commenti su un argomento.

### Scheda Moderazione utente {#user-moderation-tab}

Nella scheda **[!UICONTROL Moderazione utente]**, specificare la modalità di gestione degli argomenti e delle risposte inviati (contenuto generato dall&#39;utente). Per ulteriori informazioni, vedere [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

* **[!UICONTROL Rifiuta]**
postSe questa opzione è selezionata, i moderatori di membri attendibili potranno negare i post e impedire che vengano visualizzati nel forum pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri]**
argomentiSe questa opzione è attivata, i moderatori di membri attendibili potrebbero chiudere un argomento per ulteriori modifiche e commenti e riaprire un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Sposta]**
argomenti: se questa opzione è selezionata, i moderatori lato pubblicazione possono spostare gli argomenti. Il valore predefinito è selezionato.

* **[!UICONTROL Contrassegna]**
post: se questa opzione è selezionata, consentire ai membri di contrassegnare gli argomenti o i commenti di altri utenti in modo inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Flag Reason]**
ListSe questa opzione è selezionata, consente ai membri di scegliere, da un elenco a discesa, il motivo per cui l&#39;argomento o il commento vengono contrassegnati come non appropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Custom Flag]**
Reason (Motivo contrassegno personalizzato): se questa opzione è selezionata, consente ai membri di inserire il proprio motivo per cui l&#39;argomento o il commento viene contrassegnato come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia]**
moderazioneConsente di specificare quante volte un argomento o un commento deve essere contrassegnato dai membri prima che i moderatori ne vengano informati. Il valore predefinito è 1 (una volta).

* **[!UICONTROL Limite di]**
contrassegnazioneConsente di specificare quante volte un argomento o un commento deve essere contrassegnato prima che venga nascosto dalla visualizzazione pubblica. Se è impostato su -1, l&#39;argomento o il commento contrassegnato non viene mai nascosto dalla visualizzazione pubblica. In caso contrario, questo numero deve essere maggiore o uguale alla soglia di moderazione. Il valore predefinito è 5.

### Scheda Campo tag {#tag-field-tab}

Nella scheda **[!UICONTROL Tag field]** (Campo tag), i tag che possono essere applicati, se consentiti nella scheda **[!UICONTROL Settings]** (Impostazioni), sono limitati in base agli spazi dei nomi scelti.

* **[!UICONTROL Spazi dei]**
nomi consentitiPertinente se  `Allow Tagging` è selezionato sotto la  **** scheda Settingstab. I tag che possono essere applicati sono limitati a quelli all&#39;interno delle categorie dello spazio nomi selezionate. L’elenco degli spazi dei nomi include &quot;Tag standard&quot; (lo spazio dei nomi predefinito) e &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, il che significa che tutti gli spazi dei nomi sono consentiti.

* **[!UICONTROL Suggerimento]**
Limite: consente di immettere il numero di tag da visualizzare come suggerimento al membro che invia il messaggio al forum. Il valore predefinito è 
**-** 1 (nessun limite).

### Scheda Traduzione {#translation-tab}

Nella scheda **[!UICONTROL Translation]**, se la traduzione è abilitata per il sito della community, è possibile impostare la traduzione per tradurre l&#39;intero argomento o i post selezionati.

* **[!UICONTROL Traduci]**
tutto: se questa opzione è selezionata, il thread del forum viene tradotto nella lingua preferita dell&#39;utente. Il valore predefinito è deselezionato.

### Scheda Ordina impostazioni {#sort-settings-tab}

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

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Forum Essentials](essentials-forum.md) per gli sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, vedere [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

Per assegnare tag agli argomenti e ai commenti inviati, consultate [Assegnazione di tag ai contenuti generati dall&#39;utente](tag-ugc.md).

Per la traduzione di argomenti e commenti pubblicati, vedere [Traduzione di contenuti generati dall&#39;utente](translate-ugc.md).
