---
title: Script di analisi delle richieste
seo-title: Request Analysis Script
description: Lo script di analisi della richiesta viene eseguito per facilitare l'analisi dei file access.log producendo un report leggibile per l'elaborazione successiva
seo-description: The request analysis script is made to ease the analysis of the access.log files producing a readable report for later processing
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: 8582bbca-c11a-4880-88ba-da22e0301dba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---

# Script di analisi delle richieste{#request-analysis-script}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Scarica {#download}

Questo script è fatto per facilitare l&#39;analisi del `access.log` file che producono un rapporto leggibile per un&#39;elaborazione successiva.

[Ottieni file](assets/analyse-access.sh)

## Descrizione {#description}

Questo script è fatto per facilitare l&#39;analisi del `access.log` file che producono un rapporto leggibile per un&#39;elaborazione successiva.

Produce il numero complessivo di richieste, GET vs POST, Distribuzione delle richieste nel tempo e molto altro.

L’output è in sintassi Markdown e sarà quindi più facile convertirlo in PDF con strumenti come pandoc o mostrarlo in un browser con plug-in come visualizzatore Markdown.

Consente di analizzare un percorso personalizzato fornito sulla riga di comando.

Prendendo dal commento all&#39;interno del file che ti dice come eseguirlo:

Analizza CQ `access.log` estrapolazione di varie informazioni e produzione di un output Markdown su `stdout`.

## Utilizzo {#usage}

`./analyse-access.sh access.log.2013-&ast;`

puoi fornire percorsi personalizzati aggiuntivi da analizzare sulla riga di comando

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

è possibile salvare l&#39;output con una semplice tubazione

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
