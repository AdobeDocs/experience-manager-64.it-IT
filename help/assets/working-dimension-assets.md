---
title: Utilizzo di  risorse Adobe Dimension
seo-title: Utilizzo di  risorse Adobe Dimension
description: Utilizzo  risorse Adobe Dimension in AEM 3D.
seo-description: Utilizzo  risorse Adobe Dimension in AEM 3D.
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---


# Utilizzo di  risorse Adobe Dimension {#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>AEM feature pack 3D in AEM 6.4 non è più supportato.  Adobe consiglia di utilizzare la funzione delle risorse 3D in [AEM come Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) o [AEM 6.5.3 o superiore.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html) quando lavorate con  risorse Adobe Dimension.

AEM feature pack 3D supporta  risorse Adobe Dimension (`.dn` file) in  AEM Assets,  AEM Sites e  AEM Screens.

Un nuovo visualizzatore 3D basato sullo standard aperto glTF offre funzionalità di anteprima e visualizzazione Siti e Schermi per  risorse Adobe Dimension.

## Informazioni sul servizio di conversione basato su cloud {#about-the-cloud-based-conversion-service}

Quando una risorsa di Dimension viene caricata in AEM, una copia del file viene inoltrata a un  servizio basato su cloud gestito Adobe ospitato in  Amazon AWS. Questo servizio converte il formato di file di Dimension proprietario del Adobe  nel formato standard aperto glTF. Il modello 3D convertito viene compresso come glTF binario (`.glb`). AEM memorizza il modello convertito con la risorsa Dimension principale come rappresentazione.

È possibile configurare il formato di conversione `.glb` in uno dei due modi (vedere [Installazione e configurazione AEM 3D](install-config-3d.md) per le istruzioni):

* Includete estensioni specifiche per  Adobe per ottimizzare la qualità visiva quando usate il visualizzatore  Adobe glTF per visualizzare Dimension risorse di  in  AEM Assets,  AEM Sites o  AEM Screens. Ciò rende le rappresentazioni `.glb` incompatibili con la maggior parte delle applicazioni di terze parti.
* Escludete  estensioni specifiche del Adobe per ottenere la compatibilità del rendering `.glb` con applicazioni di terze parti. Questo limita la qualità visiva quando si visualizzano  AEM Assets,  AEM Sites o  AEM Screens (ad esempio, nessuna illuminazione IBL) per simulare la qualità delle tipiche applicazioni di terze parti.

Il trasferimento dei file Dimension/glTF da o verso  Amazon AWS e la loro memorizzazione temporanea in AWS sono completamente protetti. Tali file persistono in  Amazon AWS per un periodo minimo di tempo; in genere, non più di pochi minuti durante le normali operazioni.

Per abilitare il supporto per le risorse di Dimension, dovete ottenere le credenziali da  Adobe per accedere al servizio di conversione. Vedere [Installazione e configurazione AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Se installate e utilizzate le credenziali fornite, potete comprendere e accettare che le risorse Adobe Dimension 3D  saranno trasferite e elaborate dal  servizio di conversione basato su cloud gestito dal Adobe ospitato in  Amazon AWS.

### Visualizzazione su  AEM Assets {#viewing-on-aem-assets}

Il AEM feature pack 3D include un nuovo visualizzatore basato sullo standard aperto glTF, utilizzato per visualizzare  risorse Adobe Dimension. Questo visualizzatore viene selezionato automaticamente quando si apre un file di Dimension o un file glTF compresso nella visualizzazione Dettagli in  AEM Assets o con il componente 3D in  AEM Sites.

L&#39;interfaccia utente del visualizzatore GlTF è leggermente diversa dal visualizzatore 3D standard utilizzato per tutti gli altri tipi di risorse 3D.

#### Vedi anche quanto segue: {#see-also-the-following}

* [AEM ](/help/release-notes/aem3d-release-notes.md) note sulla versione 3D per limitazioni e limitazioni applicabili alle risorse Dn e al visualizzatore glTF.
* [Utilizzo del ](using-the-3d-sites-component.md) componente Siti 3D per le proprietà dei componenti specifiche per  risorse Adobe Dimension.
* [Installazione e configurazione AEM 3](install-config-3d.md) Dto per configurare il servizio di conversione basato su cloud.

