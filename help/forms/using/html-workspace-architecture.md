---
title: Architettura di AEM Forms Workspace
seo-title: AEM Forms Workspace Architecture
description: Informazioni concettuali e panoramica dell’architettura di LiveCycle AEM Forms Workspace.
seo-description: Conceptual information and overview of the architecture of LiveCycle AEM Forms workspace.
uuid: e1a48452-ed44-4ea7-ba38-d961c8faafa5
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c3a312fb-f684-477d-916d-2d3c99aa7607
exl-id: 30bde8d6-7959-4e4b-a6f4-faf52444e67a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 3%

---

# Architettura di AEM Forms Workspace {#aem-forms-workspace-architecture}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Forms workspace è un&#39;applicazione web ospitata su CRX™. Quando workspace viene aperto in un browser, si accede a una risorsa CRX e l&#39;applicazione viene riprodotta come pagina HTML nel browser.

L’applicazione accede al server AEM Forms sugli endpoint REST per effettuare le seguenti operazioni:

* Recupera attività utente, punti iniziali del processo, cronologia del processo e informazioni utente
* Eseguire azioni sulle attività
* Attività di query nel database
* Aggiorna le preferenze utente e altro ancora

Il server AEM Forms accede al database AEM Forms tramite JDBC. Il database persiste le attività, i processi e le relative istanze, gli utenti e le informazioni correlate.

L&#39;area di lavoro AEM Forms è progettata in componenti JavaScript™ modulari che possono essere personalizzati e riutilizzati individualmente in altre applicazioni web. I componenti sono basati su BackBone, una libreria JavaScript che fornisce struttura alle applicazioni web. Un articolo dettagliato che descrive l&#39;interazione dei componenti con BackBone è [qui](/help/forms/using/backbone-interaction.md). L’organizzazione dei componenti nella struttura di cartelle CRX è discussa in [questo](/help/forms/using/folder-structure.md) articolo.

Pacchetti consegnati per l&#39;area di lavoro AEM Forms:

* `adobe-lc-workspace-pkg-<version>.zip`: È un pacchetto CRX, cioè, può essere distribuito in CRX utilizzando la Gestione pacchetti.
* `adobe-lc-workspace-<version>-src.zip`: Si tratta di un archivio che contiene il codice completo dell&#39;area di lavoro di AEM Forms e gli script per creare i pacchetti di distribuzione, ovvero i pacchetti di spedizione, debug e sviluppo.
