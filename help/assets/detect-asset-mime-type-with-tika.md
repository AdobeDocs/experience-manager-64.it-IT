---
title: Utilizza Apache Tika per rilevare il tipo MIME delle risorse digitali
description: Abilita Apache Tika per aiutare AEM Assets a rilevare il tipo MIME di risorse dal flusso di contenuto durante l’operazione di caricamento invece dell’estensione del file.
contentOwner: AG
feature: Metadati, Strumenti per sviluppatori, Gestione risorse
role: Amministratore,Architetto
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 3%

---


# Utilizza Apache Tika per rilevare il tipo MIME delle risorse digitali {#detecting-mime-type-of-assets-using-apache-tika}

In genere, Risorse Adobe Experience Manager (AEM) rileva il tipo MIME di risorse caricate dalla loro estensione di file. Se utilizzi Apache Tika per caricare le risorse, AEM Assets rileva il loro tipo MIME dal flusso di contenuto durante l’operazione di caricamento invece dell’estensione del file.

Questa funzione è disabilitata per impostazione predefinita. Per abilitare la funzione, configura il servizio **Day CQ DAM Mime Type** da Configuration Manager.

>[!NOTE]
>
>Il rilevamento del tipo MIME con la libreria Apache Tika è un’operazione ad alta intensità di risorse.

1. Vai a `https://[AEM_server]:[port]/system/console/configMgr` per aprire la console Web di Configuration Manager.
1. Dall&#39;elenco dei servizi, individua **[!UICONTROL Day CQ DAM Mime Type Service]** e tocca/fai clic sull&#39;icona **[!UICONTROL Modifica]** accanto a essa per aprirla in modalità di modifica.

1. Seleziona l’opzione **[!UICONTROL Rileva MIME dal contenuto]** per abilitare l’analisi delle risorse caricate per determinarne il tipo MIME mentre ignora le estensioni dei file. Per impostazione predefinita, questa opzione è deselezionata.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Tocca o fai clic su **[!UICONTROL Salva]** per salvare le modifiche.
