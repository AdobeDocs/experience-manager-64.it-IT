---
title: Abilitazione e disabilitazione della modalità di backup sicuro
seo-title: Enabling and disabling safe backup mode
description: Nella pagina Impostazioni backup è possibile utilizzare moduli AEM in modalità di backup sicuro, in modo da poter eseguire il backup affidabile del database e della directory GDS (Global Document Storage). Scopri come abilitare e disabilitare la modalità di backup sicuro.
seo-description: On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory. Learn how to enable and disable safe backup mode.
uuid: 2fdeaeaf-e969-40a4-8aee-1f2b627d3942
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fda71e4-78a1-4581-9d02-bf06a75c3bcb
exl-id: 309a8cef-e84d-485b-9a7c-786a93e83c85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 3%

---

# Abilitazione e disabilitazione della modalità di backup sicuro {#enabling-and-disabling-safe-backup-mode}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Nella pagina Impostazioni backup è possibile utilizzare moduli AEM in modalità di backup sicuro, in modo da poter eseguire il backup affidabile del database e della directory GDS (Global Document Storage).

Mentre AEM moduli è in modalità di backup sicuro, funziona normalmente, tranne per il fatto che non rimuove attivamente i file dalla directory GDS.

>[!NOTE]
>
>L&#39;impostazione di questa opzione non effettua il backup del sistema; prepara il sistema per il backup.

## Attiva modalità di backup sicuro {#enable-safe-backup-mode}

1. Nella console di amministrazione, fai clic su Impostazioni > Impostazioni dei sistemi principali > Impostazioni di backup.
1. Nella pagina Impostazioni backup, selezionare Opera in modalità di backup sicuro e fare clic su OK.

>[!NOTE]
>
>Se il sistema è già in esecuzione in modalità di backup sicuro, non verrà creata una nuova prenotazione quando si fa clic su OK.

## Disattiva modalità di backup sicura {#disable-safe-backup-mode}

1. Nella console di amministrazione, fai clic su Impostazioni > Impostazioni dei sistemi principali > Impostazioni di backup.
1. Nella pagina Impostazioni backup deselezionare Attiva in modalità di backup sicuro e fare clic su OK.
