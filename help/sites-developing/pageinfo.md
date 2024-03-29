---
title: Ottenimento di informazioni di pagina in formato JSON
seo-title: Obtaining Page Information in JSON Format
description: Per ottenere le informazioni sulla pagina, invia una richiesta al servlet PageInfo per ottenere i metadati della pagina in formato JSON
seo-description: To obtain the page information, send a request to the PageInfo servlet to obtain the page metadata in JSON format
uuid: fb4f56b9-55e2-4622-a0d1-a86d6f2cce86
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 505bf3e3-ce3c-40aa-9619-e1b9f6634deb
exl-id: 5057b3d6-bf0c-4bb2-9085-f9add3f1c716
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 3%

---

# Ottenimento di informazioni di pagina in formato JSON{#obtaining-page-information-in-json-format}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per ottenere le informazioni sulla pagina, invia una richiesta al servlet PageInfo per ottenere i metadati della pagina in formato JSON.

Il servlet PageInfo restituisce informazioni sulle risorse nell&#39;archivio. Il servlet è associato all’URL `https://<server>:<port>/libs/wcm/core/content/pageinfo.json` e utilizza `path` per identificare la risorsa. L’URL di esempio seguente restituisce informazioni sul `/content/we-retail/us/en` nodo:

```shell
http://localhost:4502/libs/wcm/core/content/pageinfo.json?path=/content/we-retail/us/en
```

>[!NOTE]
>
>Se hai bisogno di informazioni di pagina in formato JSON per fornire la consegna di contenuto a canali che non sono pagine web AEM tradizionali, come:
>
>* Applicazioni a pagina singola
>* Applicazioni mobile native
>* Altri canali e punti di contatto esterni a AEM
>
>Vedere il documento [Esportatore JSON per Content Services](/help/sites-developing/json-exporter.md).

## Fornitori di informazioni sulle pagine {#page-information-providers}

I componenti della pagina possono essere associati a uno o più `com.day.cq.wcm.api.PageInfoProvider` servizi che generano metadati pagina. Il servlet PageInfo chiama ogni servizio PageInfoProvider e aggrega i metadati:

1. Il client HTTP invia una richiesta al servlet PageInfo, che include l’URL della pagina.
1. Il servlet PageInfo individua il componente che esegue il rendering della pagina.
1. Il servlet PageInfo chiama ogni PageInfoProvider associato al componente.
1. Il servlet aggrega i metadati restituiti da ogni PageInfoProvider e aggiunge i metadati alla risposta HTTP in un oggetto JSON.

![chlimage_1-2](assets/chlimage_1-2.png)

>[!NOTE]
>
>Analogamente a PageInfoProviders, utilizza ListInfoProviders per aggiornare elenchi di informazioni in formato JSON. (Vedi [Personalizzazione della console di amministrazione dei siti web](/help/sites-developing/customizing-siteadmin.md).)

## Provider di informazioni di pagina predefiniti {#default-page-information-providers}

La `/libs/foundation/components/page` Il componente è associato ai seguenti servizi PageInfoProvider:

* **Provider di stato pagina predefinito:** Informazioni sullo stato della pagina, ad esempio se è bloccata, se la pagina è il payload di un flusso di lavoro attivo e quali flussi di lavoro sono disponibili per la pagina.
* **Provider di informazioni sulle relazioni live:** Informazioni relative a Gestione multisito (MSM), ad esempio se la pagina fa parte di una Stampa blu e se si tratta di una Live Copy.
* **Servlet lingua contenuto:** Lingua della pagina corrente e informazioni su ogni lingua in cui la pagina è disponibile.
* **Provider di stato del flusso di lavoro:** Informazioni di stato sul flusso di lavoro in esecuzione con la pagina come payload.
* **Provider informazioni pacchetto flusso di lavoro:** Informazioni su ciascun pacchetto del flusso di lavoro memorizzato nell’archivio e se ogni pacchetto contiene la risorsa corrente.
* **Provider di informazioni sull&#39;emulatore:** Informazioni sugli emulatori dei dispositivi mobili disponibili per questa risorsa. Se il componente pagina non esegue il rendering delle pagine mobili, non sono disponibili emulatori.
* **Provider informazioni annotazioni:** Informazioni sulle annotazioni presenti nella pagina.

