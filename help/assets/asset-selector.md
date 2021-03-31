---
title: Selettore risorse
description: Scopri come utilizzare il selettore delle risorse per cercare, filtrare, sfogliare e recuperare metadati per le risorse in Adobe Experience Manager (AEM) Assets. Inoltre, scopri come personalizzare l’interfaccia del selettore risorse.
contentOwner: AG
feature: Gestione risorse, metadati, ricerca
role: Professionista
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---


# Selettore risorse {#asset-selector}

>[!NOTE]
>
>Il selettore Risorsa era denominato [Selettore risorse](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) nelle versioni precedenti di AEM.

Il selettore delle risorse consente di sfogliare, cercare e filtrare le risorse in [!DNL Adobe Experience Manager] Risorse. Puoi anche recuperare i metadati delle risorse selezionate utilizzando il selettore delle risorse. Per personalizzare l’interfaccia del selettore risorse, puoi avviarla con i parametri di richiesta supportati. Questi parametri impostano il contesto del selettore delle risorse per un particolare scenario.

Attualmente, puoi trasmettere i parametri di richiesta `assettype` (*Immagine/Video/Testo*) e la selezione `mode` (*Singola/Multipla*) come informazioni contestuali per il selettore delle risorse, che rimane intatto durante l’intera selezione.

Il selettore delle risorse utilizza il messaggio HTML5 **Window.postMessage** per inviare i dati della risorsa selezionata al destinatario.

Il selettore delle risorse si basa sul vocabolario del selettore delle risorse di Granite. Per impostazione predefinita, il selettore delle risorse funziona in modalità Sfoglia. Tuttavia, puoi applicare i filtri utilizzando l’esperienza Omnisearch per perfezionare la ricerca di risorse particolari.

Puoi integrare qualsiasi pagina web (indipendentemente dal fatto che faccia parte del contenitore CQ) con il selettore delle risorse (`https://[AEM_server]:[port]/aem/assetpicker.html`).

## Parametri contestuali {#contextual-parameters}

Puoi trasmettere i seguenti parametri di richiesta in un URL per avviare il selettore risorse in un particolare contesto:

| Nome | Valori | Esempio | Scopo |
|---|---|---|---|
| suffisso risorsa (B) | Percorso cartella come suffisso di risorsa nell&#39;URL:`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | Per avviare il selettore risorse con una particolare cartella selezionata, ad esempio con la cartella `/content/dam/we-retail/en/activities` selezionata, l’URL deve essere del modulo: `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | Se devi selezionare una particolare cartella all’avvio del selettore delle risorse, passala come suffisso di risorsa. |
| modalità | singolo, multiplo | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | In modalità multipla, puoi selezionare più risorse contemporaneamente utilizzando il selettore delle risorse. |
| finestra di dialogo | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | Utilizza questi parametri per aprire il selettore delle risorse come finestra di dialogo Granite. Questa opzione è applicabile solo quando si avvia il selettore risorse tramite il campo del percorso Granite e lo si configura come URL pickerSrc. |
| root | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | Utilizza questa opzione per specificare la cartella principale per il selettore di risorse. In questo caso, il selettore delle risorse consente di selezionare solo le risorse secondarie (dirette/indirette) sotto la cartella principale. |
| viewmode | ricerca |  | Per avviare il selettore delle risorse in modalità di ricerca, con parametri di tipo risorsa e mimetype. |
| asset (S) | immagini, documenti, multimedia, archivi | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives`</li> | Utilizza questa opzione per filtrare i tipi di risorse in base al valore passato. |
| mimetype | mimetype(i) (`/jcr:content/metadata/dc:format`) di una risorsa (supportato anche da caratteri jolly) | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker?viewmode=search&mimetype=*presentation&mimetype=*png`</li></ul> | Utilizzalo per filtrare le risorse in base ai tipi MIME |

## Utilizza il selettore risorse {#using-the-asset-selector}

1. Per accedere all’interfaccia del selettore risorse, passa a `https://[AEM_server]:[port]/aem/assetpicker`.
1. Individua la cartella desiderata e seleziona una o più risorse.

   ![chlimage_1-441](assets/chlimage_1-441.png)

   In alternativa, è possibile cercare la risorsa desiderata dalla casella OmniSearch, quindi selezionarla.

   ![chlimage_1-442](assets/chlimage_1-442.png)

   Se cerchi risorse utilizzando la casella OmniSearch, puoi selezionare vari filtri dal riquadro **[!UICONTROL Filtri]** per perfezionare la ricerca.

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. Tocca o fai clic su **[!UICONTROL Seleziona]** nella barra degli strumenti.
