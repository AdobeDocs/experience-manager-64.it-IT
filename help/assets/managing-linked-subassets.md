---
title: Gestire le risorse composte e generare le risorse secondarie.
description: Scoprite come creare riferimenti a AEM risorse dai file  InDesign,  Adobe Illustrator e Photoshop. Scoprite inoltre come utilizzare la funzione Visualizzatore pagina per visualizzare le singole pagine di file con più pagine, inclusi file PDF, INDD, PPT, PPTX e AI.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 0%

---


# Gestire le risorse composte con risorse secondarie {#managing-compound-assets}

Le risorse Adobe Experience Manager (AEM) possono identificare se un file caricato contiene riferimenti a risorse già presenti nella directory archivio. Questa funzione è disponibile solo per i formati di file supportati. Se la risorsa caricata contiene riferimenti a AEM risorse, viene creato un collegamento bidirezionale tra le risorse caricate e quelle a cui viene fatto riferimento.

Oltre ad eliminare la ridondanza, il riferimento AEM risorse nelle applicazioni Adobe Creative Cloud migliora la collaborazione e aumenta l&#39;efficienza e la produttività degli utenti.

 AEM Assets supporta **riferimenti bidirezionali**. Potete trovare le risorse di riferimento nella pagina dei dettagli delle risorse del file caricato. Inoltre, potete visualizzare i file di riferimento per AEM risorse nella pagina dei dettagli delle risorse della risorsa di riferimento.

I riferimenti vengono risolti in base a percorso, ID documento e ID istanza delle risorse a cui viene fatto riferimento.

## Aggiungere  AEM Assets come riferimenti in  Adobe Illustrator {#refai}

Potete fare riferimento a risorse AEM esistenti direttamente da un file Adobe Illustrator .

1. Utilizzando l&#39;app [AEM desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html), installare  repository AEM Assets come unità sul computer locale. Nell’unità montata, andate alla posizione della risorsa a cui desiderate fare riferimento.
1. Trascinate la risorsa dall’unità montata al file Illustrator .
1. Salvare il file Illustrator  sull&#39;unità montata oppure [caricare](managing-assets-touch-ui.md#uploading-assets) nell&#39;archivio AEM.
1. Al termine del flusso di lavoro, passate alla pagina dei dettagli della risorsa. I riferimenti alle risorse AEM esistenti sono elencati in **[!UICONTROL Dipendenze]** nella colonna **[!UICONTROL Riferimenti]**.

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. Le risorse di riferimento visualizzate in **[!UICONTROL Dependencies]** possono essere utilizzate anche come riferimento da file diversi da quello corrente. Per visualizzare un elenco dei file di riferimento per una risorsa, fai clic sulla risorsa in **[!UICONTROL Dipendenze]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Fare clic sull&#39;icona **[!UICONTROL Visualizza proprietà]** dalla barra degli strumenti. Nella pagina delle proprietà, l&#39;elenco dei file che fanno riferimento alla risorsa corrente viene visualizzato sotto la colonna **[!UICONTROL References]** nella scheda **[!UICONTROL Basic]**.

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Aggiungere AEM risorse come riferimenti in  Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}

Per fare riferimento AEM risorse da un file di InDesign , trascinate AEM risorse nel file  o esportate il file  InDesign come file ZIP.

Le risorse di riferimento esistono già in  AEM Assets. È possibile estrarre le risorse secondarie mediante [configurazione  server InDesign](indesign.md). Le risorse incorporate in un file InDesign  vengono estratte come risorse secondarie.

>[!NOTE]
>
>Se il server InDesign  è proxy,  file InDesign hanno la loro anteprima incorporata nei metadati XMP. In questo caso, l&#39;estrazione delle miniature non è obbligatoria in modo esplicito. Tuttavia, se il server  InDesign non è proxy, le miniature devono essere esplicitamente estratte per  file InDesign.

### Creare riferimenti Trascinando AEM risorse {#create-references-by-dragging-aem-assets}

