---
title: Aggiornamento delle impostazioni generali
seo-title: Updating general settings
description: Aggiorna le impostazioni dell’app AEM Forms, ad esempio la schermata iniziale e le opzioni dei punti iniziali di recupero e degli allegati
seo-description: Update AEM Forms app settings such as the Home screen and fetch Startpoints and attachments options
uuid: 234cd2da-2b47-4d60-82ed-68363d782632
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: a3aac07e-7d67-4a4f-b941-ff25a981092f
exl-id: 5ca6212f-d3c7-4239-beba-9a0bdac4b1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 3%

---

# Aggiornamento delle impostazioni generali {#updating-general-settings}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le impostazioni generali dell’app AEM Forms consentono di specificare impostazioni quali il recupero degli allegati, la modalità offline, la schermata di destinazione, la categoria predefinita e la frequenza di salvataggio automatico.

## Aggiornamento delle impostazioni Generali nell’app {#working-with-the-form}

Quando sincronizzi l’app con il server AEM Forms, tutti i moduli e le attività definite vengono scaricati sul dispositivo mobile.

La soluzione pronta all’uso per l’app AEM Forms non scarica gli allegati associati a ciascun modulo quando l’app viene sincronizzata.

Nella scheda Generale modificare gli allegati da scaricare, la modalità offline, la schermata di destinazione, l’salvataggio automatico e le impostazioni di sincronizzazione. È possibile modificare le [Schermata principale](/help/forms/using/home-screen.md) della tua app.

**Passa alla scheda Generale nella schermata Impostazioni**

1. Per passare alla schermata di impostazione, tocca il pulsante Menu nell’angolo in alto a sinistra della schermata iniziale, quindi tocca **Impostazioni**.
1. Nella schermata Impostazioni , tocca la scheda Generale .

   ![Impostazioni generali nell’app AEM Forms](assets/gen-settings-2.png)

   >[!NOTE]
   >
   >Le opzioni possono essere visualizzate in modo diverso su diversi dispositivi mobili.

### Impostazioni generali {#general-settings}

Puoi apportare le seguenti modifiche alle impostazioni dell’app.

* **Recupera allegati attività**: Per specificare se scaricare o meno gli allegati associati quando ogni attività viene scaricata nell&#39;app.

* **Modalità offline**: Per abilitare o disabilitare il servizio offline per l’app AEM Forms. Vedi [Utilizzo della modalità offline](/help/forms/using/work-offline-mode.md) per i dettagli.

* **Schermo di destinazione**: Per impostare la posizione iniziale ([Schermata principale](/help/forms/using/home-screen.md)) per l’app.

   Opzioni disponibili:

   * Forms
   * Attività
   * Preferiti

* **Categoria predefinita**: Consente di selezionare la categoria di moduli da visualizzare nella schermata iniziale. Quando si seleziona Tutto, è possibile visualizzare tutti i moduli nella schermata iniziale. Le categorie vengono compilate in base ai moduli caricati nell’app. Forms è disponibile nell’app in base alle impostazioni del modulo specificate nel server AEM Forms.

* **Frequenza di salvataggio automatico**: Per impostare la frequenza alla quale [i dati del modulo vengono salvati in app mobile](/help/forms/using/autosave-data-app.md) locale.

* **Frequenza di sincronizzazione**: Per impostare la frequenza alla quale [app mobile sincronizzata](/help/forms/using/sync-app.md) con il server AEM Forms in modalità online.

**Cancella dati locali**: Cancellare il database, incluse le impostazioni e i dati locali per tutti gli utenti e l&#39;archiviazione dei file dal dispositivo.

>[!NOTE]
>
>Cancellando la cache, disconnetti immediatamente l’app.
>
>Viene tuttavia richiesto di confermare l’operazione di cancellazione della cache.
