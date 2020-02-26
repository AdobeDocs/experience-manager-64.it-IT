---
title: Utilizzo delle aree di visualizzazione in AEM 3D
seo-title: Utilizzo delle aree di visualizzazione in AEM 3D
description: Le aree di visualizzazione sono leggeri file di scena 3D che forniscono un ambiente di visualizzazione di base (illuminazione, sfondo, piano terreno o altra geometria fissa), videocamere predefinite opzionali e impostazioni di rendering per i moduli di rendering di terze parti.
seo-description: Le aree di visualizzazione sono leggeri file di scena 3D che forniscono un ambiente di visualizzazione di base (illuminazione, sfondo, piano terreno o altra geometria fissa), videocamere predefinite opzionali e impostazioni di rendering per i moduli di rendering di terze parti.
uuid: 303ecbbd-131e-4c6f-812a-1e056b1e1d63
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: cbcfbe88-e60c-446c-bbfe-2509831d6c22
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42

---


# Utilizzo delle aree di visualizzazione in AEM 3D{#about-the-use-of-stages-in-aem-d}

Le aree di visualizzazione sono leggeri file di scena 3D che forniscono un ambiente di visualizzazione di base (illuminazione, sfondo, piano terreno o altra geometria fissa), videocamere predefinite opzionali e impostazioni di rendering per i moduli di rendering di terze parti.

>[!NOTE]
>
>Il formato OBJ 3D non supporta le luci. Di conseguenza, non può essere utilizzato per fornire aree di visualizzazione ad AEM 3D.

Il formato di file dell’area di visualizzazione determina quale modulo di rendering puoi usare. For example, if Autodesk® Maya® is used for high-quality rendering, the stage must be in `.ma` or `.mb` format. Se prevedi di utilizzare solo il modulo di rendering Rapid Refine™, è accettato qualsiasi formato di file supportato dell’area di visualizzazione.

È necessario preconfigurare e salvare nel file dell’area di visualizzazione tutte le impostazioni di rendering in AEM 3D, tranne il tipo di immagine prodotta e la dimensione, prima di caricarle in AEM.

