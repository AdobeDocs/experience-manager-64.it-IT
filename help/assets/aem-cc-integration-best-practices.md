---
title: Best practice per l’integrazione di Experience Manager e Creative Cloud
description: Best practice per integrare un’implementazione  [!DNL Experience Manager] con Adobe Creative Cloud per semplificare i flussi di lavoro di trasferimento delle risorse e ottenere la massima efficienza
contentOwner: AG
feature: Collaboration,Adobe Asset Link,Desktop App
role: User,Admin
exl-id: cb9bea05-3359-4fb4-b935-59e522a5f387
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '3488'
ht-degree: 16%

---

# [!DNL Experience Manager] e le best practice  [!DNL Creative Cloud] di integrazione {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets è una soluzione di gestione delle risorse digitali (DAM) che può essere integrata con Adobe Creative Cloud per aiutare gli utenti DAM a collaborare con i team creativi, semplificando la collaborazione nel processo di creazione dei contenuti.

Adobe Creative Cloud fornisce ai team creativi un ecosistema di soluzioni e servizi per aiutarli a creare risorse digitali. Include applicazioni desktop e mobili, servizi cloud come l’archiviazione con sincronizzazione desktop o esperienza web, nonché marketplace come Adobe Stock.

Continua a leggere per scoprire quali integrazioni scegliere tra desktop e DAM di livello enterprise in base al tuo caso d’uso e quali sono le best practice associate per i flussi di lavoro di connessione.

