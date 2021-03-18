---
title: Rimozione delle versioni
seo-title: Rimozione delle versioni
description: Questo articolo descrive le opzioni disponibili per l'eliminazione delle versioni.
seo-description: Questo articolo descrive le opzioni disponibili per l'eliminazione delle versioni.
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
feature: Configurazione
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 2%

---


# Rimozione della versione{#version-purging}

In un’installazione standard AEM crea una nuova versione di una pagina o di un nodo quando attivi una pagina dopo l’aggiornamento del contenuto.

>[!NOTE]
>
>Se non viene apportata alcuna modifica al contenuto, verrà visualizzato il messaggio che indica che la pagina è stata attivata, ma non verrà creata alcuna nuova versione

Puoi creare versioni aggiuntive su richiesta utilizzando la scheda **Gestione versioni** della barra laterale. Queste versioni sono memorizzate nell’archivio e possono essere ripristinate se necessario.

Queste versioni non vengono mai eliminate, pertanto la dimensione dell’archivio aumenterà nel tempo e deve quindi essere gestita.

AEM viene fornito con vari meccanismi per aiutarti a gestire il tuo archivio:

* [Version Manager](#version-manager)

   Questa può essere configurata per eliminare le versioni precedenti quando vengono create nuove versioni.

* lo strumento [Elimina versioni](/help/sites-deploying/monitoring-and-maintaining.md#version-purging)

   Viene utilizzato come parte del monitoraggio e della manutenzione dell’archivio.

   Ti consente di intervenire per rimuovere le vecchie versioni di un nodo, o una gerarchia di nodi, in base a questi parametri:

   * Il numero massimo di versioni da conservare nell’archivio.

      Quando questo numero viene superato, la versione più vecchia viene rimossa.

   * L’età massima di qualsiasi versione conservata nell’archivio.

      Quando l’età di una versione supera questo valore, viene eliminata dall’archivio.

* l&#39;attività [Version Purge Maintenance](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). È possibile pianificare l&#39;attività di manutenzione Pulizia versione per eliminare automaticamente le versioni precedenti. Di conseguenza, questo riduce al minimo la necessità di utilizzare manualmente gli strumenti di eliminazione delle versioni.

>[!CAUTION]
>
>Per ottimizzare le dimensioni del repository, è necessario eseguire frequentemente l&#39;attività di eliminazione della versione. L&#39;attività deve essere pianificata al di fuori dell&#39;orario di lavoro quando vi è una quantità limitata di traffico.

## Version Manager {#version-manager}

Oltre all&#39;eliminazione esplicita tramite lo strumento di eliminazione, Version Manager può essere configurato per eliminare le versioni precedenti quando vengono create nuove versioni.

Per configurare Version Manager, crea una configurazione per:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Sono disponibili le seguenti opzioni:

* `versionmanager.createVersionOnActivation` (Booleano, predefinito: true)

   se creare una versione quando le pagine vengono attivate.

   Viene creata una versione a meno che l’agente di replica non sia configurato per eliminare la creazione di versioni, in conformità con Version Manager

   Viene creata una versione solo se l’attivazione si verifica su un percorso contenuto in versionmanager.ivPaths (vedi sotto).

* `versionmanager.ivPaths` (Stringa[], predefinito: {&quot;/&quot;})

   percorsi in cui vengono implicitamente create versioni all&#39;attivazione se versionmanager.createVersionOnActivation è true.

* `versionmanager.purgingEnabled` (Booleano, predefinito: false)

   se abilitare l&#39;eliminazione quando vengono create nuove versioni

* `versionmanager.purgePaths` (Stringa[], predefinito: {&quot;/content&quot;})

   su quali percorsi eliminare le versioni quando vengono create nuove versioni.

* `versionmanager.maxAgeDays` (int, predefinito: 30)

   durante l’eliminazione, verranno rimosse tutte le versioni precedenti a questo valore. Se questo valore è inferiore a 1, la rimozione non viene eseguita in base all&#39;età della versione

* `versionmanager.maxNumberVersions` (int, predefinito 5)

   durante l’eliminazione, verranno rimosse tutte le versioni precedenti all’ultima versione. Se questo valore è inferiore a 1, la rimozione non viene eseguita in base al numero di versioni

* `versionmanager.minNumberVersions` (int, predefinito 0)

   Il numero minimo di versioni da mantenere indipendentemente dalla pagina. Se questo valore è impostato su un valore inferiore a 1, non viene mantenuto un numero minimo di versioni.

>[!NOTE]
>
>Si sconsiglia di mantenere un numero elevato di versioni nell’archivio. Quindi, quando configuri l&#39;operazione di eliminazione della versione, fai attenzione a non escludere troppe versioni dalla rimozione, altrimenti la dimensione dell&#39;archivio non verrà ottimizzata correttamente. Se mantieni un numero elevato di versioni a causa di un requisito aziendale, contatta il supporto Adobe per trovare modi alternativi per ottimizzare le dimensioni dell’archivio.

### Combinazione delle opzioni di conservazione {#combining-retention-options}

Le opzioni che definiscono come mantenere le versioni ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`) possono essere combinate in base alle tue esigenze.

Ad esempio, quando definisci il numero massimo di versioni da mantenere E la versione più vecchia da mantenere:

* Impostazione:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* Con:

   * 10 versioni effettuate negli ultimi 60 giorni
   * 3 di queste versioni create negli ultimi 30 giorni

* Ciò significa che:

   * Verranno mantenute le ultime 3 versioni

Ad esempio, quando definisci il numero massimo E minimo di versioni da mantenere e la versione più vecchia da mantenere:

* Impostazione:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Con:

   * 5 versioni realizzate 60 giorni fa

* Ciò significa che:

   * Verranno mantenute 3 versioni

## Strumento Elimina versioni {#purge-versions-tool}

Lo strumento [Purge Versions](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) è destinato a eliminare le versioni di un nodo o di una gerarchia di nodi nel tuo archivio. Il suo scopo principale è quello di aiutarti a ridurre le dimensioni dell’archivio rimuovendo le vecchie versioni dei nodi.
