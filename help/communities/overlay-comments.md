---
title: Componente Commenti sovrapposti
seo-title: Overlay Comments Component
description: Panoramica del componente Commenti sovrapposti
seo-description: Overlay Comments component overview
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 4%

---

# Componente Commenti sovrapposti {#overlay-comments-component}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L&#39;intenzione di [sovrapposizione](client-customize.md#overlays) un componente predefinito è quello di modificare l’aspetto o il comportamento di un componente a livello globale, per tutti i riferimenti relativi al componente. Si basa sulla natura di sling per risolvere alla cartella /apps prima di cercare nella cartella /libs . Pertanto il percorso del componente è identico al percorso del componente predefinito, tranne che si trova nella cartella /apps e non nella cartella /libs .

## Esempio {#example}

Supponiamo che desideri modificare la funzione di commento in modo che corrisponda alla progettazione del sito web, modificando l’intestazione del commento in modo che non visualizzi più l’avatar per eventuali commenti. Le soluzioni per nascondere l&#39;avatar utilizzano CSS o, come descritto qui, sovrappongono header.jsp nella cartella delle app in modo che il HTML contenente l&#39;avatar non venga mai inviato al client.

Per sovrapporre i commenti è necessario:

1. [Pagina Commenti](overlay-create-comments-page.md)
1. [Crea nodi](overlay-create-nodes.md)
1. [Modificare l’aspetto](overlay-alter-appearance.md)
