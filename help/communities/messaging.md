---
title: Configurazione della messaggistica
seo-title: Configurazione della messaggistica
description: Messaggistica community
seo-description: Messaggistica community
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 1%

---

# Configurazione della messaggistica {#configuring-messaging}

## Panoramica {#overview}

La funzione di messaggistica di AEM Communities consente ai visitatori del sito (membri) che hanno effettuato l’accesso di inviare messaggi a un altro visitatore, accessibili al momento dell’accesso al sito.

La messaggistica è abilitata per un sito community selezionando una casella durante la [creazione di siti community](sites-console.md).

In questa pagina trovi informazioni sulla configurazione predefinita e sulle possibili regolazioni.

Per ulteriori informazioni per gli sviluppatori, consulta [Nozioni di base sulla messaggistica](essentials-messaging.md).

## Servizio operazioni di messaggistica {#messaging-operations-service}

Il [AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifica l&#39;endpoint che gestisce le richieste relative alla messaggistica, le cartelle che il servizio deve utilizzare per la memorizzazione dei messaggi e, se i messaggi possono includere allegati di file, quali tipi di file sono consentiti.

Per i siti della community creati utilizzando la [console Sites di Communities](sites-console.md), esiste già un&#39;istanza del servizio, con la casella in entrata impostata su `/mail/community/inbox`.

### Servizio per le operazioni di messaggistica comunitaria {#community-messaging-operations-service}

Come mostrato di seguito, esiste una configurazione del servizio per i siti creati con la [creazione guidata sito](sites-console.md). Per visualizzare o modificare la configurazione, seleziona l’icona a forma di matita accanto alla configurazione:

![chlimage_1-63](assets/chlimage_1-63.png)

### Nuova configurazione {#new-configuration}

Per aggiungere una nuova configurazione, seleziona l’icona più &quot;**+**&quot; accanto al nome del servizio:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Campi messaggio]**
elenco consentitiSpecifica le proprietà del componente Messaggio di composizione che gli utenti possono modificare e mantenere. Se vengono aggiunti nuovi elementi modulo, se lo desideri, devi aggiungere l’ID elemento per essere memorizzato nell’SRP. Il valore predefinito è due voci: 
** soggetto e  *contenuto*.

* **[!UICONTROL Dimensione]**
limite casella messaggioIl numero massimo di byte nella finestra di messaggio di ogni utente. Il valore predefinito è 
*1073741824*  (1 GB).

* **[!UICONTROL Numero]**
limite messaggiIl numero totale di messaggi consentiti per utente. Il valore -1 indica un numero illimitato di messaggi consentiti, in base al limite di dimensioni della finestra dei messaggi. Il valore predefinito è 
*10000*  (10 k).

* **[!UICONTROL Notifica]**
errore di consegnaSe questa opzione è selezionata, avvisa il mittente se la consegna del messaggio non riesce ad alcuni destinatari. Il valore predefinito è 
*selezionato*.

* **[!UICONTROL Errore nell&#39;]**
ID mittente del mittente visualizzato nel messaggio di consegna non riuscita. Il valore predefinito è 
*failedNotification*.

* **[!UICONTROL Percorso]**
percorso assoluto del modello di messaggio di errore alla directory principale del modello di messaggio di consegna non riuscita. Il valore predefinito è 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.]**
nameNumero di volte in cui si tenta di inviare nuovamente il messaggio che non viene recapitato. Il valore predefinito è 
*3*.

* **[!UICONTROL minWaitBetweenRetries.]**
nameNumero di secondi di attesa tra i tentativi di reinvio del messaggio in caso di errore di invio. Il valore predefinito è *100 *(secondi).

* **[!UICONTROL Conteggio]**
dimensioni pool di aggiornamentoNumero di thread simultanei utilizzati per l&#39;aggiornamento del conteggio. Il valore predefinito è 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*Obbligatorio*) Il percorso, relativo al nodo dell&#39;utente (/home/users/*username*), da utilizzare per la  **`inbox`** cartella. Il percorso NON deve terminare con una barra finale &#39;/&#39;. Il valore predefinito è */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*Obbligatorio*) Il percorso, relativo al nodo dell&#39;utente (/home/users/*username*), da utilizzare per la  **`senditems`** cartella. Il percorso NON deve terminare con una barra finale &#39;/&#39;. Il valore predefinito è */mail/sentitems* .

* **[!UICONTROL supportAttachments.]**
nameSe questa opzione è selezionata, gli utenti possono aggiungere allegati ai propri messaggi. Il valore predefinito è 
*selezionato*.

* **[!UICONTROL batchSize.]**
nameNumero di messaggi da raggruppare per un invio durante l&#39;invio a un gruppo di destinatari di grandi dimensioni. Il valore predefinito è 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.]**
nameSe supportAttachments è selezionato, questo valore specifica la dimensione totale massima consentita (in byte) di tutti gli allegati. Il valore predefinito è 
*104857600*  (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.]**
nameUn inserire nell&#39;elenco Bloccati di estensioni di file, con prefisso &quot;
**.**&quot;, che sarà respinto dal sistema. Se non inserire nell&#39;elenco Bloccati, l&#39;estensione è consentita. Le estensioni possono essere aggiunte o rimosse utilizzando le icone &#39;**+**&#39; e &#39;**-**&#39;. Il valore predefinito è *DEFAULT*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*Azione richiesta*)** Un inserì nell&#39;elenco Consentiti di estensioni di file, in corrispondenza dell’inserire nell&#39;elenco Bloccati. Per consentire tutte le estensioni dei file, ad eccezione di quelle inserire nell&#39;elenco Bloccati, utilizza l&#39;icona &quot;**-**&quot; per rimuovere la singola voce vuota.

* **[!UICONTROL serviceSelector.name]**
(*Obbligatorio*) Un percorso assoluto (endpoint) attraverso il quale viene richiamato il servizio (una risorsa virtuale). La radice del percorso scelto deve essere inclusa nell&#39;impostazione di configurazione *Percorsi di esecuzione* della configurazione OSGi [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), ad esempio `/bin/`, `/apps/` e `/services/`. Per selezionare questa configurazione per la funzione di messaggistica di un sito, questo endpoint viene fornito come valore **`Service selector`** per `Message List and Compose Message components` (consulta [Funzionalità messaggio](configure-messaging.md)). Il valore predefinito è */bin/messaging* .

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**Campi Inserire nell&#39;elenco Consentiti messaggio**.

>[!CAUTION]
>
>Ogni volta che viene aperta una configurazione `Messaging Operations Service` per la modifica, se `allowedAttachmentTypes.name` è stato rimosso, viene aggiunta nuovamente una voce vuota per rendere la proprietà configurabile. Una singola voce vuota disattiva efficacemente gli allegati di file.
>
>Per consentire tutte le estensioni dei file, ad eccezione di quelle inserire nell&#39;elenco Bloccati, utilizza l&#39;icona &quot;**-**&quot; per (di nuovo) rimuovere la singola voce vuota prima di fare clic su **[!UICONTROL Salva]**.

## Risoluzione dei problemi {#troubleshooting}

Un modo per risolvere i problemi è quello di abilitare [il debug dei messaggi nel registro.](../../help/sites-administering/troubleshooting.md)

Vedi anche [Loggers e Scrittori per servizi individuali](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Il pacchetto da monitorare è `com.adobe.cq.social.messaging`.
