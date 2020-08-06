---
title: Notifiche community
seo-title: Notifiche community
description: ' AEM Communities dispone di notifiche che mostrano eventi di interesse per il membro della community che ha effettuato l''accesso'
seo-description: ' AEM Communities dispone di notifiche che mostrano eventi di interesse per il membro della community che ha effettuato l''accesso'
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 1%

---


# Notifiche community {#communities-notifications}

## Panoramica {#overview}

 AEM Communities fornisce una sezione delle notifiche che mostra gli eventi di interesse per i membri della community sottoscritti.

Le notifiche sono simili alle [attività](essentials-activities.md) e alle [sottoscrizioni](subscriptions.md) derivanti da

* Contenuto di pubblicazione membro
* Il membro che sceglie di seguire un altro membro
* Il membro che sceglie di seguire argomenti, articoli e altri thread specifici di contenuto

Ciò che distingue le notifiche dalle attività e dalle sottoscrizioni è

* Un collegamento alla sezione delle notifiche è sempre presente nell&#39;intestazione di un sito community
   * Le attività richiedono che la funzione [del flusso di](functions.md#activity-stream-function) attività sia inclusa nella struttura del sito community
   * Le iscrizioni richiedono [la configurazione dell&#39;e-mail](email.md)
* L&#39;implementazione delle notifiche avviene tramite canali scalabili e collegabili
   * Le attività sono disponibili solo sul Web
   * Le iscrizioni sono disponibili solo tramite e-mail

A livello di Community [FP1](deploy-communities.md#latestfeaturepack), i canali di notifica disponibili sono

* Canale Web a cui si accede tramite il `Notifications` collegamento
* Il canale e-mail, disponibile quando l’e-mail è configurato correttamente

I canali futuri sono mobile e desktop.

### Requisiti {#requirements}

**Configura e-mail**

Affinché il canale e-mail possa funzionare, è necessario configurare l’e-mail.

Per istruzioni sulla configurazione dell’e-mail, consultate [Configurazione dell’e-mail](analytics.md).

**Abilita Follow**

I componenti devono essere configurati per abilitare quanto segue. Le funzioni che consentono di seguire sono [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [filibreria](file-library.md)[](comments.md), commenti.

Tieni presente che

* I componenti utilizzati all&#39;interno dei modelli [di](sites.md) sito community e dei modelli [di](tools-groups.md) gruppo possono già essere configurati per consentire quanto segue

* I profili dei membri sono già configurati per consentire agli altri membri di seguire

## Notifiche dai seguenti {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

Il pulsante **Segui** consente di seguire le voci come attività, iscrizioni e/o notifiche. Ogni volta che si seleziona il pulsante **Segui** , è possibile attivare o disattivare una selezione. La `Email Subscriptions` selezione è presente solo se configurata.

Se è selezionato un metodo di seguito, il testo del pulsante diventa **Seguente**. Per comodità, è possibile selezionare `Unfollow All` per disattivare tutti i metodi.

Verrà visualizzato il pulsante **Segui**

* Quando si visualizza il profilo di un altro membro
* In una pagina delle funzioni principali, ad esempio forum, QnA e blog
   * Segue tutta l&#39;attività per la funzione generale
* Per un post specifico, ad esempio un argomento forum, una domanda QnA o un articolo blog
   * Segue tutta l&#39;attività per la voce specifica

## Gestione delle impostazioni di notifica {#managing-notification-settings}

Selezionando il collegamento Impostazioni notifica dalla pagina Notifiche, è possibile per ciascun membro gestire il modo in cui vengono ricevute le notifiche.

Il canale Web è sempre abilitato.

![chlimage_1-255](assets/chlimage_1-255.png)

Il canale e-mail, che si basa sulla corretta [configurazione dell’e-mail](email.md), fornisce le stesse impostazioni del canale Web.

Il canale e-mail è disattivato per impostazione predefinita.

![chlimage_1-256](assets/chlimage_1-256.png)

Può essere attivata da un membro, ma dipende comunque dalla configurazione dell&#39;e-mail.

![chlimage_1-257](assets/chlimage_1-257.png)

## Visualizzazione delle notifiche {#viewing-notifications}

### Notifiche Web {#web-notifications}

Una [procedura guidata per la creazione di un sito](sites-console.md) community ora include un collegamento alla `Notifications` funzione nella barra dell&#39;intestazione del sito, sopra il banner. A differenza dei messaggi, le notifiche vengono create per ogni sito community, mentre i messaggi devono essere attivati durante il processo di creazione del sito.

Quando si visita il sito pubblicato, selezionando il `Notifications` collegamento vengono visualizzate tutte le notifiche relative al membro.

![chlimage_1-258](assets/chlimage_1-258.png)

### Notifiche e-mail {#email-notifications}

Quando il canale e-mail è abilitato, il membro riceve un messaggio e-mail contenente un collegamento al contenuto sul Web.

![chlimage_1-259](assets/chlimage_1-259.png)