Ad esempio, il servlet PageInfo restituisce la seguente risposta JSON per `/content/we-retail/us/en` nodo:

```
{
   "status":{
      "path":"/content/we-retail/us/en",
      "isLocked":false,
      "lockOwner":"",
      "canUnlock":false,
      "lastModified":1467202845038,
      "lastModifiedBy":"admin",
      "timeUntilValid":0,
      "onTime":0,
      "offTime":0,
      "replication":{
         "numQueued":0
      },
      "isDesignable":true,
      "isDeveloper":true
   },
   "isPage":true,
   "pageResourceType":"weretail/components/structure/page",
   "enableFragmentIdentifier":false,
   "workflow":{
      "isRunning":false
   },
   "workflows":{
      "wcm":{
         "models":[
            {
               "wid":"/etc/workflow/models/dam/adddamsize/jcr:content/model",
               "label":"Add Asset Size",
               "label_xss":"Add Asset Size"
            },
            {
               "wid":"/etc/workflow/models/ac-newsletter-workflow-simple/jcr:content/model",
               "label":"Approve for Adobe Campaign",
               "label_xss":"Approve for Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/dam/dam-autotag-assets/jcr:content/model",
               "label":"DAM Smart Tag Assets",
               "label_xss":"DAM Smart Tag Assets"
            },
            {
               "wid":"/etc/workflow/models/dam/update_asset/jcr:content/model",
               "label":"DAM Update Asset",
               "label_xss":"DAM Update Asset"
            },
            {
               "wid":"/etc/workflow/models/cloudservices/DTM_bundle_download/jcr:content/model",
               "label":"Default DTM Bundle Download",
               "label_xss":"Default DTM Bundle Download"
            },
            {
               "wid":"/etc/workflow/models/dam/dam_download_asset/jcr:content/model",
               "label":"Download Asset",
               "label_xss":"Download Asset"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-thumbnail-replacement/jcr:content/model",
               "label":"Dynamic Media Video Thumbnail Replacement",
               "label_xss":"Dynamic Media Video Thumbnail Replacement"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail/jcr:content/model",
               "label":"Dynamic Media Video User Uploaded Thumbnail Process",
               "label_xss":"Dynamic Media Video User Uploaded Thumbnail Process"
            },
            {
               "wid":"/etc/workflow/models/projects/approval_workflow/jcr:content/model",
               "label":"Project Approval Workflow",
               "label_xss":"Project Approval Workflow"
            },
            {
               "wid":"/etc/workflow/models/publish_example/jcr:content/model",
               "label":"Publish Example",
               "label_xss":"Publish Example"
            },
            {
               "wid":"/etc/workflow/models/publish_to_campaign/jcr:content/model",
               "label":"Publish to Adobe Campaign",
               "label_xss":"Publish to Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_publish_to_youtube/jcr:content/model",
               "label":"Publish to YouTube",
               "label_xss":"Publish to YouTube"
            },
            {
               "wid":"/etc/workflow/models/projects/request_copy/jcr:content/model",
               "label":"Request Copy",
               "label_xss":"Request Copy"
            },
            {
               "wid":"/etc/workflow/models/request_for_activation/jcr:content/model",
               "label":"Request for Activation",
               "label_xss":"Request for Activation"
            },
            {
               "wid":"/etc/workflow/models/request_for_deactivation/jcr:content/model",
               "label":"Request for Deactivation",
               "label_xss":"Request for Deactivation"
            },
            {
               "wid":"/etc/workflow/models/request_for_deletion/jcr:content/model",
               "label":"Request for Deletion",
               "label_xss":"Request for Deletion"
            },
            {
               "wid":"/etc/workflow/models/request_to_complete_move_operation/jcr:content/model",
               "label":"Request to complete Move operation",
               "label_xss":"Request to complete Move operation"
            },
            {
               "wid":"/etc/workflow/models/screens-update-asset/jcr:content/model",
               "label":"Screens Update Asset",
               "label_xss":"Screens Update Asset"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_remove_from_youtube/jcr:content/model",
               "label":"Unpublish from YouTube",
               "label_xss":"Unpublish from YouTube"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/create_language_copy/jcr:content/model",
               "label":"WCM: Create Language Copy",
               "label_xss":"WCM: Create Language Copy"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/prepare_translation_project/jcr:content/model",
               "label":"WCM: Prepare Translation Project",
               "label_xss":"WCM: Prepare Translation Project"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/translate-i18n-dictionary/jcr:content/model",
               "label":"WCM: Prepare and Translate I18n-Dictionary",
               "label_xss":"WCM: Prepare and Translate I18n-Dictionary"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/sync_translation_job/jcr:content/model",
               "label":"WCM: Sync Translation Job",
               "label_xss":"WCM: Sync Translation Job"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/update_language_copy/jcr:content/model",
               "label":"WCM: Update Language Copy",
               "label_xss":"WCM: Update Language Copy"
            }
         ]
      },
      "translation":{
         "models":[
            {
               "wid":"/etc/workflow/models/dam/adddamsize/jcr:content/model",
               "label":"Add Asset Size",
               "label_xss":"Add Asset Size"
            },
            {
               "wid":"/etc/workflow/models/ac-newsletter-workflow-simple/jcr:content/model",
               "label":"Approve for Adobe Campaign",
               "label_xss":"Approve for Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/dam/dam-autotag-assets/jcr:content/model",
               "label":"DAM Smart Tag Assets",
               "label_xss":"DAM Smart Tag Assets"
            },
            {
               "wid":"/etc/workflow/models/cloudservices/DTM_bundle_download/jcr:content/model",
               "label":"Default DTM Bundle Download",
               "label_xss":"Default DTM Bundle Download"
            },
            {
               "wid":"/etc/workflow/models/dam/dam_download_asset/jcr:content/model",
               "label":"Download Asset",
               "label_xss":"Download Asset"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-thumbnail-replacement/jcr:content/model",
               "label":"Dynamic Media Video Thumbnail Replacement",
               "label_xss":"Dynamic Media Video Thumbnail Replacement"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail/jcr:content/model",
               "label":"Dynamic Media Video User Uploaded Thumbnail Process",
               "label_xss":"Dynamic Media Video User Uploaded Thumbnail Process"
            },
            {
               "wid":"/etc/workflow/models/projects/approval_workflow/jcr:content/model",
               "label":"Project Approval Workflow",
               "label_xss":"Project Approval Workflow"
            },
            {
               "wid":"/etc/workflow/models/publish_to_campaign/jcr:content/model",
               "label":"Publish to Adobe Campaign",
               "label_xss":"Publish to Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_publish_to_youtube/jcr:content/model",
               "label":"Publish to YouTube",
               "label_xss":"Publish to YouTube"
            },
            {
               "wid":"/etc/workflow/models/projects/request_copy/jcr:content/model",
               "label":"Request Copy",
               "label_xss":"Request Copy"
            },
            {
               "wid":"/etc/workflow/models/request_for_deletion/jcr:content/model",
               "label":"Request for Deletion",
               "label_xss":"Request for Deletion"
            },
            {
               "wid":"/etc/workflow/models/request_to_complete_move_operation/jcr:content/model",
               "label":"Request to complete Move operation",
               "label_xss":"Request to complete Move operation"
            },
            {
               "wid":"/etc/workflow/models/screens-update-asset/jcr:content/model",
               "label":"Screens Update Asset",
               "label_xss":"Screens Update Asset"
            },
            {
               "wid":"/etc/workflow/models/translation/jcr:content/model",
               "label":"Translation Prepare",
               "label_xss":"Translation Prepare"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_remove_from_youtube/jcr:content/model",
               "label":"Unpublish from YouTube",
               "label_xss":"Unpublish from YouTube"
            }
         ]
      }
   },
   "translation":{

   },
   "design":{
      "path":"/conf/we-retail/settings/wcm/templates/hero-page/policies",
      "lastModified":0
   },
   "componentsRef":"/libs/wcm/core/content/components.1497341312569.json",
   "editableTemplate":"/conf/we-retail/settings/wcm/templates/hero-page",
   "msm":{
      "msm:isLiveCopy":true,
      "msm:isInBlueprint":false,
      "msm:isSource":false
   },
   "launches":{
      "isLaunch":false,
      "isInLaunch":false
   },
   "language":"en",
   "languages":{
      "rows":[
         {
            "path":"/content/we-retail/us/en",
            "exists":true,
            "hasContent":true,
            "lastModified":0,
            "iso":"en",
            "country":"gb",
            "language":"English"
         },
         {
            "path":"/content/we-retail/us/es",
            "exists":true,
            "hasContent":true,
            "lastModified":0,
            "iso":"es",
            "country":"es",
            "language":"Spanish"
         }
      ]
   },
   "workflowInfo":{
      "isRunning":false
   },
   "workflowPackageInfo":{
      "workflowPackages":[

      ],
      "selectedWorkflowPackages":[

      ],
      "runningSelectedWorkflowPackages":[

      ]
   },
   "emulators":{
      "groups":{
         "responsive":{
            "title":"Responsive Devices",
            "description":"The devices in this group are able to display a website built using responsive design patterns.",
            "path":"/etc/mobile/groups/responsive",
            "galaxy5":{
               "text":"Galaxy S5",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/galaxy5",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":1080,
               "height":1920,
               "device-pixel-ratio":3
            },
            "ipad":{
               "text":"iPad",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/ipad",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":768,
               "height":1024,
               "device-pixel-ratio":1
            },
            "iphone5":{
               "text":"iPhone 5",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone5",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":640,
               "height":1136,
               "device-pixel-ratio":2
            },
            "iphone6":{
               "text":"iPhone 6",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone6",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":750,
               "height":1334,
               "device-pixel-ratio":2
            },
            "iphone4":{
               "text":"iPhone 4",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone4",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":640,
               "height":960,
               "device-pixel-ratio":2
            },
            "iphone6plus":{
               "text":"iPhone 6 Plus",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone6plus",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":1080,
               "height":1920,
               "device-pixel-ratio":2.6
            },
            "nexuss":{
               "text":"Nexus S",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/nexuss",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":320,
               "height":533,
               "device-pixel-ratio":1
            }
         }
      }
   },
   "annotations":[

   ],
   "permissions":{
      "modify":true,
      "replicate":true,
      "read":true,
      "create":true,
      "delete":true,
      "acl_read":true,
      "acl_edit":true
   },
   "isTargetable":"true",
   "responsive":{
      "breakpoints":{
         "phone":{
            "width":650,
            "title":"Smaller Screen"
         },
         "tablet":{
            "width":1200,
            "title":"Tablet"
         }
      }
   }
}
```

