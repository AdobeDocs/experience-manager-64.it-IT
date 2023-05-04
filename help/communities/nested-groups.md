---
title: Creazione di gruppi nidificati
seo-title: Authoring Nested Groups
description: Creare gruppi nidificati
seo-description: Create nested groups
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 5%

---

# Creazione di gruppi nidificati {#authoring-nested-groups}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Creazione di gruppi sull’autore {#creating-groups-on-author}

Autore, navigazione globale

* Seleziona **[!UICONTROL Community > Sites]**
* Seleziona **[!UICONTROL cartella di interazione]** per aprirlo
* Seleziona la scheda per la **[!UICONTROL Esercitazione introduttiva]**  sito inglese
   * Seleziona l&#39;immagine della scheda
   * Do *not* seleziona un’icona

Il risultato è quello di raggiungere il [Console Gruppi](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

La funzione gruppi verrà visualizzata come una cartella in cui vengono create le istanze dei gruppi. Selezionare la cartella Groups per aprirla. Il gruppo creato al momento della pubblicazione è visibile.

![chlimage_1-54](assets/chlimage_1-54.png)

## Crea gruppo di arti principali {#create-main-arts-group}

Questo gruppo può essere creato perché la struttura del sito per l&#39;interazione include una funzione di gruppi. Configurazione della funzione nel sito `Reference Template` consente per impostazione predefinita la selezione di qualsiasi modello di gruppo abilitato. Pertanto, il modello scelto per questo nuovo gruppo sarà il `Reference Group`.

Queste console sono molto simili alla console Sites di Communities.

* Seleziona **[!UICONTROL Crea gruppo]**
* `1 Community Group Template`:
   * Titolo gruppo community: Arti
   * Descrizione gruppo community: Un gruppo di genitori per vari gruppi artistici.
   * Radice gruppo community: *lascia come predefinito*
   * Lingue disponibili aggiuntive per gruppi di community: utilizza il menu a discesa per selezionare le lingue disponibili per i gruppi di community. Nel menu vengono visualizzate tutte le lingue in cui viene creato il sito della community principale. In questo singolo passaggio gli utenti possono selezionare una di queste lingue per creare gruppi in più impostazioni internazionali. Lo stesso gruppo viene creato in più lingue specificate nella console Gruppi dei rispettivi siti della community.
   * Nome gruppo community: arte
   * Modello: scendere per selezionare `Reference Group`
   * Seleziona `Next`

      ![gentonestedgroup](assets/parenttonestedgroup.png)

Procedi attraverso gli altri pannelli con le seguenti impostazioni:

* **2 Design**
   * È possibile modificare la progettazione o consentire l&#39;impostazione predefinita della progettazione del sito padre
   * Seleziona **[!UICONTROL Avanti]**
* **3 Impostazioni**
   * **Moderazione**
      * Lascia vuoto (eredita dal sito padre)
   * **Iscrizione**
      * usa predefinito `Optional Membership`
   * **Miniatura**
      * `optional`
   * Seleziona `Next`
* Seleziona **[!UICONTROL Crea]**

### Nidificazione di gruppi nel gruppo Arti {#nesting-groups-within-arts-group}

La `groups` La cartella deve ora contenere due gruppi (potrebbe essere necessario aggiornare la pagina).

![createcomunitygroup](assets/createcommunitygroup.png)

#### Pubblica gruppo {#publish-group}

Prima di creare gruppi nidificati all’interno di `arts`gruppo, passa il puntatore del mouse `arts` e seleziona l’icona pubblica per pubblicarla.

![chlimage_1-55](assets/chlimage_1-55.png)

Attendi la conferma della pubblicazione del gruppo.

![chlimage_1-56](assets/chlimage_1-56.png)

La `arts` il gruppo deve inoltre contenere `groups` ma è vuota e in cui è possibile creare nuovi gruppi. Passa alla cartella del gruppo di arti e crea 3 gruppi nidificati, ciascuno con un&#39;impostazione di appartenenza diversa:

1. Visivo
   * Titolo: `Visual Arts`
   * Nome: `visual`
   * Modello: `Reference Group`
   * Iscrizione: select `Optional Membership`
Un gruppo pubblico, aperto a tutti i membri
1. Auditor
   * Titolo: `Auditory Arts`
   * Nome: `auditory`
   * Modello: `Reference Group`
   * Iscrizione: select `Required Membership`
Un gruppo aperto, disponibile per i membri

1. Storia

   * Titolo: `Art History`
   * Nome: `history`
   * Modello: `Reference Group`
   * Iscrizione: select `Restricted Membership`
Un gruppo segreto, visibile solo ai membri invitati come esempio, invita 
[utente dimostrativo](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Aggiorna la pagina per visualizzare tutti e tre i gruppi nidificati (sottocommunity).

Se necessario, per passare ai gruppi nidificati dalla console Sites di Communities:

* Seleziona **[!UICONTROL cartella di interazione]**
* Seleziona **[!UICONTROL Esercitazione introduttiva]** scheda
* Seleziona **[!UICONTROL Cartella Gruppi]**
* Seleziona **[!UICONTROL carta d&#39;arte]**
* Seleziona **[!UICONTROL Cartella Gruppi]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Gruppi di pubblicazione {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Dopo aver pubblicato il sito della comunità principale, è necessario

* Pubblica ciascun gruppo singolarmente
   * In attesa di conferma della pubblicazione del gruppo
* Pubblica un gruppo padre prima di pubblicare qualsiasi gruppo nidificato all’interno di
   * Tutti i gruppi devono essere pubblicati in modo top-down.

![chlimage_1-59](assets/chlimage_1-59.png)

## Esperienza su Publish {#experience-on-publish}

È possibile utilizzare i diversi gruppi al momento dell’accesso, ad esempio con [utenti dimostrativi](tutorials.md#demo-users) utilizzato per

* Membro del gruppo Art/History: emily.andrews@mailinator.com/password
   * Il gruppo ristretto (segreto), arte/storia sarà visibile
   * Può visualizzare gruppi facoltativi (pubblici)
   * Può unire gruppi limitati (aperti)
* Gestione dei gruppi: aaron.mcdonald@mailinator.com/password
   * Può visualizzare gruppi facoltativi (pubblici)
   * può unire gruppi limitati (aperti)
   * Non vedrà gruppi limitati (segreti)

Accesso alle community [Console Membri e gruppi](members.md) sull&#39;autore per aggiungere altri utenti a vari gruppi di membri che corrispondono ai gruppi della community.
