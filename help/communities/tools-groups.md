---
title: Modelli per gruppi
seo-title: Modelli per gruppi
description: Come accedere alla console Modelli di gruppo
seo-description: Come accedere alla console Modelli di gruppo
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---

# Modelli per gruppi {#group-templates}

La console Modelli di gruppo è molto simile alla console [Modelli di sito](sites.md). Entrambe sono blueprint per un set di pagine e funzionalità precablate che formano un sito community. La differenza consiste nel fatto che un modello di sito è per la comunità principale e un modello di gruppo è per un gruppo community, una sottocomunità nidificata all’interno della comunità principale.

Un gruppo di community viene incorporato in un modello di sito includendo la [funzione Groups](functions.md#groups-function) (che non può essere la prima funzione o solo nel modello).

Per quanto riguarda Communities [feature pack 1](deploy-communities.md#latestfeaturepack), è possibile nidificare i gruppi includendo la funzione Groups all&#39;interno di un modello di gruppo.

Nel momento in cui viene intrapresa l&#39;azione per creare un nuovo gruppo community, viene selezionato il modello del gruppo (struttura). La selezione dipende dalla configurazione della funzione Groups (Gruppi) quando viene aggiunta al modello di sito o di gruppo.

>[!NOTE]
>
>Le console per la creazione di [siti della community](sites-console.md), [modelli di sito della community](sites.md), [modelli di gruppo della community](tools-groups.md) e [funzioni della community](functions.md) sono utilizzabili solo nell’ambiente di authoring.

## Console Modelli di gruppo {#group-templates-console}

Nell’ambiente di creazione, per raggiungere la console dei modelli di gruppi

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Modelli di gruppo]**

Questa console visualizza i modelli da cui è possibile creare un [sito community](sites-console.md) e consente di creare nuovi modelli di gruppo.

![branco](assets/groupstemplate.png)

## Crea modello di gruppo {#create-goup-template}

Per iniziare a creare un nuovo modello di gruppo, seleziona **[!UICONTROL Crea]**

Viene visualizzato il pannello Editor sito che contiene 3 pannelli secondari:

### Informazioni di base {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

Nel pannello Informazioni di base sono configurati un nome, una descrizione e se il modello è abilitato o disabilitato:

* **[!UICONTROL Nuovo]**
nome del modello di gruppoID del modello

* ****
DescrizioneDescrizione del modello

* **[!UICONTROL Interruttore Disabilitato/]**
AbilitatoA che controlla se il modello è referenziabile

### Miniatura  {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

(Facoltativo) Seleziona l’icona Carica immagine per visualizzare una miniatura insieme a Nome e Descrizione per i creatori dei siti della community.

### Struttura {#structure}

>[!CAUTION]
>
>Se lavori con AEM 6.1 Communities FP4 o versioni precedenti, non aggiungere una funzione gruppi a un modello di gruppo.
>
>La funzione dei gruppi nidificati è disponibile a partire da Communities [FP1](communities.md#latestfeaturepack).
>
>Non è ancora consentito aggiungere una funzione Groups come prima o unica funzione in un modello.

![grptemplateeditor](assets/grptemplateeditor.png)

Per aggiungere funzioni di community, trascina da destra a sinistra nell’ordine in cui dovrebbero essere visualizzati i collegamenti al menu del sito. Gli stili verranno applicati al modello durante la creazione del sito.

Ad esempio, se desideri un forum, trascina la funzione forum dalla libreria e rilascia sotto il generatore di modelli. In questo modo si aprirà la finestra di dialogo di configurazione del forum. Per informazioni sulle finestre di dialogo di configurazione, consulta la [console funzioni](functions.md) .

Trascina e rilascia tutte le altre funzioni della community desiderate per un sito (gruppo) della sottocommunity basato su questo modello.

![draga](assets/dragfunctions.png)

Una volta che tutte le funzioni desiderate sono state rilasciate nell&#39;area del generatore di modelli e configurate, seleziona **[!UICONTROL Salva]** nell&#39;angolo in alto a destra.

##  Modifica modello gruppo {#edit-group-template}

Quando visualizzi i gruppi della community nella console principale [Modelli di gruppo](#group-templates-console), è possibile selezionare un modello di gruppo esistente da modificare.

La modifica di un modello di gruppo non influisce sui siti della community già creati dal modello. È invece possibile modificare direttamente la struttura di un sito della community ](sites-console.md#modify-structure).[

Questo processo fornisce gli stessi pannelli di [creazione di un modello di gruppo](#create-goup-template).
