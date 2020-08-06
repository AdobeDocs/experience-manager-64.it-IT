---
title: Selezione dell’interfaccia
seo-title: Selezione dell’interfaccia
description: Per agevolare il lavoro degli utenti che si occupano di authoring, l’interfaccia utente touch consente di passare all’interfaccia classica quando necessario.
seo-description: Per agevolare il lavoro degli utenti che si occupano di authoring, l’interfaccia utente touch consente di passare all’interfaccia classica quando necessario.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 59%

---


# Selezione dell’interfaccia{#selecting-your-ui}

Poiché l’interfaccia touch sostituisce l’interfaccia classica, l’utente o l’amministratore dell’istanza di AEM deve prendere una decisione attiva per continuare a utilizzare l’interfaccia classica. Poiché l’interfaccia classica non viene più aggiornata, l’utente che si occupa dell’authoring non può semplicemente passare dall’interfaccia classica a quella equivalente nell’interfaccia touch.

Per agevolare il lavoro degli utenti che si occupano di authoring, l’interfaccia utente touch consente di passare all’interfaccia classica quando necessario. Per ulteriori informazioni, consulta la sezione [Selezione dell’interfaccia](/help/sites-authoring/select-ui.md) nella documentazione di authoring standard.

>[!NOTE]
>
>Nelle istanze aggiornate da una versione precedente viene mantenuta l’interfaccia classica per la creazione e la modifica delle pagine.
>
>After upgrade, page authoring will not be automatically switched to the touch-enabled UI, but you can configure this using the [OSGi configuration](/help/sites-deploying/configuring-osgi.md) of the **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service). Vedi [Ignorare le impostazioni dell’interfaccia per l’editor](#uioverridesfortheeditor).

## Configuring the Default UI for Your Instance {#configuring-the-default-ui-for-your-instance}

Un amministratore di sistema può configurare l’interfaccia utente utilizzata all’avvio e all’accesso utilizzando la [mappatura della directory principale](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

Tale impostazione può essere ignorata e sostituita dalle impostazioni predefinite dell’utente o dalle impostazioni della sessione.
