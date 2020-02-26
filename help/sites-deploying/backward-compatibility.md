---
title: Compatibilità con le versioni precedenti in AEM 6.4
seo-title: Compatibilità con le versioni precedenti in AEM 6.4
description: Scopri come mantenere le tue app e configurazioni compatibili con AEM 6.4
seo-description: Scopri come mantenere le tue app e configurazioni compatibili con AEM 6.4
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Compatibilità con le versioni precedenti in AEM 6.4{#backward-compatibility-in-aem}

## Panoramica {#overview}

>[!NOTE]
>
>Per un elenco delle modifiche al contenuto e alla configurazione che non rientrano nell’ambito del pacchetto di compatibilità, consultate Ristrutturazione [repository in AEM 6.4](/help/sites-deploying/repository-restructuring.md).

In AEM 6.4, tutte le funzioni sono state sviluppate tenendo presente la compatibilità con le versioni precedenti.

Nella maggior parte dei casi, i clienti che eseguono AEM 6.3 non devono cambiare il codice o le personalizzazioni durante l&#39;aggiornamento. Per i clienti di AEM 6.1 e 6.2 non vi sono modifiche di interruzione aggiuntive rispetto a quelle apportate durante un aggiornamento alla versione 6.3.

Per le eccezioni per le quali non è possibile mantenere le funzionalità compatibili con le versioni precedenti, è possibile ottenere la compatibilità con le versioni precedenti per i bundle e i contenuti installando un pacchetto di compatibilità per la versione 6.3 (vedere come impostare di seguito per informazioni su dove scaricare). Questo pacchetto di supporto ripristinerà la compatibilità per le applicazioni conformi a AEM 6.3.

Il pacchetto di compatibilità consente di eseguire AEM in modalità di compatibilità e di differire lo sviluppo personalizzato rispetto alle nuove funzioni di AEM:

>[!NOTE]
>
>Il pacchetto di compatibilità è solo una soluzione temporanea per posticipare lo sviluppo necessario per essere compatibile con AEM 6.4. È consigliato solo come ultima opzione se non siete in grado di risolvere problemi di compatibilità tramite lo sviluppo subito dopo l’aggiornamento. È fortemente consigliato passare alla modalità nativa e disinstallare il pacchetto di compatibilità una volta che si decide di procedere con lo sviluppo personalizzato basato su 6.4 e sfruttare la funzionalità completa 6.4.

![screen_shot_2018-04-05at43339 pm](assets/screen_shot_2018-04-05at43339pm.png)

Il pacchetto di compatibilità presenta due modalità: **Routing abilitato** e **Routing disattivato**.

Questo consente di eseguire AEM 6.4 in tre modalità:

**Modalità nativa:**

La modalità nativa è per i clienti che desiderano utilizzare tutte le nuove funzioni di AEM 6.4 e sono pronti a sviluppare qualcosa per far sì che le loro personalizzazioni funzionino con tutte le nuove funzioni.

Ciò significa che potrebbe essere necessario apportare modifiche all&#39;applicazione subito dopo l&#39;aggiornamento.

**Modalità compatibilità: Pacchetto di compatibilità installato con Routing abilitato**

La modalità di compatibilità è per i clienti che hanno personalizzazioni di interfacce non compatibili con le versioni precedenti. Questo consente ad AEM di essere eseguito in modalità di compatibilità e di posticipare lo sviluppo personalizzato richiesto rispetto alle nuove funzioni di AEM non compatibili con alcuni codici personalizzati.

**Modalità legacy: Pacchetto di compatibilità installato con Routing disattivato**

La modalità legacy è per i clienti con interfacce personalizzate basate su codice legacy o obsoleto di AEM spostato nel pacchetto di compatibilità.

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## Come impostare {#how-to-set-up}

Il pacchetto di compatibilità di AEM 6.3 verrà installato come pacchetto tramite Gestione pacchetti al [collegamento](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63).

Una volta installato il pacchetto di compatibilità, il routing può essere abilitato o disabilitato utilizzando uno switch nella configurazione OSGI come mostrato di seguito:

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

Una volta installato e configurato il pacchetto di compatibilità, le funzioni verranno utilizzate in base alla modalità di compatibilità scelta.
