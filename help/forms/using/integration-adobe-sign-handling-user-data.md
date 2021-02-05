---
title: Integrazione con  Adobe Sign | Gestione dei dati utente
seo-title: Integrazione con  Adobe Sign | Gestione dei dati utente
description: ' AEM Forms si integra con  Adobe Sign per abilitare i flussi di lavoro di firma elettronica nei moduli adattivi per l''elaborazione di moduli o accordi per flussi di lavoro legali, di vendita, di retribuzione e di gestione delle risorse umane. Approfondisci i dati utente, gli archivi dati e accedi ed elimina i dati utente.'
seo-description: ' AEM Forms si integra con  Adobe Sign per abilitare i flussi di lavoro di firma elettronica nei moduli adattivi per l''elaborazione di moduli o accordi per flussi di lavoro legali, di vendita, di retribuzione e di gestione delle risorse umane. Approfondisci i dati utente, gli archivi dati e accedi ed elimina i dati utente.'
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
translation-type: tm+mt
source-git-commit: c2dcb61d65cfc5867525f5b39769da0450d92f39
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Integrazione con  Adobe Sign | Gestione dei dati utente {#integration-with-adobe-sign-handling-user-data}

 AEM Forms si integra con  Adobe Sign per abilitare i flussi di lavoro di firma elettronica nei moduli adattivi per l&#39;elaborazione di moduli o accordi per flussi di lavoro legali, di vendita, di retribuzione e di gestione delle risorse umane. Consente la firma single e multiutente, flussi di lavoro di firma sequenziali e simultanei, la firma dei moduli come utente anonimo o connesso e diversi modi per l&#39;autenticazione degli utenti.

Quando uno o più firmatari firmano e inviano un modulo adattivo, viene generato un accordo Adobe Sign  che include informazioni sui firmatari.

Per ulteriori informazioni sullintegrazione AEM Forms con  Adobe Sign, vedere [Utilizzo  Adobe Sign in un modulo adattivo](/help/forms/using/working-with-adobe-sign.md).

## Archivio dati utente {#data}

 modulo adattivo abilitato per Adobe Sign include informazioni sui firmatari e può includere altri dati utente raccolti dal modulo adattivo. Il servizio Adobe Sign  salva i dati utente con la firma all&#39;interno dell&#39;accordo. L&#39;accordo viene salvato  server Adobe Sign configurato  servizi cloud AEM Forms. Inoltre, se il modulo adattivo è configurato per l&#39;utilizzo dell&#39;azione di invio di Forms Portal, i dati del contratto vengono salvati nell&#39;archivio dati del portale moduli insieme ai dati del modulo.

## Accesso ed eliminazione dei dati utente {#access-and-delete-user-data}

I dati utente vengono raccolti all&#39;interno del contratto ma non salvati in nessuna delle tabelle dei servizi.  Adobe Sign consente agli amministratori di effettuare le proprie scelte sulla gestione dei dati che controllano nel servizio. Gli amministratori della privacy nel  servizio Adobe Sign possono elencare o rimuovere i contratti in base all&#39;indirizzo e-mail di un richiedente.

 Adobe Sign offre un&#39;applicazione Web che consente la ricerca degli accordi da parte dei partecipanti e, se necessario, l&#39;eliminazione. Per ulteriori informazioni, vedere [ Adobe Sign - Feature: Elimina informazioni utente](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

I dati degli accordi per i moduli adattivi configurati per utilizzare l&#39;azione di invio di Forms Portal vengono salvati anche nell&#39;archivio dati del portale moduli. Per accedere ed eliminare dati dall&#39;archivio dati del portale moduli, vedere [Portale Forms | Gestione dei dati utente](/help/forms/using/forms-portal-handling-user-data.md).
