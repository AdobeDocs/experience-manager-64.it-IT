---
title: Best practice per tradurre le risorse in modo efficiente
description: Procedure consigliate per una gestione efficiente delle risorse, al fine di sincronizzare diverse versioni tradotte e semplificare i flussi di lavoro di traduzione.
contentOwner: AG
feature: Translation
role: User,Admin
exl-id: 15162b80-ddef-4ec0-9db6-36695c93ebb1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 2%

---

# Best practice per tradurre le risorse in modo efficiente {#best-practices-for-translating-assets-efficiently}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets supporta flussi di lavoro multilingue per tradurre file binari, metadati e tag per risorse digitali in più lingue e gestire le risorse tradotte. Per maggiori dettagli, vedi [Risorse multilingue](multilingual-assets.md).

Per una gestione efficiente delle risorse, assicurati che le diverse versioni tradotte rimangano sincronizzate, crea [copie per lingua](preparing-assets-for-translation.md) delle risorse prima di eseguire i flussi di lavoro di traduzione.

Una copia in lingua di una risorsa o di un gruppo di risorse è di pari livello (o una versione delle risorse in un linguaggio cognato) con una gerarchia dei contenuti simile.

Ogni copia in lingua è una risorsa indipendente. Pertanto, tradurre le risorse in più impostazioni internazionali può aumentare drasticamente le dimensioni dell’archivio CRX. Ad esempio, la traduzione di risorse con una dimensione combinata di 10 GB in due lingue può aumentare la dimensione dell’archivio di circa 20 GB (10 GB per ogni lingua).

I file binari delle risorse occupano uno spazio di archiviazione molto più ampio rispetto ai metadati e ai tag. Pertanto, se tradurre metadati e tag serve solo al tuo scopo, ometti di tradurre i binari. È possibile conservare la copia originale dei file binari nell’archivio per associarli ai metadati e ai tag tradotti in lingue diverse. Mantenere una sola copia dei file binari, invece di più versioni tradotte, riduce al minimo l&#39;impatto sulle dimensioni dell&#39;archivio.

File Data Store e Amazon S3 Data Store forniscono un&#39;infrastruttura di storage più adatta a questi scenari. Questi archivi di archiviazione memorizzano una singola copia dei file binari delle risorse (incluse le rappresentazioni) che possono essere condivisi da metadati e tag in più impostazioni internazionali. Pertanto, la creazione di copie della lingua delle risorse e la traduzione di metadati e tag non influisce sulle dimensioni dell’archivio.

Puoi anche apportare alcune modifiche alla configurazione di un paio di flussi di lavoro e del framework di integrazione della traduzione per semplificare ulteriormente il processo.

1. Effettua una delle operazioni seguenti:

   * [Imposta archivio dati file](/help/sites-deploying/data-store-config.md)
   * [Configurazione archivio dati Amazon S3](/help/sites-deploying/data-store-config.md)

1. Disattiva la [Writeback di metadati DAM](/help/sites-administering/workflow-offloader.md#disable-offloading) workflow

   Come suggerisce il nome, il *Writeback di metadati DAM* riscrive i metadati nel file binario. Poiché i metadati cambiano dopo la traduzione, riscriverli nel file binario genera un binario diverso per una copia della lingua.

   >[!NOTE]
   >
   >Disabilitazione della *Writeback di metadati DAM* il flusso di lavoro disattiva XMP riscrittura dei metadati sui binari delle risorse. Di conseguenza, le future modifiche ai metadati non verranno più salvate nelle risorse. Valuta le conseguenze prima di disabilitare questo flusso di lavoro.

1. Abilita la *Imposta data ultima modifica* workflow.

   La *Writeback di metadati DAM* configura l’ultima data di modifica per una risorsa. Poiché disattivi questo flusso di lavoro nel passaggio 2, [!DNL Experience Manager Assets] non è più in grado di mantenere aggiornata l’ultima data di modifica delle risorse. Pertanto, abilita *Imposta data ultima modifica* per garantire che le ultime date di modifica delle risorse siano aggiornate. Le risorse con date dell’ultima modifica non aggiornate possono causare errori.

1. [Configurare il framework di integrazione della traduzione](/help/sites-administering/tc-tic.md) per interrompere la traduzione dei binari delle risorse. Deseleziona l’opzione &quot;Traduci risorse&quot; nella scheda Risorse per interrompere la traduzione dei file binari delle risorse.
1. Tradurre metadati/tag delle risorse utilizzando [Flussi di lavoro per risorse multilingue](multilingual-assets.md).
