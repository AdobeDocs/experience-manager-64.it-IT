---
title: Abilitazione di CRXDE Lite in AEM
seo-title: Enabling CRXDE Lite in AEM
description: Scopri come abilitare CRXDE Lite in AEM.
seo-description: Learn how to enable CRXDE Lite in AEM.
uuid: d7a3db67-6384-463b-9aa9-f08ecc6c99c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 72df3ece-badf-466b-8f9a-0ec985d87741
exl-id: 3d8dc987-2ff9-4f71-bc07-48018caa3af4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 4%

---

# Abilitazione di CRXDE Lite in AEM{#enabling-crxde-lite-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per garantire che le installazioni AEM siano il più sicure possibile, la lista di controllo della sicurezza raccomanda [disabilitazione di WebDAV](/help/sites-administering/security-checklist.md#disable-webdav) in ambienti di produzione.

Tuttavia, CRXDE Lite dipende dal `org.apache.sling.jcr.davex` per il corretto funzionamento del bundle, pertanto la disabilitazione di WebDAV comporterà la disattivazione efficace anche di CRXDE Lite.

In questo caso, vai a `https://serveraddress:4502/crx/de/index.jsp` visualizzerà un nodo principale vuoto e tutte le richieste HTTP alle risorse CRXDE Lite avranno esito negativo:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Anche se questa raccomandazione è destinata a ridurre il più possibile le superfici di attacco, gli amministratori di sistema potrebbero talvolta aver bisogno dell&#39;accesso ad CRXDE Lite per sfogliare i contenuti o eseguire il debug dei problemi sulle istanze di produzione.

Se disabilitata, puoi attivare CRXDE Lite seguendo la procedura seguente:

1. Vai alla console Componenti OSGi all’indirizzo `http://localhost:4502/system/console/components`
1. Cerca il seguente componente:

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Fai clic sull’icona a forma di chiave inglese accanto a essa per visualizzarne le opzioni di configurazione:

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Crea la seguente configurazione:

   * **Percorso directory principale:** `/crx/server`
   * Spunta la casella sotto **Usa URI assoluti**.

1. Quando hai finito di utilizzare CRXDE Lite, assicurati di disabilitare nuovamente WebDAV.

Puoi anche abilitare CRXDE Lite tramite cURL, eseguendo questo comando:

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## Altre risorse {#other-resources}

Per ulteriori informazioni sulle funzioni di sicurezza di AEM 6, consulta le pagine seguenti:

* [Elenco di controllo AEM sicurezza](/help/sites-administering/security-checklist.md)
* [Esecuzione di AEM in modalità pronta per la produzione](/help/sites-administering/production-ready.md)
