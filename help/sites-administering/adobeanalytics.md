---
title: Integrazione con Adobe Analytics
seo-title: Integrazione con Adobe Analytics
description: Scoprite come integrare AEM con  Adobe Analytics.
seo-description: Scoprite come integrare AEM con  Adobe Analytics.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
translation-type: tm+mt
source-git-commit: 98fae2d51d73bda946f3c398e9276fe4d5a8a0fe
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 21%

---


# Integrazione con Adobe Analytics{#integrating-with-adobe-analytics}

L’integrazione  Adobe Analytics e AEM consente di monitorare l’attività della pagina Web:

* Una configurazione Adobe Analytics  consente AEM l&#39;autenticazione con  Adobe Analytics.
* Un framework identifica i dati inviati alla suite di rapporti Adobe Analytics .

I dati comprendono i dati di pagina e utente; ad esempio:

* dati raccolti AEM componenti
* clic collegamento
* informazioni sull’utilizzo video
* il numero di visite di pagina da  Adobe Analytics

Le pagine seguenti consentono di configurare l&#39;integrazione:

* [Connessione a  Adobe Analytics e creazione di framework](/help/sites-administering/adobeanalytics-connect.md)
* [Configurazione del tracciamento dei collegamenti per  Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Mappatura dei dati dei componenti con  delle proprietà Adobe Analytics](/help/sites-administering/adobeanalytics-mapping.md)
* [Configurazione del tracciamento video per  Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)

Per eseguire facilmente l&#39;integrazione è inoltre possibile utilizzare la [procedura guidata di consenso](/help/sites-administering/opt-in.md).

>[!NOTE]
>
>Consultate anche l’articolo introduttivo: [Integrazione AEM con  Adobe Target e  Adobe Analytics mediante DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## Ulteriori informazioni {#further-information}

Consulta:

* [Estensione  ](/help/sites-developing/extending-analytics.md) Integrazione Adobe Analytics per informazioni sullo sviluppo di componenti che raccolgono dati utente e la personalizzazione del framework Adobe Analytics .
* L&#39;articolo della knowledge base, [ integrazione Adobe Analytics - risoluzione dei problemi](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), per informazioni su come risolvere i problemi dell&#39;integrazione  Adobe Analytics.

>[!NOTE]
>
>Se utilizzi Adobe Analytics con una configurazione proxy personalizzata, devi [configurare due bundle OSGi](/help/sites-deploying/configuring-osgi.md) (ad esempio, con la console web), necessari per le configurazioni proxy **Apache HTTP Client**. Entrambi sono necessari, poiché alcune funzionalità di AEM utilizzano le API 3.x, mentre altre le API 4.x. Configurazione:
>
>* **Day Commons HTTP Client 3.1** per configurare l&#39;API 3.x;\
   >  ad esempio, [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Configurazione proxy** dei componenti Apache HTTP per configurare l&#39;API 4.x;
>
>  
ad esempio, [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

