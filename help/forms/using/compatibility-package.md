---
title: Pacchetto di compatibilità
seo-title: Pacchetto di compatibilità
description: 'L''installazione del pacchetto di compatibilità su AEM Forms 6.4 consente di utilizzare le risorse Gestione corrispondenza di AEM Forms 6.3 e di utilizzare modelli e pagine di moduli adattivi obsoleti '
seo-description: L'installazione del pacchetto di compatibilità su AEM Forms 6.4 consente di utilizzare le risorse Gestione corrispondenza di AEM Forms 6.3 e di utilizzare modelli e pagine di moduli adattivi obsoleti
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
translation-type: tm+mt
source-git-commit: 9a2ebded0068213903020d2c5633a05b6ffb07ef

---


# Installa pacchetto di compatibilità {#compatibility-package}

L&#39;installazione del pacchetto di compatibilità su AEM Forms 6.4 consente di utilizzare le risorse Gestione corrispondenza di AEM Forms 6.3 e di utilizzare modelli e pagine di moduli adattivi obsoleti

## Panoramica {#overview}

La comunicazione interattiva è l’approccio predefinito e consigliato per creare comunicazioni con i clienti in AEM Forms 6.4. Per continuare a utilizzare le lettere da AEM 6.3 Forms e AEM 6.2 Forms, è necessario installare il pacchetto [Compatibilità](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)AEMFD.

Il pacchetto di compatibilità AEMFD consente di utilizzare le risorse seguenti da AEM Forms 6.3 e 6.2 su AEM Forms 6.4:

* Frammenti di documenti creati in AEM Forms 6.3 e 6.2
* Lettere
* Dizionari dati
* Moduli adattivi modelli e pagine obsoleti

Per ulteriori informazioni, consultate [Risorse rese compatibili con AEM Forms 6.4, installando il pacchetto](/help/forms/using/compatibility-package.md#assetsmadecompatible)Compatibilità.

## Supporto per risorse AEM Forms 6.3 e 6.2 in AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Dopo aver effettuato l’aggiornamento, effettuate le seguenti operazioni per installare il pacchetto di compatibilità AEMFD e rendere le risorse compatibili con la versione 6.4:

Accertatevi di disporre di un pacchetto [](/help/sites-deploying/backward-compatibility.md) AEM Compatibilità preinstallato.

1. Installate il pacchetto [](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT)Compatibilità.

   Per ulteriori informazioni sul caricamento e l&#39;installazione del pacchetto, consultate [Come lavorare con i pacchetti](/help/sites-administering/package-manager.md).

1. Dopo aver stabilizzato i registri, riavviate il server.
1. Utilizzate l’utility di migrazione per rendere le risorse compatibili con la versione 6.4.

   Per ulteriori informazioni, vedi Utilità [di](/help/forms/using/migration-utility.md)migrazione.

## Risorse rese compatibili con AEM Forms 6.4 installando il pacchetto Compatibilità {#assetsmadecompatible}

Installando il pacchetto Compatibilità, potete rendere le risorse e i modelli seguenti compatibili con AEM Forms 6.4:

* Risorse per la gestione della corrispondenza da AEM 6.3 e versioni precedenti

   * [Lettere](/help/forms/using/create-letter.md)
   * [Dizionari dati](/help/forms/using/data-dictionary.md)
   * Frammenti del documento

* Modelli obsoleti per moduli adattivi

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/taccollEnrollmentTemplate
   * /libs/fd/af/templates/taccollEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Moduli adattivi: pagine obsolete:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment

