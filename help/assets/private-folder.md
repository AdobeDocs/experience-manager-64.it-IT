---
title: Condivisione di cartelle private
description: Scopri come creare una cartella privata in Adobe Experience Manager (AEM) Assets e condividerla con altri utenti e assegnare loro vari privilegi.
contentOwner: AG
feature: Collaborazione
role: Professionista
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---


# Condivisione di cartelle private {#private-folder-sharing}

Puoi creare una cartella privata nell’interfaccia utente di Adobe Experience Manager (AEM) Assets disponibile esclusivamente per l’utente. Puoi condividere questa cartella privata con altri utenti e assegnare loro vari privilegi. In base al livello di privilegio assegnato, gli utenti possono eseguire varie attività sulla cartella, ad esempio visualizzare le risorse all’interno della cartella o modificare le risorse.

1. Nella console Risorse, tocca o fai clic su **[!UICONTROL Crea]** nella barra degli strumenti, quindi scegli **[!UICONTROL Cartella]** dal menu.

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. Nella finestra di dialogo **[!UICONTROL Aggiungi cartella]**, immetti un titolo e un nome (facoltativo) per la cartella e seleziona **[!UICONTROL Privato]**.

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. Tocca o fai clic su **[!UICONTROL Crea]**. Nell’interfaccia utente viene creata una cartella privata.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Per condividere la cartella con altri utenti e assegnare loro i privilegi, seleziona la cartella e tocca o fai clic sull’icona **[!UICONTROL Proprietà]** nella barra degli strumenti.

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >La cartella non è visibile ad altri utenti finché non la condividi.

1. Nella pagina Proprietà cartella, seleziona un utente dall&#39;elenco **[!UICONTROL Aggiungi utente]** , assegna un ruolo all&#39;utente nella cartella privata e fai clic su **[!UICONTROL Aggiungi]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Puoi assegnare diversi ruoli, ad esempio Editor, Proprietario o Visualizzatore, all’utente con cui condividi la cartella. Se assegni un ruolo Proprietario all&#39;utente, quest&#39;ultimo dispone dei privilegi di Editor nella cartella. Inoltre, l’utente può condividere la cartella con altri utenti. Se assegni un ruolo Editor, l’utente può modificare le risorse nella tua cartella privata. Se assegni un ruolo Visualizzatore, l’utente può visualizzare solo le risorse presenti nella cartella privata.

1. Fai clic su **[!UICONTROL Salva]**. A seconda del ruolo assegnato, all’utente viene assegnato un set di privilegi sulla cartella privata quando accede ad AEM Assets.
1. Fai clic su **[!UICONTROL Ok]** per chiudere il messaggio di conferma.
1. L’utente con cui condividi la cartella riceve una notifica di condivisione. Accedi ad AEM Assets con le credenziali dell’utente per visualizzare la notifica.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Tocca o fai clic sull’icona Notifica per aprire l’elenco delle notifiche.

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. Tocca o fai clic sulla voce della cartella privata condivisa dall’amministratore per aprire la cartella.

>[!NOTE]
>
>Per poter creare una cartella privata, devi disporre delle autorizzazioni di lettura e modifica ACL per la cartella principale in cui desideri creare una cartella privata. Se non sei un amministratore, queste autorizzazioni non sono abilitate per impostazione predefinita in */content/dam*. In questo caso, prima di cercare di creare cartelle private o visualizzare le impostazioni della cartella, ottieni prima queste autorizzazioni per il tuo ID utente/gruppo.

