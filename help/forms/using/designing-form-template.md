---
title: Progettazione di modelli di modulo per moduli HTML5
seo-title: Progettazione di modelli di modulo per moduli HTML5
description: ' AEM Forms offre il rendering del modello di modulo XFA in formato HTML5. I progettisti di moduli possono progettare i modelli di modulo utilizzando Designer e utilizzare la funzionalità di rappresentazione HTML5. '
seo-description: ' AEM Forms offre il rendering del modello di modulo XFA in formato HTML5. I progettisti di moduli possono progettare i modelli di modulo utilizzando Designer e utilizzare la funzionalità di rappresentazione HTML5. '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# Progettazione di modelli di modulo per moduli HTML5 {#designing-form-templates-for-html-forms}

Il componente Moduli HTML5 in AEM offre il rendering del modello di modulo XFA in formato HTML5. I progettisti di moduli possono progettare modelli di modulo utilizzando [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) e utilizzare la funzionalità di rappresentazione HTML5. Questi modelli di modulo, insieme alle relative risorse, possono risiedere AEM repository, nel file system o essere esposti tramite http. Tuttavia, se si intende gestire i moduli utilizzando Forms Manager, i modelli e le risorse devono risiedere nell&#39;archivio AEM.

Sebbene i moduli HTML5 corrispondano in larga misura al comportamento dei PDF forms, alcune funzioni di entrambi i formati non sono applicabili all’altro formato. Ad esempio, il modo in cui i codici a barre vengono applicati a un modulo PDF in  Adobe Reader varia a seconda del modulo Mobile o il modo in cui il modulo viene firmato digitalmente varia anche a seconda dei formati. Per ulteriori informazioni su tali variazioni, vedere Differenza [tra i moduli HTML5 e i PDF forms](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Per le funzioni XFA comuni, vedere le procedure ottimali e le linee guida riportate di seguito per progettare un modulo che funzioni in entrambi i formati.

## Funzionalità in  AEM Forms Designer per Forms HTML5 {#capabilities-in-aem-forms-designer-for-html-forms}

### Anteprima HTML {#preview-html}

La scheda Anteprima HTML viene aggiunta nella modalità Progettazione per i progettisti di moduli per visualizzare in anteprima i moduli in formato HTML5 durante il processo di progettazione. Per ulteriori informazioni su come abilitare e configurare questa funzionalità in  AEM Forms Designer, vedere [Anteprima HTML](/help/forms/using/preview-xdp-forms-html.md).

### Firma scarabocchio {#scribble-signature}

La destinazione chiave per i moduli HTML5 sono i dispositivi touch. Pertanto, in  AEM Forms Designer è stato aggiunto un nuovo controllo firma con script. È possibile fare clic o trascinare e rilasciare il controllo firma script sul modello di modulo e configurarlo. Viene rappresentato come campo di script nella rappresentazione HTML5 e può essere utilizzato per creare script di firma sui dispositivi touch. Sui computer desktop, può essere utilizzato come campo di scripting utilizzando il controllo del mouse. Per ulteriori informazioni sull&#39;utilizzo di questa funzione, vedere Campo [di](/help/forms/using/scribble-signature.md)scorrimento XFA.

![4](assets/4.png)
