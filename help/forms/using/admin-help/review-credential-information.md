---
title: Verifica informazioni sull'uso delle credenziali
seo-title: Review credential use information
description: Scopri come esaminare le informazioni sull’uso delle credenziali.
seo-description: Learn how to review credential use information.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 3%

---

# Verifica informazioni sull&#39;uso delle credenziali {#review-credential-use-information}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La credenziale contiene informazioni che ne descrivono l’uso previsto, accessibili tramite l’applicazione Web per l’utente finale di Acrobat Reader DC extensions. È possibile utilizzare queste informazioni per determinare il tipo di credenziale installata (valutazione o produzione) e le relative date di validità.

1. Apri un browser web e immetti questo URL:

   http://localhost *[porta]*/ReaderExtensions (dove *[porta]* è il numero di porta del server dell&#39;applicazione)

1. Accedi utilizzando il nome utente e la password predefiniti:

   Nome utente: amministratore

   Password: password

   >[!NOTE]
   >
   >Per effettuare l&#39;accesso utilizzando il nome utente e la password predefiniti, è necessario disporre dei privilegi di amministratore o utente avanzato. Per consentire ad altri utenti di accedere alle estensioni Acrobat Reader DC, crea gli account utente in Gestione utente e assegna agli utenti il ruolo Applicazione Web di Acrobat Reader DC extensions.

1. Selezionare l&#39;alias delle credenziali dall&#39;elenco Seleziona credenziali e esaminare le informazioni incluse nella Data di scadenza e nell&#39;avviso di utilizzo previsto.

>[!NOTE]
>
>La data di scadenza della credenziale è disponibile anche nella pagina Impostazioni > Gestione dell’archivio attendibilità > Credenziali locali della console di amministrazione, in Data di scadenza.
