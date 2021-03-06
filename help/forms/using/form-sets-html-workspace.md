---
title: Utilizzo dei set di moduli nell’area di lavoro  AEM Forms
seo-title: Utilizzo dei set di moduli nell’area di lavoro  AEM Forms
description: Un set di moduli è un insieme di moduli HTML5 raggruppati e presentati come un singolo set di moduli agli utenti finali. Scoprite come utilizzare i set di moduli nell'area di lavoro  AEM Forms.
seo-description: Un set di moduli è un insieme di moduli HTML5 raggruppati e presentati come un singolo set di moduli agli utenti finali. Scoprite come utilizzare i set di moduli nell'area di lavoro  AEM Forms.
uuid: 77f81465-bd60-4aee-8507-585fe08adb78
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c1793e2e-413c-4b6f-b96b-09e011f06263
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---


# Utilizzo dei set di moduli nell&#39;area di lavoro  AEM Forms {#working-with-formsets-in-aem-forms-workspace}

Un set di moduli è un insieme di moduli HTML5 raggruppati e presentati come un singolo set di moduli agli utenti finali. Quando gli utenti finali iniziano a compilare un set di moduli, si passa direttamente da un modulo all&#39;altro. Il set di moduli può essere inviato con un solo clic. Per ulteriori informazioni sui set di moduli e su come configurarli, vedere [Set di moduli in  AEM Forms](/help/forms/using/formset-in-aem-forms.md).

&#39;area di lavoro di AEM Forms supporta i set di moduli. Con i formati, è possibile raggruppare più moduli relativi a un servizio o a un processo per automatizzare un processo aziendale e presentarli agli utenti finali. In questo caso, gli utenti possono compilare l&#39;intero set come un unico set e non è necessario archiviare, inviare e tenere traccia dei singoli moduli o processi.

## Associazione di un set di moduli a un punto iniziale in un&#39;app area di lavoro AEM Forms  {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Creare il flusso di lavoro del processo aziendale in Workbench. Per ulteriori informazioni, vedere [Guida di Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).
1. Dalle proprietà del processo del punto di partenza, selezionare **Usa una risorsa CRX** in Presentation &amp; Data.

   ![1-1](assets/1-1.png)

1. Fate clic su ![Sfoglia](assets/browse.png) (Sfoglia) accanto al percorso della risorsa CRX. Viene visualizzata la finestra di dialogo Seleziona risorsa modulo.

   ![2](assets/2.png)

1. Fare clic sulla scheda **Set di moduli**, selezionare il relativo set di moduli dall&#39;elenco, quindi fare clic su **OK**.

1. Distribuire l&#39;applicazione dopo l&#39;aggiornamento di altre proprietà di processo rilevanti.

## Utilizzo di formset &#39;area di lavoro AEM Forms {#using-formset-in-nbsp-aem-forms-workspace}

Una volta che un set di moduli è collegato a un punto di avvio, il punto di avvio può essere invocato, come qualsiasi altro punto di avvio, dall&#39;area di lavoro di AEM Forms .

Le operazioni supportate sui formati impostati tramite l&#39;area di lavoro di  AEM Forms sono:

* Salva come bozza
* Blocca
* Abbandona
* Invia
* Aggiungi allegati
* Aggiungi note
* Spostarsi tra i moduli in un set di moduli utilizzando i pulsanti Indietro e Avanti

![3-1](assets/3-1.png)

>[!NOTE]
>
>Per migliorare le prestazioni durante lo spostamento dai moduli precedenti e successivi in un set di moduli, tutti i pulsanti dell&#39;area di lavoro (Indietro, Avanti, Salva, Invia e ... (Altro)) vengono disattivati fino al completo rendering del modulo corrispondente.

