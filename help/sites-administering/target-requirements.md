---
title: Prerequisiti per l’integrazione con Adobe Target
seo-title: Prerequisites for Integrating with Adobe Target
description: Scopri i prerequisiti per l’integrazione con Adobe Target.
seo-description: Find out about the prerequisites for integrating with Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
exl-id: f47e5c6a-ed52-4493-83bd-73e5e693d117
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 8%

---

# Prerequisiti per l’integrazione con Adobe Target{#prerequisites-for-integrating-with-adobe-target}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Come parte del [Integrazione di AEM e Adobe Target](/help/sites-administering/target.md), è necessario registrarsi con Adobe Target, configurare l’agente di replica e proteggere le impostazioni delle attività sul nodo di pubblicazione.

## Registrazione con Adobe Target {#registering-with-adobe-target}

Per integrare AEM con Adobe Target, è necessario disporre di un account Adobe Target valido. Questo account deve avere almeno le autorizzazioni a livello di **approver **level. Quando ti registri ad Adobe Target, ricevi un codice cliente. Per connettersi AEM ad Adobe Target è necessario il codice client e il nome di accesso e la password di Adobe Target.

Il codice client identifica l&#39;account cliente Adobe Target quando si chiama il server Adobe Target.

>[!NOTE]
>
>Per poter utilizzare l’integrazione, l’account deve essere abilitato anche dal team di Target.
>
>
>In caso contrario, contattare [Assistenza clienti Adobe Target](https://experienceleague.adobe.com/docs/target/using/cmp-resources-and-contact-information.html).

## Abilitazione dell’agente di replica di Target {#enabling-the-target-replication-agent}

Test e Target [agente di replica](/help/sites-deploying/replication.md) deve essere abilitato nell’istanza di authoring. Tieni presente che questo agente di replica non è abilitato per impostazione predefinita se è stato utilizzato il [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) modalità di esecuzione per l&#39;installazione di AEM. Per ulteriori informazioni sulla protezione dell&#39;ambiente di produzione, consulta [Lista di controllo sicurezza](/help/sites-administering/security-checklist.md).

1. Nella home page di AEM, tocca o fai clic su **Strumenti** > **Distribuzione** > **Replica**.
1. Tocca o fai clic su **Agenti sull&#39;autore**.
1. Tocca o fai clic su **Test e Target (test e target)** agente di replica, quindi tocca o fai clic su **Modifica**.
1. Seleziona l’opzione Attivato, quindi tocca o fai clic su **OK**.

   >[!NOTE]
   >
   >Quando configuri l’agente di replica Test e Target, nella **Trasporti** scheda , l’URI è impostato per impostazione predefinita su **tnt:///**. Non sostituire questo URI con **https://admin.testandtarget.omniture.com**.
   >
   >Se provi a verificare la connessione con **tnt:///**, genererà un errore. Questo comportamento è previsto perché questo URI è solo per uso interno e non deve essere utilizzato con **Prova connessione**.

## Protezione del nodo Impostazioni attività {#securing-the-activity-settings-node}

È necessario proteggere il nodo delle impostazioni delle attività **cq:ActivitySettings** sull&#39;istanza di pubblicazione in modo che sia inaccessibile agli utenti normali. Il nodo delle impostazioni delle attività deve essere accessibile solo al servizio che gestisce la sincronizzazione delle attività con Adobe Target.

La **cq:ActivitySettings** node è disponibile in CRXDE lite in `/content/campaigns/*nameofbrand*`* *sotto il nodo jcr:content delle attività;* *ad esempio `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Questo nodo viene creato solo dopo aver eseguito il targeting di un componente.

La **cq:ActivitySettings** il nodo sotto il jcr:content dell&#39;attività è protetto dalle seguenti ACL:

* Nega tutto per tutti
* Consenti jcr:read,rep:write per &quot;target-activity-authors&quot; (l&#39;autore è un membro di questo gruppo pronto all&#39;uso)
* Consenti jcr:read,rep:write per &quot;targetservice&quot;

Queste impostazioni assicurano che gli utenti normali non abbiano accesso alle proprietà del nodo. Utilizza gli stessi ACL sull&#39;autore e sulla pubblicazione. Vedi [Amministrazione degli utenti e sicurezza](/help/sites-administering/security.md) per ulteriori informazioni.

## Configurazione dell’esternalizzatore AEM {#configuring-the-aem-externalizer}

Quando modifichi un’attività in Adobe Target, l’URL punta a **localhost** a meno che non modifichi l’URL sul nodo di authoring AEM.

Per configurare l&#39;esternalizzatore AEM:

1. Passa alla console web OSGi all’indirizzo **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Trova **Day CQ Link Externalizer** e immetti il dominio per il nodo autore.

   ![chlimage_1-120](assets/chlimage_1-120.png)
