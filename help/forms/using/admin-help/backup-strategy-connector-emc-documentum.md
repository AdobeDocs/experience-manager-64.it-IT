---
title: Strategia di backup per il connettore per gli utenti EMC Documentum
seo-title: Backup strategy for Connector for EMC Documentum users
description: Verificare come creare una strategia di backup per il connettore per gli utenti EMC Documentum.
seo-description: Check how to create a backup strategy for Connector for EMC Documentum users.
uuid: 5d8a0476-5231-4e1d-96c4-ae3df68e09f0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e83b1a59-a730-4d22-9d58-1c9c38e5d534
exl-id: 933c3903-2040-41f4-b803-4d672ce9a2dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Strategia di backup per il connettore per gli utenti EMC Documentum {#backup-strategy-for-connector-for-emc-documentum-users}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Se è installato Connector for EMC Documentum, oltre alle istruzioni contenute in questo capitolo, la strategia di backup e ripristino deve includere il backup (o il ripristino) del computer in cui è installato il rispettivo sistema ECM. (consultare la documentazione di ECM Documentum).

Eseguire il backup dell’ambiente AEM forms utilizzando l’archivio ECM ed eseguendo le seguenti operazioni:

* Eseguire il backup AEM moduli seguendo le istruzioni descritte in questo documento.
* Eseguire il backup del sistema ECM Documentum seguendo le istruzioni contenute in [Backup di EMC Documentum Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#back-up-the-emc-documentum-content-server).

Ripristinare l’ambiente AEM moduli utilizzando l’archivio ECM ed eseguendo le seguenti operazioni:

* Ripristinare i rispettivi sistemi ECM seguendo le istruzioni contenute in [Ripristino di EMC Documentum Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#restore-the-emc-documentum-content-server).
* Ripristinare AEM moduli seguendo le istruzioni descritte in questo documento.