## Filtrare le informazioni sul pacchetto del flusso di lavoro {#filtering-workflow-package-information}

Configura il servizio Day CQ WCM Workflow Package Info Provider in modo che restituisca informazioni solo sui pacchetti del flusso di lavoro in cui sei interessato. Per impostazione predefinita, il servizio Informazioni pacchetto flusso di lavoro restituisce informazioni su ogni pacchetto di flusso di lavoro nel repository. L&#39;iterazione su un sottoinsieme di pacchetti di flusso di lavoro utilizza meno risorse server.

>[!NOTE]
>
>La scheda Flusso di lavoro nella barra laterale utilizza il servlet PageInfo per ottenere un elenco di pacchetti di flussi di lavoro. Dall’elenco, puoi selezionare il pacchetto a cui aggiungere la pagina corrente. I filtri creati influiscono su questo elenco.

L&#39;ID del servizio è `com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider`. Per creare un filtro, specificare un valore per un `workflowpackageinfoprovider.filter` proprietà.

I valori delle proprietà hanno il prefisso + o - seguito dal percorso del pacchetto:

* Il percorso è il percorso del nodo principale del pacchetto del flusso di lavoro. Il percorso utilizza la sintassi FileVault.
* Per includere un pacchetto, utilizza il prefisso + .
* Per escludere un pacchetto, utilizza il prefisso - .

