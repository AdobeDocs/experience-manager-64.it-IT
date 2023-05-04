---
title: Gestire le risorse composite e generare le risorse secondarie.
description: Scopri come creare riferimenti a [!DNL Experience Manager] risorse da file InDesign, Adobe Illustrator e Photoshop. Inoltre, scopri come utilizzare la funzione Visualizzatore pagina per visualizzare singole pagine di file multipagina.
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 1%

---

# Gestire le risorse composite con le risorse secondarie {#managing-compound-assets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets può identificare se un file caricato contiene riferimenti a risorse già esistenti nell’archivio. Questa funzione è disponibile solo per i formati di file supportati. Se la risorsa caricata contiene riferimenti a [!DNL Experience Manager] risorse, viene creato un collegamento bidirezionale tra le risorse caricate e a cui si fa riferimento.

Oltre a eliminare la ridondanza, il riferimento [!DNL Experience Manager] le risorse nelle applicazioni Adobe Creative Cloud migliorano la collaborazione e aumentano l’efficienza e la produttività degli utenti.

[!DNL Experience Manager] Risorse supportate **riferimento bidirezionale**. Puoi trovare le risorse a cui si fa riferimento nella pagina dei dettagli della risorsa del file caricato. Inoltre, è possibile visualizzare i file di riferimento per [!DNL Experience Manager] nella pagina dei dettagli della risorsa a cui si fa riferimento.

I riferimenti vengono risolti in base al percorso, all’ID documento e all’ID istanza delle risorse a cui si fa riferimento.

## Adobe Illustrator: Aggiungere risorse come riferimenti {#refai}

È possibile fare riferimento a [!DNL Experience Manager] risorse da un file Adobe Illustrator.

