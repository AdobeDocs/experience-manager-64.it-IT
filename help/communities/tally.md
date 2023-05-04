---
title: Elementi di base di conteggio
seo-title: Tally Essentials
description: Panoramica della classe Tally
seo-description: Tally class overview
uuid: c369c6a1-9ced-4b5c-af43-8c03236eaa52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9941ba90-3d40-4c90-bca8-5db49603cbfa
exl-id: f04ec253-08b8-4ee2-9873-4a51549daeba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# Elementi di base di conteggio {#tally-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Tally è una classe astratta che fornisce un metodo standard per raccogliere feedback dai membri sul valore di prodotti e servizi specifici. Il feedback anonimo non è supportato. Il visitatore del sito deve registrarsi e accedere per partecipare e accedere per modificare il proprio feedback. L&#39;obbligo di accedere facilita la moderazione e migliora il valore del feedback impedendo l&#39;accesso a più post.

È possibile creare un componente tally personalizzato estendendo la classe tally astratta.

[Mi piace](essentials-liking.md) è un&#39;attuazione di un alleato che è una forma semplice di esprimere un parere positivo.

[Votazione](essentials-voting.md) è un&#39;attuazione di un alleato che è una forma semplice di esprimere un parere positivo o negativo.

[Valutazione](rating-basics.md) è un&#39;implementazione di tally che utilizza un sistema a stella per esprimere una serie di opinioni da positive a negative.

A partire dal AEM 6.1, il *sondaggio* Il componente non è più disponibile.

[Recensioni](reviews-basics.md) è un componente SCF che è un ibrido di [commenti](essentials-comments.md) e [valutazione](rating-basics.md).

## Funzionalità di base per lato client {#essentials-for-client-side}

* [Personalizzazioni lato client](client-customize.md)

## Funzioni di base per lato server {#essentials-for-server-side}

* [API Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Endpoint tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personalizzazioni lato server](server-customize.md)

### Accesso alle tabelle pubblicate (UGC) {#accessing-posted-tallies-ugc}

UGC dovrebbe essere moderato utilizzando uno dei metodi standard per la moderazione.\
Vedi [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

A partire da AEM 6.1 Comunità, l&#39;uso di un [negozio comune](working-with-srp.md) per UGC include l&#39;accesso programmatico a UGC indipendentemente dall&#39;opzione di archiviazione scelta (come ASRP, MSRP o JSRP).

**La posizione e il formato dell’UGC nell’archivio sono soggetti a modifiche senza preavviso**.

Consulta:

* [Panoramica del provider di risorse di storage](srp.md) - introduzione e utilizzo dell&#39;archivio
* [Essenze SRP e UGC](srp-and-ugc.md) - Metodi e esempi di utilità SRP
* [Accesso a UGC con SRP](accessing-ugc-with-srp.md) - linee guida per la codifica
* [Refactoring di SocialUtils](socialutils.md) - mappatura di metodi di utilità obsoleti ai metodi di utilità SRP correnti
