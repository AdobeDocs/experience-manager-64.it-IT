---
title: Admin Console
seo-title: Admin Consoles
description: Scopri come utilizzare gli Admin Console disponibili in AEM.
seo-description: Lear how to use the Admin Consoles available in AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 4%

---

# Admin Console{#admin-consoles}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per impostazione predefinita, è stata disabilitata la possibilità di passare all’interfaccia classica tramite le console di amministrazione. Pertanto, le icone a comparsa visualizzate quando si passa il mouse su alcune icone della console e si consente l’accesso all’interfaccia classica, non vengono più visualizzate.

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

Ogni console con una versione dell’interfaccia classica in `/libs/cq/core/content/nav` può essere riattivato singolarmente in modo che il **Interfaccia classica** torna nuovamente a essere visualizzata sull’icona della console quando viene spostata.

In questo esempio, riattiveremo l’interfaccia classica per la console Sites .

1. Utilizzando CRXDE Lite, trova il nodo corrispondente alla Admin Console per la quale desideri riabilitare l’interfaccia classica. Si trovano in:

   `/libs/cq/core/content/nav`

   Per esempio

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Seleziona il nodo corrispondente alla console per la quale desideri riattivare l’interfaccia classica. Ad esempio, riattiveremo l’interfaccia classica per la console Sites .

   `/libs/cq/core/content/nav/sites`

1. Crea una sovrapposizione utilizzando il **Nodo di sovrapposizione** opzione; ad esempio:

   * **Percorso**: `/apps/cq/core/content/nav/sites`
   * **Posizione sovrapposizione**: `/apps/`
   * **Tipi di nodo corrispondenti**: attivo (seleziona la casella di controllo)

1. Aggiungi la seguente proprietà booleana al nodo sovrapposto:

   `enableDesktopOnly = {Boolean}true`

1. La **Interfaccia classica** è nuovamente disponibile come opzione di pover in admin console.

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

Ripeti questi passaggi per ogni console per la quale desideri riabilitare l’accesso alla versione dell’interfaccia classica.
