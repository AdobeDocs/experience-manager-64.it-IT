---
title: Ideazione
seo-title: Ideazione
description: Aggiunta e configurazione della funzione Ideazione
seo-description: Aggiunta e configurazione della funzione Ideazione
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60

---


# Ideazione {#ideation-feature}

## Introduzione {#introduction}

La funzione di ideazione fornisce un’area per i visitatori del sito che hanno effettuato l’accesso (membri della community) nell’ambiente di pubblicazione per:

* Creare idee da condividere con la community
* Visualizza e commenta le idee
* Seguire un&#39;idea
* Vota un&#39;idea

Questa sezione della documentazione descrive

* Aggiunta della funzione di ideazione a un sito AEM
* Impostazioni di configurazione per il componente Ideazione

## Adding a Ideation to a Page {#adding-a-ideation-to-a-page}

Per aggiungere un `Ideation` componente a una pagina in modalità di creazione, usate il Browser componenti per individuarlo `Communities / Ideation` e trascinarlo nella posizione desiderata sulla pagina.

Per le informazioni necessarie, visita [Community Components Basics](basics.md).

Quando sono incluse le librerie [lato client](ideation.md#essentials-for-client-side) richieste, viene visualizzato il `Ideation`componente:

![chlimage_1-29](assets/chlimage_1-29.png)

## Configurazione di un&#39;idea {#configuring-an-ideation}

Selezionate il `Ideation` componente inserito a cui accedere e selezionate l’ `Configure` icona che apre la finestra di dialogo di modifica.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### scheda Impostazioni {#settings-tab}

Nella scheda **[!UICONTROL Impostazioni]** , specificate le impostazioni per idee e commenti:

* **[!UICONTROL Titolo]** idea Titolo visualizzato per l’idea. Default is `Ideation`.

* **[!UICONTROL Descrizione]** ideazione Una descrizione da visualizzare come sottotitolo per l’idea. Il valore predefinito non è una descrizione.

* **[!UICONTROL Argomenti per pagina]** Definisce il numero di idee/post mostrati per pagina. Il valore predefinito è 10.

* **[!UICONTROL Moderata]** Se questa opzione è attivata, la pubblicazione di idee e commenti deve essere approvata prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiuso]** Se selezionato, il forum di ideazione è chiuso a nuove idee e commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Editor]** Rich Text Se questa opzione è selezionata, è possibile immettere idee e commenti con la marcatura. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti tag]** Se questa opzione è selezionata, consentire ai membri di aggiungere etichette di tag al proprio post (consultate la scheda Campo **** tag). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti]** file Se questa opzione è selezionata, consenti l&#39;aggiunta di allegati all&#39;idea o al commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Dimensione]** massima file pertinente solo se `Allow File Uploads` è selezionata. Questo campo limita la dimensione (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi]** di file consentiti Pertinenti solo se `Allow File Uploads` è selezionata. Un elenco separato da virgole di estensioni di file con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati dei tipi di file, non sarà possibile caricarli. Il valore predefinito non è specificato, pertanto tutti i tipi di file sono consentiti.

* **[!UICONTROL Dimensione]** massima file immagine pertinente solo se l&#39;opzione Consenti caricamenti file è selezionata. Numero massimo di byte di cui può disporre un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti risposte]** Se questa opzione è selezionata, consenti risposte ai commenti inseriti nell&#39;idea. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e argomenti]** Se questa opzione è selezionata, consente ai membri di eliminare i commenti e le idee che hanno pubblicato. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti di seguire]** Se questa opzione è selezionata, includete la seguente funzione per i post di idee, che consente ai membri di ricevere [notifiche](notifications.md) sui nuovi post. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti iscrizioni]** e-mail Se questa opzione è selezionata, consente ai membri di ricevere notifiche sui nuovi post tramite e-mail ([iscrizione](subscriptions.md)). Richiede `Allow Following` di essere selezionato e configurato [l’](email.md)e-mail. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti votazione]** Se questa opzione è selezionata, consentire la votazione dei commenti di un&#39;idea. Il valore predefinito è deselezionato.

* **[!UICONTROL Visualizza distintivi]** Se questa opzione è selezionata, vengono visualizzati [i simboli](implementing-scoring.md) guadagnati e assegnati con l&#39;idea di un membro. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuti]** contenuti contenuti contenuti [contenuti se questa opzione è selezionata, l’idea può essere identificata come contenuto](featured.md)disponibile. Il valore predefinito è deselezionato.

### Scheda Moderazione utente {#user-moderation-tab}

