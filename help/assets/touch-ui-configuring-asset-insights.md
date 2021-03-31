---
title: Configurazione di Asset Insights
description: Scopri come configurare Asset Insights in AEM Assets.
contentOwner: AG
feature: Informazioni sulla risorsa, rapporti sulle risorse
role: Business Practices, Amministratore
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 11%

---


# Configurazione di Asset Insights {#configuring-asset-insights}

Adobe Experience Manager (AEM) Assets recupera i dati di utilizzo AEM risorse utilizzate da siti Web di terze parti da Adobe Analytics. Per abilitare Asset Insights al recupero di questi dati e alla generazione di informazioni, configura prima la funzione di integrazione con Adobe Analytics.

>[!NOTE]
>
>Gli approfondimenti sono supportati e forniti solo per le immagini.

1. In AEM, fai clic su **[!UICONTROL Strumenti > Risorse]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Fai clic sulla scheda **[!UICONTROL Configurazione approfondimenti]**.
1. Nella procedura guidata, seleziona un centro dati e fornisci le tue credenziali, compreso il nome dell’organizzazione, il nome utente e la password.

   ![chlimage_1-211](assets/insights_config2.png)

1. Tocca o fai clic su **[!UICONTROL Autentica]**.
1. Dopo aver AEM autenticato le credenziali, dall’elenco **[!UICONTROL Suite di rapporti]**, scegli una suite di rapporti Adobe Analytics dalla quale desideri che Asset Insights recuperi i dati. Fate clic su **[!UICONTROL Aggiungi]**.
1. Dopo aver impostato AEM suite di rapporti, tocca o fai clic su **[!UICONTROL Fine]**.

## Tracciamento pagina {#page-tracker}

Dopo aver configurato l’account Analytics, viene generato il codice di tracciamento pagina . Per abilitare Asset Insights a tracciare AEM risorse utilizzate in siti web di terze parti, includi il codice di tracciamento della pagina nel codice del sito web. Utilizza l’utilità Tracciamento pagina in AEM Assets per generare il codice di tracciamento pagina. Per ulteriori informazioni su come includere il codice di tracciamento pagina nelle pagine web di terze parti, consulta [Utilizzo di tracciamento pagina e codice di incorporamento nelle pagine web](touch-ui-using-page-tracker.md).

1. In AEM, fai clic su **[!UICONTROL Strumenti > Risorse]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Nella pagina **[!UICONTROL Navigazione]**, fai clic sulla scheda **[!UICONTROL Tracciamento pagina approfondimenti]**.
1. Fai clic sull&#39;icona **[!UICONTROL Scarica]** per scaricare il codice di tracciamento della pagina.