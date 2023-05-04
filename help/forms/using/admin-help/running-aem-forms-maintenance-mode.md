---
title: Esecuzione di moduli AEM in modalità manutenzione
seo-title: Running AEM forms in maintenance mode
description: La modalità di manutenzione è utile quando si eseguono attività quali l’applicazione di patch a un DSC, l’aggiornamento AEM moduli o l’applicazione di un service pack. Ulteriori informazioni sull’esecuzione AEM moduli in modalità di manutenzione.
seo-description: Maintenance mode is useful when performing tasks such as patching a DSC, upgrading AEM forms, or applying a service pack. Learn more about running AEM forms in maintenance mode.
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
exl-id: 2f56bbc7-5e23-4c84-ac0a-03f0b01150b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 2%

---

# Esecuzione di moduli AEM in modalità manutenzione {#running-aem-forms-in-maintenance-mode}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La modalità di manutenzione è utile quando si eseguono attività quali l’applicazione di patch a un DSC, l’aggiornamento AEM moduli o l’applicazione di un service pack.

Evita di richiamare processi mentre il server è in modalità di manutenzione. Questo è ciò che accade se si richiama un processo mentre il server è in modalità di manutenzione:

* Se il processo è di lunga durata, viene aggiunto al database dei processi, ma non viene avviato. Quando si esce dalla modalità di manutenzione, AEM Forms elabora i processi a lungo termine nella coda, anche se il server è stato riavviato in modalità manutenzione.
* Se il processo è di breve durata, viene elaborato immediatamente.

**Inserire AEM moduli in modalità di manutenzione**

1. In un browser Web, immetti:

   `https://`*[hostname ]*`:`*[porta]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[nome utente amministratore ]*`&password=`*[password]*

   Nella finestra del browser viene visualizzato un messaggio &quot;ora in pausa&quot;.

   >[!NOTE]
   >
   >Se si spegne il server durante la modalità di manutenzione, al riavvio il server sarà ancora in modalità manutenzione. Al termine delle attività di manutenzione, è necessario disattivare la modalità di manutenzione.

**Controllare se AEM moduli sono in esecuzione in modalità manutenzione**

1. In un browser Web, immetti:

   `https://`*[hostname]:[porta ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[nome utente amministratore]* `&password=`*[password ]*

   Lo stato viene visualizzato nella finestra del browser. Lo stato &quot;true&quot; indica che il server è in esecuzione in modalità manutenzione e &quot;false&quot; indica che il server non è in modalità manutenzione.

**Disattivare la modalità di manutenzione**

1. In un browser Web, immetti:

   `https://`*[hostname]:[porta ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[nome utente amministratore]* `&password=`*[password ]*

   Nella finestra del browser viene visualizzato un messaggio di tipo &quot;ora in esecuzione&quot;.
