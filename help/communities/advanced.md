---
title: Punteggio e badge avanzati
seo-title: Punteggio e badge avanzati
description: Impostazione del punteggio avanzato
seo-description: Impostazione del punteggio avanzato
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 1%

---


# Punteggio e badge avanzati {#advanced-scoring-and-badges}

## Panoramica {#overview}

Il punteggio avanzato consente di assegnare i badge per identificare i membri come esperti. Il punteggio avanzato assegna i punti in base alla quantità *e* di contenuto creato da un membro, mentre il punteggio di base assegna i punti semplicemente in base alla quantità di contenuto creato.

Questa differenza è dovuta al motore di valutazione utilizzato per calcolare i punteggi. Il motore di punteggio di base applica una matematica semplice. Il motore di valutazione avanzato è un algoritmo adattivo che premia i membri attivi che contribuiscono a contenuti importanti e valutati, detratti attraverso l’elaborazione delle lingue naturali (NLP) di un argomento.

Oltre alla rilevanza del contenuto, gli algoritmi di punteggio tengono conto delle attività dei membri, come il voto e la percentuale di risposte. Il punteggio di base li include in termini quantitativi, mentre il punteggio avanzato li utilizza in modo algoritmico.

Pertanto, il motore di valutazione avanzato richiede dati sufficienti per rendere significativa l’analisi. La soglia di successo per diventare un esperto viene costantemente rivalutata in quanto l&#39;algoritmo si regola continuamente sul volume e la qualità dei contenuti creati. C&#39;è anche un concetto di *decadimento* dei post precedenti di un membro. Se un membro esperto smette di partecipare all&#39;oggetto in cui ha ottenuto lo status di esperto, ad un certo punto predeterminato (vedere [configurazione del motore di punteggio](#configurable-scoring-engine)) potrebbe perdere il proprio status di esperto.

L’impostazione del punteggio avanzato è praticamente identica al punteggio di base:

* Le regole di valutazione e contrassegno di base e avanzate sono [applicate al contenuto](implementing-scoring.md#apply-rules-to-content) nello stesso modo
   * Regole di valutazione e contrassegno di base e avanzate possono essere applicate allo stesso contenuto
* [Abilitazione dei badge per ](implementing-scoring.md#enable-badges-for-component) componenti generici

Le differenze nella configurazione delle regole di valutazione e di badging sono le seguenti:

* Motore di valutazione avanzato configurabile
* Regole di valutazione avanzate:
   * `scoringType` impostato su  **[!UICONTROL avanzato]**
   * Richiede parole di arresto

* Regole di contrassegno avanzate:
   * `badgingType` impostato su  **[!UICONTROL avanzato]**
   * `badgingLevels` numero di livelli di esperti da assegnare
   * Richiede `badgingPaths` array di badge invece delle soglie dei punti di mappatura degli array sui badge

>[!NOTE]
>
>Per utilizzare le funzionalità avanzate di valutazione e contrassegno, installa il [pacchetto di identificazione esperto](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg).

## Motore di valutazione configurabile {#configurable-scoring-engine}

Il motore di punteggio avanzato fornisce una configurazione OSGi con parametri che influiscono sull’algoritmo di punteggio avanzato.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL Pesi]**
di valutazionePer un argomento, specifica il verbo a cui deve essere data la priorità più alta durante il calcolo del punteggio. È possibile inserire uno o più argomenti, ma è limitato a **un verbo per argomento**. Vedere [Argomenti e verbi](implementing-scoring.md#topics-and-verbs).

   Inserito come `topic,verb` con la virgola in sequenza. Esempio:

   `/social/forum/hbs/social/forum\,ADD`

   L’impostazione predefinita è impostata sul verbo ADD per i componenti QnA e forum.


* **[!UICONTROL Intervallo di valutazione]**

   L’intervallo per i punteggi avanzati è definito da questo valore (punteggio massimo possibile) e da 0 (punteggio più basso possibile.

   Il valore predefinito è 100, quindi l’intervallo di punteggio è compreso tra 0 e 100.


* **[!UICONTROL Intervallo di tempo decadimento entità]**

   Questo parametro rappresenta il numero di ore in cui tutti i punteggi dell’entità sono decaduti. Questo è necessario per non includere più i vecchi contenuti nei punteggi di un sito community.

   Il valore predefinito è 216000 ore (~24 anni).


* **[!UICONTROL Tasso di crescita del punteggio]**

   Specifica il punteggio. tra 0 e il punteggio, oltre il quale la crescita rallenta per limitare il numero di esperti.

   Il valore predefinito è 50.

## Regole di valutazione avanzate {#advanced-scoring-rules}

Nel punteggio di base, è nota la quantità necessaria per ottenere un badge.

Nel punteggio avanzato, la quantità necessaria viene costantemente adattata in base alla quantità di dati di qualità all&#39;interno del sistema. Il punteggio viene continuamente calcolato in modo simile a una curva a campana.

Se un membro ha guadagnato un badge esperto su un argomento che non è più attivo, c&#39;è la possibilità che perderà il loro badge a causa di decadimento nel tempo.

### Tipo di punteggio {#scoringtype}

Una regola di punteggio è un insieme di regole secondarie di punteggio, ciascuna delle quali dichiara il valore `scoringType`.

Per richiamare il motore di punteggio avanzato, è necessario impostare `scoringType`su `advanced`.

Consulta [Sottoregole di punteggio](implementing-scoring.md#scoring-sub-rules).

![chlimage_1-261](assets/chlimage_1-261.png)

### Stopwords {#stopwords}

Il pacchetto di valutazione avanzato installa una cartella di configurazione contenente un file di parole chiave:

* `/etc/community/scoring/configuration/stopwords`

L’algoritmo di valutazione avanzato utilizza l’elenco di parole contenute nel file stopwords per identificare le parole inglesi comuni che vengono ignorate durante l’elaborazione del contenuto.

Non è previsto che il file venga modificato.

Se il file delle parole chiave è mancante, il motore di punteggio avanzato genererà un errore.

## Regole di contrassegno avanzate {#advanced-badging-rules}

Le proprietà avanzate della regola di badging sono diverse dalle proprietà [base della regola di badging](implementing-scoring.md#badging-rules).

Invece di associare i punti a un’immagine del badge, è necessario solo identificare il numero di esperti consentiti e l’immagine del badge da assegnare.

![chlimage_1-262](assets/chlimage_1-262.png)

| **Proprietà** | **Tipo** | **Descrizione valore** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | Stringa[] | (Obbligatorio) Una stringa con più valori di immagini di badge fino al numero di badgingLevels. I percorsi immagine del badge devono essere ordinati in modo che il primo venga assegnato all’esperto più alto. Se sono presenti meno badge rispetto a quelli indicati da badgingLevels, l’ultimo badge nell’array riempie il resto dell’array. Esempio di voce:/etc/community/badging/images/Expert-badge/jcr:content/expert.png |
| badgingLevels | Lungo | (Facoltativo) Specifica i livelli di esperienza da assegnare. Ad esempio, se ci devono essere un esperto e un esperto (due badge), il valore deve essere impostato su 2. Il badgingLevel deve corrispondere al numero di immagini del badge relative agli esperti elencate per la proprietà badgingPath . Il valore predefinito è 1. |
| badgingType | Stringa | (Obbligatorio) Identifica il motore di punteggio come &quot;base&quot; o &quot;avanzato&quot;. Imposta su &quot;advanced&quot; altrimenti il valore predefinito è &quot;basic&quot;. |
| scoringRules | Stringa[] | (Facoltativo) Una stringa con più valori per limitare la regola di contrassegno agli eventi di punteggio identificati dalle regole di punteggio elencate.Voce di esempio:/etc/community/scoring/rules/adv-comments-scoringDefault non è una restrizione. |

## Regole incluse e badge {#included-rules-and-badge}

### Badge incluso {#included-badge}

In questa versione beta è incluso un badge di esperti basato su premi:

* esperto

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

Affinché il badge dell’esperto possa apparire come una ricompensa per l’attività, devono verificarsi due eventi:

* `badges` deve essere abilitata per la funzione , ad esempio un forum o un componente QnA
* le regole avanzate di punteggio e contrassegno devono essere applicate alla pagina (o all’predecessore) in cui è posizionato il componente.

Vedi le informazioni di base per:

* [Abilitazione del contrassegno per un componente](implementing-scoring.md#enable-badges-for-component)
* [Applicazione delle regole](implementing-scoring.md#apply-rules-to-content)

### Regole di punteggio e sottorete incluse {#included-scoring-rules-and-sub-rules}

Nella versione beta sono incluse due regole di punteggio avanzate per la [funzione forum](functions.md#forum-function) (una per ogni componente forum e commenti della funzione forum):

1. /etc/community/scoring/rules/adv-comments-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-vote-rule-owner

      /etc/community/scoring/rules/sub-rules/adv-vote rule

2. /etc/community/scoring/rules/adv-forums-scoring

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-forums-rule

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-vote-rule-owner

**Note:**

* I nodi `rules`e `sub-rules` sono entrambi di tipo `cq:Page`
* `subRules` è un attributo di tipo Stringon [] the  `jcr:content` node della regola
* `sub-rules` può essere condiviso tra diverse regole di punteggio
* `rules` devono trovarsi in una posizione archivio con autorizzazione di lettura per tutti
   * i nomi delle regole devono essere univoci indipendentemente dalla posizione

### Regole di contrassegno incluse {#included-badging-rules}

Nella versione sono incluse due regole di badging avanzate che corrispondono ai [forum avanzati e regole di punteggio dei commenti](#included-scoring-rules-and-sub-rules).

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**Note:**

* `rules` nodi di tipo  `cq:Page`
* `rules`devono trovarsi in una posizione archivio con autorizzazione di lettura per tutti
   * i nomi delle regole devono essere univoci indipendentemente dalla posizione