1. Utilizzo [[!DNL Experience Manager] app desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=it), montaggio [!DNL Experience Manager] Archivio risorse come unità sul computer locale. Nell&#39;unità montata, individuate la posizione della risorsa a cui desiderate fare riferimento.
1. Trascina la risorsa dall’unità montata al file Illustrator.
1. Salvare il file Illustrator sull&#39;unità montata oppure [caricare](managing-assets-touch-ui.md#uploading-assets) al [!DNL Experience Manager] archivio.
1. Al termine del flusso di lavoro, passa alla pagina dei dettagli della risorsa. I riferimenti a esistenti [!DNL Experience Manager] le risorse sono elencate in **[!UICONTROL Dipendenze]** in **[!UICONTROL Riferimenti]** colonna.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Le risorse di riferimento visualizzate in **[!UICONTROL Dipendenze]** può essere fatto riferimento anche a file diversi da quello corrente. Per visualizzare un elenco dei file di riferimento di una risorsa, fai clic sulla risorsa in **[!UICONTROL Dipendenze]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Fai clic sul pulsante **[!UICONTROL Visualizza proprietà]** dalla barra degli strumenti. Nella pagina delle proprietà, l’elenco dei file che fanno riferimento alla risorsa corrente viene visualizzato sotto **[!UICONTROL Riferimenti]** nella colonna **[!UICONTROL Base]** scheda .

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign: Aggiungere risorse come riferimenti {#add-aem-assets-as-references-in-adobe-indesign}

Riferimento [!DNL Experience Manager] risorse all’interno di un file InDesign, trascinate [!DNL Experience Manager] risorse nel file InDesign o esporta il file InDesign come file ZIP.

Le risorse di riferimento esistono già in [!DNL Experience Manager] Risorse. Puoi estrarre le risorse secondarie per [configurare il server InDesign](indesign.md). Le risorse incorporate in un file InDesign vengono estratte come risorse secondarie.

>[!NOTE]
>
>Se il server InDesign è proxy, i file InDesign presentano l’anteprima incorporata nei metadati XMP. In questo caso, l’estrazione delle miniature non è esplicitamente richiesta. Tuttavia, se il server InDesign non è proxy, le miniature devono essere estratte esplicitamente per i file InDesign.

Quando un file INDD viene caricato, i riferimenti vengono recuperati eseguendo una query sulle risorse che hanno `xmpMM:InstanceID` e `xmpMM:DocumentID` nella directory archivio.

### Creare riferimenti trascinando le risorse {#create-references-by-dragging-aem-assets}

Questa procedura è simile a [Aggiungere risorse come riferimenti in Adobe Illustrator](#refai).

### Creare riferimenti alle risorse esportando un file ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Esegui i passaggi descritti in [Creazione di modelli di flussi di lavoro](/help/sites-developing/workflows-models.md) per creare un nuovo flusso di lavoro.
1. Utilizza la [Funzione pacchetto di Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) per esportare il documento. Adobe InDesign può esportare un documento e le risorse collegate come pacchetto. In questo caso, la cartella esportata contiene un `Links` che contiene risorse secondarie nel file InDesign. La `Links` cartella presente nella stessa cartella del file INDD.
1. Crea un file ZIP e caricalo su [!DNL Experience Manager] archivio.
1. Avvia il flusso di lavoro Annulla archiviazione.
1. Al termine del flusso di lavoro, i riferimenti nella cartella Collegamenti vengono automaticamente indicati come risorse secondarie. Per visualizzare un elenco delle risorse a cui si fa riferimento, passa alla pagina dei dettagli delle risorse della risorsa InDesign e chiudi la [Ferrovia](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop: Aggiungere risorse come riferimenti {#refps}

1. Utilizzando un client WebDav, mount [!DNL Experience Manager] Risorse come unità.
1. Per creare riferimenti a [!DNL Experience Manager] risorse in un file Photoshop, accedi alle risorse corrispondenti nell’unità montata utilizzando la funzionalità Posiziona collegamento in Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Salva in file Photoshop sull&#39;unità montata o [caricare](managing-assets-touch-ui.md#uploading-assets) al [!DNL Experience Manager] archivio.
1. Al termine del flusso di lavoro, i riferimenti a [!DNL Experience Manager] le risorse sono elencate nella pagina dei dettagli della risorsa.

   Per visualizzare le risorse a cui si fa riferimento, chiudi la [Ferrovia](/help/sites-authoring/basic-handling.md#rail-selector) nella pagina dei dettagli della risorsa.

1. Le risorse a cui si fa riferimento contengono anche l’elenco delle risorse a cui fanno riferimento. Per visualizzare un elenco delle risorse a cui si fa riferimento, passa alla pagina dei dettagli della risorsa e chiudi la [barra](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>È inoltre possibile fare riferimento alle risorse all’interno delle risorse composte in base al relativo ID documento e ID istanza. Questa funzionalità è disponibile solo con le versioni Adobe Illustrator e Adobe Photoshop . Per altri, il riferimento viene fatto sulla base del percorso relativo delle risorse collegate nella risorsa composta principale, come fatto nelle versioni precedenti di AEM.

## Creare risorse secondarie {#generate-subassets}

Per le risorse supportate con formati multipagina — file PDF, file AI, file Microsoft PowerPoint e Apple Keynote e file Adobe InDesign — [!DNL Experience Manager] può generare risorse secondarie corrispondenti a ogni singola pagina della risorsa originale. Queste risorse secondarie sono collegate al *parent* e facilita la visualizzazione su più pagine. Per tutti gli altri scopi, le attività secondarie sono trattate come attività normali in AEM.

La generazione di risorse secondarie è disabilitata per impostazione predefinita. Per abilitare la generazione di risorse secondarie, procedi come segue:

1. Accedi ad Experience Manager come amministratore. Accesso **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Seleziona **[!UICONTROL Risorsa di aggiornamento DAM]** workflow e fai clic su **[!UICONTROL Modifica]**.
1. Fai clic su **[!UICONTROL Attiva/Disattiva pannello laterale]** e individua le **[!UICONTROL Crea risorsa secondaria]** passo. Aggiungi il passaggio al flusso di lavoro. Fai clic su **[!UICONTROL Sincronizza]**.

Per generare le risorse secondarie, effettua una delle seguenti operazioni:

* Nuove risorse: La [!UICONTROL Aggiorna risorse DAM] viene eseguito su qualsiasi nuova risorsa caricata in AEM. Le risorse secondarie vengono generate automaticamente per le nuove risorse multipagina.
* Risorse multipagina esistenti: Esegui manualmente il [!UICONTROL Aggiorna risorse DAM] flusso di lavoro seguendo uno dei passaggi seguenti:

   * Seleziona una risorsa e fai clic su [!UICONTROL Timeline] per aprire il pannello a sinistra. In alternativa, utilizza la scelta rapida da tastiera `alt + 3`. Fai clic su [!UICONTROL Avvia flusso di lavoro], seleziona [!UICONTROL Risorsa di aggiornamento DAM], fai clic su [!UICONTROL Inizio]e fai clic su [!UICONTROL Procedi].
   * Seleziona una risorsa e fai clic su [!UICONTROL Crea > Flusso di lavoro] dalla barra degli strumenti. Dalla finestra di dialogo a comparsa, seleziona [!UICONTROL Risorsa di aggiornamento DAM] flusso di lavoro, fai clic su [!UICONTROL Inizio]e fai clic su [!UICONTROL Procedi].

Specificamente per i documenti Microsoft Word, eseguire il **[!UICONTROL Documenti Word analisi DAM]** workflow. Genera un `cq:Page` dal contenuto del documento di Microsoft Word. Le immagini estratte dal documento sono referenziate dal `cq:Page` componente. Queste immagini vengono estratte anche se la generazione di risorse secondarie è disabilitata.

## Visualizzare le risorse secondarie {#viewing-subassets}

Le risorse secondarie vengono visualizzate solo se sono generate e sono disponibili per la risorsa multipagina selezionata. Per visualizzare le risorse secondarie generate, apri la risorsa multipagina. Nell’area in alto a sinistra della pagina, fai clic su ![Icona a sinistra della barra](assets/do-not-localize/aem_leftrail_contentonly.png) e fai clic su **[!UICONTROL Risorse secondarie]** dall&#39;elenco. Quando selezioni **[!UICONTROL Risorse secondarie]** dall&#39;elenco. In alternativa, utilizza la scelta rapida da tastiera `alt + 5`.

![Visualizzare le risorse secondarie di una risorsa multipagina](assets/view_subassets_simulation.gif)

## Visualizzare pagine di un file multipagina {#view-pages-of-a-multi-page-file}

È possibile visualizzare un file con più pagine, ad esempio file PDF, INDD, PPT, PPTX e AI, utilizzando la funzione Visualizzatore pagina di [!DNL Experience Manager] Risorse. Apri una risorsa multipagina e fai clic su **[!UICONTROL Visualizza pagine]** dall’angolo in alto a sinistra della pagina. Il visualizzatore pagina visualizzato mostra le pagine della risorsa e i controlli per sfogliare e ingrandire ciascuna pagina.

![Visualizzare e visualizzare le pagine di una risorsa multipagina](assets/view_multipage_asset_fmr.gif)

Ad InDesign, è possibile estrarre pagine utilizzando il server InDesign. Se le anteprime delle pagine vengono salvate durante la creazione di file InDesign, InDesign Server non è necessario per l’estrazione della pagina.

Le seguenti opzioni sono disponibili nella barra degli strumenti, nella barra a sinistra e nei controlli Visualizzatore pagina:

* **[!UICONTROL Azioni desktop]** per aprire o visualizzare una risorsa secondaria specifica utilizzando [!DNL Experience Manager] app desktop. Scopri come [configurare le azioni desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) se utilizzi [!DNL Experience Manager] app desktop.

* **[!UICONTROL Proprietà]** apre la [!UICONTROL Proprietà] della risorsa secondaria specifica.

* **[!UICONTROL Annota]** consente di annotare la risorsa secondaria specifica. Le annotazioni utilizzate in risorse secondarie separate vengono raccolte e visualizzate insieme all’apertura della risorsa principale per la visualizzazione.

* **[!UICONTROL Panoramica della pagina]** visualizza tutte le risorse secondarie simultaneamente.

* **[!UICONTROL Timeline]** dalla barra a sinistra dopo aver fatto clic su ![Icona a sinistra della barra](assets/do-not-localize/aem_leftrail_contentonly.png) visualizza il flusso di attività per il file .

## Best practice e limitazioni {#best-practice-limitation-tips}

* La generazione di risorse secondarie può richiedere un utilizzo intensivo delle risorse in qualsiasi implementazione di Experience Manager. Se generi risorse secondarie quando vengono caricate risorse complesse, aggiungi il passaggio nel flusso di lavoro Aggiorna risorsa DAM . Se generi risorse secondarie su richiesta, crea un flusso di lavoro separato per generare le risorse secondarie. Un flusso di lavoro dedicato ti consente di saltare gli altri passaggi del flusso di lavoro Aggiorna risorsa DAM e salvare le risorse di calcolo.

>[!MORELIKETHIS]
>
>* [Utilizzare l’app desktop Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

