---
title: Ristrutturazione dell’archivio Forms in AEM 6.4
seo-title: Forms Repository Restructuring in AEM 6.4
description: Scopri come apportare le modifiche necessarie per migrare alla nuova struttura dell’archivio in AEM 6.4 per Forms.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Forms.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
feature: Upgrading
exl-id: a2d6524e-3f5b-4d1e-af64-61ff95889657
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 8%

---

# Ristrutturazione dell’archivio Forms in AEM 6.4{#forms-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Come descritto nell&#39;elemento padre [Ristrutturazione dell’archivio in AEM 6.4](/help/sites-deploying/repository-restructuring.md) I clienti che eseguono l’aggiornamento a AEM 6.4 devono utilizzare questa pagina per valutare lo sforzo di lavoro associato alle modifiche dell’archivio che influiscono sulla soluzione AEM Forms. Alcune modifiche richiedono un lavoro durante il processo di aggiornamento di AEM 6.4, mentre altre possono essere differite fino a un aggiornamento 6.5.

**Con aggiornamento alla versione 6.4**

* [Varie](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**Prima dell’aggiornamento alla versione 6.5**

* [Configurazione Cloud Service Echosign](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [Configurazioni del Cloud Service Recaptcha](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [Configurazioni del Cloud Service Typekit](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [Varie](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## Con aggiornamento alla versione 6.4 {#with-upgrade}

### Varie {#misc}

| **Posizione precedente** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Nuove posizioni** | `/libs/fd/fp/components` |
| **Orientamento alla ristrutturazione** | Eventuali riferimenti espliciti nel codice personalizzato alla posizione legacy devono essere aggiornati nella nuova posizione. |
| **Note** | Queste librerie client non devono essere modificate o estese. |

| **Posizione precedente** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Nuove posizioni** | `/libs/fd/rte` |
| **Orientamento alla ristrutturazione** | Per le risorse nelle librerie client a cui è possibile fare riferimento tramite percorsi assoluti, è necessario utilizzare percorsi più recenti nelle nuove risorse. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuove posizioni** | `/libs/fd/af/authoring/clientlibs` |
| **Orientamento alla ristrutturazione** | Per le risorse nelle librerie client a cui è possibile fare riferimento tramite percorsi assoluti, è necessario utilizzare percorsi più recenti nelle nuove risorse. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Nuove posizioni** | `/libs/fd/xfaforms/clientlibs/` |
| **Orientamento alla ristrutturazione** | Per le risorse nelle librerie client a cui è possibile fare riferimento tramite percorsi assoluti, è necessario utilizzare percorsi più recenti nelle nuove risorse. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuove posizioni** | `/libs/fd/af/runtime/clientlibs` |
| **Orientamento alla ristrutturazione** | Per le risorse nelle librerie client a cui è possibile fare riferimento tramite percorsi assoluti, è necessario utilizzare percorsi più recenti nelle nuove risorse. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuove posizioni** | `/libs/fd/af/runtime/clientlibs` |
| **Orientamento alla ristrutturazione** | Per le risorse nelle librerie client a cui è possibile fare riferimento tramite percorsi assoluti, è necessario utilizzare percorsi più recenti nelle nuove risorse. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Nuove posizioni** | `/libs/fd/expeditor/clientlibs` |
| **Orientamento alla ristrutturazione** | Per le risorse nelle librerie client a cui è possibile fare riferimento tramite percorsi assoluti, è necessario utilizzare percorsi più recenti nelle nuove risorse. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Nuove posizioni** | `/libs/fd/fmaddon` |
| **Orientamento alla ristrutturazione** | La modifica di queste clientlib non è mai stata consigliata o supportata. Se sono state apportate modifiche a queste clientlibs, è necessario eseguirne il rollback per utilizzare il codice fornito da AEM. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/aep` |
|---|---|
| **Nuove posizioni** | `/var/fd/content/annotations` |
| **Orientamento alla ristrutturazione** | La modifica di queste clientlib non è mai stata consigliata o supportata. Se sono state apportate modifiche a queste clientlibs, è necessario eseguirne il rollback per utilizzare il codice fornito da AEM. |
| **Note** | N/D |

## Prima dell’aggiornamento alla versione 6.5 {#prior-to-upgrade}

### Configurazione Cloud Service Echosign {#echosign-cloud-service-configuration}

| **Posizione precedente** | `/etc/cloudservices/echosign` |
|---|---|
| **Nuove posizioni** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Orientamento alla ristrutturazione** | La [Migrazione dei contenuti Lazy](/help/sites-deploying/lazy-content-migration.md) Utility da attivare dall’interfaccia utente di migrazione di Forms. |
| **Note** | N/D |

### Configurazioni del Cloud Service Recaptcha {#recaptcha-cloud-service-configurations}

| **Posizione precedente** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Nuove posizioni** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Orientamento alla ristrutturazione** | La [Migrazione dei contenuti Lazy](/help/sites-deploying/lazy-content-migration.md) Utility da attivare dall’interfaccia utente di migrazione di Forms. |
| **Note** | N/D |

### Configurazioni del Cloud Service Typekit {#typekit-cloud-service-configurations}

| **Posizione precedente** | `/etc/cloudservices/typekit` |
|---|---|
| **Nuove posizioni** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Orientamento alla ristrutturazione** | La [Migrazione dei contenuti Lazy](/help/sites-deploying/lazy-content-migration.md) Utility da attivare dall’interfaccia utente di migrazione di Forms. |
| **Note** | N/D |

### Varie {#misc-1}

| **Posizione precedente** | `/etc/cloudservices/fdm` |
|---|---|
| **Nuove posizioni** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Orientamento alla ristrutturazione** | La [Migrazione dei contenuti Lazy](/help/sites-deploying/lazy-content-migration.md) Utility da attivare dall’interfaccia utente di migrazione di Forms. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/designs/fd/fp` |
|---|---|
| **Nuove posizioni** | `/libs/fd/fp` |
| **Orientamento alla ristrutturazione** | Eventuali riferimenti ai modelli /etc devono essere aggiornati in modo che puntino al loro `/libs` controparti. |
| **Note** | N/D |
