---
title: Panoramica dei rapporti sulle transazioni
seo-title: Transaction Reports Overview
description: Tenere un conteggio di tutti i moduli inviati, la comunicazione interattiva di cui è stato eseguito il rendering, i documenti convertiti in un formato a un altro e altro ancora
seo-description: Keep a count of all the forms submitted, interactive communication rendered, Documents converted to one format to another, and more
uuid: b40220e6-88c8-4507-b228-6c57d9b54422
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 1fb11e02-d8f1-41a0-8e23-cb890b4e2244
exl-id: a545aa0a-9d71-48ba-ba3e-ed30a7e34f3d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 1%

---

# Panoramica dei rapporti sulle transazioni {#transaction-reports-overview}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Tenere un conteggio di tutti i moduli inviati, la comunicazione interattiva di cui è stato eseguito il rendering, i documenti convertiti in un formato a un altro e altro ancora

## Introduzione {#introduction}

I rapporti sulle transazioni in AEM Forms ti consentono di tenere un conteggio di tutte le transazioni effettuate a partire da una data specifica nella distribuzione AEM Forms. L&#39;obiettivo è quello di fornire informazioni sull&#39;utilizzo dei prodotti e aiutare le parti interessate a comprendere i volumi di elaborazione digitale. Esempi di una transazione includono:

* Invio di un modulo adattivo, di un modulo HTML5 o di un set di moduli
* Rendering di una stampa o di una versione web di una comunicazione interattiva
* Conversione di un documento da un formato di file a un altro

Per ulteriori informazioni su ciò che viene considerato una transazione, vedi [API fatturabili](/help/forms/using/transaction-reports-billable-apis.md).

La registrazione delle transazioni è disabilitata per impostazione predefinita. È possibile [abilitare la registrazione delle transazioni](/help/forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) da AEM Web Console. Puoi visualizzare i rapporti sulle transazioni sulle istanze di creazione, elaborazione o pubblicazione. Visualizza rapporti sulle transazioni nelle istanze di creazione o elaborazione per una somma aggregata di tutte le transazioni. Visualizza i rapporti sulle transazioni nelle istanze di pubblicazione per un conteggio di tutte le transazioni che hanno luogo solo sull&#39;istanza di pubblicazione da cui viene eseguito il rapporto.

Non creare contenuti (creare moduli adattivi, comunicazioni interattive, temi e altre attività di authoring) ed elaborare documenti (utilizzare flussi di lavoro, servizi documenti e altre attività di elaborazione) nella stessa istanza AEM. Disattiva la registrazione delle transazioni per i server AEM Forms utilizzati per la creazione di contenuti. Mantieni la registrazione delle transazioni abilitata per i server AEM Forms utilizzati per elaborare i documenti.

![sample-transaction-report-author-1](assets/sample-transaction-report-author-1.png)

Una transazione rimane nel buffer per un periodo specificato (tempo buffer scaricamento + tempo di replica inversa). Per impostazione predefinita, il conteggio delle transazioni impiega circa 90 secondi per riflettere nel report delle transazioni.

Azioni come l’invio di un modulo PDF, l’utilizzo dell’interfaccia utente dell’agente per visualizzare in anteprima una comunicazione interattiva o l’utilizzo di metodi di invio di moduli non standard non vengono contabilizzate come transazioni. AEM Forms fornisce un’API per registrare tali transazioni. Chiama l&#39;API dalle tue implementazioni personalizzate per registrare una transazione.

## Topologia supportata {#supported-topology}

I rapporti sulle transazioni sono disponibili solo in AEM Forms nell’ambiente OSGi. Supporta le topologie di authoring-publish, author-processing-publish e solo di elaborazione. Ad esempio, topologie, vedere [Architettura e topologie di implementazione per AEM Forms](/help/forms/using/transaction-reports-overview.md).

Il conteggio delle transazioni viene replicato inversamente dalle istanze di pubblicazione alle istanze di creazione o di elaborazione. Di seguito è riportata una topologia indicativa di pubblicazione dell’autore:

![semplice autore-pubblicazione-topologia](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>I rapporti sulle transazioni di AEM Forms non supportano topologie che contengono solo istanze di pubblicazione.

### Linee guida per l’utilizzo dei rapporti sulle transazioni {#guidelines-for-using-transaction-reports}

* Disattiva i rapporti sulle transazioni su tutte le istanze dell’autore, in quanto i rapporti sulle istanze dell’autore includono le transazioni registrate durante le attività di authoring.
* Abilita la **Mostra transazioni solo da pubblicazione** nell&#39;istanza dell&#39;autore per visualizzare le transazioni cumulative da tutte le istanze di pubblicazione. Puoi anche visualizzare i rapporti sulle transazioni su ogni istanza di pubblicazione per le transazioni effettive solo su quella particolare istanza di pubblicazione.
* Non utilizzare le istanze di authoring per eseguire flussi di lavoro ed elaborare documenti.
* Prima di utilizzare la generazione di rapporti sulle transazioni, se disponi di una funzionalità con i server di pubblicazione, assicurati che la replica inversa sia abilitata per tutte le istanze di pubblicazione.
* I dati della transazione vengono replicati inversamente da un&#39;istanza di pubblicazione solo all&#39;autore o all&#39;istanza di elaborazione corrispondente. L&#39;istanza di authoring o di elaborazione non può replicare ulteriormente i dati in un&#39;altra istanza. Ad esempio, se disponi di una topologia di creazione-elaborazione-pubblicazione, i dati delle transazioni aggregate vengono replicati solo nell’istanza di elaborazione.

## Articoli correlati {#related-articles}

* [Visualizzazione e comprensione di rapporti sulle transazioni](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [API fatturabili per report transazioni](/help/forms/using/transaction-reports-billable-apis.md)
* [Registra una transazione per implementazioni personalizzate](/help/forms/using/record-transaction-custom-implementation.md)
