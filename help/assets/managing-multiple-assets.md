---
title: Modifica in blocco dei metadati di più risorse e raccolte
description: Scopri come modificare contemporaneamente i metadati di più risorse e raccolte per diffondere rapidamente le comuni modifiche ai metadati.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 184aa0a7fcd3f89510295ddaff28624b8306b7d2
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 13%

---


# Gestire più risorse e raccolte {#managing-multiple-assets-and-collections}

Scopri come modificare contemporaneamente i metadati di più risorse e raccolte per diffondere rapidamente le modifiche comuni ai metadati.

Adobe Enterprise Manager (AEM) Assets consente di modificare contemporaneamente i metadati di più risorse, in modo da poter rapidamente propagare le modifiche comuni ai metadati delle risorse in blocco. Puoi anche modificare i metadati per più raccolte in blocco.

Utilizza la pagina delle proprietà per eseguire modifiche ai metadati su più risorse o raccolte:

* Cambiare le proprietà dei metadati in un valore comune
* Aggiungere o modificare i tag

Per personalizzare la pagina delle proprietà dei metadati, tra cui l’aggiunta, la modifica, l’eliminazione delle proprietà dei metadati, utilizza l’editor schema.

>[!NOTE]
>
>I metodi di modifica collettiva funzionano per le risorse disponibili in una cartella o in una raccolta. Per le risorse disponibili nelle cartelle o che corrispondono a un criterio comune, è possibile aggiornare i metadati in blocco dai risultati della ricerca delle risorse.

## Modificare le proprietà dei metadati di più risorse {#editing-metadata-properties-of-multiple-assets}

1. Nell’interfaccia utente di Assets, individua il percorso delle risorse da modificare.
1. Seleziona le risorse per le quali desideri modificare le proprietà comuni.
1. Dalla barra degli strumenti, fai clic su **[!UICONTROL Proprietà]** per aprire la pagina delle proprietà per le risorse selezionate.
1. Modifica le proprietà dei metadati per le risorse selezionate nelle varie schede.
1. Per visualizzare i metadati di una risorsa specifica, annulla la selezione delle risorse rimanenti nell’elenco. Se annulli la selezione di alcune risorse nella pagina [!UICONTROL Proprietà], i metadati di tali risorse non vengono aggiornati.
1. Per selezionare uno schema di metadati diverso per le risorse, fai clic su **[!UICONTROL Impostazioni]** nella barra degli strumenti e seleziona uno schema. Fai clic su **[!UICONTROL Salva e chiudi]**.
1. Per aggiungere i nuovi metadati a quelli esistenti nei campi che contengono più valori, seleziona **[!UICONTROL Modalità di aggiunta]**. Se non selezioni questa opzione, i nuovi metadati sostituiranno quelli già esistenti nei campi. Fare clic su **[!UICONTROL Invia]**.

![Applicazione in blocco dello schema metadati a più risorse](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>Per i campi con valore singolo, i nuovi metadati non vengono aggiunti al valore esistente nel campo, nemmeno se selezioni **[!UICONTROL Modalità di aggiunta]**.

## Configura il limite per l&#39;aggiornamento in massa dei metadati {#configure-limit-for-bulk-metadata-update}

Per evitare situazioni simili a DOS, AEM limita il numero di parametri supportati in una richiesta Sling. Quando aggiorni i metadati di molte risorse in una sola volta, potresti raggiungere il limite e i metadati non vengono aggiornati per altre risorse. AEM genera il seguente avviso nei registri:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Per modificare il limite, accedi a **[!UICONTROL Strumenti > Operazioni > Console web]** e modifica il valore di [!UICONTROL Maximum POST Parameters] nella configurazione [!UICONTROL Apache Sling Request Parameter Handling] OSGi.

>[!MORELIKETHIS]
>
>* [Modificare i metadati di più raccolte in blocco](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)