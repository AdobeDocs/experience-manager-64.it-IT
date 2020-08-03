---
title: Note generali sulla versione per Adobe Experience Manager 6.4
seo-title: Note sulla versione
description: ' Adobe Experience Manager 6.4 note che illustrano le informazioni sulla versione, le novità, le modalità di installazione e gli elenchi dettagliati delle modifiche. '
seo-description: ' Adobe Experience Manager 6.4 note che illustrano le informazioni sulla versione, le novità, le modalità di installazione e gli elenchi dettagliati delle modifiche. '
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '2844'
ht-degree: 26%

---


# Note generali sulla versione per Adobe Experience Manager 6.4 {#general-release-notes-for-adobe-experience-manager}

## Informazioni sulla versione {#release-information}

| Prodotto | Adobe Experience Manager |
|---|---|
| Versione | 6.4 |
| Tipo | Versione principale |
| Data di disponibilità generale | 4 aprile 2018 |
| Aggiornamenti consigliati | See [AEM releases and updates](https://helpx.adobe.com/it/experience-manager/aem-releases-updates.html) |

### Informazioni varie {#trivia}

Il processo di pubblicazione di questa versione di  Adobe Experience Manager è iniziato il 27 aprile 2017 ed è terminato il 22 marzo 2018 passando per 22 fasi successive di controllo della qualità e risoluzione dei bug. Il numero complessivo di errori relativi ai clienti risolti in questa versione con miglioramenti e aggiunta di nuove funzioni è pari a 704. 

Adobe Experience Manager 6.4 è disponibile a livello generale dall’4 aprile 2018.

>[!NOTE]
>
> Adobe consiglia di installare il service pack più recente in quanto tutti i nuovi pacchetti di funzionalità vengono forniti solo tramite [Service Pack](https://helpx.adobe.com/it/experience-manager/maintenance-releases-roadmap.html).

## Novità {#what-s-new}

Adobe Experience Manager 6.4 è una versione di aggiornamento della codebase di Adobe Experience Manager 6.3. Fornisce funzionalità nuove e migliorate, importanti correzioni di casi segnalati dai clienti, miglioramenti con priorità alta e correzioni di bug generali per migliorare la stabilità del prodotto. Include inoltre la maggior parte di tutti i pacchetti di funzioni, hotfix e service pack  Adobe Experience Manager 6.3.

L&#39;elenco seguente fornisce una panoramica, mentre le pagine successive elencano tutti i dettagli.

### Experience Manager Foundation {#experience-manager-foundation}

Elenco completo delle modifiche apportate in [AEM Foundation](wcm-platform.md).

La piattaforma Adobe Experience Manager 6.4 si basa sulle versioni aggiornate del framework basato su OSGi (Apache Sling e Apache Felix) e del Java Content Repository: Apache Jackrabbit Oak 1.8.2.

Quickstart utilizza Eclipse Jetty 9.3.22 come motore servlet.

#### Interfaccia utente {#user-interface}

Sono stati apportati vari miglioramenti all’interfaccia utente per renderla più produttiva e facile da usare.

* [Nuova barra](/help/sites-authoring/basic-handling.md#content-tree) Struttura contenuto per navigare rapidamente in una gerarchia. In combinazione con la vista a elenco, questo ripristina il modello di interazione Interfaccia classica.
* È stata migliorata l&#39;esperienza di scorrimento nelle viste a schede e a elenco delle cartelle di grandi dimensioni.
* [È stata migliorata l’interazione con i risultati](/help/sites-authoring/search.md) di ricerca: il pulsante Indietro ripristina il risultato della ricerca precedente.
* [Scelte rapide](/help/sites-authoring/keyboard-shortcuts.md)da tastiera aggiuntive, per la maggior parte delle azioni comuni, ad esempio l’apertura di una determinata barra, la modifica, lo spostamento e l’eliminazione di un elemento o l’apertura di proprietà.
* [Possibilità di disabilitare le scelte rapide](/help/sites-authoring/user-properties.md) da tastiera (abilitare/disabilitare in Preferenze).
* [Interrompi la visualizzazione delle marche temporali in tutte le interfacce](/help/sites-authoring/user-properties.md) relative dopo 7 giorni (impostazione predefinita nelle Preferenze).

Per ulteriori informazioni su queste funzioni, consulta la documentazione [sull’](/help/sites-authoring/home.md) authoring.

>[!CAUTION]
>
>Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica. In AEM 6.4 è già inclusa l’interfaccia utente classica e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a usarla normalmente. Nota: l’interfaccia utente classica rimane completamente supportata anche se obsoleta. [Ulteriori informazioni](/help/sites-deploying/ui-recommendations.md).

#### Archivio dei contenuti {#content-repository}

* Compattazione più rapida ed efficiente tramite la pulizia delle revisioni online. I test interni mostrano che la nuova compattazione della coda è fino a 10 volte più veloce e può recuperare più spazio su disco con meno IOPS rispetto a AEM 6.3. Ciò riduce l&#39;impatto sulle prestazioni durante l&#39;esecuzione della pulizia delle revisioni online. Per ulteriori informazioni, consultate [la pagina](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes)della documentazione.

* Pulizia delle revisioni continue per MongoMK sostituisce la manutenzione programmata
* Miglioramento dell&#39;efficienza per la pulizia delle revisioni negli archivi appunti dei documenti

#### Ricerca e indicizzazione {#search-indexing}

* Supporto migliorato per le operazioni di indicizzazione tramite l&#39;interfaccia CLI (Oak Run):

   * Controllo coerenza indice
   * Statistiche di indicizzazione
   * Importazione o esportazione della configurazione indice
   * Reindicizzazione

* Riduzione della crescita del repository correlata a Lucene per un miglioramento generale delle prestazioni del sistema

Per ulteriori informazioni, visitare [questa pagina](/help/sites-deploying/indexing-via-the-oak-run-jar.md)della documentazione.

#### Monitoraggio {#monitoring}

* Una nuova Panoramica [del](/help/sites-administering/operations-dashboard.md#system-overview) sistema fornisce una visualizzazione istantanea su tutte le attività e lo stato del sistema relativi alle prestazioni.
* Un nuovo set di [controlli](/help/sites-administering/operations-dashboard.md#health-checks) dello stato su indicizzazione, query e manutenzione

#### Progetti e flussi di lavoro {#projects-and-workflows}

* Nuovo Editor [flussi di lavoro per creare e modificare modelli](/help/sites-developing/workflows-models.md)di workflow.

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### Aggiornamento dalla versione precedente {#upgrade-from-earlier-version}

* [Compatibilità](/help/sites-deploying/backward-compatibility.md)con versioni precedenti: Le funzioni retrocompatibili di 6.4 consentono di mantenere il codice personalizzato compatibile nella maggior parte dei casi e riducono lo sforzo di aggiornamento.
* [Valutazione](/help/sites-deploying/pattern-detector.md)della complessità dell&#39;aggiornamento: Nuovo strumento di rilevamento dei pattern per valutare la complessità degli aggiornamenti, prima di eseguire l&#39;aggiornamento.
* [Ristrutturazione](/help/sites-deploying/repository-restructuring.md)repository: ristrutturazioni significative (principalmente /etc.) per facilitare gli aggiornamenti e promuovere le migliori pratiche di implementazione
* Per ulteriori informazioni generali sugli aggiornamenti, consultate [questa pagina](/help/sites-deploying/upgrade.md) per ulteriori dettagli.

### Experience Manager - Sites {#experience-manager-sites}

Full list of changes in [AEM Sites and Add-ons](sites.md).

#### Esperienze fluide {#fluid-experiences}

L&#39;introduzione di Esperienze fluide all&#39;inizio del 2017, con il supporto di Frammenti di contenuto, Frammenti esperienza e Content Services, è stata l&#39;inizio di un&#39;evoluzione verso una gestione dei contenuti multi-canale-first. AEM 6.4 estende in modo significativo ciascuna delle aree:

**[Frammenti di contenuto](/help/assets/content-fragments.md)**

La novità di 6.4 è un editor di modelli [di](/help/assets/content-fragments-models.md) contenuto visivo e un nuovo componente [](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/content-fragment-component.html) configurabile per fornire output HTML flessibile e JSON da includere in Content Services.

**Frammenti esperienza**

Grazie alla funzionalità Blocchi predefiniti, la creazione di varianti in un frammento con lo stesso contenuto, ma con layout diversi è ora più efficiente. Oltre a inviare frammenti esperienza a Facebook e Pinterest, ora è possibile inviarli al Adobe Target  come offerta.

**Content Services**

Vari miglioramenti a Sling Model Exporter e ai componenti core sono inclusi per fornire un potente output JSON per incorporare contenuto nelle app mobili e nelle esperienze create con app a pagina singola.

#### Ottenimento Più Rapido Dei Siti {#gettings-sites-built-quicker}

AEM 6.4 completa la trasformazione al modello componente di nuova generazione. Il concetto Componenti di base introdotto in AEM 6.3 e ora unito dal Sistema di stile, fornisce un modo efficiente per creare nuovi ed estendere siti esistenti.

Esercitazione consigliata per apprendere come sfruttare al meglio il nuovo modello di componenti: [Guida introduttiva agli AEM Sites - Esercitazione WKND](https://docs.adobe.com/content/help/it-IT/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

#### Add-on Screens {#screens-add-on}

Trasmettere un messaggio coerente su tutti i canali di marketing, comprese le reti di digital signage e chioschi, è ciò che i AEM Screens rappresentano. AEM 6.4 aggiunge il supporto per l&#39;esecuzione di Signage Player su hardware Microsoft Windows e Google Chrome OS. Sono inoltre disponibili miglioramenti alla gestione e alla programmazione dei dispositivi remoti (gruppi di canali).

Per ulteriori informazioni sugli aggiornamenti di Screens, consulta la Guida [utente](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)AEM Screens.

### Experience Manager - Communities {#experience-manager-communities}

AEM 6.4 aggiunge molte nuove funzioni e miglioramenti a Communities. L’elenco completo delle modifiche è disponibile in [AEM Communities](communities-release-notes.md). I punti salienti di questa versione sono:

#### Miglioramenti alla moderazione {#enhancements-to-moderation}

**Rilevamento automatico dello spam**

È stato fornito un nuovo motore di rilevamento dello spam per filtrare i contenuti generati dagli utenti indesiderati sui siti e sui gruppi della community. Una volta attivato da system/console/configMgr, contrassegna un contenuto generato dall&#39;utente come spam in base a un set predefinito di parole spam. Per ulteriori informazioni sul motore di rilevamento dello spam, consultare [automatizzare i contenuti](/help/communities/moderate-ugc.md#spam-detection)generati dagli utenti della community.

![spamdetection](assets/spamdetection.png)

**Nuovi filtri per QnA**

Nuovi filtri, denominati Risposta non ricevuta, sono stati aggiunti alla console di moderazione collettiva per filtrare le domande QnA. Per sapere come funzionano i filtri di stato Risposte e Senza risposta, fate riferimento al contenuto [generato dall&#39;utente in](/help/communities/moderation.md#main-pars-note-521961797)massa soggetto a moderazione.

**Filtri di moderazione segnalibro**

È stata fornita la possibilità di contrassegnare i filtri di moderazione predefiniti nella console di moderazione. Questi filtri vengono aggiunti alla fine della stringa URL e possono quindi essere condivisi, riutilizzati e rivisitati in un secondo momento. Come contrassegnare i filtri in [blocco nella console](/help/communities/moderation.md#main-pars-note-429176623)di moderazione.

#### Eliminazione di UGC e profili utente {#delete-ugc-and-user-profiles}

AEM 6.4 Communities espone le API [](/help/communities/user-ugc-management-service.md) out-of-the-box e il [servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) di esempio per consentire agli utenti finali di controllare i loro dati. Queste API consentono inoltre alle organizzazioni di elaborazione dati e di controllo dei dati di soddisfare le richieste di conformità ai requisiti GDPR dell&#39;UE.

#### Miglioramenti alla gestione del sito e dei gruppi {#enhancements-to-site-and-group-management}

**Creare gruppi con più impostazioni internazionali in un singolo passaggio**

È stata fornita la possibilità di creare gruppi multilingue in un&#39;unica operazione. Per creare tali gruppi, gli utenti possono passare alla raccolta di gruppi del sito community desiderato dalla console Siti. Create un gruppo e specificate le lingue desiderate nella pagina Modello gruppo community. Per ulteriori informazioni su questa funzionalità, consulta la console [Gruppi](/help/communities/groups.md)community.

![multilingue](assets/multilingualgroup.png)

**[Eliminazione di siti e gruppi community con un clic](/help/communities/groups.md)**

L&#39;icona Elimina ora è disponibile sui rispettivi siti e gruppi, mentre si naviga dalla navigazione globale. Questa icona elimina tutti gli elementi e il contenuto associati al sito o al gruppo e rimuove tutte le associazioni utente. Per ulteriori informazioni su questa funzionalità, consulta [Gestione dei siti](/help/communities/create-site.md#main-pars-text-fe17) community e [Gestione dei gruppi](/help/communities/groups.md#main-pars-text-5e8c)community.

#### Enhancements to Enablement {#enhancements-to-enablement}

Le funzioni Assegnazione e Catalogo sono ora disponibili all&#39;interno dei gruppi. Questo consente di creare, gestire e pubblicare contenuti didattici per un set specifico di membri della community interessati. Per ulteriori informazioni sull&#39;abilitazione di gruppi di community, consulta [Gestione delle risorse](/help/communities/resource.md)di abilitazione.

![assignCatalog](assets/assignmentcatalog.png)

### Experience Manager Assets {#experience-manager-assets}

AEM 6.4 offre diverse nuove funzioni e miglioramenti alle risorse, tra cui nuova integrazione con Creative Cloud, innovazioni fondamentali nell&#39;intelligence artificiale, gestione dei metadati migliorata, miglioramenti nella generazione dei rapporti e miglioramenti generali dell&#39;esperienza utente. Elenco completo delle modifiche disponibili in [AEM Assets](assets.md). I punti salienti della release sono:

**Adobe Asset Link**

 collegamento a risorse di Adobe in Creative Cloud per aziende semplifica la collaborazione tra creativi e professionisti del marketing nel processo di creazione dei contenuti. È una nuova funzionalità nativa di Creative Cloud per enterprise che collega Photoshop CC,  Illustrator CC e  InDesign CC a AEM — senza che i creativi debbano lasciare i loro strumenti di scelta.

Per ulteriori informazioni su questa funzionalità, sui prerequisiti e su come accedervi, consulta Collegamento [risorse](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)Adobe.

![adobe_asset_link](assets/adobe_asset_link.png)

**App desktop AEM**

AEM&#39;app desktop è stata aggiornata alla versione 1.8, compatibile con AEM 6.4. L&#39;elenco completo delle modifiche per AEM app desktop è fornito in un documento dedicato [AEM note](https://docs.adobe.com/content/help/it-IT/experience-manager-desktop-app/using/release-notes.html) sulla versione dell&#39;app desktop.

I miglioramenti introdotti dalla release AEM 6.3 includono la possibilità di caricare cartelle gerarchiche in background, una nuova interfaccia utente per monitorare le operazioni in background delle risorse, il caching migliorato, la rete e il login, nonché miglioramenti generali della stabilità. La documentazione include anche una guida alle [best practice](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html).

**Adobe Sensei Services**

Le nuove funzionalità includono Smart Tags ottimizzati, con la possibilità di apprendere la tassonomia aziendale del cliente, tag automaticamente delle risorse digitali con tag specifici del cliente e Smart Translation Search, che migliora la possibilità di scoprire più lingue traducendo al volo i termini di ricerca. Per ulteriori informazioni su questa funzione, consulta [Tag](/help/assets/enhanced-smart-tags.md)avanzati avanzati.

![Enhanced_smart_tags2](assets/enhanced_smart_tags2.png)

**Metadati**

Diversi miglioramenti includono la possibilità di importare ed esportare simultaneamente metadati per un gran numero di risorse e costrutti di metadati avanzati, come i metadati [Cascading Metadata](/help/assets/cascading-metadata.md).

**Rapporti**

La generazione di rapporti sulle risorse ha subito una grande revisione in AEM 6.4 con un nuovo framework di reporting, un&#39;esperienza utente e più rapporti OOOTB per i casi di utilizzo da parte dei clienti. Per informazioni su come generare vari rapporti, consultate Rapporti sulle [risorse](/help/assets/asset-reports.md).

**Esperienza utente**

Numerosi miglioramenti per migliorare l’esperienza di navigazione, ricerca e amministrazione per gli utenti di Risorse, ad esempio esperienza di scorrimento, pulsante di ricerca indietro, filtri di ricerca migliorati e molto altro ancora. Elenco completo disponibile in [AEM Assets](assets.md).

**Brand Portal**

Diversi miglioramenti in aree quali metadati, reporting, diritti digitali, esperienza di accesso e prestazioni di pubblicazione per la distribuzione delle risorse. Per informazioni sui nuovi miglioramenti e funzionalità, consulta [Novità di AEM Assets Brand Portal](https://docs.adobe.com/content/help/it-IT/experience-manager-brand-portal/using/introduction/whats-new.html).

#### Dynamic Media Add-on {#dynamic-media-add-on}

AEM 6.4 include molte nuove funzioni e miglioramenti ad Dynamic Media. L’elenco completo è disponibile in [AEM Assets](assets.md). I principali elementi di rilievo sono i seguenti:

**Ritaglio avanzato**

Smart Crop, basato su  Adobe Sensei, fornisce automaticamente il ritaglio non distruttivo delle immagini, mantenendo il punto di interesse per un design reattivo. Potete visualizzare in anteprima i suggerimenti per le immagini ritagliate e, se necessario, regolarli manualmente. Questa funzione consente anche la generazione automatizzata dei campioni per le immagini dei prodotti.

Per ulteriori informazioni sull’utilizzo di Smart Crop, consultate la documentazione [sui profili](/help/assets/image-profiles.md) immagine.

Consultate [Aggiunta di risorse Dynamic Media alle pagine](/help/assets/adding-dynamic-media-assets-to-pages.md) per ulteriori informazioni sull’utilizzo di Smart Crop nel componente Dynamic Media.

**Imaging avanzato**

La tecnologia di imaging intelligente sfrutta le caratteristiche di visualizzazione esclusive di ogni utente per distribuire automaticamente le immagini ottimizzate per la propria esperienza, migliorando le prestazioni e il coinvolgimento.

Per ulteriori informazioni, consulta la documentazione [sulle immagini](/help/assets/imaging-faq.md) intelligenti.

![smart_crop](assets/smart_crop.png)

**Miglioramenti a supporti e visualizzatori emergenti**

I nuovi visualizzatori, inclusi Panorama e VR, consentono di offrire esperienze più coinvolgenti.

Per ulteriori informazioni, consulta [Documentazione sulle immagini](/help/assets/panoramic-images.md) panoramiche.

**Risorse 3D**

Nuova integrazione con [Adobe Dimension CC](https://www.adobe.com/products/dimension.html), un&#39;applicazione di Creative Cloud per la creazione di esperienze 3D.

Per ulteriori informazioni, consulta [Utilizzo della documentazione sulle risorse](/help/assets/assets-3d.md) 3D.

![do-not-localize/3d](assets/do-not-localize/3d.png)

### Experience Manager Forms {#experience-manager-forms}

AEM 6.4 Forms offre diverse nuove funzioni e miglioramenti. Le caratteristiche principali sono:

* Comunicazioni interattive multicanale
* Precompila comunicazioni interattive dalle applicazioni aziendali
* Modernizzazione dei flussi di lavoro e supporto per i lavoratori mobili
* Frammenti di caricamento pigri
* Aggiornamento single-hop da LiveCycle a  Experience Manager Forms 6.4

Maggiori dettagli sulla pagina delle note sulla versione [AEM Forms](forms.md) . Also, see the [Summary of new features and enhancements in AEM 6.4 Forms](/help/forms/using/whats-new.md) for information about new and improved features and documentation resources.

### Experience Manager - Livefyre {#experience-manager-livefyre}

Puoi integrare Livefyre con l’istanza di AEM 6.4. Le informazioni su come integrare Livefyre con AEM si trovano qui:

* [Integrazione di Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)

### Sfruttare lo sviluppo incentrato sul cliente {#leverage-customer-focused-development}

Adobe utilizza un modello di sviluppo incentrato sul cliente che consente ai clienti di contribuire a tutte le fasi del processo di sviluppo, per le specifiche, lo sviluppo e il testing. Il nostro ringraziamento va a tutti i clienti e partner che hanno contribuito a questo processo.

Adobe dispone delle procedure e dei processi necessari a consentire la raccolta, la definizione delle priorità e il monitoraggio della risoluzione dei bug incentrati sul cliente e dello sviluppo delle richieste di miglioramento. The [Adobe Marketing Cloud Support Portal](https://helpx.adobe.com/it/contact/enterprise-support.ec.html) is integrated with the Adobe Enhancement &amp; Defect Tracking System. Ove possibile, le domande dei clienti vengono identificate e risolte dall’Assistenza clienti. Quando è necessario passarle al reparto R&amp;D, tutte le informazioni sui clienti vengono acquisite e utilizzate per stabilire le priorità e a scopo di reportistica. Nello sviluppo viene data priorità ai casi di assistenza a pagamento, garanzia e ai miglioramenti proposti da clienti con licenze a pagamento.

Grazie a questo processo di prioritizzazione, in AEM 6.4 sono stati risolti oltre 500 cambiamenti incentrati sul cliente.

## Elenco dei file che fanno parte della versione {#list-of-files-that-are-part-of-the-release}

**Foundation**

* Quickstart autonomo: cq-quickstart-6.4.0.jar
* Avvio rapido server applicazioni: cq-quickstart-6.4.0.war
* Dispatcher 4.3.1 o versione successiva per vari server e piattaforme Web. Consulta [collegamento](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)per il download.
* Plug-in for Eclipse IDE. [Read more and download](/help/sites-developing/aem-eclipse.md).

* Extension for Brackets Code Editor. [Read more and download](/help/sites-developing/aem-brackets.md).
* Dipendenze Paradiso/Gradle. Consulta [collegamento](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/)per il download.

**Sites**

* Componenti core ([progetto GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components))
* Implementazione di riferimento We.Retail ([informazioni](/help/sites-developing/we-retail.md))
* Project Blueprint Archetype (progetto[](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)GitHub)
* Lettori AEM Screens per varie piattaforme di destinazione ([download](https://download.macromedia.com/screens/))
* Modelli lingua per contenuti avanzati. L’inglese è preinstallato, è possibile scaricare altre lingue

   * [Tedesco](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spagnolo](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italiano](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Francese](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [Strumento](/help/sites-developing/dialog-conversion.md) di conversione della finestra di dialogo per migrare i componenti dell’interfaccia classica in Coral 3

**Assets**

*  app desktop di Adobe Experience Manager ([per saperne di più](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) e per [scaricare](https://docs.adobe.com/content/help/it-IT/experience-manager-desktop-app/using/release-notes.html))

* Package to add enhanced PDF Rasterizer ([read more](/help/assets/aem-pdf-rasterizer.md) and [download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg))

* Pacchetto per aggiungere il supporto esteso per le immagini RAW ([ulteriori informazioni](/help/assets/camera-raw.md))

**Forms**

* Pacchetti per le funzionalità di AEM Forms:

   * [adobe-aemfd-aix-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-AIX)
   * [adobe-aemfd-linux-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-LX)
   * [adobe-aemfd-solaris-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-SOL)
   * [adobe-aemfd-win-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-WIN)
   * [adobe-aemfd-osx-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-OSX)

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

Per i requisiti di configurazione, consulta le [istruzioni di installazione](/help/sites-deploying/custom-standalone-install.md). 

Per istruzioni dettagliate, consulta la [documentazione di aggiornamento.](/help/sites-deploying/upgrade.md)

## Piattaforme supportate {#supported-platforms}

La matrice completa delle piattaforme supportate, incluso il livello di supporto, è riportata nei [Requisiti tecnici di AEM 6.4](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Oracle è passato al modello “Long Term Support” (LTS) per i prodotti Oracle Java SE. Java 9 and 10 are non-LTS releases by Oracle (see [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe fornirà supporto solo per le versioni LTS di Java per l’esecuzione di AEM in ambienti di produzione. Si consiglia quindi di utilizzare Java 8 con AEM 6.4.

## Funzioni obsolete e rimosse {#deprecated-and-removed-features}

Adobe valuta costantemente le funzionalità del prodotto e, nel tempo, pianifica di sostituire le funzionalità con versioni più potenti, oppure decide di reimplementare specifiche parti per una migliore preparazione a eventuali estensioni future.

Per Adobe Experience Manager 6.4, [leggi l’elenco delle funzionalità obsolete e rimosse](deprecated-removed-features.md). La pagina contiene anche un pre-annuncio delle modifiche nel 2019 e un importante avviso per i clienti che si aggiornano da versioni precedenti.

## Elenchi delle modifiche dettagliate {#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[AEM Communities](communities-release-notes.md)

[AEM Forms](forms.md)

[AEM Foundation](wcm-platform.md)

## Problemi noti {#known-issues}

[Elenco dei problemi noti](known-issues.md)

### Download e supporto del prodotto (siti con limitazioni) {#product-download-and-support-restricted-sites}

Questi siti sono disponibili solo per i clienti. Se sei un cliente e hai bisogno di accedere, contatta il manager del tuo account Adobe.

* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/).
* Aggiornamenti dei prodotti, patch e pacchetti per funzionalità aggiuntive sulla distribuzione [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)software.
* [Assistenza clienti tramite  Admin Console](https://adminconsole.adobe.com/). Per ulteriori informazioni, consulta [Nuova esperienza](https://docs.adobe.com/content/help/en/customer-one/using/home.html)di assistenza clienti  Adobe.
