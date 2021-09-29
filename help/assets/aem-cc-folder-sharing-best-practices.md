---
title: Condivisione delle cartelle di Experience Manager Assets con Creative Cloud
description: Configurazione e best practice per consentire agli utenti di Adobe Experience Manager Assets di scambiare cartelle di risorse con gli utenti di Adobe Creative Cloud.
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%

---

# [!DNL Experience Manager] alle best practice per la condivisione delle  [!DNL Creative Cloud] cartelle {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>L’Experience Manager alla funzione Creative Cloud condivisione cartelle è obsoleto. Adobe consiglia vivamente di utilizzare funzionalità più recenti come [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) o [app desktop Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Ulteriori informazioni sono disponibili in [Best practice per l&#39;integrazione di Experienci Manager e Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager può essere configurato per consentire agli utenti di Experience Manager Assets di condividere cartelle con gli utenti di Creative Cloud, in modo che siano disponibili come cartelle condivise nel servizio Creative Cloud Assets. La funzione può essere utilizzata per scambiare file tra i team creativi e gli utenti di Experience Manager Assets, specialmente quando gli utenti creativi non hanno accesso all’istanza di Experience Manager Assets (non sono sulla rete aziendale).

Questo tipo di integrazione può essere utilizzato in entrambi i casi d’uso, soprattutto quando si lavora con utenti che non hanno accesso diretto ad Experience Manager Assets:

* Condivisione di un set di risorse specifiche da Experience Manager Assets con gli utenti di Creative Cloud Files (ad esempio, una descrizione creativa e un set di risorse approvate per la progettazione di una nuova attività di marketing)
* Ricezione di nuovi file da parte degli utenti di Creative Cloud.

>[!NOTE]
>
>Prima di leggere questo documento, puoi consultare le [best practice generali sull’integrazione di Experienci Manager e Creative Cloud](aem-cc-integration-best-practices.md) per una panoramica di livello superiore dell’argomento.

## Panoramica {#overview}

Experience Manager per Creative Cloud la condivisione delle cartelle si basa sulla condivisione lato server di cartelle e file tra risorse di Experience Manager e account di Creative Cloud. I creativi professionisti, che utilizzano l&#39;applicazione desktop Creative Cloud sul desktop, possono inoltre rendere le cartelle condivise disponibili direttamente sui loro dischi utilizzando la tecnologia Adobe CreativeSync.

Il diagramma seguente fornisce una panoramica dell’integrazione.

![chlimage_1-406](assets/chlimage_1-406.png)

L’integrazione include i seguenti elementi:

* **[!DNL Assets]** server distribuiti nella rete aziendale (servizi gestiti o on-premise): La condivisione delle cartelle viene avviata qui.
* **Servizio** principale di Adobe Marketing Cloud Assets: funge da intermediario tra i servizi di storage Experience Manager e Creative Cloud. L’amministratore dell’azienda che utilizza l’integrazione deve stabilire una relazione di trust tra l’organizzazione del Marketing Cloud e l’istanza Risorse di Experience Manager. Inoltre [definiscono un elenco di collaboratori di Creative Cloud approvati](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets), che gli utenti di Assets possono condividere anche le cartelle per ulteriore sicurezza.
* **Creative Cloud servizi Web Assets**  (interfaccia web di archiviazione e Creative Cloud file): In questo caso, gli utenti di Creative Cloud specifici con cui è stata condivisa una cartella Risorse possono accettare l’invito e visualizzare la cartella nell’archivio dell’account di Creative Cloud.
* **Creative Cloud applicazione** desktop: (Facoltativo) Consente l’accesso diretto a cartelle/file condivisi dal desktop dell’utente creativo tramite sincronizzazione con l’archiviazione Creative Cloud Assets.

## Caratteristiche e limitazioni {#characteristics-and-limitations}

* **Propagazione unidirezionale delle modifiche:** le modifiche ai file vengono propagate in una sola direzione, dal sistema (Experience Manager o Creative Cloud risorse), in cui la risorsa è stata originariamente creata (caricata). L’integrazione non fornisce una sincronizzazione bidirezionale completamente automatizzata tra i due sistemi.

