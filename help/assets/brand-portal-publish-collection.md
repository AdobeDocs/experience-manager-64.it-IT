---
title: Pubblicare raccolte in Brand Portal
description: Scoprite come pubblicare e annullare la pubblicazione delle raccolte in Brand Portal.
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1

---


# Publish collections to Brand Portal {#publish-collections-to-brand-portal}

In qualità di amministratore di Risorse Adobe Experience Manager (AEM), potete pubblicare le raccolte nell&#39;istanza del Portale marchio di AEM Assets per la vostra organizzazione. Tuttavia, devi prima integrare AEM Assets con il Brand Portal. Per informazioni dettagliate, consultate [Configurare AEM Assets con il Portale](configure-aem-assets-with-brand-portal.md)marchio.

Se apportate modifiche successive alla raccolta originale in Risorse AEM, le modifiche non vengono riportate nel Portale marchio finché non pubblicate nuovamente la raccolta. Questa caratteristica garantisce che le modifiche in corso di lavoro non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono disponibili in Brand Portal.

>[!NOTE]
>
>I frammenti di contenuto non possono essere pubblicati sul Brand Portal. Pertanto, se selezionate frammenti di contenuto in AEM Author, l&#39;azione **[Pubblica su Brand Portal]** non è disponibile.
>
>Se le raccolte contenenti frammenti di contenuto vengono pubblicate da AEM Author a Brand Portal, tutto il contenuto della cartella tranne i frammenti di contenuto viene replicato nell&#39;interfaccia Brand Portal.

## Pubblicare una raccolta in Brand Portal {#publish-a-collection-to-brand-portal}

1. Nell’interfaccia utente di Risorse AEM, tocca o fai clic sul logo AEM. Quindi, andate a **[!UICONTROL Risorse > Raccolte]** dalla pagina di **[!UICONTROL navigazione]** .
2. Dalla console Raccolte, selezionate la raccolta da pubblicare nel portale dei marchi.

   ![select_collection](assets/select_collection.png)

3. Dalla barra degli strumenti, toccate o fate clic su **[!UICONTROL Pubblica sul portale]** del marchio.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Nella finestra di dialogo di conferma, toccate o fate clic su **[!UICONTROL Pubblica]**.
5. Chiudi il messaggio di conferma.
6. Accedete a Brand Portal come amministratore. La raccolta pubblicata è disponibile nella console Raccolte.

   ![published_collection](assets/published_collection.png)

## Annullamento della pubblicazione delle raccolte {#unpublish-collections}

Potete annullare la pubblicazione delle raccolte pubblicate da AEM Assets al Brand Portal. Dopo aver annullato la pubblicazione della raccolta originale, la relativa copia non è più disponibile per gli utenti di Brand Portal.

1. Dalla console Raccolte dell’istanza di Risorse AEM e selezionate la raccolta da annullare la pubblicazione.

   ![select_collection-1](assets/select_collection-1.png)

2. Dalla barra degli strumenti, toccate o fate clic sull&#39;icona **[!UICONTROL Rimuovi da Brand Portal]** .

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Nella finestra di dialogo, toccate o fate clic su **[!UICONTROL Annulla pubblicazione]**.
4. Chiudi il messaggio di conferma. La raccolta viene rimossa dall&#39;interfaccia Brand Portal.
