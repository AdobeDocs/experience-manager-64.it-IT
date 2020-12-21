---
title: Funzione Libreria file
seo-title: Funzione Libreria file
description: La funzione Libreria file consente ai visitatori del sito che hanno effettuato l’accesso di caricare, gestire e scaricare i file
seo-description: La funzione Libreria file consente ai visitatori del sito che hanno effettuato l’accesso di caricare, gestire e scaricare i file
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---


# Caratteristica Libreria file {#file-library-feature}

## Introduzione {#introduction}

La funzione di libreria dei file consente ai visitatori del sito che hanno effettuato l&#39;accesso (membri della community) di caricare, gestire e scaricare i file all&#39;interno del sito della community.

Questa sezione della documentazione descrive

* Aggiunta della funzione di libreria file a un sito AEM
* Impostazioni di configurazione per il componente `File Library`

## Aggiunta di una libreria di file a una pagina {#adding-a-file-library-to-a-page}

Per aggiungere un componente `File Library` a una pagina in modalità di creazione, individuare il componente

* `Communities / File Library`

e trascinarlo nella posizione desiderata su una pagina.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando vengono incluse le [librerie lato client ](essentials-file-library.md#essentials-for-client-side), viene visualizzato il componente `File Library`:

![chlimage_1-430](assets/chlimage_1-430.png)

## Configurazione della libreria di file {#configuring-file-library}

Selezionare il componente `File Library` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Scheda Commenti {#comments-tab}

Nella scheda **[!UICONTROL Commenti]**, specificate se e come vengono visualizzati i commenti per i file caricati:

* **[!UICONTROL Consenti commenti sui]**
file: se questa opzione è selezionata, consenti commenti sui file caricati. Il valore predefinito è deselezionato.

* **[!UICONTROL Commenti per]**
paginaLimita il numero di commenti visualizzati per pagina e il numero di risposte visualizzate. Il valore predefinito è 
**10**.

* **[!UICONTROL Max]**
dimensione file: questo valore limita la dimensione del file caricato. Il limite predefinito è 104857600 (10 Mb).

* **[!UICONTROL Numero massimo]**
lunghezza messaggio: numero massimo di caratteri che possono essere immessi nella casella di testo. Il valore predefinito è 4096 caratteri.

* **[!UICONTROL Tipi]**
di file consentitiElenco separato da virgole di estensioni di file con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se vengono specificati dei tipi di file, quelli non specificati non saranno consentiti. Il valore predefinito non è specificato, pertanto tutti i tipi di file sono consentiti.

* **[!UICONTROL Rich Text]**
EditorSe questa opzione è selezionata, è possibile inserire commenti con tag. Il valore predefinito è deselezionato.

* **[!UICONTROL Elimina]**
commentiSe questa opzione è selezionata, gli utenti possono eliminare i propri commenti. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti]**
tag: se questa opzione è selezionata, verrà abilitata la possibilità di aggiungere al file un tag. Il valore predefinito è deselezionato.

* **[!UICONTROL Spazi dei]**
nomi consentiti: se l’opzione Consenti tag è selezionata, i tag disponibili saranno limitati agli spazi dei nomi selezionati. Se non ne è selezionata alcuna, sono tutti consentiti. Il valore predefinito è tutti gli spazi dei nomi.

* **[!UICONTROL Limite]**
suggerimenti: se l’opzione Consenti tag è selezionata, questa impostazione limita il numero di tag suggeriti da visualizzare. Se è impostato su -1, non è previsto alcun limite. Il valore predefinito è -1.

* **[!UICONTROL Consenti]**
votazione: se questa opzione è selezionata, la possibilità di votare per un file verrà abilitata. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
seguenti: se questa opzione è selezionata, includete la seguente funzione per gli articoli di blog, che consente ai membri di ricevere  [](notifications.md) notifiche sui nuovi post. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti]**
risposte threadSe questa opzione è selezionata, consenti risposte ai commenti inviati. Il valore predefinito è deselezionato.

### Scheda Moderazione utente {#user-moderation-tab}

Nella scheda **[!UICONTROL Moderazione utente]**, configurare la moderazione dei commenti, se i commenti sono consentiti:

* **[!UICONTROL Pre-]**
moderazione: se questa opzione è selezionata, i commenti devono essere approvati prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Elimina]**
commenti: se questa opzione è selezionata, il visitatore che ha pubblicato il commento può eliminarlo. Il valore predefinito è selezionato.

* **[!UICONTROL Rifiuta]**
commenti: se questa opzione è selezionata, i moderatori di membri attendibili possono rifiutare i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri]**
commentiSe questa opzione è selezionata, i moderatori di membri attendibili possono chiudere e riaprire i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Contrassegna]**
commenti: se questa opzione è selezionata, i visitatori possono contrassegnare i commenti come non appropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Flag Reason]**
ListSe questa opzione è selezionata, consente ai visitatori di scegliere, da un elenco a discesa, il motivo per cui contrassegnare un commento come non appropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Custom Flag]**
Reason (Motivo contrassegno personalizzato): se questa opzione è selezionata, consente ai visitatori di inserire il proprio motivo per cui contrassegnare un commento come non appropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia]**
moderazioneConsente di specificare quante volte un commento deve essere contrassegnato dai visitatori prima che i moderatori ricevano una notifica. Il valore predefinito è una tantum (
**1**).

* **[!UICONTROL Limite di]**
contrassegnazioneConsente di specificare quante volte deve essere segnalato un commento prima di essere nascosto dalla visualizzazione pubblica. Questo numero deve essere maggiore o uguale al valore 
**Soglia moderazione**. Il valore predefinito è 5.

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [File Library Essentials](essentials-file-library.md) per gli sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, vedere [Moderazione dei contenuti generati dall&#39;utente](moderate-ugc.md).

Per assegnare tag agli argomenti e ai commenti inviati, consultate [Assegnazione di tag ai contenuti generati dall&#39;utente](tag-ugc.md).
