---
title: Configurazione di Assets Insights
description: Scopri come configurare Assets Insights in [!DNL Experience Manager] Assets.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 12%

---

# Configurazione di Assets Insights {#configuring-asset-insights}

Adobe Experience Manager Assets recupera i dati di utilizzo relativi alle risorse [!DNL Experience Manager] utilizzate da siti Web di terze parti da Adobe Analytics. Per abilitare Assets Insights al recupero di questi dati e alla generazione di informazioni, configura prima la funzione da integrare con Adobe Analytics.

>[!NOTE]
>
>Gli approfondimenti sono supportati e forniti solo per le immagini.

1. In AEM, fai clic su **[!UICONTROL Strumenti > Risorse]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Fai clic sulla scheda **[!UICONTROL Configurazione approfondimenti]**.
1. Nella procedura guidata, seleziona un centro dati e fornisci le tue credenziali, compreso il nome dell’organizzazione, il nome utente e la password.

   ![chlimage_1-211](assets/insights_config2.png)

1. Tocca o fai clic su **[!UICONTROL Autentica]**.
1. Dopo che [!DNL Experience Manager] autentica le credenziali, dall’elenco **[!UICONTROL Suite di rapporti]** scegli una suite di rapporti Adobe Analytics dalla quale desideri che Assets Insights recuperi i dati. Fate clic su **[!UICONTROL Aggiungi]**.
1. Dopo che [!DNL Experience Manager] imposta la suite di rapporti, tocca o fai clic su **[!UICONTROL Fine]**.

## Tracciamento pagina {#page-tracker}

Dopo aver configurato l’account Analytics, viene generato il codice di tracciamento pagina . Per abilitare Asset Insights a tenere traccia delle risorse [!DNL Experience Manager] utilizzate in siti web di terze parti, includi il codice di tracciamento della pagina nel codice del sito web. Utilizza l’utilità Tracciamento pagina in [!DNL Experience Manager] Risorse per generare il codice di tracciamento pagina. Per ulteriori informazioni su come includere il codice di tracciamento pagina nelle pagine web di terze parti, consulta [Utilizzo di tracciamento pagina e codice di incorporamento nelle pagine web](touch-ui-using-page-tracker.md).

1. In AEM, fai clic su **[!UICONTROL Strumenti > Risorse]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Nella pagina **[!UICONTROL Navigazione]**, fai clic sulla scheda **[!UICONTROL Tracciamento pagina approfondimenti]**.
1. Fai clic sull&#39;icona **[!UICONTROL Scarica]** per scaricare il codice di tracciamento della pagina.
