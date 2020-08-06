---
title: Importazione ed esportazione di metadati in massa
description: Questo articolo descrive come importare ed esportare i metadati in blocco.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 254a9dec248255f8f76db3531c65b54fb4ebff0c
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 9%

---


# Importazione ed esportazione in massa di metadati {#bulk-metadata-import-and-export}

 AEM Assets consente di importare in massa i metadati delle risorse mediante un file CSV. Potete eseguire aggiornamenti in blocco per le risorse caricate di recente o per le risorse esistenti importando un file CSV. Potete anche assimilare i metadati delle risorse in massa da sistemi di terze parti in formato CSV.

## Importare i metadati {#import-metadata}

L&#39;importazione dei metadati è asincrona e non ostacola le prestazioni del sistema. L’aggiornamento simultaneo dei metadati per più risorse può richiedere molte risorse, a causa XMP’attività di reinserimento se è selezionato il flag del flusso di lavoro. Pianificate tale importazione durante l&#39;utilizzo di un server magro per evitare l&#39;impatto sulle prestazioni di altri utenti.

>[!NOTE]
>
>Per importare i metadati negli spazi dei nomi personalizzati, registrate prima gli spazi dei nomi.

Per importare i metadati in massa, effettuate le seguenti operazioni:

1. Passa all’interfaccia utente Risorse e tocca o fai clic su **[!UICONTROL Crea]** dalla barra degli strumenti.
1. Dal menu, selezionate **[!UICONTROL Metadati]**.
1. On the **[!UICONTROL Metadata Import]** page, tap/click the **[!UICONTROL Select File]**.  Scegli il file CSV con i metadati.
1. Assicuratevi che il file CSV contenga i seguenti parametri:

   | Parametri di importazione metadati | Descrizione |
   |:---|:---|
   | [!UICONTROL Dimensione batch] | Numero di risorse in un batch per cui importare i metadati. Il valore predefinito è 50. Il valore massimo è 100. |
   | [!UICONTROL Separatore di campi] | Il valore predefinito è `,` - una virgola. È possibile specificare qualsiasi altro carattere. |
   | [!UICONTROL Delimitatore valori multipli] | Separatore per i valori dei metadati. Il valore predefinito è `|` - una tubazione. |
   | [!UICONTROL Avvia flussi di lavoro] | False per impostazione predefinita. Quando è impostata su true e le impostazioni predefinite di Launcher sono attive per il `DAM Metadata WriteBack Workflow` (che scrive i metadati nei dati XMP binari). L&#39;abilitazione dei flussi di lavoro di avvio ha un impatto sulle prestazioni del sistema. |
   | [!UICONTROL Nome colonna percorso risorsa] | Definisce il nome della colonna per il file CSV con le risorse. |

1. Toccate o fate clic su **[!UICONTROL Importa]** dalla barra degli strumenti. Una volta importati i metadati, viene inviata una notifica alla inbox Notifica. Passate alla pagina delle proprietà della risorsa e verificate se i valori dei metadati sono stati importati correttamente per le risorse.

Per aggiungere data e marca temporale al momento dell’importazione dei metadati, utilizzate `YYYY-MM-DDThh:mm:ss.fff-00:00` il formato per la data e l’ora. Data e ora sono separate da `T`, `hh` è ore in formato 24 ore, `fff` è nanosecondi e `-00:00` è l’offset del fuso orario. Ad esempio, `2020-03-26T11:26:00.000-07:00` è il 26 marzo 2020 alle 11:26:00.000 ora di ora precedente.

>[!CAUTION]
>
>Se il formato della data non corrisponde, `YYYY-MM-DDThh:mm:ss.fff-00:00`i valori della data non vengono impostati. I formati data del file CSV dei metadati esportati sono nel formato `YYYY-MM-DDThh:mm:ss-00:00`. Se desiderate importarlo, convertitelo nel formato accettabile aggiungendo il valore nanosecondi indicato da `fff`.

## Esporta metadati {#export-metadata}

Alcuni esempi di utilizzo per l’esportazione di metadati in massa sono:

* Importate i metadati in un sistema di terze parti durante la migrazione delle risorse.
* Condividete i metadati delle risorse con un team di progetto più ampio.
* Verificate o verificate la conformità dei metadati.
* Esternalizzare i metadati per una localizzazione separata.

Potete esportare i metadati per più risorse in formato CSV. I metadati vengono esportati in modo asincrono e non influiscono sulle prestazioni del sistema. Per esportare i metadati, AEM attraversa le proprietà del nodo della risorsa `jcr:content/metadata` e dei relativi nodi secondari ed esporta le proprietà dei metadati in un file CSV.

Per esportare i metadati di più risorse in massa, effettuate le seguenti operazioni:

1. Selezionate la cartella di risorse che contiene le risorse per le quali desiderate esportare i metadati. Dalla barra degli strumenti, selezionate **[!UICONTROL Esporta metadati]**.

1. Nella finestra di dialogo Esportazione  metadati, specificate un nome per il file CSV. Per esportare i metadati delle risorse nelle sottocartelle, selezionate **[!UICONTROL Includi risorse nelle sottocartelle]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. Selezionate le opzioni desiderate. Specificare un nome di file e, se necessario, una data.
1. In **[!UICONTROL Proprietà da esportare]**, specificate se esportare tutte le proprietà o solo proprietà specifiche. Se scegliete proprietà **[!UICONTROL selettive]** da esportare, aggiungete le proprietà desiderate.

1. Dalla barra degli strumenti, toccate o fate clic su **[!UICONTROL Esporta]**. Viene visualizzato un messaggio di conferma dell’esportazione dei metadati. Chiudi il messaggio.

1. Apri la notifica della casella in entrata del processo di esportazione. Seleziona il processo e fai clic su **[!UICONTROL Apri]** nella barra degli strumenti. Per scaricare il file CSV con i metadati, tocca o fai clic su **[!UICONTROL Scarica CSV]** nella barra degli strumenti. Fai clic su **[!UICONTROL Chiudi]**.

   ![csv_download](assets/csv_download.png)
