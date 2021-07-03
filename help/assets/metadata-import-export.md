---
title: Importazione ed esportazione di metadati in blocco
description: Questo articolo descrive come importare ed esportare i metadati in blocco.
contentOwner: AG
feature: Metadati
role: User,Admin
exl-id: 956cdec4-2ba8-43c9-9122-564d764f4681
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 9%

---

# Importazione ed esportazione di metadati in blocco {#bulk-metadata-import-and-export}

AEM Assets consente di importare in blocco i metadati delle risorse utilizzando un file CSV. È possibile eseguire aggiornamenti in blocco per le risorse caricate di recente o per le risorse esistenti importando un file CSV. Puoi anche acquisire i metadati delle risorse in blocco da sistemi di terze parti in formato CSV.

## Importare metadati {#import-metadata}

L’importazione dei metadati è asincrona e non ostacola le prestazioni del sistema. L’aggiornamento simultaneo dei metadati per più risorse può richiedere molte risorse a causa dell’attività di XMP write-back se è selezionato il flag del flusso di lavoro. Pianifica un&#39;importazione di questo tipo durante l&#39;utilizzo snello del server per evitare un impatto sulle prestazioni per altri utenti.

>[!NOTE]
>
>Per importare i metadati negli spazi dei nomi personalizzati, registra innanzitutto gli spazi dei nomi.

Per importare i metadati in blocco, effettua le seguenti operazioni:

1. Passa all’interfaccia utente Assets e dalla barra degli strumenti tocca o fai clic su **[!UICONTROL Crea]** .
1. Dal menu, seleziona **[!UICONTROL Metadati]**.
1. Nella pagina **[!UICONTROL Importazione metadati]**, tocca o fai clic su **[!UICONTROL Seleziona file]**.  Scegli il file CSV con i metadati.
1. Assicurati che il file CSV contenga i seguenti parametri:

   | Parametri di importazione metadati | Descrizione |
   |:---|:---|
   | [!UICONTROL Dimensione batch] | Numero di risorse in un batch per cui devono essere importati i metadati. Il valore predefinito è 50. Il valore massimo è 100. |
   | [!UICONTROL Separatore di campi] | Il valore predefinito è `,` - una virgola. È possibile specificare qualsiasi altro carattere. |
   | [!UICONTROL Delimitatore valori multipli] | Separatore dei valori dei metadati. Il valore predefinito è `|` - una tubazione. |
   | [!UICONTROL Avvia flussi di lavoro] | False per impostazione predefinita. Quando è impostato su true e le impostazioni predefinite di Launcher sono attive per il `DAM Metadata WriteBack Workflow` (che scrive metadati nei dati XMP binari). L’abilitazione dei flussi di lavoro di avvio ha un impatto sulle prestazioni sul sistema. |
   | [!UICONTROL Nome colonna percorso risorsa] | Definisce il nome della colonna del file CSV con le risorse. |

1. Tocca o fai clic su **[!UICONTROL Importa]** nella barra degli strumenti. Una volta importati i metadati, viene inviata una notifica alla casella in entrata delle notifiche. Passa alla pagina delle proprietà della risorsa e verifica se i valori dei metadati sono stati importati correttamente per le risorse.

Per aggiungere data e marca temporale durante l’importazione dei metadati, utilizza il formato `YYYY-MM-DDThh:mm:ss.fff-00:00` per la data e l’ora. La data e l’ora sono separate da `T`, `hh` è ore in formato 24 ore, `fff` è nanosecondi e `-00:00` è l’offset del fuso orario. Ad esempio, `2020-03-26T11:26:00.000-07:00` è il 26 marzo 2020 alle 11:26:00.000 ora PST.

>[!CAUTION]
>
>Se il formato della data non corrisponde a `YYYY-MM-DDThh:mm:ss.fff-00:00`, i valori della data non vengono impostati. I formati di data del file CSV dei metadati esportati sono nel formato `YYYY-MM-DDThh:mm:ss-00:00`. Per importarlo, convertirlo nel formato accettabile aggiungendo il valore nanosecondi indicato da `fff`.

## Esporta metadati {#export-metadata}

Alcuni casi d&#39;uso per esportare i metadati in blocco sono:

* Importa i metadati in un sistema di terze parti durante la migrazione delle risorse.
* Condividi i metadati delle risorse con un team di progetto più ampio.
* Verifica o controlla i metadati per verificarne la conformità.
* Esternalizzare i metadati per una localizzazione separata.

Puoi esportare i metadati per più risorse in un formato CSV. I metadati vengono esportati in modo asincrono e non influiscono sulle prestazioni del sistema. Per esportare i metadati, AEM analizza le proprietà del nodo della risorsa `jcr:content/metadata` e dei relativi nodi figlio ed esporta le proprietà dei metadati in un file CSV.

Per esportare i metadati di più risorse in blocco, effettua le seguenti operazioni:

1. Seleziona la cartella di risorse che contiene le risorse di cui desideri esportare i metadati. Dalla barra degli strumenti, seleziona **[!UICONTROL Esporta metadati]**.

1. Nella finestra di dialogo [!UICONTROL Esportazione metadati] , specifica un nome per il file CSV. Per esportare i metadati per le risorse nelle sottocartelle, seleziona **[!UICONTROL Includi risorse nelle sottocartelle]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Seleziona le opzioni desiderate. Fornire un nome file e, se necessario, una data.
1. In **[!UICONTROL Proprietà da esportare]**, specifica se esportare tutte le proprietà o specifiche. Se scegli le proprietà **[!UICONTROL Selective]** da esportare, aggiungi le proprietà desiderate.

1. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Esporta]**. Un messaggio conferma l’esportazione dei metadati. Chiudi il messaggio.

1. Apri la notifica della casella in entrata del processo di esportazione. Seleziona il processo e fai clic su **[!UICONTROL Apri]** nella barra degli strumenti. Per scaricare il file CSV con i metadati, tocca o fai clic su **[!UICONTROL Scarica CSV]** nella barra degli strumenti. Fai clic su **[!UICONTROL Chiudi]**.

   ![csv_download](assets/csv_download.png)
