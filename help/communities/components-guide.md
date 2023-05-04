---
title: Guida ai componenti della community
seo-title: Community Components Guide
description: Uno strumento di sviluppo interattivo per iniziare a usare il quadro dei componenti sociali (SCF)
seo-description: An interactive development tool to get started with the social component framework (SCF)
uuid: 120e56d1-b93c-4f92-bab4-6bb5e40e0ddf
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a777a3f1-b39f-4d90-b9b6-02d3e321a86f
exl-id: 8cdd7b94-b247-4598-bb0f-36c5ec1319ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 2%

---

# Guida ai componenti della community {#community-components-guide}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La guida ai componenti comunitari è uno strumento di sviluppo interattivo per [quadro della componente sociale (SCF)](scf.md). Fornisce un elenco dei componenti AEM Communities disponibili o delle funzioni più complesse create da più componenti.

Oltre alle informazioni di base per ciascun componente, la guida consente di sperimentare il funzionamento dei componenti/funzionalità SCF e le modalità di configurazione o personalizzazione.

Per informazioni sulle nozioni di base di sviluppo relative a ciascun componente, consulta [Funzionalità e componenti di base](essentials.md).

## Guida introduttiva {#getting-started}

La guida è destinata all’utilizzo sulle installazioni di sviluppo di istanze author (localhost:4502) e publish (localhost:4503).

Il sito Community Components è accessibile dalla pagina

