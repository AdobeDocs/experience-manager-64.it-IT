---
title: Pubblicare le cartelle su Brand Portal
description: Scoprite come pubblicare e annullare la pubblicazione delle cartelle in Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1

---


# Publish folders to Brand Portal {#publish-folders-to-brand-portal}

In qualità di amministratore Risorse Adobe Experience Manager (AEM), puoi pubblicare risorse e cartelle nell’istanza del Portale del marchio di AEM Assets (o pianificare il flusso di lavoro di pubblicazione in una data/ora successiva) per la tua organizzazione. Tuttavia, devi prima integrare AEM Assets con il Brand Portal. Per informazioni dettagliate, consultate [Configurare AEM Assets con il Portale](configure-aem-assets-with-brand-portal.md)marchio.

Dopo aver pubblicato una risorsa o una cartella, questa è disponibile per gli utenti in Brand Portal.

Se apportate modifiche successive alla risorsa o alla cartella originale in Risorse AEM, le modifiche non vengono riportate nel Portale marchio fino a quando non ripubblicate la risorsa o la cartella. Questa funzione garantisce che le modifiche in corso non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono disponibili in Brand Portal.

## Publish folders to Brand Portal {#publish-folders-to-brand-portal-1}

1. Dall’interfaccia di Risorse AEM, passa il mouse sulla cartella desiderata e seleziona l’opzione **[!UICONTROL Pubblica]** dalle azioni rapide.

   In alternativa, selezionate la cartella desiderata e seguite i passaggi successivi.

   ![publish2bp](assets/publish2bp.png)

2. **Pubblica le cartelle ora**

   Per pubblicare le cartelle selezionate in Brand Portal, effettuate una delle seguenti operazioni:

   * Dalla barra degli strumenti, selezionate Pubblicazione **** rapida. Dal menu, selezionate **[!UICONTROL Pubblica su Brand Portal]**.
   * Dalla barra degli strumenti, selezionate **[!UICONTROL Gestisci pubblicazione]**.

3. Quindi, dall’ **[!UICONTROL azione]** , selezionate **[!UICONTROL Pubblica su Brand Portal]**, quindi, in **[!UICONTROL Pianificazione]** , selezionate **[!UICONTROL Ora]**. Toccate **[!UICONTROL Avanti].**
4. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Pubblica sul portale]** marchio.

   Viene visualizzato un messaggio che informa che la cartella è stata messa in coda per la pubblicazione sul Brand Portal. Accedete all’interfaccia Brand Portal per visualizzare la cartella pubblicata.

   **Pubblicare le cartelle in un secondo momento**

   Per pianificare il flusso di lavoro di pubblicazione in Brand Portal delle cartelle di risorse in una data o ora successiva:

   1. Dopo aver selezionato le risorse/cartelle da pubblicare, selezionate **[!UICONTROL Gestisci pubblicazione]** dalla barra degli strumenti nella parte superiore.
   2. Nella pagina **[!UICONTROL Gestisci pubblicazione]** , selezionate **[!UICONTROL Pubblica su Brand Portal]** dall’ **[!UICONTROL azione]** e selezionate **[!UICONTROL Più tardi]** da **[!UICONTROL Pianificazione]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Selezionate una data **[!UICONTROL di]** attivazione e specificate l&#39;ora. Toccate **[!UICONTROL Avanti]**.
   4. Conferma la selezione nell’ **[!UICONTROL ambito]**. Toccate **[!UICONTROL Avanti]**.
   5. Specificate un titolo del flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Toccate **[!UICONTROL Pubblica più tardi]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Unpublish folders from Brand Portal {#unpublish-folders-from-brand-portal}

Potete rimuovere qualsiasi cartella di risorse pubblicata nel Portale marchio annullandone la pubblicazione dall’istanza di AEM Author. Dopo l’annullamento della pubblicazione della cartella originale, la relativa copia non sarà più disponibile per gli utenti di Brand Portal.

Potete annullare la pubblicazione delle cartelle da Brand Portal in modo rapido oppure pianificarle in un secondo momento. Per annullare la pubblicazione delle cartelle di risorse da Brand Portal:

1. Dall’interfaccia di AEM Assets nell’istanza di AEM Author, selezionate la cartella da annullare la pubblicazione.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Dalla barra degli strumenti, toccate o fate clic su **[!UICONTROL Gestisci pubblicazione]**.

3. **Annulla pubblicazione da Brand Portal**

   Per annullare rapidamente la pubblicazione della cartella desiderata da Brand Portal:

   1. Nella pagina **[!UICONTROL Gestisci pubblicazione]** , in **[!UICONTROL Azione]** , selezionate **[!UICONTROL Annulla pubblicazione da Brand Portal]** e in **[!UICONTROL Pianificazione]** selezionate **[!UICONTROL Ora]**.
   2. Tap/ click **[!UICONTROL Next].**
   3. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Annulla pubblicazione da Brand Portal]**.
   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Annulla pubblicazione da Brand Portal in un secondo momento**

   Per pianificare la pubblicazione di una cartella da Brand Portal a una data e un’ora successive:

   1. Nella pagina **[!UICONTROL Gestisci pubblicazione]** , in **[!UICONTROL Azione]** , selezionate **[!UICONTROL Annulla pubblicazione da Brand Portal]** e in **[!UICONTROL Pianificazione]** selezionate **[!UICONTROL Più tardi].**
   2. Selezionate una data **[!UICONTROL di]** attivazione e specificate l’ora. Toccate **[!UICONTROL Avanti]**.
   3. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Avanti]**.
   4. Specificate un titolo **** Flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Toccate **[!UICONTROL Annulla pubblicazione più tardi].**

      ![flussi di lavoro non pubblicati](assets/unpublishworkflows.png)


>[!NOTE]
>
>La procedura per pubblicare/annullare la pubblicazione di una risorsa in/da Brand Portal è simile alla procedura corrispondente per una cartella.
