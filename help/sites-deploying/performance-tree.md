---
title: Struttura delle prestazioni
seo-title: Performance Tree
description: Scopri i passaggi da seguire per risolvere i problemi di prestazioni in AEM.
seo-description: Learn about the steps that need to be taken in order to troubleshoot performance issues in AEM.
uuid: ab0624f7-6b39-4255-89e0-54c74b54cd98
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 5febbb1e-795c-49cd-a8f4-c6b4b540673d
exl-id: dfc6a660-e6b3-4395-a555-f4cf8f3fed91
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1224'
ht-degree: 6%

---

# Struttura delle prestazioni{#performance-tree}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Ambito {#scope}

Il diagramma seguente fornisce indicazioni sui passaggi da intraprendere per risolvere i problemi di prestazioni. È suddiviso in 5 sezioni per facilitarne la lettura.

Ogni passaggio nel diagramma è collegato a una risorsa della documentazione o a una raccomandazione.

## Prerequisiti e supposizioni {#prerequisites-and-assumptions}

Il presupposto è che un problema di prestazioni venga osservato in una determinata pagina (una console AEM o una pagina web) e possa essere riprodotto in modo coerente. La possibilità di testare o monitorare le prestazioni è un requisito preliminare prima di avviare l&#39;indagine.

L’analisi inizia al passaggio 0. L’obiettivo è quello di determinare quale entità (dispatcher, host esterno o AEM) è responsabile del problema di prestazioni, quindi determinare quale area (server o rete) deve essere esaminata.

### Sezione 1 {#section}

![chlimage_1-103](assets/chlimage_1-103.png)

### Sezione 2 {#section-1}

![chlimage_1-104](assets/chlimage_1-104.png)

### Sezione 3 {#section-2}

![chlimage_1-105](assets/chlimage_1-105.png)

### Sezione 4 {#section-3}

![chlimage_1-106](assets/chlimage_1-106.png)

### Sezione 5 {#section-4}

![chlimage_1-107](assets/chlimage_1-107.png)

