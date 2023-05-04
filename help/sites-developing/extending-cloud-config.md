---
title: Configurazioni Cloud Service
description: Puoi estendere le istanze esistenti per creare configurazioni personalizzate.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
exl-id: d2b8503e-8ac1-4617-ad76-b05d1e80a6b6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 5%

---

# Configurazioni Cloud Service{#cloud-service-configurations}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le configurazioni sono progettate per fornire la logica e la struttura per l’archiviazione delle configurazioni del servizio.

Puoi estendere le istanze esistenti per creare configurazioni personalizzate.

## Concetti {#concepts}

I principi utilizzati nello sviluppo delle configurazioni sono stati basati sui seguenti concetti:

* I servizi/adattatori vengono utilizzati per recuperare le configurazioni.
* Le configurazioni (ad esempio proprietà/paragrafi) sono ereditate dalle padre.
* A cui si fa riferimento dai nodi di analisi per percorso.
* Facilmente estensibile.
* Dispone della flessibilità necessaria per gestire configurazioni più complesse, come [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* Supporto delle dipendenze (ad esempio [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) i plugin hanno bisogno di un [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) configurazione).

## Struttura {#structure}

Il percorso di base delle configurazioni è:

`/etc/cloudservices`.

Per ogni tipo di configurazione verranno forniti un modello e un componente, che consentono di disporre di modelli di configurazione in grado di soddisfare le esigenze più specifiche dopo la personalizzazione.

Per fornire una configurazione per un nuovo servizio è necessario:

* creare una pagina di servizio in

   `/etc/cloudservices`

* in questo caso:

   * un modello di configurazione
   * un componente di configurazione

Il modello e il componente devono ereditare il `sling:resourceSuperType` dal modello di base:

`cq/cloudserviceconfigs/templates/configpage`

o componente di base

`cq/cloudserviceconfigs/components/configpage`

Il fornitore di servizi deve inoltre fornire la pagina del servizio:

`/etc/cloudservices/<service-name>`

### Modello {#template}

Il modello estenderà il modello di base:

`cq/cloudserviceconfigs/templates/configpage`

e definire un `resourceType` che punta al componente personalizzato.

```xml
/libs/cq/analytics/templates/sitecatalyst
sling:resourceSuperType = cq/cloudserviceconfigs/templates/configpage
allowedChildren = /libs/cq/analytics/templates/sitecatalyst
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
componentReference = cq/analytics/components/sitecatalyst
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/sitecatalystpage

/libs/cq/analytics/templates/generictracker
sling:resourceSuperType = cq/cloudservices/templates/configpage
allowedChildren = /libs/cq/analytics/templates/generictracker
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/generictrackerpage
```

### Componenti {#components}

Il componente deve estendere il componente di base:

`cq/cloudserviceconfigs/templates/configpage`

```xml
/libs/cq/analytics/components/sitecatalystpage

/libs/cq/analytics/components/generictrackerpage
```

Dopo aver impostato il modello e il componente, puoi aggiungere la configurazione aggiungendo le sottopagine in:

`/etc/cloudservices/<service-name>`

### Modello di contenuto {#content-model}

Il modello di contenuto viene memorizzato come `cq:Page` in:

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

Le configurazioni sono memorizzate sotto il sottonodo `jcr:content`.

* Le proprietà fisse, definite in una finestra di dialogo, devono essere memorizzate in `jcr:node` direttamente.
* Elementi dinamici (utilizzando `parsys` o `iparsys`) utilizza un sottonodo per memorizzare i dati del componente.

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

Per la documentazione di riferimento sull&#39;API consulta [com.day.cq.wcm.webservicesupport](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### Integrazione AEM {#aem-integration}

I servizi disponibili sono elencati nella sezione **Cloud Services** della scheda **Proprietà pagina** finestra di dialogo (di qualsiasi pagina che eredita da `foundation/components/page` o `wcm/mobile/components/page`).

La scheda fornisce inoltre:

* un collegamento alla posizione in cui è possibile abilitare il servizio
* scegli una configurazione (sottonodo del servizio) da un campo percorso

#### Crittografia della password {#password-encryption}

Quando si memorizzano le credenziali utente per il servizio, tutte le password devono essere crittografate.

A tal fine, è possibile aggiungere un campo modulo nascosto. Questo campo deve contenere l’annotazione `@Encrypted` nel nome della proprietà; vale a dire per `password` il nome viene scritto come segue:

`password@Encrypted`

La proprietà viene quindi crittografata automaticamente (utilizzando `CryptoSupport` dal `EncryptionPostProcessor`.

>[!NOTE]
>
>È simile allo standard ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)` annotazioni.

>[!NOTE]
>
>Per impostazione predefinita, `EcryptionPostProcessor` crittografa solo `POST` richieste presentate `/etc/cloudservices`.

#### Proprietà aggiuntive per i nodi jcr:content della pagina del servizio {#additional-properties-for-service-page-jcr-content-nodes}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Proprietà</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>componentReference</td> 
   <td>Percorso di riferimento per un componente da includere automaticamente nella pagina.<br /> Viene utilizzato per funzionalità aggiuntive e inclusioni JS.<br /> Questo include il componente nella pagina in cui<br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> è incluso (normalmente prima del <code>body</code> tag).<br /> Nel caso di Analytics e Target, lo utilizziamo per includere funzionalità aggiuntive, come le chiamate JavaScript per tenere traccia del comportamento dei visitatori.</td> 
  </tr> 
  <tr> 
   <td>descrizione</td> 
   <td>Breve descrizione del servizio.<br /> </td> 
  </tr> 
  <tr> 
   <td>descriptionExtended</td> 
   <td>Descrizione estesa del servizio.</td> 
  </tr> 
  <tr> 
   <td>classificazione</td> 
   <td>Classificazione del servizio da utilizzare negli elenchi.</td> 
  </tr> 
  <tr> 
   <td>selectableChildren</td> 
   <td>Filtro per la visualizzazione delle configurazioni nella finestra di dialogo delle proprietà della pagina.</td> 
  </tr> 
  <tr> 
   <td>serviceUrl</td> 
   <td>URL del sito web del servizio.</td> 
  </tr> 
  <tr> 
   <td>serviceUrlLabel</td> 
   <td>Etichetta per l’URL del servizio.</td> 
  </tr> 
  <tr> 
   <td>thumbnailPath</td> 
   <td>Percorso della miniatura del servizio.</td> 
  </tr> 
  <tr> 
   <td>visibile</td> 
   <td>Visibilità nella finestra di dialogo delle proprietà della pagina; visibile per impostazione predefinita (facoltativo)</td> 
  </tr> 
 </tbody> 
</table>

### Casi d&#39;uso {#use-cases}

Questi servizi sono forniti per impostazione predefinita:

* [Frammenti di tracciamento](/help/sites-administering/external-providers.md) (Google, WebTrends, ecc.)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [Test&amp;Target](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Vedi anche [Creazione di un Cloud Service personalizzato](/help/sites-developing/extending-cloud-config-custom-cloud.md).
