---
title: Esternalizzazione degli URL
seo-title: Esternalizzazione degli URL
description: Il servizio Externalizer è un servizio OSGI che consente di trasformare programmaticamente un percorso di risorse in un URL esterno e assoluto
seo-description: Il servizio Externalizer è un servizio OSGI che consente di trasformare programmaticamente un percorso di risorse in un URL esterno e assoluto
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573

---


# Esternalizzazione degli URL{#externalizing-urls}

In AEM, **Externalizer** è un servizio OSGI che consente di trasformare programmaticamente un percorso di risorse (ad es. `/path/to/my/page`) in un URL esterno e assoluto (ad esempio, `https://www.mycompany.com/path/to/my/page`) anteponendo il percorso a un DNS preconfigurato.

Poiché un’istanza non può conoscere il relativo URL visibile esternamente se è in esecuzione dietro un livello Web e poiché a volte è necessario creare un collegamento all’esterno dell’ambito della richiesta, il servizio fornisce una posizione centrale per configurare tali URL esterni e crearli.

Questa pagina spiega come configurare il servizio **Externalizer** e come utilizzarlo. Per ulteriori dettagli, fare riferimento a [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Configurazione del servizio Externalizer {#configuring-the-externalizer-service}

Il servizio **Externalizer** consente di definire a livello centrale più domini che possono essere utilizzati per il prefisso programmatico dei percorsi delle risorse. Ogni dominio è identificato da un nome univoco utilizzato per fare riferimento al dominio a livello di programmazione.

Per definire un mapping di dominio per il servizio **Externalizer** :

1. Passa a Gestione configurazione tramite **Strumenti**, Console **** Web o immetti `https://<host>:<port>/system/console/configMgr.`
1. Fate clic su **Day CQ Link Externalizer** per aprire la finestra di dialogo di configurazione.

   >[!NOTE]
   >
   >Il collegamento diretto alla configurazione è `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Definire un mapping di dominio: un mapping è costituito da un nome univoco che può essere utilizzato nel codice per fare riferimento al dominio, a uno spazio e al dominio:

   `<unique-name> [scheme://]server[:port][/contextpath]`, dove:

   * **di solito lo schema** è http o https, ma può anche essere ftp ecc; utilizzate https per applicare eventuali collegamenti https;viene utilizzato se il codice client non esclude lo schema quando si richiede l&#39;esternalizzazione di un URL.
   * **server** è il nome host (può essere un nome di dominio o un indirizzo IP).
   * **port** (facoltativo) è il numero della porta.
   * **contextpath** (facoltativo) è impostato solo se AEM è installato come app Web in un percorso contestuale diverso.
   Ad esempio: `production https://my.production.instance`

   I seguenti nomi di mappatura sono predefiniti e devono sempre essere impostati in base a quanto richiesto da AEM:

   * **local** - the local instance
   * **authoring** - DNS del sistema di authoring
   * **pubblicazione** - DNS del sito Web rivolto al pubblico
   >[!NOTE]
   >
   >Una configurazione personalizzata consente di aggiungere una nuova categoria, ad esempio &quot;produzione&quot;, &quot;pre-produzione&quot; o anche sistemi esterni non AEM come &quot;servizio Web interno&quot;, ed è utile per evitare la codifica di tali URL in diverse aree del codebase di un progetto.

1. Click **Save** to save your changes.

>[!NOTE]
>
>Adobe consiglia di [aggiungere la configurazione alla directory archivio](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Utilizzo del servizio Externalizer {#using-the-externalizer-service}

In questa sezione sono riportati alcuni esempi di utilizzo del servizio **Externalizer** .

**Per ottenere il servizio Externalizer in un JSP:**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Per esternalizzare un percorso con il dominio &#39;pubblica&#39;:**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

Presupponendo che la mappatura del dominio &quot; `publish https://www.website.com`&quot;, myExternalizedUrl finisca con il valore &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**Per esternalizzare un percorso con il dominio &#39;author&#39;:**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

Presupponendo che la mappatura del dominio &quot; `author https://author.website.com`&quot;, myExternalizedUrl finisca con il valore &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**Per esternalizzare un percorso con il dominio &#39;locale&#39;:**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

Presupponendo che la mappatura del dominio &quot; `local https://publish-3.internal`&quot;, myExternalizedUrl finisca con il valore &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Potete trovare altri esempi in [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
