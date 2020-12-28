---
title: AEM domande frequenti
seo-title: AEM 6.4 domande frequenti
description: Utilizzate queste domande frequenti per comprendere, configurare e risolvere i flussi di lavoro o i problemi più comuni in AEM.
seo-description: Utilizzate queste domande frequenti per comprendere, configurare e risolvere i flussi di lavoro o i problemi più comuni in AEM.
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---


# AEM FAQ{#aem-faqs}

Seguite questa pagina per trovare le risposte ad alcuni AEM problemi di risoluzione dei problemi e configurazione.

## Sites {#sites}

### Come si configura la distribuzione senza binario? {#how-do-i-configure-binary-less-distribution}

La distribuzione senza binario è supportata per le distribuzioni su un archivio dati condiviso e coinvolge gli agenti che sfruttano l&#39;esportatore di pacchetti di distribuzione basato su Vault (PID di fabbrica: Generatore di pacchetti `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`).

Se la modalità binaria è attivata, i pacchetti di contenuto distribuiti contengono riferimenti a file binari anziché ai file binari effettivi.

### Come si abilita la distribuzione senza binario? {#how-do-i-enable-binary-less-distribution}

Per abilitare la distribuzione binaria, distribuisci con uno store BLOB condiviso.\
Controllare la proprietà `useBinaryReferences` nella configurazione OSGI con il PID di fabbrica ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* utilizzato dall&#39;agente.

### Come è possibile personalizzare i messaggi di errore durante la navigazione nella gerarchia delle pagine AEM console Siti? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Controllare il pannello Rete (del browser Chrome) dove una configurazione personale (JS non è stata ridotta).

Visualizzate la colonna `Initiator` per determinare quale sia stato l&#39;iniziatore di una richiesta. Fornisce i file e i numeri di riga da cui vengono effettuate le chiamate AJAX. Successivamente, è possibile tracciare la funzione di gestione degli errori e modificare il messaggio di errore in base alle proprie esigenze.

### Come abilitare le autorizzazioni durante la creazione di una copia della lingua per gli autori di contenuti in AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Per creare la funzione di copia per lingua, gli autori dei contenuti devono disporre delle autorizzazioni nel percorso `/content/projects`.

Se uno richiede che gli autori gestiscano anche i progetti, la soluzione consiste nell&#39;aggiungere l&#39;autore al gruppo `project-administrators`.

### Come modificare il formato durante la creazione di una copia della lingua per un progetto? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Prima di creare un progetto di traduzione, create una copia radice della lingua e della lingua all’interno della directory principale.

