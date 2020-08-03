---
title: Funzioni obsolete e rimosse
description: Note specifiche per le funzioni obsolete e rimosse in Adobe Experience Manager 6.4.
translation-type: tm+mt
source-git-commit: 543f66c760d7b25681a79d5df3d8ab6e8c0b2f47
workflow-type: tm+mt
source-wordcount: '1234'
ht-degree: 27%

---


# Funzioni obsolete e rimosse {#deprecated-and-removed-features}

Adobe valuta costantemente le funzionalità dei prodotti per reinventare o sostituire nel tempo le funzioni meno recenti con alternative più moderne al fine di migliorare il valore complessivo per il cliente, tenendo comunque in considerazione la compatibilità con le versioni precedenti.

Per comunicare l’imminente rimozione/sostituzione delle funzionalità AEM, si applicano le seguenti regole:

1. Innanzitutto viene annunciato che una data funzione diventa obsoleta. Anche se è obsoleta, le funzionalità sono ancora disponibili, ma non saranno ulteriormente migliorate.
1. La rimozione delle funzionalità obsolete verrà attuata a partire dalla versione principale successiva. La data di riferimento effettiva per la rimozione verrà annunciata.

Questo processo offre ai clienti almeno un ciclo di rilascio per adattare la loro implementazione a una nuova versione o alla funzionalità che prenderà il posto di quella dichiarata obsoleta, prima che venga definitivamente rimossa.

## Funzioni obsolete {#deprecated-features}

Nella tabella seguente sono elencate le funzionalità contrassegnate come obsolete con AEM 6.4. In genere, le funzioni pianificate per essere rimosse in una versione futura sono impostate per prime su obsoleta, con un&#39;alternativa fornita.

Consigliamo ai clienti di verificare se utilizzano la funzione o funzionalità nella loro implementazione corrente e di pianificarne la modifica adottando l’alternativa fornita.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Area | Funzione obsoleta | Sostituzione |
|---|---|---|
| Interfaccia | Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica. In AEM 6.4 è già inclusa l’interfaccia utente classica e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a usarla normalmente. Nota: l’interfaccia utente classica rimane completamente supportata anche se obsoleta. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Editor pagina) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | È consigliabile passare alla nuova interfaccia AEM. |
| Componenti |  Adobe non prevede di apportare ulteriori miglioramenti ai componenti di base elencati di seguito. AEM 6.4 include i componenti di base e i clienti che effettuano l&#39;aggiornamento da versioni precedenti possono continuare a utilizzarli così com&#39;è. Nota: anche se diventano obsoleti, i componenti di base rimangono completamente supportati. <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/azioni </li> <li> foundation/components/account/passworset </li> <li> foundation/components/account/request </li> <li> foundation/components/adaptiveimage </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrumb </li> <li> foundation/components/form/creditcard </li> <li> foundation/components/listChildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilepiè di pagina </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | Consigliamo ai clienti di utilizzare i componenti core per i progetti futuri. I siti esistenti non devono essere modificati. |
| Componenti |  Adobe non prevede di apportare ulteriori miglioramenti ai componenti di base elencati di seguito. AEM 6.4 include i componenti di base e i clienti che effettuano l&#39;aggiornamento da versioni precedenti possono continuare a utilizzarli così com&#39;è. Nota: anche se diventano obsoleti, i componenti di base rimangono completamente supportati. <ul><li>foundation/components/temporizzazione</li></ul> |  Adobe non prevede di fornire una sostituzione. |
| Director Portal | Portal Director è una serie di funzionalità che consente di ospitare AEM contenuto tramite Portlet nei server di terze parti.  Adobe non prevede di apportare ulteriori miglioramenti alla funzionalità Director Portal nella posizione indicata di seguito. AEM 6.4 include Portal Director e i clienti che effettuano l’aggiornamento da versioni precedenti possono continuare a utilizzarlo così com’è. Portal Direct rimane completamente supportato anche se viene dichiarato obsoleto. <ul><li>/libs/portale/director</li></ul> |  Adobe non prevede di fornire una sostituzione. |
| Componente Portlet | Portlet Components in /foundation/components/portlet consente di ospitare i portlet JSR in AEM come componenti.  Adobe non prevede di apportare ulteriori miglioramenti alla funzione Portlet Component. AEM 6.4 include il componente Portlet e i clienti che effettuano l&#39;aggiornamento da versioni precedenti possono continuare a utilizzarlo così com&#39;è. Il componente Portlet rimane completamente supportato anche se è obsoleto. |  Adobe non prevede di fornire una sostituzione. |
| Forms | Il supporto per  servizio Adobe Central Migration Bridge è stato dichiarato obsoleto perché  prodotto di Adobe Central non è più supportato. | Nessuna sostituzione |
| Forms | Utilizzo obsoleto di JSONObject in Query e OperationOptions. Le seguenti API sono obsolete: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Utilizzare l&#39; `IValueMap` API |
| Forms | Servizio Bridge di migrazione centrale obsoleto. | Non viene offerta alcuna sostituzione. |
| Assets | Lo scarico delle risorse è stato dichiarato obsoleto a partire da AEM 6.4. |  |

