---
title: Nozioni di base sulla gestione di certificati e credenziali
seo-title: Basics of managing certificates and credentials
description: Scopri le nozioni di base sulla gestione di certificati e credenziali.
seo-description: Learn about the basics of managing certificates and credentials.
uuid: f421e206-e7b5-416c-b9fb-974094f10a66
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 986d16fc-4c81-4785-b1f3-fe8bd7ff669e
exl-id: 4817d150-9bfe-4cb9-8f06-6ff4eaaa6f55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 2%

---

# Nozioni di base sulla gestione di certificati e credenziali {#basics-of-managing-certificates-and-credentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

A *credenziale* contiene le informazioni di chiave privata necessarie per la firma o l&#39;identificazione dei documenti. A *certificato* sono informazioni di chiave pubblica configurate per l&#39;attendibilità. AEM forms utilizza certificati e credenziali per diversi scopi:

* Le estensioni Acrobat Reader DC utilizzano una credenziale per abilitare i diritti di utilizzo di Adobe Reader nei documenti PDF. (Vedi [Configurazione delle credenziali per l’utilizzo con le estensioni Acrobat Reader DC](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).)
* Puoi configurare il Rights Management per la visualizzazione delle credenziali da utilizzare in Acrobat solo da emittenti attendibili. (Vedi [Configurare le impostazioni di visualizzazione del Rights Management](/help/forms/using/admin-help/configuring-client-server-options.md#configure-document-security-display-settings).) Nel certificato deve figurare la denominazione comune (NC).
* Il servizio Firma accede a certificati e credenziali. Per informazioni dettagliate sul servizio Firma, consultare [Riferimento servizi](https://www.adobe.com/go/learn_aemforms_services_63).

**Generazione di una chiave di coppia**

AEM forms utilizza il proprio archivio certificati per memorizzare e gestire certificati, credenziali ed elenchi di revoche di certificati (CRL). È inoltre possibile utilizzare un dispositivo HSM (Hardware Security Module) indipendente per memorizzare chiavi private.

AEM forms non fornisce alcuna opzione per generare una coppia di chiavi. Tuttavia, è possibile generarlo utilizzando strumenti quali Java keytool e importarlo AEM forms Trust Store. Per ulteriori informazioni su Java keytool, consulta quanto segue:

[https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html](https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html)

[https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html](https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html)

[https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL](https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL)

I seguenti tipi di firma sono supportati e possono essere importati nei moduli AEM:

* Firma XML
* XMLTimeStampToken
* RFC 3161 TimeStampToken
* PKCS#7
* PKCS#1
* Firme DSA

**Gestione dei tasti persi o compromessi**

Se sospetti che la chiave sia persa o sia stata compromessa, procedi come segue:

1. Informare l’autorità di certificazione in modo che aggiunga la chiave compromessa nell’elenco di revoche dei certificati per revocare la chiave.
1. Ottenere una nuova chiave e i relativi certificati dall&#39;autorità di certificazione.
1. Firma nuovamente i documenti firmati utilizzando la chiave compromessa utilizzando la nuova chiave.
