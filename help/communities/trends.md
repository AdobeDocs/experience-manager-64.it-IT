---
title: Tendenze attività
seo-title: Tendenze attività
description: Aggiunta di un componente Elenco attività community a una pagina
seo-description: Aggiunta di un componente Elenco attività community a una pagina
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 5%

---


# Tendenze attività {#activity-trends}

## Introduzione {#introduction}

Il `Community Activity List` componente consente di aggiungere informazioni di tendenza relative ai post e alle viste dei membri, nonché ai post e alle viste dei contenuti.

Questa sezione della documentazione descrive

* Aggiunta del `Community Activity List` componente a un sito [community](overview.md#community-sites)

* Impostazioni di configurazione per il `Community Activity List` componente

## Requisito {#requirement}

I dati per il sito `Community Activity List` sono disponibili solo se  Adobe Analytics è concesso in licenza e configurato per il sito della community.

Consultate Configurazione [di Analytics per le funzioni](analytics.md)Community.

## Aggiunta di un elenco di attività community a una pagina {#adding-a-community-activity-list-to-a-page}

Per aggiungere un `Community Activity List` componente a una pagina in modalità di creazione, individuate il componente `Communities / Community Activity List` e trascinatelo nella posizione desiderata sulla pagina.

Per le informazioni necessarie, consulta [Community Components Basics](basics.md).

La prima volta che il componente viene inserito in una pagina di un sito community, viene visualizzato così:

![chlimage_1-227](assets/chlimage_1-227.png)

## Configurazione dell&#39;elenco delle attività community  {#configuring-community-activity-list}

Selezionate il `Community Activity List` componente inserito a cui accedere e selezionate l’ `Configure` icona che apre la finestra di dialogo di modifica.

![chlimage_1-228](assets/chlimage_1-228.png)

Nella scheda **[!UICONTROL Commenti]** , specificate se e come vengono visualizzati i commenti per i file caricati:

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL Tipo]**

   Specificate se visualizzare i dati relativi ai membri della community o al contenuto generato dall&#39;utente (UGC).

   Seleziona da
   * `Members`
   * `Content`

   Default is `Members`.

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

   Default is `Total`.

* **[!UICONTROL Percorso contesto]**

   Fornisce la possibilità di estendere l&#39;attività a un sottoinsieme del sito, ad esempio un Blog specifico.

   Default è l&#39;intero sito della community.

* **[!UICONTROL Aggregazione conteggio dei membri]**

   Se questa opzione è deselezionata (disattivata), vengono contati solo i post di livello principale. Ad esempio, se il contesto è la pagina principale (impostazione predefinita), una `Activity Type`di non `Posts`mostrerà mai alcuna attività in quanto non è possibile pubblicare contenuto nella pagina principale. Se questa opzione è selezionata, vengono inclusi i conteggi di tutte le pagine discendenti.

   Il valore predefinito è selezionato.

## Pagina di esempio con 4 componenti {#example-page-with-components}

**Configurazione visitatori** principali: Tipo = Membri, Tipo di attività = Viste

**Configurazione collaboratori** principali: Tipo = Membri, Tipo di attività = Post

**Configurazione contenuto** principale: Tipo = Contenuto, Tipo di attività = Viste,

**Configurazione dei contenuti** di tendenza: Tipo = Contenuto, Tipo di attività = Post

![chlimage_1-230](assets/chlimage_1-230.png)
