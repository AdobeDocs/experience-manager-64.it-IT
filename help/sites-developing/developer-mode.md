---
title: Modalità Sviluppatore
seo-title: Developer Mode
description: La modalità Sviluppatore apre un pannello laterale con diverse schede che forniscono a uno sviluppatore informazioni sulla pagina corrente
seo-description: Developer mode opens a side panel with several tabs that provide a developer with infomation about the current page
uuid: 2ff0d85e-fe49-4506-b6d6-74cc060d7ea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: efbe46a3-c37f-4b67-8b3a-188cfc75118b
exl-id: 733eddf1-48f9-45c2-a1b4-138cf32b4b59
source-git-commit: 51358642a2fa8f59f3f5e3996b0c37269632c4cb
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 2%

---

# Modalità Sviluppatore{#developer-mode}

Durante la modifica di pagine in AEM, diverse [modalità](/help/sites-authoring/author-environment-tools.md#page-modes) sono disponibili, inclusa la modalità Sviluppatore . Viene aperto un pannello laterale con diverse schede che forniscono a uno sviluppatore informazioni sulla pagina corrente. Le tre schede sono:

* **[Componenti](#components)** per visualizzare informazioni sulla struttura e sulle prestazioni.
* **[Test](#tests)** per eseguire i test e analizzare i risultati.
* **[Errori](#errors)** per vedere eventuali problemi.

Queste consentono a uno sviluppatore di:

* Scopri: di quali pagine sono composte.
* Debug: cosa succede dove e quando, che a sua volta aiuta a risolvere i problemi.
* Test: l&#39;applicazione si comporta come previsto.

>[!CAUTION]
>
>Modalità sviluppatore:
>
>* È disponibile solo nell’interfaccia touch (durante la modifica delle pagine).
>* Non è disponibile su dispositivi mobili o piccole finestre sul desktop (a causa di limitazioni di spazio).
   >   * Questo si verifica quando la larghezza è inferiore a 1024 px.
>* È disponibile solo per gli utenti che sono membri del gruppo `administrators` gruppo.


>[!CAUTION]
>
>La modalità Sviluppatore è disponibile solo in un’istanza standard dell’autore che non utilizza la modalità di esecuzione nosamplecontent.
>
>Se necessario, può essere configurato per l’uso:
>
>* su un&#39;istanza dell&#39;autore che utilizza nosamplecontent run-mode
>* un&#39;istanza di pubblicazione
>
>Dopo l’utilizzo, deve essere nuovamente disattivato.

>[!NOTE]
>
>Vedi:
>
>* articolo della knowledge base, [Risoluzione dei problemi AEM TouchUI](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html), per ulteriori suggerimenti e strumenti.
>* sessione AEM Gems su [AEM 6.0 Developer Mode](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html).


## Apertura della modalità Sviluppatore {#opening-developer-mode}

La modalità Sviluppatore viene implementata come pannello laterale nell’editor di pagine. Per aprire il pannello, seleziona **Sviluppatore** dal selettore modalità nella barra degli strumenti dell’editor di pagine:

![chlimage_1-229](assets/chlimage_1-229.png)

Il pannello è diviso in due schede:

* **[Componenti](/help/sites-developing/developer-mode.md#components)** - Viene visualizzata una struttura ad albero dei componenti, simile a [struttura contenuto](/help/sites-authoring/author-environment-tools.md#content-tree) per autori

* **[Errori](/help/sites-developing/developer-mode.md#errors)** - Quando si verificano dei problemi, vengono visualizzati i dettagli di ciascun componente.

### Componenti {#components}

![chlimage_1-230](assets/chlimage_1-230.png)

Viene visualizzata una struttura ad albero dei componenti che:

* Illustra la catena di componenti e modelli di cui è stato eseguito il rendering nella pagina (SLY, JSP, ecc.). La struttura ad albero può essere espansa per mostrare il contesto all’interno della gerarchia.
* Mostra il tempo di calcolo lato server necessario per eseguire il rendering del componente.
* Consente di espandere la struttura ad albero e selezionare componenti specifici all’interno della struttura. La selezione permette di accedere ai dettagli dei componenti; quali:

   * Percorso archivio
   * Collegamenti agli script (a cui si accede in CRXDE Lite)

* I componenti selezionati (nel flusso del contenuto, indicati da un bordo blu) vengono evidenziati nella struttura del contenuto (e viceversa).

Questo può essere utile per:

* Determina e confronta il tempo di rendering per componente.
* Visualizzare e comprendere la gerarchia.
* Comprendere e quindi migliorare il tempo di caricamento della pagina trovando componenti lenti.

Ogni voce di componente può mostrare (ad esempio:

![chlimage_1-231](assets/chlimage_1-231.png)

* **Visualizza dettagli**: un collegamento a un elenco che mostra:

   * tutti gli script di componenti utilizzati per il rendering del componente.
   * percorso del contenuto dell’archivio per questo componente specifico.

   ![chlimage_1-232](assets/chlimage_1-232.png)

* **Modifica script**: un collegamento che:

   * apre lo script del componente in CRXDE Lite.

* L’espansione di una voce di componente (freccia a testa) può anche mostrare:

   * La gerarchia all’interno del componente selezionato.
   * Tempi di rendering del componente selezionato in isolamento, di tutti i singoli componenti nidificati al suo interno e del totale combinato.

   ![chlimage_1-233](assets/chlimage_1-233.png)

>[!CAUTION]
>
>Alcuni collegamenti indicano gli script in `/libs`. Tuttavia, questi sono solo per riferimento, **non deve** modifica qualsiasi elemento in `/libs`, poiché eventuali modifiche apportate potrebbero andare perse. Questo è dovuto al fatto che questo ramo è suscettibile di modifiche ogni volta che aggiorni o applichi un hotfix/feature pack. Eventuali modifiche necessarie devono essere apportate in `/apps`, vedi [Sovrapposizioni e sostituzioni](/help/sites-developing/overlays.md).

### Errori {#errors}

![chlimage_1-234](assets/chlimage_1-234.png)

Speriamo che **Errori** La scheda sarà sempre vuota (come sopra), ma quando si verificano problemi, per ogni componente vengono visualizzati i seguenti dettagli:

* Un avviso se il componente scrive una voce nel registro degli errori, insieme ai dettagli dell’errore e indirizza i collegamenti al codice appropriato all’interno di CRXDE Lite.
* Un avviso se il componente apre una sessione di amministrazione.

Ad esempio, in una situazione in cui viene chiamato un metodo non definito, l’errore risultante verrà visualizzato nella **Errori** scheda:

![chlimage_1-235](assets/chlimage_1-235.png)

Anche la voce del componente nella struttura della scheda Componenti viene contrassegnata con un indicatore quando si verifica un errore.

### Prove {#tests}

>[!CAUTION]
>
>Nella AEM 6.2, le funzioni di test della modalità Sviluppatore sono state reimplementate come applicazione autonoma di Strumenti.
>
>Per maggiori dettagli vedi [Verifica dell’interfaccia utente](/help/sites-developing/hobbes.md).
