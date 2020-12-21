---
title: Clientlibs per componenti Community
seo-title: Clientlibs per componenti Community
description: Librerie lato client per Communities
seo-description: Librerie lato client per Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 2%

---


# Componenti Clientlibs per Community {#clientlibs-for-communities-components}

## Introduzione {#introduction}

Questa sezione della documentazione descrive come aggiungere librerie lato client (clientlibs) a una pagina per i componenti Community.

Per informazioni di base, visita:

* [Utilizzo delle ](../../help/sites-developing/clientlibs.md) librerie lato client per fornire dettagli di utilizzo e strumenti di debug
* [Clientlibs per ](client-customize.md#clientlibs) SCF, che fornisce informazioni utili per la personalizzazione dei componenti SCF
* [Blog: AEM librerie client spiegate dall&#39;esempio](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Perché Clientlibs sono richiesti {#why-clientlibs-are-required}

Per il corretto funzionamento (JavaScript) e lo stile (CSS) di un componente sono necessari i client.

Quando esiste una [funzione community](functions.md) per una funzione, tutti i componenti e le configurazioni necessari, inclusi i clientlibs richiesti, saranno presenti nel sito community. Solo se agli autori devono essere disponibili componenti aggiuntivi, è necessario aggiungere altri clientlibé.

Se mancano i clientlibs richiesti, l&#39;aggiunta di un componente Community a una pagina[ potrebbe causare errori javascript e un aspetto imprevisto.](author-communities.md)

### Esempio: Recensioni inserite senza Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Esempio: Recensioni inserite con Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identificazione delle librerie di client necessarie {#identifying-required-clientlibs}

Le informazioni essenziali sulle funzioni per gli sviluppatori identificano i clientlibs richiesti.

Inoltre, da un&#39;istanza AEM, l&#39;accesso alla [Guida ai componenti della community](components-guide.md) consente di accedere a un elenco delle categorie clientlib richieste per un componente.

Ad esempio, nella parte superiore della pagina [Recensioni](http://localhost:4502/content/community-components/en/reviews.html) i clientlibs richiesti elencati sono

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Aggiunta di Clientlibs richiesti {#adding-required-clientlibs}

Se si desidera aggiungere un componente Community a una pagina, sarà necessario aggiungere i clientlibs richiesti per il componente, se non è già presente.

Utilizzate [CRXDE|Lite](#using-crxde-lite) per modificare un elenco di clientlibslist esistente per una pagina di sito community.

Per aggiungere una clientlib per un sito community utilizzando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Passa a [https://&lt;server>:&lt;porta>/crx/de](http://localhost:4502/crx/de)
* Individuare il nodo `clientlibslist` per la pagina in cui si desidera aggiungere il componente

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Con il nodo `clientlibslist` selezionato

   * Individuare la proprietà String[] `scg:requiredClientLibs`
   * Selezionare `Value` per accedere alla finestra di dialogo dell&#39;array String

      * Scorri verso il basso se necessario
      * Selezionare `+` per inserire una nuova libreria client

         * Ripeti per aggiungere altre librerie client
      * Selezionare **[!UICONTROL OK]**
   * Selezionare **[!UICONTROL Salva tutto]**



>[!NOTE]
>
>Se il sito non è un sito community, è necessario individuare l&#39;esistenza o la posizione delle librerie client in uso per il sito.

Utilizzando l&#39;esempio [Guida introduttiva a  AEM Communities](getting-started.md), dove `site-name` è *interazione*, l&#39;elenco clientliblist viene visualizzato in questo modo se si aggiunge il componente recensioni:

![chlimage_1-247](assets/chlimage_1-247.png)

