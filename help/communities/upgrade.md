---
title: Aggiornamento ad AEM 6.4 Communities
seo-title: Aggiornamento ad AEM 6.4 Communities
description: Come effettuare l’aggiornamento da una versione precedente a AEM 6.4 Communities
seo-description: Come effettuare l’aggiornamento da una versione precedente a AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c

---


# Aggiornamento ad AEM 6.4 Communities {#upgrading-to-aem-communities}

A seconda della topologia e delle funzioni di ciascun sito, potrebbero essere necessarie le seguenti azioni quando si esegue l&#39;aggiornamento ad AEM Communities 6.4 o si installa l&#39;ultimo pacchetto di funzioni.

Questa sezione è specifica per Communities e integra le informazioni fornite in [Aggiornamento ad AEM 6.4](../../help/sites-deploying/upgrade.md) (piattaforma).

## Aggiornamento da AEM 6.1 o versione successiva {#upgrading-from-aem-or-later}

### Reindicizza Solr {#reindex-solr}

Durante l&#39;installazione di un nuovo pacchetto di funzionalità Community su una distribuzione configurata con MSRP, sarà necessario:

1. Installare il pacchetto [più recente](deploy-communities.md#latestfeaturepack)
2. Installare i file di configurazione Solr [più recenti](msrp.md#upgrading)
3. Reindicizza MSRP

   vedere la sezione Strumento [MSRP Reindex](msrp.md#msrp-reindex-tool)

### Enablement 2.0 {#enablement}

A partire da AEM 6.3, le funzioni di abilitazione non memorizzano più le informazioni di reporting in MySQL. La dipendenza MySQL è presente solo per il tracciamento del contenuto SCORM.

Per assistenza nella migrazione dei contenuti da Enablement 1.0, contattate l&#39; [assistenza](https://helpx.adobe.com/marketing-cloud/contact-support.html) clienti.

## Aggiornamento da AEM 6.0 {#upgrading-from-aem}

Se è necessario mantenere un UGC preesistente, i mezzi per farlo dipendono dal fatto che la distribuzione memorizzi UGC [locale](#on-premise-storage) o in [Adobe Cloud](#adobe-cloud-storage).

### Archiviazione Adobe Cloud {#adobe-cloud-storage}

Se il sito aggiornato è stato configurato per l’utilizzo dell’archiviazione cloud Adobe, potrebbe apparire (in modo non corretto) come se tutti gli UGC fossero andati perduti in quanto i metodi SRP non sarebbero in grado di individuare gli UGC preesistenti nella vecchia posizione.

Pertanto, esiste la capacità di istruire l&#39;ASRP a utilizzare `AEM 6.0 compatability-mode` per accedere a UGC.

Per tutte le istanze di creazione e pubblicazione di AEM 6.3

1. Accesso con privilegi di amministratore
2. Configurare [ASRP](asrp.md)
3. Per rendere visibile l’UGC preesistente, effettuate le seguenti operazioni:
i. Passare alla console Web, ad esempio
   [https://&lt;host>:&lt;porta>/system/console/configMgr](http://localhost:4502/system/console/configMgr)ii. Individua la configurazione **[!UICONTROL AEM Communities Utilities]** iii. Selezionare per espandere il pannello di configurazione
   * *Deseleziona***`Cloud Storage`**
   * Seleziona **[!UICONTROL Salva]**

![chlimage_1-126](assets/chlimage_1-126.png)

### Storage locale {#on-premise-storage}

Se il sito aggiornato non utilizza l’archiviazione cloud, qualsiasi UGC preesistente deve essere convertito in conformità alla nuova struttura introdotta in AEM 6.1 Communities a supporto dello store comune.

A questo scopo, su GitHub è disponibile uno strumento di migrazione open source:\
[Strumento di migrazione UGC di AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### API Java {#java-apis}

Quando eseguite l&#39;aggiornamento dalle community social di AEM 6.0 alle community AEM 6.3, tenete presente che molte API sono state riorganizzate in pacchetti diversi. La maggior parte dovrebbe essere facilmente risolta quando si utilizza un IDE per la personalizzazione delle funzionalità di Communities.

Per informazioni dettagliate sul pacchetto SocialUtils obsoleto, visitate [SocialUtils Refactoring](socialutils.md).

Vedere anche [Utilizzo di Paradiso per Community](maven.md).

### Nessun modello di componente JSP {#no-jsp-component-templates}

Il framework [di componenti](scf.md) social network (SCF) utilizza il linguaggio di modellazione [HandlebarsJS](https://www.handlebarsjs.com/) (HBS) al posto di JSP (Java Server Pages) utilizzato prima di AEM 6.0.

In AEM 6.0, i componenti JSP sono rimasti accanto ai nuovi componenti del framework HBS nella stessa posizione, mentre i componenti HBS si trovano generalmente in sottocartelle denominate &quot;hbs&quot;.

A partire da AEM 6.1, i componenti JSP sono stati rimossi completamente. Per Communities, si consiglia di sostituire tutti gli usi dei componenti JSP con i componenti SCF.

## Strumento di migrazione UGC di AEM Communities {#aem-communities-ugc-migration-tool}

Lo strumento [di migrazione UGC di](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) AEM Communities è uno strumento di migrazione open source, disponibile su GitHub, che può essere personalizzato per esportare UGC da versioni precedenti delle social community AEM e importarli in AEM Communities 6.1 o versioni successive.

Oltre a spostare UGC dalle versioni precedenti, è anche possibile utilizzare lo strumento per spostare UGC da un [SRP](working-with-srp.md) all&#39;altro, ad esempio da MSRP a DSRP.

## Aggiornamento da AEM 5.6.1 o versioni precedenti {#upgrading-from-aem-or-earlier}

Concettualmente, esistono tre generazioni di componenti per comunità:

**Gen 1**: circa CQ 5.4 fino a AEM 5.6.0: si tratta dei componenti **collab** che hanno memorizzato UGC nell&#39;archivio locale utilizzando la replica come mezzo per sincronizzare UGC tra piattaforme. Altre differenze riguardano l’implementazione tramite Java Server Pages (JSP), nonché la funzione blog che consiste nell’authoring solo nell’ambiente di authoring.

**Gen 2**: da AEM 5.6.1 a AEM 6.1 - si tratta di una combinazione di componenti **collab** e **social** . AEM 6.0 ha introdotto il nuovo framework [di componenti](scf.md) sociali (SCF) e AEM 6.2 ha introdotto un archivio [UGC](working-with-srp.md) comune a cui è possibile accedere tramite un provider [di risorse di](srp.md) storage (SRP).

**Gen 3**: da AEM 6.2 in avanti, esistono solo componenti **social** , implementati in SCF come Handlebars (HBS) e che richiedono una scelta di SRP per UGC.
