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
translation-type: tm+mt
source-git-commit: 0dced2f56fcebfb03fa6264e98cd686e8e7902c6
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 1%

---


# Rimozione delle versioni{#version-purging}

In un’installazione standard AEM crea una nuova versione di una pagina o di un nodo quando si attiva una pagina dopo l’aggiornamento del contenuto.

>[!NOTE]
>
>Se non viene apportata alcuna modifica al contenuto, verrà visualizzato il messaggio che indica che la pagina è stata attivata, ma non verrà creata alcuna nuova versione

Potete creare versioni aggiuntive su richiesta utilizzando la scheda **Gestione versioni** della barra laterale. Queste versioni sono memorizzate nella directory archivio e possono essere ripristinate se necessario.

Queste versioni non vengono mai eliminate, pertanto la dimensione del repository aumenterà nel tempo e dovrà essere gestita.

AEM viene fornito con diversi metodi per gestire il repository:

* Gestione [versioni](#version-manager)

   Questa opzione può essere configurata per eliminare le versioni precedenti al momento della creazione di nuove versioni.

* lo strumento [Rimuovi versioni](/help/sites-deploying/monitoring-and-maintaining.md#version-purging)

   Questa funzione è utilizzata per monitorare e mantenere l&#39;archivio.

   Consente di intervenire per rimuovere versioni precedenti di un nodo, o una gerarchia di nodi, in base ai seguenti parametri:

   * Il numero massimo di versioni da conservare nella directory archivio.

      Quando questo numero viene superato, viene rimossa la versione più vecchia.

   * Età massima di qualsiasi versione conservata nella directory archivio.

      Quando l’età di una versione supera tale valore, viene eliminata dalla directory archivio.

* l&#39;attività [di manutenzione](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks)Version Purge. È possibile pianificare l&#39;attività di manutenzione di Rimozione versioni per eliminare automaticamente le versioni precedenti. Questo riduce al minimo la necessità di utilizzare manualmente gli strumenti di rimozione della versione.

>[!CAUTION]
>
>Per ottimizzare le dimensioni del repository è necessario eseguire frequentemente l&#39;attività di eliminazione delle versioni. L&#39;attività deve essere programmata al di fuori degli orari di lavoro quando il traffico è limitato.

## Version Manager {#version-manager}

Oltre all&#39;eliminazione esplicita tramite lo strumento di eliminazione, Version Manager può essere configurato per eliminare le versioni precedenti quando vengono create nuove versioni.

Per configurare Gestione versioni, crea una configurazione per:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Sono disponibili le seguenti opzioni:

* `versionmanager.createVersionOnActivation` (Booleano, predefinito: true)

   se creare una versione quando le pagine vengono attivate.

   Viene creata una versione a meno che l&#39;agente di replica non sia configurato per eliminare la creazione di versioni, che viene rispettata da Version Manager

   Una versione viene creata solo se l&#39;attivazione viene eseguita su un percorso contenuto in versionmanager.ivPaths (vedere di seguito).

* `versionmanager.ivPaths` (String[], predefinito: {&quot;/&quot;})

   percorsi in cui le versioni vengono implicitamente create all&#39;attivazione se versionmanager.createVersionOnActivation è true.

* `versionmanager.purgingEnabled` (Booleano, predefinito: false)

   se abilitare l&#39;eliminazione al momento della creazione delle nuove versioni

* `versionmanager.purgePaths` (String[], predefinito: {&quot;/content&quot;})

   su quali percorsi rimuovere le versioni quando vengono create nuove versioni.

* `versionmanager.maxAgeDays` (int, predefinito: 30)

   durante la rimozione, tutte le versioni precedenti a questo valore verranno rimosse. Se questo valore è minore di 1, la rimozione non viene eseguita in base all&#39;età della versione

* `versionmanager.maxNumberVersions` (int, predefinito 5)

   durante la rimozione, tutte le versioni precedenti all’ultima versione verranno rimosse. Se questo valore è minore di 1, la rimozione non viene eseguita in base al numero di versioni

* `versionmanager.minNumberVersions` (int, predefinito 0)

   Il numero minimo di versioni da mantenere indipendentemente dall&#39;età. Se questo valore è impostato su un valore inferiore a 1, non viene mantenuto alcun numero minimo di versioni.

>[!NOTE]
>
>Non è consigliabile mantenere un numero elevato di versioni nella directory archivio. Pertanto, durante la configurazione dell&#39;operazione di eliminazione della versione, non escludere troppe versioni dalla rimozione, altrimenti la dimensione del repository non verrà ottimizzata correttamente. Se disponete di un numero elevato di versioni a causa di un requisito aziendale, contattate il supporto Adobe per trovare modi alternativi per ottimizzare le dimensioni del repository.

### Combinazione di opzioni di conservazione {#combining-retention-options}

Le opzioni che definiscono il modo in cui le versioni devono essere mantenute ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), possono essere combinate a seconda delle esigenze.

Ad esempio, quando si definisce il numero massimo di versioni da mantenere E la versione più vecchia da mantenere:

* Impostazione:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* Con:

   * 10 versioni realizzate negli ultimi 60 giorni
   * 3 di tali versioni create negli ultimi 30 giorni

* Significa che:

   * Le ultime 3 versioni verranno mantenute

Ad esempio, quando si definisce il numero massimo E minimo di versioni da mantenere E la versione più vecchia da mantenere:

* Impostazione:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Con:

   * 5 versioni realizzate 60 giorni fa

* Significa che:

   * Verranno mantenute 3 versioni

## Strumento Svuota versioni {#purge-versions-tool}

Lo strumento Versioni [di](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) eliminazione è destinato a eliminare le versioni di un nodo o di una gerarchia di nodi nel repository. Lo scopo principale è quello di ridurre le dimensioni del repository rimuovendo le versioni precedenti dei nodi.
