---
title: Pubblicare raccolte su Brand Portal
description: Scopri come pubblicare e annullare la pubblicazione delle raccolte su Brand Portal.
contentOwner: VG
feature: Brand Portal
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 22%

---


# Pubblicare raccolte su Brand Portal {#publish-collections-to-brand-portal}

In qualità di amministratore di Adobe Experience Manager (AEM) Assets, puoi pubblicare le raccolte nell’istanza di AEM Assets Brand Portal per la tua organizzazione. Tuttavia, devi prima integrare AEM Assets con Brand Portal. Per ulteriori dettagli, consulta [Configurare AEM Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Se apporti modifiche successive alla raccolta originale in AEM Assets, le modifiche non verranno applicate in Brand Portal finché non pubblichi nuovamente la raccolta. Questa caratteristica garantisce che le modifiche in corso di lavorazione non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

>[!NOTE]
>
>I frammenti di contenuto non possono essere pubblicati su Brand Portal. Pertanto, se selezioni frammenti di contenuto su AEM Author, l’azione **[Pubblica su Brand Portal]** non è disponibile.
>
>Se le raccolte contenenti frammenti di contenuto vengono pubblicate da AEM Author a Brand Portal, nell’interfaccia di Brand Portal viene replicato tutto il contenuto della cartella, ad eccezione dei frammenti di contenuto.

## Pubblicare una raccolta su Brand Portal {#publish-a-collection-to-brand-portal}

1. Nell’interfaccia utente di AEM Assets, tocca o fai clic sul logo AEM. Quindi, passa a **[!UICONTROL Risorse > Raccolte]** dalla pagina **[!UICONTROL Navigazione]**.
2. Dalla console Raccolte , seleziona la raccolta da pubblicare su Brand Portal.

   ![select_collection](assets/select_collection.png)

3. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Pubblica su Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Nella finestra di dialogo di conferma, tocca o fai clic su **[!UICONTROL Pubblica]**.
5. Chiudi il messaggio di conferma.
6. Accedi a Brand Portal come amministratore. La raccolta pubblicata è disponibile nella console Raccolte.

   ![publish_collection](assets/published_collection.png)

## Annullare la pubblicazione delle raccolte {#unpublish-collections}

Puoi annullare la pubblicazione delle raccolte pubblicate da AEM Assets su Brand Portal. Dopo aver annullato la pubblicazione della raccolta originale, la relativa copia non è più disponibile per gli utenti di Brand Portal.

1. Dalla console Raccolte dell’istanza AEM Assets, seleziona la raccolta di cui vuoi annullare la pubblicazione.

   ![select_collection-1](assets/select_collection-1.png)

2. Dalla barra degli strumenti, tocca o fai clic sull’icona **[!UICONTROL Rimuovi da Brand Portal]** .

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Nella finestra di dialogo, tocca o fai clic su **[!UICONTROL Annulla pubblicazione]**.
4. Chiudi il messaggio di conferma. La raccolta viene rimossa dall’interfaccia di Brand Portal.
