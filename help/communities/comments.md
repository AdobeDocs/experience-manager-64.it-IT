---
title: Utilizzo dei commenti
seo-title: Utilizzo dei commenti
description: La funzione Commenti consente ai visitatori del sito che hanno effettuato l’accesso di condividere le proprie opinioni e conoscenze
seo-description: La funzione Commenti consente ai visitatori del sito che hanno effettuato l’accesso di condividere le proprie opinioni e conoscenze
uuid: 30fc48ac-134c-4acb-a65c-398855c93829
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b074ebfa-2894-4a2d-aa8e-28168049971a
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 6%

---


# Utilizzo dei commenti {#using-comments}

## Introduzione {#introduction}

La funzione commenti consente ai visitatori del sito che hanno effettuato l’accesso (membri) di condividere le proprie opinioni e conoscenze in merito ai contenuti del sito. Questa funzione è spesso già presente in altre funzioni, ma può essere aggiunta a qualsiasi sito Web.

Questa sezione della documentazione descrive

* Aggiunta `Comments`a una pagina
* Impostazioni di configurazione per il `Comments`componente

>[!NOTE]
>
>L&#39;invio anonimo di un commento non è supportato. I visitatori del sito devono registrarsi (diventare membri) ed effettuare l’accesso per partecipare.

## Aggiunta di commenti a una pagina {#adding-comments-to-a-page}

Per aggiungere un `Comments`componente a una pagina in modalità di creazione, usate il browser dei componenti per individuare

* `Communities / Comments`

trascinatelo nella posizione desiderata su una pagina, ad esempio una posizione relativa alla funzione in cui gli utenti possono inserire commenti oppure semplicemente nella parte inferiore della pagina.

Per le informazioni necessarie, consulta [Community Components Basics](basics.md).

Quando vengono incluse le librerie [lato client](essentials-comments.md#essentials-for-client-side) richieste, viene visualizzato così il `Comments`componente.

![chlimage_1-428](assets/chlimage_1-428.png)

>[!NOTE]
>
>Su una pagina può esistere un solo `Comments`componente. Alcune funzioni di Communities includono già commenti, ad esempio blog, calendario, forum, QnA e recensioni.

## Configurazione dei commenti {#configuring-comments}

Selezionate il `Comments` componente inserito a cui accedere e selezionate l’ `Configure` icona che apre la finestra di dialogo di modifica.

![configurare](assets/configure.png) le impostazioni ![dei commenti](assets/commentssettings.png)

### Scheda Commenti {#comments-tab}

Nella scheda **[!UICONTROL Commenti]** , specificare il modo in cui i visitatori inseriscono i commenti.

* **[!UICONTROL Consenti risposte]**

   Se questa opzione è selezionata, consente ai membri di rispondere ai commenti esistenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Commenti per pagina]**

   Limita il numero di commenti visualizzati per pagina e il numero di risposte visualizzate. Il valore predefinito è 10.

* **[!UICONTROL Consenti caricamenti file]**

   Se questa opzione è selezionata, l&#39;opzione per caricare un file viene visualizzata con la casella di immissione testo. Il valore predefinito è deselezionato.

* **[!UICONTROL Dimensione file massima]**

   Pertinente solo se l&#39;opzione Consenti caricamenti file è selezionata. Questo valore limita le dimensioni del file caricato. Il limite predefinito è 10 MB.

* **[!UICONTROL Lunghezza massima messaggio]**

   Numero massimo di caratteri che possono essere immessi nella casella di testo. Il valore predefinito è 4096 caratteri.

* **[!UICONTROL Tipi di file consentiti]**

   Pertinente solo se l&#39;opzione Consenti caricamenti file è selezionata. Un elenco separato da virgole di estensioni di file con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati dei tipi di file, quelli non specificati non saranno consentiti. Il valore predefinito non è specificato, pertanto tutti i tipi di file sono consentiti.

* **[!UICONTROL Editor Rich Text]**

   Se questa opzione è selezionata, è possibile inserire commenti con tag. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti votazione]**

   Se questa opzione è selezionata, l&#39;opzione per votare verso l&#39;alto o verso il basso verrà visualizzata con la casella di immissione testo. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti Segui]**

   Se questa opzione è selezionata, consentire ai membri di seguire i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Visualizza badge]**

   Se questa opzione è selezionata, è possibile visualizzare i simboli acquisiti e assegnati. Il valore predefinito è deselezionato.

### Scheda Moderazione utente {#user-moderation-tab}

Nella scheda Moderazione **** utente, specificate le modalità di gestione dei commenti inviati. Per ulteriori informazioni, consultate [Moderazione del contenuto](moderate-ugc.md)generato dall&#39;utente.

* **[!UICONTROL Premoderazione]**

   Se questa opzione è attivata, i commenti devono essere approvati prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Elimina commenti]**

   Se questa opzione è attivata, al membro che ha pubblicato il commento viene fornita la possibilità di eliminarlo. Il valore predefinito è deselezionato.

