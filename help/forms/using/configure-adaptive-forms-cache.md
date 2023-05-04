---
title: Configurare la cache dei moduli adattivi
seo-title: Configure adaptive forms cache
description: La cache dei moduli adattivi è progettata appositamente per i moduli adattivi e i documenti. Memorizza in cache moduli adattivi e documenti adattivi allo scopo di ridurre il tempo necessario per eseguire il rendering di un modulo o di un documento adattivo sul client.
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 3%

---

# Configurare la cache dei moduli adattivi {#configure-adaptive-forms-cache}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Una cache è un meccanismo per ridurre i tempi di accesso ai dati, ridurre la latenza e migliorare le velocità di input/output (I/O). La cache dei moduli adattivi memorizza solo il contenuto HTML e la struttura JSON di un modulo adattivo senza salvare dati precompilati. Consente di ridurre il tempo necessario per eseguire il rendering di un modulo o di un documento adattivo sul client. È progettato appositamente per i moduli adattivi e supporta anche i documenti adattivi.

>[!NOTE]
>
>Quando si utilizza la cache dei moduli adattivi, utilizza AEM Dispatcher per memorizzare nella cache le librerie client (CSS e JavaScript) di un modulo o di un documento adattivo.

>[!NOTE]
>
>Durante lo sviluppo di componenti personalizzati, sul server utilizzato per lo sviluppo, tieni disabilitata la cache dei moduli adattivi.

## Configurare la cache {#configure-the-cache}

Esegui i seguenti passaggi per configurare la cache dei moduli adattivi:

1. Vai AEM gestione della configurazione della console Web all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
1. Fai clic su **Configurazione del canale web per moduli adattivi e comunicazioni interattive** per modificare i valori di configurazione.
1. Nella finestra di dialogo modifica valori di configurazione, specifica il numero massimo di moduli o documenti che un’istanza del server AEM Forms può memorizzare nella cache nel **Numero di Forms adattivi** campo . Il valore predefinito è 100.

   >[!NOTE]
   >
   >Per disabilitare la cache, imposta il valore nel campo Numero di Forms adattivo su **0**. La cache viene reimpostata e tutti i moduli e i documenti vengono rimossi dalla cache quando si disabilita o si modifica la configurazione della cache.

   ![Finestra di dialogo di configurazione per la cache HTML dei moduli adattivi](assets/cache-configuration-edit.png)

1. Fai clic su **Salva** per salvare la configurazione.
