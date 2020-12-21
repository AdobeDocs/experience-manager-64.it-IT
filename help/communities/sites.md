---
title: Modelli per siti
seo-title: Modelli per siti
description: Come accedere alla console Modelli per sito
seo-description: Come accedere alla console Modelli per sito
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
translation-type: tm+mt
source-git-commit: 5e30bf76fd3304ed268c45cc8862a9c51c5d30f1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 4%

---


# Modelli per siti {#site-templates}

La console Modelli per sito è molto simile alla console [Modelli per gruppi](tools-groups.md), incentrata sulle funzioni di interesse per i gruppi community.

>[!NOTE]
>
>Le console per la creazione di [siti community](sites-console.md), [modelli di siti community](sites.md), [modelli di gruppi community](tools-groups.md) e [funzioni community](functions.md) sono utilizzabili solo nell&#39;ambiente di authoring.

## Console Modelli sito {#site-templates-console}

Nell’ambiente di authoring, per accedere alla console Siti community

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Modelli del sito]**

Questa console visualizza i modelli da cui è possibile creare un [sito community](sites-console.md) e consente di creare nuovi modelli di sito.

![chlimage_1-18](assets/chlimage_1-18.png)

## Crea modello sito {#create-site-template}

Per iniziare a creare un nuovo modello di sito, selezionare `Create`.

Viene visualizzato il pannello Editor sito che contiene 3 sottopannelli:

### Informazioni di base {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

Nel pannello Informazioni di base, un nome, una descrizione e se il modello è abilitato o disabilitato sono configurati:

* **[!UICONTROL Nome modello sito communityID nome modello]**


* **[!UICONTROL Descrizione]**
del modello del sito communityDescrizione del modello

* **[!UICONTROL Disabilitato/]**
AbilitatoUn interruttore per controllare se il modello è referente o meno

### Miniatura  {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

(Facoltativo) Selezionate l’icona Carica immagine per visualizzare una miniatura con il nome e la descrizione per gli autori dei siti della community.

### Struttura {#structure}

![chlimage_1-21](assets/chlimage_1-21.png)

Per aggiungere funzioni per la community, trascinate dal lato destro a sinistra nell&#39;ordine in cui dovrebbero essere visualizzati i collegamenti del menu del sito. Gli stili verranno applicati al modello durante la creazione del sito.

Ad esempio, se desiderate una pagina principale, trascinate la funzione Pagina dalla libreria e rilasciatela sotto il generatore di modelli. Viene visualizzata la finestra di dialogo di configurazione della pagina. Per informazioni sulle finestre di dialogo di configurazione, vedere la [console delle funzioni](functions.md).

Trascinate e rilasciate tutte le altre funzioni della community desiderate per un sito community basato su questo modello.

La funzione page fornisce una pagina vuota. La funzione Groups (Gruppi) consente di creare un sito di gruppo (sub-community) all&#39;interno del sito community.

>[!CAUTION]
>
>La funzione dei gruppi deve *not* essere la *prima e la funzione unica* nella struttura del sito.
>
>Qualsiasi altra funzione, come la funzione [page](functions.md#page-function), deve essere inclusa ed elencata per prima.

![chlimage_1-22](assets/chlimage_1-22.png)

### Modelli di gruppo per la funzione dei gruppi {#group-templates-for-groups-function}

Quando si inserisce una funzione di gruppo nel modello di sito, la configurazione richiede la specifica delle scelte di modelli di gruppo consentite quando viene creato un nuovo gruppo nell&#39;ambiente di pubblicazione.

>[!CAUTION]
>
>La funzione Groups deve *not* essere la *prima e la sola funzione* nella struttura del sito.

![chlimage_1-23](assets/chlimage_1-23.png)

Selezionando due o più modelli di gruppo community, l&#39;amministratore del gruppo può scegliere se creare effettivamente un nuovo gruppo nella community.

![chlimage_1-24](assets/chlimage_1-24.png)

## Modifica modello sito{#edit-site-template}

Quando si visualizzano i modelli di sito nella [console principale dei modelli di sito](#site-templates-console), è possibile selezionare un modello di sito esistente da modificare.

Questo processo fornisce gli stessi pannelli di [creazione di un modello di sito](#create-site-template).
