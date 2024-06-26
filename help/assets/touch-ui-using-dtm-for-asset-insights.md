---
title: Abilitazione di Assets Insights tramite DTM
description: Scopri come utilizzare Adobe Dynamic Tag Management (DTM) per abilitare Asset Insights.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: d19cea4d-5395-479d-b303-4529ae2c0bf2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 2%

---

# Abilitazione di Assets Insights tramite DTM {#enabling-asset-insights-through-dtm}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Dynamic Tag Management è uno strumento che attiva i tuoi strumenti di marketing digitale. È disponibile gratuitamente per i clienti Adobe Analytics. Puoi personalizzare il codice di tracciamento per abilitare soluzioni CMS di terze parti all’utilizzo di Asset Insights oppure puoi utilizzare DTM per inserire i tag Assets Insights. Gli approfondimenti sono supportati e forniti solo per le immagini.

>[!CAUTION]
>
>Adobe DTM è obsoleto a favore di [!DNL Adobe Experience Platform] e raggiungerà presto [fine vita](https://medium.com/launch-by-adobe/dtm-plans-for-a-sunset-3c6aab003a6f). L’Adobe consiglia di [use [!DNL Adobe Experience Platform] informazioni sulle risorse](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html).

Esegui questi passaggi per abilitare Assets Insights tramite DTM:

1. Tocca o fai clic sul pulsante [!DNL Experience Manager] e vai a **[!UICONTROL Strumenti]** > **[!UICONTROL Risorse]** > **[!UICONTROL Configurazione approfondimenti]**.
1. [Configura [!DNL Experience Manager] istanza con Cloud Service DTM](../sites-administering/dtm.md)

   Il token API deve essere disponibile una volta effettuato l’accesso a [https://dtm.adobe.com](https://dtm.adobe.com/) e visita **[!UICONTROL Impostazioni account]** dall’icona Profilo . Questo passaggio non è necessario dal punto di vista di Assets Insights, perché l’integrazione di [!DNL Experience Manager Sites] con Assets Insights è ancora in esecuzione.

1. Accedi a [https://dtm.adobe.com](https://dtm.adobe.com/), e seleziona una Società, a seconda dei casi.
1. Creare/aprire una proprietà Web esistente

   * Seleziona la **[!UICONTROL Proprietà Web]** , quindi tocca o fai clic su **[!UICONTROL Aggiungi proprietà]**.
   * Aggiorna i campi come appropriato e tocca o fai clic su **[!UICONTROL Crea proprietà]** (vedi [documentazione](https://helpx.adobe.com/experience-manager/using/dtm.html)).

   ![chlimage_1-193](assets/chlimage_1-193.png)

1. In **[!UICONTROL Regole]** scheda , seleziona **[!UICONTROL Regole di caricamento pagina]** dal riquadro di navigazione e tocca o fai clic su **[!UICONTROL Crea nuova regola]**.

   ![chlimage_1-194](assets/chlimage_1-194.png)

1. Espandi **[!UICONTROL Tag Javascript /Third Party]**. Quindi tocca o fai clic su **[!UICONTROL Aggiungi nuovo script]** in **[!UICONTROL HTML sequenziale]** per aprire la finestra di dialogo Script.

   ![chlimage_1-195](assets/chlimage_1-195.png)

1. Tocca o fai clic sul pulsante [!DNL Experience Manager] e vai a **[!UICONTROL Strumenti > Risorse]**.
1. Tocca o fai clic su **[!UICONTROL Tracciamento pagina approfondimenti]**, copia il codice tracker e incollalo nella finestra di dialogo Script aperta al punto 6. Salva le modifiche.

   >[!NOTE]
   >
   >* `AppMeasurement.js` è stato rimosso. È previsto che sia disponibile tramite lo strumento Adobe Analytics di DTM.
   >* La chiamata a `assetAnalytics.dispatcher.init()` viene rimosso. La funzione deve essere chiamata una volta terminato il caricamento dello strumento Adobe Analytics di DTM.
   >* A seconda di dove è ospitato il Tracciamento pagina di Assets Insights (ad esempio AEM, CDN e così via), l’origine dell’origine dello script potrebbe richiedere modifiche.
   >* Per il tracciamento pagina ospitato da AEM, l&#39;origine deve puntare a un&#39;istanza di pubblicazione utilizzando il nome host dell&#39;istanza del dispatcher.


1. Apri [https://dtm.adobe.com](https://dtm.adobe.com). Fai clic su Panoramica nella proprietà web e fai clic su Aggiungi strumento o apri uno strumento Adobe Analytics esistente. Durante la creazione dello strumento, è possibile impostare il metodo di configurazione su Automatico.

   ![chlimage_1-196](assets/chlimage_1-196.png)

   Seleziona le suite di rapporti Staging/Produzione , a seconda dei casi.

1. Espandi **[!UICONTROL Gestione libreria]** e assicurano che **[!UICONTROL Carica libreria in]** è impostato su **[!UICONTROL Page Top]**.

   ![chlimage_1-197](assets/chlimage_1-197.png)

1. Espandi **[!UICONTROL Personalizza codice pagina]**, quindi tocca o fai clic su **[!UICONTROL Open Editor]**.

   ![chlimage_1-198](assets/chlimage_1-198.png)

1. Incolla il seguente codice nella finestra:

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

   * La regola di caricamento della pagina in DTM include solo il codice pagetracker.js . Qualsiasi `assetAnalytics` i campi sono considerati sostituzioni per i valori predefiniti. Non sono richieste per impostazione predefinita.
   * Le chiamate al codice `assetAnalytics.dispatcher.init()` dopo aver verificato che `_satellite.getToolsByType('sc')[0].getS()` è inizializzato e `assetAnalytics,dispatcher.init` è disponibile. Pertanto, puoi saltare l’aggiunta al passaggio 11.
   * Come indicato nei commenti all&#39;interno del codice di tracciamento pagina approfondimenti (**[!UICONTROL Strumenti > Risorse > Tracciamento pagina approfondimenti]**), quando il Tracker pagina non crea un `AppMeasurement` i primi tre argomenti (RSID, Tracking Server e Visitor Namespace) sono irrilevanti. Vengono invece passate stringhe vuote per evidenziarle.

      Gli argomenti rimanenti corrispondono a ciò che è configurato nella pagina Configurazione approfondimenti (**[!UICONTROL Strumenti > Risorse > Configurazione approfondimenti]**).

   * L&#39;oggetto AppMeasurement viene recuperato eseguendo una query `satelliteLib` per tutti i motori di SiteCatalyst disponibili. Se sono configurati più tag, modificare opportunamente l’indice del selettore dell’array. Le voci dell&#39;array sono ordinate in base agli strumenti di SiteCatalyst disponibili nell&#39;interfaccia DTM.

1. Salvare e chiudere la finestra Editor di codice, quindi salvare le modifiche nella configurazione dello strumento.
1. In **[!UICONTROL Approvazioni]** approvare entrambe le approvazioni in sospeso. Il tag DTM è pronto per essere inserito nella pagina web. Per informazioni dettagliate su come inserire tag DTM nelle pagine web, consulta la pagina archiviata informazioni [integrazione di DTM nei modelli di pagina personalizzati](https://web.archive.org/web/20180816221834/https://blogs.adobe.com/experiencedelivers/experience-management/integrating-dtm-custom-aem6-page-template).
