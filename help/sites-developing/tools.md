---
title: Strumenti di test e tracciamento
seo-title: Testing and Tracking Tools
description: AEM fornisce un framework per la verifica dell’interfaccia utente dei componenti e un meccanismo per la verifica e il debug dei componenti
seo-description: AEM provides a framework for testing component UI and a mechanism for testing and debugging components
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
exl-id: 9387cdb4-f8de-4229-90d1-59218ac17561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 3%

---

# Strumenti di test e tracciamento{#testing-and-tracking-tools}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Test {#testing}

AEM fornisce:

* [un framework per il test dell’interfaccia utente dei componenti](/help/sites-developing/hobbes.md).
* [un meccanismo per la verifica e il debug dei componenti](/help/sites-developing/developer-mode.md).

Di seguito sono riportati due strumenti di test Open Source:

**Selenio**

Il selenio viene utilizzato per il test delle funzioni in un browser con un utente per attività. Registra i passaggi di test (clic) come tabelle HTML o classi Java.

Per ulteriori informazioni consulta [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter viene utilizzato per monitorare le richieste e può essere utilizzato per prove funzionali, di prestazioni e di stress.

Per ulteriori informazioni consulta [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

Esistono anche molti strumenti proprietari per automatizzare i test e gestire i piani di test.

## Tracking {#tracking}

I seguenti strumenti sono facilmente disponibili. Tuttavia, un problema fondamentale in tutti i casi è la disponibilità dei dati a tutti i membri del team del progetto - partner e cliente.

**Bugzilla**

Un sistema di tracciamento dei bug configurabile in base alle tue esigenze.

**Fogli di calcolo**

Anche se non specificamente uno strumento di tracciamento dei bug, i fogli di calcolo vengono spesso utilizzati in modo improprio a questo scopo in quanto sono facili da capire e la maggior parte degli utenti hanno esperienza della loro funzionalità.

Se vengono utilizzati per il tracciamento, allora:

* dovrebbero essere mantenuti semplici.
* il numero dei singoli fogli di calcolo dovrebbe essere ridotto al minimo.
* devono essere aggiornati regolarmente.
* è necessario mantenere una sola copia master e tutti devono sapere dove si trova la copia master.
* devono essere accessibili a tutti i membri del progetto.
* se la sicurezza è un problema (spesso si verifica in grandi aziende) e l&#39;accesso comune non è possibile, le copie possono essere distribuite purché tutti comprendano che si tratta di copie e non possono essere aggiornate.

Anche in questo caso esistono molti strumenti proprietari per il monitoraggio di bug e requisiti di funzionalità.
