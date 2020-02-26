---
title: Utilizzo di Marketing Campaign Manager
seo-title: Utilizzo di Marketing Campaign Manager
description: Marketing Campaign Manager (MCM) è una console per la gestione di campagne per diversi canali Questo software di automazione marketing consente di gestire tutti i marchi, le campagne e le esperienze con i relativi segmenti, elenchi, lead e rapporti.
seo-description: Marketing Campaign Manager (MCM) è una console per la gestione di campagne per diversi canali Questo software di automazione marketing consente di gestire tutti i marchi, le campagne e le esperienze con i relativi segmenti, elenchi, lead e rapporti.
uuid: 3df6c0b8-dc0a-4a02-a38c-8250fb829404
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 1445437e-7f22-49ad-9bde-f3c0ff7d5142
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Utilizzo di Marketing Campaign Manager{#working-with-the-marketing-campaign-manager}

In AEM, Marketing Campaign Manager (MCM) è una console per la gestione di campagne per diversi canali. Questo software di automazione marketing consente di gestire tutti i marchi, le campagne e le esperienze con i relativi segmenti, elenchi, lead e rapporti.

MCM è accessibile da diverse aree di AEM, ad esempio dalla schermata introduttiva, tramite l’icona Campagne o con l’URL:

`https://<hostname>:<port>/libs/mcm/content/admin.html`

Ad esempio:

`http://localhost:4502/libs/mcm/content/admin.html`

![screen_shot_2012-02-21at114636am](assets/screen_shot_2012-02-21at114636am.png)

Da MCM è possibile accedere a:

* **[Dashboard](#dashboard)**È composto di quattro riquadri:

   * [Elenchi](#lists)

      Questo riquadro mostra gli elenchi creati e il numero di lead in ciascuno di essi. Da questo riquadro è possibile creare un nuovo elenco direttamente o tramite l’importazione di lead.

      Quando si seleziona un elenco, si passa alla sezione [Elenchi](#lists) contenente i relativi dettagli.

   * [Segmenti](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#anoverviewofsegmentation)

      Questo riquadro mostra i segmenti che sono stati definiti. I segmenti consentono di caratterizzare un set di visitatori che condividono alcune caratteristiche.

      Quando si seleziona un segmento, si passa alla pagina di definizione dello stesso.

   * [Rapporti](/help/sites-administering/reporting.md)\
      In AEM sono disponibili diversi rapporti che consentono di analizzare e monitorare lo stato dell’istanza. Questo riquadro di MCM elenca i report disponibili.

      Quando si seleziona un report si passa alla pagina dello stesso.

   * [Campagne](#campaigns)

      This pane lists your campaign experiences such as [newsletters](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) and [teasers](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers).

* **[Lead](#leads)**

   Questo riquadro consente di gestire i lead. Potete creare o importare i lead, modificare specifici dettagli di singoli lead o eliminare quelli che non sono più necessari. Puoi inoltre inserire i lead in diversi gruppi, o Elenchi. **Nota:** Adobe non prevede ulteriori miglioramenti di questa funzionalità.

   Si consiglia di utilizzare [Adobe Campaign e l’integrazione con AEM](/help/sites-administering/campaign.md).

* **[Elenchi](#lists)**

   Questo riquadro consente di gestire gli elenchi di lead.**Nota:** Adobe non prevede ulteriori miglioramenti di questa funzionalità.

   Si consiglia di utilizzare [Adobe Campaign e l’integrazione con AEM](/help/sites-administering/campaign.md).

* **[Campagne](#campaigns)**Questo riquadro consente di gestire i marchi, le campagne e le esperienze.

## Dashboard {#dashboard}

Il dashboard presenta quattro riquadri che offrono una panoramica sugli elenchi di lead, sui segmenti, sui report e sulle campagne. Sono inoltre disponibili alcune funzionalità di base.

![mcm_dashboard](assets/mcm_dashboard.png)

## Lead {#leads}

>[!NOTE]
>
>Adobe non prevede ulteriori miglioramenti di questa funzionalità (gestione dei lead).\
>Recommendation is to leverage [Adobe Campaign and the integration to AEM](/help/sites-administering/campaign.md).

In AEM MCM, puoi organizzare e aggiungere i lead immettendoli manualmente o importando un elenco di voci separate da virgole, ad esempio una mailing list. I lead possono inoltre essere generati dalle registrazioni a newsletter o community (se configurate, queste possono avviare un flusso di lavoro per la compilazione dei lead). In genere i lead sono organizzati per categorie e inseriti in un elenco in modo da consentire successive operazioni quali l’invio di messaggi e-mail personalizzati per un particolare gruppo.

Nella sezione **Lead** nel riquadro a sinistra potete creare, importare, modificare ed eliminare i lead, quindi attivarli o disattivarli secondo le necessità. Puoi aggiungere un lead a un elenco o vedere a quali elenchi appartiene.

>[!NOTE]
>
>Consulta [Lavorare con i lead](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithleads) per informazioni dettagliate sulle attività specifiche.

![screen_shot_2012-02-21at114748am-1](assets/screen_shot_2012-02-21at114748am-1.png)

## Elenchi {#lists}

>[!NOTE]
>
>Adobe non prevede ulteriori miglioramenti di questa funzionalità (gestione degli elenchi).\
>Recommendation is to leverage [Adobe Campaign and the integration to AEM](/help/sites-administering/campaign.md).

Gli elenchi consentono di organizzare i lead in gruppi. Tramite gli elenchi puoi indirizzare una campagna marketing a un determinato gruppo di utenti, ad esempio per l’invio di una newsletter mirata.

Nella sezione **Elenchi** puoi gestire gli elenchi. Puoi crearli, importarli, modificarli ed eliminarli, nonché attivarli o disattivarli secondo le necessità. Puoi inoltre visualizzare i lead che appartengono a un dato elenco, verificare se questo appartiene a un altro elenco e visualizzarne una descrizione.

>[!NOTE]
>
>Consulta [Lavorare con gli elenchi](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists) per informazioni dettagliate sulle attività specifiche.

![screen_shot_2012-02-21at124828pm-1](assets/screen_shot_2012-02-21at124828pm-1.png)

### Campagne {#campaigns}

>[!NOTE]
>
>Consulta [Teaser e strategie](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists), [Impostazione della campagna](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#settingupyourcampaign) e [Newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) per informazioni dettagliate sulle attività specifiche.

Per accedere a campagne esistenti, in MCM fate clic su **Campagne**.

![screen_shot_2012-02-21at1106pm](assets/screen_shot_2012-02-21at11106pm.png)

* **Nel riquadro a sinistra**:

   È presente un elenco di marchi e campagne.

   Fate clic su un marchio per:

   * espandere l’elenco e mostrare tutte le relative campagne nel riquadro a sinistra, con il numero di esperienze esistenti per ogni campagna;
   * aprire la panoramica del marchio nel riquadro a destra.

* **Nel riquadro di destra**:

   Per ogni marchio sono visualizzate delle icone (le campagne di versioni precedenti non sono mostrate).

   Potete fare doppio clic su di esse per aprire la panoramica del marchio.

#### Panoramica del marchio {#brand-overview}

![mcm_brandoverview](assets/mcm_brandoverview.png)

In questa sezione è possibile effettuare le seguenti attività:

* Verificare il numero di campagne ed esperienze (numero riportato nel riquadro a sinistra) per il marchio in questione.
* Usare il comando **Nuovo...** per creare una nuova campagna per il marchio.

* Modificare l’intervallo di tempo visualizzato; selezionate **Settimana**, **Mese** o **Trimestre**, usate le frecce per selezionare specifici periodi o tornate a **Oggi**.

* Seleziona una campagna (nel riquadro a destra) per:

   * Modificare le proprietà con il comando **Proprietà**
   * **Eliminare** la campagna.

* Aprire la panoramica della campagna (doppio clic su una campagna nel riquadro a destra o clic nel riquadro a sinistra)

#### Panoramica della campagna {#campaign-overview}

Per le singole campagne sono disponibili due viste:

1. **Vista calendario**

   Usate l’icona:

   ![](do-not-localize/mcm_iconcalendarview.png)

   Viene presentato un elenco di tutti i punti di contatto (grigio) con un ambito temporale orizzontale delle esperienze (verde) collegate ai vari punti di contatto:

   ![mcm_banner_Calendarview](assets/mcm_banner_calendarview.png)

   In questa sezione è possibile effettuare le seguenti attività:

   * Modificare l’ambito temporale visualizzato utilizzando le frecce o tornare a **Oggi**.
   * Usare **Aggiungi punto di contatto...** per aggiungere un nuovo punto di contatto a un’esperienza esistente.
   * Fai clic su un teaser (nel riquadro a destra) per impostare **Ora di attivazione** e **Ora di disattivazione**.

1. **Vista a elenco**

   Usate l’icona:

   ![](do-not-localize/mcm_icon_listview.png)

   Vengono elencate tutte le esperienze (ad es. teaser e newsletter) per la campagna selezionata:

   ![mcm_banner_listview](assets/mcm_banner_listview.png)

   In questa sezione è possibile effettuare le seguenti attività:

   * **Crea un** nuovo... esperienza; ad esempio, offerte Adobe Target, teaser e newsletter.
   * Seleziona **Modifica** o fai doppio clic per modificare i dettagli di una pagina teaser o newsletter.
   * Seleziona **Proprietà** per definire le proprietà di una pagina teaser o newsletter.
   * Selezionare **Simula** per simulare l’aspetto di un’esperienza (pagina teaser o newsletter).

      Una volta aperta la pagina simulata è possibile aprire la barra laterale per passare alla modalità di modifica per tale pagina.

   * Selezionare **Analizza...** per analizzare le impression generate per una pagina.
   * Selezionare **Elimina** per eliminare gli elementi che non sono più necessari.
   * Seleziona **Ricerca** per cercare del testo (la ricerca viene effettuata nel campo Titolo delle esperienze).
   * Usa la ricerca **Avanzata** per applicare filtri alla ricerca.

### Simulazione delle esperienze della campagna {#simulating-your-campaign-experiences}

In MCM, fai clic su **Campagne**. Accertati che sia attiva la vista Elenco, quindi seleziona l’esperienza di campagna desiderata e fai clic su **Simula**. Verrà aperto il punto di contatto (pagina teaser o newsletter) per mostrare l’esperienza selezionata, così come si presenterà al visitatore.

![mcm_simulateexperience](assets/mcm_simulateexperience.png)

Puoi inoltre aprire la barra laterale (clic sulla piccola freccia rivolta verso il basso) per passare alla modalità di modifica e aggiornare la pagina.

### Analisi delle esperienze della campagna {#analyzing-your-campaign-experiences}

In MCM, fai clic su **Campagne**. Accertati che sia attiva la vista Elenco, quindi seleziona l’esperienza di campagna desiderata e seleziona **Analizza**. Viene visualizzato un grafico delle impression registrate per la pagina nel tempo.

![mcm_campaign_analysis](assets/mcm_campaignanalyze.png)

