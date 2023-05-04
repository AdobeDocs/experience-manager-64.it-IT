---
title: Modelli per siti
seo-title: Site Templates
description: Come accedere alla console Modelli di sito
seo-description: How to access the Site Templates console
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
role: Admin
exl-id: 5049c5df-c874-4c34-a96b-7944cd0353d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 5%

---

# Modelli per siti {#site-templates}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La console Modelli per sito è molto simile alla [Modelli per gruppi](tools-groups.md) console, incentrata sulle funzioni di interesse per i gruppi comunitari.

>[!NOTE]
>
>Le console per la creazione di [siti della community](sites-console.md), [modelli di sito community](sites.md), [modelli di gruppo community](tools-groups.md) e [funzioni della community](functions.md) sono utilizzabili solo nell’ambiente di authoring.

## Console Modelli per siti {#site-templates-console}

Nell’ambiente di authoring, è possibile accedere alla console dei siti della community

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Modelli di sito]**

In questa console vengono visualizzati i modelli da cui viene [sito della community](sites-console.md) può essere creato e consente di creare nuovi modelli di sito.

![chlimage_1-18](assets/chlimage_1-18.png)

## Crea modello sito {#create-site-template}

Per iniziare a creare un nuovo modello di sito, seleziona `Create`.

Viene visualizzato il pannello Editor sito che contiene 3 pannelli secondari:

### Informazioni di base {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

Nel pannello Informazioni di base sono configurati un nome, una descrizione e se il modello è abilitato o disabilitato:

* **[!UICONTROL Nome del modello del sito community]**
ID del nome del modello

* **[!UICONTROL Descrizione del modello del sito community]**
Descrizione del modello

* **[!UICONTROL Disabilitato/Abilitato]**
Un interruttore di attivazione che controlla se il modello è referenziabile

### Miniatura  {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

(Facoltativo) Seleziona l’icona Carica immagine per visualizzare una miniatura insieme al nome e alla descrizione per i creatori dei siti della community.

### Struttura {#structure}

![chlimage_1-21](assets/chlimage_1-21.png)

Per aggiungere funzioni di community, trascina da destra a sinistra nell’ordine in cui dovrebbero essere visualizzati i collegamenti al menu del sito. Gli stili verranno applicati al modello durante la creazione del sito.

Ad esempio, se desideri una home page, trascina la funzione Pagina dalla libreria e rilascia sotto il generatore di modelli. In questo modo si aprirà la finestra di dialogo di configurazione della pagina. Consulta la sezione [console funzioni](functions.md) per informazioni sulle finestre di dialogo di configurazione.

Continua a trascinare e rilasciare tutte le altre funzioni della community desiderate per un sito community basato su questo modello.

La funzione page fornisce una pagina vuota. La funzione gruppi consente di creare un sito del gruppo (sottocommunity) all’interno del sito della community.

>[!CAUTION]
>
>La funzione gruppi deve *not* essere *primo né unico* nella struttura del sito.
>
>Qualsiasi altra funzione, ad esempio [funzione pagina](functions.md#page-function), deve essere incluso ed elencato per primo.

![chlimage_1-22](assets/chlimage_1-22.png)

### Funzione Group Templates for Groups (Modelli di gruppo per gruppi) {#group-templates-for-groups-function}

Quando si include una funzione di gruppi nel modello di sito, la configurazione richiede la specifica delle scelte di modelli di gruppo consentite quando si crea un nuovo gruppo nell&#39;ambiente di pubblicazione.

>[!CAUTION]
>
>La funzione Groups deve *not* essere *primo né unico* nella struttura del sito.

![chlimage_1-23](assets/chlimage_1-23.png)

Selezionando due o più modelli di gruppo community, l’amministratore del gruppo può scegliere se creare effettivamente un nuovo gruppo nella community.

![chlimage_1-24](assets/chlimage_1-24.png)

## Modifica modello sito {#edit-site-template}

Quando si visualizzano i modelli di sito nella pagina principale [Console Modelli per siti](#site-templates-console), è possibile selezionare un modello di sito esistente da modificare.

Questo processo fornisce gli stessi pannelli di [creazione di un modello di sito](#create-site-template).
