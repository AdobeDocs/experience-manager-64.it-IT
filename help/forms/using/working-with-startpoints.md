---
title: Utilizzo dei punti di avvio
seo-title: Utilizzo dei punti di avvio
description: Procedura per utilizzare un processo AEM Forms dal dispositivo mobile definito in Workbench.
seo-description: Procedura per utilizzare un processo AEM Forms dal dispositivo mobile definito in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Utilizzo dei punti di avvio {#working-with-startpoints}

Un startpoint richiama un processo creato in Workbench. È associato a un modulo che richiama il processo al momento dell&#39;invio del modulo. Per informazioni sui processi, consulta [Procedura dettagliata](/help/forms/using/finance-reference-site-walkthrough.md) sul sito Geometrixx Finance.

>[!NOTE]
>
>I termini startpoint, processo di avvio e modulo vengono utilizzati in modo intercambiabile quando si fa riferimento a questo concetto.

Per avviare un processo dall&#39;app AEM Forms, devi disporre di un punto di partenza di tipo **Workspace** nel processo. Inoltre, devi selezionare l&#39;opzione **[!UICONTROL Visibile in Mobile Workspace]** per il punto di avvio.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Avvio di un processo definito in Workbench**

1. Per visualizzare i punti di partenza disponibili nell&#39;app AEM Forms, andate alla schermata [](/help/forms/using/home-screen.md)principale.
1. Nella schermata **[!UICONTROL principale]** , per impostazione predefinita, viene visualizzato l&#39;elenco **[!UICONTROL Tutti i moduli]** .

   Il punto di avvio è associato a un modulo. Toccate il modulo associato all&#39;punto di avvio nell&#39;elenco per aprirlo.

   Viene aperto il modulo associato al punto di avvio.

1. Immettere i dettagli nel modulo **[!UICONTROL Start]** .

   È possibile aggiungere annotazioni a questa attività utilizzando il pulsante [Allegato](/help/forms/using/add-attachments.md) .

1. Dopo aver compilato il modulo, toccare il pulsante **Invia** .

Se l&#39;app è offline, il modulo e i relativi dati vengono salvati nella cartella Posta in uscita.

Se l&#39;app è online, l&#39;attività viene sincronizzata con il server AEM Forms e assegnata all&#39;utente specificato nel processo.

Per utilizzare l&#39;attività nell&#39;elenco delle attività, vedere [Apertura di un&#39;attività](/help/forms/using/open-task.md).
