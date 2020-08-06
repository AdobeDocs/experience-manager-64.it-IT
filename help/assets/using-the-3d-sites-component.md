---
title: Utilizzo del componente Siti 3D
seo-title: Utilizzo del componente Siti 3D
description: AEM 3D include un componente AEM Sites  che può essere utilizzato per implementare la visualizzazione interattiva dei modelli 3D sulle pagine Web.
seo-description: AEM 3D include un componente AEM Sites  che può essere utilizzato per implementare la visualizzazione interattiva dei modelli 3D sulle pagine Web.
uuid: 4f06bab3-1e31-49ef-89e3-b26195966538
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 9017ab55-6d4a-4306-922f-223ab1b2504b
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 0%

---


# Utilizzo del componente Siti 3D {#working-with-the-d-sites-component}

AEM 3D include un componente AEM Sites  che potete utilizzare per implementare la visualizzazione interattiva dei modelli 3D sulle pagine Web.

Dopo aver aggiunto il componente 3D, puoi [visualizzare la risorsa 3D in quel componente.](viewing-3d-assets.md)

## Aggiunta del componente 3D al modello di pagina {#adding-the-d-component-to-the-page-template}

È necessario abilitare il componente 3D nella pagina prima di posizionarlo su una pagina. Consultate [Modifica dei modelli](/help/sites-authoring/templates.md#editing-a-template-layout-template-author) per informazioni dettagliate sull&#39;abilitazione dei componenti nei modelli.

**Aggiunta del componente 3D al modello** di pagina:

1. Selezionare **[!UICONTROL Strumenti > Generale > Modelli]**.

1. Individuate il modello di pagina in cui desiderate abilitare il componente 3D e selezionatelo.

1. Toccate **[!UICONTROL Modifica]** per aprire il modello.
1. Vicino alla parte superiore destra della pagina, nel menu a discesa, selezionate **[!UICONTROL Struttura]** , se non è già attiva.

   ![image2017-11-14_15-33-57](assets/image2017-11-14_15-33-57.png)

1. Toccate l&#39;area Contenitore **[!UICONTROL di]** layout per selezionarla.

1. Toccate il pulsante **[!UICONTROL Criterio]** per aprire l&#39;Editor **** criteri.
1. Nella sezione **[!UICONTROL Proprietà]** , selezionare il segno di spunta **[!UICONTROL 3D]** , quindi toccare **[!UICONTROL Fine]** per salvare le modifiche e chiudere l&#39;Editor **** criteri.

   Ora puoi posizionare il componente Siti 3D su tutte le pagine che utilizzano questo modello.

## Aggiunta del componente visualizzatore 3D a una pagina Web {#adding-the-d-viewer-component-to-a-web-page}

>[!CAUTION]
>
>Questa versione di AEM 3D supporta solo un’istanza del componente 3D in ogni pagina Web. Più componenti 3D sulla stessa pagina non funzionano correttamente.

**Per aggiungere il componente visualizzatore 3D a una pagina** Web:

1. Aprite  AEM Sites e selezionate la pagina Web alla quale desiderate aggiungere il componente 3D.

1. Toccate l’icona **[!UICONTROL Modifica]** (matita) per aprire la pagina nell’editor pagina. Accertatevi che sia selezionata la modalità **[!UICONTROL Modifica]** in alto a destra della pagina.

   ![image2017-11-14_15-44-40](assets/image2017-11-14_15-44-40.png)

1. Toccate il selettore della barra per aprire il pannello laterale.

1. Toccate l&#39;icona più per aprire l&#39;elenco **[!UICONTROL Componenti]** .

1. Trascinate il componente Visualizzatore **** 3D dall’elenco **[!UICONTROL Componenti]** alla posizione nella pagina in cui desiderate visualizzare il visualizzatore 3D.

## Configurazione del componente 3D {#configuring-the-d-component}

1. Nell’editor  pagina di AEM Sites, selezionate il componente Visualizzatore **** 3D precedentemente aggiunto alla pagina.

1. Toccate l&#39;icona **[!UICONTROL Configurazione]** (chiave inglese) per aprire la finestra di dialogo di configurazione del componente.

   È possibile impostare le seguenti proprietà del componente:

   <table> 
    <tbody> 
    <tr> 
    <td>Proprietà</td> 
    <td>Descrizione</td> 
    <td>Applicabilità</td> 
    </tr> 
    <tr> 
    <td>Altezza (px)</td> 
    <td>Specificate l’altezza desiderata del componente 3D in pixel. Se lasciato vuoto, il valore predefinito è 600 pixel.</td> 
    <td> </td> 
    </tr> 
    <tr> 
    <td>Nome stage</td> 
    <td><p>Selezionare uno stage 3D dall'elenco delle fasi disponibili. L’area di visualizzazione fornisce informazioni sullo sfondo e l’illuminazione.</p> <p>See <a href="/help/assets/about-the-use-of-stages-in-aem-3d.md" target="_blank">About the use of stages in AEM 3D Sites</a>.</p> </td> 
    <td>Ignorato per  risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Velocità di rotazione automatica (RPM)</td> 
    <td><p>Il visualizzatore 3D orbita continuamente attorno alla telecamera dopo il caricamento e la reimpostazione. La rotazione automatica termina quando l'utente avvia un'azione di orbita manuale.</p> <p>È possibile specificare la velocità di rotazione in RPM utilizzando i seguenti valori:</p> 
        <ul> 
        <li>Imposta un valore positivo per la rotazione a destra</li> 
        <li>Imposta un valore negativo per la rotazione a sinistra</li> 
        <li>Impostate un valore 0 per disattivare la rotazione automatica.</li> 
        </ul> <p>Il valore predefinito è 3 RPM, pari a 20 secondi per ogni rivoluzione completa.<br /> <br /> <strong>Nota:</strong> La velocità di centrifuga si basa su un frame rate di 60/sec. Questo tasso viene generalmente raggiunto con modelli di piccole e medie dimensioni su hardware grafico più potente. Modelli più grandi o dispositivi più lenti eseguono la rotazione automatica a velocità più basse.</p> </td> 
    <td>Ignorato per  risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Colore pulsante di navigazione</td> 
    <td>Usate il selettore colore per scegliere il colore principale per i pulsanti di controllo del visualizzatore.</td> 
    <td>Ignorato per  asini Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Colore passaggio del mouse per la navigazione</td> 
    <td>Usate il selettore colore per scegliere il colore al passaggio del mouse o selezionato per i pulsanti di controllo del visualizzatore.</td> 
    <td>Ignorato per  risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Mostra campioni</td> 
    <td>Per utilizzi futuri.</td> 
    <td>Ignorato per  risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Mostra predefiniti per telecamere GLTF</td> 
    <td>Mostra o nasconde i predefiniti per telecamere eventualmente presenti  risorse Adobe Dimension.</td> 
    <td>Solo per  risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Colore di sfondo GLTF</td> 
    <td>Colore di sfondo predefinito se il modello 3D non include uno sfondo.</td> 
    <td>Solo per  risorse Adobe Dimension.</td> 
    </tr> 
    </tbody> 
   </table>

1. Toccate il segno di spunta per salvare le modifiche.

   Oltre alle impostazioni disponibili nella finestra di dialogo di configurazione del componente, sono disponibili diverse impostazioni di configurazione globali che possono essere modificate dal CRXDE Lite.
Per informazioni dettagliate su queste impostazioni globali, consultate Impostazioni [di configurazione](advanced-config-3d.md) avanzate.

## Assegnazione di un modello 3D al componente {#assigning-a-d-model-to-the-component}

1. Nell’editor  pagina AEM Sites, fai clic sull’icona **[!UICONTROL Risorse]** per aprire l’elenco Risorse nel pannello laterale.

1. Selezionate il filtro Modelli **** 3D per nascondere i tipi di risorse indesiderati.

   ![screen_shot_2017-12-11at124258](assets/screen_shot_2017-12-11at124258.png)

1. Cercate o scorrete fino alla risorsa 3D che desiderate visualizzare sulla pagina da modificare.

1. Trascinate la risorsa 3D dall’elenco **[!UICONTROL Risorse]** al componente Visualizzatore **** 3D precedentemente inserito nella pagina.

    le risorse Adobe Dimension vengono sottoposte a rendering con la nuova tecnologia di visualizzatore basata sullo standard aperto glTF, mentre tutti gli altri tipi di risorse 3D si basano sul visualizzatore WebGL AEM classico. Il componente seleziona automaticamente il visualizzatore appropriato in base al tipo di modello 3D.

## Anteprima di una pagina Web con un componente 3D {#previewing-a-web-page-that-has-a-d-component}

Mentre la pagina Web è in modalità **[!UICONTROL Modifica]** , il componente 3D visualizza il modello 3D ma non è possibile interagire con il modello.

È possibile visualizzare l’anteprima della pagina Web nell’editor pagina con accesso completo alle funzionalità del componente 3D.

Consultate anche [Visualizzazione di risorse 3D nel componente](viewing-3d-assets.md#viewing-d-assets-in-the-sites-d-component)Siti 3D.

**Per visualizzare in anteprima una pagina Web con un componente** 3D:

1. Effettuate una delle seguenti operazioni:

   * Nella parte superiore destra della pagina, fate clic su **[!UICONTROL Anteprima]** per passare alla modalità di anteprima.
   * Elimina `/edit.html` dall’URL della pagina nel browser.

## Pubblicazione di pagina e risorse {#publishing-the-page-and-assets}

Consultate [Pubblicazione delle risorse](managing-assets-touch-ui.md) per informazioni su come pubblicare le risorse. Consultate [Pubblicazione di pagine](/help/sites-authoring/publishing-pages.md) per informazioni su come pubblicare le pagine.

>[!NOTE]
>
>L’utilizzo della voce di menu **[!UICONTROL Pubblica pagina]** nel menu Informazioni **** pagina consente di pubblicare la pagina e tutte le dipendenze della pagina principale. Le dipendenze secondarie a cui può fare riferimento il modello 3D e/o l’area di visualizzazione 3D, come mappe di texture e immagini IBL, non vengono pubblicate quando si pubblica la pagina in questo modo.
>
> Adobe consiglia di pubblicare tutte le risorse 3D e le relative dipendenze direttamente da  AEM Assets, prima di pubblicare la pagina Web che fa riferimento a tali risorse.

