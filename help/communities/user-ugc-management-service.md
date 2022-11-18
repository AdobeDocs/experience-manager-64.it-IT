---
title: Servizio di gestione utenti e UGC in AEM Communities
seo-title: User and UGC Management Service in AEM Communities
description: Utilizza le API per eliminare e esportare in blocco i contenuti generati dagli utenti e disabilitare l’account utente.
seo-description: Use APIs to bulk delete and bulk export user generated content, and disable user account.
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
role: Admin
exl-id: f4adc53d-6809-4d89-a3dd-5d783e938a63
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Servizio di gestione utenti e UGC in AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>Il RGPD è utilizzato come esempio nelle sezioni seguenti, ma i dettagli trattati sono applicabili a tutte le normative sulla protezione dei dati e sulla privacy; come RGPD, CCPA, ecc.

AEM Communities espone le API predefinite per la gestione dei profili utente e la gestione in blocco dei contenuti generati dagli utenti (UGC, User-Generated Content). Una volta attivato, il **UserUgcManagement** Il servizio consente agli utenti con privilegi (amministratori della community e moderatori) di disabilitare i profili utente e di eliminare o esportare in blocco i contenuti generati dagli utenti specifici mediante GGC. Queste API consentono inoltre ai titolari del trattamento e ai responsabili del trattamento dei dati dei clienti di rispettare i requisiti del Regolamento generale sulla protezione dei dati (RGPD) dell’Unione Europea e altri mandati sulla privacy ispirati al RGPD.

Per ulteriori informazioni, consulta [Pagina RGPD nell’Adobe Privacy Center](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Se hai configurato [Adobe Analytics in AEM Communities](analytics.md) sito, i dati utente acquisiti vengono inviati al server Adobe Analytics. Adobe Analytics fornisce API che ti consentono di accedere, esportare ed eliminare i dati utente e di rispettare i requisiti RGPD. Per ulteriori informazioni, consulta [Inviare richieste di accesso e cancellazione](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Per utilizzare queste API, devi abilitare la `/services/social/ugcmanagement` attivazione del servizio UserUgcManagement. Per attivare questo servizio, installare il [servlet di esempio](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) disponibile su [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Quindi, colpisci l&#39;endpoint nell&#39;istanza di pubblicazione del sito Communities con i parametri appropriati utilizzando una richiesta http, simile alla seguente:

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

Tuttavia, puoi anche creare un’interfaccia utente (interfaccia utente) per gestire i profili utente e i contenuti generati dagli utenti nel sistema.

Queste API consentono di eseguire le seguenti funzioni.

## Recuperare l’UGC di un utente {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` consente di esportare dal sistema tutti i contenuti UGC di un utente.

* **user**: ID autorizzabile di un utente.
* **outputStream**: il risultato viene restituito come flusso di output, che è un file zip contenente il contenuto generato dall’utente (come file json) e gli allegati (che includono immagini o video caricati dall’utente).

Ad esempio, per esportare l’UGC di un utente chiamato Weston McCall, che utilizza weston.mccall@dodgit.com come ID autorizzabile per accedere al sito Communities, puoi inviare una richiesta http GET simile alla seguente:

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Eliminare l’UGC di un utente {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** aiuta a eliminare tutti gli UGC per un utente dal sistema.

* **user**: ID autorizzabile dell&#39;utente.

Ad esempio, per eliminare l’UGC di un utente con ID autorizzabile weston.mccall@dodgit.com tramite la richiesta http-POST, utilizza i seguenti parametri:

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### Eliminare UGC da Adobe Analytics {#delete-ugc-from-analytics}

Per eliminare i dati utente da Adobe Analytics, segui il flusso di lavoro di analisi RGPD; poiché l’API non elimina i dati utente da Adobe Analytics.

Per le mappature delle variabili Adobe Analytics utilizzate da AEM Communities, fai riferimento alla seguente immagine:

![Mappatura delle variabili AEM community per Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Disattiva un account utente {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** consente di disattivare un account utente.

* **user**: ID autorizzabile dell&#39;utente.

>[!NOTE]
>
>La disattivazione di un utente elimina tutti i contenuti generati dall’utente sul server.

Ad esempio, per eliminare il profilo di un utente con ID autorizzabile weston.mccall@dodgit.com tramite la richiesta http-POST, utilizza i seguenti parametri:

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>deleteUserAccount() API disabilita solo un profilo utente nel sistema e rimuove l&#39;UGC. Tuttavia, per eliminare un profilo utente dal sistema, passa a **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de), individua il nodo utente ed eliminalo.
