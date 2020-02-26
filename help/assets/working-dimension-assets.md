---
title: Utilizzo delle risorse Adobe Dimension
seo-title: Utilizzo delle risorse Adobe Dimension
description: Utilizzo delle risorse Adobe Dimension in AEM 3D.
seo-description: Utilizzo delle risorse Adobe Dimension in AEM 3D.
uuid: 476e6758-b3a1-42ba-a18d-bfc407c6a72e
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 4a601c2a-4ea1-4308-8ae8-704155f63c21
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f

---


# Utilizzo delle risorse Adobe Dimension {#working-with-adobe-dimension-assets}

Il feature pack AEM 3D supporta le risorse Adobe Dimension (`.dn` file) in AEM Assets, AEM Sites e AEM Screens.

Un nuovo visualizzatore 3D basato sullo standard aperto glTF offre funzionalità di anteprima e visualizzazione Siti e Schermi per le risorse Adobe Dimension.

## Informazioni sul servizio di conversione basato su cloud {#about-the-cloud-based-conversion-service}

Quando una risorsa Dimension viene caricata in AEM, una copia del file viene inoltrata a un servizio basato su cloud gestito da Adobe ospitato in Amazon AWS. Questo servizio converte il formato di file Dimension proprietario di Adobe nel formato glTF standard aperto. Il modello 3D convertito viene assemblato come glTF binario (`.glb`). AEM memorizza il modello convertito con la risorsa Dimensione primaria come rappresentazione.

Potete configurare il formato di `.glb` conversione in uno dei due modi (consultate [Installazione e configurazione di AEM 3D](install-config-3d.md) per le istruzioni):

* Includi estensioni specifiche di Adobe per massimizzare la qualità visiva quando si utilizza il visualizzatore Adobe glTF per visualizzare le risorse Dimensione in AEM Assets, AEM Sites o AEM Screens. Questo rende le `.glb` rappresentazioni incompatibili con la maggior parte delle applicazioni di terze parti.
* Escludete estensioni specifiche di Adobe per garantire la compatibilità del `.glb` rendering con applicazioni di terze parti. Questo limita la qualità visiva quando si visualizzano in AEM Assets, AEM Sites o AEM Screens (ad esempio, nessuna illuminazione IBL) per simulare la qualità delle tipiche applicazioni di terze parti.

Il trasferimento dei file Dimension/glTF a o da Amazon AWS e il loro archiviazione temporanea in AWS sono completamente protetti. Questi file persistono in Amazon AWS per un periodo minimo di tempo; in genere, non più di pochi minuti durante le normali operazioni.

Per abilitare il supporto per le risorse Dimension, devi ottenere le credenziali da Adobe per accedere al servizio di conversione. See [Installing and configuring AEM 3D](install-config-3d.md).

>[!NOTE]
>
>Se installate e utilizzate le credenziali fornite, potete comprendere e accettare che le risorse Adobe Dimension 3D verranno trasferite e elaborate dal servizio di conversione basato su cloud gestito da Adobe ospitato in Amazon AWS.

### Visualizzazione in Risorse AEM {#viewing-on-aem-assets}

Il feature pack AEM 3D include un nuovo visualizzatore basato sullo standard aperto glTF, utilizzato per visualizzare le risorse Adobe Dimension. Questo visualizzatore viene selezionato automaticamente quando si apre un file Dimensione o un file .glTF compresso nella visualizzazione Dettagli di Risorse AEM o con il componente 3D in AEM Sites.

L&#39;interfaccia utente del visualizzatore GlTF è leggermente diversa dal visualizzatore 3D standard utilizzato per tutti gli altri tipi di risorse 3D.

#### See also the following: {#see-also-the-following}

* [Note](/help/release-notes/aem3d-release-notes.md) sulla versione AEM 3D per limitazioni e limitazioni applicabili alle risorse Dn e al visualizzatore glTF.
* [Utilizzo del componente](using-the-3d-sites-component.md) Siti 3D per le proprietà dei componenti specifiche delle risorse Adobe Dimension.
* [Installazione e configurazione di AEM 3D](install-config-3d.md) per configurare il servizio di conversione basato su cloud.

