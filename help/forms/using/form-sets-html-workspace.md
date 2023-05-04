---
title: Utilizzo dei set di moduli nell’area di lavoro di AEM Forms
seo-title: Working with Formsets in AEM Forms workspace
description: Un set di moduli è una raccolta di moduli di HTML5 raggruppati e presentati come un singolo set di moduli agli utenti finali. Scopri come utilizzare i set di moduli nell’area di lavoro di AEM Forms.
seo-description: A formset is a collection of HTML5 forms grouped and presented as a single set of forms to end users. Learn how you can work with formsets in AEM Forms workspace.
uuid: 77f81465-bd60-4aee-8507-585fe08adb78
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c1793e2e-413c-4b6f-b96b-09e011f06263
exl-id: 4e39f6dd-b7a3-4c6c-be1f-66b9a5743352
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 4%

---

# Utilizzo dei set di moduli nell’area di lavoro di AEM Forms {#working-with-formsets-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Un set di moduli è una raccolta di moduli di HTML5 raggruppati e presentati come un singolo set di moduli agli utenti finali. Quando gli utenti finali iniziano a compilare un set di moduli, passano facilmente da un modulo all’altro. Il set di moduli può quindi essere inviato con un solo clic. Per ulteriori informazioni sui set di moduli e su come configurarli, consulta [Set di moduli in AEM Forms](/help/forms/using/formset-in-aem-forms.md).

AEM Forms Workspace supporta i set di moduli. Con i set di moduli, è possibile raggruppare più moduli relativi a un servizio o a un processo per automatizzare un processo aziendale e presentarli agli utenti finali. In questo caso, gli utenti possono compilare l’intero set come un unico set e non è necessario archiviare, inviare e tenere traccia dei singoli moduli o processi.

## Collegamento di un set di moduli da avviare in un’app dell’area di lavoro di AEM Forms {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Crea il flusso di lavoro del processo aziendale in Workbench. Per ulteriori informazioni, consulta [Aiuto per Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).
1. Dalle proprietà del processo del punto iniziale, seleziona **Utilizzare Una Risorsa CRX** in Presentazione e dati.

   ![1-1](assets/1-1.png)

1. Fai clic su ![navigare](assets/browse.png) (Sfoglia) accanto al percorso della risorsa CRX. Viene visualizzata la finestra di dialogo Seleziona risorsa modulo .

   ![2](assets/2.png)

1. Fai clic sul pulsante **Formset** selezionare il set di moduli appropriato dall’elenco, quindi fare clic su **OK**.

1. Distribuisci l&#39;applicazione dopo aver aggiornato altre proprietà di processo rilevanti.

## Utilizzo del set di moduli nell’area di lavoro di AEM Forms {#using-formset-in-nbsp-aem-forms-workspace}

Una volta collegato un set di moduli a un punto iniziale, è possibile richiamare il punto iniziale, come viene richiamato qualsiasi altro punto iniziale, dall’area di lavoro di AEM Forms.

Le operazioni supportate sui moduli impostati tramite l’area di lavoro di AEM Forms sono le seguenti:

* Salva come bozza
* Blocca
* Abbandona
* Invia
* Aggiungi allegati
* Aggiungi note
* Spostarsi tra i moduli di un set di moduli utilizzando i pulsanti Indietro o Avanti

![3-1](assets/3-1.png)

>[!NOTE]
>
>Per migliorare le prestazioni durante lo spostamento dai moduli precedenti e successivi di un set di moduli, tutti i pulsanti dell’area di lavoro (Indietro, Avanti, Salva, Invia e ... (Altro)) sono disabilitati fino al rendering completo del modulo corrispondente.
