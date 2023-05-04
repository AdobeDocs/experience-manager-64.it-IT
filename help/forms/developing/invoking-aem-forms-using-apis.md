---
title: Richiamo di AEM Forms tramite API
seo-title: Invoking AEM Forms using APIs
description: Adobe Experience Manager Forms è un software aziendale basato su J2EE costituito da servizi che operano all'interno di un'infrastruttura condivisa. Scopri come utilizzare le applicazioni client per richiamare AEM Forms a livello di programmazione utilizzando un’API Java, servizi Web, Remoting e API REST.
seo-description: Adobe Experience Manager Forms is J2EE-based enterprise software that consists of services that operate within a shared infrastructure. Learn how to use client applications to invoke AEM Forms programmatically using a Java API, web services, Remoting, and REST API.
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
role: Developer
exl-id: 6b60209f-aced-4698-97f1-b1a7782eef46
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 2%

---

# Richiamo di AEM Forms tramite API {#invoking-aem-forms-using-apis}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Forms è un software aziendale basato su J2EE costituito da servizi che operano all&#39;interno di un&#39;infrastruttura condivisa. Le operazioni di servizio generalmente consumano o producono documenti. Utilizzando AEM Forms, è possibile combinare il flusso di lavoro dei moduli con i moduli elettronici, la sicurezza dei documenti e la generazione di documenti in un set di servizi integrato e coerente. Questi servizi sono accessibili dall&#39;interno e dall&#39;esterno del firewall.

Le applicazioni client possono richiamare i servizi AEM Forms in modo programmatico utilizzando un’API Java, servizi web, Remoting e REST. Utilizzando la console di amministrazione, puoi configurare un servizio per esporre un endpoint che consente ai servizi AEM Forms di essere richiamati a livello di programmazione. Per impostazione predefinita, la maggior parte dei servizi è preconfigurata per esporre endpoint di tipo Remoting, Java e servizi Web.

I requisiti aziendali determinano quale metodo di chiamata utilizzare. Ad esempio, utilizzando l’API Java, puoi integrare la funzionalità AEM Forms nelle applicazioni aziendali Java, ad esempio Java Entity e Message beans. Allo stesso modo, è possibile integrare le funzionalità di AEM Forms in progetti .NET (o altri progetti sviluppati con ambienti di sviluppo che supportano gli standard di servizi Web) utilizzando i servizi Web.

I servizi richiedono l’esecuzione di un contenitore di servizi, in modo analogo a come Enterprise JavaBeans™ (EJBs) richiede un contenitore J2EE. AEM Forms include una sola implementazione di un contenitore di servizi. Il contenitore di servizi è responsabile della gestione della durata di un servizio, inclusa la distribuzione e l’invio di tutte le richieste al servizio corretto. Gestisce anche i documenti che un servizio consuma o produce.

>[!NOTE]
>
>La programmazione con AEM moduli non include informazioni su come richiamare AEM Forms utilizzando Cartelle controllate o posta elettronica.
