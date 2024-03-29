---
title: Gestione programmatica di PreferencesNodes
seo-title: Programmatically managing the PreferencesNodes
description: Utilizza l’API del servizio Preferenze Manager (Java) per gestire in modo programmatico i nodi delle preferenze.
seo-description: Use the Preferences Manager Service API (Java) to programmatically manage the Preferences Nodes.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: d580b32c-a344-4a8c-bd61-0949da76d981
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Gestione programmatica dei nodi delle preferenze {#programmatically-managing-the-preferencesnodes}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In questo argomento viene descritto come utilizzare l’API del servizio Preferenze Manager (Java) per gestire in modo programmatico i nodi Preferenze.

Puoi modificare manualmente le impostazioni di configurazione dall’interfaccia utente amministratore. Per modificare le opzioni, passa a `Home>Settings>User Management> Configuration>Manual Configuration`. Importa `config.xml` dopo aver apportato le modifiche, noterai che tutte le modifiche tranne quelle apportate al nodo `/Adobe/Adobe Experience Manager Forms/Config/UM persist` sono persi. L&#39;anteprima di Importazione ed esportazione di User Management non supporta la modifica delle impostazioni di configurazione per altri componenti. Ora, queste modifiche possono essere effettuate utilizzando `PreferencesManagerServiceClient` API.

**Riepilogo dei passaggi** Per gestire in modo programmatico i nodi delle preferenze, esegui le seguenti operazioni:

1. Includi file di progetto.
1. Creare un client PreferencesManagerService
1. Richiamare le operazioni di ruolo o autorizzazione appropriate

**Includi file di progetto**

Includi i file necessari nel progetto di sviluppo. Se stai creando un&#39;applicazione client utilizzando Java, includi i file JAR necessari. Se utilizzi i servizi web, assicurati di includere i file proxy.

**Creare un client PreferencesManagerService**

Prima di eseguire un&#39;operazione di User Management PreferencesManagerService a livello di programmazione, è necessario creare un client PreferencesManagerService. Con l&#39;API Java questo si ottiene creando un oggetto PreferencesManagerServiceClient.

**Richiamare le operazioni di ruolo o autorizzazione appropriate**

Dopo aver creato il client di servizio, puoi richiamare le operazioni di Gestione preferenze. Il client di servizi ti consente di leggere e impostare le autorizzazioni.
