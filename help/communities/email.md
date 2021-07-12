---
title: Configurazione e-mail
seo-title: Configurazione e-mail
description: Configurazione e-mail per Communities
seo-description: Configurazione e-mail per Communities
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Admin
exl-id: 0a0222e7-ca30-4603-94ad-582005b2de11
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 1%

---

# Configurazione e-mail {#configuring-email}

AEM Communities utilizza le e-mail per

* [Notifiche di Communities](notifications.md)
* [Iscrizioni alle community](subscriptions.md)

Per impostazione predefinita, la funzione e-mail non funziona in quanto richiede la specifica di un server SMTP e di un utente SMTP.

>[!CAUTION]
>
>Le e-mail per le notifiche e le sottoscrizioni devono essere configurate solo sull&#39; [editore principale](deploy-communities.md#primary-publisher).

## Configurazione predefinita servizio di posta {#default-mail-service-configuration}

Il servizio di posta predefinito è necessario sia per le notifiche che per le sottoscrizioni.

* Nell&#39;editore principale
* Accesso con privilegi di amministratore
* Accedi alla [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Individua il `Day CQ Mail Service`
* Seleziona l’icona di modifica

Questo si basa sulla documentazione relativa alla [Configurazione delle notifiche e-mail](../../help/sites-administering/notification.md), ma con una differenza nel fatto che il campo `"From" address` è *non* obbligatorio e deve essere lasciato vuoto.

Ad esempio (con valori inseriti solo a scopo illustrativo):

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL Nome]** host server SMTP:  *(obbligatorio)* Il server SMTP da utilizzare.

* **[!UICONTROL Porta server SMTP]** *(richiesta)* La porta server SMTP deve essere 25 o superiore.

* **[!UICONTROL Utente]** SMTP:  *(obbligatorio)* L&#39;utente SMTP.

* **[!UICONTROL Password]** SMTP:  *(obbligatorio)* La password dell&#39;utente SMTP.

* **[!UICONTROL Indirizzo]** &quot;Da&quot;: Lascia vuoto
* **[!UICONTROL SMTP usa SSL]**: Se questa opzione è selezionata, invia un’e-mail sicura. Verificare che la porta sia impostata su 465 o come richiesto per il server SMTP.
* **[!UICONTROL E-mail]** di debug: Se questa opzione è selezionata, abilita la registrazione delle interazioni del server SMTP.

## Configurazione e-mail AEM Communities {#aem-communities-email-configuration}

