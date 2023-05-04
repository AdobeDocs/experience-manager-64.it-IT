---
title: Configurazione dell’utilità di pianificazione della sincronizzazione
seo-title: Configuring the synchronization scheduler
description: Scopri come migrare e sincronizzare le risorse, configurare la pianificazione della sincronizzazione e utilizzare le cartelle per disporre le risorse.
seo-description: Learn how to migrate and sync assets, configure sync scheduler, and use folders to arrange assets.
uuid: a6445b45-9c1c-4483-a32e-453648c488c5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 2c8cea3c-8d8b-41d4-8ef9-a0ada8f86be6
role: Admin
exl-id: 7f1c4bac-accf-43e4-9439-89c5420d50f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Configurazione dell’utilità di pianificazione della sincronizzazione {#configuring-the-synchronization-scheduler}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per impostazione predefinita, la pianificazione della sincronizzazione viene eseguita dopo ogni 3 minuti per sincronizzare tutte le risorse modificate e aggiornate nell’archivio tramite LiveCycle Workbench 11. Le applicazioni contenenti moduli e risorse sono visibili nell’interfaccia utente di AEM Forms al termine del processo di sincronizzazione.

## Modifica dell&#39;intervallo di pianificazione della sincronizzazione {#change-interval-of-the-synchronization-scheduler}

Esegui i seguenti passaggi per modificare l&#39;intervallo della pianificazione della sincronizzazione:

1. Accedi a AEM Configuration Manager. L’URL di Configuration Manager è `https://[Server]:[Port]/lc/system/console/configMgr`

1. Individua e apri la **ConfigurazioneFormsManager** pacchetto.

1. Specifica un nuovo valore per la **Frequenza pianificazione sincronizzazione** opzione .

   L&#39;unità della frequenza è in minuti. Ad esempio, per configurare la pianificazione da eseguire ogni 60 minuti, specifica 60.

## Sincronizzazione delle risorse {#synchronizing-assets}

È possibile utilizzare **Sincronizzare le risorse dall’archivio** per sincronizzare manualmente le risorse. Per sincronizzare manualmente le risorse, effettua le seguenti operazioni:

1. Accedi ad AEM Forms. L’URL predefinito è `https://[Server]:[Port]/lc/aem/forms/`.

   ![Interfaccia utente di AEM Forms](assets/aem_forms_ui.png)

   **Figura:** *Interfaccia utente di AEM Forms*

1. Fai clic sul pulsante ![aem6forms_sync](assets/aem6forms_sync.png) nella barra degli strumenti. Se non disponi di risorse all’ultimo percorso configurato, la finestra di dialogo viene visualizzata come mostrato di seguito. Fai clic su **Inizio** per avviare la sincronizzazione.

   ![Finestra di dialogo Sincronizzazione](assets/migrate-and-syncronize.png)

   **Figura:** *Finestra di dialogo Sincronizzazione*

## Errore di sincronizzazione della risoluzione dei problemi {#troubleshooting-synchronization-error}

È possibile creare nuove applicazioni nella finestra di progettazione del flusso di lavoro (Workbench LiveCycle).

Se l&#39;applicazione appena creata e una cartella in /content/dam/formsanddocuments hanno lo stesso nome, viene visualizzato un errore &quot;*Una risorsa con lo stesso nome di questa applicazione esiste già a livello principale.*&quot; è registrato.

Per risolvere il conflitto, rinomina l’applicazione e sincronizza manualmente le risorse.

![Conflitti nella finestra di dialogo di sincronizzazione delle risorse](assets/sync-conflict.png)

**Figura:** *Conflitti nella finestra di dialogo di sincronizzazione delle risorse*
