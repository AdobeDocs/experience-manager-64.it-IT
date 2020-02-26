---
title: Base e archivio di AEM
seo-title: Base e archivio di AEM
description: Note sulla versione specifiche di piattaforma e archivio AEM in Adobe Experience Manager 6.3.
seo-description: Note sulla versione specifiche di piattaforma e archivio AEM in Adobe Experience Manager 6.3.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
translation-type: tm+mt
source-git-commit: 966263cc94f44bcad76e7e9ba5c6ecdc93574348

---


# Base e archivio di AEM {#aem-foundation-repository}

## Elenco delle modifiche {#list-of-changes}

### Archivio {#repository}

* MicroKernel segmento Oak

   * Modalità di compattazione rapida (compattazione coda) per la pulizia online delle revisioni
   * Miglioramento delle percentuali di scrittura
   * Stato delle operazioni di segmento esposto tramite JMXBean
   * Stima durata per Pulizia revisione offline

* Oak Mongo Microkernel

   * Pulizia revisioni continue per MongoMK sostituisce la manutenzione programmata

* Miglioramento dell&#39;efficienza per la pulizia delle revisioni negli archivi appunti dei documenti
* Please see [Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) and [Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) for a full overview of fixed issues.

>[!CAUTION]
>
>* La nuova versione di Oak Segment Tar presente a partire da AEM 6.3 richiede una migrazione dell’archivio. Questo passaggio è obbligatorio se stai effettuando l’aggiornamento da una versione precedente di TarMK o vuoi cambiare la nuova scheda Segment Tar da un altro tipo di persistenza. For more information on what the benefits of the new Segment Tar are, see the [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>



### Ricerca e indicizzazione {#search-amp-indexing}

* Supporto migliorato per le operazioni di indicizzazione tramite l&#39;interfaccia CLI (Oak-Run):

   * Controllo coerenza indice
   * Statistiche di indicizzazione
   * Configurazione indice Im/Export
   * Reindicizzazione

* Riduzione della crescita del repository correlata a Lucene per un miglioramento generale delle prestazioni del sistema
* Indici proprietà Lucene sincrone [(ulteriori informazioni)](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Spiega query in Gestione indici supporta ora la sintassi di AEM QueryBuilder
* Index Manager sta esponendo le metriche di indice: dimensioni, ultimo aggiornamento e verifica di coerenza

### Interfaccia utente {#user-interface}

* Sono stati apportati diversi miglioramenti all’interfaccia utente per renderla più produttiva e di facile utilizzo.
* Nuova barra ad albero contenuto per navigare rapidamente in una gerarchia. In combinazione con la vista a elenco, questo ripristina il modello di interazione Interfaccia classica.
* È stato migliorato lo scorrimento nella vista a schede e a elenco delle cartelle di grandi dimensioni.
* Migliorata l&#39;interazione con i risultati della ricerca: il pulsante Indietro ripristina il risultato della ricerca precedente.
* Scelte rapide da tastiera aggiuntive per la maggior parte delle azioni comuni, ad esempio l’apertura di una determinata barra, la modifica, lo spostamento e l’eliminazione di un elemento o l’apertura di proprietà.
* Possibilità di disabilitare le scelte rapide da tastiera (abilitare/disabilitare in Preferenze).
* Interrompi la visualizzazione delle marche temporali in tutte le interfacce utente relative dopo 7 giorni (impostazione predefinita nelle Preferenze).

>[!CAUTION]
>
>* Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica. In AEM 6.4 è già inclusa l’interfaccia utente classica e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a usarla normalmente. Note that Classic UI remains fully supported while being deprecated [Read more](/help/sites-deploying/ui-recommendations.md).
>



### Distribuzione dei contenuti {#content-distribution}

* Sono state migliorate le prestazioni di replica per supportare pubblicazioni di grandi volumi di risorse
* Supporto dell&#39;autenticazione OAuth 2.0 nel trasporto di distribuzione
* Prestazioni migliorate per i pacchetti VLT

### Monitoraggio {#monitoring}

* Una nuova Panoramica del sistema fornisce una visualizzazione istantanea su tutte le attività e lo stato del sistema relativi alle prestazioni
* Nuovi controlli di stato:

   * Rilevamento di indici Lucene di grandi dimensioni
   * Stato indicizzazione asincrona
   * Indici Lucene di grandi dimensioni
   * Prestazioni delle query
   * Limiti di attraversamento per query
   * Orologi sincronizzati
   * Manutenzione del sistema - Pulizia delle revisioni
   * Manutenzione del sistema - DataStore GC
   * Manutenzione del sistema - Revisione continua GC

* Ora l&#39;utente può definire l&#39;ambito del download status.zip

### Manutenzione {#maintenance}

* Eliminazione attiva dei binari Lucene tramite un&#39;attività di manutenzione
* L&#39;attività di manutenzione RevisionGC per MongoDB ora è disabilitata a favore della Pulizia delle revisioni continue. Vedere la sezione Repository precedente.
* La configurazione Version Purge consente di mantenere un numero minimo di versioni
* Version Purge si interrompe alla fine di una finestra di manutenzione. Può anche essere avviata e arrestata manualmente e continuerà in modo incrementale con l&#39;avvio successivo.

### Aggiornamento {#upgrade}

* Compatibilità con le versioni precedenti: Le funzioni retrocompatibili di 6.4 consentono di mantenere il codice personalizzato compatibile nella maggior parte dei casi e riducono lo sforzo di aggiornamento.
* Valutazione della complessità dell&#39;aggiornamento: Nuovo strumento di rilevamento dei pattern per valutare la complessità degli aggiornamenti.
* Aggiornamenti sostenibili: La classificazione delle superfici e dei contenuti delle API è stata introdotta per aiutarti a seguire facilmente le best practice per un aggiornamento efficiente e senza soluzione di continuità alla versione successiva durante tutto il ciclo di sviluppo.
* Ristrutturazione repository: Una ristrutturazione significativa (principalmente /etc) per facilitare gli aggiornamenti e promuovere le migliori pratiche di implementazione. [Ulteriori informazioni.](/help/sites-deploying/repository-restructuring.md)
* Please see the [Upgrade documentation](/help/sites-deploying/upgrade.md) for more details on these features.

### Servizi cloud {#cloud-services}

* Molti servizi Cloud sono ora configurabili tramite interfaccia utente touch; il resto può essere configurato nella scheda Servizi cloud legacy.
* Le cartelle Siti e Risorse possono essere configurate con i Servizi cloud che vengono caricati in base al contesto.

### Sicurezza {#security}

* Interfaccia utente per la creazione di utenti migliorata e semplificata con supporto per più profili utente.
* Sono state migliorate le prestazioni per le appartenenze a gruppi di grandi dimensioni per gli utenti.

### Progetti e flussi di lavoro {#projects-and-workflows}

* Touch UI-based Workflow Editor per gestire i modelli di workflow in modo più semplice.
* Supporto per la rimozione delle attività di progetto nelle attività di manutenzione.

