---
title: Gestire le risorse composite e generare le risorse secondarie.
description: Scopri come creare riferimenti a risorse AEM dai file InDesign, Adobe Illustrator e Photoshop. Inoltre, scopri come utilizzare la funzione Visualizzatore pagina per visualizzare singole pagine di file multipagina, inclusi file PDF, INDD, PPT, PPTX e AI.
contentOwner: AG
feature: Gestione risorse
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1412'
ht-degree: 0%

---

# Gestire le risorse composite con le risorse secondarie {#managing-compound-assets}

Le risorse di Adobe Experience Manager (AEM) possono identificare se un file caricato contiene riferimenti a risorse già esistenti nell’archivio. Questa funzione è disponibile solo per i formati di file supportati. Se la risorsa caricata contiene riferimenti a AEM risorse, viene creato un collegamento bidirezionale tra le risorse caricate e quelle a cui si fa riferimento.

Oltre a eliminare la ridondanza, il riferimento AEM risorse nelle applicazioni Adobe Creative Cloud migliora la collaborazione e aumenta l’efficienza e la produttività degli utenti.

AEM Assets supporta **riferimenti bidirezionali**. Puoi trovare le risorse a cui si fa riferimento nella pagina dei dettagli della risorsa del file caricato. Inoltre, puoi visualizzare i file di riferimento per le risorse AEM nella pagina dei dettagli delle risorse della risorsa a cui si fa riferimento.

I riferimenti vengono risolti in base al percorso, all’ID documento e all’ID istanza delle risorse a cui si fa riferimento.

## Adobe Illustrator: Aggiungere risorse come riferimenti {#refai}

Puoi fare riferimento a risorse AEM esistenti da un file Adobe Illustrator.

