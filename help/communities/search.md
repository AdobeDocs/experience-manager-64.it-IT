---
title: Funzione di ricerca
seo-title: Funzione di ricerca
description: Aggiunta e configurazione della ricerca a un sito community
seo-description: Aggiunta e configurazione della ricerca a un sito community
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
translation-type: tm+mt
source-git-commit: a6d50dbcbfec85d21072d51a5fa48e3667835f06
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 2%

---


# Funzione di ricerca {#search-feature}

La funzione di ricerca funziona con altre funzioni, come i forum, per consentire la ricerca di contenuti.

Quando si aggiunge la possibilità di cercare post inseriti dai membri della community, denominati contenuti generati dall&#39;utente (UGC), sono disponibili due componenti: [ `Search`](#search-features) e [ `Search Results`](#search-results).

La pagina che include il componente `Search Results` supporta sia la ricerca che la visualizzazione dei risultati.

La pagina che include il componente `Search`fornisce una posizione in cui avviare una ricerca con i risultati visualizzati sulla pagina `Search Results`.

La funzione di ricerca può essere utilizzata con qualsiasi altra funzione che consente ai visitatori e ai membri del sito di visualizzare il contenuto.

## Ricerca {#search-features}

### Aggiungi ricerca a una pagina {#add-search-to-a-page}

Per aggiungere un componente `Search` a una pagina in modalità di creazione, usate il browser componenti per individuare `Communities / Search` e trascinarlo nella posizione desiderata su una pagina. L&#39;utilizzo di `Search` richiede una seconda pagina per `Search Results.`

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando la libreria sul lato client richiesta, `cq.social.hbs.search`, è inclusa, viene visualizzato il componente `Search`.

![chlimage_1-373](assets/chlimage_1-373.png)

### Configurare la ricerca aggiunta {#configure-the-added-search}

Selezionare il componente `Search` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-374](assets/chlimage_1-374.png)

Nella scheda **[!UICONTROL Impostazioni di ricerca]**, specificare i percorsi di ricerca che devono essere seguiti quando un visitatore inserisce una query.

![chlimage_1-375](assets/chlimage_1-375.png)

* **[!UICONTROL Percorsi]**
di ricercaAggiungendo percorsi di ricerca mediante il pulsante Aggiungi elemento, la ricerca nel contenuto è limitata. Ad esempio, per limitare la ricerca a un forum specifico, selezionate un componente forum all’interno di una pagina:

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL Pagina]**
risultati: i risultati verranno visualizzati su una pagina separata specificata dal browser per selezionare una pagina contenente il 
`Search Results` componente.

## Risultati di ricerca {#search-results}

### Aggiungi risultati di ricerca a una pagina {#add-search-results-to-a-page}

Per aggiungere un componente `Search Results` a una pagina in modalità di creazione, usate il browser componenti per individuare

* `Communities / Search Results`

e trascinarlo nella posizione desiderata su una pagina. A differenza del componente Ricerca, non è necessaria una seconda pagina, in quanto i risultati verranno visualizzati sulla stessa pagina.

Se si utilizza Cerca in un altro sito Web, questa pagina con `Search Results` può essere configurata come `Result Page` per una o tutte le istanze di `Search`.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando la libreria sul lato client richiesta, `cq.social.hbs.search`, è inclusa, viene visualizzato il componente `Search Result`:

![chlimage_1-376](assets/chlimage_1-376.png)

### Configurare il risultato di ricerca aggiunto {#configure-the-added-search-result}

Selezionare il componente `Search Results` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-377](assets/chlimage_1-377.png)

Nella scheda **[!UICONTROL Impostazioni risultati di ricerca]** è possibile specificare quali percorsi includere nella ricerca quando una query viene inserita da un visitatore.

![chlimage_1-378](assets/chlimage_1-378.png)

* **[!UICONTROL Risultati ricerca per]**
pagina: consente di definire il numero di topic/post mostrati per pagina. Il valore predefinito è 10.

* **[!UICONTROL Percorsi]**
di ricercaAggiungendo percorsi di ricerca mediante il pulsante Aggiungi elemento, la ricerca nel contenuto è limitata.

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Search Essentials](search-implementation.md) per gli sviluppatori.
