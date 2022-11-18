---
title: Funzioni obsolete e rimosse
description: Note specifiche per le funzioni obsolete e rimosse in Adobe Experience Manager 6.4.
exl-id: 2fe0dad7-fc78-4aac-afa3-79a278008453
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 26%

---

# Funzioni obsolete e rimosse {#deprecated-and-removed-features}

Adobe valuta costantemente le funzionalità dei prodotti per reinventare o sostituire nel tempo le funzioni meno recenti con alternative più moderne al fine di migliorare il valore complessivo per il cliente, tenendo comunque in considerazione la compatibilità con le versioni precedenti.

Per comunicare l’imminente rimozione/sostituzione delle funzionalità AEM, si applicano le seguenti regole:

1. Innanzitutto viene annunciato che una data funzione diventa obsoleta. Anche se è obsoleta, le funzionalità sono ancora disponibili, ma non saranno ulteriormente migliorate.
1. La rimozione delle funzionalità obsolete verrà attuata a partire dalla versione principale successiva. La data di riferimento effettiva per la rimozione verrà annunciata.

Questo processo offre ai clienti almeno un ciclo di rilascio per adattare la loro implementazione a una nuova versione o alla funzionalità che prenderà il posto di quella dichiarata obsoleta, prima che venga definitivamente rimossa.

## Funzioni obsolete {#deprecated-features}

Nella tabella seguente sono elencate le funzioni e le funzionalità contrassegnate come obsolete con AEM 6.4. In genere, le funzioni che si prevede di rimuovere in una versione futura vengono inizialmente rese obsolete e viene fornita un’alternativa.

Consigliamo ai clienti di verificare se utilizzano la funzione o funzionalità nella loro implementazione corrente e di pianificarne la modifica adottando l’alternativa fornita.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Area | Funzione obsoleta | Sostituzione |
|---|---|---|
| Interfaccia | Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica. In AEM 6.4 è già inclusa l’interfaccia utente classica e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a usarla normalmente. Nota: l’interfaccia utente classica rimane completamente supportata anche se obsoleta. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Editor pagina) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | Consigliamo ai clienti di passare alla nuova interfaccia utente AEM. |
| Componenti | Adobe non prevede di apportare ulteriori miglioramenti ai componenti di base elencati di seguito. AEM 6.4 include i componenti di base e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a utilizzarli normalmente. Nota: anche se diventano obsoleti, i componenti di base rimangono completamente supportati. <ul> <li> foundation/components/account/account/nome account </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/password </li> <li> foundation/components/account/requestConfirm </li> <li> foundation/components/adaptiveimage </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrumb </li> <li> fondazione/componenti/modulo/carta di credito </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereferenza </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | Consigliamo ai clienti di utilizzare i componenti core per i progetti futuri. Non è necessario modificare i siti esistenti. |
| Componenti | Adobe non prevede di apportare ulteriori miglioramenti ai componenti di base elencati di seguito. AEM 6.4 include i componenti di base e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a utilizzarli normalmente. Nota: anche se diventano obsoleti, i componenti di base rimangono completamente supportati. <ul><li>foundation/components/fasatura</li></ul> | L&#39;Adobe non prevede di fornire una sostituzione. |
| Portale Director | Portal Director è un insieme di funzioni che consente l’hosting di contenuti AEM tramite Portlet in server di terze parti. Adobe non prevede di apportare ulteriori miglioramenti alla funzione Portal Director nella posizione indicata di seguito. AEM 6.4 include Portal Director e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a utilizzarlo così com’è. Portal Direct rimane completamente supportato anche se obsoleto. <ul><li>/libs/portal/director</li></ul> | L&#39;Adobe non prevede di fornire una sostituzione. |
| Componente portlet | Portlet Components in /foundation/components/portlet consente di ospitare portlet JSR in AEM come componenti. Adobe non prevede di apportare ulteriori miglioramenti alla funzionalità del componente Portlet. AEM 6.4 include il componente Portlet e i clienti che eseguono l’aggiornamento da versioni precedenti possono continuare a utilizzarlo così com’è. Il componente Portlet rimane completamente supportato anche se obsoleto. | L&#39;Adobe non prevede di fornire una sostituzione. |
| Forms | Il supporto per il servizio Adobe Central Migration Bridge è stato dichiarato obsoleto in quanto il prodotto Adobe Central non è più supportato. | Nessuna sostituzione |
| Forms | Utilizzo obsoleto di JSONObject in Query e OperationOptions. Le seguenti API sono obsolete: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Utilizza la `IValueMap` API |
| Forms | Servizio Central Migration Bridge obsoleto. | Non viene offerta alcuna sostituzione. |
| Assets | Lo scaricamento delle risorse è stato dichiarato obsoleto a partire da AEM 6.4. |  |
| Sviluppatori | Libreria client Lodash/underscore. Adobe non prevede di mantenere e aggiornare ulteriormente la libreria client Lodash/underscore fornita come parte della distribuzione (Quickstart) | Adobe consiglia ai clienti che richiedono ancora il Lodash/underscore per il loro codice di aggiungerlo alla codebase del progetto. |

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

La tabella seguente elenca le funzioni e le funzionalità che sono state rimosse da AEM 6.4. Nelle versioni precedenti queste funzionalità erano indicate come obsolete.

