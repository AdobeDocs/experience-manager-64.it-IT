---
title: 'Admin Console '
seo-title: 'Admin Console '
description: Scoprite come utilizzare gli Admin Console  disponibili in AEM.
seo-description: Scoprite come utilizzare gli Admin Console  disponibili in AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 2%

---


# Admin Console {#admin-consoles}

Per impostazione predefinita, è stata disattivata la possibilità di passare all’interfaccia classica tramite le console di amministrazione. Pertanto, le icone a comparsa visualizzate quando si passa il mouse su determinate icone della console e si consente l’accesso all’interfaccia classica, non vengono più visualizzate.

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

Ogni console con una versione dell&#39;interfaccia classica in `/libs/cq/core/content/nav` può essere riattivata singolarmente, in modo che l&#39;opzione **Interfaccia classica** venga nuovamente visualizzata sopra l&#39;icona della console quando viene spostata.

In questo esempio viene riattivata l’interfaccia classica per la console Siti.

1. Utilizzando CRXDE Lite, trovate il nodo corrispondente alla console di amministrazione per il quale desiderate riabilitare l’interfaccia classica. Sono disponibili in:

   `/libs/cq/core/content/nav`

   Esempio

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Selezionate il nodo corrispondente alla console per la quale desiderate riattivare l’interfaccia classica. Ad esempio, riattiveremo l’interfaccia classica per la console Siti.

   `/libs/cq/core/content/nav/sites`

1. Create una sovrapposizione utilizzando l&#39;opzione **Overlay Node**; ad esempio:

   * **Percorso**: `/apps/cq/core/content/nav/sites`
   * **Posizione sovrapposizione**: `/apps/`
   * **Corrispondenza tipi** di nodo: active (seleziona la casella di controllo)

1. Aggiungete la seguente proprietà booleana al nodo sovrapposto:

   `enableDesktopOnly = {Boolean}true`

1. L&#39;opzione **Interfaccia classica** è nuovamente disponibile come opzione del puntatore nella console di amministrazione.

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

Ripetete questi passaggi per ogni console per la quale desiderate riattivare l’accesso alla versione dell’interfaccia classica.
