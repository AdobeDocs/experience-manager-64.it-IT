---
title: Note sulla versione di AEM Communities
seo-title: AEM Communities
description: Note sulla versione specifiche di Adobe Experience Manager 6.4 Communities.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
exl-id: 3a341e72-01c5-4c63-8942-6320e5b08440
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 6%

---

# Note sulla versione di AEM Communities {#aem-communities-release-notes}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa sezione fornisce informazioni sui miglioramenti apportati ad AEM Communities a partire dalla versione 6.3. Per ulteriori informazioni sulle nuove funzioni, consulta [Novità di AEM 6.4 Communities](/help/communities/whats-new-aem-communities.md).

Per ottenere la versione più recente, vedi [Distribuzione di Communities](/help/communities/deploy-communities.md#latest-releases) sezione della documentazione.

## Miglioramenti principali {#main-improvements}

Siti community:

* Gli amministratori della community possono ora:

   * Elimina siti della community definitivamente
   * Selezionare una cartella di configurazione in base al contesto per Siti della community

Gruppi community:

* Gli amministratori della community possono ora:

   * Elimina gruppi community permanenti
   * Creare gruppi di community in più lingue
   * Aggiungi catalogo di abilitazione e assegnazioni all&#39;interno dei gruppi della community

* Ora i manager di abilitazione possono

   * Creare e assegnare risorse e percorsi di apprendimento all’interno dei gruppi della community

Libreria file:

* I membri della community ora dispongono di diversi miglioramenti alla libreria dei file, ad esempio ordini di ordinamento, assegnazione tag...

Notifiche:

* I membri della community ricevono ora notifiche previa approvazione dei contributi che hanno superato un processo di moderazione

Moderazione:

* Filtro di rilevamento automatico dello spam
* I moderatori della community dispongono di filtri aggiuntivi per la moderazione (ad esempio domande a risposta/senza risposta)
* I moderatori della community possono creare un segnalibro e collegare la moderazione a filtri predefiniti (ad esempio tutti i post in attesa di approvazione)

Compatibilità globale con le modifiche fondamentali di AEM 6.4.

Nota: tutte queste funzioni sono disponibili anche per AEM 6.3. Controlla le note sulla versione di AEM Communities per [6.3.](https://helpx.adobe.com/it/experience-manager/6-3/release-notes.html).

## Problemi noti {#known-issues}

* **Moderazione** - Impossibile eliminare il post principale come singola operazione di eliminazione dall&#39;interfaccia utente di moderazione in blocco (CQ-4236797)
* **Console** - Il collegamento Password o nome utente dimenticato viene reindirizzato alla pagina di accesso invece del modulo di recupero password corrispondente (CQ-4237682)

## Selezionare le funzioni {#select-features}

Punteggio esperto (*Alimentato da Sensei*) - è utilizzato per abilitare la gamificazione, che è un modo efficace per incoraggiare e premiare comportamenti comunitari preziosi. Può essere utilizzato anche per identificare gli esperti a scopo di raccomandazione o marketing.

## Manifestazioni {#demonstrations}

Tutte queste funzioni possono essere dimostrate utilizzando [AEM Demo](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponibile pubblicamente su GitHub.com quando si utilizza lo scenario demo di AEM Communities e anche all’interno della nuova implementazione di riferimento di We.Retail.