Una volta configurato il [servizio di posta predefinito](#default-mail-service-configuration), le due istanze esistenti della configurazione `AEM Communities Email Reply Configuration` OSGi, incluse nella versione, diventano funzionali.

Solo l’istanza per gli abbonamenti deve essere ulteriormente configurata quando si consente la risposta tramite e-mail.

1. ` [email](#configuration-for-notifications)` istanza

   per le notifiche che non supportano le e-mail di risposta e che non devono essere modificate

1. ` [subscriptions-email](#configuration-for-subscriptions)` istanza

   richiede la configurazione per abilitare completamente la creazione di post dall&#39;e-mail di risposta

Per raggiungere le istanze di configurazione e-mail di Communities:

* Nell&#39;editore principale
* Accesso con privilegi di amministratore
* Accedi alla [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Individua `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### Configurazione per le notifiche {#configuration-for-notifications}

L’istanza della configurazione `AEM Communities Email Reply Configuration` OSGi con l’e-mail Nome è per la funzione di notifica. Questa funzione non include le risposte via e-mail.

Questa configurazione non deve essere modificata.

* Individua il `AEM Communities Email Reply Configuration`
* Seleziona l’icona di modifica
* Verifica che **Name** sia `email`

* Verifica che **Crea post da risposta e-mail** sia `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Configurazione per sottoscrizioni {#configuration-for-subscriptions}

Per gli abbonamenti a Communities, è possibile abilitare o disabilitare la capacità di un membro di pubblicare contenuto rispondendo a un&#39;e-mail.

* Individua il `AEM Communities Email Reply Configuration`
* Seleziona l’icona di modifica
* Verifica che **Name** sia `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Nome]** :  *(obbligatorio)* `subscriptions-email`. Non modificare.

* **[!UICONTROL Crea un post dal messaggio e-mail]** di risposta: Se questa opzione è selezionata, il destinatario dell’e-mail di abbonamento può inviare contenuti inviando una risposta. Il valore predefinito è selezionato.
* **[!UICONTROL Aggiungi ID tracciato all&#39;intestazione]**: Il valore predefinito è  `Reply-To`.

* **[!UICONTROL Lunghezza massima del soggetto]**: Se si aggiunge un ID tracker alla riga dell’oggetto, questa è la lunghezza massima dell’oggetto, escludendo l’id tracciato, dopo di che verrà rifilato. Tieni presente che dovrebbe essere il più piccolo possibile per evitare che le informazioni sugli id tracciate vadano perse. Il valore predefinito è 200.
* **[!UICONTROL Indirizzo]** &quot;Da&quot; e-mail:  *(obbligatorio)* Indirizzo da cui verrà inviato il messaggio e-mail di notifica. Probabilmente lo stesso **utente SMTP** specificato per il [servizio di posta predefinito](#configuredefaultmailservice). Il valore predefinito è `no-reply@example.com`.

* **[!UICONTROL Reply-to-Delimiter]** (Delimitatore di risposta): Se viene aggiunto l’ID tracciamento all’intestazione Risposta, verrà utilizzato questo delimitatore. Il valore predefinito è `+` (segno più).

* **[!UICONTROL Prefisso ID tracciamento nell’oggetto]**: Se viene aggiunto l’ID tracciamento alla riga dell’oggetto, verrà utilizzato questo prefisso. Il valore predefinito è `post#`.

* **[!UICONTROL Prefisso ID tracciamento nel corpo]** del messaggio: Se viene aggiunto l’ID tracciamento al corpo del messaggio, verrà utilizzato questo prefisso. Il valore predefinito è `Please do not remove this:`.

* **[!UICONTROL Invia e-mail come HTML]**: Se questa opzione è selezionata, il tipo di contenuto dell’e-mail verrà impostato come  `"text/html;charset=utf-8"`. Il valore predefinito è selezionato.

* **[!UICONTROL Nome]** utente predefinito: Questo nome verrà utilizzato senza nome degli utenti. Il valore predefinito è `no-reply@example.com`.

* **[!UICONTROL Percorso]** principale dei modelli: L’e-mail viene creata utilizzando il modello memorizzato in questo percorso principale. Il valore predefinito è `/etc/community/templates/subscriptions-email`.

## Configura importazione polling {#configure-polling-importer}

Affinché l’e-mail possa essere inserita nell’archivio, è necessario configurare manualmente un importatore di polling e le relative proprietà nell’archivio.

### Aggiungi nuovo importatore di polling {#add-new-polling-importer}

* Nell&#39;editore principale
* Accesso con privilegi di amministratore
* Passa alla console di importazione sondaggi
Ad esempio, [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Seleziona **[!UICONTROL Aggiungi]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Tipo]**:  *(richiesto)* Tira giù per selezionare  `POP3 (over SSL).`

* **[!UICONTROL URL]**:  *(obbligatorio)* Il server di posta in uscita. Esempio, `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Importa in percorso]**&amp;ast;:  *(obbligatorio)* Imposta su  `/content/usergenerated/mailFolder/postEmails`
navigando nella sezione 
`postEmails`e seleziona  **OK**

* **[!UICONTROL Intervallo di aggiornamento in secondi]**:  *(facoltativo)* Il server di posta configurato per il servizio di posta predefinito può presentare requisiti relativi al valore dell&#39;intervallo di aggiornamento. Ad esempio, Gmail potrebbe richiedere un intervallo di `300`.

* **[!UICONTROL Accesso]**:  *(facoltativo)*

* **[!UICONTROL Password]**:  *(facoltativo)*

* Seleziona **[!UICONTROL OK]**

### Regola protocollo per nuovo importatore di polling {#adjust-protocol-for-new-polling-importer}

Una volta salvata la nuova configurazione di polling, è necessario modificare ulteriormente le proprietà dell’importazione di e-mail di abbonamento per modificare il protocollo da `POP3` a `emailreply`

Utilizzando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Nell&#39;editore principale
* Accesso con privilegi di amministratore
* Vai a [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importer/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Seleziona la configurazione appena creata
* Modifica le seguenti proprietà

   * **feedType**: sostituisci  `pop3s` con  **`emailreply`**
   * **sorgente**: sostituisci il protocollo di origine  `pop3s://` con  **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

I triangoli rossi indicano le proprietà modificate. Assicurati di salvare le modifiche:

* Seleziona **[!UICONTROL Salva tutto]**
