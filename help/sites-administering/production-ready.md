---
title: Esecuzione di AEM in modalità pronta per la produzione
seo-title: Esecuzione di AEM in modalità pronta per la produzione
description: Scoprite come eseguire AEM in modalità Produzione pronta.
seo-description: Scoprite come eseguire AEM in modalità Produzione pronta.
uuid: f48c8bae-c72f-4772-967e-f1526f096399
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 32da99f0-f058-40ae-95a8-2522622438ce
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 4%

---


# Esecuzione di AEM in modalità pronta per la produzione{#running-aem-in-production-ready-mode}

Con AEM 6.1,  Adobe introduce la nuova `"nosamplecontent"` modalità di esecuzione, volta ad automatizzare i passaggi necessari per preparare un&#39;istanza AEM per la distribuzione in un ambiente di produzione.

La nuova modalità di esecuzione non solo configurerà automaticamente l&#39;istanza per aderire alle best practice di protezione descritte nella lista di controllo di sicurezza, ma rimuoverà anche tutte le applicazioni e le configurazioni geometrixx campione nel processo.

>[!NOTE]
>
>Poiché, per motivi pratici, la modalità AEM Produzione pronta coprirà solo la maggior parte delle attività necessarie per proteggere un&#39;istanza, si consiglia vivamente di consultare la lista di controllo della [sicurezza](/help/sites-administering/security-checklist.md) prima di entrare in contatto con l&#39;ambiente di produzione.
>
>Inoltre, l&#39;esecuzione di AEM in modalità pronta per la produzione disattiverà l&#39;accesso ai CRXDE Lite. Se necessario per eseguire il debug, consulta [Abilitazione del CRXDE Lite in AEM](/help/sites-administering/enabling-crxde-lite.md).

![chlimage_1-83](assets/chlimage_1-83.png)

Per eseguire AEM in modalità pronta per la produzione, è sufficiente aggiungere il pulsante `nosamplecontent` tramite il `-r` commutatore in modalità di esecuzione agli argomenti di avvio esistenti:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

Ad esempio, potete utilizzare la produzione pronta per avviare un&#39;istanza di creazione con la persistenza MongoDB come segue:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Cambia parte della modalità pronta per la produzione {#changes-part-of-the-production-ready-mode}

Più precisamente, le seguenti modifiche di configurazione verranno eseguite quando AEM viene eseguito in modalità pronta per la produzione:

1. Il pacchetto **CRXDE Support** ( `com.adobe.granite.crxde-support`) è disabilitato per impostazione predefinita in modalità pronta per la produzione. Può essere installato in qualsiasi momento dal repository pubblico  Adobe Maven. La versione 3.0.0 è necessaria per AEM 6.1.

1. Il bundle **Apache Sling Simple WebDAV Access to repository** ( `org.apache.sling.jcr.webdav`) sarà disponibile solo sulle istanze **dell&#39;autore** .

1. Gli utenti appena creati dovranno cambiare la password al primo login. Ciò non vale per l&#39;utente amministratore.
1. **La generazione di informazioni** di debug è disabilitata per il gestore **di script Java** Apache.

1. **Il contenuto** mappato e **le informazioni** di debug generate sono disabilitate per il gestore **di script JSP** Apache Sling.

1. Il filtro **** Day CQ WCM è impostato su `edit` per l’ **autore** e `disabled` sulle istanze **pubblicate** .

1. **Adobe Granite HTML Library Manager** è configurato con le seguenti impostazioni:

   1. **Riduci:** `enabled`
   1. **Debug:** `disabled`
   1. **Gzip:** `enabled`
   1. **Tempo:** `disabled`

1. Il Servlet **** Apache Sling è impostato per supportare le configurazioni sicure per impostazione predefinita, come segue:

| **Configurazione** | **Authoring** | **Pubblicazione** |
|---|---|---|
| Rendering TXT | disattivato | disattivato |
| Rendering HTML | disattivato | disattivato |
| Rendering JSON | abilitato | abilitato |
| Rendering XML | disattivato | disattivato |
| json.maximumresults | 1000 | 100 |
| Indice automatico | disattivato | disattivato |

