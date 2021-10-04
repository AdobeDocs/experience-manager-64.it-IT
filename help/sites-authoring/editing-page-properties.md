---
title: Modifica delle proprietà di una pagina
seo-title: Editing Page Properties
description: Puoi impostare le proprietà richieste per una pagina.
seo-description: Define the required properties for a page
uuid: c0386cd6-ca01-4741-b8c8-36edb66e50ef
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8e85ea7f-80ea-43b6-a67c-366852ef86ce
exl-id: b0e579a4-f5bd-4a55-a003-0496224bc940
source-git-commit: d01eee7602945b8d3cb3ad004ccf5ad6cbc4c73c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Modifica delle proprietà di una pagina  {#editing-page-properties}

Puoi impostare le proprietà richieste per una pagina. Queste possono variare a seconda del tipo di pagina. Ad esempio, alcune pagine possono essere connesse a una Live Copy, mentre altre no, e le informazioni della Live Copy saranno disponibili ove appropriato.

## Proprietà pagina   {#page-properties}

Le proprietà sono distribuite su più schede.

### Base {#basic}

* **Titolo**

   Il titolo della pagina viene visualizzato in diversi punti. Ad esempio, nell’elenco della scheda **Siti web** e nelle viste a scheda o elenco di **Sites**.

   Questo campo è obbligatorio.

* **Tag**

   Qui puoi aggiungere o rimuovere i tag nella pagina modificando l’elenco nella casella di selezione:

   * Dopo aver selezionato un tag, questo viene elencato nella casella di selezione. Per rimuovere un tag dall’elenco, utilizza l’icona x.
   * Per aggiungere un tag nuovo, digita il nome in una casella di selezione vuota.

      * Il nuovo tag viene creato quando premi Invio.
      * Un asterisco a destra del nome lo identifica come nuovo tag.
   * L’elenco a discesa consente di selezionare uno dei tag esistenti.
   * Quando sposti il mouse su un tag nella casella di selezione viene visualizzata una x, che consente di rimuovere il tag dalla pagina in questione.

   Per ulteriori informazioni sui tag, consulta [Utilizzo dei tag](/help/sites-authoring/tags.md).

* **Nascondi in navigazione**

   Indica se la pagina viene visualizzata o nascosta nella navigazione delle pagine del sito finale.

* **Marchio**

   Applica un’identità di marchio coerente tra le pagine aggiungendo un marchio a ciascun titolo della pagina. Questa funzionalità richiede l&#39;utilizzo del componente Pagina dalla versione 2.14.0 o successiva dei [Componenti core.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=it)

   * **Override** : seleziona per definire il brand lumg in questa pagina.
      * Il valore viene ereditato da qualsiasi pagina figlia a meno che non siano impostati anche i valori **Override**.
   * **Valore di sostituzione** : il testo del marchio da aggiungere al titolo della pagina.
      * Il valore viene aggiunto al titolo della pagina dopo un carattere di barra come &quot;Ciclismo in Toscana | Sempre pronto per il WKND&quot;

* **Titolo pagina**

   Titolo da utilizzare nella pagina. Generalmente utilizzato dai componenti titolo. Se questo campo è vuoto, viene utilizzato il **Titolo**.

* **Titolo navigazione**

   Puoi specificare un diverso titolo da usare per la navigazione (ad esempio un titolo più conciso). Se questo campo è vuoto, viene utilizzato il **Titolo**.

* **Sottotitolo**

   Sottotitolo da utilizzare nella pagina.

* **Descrizione**

   La descrizione della pagina, del suo ruolo o altri dettagli.

* **Ora di attivazione**

   Data e ora in cui verrà attivata la pagina pubblicata. Dopo la pubblicazione, la pagina rimarrà inattiva fino alla data e all’ora specificate. 

   Lascia vuoti questi campi per le pagine da pubblicare immediatamente (lo scenario più consueto).

* **Ora di disattivazione**

   Data e ora in cui verrà disattivata la pagina pubblicata.

   Lascia questi campi vuoti per un’azione immediata.

* **URL personalizzato**

   Consente di immettere un URL personalizzato per questa pagina, se desideri inserire un URL più breve e/o più significativo.

   Ad esempio, se l’URL personalizzato è impostato su w `elcome`nella pagina identificata dal percorso / `v1.0/startpage`per il sito web h `ttp://example.com,` , h `ttp://example.com/welcome`sarà l’URL personalizzato di h `ttp://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >Gli URL personalizzati:
   >
   >* devono essere univoci, quindi accertati che il valore scelto non sia già utilizzato per un’altra pagina;
   >* non supportano le espressioni regolari;


* **Reindirizza URL personalizzato**

   Specifica se vuoi che la pagina usi l’URL personalizzato.

### Avanzate  {#advanced}

* **Lingua**

   Indica la lingua della pagina.

* **Reindirizza**

   Indica la pagina a cui deve essere automaticamente reindirizzata la pagina corrente.

* **Design**

   Indica il [design](/help/sites-developing/designer.md) da utilizzare per la pagina.

* **Alias**

   Specifica un alias da utilizzare per la pagina.

   * Ad esempio, se definisci un alias di `private` per la pagina `/content/wknd/us/en/magazine/members-only`, è possibile accedere a questa pagina anche tramite `/content/wknd/us/en/magazine/private`.
   * La creazione di un alias imposta la proprietà `sling:alias` sul nodo della pagina, che influisce solo sulla risorsa e non sul percorso dell’archivio.
   * Le pagine a cui si accede tramite alias nell’editor non possono essere pubblicate. [Le opzioni di pubblicazione ](/help/sites-authoring/publishing-pages.md) nell’editor sono disponibili solo per le pagine accessibili tramite i percorsi effettivi.
   * Per ulteriori dettagli, consulta [Nomi di pagina localizzati in Best practice per la gestione di SEO (Search Engine Optimization) e URL](/help/managing/seo-and-url-management.md#localized-page-names)

* **Modelli consentiti**

   [Definisci l’elenco di modelli che saranno disponibili](/help/sites-authoring/templates.md#enabling-and-allowing-a-template-template-author) in questo ramo secondario.

* **Autenticazione richiesta**

   Attiva (o disattiva) l’uso dell&#39;autenticazione per accedere alla pagina.

   Qui puoi impostare i requisiti di autenticazione insieme a una pagina di accesso specifica. Nella scheda **[Autorizzazioni](/help/sites-authoring/editing-page-properties.md#permissions)** è possibile definire gruppi utenti chiusi per la pagina.

   >[!CAUTION]
   >
   >La scheda **[Autorizzazioni](/help/sites-authoring/editing-page-properties.md#permissions)** consente di modificare le configurazioni del gruppo utenti chiuso in base alla presenza del mixin `granite:AuthenticationRequired`. Se le autorizzazioni della pagina sono configurate utilizzando configurazioni CUG obsolete, basate sulla proprietà cq:cugEnabled , verrà visualizzato un messaggio di avviso in **Autenticazione richiesta** e l&#39;opzione non sarà modificabile, né le [Autorizzazioni](/help/sites-authoring/editing-page-properties.md#permissions) saranno modificabili.
   >
   >
   >In questo caso, le autorizzazioni del gruppo utenti chiuso devono essere modificate [nell’interfaccia classica](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md).

* **Pagina di accesso**

   Indica la pagina da utilizzare per l’accesso.

* **Configurazione esportazione**

   Consente di specificare una configurazione di esportazione.

### Miniatura  {#thumbnail}

1. **Miniatura pagina**

   Mostra la miniatura della pagina. Operazioni disponibili:

   * **Genera anteprima**

      Genera un’anteprima della pagina da usare come miniatura.

   * **Carica immagine**

      Carica un’immagine da usare come miniatura.

### Social media {#social-media}

* **Condivisione social media**

   Definisce le opzioni di condivisione disponibili sulla pagina. Rende disponibili le opzioni per la [Condivisione dei componenti di base](https://helpx.adobe.com/experience-manager/core-components/using/sharing.html).

   * **Abilita condivisione da parte degli utenti su Facebook**
   * **Abilita condivisione da parte degli utenti su Pinterest**
   * **Variante XF preferita**
Consente di definire la variante del frammento esperienza utilizzato per generare i metadati della pagina.

### Cloud Services {#cloud-services}

* **Cloud Services**

   Consente di definire le proprietà per i [servizi cloud](/help/sites-developing/extending-cloud-config.md).

### Personalizzazione {#personalization}

* **Personalizzazione**

   Seleziona un [marchio per specificare l’ambito di targeting](/help/sites-authoring/personalization.md).

### Autorizzazioni   {#permissions}

* **Autorizzazioni**

   In questa scheda puoi:

   * [Aggiungere autorizzazioni](/help/sites-administering/user-group-ac-admin.md)
   * [Modificare un gruppo utenti chiuso](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)
   * Visualizzare le [Autorizzazioni effettive](/help/sites-administering/user-group-ac-admin.md)

   >[!CAUTION]
   >
   >La scheda **Autorizzazioni** consente di modificare le configurazioni del gruppo utenti chiuso in base alla presenza del mixin `granite:AuthenticationRequired`. Se le autorizzazioni della pagina utilizzano configurazioni del gruppo utenti chiuso obsolete, basate sulla proprietà `cq:cugEnabled`, viene visualizzato un messaggio di avvertenza e non sarà possibile modificare né l’opzione né l&#39;Autenticazione nella scheda [Avanzate](/help/sites-authoring/editing-page-properties.md#advanced).
   >
   >
   >In questo caso, le autorizzazioni del gruppo utenti chiuso devono essere modificate [nell’interfaccia classica](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md).

   >[!NOTE]
   >
   >La scheda Autorizzazioni non consente di creare gruppi utenti chiusi che siano vuoti; una soluzione utile per negare l’accesso a tutti gli utenti. A questo scopo devi usare CRX Explorer. Per ulteriori informazioni, consulta il documento [Amministrazione di utenti, gruppi e diritti di accesso](/help/sites-administering/user-group-ac-admin.md) .

### Blueprint {#blueprint}

* **Blueprint**

   Consente di definire le proprietà per una pagina Blueprint nella [gestione multisito](/help/sites-administering/msm.md). Controlla le circostanze in cui le modifiche verranno propagate alla Live Copy.

### Live Copy  {#live-copy}

* **Livecopy**

   Consente di definire le proprietà per una pagina Live Copy nell’[utilità di gestione multisito](/help/sites-administering/msm.md). Controlla le circostanze in cui le modifiche verranno propagate dalla Blueprint.

### Struttura sito  {#site-structure}

* Fornisce i collegamenti alle pagine che offrono funzionalità a livello di sito, tra cui **Pagina registrazione** e **Pagina offline**.

## Modifica delle proprietà di una pagina {#editing-page-properties-2}

Puoi definire le proprietà di pagina:

* Dalla console **Sites**:

   * [Crea una nuova pagina](/help/sites-authoring/managing-pages.md#creating-a-new-page) (un sottoinsieme delle proprietà)
   * Tocca o fai clic su **Proprietà**

      * Per una singola pagina
      * Per più pagine (solo un sottoinsieme di proprietà è disponibile per la modifica in blocco)

* Dall’editor di pagine:

   * Tramite **Informazioni pagina** (quindi **Apri proprietà**)

### Dalla console Sites - Pagina singola {#from-the-sites-console-single-page}

Tocca o fai clic su **Proprietà** per definire le proprietà di pagina:

1. Nella console **Sites** individua il punto della pagina di cui desideri visualizzare e modificare le proprietà.

1. Seleziona l’opzione **Proprietà** per la pagina desiderata, utilizzando:

   * [Azioni rapide](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Modalità di selezione](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)

   Le proprietà di pagina vengono visualizzate utilizzando le relative schede.

1. Visualizza o modifica le proprietà a seconda delle esigenze.

1. Quindi, seleziona **Salva** per salvare le modifiche e **Chiudi** per tornare alla console.

### Durante la modifica di una pagina {#when-editing-a-page}

Quando modifichi una pagina puoi utilizzare **Informazioni pagina** per definire le proprietà di pagina:

1. Apri la pagina di cui desideri modificare le proprietà.

1. Seleziona l’icona **Informazioni pagina** per aprire il menu di selezione.

   ![screen_shot_2018-03-22at095740](assets/screen_shot_2018-03-22at095740.png)

1. Seleziona **Apri proprietà** per aprire una finestra di dialogo che consente di modificare le proprietà, organizzate nella scheda appropriata. A destra della barra degli strumenti sono disponibili anche i seguenti pulsanti:

   * **Annulla**
   * **Salva e chiudi**

1. Usa il pulsante **Salva e chiudi** per salvare le modifiche.

### Dalla console Sites - Pagine multiple {#from-the-sites-console-multiple-pages}

Dalla console **Sites** è possibile selezionare più pagine e quindi utilizzare **Visualizza proprietà** per visualizzare e/o modificare le proprietà della pagina. Questa operazione è definita modifica in serie delle proprietà di pagina.

>[!NOTE]
>
>La modifica in serie delle proprietà è disponibile anche per le risorse. È molto simile, ma differisce per alcuni aspetti. Per ulteriori informazioni, consulta [Modificare le proprietà di risorse multiple](/help/assets/managing-multiple-assets.md).
>
>È disponibile anche lo strumento di [Modifica collettiva](/help/sites-administering/bulk-editor.md), che consente di cercare contenuti da più pagine tramite GQL (Google Query Language), e quindi di modificare il contenuto direttamente sullo strumento prima di salvare le modifiche sulle pagine originate.

Puoi selezionare più pagine per la modifica in serie utilizzando diversi metodi, tra i quali:

* Utilizzare la console **Sites**.
* Dopo aver utilizzato **Cerca** per individuare un insieme di pagine.

![screen_shot_2018-03-22at100039](assets/screen_shot_2018-03-22at100039.png)

Dopo aver selezionato le pagine e aver toccato o fatto clic sull&#39;opzione **Proprietà**, vengono visualizzate le proprietà di gruppo:

![screen_shot_2018-03-22at100114](assets/screen_shot_2018-03-22at100114.png)

Puoi eseguire la modifica in serie solo su pagine che:

* condividono lo stesso tipo di risorsa;
* non fanno parte di una Live Copy.

   * Se una delle pagine fa parte di una Live Copy, all’apertura delle proprietà viene visualizzato un messaggio di avviso.

Dopo aver attivato la funzione Modifica in serie, puoi effettuare le seguenti operazioni:

* **Visualizza**

   Quando visualizzi le Proprietà pagina per pagine multiple puoi vedere:

   * Un elenco delle pagine interessate.

      * Puoi selezionarle/deselezionarle se necessario.
   * Schede

      * Come per la visualizzazione delle proprietà di una pagina singola, le proprietà sono ordinate in schede.
   * Un sottoinsieme di proprietà.

      * Puoi vedere le proprietà che sono disponibili su tutte le pagine selezionate e che sono state esplicitamente definite come disponibili per la modifica in serie.
      * Se la tua selezione include una sola pagina, tutte le proprietà sono visibili.
   * Proprietà condivise con un valore comune

      * Nella modalità Visualizza vengono mostrate solo le proprietà con un valore comune.
      * Quando il campo ha più valori (ad esempio Tag), questi vengono visualizzati solo se *tutti* i valori sono applicati alle pagine selezionate. Se le pagine hanno in comune solo alcuni valori, questi verranno visualizzati solo in fase di modifica.

   Se non esiste nessuna proprietà con un valore comune, viene visualizzato un messaggio.

* **Modifica**

   Quando modifichi le Proprietà pagina per pagine multiple:

   * Puoi aggiornare i valori nei campi disponibili.

      * I nuovi valori saranno applicati a tutte le pagine selezionate quando fai clic su **Fine**.
      * Quando il campo ha valori multipli (ad esempio i Tag), puoi aggiungere un nuovo valore o rimuovere un valore comune.
   * I campi in comune ma con valori diversi nelle varie pagine saranno contraddistinti da uno speciale valore, ad esempio `<Mixed Entries>`. Presta attenzione quando modifichi tali campi per evitare perdite di dati.


>[!NOTE]
>
>Il componente di pagina può essere configurato in modo da specificare i campi disponibili per la modifica collettiva. Consulta [Configurazione della pagina per la modifica collettiva delle proprietà di pagina](/help/sites-developing/bulk-editing.md).
