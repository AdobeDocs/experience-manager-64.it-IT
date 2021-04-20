---
title: Condivisione di cartelle AEM Assets con Creative Cloud
description: Configurazione e best practice per consentire agli utenti di Adobe Experience Manager Assets di scambiare cartelle di risorse con gli utenti di Adobe Creative Cloud.
contentOwner: AG
feature: Collaboration
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---


# AEM alle best practice per la condivisione delle cartelle {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>La funzione AEM alla condivisione cartelle Creative Cloud è obsoleta. Adobe consiglia vivamente di utilizzare funzionalità più recenti come [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) o [AEM app desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Ulteriori informazioni sono disponibili nelle [procedure consigliate per l&#39;integrazione di AEM e Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager (AEM) può essere configurato per consentire agli utenti di AEM Assets di condividere cartelle con gli utenti di Creative Cloud, in modo che siano disponibili come cartelle condivise nel servizio Creative Cloud Assets. La funzione può essere utilizzata per scambiare file tra i team creativi e gli utenti AEM Assets, specialmente quando gli utenti creativi non hanno accesso all’istanza AEM Assets (non sono sulla rete aziendale).

Questo tipo di integrazione può essere utilizzato in entrambi i casi d’uso, soprattutto quando si lavora con utenti che non hanno accesso diretto ad AEM Assets:

* Condivisione di un set di risorse specifiche da AEM Assets con gli utenti di Creative Cloud Files (ad esempio, una descrizione creativa e un set di risorse approvate per lavori di progettazione per una nuova attività di marketing)
* Ricezione di nuovi file da parte degli utenti di Creative Cloud.

