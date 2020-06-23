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

La funzione di messaggistica per i AEM Communities consente ai visitatori del sito (membri) che hanno effettuato l’accesso di inviare messaggi a un altro utente accessibili una volta entrati nel sito.

La messaggistica è abilitata per un sito community selezionando una casella durante la creazione [del sito](sites-console.md)community.

In questa pagina sono riportate informazioni sulla configurazione predefinita e sulle possibili regolazioni.

Per ulteriori informazioni per gli sviluppatori, consulta [Messaging Essentials](essentials-messaging.md).

## Servizio Operazioni di messaggistica {#messaging-operations-service}

Il servizio [Operazioni messaggistica](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) AEM Communities identifica l&#39;endpoint che gestisce le richieste relative ai messaggi, le cartelle che il servizio deve utilizzare per la memorizzazione dei messaggi e, se i messaggi possono includere allegati, quali tipi di file sono consentiti.

Per i siti della community creati tramite la console [Siti](sites-console.md)community esiste già un&#39;istanza del servizio, con la casella in entrata impostata su `/mail/community/inbox`.

### Servizio Operazioni di messaggistica community {#community-messaging-operations-service}

Come mostrato di seguito, esiste una configurazione del servizio per i siti creati con la procedura guidata [per la creazione del](sites-console.md)sito. Per visualizzare o modificare la configurazione, fai clic sull’icona matita accanto alla configurazione:

![chlimage_1-63](assets/chlimage_1-63.png)

### New Configuration {#new-configuration}

Per aggiungere una nuova configurazione, selezionate l&#39;icona più&#x200B;**+** accanto al nome del servizio:

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL Elenco campi messaggio consentiti]** Specifica le proprietà del componente Componi messaggio che gli utenti possono modificare e mantenere. Se vengono aggiunti nuovi elementi modulo, l&#39;ID elemento dovrà essere aggiunto se lo si desidera per essere memorizzato nell&#39;SRP. Il valore predefinito è due voci: 
*oggetto* e *contenuto*.

* **[!UICONTROL Limite]** dimensione casella messaggio Il numero massimo di byte nella finestra di messaggio di ogni utente. Il valore predefinito è 
*1073741824* (1 GB).

* **[!UICONTROL Limite]** conteggio messaggi Il numero totale di messaggi consentiti per utente. Un valore pari a -1 indica che è consentito un numero illimitato di messaggi, in base al limite delle dimensioni delle finestre di messaggio. Il valore predefinito è 
*10000* (10 k).

* **[!UICONTROL Notifica un errore]** di consegna Se questa opzione è selezionata, avvisa il mittente se la consegna del messaggio non riesce ad alcuni destinatari. Il valore predefinito è 
*selezionato*.

* **[!UICONTROL ID]** mittente di recapito non riuscito che viene visualizzato nel messaggio di consegna non riuscita. Il valore predefinito è 
*failureNotifier*.

* **[!UICONTROL Percorso]** del modello di messaggio di errore Percorso assoluto del modello di messaggio di consegna non riuscita radice. Il valore predefinito è 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]** Numero di volte in cui si tenta di inviare nuovamente il messaggio che non viene recapitato. Il valore predefinito è 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]** Numero di secondi di attesa tra i tentativi di reinvio del messaggio in caso di mancata invio. Il valore predefinito è *100 *(secondi).

* **[!UICONTROL Dimensione]** pool di aggiornamento conteggio Numero di thread simultanei utilizzati per l&#39;aggiornamento del conteggio. Il valore predefinito è 
*10*.

* **[!UICONTROL inbox.path.name]**(
*Obbligatorio*) Percorso, relativo al nodo dell&#39;utente (/home/users/*username*), da utilizzare per la **`inbox`** cartella. Il percorso NON deve terminare con una barra finale &#39;/&#39;. Il valore predefinito è */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**(
*Obbligatorio*) Percorso, relativo al nodo dell&#39;utente (/home/users/*username*), da utilizzare per la **`senditems`** cartella. Il percorso NON deve terminare con una barra finale &#39;/&#39;. Il valore predefinito è */mail/sentitems* .

* **[!UICONTROL supportAttachments.name]** Se questa opzione è selezionata, gli utenti possono aggiungere allegati ai messaggi. Il valore predefinito è 
*selezionato*.

* **[!UICONTROL batchSize.name]** Numero di messaggi da raggruppare per un invio durante l&#39;invio a un gruppo di destinatari di grandi dimensioni. Il valore predefinito è 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]** Se supportAttachments è selezionato, questo valore specifica la dimensione totale massima consentita (in byte) di tutti gli allegati. Il valore predefinito è 
*104857600* (100 MB).

* **[!UICONTROL attachmentTypeBlocklist.name]** Un blocco di estensioni di file, con il prefisso &quot;
**.**&quot;, che verrà rifiutato dal sistema. Se non è presente in elenco, l&#39;estensione è consentita. Le estensioni possono essere aggiunte o rimosse utilizzando le icone &#39;**+**&#39; e &#39;**-**&#39;. Il valore predefinito è *PREDEFINITO*.

* **[!UICONTROL allowAttachmentTypes.name]**

   **(*Action Required*)** Un elenco di estensioni di file consentite, all&#39;opposto dell&#39;elenco di blocco. Per consentire tutte le estensioni di file, ad eccezione di quelle elencate, utilizzate l&#39;icona **-** per rimuovere la singola voce vuota.

* **[!UICONTROL serviceSelector.name]**(*Obbligatorio*) Un percorso assoluto (endpoint) attraverso il quale viene richiamato il servizio (una risorsa virtuale). La radice del percorso scelto deve essere inclusa nell&#39;impostazione di configurazione *Percorsi* di esecuzione della configurazione OSGi [ , `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver)ad esempio `/bin/`, `/apps/`e `/services/`. Per selezionare questa configurazione per la funzione di messaggistica di un sito, questo endpoint viene fornito come **`Service selector`** valore per la funzione `Message List and Compose Message components` (vedere Funzione [](configure-messaging.md)Messaggio). Il valore predefinito è */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]** Use 
**Elenco campi messaggio** consentiti.

>[!CAUTION]
>
>Ogni volta che una `Messaging Operations Service` configurazione viene aperta per la modifica, se `allowedAttachmentTypes.name` è stata rimossa, viene aggiunta una voce vuota per rendere la proprietà configurabile. Una singola voce vuota disattiva efficacemente gli allegati.
>
>Per consentire tutte le estensioni di file, ad eccezione di quelle elencate in blocco, utilizzate l&#39;icona **-** per (di nuovo) rimuovere la singola voce vuota prima di fare clic su **[!UICONTROL Salva]**.

## Risoluzione dei problemi {#troubleshooting}

Un modo per risolvere i problemi è attivare i messaggi di [debug nel registro.](../../help/sites-administering/troubleshooting.md)

Vedi anche [Loggers e Scrittori per i Servizi](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services)individuali.

Il pacchetto da monitorare è `com.adobe.cq.social.messaging`.
