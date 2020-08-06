---
title: Componente Commenti overlay
seo-title: Componente Commenti overlay
description: Panoramica del componente Commenti sovrapposizione
seo-description: Panoramica del componente Commenti sovrapposizione
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Componente Commenti overlay {#overlay-comments-component}

L’intenzione di [sovrapporre](client-customize.md#overlays) un componente predefinito consiste nel modificare l’aspetto o il comportamento di un componente a livello globale, per tutti i riferimenti relativi al componente. Si basa sulla natura di sling per risolvere nella cartella /apps prima di cercare nella cartella /libs. Il percorso del componente è quindi identico al percorso del componente predefinito, ma si trova nella cartella /apps e non nella cartella /libs.

## Esempio {#example}

Supponete di voler modificare la funzione del commento in modo che corrisponda alla progettazione del sito Web, modificando l’intestazione del commento in modo che non venga più visualizzato l’avatar per i commenti. Le soluzioni per nascondere l&#39;avatar utilizzano CSS o, come descritto qui, sovrappongono header.jsp nella cartella delle app in modo che l&#39;HTML che contiene l&#39;avatar non venga mai inviato al client.

Per sovrapporre i commenti è necessario:

1. [Pagina Commenti](overlay-create-comments-page.md)
1. [Crea nodi](overlay-create-nodes.md)
1. [Modifica dell&#39;aspetto](overlay-alter-appearance.md)

