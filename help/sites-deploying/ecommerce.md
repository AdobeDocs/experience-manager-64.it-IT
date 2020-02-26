---
title: Panoramica di eCommerce
seo-title: Panoramica di eCommerce
description: 'AEM eCommerce generico è disponibile come parte dell’installazione standard e offre tutte le funzionalità del framework eCommerce.  '
seo-description: 'AEM eCommerce generico è disponibile come parte dell’installazione standard e offre tutte le funzionalità del framework eCommerce.  '
uuid: 7be42b1e-f1d6-4891-96f8-0133b3a299a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: cb043066-aefc-4b68-b302-2b5dd710a786
translation-type: tm+mt
source-git-commit: 0a7f40dd692985890c0c51c54a153135d39c7bd8

---


# Panoramica di eCommerce{#ecommerce-overview}

AEM eCommerce generico è disponibile come parte di un’installazione standard e offre tutte le funzionalità del framework eCommerce.

Adobe fornisce due versioni di Commerce Integration Framework:

|  | CIF on-prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Versioni di AEM supportate | AEM on prem o AMS 6.x | AEM AMS 6.4 e 6.5 |
| Back-end | - AEM, Java <br> - Integrazione monolitica, mappatura pre-build (modello)<br> - archivio JCR | - Magento <br>- Java e Javascript <br>- Nessun dato Commerce memorizzato nel repository JCR |
| Front-end | AEM, pagine sottoposte a rendering sul lato server | Applicazione a pagina mista (rendering ibrido) |
| Catalogo prodotti | - Importazione prodotti, editor, memorizzazione nella cache in AEM <br>- Cataloghi regolari con AEM o pagine proxy | - Nessuna importazione di prodotti <br>- Modelli generici <br>- Dati on-demand tramite connettore |
| Scalabilità | - Può supportare fino a pochi milioni di prodotti (dipende dal caso d&#39;uso) <br> - Memorizzazione nella cache del Dispatcher | - Nessuna limitazione del volume <br>- Memorizzazione nella cache su Dispatcher o CDN |
| Modello dati standardizzato | No | Sì, schema Magento GraphQL |
| Disponibilità | <br> Sì: - SAP Commerce Cloud (estensione aggiornata per supportare AEM 6.4 e Hybris 5 (predefinito) e mantiene la compatibilità con Hybris 4 <br>- Salesforce Commerce Cloud (connettore open-source per supportare AEM 6.4) | Sì tramite open source tramite GitHub. <br> Magento Commerce (Supporta Magento 2.3.2 (predefinito) e compatibile con Magento 2.3.1). |
| Quando utilizzare | Casi di utilizzo limitati: Per gli scenari in cui potrebbe essere necessario importare cataloghi statici di piccole dimensioni | Soluzione preferita nella maggior parte dei casi di utilizzo |


## Distribuzione di altre implementazioni {#deploying-other-implementations}

* [SAP Commerce Cloud](/help/sites-deploying/sap-commerce-cloud.md)
* [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

>[!NOTE]
>
>Per informazioni sui concetti e sulla gestione delle implementazioni eCommerce, consulta [Amministrazione di eCommerce](/help/sites-administering/ecommerce.md).
>
>Per informazioni sull’estensione delle funzionalità eCommerce, consultate [Sviluppo di eCommerce](/help/sites-developing/ecommerce.md).

