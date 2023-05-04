---
title: Visualizzazione dei dati di analisi delle pagine
seo-title: Seeing Page Analytics Data
description: Utilizza i dati analitici pagina per misurare l’efficacia del contenuto della pagina
seo-description: Use page analytics data to gauge the effectiveness of their page content
uuid: 8dda89be-13e3-4a13-9a44-0213ca66ed9c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 42d2195a-1327-45c0-a14c-1cf5ca196cfc
exl-id: 6509c0ce-fc3a-4248-8dc7-db10602c30d6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 12%

---

# Visualizzazione dei dati di analisi delle pagine{#seeing-page-analytics-data}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Utilizza i dati analitici pagina per misurare l’efficacia del contenuto della pagina.

## Analytics visibile dalla console {#analytics-visible-from-the-console}

![aa-10](assets/aa-10.png)

I dati analitici pagina vengono visualizzati in [Vista a elenco](/help/sites-authoring/basic-handling.md#list-view) della console Sites . Quando le pagine vengono visualizzate in formato elenco, per impostazione predefinita sono disponibili le colonne seguenti:

* Visualizzazioni pagina
* Visitatori univoci
* Tempo sulla pagina

Ogni colonna mostra un valore per il periodo di reporting corrente e indica anche se il valore è aumentato o diminuito rispetto al periodo di reporting precedente. I dati visualizzati vengono aggiornati ogni 12 ore.

>[!NOTE]
>
>Per modificare il periodo di aggiornamento, [configurare l’intervallo di importazione](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Apri **Sites** console; per esempio [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)
1. All’estrema destra della barra degli strumenti (angolo in alto a destra), tocca o fai clic sull’icona per selezionare **Vista a elenco** L’icona visualizzata dipende dal [vista corrente](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)).

1. Di nuovo, all’estrema destra della barra degli strumenti (angolo in alto a destra), tocca o fai clic sull’icona e seleziona **Visualizza impostazioni**. La **Configura colonne** si aprirà la finestra di dialogo . Apporta le modifiche necessarie e conferma con **Aggiorna**.

   ![aa-04](assets/aa-04.png)

### Selezione del periodo di riferimento {#selecting-the-reporting-period}

Seleziona il periodo di reporting per il quale i dati di Analytics vengono visualizzati nella console Sites:

* Dati degli ultimi 30 giorni
* Dati degli ultimi 90 giorni
* Dati di quest&#39;anno

Il periodo di reporting corrente viene visualizzato sulla barra degli strumenti della console Sites (a destra della barra degli strumenti superiore). Utilizza il menu a discesa per selezionare il periodo di reporting richiesto.\
![aa-05](assets/aa-05.png)

### Configurazione delle colonne di dati disponibili {#configuring-available-data-columns}

I membri del gruppo di utenti amministratori di analytics possono configurare la console Sites per consentire agli autori di visualizzare ulteriori colonne di Analytics.

>[!NOTE]
>
>Quando una struttura ad albero di pagine contiene elementi secondari associati a diverse configurazioni cloud di Adobe Analytics, non è possibile configurare le colonne di dati disponibili per le pagine.

1. Nella Vista a elenco, utilizza i selettori di visualizzazione (a destra della barra degli strumenti), seleziona **Visualizza impostazioni** e poi A **Aggiungere dati di Analytics personalizzati**.

   ![aa-15](assets/aa-15.png)

1. Seleziona le metriche da esporre agli autori nella console Sites e fai clic su **Aggiungi**.

   Le colonne visualizzate vengono recuperate da Adobe Analytics.

   ![aa-16](assets/aa-16.png)

### Apertura di Approfondimenti contenuto da Sites {#opening-content-insights-from-sites}

Apri [Approfondimenti contenuto](/help/sites-authoring/content-insights.md) dalla console Sites per approfondire l’efficacia della pagina.

1. Nella console Siti , seleziona la pagina per la quale desideri visualizzare Approfondimenti contenuto.
1. Nella barra degli strumenti, fai clic sull’icona Analytics e Recommendations .

   ![](do-not-localize/chlimage_1-16.png)

## Analytics visibile dall’Editor pagina (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>In seguito a modifiche di sicurezza nell’API di Adobe Analytics, non è più possibile utilizzare la versione di Activity Map inclusa in AEM.
>
>La [Plug-in ActivityMap fornito da Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=it) Da utilizzare.
