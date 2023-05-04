---
title: Note generali sulla versione di Adobe Experience Manager 6.4
seo-title: Release Notes
description: Note di Adobe Experience Manager 6.4 che descrivono le informazioni sulla versione, le novità, le modalità di installazione e gli elenchi dettagliati delle modifiche.
seo-description: Adobe Experience Manager 6.4 notes outlining the release information, what's new, how to install and detailed change lists.
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
exl-id: ee034595-2d2a-4887-86c4-6bf0770da6a2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2765'
ht-degree: 9%

---

# Note generali sulla versione di Adobe Experience Manager 6.4 {#general-release-notes-for-adobe-experience-manager}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Informazioni sulla versione {#release-information}

| Prodotto | Adobe Experience Manager |
|---|---|
| Versione | 6.4 |
| Tipo | Versione principale |
| Data di disponibilità generale | 4 aprile 2018 |
| Aggiornamenti consigliati | Consulta [Versioni e aggiornamenti di AEM](https://helpx.adobe.com/it/experience-manager/aem-releases-updates.html) |

### Trivia {#trivia}

Il ciclo di rilascio di questa versione di Adobe Experience Manager è iniziato il 27 aprile 2017 ed è terminato il 22 marzo 2018 passando attraverso 22 fasi successive di controllo della qualità e risoluzione dei bug. Il numero totale di problemi relativi ai clienti risolti in questa versione con miglioramenti e nuove funzioni è 704.

Adobe Experience Manager 6.4 è generalmente disponibile dal 4 aprile 2018.

>[!NOTE]
>
>Adobe consiglia di installare il service pack più recente in quanto tutti i nuovi feature pack sono forniti solo tramite [Service Pack](https://helpx.adobe.com/it/experience-manager/maintenance-releases-roadmap.html).

## Novità {#what-s-new}

Adobe Experience Manager 6.4 è una versione di aggiornamento del codice di base di Adobe Experience Manager 6.3. Fornisce funzionalità nuove e migliorate, importanti correzioni di casi segnalati dai clienti, miglioramenti con priorità alta e correzioni di bug generali per migliorare la stabilità del prodotto. Include anche la maggior parte di tutti i pacchetti di funzioni, gli hotfix e i service pack di Adobe Experience Manager 6.3.

L’elenco seguente fornisce una panoramica, mentre nelle pagine successive sono riportati tutti i dettagli.

### Experience Manager Foundation {#experience-manager-foundation}

Elenco completo delle modifiche in [AEM Foundation](wcm-platform.md).

La piattaforma Adobe Experience Manager 6.4 si basa sulle versioni aggiornate del framework basato su OSGi (Apache Sling e Apache Felix) e del Java Content Repository: Apache Jackrabbit Oak 1.8.2.

Quickstart utilizza Eclipse Jetty 9.3.22 come motore servlet.

#### Interfaccia utente {#user-interface}

Sono stati apportati diversi miglioramenti all’interfaccia utente per renderla più produttiva e facile da usare.

* [Barra a barre Nuova struttura contenuto](/help/sites-authoring/basic-handling.md#content-tree) per navigare rapidamente in una gerarchia. In combinazione con la vista a elenco, viene ripristinato il modello di interazione con l’interfaccia classica.
* È stata migliorata l&#39;esperienza di scorrimento nella vista a schede e a elenco delle cartelle di grandi dimensioni.
* [Interazione migliorata con i risultati della ricerca](/help/sites-authoring/search.md) - il pulsante indietro ripristina il risultato della ricerca precedente.
* [Scelte rapide da tastiera aggiuntive](/help/sites-authoring/keyboard-shortcuts.md), per la maggior parte delle azioni comuni, ad esempio per aprire una particolare barra, per modificare, spostare ed eliminare un elemento o per aprire le proprietà.
* [Possibilità di disattivare le scelte rapide da tastiera](/help/sites-authoring/user-properties.md) (attiva/disattiva in Preferenze).
* [Interrompe la visualizzazione di marche temporali in tutta l’interfaccia utente](/help/sites-authoring/user-properties.md) relativo dopo 7 giorni (impostazione predefinita in Preferenze).

Consulta la sezione [Documentazione sull’authoring](/help/sites-authoring/home.md) per ulteriori informazioni su queste funzioni.

>[!CAUTION]
>
>Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica. AEM 6.4 include l’interfaccia classica e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a utilizzarla così com’è. L’interfaccia classica rimane completamente supportata anche se obsoleta. [Leggi tutto](/help/sites-deploying/ui-recommendations.md).

#### Archivio dei contenuti {#content-repository}

* Compattazione più rapida ed efficiente tramite Pulizia revisioni online. I test interni mostrano che la nuova compattazione della coda è fino a 10 volte più veloce e può recuperare più spazio su disco con meno IOPS rispetto a AEM 6.3. Questo riduce l&#39;impatto sulle prestazioni mentre è in esecuzione il cleanup delle revisioni online. Per ulteriori informazioni, consulta [la pagina della documentazione](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes).

* Pulizia revisioni continua per MongoMK sostituisce la manutenzione programmata
* Miglioramento dell&#39;efficienza del cleanup delle revisioni negli archivi dei nodi dei documenti

#### Ricerca e indicizzazione {#search-indexing}

* Supporto migliorato per le operazioni di indicizzazione tramite oak-run (CLI):

   * Controllo della coerenza dell&#39;indice
   * Statistiche di indicizzazione
   * Importazione o esportazione della configurazione dell&#39;indice
   * Reindicizzazione

* Riduzione della crescita dell&#39;archivio correlata a Lucene per un miglioramento generale delle prestazioni del sistema

Per maggiori informazioni, visita [questa pagina della documentazione](/help/sites-deploying/indexing-via-the-oak-run-jar.md).

#### Monitoraggio {#monitoring}

* Nuovo [Panoramica del sistema](/help/sites-administering/operations-dashboard.md#system-overview) fornisce una visualizzazione istantanea di tutte le attività e lo stato del sistema relativi alle prestazioni.
* Un nuovo set di [Controlli di integrità](/help/sites-administering/operations-dashboard.md#health-checks) Indicizzazione, query e manutenzione

#### Progetti e flussi di lavoro {#projects-and-workflows}

* Novità [Editor del flusso di lavoro per creare e modificare modelli di flusso di lavoro](/help/sites-developing/workflows-models.md).

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### Aggiornamento da versione precedente {#upgrade-from-earlier-version}

* [Compatibilità con le versioni precedenti](/help/sites-deploying/backward-compatibility.md): Le funzioni retrocompatibili della versione 6.4 consentono di mantenere il codice personalizzato compatibile nella maggior parte dei casi e riducono lo sforzo di aggiornamento.
* [Valutazione della complessità dell’aggiornamento](/help/sites-deploying/pattern-detector.md): Nuovo strumento di rilevamento pattern per valutare la complessità degli aggiornamenti prima dell’aggiornamento.
* [Ristrutturazione dell’archivio](/help/sites-deploying/repository-restructuring.md): ristrutturazioni significative (principalmente /etc) per facilitare gli aggiornamenti e promuovere le migliori pratiche di implementazione
* Per ulteriori informazioni generali sugli aggiornamenti, consulta la sezione [questa pagina](/help/sites-deploying/upgrade.md) per ulteriori dettagli.

### Experience Manager Sites {#experience-manager-sites}

Elenco completo delle modifiche in [AEM Sites e componenti aggiuntivi](sites.md).

#### Esperienze fluide {#fluid-experiences}

L’introduzione di Esperienze fluide all’inizio del 2017, con il supporto di Frammenti di contenuto, Frammenti esperienza e Content Services, ha dato il via all’evoluzione verso una gestione dei contenuti multicanale all’inizio. AEM 6.4 estende in modo significativo ciascuna delle aree:

**[Frammenti di contenuto](/help/assets/content-fragments.md)**

Novità nella versione 6.4 sono [modello di contenuto](/help/assets/content-fragments-models.md) e un nuovo [componente configurabile](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=it) per fornire un output HTML flessibile e JSON da includere in Content Services.

**Frammenti esperienza**

Grazie alla funzionalità Blocchi predefiniti, ora è più efficiente creare varianti di un frammento con lo stesso contenuto ma con layout diverso. Oltre a inviare frammenti di esperienza a Facebook e Pinterest, ora è possibile inviarli ad Adobe Target come offerta.

**Content Services**

Sono stati apportati diversi miglioramenti a Sling Model Exporter e ai componenti core, allo scopo di fornire un output JSON affidabile per incorporare contenuti nelle app mobili e nelle esperienze create con app a pagina singola.

#### Come Creare I Siti Più Rapidamente {#gettings-sites-built-quicker}

AEM 6.4 completa la trasformazione al modello componente di nuova generazione. Il concetto dei componenti core introdotto in AEM 6.3 e ora unito al sistema di stili, fornisce un modo efficiente per creare nuovi siti ed estendere quelli esistenti.

Esercitazione consigliata per scoprire come sfruttare al meglio il nuovo modello di componente: [Guida introduttiva ad AEM Sites - Tutorial WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=it)

#### Add-on Screens {#screens-add-on}

Il significato di AEM Screens è la trasmissione di un messaggio coerente su tutti i canali di marketing, comprese le reti di digital signage e chiosco. AEM 6.4 aggiunge il supporto per l&#39;esecuzione di Signage Player su hardware Microsoft Windows e Google Chrome OS. Sono inoltre disponibili miglioramenti alla gestione e alla programmazione dei dispositivi remoti (gruppi di canali).

Per ulteriori informazioni sugli aggiornamenti di Screens, consulta [Guida utente di AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html?lang=it).

### Experience Manager Communities {#experience-manager-communities}

AEM 6.4 aggiunge molte nuove funzioni e miglioramenti a Communities. L’elenco completo delle modifiche è disponibile in [AEM Communities](communities-release-notes.md). Gli elementi di rilievo di questa versione sono:

#### Miglioramenti alla moderazione {#enhancements-to-moderation}

**Rilevamento automatico dello spam**

È stato fornito un nuovo motore di rilevamento dello spam per filtrare i contenuti generati dagli utenti indesiderati sui siti e sui gruppi della community. Una volta abilitato da system/console/configMgr, contrassegna un contenuto generato dall&#39;utente come spam in base a un set predefinito di parole spam. Per ulteriori informazioni sul motore di rilevamento dello spam, consulta [automatizzazione della generazione di contenuti da parte degli utenti della community](/help/communities/moderate-ugc.md#spam-detection).

![spamdetection](assets/spamdetection.png)

**Nuovi filtri per QnA**

Sono stati aggiunti nuovi filtri, denominati Risposta e Non risposto, alla console di moderazione di gruppo per filtrare le domande di QnA. Per sapere come funzionano i filtri di stato con risposta e senza risposta, consulta [contenuto generato dagli utenti per la moderazione in massa](/help/communities/moderation.md#main-pars-note-521961797).

**Filtri di moderazione dei segnalibri**

È stata fornita la possibilità di contrassegnare i filtri di moderazione predefiniti nella console di moderazione. Questi filtri vengono aggiunti alla fine della stringa URL e possono quindi essere condivisi, riutilizzati e rivisitati in un secondo momento. Scopri come contrassegnare i filtri nei segnalibri [console di moderazione di gruppo](/help/communities/moderation.md#main-pars-note-429176623).

#### Eliminare i profili UGC e utente {#delete-ugc-and-user-profiles}

AEM 6.4 Comuni espone [API predefinite](/help/communities/user-ugc-management-service.md) e campione [servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) per consentire agli utenti finali di controllare i propri dati. Queste API consentono inoltre alle organizzazioni di elaborazione dei dati e di controllo dei dati di soddisfare le richieste di conformità RGPD dell’UE.

#### Miglioramenti alla gestione del sito e dei gruppi {#enhancements-to-site-and-group-management}

**Creare gruppi con più impostazioni internazionali in un singolo passaggio**

È stata fornita la possibilità di creare gruppi multilingue in un’unica operazione. Per creare tali gruppi, gli utenti possono accedere a Raccolta di gruppi del sito community desiderato dalla console Sites . Crea un gruppo e specifica le lingue desiderate nella pagina Modello per gruppo community . Per ulteriori informazioni su questa funzionalità, consulta [console gruppi community](/help/communities/groups.md).

![multilingue](assets/multilingualgroup.png)

**[Elimina siti e gruppi della community con un clic](/help/communities/groups.md)**

L’icona Elimina è ora disponibile sui rispettivi siti e gruppi durante la navigazione dalla navigazione globale. Questa icona elimina tutti gli elementi e i contenuti associati al sito o al gruppo e rimuove tutte le associazioni utente. Per ulteriori informazioni su questa funzionalità, consulta [gestione di siti community](/help/communities/create-site.md#main-pars-text-fe17) e [gestione di gruppi di community](/help/communities/groups.md#main-pars-text-5e8c).

#### Miglioramenti all’abilitazione {#enhancements-to-enablement}

Le funzioni Assegnazione e Catalogo sono ora disponibili all&#39;interno dei gruppi. Questo consente di creare, gestire e pubblicare contenuti di apprendimento per un set specifico di membri della community mirati. Per ulteriori informazioni sull&#39;abilitazione dei gruppi community, consulta [gestione delle risorse di abilitazione](/help/communities/resource.md).

![assegna catalogo](assets/assignmentcatalog.png)

### Experience Manager Assets {#experience-manager-assets}

AEM 6.4 introduce diverse nuove funzioni e miglioramenti per Assets, tra cui nuova integrazione Creative Cloud, innovazioni fondamentali in materia di intelligenza artificiale, gestione migliorata dei metadati, miglioramenti alla generazione di rapporti e miglioramenti generali dell’esperienza utente. Elenco completo delle modifiche disponibili in [AEM Assets](assets.md). Gli elementi di rilievo della versione sono:

**Adobe Asset Link**

Adobe Asset Link in Creative Cloud for enterprise semplifica la collaborazione tra creativi e addetti al marketing nel processo di creazione dei contenuti. Si tratta di una nuova funzionalità nativa nella Creative Cloud per le aziende che collega Photoshop, Illustrator e InDesign a AEM, senza dover lasciare il proprio strumento di scelta.

Per ulteriori informazioni su questa funzionalità, sui prerequisiti e su come accedervi, consulta [Adobe Asset Link](https://www.adobe.com/it/creativecloud/business/enterprise/adobe-asset-link.html).

![adobe_asset_link](assets/adobe_asset_link.png)

**App desktop AEM**

AEM’app desktop è stata aggiornata alla versione 1.8, compatibile con AEM 6.4. L’elenco completo delle modifiche per AEM’app desktop è disponibile in un apposito [Note sulla versione dell’app desktop AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html) documento.

I miglioramenti introdotti a partire dalla versione 6.3 di AEM includono la possibilità di caricare cartelle gerarchiche in background, una nuova interfaccia utente per monitorare le operazioni in background sulle risorse, il caching migliorato, la rete e l’accesso, nonché miglioramenti generali della stabilità. La documentazione include anche un [guida alle best practice](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html).

**Servizi Adobe Sensei**

Le nuove funzionalità includono Tag avanzati migliorati, con la possibilità di apprendere la tassonomia aziendale del cliente, assegnare automaticamente tag alle risorse digitali con tag specifici per il cliente e la Ricerca di traduzione avanzata, che migliora la reperibilità in più lingue traducendo al volo i termini di ricerca. Per ulteriori informazioni su questa funzione, consulta [Tag avanzati migliorati](/help/assets/enhanced-smart-tags.md).

![advanced_smart_tags2](assets/enhanced_smart_tags2.png)

**Metadati**

Diversi miglioramenti includono la possibilità di importare ed esportare simultaneamente metadati per un gran numero di risorse e costrutti di metadati avanzati, come [Metadati a cascata](/help/assets/cascading-metadata.md).

**Rapporti**

Il reporting delle risorse è stato sottoposto a una grande revisione in AEM 6.4 con nuovo framework di reporting, esperienza utente e più rapporti OOTB per i casi d’uso dei clienti. Per scoprire come generare vari rapporti, consulta [Rapporti sulle risorse](/help/assets/asset-reports.md).

**Esperienza utente**

Sono stati apportati diversi miglioramenti per migliorare l’esperienza di navigazione, ricerca e amministrazione per gli utenti di Assets, ad esempio esperienza di scorrimento, pulsante di ricerca, filtri di ricerca migliorati e molto altro ancora. Elenco completo disponibile in [AEM Assets](assets.md).

**Brand Portal**

Diversi miglioramenti in aree di metadati, reporting, diritti digitali, esperienza di accesso e prestazioni di pubblicazione per la distribuzione delle risorse. Per informazioni sui nuovi miglioramenti e funzioni, consulta [Novità di AEM Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=it).

#### Add-on Dynamic Media {#dynamic-media-add-on}

AEM 6.4 include molte nuove funzioni e miglioramenti apportati a Dynamic Media. L’elenco completo è disponibile in [AEM Assets](assets.md). Elementi di rilievo:

**Ritaglio avanzato**

Il ritaglio avanzato, basato su Adobe Sensei, fornisce automaticamente un ritaglio non distruttivo delle immagini, mantenendo il punto di interesse per il design reattivo. Potete visualizzare in anteprima i suggerimenti per le immagini ritagliate e, se necessario, regolarli manualmente. Questa funzione consente anche la generazione automatizzata dei campioni per le immagini dei prodotti.

Vedi [Profili immagine](/help/assets/image-profiles.md) documentazione per ulteriori informazioni sull’utilizzo di Smart Crop.

Vedi [Aggiunta di risorse Dynamic Media alle pagine](/help/assets/adding-dynamic-media-assets-to-pages.md) per ulteriori informazioni sull’utilizzo di Smart Crop nel componente Dynamic Media.

**Imaging avanzato**

L&#39;imaging intelligente sfrutta le caratteristiche di visualizzazione esclusive di ogni utente per distribuire automaticamente le immagini ottimizzate per la propria esperienza, ottenendo prestazioni e coinvolgimento migliori.

Vedi [Imaging avanzato](/help/assets/imaging-faq.md) documentazione per ulteriori informazioni.

![smart_crop](assets/smart_crop.png)

**Miglioramenti a supporti e visualizzatori emergenti**

I nuovi visualizzatori, tra cui Panoramico e VR, consentono di offrire esperienze più coinvolgenti.

Vedi [Immagini panoramiche](/help/assets/panoramic-images.md) documentazione per ulteriori informazioni.

### Experience Manager Forms {#experience-manager-forms}

AEM 6.4 Forms introduce diverse nuove funzioni e miglioramenti. Gli elementi di rilievo includono:

* Comunicazioni interattive multicanale
* Precompilare le comunicazioni interattive dalle applicazioni aziendali
* Modernizzazione del flusso di lavoro e supporto per i lavoratori mobili
* Frammenti di carico pigri
* Aggiornamento single-hop da LiveCycle a Experience Manager Forms 6.4

Maggiori dettagli su [AEM Forms](forms.md) pagina delle note sulla versione. Inoltre, consulta la sezione [Riepilogo delle nuove funzioni e dei miglioramenti in Forms 6.4 AEM](/help/forms/using/whats-new.md) per informazioni sulle funzioni nuove e migliorate e sulle risorse di documentazione.

### Experience Manager Livefyre {#experience-manager-livefyre}

Puoi integrare Livefyre con la tua istanza AEM 6.4. Le informazioni su come integrare Livefyre con AEM si trovano qui:

* [Integrazione di Livefyre](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html)

### Sfruttare lo sviluppo mirato dei clienti {#leverage-customer-focused-development}

Adobe utilizza un modello di sviluppo incentrato sul cliente che consente ai clienti di contribuire a tutte le fasi del processo di sviluppo, durante le specifiche, lo sviluppo e il test. Ringraziamo tutti i clienti e i partner che hanno contribuito a questo processo.

Adobe dispone delle procedure e dei processi necessari per abilitare la raccolta, la definizione delle priorità e il tracciamento della risoluzione dei bug incentrati sul cliente e lo sviluppo delle richieste di miglioramento. La [Portale di supporto Adobe Marketing Cloud](https://helpx.adobe.com/it/contact/enterprise-support.ec.html) è integrato con il sistema di monitoraggio Adobe e difetti. Laddove possibile, le domande dei clienti vengono identificate e risolte con l’Assistenza clienti. Quando si passa a R&amp;S, tutte le informazioni dei clienti vengono acquisite e utilizzate a scopo di definizione delle priorità e reporting. Nello sviluppo viene data la priorità ai problemi di assistenza a pagamento e garanzia e ai miglioramenti per i clienti a pagamento.

Questo processo di prioritizzazione ha portato a più di 500 cambiamenti incentrati sul cliente risolti nella AEM 6.4.

## Elenco dei file che fanno parte della versione {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Quickstart indipendente: cq-quickstart-6.4.0.jar
* Avvio rapido server applicazioni: cq-quickstart-6.4.0.war
* Dispatcher 4.3.1 o successivo per vari server web e piattaforme. Vedi [collegamento di download](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html).
* Plug-in per Eclipse IDE. [Ulteriori informazioni e download](/help/sites-developing/aem-eclipse.md).

* Estensione per l&#39;editor di codice Brackets. [Ulteriori informazioni e download](/help/sites-developing/aem-brackets.md).
* Dipendenze Maven/Gradle. Vedi [collegamento di download](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/).

**Sites**

* Componenti core ([Progetto GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components))
* Implementazione di riferimento We.Retail ([leggi tutto](/help/sites-developing/we-retail.md))
* Archetipo di progetto Blueprint ([Progetto GitHub](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype))
* Lettori AEM Screens per varie piattaforme target ([scaricare](https://download.macromedia.com/screens/))
* Modelli per lingue con contenuti avanzati. L&#39;inglese è preinstallato - è possibile scaricare altre lingue

   * [Tedesco](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spagnolo](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italiano](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Francese](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [Strumenti di modernizzazione AEM](/help/sites-developing/modernization-tools.md) per migrare i componenti dell’interfaccia classica a Coral 3

**Risorse**

* App desktop Adobe Experience Manager ([leggi tutto](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) e [scaricare](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html))

* Pacchetto per aggiungere un PDF Rasterizer migliorato ([leggi tutto](/help/assets/aem-pdf-rasterizer.md) e [scaricare](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg))

* Pacchetto per aggiungere supporto esteso per immagini RAW ([leggi tutto](/help/assets/camera-raw.md))

**Forms**

* Pacchetti per le funzionalità di AEM Forms:

   * [adobe-aemfd-aix-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-linux-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-solaris-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-win-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-osx-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)

## Lingue {#languages}

L’interfaccia utente è disponibile nelle seguenti lingue:

* Inglese
* Tedesco
* Francese
* Spagnolo
* Italiano
* Portoghese brasiliano
* Giapponese
* Cinese semplificato
* Cinese tradizionale (supporto limitato)
* Coreano

Experience Manager 6.4 è stato certificato per GB18030-2005 CITS per l’utilizzo dello standard di codifica cinese.

## Installazione e aggiornamento {#install-update}

Vedi [istruzioni di installazione](/help/sites-deploying/custom-standalone-install.md) per i requisiti di configurazione.

Vedi [documentazione di aggiornamento](/help/sites-deploying/upgrade.md) per istruzioni dettagliate.

## Piattaforme supportate {#supported-platforms}

Trova la matrice completa delle piattaforme supportate incl. Livello di supporto attivato [AEM 6.4 Requisiti tecnici](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Oracle è stato spostato in un modello &quot;Long Term Support&quot; (LTS) per i prodotti Java SE di Oracle. Java 9 e 10 sono versioni non LTS per Oracle (vedi [Roadmap del supporto Java SE di Oracle](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe supporterà solo le versioni LTS di Java per l’esecuzione di AEM in produzione. Pertanto Java 8 è la versione consigliata da utilizzare con AEM 6.4.

## Funzioni obsolete e rimosse {#deprecated-and-removed-features}

Adobe valuta costantemente le funzionalità del prodotto e nel tempo pianifica di sostituire le funzionalità con versioni più potenti, oppure decide di reimplementare parti selezionate per essere meglio preparate per aspettative o estensioni future.

Per Adobe Experience Manager 6.4, [leggi l’elenco delle funzionalità obsolete e rimosse](deprecated-removed-features.md). La pagina contiene anche un pre-annuncio delle modifiche nel 2019 e un avviso importante per i clienti che aggiornano da versioni precedenti.

## Elenchi di modifiche dettagliati {#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[Community AEM](communities-release-notes.md)

[AEM Forms](forms.md)

[AEM Foundation](wcm-platform.md)

## Problemi noti {#known-issues}

[Elenco dei problemi noti](known-issues.md)

### Download e supporto del prodotto (siti con restrizioni) {#product-download-and-support-restricted-sites}

Questi siti sono disponibili solo per i clienti. Se sei un cliente e hai bisogno di accedere, contatta il tuo responsabile commerciale di Adobe.

* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/).
* Aggiornamenti dei prodotti, patch e pacchetti per funzionalità aggiuntive su [Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/it/aem.html).
* [Assistenza clienti tramite Admin Console](https://adminconsole.adobe.com/). Per ulteriori informazioni, consulta [Nuova esperienza di accesso all’Assistenza clienti di Adobe](https://experienceleague.adobe.com/docs/customer-one/using/home.html).
