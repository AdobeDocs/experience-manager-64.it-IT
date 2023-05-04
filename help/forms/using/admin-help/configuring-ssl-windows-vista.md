---
title: Configurazione di SSL su Windows Vista
seo-title: Configuring SSL on Windows Vista
description: Scopri come configurare SSL in Windows Vista.
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 4%

---

# Configurazione di SSL su Windows Vista {#configuring-ssl-on-windows-vista}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per configurare SSL su Windows Vista™, è necessario un certificato SSL con chiavi RSA per l&#39;autenticazione. Puoi usare il keytool Java per creare il certificato.

>[!NOTE]
>
>Windows Vista non funziona con le chiavi DSA.

È possibile eseguire keytool utilizzando un singolo comando che include tutte le informazioni necessarie per creare il certificato e il keystore.

**Creare un certificato SSL**

1. Al prompt dei comandi, passa a *[CASA JAVA]*/bin e digita il seguente comando per creare il certificato e il keystore:

   `keytool -genkey -keyalg RSA -dname "CN=`*Nome host* `, OU=`*Nome gruppo* `, O=`*Nome dell&#39;azienda* `,L=`*Città*****Nome* `, S=`*Stato* `, C=`*Codice paese* `" -alias`*&quot;LC Cert&quot;* `-keypass` `*key*`*_**password* `-keystore`*nome chiave* `.keystore`

   >[!NOTE]
   >
   >Sostituisci *[JAVA_HOME] con la directory in cui è installato JDK e sostituisci il testo in corsivo con i valori corrispondenti al tuo ambiente.*

1. Tipo `changeit` come password. Questa password è l&#39;impostazione predefinita per un&#39;installazione Java e l&#39;amministratore di sistema potrebbe averla modificata.