Questa procedura è simile a [Aggiunta di risorse AEM come riferimenti in  Adobe Illustrator](#refai).

### Creare riferimenti a AEM risorse esportando un file ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Per creare un nuovo flusso di lavoro, eseguite i passaggi descritti in [Creazione di modelli di flussi di lavoro](/help/sites-developing/workflows-models.md).
1. Utilizzate la funzione Pacchetto di  Adobe InDesign per esportare il documento.
 Adobe InDesign può esportare come pacchetto un documento e le risorse collegate. In questo caso, la cartella esportata contiene una cartella Links che contiene le risorse secondarie nel file InDesign .
1. Create un file ZIP e caricatelo nell’archivio AEM.
1. Avviate il flusso di lavoro Unarchiver.
1. Al termine del flusso di lavoro, i riferimenti nella cartella Links vengono automaticamente indicati come risorse secondarie. Per visualizzare un elenco delle risorse di riferimento, andate alla pagina dei dettagli delle risorse della risorsa InDesign  e chiudete la [Barra](/help/sites-authoring/basic-handling.md#rail-selector).

## Aggiungere AEM risorse come riferimenti in  Adobe Photoshop {#refps}

1. Utilizzando un client WebDav, montate  AEM Assets come unità.
1. Per creare riferimenti a AEM risorse in un file Photoshop, individuate le risorse corrispondenti nell’unità montata mediante la funzione Inserisci collegamento di Photoshop.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. Salvate in file Photoshop sull&#39;unità montata o [caricate](managing-assets-touch-ui.md#uploading-assets) nell&#39;archivio AEM.
1. Al termine del flusso di lavoro, i riferimenti alle risorse AEM esistenti sono elencati nella pagina dei dettagli della risorsa.

   Per visualizzare le risorse di riferimento, chiudete la [Barra](/help/sites-authoring/basic-handling.md#rail-selector) nella pagina dei dettagli della risorsa.

1. Le risorse a cui viene fatto riferimento contengono anche l’elenco delle risorse a cui fanno riferimento. Per visualizzare un elenco delle risorse di riferimento, andate alla pagina dei dettagli delle risorse e chiudete la barra laterale [a1/>.](/help/sites-authoring/basic-handling.md#rail-selector)

>[!NOTE]
>
>È inoltre possibile fare riferimento alle risorse all’interno delle risorse composte in base al relativo ID documento e all’ID istanza. Questa funzionalità è disponibile solo  versioni Adobe Illustrator e  Adobe Photoshop. Per altri, il riferimento viene fatto sulla base del percorso relativo delle risorse collegate nella risorsa composta principale, come già fatto nelle versioni precedenti di AEM.

## Creare risorse secondarie {#generate-subassets}

Per le risorse supportate con formati con più pagine — File PDF, file AI, file Microsoft PowerPoint e Apple Keynote e file  Adobe InDesign — AEM generare risorse secondarie corrispondenti a ogni singola pagina della risorsa originale. Queste risorse secondarie sono collegate alla risorsa *principale* e semplificano la visualizzazione di più pagine. Per tutti gli altri scopi, le attività secondarie sono trattate come attività normali in AEM.

La generazione di risorse secondarie è disabilitata per impostazione predefinita. Per attivare la generazione di risorse secondarie, effettuate le seguenti operazioni:

1. Accedete  Experience Manager come amministratore. Accedere a **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Selezionare il flusso di lavoro **[!UICONTROL Aggiorna risorsa DAM]** e fare clic su **[!UICONTROL Modifica]**.
1. Fare clic su **[!UICONTROL Attiva/Disattiva pannello laterale]** e individuare il passaggio **[!UICONTROL Crea risorsa secondaria]**. Aggiungete il passaggio al flusso di lavoro. Fai clic su **[!UICONTROL Sincronizza]**.

Per generare le risorse secondarie, effettuate una delle seguenti operazioni:

* Nuove risorse: Il flusso di lavoro [!UICONTROL Risorse aggiornamento DAM] viene eseguito su qualsiasi nuova risorsa caricata in AEM. Le risorse secondarie vengono generate automaticamente per le nuove risorse multipagina.
* Risorse multipagina esistenti: Eseguire manualmente il flusso di lavoro [!UICONTROL DAM Update Assets] seguendo una delle seguenti procedure:

   * Selezionate una risorsa e fate clic su [!UICONTROL Timeline] per aprire il pannello a sinistra. In alternativa, utilizzare la scelta rapida da tastiera `alt + 3`. Fate clic su [!UICONTROL Avvia flusso di lavoro], selezionate [!UICONTROL Aggiorna risorsa DAM], fate clic su [!UICONTROL Avvia] e fate clic su [!UICONTROL Procedi].
   * Selezionate una risorsa e fate clic su [!UICONTROL Crea > Flusso di lavoro] nella barra degli strumenti. Dalla finestra di dialogo a comparsa, selezionate il flusso di lavoro [!UICONTROL Aggiorna risorsa DAM], fate clic su [!UICONTROL Avvia] e fate clic su [!UICONTROL Procedi].

Per i documenti di Microsoft Word, eseguire il flusso di lavoro **[!UICONTROL DAM Parse Word Documents]**. Viene generato un componente `cq:Page` dal contenuto del documento di Microsoft Word. Alle immagini estratte dal documento viene fatto riferimento dal componente `cq:Page`. Queste immagini vengono estratte anche se la generazione di risorse secondarie è disabilitata.

## Visualizza risorse secondarie {#viewing-subassets}

Le risorse secondarie vengono visualizzate solo se sono state generate delle risorse secondarie e sono disponibili per la risorsa multipagina selezionata. Per visualizzare le risorse secondarie generate, aprite la risorsa con più pagine. Nell&#39;area in alto a sinistra della pagina, fare clic su ![Icona della barra a sinistra](assets/do-not-localize/aem_leftrail_contentonly.png), quindi fare clic su **[!UICONTROL Risorse secondarie]** dall&#39;elenco. Quando si seleziona **[!UICONTROL Risorse secondarie]** dall&#39;elenco. In alternativa, utilizzare la scelta rapida da tastiera `alt + 5`.

![Visualizzare le risorse secondarie per una risorsa con più pagine](assets/view_subassets_simulation.gif)

## Visualizzare le pagine di un file con più pagine {#view-pages-of-a-multi-page-file}

Potete visualizzare un file con più pagine, ad esempio PDF, INDD, PPT, PPTX e AI, utilizzando la funzione Visualizzatore pagina di  AEM Assets. Aprite una risorsa con più pagine e fate clic su **[!UICONTROL Visualizza pagine]** nell’angolo in alto a sinistra della pagina. Il visualizzatore pagina che apre mostra le pagine della risorsa e i controlli per scorrere e ingrandire ciascuna pagina.

![Visualizzare e visualizzare le pagine di una risorsa con più pagine](assets/view_multipage_asset_fmr.gif)

Per  InDesign, è possibile estrarre le pagine utilizzando  server InDesign. Se le anteprime delle pagine vengono salvate durante  creazione di file InDesign,  InDesign Server non è necessario per l&#39;estrazione della pagina.

Le seguenti opzioni sono disponibili nella barra degli strumenti, nella barra a sinistra e nei controlli Visualizzatore pagina:

* **[!UICONTROL Azioni]** desktop per aprire o visualizzare una risorsa secondaria specifica tramite AEM&#39;app desktop. Scopri come [configurare Azioni desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#desktopactions-v2) se utilizzi AEM&#39;app desktop.

* **[!UICONTROL L’]** opzione Proprietà consente di aprire la pagina   Proprietà della risorsa secondaria specifica.

* **[!UICONTROL L’opzione]** Annota consente di aggiungere annotazioni alla risorsa secondaria specifica. Le annotazioni utilizzate in risorse secondarie separate vengono raccolte e visualizzate insieme all’apertura della risorsa principale per la visualizzazione.

* **[!UICONTROL L’opzione]** Anteprima pagina visualizza tutte le risorse secondarie contemporaneamente.

* **[!UICONTROL L&#39;opzione]** Timelineantesulla barra a sinistra dopo aver fatto clic sull&#39;icona della barra a  ![sinistra ](assets/do-not-localize/aem_leftrail_contentonly.png) mostra il flusso di attività per il file.

## Best practice e limitazioni {#best-practice-limitation-tips}

* La generazione di risorse secondarie può richiedere molte risorse per qualsiasi implementazione  Experience Manager. Se generate risorse secondarie quando vengono caricate risorse complesse, aggiungete il passaggio nel flusso di lavoro Aggiorna risorsa DAM. Se generate risorse secondarie su richiesta, create un flusso di lavoro separato per generare le risorse secondarie. Un flusso di lavoro dedicato consente di saltare gli altri passaggi del flusso di lavoro DAM Update Asset e di salvare le risorse di calcolo.

>[!MORELIKETHIS]
>
>* [Usa app desktop Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)

