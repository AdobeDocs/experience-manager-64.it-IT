---
title: Utilizza Apache Tika per rilevare il tipo MIME delle risorse digitali
description: Abilita Apache Tika per aiutare [!DNL Experience Manager] Assets a rilevare il tipo MIME di risorse dal flusso di contenuto durante l'operazione di caricamento invece che l'estensione del file.
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 4%

---

# Utilizza Apache Tika per rilevare il tipo MIME delle risorse digitali {#detecting-mime-type-of-assets-using-apache-tika}

In genere, Adobe Experience Manager Assets rileva il tipo MIME di risorse caricate dall’estensione del file. Se utilizzi Apache Tika per caricare le risorse, [!DNL Experience Manager] le risorse rilevano il loro tipo MIME dal flusso di contenuto durante l’operazione di caricamento anziché dall’estensione del file.

Questa funzione è disabilitata per impostazione predefinita. Per abilitare la funzione, configura il servizio **Day CQ DAM Mime Type** da Configuration Manager.

>[!NOTE]
>
>Il rilevamento del tipo MIME con la libreria Apache Tika è un’operazione ad alta intensità di risorse.

1. Vai a `https://[AEM_server]:[port]/system/console/configMgr` per aprire la console Web di Configuration Manager.
1. Dall&#39;elenco dei servizi, individua **[!UICONTROL Day CQ DAM Mime Type Service]** e tocca/fai clic sull&#39;icona **[!UICONTROL Modifica]** accanto a essa per aprirla in modalità di modifica.

1. Seleziona l’opzione **[!UICONTROL Rileva MIME dal contenuto]** per abilitare l’analisi delle risorse caricate per determinarne il tipo MIME mentre ignora le estensioni dei file. Per impostazione predefinita, questa opzione è deselezionata.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Tocca o fai clic su **[!UICONTROL Salva]** per salvare le modifiche.
