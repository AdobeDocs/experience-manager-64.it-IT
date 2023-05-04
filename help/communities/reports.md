---
title: Console Rapporti
seo-title: Reports Console
description: Scopri come accedere ai rapporti
seo-description: Learn how to access reports
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: Admin
exl-id: 766711ea-f3d3-49ab-8346-4e4477c261bd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 8%

---

# Console Rapporti {#reports-console}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

Per AEM Communities, è possibile accedere a diversi rapporti in diversi modi dall’ambiente di authoring.

In generale, le varie relazioni sono:

* [Rapporto Assegnazioni](#assignments-report) - per un [comunità di abilitazione](overview.md#enablement-community), fornisce una panoramica dei progressi compiuti dagli studenti nelle loro assegnazioni, con un punteggio associato se si implementa lo standard SCORM
* [Rapporto visualizzazioni](#views-report) - fornisce un grafico dei contenuti dei membri della community e dei visitatori del sito per qualsiasi sito della community
* [Report post](#posts-report) - fornisce un grafico dei vari tipi di post dei membri della community su qualsiasi sito della community

Quando [Adobe Analytics è abilitato](sites-console.md#analytics), i rapporti includeranno il numero di visualizzazioni, riproduzioni, commenti e valutazioni per ogni risorsa di abilitazione nel tempo

I rapporti tabulari possono essere esportati in formato .csv per successive elaborazioni.

## Console di reporting {#reporting-consoles}

### Rapporti per siti della community {#reports-for-community-sites}

* Dalla navigazione globale: **[!UICONTROL Navigazione > Community > Report]**
* Scegli tra
   * **[!UICONTROL Rapporto assegnazioni]**
      * Genera un report per la sede, l&#39;utente o il gruppo della community selezionati e l&#39;assegnazione
   * **[!UICONTROL Rapporto sui post]**
      * Genera un report per il sito della community selezionato, il tipo di contenuto e il periodo di tempo
   * **[!UICONTROL Rapporto visualizzazioni]**
      * Genera un report per il sito della community selezionato, il tipo di contenuto e il periodo di tempo
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Rapporti per risorse di abilitazione e percorsi di apprendimento {#reports-for-enablement-resources-and-learning-paths}

* Dalla navigazione globale: **[!UICONTROL Navigazione > Community > Risorse]**
* Seleziona un sito community di abilitazione esistente
   * Seleziona **[!UICONTROL Rapporto]** icona per generare rapporti che coprono tutte le risorse di abilitazione
   * Selezionare un percorso di apprendimento per l’abilitazione
   * Seleziona **[!UICONTROL Rapporto]** icona per generare rapporti per
      * Risorse di abilitazione incluse
      * Gli studenti assegnati al percorso di apprendimento
* Tali rapporti forniscono:
   * Dati tabella, scaricabili come CSV
      * Identificazione dello studente
      * Il loro status
      * Assegnazione o accesso tramite catalogo
      * Numero di osservazioni formulate
      * Classificazione a stelle

Per ulteriori dettagli, consulta [Sezione Rapporti](resources.md#report) della console Risorse .

## Rapporto assegnazioni {#assignments-report}

La console Assegnazioni consente di filtrare i rapporti in base al sito della community di abilitazione, agli utenti o ai gruppi e all’assegnazione.

La relazione fornisce informazioni sui loro progressi nonché eventuali commenti o valutazioni forniti.

![chlimage_1-157](assets/chlimage_1-157.png)

Seleziona i criteri per il rapporto:

* **[!UICONTROL Sito]**
Selezionare un sito community di abilitazione
* **[!UICONTROL Utente o gruppo]**
   * Selezionare Utente per generare un rapporto per uno studente
   * Selezionare Gruppo per generare un rapporto per un gruppo di studenti Il servizio tunnel accederà ai membri e ai gruppi di membri dall&#39;ambiente di pubblicazione
* **[!UICONTROL Assegnazione]**
Scegli tra le risorse di abilitazione assegnate agli studenti selezionati

Seleziona **[!UICONTROL Genera]** per creare il rapporto:

![chlimage_1-158](assets/chlimage_1-158.png)

## Rapporto visualizzazioni {#views-report}

La console Visualizzazioni consente di generare rapporti sulle visualizzazioni di pagina in base alle funzioni della community per un determinato periodo di tempo.

![chlimage_1-159](assets/chlimage_1-159.png)

Seleziona i criteri per il rapporto:

* **[!UICONTROL Sito]**
Selezionare un sito community
* **[!UICONTROL Tipo di contenuto]**
Può scegliere Tutto il contenuto o selezionare una delle funzioni presenti sul sito
* Intervallo temporale Selezionare una delle seguenti opzioni:
   * Ultimi 7 giorni
   * Ultimi 30 giorni
   * Ultimi 90 giorni
   * Ultimo anno

Seleziona **[!UICONTROL Genera]** per creare il rapporto:

![chlimage_1-160](assets/chlimage_1-160.png)

## Rapporto sui post {#posts-report}

La console Post consente di generare rapporti sul numero di post nelle funzioni della community per un determinato periodo di tempo.

![chlimage_1-161](assets/chlimage_1-161.png)

Seleziona i criteri per il rapporto:

* **[!UICONTROL Sito]**
Selezionare un sito community
* **[!UICONTROL Tipo di contenuto]**
Può scegliere Tutto il contenuto o selezionare una delle funzioni presenti sul sito
* Intervallo temporale Selezionare una delle seguenti opzioni:
   * Ultimi 7 giorni
   * Ultimi 30 giorni
   * Ultimi 90 giorni
   * Ultimo anno

Seleziona **[!UICONTROL Genera]** per creare il rapporto:

![chlimage_1-162](assets/chlimage_1-162.png)

## Risoluzione dei problemi {#troubleshooting}

### Nessun sito community elencato {#no-community-sites-listed}

Se non sono elencati siti della community, assicurati che Adobe Analytics sia stato abilitato per un sito. Se si selezionano i rapporti relativi alle assegnazioni, verificare che la funzione delle assegnazioni si trovi nella struttura del sito della community.
