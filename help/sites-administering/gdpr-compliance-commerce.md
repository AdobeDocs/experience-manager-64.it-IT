---
title: AEM Commercio - Preparazione GDPR
seo-title: AEM Commercio - Preparazione GDPR
description: 'null'
seo-description: 'null'
uuid: 7ca26587-8cce-4c75-8629-e0e5cfb8166c
contentOwner: carlino
discoiquuid: c637964a-dfcb-41fe-9c92-934620fe2cb3
translation-type: tm+mt
source-git-commit: 0db56cb77628b3e81b69382a314c30b43887bde6
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# AEM Commercio - Preparazione GDPR{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>Il GDPR è utilizzato come esempio nelle sezioni seguenti, ma i dettagli trattati sono applicabili a tutte le normative sulla protezione dei dati e sulla privacy; come GDPR, CCPA ecc.

Il regolamento generale dell&#39;Unione europea sulla protezione dei dati in materia di diritti sulla privacy ha effetto a maggio 2018. Per ulteriori informazioni, consulta la pagina [GDPR all’ Centro](https://www.adobe.com/privacy/general-data-protection-regulation.html)per la privacy del Adobe.

>[!NOTE]
>
>Per ulteriori informazioni, consulta [AEM preparazione](/help/managing/data-protection-and-privacy.md) al GDPR.

![screen_shot_2018-03-22at111606](assets/screen_shot_2018-03-22at111606.jpg)

Nelle integrazioni Commerce pronte all&#39;uso, AEM è il livello esperienza, i servizi di consumo e l&#39;invio di dati alla piattaforma di e-commerce del cliente che viene eseguita in modalità headless.

Per alcune piattaforme di e-commerce, vengono memorizzate le informazioni di profilo ( `/home/users`) e i token di e-commerce (per accedere alla piattaforma di e-commerce) in AEM. Per questi casi di utilizzo, leggete [Gestione delle richieste GDPR per la piattaforma](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md)AEM.

![screen_shot_2018-03-22at111621](assets/screen_shot_2018-03-22at111621.jpg)

## Gestione delle richieste GDPR per AEM Commerce {#handling-gdpr-requests-for-aem-commerce}

Per l&#39;integrazione con l&#39;Commerce Cloud Salesforce, AEM Commerce non memorizza informazioni rilevanti per il GDPR. Inoltra la richiesta a [Salesforce Cloud](https://documentation.demandware.com/).

Per le integrazioni hybris e IBM WebSphere, ci sono alcuni dati in AEM. Devi usare le istruzioni [GDPR della piattaforma](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) AEM e prendere in considerazione le seguenti domande:

1. **Dove vengono memorizzati o utilizzati i dati personali?** Le informazioni del profilo utente memorizzate nella cache, come nome, identificatore utente di e-commerce, token, password, dati dell&#39;indirizzo e così via, vengono visualizzate da AEM.
1. **Con chi condivido i dati GDPR coperti?** Qualsiasi aggiornamento dei dati GDPR rilevanti in AEM Commerce non viene memorizzato (ad eccezione delle informazioni di profilo pertinenti, come indicato sopra) ma viene proxy alla piattaforma di eCommerce.
1. **Come eliminare i dati** utente? Eliminate il profilo utente in AEM e richiamate l&#39;eliminazione dell&#39;utente sulla piattaforma di eCommerce.

>[!NOTE]
>
>Date un&#39;occhiata al wiki [hybris](https://wiki.hybris.com/) o alla documentazione [Commerce di](https://www-01.ibm.com/support/docview.wss?uid=swg27036450) Web-sfera, se necessario.

