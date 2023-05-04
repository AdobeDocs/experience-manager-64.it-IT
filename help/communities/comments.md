---
title: Utilizzo dei commenti
seo-title: Using Comments
description: La funzione Commenti consente ai visitatori del sito che hanno effettuato l’accesso di condividere le proprie opinioni e conoscenze
seo-description: Comments feature lets signed-in site visitors share their opinions and knowledge
uuid: 30fc48ac-134c-4acb-a65c-398855c93829
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b074ebfa-2894-4a2d-aa8e-28168049971a
exl-id: 8ad5ce3e-c5dd-48d7-8812-43172eda36cc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 7%

---

# Utilizzo dei commenti {#using-comments}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La funzione commenti viene utilizzata per consentire ai visitatori del sito (membri) che hanno effettuato l’accesso di condividere le loro opinioni e conoscenze sui contenuti del sito. Questa funzione è spesso già presente in altre funzioni, ma può essere aggiunta a qualsiasi sito web.

Questa sezione della documentazione descrive

* Aggiunta `Comments`a una pagina
* Impostazioni di configurazione per `Comments`component

>[!NOTE]
>
>Pubblicazione anonima di un commento non supportata. I visitatori del sito devono registrarsi (diventare membro) e accedere per partecipare.

## Aggiunta di commenti a una pagina {#adding-comments-to-a-page}

Per aggiungere una `Comments`componente per una pagina in modalità di creazione, usate il browser componenti per individuare

* `Communities / Comments`

e trascinarlo nella posizione desiderata su una pagina, ad esempio una posizione relativa alla funzione in cui gli utenti possono commentare, o semplicemente nella parte inferiore della pagina.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](essentials-comments.md#essentials-for-client-side) sono inclusi, è così che `Comments`apparirà .

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>Solo uno `Comments`può esistere in una pagina. Tieni presente che diverse funzioni di Communities includono già commenti, come un blog, un calendario, un forum, QnA e recensioni.

## Configurazione dei commenti {#configuring-comments}

Seleziona il `Comments` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![configurare](assets/configure.png) ![osservazioni](assets/commentssettings.png)

### Scheda Commenti {#comments-tab}

Sotto la **[!UICONTROL Commenti]** Specifica in che modo i commenti vengono immessi dai visitatori.

* **[!UICONTROL Consenti risposte]**

   Se questa opzione è selezionata, consente ai membri di rispondere ai commenti esistenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Commenti per pagina]**

   Limita il numero di commenti visualizzati per pagina e il numero di risposte visualizzate. Il valore predefinito è 10.

* **[!UICONTROL Consenti caricamenti file]**

   Se questa opzione è selezionata, all’opzione per caricare un file verrà visualizzata la casella di immissione testo. Il valore predefinito è deselezionato.

* **[!UICONTROL Dimensione file massima]**

   Pertinente solo se l’opzione Consenti caricamenti file è selezionata. Questo valore limiterà la dimensione del file caricato. Il limite predefinito è 10 MB.

* **[!UICONTROL Lunghezza massima messaggio]**

   Numero massimo di caratteri che possono essere immessi nella casella di testo. Il valore predefinito è 4096 caratteri.

* **[!UICONTROL Tipi di file consentiti]**

   Pertinente solo se l’opzione Consenti caricamenti file è selezionata. Elenco di estensioni di file separate da virgola con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati tipi di file, quelli non specificati non saranno consentiti. Il valore predefinito non è specificato in modo che tutti i tipi di file siano consentiti.

* **[!UICONTROL Editor Rich Text]**

   Se questa opzione è selezionata, è possibile inserire commenti con markup. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti votazione]**

   Se questa opzione è selezionata, all’opzione per votare verso l’alto o verso il basso verrà visualizzata la casella di immissione testo. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti Segui]**

   Se questa opzione è selezionata, consentire ai membri di seguire i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Visualizza badge]**

   Se questa opzione è selezionata, consenti la visualizzazione dei badge acquisiti e assegnati. Il valore predefinito è deselezionato.

### Scheda Moderazione utente {#user-moderation-tab}

Sotto la **[!UICONTROL Moderazione utente]** , specifica come vengono gestiti i commenti inviati. Per ulteriori informazioni, consulta [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

* **[!UICONTROL Premoderazione]**

   Se questa opzione è selezionata, i commenti devono essere approvati prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Elimina commenti]**

   Se questa opzione è selezionata, il membro che ha pubblicato il commento potrà eliminarlo. Il valore predefinito è deselezionato.

