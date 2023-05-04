---
title: Configurazione della sincronizzazione di una Live Copy
seo-title: Configuring Live Copy Synchronization
description: Scopri come configurare la sincronizzazione di Live Copy.
seo-description: Learn about configuring Live Copy Synchronization.
uuid: a14fab89-fd1c-4fec-a9e0-9f6511f764a6
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: c491f0f3-375d-4203-bdf3-234987bbf685
feature: Multi Site Manager
exl-id: 42b92993-abde-4ae4-8f0d-44166a3ea22e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2731'
ht-degree: 28%

---

# Configurazione della sincronizzazione di una Live Copy{#configuring-live-copy-synchronization}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Esegui le seguenti operazioni per controllare come e quando vengono sincronizzate le Live Copy con il relativo contenuto sorgente.

* Decidi se le configurazioni di rollout esistenti soddisfano le tue esigenze o se devi crearne una o più.
* Specifica le configurazioni di rollout da utilizzare per le Live Copy.

## Configurazioni di rollout installate e personalizzate {#installed-and-custom-rollout-configurations}

Questa sezione fornisce informazioni sulle configurazioni di rollout installate e sulle azioni di sincronizzazione che utilizzano, nonché su come creare configurazioni personalizzate, se necessario.

>[!CAUTION]
>
>L&#39;aggiornamento o la modifica di una configurazione di rollout predefinita (installata) è **not** consigliato. Se è necessaria un’azione live personalizzata, questa deve essere aggiunta in una configurazione di rollout personalizzata.

### Attivatori di rollout {#rollout-triggers}

Ogni configurazione di rollout utilizza un attivatore (o trigger) di rollout che determina l’esecuzione dell’implementazione. Le configurazioni di rollout possono utilizzare uno dei seguenti attivatori:

* **Al rollout**: La **Rollout** viene utilizzato nella pagina di stampa blu, oppure **Sincronizza** viene utilizzato nella pagina Live Copy.

* **In caso di modifica**: quando la pagina sorgente viene modificata.

* **Al momento dell’attivazione**: quando la pagina sorgente viene attivata.

* **Alla disattivazione**: quando la pagina sorgente viene disattivata.

