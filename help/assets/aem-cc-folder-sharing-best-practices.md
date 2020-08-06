---
title: Condivisione  cartelle AEM Assets con Creative Cloud
description: Configurazione e procedure ottimali per consentire agli utenti di Adobe Experience Manager Assets di scambiare cartelle di risorse con gli utenti Adobe Creative Cloud.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 0%

---


# AEM alle procedure ottimali per la condivisione delle cartelle {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>La funzione di AEM alla condivisione delle cartelle è obsoleta.  Adobe consiglia vivamente di utilizzare funzionalità più recenti, come [collegamento](https://helpx.adobe.com/it/enterprise/using/adobe-asset-link.html) risorse Adobe o l&#39;app [desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)AEM. Scopri di più nelle procedure ottimali per l&#39;integrazione [AEM e Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager (AEM) può essere configurato per consentire agli utenti  AEM Assets di condividere cartelle con gli utenti di Creative Cloud, in modo che siano disponibili come cartelle condivise nel servizio Creative Cloud risorse. La funzione può essere utilizzata per scambiare file tra team creativi e utenti  AEM Assets, soprattutto quando gli utenti creativi non hanno accesso all’istanza  AEM Assets (non sono sulla rete aziendale).

Questo tipo di integrazione può essere utilizzato in entrambi i casi di utilizzo, soprattutto quando si lavora con utenti che non hanno accesso diretto a  AEM Assets:

* Condivisione di una serie di risorse specifiche da  AEM Assets con gli utenti di Creative Cloud Files (ad esempio, una serie di risorse creative e approvate per il lavoro di progettazione di una nuova attività di marketing)
* Ricezione di nuovi file da parte degli utenti di Creative Cloud.

