---
title: Utilizzo del salvataggio automatico in  app AEM Forms
seo-title: Utilizzo del salvataggio automatico in  app AEM Forms
description: 'Scoprite come utilizzare la funzione di salvataggio automatico in  app AEM Forms per evitare la perdita di dati. '
seo-description: 'Scoprite come utilizzare la funzione di salvataggio automatico in  app AEM Forms per evitare la perdita di dati. '
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Utilizzo del salvataggio automatico nell&#39;app  AEM Forms {#using-autosave-in-aem-forms-app}

Quando un utente immette dei dati nell&#39;app Adobe Experience Manager Forms , la funzione di salvataggio automatico li salva a intervalli regolari. La funzione di salvataggio automatico nell&#39;app AEM Forms  consente di evitare la perdita di dati in caso di chiusura accidentale dell&#39;app.

L&#39;app può chiudersi accidentalmente:

* Se il dispositivo si spegne a causa della batteria scarica
* Se l&#39;utente uccide l&#39;app
* Se si verifica un arresto anomalo imprevisto

Potete specificare gli intervalli dopo i quali l&#39;app salva i dati immessi.

>[!NOTE]
>
>Selezionare la frequenza di salvataggio automatico con cautela. Le frequenti operazioni di salvataggio automatico possono avere un notevole impatto sulle prestazioni del dispositivo.

Per utilizzare la funzione di salvataggio automatico nell&#39;app  AEM Forms, effettuate le seguenti operazioni:

1. Accedete all&#39;app e andate a **[!UICONTROL Impostazioni > Generale]**.
1. Nella schermata Generale, utilizzate l&#39;opzione **[!UICONTROL Frequenza salvataggio automatico]** per selezionare gli intervalli in cui desiderate che l&#39;app salvi i dati immessi.
   [ ![Impostazione della frequenza di salvataggio automatico](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Quando riavviate l&#39;app ed effettuate l&#39;accesso con lo stesso utente, vi viene richiesto di ripristinare l&#39;attività mediante la finestra di dialogo Ripristina attività non salvata. Fare clic su **[!UICONTROL OK]** nella finestra di dialogo Recupera attività non salvata per riprendere a lavorare con l&#39;attività salvata. È possibile fare clic su **[!UICONTROL Annulla]** per eliminare i dati salvati corrispondenti all&#39;ultimo salvataggio automatico attivato e iniziare a lavorare con una nuova attività.

   Quando fate clic su **[!UICONTROL OK]**, l&#39;attività viene ripristinata con i dati corrispondenti all&#39;ultimo salvataggio automatico attivato prima dell&#39;arresto anomalo dell&#39;app. Include i dati del modulo e tutti gli allegati associati all&#39;attività.
   [ ![Ottenimento di un&#39;attività ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**recuperataA.** A lavoro in corso modulo  **B.** App chiusa forzatamente  **C.** App riavviata con Recover Unsaved Task Dialog  **D.** Form ripristinato con i dati originali

