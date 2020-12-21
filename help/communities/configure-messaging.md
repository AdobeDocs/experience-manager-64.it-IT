---
title: Funzionalità di messaggistica
seo-title: Funzionalità di messaggistica
description: Configurazione dei componenti di messaggistica
seo-description: Configurazione dei componenti di messaggistica
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---


# Funzione di messaggistica {#messaging-feature}

Oltre alle interazioni pubblicamente visibili che si verificano nei forum e nei commenti, la funzione di messaggistica di  AEM Communities consente ai membri della community di interagire più privatamente tra di loro.

Questa funzione può essere inclusa quando si crea un [sito community](overview.md#communitiessites).

Le funzioni di messaggistica consentono di:

* Inviare un messaggio a uno o più membri della community
* Invio di un messaggio a un gruppo di membri della community
* Invio di un messaggio con allegati
* Inoltra un messaggio
* Rispondi a un messaggio
* Eliminare un messaggio
* Ripristino di un messaggio eliminato

Per abilitare e modificare la funzione di messaggistica, visita

* [Configurazione dei ](messaging.md) messaggi per gli amministratori
* [Messaging ](essentials-messaging.md) Essentials for developer

>[!NOTE]
>
>Non è supportato l&#39;aggiunta di componenti `Compose Message, Message, or Message List` (nel gruppo di componenti `Communities`) a una pagina in modalità di modifica dell&#39;autore.

## Configurazione dei componenti di messaggistica {#configuring-messaging-components}

Quando la messaggistica è abilitata per un sito community, viene completamente configurata senza bisogno di ulteriori configurazioni. Queste informazioni vengono fornite se è necessario modificare la configurazione predefinita.

### Configurazione dell&#39;elenco dei messaggi (messagebox) {#configuring-message-list-messagebox}

Per modificare la configurazione dell&#39;elenco dei messaggi per le pagine **Inbox**, **Posta inviata** e **Cestino** della funzione di messaggistica, aprire il sito in [modalità di modifica dell&#39;autore](sites-console.md#authoring-site-content).

In modalità `Preview`, selezionare il collegamento **[!UICONTROL Messages]** per aprire la pagina di messaggi principale. Quindi, per configurare il componente per l&#39;elenco dei messaggi, selezionate **[!UICONTROL Inbox, Inviati elementi o Cestino]**.

In modalità `Edit`, selezionate il componente sulla pagina.

Per accedere alla finestra di dialogo di configurazione, è necessario annullare l&#39;ereditarietà selezionando l&#39;icona `link`.

Una volta completata la configurazione, è necessario ripristinare l&#39;ereditarietà selezionando l&#39;icona `broken link`.

![chlimage_1-396](assets/chlimage_1-396.png)

Una volta annullata l&#39;ereditarietà, sarà possibile selezionare l&#39;icona `configure` per aprire la finestra di dialogo di configurazione.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Scheda di base {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Selettore]**
 del servizio (*obbligatorio*) Impostare questo valore sulla proprietà  `serviceSelector.name` dal  [ AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service).

* **[!UICONTROL Componi pagina]**
 (*richiesta*) La pagina da aprire quando un membro fa clic sul  `Reply` pulsante. La pagina di destinazione deve contenere il modulo **[!UICONTROL Componi messaggio]**.

* **[!UICONTROL Rispondi/Visualizza come]**
risorsaSe questa opzione è selezionata, l&#39;URL di risposta e l&#39;URL di visualizzazione faranno riferimento a una risorsa. In caso contrario, i dati vengono passati come parametri di query nell&#39;URL.

* **[!UICONTROL Modulo di visualizzazione profilo:]**
il modulo del profilo da utilizzare per visualizzare il profilo di mittenti.

* **[!UICONTROL Cartella]**
cestino: se questa opzione è selezionata, questo componente Elenco messaggi visualizza solo i messaggi contrassegnati come eliminati (cestino).

* **[!UICONTROL Percorsi]**
 cartella (*obbligatorio*) Riferimento ai valori impostati per  `inbox.path.name` e  `sentitems.path.name` nel  [ AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service). Durante la configurazione di un `Inbox`, aggiungere una voce utilizzando il valore di `inbox.path.name`. Durante la configurazione di un `Outbox`, aggiungere una voce utilizzando il valore di `sentitems.path.name`. Durante la configurazione per `Trash`, aggiungere due voci con entrambi i valori.

#### Scheda Visualizza {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Contrassegna]**
pulsante di letturaSe questa opzione è selezionata, viene visualizzata una 
`Read`che consente di contrassegnare un messaggio come letto.

* **[!UICONTROL Contrassegna]**
pulsante non lettoSe questa opzione è selezionata, visualizza un 
`Mark Unread` che consente di contrassegnare un messaggio come letto.

* **[!UICONTROL Elimina]**
pulsanteSe selezionato, visualizza un 
`Delete`che consente di contrassegnare un messaggio come letto. Duplica la funzionalità di eliminazione se è selezionata anche **`Message Options`**.

* **[!UICONTROL Opzioni]**
messaggioSe selezionato, viene visualizzato 
**`Reply`**,  **`Reply All`** **`Forward`** e  **`Delete`** i pulsanti che consentono di inviare o eliminare un messaggio. Duplica la funzionalità di eliminazione se è selezionata anche **`Delete Button`**.

* **[!UICONTROL Messaggi per]**
paginaIl numero specificato corrisponde al numero massimo di messaggi visualizzati per pagina in uno schema di impaginazione. Se non viene specificato alcun numero (lasciato vuoto), vengono visualizzati tutti i messaggi e non è prevista alcuna impaginazione.

* **[!UICONTROL Modelli]**
di marca temporaleFornisci pattern di marca temporale per una o più lingue. Il valore predefinito è en, de, fr, it, es, ja, zh_CN, ko_KR.

* **[!UICONTROL Visualizza]**
utenteScegliere 
**`Sender`** o  **`Recipients`** per determinare se visualizzare il mittente o i destinatari.

### Configurazione del messaggio di composizione {#configuring-compose-message}

Per modificare la configurazione della pagina dei messaggi di composizione, aprire il sito in [modalità di modifica dell&#39;autore](sites-console.md#authoring-site-content).

In `Preview`modalità, selezionare il collegamento **[!UICONTROL Messaggi]** per aprire la pagina di messaggi principale. Quindi fate clic sul pulsante Nuovo messaggio per aprire la pagina `Compose Message`.

In modalità `Edit`, selezionate il componente principale nella pagina contenente il corpo del messaggio.

Per accedere alla finestra di dialogo di configurazione, è necessario annullare l&#39;ereditarietà selezionando l&#39;icona `link`.

Una volta completata la configurazione, è necessario ripristinare l&#39;ereditarietà selezionando l&#39;icona `broken link`.

![chlimage_1-400](assets/chlimage_1-400.png)

Una volta annullata l&#39;ereditarietà, sarà possibile selezionare l&#39;icona `configure` per aprire la finestra di dialogo di configurazione.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Scheda di base {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL Reindirizza]**
URLE: immettete l’URL della pagina visualizzata dopo l’invio del messaggio. Esempio, 
`../messaging.html`.

* **[!UICONTROL Annulla]**
URLImmettere l&#39;URL della pagina visualizzata se il mittente annulla il messaggio. Esempio, 
`../messaging.html`.

* **[!UICONTROL Lunghezza massima]**
oggetto messaggioNumero massimo di caratteri consentiti nel campo Oggetto. Ad esempio, 500. Il valore predefinito non è alcun limite.

* **[!UICONTROL Lunghezza massima del]**
corpo del messaggioNumero massimo di caratteri consentiti nel campo Contenuto. Ad esempio, 10000. Il valore predefinito non è alcun limite.

* **[!UICONTROL Selettore]**
 del servizio (*obbligatorio*) Impostare questo valore sulla proprietà  **`serviceSelector.name`** dal  [ AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service).

#### Scheda Visualizza {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Mostra]**
campo oggetto Se questa opzione è selezionata, viene visualizzata la 
`Subject` e abilitare l&#39;aggiunta di un oggetto al messaggio. Il valore predefinito non è selezionato.

* **[!UICONTROL Oggetto]**
Etichetta: testo da visualizzare accanto al pulsante 
`Subject` o in un altro campo. Il valore predefinito è `Subject`.

* **[!UICONTROL Mostra]**
campo Allega fileSe questa opzione è selezionata, viene visualizzata la variabile 
`Attachment` e abilitare l&#39;aggiunta di allegati al messaggio. Il valore predefinito non è selezionato.

* **[!UICONTROL Allega]**
etichetta fileImmettere il testo da visualizzare accanto al pulsante 
`Attachment` o in un altro campo. Il valore predefinito è **`Attach File`**.

* **[!UICONTROL Mostra]**
campo contenutoSe questa opzione è selezionata, viene visualizzata la variabile 
`Content` e abilitare l&#39;aggiunta di un corpo del messaggio. Il valore predefinito non è selezionato.

* **[!UICONTROL Etichetta]**
contenutoImmettere il testo da visualizzare accanto al pulsante 
`Content` o in un altro campo. Il valore predefinito è **`Body`**.

* **[!UICONTROL Con l’]**
Editor Rich TextSe questa opzione è selezionata, indica l’utilizzo di una casella di testo Contenuto personalizzata con un proprio editor Rich Text. Il valore predefinito non è selezionato.

* **[!UICONTROL Modelli]**
di marca temporaleFornisci pattern di marca temporale per una o più lingue. Il valore predefinito è en, de, fr, it, es, ja, zh_CN, ko_KR.