>[!NOTE]
>
>Prima di leggere questo documento, potete esaminare le best practice [generali per l&#39;integrazione di](aem-cc-integration-best-practices.md) AEM e Creative Cloud per una panoramica di livello superiore dell&#39;argomento.

## Panoramica {#overview}

AEM per Creative Cloud la condivisione delle cartelle si basa sulla condivisione lato server di cartelle e file tra  account AEM Assets e di Creative Cloud. I creativi professionisti, che utilizzano l&#39;applicazione desktop Creative Cloud sul proprio desktop, possono inoltre rendere le cartelle condivise disponibili direttamente sui propri dischi utilizzando  tecnologia Adobe CreativeSync.

Il diagramma seguente fornisce una panoramica dell&#39;integrazione.

![chlimage_1-406](assets/chlimage_1-406.png)

L&#39;integrazione include i seguenti elementi:

* **server** AEM Assets implementato nella rete aziendale (servizi gestiti o locali): La condivisione delle cartelle viene avviata qui.
* **Servizio** di base di Adobe Marketing Cloud Assets: funge da intermediario tra i servizi di storage AEM e Creative Cloud. L&#39;amministratore della società che utilizza l&#39;integrazione deve stabilire una relazione di trust tra l&#39;organizzazione del Marketing Cloud e l&#39;istanza AEM Assets . Inoltre, [definiscono un elenco di collaboratori](https://docs.adobe.com/content/help/en/core-services/interface/assets/t-admin-add-cc-user.html)di Creative Cloud approvati, che  utenti AEM Assets possono condividere anche le cartelle per ulteriore protezione.
* **Creative Cloud servizi** Web Risorse (interfaccia utente Web per l’archiviazione e la Creative Cloud di file): Questo è il punto in cui gli utenti di Creative Cloud specifici, con cui è stata condivisa una cartella AEM Assets , potrebbero accettare l’invito e visualizzare la cartella nell’archivio dell’account Creative Cloud.
* **Creative Cloud applicazione** desktop: (Facoltativo) Consente l&#39;accesso diretto alla cartella o ai file condivisi dal desktop dell&#39;utente creativo tramite sincronizzazione con l&#39;archiviazione Creative Cloud risorse.

## Caratteristiche e limitazioni {#characteristics-and-limitations}

* **Propagazione unidirezionale delle modifiche:** Le modifiche ai file vengono propagate in una sola direzione, dal sistema (AEM o Creative Cloud risorse), dove la risorsa è stata creata originariamente (caricata). L&#39;integrazione non fornisce una sincronizzazione bidirezionale completamente automatizzata tra i due sistemi.

* **Gestione versioni:**

   * AEM solo le versioni di una risorsa sugli aggiornamenti se il file è stato creato in AEM e vi è stato aggiornato.
   * Creative Cloud risorse offre una funzione [di](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) controllo delle versioni specifica per gli aggiornamenti di Work in Progress (praticamente, memorizza gli aggiornamenti fino a 10 giorni)

* **Limiti di spazio:** Le dimensioni e i volumi dei file scambiati sono limitati dalla quota [di risorse per le](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) Creative Cloud specifiche per gli utenti creativi (dipende dal livello di iscrizione) e da un limite di 5 GB per la dimensione massima dei file. Lo spazio è inoltre limitato dalla quota di risorse di cui dispone l’organizzazione nel servizio di base di Adobe Marketing Cloud Assets.

* **Requisiti di spazio:** Anche i file nelle cartelle condivise devono essere memorizzati fisicamente in AEM e quindi nell’account di Creative Cloud, con una copia memorizzata nella cache nel Marketing Cloud servizio di base Risorse di .
* **Rete e larghezza di banda:** I file in cartelle condivise e tutti gli aggiornamenti devono essere trasportati attraverso la rete tra i sistemi. Devi accertarti che siano condivisi solo i file e gli aggiornamenti rilevanti.
* **Tipo** cartella: La condivisione di una cartella di risorse di tipo `sling:OrderedFolder`non è supportata. Se desiderate condividere una cartella, quando la create in  AEM Assets, non selezionate l’opzione Ordinato.

## Best practices {#best-practices}

Le best practice per sfruttare la AEM per la condivisione delle cartelle includono:

* **Considerazioni sul volume:** AEM/Creative Cloud condivisione cartelle deve essere utilizzata per condividere un numero minore di file, ad esempio relativi a una campagna o un&#39;attività specifica. Per condividere set di risorse più grandi, come tutte le risorse approvate nell’organizzazione, usate altri metodi di distribuzione (ad esempio,  AEM Assets Brand Portal) o AEM app desktop.
* **Evitate la condivisione di gerarchie profonde:** La condivisione funziona in modo ricorsivo e non consente la condivisione selettiva. In genere, per la condivisione devono essere prese in considerazione solo le cartelle prive di sottocartelle o con una gerarchia molto bassa, come 1 livello di sottocartella.
* **Cartelle separate per la condivisione unidirezionale:** Le cartelle separate devono essere utilizzate per condividere le risorse finali da  AEM Assets ai file di Creative Cloud e per condividere le risorse pronte per la creazione da Creative Cloud file a  AEM Assets. Insieme a una buona convenzione di denominazione per queste cartelle, crea un ambiente di lavoro facile da capire per  utenti AEM Assets e Creative Cloud.
* **Evitare WIP nella cartella condivisa:** La cartella condivisa non deve essere utilizzata per Work in Progress. Per eseguire il lavoro che richiede frequenti modifiche al file, usate una cartella separata in Creative Cloud Files.
* **Avvia nuovo lavoro all&#39;esterno della cartella condivisa:** Le nuove progettazioni (file creativi) devono essere avviate nella cartella WIP separata in File Creative Cloud e, quando sono pronte per essere condivise con  utenti AEM Assets, devono essere spostate o salvate nella cartella condivisa.
* **Semplificazione della struttura di condivisione:** Per una configurazione operativa più gestibile, pensate a semplificare la struttura di condivisione. Invece di condividere con tutti gli utenti creativi,  cartelle AEM Assets devono essere condivise solo con i rappresentanti del team, come un direttore creativo o un responsabile del team. Dal lato creativo, il manager riceve le risorse finali, decide sulle assegnazioni di lavoro e quindi lascia che i progettisti lavorino nei propri conti di Creative Cloud sulle risorse WIP. Possono usare le funzioni di collaborazione Creative Cloud per coordinare il lavoro, e infine selezionare e inserire le risorse che possono essere condivise  AEM Assets nella cartella condivisa pronta per la creazione.

Nel diagramma seguente è illustrata una configurazione di esempio per la creazione di nuove progettazioni basate sulle risorse finali esistenti di  AEM Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
