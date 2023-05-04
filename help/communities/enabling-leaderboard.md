---
title: Funzionalità della classifica
seo-title: Leaderboard Feature
description: Aggiunta di un componente della classifica a una pagina
seo-description: Adding a Leaderboard component to a page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 8%

---

# Funzionalità della classifica {#leaderboard-feature}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La `Leaderboard` Il componente consente di ottenere un&#39;idea di come i membri interagiscono all&#39;interno della comunità, in base ai punti guadagnati (punteggio di base) o alla loro esperienza (punteggio avanzato).

Prima di includere il componente della classifica in una pagina, è necessario configurare [Punteggio e badge delle community](implementing-scoring.md).

Questa sezione della documentazione descrive

* Aggiunta di `Leaderboard` a un [sito della community](overview.md#community-sites)

* Impostazioni di configurazione per `Leaderboard` component

## Aggiunta di una classifica a una pagina {#adding-a-leaderboard-to-a-page}

Per aggiungere una `Leaderboard` in una pagina in modalità di authoring, individua il componente

* `Communities / Leaderboard`

e trascinarlo nella posizione desiderata su una pagina.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando viene posizionato per la prima volta su una pagina di un sito della community, viene visualizzato questo componente:

![chlimage_1-8](assets/chlimage_1-8.png)

## Configurazione della classifica {#configuring-leaderboard}

Seleziona il `Leaderboard` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### Scheda Impostazioni {#settings-tab}

Sotto la **[!UICONTROL Impostazioni]** specificare le informazioni relative al membro da visualizzare:

* **[!UICONTROL Nome visualizzato]**
Un nome descrittivo da visualizzare per la bacheca, che rifletta le regole selezionate per la visualizzazione di badge e punteggi.

   Il valore predefinito è `Leaderboard`, se non è stato inserito nulla.

* **[!UICONTROL Badge]**
Se questa opzione è selezionata, nella classifica è inclusa una colonna per le icone del badge.

   Il valore predefinito è deselezionato.

* **[!UICONTROL Nome badge]**
Se questa opzione è selezionata, nella classifica è inclusa una colonna relativa al nome del badge.

   Il valore predefinito è deselezionato.

* **[!UICONTROL Usa avatar]**
Se questa opzione è selezionata, l&#39;immagine avatar del membro viene inclusa nella classifica, accanto al collegamento del nome al profilo membro.

   Il valore predefinito è deselezionato.

### Scheda Regole {#rules-tab}

Sotto la **[!UICONTROL Regole]** scheda , il sito community e le relative regole di valutazione e contrassegno

* **[!UICONTROL Posizione della regola]**
(obbligatorio) Posizione in cui è configurata la regola Punteggio/Badging .

* **[!UICONTROL Regola di valutazione]**
(obbligatorio) Regola specifica che genera i punteggi da visualizzare.

* **[!UICONTROL Regola di contrassegno]**
(obbligatorio) Regola specifica che genera il badge da visualizzare.

* **[!UICONTROL Limite visualizzazione]**
Numero di membri da visualizzare per pagina.

   Il valore predefinito è 10.

## Esempio: Leader dei partecipanti {#example-participants-leaderboard}

Questo rapporto della classifica deriva dall’applicazione di regole di punteggio di base.

Configurazione del componente della classifica:

* **[!UICONTROL Impostazioni]** scheda:

   * Nome visualizzato = `Participation Board`
   * `checked`:

      * Badge
      * Nome badge
      * Usa avatar

* **[!UICONTROL Regole]** scheda:

   * Percorso regola = `/content/sites/communities/jcr:content`
   * Regola punteggio = `/etc/community/scoring/rules/forums-scoring`
   * Regola assegnazione badge = `/etc/community/badging/rules/reference-badging`
   * Limite di visualizzazione = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## Esempio: Leaderboard di esperti {#example-experts-leaderboard}

Questo rapporto della classifica deriva dall’applicazione di regole di punteggio avanzate.

Configurazione del componente della classifica:

* **[!UICONTROL Impostazioni]** scheda:

   * Nome visualizzato = `Expertise Board`
   * `checked`:

      * Badge
      * Usa avatar

* **[!UICONTROL Regole]** scheda:

   * Percorso regola = `/content/sites/communities/jcr:content`
   * Regola punteggio = `/etc/community/scoring/rules/adv-forums-scoring`
   * Regola assegnazione badge = `/etc/community/badging/rules/adv-forums-badging`
   * Limite di visualizzazione = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Nozioni di base sulla classifica](leaderboard.md) per sviluppatori.

Le istruzioni per la creazione delle regole sono fornite nella sezione [Punteggio e badge delle community](implementing-scoring.md) per amministratori.
