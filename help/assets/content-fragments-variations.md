---
title: Varianti - Authoring dei contenuti di frammenti
seo-title: Variations - Authoring Fragment Content
description: Le varianti consentono di creare contenuti per il frammento, quindi di creare varianti di tali contenuti in base allo scopo (se necessario).
seo-description: Variations allow you to author content for the fragment, then create variations of that content according to purpose (if required).
uuid: affccda0-be5f-47d2-85b6-8701b77ac932
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: 1cdb2dfc-623b-44cf-9a7b-98cfabbb1d0c
exl-id: 15a5fdc9-2878-4f95-83ee-02a2899aeb43
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1738'
ht-degree: 85%

---

# Varianti - Authoring dei contenuti di frammenti  {#variations-authoring-fragment-content}

>[!CAUTION]
>
>Alcune funzionalità dei frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](../release-notes/sp-release-notes.md).

[Variazioni](content-fragments.md#constituent-parts-of-a-content-fragment) sono una funzione significativa dei frammenti di contenuto, in quanto consentono di creare e modificare copie del contenuto principale da utilizzare su canali e/o scenari specifici.

Dalla scheda **Varianti** è possibile:

* [Inserisci il contenuto](#authoring-your-content) per il frammento
* [Creare e gestire le varianti](#managing-variations) del **Master** content

Puoi eseguire una serie di altre azioni a seconda del tipo di dati in corso di modifica; ad esempio:

* [Inserire risorse visive nel frammento](#inserting-assets-into-your-fragment) (immagini)
* Scegliere tra [Testo formattato](#rich-text), [Testo normale](#plain-text) e [Markdown](#markdown) per la modifica

* [Caricare contenuti](#uploading-content)

* [Visualizzare le statistiche chiave](#viewing-key-statistics) (informazioni sul testo su più righe)
* [Ottenere un riepilogo del testo](#summarizing-text)

* [Sincronizzare le varianti con il contenuto principale](#synchronizing-with-master)

>[!CAUTION]
>
>Dopo la pubblicazione e/o il riferimento a un frammento, AEM mostra un avviso quando un autore riapre il frammento per la modifica. L’avviso informa l’utente che le modifiche al frammento avranno effetto anche sulle pagine a cui si fa riferimento.

## Authoring dei contenuti {#authoring-your-content}

Quando apri il frammento di contenuto per la modifica, la scheda **Varianti** viene aperta per impostazione predefinita. Qui puoi creare il contenuto per l’elemento Principale o per una delle varianti disponibili. Operazioni disponibili:

* Apportare modifiche direttamente nella scheda **Varianti**
* apri [editor a schermo intero](#full-screen-editor) a:

   * Selezionare il [Formato](#formats)
   * Accedere a ulteriori opzioni di modifica (per il formato [Testo formattato](#rich-text))
   * Accedere a una serie di [azioni](#actions)

Esempio:

* Modifica di un frammento semplice

   Un frammento semplice è costituito da un campo di testo a più righe (è possibile aggiungere risorse visive dall’editor a schermo intero).

   ![cfm-6420-21](assets/cfm-6420-21.png)

* Modifica di un frammento con contenuto strutturato

   Un frammento strutturato contiene vari campi, di vari tipi di dati, definiti nel modello di contenuto. Per tutti i campi con più righe, l’ [editor a schermo intero](#full-screen-editor) è disponibile.

   ![cfm-6420-16](assets/cfm-6420-16.png)

### Editor a schermo intero {#full-screen-editor}

Quando modifichi un campo di testo su più righe puoi aprire l’editor a schermo intero:

![cf-fullscreeneditor-icon](assets/cf-fullscreeneditor-icon.png)

L’editor a schermo intero fornisce:

* accesso a varie [azioni](#actions);
* a seconda del [formato](#formats), opzioni di formattazione aggiuntive ([Testo formattato](#rich-text)).

### Azioni {#actions}

Qquando l’editor a schermo intero (ad esempio testo su più righe) è aperto, sono disponibili anche le seguenti azioni (per tutti i [formati](#formats)):

* Seleziona la [format](#formats) ([Rich Text](#rich-text), [Testo normale](#plain-text), [Markdown](#markdown))
* [Mostrare statistiche sul testo](#viewing-key-statistics)
* [Caricare contenuti](#uploading-content)
* [Sincronizzare con il contenuto principale](#synchronizing-with-master) (se si modifica una variante)
* [Ottenere un riepilogo del testo](#summarizing-text)
* [Annota](content-fragments-variations.md#annotating-a-content-fragment) il testo

* [Inserire risorse visive nel frammento](#inserting-assets-into-your-fragment) (immagini)

### Formati {#formats}

Le opzioni per la modifica del testo su più righe dipendono dal formato selezionato:

* [Testo formattato](#rich-text)
* [Testo normale](#plain-text)
* [Markdown](#markdown)

Il formato può essere selezionato quando si utilizza l’editor a schermo intero.

### Testo formattato {#rich-text}

La modifica come testo formattato consente di applicare la seguente formattazione:

* Grassetto
* Corsivo
* Sottolineato
* Allineamento: sinistra, centro, destra
* Elenco puntato
* Elenco numerato
* Rientro: aumento, riduzione
* Creare/interrompere collegamenti ipertestuali
* Aprire l’editor a schermo intero, in cui sono disponibili le seguenti opzioni di formattazione:

   * Incolla testo/da Word
   * Inserisci tabella
   * Stile paragrafo: Paragrafo, Titolo 1/2/3
   * [Inserire risorse visive](#inserting-assets-into-your-fragment)
   * Ricerca
   * Trova/Sostituisci
   * Controllo ortografia
   * [Annotazioni](content-fragments-variations.md#annotating-a-content-fragment)

Dall’editor a schermo intero sono accessibili anche le [azioni](#actions).

### Testo normale {#plain-text}

Testo normale consente di inserire rapidamente contenuti senza formattazione o informazioni di markdown. Puoi anche aprire l’editor a schermo intero per ulteriori [azioni](#actions).

>[!CAUTION]
>
>Se selezioni **Testo normale**, potresti perdere la formattazione, elementi di markdown e/o risorse inserite in **Testo formattatot** o **Markdown**.

### Markdown {#markdown}

>[!NOTE]
>
>Per informazioni complete vedi la documentazione relativa a [Markdown](content-fragments-markdown.md).

Questo consente di formattare il testo utilizzando il linguaggio markdown. Puoi definire:

* Titoli
* Paragrafi e interruzioni di riga
* Collegamenti
* Immagini
* Citazioni
* Elenchi
* Enfasi
* Blocchi di codice
* Escape barra rovesciata

Puoi anche aprire l’editor a schermo intero per ulteriori [azioni](#actions).

>[!CAUTION]
>
>Se passi da **Testo formattatot** a **Markdown**, potresti riscontrare effetti imprevisti con Citazioni e Blocchi di codice, in quanto questi due formati possono presentare differenze nelle modalità di gestione.

### Visualizzazione delle statistiche chiave {#viewing-key-statistics}

Quando l’editor a schermo intero è aperto, l’azione **Statistiche testo** visualizzerà una serie di informazioni sul testo. Esempio:

![cfx-6420-22](assets/cfx-6420-22.png)

### Caricamento del contenuto {#uploading-content}

Per facilitare il processo di creazione dei frammenti di contenuto, puoi caricare il testo, prepararlo in un editor esterno e aggiungerlo direttamente al frammento.

### Ottenere un riepilogo del testo {#summarizing-text}

La funzione di riepilogo del testo è progettata per aiutare gli utenti a ridurre la lunghezza del testo a un numero predefinito di parole, mantenendo i punti chiave e il significato generale.

>[!NOTE]
>
>A livello più tecnico, il sistema mantiene le frasi che ritiene fornire *miglior rapporto tra densità e unicità delle informazioni* secondo specifici algoritmi.

>[!CAUTION]
>
>Il frammento di contenuto deve avere come predecessore una cartella di lingua valida; viene utilizzato per determinare il modello di lingua da utilizzare.
>
>Ad esempio: `en/` nel seguente percorso:
>
>`/content/dam/my-brand/en/path-down/my-content-fragment`

>[!CAUTION]
>
>L’inglese è disponibile in modo predefinito.
>
>Altre lingue sono disponibili come Pacchetti modello di lingua da Software Distribution:
>
>* [Francese (fr) da Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)
>* [Tedesco (de) da Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
>* [Italiano (it) da Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
>* [Spagnolo (es) da Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
>


1. Seleziona **[!UICONTROL Principale]** o la variante richiesta.
1. Apri l’editor a schermo intero.

1. Seleziona **[!UICONTROL Riepiloga testo]** nella barra degli strumenti.

   ![cf-17](assets/cf-17.png)

1. Specifica il numero di parole desiderato e seleziona **[!UICONTROL Inizia]**:
1. Il testo originale viene visualizzato affiancato al riepilogo proposto:

   * Tutte le frasi da eliminare sono evidenziate in rosso e barrate.
   * Fai clic su una frase evidenziata per mantenerla nel contenuto del riepilogo.
   * Fai clic su una frase non evidenziata per eliminarla.

   ![cfm-6420-23](assets/cfm-6420-23.png)

1. Seleziona **[!UICONTROL Riepiloga]** per confermare le modifiche.

### Annotazione di un frammento di contenuto {#annotating-a-content-fragment}

Per annotare un frammento:

1. Seleziona **[!UICONTROL Principale]** o la variante richiesta.
1. Apri l’editor a schermo intero.
1. Seleziona del testo. La **[!UICONTROL Annota]** l’icona diventa disponibile.

   ![cfm-6420-24](assets/cfm-6420-24.png)

1. Viene aperta una finestra di dialogo. Consente di inserire l’annotazione.

1. Chiudi l’editor a schermo intero e **[!UICONTROL Salva]** il frammento.

### Visualizzazione, modifica ed eliminazione delle annotazioni {#viewing-editing-deleting-annotations}

Caratteristiche delle annotazioni:

* Sono evidenziate nel testo, sia nella modalità a schermo intero che nella modalità normale dell’editor. Per visualizzare, modificare e/o eliminare tutti i dettagli di un’annotazione, fai clic sul testo evidenziato per riaprire la finestra di dialogo.

   >[!NOTE]
   >
   >Se a un testo sono state applicate più annotazioni, viene fornito un selettore a discesa.

* Quando si elimina l’intero testo a cui è stata applicata l’annotazione, viene eliminata anche l’annotazione.

* Può essere elencata ed eliminata selezionando dalla scheda **[!UICONTROL Annotazioni]** nell’editor frammenti.

   ![cfm-6420-25](assets/cfm-6420-25.png)

* Può essere visualizzata ed eliminata nella [Timeline](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments) del frammento selezionato.

### Inserimento di risorse nel frammento {#inserting-assets-into-your-fragment}

Per semplificare il processo di creazione dei frammenti di contenuto, puoi aggiungere [Risorse](managing-assets-touch-ui.md) (immagini) direttamente al frammento.

Vengono aggiunte alla sequenza di paragrafi del frammento senza formattazione; la formattazione può essere impostata quando il [frammento viene utilizzato o inserito come riferimento in una pagina](/help/sites-authoring/content-fragments.md).

>[!CAUTION]
>
>Non è possibile spostare o eliminare le risorse in una pagina di riferimento; tali azioni devono essere eseguite nell’editor frammenti.
>
>La formattazione della risorsa (ad es. per ridimensionarla) deve invece essere eseguita nell’[editor pagina](/help/sites-authoring/content-fragments.md). La rappresentazione della risorsa nell’editor frammenti è puramente a scopo di creazione del flusso di contenuto.

>[!NOTE]
>
>Esistono diversi metodi per aggiungere [immagini](content-fragments.md#fragments-with-visual-assets) al frammento e/o alla pagina.

1. Posiziona il cursore nel punto in cui vuoi aggiungere l’immagine.
1. Per aprire la finestra di dialogo di ricerca, utilizza l’icona **[!UICONTROL Inserisci risorsa]**.

   ![cf-insertasset-icon](assets/cf-insertasset-icon.png)

1. Nella finestra di dialogo puoi effettuare le seguenti operazioni:

   * Passare alla risorsa richiesta in DAM
   * Cercare la risorsa in DAM

   Una volta individuata la risorsa desiderata, fai clic sulla miniatura.

1. Utilizza **[!UICONTROL Seleziona]** per aggiungere la risorsa al sistema paragrafo del frammento di contenuto nella posizione corrente.

   >[!CAUTION]
   >
   >Se, dopo aver aggiunto una risorsa, ne cambi il formato in:
   >
   >* **Testo normale**: la risorsa verrà persa completamente dal frammento.
   >* **Markdown**: la risorsa non sarà visibile, ma lo tornerà a essere quando tornerai a **Rich Text**.


## Gestione delle varianti {#managing-variations}

### Creazione di una variante {#creating-a-variation}

Le varianti consentono di utilizzare il contenuto **principale** e modificarlo in base allo scopo (se necessario).

Per creare una nuova variante:

1. Apri il frammento e accertati che il pannello laterale sia visibile.
1. Seleziona **[!UICONTROL Varianti]** dalla barra delle icone nel pannello laterale.
1. Seleziona **[!UICONTROL Crea variante]**.
1. Viene aperta una finestra di dialogo in cui vengono specificati **[!UICONTROL Titolo]** e **[!UICONTROL Descrizione]** per la nuova variante.
1. Seleziona **[!UICONTROL Aggiungi]**, il frammento **[!UICONTROL Principale]** viene copiato nella nuova variante, che è ora aperta per la [modifica](#editing-a-variation).

   >[!NOTE]
   >
   >Quando crei una nuova variante, viene sempre copiato l’elemento **Principale**, non la variante attualmente aperta.

### Modifica di una variante {#editing-a-variation}

Puoi apportare modifiche al contenuto della variante dopo:

* la [creazione della variante](#creating-a-variation);
* l’apertura di un frammento esistente e la selezione della variante desiderata dal pannello laterale.

![cfm-6420-26](assets/cfm-6420-26.png)

### Modifica del nome di una variante {#renaming-a-variation}

Per modificare il nome di una variante esistente:

1. Apri il frammento e seleziona **[!UICONTROL Varianti]** nel pannello laterale.
1. Seleziona la variante desiderata.
1. Seleziona **[!UICONTROL Rinomina]** dal menu a discesa **[!UICONTROL Azioni]**.

1. Nella finestra di dialogo che si apre, immetti il nuovo **[!UICONTROL Titolo]** e/o la nuova **[!UICONTROL Descrizione]**.

1. Conferma l’azione **[!UICONTROL Rinomina]**.

>[!NOTE]
>
>Questo influisce solo sul **Titolo** della variante.

### Eliminazione di una variante {#deleting-a-variation}

Per eliminare una variante esistente:

1. Apri il frammento e seleziona **[!UICONTROL Varianti]** nel pannello laterale.
1. Seleziona la variante desiderata.
1. Seleziona **[!UICONTROL Elimina]** dal menu a discesa **[!UICONTROL Azioni]**.

1. Nella finestra di dialogo che si apre, conferma l’azione **[!UICONTROL Elimina]**.

>[!NOTE]
>
>Non è possibile eliminare l’elemento **Principale**.

### Sincronizzazione con l’elemento Principale {#synchronizing-with-master}

L’elemento **Principale** è parte integrante di un frammento di contenuto e, per definizione, contiene la copia principale del contenuto; le varianti ne contengono le singole versioni aggiornate e personalizzate. Quando Master viene aggiornato, è possibile che queste modifiche siano pertinenti anche alle varianti e, pertanto, devono essere propagate a esse.

Quando modifichi una variante, hai accesso all’azione che consente di sincronizzare l’elemento corrente della variante con l’elemento Principale. Questo consente di copiare automaticamente le modifiche apportate all’elemento Principale nella variante desiderata.

>[!CAUTION]
>
>La sincronizzazione è disponibile solo per copiare le modifiche *dall’elemento **Principale** alla variante*.
>
>Viene sincronizzato solo l’elemento corrente della variante.
>
>La sincronizzazione funziona solo sul tipo di dati **Testo su più righe**.
>
>Il trasferimento delle modifiche *da una variante all’elemento **Principale*** non è disponibile come opzione.

1. Apri il frammento di contenuto nell’editor frammenti. Assicurati che l’elemento **Principale** sia stato modificato.
2. Seleziona una variante specifica, quindi seleziona l’azione di sincronizzazione appropriata da una delle seguenti aree:

   * Selettore a discesa **Azioni**: **Sincronizza elemento corrente con elemento principale**
   * Barra degli strumenti dell’editor a schermo intero: **Sincronizza con elemento principale**

3. L’elemento Principale e la variante vengono visualizzati affiancati:

   * Il contenuto aggiunto alla variante è indicato in verde.
   * II contenuto rimosso dalla variante è indicato in rosso.

   ![cfm-6420-27](assets/cfm-6420-27.png)

4. Seleziona **[!UICONTROL Sincronizza]**; la variante viene aggiornata e visualizzata.
