---
title: Console di gestione membri e gruppi
seo-title: Members & Groups Management Consoles
description: Accesso alle console Gestione membri e gruppi
seo-description: How to access Members and Groups Management consoles
uuid: 2e93e861-a066-4189-91db-f8b784bc5aea
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ccabf301-b417-48aa-8501-8360fd9f3e36
role: Admin
exl-id: 2d0154b3-4cd7-439a-869d-cb116f60b69d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 5%

---

# Console di gestione membri e gruppi {#members-groups-management-consoles}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

Le funzioni di AEM Communities richiedono spesso la registrazione e l’accesso dei visitatori del sito prima di partecipare a una community nell’ambiente di pubblicazione. La registrazione utente deve esistere solo nell’ambiente di pubblicazione e viene comunemente definita *membri* distinguerli *utenti* registrati nell’ambiente di authoring.

### Membri (utenti) in Pubblica {#members-users-on-publish}

Utilizzo delle console Membri e Gruppi della community, dei membri e dei gruppi membri registrati nella *pubblicare* l&#39;ambiente può essere creato e gestito dal *autore* ambiente. Questo è possibile solo quando il [servizio tunnel](deploy-communities.md#tunnel-service-on-author) è abilitato.

### Utenti sull’autore {#users-on-author}

Per la gestione di utenti e gruppi registrati nel *autore* è necessario utilizzare la console di sicurezza della piattaforma:

* Dalla navigazione globale seleziona `Tools, Security, Users`
* Dalla navigazione globale seleziona `Tools, Security, Groups`

>[!NOTE]
>
>Con il contenuto di esempio distribuito e abilitato, molti utenti di esempio esistono sia nell’ambiente di authoring che in quello di pubblicazione. Questi utenti non saranno presenti durante l&#39;esecuzione con [modalità runmode nosamplecontent](../../help/sites-administering/production-ready.md).

## Console dei membri {#members-console}

Nell’ambiente di authoring, per accedere alla console Membri per la gestione dei membri registrati nell’ambiente di pubblicazione:

* Dalla navigazione globale: **[!UICONTROL Navigazione > Community > Membri]**

