---
title: Panoramica sulla configurazione di SSL
seo-title: Overview of configuring SSL
description: Scopri come migliorare la sicurezza delle comunicazioni configurando SSL.
seo-description: Learn about how to enhance security of communication by configuring SSL.
uuid: 3e99d2bf-137b-45ba-8384-309624094623
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8e107abb-861f-4063-b600-c87e34639019
exl-id: 5dc68401-f6bc-42cb-84db-1db805b045c5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 3%

---

# Panoramica sulla configurazione di SSL {#overview-of-configuring-ssl}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi creare credenziali SSL (Secure Sockets Layer) e configurare SSL sul server dell&#39;applicazione per migliorare la sicurezza della comunicazione con il server dell&#39;applicazione.

Come prodotto di sicurezza, il Rights Management richiede la configurazione di SSL. Durante la configurazione dei certificati SSL, assicurati di utilizzare solo le chiavi RSA. I certificati SSL con chiavi DSA non sono supportati.

Le informazioni fornite si applicano alle installazioni chiavi in mano, automatiche e manuali. Offre un esempio di metodo per configurare SSL. È inoltre possibile utilizzare altri metodi più appropriati per la rete o l&#39;organizzazione.

>[!NOTE]
>
>È consigliabile completare l’installazione, la configurazione e la distribuzione dei moduli AEM e assicurarsi che i prodotti siano in esecuzione correttamente prima di configurare SSL sul server dell’applicazione.

>[!NOTE]
>
>Durante la creazione di certificati di sicurezza e credenziali SSL, utilizza gli stessi privilegi dell’account utente utilizzati per eseguire il server dell’applicazione. Se il server applicazioni viene eseguito utilizzando altri privilegi utente, il modulo potrebbe non essere eseguito correttamente per le rappresentazioni PDFForm quando ContentRootURI punta a https.

Se disponi di un server LDAP abilitato per SSL, configura Gestione utente per utilizzarlo. (Vedi [Configurare la gestione utente per un server LDAP abilitato per SSL](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)
