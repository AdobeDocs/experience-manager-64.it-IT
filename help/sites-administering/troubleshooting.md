---
title: Utilizzo dei registri
seo-title: Working with Logs
description: Scopri come risolvere i problemi di AEM utilizzando i registri.
seo-description: Learn how to troubleshoot AEM by working with logs.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
exl-id: 201e2b57-17c0-4454-9b0e-026e2c95ac63
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 6%

---

# Utilizzo dei registri{#working-with-logs}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa sezione include informazioni dettagliate sui registri disponibili per la risoluzione dei problemi.

CRX registra i registri dettagliati. Dopo aver decompresso e avviato Quickstart, puoi trovare i registri nelle seguenti posizioni:

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Attivazione del livello di registro DEBUG {#activating-the-debug-log-level}

Il livello di registro predefinito è INFO, ovvero i messaggi DEBUG non vengono registrati.

Per attivare il livello di log DEBUG, utilizza l&#39;explorer CRX per impostare il

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

per eseguire il debug. Non lasciare il registro a livello di registro DEBUG più a lungo del necessario, in quanto genera molti registri.

Una riga nel file di debug solitamente inizia con DEBUG, e quindi fornisce il livello di log, l&#39;azione di installazione e il messaggio di log. Ad esempio:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

I livelli di log sono i seguenti:

| 0 | Errore irreversibile | L&#39;azione non è riuscita e non è possibile continuare l&#39;installazione. |
|---|---|---|
| 1 | Errore | L&#39;azione non è riuscita. L&#39;installazione continua, ma una parte di CRX non è stata installata correttamente e non funzionerà. |
| 2 | Avvertenza | L&#39;azione è riuscita ma si sono verificati problemi. CRX potrebbe funzionare o meno correttamente. |
| 3 | Informazioni | L&#39;azione è riuscita. |

## Opzione dettagliata utilizzata per la risoluzione dei problemi {#verbose-option-used-for-troubleshooting}

Quando avvii CRX, puoi aggiungere l&#39;opzione -v (verbose) alla riga di comando come in: &quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

Utilizza l’opzione dettagliata per la risoluzione dei problemi in quanto questa opzione visualizza alcuni dei dati di log quickstart sulla console.
