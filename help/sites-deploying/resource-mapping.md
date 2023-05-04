---
title: Mappatura delle risorse
seo-title: Resource Mapping
description: Scopri come definire reindirizzamenti, URL personalizzati e host virtuali per AEM utilizzando la mappatura delle risorse.
seo-description: Learn how to define redirects, vanity URLs and virtual hosts for AEM by using resource mapping.
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
feature: Configuring
exl-id: 81dddbab-1a9e-49ee-b2a5-a8e4de3630d1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 5%

---

# Mappatura delle risorse{#resource-mapping}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La mappatura delle risorse viene utilizzata per definire reindirizzamenti, URL personalizzati e host virtuali per AEM.

Ad esempio, puoi utilizzare queste mappature per:

* Prefisso tutte le richieste con `/content` in modo che la struttura interna sia nascosta ai visitatori del sito web.
* Definire un reindirizzamento in modo che tutte le richieste al `/content/en/gateway` vengono reindirizzati a `https://gbiv.com/`.

Una possibile mappatura HTTP [prefissa tutte le richieste a localhost:4503 con /content](#configuring-an-internal-redirect-to-content). Una mappatura come questa può essere utilizzata per nascondere la struttura interna dai visitatori al sito web in quanto consente:

`localhost:4503/content/geometrixx/en/products.html`

da accedere utilizzando:

`localhost:4503/geometrixx/en/products.html`

poiché la mappatura aggiunge automaticamente il prefisso `/content` a `/geometrixx/en/products.html`.

>[!CAUTION]
>
>Gli URL personalizzati non supportano i pattern regex.

>[!NOTE]
>
>Consulta la documentazione Sling e [Mappature per la risoluzione delle risorse](https://sling.apache.org/site/resources.html) e [Risorse](https://sling.apache.org/site/mappings-for-resource-resolution.html) per ulteriori informazioni.

## Visualizzazione delle definizioni di mappatura {#viewing-mapping-definitions}

Le mappature sono costituite da due elenchi che il risolutore risorse JCR valuta (dall’alto verso il basso) per trovare una corrispondenza.

Questi elenchi possono essere visualizzati (insieme alle informazioni di configurazione) nella sezione **JCR ResourceResolver** opzione della console Felix; ad esempio, `https://<host>:<port>/system/console/jcrresolver`:

* Configurazione

   Mostra la configurazione corrente (come definita per la [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md).

* Test di configurazione

   Consente di immettere un URL o un percorso di risorsa. Fai clic su **Risolvi** o **Mappa** per confermare come il sistema trasformerà la voce.

* **Voci di Resolver Map**
Elenco di voci utilizzate dai metodi ResourceResolver.resolve per mappare gli URL a Resources.

* **Voci mappa mappatura**
Elenco di voci utilizzate dai metodi ResourceResolver.map per mappare i percorsi delle risorse agli URL.

I due elenchi mostrano varie voci, incluse quelle definite come predefinite dalle applicazioni. Spesso mirano a semplificare gli URL per l’utente.

Gli elenchi corrispondono a una coppia **Pattern**, un’espressione regolare associata alla richiesta, con un **Sostituzione** che definisce il reindirizzamento da imporre.

Ad esempio:

**Pattern** `^[^/]+/[^/]+/welcome$`

attiverà:

**Sostituzione** `/libs/cq/core/content/welcome.html`.

per reindirizzare una richiesta:

`http://localhost:4503/welcome`

a:

`http://localhost:4503/libs/cq/core/content/welcome.html`

All&#39;interno dell&#39;archivio vengono create nuove definizioni di mappatura.

>[!NOTE]
>
>Sono disponibili numerose risorse che spiegano come definire le espressioni regolari; per esempio [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

## Creazione di definizioni di mappatura in AEM {#creating-mapping-definitions-in-aem}

In un’installazione standard di AEM è possibile trovare la cartella:

`/etc/map/http`

Questa è la struttura utilizzata per definire le mappature per il protocollo HTTP. Altre cartelle ( `sling:Folder`) può essere creata in `/etc/map` per qualsiasi altro protocollo da mappare.

### Configurazione di un reindirizzamento interno a /content {#configuring-an-internal-redirect-to-content}

Per creare la mappatura che prefissa qualsiasi richiesta a http://localhost:4503/ con `/content`:

1. Utilizzo di CRXDE per navigare a `/etc/map/http`.

1. Crea un nuovo nodo:

   * **Tipo** `sling:Mapping`

      Questo tipo di nodo è destinato a tali mappature, anche se il suo utilizzo non è obbligatorio.

   * **Nome** `localhost_any`

1. Fai clic su **Salva tutto**.
1. **Aggiungi** le seguenti proprietà di questo nodo:

   * **Nome** `sling:match`

      * **Tipo** `String`
      * **Valore** `localhost.4503/`
   * **Nome** `sling:internalRedirect`

      * **Tipo** `String`
      * **Valore** `/content/`


1. Fai clic su **Salva tutto**.

Questo gestirà una richiesta come:\
`localhost:4503/geometrixx/en/products.html`\
come se:\
`localhost:4503/content/geometrixx/en/products.html`\
era stato richiesto.

>[!NOTE]
>
>Vedi [Risorse](https://sling.apache.org/site/mappings-for-resource-resolution.html) nella documentazione Sling per ulteriori informazioni sulle proprietà sling disponibili e su come configurarle.

>[!NOTE]
>
>È possibile utilizzare `/etc/map.publish` per conservare le configurazioni per l’ambiente di pubblicazione. Questi devono quindi essere replicati e la nuova posizione ( `/etc/map.publish`) configurata per la **Posizione mappatura** del [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) dell’ambiente di pubblicazione.
