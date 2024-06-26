---
title: Filtro di disposizione dei contenuti
seo-title: Content Disposition Filter
description: Scopri come utilizzare il filtro di disposizione dei contenuti per evitare attacchi XSS.
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 2%

---

# Filtro di disposizione dei contenuti {#content-disposition-filter}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il filtro di disposizione dei contenuti è una funzione di sicurezza contro gli attacchi XSS sui file SVG.

Una volta installato, il filtro blocca l’accesso a tutte le risorse. Ad esempio, non è stato possibile visualizzare un PDF online. Questa sezione descrive come configurare il filtro in base alle tue esigenze.

## Configura filtro di disposizione del contenuto {#configure-content-disposition-filter}

È possibile visualizzare [Filtro per la disposizione dei contenuti Apache Sling in GitHub.](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

Le opzioni Filtro disposizione contenuto forniscono le funzionalità seguenti:

* **Percorsi di disposizione del contenuto:** un elenco di percorsi in cui il filtro verrà applicato seguito da un elenco di mime-types da escludere su quel percorso. Questo percorso deve essere un percorso assoluto e può contenere un carattere jolly (`*`) alla fine, per far corrispondere ogni percorso di risorsa con il prefisso del percorso specificato. Ad esempio: `/content/*:image/jpeg,image/svg+xml` applica il filtro a ogni nodo in `/content` eccetto immagini jpg e svg

* **Percorsi risorsa esclusi:** un elenco di risorse escluse, ogni percorso di risorsa deve essere indicato come percorso assoluto e completo. I caratteri jolly/corrispondenti al prefisso non sono supportati.

* **Abilita Per Tutti I Percorsi Di Risorse:** questo flag controlla se abilitare questo filtro per tutti i percorsi, ad eccezione dei percorsi esclusi definiti dai percorsi delle risorse escluse. Impostando questo valore su &quot;true&quot; si ignorano i percorsi di disposizione del contenuto. Indipendente dalla configurazione vengono coperti solo i percorsi delle risorse che contengono una proprietà denominata `jcr:data` o
   `jcr:content jcr:data`.
