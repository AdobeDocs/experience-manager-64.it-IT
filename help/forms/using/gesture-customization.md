---
title: Personalizzazione dei movimenti
seo-title: Gesture customization
description: Personalizzare i gesti sull’app AEM Forms
seo-description: Customize the gestures on your AEM Forms app
uuid: 117e0e21-66bd-42f1-879c-6c1443991974
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 747d13d3-e7cc-4aa1-bcc8-4b57157e71ed
exl-id: 238410e0-1623-49dc-b2fc-b5b2d5fb362b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# Personalizzazione dei movimenti {#gesture-customization}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi personalizzare i gesti dell’app AEM Forms per fornire un metodo distinto di interazione con l’app. Ad esempio, è possibile aggiungere nuovi gesti per aprire o chiudere un&#39;attività o un punto iniziale.

## Personalizzazione dei gesti nell’app AEM Forms {#to-customize-gestures-in-aem-forms-app}

Nell’app AEM Forms, lo scorrimento a sinistra apre una nuova attività o un punto iniziale mentre lo scorrimento a destra non fa nulla. L’esempio seguente fornisce passaggi per aprire una nuova attività o un punto iniziale sull’esecuzione dei gesti con scorrimento rapido a destra nell’app AEM Forms.

1. Apri il progetto.

   * Per iOS, apri `Capture.xcodeproj` in Xcode
   * Per Android, apri il progetto Android in Eclipse.
   * Per Windows, apri `MWSWindows.sln` in Visual Studio.

1. Passa alla cartella delle visualizzazioni e apri le `task.js` file da modificare.

   * In Xcode, passa alla **Cattura > www > wsmobile > js > runtime > visualizzazioni** cartella.
   * In Eclipse, passa alla **risorse > www > wsmobile > js > runtime > visualizzazioni** cartella.
   * In Visual Studio, passare alla **MWSWindows > www > wsmobile > js > runtime > visualizzazioni** cartella.

   >[!NOTE]
   >
   >Il file task.js contiene la visualizzazione backbone associata a ogni attività o punto iniziale elencato negli elenchi task o Startpoint.

1. In `task.js` , cerca la proprietà events della visualizzazione.

   La proprietà events è una mappa con ogni voce nel formato :

   `"EventName Selector": "Function"`

   Quando si attiva un evento Javascript denominato `EventName`su un elemento HTML specificato da `Selector`, `Function`viene chiamato.

1. Trova

   * &quot;tocca .taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;tocca .taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;tocca .task-content&quot; : &quot;onTaskClick&quot;,

      &quot;tap .last_empty_div&quot; : &quot;onTaskClick&quot;,
   e sostituisci con

   * &quot;swipe.taskContentArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe.taskOpenArea&quot; : &quot;onTaskClick&quot;,

      &quot;swipe.task-content&quot; : &quot;onTaskClick&quot;,

      &quot;swipe.last_empty_div&quot;: &quot;onTaskClick&quot;,


1. Salva e chiudi il `task.js` file.
1. Crea ed esegui l’app AEM Forms. Ora è possibile aprire un utilizzo con scorrimento a sinistra e a destra.

Allo stesso modo, è possibile apportare modifiche in altre viste per diverse combinazioni di gesti, elementi di HTML e funzioni.
