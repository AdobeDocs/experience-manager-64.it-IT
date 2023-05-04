---
title: Pubblicare cartelle su Brand Portal
description: Scopri come pubblicare e annullare la pubblicazione delle risorse in Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 30%

---

# Pubblicare risorse su Brand Portal {#publish-assets-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In qualità di amministratore di Adobe Experience Manager Assets, puoi pubblicare le risorse nel [!DNL Experience Manager Assets Brand Portal] istanza (o pianifica il flusso di lavoro di pubblicazione in una data/ora successiva) per la tua organizzazione. Tuttavia, devi prima configurare [!DNL Assets] con [!DNL Brand Portal]. Per maggiori dettagli, vedi [Configura [!DNL Assets] con [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md).

Dopo la pubblicazione di una risorsa, questa è disponibile per gli utenti in Brand Portal.

Se apporti modifiche successive alla risorsa originale in [!DNL Assets], le modifiche vengono applicate in Brand Portal solo dopo la ripubblicazione della risorsa. Questa funzione garantisce che le modifiche in corso d’opera non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

Una volta completata la replica, puoi pubblicare risorse, cartelle e raccolte in [!DNL Brand Portal]. Per pubblicare le risorse in Brand Portal, effettua le seguenti operazioni:

>[!NOTE]
>
>L’Adobe consiglia di scaglionare la pubblicazione, preferibilmente nelle ore non di picco, in modo che il [!DNL Experience Manager] l’autore non occupa risorse in eccesso.

1. Dalla console Risorse, passa il puntatore del mouse sulle risorse desiderate e seleziona **[!UICONTROL Pubblica]** dalle azioni rapide.

   In alternativa, seleziona le risorse da pubblicare in Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Per pubblicare le risorse in Brand Portal, sono disponibili le due opzioni seguenti:
   * [Pubblicare immediatamente le risorse](#publish-now)
   * [Pubblicare le risorse in un secondo momento](#publish-later)

## Pubblicare subito le risorse {#publish-now}

Per pubblicare le risorse selezionate su Brand Portal, effettua una delle seguenti operazioni:

* Dalla barra degli strumenti, seleziona **[!UICONTROL Pubblicazione rapida]**. Dal menu , seleziona **[!UICONTROL Pubblicare su Brand Portal]**.

* Dalla barra degli strumenti, seleziona **[!UICONTROL Gestisci pubblicazione]**.

   1. Poi dal **[!UICONTROL Azione]** select **[!UICONTROL Pubblicare su Brand Portal]** e da **[!UICONTROL Pianificazione]** select **[!UICONTROL Ora]**. Tocca o fai clic su **[!UICONTROL Successivo].**

   2. Within **[!UICONTROL Ambito]**, conferma la selezione e tocca o fai clic su **[!UICONTROL Pubblicare su Brand Portal]**.

Viene visualizzato un messaggio per informare che le risorse sono state accodate per la pubblicazione su Brand Portal. Accedi all’interfaccia di Brand Portal per visualizzare le risorse pubblicate.

## Pubblicare le risorse in un secondo momento {#publish-later}

Per pianificare la pubblicazione delle risorse su Brand Portal in una data o un’ora successiva:

1. Dopo aver selezionato le risorse o le cartelle da pubblicare, seleziona **[!UICONTROL Gestisci pubblicazione]** dalla barra degli strumenti nella parte superiore.
2. On **[!UICONTROL Gestisci pubblicazione]** pagina, seleziona **[!UICONTROL Pubblicare su Brand Portal]** da **[!UICONTROL Azione]** e seleziona **[!UICONTROL Più tardi]** da **[!UICONTROL Pianificazione]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca o fai clic su **[!UICONTROL Successivo]**.
4. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca o fai clic su **[!UICONTROL Successivo]**.
5. Specifica un titolo del flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Tocca o fai clic su **[!UICONTROL Pubblica più tardi]**.

   ![publishworkflow](assets/publishworkflow.png)

Ora accedi a Brand Portal per verificare se le risorse pubblicate sono disponibili nell’interfaccia Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
