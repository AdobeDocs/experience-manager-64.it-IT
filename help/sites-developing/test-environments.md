---
title: Quali ambienti di test sono necessari?
seo-title: Which Test Environments are needed?
description: Diversi ambienti devono essere considerati come parte dei test
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 3%

---

# Quali ambienti di test saranno necessari?{#which-test-environments-will-be-needed}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per definire quali configurazioni per il test, considera quanto segue:

**Sviluppo** - per unità e determinati test di integrazione.

**Test** - Per la maggior parte dei test.

**Live** - per le prove finali di prestazioni e di stress. Anche per i test di accettazione con il cliente.

Sarà inoltre necessario decidere quali istanze saranno necessarie dove (di solito almeno una di ciascuna per tutti i livelli di test):

**Autore** - Questa istanza consente agli autori di inserire e pubblicare contenuti.

**Pubblica** - Questa istanza presenta il sito web nel suo modulo pubblicato per l’accesso dei visitatori.

Deve essere testato insieme al Dispatcher.

Infine, è necessario considerare l&#39;hardware effettivo: qualsiasi test di prestazioni deve essere effettuato su un sistema il più vicino possibile alla configurazione dell&#39;ambiente live finale. Per questo motivo, si consiglia anche di dividere il lancio del progetto in un:

**Lancio morbido** - riduzione della disponibilità; che consente di disporre di tempo per i test delle prestazioni, la messa a punto e l&#39;ottimizzazione in condizioni realistiche nell&#39;ambiente di produzione.

**Lancio rigido** - Piena disponibilità.
