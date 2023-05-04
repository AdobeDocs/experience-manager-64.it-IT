---
title: Funzione Libreria file
seo-title: File Library Feature
description: La funzione Libreria file consente ai visitatori del sito con accesso di caricare, gestire e scaricare file
seo-description: The File Library feature lets signed-in site visitors upload, manage, and download files
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
exl-id: c72b246d-442e-4841-810d-1045e83f60f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 2%

---

# Funzione Libreria file {#file-library-feature}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La funzione di libreria dei file consente ai visitatori del sito che hanno effettuato l’accesso (membri della community) di caricare, gestire e scaricare file all’interno del sito della community.

Questa sezione della documentazione descrive

* Aggiunta della funzionalità di libreria file a un sito AEM
* Impostazioni di configurazione per `File Library` component

## Aggiunta di una libreria di file a una pagina {#adding-a-file-library-to-a-page}

Per aggiungere una `File Library` in una pagina in modalità di authoring, individua il componente

* `Communities / File Library`

e trascinarlo nella posizione desiderata su una pagina.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](essentials-file-library.md#essentials-for-client-side) sono inclusi, è così che `File Library` apparirà il componente:

![chlimage_1-430](assets/chlimage_1-430.png)

## Configurazione della libreria dei file {#configuring-file-library}

Seleziona il `File Library` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### Scheda Commenti {#comments-tab}

Sotto la **[!UICONTROL Commenti]** scheda , specifica se e come vengono visualizzati i commenti per i file caricati:

* **[!UICONTROL Consenti commenti su file]**
Se questa opzione è selezionata, consenti commenti sui file caricati. Il valore predefinito è deselezionato.

* **[!UICONTROL Commenti per pagina]**
Limita il numero di commenti visualizzati per pagina e il numero di risposte visualizzate. Il valore predefinito è 
**10**.

* **[!UICONTROL Dimensione massima file]**
Questo valore limiterà la dimensione del file caricato. Il limite predefinito è 104857600 (10 Mb).

* **[!UICONTROL Lunghezza massima messaggio]**
Numero massimo di caratteri che possono essere immessi nella casella di testo. Il valore predefinito è 4096 caratteri.

* **[!UICONTROL Tipi di file consentiti]**
Elenco di estensioni di file separate da virgola con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se sono specificati tipi di file, quelli non specificati non saranno consentiti. Il valore predefinito non è specificato in modo che tutti i tipi di file siano consentiti.

* **[!UICONTROL Editor Rich Text]**
Se questa opzione è selezionata, è possibile inserire commenti con markup. Il valore predefinito è deselezionato.

* **[!UICONTROL Elimina commenti]**
Se questa opzione è selezionata, gli utenti possono eliminare i propri commenti. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti assegnazione tag]**
Se questa opzione è selezionata, verrà abilitata la possibilità di aggiungere un tag al file . Il valore predefinito è deselezionato.

* **[!UICONTROL Namespace consentiti]**
Se l’opzione Consenti assegnazione tag è selezionata, i tag disponibili saranno limitati ai namespace selezionati. Se non ne è selezionata alcuna, sono consentiti tutti. Il valore predefinito è tutti i namespace.

* **[!UICONTROL Limite di suggerimenti]**
Se l’opzione Consenti assegnazione tag è selezionata, il numero di tag suggeriti da visualizzare è limitato. Se è impostato su -1, non vi è alcun limite. Il valore predefinito è -1.

* **[!UICONTROL Consenti votazione]**
Se questa opzione è selezionata, verrà abilitata la possibilità di votare un file. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti seguenti]**
Se questa opzione è selezionata, includi la seguente funzione per gli articoli di blog, che consente ai membri di essere [notificato](notifications.md) di nuovi posti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti risposte thread]**
Se questa opzione è selezionata, consenti risposte ai commenti inviati. Il valore predefinito è deselezionato.

### Scheda Moderazione utente {#user-moderation-tab}

Sotto la **[!UICONTROL Moderazione utente]** , configura la moderazione dei commenti, se i commenti sono consentiti:

* **[!UICONTROL Pre-moderazione]**
Se questa opzione è selezionata, i commenti devono essere approvati prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Elimina commenti]**
Se questa opzione è selezionata, il visitatore che ha pubblicato il commento potrà eliminarlo. Il valore predefinito è selezionato.

* **[!UICONTROL Rifiuta commenti]**
Se questa opzione è selezionata, consentire ai moderatori membri attendibili di negare i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri commenti]**
Se questa opzione è selezionata, consentire ai moderatori membri attendibili di chiudere e riaprire i commenti. Il valore predefinito è deselezionato.

* **[!UICONTROL Contrassegna commenti]**
Se questa opzione è selezionata, consenti ai visitatori di contrassegnare i commenti come inappropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Elenco dei motivi del contrassegno]**
Se questa opzione è selezionata, consenti ai visitatori di scegliere, da un elenco a discesa, il motivo per cui contrassegnano un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Motivo contrassegno personalizzato]**
Se questa opzione è selezionata, consenti ai visitatori di inserire il proprio motivo per contrassegnare un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia moderazione]**
Immetti il numero di volte in cui un commento deve essere segnalato dai visitatori prima che i moderatori vengano informati. Il valore predefinito è una tantum (
**1**).

* **[!UICONTROL Limite di flag]**
Immetti il numero di volte in cui un commento deve essere contrassegnato prima che venga nascosto dalla visualizzazione pubblica. Questo numero deve essere maggiore o uguale a 
**Soglia moderazione**. Il valore predefinito è 5.

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Nozioni di base sulla libreria dei file](essentials-file-library.md) per sviluppatori.

Per la moderazione degli argomenti e dei commenti pubblicati, vedi [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

Per assegnare tag agli argomenti e ai commenti pubblicati, vedi [Assegnazione tag ai contenuti generati dagli utenti](tag-ugc.md).
