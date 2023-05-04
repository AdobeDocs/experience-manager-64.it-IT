---
title: Note sulla versione di AEM Sites
seo-title: AEM Sites
description: Note sulla versione specifiche di Adobe Experience Manager 6.4 Sites.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 1%

---

# Note sulla versione di AEM Sites {#aem-sites-release-notes}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Sites {#sites}

Per i miglioramenti di AEM Sites 6.4, consulta quanto segue:

### Amministrazione del sito {#site-administration}

* Nuova barra Struttura contenuto per navigare rapidamente nella gerarchia di un sito. In combinazione con la vista a elenco, viene ripristinato il modello di interazione con l’interfaccia classica per la navigazione in un sito.
* È stato migliorato lo scorrimento nella vista a schede e a elenco delle cartelle di grandi dimensioni.
* È stata migliorata l’interazione con i risultati della ricerca: il pulsante Indietro ripristina il risultato della ricerca precedente.
* Scelte rapide da tastiera aggiuntive per le azioni più comuni, ad esempio per aprire una particolare barra, modificare, spostare ed eliminare pagine o aprire proprietà.
* Possibilità di disattivare le scelte rapide da tastiera (attiva/disattiva in Preferenze).
* Interrompi la visualizzazione di marche temporali in tutta l’interfaccia utente relative dopo 7 giorni (impostazione predefinita in Preferenze).

### Editor pagina {#page-editor}

* È stato aggiornato l’elenco dei dispositivi per l’anteprima dinamica del sito, ora inclusi Apple iPhone 8, 8 Plus e X e Samsung S7
* La posizione predefinita per le informazioni sulla progettazione del modello è stata spostata da /etc/design per supportare le impostazioni specifiche dei siti in /conf. I clienti che eseguono l’aggiornamento da versioni AEM precedenti possono continuare a utilizzare /etc/design.

### Sviluppo di componenti e modelli {#component-amp-template-development}

