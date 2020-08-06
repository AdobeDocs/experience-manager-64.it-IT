---
title: Ordinamento migliorato delle risorse in AEM
description: Scoprite come  AEM Assets distribuisce l’ordinamento lato server per ordinare le risorse delle cartelle o una query di ricerca immediatamente anziché ordinarle in batch sul lato client.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 4%

---


# Ordinamento migliorato delle risorse in AEM {#enhanced-sorting-of-assets-in-aem}

Scoprite come  AEM Assets distribuisce l’ordinamento lato server per ordinare le risorse delle cartelle o una query di ricerca immediatamente anziché ordinarle in batch sul lato client.

La funzione di ricerca di Risorse Adobe Experience Manager (AEM) è stata migliorata per ordinare in modo efficiente un gran numero di risorse nelle pagine di elenco delle cartelle e di risultati della ricerca. Potete anche ordinare le voci della cronologia.

 AEM Assets distribuisce l’ordinamento lato server per ordinare l’intero set di risorse (indipendentemente dalle dimensioni) all’interno di una cartella o di una query di ricerca contemporaneamente, anziché ordinarle in batch sul lato client. In questo modo, i risultati pregenerati possono essere visualizzati rapidamente sull&#39;interfaccia utente, il che rende l&#39;operazione di ordinamento più reattiva e semplice.

## Ordinamento delle risorse nella visualizzazione Elenco {#sorting-assets-in-list-view}

 AEM Assets consente di ordinare le risorse delle cartelle in base ai seguenti campi:

* Paese
* Stato
* Tipo
* Dimensione
* Valutazione
* Data modifica
* Data di pubblicazione
* Utilizzo
* Clic
* Impression
* Ritirato

1. Individuate una cartella contenente un numero elevato di risorse.
1. Tocca o fai clic sull’icona Layout e passa alla vista a elenco.

   ![chlimage_1-394](assets/chlimage_1-394.png)

1. Toccate o fate clic sull’icona Ordina accanto all’intestazione di una colonna nell’elenco delle risorse.

   ![chlimage_1-395](assets/chlimage_1-395.png)

   L&#39;elenco delle risorse è ordinato in base ai valori dei campi.

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>Per ordinare i valori nelle `Name` colonne o nelle `Title`colonne, sovrapponete `/libs/dam/gui/content/commons/availablecolumns` e modificate il valore di `sortable` in `True`.

## Ordinamento delle risorse nei risultati della ricerca {#sorting-assets-in-search-results}

Potete ordinare i risultati della ricerca in base ai seguenti campi:

* Titolo
* Stato
* Tipo
* Dimensione
* Data modifica
* Data di pubblicazione

1. Dalla casella di ricerca Omni, cercate le risorse in base ai criteri desiderati.

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. Tocca o fai clic sull’icona Layout e passa alla vista a elenco. Se i risultati della ricerca sono già visualizzati nella vista a elenco, ignorate questo passaggio.
1. Toccate o fate clic sull’icona Ordina accanto all’intestazione di una colonna nell’elenco delle risorse. L&#39;elenco delle risorse è ordinato in base ai valori dei campi.

   ![chlimage_1-398](assets/chlimage_1-398.png)

## Ordinamento delle risorse nella timeline {#sorting-assets-in-timeline}

 AEM Assets consente di ordinare cronologicamente le voci della cronologia, come annotazioni, versioni, flussi di lavoro e attività.

1. Nell’interfaccia utente Risorse, seleziona una risorsa per la quale vuoi visualizzare la timeline.
1. Tocca o fai clic sull&#39;icona Navigazione globale e seleziona **[!UICONTROL Timeline]**.

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. Nella timeline, selezionate una voce dall’elenco. Ad esempio, selezionate **[!UICONTROL Commenti]** per visualizzare l’elenco delle annotazioni associate alla risorsa.

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. Tocca o fai clic sull’icona **[!UICONTROL Ordina]** accanto all’etichetta **[!UICONTROL Data]** . In base alla selezione, le annotazioni sono elencate in ordine cronologico/inverso in cui sono state aggiunte alla risorsa.

   ![chlimage_1-401](assets/chlimage_1-401.png)