>[!NOTE]
>
>L’utilizzo del trigger Durante la modifica può influire sulle prestazioni. Per ulteriori informazioni, consulta la sezione sulle [best practice per MSM](/help/sites-administering/msm-best-practices.md#onmodify).

### Configurazioni di rollout installate {#installed-rollout-configurations}

Nella tabella seguente sono elencate le configurazioni di rollout installate con AEM. La tabella contiene le azioni di attivazione e sincronizzazione per ciascuna configurazione di rollout. Se le azioni di configurazione di rollout installate non soddisfano le tue esigenze, puoi [creare una nuova configurazione di rollout](#creating-a-rollout-configuration).

<table> 
 <tbody> 
  <tr> 
   <th>Nome</th> 
   <th>Descrizione</th> 
   <th>Attivatore</th> 
   <th>Azioni di sincronizzazione<br /> <br /> vedi anche <a href="#installed-synchronization-actions">Azioni di sincronizzazione installate</a></th> 
  </tr> 
  <tr> 
   <td>Configurazione di rollout standard</td> 
   <td>Configurazione di rollout standard che consente di avviare il processo di rollout all’attivazione del rollout ed esegue le seguenti azioni: crea, aggiorna, elimina contenuto e ordina nodi figlio.</td> 
   <td>Al momento del rollout</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> productUpdate<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>Attiva in caso di attivazione Blueprint</td> 
   <td>Pubblica la Live Copy quando l’origine viene pubblicata.</td> 
   <td>Al momento dell’attivazione</td> 
   <td>targetActivate</td> 
  </tr> 
  <tr> 
   <td>Disattiva in caso di disattivazione Blueprint</td> 
   <td>Disattiva la Live Copy quando l’origine viene disattivata.</td> 
   <td>Alla disattivazione</td> 
   <td>targetDeactivate<br /> </td> 
  </tr> 
  <tr> 
   <td>Invia dopo modifica</td> 
   <td><p>Invia il contenuto alla Live Copy quando l’origine viene modificata.</p> <p>Utilizza questa configurazione di rollout con moderazione in quanto utilizza l’attivatore Al momento della modifica.</p> </td> 
   <td>In caso di modifica</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> orderChildren<br /> </td> 
  </tr> 
  <tr> 
   <td>Invia dopo modifica (superficiale)</td> 
   <td><p>Invia il contenuto alla Live Copy quando la pagina blueprint viene modificata, senza aggiornare i riferimenti (ad esempio, per le copie superficiali).</p> <p>Utilizza questa configurazione di rollout con moderazione in quanto utilizza l’attivatore Al momento della modifica.</p> </td> 
   <td>In caso di modifica</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>Promuovi lancio</td> 
   <td>Configurazione rollout standard per la promozione di pagine di lanci.</td> 
   <td>Al momento del rollout</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> orderChildren<br /> markLiveRelationship</td> 
  </tr> 
  <tr> 
   <td>Configurazione di rollout del contenuto della pagina del catalogo</td> 
   <td>Applica i modelli pagina da una blueprint del catalogo.</td> 
   <td>Al momento del rollout</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> productCreateUpdate<br /> orderChildren</td> 
  </tr> 
  <tr> 
   <td>Configurazione rollout dell'aggiornamento pagina del catalogo</td> 
   <td>Applica le proprietà di destinazione da una blueprint del catalogo. Deve essere eseguito dopo la configurazione di rollout del contenuto della pagina del catalogo.</td> 
   <td>Al momento del rollout</td> 
   <td>catalogRolloutHooks</td> 
  </tr> 
  <tr> 
   <td>Configurazione rollout pubblicazioni DPS</td> 
   <td>Configurazione di rollout della pubblicazione DPS che consente di avviare il processo di rollout all'attivazione del rollout escludendo le proprietà di binding FolioProducer al rollout iniziale</td> 
   <td>Al momento del rollout</td> 
   <td>contentUpdate<br /> contentCopy<br /> contentDelete<br /> referencesUpdate<br /> orderChildren<br /> dpsMetadataFilter</td> 
  </tr> 
  <tr> 
   <td>Configurazione rollout catalogo legacy (5.6.0)</td> 
   <td>Obsoleto. Utilizza Catalog Generator invece di MSM per i rollout di cataloghi.</td> 
   <td>Al momento del rollout</td> 
   <td>editProperties</td> 
  </tr> 
 </tbody> 
</table>

### Azioni di sincronizzazione installate {#installed-synchronization-actions}

Nella tabella seguente sono elencate le azioni di sincronizzazione installate con AEM. Se le azioni installate non soddisfano le tue esigenze, puoi [Creare una nuova azione di sincronizzazione](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action).

<table> 
 <tbody> 
  <tr> 
   <th>Nome azione</th> 
   <th>Descrizione</th> 
   <th>Proprietà<br /> </th> 
  </tr> 
  <tr> 
   <td>contentCopy</td> 
   <td>Quando i nodi dell’origine non esistono nella Live Copy, copia i nodi nella Live Copy. <a href="#excluding-properties-and-node-types-from-synchronization">Configura il servizio CQ MSM Content Copy Action</a> per specificare i tipi di nodo, gli elementi di paragrafo e le proprietà di pagina da escludere. <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>contentDelete</td> 
   <td><p>Elimina i nodi della Live Copy che non esistono nell’origine. <a href="#excluding-properties-and-node-types-from-synchronization">Configura il servizio CQ MSM Content Delete Action</a> per specificare i tipi di nodo, gli elementi di paragrafo e le proprietà di pagina da escludere. </p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>contentUpdate</td> 
   <td>Aggiorna il contenuto della Live Copy con le modifiche dall’origine. <a href="#excluding-properties-and-node-types-from-synchronization">Configura il servizio CQ MSM Content Update Action</a> per specificare i tipi di nodo, gli elementi di paragrafo e le proprietà di pagina da escludere. <br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>editProperties</td> 
   <td><p>Modifica le proprietà della Live Copy. La proprietà editMap determina le proprietà modificate e il relativo valore. Il valore della proprietà editMap deve utilizzare il formato seguente:</p> <p><code>[property_name_1]#[current_value]#</code>[new_value],<br /> <code>[property_name_2]#[current_value]#</code>[new_value],<br /> ...<br /> <code>[property_name_n]#[current_value]#</code>[new_value]</p> <p>La <code>current_value</code> e <code>new_value</code> gli elementi sono espressioni regolari. <br /> </p> <p>Ad esempio, considera il seguente valore per editMap:</p> <p><code>sling:resourceType#/</code>(contentpage|homepage)#/<br /> mobilecontentpage,<br /> cq:template#/contentpage#/mobilecontentpage</p> <p>Questo valore modifica le proprietà dei nodi della Live Copy come segue:</p> 
    <ul> 
     <li>La <code>sling:resourceType</code> proprietà impostate su <code>contentpage</code> o <code>homepage</code> sono impostati su <code>mobilecontentpage.</code></li> 
     <li>Le proprietà <code>cq:template</code> impostate su <code>contentpage</code> vengono impostate su <code>mobilecontentpage.</code></li> 
    </ul> </td> 
   <td><p> </p> <p>editMap: (Stringa) Identifica la proprietà, il valore corrente e il nuovo valore. Per informazioni, consulta Descrizione .<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>notify</td> 
   <td>Invia un evento di pagina per segnalare che la pagina è stata implementata. Per ricevere una notifica, è necessario innanzitutto iscriversi a eventi di rollout.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>orderChildren</td> 
   <td>Nella Live Copy, ordina gli elementi secondari (nodi), in base all’ordine della blueprint<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>referencesUpdate</td> 
   <td><p>Nella Live Copy, questa azione di sincronizzazione aggiorna i riferimenti come i collegamenti.<br /> Cerca i percorsi nelle pagine Live Copy che puntano a una risorsa all’interno della blueprint. Quando viene trovato, aggiorna il percorso in modo che punti alla risorsa correlata all’interno della Live Copy (invece della blueprint). I riferimenti che hanno destinazioni esterne alla blueprint non vengono modificati.</p> <p><a href="#excluding-properties-and-node-types-from-synchronization">Configure il servizio CQ MSM References Update Action</a> per specificare i tipi di nodo, gli elementi di paragrafo e le proprietà di pagina da escludere. </p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetVersion</td> 
   <td><p>Crea una versione della Live Copy.</p> <p>Questa deve essere l’unica azione di sincronizzazione inclusa in una configurazione di rollout.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetActivate</td> 
   <td><p>Attiva la Live Copy.</p> <p>Questa deve essere l’unica azione di sincronizzazione inclusa in una configurazione di rollout.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>targetDeactivate</td> 
   <td><p>Disattiva la Live Copy.</p> <p>Questa deve essere l’unica azione di sincronizzazione inclusa in una configurazione di rollout.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>flusso di lavoro</td> 
   <td><p>Avvia il flusso di lavoro definito dalla proprietà target (solo per le pagine) e considera la Live Copy come payload.</p> <p>Il percorso di destinazione è il percorso del nodo modello.</p> </td> 
   <td>target: (Stringa) Il percorso del modello di flusso di lavoro.<br /> </td> 
  </tr> 
  <tr> 
   <td>obbligatorio</td> 
   <td><p>Imposta l'autorizzazione di diversi ACL nella pagina Live Copy in sola lettura per un gruppo di utenti specifico. Le seguenti ACL sono configurate:</p> 
    <ul> 
     <li>ActionSet.ACTION_NAME_REMOVE</li> 
     <li>ActionSet.ACTION_NAME_SET_PROPERTY</li> 
     <li>ActionSet.ACTION_NAME_ACL_MODIFY</li> 
    </ul> <p>Usa questa azione solo per le pagine.</p> </td> 
   <td>target: (Stringa) L'ID del gruppo per il quale stai impostando le autorizzazioni. <br /> </td> 
  </tr> 
  <tr> 
   <td>mandatoryContent</td> 
   <td><p>Imposta l'autorizzazione di diversi ACL nella pagina Live Copy in sola lettura per un gruppo di utenti specifico. Le seguenti ACL sono configurate:</p> 
    <ul> 
     <li>ActionSet.ACTION_NAME_SET_PROPERTY</li> 
     <li>ActionSet.ACTION_NAME_ACL_MODIFY</li> 
    </ul> <p>Usa questa azione solo per le pagine.</p> </td> 
   <td>target: (Stringa) L'ID del gruppo per il quale stai impostando le autorizzazioni. </td> 
  </tr> 
  <tr> 
   <td>mandatoryStructure</td> 
   <td>Imposta l'autorizzazione dell'ACL ActionSet.ACTION_NAME_REMOVE nella pagina Live Copy in sola lettura per un gruppo di utenti specifico. Usa questa azione solo per le pagine.</td> 
   <td>target: (Stringa) L'ID del gruppo per il quale stai impostando le autorizzazioni. </td> 
  </tr> 
  <tr> 
   <td>VersionCopyAction</td> 
   <td>Se la pagina blueprint/sorgente è stata pubblicata almeno una volta, crea una pagina Live Copy utilizzando la versione pubblicata. Nota: questa azione è disponibile solo per creare una pagina Live Copy basata su una pagina sorgente pubblicata e non per aggiornare una pagina Live Copy esistente. </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>PageMoveAction</td> 
   <td><p>PageMoveAction si applica quando una pagina è stata spostata nella blueprint.</p> <p>L’azione copia invece di spostare la pagina Live Copy (correlata) dalla posizione prima dello spostamento alla posizione successiva.</p> <p>PageMoveAction non modifica la pagina LiveCopy nella posizione precedente allo spostamento. Pertanto, per configurazioni rollout consecutive ha lo stato di un LiveRelationship senza Blueprint.</p> <p><a href="#excluding-properties-and-node-types-from-synchronization">Configura il servizio Azione di spostamento di pagine di CQ MSM</a> per specificare i tipi di nodo, gli elementi di paragrafo e le proprietà di pagina da escludere. </p> <p>Questa deve essere l’unica azione di sincronizzazione inclusa in una configurazione di rollout.</p> </td> 
   <td><p>prop_referenceUpdate: (Booleano) Imposta su true per aggiornare i riferimenti. Il valore predefinito è true.</p> <p> </p> </td> 
  </tr> 
  <tr> 
   <td>productCreateUpdate</td> 
   <td>Crea o aggiorna le risorse Prodotto all’interno di un catalogo. Questa azione è destinata a essere utilizzata in una delle situazioni seguenti: 
    <ul> 
     <li>Generazione o rollout di un catalogo (o sezione di catalogo)</li> 
     <li>Un utente ripristina l’ereditarietà di sincronizzazione per un componente di prodotto.</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>markLiveRelationship</td> 
   <td>Indica una relazione live per il contenuto creato da un lancio.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>catalogRolloutHooks</td> 
   <td>Esegue gli hook di rollout specifici per la generazione del catalogo. Chiama i metodi executePageRolloutHooks ed executeProductRolloutHooks del di CatalogGenerator.<br /> Consulta com.adobe.cq.commerce.pim.api.CatalogGenerator in Javadocs AEM.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>productUpdate</td> 
   <td>Aggiorna le pagine di prodotto in una Live Copy di un catalogo di prodotti</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

### Creazione di una configurazione di rollout {#creating-a-rollout-configuration}

È possibile [creare una configurazione di rollout](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration) quando le configurazioni di rollout installate non soddisfano i requisiti dell&#39;applicazione:

* [Creare la configurazione di rollout](/help/sites-developing/extending-msm.md#create-the-rollout-configuration).
* [Aggiungere azioni di sincronizzazione alla configurazione di rollout](/help/sites-developing/extending-msm.md#add-synchronization-actions-to-the-rollout-configuration).

La nuova configurazione di rollout è quindi disponibile quando imposti le configurazioni di rollout su una pagina blueprint o Live Copy.

### Esclusione delle proprietà e dei tipi di nodo dalla sincronizzazione {#excluding-properties-and-node-types-from-synchronization}

Puoi configurare diversi servizi OSGi che supportano le azioni di sincronizzazione corrispondenti in modo che non influiscano su proprietà e tipi di nodo specifici. Ad esempio, molte proprietà e sottonodi relativi al funzionamento interno di AEM non devono essere inclusi in una Live Copy. Deve essere copiato solo il contenuto rilevante per l’utente della pagina.

Quando si lavora con AEM esistono diversi metodi per gestire le impostazioni di configurazione di tali servizi; vedere [Configurazione di OSGi](/help/sites-deploying/configuring-osgi.md) per ulteriori dettagli e procedure consigliate.

Nella tabella seguente sono elencate le azioni di sincronizzazione per le quali è possibile specificare i nodi da escludere. La tabella fornisce i nomi dei servizi da configurare utilizzando la console Web e il PID per la configurazione tramite un nodo di archivio.

| Azione di sincronizzazione | Nome del servizio nella console Web | Servizio PID |
|---|---|---|
| contentCopy | CQ MSM Content Copy Action | com.day.cq.wcm.msm.impl.actions.ContentCopyActionFactory |
| contentDelete | CQ MSM Content Delete Action | com.day.cq.wcm.msm.impl.actions.ContentDeleteActionFactory |
| contentUpdate | CQ MSM Content Update Action | com.day.cq.wcm.msm.impl.actions.ContentUpdateActionFactory |
| PageMoveAction | CQ MSM Page Move Action | com.day.cq.wcm.msm.impl.actions.PageMoveActionFactory |
| referencesUpdate | CQ MSM References Update Action | com.day.cq.wcm.msm.impl.actions.ReferencesUpdateActionFactory |

La tabella seguente descrive le proprietà che puoi configurare:

<table> 
 <tbody> 
  <tr> 
   <th>Proprietà Console web / Proprietà OSGi</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td><p>Tipi di nodi esclusi</p> <p>cq.wcm.msm.action.excludednodetypes</p> </td> 
   <td>Un’espressione regolare che corrisponde ai tipi di nodo che devono essere esclusi dall’azione di sincronizzazione.</td> 
  </tr> 
  <tr> 
   <td><p>Elementi di paragrafo esclusi</p> <p>cq.wcm.msm.action.excludedparagraphitems</p> </td> 
   <td>Un'espressione regolare che corrisponde agli elementi di paragrafo da escludere dall’azione di sincronizzazione.</td> 
  </tr> 
  <tr> 
   <td><p>Proprietà pagina escluse</p> <p>cq.wcm.msm.action.excludedprops</p> </td> 
   <td>Un’espressione regolare che corrisponde alle proprietà della pagina da escludere dall’azione di sincronizzazione.</td> 
  </tr> 
  <tr> 
   <td><p>Tipi di nodi Mixin ignorati</p> <p>cq.wcm.msm.action.ignoredMixin</p> </td> 
   <td>Disponibile solo per l’azione di aggiornamento dei contenuti di CQ MSM. Un'espressione regolare che corrisponde ai nomi dei tipi di nodo mixin da escludere dall'azione di sincronizzazione.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Nell’interfaccia classica, l’icona di blocco visualizzata nella finestra di dialogo Proprietà pagina per le pagine LiveCopy non riflette la configurazione della proprietà Proprietà pagina escluse. L’icona a forma di lucchetto viene visualizzata anche per le proprietà escluse dall’azione di sincronizzazione.

>[!NOTE]
>
>Nell’interfaccia touch vedi anche [Configurazione dei blocchi MSM nelle proprietà di pagina)](/help/sites-developing/extending-msm.md).

#### Azione di aggiornamento dei contenuti di CQ MSM - Esclusioni {#cq-msm-content-update-action-exclusions}

Diverse proprietà e tipi di nodo sono esclusi per impostazione predefinita, questi sono definiti nella configurazione OSGi di **Azione di aggiornamento dei contenuti di CQ MSM**, **Proprietà pagina escluse**.

Per impostazione predefinita, le proprietà che corrispondono alle seguenti espressioni regolari vengono escluse (cioè non aggiornate) durante il rollout:

![chlimage_1-18](assets/chlimage_1-18.png)

Puoi modificare le espressioni che definiscono l’elenco di esclusione secondo le tue esigenze.

Ad esempio, se desideri includere il **Titolo** della pagina nelle modifiche considerate per il rollout, rimuovi `jcr:title` dalle esclusioni. Ad esempio, con il codice regex:

`jcr:(?!(title)$).*`

### Configurazione della sincronizzazione per l’aggiornamento dei riferimenti {#configuring-synchronization-for-updating-references}

Puoi configurare diversi servizi OSGi che supportano le azioni di sincronizzazione corrispondenti, relative all’aggiornamento dei riferimenti.

Quando si lavora con AEM esistono diversi metodi per gestire le impostazioni di configurazione di tali servizi; vedere [Configurazione di OSGi](/help/sites-deploying/configuring-osgi.md) per ulteriori dettagli e procedure consigliate.

Nella tabella seguente sono elencate le azioni di sincronizzazione per cui è possibile specificare l’aggiornamento dei riferimenti. La tabella fornisce i nomi dei servizi da configurare utilizzando la console Web e il PID per la configurazione tramite un nodo di archivio.

<table> 
 <tbody> 
  <tr> 
   <th>Proprietà Console web / Proprietà OSGi</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td><p>Aggiornare il riferimento tra LiveCopy nidificate</p> <p>cq.wcm.msm.impl.action.referencesupdate.prop_updateNested</p> </td> 
   <td>Disponibile solo per l’azione di aggiornamento dei riferimenti di CQ MSM. Seleziona questa opzione (Console web) o imposta questa proprietà booleana su true (configurazione archivio) per sostituire i riferimenti a qualsiasi risorsa all’interno del ramo della Live Copy principale.</td> 
  </tr> 
  <tr> 
   <td><p>Aggiornare le pagine di riferimento</p> <p>cq.wcm.msm.impl.actions.pagemove.prop_referenceUpdate</p> </td> 
   <td>Disponibile solo per l’azione Sposta pagina di CQ MSM. Seleziona questa opzione (Console web) o imposta questa proprietà booleana su <code>true</code> (configurazione archivio) per aggiornare tutti i riferimenti per utilizzare la pagina originale per fare riferimento invece alla pagina LiveCopy.</td> 
  </tr> 
 </tbody> 
</table>

## Specifica delle configurazioni di rollout da utilizzare {#specifying-the-rollout-configurations-to-use}

MSM consente di specificare set di configurazioni di rollout che vengono utilizzate in genere e, quando necessario, è possibile sostituirle per specifiche Live Copy. MSM fornisce diverse posizioni per specificare le configurazioni di rollout da utilizzare. La posizione determina se la configurazione si applica a una Live Copy specifica.

Il seguente elenco di posizioni in cui è possibile specificare le configurazioni di rollout da utilizzare descrive come MSM determina quali configurazioni di rollout utilizzare per una Live Copy:

* **[Proprietà pagina Live Copy](/help/sites-administering/msm-sync.md#setting-the-rollout-configurations-for-a-live-copy-page):** Quando una pagina Live Copy è configurata per l’utilizzo di una o più configurazioni di rollout, MSM utilizza tali configurazioni di rollout.
* **[Proprietà pagina blueprint](/help/sites-administering/msm-sync.md#setting-the-rollout-configuration-for-a-blueprint-page):** Quando una Live Copy è basata su una blueprint e la pagina Live Copy non è configurata con una configurazione di rollout, viene utilizzata la configurazione di rollout associata alla pagina blueprint sorgente.
* **Proprietà della pagina padre della Live Copy:** Quando né la pagina Live Copy né la pagina sorgente blueprint sono configurate con una configurazione di rollout, viene utilizzata la configurazione di rollout che si applica alla pagina padre della pagina Live Copy.
* **[Impostazione predefinita del sistema](/help/sites-administering/msm-sync.md#setting-the-system-default-rollout-configuration):** Quando non è possibile determinare la configurazione di rollout della pagina padre della Live Copy, viene utilizzata la configurazione di rollout predefinita del sistema.

Ad esempio, una blueprint utilizza il sito di riferimento We.Retail come contenuto sorgente. Un sito viene creato dalla blueprint. Ogni voce nell’elenco seguente descrive uno scenario diverso per quanto riguarda l’utilizzo delle configurazioni di rollout:

* Nessuna delle pagine blueprint o Live Copy è configurata per l’utilizzo di una configurazione di rollout. MSM utilizza la configurazione di rollout predefinita del sistema per tutte le pagine Live Copy.
* La pagina principale del sito di riferimento We.Retail è configurata con diverse configurazioni di rollout. MSM utilizza queste configurazioni di rollout per tutte le pagine Live Copy.
* La pagina principale del sito di riferimento We.Retail è configurata con diverse configurazioni di rollout e la pagina principale del sito Live Copy è configurata con un diverso set di configurazioni di rollout. MSM utilizza le configurazioni di rollout configurate nella pagina principale del sito Live Copy.

### Impostazione delle configurazioni di rollout per una pagina Live Copy {#setting-the-rollout-configurations-for-a-live-copy-page}

Configura una pagina Live Copy con le configurazioni di rollout da utilizzare quando la pagina sorgente viene soggetta a rollout. Per impostazione predefinita, le pagine secondarie ereditano la configurazione. Quando configuri la configurazione di rollout da utilizzare, sovrascrivi la configurazione che la pagina Live Copy eredita dal relativo elemento padre.

Puoi anche configurare le configurazioni di rollout per una pagina Live Copy quando [crea la Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page).

1. Utilizza la **Sites** per selezionare la pagina Live Copy.

1. Seleziona **Proprietà** nella barra degli strumenti.
1. Apri la scheda **Live Copy.**

   La sezione **Configurazione** mostra le configurazioni di rollout ereditate dalla pagina.

   ![chlimage_1-19](assets/chlimage_1-19.png)

1. Se necessario, regola il flag **Ereditarietà Live Copy**. Se questa opzione è selezionata, la configurazione Live Copy ha effetto su tutti gli elementi figlio.

1. Elimina **Eredita configurazione di rollout da padre** , quindi seleziona una o più configurazioni di rollout dall&#39;elenco.

   Le configurazioni di rollout selezionate vengono visualizzate sotto l’elenco a discesa.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Tocca o fai clic su **Salva**.

### Impostazione della configurazione di rollout per una pagina Blueprint {#setting-the-rollout-configuration-for-a-blueprint-page}

Configura una pagina blueprint con le configurazioni di rollout da utilizzare quando la pagina blueprint viene implementata.

Le pagine figlie della pagina blueprint ereditano la configurazione. Quando configuri la configurazione di rollout da utilizzare, potresti sovrascrivere la configurazione che la pagina eredita dal suo elemento padre.

1. Utilizza la console **Sites** per selezionare la pagina principale della blueprint.
1. Seleziona **Proprietà** nella barra degli strumenti.
1. Apri la scheda **Blueprint.**
1. Seleziona una o più **Configurazioni di rollout** con il selettore a discesa.
1. Per confermare gli aggiornamenti, seleziona **Salva**.

### Impostazione della configurazione di rollout predefinita del sistema {#setting-the-system-default-rollout-configuration}

Specifica una configurazione di rollout da utilizzare come impostazione predefinita del sistema. Per specificare il valore predefinito, configura il servizio OSGi:

* **Day CQ WCM Live Relationship Manager**
il PID del servizio è 
`com.day.cq.wcm.msm.impl.LiveRelationshipManagerImpl`

Configura il servizio utilizzando [Console web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) o [nodo del repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository).

* Nella console web, il nome della proprietà da configurare è Default rollout config.
* Utilizzando un nodo di archivio, il nome della proprietà da configurare è `liverelationshipmgr.relationsconfig.default`.

Imposta il valore di questa proprietà sul percorso della configurazione di rollout da utilizzare come impostazione predefinita del sistema. Il valore predefinito è `/libs/msm/wcm/rolloutconfigs/default`, che corrisponde alla **Configurazione di rollout standard**.
