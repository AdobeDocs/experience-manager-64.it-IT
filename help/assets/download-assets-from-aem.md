---
title: Scarica le risorse digitali da [!DNL Adobe Experience Manager].
description: Scopri come scaricare le risorse da [!DNL Adobe Experience Manager] e abilitare o disabilitare la funzionalità di download.
contentOwner: AG
feature: Asset Management,Asset Distribution
role: User
exl-id: bfe4d597-1080-4de5-a100-73a5175863d7
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 3%

---

# Scaricare risorse da [!DNL Adobe Experience Manager] {#download-assets-from-aem}

Puoi scaricare le risorse, compresi i rendering statici e dinamici. In alternativa, puoi inviare e-mail con collegamenti alle risorse direttamente da [!DNL Adobe Experience Manager Assets]. Le risorse scaricate sono raggruppate in un file ZIP. Il file ZIP compresso ha una dimensione massima del file di 1 GB per il processo di esportazione. È consentito un massimo di 500 risorse totali per processo di esportazione.

>[!NOTE]
>
>I destinatari delle e-mail devono essere membri del gruppo `dam-users` per accedere al collegamento di download ZIP nel messaggio e-mail. Per poter scaricare le risorse, i membri devono disporre delle autorizzazioni per avviare flussi di lavoro che attivano il download delle risorse.

Non è possibile scaricare i tipi di risorse Set immagini, Set 360 gradi, Set di file multimediali diversi e Set carosello.

Per scaricare le risorse, effettua le seguenti operazioni:

1. Nell’angolo in alto a sinistra di AEM, tocca il logo [!DNL Experience Manager], quindi nella barra a sinistra tocca **[!UICONTROL Navigazione]**.
1. Nella pagina Navigazione, tocca **[!UICONTROL Risorse]** > **[!UICONTROL File.]**
1. Passa a una cartella contenente le risorse da scaricare.
1. Seleziona la cartella o seleziona una o più risorse all’interno della cartella.
1. Sulla barra degli strumenti, tocca **[!UICONTROL Scarica.]**

   ![Opzioni disponibili durante il download delle risorse da Experience Manager Assets](/help/assets/assets/asset_download_dialog.png)

   *Figura: Opzioni della finestra di dialogo Scarica.*

1. Nella finestra di dialogo Scarica selezionare le opzioni di download desiderate.

   | Opzione di esportazione o download | Descrizione |
   |---|---|
   | **[!UICONTROL Crea una cartella separata per ogni risorsa]** | Seleziona questa opzione per includere ogni risorsa scaricata, incluse le risorse in cartelle secondarie nidificate sotto la cartella padre della risorsa, in un’unica cartella sul computer locale. Quando questa opzione non è selezionata, per impostazione predefinita la gerarchia delle cartelle viene ignorata e tutte le risorse vengono scaricate in un&#39;unica cartella nel computer locale. |
   | **[!UICONTROL E-mail]** | Viene inviata all’utente una notifica e-mail. I modelli e-mail standard sono disponibili nelle seguenti posizioni:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> I modelli personalizzati durante la distribuzione sono disponibili nelle seguenti posizioni: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>È possibile archiviare modelli personalizzati specifici per il tenant nelle seguenti posizioni:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Assets]** | Seleziona questa opzione per scaricare la risorsa nel modulo originale senza rendering.<br>L’opzione Risorse secondarie è disponibile se la risorsa originale include risorse secondarie. |
   | **[!UICONTROL Rappresentazioni]** | Rappresentazione binaria di una risorsa. Le risorse hanno una rappresentazione principale, ossia quella del file caricato. Possono avere diverse rappresentazioni. <br> Con questa opzione, puoi selezionare le rappresentazioni da scaricare. Le rappresentazioni disponibili dipendono dalla risorsa selezionata. L’opzione è disponibile se la risorsa dispone di rendering. |
   | **[!UICONTROL Rendering dinamici]** | Seleziona questa opzione per generare una serie di rappresentazioni alternative in tempo reale. Quando selezioni questa opzione, selezioni anche le rappresentazioni che desideri creare dinamicamente selezionando dall&#39;elenco [Predefinito immagine](image-presets.md). <br>È inoltre possibile selezionare le dimensioni e l&#39;unità di misura, il formato, lo spazio colore, la risoluzione e qualsiasi modificatore di immagine opzionale, ad esempio l&#39;inversione dell&#39;immagine. L’opzione è disponibile solo se è stato abilitato [!DNL Dynamic Media] . |

1. Nella finestra di dialogo, tocca **[!UICONTROL Scarica.]**.

Quando selezioni una cartella da scaricare, viene scaricata l’intera gerarchia delle risorse sotto la cartella. Per includere ogni risorsa scaricata (incluse le risorse nelle cartelle figlie nidificate sotto la cartella principale) in una singola cartella, seleziona **[!UICONTROL Crea una cartella separata per ogni risorsa]**.

## Abilita il servlet di download delle risorse {#enable-asset-download-servlet}

Il servlet predefinito in [!DNL Experience Manager] consente agli utenti autenticati di emettere richieste di download simultanee di grandi dimensioni per la creazione di file ZIP di risorse visibili che possono sovraccaricare il server e la rete. Per attenuare i potenziali rischi DoS causati da questa funzione, il componente `AssetDownloadServlet` OSGi è disabilitato per impostazione predefinita per le istanze di pubblicazione.

Per consentire il download delle risorse dal tuo DAM, ad esempio quando utilizzi qualcosa come Asset Share Commons o un’altra implementazione simile a un portale, abilita manualmente il servlet tramite una configurazione OSGi. L’Adobe consiglia di impostare la dimensione del download consentito il più possibile bassa senza influire sui requisiti di download giornalieri. Un valore elevato può influire sulle prestazioni.

1. Crea una cartella con una convenzione di denominazione per la modalità di esecuzione di pubblicazione (`config.publish`): `/apps/<your-app-name>/config.publish`. Per definire le proprietà di configurazione per una modalità di esecuzione, vedere [Modalità di esecuzione](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).
1. Nella cartella di configurazione, crea un file di tipo `nt:file` denominato `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Compila `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` con quanto segue. Imposta una dimensione massima (in byte) per il download come valore di `asset.download.prezip.maxcontentsize`. L&#39;esempio seguente configura la dimensione massima del download ZIP in modo che non superi 100 kB.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Disattiva il servlet di download delle risorse {#disable-asset-download-servlet}

È possibile disabilitare `Asset Download Servlet` in un’istanza di [!DNL Experience Manager] Publish aggiornando la configurazione del dispatcher per bloccare eventuali richieste di download di risorse. Il servlet può anche essere disabilitato manualmente tramite la console OSGi direttamente.

1. Per bloccare le richieste di download delle risorse tramite una configurazione del dispatcher, modifica la configurazione `dispatcher.any` e aggiungi una regola alla sezione [filtro](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-access-to-content-filter). `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Per disabilitare il componente OSGi in un&#39;istanza Publish, accedi alla console OSGi all&#39;indirizzo `http://[aem_server]:[port]/system/console/components`. Individua `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` e fai clic su **[!UICONTROL Disattiva]**.

>[!MORELIKETHIS]
>
>* [Scaricare le risorse](drm.md) protette DRM.
>* [Scarica le risorse utilizzando l’app desktop Experience Manager su desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=it) Win o Mac.
>* [Scarica le risorse utilizzando il collegamento Risorse di Adobe dalle app](https://helpx.adobe.com/it/enterprise/using/manage-assets-using-adobe-asset-link.html) Adobe Creative Cloud supportate.

