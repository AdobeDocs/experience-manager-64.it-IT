---
title: Esternalizzazione degli URL
seo-title: Externalizing URLs
description: L’esternalizzatore è un servizio OSGI che consente di trasformare programmaticamente un percorso di risorsa in un URL esterno e assoluto
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: ea887096-1a48-4bdb-bc5c-e4fe719e5632
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 53342acb-c1a5-443d-8727-cb27cc9d6845
exl-id: 123ef72b-f09b-47eb-9b5a-e0deb38799df
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---

# Esternalizzazione degli URL{#externalizing-urls}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In AEM, il **Esternalizzatore** è un servizio OSGI che consente di trasformare programmaticamente un percorso di risorsa (ad es. `/path/to/my/page`) in un URL esterno e assoluto (ad esempio, `https://www.mycompany.com/path/to/my/page`) prefissando il percorso con un DNS preconfigurato.

Poiché un’istanza non può conoscere il suo URL visibile esternamente se è in esecuzione dietro un livello web e poiché a volte un collegamento deve essere creato al di fuori dell’ambito della richiesta, questo servizio fornisce una posizione centrale per configurare tali URL esterni e generarli.

Questa pagina spiega come configurare il **Esternalizzatore** e come usarlo. Per ulteriori informazioni, consulta la [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## Configurazione del servizio Externalizer {#configuring-the-externalizer-service}

La **Esternalizzatore** il servizio ti consente di definire centralmente più domini che possono essere utilizzati per prefisso programmaticamente i percorsi delle risorse. Ogni dominio è identificato da un nome univoco utilizzato per fare riferimento programmaticamente al dominio.

Per definire una mappatura del dominio per **Esternalizzatore** servizio:

1. Passa alla gestione della configurazione tramite **Strumenti**, quindi **Console web** o immetti `https://<host>:<port>/system/console/configMgr.`
1. Fai clic su **Day CQ Link Externalizer** per aprire la finestra di dialogo di configurazione.

   >[!NOTE]
   >
   >Il collegamento diretto alla configurazione è `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. Definire una mappatura del dominio: una mappatura consiste in un nome univoco che può essere utilizzato nel codice per fare riferimento al dominio, a uno spazio e al dominio:

   `<unique-name> [scheme://]server[:port][/contextpath]`, Dove:

   * **schema** di solito è http o https, ma può anche essere ftp ecc.; utilizza https per applicare i collegamenti https, se necessario; viene utilizzato se il codice client non sostituisce lo schema quando si richiede l’esternalizzazione di un URL.
   * **server** è il nome host (può essere un nome di dominio o un indirizzo ip).
   * **porta** (facoltativo) è il numero di porta.
   * **contextpath** (facoltativo) è impostato solo se AEM è installato come applicazione web in un percorso contestuale diverso.

   Esempio: `production https://my.production.instance`

   I seguenti nomi di mappatura sono predefiniti e devono sempre essere impostati in base a AEM:

   * **locale** - l&#39;istanza locale
   * **autore** - DNS del sistema di authoring
   * **pubblicare** - DNS del sito web pubblico

   >[!NOTE]
   >
   >Una configurazione personalizzata consente di aggiungere una nuova categoria, ad esempio &quot;produzione&quot;, &quot;staging&quot; o anche sistemi esterni non AEM come &quot;my-internal-webservice&quot; ed è utile per evitare la codifica fissa di tali URL in diverse posizioni nella base di codice di un progetto.

1. Fai clic su **Salva** per salvare le modifiche.

>[!NOTE]
>
>L’Adobe consiglia di [aggiungi la configurazione al repository](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

## Utilizzo del servizio Externalizer {#using-the-externalizer-service}

Questa sezione mostra alcuni esempi di come **Esternalizzatore** può essere utilizzato.

**Per ottenere il servizio Externalizer in un JSP:**

`Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);`

**Per esternalizzare un percorso con il dominio &quot;pubblica&quot;:**

`String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";`

Supponendo la mappatura del dominio &quot; `publish https://www.website.com`&quot;, myExternalizedUrl termina con il valore &quot; `https://www.website.com/contextpath/my/page.html`&quot;.

**Per esternalizzare un percorso con il dominio &quot;author&quot;:**

`String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";`

Supponendo la mappatura del dominio &quot; `author https://author.website.com`&quot;, myExternalizedUrl termina con il valore &quot; `https://author.website.com/contextpath/my/page.html`&quot;.

**Per esternalizzare un percorso con il dominio &quot;locale&quot;:**

`String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";`

Supponendo la mappatura del dominio &quot; `local https://publish-3.internal`&quot;, myExternalizedUrl termina con il valore &quot; `https://publish-3.internal/contextpath/my/page.html`&quot;.

Puoi trovare ulteriori esempi nella sezione [Javadocs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