>[!NOTE]
>
>La condivisione di cartelle da [!DNL Experience Manager] a Creative Cloud è obsoleta e non è più inclusa in questa guida. Adobe consiglia di utilizzare funzionalità più recenti, come [Adobe Asset Link](https://helpx.adobe.com/it/enterprise/using/adobe-asset-link.html) o [[!DNL Experience Manager] app desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html) per fornire all’utente creativo l’accesso alle risorse gestite in [!DNL Experience Manager].

## Esigenze di collaborazione di creativi, esperti marketing e utenti DAM {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Requisiti | Caso d’uso | Superfici interessate |
|---|---|---|
| Semplificare l&#39;esperienza per i creativi sul desktop | Semplifica l’accesso alle risorse da un DAM ([!DNL Assets]) per i creativi o, più in generale, per gli utenti desktop che lavorano in applicazioni di creazione di risorse native. Hanno bisogno di un modo semplice e semplice per scoprire, utilizzare (aprire), modificare e salvare le modifiche a [!DNL Experience Manager], nonché caricare nuovi file. | desktop Win o Mac; Creative Cloud app |
| Fornire risorse pronte all’uso di alta qualità da Adobe Stock | Gli addetti al marketing contribuiscono ad accelerare il processo di creazione dei contenuti fornendo assistenza per l’origine e l’individuazione delle risorse. I professionisti creativi utilizzano le risorse approvate direttamente dai propri strumenti creativi. | [!DNL Assets]; marketplace Adobe Stock; campi metadati |
| Distribuire e condividere le risorse per organizzazioni | I dipartimenti interni/le filiali locali e i partner esterni, i distributori e le agenzie utilizzano le risorse approvate condivise dall&#39;organizzazione madre. L&#39;organizzazione desidera condividere in modo sicuro e senza soluzione di continuità le risorse create per un riutilizzo più ampio. | Brand Portal, Asset Share Commons |

## Offerte di Adobe per supportare le esigenze di collaborazione {#adobe-offerings-to-support-the-collaboration-need}

| Proposta di valore per i soggetti coinvolti | offerta Adobe | Superfici interessate |
|---|---|---|
| Gli utenti creativi individuano le risorse da [!DNL Experience Manager], le aprono e le utilizzano, le modificano e caricano le modifiche in [!DNL Experience Manager], nonché caricano nuovi file in [!DNL Experience Manager], senza uscire dalle app Creative Cloud. | [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator e InDesign |
| Gli utenti aziendali semplificano l’apertura e l’utilizzo delle risorse, la modifica e il caricamento delle modifiche a [!DNL Experience Manager] e il caricamento di nuovi file in [!DNL Experience Manager] dall’ambiente desktop. Utilizzano un’integrazione generica per aprire qualsiasi tipo di risorsa nell’applicazione desktop nativa, inclusi quelli non Adobi. | App desktop [[!DNL Experience Manager]  ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | [!DNL Experience Manager] app desktop su desktop Win e Mac |
| Gli addetti al marketing e gli utenti aziendali possono individuare, visualizzare in anteprima, concedere in licenza e salvare le risorse Adobe Stock e gestirle dall’interno di [!DNL Experience Manager]. Le risorse concesse in licenza e salvate forniscono metadati selezionati di Adobe Stock per una migliore governance. | [Integrazione di Experience Manager e Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager] interfaccia web |

Questo articolo si concentra principalmente sui primi due aspetti delle esigenze di collaborazione. La distribuzione e l’approvvigionamento delle risorse su scala viene brevemente citata come caso d’uso. Per tali esigenze, valuta prodotti come Adobe Brand Portal o Asset Share Commons. Le soluzioni alternative come [Brand Portal](https://helpx.adobe.com/it/experience-manager/brand-portal/user-guide.html), che possono essere create in base ai componenti [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/), [Condivisione collegamenti](/help/assets/link-sharing.md), che utilizzano [Risorse Experienci Manager](/help/assets/managing-assets-touch-ui.md) devono essere esaminate in base a requisiti specifici.

![Creative Cloud connessioni per  [!DNL Experience Manager]: Decidere quale funzionalità utilizzare](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### Mappatura dei casi di utilizzo

| Caso d’uso | App desktop [!DNL Experience Manager] | Condivisione di cartelle | Altre soluzioni |
|---|---|---|---|
| Condividi un numero inferiore (1) di risorse DAM con l’utente creativo | ↓ ✔ | ↓ |  |
| Condividere un numero maggiore (2) di risorse DAM con utenti creativi | ↓ ✔ | ✘ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [Condivisione risorse](assets-finder-editor.md) |
| Condividere risorse DAM con utenti che hanno accesso a DAM | ↓ ✔ | ↓ | [Condivisione collegamenti](link-sharing.md) |
| Condividi risorse DAM con utenti che non hanno accesso a DAM | ✘ | ↓ ✔ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [Condivisione risorse](assets-finder-editor.md) |
| Salvare un numero/volume minore di risorse in DAM | ↓ ✔ | ↓ | [Caricamento interfaccia web](managing-assets-touch-ui.md) |
| Possibilità di salvare un numero maggiore di risorse in DAM (3) | ↓ ✔ | ✘ | [Interfaccia web ](managing-assets-touch-ui.md) <br> CaricaScript/strumento personalizzato |
| Migrare un numero elevato di risorse a DAM | ✘ | ✘ | [Guida alla migrazione](assets-migration-guide.md) |
| Apri rapidamente una risorsa sul desktop | ↓ ✔ | ✘ |  |
| Apertura e modifica rapida delle risorse sul desktop | ↓ ✔ | ✘ |  |

La legenda dei simboli:

* ↓ ✔: soluzione preferita
* ③: soluzione accettabile
* ✘: non deve essere utilizzato per il caso d&#39;uso

Osservazioni aggiuntive:

* (1) Numero più ridotto di attività: ad esempio, un piccolo set di risorse relative a un progetto o a una campagna
* (2) Maggiore numero di attività: ad esempio, tutte le risorse approvate nell&#39;organizzazione
* (3) Utilizza la funzionalità di caricamento cartelle dell&#39;app desktop [!DNL Experience Manager]

Per supportare i casi di utilizzo della distribuzione delle risorse, è necessario considerare altre soluzioni:

* [Brand ](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) Portal è un componente aggiuntivo SaaS configurabile per  [!DNL Experience Manager] Assets per la pubblicazione delle risorse.
* Le soluzioni personalizzate vengono create in base al codice [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* [!DNL Experience Manager] [collegare ](/help/assets/link-sharing.md) shareto condividere risorse ad hoc utilizzando i collegamenti.
* [[!DNL Experience Manager] Interfaccia web di Assets ](/help/assets/managing-assets-touch-ui.md) con aree per soggetti esterni protette dalla configurazione di  [!DNL Experience Manager] Access Control e con le necessarie regolazioni di configurazione IT/rete, che consentono a tali utenti esterni di accedere a  [!DNL Experience Manager].

## Concetti chiave e casi d’uso {#key-concepts-and-use-cases}

### Glossario dei termini comuni {#glossary-of-common-terms}

* **Work-in-progress o creative work-in-progress (WIP):** una fase del ciclo di vita delle risorse in cui una risorsa subisce più modifiche e, in genere, non è ancora pronta per essere condivisa con team più grandi.
* **Creative-ready assets (Risorse pronte per i creativi):** risorse pronte per essere condivise con un team più ampio oppure che sono state selezionate o approvate dal team creativo per la condivisione con i team di marketing o LOB.
* **Asset approvals (Approvazioni risorse):** il processo di approvazione che viene eseguito per le risorse già caricate in DAM, che, in genere, include approvazioni del marchio, approvazioni legali e così via.
* **Final asset (Risorsa finale):** una risorsa che ha superato tutte le approvazioni/assegnazione tag dei metadati ed è pronta per essere utilizzata dal team più ampio. Tale risorsa viene memorizzata in DAM, per poi essere resa disponibile a tutti gli utenti (o a tutti gli interessati). Può essere utilizzata nei canali di marketing o dai team creativi per la creazione di design.
* **Minor asset update/change (Aggiornamento/modifica risorsa secondaria):** una modifica rapida e piccola a una risorsa digitale. Spesso viene effettuata in risposta a una richiesta di ritocco o di modifica minore, a una revisione delle risorse o all’approvazione (ad esempio: riposizionamento, modifica dimensioni del testo, regolazione di saturazione/luminosità, colore e così via).
* **Major asset update/change (Aggiornamento/modifica risorsa principale):** un passaggio a una risorsa digitale che richiede un lavoro considerevole e che a volte deve essere effettuato in un periodo di tempo più lungo. Generalmente include più modifiche. La risorsa deve essere salvata più volte durante l’aggiornamento. In genere, gli aggiornamenti principali delle risorse fanno sì che la risorsa entri in una fase WIP.
* **DAM:** gestione delle risorse digitali. In questo documento, è sinonimo di [!DNL Experience Manager Assets], salvo specificazione contraria.
* **Creative user (Utente creativo):** un professionista che crea risorse digitali utilizzando le app e i servizi Creative Cloud. In alcuni casi, è possibile che un utente creativo sia membro di un team creativo che utilizza Creative Cloud, ma che non crea risorse digitali, ad esempio un direttore creativo o un manager del team creativo.
* **DAM user (Utente DAM)**: utente tipico di un sistema DAM. A seconda dell’organizzazione, un utente DAM può essere di marketing o non, come un utente Line-of-Business (LOB), un bibliotecario, un venditore e così via.

### Considerazioni sull’utilizzo di [!DNL Experience Manager] e l’integrazione con Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

* Consulta [best practice per le app desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Vedi [Integrazione Adobe Stock](aem-assets-adobe-stock.md)
* Consulta [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Questo è un breve riepilogo delle best practice per l’integrazione di Experience Manager e Creative Cloud. Leggi il resto di questo documento per ottenere la comprensione dettagliata di questi.

* **For creative users, working in Photoshop, InDesign, or Illustrator (Per gli utenti creativi che lavorano in Photoshop, InDesign o Illustrator)**: Adobe Asset Link offre la migliore esperienza utente possibile, inclusa la gestione del Work-in-progress sulle risorse estratte da [!DNL Experience Manager]
* **For simplifying access to assets from desktop for any generic file format or application (Per semplificare l’accesso alle risorse dal desktop per qualsiasi formato di file o applicazione di tipo generico):**[!DNL Experience Manager] utilizza l’app desktop 
* **Understand why and when to store assets in DAM (Scopri perché e quando archiviare le risorse in DAM)**: aggiornamenti da rendere disponibili al team più ampio della tua organizzazione
* **Mind the volume of assets shared (Considera il volume di risorse condivise):** se il caso d’uso è la distribuzione delle risorse, la governance e la sicurezza potrebbero diventare gli aspetti più importanti. Valuta l’utilizzo di strumenti creati per il lavoro in scala, come Brand Portal.
* **Understand asset lifecycle (Informazioni sul ciclo di vita delle risorse):** scopri come le risorse vengono gestite dai diversi team all’interno dell’organizzazione
* **Handle frequent saves to assets with care (Gestisci con attenzione i salvataggi frequenti nelle risorse):** Adobe Asset Link si occupa di questo aspetto con PS, AI, ID. Per altre applicazioni, non eseguire le attività WIP in cartelle condivise o mappate, a meno che non ti servano tutte le modifiche all’interno di DAM

### Accesso alle risorse Adobe Stock da [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[[!DNL Experience Manager] l’](/help/assets/aem-assets-adobe-stock.md) integrazione con Adobe Stock consente  [!DNL Experience Manager] agli utenti di cercare, visualizzare in anteprima, concedere in licenza e salvare le risorse da Adobe Stock in  [!DNL Experience Manager]. Le risorse Adobe Stock concesse in licenza e salvate hanno selezionato i metadati Stock, che possono essere utilizzati per cercarli con filtri aggiuntivi.

Alcuni punti importanti su questa integrazione:

* Quando le risorse da stock di Adobe vengono salvate in [!DNL Experience Manager], diventano normali [!DNL Experience Manager] risorse e il file binario viene salvato nell’archivio [!DNL Experience Manager]. Alcuni metadati relativi ad Adobe Stock vengono salvati per la risorsa in [!DNL Experience Manager], altrimenti il processo di acquisizione sarà lo stesso di qualsiasi altro file. Ad esempio, se Tag avanzati sono attivi, al momento del salvataggio questi tag vengono aggiunti a tali risorse.
* La risorsa salvata in [!DNL Experience Manager] è una copia, non un collegamento in Adobe Stock.

**Utilizzo delle risorse salvate da Adobe Stock in  [!DNL Experience Manager] Creative Cloud**. Questa integrazione è indipendente da Adobe Asset Link, ma Adobe Asset Link riconosce le risorse salvate da Stock in questo modo e visualizza metadati aggiuntivi e l’icona Stock su queste risorse nell’interfaccia utente dell’estensione Asset Link di Adobe in Photoshop, Illustrator o InDesign. I file sono disponibili per la navigazione, l’apertura e così via, perché sono normali risorse [!DNL Experience Manager] quando vengono salvate in [!DNL Experience Manager].
I creativi che lavorano nelle app Creative Cloud con estensione Adobe Asset Link presente, oltre ad avere accesso a risorse già concesse in licenza da Adobe Stock in [!DNL Experience Manager], possono anche utilizzare il pannello Creative Cloud librerie per cercare, visualizzare in anteprima e concedere in licenza le risorse Adobe Stock.
Le risorse da Adobe Stock concesse in licenza e salvate in [!DNL Experience Manager] diventano disponibili per i team più grandi che accedono all’implementazione di [!DNL Experience Manager] Assets, mentre i creativi che concedono in licenza le risorse da Adobe Stock tramite il pannello Librerie Creative Cloud le rendono disponibili solo per impostazione predefinita nel loro account Creative Cloud.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## Informazioni sull’archiviazione delle risorse in un DAM {#about-storing-assets-in-a-dam}

Per progettare un flusso di lavoro efficiente tra team creativi e di marketing/line-of-business (LOB) e scegliere le migliori funzionalità di supporto, è importante comprendere quando e perché le risorse vengono memorizzate in DAM.

### Perché le risorse vengono memorizzate in DAM {#why-assets-are-stored-in-dam}

L’archiviazione delle risorse in DAM le rende facilmente accessibili e accessibili. Garantisce che le risorse possano essere sfruttate da numerosi utenti nell’organizzazione o nell’ecosistema, inclusi partner, clienti e così via.

La maggior parte delle organizzazioni sceglie di archiviare solo le risorse rilevanti per i processi di marketing/LOB a valle (pubblicazione su canali come il canale web tramite [!DNL Experience Manager] Sites o altri canali gestiti da Adobe Experience Cloud, Advertising Cloud e misurati da Analytics Cloud, fornendo a utenti/partner e così via). Inoltre, le organizzazioni memorizzano risorse che possono essere soggette a un processo di revisione/approvazione in DAM. In questo modo, DAM memorizza principalmente risorse che hanno alte probabilità di essere sfruttate ed evita di archiviare le risorse inattive.

La memorizzazione delle risorse è inoltre soggetta a considerazioni tecniche e relative all’utilizzo delle risorse. DAM fornisce servizi aggiuntivi sulle risorse memorizzate, tra cui l’estrazione dei metadati, il controllo delle versioni, la generazione di anteprime/transcodifica, la gestione dei riferimenti e l’aggiunta di informazioni sul controllo degli accessi. Questi servizi richiedono tempo e risorse aggiuntive per l&#39;infrastruttura.

Spesso, l’archiviazione di tutte le risorse e gli aggiornamenti non è auspicabile. Ad esempio, se gli aggiornamenti a risorse specifiche sono di scarsa qualità e consumano risorse eccessive, le risorse potrebbero non essere memorizzate in DAM.

### Quando le risorse vengono memorizzate in DAM {#when-assets-are-stored-in-dam}

I team creativi (e le organizzazioni) solitamente non sono interessati a memorizzare le risorse in ogni fase del ciclo di vita delle risorse. Ad esempio, evitano di memorizzare le risorse nei seguenti casi:

* Risorse ancora da completare o oggetto di sperimentazione
* Risorse che non superano il ciclo di revisione creativo/interno del team
* Rispetto alla risorsa in questione, il team ha candidati migliori per rappresentare il proprio lavoro a team esterni

Di solito, le risorse delle classi seguenti vengono memorizzate in DAM:

* Attività che hanno raggiunto una certa scadenza e sono considerate pronte per essere condivise
* Risorse preselezionate dal team creativo
* Formati di risorse specifici utilizzabili o richiesti dal marketing, a seconda di un contratto o contratto specifico (ad esempio, file JPG convertiti da file RAW, TIFF/immagini da originali PSD)

### Quando gli aggiornamenti alle risorse vengono memorizzati in DAM {#when-updates-to-assets-are-stored-in-dam}

Di regola, solo gli aggiornamenti alle risorse rilevanti per il set più ampio di utenti DAM devono essere archiviati in DAM. Assicura che gli utenti (marketing e funzioni simili) vedano solo le versioni rilevanti nella timeline delle risorse DAM.

In genere, le modifiche sono correlate alle fasi principali del ciclo di vita delle risorse. Ad esempio, la risorsa iniziale pronta per la creazione o un aggiornamento ufficiale basato su richiesta/revisione fornita dal team creativo devono essere memorizzati e versioni in DAM.

L’aggiornamento del team creativo per la revisione da parte del team marketing dopo una richiesta di modifica della risorsa esistente in DAM è un esempio di aggiornamento rilevante. Deve essere memorizzato e modificato in DAM per ulteriori riferimenti o per ripristinare la versione precedente.

Di seguito sono riportati alcuni esempi di aggiornamenti che in genere non sono rilevanti:

* Versioni precedenti delle risorse caricate prima che sia pronto per la revisione del marketing
* Frequenti modifiche creative alla risorsa nella fase in corso di lavorazione prima che il team creativo decida che la risorsa è pronta

### Accesso utente a DAM {#user-access-to-dam}

[!DNL Experience Manager] Assets supporta due tipi di utenti in base al loro accesso alla distribuzione di  [!DNL Experience Manager] Assets. In genere, gli utenti all’interno della rete aziendale (firewall) hanno accesso diretto a DAM. Altri utenti esterni alla rete aziendale non avrebbero accesso diretto. Il tipo di utente determina quali integrazioni possono essere utilizzate dal punto di vista tecnico.

#### Utenti creativi con accesso diretto a DAM {#creative-users-with-direct-access-to-dam}

In genere, i team creativi interni o le agenzie/professionisti creativi caricati nella rete interna hanno accesso all’istanza DAM, incluso l’accesso [!DNL Experience Manager].

In questi casi, l’app desktop [!DNL Experience Manager] consente di accedere facilmente alle risorse finali/approvate e di salvare le risorse pronte per la creazione in DAM.

#### Utenti creativi senza accesso a DAM {#creative-users-without-access-to-dam}

Le agenzie esterne e i freelance senza accesso diretto all’istanza DAM possono richiedere l’accesso alle risorse approvate o desiderano aggiungere le loro nuove progettazioni al DAM.

In questi casi, puoi sfruttare l’ integrazione [!DNL Experience Manager]/Creative Cloud per migliorare il flusso di lavoro. Il prerequisito è che gli utenti creativi abbiano un Adobe ID e abbiano un account Creative Cloud con il servizio di storage.

Utilizza le seguenti strategie per fornire accesso alle risorse finali/approvate:

* Per fornire accesso a un numero elevato di risorse: Utilizza [[!DNL Experience Manager] Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) o l&#39;implementazione da parte del cliente di [Asset Share](assets-finder-editor.md) sull&#39;infrastruttura di pubblicazione [!DNL Experience Manager]

* Per fornire accesso ad alcune risorse: È possibile utilizzare la condivisione di cartelle [!DNL Experience Manager] con Adobe Creative Cloud oltre a [!DNL Experience Manager] Assets Brand Portal o Condivisione risorse. Tieni presente che esistono alcune limitazioni relative a questa integrazione, descritte più dettagliatamente in questo articolo.

### Casi d&#39;uso {#use-cases}

I seguenti casi d’uso descrivono vari tipi di flussi di lavoro tra DAM e il desktop di designer.

#### Creare nuove progettazioni utilizzando le risorse di DAM {#creating-new-designs-using-assets-from-dam}

Il diagramma seguente illustra il ciclo di vita delle risorse digitali. Mostra come gli utenti creativi e gli utenti DAM (addetti al marketing, utenti LOB) sfruttano le risorse esistenti e le utilizzano per creare più risorse e inviarle per l’approvazione.

![chlimage_1-301](assets/chlimage_1-301.png)

Il ciclo di vita delle risorse include le seguenti fasi:

1. Condividi risorse approvate su desktop creativo: Le risorse finali da DAM sono rese disponibili all’utente creativo (sul desktop)
1. Crea una nuova progettazione (risorsa digitale creativa): Un nuovo file viene memorizzato nell&#39;area WIP.
1. Utilizzare (inserire) risorse approvate in una nuova progettazione: L’utente creativo produce una nuova risorsa utilizzando le risorse approvate esistenti nelle app Creative Cloud
1. Salvataggio frequente degli aggiornamenti WIP: L’utente creativo esegue un’iterazione rapida e salva il file frequentemente. A questo punto, l’utente creativo può collaborare con altri, ma gli aggiornamenti salvati di frequente non sono di interesse per gli utenti DAM.
1. La risorsa raggiunge lo stato di preparazione creativa e viene salvata nella cartella Creative Ready .
1. Aggiornamento risorsa : Un aggiornamento delle risorse o un nuovo file è disponibile per gli utenti in DAM
1. La risorsa viene messa in produzione: Si tratta di un processo DAM che, a seconda dell’organizzazione, può comprendere l’assegnazione di tag, le approvazioni e la modifica del controllo di accesso. A questo punto, la risorsa è considerata finale e può essere utilizzata da team più ampi che sfruttano DAM. Può essere utilizzato anche dagli utenti creativi per creare altre risorse.

Di seguito sono riportati alcuni consigli generali su come gestire le risorse tramite questo processo:

* Utilizzare un&#39;area/sistema di archiviazione dedicata, ad esempio la cartella sincronizzata Adobe Creative Cloud Assets, per i file WIP: Gli aggiornamenti frequenti non rilevanti per gli utenti DAM sono gestiti al meglio da un sistema dedicato e non da [!DNL Experience Manager] Assets. Le risorse WIP possono essere sincronizzate con il disco locale utilizzando l’applicazione desktop Adobe Creative Cloud, salvate nell’archivio locale e così via.
* Utilizza cartelle/condivisioni separate per le risorse finali e le risorse caricate in DAM: per chiarezza, le risorse finali devono avere la propria cartella mappata/condivisa (&quot;Ultimo&quot; esempio precedente) e le risorse da caricare nuovamente in DAM devono avere la propria (&quot;Creative Ready&quot;)

#### Modifica delle risorse esistenti gestite in DAM {#changing-existing-assets-managed-in-dam}

In alcuni casi, le risorse in DAM potrebbero richiedere modifiche. Gli esempi includono:

* Richiesta di modifiche alle risorse dalla revisione e dall’approvazione eseguite in [!DNL Experience Manager] Risorse
* Aggiornamenti principali alle risorse finali esistenti
* Modifiche rapide apportate a un file esistente (in particolare prima che venga approvato definitivamente)

In questi casi, l’ app desktop [!DNL Experience Manager] fornisce il modo più semplice per eseguire queste operazioni.

![chlimage_1-302](assets/chlimage_1-302.png)

Ecco il flusso di eventi rappresentato nel diagramma:

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for [!DNL Experience Manager] desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** condividi la risorsa da DAM a desktop o aprila direttamente sul desktop nell’applicazione scelta (ad esempio, Adobe Photoshop e così via). Per bloccare il file, si consiglia di effettuare il check-out.
* **2:** Aggiornamento secondario: Modifica il file e salva le modifiche.
* Flusso alternativo al passaggio 2

   * **A:** Aggiornamento principale: Se il file richiede un set elaborato di modifiche, deve essere salvato in modo intermittente e copiato in una cartella o area WIP.
   * **B:** Il lavoro continua sul file nelle cartelle WIP. Le modifiche salvate non vengono sincronizzate con la versione in DAM
   * **C:** Al termine degli aggiornamenti, il file viene copiato o salvato nella cartella mappata

* **3:** gli aggiornamenti delle risorse si riflettono in DAM. Seleziona la risorsa per sbloccarla.
* **4:** Il bene viene messo in produzione.

Di seguito sono riportati alcuni consigli generali su come gestire le risorse durante questo processo:

* Evita di salvare direttamente un file aperto da una condivisione di rete mappata da [!DNL Experience Manager] app desktop, a meno che le modifiche apportate al file non siano di piccole dimensioni.
* Copiare il file in una cartella WIP separata se si desidera apportare ulteriori modifiche, salvarlo a intermittenza o collaborare con il team Creative.

#### Caricamento in serie in DAM {#bulk-upload-to-dam}

Potrebbe essere necessario caricare contemporaneamente un numero maggiore di file in DAM in alcuni scenari, ad esempio:

* Caricamento dei risultati di fotografie o progetti più grandi
* Caricamento delle risorse fornite dalle agenzie creative
* Caricamento di risorse selezionate da un set più grande se la selezione viene eseguita al di fuori di DAM

Questa descrizione fa riferimento al caricamento di file operativamente (ad esempio, ogni settimana o con ogni servizio fotografico , ecc.), come parte normale del flusso di lavoro dell’utente desktop. Le migrazioni di risorse di grandi dimensioni non sono coperte qui.

Puoi sfruttare le seguenti funzionalità se desideri caricare le risorse in blocco:

* Per caricare cartelle grandi/gerarchiche, utilizza l’ app desktop [!DNL Experience Manager] che fornisce una funzione [Caricamento cartelle](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload). Puoi anche caricare strutture di cartelle gerarchiche. Le risorse vengono caricate in background, quindi non sono collegate a una sessione del browser web
* Se desideri caricare alcuni file da una singola cartella, trascinali direttamente dal desktop all’interfaccia utente Web o utilizza l’opzione Crea nell’ [!DNL Experience Manager] interfaccia web Assets.

>[!NOTE]
>
>A seconda delle esigenze aziendali, puoi anche utilizzare caricatori personalizzati.

#### Gestione delle risorse digitali direttamente dal desktop {#managing-digital-assets-directly-from-desktop}

Se utilizzi Condivisione file di rete per gestire le risorse digitali, puoi considerare come un comodo sostituto solo l’utilizzo della condivisione di rete mappata dall’ [!DNL Experience Manager] app desktop. Durante la transizione dalle condivisioni di file di rete, ricorda che l’ [!DNL Experience Manager] interfaccia utente web offre un set completo di funzionalità di gestione delle risorse digitali che vanno ben oltre quanto possibile su una condivisione di rete (ricerca, raccolte, metadati, collaborazione, anteprime, ecc.) e [!DNL Experience Manager] l’app desktop fornisce un comodo collegamento per collegare l’archivio DAM lato server al lavoro sul desktop.

Evita di usare l’app desktop [!DNL Experience Manager] per gestire le risorse direttamente nella condivisione di rete di [!DNL Experience Manager] risorse. Ad esempio, evita di utilizzare l’ [!DNL Experience Manager] app desktop per spostare/copiare più file. Utilizza invece l’ [!DNL Experience Manager] interfaccia utente web Assets per trascinare cartelle da Finder/Explorer alla condivisione di rete o utilizza la funzione [!DNL Experience Manager] Caricamento cartelle risorse .

#### Migrazione delle risorse {#asset-migration}

Per pianificare ed eseguire le migrazioni delle risorse dal sistema esistente a un nuovo sistema o per la migrazione di un grande volume di risorse memorizzate sui server, consulta la [Guida alla migrazione](/help/assets/assets-migration-guide.md). [!DNL Experience Manager] l’app desktop e  [!DNL Experience Manager] le integrazioni Creative Cloud non supportano tali migrazioni. A causa dei grandi volumi di risorse da acquisire e dei requisiti aggiuntivi relativi alla mappatura, alla trasformazione e all’acquisizione dei metadati, le migrazioni devono essere gestite utilizzando strumenti e approcci diversi.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/in/enterprise/admin-guide.html/in/enterprise/using/adobe-asset-link.ug.html)
>* [[!DNL Experience Manager] best practice per le app desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [[!DNL Experience Manager] Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [[!DNL Experience Manager] e integrazione con Adobe Stock](aem-assets-adobe-stock.md)

