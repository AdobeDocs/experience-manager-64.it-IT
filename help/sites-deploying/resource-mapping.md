---
title: Mapping delle risorse
seo-title: Mapping delle risorse
description: Scoprite come definire reindirizzamenti, URL personalizzati e host virtuali per AEM utilizzando la mappatura delle risorse.
seo-description: Scoprite come definire reindirizzamenti, URL personalizzati e host virtuali per AEM utilizzando la mappatura delle risorse.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
translation-type: tm+mt
source-git-commit: c4ac10736c937198aa0c81ecf547dd489ef93366
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 1%

---


# Mapping delle risorse{#resource-mapping}

La mappatura delle risorse viene utilizzata per definire reindirizzamenti, URL personalizzati e host virtuali per AEM.

Ad esempio, è possibile utilizzare queste mappature per:

* Prefissate tutte le richieste in `/content` modo che la struttura interna sia nascosta ai visitatori del sito Web.
* Definite un reindirizzamento in modo che tutte le richieste alla `/content/en/gateway` pagina del sito Web vengano reindirizzate a `https://gbiv.com/`.

Una possibile mappatura HTTP [prefissa tutte le richieste a localhost:4503 con /content](#configuring-an-internal-redirect-to-content). Una mappatura di questo tipo potrebbe essere utilizzata per nascondere la struttura interna dai visitatori al sito Web, così come consente:

`localhost:4503/content/geometrixx/en/products.html`

per l’accesso tramite:

`localhost:4503/geometrixx/en/products.html`

come la mappatura aggiungerà automaticamente il prefisso `/content` a `/geometrixx/en/products.html`.

>[!CAUTION]
>
>Gli URL personalizzati non supportano i pattern regolari.

>[!NOTE]
>
>Per ulteriori informazioni, consulta la documentazione Sling e [Mappature per la risoluzione](https://sling.apache.org/site/resources.html) delle risorse e [le risorse](https://sling.apache.org/site/mappings-for-resource-resolution.html) .

## Visualizzazione delle definizioni di mapping {#viewing-mapping-definitions}

Le mappature sono due elenchi che il Risolutore risorse JCR valuta (dall&#39;alto verso il basso) per trovare una corrispondenza.

Questi elenchi possono essere visualizzati (insieme alle informazioni di configurazione) nell’opzione **JCR ResourceResolver** della console Felix; ad esempio `https://<host>:<port>/system/console/jcrresolver`:

* Configurazione

   Mostra la configurazione corrente (come definita per il Risolutore risorse Sling [Apache](/help/sites-deploying/osgi-configuration-settings.md)).

* Test di configurazione

   Consente di inserire un URL o un percorso di risorsa. Fate clic su **Risolvi** o **Mappa** per confermare come il sistema trasformerà la voce.

* **Voci** mappa di risoluzione L&#39;elenco di voci utilizzate dai metodi ResourceResolver.resolve per mappare gli URL sulle risorse.

* **Mappatura voci** mappa Elenco di voci utilizzate dai metodi ResourceResolver.map per mappare i percorsi delle risorse agli URL.

I due elenchi mostrano varie voci, comprese quelle definite come predefinite dalle applicazioni. Spesso con lo scopo di semplificare gli URL per l’utente.

Gli elenchi associano un **pattern**, un&#39;espressione regolare associata alla richiesta, con una **Sostituzione** che definisce il reindirizzamento da imporre.

Ad esempio:

**Pattern** `^[^/]+/[^/]+/welcome$`

attiverà:

**Sostituzione** `/libs/cq/core/content/welcome.html`.

per reindirizzare una richiesta:

`http://localhost:4503/welcome`

a:

`http://localhost:4503/libs/cq/core/content/welcome.html`

All&#39;interno dell&#39;archivio vengono create nuove definizioni di mapping.

>[!NOTE]
>
>Sono disponibili numerose risorse che spiegano come definire le espressioni regolari; ad esempio [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Creazione di definizioni di mapping in AEM {#creating-mapping-definitions-in-aem}

In un’installazione standard di AEM potete trovare la cartella:

`/etc/map/http`

Questa è la struttura utilizzata per definire le mappature per il protocollo HTTP. In altre cartelle ( `sling:Folder`) è possibile creare `/etc/map` per qualsiasi altro protocollo da mappare.

### Configurazione di un reindirizzamento interno a /content {#configuring-an-internal-redirect-to-content}

Per creare la mappatura che prefissa qualsiasi richiesta a http://localhost:4503/ con `/content`:

1. Utilizzando CRXDE navigate fino a `/etc/map/http`.

1. Crea un nuovo nodo:

   * **Tipo** `sling:Mapping`

      Questo tipo di nodo è destinato a tali mappature, anche se il suo utilizzo non è obbligatorio.

   * **Nome** `localhost_any`

1. Fate clic su **Salva tutto**.
1. **Aggiungi** le seguenti proprietà al nodo:

   * **Nome** `sling:match`

      * **Tipo** `String`
      * **Valore** `localhost.4503/`
   * **Nome** `sling:internalRedirect`

      * **Tipo** `String`
      * **Valore** `/content/`


1. Fate clic su **Salva tutto**.

Questo gestirà una richiesta come:\
`localhost:4503/geometrixx/en/products.html`\
come se:\
`localhost:4503/content/geometrixx/en/products.html`\
era stato richiesto.

>[!NOTE]
>
>Consulta [Risorse](https://sling.apache.org/site/mappings-for-resource-resolution.html) nella Documentazione Sling per ulteriori informazioni sulle proprietà di sling disponibili e su come configurarle.

>[!NOTE]
>
>Potete usare `/etc/map.publish` per conservare le configurazioni dell’ambiente di pubblicazione. Devono quindi essere replicati e la nuova posizione ( `/etc/map.publish`) configurata per la posizione **di** mapping del Risolutore risorse Sling [Apache](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) dell&#39;ambiente di pubblicazione.

