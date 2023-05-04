---
title: Esportazione in formato CSV
seo-title: Export to CSV
description: Esporta informazioni sulle pagine in un file CSV nel sistema locale
seo-description: Export information about your pages to a CSV file on your local system
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 51%

---

# Esportazione in formato CSV  {#export-to-csv}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

**Crea esportazione CSV** consente di esportare le informazioni sulle pagine in un file CSV nel sistema locale.

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
   * Analytics

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

La creazione **Esportazione CSV** è disponibile quando esplori la pagina **Sites** console (nella vista a elenco): è un&#39;opzione del **Crea** menu a discesa:

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

Per creare un’esportazione CSV:

1. Apri la console **Sites** e passa alla posizione desiderata, se necessario.
1. Dalla barra degli strumenti, seleziona **Crea** then **Esportazione CSV** per aprire la procedura guidata:

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. Seleziona le proprietà da esportare.
1. Seleziona **Crea**.
