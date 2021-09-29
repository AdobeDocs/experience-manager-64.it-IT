---
title: Pubblicare raccolte su Brand Portal
description: Scopri come pubblicare e annullare la pubblicazione delle raccolte in Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 22%

---

# Pubblicare raccolte su Brand Portal {#publish-collections-to-brand-portal}

In qualità di amministratore di Adobe Experience Manager Assets, puoi pubblicare le raccolte nell’istanza [!DNL Experience Manager Assets Brand Portal] della tua organizzazione. Tuttavia, devi prima integrare Assets con Brand Portal. Per ulteriori dettagli, consulta [Configurare Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Se apporti modifiche successive alla raccolta originale in Assets, le modifiche non verranno applicate in Brand Portal finché non pubblichi nuovamente la raccolta. Questa caratteristica garantisce che le modifiche in corso di lavorazione non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

>[!NOTE]
>
>I frammenti di contenuto non possono essere pubblicati su Brand Portal. Pertanto, se selezioni frammenti di contenuto su [!DNL Experience Manager] Autore, l&#39;azione **[Pubblica su Brand Portal]** non è disponibile.
>
>Se le raccolte contenenti frammenti di contenuto vengono pubblicate da [!DNL Experience Manager] Autore in Brand Portal, tutti i contenuti della cartella ad eccezione dei frammenti di contenuto vengono replicati nell’interfaccia Brand Portal.

## Pubblicare una raccolta in Brand Portal {#publish-a-collection-to-brand-portal}

1. Nell’interfaccia utente Assets, tocca o fai clic sul logo [!DNL Experience Manager]. Quindi, passa a **[!UICONTROL Risorse > Raccolte]** dalla pagina **[!UICONTROL Navigazione]**.
2. Dalla console Raccolte , seleziona la raccolta da pubblicare in Brand Portal.

   ![select_collection](assets/select_collection.png)

3. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Pubblica in Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Nella finestra di dialogo di conferma, tocca o fai clic su **[!UICONTROL Pubblica]**.
5. Chiudi il messaggio di conferma.
6. Accedi a Brand Portal come amministratore. La raccolta pubblicata è disponibile nella console Raccolte.

   ![publish_collection](assets/published_collection.png)

## Annullare la pubblicazione delle raccolte {#unpublish-collections}

Puoi annullare la pubblicazione delle raccolte pubblicate da Assets in Brand Portal. Dopo aver annullato la pubblicazione della raccolta originale, la relativa copia non è più disponibile per gli utenti Brand Portal.

1. Dalla console Raccolte dell’istanza [!DNL Assets], seleziona la raccolta di cui vuoi annullare la pubblicazione.

   ![select_collection-1](assets/select_collection-1.png)

2. Dalla barra degli strumenti, tocca o fai clic sull&#39;icona **[!UICONTROL Rimuovi da Brand Portal]** .

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Nella finestra di dialogo, tocca o fai clic su **[!UICONTROL Annulla pubblicazione]**.
4. Chiudi il messaggio di conferma. La raccolta viene rimossa dall’interfaccia di Brand Portal.
