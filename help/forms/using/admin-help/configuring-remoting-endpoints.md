---
title: Configurazione degli endpoint remoti
seo-title: Configuring Remoting endpoints
description: Scopri come configurare gli endpoint remoti.
seo-description: Learn how to configure remoting endpoints.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---

# Configurazione degli endpoint remoti {#configuring-remoting-endpoints}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Un endpoint remoto consente a un&#39;applicazione creata con Flex di richiamare il servizio utilizzando (obsoleto per i moduli AEM) AEM Remoting dei moduli. Viene creato automaticamente un endpoint remoto per ogni servizio attivato. Una destinazione Flex con lo stesso nome dell&#39;endpoint viene creata e i client Flex possono creare oggetti remoti che puntano a questa destinazione per richiamare le operazioni sul servizio pertinente.

## Impostazioni endpoint remoto {#remoting-endpoint-settings}

**Metodo di autenticazione client Flex:** Determina il tipo di risposta che il server invia al client quando il servizio richiamato è protetto, l&#39;operazione richiamata non supporta le chiamate anonime e il client trasmette credenziali non valide o non valide.
