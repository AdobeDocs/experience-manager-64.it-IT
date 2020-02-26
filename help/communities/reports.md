---
title: Console Rapporti
seo-title: Console Rapporti
description: Scopri come accedere ai rapporti
seo-description: Scopri come accedere ai rapporti
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7

---


# Console Rapporti {#reports-console}

## Panoramica {#overview}

Per AEM Communities, esistono diversi rapporti a cui è possibile accedere in diversi modi dall&#39;ambiente di authoring.

In generale, le varie relazioni sono:

* [Rapporto](#assignments-report) Assegnazioni - per una comunità di [abilitazione](overview.md#enablement-community), fornisce una panoramica dei progressi compiuti dagli studenti nelle loro mansioni, inclusa una valutazione associata nell&#39;implementazione dello standard SCORM
* [Rapporto](#views-report) visualizzazioni - fornisce un grafico dei contenuti per membri della community e visitatori del sito per qualsiasi sito della community
* [Rapporto](#posts-report) Post - fornisce un grafico dei vari tipi di post dei membri della community in qualsiasi sito della community

Quando [Adobe Analytics è abilitato](sites-console.md#analytics), i rapporti includeranno il numero di visualizzazioni, riproduzioni, commenti e valutazioni per ciascuna risorsa di abilitazione nel tempo

I rapporti tabulari possono essere esportati in formato .csv per l’elaborazione successiva.

## Console di reporting {#reporting-consoles}

### Report per siti community {#reports-for-community-sites}

* Dalla navigazione globale: **[!UICONTROL Navigazione > Community > Rapporti]**
* Scegli da
   * **[!UICONTROL Rapporto assegnazioni]**
      * Genera un rapporto per il sito, l&#39;utente o il gruppo community selezionato e l&#39;assegnazione
   * **[!UICONTROL Rapporto sui post]**
      * Genera un rapporto per il sito community selezionato, il tipo di contenuto e il periodo di tempo
   * **[!UICONTROL Rapporto visualizzazioni]**
      * Genera un rapporto per il sito community selezionato, il tipo di contenuto e il periodo di tempo
         ![chlimage_1-156](assets/chlimage_1-156.png)

### Rapporti per risorse di abilitazione e percorsi di apprendimento {#reports-for-enablement-resources-and-learning-paths}

* Dalla navigazione globale: **[!UICONTROL Navigazione > Community > Risorse]**
* Selezione di un sito community di abilitazione esistente
   * Selezionate l’icona **[!UICONTROL Rapporto]** per generare rapporti che coprono tutte le risorse di abilitazione
   * Selezionare un percorso di apprendimento per l&#39;abilitazione
   * Seleziona l’icona **[!UICONTROL Rapporto]** per generare i rapporti
      * Risorse di abilitazione incluse
      * Gli studenti assegnati al percorso di apprendimento
* Tali rapporti forniscono:
   * Dati tabella, scaricabili come CSV
      * Identificazione dello studente
      * Il loro status
      * Assegnazione o accesso tramite catalogo
      * Numero di osservazioni fatte
      * Valutazione a stella

Per ulteriori dettagli, consultate la sezione [](resources.md#report) Rapporti della console Risorse.

## Rapporto assegnazioni {#assignments-report}

La console Assegnazioni consente di filtrare i rapporti in base all&#39;abilitazione del sito community, degli utenti o dei gruppi e dell&#39;assegnazione.

Il rapporto fornisce informazioni sui loro progressi nonché eventuali commenti o valutazioni forniti.

![chlimage_1-157](assets/chlimage_1-157.png)

Seleziona i criteri per il rapporto:

* **[!UICONTROL Sito]** Selezione di un sito community di abilitazione
* **[!UICONTROL Utente o gruppo]**
   * Selezionate Utente per generare un rapporto per uno studente
   * Selezionate Gruppo per generare un rapporto per un gruppo di utenti in formazione. Il servizio tunnel accederà ai membri e ai gruppi di membri dall’ambiente di pubblicazione
* **[!UICONTROL Assegnazione]** Scegliere tra le risorse di abilitazione assegnate allo studente selezionato

Selezionate **[!UICONTROL Genera]** per creare il rapporto:

![chlimage_1-158](assets/chlimage_1-158.png)

## Rapporto visualizzazioni {#views-report}

La console Visualizzazioni consente di generare rapporti sulle visualizzazioni di pagina in base alle funzioni per community per un determinato periodo di tempo.

![chlimage_1-159](assets/chlimage_1-159.png)

Seleziona i criteri per il rapporto:

* **[!UICONTROL Sito]** Selezionare un sito community
* **[!UICONTROL Tipo]** di contenuto Può scegliere Tutto il contenuto o selezionare una delle funzioni presenti sul sito
* Intervallo di tempo: selezionare una delle seguenti opzioni:
   * Ultimi 7 giorni
   * Ultimi 30 giorni
   * Ultimi 90 giorni
   * Ultimo anno

Selezionate **[!UICONTROL Genera]** per creare il rapporto:

![chlimage_1-160](assets/chlimage_1-160.png)

## Rapporto sui post {#posts-report}

La console Post consente di generare rapporti sul numero di post alle funzioni della community per un determinato periodo di tempo.

![chlimage_1-161](assets/chlimage_1-161.png)

Seleziona i criteri per il rapporto:

* **[!UICONTROL Sito]** Selezionare un sito community
* **[!UICONTROL Tipo]** di contenuto Può scegliere Tutto il contenuto o selezionare una delle funzioni presenti sul sito
* Intervallo di tempo: selezionare una delle seguenti opzioni:
   * Ultimi 7 giorni
   * Ultimi 30 giorni
   * Ultimi 90 giorni
   * Ultimo anno

Selezionate **[!UICONTROL Genera]** per creare il rapporto:

![chlimage_1-162](assets/chlimage_1-162.png)

## Risoluzione dei problemi {#troubleshooting}

### Nessun sito community elencato {#no-community-sites-listed}

Se non sono elencati siti community, accertati che Adobe Analytics sia stato abilitato per un sito. Se scegli rapporti sulle assegnazioni, assicurati che la funzione delle assegnazioni sia nella struttura del sito della community.
