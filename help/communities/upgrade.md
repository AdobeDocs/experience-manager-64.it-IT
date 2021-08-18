---
title: Aggiornamento ad AEM 6.4 Communities
seo-title: Aggiornamento ad AEM 6.4 Communities
description: Come effettuare l’aggiornamento da una versione precedente a AEM community 6.4
seo-description: Come effettuare l’aggiornamento da una versione precedente a AEM community 6.4
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 2%

---

# Aggiornamento ad AEM 6.4 Communities {#upgrading-to-aem-communities}

A seconda della topologia e delle funzioni di ogni sito, possono essere necessarie le seguenti azioni durante l’aggiornamento ad AEM Communities 6.4 o l’installazione del pacchetto di funzioni più recente.

Questa sezione è specifica delle Community e integra le informazioni fornite in [Aggiornamento a AEM 6.4](../../help/sites-deploying/upgrade.md) (piattaforma).

## Aggiornamento da AEM 6.1 o versione successiva {#upgrading-from-aem-or-later}

### Solr reindicizzazione {#reindex-solr}

Quando installi un nuovo pacchetto di funzioni di Communities su una distribuzione configurata con MSRP, sarà necessario:

1. Installa il [pacchetto di funzioni più recente](deploy-communities.md#latestfeaturepack)
2. Installa i [file di configurazione Solr più recenti](msrp.md#upgrading)
3. Reindicizza MSRP

   vedere la sezione [Strumento di reindicizzazione MSRP](msrp.md#msrp-reindex-tool)

### Abilitazione 2.0 {#enablement}

A partire da AEM 6.3, le funzioni di abilitazione non memorizzano più le informazioni di reporting in MySQL. La dipendenza MySQL è presente solo per il tracciamento del contenuto SCORM.

Contatta l’ [assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html) per assistenza nella migrazione dei contenuti da Enablement 1.0.

## Aggiornamento da AEM 6.0 {#upgrading-from-aem}

Se è necessario mantenere un UGC preesistente, i mezzi per farlo dipendono dal fatto che la distribuzione abbia memorizzato UGC [on-premise](#on-premise-storage) o in [Adobe cloud](#adobe-cloud-storage).

### Adobe Cloud Storage {#adobe-cloud-storage}

Se il sito aggiornato è stato configurato per l’utilizzo dell’archiviazione cloud di Adobe, potrebbe apparire (in modo errato) come se tutto l’UGC fosse stato perso, in quanto i metodi SRP non saranno in grado di individuare l’UGC preesistente nella vecchia posizione.

Pertanto, esiste la possibilità di istruire l’ASRP affinché utilizzi `AEM 6.0 compatability-mode` per accedere all’UGC.

Per tutte le istanze di authoring e pubblicazione AEM 6.3

1. Accesso con privilegi di amministratore
2. Configura [ASRP](asrp.md)
3. Segui questi passaggi per rendere visibile un UGC preesistente:
i. Passa alla console Web, ad esempio
   [https://&lt;host>:&lt;port>/system/console/](http://localhost:4502/system/console/configMgr)
configMgrii. Individua la configurazione **[!UICONTROL Utilità AEM Communities]**
iii) Seleziona per espandere il pannello di configurazione
   * *Deseleziona* **`Cloud Storage`**
   * Seleziona **[!UICONTROL Salva]**

![chlimage_1-126](assets/chlimage_1-126.png)

### Storage on-premise {#on-premise-storage}

Se il sito aggiornato non ha utilizzato l’archiviazione cloud, qualsiasi UGC preesistente deve essere convertito in conformità alla nuova struttura introdotta in AEM 6.1 Communities a supporto dello store comune.

A questo scopo, su GitHub è disponibile uno strumento di migrazione open source:\
[Strumento di migrazione UGC di AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### API Java {#java-apis}

Quando esegui l’aggiornamento da AEM 6.0 social community a AEM 6.3 Communities, molte API sono state riorganizzate in pacchetti diversi. La maggior parte dovrebbe essere facilmente risolta quando si utilizza un IDE per la personalizzazione delle funzioni di Communities.

Per informazioni dettagliate sul pacchetto SocialUtils dichiarato obsoleto, visita [Refactoring SocialUtils](socialutils.md).

Vedi anche [Utilizzo di Maven per Communities](maven.md).

### Nessun modello di componente JSP {#no-jsp-component-templates}

Il [framework dei componenti social](scf.md) (SCF) utilizza il linguaggio di template `HandlebarsJS` (HBS) al posto delle pagine Java Server (JSP) utilizzate prima di AEM 6.0.

Nella AEM 6.0, i componenti JSP sono rimasti accanto ai nuovi componenti del framework HBS nella stessa posizione, con i componenti HBS generalmente situati in sottocartelle denominate &quot;hbs&quot;.

A partire AEM 6.1, i componenti JSP sono stati rimossi completamente. Per Communities, si consiglia di sostituire tutti gli usi dei componenti JSP con i componenti SCF.

## Strumento di migrazione UGC di AEM Communities {#aem-communities-ugc-migration-tool}

Lo [strumento di migrazione UGC di AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) è uno strumento di migrazione open source disponibile su GitHub, che può essere personalizzato per l’esportazione di contenuti generati dagli utenti generati dagli utenti generati da versioni precedenti di AEM social community e può essere importato in AEM Communities 6.1 o versioni successive.

Oltre a spostare UGC da versioni precedenti, è anche possibile utilizzare lo strumento per spostare UGC da un [SRP](working-with-srp.md) a un altro, ad esempio da MSRP a DSRP.

## Aggiornamento da AEM 5.6.1 o versioni precedenti {#upgrading-from-aem-or-earlier}

Concettualmente, ci sono tre generazioni di componenti di comunità:

**Gen 1**: all&#39;incirca CQ 5.4 fino a AEM 5.6.0 - questi sono i  **** collabcomponents che hanno memorizzato UGC nell&#39;archivio locale utilizzando la replica come mezzo per sincronizzare UGC tra piattaforme. Altre differenze riguardano l’implementazione tramite Java Server Pages (JSP) e la funzione blog che consiste nell’authoring solo nell’ambiente di authoring.

**Gen 2**: da AEM 5.6.1 a AEM 6.1 - questo è un mix di  **** collaband  **** socialcomponents. AEM 6.0 ha introdotto il nuovo [social component framework](scf.md) (SCF) e AEM 6.2 ha introdotto un [archivio UGC comune](working-with-srp.md) in cui l&#39;accesso UGC è effettuato tramite un [provider di risorse di storage](srp.md) (SRP).

**Gen 3**: dal AEM 6.2 in avanti, esistono solo componenti  **** sociali, implementati in SCF come componenti Handlebars (HBS) che richiedono una scelta di SRP per UGC.