| Area | Funzione obsoleta | Sostituzione |
|---|---|---|
| Integrazione con [!DNL Experience Cloud] | Puoi sincronizzare le tue risorse con [!DNL Experience Cloud] utilizzo di una configurazione tramite [!DNL Adobe I/O]. [!DNL Adobe Experience Cloud] è stato precedentemente chiamato [!DNL Adobe Marketing Cloud]. | Se hai delle domande, contatta [Adobe Assistenza clienti](https://experienceleague.adobe.com/?support-solution=General&amp;lang=it#support). |
| Activity Map di Analytics | Versione di Activity Map inclusa in AEM. | In seguito a modifiche di sicurezza nell’API di Adobe Analytics, non è più possibile utilizzare la versione di Activity Map inclusa in AEM. La [Plug-in ActivityMap fornito da Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=it) Da utilizzare. |
| Componenti-Forms | Modulo Captcha (foundation/components/form/captcha) | Utilizza invece il componente ReCaptcha per Google |
| Componenti | Presentazione (foundation/components/slideshow) | Nessuna sostituzione |
| Componenti | Flash (foundation/components/flash) | Nessuna sostituzione |
| Componenti | Supporto per la riproduzione di file SWF nel componente video (foundation/components/video) | Utilizzare formati video basati su non-flash. |
| Componenti | Tabella prodotti (commerce/components/product_table) | Nessuna sostituzione |
| Gestione attività | Gestione attività interfaccia utente classica (/libs/cq/taskmanagement/content/taskmanager.html) | Obsoleto a partire dalla versione 6.0. Utilizza la nuova gestione attività combinata con l&#39;interfaccia utente del flusso di lavoro. |
| Flusso di lavoro | Interfaccia per le notifiche utilizzata tra le versioni 5.6-6.2 (/libs/cq/workflow/content/notifications.html) | Casella in entrata per i flussi di lavoro /aem/inbox |
| Forms | È stato rimosso l’Export PDF al formato PDF/E-1 che utilizza PDF Generator. | PDF Generator continua a supportare l’esportazione di PDF nei formati PDF/A-1a/b, PDF/A-2a/b e PDF/A-3a/b. |
| Forms | Il supporto per le immagini nei frammenti di documento è stato rimosso. | Le comunicazioni interattive consentono di utilizzare direttamente le immagini nei canali web e di stampa. |
| Forms | Aggiornamento fuori sede | Il supporto per eseguire l&#39;aggiornamento locale non è disponibile |
| Forms | Sidegrade per le migrazioni da TarMK a DocumentMK | Puoi esportare i dati dal sistema precedente e quindi importarli in un sistema di configurazione di recente. Per istruzioni dettagliate, consulta la documentazione relativa all’aggiornamento di AEM Forms su JEE |
| Forms | Il programma di installazione di AEM Forms su JEE a 32 bit non è disponibile. | Adobe ha interrotto la spedizione di AEM Forms sul programma di installazione JEE a 32 bit. Puoi continuare a utilizzare il programma di installazione a 64 bit per installare AEM Forms su JEE. |
| Forms | È stato rimosso il supporto per l’utilizzo di immagini DAM nel componente Frammento documento. | È possibile utilizzare il componente Immagine e Grafico nel canale di stampa della comunicazione interattiva. Se utilizzi un componente per frammenti di documento adattivo nei moduli adattivi, questo smette di funzionare dopo l’aggiornamento a Forms 6.4 AEM. |
| Forms | Funzione Documenti adattivi rimossa | È possibile utilizzare la funzione di comunicazione interattiva per creare comunicazioni stampate e basate su web. Se utilizzi Documenti adattivi, installa il pacchetto di compatibilità per continuare a utilizzare i documenti adattivi esistenti |
| Forms | È stato rimosso AEM Forms sulla pagina di destinazione specifica di JEE. | AEM Forms sulla pagina di destinazione JEE viene sostituito con AEM pagina di destinazione (/aem/start.html) |
| Forms | Supporto rimosso per Captcha predefinito | Utilizza il servizio reCAPTCHA di Google. |
| Forms | È stato rimosso il supporto per i campi Flash in AEM Designer. AEM Designer non consente di modificare i campi Flash utilizzati in un modulo. | È possibile utilizzare AEM Designer rilasciato per una versione precedente per modificare tali moduli. |
| Communities | Il supporto per la verifica Captcha è stato rimosso. | Utilizza l’integrazione captcha personalizzata (ad esempio reCAPTCHA by Google) per la verifica. |

## Pre-annuncio per rilascio successivo {#pre-announcement-for-next-release}

La tabella seguente fornisce un elenco delle modifiche per le versioni future, che non sono obsolete ma che possono avere un impatto sui clienti. Queste informazioni vengono fornite a scopo di pianificazione.

| Area | Funzione obsoleta | Annuncio |
|---|---|---|
| Supporto del browser | Microsoft Internet Explorer | AEM 6.4 è l’ultima versione che supporta Microsoft Internet Explorer 11. |
| Foundation | Framework interfaccia utente | Nel 2019 Adobe dichiarerà obsoleti i componenti Coral UI 2 . AEM 6.4 è completamente basato su Coral UI 3 (introdotto con AEM 6.2). Adobe consiglia ai suoi clienti e partner che hanno creato interfacce utente personalizzate con Coral 2 di eseguire il refactoring di queste interfacce con Coral 3. Adobe offre uno strumento per convertire le finestre di dialogo Coral 2 in Coral 3 - [Ulteriori informazioni.](/help/sites-developing/modernization-tools.md) |
