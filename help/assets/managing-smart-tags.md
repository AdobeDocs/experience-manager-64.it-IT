---
title: Gestire tag avanzati
description: Aggiornare o rimuovere gli smart tag inesatti per migliorare la pertinenza dei tag
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: User
exl-id: 05f43e43-ac72-4ab1-a373-687c137d2bed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 4%

---

# Gestione dei tag avanzati {#managing-smart-tags}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi curare i tag avanzati per rimuovere eventuali tag non accurati assegnati alle immagini del tuo marchio, in modo da visualizzare solo i tag più rilevanti.

La moderazione degli smart tag consente inoltre di perfezionare le ricerche basate sui tag per le immagini, garantendo che l’immagine venga visualizzata nei risultati della ricerca per i tag più rilevanti. In sostanza, aiuta ad eliminare le possibilità che immagini non collegate vengano visualizzate nei risultati di ricerca.

Puoi anche assegnare un rango più alto a un tag per aumentarne la pertinenza rispetto a un’immagine. La promozione di un tag per un’immagine aumenta le possibilità che l’immagine appaia nei risultati della ricerca quando viene eseguita una ricerca in base al tag specifico.

1. Nella casella OmniSearch, cerca le risorse in base a un tag.
1. Inspect i risultati della ricerca per identificare un’immagine che non è pertinente alla ricerca.
1. Seleziona l’immagine, quindi tocca o fai clic sul pulsante **[!UICONTROL Gestire i tag]** dalla barra degli strumenti.
1. Da **[!UICONTROL Gestire i tag]** , controllare i tag. Se non desideri che la ricerca dell’immagine sia basata su un tag specifico, selezionalo e tocca o fai clic sul tag **[!UICONTROL Elimina]** dalla barra degli strumenti. In alternativa, tocca o fai clic su (**[!UICONTROL X]**) accanto all’etichetta.
1. Per assegnare un rango più alto a un tag, selezionalo e tocca o fai clic sul tag **[!UICONTROL Promuovi]** dalla barra degli strumenti. Il tag promosso viene spostato in **[!UICONTROL Tag]** sezione .
1. Tocca o fai clic su **[!UICONTROL Salva]**, quindi su **[!UICONTROL OK]** per chiudere la finestra di dialogo Corretto.
1. Passa alla pagina delle proprietà dell’immagine. Osserva che al tag promosso è assegnata un’elevata rilevanza e, quindi, appare più alta nei risultati della ricerca.

## Comprendere [!DNL Experience Manager] risultati di ricerca con tag avanzati {#understand-search-results-with-smart-tags}

Per impostazione predefinita, [!DNL Experience Manager] la ricerca combina i termini di ricerca con un `AND` clausola . L’utilizzo di smart tag non modifica questo comportamento predefinito. L’utilizzo di tag avanzati aggiunge un’ulteriore `OR` per trovare uno dei termini di ricerca negli smart tag di applica. Ad esempio, considera la ricerca `woman running`. Risorse con `woman` o semplicemente `running` nei metadati non vengono visualizzate nei risultati della ricerca per impostazione predefinita. Tuttavia, una risorsa è taggata con `woman` o `running` l’utilizzo di smart tag viene visualizzato in una query di ricerca di questo tipo. Quindi i risultati della ricerca sono una combinazione di:

* risorse con entrambe le parole chiave, `woman` e `running` nei metadati.
* risorse con tag avanzati con una delle parole chiave.

I risultati della ricerca che corrispondono a tutti i termini di ricerca nei campi di metadati vengono visualizzati per primi, seguiti dai risultati della ricerca che corrispondono a qualsiasi termine di ricerca negli smart tag. Nell’esempio precedente, l’ordine approssimativo di visualizzazione dei risultati della ricerca è:

1. corrispondenze di `woman running` nei vari campi di metadati.
1. corrispondenze di `woman running` in smart tag.
1. corrispondenze di `woman` o `running` in smart tag.
