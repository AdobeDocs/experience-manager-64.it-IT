---
title: Pubblicare cartelle su Brand Portal
description: Scopri come pubblicare e annullare la pubblicazione delle cartelle in Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 27%

---

# Pubblicare cartelle su Brand Portal {#publish-folders-to-brand-portal}

In qualità di amministratore di Adobe Experience Manager Assets, puoi pubblicare risorse e cartelle nell’ istanza [!DNL Experience Manager Assets Brand Portal] (o pianificare il flusso di lavoro di pubblicazione in una data/ora successiva) per la tua organizzazione. Tuttavia, devi prima integrare [!DNL Experience Manager Assets] con [!DNL Brand Portal]. Per informazioni dettagliate, consulta [Configurare [!DNL Experience Manager Assets] con Brand Portal](configure-aem-assets-with-brand-portal.md).

Dopo aver pubblicato una risorsa o una cartella, questa è disponibile per gli utenti in Brand Portal.

Se apporti modifiche successive alla risorsa o alla cartella originale in [!DNL Assets], le modifiche non verranno applicate in Brand Portal finché non ripubblichi la risorsa o la cartella. Questa funzione garantisce che le modifiche in corso d’opera non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

## Pubblicare cartelle su Brand Portal {#publish-folders-to-brand-portal-1}

1. Nell’interfaccia [!DNL Assets] , passa il cursore del mouse sulla cartella desiderata e seleziona l’opzione **[!UICONTROL Pubblica]** dalle azioni rapide.

   In alternativa, seleziona la cartella desiderata e segui i passaggi successivi.

   ![publish2bp](assets/publish2bp.png)

2. **Pubblicare subito le cartelle**

   Per pubblicare le cartelle selezionate su Brand Portal, effettua una delle seguenti operazioni:

   * Dalla barra degli strumenti, seleziona **[!UICONTROL Pubblicazione rapida]**. Dal menu, seleziona **[!UICONTROL Pubblica in Brand Portal]**.
   * Dalla barra degli strumenti, seleziona **[!UICONTROL Gestisci pubblicazione]**.

3. Quindi, da **[!UICONTROL Azione]** seleziona **[!UICONTROL Pubblica in Brand Portal]**, e da **[!UICONTROL Pianificazione]** seleziona **[!UICONTROL Ora]**. Tocca **[!UICONTROL Avanti].**
4. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Pubblica in Brand Portal]**.

   Viene visualizzato un messaggio per informare che la cartella è stata accodata per la pubblicazione su Brand Portal. Accedi all’interfaccia di Brand Portal per visualizzare la cartella pubblicata.

   **Pubblicare le cartelle in un secondo momento**

   Per pianificare la pubblicazione in Brand Portal del flusso di lavoro delle cartelle di risorse in una data o un’ora successiva:

   1. Dopo aver selezionato le risorse/cartelle da pubblicare, seleziona **[!UICONTROL Gestisci pubblicazione]** dalla barra degli strumenti in alto.
   2. Nella pagina **[!UICONTROL Gestisci pubblicazione]**, seleziona **[!UICONTROL Pubblica in Brand Portal]** da **[!UICONTROL Azione]** e seleziona **[!UICONTROL Più tardi]** da **[!UICONTROL Pianificazione]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca **[!UICONTROL Avanti]**.
   4. Conferma la selezione in **[!UICONTROL Ambito]**. Tocca **[!UICONTROL Avanti]**.
   5. Specifica un titolo del flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Tocca **[!UICONTROL Pubblica più tardi]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Annullare la pubblicazione di cartelle su Brand Portal {#unpublish-folders-from-brand-portal}

Per rimuovere una cartella di risorse pubblicata in Brand Portal, annullane la pubblicazione dall’istanza di authoring [!DNL Experience Manager]. Dopo l’annullamento della pubblicazione della cartella originale, la relativa copia non sarà più disponibile per gli utenti di Brand Portal.

È possibile annullare rapidamente la pubblicazione delle cartelle da Brand Portal o pianificarle per una data e un’ora successive. Per annullare la pubblicazione delle cartelle di risorse su Brand Portal:

1. Dall’interfaccia [!DNL Assets] nell’istanza di authoring [!DNL Experience Manager], seleziona la cartella di cui vuoi annullare la pubblicazione.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Gestisci pubblicazione]**.

3. **Annulla pubblicazione da Brand Portal**

   Per annullare rapidamente la pubblicazione della cartella desiderata da Brand Portal:

   1. Nella pagina **[!UICONTROL Gestisci pubblicazione]**, in **[!UICONTROL Azione]** seleziona **[!UICONTROL Annulla pubblicazione da Brand Portal]** e in **[!UICONTROL Pianificazione]** seleziona **[!UICONTROL Ora]**.
   2. Tocca o fai clic su **[!UICONTROL Avanti].**
   3. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Annulla pubblicazione da Brand Portal]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Annulla pubblicazione da Brand Portal in un secondo momento**

   Per pianificare la pubblicazione di una cartella da Brand Portal in una data e un’ora successive:

   1. Nella pagina **[!UICONTROL Gestisci pubblicazione]**, in **[!UICONTROL Azione]** seleziona **[!UICONTROL Annulla pubblicazione da Brand Portal]** e in **[!UICONTROL Pianificazione]** seleziona **[!UICONTROL Più tardi].**
   2. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca **[!UICONTROL Avanti]**.
   3. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Avanti]**.
   4. Specifica un **[!UICONTROL titolo del flusso di lavoro]** in **[!UICONTROL Flussi di lavoro]**. Tocca **[!UICONTROL Annulla pubblicazione più tardi].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>La procedura per pubblicare/annullare la pubblicazione di una risorsa su/da Brand Portal è simile a quella per una cartella.