* **[!UICONTROL Rifiuta commenti]**

   Se questa opzione è selezionata, consentire ai moderatori di negare i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri commenti]**

   Se questa opzione è selezionata, consenti ai moderatori di chiudere e riaprire i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Segnala commenti]**

   Se questa opzione è selezionata, consentire ai membri di contrassegnare i commenti come non appropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Elenco di motivi per segnalazione]**

   Se questa opzione è selezionata, consenti ai membri di scegliere, da un elenco a discesa, il motivo per cui contrassegnano un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Motivo per segnalazione personalizzato]**

   Se questa opzione è selezionata, consenti ai membri di inserire il proprio motivo per contrassegnare un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia moderazione]**

   Immetti il numero di volte in cui un commento deve essere contrassegnato dai membri prima che i moderatori vengano informati. Il valore predefinito è una tantum (1).

* **[!UICONTROL Limite segnalazione]**

   Immetti il numero di volte in cui un commento deve essere contrassegnato prima che venga nascosto dalla visualizzazione pubblica. Questo numero deve essere maggiore o uguale a **[!UICONTROL Soglia moderazione]**. Il valore predefinito è 5.

### Scheda Impostazioni di ordinamento {#sort-settings-tab}

Sotto la **[!UICONTROL Impostazioni di ordinamento]** specificare l&#39;ordine dei commenti inviati quando vengono visualizzati.

* **[!UICONTROL Campo di ordinamento]**

   Abbassi per selezionare uno dei `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`oppure `Most Liked`.

* **[!UICONTROL Ordinamento]**

   Abbassi per selezionare uno dei `Ascending` o `Descending`.

### Modifica a un tipo di commento personalizzato {#changing-to-a-custom-comment-type}

Modificando il tipo di risorsa commento, il sistema di commento non genererà più un&#39;istanza di un commento utilizzando il valore predefinito, ma piuttosto un&#39;istanza personalizzata (estesa) dagli sviluppatori.

Una volta noti i tipi di risorse personalizzati, immetti [Modalità Progettazione](../../help/sites-authoring/default-components-designmode.md) e fai doppio clic sul `Comments` per aprire una finestra di dialogo con una scheda aggiuntiva.

Sotto la **[!UICONTROL Tipi di risorse]** specifica il resourceType personalizzato per le nuove istanze del `Comments or Voting`componenti:

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL Tipo risorsa commento]**

   Passa al resourceType di un esteso `comment`componente (singolo commento) in /apps. Ad esempio `/apps/social/commons/components/hbs/comments/comment`

   Questa risorsa identificherà il resourceType dell&#39;UGC creato quando un visitatore pubblica un commento.

* **[!UICONTROL Tipo di risorsa per votazione]**

   Passa al resourceType di un esteso `voting`in /apps. Ad esempio `/apps/social/components/hbs/voting`

   Questa risorsa identificherà il tipo di risorsa dell’UGC creato quando un visitatore pubblica un voto.

* **[!UICONTROL Tipo risorsa sistema di commenti]**

   Passa al resourceType di un esteso `comments`componente (sistema di commenti) in /apps. Lascia vuoto a meno che il modello di pagina [include dinamicamente](scf.md#add-or-include-a-communities-component) il sistema di commenti nello script sottostante anziché essere aggiunto alla pagina come risorsa (nodo di commenti). Per saperne di più, leggi [{{include}} aiutante](handlebars-helpers.md#include).

## Esperienza dei visitatori del sito {#site-visitor-experience}

### Moderatori e amministratori {#moderators-and-administrators}

Quando l’utente connesso dispone di privilegi di moderatore o amministratore, può eseguire le attività di moderazione consentite dalla configurazione del componente, indipendentemente da chi ha creato il commento.

### Membri {#members}

Quando il visitatore del sito è connesso, a seconda della configurazione, può

* Pubblica un nuovo commento
* Modifica il proprio commento
* Elimina il proprio commento
* Contrassegna i commenti degli altri

### Anonimo {#anonymous}

I visitatori del sito che non hanno effettuato l’accesso possono solo leggere i commenti postati, tradurli se supportati, ma non possono aggiungere un commento o contrassegnare i commenti degli altri.

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Nozioni di base sui commenti](essentials-comments.md) per sviluppatori.

Per la moderazione dei commenti pubblicati, vedere [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

Per la traduzione dei commenti pubblicati, consultare [Traduzione di contenuti generati dagli utenti](translate-ugc.md).
