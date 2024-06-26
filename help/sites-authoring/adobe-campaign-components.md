---
title: Componenti di Adobe Campaign
seo-title: Adobe Campaign Components
description: Quando si esegue l’integrazione con Adobe Campaign, sono disponibili componenti per le newsletter e i moduli
seo-description: When you integrate with Adobe Campaign, you have components available for when working with newsletters and with forms
uuid: d1fb8649-8aae-49a5-8663-1b7cb74ee0e7
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: f328cd1e-30a3-42d2-88b7-64455ee9eb1f
exl-id: 02641496-188b-465c-9256-b2e377eb685c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2801'
ht-degree: 7%

---

# Componenti di Adobe Campaign{#adobe-campaign-components}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Quando si esegue l’integrazione con Adobe Campaign, sono disponibili componenti per le newsletter e i moduli. Entrambi sono descritti in questo documento.

## Componenti per newsletter di Adobe Campaign {#adobe-campaign-newsletter-components}

Tutti i componenti di Campaign seguono le best practice descritte in [Tecniche consigliate per i modelli e-mail](/help/sites-administering/best-practices-for-email-templates.md) e si basano sul linguaggio di markup Adobe [HTL](https://helpx.adobe.com/it/experience-manager/htl/using/overview.html).

Quando apri una newsletter/e-mail configurata per l’integrazione con Adobe Campaign, dovresti visualizzare i seguenti componenti nel **Newsletter Adobe Campaign** sezione:

* Intestazione (Campaign)
* Immagine (Campaign)
* Collegamento (Campagna)
* Modello immagini Dynamic Media (Campaign)
* Riferimento di destinazione (Campaign)
* Testo e immagine (Campaign)
* Testo e personalizzazione (Campaign)

Una descrizione di questi componenti si trova nella sezione seguente.

I componenti vengono visualizzati come segue:

![chlimage_1-105](assets/chlimage_1-105.png)

### Intestazione (Campaign) {#heading-campaign}

Il componente di intestazione può:

* Visualizza il nome della pagina corrente lasciando **Titolo** campo vuoto.
* Visualizza un testo specificato nel **Titolo** campo .

È possibile modificare **Intestazione (Campaign)** componenti direttamente. Lascia vuoto per usare il titolo della pagina.

![chlimage_1-106](assets/chlimage_1-106.png)

Puoi configurare quanto segue:

* **Titolo**
Se desideri utilizzare un nome diverso dal titolo della pagina, inseriscilo qui.

* **Livello di intestazione (1, 2, 3, 4)**
Il livello di intestazione basato sulle dimensioni da 1 a 4 del titolo HTML.

L’esempio seguente mostra come viene visualizzato un componente Intestazione (Campaign) .

![chlimage_1-107](assets/chlimage_1-107.png)

### Immagine (Campaign) {#image-campaign}

Il componente Immagine (campagna) visualizza un’immagine e il relativo testo in base ai parametri specificati.

Puoi caricare un’immagine, quindi modificarla e manipolarla (ad esempio, ritagliarla, ruotarla, aggiungere un collegamento/titolo/testo).

Puoi trascinare un’immagine da [Browser risorse](/help/sites-authoring/author-environment-tools.md#assets-browser) direttamente sul componente o sul relativo [Finestra di dialogo Configura](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste). Puoi anche caricare un’immagine dalla finestra di dialogo Configura (Configure); questa finestra di dialogo controlla anche tutte le definizioni e le manipolazioni dell&#39;immagine:

![chlimage_1-108](assets/chlimage_1-108.png)

>[!NOTE]
>
>È necessario immettere le informazioni nel **Testo Alt** oppure l&#39;immagine non può essere salvata.

Dopo il caricamento dell’immagine (e non prima) puoi utilizzare [modifica diretta](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) per ritagliare/ruotare l’immagine come necessario:

![](do-not-localize/chlimage_1-10.png)

>[!NOTE]
>
>L’editor locale utilizza le dimensioni e le proporzioni originali dell’immagine durante la modifica. È inoltre possibile specificare le proprietà relative a altezza e larghezza. Eventuali restrizioni relative a dimensioni e proporzioni definite nelle proprietà vengono applicate al salvataggio delle modifiche.
>
>A seconda dell’istanza, le restrizioni minime e massime possono essere imposte anche dal [progettazione della pagina](/help/sites-developing/designer.md); vengono sviluppate durante l’implementazione del progetto.

Sono disponibili diverse opzioni aggiuntive nella modalità di modifica a schermo intero; ad esempio, mappa e zoom:

![](do-not-localize/chlimage_1-11.png)

Quando un’immagine viene caricata, puoi configurare quanto segue:

* **Mappa**

   Per mappare un’immagine, seleziona Mappa. È possibile specificare come si desidera creare la mappa immagine (rettangolare, poligonale e così via) e la destinazione dell’area.

* **Ritaglia**

   Selezionate Ritaglia per ritagliare un’immagine. Utilizza il mouse per ritagliare l&#39;immagine.

* **Rotazione**

   Per ruotare un’immagine, selezionate Ruota. Utilizzare ripetutamente finché l&#39;immagine non viene ruotata nel modo desiderato.

* **Cancella**

   Rimuovi l&#39;immagine corrente.

* Barra Zoom (solo interfaccia classica)

   Per ingrandire e ridurre l’immagine, utilizzate la barra di scorrimento al di sotto dell’immagine (sopra i pulsanti OK e Annulla)

* **Titolo**

   Titolo dell’immagine.

* **Testo Alt**

   Testo alternativo da utilizzare per la creazione di contenuto accessibile.

* **Collega a**

   Crea un collegamento a risorse o altre pagine all’interno del sito web.

* **Descrizione**

   Una descrizione dell’immagine.

* **Dimensione**

   Imposta l’altezza e la larghezza dell’immagine.

>[!NOTE]
>
>È necessario immettere le informazioni nel **Testo Alt** nel campo **Avanzate** oppure l&#39;immagine non può essere salvata e viene visualizzato il seguente messaggio di errore:
>
>`Validation failed. Verify the values of the marked fields.`

L’esempio seguente mostra come viene visualizzato un componente Immagine (Campaign) .

![chlimage_1-109](assets/chlimage_1-109.png)

### Collegamento (Campagna) {#link-campaign}

Il componente Collegamento (Campaign) consente di aggiungere un collegamento alla newsletter.

Puoi configurare quanto segue in **Visualizzazione**, **Informazioni URL** oppure **Avanzate** schede:

* **Didascalia collegamento**

   Didascalia del collegamento. Testo visualizzato dagli utenti.

* **Descrizione dei collegamenti**

   Aggiunge ulteriori informazioni su come utilizzare il collegamento.

* **LinkType**

   Nell’elenco a discesa , seleziona tra **URL personalizzato** e **Documento adattivo**. Questo campo è obbligatorio. Se selezioni URL personalizzato, puoi fornire l’URL del collegamento. Se si seleziona Documento adattivo, è possibile specificare il percorso del documento.

* **Parametro URL aggiuntivo**

   Aggiungi eventuali parametri URL aggiuntivi. Fai clic su Aggiungi elemento per aggiungere più elementi.

>[!NOTE]
>
>È necessario immettere le informazioni nel **Tipo di collegamento** nel campo **Informazioni URL** oppure il componente non può essere salvato e viene visualizzato il seguente messaggio di errore:
>
>`Validation failed. Verify the values of the marked fields.`

L’esempio seguente mostra come viene visualizzato il componente Collegamento (Campaign) .

![chlimage_1-110](assets/chlimage_1-110.png)

### Modello immagini di Scene7 (Campaign) {#scene-image-template-campaign}

[Modelli immagine Scene7](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/quick-start-template-basics.html#template-basics) I livelli sono file immagine a livelli, in cui il contenuto e le proprietà possono essere parametrizzati per la variabilità. La **Modello immagini** componente consente di utilizzare i modelli Dynamic Media Classic (precedentemente Scene7) nelle newsletter e modificare i valori dei parametri dei modelli. Inoltre, puoi utilizzare le variabili dei metadati Adobe Campaign all&#39;interno dei parametri, in modo che ogni utente possa visualizzare l&#39;immagine in modo personalizzato.

![chlimage_1-111](assets/chlimage_1-111.png)

Fai clic su **Modifica** per configurare il componente . Puoi configurare le impostazioni descritte in questa sezione. Questo modello di immagine Dynamic Media Classic (precedentemente Scene7) è descritto in dettaglio in [Componente Modello immagini Scene7](/help/assets/scene7.md#image-template).

Inoltre, il pannello dei parametri elenca tutti i parametri del modello definiti per il modello in Dynamic Media Classic (precedentemente Scene7). Per ciascuno di questi parametri, puoi adattare il valore, inserire variabili o reimpostarli sul valore predefinito.

![chlimage_1-112](assets/chlimage_1-112.png)

### Riferimento di destinazione (Campaign) {#targeted-reference-campaign}

Il componente Riferimento di destinazione (Campaign) consente di creare un riferimento a un paragrafo di destinazione.

In questo componente, accedi al paragrafo di destinazione per selezionarlo.

Fai clic sull’icona della cartella per passare al paragrafo a cui si desidera fare riferimento. Al termine, fare clic sul segno di spunta.

### Testo e immagine (Campaign) {#text-image-campaign}

Il componente Testo e immagine (Campaign) aggiunge un blocco di testo e un’immagine.

Quando fai clic per configurare il componente, seleziona Testo o Immagine .

![chlimage_1-113](assets/chlimage_1-113.png)

Selezione **Testo** visualizza un editor in linea:

![](do-not-localize/chlimage_1-12.png)

Selezione **Immagine** visualizza l’editor locale per le immagini:

![](do-not-localize/chlimage_1-13.png)

Vedi [Componente Immagine (Campaign)](#image-campaign) per ulteriori informazioni sulle operazioni con le immagini. Vedi [Componente Testo e personalizzazione (Campaign)](#text-personalization-campaign) per ulteriori informazioni sulle operazioni con il testo.

Come per i componenti Testo e personalizzazione (Campaign) e Immagine (Campaign), puoi configurare:

* **Testo**

   Inserisci testo. Utilizzare la barra degli strumenti per modificare la formattazione, creare elenchi e aggiungere collegamenti.

* **Immagine**

   Trascina un’immagine da Content Finder oppure fai clic su per individuare un’immagine. Ritaglia o ruota come necessario.

* **Proprietà immagine** (**Proprietà immagine avanzate**)

   Consente di specificare quanto segue:

   * **Titolo**

      il titolo del blocco; Il mouse viene visualizzato al passaggio del mouse.

   * **Testo Alt**

      Testo alternativo che verrà mostrato qualora l’immagine non sia disponibile.

   * **Collega a**

      Crea un collegamento a risorse o altre pagine all’interno del sito web.

   * **Descrizione**

      Una descrizione dell’immagine.

   * **Dimensione**

      Imposta l’altezza e la larghezza dell’immagine.

>[!NOTE]
>
>La **Testo Alt** nel campo **Avanzate** è necessaria una scheda oppure il componente non può essere salvato e viene visualizzato il seguente messaggio di errore:
>
>`Validation failed. Verify the values of the marked fields.`

L’esempio seguente mostra come viene visualizzato un componente Testo e immagine (Campaign) .

![chlimage_1-114](assets/chlimage_1-114.png)

### Testo e personalizzazione (Campaign) {#text-personalization-campaign}

Il componente Testo e personalizzazione (Campaign) consente di inserire un blocco di testo utilizzando un editor WYSIWYG, con funzionalità fornite da [Editor Rich Text](/help/sites-authoring/rich-text-editor.md). Inoltre, questo componente consente di utilizzare i campi di contesto e i blocchi di personalizzazione disponibili in Adobe Campaign; vedere [Inserimento di personalizzazioni](/help/sites-authoring/campaign.md#inserting-personalization).

La selezione di icone consente di formattare il testo, con caratteristiche del font, allineamento, collegamenti, elenchi e rientri. La funzionalità è sostanzialmente la stessa in [entrambe le interfacce](/help/sites-authoring/editing-content.md), anche se l’aspetto è diverso:

![chlimage_1-115](assets/chlimage_1-115.png)

Nell’editor interno puoi aggiungere testo, modificare la giustificazione, aggiungere e rimuovere collegamenti, aggiungere campi di contesto o blocchi di personalizzazione e accedere alla modalità a schermo intero. Al termine dell’aggiunta di testo/personalizzazione, seleziona il segno di spunta per salvare le modifiche (o x per annullare). Vedi [Modifica locale](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) per ulteriori informazioni.

>[!NOTE]
>
>* I campi di personalizzazione disponibili dipendono dal modello Adobe Campaign a cui è collegata la newsletter.
>* Dopo aver selezionato una persona da ContextHub, i campi di personalizzazione vengono sostituiti automaticamente dai dati del profilo selezionato.
>
>Vedi [Inserimento di personalizzazioni](/help/sites-authoring/campaign.md#inserting-personalization).

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>Solo i campi definiti nel **nms:seedMember** viene preso in considerazione lo schema o una delle sue estensioni. Attributi delle tabelle collegate a **nms:seedMember** non sono disponibili.

## Componenti per moduli di Adobe Campaign {#adobe-campaign-form-components}

I componenti di Adobe Campaign consentono di creare un modulo che gli utenti compilano per iscriversi a una newsletter, annullare l’iscrizione a una newsletter o aggiornare i profili utente. Vedi [Creazione di Adobe Campaign Forms](/help/sites-authoring/adobe-campaign-forms.md) per ulteriori informazioni.

Ogni campo componente può essere collegato a un campo del database Adobe Campaign. I campi disponibili variano a seconda del tipo di dati che contengono, come descritto nella sezione [Componenti e tipi di dati](#components-and-data-type). Se estendi lo schema dei destinatari in Adobe Campaign, i nuovi campi saranno disponibili nei componenti i cui tipi di dati corrispondono.

Quando si apre un modulo configurato per l’integrazione con Adobe Campaign, vengono visualizzati i seguenti componenti nel **Adobe Campaign** sezione:

* Casella di selezione (Campaign)
* Campo data (Campaign) e campo data/HTML5 (Campaign)
* Chiave principale crittografata (Campaign)
* Visualizzazione errori (Campaign)
* Chiave riconciliazione nascosta (Campaign)
* Campo numerico (Campaign)
* Campo opzione (Campaign)
* Lista di controllo delle iscrizioni (Campaign)
* Campo testo (Campaign)

I componenti vengono visualizzati come segue:

![chlimage_1-117](assets/chlimage_1-117.png)

Questa sezione descrive in dettaglio ogni componente.

### Componenti e tipi di dati {#components-and-data-type}

Nella tabella seguente sono descritti i componenti disponibili per visualizzare e modificare i dati del profilo Adobe Campaign. Ogni componente può essere mappato su un campo del profilo Adobe Campaign per visualizzarne il valore e aggiornare il campo quando il modulo viene inviato. I diversi componenti possono essere associati solo a campi di un tipo di dati appropriato.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Componente</strong></p> </td> 
   <td><p><strong>Tipo di dati del campo Adobe Campaign</strong></p> </td> 
   <td><p><strong>Campo di esempio</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Casella di selezione (Campaign)</p> </td> 
   <td><p>booleano</p> </td> 
   <td><p>Nessun contatto (da qualsiasi canale)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Campo data (Campaign)</p> <p>Campo data/HTML 5 (Campaign)</p> </td> 
   <td><p>data</p> </td> 
   <td><p>Data di nascita</p> </td> 
  </tr> 
  <tr> 
   <td><p>Campo numerico (Campaign)</p> </td> 
   <td><p>numerico (byte, breve, lungo, doppio)</p> </td> 
   <td><p>Età</p> </td> 
  </tr> 
  <tr> 
   <td><p>Campo opzione (Campaign)</p> </td> 
   <td><p>byte con valori associati</p> </td> 
   <td><p>Genere</p> </td> 
  </tr> 
  <tr> 
   <td><p>Campo testo (Campaign)</p> </td> 
   <td><p>stringa</p> </td> 
   <td><p>E-mail</p> </td> 
  </tr> 
 </tbody> 
</table>

### Impostazioni comuni alla maggior parte dei componenti {#settings-common-to-most-components}

I componenti Adobe Campaign hanno impostazioni comuni a tutti i componenti (ad eccezione dei componenti Chiave principale crittografata e Chiave di riconciliazione nascosta).

Nella maggior parte dei componenti, puoi configurare quanto segue:

#### Titolo e testo {#title-and-text}

![chlimage_1-118](assets/chlimage_1-118.png)

* **Titolo**

   Se desideri utilizzare un nome diverso dal nome dell’elemento, inseriscilo qui.

* **Nascondi titolo**

   Selezionare questa casella di controllo se non si desidera che il titolo sia visibile.

* **Descrizione**

   Aggiungi una descrizione al campo per fornire ulteriori informazioni agli utenti.

* **Mostra solo valore**

   Mostra solo il valore, se presente

#### Adobe Campaign {#adobe-campaign}

Puoi configurare quanto segue:

* **Mappatura**

   Se appropriato, seleziona un campo di personalizzazione Adobe Campaign .

* **Chiave riconciliazione**

   Selezionare questa casella di controllo se il campo fa parte della chiave di riconciliazione.

![chlimage_1-119](assets/chlimage_1-119.png)

#### Vincoli {#constraints}

* **Obbligatorio**

   Seleziona questa casella di controllo per rendere obbligatorio questo componente; in altre parole, gli utenti devono immettere un valore.

* **Messaggio richiesto**

   Facoltativamente, aggiungi un messaggio che indica che il campo è obbligatorio.

![chlimage_1-120](assets/chlimage_1-120.png)

#### Attribuzione stile {#styling}

* **CSS**
Immetti le classi CSS da utilizzare per questo componente.

![chlimage_1-121](assets/chlimage_1-121.png)

### Casella di selezione (Campaign) {#checkbox-campaign}

Il componente Casella di controllo (Campaign) consente all’utente di modificare i campi del profilo Adobe Campaign che sono di tipo dati booleano. Ad esempio, puoi avere un componente Casella di selezione (Campaign) che consente al destinatario di specificare che non desidera essere contattato tramite alcun canale.

È possibile [configurare le impostazioni comuni alla maggior parte dei componenti di Adobe Campaign](#settings-common-to-most-components) nel componente Casella di selezione (Campaign).

L’esempio seguente mostra come viene visualizzato un componente Casella di selezione (Campaign).

![chlimage_1-122](assets/chlimage_1-122.png)

### Campo data (Campaign) e campo data/HTML 5 (Campaign) {#date-field-campaign-and-date-field-html-campaign}

Utilizza il campo data per consentire ai destinatari di impostare una data; ad esempio, puoi desiderare che i destinatari specifichino le rispettive date di nascita. Il formato della data corrisponde al formato utilizzato nella tua istanza Adobe Campaign.

Oltre a [impostazioni comuni alla maggior parte dei componenti di Adobe Campaign](#settings-common-to-most-components), puoi configurare quanto segue:

* **Vincoli - Vincolo** a discesa

   È possibile selezionare - **Nessuno** o **Data**- per aggiungere il vincolo di una data o nessun vincolo. Se si seleziona la data, le risposte inserite dagli utenti nel campo devono essere in un formato data.

* **Messaggio vincolo**

   Inoltre, è possibile aggiungere un messaggio di vincolo in modo che gli utenti sappiano come formattare correttamente le risposte.
* **Stile - Larghezza**
Per regolare la larghezza del campo, tocca o fai clic sul pulsante 
**+** e **-** icone o immissione di un numero.

L’esempio seguente mostra come viene visualizzato un componente Campo data (Campaign) con la larghezza regolata.

![chlimage_1-123](assets/chlimage_1-123.png)

### Chiave principale crittografata (Campaign) {#encrypted-primary-key-campaign}

Questo componente definisce il nome del parametro URL che conterrà l’identificatore di un profilo Adobe Campaign (**Identificatore risorsa principale** o **Chiave primaria crittografata** in Adobe Campaign Standard e 6.1, rispettivamente).

Visualizzazione e modifica dei dati del profilo Adobe Campaign in ciascun modulo **deve** include un componente Chiave principale crittografata.

Puoi configurare quanto segue nel componente Chiave principale crittografata (Campaign) :

* **Titolo e testo - Nome elemento**

   Impostazione predefinita di encrypkPK. È sufficiente modificare il nome dell’elemento quando è in conflitto con il nome di un altro elemento del modulo. Due campi modulo non possono avere lo stesso nome elemento.
* **Adobe Campaign - parametro URL**
Aggiungi il parametro URL per l’EPK. Ad esempio, puoi utilizzare il valore 
**epk**.

L’esempio seguente mostra la visualizzazione di un componente Chiave principale crittografata (Campaign).

![chlimage_1-124](assets/chlimage_1-124.png)

### Visualizzazione errori (Campaign) {#error-display-campaign}

Questo componente consente di visualizzare gli errori di backend. Per il corretto funzionamento del componente, è necessario impostare la gestione degli errori del modulo su Inoltra .

L’esempio seguente mostra la visualizzazione di un componente Visualizzazione errori (Campaign).

![chlimage_1-125](assets/chlimage_1-125.png)

### Chiave riconciliazione nascosta (Campaign) {#hidden-reconciliation-key-campaign}

Il componente Chiave riconciliazione nascosta (Campaign) consente di aggiungere a un modulo campi nascosti come parte della chiave di riconciliazione.

Puoi configurare quanto segue nel componente Chiave riconciliazione nascosta (Campaign) :

* **Titolo e testo - Nome elemento**

   Impostazione predefinita di reconcilKey. È sufficiente modificare il nome dell’elemento quando è in conflitto con il nome di un altro elemento del modulo. Due campi modulo non possono avere lo stesso nome elemento.
* **Adobe Campaign - Mappatura**
Mappa su un campo di personalizzazione Adobe Campaign.

L’esempio seguente mostra come viene visualizzato il componente Chiave riconciliazione nascosta (Campaign) .

![chlimage_1-126](assets/chlimage_1-126.png)

### Campo numerico (Campaign) {#numeric-field-campaign}

Utilizza il campo numerico per consentire ai destinatari di immettere numeri, ad esempio la loro età.

Oltre a [impostazioni comuni alla maggior parte dei componenti di Adobe Campaign](#settings-common-to-most-components), puoi configurare quanto segue:

* **Vincoli - Vincolo** a discesa

   È possibile selezionare - **Nessuno** o **Numerico** - per aggiungere il vincolo di un numero o nessun vincolo. Se si seleziona un numero, le risposte inserite dagli utenti nel campo devono essere numeriche.

* **Messaggio vincolo**

   Inoltre, è possibile aggiungere un messaggio di vincolo in modo che gli utenti sappiano come formattare correttamente le risposte.
* **Stile - Larghezza**
Per regolare la larghezza del campo, tocca o fai clic sul pulsante 
**+** e **-** icone o immissione di un numero.

L’esempio seguente mostra come viene visualizzato un componente Campo numerico (Campaign) con la larghezza configurata.

![chlimage_1-127](assets/chlimage_1-127.png)

### Campo opzione (Campaign) {#option-field-campaign}

Questo elenco a discesa consente di selezionare un’opzione; ad esempio, il genere o lo stato di un destinatario.

È possibile [configurare le impostazioni comuni alla maggior parte dei componenti di Adobe Campaign](#settings-common-to-most-components) nel componente Campo opzione (Campaign). Per compilare l’elenco a discesa, seleziona il campo appropriato nei campi di personalizzazione Adobe Campaign toccando o facendo clic sul simbolo Adobe Campaign e passando al campo .

![chlimage_1-128](assets/chlimage_1-128.png)

L’esempio seguente mostra come viene visualizzato un componente Campo opzione (Campaign) .

![chlimage_1-129](assets/chlimage_1-129.png)

### Lista di controllo delle iscrizioni (Campaign) {#subscriptions-checklist-campaign}

Utilizza la **Lista di controllo delle iscrizioni (Campaign)** per modificare le sottoscrizioni associate a un profilo Adobe Campaign.

Quando viene aggiunto a un modulo, questo componente visualizza tutte le sottoscrizioni disponibili come caselle di controllo e consente all’utente di selezionare le sottoscrizioni desiderate. Quando gli utenti inviano il modulo, questo componente si abbona o annulla l’iscrizione dell’utente ai servizi selezionati a seconda del tipo di azione del modulo (**Adobe Campaign: Iscriviti ai servizi** o **Adobe Campaign: Annulla sottoscrizione a servizi**).

>[!NOTE]
>
>Il componente non controlla a quali servizi l’utente è già iscritto o ha annullato l’abbonamento.

È possibile [configurare le impostazioni comuni alla maggior parte dei componenti di Adobe Campaign](#settings-common-to-most-components) nel componente Lista di controllo delle iscrizioni (Campaign). Non sono disponibili configurazioni di Adobe Campaign per questo componente.

L’esempio seguente mostra come viene visualizzato il componente Lista di controllo delle iscrizioni (Campaign) .

![chlimage_1-130](assets/chlimage_1-130.png)

### Campo testo (Campaign) {#text-field-campaign}

Il componente Campo di testo (Campaign) che consente di inserire dati di tipo stringa, ad esempio nome, cognome, indirizzo, indirizzo e-mail e così via.

Oltre a [impostazioni comuni alla maggior parte dei componenti di Adobe Campaign](#settings-common-to-most-components), puoi configurare quanto segue:

* **Vincoli - Vincolo** a discesa

   È possibile selezionare - **Nessuno, E-Mail,** o **Nome (senza umlaut)**- per aggiungere il vincolo di un indirizzo e-mail, un nome o nessun vincolo. Se selezioni e-mail, le risposte inserite dagli utenti nel campo devono essere un indirizzo e-mail. Se selezioni il nome, deve essere un nome (gli umlaut non sono consentiti).

* **Messaggio vincolo**

   Inoltre, è possibile aggiungere un messaggio di vincolo in modo che gli utenti sappiano come formattare correttamente le risposte.

* **Stile - Larghezza**

   Per regolare la larghezza del campo, tocca o fai clic sul pulsante **+** e **-** icone o immissione di un numero.

L’esempio seguente mostra come viene visualizzato un componente Campo di testo (Campaign).

![chlimage_1-131](assets/chlimage_1-131.png)
