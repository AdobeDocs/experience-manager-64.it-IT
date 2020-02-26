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

---


# Clientlibs per componenti Community {#clientlibs-for-communities-components}

## Introduzione {#introduction}

Questa sezione della documentazione descrive come aggiungere librerie lato client (clientlibs) a una pagina per i componenti Community.

Per informazioni di base, visita:

* [Utilizzo delle librerie](../../help/sites-developing/clientlibs.md) lato client per fornire dettagli di utilizzo e strumenti di debug
* [Clientlibs per SCF](client-customize.md#clientlibs) che fornisce informazioni utili per la personalizzazione dei componenti SCF
* [Blog: Librerie client AEM spiegate ad esempio](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Perché Clientlibs sono richiesti {#why-clientlibs-are-required}

Per il corretto funzionamento (JavaScript) e lo stile (CSS) di un componente sono necessari i client.

Se esiste una funzione [](functions.md) comunitaria per una funzione, tutti i componenti e le configurazioni necessari, inclusi i clientlibs richiesti, saranno presenti nel sito della community. Solo se agli autori devono essere disponibili componenti aggiuntivi, è necessario aggiungere altri clientlibé.

Se i clientlibs richiesti non sono disponibili, l’ [aggiunta di un componente Community a una pagina](author-communities.md) potrebbe causare errori javascript e un aspetto imprevisto.

### Esempio: Recensioni inserite senza Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Esempio: Recensioni inserite con Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identificazione delle librerie di client necessarie {#identifying-required-clientlibs}

Le informazioni essenziali sulle funzioni per gli sviluppatori identificano i clientlibs richiesti.

Inoltre, da un’istanza di AEM, l’accesso alla Guida [ai componenti](components-guide.md) della community consente di accedere a un elenco delle categorie clientlib richieste per un componente.

Ad esempio, nella parte superiore della pagina [](http://localhost:4502/content/community-components/en/reviews.html) Recensioni i clientlibs richiesti sono elencati

* cq.ckeditor
* cq.social.hbs.recensioni

![chlimage_1-246](assets/chlimage_1-246.png)

## Aggiunta Di Client Richiesti {#adding-required-clientlibs}

Se si desidera aggiungere un componente Community a una pagina, sarà necessario aggiungere i clientlibs richiesti per il componente, se non è già presente.

Utilizzare [CRXDE|Lite](#using-crxde-lite) per modificare un elenco di clientlibslist esistente per una pagina di sito community.

Per aggiungere una clientlib per un sito community utilizzando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Passa a [https://&lt;server>:&lt;porta>/crx/de](http://localhost:4502/crx/de)
* Individuare il `clientlibslist` nodo della pagina in cui si desidera aggiungere il componente

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Con `clientlibslist` nodo selezionato

   * Individuare la proprietà String[]`scg:requiredClientLibs`
   * Selezionare la stringa `Value` per accedere alla finestra di dialogo dell&#39;array String

      * Scorri verso il basso se necessario
      * Selezionare `+` per immettere una nuova libreria client

         * Ripeti per aggiungere altre librerie client
      * Selezionare **[!UICONTROL OK]**
   * Seleziona **[!UICONTROL Salva tutto]**



>[!NOTE]
>
>Se il sito non è un sito community, è necessario individuare l&#39;esistenza o la posizione delle librerie client in uso per il sito.

Utilizzando l’esempio [Guida introduttiva ad AEM Communities](getting-started.md) , in cui `site-name` è *attiva*, l’elenco dei clienti verrà visualizzato così se si aggiunge il componente recensioni:

![chlimage_1-247](assets/chlimage_1-247.png)