Esempio,\
Create una radice della lingua in `/content/geometrixx` con il nome `fr_LU` (e il titolo in francese (Lussemburgo). Successivamente, creare una copia della lingua della pagina dal pannello dei riferimenti e passare all&#39;opzione `Create structure only` in `Create & Translate`. Infine, create un progetto di traduzione e aggiungete la copia per lingua al processo di traduzione.

Per informazioni dettagliate, consultate le risorse aggiuntive riportate di seguito:

* [Preparazione del contenuto per la traduzione](/help/sites-administering/tc-prep.md)
* [Gestione dei progetti di traduzione](/help/sites-administering/tc-manage.md)

### Come controllare AEM funzionalità come tentativi di accesso e modifiche di ACL o autorizzazioni? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM ha introdotto la possibilità di registrare le modifiche amministrative per migliorare la risoluzione dei problemi e il controllo. Per impostazione predefinita, le informazioni vengono registrate nel file `error.log`. Per semplificare il monitoraggio, si consiglia di reindirizzarli a un file di registro separato.\
Per reindirizzare l&#39;output a un file di registro separato, vedere [Come controllare le operazioni di gestione degli utenti in AEM](/help/sites-administering/audit-user-management-operations.md).

### Come abilitare SSL per impostazione predefinita? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 viene fornito con la procedura guidata SSL e offre un&#39;interfaccia utente per configurare il supporto SSL Jetty e Granite Jetty.

Per abilitare SSL per impostazione predefinita, vedere [SSL per impostazione predefinita](/help/sites-administering/ssl-by-default.md).

### Qual è l&#39;architettura consigliata quando si utilizzano i Content Services di AEM da un&#39;app mobile, React Native (Reazione nativa) idealmente? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Content Services si basa sui modelli Sling e gli sviluppatori AEM devono fornire un pojo Sling Model per ciascun componente esportato.

Per informazioni su come utilizzare AEM servizi di contenuto da un&#39;applicazione React, vedere l&#39;esercitazione [Guida introduttiva a AEM Content Services](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html).

Inoltre, se gli sviluppatori desiderano esportare una struttura di componenti, possono implementare anche le interfacce `ComponentExporter` e `ContainerExporter`, nonché utilizzare l&#39;interfaccia `ModelFactory` per iterare sui componenti secondari e restituire la rappresentazione del modello. Consulta le risorse seguenti:

[1] [ Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2 ] [Apache Sling :: Modelli Sling](https://sling.apache.org/documentation/bundles/models.html)

### Come disattivare AEM sondaggio popup 6.4? {#how-to-disable-aem-survey-pop-up}

È possibile scegliere di utilizzare la raccolta delle statistiche di utilizzo utilizzando l&#39;interfaccia utente touch o la console Web. Per istruzioni dettagliate, vedere [Scelta nella raccolta delle statistiche di utilizzo aggregate](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

### Esiste una buona risorsa che evidenzia le caratteristiche chiave per l&#39;aggiornamento a AEM 6.4? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Fare riferimento a [I motivi dell&#39;aggiornamento AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) che descrive la suddivisione di alto livello delle funzioni chiave per i clienti che considerano l&#39;aggiornamento all&#39;ultima versione di Adobe Experience Manager.

### Come configurare un&#39;istanza AEM per l&#39;utilizzo del filtro PorterStem? {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

Il filtro PorterStem applica l’algoritmo Porter Stemming per l’inglese. I risultati sono simili all&#39;utilizzo di Snowball Porter Stemmer con l&#39;argomento *language=&quot;English&quot;*. Ma questo stemmer è codificato direttamente in Java e non è basato su Snowball. Non accetta un elenco di parole protette ed è appropriato solo per il testo in lingua inglese.

Oak espone una serie di elementi di configurazione dell&#39;analizzatore di tipo lucene da usare in AEM. Per informazioni sull&#39;utilizzo dei filtri, fare riferimento a **Apache Oak Analyzers** in [Guida all&#39;implementazione della ricerca semplice](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

### Come eseguire una reindicizzazione completa? {#how-to-perform-a-full-re-indexing}

La reindicizzazione deve sempre essere affrontata con la dovuta considerazione per il suo impatto sulle prestazioni complessive AEM, ed eseguita durante i periodi di attività o finestre di manutenzione ridotte.

Fare riferimento alle [Best practice per query e indicizzazione](/help/sites-deploying/best-practices-for-queries-and-indexing.md) per comprendere i motivi della reindicizzazione.

### Supportiamo librerie JS ridotte in Importazione progettazione? {#do-we-support-minified-js-libs-in-design-importer}

È necessario modificare la proprietà di configurazione predefinita del processore JS del Adobe  Granite HTML Library Manager in ***min:gcc***. Per importare correttamente il pacchetto di progettazione, si consiglia di includere librerie di terze parti preminenti nelle librerie lato client.

## Assets {#assets}

### Perché il flusso di lavoro Risorse si ripete durante il caricamento di file MP4 (ad esempio, tramite trascinamento)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Se l’utente carica i file del filmato non dispone delle autorizzazioni di eliminazione nel nodo della risorsa, i nodi dei blocchi eliminati non riescono e il caricamento viene riavviato.

### Qual è il numero massimo di risorse digitali utilizzabili con AEM 6.4 alla volta? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager (AEM) 6.4 attualmente consente di caricare fino a 2 GB di risorse alla volta.

Per ulteriori informazioni sul numero massimo di risorse utilizzabili con AEM 6.4, vedere [Guida alle dimensioni delle risorse](/help/assets/assets-sizing-guide.md).

### Quali sono le impostazioni predefinite per le configurazioni OOOTB durante la creazione di una copia lingua? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Durante la creazione di copie della lingua nell’interfaccia classica, le risorse non vengono spostate sotto la nuova gerarchia di lingue ma utilizzate dal master della lingua.

Mentre, quando create una copia della lingua tramite l&#39;interfaccia utente touch (**References** -> **Update Language Copy**), viene creata una nuova cartella DAM nella nuova lingua e da tale cartella si fa riferimento alle risorse.

Questa è l&#39;impostazione predefinita per le configurazioni OOTB. È possibile impostare **Traduci risorse pagina** = **Non tradurre** nelle configurazioni di traduzione.\
Per AEM 6.4, **Strumenti** > **Cloud Services** > **Servizi di Translation Cloud**.

### Come disattivare un componente AEM che causa una crescita esponenziale per il AEM SegmentStore (AEM 6.3.1.1)? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

È possibile disattivare il Disabler dei componenti OSGi. Per utilizzare questo servizio, vedere [Disabler componente OSGi](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Per risolvere il problema, potete anche disattivare manualmente il componente tramite l&#39;interfaccia utente o mediante un comando `curl` (ad esempio di seguito), dopo ogni AEM riavvio.

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### Come configurare Asset Insights con AEM 6.4 instance? {#how-to-configure-asset-insights-with-aem-instance}

Per impostare e configurare approfondimenti delle risorse per  Experience Manager distribuito tramite attivazione  Adobe (DTM), consultare [Configurare approfondimenti delle risorse con  AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

### Come personalizzare le console di amministrazione? {#how-to-customize-admin-consoles}

AEM offre diversi metodi per personalizzare le console e la funzionalità di authoring delle pagine dell’istanza di authoring.
Per informazioni su come creare una console personalizzata e personalizzare una visualizzazione predefinita per una console, vedere [Personalizzazione delle console](/help/sites-developing/customizing-consoles-touch.md).

### Qual è la differenza tra i componenti basati su CoralUI 2 e CoralUI 3? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Per Coral3 viene creato un nuovo set di componenti Sling di Granite UI Foundation, situato in [/libs/granite/ui/components/coral/foundation.](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) È disponibile un set per i componenti basati su CoralUI 2 e uno per i componenti basati su CoralUI 3. Il nuovo set non sarà solo una copia-incolla del set precedente, ma verrà anche ripulito (ad esempio, snellimento, rimozione della funzione obsoleta). È quindi consigliabile che una pagina utilizzi solo il set basato su CoralUI 3 o CoralUI 2 basato su CoralUI.

Per ulteriori informazioni, fare riferimento alla [Guida alla migrazione a CoralUI 3-based](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

### Come personalizzare il componente di ricerca in  AEM Assets? {#how-to-customize-the-search-component-in-aem-assets}

Per ulteriori informazioni sull&#39;incremento/classificazione della ricerca e ulteriori informazioni sull&#39;implementazione, fare riferimento a [Guida all&#39;implementazione della ricerca semplice.](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

L&#39;implementazione semplice della ricerca sono i materiali del laboratorio Summit 2017 AEM Search Demystified.

### Se un cliente acquista solo la licenza Site in AEM, può comunque accedere alle Risorse? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

No, il cliente non può accedere a Risorse (o a qualsiasi altra risorsa diversa da Siti). Anche se tutti i componenti di Adobe Experience Manager (AEM) in sede sono inclusi nella JAR, il cliente è autorizzato ad accedere solo ai componenti della JAR per i quali è stato concesso il permesso nel contratto. Se desiderano esplorare altri componenti, possono utilizzare il programma di prova AEM per un massimo di 45 giorni oppure firmare un ordine di vendita di $ 0 che consente loro di valutare (nessun utilizzo in produzione) componenti denominati come Risorse.

Per ulteriori informazioni su AEM software locale e servizi gestiti Adobe, consultare le risorse seguenti:

* [Software Adobe Experience Manager locale](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### Come può un cliente estendere le proprietà predefinite di una pagina o di una risorsa? {#how-to-extend-default-properties-page-or-asset}

Per informazioni sull’estensione delle proprietà predefinite di una pagina o di una risorsa, consulta le risorse seguenti:

* [Schemi di metadati nelle risorse](/help/assets/metadata-schemas.md)
* [Personalizzazione delle visualizzazioni delle proprietà pagina](/help/sites-developing/page-properties-views.md)
