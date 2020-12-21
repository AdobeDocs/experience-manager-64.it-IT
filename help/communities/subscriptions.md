---
title: Iscrizioni community
seo-title: Iscrizioni community
description: 'I membri della community interagiscono con altri membri tramite e-mail '
seo-description: 'I membri della community interagiscono con altri membri tramite e-mail '
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 1%

---


# Iscrizioni community {#communities-subscriptions}

## Panoramica {#overview}

A partire da Communities [FP1](deploy-communities.md#latestfeaturepack), i membri della community possono interagire con la community tramite e-mail utilizzando una funzione denominata come abbonamenti.

Le iscrizioni sono simili alle [notifiche](notifications.md) in quanto i membri possono iscriversi quando seguono articoli di blog, argomenti di forum o domande di QnA.

Ciò che distingue le sottoscrizioni dalle notifiche è:

* I membri non possono iscriversi quando seguono altri membri
* L&#39;unica azione che i membri devono intraprendere è selezionare `Email Subscriptions` quando segue
* Quando è configurata la risposta e-mail, i membri possono pubblicare contenuti semplicemente rispondendo all&#39;e-mail ricevuta

### Requisiti {#requirements}

**Configura e-mail**

Affinché le iscrizioni funzionino e i membri rispondano via e-mail, è necessario configurare l&#39;e-mail.

Per istruzioni sulla configurazione dell&#39;e-mail, vedere [Configurazione di e-mail](email.md).

**Abilita iscrizioni e segui**

I componenti devono essere configurati per abilitare le iscrizioni *e* seguenti. Le funzioni che consentono l&#39;iscrizione sono [blog](blog-feature.md), [forum](forum.md) e [QnA](working-with-qna.md).

## Iscrizioni da {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

Il pulsante **Segui** consente di seguire le voci come attività, iscrizioni e/o notifiche. Ogni volta che il tasto **Segui** è selezionato, è possibile attivare o disattivare una selezione.

Se è selezionato un metodo di seguito, il testo del pulsante diventa **Successivo**. Per comodità, è possibile selezionare `Unfollow All` per disattivare tutti i metodi.

Il pulsante **Segui** includerà l&#39;opzione `Email Subscriptions` solo quando un forum, QnA o un blog è configurato per abilitare le iscrizioni alle e-mail. Questo pulsante verrà visualizzato

* Nella pagina delle funzioni principali per il forum abilitato, QnA o il blog

   * Invierà un&#39;e-mail per tutte le attività in quella funzionalità

* Per un post specifico, ad esempio un argomento forum, una domanda QnA o un articolo blog

   * Invia un messaggio e-mail quando esiste attività per la voce specifica

## Rispondi per e-mail {#reply-by-email}

Quando l&#39;e-mail è [configurata per la risposta tramite e-mail](email.md#configure-polling-importer), il membro che ha effettuato l&#39;iscrizione riceverà un&#39;e-mail con il contenuto pubblicato e un collegamento al contenuto online.

Se rispondono all’e-mail, il contenuto immesso nella risposta verrà visualizzato come contenuto online.

![chlimage_1-6](assets/chlimage_1-6.png)

Il tempo necessario per inviare una risposta è controllato dall&#39;intervallo di aggiornamento dell&#39;importatore [polling ](email.md#configure-polling-importer).

![chlimage_1-7](assets/chlimage_1-7.png)

