---
title: Sincronizzazione dell'app
seo-title: Sincronizzazione dell'app
description: Sincronizzate l'app AEM Forms sul dispositivo mobile con il server AEM Forms.
seo-description: Sincronizzate l'app AEM Forms sul dispositivo mobile con il server AEM Forms.
uuid: 7e1526e1-13bd-498a-a265-cd4f2d05ccdd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: dae1ce32-702e-4cf0-b3c6-976551208d09
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Sincronizzazione dell&#39;app {#synchronizing-the-app}

## Sincronizzazione dell&#39;app {#synchronizing-the-app-1}

I moduli contenuti nell&#39;app vengono scaricati dal server AEM Forms. I moduli vengono scaricati nelle schede Attività e Moduli. Le bozze create dai moduli vengono scaricate nella scheda delle bozze e le bozze create dalle attività vengono scaricate nella scheda delle attività. Per un modulo standalone sul server OSGi, i moduli e le bozze vengono scaricati nelle schede Moduli e Bozza, rispettivamente.

Quando si completa e si invia un modulo, quest&#39;ultimo viene immediatamente caricato nel server AEM Forms se l&#39;app è online. I moduli vengono recuperati dal server quando l&#39;app viene sincronizzata. Le bozze, tuttavia, vengono sincronizzate immediatamente con il server se l&#39;app è online.

Se siete online con il server AEM Forms, per impostazione predefinita l&#39;app viene sincronizzata ogni 15 minuti. Tuttavia, potete modificare la frequenza di sincronizzazione. In alternativa, potete sincronizzare manualmente l&#39;app in qualsiasi momento.

**Per sincronizzare manualmente l&#39;app**

Toccate il pulsante Sincronizza ![sincronizzazione-app](assets/sync-app.png) nell’angolo inferiore destro della schermata principale.

**Per modificare la frequenza di sincronizzazione**

1. Per passare alla schermata Impostazioni, toccate il pulsante del menu in alto a sinistra nella schermata Home, quindi toccate **Impostazioni**.
1. Nella schermata Impostazioni, toccate la scheda Generale.

   ![Impostazione della frequenza di sincronizzazione nella finestra Impostazioni generali](assets/gen-settings-1.png)

1. Nell’opzione Frequenza sincronizzazione, toccate il valore a destra della frequenza di sincronizzazione.
1. Nell’elenco a discesa, selezionate la nuova frequenza di sincronizzazione.

### Specifiche tecniche {#technical-specifications}

* La logica principale per l&#39;invio dei dati dell&#39;app offline al server AEM Forms è inclusa in runtime/offline/util/offline.js.
* In .js, la chiamata alla funzione processOfflineSubsentSavedTasks(...) invia al server le attività salvate/inviate. Vengono inoltre gestiti eventuali errori o conflitti nel processo di sincronizzazione. Se l&#39;invio di un&#39;attività non riesce, l&#39;attività nell&#39;app viene contrassegnata come non riuscita. Inoltre, l&#39;attività rimane nella casella in uscita.
* Le funzioni syncSubsentTask() e syncSavedTask() eseguono operazioni su singole attività.
* La chiamata alla funzione processOfflineSubsentSavedTasks() viene avviata dal componente Elenco attività dopo che l&#39;utente ha selezionato la sincronizzazione dello stato offline con il server o una sincronizzazione automatica dal thread in background.

