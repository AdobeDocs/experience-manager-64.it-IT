---
title: Invio asincrono di moduli adattivi
seo-title: Invio asincrono di moduli adattivi
description: Informazioni sulla configurazione dell'invio asincrono per i moduli adattivi.
seo-description: Informazioni sulla configurazione dell'invio asincrono per i moduli adattivi.
uuid: 3b8aeac8-cb38-4a2b-8375-556b2736d58b
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 6e4e3af5-4260-4f38-9b29-0818e92bc182
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Invio asincrono di moduli adattivi {#asynchronous-submission-of-adaptive-forms}

Tradizionalmente, i moduli Web sono configurati per l&#39;invio sincrono. Quando gli utenti inviano un modulo, vengono reindirizzati a una pagina di conferma o, in caso di invio non riuscito, a una pagina di errore. Tuttavia, esperienze Web moderne come applicazioni a pagina singola stanno acquisendo sempre maggiore popolarità, dove la pagina Web rimane statica mentre l&#39;interazione client-server avviene in background. È ora possibile fornire questa esperienza con i moduli adattivi configurando l&#39;invio asincrono. In questo caso, un modulo adattivo si comporta come un&#39;applicazione a pagina singola in quanto il modulo non viene ricaricato o il relativo URL non cambia quando i dati del modulo inviato vengono convalidati sul server.

Per ulteriori informazioni sull&#39;invio asincrono nei moduli adattivi, consultare il documento.

## Configurare l&#39;invio asincrono {#configure}

Per configurare l&#39;invio asincrono per un modulo adattivo:

1. In modalità di creazione moduli adattivi, selezionare l&#39;oggetto Contenitore modulo e toccare ![cmppr1](assets/cmppr1.png) per aprirne le proprietà.
1. Nella sezione Proprietà **[!UICONTROL invio]** , abilitare **[!UICONTROL Usa invio]** asincrono.
1. Nella sezione **[!UICONTROL Al momento dell&#39;invio]** , selezionare una delle opzioni seguenti da eseguire in caso di invio corretto del modulo.

   * **[!UICONTROL Reindirizza a URL]**: Reindirizza all&#39;URL o alla pagina specificati all&#39;invio del modulo. Potete specificare un URL o individuare il percorso di una pagina nel campo URL/percorso **[!UICONTROL di]** reindirizzamento.
   * **[!UICONTROL Mostra messaggio]**: Visualizza un messaggio all&#39;invio del modulo. È possibile scrivere un messaggio nel campo di testo sotto l&#39;opzione Mostra messaggio. Il campo di testo supporta la formattazione RTF.

1. Toccate ![check-button1](assets/check-button1.png) per salvare le proprietà.

## Funzionamento dell&#39;invio asincrono {#how-asynchronous-submission-works}

In AEM Forms sono inclusi i gestori di errori e di successo per l&#39;invio dei moduli. I gestori sono funzioni lato client che vengono eseguite in base alla risposta del server. Quando un modulo viene inviato, i dati vengono trasmessi al server per la convalida, che restituisce una risposta al client con informazioni sull&#39;evento success o error per l&#39;invio. Le informazioni vengono trasmesse come parametri al gestore interessato per eseguire la funzione.

Inoltre, autori e sviluppatori di moduli possono scrivere regole a livello di modulo per ignorare i gestori predefiniti. Per ulteriori informazioni, vedere [Ignorare i gestori predefiniti utilizzando le regole](#custom).

Esaminiamo innanzitutto la risposta del server per gli eventi di successo e di errore.

### Risposta del server per l&#39;evento di successo invio {#server-response-for-submission-success-event}

La struttura per la risposta del server per l&#39;evento di successo di invio è la seguente:

```
{
  contentType : "<xmlschema or jsonschema>", 
  data : "<dataXML or dataJson>" , 
  thankYouOption : <page/message>, 
  thankYouContent : "<thank you page url/thank you message>"
}
```

La risposta del server in caso di invio corretto del modulo include:

* Tipo formato dati modulo: XML o JSON
* Dati del modulo in formato XML o JSON
* Opzione selezionata per reindirizzare a una pagina o visualizzare un messaggio come configurato nel modulo
* URL pagina o contenuto del messaggio come configurato nel modulo

Il gestore di eventi di successo legge la risposta del server e reindirizza quindi all&#39;URL di pagina configurato o visualizza un messaggio.

### Risposta del server all&#39;evento di errore di invio {#server-response-for-submission-error-event}

La struttura per la risposta del server all&#39;evento di errore di invio è la seguente:

```
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

La risposta del server in caso di errore nell&#39;invio del modulo include:

* Motivo dell’errore, convalida CAPTCHA non riuscita o convalida lato server
* Elenco di oggetti errore, che include l&#39;espressione SOM del campo con errore di convalida e il messaggio di errore corrispondente

Il gestore errori legge la risposta del server e visualizza di conseguenza il messaggio di errore sul modulo.

## Ignora gestori predefiniti utilizzando le regole {#custom}

Gli sviluppatori di moduli e gli autori possono scrivere regole, a livello di modulo, nell&#39;editor di codice per ignorare i gestori predefiniti. La risposta del server agli eventi di successo e di errore è esposta a livello di modulo, a cui gli sviluppatori possono accedere utilizzando `$event.data` nelle regole.

Effettuate le seguenti operazioni per scrivere le regole nell&#39;editor di codice per gestire gli eventi di successo e di errore.

1. Aprite il modulo adattivo in modalità di creazione, selezionate un oggetto modulo qualsiasi e toccate ![edit-rules1](assets/edit-rules1.png) per aprire l&#39;editor di regole.
1. Selezionare **[!UICONTROL Modulo]** nella struttura Oggetti modulo e toccare **[!UICONTROL Crea]**.
1. Selezionate Editor **[!UICONTROL di]** codice dal menu a discesa di selezione della modalità.
1. Nell&#39;editor di codice, tocca **[!UICONTROL Modifica codice]**. Toccate **[!UICONTROL Modifica]** nella finestra di dialogo di conferma.
1. Scegliete **[!UICONTROL Invio]** o **[!UICONTROL Errore nell&#39;invio]** dall&#39;elenco a discesa **[!UICONTROL Evento]** .
1. Scrivete una regola per l&#39;evento selezionato e toccate **[!UICONTROL Fine]** per salvare la regola.

