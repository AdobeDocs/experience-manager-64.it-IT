---
title: Definizione dei casi di test
seo-title: Defining your Test Cases
description: I casi di test devono essere basati sui casi di utilizzo e sulle specifiche dei requisiti dettagliati
seo-description: Your test cases should be based upon the use cases and the detailed requirements specification
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
exl-id: ad529be3-9d31-492f-943f-ef3e99e13586
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 1%

---

# Definizione dei casi di test{#defining-your-test-cases}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I casi di test devono essere basati su:

**Casi d&#39;uso**

* Questi definiscono la funzionalità necessaria in termini di interazione tra gli attori (ruoli che avviano determinate azioni) e il sistema.
* I casi d’uso devono essere definiti dal cliente.

**Specifiche tecniche**

* Tutti i requisiti funzionali e di prestazioni devono essere verificati.

Le prove devono definire chiaramente:

* Prerequisiti; questi possono riguardare sistemi, configurazioni o esperienza di tester specifici.
* Le misure da seguire; ad un livello di dettaglio adeguato.
* Risultati previsti.
* Cancella i criteri per il superamento o il mancato funzionamento.

La prospettiva di automatizzare i test case è ovviamente attraente in quanto può eliminare i compiti ripetitivi.

## Test manuali e automatici {#manual-versus-automated-tests}

Tuttavia, automatizzare i test case è un investimento significativo, pertanto alcuni aspetti dovrebbero essere presi in considerazione:

* Richiedi tempo, fatica ed esperienza per la configurazione e la configurazione.
* Se basato sul browser, aumenta il rischio di problemi quando vengono installati gli aggiornamenti del browser; che richiedono ulteriore tempo per correggere.
* Solo progetti veramente realizzabili.
* È utile quando vengono generate più versioni per eseguire test o nel piano di rilascio a lungo termine.

## Verifica di aspetti specifici {#testing-specific-aspects}

Nel testare AEM alcuni dettagli specifici sono di particolare interesse:

Ambienti di authoring e pubblicazione

Tuttavia, sono coperti [Ambienti](/help/sites-developing/the-basics.md#environments) vale la pena evidenziare un fattore decisivo di AEM per quanto riguarda i test.

È necessario considerare AEM come due applicazioni:

* la **Autore** ambiente Questa istanza consente agli autori di inserire e pubblicare contenuti.
Questo dispone di un set di utenti piccolo (er) e prevedibile, per i quali funzionalità e prestazioni specifiche sono cruciali.
* la **Pubblica** ambiente Questa istanza presenta il sito web nel relativo modulo pubblicato per l’accesso dei visitatori.
Questo di solito ha un set più ampio di utenti, in cui il volume di traffico non è sempre prevedibile al 100%. Le prestazioni restano cruciali quando si risponde alle richieste. Occorre inoltre considerare la memorizzazione in cache e il bilanciamento del carico.

Anche se lo stesso software in quanto tale, essi:

* a scopi diversi
* hanno requisiti diversi in termini di funzionalità e prestazioni
* sono configurati in modo diverso
* sono sintonizzati separatamente
* avranno ciascuno una propria serie di prove di accettazione

In altre parole devono essere testati separatamente e con diversi casi di prova.

**Personalizzazione**

Quando verifichi la personalizzazione ogni singolo caso d’uso deve essere ripetuto utilizzando più account utente per dimostrare il comportamento.

È inoltre necessario controllare il comportamento corretto nella memorizzazione in cache.

**Dispatcher**

La maggior parte dei progetti installerà Dispatcher per la memorizzazione in cache e il bilanciamento del carico.

Il test è difficile (la memorizzazione in cache si verifica a vari livelli e in varie posizioni) e deve essere eseguita a livello di black-box. Gli aspetti chiave per i quali eseguire la prova sono:

* **Precisione**; assicurati che gli aggiornamenti dei contenuti siano visualizzati dal visitatore del sito web.
* **Continuità**; assicurati che il sito web sia ancora disponibile quando un server viene arrestato.
* **Cluster** I cluster vengono utilizzati per fornire:
   * **Failover**
Se un server non riesce, gli altri server del cluster subiranno un&#39;elaborazione.
   * **Prestazioni**
Il bilanciamento del carico con failover completo aumenta le prestazioni di un cluster.

Se utilizzato per un progetto cliente, il cluster deve essere testato per confermare il corretto funzionamento della configurazione.

## Verifica di software di terze parti {#testing-third-party-software}

Qualsiasi software di terze parti interfacciato a AEM sarà menzionato nelle Specifiche dettagliate dei requisiti.

Eventuali prove richieste (in funzione della portata definita) devono essere analizzate e sottoposte a prova pulita.
