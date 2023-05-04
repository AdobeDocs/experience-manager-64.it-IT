---
title: Integrazione di SPA e Adobe Experience Platform Launch
seo-title: SPA and Adobe Experience Platform Launch Integration
description: Adobe Experience Platform Launch è il metodo consigliato per implementare Analytics, Target e Audience Manager in SPA.
seo-description: Adobe Experience Platform Launch is the recommended way to implement Analytics, Target, and Audience Manager within SPAs.
uuid: 8535a911-2863-4e3b-a3fb-414a0e7e9a4e
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: spa
discoiquuid: a458cc95-cd94-4f3f-9e7b-d6a5780ec4d5
exl-id: 1af29921-7c24-49b5-9f4c-60671641d4e4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 3%

---

# Integrazione SPA e Launch{#spa-and-launch-integration}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Experience Platform Launch è il metodo consigliato per implementare Analytics, Target e Audience Manager nelle applicazioni a pagina singola (SPA).

>[!NOTE]
>
>La funzione Editor applicazioni a pagina singola (SPA) richiede AEM service pack 2 o successivo 6.4.
>
>L’editor di SPA è la soluzione consigliata per i progetti che richiedono SPA rendering lato client basato su framework (ad esempio, React o Angular).

## Tutorial {#tutorial}

Per informazioni su come integrare il SPA con Adobe Experience Platform Launch, consulta [questo articolo e tutorial della knowledge base](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html), che ti guiderà attraverso la configurazione di Launch e implementerà l’Experience Cloud in integrato con Angular o React.

>[!NOTE]
>
>Il KB di riferimento è stato creato per abilitare l’integrazione di Adobe Experience Platform Launch con SPA che non sfruttano l’editor di SPA di AEM. Questi metodi dovrebbero inoltre consentire all’integrazione di Adobe Experience Platform Launch di coesistere con SPA generati per utilizzare l’editor di SPA.
>
>L&#39;utilizzo di Redux insieme alle librerie SPA Javascript non è stato esplorato completamente. Il supporto di Redux è pianificato in una versione futura dell’editor di SPA.
