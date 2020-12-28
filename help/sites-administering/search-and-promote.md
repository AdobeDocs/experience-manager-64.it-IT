---
title: Integrazione con  Search&Promote Adobe
seo-title: Integrazione con  Search&Promote Adobe
description: Scoprite come integrare  Search&Promote Adobe.
seo-description: Scoprite come integrare  Search&Promote Adobe.
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---


# Integrazione con  Search&amp;Promote Adobe{#integrating-with-adobe-search-promote}

Per richiamare il servizio di Search&amp;Promote  dal sito Web, effettuate le seguenti operazioni:

1. Specificate l&#39;URL del cloud.
1. Configurare la connessione al servizio Search&amp;Promote.
1. Aggiungere componenti Search&amp;Promote alla barra laterale [!UICONTROL Sidekick].
1. Utilizzate i componenti per creare il contenuto. (Vedere [Aggiunta di funzionalità di Search&amp;Promote a una pagina Web](/help/sites-authoring/search-and-promote.md).)
1. Aggiungete i banner alle pagine. Le immagini dei banner sono sensibili ai dati degli Search&amp;Promote.
1. Generare una mappa del sito per il servizio di Search&amp;Promote da utilizzare.

>[!NOTE]
>
>Se utilizzate Search&amp;Promote con una configurazione proxy personalizzata, dovete configurare sia le configurazioni proxy del client HTTP, in quanto alcune funzionalità di AEM utilizzano le API 3.x, sia le API 4.x:
>
>* 3.x è configurato con [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x è configurato con [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## Modifica dell&#39;URL del servizio di Search&amp;Promote {#changing-the-search-promote-service-url}

L&#39;URL predefinito configurato per il servizio di Search&amp;Promote è `https://searchandpromote.omniture.com/px/`. Per usare un servizio diverso, usate la console OSGi per specificare un URL diverso.

**Per modificare l&#39;URL** del servizio di Search&amp;Promote:

1. Aprite la console [!UICONTROL OSGi] e toccate la scheda **[!UICONTROL Configuration]**. ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. Fare clic sull&#39;elemento **[!UICONTROL Configurazione Search&amp;Promote giorno CQ]**.
1. Nel campo di testo **[!UICONTROL URI del server remoto]**, immettere l&#39;URL, quindi toccare **[!UICONTROL Salva]**.

## Configurazione della connessione all&#39;Search&amp;Promote {#configuring-the-connection-to-search-promote}

Configurate una o più connessioni alle Search&amp;Promote in modo che le pagine Web possano interagire con il servizio. Per connettersi, è necessario l&#39;identificazione del membro e il numero di account dell&#39;account di Search&amp;Promote.

**Per configurare la connessione all&#39;Search&amp;Promote**:

1. Dall&#39;icona **[!UICONTROL Strumenti]** > **[!UICONTROL Distribuzione]**, selezionare **[!UICONTROL Cloud Services]**.

   Viene visualizzato il Pannello Cloud Services. Se su un computer locale, l&#39;URL del dashboard sarà simile al seguente:

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. Nella pagina [!UICONTROL Cloud Services], toccare il collegamento **[!UICONTROL Adobe Search&amp;Promote]** o l&#39;icona **[!UICONTROL Search&amp;Promote]**.

1. Se si tratta della prima volta che si sta configurando  Search&amp;Promote, toccare **[!UICONTROL Configura ora]** per aprire il pannello [!UICONTROL Crea configurazione].

   Per ulteriori informazioni sull&#39;Search&amp;Promote, fare clic su **[!UICONTROL Ulteriori informazioni]**.

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. Immettete un **[!UICONTROL Titolo]** riconoscibile per gli autori di pagine, quindi immettete un **[!UICONTROL Nome]** univoco, quindi toccate **[!UICONTROL Crea]**.

   Inoltre, la configurazione appena creata viene visualizzata sotto **[!UICONTROL Configurazioni disponibili]** nel **[!UICONTROL pannello Cloud Services]**  Adobe Search&amp;Promote voce di elenco.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. Nella finestra di dialogo [!UICONTROL Modifica componente], aggiungere quanto segue ai campi:

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
   >Dove **XXXXXXXX** corrisponde al **[!UICONTROL ID membro]** e **[!UICONTROL spYYYYYYYYYY]** corrisponde al numero del vostro account.

1. Toccate **[!UICONTROL Connetti a Search&amp;Promote]**.

   Quando viene visualizzato il messaggio di riuscita della connessione, toccate **[!UICONTROL OK]**.

   Dopo la connessione, il testo del pulsante diventa **[!UICONTROL Connetti di nuovo a Search&amp;Promote]**.

1. Toccate **[!UICONTROL OK]**. Viene visualizzata la pagina Impostazioni Search&amp;Promote per la configurazione appena creata.

## Configurazione del centro dati {#configuring-the-data-center}

Se l&#39;account di Search&amp;Promote è in Asia o in Europa, è necessario modificare il centro dati predefinito in modo che punti a quello destro (il centro dati predefinito è per gli account nordamericani).

**Per configurare il data center**:

1. Andate alla console Web all&#39;indirizzo `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. A seconda della posizione del server, imposta l’URI su una delle seguenti opzioni:

   * America del Nord: [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC: [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. Toccate **[!UICONTROL Salva]**.

## Aggiunta di componenti Search&amp;Promote alla barra laterale {#adding-search-promote-components-to-sidekick}

In modalità [!UICONTROL Progettazione], modificare un componente **[!UICONTROL par]** per consentire ai componenti Search&amp;Promote in [!UICONTROL Barra laterale]. Per ulteriori informazioni, consultare la documentazione relativa ai [componenti](/help/sites-developing/components.md).

Per informazioni sull&#39;utilizzo dei componenti, vedere [Aggiunta di funzionalità di Search&amp;Promote a una pagina Web](/help/sites-authoring/search-and-promote.md).

## Specifica del servizio di Search&amp;Promote utilizzato dalle pagine {#specifying-the-search-promote-service-that-your-pages-use}

Configurate le pagine Web in modo che utilizzino un servizio Search&amp;Promote specifico. I componenti di Search&amp;Promote utilizzano automaticamente il servizio della pagina host.

Quando si configurano le proprietà degli Search&amp;Promote per una pagina, tutte le pagine figlie ereditano le impostazioni. Se necessario, potete configurare le pagine figlie in modo da ignorare le impostazioni ereditate.

>[!NOTE]
>
>La connessione del servizio deve essere già configurata. Vedere [Configurare la connessione a Search&amp;Promote](#configuring-the-connection-to-search-promote).

1. Aprire la finestra di dialogo **[!UICONTROL Proprietà pagina]**. Ad esempio, nella pagina **[!UICONTROL Siti Web]** fare clic con il pulsante destro del mouse sulla pagina e scegliere **[!UICONTROL Proprietà]**.

1. Fare clic sulla scheda **[!UICONTROL Cloud Services]**.

1. Per disabilitare l&#39;ereditarietà delle configurazioni dei servizi cloud da una pagina padre, fai clic sull&#39;icona lucchetto accanto al percorso di ereditarietà.

   ![sandpinheritpadlock](assets/sandpinheritpadlock.png)

1. Fare clic su **[!UICONTROL Aggiungi servizio]**, selezionare **[!UICONTROL Search&amp;Promote]**, quindi fare clic su **[!UICONTROL OK]**.

1. Selezionate la configurazione della connessione per l&#39;account di Search&amp;Promote, quindi fate clic su **[!UICONTROL OK]**.

## Feed prodotto {#product-feed}

L’integrazione di Search&amp;Promote consente di effettuare le seguenti operazioni:

* Utilizzate l&#39;API [!UICONTROL eCommerce], indipendentemente dalla struttura del repository sottostante e dalla piattaforma di eCommerce.
* Sfruttate la funzione [!UICONTROL Connettore indice] di Search&amp;Promote per fornire un feed di prodotto in formato XML.
* Sfruttate la funzione [!UICONTROL Controllo remoto] del Search&amp;Promote per eseguire richieste on-demand o pianificate del feed di prodotto.
* Generazione di feed per account di Search&amp;Promote diversi, configurati come configurazioni di servizi cloud.

Per ulteriori informazioni, vedere [Feed prodotto](/help/sites-administering/product-feed.md).
