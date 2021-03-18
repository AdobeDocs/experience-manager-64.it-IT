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
feature: Commerce Integration Framework
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 6%

---


# Panoramica di eCommerce{#ecommerce-overview}

AEM eCommerce generico è disponibile come parte di un’installazione standard e offre tutte le funzionalità del framework eCommerce.

In Adobe sono disponibili due versioni di Commerce Integration Framework:

|  | CIF on-prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Versioni di AEM supportate | AEM on-premise o AMS 6.x | AEM AMS 6.4 e 6.5 |
| Back-end | - AEM, Java <br> - Integrazione monolitica, mappatura pre-compilazione (modello)<br> - archivio JCR | - Magento <br>- Java e Javascript <br>- Nessun dato Commerce memorizzato nell&#39;archivio JCR |
| Front-end | AEM pagine di rendering lato server | Applicazione a pagina mista (rendering ibrido) |
| Catalogo dei prodotti | - Importazione prodotti, editor, memorizzazione in cache in AEM <br>- Cataloghi regolari con pagine AEM o proxy | - Nessuna importazione di prodotti <br>- Modelli generici <br>- Dati su richiesta tramite connettore |
| Scalabilità | - Può supportare fino a pochi milioni di prodotti (dipende dal caso d’uso) <br> - Memorizzazione in cache su Dispatcher | - Nessuna limitazione del volume <br>- Memorizzazione in cache su Dispatcher o CDN |
| Modello dati standardizzato | No | Sì, Magento schema GraphQL |
| Disponibilità | Sì:<br> - Commerce Cloud SAP (estensione aggiornata per supportare AEM 6.4 e Hybris 5 (impostazione predefinita) e mantiene la compatibilità con Hybris 4 <br>- Commerce Cloud Salesforce (connettore open source per supportare AEM 6.4) | Sì tramite open source tramite GitHub. <br> Magento Commerce (supporta Magenti 2.3.2 (predefinito) e compatibile con Magenti 2.3.1). |
| Quando utilizzare | Casi d’uso limitati: Per gli scenari in cui possono essere necessari l’importazione di cataloghi statici di piccole dimensioni | Soluzione preferita nella maggior parte dei casi d&#39;uso |


## Implementazione di altre implementazioni {#deploying-other-implementations}

* [Commerce Cloud SAP](/help/sites-deploying/sap-commerce-cloud.md)
* [Commerce Cloud Salesforce](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

>[!NOTE]
>
>Per informazioni sui concetti e sull’amministrazione delle implementazioni di eCommerce, consulta [Amministrazione di eCommerce](/help/sites-administering/ecommerce.md).
>
>Per informazioni sull’estensione delle funzionalità di eCommerce, consulta [Sviluppo di eCommerce](/help/sites-developing/ecommerce.md).

