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
* Impostazioni di configurazione per il `Forum`componente

## Adding a Forum to a Page {#adding-a-forum-to-a-page}

Per aggiungere un `Forum` componente a una pagina in modalità di creazione, usate il browser Componenti per individuare

* `Communities / Forum`

Trascinala nella stessa posizione di una pagina in cui dovrebbe essere visualizzato il forum.

Per le informazioni necessarie, visita [Community Components Basics](basics.md).

Quando sono incluse le librerie [lato client](essentials-forum.md#essentials-for-client-side) richieste, viene visualizzato il `Forum`componente:

![chlimage_1-60](assets/chlimage_1-60.png)

## Configurazione di un forum {#configuring-a-forum}

Selezionate il `Forum` componente inserito a cui accedere e selezionate l’ `Configure` icona che apre la finestra di dialogo di modifica.

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### scheda Impostazioni {#settings-tab}

Nella scheda **[!UICONTROL Impostazioni]** , specificate le impostazioni per gli argomenti e le risposte:

* **[!UICONTROL Argomenti per pagina]** Definisce il numero di topic/post mostrati per pagina. Il valore predefinito è 10.

* **[!UICONTROL Moderato]** Se selezionato, la pubblicazione di argomenti e commenti deve essere approvata prima che vengano visualizzati in un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiuso]** Se selezionato, il forum è chiuso ai nuovi argomenti e commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Editor]** Rich Text Se questa opzione è selezionata, è possibile immettere commenti e argomenti con la marcatura. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti tag]** Se questa opzione è selezionata, consentire ai membri di aggiungere etichette di tag al proprio post (consultate la scheda Campo **** tag). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti]** file Se questa opzione è selezionata, consenti l&#39;aggiunta di allegati all&#39;argomento o al commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]** se questa opzione è selezionata, includete la seguente funzione per i post del forum, che consente ai membri di ricevere [notifiche](notifications.md) sui nuovi post. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti blocco]** Se questa opzione è selezionata, gli argomenti del forum possono essere bloccati in cima all’elenco di argomenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuti]** contenuti contenuti contenuti [contenuti se questa opzione è selezionata, l’idea può essere identificata come contenuto](featured.md)disponibile. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti iscrizioni]** e-mail Se questa opzione è selezionata, consente ai membri di ricevere notifiche sui nuovi post tramite e-mail ([iscrizione](subscriptions.md)). Richiede `Allow Following` di essere selezionato e configurato [l’](email.md)e-mail. Il valore predefinito è deselezionato.

* **[!UICONTROL Dimensione]** massima file pertinente solo se `Allow File Uploads` è selezionata. Questo campo limita la dimensione (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi]** di file consentiti Pertinenti solo se `Allow File Uploads` è selezionata. Un elenco separato da virgole di estensioni di file con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati dei tipi di file, non sarà possibile caricarli. Il valore predefinito non è specificato, pertanto tutti i tipi di file sono consentiti.

* **[!UICONTROL Dimensione]** massima file immagine pertinente solo se l&#39;opzione Consenti caricamenti file è selezionata. Numero massimo di byte di cui può disporre un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti risposte]** filettate se questa opzione è selezionata, consenti risposte ai commenti inviati all&#39;argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e argomenti]** Se questa opzione è selezionata, consente ai membri di eliminare i commenti e gli argomenti inviati. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti votazione]** Se questa opzione è selezionata, includi la funzione di votazione con un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Mostra breadcrumb]** Se questa opzione è selezionata, vengono visualizzate le breadcrumb di navigazione nelle pagine dell&#39;argomento. Il valore predefinito è selezionato.

* **[!UICONTROL Visualizza Badge]** Se questa opzione è selezionata, visualizza [i simboli](implementing-scoring.md) guadagnati e assegnati con il post di blog di un membro. Il valore predefinito è deselezionato.

>[!NOTE]
>
>Potrebbe essere necessario controllare sia `AllowThreaded Replies` che `Allow users to Delete Comments and Topics` abilitare i commenti su un argomento.

### Scheda Moderazione utente {#user-moderation-tab}

Nella scheda Moderazione **** utente, specificate in che modo vengono gestiti gli argomenti e le risposte inviati (contenuto generato dall’utente). Per ulteriori informazioni, consultate [Moderazione del contenuto](moderate-ugc.md)generato dall&#39;utente.

