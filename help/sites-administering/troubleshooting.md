---
title: Utilizzo dei registri
seo-title: Utilizzo dei registri
description: Scoprite come risolvere AEM utilizzando i file di registro.
seo-description: Scoprite come risolvere AEM utilizzando i file di registro.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 3%

---


# Utilizzo dei registri{#working-with-logs}

Questa sezione contiene informazioni dettagliate sui registri disponibili per la risoluzione dei problemi.

CRX registra registri dettagliati. Dopo aver decompresso e avviato Quickstart, potete trovare i registri nelle seguenti posizioni:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Attivazione del livello di registro DEBUG {#activating-the-debug-log-level}

Il livello di registro predefinito è INFO, ovvero i messaggi DEBUG non vengono registrati.

Per attivare il livello di registro DEBUG, utilizzare CRX Explorer per impostare

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

da eseguire il debug. Non lasciare il registro a livello di registro DEBUG più a lungo del necessario, in quanto genera molti registri.

Una riga nel file di debug in genere inizia con DEBUG, quindi fornisce il livello di registro, l&#39;azione del programma di installazione e il messaggio di registro. Ad esempio:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

I livelli di registro sono i seguenti:

| 0 | Errore irreversibile | L&#39;azione non è riuscita e il programma di installazione non può proseguire. |
|---|---|---|
| 1 | Errore | L&#39;azione non è riuscita. L&#39;installazione continua, ma una parte di CRX non è stata installata correttamente e non funzionerà. |
| 2 | Avvertenza | L&#39;azione è riuscita ma ha incontrato dei problemi. CRX può funzionare o meno correttamente. |
| 3 | Informazioni | L&#39;azione è riuscita. |

## Opzioni dettagliate utilizzate per la risoluzione dei problemi {#verbose-option-used-for-troubleshooting}

Quando avviate CRX, potete aggiungere l&#39;opzione -v (verbose) alla riga di comando come in: &quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

Utilizzate l&#39;opzione dettagliata per la risoluzione dei problemi, in quanto questa opzione consente di visualizzare parte dell&#39;output del registro di avvio rapido sulla console.
