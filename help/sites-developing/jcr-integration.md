---
title: Integrazione JCR
seo-title: JCR Integration
description: Suggerimenti per quando è necessario integrare a livello JCR
seo-description: Tips for when you must integrate at the JCR level
uuid: 11518baf-521e-471d-ad4f-2baa76075cfa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: e6647a11-a36e-4808-bb61-29b2895c6b1d
exl-id: 3e9727a5-32f8-40ad-aa06-619f50d109b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 2%

---

# Integrazione JCR{#jcr-integration}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Preferisci l’API della risorsa Sling all’API JCR {#prefer-the-sling-resource-api-to-jcr-api}

L’API Sling funziona a un livello più alto e astratto rispetto all’API JCR. Questo consente al codice di essere più riutilizzabile e indipendente dalla memorizzazione sottostante. In questo modo è più facile includere i dati virtuali esterni tramite il meccanismo ResourceProvider, se necessario.

## Evitare le query laddove possibile {#avoid-queries-wherever-possible}

È sempre più veloce navigare nell’archivio per recuperare i dati rispetto all’esecuzione di una query. Ci sono casi in cui saranno necessarie query, come una query utente finale o la necessità di trovare contenuto strutturato dall&#39;intero archivio, ma per tutti gli altri casi, è preferibile passare ai nodi necessari. Le query devono sempre essere evitate nella logica di rendering, come i componenti di navigazione, un &quot;elenco di elementi recenti&quot;, un conteggio di elementi e così via. In questi casi, è meglio attraversare la gerarchia o pre-memorizzare il risultato in modo che possa essere utilizzato direttamente durante il rendering.

## Limitare il campo di applicazione dell&#39;osservazione JCR {#restrict-the-scope-of-jcr-observation}

Quando si ascoltano gli eventi nell’archivio, è importante restringere l’ambito il più possibile. Ad esempio, è molto meglio ascoltare un evento in `/etc/mycompany` che ascoltare `/etc`. Non ascoltare mai gli eventi nella directory principale dell’archivio. Inoltre, assicurati che i metodi di callback vengano eseguiti il più rapidamente possibile quando non è possibile eseguire alcuna operazione.

## Elimina l&#39;utilizzo dell&#39;accesso amministratore JCR {#eliminate-use-of-jcr-admin-access}

A partire dal AEM 6, l&#39;accesso Amministrazione è stato dichiarato obsoleto e ha ricevuto una sessione amministrativa da ResourceResolverFactory. Piuttosto, gli account di servizio devono essere creati per le operazioni di back office che richiederebbero questo tipo di accesso e ResourceResolverFactory può essere utilizzato per ottenere un ResourceResolver per questo account.
