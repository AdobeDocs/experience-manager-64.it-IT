---
title: Utilizzo della modalità offline
seo-title: Working in the offline mode
description: Disconnetti il tuo dispositivo mobile al di fuori della gamma di rete AEM Forms o in modalità offline e lavora sull'app AEM Forms
seo-description: Take your mobile device offline outside your AEM Forms network range or in a completely offline mode and work on the AEM Forms app
uuid: b900a0f8-90ce-486a-bde6-6cdf11bd2801
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 9a3c6ab4-8bb9-40c7-8c56-59153b364887
exl-id: 14303b8f-40a7-4bc5-8282-7526e0319264
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Utilizzo della modalità offline {#working-in-the-offline-mode}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La modalità offline dell’app AEM Forms ti consente di lavorare senza problemi anche se l’app non è in linea. È possibile aprire, aggiornare e inviare un modulo senza richiedere alcuna connettività di rete.

Inizia a lavorare sull’app AEM Forms sincronizzando l’app con il server AEM Forms. Tutti i moduli assegnati all’utente vengono scaricati nell’app. Per AEM Forms su JEE, le attività vengono recuperate nella scheda attività e i punti di partenza associati a moduli e altri moduli nella scheda Forms. Per AEM Forms su OSGi, nella scheda Forms vengono caricati solo Forms.

Per informazioni dettagliate su come sincronizzare l’app, vedi [Sincronizzazione dell’app](/help/forms/using/sync-app.md).

## Forms disponibile offline {#making-forms-available-offline}

Quando sincronizzi l’app con il server AEM Forms, i moduli vengono scaricati sul dispositivo mobile. Tuttavia, per impostazione predefinita, gli allegati associati al modulo non vengono scaricati. Ciò implica che se sei online, puoi visualizzare gli allegati. Tuttavia, per assicurarti di poter visualizzare l’allegato in modalità offline, modifica le impostazioni predefinite nell’app.

Per fare in modo che gli allegati associati siano scaricati con ciascun modulo, impostare gli allegati di recupero su ON. Per maggiori dettagli, vedi [Aggiornamento delle impostazioni generali](/help/forms/using/update-general-settings.md).

Poiché il download dei dati sul dispositivo mobile può influire sulle prestazioni del dispositivo, per impostazione predefinita, l&#39;impostazione Fetch Allegati è impostata su OFF. Gli allegati vengono recuperati nel dispositivo per qualsiasi attività scaricata dal server dopo l&#39;aggiornamento dell&#39;impostazione su ON. In modalità offline, un utente può quindi lavorare su tutte le attività scaricate sul dispositivo dopo aver impostato il **Recupera allegati** opzioni su ON.

## Configurazione del servizio offline per l’app AEM Forms {#configuring-offline-service-for-aem-forms-app-br}

Il servizio AEM Forms app offline identifica le risorse utilizzate in un modulo. L’app AEM Forms si basa su questo servizio per ottenere informazioni sulle dipendenze del modulo. Per abilitare le funzionalità offline sono necessarie informazioni sulle dipendenze del modulo. Il servizio AEM Forms app offline memorizza in cache i percorsi o gli URL delle risorse utilizzate in un modulo. La cache viene aggiornata in base alle modifiche apportate al modulo e al periodo di validità configurato per il servizio offline. La memorizzazione nella cache di percorsi o URL delle risorse utilizzate in un modulo migliora le prestazioni lato server.

Per configurare il componente offline lato server dell&#39;app AEM Forms:

1. Nell’istanza di authoring, passa a **Adobe Experience Manager** >**Strumenti** > **Forms** > **Configurare il servizio offline app Forms**.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. In Impostazioni generali puoi effettuare le seguenti operazioni:

   * **Cancella cache**: Cancella la cache lato server delle dipendenze del modulo.
   * **Ripristina configurazione**: Ripristina la configurazione offline dell’app AEM Forms.
   * **Validità cache**: Specifica il periodo di validità della cache offline lato server.
   * **Percorsi di osservazione delle risorse**: Specifica i percorsi in cui il servizio offline controlla le modifiche alle risorse. Se si verificano modifiche nei percorsi specificati, viene aggiornata la cache offline di tutti i moduli dipendenti. Esempio: `/etc/clientlibs/fd,/content/dam/images`.

1. In **Cache delle risorse manuali** scheda , specifica che il servizio offline dipendenze modulo non può identificare. Puoi specificare risorse quali le immagini caricate da JavaScript. L’app AEM Forms scaricherà anche queste risorse per la modalità offline.
