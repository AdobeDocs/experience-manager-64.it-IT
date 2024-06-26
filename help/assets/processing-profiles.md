---
title: Profili per elaborazione di metadati, immagini e video
description: Un profilo rappresenta un insieme di regole relative alle opzioni da applicare alle risorse caricate in una cartella. Specifica il profilo di metadati e il profilo di codifica video da applicare alle risorse video caricate. Per le risorse di immagini, puoi anche specificare quale profilo di immagine applicare alle risorse di immagini per ritagliarle correttamente.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
feature: Workflow,Asset Management,Renditions
role: User,Admin
exl-id: 78d76b4f-a46c-4ffc-b772-ed925eb8e34c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1410'
ht-degree: 3%

---

# Informazioni sui profili per l’elaborazione di metadati, immagini e video {#profiles-for-processing-metadata-images-and-videos}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Un profilo è una ricetta delle opzioni da applicare alle risorse caricate in una cartella. Ad esempio, puoi specificare il profilo di metadati e il profilo di codifica video da applicare alle risorse video caricate. Oppure, quale profilo di imaging applicare alle risorse di immagini per ritagliarle correttamente.

Tali regole possono includere l’aggiunta di metadati, il ritaglio avanzato delle immagini o la definizione di profili di codifica video. In AEM, puoi creare tre tipi di profili, descritti in dettaglio nei seguenti collegamenti:

* [Profili metadati](metadata-profiles.md)
* [Profili immagine](image-profiles.md)
* [Profili video](video-profiles.md)

Per creare, modificare ed eliminare metadati, immagini o profili video, è necessario disporre dei diritti di amministratore.

Dopo aver creato i metadati, le immagini o il profilo video, li assegni a una o più cartelle che utilizzi come destinazione per le risorse appena caricate.

