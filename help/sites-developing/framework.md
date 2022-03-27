---
title: Framework di assegnazione tag AEM
seo-title: AEM Tagging Framework
description: Assegnare tag ai contenuti e sfruttare l’infrastruttura di assegnazione tag AEM
seo-description: Tag content and leverage the AEM Tagging infrastructure
uuid: 55ba5977-217b-4b0f-a794-ddb9216ee62b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 4b680d17-383b-4173-a444-0b7bdb24e6c8
feature: Tagging
exl-id: bae592db-dc36-409f-b841-0582c464c3f6
source-git-commit: 381e760d1634dec6c6cdb933fd4da6b4652e6ff7
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 0%

---

# Framework di assegnazione tag AEM{#aem-tagging-framework}

Per assegnare tag ai contenuti e sfruttare l’infrastruttura di assegnazione tag AEM :

* Il tag deve esistere come nodo di tipo [`cq:Tag`](#tags-cq-tag-node-type) in [nodo principale della tassonomia.](#taxonomy-root-node)
* Il nodo del contenuto con tag `NodeType` deve includere [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.
* La [TagID](#tagid) viene aggiunto al nodo del contenuto [`cq:tags`](#tagged-content-cq-tags-property) e risolve in un nodo di tipo [`cq:Tag`.](#tags-cq-tag-node-type)

## Tag : cq:Tag Node Type  {#tags-cq-tag-node-type}

La dichiarazione di un tag viene acquisita nell’archivio in un nodo di tipo `cq:Tag.`

Un tag può essere una parola semplice (ad esempio `fruit`) o rappresentano una tassonomia gerarchica (ad es. `fruit/apple`, vale a dire frutti in generale e mele più specifiche).

I tag sono identificati da un TagID univoco.

Un tag contiene metadati facoltativi, ad esempio un titolo, titoli localizzati e una descrizione. Il titolo deve essere visualizzato nelle interfacce utente anziché nel `TagID`, se presente.

Il framework di assegnazione tag consente inoltre di limitare gli autori e i visitatori del sito a utilizzare solo tag predefiniti specifici.

### Caratteristiche del tag {#tag-characteristics}

* Il tipo di nodo è `cq:Tag`.
* Il nome del nodo è un componente del [`TagID`.](#tagid)
* La [`TagID`](#tagid) include sempre [spazio dei nomi.](#tag-namespace)
* Facoltativo `jcr:title` (titolo da visualizzare nell&#39;interfaccia utente)
* Facoltativo `jcr:description` property
* Quando contiene nodi figlio, viene indicato come [tag contenitore .](#container-tags)
* Viene memorizzato nell’archivio sotto un percorso di base denominato [nodo principale della tassonomia.](#taxonomy-root-node)

### ID tag {#tagid}

A `TagID` identifica un percorso che si risolve in un nodo di tag nella directory archivio.

In genere, il `TagID` è una abbreviazione che inizia con lo spazio dei nomi o può essere assoluta a partire dal [nodo principale tassonomia](#taxonomy-root-node).

Quando il contenuto è contrassegnato, se non esiste ancora, la [`cq:tags`](#tagged-content-cq-tags-property) viene aggiunta al nodo del contenuto e il `TagID` viene aggiunto al valore della stringa array della proprietà.

La `TagID` è costituito da [namespace](#tag-namespace) seguito dal locale `TagID`. [Tag contenitore](#container-tags) dispongono di tag secondari che rappresentano un ordine gerarchico nella tassonomia. I tag secondari possono essere utilizzati per fare riferimento ai tag come qualsiasi altro tag locale `TagID`. Ad esempio, assegnare tag al contenuto con `fruit` è consentito, anche se si tratta di un tag contenitore con tag secondari, come `fruit/apple` e `fruit/banana`.

### Nodo principale tassonomia {#taxonomy-root-node}

Il nodo principale della tassonomia è il percorso di base per tutti i tag nel repository. Il nodo principale della tassonomia non deve essere un nodo di tipo `cq:Tag`.

In AEM, il percorso di base è `/content/cq:tags` e il nodo principale è di tipo `cq:Folder`.

### Spazio dei nomi tag {#tag-namespace}

I namespace consentono elementi di gruppo. Il caso d’uso più tipico è quello di avere uno spazio dei nomi per sito (pubblico, interno e portale) o per applicazione più grande (ad esempio Sites, Assets, Forms), ma i namespace possono essere utilizzati per varie altre esigenze. I namespace vengono utilizzati nell’interfaccia utente per mostrare solo il sottoinsieme di tag (ovvero i tag di un determinato namespace) applicabile al contenuto corrente.

Lo spazio dei nomi del tag è il primo livello della sottostruttura della tassonomia, che è il nodo immediatamente sotto la [nodo principale tassonomia](#taxonomy-root-node). Uno spazio dei nomi è un nodo di tipo `cq:Tag` il cui genitore non è un `cq:Tag` tipo di nodo.

Tutti i tag hanno uno spazio dei nomi. Se non viene specificato alcun namespace, il tag viene assegnato allo spazio dei nomi predefinito, ovvero `TagID` `default` (il titolo è `Standard Tags`) `/content/cq:tags/default`.

### Tag contenitore {#container-tags}

Un tag contenitore è un nodo di tipo `cq:Tag` contenente qualsiasi numero e tipo di nodi figlio, che consente di migliorare il modello di tag con metadati personalizzati.

Inoltre, i tag contenitore (o super tag) in una tassonomia fungono da sotto-somma di tutti i tag secondari. Ad esempio, il contenuto con tag `fruit/apple` è considerato con tag `fruit` anche. Ciò significa che la ricerca di contenuti con tag `fruit` troverà anche il contenuto con tag `fruit/apple`.

### Risoluzione degli ID tag {#resolving-tagids}

Se l’ID del tag contiene due punti `:`, separa lo spazio dei nomi dal tag o dalla tassonomia secondaria, che vengono poi separati con le normali barre `/`. Se l’ID del tag non ha due punti, viene implicito il namespace predefinito.

Di seguito è riportata la posizione standard e l’unica posizione dei tag `/content/cq:tags`.

Assegnare tag a percorsi o percorsi non esistenti che non puntano a un `cq:Tag` i nodi sono considerati non validi e vengono ignorati.

Nella tabella seguente sono riportati alcuni esempi `TagIDs`, i loro elementi e il modo in cui `TagID` risolve in un percorso assoluto nell&#39;archivio.

| `TagID` | Namespace | ID locale | Tag contenitore | Tag foglia | Percorso archivio assoluto |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Nessuno | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Nessuno | Nessuno | Nessuno | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Localizzazione del titolo del tag {#localization-of-tag-title}

Quando il tag include la stringa del titolo opzionale (`jcr:title`) è possibile localizzare il titolo per la visualizzazione aggiungendo la proprietà `jcr:title.<locale>`.

Per maggiori dettagli vedi:

* [Tag in diverse lingue,](/help/sites-developing/building.md#tags-in-different-languages) che descrive l’utilizzo delle API.
* [Gestione dei tag in diverse lingue,](/help/sites-administering/tags.md#managing-tags-in-different-languages) che descrive l’utilizzo della console Tagging .

### Controllo accesso {#access-control}

I tag esistono come nodi nell’archivio sotto [nodo principale della tassonomia.](#taxonomy-root-node) È possibile consentire o negare agli autori e ai visitatori del sito la possibilità di creare tag in un dato spazio dei nomi impostando ACL appropriati nell’archivio.

Inoltre, negare le autorizzazioni di lettura per alcuni tag o namespace controllerà la possibilità di applicare tag a contenuti specifici.

Una configurazione tipica include:

* Consentire la `tag-administrators` accesso in scrittura di gruppo/ruolo a tutti i namespace (aggiungere/modificare in `/content/cq:tags`).
   * Questo gruppo viene fornito con AEM preconfigurato.
* Consentire agli utenti/autori di accedere in lettura a tutti i namespace che dovrebbero essere leggibili per loro (per lo più tutti).
* Consentire a utenti/autori di accedere in scrittura a quei namespace in cui i tag devono essere liberamente definiti dagli utenti/autori (`add_node` sotto `/content/cq:tags/some_namespace`)

## Contenuto variabile : cq:Mixin taggabile {#taggable-content-cq-taggable-mixin}

Per consentire agli sviluppatori di applicazioni di allegare tag a un tipo di contenuto, la registrazione del nodo ([CND](https://jackrabbit.apache.org/node-type-notation.html)) deve includere `cq:Taggable` miscelazione o `cq:OwnerTaggable` mixin.

La `cq:OwnerTaggable` mixin, che eredita da `cq:Taggable`, indica che il contenuto può essere classificato dal proprietario/autore. In AEM, è solo un attributo del `cq:PageContent` nodo. La `cq:OwnerTaggable` il mixin non è richiesto dal framework di assegnazione tag.

>[!NOTE]
>
>Si consiglia di abilitare solo i tag sul nodo di primo livello di un elemento di contenuto aggregato (o sul relativo `jcr:content` node). Gli esempi includono:
>
>* Pagine ( `cq:Page`) dove `jcr:content`il nodo è di tipo `cq:PageContent` che include `cq:Taggable` mixin.
>* Risorse ( `cq:Asset`) dove `jcr:content/metadata` il nodo ha sempre `cq:Taggable` mixin.


### Notazione del tipo di nodo (CND) {#node-type-notation-cnd}

Le definizioni dei tipi di nodo esistono nell’archivio come file CND. La notazione CND è definita come parte della documentazione JCR [qui](https://jackrabbit.apache.org/node-type-notation.html).

Le definizioni essenziali per i tipi di nodo inclusi in AEM sono le seguenti:

```text
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## Contenuto con tag: cq:tags, proprietà {#tagged-content-cq-tags-property}

La `cq:tags` è un array di stringhe utilizzato per memorizzare uno o più `TagID`viene applicata al contenuto da autori o visitatori del sito. La proprietà ha un significato solo quando viene aggiunta a un nodo definito con [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.

>[!NOTE]
>
>Per sfruttare AEM funzionalità di assegnazione tag, le applicazioni sviluppate personalizzate non devono definire proprietà di tag diverse da `cq:tags`.

## Spostamento e unione dei tag {#moving-and-merging-tags}

Di seguito è riportata una descrizione degli effetti nell’archivio durante lo spostamento o l’unione dei tag utilizzando [Console di assegnazione tag](/help/sites-administering/tags.md):

* Quando un tag A viene spostato o unito nel tag B in `/content/cq:tags`:

   * Il tag A non viene eliminato e ottiene un `cq:movedTo` proprietà.
   * Il tag B viene creato (in caso di spostamento) e ottiene un `cq:backlinks` proprietà.

* `cq:movedTo` punta al tag B.

   * Questa proprietà significa che il tag A è stato spostato o unito nel tag B.
   * Lo spostamento del tag B comporterà l’aggiornamento di conseguenza di questa proprietà. Il tag A è quindi nascosto e viene conservato solo nell’archivio per risolvere gli ID tag nei nodi di contenuto che puntano al tag A.
   * Il tag Garbage Collector rimuove i tag come tag A una volta nessun altro nodo di contenuto li punta.
   * Un valore speciale per `cq:movedTo` è `nirvana`: viene applicata quando il tag viene eliminato ma non può essere rimosso dall’archivio perché sono presenti tag secondari con un `cq:movedTo` deve essere mantenuto.

      >[!NOTE]
      >
      >La `cq:movedTo` viene aggiunta al tag spostato o unito solo se viene soddisfatta una delle seguenti condizioni:
      >
      >1. Il tag viene utilizzato nel contenuto (ovvero ha un riferimento).
      >1. Il tag include elementi secondari già spostati.


* `cq:backlinks` mantiene i riferimenti nell’altra direzione, ovvero mantiene un elenco di tutti i tag spostati o uniti al tag B.

   * Questo è richiesto principalmente per mantenere `cq:movedTo`le proprietà sono aggiornate anche quando il tag B viene spostato/unito/eliminato o quando il tag B viene attivato, nel qual caso devono essere attivati anche tutti i suoi tag backlink.

>[!NOTE]
>
>La `cq:backlinks` viene aggiunta al tag spostato o unito solo se viene soddisfatta una delle seguenti condizioni:
>
>1. Il tag viene utilizzato nel contenuto (ovvero ha un riferimento).
>1. Il tag include elementi secondari già spostati.


* Lettura di un `cq:tags` di un nodo di contenuto comporta la seguente risoluzione:

   1. Se non c&#39;è alcuna corrispondenza in `/content/cq:tags`, non viene restituito alcun tag.
   1. Se il tag ha un `cq:movedTo` impostato sulla proprietà , viene seguito l&#39;ID tag di riferimento.

      * Questo passaggio viene ripetuto purché il tag seguito abbia un `cq:movedTo` proprietà.
   1. Se il tag seguito non ha un `cq:movedTo` , il tag viene letto.


* Per pubblicare la modifica quando un tag è stato spostato o unito, l’ `cq:Tag` e tutti i relativi backlink devono essere replicati.
   * Questa operazione viene eseguita automaticamente quando il tag viene attivato nella console di amministrazione dei tag.

* Aggiornamenti successivi al `cq:tags` la proprietà pulisce automaticamente i riferimenti &quot;vecchi&quot;.
   * Questo viene attivato perché la risoluzione di un tag spostato attraverso l&#39;API restituisce il tag di destinazione, fornendo così l&#39;ID del tag di destinazione.

## Migrazione dei tag {#tags-migration}

A partire da Adobe Experience Manager 6.4, i tag sono memorizzati in `/content/cq:tags`. Tuttavia, negli scenari in cui Adobe Experience Manager è stato aggiornato dalla versione precedente, i tag sono ancora presenti nella vecchia posizione `/etc/tags`. Nei sistemi aggiornati è necessario eseguire la migrazione dei tag in `/content/cq:tags`.

>[!NOTE]
>
>Nelle Proprietà pagina della pagina dei tag , si consiglia di utilizzare l’ID tag (ad esempio `geometrixx-outdoors:activity/biking`) invece di codificare il percorso di base del tag (ad esempio, `/etc/tags/geometrixx-outdoors/activity/biking`).
>
>Per elencare i tag, `com.day.cq.tagging.servlets.TagListServlet` può essere utilizzato.

>[!NOTE]
>
>È consigliabile utilizzare l’API di gestione tag come risorsa.

### Se l’istanza AEM aggiornata supporta l’API TagManager**

1. All’inizio del componente, l’API TagManager rileva se si tratta di un’istanza AEM aggiornata. Nel sistema aggiornato, i tag vengono memorizzati in `/etc/tags`.

1. L’API TagManager viene quindi eseguita in modalità di retrocompatibilità, il che significa che l’API utilizza `/etc/tags` come percorso di base. In caso contrario, utilizza una nuova posizione `/content/cq:tags`.

1. Aggiorna la posizione dei tag.

1. Dopo aver trasferito i tag nella nuova posizione, esegui lo script seguente.

```java
import org.apache.sling.api.resource.*
import javax.jcr.*

ResourceResolverFactory resourceResolverFactory = osgi.getService(ResourceResolverFactory.class);
ResourceResolver resolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
Session session = resolver.adaptTo(Session.class);

def queryManager = session.workspace.queryManager;
def statement = "/jcr:root/content/cq:tags//element(*, cq:Tag)[jcr:contains(@cq:movedTo,\'/etc/tags\') or jcr:contains(@cq:backlinks,\'/etc/tags\')]";
def query = queryManager.createQuery(statement, "xpath");

println "query = ${query.statement}\n";

def tags = query.execute().getNodes();


tags.each { node ->
        def tagPath = node.path;
        println "tag = ${tagPath}";

        if(node.hasProperty("cq:movedTo") && node.getProperty("cq:movedTo").getValue().toString().startsWith("/etc/tags")){

                def movedTo = node.getProperty("cq:movedTo").getValue().toString();

                println "cq:movedTo = ${movedTo} \n";

                movedTo = movedTo.replace("/etc/tags","/content/cq:tags");
                node.setProperty("cq:movedTo",movedTo);
        } else if(node.hasProperty("cq:backlinks")){

               String[] backLinks = node.getProperty("cq:backlinks").getValues();
               int count = 0;

               backLinks.each { value ->
                       if(value.startsWith("/etc/tags")){
                               println "cq:backlinks = ${value}\n";
                               backLinks[count] = value.replace("/etc/tags","/content/cq:tags");
    }
                       count++;
               }

               node.setProperty("cq:backlinks",backLinks);
  }
}
session.save();

println "---------------------------------Success-------------------------------------"
```

Lo script recupera tutti i tag che hanno `/etc/tags` nel valore di `cq:movedTo/cq:backLinks` proprietà. Quindi esegue un&#39;iterazione del set di risultati recuperato e risolve il `cq:movedTo` e `cq:backlinks` valori delle proprietà su `/content/cq:tags` (nel caso in cui `/etc/tags` viene rilevato nel valore).

### Se l’istanza AEM aggiornata viene eseguita nell’interfaccia classica**

>[!NOTE]
>
>L’interfaccia classica non è conforme allo zero tempi di inattività e non supporta il nuovo percorso di base dei tag. Se desideri utilizzare l’interfaccia classica anziché `/etc/tags` deve essere creato e `cq-tagging` riavvio del componente.

Se le istanze AEM aggiornate sono supportate dall’API TagManager ed eseguite nell’interfaccia classica:

1. Una volta fa riferimento al vecchio percorso di base tag `/etc/tags` vengono sostituiti utilizzando tagId o nuova posizione tag `/content/cq:tags`, puoi migrare i tag nella nuova posizione `/content/cq:tags` in CRX DE seguito dal riavvio del componente.

1. Dopo aver trasferito i tag nella nuova posizione, esegui lo script menzionato sopra.
