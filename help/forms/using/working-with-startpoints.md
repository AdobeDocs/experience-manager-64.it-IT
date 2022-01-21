---
title: Utilizzo dei punti iniziali
seo-title: Working with Startpoints
description: Passaggi per lavorare con un processo AEM Forms dal dispositivo mobile definito in Workbench.
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: 977ada5fefe476c7cd2fe1470eb024a517a681d2
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Utilizzo dei punti iniziali {#working-with-startpoints}

Un punto di avvio richiama un processo creato in Workbench. È associato a un modulo che richiama il processo al momento dell’invio del modulo. Vedi [Procedura dettagliata sul sito di riferimento finanziario di Geometrixx](/help/forms/using/finance-reference-site-walkthrough.md) per comprendere i processi.

>[!NOTE]
>
>I termini start point, start process e form vengono utilizzati in modo intercambiabile quando si fa riferimento a questo concetto.

Per avviare un processo dall’app AEM Forms, devi disporre di un punto di partenza di tipo **Area di lavoro** nel tuo processo. Inoltre, è necessario selezionare il **[!UICONTROL Visibile in Workspace mobile]** per il punto iniziale.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Per avviare un processo definito in Workbench**

1. Per visualizzare i punti iniziali disponibili nell’app AEM Forms, passa a [Schermata principale](/help/forms/using/home-screen.md).
1. Sulla **[!UICONTROL Pagina principale]** per impostazione predefinita, la **[!UICONTROL Tutti i Forms]** viene visualizzato l&#39;elenco.

   Il punto iniziale è associato a un modulo. Toccare il modulo associato all’interno dell’elenco per aprirlo.

   Viene visualizzato il modulo associato al punto iniziale.

1. Immetti i dettagli nella **[!UICONTROL Startpoint]** modulo.

   È possibile aggiungere annotazioni a questa attività utilizzando [attacco](/help/forms/using/add-attachments.md) pulsante .

1. Dopo aver compilato il modulo, tocca **Invia** pulsante .

Se l’app è offline, il modulo e i relativi dati vengono salvati nella cartella Posta in uscita.

Se l’app è online, l’attività viene sincronizzata con il server AEM Forms e assegnata all’utente specificato nel processo.

Per utilizzare l&#39;attività nell&#39;elenco delle attività, vedere [Apertura di un’attività](/help/forms/using/open-task.md).
