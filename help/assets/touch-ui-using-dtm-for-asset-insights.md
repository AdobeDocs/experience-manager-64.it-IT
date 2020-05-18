---
title: Abilitazione di approfondimenti sulle risorse tramite DTM
description: Scopri come utilizzare Adobe Dynamic Tag Management (DTM) per abilitare Asset Insights.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0560d47dcffbf9b74a36ea00e118f8a176adafcd
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# Abilitazione di approfondimenti sulle risorse tramite DTM {#enabling-asset-insights-through-dtm}

Adobe Dynamic Tag Management è uno strumento che attiva i tuoi strumenti di marketing digitale. Viene fornito gratuitamente ai clienti di Adobe Analytics.

Sebbene sia possibile personalizzare il codice di tracciamento per consentire a soluzioni CMS di terze parti di utilizzare Asset Insights, Adobe consiglia di utilizzare DTM per inserire i tag Asset Insights.

Per abilitare Asset Insights tramite Gestione dinamica dei tag, effettuate le seguenti operazioni:

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools > Assets > Insights Configuration]**.
1. [Configurare l&#39;istanza di AEM con il servizio cloud DTM](../sites-administering/dtm.md)

   Il token API dovrebbe essere disponibile dopo l&#39;accesso a [https://dtm.adobe.com](https://dtm.adobe.com/) e visitare Impostazioni **** account dall&#39;icona Profilo. Questo passaggio non è richiesto dal punto di vista di Asset Insights, perché l’integrazione di AEM Sites con Asset Insights è ancora in corso.

1. Accedete a [https://dtm.adobe.com](https://dtm.adobe.com/)e selezionate una Società, a seconda delle necessità.
1. Creare/aprire una proprietà Web esistente

   * Selezionate la scheda Proprietà **** Web, quindi toccate o fate clic su **[!UICONTROL Aggiungi proprietà]**.
   * Aggiornate i campi come appropriato, quindi toccate o fate clic su **[!UICONTROL Crea proprietà]** (consultate la [documentazione](https://helpx.adobe.com/experience-manager/using/dtm.html)).
   ![chlimage_1-193](assets/chlimage_1-193.png)

1. Nella scheda **[!UICONTROL Regole]** , selezionare Regole di caricamento **[!UICONTROL pagina]** dal riquadro di navigazione e toccare o fare clic su **[!UICONTROL Crea nuova regola]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. Espandete **[!UICONTROL Tag]** Javascript/Di Terze Parti. Quindi toccate o fate clic su **[!UICONTROL Aggiungi nuovo script]** nella scheda HTML **** sequenziale per aprire la finestra di dialogo Script.

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. Tap/click the AEM logo, and go to **[!UICONTROL Tools > Assets]**.
1. Toccate/fate clic su **[!UICONTROL Insights Page Tracker]**(Tracciatore pagina approfondimenti), copiate il codice di tracciamento e incollatelo nella finestra di dialogo Script aperta al punto 6. Salva le modifiche.

   >[!NOTE]
   >
   >* `AppMeasurement.js` è stato rimosso. È previsto che sia disponibile tramite lo strumento Adobe Analytics di DTM.
   >* La chiamata a `assetAnalytics.dispatcher.init()` viene rimossa. La funzione verrà chiamata al termine del caricamento dello strumento Adobe Analytics di DTM.
   >* A seconda di dove è ospitato Asset Insights Page Tracker (ad esempio AEM, CDN e così via), l’origine della sorgente dello script potrebbe richiedere delle modifiche.
   >* Per il Tracciatore pagina ospitato in AEM, l’origine deve puntare a un’istanza di pubblicazione utilizzando il nome host dell’istanza del dispatcher.



1. Aprite [https://dtm.adobe.com](https://dtm.adobe.com). Fai clic su Panoramica nella proprietà Web e fai clic su Aggiungi strumento o apri uno strumento Adobe Analytics esistente. Durante la creazione dello strumento, potete impostare il metodo di configurazione su Automatico.

   ![chlimage_1-196](assets/chlimage_1-196.png)

   Selezionate le suite di rapporti Staging/Produzione, a seconda delle necessità.

1. Espandete Gestione **** libreria e accertatevi che **[!UICONTROL Carica libreria in]** sia impostato su **[!UICONTROL Page Top]**.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. Espandete **[!UICONTROL Personalizza codice]** pagina e toccate o fate clic su **[!UICONTROL Apri editor]**.

   ![chlimage_1-198](assets/chlimage_1-198.png)

1. Incollate il seguente codice nella finestra:

   ```java
   var sObj;
   
   if (arguments.length > 0) {
     sObj = arguments[0];
   } else {
     sObj = _satellite.getToolsByType('sc')[0].getS();
   }
   _satellite.notify('in assetAnalytics customInit');
   (function initializeAssetAnalytics() {
     if ((!!window.assetAnalytics) && (!!assetAnalytics.dispatcher)) {
       _satellite.notify('assetAnalytics ready');
       /** NOTE:
           Copy over the call to 'assetAnalytics.dispatcher.init()' from Assets Pagetracker
           Be mindful about changing the AppMeasurement object as retrieved above.
       */
       assetAnalytics.dispatcher.init(
             "",  /** RSID to send tracking-call to */
             "",  /** Tracking Server to send tracking-call to */
             "",  /** Visitor Namespace to send tracking-call to */
             "",  /** listVar to put comma-separated-list of Asset IDs for Asset Impression Events in tracking-call, e.g. 'listVar1' */
             "",  /** eVar to put Asset ID for Asset Click Events in, e.g. 'eVar3' */
             "",  /** event to include in tracking-calls for Asset Impression Events, e.g. 'event8' */
             "",  /** event to include in tracking-calls for Asset Click Events, e.g. 'event7' */
             sObj  /** [OPTIONAL] if the webpage already has an AppMeasurement object, please include the object here. If unspecified, Pagetracker Core shall create its own AppMeasurement object */
             );
       sObj.usePlugins = true;
       sObj.doPlugins = assetAnalytics.core.updateContextData;
       assetAnalytics.core.optimizedAssetInsights();
     }
     else {
       _satellite.notify('assetAnalytics not available. Consider updating the Custom Page Code', 4);
     }
   })();
   ```

   * La regola di caricamento delle pagine in Gestione dinamica dei tag include solo il codice pagetracker.js. Tutti `assetAnalytics` i campi sono considerati sostituzioni per i valori predefiniti. Non sono richiesti per impostazione predefinita.
   * Il codice richiama `assetAnalytics.dispatcher.init()` dopo aver verificato che `_satellite.getToolsByType('sc')[0].getS()` sia inizializzato e `assetAnalytics,dispatcher.init` sia disponibile. Pertanto, potete saltare l’aggiunta al punto 11.
   * Come indicato nei commenti all&#39;interno del codice Tracciatore pagina Insights (**[!UICONTROL Strumenti > Risorse > Tracciatore]** pagina Insights), quando il Tracker pagina non crea un `AppMeasurement` oggetto, i primi tre argomenti (RSID, Server di tracciamento e Spazio dei nomi dei visitatori) sono irrilevanti. Vengono invece passate stringhe vuote per evidenziare questo problema.

      Gli argomenti rimanenti corrispondono a ciò che è configurato nella pagina Insights Configuration (**[!UICONTROL Strumenti > Risorse > Insights Configuration]**).

   * L&#39;oggetto AppMeasurement viene recuperato eseguendo query `satelliteLib` per tutti i motori SiteCatalyst disponibili. Se sono configurati più tag, modificate l&#39;indice del selettore di array in modo appropriato. Le voci dell&#39;array sono ordinate in base agli strumenti SiteCatalyst disponibili nell&#39;interfaccia DTM.

1. Salvare e chiudere la finestra Editor di codice, quindi salvare le modifiche nella configurazione dello strumento.
1. Nella scheda **[!UICONTROL Approvazioni]** , approvare entrambe le approvazioni in sospeso. Il tag DTM è pronto per essere inserito nella pagina Web. Per informazioni dettagliate su come inserire tag DTM nelle pagine Web, consultate [Integrazione di DTM nei modelli](https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template/)di pagina personalizzati.
