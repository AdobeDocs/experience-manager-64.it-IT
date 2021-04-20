---
title: Gestire tag avanzati
description: Aggiornare o rimuovere gli smart tag inesatti per migliorare la pertinenza dei tag
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 3%

---


# Gestione dei tag avanzati {#managing-smart-tags}

Puoi curare i tag avanzati per rimuovere eventuali tag non accurati assegnati alle immagini del tuo marchio, in modo da visualizzare solo i tag più rilevanti.

La moderazione degli smart tag consente inoltre di perfezionare le ricerche basate sui tag per le immagini, garantendo che l’immagine venga visualizzata nei risultati della ricerca per i tag più rilevanti. In sostanza, aiuta ad eliminare le possibilità che immagini non collegate vengano visualizzate nei risultati di ricerca.

Puoi anche assegnare un rango più alto a un tag per aumentarne la pertinenza rispetto a un’immagine. La promozione di un tag per un’immagine aumenta le possibilità che l’immagine appaia nei risultati della ricerca quando viene eseguita una ricerca in base al tag specifico.

1. Nella casella OmniSearch, cerca le risorse in base a un tag.
1. Inspect i risultati della ricerca per identificare un’immagine che non è pertinente alla ricerca.
1. Seleziona l’immagine, quindi tocca o fai clic sull’icona **[!UICONTROL Gestisci tag]** nella barra degli strumenti.
1. Dalla pagina **[!UICONTROL Gestione tag]** , controlla i tag . Se non desideri che la ricerca dell’immagine sia basata su un tag specifico, selezionalo e tocca o fai clic sull’icona **[!UICONTROL Elimina]** nella barra degli strumenti. In alternativa, tocca o fai clic sul simbolo (**[!UICONTROL X]**) visualizzato accanto all’etichetta.
1. Per assegnare un rango più alto a un tag, selezionalo e tocca o fai clic sull’icona **[!UICONTROL Promuovi]** nella barra degli strumenti. Il tag promosso viene spostato nella sezione **[!UICONTROL Tag]** .
1. Tocca o fai clic su **[!UICONTROL Salva]**, quindi su **[!UICONTROL OK]** per chiudere la finestra di dialogo Corretto.
1. Passa alla pagina delle proprietà dell’immagine. Osserva che al tag promosso è assegnata un’elevata rilevanza e, quindi, appare più alta nei risultati della ricerca.

## Comprendere AEM risultati della ricerca con tag avanzati {#understand-search-results-with-smart-tags}

Per impostazione predefinita, AEM ricerca combina i termini di ricerca con una clausola `AND`. L’utilizzo di smart tag non modifica questo comportamento predefinito. L’utilizzo di tag avanzati aggiunge una clausola `OR` aggiuntiva per trovare uno dei termini di ricerca nei tag avanzati applicati. Ad esempio, è consigliabile cercare `woman running`. Le risorse con una semplice `woman` o una semplice `running` parola chiave nei metadati non vengono visualizzate nei risultati di ricerca per impostazione predefinita. Tuttavia, una risorsa con tag `woman` o `running` utilizzando tag avanzati viene visualizzata in una query di ricerca di questo tipo. Quindi i risultati della ricerca sono una combinazione di:

* risorse con entrambe le parole chiave, `woman` e `running` nei metadati.
* risorse con tag avanzati con una delle parole chiave.

I risultati della ricerca che corrispondono a tutti i termini di ricerca nei campi di metadati vengono visualizzati per primi, seguiti dai risultati della ricerca che corrispondono a qualsiasi termine di ricerca negli smart tag. Nell’esempio precedente, l’ordine approssimativo di visualizzazione dei risultati della ricerca è:

1. corrisponde a `woman running` nei vari campi di metadati.
1. corrispondenze di `woman running` negli smart tag.
1. corrispondenze di `woman` o di `running` negli smart tag.
