---
title: Configurazione per le app AEM
seo-title: Configuring for AEM Apps
description: Scopri come configurare AEM app.
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: 593a588c-02f1-4b48-ac57-9348d6652bcc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 5%

---

# Configurazione per le app AEM{#configuring-for-aem-apps}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le app Adobe Experience Manager consentono di aggiornare il contenuto dell’applicazione in modalità aerea (OTA). Il contenuto aggiornato viene memorizzato nell’istanza di pubblicazione. Per consentire all’app sul dispositivo di connettersi all’istanza di pubblicazione e verificare la disponibilità di aggiornamenti, l’istanza di pubblicazione deve essere configurata per consentire un’intestazione di referente vuota.

## Configurazione dell’intestazione di riferimento vuota {#configuring-empty-referrer-header}

Per configurare il servizio filtro referrer:

* Apri la console Apache Felix (**Configurazioni**) all&#39;indirizzo:
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Accedi come amministratore.
* In **Configurazioni** seleziona il menu: *Filtro di riferimento Apache Sling*
* Seleziona il campo Consenti valori vuoti per consentire intestazioni referrer vuote o mancanti.
* Fai clic su **Salva** per salvare le modifiche.

![chlimage_1-58](assets/chlimage_1-58.png)

Consulta la sezione [Impostazioni di configurazione OSGI](/help/sites-deploying/osgi-configuration-settings.md) e [Lista di controllo sicurezza - Problemi relativi alla falsificazione delle richieste tra siti diversi](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) per ulteriori dettagli.
