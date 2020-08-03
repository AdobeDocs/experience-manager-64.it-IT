---
title: Note sulla versione di AEM Assets
seo-title: AEM Assets
description: Note sulla versione specifiche per  Adobe Experience Manager 6.4 Assets.
seo-description: Note sulla versione specifiche per  Adobe Experience Manager 6.4 Assets.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 2%

---


# Note sulla versione di AEM Assets {#aem-assets-release-notes}

Le funzioni chiave, le evidenziazioni e i miglioramenti effettuati in AEM 6.4 Assets sono trattati in queste note sulla versione. Per informazioni dettagliate, seguite i collegamenti forniti.

## Adobe Asset Link {#adobe-asset-link}

 collegamento a risorse di Adobe in Creative Cloud per aziende semplifica la collaborazione tra creativi e professionisti del marketing nel processo di creazione dei contenuti. È una nuova funzionalità nativa in Creative Cloud per l&#39;azienda, che fornisce una connessione ad AEM Assets direttamente da  Adobe Photoshop,  Adobe Illustrator o  Adobe InDesign — senza lasciare questi strumenti.

Per ulteriori informazioni su funzionalità, prerequisiti e come accedervi, consultate la pagina Collegamento [risorse](https://helpx.adobe.com/it/enterprise/using/adobe-asset-link.html) Adobe.

## Smart tag avanzati avanzati (basati su  Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 introduce la funzionalità di intelligenza artificiale basata su Smart Tags Enhanced in aggiunta ai Smart Tags lanciati in AEM 6.3.

* Smart Content Service apprende la tassonomia aziendale dei clienti e la utilizza per assegnare automaticamente tag alle risorse digitali con tag pertinenti ai clienti oltre a tag generici. Migliora in modo significativo la reperibilità delle attività e riduce il tempo sul mercato.
*  Adobe Sensei potenzia Smart Content Service, che consente di formare l&#39;algoritmo di riconoscimento delle immagini nella tassonomia aziendale. Questa funzione di content intelligence viene quindi utilizzata per applicare tag rilevanti a risorse simili.

Per utilizzare AEM Assets Smart Tags avanzati avanzati, installare il service pack [più recente di AEM 6.4](https://helpx.adobe.com/it/experience-manager/aem-releases-updates.html).

## Ricerca di traduzione intelligente (con  Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 introduce la funzionalità Smart Translation Search per supportare scenari di ricerca multilingue. I clienti con team distribuiti a livello globale in più lingue ora possono effettuare ricerche in diverse lingue senza dover affrontare flussi di lavoro di traduzione costosi e lunghi.

* La query di ricerca viene tradotta senza intervento manuale.
* I tag avanzati vengono generati in inglese e tradotti automaticamente in altre lingue.
* La ricerca multilingue è realizzata utilizzando la libreria open source Apache Joshua che supporta più di 50 lingue.

## Esperienza utente {#user-experience}

AEM 6.4 offre significativi miglioramenti all&#39;esperienza utente in aree quali ricerca, ricerca, risorse multipagina e strumenti di amministrazione. Dettagli di seguito:

Miglioramenti alla navigazione

* Nuova barra ad albero del contenuto per navigare rapidamente in una gerarchia di risorse. In combinazione con la vista a elenco, questo ripristina il modello di interazione Interfaccia classica per la ricerca delle gerarchie di risorse.
* Nuove scelte rapide da tastiera come m per spostare le risorse, p per aprire la pagina delle proprietà, Ctrl + C per copiare l&#39;operazione e molto altro ancora.
* È stata migliorata l&#39;esperienza di scorrimento e caricamento lento nelle viste a schede e a elenco per la navigazione in un gran numero di risorse.
* Vista a schede migliorata con il supporto per schede di diverse dimensioni in base all&#39;impostazione della vista.
* Esperienza di dettaglio delle risorse migliorata con la possibilità di visualizzare, passare alla risorsa &quot;precedente&quot; o &quot;successiva&quot; e al numero di risorse correnti.

Miglioramenti alla ricerca

* Nuovo pulsante Ricerca indietro con la possibilità di passare a un elemento di ricerca e tornare alla stessa posizione nei risultati della ricerca senza eseguire nuovamente la query di ricerca.
* Conteggio dei nuovi risultati della ricerca per visualizzare il numero di risultati della ricerca.
* È stato migliorato il filtro di ricerca per i tipi di file con la possibilità di filtrare i risultati di ricerca in base a tipi di mime con granulosità fine come JPG, PNG e PSD, rispetto alle opzioni precedenti per immagini, documenti e contenuti multimediali.
* Sono stati migliorati i filtri di ricerca con marche temporali precise invece della funzionalità del cursore tempo precedente.

Miglioramenti alle risorse multipagina

* Esperienza di navigazione delle risorse multipagina migliorata con un numero ridotto di clic.
* Migliorato il supporto di commenti e annotazioni con tutti i commenti raccolti a livello di risorsa anziché a livello di pagina.

Miglioramenti agli strumenti di amministrazione

* È stato migliorato il selettore delle proprietà negli strumenti di amministrazione per metadati, ricerche e rapporti con funzionalità di navigazione e navigazione per semplificare l’esperienza di amministrazione.

Cataloghi

* Esperienza utente migliorata, allineamento con l&#39;interfaccia utente Templates. Per ulteriori informazioni, consultate [Catalog Producer](../sites-administering/catalog-producer.md).

## Metadati {#metadata}

AEM 6.4 offre diverse funzionalità avanzate per la gestione dei metadati, che consentono di gestire i metadati su larga scala e di garantire l&#39;integrità dei metadati attraverso regole e convalide. Le funzionalità principali sono le seguenti:

* Nuova funzionalità di esportazione in blocco di metadati per esportare (tutti, selettivi) metadati per un numero elevato di risorse in formato CSV per la modifica, la condivisione e l’integrazione con terze parti.
* Nuova funzionalità di importazione di metadati in blocco per importare file CSV per l’aggiunta di nuovi metadati, aggiornando i metadati esistenti per più risorse in un solo passaggio. Questa operazione è asincrona e non ostacola le prestazioni del sistema. Una volta completato, l&#39;utente riceve una notifica tramite AEM sistema di notifica.
* Nuovi metadati concatenati e contestuali mediante lo strumento Schema metadati. È ora possibile definire catene di dipendenze e mappature dei valori tra i campi. È inoltre possibile definire il contesto in cui i campi dei metadati vengono visualizzati o nascosti. In questo modo, è possibile visualizzare solo i campi pertinenti in qualsiasi momento, a seconda dei valori presenti in altri campi.

## Rapporti {#reports}

AEM 6.4 offre significativi miglioramenti nella generazione dei rapporti sulle risorse:

* Nuovo framework di report scalabile (per repository di grandi dimensioni) a livello aziendale che applica processi Sling per l&#39;elaborazione asincrona delle richieste di report. Puoi pianificare il rapporto in una data e in un&#39;ora specifiche. È inoltre possibile aggiungere colonne personalizzate a un rapporto.
* I nuovi report OOTB più comunemente richiesti dai clienti, come Uso del disco, File, Condivisione collegamenti, Pubblica sul portale dei marchi e Formazione smart tag.
* Nuova interfaccia utente per la creazione e la gestione di report con opzioni precise, possibilità di accedere ai report archiviati, stato di esecuzione dei report (success, fail, queue e così via).

## Brand Portal {#brand-portal}

* **6.3 Aggiornamento** Platform: Portale marchio aggiornato da AEM 6.0 a AEM 6.3, con nuove funzioni e miglioramenti delle prestazioni.
* **Pubblicazione** parallela: Possono verificarsi fino a repliche tra AEM Assets e Brand Portal (precedentemente 1), il che migliora notevolmente le prestazioni di pubblicazione
* **Pubblicazione** Facet di schema e ricerca: Possibilità di pubblicare schemi di metadati e facet di ricerca personalizzati in Brand Portal, eliminando la duplicazione degli sforzi.
* **Pubblicazione** tag di massa: Possibilità di pubblicare tassonomia (insieme alla gerarchia) in Brand Portal, eliminando la duplicazione degli sforzi.
* **Accesso** autonomo o richiesta di accesso: Flusso di lavoro per utenti non registrati al Brand Portal.
* **Notifica** di manutenzione in-app (sullo schermo): Le notifiche vengono visualizzate con largo anticipo per evitare interruzioni nell&#39;attività.
* **Miglioramenti** del reporting: Sono disponibili tre report OOTB: download, pubblicazione e condivisione di collegamenti.
* **Limitazioni** basate su DRM: Una volta scaduta una risorsa con licenza, non sarà più disponibile per il download dal Brand Portal.

## App desktop AEM {#aem-desktop-app}

AEM&#39;app desktop viene aggiornata alla versione 1.8, compatibile con AEM 6.4. L&#39;elenco completo delle modifiche per AEM app desktop è fornito in un documento dedicato [AEM note](https://docs.adobe.com/content/help/it-IT/experience-manager-desktop-app/using/release-notes.html) sulla versione dell&#39;app desktop.\
Di seguito è riportato un elenco AEM evidenziazioni delle app desktop dal rilascio di AEM 6.3:

* Possibilità di caricare cartelle gerarchiche in background.
* Interfaccia utente per monitorare i caricamenti delle risorse in background.
* Miglioramenti nella cache, inclusa un&#39;interfaccia per gestire i parametri di memorizzazione nella cache.
* Supporto più ampio per AEM configurazioni di autenticazione (SAML/SSO) e proxy di rete.
* Supporto: accesso facilitato ai registri dall&#39;interfaccia utente.
* Miglioramento della stabilità e delle correzioni per i problemi dei clienti.

Per un accesso più semplice alla documentazione e alle procedure ottimali, è disponibile la seguente documentazione:

* [Guida](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)utente, destinata agli utenti finali che utilizzano l’applicazione.
* [Guida](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/install-upgrade.html)all&#39;installazione, destinata agli amministratori che configurano AEM e AEM app desktop per lavorare insieme

## Storage su più livelli {#tiered-storage}

AEM 6.4 include una serie di funzioni che supportano diverse preferenze di storage su più livelli e implementano le regole del ciclo di vita. Le opzioni di archiviazione supportano anche (ma non sono limitate) cloud pubblici - AWS o Azure.

* Possibilità per gli utenti di selezionare e successivamente modificare la classe di storage a piacimento e definire regole per l&#39;archiviazione delle risorse da una classe all&#39;altra o gestire il ciclo di vita delle risorse.
* Possibilità per gli utenti di ridurre i costi di archiviazione selezionando un&#39;altra AWS o Azure.

Per una panoramica delle piattaforme supportate, consulta la Documentazione [sui requisiti](../sites-deploying/technical-requirements.md)tecnici.

## Gruppo utenti chiuso {#closed-user-group}

* In AEM 6.4, il gruppo di utenti chiuso o il gruppo di utenti chiuso consentono di limitare l’accesso alle cartelle nell’istanza di pubblicazione. È un’opzione dell’interfaccia touch per aggiungere entità tramite la pagina delle proprietà delle cartelle a livello di cartella e vengono applicate a tutte le cartelle e sottocartelle/risorse all’interno.
* In modalità di pubblicazione, se un gruppo di utenti chiuso è configurato e l’autorizzazione è abilitata in una cartella, gli utenti vengono reindirizzati a una pagina di accesso quando tentano di accedere alla cartella. Pertanto, gli utenti autorizzati possono accedere alla cartella e alle relative risorse solo dopo l’accesso. Pertanto, CUG limita l’accesso in lettura a una determinata struttura nell’archivio dei contenuti per tutti gli utenti tranne le entità selezionate.

## Dynamic Media add-on {#dynamic-media-add-on}

Dynamic Media in 6.4 supporta una nuova modalità, in cui le risorse master vengono caricate e gestite con l’interfaccia Web dei AEM Assets, mentre le rappresentazioni dinamiche e altre funzioni per i contenuti multimediali dinamici vengono gestite in background dal servizio di distribuzione cloud di Dynamic Media.

In questa modalità (introdotta per prima cosa con il rilascio di [AEM 6.3 Feature Pack 14410 e 18912](https://helpx.adobe.com/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), gli utenti beneficiano della gestione delle risorse end-to-end e delle funzioni per contenuti multimediali dinamici utilizzando l&#39;interfaccia utente Web AEM Assets moderna e sfruttando i servizi di consegna che sono compatibili con Dynamic Media Classic (Scene7), inclusi gli URL di consegna, che non subiscono modifiche.

Inoltre, AEM 6.4 introduce nuove funzioni con tecnologia  Adobe Sensei, miglioramenti per contenuti multimediali emergenti come VR e 3D, visualizzatori Dynamic Media e supporto per frammenti esperienza in immagini interattive e banner carosello.

### Smart Crop (alimentato da  Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* Smart Crop consente automaticamente il ritaglio non distruttivo delle immagini per mantenere il punto di interesse del design reattivo. Potete visualizzare in anteprima i suggerimenti ritagliati e, se necessario, modificarli manualmente.
* Questa funzione consente anche la generazione automatizzata dei campioni per le immagini dei prodotti. La generazione automatizzata dei campioni consente di aggiungere automaticamente campioni colore, campioni di pattern o entrambi alle immagini del prodotto.

Per ulteriori informazioni, consulta la documentazione [sui profili](../assets/image-profiles.md) immagine.

Consultate anche la documentazione [Aggiunta di risorse Dynamic Media alle pagine](../assets/adding-dynamic-media-assets-to-pages.md) per ulteriori informazioni sull’utilizzo di Smart Crop con il componente Dynamic Media.

### Imaging avanzato {#smart-imaging}

* La tecnologia di imaging intelligente sfrutta le caratteristiche di visualizzazione esclusive di ogni utente per distribuire automaticamente le immagini ottimizzate per la propria esperienza, migliorando le prestazioni e il coinvolgimento.
* Le immagini vengono automaticamente convertite in formati diversi in base alle funzionalità del browser.
* Le impostazioni di qualità delle immagini vengono determinate nel browser e applicate rispettivamente. Questa funzionalità consente di mantenere le prestazioni di caricamento delle immagini accettabili per larghezza di banda limitata e velocità di connessione ridotte.

Per ulteriori informazioni, consulta la documentazione [sulle immagini](../assets/imaging-faq.md) intelligenti.

### Miglioramenti per contenuti multimediali e visualizzatori emergenti {#emerging-media-amp-viewer-enhancements}

* Sono supportati nuovi visualizzatori, che offrono agli utenti esperienze più coinvolgenti e di migliore qualità.
* Il visualizzatore panoramico consente di interagire con l’utente e offre la possibilità di sperimentare meglio scene, proprietà, posizioni e paesaggi delle stanze. Per ulteriori informazioni, consulta [Documentazione sulle immagini](../assets/panoramic-images.md) panoramiche.

* Il visualizzatore VR offre un’esperienza completa su proprietà, posizioni e paesaggi.
* Visualizzatore di immagini verticali ottimizzato per le immagini dei prodotti.
* Miglioramenti dell&#39;accessibilità della tastiera.

### 3D e integrazione con Dimension CC {#d-and-integration-with-dimension-cc}

È stata introdotta l&#39;integrazione con [Adobe Dimension CC](https://www.adobe.com/products/dimension.html) per un flusso di lavoro 3D più semplice. Per ulteriori informazioni, consulta [Utilizzo della documentazione delle risorse](../assets/assets-3d.md) 3D.
