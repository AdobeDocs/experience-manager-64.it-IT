---
title: Utilizzo delle risorse Adobe Dimension
description: Utilizzo delle risorse Adobe Dimension in AEM 3D.
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: be8f6361-607d-4529-aef0-e8978dfd04b4
feature: Risorse 3D
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Utilizzo delle risorse Adobe Dimension {#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>Il feature pack AEM 3D in AEM 6.4 non è più supportato. Adobe consiglia di utilizzare la funzione risorse 3D in [AEM come Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) o [AEM 6.5.3 o superiore.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) quando si lavora con risorse Adobe Dimension.

Il feature pack AEM 3D supporta le risorse Adobe Dimension (`.dn` file) in AEM Assets , AEM Sites e AEM Screens.

Un nuovo visualizzatore 3D basato sullo standard aperto glTF fornisce funzionalità di anteprima e visualizzazione di Sites e Screens per le risorse Adobe Dimension.

## Informazioni sul servizio di conversione basato su cloud {#about-the-cloud-based-conversion-service}

Quando una risorsa di Dimension viene caricata in AEM, una copia del file viene inoltrata a un servizio basato su cloud gestito da Adobe ospitato in Amazon AWS. Questo servizio converte il formato di file di Dimension proprietario dell&#39;Adobe in formato glTF standard aperto. Il modello 3D convertito viene assemblato come glTF binario (`.glb`). AEM memorizza il modello convertito con la risorsa del Dimension principale come rendering.

Puoi configurare il formato di conversione `.glb` in uno dei due modi seguenti (per istruzioni consulta [Installazione e configurazione AEM 3D](install-config-3d.md) ):

* Includi estensioni specifiche per Adobi per massimizzare la qualità visiva quando utilizzi il visualizzatore Adobe glTF per visualizzare le risorse di Dimension in AEM Assets, AEM Sites o AEM Screens. Questo rende i rendering `.glb` incompatibili con la maggior parte delle applicazioni di terze parti.
* Escludi le estensioni specifiche per Adobe per ottenere la compatibilità del rendering `.glb` con applicazioni di terze parti. Questo limita la qualità visiva quando si visualizzano in AEM Assets, AEM Sites o AEM Screens (ad esempio, senza illuminazione IBL) per simulare la qualità delle tipiche applicazioni di terze parti.

Il trasferimento dei file di Dimension/glTF da o verso Amazon AWS e la relativa memorizzazione temporanea in AWS sono completamente protetti. Questi file persistono in Amazon AWS per un periodo di tempo minimo; normalmente, non più di pochi minuti durante le operazioni normali.

Per abilitare il supporto per le risorse di Dimension, devi ottenere le credenziali da Adobe per accedere al servizio di conversione. Consulta [Installazione e configurazione AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Se installi e utilizzi le credenziali fornite, comprendi e accetti che le risorse 3D di Adobe Dimension vengano trasferite al servizio di conversione basato su cloud gestito da Adobe ospitato in Amazon AWS e da esso elaborate.

### Visualizzazione su AEM Assets {#viewing-on-aem-assets}

Il feature pack AEM 3D include un nuovo visualizzatore basato sullo standard aperto glTF utilizzato per visualizzare le risorse Adobe Dimension. Questo visualizzatore viene selezionato automaticamente quando si apre un file di Dimension o un GlTF compresso nella vista Dettaglio in AEM Assets o con il componente 3D in AEM Sites.

L’interfaccia utente del visualizzatore glTF è leggermente diversa dal visualizzatore 3D standard utilizzato per tutti gli altri tipi di risorse 3D.

#### Vedi anche quanto segue: {#see-also-the-following}

* [AEM ](/help/release-notes/aem3d-release-notes.md) note sulla versione 3D per le restrizioni e le limitazioni applicabili alle risorse Dn e al visualizzatore glTF.
* [Utilizzo del ](using-the-3d-sites-component.md) componente Siti 3D per le proprietà dei componenti specifiche delle risorse Adobe Dimension.
* [Installazione e configurazione di AEM 3](install-config-3d.md) Dper configurare il servizio di conversione basato su cloud.
