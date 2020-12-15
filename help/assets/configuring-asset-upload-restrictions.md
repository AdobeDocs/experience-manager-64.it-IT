---
title: Configurare le restrizioni di caricamento delle risorse
description: Scoprite come configurare Risorse Adobe Experience Manager (AEM) per limitare il tipo di risorse (file) che gli utenti possono caricare.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 31%

---


# Configurare le limitazioni di caricamento delle risorse {#configuring-asset-upload-restrictions}

Potete configurare Risorse Adobe Experience Manager (AEM) per limitare il tipo di risorse (file) che gli utenti possono caricare. Questa funzione consente di eliminare la possibilità per gli utenti di caricare risorse in un formato indesiderato o qualsiasi file dannoso. Il servizio `Day CQ DAM Asset Upload Restriction` consente di controllare il tipo di file che gli utenti possono caricare. Per impostazione predefinita,  AEM Assets consente agli utenti di caricare risorse di tutti i tipi MIME. Tuttavia, potete configurare il servizio per limitare gli utenti al caricamento di file di tipi MIME specifici.

1. Per aprire la console Web di Configuration Manager, accedere a `https://[AEM_server]:[port]/system/console/configMgr`.
1. Aprite il servizio **[!UICONTROL Giorno CQ DAM Asset Restriction]** in modalità di modifica. Per impostazione predefinita, è selezionata l&#39;opzione **Consenti tutto MIME**, che consente agli utenti di caricare file di tutti i tipi MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Per limitare gli utenti al caricamento solo di file di determinati tipi MIME, deseleziona l’opzione **[!UICONTROL Allow all MIME (Consenti tutti i tipi MIME)]** e specifica quelli ammessi nei campi **[!UICONTROL Tipi MIME consentiti (regex)]**, utilizzando le espressioni regolari.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Tocca o fai clic su **[!UICONTROL Salva]** per salvare le modifiche. Se specifichi stringhe MIME per i tipi MIME consentiti, l’operazione di caricamento non riuscirà per qualsiasi risorsa il cui tipo MIME non corrisponde alle stringhe MIME configurate in questi campi.
