---
title: Utilizzo del riepilogo di recensioni e recensioni (visualizzazione)
seo-title: Utilizzo del riepilogo di recensioni e recensioni (visualizzazione)
description: Aggiunta di componenti Riepilogo recensioni e revisioni a una pagina
seo-description: Aggiunta di componenti Riepilogo recensioni e revisioni a una pagina
uuid: bd1ccee7-b26b-4a27-b1ea-89609f5080af
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bf4e7809-8def-4647-aaa6-3ac36865511f
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 2%

---


# Utilizzo del riepilogo di recensioni e recensioni (visualizzazione) {#using-reviews-and-reviews-summary-display}

Il componente `Reviews`è un composto di [ `Comments`](comments.md) e [ `Rating`](rating.md) componenti pronti per l&#39;uso.

Il componente `Reviews Summary (Display)` fornisce un riepilogo di un&#39;istanza attiva o chiusa di un componente `Reviews` da visualizzare altrove sul sito.

>[!NOTE]
>
>L&#39;invio anonimo di una revisione non è supportato. I visitatori del sito devono registrarsi (diventare membri) ed effettuare l’accesso per partecipare. Il visitatore che ha effettuato l’accesso può aggiornare la propria revisione in qualsiasi momento.

## Aggiunta di una revisione a una pagina {#adding-a-review-to-a-page}

Per aggiungere un componente `Reviews` a una pagina in modalità di creazione, utilizzate il browser componenti per individuare `Communities / Reviews` e trascinatelo nella posizione desiderata su una pagina, ad esempio una posizione relativa alla funzione che gli utenti potranno rivedere.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando vengono incluse le [librerie lato client ](reviews-basics.md#essentials-for-client-side), viene visualizzato il componente `Reviews`in questo modo.

![chlimage_1-340](assets/chlimage_1-340.png)

## Configurazione di recensioni {#configuring-reviews}

Selezionare il componente `Reviews` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-341](assets/chlimage_1-341.png)

Nella scheda **[!UICONTROL Valutazioni consentite]**, specificare l&#39;elenco completo delle valutazioni da visualizzare ai membri. Il primo rating dovrebbe essere un rating generale, in quanto è il rating che fornisce il rating medio per il componente `Review Summary (Display)`. Alle due valutazioni successive nella configurazione predefinita dovrebbe essere assegnato un titolo diverso, diverso da &quot;Subrating 1&quot; o &quot;Subrating 2&quot;.

![chlimage_1-342](assets/chlimage_1-342.png)

* **[!UICONTROL Classificazioni consentite]**

   Un elenco di valutazioni da cui un membro può scegliere.

   Utilizzare i pulsanti freccia su, freccia giù ed eliminazione per modificare le selezioni visibili.

   Fare clic su **[!UICONTROL Aggiungi elemento]** per aggiungere un&#39;altra scelta di valutazione.

Nella scheda **[!UICONTROL Valutazioni richieste]**, immettere nuovamente gli elementi dall&#39;elenco **[!UICONTROL Valutazioni consentite]** che devono essere valutati. Se un elemento è specificato solo nella scheda Valutazioni consentite, può essere lasciato senza contrassegno quando viene inviato dal membro.

Nel sito Web, le valutazioni richieste sono contrassegnate da un asterisco. Se un elemento è obbligatorio e lasciato senza contrassegno, viene visualizzato un messaggio al membro e l&#39;invio viene negato finché non vengono contrassegnate tutte le valutazioni richieste.

![chlimage_1-343](assets/chlimage_1-343.png)

* **[!UICONTROL Classificazioni richieste]**

   Un sottoinsieme di valutazioni consentite, che indica quali sono richieste.

   Utilizzare i pulsanti freccia su, freccia giù ed eliminazione per modificare le selezioni visibili.

   Fare clic su **[!UICONTROL Aggiungi elemento]** per aggiungere un&#39;altra scelta di risposta.

>[!NOTE]
>
>Se un elemento viene immesso nella scheda **[!UICONTROL Valutazioni richieste]** che non è specificata nella scheda **[!UICONTROL Valutazioni consentite]**, non è incluso negli elementi da valutare.

Nella scheda **[!UICONTROL Recensioni]**, specificare le modalità di gestione delle revisioni.

