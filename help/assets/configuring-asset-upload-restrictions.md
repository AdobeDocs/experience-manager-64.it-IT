---
title: Configurare le restrizioni di caricamento delle risorse
description: Scopri come configurare Risorse Adobe Experience Manager per limitare il tipo di risorse (file) che gli utenti possono caricare.
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 33%

---

# Configurare le restrizioni di caricamento delle risorse {#configuring-asset-upload-restrictions}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi configurare Risorse Adobe Experience Manager per limitare il tipo di risorse (file) che gli utenti possono caricare. Questa funzione consente di eliminare la possibilità per gli utenti di caricare le risorse in un formato indesiderato o di caricare file dannosi. La `Day CQ DAM Asset Upload Restriction` consente di controllare il tipo di file che gli utenti possono caricare. Per impostazione predefinita, [!DNL Experience Manager] Le risorse consentono agli utenti di caricare risorse di tutti i tipi MIME. Tuttavia, puoi configurare il servizio per limitare gli utenti a caricare solo file di tipi MIME specifici.

1. Per aprire la console Web di Configuration Manager, accedere a `https://[AEM_server]:[port]/system/console/configMgr`.
1. Apri **[!UICONTROL Restrizione al caricamento delle risorse DAM del giorno CQ]** in modalità Modifica. Per impostazione predefinita, la **Consenti tutto** , che consente agli utenti di caricare file di tutti i tipi MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Per limitare gli utenti al caricamento solo di file di determinati tipi MIME, deseleziona l’opzione **[!UICONTROL Allow all MIME (Consenti tutti i tipi MIME)]** e specifica quelli ammessi nei campi **[!UICONTROL Tipi MIME consentiti (regex)]**, utilizzando le espressioni regolari.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Tocca o fai clic su **[!UICONTROL Salva]** per salvare le modifiche. Se specifichi stringhe MIME per i tipi MIME consentiti, l’operazione di caricamento non riuscirà per qualsiasi risorsa il cui tipo MIME non corrisponde alle stringhe MIME configurate in questi campi.
