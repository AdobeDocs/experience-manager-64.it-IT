---
title: Creazione di gruppi nidificati
seo-title: Creazione di gruppi nidificati
description: Creazione di gruppi nidificati
seo-description: Creazione di gruppi nidificati
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 4%

---


# Creazione di gruppi nidificati {#authoring-nested-groups}

## Creazione di gruppi sull&#39;autore {#creating-groups-on-author}

Per l&#39;authoring, dalla navigazione globale

* Seleziona **[!UICONTROL Community > Siti]**
* Selezionate la cartella **** di interazione per aprirla
* Selezionate la scheda per il sito **[!UICONTROL Guida introduttiva all&#39;esercitazione]** inglese
   * Selezionate l&#39;immagine della scheda
   * Non *selezionare* un&#39;icona

Il risultato è di raggiungere la console [](groups.md)Gruppi:

![chlimage_1-53](assets/chlimage_1-53.png)

La funzione dei gruppi verrà visualizzata come una cartella in cui vengono create le istanze dei gruppi. Selezionate la cartella Gruppi per aprirla. Il gruppo creato al momento della pubblicazione è visibile.

![chlimage_1-54](assets/chlimage_1-54.png)

## Crea gruppo di arti principali {#create-main-arts-group}

Questo gruppo può essere creato perché la struttura del sito per il coinvolgimento include una funzione di gruppi. Per impostazione predefinita, la configurazione della funzione nel sito `Reference Template` consente la selezione di qualsiasi modello di gruppo abilitato. Pertanto, il modello scelto per questo nuovo gruppo sarà il `Reference Group`.

Queste console sono molto simili alla console Siti di Communities.

* Seleziona **[!UICONTROL Crea gruppo]**
* `1 Community Group Template`:
   * Titolo gruppo community: Arti
   * Descrizione gruppo community: Un gruppo padre per vari gruppi artistici.
   * Radice gruppo community: *left as default*
   * Lingue aggiuntive per i gruppi di community disponibili:utilizzate il menu a discesa per selezionare le lingue disponibili per i gruppi di community. Nel menu vengono visualizzate tutte le lingue in cui viene creato il sito community principale. Gli utenti possono selezionare una di queste lingue per creare gruppi in più lingue in questo singolo passaggio. Lo stesso gruppo viene creato in più lingue specificate nella console Gruppi dei rispettivi siti della community.
   * Nome gruppo community: arte
   * Modello: premuto per selezionare `Reference Group`
   * Seleziona `Next`

      ![parent tonestedgroup](assets/parenttonestedgroup.png)

Proseguite attraverso gli altri pannelli con le seguenti impostazioni:

* **2 Design**
   * Potete modificare la progettazione o consentire l&#39;impostazione predefinita per la progettazione del sito padre
   * Seleziona **[!UICONTROL Avanti]**
* **3 Impostazioni**
   * **Moderazione**
      * Lascia vuoto (eredita dal sito padre)
   * **Iscrizione**
      * use default `Optional Membership`
   * **Miniatura**
      * `optional`
   * Seleziona `Next`
* Seleziona **[!UICONTROL Crea]**

### Nidificazione di gruppi all&#39;interno del gruppo Arti {#nesting-groups-within-arts-group}

La `groups` cartella deve ora contenere due gruppi (potrebbe essere necessario aggiornare la pagina).

![create ecommunitygroup](assets/createcommunitygroup.png)

#### Pubblica gruppo{#publish-group}

Prima di creare gruppi nidificati all’interno del `arts`gruppo, passate il mouse sulla `arts` scheda e selezionate l’icona Pubblica per pubblicarla.

![chlimage_1-55](assets/chlimage_1-55.png)

Attendete la conferma della pubblicazione del gruppo.

![chlimage_1-56](assets/chlimage_1-56.png)

Il `arts` gruppo deve contenere anche una `groups` cartella, ma vuota e in cui è possibile creare nuovi gruppi. Andate alla cartella del gruppo di arti e create 3 gruppi nidificati, ciascuno con un&#39;impostazione di appartenenza diversa:

1. Visuale
   * Titolo: `Visual Arts`
   * Nome: `visual`
   * Modello: `Reference Group`
   * Appartenenza: selezionate `Optional Membership`Un gruppo pubblico, aprite a tutti i membri
1. Auditory
   * Titolo: `Auditory Arts`
   * Nome: `auditory`
   * Modello: `Reference Group`
   * Appartenenza: selezionate `Required Membership`Un gruppo aperto, disponibile per i membri a partecipare

1. Storia

   * Titolo: `Art History`
   * Nome: `history`
   * Modello: `Reference Group`
   * Appartenenza: selezionate `Restricted Membership`Un gruppo segreto, visibile solo ai membri invitati come esempio, invitate 
[utente dimostrativo](tutorials.md#demo-users) `emily.andrews@mailinator.com`

Aggiornate la pagina per visualizzare tutti e tre i gruppi nidificati (sottocomunità).

Se necessario, per accedere ai gruppi nidificati dalla console Siti community:

* Seleziona cartella **[!UICONTROL di coinvolgimento]**
* Seleziona scheda **[!UICONTROL Esercitazione]** iniziale
* Seleziona cartella **[!UICONTROL Gruppi]**
* Seleziona scheda **[!UICONTROL arti]**
* Seleziona cartella **[!UICONTROL Gruppi]**

![chlimage_1-57](assets/chlimage_1-57.png)

## Pubblicazione di gruppi {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

Dopo la pubblicazione del sito della community principale, è necessario

* Pubblicare ciascun gruppo singolarmente
   * In attesa della conferma della pubblicazione del gruppo
* Pubblica gruppo padre prima di pubblicare qualsiasi gruppo nidificato all’interno di
   * Tutti i gruppi devono essere pubblicati in modo top-down.

![chlimage_1-59](assets/chlimage_1-59.png)

## Esperienza su Pubblica {#experience-on-publish}

È possibile utilizzare i diversi gruppi al momento dell&#39;accesso, ad esempio con gli utenti [](tutorials.md#demo-users) demo utilizzati per

* Membro del gruppo Art/History: emily.andrews@mailinator.com/password
   * Il gruppo limitato (segreto), arti/storia, sarà visibile
   * Può visualizzare i gruppi facoltativi (pubblici)
   * Può partecipare a gruppi limitati (aperti)
* Manager gruppo: aaron.mcdonald@mailinator.com/password
   * Può visualizzare i gruppi facoltativi (pubblici)
   * può partecipare a gruppi con restrizioni (aperti)
   * Non verranno visualizzati gruppi limitati (segreti)

Accedete alle console [Membri e Gruppi della community](members.md) sull’autore per aggiungere altri utenti a vari gruppi di membri che corrispondono ai gruppi della community.
