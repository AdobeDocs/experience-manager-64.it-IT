---
title: Configurazione di Assets Insights
description: Scopri come configurare Assets Insights in [!DNL Experience Manager] Risorse.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 12%

---

# Configurazione di Assets Insights {#configuring-asset-insights}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Risorse Adobe Experience Manager recupera i dati di utilizzo [!DNL Experience Manager] risorse utilizzate da siti web di terze parti di Adobe Analytics. Per abilitare Assets Insights al recupero di questi dati e alla generazione di informazioni, configura prima la funzione da integrare con Adobe Analytics.

>[!NOTE]
>
>Gli approfondimenti sono supportati e forniti solo per le immagini.

1. In AEM, fai clic su **[!UICONTROL Strumenti > Risorse]**.

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. Fai clic sulla scheda **[!UICONTROL Configurazione approfondimenti]**.
1. Nella procedura guidata, seleziona un centro dati e fornisci le tue credenziali, compreso il nome dell’organizzazione, il nome utente e la password.

   ![chlimage_1-211](assets/insights_config2.png)

1. Tocca o fai clic su **[!UICONTROL Autentica]**.
1. Dopo [!DNL Experience Manager] autentica le credenziali dal **[!UICONTROL Suite di rapporti]** scegli una suite di rapporti Adobe Analytics dalla quale desideri che Assets Insights recuperi i dati. Fai clic su **[!UICONTROL Aggiungi]**.
1. Dopo [!DNL Experience Manager] imposta la suite di rapporti, tocca o fai clic su **[!UICONTROL Fine]**.

## Tracciamento pagina {#page-tracker}

Dopo aver configurato l’account Analytics, viene generato il codice di tracciamento pagina . Per abilitare Asset Insights al tracciamento [!DNL Experience Manager] risorse utilizzate in siti web di terze parti, includi il codice di tracciamento della pagina nel codice del sito web. Utilizzare l&#39;utilità di tracciamento pagina in [!DNL Experience Manager] Risorse per generare il codice di tracciamento della pagina. Per ulteriori informazioni su come includere il codice di tracciamento pagina nelle pagine web di terze parti, vedi [Utilizzo del tracciamento pagina e del codice da incorporare nelle pagine web](touch-ui-using-page-tracker.md).

1. In AEM, fai clic su **[!UICONTROL Strumenti > Risorse]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. Nella pagina **[!UICONTROL Navigazione]**, fai clic sulla scheda **[!UICONTROL Tracciamento pagina approfondimenti]**.
1. Fai clic sul pulsante **[!UICONTROL Scarica]** per scaricare il codice di tracciamento della pagina.
