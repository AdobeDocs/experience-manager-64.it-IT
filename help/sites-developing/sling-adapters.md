---
title: Utilizzo di adattatori Sling
seo-title: Utilizzo di adattatori Sling
description: Sling offre un pattern di adattatore per tradurre facilmente gli oggetti che implementano l'interfaccia Adattabile
seo-description: Sling offre un pattern di adattatore per tradurre facilmente gli oggetti che implementano l'interfaccia Adattabile
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
translation-type: tm+mt
source-git-commit: 269facfb6351b0b7c73e963ac7c5dc0b57c78a3e
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 1%

---


# Utilizzo di adattatori Sling{#using-sling-adapters}

[](https://sling.apache.org) Slingoffer un  [Adapter ](https://sling.apache.org/site/adapters.html) trasforma in modo conveniente gli oggetti che implementano l&#39;interfaccia  [](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) Adaptable. Questa interfaccia fornisce un metodo generico [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) che tradurrà l&#39;oggetto nel tipo di classe passato come argomento.

Ad esempio, per tradurre un oggetto Resource in un oggetto Node corrispondente, è sufficiente eseguire le operazioni seguenti:

```java
Node node = resource.adaptTo(Node.class);
```

## Casi di utilizzo {#use-cases}

Esistono i seguenti casi di utilizzo:

* Ottenete oggetti specifici per l&#39;implementazione.

   Ad esempio, un&#39;implementazione basata su JCR dell&#39;interfaccia generica [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) fornisce l&#39;accesso al JCR sottostante [`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* Creazione di collegamenti per oggetti che richiedono il passaggio di oggetti contestuali interni.

   Ad esempio, l&#39;elemento [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) basato su JCR contiene un riferimento all&#39;elemento [`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html) della richiesta, che a sua volta è necessario per molti oggetti che funzioneranno in base alla sessione di richiesta, ad esempio [`PageManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) o [`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* Collegamento ai servizi.

   Un caso raro - `sling.getService()` è anche semplice.

### Valore restituito Null {#null-return-value}

`adaptTo()` può restituire null.

I motivi di tale scelta sono diversi, tra cui:

* l&#39;implementazione non supporta il tipo di destinazione
* un gestore di schede che gestisce questo caso non è attivo (ad esempio a causa di riferimenti di servizio mancanti)
* condizione interna non riuscita
* il servizio non è disponibile

È importante gestire il caso nullo in modo corretto. Per i rendering jsp potrebbe essere accettabile che il jsp non riesca se si traduce in una parte vuota del contenuto.

### Cache {#caching}

Per migliorare le prestazioni, le implementazioni possono memorizzare nella cache l&#39;oggetto restituito da una chiamata `obj.adaptTo()`. Se `obj` è lo stesso, l&#39;oggetto restituito è lo stesso.

Questa memorizzazione nella cache viene eseguita per tutti i casi basati su `AdapterFactory`.

Tuttavia, non esiste una regola generale: l&#39;oggetto potrebbe essere una nuova istanza o una esistente. Ciò significa che non potete fare affidamento su entrambi i comportamenti. È quindi importante, soprattutto all&#39;interno di `AdapterFactory`, che gli oggetti siano riutilizzabili in questo scenario.

### Come funziona {#how-it-works}

Esistono diversi modi in cui `Adaptable.adaptTo()` può essere implementato:

* dall&#39;oggetto stesso; implementazione del metodo stesso e mappatura a determinati oggetti.
* Tramite un elemento [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)`, che può mappare oggetti arbitrari.

   Gli oggetti devono comunque implementare l&#39;interfaccia `Adaptable` ed estendere [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (che trasmette la chiamata `adaptTo` a un gestore di adattatori centrali).

   Questo consente di inserire i ganci nel meccanismo `adaptTo` per le classi esistenti, ad esempio `Resource`.

* Una combinazione di entrambi.

Per il primo caso, javadocs può indicare quali `adaptTo-targets` sono possibili. Tuttavia, per sottoclassi specifiche come la risorsa basata su JCR, spesso ciò non è possibile. In quest&#39;ultimo caso, le implementazioni di `AdapterFactory` fanno generalmente parte delle classi private di un bundle e quindi non sono esposte in un&#39;API client, né sono elencate in javadocs. In teoria, sarebbe possibile accedere a tutte le `AdapterFactory` implementazioni dal runtime di [OSGi](/help/sites-deploying/configuring-osgi.md) servizio e vedere le relative configurazioni &quot;adaptables&quot; (origini e destinazioni), ma non mapparle l&#39;una sull&#39;altra. Alla fine, questo dipende dalla logica interna, che deve essere documentata. Di qui il riferimento.

## Riferimento {#reference}

### Sling {#sling}

[**Adattamento**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) risorsa a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td> 
   <td>Se si tratta di una risorsa basata su nodo JCR o di una proprietà JCR che fa riferimento a un nodo.</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Proprietà</a></td> 
   <td>Se si tratta di una risorsa basata su proprietà JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Elemento</a></td> 
   <td>Se si tratta di una risorsa basata su JCR (nodo o proprietà).</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">Mappa</a></td> 
   <td>Restituisce una mappa delle proprietà, se si tratta di una risorsa basata su nodo JCR (o di altre mappe dei valori di supporto delle risorse).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>Restituisce una mappa pratica delle proprietà, se si tratta di una risorsa basata su nodo JCR (o di altre mappe di valore di supporto delle risorse). Può essere anche ottenuto (più semplicemente) utilizzando <br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (gestisce maiuscole/minuscole, ecc.).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">EreditanceValueMap</a></td> 
   <td>Estensione di <a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> che consente di tenere conto della gerarchia delle risorse nella ricerca delle proprietà.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersistableValueMap</a></td> 
   <td>Se si tratta di una risorsa basata su nodo JCR e l'utente dispone delle autorizzazioni necessarie per modificare le proprietà su tale nodo.<br /> Nota: più mappe persistenti non condividono i loro valori.</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td> 
   <td>Restituisce il contenuto binario di un "file"<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[**ResourceResolverts si adatta a:**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) 

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sessione</a></td> 
   <td>La sessione JCR della richiesta, se si tratta di un risolutore di risorse basato su JCR (predefinito).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td> 
   <td>In base alla sessione JCR, se si tratta di un risolutore di risorse basato su JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td> 
   <td>In base alla sessione JCR, se si tratta di un risolutore di risorse basato su JCR.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td> 
   <td>In base alla sessione JCR, se si tratta di un risolutore di risorse basato su JCR e se l'utente dispone delle autorizzazioni per accedere a UserManager.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Autorizzabile</a> </td> 
   <td>L’utente corrente.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">User</a><br /> </td> 
   <td>L’utente corrente.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/privileges/PrivilegeManager.html">PrivilegeManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/Preferences.html">Preferenze</a></td> 
   <td>Preferenze dell’utente corrente (basate sulla sessione JCR, se si tratta di un risolutore di risorse basato su JCR).</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/PreferencesService.html">PreferencesService</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/auth/pin/PinManager.html">PinManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">Externalizer</a></td> 
   <td>Per esternalizzare gli URL assoluti, anche con l'oggetto di richiesta.<br /> </td> 
  </tr> 
 </tbody> 
</table>

[**SlingHttpServletRequests si adatta a:**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) 

Nessuna destinazione ancora, ma implementa Adattabile e potrebbe essere utilizzato come origine in un AdapterFactory personalizzato.

[**SlingHttpServletResponsesi adatta a:**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) 

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td> 
   <td>Se si tratta di una risposta sling rewriter.</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[**Pageadts**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) si adatta a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Risorsa</a><br /> </td> 
   <td>Risorsa della pagina.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td> 
   <td>Risorsa con etichetta (== this).</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td> 
   <td>Nodo della pagina.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>Tutto ciò a cui è possibile adattare la risorsa della pagina.</td> 
  </tr> 
 </tbody> 
</table>

[****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) Componenti si adattano a:

| [Risorsa](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Risorsa del componente. |
|---|---|
| [LabeledResource](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Risorsa con etichetta (== this). |
| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo del componente. |
| ... | Tutto ciò a cui la risorsa del componente può essere adattata. |

[**Modello**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) adattabile a:

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Risorsa</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>Risorsa del modello.</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td> 
   <td>Risorsa con etichetta (== this).</td> 
  </tr> 
  <tr> 
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td> 
   <td>Nodo di questo modello.</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>Tutto ciò a cui può essere adattata la risorsa del modello.</td> 
  </tr> 
 </tbody> 
</table>

#### Sicurezza {#security}

[**Autorizzabili**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html),  [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) utenti e  [****](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) gruppi di utenti possono:

| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Restituisce il nodo principale utente/gruppo. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Restituisce lo stato di replica per il nodo principale utente/gruppo. |

#### DAM {#dam}

[**Le**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) risorse si adattano a:

| [Risorsa](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Risorsa della risorsa. |
|---|---|
| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo della risorsa. |
| ... | Tutto ciò a cui la risorsa della risorsa può essere adattata. |

#### Assegnazione tag {#tagging}

[**I**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) tag si adattano a:

| [Risorsa](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Risorsa del tag. |
|---|---|
| [Node](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nodo del tag. |
| ... | Tutto ciò a cui la risorsa del tag può essere adattata. |

#### Altro {#other}

Inoltre Sling / JCR / OCM fornisce un ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` per gli oggetti OCM personalizzati ([Object Content Mapping](https://jackrabbit.apache.org/object-content-mapping.html)).
