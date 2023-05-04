---
title: Archiviare ed estrarre le risorse digitali per la modifica
description: Scopri come estrarre le risorse per la modifica e archiviarle nuovamente al termine delle modifiche.
contentOwner: AG
feature: Asset Management
role: User
exl-id: 0c79ed42-0acd-426e-8e14-412bb4117585
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 8%

---

# Archiviazione e estrazione dei file in Assets {#check-in-and-check-out-files-in-assets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Risorse Adobe Experience Manager consente di estrarre le risorse per la modifica e di archiviarle nuovamente dopo aver completato le modifiche. Dopo aver estratto una risorsa, puoi modificarla, annotarla, pubblicarla, spostarla o eliminarla. Il ritiro di una risorsa blocca la risorsa. Altri utenti non possono eseguire nessuna di queste operazioni sulla risorsa finché non accedi nuovamente a [!DNL Experience Manager] Risorse. Tuttavia, possono comunque modificare i metadati della risorsa bloccata.

Per poter estrarre o archiviare le risorse, è necessario disporre dell’accesso in scrittura.

Questa funzione consente di impedire ad altri utenti di ignorare le modifiche apportate da un autore, in cui più utenti collaborano alla modifica dei flussi di lavoro tra più team.

## Risorse di estrazione {#checking-out-assets}

1. Dall’interfaccia utente Assets, seleziona la risorsa da estrarre. È inoltre possibile selezionare più risorse da estrarre.

   ![chlimage_1-468](assets/chlimage_1-468.png)

1. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Pagamento]** icona.

   ![chlimage_1-469](assets/chlimage_1-469.png)

   Osserva che il **[!UICONTROL Pagamento]** l&#39;icona passa alla **[!UICONTROL Controllo]** con la serratura aperta.

   ![chlimage_1-470](assets/chlimage_1-470.png)

   Per verificare se altri utenti possono modificare la risorsa estratta, accedi come un altro utente. L’icona Blocca viene visualizzata sulla miniatura della risorsa estratta.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Seleziona la risorsa. Nella barra degli strumenti non sono visualizzate opzioni che consentono di modificare, annotare, pubblicare o eliminare la risorsa.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   Tuttavia, puoi fare clic o toccare il pulsante **[!UICONTROL Visualizza proprietà]** per modificare i metadati della risorsa bloccata.

1. Tocca o fai clic sull’icona Modifica per aprire la risorsa in modalità di modifica.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Modifica la risorsa e salva le modifiche. Ad esempio, ritaglia l’immagine e salva.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   Puoi anche scegliere di annotare o pubblicare la risorsa.

1. Seleziona la risorsa modificata dall’interfaccia utente Assets, quindi tocca o fai clic sull’icona **[!UICONTROL Registra]** della barra degli strumenti.

   ![chlimage_1-475](assets/chlimage_1-475.png)

   La risorsa modificata viene archiviata in [!DNL Assets] ed è disponibile per la modifica ad altri utenti.

## Check-in forzato {#forced-check-in}

Gli amministratori possono archiviare le risorse estratte da altri utenti.

1. Accedi a [!DNL Assets] come amministratore.
1. Dall’interfaccia utente Assets, seleziona una o più risorse sottoposte a Check-Out da altri utenti.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Dalla barra degli strumenti, tocca o fai clic su **[!UICONTROL Blocco versione]** icona. La risorsa viene archiviata ed è disponibile per la modifica ad altri utenti.

   ![chlimage_1-477](assets/chlimage_1-477.png)
