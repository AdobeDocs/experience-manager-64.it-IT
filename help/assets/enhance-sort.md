---
title: Ordinamento migliorato delle risorse in AEM
description: Scopri come  [!DNL Experience Manager] Assets distribuisce l’ordinamento lato server per ordinare le risorse delle cartelle o una query di ricerca contemporaneamente, anziché ordinarle in batch sul lato client.
contentOwner: AG
feature: Search
role: User
exl-id: aa24ca68-d94e-4bd4-a5cc-113906650a2e
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 5%

---

# Ordinamento migliorato delle risorse in [!DNL Experience Manager] {#enhanced-sorting-of-assets-in-aem}

Scopri in che modo [!DNL Experience Manager] Assets implementa l’ordinamento lato server per ordinare le risorse delle cartelle o una query di ricerca contemporaneamente, anziché ordinarle in batch sul lato client.

La funzionalità di ricerca di Adobe Experience Manager Assets è stata migliorata per ordinare in modo efficiente un gran numero di risorse nelle pagine di elenco cartelle e di risultati di ricerca. Puoi anche ordinare le voci della timeline.

[!DNL Experience Manager] Le risorse distribuiscono l’ordinamento lato server per ordinare l’intero set di risorse (indipendentemente dalle dimensioni) all’interno di una cartella o di una query di ricerca contemporaneamente, anziché ordinarle in batch sul lato client. In questo modo, i risultati prerecuperati possono essere visualizzati rapidamente sull’interfaccia utente, il che rende l’operazione di ordinamento più reattiva e più chiara.

## Ordinamento delle risorse nella vista Elenco {#sorting-assets-in-list-view}

[!DNL Experience Manager] Assets consente di ordinare le risorse delle cartelle in base ai campi seguenti:

* Paese
* Stato
* Tipo
* Dimensione
* Valutazione
* Data di modifica
* Data di pubblicazione
* Utilizzo
* Clic
* Impression
* Ritirato

1. Passa a una cartella contenente un numero elevato di risorse.
1. Tocca o fai clic sull’icona Layout e passa alla vista a elenco.

   ![chlimage_1-394](assets/chlimage_1-394.png)

1. Tocca o fai clic sull’icona Ordina accanto all’intestazione di una colonna nell’elenco delle risorse.

   ![chlimage_1-395](assets/chlimage_1-395.png)

   L’elenco delle risorse viene ordinato in base ai valori dei campi.

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>Per ordinare i valori nelle colonne `Name` o `Title`, sovrapponi `/libs/dam/gui/content/commons/availablecolumns` e modifica il valore di `sortable` in `True`.

## Ordinamento delle risorse nei risultati della ricerca {#sorting-assets-in-search-results}

Puoi ordinare i risultati della ricerca in base ai campi seguenti:

* Titolo
* Stato
* Tipo
* Dimensione
* Data di modifica
* Data di pubblicazione

1. Dalla casella OmniSearch, cerca le risorse in base ai criteri desiderati.

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. Tocca o fai clic sull’icona Layout e passa alla vista a elenco. Se i risultati della ricerca sono già visualizzati nella vista a elenco, salta questo passaggio.
1. Tocca o fai clic sull’icona Ordina accanto all’intestazione di una colonna nell’elenco delle risorse. L’elenco delle risorse viene ordinato in base ai valori dei campi.

   ![chlimage_1-398](assets/chlimage_1-398.png)

## Ordinamento delle risorse nella timeline {#sorting-assets-in-timeline}

[!DNL Assets] consente di ordinare in modo cronologico le voci della timeline, ad esempio annotazioni, versioni, flussi di lavoro e attività.

1. Dall’interfaccia utente Assets, seleziona una risorsa per la quale vuoi visualizzare la timeline.
1. Tocca o fai clic sull&#39;icona di navigazione globale e seleziona **[!UICONTROL Timeline]**.

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. Nella timeline, seleziona una voce dall’elenco. Ad esempio, seleziona **[!UICONTROL Commenti]** per visualizzare l’elenco delle annotazioni associate alla risorsa.

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. Tocca o fai clic sull&#39;icona **[!UICONTROL Ordina]** accanto all&#39;etichetta **[!UICONTROL Data]**. In base alla selezione, le annotazioni sono elencate nell’ordine cronologico/inverso in cui sono state aggiunte alla risorsa.

   ![chlimage_1-401](assets/chlimage_1-401.png)
