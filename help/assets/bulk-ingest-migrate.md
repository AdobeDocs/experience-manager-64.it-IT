---
title: Installazione di Feature Pack 18912 per la migrazione di massa delle risorse
seo-title: Installazione di Feature Pack 18912 per la migrazione di massa delle risorse
description: Il Feature Pack 18912 consente di caricare le risorse in blocco tramite FTP o di migrare le risorse da Dynamic Media Classic a Dynamic Media in AEM. Questo pacchetto di funzioni opzionale è disponibile dal supporto Adobe.
seo-description: Il Feature Pack 18912 consente di caricare le risorse in blocco tramite FTP o di migrare le risorse da Dynamic Media Classic a Dynamic Media in AEM. Questo pacchetto di funzioni opzionale è disponibile dal supporto Adobe.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# Installazione del feature pack 18912 per la migrazione di massa delle risorse {#installing-feature-pack}

L&#39;installazione del feature pack 18912 è _opzionale_.

Il Feature Pack 18912 consente di trasferire le risorse direttamente in contenuti multimediali dinamici - modalità Scene7 su AEM tramite FTP, oppure di migrare le risorse da Dynamic Media Classic a Dynamic Media - modalità Scene7 su AEM. Il pacchetto di funzioni è disponibile presso [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Sebbene sia possibile utilizzare il pacchetto di funzioni per migrare in massa le risorse in modo autonomo da Dynamic Media Classic a Dynamic Media - Scene7 in AEM o per migrare in massa le risorse tramite la funzione FTP in Dynamic Media Classic, Adobe *non* consiglia questo metodo a causa della complessità in questione.
>
>I pacchetti di funzionalità di migrazione, come questo, sono supportati *solo* come parte di un progetto di migrazione tramite [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

Prima di installare questo pacchetto di funzionalità, è necessario creare un utente di servizi e fornire tali informazioni ad Adobe.

Consultate anche [Configurazione di contenuti multimediali dinamici - modalità](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)Scene7.

**Per installare feature pack 18912 per la migrazione** in massa delle risorse,

1. Nell’istanza di AEM, andate a **[!UICONTROL Strumenti > Protezione > Utenti > Crea utente]**. Questo utente del servizio deve disporre delle autorizzazioni di lettura/scrittura per `/content/dam`.
1. Nei campi **[!UICONTROL ID]** e **[!UICONTROL Password]** , immettete un nome utente e una password; ad esempio, `FTP User`. Questo nome viene visualizzato nella timeline come utente che ha creato la risorsa. Quando una risorsa viene caricata dall’FTP, viene considerata creata quando viene caricata sul server FTP e inviata ad AEM.
1. Contatta il supporto [Adobe Enterprise per Experience Manager](https://helpx.adobe.com/contact/enterprise-support.ec.html) per richiedere l’accesso al feature pack 18912 da scaricare. Quando contattate il supporto, potreste aver bisogno delle seguenti informazioni:

   * Indirizzo IP del server per l’istanza Author, incluso il numero di porta (per impostazione predefinita, il numero di porta è 4502).
   * Nome utente e password del servizio AEM dal passaggio precedente.

1. Il supporto Adobe Enterprise per AEM fornisce le credenziali FTP e l&#39;accesso al feature pack 18912.

1. Quando si riceve il pacchetto di funzionalità 18912, installarlo.

   Consultate [Come lavorare con i pacchetti](/help/sites-administering/package-manager.md) per ulteriori informazioni sull&#39;utilizzo di Package Share e dei pacchetti in AEM.

