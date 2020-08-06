---
title: Pubblicare cartelle su Brand Portal
description: Scoprite come pubblicare e annullare la pubblicazione delle risorse in Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: f09853921dec6602952f369982a1563c7e4a9727
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 35%

---


# Pubblicare risorse su Brand Portal {#publish-assets-to-brand-portal}

In qualità di amministratore di Adobe Experience Manager (AEM) Assets, puoi pubblicare le risorse nell’istanza  AEM Assets Brand Portal (o pianificare il flusso di lavoro di pubblicazione in una data/ora successiva) per la tua organizzazione. Tuttavia, è prima necessario configurare  AEM Assets con Brand Portal. Per ulteriori dettagli, consulta [Configurare AEM Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Dopo aver pubblicato una risorsa, questa è disponibile per gli utenti in Brand Portal.

Se apportate modifiche successive alla risorsa originale in  AEM Assets, le modifiche non vengono riportate nel Portale marchio finché non ripubblicate la risorsa. Questa funzione garantisce che le modifiche in corso d’opera non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

Una volta completata la replica, potete pubblicare risorse, cartelle e raccolte in Brand Portal. Per pubblicare le risorse su Brand Portal, effettuate le seguenti operazioni:

>[!NOTE]
>
>Adobe consiglia di scaglionare la pubblicazione, eseguendola preferibilmente nelle ore non di picco, in modo che AEM Author non utilizzi troppe risorse.

1. Dalla console Risorse, passa il mouse sulle risorse desiderate e seleziona l’opzione **[!UICONTROL Pubblica]** dalle azioni rapide.

   In alternativa, selezionate le risorse da pubblicare nel Brand Portal.

   ![publish2bp-2](assets/publish2bp-2.png)

2. Per pubblicare le risorse su Brand Portal, sono disponibili due opzioni:
   * [Pubblicare immediatamente le risorse](#publish-now)
   * [Pubblicare le risorse in un secondo momento](#publish-later)

## Pubblicare subito le risorse {#publish-now}

Per pubblicare le risorse selezionate su Brand Portal, effettua una delle seguenti operazioni:

* Dalla barra degli strumenti, seleziona **[!UICONTROL Pubblicazione rapida]**. Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.

* Dalla barra degli strumenti, seleziona **[!UICONTROL Gestisci pubblicazione]**.

   1. Quindi, dall’ **[!UICONTROL azione]** , selezionate **[!UICONTROL Pubblica su Brand Portal]**, quindi, in **[!UICONTROL Pianificazione]** , selezionate **[!UICONTROL Ora]**. Tap/ click **[!UICONTROL Next].**

   2. In **[!UICONTROL Ambito]**, conferma la selezione e tocca o fai clic su **[!UICONTROL Pubblica su Brand Portal]**.

Viene visualizzato un messaggio per informare che le risorse sono state accodate per la pubblicazione su Brand Portal. Effettuate l’accesso all’interfaccia del Portale marchio per visualizzare le risorse pubblicate.

## Pubblicare le risorse in un secondo momento {#publish-later}

Per pianificare la pubblicazione delle risorse su Brand Portal in una data o un’ora successiva:

1. Dopo aver selezionato le risorse o le cartelle da pubblicare, selezionate **[!UICONTROL Gestisci pubblicazione]** dalla barra degli strumenti nella parte superiore.
2. Nella pagina **[!UICONTROL Gestisci pubblicazione]** , selezionate **[!UICONTROL Pubblica su Brand Portal]** dall’ **[!UICONTROL azione]** e selezionate **[!UICONTROL Più tardi]** da **[!UICONTROL Pianificazione]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tap/ click **[!UICONTROL Next]**.
4. Seleziona un valore per **[!UICONTROL Data di attivazione]** e specifica l’ora. Tap/ click **[!UICONTROL Next]**.
5. Specifica un titolo del flusso di lavoro in **[!UICONTROL Flussi di lavoro]**. Tap/ click **[!UICONTROL Publish Later]**.

   ![publishworkflow](assets/publishworkflow.png)

A questo punto, accedete a Brand Portal per verificare se le risorse pubblicate sono disponibili nell’interfaccia di Brand Portal.

![bp_631_landing_page](assets/bp_landing_page.png)
