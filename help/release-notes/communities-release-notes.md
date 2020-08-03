---
title: Note sulla versione di AEM Communities
seo-title: AEM Communities
description: Note sulla versione relative ad Adobe Experience Manager 6.4 Communities.
seo-description: Note sulla versione relative ad Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 12%

---


# AEM Communities Note sulla versione {#aem-communities-release-notes}

Questa sezione fornisce informazioni sui miglioramenti apportati agli AEM Communities a partire dalla versione 6.3. Per ulteriori informazioni sulle nuove funzioni, consulta [Novità di AEM 6.4 Communities](/help/communities/whats-new-aem-communities.md).

To obtain the latest release, see the [Deploying Communities](/help/communities/deploy-communities.md#latest-releases) section of the documentation.

## Miglioramenti principali {#main-improvements}

Siti community:

* Gli amministratori della community ora possono:

   * Elimina siti community in modo permanente
   * Selezionate una cartella di configurazione in base al contesto per Siti community

Gruppi community:

* Gli amministratori della community ora possono:

   * Elimina gruppi community permanenti
   * Creazione di gruppi di community in più lingue
   * Aggiungi catalogo di abilitazione e assegnazioni in Gruppi community

* I manager di abilitazione possono

   * Creazione e assegnazione di risorse e percorsi di apprendimento all&#39;interno dei gruppi community

Libreria file:

* I membri della community ora dispongono di diversi miglioramenti nella libreria dei file, ad esempio ordini di ordinamento, tag...

Notifiche:

* I membri della community ricevono ora notifiche previa approvazione dei contributi che hanno avuto luogo durante un processo di moderazione

Moderazione:

* Filtro di rilevamento automatico dello spam
* I moderatori della community dispongono di filtri Moderazione aggiuntivi (ad esempio, domande con risposta/senza risposta)
* I moderatori della community possono creare segnalibri e collegare la moderazione a filtri predefiniti (ad esempio, tutti i post in attesa di approvazione)

Compatibilità generale con le modifiche fondamentali di AEM 6.4.

Nota: tutte queste funzioni sono disponibili anche per AEM 6.3. Controlla le note di rilascio dei AEM Communities per [6.3](https://helpx.adobe.com/it/experience-manager/6-3/release-notes.html).

## Problemi noti {#known-issues}

* **Moderazione** - Impossibile eliminare il post principale come singola operazione di eliminazione dall&#39;interfaccia utente di moderazione in blocco (CQ-4236797)
* **Console** - Il collegamento Password o Nome utente dimenticato viene reindirizzato alla pagina di accesso invece del modulo di recupero password corrispondente (CQ-4237682)

## Seleziona funzioni {#select-features}

Il punteggio di esperti (*fornito da Sensei*) è utilizzato per abilitare la gamificazione, che è un modo efficace per incoraggiare e premiare comportamenti comunitari di valore. Può essere utilizzato anche per identificare esperti a scopo di raccomandazione o marketing.

## Manifestazioni {#demonstrations}

Tutte queste funzioni possono essere dimostrate utilizzando la [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponibile pubblicamente su GitHub.com quando si utilizza lo scenario demo AEM Communities e anche all&#39;interno della nuova implementazione di riferimento We.Retail.
