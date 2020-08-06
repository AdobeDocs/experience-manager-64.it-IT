---
title: Utilizzate Apache Tika per rilevare il tipo MIME delle risorse digitali
description: Abilitate Apache Tika per aiutare  AEM Assets a rilevare il tipo MIME di risorse dal flusso di contenuto durante l’operazione di caricamento invece che l’estensione del file.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 4%

---


# Utilizzate Apache Tika per rilevare il tipo MIME delle risorse digitali {#detecting-mime-type-of-assets-using-apache-tika}

In genere, Risorse Adobe Experience Manager (AEM) rileva il tipo MIME di risorse caricate dall’estensione del file. Se utilizzate Apache Tika per caricare le risorse,  AEM Assets rileva il tipo MIME delle risorse dal flusso di contenuto durante l’operazione di caricamento invece dell’estensione del file.

Questa funzione è disattivata per impostazione predefinita. Per abilitare questa funzione, configura il servizio **Day CQ DAM Mime Type** da Configuration Manager.

>[!NOTE]
>
>Il rilevamento del tipo MIME con la libreria Apache Tika richiede molte risorse.

1. Passate `https://[AEM_server]:[port]/system/console/configMgr` a per aprire la console Web di Configuration Manager.
1. Dall&#39;elenco dei servizi, individua il servizio **[!UICONTROL Day CQ DAM Mime Type Service]** e tocca o fai clic sull&#39;icona **[!UICONTROL Modifica]** accanto ad esso per aprirlo in modalità di modifica.

1. Selezionate l’opzione **[!UICONTROL Rileva MIME dal contenuto]** per abilitare l’analisi delle risorse caricate per determinarne il tipo MIME mentre ignorate le estensioni dei file. Per impostazione predefinita, questa opzione è deselezionata.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Tocca o fai clic su **[!UICONTROL Salva]** per salvare le modifiche.
