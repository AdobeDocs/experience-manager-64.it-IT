---
title: Funzioni community
seo-title: Community Functions
description: Scopri come accedere alla console Funzioni della community
seo-description: Learn how to access the Community Functions console
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Admin
exl-id: 2007336d-d75c-4e01-af81-181751c04cfe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 3%

---

# Funzioni community {#community-functions}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il tipo di funzionalità previsto da un’esperienza community è noto. Le funzioni della community sono disponibili come funzioni della community. In sostanza, si tratta di una o più pagine precablate per implementare una funzione community che richiede più che semplicemente l’aggiunta di un componente a una pagina in modalità di authoring. Sono gli elementi costitutivi utilizzati per definire la struttura di un [modello di sito community](sites.md) da quali siti comunitari [creato](sites-console.md).

Una volta creato un sito community, il contenuto può essere aggiunto alle pagine risultanti utilizzando lo standard [Modalità di authoring AEM](../../help/sites-authoring/editing-content.md).

Una serie di funzioni della community sono immediatamente disponibili, come mostrato nella console delle funzioni della community. Nelle versioni future verranno fornite più funzioni della community e sarà possibile creare anche funzioni personalizzate.

>[!NOTE]
>
>Le console per la creazione di [siti della community](sites-console.md), [modelli di sito community](sites.md), [modelli di gruppo community](tools-groups.md) e [funzioni della community](functions.md) sono utilizzabili solo nell’ambiente di authoring.

## Console Funzioni community {#community-functions-console}

Nell’ambiente di authoring, è possibile accedere alla console funzioni della community

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Funzioni della community]**

![chlimage_1-379](assets/chlimage_1-379.png)

## Funzioni predefinite {#pre-built-functions}

Di seguito è riportata una breve descrizione delle funzioni fornite con AEM Communities. Ciascuna funzione è composta da una o più pagine AEM contenenti i componenti Community collegati tra loro in una funzione facilmente incorporata in un [modello di sito community](sites.md).

Un modello di sito community fornisce la struttura di un sito community con login, profili utente, notifiche, messaggi, menu del sito, ricerca, temi e funzioni di branding.

### Impostazioni titolo e URL {#title-and-url-settings}

**Titolo** e **URL** sono proprietà comuni a tutte le funzioni della community.

