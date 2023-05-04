---
title: Frammenti di esperienza
seo-title: Experience Fragments
description: Frammenti di esperienza
seo-description: null
uuid: be1aceef-eb6e-47e5-a920-be5cc6de6191
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 1fe58af0-3005-46fc-8717-5d32557947ed
exl-id: 8906b3ab-cb08-4b3e-8796-334e36b1e491
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 52%

---

# Frammenti di esperienza{#experience-fragments}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Un frammento esperienza è un gruppo di uno o più componenti, compresi contenuto e layout, a cui è possibile fare riferimento all’interno delle pagine. Possono contenere qualsiasi componente.

Un Frammento Esperienza:

* Fa parte di un’esperienza (pagina).
* Può essere utilizzato su più pagine.
* Si basa su un modello (solo modificabile) per definire struttura e componenti.
* È costituito da uno o più componenti, con layout, in un sistema paragrafo.
* Può contenere altri frammenti di esperienza.
* Può essere combinato con altri componenti (inclusi altri frammenti esperienza) per formare una pagina completa (esperienza).
* Può avere diverse varianti, che possono condividere contenuti e/o componenti.
* Può essere suddiviso in blocchi predefiniti che possono essere utilizzati in più varianti del frammento.

Puoi utilizzare Frammenti esperienza:

* Se un autore desidera riutilizzare parti (un frammento di un’esperienza) di una pagina, deve copiare e incollare tale frammento. Creare e gestire queste esperienze di copia/incolla richiede tempo e può essere fonte di errori da parte dell’utente. Grazie a Frammenti esperienza non è più necessario eseguire operazioni di copia/incolla.
* Per supportare il caso d’uso del CMS headless. Gli autori intendono utilizzare AEM solo per l’authoring, ma non per la distribuzione al cliente. Un sistema o punto di contatto di terze parti potrebbe prendere in carico questa particolare esperienza e in seguito trasmetterla all’utente finale.

>[!NOTE]
>
>Per poter accedere in scrittura ai frammenti esperienza, l’account utente deve essere registrato nel gruppo
>
>`experience-fragments-editors`
>
>In caso di problemi, contatta l’amministratore di sistema.

## Quando utilizzare i frammenti esperienza?   {#when-should-you-use-experience-fragments}

I frammenti esperienza sono indicati nei seguenti casi:

* Quando desideri riutilizzare le esperienze.

   * Per esperienze che riutilizzerai con contenuti simili o uguali. 

* Quando utilizzi AEM come piattaforma di distribuzione di contenuti per terze parti.

   * Per qualsiasi soluzione che utilizza AEM come piattaforma di distribuzione di contenuti. 
   * Per incorporare contenuti nei punti di contatto di terze parti

* Se usi un’esperienza con diverse varianti o rappresentazioni.

   * Varianti per un canale o per un contesto specifico. 
   * Esperienze che è utile raggruppare (ad esempio una campagna con diverse esperienze tra i vari canali)

* Quando utilizzi Commerce omnichannel.

   * Per condividere contenuti commerciali sui canali di social media su larga scala
   * Per assegnare funzioni transazionali ai punti di contatto

## Organizzazione dei frammenti esperienza {#organizing-your-experience-fragments}

È consigliabile:
* organizzare i frammenti esperienza in cartelle;

