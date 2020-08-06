---
title: Abilitazione del rilevamento duplicato
description: Scoprite come attivare il rilevamento di risorse duplicate in AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26e860cd513d70d748f872e2ce445a042d075bc6
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# Abilitazione del rilevamento duplicato {#enabling-duplicate-detection}

Se tentate di caricare una risorsa esistente in Adobe Experience Manager (AEM) Assets, la funzione di rilevamento duplicato la identifica come duplicato. Per impostazione predefinita, il rilevamento di duplicati è disabilitato. Per attivare la funzione, effettuare le seguenti operazioni:

1. Aprite la pagina Configurazione **[!UICONTROL console Web di]** Adobe Experience Manager all&#39;indirizzo `https://[server]:[port]/system/console/configMgr`.
1. Modificate la configurazione per il servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selezionate l’opzione **[!UICONTROL Rileva duplicato]** e toccate o fate clic su **[!UICONTROL Salva]**.

   ![Selezionate l’opzione Rileva duplicato nel servlet](assets/chlimage_1-377.png)

La funzione Rileva duplicato è ora abilitata in  AEM Assets. Quando un utente tenta di caricare una risorsa esistente in AEM, il sistema cerca eventuali conflitti e la segnala. Le risorse vengono identificate tramite hash SHA-1 memorizzato in `jcr:content/metadata/dam:sha1`, il che significa che le risorse duplicate vengono rilevate indipendentemente dal nome del file.

>[!MORELIKETHIS]
>
>* [Duplicare le risorse presenti nell&#39;archivio esistente (esercitazione di un membro della community)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

