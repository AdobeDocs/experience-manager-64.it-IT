---
title: Configurare le restrizioni di caricamento delle risorse
description: Scopri come configurare Risorse Adobe Experience Manager per limitare il tipo di risorse (file) che gli utenti possono caricare.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 31%

---

# Configurare le restrizioni di caricamento delle risorse {#configuring-asset-upload-restrictions}

Puoi configurare Risorse Adobe Experience Manager per limitare il tipo di risorse (file) che gli utenti possono caricare. Questa funzione consente di eliminare la possibilità per gli utenti di caricare le risorse in un formato indesiderato o di caricare file dannosi. Il servizio `Day CQ DAM Asset Upload Restriction` ti consente di controllare il tipo di file che gli utenti possono caricare. Per impostazione predefinita, [!DNL Experience Manager] Assets consente agli utenti di caricare risorse di tutti i tipi MIME. Tuttavia, puoi configurare il servizio per limitare gli utenti a caricare solo file di tipi MIME specifici.

1. Per aprire la console Web di Configuration Manager, accedi a `https://[AEM_server]:[port]/system/console/configMgr`.
1. Apri il servizio **[!UICONTROL Day CQ DAM Asset Upload Restriction]** in modalità Modifica. Per impostazione predefinita, è selezionata l’opzione **Consenti tutto MIME** , che consente agli utenti di caricare file di tutti i tipi MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Per limitare gli utenti al caricamento solo di file di determinati tipi MIME, deseleziona l’opzione **[!UICONTROL Allow all MIME (Consenti tutti i tipi MIME)]** e specifica quelli ammessi nei campi **[!UICONTROL Tipi MIME consentiti (regex)]**, utilizzando le espressioni regolari.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Tocca o fai clic su **[!UICONTROL Salva]** per salvare le modifiche. Se specifichi stringhe MIME per i tipi MIME consentiti, l’operazione di caricamento non riuscirà per qualsiasi risorsa il cui tipo MIME non corrisponde alle stringhe MIME configurate in questi campi.
