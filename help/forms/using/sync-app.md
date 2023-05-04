---
title: Sincronizzazione dell’app
seo-title: Synchronizing the app
description: Sincronizza l’app AEM Forms sul tuo dispositivo mobile con il server AEM Forms.
seo-description: Synchronize the AEM Forms app on your mobile device with the AEM Forms server.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
exl-id: b5681fe5-69ba-4fc0-95e3-6ffdcdd95382
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# Sincronizzazione dell’app {#synchronizing-the-app}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Sincronizzazione dell’app {#synchronizing-the-app-1}

I moduli nell’app vengono scaricati dal server AEM Forms. I moduli vengono scaricati nelle schede Attività e Forms. Le bozze create dai moduli vengono scaricate nella scheda bozze e le bozze create dalle attività vengono scaricate nella scheda attività. Per un modulo indipendente sul server OSGi, i moduli e le bozze vengono scaricati rispettivamente nelle schede Forms e Bozza.

Quando si completa e si invia un modulo, questo viene immediatamente caricato sul server AEM Forms se l’app è online. I moduli vengono recuperati dal server quando l’app viene sincronizzata. Le bozze, tuttavia, vengono sincronizzate istantaneamente con il server se l’app è online.

Quando sei online con il server AEM Forms, per impostazione predefinita l’app viene sincronizzata ogni 15 minuti. Tuttavia, è possibile modificare la frequenza di sincronizzazione. In alternativa, puoi sincronizzare manualmente l’app in qualsiasi momento.

**Per sincronizzare manualmente l’app**

Tocca il pulsante Sincronizza ![sync-app](assets/sync-app.png) nell&#39;angolo in basso a destra della schermata iniziale.

**Per modificare la frequenza di sincronizzazione**

1. Per passare alla schermata di impostazione, tocca il pulsante del menu nell’angolo in alto a sinistra della schermata iniziale, quindi tocca **Impostazioni**.
1. Nella schermata Impostazioni , tocca la scheda Generale .

   ![Impostazione della frequenza di sincronizzazione nella finestra Impostazioni generali](assets/gen-settings-1.png)

1. Nell’opzione Frequenza di sincronizzazione, toccare il valore a destra della frequenza di sincronizzazione.
1. Nell’elenco a discesa , seleziona la nuova frequenza di sincronizzazione.

### Specifiche tecniche {#technical-specifications}

* La logica principale dell’invio dei dati dell’app offline al server AEM Forms è inclusa in runtime/offline/util/offline.js.
* In .js, la chiamata alla funzione processOfflineSubmittedSavedTasks(...) invia al server le attività salvate/inviate. Inoltre, gestisce eventuali errori o conflitti nel processo di sincronizzazione. Se l’invio di un’attività non riesce, l’attività nell’app viene contrassegnata come non riuscita. Inoltre, l&#39;attività rimane nella Posta in uscita.
* La funzione syncSubmittedTask() e syncSavedTask() eseguono operazioni su singole attività.
* La chiamata alla funzione processOfflineSubmittedSavedTasks() viene avviata dal componente dell&#39;elenco delle attività dopo che un utente seleziona di sincronizzare lo stato offline al server o una sincronizzazione automatica dal thread in background.
