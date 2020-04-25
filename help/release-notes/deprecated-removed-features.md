---
title: Funzioni obsolete e rimosse
seo-title: Funzioni obsolete e rimosse
description: Note specifiche per le funzioni obsolete e rimosse in Adobe Experience Manager 6.4.
seo-description: Note specifiche per le funzioni obsolete e rimosse in Adobe Experience Manager 6.4.
uuid: 2619039b-72b4-4c6c-a813-90eed622b423
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 15819d42-4897-40fa-a013-e019d1580fa2
translation-type: tm+mt
source-git-commit: 45849a1a22f99d149369cd91781de4de0260c8e3

---


# Funzioni obsolete e rimosse {#deprecated-and-removed-features}

Adobe valuta costantemente le funzionalità dei prodotti, per reinventare o sostituire nel tempo le funzioni meno recenti con alternative più moderne al fine di migliorare il valore complessivo per il cliente, tenendo comunque in considerazione la compatibilità con le versioni precedenti.

Per comunicare l’imminente rimozione/sostituzione delle funzionalità AEM, si applicano le seguenti regole:

1. Innanzitutto viene annunciato che una data funzione diventa obsoleta. Anche se è obsoleta, le funzionalità sono ancora disponibili, ma non saranno ulteriormente migliorate.
1. La rimozione delle funzionalità obsolete verrà attuata a partire dalla versione principale successiva. La data di riferimento effettiva per la rimozione verrà annunciata.

Questo processo offre ai clienti almeno un ciclo di rilascio per adattare la loro implementazione a una nuova versione o alla funzionalità che prenderà il posto di quella dichiarata obsoleta, prima che venga definitivamente rimossa.

## Funzioni obsolete {#deprecated-features}

La tabella seguente elenca le funzioni e le funzionalità contrassegnate come obsolete con AEM 6.4. In genere, le funzioni pianificate per essere rimosse in una versione futura sono impostate per prime su obsoleta, con un&#39;alternativa fornita.

