---
title: Suggerimenti per ridurre al minimo la crescita del database
seo-title: Tips for minimizing database growth
description: I processi a lungo termine memorizzano i dati del processo nel database dei moduli AEM. La crescita del database dei moduli AEM può essere ridotta al minimo utilizzando alcune semplici strategie di progettazione del processo e di configurazione del prodotto.
seo-description: Long-lived processes store process data in the AEM forms database. The growth of the AEM forms database can be minimized using a few easy process design and product configuration strategies.
uuid: 13f99d4f-848e-451e-90d9-55e202dc0bdb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 89441336-babc-4d1f-9053-d1566cd42d22
exl-id: 7b266170-c7e2-42e7-8ee0-153e1e73a901
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---

# Suggerimenti per ridurre al minimo la crescita del database {#tips-for-minimizing-database-growth}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I processi a lungo termine memorizzano i dati del processo nel database dei moduli AEM. La crescita del database dei moduli AEM può essere ridotta al minimo utilizzando alcune semplici strategie di progettazione del processo e di configurazione del prodotto.

## Suggerimenti per la progettazione del processo {#process-design-tips}

Utilizzare processi di breve durata quando possibile. I processi di breve durata non memorizzano i dati di processo nel database. Lo svantaggio di utilizzare i processi di breve durata è che lo stato e lo stato non vengono tracciati nella console di amministrazione e non c&#39;è storia del processo.

Alcune operazioni di servizio, come l&#39;operazione Assegna attività (servizio utente), richiedono che siano utilizzate in processi di lunga durata. In questo caso, puoi segmentare il processo in diversi sottoprocessi e renderlo di breve durata quando possibile. Se si utilizza questa strategia, i processi secondari di breve durata devono gestire elementi di dati di grandi dimensioni, ad esempio i valori del documento.

Utilizza le variabili con moderazione. Quando si utilizzano processi di lunga durata, per ogni istanza di processo viene allocato spazio nel database per ogni variabile del processo. L&#39;uso strategico delle variabili può risparmiare una notevole quantità di spazio. Ad esempio, puoi sovrascrivere i valori delle variabili quando nel processo non sono più necessari i vecchi valori. Elimina inoltre le variabili create e non in uso. Puoi convalidare il processo per trovare le variabili non utilizzate.

Utilizza tipi di variabili semplici (ad esempio stringa o int) ed evita di utilizzare tipi di variabili complesse quando possibile. Lo spazio del database è allocato per le variabili anche quando non contengono un valore. Le variabili complesse in genere richiedono più spazio di quelle semplici.

## Suggerimenti per l’amministrazione del prodotto {#product-administration-tips}

Utilizzare l&#39;archiviazione globale dei documenti (GDS) in modo efficace. La directory GDS sul server dei moduli viene utilizzata, tra l’altro, per memorizzare i file che vengono passati ai servizi che fanno parte dei moduli AEM nei processi. Per migliorare le prestazioni, i documenti più piccoli vengono invece memorizzati in memoria e memorizzati nel database.

la console di amministrazione espone la proprietà Dimensione in linea massima documento predefinita per configurare la dimensione massima dei documenti memorizzati in memoria e memorizzati nel database. (Vedi [Configurare le impostazioni generali dei moduli AEM](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).) Se si imposta questa proprietà su un valore basso, la maggior parte dei documenti viene mantenuta nella directory GDS anziché nel database. Il vantaggio è che è possibile eliminare più facilmente i file quando non sono più necessari quando vengono memorizzati nella directory GDS.
