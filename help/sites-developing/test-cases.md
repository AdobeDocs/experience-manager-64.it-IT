---
title: Definizione dei casi di test
seo-title: Definizione dei casi di test
description: I casi di test devono essere basati sui casi di utilizzo e sulle specifiche dettagliate dei requisiti
seo-description: I casi di test devono essere basati sui casi di utilizzo e sulle specifiche dettagliate dei requisiti
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
translation-type: tm+mt
source-git-commit: 0edddfde1e66ec487139f98e9ffafee885e61dfd

---


# Definizione dei casi di test{#defining-your-test-cases}

I casi di test devono essere basati su:

**Casi di utilizzo**

* Questi definiscono la funzionalità necessaria in termini di interazione tra gli attori (ruoli che avviano determinate azioni) e il sistema.
* I Casi di utilizzo devono essere definiti dal cliente.

**Specifiche dettagliate**

* Tutti i requisiti funzionali e di prestazioni devono essere sottoposti a test.

Le prove devono definire chiaramente:

* Prerequisiti; possono riguardare sistemi, configurazioni o esperienza tester specifici.
* Le misure da seguire; ad un livello di dettaglio adeguato.
* Risultati previsti.
* Cancella criteri per superato o non superato.

La prospettiva di automatizzare i test case è ovviamente attraente in quanto può eliminare le attività ripetitive.

## Test manuali e automatici {#manual-versus-automated-tests}

Tuttavia, l&#39;automazione dei test case è un investimento significativo, pertanto occorre considerare alcuni aspetti:

* Richiedi tempo, fatica ed esperienza per la configurazione.
* Se basato su browser, esiste un rischio maggiore di problemi quando vengono installati gli aggiornamenti del browser; che richiedono ulteriore tempo per correggere.
* Solo realizzabili per grandi progetti.
* Ideale quando vengono generate più versioni per il test o nel piano di rilascio a lungo termine.

## Verificare gli aspetti specifici {#testing-specific-aspects}

Durante il test di AEM, alcuni dettagli specifici sono di particolare interesse:

Ambienti di authoring e pubblicazione

Anche se, in [Ambienti](/help/sites-developing/the-basics.md#environments) , vale la pena evidenziare un fattore determinante di AEM per quanto riguarda i test.

È necessario considerare AEM come due applicazioni:

* ambiente **Authoring** Questa istanza consente agli autori di inserire e pubblicare contenuti.
Questo dispone di un set di utenti piccolo (e) e prevedibile, per i quali funzionalità e prestazioni specifiche sono fondamentali.
* ambiente **Pubblica** Questa istanza presenta il sito Web nel modulo pubblicato per l’accesso dei visitatori.
In genere questo tipo di utenti è composto da un numero maggiore, dove il volume di traffico non è sempre prevedibile al 100%. Le prestazioni sono ancora cruciali, quando si risponde alle richieste. Occorre inoltre considerare la memorizzazione nella cache e il bilanciamento del carico.

Anche se lo stesso software in quanto tale, essi:

* servire scopi diversi
* avere requisiti diversi in termini di funzionalità e prestazioni
* sono configurate in modo diverso
* sono sintonizzati separatamente
* avranno ciascuno una propria serie di prove di accettazione

In altre parole devono essere testati separatamente e con diversi casi di prova.

**Personalizzazione**

Durante il test della personalizzazione ogni singolo caso di utilizzo deve essere ripetuto utilizzando più account utente per dimostrare il comportamento.

È inoltre necessario verificare che la memorizzazione nella cache sia corretta.

**Il dispatcher**

La maggior parte dei progetti installerà il dispatcher per il caching e il bilanciamento del carico.

Il test è difficile (il caching si verifica a vari livelli e in diverse posizioni) e deve essere eseguito a livello di scatola nera. Gli aspetti chiave per i quali eseguire la prova sono:

* **Precisione**; accertatevi che gli aggiornamenti di contenuto siano visibili al visitatore del sito Web.
* **Continuità**; accertatevi che il sito Web sia ancora disponibile quando un server viene spento.
* **I cluster** sono utilizzati per fornire:
   * **Failover** Se un server ha esito negativo, gli altri server del cluster subiranno l&#39;elaborazione.
   * **Il bilanciamento del** carico di prestazioni con failover completo aumenta le prestazioni di un cluster.

Se utilizzato per un progetto cliente, il cluster deve essere testato per confermare il corretto funzionamento della configurazione.

## Verifica del software di terze parti {#testing-third-party-software}

Qualsiasi software di terze parti interfacciato con AEM sarà riportato nelle Specifiche dettagliate dei requisiti.

Eventuali prove richieste (in funzione dell&#39;ambito di applicazione definito) devono essere analizzate e si deve ottenere una prova pulita.
