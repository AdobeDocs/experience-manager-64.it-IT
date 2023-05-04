---
title: Configurare il Cloud Service Adobe Mobile Services
seo-title: Configure your Adobe Mobile Services Cloud Service
description: Segui questa pagina per configurare il tuo Cloud Service Adobe Mobile Services .
seo-description: Follow this page to configure your Adobe Mobile Services Cloud Service.
uuid: 21fe5b24-dc4d-4ee4-9e7f-ed4783baf276
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 962e9e98-a303-435b-a938-31319282e022
legacypath: /content/docs/en/aem/6-1/develop/mobile-apps/apps/managing-aem-mobile-apps/configure-your-adobe-phonegap-build-cloud-service1
exl-id: 360c0ba9-ea49-495c-86d0-6d1db3f806a5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 3%

---

# Configurare il Cloud Service Adobe Mobile Services {#configure-your-adobe-mobile-services-cloud-service}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe consiglia di utilizzare l’editor di SPA per i progetti che richiedono il rendering lato client basato sul framework di un’applicazione a pagina singola (ad esempio, React). [Ulteriori informazioni](/help/sites-developing/spa-overview.md).

La **Riquadro delle metriche di Mobile** nel centro comandi fornisce analisi in tempo reale per la tua app mobile.

La [Adobe Mobile Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) L’SDK è reso disponibile tramite un plug-in PhoneGap. Le metriche vengono raccolte e memorizzate nella cache del dispositivo fino a quando il dispositivo non viene connesso, e a quel punto i dati vengono inviati ad Adobe Mobile Services Cloud per scopi di reporting e analisi.

Adobe Mobile Analytics SDK fornisce quanto segue:

1. **Raccolta di dati per i canali mobili** - Raccogliere dati completi per i siti web e le app mobili su tutti i principali sistemi operativi.
1. **Analisi del coinvolgimento mobile** - Comprendere il coinvolgimento degli utenti all’interno della tua app mobile, del tuo sito web o del tuo video, tra cui la frequenza con cui i consumatori avviano il canale, se ne fanno acquisti e altro ancora.
1. **Dashboard e rapporti per app mobili** - Ottieni rapporti sull&#39;utilizzo che includono metriche sul ciclo di vita per le tue app e metriche dell&#39;app store: vedi tendenze per gli utenti, avvii, lunghezza media della sessione, durata della conservazione e arresti anomali.
1. **Analisi delle campagne mobile** - Quantificare l’efficacia delle campagne specifiche per dispositivi mobili come SMS, annunci di ricerca mobile, annunci display mobile e codici QR.
1. **Analisi della geolocalizzazione** - Trova dove gli utenti dell’app avviano e interagiscono con le tue esperienze mobili in base alla posizione GPS o ai punti di interesse.
1. **Analisi dei percorsi** - Scopri come gli utenti navigano nell’app per determinare quali schermate e elementi dell’interfaccia utente coinvolgono gli utenti e quali causano il rilascio.

>[!CAUTION]
>
>La **Analizzare le metriche** Il riquadro viene visualizzato nel dashboard solo se hai configurato Cloud Services.

![chlimage_1-22](assets/chlimage_1-22.png)

Riquadro delle metriche del centro di comando AEM

## Configurazione del Cloud Service {#configuring-the-cloud-service}

Per sfruttare l’Adobe Mobile Services Analytics devi configurare AEM Mobile Analytics Cloud Service con le informazioni sul tuo account Adobe Analytics.

1. Fai clic sull’icona in alto a destra per aggiungere o modificare i Cloud Services dal **Gestire i Cloud Services** dal dashboard dell&#39;app.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. La **Aggiungere o modificare Cloud Services** viene visualizzato lo schermo. Seleziona **Adobe Mobile Services** e fai clic su **Successivo**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Scegli una configurazione esistente dal **Mobile Services** o scegliere **Crea configurazione** per crearne una nuova.

   Per una nuova configurazione, immetti il **Proprietà di Mobile Services** e fai clic su **Verifica.**

   ![chlimage_1-25](assets/chlimage_1-25.png)

   Se le credenziali vengono verificate, la **Verifica** il pulsante cambia in **Verificato**. Puoi scegliere un’app di servizi mobili da **Selezionare un servizio app mobile**.

   Fai clic su **Invia** per configurare la configurazione.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Una volta impostata una configurazione cloud, puoi visualizzarla nel dashboard.

   ![chlimage_1-27](assets/chlimage_1-27.png)

   >[!NOTE]
   >
   >Una volta impostata la configurazione cloud, puoi visualizzare la **Analizzare le metriche** Affianca nel dashboard dell&#39;app.

   ![chlimage_1-28](assets/chlimage_1-28.png)
