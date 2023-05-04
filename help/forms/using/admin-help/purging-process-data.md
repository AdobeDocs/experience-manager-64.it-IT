---
title: Rimozione dei dati del processo
seo-title: Purging process data
description: I dati del processo generati quando viene richiamato un processo di lunga durata possono diventare troppo grandi, con conseguente riduzione delle prestazioni dei moduli AEM e utilizzo di spazio su disco non necessario. Scopri come eliminare i dati del processo.
seo-description: Process data that is generated when a long-lived process is invoked can become too large, resulting in lower AEM forms performance and the use of unnecessary disk space. See how you can purge process data.
uuid: 2f04452c-71c6-452c-88c2-7560d35e7dec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3157bb92-4b07-40f2-be4c-8f5807f9a380
exl-id: ecedde63-abbb-4e69-901e-1e4b7a59f539
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 3%

---

# Rimozione dei dati del processo {#purging-process-data}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I dati del processo generati quando viene richiamato un processo di lunga durata possono diventare troppo grandi, con conseguente riduzione delle prestazioni dei moduli AEM e utilizzo di spazio su disco non necessario. È buona prassi eliminare i dati del processo quando i record non sono più necessari. AEM forms offre diversi metodi per eliminare i dati del processo:

* È possibile utilizzare la console di amministrazione per eseguire una rimozione una tantum di record obsoleti relativi a processi di lunga durata o per pianificare le pulizie automatiche regolari. (Vedi [Eliminare i record dal database di Job Manager](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)
* È possibile utilizzare l’API Java AEM forms e l’API del servizio Web per eliminare programmaticamente i dati di processo relativi a processi longevi. (Vedi &quot;Rimozione dei dati del processo&quot; in [Programmazione con moduli AEM](https://www.adobe.com/go/learn_aemforms_programming_63).)
* Utilizza lo strumento di eliminazione del processo per eliminare i processi in base al nome del processo e ad altri parametri. Per ulteriori informazioni, vedere il file readme dello strumento di eliminazione del processo, situato in *[root di aem_forms]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt.
