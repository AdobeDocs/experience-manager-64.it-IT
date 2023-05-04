---
title: Tendenze delle attività
seo-title: Activity Trends
description: Aggiunta di un componente Elenco attività della community a una pagina
seo-description: Adding a Community Activity List component to a page
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 7%

---

# Tendenze delle attività {#activity-trends}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La `Community Activity List` Il componente consente di aggiungere informazioni di tendenza relative a post e visualizzazioni per membri, nonché a post e visualizzazioni di contenuto.

Questa sezione della documentazione descrive

* Aggiunta di `Community Activity List` a un [sito della community](overview.md#community-sites)

* Impostazioni di configurazione per `Community Activity List` component

## Requisito {#requirement}

Dati per `Community Activity List` è disponibile solo quando Adobe Analytics è concesso in licenza e configurato per il sito della community.

Vedi [Funzionalità di configurazione di Analytics for Communities](analytics.md).

## Aggiunta di un elenco di attività della community a una pagina {#adding-a-community-activity-list-to-a-page}

Per aggiungere una `Community Activity List` in una pagina in modalità di authoring, individua il componente `Communities / Community Activity List` e trascinarlo nella posizione desiderata su una pagina.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando viene posizionato per la prima volta su una pagina di un sito della community, viene visualizzato questo componente:

![chlimage_1-227](assets/chlimage_1-227.png)

## Configurazione dell’elenco delle attività della community  {#configuring-community-activity-list}

Seleziona il `Community Activity List` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-228](assets/chlimage_1-228.png)

Sotto la **[!UICONTROL Commenti]** scheda , specifica se e come vengono visualizzati i commenti per i file caricati:

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Tipo]**

   Specifica se visualizzare i dati relativi ai membri della community o al contenuto generato dall’utente (UGC).

   Seleziona da
   * `Members`
   * `Content`

   Il valore predefinito è `Members`.

* **[!UICONTROL Titolo da visualizzare]**

   Titolo descrittivo da visualizzare sopra i dati, ad esempio `Trending Content`.

   Il valore predefinito non è un titolo.

* **[!UICONTROL Numero di visualizzazioni]**

   Numero di elementi da elencare.

   Il valore predefinito è 10.

* **[!UICONTROL Tipo di attività]**

   Seleziona uno dei
   * `Views`(visite alle pagine)
   * `Posts`(creazione di UGC)
   * `Follows`
   * `Likes`

   Il valore predefinito è Visualizzazioni.

* **[!UICONTROL Periodo di tempo]**

   Seleziona uno dei
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   Il valore predefinito è `Total`.

* **[!UICONTROL Percorso contesto]**

   Consente di estendere l’ambito dell’attività a un sottoinsieme del sito, ad esempio a un Blog specifico.

   L&#39;impostazione predefinita è l&#39;intero sito della community.

* **[!UICONTROL Aggregazione conteggio dei membri]**

   Se questa opzione è deselezionata (disattivata), vengono conteggiati solo i post di primo livello. Ad esempio, se il contesto è la pagina principale (l’impostazione predefinita), un `Activity Type`di `Posts`non mostrerà mai alcuna attività in quanto non è possibile pubblicare contenuto nella pagina principale. Quando questa opzione è selezionata, vengono inclusi i conteggi di tutte le pagine discendenti.

   Il valore predefinito è selezionato.

## Pagina di esempio con 4 componenti {#example-page-with-components}

**Visitatori principali** config: Tipo = Membri, Tipo di attività = Viste

**Collaboratori principali** config: Tipo = Membri, Tipo di attività = Posti

**Contenuto principale** config: Tipo = Contenuto, tipo di attività = Viste,

**Contenuto di tendenza** config: Tipo = Contenuto, tipo di attività = Posts

![chlimage_1-230](assets/chlimage_1-230.png)
