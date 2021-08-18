---
title: Componenti Clientlibs for Communities
seo-title: Componenti Clientlibs for Communities
description: Librerie lato client per Communities
seo-description: Librerie lato client per Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---

# Componenti Clientlibs for Communities {#clientlibs-for-communities-components}

## Introduzione {#introduction}

Questa sezione della documentazione descrive come aggiungere librerie lato client (clientlibs) a una pagina per i componenti di Communities.

Per informazioni di base, visita:

* [Utilizzo delle ](../../help/sites-developing/clientlibs.md) librerie lato client per informazioni sull’utilizzo e per strumenti di debug
* [Clientlibs per ](client-customize.md#clientlibs) SCF che fornisce informazioni utili durante la personalizzazione dei componenti SCF

## Perché sono necessarie le clientlibs {#why-clientlibs-are-required}

Le librerie client sono necessarie per il corretto funzionamento (JavaScript) e lo stile (CSS) di un componente.

Quando esiste una [funzione community](functions.md) per una funzione, tutti i componenti e le configurazioni necessarie, incluse le clientlib richieste, saranno presenti nel sito della community. Solo se gli autori devono disporre di componenti aggiuntivi, è necessario aggiungere ulteriori clientlibs.

Se mancano le clientlib richieste, l&#39;aggiunta di un componente Communities a una pagina](author-communities.md) potrebbe causare errori javascript e un aspetto imprevisto.[

### Esempio: Recensioni posizionate senza Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Esempio: Recensioni inserite con Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identificazione delle librerie client richieste {#identifying-required-clientlibs}

Le informazioni essenziali sulle funzioni per gli sviluppatori identificano le clientlib richieste.

Inoltre, da un&#39;istanza AEM, la navigazione alla [Guida ai componenti della community](components-guide.md) fornisce l&#39;accesso a un elenco delle categorie clientlib richieste per un componente.

Ad esempio, nella parte superiore della [Pagina recensioni](http://localhost:4502/content/community-components/en/reviews.html) le clientlibs richieste sono elencate

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Aggiunta di clientlibs richiesti {#adding-required-clientlibs}

Se desideri aggiungere un componente Community a una pagina, dovrai aggiungere le clientlib richieste per il componente, se non già presenti.

Utilizza [CRXDE|Lite](#using-crxde-lite) per modificare un elenco di clientlibslist esistente per una pagina del sito community.

Per aggiungere una clientlib per un sito community utilizzando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Vai a [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Individua il nodo `clientlibslist` della pagina in cui desideri aggiungere il componente

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Con il nodo `clientlibslist` selezionato

   * Individua la proprietà String[] `scg:requiredClientLibs`
   * Seleziona la relativa `Value` per accedere alla finestra di dialogo Array String

      * Scorri verso il basso se necessario
      * Seleziona `+` per inserire una nuova libreria client

         * Ripeti l’operazione per aggiungere altre librerie client
      * Seleziona **[!UICONTROL OK]**
   * Seleziona **[!UICONTROL Salva tutto]**



>[!NOTE]
>
>Se il sito non è un sito community, è necessario individuare l’esistenza o la posizione delle librerie client in uso per il sito.

Utilizzando l&#39;esempio [Guida introduttiva ad AEM Communities](getting-started.md), dove `site-name` è *coinvolgi*, questo è il modo in cui apparirebbe la lista clientliblist se si aggiunge il componente recensioni:

![chlimage_1-247](assets/chlimage_1-247.png)
