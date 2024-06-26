---
title: Banner a carosello
seo-title: Carousel Banners
description: Scopri come utilizzare i banner carosello negli elementi multimediali dinamici
seo-description: Learn how to work with carousel banners in dynamic media
uuid: 6d6de9ac-a6e1-4f07-a610-cc84e26bf76b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4b532cd3-1561-4b5c-8b4b-420c278926f0
exl-id: d2fdad3f-513b-4147-a7c6-a3c1b64dd6e3
feature: Carousel Banners
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4771'
ht-degree: 4%

---

# Banner a carosello {#carousel-banners}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I banner a carosello consentono agli addetti al marketing di guidare la conversione creando facilmente contenuti promozionali interattivi rotanti e consegnandoli a qualsiasi schermo.

La creazione e la modifica dei contenuti contenuti contenuti nei banner promozionali può richiedere molto tempo, limitando la possibilità di pubblicare rapidamente nuovi contenuti o renderli più mirati. I banner a carosello consentono di creare o modificare rapidamente i banner rotanti, aggiungere interattività quali punti attivi collegati ai dettagli del prodotto o alle risorse correlate e consegnarli a qualsiasi schermo, consentendo di introdurre nuovi contenuti promozionali sul mercato più rapidamente.

I banner a carosello sono contrassegnati da un banner con la parola **CAROUSELSET**:

![chlimage_1-438](assets/chlimage_1-438.png)

Sul sito web, un banner a carosello può essere visualizzato come segue:

![chlimage_1-439](assets/chlimage_1-439.png)

Qui puoi navigare tra le immagini (facendo clic sui numeri). Inoltre, le diapositive ruotano automaticamente in base a un intervallo di tempo personalizzabile. Le immagini aggiunte nel banner carosello supportano sia punti attivi che mappe immagine, dove gli utenti possono toccare o passare a un collegamento ipertestuale o accedere a una finestra Quickview.

In questo esempio, un utente ha toccato o fatto clic su una mappa immagine e ha effettuato l’accesso alla finestra Quickview per i guanti:

![chlimage_1-440](assets/chlimage_1-440.png)

## Guarda come vengono creati i banner a carosello {#watch-how-carousel-banners-are-created}

