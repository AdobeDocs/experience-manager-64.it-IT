---
title: Gruppi community
seo-title: Gruppi community
description: Creazione di gruppi community
seo-description: Creazione di gruppi community
uuid: 05429b23-9083-498c-9eb3-d49b049d9446
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 868a3d5d-d505-4ce5-8776-5bbe68a30ccb
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87

---


# Gruppi community {#community-groups}

La funzione per i gruppi della community è la possibilità per una sottocomunità di essere creata in modo dinamico all&#39;interno di un sito della community da utenti autorizzati (membri della community e autori) dagli ambienti di pubblicazione e authoring.

Questa capacità è presente quando la funzione [](functions.md#groups-function) dei gruppi è presente nella struttura del sito [](sites-console.md) community.

Un modello [di gruppo](tools-groups.md) community fornisce la progettazione della pagina di gruppo community quando un gruppo community viene creato in modo dinamico.

Uno o più modelli di gruppo vengono selezionati per la funzione dei gruppi quando la funzione viene aggiunta alla struttura di un sito community o a un modello di sito community. Questo elenco di modelli di gruppo viene presentato al membro o all&#39;autore che crea in modo dinamico un nuovo gruppo dall&#39;interno del sito della community.

## Creazione di un nuovo gruppo {#creating-a-new-group}

La capacità di creare un nuovo gruppo di community si basa sull&#39;esistenza di un sito community che include la funzione dei gruppi, come quella creata dal ` [Reference Site Template](sites.md)`.

Gli esempi che seguono utilizzano il sito della community creato a partire dal `Reference Site Template` sito come descritto nell&#39;esercitazione [Guida introduttiva ad AEM Communities](getting-started.md) .

Pagina che viene caricata al momento della pubblicazione quando è selezionata la voce di menu **[!UICONTROL Gruppi]** :

![chlimage_1-236](assets/chlimage_1-236.png)

Quando selezionate l’icona **[!UICONTROL Nuovo gruppo]** , si apre una finestra di dialogo di modifica.

Nella scheda **[!UICONTROL Impostazioni]** , sono disponibili le funzioni di base del gruppo:

![chlimage_1-237](assets/chlimage_1-237.png)

* **[!UICONTROL Nome]** gruppo Titolo del gruppo da visualizzare sul sito della community.

* **[!UICONTROL Descrizione]** Una descrizione del gruppo da visualizzare sul sito della community.

* **[!UICONTROL Invita]** Un elenco di membri da invitare a far parte del gruppo. La ricerca con tipo di programma fornirà suggerimenti da invitare ai membri della community.

* **[!UICONTROL Nome]** URL gruppo Il nome della pagina del gruppo che diventa parte dell’URL.

* **[!UICONTROL Apri gruppo]** Selezionando `Open Group` , qualsiasi visitatore anonimo del sito potrebbe visualizzare il contenuto e verrà deselezionato `Member Only Group`.

* **[!UICONTROL Gruppo]** Solo membriSelezionando `Member Only Group` solo i membri del gruppo possono visualizzare il contenuto e deselezionare `Open Group`.

Nella scheda **[!UICONTROL Modello]** è possibile selezionare dall&#39;elenco dei modelli di gruppo community specificati quando la funzione dei gruppi è stata inclusa nella struttura del sito community o in un modello di sito community.

![chlimage_1-238](assets/chlimage_1-238.png)

Nella scheda **[!UICONTROL Immagine]** è possibile caricare un&#39;immagine da visualizzare per il gruppo nella pagina Gruppi del sito della community. Il foglio di stile predefinito ridimensiona l&#39;immagine a 170 x 90 pixel.

![chlimage_1-239](assets/chlimage_1-239.png)

Selezionando il pulsante **[!UICONTROL Crea gruppo]** , le pagine del gruppo vengono create in base al modello scelto e viene creato un gruppo di utenti per l’iscrizione. La pagina Gruppi verrà aggiornata per mostrare la nuova sub-community.

Ad esempio, la pagina Gruppi con una nuova sottocomunità denominata &quot;Focus Group&quot;, per la quale è stata caricata una miniatura di immagine, verrà visualizzata come segue (ancora con accesso come amministratore di gruppo community):

![chlimage_1-240](assets/chlimage_1-240.png)

Selezionando il `Focus Group` collegamento, si aprirà la pagina Gruppo di interesse nel browser, con un aspetto iniziale basato sul modello scelto, e un sottomenu sotto il menu del sito della community principale:

![chlimage_1-241](assets/chlimage_1-241.png)

## Community Group Member List Component {#community-group-member-list-component}

Il `Community Group Member List` componente è destinato agli sviluppatori di modelli di gruppo.

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Community Group Essentials](essentials-groups.md) per gli sviluppatori.

Per altre informazioni relative ai gruppi della community, visita [Gestione di utenti e gruppi](users.md)di utenti.
