---
title: Configurazione della messaggistica
seo-title: Configuring Messaging
description: Messaggistica community
seo-description: Communities messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 2%

---

# Configurazione della messaggistica {#configuring-messaging}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

La funzione di messaggistica di AEM Communities consente ai visitatori del sito (membri) che hanno effettuato l’accesso di inviare messaggi a un altro visitatore, accessibili al momento dell’accesso al sito.

La messaggistica è abilitata per un sito community selezionando una casella durante [creazione di siti community](sites-console.md).

In questa pagina trovi informazioni sulla configurazione predefinita e sulle possibili regolazioni.

Per ulteriori informazioni per gli sviluppatori, consulta [Nozioni di base sulla messaggistica](essentials-messaging.md).

## Servizio operazioni di messaggistica {#messaging-operations-service}

La [Servizio AEM Communities Messaging Operations](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifica l&#39;endpoint che gestisce le richieste correlate alla messaggistica, le cartelle che il servizio deve utilizzare per memorizzare i messaggi e, se i messaggi possono includere allegati di file, quali tipi di file sono consentiti.

Per i siti della community creati utilizzando [Console Sites di Communities](sites-console.md), esiste già un&#39;istanza del servizio, con la casella in entrata impostata su `/mail/community/inbox`.

### Servizio per le operazioni di messaggistica comunitaria {#community-messaging-operations-service}

Come mostrato di seguito, esiste una configurazione del servizio per i siti creati con [creazione guidata sito](sites-console.md). Per visualizzare o modificare la configurazione, seleziona l’icona a forma di matita accanto alla configurazione:

![chlimage_1-63](assets/chlimage_1-63.png)

### Nuova configurazione {#new-configuration}

Per aggiungere una nuova configurazione, seleziona il segno più &quot;**+** Icona &quot; accanto al nome del servizio:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Inserire nell&#39;elenco Consentiti campi messaggio]**
Specifica le proprietà del componente Componi messaggio che gli utenti possono modificare e mantenere. Se vengono aggiunti nuovi elementi modulo, se lo desideri, devi aggiungere l’ID elemento per essere memorizzato nell’SRP. Il valore predefinito è due voci: 
*soggetto* e *content*.

* **[!UICONTROL Limite dimensione casella messaggio]**
Il numero massimo di byte nella finestra di messaggio di ogni utente. Il valore predefinito è 
*1073741824* (1 GB).

* **[!UICONTROL Limite del conteggio dei messaggi]**
Numero totale di messaggi consentiti per utente. Il valore -1 indica un numero illimitato di messaggi consentiti, in base al limite di dimensioni della finestra dei messaggi. Il valore predefinito è 
*10000* (10 k).

* **[!UICONTROL Notifica errore di consegna]**
Se questa opzione è selezionata, invia una notifica al mittente se la consegna del messaggio non riesce ad alcuni destinatari. Il valore predefinito è 
*selezionato*.

* **[!UICONTROL ID mittente della consegna non riuscita]**
Nome del mittente visualizzato nel messaggio di consegna non riuscita. Il valore predefinito è 
*failedNotifier*.

* **[!UICONTROL Percorso modello messaggio di errore]**
Percorso assoluto della directory principale del modello di messaggio non riuscito di consegna. Il valore predefinito è 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**
Numero di volte in cui è possibile provare a inviare nuovamente il messaggio che non è stato recapitato. Il valore predefinito è 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
Numero di secondi di attesa tra i tentativi di reinvio del messaggio in caso di invio non riuscito. Il valore predefinito è *100 *(secondi).

* **[!UICONTROL Conta dimensioni pool di aggiornamenti]**
Numero di thread simultanei utilizzati per l&#39;aggiornamento del conteggio. Il valore predefinito è 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obbligatorio*) Il percorso relativo al nodo dell&#39;utente (/home/users/*username*), da utilizzare per **`inbox`** cartella. Il percorso NON deve terminare con una barra finale &#39;/&#39;. Il valore predefinito è */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*Obbligatorio*) Il percorso relativo al nodo dell&#39;utente (/home/users/*username*), da utilizzare per **`senditems`** cartella. Il percorso NON deve terminare con una barra finale &#39;/&#39;. Il valore predefinito è */mail/sentitems* .

* **[!UICONTROL supportAttachments.name]**
Se questa opzione è selezionata, gli utenti possono aggiungere allegati ai messaggi. Il valore predefinito è 
*selezionato*.

* **[!UICONTROL batchSize.name]**
Numero di messaggi da raggruppare per un invio quando si invia a un gruppo di destinatari di grandi dimensioni. Il valore predefinito è 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]**
Se supportAttachments è selezionato, questo valore specifica la dimensione totale massima consentita (in byte) di tutti gli allegati. Il valore predefinito è 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.name]**
Un inserire nell&#39;elenco Bloccati di estensioni di file, con prefisso &quot;
**.**&quot;, che sarà respinto dal sistema. Se non inserire nell&#39;elenco Bloccati, l&#39;estensione è consentita. Le estensioni possono essere aggiunte o rimosse utilizzando &quot;**+**&#39; e &#39;**-** icone. Il valore predefinito è *PREDEFINITO*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Azione richiesta*)** Un inserire nell&#39;elenco Consentiti di estensioni di file, l&#39;opposto dell&#39;inserire nell&#39;elenco Bloccati. Per consentire tutte le estensioni di file, ad eccezione di quelle inserire nell&#39;elenco Bloccati, utilizza il **-** Icona &#39; per rimuovere la singola voce vuota.

* **[!UICONTROL serviceSelector.name]**
(*Obbligatorio*) Un percorso assoluto (endpoint) attraverso il quale viene richiamato il servizio (una risorsa virtuale). La radice del percorso scelto deve essere una inclusa nel *Percorsi di esecuzione* configurazione della configurazione della configurazione OSGi [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), quali `/bin/`, `/apps/`e `/services/`. Per selezionare questa configurazione per la funzione di messaggistica di un sito, questo endpoint viene fornito come **`Service selector`** valore per `Message List and Compose Message components` (vedi [Funzione messaggio](configure-messaging.md)). Il valore predefinito è */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
Utilizzo 
**Inserire nell&#39;elenco Consentiti campi messaggio**.

>[!CAUTION]
>
>Ogni volta `Messaging Operations Service` la configurazione viene aperta per la modifica, se `allowedAttachmentTypes.name` dopo la rimozione, viene aggiunta nuovamente una voce vuota per rendere configurabile la proprietà. Una singola voce vuota disattiva efficacemente gli allegati di file.
>
>Per consentire tutte le estensioni di file, ad eccezione di quelle inserire nell&#39;elenco Bloccati, utilizza il **-** Icona &#39; per (di nuovo) rimuovere la singola voce vuota prima di fare clic **[!UICONTROL Salva]**.

## Risoluzione dei problemi {#troubleshooting}

Un modo per risolvere i problemi è quello di abilitare [debug dei messaggi nel registro.](../../help/sites-administering/troubleshooting.md)

Vedi anche [Loggers e Scrittori per servizi individuali](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Il pacchetto da monitorare è `com.adobe.cq.social.messaging`.
