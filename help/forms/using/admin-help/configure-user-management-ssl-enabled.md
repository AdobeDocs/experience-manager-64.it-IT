---
title: Configurare la gestione utente per un server LDAP abilitato per SSL
seo-title: Configure User Management for an SSL-enabled LDAP server
description: Scopri come configurare User Management per un server LDAP abilitato per SSL per consentire il corretto funzionamento della sincronizzazione su LDAPS.
seo-description: Learn how  to configure User Management for an SSL-enabled LDAP server to enable synchronization to work properly over LDAPS.
uuid: 4b3f8ac7-fa38-4adf-a851-82d55fe431fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e6e7e2fa-579d-4b36-8598-6ced469a94b1
exl-id: 9ed22c75-bce7-4d26-a4cd-a58e41e5068e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 2%

---

# Configurare la gestione utente per un server LDAP abilitato per SSL {#configure-user-management-for-an-ssl-enabled-ldap-server}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Affinché la sincronizzazione funzioni correttamente su LDAPS, i certificati LDAP rilasciati dall’autorità di certificazione (CA) devono essere presenti nell’ambiente di runtime Java (JRE) del server dell’applicazione. Importa il certificato nel file di avvisi JRE del server dell&#39;applicazione, in genere nel *[JAVA_HOME]*/jre/lib/security/cacerts directory.

1. Abilita SSL sul server delle directory. Per ulteriori informazioni, consulta la documentazione fornita dal fornitore della directory.
1. Esporta un certificato client dal server delle directory.
1. Utilizzare il programma keytool per importare il file del certificato client nell&#39;archivio certificati Java Virtual Machine (JVM™) predefinito del server applicazioni AEM forms . La procedura per questa attività varia a seconda dei percorsi di installazione di JVM e client. Ad esempio, se utilizzi BEA WebLogic Server con JDK 1.5 da un prompt dei comandi, digita questo testo:

   `keytool -import -alias`*alias* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. Quando richiesto, digitare la password. (Per Java, la password predefinita è `changeit`.) Viene visualizzato un messaggio per informare che il certificato è stato importato correttamente.
1. Quando richiesto, digita `Yes` per considerare attendibile il certificato.
1. Abilitare SSL in Gestione utente e, durante la configurazione delle impostazioni della directory, selezionare Sì per l’opzione SSL e modificare di conseguenza l’impostazione della porta. Il numero di porta predefinito è 636.

>[!NOTE]
>
>Se riscontri problemi durante l&#39;utilizzo di SSL, utilizza un browser LDAP per verificare se può accedere al sistema LDAP quando utilizzi SSL. Se il browser LDAP non riesce ad accedere, il certificato o il server dell&#39;applicazione non è configurato correttamente. Se il browser LDAP funziona correttamente e si verificano ancora problemi, Gestione utente non è configurato correttamente.
