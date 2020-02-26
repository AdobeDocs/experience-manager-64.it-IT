---
title: Strumenti di verifica e tracciamento
seo-title: Strumenti di verifica e tracciamento
description: AEM offre un framework per il test dell’interfaccia utente dei componenti e un meccanismo per il test e il debug dei componenti
seo-description: AEM offre un framework per il test dell’interfaccia utente dei componenti e un meccanismo per il test e il debug dei componenti
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
translation-type: tm+mt
source-git-commit: 60f36a33471dbbd9ca877dbbedc82ade606a125c

---


# Strumenti di verifica e tracciamento{#testing-and-tracking-tools}

## Test {#testing}

AEM fornisce:

* [un framework per il test dell’interfaccia](/help/sites-developing/hobbes.md)del componente.
* [un meccanismo di verifica e debug dei componenti](/help/sites-developing/developer-mode.md).

Di seguito sono riportati due strumenti Open Source Testing:

**Selenio**

Il selenio viene utilizzato per il test delle funzioni in un browser con un utente per attività. Registra i passaggi di test (clic) come tabelle HTML o classi Java.

Per ulteriori informazioni, consultate [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter viene utilizzato per monitorare le richieste e può essere utilizzato per test funzionali, di prestazioni e di stress.

Per ulteriori informazioni, consultate [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

Esistono anche molti strumenti proprietari per automatizzare i test e gestire i piani di test.

## Tracciamento {#tracking}

I seguenti strumenti sono facilmente disponibili. Tuttavia, un problema fondamentale in tutti i casi è la disponibilità dei dati a tutti i membri del team - partner e cliente del progetto.

**Bugzilla**

Un sistema di monitoraggio dei bug che può essere configurato in base alle proprie esigenze.

**Fogli di calcolo**

Anche se non specificamente uno strumento di tracciamento dei bug, i fogli di calcolo vengono spesso utilizzati in modo improprio a questo scopo, in quanto sono facili da capire e la maggior parte degli utenti ha esperienza della loro funzionalità.

Se vengono utilizzati per il tracciamento,

* dovrebbero essere tenuti semplici.
* il numero dei singoli fogli di calcolo dovrebbe essere limitato al minimo.
* devono essere aggiornati regolarmente.
* è necessario mantenere una sola copia master e tutti devono sapere dov&#39;è la copia master.
* devono essere accessibili a tutti i membri del progetto.
* se la sicurezza è un problema (spesso si verifica in grandi aziende) e l&#39;accesso comune non è possibile, le copie possono essere distribuite purché tutti comprendano che si tratta di copie e che non è possibile aggiornarle.

Anche in questo caso esistono molti strumenti proprietari per tenere traccia dei bug e dei requisiti delle funzioni.
