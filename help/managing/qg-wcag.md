---
title: Guida rapida alle linee guida WCAG 2.0
seo-title: Quick Guide to WCAG 2.0
description: Panoramica rapida delle linee guida per l’accessibilità WCAG 2.0.
seo-description: Read a quick overview of the WCAG 2.0 accessibility guidelines.
uuid: a5cf463e-89e9-4cc0-9c91-69a1fd3d8ea2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing-accessibility
content-type: reference
discoiquuid: 3cac0e34-7514-48ce-a93b-592bbdbcd252
exl-id: 80edcd53-bc3c-4f61-8dfb-c592e7e51f60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1708'
ht-degree: 82%

---

# Guida rapida alle linee guida WCAG 2.0{#quick-guide-to-wcag}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM è stato sviluppato per massimizzare la conformità alle linee guida per l’accessibilità dei contenuti web:

La [Linee guida per l’accessibilità dei contenuti web versione 2.0 (WCAG2)](https://www.w3.org/TR/WCAG/) sono una serie di linee guida riconosciute a livello internazionale elaborate [World Wide Web Consortium (W3C)](https://www.w3.org/) sotto il loro [Iniziativa per l’accessibilità web (WAI)](https://www.w3.org/WAI/).

Le linee guida WCAG 2.0 sono costituite da un insieme di criteri di successo e linee guida che non dipendono dalla tecnologia in uso e hanno l’obiettivo di rendere i contenuti web accessibili e utilizzabili da persone con disabilità. Includono suggerimenti e indicazioni per autori, designer e sviluppatori di contenuti web al fine di garantire che le risorse prodotte siano progettate in modo da essere accessibili per un pubblico che sia il più ampio possibile, indipendentemente da eventuali disabilità o limitazioni, quali disabilità visive o uditive, difficoltà di apprendimento o limiti correlati all’età.

Ad esempio, la descrizione di un’immagine (o di qualsiasi altro contenuto non testuale) tramite l’attributo `alt` nel linguaggio HTML offre notevoli vantaggi alle persone non vedenti o ipovedenti. La descrizione testuale contenuta nell’attributo `alt` può essere convertita in un output vocale o trasmessa a display Braille elettronici aggiornabili.

Inoltre, la conformità alle linee guida WCAG 2.0 può offrire vantaggi anche ad altri beneficiari, tra cui persone con *disabilità situazionale*: persone che, a causa di fattori quali tecnologia di navigazione, velocità della connessione di rete o ambiente di navigazione, possono incontrare barriere simili alle persone con disabilità.

Utilizzando Adobe Experience Manager, gli autori di contenuti e/o i proprietari di siti web possono creare contenuti web che soddisfano i criteri di successo WCAG 2.0 pertinenti di livello A e AA.

È quindi importante comprendere gli obiettivi e la struttura delle linee guida WCAG 2.0, per capire il ruolo dell’accessibilità web e come le linee guida consentano di creare contenuti web accessibili.

WCAG 2.0 intende fornire linee guida con le caratteristiche indicate di seguito.

* Sono **agnostico della tecnologia:**

   In altre parole, linee guida che possono essere applicate a diversi formati di contenuti web, non solo ad HTML. Le linee guida WCAG 2.0 sono quindi applicabili anche a contenuti generati o forniti tramite PDF, Flash, JavaScript o altre tecnologie web attuali e future. L’obiettivo è quello di ovviare a una debolezza riconosciuta delle linee guida WCAG 1.0, in quanto si concentrava su HTML a scapito di altri formati di contenuti web.

* Sono **testabile:**

   Ogni linea guida è redatta in modo da poter essere testata in modo oggettivo per garantire che un gruppo di esperti in materia di accessibilità concordi generalmente sul fatto che la linea guida sia stata rispettata. Una delle problematiche correlate all’accessibilità, infatti, consiste nel fatto che alcune linee guida possono essere tecnicamente testabili, mentre altre richiedono una valutazione umana per verificare se siano state rispettate o meno. WCAG 2.0 è stato scritto allo scopo di ridurre la soggettività presente in alcune delle linee guida e dei punti di controllo WCAG 1.0.

* **Implementazione contestuale e con priorità**:

   Come per le linee guida WCAG 1.0, anche le linee guida WCAG 2.0 hanno priorità, in relazione al probabile impatto del mancato rispetto di una linea guida per un particolare gruppo di utenti con disabilità. Questo consente agli autori di prendere decisioni informate sulle linee guida più importanti per una situazione specifica. Viene inoltre introdotto il concetto di *supporto dell’accessibilità*. Questo consente agli autori di decidere come utilizzare al meglio le tecnologie web che potrebbero non prevedere il supporto completo per l’accessibilità oppure che, per beneficiare delle funzioni di accessibilità, potrebbero richiedere l’accesso a particolari browser e/o tecnologie per l’accessibilità.

Tali obiettivi hanno influenzato in modo significativo la struttura delle linee guida WCAG 2.0.

>[!NOTE]
>
>Non è possibile creare un sito web che tenga in considerazione ogni possibile disabilità o tipo di persona. Le linee guida WCAG 2.0 intendono aiutare gli autori di siti web a creare, per quanto possibile, siti ragionevolmente accessibili per determinate condizioni.

>[!NOTE]
>
>Se conosci le linee guida WCAG 1.0, noterai alcune modifiche alle linee guida WCAG 2.0 relative a scopo, organizzazione e scopo.

## Struttura {#structure}

Le linee guida WCAG 2.0 sono strutturate in modo da introdurre i concetti di creazione di contenuti web accessibili in ordine progressivo, dal più semplice al più dettagliato. Questa caratteristica può dare l’impressione che le linee guida WCAG 2.0 siano un insieme molto complesso di documenti interconnessi. In realtà l’obiettivo è quello di fornire le informazioni in modo progressivamente più dettagliato, a cui gli autori possono accedere come e quando ne hanno bisogno, anziché fornire tutte le istruzioni in un unico documento molto esteso.

Le linee guida WCAG 2.0 si basano su quattro principi chiave per la progettazione accessibile. Secondo questi principi, il contenuto deve essere:

1. **Percepibile**: un utente è in grado di percepire il contenuto web in questione?
1. **Utilizzabile**: un utente ha la possibilità di navigare, inserire dati o interagire in altro modo con il contenuto web?
1. **Comprensibile**: un utente è in grado di elaborare e comprendere il contenuto web presentato?
1. **Robusto**: il contenuto web è disponibile nel modo previsto in un’ampia gamma di ambienti di navigazione, inclusi quelli legacy ed emergenti?

Tali principi sono talvolta indicati dall&#39;acronimo POUR.

* Ogni **principio** è costituito da una o più **linee guida**.

   * Le linee guida sono formulate come istruzioni, che possono essere positive (cose da fare) o negative (cose da non fare).
   * Le linee guida sono numerate da 1.1 a 4.1 e la prima cifra corrisponde al principio padre.

* Ogni linea guida è costituita da uno o più **criteri di successo**.

   * I criteri di successo sono formulati come istruzioni, che possono essere `True` o `False` per una determinata pagina web.
   * I criteri di successo possono includere una o più opzioni oppure eccezioni, ovvero situazioni in cui non è necessario soddisfare i criteri di successo.
   * I criteri di successo sono numerati in base alla linea guida e al principio padre, da 1.1.1 a 4.1.1. Hanno anche un nome breve che riassume l’intento del criterio, per un riferimento più semplice. Ad esempio, il criterio di successo 1.1.1 prevede un’alternativa non testuale.
   * I criteri di successo includono un elenco delle **tecniche** correlate (descritte più in dettaglio di seguito).

## Risorse di supporto {#supporting-resources}

Oltre alle componenti WCAG 2.0 di base, ovvero principi, linee guida e criteri di successo, è disponibile una serie di documenti di supporto. Alcuni forniscono consigli specifici su come soddisfare gli aspetti delle linee guida; altri sono riferimenti più generali che aiutano gli autori, i designer e gli sviluppatori a comprendere e utilizzare le linee guida WCAG 2.0 nel modo più efficace possibile, a prescindere dal loro livello di competenza.

Mentre le linee guida WCAG 2.0 rappresentano un documento stabile che non verrà modificato, la maggior parte delle risorse di supporto è costituita da documenti dinamici che verranno modificati e incrementati nel tempo, man mano che emergono nuove tecnologie e si scoprono nuovi esempi di come l’obiettivo di accessibilità dei contenuti web possa essere conseguito.

### Risorse WCAG 2.0 {#wcag-resources}

* [Panoramica di tutti i documenti correlati alle linee guida WCAG 2.0](https://www.w3.org/WAI/intro/wcag.php);
* [Spiegazione del rapporto tra i diversi componenti](https://www.w3.org/WAI/intro/wcag20);
* [Domande frequenti sulle linee guida WCAG 2.0](https://www.w3.org/WAI/WCAG20/wcag2faq.html);

### Tecniche per WCAG 2.0 {#techniques-for-wcag}

Le tecniche per le linee guida WCAG 2.0 sono disponibili nella pagina [Tecniche per WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/) pagina.

Nella gerarchia WCAG 2.0, le **tecniche** rappresentano il livello inferiore ai criteri di successo e sono classificate da WAI come informative anziché normative. In altre parole, non è necessario seguire una tecnica specifica affinché una risorsa sia conforme a WCAG 2.0.

Poiché le tecniche sono molto più specifiche dei criteri di successo, in genere fanno riferimento a una particolare tecnologia, a un tipo di contenuto specifico (ad esempio HTML o video) oppure a una situazione particolare, come un’applicazione di e-commerce o di e-learning. È possibile considerarle esempi comprovati di come possono essere soddisfatti specifici criteri di successo e linee guida, e rappresentano quindi strumenti utili per autori e sviluppatori che lavorano in contesti specifici.

È possibile accedere alle tecniche nei seguenti modi:

* In base alla raccolta - Le tecniche possono essere generali o correlate a una tecnologia oppure a un formato specifico, ad esempio HTML, CSS o script sul lato client.
* Da criteri di successo correlati - Le tecniche possono essere applicate a più criteri di successo.

Ogni tecnica ha un numero univoco, relativo alla raccolta corrispondente. Ad esempio, una delle tecniche ARIA è *ARIA2: identificazione dei campi obbligatori con la proprietà “required”*.

Le tecniche possono essere sufficienti, consigliate o di errore.

* Una *tecnica sufficiente*, se seguita, sarà sufficiente per soddisfare un particolare criterio di successo.
* Una *tecnica consigliata*, se seguita, avrà un impatto positivo sull’accessibilità, ma potrebbe non essere sufficiente da sola per garantire il rispetto di un particolare criterio di successo.
* Un *tecnica di errore* descrive un esempio specifico in cui i criteri di successo non sono stati soddisfatti.

I dettagli delle tecniche includono descrizione, applicabilità, esempi, risorse per ulteriori informazioni e dettagli su come gli autori possono eseguire un test per verificare se l’applicazione della tecnica è efficace.

L’elenco delle tecniche non è statico: WAI lo aggiorna costantemente con nuovi esempi, che riflettono gli sviluppi della tecnologia web, degli approcci di progettazione e dei risultati della ricerca. Si consiglia quindi di controllare regolarmente l’elenco delle tecniche per verificare eventuali nuove aggiunte.

### Informazioni sulle linee guida WCAG 2.0 {#understanding-wcag}

Si tratta di una serie di documenti che forniscono consigli ai lettori per approfondire lo scopo di linee guida e criteri di successo specifici. È possibile [scaricare un’introduzione con collegamenti a informazioni più dettagliate](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/Overview.html).

Per ogni linea guida e criterio di successo è disponibile anche un breve documento esplicativo con informazioni su:

* Intento della linea guida
* Criteri di successo specifici
* Tecniche consigliate, che contribuiscono a soddisfare i requisiti della linea guida, ma che non rientrano in alcun criterio di successo specifico.

Il documento esplicativo per ogni criterio di successo fornisce informazioni su:

* Intento del criterio di successo
* Esempi generali di come può essere soddisfatto il criterio di successo
* Risorse correlate (non W3C) su come soddisfare il criterio di successo
* Tecniche ed errori - Esempi specifici e dettagliati su come soddisfare il criterio di successo (descritti più dettagliatamente di seguito)
* Termini chiave - Glossario dei termini importanti per la comprensione del criterio di successo

Nella sezione per la [comprensione del criterio di successo 1.1.1 (“Contenuti non testuali”)](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/text-equiv-all.html) è disponibile un esempio.

### Come soddisfare le linee guida WCAG 2.0 {#how-to-meet-wcag}

Nella pagina dedicata a [come soddisfare le linee guida WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref/) sono disponibili indicazioni sulla conformità alle linee guida. Viene fornita una presentazione alternativa delle linee guida WCAG, che consente di ottenere i contenuti delle linee guida pertinenti in base agli interessi o agli obiettivi del lettore. È possibile filtrare le tecniche relative ai criteri di successo da visualizzare specificando particolari tecnologie di contenuti web, ad esempio Cascading Style Sheets o script oppure specificando un particolare livello di priorità.

Se non viene applicato alcun filtro, vengono presentati tutti i criteri di successo raggruppati per linea guida. Per ciascun criterio di successo, vengono fornite le seguenti informazioni:

* Testo del criterio di successo
* Collegamento al corrispondente documento per la comprensione
* Elenco delle tecniche sufficienti correlate, con collegamento ai dettagli di ciascuna tecnica
* Elenco delle tecniche consigliate correlate, con collegamento ai dettagli di ciascuna tecnica (se disponibile)
* Elenco degli errori correlati, con collegamento ai dettagli di ogni errore