* [configurare i modelli consentiti in queste cartelle](#configure-allowed-templates-folder).

La creazione di cartelle consente di:

* creare una struttura significativa per i frammenti esperienza, ad esempio, in base alla classificazione

   >[!NOTE]
   >
   >Non è necessario allineare la struttura dei frammenti esperienza alla struttura delle pagine del sito.

* [allocare i modelli consentiti a livello di cartella](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >Per creare un modello personalizzato, puoi utilizzare [l’editor modelli](/help/sites-authoring/templates.md).

L’esempio seguente mostra Frammenti esperienza strutturati in base a `Contributors`. La struttura utilizzata illustra anche come utilizzare altre funzioni, come la gestione multisito (incluse le copie per lingua).

>[!CAUTION]
>
>La schermata seguente è stata scattata dal sito WKND utilizzando Adobe Experience Manager as a Cloud Service.

![Cartelle per i frammenti esperienza](assets/xf-folders.png)

## Creazione e configurazione di una cartella per i frammenti esperienza {#creating-and-configuring-a-folder-for-your-experience-fragments}

Per creare e configurare una cartella per i frammenti esperienza, è consigliabile:

1. [Creare una cartella](/help/sites-authoring/managing-pages.md#creating-a-new-folder).

1. [Configurare i modelli di frammento esperienza consentiti per la cartella](#configure-allowed-templates-folder).

>[!NOTE]
>
>È inoltre possibile configurare il [Modelli consentiti per la tua istanza](#configure-allowed-templates-instance), ma questo metodo è **not** consigliato in quanto i valori possono essere sovrascritti in seguito a un aggiornamento.

### Configurare i modelli consentiti per la cartella {#configure-allowed-templates-folder}

>[!NOTE]
>
>Si tratta del metodo consigliato per specificare i **[!UICONTROL modelli consentiti]**, poiché i valori non verranno sovrascritti in seguito a un aggiornamento.

1. Individua la cartella **[!UICONTROL Frammenti esperienza]** necessaria.

1. Seleziona la cartella e quindi **[!UICONTROL Proprietà]**.

1. Specifica l’espressione regolare per recuperare i modelli richiesti nel campo **[!UICONTROL Modelli consentiti]**.

   Esempio:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   ![Proprietà dei frammenti esperienza - Modelli consentiti](assets/xf-folders-templates.png)

1. Seleziona **[!UICONTROL Salva e chiudi]**.

### Configurare i modelli consentiti per l’istanza {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Si sconsiglia di modificare il **[!UICONTROL Modelli consentiti]** con questo metodo, in quanto i modelli specificati potrebbero essere sovrascritti in seguito a un aggiornamento.
>
>Utilizza questa finestra di dialogo solo a scopo informativo.

1. Individua la console **[!UICONTROL Frammenti esperienza]** necessaria.

1. Seleziona le **[!UICONTROL opzioni di configurazione]**:

   ![Pulsante Configurazione](assets/xf-folders-18.png)

1. Specifica i modelli richiesti nella finestra di dialogo **[!UICONTROL Configura frammenti esperienza]**:

   ![Configura frammenti esperienza](assets/xf-folders-19.png)

1. Seleziona **[!UICONTROL Salva]**.

## Creazione di un frammento esperienza {#creating-an-experience-fragment}

Per creare un frammento esperienza:

1. Seleziona **[!UICONTROL Frammenti esperienza]** nel pannello di navigazione globale.

   ![screen_shot_2018-04-05at92221am1](assets/screen_shot_2018-04-05at92221am1.png)

1. Individua la cartella desiderata e seleziona **[!UICONTROL Crea]**.

1. Seleziona **[!UICONTROL Frammento esperienza]** per aprire la procedura guidata **[!UICONTROL Crea frammento esperienza]**.

   Seleziona il **[!UICONTROL modello]** appropriato, quindi **[!UICONTROL Avanti]**:

   ![xf-authoring-02](assets/xf-authoring-02.png)


1. Inserisci le **[!UICONTROL proprietà]** per il frammento esperienza.

   A **[!UICONTROL Titolo]** è obbligatorio. Se la **[!UICONTROL Nome]** viene lasciato vuoto e viene derivato da **[!UICONTROL Titolo]**.

   ![xf-authoring-03](assets/xf-authoring-03.png)

1. Fai clic su **[!UICONTROL Crea]**.

   Verrà visualizzato un messaggio. Seleziona:

   * **[!UICONTROL Fine]** per tornare alla console
   * **[!UICONTROL Apri]** per aprire l’editor frammenti

## Modifica del frammento esperienza {#editing-your-experience-fragment}

L’Editor frammento esperienza offre funzionalità simili al normale Editor pagina. Vedi [Modifica del contenuto di una pagina](/help/sites-authoring/editing-content.md) per ulteriori informazioni su come utilizzarlo.

L’esempio seguente illustra come creare un teaser per un prodotto:

1. Trascina e rilascia una **[!UICONTROL Teaser per categorie]** dal [Browser Componenti](/help/sites-authoring/author-environment-tools.md#components-browser).

   ![xf-authoring-04](assets/xf-authoring-04.png)

1. Seleziona **[[!UICONTROL Configura]](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)** dalla barra degli strumenti del componente.
1. Aggiungi la **[!UICONTROL Risorsa]** e definisci le **[!UICONTROL Proprietà]** secondo le esigenze.
1. Conferma le definizioni con **[!UICONTROL Fine]** (icona di spunta).
1. Aggiungi altri componenti in base alle esigenze.

## Creazione di una variante del frammento esperienza {#creating-an-experience-fragment-variation}

Puoi creare varianti del frammento esperienza, a seconda delle tue esigenze:

1. Apri il frammento per [modifica](/help/sites-authoring/experience-fragments.md#editing-your-experience-fragment).
1. Apri la scheda **[!UICONTROL Varianti]**.

   ![xf-authoring-06](assets/xf-authoring-06.png)

1. **Crea** consente di creare:

   * **[!UICONTROL Variazione]**
   * **[!UICONTROL Variante come Live Copy]**.

1. Definisci le proprietà richieste:

   * **[!UICONTROL Modello]**
   * **[!UICONTROL Titolo]**
   * **[!UICONTROL Nome]**; se lasciato vuoto, verrà derivato dal campo Titolo
   * **[!UICONTROL Descrizione]**
   * **[!UICONTROL Tag varianti]**

   ![xf-authoring-07](assets/xf-authoring-07.png)

1. Conferma con **[!UICONTROL Fine]** (icona di spunta), la nuova variante verrà visualizzata nel pannello:

   ![xf-authoring-08](assets/xf-authoring-08.png)

## Utilizzo del frammento esperienza {#using-your-experience-fragment}

È ora possibile utilizzare il Frammento esperienza durante la creazione delle pagine:

1. Apri una pagina qualsiasi per la modifica.

   Ad esempio: [http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html)

1. Crea un’istanza del componente Frammento esperienza trascinandolo dal browser Componenti al sistema di paragrafi della pagina:

   ![xf-authoring-09](assets/xf-authoring-09.png)

1. Aggiungi il frammento esperienza effettivo all’istanza del componente, eseguendo una delle seguenti operazioni:

   * Trascina il frammento richiesto dal browser Risorse e rilascialo nel componente
   * Seleziona **[!UICONTROL Configura]** dalla barra degli strumenti del componente e specifica il frammento da utilizzare, quindi conferma con **Fine** (segno di spunta)

   ![xf-authoring-10](assets/xf-authoring-10.png)

   >[!NOTE]
   >
   >L’opzione Modifica, nella barra degli strumenti del componente, funziona come una scelta rapida per aprire il frammento nell’editor frammenti.

## Blocchi predefiniti {#building-blocks}

Puoi selezionare uno o più componenti per creare un blocco predefinito da riutilizzare nel frammento:

### Creazione di un blocco predefinito {#creating-a-building-block}

Per creare un nuovo blocco predefinito:

1. Nell’editor Frammento esperienza, seleziona i componenti che desideri riutilizzare:

   ![xf-authoring-12](assets/xf-authoring-12.png)

1. Dalla barra degli strumenti Componenti, seleziona **[!UICONTROL Converti in blocco predefinito]**:

   ![xf-authoring-13-icon](assets/xf-authoring-13-icon.png)

   Ad esempio:

   ![xf-authoring-13](assets/xf-authoring-13.png)

1. Inserisci il nome del **[!UICONTROL blocco predefinito]** e conferma con **[!UICONTROL Converti]**:

   ![xf-authoring-14](assets/xf-authoring-14.png)

1. Il **Blocco predefinito** viene visualizzato nella scheda e può essere selezionato nel sistema paragrafo:

   ![xf-authoring-15](assets/xf-authoring-15.png)

### Gestione di un blocco predefinito {#managing-a-building-block}

Il blocco predefinito è visibile nel **[!UICONTROL Blocchi predefiniti]** scheda . Per ogni blocco sono disponibili le seguenti azioni:

* Vai a principale: apre la variante principale in una nuova scheda
* Rinomina
* Eliminare

![xf-authoring-16](assets/xf-authoring-16.png)

### Utilizzo di un blocco predefinito {#using-a-building-block}

Puoi trascinare il blocco predefinito nel sistema di paragrafi di qualsiasi frammento, come un qualsiasi altro componente.

## Rendering HTML semplice {#the-plain-html-rendition}

Utilizzo della `.plain.` nell’URL, puoi accedere al rendering semplice di HTML.

Questo è disponibile dal browser, ma il suo scopo principale è quello di consentire ad altre applicazioni (ad esempio, applicazioni web di terze parti, implementazioni mobili personalizzate) di accedere direttamente al contenuto del frammento esperienza, utilizzando solo l’URL.

Il rendering HTML semplice aggiunge il protocollo, l&#39;host e il percorso contestuale a percorsi che sono:

* del tipo: `src`, `href`oppure `action`

* o termina con: `-src`oppure `-href`

Ad esempio:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>I collegamenti fanno sempre riferimento all’istanza di pubblicazione. Sono destinati a essere utilizzati da terze parti, pertanto il collegamento verrà sempre chiamato dall’istanza di pubblicazione, non dall’autore.

![xf-authoring-17](assets/xf-authoring-17.png)

## Esportazione di frammenti esperienza   {#exporting-experience-fragments}

Per impostazione predefinita, i frammenti esperienza vengono consegnati nel formato HTML. Può essere utilizzato sia da canali AEM che di terze parti.

Per l’esportazione in Adobe Target, viene utilizzato HTML. Vedi [Integrazione di Target con i frammenti esperienza](/help/sites-administering/experience-fragments-target.md) per informazioni complete.
