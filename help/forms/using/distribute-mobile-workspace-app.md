---
title: Distribuire l’app AEM Forms
seo-title: Distribute AEM Forms app
description: Utilizza Mobile Device Management (MDM) per la distribuzione su larga scala di app su dispositivi mobili.
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: c1bf0a0e-70f7-41dd-8b1a-c114d89a265b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 2%

---

# Distribuire l’app AEM Forms {#distribute-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Mobile Device Management (MDM) consente la distribuzione su larga scala di app su dispositivi mobili.

>[!NOTE]
>
>Questa distribuzione è applicabile solo per i dispositivi iOS e Android.

## Caratteristiche principali generalmente fornite dalle soluzioni MDM: {#main-features-generally-provided-by-mdm-solutions}

* Abilitare la registrazione dei dispositivi nell&#39;ambiente aziendale
* Consenti configurazione e aggiornamento delle impostazioni del dispositivo
* Applica la conformità in materia di sicurezza.
* Accesso mobile sicuro alle risorse aziendali

Una soluzione MDM, insieme a Mobile Application Management, consente di gestire app interne, pubbliche e acquistate sui dispositivi mobili della tua azienda.

L’amministratore MDM può caricare sia file ipa che apk sul server MDM e controllare gli utenti che possono accedere ai file ipa o apk. L’amministratore può inoltre controllare l’impostazione del profilo corrispondente a ciascuna applicazione.

## Impostazioni del profilo che interessano l’app AEM Forms {#profile-settings-affecting-the-aem-forms-app-br}

Le seguenti impostazioni del profilo sul tuo dispositivo influiranno sul funzionamento dell’app AEM Forms sul tuo dispositivo:

* **Consenti uso della fotocamera** in **Funzionalità del dispositivo** sezione

Se si disattiva **Consenti uso della fotocamera**, la funzione della telecamera [Annotazione foto](/help/forms/using/add-attachments.md) non funzionerà. Abilita questa opzione per usare la fotocamera nell’app.

* **Richiedi passcode sul dispositivo** nella sezione Criteri passcode

Per abilitare **crittografia dei dati delle applicazioni**, si consiglia di abilitare **passcode** sul dispositivo. Se il passcode non è impostato sul dispositivo, i dati dell&#39;applicazione memorizzati sul dispositivo non sono crittografati.
