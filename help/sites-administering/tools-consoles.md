---
title: Console Strumenti
description: Scopri le diverse console di strumenti di Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
translation-type: tm+mt
source-git-commit: 425f1e6288cfafc3053877a43fa0a20fd5d2f3ac
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 34%

---


# Console Strumenti{#tools-consoles}

Le console **Strumenti** permettono di accedere a console e strumenti specifici per la gestione di siti web, risorse digitali e altri aspetti dell’archivio dei contenuti. Esistono attualmente due versioni della console **Strumenti** a seconda dell&#39;interfaccia in uso:

* [Strumenti - Interfaccia classica](#tools-classic-ui)
* [Strumenti - Interfaccia touch](#tools-touch-optimized-ui)

## Strumenti - Interfaccia classica {#tools-classic-ui}

<table> 
 <tbody> 
  <tr> 
   <th>Pagina o cartella</th> 
   <th> </th> 
   <th>Scopo</th> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">Centro di controllo MSM</a></td> 
   <td> </td> 
   <td>Punto centralizzato per la gestione di più siti.</td> 
  </tr> 
  <tr> 
   <td>Configurazioni ClientContext<br /> </td> 
   <td> </td> 
   <td>Il <a href="/help/sites-developing/client-context.md">Client Context</a> rappresenta una raccolta di dati utente assemblata in modo dinamico. Le configurazioni predefinite e di Marketing Cloud si trovano qui.<br /> </td> 
  </tr> 
  <tr> 
   <td>Configurazioni servizi cloud<br /> </td> 
   <td> </td> 
   <td>Contiene configurazioni relative a <a href="/help/sites-administering/marketing-cloud.md">Integrazione con Adobe Marketing Cloud</a>.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">Commerce</a></td> 
   <td> </td> 
   <td>Consente l'accesso a importatori e a vari dati di prodotto.</td> 
  </tr> 
  <tr> 
   <td>DAM - Digital Rights Management<br /> </td> 
   <td> </td> 
   <td>Consente l'accesso alle informazioni sui diritti digitali e alle licenze.</td> 
  </tr> 
  <tr> 
   <td>DAM - Controllo integrità<br /> </td> 
   <td> </td> 
   <td>Confronta <code>/var/dam</code> e <code>/content/dam</code> e verifica eventuali incongruenze. <br /> È quindi possibile sincronizzare o eliminare tutti i file/cartelle elencati. I tipi di nodo per il confronto delle cartelle sono configurabili nella console Web.</td> 
  </tr> 
  <tr> 
   <td>DAM -  Adobe Indesign<br /> </td> 
   <td> </td> 
   <td>Script da utilizzare insieme a  Adobe Indesign.</td> 
  </tr> 
  <tr> 
   <td>DAM - Profili video<br /> </td> 
   <td> </td> 
   <td>Profili configurabili per le transcodifiche ffmpeg.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">Dashboard</a></td> 
   <td> </td> 
   <td>Consente di creare dashboard di reporting; questi forniscono un modo personalizzabile per definire le pagine che visualizzano dati consolidati.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">Progettazione</a></td> 
   <td> </td> 
   <td>Contiene l'elenco delle progettazioni definite, inclusi i file di grafica e css da utilizzare.</td> 
  </tr> 
  <tr> 
   <td>Documentazione personalizzata</td> 
   <td> </td> 
   <td>Utilizzato per estendere la documentazione e la guida in linea.</td> 
  </tr> 
  <tr> 
   <td>Invii modulo</td> 
   <td> </td> 
   <td>Contiene l'elenco degli invii di moduli ricevuti.</td> 
  </tr> 
  <tr> 
   <td>Importatori - <a href="/help/sites-administering/bulk-editor.md">Bulk Editor</a></td> 
   <td> </td> 
   <td>Consente di cercare gli elementi e modificarli in blocco. Potete anche esportare e importare contenuti (in blocco) nella directory archivio.</td> 
  </tr>
  <tr> 
   <td>Importazione - Feed Importer</td> 
   <td> </td> 
   <td><p>Feed Importer è un framework per importare ripetutamente contenuti da origini esterne nel repository. L'idea di Feed Importer è di eseguire il polling di una risorsa remota a un intervallo specificato, di analizzarla e di creare nodi nell'archivio del contenuto che rappresentano il contenuto della risorsa remota.</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">Verifica collegamenti esterni</a></td> 
   <td> </td> 
   <td>Esegue l'analisi di tutte le pagine di contenuto all'interno dell'istanza AEM e verifica eventuali collegamenti esterni. Viene visualizzato un elenco di collegamenti validi e non validi.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">Mobile</a></td> 
   <td> </td> 
   <td>Consente di creare siti Web progettati per dispositivi mobili.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>Gestisce contenuti multilingue e multinazionali, aiutandoti a bilanciare il branding centralizzato con contenuti localizzati.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">Notifica</a></td> 
   <td> </td> 
   <td>Modelli di notifica.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">Pacchetti</a></td> 
   <td> </td> 
   <td>Un collegamento alternativo a Gestione pacchetti che mostra i pacchetti caricati per AEM WCM. Simili alle informazioni visualizzate in Gestione pacchetti di CRX.</td> 
  </tr> 
  <tr> 
   <td>Replica - <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">Agenti di replica</a></td> 
   <td> </td> 
   <td>Utilizzato per replicare i dati dall’autore alla pubblicazione al momento della pubblicazione delle pagine o con replica inversa per restituire i commenti degli utenti dall’ambiente di pubblicazione all’autore.</td> 
  </tr> 
  <tr> 
   <td>Importatori - <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">Attiva albero</a></td> 
   <td> </td> 
   <td>La scheda Siti Web consente di attivare le singole pagine. Se tuttavia è stato inserito o aggiornato un numero considerevole di pagine di contenuto, tutte residenti sotto la stessa pagina principale, può essere più semplice attivare l’intero albero con una singola azione. È anche possibile eseguire una prova per simulare l’attivazione e determinare le pagine da attivare.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">Rapporti</a></td> 
   <td> </td> 
   <td>AEM offre una serie di rapporti personalizzati, che consentono di creare rapporti personalizzati e/o di sviluppare rapporti personalizzati.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">Scaffolding pagine predefinito</a></td> 
   <td> </td> 
   <td>Con la funzione di scaffolding è invece possibile creare un modulo (scaffolding significa letteralmente impalcatura) con i campi necessari per creare la struttura desiderata per le pagine e quindi utilizzare il modulo per creare agevolmente pagine basate su tale struttura.</td> 
  </tr> 
  <tr> 
   <td>Sicurezza - <a href="/help/sites-administering/notification.md">Configurazione self-service </a> </td> 
   <td> </td> 
   <td>Consente di configurare le e-mail che gli utenti ricevono automaticamente quando creano un account o reimpostano una password e di confermare una password che è stata reimpostata.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">Segmentazione</a></td> 
   <td> </td> 
   <td>I visitatori che arrivano a un sito hanno interessi e obiettivi diversi. Per il successo di operazioni di marketing online, è importante comprendere tali obiettivi e soddisfare le aspettative dei visitatori. La segmentazione consente di ottenere questo risultato analizzando e caratterizzando i dettagli di un visitatore.<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>Configurazione SRP predefinita. Vedere <a href="/help/communities/srp-config.md">Console Storage Configuration</a>.</td> 
  </tr> 
  <tr> 
   <td>gestione attività</td> 
   <td> </td> 
   <td>Nessuna funzionalità attiva correlata a questa voce.</td> 
  </tr> 
  <tr> 
   <td>inquilini</td> 
   <td> </td> 
   <td>Nessuna funzionalità attiva correlata a questa voce.</td> 
  </tr> 
  <tr> 
   <td>Versioni - <a href="/help/sites-deploying/version-purging.md">Rimuovi versioni</a></td> 
   <td> </td> 
   <td>Consente di eliminare le versioni delle pagine come necessario.</td> 
  </tr> 
  <tr> 
   <td>Repository virtuali</td> 
   <td> </td> 
   <td>È possibile impostare un repository virtuale utilizzando la funzione di montaggio dell'area di lavoro per fornire alle applicazioni di contenuto abilitate per JCR l'accesso semplificato all'infrastruttura di contenuto JCR basata su CRX e sui connettori JCR.</td> 
  </tr> 
  <tr> 
   <td>watchwords</td> 
   <td> </td> 
   <td>Obsoleto. Vedere <a href="/help/communities/moderate-ugc.md#watchwords">Moderazione dei contenuti della community</a></td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/workflows.md">Flusso di lavoro</a></td> 
   <td> </td> 
   <td>I flussi di lavoro controllano una serie di azioni su pagine o risorse digitali che supportano qualsiasi processo editoriale.</td> 
  </tr> 
 </tbody> 
</table>

## Strumenti - Interfaccia touch {#tools-touch-optimized-ui}

<table> 
 <tbody> 
  <tr> 
   <th>Sezione</th> 
   <th>Opzione</th> 
   <th>Scopo</th> 
  </tr> 
  <tr> 
   <td>Authoring  </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-classic-ui-authoring/classic-personalization-campaigns.md">Campagne</a></td> 
   <td>Gestisci le campagne marketing</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/launches.md">Lanci</a></td> 
   <td>Gestione dei lanci marketing</td> 
  </tr> 
  <tr> 
   <td>Attività</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/task-content.md">Casella in entrata</a></td> 
   <td>Gestire gli elementi Inbox.</td> 
  </tr> 
  <tr> 
   <td>Operazioni</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/security.md">Utenti e gruppi </a></td> 
   <td>Gestione degli utenti e gruppi.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-authoring/tags.md">Gestione tag</a></td> 
   <td>Organizzazione dei tag e namespace.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="https://helpx.adobe.com/cloud-manager/using/using-cloud-manager.html">Cloud Services</a></td> 
   <td>Connessione ad Adobe Marketing Cloud.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/workflows.md">Flussi di lavoro</a></td> 
   <td>Modellazione e gestione dei flussi di lavoro.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/replication.md">Replica</a></td> 
   <td>Creare e gestire più siti Web.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/reporting.md">Rapporti</a></td> 
   <td>Creazione e monitoraggio di report personalizzati.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/hobbes.md">Test</a></td> 
   <td>Esecuzione di test definiti per l'applicazione.</td> 
  </tr> 
  <tr> 
   <td>Operazioni Granite</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-developing/developing-with-crxde-lite.md">CRXDE Lite</a></td> 
   <td>Sviluppo di applicazioni con IDE basata sul Web.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md">Pacchetti</a></td> 
   <td>Creazione pacchetti e condivisione di applicazioni.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-administering/package-manager.md#package-share">Condivisione pacchetti</a></td> 
   <td>Download delle applicazioni da Adobe e dalla community.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md#administering-topologies">Browser topologia</a></td> 
   <td>Visualizzazione della topologia delle istanze.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/offloading.md">Offload del browser</a></td> 
   <td>Gestire lo scaricamento.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#backups">Backup</a></td> 
   <td>Esecuzione di attività di backup.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Console Web<br /> </td> 
   <td>Configurazione e gestione della piattaforma dell'applicazione.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Immagine configurazione console Web<br /> </td> 
   <td>Scaricate lo stato di configurazione dalla console Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Utenti</td> 
   <td>Gestione degli utenti.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Gruppi</td> 
   <td>Gestione dei gruppi.</td> 
  </tr> 
  <tr> 
   <td>Risorse esterne<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Documentazione</td> 
   <td>Documentazione di Web Experience Management.<br /> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Riferimenti per sviluppatori</td> 
   <td>Riferimenti e download per sviluppatori.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alcune delle opzioni precedenti sono effettivamente collegate all’interfaccia classica.

