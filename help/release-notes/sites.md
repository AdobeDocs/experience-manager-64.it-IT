---
title: Note sulla versione di AEM Sites
seo-title: AEM Sites
description: Note sulla versione specifiche di Adobe Experience Manager 6.4 Sites.
seo-description: Note sulla versione specifiche di Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 13%

---


# AEM Sites Note sulla versione {#aem-sites-release-notes}

## Sites {#sites}

Per informazioni sui miglioramenti di AEM Sites 6.4, consulta i seguenti riferimenti:

### Amministrazione del sito {#site-administration}

* Nuova barra ad albero del contenuto per navigare rapidamente nella gerarchia di un sito. In combinazione con la vista a elenco, questo ripristina il modello di interazione Interfaccia classica per la navigazione in un sito.
* È stato migliorato lo scorrimento nella vista a schede e a elenco delle cartelle di grandi dimensioni.
* È stata migliorata l’interazione con i risultati della ricerca: il pulsante Indietro ripristina il risultato della ricerca precedente.
* Scelte rapide da tastiera aggiuntive, per la maggior parte delle azioni comuni, ad esempio l’apertura di una determinata barra, la modifica, lo spostamento e l’eliminazione di pagine o l’apertura di proprietà.
* Possibilità di disabilitare le scelte rapide da tastiera (abilitare/disabilitare in Preferenze).
* Interrompi la visualizzazione delle marche temporali in tutte le interfacce utente relative dopo 7 giorni (impostazione predefinita nelle Preferenze).

### Editor pagina {#page-editor}

* Elenco dei dispositivi aggiornato per l&#39;anteprima reattiva del sito, ora inclusi Apple iPhone 8, 8 Plus e X e Samsung S7
* È stata spostata la posizione predefinita per le informazioni sulla progettazione del modello lontano da /etc/design per supportare le impostazioni specifiche dei siti in /conf. I clienti che eseguono l&#39;aggiornamento da versioni AEM precedenti possono continuare a utilizzare /etc/design.

### Sviluppo di componenti e modelli {#component-amp-template-development}

