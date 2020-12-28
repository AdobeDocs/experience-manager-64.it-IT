---
title: Editor
seo-title: Editor
description: Scoprite come tornare all’editor dell’interfaccia classica.
seo-description: Scoprite come tornare all’editor dell’interfaccia classica.
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
translation-type: tm+mt
source-git-commit: 9fa15a44cf83a50538cea3fb37bcccf405f66738
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 8%

---


# Editor{#editor}

Per impostazione predefinita, è stata disattivata la possibilità di passare all’interfaccia classica dall’editor.

![chlimage_1-9](assets/chlimage_1-9.png)

Per riattivare l&#39;opzione **Apri nell&#39;interfaccia classica** nel menu **Informazioni pagina**, procedere come segue.

1. Utilizzando CRXDE Lite, trova il nodo seguente:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Esempio

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. Create una sovrapposizione utilizzando l&#39;opzione **Overlay Node**; ad esempio:

   * **Percorso**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Posizione sovrapposizione**: `/apps/`
   * **Corrispondenza tipi** di nodo: active (seleziona la casella di controllo)

1. Aggiungete la seguente proprietà di testo con più valori al nodo sovrapposto:

   `sling:hideProperties = ["granite:hidden"]`

1. L&#39;opzione **Apri nell&#39;interfaccia classica** è nuovamente disponibile nel menu **Informazioni pagina** durante la modifica delle pagine.

   ![chlimage_1-10](assets/chlimage_1-10.png)

