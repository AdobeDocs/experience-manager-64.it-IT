---
title: Configurazione e-mail
seo-title: Configuring Email
description: Configurazione e-mail per Communities
seo-description: Email configuration for Communities
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Admin
exl-id: 0a0222e7-ca30-4603-94ad-582005b2de11
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 3%

---

# Configurazione e-mail {#configuring-email}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Communities utilizza le e-mail per

* [Notifiche di Communities](notifications.md)
* [Iscrizioni alle community](subscriptions.md)

Per impostazione predefinita, la funzione e-mail non funziona in quanto richiede la specifica di un server SMTP e di un utente SMTP.

>[!CAUTION]
>
>Le e-mail per le notifiche e gli abbonamenti devono essere configurati solo nel [editore principale](deploy-communities.md#primary-publisher).

## Configurazione predefinita servizio di posta {#default-mail-service-configuration}

Il servizio di posta predefinito è necessario sia per le notifiche che per le sottoscrizioni.

* Nell&#39;editore principale
* Accesso con privilegi di amministratore
* Accedere al [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Individua il `Day CQ Mail Service`
* Seleziona l’icona di modifica

In base alla documentazione di [Configurazione della notifica e-mail](../../help/sites-administering/notification.md)ma con una differenza nel campo `"From" address` è *not* obbligatorio e deve essere lasciato vuoto.

Ad esempio (con valori inseriti solo a scopo illustrativo):

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL Nome host server SMTP]**: *(obbligatorio)* Server SMTP da utilizzare.

* **[!UICONTROL Porta server SMTP]** *(obbligatorio)* La porta del server SMTP deve essere 25 o superiore.

* **[!UICONTROL Utente SMTP]**: *(obbligatorio)* Utente SMTP.

* **[!UICONTROL Password SMTP]**: *(obbligatorio)* Password dell&#39;utente SMTP.

* **[!UICONTROL Indirizzo &quot;Da&quot;]**: Lascia vuoto
* **[!UICONTROL Utilizza SSL SMTP]**: Se questa opzione è selezionata, invia un’e-mail sicura. Verificare che la porta sia impostata su 465 o come richiesto per il server SMTP.
* **[!UICONTROL E-mail di debug]**: Se questa opzione è selezionata, abilita la registrazione delle interazioni del server SMTP.

## Configurazione e-mail AEM Communities {#aem-communities-email-configuration}

Una volta che [servizio di posta elettronica predefinito](#default-mail-service-configuration) è configurato, le due istanze esistenti del `AEM Communities Email Reply Configuration` La configurazione OSGi, inclusa nella versione, diventa funzionale.

Solo l’istanza per gli abbonamenti deve essere ulteriormente configurata quando si consente la risposta tramite e-mail.

1. ` [email](#configuration-for-notifications)` istanza

   per le notifiche che non supportano le e-mail di risposta e che non devono essere modificate

1. ` [subscriptions-email](#configuration-for-subscriptions)` istanza

   richiede la configurazione per abilitare completamente la creazione di post dall&#39;e-mail di risposta

Per raggiungere le istanze di configurazione e-mail di Communities:

* Nell&#39;editore principale
* Accesso con privilegi di amministratore
* Accedere al [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Individua `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### Configurazione per le notifiche {#configuration-for-notifications}

L&#39;istanza di `AEM Communities Email Reply Configuration` La configurazione OSGi con l’e-mail Nome è per la funzione di notifica. Questa funzione non include le risposte via e-mail.

Questa configurazione non deve essere modificata.

* Individua il `AEM Communities Email Reply Configuration`
* Seleziona l’icona di modifica
* Verifica la **Nome** è `email`

* Verifica **Crea post dal messaggio e-mail di risposta** è `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Configurazione per sottoscrizioni {#configuration-for-subscriptions}

Per gli abbonamenti a Communities, è possibile abilitare o disabilitare la capacità di un membro di pubblicare contenuto rispondendo a un&#39;e-mail.

* Individua il `AEM Communities Email Reply Configuration`
* Seleziona l’icona di modifica
* Verifica la **Nome** è `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Nome]** : *(obbligatorio)* `subscriptions-email`. Non modificare.

* **[!UICONTROL Crea post dal messaggio e-mail di risposta]**: Se questa opzione è selezionata, il destinatario dell’e-mail di abbonamento può inviare contenuti inviando una risposta. Il valore predefinito è selezionato.
* **[!UICONTROL Aggiungi ID tracciato all’intestazione]**: Il valore predefinito è `Reply-To`.

* **[!UICONTROL Lunghezza massima del soggetto]**: Se si aggiunge un ID tracker alla riga dell’oggetto, questa è la lunghezza massima dell’oggetto, escludendo l’id tracciato, dopo di che verrà rifilato. Tieni presente che dovrebbe essere il più piccolo possibile per evitare che le informazioni sugli id tracciate vadano perse. Il valore predefinito è 200.
* **[!UICONTROL Indirizzo e-mail &quot;Da&quot;]**: *(obbligatorio)* Indirizzo da cui verrà recapitato l’e-mail di notifica. Probabilmente lo stesso **Utente SMTP** specificato per [servizio di posta elettronica predefinito](#configuredefaultmailservice). Il valore predefinito è `no-reply@example.com`.

* **[!UICONTROL Risposta al delimitatore]**: Se viene aggiunto l’ID tracciamento all’intestazione Risposta, verrà utilizzato questo delimitatore. Il valore predefinito è `+` (segno più).

* **[!UICONTROL Prefisso ID tracciamento nell’oggetto]**: Se viene aggiunto l’ID tracciamento alla riga dell’oggetto, verrà utilizzato questo prefisso. Il valore predefinito è `post#`.

* **[!UICONTROL Prefisso ID tracciamento nel corpo del messaggio]**: Se viene aggiunto l’ID tracciamento al corpo del messaggio, verrà utilizzato questo prefisso. Il valore predefinito è `Please do not remove this:`.

* **[!UICONTROL Invia e-mail come HTML]**: Se questa opzione è selezionata, il tipo di contenuto dell’e-mail verrà impostato come `"text/html;charset=utf-8"`. Il valore predefinito è selezionato.

* **[!UICONTROL Nome utente predefinito]**: Questo nome verrà utilizzato senza nome degli utenti. Il valore predefinito è `no-reply@example.com`.

* **[!UICONTROL Percorso principale dei modelli]**: L’e-mail viene creata utilizzando il modello memorizzato in questo percorso principale. Il valore predefinito è `/etc/community/templates/subscriptions-email`.

## Configura importazione polling {#configure-polling-importer}

Affinché l’e-mail possa essere inserita nell’archivio, è necessario configurare manualmente un importatore di polling e le relative proprietà nell’archivio.

### Aggiungi nuovo importatore di polling {#add-new-polling-importer}

* Nell&#39;editore principale
* Accesso con privilegi di amministratore
* Sfoglia la console di importazione sondaggi Ad esempio, [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Seleziona **[!UICONTROL Aggiungi]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Tipo]**: *(obbligatorio)* Porta in basso per selezionare `POP3 (over SSL).`

* **[!UICONTROL URL]**: *(obbligatorio)* Server di posta in uscita. Ad esempio `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Importa nel percorso]**&amp;ast;: *(obbligatorio)* Imposta su `/content/usergenerated/mailFolder/postEmails`
sfogliando il 
`postEmails`e seleziona **OK**

* **[!UICONTROL Intervallo di aggiornamento in secondi]**: *(facoltativo)* Il server di posta configurato per il servizio di posta predefinito può presentare requisiti relativi al valore dell&#39;intervallo di aggiornamento. Ad esempio, Gmail potrebbe richiedere un intervallo di `300`.

* **[!UICONTROL Login]**: *(facoltativo)*

* **[!UICONTROL Password]**: *(facoltativo)*

* Seleziona **[!UICONTROL OK]**

### Regola protocollo per nuovo importatore di polling {#adjust-protocol-for-new-polling-importer}

Una volta salvata la nuova configurazione di polling, è necessario modificare ulteriormente le proprietà dell’importazione di e-mail di abbonamento per modificare il protocollo da `POP3` a `emailreply`

Utilizzo [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Nell&#39;editore principale
* Accesso con privilegi di amministratore
* Sfoglia per [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importer/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Seleziona la configurazione appena creata
* Modifica le seguenti proprietà

   * **feedType**: replace `pop3s` con **`emailreply`**
   * **source**: sostituire il protocollo di origine `pop3s://` con **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

I triangoli rossi indicano le proprietà modificate. Assicurati di salvare le modifiche:

* Seleziona **[!UICONTROL Salva tutto]**
