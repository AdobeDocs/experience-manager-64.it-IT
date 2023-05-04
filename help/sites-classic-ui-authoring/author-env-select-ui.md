---
title: Selezione dell’interfaccia utente
seo-title: Selecting your UI
description: Per agevolare l’authoring degli utenti, l’interfaccia touch consente di passare all’interfaccia classica quando necessario.
seo-description: For convenience to authoring users, the touch-enabled UI does allow for switching to the classic UI when necessary.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
exl-id: 997040d4-cf8f-4240-8423-a98d562aae02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 3%

---

# Selezione dell’interfaccia utente{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Poiché l’interfaccia touch sostituisce l’interfaccia classica, l’utente o l’amministratore dell’istanza di AEM deve prendere una decisione attiva per continuare a utilizzare l’interfaccia classica. Poiché l’interfaccia classica non viene più aggiornata, l’utente che si occupa dell’authoring non può semplicemente passare dall’interfaccia classica all’equivalente nell’interfaccia touch.

Per agevolare l’authoring degli utenti, l’interfaccia touch consente di passare all’interfaccia classica quando necessario. Consulta la sezione [Selezione dell’interfaccia utente](/help/sites-authoring/select-ui.md) per ulteriori informazioni, consulta la documentazione standard sull’authoring .

>[!NOTE]
>
>Le istanze aggiornate da una versione precedente manterranno l’interfaccia classica per la creazione delle pagine.
>
>Dopo l’aggiornamento, l’authoring delle pagine non passa automaticamente all’interfaccia touch, ma puoi configurarlo utilizzando l’ [Configurazione OSGi](/help/sites-deploying/configuring-osgi.md) del **Servizio modalità interfaccia utente di authoring WCM** ( `AuthoringUIMode` servizio). Vedi [Ignorare le impostazioni dell’interfaccia per l’editor](#uioverridesfortheeditor).

## Configurazione dell’interfaccia utente predefinita per la tua istanza {#configuring-the-default-ui-for-your-instance}

Un amministratore di sistema può configurare l’interfaccia utente visualizzata all’avvio e all’accesso utilizzando [Mappatura radice](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

Questo valore può essere ignorato dalle impostazioni predefinite dell’utente o dalle impostazioni della sessione.
