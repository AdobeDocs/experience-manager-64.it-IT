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
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---


# Caratteristica ideazione {#ideation-feature}

## Introduzione {#introduction}

La funzione di ideazione fornisce un’area per i visitatori del sito che hanno effettuato l’accesso (membri della community) nell’ambiente di pubblicazione per:

* Creare idee da condividere con la community
* Visualizza e commenta le idee
* Seguire un&#39;idea
* Vota un&#39;idea

Questa sezione della documentazione descrive

* Aggiunta della funzione di ideazione a un sito AEM
* Impostazioni di configurazione per il componente Ideazione

## Aggiunta di un&#39;idea a una pagina {#adding-a-ideation-to-a-page}

Per aggiungere un componente `Ideation` a una pagina in modalità di creazione, usate il browser componenti per individuare `Communities / Ideation` e trascinatelo nella posizione della pagina in cui dovrebbe essere visualizzata l’idea.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando sono incluse le [librerie lato client ](ideation.md#essentials-for-client-side), viene visualizzato il componente `Ideation`seguente:

![chlimage_1-29](assets/chlimage_1-29.png)

## Configurazione di un&#39;idea {#configuring-an-ideation}

Selezionare il componente `Ideation` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### Scheda Impostazioni {#settings-tab}

Nella scheda **[!UICONTROL Impostazioni]**, specificate le impostazioni per idee e commenti:

* **[!UICONTROL Titolo]**
ideaTitolo visualizzato per l’idea. Il valore predefinito è 
`Ideation`.

* **[!UICONTROL Ideazione]**
Descrizione: descrizione da visualizzare come sottotitolo per l’idea. Il valore predefinito non è una descrizione.

* **[!UICONTROL Argomenti per]**
paginaDefinisce il numero di idee/post mostrati per pagina. Il valore predefinito è 10.

* ****
Moderato: se questa opzione è attivata, le idee e i commenti devono essere approvati prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* ****
ChiusoSe questa opzione è selezionata, il forum di ideazione è chiuso alle nuove idee e ai nuovi commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Rich Text]**
EditorSe questa opzione è selezionata, è possibile immettere idee e commenti con la marcatura. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
tag: se questa opzione è selezionata, consente ai membri di aggiungere etichette di tag al proprio post (consultate la scheda  **[!UICONTROL Tag]** fieldtab). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
caricamenti file: se questa opzione è selezionata, consentite l&#39;aggiunta di allegati all&#39;idea o al commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Max]**
Dimensione fileRilevante solo se 
`Allow File Uploads` è selezionato. Questo campo limita la dimensione (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi]**
di file consentitiRilevanti solo se 
`Allow File Uploads` è selezionato. Un elenco separato da virgole di estensioni di file con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati dei tipi di file, non sarà possibile caricare quelli non specificati. Il valore predefinito non è specificato, pertanto tutti i tipi di file sono consentiti.

* **[!UICONTROL Max Allega]**
dimensione file immaginePertinente solo se l&#39;opzione Consenti caricamenti file è selezionata. Numero massimo di byte di cui può disporre un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti]**
risposte: se questa opzione è selezionata, consenti risposte ai commenti inseriti nell&#39;idea. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e]**
argomentiSe questa opzione è selezionata, consente ai membri di eliminare i commenti e le idee che hanno pubblicato. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
seguenti: se questa opzione è selezionata, includete la seguente funzione per i post di idee, che consente ai membri di ricevere  [](notifications.md) notifiche sui nuovi post. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
iscrizioni e-mailSe questa opzione è selezionata, consentite ai membri di ricevere notifiche sui nuovi post tramite e-mail ([iscrizione](subscriptions.md)). È necessario che `Allow Following` sia selezionato e che [e-mail sia configurato](email.md). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
votazione: se questa opzione è selezionata, consentire la votazione dei commenti di un&#39;idea. Il valore predefinito è deselezionato.

* **[!UICONTROL Visualizza]**
badge: se questa opzione è selezionata, vengono visualizzati  [](implementing-scoring.md) i badgesgesin acquisiti e assegnati con l&#39;idea di un membro. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuti]**
contenuti contenuti se questa opzione è selezionata, l’idea può essere identificata come contenuto [ ](featured.md)disponibile. Il valore predefinito è deselezionato.

### Scheda Moderazione utente {#user-moderation-tab}

Nella scheda **[!UICONTROL Moderazione utente]**, specificate in che modo vengono gestiti le idee e i commenti pubblicati (contenuto generato dall&#39;utente). Per ulteriori informazioni, vedere [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

* **[!UICONTROL Rifiuta]**
postSe questa opzione è selezionata, i moderatori di membri attendibili potranno negare i post e impedire che vengano visualizzati nel forum pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri]**
argomentiSe questa opzione è attivata, i moderatori di membri attendibili potrebbero chiudere un argomento per ulteriori modifiche e commenti e riaprire un argomento. Il valore predefinito è deselezionato.

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
nomi consentitiPertinente se 
`Allow Tagging` è selezionato sotto la  **** scheda Settingstab. I tag che possono essere applicati sono limitati a quelli all&#39;interno delle categorie dello spazio nomi selezionate. L’elenco degli spazi dei nomi include &quot;Tag standard&quot; (lo spazio dei nomi predefinito) e &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, il che significa che tutti gli spazi dei nomi sono consentiti.

* **[!UICONTROL Suggerimento]**
Limite: consente di immettere il numero di tag da visualizzare come suggerimento al membro che invia il messaggio al forum. Un valore di 
**-** 1 significa nessun limite. Il valore predefinito è 0.

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

## Esperienza visitatori del sito {#site-visitor-experience}

### Creazione di un&#39;idea {#creating-idea}

Come per tutte le funzioni di Community, se non è stato effettuato l’accesso, un visitatore del sito può solo leggere idee e visualizzare altre opinioni (tramite commenti e voti).

Una volta effettuato l’accesso, un membro può creare una nuova idea.

![chlimage_1-32](assets/chlimage_1-32.png)

Prima di inviare l&#39;idea, è possibile salvare una bozza.

Selezionando il pulsante `Save as Draft`, viene salvata una bozza.

![chlimage_1-33](assets/chlimage_1-33.png)

Quando visualizzate le bozze salvate nella scheda `My Drafts`, selezionate `Read More` per rientrare in modalità di modifica:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Feedback {#providing-feedback}

Una volta pubblicata l&#39;idea, altri membri possono accedere, aprire l&#39;idea ( `Read More`) e come l&#39;idea, aggiungendo così al conteggio dei voti, e fare commenti.

![chlimage_1-35](assets/chlimage_1-35.png)

### Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Ideation Essentials](ideation.md) per gli sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, vedere [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

Per assegnare tag agli argomenti e ai commenti inviati, consultate [Assegnazione di tag ai contenuti generati dall&#39;utente](tag-ugc.md).