Nella scheda Moderazione **** utente, specificate le modalità di gestione delle idee e dei commenti pubblicati (contenuto generato dall’utente). Per ulteriori informazioni, consultate [Moderazione del contenuto](moderate-ugc.md)generato dall&#39;utente.

* **[!UICONTROL Rifiuta post]** Se questa opzione è selezionata, i moderatori di membri attendibili potranno negare i post e impedire che vengano visualizzati nel forum pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri argomenti]** Se questa opzione è selezionata, i moderatori di membri attendibili potrebbero chiudere un argomento per ulteriori modifiche e commenti e riaprire un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Contrassegna post]** Se questa opzione è selezionata, consentire ai membri di contrassegnare gli argomenti o i commenti di altri utenti in modo inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Elenco]** motivi contrassegno Se questa opzione è selezionata, consente ai membri di scegliere, da un elenco a discesa, il motivo per cui l&#39;argomento o il commento vengono contrassegnati come non appropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Motivo]** contrassegno personalizzato Se questa opzione è selezionata, consentire ai membri di inserire il proprio motivo per cui l&#39;argomento o il commento è contrassegnato come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia moderazione]** Immettere il numero di volte in cui un argomento o un commento deve essere contrassegnato dai membri prima che i moderatori ricevano una notifica. Il valore predefinito è 1 (una volta).

* **[!UICONTROL Limite]** contrassegno Consente di specificare quante volte un argomento o un commento deve essere contrassegnato prima che venga nascosto dalla visualizzazione pubblica. Se è impostato su -1, l&#39;argomento o il commento contrassegnato non viene mai nascosto dalla visualizzazione pubblica. In caso contrario, questo numero deve essere maggiore o uguale alla soglia di moderazione. Il valore predefinito è 5.

### Scheda Campo tag {#tag-field-tab}

Nella scheda Campo **** tag, i tag che possono essere applicati, se consentiti nella scheda **[!UICONTROL Impostazioni]** , sono limitati in base agli spazi dei nomi selezionati.

* **[!UICONTROL Spazi dei nomi consentiti]** Rilevanti se `Allow Tagging` è selezionato nella scheda **Impostazioni** . I tag che possono essere applicati sono limitati a quelli all&#39;interno delle categorie dello spazio nomi selezionate. L&#39;elenco degli spazi dei nomi include &quot;Tag standard&quot; (lo spazio dei nomi predefinito) e &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, ovvero tutti gli spazi dei nomi sono consentiti.

* **[!UICONTROL Limite]** suggerimenti Consente di specificare il numero di tag da visualizzare come suggerimento al membro che invia il messaggio al forum. Un valore pari a **-** 1 non indica alcun limite. Il valore predefinito è 0.

### Scheda Impostazioni ordinamento {#sort-settings-tab}

Nella scheda **[!UICONTROL Impostazioni]** ordinamento, specificare in che modo i commenti inviati vengono ordinati quando vengono visualizzati.

* **[!UICONTROL Ordina per]** selezionare tutte le selezioni di ordinamento consentite: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Default is `Newest, Oldest, Last Updated`.

* **[!UICONTROL Imposta come Predefinito]** pull verso il basso per selezionare una delle opzioni di ordinamento selezionate da visualizzare come predefinita. Default is `Newest`.

* **[!UICONTROL Seleziona Opzioni ora per l&#39;ordinamento]** pull in basso di Analytics per selezionare una delle opzioni `All, Last 24 Hours, Last 7 Days, Last 30 Days`. Default is `All`.

## Esperienza dei visitatori del sito {#site-visitor-experience}

### Creazione di Idea {#creating-idea}

Come per tutte le funzioni di Community, se non è stato effettuato l’accesso, un visitatore del sito può solo leggere idee e visualizzare altre opinioni (tramite commenti e voti).

Una volta effettuato l’accesso, un membro può creare una nuova idea.

![chlimage_1-32](assets/chlimage_1-32.png)

Prima di inviare l&#39;idea, è possibile salvare una bozza.

Selezionando il `Save as Draft` pulsante, viene salvata una bozza.

![chlimage_1-33](assets/chlimage_1-33.png)

Quando visualizzate le bozze salvate nella `My Drafts` scheda, selezionate `Read More` di nuovo la modalità di modifica:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Feedback {#providing-feedback}

Una volta pubblicata l&#39;idea, altri membri possono accedere, aprire l&#39;idea ( `Read More`) e come l&#39;idea, aggiungendo così al conteggio dei voti, e fare commenti.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Ideation Essentials](ideation.md) per gli sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, consultate [Moderazione del contenuto](moderate-ugc.md)generato dall&#39;utente.

Per assegnare tag agli argomenti e ai commenti inviati, consultate [Assegnazione di tag ai contenuti](tag-ugc.md)generati dagli utenti.