* Project Archetype 13+, consulta [Github per le note](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases)sulla versione.
* HTL versione 1.3.1, consulta le [note sulla versione su Github](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* Core Components 2.0.4+, consulta le [note sulla versione su Github](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Sistema di stili

   * È stato aggiunto un concetto completamente nuovo per assegnare classi CSS ai componenti e consentire agli utenti di Editor pagina di selezionare da un sottoinsieme di stili tramite l’interfaccia utente
   * Aggiunta la possibilità di definire il nome dell’elemento HTML rappresentato intorno al componente, ad esempio &lt;main>, &lt;side>

* Sistema a griglia per contenitore layout, consulta [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Editor modelli e criteri

   * I criteri ora supportano le configurazioni di Style System per componente, contenitore e modello.
   * Supporto migliorato per la definizione del layout nei modelli su componenti modificabili

* Sito di riferimento We.Retail 3.0, consulta le [note sulla versione su Github](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM include la versione 1.12.4 della libreria jQuery per garantire la massima compatibilità con il codice personalizzato esistente. Adobe ha apportato modifiche per risolvere problemi di sicurezza noti.

### Editor e frammenti di contenuto {#content-fragments-amp-editor}

* Modelli di contenuti strutturati introdotti come base per i frammenti di contenuto

   * Interfaccia dell&#39;editor modelli
   * Elementi dati preconfigurati per modelli di frammenti di contenuto (testo su una sola riga, testo su più righe, numero, booleano, data e ora, enumerazione, riferimento contenuto, tag)

* Miglioramento dell&#39;usabilità dell&#39;editor AEM frammenti di contenuto

   * Panoramica di View-all-elements
   * Modifica a schermo intero per singoli elementi
   * Funzionalità avanzate di modifica di testo RTF (elenchi puntati, elenchi numerati, rientri, collegamenti ipertestuali, tabelle, ricerca e sostituzione, controllo ortografia)

* Sono state aggiunte opzioni di output avanzate per AEM frammenti di contenuto

   * Nuovo componente Frammento di contenuto, come parte dei componenti core. [Vedi il codice su GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * Supporto di Content Services con output JSON tramite Sling Model Exporter

### Frammenti esperienza {#experience-fragments}

* Sono stati introdotti blocchi predefiniti per frammenti esperienza, per facilitare il riutilizzo dei contenuti tra varianti di frammenti esperienza raggruppando i componenti e consentendo riferimenti semplici all’interno delle varianti.
* Aggiunta la possibilità di aggiungere frammenti esperienza ai progetti di traduzione tramite la barra laterale di riferimento
* Aggiunta la possibilità di avviare flussi di lavoro con frammenti esperienza tramite la barra laterale della cronologia
* La barra laterale di riferimento ora mostra dove viene utilizzato un frammento esperienza in AEM
* La configurazione delle posizioni dei modelli ora consente agli autori di definire a livello globale o di cartella quali modelli di frammenti esperienza possono essere utilizzati
* La ricerca sfaccettata ora supporta i filtri avanzati, come quelli pubblicati/non pubblicati, esportati nei social media e  Adobe Target
* È stato aggiunto l&#39;accesso a un singolo social media durante l&#39;esportazione di frammenti esperienza in Pinterest o Facebook
* Frammenti esperienza AEM integrati con  Adobe Target. La sincronizzazione di frammenti esperienza in Target creerà offerte in  Adobe Target che possono essere utilizzate con Target Visual Experience Composer (Compositore esperienza visivo) per incorporarle in qualsiasi esperienza Target abilitata.

### Traduzione {#translation}

* Miglioramento dell&#39;usabilità dei progetti di traduzione AEM:

   * Supporto di più lingue di destinazione in un progetto
   * Opzione per promuovere ed eliminare automaticamente gli avvii di traduzione
   * Opzione per pianificare l&#39;esecuzione periodica dei progetti di traduzione (giornaliera, settimanale, mensile, annuale)
   * Miglioramento delle sezioni di progetto di traduzione con informazioni più dettagliate sullo stato

* È stato introdotto l&#39;aggiornamento della memoria di traduzione inversa, per aggiornare la memoria di traduzione nel sistema di gestione della traduzione 3rd-party dopo le modifiche locali del contenuto in AEM
* I flussi di lavoro di traduzione ora supportano le origini di lingua raggruppate
* Aggiunta la possibilità di assegnare nomi arbitrari alle radici della lingua e utilizzare la proprietà JCR per la mappatura al codice ISO
* Gli aggiornamenti di traduzione intelligente ora riconoscono le nuove pagine aggiunte a un ramo master lingua
* Generazione di rapporti sullo stato di traduzione nella vista elenco Amministratore siti

### Gestione multisito (MSM) {#multi-site-management-msm}

* Miglioramento della scalabilità MSM mediante l&#39;utilizzo di un indice basato su Oak rispetto alla memoria (LiveCopyIndex)

### Lanci {#launches}

* Sono state migliorate le prestazioni dei lanci che contengono un albero del sito di grandi dimensioni e se sono attivi numerosi lanci
* Miglioramento della promozione automatica e della pubblicazione di avvii con più pagine radice.
* È stato risolto un problema che impediva il funzionamento dell’anteprima del dispositivo reattivo con le pagine modificate nel contesto di un lancio.

### Simulazione e targeting dei contenuti {#content-targeting-simulation}

* Cartelle di supporto per organizzare i segmenti in base al sito/contesto (CQ-94620)
* È stata spostata la posizione predefinita per i segmenti in /conf in modo da avere elenchi Segmento specifici per il sito o il contesto.

### AEM e Adobe Target  {#aem-amp-adobe-target-nbsp}

* Frammenti esperienza AEM integrati con  Adobe Target. La sincronizzazione di frammenti esperienza in Target creerà offerte in  Adobe Target che possono essere utilizzate con Target Visual Experience Composer (Compositore esperienza visivo) per incorporarle in qualsiasi esperienza Target abilitata.
*  Adobe Target mbox.js versione 63 ora incluso.  Adobe consiglia di passare all&#39;implementazione a at.js.
* at.js versione 1.2.2 è ora incluso.  Adobe consiglia di utilizzare Dynamic Tag Management (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) per effettuare il provisioning di at.js nel sito.

### AEM e Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5 ora incluso.  Adobe consiglia di passare all’implementazione in AppMeasurement.js
* AppMeasurement.js 1.8.0 ora incluso.  Adobe consiglia di utilizzare Gestione tag dinamica (DTM) o [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) per eseguire il provisioning di AppMeasurement.js nel sito.

## Add-on Communities {#communities-add-on}

Consulta la [pagina delle note sulla versione di Communities](/help/release-notes/communities-release-notes.md)

## Add-on Screens {#screens-add-on}

* È stato aggiunto il supporto per la connessione dei lettori di schermo AEM server di pubblicazione per i download di comandi e controlli e canali (invece di AEM l’autore).
* Possibilità di raggruppare le assegnazioni dei canali nelle pianificazioni
* Le assegnazioni dei canali ora dispongono della data di inizio e di fine
* Pannello dispositivo ora mostra la shell del lettore e la versione del firmware
* Nell&#39;elenco Dashboard dispositivo viene visualizzato lo stato di connessione del lettore
* Aggiunto il supporto Google Chrome OS per AEM Screens Player
* Aggiunta di Microsoft Windows 10 per il lettore AEM Screens
