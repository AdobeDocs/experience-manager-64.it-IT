---
title: Configurare l’ambiente per l’app AEM Forms
seo-title: Set up environment for AEM Forms app
description: Hardware, software e licenze per la creazione e l’implementazione dell’app AEM Forms.
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 3%

---

# Configurare l’ambiente per l’app AEM Forms {#set-up-environment-for-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per creare e distribuire l’app AEM Forms sono necessari i seguenti hardware, software e licenze:

## Per dispositivi Windows {#for-windows-devices}

* Microsoft Windows 8.1 o Windows 10
* Microsoft Visual Studio 2015
* Strumenti di Microsoft Visual Studio per Apache Cordova

## Per dispositivi iOS {#for-ios-devices}

* Apple Mac basato su Intel con Mac OS X 10.9.5 o superiore
* SDK iOS 8.4 o successivo
* Versione Xcode: Xcode 6.4 per OS X o versioni successive
* Iscrizione al programma iOS Developer Enterprise
* Certificato Enterprise per la distribuzione di app iOS interne
* Apple iPad con iOS 8.4 o versione successiva

## Per dispositivi Android {#for-android-devices}

* Android Development Toolkit (bundle ADT) che può essere scaricato da [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Se l&#39;ambiente è configurato in un sistema MAC, l&#39;ADT deve essere installato nella cartella Applicazioni.
* Se ADT è installato in un altro percorso in MAC o se l&#39;ambiente è configurato in un sistema Windows, è necessario aggiornare il percorso SDK ADT in `local.properties` file disponibile in `src\android` cartella nell&#39;archivio sorgente estratto `mobileworkspace-src.zip`. In questo file, seleziona `sdk.dir` alla posizione ADT SDK sul desktop.

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip contiene PhoneGap SDK 5.0. Assicurati che PhoneGap SDK non sia preinstallato.
