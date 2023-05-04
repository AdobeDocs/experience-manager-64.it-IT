---
title: Aggiunta di font al rendering grafico
seo-title: Adding Fonts for Graphic-Rendering
description: AEM consente di generare elementi grafici che incorporano testo tratto dinamicamente dal contenuto
seo-description: AEM allows you to generate graphics incorporating text dynamically taken from your content
uuid: 67d9b10f-e986-4d29-bde2-10e08075fe17
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6af48ef5-75e6-4b66-bc0d-ecf254b1c4ef
exl-id: f29868e3-d05c-4898-94d1-0c77ab6b72eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 4%

---

# Aggiunta di font al rendering grafico{#adding-fonts-for-graphic-rendering}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM consente di generare elementi grafici che incorporano testo tratto dinamicamente dal contenuto.

A questo scopo è anche possibile caricare e utilizzare i propri font.

Attualmente tutte le implementazioni del supporto della piattaforma Java [TrueType](https://en.wikipedia.org/wiki/Truetype) font.

1. Apri CRXDE Lite e passa alla cartella dell&#39;applicazione di progetto:

   `/apps/<your-project>/`

1. Sotto `/apps/<your-project>/` crea un nuovo nodo:

   * **Nome**: `fonts`
   * **Tipo**: `sling:Folder`

   Salva tutte le modifiche.

1. Copiare i file di font in questa cartella; ad esempio, utilizzando WebDAV.

   >[!NOTE]
   >
   >I file di font nell’archivio devono avere il suffisso `*.ttf` o `*.TTF`.

1. Aggiorna [Configurazione OSGi](/help/sites-deploying/configuring-osgi.md) di [Helper font GFX Day Commons](/help/sites-deploying/osgi-configuration-settings.md). Aggiungi il percorso alla cartella dei font; ovvero `/apps/<your-project>/fonts`.

1. Torna a CRXDE Lite. Ora dovresti visualizzare un `.fontlist` nella cartella contenente il nome dei font importati.

   Questi font sono ora pronti per essere utilizzati nell’API Java.

Per informazioni dettagliate su come utilizzare i font con l’API Java, consulta la sezione [documentazione per la classe Font dell&#39;API Java](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
