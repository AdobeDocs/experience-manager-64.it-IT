---
title: Integrazione con Adobe Sign | Gestione dei dati utente
seo-title: Integrazione con Adobe Sign | Gestione dei dati utente
description: AEM Forms si integra con Adobe Sign per consentire i flussi di lavoro di firma elettronica in moduli adattivi per elaborare moduli o accordi per flussi di lavoro legali, di vendita, di retribuzione, di gestione delle risorse umane. Approfondisci i dati utente, gli archivi dati e accedi ed elimina i dati utente.
seo-description: AEM Forms si integra con Adobe Sign per consentire i flussi di lavoro di firma elettronica in moduli adattivi per elaborare moduli o accordi per flussi di lavoro legali, di vendita, di retribuzione, di gestione delle risorse umane. Approfondisci i dati utente, gli archivi dati e accedi ed elimina i dati utente.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Adobe Sign
role: Admin
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Integrazione con Adobe Sign | Gestione dei dati utente {#integration-with-adobe-sign-handling-user-data}

AEM Forms si integra con Adobe Sign per consentire i flussi di lavoro di firma elettronica in moduli adattivi per elaborare moduli o accordi per flussi di lavoro legali, di vendita, di retribuzione, di gestione delle risorse umane. Consente la firma di utenti singoli e multipli, flussi di lavoro di firma sequenziali e simultanei, la firma di moduli come utente anonimo o connesso e diversi modi per autenticare gli utenti.

Quando un firmatario o più firmatari firmano e inviano un modulo adattivo, viene generato un accordo Adobe Sign che include informazioni sui firmatari.

Per ulteriori informazioni sull&#39;integrazione di AEM Forms con Adobe Sign, consulta [Uso di Adobe Sign in un modulo adattivo](/help/forms/using/working-with-adobe-sign.md).

## Archiviazione dati e dati utente {#data}

Il modulo adattivo abilitato per Adobe Sign include informazioni sui firmatari e può includere altri dati utente raccolti dal modulo adattivo. Il servizio Adobe Sign salva i dati utente con la firma all’interno del contratto. Il contratto viene salvato sul server Adobe Sign configurato in AEM Forms Cloud Services. Inoltre, se il modulo adattivo è configurato per utilizzare l’azione di invio di Forms Portal, i dati del contratto vengono salvati nell’archivio dati del portale dei moduli insieme ai dati del modulo.

## Accedere ed eliminare i dati utente {#access-and-delete-user-data}

I dati utente vengono raccolti all&#39;interno del contratto ma non vengono salvati in nessuna delle tabelle del servizio. Adobe Sign consente agli amministratori di effettuare le proprie scelte sulla gestione dei dati che controllano nel servizio. Gli amministratori della privacy sul servizio Adobe Sign possono elencare o rimuovere gli accordi in base all&#39;indirizzo e-mail di un richiedente.

Adobe Sign offre un’applicazione web che consente la ricerca dei contratti da parte dei partecipanti e, se necessario, la loro eliminazione. Per ulteriori informazioni, consulta [Adobe Sign - Funzionalità: Elimina informazioni utente](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

I dati dei contratti per i moduli adattivi configurati per utilizzare l’azione di invio del portale Forms vengono salvati anche nell’archivio dati del portale dei moduli. Per accedere e eliminare i dati dall’archivio dati del portale dei moduli, vedere [Portale Forms | Gestione dei dati utente](/help/forms/using/forms-portal-handling-user-data.md).
