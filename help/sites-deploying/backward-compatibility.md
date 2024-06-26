---
title: Compatibilità con le versioni precedenti in AEM 6.4
seo-title: Backward Compatibility in AEM 6.4
description: Scopri come mantenere le tue app e configurazioni compatibili con AEM 6.4
seo-description: Learn how to keep your apps and configurations compatible with AEM 6.4
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
feature: Upgrading
exl-id: 5798100a-e03a-43f8-9189-ae51c06e192b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 2%

---

# Compatibilità con le versioni precedenti in AEM 6.4{#backward-compatibility-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

>[!NOTE]
>
>Per un elenco delle modifiche di contenuto e configurazione che non rientrano nell’ambito del pacchetto di compatibilità, consulta [Ristrutturazione dell’archivio in AEM 6.4](/help/sites-deploying/repository-restructuring.md).

Nella AEM 6.4, tutte le funzioni sono state sviluppate pensando alla compatibilità con le versioni precedenti.

Nella maggior parte dei casi, i clienti che eseguono AEM 6.3 non devono modificare il codice o le personalizzazioni durante l&#39;aggiornamento. Per i clienti AEM 6.1 e 6.2 non vi sono modifiche di interruzione aggiuntive rispetto a quelle che si verificherebbero durante un aggiornamento alla versione 6.3.

Per le eccezioni in cui le funzionalità non potevano essere mantenute compatibili con le versioni precedenti, è possibile ottenere la compatibilità con le versioni precedenti per i bundle e i contenuti installando un pacchetto di compatibilità per la versione 6.3 (vedi come impostare di seguito per i dettagli su dove scaricare). Questo pacchetto di compatibilità ripristina la compatibilità per le applicazioni conformi a AEM 6.3.

Il pacchetto di compatibilità consente di eseguire AEM in modalità di compatibilità e di differire lo sviluppo personalizzato rispetto alle nuove funzioni di AEM:

>[!NOTE]
>
>Nota che il pacchetto di compatibilità è solo una soluzione temporanea per posticipare lo sviluppo necessario per essere compatibile con AEM 6.4. Questa opzione è consigliata solo come ultima se non sei in grado di risolvere i problemi di compatibilità tramite sviluppo immediatamente dopo l’aggiornamento. Si consiglia vivamente di passare alla modalità nativa e disinstallare il pacchetto di compatibilità una volta deciso di procedere con lo sviluppo personalizzato basato su 6.4 e usufruire della funzionalità 6.4 completa.

![screen_shot_2018-04-05at43339pm](assets/screen_shot_2018-04-05at43339pm.png)

Il pacchetto di compatibilità dispone di due modalità: **Routing abilitato** e **Routing disattivato**.

Questo consente di eseguire AEM 6.4 in tre modalità:

**Modalità nativa:**

La modalità nativa è per i clienti che desiderano utilizzare tutte le nuove funzioni di AEM 6.4 e sono pronti a svolgere alcune attività di sviluppo per far sì che le loro personalizzazioni funzionino con tutte le nuove funzioni.

Ciò significa che potrebbe essere necessario apportare modifiche all&#39;applicazione immediatamente dopo l&#39;aggiornamento.

**Modalità di compatibilità: Pacchetto di compatibilità installato con Routing abilitato**

La modalità di compatibilità è destinata ai clienti che hanno personalizzazioni di interfacce non compatibili con le versioni precedenti. Questo consente di eseguire AEM in modalità di compatibilità e di differire lo sviluppo personalizzato richiesto rispetto alle nuove funzionalità AEM che non sono compatibili con alcuni dei codici personalizzati.

**Modalità legacy: Pacchetto di compatibilità installato con Routing disabilitato**

La modalità legacy è destinata ai clienti con interfacce personalizzate basate su codice legacy o obsoleto di AEM che è stato spostato nel pacchetto di compatibilità.

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## Configurazione {#how-to-set-up}

Il pacchetto di compatibilità AEM 6.3 può essere installato come pacchetto utilizzando Gestione pacchetti. È possibile scaricare [Pacchetto di compatibilità di AEM 6.3 dalla Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63) sito.

Una volta installato il pacchetto di compatibilità, il routing può essere abilitato o disabilitato utilizzando un interruttore nella configurazione OSGI come mostrato di seguito:

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

Una volta installato e configurato il pacchetto di compatibilità, le funzioni verranno utilizzate in base alla modalità di compatibilità scelta.
