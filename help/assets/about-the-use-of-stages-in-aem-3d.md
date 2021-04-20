---
title: Utilizzo delle aree di visualizzazione in AEM 3D
seo-title: Utilizzo delle aree di visualizzazione in AEM 3D
description: Le aree di visualizzazione sono file di scena 3D leggeri che forniscono l'ambiente di visualizzazione di base.
seo-description: Le aree di visualizzazione sono file di scena 3D leggeri che forniscono l'ambiente di visualizzazione di base.
uuid: 9098278c-0467-45ea-98ad-7f345c314d9e
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 7b9d3b81-3bb4-4ca6-b6e1-f9adfb455855
exl-id: 6d82fec0-608e-4eaa-aebd-b3ce2f7d8088
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 55%

---

# Utilizzo delle aree di visualizzazione in AEM 3D {#about-the-use-of-stages-in-aem-d}

Le aree di visualizzazione sono leggeri file di scena 3D che forniscono un ambiente di visualizzazione di base (illuminazione, sfondo, piano terreno o altra geometria fissa), videocamere predefinite opzionali e impostazioni di rendering per i moduli di rendering di terze parti.

>[!NOTE]
>
>Il formato **[!UICONTROL OBJ 3D]** non supporta le luci. Di conseguenza, non può essere utilizzato per fornire aree di visualizzazione ad AEM 3D.

Il formato di file dell’area di visualizzazione determina quale modulo di rendering puoi usare. Ad esempio, se si utilizza Autodesk® Maya® per il rendering di alta qualità, l’area di visualizzazione deve essere in formato `.ma` o `.mb`. Se prevedi di utilizzare solo il modulo di rendering Rapid Refine™, è accettato qualsiasi formato di file supportato dell’area di visualizzazione.

Tutte le impostazioni di rendering in AEM 3D, ad eccezione del tipo e della dimensione dell&#39;immagine di output, devono essere preconfigurate e salvate nel file dell&#39;area di visualizzazione prima di caricarle in AEM.
