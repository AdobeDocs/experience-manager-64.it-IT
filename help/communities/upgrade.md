---
title: Aggiornamento a AEM 6.4 Communities
seo-title: Upgrading to AEM 6.4 Communities
description: Come effettuare l’aggiornamento da una versione precedente a AEM community 6.4
seo-description: How to upgrade from an earlier version to AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 1%

---

# Aggiornamento a AEM 6.4 Communities {#upgrading-to-aem-communities}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

A seconda della topologia e delle funzioni di ogni sito, possono essere necessarie le seguenti azioni durante l’aggiornamento ad AEM Communities 6.4 o l’installazione del pacchetto di funzioni più recente.

Questa sezione è specifica delle Comunità e integra le informazioni fornite in [Aggiornamento a AEM 6.4](../../help/sites-deploying/upgrade.md) (piattaforma).

## Aggiornamento da AEM 6.1 o versione successiva {#upgrading-from-aem-or-later}

### Solr reindicizzazione {#reindex-solr}

Quando installi un nuovo pacchetto di funzioni di Communities su una distribuzione configurata con MSRP, sarà necessario:

1. Installa il [pacchetto di funzionalità più recente](deploy-communities.md#latestfeaturepack)
2. Installa il [file di configurazione Solr più recenti](msrp.md#upgrading)
3. Reindicizza MSRP

   vedere la sezione [Strumento di reindicizzazione MSRP](msrp.md#msrp-reindex-tool)

### Abilitazione 2.0 {#enablement}

A partire da AEM 6.3, le funzioni di abilitazione non memorizzano più le informazioni di reporting in MySQL. La dipendenza MySQL è presente solo per il tracciamento del contenuto SCORM.

Contattare [assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html) per assistenza nella migrazione dei contenuti da Abilitazione 1.0.

## Aggiornamento da AEM 6.0 {#upgrading-from-aem}

Se è necessario mantenere UGC preesistente, i mezzi per farlo dipendono dal fatto che la distribuzione memorizzi UGC [on-premise](#on-premise-storage) o [Adobe cloud](#adobe-cloud-storage).

### Adobe Cloud Storage {#adobe-cloud-storage}

Se il sito aggiornato è stato configurato per l’utilizzo dell’archiviazione cloud di Adobe, potrebbe apparire (in modo errato) come se tutto l’UGC fosse stato perso, in quanto i metodi SRP non saranno in grado di individuare l’UGC preesistente nella vecchia posizione.

Quindi, c&#39;è la possibilità di istruire l&#39;ASRP per utilizzare `AEM 6.0 compatability-mode` per accedere a UGC.

Per tutte le istanze di authoring e pubblicazione AEM 6.3:

1. Accesso con privilegi di amministratore e configurazione [ASRP](asrp.md).
1. Segui questi passaggi per rendere visibile l’UGC esistente:

   i. Passa alla console Web. L’URL predefinito è
   `https://localhost:4502/system/console/configMgr`.

   ii) Individua **[!UICONTROL Utilità AEM Communities]** e seleziona per espandere il pannello di configurazione.

   iii) Deseleziona **[!UICONTROL Archiviazione cloud]** e fai clic su **[!UICONTROL Salva]**.

![chlimage_1-126](assets/chlimage_1-126.png)

### Storage on-premise {#on-premise-storage}

Se il sito aggiornato non ha utilizzato l’archiviazione cloud, qualsiasi UGC preesistente deve essere convertito in conformità alla nuova struttura introdotta in AEM 6.1 Communities a supporto dello store comune.

A questo scopo, su GitHub è disponibile uno strumento di migrazione open source:\
[Strumento di migrazione UGC di AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### API Java {#java-apis}

Quando esegui l’aggiornamento da AEM 6.0 social community a AEM 6.3 Communities, molte API sono state riorganizzate in pacchetti diversi. La maggior parte dovrebbe essere facilmente risolta quando si utilizza un IDE per la personalizzazione delle funzioni di Communities.

Per informazioni dettagliate sul pacchetto SocialUtils obsoleto, visita [Refactoring di SocialUtils](socialutils.md).

Vedi anche [Utilizzo di Maven per Communities](maven.md).

### Nessun modello di componente JSP {#no-jsp-component-templates}

La [quadro della componente sociale](scf.md) (SCF) utilizza [HandlebarsJS](https://handlebarsjs.com/) (HBS) linguaggio di template al posto di Java Server Pages (JSP) utilizzato prima di AEM 6.0.

Nella AEM 6.0, i componenti JSP sono rimasti accanto ai nuovi componenti del framework HBS nella stessa posizione, con i componenti HBS generalmente situati in sottocartelle denominate &quot;hbs&quot;.

A partire AEM 6.1, i componenti JSP sono stati rimossi completamente. Per Communities, si consiglia di sostituire tutti gli usi dei componenti JSP con i componenti SCF.

## Strumento di migrazione UGC di AEM Communities {#aem-communities-ugc-migration-tool}

La [Strumento di migrazione UGC di AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) è uno strumento di migrazione open source disponibile su GitHub, che può essere personalizzato per esportare contenuti generati dagli utenti generati dagli utenti da versioni precedenti di AEM social community e importarli in AEM Communities 6.1 o versioni successive.

Oltre a spostare UGC da versioni precedenti, è anche possibile utilizzare lo strumento per spostare UGC da uno [SRP](working-with-srp.md) a un altro, ad esempio da MSRP a DSRP.

## Aggiornamento da AEM 5.6.1 o versioni precedenti {#upgrading-from-aem-or-earlier}

Concettualmente, ci sono tre generazioni di componenti di comunità:

**Gen.**: circa da CQ 5.4 a AEM 5.6.0 - questi sono i **collare** componenti che hanno memorizzato UGC nell’archivio locale utilizzando la replica come mezzo per sincronizzare UGC tra piattaforme. Altre differenze riguardano l’implementazione tramite Java Server Pages (JSP) e la funzione blog che consiste nell’authoring solo nell’ambiente di authoring.

**Gen.**: da AEM 5.6.1 a AEM 6.1 - questo è un mix di **collare** e **sociale** componenti. AEM 6.0 introduce la nuova [quadro della componente sociale](scf.md) (SCF) e AEM 6.2 hanno introdotto un [archivio UGC comune](working-with-srp.md) in cui è possibile accedere a UGC utilizzando un [provider di risorse di archiviazione](srp.md) (SRP).

**Gen.**: dal AEM 6.2 in avanti, **sociale** componenti, implementati in SCF come componenti Handlebars (HBS) che richiedono una scelta di SRP per UGC.
