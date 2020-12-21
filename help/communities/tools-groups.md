---
title: Modelli per gruppi
seo-title: Modelli per gruppi
description: Come accedere alla console Modelli gruppo
seo-description: Come accedere alla console Modelli gruppo
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---


# Modelli per gruppi {#group-templates}

La console Modelli per gruppi è molto simile alla console [Site Templates](sites.md). Entrambi sono blueprint per un set di pagine e funzionalità precablate che formano un sito community. La differenza è che un modello di sito è per la comunità principale e un modello di gruppo è per un gruppo di community, una sottocomunità nidificata all&#39;interno della comunità principale.

Un gruppo community è incorporato in un modello di sito includendo la funzione [Groups](functions.md#groups-function) (che non può essere né la prima né la sola funzione nel modello).

Per quanto riguarda Communities [feature pack 1](deploy-communities.md#latestfeaturepack), è possibile nidificare i gruppi includendo la funzione Groups all&#39;interno di un modello di gruppo.

Nel momento in cui viene eseguita l&#39;azione per creare un nuovo gruppo community, viene selezionato il modello (struttura) del gruppo. La selezione dipende dalla configurazione della funzione Gruppi al momento dell&#39;aggiunta al modello di sito o di gruppo.

>[!NOTE]
>
>Le console per la creazione di [siti community](sites-console.md), [modelli di siti community](sites.md), [modelli di gruppi community](tools-groups.md) e [funzioni community](functions.md) sono utilizzabili solo nell&#39;ambiente di authoring.

## Console Modelli gruppo {#group-templates-console}

Nell’ambiente di authoring, per accedere alla console dei modelli per gruppi

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Modelli di gruppo]**

Questa console visualizza i modelli da cui è possibile creare un [sito community](sites-console.md) e consente di creare nuovi modelli di gruppo.

![groupstemplate](assets/groupstemplate.png)

## Crea modello gruppo {#create-goup-template}

Per iniziare a creare un nuovo modello di gruppo, selezionate **[!UICONTROL Crea]**

Viene visualizzato il pannello Editor sito che contiene 3 sottopannelli:

### Informazioni di base {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

Nel pannello Informazioni di base, un nome, una descrizione e se il modello è abilitato o disabilitato sono configurati:

* **[!UICONTROL Nuovo]**
nome modello gruppoID nome modello

* **[!UICONTROL DescrizioneDescrizione]**
del modello

* **[!UICONTROL Disabilitato/]**
AbilitatoUn interruttore per controllare se il modello è referente o meno

### Miniatura  {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Facoltativo) Selezionate l’icona Carica immagine per visualizzare una miniatura con il nome e la descrizione per gli autori dei siti della community.

### Struttura {#structure}

>[!CAUTION]
>
>Se lavorate con AEM 6.1 Communities FP4 o versioni precedenti, non aggiungete una funzione di gruppo a un modello di gruppo.
>
>La funzione dei gruppi nidificati è disponibile a partire da Communities [FP1](communities.md#latestfeaturepack).
>
>Non è ancora consentito aggiungere una funzione Groups come prima o unica funzione in un modello.

![grptemplateeditor](assets/grptemplateeditor.png)

Per aggiungere funzioni per la community, trascinate dal lato destro a sinistra nell&#39;ordine in cui dovrebbero essere visualizzati i collegamenti del menu del sito. Gli stili verranno applicati al modello durante la creazione del sito.

Ad esempio, se desiderate un forum, trascinate la funzione forum dalla libreria e rilasciatela sotto il generatore di modelli. In questo modo si aprirà la finestra di dialogo di configurazione del forum. Per informazioni sulle finestre di dialogo di configurazione, vedere la [console delle funzioni](functions.md).

Trascinate e rilasciate tutte le altre funzioni della community desiderate per un sito della community secondaria (gruppo) basato su questo modello.

![dragfunzioni](assets/dragfunctions.png)

Una volta che tutte le funzioni desiderate sono state rilasciate nell&#39;area del generatore di modelli e configurate, selezionare **[!UICONTROL Save]** nell&#39;angolo superiore destro.

##  Modifica modello gruppo{#edit-group-template}

Quando visualizzate i gruppi della community nella console principale [Modelli di gruppo](#group-templates-console), è possibile selezionare un modello di gruppo esistente da modificare.

La modifica di un modello di gruppo non ha effetto sui siti community già creati dal modello. È possibile [modificare direttamente la struttura di un sito della community ](sites-console.md#modify-structure).

Questo processo fornisce gli stessi pannelli di [creazione di un modello di gruppo](#create-goup-template).
