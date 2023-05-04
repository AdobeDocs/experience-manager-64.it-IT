---
title: Risoluzione di problemi AEM nell’ambiente di authoring
seo-title: Troubleshooting AEM when Authoring
description: Alcuni problemi che potrebbero verificarsi durante l'utilizzo di AEM
seo-description: Some issues that you might encounter when using AEM
uuid: 99af51ea-8628-4811-83f2-ab3f88f0279e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: da0a5644-2e1d-4394-a6aa-11bb41406ba6
exl-id: b0890070-c9e8-4ce4-9149-00c8c38298ce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 45%

---

# Risoluzione di problemi AEM nell’ambiente di authoring {#troubleshooting-aem-when-authoring}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Nella seguente sezione vengono descritti alcuni problemi che potresti riscontrare durante l’utilizzo di AEM e vengono proposte possibili soluzioni.

>[!NOTE]
>
>Quando si verificano problemi, è anche utile controllare l&#39;elenco di [Problemi noti](/help/release-notes/known-issues.md) per la tua istanza (release e service pack).

>[!NOTE]
>
>Gli utenti con privilegi di amministratore possono utilizzare i metodi di risoluzione dei problemi descritti in [AEM per la risoluzione dei problemi (per gli amministratori)](/help/sites-administering/troubleshoot.md). Se non disponi di privilegi sufficienti, rivolgiti all’amministratore di sistema per informazioni sulla risoluzione dei AEM.

## La vecchia versione della pagina è ancora nel sito pubblicato {#old-page-version-still-on-published-site}

* **Problema**:

   * Hai apportato modifiche a una pagina e l&#39;hai replicata sul sito pubblicato, ma la *vecchio* sul sito di pubblicazione viene ancora visualizzata la versione della pagina.

* **Motivo**:

   * Questo può avere diverse cause, più spesso la cache (sia il browser locale che il Dispatcher), anche se a volte può essere un problema con la coda di replica.

* **Soluzioni**:

   * Ci sono diverse possibilità qui:
   * Verifica che la pagina sia stata replicata correttamente. Controlla lo stato della pagina e, se necessario, lo stato della coda di replica.
   * Cancella la cache del browser locale e accedi di nuovo alla pagina.
   * Aggiungi `?` alla fine dell’URL della pagina, ad esempio:

      * `http://localhost:4502/sites.html/content?`
      * In questo modo la pagina viene richiesta direttamente da AEM senza passare dal Dispatcher. Se viene visualizzata la pagina aggiornata, significa che è necessario cancellare la cache del Dispatcher.
   * In caso di problemi relativi alla coda di replica, rivolgiti all’amministratore di sistema.


## Azioni per componenti non visibili sulla barra degli strumenti {#component-actions-not-visible-on-toolbar}

* **Problema**:

   * Non tutte le azioni disponibili per i componenti sono visibili quando si modifica il contenuto di una pagina nell’ambiente di authoring.

* **Motivo**:

   * In rari casi, un’azione precedente potrebbe influenzare la barra degli strumenti.

* **Soluzione**:

   * Aggiorna la pagina.