>[!NOTE]
>
>Prima di leggere questo documento, puoi rivedere le [best practice generali sull&#39;integrazione di AEM e Creative Cloud](aem-cc-integration-best-practices.md) per una panoramica di livello superiore dell&#39;argomento.

## Panoramica {#overview}

AEM la condivisione delle cartelle su Creative Cloud si basa sulla condivisione lato server di cartelle e file tra account AEM Assets e Creative Cloud. I creativi professionisti, che utilizzano l&#39;applicazione desktop Creative Cloud sul desktop, possono inoltre rendere le cartelle condivise disponibili direttamente sui loro dischi utilizzando la tecnologia Adobe CreativeSync.

Il diagramma seguente fornisce una panoramica dell’integrazione.

![chlimage_1-406](assets/chlimage_1-406.png)

L’integrazione include i seguenti elementi:

* **Server AEM Assets** implementato nella rete aziendale (servizi gestiti o on-premise): La condivisione delle cartelle viene avviata qui.
* **Servizio** principale di Adobe Marketing Cloud Assets: funge da intermediario tra i servizi di storage AEM e Creative Cloud. L’amministratore dell’azienda che utilizza l’integrazione deve stabilire una relazione di trust tra l’organizzazione del Marketing Cloud e l’istanza AEM Assets. Inoltre [definiscono un elenco di collaboratori di Creative Cloud approvati](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html?lang=en#assets), che gli utenti AEM Assets possono condividere anche le cartelle per ulteriore sicurezza.
* **Creative Cloud servizi Web Assets**  (interfaccia web di archiviazione e Creative Cloud file): In questo caso, gli utenti Creative Cloud specifici con cui è stata condivisa una cartella AEM Assets possono accettare l’invito e visualizzare la cartella nell’archivio dell’account Creative Cloud.
* **Creative Cloud applicazione** desktop: (Facoltativo) Consente l’accesso diretto a cartelle/file condivisi dal desktop dell’utente creativo tramite sincronizzazione con l’archiviazione Creative Cloud Assets.

## Caratteristiche e limitazioni {#characteristics-and-limitations}

* **Propagazione unidirezionale delle modifiche:** le modifiche ai file vengono propagate in una sola direzione, dal sistema (AEM o Creative Cloud risorse), in cui la risorsa è stata originariamente creata (caricata). L’integrazione non fornisce una sincronizzazione bidirezionale completamente automatizzata tra i due sistemi.

* **Gestione versioni:**

   * AEM crea solo versioni di una risorsa sugli aggiornamenti se il file è stato creato in AEM e vi viene aggiornato.
   * Creative Cloud Assets fornisce la propria [funzionalità di controllo delle versioni](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) destinata agli aggiornamenti di Work In Progress (in sostanza, memorizza gli aggiornamenti per un massimo di 10 giorni)

* **Limitazioni dello spazio:** Le dimensioni e i volumi dei file scambiati sono limitati dalla  [Creative Cloud specifica delle risorse ](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) per gli utenti creativi (dipende dal livello di abbonamento) e da una limitazione delle dimensioni massime dei file pari a 5 GB. Lo spazio è inoltre limitato dalla quota di risorse di cui dispone l’organizzazione nel servizio di base Adobe Marketing Cloud Assets.

* **Requisiti di spazio:** anche i file nelle cartelle condivise devono essere fisicamente memorizzati in AEM e quindi nell’account Creative Cloud, con una copia nella cache nel servizio core Assets di Marketing Cloud.
* **Rete e larghezza di banda:** i file in cartelle condivise e tutti gli aggiornamenti devono essere trasportati attraverso la rete tra i sistemi. Assicurati che siano condivisi solo i file e gli aggiornamenti pertinenti.
* **Tipo** cartella: La condivisione di una cartella di risorse di tipo  `sling:OrderedFolder` non è supportata. Se desideri condividere una cartella, quando la crei in AEM Assets, non selezionare l’opzione Ordinato .

## Best practice {#best-practices}

Le best practice per sfruttare l’AEM per la condivisione delle cartelle Creative Cloud includono:

* **Considerazioni sul volume:** AEM/Creative Cloud condivisione cartelle per condividere un numero minore di file, ad esempio, relativi a una campagna o a un’attività specifica. Per condividere set di risorse più grandi, come tutte le risorse approvate nell’organizzazione, utilizza altri metodi di distribuzione (ad esempio, AEM Assets Brand Portal) o AEM’app desktop.
* **Evita la condivisione di gerarchie profonde:** la condivisione funziona in modo ricorsivo e non consente l&#39;annullamento selettivo della condivisione. In genere, per la condivisione è consigliabile considerare solo le cartelle prive di sottocartelle o con una gerarchia molto superficiale, ad esempio 1 livello di sottocartella.
* **Cartelle separate per la condivisione unidirezionale:** è necessario utilizzare cartelle separate per la condivisione delle risorse finali da AEM Assets a file di Creative Cloud e per la condivisione di risorse pronte per la creazione da file di Creative Cloud ad AEM Assets. Insieme a una buona convenzione di denominazione per queste cartelle, crea un ambiente di lavoro facile da capire per gli utenti di AEM Assets e Creative Cloud.
* **Evitare WIP nella cartella condivisa:** La cartella condivisa non deve essere utilizzata per Work in Progress. Utilizzare una cartella separata in Creative Cloud Files per eseguire un lavoro che richiede frequenti modifiche al file.
* **Avvia nuovo lavoro all&#39;esterno della cartella condivisa:** le nuove progettazioni (file creativi) devono essere avviate nella cartella WIP separata in File di Creative Cloud e, quando sono pronte per essere condivise con gli utenti di AEM Assets, devono essere spostate o salvate nella cartella condivisa.
* **Semplificare la struttura di condivisione:** per una configurazione operativa più gestibile, pensa a semplificare la struttura di condivisione. Invece di condividere con tutti gli utenti creativi, le cartelle AEM Assets devono essere condivise solo con i rappresentanti del team, come un direttore creativo o un responsabile del team. Il manager dal lato creativo riceverà le risorse finali, deciderà sulle assegnazioni di lavoro e quindi lascerà che i designer lavorino nei propri account di Creative Cloud sulle risorse WIP. È possibile utilizzare le funzioni di collaborazione Creative Cloud per coordinare il lavoro e infine selezionare e mettere le risorse pronte per la condivisione in AEM Assets nella cartella condivisa creativa.

Il diagramma seguente illustra un esempio di configurazione per la creazione di nuove progettazioni basate sulle risorse finali esistenti da AEM Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
