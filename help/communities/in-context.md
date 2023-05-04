---
title: Moderazione nel contesto
seo-title: In-Context Moderation
description: Come eseguire azioni di moderatore
seo-description: How to perform moderator actions
uuid: 282a8bea-2822-4e5c-b9f4-4d9a5380d895
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ee104f6f-123b-4a6e-9031-849fc1318cc5
role: Admin
exl-id: a7678273-81f6-4089-ac73-2458d940e374
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 2%

---

# Moderazione nel contesto {#in-context-moderation}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per AEM Communities, la moderazione può essere eseguita da amministratori e membri della community fidati direttamente nella pagina pubblicata in cui è stato pubblicato il contenuto della community.

Quando si utilizza un [console di moderazione](moderation.md), le informazioni visualizzate per il contenuto includono un collegamento alla pagina pubblicata per consentire l’accesso a ulteriori azioni di moderazione disponibili durante la moderazione nel contesto.

## Azioni di moderazione {#moderation-actions}

Per una descrizione di [azioni di moderazione](moderate-ugc.md#moderation-actions).

## Interfaccia utente di moderazione {#moderation-ui}

L’interfaccia utente presentata al moderatore nell’istanza di pubblicazione è contenuta nella finestra di dialogo per la pubblicazione e la gestione del contenuto generato dall’utente (UGC). Gli elementi dell’interfaccia utente sono determinati dallo stato del visitatore del sito, indipendentemente dal fatto che siano...

1. Membro che ha pubblicato il contenuto
1. Un moderatore membro affidabile
1. Amministratore
1. Accesso eseguito da un amministratore, un moderatore o un autore del contenuto
1. Accesso non effettuato

## Esempio {#example}

Utilizzo della [Geometrixx Engage](http://localhost:4503/content/sites/engage/en.html) sito creato quando [Guida introduttiva ad AEM Communities](getting-started.md), è possibile impostare rapidamente un thread in un forum in cui sperimentare varie attività di moderazione nell&#39;ambiente di pubblicazione, come mostrato di seguito.

Aaron McDonald (aaron.mcdonald@mailinator.com) è stato identificato come membro fidato della comunità aggiungendo lui al gruppo di moderatori-impegnati della comunità durante la creazione del sito.

Rebekah Larsen (rebekah.larsen@trashymail.com) può essere aggiunto come membro del gruppo di membri della community che coinvolgono i membri utilizzando [Console dei membri](members.md).

Per ulteriori informazioni sui gruppi di utenti della community, visita [Gestione di utenti e gruppi di utenti](users.md).

### Creare i post del forum {#create-the-forum-posts}

* Accedi come Rebekah Larsen (rebekah.larsen@trashymail.com)

   * Seleziona forum
   * Seleziona nuovo post
   * Inserisci l&#39;oggetto

      Quando cambiare il nettare nell&#39;Alimentatore Umano di Uccello

   * Inserisci il testo del corpo

      Non ho avuto molto successo quando appendo un mangime per colibrì ogni anno. Sembra che arrivino un giorno o due allora questo è tutto. Lo cambio una volta alla settimana è troppo lungo? Devo cambiarla prima?
   * Seleziona post
   * Seleziona Esci

* Accedi come Aaron McDonald (aaron.mcdonald@mailinator.com)

   * Seleziona forum
   * Per l&#39;argomento Hummingbird, selezionare Leggi tutto
   * Inserisci il commento per Risposta post

      Io cambio la mia una volta alla settimana e le ricevo da maggio a ottobre.

   * Seleziona risposta
   * Seleziona Esci

* Accedi come Andrew Schaeffer (andrew.schaeffer@trashymail.com)

   * Seleziona forum
   * Per l&#39;argomento Hummingbird, selezionare Leggi tutto
   * Inserisci il commento per Risposta post

      Vendo nettare e alimentatori - visita https://my.viral.url/

   * Seleziona risposta
   * Seleziona Esci

### Visitatore del sito anonimo (#5) {#anonymous-site-visitor}

Di seguito è riportata una visualizzazione del forum visualizzato da un visitatore del sito che non ha effettuato l’accesso (5).

Un visitatore anonimo del sito può solo visualizzare il forum, ma non può pubblicare alcun contenuto né eseguire azioni di moderazione.

![chlimage_1](assets/chlimage_1.png)

### Nuovo membro (#4) {#new-member}

Sull&#39;autore, accedi come amministratore e aggiungi Boyd Larsen (boyd.larsen@dodgit.com) come nuovo membro del gruppo di membri della community-coinvolgiti utilizzando [Console dei membri](members.md), quindi Esci.

Al momento della pubblicazione, accedi come Boyd Larsen e accedi al thread selezionando `Forum`e quindi `Read more` per il post colibrì.

Avviso

* Boyd non ha partecipato al forum
* Boyd non può eliminare nulla
* Boyd è connesso e può rispondere o contrassegnare il contenuto

Chiedi a Boyd di selezionare Flag per contrassegnare il contenuto pubblicato da Andrew.

Disconnetti

![chlimage_1-1](assets/chlimage_1-1.png)

### Amministratore (#3) {#administrator}

Accedi come amministratore (amministratore) e accedi al thread selezionando Forum, quindi Ulteriori informazioni per un post.

Avviso

* L’Amministratore può contrassegnare, eliminare, modificare, rifiutare, tagliare, chiudere, fissare, feature
* L’amministratore può selezionare Amministrazione per accedere alla console di moderazione

![communityadmin-forum](assets/communityadmin-forum.png)

Seleziona la voce di menu Amministrazione per accedere alla [console di moderazione](moderation.md) dall’ambiente di pubblicazione.

Tieni presente che, per un amministratore, tutti i contenuti modificabili sono visibili, non solo quelli del sito della community di Geometrixx Engage.

Il filtro di ricerca è un pannello laterale che attiva o disattiva l’apertura o la chiusura.

Disconnetti.

![moderationconsole-publish](assets/moderationconsole-publish.png)

### Moderatore community (#2) {#community-moderator}

Accedi come Aaron McDonald (aaron.mcdonal@mailinator.com), un moderatore della comunità, e accedi al thread selezionando Forum, e poi Ulteriori informazioni per il post colibrì.

Avviso

* Aaron può rispondere, eliminare, modificare o negare il proprio post
* Aaron può anche contrassegnare/consentire, rispondere, eliminare, modificare, negare altri contenuti
* Aaron può tagliare l&#39;argomento del forum per spostarlo in un altro forum per il quale modera
* Aaron può selezionare Amministrazione per accedere alla console di moderazione

![chlimage_1-2](assets/chlimage_1-2.png)

Seleziona la voce di menu Amministrazione per accedere alla [console di moderazione](moderation.md) dall’ambiente di pubblicazione.

Nota che, per un moderatore della community, è visibile solo il contenuto moderabile del sito della community di Geometrixx Engage.

Il moderatore della community dispone delle stesse opzioni dell’amministratore (l’immagine è con la barra laterale di ricerca disattivata), ma non ha accesso ad altre console AEM.

Disconnetti.

![moderatoraccess](assets/moderatoraccess.png)

### Autore del contenuto (#1) {#content-author}

Accedi come Rebekah Larsen (rebekah.larsen@mailinator.com), un membro della comunità che ha avviato il thread, e accedi al thread selezionando Forum, e poi Ulteriori informazioni per il post di colibrì.

Avviso

* Rebekah può eliminare o modificare il proprio post
* Rebekah può anche rispondere o contrassegnare altri contenuti
* Rebekah non può accedere alla console di moderazione

![chlimage_1-3](assets/chlimage_1-3.png)
