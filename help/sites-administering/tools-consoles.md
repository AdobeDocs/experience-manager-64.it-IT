---
title: Console Strumenti
description: Scopri le diverse console Strumenti disponibili in Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
exl-id: 7566e1bc-8571-4b3c-b420-4324026bd4dd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 20%

---

# Console Strumenti{#tools-consoles}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le console **Strumenti** permettono di accedere a console e strumenti specifici per la gestione di siti web, risorse digitali e altri aspetti dell’archivio dei contenuti. Attualmente esistono due sapori del **Strumenti** a seconda dell’interfaccia in uso:

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
   <td>Configurazioni del contesto client<br /> </td> 
   <td> </td> 
   <td>La <a href="/help/sites-developing/client-context.md">Contesto client</a> rappresenta una raccolta di dati utente assemblata in modo dinamico. Le configurazioni predefinite e di marketing cloud si trovano qui.<br /> </td> 
  </tr> 
  <tr> 
   <td>Configurazioni servizi cloud<br /> </td> 
   <td> </td> 
   <td>Configurazioni dei blocchi relative a <a href="/help/sites-administering/marketing-cloud.md">Integrazione con Adobe Marketing Cloud</a>.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/ecommerce.md">Commerce</a></td> 
   <td> </td> 
   <td>Consente l'accesso agli importatori e a vari dati di prodotto.</td> 
  </tr> 
  <tr> 
   <td>DAM - Digital Rights Management<br /> </td> 
   <td> </td> 
   <td>Consente l'accesso a informazioni e licenze per i diritti digitali.</td> 
  </tr> 
  <tr> 
   <td>DAM - Verifica stato<br /> </td> 
   <td> </td> 
   <td>Confronti <code>/var/dam</code> e <code>/content/dam</code> e controlla<br /> eventuali incongruenze. Tutti i file/cartelle elencati possono quindi essere sincronizzati o eliminati. I tipi di nodo per il confronto delle cartelle sono configurabili nella console Web.</td> 
  </tr> 
  <tr> 
   <td>DAM - Adobe Indesign<br /> </td> 
   <td> </td> 
   <td>Script da utilizzare in combinazione con Adobe Indesign.</td> 
  </tr> 
  <tr> 
   <td>DAM - Profili video<br /> </td> 
   <td> </td> 
   <td>Profili configurabili per le transcodings ffmpeg.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/dashboards.md">Dashboard</a></td> 
   <td> </td> 
   <td>Consente di creare dashboard di reporting; queste forniscono un modo personalizzabile per definire pagine che visualizzano dati consolidati.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-developing/designer.md">Disegni</a></td> 
   <td> </td> 
   <td>Contiene l’elenco delle progettazioni definite, inclusi i file grafici e css da utilizzare.</td> 
  </tr> 
  <tr> 
   <td>Documentazione personalizzata</td> 
   <td> </td> 
   <td>Utilizzato per l’estensione della documentazione e della guida in linea.</td> 
  </tr> 
  <tr> 
   <td>Invii modulo</td> 
   <td> </td> 
   <td>Contiene l’elenco degli invii dei moduli ricevuti.</td> 
  </tr> 
  <tr> 
   <td>Importatori - <a href="/help/sites-administering/bulk-editor.md">Editor in serie</a></td> 
   <td> </td> 
   <td>Consente di cercare gli elementi e modificarli in blocco. Puoi anche esportare e importare contenuti (in blocco) nell’archivio.</td> 
  </tr>
  <tr> 
   <td>Importazione - Importazione feed</td> 
   <td> </td> 
   <td><p>Importazione feed è un framework per importare ripetutamente contenuti da fonti esterne nell’archivio. L’idea di Importazione feed è quella di eseguire il polling di una risorsa remota a un intervallo specificato, di analizzarla e di creare nodi nell’archivio dei contenuti che rappresentano il contenuto della risorsa remota.</p> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/external-link-checker.md">Verifica collegamenti esterni</a></td> 
   <td> </td> 
   <td>Esegue l'analisi di tutte le pagine di contenuto all'interno dell'istanza AEM e controlla eventuali collegamenti esterni. Viene visualizzato un elenco di collegamenti validi e non validi.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/mobile.md">Mobile</a></td> 
   <td> </td> 
   <td>Consente di creare siti web progettati per dispositivi mobili.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/msm.md">MSM</a></td> 
   <td> </td> 
   <td>Gestisce i contenuti multilingue e multinazionali, aiutandoti a bilanciare il branding centralizzato con contenuti localizzati.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/notification.md">Notifica</a></td> 
   <td> </td> 
   <td>Modelli di notifica.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/package-manager.md">Pacchetti</a></td> 
   <td> </td> 
   <td>Un collegamento alternativo a Gestione pacchetti che mostra i pacchetti caricati per AEM WCM. Simile alle informazioni visualizzate in Gestione pacchetti di CRX.</td> 
  </tr> 
  <tr> 
   <td>Replica <a href="/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents">Agenti di replica</a></td> 
   <td> </td> 
   <td>Utilizzato per replicare i dati dall’autore alla pubblicazione durante la pubblicazione delle pagine o con replica inversa per restituire i commenti degli utenti dall’ambiente di pubblicazione all’autore.</td> 
  </tr> 
  <tr> 
   <td>Importatori - <a href="/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree">Attiva albero</a></td> 
   <td> </td> 
   <td>Dalla scheda Siti web è possibile attivare le singole pagine. Dopo aver inserito o aggiornato un numero considerevole di pagine di contenuto, tutte residenti sotto la stessa pagina principale, può essere più semplice attivare l’intero albero con una singola azione. Puoi anche eseguire una prova per simulare un’attivazione ed evidenziare le pagine da attivare.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/reporting.md">Rapporti</a></td> 
   <td> </td> 
   <td>AEM fornisce una serie di report personalizzati, ti consente di creare report personalizzati e/o di svilupparne uno personalizzato.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-authoring/scaffolding.md">Scaffolding pagine predefinito</a></td> 
   <td> </td> 
   <td>Con la pagina di scaffolding è possibile creare un modulo (scaffolding) con campi che riflettono la struttura desiderata per le pagine e quindi utilizzare il modulo per creare facilmente pagine basate su questa struttura.</td> 
  </tr> 
  <tr> 
   <td>Sicurezza - <a href="/help/sites-administering/notification.md">Configurazione self-service </a> </td> 
   <td> </td> 
   <td>Consente di configurare le e-mail che gli utenti ricevono automaticamente quando creano un account o reimpostano una password e di confermare una password reimpostata.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/sites-administering/campaign-segmentation.md">Segmentazione</a></td> 
   <td> </td> 
   <td>I visitatori del sito hanno interessi e obiettivi diversi quando accedono a un sito. Comprendere questi obiettivi e soddisfare le aspettative è un importante fattore di successo per il marketing online. La segmentazione consente di ottenere questo risultato analizzando e caratterizzando i dettagli di un visitatore.<br /> </td> 
  </tr> 
  <tr> 
   <td><a href="/help/communities/working-with-srp.md">socialconfig</a></td> 
   <td> </td> 
   <td>Configurazione SRP predefinita. Vedi <a href="/help/communities/srp-config.md">Configurazione dell'archiviazione</a> console.</td> 
  </tr> 
  <tr> 
   <td>gestione delle attività</td> 
   <td> </td> 
   <td>Nessuna funzionalità attiva correlata a questa voce.</td> 
  </tr> 
  <tr> 
   <td>inquilini</td> 
   <td> </td> 
   <td>Nessuna funzionalità attiva correlata a questa voce.</td> 
  </tr> 
  <tr> 
   <td>Controllo delle versioni - <a href="/help/sites-deploying/version-purging.md">Eliminare le versioni</a></td> 
   <td> </td> 
   <td>Consente di eliminare le versioni della pagina in base alle esigenze.</td> 
  </tr> 
  <tr> 
   <td>Repository virtuali</td> 
   <td> </td> 
   <td>È possibile impostare un archivio virtuale utilizzando la funzione di montaggio dell’area di lavoro per fornire alle applicazioni di contenuto abilitate per JCR un accesso semplificato all’infrastruttura di contenuto JCR basata su CRX e sui connettori JCR.</td> 
  </tr> 
  <tr> 
   <td>parole d'ordine</td> 
   <td> </td> 
   <td>Obsoleto. Vedi <a href="/help/communities/moderate-ugc.md#watchwords">Moderazione dei contenuti della community</a></td> 
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
   <td>Gestisci gli elementi della Posta in arrivo.</td> 
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
   <td><a href="https://helpx.adobe.com/cloud-manager/using/using-cloud-manager.html">Servizi cloud</a></td> 
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
   <td>Creazione e gestione di più siti web.</td> 
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
   <td>Gestisci lo scaricamento.</td> 
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
   <td>Scarica lo stato di configurazione dalla console web.<br /> </td> 
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
   <td>Risorse per sviluppatori</td> 
   <td>Riferimenti e download per sviluppatori.</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alcune delle opzioni di cui sopra si collegano effettivamente all’interfaccia classica.
