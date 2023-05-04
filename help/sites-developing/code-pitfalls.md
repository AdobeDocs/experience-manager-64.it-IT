---
title: Problemi di codice
seo-title: Code pitfalls
description: Problemi comuni di codifica da evitare durante lo sviluppo per AEM
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 6%

---

# Problemi di codice{#code-pitfalls}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Evitare i binding Sling nel codice Java {#avoid-sling-bindings-in-java-code}

I binding Sling sono un modo inappropriato per accedere a un servizio nel 90% dei casi. Invece, devi utilizzare *@Reference* o *@Inject* annotazioni.

## Evita Thread.interrupt nel codice Java {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* è pericoloso perché può chiudere i file, inclusi i file Lucene e i file di cache persistenti, quando vengono chiamati al momento sbagliato.

## Evita di mixare la sincronizzazione Java con ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Questo può portare a una condizione di corsa in cui il codice alla fine si bloccherà.