* **[!UICONTROL Rifiuta commenti]**

   Se questa opzione è selezionata, consentire ai moderatori di negare i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri commenti]**

   Se questa opzione è selezionata, consentire ai moderatori di chiudere e riaprire i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Segnala commenti]**

   Se questa opzione è selezionata, consentire ai membri di contrassegnare i commenti come non appropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Elenco di motivi per segnalazione]**

   Se questa opzione è selezionata, consentire ai membri di scegliere, da un elenco a discesa, il motivo per cui contrassegnare un commento come non appropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Motivo per segnalazione personalizzato]**

   Se questa opzione è selezionata, consentire ai membri di inserire il proprio motivo per il quale è stato segnalato un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia moderazione]**

   Immettete il numero di volte in cui un commento deve essere contrassegnato dai membri prima che i moderatori ne vengano informati. Il valore predefinito è una tantum (1).

* **[!UICONTROL Limite segnalazione]**

   Specificate quante volte un commento deve essere contrassegnato prima che venga nascosto dalla visualizzazione pubblica. Questo numero deve essere maggiore o uguale alla soglia di **[!UICONTROL moderazione]**. Il valore predefinito è 5.

### Scheda Impostazioni ordinamento {#sort-settings-tab}

Nella scheda **[!UICONTROL Impostazioni]** ordinamento, specificare in che modo i commenti inviati vengono ordinati quando vengono visualizzati.

* **[!UICONTROL Campo di ordinamento]**

   Per selezionare uno dei `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`, o `Most Liked`.

* **[!UICONTROL Ordinamento]**

   Per selezionare una delle `Ascending` opzioni o `Descending`, trascinate verso il basso.

### Passaggio a un tipo di commento personalizzato {#changing-to-a-custom-comment-type}

Modificando il Tipo risorsa commento, il sistema di commenti non genererà più un&#39;istanza di commento utilizzando l&#39;impostazione predefinita, ma piuttosto un&#39;istanza che è stata personalizzata (estesa) dagli sviluppatori.

Una volta noti i tipi di risorse personalizzati, immettete la modalità [](../../help/sites-authoring/default-components-designmode.md) Progettazione e fate doppio clic sul `Comments` componente inserito per aprire una finestra di dialogo con una scheda aggiuntiva.

Nella scheda Tipi **[!UICONTROL di]** risorse, specificare il resourceType personalizzato per le nuove istanze dei `Comments or Voting`componenti:

![chlimage_1-429](assets/chlimage_1-429.png)

* **[!UICONTROL Tipo risorsa commento]**

   Passa a resourceType di un `comment`componente esteso (commento singolo) in /apps. Esempio, `/apps/social/commons/components/hbs/comments/comment`

   Questa risorsa identificherà resourceType dell&#39;UGC creato quando un visitatore inserisce un commento.

* **[!UICONTROL Tipo di risorsa per votazione]**

   Passa a resourceType di un `voting`componente esteso in /apps. Esempio, `/apps/social/components/hbs/voting`

   Questa risorsa identificherà il tipo di risorsa dell&#39;UGC creato quando un visitatore pubblica un voto.

* **[!UICONTROL Tipo risorsa sistema commenti]**

   Passa a resourceType di un `comments`componente esteso (sistema di commenti) in /apps. Lasciate vuoto, a meno che il modello di pagina includa [](scf.md#add-or-include-a-communities-component) dinamicamente il sistema di commenti nello script sottostante, anziché essere aggiunto alla pagina come risorsa (nodo commenti). Ulteriori informazioni leggendo l&#39;helper [](handlebars-helpers.md#include){{include}}.

## Esperienza dei visitatori del sito {#site-visitor-experience}

### Moderatori e amministratori {#moderators-and-administrators}

Quando l’utente che ha effettuato l’accesso dispone di privilegi di moderatore o amministratore, può eseguire le attività di moderazione consentite dalla configurazione del componente, indipendentemente da chi ha creato il commento.

### Membri {#members}

Quando il visitatore del sito ha effettuato l&#39;accesso, a seconda della configurazione, può

* Pubblicare un nuovo commento
* Modificare il proprio commento
* Elimina il proprio commento
* Contrassegnare altri commenti

### Anonimo {#anonymous}

I visitatori del sito che non hanno effettuato l&#39;accesso possono solo leggere i commenti pubblicati, tradurli se supportati, ma non aggiungere commenti o contrassegnare i commenti di altri utenti.

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Comments Essentials](essentials-comments.md) per gli sviluppatori.

Per la moderazione dei commenti pubblicati, vedere [Moderazione del contenuto](moderate-ugc.md)generato dall&#39;utente.

Per la traduzione dei commenti postati, vedere [Traduzione del contenuto](translate-ugc.md)generato dall&#39;utente.
