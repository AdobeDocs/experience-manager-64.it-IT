---
title: Progettazione di modelli di modulo per i moduli HTML5
seo-title: Progettazione di modelli di modulo per i moduli HTML5
description: 'AEM Forms offre il rendering del modello di modulo XFA in formato HTML5. I progettisti di moduli possono progettare modelli di modulo utilizzando Designer e utilizzare la funzionalità di rendering HTML5. '
seo-description: 'AEM Forms offre il rendering del modello di modulo XFA in formato HTML5. I progettisti di moduli possono progettare modelli di modulo utilizzando Designer e utilizzare la funzionalità di rendering HTML5. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---


# Progettazione di modelli di modulo per moduli HTML5 {#designing-form-templates-for-html-forms}

Il componente Moduli HTML5 in AEM offre il rendering del modello di modulo XFA in formato HTML5. I progettisti di moduli possono progettare modelli di modulo utilizzando [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) e utilizzare la funzionalità di rendering HTML5. Questi modelli di modulo, insieme alle relative risorse, possono risiedere AEM archivio, nel file system o essere esposti tramite http. Tuttavia, se si intende gestire i moduli utilizzando Forms Manager, i modelli e le risorse devono trovarsi nell’archivio AEM.

Sebbene i moduli HTML5 corrispondano in larga misura al comportamento dei PDF forms, vi sono alcune funzioni in entrambi i formati che non sono applicabili all’altro formato. Ad esempio, il modo in cui i codici a barre vengono applicati a un modulo PDF in Adobe Reader varia a seconda del modulo mobile o del modo in cui un modulo viene firmato digitalmente. Per ulteriori informazioni su tali varianti, vedere [Differenziazione delle funzioni tra i moduli HTML5 e i PDF forms](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Per informazioni sulle funzioni XFA comuni, vedere le best practice e le linee guida seguenti per progettare un modulo che funzioni in entrambi i formati.

## Funzionalità di AEM Forms Designer per Forms HTML5 {#capabilities-in-aem-forms-designer-for-html-forms}

### Anteprima HTML {#preview-html}

La scheda Anteprima HTML viene aggiunta in modalità Progettazione per consentire ai progettisti di visualizzare in anteprima i moduli in formato HTML5 durante il processo di progettazione. Per ulteriori informazioni su come abilitare e configurare questa funzionalità in AEM Forms Designer, consulta [Anteprima HTML](/help/forms/using/preview-xdp-forms-html.md).

### Firma scarabocchio {#scribble-signature}

Il target chiave dei moduli HTML5 è rappresentato dai dispositivi touch. Pertanto, in AEM Forms Designer viene aggiunto un nuovo controllo firma scarabocchio. È possibile fare clic o trascinare e rilasciare il controllo firma a mano libera sul modello di modulo e configurarlo. Viene rappresentato come un campo scarabocchio nel rendering HTML5 e può essere utilizzato per scarabocchiare la firma sui dispositivi touch. Sui computer desktop, può essere utilizzato come campo scarabocchio utilizzando il controllo del mouse. Per ulteriori informazioni su come utilizzare questa funzione, consulta [Campo di distribuzione XFA](/help/forms/using/scribble-signature.md).

![4](assets/4.png)
