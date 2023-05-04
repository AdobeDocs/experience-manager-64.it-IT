---
title: Configurazione di Dispatcher per Communities
seo-title: Configuring Dispatcher for Communities
description: Configurare il dispatcher per AEM Communities
seo-description: Configure the dispatcher for AEM Communities
uuid: c17daca9-3244-4b10-9d4e-2e95df633dd9
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 23745dd3-1424-4d22-8456-d2dbd42467f4
exl-id: dc4e27dd-fb2e-485d-8c7f-ab830bde1d3d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Configurazione di Dispatcher per Communities {#configuring-dispatcher-for-communities}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Community AEM {#aem-communities}

Per AEM Communities, è necessario configurare il Dispatcher per garantire il corretto funzionamento di [siti della community](overview.md#community-sites). Sono necessarie configurazioni aggiuntive quando si includono funzionalità quali l’abilitazione di Communities e l’accesso social.

Per scoprire cosa è necessario per una particolare implementazione e progettazione del sito

* Contatta il [Servizio clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html)

Vedi anche il [Documentazione di Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html).

## Memorizzazione in cache del dispatcher {#dispatcher-caching}

### Panoramica {#overview}

Il caching del dispatcher per AEM Communities è la capacità del dispatcher di servire versioni completamente memorizzate nella cache delle pagine di un sito community.

Attualmente, è supportato solo per i visitatori anonimi del sito, ad esempio gli utenti che navigano sul sito community o che accedono a una pagina della community in seguito a una ricerca, nonché per i motori di ricerca che indicizzano le pagine. Il vantaggio è che gli utenti anonimi e i motori di ricerca avranno prestazioni migliori.

Per i membri con accesso, il dispatcher bypassa la cache, inoltrando le richieste direttamente all’editore, in modo che tutte le pagine vengano generate e distribuite in modo dinamico.

Quando è configurato per supportare il caching del dispatcher, all’intestazione viene aggiunta una scadenza &quot;età massima&quot; basata su TTL per garantire che le pagine memorizzate nella cache del dispatcher siano correnti.

### Requisiti {#requirements}

* Dispatcher versione 4.1.2 o successiva (vedi [Installazione di Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html) per la versione più recente)
* [Pacchetto ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)

   * Versione 3.3.2 o successiva
   * `ACS AEM Commons - Dispatcher Cache Control Header - Max Age` Configurazione OSGi

### Configurazione {#configuration}

Configurazione OSGi **ACS AEM Commons - Intestazione di controllo cache del dispatcher - Età massima** imposta la scadenza delle pagine memorizzate nella cache che vengono visualizzate sotto un percorso specificato.

* Da [Console web](../../help/sites-deploying/configuring-osgi.md)

   * Ad esempio: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Individua `ACS AEM Commons - Dispatcher Cache Control Header - Max Age`
* Seleziona l’icona &quot;+&quot; per creare una nuova configurazione di connessione

![chlimage_1-339](assets/chlimage_1-339.png)

* **Pattern di filtro**

   *(obbligatorio)* Uno o più percorsi alle pagine della community. Esempio: `/content/sites/engage/(.*)`.

* **Cache-Control Max Age**

   *(obbligatorio)* L’età massima (in secondi) da aggiungere all’intestazione Controllo cache. Il valore deve essere maggiore di zero (0).

## Intestazioni client di Dispatcher {#dispatcher-client-headers}

Nella sezione /clientheaders di `dispatcher.any`, se elencare un set specifico di intestazioni, è necessario includere `"CSRF-Token"` per [Funzione di abilitazione](enablement.md) per funzionare correttamente.

## Filtri del Dispatcher {#dispatcher-filters}

La sezione /filter del `dispatcher.any` file documentato in [Configurazione dell&#39;accesso al contenuto - /filter](https://helpx.adobe.com/it/experience-manager/dispatcher/using/dispatcher-configuration.html#filter).

Questa sezione descrive le voci probabilmente necessarie per il corretto funzionamento delle funzioni di Communities.

I nomi delle proprietà del filtro seguono la convenzione relativa all&#39;utilizzo di un numero di quattro cifre per indicare l&#39;ordine in cui applicare i pattern di filtro. Quando a una richiesta sono applicati più modelli di filtri, l’ultimo modello applicato è quello valido. Pertanto, il primo modello di filtro viene spesso utilizzato per negare tutto, in modo tale che i seguenti modelli servono a ripristinare l&#39;accesso in modo controllato.

Gli esempi seguenti utilizzano nomi di proprietà che probabilmente dovranno essere modificati per adattarsi a un particolare file dispatcher.any.

Consulta anche

* [Elenco di controllo della sicurezza del dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/security-checklist.html?lang=it#getting-started)

>[!NOTE]
>
>**Esempi di nomi di proprietà**
>Vengono visualizzati tutti i nomi delle proprietà, ad esempio **0050** e **0170**, deve essere regolato per adattarsi a un file di configurazione dispatcher.any esistente.

Le seguenti voci devono essere aggiunte alla fine della sezione /filter, soprattutto dopo tutte le voci non consentite.

```shell
# design and template assets

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0050 { /type "allow" /glob "GET /etc/designs/*" }

# collected JS/CSS from the components and design

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0051 { /type "allow" /glob "GET /etc/clientlibs/*" }

# foundation search component - write stats

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0052 { /type "allow" /glob "GET /bin/statistics/tracker/*" }

# allow users to edit profile page

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0054 { /type "allow" /glob "* /home/users/*/*/profile.form.html*" }

# all profile data

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0057 { /type "allow" /glob "GET /home/users/*/profile/*" }

# required for social "Sign In" link.

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0059 { /type "allow" /glob "GET /etc/clientcontext/*" }

# required for "Sign Out" operation

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0063 { /type "allow" /glob "* /system/sling/logout*" }

# enable Facebook and Twitter signin

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0064 { /type "allow" /glob "GET /etc/cloudservices/*" }

# enable personalization

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0062 { /type "allow" /url "/libs/cq/personalization/*" }

# for Enablement features

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0170 { /type "allow" /url "/libs/granite/csrf/token.json*" }
/0171 { /type "allow" /glob "POST /content/sites/*/resources/en/*" }
/0172 { /type "allow" /glob "GET /content/communities/enablement/reports/*" }
/0173 { /type "allow" /glob "GET /content/sites/*" }
/0174 { /type "allow" /glob "GET /content/communities/scorm/*" }
/0175 { /type "allow" /url "GET /content/sites/*" }
/0176 { /type "allow" /url "GET /libs/granite/security/userinfo.json"}
/0177 { /type "allow" /url "GET /libs/granite/security/currentuser.json" }

# Enable CSRF token otherwise nothings works.

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/5001 { /type "allow" /glob "GET /libs/granite/csrf/token.json *"}        
# Allow SCF User Model to bootstrap as it depends on the granite user

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/5002 { /type "allow" /glob "GET /libs/granite/security/currentuser.json*" }
   
# Allow Communities Site Logout button work

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/5003 { /type "allow" /glob "GET /system/sling/logout.html*" }
   
# Allow i18n to load correctly

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/5004 { /type "allow" /glob "GET /libs/cq/i18n/dict.en.json *" }

# Allow social json get pattern.

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/6002 { /type "allow" /glob "GET *.social.*.json*" }
   
# Allow loading of templates

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/6003 { /type "allow" /glob "GET /services/social/templates*" }
   
# Allow SCF User model to check moderator rules

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/6005 { /type "allow" /glob "GET /services/social/getLoggedInUser?moderatorCheck=*" }
   
# Allow CKEditor to load which uses a query pattern not sufficed by regular glob above.

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/6006 { /type "allow" /glob "GET /etc/clientlibs/social/thirdparty/ckeditor/*.js?t=*" }
/6007 { /type "allow" /glob "GET /etc/clientlibs/social/thirdparty/ckeditor/*.css?t=*" }
   
# Allow Fonts from Communities to load

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/6050 { /type "allow" /glob "GET *.woff *" }
/6051 { /type "allow" /glob "GET *.ttf *" }

# Enable CQ Security checkpoint for component guide.

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/7001 { /type "allow" /glob "GET /libs/cq/security/userinfo.json?cq_ck=*"
```

## Regole del Dispatcher {#dispatcher-rules}

La sezione Regole di `dispatcher.any` definisce le risposte da memorizzare nella cache in base all’URL richiesto. Per Communities, la sezione regole viene utilizzata per definire ciò che non deve essere mai memorizzato nella cache.

```shell
# Never cache the client-side .social.json calls

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0001 { /type "deny" /glob "*.social.json*" }

# Never cache the user-specific .json requests

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0002 { /type "deny" /glob "/libs/granite/csrf/token.json*" }
/0003 { /type "deny" /glob "/libs/granite/security/currentuser.json*" }
/0004 { /type "deny" /glob "/libs/granite/security/userinfo.json*" }

# Never cache the private community groups pages in case - add your own deny rules in there

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0005 { /type "deny" /glob "/content/*/groups/*" }

# Never cache the assignments page in case the Enablement feature is in use - add your own deny rules in there

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0006 { /type "deny" /glob "/content/*/assignments/*" }

# Never cache user generated content

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/0208 { /type "deny" /glob "/content/usergenerated/*" }
```

## Risoluzione dei problemi {#troubleshooting}

Una fonte principale di problemi è l&#39;inserimento di regole di filtro senza prestare attenzione all&#39;effetto sulle regole precedenti, soprattutto quando si aggiunge una regola per negare l&#39;accesso.

Il primo pattern di filtro viene spesso utilizzato per negare tutto, in modo che i filtri seguenti ripristinino l’accesso in modo controllato. Quando a una richiesta sono applicati più filtri, l’ultimo filtro applicato è quello effettivo.

## dispatcher di esempio.any {#sample-dispatcher-any}

Di seguito è riportato un esempio `dispatcher.any` file che include le regole /filters e /rules di Communities.

```shell
# Each farm configures a set of load balanced renders (i.e. remote servers)

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
/farms
  {
  # First farm entry
  /website 
    {  
    # Request headers that should be forwarded to the remote server.
    /clientheaders
      {
      # Forward all request headers that are end-to-end. If you want
      # to forward a specific set of headers, you'll have to list
      # them here.
      "*"
      }
      
    # Hostname globbing for farm selection (virtual domain addressing)
    /virtualhosts
      {
      # Entries will be compared against the "Host" request header
      # and an optional request URL prefix.
      #
      # Examples:
      #
      #   www.company.com
      #   intranet.*
      #   myhost:8888/mysite
      "*"
      }
      
    # The load will be balanced among these render instances
    /renders
      {
      /rend01
        {
        # Hostname or IP of the render
        /hostname "127.0.0.1"
        # Port of the render
        /port "4503"
        # Connect timeout in milliseconds, 0 to wait indefinitely
        # /timeout "0"
        }
      }
      
    # The filter section defines the requests that should be handled by the dispatcher.
    #
    # Entries can be either specified using globs, or elements of the request line:
    #
    # (1) globs will be compared against the entire request line, e.g.:
    #
    #     /0001 { /type "deny" /glob "* /index.html *" }
    #
    #   matches request "GET /index.html HTTP/1.1" but not "GET /index.html?a=b HTTP/1.1".
    #
    # (2) method/url/query/protocol will be compared againts the respective elements of
    #   the request line, e.g.:
    #
    #     /0001 { /type "deny" /method "GET" /url "/index.html" }
    #
    #   matches both "GET /index.html" and "GET /index.html?a=b HTTP/1.1".
    #
    # Note: specifying elements of the request line is the preferred method.
    /filter
      {
      # Deny everything first and then allow specific entries
      /0001 { /type "deny" /glob "*" }
      
      # Open consoles
#     /0011 { /type "allow" /url "/admin/*"  }  # allow servlet engine admin

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
#     /0012 { /type "allow" /url "/crx/*"    }  # allow content repository

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
#     /0013 { /type "allow" /url "/system/*" }  # allow OSGi console

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
        
      # Allow non-public content directories
#     /0021 { /type "allow" /url "/apps/*"   }  # allow apps access

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
#     /0022 { /type "allow" /url "/bin/*"    }

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
      /0023 { /type "allow" /url "/content*" }  # disable this rule to allow mapped content only
      
#     /0024 { /type "allow" /url "/libs/*"   }

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
#     /0025 { /type "deny"  /url "/libs/shindig/proxy*" } # if you enable /libs close access to proxy

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

#     /0026 { /type "allow" /url "/home/*"   }

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
#     /0027 { /type "allow" /url "/tmp/*"    }

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
#     /0028 { /type "allow" /url "/var/*"    }

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

      # Enable specific mime types in non-public content directories 
      /0041 { /type "allow" /url "*.css"   }  # enable css
      /0042 { /type "allow" /url "*.gif"   }  # enable gifs
      /0043 { /type "allow" /url "*.ico"   }  # enable icos
      /0044 { /type "allow" /url "*.js"    }  # enable javascript
      /0045 { /type "allow" /url "*.png"   }  # enable png
      /0046 { /type "allow" /url "*.swf"   }  # enable flash
      /0047 { /type "allow" /url "*.jpg"   }  # enable jpg
      /0048 { /type "allow" /url "*.jpeg"  }  # enable jpeg

      # Deny content grabbing
      /0081 { /type "deny"  /url "*.infinity.json" }
      /0082 { /type "deny"  /url "*.tidy.json"     }
      /0083 { /type "deny"  /url "*.sysview.xml"   }
      /0084 { /type "deny"  /url "*.docview.json"  }
      /0085 { /type "deny"  /url "*.docview.xml"  }
      
      /0086 { /type "deny"  /url "*.*[0-9].json" }
#     /0087 { /type "allow" /method "GET" /url "*.1.json" }  # allow one-level json requests

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

      # Deny query
   /0090 { /type "deny"  /url "*.query.json" }
   
      #######################################
      ## BEGIN: AEM COMMUNITITES ADDITIONS
   #######################################
   /0050 { /type "allow" /glob "GET /etc/designs/*" }  
   /0051 { /type "allow" /glob "GET /etc/clientlibs/*" }  
   /0052 { /type "allow" /glob "GET /bin/statistics/tracker/*" } 
   /0054 { /type "allow" /glob "* /home/users/*/*/profile.form.html*" } 
   /0057 { /type "allow" /glob "GET /home/users/*/profile/*" } 
   /0059 { /type "allow" /glob "GET /etc/clientcontext/*" }
   /0063 { /type "allow" /glob "* /system/sling/logout*" } 
   /0064 { /type "allow" /glob "GET /etc/cloudservices/*" } 
   /0062 { /type "allow" /url "/libs/cq/personalization/*"  }  # enable personalization

   # For Enablement features
   /0170 { /type "allow" /url "/libs/granite/csrf/token.json*" }
   /0171 { /type "allow" /glob "POST /content/sites/*/resources/en/*" }
   /0172 { /type "allow" /glob "GET /content/communities/enablement/reports/*" }
   /0173 { /type "allow" /glob "GET /content/sites/*" }
   /0174 { /type "allow" /glob "GET /content/communities/scorm/*" }
   /0175 { /type "allow" /url "GET /content/sites/*" }
   /0176 { /type "allow" /url "GET /libs/granite/security/userinfo.json"}
   /0177 { /type "allow" /url "GET /libs/granite/security/currentuser.json" }
 
      # Enable CSRF token otherwise nothings works.
   /5001 { /type "allow" /glob "GET /libs/granite/csrf/token.json *"}        
    
   # Allow SCF User Model to bootstrap as it depends on the granite user
   /5002 { /type "allow" /glob "GET /libs/granite/security/currentuser.json*" }
   
      # Allow Communities Site Logout button work
      /5003 { /type "allow" /glob "GET /system/sling/logout.html*" }
   
   # Allow i18n to load correctly
   /5004 { /type "allow" /glob "GET /libs/cq/i18n/dict.en.json *" }

   # Allow social json get pattern.
   /6002 { /type "allow" /glob "GET *.social.*.json*" }
   
   # Allow loading of templates
   /6003 { /type "allow" /glob "GET /services/social/templates*" }
   
   # Allow SCF User model to check moderator rules
   /6005 { /type "allow" /glob "GET /services/social/getLoggedInUser?moderatorCheck=*" }
   
   # Allow CKEditor to load which uses a query pattern not sufficed by regular glob above.
   /6006 { /type "allow" /glob "GET /etc/clientlibs/social/thirdparty/ckeditor/*.js?t=*" }
   /6007 { /type "allow" /glob "GET /etc/clientlibs/social/thirdparty/ckeditor/*.css?t=*" }
   
   # Allow Fonts from Communities to load
   /6050 { /type "allow" /glob "GET *.woff *" }
   /6051 { /type "allow" /glob "GET *.ttf *" }

      # Enable CQ Security checkpoint for component guide.
   /7001 { /type "allow" /glob "GET /libs/cq/security/userinfo.json?cq_ck=*"}

      #######################################
      ## END: AEM COMMUNITITES ADDITIONS
   #######################################
      
      }

    # The cache section regulates what responses will be cached and where.
    /cache
      {
      # The docroot must be equal to the document root of the webserver. The
      # dispatcher will store files relative to this directory and subsequent
      # requests may be "declined" by the dispatcher, allowing the webserver
      # to deliver them just like static files.
      /docroot "/opt/dispatcher"

      # Sets the level upto which files named ".stat" will be created in the 
      # document root of the webserver. When an activation request for some 
      # page is received, only files within the same subtree are affected 
      # by the invalidation.
      #/statfileslevel "0"
      
      # Flag indicating whether to cache responses to requests that contain
      # authorization information.
      /allowAuthorized "1"
      
      # Flag indicating whether the dispatcher should serve stale content if
      # no remote server is available.
      #/serveStaleOnError "0"
      
      # The rules section defines what responses should be cached based on
      # the requested URL. Please note that only the following requests can
      # lead to cacheable responses:
      #
      # - HTTP method is GET
      # - URL has an extension
      # - Request has no query string
      # - Request has no "Authorization" header (unless allowAuthorized is 1)
      /rules
        {
        /0000
          {
          # the globbing pattern to be compared against the url
          # example: * -> everything
          #        : /foo/bar.* -> only the /foo/bar documents
          #        : /foo/bar/* -> all pages below /foo/bar
          #        : /foo/bar[./]* -> all pages below and /foo/bar itself
          #        : *.html        -> all .html files
          /glob "*"
          /type "allow"
          }

      #######################################
      ## BEGIN: AEM COMMUNITITES ADDITIONS
     #######################################   
    
   # Never cache the client-side .social.json calls
   /0001 { /type "deny" /glob "*.social.json*" }

   # Never cache the user-specific .json requests
   /0002 { /type "deny" /glob "/libs/granite/csrf/token.json*" }
   /0003 { /type "deny" /glob "/libs/granite/security/currentuser.json*" }
   /0004 { /type "deny" /glob "/libs/granite/security/userinfo.json*" }

   # Never cache the private community groups pages in case - add your own deny rules in there
   /0005 { /type "deny" /glob "/content/*/groups/*" }

   # Never cache the assignments page in case the enablement feature is in use - add your own deny rules in there
   /0006 { /type "deny" /glob "/content/*/assignments/*" }
     
      #######################################
      ## END: AEM COMMUNITITES ADDITIONS
      #######################################   
    
        }
        
      # The invalidate section defines the pages that are "invalidated" after
      # any activation. Please note that the activated page itself and all 
      # related documents are flushed on an modification. For example: if the 
      # page /foo/bar is activated, all /foo/bar.* files are removed from the
      # cache.
      /invalidate
        {
        /0000
          {
          /glob "*"
          /type "deny"
          }
        /0001
          {
          # Consider all HTML files stale after an activation.
          /glob "*.html"
          /type "allow"
          }
        /0002
          {
          /glob "/etc/segmentation.segment.js"
          /type "allow"
          }
        /0003
          {
          /glob "*/analytics.sitecatalyst.js"
          /type "allow"
          }
        }

      # The allowedClients section restricts the client IP addresses that are
      # allowed to issue activation requests.
      /allowedClients
        {
        # Uncomment the following to restrict activation requests to originate
        # from "localhost" only.
        #
        #/0000
        #  {
        #  /glob "*"
        #  /type "deny"
        #  }
        #/0001
        #  {
        #  /glob "127.0.0.1"
        #  /type "allow"
        #  }
        }
        
      # The ignoreUrlParams section contains query string parameter names that
      # should be ignored when determining whether some request's output can be
      # cached or delivered from cache.
      #
      # In this example configuration, the "q" parameter will be ignored. 
      #/ignoreUrlParams
      #  {
      #  /0001 { /glob "*" /type "deny" }
      #  /0002 { /glob "q" /type "allow" }
      #  }
      
    /enableTTL "1"

      }
      
    # The statistics sections dictates how the load should be balanced among the
    # renders according to the media-type. 
    /statistics
      {
      /categories
        {
        /html
          {
          /glob "*.html"
          }
        /others
          {
          /glob "*"
          }
        }
      }
    }
  }
```
