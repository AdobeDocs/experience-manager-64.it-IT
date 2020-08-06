---
title: Condivisione dei collegamenti delle risorse
description: Come condividere risorse, cartelle e raccolte all'interno  AEM Assets come URL per parti esterne.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 14%

---


# Condivisione dei collegamenti delle risorse {#asset-link-sharing}

Risorse Adobe Experience Manager (AEM) consente di condividere risorse, cartelle e raccolte come URL con i membri dell’organizzazione e le entità esterne, inclusi partner e fornitori. La condivisione di risorse tramite un collegamento è un modo pratico per rendere disponibili le risorse a soggetti esterni senza dover prima accedere a  AEM Assets.

>[!NOTE]
>
>È necessaria l’autorizzazione Modifica ACL per le cartelle e le risorse che si desidera condividere come collegamento.

## Condividere le risorse {#share-assets}

Per generare l’URL delle risorse da condividere con gli utenti, usate la finestra di dialogo Condivisione collegamenti. Gli utenti con privilegi di amministratore o con autorizzazioni di lettura sul `/var/dam/share` posto possono visualizzare i collegamenti condivisi con tali utenti.

>[!NOTE]
>
>Prima di condividere un collegamento con gli utenti, assicurarsi che [!UICONTROL Day CQ Mail Service] sia configurato. Si verifica un errore se si tenta di condividere un collegamento senza prima [configurare Day CQ Mail Service](link-sharing.md#configure-day-cq-mail-service).

1. Nell’interfaccia utente Risorse, seleziona la risorsa da condividere come collegamento.
1. Dalla barra degli strumenti, tocca o fai clic sull’icona **[!UICONTROL di condivisione delle]** risorse Condividi collegamento ![](assets/assets_share.png).

   Nel campo **[!UICONTROL Condividi collegamento]** viene creato automaticamente un collegamento a una risorsa. Copiate questo collegamento e condividetelo con gli utenti. Il tempo di scadenza predefinito per il collegamento è un giorno.

   ![Finestra di dialogo con la condivisione dei collegamenti](assets/chlimage_1-542.png)

   In alternativa, esegui i passaggi 3-7 di questa procedura per aggiungere i destinatari e-mail, configurare l’ora di scadenza del collegamento e inviarlo dalla finestra di dialogo.

   >[!NOTE]
   >
   >Per condividere i collegamenti da AEM Author alle entità esterne, esporre solo i seguenti URL utilizzati per la condivisione dei collegamenti, per le richieste di GET. Bloccate altri URL per assicurare che la distribuzione AEM sia sicura.
   >
   >* &lt;AEM Server>/linkshare.html
   * &lt;AEM Server>/linksharepreview.html
   * &lt;AEM Server>/linkexpired.html


   >[!NOTE]
   Se una risorsa condivisa viene spostata in un percorso diverso, il collegamento non funziona più. Crea di nuovo il collegamento e condividi nuovamente con gli utenti.

1. Dalla console web, apri la configurazione **[!UICONTROL Day CQ Link Externalizer]** e modifica le seguenti proprietà nel campo **[!UICONTROL Domini]**, indicando i valori:

   * locale
   * author
   * pubblicazione

   Per le proprietà `local` e `author` , fornite l&#39;URL rispettivamente per l&#39;istanza locale e per l&#39;istanza di creazione. Sia `local` che `author` le proprietà hanno lo stesso valore se si esegue una singola istanza AEM autore. Ad `publish`esempio, fornite l’URL per l’istanza di pubblicazione.

1. Nella casella dell’indirizzo e-mail della finestra di dialogo **[!UICONTROL Condivisione collegamenti]**, digita l’ID e-mail dell’utente con cui vuoi condividere il collegamento. Puoi anche condividere il collegamento con più utenti.

   Se l’utente è membro dell’organizzazione, selezionate l’ID e-mail dell’utente dagli ID e-mail suggeriti che vengono visualizzati nell’elenco al di sotto dell’area di digitazione. Per un utente esterno, digitate l’ID e-mail completo e selezionatelo dall’elenco.

   Per abilitare l&#39;invio di e-mail agli utenti, configurate i dettagli del server SMTP in [Day CQ Mail Service](link-sharing.md#configure-day-cq-mail-service).

   ![Condivisione di collegamenti alle risorse direttamente dalla finestra di dialogo Condivisione collegamenti](assets/chlimage_1-543.png)

   Condivisione di collegamenti alle risorse direttamente dalla finestra di dialogo Condivisione collegamenti

   >[!NOTE]
   Se immettete un ID e-mail di un utente che non è membro dell’organizzazione, le parole &quot;Utente esterno&quot; hanno il prefisso &quot;ID e-mail dell’utente.

1. Nella casella **[!UICONTROL Oggetto]** , inserite l’oggetto della risorsa da condividere.
1. Nella casella **[!UICONTROL Messaggio]** , immettere un messaggio facoltativo.
1. Nel campo **[!UICONTROL Scadenza]** , specifica una data e un&#39;ora di scadenza per il collegamento utilizzando il selettore data. Per impostazione predefinita, la data di scadenza è impostata per una settimana dalla data di condivisione del collegamento.

   ![Imposta data e ora di scadenza per il collegamento condiviso](assets/chlimage_1-544.png)

1. Per consentire agli utenti di scaricare l&#39;immagine originale insieme alle rappresentazioni, selezionate **[!UICONTROL Consenti download del file]** originale.

   >[!NOTE]
   Per impostazione predefinita, gli utenti possono scaricare solo le rappresentazioni della risorsa condivisa come collegamento.

1. Fate clic su **[!UICONTROL Condividi]**. Un messaggio conferma la condivisione del collegamento con gli utenti tramite e-mail.
1. Per visualizzare la risorsa condivisa, toccate o fate clic sul collegamento contenuto nell&#39;e-mail inviata all&#39;utente. La risorsa condivisa viene visualizzata nella pagina [!UICONTROL Adobe Marketing Cloud] .

   ![Le risorse condivise sono disponibili in Adobe Marketing Cloud](assets/chlimage_1-545.png)

   Per passare alla vista a elenco, toccate o fate clic sull’icona del layout sulla barra degli strumenti.

1. Per generare un’anteprima della risorsa, tocca o fai clic sulla risorsa condivisa. Tocca o fai clic su **[!UICONTROL Indietro]** sulla barra degli strumenti per chiudere l’anteprima e tornare alla pagina dell’ [!UICONTROL Marketing Cloud] . Se hai condiviso una cartella, tocca o fai clic su **[!UICONTROL Cartella padre]** per tornare ad essa.

   ![chlimage_1-546](assets/chlimage_1-546.png)

   >[!NOTE]
   AEM supporta la generazione dell&#39;anteprima delle risorse di questi tipi MIME: JPG, PNG, GIF, BMP, INDD, PDF e PPT. Potete scaricare solo le risorse degli altri tipi MIME.

1. Per scaricare la risorsa condivisa, tocca o fai clic sull’icona **[!UICONTROL Seleziona]** nella barra degli strumenti, tocca o fai clic sulla risorsa, quindi tocca o fai clic su **[!UICONTROL Scarica]** dalla barra degli strumenti.

   ![Opzione della barra degli strumenti per scaricare la risorsa condivisa](assets/chlimage_1-547.png)

1. Per visualizzare le risorse condivise come collegamenti, accedi all’interfaccia utente delle risorse e tocca o fai clic sull’icona **[!UICONTROL GlobalNav]** . Scegliere **[!UICONTROL Navigazione]** dall&#39;elenco per visualizzare il riquadro di navigazione.
1. Per visualizzare un elenco delle risorse condivise, scegli **[!UICONTROL Collegamenti condivisi]** nel riquadro di navigazione.
1. Per annullare la condivisione di una risorsa, selezionatela e toccate o fate clic su **[!UICONTROL Annulla condivisione]** nella barra degli strumenti. Viene visualizzato un messaggio di conferma dell’annullamento della condivisione della risorsa. Inoltre, la voce relativa alla risorsa viene rimossa dall’elenco.

## Configurare il servizio di posta di CQ Day {#configure-day-cq-mail-service}

1. Tocca o fai clic sul logo AEM, quindi passa a **[!UICONTROL Strumenti > Operazioni > Console web]**.
1. Dall&#39;elenco dei servizi, individuare il servizio **[!UICONTROL di posta]** Day CQ.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **[!UICONTROL Day CQ Mail Service]** with the details mentioned against their names:

   * Nome host del server SMTP: nome host del server di posta elettronica
   * Porta server SMTP: porta del server di posta elettronica
   * Utente SMTP: nome utente del server di posta elettronica
   * Password SMTP: password del server di posta elettronica

   ![chlimage_1-548](assets/chlimage_1-548.png)

1. Click/tap **[!UICONTROL Save]**.

## Configurare la dimensione massima dei dati {#configure-maximum-data-size}

Quando scaricate le risorse dal collegamento condiviso mediante la funzione Condivisione collegamenti, AEM comprime l’intera gerarchia di risorse dall’archivio e quindi restituisce la risorsa in un file ZIP. Tuttavia, in assenza di limiti alla quantità di dati che possono essere compressi in un file ZIP, enormi quantità di dati sono soggetti a compressione, il che causa errori di memoria insufficiente in JVM. Per proteggere il sistema da un potenziale attacco di negazione di servizio a causa di questa situazione, configurate la dimensione massima utilizzando il parametro **[!UICONTROL Max Content Size (non compresso)]** per il servlet **[!UICONTROL proxy di condivisione di risorse Adhoc]** Day CQ DAM in Configuration Manager. Se le dimensioni non compresse della risorsa superano il valore configurato, le richieste di download delle risorse vengono rifiutate. Il valore predefinito è 100 MB.

1. Tocca o fai clic sul logo AEM, quindi passa a **[!UICONTROL Strumenti > Operazioni > Console web]**.
1. Dalla console Web, individua la configurazione **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** .
1. Apri la configurazione **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** in modalità di modifica e cambia il valore del parametro in **[!UICONTROL Max Content Size (uncompressed)]**.

   ![chlimage_1-549](assets/chlimage_1-549.png)

1. Salva le modifiche.

## Best practices and troubleshooting {#best-practices-and-troubleshooting}

* Le cartelle di risorse o le raccolte che contengono uno spazio vuoto nel loro nome potrebbero non essere condivise.
* Se gli utenti non possono scaricare le risorse condivise, verificate con il vostro amministratore AEM quali siano i limiti [di](#configure-maximum-data-size) download.
* Se non potete inviare e-mail con collegamenti a risorse condivise o se gli altri utenti non possono ricevere l’e-mail, verificate con AEM amministratore se il servizio [e-](#configure-day-cq-mail-service) mail è configurato o meno.
* Se non potete condividere le risorse utilizzando la funzionalità di condivisione dei collegamenti, accertatevi di disporre delle autorizzazioni appropriate. Consultate [Condividere le risorse](#share-assets).
