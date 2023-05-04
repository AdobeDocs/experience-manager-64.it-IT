---
title: Notifiche di Communities
seo-title: Communities Notifications
description: AEM Communities dispone di notifiche che mostrano eventi di interesse per il membro della community che ha effettuato l’accesso
seo-description: AEM Communities has notifications that display events of interest to the signed-in community member
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 3%

---

# Notifiche di Communities {#communities-notifications}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

AEM Communities fornisce una sezione sulle notifiche che mostra gli eventi di interesse per i membri della community firmati.

Le notifiche sono simili a [attività](essentials-activities.md) e [abbonamenti](subscriptions.md) dal

* Il membro che pubblica il contenuto
* Il membro che sceglie di seguire un altro membro
* Il membro che sceglie di seguire specifici argomenti, articoli e altri thread di contenuto

Ciò che distingue le notifiche dalle attività e dagli abbonamenti è

* Un collegamento alla sezione notifiche è sempre presente nell&#39;intestazione di un sito community
   * Le attività richiedono [funzione flusso di attività](functions.md#activity-stream-function) da includere nella struttura del sito comunitario
   * Gli abbonamenti richiedono [configurazione dell’e-mail](email.md)
* L’implementazione delle notifiche avviene tramite canali scalabili e collegabili
   * Le attività sono disponibili solo sul web
   * Gli abbonamenti sono disponibili solo tramite e-mail

A livello di Comunità [FP1](deploy-communities.md#latestfeaturepack), i canali di notifica disponibili sono

* Il canale web a cui si accede tramite il `Notifications` collegamento
* Il canale e-mail, disponibile quando l’e-mail è configurata correttamente

I canali futuri sono mobile e desktop.

### Requisiti {#requirements}

**Configura e-mail**

Affinché il canale e-mail funzioni, le notifiche devono essere configurate e-mail.

Per istruzioni sulla configurazione dell’e-mail, consulta [Configurazione e-mail](analytics.md).

**Abilita segui**

I componenti devono essere configurati per abilitare quanto segue. Funzioni che consentono quanto segue: [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [filelibrio](file-library.md)e [commenti](comments.md).

Tieni presente che

* Componenti utilizzati nella community [modelli di sito](sites.md) e [modelli di gruppo](tools-groups.md) può essere già configurato per consentire quanto segue

* I profili dei membri sono già configurati per consentire ad altri membri di seguire

## Notifiche da {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

La **Segui** Questo pulsante consente di seguire le voci come attività, abbonamenti e/o notifiche. Ogni volta che **Segui** è selezionato, è possibile attivare o disattivare una selezione. La `Email Subscriptions` la selezione è presente solo se configurata.

Se è selezionato un metodo di seguito, il testo del pulsante diventa **Seguente**. Per comodità, è possibile selezionare `Unfollow All` per disattivare tutti i metodi.

La **Segui** apparirà

* Visualizzazione del profilo di un altro membro
* In una pagina principale con funzioni quali forum, QnA e blog
   * Segue tutta l&#39;attività per quella funzione generale
* Per un post specifico, ad esempio un argomento del forum, una domanda QnA o un articolo di blog
   * Segue tutte le attività per quella voce specifica

## Gestione delle impostazioni di notifica {#managing-notification-settings}

Selezionando il collegamento Impostazioni notifiche dalla pagina Notifiche, è possibile per ogni membro gestire la modalità di ricezione delle notifiche.

Il canale web è sempre abilitato.

![chlimage_1-255](assets/chlimage_1-255.png)

Il canale e-mail, che si basa sul [configurazione dell’e-mail](email.md), fornisce le stesse impostazioni del canale web.

Il canale e-mail è disattivato per impostazione predefinita.

![chlimage_1-256](assets/chlimage_1-256.png)

Può essere attivato da un membro, ma dipende comunque dalla configurazione dell’e-mail.

![chlimage_1-257](assets/chlimage_1-257.png)

## Visualizzazione delle notifiche {#viewing-notifications}

### Notifiche web {#web-notifications}

A [creazione guidata sito community](sites-console.md) ora include un collegamento alla `Notifications` nella barra dell&#39;intestazione del sito sopra il banner. A differenza dei messaggi, le notifiche vengono create per ogni sito della community, mentre i messaggi devono essere attivati durante il processo di creazione del sito.

Quando visiti il sito pubblicato, seleziona la `Notifications` visualizza tutte le notifiche per il membro.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notifiche e-mail {#email-notifications}

Quando il canale e-mail è abilitato, il membro riceve un messaggio e-mail contenente un collegamento al contenuto sul web.

![chlimage_1-259](assets/chlimage_1-259.png)