## Collegamenti di riferimento {#reference-links}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Passaggio</strong></td> 
   <td><strong>Titolo</strong></td> 
   <td><strong>Riferimenti</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 0</strong></td> 
   <td>Analizza flusso di richieste</td> 
   <td><p>Puoi utilizzare l’analisi standard delle richieste HTTP nel browser per analizzare il flusso delle richieste. Per ulteriori informazioni su come eseguire questa operazione su Chrome, vedi:<br /> </p> <p><a href="https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/resource-loading">https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/resource-loading</a><a href="https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/understanding-resource-timing"><br /> https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/understanding-resource-timing</a><br /> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 2</strong></td> 
   <td>Le richieste provengono da host esterni?</td> 
   <td>Puoi utilizzare l’analisi standard delle richieste HTTP nel browser per analizzare il flusso delle richieste. Vedi i collegamenti di cui sopra su come eseguire questa operazione su Chrome.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 3</strong></td> 
   <td>Le richieste possono essere memorizzate nella cache?</td> 
   <td>Per ulteriori informazioni sulle richieste memorizzabili nella cache e sui consigli generali per l’ottimizzazione delle prestazioni del dispatcher, vedi <a href="/help/sites-deploying/configuring-performance.md#optimizing-performance-when-using-the-dispatcher">Ottimizzazione delle prestazioni del dispatcher</a>.</td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 4</strong></td> 
   <td>Le richieste vengono dal Dispatcher?</td> 
   <td><p>Controlla la <a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#debugging">Documentazione sul debug di Dispatcher</a> per vedere se le richieste sono memorizzate nella cache correttamente.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 5</strong></td> 
   <td>Dispatcher sta tentando di autenticare ogni richiesta tramite AEM?</td> 
   <td>Controlla se il dispatcher invia <code>HEAD</code> richiede a AEM l’autenticazione prima di distribuire la risorsa in cache. Puoi farlo cercando <code>HEAD</code> richieste in AEM <code>access.log</code>. Per ulteriori informazioni, consulta <a href="/help/sites-deploying/configure-logging.md">Registrazione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 6</strong></td> 
   <td>La posizione geografica del Dispatcher è lontana dagli utenti?</td> 
   <td>Sposta il Dispatcher più vicino agli utenti.</td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 7</strong></td> 
   <td>Il livello di rete del Dispatcher è OK?</td> 
   <td><br /> Esaminare il livello di rete per i problemi di saturazione e latenza.<p> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 8</strong></td> 
   <td>La lentezza è riproducibile con un'istanza locale?</td> 
   <td><br /> <p>Utilizzo <a href="/help/sites-developing/tough-day.md">Giorno difficile</a> per replicare le condizioni del "mondo reale" dalle istanze di produzione. Se questo non è realistico per lo spazio di sviluppo, assicurati di testare l’istanza di produzione (o una fase di staging identica) in un contesto di rete diverso.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 9</strong></td> 
   <td>La posizione geografica del server è lontana dagli utenti?</td> 
   <td>Sposta il server più vicino agli utenti.</td> 
  </tr> 
  <tr> 
   <td><strong>Passaggi 10 e 29</strong></td> 
   <td>Indagare il livello di rete</td> 
   <td><p>Esaminare il livello di rete per i problemi di saturazione e latenza.</p> <p>Per il livello di authoring, si consiglia di non superare i 100 millisecondi.</p> <p>Per ulteriori informazioni sui suggerimenti per l'ottimizzazione delle prestazioni, vedi <a href="https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html">questa pagina</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 11</strong></td> 
   <td>Sposta il server più vicino o aggiungi uno per area geografica</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 12</strong></td> 
   <td>Risoluzione dei problemi AEM server</td> 
   <td>Per ulteriori informazioni, consulta i seguenti passaggi secondari nel diagramma.</td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 13</strong></td> 
   <td>Controllare i requisiti hardware</td> 
   <td>Controlla la documentazione su <a href="/help/managing/hardware-sizing-guidelines.md">Linee guida per il dimensionamento dell'hardware</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 14</strong></td> 
   <td>Verifica delle cause frequenti dei problemi di prestazioni</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 15</strong></td> 
   <td>Trova richieste lente</td> 
   <td><p>Puoi verificare la presenza di richieste lente analizzando la variabile <code>request.log</code> o utilizzando <code>rlog.jar</code>.</p> <p>Per ulteriori informazioni sull'utilizzo di rlog.jar, consulta questa pagina.</p> <p>Vedi <a href="/help/sites-deploying/monitoring-and-maintaining.md#using-rlog-jar-to-find-requests-with-long-duration-times">Utilizzo di rlog.jar per trovare le richieste con tempi lunghi</a>.<br /> </p> <p> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 16</strong></td> 
   <td>Server dei profili</td> 
   <td><p>Per informazioni sugli strumenti di profilatura utilizzabili con AEM, consulta <a href="/help/sites-deploying/monitoring-and-maintaining.md#tools-for-monitoring-and-analyzing-performance">Strumenti per il monitoraggio e l’analisi delle prestazioni</a>.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 17</strong></td> 
   <td>Trova metodi lenti nel profiling</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 18</strong></td> 
   <td>Scenari comuni di profilazione</td> 
   <td>Vedi <a href="/help/sites-deploying/monitoring-and-maintaining.md#analyzing-specific-scenarios">Analisi di scenari specifici</a> nella sezione Ottimizzazione delle prestazioni .<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 19</strong></td> 
   <td>CPU al 100%</td> 
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance">https://helpx.adobe.com/experience-manager/6-3/sites-deploying/monitoring-and-maintaining.html#MonitoringPerformance</a></td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 20</strong></td> 
   <td>Memoria esaurita</td> 
   <td><br /> 
    <ol> 
     <li><a href="/help/sites-deploying/monitoring-and-maintaining.md#out-of-memory">Memoria esaurita</a></li> 
     <li><a href="/help/sites-deploying/troubleshooting.md">La mia applicazione genera errori di memoria esaurita</a></li> 
     <li><a href="https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html">Analizzare i problemi di memoria su Helpx.</a><br /> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 21</strong></td> 
   <td>I/O disco</td> 
   <td><p>Consulta la sezione <a href="/help/sites-deploying/monitoring-and-maintaining.md#disk-i-o">I/O disco</a> nella sezione Monitoraggio e manutenzione.</p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggi 22 e 22.1</strong></td> 
   <td>Rapporto cache</td> 
   <td>Vedi <a href="/help/sites-deploying/configuring-performance.md#calculating-the-dispatcher-cache-ratio">Calcolo del rapporto della cache del Dispatcher</a>.<br /> <br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 23</strong></td> 
   <td>Query lente</td> 
   <td><a href="/help/sites-deploying/best-practices-for-queries-and-indexing.md">Tecniche consigliate per query e indicizzazione</a></td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 24</strong></td> 
   <td>Regolazione del repository</td> 
   <td> 
    <ul> 
     <li><a href="https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html">Suggerimenti sull'ottimizzazione delle prestazioni</a></li> 
     <li><a href="/help/sites-deploying/configuring-performance.md#configuring-for-performance">Configurazione per le prestazioni</a></li> 
     <li><a href="https://www.slideshare.net/jukka/repository-performance-tuning">Ottimizzazione delle prestazioni del repository</a></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 25</strong></td> 
   <td>Flussi di lavoro in esecuzione</td> 
   <td> 
    <ul> 
     <li><a href="/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing">Elaborazione simultanea del flusso di lavoro</a></li> 
     <li><a href="/help/sites-deploying/configuring-performance.md#configure-the-queue-for-a-specific-workflow">Configurare la coda per un flusso di lavoro specifico</a></li> 
     <li><a href="/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances">Rimozione regolare delle istanze del flusso di lavoro</a></li> 
     <li><a href="/help/sites-developing/workflows.md#transient-workflows">Flussi di lavoro transitori</a><br /> </li> 
    </ul> <p> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 26</strong></td> 
   <td>Infrastruttura MSM</td> 
   <td><p><a href="/help/sites-administering/msm-best-practices.md">Best practice per Multi Site Manager</a><br /> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 27</strong></td> 
   <td>Ottimizzazione delle risorse</td> 
   <td> 
    <ol> 
     <li><a href="/help/sites-deploying/configuring-performance.md#cq-dam-asset-synchronization-service">Servizio di sincronizzazione delle risorse</a></li> 
     <li><a href="/help/sites-deploying/configuring-performance.md#multiple-dam-instances">Più istanze DAM</a></li> 
     <li>Articoli per suggerimenti sull’ottimizzazione delle prestazioni <a href="https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html">qui</a> e <a href="https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html">qui</a>.<br /> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 28</strong></td> 
   <td>Sessioni non chiuse</td> 
   <td><p> </p> <p><a href="/help/sites-administering/troubleshoot.md#checking-for-unclosed-jcr-sessions">Verifica di sessioni JCR non chiuse</a></p> <p> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 30</strong></td> 
   <td>Sposta il dispatcher più vicino (aggiungine uno per "regione"?)</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 31</strong></td> 
   <td>Usa CDN di fronte al dispatcher</td> 
   <td><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html#using-dispatcher-with-a-cdn">Utilizzo di Dispatcher con una rete CDN</a><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 32</strong></td> 
   <td>Utilizza la gestione delle sessioni a livello di dispatcher per scaricare AEM server</td> 
   <td><p><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement">Abilitazione di sessioni sicure</a></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 33</strong></td> 
   <td>Effettuare le richieste in cache</td> 
   <td> 
    <ol> 
     <li><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html">Configurazione generale del Dispatcher</a></li> 
     <li><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache">Configurazione della cache del Dispatcher</a></li> 
    </ol> <p>Come migliorare il rapporto cache; rende le richieste compatibili con la cache (best practice per Dispatcher)</p> <p>Inoltre, prendi in considerazione le seguenti impostazioni per ottimizzare le configurazioni di memorizzazione in cache<br /> </p> 
    <ol> 
     <li>Imposta una regola di no-cache per le richieste HTTP che non sono GET</li> 
     <li>Configurare le stringhe di query per non essere memorizzabili nella cache</li> 
     <li>Non memorizzare in cache gli URL con estensioni mancanti</li> 
     <li>Intestazioni di autenticazione cache (possibile dalla versione 4.1.10 di Dispatcher)</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 34</strong></td> 
   <td>Aggiorna la versione del dispatcher</td> 
   <td><p>Puoi scaricare la versione più recente di Dispatcher da questa posizione:</p> <p><a href="https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html">Segui collegamento</a></p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 35</strong></td> 
   <td>Configurare il dispatcher</td> 
   <td><a href="https://helpx.adobe.com/it/experience-manager/dispatcher/using/dispatcher-configuration.html">Configurazione del Dispatcher</a><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 36</strong></td> 
   <td>Verifica invalidazione della cache</td> 
   <td><br /> 
    <ul> 
     <li><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/page-invalidate.html#invalidating-dispatcher-cache-from-the-authoring-environment">Annullamento della validità della cache per il livello di authoring;</a></li> 
     <li><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance">Annullamento della validità della cache per il livello di pubblicazione.</a></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggi 37 e 38</strong></td> 
   <td>Caricamento pigro</td> 
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html">Vedi la sessione Gem su Prestazioni Web AEM.</a><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 39</strong></td> 
   <td>Utilizzare la preconnessione per ridurre il sovraccarico di connessione</td> 
   <td>Vedi la Sessione Gem sopra indicata. Inoltre, preconnessione della documentazione aggiuntiva su W3c:<a href="https://www.w3.org/TR/resource-hints/#dfn-preconnect"> https://www.w3.org/TR/resource-hints/#dfn-preconnect</a></td> 
  </tr> 
  <tr> 
   <td><strong>Passaggi 40 e 41</strong><br /> </td> 
   <td>Latenza e tempo di risposta degli host esterni</td> 
   <td>Analizzare la latenza e il tempo di risposta per gli host esterni.</td> 
  </tr> 
  <tr> 
   <td><strong>Passaggi 45<br /> e 47</strong><br /> </td> 
   <td>Utilizzo di HTTP/2</td> 
   <td>Consulta la sessione Gem per i passaggi 37,38 e 39. Inoltre, controlla <a href="https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.topic.html/forum__kdzc-does_anyoneknowwhe.html">questo</a> post del forum sul supporto HTTP/2.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 49</strong></td> 
   <td>Riduci dimensioni del payload</td> 
   <td><a href="/help/sites-deploying/osgi-configuration-settings.md">Abilita Gzip</a> e <a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html">ridurre le dimensioni dell'immagine</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggi 42 e 43</strong></td> 
   <td>Mantieni vivo</td> 
   <td><p>È <code>Keep-Alive</code> intestazione presente nelle diverse richieste di riutilizzo delle connessioni? In caso contrario, ciò significherebbe che ogni richiesta porta a un altro stabilimento di connessione, il che introduce costi generali superflui. (Analisi delle richieste HTTP standard nel browser)</p> <p>Puoi controllare la <a href="/help/sites-administering/proxy-jar.md">Strumento Server proxy</a> per controllare le connessioni Keep-Alive.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 44</strong></td> 
   <td>Quante richieste vengono effettuate?</td> 
   <td>Esegui l’analisi standard delle richieste HTTP nel browser.</td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 46</strong></td> 
   <td>Riduzione del numero di richieste</td> 
   <td> 
    <ol> 
     <li>Concatenare risorse (immagini, sprite CSS, JSON, ecc.)<br /> </li> 
     <li>Incorporazione Clientlibs: 
      <ol> 
       <li><a href="/help/sites-developing/clientlibs.md#creating-client-library-folders">Creazione di cartelle della libreria client</a> - vedere Utilizzo dell’incorporamento per ridurre al minimo le richieste</li> 
      </ol> </li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><strong>Passaggio 48</strong></td> 
   <td>Qual è la dimensione del payload?</td> 
   <td>Analisi standard delle richieste HTTP nel browser</td> 
  </tr> 
  <tr> 
   <td><strong>Passaggi 50 e 51</strong></td> 
   <td>Blocco del codice JS</td> 
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html">Prestazioni Web AEM</a></td> 
  </tr> 
 </tbody> 
</table>
