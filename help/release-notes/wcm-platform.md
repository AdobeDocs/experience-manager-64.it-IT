---
title: AEM Foundation e Repository
seo-title: AEM Foundation & Repository
description: Note sulla versione specifiche di Adobe Experience Manager 6.3 AEM Platform e Repository.
seo-description: Release notes specific to Adobe Experience Manager 6.3 AEM Platform and Repository.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 3%

---

# AEM Foundation e Repository {#aem-foundation-repository}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Elenco delle modifiche {#list-of-changes}

### Archivio {#repository}

* MicroKernel segmento Oak

   * Modalità di compattazione rapida (compattazione tail) per Pulizia revisioni online
   * Percentuali di scrittura migliorate
   * Statistiche delle operazioni del segmento esposte tramite JMXBean
   * Stima della durata per il cleanup delle revisioni offline

* Oak Mongo Microkernel

   * Pulizia revisioni continua per MongoMK sostituisce la manutenzione programmata

* Miglioramento dell&#39;efficienza del cleanup delle revisioni negli archivi dei nodi dei documenti
* Vedi [Apache Jackrabbit Oak Jira v 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) e [Apache Jackrabbit Oak Jira v 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) per una panoramica completa dei problemi risolti.

>[!CAUTION]
>
>* La nuova versione di Oak Segment Tar presente a partire da AEM 6.3 richiede una migrazione dell&#39;archivio. Questo passaggio è obbligatorio se effettui l’aggiornamento da una versione precedente di TarMK o desideri cambiare il nuovo Segment Tar da un altro tipo di persistenza. Per ulteriori informazioni sui vantaggi del nuovo Segment Tar, consulta la sezione [Domande frequenti sulla migrazione a Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>


### Ricerca e indicizzazione {#search-amp-indexing}

* Supporto migliorato per le operazioni di indicizzazione tramite oak-run (CLI):

   * Controllo della coerenza dell&#39;indice
   * Statistiche di indicizzazione
   * Configurazione indice Im/Export
   * Reindicizzazione

* Riduzione della crescita dell&#39;archivio correlata a Lucene per un miglioramento generale delle prestazioni del sistema
* Indici delle proprietà Lucene sincroni [(Ulteriori informazioni)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Explain Query in Index Manager supporta ora AEM sintassi QueryBuilder
* Index Manager sta esponendo le metriche dell&#39;indice: dimensioni, ultimo aggiornamento e controllo di coerenza

### Interfaccia utente {#user-interface}

* Sono stati apportati diversi miglioramenti all’interfaccia utente per renderla più produttiva e facile da usare.
* Nuova barra Struttura contenuto per navigare rapidamente in una gerarchia. In combinazione con la vista a elenco, viene ripristinato il modello di interazione con l’interfaccia classica.
* È stato migliorato lo scorrimento nella vista a schede e a elenco delle cartelle di grandi dimensioni.
* È stata migliorata l’interazione con i risultati della ricerca: il pulsante Indietro ripristina il risultato della ricerca precedente.
* Scelte rapide da tastiera aggiuntive per le azioni più comuni, ad esempio per aprire una particolare barra, modificare, spostare ed eliminare un elemento o per aprire le proprietà.
* Possibilità di disattivare le scelte rapide da tastiera (attiva/disattiva in Preferenze).
* Interrompi la visualizzazione di marche temporali in tutta l’interfaccia utente relative dopo 7 giorni (impostazione predefinita in Preferenze).

>[!CAUTION]
>
>* Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica. AEM 6.4 include l’interfaccia classica e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a utilizzarla così com’è. L’interfaccia classica rimane completamente supportata anche se obsoleta [Leggi tutto](/help/sites-deploying/ui-recommendations.md).
>


### Distribuzione dei contenuti {#content-distribution}

* Prestazioni di replica migliorate per supportare pubblicazioni di risorse di grandi volumi
* Supporto dell’autenticazione OAuth 2.0 nel trasporto di distribuzione
* Prestazioni migliorate per i pacchetti VLT

### Monitoraggio {#monitoring}

* Una nuova panoramica del sistema fornisce una visualizzazione istantanea dello stato e delle attività del sistema relative alle prestazioni
* Nuovi controlli di stato:

   * Rileva indici Lucene di grandi dimensioni
   * Stato dell&#39;indicizzazione asincrona
   * Indici Lucene di grandi dimensioni
   * Prestazioni delle query
   * Limiti di attraversamento per query
   * Orologi sincronizzati
   * Manutenzione del sistema - Pulizia delle revisioni
   * Manutenzione del sistema - GC DataStore
   * Manutenzione del sistema - Revisione continua GC

* L&#39;utente può ora definire l&#39;ambito del download status.zip

### Manutenzione {#maintenance}

* Eliminazione attiva dei binari Lucene tramite un&#39;attività di manutenzione
* L&#39;attività di manutenzione RevisionGC per MongoDB è ora disabilitata a favore del cleanup delle revisioni continue, consulta la sezione Repository di cui sopra.
* La configurazione di eliminazione della versione consente di mantenere un numero minimo di versioni
* Version Purge si arresta alla fine di una finestra di manutenzione. Può anche essere avviato e arrestato manualmente e continuerà in modo incrementale con l&#39;avvio successivo.

### Aggiornamento {#upgrade}

* Compatibilità con le versioni precedenti: Le funzioni retrocompatibili della versione 6.4 consentono di mantenere il codice personalizzato compatibile nella maggior parte dei casi e riducono lo sforzo di aggiornamento.
* Valutazione della complessità dell’aggiornamento: Nuovo strumento di rilevamento pattern per valutare la complessità degli aggiornamenti.
* Aggiornamenti sostenibili: La classificazione delle superfici e dei contenuti delle API è stata introdotta per aiutarti a seguire facilmente le best practice per un aggiornamento efficiente e senza soluzione di continuità alla versione successiva durante tutto il ciclo di sviluppo.
* Ristrutturazione archivio: Una ristrutturazione significativa (principalmente /etc) per facilitare gli aggiornamenti e promuovere le best practice di implementazione. [Ulteriori informazioni.](/help/sites-deploying/repository-restructuring.md)
* Vedi la [Documentazione di aggiornamento](/help/sites-deploying/upgrade.md) per ulteriori informazioni su queste funzioni.

### Servizi cloud {#cloud-services}

* Molti Cloud Services sono ora configurabili tramite l’interfaccia utente touch; il resto può essere configurato sotto la scheda Cloud Services legacy.
* Le cartelle Sites e Assets possono essere configurate con Cloud Services caricati in modo contestuale.

### Sicurezza {#security}

* Interfaccia utente migliorata e semplificata per la creazione di utenti con supporto per più profili utente.
* Prestazioni migliorate per le appartenenze a gruppi di grandi dimensioni per gli utenti.

### Progetti e flussi di lavoro {#projects-and-workflows}

* L’editor di flussi di lavoro basato sull’interfaccia utente touch consente di gestire i modelli di flussi di lavoro in modo più semplice.
* Supporto per l&#39;eliminazione delle attività del progetto nelle attività di manutenzione.