![chlimage_1-344](assets/chlimage_1-344.png)

* **[!UICONTROL Consenti]**
risposte: se questa opzione è selezionata, consenti risposte alle revisioni. Il valore predefinito è deselezionato.

* ****
ChiusoSe questa opzione è selezionata, la revisione è chiusa a nuove recensioni e risposte. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
caricamenti fileSe questa opzione è selezionata, consentire il caricamento degli allegati per la revisione. Il valore predefinito è deselezionato.

* **[!UICONTROL Max]**
Dimensione fileRilevante solo se  **[!UICONTROL Consenti]** caricamenti file è selezionata. Questo campo limita la dimensione (in byte) di un file caricato. Il valore predefinito è 10 MB.

* **[!UICONTROL Numero massimo]**
lunghezza messaggio: numero massimo di caratteri che possono essere immessi nella casella di testo. Il valore predefinito è 4096 caratteri.

* **[!UICONTROL Tipi]**
di file consentitiRilevanti solo se  **[!UICONTROL Consenti]** caricamenti file è selezionata. Un elenco separato da virgole di estensioni di file con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati dei tipi di file, quelli non specificati non saranno consentiti. Il valore predefinito non è specificato, pertanto tutti i tipi di file sono consentiti.

* **[!UICONTROL Rich Text]**
EditorSe questa opzione è selezionata, è possibile immettere i post con la marcatura. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
votazione: se questa opzione è selezionata, includete la funzione di votazione per un argomento. Il valore predefinito è deselezionato.

Nella scheda **[!UICONTROL Moderazione utente]**, specificare le modalità di gestione delle revisioni pubblicate. Per ulteriori informazioni, vedere [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

![chlimage_1-345](assets/chlimage_1-345.png)

* **[!UICONTROL Pre-]**
moderazione: se questa opzione è selezionata, le revisioni devono essere approvate prima che vengano visualizzate su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Elimina]**
revisioniSe questa opzione è selezionata, al membro che ha pubblicato la revisione viene fornita la possibilità di eliminarla. Il valore predefinito è deselezionato.

* **[!UICONTROL Rifiuta]**
recensioniSe questa opzione è selezionata, consente ai moderatori di rifiutare le revisioni. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri]**
revisioniSe questa opzione è selezionata, i moderatori possono chiudere e riaprire le revisioni. Il valore predefinito è deselezionato.

* **[!UICONTROL Contrassegna]**
revisioniSe questa opzione è selezionata, consentire ai membri di contrassegnare le revisioni come non appropriate. Il valore predefinito è deselezionato.

* **[!UICONTROL Flag Reason]**
ListSe questa opzione è selezionata, consente ai membri di scegliere, da un elenco a discesa, il motivo per cui contrassegnano una revisione come non appropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Custom Flag]**
Reason (Motivo contrassegno personalizzato): se questa opzione è selezionata, consente ai membri di inserire il proprio motivo per cui la revisione viene contrassegnata come non corretta. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia]**
moderazioneConsente di specificare il numero di volte in cui i membri devono contrassegnare una revisione prima che i moderatori ne ricevano una notifica. Il valore predefinito è una tantum (1).

* **[!UICONTROL Limite di]**
contrassegnazioneConsente di specificare quante volte deve essere segnalata una revisione prima che questa venga nascosta dalla visualizzazione pubblica. Questo numero deve essere maggiore o uguale alla **[!UICONTROL Soglia moderazione]**. Il valore predefinito è 5.

### Aggiunta di un riepilogo delle revisioni (visualizzazione) a una pagina {#adding-a-review-summary-display-to-a-page}

Per aggiungere un componente `Reviews Summary (Display)` a una pagina in modalità di creazione, individuare il componente

* `Communities / Reviews Summary (Display)`

trascinarlo nella posizione desiderata su una pagina in cui deve essere visualizzato il riepilogo di una revisione attiva o chiusa.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando vengono incluse le [librerie lato client ](reviews-basics.md#essentials-for-client-side), viene visualizzato il componente `Reviews Summary (Display)`in questo modo.

![chlimage_1-346](assets/chlimage_1-346.png)

>[!NOTE]
>
>La &quot;media&quot; riflette i voti per il primo elemento elencato nelle schede Valutazioni consentite della revisione che viene riepilogata.

### Configurazione del riepilogo delle revisioni (visualizzazione) {#configuring-reviews-summary-display}

Selezionare il componente `Reviews Summary (Display)` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-347](assets/chlimage_1-347.png)

