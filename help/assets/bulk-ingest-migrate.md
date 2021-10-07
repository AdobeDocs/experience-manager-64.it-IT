---
title: Installazione del Feature Pack 18912 per la migrazione in massa delle risorse
seo-title: Installing Feature Pack 18912 for bulk asset migration
description: Il Feature Pack 18912 consente di caricare in massa le risorse tramite FTP oppure di migrare le risorse da Dynamic Media Classic a Dynamic Media in AEM. Questo pacchetto di funzioni opzionale è disponibile dal supporto Adobe.
seo-description: Feature pack 18912 lets you either bulk ingest assets by way of FTP, or migrate assets from Dynamic Media Classic to Dynamic Media in AEM. This optional feature pack is available from Adobe support.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Configuration
role: Admin,User
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---

# Installazione del feature pack 18912 per la migrazione di massa delle risorse {#installing-feature-pack}

L&#39;installazione del feature pack 18912 è _opzionale_.

Il Feature Pack 18912 consente di caricare in massa le risorse direttamente in modalità Dynamic Media - Scene 7 in AEM tramite FTP oppure di migrare le risorse da Dynamic Media Classic in modalità Dynamic Media - Scene7 in AEM. Il pacchetto di funzioni è disponibile da [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Anche se è possibile utilizzare il pacchetto di funzioni per eseguire la migrazione in massa delle risorse da Dynamic Media Classic a Dynamic Media - Modalità Scene 7 in modalità AEM o per eseguire la migrazione in massa delle risorse utilizzando la funzione FTP in Dynamic Media Classic, questo metodo è consigliato da *not* a causa della complessità in questione.
>
>I pacchetti di funzioni di migrazione, come questo, sono *solo* supportati come parte di un progetto di migrazione tramite [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

Prima di poter installare questo feature pack, è necessario creare un utente del servizio e fornire ad Adobe tali informazioni.

Vedi anche [Configurazione di Dynamic Media - Modalità Scene7](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**Per installare il feature pack 18912 per la migrazione** di massa delle risorse,

1. Nella tua istanza AEM, passa a **[!UICONTROL Strumenti > Protezione > Utenti > Crea utente]**. L&#39;utente del servizio deve disporre delle autorizzazioni di lettura/scrittura per `/content/dam`.
1. Nei campi **[!UICONTROL ID]** e **[!UICONTROL Password]** , immetti un nome utente e una password; ad esempio, `FTP User`. Questo nome viene visualizzato nella timeline come utente che ha creato la risorsa. Quando una risorsa viene caricata da FTP, viene considerata una creazione quando viene caricata sul server FTP e inviata a AEM.
1. Contatta il [Adobe Customer Support per Experience Manager](https://helpx.adobe.com/it/contact/enterprise-support.ec.html) per richiedere l&#39;accesso al feature pack 18912 per il download. Quando si contatta l&#39;assistenza, potrebbe essere necessario disporre delle seguenti informazioni:

   * Indirizzo IP del server per l’istanza Author, incluso il numero di porta (per impostazione predefinita, il numero di porta è 4502).
   * AEM nome utente e password del servizio dal passaggio precedente.

1. Adobe Customer Support per AEM fornisce le credenziali FTP e l&#39;accesso al feature pack 18912.

1. Quando ricevi il feature pack 18912, installalo.

   Per ulteriori informazioni sull&#39;utilizzo di Distribuzione software e pacchetti in AEM, consulta [Come lavorare con i pacchetti](/help/sites-administering/package-manager.md) .