Consigliamo ai clienti di verificare se utilizzano la funzione/funzionalità nella loro implementazione corrente e di pianificarne la modifica adottando l’alternativa fornita.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Funzione</td> 
   <td>Sostituzione</td> 
  </tr>
  <tr>
   <td>Interfaccia</td> 
   <td><p>Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica. In AEM 6.4 è già inclusa l’interfaccia utente classica e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a usarla normalmente. Nota: l’interfaccia utente classica rimane completamente supportata anche se obsoleta. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Editor pagina)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Ai clienti viene consigliato di utilizzare la nuova interfaccia utente di AEM.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Componenti</td> 
   <td><p>Adobe non prevede di apportare ulteriori miglioramenti ai componenti di base elencati di seguito. In AEM 6.4 sono inclusi i componenti di base e i clienti che effettuano l’aggiornamento da versioni precedenti possono continuare a utilizzarli così com’è. Nota: anche se diventano obsoleti, i componenti di base rimangono completamente supportati. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/azioni</li> 
     <li>foundation/components/account/passworset</li> 
     <li>foundation/components/account/request</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listChildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilepiè di pagina</li> 
     <li>foundation/components/mobileimage</li> 
     <li>foundation/components/mobilelist</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>foundation/components/mobilereference</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Consigliamo ai clienti di utilizzare i componenti core per i progetti futuri. I siti esistenti non devono essere modificati.</td> 
  </tr>
  <tr>
   <td>Componenti</td> 
   <td><p>Adobe non prevede di apportare ulteriori miglioramenti ai componenti di base elencati di seguito. In AEM 6.4 sono inclusi i componenti di base e i clienti che effettuano l’aggiornamento da versioni precedenti possono continuare a utilizzarli così com’è. Nota: anche se diventano obsoleti, i componenti di base rimangono completamente supportati.</p> 
    <ul> 
     <li>foundation/components/temporizzazione</li> 
    </ul> </td> 
   <td>Al momento della scrittura, non è prevista una sostituzione.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>Portal Director è una serie di funzioni che consentono di ospitare contenuti AEM tramite Portlet nei server di terze parti.</p> <p>Adobe non prevede di apportare ulteriori miglioramenti alla funzione Portal Director nella posizione indicata di seguito. In AEM 6.4 Portal Director è incluso e i clienti che effettuano l’aggiornamento da versioni precedenti possono continuare a utilizzarlo così com’è. Portal Direct rimane completamente supportato anche se viene dichiarato obsoleto.</p> 
    <ul> 
     <li>/libs/portale/director</li> 
    </ul> </td> 
   <td>Al momento della scrittura, non è prevista una sostituzione.</td> 
  </tr>
  <tr>
   <td>Componente Portlet</td> 
   <td><p>Portlet Components in /foundation/components/portlet consente di ospitare portlet JSR in AEM come componenti.</p> <p>Adobe non intende apportare ulteriori miglioramenti alla funzione Portlet Component. AEM 6.4 include il componente Portlet e i clienti che effettuano l’aggiornamento da versioni precedenti possono continuare a utilizzarlo così com’è. Il componente Portlet rimane completamente supportato anche se è obsoleto.</p> </td> 
   <td>Al momento della scrittura, non è prevista una sostituzione.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Il supporto per il servizio Adobe Central Migration Bridge è stato dichiarato obsoleto perché il prodotto Adobe Central non è più supportato.</p> </td> 
   <td>Nessuna sostituzione </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Utilizzo obsoleto di JSONObject in Query e OperationOptions. Le seguenti API sono obsolete:
   <ul><li>setArguments(argomenti JSONObject)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, argomenti JSONObject</li><li>JSONObject getArguments()</li><li>void setArguments(argomenti JSONObject)</li></ul>
   </p> </td> 
   <td>Utilizzare l'API IValueMap </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Servizio Bridge di migrazione centrale obsoleto</p> </td> 
   <td> Nessuna sostituzione </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>L’offload di risorse è stato dichiarato obsoleto a partire da AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Funzioni rimosse {#removed-features}

La tabella seguente elenca le funzioni e le funzionalità rimosse da AEM 6.4. Le versioni precedenti presentavano queste funzionalità contrassegnate come obsolete.

<table> 
 <tbody>
  <tr>
   <td><strong>Area</strong></td> 
   <td><strong>Funzione</strong></td> 
   <td><strong>Sostituzione</strong></td> 
  </tr>
  <tr>
   <td>Activity Map di Analytics</td> 
   <td>Versione della Activity Map inclusa in AEM.</td> 
   <td>In seguito a modifiche di sicurezza in Adobe Analytics API, non è più possibile utilizzare la versione di Activity Map inclusa in AEM.<br><br>È ora necessario utilizzare il plug-in <a href="https://docs.adobe.com/content/help/it/IT/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html">ActivityMap fornito da Adobe Analytics</a> .</td> 
  </tr>
  <tr>
   <td>Componenti - Moduli</td> 
   <td>Captcha<br /> modulo (foundation/components/form/captcha)</td> 
   <td>Utilizzare invece il componente ReCaptcha di Google</td> 
  </tr>
  <tr>
   <td>Componenti</td> 
   <td>Presentazione<br /> (foundation/components/slideshow)</td> 
   <td>Nessuna sostituzione</td> 
  </tr>
  <tr>
   <td>Componenti</td> 
   <td>Flash<br /> (foundation/components/flash)</td> 
   <td>Nessuna sostituzione</td> 
  </tr>
  <tr>
   <td>Componenti</td> 
   <td>Rimosso il supporto per la riproduzione di file SWF nel componente<br /> video (foundation/components/video)</td> 
   <td>Utilizzate formati video basati su none-flash.</td> 
  </tr>
  <tr>
   <td>Componenti</td> 
   <td>Tabella<br /> prodotti (commerce/components/product_table)</td> 
   <td>Nessuna sostituzione</td> 
  </tr>
  <tr>
   <td>Gestione attività</td> 
   <td>Gestione<br /> attività interfaccia classica (/libs/cq/taskmanagement/content/taskmanager.html)</td> 
   <td>Obsoleto dal 6.0. Utilizzare la nuova gestione attività combinata con l'interfaccia utente del flusso di lavoro.</td> 
  </tr>
  <tr>
   <td>Flusso di lavoro</td> 
   <td>Interfaccia utente delle notifiche utilizzata tra la 5.6 e la 6.2<br /> (/libs/cq/workflow/content/notifications.html)</td> 
   <td>Inbox flusso di lavoro /aem/inbox</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>È stata rimossa l’esportazione di PDF in formato PDF/E-1 tramite PDF Generator.</td> 
   <td>PDF Generator continua a supportare l’esportazione di PDF nei formati PDF/A-1a/b, PDF/A-2a/b e PDF/A-3a/b.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>Il supporto per le immagini all'interno di frammenti di documento è stato rimosso. </td> 
   <td>Le comunicazioni interattive consentono di utilizzare direttamente le immagini nei canali Web e per la stampa.<br /> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td> Aggiornamento fuori sede </td> 
   <td>Il supporto per l'esecuzione dell'aggiornamento locale non è disponibile <br/> </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Sidegrade per le migrazioni da TarMK a DocumentMK </td> 
   <td> È possibile esportare i dati da sistemi meno recenti e quindi importarli in un sistema di configurazione più recente. Per istruzioni dettagliate, consultate Moduli AEM su documenti di aggiornamento JEE <br/> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
 <td>AEM Forms sul programma di installazione JEE a 32 bit non disponibile.</td> 
   <td>Adobe ha interrotto la spedizione di AEM Forms sul programma di installazione JEE a 32 bit. Potete continuare a utilizzare il programma di installazione a 64 bit per installare AEM Forms su JEE. </td>  
  </tr>
    <tr>
    <td>Forms</td> 
    <td>È stato rimosso il supporto per l'utilizzo di immagini DAM in Componente frammento documento.</td> 
    <td> Potete usare i componenti Immagine e Grafico nel canale di stampa delle comunicazioni interattive. Se nei moduli adattivi si utilizza il componente frammento di documento del documento adattivo, questo non funziona più dopo l'aggiornamento ad AEM 6.4 Forms. </td>  
  </tr>
  <tr>
   <td>Forms</td> 
   <td> È stata rimossa la funzione Documenti adattivi</td> 
   <td> Potete utilizzare la funzione di comunicazione interattiva per creare comunicazioni stampate e basate sul Web. Se utilizzate Documenti adattivi, installate il pacchetto di compatibilità per continuare a utilizzare i documenti adattivi esistenti<br/> </td> 
  </tr>
    <tr>
    <td>Forms</td> 
    <td>AEM Forms rimosso sulla pagina di destinazione specifica per JEE.</td> 
    <td>La pagina di destinazione AEM Forms su JEE viene sostituita dalla pagina di destinazione AEM (/aem/start.html) </td>  
  </tr>
   <tr>
   <td>Forms</td> 
   <td>Rimosso il supporto per Captcha predefinito</td> 
   <td>Utilizzate il servizio reCAPTCHA di Google.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>È stato rimosso il supporto per i campi Flash in AEM Designer. AEM Designer non consente di modificare i campi Flash utilizzati in un modulo.</td> 
   <td>È possibile utilizzare AEM Designer rilasciato per una versione precedente per modificare tali moduli.</td> 
  </tr>
  <tr>
   <td>Communities</td> 
   <td>Il supporto per la verifica Captcha è stato rimosso.</td> 
   <td>Utilizzate l'integrazione captcha personalizzata (ad esempio reCAPTCHA di Google) per la verifica.</td> 
  </tr>
 </tbody>
</table>

## Pre-annuncio per rilascio successivo {#pre-announcement-for-next-release}


La tabella seguente fornisce un elenco delle modifiche per le release future, che non sono obsolete, ma che possono interessare i clienti. Queste informazioni vengono fornite a scopo di pianificazione.

<table> 
 <tbody>
  <tr>
   <td>Area<br /> </td> 
   <td>Funzione<br /> </td> 
   <td>Annuncio</td> 
  </tr>
  <tr>
   <td>Supporto browser</td> 
   <td>Microsoft Internet Explorer</td> 
   <td>AEM 6.4 è l'ultima versione che supporta Microsoft Internet Explorer 11.</td> 
  </tr>
  <tr>
   <td>Foundation</td> 
   <td>Framework interfaccia utente</td> 
   <td>Adobe sta ritirando i componenti Coral UI 2 nel 2019. AEM 6.4 è completamente basato sull’interfaccia Coral 3 (introdotta con AEM 6.2). Adobe consiglia ai clienti e ai partner che dispongono di un’interfaccia utente personalizzata con Coral 2 di reimpostare tali interfacce su Coral 3. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - <a href="/help/sites-developing/dialog-conversion.md">Read more</a>.</td> 
  </tr>
 </tbody>
</table>