Nella scheda **[!UICONTROL Riepilogo revisione]**

![chlimage_1-348](assets/chlimage_1-348.png)

* `Review Path`

   immettere o individuare l&#39;istanza inserita del componente `reviews`per riepilogare, ad esempio, se aggiunta alla pagina Web del sito di coinvolgimento [Geometrixx,](getting-started.md) il percorso sarebbe:

   /content/sites/interazione/it/page/jcr:content/content/Primary/review

* `Include histogram`

   Se questa opzione è selezionata, includete la visualizzazione di un grafico a barre che indica il numero di valutazioni a stella presenti nelle revisioni riepilogate. Il valore predefinito è deselezionato.

### Passaggio a un tipo di revisione personalizzato {#changing-to-a-custom-review-type}

Il componente Recensioni utilizza il sistema di commenti.

Modificando il Tipo risorsa commento, il sistema di commenti non genererà più un&#39;istanza di commento utilizzando l&#39;impostazione predefinita, ma piuttosto un&#39;istanza che è stata personalizzata (estesa) dagli sviluppatori.

Una volta noti i tipi di risorse personalizzati, immettete [Modalità progettazione](../../help/sites-authoring/default-components-designmode.md) e fate doppio clic sul componente `Comments` inserito per aprire una finestra di dialogo con una scheda aggiuntiva.

Nella scheda **[!UICONTROL Tipi di risorse]**, specificare il resourceType personalizzato per le nuove istanze dei componenti `Comments or Voting`:

![chlimage_1-349](assets/chlimage_1-349.png)

* **[!UICONTROL Tipo risorsa commento]**

   Passa a resourceType di un componente esteso `comment`(commento singolo) in /apps. Esempio, `/apps/social/commons/components/hbs/comments/comment`

   Questa risorsa identificherà resourceType dell&#39;UGC creato quando un visitatore inserisce un commento.

* **[!UICONTROL Tipo di risorsa per votazione]**

   Passa a resourceType di un componente esteso `voting`in /apps. Esempio, `/apps/social/components/hbs/voting`

   Questa risorsa identificherà il tipo di risorsa dell&#39;UGC creato quando un visitatore pubblica un voto.

* **[!UICONTROL Tipo risorsa sistema commenti]**

   Passa a resourceType di un componente esteso `comments`(sistema di commenti) in /apps. Lasciate vuoto, a meno che il modello di pagina [includa dinamicamente](scf.md#add-or-include-a-communities-component) il sistema di commenti nello script sottostante anziché essere aggiunto alla pagina come risorsa (nodo di commenti). Per saperne di più, leggi l&#39; [{{include}} helper](handlebars-helpers.md#include)

## Esperienza visitatori del sito {#site-visitor-experience}

### Moderatori e amministratori {#moderators-and-administrators}

Quando l’utente che ha effettuato l’accesso dispone di privilegi di moderatore o amministratore, può eseguire le attività di moderazione consentite dalla configurazione del componente, indipendentemente da chi ha creato la revisione.

### Membri {#members}

Quando il visitatore del sito ha effettuato l&#39;accesso, a seconda della configurazione, può

* Pubblicare una nuova revisione
* Modifica la propria revisione
* Elimina la propria revisione
* Contrassegnare i commenti di revisione di altri utenti

È consentita una sola valutazione per membro. Il membro può cambiare la propria valutazione in qualsiasi momento.

### Anonimo {#anonymous}

I visitatori del sito che non hanno effettuato l&#39;accesso possono solo leggere le revisioni pubblicate, tradurle se supportate, ma non aggiungere una valutazione o una revisione, né contrassegnare i commenti di revisione di altri utenti.

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Rivedi essenziali](reviews-basics.md) per gli sviluppatori.

Per la moderazione dei commenti inviati, vedere [Contenuto generato dall&#39;utente moderatore](moderate-ugc.md).

Per la traduzione dei commenti inviati, vedere [Traduzione di contenuti generati dall&#39;utente](translate-ugc.md).
