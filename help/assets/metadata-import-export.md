---
title: Importazione ed esportazione di metadati in blocco
description: Questo articolo descrive come importare ed esportare i metadati in blocco.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 956cdec4-2ba8-43c9-9122-564d764f4681
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 10%

---

# Importazione ed esportazione di metadati in blocco {#bulk-metadata-import-and-export}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

[!DNL Experience Manager] Assets consente di importare in blocco i metadati delle risorse utilizzando un file CSV. È possibile eseguire aggiornamenti in blocco per le risorse caricate di recente o per le risorse esistenti importando un file CSV. Puoi anche acquisire i metadati delle risorse in blocco da sistemi di terze parti in formato CSV.

## Importare metadati {#import-metadata}

L’importazione dei metadati è asincrona e non ostacola le prestazioni del sistema. L’aggiornamento simultaneo dei metadati per più risorse può richiedere molte risorse a causa dell’attività di XMP write-back se è selezionato il flag del flusso di lavoro. Pianifica un&#39;importazione di questo tipo durante l&#39;utilizzo snello del server per evitare un impatto sulle prestazioni per altri utenti.

>[!NOTE]
>
>Per importare i metadati negli spazi dei nomi personalizzati, registra innanzitutto gli spazi dei nomi.

Per importare i metadati in blocco, effettua le seguenti operazioni:

1. Passa all’interfaccia utente Assets e tocca o fai clic su **[!UICONTROL Crea]** dalla barra degli strumenti.
1. Dal menu , seleziona **[!UICONTROL Metadati]**.
1. Sulla **[!UICONTROL Importazione metadati]** pagina, tocca o fai clic sul **[!UICONTROL Seleziona file]**.  Scegli il file CSV con i metadati.
1. Assicurati che il file CSV contenga i seguenti parametri:

   | Parametri di importazione metadati | Descrizione |
   |:---|:---|
   | [!UICONTROL Dimensione batch] | Numero di risorse in un batch per cui devono essere importati i metadati. Il valore predefinito è 50. Il valore massimo è 100. |
   | [!UICONTROL Separatore di campi] | Il valore predefinito è `,` - una virgola. È possibile specificare qualsiasi altro carattere. |
   | [!UICONTROL Delimitatore valori multipli] | Separatore dei valori dei metadati. Il valore predefinito è `|` - una pipa. |
   | [!UICONTROL Avvia flussi di lavoro] | False per impostazione predefinita. Quando è impostato su true e le impostazioni predefinite sono attive per `DAM Metadata WriteBack Workflow` (che scrive i metadati nei dati XMP binari). L&#39;abilitazione dei flussi di lavoro ha un impatto sulle prestazioni sul sistema. |
   | [!UICONTROL Nome colonna percorso risorsa] | Definisce il nome della colonna del file CSV con le risorse. |

1. Tocca o fai clic su **[!UICONTROL Importa]** dalla barra degli strumenti. Una volta importati i metadati, viene inviata una notifica alla casella in entrata delle notifiche. Passa alla pagina delle proprietà della risorsa e verifica se i valori dei metadati sono importati correttamente per le risorse.

Per aggiungere data e marca temporale durante l’importazione dei metadati, utilizza `YYYY-MM-DDThh:mm:ss.fff-00:00` formato per data e ora. Data e ora sono separate da `T`, `hh` è in formato 24 ore, `fff` è nanosecondi, e `-00:00` è l&#39;offset del fuso orario. Ad esempio: `2020-03-26T11:26:00.000-07:00` è il 26 marzo 2020 alle 11:26:00.000 PST tempo.

>[!CAUTION]
>
>Se il formato della data non corrisponde `YYYY-MM-DDThh:mm:ss.fff-00:00`, i valori di data non sono impostati. Il formato dei formati di data del file CSV dei metadati esportati è `YYYY-MM-DDThh:mm:ss-00:00`. Per importarlo, convertirlo nel formato accettabile aggiungendo il valore nanosecondi indicato da `fff`.

## Esporta metadati {#export-metadata}

Alcuni casi d&#39;uso per esportare i metadati in blocco sono:

* Importa i metadati in un sistema di terze parti durante la migrazione delle risorse.
* Condividi i metadati delle risorse con un team di progetto più ampio.
* Verifica o controlla i metadati per verificarne la conformità.
* Esternalizzare i metadati per una localizzazione separata.

Puoi esportare i metadati per più risorse in un formato CSV. I metadati vengono esportati in modo asincrono e non influiscono sulle prestazioni del sistema. Per esportare i metadati, [!DNL Experience Manager] attraversa le proprietà del nodo risorsa `jcr:content/metadata` ed esporta le proprietà dei metadati in un file CSV.

Per esportare i metadati di più risorse in blocco, effettua le seguenti operazioni:

1. Seleziona la cartella di risorse che contiene le risorse di cui desideri esportare i metadati. Dalla barra degli strumenti, seleziona **[!UICONTROL Esportare i metadati]**.

1. In [!UICONTROL Esportazione metadati] specifica un nome per il file CSV. Per esportare i metadati delle risorse nelle sottocartelle, seleziona **[!UICONTROL Includere risorse nelle sottocartelle]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Seleziona le opzioni desiderate. Fornire un nome file e, se necessario, una data.
1. In **[!UICONTROL Proprietà da esportare]**, specifica se esportare tutte le proprietà o specifiche. Se scegli **[!UICONTROL Selettivo]** proprietà da esportare, aggiungi le proprietà desiderate.

1. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Esporta]**. Un messaggio conferma l’esportazione dei metadati. Chiudi il messaggio.

1. Apri la notifica della casella in entrata del processo di esportazione. Seleziona il processo e fai clic su **[!UICONTROL Apri]** nella barra degli strumenti. Per scaricare il file CSV con i metadati, tocca o fai clic su **[!UICONTROL Scarica CSV]** nella barra degli strumenti. Fai clic su **[!UICONTROL Chiudi]**.

   ![csv_download](assets/csv_download.png)
