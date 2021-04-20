---
title: Pubblicare cartelle su Brand Portal
description: Scopri come pubblicare e annullare la pubblicazione delle cartelle su Brand Portal.
contentOwner: VG
feature: Brand Portal
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 28%

---


# Pubblicare cartelle su Brand Portal {#publish-folders-to-brand-portal}

In qualità di amministratore di Adobe Experience Manager (AEM) Assets, puoi pubblicare risorse e cartelle nell’istanza di AEM Assets Brand Portal (o pianificare il flusso di lavoro di pubblicazione in una data/ora successiva) per la tua organizzazione. Tuttavia, devi prima integrare AEM Assets con Brand Portal. Per ulteriori dettagli, consulta [Configurare AEM Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Dopo aver pubblicato una risorsa o una cartella, questa è disponibile per gli utenti in Brand Portal.

Se apporti modifiche successive alla risorsa o alla cartella originale in AEM Assets, le modifiche non verranno applicate in Brand Portal finché non ripubblichi la risorsa o la cartella. Questa funzione garantisce che le modifiche in corso d’opera non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

## Pubblicare cartelle su Brand Portal {#publish-folders-to-brand-portal-1}

1. Nell’interfaccia di AEM Assets, passa il puntatore del mouse sulla cartella desiderata e seleziona l’opzione **[!UICONTROL Pubblica]** dalle azioni rapide.

   In alternativa, seleziona la cartella desiderata e segui i passaggi successivi.

   ![publish2bp](assets/publish2bp.png)

2. **Pubblicare subito le cartelle**

   Per pubblicare le cartelle selezionate su Brand Portal, effettua una delle seguenti operazioni:

   * Dalla barra degli strumenti, seleziona **[!UICONTROL Pubblicazione rapida]**. Dal menu, seleziona **[!UICONTROL Pubblica su Brand Portal]**.
   * Dalla barra degli strumenti, seleziona **[!UICONTROL Gestisci pubblicazione]**.

3. Quindi, da **[!UICONTROL Azione]** seleziona **[!UICONTROL Pubblica su Brand Portal]**, e da **[!UICONTROL Pianificazione]** seleziona **[!UICONTROL Ora]**. Tocca **[!UICONTROL Avanti].**
4. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Pubblica su Brand Portal]**.

   Viene visualizzato un messaggio per informare che la cartella è stata accodata per la pubblicazione su Brand Portal. Accedi all’interfaccia di Brand Portal per visualizzare la cartella pubblicata.

   **Pubblicare le cartelle in un secondo momento**

   Per pianificare il flusso di lavoro per la pubblicazione su Brand Portal delle cartelle di risorse in una data o un’ora successiva:

   1. Dopo aver selezionato le risorse/cartelle da pubblicare, seleziona **[!UICONTROL Gestisci pubblicazione]** dalla barra degli strumenti in alto.
   2. Nella pagina **[!UICONTROL Gestisci pubblicazione]**, seleziona **[!UICONTROL Pubblica su Brand Portal]** da **[!UICONTROL Azione]** e seleziona **[!UICONTROL Più tardi]** da **[!UICONTROL Pianificazione]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca **[!UICONTROL Avanti]**.
   4. Conferma la selezione in **[!UICONTROL Ambito]**. Tocca **[!UICONTROL Avanti]**.
   5. Specifica un titolo del flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Tocca **[!UICONTROL Pubblica più tardi]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Annullare la pubblicazione di cartelle su Brand Portal {#unpublish-folders-from-brand-portal}

Per rimuovere una cartella di risorse pubblicata su Brand Portal, annullane la pubblicazione dall’istanza di AEM Author. Dopo l’annullamento della pubblicazione della cartella originale, la relativa copia non sarà più disponibile per gli utenti di Brand Portal.

Puoi annullare rapidamente la pubblicazione delle cartelle su Brand Portal oppure programmarle per una data e un’ora successive. Per annullare la pubblicazione delle cartelle di risorse su Brand Portal:

1. Dall’interfaccia di AEM Assets nell’istanza di AEM Author, seleziona la cartella di cui vuoi annullare la pubblicazione.

   ![publish2bp-1](assets/publish2bp-1.png)

2. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Gestisci pubblicazione]**.

3. **Annullare subito la pubblicazione su Brand Portal**

   Per annullare rapidamente la pubblicazione della cartella desiderata su Brand Portal:

   1. Nella pagina **[!UICONTROL Gestisci pubblicazione]**, in **[!UICONTROL Azione]** seleziona **[!UICONTROL Annulla pubblicazione su Brand Portal]** e in **[!UICONTROL Pianificazione]** seleziona **[!UICONTROL Ora]**.
   2. Tocca o fai clic su **[!UICONTROL Avanti].**
   3. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Annulla pubblicazione su Brand Portal]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Annulla pubblicazione su Brand Portal in un secondo momento**

   Per pianificare la pubblicazione di una cartella da Brand Portal in una data e un’ora successive:

   1. Nella pagina **[!UICONTROL Gestisci pubblicazione]**, in **[!UICONTROL Azione]** seleziona **[!UICONTROL Annulla pubblicazione su Brand Portal]** e in **[!UICONTROL Pianificazione]** seleziona **[!UICONTROL Più tardi].**
   2. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca **[!UICONTROL Avanti]**.
   3. In **[!UICONTROL Ambito]**, conferma la selezione e tocca **[!UICONTROL Avanti]**.
   4. Specifica un **[!UICONTROL titolo del flusso di lavoro]** in **[!UICONTROL Flussi di lavoro]**. Tocca **[!UICONTROL Annulla pubblicazione più tardi].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>La procedura per pubblicare/annullare la pubblicazione di una risorsa su/da Brand Portal è simile alla procedura di corresponsing per una cartella.
