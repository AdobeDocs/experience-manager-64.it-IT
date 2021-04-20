---
title: Utilizzo del componente Siti 3D
seo-title: Utilizzo del componente Siti 3D
description: AEM 3D include un componente AEM Sites che può essere utilizzato per implementare la visualizzazione interattiva dei modelli 3D sulle pagine web.
seo-description: AEM 3D include un componente AEM Sites che può essere utilizzato per implementare la visualizzazione interattiva dei modelli 3D sulle pagine web.
uuid: 4f06bab3-1e31-49ef-89e3-b26195966538
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 9017ab55-6d4a-4306-922f-223ab1b2504b
exl-id: bf87b470-08c8-44b4-95d9-1251586b0610
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# Utilizzo del componente Siti 3D {#working-with-the-d-sites-component}

AEM 3D include un componente AEM Sites che può essere utilizzato per implementare la visualizzazione interattiva dei modelli 3D sulle pagine web.

Dopo aver aggiunto il componente 3D, puoi [visualizzare la risorsa 3D in quel componente.](viewing-3d-assets.md)

## Aggiunta del componente 3D al modello di pagina {#adding-the-d-component-to-the-page-template}

È necessario attivare il componente 3D nella pagina prima di poterlo posizionare su una pagina. Consulta [Modifica di modelli](/help/sites-authoring/templates.md#editing-a-template-layout-template-author) per informazioni dettagliate sull&#39;abilitazione dei componenti nei modelli.

**Aggiunta del componente 3D al modello** di pagina:

1. Passa a **[!UICONTROL Strumenti > Generale > Modelli]**.

1. Passa al modello di pagina in cui desideri abilitare il componente 3D e seleziona il modello.

1. Tocca **[!UICONTROL Modifica]** per aprire il modello.
1. Vicino all’angolo superiore destro della pagina, nel menu a discesa selezionare la modalità **[!UICONTROL Struttura]** , se non è già attiva.

   ![image2017-11-14_15-33-57](assets/image2017-11-14_15-33-57.png)

1. Toccare l’area **[!UICONTROL Contenitore di layout]** per selezionarla.

1. Tocca il pulsante **[!UICONTROL Policy]** per aprire l&#39; **[!UICONTROL Editor criteri]**.
1. Nella sezione **[!UICONTROL Proprietà]**, seleziona il segno di spunta **[!UICONTROL 3D]**, quindi tocca **[!UICONTROL Fine]** per salvare le modifiche e chiudere l&#39; **[!UICONTROL Editor criteri]**.

   Ora puoi posizionare il componente Siti 3D su tutte le pagine che utilizzano questo modello.

## Aggiunta del componente visualizzatore 3D a una pagina web {#adding-the-d-viewer-component-to-a-web-page}

>[!CAUTION]
>
>Questa versione di AEM 3D supporta una sola istanza del componente 3D su ogni pagina web. Più componenti 3D sulla stessa pagina non funzionano correttamente.

**Per aggiungere un componente visualizzatore 3D a una pagina** web:

1. Apri AEM Sites e seleziona la pagina web alla quale desideri aggiungere il componente 3D.

1. Tocca l’icona **[!UICONTROL Modifica]** (matita) per aprire la pagina nell’editor di pagine. Assicurati che sia selezionata la modalità **[!UICONTROL Modifica]** vicino alla pagina in alto a destra.

   ![image2017-11-14_15-44-40](assets/image2017-11-14_15-44-40.png)

1. Toccate il selettore della barra per aprire il pannello laterale.

1. Tocca l’icona del segno più per aprire l’elenco **[!UICONTROL Componenti]** .

1. Trascina il componente **[!UICONTROL Visualizzatore 3D]** dall’elenco **[!UICONTROL Componenti]** nella posizione nella pagina in cui desideri visualizzare il visualizzatore 3D.

## Configurazione del componente 3D {#configuring-the-d-component}

1. Nell’editor pagina di AEM Sites, seleziona il componente **[!UICONTROL Visualizzatore 3D]** che hai aggiunto in precedenza alla pagina.

1. Toccare l&#39;icona **[!UICONTROL Configurazione]** (chiave inglese) per aprire la finestra di dialogo di configurazione del componente.

   Puoi impostare le seguenti proprietà del componente:

   <table> 
    <tbody> 
    <tr> 
    <td>Proprietà</td> 
    <td>Descrizione</td> 
    <td>Applicabilità</td> 
    </tr> 
    <tr> 
    <td>Altezza (px)</td> 
    <td>Specifica l’altezza desiderata in pixel del componente 3D. Se lasciato vuoto, il valore predefinito è 600 pixel.</td> 
    <td> </td> 
    </tr> 
    <tr> 
    <td>Nome della fase</td> 
    <td><p>Selezionare uno stage 3D dall'elenco degli stadi disponibili. Lo stage fornisce sfondo e illuminazione.</p> <p>Consulta <a href="/help/assets/about-the-use-of-stages-in-aem-3d.md" target="_blank">Informazioni sull'utilizzo delle aree di visualizzazione in AEM siti 3D</a>.</p> </td> 
    <td>Ignorato per le risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Velocità di rotazione automatica (RPM)</td> 
    <td><p>Il visualizzatore 3D orbita continuamente la telecamera dopo il caricamento e resetta. La rotazione automatica termina quando l’utente avvia un’azione orbitale manuale.</p> <p>È possibile specificare la velocità di rotazione in giri/min utilizzando i seguenti valori:</p> 
        <ul> 
        <li>Imposta un valore positivo per la rotazione a destra</li> 
        <li>Imposta un valore negativo per girare a sinistra</li> 
        <li>Imposta un valore 0 per disattivare la rotazione automatica.</li> 
        </ul> <p>Il valore predefinito è 3 RPM, pari a 20 secondi per rivoluzione completa.<br /> <br /> <strong>Nota:</strong> la velocità di centrifuga presuppone un frame rate di 60/sec. Questo tasso viene generalmente raggiunto con modelli di piccole e medie dimensioni su hardware grafico più potente. Modelli più grandi o dispositivi più lenti con rotazione automatica a velocità più basse.</p> </td> 
    <td>Ignorato per le risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Colore pulsante di navigazione</td> 
    <td>Utilizza il selettore colore per scegliere il colore primario per i pulsanti di controllo del visualizzatore.</td> 
    <td>Ignorato per le risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Colore puntatore del mouse di navigazione</td> 
    <td>Utilizza il selettore colore per scegliere il colore al passaggio del mouse/selezionato per i pulsanti di controllo del visualizzatore.</td> 
    <td>Ignorato per le risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Mostra campioni</td> 
    <td>Per utilizzi futuri.</td> 
    <td>Ignorato per le risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Mostra impostazioni fotocamera GLTF</td> 
    <td>Mostra o nasconde i predefiniti per telecamere eventualmente presenti nelle risorse di Adobe Dimension.</td> 
    <td>Solo per risorse Adobe Dimension.</td> 
    </tr> 
    <tr> 
    <td>Colore di sfondo GLTF</td> 
    <td>Colore di sfondo predefinito se il modello 3D non include uno sfondo.</td> 
    <td>Solo per risorse Adobe Dimension.</td> 
    </tr> 
    </tbody> 
   </table>

1. Tocca il segno di spunta per salvare le modifiche.

   Oltre alle impostazioni disponibili nella finestra di dialogo di configurazione del componente, sono disponibili diverse impostazioni di configurazione globali che possono essere modificate tramite CRXDE Lite.
Consulta [Impostazioni di configurazione avanzate](advanced-config-3d.md) per informazioni dettagliate su queste impostazioni globali.

## Assegnazione di un modello 3D al componente {#assigning-a-d-model-to-the-component}

1. Nell’editor pagina di AEM Sites, fai clic sull’icona **[!UICONTROL Risorse]** per aprire l’elenco Risorse nel pannello laterale.

1. Seleziona il filtro **[!UICONTROL Modelli 3D]** per nascondere i tipi di risorse indesiderati.

   ![screen_shot_2017-12-11at124258](assets/screen_shot_2017-12-11at124258.png)

1. Cerca o scorri fino alla risorsa 3D che desideri visualizzare nella pagina da modificare.

1. Trascina la risorsa 3D dall’elenco **[!UICONTROL Risorse]** al componente **[!UICONTROL Visualizzatore 3D]** precedentemente inserito nella pagina.

   Le risorse Adobe Dimension vengono sottoposte a rendering utilizzando la nuova tecnologia di visualizzatore basata sullo standard aperto glTF, mentre tutti gli altri tipi di risorse 3D si basano sul classico visualizzatore webGL AEM 3D. Il componente seleziona automaticamente il visualizzatore appropriato in base al tipo di modello 3D.

## Anteprima di una pagina web con un componente 3D {#previewing-a-web-page-that-has-a-d-component}

Mentre la pagina web è in modalità **[!UICONTROL Modifica]**, il componente 3D visualizza il modello 3D ma non è possibile alcuna interazione con il modello.

Puoi visualizzare in anteprima la pagina web nell’editor di pagine con accesso completo alle funzionalità del componente 3D.

Vedi anche [Visualizzazione delle risorse 3D nel componente 3D di Sites](viewing-3d-assets.md#viewing-d-assets-in-the-sites-d-component).

**Per visualizzare in anteprima una pagina web con un componente** 3D:

1. Effettua una delle seguenti operazioni:

   * Fai clic su **[!UICONTROL Anteprima]** in alto a destra per accedere alla modalità di anteprima.
   * Elimina `/edit.html` dall’URL della pagina nel browser.

## Pubblicazione della pagina e delle risorse {#publishing-the-page-and-assets}

Per informazioni su come pubblicare le risorse, consulta [Pubblicazione delle risorse](managing-assets-touch-ui.md) . Per informazioni su come pubblicare le pagine, consulta [Pubblicazione di pagine](/help/sites-authoring/publishing-pages.md) .

>[!NOTE]
>
>Utilizzando la voce di menu **[!UICONTROL Pubblica pagina]** nel menu **[!UICONTROL Informazioni pagina]** verrà pubblicata la pagina e tutte le dipendenze principali della pagina. Le dipendenze secondarie a cui può fare riferimento il modello 3D e/o lo stadio 3D, come le mappe di texture e le immagini IBL, non vengono pubblicate quando la pagina viene pubblicata in questo modo.
>
>Adobe consiglia di pubblicare tutte le risorse 3D e le relative dipendenze direttamente da AEM Assets, prima di pubblicare la pagina web che fa riferimento a tali risorse.