>[!CAUTION]
>
>Non sarà possibile utilizzare la console Membri se la [servizio tunnel](deploy-communities.md#tunnel-service-on-author) non è abilitato.

![chlimage_1-119](assets/chlimage_1-119.png)

### Ricerca {#search-features}

Seleziona l’icona del pannello laterale sul lato sinistro del `Members` per aprire il pannello laterale di ricerca.

![chlimage_1-120](assets/chlimage_1-120.png) ![chlimage_1-121](assets/chlimage_1-121.png)

Seleziona l’icona di ricerca sul lato sinistro del `Members` intestazione per chiudere il pannello laterale di ricerca.

### Statistiche membri {#member-statistics}

Colonne visualizzate `Views`, `Posts`, `Follows`e `Likes` vengono aggiornati quando l’utente è membro di uno o più siti della community con Adobe Analytics [abilitato](sites-console.md#analytics).

### Esporta CSV {#export-csv}

Selezione della `Export CSV` il collegamento consente di scaricare tutti i membri come un elenco di valori separati da virgole, adatti all’importazione in un foglio di calcolo.

Le intestazioni di colonna sono

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Crea nuovo membro {#create-new-member}

Seleziona `Create Member` per creare un utente nell’ambiente di pubblicazione.

![chlimage_1-122](assets/chlimage_1-122.png)

### GENERALE - Dettagli dei membri {#general-member-details}

La maggior parte dei campi sono campi facoltativi che il membro può successivamente compilare sul proprio profilo.

* **[!UICONTROL ID]**
(
*obbligatorio*) L&#39;ID autorizzabile è l&#39;ID di accesso del membro.
Per impostazione predefinita, l’ID è impostato sul valore dell’indirizzo e-mail richiesto.
   *Una volta creato, l&#39;ID potrebbe non essere modificato.*

* **[!UICONTROL Indirizzo e-mail]**
(
*obbligatorio*) L&#39;indirizzo e-mail del membro.
Il membro può cambiare il proprio indirizzo e-mail quando aggiorna il proprio profilo.I Se l&#39;ID è stato impostato come impostazione predefinita sull&#39;indirizzo e-mail, l&#39;ID verrà *not* cambia quando l’indirizzo e-mail viene modificato.

* **[!UICONTROL Password]**
(
*obbligatorio*) La password di accesso.

* **[!UICONTROL Ripeti password]**
(
*obbligatorio*) Immetti nuovamente la password per la verifica.

* **[!UICONTROL Aggiungi membro ai siti]**
(
*facoltativo*) Seleziona uno dei siti community esistenti per aggiungere il membro al gruppo di membri del sito community.

* **[!UICONTROL Aggiungi membro a gruppi]**
(
*facoltativo*) Selezionare uno dei gruppi di membri esistenti per aggiungere il membro a tale gruppo.

* Seleziona **[!UICONTROL Salva]**

### GENERALE - Impostazioni account {#general-account-settings}

In Impostazioni account è possibile per un amministratore della community di

* **[!UICONTROL Stato]**
   * Vietati\
      Un membro non è in grado di accedere, impedendo loro di visualizzare pagine o partecipare ad attività che richiedono l’accesso. Possono ancora visitare in forma anonima un sito aperto della comunità.

   * Non vietato Un membro ha accesso completo al sito della community.

   Il valore predefinito è `Not Banned`.

* **[!UICONTROL Limiti di contributo]**
Se questa opzione è selezionata, la capacità del membro di pubblicare contenuto è limitata.
L’impostazione predefinita dipende dalla configurazione dei limiti dei contributi.
Vedi [Limiti dei contributi degli Stati membri](limits.md).

* **[!UICONTROL Modifica password]**
Collegamento presente durante la modifica di un membro esistente. Consente a un amministratore della community di reimpostare una password per un membro.

### GENERALE - Foto {#general-photo}

Per fornire un avatar per il membro, inizia selezionando **[!UICONTROL Carica immagine]** e scegli un&#39;immagine di tipo .jpg, .png, .tif o .gif. La dimensione preferita di un’immagine è 240 x 240 pixel a 72 dpi.

### GENERALE - Aggiungi membro a siti {#general-add-member-to-sites}

Il membro può essere aggiunto a uno o più gruppi di membri della community. Iniziare inserendo testo nella casella di testo.

### GENERALE - Aggiungi membro ai gruppi {#general-add-member-to-groups}

Il membro può essere aggiunto a uno o più gruppi di membri. Iniziare inserendo testo nella casella di testo.

### Scheda BADGES {#badges-tab}

La `BADGES` Il pannello consente di assegnare manualmente i badge e di revocarli. I badge possono essere assegnati a ruoli e badge tipicamente acquisiti.

Vedi anche [Punteggio e badge](implementing-scoring.md).

![chlimage_1-123](assets/chlimage_1-123.png)

* **[!UICONTROL Aggiungi badge]**
   * Inizia a digitare per selezionare [badge disponibili](badges.md). Dopo aver selezionato un badge, scegli ogni sito o tutti i siti in cui deve essere visualizzato il badge insieme all’avatar del membro.
   * È possibile scegliere più badge e siti.
* **[!UICONTROL Rimuovere i badge]**
   * Seleziona l’icona del cestino accanto a un badge per rimuoverlo

## Console Gruppi {#groups-console}

La console Gruppi, disponibile nell’ambiente di authoring, consente di creare e gestire i gruppi di membri registrati nell’ambiente di pubblicazione. È particolarmente utile per:
* [Gruppi di membri privilegiati](users.md#privilegedmembersgroups)
* Assegnazione basata su gruppi di [risorse di abilitazione](resources.md)

Per accedere alla console Gruppi :
* Dalla navigazione globale: **[!UICONTROL Navigazione > Community > Gruppi]**

>[!CAUTION]
>
>Non sarà possibile utilizzare la console Gruppi se [servizio tunnel](deploy-communities.md#tunnel-service-on-author) non è abilitato.

### Crea nuovo gruppo {#create-new-group}

Seleziona `Add Group` per creare un gruppo nell’ambiente di pubblicazione.

![chlimage_1-124](assets/chlimage_1-124.png)

I campi richiesti per la creazione di un nuovo gruppo di membri lato pubblicazione sono:

* **[!UICONTROL ID]**
(
*obbligatorio*) L&#39;ID univoco del gruppo.
   *Una volta creato, l&#39;ID potrebbe non essere modificato.*

* **[!UICONTROL Nome]**
(
*facoltativo*) Nome visualizzato del gruppo.

   Il valore predefinito è ID.

* **[!UICONTROL Descrizione]**
(
*facoltativo*) Una descrizione dello scopo e delle autorizzazioni del gruppo.

* **[!UICONTROL Aggiungi membri al gruppo]**
(
*facoltativo*) Seleziona i membri lato pubblicazione da includere come membri iniziali del gruppo.

* Seleziona **[!UICONTROL Salva]**

## Amministratori autorizzati {#authorized-administrators}

Quando si lavora con i membri nella console dei membri di Communities, è necessario effettuare l&#39;accesso come utente con le autorizzazioni appropriate e per l&#39;agente di replica utilizzato dal [servizio tunnel](deploy-communities.md#tunnel-service-on-author) da configurare correttamente.

Se non hai effettuato l’accesso come `admin`, quindi l’utente connesso deve essere membro del gruppo `administrators` gruppo di utenti.

Vedi anche [Agenti di replica sull’autore](deploy-communities.md#replication-agents-on-author).
