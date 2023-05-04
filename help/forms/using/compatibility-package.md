---
title: Pacchetto di compatibilità
seo-title: Compatibility Package
description: L’installazione del pacchetto di compatibilità su AEM Forms 6.4 consente di utilizzare le risorse Gestione Corrispondenza di AEM Forms 6.3 e i modelli e le pagine dei moduli adattivi obsoleti
seo-description: Installing the Compatibility package on AEM Forms 6.4 allows you to use the Correspondence Management assets from AEM Forms 6.3 and deprecated adaptive forms templates and pages
uuid: e50b1ff9-c357-422a-8da8-a791ff805317
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 38a80992-2eda-4535-89af-0de34b1a9686
role: Admin
exl-id: 0bfa0e65-c4cd-4c37-b42b-bff1b777a7be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 3%

---

# Installa il pacchetto di compatibilità {#compatibility-package}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’installazione del pacchetto di compatibilità su AEM Forms 6.4 consente di utilizzare le risorse Gestione Corrispondenza di AEM Forms 6.3 e i modelli e le pagine dei moduli adattivi obsoleti

## Panoramica {#overview}

La comunicazione interattiva è l’approccio predefinito e consigliato per creare comunicazioni con i clienti in AEM Forms 6.4. Per continuare a utilizzare le lettere di AEM 6.3 Forms e AEM 6.2 Forms, è necessario installare il [Pacchetto di compatibilità AEMFD](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

Il pacchetto di compatibilità di AEMFD consente di utilizzare le seguenti risorse da AEM Forms 6.3 e 6.2 su AEM Forms 6.4:

* Frammenti di documenti creati in AEM Forms 6.3 e 6.2
* Lettere
* Dizionari dati
* Modelli e pagine obsolete per i moduli adattivi

Per ulteriori informazioni, consulta [Risorse rese compatibili con AEM Forms 6.4 mediante l’installazione del pacchetto di compatibilità](/help/forms/using/compatibility-package.md#assetsmadecompatible).

## Supporto per risorse AEM Forms 6.3 e 6.2 in AEM Forms 6.4 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Dopo aver eseguito un aggiornamento, procedi come segue per installare il pacchetto di compatibilità AEMFD e rendere le risorse compatibili con la versione 6.4:

Assicurati di avere [Pacchetto di compatibilità AEM](/help/sites-deploying/backward-compatibility.md) preinstallato.

1. Installa il [Pacchetto di compatibilità](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

   Per ulteriori informazioni sul caricamento e l’installazione del pacchetto, vedi [Come lavorare con i pacchetti](/help/sites-administering/package-manager.md).

1. Dopo aver stabilizzato i registri, riavvia il server.
1. Utilizza l’utility di migrazione per rendere le risorse compatibili con la versione 6.4.

   Per ulteriori informazioni, consulta [utility di migrazione](/help/forms/using/migration-utility.md).

## Risorse rese compatibili con AEM Forms 6.4 mediante l’installazione del pacchetto di compatibilità {#assetsmadecompatible}

Installando il pacchetto di compatibilità, puoi rendere compatibili con AEM Forms 6.4 le risorse e i modelli seguenti:

* Attività di gestione della corrispondenza dal AEM 6.3 e precedenti

   * [Lettere](/help/forms/using/create-letter.md)
   * [Dizionari dati](/help/forms/using/data-dictionary.md)
   * Frammenti del documento

* Modelli obsoleti per moduli adattivi

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/ttabsEnrollmentTemplate
   * /libs/fd/af/templates/taggedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Pagine obsolete dei moduli adattivi:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenregistrazione
   * /libs/fd/afaddon/components/page/advancedensubscription
