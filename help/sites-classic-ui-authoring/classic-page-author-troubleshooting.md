---
title: Risoluzione di problemi AEM nell’ambiente di authoring
seo-title: Troubleshooting AEM when Authoring
description: Nella seguente sezione vengono descritti alcuni problemi che potresti riscontrare durante l’utilizzo di AEM e vengono proposte possibili soluzioni.
seo-description: The following section covers some issues that you might encounter when using AEM, together with suggestions on how to troubleshoot them.
uuid: eb95e5ba-1eed-4ffb-80c1-9b8468820c22
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 9b492b17-9029-46ae-9dc0-bb21e6b484df
exl-id: 09409631-c579-4b1f-9193-1348896f6a09
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 32%

---

# Risoluzione di problemi AEM nell’ambiente di authoring{#troubleshooting-aem-when-authoring}

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

      `http://localhost:4502/sites.html/content?`

      In questo modo la pagina viene richiesta direttamente da AEM senza passare dal Dispatcher. Se viene visualizzata la pagina aggiornata, significa che è necessario cancellare la cache del Dispatcher.

   * In caso di problemi relativi alla coda di replica, rivolgiti all’amministratore di sistema.

## Barra laterale non visibile {#sidekick-not-visible}

* **Problema**:

   * La barra laterale non è visibile quando si modifica un contenuto di una pagina nell’ambiente di authoring.

* **Motivo**:

   * In rari casi è possibile che l’intestazione della barra laterale sia stata posizionata al di fuori dell’ambito della finestra corrente. Ciò significa che non è possibile riposizionarlo.

* **Soluzione**:

   * Disconnettiti dalla sessione corrente e accedi di nuovo. La barra laterale torna nella posizione predefinita.

## Trova e sostituisci - Non vengono sostituite tutte le istanze {#find-replace-not-all-instances-are-replaced}

* **Problema:**

   * Quando utilizzi **Trova e sostituisci** può accadere che non tutte le istanze del `find` i termini vengono sostituiti in una pagina.

* **Motivo**:

   * La capacità di **Trova e sostituisci** dipende da come è stato salvato il contenuto e se è possibile eseguire ricerche in esso contenute. Ad esempio, il testo di un blog viene memorizzato in `jcr:text` proprietà non configurata per la ricerca. L’ambito predefinito del servlet di ricerca e sostituzione include le seguenti proprietà:

      * `jcr:title`
      * `jcr:description`
      * `jcr:text`
      * `text`

* **Soluzione**:

   * Queste definizioni possono essere modificate con la configurazione di **Day CQ WCM Find Replace Servlet** utilizzando **Console web**; ad esempio, in

      `http://localhost:4502/system/console/configMgr`
