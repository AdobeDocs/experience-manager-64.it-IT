---
title: Ristrutturazione dell'archivio Forms in AEM 6.4
seo-title: Ristrutturazione dell'archivio Forms in AEM 6.4
description: Scoprite come apportare le modifiche necessarie per eseguire la migrazione alla nuova struttura del repository in AEM 6.4 per Forms.
seo-description: Scoprite come apportare le modifiche necessarie per eseguire la migrazione alla nuova struttura del repository in AEM 6.4 per Forms.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 7%

---


# Ristrutturazione dell&#39;archivio Forms in AEM 6.4{#forms-repository-restructuring-in-aem}

Come descritto nella pagina [Ristrutturazione del repository principale di AEM 6.4](/help/sites-deploying/repository-restructuring.md), i clienti che effettuano l&#39;aggiornamento a AEM 6.4 devono utilizzare questa pagina per valutare lo sforzo di lavoro associato alle modifiche del repository che hanno un impatto sulla soluzione  AEM Forms. Alcune modifiche richiedono sforzi di lavoro durante il processo di aggiornamento di AEM 6.4, mentre altre possono essere posticipate fino a un aggiornamento di 6.5.

**Con aggiornamento 6.4**

* [Misc](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**Aggiornamento precedente a 6.5**

* [Configurazione Cloud Service Echosign](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [Configurazioni Cloud Service Recaptcha](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [Configurazioni Cloud Service Typekit](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [Misc](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## Con aggiornamento 6.4 {#with-upgrade}

### Misc {#misc}

| **Posizione precedente** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Nuove posizioni** | `/libs/fd/fp/components` |
| **Orientamenti per la ristrutturazione** | Eventuali riferimenti espliciti nel codice personalizzato alla posizione Legacy devono essere aggiornati alla nuova posizione. |
| **Note** | Queste librerie client non devono essere modificate o estese. |

| **Posizione precedente** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Nuove posizioni** | `/libs/fd/rte` |
| **Orientamenti per la ristrutturazione** | Per le risorse nelle librerie client cui è possibile fare riferimento in percorsi assoluti, è necessario utilizzare percorsi più recenti per le risorse nuove. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuove posizioni** | `/libs/fd/af/authoring/clientlibs` |
| **Orientamenti per la ristrutturazione** | Per le risorse nelle librerie client cui è possibile fare riferimento in percorsi assoluti, è necessario utilizzare percorsi più recenti per le risorse nuove. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Nuove posizioni** | `/libs/fd/xfaforms/clientlibs/` |
| **Orientamenti per la ristrutturazione** | Per le risorse nelle librerie client cui è possibile fare riferimento in percorsi assoluti, è necessario utilizzare percorsi più recenti per le risorse nuove. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuove posizioni** | `/libs/fd/af/runtime/clientlibs` |
| **Orientamenti per la ristrutturazione** | Per le risorse nelle librerie client cui è possibile fare riferimento in percorsi assoluti, è necessario utilizzare percorsi più recenti per le risorse nuove. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuove posizioni** | `/libs/fd/af/runtime/clientlibs` |
| **Orientamenti per la ristrutturazione** | Per le risorse nelle librerie client cui è possibile fare riferimento in percorsi assoluti, è necessario utilizzare percorsi più recenti per le risorse nuove. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Nuove posizioni** | `/libs/fd/expeditor/clientlibs` |
| **Orientamenti per la ristrutturazione** | Per le risorse nelle librerie client cui è possibile fare riferimento in percorsi assoluti, è necessario utilizzare percorsi più recenti per le risorse nuove. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Nuove posizioni** | `/libs/fd/fmaddon` |
| **Orientamenti per la ristrutturazione** | La modifica di questi clientlibs non è mai stata consigliata o supportata. Se sono state apportate modifiche a questi clientlibs, è necessario ripristinarli per utilizzare il codice AEM fornito. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/aep` |
|---|---|
| **Nuove posizioni** | `/var/fd/content/annotations` |
| **Orientamenti per la ristrutturazione** | La modifica di questi clientlibs non è mai stata consigliata o supportata. Se sono state apportate modifiche a questi clientlibs, è necessario ripristinarli per utilizzare il codice AEM fornito. |
| **Note** | N/D |

## Aggiornamento precedente a 6.5 {#prior-to-upgrade}

### Configurazione Cloud Service Echosign {#echosign-cloud-service-configuration}

| **Posizione precedente** | `/etc/cloudservices/echosign` |
|---|---|
| **Nuove posizioni** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Orientamenti per la ristrutturazione** | L&#39;utility [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) da attivare dall&#39;interfaccia utente di migrazione di Forms. |
| **Note** | N/D |

### Configurazioni di Cloud Service Recaptcha {#recaptcha-cloud-service-configurations}

| **Posizione precedente** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Nuove posizioni** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Orientamenti per la ristrutturazione** | L&#39;utility [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) da attivare dall&#39;interfaccia utente di migrazione di Forms. |
| **Note** | N/D |

### Configurazioni Cloud Service Typekit {#typekit-cloud-service-configurations}

| **Posizione precedente** | `/etc/cloudservices/typekit` |
|---|---|
| **Nuove posizioni** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Orientamenti per la ristrutturazione** | L&#39;utility [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) da attivare dall&#39;interfaccia utente di migrazione di Forms. |
| **Note** | N/D |

### Misc {#misc-1}

| **Posizione precedente** | `/etc/cloudservices/fdm` |
|---|---|
| **Nuove posizioni** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Orientamenti per la ristrutturazione** | L&#39;utility [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) da attivare dall&#39;interfaccia utente di migrazione di Forms. |
| **Note** | N/D |

| **Posizione precedente** | `/etc/designs/fd/fp` |
|---|---|
| **Nuove posizioni** | `/libs/fd/fp` |
| **Orientamenti per la ristrutturazione** | Eventuali riferimenti ai modelli /etc dovrebbero essere aggiornati in modo da indicare le controparti `/libs`. |
| **Note** | N/D |

