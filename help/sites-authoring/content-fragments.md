---
title: Authoring delle pagine con frammenti di contenuto
seo-title: Page Authoring with Content Fragments
description: I frammenti di contenuto AEM consentono di progettare, creare, curare e utilizzare contenuti indipendenti dalla pagina
seo-description: AEM Content Fragments allow you to design, create, curate, and use page-independent content
uuid: 66ccdff8-1658-4374-8562-97f81f434488
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 076a3064-80c3-454b-93f9-6ae925c54328
exl-id: bbe4ae86-e9b8-4c3f-ada3-82470e371c4e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 53%

---

# Authoring delle pagine con frammenti di contenuto{#page-authoring-with-content-fragments}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Alcune funzionalità dei frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](/help/release-notes/sp-release-notes.md).

I frammenti di contenuto di Adobe Experience Manager (AEM) vengono [creati e gestiti come risorse indipendenti dalla pagina](/help/assets/content-fragments.md).

Consentono di creare contenuti neutri per il canale, insieme a varianti (eventualmente specifiche per il canale). Puoi quindi utilizzare questi frammenti, con le relative varianti, durante l’authoring di pagine di contenuto.

Insieme alla funzione di esportazione JSON aggiornata, i frammenti di contenuto strutturati possono anche essere utilizzati per distribuire contenuti AEM, tramite Content Services a canali diversi dalle pagine AEM.

>[!NOTE]
>
>I **frammenti di contenuto** e i **[frammenti di esperienza](/help/sites-authoring/experience-fragments.md)** sono funzioni diverse in AEM:
>
>* **Frammenti di contenuto** sono contenuti editoriali, principalmente testo e immagini correlate. Sono contenuti puri, senza design e layout.
>* I **frammenti di esperienza** sono contenuti completi di layout, frammenti di una pagina web.
>
>I frammenti esperienza possono includere contenuti sotto forma di frammenti di contenuto, ma non viceversa.

>[!CAUTION]
>
>Questa pagina deve essere letta insieme a [Utilizzo dei frammenti di contenuto](/help/assets/content-fragments.md) (e pagine correlate), in quanto introduce la terminologia e i concetti di base e spiega come creare e gestire i frammenti.

I frammenti di contenuto consentono:

* **Strategia di marketing e campagne**

   * Revisione dei contenuti tramite frammenti di contenuto gestiti a livello centrale.

* **Creative Pro**

   * Tracciamento delle risorse creative tramite raccolte associate ai frammenti di contenuto.

* **Scrittori copia**

   * Creazione di contenuti nell’editor frammento di contenuto di AEM.
   * Può creare varianti di contenuto.
   * Può associare contenuti rilevanti al frammento di contenuto.
   * Può utilizzare il controllo delle versioni/flusso di lavoro.
   * Può condividere frammento di contenuto.
   * Gestione centralizzata delle traduzioni.

* **Produttori e Percorsi**

   * Selezione di frammenti e varianti predefiniti con authoring in AEM.
   * Può contare sul fatto che frammenti e contenuti associati siano sempre aggiornati, in quanto autori e creativi di copie possono eseguire gli aggiornamenti in frammenti e risorse gestiti a livello centrale.
   * Può contare sul fatto che i contenuti multimediali associati siano curati per la loro rilevanza.
   * È in grado di creare al volo varianti di contenuto ad hoc, garantendo al contempo che tali varianti rimangano gestite a livello centrale nel frammento.

## Aggiunta di un frammento di contenuto alla pagina  {#adding-a-content-fragment-to-your-page}

1. Apri la pagina per la modifica.

1. Aggiungi il componente **[!UICONTROL Frammento di contenuto]** dal browser **[!UICONTROL Componenti]** o mediante il comando **[!UICONTROL Inserisci nuovo componente]**.

