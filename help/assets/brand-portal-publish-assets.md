---
title: Pubblicare cartelle su Brand Portal
description: Scopri come pubblicare e annullare la pubblicazione delle risorse su Brand Portal.
contentOwner: VG
feature: Brand Portal
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 36%

---


# Pubblicare risorse su Brand Portal {#publish-assets-to-brand-portal}

In qualità di amministratore di Adobe Experience Manager (AEM) Assets, puoi pubblicare le risorse nell’istanza di AEM Assets Brand Portal (o pianificare il flusso di lavoro di pubblicazione in una data/ora successiva) per la tua organizzazione. Tuttavia, devi prima configurare AEM Assets con Brand Portal. Per ulteriori dettagli, consulta [Configurare AEM Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Dopo la pubblicazione di una risorsa, questa è disponibile per gli utenti in Brand Portal.

Se apporti modifiche successive alla risorsa originale in AEM Assets, le modifiche non verranno applicate in Brand Portal finché non ripubblichi la risorsa. Questa funzione garantisce che le modifiche in corso d’opera non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

Una volta completata la replica, puoi pubblicare risorse, cartelle e raccolte su Brand Portal. Per pubblicare le risorse su Brand Portal, effettua le seguenti operazioni:

>[!NOTE]
>
>Adobe consiglia di scaglionare la pubblicazione, eseguendola preferibilmente nelle ore non di picco, in modo che AEM Author non utilizzi troppe risorse.

1. Dalla console Assets, passa il puntatore del mouse sulle risorse desiderate e seleziona l’opzione **[!UICONTROL Pubblica]** dalle azioni rapide.

   In alternativa, seleziona le risorse da pubblicare su Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Per pubblicare le risorse su Brand Portal sono disponibili le due opzioni seguenti:
   * [Pubblicare immediatamente le risorse](#publish-now)
   * [Pubblicare le risorse in un secondo momento](#publish-later)

## Pubblicare subito le risorse {#publish-now}

Per pubblicare le risorse selezionate su Brand Portal, effettua una delle seguenti operazioni:

* Dalla barra degli strumenti, seleziona **[!UICONTROL Pubblicazione rapida]**. Dal menu, seleziona **[!UICONTROL Pubblica su Brand Portal]**.

* Dalla barra degli strumenti, seleziona **[!UICONTROL Gestisci pubblicazione]**.

   1. Quindi, da **[!UICONTROL Azione]** seleziona **[!UICONTROL Pubblica su Brand Portal]**, e da **[!UICONTROL Pianificazione]** seleziona **[!UICONTROL Ora]**. Tocca o fai clic su **[!UICONTROL Avanti].**

   2. In **[!UICONTROL Ambito]**, conferma la selezione e tocca o fai clic su **[!UICONTROL Pubblica su Brand Portal]**.

Viene visualizzato un messaggio per informare che le risorse sono state accodate per la pubblicazione su Brand Portal. Accedi all’interfaccia di Brand Portal per visualizzare le risorse pubblicate.

## Pubblicare le risorse in un secondo momento {#publish-later}

Per pianificare la pubblicazione delle risorse su Brand Portal in una data o un’ora successiva:

1. Dopo aver selezionato le risorse o le cartelle da pubblicare, seleziona **[!UICONTROL Gestisci pubblicazione]** dalla barra degli strumenti in alto.
2. Nella pagina **[!UICONTROL Gestisci pubblicazione]**, seleziona **[!UICONTROL Pubblica su Brand Portal]** da **[!UICONTROL Azione]** e seleziona **[!UICONTROL Più tardi]** da **[!UICONTROL Pianificazione]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca o fai clic su **[!UICONTROL Avanti]**.
4. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tocca o fai clic su **[!UICONTROL Avanti]**.
5. Specifica un titolo del flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Tocca o fai clic su **[!UICONTROL Pubblica più tardi]**.

   ![publishworkflow](assets/publishworkflow.png)

Ora accedi a Brand Portal per verificare se le risorse pubblicate sono disponibili nell’interfaccia di Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