<!-- Original HTML table that came from helpx during migration.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Feature</td> 
   <td>Replacement</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe does not plan to make further enhancements to the Classic UI. AEM 6.4 has the Classic UI included, and customers upgrading from earlier releases can keep using it as is. Note that Classic UI remains fully supported while being deprecated. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Page Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Customers are advised to switch to use the new AEM UI.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listchildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
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
   <td>Customers are advised to use the Core Components for future projects. Existing sites do not need to be changed.</td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>The Portal Director is a set of features, that enables the hosting of AEM content via Portlet in 3rd party servers.</p> <p>Adobe does not plan to make further enhancements to the Portal Director feature under the location listed below. AEM 6.4 has the Portal Director included, and customers upgrading from earlier releases can keep using it as is. Note that Portal Direct remains fully supported while being deprecated.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portlet Component</td> 
   <td><p>Portlet Components under /foundation/components/portlet enables the hosting of JSR Portlets in AEM as components.</p> <p>Adobe does not plan to make further enhancements to the Portlet Component feature. AEM 6.4 has the Portlet Component included, and customers upgrading from earlier releases can keep using it as is. Note that Portlet Component remains fully supported while being deprecated.</p> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Support for Adobe Central Migration Bridge service has been deprecated as Adobe Central product is no longer supported.</p> </td> 
   <td>No replacement </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Deprecated use of JSONObject in Query and OperationOptions. The following APIs are deprecated:
   <ul><li>setArguments(JSONObject arguments)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject arguments</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Use the IValueMap API </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Deprecated Central Migration Bridge service</p> </td> 
   <td> No replacement </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Assets Offloading has been deprecated starting with AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>
-->

## Funzioni rimosse {#removed-features}

Nella tabella seguente sono elencate le funzionalità rimosse dalla AEM 6.4. Le versioni precedenti presentavano queste funzionalità contrassegnate come obsolete.