1. Puoi effettuare le seguenti operazioni:

   * Apri il browser **[!UICONTROL Risorse]** e applica il filtro **[!UICONTROL Frammenti di contenuto]** (l’impostazione predefinita è Immagini). Quindi trascina il frammento desiderato sull’istanza del componente.
   * Seleziona il componente del frammento di contenuto, quindi **[!UICONTROL Configura]** dalla barra degli strumenti. Nella finestra di dialogo, apri la finestra di dialogo di selezione per individuare e selezionare il **[!UICONTROL frammento di contenuto]** richiesto.

   >[!NOTE]
   >
   >In alternativa, puoi trascinare un frammento di contenuto specifico direttamente nella pagina. In questo modo verrà creato automaticamente il componente associato (Frammento di contenuto).

1. Inizialmente verrà visualizzato il contenuto dell’**[!UICONTROL elemento principale]** e la **[!UICONTROL pagina mastro]** (variante). Puoi [selezionare altri elementi e/o varianti](#selecting-the-element-or-variation), secondo necessità.

   ![cfm-6420-01](assets/cfm-6420-01.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni su ulteriori funzionalità di modifica, consulta anche:
   >
   >* [Layout dinamico](/help/sites-authoring/responsive-layout.md)
   >* [Modifica del contenuto di una pagina](/help/sites-authoring/editing-content.md)


## Selezione dell’elemento o della variante {#selecting-the-element-or-variation}

Apri la finestra di dialogo **[!UICONTROL Configurazione]** del frammento per configurare il frammento per la pagina corrente. La finestra di dialogo può dipendere dal componente utilizzato.

Nella finestra di dialogo di configurazione appropriata puoi selezionare i parametri disponibili, tra cui:

* **[!UICONTROL Frammento di contenuto]**

   Specifica il frammento da utilizzare.

* **[!UICONTROL Modalità di visualizzazione]**:

   * **[!UICONTROL Elemento di testo singolo]**
   * **[!UICONTROL Elemento multiplo]**

* **[!UICONTROL Elemento]**

   * Il valore predefinito **[!UICONTROL Principale]** sarà sempre disponibile.
   * Una selezione è disponibile se il frammento è stato creato con un modello appropriato.

   >[!NOTE]
   >
   >Gli elementi disponibili dipendono dal modello utilizzato.

* **[!UICONTROL Variazione]**

   * Il **[!UICONTROL Master]** predefinito sarà sempre disponibile.
   * Se per il frammento sono state create delle varianti, sarà disponibile una selezione.

* **[!UICONTROL Paragrafi]**: specificare l’intervallo di paragrafi da includere:

   * **[!UICONTROL Tutti i bundle]**
   * **[!UICONTROL Intervallo]**: ad esempio, `1`, `3-5`, `9-*`

      * **[!UICONTROL Tratta le intestazioni come paragrafi propri]**

* **[!UICONTROL Tratta le intestazioni come paragrafi propri]**

## Collegamento rapido all’Editor frammento di contenuto  {#quick-connection-to-fragment-editor}

Puoi aprire l’origine del frammento in modalità di modifica (la risorsa) mediante l’icona **[!UICONTROL Modifica]** nella barra degli strumenti del componente, così da poter [modificare e gestire il frammento di contenuto](/help/assets/content-fragments.md).

>[!CAUTION]
>
>Come sempre, la modifica dell’origine del frammento ha un impatto su tutte le pagine che fanno riferimento a tale frammento di contenuto.

## Aggiunta di contenuto intermedio  {#adding-in-between-content}

Quando un frammento di contenuto specifico viene aggiunto alla pagina, è disponibile un **[!UICONTROL Trascina qui i componenti]** segnaposto tra ciascun paragrafo di HTML (e in alto/in basso) del frammento.

Questo consente di aggiungere ulteriori contenuti [intermedio (ovvero contenuto intermedio)](/help/assets/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) il contenuto del frammento (nei punti disponibili), senza dover modificare il frammento principale.

Per il contenuto intermedio è possibile:

* Aggiungi componenti dal [Browser Componenti](/help/sites-authoring/author-environment-tools.md#components-browser).
* Aggiungi risorse da [Browser risorse](/help/sites-authoring/author-environment-tools.md#assets-browser).
* Usare [Contenuto associato](#using-associated-content) come origine per il contenuto intermedio.

>[!CAUTION]
>
>Il contenuto intermedio è contenuto di pagina. Non viene memorizzato nel frammento di contenuto.

![cfm-6420-02](assets/cfm-6420-02.png)

>[!NOTE]
>
>È inoltre possibile [inserire risorse visive (immagini) nel frammento stesso](/help/assets/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Le risorse visive inserite nel frammento stesso sono associate al paragrafo precedente nel frammento. Non è pertanto possibile inserire contenuto intermedio tra una risorsa visiva e il paragrafo precedente.

>[!CAUTION]
>
>Dopo aver aggiunto contenuto intermedio a un frammento di contenuto nella pagina, se si modifica la struttura del frammento di contenuto sottostante (ovvero nell’editor frammento di contenuto) si potrebbero verificare risultati erronei o imprevisti.
>
>In questi casi, il contenuto intermedio rimane inalterato:
>
>* I componenti intermedi hanno una posizione assoluta all’interno della sequenza di componenti nel flusso del frammento. Questa posizione non cambia, anche quando cambia il contenuto dei paragrafi nel frammento.\
   >  Questo potrebbe dare l’impressione di una modifica nella posizione relativa, poiché i paragrafi intermedi non hanno alcuna relazione contestuale con i paragrafi (del frammento) accanto ai quali sono posizionati,
>* a meno che le due strutture di paragrafo non siano in conflitto. In questo caso il contenuto intermedio non viene visualizzato, ma resta comunque presente nel codice interno.
>


## Uso di contenuti associati  {#using-associated-content}

Se hai [associato del contenuto](/help/assets/content-fragments-assoc-content.md) al [frammento di contenuto](/help/assets/content-fragments.md), queste risorse saranno disponibili nel pannello laterale (dopo aver inserito il frammento nella pagina del contenuto). Il contenuto associato è di fatto una fonte speciale di contenuto per il [contenuto intermedio](#adding-in-between-content).

>[!NOTE]
>
>Esistono diversi metodi per aggiungere [risorse visive (ad es. immagini)](/help/assets/content-fragments.md#fragments-with-visual-assets) al frammento e/o alla pagina.

>[!NOTE]
>
>Se sulla stessa pagina sono presenti più frammenti di contenuto, la funzione **[!UICONTROL Contenuto associato]** vengono visualizzate le risorse appropriate per tutti i frammenti.

Una volta aggiunto alla pagina un frammento con contenuto associato, nel pannello laterale viene aperta una nuova scheda (**[!UICONTROL Contenuto associato]**).

Da qui puoi trascinare le risorse nella posizione richiesta (su un componente esistente o nella posizione in cui sarà creato il componente appropriato):

![cfm-6420-03](assets/cfm-6420-03.png)

## Risorse inserite nel frammento {#assets-inserted-into-the-fragment}

Se [sono state inserite risorse (ad esempio immagini) nel frammento stesso](/help/assets/content-fragments-variations.md#inserting-assets-into-your-fragment), le opzioni per la modifica di queste risorse nell’editor pagina sono limitate.

Ad esempio, per un’immagine è possibile:

* Ritaglia, ruota o capovolgi l’immagine.
* Aggiungi un titolo o un testo alternativo.
* Specifica una dimensione.
* Puoi anche configurare il layout.

Altre modifiche, ad esempio spostamento, copia, eliminazione, devono essere effettuate nell’editor frammenti.

## Pubblicazione {#publishing}

I frammenti devono essere pubblicati in modo che possano essere utilizzati nelle pagine web pubblicate:

* Un frammento può essere pubblicato dopo [creazione del frammento nella console Risorse](/help/assets/content-fragments-managing.md#publishing-and-referencing-a-fragment).
* Se in una pagina in corso di pubblicazione viene utilizzato un *frammento non pubblicato*, è possibile pubblicare anche quest’ultimo allo stesso tempo.
