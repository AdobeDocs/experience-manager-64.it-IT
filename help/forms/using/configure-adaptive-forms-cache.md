---
title: Configurare la cache dei moduli adattivi
seo-title: Configurare la cache dei moduli adattivi
description: 'La cache dei moduli adattivi è progettata appositamente per i moduli adattivi e i documenti. Memorizza in cache moduli adattivi e documenti adattivi allo scopo di ridurre il tempo necessario per eseguire il rendering di un modulo o di un documento adattivo sul client. '
seo-description: 'La cache dei moduli adattivi è progettata appositamente per i moduli adattivi e i documenti. Memorizza in cache moduli adattivi e documenti adattivi allo scopo di ridurre il tempo necessario per eseguire il rendering di un modulo o di un documento adattivo sul client. '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---


# Configurare la cache dei moduli adattivi {#configure-adaptive-forms-cache}

Una cache è un meccanismo per ridurre i tempi di accesso ai dati, ridurre la latenza e migliorare le velocità di input/output (I/O). La cache dei moduli adattivi memorizza solo il contenuto HTML e la struttura JSON di un modulo adattivo senza salvare dati precompilati. Consente di ridurre il tempo necessario per eseguire il rendering di un modulo o di un documento adattivo sul client. È progettato appositamente per i moduli adattivi e supporta anche i documenti adattivi.

>[!NOTE]
>
>Quando si utilizza la cache dei moduli adattivi, utilizza AEM Dispatcher per memorizzare nella cache le librerie client (CSS e JavaScript) di un modulo o di un documento adattivo.

>[!NOTE]
>
>Durante lo sviluppo di componenti personalizzati, sul server utilizzato per lo sviluppo, tieni disabilitata la cache dei moduli adattivi.

## Configura la cache {#configure-the-cache}

Esegui i seguenti passaggi per configurare la cache dei moduli adattivi:

1. Vai AEM gestione della configurazione della console Web all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
1. Fai clic su **Configurazione canale web per moduli adattivi e comunicazioni interattive** per modificare i relativi valori di configurazione.
1. Nella finestra di dialogo modifica valori di configurazione, specifica il numero massimo di moduli o documenti che un’istanza del server AEM Forms può memorizzare nella cache nel campo **Number of Adaptive Forms** . Il valore predefinito è 100.

   >[!NOTE]
   >
   >Per disabilitare la cache, imposta il valore nel campo Numero di Forms adattivo su **0**. La cache viene reimpostata e tutti i moduli e i documenti vengono rimossi dalla cache quando si disabilita o si modifica la configurazione della cache.

   ![Finestra di dialogo di configurazione per la cache HTML dei moduli adattivi](assets/cache-configuration-edit.png)

1. Fai clic su **Salva** per salvare la configurazione.

