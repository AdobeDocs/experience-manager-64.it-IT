---
title: Ristrutturazione dell’archivio in AEM 6.4
seo-title: Repository Restructuring in AEM 6.4
description: Scopri le nozioni di base e le motivazioni alla base della ristrutturazione dell’archivio in AEM 6.4
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 6ff5a23a-c9b5-49ca-87b2-ba01eaf48a9f
source-git-commit: cda63b9ece88d8172fa4d9817e315c9cff88c224
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Ristrutturazione dell’archivio in AEM 6.4{#repository-restructuring-in-aem}

## Introduzione {#introduction}

Prima di AEM 6.4, il codice cliente veniva distribuito in aree imprevedibili del JCR soggette a modifiche agli aggiornamenti. Per questo motivo, nelle versioni formali AEM veniva spesso sovrascritto il codice personalizzato, la configurazione o il contenuto. Inoltre, le modifiche dei clienti talvolta hanno sovrascritto AEM codice prodotto o contenuto, interrompendo le funzionalità del prodotto.

delineando chiaramente le gerarchie per AEM codice prodotto e codice cliente, questi conflitti possono essere evitati.

A tal fine, a partire dal AEM 6.4 e per essere proseguito nelle versioni future, il contenuto viene ristrutturato da /etc ad altre cartelle nell’archivio, insieme alle linee guida su quale contenuto va dove, in conformità alle seguenti regole di alto livello:

* AEM codice prodotto verrà sempre inserito in /libs, che non deve essere sovrascritto dal codice personalizzato
* Il codice personalizzato deve essere posizionato in /apps, /content e /conf

## Impatto sugli aggiornamenti 6.4 {#impact-on-upgrades}

Quando si esegue l’aggiornamento a AEM 6.4, un grande sottoinsieme di contenuto in /etc verrà duplicato in altre cartelle nell’archivio. Queste nuove posizioni sono le posizioni preferite in cui viene fatto riferimento al contenuto. Tuttavia, è stato fatto ogni tentativo per rendere l’aggiornamento AEM 6.4 compatibile con le posizioni precedenti nella cartella /etc e quindi nella maggior parte dei casi le posizioni precedenti continueranno a essere referenziate dal codice fino a quando le modifiche vengono apportate attivamente, e in molti casi manualmente, nell’applicazione di un cliente. Dal punto di vista della timeline, esistono due categorie di modifiche:

* Con l&#39;aggiornamento 6.4 - una manciata delle modifiche alla ristrutturazione /etc non sono compatibili con le versioni precedenti e pertanto le modifiche dovrebbero essere pianificate e implementate come parte dell&#39;aggiornamento AEM 6.4.
* Prima dell’aggiornamento alla versione 6.5 - la stragrande maggioranza delle modifiche alla ristrutturazione /etc può essere posticipata fino a qualche tempo nel futuro post-aggiornamento. Come accennato in precedenza, AEM codice 6.4 continuerà a fare riferimento alle posizioni precedenti fino a quando le modifiche non saranno implementate come parte di un rilascio da parte del cliente. Sebbene non vi sia una tempistica forzata per la quale le modifiche devono essere apportate, si consiglia di effettuarle prima dell’aggiornamento 6.5, in quanto le funzioni future potrebbero dipendere dalle nuove posizioni a cui si fa riferimento. Inoltre, la documentazione di una data funzione farà riferimento per convenzione alle nuove posizioni e potrebbe quindi confondere se le vecchie posizioni sono ancora in uso.

### Orientamento alla ristrutturazione {#restructuring-guidance}

Durante la pianificazione di un aggiornamento al AEM 6.4, per valutare lo sforzo di lavoro è necessario fare riferimento alle seguenti pagine per soluzione:

* [Ristrutturazione dell’archivio comune a tutte le soluzioni AEM](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [Ristrutturazione dell’archivio AEM Sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [Ristrutturazione dell’archivio AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html)
* [Ristrutturazione dell’archivio AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [Ristrutturazione dell’archivio AEM Forms](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [Ristrutturazione dell’archivio AEM Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [Ristrutturazione dell’archivio Commerce di AEM](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

Ogni pagina contiene due sezioni corrispondenti all’urgenza delle modifiche necessarie. Qualsiasi cosa nella sezione &quot;Con aggiornamento 6.4&quot; deve essere trattata come parte del progetto di aggiornamento AEM 6.4. Qualsiasi elemento nell’ambito dell’aggiornamento precedente alla versione 6.5 può essere eventualmente posticipato fino all’aggiornamento successivo.

Ogni voce della pagina include un campo &quot;Guida alla ristrutturazione&quot;, che descrive la strategia tecnica consigliata per l&#39;allineamento con il nuovo modello di archivio 6.4 in modo che le nuove posizioni siano referenziate per i contenuti precedentemente presenti nella cartella /etc. Un ulteriore campo &quot;Note&quot; fornisce qualsiasi contesto utile aggiuntivo.
