---
title: 'Esportazione in formato CSV  '
seo-title: 'Esportazione in formato CSV  '
description: Esporta informazioni sulle pagine in un file CSV sul sistema locale
seo-description: Esporta informazioni sulle pagine in un file CSV sul sistema locale
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 79%

---


# Esportazione in formato CSV  {#export-to-csv}

L’opzione **Crea esportazione CSV** consente di esportare le informazioni sulle pagine in un file CSV nel sistema locale.

* Il nome del file scaricato è `export.csv`
* Il contenuto dipende dalle proprietà selezionate.
* Puoi definire il percorso e il livello di profondità dell’esportazione.

>[!NOTE]
>
>Vengono utilizzate la funzione di download e la destinazione predefinita del browser in uso.

La procedura guidata Crea esportazione CSV permette di selezionare:

* Proprietà da esportare

   * Metadati

      * Modificato
      * Pubblicato
   * Analisi

      * Visualizzazioni pagina
      * Visitatori univoci
      * Tempo sulla pagina


* Profondità

   * Percorso principale
   * Solo elementi figlio diretti
   * Livelli aggiuntivi di elementi figlio
   * Livelli

Il file `export.csv` risultante può essere aperto in Excel o in un’altra applicazione compatibile.

![chlimage_1-58](assets/chlimage_1-58.png)

L&#39;opzione Crea **esportazione CSV** è disponibile quando si sfoglia la console **Siti** (in visualizzazione Elenco): è un&#39;opzione del menu a discesa **Crea**:

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

Per creare un’esportazione CSV:

1. Apri la console **Sites** e passa alla posizione desiderata, se necessario.
1. Dalla barra degli strumenti, selezionare **Crea** quindi **Esportazione CSV** per aprire la procedura guidata:

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. Seleziona le proprietà da esportare.
1. Seleziona **Crea**.

