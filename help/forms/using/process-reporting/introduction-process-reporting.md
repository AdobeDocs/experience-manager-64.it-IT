---
title: Introduzione alla generazione di rapporti sui processi
seo-title: Introduction to Process Reporting
description: Introduzione e funzionalità chiave di AEM Forms per la generazione di rapporti sui processi JEE
seo-description: Introduction and key capabilities of AEM Forms on JEE Process Reporting
uuid: a33ea729-7e1f-4093-bdb6-b8dc3afd59a7
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0cfe62b8-839e-414b-95e5-1bfce6a9d16a
exl-id: 279b2f89-5b91-4b8f-ab0f-8ade9b9f3932
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 3%

---

# Introduzione alla generazione di rapporti sui processi {#introduction-to-process-reporting}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

![reportistica dei processi](assets/process-reporting.png)

Process Reporting è uno strumento basato su browser che consente di creare e visualizzare rapporti sui processi e le attività di AEM Forms.

La funzione di reporting dei processi fornisce una serie di rapporti predefiniti che ti consentono di filtrare, visualizzare informazioni sui processi in esecuzione a lungo termine, sulla durata del processo e sul volume del flusso di lavoro.

Reporting dei processi fornisce un&#39;interfaccia per eseguire query ad hoc e integrare visualizzazioni di report personalizzate nell&#39;interfaccia utente di Reporting dei processi.

Per l’elenco dei browser supportati, consulta [Piattaforme supportate da AEM Forms](/help/forms/using/aem-forms-jee-supported-platforms.md).

Il reporting dei processi è basato su moduli che:

* Lettura dei dati del processo dal database AEM Forms
* Pubblicare i dati del processo in un archivio incorporato di Process Reporting
* Fornisce un&#39;interfaccia utente basata su browser per visualizzare i rapporti

## Funzionalità principali {#key-capabilities}

### Generazione di rapporti sempre attiva {#always-on-reporting}

![gestione del sito](assets/site-management.png)

Visualizza l’elenco dei processi in esecuzione a lungo termine, dei grafici della durata del processo e esegue query personalizzate utilizzando i filtri.

La funzione di reporting dei processi offre anche la possibilità di esportare il rapporto e di eseguire query sui dati in formato CSV.

### Report ad hoc {#adhoc-reports}

![stampa a colori](assets/print-&-colour.png)

Utilizza i filtri per ottenere una visualizzazione specifica dei tuoi dati.

Puoi cercare processi o attività per ID, durata, date di inizio e fine, iniziatore del processo e così via.

Puoi combinare più filtri per creare rapporti specifici.

Puoi quindi salvare i filtri per i rapporti da eseguire in una data o in un’ora successive.

### Cronologia processi/task {#process-task-history}

![gestione dei file](assets/file-management.png)

I server AEM Forms eseguono numerosi processi in parallelo. Questi processi continuano a passare da uno stato all’altro. Pubblicando i dati di Forms nell’archivio di Process Reporting a intervalli regolari, Process Reporting conserva le informazioni di transizione sui processi in esecuzione in AEM Forms.

### Controllo accesso {#access-control-br}

![senza titolo](assets/untitled.png)

La funzione di reporting dei processi consente l’accesso all’interfaccia utente in base alle autorizzazioni.

Ciò significa che solo gli utenti con autorizzazioni di reporting possono accedere all’interfaccia utente di Process Reporting.
