---
title: Configurazione dei messaggi
seo-title: Configurazione dei messaggi
description: Messaggi community
seo-description: Messaggi community
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
translation-type: tm+mt
source-git-commit: 9fa89ca34843d41a5ab5711c1090fcc7a1077760
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 1%

---


# Configurazione dei messaggi {#configuring-messaging}

## Panoramica {#overview}

La funzione di messaggistica di  AEM Communities consente ai visitatori del sito che hanno effettuato l’accesso (membri) di inviare messaggi a un altro utente accessibili una volta effettuato l’accesso al sito.

La messaggistica è abilitata per un sito community selezionando una casella durante la creazione del sito community [](sites-console.md).

In questa pagina sono riportate informazioni sulla configurazione predefinita e sulle possibili regolazioni.

Per ulteriori informazioni per gli sviluppatori, vedere [Messaging Essentials](essentials-messaging.md).

## Servizio operazioni di messaggistica {#messaging-operations-service}

Il [ AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifica l&#39;endpoint che gestisce le richieste correlate ai messaggi, le cartelle che il servizio deve utilizzare per memorizzare i messaggi e, se i messaggi possono includere allegati, quali tipi di file sono consentiti.

Per i siti community creati con la [console Siti community](sites-console.md), esiste già un&#39;istanza del servizio, con la casella in entrata impostata su `/mail/community/inbox`.

### Servizio Operazioni messaggistica community {#community-messaging-operations-service}

Come mostrato di seguito, esiste una configurazione del servizio per i siti creati con la [creazione guidata sito](sites-console.md). Per visualizzare o modificare la configurazione, fai clic sull’icona matita accanto alla configurazione:

![chlimage_1-63](assets/chlimage_1-63.png)

### Nuova configurazione {#new-configuration}

Per aggiungere una nuova configurazione, selezionate l&#39;icona più &quot;**+**&quot; accanto al nome del servizio:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Campi messaggio]**
Elenco campi consentitiSpecifica le proprietà del componente Componi messaggio che gli utenti possono modificare e mantenere. Se vengono aggiunti nuovi elementi modulo, l&#39;ID elemento dovrà essere aggiunto se lo si desidera per essere memorizzato nell&#39;SRP. Il valore predefinito è due voci: 
*oggetto* e  *contenuto*.

* **[!UICONTROL Dimensione]**
limite casella messaggio: il numero massimo di byte nella finestra di messaggio di ogni utente. Il valore predefinito è 
*1073741824*  (1 GB).

* ****
Limite conteggio messaggi: il numero totale di messaggi consentiti per utente. Un valore pari a -1 indica che è consentito un numero illimitato di messaggi, in base al limite delle dimensioni delle finestre di messaggio. Il valore predefinito è 
*10000*  (10 k).

* **[!UICONTROL Notifica]**
errore consegnaSe questa opzione è selezionata, avvisa il mittente se la consegna del messaggio non riesce ad alcuni destinatari. Il valore predefinito è 
*selezionato*.

* **[!UICONTROL Errore di consegna]**
ID mittente del mittente visualizzato nel messaggio di consegna non riuscita. Il valore predefinito è 
*failureNotifier*.

* **[!UICONTROL Percorso del modello di messaggio di errore: percorso]**
assoluto del modello di messaggio principale di consegna non riuscita. Il valore predefinito è 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.]**
nameNumero di volte in cui si tenta di inviare nuovamente il messaggio che non viene recapitato. Il valore predefinito è 
*3*.

* **[!UICONTROL minWaitBetweenRetries.]**
nameNumero di secondi di attesa tra i tentativi di reinvio del messaggio in caso di mancata invio. Il valore predefinito è *100 *(secondi).

* **[!UICONTROL Conteggio]**
dimensione pool di aggiornamentoNumero di thread simultanei utilizzati per l&#39;aggiornamento del conteggio. Il valore predefinito è 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obbligatorio*) Percorso, relativo al nodo dell&#39;utente (/home/users/*username*), da utilizzare per la  **`inbox`** cartella. Il percorso NON deve terminare con una barra finale &#39;/&#39;. Il valore predefinito è */mail/inbox*.

* **[!UICONTROL sentitems.path.name]**
(
*Obbligatorio*) Percorso, relativo al nodo dell&#39;utente (/home/users/*username*), da utilizzare per la  **`senditems`** cartella. Il percorso NON deve terminare con una barra finale &#39;/&#39;. Il valore predefinito è */mail/sentitems*.

* **[!UICONTROL supportAttachments.]**
nameSe questa opzione è selezionata, gli utenti possono aggiungere allegati ai messaggi. Il valore predefinito è 
*selezionato*.

* **[!UICONTROL batchSize.]**
nameNumero di messaggi da raggruppare in batch per un invio durante l’invio a un grande gruppo di destinatari. Il valore predefinito è 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.]**
nameSe supportAttachments è selezionato, questo valore specifica la dimensione totale massima consentita (in byte) di tutti gli allegati. Il valore predefinito è 
*104857600*  (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.]**
nameUn  inserire nell&#39;elenco Bloccati di estensioni di file, con il prefisso &quot;
**.**&quot;, che verrà rifiutato dal sistema. Se non  inserire nell&#39;elenco Bloccati, l&#39;estensione è consentita. Le estensioni possono essere aggiunte o rimosse utilizzando le icone &#39;**+**&#39; e &#39;**-**&#39;. Il valore predefinito è *DEFAULT*.

* **[!UICONTROL allowAttachmentTypes.name]**

   **(*Azione richiesta*)** Un inserire nell&#39;elenco Consentiti  di estensioni di file, l&#39;opposto del inserire nell&#39;elenco Bloccati . Per consentire tutte le estensioni di file, ad eccezione di quelle  inserire nell&#39;elenco Bloccati, utilizzate l&#39;icona &quot;**-**&quot; per rimuovere la singola voce vuota.

* **[!UICONTROL serviceSelector.name]**
(*Obbligatorio*) Un percorso assoluto (endpoint) attraverso il quale viene richiamato il servizio (una risorsa virtuale). La radice del percorso scelto deve essere inclusa nell&#39;impostazione di configurazione *Percorsi di esecuzione* della configurazione OSGi [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), ad esempio `/bin/`, `/apps/` e `/services/`. Per selezionare questa configurazione per la funzione di messaggistica di un sito, questo endpoint viene fornito come il valore **`Service selector`** per la `Message List and Compose Message components` (vedere [Funzione messaggio](configure-messaging.md)). Il valore predefinito è */bin/messaging* .

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**Campi  messaggio Inserire nell&#39;elenco Consentiti**.

>[!CAUTION]
>
>Ogni volta che si apre una configurazione `Messaging Operations Service` per la modifica, se `allowedAttachmentTypes.name` è stato rimosso, viene aggiunta una voce vuota per rendere la proprietà configurabile. Una singola voce vuota disattiva efficacemente gli allegati.
>
>Per consentire tutte le estensioni di file, ad eccezione di quelle  inserire nell&#39;elenco Bloccati, utilizzare l&#39;icona &quot;**-**&quot; per (di nuovo) rimuovere la singola voce vuota prima di fare clic su **[!UICONTROL Salva]**.

## Risoluzione dei problemi {#troubleshooting}

Un modo per risolvere i problemi consiste nell&#39;abilitare [il debug dei messaggi nel registro.](../../help/sites-administering/troubleshooting.md)

Vedere anche [Registratori e scrittori per servizi individuali](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Il pacchetto da monitorare è `com.adobe.cq.social.messaging`.