* Archetipo di progetto 13+, vedi [Github per le note sulla versione](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL versione 1.3.1, vedi [Github per le note sulla versione](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Componenti core 2.0.4+, vedi [Github per le note sulla versione](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Sistema di stili

   * È stato aggiunto un concetto completamente nuovo per assegnare le classi CSS ai componenti e consentire agli utenti nell’Editor pagina di selezionare da un sottoinsieme di stili tramite l’interfaccia utente
   * È stata aggiunta la possibilità di definire il nome dell’elemento HTML rappresentato intorno al componente, ad esempio &lt;main>, &lt;aside>

* Sistema a griglia per contenitore di layout, vedi [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Editor modelli e criteri

   * I criteri ora supportano le configurazioni del sistema di stili per componente, contenitore, modello.
   * Supporto migliorato per la definizione del layout nei modelli su componenti modificabili

* Sito di riferimento We.Retail 3.0, vedi [Github per le note sulla versione](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM include la versione 1.12.4 della libreria jQuery per fornire la massima compatibilità con il codice personalizzato esistente. Sono state apportate modifiche per Adobe per risolvere problemi di sicurezza noti.

### Editor e frammenti di contenuto {#content-fragments-amp-editor}

* Modelli di contenuto strutturati introdotti come base per i frammenti di contenuto

   * Interfaccia dell’editor modelli
   * Elementi dati preconfigurati per modelli di frammenti di contenuto (testo a riga singola, testo su più righe, numero, booleano, data e ora, enumerazione, riferimento contenuto, tag)

* Miglioramento dell’usabilità dell’editor dei frammenti di contenuto AEM

   * Panoramica di View-all-elements
   * Modifica a schermo intero per elementi singoli
   * Funzionalità di modifica avanzata del testo (elenchi puntati, elenchi numerati, rientri, collegamenti ipertestuali, tabelle, ricerca e sostituzione, controllo ortografia)

* Sono state aggiunte opzioni di output avanzate per i frammenti di contenuto AEM

   * Nuovo componente Frammento di contenuto , come parte dei componenti core. [Vedi il codice su GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Supporto di Content Services per l’output JSON tramite Sling Model Exporter

### Frammenti di esperienza {#experience-fragments}

* Sono stati introdotti blocchi predefiniti per frammenti esperienza per facilitare il riutilizzo dei contenuti tra le varianti di Frammenti esperienza raggruppando i componenti e consentendo un riferimento semplice all’interno delle varianti.
* Aggiunta della possibilità di aggiungere Frammenti esperienza ai progetti di traduzione tramite la barra degli strumenti Riferimento
* Aggiunta la possibilità di avviare flussi di lavoro con Frammenti esperienza tramite la barra Timeline
* La barra dei riferimenti mostra ora dove viene utilizzato un frammento esperienza in AEM
* La configurazione delle posizioni dei modelli ora consente agli autori di definire a livello globale o di cartella quali modelli di frammento esperienza possono utilizzare
* La ricerca su facet ora supporta il filtro avanzato, ad esempio pubblicato/non pubblicato, esportato nei social media e in Adobe Target
* Accesso a singoli social media durante l’esportazione di frammenti esperienza in Pinterest o Facebook
* Frammenti esperienza AEM integrati con Adobe Target. La sincronizzazione dei frammenti esperienza con Target creerà offerte in Adobe Target che possono essere utilizzate con il Compositore esperienza visivo di Target per incorporarlo in qualsiasi esperienza abilitata per Target.

### Traduzione {#translation}

* Miglioramento dell’usabilità dei progetti di traduzione AEM:

   * Supporto per più lingue di destinazione in un progetto
   * Opzione per promuovere ed eliminare automaticamente i lanci di traduzione
   * Opzione di programmazione dell&#39;esecuzione periodica dei progetti di traduzione (giornaliera, settimanale, mensile, annuale)
   * Riquadri di progetto di traduzione ottimizzati con informazioni sullo stato più dettagliate

* Aggiornamento della memoria di traduzione inversa, per aggiornare la memoria di traduzione nel sistema di gestione della traduzione di terze parti dopo le modifiche locali del contenuto in AEM
* I flussi di lavoro di traduzione ora supportano le radici della lingua raggruppate
* Aggiunta la possibilità di assegnare nomi arbitrari alle radici della lingua e utilizzare la proprietà JCR per la mappatura al codice ISO
* Gli aggiornamenti di traduzione avanzata ora riconoscono le nuove pagine aggiunte a un ramo principale della lingua
* Generazione di rapporti sullo stato di traduzione nella vista a elenco dell’amministratore di Sites

### Gestione multisito (MSM) {#multi-site-management-msm}

* Miglioramento della scalabilità MSM utilizzando un indice basato su Oak e in memoria (LiveCopyIndex)

### Lanci {#launches}

* Migliorate le prestazioni dei lanci che contengono una struttura del sito di grandi dimensioni e se sono attivi molti lanci
* Miglioramento della promozione automatica e della pubblicazione dei lanci con più pagine principali.
* È stato risolto un problema che impediva il funzionamento dell’anteprima del dispositivo reattivo con le pagine modificate nel contesto di un lancio.

### Targeting e simulazione dei contenuti {#content-targeting-simulation}

* Cartelle di supporto per organizzare i segmenti in base al sito/contesto (CQ-94620)
* La posizione predefinita per i segmenti è stata spostata in /conf in modo da avere elenchi di segmenti specifici per il sito o il contesto.

### AEM e Adobe Target  {#aem-amp-adobe-target-nbsp}

* Frammenti esperienza AEM integrati con Adobe Target. La sincronizzazione dei frammenti esperienza con Target creerà offerte in Adobe Target che possono essere utilizzate con il Compositore esperienza visivo di Target per incorporarlo in qualsiasi esperienza abilitata per Target.
* Adobe Target mbox.js versione 63 è ora incluso. Adobe consiglia di passare all’implementazione di at.js.
* È ora inclusa la versione 1.2.2 di at.js . Adobe consiglia di utilizzare Dynamic Tag Management (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) per eseguire il provisioning di at.js nel sito.

### AEM e Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 ora incluso. Adobe consiglia di passare all’implementazione in AppMeasurement.js
* AppMeasurement.js 1.8.0 ora incluso. Adobe consiglia di utilizzare Dynamic Tag Management (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) per eseguire il provisioning di AppMeasurement.js nel sito.

## Componente aggiuntivo per community {#communities-add-on}

Vedi [Pagina Note sulla versione di Communities](/help/release-notes/communities-release-notes.md)

## Add-on Screens {#screens-add-on}

* È stato aggiunto il supporto per la connessione dei lettori Screens ai server di pubblicazione AEM per i download di comandi e controlli e canali (anziché direttamente all’autore AEM).
* Aggiunta la possibilità di raggruppare le assegnazioni dei canali in Pianificazioni
* Le assegnazioni dei canali ora dispongono della data di inizio e di fine
* Dashboard del dispositivo mostra ora la shell del lettore e la versione del firmware
* L&#39;elenco del dashboard del dispositivo mostra lo stato di connessione del lettore
* È stato aggiunto il supporto Google Chrome OS per AEM Screens Player
* Aggiunto Microsoft Windows 10 per AEM Screens Player
