---
title: Componenti Clientlibs for Communities
seo-title: Clientlibs for Communities Components
description: Librerie lato client per Communities
seo-description: Client-side libraries for Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 4%

---

# Componenti Clientlibs for Communities {#clientlibs-for-communities-components}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

Questa sezione della documentazione descrive come aggiungere librerie lato client (clientlibs) a una pagina per i componenti di Communities.

Per informazioni di base, visita:

* [Utilizzo delle librerie lato client](../../help/sites-developing/clientlibs.md) che fornisce dettagli sull’utilizzo e strumenti di debug
* [Clientlibs per SCF](client-customize.md#clientlibs) che fornisce informazioni utili durante la personalizzazione dei componenti SCF

## Perché sono necessarie le clientlibs {#why-clientlibs-are-required}

Le librerie client sono necessarie per il corretto funzionamento (JavaScript) e lo stile (CSS) di un componente.

Quando esiste una [funzione comunitaria](functions.md) per una funzione, tutti i componenti e le configurazioni necessarie, incluse le clientlib richieste, saranno presenti nel sito community. Solo se gli autori devono disporre di componenti aggiuntivi, è necessario aggiungere ulteriori clientlibs.

Se mancano le clientlib richieste, [aggiunta di un componente Community a una pagina](author-communities.md) potrebbe causare errori javascript e un aspetto imprevisto.

### Esempio: Recensioni posizionate senza Clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Esempio: Recensioni inserite con Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identificazione delle librerie client richieste {#identifying-required-clientlibs}

Le informazioni essenziali sulle funzioni per gli sviluppatori identificano le clientlib richieste.

Inoltre, da un&#39;istanza AEM, naviga fino al [Guida ai componenti della community](components-guide.md) fornisce l’accesso a un elenco di categorie clientlib richieste per un componente.

Ad esempio, nella parte superiore della [Pagina Recensioni](http://localhost:4502/content/community-components/en/reviews.html) le clientlibs richieste elencate sono

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Aggiunta di clientlibs richiesti {#adding-required-clientlibs}

Se desideri aggiungere un componente Community a una pagina, dovrai aggiungere le clientlib richieste per il componente, se non già presenti.

Utilizzo [CRXDE|Lite](#using-crxde-lite) per modificare un elenco clientlibslist esistente per una pagina del sito community.

Per aggiungere una clientlib per un sito della community utilizzando [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Sfoglia per [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Individua il `clientlibslist` nodo della pagina in cui si desidera aggiungere il componente

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Con `clientlibslist` nodo selezionato

   * Individua la stringa[] property `scg:requiredClientLibs`
   * Seleziona i relativi `Value` per accedere alla finestra di dialogo Array di stringa

      * Scorri verso il basso se necessario
      * Seleziona `+` per immettere una nuova libreria client

         * Ripeti l’operazione per aggiungere altre librerie client
      * Seleziona **[!UICONTROL OK]**
   * Seleziona **[!UICONTROL Salva tutto]**



>[!NOTE]
>
>Se il sito non è un sito community, è necessario individuare l’esistenza o la posizione delle librerie client in uso per il sito.

Utilizzo della [Guida introduttiva ad AEM Communities](getting-started.md) esempio, dove `site-name` è *coinvolgere*, questo è il modo in cui apparirebbe la clientliblist se si aggiungesse il componente recensioni:

![chlimage_1-247](assets/chlimage_1-247.png)
