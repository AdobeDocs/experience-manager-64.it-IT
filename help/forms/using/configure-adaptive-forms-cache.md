---
title: Configurare la cache dei moduli adattivi
seo-title: Configurare la cache dei moduli adattivi
description: 'La cache dei moduli adattivi è stata progettata specificamente per i moduli e i documenti adattivi. Memorizza nella cache moduli adattivi e documenti adattivi allo scopo di ridurre il tempo necessario per eseguire il rendering di un modulo o di un documento adattivo sul client. '
seo-description: 'La cache dei moduli adattivi è stata progettata specificamente per i moduli e i documenti adattivi. Memorizza nella cache moduli adattivi e documenti adattivi allo scopo di ridurre il tempo necessario per eseguire il rendering di un modulo o di un documento adattivo sul client. '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---


# Configurare la cache dei moduli adattivi {#configure-adaptive-forms-cache}

Una cache è un meccanismo per ridurre i tempi di accesso ai dati, ridurre la latenza e migliorare le velocità di ingresso/uscita (I/O). La cache dei moduli adattivi memorizza solo il contenuto HTML e la struttura JSON di un modulo adattivo senza salvare i dati precompilati. Consente di ridurre il tempo necessario per eseguire il rendering di un modulo o di un documento adattivo sul client. È progettata specificamente per i moduli adattivi e supporta anche i documenti adattivi.

>[!NOTE]
>
>Quando si utilizza la cache dei moduli adattivi, utilizzare il dispatcher AEM per memorizzare nella cache le librerie client (CSS e JavaScript) di un modulo o di un documento adattivo.

>[!NOTE]
>
>Durante lo sviluppo di componenti personalizzati, sul server utilizzato per lo sviluppo, mantenere disattivata la cache dei moduli adattivi.

## Configurare la cache {#configure-the-cache}

Per configurare la cache dei moduli adattivi, effettuate le seguenti operazioni:

1. Andate AEM console Web Configuration Manager all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
1. Fare clic su **Configurazione canale Web per moduli adattivi e comunicazioni interattive** per modificarne i valori di configurazione.
1. Nella finestra di dialogo Modifica valori configurazione, specificare il numero massimo di moduli o documenti che un&#39;istanza del server AEM Forms  può memorizzare nella cache nel campo **Numero di Forms adattivo**. Il valore predefinito è 100.

   >[!NOTE]
   >
   >Per disattivare la cache, impostate il valore nel campo Numero di Forms adattivo su **0**. La cache viene reimpostata e tutti i moduli e i documenti vengono rimossi dalla cache quando si disabilita o si modifica la configurazione della cache.

   ![Finestra di dialogo di configurazione per la cache HTML dei moduli adattivi](assets/cache-configuration-edit.png)

1. Fare clic su **Salva** per salvare la configurazione.

