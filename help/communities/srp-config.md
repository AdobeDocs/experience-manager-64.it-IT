---
title: Configurazione dell’archiviazione
seo-title: Configurazione dell’archiviazione
description: Accesso alla console di configurazione dell'archiviazione
seo-description: Accesso alla console di configurazione dell'archiviazione
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 4%

---


# Configurazione dell’archiviazione {#storage-configuration}

La configurazione dello storage è il mezzo per identificare lo storage scelto per il contenuto della community, noto anche come contenuto generato dall’utente (UGC).

Questa impostazione informa il codice AEM Communities in merito all&#39;implementazione del provider di risorse di archiviazione (SRP) da utilizzare per l&#39;accesso a UGC e deve riflettere la topologia stabilita al momento della distribuzione di AEM.

Per una discussione sulle opzioni di storage e sulle topologie di distribuzione, visita

* [Archivio dei contenuti della community](working-with-srp.md)
* [Topologie consigliate](topologies.md)

## Console di configurazione dello storage {#storage-configuration-console}

![chlimage_1-188](assets/chlimage_1-188.png)

Nell’ambiente di authoring, per raggiungere la console di configurazione dello storage

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Configurazione dello storage]**

Per selezionare un&#39;opzione di archiviazione diversa dal JCR predefinito:

* seleziona un’opzione
* Configurare in modo appropriato

   * Vedere i dettagli per [selezionare MSRP](msrp.md#select-msrp)
   * Vedere i dettagli per [selezionare DSRP](dsrp.md#select-dsrp)
   * Vedere i dettagli per [selezionare ASRP](asrp.md#select-asrp)

* Seleziona **[!UICONTROL Invia]**

### Informazioni su JCR Storage {#about-jcr-storage}

Se non viene effettuata alcuna selezione, l’impostazione predefinita è l’archivio AEM, JCR.

JCR è *non* un archivio comune condiviso dagli ambienti di authoring e pubblicazione. Il contenuto della community sarà visibile solo dall’ambiente di authoring o pubblicazione in cui è stato creato.

Visita [JCR Store](jsrp.md) per ulteriori informazioni.

>[!NOTE]
>
>L&#39;assenza del nodo `srpc`sotto `/etc/socialconfig` indica il valore predefinito [JCR store](jsrp.md).