Il servizio applica il risultato cumulativo di tutti i filtri. Ad esempio, i seguenti valori di filtro escludono tutti i pacchetti del flusso di lavoro eccetto quelli presenti nella cartella Editions:

```
-/etc/workflow/packages(/.*)?
+/etc/workflow/packages/Editions(/.&ast;)?
```

>[!NOTE]
>
>Quando si lavora con AEM esistono diversi metodi per gestire le impostazioni di configurazione per tali servizi. Vedi [Configurazione di OSGi](/help/sites-deploying/configuring-osgi.md) per informazioni complete.

Ad esempio, per configurare il servizio utilizzando CRXDE Lite:

1. Apri CRXDE Lite ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Nella cartella di configurazione dell&#39;applicazione, crea un nodo:

   * Nome: `com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider`
   * Tipo: `sling:OsgiConfig`

1. Seleziona il nodo e aggiungi una proprietà:

   * Nome: `workflowpackageinfoprovider.filter`
   * Tipo: `String[]`
   * Valore: Il percorso del pacchetto del flusso di lavoro utilizzando il formato corretto.

1. Fai clic su Salva tutto.

Per configurare il servizio nell’origine del progetto:

1. Individua o crea la cartella di configurazione per l&#39;applicazione AEM nell&#39;origine del progetto.

   Ad esempio, se per creare il progetto hai utilizzato l’archetipo multimodulo del plugin Content Package Maven, il percorso della cartella è `<projectroot>/content/src/ for example content/src/main/content/jcr_root/apps/<appname>/config`.
