---
title: Salvataggio di un'attività o di un modulo come bozza
seo-title: Saving a task or form as a draft
description: Passaggi per salvare una bozza di copia di un’attività o di un modulo nell’app AEM Forms
seo-description: Steps to save a draft copy of a task or a form in the AEM Forms app
uuid: 1192d2c2-05a4-4a96-9015-e56111aa2646
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 9950288c-b5a2-4945-afad-be9ce2abc8e9
exl-id: c21cddb3-d12d-4e1b-bd62-cf75946569be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%

---

# Salvataggio di un&#39;attività o di un modulo come bozza {#saving-a-task-or-form-as-a-draft}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’opzione Salva come bozza consente di salvare un’istantanea di un’attività o di un modulo insieme ai dati compilati nel modulo associato. Potete anche creare una bozza da un modello. Le bozze vengono salvate nel dispositivo mobile e sincronizzate con il server Adobe Experience Manager Forms per un successivo recupero.

È possibile [aggiornare il modulo](/help/forms/using/working-with-form.md), [annotarlo](/help/forms/using/add-attachments.md) con fotografie e note di scarabocchio. Quando si continua ad aggiornare un modulo, è consigliabile salvarlo come bozza. Per le situazioni in cui si decide di inviare un modulo compilato in un secondo momento, è utile salvarlo come bozza.

Per abilitare la funzione Salva come bozza per i moduli salvati nel portale dei moduli, vedere [Salvataggio di un modulo HTML5 come bozza](/help/forms/using/saving-html5-form-draft.md).\
Per configurare l’invio di moduli adattivi, consulta [Componente Bozze e invii](/help/forms/using/draft-submission-component.md). (Non valido per i moduli sincronizzati con il server JEE di AEM Forms.)

Per creare una bozza, apri il modulo e tocca il pulsante **Salva come bozza** ![salva come bozza](assets/save-as-draft.png). Fornisci il nome della bozza e tocca **Salva**. La bozza viene salvata nella cartella Bozze e sincronizzata con il server. Viene salvata nella cartella Posta in uscita se l’app è offline.

Se successivamente si aggiorna il modulo corrispondente, le modifiche verranno applicate immediatamente. Al momento della sincronizzazione dell’app AEM Forms con il server AEM Forms, la bozza viene caricata sul server AEM Forms. Inoltre, la bozza viene spostata dalla casella in uscita alla cartella Attività o Bozze. Accanto ad essa viene visualizzata un’icona di modifica.

Mentre si continua a lavorare su più attività e punti iniziali e li si salva, le bozze vengono salvate. Ogni volta che l’app viene sincronizzata con il server AEM Forms, la bozza viene salvata sul server. In qualsiasi momento è possibile recuperare le bozze in base all&#39;ultima data e ora salvate. Ad esempio, se reinstalli l’app o modifichi il dispositivo mobile, puoi scaricare la bozza dal server.

## Eliminare una bozza {#delete-a-draft}

Nella cartella delle bozze sono elencate tutte le bozze. Puoi utilizzare l’opzione Elimina bozza per eliminare definitivamente le bozze dal dispositivo mobile e dal server.

L&#39;opzione per eliminare le bozze create da un&#39;attività non è disponibile. Quando si elimina una bozza creata da un&#39;attività, l&#39;attività viene abbandonata.

È possibile eliminare le bozze sia in modalità offline che online. Quando si scartano le bozze in modalità offline, le bozze vengono eliminate dal server solo quando viene ripristinata la connessione con il server.

Per eliminare una bozza, effettua le seguenti operazioni:

1. Nell’app AEM Forms, passa a **Forms.**
1. Seleziona **Bozze** dall’elenco a discesa accanto a Ricerca .
1. Un modulo con l’icona di modifica ![modifica-bozza-app](assets/edit-draft-app.png) denota una bozza. Toccate i puntini di sospensione orizzontali accanto alla bozza.
1. Nelle opzioni visualizzate quando toccate i puntini di sospensione orizzontali, toccate **Elimina bozza**.
