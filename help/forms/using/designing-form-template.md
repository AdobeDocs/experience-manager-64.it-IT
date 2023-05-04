---
title: Progettazione di modelli di modulo per i moduli HTML5
seo-title: Designing form templates for HTML5 forms
description: AEM Forms offre il rendering del modello di modulo XFA in formato HTML5. I progettisti di moduli possono progettare modelli di modulo utilizzando Designer e utilizzare la funzionalità di rendering di HTML5.
seo-description: AEM Forms offers rendering XFA form template to HTML5 format. Form designers can design form templates using Designer and use the HTML5 rendition capability.
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 4%

---

# Progettazione di modelli di modulo per i moduli HTML5 {#designing-form-templates-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il componente HTML5 forms in AEM offre il rendering del modello di modulo XFA in formato HTML5. I progettisti di moduli possono progettare modelli di modulo utilizzando [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_it) e utilizzare la funzionalità di rendering di HTML5. Questi modelli di modulo, insieme alle relative risorse, possono risiedere AEM archivio, nel file system o essere esposti tramite http. Tuttavia, se si intende gestire i moduli utilizzando Forms Manager, i modelli e le risorse devono trovarsi nell’archivio AEM.

Sebbene i moduli di HTML5 corrispondano in larga misura al comportamento dei PDF forms, esistono alcune funzioni in entrambi i formati che non sono applicabili all’altro formato. Ad esempio, il modo in cui i codici a barre vengono applicati a un modulo PDF in Adobe Reader varia a seconda del modulo Mobile o del modo in cui un modulo viene firmato digitalmente. Per ulteriori informazioni su tali varianti, vedi [Differenziazione delle funzioni tra moduli e PDF forms di HTML5](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Per informazioni sulle funzioni XFA comuni, vedere le best practice e le linee guida seguenti per progettare un modulo che funzioni in entrambi i formati.

## Funzionalità di AEM Forms Designer per HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

### Anteprima HTML {#preview-html}

La scheda Anteprima HTML viene aggiunta in modalità Progettazione per consentire ai progettisti di visualizzare in anteprima i moduli in formato HTML5 durante il processo di progettazione. Per ulteriori informazioni su come abilitare e configurare questa funzionalità in AEM Forms Designer, consulta [Anteprima HTML](/help/forms/using/preview-xdp-forms-html.md).

### Firma scarabocchio {#scribble-signature}

Il target chiave per HTML5 forms è rappresentato dai dispositivi touch. Pertanto, in AEM Forms Designer viene aggiunto un nuovo controllo firma scarabocchio. È possibile fare clic o trascinare e rilasciare il controllo firma a mano libera sul modello di modulo e configurarlo. Viene rappresentato come un campo scarabocchio nel rendering di HTML5 e può essere utilizzato per scarabocchiare la firma sui dispositivi touch. Sui computer desktop, può essere utilizzato come campo scarabocchio utilizzando il controllo del mouse. Per ulteriori informazioni su come utilizzare questa funzione, consulta [Campo di distribuzione XFA](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