1. Nella cartella di configurazione, crea un file di testo denominato com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider.xml
1. Copia nel file il seguente testo:

   ```
   <?xml version="1.0" encoding="UTF-8"?> 
    <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" 
    xmlns:jcr="https://www.jcp.org/jcr/1.0" 
    jcr:primaryType="sling:OsgiConfig" 
    workflowpackageinfoprovider.filter="[]"/>
   ```

1. All&#39;interno delle staffe (`[]`) che circondano `workflowpackageinfoprovider.filter` digitare un elenco di valori di filtro separati da virgole, simile all&#39;esempio seguente:

   `workflowpackageinfoprovider.filter="[-/etc/workflow/packages(/.*)?,+/etc/workflow/packages/Editions(/.*)?]"/>`

1. Salva il file.

## Creazione di un provider di informazioni di pagina {#creating-a-page-information-provider}

Crea un servizio di provider di informazioni sulle pagine personalizzato per aggiungere metadati alle pagine facilmente ottenibili dall’applicazione.

1. Implementa l’interfaccia `com.day.cq.wcm.api.PageInfoProvider`. 
1. Esegui il bundle e implementa la classe come servizio OSGi.
1. Crea un componente pagina nell’applicazione. Utilizzo `foundation/components/page` come valore del `sling:resourceSuperType` proprietà.

1. Aggiungi un nodo sotto il nodo del componente denominato `cq:infoProviders`.
1. Sotto la `cq:infoProviders` aggiungi un nodo per il servizio PageInfoProvider. Puoi specificare un nome qualsiasi per il nodo.
1. Aggiungi la seguente proprietà al nodo PageInfoProvider:

   * Nome: className
   * Tipo: Stringa
   * Valore: PID del servizio PageInfoProvider.

Per le risorse che utilizzano il componente pagina dell’applicazione come `sling:resourceType`, il servlet PageInfo restituisce i metadati PageInfoProvider personalizzati oltre ai metadati PageInfoProvider predefiniti.

### Esempio di implementazione di PageInfoProvider {#example-pageinfoprovider-implementation}

La seguente classe Java viene implementata [PageInfoProvider](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html) e restituisce l&#39;URL pubblicato della risorsa pagina corrente.

```java
package com.adobe.example;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.ReferenceCardinality;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;

import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;

import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;

import com.day.cq.wcm.api.Page;
import com.day.cq.wcm.api.PageInfoProvider;

@Component(metatype = false)
@Properties({
 @Property(name="service.description", value="Returns the public URL of a resource.")
})
@Service
public class PageUrlInfoProvider implements PageInfoProvider {

 @Reference(cardinality = ReferenceCardinality.OPTIONAL_UNARY)
 private com.day.cq.commons.Externalizer externalizer;

 private String fetchExternalUrl(ResourceResolver rr, String path) {
  return externalizer.publishLink(rr, path);
 }

 public void updatePageInfo(SlingHttpServletRequest request, JSONObject info, Resource resource)
   throws JSONException {

  Page page = resource.adaptTo(Page.class);
  JSONObject urlinfo = new JSONObject();
  urlinfo.put("publishURL", fetchExternalUrl(null,page.getPath()));
  info.put("URLs",urlinfo);
 }
}
```

L’esempio seguente, in CRXDE Lite, mostra il componente pagina configurato per l’utilizzo del servizio PageUrlInfoProvider:

![chlimage_1-3](assets/chlimage_1-3.png)

Il servizio PageUrlInfoProvider restituisce i dati seguenti per il `/content/we-retail/us/en` nodo:

```xml
"URLs": {
    "publishURL": "http://localhost:4503/content/we-retail/us/en"
}
```
