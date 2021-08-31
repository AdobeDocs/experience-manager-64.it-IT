---
title: Configurazione delle estensioni Acrobat Reader DC per l’acquisizione dei dati
seo-title: Configuring Acrobat Reader DC extensions for data capture
description: Scopri come configurare le estensioni Acrobat Reader DC per l’acquisizione dei dati.
seo-description: Learn how to configure Acrobat Reader DC extensions for data capture.
uuid: af6b3c72-601e-4f54-8343-a323eeee5906
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8f8367fe-a8e9-46ee-a980-1633be02932d
exl-id: 3609ad29-f5b4-4426-8bbc-7c2e38f9b140
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Configurazione delle estensioni Acrobat Reader DC per l’acquisizione dei dati {#configuring-acrobat-reader-dc-extensions-for-data-capture}

Se gli utenti dell’installazione dei moduli di AEM utilizzano la funzionalità di acquisizione dati di Content Services (obsoleto), è consigliabile creare un ruolo con accesso in sola lettura per questi utenti.

***nota**: Adobe® LiveCycle® Content Services ES (obsoleto) è un sistema di gestione dei contenuti installato con il LiveCycle. Consente agli utenti di progettare, gestire, monitorare e ottimizzare processi incentrati sulle persone. Il supporto per Content Services (obsoleto) termina il 31/12/2014.

L&#39;acquisizione dei dati richiede l&#39;assegnazione di un ruolo utente per accedere a SampleReaderExtensionsCredential. È possibile assegnare il ruolo Amministratore trust standard, ma si considera che questo ruolo fornisce agli utenti generali non amministrativi i privilegi di amministratore potenti che controllano le impostazioni PKI Trust e gestiscono le credenziali PKI, che potrebbero compromettere la sicurezza dell’installazione dei moduli AEM in un ambiente di produzione. È consigliabile che l’amministratore di sistema dei moduli di AEM crei un ruolo che consenta l’accesso in sola lettura all’archivio attendibilità e assegni questo nuovo ruolo agli utenti non amministratori che utilizzano l’acquisizione dati.

## Creare un ruolo per gli utenti di acquisizione dati {#create-a-role-for-data-capture-users}

1. Nella console di amministrazione, fai clic su Impostazioni > Gestione utente > Gestione ruolo, quindi fai clic su Nuovo ruolo.
1. Immetti il nome del ruolo (ad esempio, Utente acquisizione dati) e la descrizione nei campi appropriati, quindi fai clic su Avanti.
1. Nella schermata Autorizzazioni ruolo fare clic su Trova autorizzazioni, quindi selezionare Letto credenziali dall&#39;elenco delle autorizzazioni disponibili.
1. Fare clic su OK, quindi su Fine.

## Assegnare il ruolo di acquisizione dati {#assign-the-data-capture-role}

1. Nella console di amministrazione, fai clic su Impostazioni > Gestione utente > Gestione ruolo, quindi fai clic su Trova.
1. Fai clic sul ruolo utente di acquisizione dati creato.
1. Nella scheda Utenti/gruppi ruolo fare clic su Trova utenti/gruppi.
1. Nella schermata Trova utenti e gruppi fare clic su Trova, selezionare gli utenti che richiedono il ruolo utente di acquisizione dati, quindi fare clic su OK.
1. Nella schermata Modifica ruolo fare clic su Salva.