* **Controllo delle versioni:**

   * Experience Manager crea versioni di una risorsa solo in caso di aggiornamenti, se il file è stato creato in Experience Manager e viene aggiornato in tale ambiente.
   * Creative Cloud Assets fornisce la propria [funzionalità di controllo delle versioni](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) destinata agli aggiornamenti di Work In Progress (in sostanza, memorizza gli aggiornamenti per un massimo di 10 giorni)

* **Limitazioni dello spazio:** Le dimensioni e i volumi dei file scambiati sono limitati dalla  [Creative Cloud specifica delle risorse ](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) per gli utenti creativi (dipende dal livello di abbonamento) e da una limitazione delle dimensioni massime dei file pari a 5 GB. Lo spazio è inoltre limitato dalla quota di risorse di cui dispone l’organizzazione nel servizio di base Adobe Marketing Cloud Assets.

* **Requisiti di spazio:** anche i file nelle cartelle condivise devono essere fisicamente memorizzati in Experience Manager e quindi nell’account Creative Cloud, con una copia nella cache nel servizio core Assets di Marketing Cloud.
* **Rete e larghezza di banda:** i file in cartelle condivise e tutti gli aggiornamenti devono essere trasportati attraverso la rete tra i sistemi. Assicurati che siano condivisi solo i file e gli aggiornamenti pertinenti.
* **Tipo** cartella: La condivisione di una cartella di risorse di tipo  `sling:OrderedFolder` non è supportata. Se desideri condividere una cartella, quando la crei in Experience Manager Assets, non selezionare l’opzione Ordinato .

## Best practice {#best-practices}

Le best practice per sfruttare l’Experience Manager per Creative Cloud della condivisione delle cartelle includono:

* **Considerazioni sul volume:** ad Experience Manager, la condivisione delle cartelle di Creative Cloud deve essere utilizzata per condividere un numero inferiore di file, ad esempio, relativi a una campagna o a un&#39;attività specifica. Per condividere set di risorse più grandi, come tutte le risorse approvate nell’organizzazione, utilizza altri metodi di distribuzione (ad Experience Manager Assets Brand Portal) o l’app desktop Experience Manager.
* **Evita la condivisione di gerarchie profonde:** la condivisione funziona in modo ricorsivo e non consente l&#39;annullamento selettivo della condivisione. In genere, per la condivisione è consigliabile considerare solo le cartelle prive di sottocartelle o con una gerarchia molto superficiale, ad esempio 1 livello di sottocartella.
* **Cartelle separate per la condivisione unidirezionale:** è necessario utilizzare cartelle separate per la condivisione delle risorse finali da Experience Manager Assets a file di Creative Cloud e per la condivisione di risorse creative pronte dai file di Creative Cloud a  [!DNL Assets]. Insieme a una buona convenzione di denominazione per queste cartelle, crea un ambiente di lavoro facile da comprendere per gli utenti di Experience Manager Assets e Creative Cloud.
* **Evitare WIP nella cartella condivisa:** La cartella condivisa non deve essere utilizzata per Work in Progress. Utilizzare una cartella separata in Creative Cloud Files per eseguire un lavoro che richiede frequenti modifiche al file.
* **Avvia nuovo lavoro all’esterno della cartella condivisa:** le nuove progettazioni (file creativi) devono essere avviate nella cartella WIP separata in File di Creative Cloud e, quando sono pronte per essere condivise con gli utenti di Experience Manager Assets, devono essere spostate o salvate nella cartella condivisa.
* **Semplificare la struttura di condivisione:** per una configurazione operativa più gestibile, pensa a semplificare la struttura di condivisione. Invece di condividere con tutti gli utenti creativi, le cartelle Risorse di Experience Manager devono essere condivise solo con i rappresentanti del team, come un direttore creativo o un responsabile del team. Il manager dal lato creativo riceverà le risorse finali, deciderà sulle assegnazioni di lavoro e quindi lascerà che i designer lavorino nei propri account di Creative Cloud sulle risorse WIP. Possono utilizzare funzioni di collaborazione Creative Cloud per coordinare il lavoro e infine selezionare e mettere le risorse pronte per la condivisione in Experience Manager Assets nella cartella condivisa creativa.

Il diagramma seguente illustra una configurazione di esempio per la creazione di nuove progettazioni basate sulle risorse finali esistenti da Experience Manager Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
