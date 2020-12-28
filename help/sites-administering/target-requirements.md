---
title: Prerequisiti per l’integrazione con  Adobe Target
seo-title: Prerequisiti per l’integrazione con  Adobe Target
description: Scoprite i prerequisiti per l'integrazione con  Adobe Target.
seo-description: Scoprite i prerequisiti per l'integrazione con  Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 3%

---


# Prerequisiti per l&#39;integrazione con  Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Come parte dell&#39;integrazione di [AEM e  Adobe Target](/help/sites-administering/target.md), è necessario registrarsi  Adobe Target, configurare l&#39;agente di replica e le impostazioni dell&#39;attività protetta sul nodo di pubblicazione.

## Registrazione con  Adobe Target {#registering-with-adobe-target}

Per integrare AEM con  Adobe Target, è necessario disporre di un account  Adobe Target valido. Questo account deve avere un **approver **autorizzazioni di livello minimo. Quando vi registrate  Adobe Target, ricevete un codice cliente. Per connettersi AEM a  Adobe Target, è necessario disporre del codice client e del nome di accesso e della password  Adobe Target.

Il Codice client identifica l&#39;account cliente Adobe Target  quando si chiama il server Adobe Target .

>[!NOTE]
>
>Per poter utilizzare l&#39;integrazione, l&#39;account deve essere abilitato anche dal team di Target.
>
>
>In caso contrario, contattare l&#39;Assistenza clienti di Adobe Target [](https://docs.adobe.com/content/help/en/target/using/cmp-resources-and-contact-information.html).

## Abilitazione dell&#39;agente di replica di destinazione {#enabling-the-target-replication-agent}

L&#39;agente di replica Test e Target [agente di replica](/help/sites-deploying/replication.md) deve essere abilitato nell&#39;istanza di creazione. Questo agente di replica non è abilitato per impostazione predefinita se per l&#39;installazione del AEM è stata utilizzata la modalità di esecuzione [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent). Per ulteriori informazioni sulla protezione dell&#39;ambiente di produzione, vedere [Elenco di controllo della sicurezza](/help/sites-administering/security-checklist.md).

1. Nella pagina principale AEM, fare clic o toccare **Strumenti** > **Distribuzione** > **Replica**.
1. Tocca o fai clic su **Agenti sull&#39;autore**.
1. Tocca o fai clic sull&#39;agente di replica **Test and Target (test and target)**, quindi tocca o fai clic su **Edit**.
1. Selezionate l&#39;opzione Attivato, quindi toccate o fate clic su **OK**.

   >[!NOTE]
   >
   >Quando configurate l&#39;agente di replica Test e Target, nella scheda **Transport** l&#39;URI è impostato per impostazione predefinita su **tnt:///**. Non sostituire questo URI con **https://admin.testandtarget.omniture.com**.
   >
   >Se si tenta di verificare la connessione con **tnt:///**, verrà generato un errore. Questo comportamento è previsto perché l&#39;URI è solo per uso interno e non deve essere utilizzato con **Test Connection**.

## Protezione del nodo delle impostazioni dell&#39;attività {#securing-the-activity-settings-node}

È necessario proteggere il nodo delle impostazioni dell&#39;attività **cq:ActivitySettings** nell&#39;istanza di pubblicazione in modo che sia inaccessibile agli utenti normali. Il nodo delle impostazioni delle attività deve essere accessibile solo al servizio che gestisce la sincronizzazione delle attività con Adobe Target.

Il nodo **cq:ActivitySettings** è disponibile in CRXDE lite in `/content/campaigns/*nameofbrand*`* *sotto il nodo jcr:content delle attività;* *ad esempio `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Questo nodo viene creato solo dopo aver eseguito il targeting di un componente.

Il nodo **cq:ActivitySettings** sotto il nodo jcr:content dell&#39;attività è protetto dai seguenti ACL:

* Nega tutti per tutti
* Consenti jcr:read,rep:write per &quot;target-activity-authors&quot; (l’autore è un membro di questo gruppo)
* Consenti jcr:read,rep:write per &quot;target service&quot;

Queste impostazioni assicurano che gli utenti normali non abbiano accesso alle proprietà del nodo. Utilizzate gli stessi ACL per l&#39;autore e la pubblicazione. Per ulteriori informazioni, vedere [Amministrazione utente e sicurezza](/help/sites-administering/security.md).

## Configurazione dell&#39;esternalizzatore AEM {#configuring-the-aem-externalizer}

Durante la modifica di un&#39;attività in  Adobe Target, l&#39;URL punta a **localhost** a meno che non cambiate l&#39;URL sul nodo di creazione AEM.

Per configurare l&#39;esternalizzatore AEM:

1. Andate alla console Web OSGi all&#39;indirizzo **https://&lt;server>:&lt;porta>/system/console/configMgr.**
1. Trovate **Day CQ Link Externalizer** e immettete il dominio per il nodo dell&#39;autore.

   ![chlimage_1-120](assets/chlimage_1-120.png)

