---
title: Utilizzo di un modulo adattivo in HTML Workspace
seo-title: Using an adaptive form in HTML Workspace
description: Utilizzo di un modulo adattivo in HTML Workspace
seo-description: Using an adaptive form in HTML Workspace
uuid: 1ebe81ae-5c0b-4c07-8cd1-86efdf8415be
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2f514072-81d9-48de-8369-cca94a330f1d
exl-id: 88fa9c80-4eae-4663-a6c8-abbf1921444e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 1%

---

# Utilizzo di un modulo adattivo in HTML Workspace {#using-an-adaptive-form-in-html-workspace}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Forms su JEE consente di utilizzare un modulo adattivo in HTML Workspace.

Poiché è possibile selezionare un file XDP durante la progettazione del processo, è stata aggiunta la possibilità di sfogliare da un modulo adattivo esistente AEM archivio. Questa funzionalità consente al progettista del processo di configurare un modulo adattivo sia nel punto iniziale che in Task.

## Esperienza di progettazione del processo {#process-design-experience}

Esegui le seguenti operazioni per abilitare i moduli adattivi da utilizzare nella progettazione del processo:

* In Assegna attività e Punto iniziale, puoi passare a una risorsa modulo adattivo nell’archivio CRX quando assegni una risorsa modulo a un’attività.
* Nel foglio delle proprietà Assegna attività/Avvia punto di Workbench è possibile nascondere la barra degli strumenti di livello superiore/globale di un modulo adattivo.
* È possibile utilizzare nuovi profili di azione per le azioni Rendering e invio nei moduli adattivi.

### Esportazione e importazione di applicazioni LiveCycli {#livecycle-application-export-and-import}

Poiché i moduli adattivi si trovano nell’archivio AEM, l’esportazione dell’applicazione di LiveCycle contiene solo i riferimenti per i moduli adattivi utilizzati. Pertanto, l&#39;esportazione e l&#39;importazione di applicazioni di LiveCycle è un processo in due fasi. L&#39;applicazione di LiveCycle include le definizioni dei processi e così via. Un pacchetto separato contenente moduli adattivi viene esportato come file ZIP da AEM. Durante l’importazione, l’applicazione di LiveCycle viene importata tramite Workbench e i moduli adattivi vengono importati tramite AEM.

## Esperienza utente del modulo adattivo in HTML Workspace {#user-experience-of-adaptive-form-in-html-workspace}

HTML Workspace offre alcuni controlli specifici per i moduli adattivi, oltre ai controlli disponibili per i moduli mobili. Un utente può aggiungere allegati, salvare, firmare, inviare e spostarsi all’interno dei moduli adattivi in HTML Workspace quando l’utente apre un’attività o un punto iniziale. Di seguito sono riportate le specifiche:

1. Per **allegare **i file utilizzano gli allegati task, come nel caso di Mobile Forms. Qualsiasi pulsante di tipo File allegato del modulo adattivo è nascosto.

1. Per salvare un modulo adattivo, fai clic su **Salva**, come nel caso di Mobile Forms. Qualsiasi pulsante Save type del modulo adattivo è nascosto.

1. Per inviare un modulo adattivo, utilizza il **Invia** azioni di pulsante o di indirizzamento disponibili, come nel caso di Mobile Forms. Qualsiasi pulsante di invio del modulo adattivo è nascosto.

1. **Visibilità globale della barra degli strumenti del modulo adattivo**: Se designer del processo nasconde la barra degli strumenti globale/di primo livello, la barra degli strumenti e i pulsanti non vengono visualizzati nei moduli adattivi.

1. **Controlli di navigazione nell’area di lavoro per Adaptive Forms**: I pulsanti Successivo/Precedente sono disponibili insieme ai pulsanti Salva, Invia e Inoltra azione per un modulo adattivo in HTML Workspace. Fare clic sui pulsanti Successivo/Precedente per spostarsi nei pannelli dei moduli adattivi in HTML Workspace. I pulsanti Successivo/Precedente forniscono una navigazione approfondita, simile ai controlli di navigazione nella visualizzazione Mobile dei moduli adattivi.

1. **Servizi eSign e componente di riepilogo del modulo adattivo**: Il componente Riepilogo non è operativo in HTML Workspace. In altre parole, se un modulo adattivo ha un componente Riepilogo, non è visibile nell’area di lavoro. Invece dell’invio automatico nel componente Progettazione, l’utente dell’area di lavoro fa clic sull’azione Invia o su un percorso in HTML Workspace. Dopo la firma, un documento è visibile come documento firmato piatto. Fai clic su **Invia** oppure un&#39;azione di route per chiudere/completare l&#39;attività o il punto iniziale.

   Il documento firmato viene raccolto dal server dei servizi eSign e il file xml dei dati viene inoltrato al passaggio successivo del processo.

## Passaggi per utilizzare i moduli adattivi nella progettazione del processo {#steps-to-use-adaptive-forms-in-process-design}

1. Apri Adobe Experience Manager Forms Workbench.

1. Vai a **File > Nuovo > Applicazione** oppure utilizzare l&#39;applicazione esistente per creare un&#39;applicazione.

   ![Crea nuova applicazione](assets/create_new_appl.png)

1. Crea un processo o utilizza un processo esistente nell&#39;applicazione.

   ![Crea nuovo processo](assets/create_new_process.png)

1. Crea un punto iniziale o Assegna attività e fai doppio clic su di esso.
1. Sotto la **[!UICONTROL Presentazione e dati]** sezione , seleziona **[!UICONTROL utilizzare una risorsa CRX]** e fai clic sui puntini di sospensione prima della risorsa.

   ![Utilizzare una risorsa CRX](assets/use_crx_asset.png)

1. Seleziona il modulo adattivo creato tramite l’interfaccia utente Gestione risorse e fai clic su **[!UICONTROL OK]**.

   ![Selezionare un modulo adattivo](assets/selecting_form.png)

   >[!NOTE]
   >
   >Per informazioni dettagliate sulla creazione di un modulo adattivo, consulta [Creazione di un modulo adattivo](/help/forms/using/creating-adaptive-form.md).
   >
   >Per informazioni dettagliate sulla creazione di un processo, vedi [Creazione e gestione dei processi](https://help.adobe.com/en_US/AEMForms/6.1/WorkbenchHelp/WS92d06802c76abadb-1cc35bda128261a20dd-7ff7.2.html).
