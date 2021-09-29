---
title: Abilitazione del rilevamento dei duplicati
description: Scopri come abilitare il rilevamento delle risorse duplicate in AEM.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Abilitazione del rilevamento dei duplicati {#enabling-duplicate-detection}

Se tenti di caricare una risorsa esistente in Adobe Experience Manager Assets, la funzione di rilevamento duplicato la identifica come duplicato. Il rilevamento dei duplicati è disattivato per impostazione predefinita. Per abilitare la funzione, procedi come segue:

1. Apri la pagina **[!UICONTROL Configurazione della console Web Adobe Experience Manager]** in `https://[server]:[port]/system/console/configMgr`.
1. Modifica la configurazione del servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Seleziona l&#39;opzione **[!UICONTROL Rileva duplicati]** e tocca o fai clic su **[!UICONTROL Salva]**.

   ![Seleziona l’opzione per rilevare i duplicati nel servlet](assets/chlimage_1-377.png)

La funzione di rilevamento duplicati è ora abilitata nelle risorse [!DNL Experience Manager] . Quando un utente tenta di caricare una risorsa esistente in AEM, il sistema verifica la presenza di un conflitto e lo indica. Le risorse vengono identificate utilizzando l’hash SHA-1 memorizzato in `jcr:content/metadata/dam:sha1`, il che significa che le risorse duplicate vengono rilevate indipendentemente dai nomi dei file.

>[!MORELIKETHIS]
>
>* [Duplicare le risorse nell’archivio esistente (un tutorial tratto da un membro della community)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