1. Utilizzando [AEM app desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=it), monta l&#39;archivio AEM Assets come unità sul computer locale. Nell&#39;unità montata, individuate la posizione della risorsa a cui desiderate fare riferimento.
1. Trascina la risorsa dall’unità montata al file Illustrator.
1. Salva il file Illustrator sull&#39;unità montata o [carica](managing-assets-touch-ui.md#uploading-assets) nell&#39;archivio AEM.
1. Al termine del flusso di lavoro, passa alla pagina dei dettagli della risorsa. I riferimenti alle risorse AEM esistenti sono elencati in **[!UICONTROL Dipendenze]** nella colonna **[!UICONTROL Riferimenti]** .

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Le risorse di riferimento visualizzate in **[!UICONTROL Dipendenze]** possono essere referenziate anche da file diversi da quello corrente. Per visualizzare un elenco dei file di riferimento per una risorsa, fai clic sulla risorsa in **[!UICONTROL Dipendenze]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Fai clic sull&#39;icona **[!UICONTROL Visualizza proprietà]** nella barra degli strumenti. Nella pagina delle proprietà, l’elenco dei file che fanno riferimento alla risorsa corrente viene visualizzato sotto la colonna **[!UICONTROL Riferimenti]** nella scheda **[!UICONTROL Base]** .

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign: Aggiungere risorse come riferimenti {#add-aem-assets-as-references-in-adobe-indesign}

Per fare riferimento AEM risorse all’interno di un file InDesign, trascina AEM risorse nel file InDesign o esporta il file InDesign come file ZIP.

Le risorse di riferimento esistono già in AEM Assets. È possibile estrarre le risorse secondarie da [configurare il server InDesign](indesign.md). Le risorse incorporate in un file InDesign vengono estratte come risorse secondarie.

>[!NOTE]
>
>Se il server InDesign è proxy, i file InDesign presentano l’anteprima incorporata nei metadati XMP. In questo caso, l’estrazione delle miniature non è esplicitamente richiesta. Tuttavia, se il server InDesign non è proxy, le miniature devono essere estratte esplicitamente per i file InDesign.

Quando un file INDD viene caricato, i riferimenti vengono recuperati eseguendo una query sulle risorse con proprietà `xmpMM:InstanceID` e `xmpMM:DocumentID` nell’archivio.

### Creare riferimenti trascinando le risorse {#create-references-by-dragging-aem-assets}

Questa procedura è simile a [Aggiungi risorse come riferimenti in Adobe Illustrator](#refai).

### Creare riferimenti alle risorse esportando un file ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Esegui i passaggi descritti in [Creazione di modelli di flusso di lavoro](/help/sites-developing/workflows-models.md) per creare un nuovo flusso di lavoro.
1. Utilizza la funzione [Pacchetto di Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) per esportare il documento. Adobe InDesign può esportare un documento e le risorse collegate come pacchetto. In questo caso, la cartella esportata contiene una cartella `Links` contenente risorse secondarie nel file InDesign. La cartella `Links` è presente nella stessa cartella del file INDD.
1. Crea un file ZIP e caricalo nell’archivio AEM.
1. Avvia il flusso di lavoro Annulla archiviazione.
1. Al termine del flusso di lavoro, i riferimenti nella cartella Collegamenti vengono automaticamente indicati come risorse secondarie. Per visualizzare un elenco delle risorse a cui si fa riferimento, passa alla pagina dei dettagli delle risorse della risorsa InDesign e chiudi la barra [Barra](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop: Aggiungere risorse come riferimenti {#refps}

1. Utilizzando un client WebDav, monta AEM Assets come unità.
1. Per creare riferimenti a AEM risorse in un file Photoshop, accedi alle risorse corrispondenti nell’unità montata utilizzando la funzionalità Posiziona collegamento in Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Salva nel file Photoshop sull&#39;unità montata o [carica](managing-assets-touch-ui.md#uploading-assets) nell&#39;archivio AEM.
1. Al termine del flusso di lavoro, i riferimenti alle risorse AEM esistenti sono elencati nella pagina dei dettagli della risorsa.

   Per visualizzare le risorse a cui si fa riferimento, chiudi la barra [Barra](/help/sites-authoring/basic-handling.md#rail-selector) nella pagina dei dettagli delle risorse.

1. Le risorse a cui si fa riferimento contengono anche l’elenco delle risorse a cui fanno riferimento. Per visualizzare un elenco delle risorse a cui si fa riferimento, passa alla pagina dei dettagli della risorsa e chiudi la barra [a1/>.](/help/sites-authoring/basic-handling.md#rail-selector)

>[!NOTE]
>
>È inoltre possibile fare riferimento alle risorse all’interno delle risorse composte in base al relativo ID documento e ID istanza. Questa funzionalità è disponibile solo con le versioni Adobe Illustrator e Adobe Photoshop . Per altri, il riferimento viene fatto sulla base del percorso relativo delle risorse collegate nella risorsa composta principale, come fatto nelle versioni precedenti di AEM.

## Creare risorse secondarie {#generate-subassets}

Per le risorse supportate con formati a più pagine (file PDF, file AI, file Microsoft PowerPoint e Apple Keynote e file Adobe InDesign) AEM possono generare risorse secondarie corrispondenti a ogni singola pagina della risorsa originale. Queste risorse secondarie sono collegate alla risorsa *principale* e facilitano la visualizzazione multipagina. Per tutti gli altri scopi, le attività secondarie sono trattate come attività normali in AEM.

La generazione di risorse secondarie è disabilitata per impostazione predefinita. Per abilitare la generazione di risorse secondarie, procedi come segue:

1. Accedi ad Experience Manager come amministratore. Accedi a **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Seleziona il flusso di lavoro **[!UICONTROL Aggiorna risorsa DAM]** e fai clic su **[!UICONTROL Modifica]**.
1. Fai clic su **[!UICONTROL Attiva/Disattiva pannello laterale]** e individua il passaggio **[!UICONTROL Crea sottorisorsa]** . Aggiungi il passaggio al flusso di lavoro. Fai clic su **[!UICONTROL Sincronizza]**.

Per generare le risorse secondarie, effettua una delle seguenti operazioni:

* Nuove risorse: Il flusso di lavoro [!UICONTROL Aggiorna risorse DAM] viene eseguito su qualsiasi nuova risorsa caricata in AEM. Le risorse secondarie vengono generate automaticamente per le nuove risorse multipagina.
* Risorse multipagina esistenti: Esegui manualmente il flusso di lavoro [!UICONTROL Aggiorna risorse DAM] seguendo uno dei passaggi seguenti:

   * Seleziona una risorsa e fai clic su [!UICONTROL Timeline] per aprire il pannello a sinistra. In alternativa, utilizza la scelta rapida da tastiera `alt + 3`. Fai clic su [!UICONTROL Avvia flusso di lavoro], seleziona [!UICONTROL Aggiorna risorsa DAM], fai clic su [!UICONTROL Avvia] e fai clic su [!UICONTROL Procedi].
   * Seleziona una risorsa e fai clic su [!UICONTROL Crea > Flusso di lavoro] nella barra degli strumenti. Dalla finestra di dialogo a comparsa, seleziona [!UICONTROL Aggiorna risorsa DAM] flusso di lavoro, fai clic su [!UICONTROL Avvia] e fai clic su [!UICONTROL Procedi].

Specificamente per i documenti Microsoft Word, eseguire il flusso di lavoro **[!UICONTROL DAM Parse Word Documents]**. Viene generato un componente `cq:Page` dal contenuto del documento di Microsoft Word. Le immagini estratte dal documento sono referenziate dal componente `cq:Page` . Queste immagini vengono estratte anche se la generazione di risorse secondarie è disabilitata.

## Visualizzare le risorse secondarie {#viewing-subassets}

Le risorse secondarie vengono visualizzate solo se sono generate e sono disponibili per la risorsa multipagina selezionata. Per visualizzare le risorse secondarie generate, apri la risorsa multipagina. Nell’area in alto a sinistra della pagina, fai clic su ![Icona della barra a sinistra](assets/do-not-localize/aem_leftrail_contentonly.png) e fai clic su **[!UICONTROL Risorse secondarie]** dall’elenco. Quando selezioni **[!UICONTROL Risorse secondarie]** dall’elenco. In alternativa, utilizza la scelta rapida da tastiera `alt + 5`.

![Visualizzare le risorse secondarie di una risorsa multipagina](assets/view_subassets_simulation.gif)

## Visualizzare pagine di un file multipagina {#view-pages-of-a-multi-page-file}

È possibile visualizzare un file con più pagine, ad esempio PDF, INDD, PPT, PPTX e AI, utilizzando la funzione visualizzatore pagina di AEM Assets. Apri una risorsa multipagina e fai clic su **[!UICONTROL Visualizza pagine]** nell’angolo in alto a sinistra della pagina. Il visualizzatore pagina visualizzato mostra le pagine della risorsa e i controlli per sfogliare e ingrandire ciascuna pagina.

![Visualizzare e visualizzare le pagine di una risorsa multipagina](assets/view_multipage_asset_fmr.gif)

Ad InDesign, è possibile estrarre pagine utilizzando il server InDesign. Se le anteprime delle pagine vengono salvate durante la creazione di file InDesign, InDesign Server non è necessario per l’estrazione della pagina.

Le seguenti opzioni sono disponibili nella barra degli strumenti, nella barra a sinistra e nei controlli Visualizzatore pagina:

* **[!UICONTROL Azioni desktop]** per aprire o visualizzare una risorsa secondaria specifica utilizzando AEM’app desktop. Scopri come [configurare le azioni desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#desktopactions-v2) se utilizzi AEM’app desktop.

* **** L’opzione Proprietà apre la pagina   Proprietà della risorsa secondaria specifica.

* **[!UICONTROL L’opzione]** Annota consente di annotare la risorsa secondaria specifica. Le annotazioni utilizzate in risorse secondarie separate vengono raccolte e visualizzate insieme all’apertura della risorsa principale per la visualizzazione.

* **[!UICONTROL L’opzione]** Panoramica pagina visualizza tutte le risorse secondarie simultaneamente.

* **** L’opzione Timeline dalla barra a sinistra dopo aver fatto clic sull’icona della barra a  ![sinistra ](assets/do-not-localize/aem_leftrail_contentonly.png) visualizza il flusso di attività per il file.

## Best practice e limitazioni {#best-practice-limitation-tips}

* La generazione di risorse secondarie può richiedere un utilizzo intensivo delle risorse in qualsiasi implementazione di Experience Manager. Se generi risorse secondarie quando vengono caricate risorse complesse, aggiungi il passaggio nel flusso di lavoro Aggiorna risorsa DAM . Se generi risorse secondarie su richiesta, crea un flusso di lavoro separato per generare le risorse secondarie. Un flusso di lavoro dedicato ti consente di saltare gli altri passaggi del flusso di lavoro Aggiorna risorsa DAM e salvare le risorse di calcolo.

>[!MORELIKETHIS]
>
>* [Utilizzare l’app desktop Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

