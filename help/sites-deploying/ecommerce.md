---
title: Panoramica di eCommerce
seo-title: Panoramica di eCommerce
description: 'AEM eCommerce generico è disponibile come parte dell''installazione standard e offre tutte le funzionalità del framework eCommerce.  '
seo-description: 'AEM eCommerce generico è disponibile come parte dell''installazione standard e offre tutte le funzionalità del framework eCommerce.  '
uuid: 7be42b1e-f1d6-4891-96f8-0133b3a299a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: cb043066-aefc-4b68-b302-2b5dd710a786
translation-type: tm+mt
source-git-commit: 0a7f40dd692985890c0c51c54a153135d39c7bd8
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 5%

---


# Panoramica di eCommerce{#ecommerce-overview}

AEM eCommerce generico è disponibile come parte di un&#39;installazione standard e offre tutte le funzionalità del framework eCommerce.

 Adobe fornisce due versioni di Commerce Integration Framework:

|  | CIF on-prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Versioni di AEM supportate | AEM on prem o AMS 6.x | AEM AMS 6.4 e 6.5 |
| Back-end | - AEM, Java <br> - Integrazione monolitica, mappatura pre-compilazione (template)<br> - archivio JCR | - Magento <br>- Java e Javascript <br>- Nessun dato Commerce memorizzato nell&#39;archivio JCR |
| Front-end | AEM pagine sottoposte a rendering sul lato server | Applicazione a pagina mista (rendering ibrido) |
| Catalogo prodotti | - Importazione prodotti, editor, memorizzazione nella cache in AEM <br>- Cataloghi regolari con AEM o pagine proxy | - Nessuna importazione di prodotti <br>- Modelli generici <br>- Dati su richiesta tramite connettore |
| Scalabilità | - Può supportare fino a pochi milioni di prodotti (dipende dal caso d&#39;uso) <br> - Caching on Dispatcher | - Nessuna limitazione del volume <br>- Memorizzazione nella cache del dispatcher o CDN |
| Modello dati standardizzato | No | Sì, schema Magento GraphQL |
| Disponibilità | Sì:<br> - Commerce Cloud SAP (estensione aggiornata per supportare AEM 6.4 e Hybris 5 (impostazione predefinita) e mantiene la compatibilità con l&#39;Commerce Cloud Hybris 4 <br>- Salesforce (connettore open source per supportare AEM 6.4) | Sì tramite open source tramite GitHub. <br> Magento Commerce (Supporta l&#39;Magento 2.3.2 (predefinito) e compatibile con Magento 2.3.1). |
| Quando utilizzare | Casi di utilizzo limitati: Per gli scenari in cui potrebbe essere necessario importare cataloghi statici di piccole dimensioni | Soluzione preferita nella maggior parte dei casi di utilizzo |


## Implementazione di altre implementazioni {#deploying-other-implementations}

* [COMMERCE CLOUD SAP](/help/sites-deploying/sap-commerce-cloud.md)
* [Commerce Cloud Salesforce](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

>[!NOTE]
>
>Per informazioni sui concetti e sulla gestione delle implementazioni eCommerce, consultate [Amministrazione di eCommerce](/help/sites-administering/ecommerce.md).
>
>Per informazioni sull&#39;estensione delle funzionalità di eCommerce, vedere [Sviluppo di eCommerce](/help/sites-developing/ecommerce.md).

