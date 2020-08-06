---
title: Pubblicare cartelle su Brand Portal
description: Scoprite come pubblicare e annullare la pubblicazione delle cartelle in Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 27%

---


# Pubblicare cartelle su Brand Portal {#publish-folders-to-brand-portal}

In qualità di amministratore di Adobe Experience Manager (AEM) Assets, puoi pubblicare risorse e cartelle nell’istanza  AEM Assets Brand Portal (o pianificare il flusso di lavoro di pubblicazione in una data/ora successiva) per la tua organizzazione. Tuttavia, è prima necessario integrare  AEM Assets con il Portale marchio. Per ulteriori dettagli, consulta [Configurare AEM Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Dopo aver pubblicato una risorsa o una cartella, questa è disponibile per gli utenti in Brand Portal.

Se apportate modifiche successive alla risorsa o alla cartella originale in  AEM Assets, le modifiche non verranno applicate al Portale marchio finché non ripubblicate la risorsa o la cartella. Questa funzione garantisce che le modifiche in corso d’opera non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

## Pubblicare cartelle su Brand Portal {#publish-folders-to-brand-portal-1}

1. Dall’interfaccia AEM Assets , passate il mouse sulla cartella desiderata e selezionate l’opzione **[!UICONTROL Pubblica]** dalle azioni rapide.

   In alternativa, selezionate la cartella desiderata e seguite i passaggi successivi.

   ![publish2bp](assets/publish2bp.png)

2. **Pubblicare subito le cartelle**

   Per pubblicare le cartelle selezionate su Brand Portal, effettua una delle seguenti operazioni:

   * Dalla barra degli strumenti, seleziona **[!UICONTROL Pubblicazione rapida]**. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.
   * Dalla barra degli strumenti, seleziona **[!UICONTROL Gestisci pubblicazione]**.

3. Quindi, dall’ **[!UICONTROL azione]** , selezionate **[!UICONTROL Pubblica su Brand Portal]**, quindi, in **[!UICONTROL Pianificazione]** , selezionate **[!UICONTROL Ora]**. Toccate **[!UICONTROL Avanti].**
4. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Pubblica sul portale]** marchio.

   Viene visualizzato un messaggio per informare che la cartella è stata accodata per la pubblicazione su Brand Portal. Accedete all’interfaccia Brand Portal per visualizzare la cartella pubblicata.

   **Pubblicare le cartelle in un secondo momento**

   Per pianificare il flusso di lavoro di pubblicazione in Brand Portal delle cartelle di risorse in una data o ora successiva:

   1. Dopo aver selezionato le risorse/cartelle da pubblicare, selezionate **[!UICONTROL Gestisci pubblicazione]** dalla barra degli strumenti nella parte superiore.
   2. Nella pagina **[!UICONTROL Gestisci pubblicazione]** , selezionate **[!UICONTROL Pubblica su Brand Portal]** dall’ **[!UICONTROL azione]** e selezionate **[!UICONTROL Più tardi]** da **[!UICONTROL Pianificazione]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Toccate **[!UICONTROL Avanti]**.
   4. Conferma la selezione in **[!UICONTROL Ambito]**. Toccate **[!UICONTROL Avanti]**.
   5. Specifica un titolo del flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Toccate **[!UICONTROL Pubblica più tardi]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Annullare la pubblicazione di cartelle su Brand Portal {#unpublish-folders-from-brand-portal}

Potete rimuovere qualsiasi cartella di risorse pubblicata nel Portale marchio annullandone la pubblicazione dall’istanza di AEM Author. Dopo l’annullamento della pubblicazione della cartella originale, la relativa copia non sarà più disponibile per gli utenti di Brand Portal.

Potete annullare la pubblicazione delle cartelle da Brand Portal in modo rapido oppure pianificarle in un secondo momento. Per annullare la pubblicazione delle cartelle di risorse su Brand Portal:

1. Dall&#39;interfaccia AEM Assets  nell&#39;istanza di AEM Author, selezionate la cartella da annullare la pubblicazione.

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
   2. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Toccate **[!UICONTROL Avanti]**.
   3. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Avanti]**.
   4. Specify a **[!UICONTROL Workflow title]** under **[!UICONTROL Workflows]**. Toccate **[!UICONTROL Annulla pubblicazione più tardi].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>La procedura per pubblicare/annullare la pubblicazione di una risorsa in/da Brand Portal è simile alla procedura corrispondente per una cartella.