Segui una procedura dettagliata di 10 minuti e 33 secondi [creazione dei banner a carosello](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Scoprirai anche come visualizzare in anteprima, modificare e distribuire banner a carosello.

>[!NOTE]
>
>Gli utenti non amministrativi devono essere aggiunti al **utenti dam** per poter creare o modificare banner carosello. In caso di problemi durante la creazione o la modifica, rivolgiti all’amministratore di sistema che può aggiungerti al **utenti dam** gruppo.

## Avvio rapido: Banner a carosello {#quick-start-carousel-banners}

Per farti iniziare a lavorare velocemente:

1. [Identificare le variabili dei punti attivi e delle mappe immagine](#identifying-hotspot-and-image-map-variables) (solo per i clienti che utilizzano AEM Assets + Dynamic Media)

   Per iniziare, identifica le variabili dinamiche utilizzate dall&#39;implementazione Quickview esistente in modo da poter inserire correttamente i punti attivi e i dati della mappa immagine durante il processo di creazione del banner carosello in AEM Assets.

   >[!NOTE]
   >
   >Se sei un cliente AEM Sites o Ecommerce, puoi utilizzare la funzione integrata per passare alle pagine dei prodotti e cercare lo SKU esistente nel catalogo dei prodotti. Non è necessario immettere manualmente le variabili punto attivo o mappa immagine. Consulta le informazioni su [configurazione di eCommerce](/help/sites-administering/generic.md).
   >
   >Se sei un cliente di AEM Assets e Dynamic Media, immetti manualmente i dati per gli hotspot e le mappe immagine, e quindi integra l’URL pubblicato o il codice da incorporare con il tuo sistema di gestione dei contenuti di terze parti.

1. Facoltativo: se necessario, [crea un predefinito visualizzatore per set carosello](managing-viewer-presets.md).

   Gli amministratori possono personalizzare il comportamento e l’aspetto del carosello creando un proprio predefinito per visualizzatori Carosello. Il vantaggio principale è che puoi riutilizzare questo predefinito visualizzatore personalizzato per più caroselli. Tuttavia, gli utenti possono anche personalizzare direttamente il comportamento e l’aspetto del carosello durante la creazione del carosello. Questo è l’approccio preferito quando si desidera una progettazione molto specifica per un determinato carosello.

1. [Caricare un banner immagine](#uploading-image-banners).

   Carica i banner immagine che desideri rendere interattivi.

1. [Creare un set carosello](#creating-carousel-sets).

   In Set caroselli, gli utenti navigano tra le immagini dei banner e toccano punti attivi o mappe immagine per accedere ai contenuti pertinenti.

   Per creare un set carosello all’interno di Assets, tocca **[!UICONTROL Crea]**, quindi seleziona **[!UICONTROL Set carosello]**. Aggiungi le risorse alle diapositive e tocca **[!UICONTROL Salva]**. Inoltre, puoi modificare l’aspetto e il comportamento del carosello direttamente nell’editor.

1. [Aggiungi punti attivi o mappe immagine a un banner immagine.](#adding-hotspots-or-image-maps-to-an-image-banner)

   Aggiungi uno o più punti attivi o mappe immagine a un banner immagine e associali ciascuno di essi a un&#39;azione come un collegamento, una visualizzazione rapida o un frammento esperienza. Dopo aver aggiunto punti attivi o mappe immagine, finisci questa attività pubblicando il set carosello. La pubblicazione crea il codice di incorporamento che puoi utilizzare per copiare e applicare alla pagina di destinazione del tuo sito web.

   Vedi [(Facoltativo) Anteprima Dei Banner Carosello](#optional-previewing-carousel-banners) - Facoltativo. Se lo desideri, puoi visualizzare una rappresentazione del set carosello e verificarne l’interattività.

1. [Pubblicare Banner Carosello.](#publishing-carousel-banners)

   Puoi pubblicare un set carosello come faresti con una risorsa. In Assets, passa al set carosello e selezionalo, quindi tocca o tocca **[!UICONTROL Pubblica]**. La pubblicazione di un set carosello attiva l’URL e la stringa di incorporamento.

1. Effettua una delle operazioni seguenti:

   * [Aggiungere un banner carosello alla pagina del sito web](#adding-a-carousel-banner-to-your-website-page) Puoi aggiungere l’URL del banner carosello o il codice di incorporamento copiato nella pagina del sito web.

      * [Integrare il banner carosello con una Quickview esistente](#integrating-the-carousel-banner-with-an-existing-quickview). Se utilizzi un sistema di gestione dei contenuti web di terze parti, dovrai integrare il nuovo banner carosello con l’implementazione Quickview esistente sul sito web.
   * [Aggiungi un banner carosello al sito web in AEM](adding-dynamic-media-assets-to-pages.md) Se sei un cliente AEM Sites puoi aggiungere il set carosello direttamente alla pagina in AEM, utilizzando il componente File multimediali interattivi .


Per modificare i set carosello, consulta [modifica di set carosello](#editing-carousel-sets). Inoltre, puoi visualizzare e modificare [Proprietà del set carosello](/help/assets/managing-assets-touch-ui.md#editing-properties).

## Identificazione delle variabili dei punti attivi e delle mappe immagine {#identifying-hotspot-and-image-map-variables}

Per iniziare, identifica le variabili dinamiche utilizzate dall&#39;implementazione Quickview esistente in modo da poter inserire correttamente i punti attivi o i dati della mappa immagine durante il processo di creazione del set carosello in AEM Assets.

Quando aggiungi punti attivi o mappe immagine a un&#39;immagine banner in AEM Assets, devi assegnare un SKU e variabili aggiuntive facoltative a ogni punto attivo o mappa immagine. Tali variabili vengono utilizzate in seguito per far corrispondere hotspot o mappe immagine con contenuto Quickview.

>[!NOTE]
>
>Se sei un cliente AEM Sites e/o AEM e-commerce, salta questo passaggio. Non è necessario identificare manualmente le variabili dei punti attivi o delle mappe immagine; puoi utilizzare l’integrazione con e-commerce per l’integrazione dei prodotti. Consulta le informazioni su [configurazione di eCommerce](/help/sites-administering/generic.md). Inoltre, puoi utilizzare il componente interattivo e aggiungerlo alla pagina web.
>
>Se sei un cliente AEM Assets o Media, pubblica l’URL o il codice da incorporare e poi ti integra con il tuo sistema di gestione dei contenuti di terze parti e individua manualmente gli hotspot e le mappe immagine.

È importante identificare in modo appropriato il numero e il tipo di variabili da associare ai dati del punto attivo o della mappa immagine. Ogni punto attivo o mappa immagine aggiunta a un&#39;immagine del banner deve contenere informazioni sufficienti per identificare in modo non ambiguo il prodotto nel sistema di back-end esistente. Allo stesso tempo, ogni punto attivo o mappa immagine non deve includere più dati del necessario. Questo perché renderebbe il processo di immissione dei dati eccessivamente complesso e la gestione continua dei punti attivi o delle mappe immagine più soggetta a errori.

Esistono diversi modi per identificare un set di variabili da utilizzare per i dati dei punti attivi o delle mappe immagine.

A volte può essere sufficiente consultare gli specialisti IT responsabili dell&#39;implementazione di Quickview esistente, in quanto è probabile che sappiano quale sia il set minimo di dati necessari per identificare Quickview nel sistema. Tuttavia, nella maggior parte dei casi è anche possibile analizzare semplicemente il comportamento esistente del codice front-end.

La maggior parte delle implementazioni di Quickview utilizza il seguente paradigma:

* L’utente attiva un elemento dell’interfaccia utente sul sito web. Ad esempio, facendo clic su un **[!UICONTROL Visualizzazione rapida]** pulsante .
* Il sito web invia una richiesta Ajax al backend per caricare i dati o il contenuto della visualizzazione rapida, se necessario.
* I dati Quickview vengono tradotti nel contenuto in preparazione al rendering sulla pagina web.
* Infine, il codice front-end esegue il rendering visivo di tali contenuti sullo schermo.

L’approccio consiste quindi nel visitare diverse aree del sito web esistente in cui è implementata la funzione Quickview , attivare la visualizzazione rapida e acquisire l’URL Ajax inviato dalla pagina web per caricare i dati o il contenuto della visualizzazione rapida.

Normalmente non è necessario utilizzare strumenti di debug specializzati. I browser web moderni dispongono di ispettori web che svolgono un lavoro adeguato. Di seguito sono riportati alcuni esempi di browser web che includono ispettori web:

* Per visualizzare tutte le richieste HTTP in uscita in Google Chrome, premi F12 (Windows) o Comando-Opzione-I (Mac) per aprire il pannello Strumenti di sviluppo, quindi tocca il **[!UICONTROL Rete]** scheda .
* In Firefox, è possibile attivare il plug-in Firebug premendo F12 (Windows) o Comando-Opzione-I (Mac) e utilizzando la relativa scheda Net, oppure è possibile utilizzare lo strumento integrato Inspector e la relativa scheda Rete.

Quando il monitoraggio della rete è attivato nel browser, attiva la visualizzazione rapida nella pagina.

Ora trova l&#39;URL Ajax Quickview nel registro di rete e copia l&#39;URL registrato per analisi future. Nella maggior parte dei casi, quando si attiva la visualizzazione rapida sono presenti numerose richieste inviate al server. In genere, l’URL Ajax Quickview è uno dei primi dell’elenco. Dispone di una porzione o di un percorso di stringa di query complessa e il relativo tipo MIME di risposta è `text/html`, `text/xml`oppure `text/javascript`.

Durante questo processo è importante visitare diverse aree del sito web, con diverse categorie di prodotti e tipi. Il motivo è che gli URL Quickview possono avere parti comuni per una determinata categoria di siti web, ma possono essere modificati solo se visiti un’area diversa del sito web.

Nel caso più semplice, l’unica parte variabile nell’URL Quickview è lo SKU del prodotto. In questo caso, il valore SKU è l’unico elemento dati necessario per aggiungere punti attivi o mappe immagine all’immagine del banner.

Tuttavia, in casi complessi, l’URL Quickview presenta diversi elementi diversi rispetto all’SKU, come ID categoria, codice colore, codice dimensione e così via. In questi casi, ogni elemento è una variabile separata nella definizione dei dati del punto attivo o della mappa immagine nella funzione del banner carosello.

Prendi in considerazione i seguenti esempi di URL di visualizzazione rapida e le relative variabili di punti attivi o mappe immagine risultanti:

<table> 
 <tbody> 
  <tr> 
   <td>SKU singolo, trovato nella stringa query.</td> 
   <td><p>Gli URL registrati di Quickview includono quanto segue:</p> 
    <ul> 
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
    </ul> <p>L’unica parte variabile nell’URL è il valore della variabile <code>productId=</code> parametro della stringa query, ed è chiaramente un valore SKU. Pertanto, i nostri hotspot o mappe immagine richiedono solo campi SKU popolati con valori come <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td> 
  </tr> 
  <tr> 
   <td>SKU singolo, trovato nel percorso URL.</td> 
   <td><p>Gli URL registrati di Quickview includono quanto segue:</p> 
    <ul> 
     <li><p><code>https://server/product/6422350843</code></p> </li> 
     <li><p><code>https://server/product/1607745002</code></p> </li> 
     <li><p><code>https://server/product/0086724882</code></p> </li> 
    </ul> <p>La parte variabile si trova nell’ultima parte del percorso e diventa il valore SKU delle hotspot/mappe immagine:<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td> 
  </tr> 
  <tr> 
   <td>SKU e ID categoria nella stringa query.</td> 
   <td><p>Gli URL registrati di Quickview includono quanto segue:</p> 
    <ul> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
    </ul> <p>In questo caso, l’URL contiene due parti diverse. La SKU viene memorizzata nel <code>prodId</code> e l'ID della categoria viene memorizzato nella variabile <code>category=</code>parametro .</p> <p>Di conseguenza, le definizioni dei punti attivi e delle mappe immagine sono coppie. Cioè, un valore SKU e una variabile aggiuntiva denominata <code>categoryId</code>. Le coppie risultanti sono le seguenti:</p> 
    <ul> 
     <li><p>SKU <strong><code>305466</code></strong> e <code>categoryId</code> è <code>1100004</code>.</p> </li> 
     <li><p>SKU <strong><code>310181</code></strong> e <code>categoryId</code> è <strong><code>1100004</code></strong>.</p> </li> 
     <li><p>SKU <strong><code>308706</code></strong> e <code>categoryId</code> è <strong><code>1740148</code></strong>.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Caricamento dei banner immagine {#uploading-image-banners}

Se hai già caricato le immagini da utilizzare, passa al passaggio successivo, [Creazione di set carosello](#creating-carousel-sets). Le immagini utilizzate nel carosello devono essere caricate dopo l’abilitazione di Dynamic Media.

Per caricare i banner immagine, vedi [Caricamento delle risorse](managing-assets-touch-ui.md).

## Creazione di set carosello {#creating-carousel-sets}

>[!NOTE]
>
>Gli utenti non amministrativi devono essere aggiunti al **[!UICONTROL utenti dam]** per creare o modificare banner carosello. In caso di problemi durante la creazione o la modifica, rivolgiti all’amministratore di sistema che può aggiungerti al **utenti dam** gruppo.

**Per creare un set carosello**:

1. In Assets, individua la cartella in cui vuoi creare il set carosello e tocca **[!UICONTROL Crea > Set carosello]**.
1. Sulla **[!UICONTROL Editor banner carosello]** pagina, tocca **[!UICONTROL Tocca per aprire il selettore risorse]** per selezionare l&#39;immagine per la prima diapositiva.

   Sulla **[!UICONTROL Editor banner carosello]** eseguire una delle operazioni seguenti:

   * Nell’angolo in alto a sinistra della pagina, tocca **[!UICONTROL Aggiungi diapositiva]** icona.
   * Vicino al centro della pagina, tocca **[!UICONTROL Tocca per aprire il selettore risorse]**.

   Tocca per selezionare le risorse da includere nel Set carosello. Le risorse selezionate dispongono di un’icona a forma di segno di spunta. Al termine della procedura, tocca **[!UICONTROL Seleziona]**.

   Con il Selettore risorse, puoi cercare le risorse digitando una parola chiave e toccando **[!UICONTROL Invio]**. Per perfezionare i risultati della ricerca, puoi anche applicare i filtri. Puoi filtrare in base a percorso, raccolta, tipo di file e tag. Seleziona il filtro e tocca l’icona **[!UICONTROL Filtro]** nella barra degli strumenti. Per modificare la visualizzazione, tocca il pulsante **[!UICONTROL Visualizza]** icona e selezione **[!UICONTROL Vista a colonne]**, **[!UICONTROL Vista a schede]** oppure **[!UICONTROL Vista a elenco]**.

   Vedi [Utilizzo dei selettori](working-with-selectors.md) per ulteriori informazioni.

1. Continua ad aggiungere diapositive finché non avrai aggiunto tutte le immagini da ruotare nel set carosello.
1. (Facoltativo) Effettua una delle seguenti operazioni:

   * Se necessario, trascinate le diapositive per riordinare le immagini nell’elenco dei set.
   * Per eliminare un’immagine, selezionala e tocca **[!UICONTROL Elimina diapositiva]** sulla barra degli strumenti.
   * Per applicare un predefinito, tocca l’elenco a discesa dei predefiniti nell’angolo in alto a destra della pagina, quindi seleziona un predefinito da applicare al set contemporaneamente.

   Per eliminare una diapositiva, toccate la diapositiva e toccate **[!UICONTROL Elimina diapositiva]** nella barra degli strumenti. Per spostare una diapositiva, toccate l&#39;icona del repository e tenete premuto e spostatevi nella posizione desiderata.

1. Dopo aver aggiunto le immagini nelle diapositive, puoi aggiungere un punto attivo, una mappa immagine o entrambi all’immagine. Vedi [aggiunta di punti attivi o mappe immagine](#adding-hotspots-or-image-maps-to-an-image-banner).
1. Per modificare la struttura e il comportamento visivi dei set carosello, tocca o fai clic sulle schede Comportamento e aspetto e apporta le modifiche necessarie per modificare l’aspetto del banner carosello o il comportamento di componenti specifici. Vedi [gestione dei predefiniti per visualizzatori](viewer-presets.md) per ulteriori informazioni su come utilizzare l’editor per visualizzatori.

   >[!NOTE]
   >
   >Per i banner a carosello, è possibile che si desideri regolare quanto segue:
   >* Durata visualizzata da un’immagine. Per impostazione predefinita, ogni immagine viene visualizzata per 9 secondi.
   >* Animazione. Per impostazione predefinita, ogni transizione di diapositiva è una dissolvenza. È possibile passare a una transizione diapositiva.
   >* Stile dei pulsanti. Gli utenti possono ruotare attraverso i banner toccando ogni punto o numero. È possibile modificare la posizione in cui vengono visualizzati i pulsanti degli indicatori impostati (e se si tratta di uno stile numerico o punteggiato) e la loro dimensione.
   >* Modifica lo stile di evidenziazione di una mappa immagine o dell’icona utilizzata per gli hotspot.
   >* Prima di modificare un predefinito visualizzatore, scegli lo stile su cui desideri basare il predefinito. In caso contrario, quando si inizia a modificare il predefinito visualizzatore, tutte le modifiche andranno perse se si decide di passare a un predefinito diverso.


   Puoi anche visualizzare un’anteprima dell’aspetto del banner carosello. Vedi [(Facoltativo) Anteprima Dei Banner Carosello](#optional-previewing-carousel-banners).

1. Tocca **[!UICONTROL Salva]** una volta finito.

## Aggiunta di punti attivi o mappe immagine a un banner immagine {#adding-hotspots-or-image-maps-to-an-image-banner}

Puoi aggiungere punti attivi o mappe immagine a un banner utilizzando l’editor per set carosello.

Quando aggiungi punti attivi o mappe immagine, puoi definirli come una visualizzazione a comparsa Quickview, come un collegamento ipertestuale o un frammento esperienza.

Vedi [Frammenti esperienza](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Gli strumenti di condivisione social media in Banner carosello non sono supportati quando incorpori il visualizzatore in un frammento esperienza. Per ovviare a questo problema, puoi utilizzare o creare predefiniti visualizzatore privi di strumenti per la condivisione dei social media. Questi predefiniti per visualizzatori consentono di incorporarli correttamente nei Frammenti esperienza.

Quando aggiungi punti attivi o mappe immagine a un&#39;immagine, ricorda di salvare il tuo lavoro. **[!UICONTROL Annulla]** e **[!UICONTROL Ripeti]** le opzioni , situate nell’angolo superiore destro della pagina, sono supportate durante la sessione di creazione/modifica corrente.

Al termine della creazione del banner carosello, è possibile utilizzare **[!UICONTROL Anteprima]** per visualizzare una rappresentazione dell’aspetto del banner carosello per i clienti.

Vedi [(Facoltativo) Anteprima Dei Banner Carosello](#optional-previewing-carousel-banners).

>[!NOTE]
>
>Quando aggiungi punti attivi a un&#39;immagine in un [Immagine interattiva](interactive-images.md) Per un banner carosello, le informazioni relative al punto attivo vengono memorizzate nella stessa posizione di metadati, relativa alla posizione dell’immagine, indipendentemente dal fatto che si tratti di un’immagine interattiva o di un banner carosello. Questa funzionalità consente di riutilizzare facilmente la stessa immagine, insieme ai dati del relativo punto attivo definito, in entrambi i visualizzatori.
>
>Tenere tuttavia presente che i caroselli banner supportano mappe immagine su immagini che possono contenere anche punti attivi; un&#39;immagine interattiva non lo è. Tieni presente questo se desideri creare un’immagine interattiva o un banner carosello che utilizza la stessa immagine. È possibile creare immagini interattive e banner carosello utilizzando copie separate della stessa immagine.

>[!NOTE]
>
>Se modifichi immagini interattive con punti attivi e ritagli l’immagine, questi vengono rimossi.

**Per aggiungere punti attivi a un banner immagine**:

1. Da Risorse, accedi al set carosello che desideri rendere interattivo.
1. Seleziona il set carosello e tocca **[!UICONTROL Modifica]**.
1. Nell’Editor visualizzatore carosello, selezionate la diapositiva da rendere interattiva.
1. Nell’angolo in alto a sinistra della pagina, tocca **[!UICONTROL Punto attivo]** o **[!UICONTROL Mappa immagine]**.
1. Effettua una delle seguenti operazioni:

   * Per gli hotspot: Sull’immagine, tocca la posizione in cui vuoi visualizzare il punto attivo.
   * Per le mappe immagine: Sull’immagine, tocca, quindi trascina dall’alto a sinistra verso il basso a destra per creare l’area della mappa immagine. È possibile regolare le dimensioni della mappa immagine trascinando gli angoli.

   Se necessario, trascina il punto attivo o la mappa immagine in una nuova posizione. Aggiungi altri punti attivi o mappe immagine se necessario.

   Per eliminare un punto attivo o una mappa immagine, tocca la scheda **[!UICONTROL Azioni]**. Seleziona il nome del punto attivo o della mappa immagine da rimuovere dall’intestazione **[!UICONTROL Mappe e punti attivi]** del menu a discesa **[!UICONTROL Tipo selezionato]**. Tocca l’icona **[!UICONTROL Cestino]** accanto al menu, quindi seleziona **[!UICONTROL Elimina]**.

1. Nel campo di testo Nome , digita il nome del punto attivo o della mappa immagine. Questo nome viene visualizzato anche nel **[!UICONTROL Mappe e punti attivi]** elenco a discesa. Specificando un nome è facile identificare il punto attivo o la mappa immagine se si decide di apportarvi modifiche in futuro.
1. Effettua una delle seguenti operazioni nel **[!UICONTROL Azioni]** scheda:

   * Tocca **[!UICONTROL Quickview]**.

      * Se sei un cliente AEM Sites ed e-commerce, tocca il **[!UICONTROL Selettore prodotto]** icona (lente di ingrandimento) per aprire **[!UICONTROL Seleziona prodotto]** pagina. Tocca il prodotto che desideri utilizzare, quindi tocca il segno di spunta nell’angolo in alto a destra della pagina per tornare al **[!UICONTROL Editor banner carosello]**.
      * Se non sei un cliente AEM Sites o Ecommerce

         * Vedi [Identificazione delle variabili dei punti attivi](#identifying-hotspot-and-image-map-variables) definire queste variabili.
         * Quindi, inserisci manualmente il valore SKU. In **[!UICONTROL Valore SKU]** campo di testo, digitare la SKU del prodotto (Stock Keeping Unit), che è un identificatore univoco per ogni prodotto o servizio distinto offerto. Il valore SKU inserito popola automaticamente la parte variabile del modello Quickview in modo che il sistema sappia associare il punto attivo toccato a una particolare visualizzazione rapida SKU.
         * (Facoltativo) Se nella visualizzazione rapida sono presenti altre variabili che è necessario utilizzare per identificare ulteriormente un prodotto, tocca **[!UICONTROL Aggiungi variabile generica]**. Nel campo di testo, specifica una variabile aggiuntiva. Ad esempio: `category=Mens` è una variabile aggiunta.
         * Vedi [Utilizzo dei selettori](working-with-selectors.md) per ulteriori informazioni.
   * Tocca **[!UICONTROL Collegamento ipertestuale]**.

      * Se sei un cliente AEM Sites, tocca il **[!UICONTROL Selettore sito]** icona (cartella) per passare a un URL.

         >[!NOTE]
         >Il metodo di collegamento basato su URL non è possibile se il contenuto interattivo include collegamenti con URL relativi, in particolare con le pagine AEM Sites.

      * Se sei un cliente indipendente, nella **[!UICONTROL HREF]** campo di testo, specifica il percorso URL completo di una pagina web collegata.

         Assicurati di specificare se aprire il collegamento in una nuova scheda del browser (impostazione predefinita consigliata) o nella stessa scheda.

         Vedi [Utilizzo dei selettori](working-with-selectors.md) per ulteriori informazioni.
   * Tocca **[!UICONTROL Frammento esperienza]**.

      * Se sei un cliente AEM Sites, tocca il **[!UICONTROL Ricerca]** icona (lente di ingrandimento) per aprire la pagina Frammento esperienza . Tocca il frammento esperienza da utilizzare, quindi tocca **[!UICONTROL Seleziona]** nell’angolo in alto a destra della pagina per tornare alla pagina Gestione punti attivi.

         Vedi [Frammenti esperienza](/help/sites-authoring/experience-fragments.md).

         **Nota**: Gli strumenti di condivisione social media in Banner carosello non sono supportati quando incorpori il visualizzatore in un frammento esperienza. Per ovviare a questo problema, puoi utilizzare o creare predefiniti visualizzatore privi di strumenti per la condivisione dei social media. Questi predefiniti per visualizzatori consentono di incorporarli correttamente nei Frammenti esperienza.

      * Specifica la larghezza e l’altezza del frammento esperienza così come apparirà sul banner.

   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   Puoi anche visualizzare un’anteprima dell’aspetto del banner carosello. Vedi [(Facoltativo) Anteprima Dei Banner Carosello](#optional-previewing-carousel-banners).

1. Tocca **[!UICONTROL Salva]**.
1. Pubblica il set carosello. La pubblicazione crea il codice di incorporamento o l’URL che puoi utilizzare sulla pagina del tuo sito web. Se sei un cliente AEM Sites, puoi aggiungere il set carosello direttamente alla tua pagina web.

   Vedi [Pubblicazione delle risorse](publishing-dynamicmedia-assets.md).

   Vedi [Aggiunta di un set carosello alla pagina di destinazione del sito web](#adding-a-carousel-banner-to-your-website-page)

## Modifica dei set carosello {#editing-carousel-sets}

>[!NOTE]
>
>Gli utenti non amministrativi devono essere aggiunti al **[!UICONTROL utenti dam]** per poter creare o modificare banner carosello. In caso di problemi durante la creazione o la modifica, rivolgiti all’amministratore di sistema che può aggiungerti al **[!UICONTROL utenti dam]** gruppo.

È possibile eseguire diverse attività di modifica sui set carosello, ad esempio:

* Aggiungi le diapositive a un set carosello. Vedi anche [Utilizzo dei selettori](working-with-selectors.md).
* Riordinare le diapositive nel set carosello.
* Elimina le risorse nel set carosello.
* Applica un predefinito visualizzatore.
* Elimina il set carosello.
* Aggiungi o modifica punti attivi e mappe immagine. Vedi anche [Utilizzo dei selettori](working-with-selectors.md).

Se modifichi immagini interattive con punti attivi e ritagli l’immagine, questi vengono rimossi.

**Per modificare un set carosello**:

1. Effettua una delle seguenti operazioni:

   * Passa il puntatore del mouse su una risorsa Set carosello, quindi tocca **[!UICONTROL Modifica]** (icona a forma di matita).
   * Passa il puntatore del mouse su una risorsa del set carosello e tocca **[!UICONTROL Seleziona]** (icona a forma di segno di spunta), quindi tocca **[!UICONTROL Modifica]** sulla barra degli strumenti.
   * Tocca una risorsa Set carosello, quindi nell’angolo in alto a sinistra della pagina tocca **[!UICONTROL Modifica]** (icona a forma di matita).

1. Per modificare il set carosello, effettuate una delle seguenti operazioni:

   * Per aggiungere una diapositiva, tocca **[!UICONTROL Aggiungi diapositiva]** , quindi individua la risorsa da aggiungere alla diapositiva e tocca il segno di spunta.
   * Per riordinare le diapositive, trascinate una diapositiva in una nuova posizione (selezionate l&#39;icona di riordino per spostare gli elementi).
   * Per aggiungere un punto attivo o una mappa immagine, tocca le icone del punto attivo o della mappa immagine e vedi [aggiunta di punti attivi e mappe immagine](#adding-hotspots-or-image-maps-to-an-image-banner).
   * Per modificare l’aspetto o il comportamento del set carosello, tocca **[!UICONTROL Aspetto]** scheda o **[!UICONTROL Comportamento]** , quindi imposta le opzioni desiderate.
   * Per modificare punti attivi o mappe immagine, nella diapositiva appropriata seleziona un punto attivo o una mappa immagine e apporta le modifiche necessarie nella sezione **[!UICONTROL Azioni]** scheda .
   * Per eliminare una diapositiva, selezionala e tocca **[!UICONTROL Elimina diapositiva]** sulla barra degli strumenti.
   * Per applicare un predefinito, tocca l’elenco a discesa dei predefiniti nell’angolo in alto a destra della pagina, quindi seleziona un predefinito visualizzatore.
   * Per eliminare un intero set carosello, accedi al set carosello, selezionalo, quindi tocca **[!UICONTROL Elimina]**.

## (Facoltativo) Anteprima Dei Banner Carosello {#optional-previewing-carousel-banners}

È possibile utilizzare **[!UICONTROL Anteprima]** per vedere come apparirà il banner carosello ai clienti e per testare gli hotspot e le mappe immagine dei banner carosello in modo che si comportino come previsto.

Quando sei soddisfatto del banner carosello, puoi pubblicarlo.

* Vedi [Incorporamento del visualizzatore di video o immagini in una pagina web](embed-code.md).
* Vedi [Collegamento di URL all’applicazione web](linking-urls-to-yourwebapplication.md). Il metodo di collegamento basato su URL non è possibile se il contenuto interattivo include collegamenti con URL relativi, in particolare con le pagine AEM Sites.
* Vedi [Aggiunta di risorse Dynamic Media alle pagine.](adding-dynamic-media-assets-to-pages.md)

Puoi visualizzare in anteprima i banner carosello dall’Editor carosello (metodo preferito) o dal **[!UICONTROL Visualizzatori]** elenco.

**Per visualizzare in anteprima i banner a carosello**:

1. In **[!UICONTROL Risorse]**, passa a un banner carosello esistente creato e tocca per aprirlo.
1. Tocca **[!UICONTROL Modifica]**.
1. Nell’elenco dei predefiniti visualizzatore nell’angolo a destra della barra degli strumenti, seleziona un visualizzatore per visualizzare l’anteprima del banner carosello.

   ![experience_fragment-carouselbanner-riquadro a discesa](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Tocca **[!UICONTROL Anteprima]**.
1. Tocca i punti attivi o le mappe immagine sull’immagine per testare le azioni associate.

**Per visualizzare in anteprima i banner a carosello dall’elenco Visualizzatori**:

1. In **[!UICONTROL Risorse]**, passa a un banner carosello esistente creato e tocca per aprirlo.
1. Vicino all&#39;angolo superiore sinistro del **[!UICONTROL Anteprima]** , tocca **[!UICONTROL Contenuto]** icona.
1. In **[!UICONTROL Visualizzatori]** nel pannello a sinistra della pagina, tocca il nome del predefinito visualizzatore del banner carosello da usare.
1. Tocca i punti attivi o le mappe immagine sull’immagine per testare le azioni associate.

## Pubblicazione dei banner a carosello {#publishing-carousel-banners}

Per utilizzarlo, devi pubblicare il carosello. La pubblicazione di un set carosello attiva l’URL e il codice di incorporamento. Pubblica anche il carosello su Dynamic Media cloud, integrato con una rete CDN per una distribuzione scalabile e performante.

Se utilizzi un’immagine interattiva esistente con punti attivi per il banner carosello, devi pubblicare separatamente l’immagine interattiva dopo aver pubblicato il banner carosello.

Inoltre, se modifichi un’immagine interattiva pubblicata precedentemente che utilizzi in un banner carosello, devi pubblicare l’immagine interattiva prima che tali modifiche si riflettano nel banner carosello.

Vedi [Pubblicazione delle risorse Dynamic Media](publishing-dynamicmedia-assets.md) per informazioni su come pubblicare banner carosello.

## Aggiunta di un banner carosello alla pagina del sito web {#adding-a-carousel-banner-to-your-website-page}

Dopo aver caricato le immagini del banner per creare un carosello, aggiunto gli hotspot e/o le mappe immagine al banner e pubblicato il set carosello, ora puoi aggiungerlo alla pagina del sito web esistente.

Se sei un cliente di AEM Sites, puoi aggiungere il banner carosello direttamente alla pagina trascinando il componente File multimediali interattivi nella pagina. Vedi [Aggiunta di risorse Dynamic Media alle pagine.](adding-dynamic-media-assets-to-pages.md)

Tuttavia, se sei un cliente di risorse AEM autonomo puoi aggiungere manualmente il banner carosello alla pagina di destinazione del sito web come descritto in questa sezione.

1. Copia il codice di incorporamento del set carosello pubblicato.

   Vedi [Incorporamento del visualizzatore di video o immagini in una pagina web](embed-code.md).

1. Aggiungi il codice di incorporamento copiato da AEM Assets alla pagina web.

   Il codice di incorporamento copiato è reattivo e dovrebbe quindi adattarsi automaticamente all’area di incorporamento della pagina.

## Integrazione del banner carosello con una visualizzazione rapida esistente {#integrating-the-carousel-banner-with-an-existing-quickview}

Questa attività si applica solo se sei un cliente AEM Assets autonomo.

L’ultimo passaggio di questo processo consiste nell’integrare il banner carosello con un’implementazione Quickview esistente sul sito web. Ogni implementazione di Quickview è unica ed è necessario un approccio specifico che molto probabilmente coinvolge l&#39;assistenza di una persona IT front-end.

L&#39;implementazione di Quickview esistente rappresenta normalmente una catena di azioni correlate che avvengono sulla pagina web nel seguente ordine:

1. Un utente attiva un elemento nell’interfaccia utente del sito web.
1. Il codice front-end ottiene un URL Quickview basato sull’elemento dell’interfaccia utente attivato nel passaggio 1.
1. Il codice front-end invia una richiesta Ajax utilizzando l’URL ottenuto al passaggio 2.
1. La logica di back-end restituisce i dati o il contenuto Quickview corrispondenti al codice front-end.
1. Il codice front-end carica i dati o il contenuto di Quickview.
1. Facoltativamente, il codice front-end converte i dati Quickview caricati in una rappresentazione HTML.
1. Il codice front-end visualizza una finestra di dialogo o un pannello modale ed esegue il rendering del contenuto HTML sullo schermo per l’utente finale.

Queste chiamate potrebbero non rappresentare chiamate API pubbliche indipendenti che possono essere richiamate dalla logica della pagina web da un passaggio arbitrario. Si tratta invece di una chiamata concatenata in cui ogni passaggio successivo viene nascosto nell’ultima fase (callback) del passaggio precedente.

Contemporaneamente alla sostituzione del passaggio 1 e in parte del passaggio 2 da parte del banner carosello, quando un utente fa clic su un punto attivo o una mappa immagine all’interno del banner carosello, l’interazione dell’utente viene gestita dal visualizzatore. Il visualizzatore restituisce un evento alla pagina web che contiene tutti i dati del punto attivo o della mappa immagine precedentemente aggiunti.

In un tale gestore di eventi, il codice front-end effettua le seguenti operazioni:

* Ascolta un evento emesso dal banner carosello.
* Crea un URL di visualizzazione rapida basato sui dati del punto attivo o della mappa immagine.
* Attiva il processo di caricamento della visualizzazione rapida dal back-end e di rendering sullo schermo per la visualizzazione.

Il codice di incorporamento restituito da AEM Assets dispone già di un gestore eventi ready-to-use in posizione, che viene aggiunto un commento.

Pertanto, è solo necessario rimuovere il commento dal codice e sostituire il corpo del gestore fittizio con il codice specifico per la pagina web specifica.

Il processo di costruzione dell’URL di visualizzazione rapida è sostanzialmente opposto al processo utilizzato per identificare le variabili dei punti attivi e delle mappe immagine trattate in precedenza.

Vedi [Identificazione delle variabili dei punti attivi e delle mappe immagine](#identifying-hotspot-and-image-map-variables).

L&#39;ultimo passaggio per attivare l&#39;URL Quickview e attivare il pannello Quickview richiede molto probabilmente l&#39;assistenza di un esperto IT front-end del reparto IT. Hanno la conoscenza di sapere come attivare con precisione l&#39;implementazione di Quickview dal passaggio appropriato, avendo un URL di Quickview pronto all&#39;uso.

## Utilizzo delle visualizzazioni rapide per creare finestre a comparsa personalizzate {#using-quickviews-to-create-custom-pop-ups}

Vedi [Utilizzo delle Quickview per creare pop-up personalizzati](custom-pop-ups.md).
