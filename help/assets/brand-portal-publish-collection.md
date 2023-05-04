---
title: Pubblicare raccolte su Brand Portal
description: Scopri come pubblicare e annullare la pubblicazione delle raccolte in Brand Portal.
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 22%

---

# Pubblicare raccolte su Brand Portal {#publish-collections-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In qualità di amministratore di Adobe Experience Manager Assets, puoi pubblicare le raccolte nel [!DNL Experience Manager Assets Brand Portal] istanza per la tua organizzazione. Tuttavia, devi prima integrare Assets con Brand Portal. Per ulteriori dettagli, consulta [Configurare Assets con Brand Portal](configure-aem-assets-with-brand-portal.md).

Se apporti modifiche successive alla raccolta originale in Assets, le modifiche non verranno applicate in Brand Portal finché non pubblichi nuovamente la raccolta. Questa caratteristica garantisce che le modifiche in corso di lavorazione non siano disponibili in Brand Portal. Solo le modifiche approvate pubblicate da un amministratore sono infatti disponibili in Brand Portal.

>[!NOTE]
>
>I frammenti di contenuto non possono essere pubblicati su Brand Portal. Pertanto, se selezioni frammenti di contenuto su [!DNL Experience Manager] Autore, quindi **[Pubblicare su Brand Portal]** azione non disponibile.
>
>Se le raccolte contenenti frammenti di contenuto sono pubblicate da [!DNL Experience Manager] Esegui l’authoring in Brand Portal e tutti i contenuti della cartella, eccetto i frammenti di contenuto, vengono replicati nell’interfaccia Brand Portal.

## Pubblicare una raccolta in Brand Portal {#publish-a-collection-to-brand-portal}

1. Nell’interfaccia utente Assets, tocca o fai clic sul pulsante [!DNL Experience Manager] logo. Quindi, vai a **[!UICONTROL Risorse > Raccolte]** dal **[!UICONTROL Navigazione]** pagina.
2. Dalla console Raccolte , seleziona la raccolta da pubblicare in Brand Portal.

   ![select_collection](assets/select_collection.png)

3. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Pubblicare su Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. Nella finestra di dialogo di conferma, tocca o fai clic su **[!UICONTROL Pubblica]**.
5. Chiudi il messaggio di conferma.
6. Accedi a Brand Portal come amministratore. La raccolta pubblicata è disponibile nella console Raccolte.

   ![publish_collection](assets/published_collection.png)

## Annullare la pubblicazione delle raccolte {#unpublish-collections}

Puoi annullare la pubblicazione delle raccolte pubblicate da Assets in Brand Portal. Dopo aver annullato la pubblicazione della raccolta originale, la relativa copia non è più disponibile per gli utenti Brand Portal.

1. Dalla console Raccolte della [!DNL Assets] e seleziona la raccolta di cui desideri annullare la pubblicazione.

   ![select_collection-1](assets/select_collection-1.png)

2. Dalla barra degli strumenti, tocca o fai clic sul pulsante **[!UICONTROL Rimuovi da Brand Portal]** icona.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. Nella finestra di dialogo, tocca o fai clic su **[!UICONTROL Annulla pubblicazione]**.
4. Chiudi il messaggio di conferma. La raccolta viene rimossa dall’interfaccia di Brand Portal.