Quando una funzione community viene aggiunta a un modello di sito community o quando [modifica](sites-console.md#modifying-site-properties) la struttura di un sito community, la finestra di dialogo della funzione viene visualizzata in modo da configurare il Titolo e l’URL.

#### Dettagli funzione di configurazione {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL Titolo]**
(
*obbligatorio*) Testo visualizzato nel menu delle funzioni del sito

* **[!UICONTROL URL]**
(*obbligatorio*) Nome utilizzato per generare l’URI. Il nome deve essere conforme al [convenzioni di denominazione](../../help/sites-developing/naming-conventions.md) imposto da AEM e JCR.

Ad esempio, utilizzando il sito creato da [Introduzione](getting-started.md) esercitazione, se

* Titolo = Pagina Web
* URL = page

L’URL della pagina è quindi http://local_host:4503/content/sites/engage/en/page.html e il collegamento del menu per la pagina viene visualizzato come:

![chlimage_1-381](assets/chlimage_1-381.png)

### Funzione Flusso attività {#activity-stream-function}

La funzione di flusso di attività è una pagina con un [Componente Flussi di attività](activities.md) con tutte le visualizzazioni selezionate (tutte le attività, le attività utente e seguenti). Vedi anche [Nozioni di base sul flusso di attività](essentials-activities.md) per sviluppatori.

Quando viene aggiunto a un modello, si apre la seguente finestra di dialogo:

#### Dettagli funzione di configurazione {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Mostra la vista &quot;Attività personali&quot;]**
Se questa opzione è selezionata, la pagina Attività includerà una scheda che filtra le attività in base a quelle generate all’interno della community dal membro corrente. Il valore predefinito è selezionato.

* **[!UICONTROL Mostra la vista &quot;Tutte le attività&quot;]**
Se questa opzione è selezionata, la pagina Attività includerà una scheda che include tutte le attività generate all’interno della community a cui il membro corrente ha accesso. Il valore predefinito è selezionato.

* **[!UICONTROL Mostra la vista &quot;News Feed&quot;]**
Se questa opzione è selezionata, la pagina Attività includerà una scheda che filtra le attività in base a quelle che il membro corrente sta seguendo. Il valore predefinito è selezionato.

### Funzione Assegnazioni {#assignments-function}

La funzione di assegnazione è la funzione di base che definisce un [sito comunitario di abilitazione](overview.md#enablement-community). Consente l&#39;assegnazione di risorse di abilitazione ai membri della community. Vedi anche [Componenti di base per le assegnazioni](essentials-assignments.md) per sviluppatori.

Questa funzione è disponibile come funzione del [componente aggiuntivo per l’abilitazione](enablement.md). Il componente aggiuntivo per l’abilitazione richiede licenze aggiuntive per l’utilizzo in un ambiente di produzione.

Quando viene aggiunta a un modello, l’unica configurazione è per [Impostazioni titolo e URL](#title-and-url-settings).

### Funzione Blog {#blog-function}

La funzione blog è una pagina con un [Componente blog](blog-feature.md) configurati per l’assegnazione di tag, il caricamento di file, i seguenti elementi, i membri per la modifica automatica, il voto e la moderazione. Vedi anche [Blog Essentials](blog-developer-basics.md) per sviluppatori.

Quando viene aggiunto a un modello, si apre la seguente finestra di dialogo:

![chlimage_1-383](assets/chlimage_1-383.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Consenti membri con privilegi]**
Se selezionato, il blog consentirà solo ai membri privilegiati di creare articoli consentendo la selezione di un [gruppo di membri privilegiati](users.md#privileged-members-group). Se non è selezionato, tutti i membri della community possono creare. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**
Se questa opzione è selezionata, il blog includerà la possibilità per i membri di caricare i file. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti risposte thread]**
Se non è selezionato, il blog consentirà le risposte (commenti) a un articolo, ma le risposte ai commenti non sono consentite. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**
Se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è selezionato.

### Funzione Calendario {#calendar-function}

La funzione calendario è una pagina con un [Componente calendario](calendar.md) configurato per consentire l’assegnazione di tag. Vedi anche [Nozioni di base sul calendario](calendar-basics-for-developers.md) per sviluppatori.

Quando viene aggiunto a un modello, si apre la seguente finestra di dialogo:

![chlimage_1-384](assets/chlimage_1-384.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Consenti ritaglio]**
Se questa opzione è selezionata, il forum consente di aggiungere le risposte all’argomento all’inizio dell’elenco dei commenti. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti membri con privilegi]**
Se selezionato, il blog consentirà solo ai membri privilegiati di creare articoli consentendo la selezione di un [gruppo di membri privilegiati](users.md#privileged-members-group). Se non è selezionato, tutti i membri della community possono creare. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**
Se questa opzione è selezionata, il blog includerà la possibilità per i membri di caricare i file. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti risposte thread]**
Se non è selezionato, il blog consentirà le risposte (commenti) a un articolo, ma le risposte ai commenti non sono consentite. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**
Se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è selezionato.

### Funzione Catalogo {#catalog-function}

La funzione di catalogo permette di [comunità di abilitazione](overview.md#enablement-community) membri per sfogliare le risorse di abilitazione che non sono assegnate a loro. Vedi [Risorse di abilitazione assegnazione tag](tag-resources.md) e [Nozioni di base sul catalogo](catalog-developer-essentials.md) per sviluppatori.

Tutte le risorse di abilitazione e i percorsi di apprendimento per il sito community verranno visualizzati in tutti i cataloghi, se di proprietà, ` [Show in Catalog](resources.md)`, è impostato su true. Per includere esplicitamente le risorse e i percorsi di apprendimento, è necessario applicare un [pre-filtro](catalog-developer-essentials.md#pre-filters) al catalogo.

Quando viene aggiunta a un modello, la configurazione consente di specificare i namespace dei tag utilizzati per configurare il filtro tag presentato ai visitatori del sito:

![catalogfunc](assets/catalogfunc.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Seleziona tutti i namespace]**

   * Gli spazi dei nomi dei tag selezionati definiscono quali tag possono essere selezionati dai visitatori per filtrare l’elenco delle risorse di abilitazione elencate nel catalogo.
   * Se questa opzione è selezionata, sono disponibili tutti i namespace consentiti per il sito community.
   * Se deselezionata, è possibile selezionare uno o più namespace consentiti per il sito community.
   * Il valore predefinito è selezionato.

### Funzione di contenuto {#featured-content-function}

La funzione di contenuto in primo piano è una pagina con un [Componente Contenuto](featured.md) configurato per consentire l’aggiunta e l’eliminazione di commenti.

La possibilità di utilizzare il contenuto può essere consentita o disabilitata per ciascun componente (consulta [Funzione blog](#blog-function), [Funzione Calendario](#calendar-function), [Funzione Forum](#forum-function), [Funzione di ideazione](#ideation-function)e [Funzione QnA](#qna-function)).

Quando viene aggiunta a un modello, l’unica configurazione è per [Impostazioni titolo e URL](#title-and-url-settings).

### Funzione Libreria file {#file-library-function}

La funzione libreria file è una pagina con un [Componente Libreria file](file-library.md) configurato per consentire l’aggiunta e l’eliminazione di commenti.

Quando viene aggiunta a un modello, l’unica configurazione è per [Impostazioni titolo e URL](#title-and-url-settings).

### Funzione Forum {#forum-function}

La funzione forum è una pagina con un [Componente Forum](forum.md) configurati per l’assegnazione di tag, il caricamento di file, i seguenti elementi, i membri per la modifica automatica, il voto e la moderazione.

Quando viene aggiunto a un modello, si apre la seguente finestra di dialogo:

#### Dettagli funzione di configurazione {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Consenti ritaglio]**
Se questa opzione è selezionata, il forum consente di aggiungere le risposte all’argomento all’inizio dell’elenco dei commenti. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti membri con privilegi]**
Se questa opzione è selezionata, il forum consente ai membri privilegiati di pubblicare argomenti solo selezionando un [gruppo di membri privilegiati](users.md#privileged-members-group). Se non è selezionato, tutti i membri della community possono effettuare la pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**
Se questa opzione è selezionata, il forum includerà la possibilità per i membri di caricare i file. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti risposte thread]**
Se non è selezionato, il forum consentirà la creazione di commenti su un argomento, ma non sarà possibile rispondere a tali commenti. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**
Se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è selezionato.

### Funzione Groups {#groups-function}

>[!CAUTION]
>
>La funzione gruppi deve *not* essere *primo né unico* funziona nella struttura di un sito o in un modello di sito community.
>
>Qualsiasi altra funzione, ad esempio [funzione pagina](#page-function), deve essere incluso ed elencato per primo.

La funzione gruppi consente ai membri della community di creare sottocommunity all’interno del sito della community nell’ambiente di pubblicazione.

A seconda [impostazioni](sites-console.md#groupmanagement) quando la funzione Groups è inclusa in un [modello di sito community](sites.md), i gruppi possono essere pubblici o privati e uno o più modelli di gruppo community possono essere configurati per fornire una scelta di modelli quando il gruppo community viene effettivamente creato (ad esempio dall’ambiente di pubblicazione). A [modello di gruppo community](tools-groups.md) specifica quali funzioni di Communities vengono create per le pagine del gruppo, ad esempio forum e calendari.

Quando viene creato un gruppo di community, viene creato in modo dinamico un gruppo di membri per il nuovo gruppo, a cui è possibile assegnare o unire i membri. Per ulteriori informazioni, consulta [Gestione di utenti e gruppi di utenti](users.md).

A livello di Comunità [feature pack 1](deploy-communities.md#latestfeaturepack), i gruppi community vengono creati nell’ambiente di authoring utilizzando [Console Gruppi di Communities Sites](groups.md)e può essere creato nell’ambiente di pubblicazione quando è abilitato.

Quando viene aggiunto a un modello, si apre la seguente finestra di dialogo:

![chlimage_1-386](assets/chlimage_1-386.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Seleziona modelli di gruppo]**
Un menu a discesa che consente di selezionare uno o più modelli di gruppo abilitati da cui può scegliere il futuro creatore di un nuovo gruppo community (nell’ambiente di pubblicazione).

* **[!UICONTROL Consenti membri con privilegi]**
Se questa opzione è selezionata, il forum consente ai membri privilegiati di pubblicare argomenti solo selezionando un [gruppo di sicurezza membri privilegiati](users.md#privileged-members-group). Se non è selezionato, tutti i membri della community possono effettuare la pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti creazione pubblicazione]**
Se questa opzione è selezionata, i membri della community autorizzati possono creare un gruppo nell’ambiente di pubblicazione. Se questa opzione è deselezionata, i nuovi gruppi (sottocommunity) possono essere creati solo nell’ambiente di authoring dalla console Gruppi di siti di Communities.

   Il valore predefinito è `checked`.

### Funzione ideazione {#ideation-function}

La funzione ideazione è una pagina con una [Componente ideazione](ideation-feature.md).

Quando viene aggiunta a un modello, viene visualizzata la finestra di dialogo seguente, che specifica il Titolo e i nomi URL predefiniti, nonché le impostazioni di visualizzazione predefinite per il modello:

![chlimage_1-387](assets/chlimage_1-387.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Consenti membri con privilegi]**
Se questa opzione è selezionata, il forum consente ai membri privilegiati di pubblicare argomenti solo selezionando un [gruppo di sicurezza membri privilegiati](users.md#privileged-members-group). Se non è selezionato, tutti i membri della community possono effettuare la pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**
Se questa opzione è selezionata, l’idea includerà la possibilità per i membri di caricare i file. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti risposte thread]**
Se non è selezionata, l’idea consentirà di rispondere (commenti) a un argomento, ma non di rispondere ai commenti. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**
Se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è selezionato.

### Funzione Classifica {#leaderboard-function}

La funzione della classifica è una pagina con una [Componente della classifica](enabling-leaderboard.md).

**NOTA**: Il componente Leaderboard dovrà essere configurato ulteriormente *dopo* un sito community viene creato da un modello community che include la funzione Leaderboard. Il componente della classifica [regole](enabling-leaderboard.md#rules-tab) devono essere specificati, a seconda della configurazione di [punteggio e badge](implementing-scoring.md) per il sito della community.

Quando viene aggiunta a un modello, viene visualizzata la finestra di dialogo seguente, che specifica il Titolo e i nomi URL predefiniti, nonché le impostazioni di visualizzazione predefinite per il modello:

![chlimage_1-388](assets/chlimage_1-388.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Badge di visualizzazione]**
Se questa opzione è selezionata, nella classifica è inclusa una colonna per le icone del badge.

   Il valore predefinito è deselezionato.

* **[!UICONTROL Nome badge visualizzazione]**
Se questa opzione è selezionata, nella classifica è inclusa una colonna relativa al nome del badge.

   Il valore predefinito è deselezionato.

* **[!UICONTROL Avatar display]**
Se questa opzione è selezionata, l&#39;immagine avatar del membro viene inclusa nella classifica, accanto al collegamento del nome al profilo membro.

   Il valore predefinito è deselezionato.

### Funzione Pagina {#page-function}

La funzione page aggiunge al sito community una pagina vuota che è collegata alle funzioni del sito community: accesso, menu, notifiche, messaggistica, temi e branding. Il contenuto può essere aggiunto alla pagina utilizzando [modalità di authoring standard AEM](../../help/sites-authoring/editing-content.md).

Quando viene aggiunta a un modello, l’unica configurazione è per [Impostazioni titolo e URL](#title-and-url-settings).

### Funzione D/R {#qna-function}

La funzione QnA è una pagina con un [Componente QnA](working-with-qna.md) configurati per l’assegnazione di tag, il caricamento di file, i seguenti elementi, i membri per la modifica automatica, il voto e la moderazione.

Quando viene aggiunta a un modello, la configurazione consente restrizioni ai membri con privilegi:

![chlimage_1-389](assets/chlimage_1-389.png)

* Vedi [Impostazioni titolo e URL](#title-and-url-settings)
* **[!UICONTROL Consenti ritaglio]**
Se questa opzione è selezionata, il forum consente di aggiungere le risposte all’argomento all’inizio dell’elenco dei commenti. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti membri con privilegi]**
Se questa opzione è selezionata, il forum QnA consente solo ai membri privilegiati di inviare domande consentendo la selezione di un [gruppo di membri privilegiati](users.md#privileged-members-group). Se non è selezionato, tutti i membri della community possono effettuare la pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**
Se questa opzione è selezionata, il forum QnA includerà la possibilità per i membri di caricare i file. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti risposte thread]**
Se non è selezionato, il forum QnA consentirà la presenza di commenti (risposte) a una domanda pubblicata, ma le risposte alle risposte non sono consentite. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**
Se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è selezionato.

## Crea funzione community {#create-community-function}

La possibilità di creare una funzione community viene raggiunta selezionando la `Create Community Function` nella parte superiore della console Funzioni della community. È possibile creare più funzioni basate sullo stesso Blueprint AEM e quindi personalizzate in modo univoco aprendo in modalità di modifica dell’autore.

![chlimage_1-390](assets/chlimage_1-390.png)

### Nome funzione community {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

Nel pannello Nome funzione community sono configurati un nome, una descrizione e se la funzione è abilitata o disabilitata:

* **[!UICONTROL Nome funzione community]**
Nome della funzione utilizzata per la visualizzazione e l&#39;archiviazione

* **[!UICONTROL Descrizione della funzione community]**
Descrizione della funzione per la visualizzazione

* **[!UICONTROL Disabilitato/Abilitato]**
Un interruttore che controlla se la funzione è referente

### Blueprint AEM {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

Sulla `AEM Blueprint` è possibile selezionare il modello che è l&#39;attuazione sottostante della funzione comunitaria.

La funzione community è un mini sito composto da una o più pagine, preconnesso per l’inclusione in un sito community che include login, profili utente, notifiche, messaggistica, menu del sito, ricerca, temi e funzioni di branding. Una volta creata la funzione, è possibile [aprire la funzione](#open-community-function) in modalità di modifica dell’autore e personalizzare le impostazioni della pagina e/o del componente.

Poiché la funzione comunitaria è attuata come [Live Copy](../../help/sites-administering/msm.md#live-copies) di [blueprint](../../help/sites-administering/msm-livecopy.md#creatingablueprint), è possibile eseguire il rollout delle modifiche apportate a una funzione che interessa tutte le pagine del sito community create da [modello di sito community](sites.md) o [modello di gruppo community](tools-groups.md) che includeva la funzione . È inoltre possibile dissociare una pagina dalla relativa blueprint principale per apportare modifiche a livello di pagina.

Vedi anche [Multi Site Manager](../../help/sites-administering/msm.md).

### Miniatura  {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

Nel pannello Miniatura, è possibile caricare un’immagine da visualizzare nel [Console Funzioni community](#community-functions-console).

## Apri funzione community {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Seleziona la `Open Community Function` per accedere alla modalità di modifica dell’autore per creare il contenuto della pagina e modificare la configurazione dei componenti della funzione.

### Configurazione dei componenti {#configuring-components}

Una funzione community viene implementata come Live Copy di una blueprint AEM, i cui dettagli sono documentati in [Multi Site Manager](../../help/sites-administering/msm.md).

È possibile non solo creare il contenuto della pagina, ma anche configurare i componenti.

Se si configura un componente in una pagina di un sito community creato, può essere necessario annullare [eredità](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) per configurare il componente. L’ereditarietà deve essere ristabilita al termine della configurazione.

Per informazioni sulla configurazione, visita [Componenti di Communities](author-communities.md) per gli autori.

## Funzione modifica per community {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Seleziona la `Edit Community Function` per modificare le proprietà della funzione utilizzando gli stessi pannelli di [creazione di una funzione community](#create-community-function), inclusa l’abilitazione o la disattivazione della funzione.