* **[!UICONTROL Rifiuta post]** Se questa opzione è selezionata, i moderatori di membri attendibili potranno negare i post e impedire che vengano visualizzati nel forum pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri argomenti]** Se questa opzione è selezionata, i moderatori di membri attendibili potrebbero chiudere un argomento per ulteriori modifiche e commenti e riaprire un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Sposta argomenti]** Se questa opzione è selezionata, consente ai moderatori lato pubblicazione di spostare gli argomenti. Il valore predefinito è selezionato.

* **[!UICONTROL Contrassegna post]** Se questa opzione è selezionata, consentire ai membri di contrassegnare gli argomenti o i commenti di altri utenti in modo inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Elenco]** motivi contrassegno Se questa opzione è selezionata, consente ai membri di scegliere, da un elenco a discesa, il motivo per cui l&#39;argomento o il commento vengono contrassegnati come non appropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Motivo]** contrassegno personalizzato Se questa opzione è selezionata, consentire ai membri di inserire il proprio motivo per cui l&#39;argomento o il commento è contrassegnato come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia moderazione]** Immettere il numero di volte in cui un argomento o un commento deve essere contrassegnato dai membri prima che i moderatori ricevano una notifica. Il valore predefinito è 1 (una volta).

* **[!UICONTROL Limite]** contrassegno Consente di specificare quante volte un argomento o un commento deve essere contrassegnato prima che venga nascosto dalla visualizzazione pubblica. Se è impostato su -1, l&#39;argomento o il commento contrassegnato non viene mai nascosto dalla visualizzazione pubblica. In caso contrario, questo numero deve essere maggiore o uguale alla soglia di moderazione. Il valore predefinito è 5.

### Scheda Campo tag {#tag-field-tab}

Nella scheda Campo **** tag, i tag che possono essere applicati, se consentiti nella scheda **[!UICONTROL Impostazioni]** , sono limitati in base agli spazi dei nomi selezionati.

* **[!UICONTROL Spazi dei nomi consentiti]** Rilevanti se `Allow Tagging` è selezionato nella scheda **[!UICONTROL Impostazioni]** . I tag che possono essere applicati sono limitati a quelli all&#39;interno delle categorie dello spazio nomi selezionate. L&#39;elenco degli spazi dei nomi include &quot;Tag standard&quot; (lo spazio dei nomi predefinito) e &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, ovvero tutti gli spazi dei nomi sono consentiti.

* **[!UICONTROL Limite]** suggerimenti Consente di specificare il numero di tag da visualizzare come suggerimento al membro che invia il messaggio al forum. Il valore predefinito è **-** 1 (nessun limite).

### Scheda Traduzione {#translation-tab}

Nella scheda **[!UICONTROL Traduzione]** , se la traduzione è abilitata per il sito community, la traduzione può essere impostata per tradurre l&#39;intero argomento o i post selezionati.

* **[!UICONTROL Traduci tutto]** Se questa opzione è selezionata, il thread del forum viene tradotto nella lingua preferita dell&#39;utente. Il valore predefinito è deselezionato.

### Scheda Impostazioni ordinamento {#sort-settings-tab}

Nella scheda **[!UICONTROL Impostazioni]** ordinamento, specificare in che modo i commenti inviati vengono ordinati quando vengono visualizzati.

* **[!UICONTROL Ordina per]** selezionare tutte le selezioni di ordinamento consentite: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Default is `Newest, Oldest, Last Updated`.

* **[!UICONTROL Imposta come Predefinito]** pull verso il basso per selezionare una delle opzioni di ordinamento selezionate da visualizzare come predefinita. Default is `Newest`.

* **[!UICONTROL Seleziona Opzioni ora per l&#39;ordinamento]** pull in basso di Analytics per selezionare una delle opzioni `All, Last 24 Hours, Last 7 Days, Last 30 Days`. Default is `All`.

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Forum Essentials](essentials-forum.md) per gli sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, consultate [Moderazione del contenuto](moderate-ugc.md)generato dall&#39;utente.

Per assegnare tag agli argomenti e ai commenti inviati, consultate [Assegnazione di tag ai contenuti](tag-ugc.md)generati dagli utenti.

Per la traduzione di argomenti e commenti pubblicati, vedere [Traduzione di contenuto](translate-ugc.md)generato dall&#39;utente.
