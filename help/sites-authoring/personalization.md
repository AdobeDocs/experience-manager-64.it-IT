---
title: Personalizzazione e targeting dei contenuti
seo-title: Personalization and Content Targeting
description: Scopri in che modo AEM può creare contenuti personalizzati
seo-description: Learn how AEM can create personalized content
uuid: 3a1aaa3d-5f57-4fb7-a4be-523f0d274b79
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 850da0da-f7c3-4dd7-bb06-404c14a2a791
exl-id: 669e2509-e563-46ff-b01c-3f05ec196df5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 34%

---

# Personalizzazione e targeting dei contenuti {#personalization}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Personalizzazione e targeting dei contenuti {#personalization-and-content-targeting}

AEM fornisce un set di strumenti per la creazione e modifica di contenuti mirati e la presentazione di esperienze personalizzate.

## Modalità di targeting {#targeting-mode}

[Puoi creare contenuti mirati (di destinazione) utilizzando la modalità di targeting di AEM. ](/help/sites-authoring/content-targeting-touch.md) La modalità di targeting e i componenti di destinazione forniscono gli strumenti necessari per creare i contenuti da usare nelle esperienze delle attività di marketing.

## Attività {#activities}

Le attività definiscono e organizzano le tue attività di marketing. Le attività comprendono i tipi di pubblico di destinazione e il periodo di tempo in cui viene applicato il targeting.

Ad esempio, il catalogo dei prodotti We.Retail include teaser che focalizzano l’attenzione sui prodotti stagionali. L’attività Sport estivi definisce i segmenti di marketing target dei teaser nei mesi estivi.

Le attività identificano inoltre [motore di destinazione](/help/sites-authoring/personalization.md#targeting-engine) che le tue pagine usano.

Utilizza la [Console Attività](/help/sites-authoring/activitylib.md) per creare e gestire le attività dei brand. Puoi anche creare delle attività mentre [realizzi contenuti mirati](/help/sites-authoring/content-targeting-touch.md).

## Esperienze {#experiences}

Per ogni attività, definisci una o più esperienze che identificano il pubblico di destinazione. AEM ti consente di controllare il contenuto che comprende ogni esperienza.

I tipi di pubblico si basano sui segmenti di marketing creati in AEM o Adobe Target. Quando un visitatore apre una pagina web, la logica della pagina determina il pubblico a cui appartiene e visualizza il contenuto creato per quel pubblico.

Ad esempio, un&#39;attività definisce le esperienze per due segmenti di pubblico distinti: le donne over 30 anni e le donne under 30 anni. La pagina Donne del sito Web We.Retail mostra diversi prodotti per ogni esperienza.

Puoi definire le esperienze per un’attività. È possibile utilizzare [Console Attività](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) o [Modalità di targeting](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) per aggiungere esperienze a un’attività.

## Offerte {#offers}

Un&#39;offerta è un contenuto che viene visualizzato in una posizione di una pagina per un&#39;esperienza. Utilizza offerte diverse per esperienze diverse per massimizzare l’efficacia dei contenuti per il pubblico.

Ad esempio, la pagina Donne del sito web di esempio We.Retail può utilizzare le offerte come immagine teaser che appare nella parte superiore della pagina. Un’offerta diversa viene utilizzata come teaser per l’esperienza Donna Over 30 e per l’esperienza Donna Under 30.

Utilizza la [Console Offerte](/help/sites-authoring/offerlib.md) per creare offerte da utilizzare in più esperienze. Crea offerte a uso singolo o aggiungi offerte da una libreria di offerte quando [creazione di contenuti mirati](/help/sites-authoring/content-targeting-touch.md).

## Motore di targeting {#targeting-engine}

Il motore di targeting è il meccanismo che guida la logica per il contenuto di destinazione. Le [attività](/help/sites-authoring/activitylib.md) sono configurate per utilizzare uno di due motori di targeting disponibili: AEM e Adobe Target.

### AEM {#aem}

AEM fornisce un motore di targeting integrato che elabora le richieste di pagina e determina il contenuto da visualizzare. Quando utilizzi il motore di targeting di AEM, puoi usare solo i segmenti creati con AEM per definire il pubblico delle esperienze.

### Adobe Target {#adobe-target}

Il motore di targeting di Adobe Target permette di tenere traccia delle informazioni raccolte dalle visite della pagina in Adobe Target.

* Quando utilizzi questo motore di targeting, utilizza i segmenti importati da Adobe Target per definire i tipi di pubblico per le esperienze.
* Le attività che utilizzano il motore Adobe Target sono [sincronizzato con Target](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target).

Puoi usare questo motore di targeting dopo averlo [integrato con Adobe Target](/help/sites-administering/opt-in.md).