Un concetto importante relativo all’utilizzo dei profili in [!DNL Experience Manager] Le risorse vengono assegnate alle cartelle. All’interno di un profilo, le impostazioni sono sotto forma di profili di metadati, insieme a profili video o di immagini. Queste impostazioni elaborano il contenuto di una cartella insieme a una delle relative sottocartelle. Pertanto, la modalità di denominazione di file e cartelle, la modalità di organizzazione delle sottocartelle e la gestione dei file all’interno di tali cartelle hanno un impatto significativo sul modo in cui tali risorse vengono elaborate da un profilo. Utilizzando strategie di denominazione dei file e delle cartelle coerenti e appropriate, insieme a buone pratiche in materia di metadati, puoi sfruttare al massimo la tua raccolta di risorse digitali e garantire che i file giusti vengano elaborati dal profilo giusto. Ad esempio, vedi [organizzare le risorse utilizzando le cartelle](organize-assets.md#organize-using-folders).

>[!NOTE]
>
>Le risorse spostate da una cartella all’altra non vengono rielaborate. Ad esempio, supponiamo che alla cartella 1 sia assegnato il profilo A e alla cartella 2 il cui profilo B è assegnato. Se si spostano le risorse dalla cartella 1 alla cartella 2, le risorse spostate conservano l&#39;elaborazione originale dalla cartella 1.
>
>Lo stesso vale anche quando si spostano le risorse tra due cartelle a cui è stato assegnato lo stesso profilo.

## Rielaborazione delle risorse in una cartella {#reprocessing-assets}

>[!NOTE]
>
>Si applica a *Dynamic Media - Modalità Scene7* solo in [!DNL Experience Manager] 6.4.7.0 o successivo.

Puoi rielaborare le risorse in una cartella che dispone già di un profilo di elaborazione esistente che hai successivamente modificato.

Ad esempio, supponi di aver creato un profilo immagine e di averlo assegnato a una cartella. A tutte le risorse immagine caricate nella cartella veniva automaticamente applicato il profilo Immagine alle risorse. Tuttavia, in seguito decidi di aggiungere al profilo una nuova proporzione di ritaglio avanzato. Ora, invece di dover selezionare e ricaricare le risorse nella cartella tutte le volte, esegui semplicemente il *Scene7: Rielaborazione delle risorse* workflow.

Puoi eseguire il flusso di lavoro di rielaborazione su una risorsa per la quale l’elaborazione non è riuscita la prima volta. Di conseguenza, anche se non hai modificato un profilo di elaborazione o applicato un profilo di elaborazione, puoi comunque eseguire il flusso di lavoro di rielaborazione su una cartella di risorse in qualsiasi momento.

Facoltativamente, puoi regolare la dimensione batch del flusso di lavoro di rielaborazione da un valore predefinito di 50 risorse fino a 1000 risorse. Quando esegui la _Scene7: Rielaborazione delle risorse_ in una cartella, le risorse vengono raggruppate in batch e quindi inviate al server Dynamic Media per l’elaborazione. Dopo l’elaborazione, i metadati di ogni risorsa nell’intero set di batch vengono aggiornati in AEM. Se la dimensione del batch è molto grande, si potrebbe verificare un ritardo nell&#39;elaborazione. Oppure, se la dimensione del batch è troppo piccola, può causare troppi viaggi di andata e ritorno al server Dynamic Media.

Vedi [Regolazione della dimensione batch del flusso di lavoro di rielaborazione](#adjusting-load).

>[!NOTE]
>
>Se esegui una migrazione di massa delle risorse da Dynamic Media Classic a AEM, devi abilitare l’agente di replica della migrazione sul server Dynamic Media. Al termine della migrazione, assicurati di disabilitare l’agente. L’agente di pubblicazione della migrazione deve essere disabilitato sul server Dynamic Media in modo che il flusso di lavoro Rielabora funzioni come previsto.

<!-- Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. -->

**Per rielaborare le risorse in una cartella**:

1. In AEM, dalla pagina Risorse, passa a una cartella di risorse a cui è assegnato un profilo di elaborazione e alla quale desideri applicare il **Scene7: Rielabora risorsa** flusso di lavoro,

   Le cartelle a cui è già stato assegnato un profilo di elaborazione sono indicate dalla visualizzazione del nome del profilo che si trova direttamente sotto il nome della cartella nella Vista a schede.

1. Seleziona una cartella.

   * Il flusso di lavoro considera in modo ricorsivo tutti i file presenti nella cartella selezionata.
   * Se sono presenti una o più sottocartelle con risorse nella cartella principale selezionata, il flusso di lavoro rielaborerà ogni risorsa nella gerarchia delle cartelle.
   * Come best practice, evita di eseguire questo flusso di lavoro in una gerarchia di cartelle con più di 1000 risorse.

1. Fai clic su **[!UICONTROL Timeline]** dall’elenco a discesa nell’angolo in alto a sinistra della pagina.
1. Fai clic sull’icona del carrello ( **^** ).

   ![Rielaborazione del flusso di lavoro delle risorse 1](/help/assets/assets/reprocess-assets1.png)

1. Fai clic su **[!UICONTROL Avvia flusso di lavoro]**.
1. Da **[!UICONTROL Avvia flusso di lavoro]** elenco a discesa, scegli **[!UICONTROL Scene7: Rielaborazione delle risorse]**.
1. (Facoltativo) In **Immetti il titolo del flusso di lavoro** campo di testo, immetti un nome per il flusso di lavoro. Se necessario, puoi utilizzare il nome per fare riferimento all’istanza del flusso di lavoro.

   ![Rielaborazione delle risorse 2](/help/assets/assets/reprocess-assets2.png)

1. Fai clic su **[!UICONTROL Inizio]**, quindi fai clic su **[!UICONTROL Conferma]**.

   Per monitorare il flusso di lavoro o controllarne l’avanzamento, dai [!DNL Experience Manager] pagina della console principale, fai clic su **[!UICONTROL Strumenti > Flusso di lavoro]**. Nella pagina Istanze flusso di lavoro , seleziona un flusso di lavoro. Nella barra dei menu, fai clic su **[!UICONTROL Cronologia aperta]**. Puoi anche interrompere, sospendere o rinominare un flusso di lavoro selezionato dalla stessa pagina Istanze flusso di lavoro.

### Regolazione della dimensione batch del flusso di lavoro di rielaborazione {#adjusting-load}

(Facoltativo) La dimensione predefinita del batch nel flusso di lavoro di rielaborazione è 50 risorse per processo. Questa dimensione batch ottimale è governata dalla dimensione media delle risorse e dai tipi MIME delle risorse su cui viene eseguita la rielaborazione. Un valore più elevato significa che in un singolo processo di rielaborazione saranno presenti molti file. Di conseguenza, il banner di elaborazione rimane attivo [!DNL Experience Manager] risorse per un periodo di tempo più lungo. Tuttavia, se la dimensione media del file è piccola-1 MB o inferiore, l&#39;Adobe consiglia di aumentare il valore a diverse centinaia, ma mai più di 1000. Se la dimensione media del file è grande centinaia di megabyte, l&#39;Adobe consiglia di ridurre la dimensione del batch fino a 10.

**Per regolare facoltativamente la dimensione batch del flusso di lavoro di rielaborazione**

1. In Experience Manager, tocca **[!UICONTROL Adobe Experience Manager]** per accedere alla console di navigazione globale, quindi tocca l’icona **[!UICONTROL Strumenti]** (martello) > **[!UICONTROL Flusso di lavoro > Modelli]**.
1. Nella pagina Modelli di flusso di lavoro, seleziona Vista a schede o Vista a elenco **[!UICONTROL Scene7: Rielaborazione delle risorse]**.

   ![Pagina Modelli di flusso di lavoro con Scene7: Rielaborazione del flusso di lavoro delle risorse selezionato nella vista a schede](/help/assets/assets-dm/reprocess-assets7.png)

1. Sulla barra degli strumenti, fai clic su **[!UICONTROL Modifica]**. Viene visualizzata una nuova scheda del browser Scene7: Rielabora la pagina del modello di flusso di lavoro Assets.
1. Su Scene7: Rielabora la pagina del flusso di lavoro Assets, nell’angolo in alto a destra, tocca **[!UICONTROL Modifica]** per &quot;sbloccare&quot; il flusso di lavoro.
1. Nel flusso di lavoro, seleziona il componente Caricamento in batch di Scene7 per aprire la barra degli strumenti, quindi tocca **[!UICONTROL Configura]** sulla barra degli strumenti.

   ![Componente Caricamento in batch di Scene7](/help/assets/assets-dm/reprocess-assets8.png)

1. Sulla **[!UICONTROL Caricamento in batch in proprietà dei passaggi Scene7]** impostare quanto segue:
   * In **[!UICONTROL Titolo]** e **[!UICONTROL Descrizione]** campi di testo, immettere un nuovo titolo e una nuova descrizione per il processo, se necessario.
   * Seleziona **[!UICONTROL Avanzamento gestore]** se il tuo handler passerà al passaggio successivo.
   * In **[!UICONTROL Timeout]** immetti il timeout del processo esterno (secondi).
   * In **[!UICONTROL Punto]** immettere un intervallo di polling (secondi) per verificare il completamento del processo esterno.
   * In **[!UICONTROL Campo batch]**, immetti il numero massimo di risorse (50-1000) da elaborare in un processo di caricamento batch di elaborazione batch del server Dynamic Media.
   * Seleziona **[!UICONTROL Avanzamento al timeout]** se desideri avanzare quando viene raggiunto il timeout. Deseleziona se desideri passare alla casella in entrata quando viene raggiunto il timeout.

   ![Finestra di dialogo Proprietà](/help/assets/assets-dm/reprocess-assets3.png)

1. Nell&#39;angolo in alto a destra del **[!UICONTROL Caricamento in batch in proprietà dei passaggi Scene7]** finestra di dialogo, tocca **[!UICONTROL Fine]**.

1. Nell’angolo in alto a destra di Scene7: Rielabora la pagina del modello di flusso di lavoro Assets, tocca **[!UICONTROL Sincronizzazione]**. Quando vedi **[!UICONTROL Sincronizzato]**, il modello di runtime del flusso di lavoro viene sincronizzato correttamente e pronto per rielaborare la risorsa in una cartella.

   ![Sincronizzazione del modello di flusso di lavoro](/help/assets/assets-dm/reprocess-assets1.png)

1. Chiudi la scheda del browser che mostra Scene7: Rielabora il modello di flusso di lavoro Assets.

<!-- 1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, tap **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then tap the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/assets/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, tap **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/assets/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, tap **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, tap **[!UICONTROL CRXDE Lite]** to return to the main [!DNL Experience Manager] console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model. -->
