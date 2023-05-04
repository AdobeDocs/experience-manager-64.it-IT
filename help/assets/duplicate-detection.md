---
title: Abilitazione del rilevamento dei duplicati
description: Scopri come abilitare il rilevamento delle risorse duplicate in AEM.
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 4%

---

# Abilitazione del rilevamento dei duplicati {#enabling-duplicate-detection}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Se tenti di caricare una risorsa esistente in Adobe Experience Manager Assets, la funzione di rilevamento duplicato la identifica come duplicato. Il rilevamento dei duplicati è disattivato per impostazione predefinita. Per abilitare la funzione, procedi come segue:

1. Apri **[!UICONTROL Configurazione della console Web di Adobe Experience Manager]** page at `https://[server]:[port]/system/console/configMgr`.
1. Modificare la configurazione del servlet **[!UICONTROL Crea risorsa Day CQ DAM]**.
1. Seleziona la **[!UICONTROL rilevare]** e tocca o fai clic su **[!UICONTROL Salva]**.

   ![Seleziona l’opzione per rilevare i duplicati nel servlet](assets/chlimage_1-377.png)

La funzione di rilevamento duplicati è ora abilitata in [!DNL Experience Manager] Risorse. Quando un utente tenta di caricare una risorsa esistente in AEM, il sistema verifica la presenza di un conflitto e lo indica. Le risorse vengono identificate utilizzando l’hash SHA-1 memorizzato in `jcr:content/metadata/dam:sha1`, il che significa che le risorse duplicate vengono rilevate indipendentemente dai nomi dei file.

>[!MORELIKETHIS]
>
>* [Duplicare le risorse nell’archivio esistente (un tutorial tratto da un membro della community)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

