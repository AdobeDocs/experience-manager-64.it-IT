---
title: Utilizzo delle aree di visualizzazione in AEM 3D
seo-title: Utilizzo delle aree di visualizzazione in AEM 3D
description: I passaggi sono file di scene 3D leggeri che forniscono l'ambiente di visualizzazione di base.
seo-description: I passaggi sono file di scene 3D leggeri che forniscono l'ambiente di visualizzazione di base.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
translation-type: tm+mt
source-git-commit: 9cc06c16122b98146c51ac61d7fa27553a9d971e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 56%

---


# Utilizzo delle aree di visualizzazione in AEM 3D {#about-the-use-of-stages-in-aem-d}

Le aree di visualizzazione sono leggeri file di scena 3D che forniscono un ambiente di visualizzazione di base (illuminazione, sfondo, piano terreno o altra geometria fissa), videocamere predefinite opzionali e impostazioni di rendering per i moduli di rendering di terze parti.

>[!NOTE]
>
>The **[!UICONTROL OBJ 3D]** format does not support lights. Di conseguenza, non può essere utilizzato per fornire aree di visualizzazione ad AEM 3D.

Il formato di file dell’area di visualizzazione determina quale modulo di rendering puoi usare. For example, if Autodesk® Maya® is used for high-quality rendering, the stage must be in `.ma` or `.mb` format. Se prevedi di utilizzare solo il modulo di rendering Rapid Refine™, è accettato qualsiasi formato di file supportato dell’area di visualizzazione.

Tutte le impostazioni di rendering in AEM 3D eccetto il tipo e la dimensione dell’immagine di output devono essere preconfigurate e salvate nel file dell’area di visualizzazione prima di caricare su AEM.