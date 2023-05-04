---
title: Utilizzo del salvataggio automatico nell’app AEM Forms
seo-title: Using autosave in AEM Forms app
description: Scopri come utilizzare la funzione di salvataggio automatico nell’app AEM Forms per evitare la perdita di dati.
seo-description: Learn how to use autosave feature in AEM Forms app that lets you avoid data loss.
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
exl-id: 6eb00c31-6806-478a-99d1-55912798ea69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---

# Utilizzo del salvataggio automatico nell’app AEM Forms {#using-autosave-in-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Quando un utente immette dei dati nell’app Adobe Experience Manager Forms, la funzione di salvataggio automatico li salva a intervalli regolari. La funzione di salvataggio automatico nell’app AEM Forms consente di evitare la perdita di dati in caso di chiusura accidentale dell’app.

L’app può chiudersi accidentalmente:

* Se il dispositivo si spegne a causa della batteria scarica
* Se l’utente uccide l’app
* Se si verifica un arresto anomalo imprevisto

Puoi specificare gli intervalli in cui l’app salva i dati immessi.

>[!NOTE]
>
>Selezionare la frequenza di salvataggio automatico in modo giudizioso. Le frequenti operazioni di salvataggio automatico possono avere un impatto notevole sulle prestazioni del dispositivo.

Esegui i seguenti passaggi per utilizzare la funzione di salvataggio automatico nell’app AEM Forms:

1. Accedi all’app e passa a **[!UICONTROL Impostazioni > Generale]**.
1. Nella schermata Generale, utilizza il **[!UICONTROL Frequenza di salvataggio automatico]** per selezionare gli intervalli in cui salvare i dati immessi dall’app.
   [ ![Impostazione della frequenza di salvataggio automatico](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Quando riavvii l&#39;app e accedi con lo stesso utente, ti viene richiesto di ripristinare l&#39;attività con la finestra di dialogo Ripristina attività non salvata. Fai clic su **[!UICONTROL OK]** nella finestra di dialogo Ripristina attività non salvata per riprendere a lavorare con l&#39;attività salvata. Puoi fare clic su **[!UICONTROL Annulla]** per eliminare i dati salvati corrispondenti all&#39;ultimo salvataggio automatico attivato e iniziare a lavorare con una nuova attività.

   Quando fai clic su **[!UICONTROL OK]**, l’attività viene ripristinata con i dati corrispondenti all’ultimo salvataggio automatico attivato prima dell’arresto anomalo dell’app. Include i dati del modulo e tutti gli allegati associati all’attività.
   [ ![Recupero di un&#39;attività&#x200B;](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** Modulo work-in-progress **B.** Applicazione chiusa con forza **C.** App riavviata con la finestra di dialogo Ripristina attività non salvata **D.** Modulo ripristinato con dati originali
