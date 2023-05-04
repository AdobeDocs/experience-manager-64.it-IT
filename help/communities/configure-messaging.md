---
title: Funzionalità di messaggistica
seo-title: Messaging Feature
description: Configurazione dei componenti di messaggistica
seo-description: Configuring Messaging components
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 2%

---

# Funzionalità di messaggistica {#messaging-feature}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Oltre alle interazioni visibili al pubblico che si verificano nei forum e nei commenti, la funzione di messaggistica di AEM Communities consente ai membri della community di interagire più privatamente tra di loro.

Questa funzione può essere inclusa quando [sito della community](overview.md#communitiessites) viene creato.

Le funzioni di messaggistica consentono di:

* Invia un messaggio a uno o più membri della community
* Invia un messaggio a un gruppo di membri della community
* Inviare un messaggio con allegati
* Inoltrare un messaggio
* Risposta a un messaggio
* Eliminare un messaggio
* Ripristinare un messaggio eliminato

Per abilitare e modificare la funzione di messaggistica, visita

* [Configurazione della messaggistica](messaging.md) per amministratori
* [Nozioni di base sulla messaggistica](essentials-messaging.md) per sviluppatori

>[!NOTE]
>
>Non è supportato per aggiungere `Compose Message, Message, or Message List` componenti (disponibili in `Communities`gruppo di componenti) in una pagina in modalità di modifica dell’autore.

## Configurazione dei componenti di messaggistica {#configuring-messaging-components}

Quando la messaggistica è abilitata per un sito community, viene completamente configurata senza necessità di ulteriori configurazioni. Queste informazioni vengono fornite se è necessario modificare la configurazione predefinita.

### Configurazione dell’elenco dei messaggi (messagebox) {#configuring-message-list-messagebox}

Per modificare la configurazione dell’elenco dei messaggi per **Inbox**, **Elementi inviati** e **Cestino** pagine della funzione di messaggistica, apri il sito in [modalità modifica autore](sites-console.md#authoring-site-content).

In `Preview` seleziona la modalità **[!UICONTROL Messaggi]** per aprire la pagina di messaggistica principale. Quindi seleziona uno **[!UICONTROL Casella in entrata, Elementi inviati o Cestino]** per configurare il componente per l’elenco dei messaggi.

In `Edit` , seleziona il componente nella pagina.

Per accedere alla finestra di dialogo di configurazione, è necessario annullare l’ereditarietà selezionando la `link`icona.

Una volta completata la configurazione, è necessario ripristinare l’ereditarietà selezionando la `broken link` icona.

![chlimage_1-396](assets/chlimage_1-396.png)

Una volta annullata l’ereditarietà, sarà possibile selezionare la `configure` per aprire la finestra di dialogo di configurazione.

![chlimage_1-397](assets/chlimage_1-397.png)

#### Scheda Base {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL Selettore del servizio]**
(*Obbligatorio*) Impostalo sul valore della proprietà `serviceSelector.name` dal [Servizio AEM Communities Messaging Operations](messaging.md#messaging-operations-service).

* **[!UICONTROL Pagina Componi]**
(*Obbligatorio*) La pagina da aprire quando un membro fa clic sul pulsante `Reply` pulsante . La pagina di destinazione deve contenere **[!UICONTROL Componi messaggio]** modulo.

* **[!UICONTROL Rispondi/visualizza come risorsa]**
Se questa opzione è selezionata, l’URL di risposta e l’URL di visualizzazione faranno riferimento a una risorsa; in caso contrario i dati vengono passati come parametri di query nell’URL.

* **[!UICONTROL Modulo di visualizzazione del profilo]**
Il modulo del profilo da utilizzare per visualizzare il profilo dei mittenti.

* **[!UICONTROL Cartella Cestino]**
Se questa opzione è selezionata, in questo componente Elenco messaggi vengono visualizzati solo i messaggi contrassegnati come eliminati (cestino).

* **[!UICONTROL Percorsi cartella]**
(*Obbligatorio*) Riferimento ai valori impostati per `inbox.path.name` e `sentitems.path.name` in [Servizio AEM Communities Messaging Operations](messaging.md#messaging-operations-service). Durante la configurazione di un `Inbox`, aggiungi una voce utilizzando il valore di `inbox.path.name`. Durante la configurazione di un `Outbox`, aggiungi una voce utilizzando il valore di `sentitems.path.name`. Per la configurazione di `Trash`, aggiungi due voci con entrambi i valori.

#### Scheda Visualizzazione {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL Contrassegna pulsante di lettura]**
Se questa opzione è selezionata, viene visualizzata una 
`Read`che consente di contrassegnare un messaggio come letto.

* **[!UICONTROL Pulsante Segna non letto]**
Se questa opzione è selezionata, viene visualizzata una 
`Mark Unread` che consente di contrassegnare un messaggio come letto.

* **[!UICONTROL Pulsante Elimina]**
Se questa opzione è selezionata, viene visualizzata una 
`Delete`che consente di contrassegnare un messaggio come letto. Duplica la funzionalità di eliminazione se **`Message Options`** è anche controllato.

* **[!UICONTROL Opzioni messaggio]**
Se questa opzione è selezionata, viene visualizzato 
**`Reply`**, **`Reply All`**, **`Forward`** e **`Delete`** pulsanti che consentono di inviare o eliminare un messaggio. Duplica la funzionalità di eliminazione se **`Delete Button`** è anche controllato.

* **[!UICONTROL Messaggi per pagina]**
Il numero specificato è il numero massimo di messaggi visualizzati per pagina in uno schema di impaginazione. Se non viene specificato alcun numero (lasciato vuoto), vengono visualizzati tutti i messaggi e non è presente alcuna impaginazione.

* **[!UICONTROL Pattern di marca temporale]**
Fornisci pattern di marca temporale per una o più lingue. Il valore predefinito è en, de, fr, it, es, ja, zh_CN, ko_KR.

* **[!UICONTROL Visualizza utente]**
Scegli una 
**`Sender`** o **`Recipients`** per determinare se visualizzare il mittente o i destinatari.

### Configurazione del messaggio di composizione {#configuring-compose-message}

Per modificare la configurazione della pagina dei messaggi di composizione, apri il sito in [modalità modifica autore](sites-console.md#authoring-site-content).

In `Preview`seleziona la modalità **[!UICONTROL Messaggi]** per aprire la pagina di messaggistica principale. Quindi seleziona il pulsante Nuovo messaggio per aprire il `Compose Message` pagina..

In `Edit` in , seleziona il componente principale nella pagina contenente il corpo del messaggio.

Per accedere alla finestra di dialogo di configurazione, è necessario annullare l’ereditarietà selezionando la `link`icona.

Una volta completata la configurazione, è necessario ripristinare l’ereditarietà selezionando la `broken link` icona.

![chlimage_1-400](assets/chlimage_1-400.png)

Una volta annullata l’ereditarietà, sarà possibile selezionare la `configure` per aprire la finestra di dialogo di configurazione.

![chlimage_1-401](assets/chlimage_1-401.png)

#### Scheda Base {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL URL di reindirizzamento]**
Immetti l’URL della pagina visualizzata dopo l’invio del messaggio. Ad esempio: 
`../messaging.html`.

* **[!UICONTROL Annulla URL]**
Immetti l’URL della pagina visualizzata se il mittente annulla il messaggio. Ad esempio: 
`../messaging.html`.

* **[!UICONTROL Lunghezza massima dell&#39;oggetto del messaggio]**
Numero massimo di caratteri consentiti nel campo Oggetto. Ad esempio, 500. Il valore predefinito non è un limite.

* **[!UICONTROL Lunghezza massima del corpo del messaggio]**
Il numero massimo di caratteri consentiti nel campo Contenuto. Ad esempio, 10000. Il valore predefinito non è un limite.

* **[!UICONTROL Selettore del servizio]**
(*Obbligatorio*) Impostalo sul valore della proprietà **`serviceSelector.name`** dal [Servizio AEM Communities Messaging Operations](messaging.md#messaging-operations-service).

#### Scheda Visualizzazione {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL Mostra campo oggetto]**
Se questa opzione è selezionata, mostra la 
`Subject` e abilita l’aggiunta di un oggetto al messaggio. Il valore predefinito non è selezionato.

* **[!UICONTROL Etichetta oggetto]**
Immetti il testo da visualizzare accanto al 
`Subject` o in un altro campo. Il valore predefinito è `Subject`.

* **[!UICONTROL Mostra campo file allegato]**
Se questa opzione è selezionata, mostra la 
`Attachment` e abilitare l&#39;aggiunta di allegati al messaggio. Il valore predefinito non è selezionato.

* **[!UICONTROL Etichetta file allegato]**
Immetti il testo da visualizzare accanto al 
`Attachment` o in un altro campo. Il valore predefinito è **`Attach File`**.

* **[!UICONTROL Mostra campo contenuto]**
Se questa opzione è selezionata, mostra la 
`Content` e abilita l’aggiunta di un corpo del messaggio. Il valore predefinito non è selezionato.

* **[!UICONTROL Etichetta contenuto]**
Immetti il testo da visualizzare accanto al 
`Content` o in un altro campo. Il valore predefinito è **`Body`**.

* **[!UICONTROL Con Editor Rich Text]**
Se questa opzione è selezionata, indica l’utilizzo di una casella di testo Contenuto personalizzato con il proprio editor di testo RTF. Il valore predefinito non è selezionato.

* **[!UICONTROL Pattern di marca temporale]**
Fornisci pattern di marca temporale per una o più lingue. Il valore predefinito è en, de, fr, it, es, ja, zh_CN, ko_KR.
