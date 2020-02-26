---
title: Configurazione di SSL in Windows Vista
seo-title: Configurazione di SSL in Windows Vista
description: Scoprite come configurare SSL in Windows Vista.
seo-description: Scoprite come configurare SSL in Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8

---


# Configurazione di SSL in Windows Vista {#configuring-ssl-on-windows-vista}

Per configurare SSL su Windows Vista™, è necessario un certificato SSL con chiavi RSA per l&#39;autenticazione. Potete utilizzare lo strumento Java keytool per creare il certificato.

>[!NOTE]
>
>Windows Vista non funzionerà con le chiavi DSA.

È possibile eseguire keytool utilizzando un singolo comando che include tutte le informazioni necessarie per creare il certificato e l&#39;archivio di chiavi.

**Creare un certificato SSL**

1. Al prompt dei comandi, andate a *[JAVA HOME]*/bin e digitate il comando seguente per creare il certificato e l&#39;archivio di chiavi:

   `keytool -genkey -keyalg RSA -dname "CN=`*Nome *host Nome`, OU=`*gruppo Nome* `, O=`*società Nome *`,L=`*città******Nome* `, S=`*Stato *Codice`, C=`** `" -alias`**`-keypass``*key*`**`-keystore`** Paese&quot;LC Cert&quot;&quot;*_*passwordkeystorename `.keystore`

   >[!NOTE]
   >
   >Sostituite *[JAVA_HOME]con la directory in cui è installato JDK e sostituite il testo in corsivo con valori corrispondenti all’ambiente in uso.*

1. Digitare `changeit` la password. Questa password è l&#39;impostazione predefinita per un&#39;installazione Java e l&#39;amministratore di sistema potrebbe averla modificata.

