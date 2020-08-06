---
title: Gestire gli smart tag
description: Aggiornare o rimuovere gli smart tag non accurati per migliorare la pertinenza dei tag
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
translation-type: tm+mt
source-git-commit: 7771cbb218d80247f65e92cbe7e8cdfd9720b75e
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 2%

---


# Gestione dei tag avanzati {#managing-smart-tags}

Potete curare i tag avanzati per rimuovere eventuali tag non accurati eventualmente assegnati alle immagini del vostro marchio, in modo da visualizzare solo i tag più rilevanti.

La moderazione degli smart tag consente inoltre di perfezionare le ricerche basate sui tag per le immagini, assicurando che l’immagine venga visualizzata nei risultati di ricerca per i tag più rilevanti. In sostanza, elimina la possibilità che immagini non collegate vengano visualizzate nei risultati della ricerca.

Potete anche assegnare un rango più alto a un tag per aumentarne la rilevanza rispetto a un’immagine. La promozione di un tag per un’immagine aumenta le probabilità che l’immagine venga visualizzata nei risultati di ricerca quando viene eseguita una ricerca in base al tag specifico.

1. Nella casella di ricerca Omni, cercate le risorse in base a un tag.
1.  Inspect i risultati della ricerca per identificare un’immagine che non si trova rilevante ai fini della ricerca.
1. Selezionate l’immagine, quindi toccate o fate clic sull’icona **[!UICONTROL Gestisci tag]** nella barra degli strumenti.
1. Dalla pagina **[!UICONTROL Gestisci tag]** , ispezionate i tag. Se non desiderate che l’immagine venga cercata in base a un tag specifico, selezionate il tag e toccate o fate clic sull’icona **[!UICONTROL Elimina]** dalla barra degli strumenti. In alternativa, tocca o fai clic sul simbolo (**[!UICONTROL X]**) visualizzato accanto all’etichetta.
1. Per assegnare un rango più alto a un tag, selezionatelo e toccate o fate clic sull’icona **[!UICONTROL Promuovi]** dalla barra degli strumenti. Il tag promosso viene spostato nella sezione **[!UICONTROL Tag]** .
1. Tocca o fai clic su **[!UICONTROL Salva]**, quindi su **[!UICONTROL OK]** per chiudere la finestra di dialogo Corretto.
1. Passate alla pagina delle proprietà dell’immagine. Osservate che al tag promosso è stata assegnata un’elevata rilevanza e, di conseguenza, appare più alta nei risultati della ricerca.

## Comprendere AEM risultati di ricerca con gli smart tag {#understand-search-results-with-smart-tags}

Per impostazione predefinita, AEM ricerca combina i termini di ricerca con una `AND` clausola. L&#39;utilizzo di smart tag non modifica questo comportamento predefinito. L&#39;utilizzo di smart tag aggiunge una `OR` clausola aggiuntiva per individuare qualsiasi termine di ricerca negli smart tag applicati. For example, consider searching for `woman running`. Per impostazione predefinita, le risorse con una sola parola chiave `woman` o una sola `running` parola chiave nei metadati non vengono visualizzate nei risultati della ricerca. Tuttavia, in una query di ricerca di questo tipo viene visualizzata una risorsa con `woman` o `running` tramite smart tag. Quindi i risultati della ricerca sono una combinazione di:

* risorse con entrambe le parole chiave `woman` e `running` nei metadati.
* assets smart tag con una delle parole chiave.

I risultati della ricerca che corrispondono a tutti i termini di ricerca nei campi di metadati vengono visualizzati per primi, seguiti dai risultati della ricerca che corrispondono a uno qualsiasi dei termini di ricerca negli smart tag. Nell&#39;esempio precedente, l&#39;ordine approssimativo di visualizzazione dei risultati della ricerca è:

1. corrispondenze di `woman running` nei vari campi di metadati.
1. corrispondenze di `woman running` in smart tag.
1. corrispondenze di `woman` o di `running` in smart tag.
