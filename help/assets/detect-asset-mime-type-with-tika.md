---
title: Utilizza Apache Tika per rilevare il tipo MIME delle risorse digitali
description: Abilitare Apache Tika ad aiutare [!DNL Experience Manager] Le risorse rilevano il tipo MIME di risorse dal flusso di contenuto durante l’operazione di caricamento invece che dall’estensione del file.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 6%

---

# Utilizza Apache Tika per rilevare il tipo MIME delle risorse digitali {#detecting-mime-type-of-assets-using-apache-tika}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In genere, Adobe Experience Manager Assets rileva il tipo MIME di risorse caricate dall’estensione del file. Se utilizzi Apache Tika per caricare le risorse, [!DNL Experience Manager] Le risorse rilevano il tipo MIME dal flusso di contenuto durante l’operazione di caricamento invece dell’estensione del file.

Questa funzione è disabilitata per impostazione predefinita. Per abilitare la funzione, configura la **Tipo MIME Day CQ** da Configuration Manager.

>[!NOTE]
>
>Il rilevamento del tipo MIME con la libreria Apache Tika è un’operazione ad alta intensità di risorse.

1. Vai a `https://[AEM_server]:[port]/system/console/configMgr` per aprire la console Web di Configuration Manager.
1. Dall’elenco dei servizi, individua **[!UICONTROL Servizio Day CQ DAM Mime Type]** e tocca o fai clic sul pulsante **[!UICONTROL Modifica]** accanto a essa per aprirla in modalità Modifica.

1. Seleziona la **[!UICONTROL Rileva MIME dal contenuto]** per abilitare l’analisi delle risorse caricate per determinare il loro tipo MIME mentre si ignorano le estensioni dei file. Per impostazione predefinita, questa opzione è deselezionata.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Tocca o fai clic su **[!UICONTROL Salva]** per salvare le modifiche.
