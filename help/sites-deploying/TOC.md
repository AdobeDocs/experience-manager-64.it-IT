---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: Guida alla distribuzione di AEM 6.4
breadcrumb-title: Guida alla distribuzione
user-guide-description: Ulteriori informazioni sull’installazione, la distribuzione e l’architettura di Adobe Experience Manager 6.4, inclusa la distribuzione cloud di Adobe Managed Services.
feature: Deploying
role: Architect
hide: true
source-git-commit: b61797a9096c0473658d6aabfb584a53e42095b7
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 13%

---


# Guida utente alla distribuzione di AEM 6.4 {#deploying}

+ [Guida utente alla distribuzione](home.md)
+ Introduzione alla piattaforma AEM {#introduction}
   + [Introduzione alla piattaforma AEM](platform.md)
   + [Requisiti tecnici](technical-requirements.md)
   + [Elementi di storage in AEM 6.4](storage-elements-in-aem-6.md)
   + [AEM con MongoDB](aem-with-mongodb.md)
+ Distribuzione AEM {#deploying}
   + [Implementazione e manutenzione](deploy.md)
   + [Implementazioni consigliate](recommended-deploys.md)
   + [Installazione del server applicazioni](application-server-install.md)
   + [Installazione personalizzata indipendente](custom-standalone-install.md)
   + [Avvio e arresto da riga di comando](command-line-start-and-stop.md)
   + [Configurazione degli archivi di nodi e degli archivi di dati nel AEM 6](data-store-config.md)
   + [Pulizia revisioni](revision-cleanup.md)
   + [Come eseguire AEM con lo standby a freddo TarMK](tarmk-cold-standby.md)
   + [Supporto RDBMS in AEM 6.4](rdbms-support-in-aem.md)
   + [Query e indicizzazione Oak](queries-and-indexing.md)
   + [Indicizzazione tramite Oak-run Jar](indexing-via-the-oak-run-jar.md)
   + [Casi d&#39;uso dell&#39;indicizzazione Oak-run.jar](oak-run-indexing-usecases.md)
   + [Risoluzione dei problemi degli indici Oak](troubleshooting-oak-indexes.md)
   + [Consenso alla raccolta di statistiche di utilizzo aggregate](opt-in-aggregated-usage-statistics.md)
   + [Risoluzione dei problemi](troubleshooting.md)
+ Configurazione di AEM {#configuring}
   + [Concetti di configurazione di base](configuring.md)
   + [Registrazione](configure-logging.md)
   + [Configurazione di OSGi](configuring-osgi.md)
   + [Impostazioni di configurazione OSGi](osgi-configuration-settings.md)
   + [Modalità di esecuzione](configure-runmodes.md)
   + [Console Web](web-console.md)
   + [Replica](replication.md)
   + [Replicazione con SSL reciproco](mssl-replication.md)
   + [Risoluzione dei problemi di replica](troubleshoot-rep.md)
   + [Scadenza degli oggetti statici](expiration-static-objects.md)
   + [Rimozione delle versioni](version-purging.md)
   + [Monitoraggio e manutenzione dell’istanza AEM](monitoring-and-maintaining.md)
   + [Offload dei processi](offloading.md)
   + [Single Sign On](single-sign-on.md)
   + [Mappatura delle risorse](resource-mapping.md)
   + [Abilitazione di HTTP su SSL](https://experienceleague.adobe.com/docs/experience-manager-64/administering/security/ssl-by-default.html)
   + [Controlli di coerenza e di transito](consistency-check.md)
   + [Linee guida sulle prestazioni](performance-guidelines.md)
   + [Ottimizzazione delle prestazioni](configuring-performance.md)
   + [Guida alle prestazioni di Assets](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html)
   + [Articoli dimostrativi sulla configurazione](ht-deploy.md)
   + [Rimozione dei siti di Geometrixx](removing-the-geometrixx-sites.md)
   + [Configurazione della console Web](configuring-web-console.md)
+ Aggiornamento a AEM 6.4 {#upgrading}
   + [Aggiornamento a AEM 6.4](upgrade.md)
   + [Pianificazione dell&#39;aggiornamento](upgrade-planning.md)
   + [Valutazione della complessità dell’aggiornamento con il rilevatore pattern](pattern-detector.md)
   + [Compatibilità con le versioni precedenti in AEM 6.4](backward-compatibility.md)
   + [Procedura di aggiornamento](upgrade-procedure.md)
   + [Utilizzo della reindicizzazione offline per ridurre i tempi di inattività durante un aggiornamento](upgrade-offline-reindexing.md)
   + [Esecuzione di un aggiornamento sul posto](in-place-upgrade.md)
   + [Migrazione dei contenuti Lazy](lazy-content-migration.md)
   + [Utilizzo dello strumento di migrazione CRX2Oak](using-crx2oak.md)
   + [Attività di manutenzione pre-aggiornamento](pre-upgrade-maintenance-tasks.md)
   + [Controlli e risoluzione dei problemi post-aggiornamento](post-upgrade-checks-and-troubleshooting.md)
   + [Aggiornamento di Custom Search Forms](upgrading-custom-search-forms.md)
   + [Aggiornamenti sostenibili](sustainable-upgrades.md)
   + [Aggiornamento di codice e personalizzazioni](upgrading-code-and-customizations.md)
   + [Passaggi di aggiornamento per le installazioni di Application Server](app-server-upgrade.md)
   + [Elenco dei bundle obsoleti disinstallati dopo l&#39;aggiornamento](obsolete-bundles.md)
+ Ristrutturazione dell’archivio {#restructuring}
   + [Ristrutturazione dell’archivio in AEM 6.4](repository-restructuring.md)
   + [Ristrutturazione dell’archivio comune in AEM 6.4](all-repository-restructuring-in-aem-6-4.md)
   + [Ristrutturazione dell’archivio siti in AEM 6.4](sites-repository-restructuring-in-aem-6-4.md)
   + [Ristrutturazione dell’archivio risorse in AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html?lang=it)
   + [Ristrutturazione dell’archivio Dynamic Media in AEM 6.4](dynamicmedia-repository-restructuring-in-aem-6-4.md)
   + [Ristrutturazione dell’archivio Forms in AEM 6.4](forms-repository-restructuring-in-aem-6-4.md)
   + [Ristrutturazione dell’archivio di e-commerce in AEM 6.4](ecommerce-repository-restructuring-in-aem-6-4.md)
   + [Ristrutturazione dell’archivio per AEM Communities nella versione 6.4](communities-repository-restructuring-in-aem-6-4.md)
+ eCommerce {#ecommerce}
   + [Panoramica di eCommerce](ecommerce.md)
   + [Commerce Cloud SAP](sap-commerce-cloud.md)
   + [Commerce Cloud Salesforce](https://github.com/adobe/commerce-salesforce)
   + [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)
+ Best practice   {#practices}
   + [Best practice di distribuzione](best-practices.md)
   + [Struttura delle prestazioni](performance-tree.md)
   + [Tecniche consigliate per il test delle prestazioni](best-practices-for-performance-testing.md)
   + [Tecniche consigliate per query e indicizzazione](best-practices-for-queries-and-indexing.md)
   + [Interfaccia utente Recommendations per clienti](ui-recommendations.md)
   + [Prestazioni e scalabilità](performance.md)


<!--

To be removed:
[Quickstart for AEM Screens](setting-up-a-basic-project-screens.md)
[Device Control Center](device-control-center.md)
[repository-restructuring-in-aem64](repository-restructuring-in-aem64.md)
[Web Console] (configuring-web-console.md)
[Configuring and Deploying AEM Screens](configuring-screens-introduction.md)
[Kickstart Guide](kickstart-for-aem-screens.md)
/help/sites/deploying/using/performance-lp.md
/help/sites-deploying/do-not-delete-performance-guidelines-pdf.md
/help/sites-deploying/removing-the-geometrixx-sites.md
/help/sites-deploying/consistency-check.md

Redirects:
[(Enabling HTTP Over SSL)](config-ssl.md) redirect to /content/help/en/experience-manager/6-4/sites-administering/ssl-by-default
-->
