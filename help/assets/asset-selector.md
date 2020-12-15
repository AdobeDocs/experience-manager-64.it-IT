---
title: Selettore risorse
description: Scoprite come usare il selettore delle risorse per cercare, filtrare, sfogliare e recuperare metadati per risorse all’interno di Adobe Experience Manager (AEM) Assets. Scoprite inoltre come personalizzare l’interfaccia del selettore delle risorse.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1de8efce9cd5cf47163cba8f0c962a9e2fc5116c
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 1%

---


# Selettore risorse {#asset-selector}

>[!NOTE]
>
>Il selettore Risorse era denominato [Selettore risorse](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) nelle versioni precedenti di AEM.

Il selettore delle risorse consente di sfogliare, cercare e filtrare le risorse in [!DNL Adobe Experience Manager] Risorse. Potete anche recuperare i metadati delle risorse selezionate mediante il selettore delle risorse. Per personalizzare l’interfaccia del selettore delle risorse, potete avviarla con i parametri di richiesta supportati. Questi parametri definiscono il contesto del selettore delle risorse per uno scenario particolare.

Attualmente, potete trasmettere i parametri di richiesta `assettype` (*Immagine/Video/Testo*) e la selezione `mode` (*Singola/Multipla*) come informazioni contestuali per il selettore delle risorse, che rimane intatto per tutta la selezione.

Il selettore delle risorse utilizza il messaggio HTML5 **Window.postMessage** per inviare al destinatario i dati per la risorsa selezionata.

Il selettore delle risorse si basa sul vocabolario del selettore base di Granite. Per impostazione predefinita, il selettore delle risorse funziona in modalità Sfoglia. Tuttavia, potete applicare i filtri utilizzando l’esperienza Omnisearch per perfezionare la ricerca di risorse particolari.

Potete integrare qualsiasi pagina Web (indipendentemente dal fatto che faccia parte del contenitore CQ) con il selettore delle risorse (`https://[AEM_server]:[port]/aem/assetpicker.html`).

## Parametri contestuali {#contextual-parameters}

Puoi trasmettere i seguenti parametri di richiesta in un URL per avviare il selettore risorse in un contesto particolare:

| Nome | Valori | Esempio | Scopo |
|---|---|---|---|
| suffisso risorsa (B) | Percorso della cartella come suffisso della risorsa nell&#39;URL:`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | Per avviare il selettore risorse con una particolare cartella selezionata, ad esempio con la cartella `/content/dam/we-retail/en/activities` selezionata, l&#39;URL deve essere del modulo: `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | Se al momento dell’avvio del selettore delle risorse è necessario selezionare una determinata cartella, passatela come suffisso di risorsa. |
| mode | singolo, multiplo | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | In modalità multipla, potete selezionare più risorse contemporaneamente utilizzando il selettore delle risorse. |
| finestra di dialogo | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | Usate questi parametri per aprire il selettore delle risorse come finestra di dialogo Granite. Questa opzione è applicabile solo quando si avvia il selettore delle risorse tramite Granite Path Field e lo si configura come URL pickerSrc. |
| root | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | Utilizzate questa opzione per specificare la cartella principale per il selettore di risorse. In questo caso, il selettore delle risorse consente di selezionare solo le risorse secondarie (dirette/indirette) sotto la cartella principale. |
| viewmode | ricerca |  | Per avviare il selettore delle risorse in modalità di ricerca, con i parametri relativi al tipo di risorsa e al tipo di mime. |
| assettype (S) | immagini, documenti, contenuti multimediali, archivi | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives`</li> | Utilizzate questa opzione per filtrare i tipi di risorse in base al valore passato. |
| mimetype | mimetype(i) (`/jcr:content/metadata/dc:format`) di una risorsa (supportati anche i caratteri jolly) | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker?viewmode=search&mimetype=*presentation&mimetype=*png`</li></ul> | Utilizzatelo per filtrare le risorse in base ai tipi MIME |

## Utilizzate il selettore delle risorse {#using-the-asset-selector}

1. Per accedere all’interfaccia del selettore delle risorse, passate a `https://[AEM_server]:[port]/aem/assetpicker`.
1. Individuate la cartella desiderata e selezionate una o più risorse.

   ![chlimage_1-441](assets/chlimage_1-441.png)

   In alternativa, potete cercare la risorsa desiderata dalla casella di ricerca Omni e selezionarla.

   ![chlimage_1-442](assets/chlimage_1-442.png)

   Se cercate risorse tramite la casella OmniSearch, potete selezionare vari filtri dal riquadro **[!UICONTROL Filtri]** per perfezionare la ricerca.

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. Toccate/fate clic su **[!UICONTROL Seleziona]** nella barra degli strumenti.
