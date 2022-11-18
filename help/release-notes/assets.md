---
title: Note sulla versione di AEM Assets
seo-title: AEM Assets
description: Note sulla versione specifiche di Adobe Experience Manager 6.4 Assets.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Assets.
uuid: f5e7608d-f906-4a35-b442-899703de3587
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 397b3267-1437-4263-963c-9d68ccc928ab
exl-id: 3f2cb2f9-2a4e-4c5d-b937-b693f27e11da
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 2%

---

# Note sulla versione di AEM Assets {#aem-assets-release-notes}

Le funzioni chiave, le evidenziazioni e i miglioramenti effettuati in AEM 6.4 Assets sono trattati in queste note sulla versione. Per informazioni dettagliate, segui i collegamenti forniti.

## Adobe Asset Link {#adobe-asset-link}

Adobe Asset Link in Creative Cloud for enterprise semplifica la collaborazione tra creativi e addetti al marketing nel processo di creazione dei contenuti. Si tratta di una nuova funzionalità nativa di Creative Cloud per le aziende, che fornisce una connessione ad AEM Assets direttamente da Adobe Photoshop, Adobe Illustrator o Adobe InDesign, senza uscire da questi strumenti.

Per ulteriori informazioni su funzionalità, prerequisiti e modalità di accesso, consulta la sezione [Adobe Asset Link](https://helpx.adobe.com/it/enterprise/using/adobe-asset-link.html) pagina.

## Tag avanzati migliorati (basati su Adobe Sensei) {#enhanced-smart-tags-powered-by-adobe-sensei}

AEM 6.4 introduce la funzionalità Tag avanzati avanzati avanzati basati su intelligenza artificiale in aggiunta ai tag avanzati lanciati in AEM 6.3.

* Il Servizio di contenuti avanzati impara la tassonomia aziendale del cliente e lo utilizza per assegnare automaticamente tag alle risorse digitali con tag pertinenti per i clienti, oltre ai tag generici. Migliora in modo significativo la reperibilità delle risorse e riduce il tempo sul mercato.
* Adobe Sensei potenzia il Servizio di contenuti avanzati, che consente di addestrare l’algoritmo di riconoscimento delle immagini sulla tassonomia aziendale. Questa intelligenza dei contenuti viene quindi utilizzata per applicare tag rilevanti a risorse simili.

Per utilizzare i tag avanzati migliorati di AEM Assets, installa la [service pack più recente di AEM 6.4](https://helpx.adobe.com/it/experience-manager/aem-releases-updates.html).

## Ricerca di traduzioni intelligenti (con tecnologia Adobe Sensei) {#smart-translation-search-powered-by-adobe-sensei}

AEM 6.4 introduce la funzionalità di ricerca di traduzioni intelligenti per supportare scenari di ricerca multilingue. I clienti con team distribuiti a livello globale in più lingue ora hanno accesso alla ricerca in lingue diverse senza dover passare attraverso flussi di lavoro di traduzione costosi e lunghi.

* La query di ricerca viene tradotta senza intervento manuale.
* I tag avanzati vengono generati in inglese e tradotti a macchina in altre lingue.
* La ricerca multilingue viene creata utilizzando la libreria open source Apache Joshua che supporta più di 50 lingue.

## Esperienza utente {#user-experience}

AEM 6.4 offre miglioramenti significativi nell’esperienza utente in aree come ricerca, ricerca, risorse multipagina e strumenti di amministrazione. Dettagli qui sotto:

Miglioramenti alla navigazione

* Nuova barra Struttura contenuto per navigare rapidamente in una gerarchia di risorse. In combinazione con la vista a elenco, ripristina il modello di interazione con l’interfaccia classica per la ricerca delle gerarchie di risorse.
* Nuove scelte rapide da tastiera come m per spostare le risorse, p per aprire la pagina delle proprietà, Ctrl + C per copiare l’operazione e molto altro.
* È stata migliorata l’esperienza di scorrimento e caricamento lento nella vista a schede e a elenco per la navigazione in un gran numero di risorse.
* È stata migliorata la vista a schede con il supporto per schede di diverse dimensioni in base all&#39;impostazione della vista.
* È stata migliorata l’esperienza di dettaglio delle risorse con la possibilità di visualizzare, passare alla risorsa &quot;precedente&quot; o &quot;successiva&quot; con il numero di risorse e la risorsa corrente.

Miglioramenti alla ricerca

* Nuovo pulsante Ricerca indietro con la possibilità di passare a un elemento di ricerca e tornare alla stessa posizione nei risultati di ricerca senza eseguire nuovamente la query di ricerca.
* Conteggio dei nuovi risultati di ricerca per visualizzare il numero di risultati di ricerca.
* È stato migliorato il Filtro di ricerca per tipo di file con la possibilità di filtrare i risultati di ricerca in base a tipi di MIME a grana fine come JPG, PNG e PSD, rispetto alle opzioni precedenti per immagini, documenti e contenuti multimediali.
* Filtri di ricerca migliorati con marche temporali precise invece della funzionalità precedente del cursore temporale.

Miglioramenti a risorse multipagina

* È stata migliorata l’esperienza di navigazione delle risorse a più pagine con un numero ridotto di clic.
* È stato migliorato il supporto per commenti e annotazioni, con tutti i commenti raggruppati a livello di risorsa anziché a livello di pagina.

Miglioramenti agli strumenti di amministrazione

* È stato migliorato il selettore delle proprietà negli strumenti di amministrazione per metadati, ricerche e rapporti con funzionalità di navigazione e di ricerca per semplificare l’esperienza di amministrazione.

Cataloghi

* Esperienza utente migliorata, allineamento con l&#39;interfaccia utente Templates. Per ulteriori informazioni, consulta [Produttore catalogo](../sites-administering/catalog-producer.md).

## Metadati {#metadata}

AEM 6.4 include funzionalità avanzate di gestione dei metadati per gestire i metadati su larga scala e applicare l&#39;integrità dei metadati tramite regole e convalide. Di seguito sono elencate le funzionalità chiave:

* Nuova funzionalità di esportazione di metadati in blocco per esportare (tutti, selettivi) metadati per un numero elevato di risorse in formato CSV per la modifica, la condivisione e l’integrazione con terze parti.
* Nuova funzionalità di importazione in blocco di metadati per importare file CSV per l’aggiunta di nuovi metadati, con l’aggiornamento dei metadati esistenti per più risorse in un’unica operazione. Questa operazione è asincrona e non ostacola le prestazioni del sistema. Una volta completato, l&#39;utente viene informato tramite AEM sistema di notifica.
* Nuovi metadati a cascata e contestuali mediante lo strumento schema metadati . È ora possibile definire catene di dipendenze e mappature dei valori tra i campi. È inoltre possibile definire il contesto in cui i campi del modulo metadati vengono visualizzati/nascosti. In questo modo, puoi visualizzare solo i campi rilevanti in qualsiasi momento a seconda dei valori presenti in altri campi.

## Rapporti {#reports}

AEM 6.4 offre significativi miglioramenti alla generazione di rapporti sulle risorse:

* Nuovo framework di rapporti scalabile a livello aziendale (per archivi di grandi dimensioni) che applica processi Sling per l’elaborazione asincrona delle richieste di rapporti. Puoi pianificare il rapporto in una data e in un&#39;ora specifiche. Puoi anche aggiungere colonne personalizzate a un rapporto.
* I nuovi report OOTB più comunemente richiesti dai clienti come Utilizzo del disco, File, Condivisione collegamenti, Pubblica su Brand Portal e Formazione sui tag avanzati.
* Nuova interfaccia utente per la creazione e la gestione di rapporti con opzioni dettagliate, possibilità di accedere ai rapporti archiviati, stato di esecuzione dei rapporti (riuscito, non riuscito, in coda e così via).

## Brand Portal {#brand-portal}

* **6.3 Aggiornamento della piattaforma**: Brand Portal è stato aggiornato da AEM 6.0 a AEM 6.3, con nuove funzioni e miglioramenti delle prestazioni.
* **Pubblicazione parallela**: Possono verificarsi fino a repliche tra AEM Assets e Brand Portal (prima 1), il che migliora notevolmente le prestazioni di pubblicazione
* **Pubblicazione facet schema e ricerca**: Possibilità di pubblicare schemi di metadati e facet di ricerca personalizzati in Brand Portal, eliminando la duplicazione degli sforzi.
* **Pubblicazione di tag in blocco**: Possibilità di pubblicare la tassonomia (insieme alla gerarchia) in Brand Portal, eliminando la duplicazione degli sforzi.
* **Iscriviti o richiedi accesso**: Flusso di lavoro per gli utenti non registrati in Brand Portal.
* **Notifica di manutenzione in-app (sullo schermo)**: Le notifiche vengono visualizzate con largo anticipo per evitare interruzioni nel business.
* **Miglioramenti al reporting**: Sono disponibili tre report OOTB: download, pubblicazione e condivisione dei collegamenti.
* **Restrizioni basate su DRM**: Dopo la scadenza di una risorsa con licenza, non è più disponibile per il download da Brand Portal.

## App desktop AEM {#aem-desktop-app}

L’app desktop AEM viene aggiornata alla versione 1.8, compatibile con AEM 6.4. L’elenco completo delle modifiche per AEM’app desktop è disponibile in un elenco dedicato [Note sulla versione dell’app desktop AEM](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html) documento.\
Elenco delle funzionalità principali AEM’app desktop dal rilascio di AEM 6.3:

* Possibilità di caricare cartelle gerarchiche in background.
* Interfaccia utente per monitorare il caricamento delle risorse in background.
* Miglioramenti alla memorizzazione in cache, inclusa un’interfaccia utente per gestire i parametri di memorizzazione in cache.
* Supporto più ampio per configurazioni di autenticazione AEM (SAML/SSO) e proxy di rete.
* Supporto: accesso facilitato ai registri dall&#39;interfaccia utente.
* Miglioramento della stabilità e delle correzioni dei problemi dei clienti.

Per un accesso più semplice alla documentazione e alle best practice, è disponibile la seguente documentazione:

* [Guida utente](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html), per gli utenti finali che utilizzano l’applicazione.
* [Guida all’installazione](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/install-upgrade.html), rivolta agli amministratori che impostano AEM e AEM app desktop per lavorare insieme

## Storage su più livelli {#tiered-storage}

AEM 6.4 include una serie di funzioni che supportano varie preferenze di storage su più livelli e implementano le regole del ciclo di vita. Le opzioni di archiviazione supportano anche (ma non sono limitate) cloud pubblici - AWS o Azure.

* Possibilità per gli utenti di selezionare e successivamente modificare la classe di storage a piacimento e definire regole per l&#39;archiviazione delle risorse da una classe all&#39;altra o gestire il ciclo di vita delle risorse.
* Possibilità per gli utenti di ridurre i costi di archiviazione selezionando un AWS o Azure diverso.

Per una panoramica delle piattaforme supportate, consulta la sezione [Documentazione sui requisiti tecnici](../sites-deploying/technical-requirements.md).

## Gruppo utenti chiuso {#closed-user-group}

* In AEM 6.4, Gruppo utenti chiuso o CUG fornisce un modo per limitare l’accesso alle cartelle nell’istanza di pubblicazione, è un’opzione dell’interfaccia touch aggiungere entità tramite la pagina delle proprietà delle cartelle a livello di cartella e vengono applicate a tutte le cartelle e sottocartelle/risorse all’interno.
* In modalità di pubblicazione, se un gruppo utenti chiuso è configurato e l’autorizzazione è abilitata in una cartella, gli utenti vengono reindirizzati a una pagina di accesso quando tentano di accedere alla cartella. Pertanto, gli utenti autorizzati possono accedere alla cartella e alle relative risorse solo dopo l’accesso. Pertanto, CUG limita l’accesso in lettura a una determinata struttura nell’archivio dei contenuti per tutti, ad eccezione delle entità selezionate.

## Componente aggiuntivo Dynamic Media {#dynamic-media-add-on}

Dynamic Media in 6.4 supporta una nuova modalità, in cui le risorse master vengono caricate e gestite con l’interfaccia utente web di AEM Assets, mentre le rappresentazioni dinamiche e altre funzioni per contenuti multimediali dinamici vengono gestite in background dal servizio di distribuzione cloud di Dynamic Media.

In questa modalità (introdotta per prima cosa con il rilascio di [Pacchetti di funzioni AEM 6.3 14410 e 18912](https://helpx.adobe.com/it/experience-manager/6-3/release-notes/dynamic-media-featurepack-14410.html)), gli utenti possono trarre vantaggio dalla gestione delle risorse end-to-end e dalle funzionalità per i contenuti multimediali dinamici utilizzando la moderna interfaccia utente web di AEM Assets e continuare a sfruttare i servizi di consegna che sono compatibili con Dynamic Media Classic (Scene7), inclusi gli URL di consegna, che rimangono invariati.

Inoltre, AEM 6.4 introduce nuove funzioni fornite da Adobe Sensei, miglioramenti per i media emergenti come VR e 3D, visualizzatori Dynamic Media e supporto per i frammenti esperienza nelle immagini interattive e nei banner carosello.

### Ritaglio avanzato (basato su Adobe Sensei) {#smart-crop-powered-by-adobe-sensei}

* Il ritaglio avanzato fornisce automaticamente un ritaglio non distruttivo delle immagini per preservare il punto di interesse del design reattivo. Potete visualizzare in anteprima i suggerimenti ritagliati e, se necessario, regolarli manualmente.
* Questa funzione consente anche la generazione automatizzata dei campioni per le immagini dei prodotti. La generazione automatizzata dei campioni consente di aggiungere automaticamente campioni colore, campioni pattern o entrambi alle immagini del prodotto.

Vedi [Profili immagine](../assets/image-profiles.md) documentazione per ulteriori informazioni.

Vedi anche [Aggiunta di risorse Dynamic Media alle pagine](../assets/adding-dynamic-media-assets-to-pages.md) documentazione per ulteriori informazioni sull’utilizzo di Smart Crop con il componente Dynamic Media.

### Imaging avanzato {#smart-imaging}

* L&#39;imaging intelligente sfrutta le caratteristiche di visualizzazione esclusive di ogni utente per distribuire automaticamente le immagini ottimizzate per la propria esperienza, ottenendo prestazioni e coinvolgimento migliori.
* Le immagini vengono automaticamente convertite in formati diversi in base alle funzionalità del browser.
* Le impostazioni di qualità dell&#39;immagine sono determinate rispettivamente nel browser e applicate. Questa intelligenza mantiene accettabili le prestazioni di caricamento delle immagini per una larghezza di banda limitata e velocità di connessione lente.

Vedi [Imaging avanzato](../assets/imaging-faq.md) documentazione per ulteriori informazioni.

### Miglioramenti a media e visualizzatori emergenti {#emerging-media-amp-viewer-enhancements}

* Sono supportati nuovi visualizzatori, che forniscono esperienze migliori e coinvolgenti per l’utente.
* Il visualizzatore panoramico consente di coinvolgere l’utente e di offrire la possibilità di sperimentare meglio scene, proprietà, posizioni e paesaggi della stanza. Vedi [Immagini panoramiche](../assets/panoramic-images.md) documentazione da apprendere.

* Il visualizzatore VR offre un’esperienza coinvolgente per proprietà, posizioni e paesaggi.
* Visualizzatore di immagini verticali ottimizzato per le immagini dei prodotti.
* Miglioramenti all’accessibilità della tastiera.
