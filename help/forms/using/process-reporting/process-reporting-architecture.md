---
title: Come funziona Reporting dei processi
seo-title: Come funziona Reporting dei processi
description: Descrizione dei servizi che compongono l'AEM Forms  su JEE Process Reporting e introduzione all'interfaccia utente di Process Reporting
seo-description: Descrizione dei servizi che compongono l'AEM Forms  su JEE Process Reporting e introduzione all'interfaccia utente di Process Reporting
uuid: 00a2dd6d-8a6f-4c7b-b03e-81cfd4bcf50d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: process-reporting
discoiquuid: 4afc68fc-6b39-4c31-95fa-2ef3111c57da
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# Funzionamento di Reporting dei processi {#how-process-reporting-works}

Process Reporting è il modulo di reporting dell&#39;AEM Forms  su JEE.

Process Reporting (Generazione rapporti di processo) consente di eseguire rapporti  processi e attività AEM Forms.

Process Reporting utilizza l&#39;archivio di Process Reporting incorporato per pubblicare i dati Forms. Quindi utilizza quei dati per eseguire i report.

Process Reporting è costituito dai seguenti moduli:

* [Servizio ProcessDataPublisher](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatapublisher-service-br-p)
* [Servizio ProcessDataStorage](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatastorageprovider-service-br-p)
* [servizio OSGi](/help/forms/using/process-reporting/process-reporting-architecture.md#p-osgi-service-br-p)
* [Server dati query](/help/forms/using/process-reporting/process-reporting-architecture.md#p-querydataservlet-service-br-p)
* [Interfaccia utente di Process Reporting](/help/forms/using/process-reporting/process-reporting-architecture.md#p-process-reporting-user-interface-br-p)

## Architettura di reporting dei processi {#process-reporting-architecture-br}

![processreportistica](assets/processreportingarchitecture.png)

## Moduli di generazione rapporti processo {#process-reporting-modules}

### Servizio ProcessDataPublisher {#processdatapublisher-service-br}

Il server ProcessDataPublisher viene eseguito periodicamente sul database AEM Forms  ed estrae i dati modificati dall&#39;ultima esecuzione del servizio. Quindi pubblica i dati nel servizio Process Data Storage.

Per informazioni dettagliate sulla configurazione del servizio, vedere [Configurare il servizio ProcessDataPublisher](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p).

### Servizio ProcessDataStorageProvider {#processdatastorageprovider-service-br}

Il servizio ProcessDataStorageProvider riceve i dati del processo dal servizio ProcessDataPublisher e li salva nell&#39;archivio di Process Reporting.

Per informazioni dettagliate sulla configurazione del servizio, vedere [Configurare il servizio ProcessDataStorageProvider](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p).

### Servizio OSGi {#osgi-service-br}

QueryDataServlet utilizza questo servizio per ottenere i dati di reporting dall&#39;archivio di Process Reporting.

### Servizio QueryDataServlet {#querydataservlet-service-br}

Il servizio QueryDataServlet accetta le query dall&#39;interfaccia utente di Process Reporting.

Il servizio utilizza quindi i servizi OSGi per ottenere i dati di reporting rilevanti, elabora i dati e restituisce i dati all&#39;interfaccia utente.

### Interfaccia utente di Process Reporting {#process-reporting-user-interface-br}

L&#39;interfaccia utente di Process Reporting è basata su browser Web. È possibile utilizzare questa interfaccia per visualizzare le informazioni su processi e attività pubblicate dal database AEM Forms .

### Servizio QueryDataServlet {#querydataservlet-service-br-1}

Il servizio QueryDataServlet accetta le query dall&#39;interfaccia utente di Process Reporting.

Il servizio utilizza quindi i servizi OSGi per ottenere i dati di reporting rilevanti, elabora i dati e restituisce i dati all&#39;interfaccia utente.

### Report personalizzati {#custom-reports-br}

Potete creare rapporti personalizzati e visualizzarli nella scheda Report personalizzati dell&#39;interfaccia utente di Process Reporting.

Per i passaggi necessari per creare un rapporto personalizzato, vedere Creazione di un rapporto personalizzato nell&#39;articolo [Report personalizzati in Process Reporting](/help/forms/using/process-reporting/process-reporting-custom-reports.md).

