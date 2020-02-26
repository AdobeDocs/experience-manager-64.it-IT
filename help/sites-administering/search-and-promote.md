---
title: Integrazione con Adobe Search&Promote
seo-title: Integrazione con Adobe Search&Promote
description: Scopri come integrare Adobe Search&Promote.
seo-description: Scopri come integrare Adobe Search&Promote.
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Integrating with Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

Per chiamare il servizio Adobe Search&amp;Promote dal sito Web, effettuate le seguenti operazioni:

1. Specificate l&#39;URL del cloud.
1. Configurare la connessione al servizio Search&amp;Promote.
1. Aggiungere componenti Search&amp;Promote alla barra [!UICONTROL laterale].
1. Utilizzate i componenti per creare il contenuto. Consultate [Aggiunta di funzioni Search&amp;Promote a una pagina](/help/sites-authoring/search-and-promote.md)Web.
1. Aggiungete i banner alle pagine. Le immagini dei banner sono sensibili ai dati Search&amp;Promote.
1. Generate una mappa del sito per il servizio Search&amp;Promote da utilizzare.

>[!NOTE]
>
>Se utilizzate Search&amp;Promote con una configurazione proxy personalizzata, è necessario configurare sia le configurazioni proxy client HTTP, in quanto alcune funzionalità di AEM utilizzano le API 3.x, sia le API 4.x:
>
>* 3.x è configurato con [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x è configurato con [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



## Modifica dell’URL del servizio Search&amp;Promote {#changing-the-search-promote-service-url}

L’URL predefinito configurato per il servizio Search&amp;Promote è `https://searchandpromote.omniture.com/px/`. Per usare un servizio diverso, usate la console OSGi per specificare un URL diverso.

**Per modificare l’URL** del servizio Search&amp;Promote:

1. Aprite la console [!UICONTROL OSGi] e toccate la scheda **[!UICONTROL Configurazione]** . ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. Fate clic sull’elemento Configurazione **[!UICONTROL di CQ Search&amp;Promote]** Day.
1. Nel campo di testo URI **[!UICONTROL del server]** remoto, immettete l&#39;URL, quindi toccate **[!UICONTROL Salva]**.

## Configurazione della connessione a Search&amp;Promote {#configuring-the-connection-to-search-promote}

Configurate una o più connessioni a Search&amp;Promote in modo che le pagine Web possano interagire con il servizio. Per connettersi, è necessario l&#39;identificazione dei membri e il numero di account dell&#39;account Search&amp;Promote.

**Per configurare la connessione a Search&amp;Promote**:

1. Dall&#39;icona **[!UICONTROL Strumenti]** > **[!UICONTROL Distribuzione]**, seleziona Servizi **** cloud.

   Viene aperta la Dashboard di Cloud Services. Se su un computer locale, l&#39;URL del dashboard sarà simile al seguente:

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. Nella pagina Servizi  cloud, tocca il collegamento **[!UICONTROL Adobe Search&amp;Promote]** o l’icona **[!UICONTROL Search&amp;Promote]** .

1. Se questa è la prima volta che configurate Adobe Search&amp;Promote, toccate **[!UICONTROL Configura ora]** per aprire il pannello [!UICONTROL Crea configurazione] .

   Per ulteriori informazioni su Search&amp;Promote, fai clic su **[!UICONTROL Ulteriori]** informazioni.

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. Immettete un **[!UICONTROL Titolo]** riconoscibile per gli autori delle pagine, quindi immettete un **[!UICONTROL Nome]** univoco, quindi toccate **[!UICONTROL Crea]**.

   Inoltre, la configurazione appena creata viene visualizzata sotto Configurazioni **** disponibili nella voce di elenco Dashboard **[!UICONTROL di]** Cloud Services di Adobe Search&amp;Promote.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. Nella finestra di dialogo [!UICONTROL Modifica componente] , aggiungere quanto segue ai campi:

   * **[!UICONTROL ID membro]**
   * **[!UICONTROL Numero account]**
   >[!NOTE]
   >
   >Per ottenere queste informazioni, accedi a:
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >utilizzando le credenziali Seach&amp;Promote valide (e-mail/password).
   >
   >Osservate l&#39;URL nella barra degli indirizzi del brouser. Dovrebbe essere simile al seguente:
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >Se **XXXXXXXX** corrisponde all’ID **** membro e **[!UICONTROL spYYYYYYYYYYYYYY]** corrisponde al numero del vostro account.

1. Tap **[!UICONTROL Connect To Search&amp;Promote]**.

   Quando viene visualizzato il messaggio di riuscita della connessione, toccate **[!UICONTROL OK]**.

   Dopo la connessione, il testo del pulsante cambia in **[!UICONTROL Riconnetti a Search&amp;Promote]**.

1. Toccate **[!UICONTROL OK]**. Viene visualizzata la pagina Impostazioni Search&amp;Promote per la configurazione appena creata.

## Configurazione del centro dati {#configuring-the-data-center}

Se l’account Search&amp;Promote si trova in Asia o in Europa, è necessario modificare il centro dati predefinito in modo che punti a quello destro (il centro dati predefinito è per gli account nordamericani).

**Per configurare il data center**:

1. Passate alla console Web in `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. A seconda della posizione del server, imposta l’URI su una delle seguenti opzioni:

   * America del Nord: [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC: [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. Toccate **[!UICONTROL Salva]**.

## Aggiunta di componenti Search&amp;Promote alla barra laterale {#adding-search-promote-components-to-sidekick}

In modalità [!UICONTROL Progettazione] , modificate un componente **[!UICONTROL par]** per consentire ai componenti Search&amp;Promote nella barra [!UICONTROL laterale]. (See the [Components](/help/sites-developing/components.md) documentation for more information.)

Per informazioni sull’utilizzo dei componenti, consultate [Aggiunta delle funzioni Search&amp;Promote a una pagina](/help/sites-authoring/search-and-promote.md)Web.

## Specifica del servizio Search&amp;Promote utilizzato dalle pagine {#specifying-the-search-promote-service-that-your-pages-use}

Configurate le pagine Web in modo che utilizzino un servizio specifico Search&amp;Promote. I componenti Search&amp;Promote utilizzano automaticamente il servizio della pagina host.

Quando configurate le proprietà Search&amp;Promote per una pagina, tutte le pagine figlie ereditano le impostazioni. Se necessario, potete configurare le pagine figlie in modo da ignorare le impostazioni ereditate.

>[!NOTE]
>
>La connessione del servizio deve essere già configurata. Consultate [Configurare la connessione a Search&amp;Promote](#configuring-the-connection-to-search-promote).

1. Aprire la finestra di dialogo Proprietà **** pagina. Ad esempio, nella pagina **[!UICONTROL Siti]** Web fare clic con il pulsante destro del mouse sulla pagina e scegliere **[!UICONTROL Proprietà]**.

1. Fate clic sulla scheda Servizi **** cloud.

1. Per disabilitare l&#39;ereditarietà delle configurazioni dei servizi cloud da una pagina padre, fai clic sull&#39;icona lucchetto accanto al percorso di ereditarietà.

   ![sandpinheritpadlock](assets/sandpinheritpadlock.png)

1. Fate clic su **[!UICONTROL Aggiungi servizio]**, selezionate **[!UICONTROL Adobe Search&amp;Promote]**, quindi fate clic su **[!UICONTROL OK]**.

1. Selezionate la configurazione di connessione per l’account Search&amp;Promote, quindi fate clic su **[!UICONTROL OK]**.

## Product Feed {#product-feed}

L’integrazione Search&amp;Promote consente di effettuare le seguenti operazioni:

* Utilizzate l&#39;API [!UICONTROL eCommerce] , indipendentemente dalla struttura del repository sottostante e dalla piattaforma di eCommerce.
* Sfruttate la funzione Connettore  indice di Search&amp;Promote per fornire un feed di prodotto in formato XML.
* Utilizzate la funzione [!UICONTROL Controllo] remoto di Search&amp;Promote per eseguire richieste on-demand o pianificate del feed di prodotto.
* Generazione di feed per diversi account Search&amp;Promote, configurati come configurazioni di servizi cloud.

Per ulteriori informazioni, consultate Feed [](/help/sites-administering/product-feed.md)prodotto.