| Area | Funzione obsoleta | Sostituzione |
|---|---|---|
| Activity Map di Analytics | Versione di Activity Map inclusa in AEM. | In seguito a modifiche di sicurezza in Adobe Analytics API, non è più possibile utilizzare la versione di Activity Map inclusa in AEM. The [ActivityMap plug-in provided by Adobe Analytics](https://docs.adobe.com/content/help/it/IT/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) should now be used. |
| Componenti-Forms | Captcha modulo (foundation/components/form/captcha) | Utilizzare invece il componente ReCaptcha di Google |
| Componenti | Presentazione (foundation/components/slideshow) | Nessuna sostituzione |
| Componenti | Flash (foundation/components/flash) | Nessuna sostituzione |
| Componenti | Rimosso il supporto per la riproduzione di file SWF nel componente video (foundation/components/video) | Utilizzate formati video basati su none-flash. |
| Componenti | Tabella prodotti (commerce/components/product_table) | Nessuna sostituzione |
| Gestione attività | Gestione attività interfaccia classica (/libs/cq/taskmanagement/content/taskmanager.html) | Obsoleto dal 6.0. Utilizzare la nuova gestione attività combinata con l&#39;interfaccia utente del flusso di lavoro. |
| Flusso di lavoro | Interfaccia per le notifiche utilizzata tra le versioni 5.6-6.2 (/libs/cq/workflow/content/notifications.html) | Casella in entrata per i flussi di lavoro /aem/inbox |
| Forms |  Export PDF al formato PDF/E-1 tramite PDF Generator è stato rimosso. | PDF Generator continua a supportare l’esportazione di PDF nei formati PDF/A-1a/b, PDF/A-2a/b e PDF/A-3a/b. |
| Forms | Il supporto per le immagini all&#39;interno di frammenti di documento è stato rimosso. | Le comunicazioni interattive consentono di utilizzare direttamente le immagini nei canali Web e per la stampa. |
| Forms | Aggiornamento fuori sede | Il supporto per l&#39;esecuzione dell&#39;aggiornamento locale non è disponibile |
| Forms | Sidegrade per le migrazioni da TarMK a DocumentMK | È possibile esportare i dati da sistemi meno recenti e quindi importarli in un sistema di configurazione più recente. Per istruzioni dettagliate, consultate AEM Forms sulla documentazione di aggiornamento JEE |
| Forms | AEM Forms nel programma di installazione JEE a 32 bit non disponibili. |  Adobe ha interrotto la spedizione dei AEM Forms nel programma di installazione JEE a 32 bit. Potete continuare a utilizzare il programma di installazione a 64 bit per installare AEM Forms su JEE. |
| Forms | È stato rimosso il supporto per l&#39;utilizzo di immagini DAM in Componente frammento documento. | Potete usare i componenti Immagine e Grafico nel canale di stampa delle comunicazioni interattive. Se nei moduli adattivi si utilizza il componente frammento di documento del documento adattivo, questo non funziona più dopo l&#39;aggiornamento a AEM 6.4 Forms. |
| Forms | È stata rimossa la funzione Documenti adattivi | Potete utilizzare la funzione di comunicazione interattiva per creare comunicazioni stampate e basate sul Web. Se utilizzate Documenti adattivi, installate il pacchetto di compatibilità per continuare a utilizzare i documenti adattivi esistenti |
| Forms | Sono stati rimossi AEM Forms sulla pagina di destinazione specifica per JEE. | I AEM Forms sulla pagina di destinazione JEE vengono sostituiti da AEM pagina di destinazione (/aem/start.html) |
| Forms | Rimosso il supporto per Captcha predefinito | Utilizzate il servizio reCAPTCHA di Google. |
| Forms | È stato rimosso il supporto per i campi Flash in AEM Designer. AEM Designer non consente la modifica dei campi Flash utilizzati in un modulo. | È possibile utilizzare AEM Designer rilasciato per una versione precedente per modificare tali moduli. |
| Communities | Il supporto per la verifica Captcha è stato rimosso. | Utilizzate l&#39;integrazione captcha personalizzata (ad esempio reCAPTCHA di Google) per la verifica. |

## Pre-annuncio per rilascio successivo {#pre-announcement-for-next-release}

La tabella seguente fornisce un elenco delle modifiche per le release future, che non sono obsolete, ma che possono interessare i clienti. Queste informazioni vengono fornite a scopo di pianificazione.

| Area | Funzione obsoleta | Annuncio |
|---|---|---|
| Supporto browser | Microsoft Internet Explorer | AEM 6.4 è l&#39;ultima versione che supporta Microsoft Internet Explorer 11. |
| Foundation | Framework interfaccia utente |  Adobe dichiara obsoleti i componenti Coral UI 2 nel 2019. AEM 6.4 è completamente basato sull’interfaccia Coral 3 (introdotta con AEM 6.2).  Adobe consiglia ai propri clienti e partner che dispongono di un’interfaccia utente personalizzata con Coral 2 di reimpostare tali interfacce sul Coral 3. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - [Read more](/help/sites-developing/dialog-conversion.md). |
