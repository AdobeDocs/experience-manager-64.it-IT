---
title: Pubblicare cartelle su Brand Portal
description: Scopri come pubblicare e annullare la pubblicazione delle cartelle in Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 26%

---

# Pubblicare cartelle su Brand Portal {#publish-folders-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In qualità di amministratore di Adobe Experience Manager Assets, puoi pubblicare risorse e cartelle nel [!DNL Experience Manager Assets Brand Portal] istanza (o pianifica il flusso di lavoro di pubblicazione in una data/ora successiva) per la tua organizzazione. Tuttavia, devi prima integrare [!DNL Experience Manager Assets] con [!DNL Brand Portal]. Per maggiori dettagli, vedi [Configura [!DNL Experience Manager Assets] con Brand Portal](configure-aem-assets-with-brand-portal.md).

Dopo aver pubblicato una risorsa o una cartella, questa è disponibile per gli utenti in Brand Portal.

Se apporti modifiche successive alla risorsa o alla cartella originale in [!DNL Assets], le modifiche vengono applicate in Brand Portal solo dopo aver ripubblicato la risorsa o la cartella. Questa funzione garantisce che le modifiche in corso d’opera non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

## Pubblicare cartelle su Brand Portal {#publish-folders-to-brand-portal-1}

1. Da [!DNL Assets] , passa il puntatore del mouse sulla cartella desiderata e seleziona **[!UICONTROL Pubblica]** dalle azioni rapide.

   In alternativa, seleziona la cartella desiderata e segui i passaggi successivi.

   ![publish2bp](assets/publish2bp.png)

2. **Pubblicare subito le cartelle**

   Per pubblicare le cartelle selezionate su Brand Portal, effettua una delle seguenti operazioni:

   * Dalla barra degli strumenti, seleziona **[!UICONTROL Pubblicazione rapida]**. Dal menu , seleziona **[!UICONTROL Pubblicare su Brand Portal]**.
   * Dalla barra degli strumenti, seleziona **[!UICONTROL Gestisci pubblicazione]**.

3. Poi dal **[!UICONTROL Azione]** select **[!UICONTROL Pubblicare su Brand Portal]** e da **[!UICONTROL Pianificazione]** select **[!UICONTROL Ora]**. Tocca **[!UICONTROL Successivo].**
4. Within **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Pubblicare su Brand Portal]**.

   Viene visualizzato un messaggio per informare che la cartella è stata accodata per la pubblicazione su Brand Portal. Accedi all’interfaccia di Brand Portal per visualizzare la cartella pubblicata.

   **Pubblicare le cartelle in un secondo momento**

   Per pianificare la pubblicazione in Brand Portal del flusso di lavoro delle cartelle di risorse in una data o un’ora successiva:

   1. Dopo aver selezionato le risorse/cartelle da pubblicare, seleziona **[!UICONTROL Gestisci pubblicazione]** dalla barra degli strumenti nella parte superiore.
   2. On **[!UICONTROL Gestisci pubblicazione]** pagina, seleziona **[!UICONTROL Pubblicare su Brand Portal]** da **[!UICONTROL Azione]** e seleziona **[!UICONTROL Più tardi]** da **[!UICONTROL Pianificazione]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca **[!UICONTROL Successivo]**.
   4. Conferma la selezione in **[!UICONTROL Ambito]**. Tocca **[!UICONTROL Successivo]**.
   5. Specifica un titolo del flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Tocca **[!UICONTROL Pubblica più tardi]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Annullare la pubblicazione di cartelle su Brand Portal {#unpublish-folders-from-brand-portal}

Per rimuovere una cartella di risorse pubblicata in Brand Portal, annullane la pubblicazione da [!DNL Experience Manager] Istanza di authoring. Dopo l’annullamento della pubblicazione della cartella originale, la relativa copia non sarà più disponibile per gli utenti di Brand Portal.

È possibile annullare rapidamente la pubblicazione delle cartelle da Brand Portal o pianificarle per una data e un’ora successive. Per annullare la pubblicazione delle cartelle di risorse su Brand Portal:

1. Da [!DNL Assets] interfaccia in [!DNL Experience Manager]  Istanza autore, seleziona la cartella di cui vuoi annullare la pubblicazione.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Gestisci pubblicazione]**.

3. **Annulla pubblicazione da Brand Portal**

   Per annullare rapidamente la pubblicazione della cartella desiderata da Brand Portal:

   1. On **[!UICONTROL Gestisci pubblicazione]** da **[!UICONTROL Azione]** select **[!UICONTROL Annulla pubblicazione da Brand Portal]** e da **[!UICONTROL Pianificazione]** select **[!UICONTROL Ora]**.
   2. Tocca o fai clic su **[!UICONTROL Successivo].**
   3. Within **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Annulla pubblicazione da Brand Portal]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Annulla pubblicazione da Brand Portal in un secondo momento**

   Per pianificare la pubblicazione di una cartella da Brand Portal in una data e un’ora successive:

   1. On **[!UICONTROL Gestisci pubblicazione]** da **[!UICONTROL Azione]** select **[!UICONTROL Annulla pubblicazione da Brand Portal]** e da **[!UICONTROL Pianificazione]** select **[!UICONTROL Più tardi].**
   2. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca **[!UICONTROL Successivo]**.
   3. Within **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Successivo]**.
   4. Specifica una **[!UICONTROL Titolo flusso di lavoro]** sotto **[!UICONTROL Flussi di lavoro]**. Tocca **[!UICONTROL Annulla pubblicazione più tardi].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>La procedura per pubblicare/annullare la pubblicazione di una risorsa su/da Brand Portal è simile a quella per una cartella.
