---
title: Controlli di coerenza e di transito
seo-title: Consistency and Traversal Checks
description: Scopri come eseguire controlli di coerenza e di attraversamento.
seo-description: Learn how to perform consistency and traversal checks.
uuid: 0304e378-7c60-4bf5-9052-d01149d2a6df
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: af9a3e9d-194a-42e5-be28-b238e0c1e55e
feature: Configuring
exl-id: 67dfa0f7-24ac-41ae-83c9-3bb1a8656502
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Controlli di coerenza e di transito{#consistency-and-traversal-checks}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Durante l’aggiornamento possono verificarsi problemi a causa di incongruenze nell’area di lavoro. Puoi eseguire un aggiornamento del test per verificare se si tratta di un problema, oppure eseguire i controlli di coerenza come azione preventiva.

Se esegui un aggiornamento del test che non riesce a causa di incongruenze nell’area di lavoro, vedrai voci simili alle seguenti in crx-quickstart/logs/crx/error.log:

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## Eseguire un controllo di coerenza {#perform-a-consistency-check}

Per eseguire un controllo di coerenza, passa alla pagina di amministrazione per JMX Mbean** com.adobe.granite (Repository)**. Dalla schermata principale AEM, vai a:

**Strumenti > Console web > Principale (nella barra dei menu) > JMX > com.adobe.granite (Repository)**

In un&#39;installazione predefinita, si trova qui:  **[|Mostra utente|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

In **Operazioni** nella sezione della pagina sono disponibili due metodi: **`traversalCheck`** e **`consistencyCheck`**. Per eseguire un controllo, fai clic sull’operazione e immetti i parametri desiderati.

![chlimage_1-117](assets/chlimage_1-117.png)
