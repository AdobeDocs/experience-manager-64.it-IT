---
title: Abilitazione del rilevamento dei duplicati
description: Scopri come abilitare il rilevamento delle risorse duplicate in AEM.
contentOwner: AG
feature: Gestione delle risorse, rapporti sulle risorse
role: Business Practices, Amministratore
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Abilitazione del rilevamento duplicato {#enabling-duplicate-detection}

Se tenti di caricare una risorsa esistente in Adobe Experience Manager (AEM) Assets, la funzione di rilevamento duplicato la identifica come duplicato. Il rilevamento dei duplicati è disattivato per impostazione predefinita. Per abilitare la funzione, procedi come segue:

1. Apri la pagina **[!UICONTROL Configurazione console Web Adobe Experience Manager]** in `https://[server]:[port]/system/console/configMgr`.
1. Modifica la configurazione del servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Seleziona l&#39;opzione **[!UICONTROL Rileva duplicati]** e tocca o fai clic su **[!UICONTROL Salva]**.

   ![Seleziona l’opzione per rilevare i duplicati nel servlet](assets/chlimage_1-377.png)

La funzione di rilevamento duplicati è ora abilitata in AEM Assets. Quando un utente tenta di caricare una risorsa esistente in AEM, il sistema verifica la presenza di un conflitto e lo indica. Le risorse vengono identificate utilizzando l’hash SHA-1 memorizzato in `jcr:content/metadata/dam:sha1`, il che significa che le risorse duplicate vengono rilevate indipendentemente dai nomi dei file.

>[!MORELIKETHIS]
>
>* [Duplicare le risorse nell’archivio esistente (un tutorial tratto da un membro della community)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