* [https://&lt;server>:&lt;port>/content/community-components/en.html](http://localhost:4502/content/community-components/en.html)

Le interazioni con i componenti di Communities variano a seconda di:

* Server (autore o pubblicazione)
* Se il visitatore del sito ha effettuato o meno l&#39;accesso
* Se l&#39;utente ha effettuato l&#39;accesso, i privilegi assegnati al membro
* Se l’SRP predefinito è o meno, [JSRP](jsrp.md), è in uso

Per accedere alla modalità di modifica, seleziona `editor.html` o `cf#` come primo segmento di percorso dopo il nome del server:

* Interfaccia standard:

   [https://&lt;server>:&lt;port>/editor.html/content/community-components/en.html](http://localhost:4502/editor.html/content/community-components/en.html)

* Interfaccia classica:

   [https://&lt;server>:&lt;port>/cf#/content/community-components/en.html](http://localhost:4502/cf#/content/community-components/en.html)

>[!NOTE]
>
>In modalità Modifica, i collegamenti presenti in una pagina non sono attivi.
>
>Per passare alla pagina di un componente, seleziona innanzitutto Modalità Anteprima per attivare i collegamenti.
>
>Con la pagina del componente visualizzata nel browser, torna alla modalità Modifica per aprire la finestra di dialogo di modifica del componente.
>
>Per informazioni generali sull’authoring, visualizzare il [guida rapida all’authoring delle pagine](../../help/sites-authoring/qg-page-authoring.md).
>
>Se non hai familiarità con AEM, consulta la documentazione su [trattamento di base](../../help/sites-authoring/basic-handling.md).

### Home page {#home-page}

La guida fornisce un elenco dei componenti SCF disponibili per l’anteprima e la creazione di prototipi lungo il lato sinistro della pagina.

Guida ai componenti visualizzata su un’istanza dell’autore in modalità Modifica :

![chlimage_1-404](assets/chlimage_1-404.png)

## Pagine dei componenti {#component-pages}

Seleziona un componente dall’elenco lungo il lato sinistro della pagina.

![chlimage_1-405](assets/chlimage_1-405.png)

Il corpo principale della guida mostra:

1. Titolo: Nome del componente selezionato
1. [Librerie lato client](#client-side-libraries): Elenco di una o più categorie richieste
1. [Incluso](scf.md#add-or-include-a-communities-component): Se il componente può essere incluso in modo dinamico, è possibile attivare o disattivare lo stato in modalità di modifica dell’autore:

   * Se aggiunto, il testo visualizzato è: &quot;Questo componente è incluso tramite il suo nodo par.&quot;
   * Se incluso, il testo visualizzato è: &quot;Questo componente viene incluso dinamicamente.&quot;
   * Se non incluso, non viene visualizzato testo

1. Componente o funzione di esempio: un&#39;istanza attiva del componente o della funzione. Se un componente, può essere modificato con modifiche apportate ai modelli, CSS e dati forniti nella sezione scheda .

>[!NOTE]
>
>Dopo aver effettuato una selezione dal lato sinistro, il componente compare sotto, invece che accanto, l’elenco dei componenti quando la finestra del browser è troppo stretta.

### Interazioni autore {#author-interactions}

Quando si utilizza la guida su un’istanza di authoring, è possibile configurare un componente aprendo la relativa finestra di dialogo. Le informazioni per gli sviluppatori sono fornite nella sezione [Componenti e funzioni essenziali](essentials.md) della documentazione, mentre le impostazioni della finestra di dialogo sono descritte in [Componenti di Communities](author-communities.md) sezione per gli autori.

Per la guida ai componenti della community , alcune impostazioni della finestra di dialogo dei componenti sono sovrapposte alle [Incluso](scf.md#add-or-include-a-communities-component) stato di attivazione/disattivazione. Per passare dall’utilizzo della risorsa esistente o di una risorsa inclusa dinamicamente, in modalità di modifica seleziona sia il componente che il testo da includere, quindi fai doppio clic per aprire la finestra di dialogo di modifica:

![chlimage_1-406](assets/chlimage_1-406.png)

Sotto la **Modelli** scheda:

![chlimage_1-407](assets/chlimage_1-407.png)

* **Includi componente secondario con sling:include**

   Se questa opzione è deselezionata, la Guida ai componenti utilizza la risorsa esistente nell’archivio (un nodo jcr che è figlio di un nodo par).

   * il testo visualizzato è: &quot;Questo componente è incluso tramite il suo nodo par.&quot;

   Se questa opzione è selezionata, nella Guida ai componenti verrà utilizzato sling per includere in modo dinamico un componente del resourceType del nodo figlio (risorsa non esistente).

   * il testo visualizzato è: &quot;Questo componente viene incluso dinamicamente.&quot;

   Il valore predefinito è deselezionato.

### Pubblicare le interazioni {#publish-interactions}

Quando utilizzi la guida su un’istanza di pubblicazione, puoi utilizzare i componenti e le funzioni come visitatore del sito (non connesso) e come membri con vari privilegi al momento dell’accesso.

>[!NOTE]
>
>Tieni presente che se l’SRP viene lasciato impostato come impostazione predefinita su [JSRP](jsrp.md), quindi l&#39;UGC inserito nell&#39;istanza di pubblicazione sarà visibile solo al momento della pubblicazione e *non *sarà visibile dal [moderazione](moderate-ugc.md) nell’istanza di authoring.

## Librerie lato client {#client-side-libraries}

Le librerie lato client (clientlibs) elencate per ciascun componente sono quelle *obbligatorio* a cui fare riferimento quando il componente viene posizionato in una pagina. Le clientlibs forniscono un mezzo per gestire e ottimizzare il download di Javascript e CSS utilizzati per il rendering del componente nel browser.

Per ulteriori informazioni, visita [Componenti Clientlibs for Communities](clientlibs.md).

## Impersonazione {#impersonation}

Nell’istanza di authoring, in cui uno di loro ha spesso effettuato l’accesso come amministratore o sviluppatore, per poter utilizzare il componente connesso come un altro utente, utilizza la casella di testo a sinistra della **[!UICONTROL Impersona]** per digitare il nome utente o selezionare dall&#39;elenco a discesa, quindi fare clic sul pulsante. Fai clic su Ripristina per uscire e terminare la rappresentazione.

L’istanza di pubblicazione non deve rappresentare. Utilizza semplicemente il collegamento Accesso/Disconnessione per rappresentare vari utenti, ad esempio [utenti dimostrativi](tutorials.md#demo-users).

## Personalizzazione {#customization}

Quando abilitato, ogni componente SCF è disponibile per la prototipazione di possibili personalizzazioni modificando temporaneamente il modello, i CSS e i dati del componente.

### Abilitazione della personalizzazione {#enabling-customization}

>[!NOTE]
>
>**Questo strumento è di sola lettura**. Nessuna delle modifiche apportate a modelli, CSS o dati viene salvata nell’archivio.

Per sperimentare rapidamente le personalizzazioni, la `scg:showIde`deve essere aggiunta al nodo JCR del contenuto della pagina del componente e impostata su true.

Utilizzando il componente commenti come esempio, nell’istanza di authoring o di pubblicazione, con privilegi di amministratore, è stato effettuato l’accesso:

1. Sfoglia per [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   Ad esempio: [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

1. Seleziona il `jcr:content` nodo

   Ad esempio `/content/community-components/en/comments/jcr:content`

1. Aggiungi una proprietà

   * **Nome** `scg:showIde`
   * **Tipo** `String`
   * **Valore** `true`

1. Seleziona **[!UICONTROL Salva tutto]**
1. Ricarica la pagina Commenti nella guida

   [http://localhost:4503/content/community-components/en/comments.html](http://localhost:4503/content/community-components/en/comments.html)

1. Tieni presente che ora sono disponibili 3 schede per Modelli, CSS e Dati.

![chlimage_1-408](assets/chlimage_1-408.png) ![chlimage_1-409](assets/chlimage_1-409.png)

### Scheda Modelli {#templates-tab}

Seleziona la scheda dei modelli per visualizzare i modelli associati al componente.

L’Editor modelli consente di compilare e applicare modifiche locali all’istanza del componente di esempio nella parte superiore della pagina senza influire sul componente nell’archivio.

L’esecuzione della compilazione sulle modifiche locali evidenzierà eventuali errori posizionando un punto nel margine e contrassegnando il testo in rosso.

### Scheda CSS {#css-tab}

Seleziona la scheda CSS per visualizzare il CSS associato al componente.

Se un componente è un composito di più componenti, alcuni CSS possono essere elencati in uno degli altri componenti.

L’Editor CSS consente di modificare il CSS e applicarlo all’istanza del componente di esempio nella parte superiore della pagina.

È possibile selezionare una regola per evidenziare le parti del DOM che utilizzano tale regola facendo clic su accanto alla regola nell&#39;otturatore.

### Scheda Dati {#data-tab}

Seleziona la scheda Dati per visualizzare i dati dell’endpoint .social.json . Questi dati sono modificabili e vengono applicati all’istanza del componente di esempio.

Gli errori di sintassi possono essere contrassegnati nell&#39;otturatore ed evidenziati nell&#39;editor.
