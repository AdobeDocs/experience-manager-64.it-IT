---
title: Punteggio e distintivi avanzati
seo-title: Punteggio e distintivi avanzati
description: Impostazione del punteggio avanzato
seo-description: Impostazione del punteggio avanzato
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
translation-type: tm+mt
source-git-commit: ddf92a270835259998aa28f5960abcf55f56d1fc

---


# Punteggio e distintivi avanzati {#advanced-scoring-and-badges}

## Panoramica {#overview}

Il punteggio avanzato consente di assegnare i distintivi per identificare i membri come esperti. Il punteggio avanzato assegna punti in base alla quantità *e alla* qualità del contenuto creato da un membro, mentre il punteggio di base assegna punti semplicemente in base alla quantità di contenuto creata.

Questa differenza è dovuta al motore di valutazione utilizzato per calcolare i punteggi. Il motore di punteggio di base applica la matematica semplice. Il motore di valutazione avanzato è un algoritmo adattivo che premia i membri attivi che contribuiscono al contenuto con valore e rilevanza, dedotto attraverso l&#39;elaborazione in linguaggio naturale (NLP) di un argomento.

Oltre alla rilevanza del contenuto, gli algoritmi di punteggio tengono conto delle attività dei membri, come il voto e la percentuale di risposte. Mentre il punteggio di base li include in termini quantitativi, il punteggio avanzato li utilizza algoritmicamente.

Pertanto, il motore di valutazione avanzato richiede dati sufficienti per rendere significativa l&#39;analisi. La soglia di successo per diventare un esperto viene costantemente rivalutata man mano che l&#39;algoritmo si adatta continuamente al volume e alla qualità dei contenuti creati. C&#39;è anche un concetto di *decadimento* dei posti più vecchi di un membro. Se un membro esperto smette di partecipare all&#39;argomento per il quale ha ottenuto lo status di esperto, ad un certo punto predeterminato (vedere configurazione [del motore di](#configurable-scoring-engine)punteggio) potrebbe perdere il suo status di esperto.

L’impostazione del punteggio avanzato è praticamente uguale al punteggio di base:

* Regole di punteggio e contrassegno di base e avanzate vengono [applicate al contenuto](implementing-scoring.md#apply-rules-to-content) allo stesso modo
   * Regole di punteggio e contrassegno di base e avanzate possono essere applicate allo stesso contenuto
* [Abilitare i simboli per i componenti](implementing-scoring.md#enable-badges-for-component) è generico

Le differenze nella configurazione delle regole di punteggio e contrassegno sono:

* Motore di valutazione avanzato configurabile
* Regole di punteggio avanzate:
   * `scoringType` impostato su **[!UICONTROL avanzato]**
   * Richiede termini di arresto

* Regole di contrassegno avanzate:
   * `badgingType` impostato su **[!UICONTROL avanzato]**
   * `badgingLevels` imposta il numero di livelli di esperti da assegnare
   * Richiede un `badgingPaths` array di simboli al posto dei punti di mappatura dell&#39;array di soglie ai simboli

>[!NOTE]
>
>Per utilizzare funzionalità avanzate di valutazione e contrassegno, installate il pacchetto [Expert Identification (Identificazione Esperti)](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg).

## Motore di valutazione configurabile {#configurable-scoring-engine}

Il motore di punteggio avanzato fornisce una configurazione OSGi con parametri che influiscono sull’algoritmo di punteggio avanzato.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL Pesi]** punteggio Per un argomento, specificate il verbo al quale assegnare la priorità più alta per il calcolo del punteggio. È possibile inserire uno o più argomenti, ma solo **un verbo per argomento**. Consulta [Argomenti e verbi](implementing-scoring.md#topics-and-verbs).

   Inserito come `topic,verb` con la virgola con carattere di escape. Ad esempio:

   `/social/forum/hbs/social/forum\,ADD`

   
Il valore predefinito è impostato sul verbo ADD per i componenti QnA e forum.


* **[!UICONTROL Intervallo di punteggio]**

   L’intervallo per i punteggi avanzati è definito da questo valore (punteggio massimo possibile) e da 0 (punteggio più basso possibile).

   Il valore predefinito è 100 e l’intervallo di punteggio è compreso tra 0 e 100.


* **[!UICONTROL Intervallo di tempo decadimento entità]**

   Questo parametro rappresenta il numero di ore dopo le quali tutti i punteggi dell&#39;entità sono disattivati. Ciò non è più necessario per non includere contenuti obsoleti nelle valutazioni di un sito community.

   Il valore predefinito è 216000 ore (~24 anni).


* **[!UICONTROL Tasso di crescita del punteggio]**

   Specifica il punteggio. tra 0 e il punteggio, oltre il quale la crescita rallenta per limitare il numero di esperti.

   Il valore predefinito è 50.

## Regole di punteggio avanzate {#advanced-scoring-rules}

Nel punteggio di base, è nota la quantità necessaria per ottenere un contrassegno.

Nel punteggio avanzato, la quantità necessaria viene costantemente regolata in base alla quantità di dati di qualità all&#39;interno del sistema. Il punteggio viene calcolato in modo continuo in modo simile a una curva a campana.

Se un membro ha ottenuto un badge esperto su un argomento che non è più attivo, c&#39;è la possibilità che perderà il loro distintivo a causa di decadimento nel tempo.

### ScoringType {#scoringtype}

Una regola di punteggio è un insieme di regole secondarie di punteggio, ciascuna delle quali dichiara il `scoringType`.

Per richiamare il motore di punteggio avanzato, `scoringType`impostare `advanced`.

Consulta [Regole](implementing-scoring.md#scoring-sub-rules)secondarie punteggio.

![chlimage_1-261](assets/chlimage_1-261.png)

### Stopwords {#stopwords}

Il pacchetto di punteggio avanzato installa una cartella di configurazione che contiene un file di parole di arresto:

* `/etc/community/scoring/configuration/stopwords`

L&#39;algoritmo avanzato di valutazione utilizza l&#39;elenco di parole contenute nel file delle parole chiave per identificare le parole inglesi comuni che vengono ignorate durante l&#39;elaborazione del contenuto.

Non è previsto che il file venga modificato.

Se manca il file delle parole di arresto, il motore di punteggio avanzato genererà un errore.

## Regole di Badking avanzate {#advanced-badging-rules}

Le proprietà avanzate della regola di contrassegno sono diverse dalle proprietà [di base della regola](implementing-scoring.md#badging-rules)di contrassegno.

Invece di associare i punti a un’immagine badge, è necessario identificare solo il numero di esperti consentiti e l’immagine del contrassegno da assegnare.

![chlimage_1-262](assets/chlimage_1-262.png)

| **Proprietà** | **Tipo** | **Descrizione valore** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | Stringa[] | (Obbligatorio) Una stringa di più valori di immagini contrassegno fino al numero di badgingLevels. I percorsi immagine del contrassegno devono essere ordinati in modo che il primo venga assegnato all’esperto più alto. Se sono presenti meno simboli di quelli indicati da badgingLevels, l&#39;ultimo contrassegno nell&#39;array riempie il resto dell&#39;array. Voce di esempio:/etc/community/badging/images/Expert-badge/jcr:content/expert.png |
| badgingLevels | Lungo | (Facoltativo) Specifica i livelli di esperienza da assegnare. Ad esempio, se un esperto e un esperto (due simboli) devono essere presenti, il valore deve essere impostato su 2. Il valore badgingLevel deve corrispondere al numero di immagini del contrassegno relative agli esperti elencate per la proprietà badgingPath. Il valore predefinito è 1. |
| badgingType | Stringa | (Obbligatorio) Identifica il motore di valutazione come &quot;base&quot; o &quot;avanzato&quot;. Impostato su &quot;advanced&quot;, altrimenti il valore predefinito è &quot;basic&quot;. |
| scoringRules | Stringa[] | (Facoltativo) Una stringa di più valori per limitare la regola di contrassegno agli eventi di punteggio identificati dalle regole di punteggio elencate.Voce di esempio:/etc/community/scoring/rules/adv-comments-scoringDefault non è una restrizione. |

## Regole e Badge inclusi {#included-rules-and-badge}

### Badge incluso {#included-badge}

In questa versione beta è incluso un badge di esperti basato sui premi:

* esperto

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

Affinché il contrassegno dell&#39;esperto possa essere visualizzato come una ricompensa per l&#39;attività, devono accadere due cose:

* `badges` deve essere abilitata per la funzione, ad esempio un forum o un componente QnA
* le regole avanzate di valutazione e contrassegno devono essere applicate alla pagina (o antenato) in cui è collocato il componente

Consulta le informazioni di base per:

* [Abilitazione del contrassegno per un componente](implementing-scoring.md#enable-badges-for-component)
* [Applicazione delle regole](implementing-scoring.md#apply-rules-to-content)

### Regole di punteggio e regole secondarie incluse {#included-scoring-rules-and-sub-rules}

Nella versione beta sono incluse due regole di punteggio avanzate per la funzione [](functions.md#forum-function) forum (una per ciascuna delle componenti forum e commenti della funzione forum):

1. /etc/community/scoring/rules/adv-comments-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-Votazione-rule-owner

      /etc/community/scoring/rules/sub-rules/adv-Votazione-rule

2. /etc/community/scoring/rules/adv-forums-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-forums-rule

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-Votazione-rule-owner

**Note:**

* Entrambi `rules`e `sub-rules` i nodi sono di tipo `cq:Page`
* `subRules` è un attributo di tipo String[] sul nodo della `jcr:content` regola
* `sub-rules` può essere condiviso tra diverse regole di punteggio
* `rules` devono trovarsi in una posizione di repository con l&#39;autorizzazione di lettura per tutti
   * i nomi delle regole devono essere univoci indipendentemente dalla posizione

### Regole di Badging incluse {#included-badging-rules}

Nella release sono incluse due regole di contrassegno avanzate che corrispondono ai forum [avanzati e alle regole](#included-scoring-rules-and-sub-rules)di valutazione dei commenti.

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**Note:**

* `rules` nodi di tipo `cq:Page`
* `rules`devono trovarsi in una posizione di repository con l&#39;autorizzazione di lettura per tutti
   * i nomi delle regole devono essere univoci indipendentemente dalla posizione
